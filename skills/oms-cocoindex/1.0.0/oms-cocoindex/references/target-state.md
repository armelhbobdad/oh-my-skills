# Target State Reconciliation

v1.0.0 replaces v0.3.37's flow-lifecycle CRUD (`Flow.setup` / `Flow.drop` / `setup_all_flows` / `drop_all_flows`) with a declarative state-reconciliation API. A *target state* is the desired configuration of an external resource (a Postgres table, a Qdrant collection, a Kafka topic). Cocoindex compares it against tracked previous records and applies the diff via a typed sink. All defined in `python/cocoindex/_internal/target_state.py`.

## Building blocks

```python
class TargetHandler(Protocol[ValueT_contra, TrackingRecordT, OptChildHandlerT_co]):
    def reconcile(
        self,
        key: StableKey,
        desired_target_state: ValueT_contra | NonExistenceType,
        prev_possible_records: Collection[TrackingRecordT],
        prev_may_be_missing: bool,
        /,
    ) -> TargetReconcileOutput[Any, TrackingRecordT, OptChildHandlerT_co] | None: ...
```
[AST:python/cocoindex/_internal/target_state.py:L197]

A `TargetHandler` decides what action to take given the desired state vs. the engine's tracked previous state. It returns a `TargetReconcileOutput` (or `None` for "no-op"):

```python
class TargetReconcileOutput(Generic[ActionT, TrackingRecordT_co, OptChildHandlerT_co], NamedTuple):
    action: ActionT
    sink: TargetActionSink[ActionT, OptChildHandlerT_co]
    tracking_record: TrackingRecordT_co | NonExistenceType
    child_invalidation: Literal["destructive", "lossy"] | None = None
```
[AST:python/cocoindex/_internal/target_state.py:L188]

The sink is what actually mutates the target backend:

```python
class TargetActionSink(Generic[ActionT_contra, OptChildHandlerT_co]):
    @staticmethod
    def from_fn(fn: TargetActionSinkFn[ActionT_contra, OptChildHandlerT_co]) -> TargetActionSink[...]: ...
    @staticmethod
    def from_async_fn(fn: AsyncTargetActionSinkFn[ActionT_contra, OptChildHandlerT_co]) -> TargetActionSink[...]: ...
```
[AST:python/cocoindex/_internal/target_state.py:L143] [:L150] [:L157]

Sink-fn signature ([AST:python/cocoindex/_internal/target_state.py:L99] [:L121]):
```python
# Sync
def __call__(
    self, context_provider: ContextProvider, actions: Sequence[ActionT_contra], /,
) -> Sequence[ChildTargetDef[HandlerT_co] | None] | None: ...

# Async
async def __call__(
    self, context_provider: ContextProvider, actions: Sequence[ActionT_contra], /,
) -> Sequence[ChildTargetDef[HandlerT_co] | None] | None: ...
```

Returning a sequence of `ChildTargetDef[HandlerT]` (one per action) provides child handlers for the next reconciliation level.

```python
class ChildTargetDef(Generic[HandlerT_co], NamedTuple):
    handler: HandlerT_co
```
[AST:python/cocoindex/_internal/target_state.py:L95]

## Provider + State

```python
class TargetStateProvider(
    Generic[ValueT, OptChildHandlerT, MaybePendingS],
    ResolvesTo["TargetStateProvider[ValueT, OptChildHandlerT]"],
):
    @property
    def memo_key(self) -> str: ...
    def target_state(self, key: StableKey, value: ValueT) -> TargetState[OptChildHandlerT]: ...
    def attachment(self, att_type: str) -> TargetStateProvider: ...
```
[AST:python/cocoindex/_internal/target_state.py:L208]

```python
PendingTargetStateProvider: TypeAlias = TargetStateProvider[ValueT, OptChildHandlerT, PendingS]
```
[AST:python/cocoindex/_internal/target_state.py:L243]

```python
class TargetState(Generic[OptChildHandlerT]):
    def __init__(
        self,
        provider: TargetStateProvider[ValueT, OptChildHandlerT],
        key: StableKey,
        value: ValueT,
    ): ...
```
[AST:python/cocoindex/_internal/target_state.py:L248]

A `TargetState` bundles `(provider, key, value)`. Build via `provider.target_state(key, value)` — the connector's helper functions (e.g. `postgres.table_target(...)`) construct these for you.

## Declaration helpers

```python
def declare_target_state(target_state: TargetState[None]) -> None:
    """Declare a target state within the current component context."""
```
[AST:python/cocoindex/_internal/target_state.py:L265]

For target states **without** a child handler. Use case: the target is a leaf (no nested reconciliation needed).

```python
def declare_target_state_with_child(
    target_state: TargetState[TargetHandler[ValueT, Any, OptChildHandlerT]],
) -> PendingTargetStateProvider[ValueT, OptChildHandlerT]:
    """Declare a target state with a child handler within the current component context.
       Returns a TargetStateProvider for the child target states."""
```
[AST:python/cocoindex/_internal/target_state.py:L282]

For target states **with** a child handler. Returns a child provider, allowing nested declarations (e.g., a database target with multiple tables; a Kafka cluster target with multiple topics).

```python
def register_root_target_states_provider(
    name: str,
    handler: TargetHandler[ValueT, Any, OptChildHandlerT],
) -> TargetStateProvider[ValueT, OptChildHandlerT]:
    """Register a top-level provider so connectors can construct TargetStates against it."""
```
[AST:python/cocoindex/_internal/target_state.py:L305]

This is the connector-author entry point — concrete connectors call `register_root_target_states_provider(name, handler)` once at module load, then expose helpers like `mount_table_target(...)` that ultimately resolve through the registered provider.

## Patterns

### Connector users (typical case)

You almost never write a `TargetHandler` directly. Connectors give you a `mount_*_target` helper that wraps `mount_target` + `declare_target_state_with_child`:

```python
target = await postgres.mount_table_target(
    PG_DB,
    table_name="doc_embeddings",
    table_schema=await postgres.TableSchema.from_class(DocEmbedding, primary_key=["id"]),
)
target.declare_vector_index(column="embedding")

@coco.fn
async def process_chunk(chunk, ..., table: postgres.TableTarget[DocEmbedding]) -> None:
    table.declare_row(row=DocEmbedding(...))
```

`target.declare_row(...)` registers a row-level state. The reconciliation engine compares declared rows against previously tracked rows and emits `INSERT`/`UPDATE`/`DELETE` actions through the connector's sink fn.

### Connector authors

```python
class MyTableHandler:
    def reconcile(self, key, desired_target_state, prev_possible_records, prev_may_be_missing):
        if isinstance(desired_target_state, NonExistenceType):
            return TargetReconcileOutput(
                action=DropTable(name=key),
                sink=DROP_SINK,
                tracking_record=NON_EXISTENCE,
            )
        ...

_PROVIDER = register_root_target_states_provider("my_db", MyTableHandler())

async def mount_table_target(db_key, *, table_name, table_schema):
    state = _PROVIDER.target_state(table_name, MyTableValue(schema=table_schema))
    child_provider = await coco.mount_target(state)   # mount_target == use_mount + declare_target_state_with_child
    return MyTableTarget(child_provider)
```

`child_invalidation` in `TargetReconcileOutput`:
- `"destructive"` — child state must be re-declared from scratch on next pass (e.g., schema mismatch detected).
- `"lossy"` — child state can be incrementally re-declared (e.g., a column was added).
- `None` — child state survives the parent's reconciliation.

## Auto-deserialization

The internal `_TypedTargetHandlerWrapper` ([AST:python/cocoindex/_internal/target_state.py:L56]) introspects your `TargetHandler.reconcile` signature, reads the type annotation on `prev_possible_records` (parameter index 3), and auto-deserializes raw stored values into typed objects. You don't need to do this yourself — write `prev_possible_records: Collection[MyTrackingRecord]` and the wrapper takes care of the rest.
