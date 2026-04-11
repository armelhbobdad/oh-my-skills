# cocoindex Settings, Auth, Lifecycle Reference

Detailed reference for `cocoindex.lib`, `cocoindex.setting`, `cocoindex.auth_registry`, `cocoindex.index`, `cocoindex.llm`, `cocoindex.query_handler`, `cocoindex.typing`, and `cocoindex.utils`. All citations T1 on v0.3.37 (commit `87c5dbf0`).

## Contents

- [Library lifecycle](#library-lifecycle)
- [Settings](#settings)
- [Auth registry](#auth-registry)
- [Index definitions](#index-definitions)
- [LLM specs](#llm-specs)
- [Query handlers](#query-handlers)
- [Schema typing](#schema-typing)
- [Utils](#utils)
- [CLI](#cli)

## Library lifecycle

### settings decorator

```python
@overload
def settings(fn: Callable[[], setting.Settings]) -> Callable[[], setting.Settings]: ...
@overload
def settings(fn: None) -> Callable[[Callable[[], setting.Settings]], Callable[[], setting.Settings]]: ...
def settings(fn: Callable[[], setting.Settings] | None = None) -> Any
```
[AST:python/cocoindex/lib.py:L35]

Decorator registering a function that returns a `Settings` object as the settings provider. Called once at init time. Warns (non-fatal) if re-registered — the new function overrides. When a settings function is registered, environment variables are NO LONGER consulted.

Usage:
```python
@cocoindex.settings
def provide_settings() -> cocoindex.Settings:
    return cocoindex.Settings(
        database=cocoindex.DatabaseConnectionSpec(url="postgres://..."),
    )
```

### init

```python
def init(settings: setting.Settings | None = None) -> None
```
[AST:python/cocoindex/lib.py:L58]

Explicit cocoindex initialization. Optional — cocoindex auto-initializes on first flow method call. Prefer calling explicitly at startup so potential errors surface before running flows.

If `settings` is None, loads from the registered settings function (via `@settings` decorator) or from environment variables.

If `settings` is provided, it overrides both the decorator-registered function AND environment variables.

### start_server

```python
def start_server(settings: setting.ServerSettings) -> None
```
[AST:python/cocoindex/lib.py:L67]

Starts the HTTP server for CocoInsight and REST access. Ensures all flows are built first via `flow.ensure_all_flows_built()`. Blocks until the server stops.

This is the underlying function for the `cocoindex server` CLI.

### stop

```python
def stop() -> None
```
[AST:python/cocoindex/lib.py:L73]

Stop the cocoindex library. [AST:python/cocoindex/lib.py:L73]

## Settings

### Settings

```python
@dataclass
class Settings:
    ignore_target_drop_failures: bool = False
    database: DatabaseConnectionSpec | None = None
    db_schema_name: str | None = None
    app_namespace: str = ""
    global_execution_options: GlobalExecutionOptions | None = None

    @classmethod
    def from_env(cls) -> Self: ...
```
[AST:python/cocoindex/setting.py:L75]

Library-level settings dataclass.

- `ignore_target_drop_failures` — env `COCOINDEX_IGNORE_TARGET_DROP_FAILURES`. When `True`, target drop errors during setup changes are logged and skipped instead of halting.
- `database` — Postgres connection for CocoIndex internal storage AND default for the built-in `Postgres` target.
- `db_schema_name` — env `COCOINDEX_DATABASE_SCHEMA_NAME`. Auto-created if missing.
- `app_namespace` — env `COCOINDEX_APP_NAMESPACE`. Prefix for flow full names (e.g., `Staging.MyFlow`).
- `global_execution_options` — shared execution limits.

`from_env()` reads all of the above from environment variables (listed below).

### DatabaseConnectionSpec

```python
@dataclass
class DatabaseConnectionSpec:
    url: str
    user: str | None = None
    password: str | None = None
    max_connections: int = 25
    min_connections: int = 5
```
[AST:python/cocoindex/setting.py:L29]

- `url` — `postgres://user:pass@host[:port]/db`. Env `COCOINDEX_DATABASE_URL`.
- `user` / `password` — override the URL's embedded credentials. Env `COCOINDEX_DATABASE_USER` / `COCOINDEX_DATABASE_PASSWORD`. Preferred over embedding in the URL when credentials contain special characters (avoids URL-encoding pitfalls).
- `max_connections` / `min_connections` — pool bounds. Env `COCOINDEX_DATABASE_MAX_CONNECTIONS` / `COCOINDEX_DATABASE_MIN_CONNECTIONS`. Defaults 25 / 5. Note: if using Supabase's session pooler, its pool size defaults to 15 — either raise Supabase's limit or lower `max_connections`.

### GlobalExecutionOptions

```python
@dataclass
class GlobalExecutionOptions:
    source_max_inflight_rows: int | None = 1024
    source_max_inflight_bytes: int | None = None
```
[AST:python/cocoindex/setting.py:L43]

- `source_max_inflight_rows` — shared cap across all sources in all flows. Env `COCOINDEX_SOURCE_MAX_INFLIGHT_ROWS`.
- `source_max_inflight_bytes` — shared byte-budget across sources. Env `COCOINDEX_SOURCE_MAX_INFLIGHT_BYTES`.

Global and per-source limits (on `FlowBuilder.add_source()`) are enforced independently — a row is admitted only when BOTH budgets have capacity.

### ServerSettings

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
[AST:python/cocoindex/setting.py:L149]

- `address` — bind address for the HTTP server. Default `127.0.0.1:49344`.
- `cors_origins` — CORS whitelist for browsers accessing the server (e.g., CocoInsight UI).

`parse_cors_origins` is a helper that splits a comma-delimited env var into a list.

### get_app_namespace

```python
def get_app_namespace(*, trailing_delimiter: str | None = None) -> str
```
[AST:python/cocoindex/setting.py:L12]

Returns the configured `app_namespace` string. When `trailing_delimiter` is provided and the namespace is non-empty, appends the delimiter. E.g., with `app_namespace="Staging"` and `trailing_delimiter='.'`, returns `"Staging."`. With empty namespace, returns `""` regardless.

Useful for naming external backends that need namespace-prefixed identifiers.

## Auth registry

### AuthEntryReference / TransientAuthEntryReference

```python
@dataclass
class TransientAuthEntryReference(Generic[T]):
    key: str

class AuthEntryReference(TransientAuthEntryReference[T]):
    """Reference an auth entry, with a key stable across runs."""
```
[AST:python/cocoindex/auth_registry.py:L15] [AST:python/cocoindex/auth_registry.py:L21]

`AuthEntryReference[T]` is a subclass of `TransientAuthEntryReference[T]`, so anywhere a transient ref is expected, you can pass a stable one.

### add_auth_entry

```python
def add_auth_entry(key: str, value: T) -> AuthEntryReference[T]
```
[AST:python/cocoindex/auth_registry.py:L31]

Register an auth entry with an explicit, stable key. Use this for target backend credentials — the key IS the identity cocoindex uses to reconcile backend state across flow definition changes. Keep keys stable even as the underlying credentials change.

### add_transient_auth_entry

```python
def add_transient_auth_entry(value: T) -> TransientAuthEntryReference[T]
```
[AST:python/cocoindex/auth_registry.py:L25]

Register an auth entry with an auto-generated key. Use for sources and functions where key stability doesn't matter.

### ref_auth_entry

```python
def ref_auth_entry(key: str) -> AuthEntryReference[T]
```
[AST:python/cocoindex/auth_registry.py:L37]

Look up an existing auth entry by key. Returns a reference without re-registering.

## Index definitions

### VectorSimilarityMetric

```python
class VectorSimilarityMetric(Enum):
    COSINE_SIMILARITY = "CosineSimilarity"
    L2_DISTANCE = "L2Distance"
    INNER_PRODUCT = "InnerProduct"
```
[AST:python/cocoindex/index.py:L6]

Similarity metrics supported across all vector targets. Larger = more similar for cosine/inner-product; smaller = more similar for L2.

### HnswVectorIndexMethod / IvfFlatVectorIndexMethod

```python
@dataclass
class HnswVectorIndexMethod:
    kind: str = "Hnsw"
    m: int | None = None
    ef_construction: int | None = None

@dataclass
class IvfFlatVectorIndexMethod:
    kind: str = "IvfFlat"
    lists: int | None = None
```
[AST:python/cocoindex/index.py:L13] [AST:python/cocoindex/index.py:L22]

HNSW is the pgvector default; IvfFlat is available as an alternative. Leave fields unset to use target defaults.

### VectorIndexDef

```python
@dataclass
class VectorIndexDef:
    field_name: str
    metric: VectorSimilarityMetric
    method: VectorIndexMethod | None = None
```
[AST:python/cocoindex/index.py:L33]

`VectorIndexMethod = Union[HnswVectorIndexMethod, IvfFlatVectorIndexMethod]`. [AST:python/cocoindex/index.py:L29]

### FtsIndexDef

```python
@dataclass
class FtsIndexDef:
    field_name: str
    parameters: dict[str, Any] | None = None
```
[AST:python/cocoindex/index.py:L44]

`parameters` accepts target-specific kwargs (e.g., `tokenizer_name` for LanceDB). **Currently only LanceDB enterprise supports FTS indexes** — specifying one on other targets raises an error.

### IndexOptions

```python
@dataclass
class IndexOptions:
    primary_key_fields: Sequence[str]
    vector_indexes: Sequence[VectorIndexDef] = ()
    fts_indexes: Sequence[FtsIndexDef] = ()
```
[AST:python/cocoindex/index.py:L57]

Assembled internally by `DataCollector.export()` from its keyword arguments. Users typically don't construct this directly.

## LLM specs

### LlmApiType

```python
class LlmApiType(Enum):
    OPENAI = "OpenAi"
    OLLAMA = "Ollama"
    GEMINI = "Gemini"
    VERTEX_AI = "VertexAi"
    ANTHROPIC = "Anthropic"
    LITE_LLM = "LiteLlm"
    OPEN_ROUTER = "OpenRouter"
    VOYAGE = "Voyage"
    VLLM = "Vllm"
    BEDROCK = "Bedrock"
    AZURE_OPENAI = "AzureOpenAi"
    NOVITA = "Novita"
```
[AST:python/cocoindex/llm.py:L7]

Supported LLM provider types. Not all support both generation and embedding — consult [EXT:https://cocoindex.io/docs/ai/llm] for capability matrix.

### LlmSpec

```python
@dataclass
class LlmSpec:
    api_type: LlmApiType
    model: str
    address: str | None = None
    api_key: TransientAuthEntryReference[str] | None = None
    api_config: VertexAiConfig | OpenAiConfig | AzureOpenAiConfig | None = None
```
[AST:python/cocoindex/llm.py:L55]

Used by `ExtractByLlm` and other generation functions. `address` overrides the default provider URL. `api_key` is a transient auth ref when you want to avoid env vars. `api_config` carries provider-specific fields.

### Provider configs

```python
@dataclass
class VertexAiConfig:
    kind = "VertexAi"
    project: str
    region: str | None = None
```
[AST:python/cocoindex/llm.py:L25]

```python
@dataclass
class OpenAiConfig:
    kind = "OpenAi"
    org_id: str | None = None
    project_id: str | None = None
```
[AST:python/cocoindex/llm.py:L35]

```python
@dataclass
class AzureOpenAiConfig:
    kind = "AzureOpenAi"
    deployment_id: str
    api_version: str | None = None
```
[AST:python/cocoindex/llm.py:L45]

Azure OpenAI **does not** use `api_key`; it uses Azure credentials. Vertex AI uses ADC (Application Default Credentials) via `gcloud auth application-default login`.

## Query handlers

### QueryHandlerResultFields

```python
@dataclass
class QueryHandlerResultFields:
    embedding: list[str] = field(default_factory=list)
    score: str | None = None
```
[AST:python/cocoindex/query_handler.py:L11]

Metadata telling CocoInsight which columns in your query results hold embeddings and scores — lets the UI render vectors and similarity rankings.

### QueryInfo

```python
@dataclass
class QueryInfo:
    embedding: list[float] | npt.NDArray[np.float32] | None = None
    similarity_metric: VectorSimilarityMetric | None = None
```
[AST:python/cocoindex/query_handler.py:L31]

Per-query metadata your handler attaches to the response. The engine reads this for CocoInsight visualization.

### QueryOutput

```python
@dataclass
class QueryOutput(Generic[R]):
    results: list[R]
    query_info: QueryInfo = field(default_factory=QueryInfo)
```
[AST:python/cocoindex/query_handler.py:L44]

Return type for query handlers. `results` can be a list of dicts or dataclasses.

## Schema typing

### Annotated aliases

Used to attach CocoIndex schema kind tags to Python types on dataclass fields and function signatures. [AST:python/cocoindex/typing.py:L37]

```python
Int64 = Annotated[int, TypeKind("Int64")]
Float32 = Annotated[float, TypeKind("Float32")]
Float64 = Annotated[float, TypeKind("Float64")]
Range = Annotated[tuple[int, int], TypeKind("Range")]
Json = Annotated[Any, TypeKind("Json")]
LocalDateTime = Annotated[datetime.datetime, TypeKind("LocalDateTime")]
OffsetDateTime = Annotated[datetime.datetime, TypeKind("OffsetDateTime")]
```

### Vector

`Vector` is a typing alias with dimension info. [AST:python/cocoindex/typing.py:L49]

Usage:
```python
Vector[np.float32]                      # unbounded dim
Vector[np.float32, Literal[384]]        # fixed dim 384 — maps to pgvector(384)
```

When the element type is numpy-compatible (numeric), resolves to `Annotated[NDArray[dtype], VectorInfo(dim=...)]`. Otherwise resolves to `Annotated[list[dtype], VectorInfo(dim=...)]`.

Only fixed-dimension `Float32`/`Float64`/`Int64` vectors map to pgvector `vector(N)` columns; other vectors become `jsonb` in Postgres targets.

### Supporting types

- `VectorInfo(NamedTuple)`: `dim: int | None` [AST:python/cocoindex/typing.py:L18]
- `TypeKind(NamedTuple)`: `kind: str` [AST:python/cocoindex/typing.py:L22]
- `TypeAttr(key: str, value: Any)` [AST:python/cocoindex/typing.py:L26]

## Utils

### get_target_default_name

```python
def get_target_default_name(flow: Flow, target_name: str, delimiter: str = "__") -> str
```
[AST:python/cocoindex/utils.py:L5]

Returns `{app_namespace}{delimiter}{flow.name}{delimiter}{target_name}`. Used by most targets to pick a default table/collection name.

### get_target_storage_default_name (DEPRECATED)

Alias for `get_target_default_name`. Kept for backward compatibility — use the shorter name in new code. [AST:python/cocoindex/utils.py:L18]

## CLI

The `cocoindex` CLI is a click group with subcommands. Full entry point: [AST:python/cocoindex/cli.py:L122].

```
cocoindex [-e ENV_FILE] [-d APP_DIR] COMMAND ...
```

Top-level options:
- `-e/--env-file PATH` — load env vars from `.env` file. Defaults to `.env` in cwd.
- `-d/--app-dir PATH` — add to `sys.path` before loading the app module.
- `-V/--version` — show version (reads from `cocoindex` package metadata).

### Subcommands

- `ls [APP_TARGET]` [AST:python/cocoindex/cli.py:L143] — list flows. With `APP_TARGET`, lists flows defined in that app (marks missing setup with `[+]`). Without, lists all flows persisted in the backend.
- `show APP_FLOW_SPECIFIER [--color] [--verbose]` [AST:python/cocoindex/cli.py:L195] — render the flow spec as a rich tree.
- `setup APP_TARGET [-f] [--reset]` [AST:python/cocoindex/cli.py:L337] — check and apply backend setup. `--reset` drops existing before setup.
- `drop APP_TARGET [FLOW_NAME...] [-f]` [AST:python/cocoindex/cli.py:L364] — drop backends for all or named flows.
- `update APP_FLOW_SPECIFIER [-L] [--reexport] [--reset] [-f] [-q]` [AST:python/cocoindex/cli.py:L456] — build/update the index. `-L` = live mode.
- `evaluate APP_FLOW_SPECIFIER [--output-dir DIR] [--no-cache]` [AST:python/cocoindex/cli.py:L522] — run transformations to disk without updating targets.
- `server APP_TARGET [-a ADDR] [-L] [--reexport] [--full-reprocess] [--setup/--reset] [-f] [-q] [--cors-origin URL] [--cors-cocoindex] [--cors-local PORT] [--reload]` [AST:python/cocoindex/cli.py:L642] — start the HTTP server. `--reload` enables auto-reload on code changes via `watchfiles`.

`APP_TARGET` forms:
- `path/to/app.py` — a Python file
- `installed_module` — a module importable by name
