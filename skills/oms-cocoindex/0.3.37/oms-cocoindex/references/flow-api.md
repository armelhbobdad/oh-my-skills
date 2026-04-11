# cocoindex Flow API Reference

Detailed reference for `cocoindex.flow` — the public flow-authoring API. All citations are T1 (AST-verified via `ast-grep run` on v0.3.37 source, commit `87c5dbf0`).

## Contents

- [FlowBuilder](#flowbuilder)
- [DataScope](#datascope)
- [DataSlice](#dataslice)
- [DataCollector](#datacollector)
- [Flow](#flow)
- [FlowLiveUpdater](#flowliveupdater)
- [Module-level functions](#module-level-functions)
- [Dataclasses](#dataclasses)
- [Deprecation notes](#deprecation-notes)

## FlowBuilder

`FlowBuilder` [AST:python/cocoindex/flow.py:L495]

```python
class FlowBuilder:
    """A flow builder is used to build a flow."""
    _state: _FlowBuilderState
    def __init__(self, state: _FlowBuilderState): ...
```

### add_source

```python
def add_source(
    self,
    spec: op.SourceSpec,
    /,
    *,
    name: str | None = None,
    refresh_interval: datetime.timedelta | None = None,
    max_inflight_rows: int | None = None,
    max_inflight_bytes: int | None = None,
) -> DataSlice[T]
```
[AST:python/cocoindex/flow.py:L511]

Import a source. `spec` must be a `SourceSpec` subclass (e.g., `LocalFile`, `AmazonS3`, `Postgres` source). `name` overrides the default field name (snake_case of the spec class name). `refresh_interval` enables periodic list-and-diff in live mode for sources without native change capture. `max_inflight_rows`/`max_inflight_bytes` limit concurrent processing per source (stacks on top of `GlobalExecutionOptions`).

Raises `ValueError` if `spec` is not a `SourceSpec`.

### transform

```python
def transform(
    self,
    fn_spec: FunctionSpec | Callable[..., Any],
    *args: Any,
    **kwargs: Any,
) -> DataSlice[Any]
```
[AST:python/cocoindex/flow.py:L548]

Apply a function spec to input data slices. The first positional arg and any kwargs are treated as function inputs. Use `DataSlice.transform()` instead when transforming a specific slice (it auto-passes the slice as the first argument).

Raises `ValueError` if no input arguments are provided.

### declare

```python
def declare(self, spec: op.DeclarationSpec) -> None
```
[AST:python/cocoindex/flow.py:L566]

Add a declaration to the flow. Used for graph targets to configure nodes referenced by relationships — nodes that don't come directly from any data collector. Example: `flow_builder.declare(Neo4jDeclaration(connection=..., nodes_label="Entity", primary_key_fields=["name"]))`.

## DataScope

`DataScope` [AST:python/cocoindex/flow.py:L302]

Represents data for a certain unit — top-level scope, per-document scope, per-chunk scope, etc. Has fields (accessed via `[]`) and collectors.

Key operations (T1 AST-verified):

- `__getitem__(field_name: str) -> DataSlice[T]` — get a field as a `DataSlice`.
- `__setitem__(field_name: str, value: DataSlice[T]) -> None` — set a field. Raises on override attempts (no shadowing).
- `__enter__` / `__exit__` — context manager support (used internally by `DataSlice.for_each` / `row`).
- `add_collector(name: str | None = None) -> DataCollector` [AST:python/cocoindex/flow.py:L345]

## DataSlice

`DataSlice[T]` [AST:python/cocoindex/flow.py:L212]

Readonly typed reference to a slice of flow data.

### row

```python
def row(
    self,
    /,
    *,
    max_inflight_rows: int | None = None,
    max_inflight_bytes: int | None = None,
) -> DataScope
```
[AST:python/cocoindex/flow.py:L232]

Return a child scope representing each row of the table. Use as a context manager:

```python
with doc_slice.row() as doc:
    doc["summary"] = doc["content"].transform(ExtractByLlm(...))
```

### for_each

```python
def for_each(
    self,
    f: Callable[[DataScope], None],
    /,
    *,
    max_inflight_rows: int | None = None,
    max_inflight_bytes: int | None = None,
) -> None
```
[AST:python/cocoindex/flow.py:L253]

Apply a function to each row. Equivalent to `with self.row() as scope: f(scope)`.

### transform

```python
def transform(
    self,
    fn_spec: op.FunctionSpec | Callable[..., Any],
    *args: Any,
    **kwargs: Any,
) -> DataSlice[Any]
```
[AST:python/cocoindex/flow.py:L270]

Apply a function spec to this slice. The slice is passed as the first positional argument; `args`/`kwargs` become additional inputs.

### call

```python
def call(self, func: Callable[..., S], *args: Any, **kwargs: Any) -> S
```
[AST:python/cocoindex/flow.py:L291]

Call a plain Python function with this slice as the first argument. Used for host-side composition helpers.

### __getitem__

```python
def __getitem__(self, field_name: str) -> DataSlice[T]
```

Select a sub-field when the slice has `Struct` type. Raises `KeyError` if field doesn't exist.

## DataCollector

`DataCollector` [AST:python/cocoindex/flow.py:L367]

Collects entries from the same or descendant scopes, to be exported to a target.

### collect

```python
def collect(self, **kwargs: Any) -> None
```
[AST:python/cocoindex/flow.py:L381]

Collect a single entry. Values may be `DataSlice` instances or the enum `GeneratedField.UUID` (auto-generated UUID stable across unchanged inputs). Only one `GeneratedField.UUID` field allowed per collector. Raises `ValueError` on multiple UUID fields.

### export

```python
def export(
    self,
    target_name: str,
    target_spec: op.TargetSpec,
    /,
    *,
    primary_key_fields: Sequence[str],
    attachments: Sequence[op.TargetAttachmentSpec] = (),
    vector_indexes: Sequence[index.VectorIndexDef] = (),
    fts_indexes: Sequence[index.FtsIndexDef] = (),
    vector_index: Sequence[tuple[str, index.VectorSimilarityMetric]] = (),
    setup_by_user: bool = False,
) -> None
```
[AST:python/cocoindex/flow.py:L402]

Export collected data to an external target. Must be called at the top level of a flow (not inside a `row()` scope).

- `target_name` — identifier for this export. Must remain stable across runs; renaming triggers drop+recreate.
- `target_spec` — any `TargetSpec` subclass (`Postgres`, `Qdrant`, `Pinecone`, `Neo4j`, etc.).
- `primary_key_fields` — required. Types must be CocoIndex key types.
- `attachments` — extra target attachments (e.g., `PostgresSqlCommand`).
- `vector_indexes` — list of `VectorIndexDef`.
- `fts_indexes` — list of `FtsIndexDef` (currently LanceDB-only).
- `vector_index` — **legacy alias**, list of `(field_name, metric)` tuples. New code should use `vector_indexes`. When `vector_indexes` is empty and `vector_index` is provided, the tuples are converted to `VectorIndexDef` entries automatically.
- `setup_by_user` — when `True`, the user manages the target lifecycle; CocoIndex will not create/drop it during `setup`/`drop`.

Raises `ValueError` if `target_spec` is not a `TargetSpec` subclass.

## Flow

`Flow` [AST:python/cocoindex/flow.py:L705]

Indexing pipeline handle.

### Properties

- `name: str` — the registered flow name. [AST:python/cocoindex/flow.py:L758]
- `full_name: str` — `{app_namespace}.{name}` (or just `name` if no namespace). [AST:python/cocoindex/flow.py:L765]

### update / update_async

```python
def update(
    self,
    /,
    *,
    reexport_targets: bool = False,
    full_reprocess: bool = False,
    print_stats: bool = False,
) -> _engine.IndexUpdateInfo
```
[AST:python/cocoindex/flow.py:L771]

One-time update. Returns when target is fresh up to the call time. Internally runs a `FlowLiveUpdater` with `live_mode=False`.

`update_async(...)` is the awaitable variant. [AST:python/cocoindex/flow.py:L791]

Options:
- `reexport_targets` — reexport unchanged data (useful after target data loss).
- `full_reprocess` — reprocess everything, invalidating caches.
- `print_stats` — print per-source stats to stdout.

Multiple concurrent calls are cheap — CocoIndex combines them as long as freshness is preserved.

### setup / setup_async / drop / drop_async

```python
def setup(self, report_to_stdout: bool = False) -> None                # [AST:python/cocoindex/flow.py:L855]
async def setup_async(self, report_to_stdout: bool = False) -> None    # [AST:python/cocoindex/flow.py:L861]
def drop(self, report_to_stdout: bool = False) -> None                 # [AST:python/cocoindex/flow.py:L868]
async def drop_async(self, report_to_stdout: bool = False) -> None     # [AST:python/cocoindex/flow.py:L879]
```

Setup creates/updates target backends (tables, collections, etc.) to match the current flow definition. Drop removes all target backends owned by the flow. After drop, the `Flow` instance is still valid — call `setup` again to recreate.

### close

```python
def close(self) -> None
```
[AST:python/cocoindex/flow.py:L886]

Remove the flow from the current process. After calling, no methods on this instance should be used. Does NOT affect persistent backends — call `drop()` first for that.

### evaluate_and_dump

```python
def evaluate_and_dump(self, options: EvaluateAndDumpOptions) -> _engine.IndexUpdateInfo
```
[AST:python/cocoindex/flow.py:L815]

Run the flow transformations and dump outputs to files without updating any target. Used for testing/debugging flows.

### add_query_handler / query_handler

```python
def add_query_handler(
    self,
    name: str,
    handler: Callable[[str], Any],
    /,
    *,
    result_fields: QueryHandlerResultFields | None = None,
) -> None                                                              # [AST:python/cocoindex/flow.py:L898]

def query_handler(
    self,
    name: str | None = None,
    result_fields: QueryHandlerResultFields | None = None,
) -> Callable[[Callable[[str], Any]], Callable[[str], Any]]            # [AST:python/cocoindex/flow.py:L935]
```

Register a query handler callable (sync or async). Returns an object with `.results` (list of dicts/dataclasses) and `.query_info` (`QueryInfo`). `result_fields` provides metadata for tools like CocoInsight. Use the decorator form for clean syntax:

```python
@demo_flow.query_handler(result_fields=QueryHandlerResultFields(embedding=["embedding"], score="score"))
async def search(query: str) -> QueryOutput:
    ...
```

### Other methods

- `internal_flow() -> _engine.Flow` — build and return the engine flow synchronously. [AST:python/cocoindex/flow.py:L823]
- `internal_flow_async() -> _engine.Flow` — async variant. [AST:python/cocoindex/flow.py:L831]

## FlowLiveUpdater

`FlowLiveUpdater` [AST:python/cocoindex/flow.py:L603]

```python
class FlowLiveUpdater:
    def __init__(self, fl: Flow, options: FlowLiveUpdaterOptions | None = None): ...
```
[AST:python/cocoindex/flow.py:L612]

### Lifecycle methods

- `start()` / `async start_async()` [AST:python/cocoindex/flow.py:L632] [AST:python/cocoindex/flow.py:L638]
- `abort()` [AST:python/cocoindex/flow.py:L677]
- `wait()` / `async wait_async()` [AST:python/cocoindex/flow.py:L646] [AST:python/cocoindex/flow.py:L652]
- `next_status_updates() -> FlowUpdaterStatusUpdates` / `async next_status_updates_async()` [AST:python/cocoindex/flow.py:L658] [AST:python/cocoindex/flow.py:L667]
- `update_stats() -> _engine.IndexUpdateInfo` [AST:python/cocoindex/flow.py:L683]

### Context manager usage

Supports both sync (`with`) and async (`async with`) context managers:

```python
with cocoindex.FlowLiveUpdater(demo_flow, opts) as updater:
    ...  # your logic (query loop, etc.)
# On exit: abort() + wait()
```
[AST:python/cocoindex/flow.py:L616] [AST:python/cocoindex/flow.py:L624]

### next_status_updates behavior

Blocks until new status updates arrive. Automatically coalesces multiple updates between calls — no risk of pile-up. Returns a `FlowUpdaterStatusUpdates` with:
- `active_sources: list[str]` — sources still running. Empty means the updater has stopped.
- `updated_sources: list[str]` — sources with updates since last call.

Use in a polling loop to react to changes:

```python
while True:
    updates = updater.next_status_updates()
    for s in updates.updated_sources:
        trigger_downstream(s)
    if not updates.active_sources:
        break
```

## Module-level functions

### flow_def

```python
def flow_def(name: str | None = None) -> Callable[[Callable[[FlowBuilder, DataScope], None]], Flow]
```
[AST:python/cocoindex/flow.py:L1011]

Decorator form of `open_flow`. Wraps a function with signature `(FlowBuilder, DataScope) -> None` and registers it as a named flow. Returns the resulting `Flow` object.

```python
@cocoindex.flow_def(name="MyFlow")
def my_flow(fb: FlowBuilder, ds: DataScope):
    ...
```

### open_flow

```python
def open_flow(name: str, fl_def: Callable[[FlowBuilder, DataScope], None]) -> Flow
```
[AST:python/cocoindex/flow.py:L986]

Explicit registration — the imperative alternative to `@flow_def`. Useful when the name is computed at runtime. Raises `KeyError` if a flow with that name already exists.

### transform_flow

```python
def transform_flow() -> Callable[[Callable[..., DataSlice[T]]], TransformFlow[T]]
```
[AST:python/cocoindex/flow.py:L1251]

Decorator for transient in-memory transforms (no target, no source, just an input→output function). Returns a `TransformFlow` with:
- `__call__(*args, **kwargs) -> DataSlice[T]` — usable inside a flow definition.
- `eval(*args, **kwargs) -> T` — run on concrete inputs. [AST:python/cocoindex/flow.py:L1227]
- `eval_async(*args, **kwargs) -> T` [AST:python/cocoindex/flow.py:L1233]

Parameters must be annotated as `DataSlice[T]`; return must be `DataSlice[U]`.

### Bulk lifecycle helpers

- `flow_names() -> list[str]` [AST:python/cocoindex/flow.py:L1020]
- `flows() -> dict[str, Flow]` [AST:python/cocoindex/flow.py:L1028]
- `flow_by_name(name: str) -> Flow` [AST:python/cocoindex/flow.py:L1036]
- `ensure_all_flows_built() -> None` / `async ensure_all_flows_built_async()` [AST:python/cocoindex/flow.py:L1044] [AST:python/cocoindex/flow.py:L1051]
- `update_all_flows(options: FlowLiveUpdaterOptions) -> dict[str, _engine.IndexUpdateInfo]` [AST:python/cocoindex/flow.py:L1059]
- `async update_all_flows_async(options: FlowLiveUpdaterOptions) -> dict[str, _engine.IndexUpdateInfo]` [AST:python/cocoindex/flow.py:L1068]
- `setup_all_flows(report_to_stdout: bool = False) -> None` [AST:python/cocoindex/flow.py:L1300]
- `drop_all_flows(report_to_stdout: bool = False) -> None` [AST:python/cocoindex/flow.py:L1309]
- `get_flow_full_name(name: str) -> str` [AST:python/cocoindex/flow.py:L979]
- `make_setup_bundle(flow_iter: Iterable[Flow]) -> SetupChangeBundle` / `make_setup_bundle_async(...)` [AST:python/cocoindex/flow.py:L1275] [AST:python/cocoindex/flow.py:L1264]
- `make_drop_bundle(flow_iter: Iterable[Flow]) -> SetupChangeBundle` / `make_drop_bundle_async(...)` [AST:python/cocoindex/flow.py:L1293] [AST:python/cocoindex/flow.py:L1282]

## Dataclasses

- `FlowLiveUpdaterOptions` [AST:python/cocoindex/flow.py:L574]:
  - `live_mode: bool = True`
  - `reexport_targets: bool = False`
  - `full_reprocess: bool = False`
  - `print_stats: bool = False`

- `FlowUpdaterStatusUpdates` [AST:python/cocoindex/flow.py:L591]:
  - `active_sources: list[str]`
  - `updated_sources: list[str]`

- `EvaluateAndDumpOptions` [AST:python/cocoindex/flow.py:L696]:
  - `output_dir: str`
  - `use_cache: bool = True`

- `GeneratedField(Enum)` [AST:python/cocoindex/flow.py:L359]:
  - `UUID = "Uuid"`

## Deprecation notes

**T2-future annotations** from source-level comments and upstream confirmation:

- `add_flow_def(name, fl_def) -> Flow` — DEPRECATED; use `open_flow`. Docstring: `"DEPRECATED: Use ``open_flow()`` instead."` [AST:python/cocoindex/flow.py:L997]
- `remove_flow(fl) -> None` — DEPRECATED; use `fl.close()`. Docstring: `"DEPRECATED: Use ``Flow.close()`` instead."` [AST:python/cocoindex/flow.py:L1004]
- `cocoindex.storages` is a module alias for `cocoindex.targets` (kept for backward compat). [AST:python/cocoindex/__init__.py:L12] [QMD:oms-cocoindex-docs:flow_def.md]

All three are still exported from `__all__` for compatibility. New code should use the replacements.
