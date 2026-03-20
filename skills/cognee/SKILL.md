---
name: cognee
description: Use when cognee is a Python AI memory engine that transforms
  documents into knowledge graphs with vector and graph storage for semantic
  search and reasoning. Use this skill when writing code that calls cognee's
  Python API (add, cognify, search, memify, config, datasets, prune, session) or
  integrating cognee-mcp. Covers the full public API, SearchType modes,
  DataPoint custom models, pipeline tasks, and configuration for
  LLM/embedding/vector/graph providers. Do NOT use for general knowledge graph
  theory or unrelated Python libraries.
---

## Overview

Cognee v0.5.5 — open-source Python AI memory engine that converts raw data into searchable knowledge graphs combining vector search with graph databases.

- **Source:** [topoteretes/cognee](https://github.com/topoteretes/cognee) @ main
- **Language:** Python (async/await throughout)
- **Forge tier:** Deep (AST + gh + QMD)
- **Public API exports:** 22 | **Total extracted:** 837 (302 functions, 535 classes)
- **Confidence:** 837 T1 (AST-verified), 14 T2 (QMD-enriched), T3 (docs supplemental)

## Quick Start

```python
import cognee
import asyncio

async def main():
    # Reset state
    await cognee.prune.prune_data()
    await cognee.prune.prune_system(metadata=True)

    # 1. Ingest data
    await cognee.add("Cognee turns documents into AI memory.")  # [AST:cognee/api/v1/add/add.py:L22]

    # 2. Build knowledge graph
    await cognee.cognify()  # [AST:cognee/api/v1/cognify/cognify.py:L47]

    # 3. Search
    results = await cognee.search(  # [AST:cognee/api/v1/search/search.py:L26]
        query_text="What does Cognee do?"
    )
    for r in results:
        print(r)

asyncio.run(main())
```

All core functions are **async** — must use `await` inside an async context. `[EXT:docs.cognee.ai/getting-started/quickstart]`

<!-- [MANUAL:additional-notes] -->
<!-- Add custom notes here. This section is preserved during skill updates. -->
<!-- [/MANUAL:additional-notes] -->

## Common Workflows

**Add and process data:**
`await cognee.add(data) → await cognee.cognify() → await cognee.search(query_text)`

**Multi-format ingestion:**
`await cognee.add(["/path/to/file.pdf", "raw text", open("doc.txt","rb")], dataset_name="my_data")`

**Ontology-grounded cognify:**
`config = {"ontology_config": {"ontology_resolver": RDFLibOntologyResolver(ontology_file=path)}}` → `await cognee.cognify(config=config)` `[EXT:docs.cognee.ai/guides/ontology-support]`

**Session-aware search:**
`await cognee.search(query_text="Q1", session_id="conv_1")` → `await cognee.search(query_text="Follow-up", session_id="conv_1")` `[EXT:docs.cognee.ai/guides/sessions]`

**Custom data models:**
`class MyEntity(DataPoint): name: str; metadata = {"index_fields": ["name"]}` → `await add_data_points([entity])` `[EXT:docs.cognee.ai/guides/custom-data-models]`

## Key API Summary

| Function | Purpose | Key Params |
|----------|---------|------------|
| `add()` | Ingest text, files, binary data | `data`, `dataset_name`, `user` | `[AST:cognee/api/v1/add/add.py:L22]` |
| `cognify()` | Build knowledge graph from ingested data | `datasets`, `graph_model`, `chunker`, `temporal_cognify` | `[AST:cognee/api/v1/cognify/cognify.py:L47]` |
| `search()` | Query knowledge graph | `query_text`, `query_type`, `top_k`, `session_id` | `[AST:cognee/api/v1/search/search.py:L26]` |
| `memify()` | Enrich existing graph with custom tasks | `extraction_tasks`, `enrichment_tasks`, `data` | `[AST:cognee/modules/memify/memify.py:L27]` |
| `config.*` | Runtime configuration (LLM, DB, vectors) | static methods | `[AST:cognee/api/v1/config/config.py:L18]` |
| `datasets.*` | List, inspect, delete datasets | static methods | `[AST:cognee/api/v1/datasets/datasets.py:L26]` |
| `prune.*` | Clean up data and system resources | `prune_data()`, `prune_system()` | `[AST:cognee/api/v1/prune/prune.py:L4]` |
| `update()` | Update existing data items | `data_id`, `data`, `dataset_id` | `[AST:cognee/api/v1/update/update.py:L13]` |
| `session.*` | Session history and feedback | `get_session()`, `add_feedback()` | `[SRC:cognee/api/v1/session/__init__.py:L8]` |
| `run_custom_pipeline()` | Execute custom task pipelines | `tasks`, `data`, `dataset` | `[AST:cognee/modules/run_custom_pipeline/run_custom_pipeline.py:L16]` |
| `SearchType` | Enum of 14 search modes | `GRAPH_COMPLETION` (default) | `[AST:cognee/modules/search/types/SearchType.py:L4]` |
| `visualize_graph()` | Render knowledge graph to HTML | `destination_file_path` | `[AST:cognee/api/v1/visualize/visualize.py:L18]` |
| `enable_tracing()` | Enable OpenTelemetry tracing | `console_output` | `[AST:cognee/modules/observability/trace_context.py:L14]` |
| `run_migrations()` | Run Alembic database migrations | — | `[AST:cognee/run_migrations.py:L18]` |
| `start_ui()` | Launch local Cognee UI (frontend + backend + MCP servers) | `pid_callback`, `port`, `start_backend`, `start_mcp` | `[SRC:cognee/api/v1/ui/ui.py]` |
| `cognee_network_visualization()` | Render knowledge graph to interactive HTML | `graph_data`, `destination_file_path` | `[SRC:cognee/modules/visualization/cognee_network_visualization.py:L17]` |
| `pipelines` | Module re-export: Task, run_tasks, run_tasks_parallel, run_pipeline | — | `[SRC:cognee/modules/pipelines/__init__.py:L1]` |

<!-- [MANUAL:additional-notes] -->
<!-- Add custom notes here. This section is preserved during skill updates. -->
<!-- [/MANUAL:additional-notes] -->

## Migration & Deprecation Warnings

- **`delete()`** deprecated since v0.3.9 — use `datasets.delete_data()` instead `[SRC:cognee/api/v1/delete/__init__.py:L13]`
- **`memify()` default pipeline changed** — coding rules replaced with triplet embedding (Mar 2026) `[QMD:cognee-temporal:prs.md]`
- **`update()` bug** — PATCH updates timestamps but GET raw may return old data `[QMD:cognee-temporal:issues.md]`
- **`visualize_graph()` frontend** — open bug #2442: missing component in UI mode `[QMD:cognee-temporal:issues.md]`
- **`start_ui()` v0.5.5 bug** — pip-installed frontend fails with 500 errors due to missing npm deps (react-markdown, ngraph.graph) `[QMD:cognee-temporal:issues.md]`

See Full API Reference for migration details.

## Key Types

**SearchType** (14 modes) `[AST:cognee/modules/search/types/SearchType.py:L4]`:
`GRAPH_COMPLETION` (default), `RAG_COMPLETION`, `CHUNKS`, `SUMMARIES`, `TRIPLET_COMPLETION`, `GRAPH_SUMMARY_COMPLETION`, `CYPHER`, `NATURAL_LANGUAGE`, `GRAPH_COMPLETION_COT`, `GRAPH_COMPLETION_CONTEXT_EXTENSION`, `FEELING_LUCKY`, `TEMPORAL`, `CODING_RULES`, `CHUNKS_LEXICAL`

**Task** — wraps any callable (async/sync/generator) for pipeline execution `[AST:cognee/modules/pipelines/tasks/task.py]`

**DataPoint** — base class for custom graph nodes; inherit and add typed fields `[EXT:docs.cognee.ai/guides/custom-data-models]`

**ChunkStrategy** — `PARAGRAPH`, `SENTENCE`, `LANGCHAIN_CHARACTER` `[AST:cognee/shared/data_models.py:L83]`

## Architecture at a Glance

- **Storage:** Relational (SQLite/Postgres) + Vector (LanceDB/PGVector/Qdrant/Redis/ChromaDB/FalkorDB) + Graph (Kuzu/Neo4j/Neptune/Memgraph)
- **LLM Providers:** OpenAI, Azure OpenAI, Gemini, Anthropic, Ollama, custom (vLLM)
- **Embedding:** OpenAI, Azure, Gemini, Mistral, Ollama, Fastembed
- **Pipeline:** Tasks → Pipelines → run_pipeline (orchestration with async generators)
- **Observability:** OpenTelemetry tracing via `enable_tracing()` / `disable_tracing()`
- **MCP Server:** 7 tools (cognify, search, list_data, delete, prune, cognify_status, save_interaction) `[AST:cognee-mcp/src/server.py]`

## CLI

```bash
cognee --add "data"          # Ingest data
cognee --cognify             # Build knowledge graph
cognee --search "query"      # Search
cognee --debug               # Enable debug logging
cognee --ui                  # Launch local UI
```

`[AST:cognee/cli/_cognee.py:L32]`

## Full API Reference

### add()

```python
async def add(
    data: Union[BinaryIO, list[BinaryIO], str, list[str], DataItem, list[DataItem], Any],
    dataset_name: str = "main_dataset",
    user: User = None,
    node_set: Optional[List[str]] = None,
    vector_db_config: dict = None,
    graph_db_config: dict = None,
    dataset_id: Optional[UUID] = None,
    preferred_loaders: Optional[List[Union[str, dict[str, dict[str, Any]]]]] = None,
    incremental_loading: bool = True,
    data_per_batch: Optional[int] = 20,
    **kwargs,
)
```

`[AST:cognee/api/v1/add/add.py:L22]`

**Parameters:**
| Param | Type | Default | Description |
|-------|------|---------|-------------|
| `data` | Union[str, list, BinaryIO, DataItem, Any] | required | Text, file paths, binary streams, DltResource |
| `dataset_name` | str | `"main_dataset"` | Target dataset name |
| `user` | Optional[User] | None | Auth context (auto-creates default user) |
| `node_set` | Optional[List[str]] | None | Tag data with node set labels |
| `incremental_loading` | bool | True | Skip already-processed data |
| `data_per_batch` | Optional[int] | 20 | Parallel processing batch size |
| `preferred_loaders` | Optional[List] | None | Custom file format loaders |

**Supported inputs:** text strings, absolute paths (`/path/to/file.pdf`), file URLs (`file:///path`), S3 paths (`s3://bucket/file`), binary file objects, lists of mixed types.

**T2 annotation:** v0.5.5 release focused on faster memory ingestion. `[QMD:cognee-temporal:releases.md]`

### cognify()

```python
async def cognify(
    datasets: Union[str, list[str], list[UUID]] = None,
    user: User = None,
    graph_model: BaseModel = KnowledgeGraph,
    chunker=TextChunker,
    chunk_size: int = None,
    chunks_per_batch: int = None,
    config: Config = None,
    vector_db_config: dict = None,
    graph_db_config: dict = None,
    run_in_background: bool = False,
    incremental_loading: bool = True,
    custom_prompt: Optional[str] = None,
    temporal_cognify: bool = False,
    data_per_batch: int = 20,
    **kwargs,
)
```

`[AST:cognee/api/v1/cognify/cognify.py:L47]`

**6-step pipeline:** classify documents → check permissions → extract chunks → extract graph → summarize text → add data points. `[EXT:docs.cognee.ai/core-concepts/main-operations/cognify]`

**Key params:** `graph_model` (custom Pydantic model for extraction), `config` (ontology configuration), `temporal_cognify` (enable temporal event extraction), `custom_prompt` (shape LLM extraction).

**T2 annotation:** Re-cognify after delete may not re-ingest due to pipeline state caching. `[QMD:cognee-temporal:issues.md]`

### search()

```python
async def search(
    query_text: str,
    query_type: SearchType = SearchType.GRAPH_COMPLETION,
    user: Optional[User] = None,
    datasets: Optional[Union[list[str], str]] = None,
    dataset_ids: Optional[Union[list[UUID], UUID]] = None,
    system_prompt_path: str = "answer_simple_question.txt",
    system_prompt: Optional[str] = None,
    top_k: int = 10,
    node_type: Optional[Type] = NodeSet,
    node_name: Optional[List[str]] = None,
    only_context: bool = False,
    session_id: Optional[str] = None,
    wide_search_top_k: Optional[int] = 100,
    triplet_distance_penalty: Optional[float] = 3.5,
    verbose: bool = False,
    retriever_specific_config: Optional[dict] = None,
) -> List[SearchResult]
```

`[AST:cognee/api/v1/search/search.py:L26]`

**Sessions:** `session_id` enables conversational memory (only GRAPH_COMPLETION, RAG_COMPLETION, TRIPLET_COMPLETION). `[EXT:docs.cognee.ai/guides/sessions]`

**Access control:** When `ENABLE_BACKEND_ACCESS_CONTROL=true`, results are per-dataset objects with `dataset_name`, `dataset_id`, `search_result`. `[EXT:docs.cognee.ai/guides/search-basics]`

**T2 annotation:** Feedback-weight-aware graph retrieval added; ChromaDB adapter has unimplemented query params. `[QMD:cognee-temporal:prs.md]`

### memify()

```python
async def memify(
    extraction_tasks: Union[List[Task], List[str]] = None,
    enrichment_tasks: Union[List[Task], List[str]] = None,
    data: Optional[Any] = None,
    dataset: Union[str, UUID] = "main_dataset",
    user: User = None,
    node_type: Optional[Type] = NodeSet,
    node_name: Optional[List[str]] = None,
    vector_db_config: Optional[dict] = None,
    graph_db_config: Optional[dict] = None,
    run_in_background: bool = False,
)
```

`[AST:cognee/modules/memify/memify.py:L27]`

Enrichment pipeline for existing graphs. If no data provided, uses existing graph (optionally filtered by node_type/node_name).

**T2-future:** Default pipeline changed from coding rules to triplet embedding (Mar 2026). `[QMD:cognee-temporal:prs.md]`

### config

Static configuration namespace. `[AST:cognee/api/v1/config/config.py:L18]`

Key methods: `set_llm_api_key(key)`, `set_llm_model(model)`, `set_llm_provider(provider)`, `system_root_directory(path)`, `data_root_directory(path)`, `set_vector_db_provider(provider)`, `set_graph_db_provider(provider)`, `set_embedding_provider(provider)`.

**T2 annotation:** Custom LLM provider endpoint fix for GenericAPIAdapter. `[QMD:cognee-temporal:prs.md]`

### datasets

Static dataset management namespace. `[AST:cognee/api/v1/datasets/datasets.py:L26]`

Methods: `list_datasets(user)`, `discover_datasets(dir_path)`, `list_data(dataset_id, user)`, `get_status(datasets, user)`, `delete_data(dataset_id, data_id, mode, user)`, `delete_dataset(dataset_id, user)`, `empty_dataset(dataset_id, user)`.

### session

`SimpleNamespace(get_session, add_feedback, delete_feedback)` `[SRC:cognee/api/v1/session/__init__.py:L8]`

- `get_session(session_id, last_n, user)` → `List[SessionQAEntry]`
- `add_feedback(session_id, qa_id, feedback_text, score, user)` → records feedback
- `delete_feedback(session_id, qa_id, user)` → removes feedback

### Tracing API

- `enable_tracing(console_output=False)` `[AST:cognee/modules/observability/trace_context.py:L14]`
- `disable_tracing()` `[AST:cognee/modules/observability/trace_context.py:L23]`
- `get_last_trace() -> Optional[CogneeTrace]` `[AST:cognee/modules/observability/trace_context.py:L55]`
- `get_all_traces() -> list[CogneeTrace]` `[AST:cognee/modules/observability/trace_context.py:L63]`
- `clear_traces()` `[AST:cognee/modules/observability/trace_context.py]`

### start_ui()

```python
def start_ui(
    pid_callback: Callable[[int], None],
    port: int = 3000,
    open_browser: bool = True,
    auto_download: bool = False,
    start_backend: bool = False,
    backend_port: int = 8000,
    start_mcp: bool = False,
    mcp_port: int = 8001,
) -> Optional[subprocess.Popen]
```

`[SRC:cognee/api/v1/ui/ui.py]`

Starts the cognee frontend UI server, optionally with the backend API server and MCP server. Downloads and caches frontend assets from GitHub releases if not found locally. Requires Node.js and npm.

**Parameters:**
| Param | Type | Default | Description |
|-------|------|---------|-------------|
| `pid_callback` | Callable[[int], None] | required | Callback notified with PID of each spawned process |
| `port` | int | 3000 | Frontend server port |
| `open_browser` | bool | True | Auto-open browser on start |
| `auto_download` | bool | False | Download frontend without prompting |
| `start_backend` | bool | False | Also start the cognee API backend server |
| `backend_port` | int | 8000 | Backend server port |
| `start_mcp` | bool | False | Also start the cognee MCP server via Docker |
| `mcp_port` | int | 8001 | MCP server port |

**T2 annotation:** v0.5.5 pip install has known 500 error due to missing npm dependencies in cognee-frontend. `[QMD:cognee-temporal:issues.md]`

### cognee_network_visualization()

```python
async def cognee_network_visualization(
    graph_data,
    destination_file_path: str = None,
)
```

`[SRC:cognee/modules/visualization/cognee_network_visualization.py:L17]`

Renders knowledge graph to interactive HTML visualization with color-coded node types. Takes graph data tuple `(nodes_data, edges_data)` from graph traversal.

**Parameters:**
| Param | Type | Default | Description |
|-------|------|---------|-------------|
| `graph_data` | tuple | required | Tuple of `(nodes_data, edges_data)` from graph database |
| `destination_file_path` | str | None | Output file path for the HTML visualization |

**T2 annotation:** Open bug #2442 — frontend visualization component missing when used through UI mode. `[QMD:cognee-temporal:targeted-issues.md]`

## Full Type Definitions

### SearchType `[AST:cognee/modules/search/types/SearchType.py:L4]`

```python
class SearchType(str, Enum):
    SUMMARIES = "SUMMARIES"               # Vector similarity on TextSummary nodes
    CHUNKS = "CHUNKS"                     # Vector similarity on DocumentChunk nodes
    RAG_COMPLETION = "RAG_COMPLETION"     # LLM-backed with chunk context
    TRIPLET_COMPLETION = "TRIPLET_COMPLETION"  # Graph triplet-based retrieval
    GRAPH_COMPLETION = "GRAPH_COMPLETION" # Default — LLM + graph traversal
    GRAPH_SUMMARY_COMPLETION = "GRAPH_SUMMARY_COMPLETION"
    CYPHER = "CYPHER"                     # Raw Cypher query
    NATURAL_LANGUAGE = "NATURAL_LANGUAGE" # NL → Cypher translation
    GRAPH_COMPLETION_COT = "GRAPH_COMPLETION_COT"  # Chain-of-thought graph
    GRAPH_COMPLETION_CONTEXT_EXTENSION = "GRAPH_COMPLETION_CONTEXT_EXTENSION"
    FEELING_LUCKY = "FEELING_LUCKY"       # Single best result
    TEMPORAL = "TEMPORAL"                 # Time-aware search
    CODING_RULES = "CODING_RULES"         # Code rule retrieval
    CHUNKS_LEXICAL = "CHUNKS_LEXICAL"     # BM25 keyword search on chunks
```

### DataPoint `[EXT:docs.cognee.ai/guides/custom-data-models]`

Base class for all graph nodes. Inherits from Pydantic BaseModel. Set `metadata = {"index_fields": ["field"]}` for vector indexing. Use `Edge(weight, relationship_type)` for weighted relationships.

Notable subclasses: `DocumentChunk`, `TextSummary`, `CodeSummary`, `DatabaseSchema`, `SchemaTable`, `TranslatedContent`, `GraphitiNode`, `WebPage`.

### Task `[AST:cognee/modules/pipelines/tasks/task.py]`

```python
class Task:
    def __init__(self, executable, *args, task_config=None, **kwargs)
```

Wraps any callable (async/sync function, generator, async generator). Use `task_config={"batch_size": N}` for parallel processing. Decorate with `@task_summary("Processed {n} items")` for pipeline reporting.

### Pipeline Exports `[SRC:cognee/modules/pipelines/__init__.py:L1]`

`Task`, `run_tasks`, `run_tasks_parallel`, `run_pipeline`

## Full Integration Patterns

### Co-import Patterns

- **pydantic** — `BaseModel` for graph models, `BaseSettings` for config
- **sqlalchemy** — relational storage layer (async sessions)
- **fastapi** — HTTP API server for deployment
- **uuid** — dataset and data item identifiers
- **asyncio** — all core operations are async

### MCP Server Integration `[AST:cognee-mcp/src/server.py]`

7 MCP tools: `cognify(data, graph_model_file, graph_model_name, custom_prompt)`, `search(search_query, search_type, top_k)`, `save_interaction(...)`, `list_data(dataset_id)`, `delete(data_id, dataset_id, mode)`, `prune()`, `cognify_status()`.

Runs via `FastMCP("Cognee")`. Supports SSE and streamable HTTP transports with CORS.

### Provider Configuration `[EXT:docs.cognee.ai/setup-configuration/overview]`

Configure via `.env` or `cognee.config.*` methods:
- **LLM:** `LLM_API_KEY`, `LLM_MODEL`, `LLM_PROVIDER` (openai/azure/gemini/anthropic/ollama/custom)
- **Embedding:** `EMBEDDING_PROVIDER`, `EMBEDDING_MODEL`
- **Vector:** `VECTOR_DB_PROVIDER` (lancedb/pgvector/qdrant/redis/chromadb/falkordb)
- **Graph:** `GRAPH_DB_PROVIDER` (kuzu/neo4j/neptune/memgraph)
- **Debug:** `LOG_LEVEL=DEBUG`, `TELEMETRY_DISABLED=true`
