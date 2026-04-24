# Component API Reference

The component API is cocoindex v1.0.0's authoring surface. Pipelines are built from `@coco.fn`-decorated functions mounted into an `Environment` orchestrated by an `App`.

## App

`coco.App[P, R]` is the top-level pipeline runner. It owns a `main_fn` (a `@coco.fn`-decorated callable) plus its bound args/kwargs, and lazily creates a `core.App` against the configured `Environment` on first use. Defined at [AST:python/cocoindex/_internal/app.py:L208].

```python
@dataclass(frozen=True)
class AppConfig:
    name: str
    environment: Environment | LazyEnvironment = _default_env
    max_inflight_components: int | None = None   # falls back to COCOINDEX_MAX_INFLIGHT_COMPONENTS env var, then a default
```
[AST:python/cocoindex/_internal/app.py:L202]

```python
class App(Generic[P, R]):
    def __init__(
        self,
        name_or_config: str | AppConfig,
        main_fn: AsyncCallable[P, R] | Callable[P, R],
        /,
        *args: P.args,
        **kwargs: P.kwargs,
    ) -> None: ...

    def update(self, *, full_reprocess: bool = False, live: bool = False) -> UpdateHandle[R]: ...
    def update_blocking(self, *, report_to_stdout: bool = False, full_reprocess: bool = False, live: bool = False) -> R: ...
    async def drop(self) -> None: ...
    def drop_blocking(self, *, report_to_stdout: bool = False) -> None: ...
```
[AST:python/cocoindex/_internal/app.py:L208] [:L299] [:L335] [:L368] [:L380]

- A `str` for `name_or_config` is shorthand for `AppConfig(name=name_or_config)`.
- `update()` returns an `UpdateHandle[R]` that is also `Awaitable[R]` — `result = await app.update()` works as a one-liner. Use `handle.stats()` for a snapshot or `async for snap in handle.watch():` to follow progress.
- `live=True` keeps live components processing after `mark_ready` (see `live-components.md`).
- `full_reprocess=True` invalidates memoized state and reprocesses everything.

```python
async def show_progress(handle: UpdateHandle[R]) -> R: ...   # Run the operation with progress display. Consumes the handle.
```
[AST:python/cocoindex/_internal/app.py:L194]

`UpdateHandle[R]` (defined at [AST:python/cocoindex/_internal/app.py:L49]) and `DropHandle` ([:L143]) are the runtime handles; both expose `stats()` and an awaitable `result()`.

## Environment

`Environment` is the cocoindex runtime — it owns settings, an asyncio event loop, a `ContextProvider`, and an exception handler. The default environment is a `LazyEnvironment` accessed via `coco.start()` / `coco.stop()` (or `coco.runtime()` as a context manager) — direct construction is rare. [AST:python/cocoindex/_internal/environment.py:L183]

```python
class Environment:
    def __init__(
        self,
        settings: setting.Settings,
        *,
        name: str | None = None,
        context_provider: ContextProvider | None = None,
        event_loop: asyncio.AbstractEventLoop | None = None,
        exception_handler: ExceptionHandler | None = None,
        info: EnvironmentInfo | None = None,
    ): ...

    @property
    def name(self) -> str: ...
    @property
    def settings(self) -> setting.Settings: ...
    @property
    def context_provider(self) -> ContextProvider: ...
    @property
    def event_loop(self) -> asyncio.AbstractEventLoop: ...
    @property
    def async_context(self) -> core.AsyncContext: ...
    @property
    def exception_handler(self) -> ExceptionHandler | None: ...

    def get_context(self, key: ContextKey[T]) -> T: ...
```
[AST:python/cocoindex/_internal/environment.py:L212] [:L247–:L278]

`Settings.db_path` is **required** — Environment construction raises `ValueError` if it's `None`. Set `COCOINDEX_DB=/path/to/state.lmdb` and use `Settings.from_env()`.

## EnvironmentBuilder + lifespan

`@coco.lifespan` registers a function that builds the environment. It runs once when the environment starts; lifespan-scoped resources live until `stop()`.

```python
class EnvironmentBuilder:
    def __init__(self, settings: setting.Settings | None = None): ...   # default: Settings.from_env()
    @property
    def settings(self) -> setting.Settings: ...
    def provide(self, key: ContextKey[Any], value: Any) -> Any: ...
    def provide_with(self, key: ContextKey[Any], cm: ContextManager[Any]) -> Any: ...
    async def provide_async_with(self, key: ContextKey[Any], cm: AsyncContextManager[Any]) -> Any: ...
    def set_exception_handler(self, handler: ExceptionHandler) -> None: ...
```
[AST:python/cocoindex/_internal/environment.py:L87]

```python
LifespanFn = (
    Callable[[EnvironmentBuilder], Iterator[None]]
  | Callable[[EnvironmentBuilder], AsyncIterator[None]]
)

@overload
def lifespan(fn: LifespanFn) -> LifespanFn: ...
@overload
def lifespan(fn: None) -> Callable[[LifespanFn], LifespanFn]: ...
def lifespan(fn: LifespanFn | None = None) -> Any: ...
```
[AST:python/cocoindex/_internal/environment.py:L118] [:L452]

Pattern:
```python
PG_DB = coco.ContextKey[asyncpg.Pool]("pg_db")

@coco.lifespan
async def env_lifespan(builder: coco.EnvironmentBuilder) -> AsyncIterator[None]:
    async with await asyncpg.create_pool(DSN) as pool:
        builder.provide(PG_DB, pool)
        yield     # run the app
    # pool closes here on stop()
```

`provide_with` / `provide_async_with` accept a context manager and enter it on the builder's exit stack — equivalent to `provide(key, ctx.enter_context(cm))` but with deterministic teardown.

## start / stop / runtime

```python
async def start() -> None: ...           # Start default environment + enter lifespan
async def stop() -> None: ...            # Stop default environment + exit lifespan
def start_blocking() -> None: ...        # Sync variant
def stop_blocking() -> None: ...         # Sync variant
async def default_env() -> Environment: ...  # Get the default environment (starting it if needed)
def runtime() -> _DualModeRuntime: ...   # Dual-mode context manager (with / async with)
```
[AST:python/cocoindex/_internal/api.py:L603] [:L608] [:L613] [:L618] [:L623] [:L655]

```python
# Sync code
with coco.runtime():
    app.update_blocking()

# Async code
async with coco.runtime():
    await app.update()
```

`runtime()` raises if you call the sync form from inside a running event loop.

## @coco.fn

`coco.fn` is a singleton instance of `_FunctionDecorator`. It exposes both the decorator namespace (`@coco.fn(...)`) and an `as_async` variant. [AST:python/cocoindex/_internal/function.py:L1578] [:L1811]

```python
# All overloads
@coco.fn                                                # bare — preserves sync/async
@coco.fn(memo=True)                                     # memoize results
@coco.fn(batching=True, max_batch_size=64)              # batch — function takes list[T], returns list[R]; requires async
@coco.fn(runner=GPU)                                    # serialize through a Runner (e.g. GPU)
@coco.fn(version=2)                                     # explicit version for change tracking
@coco.fn(logic_tracking="full"|"self"|None)             # tracking granularity (default "full")
@coco.fn(deps={"prompt": SYSTEM_PROMPT, "model": MODEL_NAME})  # external dependency snapshot at decoration time

# Always-async variant (use when you need batching/runner on a sync function)
@coco.fn.as_async
@coco.fn.as_async(batching=True, runner=GPU)
```

Behavior:
- **Memoization** (`memo=True`): skip execution when inputs unchanged; without batching/runner requires a `ComponentContext`; with batching/runner, ComponentContext is optional.
- **Batching** (`batching=True`): the underlying function receives `list[T]` and returns `list[R]`. Requires async signature with the bare decorator; use `as_async` to wrap a sync fn into async batching.
- **`runner=GPU`** (the singleton from `_internal/runner.py:L282`): sync fns run on a dedicated single-worker thread pool; async fns run in-process. Setting `COCOINDEX_RUN_GPU_IN_SUBPROCESS=1` switches to subprocess isolation.
- **`version`**: when set, the integer version replaces the AST-derived logic fingerprint. Bump it to force re-execution.
- **`logic_tracking`**: `"full"` propagates code changes transitively; `"self"` only tracks the function itself (children invalidate independently); `None` disables tracking and is incompatible with `deps`.
- **`deps`**: external values that affect logic but aren't visible in the body (e.g. module-level prompts). Canonicalized through the memoization-key pipeline at decoration time. For per-call values, pass arguments instead.

## Mount APIs

All mount APIs require an active `ComponentContext` (i.e., they must be called from inside a `@coco.fn` running under `App.update()` / `mount()`).

```python
class ComponentMountHandle:
    """Handle for processing unit(s) started with mount() / mount_each(). Allows waiting until ready."""
    async def ready(self) -> None: ...
```
[AST:python/cocoindex/_internal/api.py:L170]

### mount

```python
async def mount(processor_fn: AnyCallable[P, Any], *args, **kwargs) -> ComponentMountHandle: ...
async def mount(subpath: ComponentSubpath, processor_fn: AnyCallable[P, Any], *args, **kwargs) -> ComponentMountHandle: ...
```
[AST:python/cocoindex/_internal/api.py:L349]

Mounts a processing unit in the background. Subpath defaults to `Symbol(processor_fn.__name__)` when omitted. Pass a `LiveComponent` class to mount a live component; for regular functions a normal processing unit is created.

### mount_each

```python
async def mount_each(fn: AnyCallable[Concatenate[T, P], Any], items: _ItemsType[T], *args, **kwargs) -> ComponentMountHandle: ...
async def mount_each(subpath, fn, items, *args, **kwargs) -> ComponentMountHandle: ...
# items: Iterable[(StableKey, T)] | AsyncIterable[(StableKey, T)] | LiveMapFeed[StableKey, T]
```
[AST:python/cocoindex/_internal/api.py:L445] [:L419]

One independent component per item. When `items` is a `LiveMapFeed`/`LiveMapView`, an internal `LiveComponent` is created automatically; you must run with `app.update(live=True)` for `LiveMapFeed` (no scannable snapshot).

### use_mount

```python
async def use_mount(processor_fn: AnyCallable[P, ResolvesTo[ReturnT] | ReturnT], *args, **kwargs) -> ReturnT: ...
async def use_mount(subpath: ComponentSubpath, processor_fn, *args, **kwargs) -> ReturnT: ...
```
[AST:python/cocoindex/_internal/api.py:L245] (8 overloads at [:L193]–[:L244])

Mount a dependent unit and return its result. The child cannot refresh independently — re-executing the child requires re-executing the parent. The return-type bridge `ResolvesTo[T]` lets a child return a `Pending`-state provider while `use_mount` returns the resolved variant.

### mount_target

```python
async def mount_target(
    target_state: TargetState[TargetHandler[_ValueT, Any, _ChildHandlerT]],
) -> TargetStateProvider[_ValueT, _ChildHandlerT]: ...
```
[AST:python/cocoindex/_internal/api.py:L566]

Sugar over `use_mount` + `declare_target_state_with_child`. The component subpath is auto-derived from the target's globally unique stable key. See `target-state.md` for the underlying primitives.

### map

```python
async def map(
    fn: Callable[Concatenate[T, P], Coroutine[Any, Any, ReturnT]],
    items: Iterable[T] | AsyncIterable[T],
    *args, **kwargs,
) -> list[ReturnT]: ...
```
[AST:python/cocoindex/_internal/api.py:L532]

Pure concurrent execution via `asyncio.TaskGroup`. No components, no memoization, no checkpoints — use when you need fan-out without sub-component lifecycle.

## ComponentSubpath

```python
class ComponentSubpath:
    def __init__(self, *key_parts: StableKey) -> None: ...
    @property
    def parts(self) -> tuple[StableKey, ...]: ...
    def __enter__(self) -> ComponentSubpath: ...
    def __exit__(self, *exc) -> None: ...
    def __truediv__(self, part: StableKey) -> ComponentSubpath: ...   # chaining: subpath / "child"

def component_subpath(*key_parts: StableKey) -> ComponentSubpath: ...
```
[AST:python/cocoindex/_internal/component_ctx.py:L142] [:L198]

Two usage modes:

```python
# (1) As first arg to mount / use_mount
await coco.mount(coco.component_subpath("process", filename), process_file, file, target)

# (2) As a context manager — applies the subpath to all nested mount calls
with coco.component_subpath("process_files"):
    for f in files:
        await coco.mount(coco.component_subpath(str(f.path)), process_file, f, target)
```

## Component context helpers

```python
def get_component_context() -> ComponentContext: ...
def use_context(key: ContextKey[T]) -> T: ...

@asynccontextmanager
async def exception_handler(handler: ExceptionHandler) -> AsyncIterator[None]: ...
```
[AST:python/cocoindex/_internal/component_ctx.py:L305] [:L273] [:L331]

`ComponentContext.attach()` is the bridge for cross-thread execution:

```python
ctx = coco.get_component_context()
with ThreadPoolExecutor() as executor:
    def task():
        with ctx.attach():
            # coco APIs work correctly here, even off the asyncio loop
            ...
    executor.submit(task)
```
[AST:python/cocoindex/_internal/component_ctx.py:L103]

`exception_handler` pushes a handler for background-mounted components within a dynamic scope. The handler signature is `Callable[[BaseException, ExceptionContext], None | Awaitable[None]]`. Multiple handlers form a chain — innermost runs first; if a handler raises, the next outer handler runs with the new exception.
