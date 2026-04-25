# Settings, Query Handler, and CLI

The pieces that survived from v0.3.37 (with breaking changes) plus the LMDB-backed Settings rewrite and the v1.0.0 CLI.

## Settings — `cocoindex.setting`

```python
@dataclass
class GlobalExecutionOptions:
    source_max_inflight_rows: int | None = 1024
    source_max_inflight_bytes: int | None = None
```
[AST:python/cocoindex/setting.py:L12]

```python
@dataclass
class Settings:
    db_path: os.PathLike[str] | None = None
    global_execution_options: GlobalExecutionOptions | None = None
    lmdb_max_dbs: int = 1024
    lmdb_map_size: int = 0x1_0000_0000   # 4 GiB

    @classmethod
    def from_env(cls, db_path: os.PathLike[str] | None = None) -> Self: ...
```
[AST:python/cocoindex/setting.py:L44] [:L53]

**Breaking change from v0.3.37.** v0.3.37's `Settings` had `database: DatabaseConnectionSpec`, `db_schema_name`, `app_namespace`, `ignore_target_drop_failures` — **all four are gone**. v1.0.0 stores everything in a local **LMDB** file at `db_path`.

`Settings.from_env(db_path=None)` reads (in order):
- `db_path` argument (overrides env)
- `COCOINDEX_SOURCE_MAX_INFLIGHT_ROWS` (parsed as int, defaults to `GlobalExecutionOptions.source_max_inflight_rows = 1024`)
- `COCOINDEX_SOURCE_MAX_INFLIGHT_BYTES` (parsed as int, defaults to `None`)
- `COCOINDEX_LMDB_MAX_DBS` (parsed as int, defaults to `1024`)
- `COCOINDEX_LMDB_MAP_SIZE` (parsed as int, defaults to `0x1_0000_0000` = 4 GiB)

The default db_path env var is read by `cocoindex._internal.setting.get_default_db_path()` ([AST:python/cocoindex/_internal/setting.py:L12]) which checks `COCOINDEX_DB`. The public `cocoindex.setting.Settings.from_env` does NOT read `COCOINDEX_DB` — pass `db_path` explicitly or set it in your `lifespan` builder:

```python
@coco.lifespan
async def lifespan(builder: coco.EnvironmentBuilder):
    # builder.settings already populated from Settings.from_env() in __init__
    yield
```

`db_path` is **required** at `Environment` construction — `ValueError("Settings.db_path must be provided")` is raised if `None`.

```python
@dataclass
class ServerSettings:
    address: str = "127.0.0.1:49344"
    cors_origins: list[str] | None = None

    @classmethod
    def from_env(cls) -> Self: ...

    @staticmethod
    def parse_cors_origins(s: str | None) -> list[str] | None: ...
```
[AST:python/cocoindex/setting.py:L93] [:L102] [:L123]

`ServerSettings.from_env()` reads `COCOINDEX_SERVER_ADDRESS` and `COCOINDEX_SERVER_CORS_ORIGINS` (CSV-split, whitespace-trimmed). v1.0.0 retains `ServerSettings` as a type but the `cocoindex server` CLI subcommand from v0.3.37 was **removed** — `ServerSettings` is now reserved for future server tooling or custom embedded servers.

## Query Handler — `cocoindex.query_handler`

```python
@dataclass
class QueryHandlerResultFields:
    embedding: list[str] = field(default_factory=list)
    score: str | None = None
```
[AST:python/cocoindex/query_handler.py:L10]

```python
@dataclass
class QueryHandlerInfo:                      # NEW in v1.0.0
    result_fields: QueryHandlerResultFields | None = None
```
[AST:python/cocoindex/query_handler.py:L21]

```python
@dataclass
class QueryInfo:
    embedding: list[float] | NDArray[np.float32] | None = None
    # Note: similarity_metric: VectorSimilarityMetric | None = None  -- REMOVED in v1.0.0
```
[AST:python/cocoindex/query_handler.py:L30]

```python
R = TypeVar("R", default=Any)

@dataclass
class QueryOutput(Generic[R]):
    results: list[R]
    query_info: QueryInfo = field(default_factory=QueryInfo)
```
[AST:python/cocoindex/query_handler.py:L43]

`QueryInfo.similarity_metric` was removed because v1.0.0 has no top-level `VectorSimilarityMetric` enum (similarity is per-connector now). If you stored `similarity_metric` in tracking records, drop the field on read.

The query-handler types are metadata for tools like CocoInsight to introspect the structure of query results — they are not invoked by the runtime directly. `Flow.add_query_handler(...)` from v0.3.37 is gone; query handlers in v1.0.0 attach via the connector's target API (e.g., `target.add_query_handler(name, handler, result_fields=...)` where supported).

## CLI — `cocoindex` command

```python
@click.group()
@click.version_option(...)
@click.option("-e", "--env-file", "env_file", ...)
@click.option("-d", "--app-dir", "app_dir", default="", ...)
def cli(env_file: str | None = None, app_dir: str | None = "") -> None: ...
```
[AST:python/cocoindex/cli.py:L505]

`-e <path>` loads a `.env` file via `python-dotenv` before subcommand dispatch. `-d <path>` sets the working directory for app loading (so `app_target` paths can be relative to a project root rather than CWD).

### Subcommands

```sh
cocoindex ls   [APP_TARGET] [--db PATH]                 # List apps registered in the LMDB store
cocoindex show APP_TARGET [--verbose] [--persisted]     # Show app details
cocoindex update APP_TARGET [-L|--live] [--full-reprocess] [--quiet]
cocoindex drop APP_TARGET [-f|--force] [--quiet]
cocoindex init [PROJECT_NAME] [--dir PATH]
```
[AST:python/cocoindex/cli.py:L522] [:L561] [:L652] [:L745] [:L811]

**APP_TARGET** is a path to a `.py` file or an installed module name. `_load_app(app_target)` ([AST:python/cocoindex/cli.py:L274]) imports the module and looks for a top-level `App` instance.

**v0.3.37 → v1.0.0 CLI changes:**
- `cocoindex setup` — gone. Setup is implicit on first `update`.
- `cocoindex evaluate` — gone. There is no `Flow.evaluate_and_dump` equivalent in v1.0.0.
- `cocoindex server` — gone (the embedded HTTP server is gone too, see ServerSettings note above).
- `cocoindex init` — NEW. Scaffolds a project skeleton.
- `cocoindex ls` — semantics changed. Listed flows in v0.3.37; lists registered apps from the LMDB store in v1.0.0. `_get_persisted_app_names(env)` ([AST:python/cocoindex/cli.py:L131]) is the discovery mechanism.

### Specifying APP_TARGET

```sh
cocoindex update main.py                  # Path to a .py file
cocoindex update my_package.indexer       # Installed module name
cocoindex -d ./src update indexer.py      # Path relative to ./src
```

The v0.3.37 `APP_TARGET:FLOW_NAME` syntax (`main.py:my_flow`) is not supported — apps are uniquely identified by their `App.name` attribute, not by module-level symbol selection. To run a different app from the same module, instantiate it under a different `AppConfig.name` and load via the appropriate module.

### Lifespan integration in CLI

`cli.py` defines its own `coco_lifespan` ([AST:python/cocoindex/cli.py:L358]) that wraps the user's app loading. When users decorate their own function with `@coco.lifespan`, it registers with the default environment; the CLI's lifespan composes with the user's at start time.

## ContextKey + ContextProvider plumbing

```python
class ContextKey(Generic[T_co]):
    def __init__(self, key: str, *, detect_change: bool = False): ...
    @property
    def detect_change(self) -> bool: ...
    @property
    def key(self) -> str: ...
```
[AST:python/cocoindex/_internal/context_keys.py:L99]

`detect_change=True` makes the context value a memoization dependency — when the value changes (per `__coco_memo_key__` / canonicalization), components that read it via `coco.use_context(key)` are invalidated. Use this for things like embedder model identity, system prompts, schema versions.

Key strings must be globally unique per process. Re-using a key raises `ValueError("Context key X already used")` at construction time. Use module-namespaced strings (`"my_module.PG_DB"`) to avoid collisions across libraries.

```python
class ContextProvider:
    def provide(self, key: ContextKey[T], value: T) -> T: ...
    def provide_with(self, key: ContextKey[T], cm: ContextManager[T]) -> T: ...
    async def provide_async_with(self, key: ContextKey[T], cm: AsyncContextManager[T]) -> T: ...
    def get(self, key: ContextKey[T] | str, t: type[T] | None = None) -> Any: ...
    async def aclose(self) -> None: ...
```
[AST:python/cocoindex/_internal/context_keys.py:L124] [:L177] [:L238] [:L242] [:L248] [:L271]

`ContextProvider` is owned by the `Environment` (you don't construct it manually). The `EnvironmentBuilder.provide*` methods delegate to it. `provide_with` / `provide_async_with` enter the supplied context manager on the provider's exit stack, ensuring teardown when the lifespan exits.
