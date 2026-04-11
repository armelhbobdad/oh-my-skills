---
name: oms-cognee
description: >
  Builds apps on top of cognee v0.5.8, the knowledge-graph memory engine for AI agents.
  Use when ingesting text/files/URLs into persistent agent memory, building knowledge
  graphs with entities and relationships, searching graph-backed memory with multiple
  search modes (GRAPH_COMPLETION, CHUNKS, SUMMARIES, TEMPORAL, CYPHER, CODING_RULES),
  enriching existing graphs with memify, scoping memory with datasets and node_sets,
  configuring LLM/embedding/graph/vector backends, running custom task pipelines,
  tracing cognee operations, or visualizing the resulting graph. Covers the top-level
  exports from cognee/__init__.py: add, cognify, search, memify, datasets, prune,
  update, run_custom_pipeline, config, SearchType, visualize_graph, and the tracing
  API. Do NOT use for: cognee internals (cognify task implementation, graph adapters),
  the HTTP REST API (use cognee-mcp or the FastAPI server instead), non-cognee memory
  or RAG libraries.
---

# oms-cognee

## Overview

**Cognee** is an open-source knowledge-graph memory engine for AI agents. It combines a vector store (semantic search), a graph store (entities + relationships), and a relational store (provenance) into a single three-layer memory architecture. The canonical workflow is **`add → cognify → search`**: ingest data, build a knowledge graph, then query it.

- **Source:** [topoteretes/cognee](https://github.com/topoteretes/cognee) @ `v0.5.8` (commit `b51dcce`) `[SRC:pyproject.toml:L4]`
- **Language:** Python >=3.10, <3.14 `[SRC:pyproject.toml:L10]`
- **Forge tier:** Deep (AST + ccc + QMD + docs fetch)
- **Public exports:** 25 top-level names in `cognee/__init__.py` `[AST:cognee/__init__.py:L1]`
- **Confidence:** All T1 (AST-verified from source clone)
- **Async model:** Cognee is **async-first** — nearly all top-level functions are coroutines and must be `await`ed `[EXT:https://docs.cognee.ai/getting-started/quickstart]`

## Quick Start

```python
import asyncio
import cognee
from cognee import SearchType

async def main():
    # (optional) start from a clean slate
    await cognee.prune.prune_data()
    await cognee.prune.prune_system(metadata=True)

    # 1) Ingest data — text, file path, URL, or list of any of those
    await cognee.add(
        "Cognee turns documents into AI memory.",
        dataset_name="main_dataset",
    )

    # 2) Build the knowledge graph
    await cognee.cognify(datasets="main_dataset")

    # 3) Query the graph with graph-backed LLM completion (default)
    results = await cognee.search(
        query_text="What does Cognee do?",
        query_type=SearchType.GRAPH_COMPLETION,
    )
    for r in results:
        print(r)

if __name__ == "__main__":
    asyncio.run(main())
```

Signatures: `[AST:cognee/api/v1/add/add.py:L21]` · `[AST:cognee/api/v1/cognify/cognify.py:L44]` · `[AST:cognee/api/v1/search/search.py:L27]`

Before running, set `LLM_API_KEY` for graph extraction and completion; Cognee defaults to OpenAI but supports litellm-compatible providers (Anthropic, Gemini, Ollama, etc.) via `cognee.config.set_llm_provider(...)` and friends. `[AST:cognee/api/v1/config/config.py:L141]` · `[SRC:cognee/api/v1/add/add.py:L166]`

<!-- [MANUAL:quick-start-notes] -->
<!-- Add project-specific quick-start notes here. Preserved during skill updates. -->
<!-- [/MANUAL:quick-start-notes] -->

## Common Workflows

**Add and process data:**
`await cognee.add(data, dataset_name="main") → await cognee.cognify(datasets="main") → await cognee.search(query_text=..., datasets="main")` `[AST:cognee/api/v1/add/add.py:L21]`

**Scope memory per tenant / customer / workflow with node_set:**
`await cognee.add(data, dataset_name="agent_memory", node_set=["customer_123", "preferences"]) → await cognee.cognify(datasets="agent_memory") → await cognee.search(query_text=..., datasets="agent_memory", node_name=["customer_123"])` `[SRC:cognee/skill.md:L97]`

**Enrich an existing graph with memify:**
`await cognee.add(...) → await cognee.cognify(...) → await cognee.memify(dataset="rules_demo") → await cognee.search(query_type=SearchType.CODING_RULES, node_name=["coding_agent_rules"])` — memify creates `Rule` nodes with `rule_associated_from` edges grouped under the `coding_agent_rules` node_set. `[AST:cognee/modules/memify/memify.py:L25]` · `[EXT:https://docs.cognee.ai/guides/memify-quickstart]`

**Run a custom task pipeline:**
`from cognee.modules.pipelines import Task, run_pipeline; tasks = [Task(extract_people), Task(add_data_points)]; async for _ in run_pipeline(tasks=tasks, data=text, datasets=["people_demo"]): pass` `[AST:cognee/modules/pipelines/__init__.py:L1]` · `[EXT:https://docs.cognee.ai/guides/custom-tasks-pipelines]`

**Insert structured DataPoints directly (skip cognify):**
`from cognee.low_level import DataPoint; from cognee.tasks.storage import add_data_points; await add_data_points([person1, person2])` — field assignment between DataPoints becomes a graph edge; use `Edge(weight=..., relationship_type=...)` for custom edge metadata. `[AST:cognee/low_level.py:L1]` · `[EXT:https://docs.cognee.ai/guides/custom-data-models]`

**Visualize the graph:**
`await cognee.visualize_graph("/path/to/graph.html")` — writes an interactive HTML visualization. `[AST:cognee/api/v1/visualize/visualize.py:L17]`

## Key API Summary

| Export | Kind | Key params | Source |
|---|---|---|---|
| `cognee.add` | async fn | `data, dataset_name="main_dataset", node_set=None, dataset_id=None, incremental_loading=True, data_per_batch=20, importance_weight=0.5` | `[AST:cognee/api/v1/add/add.py:L21]` |
| `cognee.cognify` | async fn | `datasets=None, graph_model=KnowledgeGraph, chunker=TextChunker, chunk_size=None, temporal_cognify=False, custom_prompt=None, run_in_background=False` | `[AST:cognee/api/v1/cognify/cognify.py:L44]` |
| `cognee.search` | async fn | `query_text, query_type=SearchType.GRAPH_COMPLETION, datasets=None, top_k=10, node_name=None, only_context=False, session_id=None, verbose=False` | `[AST:cognee/api/v1/search/search.py:L27]` |
| `cognee.memify` | async fn | `extraction_tasks=None, enrichment_tasks=None, data=None, dataset="main_dataset", node_name=None, run_in_background=False` | `[AST:cognee/modules/memify/memify.py:L25]` |
| `cognee.update` | async fn | `data_id, data, dataset_id, node_set=None, preferred_loaders=None, incremental_loading=True` | `[AST:cognee/api/v1/update/update.py:L12]` |
| `cognee.run_custom_pipeline` | async fn | `tasks=None, data=None, dataset="main_dataset", pipeline_name="custom_pipeline", run_in_background=False` | `[AST:cognee/modules/run_custom_pipeline/run_custom_pipeline.py:L14]` |
| `cognee.prune` | class (ns) | `.prune_data()`, `.prune_system(graph=True, vector=True, metadata=False, cache=True)` — all async | `[AST:cognee/api/v1/prune/prune.py:L4]` |
| `cognee.datasets` | class (ns) | `.list_datasets()`, `.list_data(dataset_id)`, `.has_data(dataset_id)`, `.get_status([ids])`, `.empty_dataset(id)`, `.delete_data(dataset_id, data_id, mode="soft")`, `.delete_all()` — all async | `[AST:cognee/api/v1/datasets/datasets.py:L25]` |
| `cognee.config` | class (ns) | `set_llm_provider`, `set_llm_model`, `set_llm_api_key`, `set_embedding_provider`, `set_embedding_model`, `set_embedding_dimensions`, `set_vector_db_provider`, `set_graph_database_provider`, `system_root_directory`, ... (32 static methods) | `[AST:cognee/api/v1/config/config.py:L18]` |
| `cognee.SearchType` | enum | 14 modes: `GRAPH_COMPLETION` (default), `RAG_COMPLETION`, `CHUNKS`, `CHUNKS_LEXICAL`, `SUMMARIES`, `TEMPORAL`, `CODING_RULES`, `CYPHER`, `NATURAL_LANGUAGE`, `FEELING_LUCKY`, `TRIPLET_COMPLETION`, `GRAPH_SUMMARY_COMPLETION`, `GRAPH_COMPLETION_COT`, `GRAPH_COMPLETION_CONTEXT_EXTENSION` | `[AST:cognee/modules/search/types/SearchType.py:L4]` |
| `cognee.visualize_graph` | async fn | `destination_file_path=None` → returns HTML str. For lower-level use (when you already have graph data), see `cognee.cognee_network_visualization(graph_data, destination_file_path=None)` in `references/full-api-reference.md`. | `[AST:cognee/api/v1/visualize/visualize.py:L17]` · `[AST:cognee/modules/visualization/cognee_network_visualization.py:L22]` |
| `cognee.enable_tracing` / `disable_tracing` / `get_last_trace` / `get_all_traces` / `clear_traces` | sync fns | OpenTelemetry in-memory tracing (5 functions) | `[AST:cognee/modules/observability/trace_context.py:L16]` |
| `cognee.pipelines` | module | Re-exports `Task`, `run_tasks`, `run_tasks_parallel`, `run_pipeline` from `cognee.modules.pipelines` | `[AST:cognee/pipelines.py:L5]` |
| `cognee.low_level` | module | `DataPoint` (aliased from `ExtendableDataPoint`), `setup()` — primitives for custom-pipeline authors | `[AST:cognee/low_level.py:L1]` |
| `cognee.session` | module | Session-scoped Q&A helpers — `get_session`, `add_feedback`, `delete_feedback` (all async). Access via `cognee.session.<fn>`. See `references/full-api-reference.md` for signatures. | `[AST:cognee/api/v1/session/session.py:L1]` |
| `cognee.run_migrations` | async fn | Runs Alembic migrations bundled with the installed package | `[AST:cognee/run_migrations.py:L16]` |
| `cognee.__version__` | str | Package version string (e.g., `"0.5.8"`) — resolved at import time via `get_cognee_version()`. Use for version-gated code paths. | `[AST:cognee/__init__.py:L6]` |

## Deprecations & Gotchas

> Current-state deprecations and source/docs discrepancies surfaced during extraction — not forward-looking breaking changes. v0.5.8 introduces no breaking changes over v0.5.7.

- **`cognee.delete(data_id, dataset_id, mode="soft", user=None)` is deprecated since cognee v0.3.9.** Use `await cognee.datasets.delete_data(dataset_id=..., data_id=...)` instead. The old function still works and delegates to `datasets.delete_data`, but is decorated with `@deprecated`. `[AST:cognee/api/v1/delete/delete.py:L10]`
- **v0.5.8 has no breaking changes.** Release is a stability/bugfix update over v0.5.7: fixed duplicate memories after sync, resolved search timeouts, fixed auth token refresh. `[QMD:oms-cognee-temporal:releases.md]`
- **`cognee.start_ui` is sync (not async) and requires a `pid_callback` positional argument.** Do not call `await cognee.start_ui()` — the function returns `Optional[subprocess.Popen]` synchronously. Signature: `start_ui(pid_callback, port=3000, open_browser=True, auto_download=False, start_backend=False, backend_port=8000, start_mcp=False, mcp_port=8001)`. `[AST:cognee/api/v1/ui/ui.py:L369]`
- **`cognee.start_visualization_server` is a module, not a function.** The top-level `__init__.py` re-imports the submodule name. To start the visualization HTTP server, call `cognee.start_visualization_server.visualization_server(port)` which is synchronous. `[AST:cognee/api/v1/visualize/start_visualization_server.py:L6]`

See Full API Reference for complete parameter tables and behavioral notes.

## Key Types

### `SearchType` (enum) — `cognee.SearchType`

All modes accepted by `cognee.search(query_type=...)`:

| Mode | Use for |
|---|---|
| `GRAPH_COMPLETION` (default) | LLM answer backed by graph context — best default for Q&A |
| `RAG_COMPLETION` | Traditional chunk-based RAG without graph structure |
| `CHUNKS` | Raw semantic chunk retrieval, no LLM |
| `CHUNKS_LEXICAL` | Token/BM25-style exact-term chunk search |
| `SUMMARIES` | Pre-generated hierarchical document summaries |
| `TRIPLET_COMPLETION` | Subject-predicate-object graph Q&A |
| `GRAPH_SUMMARY_COMPLETION` | Graph + summaries hybrid |
| `GRAPH_COMPLETION_COT` | Deeper reasoning with chain-of-thought over graph |
| `GRAPH_COMPLETION_CONTEXT_EXTENSION` | Broader graph context retrieval |
| `CYPHER` | Raw Cypher queries (enable in config) |
| `NATURAL_LANGUAGE` | Natural-language → graph query translation |
| `TEMPORAL` | Time-aware graph search (pairs with `temporal_cognify=True`) |
| `CODING_RULES` | Queries against `coding_agent_rules` node_set (populated by memify defaults) |
| `FEELING_LUCKY` | Cognee auto-selects the best search type |

`[AST:cognee/modules/search/types/SearchType.py:L4]`

### `Task` — `cognee.pipelines.Task`

Constructor: `Task(executable, *args, task_config=None, **kwargs)`. Wraps any callable (function, coroutine function, generator, or async generator). Detects type via `inspect` and picks the right execute path. `task_config={"batch_size": N}` controls batching. `[AST:cognee/modules/pipelines/tasks/task.py:L24]`

### `DataPoint` — `cognee.low_level.DataPoint`

Alias for `cognee.infrastructure.engine.ExtendableDataPoint`. Pydantic base class for graph-native entities. Assigning one `DataPoint` instance to another's field creates an edge; the field name becomes the edge label. Use `metadata = {"index_fields": [...]}` to mark which fields should be embedded in the vector store. `[AST:cognee/low_level.py:L1]` · `[EXT:https://docs.cognee.ai/guides/custom-data-models]`

### Exceptions — `cognee.exceptions`

- `CogneeApiError` — base class (HTTP 418 default)
- `CogneeSystemError` — 500
- `CogneeValidationError` — 422
- `CogneeConfigurationError` — 500
- `CogneeTransientError` — 503

All accept `(message, name, status_code, log, log_level)`. `[AST:cognee/exceptions/exceptions.py:L7]`

## Architecture at a Glance

- **Three-layer storage with node_set-aware graph:** relational (provenance), vector (semantic), graph (entities + edges + `node_set` tagging). `node_set` tags passed to `cognee.add` become first-class graph nodes after `cognify`. `[EXT:https://docs.cognee.ai/core-concepts/overview]`
- **Default backends (pinned in `pyproject.toml`):** LLM via `litellm` / `openai` / `instructor`; vector `lancedb` + `pylance`; graph `kuzu==0.11.3` + `networkx`; relational `sqlalchemy` + `aiosqlite` + `alembic`. Optional extras: `neo4j`, `postgres` (`pgvector`+`asyncpg`), `fastembed`, `scraping`, `distributed` (Modal). `[SRC:pyproject.toml:L22]`
- **Async-first:** every ingestion/graph/search/memify/update function is a coroutine — call via `await` from inside an `async def` and drive with `asyncio.run(main())`. The sole exceptions are `start_ui`, `start_visualization_server.visualization_server`, and the `enable_tracing`/`disable_tracing`/`get_*_trace`/`clear_traces` family.

## CLI

Cognee ships a CLI (`cognee-cli`) for terminal usage, but it lives outside this skill's scope. Quick reference from the upstream repo:

```
cognee-cli add "Cognee turns documents into AI memory."
cognee-cli cognify
cognee-cli search "What does cognee do?"
cognee-cli -ui   # Launches UI, backend API, and MCP server together
```

`[SRC:AGENTS.md:L40]` — use this skill for the Python API only; reach for `cognee-cli` or `cognee-mcp` for CLI/MCP flows.

<!-- [MANUAL:additional-notes] -->
<!-- Add custom notes here. This section is preserved during skill updates. -->
<!-- [/MANUAL:additional-notes] -->

---

**Full API details, complete type definitions, and integration patterns:** see [references/full-api-reference.md](references/full-api-reference.md). Detailed config setter reference: [references/config.md](references/config.md). Extended core-workflow walkthrough with env matrix: [references/core-workflow.md](references/core-workflow.md). Custom pipelines and DataPoint primitives: [references/pipelines-and-datapoints.md](references/pipelines-and-datapoints.md).
