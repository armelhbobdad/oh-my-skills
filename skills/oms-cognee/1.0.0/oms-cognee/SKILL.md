---
name: oms-cognee
description: >
  Builds apps on top of cognee v1.0.0, the knowledge-graph memory engine for AI agents.
  Use when ingesting text/files/URLs into persistent memory, building knowledge graphs,
  searching graph-backed memory with multiple SearchType modes, enriching graphs with
  memify/improve, scoping memory with datasets and node_sets, configuring LLM/embedding/
  graph/vector backends, running custom task pipelines, tracing operations, decorating
  agent entrypoints with `agent_memory`, connecting to Cognee Cloud with `serve`, or
  visualizing the graph. Covers cognee/__init__.py exports: the V1 API (add, cognify,
  search, memify, datasets, prune, update, run_custom_pipeline, config, SearchType,
  visualize_graph, pipelines, Drop, run_startup_migrations, tracing) and the V2
  memory-oriented API (remember, RememberResult, recall, improve, forget, serve,
  disconnect, visualize, agent_memory). Do NOT use for: cognee internals, the HTTP
  REST API (use cognee-mcp or the FastAPI server), non-cognee memory/RAG libraries.
---

# oms-cognee

## Overview

**Cognee** is an open-source knowledge-graph memory engine for AI agents. It combines a vector store (semantic search), a graph store (entities + relationships), and a relational store (provenance) into a single three-layer memory architecture. The canonical V1 workflow is **`add → cognify → search`**: ingest data, build a knowledge graph, then query it. The new **V2 memory-oriented API** wraps this as **`remember → recall`** with an optional `improve`/`forget`/`serve`/`agent_memory` layer for agent contexts.

- **Source:** [topoteretes/cognee](https://github.com/topoteretes/cognee) @ `v1.0.0` (commit `3c048aa4`) `[SRC:pyproject.toml:L4]`
- **Language:** Python >=3.10, <3.14 `[SRC:pyproject.toml:L10]`
- **Forge tier:** Deep (AST + ccc + QMD + docs fetch)
- **Public exports:** 34 top-level names in `cognee/__init__.py` `[AST:cognee/__init__.py:L1]`
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

**V2 memory-oriented shortcut** (same workflow, simpler API):

```python
import asyncio
import cognee

async def main():
    result = await cognee.remember("Cognee turns documents into AI memory.")
    print(result)  # RememberResult — await it to block until cognify completes
    answers = await cognee.recall("What does Cognee do?")
    for a in answers:
        print(a)

if __name__ == "__main__":
    asyncio.run(main())
```

Signatures: `[AST:cognee/api/v1/add/add.py:L22]` · `[AST:cognee/api/v1/cognify/cognify.py:L44]` · `[AST:cognee/api/v1/search/search.py:L26]` · `[AST:cognee/api/v1/remember/remember.py:L339]` · `[AST:cognee/api/v1/recall/recall.py:L122]`

Before running, set `LLM_API_KEY` for graph extraction and completion; Cognee defaults to OpenAI but supports litellm-compatible providers (Anthropic, Gemini, Ollama, etc.) via `cognee.config.set_llm_provider(...)` and friends. `[AST:cognee/api/v1/config/config.py:L141]` · `[SRC:cognee/api/v1/add/add.py:L166]`

<!-- [MANUAL:quick-start-notes] -->
<!-- Add project-specific quick-start notes here. Preserved during skill updates. -->
<!-- [/MANUAL:quick-start-notes] -->

## Common Workflows

**V1 — Add and process data:**
`await cognee.add(data, dataset_name="main") → await cognee.cognify(datasets="main") → await cognee.search(query_text=..., datasets="main")` `[AST:cognee/api/v1/add/add.py:L22]`

**V2 — Remember and recall:**
`await cognee.remember(data, dataset_name="main") → await cognee.recall(query_text="...")` — wraps add+cognify into one call and search+auto-routing into another. `[AST:cognee/api/v1/remember/remember.py:L339]` · `[AST:cognee/api/v1/recall/recall.py:L122]`

**Scope memory per tenant / customer / workflow with node_set:**
`await cognee.add(data, dataset_name="agent_memory", node_set=["customer_123", "preferences"]) → await cognee.cognify(datasets="agent_memory") → await cognee.search(query_text=..., datasets="agent_memory", node_name=["customer_123"])` `[SRC:cognee/skill.md:L97]`

**Enrich an existing graph with memify (V1) or improve (V2):**
`await cognee.add(...) → await cognee.cognify(...) → await cognee.memify(dataset="rules_demo") → await cognee.search(query_type=SearchType.CODING_RULES, node_name=["coding_agent_rules"])` — memify creates `Rule` nodes with `rule_associated_from` edges. Equivalent V2: `await cognee.improve(dataset="rules_demo", session_ids=[...])` which additionally applies feedback weights from past session Q&A. `[AST:cognee/modules/memify/memify.py:L25]` · `[AST:cognee/api/v1/improve/improve.py:L36]`

**Delete data (V2):**
`await cognee.forget(data_id=..., dataset=...)` — single deletion command that replaces prune/delete/empty_dataset; supports `everything=True` to wipe all user data. `[AST:cognee/api/v1/forget/forget.py:L15]`

**Connect to Cognee Cloud:**
`await cognee.serve(url="https://my-instance.cognee.ai", api_key="ck_...")` — routes subsequent `remember`/`recall`/`improve`/`forget`/`visualize` calls through the remote instance. `await cognee.disconnect()` returns to local mode. `[AST:cognee/api/v1/serve/serve.py:L17]` · `[AST:cognee/api/v1/serve/disconnect.py:L8]`

**Decorate an async agent entrypoint with memory context:**
`@cognee.agent_memory(with_memory=True, save_traces=True, memory_query_from_method="question", memory_top_k=5)` — retrieves relevant memory context before the call and persists a trace after. `[AST:cognee/modules/agent_memory/decorator.py:L22]`

**Run a custom task pipeline:**
`from cognee.modules.pipelines import Task, run_pipeline; tasks = [Task(extract_people), Task(add_data_points)]; async for _ in run_pipeline(tasks=tasks, data=text, datasets=["people_demo"]): pass` `[AST:cognee/modules/pipelines/__init__.py:L1]` · `[EXT:https://docs.cognee.ai/guides/custom-tasks-pipelines]`

**Filter pipeline items with `Drop`:**
`from cognee import Drop; async def skip_short(text): return Drop if len(text) < 10 else text` — returning `Drop` from any pipeline step removes that item from the stream. `[AST:cognee/pipelines/types.py:L32]`

**Visualize the graph:**
`await cognee.visualize_graph("/path/to/graph.html")` — writes an interactive HTML visualization. V2 alias: `await cognee.visualize(...)` (same function). `[AST:cognee/api/v1/visualize/visualize.py:L17]`

## Key API Summary

### V1 API (knowledge-graph primitives)

| Export | Kind | Key params | Source |
|---|---|---|---|
| `cognee.add` | async fn | `data, dataset_name="main_dataset", node_set=None, dataset_id=None, incremental_loading=True, data_per_batch=20, importance_weight=0.5, run_in_background=False` | `[AST:cognee/api/v1/add/add.py:L22]` |
| `cognee.cognify` | async fn | `datasets=None, graph_model=KnowledgeGraph, chunker=TextChunker, chunk_size=None, temporal_cognify=False, custom_prompt=None, run_in_background=False` | `[AST:cognee/api/v1/cognify/cognify.py:L44]` |
| `cognee.search` | async fn | `query_text, query_type=SearchType.GRAPH_COMPLETION, datasets=None, top_k=10, node_name=None, only_context=False, session_id=None, verbose=False, neighborhood_depth=None, neighborhood_seed_top_k=None` | `[AST:cognee/api/v1/search/search.py:L26]` |
| `cognee.memify` | async fn | `extraction_tasks=None, enrichment_tasks=None, data=None, dataset="main_dataset", node_name=None, run_in_background=False` | `[AST:cognee/modules/memify/memify.py:L25]` |
| `cognee.update` | async fn | `data_id, data, dataset_id, node_set=None, preferred_loaders=None, incremental_loading=True` | `[AST:cognee/api/v1/update/update.py:L12]` |
| `cognee.run_custom_pipeline` | async fn | `tasks=None, data=None, dataset="main_dataset", pipeline_name="custom_pipeline", run_in_background=False` | `[AST:cognee/modules/run_custom_pipeline/run_custom_pipeline.py:L14]` |
| `cognee.prune` | class (ns) | `.prune_data()`, `.prune_system(graph=True, vector=True, metadata=False, cache=True)` — all async | `[AST:cognee/api/v1/prune/prune.py:L4]` |
| `cognee.datasets` | class (ns) | `.list_datasets()`, `.list_data(dataset_id)`, `.has_data(dataset_id)`, `.get_status([ids])`, `.empty_dataset(id)`, `.delete_data(dataset_id, data_id, mode="soft")`, `.delete_all()` — all async | `[AST:cognee/api/v1/datasets/datasets.py:L25]` |
| `cognee.config` | class (ns) | `set_llm_provider`, `set_llm_model`, `set_llm_api_key`, `set_embedding_provider`, `set_embedding_model`, `set_embedding_dimensions`, `set_vector_db_provider`, `set_graph_database_provider`, `system_root_directory`, ... (32 static methods) | `[AST:cognee/api/v1/config/config.py:L18]` |
| `cognee.SearchType` | enum | 15 modes: `GRAPH_COMPLETION` (default), `RAG_COMPLETION`, `CHUNKS`, `CHUNKS_LEXICAL`, `SUMMARIES`, `TEMPORAL`, `CODING_RULES`, `CYPHER`, `NATURAL_LANGUAGE`, `FEELING_LUCKY`, `TRIPLET_COMPLETION`, `GRAPH_SUMMARY_COMPLETION`, `GRAPH_COMPLETION_COT`, `GRAPH_COMPLETION_CONTEXT_EXTENSION`, `GRAPH_COMPLETION_DECOMPOSITION` | `[AST:cognee/modules/search/types/SearchType.py:L4]` |
| `cognee.visualize_graph` | async fn | `destination_file_path=None` → returns HTML str. For lower-level use, see `cognee.cognee_network_visualization(graph_data, destination_file_path=None)`. | `[AST:cognee/api/v1/visualize/visualize.py:L17]` · `[AST:cognee/modules/visualization/cognee_network_visualization.py:L22]` |
| `cognee.enable_tracing` / `disable_tracing` / `get_last_trace` / `get_all_traces` / `clear_traces` | sync fns | OpenTelemetry in-memory tracing (5 functions) | `[AST:cognee/modules/observability/trace_context.py:L16]` |
| `cognee.pipelines` | module | Re-exports `Task`, `run_tasks`, `run_tasks_parallel`, `run_pipeline` from `cognee.modules.pipelines` (lazy). Imported as `from .modules import pipelines`. | `[AST:cognee/modules/pipelines/__init__.py:L1]` |
| `cognee.Drop` | sentinel | Singleton `_Drop()` instance. Return `Drop` from any pipeline step to filter the item out of the stream. `bool(Drop) is False`. | `[AST:cognee/pipelines/types.py:L32]` |
| `cognee.session` | module | Session-scoped Q&A helpers — `get_session`, `add_feedback`, `delete_feedback` (all async). | `[AST:cognee/api/v1/session/session.py:L1]` |
| `cognee.run_startup_migrations` | async fn | Runs relational (Alembic) + vector schema migrations in sequence. Replaces standalone `run_migrations` for startup setup. | `[AST:cognee/run_migrations.py:L80]` |
| `cognee.__version__` | str | Package version string (e.g., `"1.0.0"`) — resolved at import time via `get_cognee_version()`. Use for version-gated code paths. | `[AST:cognee/__init__.py:L6]` |

### V2 memory-oriented API

| Export | Kind | Key params | Source |
|---|---|---|---|
| `cognee.remember` | async fn | `data, dataset_name="main_dataset", *, session_id=None, chunk_size=None, chunker=None, custom_prompt=None, run_in_background=False, self_improvement=True, session_ids=None, **kwargs` → `RememberResult`. Wraps `add + cognify` into one call. | `[AST:cognee/api/v1/remember/remember.py:L339]` |
| `cognee.RememberResult` | class | Promise-like result. Printable summary, awaitable (block until pipeline finishes in background mode), attributes: `status`, `dataset_name`, `dataset_id`, `session_id`, `pipeline_run_id`, `error`, `elapsed_seconds`, `content_hash`. | `[AST:cognee/api/v1/remember/remember.py:L139]` |
| `cognee.recall` | async fn | `query_text, query_type=None, *, datasets=None, top_k=10, auto_route=True, **kwargs` → `list`. Thin wrapper over `search` with auto-routing heuristics. | `[AST:cognee/api/v1/recall/recall.py:L122]` |
| `cognee.improve` | async fn | `dataset="main_dataset", *, run_in_background=False, node_name=None, session_ids=None, **kwargs`. When `session_ids` given: applies feedback weights → persists session Q&A → default enrichment (triplet embeddings). | `[AST:cognee/api/v1/improve/improve.py:L36]` |
| `cognee.forget` | async fn | `*, data_id=None, dataset=None, everything=False, user=None` → `dict`. Unified deletion; replaces prune/delete/empty_dataset for most cases. | `[AST:cognee/api/v1/forget/forget.py:L15]` |
| `cognee.serve` | async fn | `url=None, api_key=None, *, management_url=None, auth0_domain=None, auth0_client_id=None, auth0_audience=None` → `CloudClient`. Local/direct mode when `url` given; Cloud Auth0 device-code flow otherwise. | `[AST:cognee/api/v1/serve/serve.py:L17]` |
| `cognee.disconnect` | async fn | `clear_saved: bool = False` → `None`. Reverts V2 ops to local execution; optionally deletes saved credentials. | `[AST:cognee/api/v1/serve/disconnect.py:L8]` |
| `cognee.visualize` | async fn | Alias for `cognee.visualize_graph` re-exported via V2 namespace. | `[AST:cognee/api/v1/__init__.py:L6]` |
| `cognee.agent_memory` | decorator | `*, with_memory=True, save_traces=False, memory_query_fixed=None, memory_query_from_method=None, memory_system_prompt=None, memory_top_k=5, user=None, dataset_name=None`. Decorates an async agent entrypoint; retrieves memory context before the call and persists a trace after. Requires the wrapped function to be async. | `[AST:cognee/modules/agent_memory/decorator.py:L22]` |

## Deprecations & Gotchas

> Current-state deprecations and source/docs discrepancies surfaced during extraction. v1.0.0 is the first major release and introduces a new V2 API layer alongside the V1 API.

- **`cognee.low_level` is no longer exported** from `cognee/__init__.py`. The file `cognee/low_level.py` still exists and re-exports `DataPoint` (`ExtendableDataPoint`) + `setup`, but access it via the full path: `from cognee.infrastructure.engine import ExtendableDataPoint as DataPoint` or `from cognee.modules.engine.operations.setup import setup`. `[AST:cognee/low_level.py:L1]`
- **`cognee.run_migrations` is no longer exported** from `cognee/__init__.py` — replaced by **`cognee.run_startup_migrations()`** which runs relational + vector migrations in sequence. The standalone `run_migrations` function still lives at `cognee/run_migrations.py:16` but must be imported directly. `[AST:cognee/run_migrations.py:L80]`
- **`cognee.delete(data_id, dataset_id, mode="soft", user=None)` is deprecated since cognee v0.3.9.** Use `await cognee.datasets.delete_data(dataset_id=..., data_id=...)` or the V2 `await cognee.forget(data_id=..., dataset=...)` instead. The old function is now defined in `cognee/api/v1/delete/__init__.py` (source file `delete.py` is empty) and decorated with `@deprecated(version="0.3.9")`. `[AST:cognee/api/v1/delete/__init__.py:L1]`
- **`cognee.pipelines` has been restructured in v1.0.0.** Old flat file `cognee/pipelines.py` is gone; the name now resolves to `cognee/modules/pipelines/` (via `from .modules import pipelines`) for `Task`/`run_tasks`/`run_pipeline`, AND there's a new `cognee/pipelines/` **package** that exports `Drop` and provides lazy legacy re-exports of the same names via `__getattr__`. Either import path (`from cognee.modules.pipelines import Task` or `from cognee.pipelines import Task`) works. `[AST:cognee/modules/pipelines/__init__.py:L1]` · `[AST:cognee/pipelines/__init__.py:L1]`
- **`cognee.agent_memory` requires the wrapped function to be async** — decorating a sync function raises `CogneeValidationError`. If `memory_query_from_method="name"` is set, the method must have a parameter literally named `name`. `[AST:cognee/modules/agent_memory/decorator.py:L45]`
- **`cognee.serve()` without arguments triggers Auth0 Device Code Flow** (interactive browser login). Pass `url=` + optional `api_key=` for non-interactive/local connections. After `serve()`, V2 operations route through the remote instance; V1 operations still execute locally. `[AST:cognee/api/v1/serve/serve.py:L17]`
- **`cognee.start_ui` is sync (not async) and requires a `pid_callback` positional argument.** Do not call `await cognee.start_ui()` — the function returns `Optional[subprocess.Popen]` synchronously. Signature: `start_ui(pid_callback, port=3000, open_browser=True, auto_download=False, start_backend=False, backend_port=8000, start_mcp=False, mcp_port=8001)`. `[AST:cognee/api/v1/ui/ui.py:L369]`
- **`cognee.start_visualization_server` is a module, not a function.** The top-level `__init__.py` re-imports the submodule name. To start the visualization HTTP server, call `cognee.start_visualization_server.visualization_server(port)` which is synchronous. `[AST:cognee/api/v1/visualize/start_visualization_server.py:L6]`

See Full API Reference for complete parameter tables and behavioral notes.

## Key Types

### `SearchType` (enum) — `cognee.SearchType`

All modes accepted by `cognee.search(query_type=...)` and `cognee.recall(query_type=...)`:

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
| `GRAPH_COMPLETION_DECOMPOSITION` | Decomposes complex questions into sub-queries for broader graph coverage (new in v1.0.0) |
| `CYPHER` | Raw Cypher queries (enable in config) |
| `NATURAL_LANGUAGE` | Natural-language → graph query translation |
| `TEMPORAL` | Time-aware graph search (pairs with `temporal_cognify=True`) |
| `CODING_RULES` | Queries against `coding_agent_rules` node_set (populated by memify defaults) |
| `FEELING_LUCKY` | Cognee auto-selects the best search type |

`[AST:cognee/modules/search/types/SearchType.py:L4]`

### `Task` — `cognee.pipelines.Task` (or `cognee.modules.pipelines.Task`)

Constructor: `Task(executable, *args, task_config=None, **kwargs)`. Wraps any callable (function, coroutine function, generator, or async generator). Detects type via `inspect` and picks the right execute path. `task_config={"batch_size": N}` controls batching. `[AST:cognee/modules/pipelines/tasks/task.py:L24]`

### `Drop` — `cognee.Drop` (or `cognee.pipelines.Drop`)

Singleton sentinel. Returning `Drop` from any pipeline step filters that item out of the stream. `bool(Drop) is False`, `repr(Drop) == "Drop"`. `[AST:cognee/pipelines/types.py:L32]`

### `RememberResult` — `cognee.RememberResult`

Promise-like result returned by `cognee.remember()`. Printable for a quick summary; awaitable to block until the background pipeline finishes. Status values: `"running"`, `"completed"`, `"errored"`, `"session_stored"`. Attributes: `dataset_name`, `dataset_id`, `session_id`, `pipeline_run_id`, `error`, `elapsed_seconds`, `content_hash`. `[AST:cognee/api/v1/remember/remember.py:L139]`

### `DataPoint` — `cognee.infrastructure.engine.ExtendableDataPoint`

Pydantic base class for graph-native entities. Assigning one `DataPoint` instance to another's field creates an edge; the field name becomes the edge label. Use `metadata = {"index_fields": [...]}` to mark which fields should be embedded in the vector store. In v1.0.0 this is no longer re-exported via `cognee.low_level`; import directly. `[AST:cognee/low_level.py:L1]` · `[EXT:https://docs.cognee.ai/guides/custom-data-models]`

### Exceptions — `cognee.exceptions`

- `CogneeApiError` — base class (HTTP 418 default)
- `CogneeSystemError` — 500
- `CogneeValidationError` — 422
- `CogneeConfigurationError` — 500
- `CogneeTransientError` — 503

All accept `(message, name, status_code, log, log_level)`. `[AST:cognee/exceptions/exceptions.py:L7]`

## Architecture at a Glance

- **Three-layer storage with node_set-aware graph:** relational (provenance), vector (semantic), graph (entities + edges + `node_set` tagging). `node_set` tags passed to `cognee.add` become first-class graph nodes after `cognify`. `[EXT:https://docs.cognee.ai/core-concepts/overview]`
- **V1 vs V2 APIs coexist:** V1 (`add → cognify → search`) exposes the full graph-building primitives; V2 (`remember → recall`) is a thin, opinionated wrapper that folds the two most common calls into one per step, adds `improve`/`forget`/`serve`/`agent_memory` for agent workflows, and supports cloud routing via `serve()`. Both share the same underlying pipelines.
- **Default backends (pinned in `pyproject.toml`):** LLM via `litellm` / `openai` / `instructor`; vector `lancedb` + `pylance`; graph `kuzu==0.11.3` + `networkx`; relational `sqlalchemy` + `aiosqlite` + `alembic`. Optional extras: `neo4j`, `postgres` (`pgvector`+`asyncpg`), `fastembed`, `scraping`, `distributed` (Modal). `[SRC:pyproject.toml:L22]`
- **Async-first:** every ingestion/graph/search/memify/update/remember/recall/improve/forget/serve function is a coroutine — call via `await` from inside an `async def` and drive with `asyncio.run(main())`. The sole exceptions are `start_ui`, `start_visualization_server.visualization_server`, and the `enable_tracing`/`disable_tracing`/`get_*_trace`/`clear_traces` family.

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
