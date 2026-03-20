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

### Setup Requirements

**Python:** >=3.10, <3.14. Recommended installer: `uv`.

```bash
uv pip install -e "."                    # minimal (SQLite + LanceDB + Kuzu)
uv pip install -e ".[postgres,neo4j]"    # with PostgreSQL + Neo4j
```

**Key installation extras:** `postgres` / `postgres-binary`, `neo4j`, `neptune`, `chromadb`, `qdrant`, `redis`, `ollama`, `anthropic`, `gemini`, `mistral`, `groq`, `huggingface`, `llama-cpp`, `aws` (S3), `langchain`, `llama-index`, `graphiti`, `baml`, `dlt`, `docling`, `codegraph`, `scraping`, `docs`, `monitoring` (Sentry+Langfuse), `distributed` (Modal), `dev`, `debug`.

**Minimal .env:**
```bash
LLM_API_KEY="your_openai_api_key"
LLM_MODEL="openai/gpt-4o-mini"
```

Defaults (no extra setup): SQLite (relational), LanceDB (vector), Kuzu (graph). All stored in `.venv` by default — override with `DATA_ROOT_DIRECTORY` and `SYSTEM_ROOT_DIRECTORY`.

**Important:** If you configure only LLM or only embeddings, the other defaults to OpenAI. Always configure both, or ensure a valid OpenAI API key.

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

### LLM Provider Configuration

Configure via `.env` — provider-specific examples:

```bash
# Azure OpenAI
LLM_PROVIDER="azure"
LLM_MODEL="azure/gpt-4o-mini"
LLM_ENDPOINT="https://YOUR-RESOURCE.openai.azure.com/openai/deployments/gpt-4o-mini"
LLM_API_KEY="your_key"
LLM_API_VERSION="2024-12-01-preview"

# Anthropic (requires: pip install cognee[anthropic])
LLM_PROVIDER="anthropic"
LLM_MODEL="claude-3-5-sonnet-20241022"
LLM_API_KEY="your_key"

# Ollama (requires: pip install cognee[ollama])
LLM_PROVIDER="ollama"
LLM_MODEL="llama3.1:8b"
LLM_ENDPOINT="http://localhost:11434/v1"
LLM_API_KEY="ollama"
EMBEDDING_PROVIDER="ollama"
EMBEDDING_MODEL="nomic-embed-text:latest"
EMBEDDING_ENDPOINT="http://localhost:11434/api/embed"
HUGGINGFACE_TOKENIZER="nomic-ai/nomic-embed-text-v1.5"

# AWS Bedrock (requires: pip install cognee[aws])
LLM_PROVIDER="bedrock"
LLM_MODEL="anthropic.claude-3-sonnet-20240229-v1:0"
AWS_REGION="us-east-1"

# Custom / OpenRouter / vLLM
LLM_PROVIDER="custom"
LLM_MODEL="openrouter/google/gemini-2.0-flash-lite-preview-02-05:free"
LLM_ENDPOINT="https://openrouter.ai/api/v1"
```

**Rate limiting:** `LLM_RATE_LIMIT_ENABLED=true`, `LLM_RATE_LIMIT_REQUESTS=60`, `LLM_RATE_LIMIT_INTERVAL=60`

**Structured output:** `STRUCTURED_OUTPUT_FRAMEWORK="instructor"` (default) or `"baml"` (requires `cognee[baml]`). Override instructor mode: `LLM_INSTRUCTOR_MODE="json_schema_mode"`.

### Database Switching

```bash
# PostgreSQL (requires: pip install cognee[postgres])
DB_PROVIDER=postgres
DB_HOST=localhost  DB_PORT=5432  DB_USERNAME=cognee  DB_PASSWORD=cognee  DB_NAME=cognee_db

# PGVector (requires: pip install cognee[postgres])
VECTOR_DB_PROVIDER=pgvector
VECTOR_DB_URL=postgresql://cognee:cognee@localhost:5432/cognee_db

# Neo4j (requires: pip install cognee[neo4j])
GRAPH_DATABASE_PROVIDER=neo4j
GRAPH_DATABASE_URL=bolt://localhost:7687
GRAPH_DATABASE_USERNAME=neo4j  GRAPH_DATABASE_PASSWORD=yourpassword

# S3 storage (requires: pip install cognee[aws])
STORAGE_BACKEND="s3"
STORAGE_BUCKET_NAME="your-bucket"
DATA_ROOT_DIRECTORY="s3://your-bucket/cognee/data"
```

### Security Environment Variables

```bash
ACCEPT_LOCAL_FILE_PATH=True     # Allow local file paths in add()
ALLOW_HTTP_REQUESTS=True        # Allow HTTP fetches
ALLOW_CYPHER_QUERY=True         # Allow raw Cypher in SearchType.CYPHER
REQUIRE_AUTHENTICATION=False    # Enable API auth
ENABLE_BACKEND_ACCESS_CONTROL=True  # Multi-tenant dataset isolation
```

### Extension Patterns

**Custom pipeline task:**
```python
from cognee.modules.pipelines.tasks.Task import Task

async def my_task(data):
    return process(data)

task = Task(my_task)
```

**Direct database access:**
```python
from cognee.infrastructure.databases.graph import get_graph_engine
from cognee.infrastructure.databases.vector import get_vector_engine

graph_engine = await get_graph_engine()
vector_engine = await get_vector_engine()
```

**LLM Gateway (structured output):**
```python
from cognee.infrastructure.llm.get_llm_client import get_llm_client

llm_client = get_llm_client()
response = await llm_client.acreate_structured_output(
    text_input="prompt", system_prompt="instructions", response_model=YourPydanticModel
)
```

### MCP Server Transport Modes

```bash
python src/server.py                    # stdio (default)
python src/server.py --transport sse    # SSE
python src/server.py --transport http --host 127.0.0.1 --port 8000 --path /mcp
# API mode (connect to running Cognee API):
python src/server.py --transport sse --api-url http://localhost:8000 --api-token TOKEN
```

Docker: `docker run -e TRANSPORT_MODE=sse --env-file .env -p 8000:8000 cognee/cognee-mcp:main`

### Common Troubleshooting

- **Ollama + OpenAI embeddings NoDataError** — configure both LLM and embedding to same provider, or set `HUGGINGFACE_TOKENIZER`
- **LM Studio structured output** — set `LLM_INSTRUCTOR_MODE="json_schema_mode"`
- **Default provider fallback** — configuring only LLM or only embeddings defaults the other to OpenAI
- **Permission denied on search** — returns empty list (not error) to prevent info leakage; check dataset permissions
- **Docker DB connections** — use `DB_HOST=host.docker.internal` for local databases
- **Debug logging** — `LITELLM_LOG="DEBUG"`, `ENV="development"`, `TELEMETRY_DISABLED=1`

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

See [references/full-api-reference.md](references/full-api-reference.md) for complete signatures with parameters, return types, and T2 annotations for all 22 exports.

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
