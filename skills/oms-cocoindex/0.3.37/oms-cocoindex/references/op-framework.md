# cocoindex Op Framework Reference

Detailed reference for `cocoindex.op` — the custom-operation authoring API. Use these primitives when the built-in sources/functions/targets don't cover your use case. All citations T1 on v0.3.37 (commit `87c5dbf0`).

## Contents

- [Spec base classes](#spec-base-classes)
- [Enums and dataclasses](#enums-and-dataclasses)
- [Function authoring](#function-authoring)
- [Source connector authoring](#source-connector-authoring)
- [Target connector authoring](#target-connector-authoring)
- [Batching semantics](#batching-semantics)

## Spec base classes

All spec base classes use the `SpecMeta` metaclass [AST:python/cocoindex/op.py:L51], which applies `@dataclasses.dataclass` to subclasses automatically. Inherit to define fields as normal dataclass attributes — instances can be constructed as `ClassName(field1=value1, ...)`.

```python
class SourceSpec(metaclass=SpecMeta, category=OpCategory.SOURCE): ...          # [AST:python/cocoindex/op.py:L71]
class FunctionSpec(metaclass=SpecMeta, category=OpCategory.FUNCTION): ...      # [AST:python/cocoindex/op.py:L75]
class TargetSpec(metaclass=SpecMeta, category=OpCategory.TARGET): ...          # [AST:python/cocoindex/op.py:L79]
class TargetAttachmentSpec(metaclass=SpecMeta, category=OpCategory.TARGET_ATTACHMENT): ...  # [AST:python/cocoindex/op.py:L83]
class DeclarationSpec(metaclass=SpecMeta, category=OpCategory.DECLARATION): ...  # [AST:python/cocoindex/op.py:L87]
```

Every subclass has `_op_category` automatically set based on the base class category.

### Executor protocol

```python
class Executor(Protocol):
    op_category: OpCategory
```
[AST:python/cocoindex/op.py:L91]

Executors are plain classes (not Protocols) in practice; this Protocol exists for static type hinting.

### EmptyFunctionSpec

```python
class EmptyFunctionSpec(FunctionSpec):
    pass
```
[AST:python/cocoindex/op.py:L478]

Placeholder spec used internally by `@op.function` (standalone function decorator). You don't need to reference it directly.

## Enums and dataclasses

### OpCategory

```python
class OpCategory(Enum):
    FUNCTION = "function"
    SOURCE = "source"
    TARGET = "target"
    DECLARATION = "declaration"
    TARGET_ATTACHMENT = "target_attachment"
```
[AST:python/cocoindex/op.py:L40]

### ArgRelationship

```python
class ArgRelationship(Enum):
    EMBEDDING_ORIGIN_TEXT = "cocoindex.io/embedding_origin_text"
    CHUNKS_BASE_TEXT = "cocoindex.io/chunk_base_text"
    RECTS_BASE_IMAGE = "cocoindex.io/rects_base_image"
```
[AST:python/cocoindex/op.py:L126]

Attaches semantic metadata to the relationship between an input argument and a function's output. Used by CocoInsight and other tools to understand what your custom function produces:

- `EMBEDDING_ORIGIN_TEXT` — output is an embedding vector for the input text arg.
- `CHUNKS_BASE_TEXT` — output is a chunks table (Range-keyed) for the input text arg.
- `RECTS_BASE_IMAGE` — output is a rectangles table for the input image arg.

### OpArgs

```python
@dataclass
class OpArgs:
    gpu: bool = False
    cache: bool = False
    batching: bool = False
    max_batch_size: int | None = None
    behavior_version: int | None = None
    timeout: datetime.timedelta | None = None
    arg_relationship: tuple[ArgRelationship, str] | None = None
```
[AST:python/cocoindex/op.py:L135]

Assembled from kwargs passed to `@function(...)` / `@executor_class(...)`. See decorator docs below for usage.

### SourceReadOptions

```python
@dataclass
class SourceReadOptions:
    include_ordinal: bool = False
    include_content_version_fp: bool = False
    include_value: bool = False
```
[AST:python/cocoindex/op.py:L521]

Passed by the engine to `list()` and `get_value()` methods of a custom source. Fields are hints:

- `include_ordinal` — when `provides_ordinal()` returns True, `list()` **must** include `ordinal` in yielded rows when this flag is True. Helps skip unnecessary reprocessing.
- `include_content_version_fp` — optional fingerprint for cheap change detection.
- `include_value` — when True, `get_value()` **must** provide the full row value. Optional for `list()`.

### PartialSourceRowData

```python
@dataclass
class PartialSourceRowData(Generic[V]):
    value: V | Literal["NON_EXISTENCE"] | None = None
    ordinal: int | Literal["NO_ORDINAL"] | None = None
    content_version_fp: bytes | None = None
```
[AST:python/cocoindex/op.py:L556]

Sentinels:
- `NON_EXISTENCE` — the row has been deleted from the source. [AST:python/cocoindex/op.py:L551]
- `NO_ORDINAL` — source does not support ordinals. [AST:python/cocoindex/op.py:L552]

### PartialSourceRow

```python
@dataclass
class PartialSourceRow(Generic[K, V]):
    key: K
    data: PartialSourceRowData[V]
```
[AST:python/cocoindex/op.py:L571]

Yielded by `list()` methods of custom sources.

### TargetStateCompatibility

```python
class TargetStateCompatibility(Enum):
    COMPATIBLE = "Compatible"
    PARTIALLY_COMPATIBLE = "PartialCompatible"
    NOT_COMPATIBLE = "NotCompatible"
```
[AST:python/cocoindex/op.py:L811]

Returned by target connector `check_state_compatibility()` when CocoIndex checks if an existing target setup matches the current flow definition. Governs whether setup is a no-op, an in-place upgrade, or a drop-and-recreate.

## Function authoring

### @op.function

```python
def function(**args: Any) -> Callable[[Callable[..., Any]], Callable[..., Any]]
```
[AST:python/cocoindex/op.py:L489]

Decorator for standalone functions. Kwargs populate `OpArgs`. The function's `op_kind` is auto-derived from `snake_case` → `CamelCase` of the function name.

```python
@cocoindex.op.function(cache=True, behavior_version=1)
def compute_something(text: str, window: int = 10) -> str:
    """Docstring is used as human-readable description."""
    ...
```

All argument and return types MUST be annotated — they determine the CocoIndex data schema.

### @op.executor_class

```python
def executor_class(**args: Any) -> Callable[[type], type]
```
[AST:python/cocoindex/op.py:L448]

Decorator for class-based executors. Use when you need:
- Configurable behavior via a `FunctionSpec` subclass.
- Preparation logic (e.g., load a model) separate from per-call execution.
- Batched execution.

```python
class ComputeSomething(cocoindex.op.FunctionSpec):
    """Docstring is used as description."""
    param1: str
    param2: int | None = None

@cocoindex.op.executor_class(cache=True, behavior_version=1, gpu=True)
class ComputeSomethingExecutor:
    spec: ComputeSomething  # REQUIRED — must be a class annotation
    _model: Any | None = None

    def prepare(self) -> None:
        """Runs once before any __call__."""
        self._model = load_model(self.spec.param1)

    def __call__(self, text: str, count: int = 1) -> list[str]:
        """Runs per input row."""
        ...
```

Requirements:
- The class MUST have a `spec: YourSpecClass` annotation (not an instance attribute — cocoindex reads `__annotations__`).
- `prepare()` is optional.
- `__call__()` is required. Arguments and return must be type-annotated.

The decorator validates the `spec` annotation, extracts the spec class type, registers the op factory based on `spec_cls._op_category`, and returns the class unchanged.

### OpArgs fields in detail

- `gpu=True` — executor will run on GPU; affects scheduling and resource allocation.
- `cache=True` — executor results are cached for reuse during reprocessing. **Requires** `behavior_version` to be set. Recommended for computationally intensive functions.
- `batching=True` — `__call__` receives a list of inputs instead of a single input. See [Batching semantics](#batching-semantics).
- `max_batch_size: int` — upper bound for batch size when batching is enabled.
- `behavior_version: int` — version number. Bump to invalidate existing cache entries when the function's observable behavior changes.
- `timeout: datetime.timedelta | None` — execution timeout per call; `None` = default (1800 seconds).
- `arg_relationship: tuple[ArgRelationship, str]` — e.g., `(ArgRelationship.EMBEDDING_ORIGIN_TEXT, "text")` declares that this function embeds the `text` arg.

## Source connector authoring

### @op.source_connector

```python
def source_connector(
    *,
    spec_cls: type[Any],
    key_type: Any = Any,
    value_type: Any = Any,
) -> Callable[[type], type]
```
[AST:python/cocoindex/op.py:L746]

Decorator for registering a custom source. `spec_cls` must be a `SourceSpec` subclass; validated at decoration time (raises `ValueError` otherwise).

```python
class MySourceSpec(cocoindex.op.SourceSpec):
    connection_string: str
    query: str

@dataclass
class MyKey:
    id: str

@dataclass
class MyValue:
    title: str
    body: str

@cocoindex.op.source_connector(spec_cls=MySourceSpec, key_type=MyKey, value_type=MyValue)
class MyConnector:
    async def create(self, spec: MySourceSpec) -> "MyExecutor":
        return MyExecutor(spec)

class MyExecutor:
    def __init__(self, spec: MySourceSpec):
        self._spec = spec

    def provides_ordinal(self) -> bool:
        return True

    async def list(
        self, options: cocoindex.op.SourceReadOptions,
    ) -> AsyncIterator[cocoindex.op.PartialSourceRow[MyKey, MyValue]]:
        ...

    async def get_value(
        self, key: MyKey, options: cocoindex.op.SourceReadOptions,
    ) -> cocoindex.op.PartialSourceRowData[MyValue]:
        ...
```

Required methods on the connector class:
- `create(spec) -> Executor` — returns an executor object (awaited if coroutine).

Required methods on the executor object:
- `list(options) -> Iterator | AsyncIterator` of `PartialSourceRow`
- `get_value(key, options) -> PartialSourceRowData`

Optional:
- `provides_ordinal() -> bool` — returns True if the source supplies ordinal values. When True, `SourceReadOptions.include_ordinal=True` requires ordinals in `list()` output.

## Target connector authoring

### @op.target_connector

```python
def target_connector(
    *,
    spec_cls: type[Any],
    persistent_key_type: Any = Any,
    setup_state_cls: type[Any] | None = None,
) -> Callable[[type], type]
```
[AST:python/cocoindex/op.py:L1073]

Decorator for registering a custom target. `spec_cls` must be a `TargetSpec` subclass. `persistent_key_type` is the key type used for backend identity. `setup_state_cls` defaults to `spec_cls` when None.

The connector class must implement several lifecycle methods (see `_TargetConnector` [AST:python/cocoindex/op.py:L819] for the full internal contract, or refer to existing extended target modules like `cocoindex.targets.chromadb`, `lancedb`, `doris`, `turbopuffer`, `pinecone` as authoritative examples).

Key methods:
- `get_persistent_key(target_spec_context, target_name) -> persistent_key` — identifies the backend
- `get_setup_state(target_spec_context) -> setup_state` — current desired state
- `check_state_compatibility(existing_state, desired_state) -> TargetStateCompatibility`
- `describe_resource(persistent_key) -> str`
- `apply_setup_changes_async(changes) -> None`
- `prepare_async(target_spec_context) -> mutate_context`
- `mutate_async(mutate_context, changes) -> None`

## Batching semantics

When `batching=True` is set on `@function` or `@executor_class`:

- `__call__` receives a `list[T]` of inputs (one batch) and must return a `list[U]` of outputs.
- Currently, **batching only supports functions with a single argument**. The argument type in the signature must be `list[SomeType]`.
- A batch flushes when:
  1. No other batches are running AND the queue has pending items
  2. The pending batch reaches `max_batch_size`

```python
@cocoindex.op.function(batching=True, max_batch_size=32)
def embed_batch(texts: list[str]) -> list[list[float]]:
    return model.encode(texts)
```

For class-based:
```python
@cocoindex.op.executor_class(batching=True, max_batch_size=512, gpu=True, cache=True, behavior_version=1)
class MyEmbedExecutor:
    spec: MyEmbedSpec

    def __call__(self, texts: list[str]) -> list[list[float]]:
        ...
```

Batching prevents requests from waiting indefinitely for batches to fill, while still allowing high throughput for GPU inference and rate-limited APIs.
