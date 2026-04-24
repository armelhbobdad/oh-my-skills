# Connectors

v1.0.0 consolidates v0.3.37's `cocoindex.sources.*` and `cocoindex.targets.*` namespaces into a single `cocoindex.connectors.*` package. Each connector lives in its own sub-package and exposes:

- a typed **target** (or **source**) class
- a **`declare_*_target` / `declare_*_source`** primitive (registers state in the current component context)
- a **`mount_*_target` / `mount_*_source`** helper (sugar over `coco.mount_target` / `coco.mount`)
- a **`*_target(...)` / `*_source(...)`** factory for the underlying `TargetState`
- type helpers (`ColumnDef`, `TableSchema`, `ValueEncoder`)

Each package's `__init__.py` does `from ._source import *` and/or `from ._target import *` — the public surface is the union of those modules' `__all__`.

## Postgres — `cocoindex.connectors.postgres`

`__init__.py` re-exports both `_source` and `_target`. [AST:python/cocoindex/connectors/postgres/__init__.py:L1]

**Target** ([AST:python/cocoindex/connectors/postgres/_target.py:L1378]):
```python
__all__ = [
    "ColumnDef", "ValueEncoder", "PgType", "TableSchema", "TableTarget",
    "create_pool", "declare_table_target", "mount_table_target", "table_target",
]
```

**Source** ([AST:python/cocoindex/connectors/postgres/_source.py:L230]):
```python
__all__ = ["PgSourceSpec", "PgTableSource", "RowFetcher"]
```

Idiom:
```python
from cocoindex.connectors import postgres

PG_DB = coco.ContextKey[asyncpg.Pool]("pg_db")

target = await postgres.mount_table_target(
    PG_DB,
    table_name="doc_embeddings",
    table_schema=await postgres.TableSchema.from_class(DocEmbedding, primary_key=["id"]),
    pg_schema_name="public",  # optional
)
target.declare_vector_index(column="embedding")    # adds a pgvector index entry to the target schema
target.declare_row(row=DocEmbedding(...))          # called from inside @coco.fn
```

## Qdrant — `cocoindex.connectors.qdrant`

Target only. [AST:python/cocoindex/connectors/qdrant/_target.py:L643]
```python
__all__ = [
    "CollectionSchema", "CollectionTarget", "PointStruct", "QdrantVectorDef",
    "collection_target", "create_client",
    "declare_collection_target", "mount_collection_target",
]
```

```python
from cocoindex.connectors import qdrant

target = await qdrant.mount_collection_target(QDRANT_KEY, collection_name="docs",
    collection_schema=qdrant.CollectionSchema(vectors=[qdrant.QdrantVectorDef("embedding", size=384, distance="Cosine")]))
```

## LanceDB — `cocoindex.connectors.lancedb`

Target only. [AST:python/cocoindex/connectors/lancedb/_target.py:L914]
```python
__all__ = [
    "ColumnDef", "LanceAsyncConnection", "LanceType", "TableSchema",
    "TableTarget", "ValueEncoder",
    "connect", "connect_async",
    "declare_table_target", "mount_table_target", "table_target",
]
```

## SurrealDB — `cocoindex.connectors.surrealdb`

Target only. Supports both table and relation targets. [AST:python/cocoindex/connectors/surrealdb/_target.py:L1411]
```python
__all__ = [
    "ColumnDef", "ConnectionFactory",
    "RelationTarget", "SurrealType", "TableSchema", "TableTarget", "ValueEncoder",
    "declare_relation_target", "declare_table_target",
    "mount_relation_target", "mount_table_target",
    "relation_target", "table_target",
]
```

## SQLite — `cocoindex.connectors.sqlite`

Target only. Supports `Vec0TableDef` for sqlite-vec extension. [AST:python/cocoindex/connectors/sqlite/_target.py:L1344]
```python
__all__ = [
    "ColumnDef", "ManagedConnection", "ValueEncoder",
    "SqliteType", "TableSchema", "TableTarget", "Vec0TableDef",
    "connect", "managed_connection",
    "table_target", "declare_table_target", "mount_table_target",
]
```

## Doris — `cocoindex.connectors.doris`

Target only. Supports inverted indexes + vector search. [AST:python/cocoindex/connectors/doris/_target.py:L1373]
```python
__all__ = [
    "ColumnDef", "connect", "connect_async",
    "build_vector_search_query", "declare_table_target",
    "DorisConnectionConfig", "DorisTableTarget", "DorisType",
    "InvertedIndexDef",
    "ManagedConnection",
    "mount_table_target", "RetryConfig", "TableSchema",
    "table_target", "ValueEncoder", "VectorIndexDef",
]
```

## Kafka — `cocoindex.connectors.kafka`

Both source and target.

**Source** ([AST:python/cocoindex/connectors/kafka/_source.py:L391]):
```python
__all__ = ["IsDeleteFn", "topic_as_map"]
```

**Target** ([AST:python/cocoindex/connectors/kafka/_target.py:L327]):
```python
__all__ = [
    "DeletionValueFn", "KafkaTopicTarget",
    "declare_kafka_topic_target", "kafka_topic_target", "mount_kafka_topic_target",
]
```

`kafka.topic_as_map(...)` returns a `LiveMapFeed[K, V]` — pass it to `coco.mount_each` to consume a topic as a streaming feed. Requires `app.update(live=True)`.

## Local filesystem — `cocoindex.connectors.localfs`

Both source and target. [AST:python/cocoindex/connectors/localfs/__init__.py:L1]

**Common** ([AST:python/cocoindex/connectors/localfs/_common.py:L78]): `__all__ = ["FilePath"]`

**Source** ([AST:python/cocoindex/connectors/localfs/_source.py:L263]):
```python
__all__ = ["walk_dir", "File", "DirWalker"]
```

**Target** ([AST:python/cocoindex/connectors/localfs/_target.py:L500]):
```python
__all__ = [
    "DirTarget", "declare_dir_target", "declare_file",
    "dir_target", "mount_dir_target",
]
```

Idiom:
```python
from cocoindex.connectors import localfs
from cocoindex.resources.file import PatternFilePathMatcher

files = localfs.walk_dir(
    sourcedir,
    recursive=True,
    path_matcher=PatternFilePathMatcher(included_patterns=["**/*.md"]),
)
# files is a LiveMapView — supports both one-shot iteration and live mode
await coco.mount_each(process_file, files.items(), target)
```

## Amazon S3 — `cocoindex.connectors.amazon_s3`

Source only. [AST:python/cocoindex/connectors/amazon_s3/_source.py:L12]
```python
__all__ = ["S3File", "S3FilePath", "S3Walker", "get_object", "list_objects", "read"]
```

`S3Walker` is the source counterpart of `localfs.DirWalker` — yields `(key, S3File)` pairs over a bucket+prefix.

## Google Drive — `cocoindex.connectors.google_drive`

Source only. [AST:python/cocoindex/connectors/google_drive/_source.py:L247]
```python
__all__ = [
    "DriveFile", "DriveFileInfo",
    "GoogleDriveSource", "GoogleDriveSourceSpec",
    "list_files",
]
```

## Connector authoring contract

Connector packages all follow the same shape:

1. `_target.py` (or `_source.py`) defines a typed `*Target` class wrapping a `TargetStateProvider`.
2. The module calls `coco.register_root_target_states_provider("my_connector", MyHandler())` once at import.
3. `mount_*_target(key_or_args, ...)` builds a `TargetState` from the registered provider and calls `coco.mount_target(state)`.
4. The returned `*Target` exposes connector-specific methods like `declare_row(...)`, `declare_vector_index(...)`, etc.
5. `__all__` lists every public name (re-exported by the package `__init__.py` via `from ._target import *`).

When writing a new connector, mirror the postgres pattern (`postgres/_target.py`) — it's the most complete reference (1388 lines covering `TableSchema.from_class()`, `ValueEncoder` registration, vector-index declarations, schema migrations, and the `TableTarget` row API).

## Removed v0.3.37 backends not present in v1.0.0

The v0.3.37 connectors **NOT** in v1.0.0:
- `targets.Pinecone` — gone
- `targets.Neo4j` — gone
- `targets.FalkorDB` — gone
- `targets.Ladybug` (ex-Kuzu) — gone
- `targets.Nodes` / `targets.Relationships` (graph builders) — gone
- `targets.Turbopuffer` — gone
- `targets.chromadb.ChromaDB` — gone
- `targets.PostgresSqlCommand` — gone (use `asyncpg.Pool` direct + `coco.lifespan`)
- `sources.AzureBlob` — gone

If you need any of these in v1.0.0, write a connector against the `TargetHandler` / `register_root_target_states_provider` API (see `target-state.md`) or pin to v0.3.37.
