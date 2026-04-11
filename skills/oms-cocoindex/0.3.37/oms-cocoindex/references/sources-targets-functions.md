# cocoindex Sources, Targets, Functions Reference

Detailed reference for built-in sources, targets, and functions. All citations T1 on v0.3.37 (commit `87c5dbf0`).

## Contents

- [Sources](#sources)
- [Targets — built-in](#targets--built-in)
- [Targets — extended modules](#targets--extended-modules)
- [Graph mapping types](#graph-mapping-types)
- [Functions — built-in](#functions--built-in)
- [Functions — SentenceTransformer](#functions--sentencetransformer)
- [Functions — ColPali](#functions--colpali)

## Sources

All sources are subclasses of `op.SourceSpec` with `_op_category = op.OpCategory.SOURCE`.

### LocalFile

```python
class LocalFile(op.SourceSpec):
    path: str
    binary: bool = False
    included_patterns: list[str] | None = None
    excluded_patterns: list[str] | None = None
    max_file_size: int | None = None
```
[AST:python/cocoindex/sources/_engine_builtin_specs.py:L10]

Imports files from a local filesystem. Output is a KTable with `filename` (Str, key) and `content` (Str if `binary=False`, Bytes otherwise). Patterns use [globset syntax](https://docs.rs/globset/latest/globset/index.html#syntax).

See [EXT:https://cocoindex.io/docs/sources/localfile] for optional `watch_changes` flag described in docs but not in the v0.3.37 spec class (added in later versions).

### GoogleDrive

```python
class GoogleDrive(op.SourceSpec):
    service_account_credential_path: str
    root_folder_ids: list[str]
    binary: bool = False
    included_patterns: list[str] | None = None
    excluded_patterns: list[str] | None = None
    max_file_size: int | None = None
    recent_changes_poll_interval: datetime.timedelta | None = None
```
[AST:python/cocoindex/sources/_engine_builtin_specs.py:L30]

Imports from Google Drive folders. Set `recent_changes_poll_interval` to enable polling-based change capture in live mode.

### AmazonS3

```python
class AmazonS3(op.SourceSpec):
    bucket_name: str
    prefix: str | None = None
    binary: bool = False
    included_patterns: list[str] | None = None
    excluded_patterns: list[str] | None = None
    max_file_size: int | None = None
    sqs_queue_url: str | None = None
    redis: RedisNotification | None = None
    force_path_style: bool = False
```
[AST:python/cocoindex/sources/_engine_builtin_specs.py:L61]

Imports from S3 buckets. Live updates via:
- SQS queue notifications (set `sqs_queue_url`)
- Redis pub/sub via `RedisNotification(redis_url, redis_channel)` [AST:python/cocoindex/sources/_engine_builtin_specs.py:L52]

### AzureBlob

```python
class AzureBlob(op.SourceSpec):
    account_name: str
    container_name: str
    prefix: str | None = None
    binary: bool = False
    included_patterns: list[str] | None = None
    excluded_patterns: list[str] | None = None
    max_file_size: int | None = None
    sas_token: TransientAuthEntryReference[str] | None = None
    account_access_key: TransientAuthEntryReference[str] | None = None
```
[AST:python/cocoindex/sources/_engine_builtin_specs.py:L77]

Auth precedence: SAS token → account access key → default Azure credential. Credentials are transient auth refs — add via `cocoindex.add_transient_auth_entry(...)`.

### Postgres

```python
class Postgres(op.SourceSpec):
    table_name: str
    database: TransientAuthEntryReference[DatabaseConnectionSpec] | None = None
    included_columns: list[str] | None = None
    ordinal_column: str | None = None
    notification: PostgresNotification | None = None
    filter: str | None = None
```
[AST:python/cocoindex/sources/_engine_builtin_specs.py:L110]

Imports rows from a Postgres table. Live updates via `PostgresNotification(channel_name=None)` which subscribes to `LISTEN`/`NOTIFY`. `ordinal_column` (timestamp or serial) enables incremental updates without notifications. `filter` is an arbitrary SQL boolean expression applied per row.

## Targets — built-in

Defined in `targets/_engine_builtin_specs.py`. All extend `op.TargetSpec`.

### Postgres

```python
class Postgres(op.TargetSpec):
    database: AuthEntryReference[DatabaseConnectionSpec] | None = None
    table_name: str | None = None
    schema: str | None = None
    column_options: dict[str, PostgresColumnOptions] | None = None
```
[AST:python/cocoindex/targets/_engine_builtin_specs.py:L20]

- Fixed-dim `Float32`/`Float64`/`Int64` vectors → `vector(N)` column (pgvector).
- All other vector types → `jsonb`.
- U+0000 characters are automatically stripped from strings.
- `column_options`: per-column overrides, e.g., `{"embedding": PostgresColumnOptions(type="halfvec")}`.

`PostgresColumnOptions(type: Literal["vector", "halfvec"] | None = None)` [AST:python/cocoindex/targets/_engine_builtin_specs.py:L13]

### PostgresSqlCommand (attachment)

```python
class PostgresSqlCommand(op.TargetAttachmentSpec):
    name: str
    setup_sql: str
    teardown_sql: str | None = None
```
[AST:python/cocoindex/targets/_engine_builtin_specs.py:L29]

Executes arbitrary SQL during setup/teardown. Useful for custom indexes, triggers, grants. Both statements should be idempotent (`CREATE ... IF NOT EXISTS`, `DROP ... IF EXISTS`). Multi-statement allowed (`;`-separated).

### Qdrant

```python
@dataclass
class QdrantConnection:
    grpc_url: str
    api_key: str | None = None

@dataclass
class Qdrant(op.TargetSpec):
    collection_name: str
    connection: AuthEntryReference[QdrantConnection] | None = None
```
[AST:python/cocoindex/targets/_engine_builtin_specs.py:L38] [AST:python/cocoindex/targets/_engine_builtin_specs.py:L46]

### Pinecone

```python
@dataclass
class PineconeConnection:
    api_key: str
    environment: str | None = None

@dataclass
class Pinecone(op.TargetSpec):
    index_name: str
    connection: AuthEntryReference[PineconeConnection]
    namespace: str = ""
    cloud: str = "aws"
    region: str = "us-east-1"
    batch_size: int = 100
```
[AST:python/cocoindex/targets/_engine_builtin_specs.py:L54] [AST:python/cocoindex/targets/_engine_builtin_specs.py:L62]

### Neo4j

```python
@dataclass
class Neo4jConnection:
    uri: str
    user: str
    password: str
    db: str | None = None

class Neo4j(op.TargetSpec):
    connection: AuthEntryReference[Neo4jConnection]
    mapping: Nodes | Relationships

class Neo4jDeclaration(op.DeclarationSpec):
    kind = "Neo4j"
    connection: AuthEntryReference[Neo4jConnection]
    nodes_label: str
    primary_key_fields: Sequence[str]
    vector_indexes: Sequence[index.VectorIndexDef] = ()
```
[AST:python/cocoindex/targets/_engine_builtin_specs.py:L127] [AST:python/cocoindex/targets/_engine_builtin_specs.py:L136] [AST:python/cocoindex/targets/_engine_builtin_specs.py:L143]

`Neo4jDeclaration` is used via `flow_builder.declare(...)` to configure referenced nodes not emitted by any specific collector.

### FalkorDB

```python
@dataclass
class FalkorDBConnection:
    uri: str
    graph: str | None = None

class FalkorDB(op.TargetSpec):
    connection: AuthEntryReference[FalkorDBConnection]
    mapping: Nodes | Relationships

class FalkorDBDeclaration(op.DeclarationSpec):
    kind = "FalkorDB"
    connection: AuthEntryReference[FalkorDBConnection]
    nodes_label: str
    primary_key_fields: Sequence[str]
    vector_indexes: Sequence[index.VectorIndexDef] = ()
    fts_indexes: Sequence[index.FtsIndexDef] = ()
```
[AST:python/cocoindex/targets/_engine_builtin_specs.py:L154] [AST:python/cocoindex/targets/_engine_builtin_specs.py:L163] [AST:python/cocoindex/targets/_engine_builtin_specs.py:L170]

### Ladybug

```python
@dataclass
class LadybugConnection:
    api_server_url: str

class Ladybug(op.TargetSpec):
    connection: AuthEntryReference[LadybugConnection]
    mapping: Nodes | Relationships

class LadybugDeclaration(op.DeclarationSpec):
    kind = "Ladybug"
    connection: AuthEntryReference[LadybugConnection]
    nodes_label: str
    primary_key_fields: Sequence[str]
```
[AST:python/cocoindex/targets/_engine_builtin_specs.py:L182] [AST:python/cocoindex/targets/_engine_builtin_specs.py:L188] [AST:python/cocoindex/targets/_engine_builtin_specs.py:L195]

**Backward-compat aliases:** `Kuzu = Ladybug`, `KuzuConnection = LadybugConnection`, `KuzuDeclaration = LadybugDeclaration`. The Kuzu target was retired; use `Ladybug` in new code. [AST:python/cocoindex/targets/_engine_builtin_specs.py:L205]

## Targets — extended modules

Separate modules under `cocoindex.targets.*`. Imported individually.

### ChromaDB — `cocoindex.targets.chromadb`

```python
class ClientType(Enum):
    PERSISTENT = "persistent"
    HTTP = "http"
    CLOUD = "cloud"

class HnswConfig:
    m: int | None = None
    ef_construction: int | None = None
    ef_search: int | None = None

class ChromaDB(op.TargetSpec):
    collection_name: str
    client_type: ClientType = ClientType.PERSISTENT
    path: str | None = None
    host: str | None = None
    port: int | None = None
    ssl: bool = False
    api_key: str | None = None
    tenant: str = chromadb.config.DEFAULT_TENANT
    database: str = chromadb.config.DEFAULT_DATABASE
    hnsw_config: HnswConfig | None = None
    document_field: str | None = None
```
[AST:python/cocoindex/targets/chromadb.py:L22] [AST:python/cocoindex/targets/chromadb.py:L28] [AST:python/cocoindex/targets/chromadb.py:L34]

Metric mapping: `COSINE_SIMILARITY → "cosine"`, `L2_DISTANCE → "l2"`, `INNER_PRODUCT → "ip"`.

### LanceDB — `cocoindex.targets.lancedb`

```python
@dataclass
class DatabaseOptions:
    storage_options: dict[str, Any] | None = None

class LanceDB(op.TargetSpec):
    db_uri: str
    table_name: str
    db_options: DatabaseOptions | None = None
    num_transactions_before_optimize: int = 50
```
[AST:python/cocoindex/targets/lancedb.py:L80] [AST:python/cocoindex/targets/lancedb.py:L84]

LanceDB is the only target that currently supports FTS indexes (enterprise edition).

### Doris — `cocoindex.targets.doris`

```python
class DorisTarget(op.TargetSpec):
    """Apache Doris target connector specification."""
    fe_host: str
    database: str
    table: str
    fe_http_port: int = 8080
    query_port: int = 9030
    username: str = "root"
    password: str = ""
    enable_https: bool = False
    be_load_host: str | None = None
    batch_size: int = 10000
    stream_load_timeout: int = 600
    auto_create_table: bool = True
    schema_change_timeout: int = 60
    index_build_timeout: int = 300
    max_retries: int = 3
    retry_base_delay: float = 1.0
    retry_max_delay: float = 30.0
    replication_num: int = 1
    buckets: int | str = "auto"
    schema_evolution: Literal["extend", "strict"] = "extend"
```
[AST:python/cocoindex/targets/doris.py:L105]

Error hierarchy (plain `Exception` subclasses):
- `DorisError(Exception)` [AST:python/cocoindex/targets/doris.py:L231]
- `DorisConnectionError(DorisError)` [AST:python/cocoindex/targets/doris.py:L235]
- `DorisAuthError(DorisConnectionError)` [AST:python/cocoindex/targets/doris.py:L247]
- `DorisStreamLoadError(DorisError)` [AST:python/cocoindex/targets/doris.py:L251]
- `DorisSchemaError(DorisError)` [AST:python/cocoindex/targets/doris.py:L269]

`RetryConfig` dataclass for tuning retry behavior. [AST:python/cocoindex/targets/doris.py:L283]

### Turbopuffer — `cocoindex.targets.turbopuffer`

```python
class Turbopuffer(op.TargetSpec):
    namespace_name: str
    api_key: str
    region: str = "gcp-us-central1"
```
[AST:python/cocoindex/targets/turbopuffer.py:L36]

Metric mapping: `COSINE_SIMILARITY → "cosine_distance"`, `L2_DISTANCE → "euclidean_squared"`, `INNER_PRODUCT → "dot_product"`.

### Pinecone (connector) — `cocoindex.targets.pinecone`

Provides the runtime connector class (not a new public spec) for the built-in `Pinecone` spec defined in `_engine_builtin_specs.py`. Users don't import this module directly — the connector is registered automatically on package import.

## Graph mapping types

Used by graph targets (`Neo4j`, `FalkorDB`, `Ladybug`) to describe how collected rows map to graph nodes/relationships.

### Nodes

```python
@dataclass
class Nodes:
    kind = "Node"
    label: str
```
[AST:python/cocoindex/targets/_engine_builtin_specs.py:L101]

Maps a row to a graph node with the given label.

### Relationships

```python
@dataclass
class Relationships:
    kind = "Relationship"
    rel_type: str
    source: NodeFromFields
    target: NodeFromFields
```
[AST:python/cocoindex/targets/_engine_builtin_specs.py:L110]

Maps a row to an edge. `source` and `target` identify the connected nodes by their field values.

### NodeFromFields

```python
@dataclass
class NodeFromFields:
    label: str
    fields: list[TargetFieldMapping]
```
[AST:python/cocoindex/targets/_engine_builtin_specs.py:L84]

### ReferencedNode

```python
@dataclass
class ReferencedNode:
    label: str
    primary_key_fields: Sequence[str]
    vector_indexes: Sequence[index.VectorIndexDef] = ()
```
[AST:python/cocoindex/targets/_engine_builtin_specs.py:L92]

Metadata for a graph node label that's referenced by relationships but not directly produced by any collector.

### TargetFieldMapping

```python
@dataclass
class TargetFieldMapping:
    source: str
    target: str | None = None
```
[AST:python/cocoindex/targets/_engine_builtin_specs.py:L74]

If `target` is None, the target field name equals the source field name.

### Backward-compat aliases

```python
NodeMapping = Nodes
RelationshipMapping = Relationships
NodeReferenceMapping = NodeFromFields
```
[AST:python/cocoindex/targets/_engine_builtin_specs.py:L121]

## Functions — built-in

Defined in `functions/_engine_builtin_specs.py`. All extend `op.FunctionSpec`.

### ParseJson

```python
class ParseJson(op.FunctionSpec):
    """Parse a text into a JSON object."""
```
[AST:python/cocoindex/functions/_engine_builtin_specs.py:L10]

Runtime input: `text: Str`, optional `language: Str = "json"`. Returns `Json`.

### DetectProgrammingLanguage

```python
class DetectProgrammingLanguage(op.FunctionSpec):
    """Detect the programming language of a file."""
```
[AST:python/cocoindex/functions/_engine_builtin_specs.py:L23]

Runtime input: `filename: Str`. Returns tree-sitter language name or `Null`.

### SplitRecursively

```python
class SplitRecursively(op.FunctionSpec):
    """Split a document (in string) recursively."""
    custom_languages: list[CustomLanguageSpec] = field(default_factory=list)
```
[AST:python/cocoindex/functions/_engine_builtin_specs.py:L27]

`CustomLanguageSpec(language_name, separators_regex, aliases=[])` [AST:python/cocoindex/functions/_engine_builtin_specs.py:L15] — custom splitting rules using regex boundary patterns (higher-level first).

Runtime inputs (via `.transform(SplitRecursively(), ...)`):
- `text: Str`
- `chunk_size: Int64` (bytes)
- `min_chunk_size: Int64` (default `chunk_size / 2`)
- `chunk_overlap: Int64 | None`
- `language: Str | None` — language name or file extension

Returns _KTable_ with fields: `location: Range`, `text: Str`, `start: Struct{offset, line, column}`, `end: Struct{offset, line, column}`.

Built-in supported languages: c, cpp, csharp, css, dtd, fortran, go, html, java, javascript, json, kotlin, markdown, pascal, php, python, r, ruby, rust, scala, solidity, sql, swift, toml, tsx, typescript, xml, yaml. [EXT:https://cocoindex.io/docs/ops/functions#splitrecursively]

### SplitBySeparators

```python
class SplitBySeparators(op.FunctionSpec):
    separators_regex: list[str] = field(default_factory=list)
    keep_separator: Literal["NONE", "LEFT", "RIGHT"] = "NONE"
    include_empty: bool = False
    trim: bool = True
```
[AST:python/cocoindex/functions/_engine_builtin_specs.py:L33]

Drop-in schema-compatible alternative to `SplitRecursively` when you want direct control over split points (no recursive chunking). Output KTable schema matches `SplitRecursively`.

### EmbedText

```python
class EmbedText(op.FunctionSpec):
    api_type: llm.LlmApiType
    model: str
    address: str | None = None
    output_dimension: int | None = None
    expected_output_dimension: int | None = None
    task_type: str | None = None
    api_config: llm.VertexAiConfig | None = None
    api_key: TransientAuthEntryReference[str] | None = None
```
[AST:python/cocoindex/functions/_engine_builtin_specs.py:L51]

Runtime input: `text: Str`. Returns `Vector[Float32, N]`. For models cocoindex doesn't know, set `expected_output_dimension` explicitly.

### ExtractByLlm

```python
class ExtractByLlm(op.FunctionSpec):
    llm_spec: llm.LlmSpec
    output_type: type
    instruction: str | None = None
```
[AST:python/cocoindex/functions/_engine_builtin_specs.py:L64]

Extracts structured information from text. `output_type` is typically a Python dataclass — cocoindex feeds its schema to the LLM. Clear field names, docstrings, and optional annotations (`T | None`) improve extraction quality. Runtime input: `text: Str`. Returns a value of type `output_type`.

## Functions — SentenceTransformer

Module: `functions/sbert.py`. Requires `pip install 'cocoindex[embeddings]'`.

### SentenceTransformerEmbed

```python
class SentenceTransformerEmbed(op.FunctionSpec):
    model: str
    args: dict[str, Any] | None = None
```
[AST:python/cocoindex/functions/sbert.py:L12]

`args` is passed to the SentenceTransformer constructor — e.g., `{"trust_remote_code": True}`.

### SentenceTransformerEmbedExecutor

```python
@op.executor_class(
    gpu=True,
    cache=True,
    batching=True,
    max_batch_size=512,
    behavior_version=1,
    arg_relationship=(op.ArgRelationship.EMBEDDING_ORIGIN_TEXT, "text"),
)
class SentenceTransformerEmbedExecutor:
    spec: SentenceTransformerEmbed
    _model: Any | None = None

    def analyze(self) -> type: ...
    def __call__(self, text: list[str]) -> list[NDArray[np.float32]]: ...
```
[AST:python/cocoindex/functions/sbert.py:L38]

Reference implementation of a spec+executor pattern. Demonstrates batched GPU execution with automatic sort-by-length optimization.

## Functions — ColPali

Module: `functions/colpali.py`. Requires `pip install 'cocoindex[colpali]'`. Supports ColPali, ColQwen2, ColQwen2.5, ColSmol model families via `colpali-engine`.

### ColPaliEmbedImage

```python
class ColPaliEmbedImage(op.FunctionSpec):
    model: str
```
[AST:python/cocoindex/functions/colpali.py:L99]

Runtime input: `img_bytes: Bytes`. Returns `Vector[Vector[Float32, N]]` (multi-vector format: variable patches × fixed hidden dimension).

### ColPaliEmbedImageExecutor

```python
@op.executor_class(
    gpu=True, cache=True, batching=True, max_batch_size=32, behavior_version=1,
)
class ColPaliEmbedImageExecutor:
    spec: ColPaliEmbedImage
    _model_info: ColPaliModelInfo
```
[AST:python/cocoindex/functions/colpali.py:L132]

### ColPaliEmbedQuery

```python
class ColPaliEmbedQuery(op.FunctionSpec):
    model: str
```
[AST:python/cocoindex/functions/colpali.py:L178]

Runtime input: `query: Str`. Returns multi-vector `Vector[Vector[Float32, N]]` compatible with `ColPaliEmbedImage` output for late-interaction scoring (MaxSim).

### ColPaliEmbedQueryExecutor

```python
@op.executor_class(
    gpu=True, cache=True, behavior_version=1, batching=True, max_batch_size=32,
)
class ColPaliEmbedQueryExecutor:
    spec: ColPaliEmbedQuery
```
[AST:python/cocoindex/functions/colpali.py:L211]
