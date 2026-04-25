# Live Components

Live components run continuously, reacting to streaming change feeds (Kafka, file-watch, etc.). They are protocol-based — any class with `process()` and `process_live(operator)` async methods qualifies. Defined in `python/cocoindex/_internal/live_component.py`.

## LiveComponent Protocol

```python
@runtime_checkable
class LiveComponent(Protocol):
    """Protocol for live components that process continuously."""
    async def process(self) -> None: ...
    async def process_live(self, operator: LiveComponentOperator) -> None: ...

def is_live_component_class(cls: Any) -> bool: ...   # duck-types: type with both methods
```
[AST:python/cocoindex/_internal/live_component.py:L28] [:L35]

`process()` is called for one-shot updates (`app.update(live=False)`). `process_live(operator)` is called for live mode — receives a `LiveComponentOperator` and is expected to call `operator.update(...)`, `operator.delete(...)`, and `operator.mark_ready()` as changes arrive.

## LiveComponentOperator

Wraps the Rust `LiveComponentController`. Passed to `process_live`. [AST:python/cocoindex/_internal/live_component.py:L46]

```python
class LiveComponentOperator:
    async def update_full(self) -> None: ...
    async def update(
        self,
        subpath: ComponentSubpath,
        processor_fn: AnyCallable[_P, Any],
        *args: _P.args,
        **kwargs: _P.kwargs,
    ) -> ComponentMountHandle: ...
    async def delete(self, subpath: ComponentSubpath) -> ComponentMountHandle: ...
    async def mark_ready(self) -> None: ...
```
[AST:python/cocoindex/_internal/live_component.py:L63] [:L70] [:L93] [:L102]

- `update_full()` — re-runs the component's `process()` (full sweep). Blocks until fully ready.
- `update(subpath, fn, *args)` — incremental update; mounts/refreshes a single sub-component at `subpath`. Cannot pass a `LiveComponent` class — `mount()` is for nested live components.
- `delete(subpath)` — incremental deletion of a sub-component.
- `mark_ready()` — signals readiness. **In catch-up mode, this never returns** (terminates `process_live`). Always reachable from live mode.

## LiveMapFeed and LiveMapView

Used as the `items` argument to `mount_each` for streaming sources. [AST:python/cocoindex/_internal/live_component.py:L108] [:L119]

```python
@runtime_checkable
class LiveMapFeed(Protocol[_K, _V]):
    """Watch-only feed (Kafka-style — no scannable snapshot)."""
    async def watch(self, subscriber: LiveMapSubscriber[_K, _V]) -> None: ...

@runtime_checkable
class LiveMapView(LiveMapFeed[_K, _V], Protocol[_K, _V]):
    """Scannable + watchable (localfs-style)."""
    def __aiter__(self) -> AsyncIterator[tuple[_K, _V]]: ...
```

- `LiveMapFeed` requires `app.update(live=True)`. Passing one to `mount_each` outside live mode raises `TypeError`.
- `LiveMapView` extends `LiveMapFeed` with iteration over current items, so it supports both one-shot and live updates.

## LiveMapSubscriber

The callback interface `LiveMapFeed.watch()` writes to. Wraps a `LiveComponentOperator` at a higher level — callers provide keys and values instead of subpaths and processor fns. [AST:python/cocoindex/_internal/live_component.py:L130]

```python
class LiveMapSubscriber(Generic[_K, _V]):
    async def update_all(self) -> None: ...                  # full re-iteration (==operator.update_full())
    async def mark_ready(self) -> None: ...                  # signals readiness
    async def update(self, key: _K, value: _V) -> ComponentMountHandle: ...   # incremental upsert
    async def delete(self, key: _K) -> ComponentMountHandle: ...              # incremental remove
```

## Patterns

### Consuming a streaming source

```python
from cocoindex.connectors import kafka

@coco.fn
async def app_main() -> None:
    target = await postgres.mount_table_target(...)
    feed = kafka.topic_as_map(KAFKA_KEY, topic="events", group="ingestor")  # returns LiveMapFeed
    await coco.mount_each(process_event, feed, target)

# Run with: app.update(live=True)
```

`mount_each` detects the `LiveMapFeed` and creates an internal `_MountEachLiveComponent` that iterates current items in `process()` and watches in `process_live()`. [AST:python/cocoindex/_internal/live_component.py:L174]

### Writing a custom LiveComponent

```python
class MySource:
    async def process(self) -> None:
        # one-shot: snapshot all current items, mount each
        for key, value in self._snapshot():
            await coco.mount(coco.component_subpath(key), process_one, value)

    async def process_live(self, operator: LiveComponentOperator) -> None:
        # live: subscribe to changes, drive the operator
        async for change in self._stream():
            if change.kind == "delete":
                await operator.delete(coco.component_subpath(change.key))
            else:
                await operator.update(coco.component_subpath(change.key), process_one, change.value)
        await operator.mark_ready()

# Mount it like any callable — mount() detects via is_live_component_class()
await coco.mount(MySource, ...)
```
