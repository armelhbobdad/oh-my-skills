---
name: oms-cognee
description: >
  Builds apps on cognee v1.6.2, the knowledge-graph memory engine for AI agents.
  Use when ingesting text/files/URLs into memory, building knowledge graphs, searching
  memory with SearchType modes, enriching graphs with memify/improve, scoping memory
  with datasets and node_sets, configuring LLM/embedding/graph/vector backends,
  running custom pipelines, decorating agents with `agent_memory`, connecting
  to Cognee Cloud with `serve`/`push`, exporting, validating or reporting on graphs,
  or visualizing graphs and memory provenance. Covers cognee/__init__.py exports: the
  V1 API (add, cognify, search, memify, datasets, agents, prune, update,
  run_custom_pipeline, config, SearchType, report, validate, visualize_graph,
  pipelines, Drop, run_migrations, tracing, tools) and the V2 memory API (remember,
  recall, improve, forget, serve, disconnect, visualize, push, export, agent_memory,
  MemoryEntry). Do NOT use for: cognee internals, the HTTP REST API (use
  cognee-mcp or the FastAPI server), non-cognee memory/RAG libraries.
---

# oms-cognee

## Overview

**Cognee** is an open-source knowledge-graph memory engine for AI agents. It combines a vector store (semantic search), a graph store (entities + relationships), and a relational store (provenance) into a single three-layer memory architecture. The canonical V1 workflow is **`add → cognify → search`**: ingest data, build a knowledge graph, then query it. The new **V2 memory-oriented API** wraps this as **`remember → recall`** with an optional `improve`/`forget`/`serve`/`agent_memory` layer for agent contexts.

- **Source:** [topoteretes/cognee](https://github.com/topoteretes/cognee) @ `v1.6.2` (commit `ba3631f2`) `[SRC:pyproject.toml:L4]`
- **Language:** Python >=3.10, <3.15 `[SRC:pyproject.toml:L10]`
- **Forge tier:** Deep (AST + ccc + QMD + docs fetch)
- **Public exports:** 60 non-underscore top-level names in `cognee/__init__.py` (plus `__version__`). `load_env_file`, `describe_resolution` and `setup_logging` are among them but out of scope for this skill. The `logger` it binds and the 29 names of the `cognee.migration` module (`from . import migration`) are summarized in the Key API Summary. `[SRC:cognee/__init__.py:L18-L116]` · `[SRC:cognee/__init__.py:L27-L34]` · `[SRC:cognee/__init__.py:L98]` · `[SRC:cognee/migration/__init__.py:L54-L84]`
- **Confidence:** T1 (37 entries) where an ast-grep recipe extracted the signature from the source tree; T1-low (49) where it was read by eye: the `__version__` variable, the `visualize` alias, the `session` namespace, the `pipelines` and `tools` modules, the `MemoryEntry` type alias, `logger`, `Drop`, `DataPoint` (the `cognee.low_level` alias), `disconnect`, `enable_tracing`/`disable_tracing`/`get_all_traces`/`clear_traces`, `visualization_server`/`start_visualization_server`, the `cognee.migration` names (outside `scope.include`), and the member and method lists of the `SearchType`, `config`, `datasets`, `prune` and `RememberResult` classes (their class lines are ast-grep matches). A recipe would match some of these definitions too (`disconnect`, those four tracing functions, `visualization_server`, the `cognee.migration` classes and functions), but their entries were read by eye, so they stay T1-low
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

    # 3) Query with graph-backed LLM completion (pinned; the default is HYBRID_COMPLETION)
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
    print(result)  # RememberResult — blocks by default; with run_in_background=True, await it
    answers = await cognee.recall("What does Cognee do?")
    for a in answers:  # list[RecallResponse], told apart by a.source ("graph", "system", ...)
        print(a.source, getattr(a, "text", a))

if __name__ == "__main__":
    asyncio.run(main())
```

Signatures: `[AST:cognee/api/v1/add/add.py:L39]` · `[AST:cognee/api/v1/cognify/cognify.py:L110]` · `[AST:cognee/api/v1/search/search.py:L41]` · `[AST:cognee/api/v1/remember/remember.py:L867]` · `[AST:cognee/api/v1/recall/recall.py:L347]` · `[SRC:cognee/api/v1/remember/remember.py:L639-L643]` · `[SRC:cognee/modules/recall/types/RecallResponse.py:L91-L101]`

Set `LLM_API_KEY` for LLM graph extraction and completion (the Quick Start's `GRAPH_COMPLETION` search needs it); Cognee defaults to OpenAI but supports litellm-compatible providers (Anthropic, Gemini, Ollama, etc.) via `cognee.config.set_llm_provider(...)` and friends. Without a key (and no embedding settings), `add()` validates only the embedding config and `cognify()` (`GRAPH_EXTRACTOR=auto`) falls back to the local GLiNER demo extractor and fastembed embeddings; the `gliner` extra installs itself on first use unless `GLINER_AUTO_INSTALL=false`. `[SRC:cognee/api/v1/config/config.py:L350]` · `[SRC:cognee/api/v1/add/add.py:L204-L209]` · `[SRC:cognee/api/v1/add/add.py:L238-L248]` · `[SRC:cognee/api/v1/cognify/cognify.py:L308-L310]` · `[SRC:cognee/modules/cognify/config.py:L23-L34]` · `[SRC:cognee/api/v1/search/search.py:L227-L229]`

Importing `cognee` loads a single `.env`: the exact file in `COGNEE_ENV_FILE` if set (an error if that path is not a file), else the first `.env` in the working directory or its parents up to the project root (`.git` or `pyproject.toml`), else the first one in the cognee package directory or its parents. Its values override variables already set in the shell, and the chosen path is logged. `[SRC:cognee/__init__.py:L24-L35]` · `[SRC:cognee/shared/env_file.py:L13-L29]` · `[SRC:cognee/shared/env_file.py:L112-L124]`

<!-- [MANUAL:quick-start-notes] -->
<!-- Add project-specific quick-start notes here. Preserved during skill updates. -->
<!-- [/MANUAL:quick-start-notes] -->

## Common Workflows

**V1 — Add and process data:**
`await cognee.add(data, dataset_name="main") → await cognee.cognify(datasets="main") → await cognee.search(query_text=..., datasets="main")` `[AST:cognee/api/v1/add/add.py:L39]`

**V2 — Remember and recall:**
`await cognee.remember(data, dataset_name="main") → await cognee.recall(query_text="...")` — wraps add+cognify into one call; `recall` calls `authorized_search` directly and merges the sources chosen by `scope`, auto-routing the search type. `[AST:cognee/api/v1/remember/remember.py:L867]` · `[AST:cognee/api/v1/recall/recall.py:L347]` · `[SRC:cognee/api/v1/recall/recall.py:L788-L789]`

**Scope memory per tenant / customer / workflow with node_set:**
`await cognee.add(data, dataset_name="agent_memory", node_set=["customer_123", "preferences"]) → await cognee.cognify(datasets="agent_memory") → await cognee.search(query_text=..., datasets="agent_memory", node_name=["customer_123"])` `[AST:cognee/api/v1/add/add.py:L39]` · `[SRC:cognee/skill.md:L122-L130]`

**Enrich an existing graph with memify (V1) or improve (V2):**
`await cognee.add(...) → await cognee.cognify(...) → await cognee.memify(dataset="rules_demo")` — with no task lists, memify runs `get_triplet_datapoints` (only when triplet embedding is enabled) and then `index_data_points`; it does not create `Rule` nodes (the coding-rule association task lives in `cognee/tasks/codingagents`). Equivalent V2: `result = await cognee.improve(dataset="rules_demo", session_ids=[...])`, which runs the gated stage registry (feedback weights from past session Q&A, session persistence, enrichment) and returns an `ImproveResult`; with `run_in_background=True`, `await result.wait()`. `[AST:cognee/modules/memify/memify.py:L27]` · `[SRC:cognee/memify_pipelines/memify_default_tasks.py:L6-L15]` · `[SRC:cognee/tasks/codingagents/coding_rule_associations.py:L94]` · `[AST:cognee/api/v1/improve/improve.py:L101]` · `[SRC:cognee/modules/improve/result.py:L187-L195]`

**Delete data (V2):**
`await cognee.forget(data_id=..., dataset=...)` — single deletion command that replaces prune/delete/empty_dataset; supports `everything=True` to wipe all user data and `memory_only=True` to drop graph/vector memory but keep the raw files. `[AST:cognee/api/v1/forget/forget.py:L22]` · `[SRC:cognee/api/v1/forget/forget.py:L62-L65]`

**Connect to Cognee Cloud:**
`await cognee.serve(url="https://my-instance.cognee.ai", api_key="ck_...")` — raises `CogneeConfigurationError` at connect time if the instance rejects the key (401/403), then routes subsequent `remember`/`recall`/`improve`/`forget` and `add`/`cognify`/`update`/`search`/`datasets.list_data` calls through the remote instance; `visualize` always renders the local graph. `await cognee.disconnect()` returns to local mode. To upload a local graph instead of re-deriving it remotely: `await cognee.push("main_dataset")`. `[AST:cognee/api/v1/serve/serve.py:L17]` · `[SRC:cognee/api/v1/serve/serve.py:L98-L120]` · `[SRC:cognee/api/v1/serve/disconnect.py:L8]` · `[AST:cognee/api/v1/push/push.py:L96]`

**Decorate an async agent entrypoint with memory context:**
`@cognee.agent_memory(with_memory=True, save_session_traces=True, memory_query_from_method="question", memory_top_k=5, session_id="support_agent")` — retrieves relevant memory context before the call and stores a trace step in the session cache after (caching must be enabled); the trace reaches the graph via `persist_session_trace_after=N` or `improve(session_ids=...)`. `[AST:cognee/modules/agent_memory/decorator.py:L29]` · `[SRC:cognee/modules/agent_memory/runtime.py:L478-L483]` · `[SRC:cognee/modules/agent_memory/runtime.py:L509-L539]`

**Run a custom task pipeline:**
`from cognee.modules.pipelines import Task, run_pipeline; tasks = [Task(extract_people), Task(add_data_points)]; async for _ in run_pipeline(tasks=tasks, data=text, datasets=["people_demo"]): pass` `[SRC:cognee/modules/pipelines/__init__.py:L75-L78]` · `[SRC:cognee/modules/pipelines/operations/pipeline.py:L53-L57]` · `[EXT:https://docs.cognee.ai/guides/custom-tasks-pipelines]`

**Filter pipeline items with `Drop`:**
`from cognee import Drop; async def skip_short(text): return Drop if len(text) < 10 else text` — returning `Drop` from any pipeline step removes that item from the stream. `[SRC:cognee/pipelines/types.py:L32]`

**Visualize the graph:**
`await cognee.visualize_graph("/path/to/graph.html")` — writes an interactive HTML visualization of a bounded subgraph of `dataset="main_dataset"` (2-hop neighborhood of up to 10 seed nodes, capped at 500 nodes); `full=True` renders the whole graph. V2 alias: `await cognee.visualize(...)` (same function). To serve the working directory over HTTP: `shutdown = cognee.start_visualization_server.visualization_server(8001)`. For the actor/dataset/file provenance view: `await cognee.visualize_memory_provenance(...)`. `[AST:cognee/api/v1/visualize/visualize.py:L193]` · `[SRC:cognee/modules/visualization/subgraph_data.py:L24-L26]` · `[SRC:cognee/api/v1/visualize/start_visualization_server.py:L6]` · `[AST:cognee/api/v1/visualize/memory_provenance.py:L848]`

**Migrate memory from another system, or back up and restore a dataset:**
`from cognee.migration import Mem0Source, ZepSource, LettaSource, COGXArchiveSource; await cognee.remember(Mem0Source("mem0_export.json")); await cognee.remember(ZepSource("graphiti_dump.json", mode="hybrid")); await cognee.export("main_dataset", format="cogx", destination="backup_cogx"); await cognee.remember(COGXArchiveSource("backup_cogx"))` — `remember()` accepts any `MemorySource` and routes it through the migration loader. `snapshot = await cognee.export("main_dataset")` returns a `GraphSnapshot` of typed DataPoint objects (`snapshot.find(name="Alice")`). `[SRC:cognee/migration/__init__.py:L3-L20]` · `[SRC:cognee/modules/migration/sources/base.py:L1-L10]`

## Key API Summary

### V1 API (knowledge-graph primitives)

| Export | Kind | Key params | Source |
|---|---|---|---|
| `cognee.add` | async fn | Ingest text, files, URLs or `DataItem`s: [16 params + `**kwargs`](references/full-api-reference.md#cogneeadd--ingest-data-into-a-dataset). | `[AST:cognee/api/v1/add/add.py:L39]` |
| `cognee.cognify` | async fn | Build the graph: [23 params + `**kwargs`](references/full-api-reference.md#cogneecognify--build-the-knowledge-graph) → `{dataset_id: PipelineRunInfo}` (the initial run infos in background mode), or `DryRunEstimate` with `dry_run=True`. `extractor="gliner_demo"` rejects a custom `graph_model`, `temporal_cognify` and `dry_run`, and ignores `custom_prompt`. | `[AST:cognee/api/v1/cognify/cognify.py:L110]` · `[SRC:cognee/modules/pipelines/layers/pipeline_execution_mode.py:L113-L129]` · `[SRC:cognee/api/v1/cognify/cognify.py:L418]` · `[SRC:cognee/api/v1/cognify/cognify.py:L323-L332]` · `[SRC:cognee/api/v1/cognify/cognify.py:L434-L441]` |
| `cognee.search` | async fn | [27 params](references/full-api-reference.md#cogneesearch--query-the-knowledge-graph), `query_type=SearchType.HYBRID_COMPLETION` by default → `list[SearchResult]`. `top_k` (default 15) applies per dataset; `top_k<=0` raises `QueryValidationError`. | `[AST:cognee/api/v1/search/search.py:L41]` · `[SRC:cognee/api/v1/search/search.py:L215-L218]` · `[SRC:cognee/modules/search/methods/get_search_type_retriever_instance.py:L78-L79]` |
| `cognee.memify` | async fn | Enrich an existing graph: [10 params](references/full-api-reference.md#cogneememify--enrich-an-existing-graph). | `[AST:cognee/modules/memify/memify.py:L27]` |
| `cognee.update` | async fn | [15 params](references/full-api-reference.md#cogneeupdate--replace-data-inside-a-dataset), `data_id`, `data`, `dataset_id` required → `dict`. Keeps `data_id`. By default replaces only the chunks the edit touched; otherwise runs `forget(memory_only=True)`, a pinned re-add, then cognify. An unmatched `data_id` raises `UpdateTargetNotFoundError`; a list that does not hold exactly one item raises `IngestionError`. | `[AST:cognee/api/v1/update/update.py:L28]` · `[SRC:cognee/api/v1/update/update.py:L101-L108]` · `[SRC:cognee/api/v1/update/update.py:L179-L197]` · `[SRC:cognee/api/v1/update/update.py:L286-L309]` |
| `cognee.run_custom_pipeline` | async fn | Run `Task`s over a dataset in one call: [12 params](references/pipelines-and-datapoints.md#run_custom_pipeline). | `[AST:cognee/modules/run_custom_pipeline/run_custom_pipeline.py:L14]` |
| `cognee.prune` | class (ns) | `.prune_data()`, `.prune_system(graph=True, vector=True, metadata=False, cache=True)` — all async | `[AST:cognee/api/v1/prune/prune.py:L5]` |
| `cognee.datasets` | class (ns) | `.list_datasets`, `.list_data`, `.has_data`, `.get_status`, `.get_progress`, `.empty_dataset`, `.delete_data`, `.delete_all` — all async, each but `get_status`/`get_progress` with an optional `user`; plus sync `.discover_datasets`. [Signatures](references/full-api-reference.md#dataset-management--cogneedatasets). `get_status` returns a flat cognify-status map by default and `{dataset_id: {pipeline: status}}` for several pipelines; `get_progress` returns `{status, progress}` values in the same shapes. | `[AST:cognee/api/v1/datasets/datasets.py:L105]` · `[SRC:cognee/api/v1/datasets/datasets.py:L37-L63]` |
| `cognee.config` | class (ns) | `set_llm_provider`, `set_llm_model`, `set_llm_api_key`, `set_embedding_provider`, `set_embedding_model`, `set_embedding_dimensions`, `set_vector_db_provider`, `set_graph_database_provider`, `set_recall_config`, `system_root_directory`, `get`/`get_all`/`set`, ... (45 static methods, one of them the private `_update_config`); bulk `set_*_config` setters coerce string values to the field's declared `bool`/`int`/`float` type | `[AST:cognee/api/v1/config/config.py:L171]` · `[SRC:cognee/api/v1/config/config.py:L419-L428]` · `[SRC:cognee/api/v1/config/config.py:L162-L167]` |
| `cognee.SearchType` | enum | 20 modes: `HYBRID_COMPLETION` (default), `GRAPH_COMPLETION`, `RAG_COMPLETION`, `CHUNKS`, `CHUNKS_LEXICAL`, `SUMMARIES`, `TEMPORAL`, `CODING_RULES`, `CYPHER`, `NATURAL_LANGUAGE`, `FEELING_LUCKY`, `TRIPLET_COMPLETION`, `GRAPH_SUMMARY_COMPLETION`, `GRAPH_COMPLETION_COT`, `GRAPH_COMPLETION_CONTEXT_EXTENSION`, `GRAPH_COMPLETION_DECOMPOSITION`, `AGENTIC_COMPLETION`, `CODE`, `GRAPH_REPORT`, `SKILLS` | `[AST:cognee/modules/search/types/SearchType.py:L4]` |
| `cognee.visualize_graph` | async fn | `destination_file_path=None, include_session_events=True, session_ids=None, user=None, dataset="main_dataset", *, full=False, query=None, seed_node_ids=None, recall_result=None, neighborhood_depth=2, neighborhood_seed_top_k=10, max_nodes=500` → returns HTML str. For lower-level use, see `cognee.cognee_network_visualization(graph_data, destination_file_path=None, schema_data=None, search_events=None)`, which also fetches node embeddings (best effort) for a semantic map. | `[AST:cognee/api/v1/visualize/visualize.py:L193]` · `[AST:cognee/modules/visualization/cognee_network_visualization.py:L154]` · `[SRC:cognee/modules/visualization/cognee_network_visualization.py:L43-L53]` |
| `cognee.enable_tracing` / `disable_tracing` / `get_last_trace` / `get_all_traces` / `clear_traces` | sync fns | OpenTelemetry in-memory tracing (5 functions) | `[SRC:cognee/modules/observability/trace_context.py:L18]` |
| `cognee.pipelines` | module | Re-exports `Task`, `run_tasks`, `run_tasks_parallel`, `run_pipeline` from `cognee.modules.pipelines`. Imported as `from .modules import pipelines`; this `run_pipeline` is the dataset-aware orchestrator. | `[SRC:cognee/modules/pipelines/__init__.py:L75-L78]` · `[SRC:cognee/__init__.py:L67]` |
| `cognee.Drop` | sentinel | Singleton `_Drop()` instance. Return `Drop` from any pipeline step to filter the item out of the stream. `bool(Drop) is False`. | `[SRC:cognee/pipelines/types.py:L32]` |
| `cognee.session` | namespace | `types.SimpleNamespace` of session-scoped Q&A helpers — `get_session`, `add_feedback`, `delete_feedback` and `distill_session` (→ `DistillationResult`), all async, each ending in an optional `user`. [Signatures](references/full-api-reference.md#sessions--cogneesession). Call `cognee.session.<fn>(...)`; `import cognee.session` and `from cognee.session import ...` do not work. | `[SRC:cognee/api/v1/session/__init__.py:L8-L13]` · `[AST:cognee/api/v1/session/session.py:L65]` · `[AST:cognee/api/v1/session/session.py:L113]` · `[AST:cognee/api/v1/session/session.py:L147]` · `[SRC:cognee/modules/session_distillation/distill.py:L471-L475]` |
| `cognee.run_migrations` | async fn | `()` → `list[str]` of databases whose migration failed (the shim declares no return annotation; it returns the orchestrator's `list[str]`). Runs relational (Alembic) migrations first, then the graph/vector revision chains; once per process. | `[AST:cognee/run_migrations.py:L18]` · `[SRC:cognee/modules/migrations/startup.py:L386-L397]` |
| `cognee.__version__` | str | Package version string (e.g., `"1.6.2"`; `"1.6.2-local"` from a source checkout) — resolved at import time via `get_cognee_version()`. Use for version-gated code paths. | `[SRC:cognee/__init__.py:L22]` · `[SRC:cognee/version.py:L10-L26]` |
| `cognee.get_cognee_version` | sync fn | `()` → `str`: the version from a nearby `pyproject.toml` suffixed `-local`, else the installed package version, else `"unknown"`. Backs `__version__`. | `[AST:cognee/version.py:L7]` |

### V2 memory-oriented API

| Export | Kind | Key params | Source |
|---|---|---|---|
| `cognee.remember` | async fn | `data, dataset_name="main_dataset", *, dataset_id=None, session_id=None, chunk_size=None, chunker=None, custom_prompt=None, run_in_background=False, self_improvement=True, session_ids=None, dry_run=False, raise_on_error=True, **kwargs: Unpack[RememberKwargs]` → `RememberResult` (`DryRunEstimate` with `dry_run=True`, `PresortReport` with `dry_run="presort"`, or `dict`). `data` also takes a `MemoryEntry`, `MemorySource`, `PresortReport` or `dict`. `dataset_id` takes precedence over `dataset_name` (not for `MemorySource`/`MemoryEntry`). `RememberKwargs` (power-user overrides such as `graph_model`, `node_set`, `user`, `vector_db_config`, `graph_db_config`) is importable from `cognee.api.v1.remember`, not top-level. Wraps `add + cognify` into one call. | `[AST:cognee/api/v1/remember/remember.py:L867]` · `[SRC:cognee/api/v1/remember/remember.py:L920-L923]` · `[AST:cognee/api/v1/remember/remember.py:L90]` |
| `cognee.RememberResult` | class | Promise-like result. Printable summary, awaitable (block until a background run finishes), attributes: `status`, `dataset_name`, `dataset_id`, `session_ids` (+ `session_id` property), `pipeline_run_id`, `error`, `elapsed_seconds`, `content_hash`, `items_processed`, `items`, `raw_result`, `improve`, `improve_error`, `entry_type`, `entry_id`. Scripts that use `run_in_background=True` (or `session_id` without awaiting the result) should `await cognee.wait_for_background_tasks()` before exit. | `[AST:cognee/api/v1/remember/remember.py:L600]` · `[SRC:cognee/api/v1/remember/remember.py:L655-L675]` · `[SRC:cognee/__init__.py:L92-L94]` |
| `cognee.recall` | async fn | `query_text: str, query_type: SearchType \| None = None, *, datasets: list[str] \| None = None, dataset_ids: list[UUID] \| None = None, top_k: int = 15, auto_route: bool = True, scope: str \| list[str] \| None = None, system_prompt: str \| None = None, system_prompt_path: str = "answer_simple_question.txt", node_name: list[str] \| None = None, node_name_filter_operator: str = "OR", only_context: bool = False, session_id: str \| None = None, context_profile: str = "qa", wide_search_top_k: int \| None = None, triplet_distance_penalty: float \| None = None, feedback_influence: float = get_base_config().default_feedback_influence, verbose: bool = False, retriever_specific_config: dict \| None = None, response_model: type \| None = None, neighborhood_depth: int \| None = None, neighborhood_seed_top_k: int \| None = None, include_references: bool = False, tool_connections: list[str] \| None = None, tools_trigger: str = "always", code_query: dict \| None = None, user: object \| None = None, llm_config: LLMConfig \| None = None, embedding_config: EmbeddingConfig \| None = None` → `list[RecallResponse]` (29 params). Explicit keyword-only params, no `**kwargs`: other search kwargs such as `node_type` raise `TypeError`. Calls `authorized_search` directly (not through `cognee.search`) and merges the sources chosen by `scope` (`auto`, `graph`, `session`, `session_first`, `trace`, `graph_context`, `session_context`, `all`, `tools`, `code`). The router falls back to `HYBRID_COMPLETION`, and picks `CHUNKS` when no usable LLM is configured. Entries are pydantic models told apart by `source` (`session`, `trace`, `session_context`, `graph`, `code`, `tools`, `skills`, `system`); a cold graph may return a single `source="system"` marker. | `[AST:cognee/api/v1/recall/recall.py:L347]` · `[SRC:cognee/memory/entries.py:L137-L148]` · `[SRC:cognee/api/v1/recall/recall.py:L651-L666]` · `[SRC:cognee/api/v1/recall/query_router.py:L25]` · `[SRC:cognee/api/v1/recall/recall.py:L776-L789]` · `[SRC:cognee/modules/recall/types/RecallResponse.py:L91-L101]` |
| `cognee.improve` | async fn | `dataset="main_dataset", *, run_in_background=False, node_name=None, session_ids=None, build_global_context_index=False, build_truth_subspace=False, **kwargs: Unpack[ImproveKwargs]` → `ImproveResult` (one entry per stage; `status` `completed`/`errored`/`skipped`/`running`; background mode returns `running`, so `await result.wait()`; legacy run info at `result.memify_run`). Runs 9 gated stages: `feedback_weights`, `persist_session_qa`, `persist_agent_traces`, `extract_agent_context`, `distill_sessions`, `update_user_preferences`, `build_truth_subspace`, `triplet_enrichment`, `global_context_index`. Session-fed stages skip without `session_ids`, `IMPROVE_STAGES_DISABLED` skips named stages, a failing `persist_session_qa` raises, and a run that loses the lock returns every stage skipped (`lock_held`). `ImproveKwargs` (`extraction_tasks`, `enrichment_tasks`, `data`, `node_type`, `user`, `vector_db_config`, `graph_db_config`, `feedback_alpha`) is importable from `cognee.api.v1.improve`, not top-level. | `[AST:cognee/api/v1/improve/improve.py:L101]` · `[SRC:cognee/modules/improve/registry.py:L27-L37]` · `[SRC:cognee/api/v1/improve/improve.py:L113-L131]` · `[SRC:cognee/modules/improve/result.py:L184-L205]` · `[AST:cognee/api/v1/improve/improve.py:L88]` |
| `cognee.forget` | async fn | `*, data_id=None, dataset=None` (name), `dataset_id=None, everything=False, memory_only=False, user=None` → `dict`. Unified deletion; replaces prune/delete/empty_dataset for most cases. `memory_only=True` keeps the raw files and data records; passing both `dataset` and `dataset_id` raises `ValueError`; an unknown dataset name raises `DatasetNotFoundError`. | `[AST:cognee/api/v1/forget/forget.py:L22]` · `[SRC:cognee/api/v1/forget/forget.py:L76-L77]` · `[SRC:cognee/api/v1/forget/forget.py:L477-L484]` |
| `cognee.serve` | async fn | `url=None, api_key=None, *, management_url=None, auth0_domain=None, auth0_client_id=None, auth0_audience=None` → `CloudClient`. Direct mode when `url` (or `COGNEE_SERVICE_URL`) is set: health check, then an auth probe that raises `CogneeConfigurationError` on 401/403. Otherwise saved credentials, then the Auth0 device flow only if a device client ID is configured, else `CogneeConfigurationError`. | `[AST:cognee/api/v1/serve/serve.py:L17]` · `[SRC:cognee/api/v1/serve/serve.py:L70-L82]` · `[SRC:cognee/api/v1/serve/serve.py:L220-L252]` |
| `cognee.disconnect` | async fn | `clear_saved: bool = False` → `None`. Drops the remote client so routed calls execute locally again; optionally deletes saved credentials. | `[SRC:cognee/api/v1/serve/disconnect.py:L8]` |
| `cognee.visualize` | async fn | Alias for `cognee.visualize_graph` re-exported via V2 namespace. | `[SRC:cognee/api/v1/__init__.py:L8]` |
| `cognee.agent_memory` | decorator | 17 keyword-only params: `agent_session_name=None, with_memory=True, with_session_memory=False, save_session_traces=False, memory_query_fixed=None, memory_query_from_method=None, memory_system_prompt=None, memory_top_k=5, memory_only_context=False, session_memory_last_n=5, session_id=None, user=None, dataset_name=None, session_trace_summary=False, persist_session_trace_after=None, persist_session_trace_raw_content=False, persist_session_trace_node_set_name=None`. Decorates an async agent entrypoint; retrieves memory context before the call and stores a trace step in the session cache after. Give each decorated entrypoint its own `session_id`. Requires the wrapped function to be async. | `[AST:cognee/modules/agent_memory/decorator.py:L29]` · `[SRC:cognee/modules/agent_memory/decorator.py:L52-L55]` |

### Further exports (agents, cloud push/export, inspection, memory types)

| Export | Kind | Key params | Source |
|---|---|---|---|
| `cognee.agents` | class (ns) | `.create`, `.list`, `.get`, `.delete`, `.register`, `.unregister`, `.list_connections`, `.get_connection` — all async, each with an optional `user`; agent and agent-connection management, permission-scoped per acting user. [Signatures](references/full-api-reference.md#agents--cogneeagents). | `[AST:cognee/api/v1/agents/agents.py:L40]` |
| `cognee.push` | async fn | `dataset="main_dataset", *, target_dataset=None, mode="preserve"` (or `"hybrid"`/`"re-derive"`), `run_in_background=False, url=None, api_key=None, user=None` → `PushResult`. Exports the local graph as a COGX archive and uploads it to a Cognee Cloud instance; `url`/`api_key` fall back to the active `serve()` connection, `COGNEE_SERVICE_URL` or saved credentials. | `[AST:cognee/api/v1/push/push.py:L96]` · `[SRC:cognee/api/v1/push/push.py:L1-L10]` · `[SRC:cognee/api/v1/push/push.py:L112-L123]` |
| `cognee.PushResult` | dataclass | `status, dataset_name, target_dataset, num_nodes, num_edges, remote_response, pipeline_run_id=None` | `[AST:cognee/api/v1/push/push.py:L26]` |
| `cognee.export` | async fn | `dataset="main_dataset", format="pydantic", destination=None, user=None, link_relations=False, include_permissions=False` → `GraphSnapshot` for `"pydantic"`, `ExportResult` for `"cogx"`/`"json"`/`"graphml"`/`"cypher"` (3 `@overload`s + implementation) | `[AST:cognee/api/v1/export/export.py:L16]` · `[SRC:cognee/api/v1/export/export.py:L49-L56]` |
| `cognee.ExportResult` | dataclass | `format, destination, dataset_name, dataset_id, num_nodes, num_edges` | `[AST:cognee/modules/migration/export.py:L41]` |
| `cognee.report` | async fn | `datasets="main_dataset", output_path="graph_report.md", top_n=10, user=None` → Markdown `str` (Graph Insight Report: hub nodes, surprising cross-node_set connections, edge provenance, LLM-suggested questions; no storage changes; `output_path=None` skips the file) | `[AST:cognee/api/v1/report/report.py:L13]` |
| `cognee.validate` | async fn | `dataset="main_dataset", user=None` → `ValidationReport`. Read-only graph/vector consistency check: orphaned edges, identity-id mismatches, missing vector entries. | `[AST:cognee/api/v1/validate/validate.py:L198]` · `[SRC:cognee/api/v1/validate/validate.py:L11-L29]` |
| `cognee.ValidationReport` / `ValidationIssue` / `ValidationStatus` | pydantic models / str enum | `ValidationReport(status, summary, issues)`, `ValidationIssue(severity, type, detail)`, `ValidationStatus.HEALTHY`/`DEGRADED`/`UNHEALTHY` | `[AST:cognee/api/v1/validate/validate.py:L105]` · `[AST:cognee/api/v1/validate/validate.py:L99]` · `[AST:cognee/api/v1/validate/validate.py:L93]` |
| `cognee.get_schema_inventory` | async fn | `dataset=None, samples_per_type=5, sort="count"` → list of `{type, count, samples, sample_size, relationships}` dicts summarizing the graph by semantic type | `[AST:cognee/api/v1/visualize/get_schema_inventory.py:L77]` |
| `cognee.get_memory_provenance_graph` / `visualize_memory_provenance` | async fns | `include_memory=False, scope_tenant_ids=None, scope_user_ids=None, scope_dataset_ids=None` (+ leading `destination_file_path=None` on the render) → `(nodes, edges)` / HTML `str`. Pass a scope in multi-tenant deployments: unscoped, it reads every tenant's actors, datasets and files. | `[AST:cognee/api/v1/visualize/memory_provenance.py:L645]` · `[AST:cognee/api/v1/visualize/memory_provenance.py:L848]` · `[SRC:cognee/api/v1/visualize/memory_provenance.py:L656-L659]` |
| `cognee.MemoryEntry` / `QAEntry` / `TraceEntry` / `FeedbackEntry` | type alias / pydantic models | `MemoryEntry = QAEntry \| TraceEntry \| FeedbackEntry \| SkillRunEntry`, discriminated by a literal `type` (`"qa"`, `"trace"`, `"feedback"`, `"skill_run"`). Pass one to `remember()`; QA, trace and feedback entries need a `session_id`. | `[SRC:cognee/memory/entries.py:L129]` · `[AST:cognee/memory/entries.py:L24]` · `[AST:cognee/memory/entries.py:L40]` · `[AST:cognee/memory/entries.py:L62]` · `[SRC:cognee/api/v1/remember/remember.py:L434-L438]` |
| `cognee.tools` | module | `register_sql_connection`, `list_sql_connections`, `remove_sql_connection`, plus write-proposal helpers (`propose_sql_write`, `propose_corrections`, `list_write_proposals`, `apply_write_proposal`, `reject_write_proposal`) — all async, each with an optional `user`. [Signatures](references/full-api-reference.md#tool-connections--cogneetools). Registered connections feed `recall(scope=["tools"])` once `TOOL_CALLS_ENABLED=true`. | `[SRC:cognee/api/v1/tools/tools.py:L1-L14]` · `[SRC:cognee/api/v1/tools/__init__.py:L1-L11]` |
| `cognee.SessionRecord` / `SessionModelUsage` | SQLAlchemy models | Relational session-lifecycle rows: one per (user, session_id) with status, token and cost counters; per-(session, user, model) token and cost aggregates. Both have `to_dict()`. Not the internal `SessionRecord` TypedDict in `memory_provenance.py`. | `[AST:cognee/modules/session_lifecycle/models.py:L10]` · `[AST:cognee/modules/session_lifecycle/models.py:L96]` |
| `cognee.logger` | structlog logger | The logger `cognee/__init__.py` binds at import as `logger = setup_logging()` and uses to log which `.env` it loaded. `setup_logging` configures logging once per process (level from `LOG_LEVEL`, default `INFO`); later calls return a logger without reconfiguring. Its `-> bool` annotation is wrong: it returns the logger. | `[SRC:cognee/__init__.py:L34]` · `[SRC:cognee/__init__.py:L35]` · `[SRC:cognee/shared/logging_utils.py:L345]` · `[SRC:cognee/shared/logging_utils.py:L365-L369]` · `[SRC:cognee/shared/logging_utils.py:L632]` |

### Memory migration — `cognee.migration`

`cognee.migration` is a module (`from . import migration`); import its names with `from cognee.migration import ...`. Each re-exports a definition from `cognee.modules.migration`. A `MemorySource` turns an external memory system's export into COGX (Cognee eXchange format) records that `cognee.remember()` ingests; a COGX archive is a directory holding `manifest.json` plus one JSONL file per record kind. `[SRC:cognee/__init__.py:L98]` · `[SRC:cognee/migration/__init__.py:L22-L52]` · `[SRC:cognee/modules/migration/cogx.py:L1-L10]`

| Export | Kind | Key params | Source |
|---|---|---|---|
| `MemorySource` | abstract class | `MemorySource(mode="re-derive")`: base of every source; subclasses implement async `records()`, which yields COGX records. `mode` must be one of `IMPORT_MODES`, else `ValueError`. | `[SRC:cognee/modules/migration/sources/base.py:L36]` · `[SRC:cognee/modules/migration/sources/base.py:L79-L86]` |
| `IMPORT_MODES` | tuple | `("re-derive", "preserve", "hybrid")`: `"re-derive"` ingests the raw content and runs cognify (LLM tokens); `"preserve"` maps the source's extracted entities and facts into the graph with zero LLM calls and stores raw content uncognified; `"hybrid"` preserves the source graph and cognifies the raw content. | `[SRC:cognee/modules/migration/sources/base.py:L19]` · `[SRC:cognee/modules/migration/sources/base.py:L39-L48]` |
| `Mem0Source` | class | `Mem0Source(data, mode="re-derive")`: `data` is a path to a Mem0 export, or the already-parsed list or dict (`results`/`memories`/`items` wrapper); each memory becomes a `COGXMemory` scoped by `user_id`/`agent_id`/`run_id`. An unrecognized shape raises `ValueError`. | `[SRC:cognee/modules/migration/sources/mem0.py:L26]` · `[SRC:cognee/modules/migration/sources/mem0.py:L1-L12]` |
| `ZepSource` | class | `ZepSource(data, mode="hybrid")`: path or dict of a Zep/Graphiti JSON export; episodes become `COGXEpisode`, entity nodes `COGXEntity`, relation edges `COGXFact` with `valid_at`/`invalid_at`. A non-object export raises `ValueError`. | `[SRC:cognee/modules/migration/sources/zep.py:L57]` · `[SRC:cognee/modules/migration/sources/zep.py:L1-L21]` |
| `GraphitiSource` | class | Subclass of `ZepSource` for OSS Graphiti exports (same shape, same `ZepSource(data, mode="hybrid")` constructor), with `source_system="graphiti"`. | `[SRC:cognee/modules/migration/sources/zep.py:L136]` |
| `LettaSource` | class | `LettaSource(data, mode="re-derive")`: path or dict of a Letta Agent File (`.af`); core memory blocks become `COGXMemoryBlock`, message history one `COGXEpisode` per agent, archival passages `COGXDocument`. | `[SRC:cognee/modules/migration/sources/letta.py:L72]` · `[SRC:cognee/modules/migration/sources/letta.py:L1-L12]` |
| `COGXArchiveSource` | class | `COGXArchiveSource(directory, mode="preserve")`: re-imports an archive written by `cognee.export(format="cogx")` (restore, or Cognee-to-Cognee migration); zero-LLM by default. An archive of a newer major COGX version raises `ValueError`. | `[SRC:cognee/modules/migration/sources/cogx_archive.py:L19]` · `[SRC:cognee/modules/migration/sources/cogx_archive.py:L20-L29]` |
| `COGX_VERSION` | str | `"0.1"`: the COGX version this reader writes; `read_manifest` rejects an archive of a newer major version. | `[SRC:cognee/modules/migration/cogx.py:L22]` |
| `COGXScope` | pydantic model | `user_id=None, agent_id=None, session_id=None, run_id=None`: a record's ownership scope in the source system. | `[SRC:cognee/modules/migration/cogx.py:L60]` |
| `COGXDocument` / `COGXEpisode` / `COGXEntity` / `COGXFact` / `COGXMemory` / `COGXMemoryBlock` | pydantic models | Record kinds, each with a literal `kind` and the base fields `external_system="unknown", external_id, scope=COGXScope(), created_at=None, updated_at=None, metadata={}`. `COGXDocument(content, title=None, mime_type=None)`; `COGXEpisode(turns=[], title=None)`; `COGXEntity(name, entity_type=None, description=None, aliases=[], attributes={})`; `COGXFact(subject_ref, predicate, object_ref, fact_text=None, valid_at=None, invalid_at=None, confidence=None, provenance=[])`; `COGXMemory(content, categories=[])`; `COGXMemoryBlock(label, value, limit=None)`. | `[SRC:cognee/modules/migration/cogx.py:L78]` · `[SRC:cognee/modules/migration/cogx.py:L93]` · `[SRC:cognee/modules/migration/cogx.py:L101]` · `[SRC:cognee/modules/migration/cogx.py:L112]` · `[SRC:cognee/modules/migration/cogx.py:L131]` · `[SRC:cognee/modules/migration/cogx.py:L139]` · `[SRC:cognee/modules/migration/cogx.py:L69-L75]` |
| `COGXTurn` | pydantic model | `role, content, occurred_at=None`: one turn of a `COGXEpisode`. | `[SRC:cognee/modules/migration/cogx.py:L87]` |
| `COGXRawNode` | pydantic model | `kind="raw_node", properties={}`: a graph node kept verbatim when no typed mapping exists; rehydrated into a DataPoint on import. | `[SRC:cognee/modules/migration/cogx.py:L148]` |
| `COGXRecord` | type alias | `COGXDocument \| COGXEpisode \| COGXEntity \| COGXFact \| COGXMemory \| COGXMemoryBlock \| COGXRawNode`, discriminated by `kind`. | `[SRC:cognee/modules/migration/cogx.py:L160]` |
| `COGXManifest` | pydantic model | `cogx_version=COGX_VERSION, source_system="unknown", exported_at=None, counts={}, embedding_model=None, migration_revision=None, notes=[]`: an archive's `manifest.json`. | `[SRC:cognee/modules/migration/cogx.py:L180]` |
| `read_manifest` | sync fn | `read_manifest(directory) -> COGXManifest \| None`: `None` when the directory has no `manifest.json`; a newer major COGX version raises `ValueError`. | `[SRC:cognee/modules/migration/cogx.py:L276]` |
| `read_archive` | sync generator | `read_archive(directory) -> Iterator[COGXRecord]`: streams the typed records of each JSONL file, then the raw nodes as `COGXRawNode`; a missing directory raises `FileNotFoundError`. | `[SRC:cognee/modules/migration/cogx.py:L322]` |
| `EXPORT_FORMATS` | tuple | `("pydantic", "cogx", "json", "graphml", "cypher")`: the formats `export_dataset` (and `cognee.export`) accept. | `[SRC:cognee/modules/migration/export.py:L35]` |
| `export_dataset` | async fn | `export_dataset(dataset="main_dataset", format="pydantic", destination=None, user=None, link_relations=False, include_permissions=False) -> ExportResult \| GraphSnapshot`: the function `cognee.export` delegates to, same parameters and behavior. An unknown format raises `ValueError`. | `[SRC:cognee/modules/migration/export.py:L198]` · `[SRC:cognee/api/v1/export/export.py:L99]` |
| `GraphSnapshot` | pydantic model | `dataset_name="", dataset_id="", nodes=[]` (DataPoint instances), `edges=[]` (`GraphEdge`); `nodes_of_type(node_type)`, `find(node_type=None, **field_filters)`, `link_relations()`, `save(path)`, classmethod `load(path)`. Nodes are rehydrated into the DataPoint subclasses that produced them. | `[SRC:cognee/modules/migration/snapshot.py:L161]` · `[SRC:cognee/modules/migration/snapshot.py:L1-L18]` |
| `GraphEdge` | pydantic model | `source_id, target_id, relationship, properties={}` | `[SRC:cognee/modules/migration/snapshot.py:L152]` |
| `build_snapshot` | sync fn | `build_snapshot(nodes, edges, dataset_name="", dataset_id="", link_relations=False) -> GraphSnapshot` from `get_graph_data()` shapes: `(node_id, properties)` and `(source_id, target_id, relationship_name, properties)` tuples. | `[SRC:cognee/modules/migration/snapshot.py:L243]` |
| `datapoint_registry` | sync fn | `datapoint_registry() -> dict[str, type[DataPoint]]`: every loaded DataPoint subclass, keyed by class name and by `module.ClassName`. | `[SRC:cognee/modules/migration/snapshot.py:L39]` |
| `rehydrate_node` | sync fn | `rehydrate_node(properties, registry=None) -> DataPoint`: the registered class for the node's `type`, else a dynamically created DataPoint subclass with `extra="allow"`. | `[SRC:cognee/modules/migration/snapshot.py:L116]` |

`ExportResult`, the 29th name, is in the Further exports table above.

## Deprecations & Gotchas

> Current-state deprecations and source/docs discrepancies at v1.6.2 (`ba3631f2`). The V2 memory API coexists with the V1 API.

- **`low_level` is not in the top-level `cognee/__init__.py` imports**, but the `cognee/low_level.py` module still re-exports `DataPoint` (`ExtendableDataPoint`), `setup`, `Edge`, `FromIdentity` and graph-model spec helpers. Import it explicitly: `from cognee.low_level import DataPoint, setup` (or the full paths `from cognee.infrastructure.engine import ExtendableDataPoint as DataPoint`, `from cognee.modules.engine.operations.setup import setup`). `[SRC:cognee/low_level.py:L1-L9]`
- **`cognee.run_migrations()` is the top-level migration entry point; `cognee.run_startup_migrations` (the v1.0.0 name) no longer exists** and raises `AttributeError`. `run_migrations() -> list[str]` runs the relational Alembic migrations in a worker thread, then the graph and vector chains, once per process, and returns the ids of databases that failed; a relational failure raises `MigrationError`. `COGNEE_ALEMBIC_PATH` overrides the Alembic script location. Migrations also run automatically on the first `add`, `cognify`, `remember`, `memify` or `improve` call, which raises `MigrationError` when a database it targets failed to migrate. `ENABLE_AUTO_MIGRATIONS=false` disables every automatic run (`run_migrations()` then returns `[]`); `cognee-cli upgrade` remains the explicit path. `[AST:cognee/run_migrations.py:L18]` · `[SRC:cognee/__init__.py:L71]` · `[SRC:cognee/modules/migrations/startup.py:L160-L184]` · `[SRC:cognee/modules/migrations/startup.py:L386-L405]` · `[SRC:cognee/modules/migrations/startup.py:L443-L451]` · `[SRC:cognee/modules/migrations/startup.py:L14-L19]` · `[SRC:cognee/modules/migrations/startup.py:L144]` · `[SRC:cognee/api/v1/add/add.py:L255-L257]`
- **`cognee.delete(data_id, dataset_id, mode="soft", user=None)` is deprecated since cognee v0.3.9.** Use `await cognee.datasets.delete_data(dataset_id=..., data_id=...)` or the V2 `await cognee.forget(data_id=..., dataset=...)` instead. The old function is now defined in `cognee/api/v1/delete/__init__.py` (source file `delete.py` is empty) and decorated with `@deprecated(version="0.3.9")`. `[AST:cognee/api/v1/delete/__init__.py:L12]` · `[SRC:cognee/api/v1/delete/__init__.py:L9-L11]`
- **`cognee.pipelines` vs the `cognee/pipelines/` package.** The top-level name resolves to `cognee/modules/pipelines/` (via `from .modules import pipelines`), whose `run_pipeline` is the dataset-aware orchestrator (dataset locking, `PipelineRun` records, `PipelineRunInfo` events). The separate `cognee/pipelines/` **package** exports `Drop` and lazy legacy re-exports via `__getattr__`: `from cognee.pipelines import Task` (or `run_tasks`, `run_tasks_parallel`) gives the same objects as `cognee.modules.pipelines`, but `from cognee.pipelines import run_pipeline` gives the lightweight `BoundTask` runner ([signature](references/pipelines-and-datapoints.md#lightweight-runner-cogneepipelinesrun_pipeline)), with no dataset locking or run records. Import the orchestrator from `cognee.modules.pipelines`. `[SRC:cognee/modules/pipelines/__init__.py:L23-L37]` · `[SRC:cognee/pipelines/__init__.py:L22-L28]` · `[SRC:cognee/modules/pipelines/operations/run_pipeline.py:L37-L45]`
- **`search()` defaults changed.** `query_type` defaults to `SearchType.HYBRID_COMPLETION`, which silently defers to `GRAPH_COMPLETION` for a custom `node_type`, `node_name` with `node_type=None`, `neighborhood_depth`, `feedback_influence > 0` or a missing chunk collection. Results do not name the type that ran, so pin `query_type` when the result shape matters. `top_k` defaults to 15 per dataset; `HYBRID_COMPLETION` caps each lane at `min(top_k, 10)`, so raise a lane with the `chunks_top_k`, `entities_top_k` or `facts_top_k` keys in `retriever_specific_config`. `AGENTIC_COMPLETION` and `SKILLS` require exactly one explicit dataset. `[SRC:cognee/api/v1/search/search.py:L43]` · `[SRC:cognee/api/v1/search/search.py:L89-L93]` · `[SRC:cognee/modules/search/methods/search.py:L638-L640]` · `[SRC:cognee/api/v1/search/search.py:L215-L218]` · `[SRC:cognee/api/v1/search/search.py:L359-L372]`
- **A blocking `remember()` raises on failure.** With the defaults (`run_in_background=False`, `raise_on_error=True`) a failed graph build raises `CognifyFailedError`, and a preflight `validate_provider_config()` raises on inconsistent LLM or embedding config; status `"errored"` only appears with `run_in_background=True` or `raise_on_error=False`. `self_improvement=True` is non-fatal: a failed `improve()` lands on `result.improve_error` and the status stays `"completed"`/`"session_stored"`. `IMPROVE_AUTO_ENABLED=false` turns automatic improves off, and `IMPROVE_DEBOUNCE_ENTRIES`/`IMPROVE_DEBOUNCE_SECONDS` throttle the session-to-graph bridge. `[SRC:cognee/api/v1/remember/remember.py:L1940-L1947]` · `[SRC:cognee/api/v1/remember/remember.py:L2001-L2007]` · `[SRC:cognee/api/v1/remember/remember.py:L1398-L1421]` · `[SRC:cognee/api/v1/remember/remember.py:L1961-L1967]` · `[SRC:cognee/api/v1/remember/remember.py:L907-L915]` · `[SRC:cognee/modules/improve/config.py:L12-L14]`
- **`cognee.agent_memory` requires the wrapped function to be async** — decorating a sync function raises `CogneeValidationError`. If `memory_query_from_method="name"` is set, the method must have a parameter literally named `name`. `save_session_traces`, `with_session_memory` and `persist_session_trace_after` raise `CogneeValidationError` at decoration time unless caching is enabled. Traces go to the session cache, not the graph; they reach the graph only through `persist_session_trace_after` or `improve(session_ids=...)`. Passing the old `save_traces=` raises `TypeError`. `[SRC:cognee/modules/agent_memory/decorator.py:L86-L100]` · `[SRC:cognee/modules/agent_memory/runtime.py:L120-L129]` · `[SRC:cognee/modules/improve/stages.py:L142-L155]`
- **`cognee.serve()` connection and routing rules.** A bare `serve()` tries `COGNEE_SERVICE_URL`, then saved credentials, and runs the Auth0 Device Code Flow only if `auth0_client_id` or `COGNEE_AUTH0_DEVICE_CLIENT_ID` is set; otherwise it raises `CogneeConfigurationError` (`ServeConfigurationError`). `serve(url=...)` probes auth after the health check and raises `CogneeConfigurationError` (`ServeAuthenticationError`) on 401/403, so `api_key=` is effectively required for instances with auth enabled; credentials are saved only after the probe passes. While connected, `remember`, `recall`, `improve`, `forget` and also `add`, `cognify`, `update`, `datasets.list_data` and `search` forward to the remote. Remote `add` returns a `SimpleNamespace`; remote `cognify` raises `ValueError` for `dry_run`, `chunk_attachment` or `extractor`; remote `update` warns and drops config arguments the remote cannot take; remote `remember` raises `ValueError` for `session_ids`, an explicit `extractor`, `MemorySource` imports and `dry_run` (including `"presort"`). `visualize`/`visualize_graph` always render the local graph. `[SRC:cognee/api/v1/serve/serve.py:L220-L252]` · `[SRC:cognee/api/v1/serve/serve.py:L98-L130]` · `[SRC:cognee/api/v1/add/add.py:L218-L227]` · `[SRC:cognee/api/v1/cognify/cognify.py:L352-L380]` · `[SRC:cognee/api/v1/update/update.py:L139-L168]` · `[SRC:cognee/api/v1/datasets/datasets.py:L145-L151]` · `[SRC:cognee/api/v1/search/search.py:L267-L285]` · `[SRC:cognee/api/v1/remember/remember.py:L1366-L1396]` · `[SRC:cognee/api/v1/remember/remember.py:L1025-L1031]` · `[SRC:cognee/api/v1/remember/remember.py:L1155-L1161]` · `[SRC:cognee/api/v1/remember/remember.py:L1239-L1245]` · `[SRC:cognee/api/v1/visualize/visualize.py:L243-L259]`
- **`visualize_graph` HTML embeds session history.** With the default `include_session_events=True`, the user's session search and feedback Q&A is collected into the HTML's Memory timeline; pass `include_session_events=False` before sharing the file. `[SRC:cognee/api/v1/visualize/visualize.py:L217-L222]`
- **`cognee.start_ui` is sync (not async) and requires a `pid_callback` positional argument.** Do not call `await cognee.start_ui()` — the function returns `Optional[subprocess.Popen]` synchronously. Signature: `start_ui(pid_callback, port=3000, open_browser=True, auto_download=False, start_backend=False, backend_port=8000, start_mcp=False, mcp_port=8001)`. `pid_callback` receives an int PID or a `(pid, container_name)` tuple; after a successful start the caller owns shutdown of everything reported through it. A busy `mcp_port` skips MCP with a warning, and a failed startup cleans up what it created and returns `None`. `[AST:cognee/api/v1/ui/ui.py:L514]` · `[SRC:cognee/api/v1/ui/ui.py:L546-L550]` · `[SRC:cognee/api/v1/ui/ui.py:L619-L624]` · `[SRC:cognee/api/v1/ui/ui.py:L584-L589]`
- **`cognee.start_visualization_server` is a module, not a function.** The top-level `__init__.py` re-imports the submodule name. To start the visualization HTTP server, call `cognee.start_visualization_server.visualization_server(port)` which is synchronous: it serves files from the working directory on a background thread bound to `0.0.0.0` and returns a `shutdown()` callable. `[SRC:cognee/api/v1/visualize/start_visualization_server.py:L6]` · `[SRC:cognee/shared/utils.py:L481-L508]`

See Full API Reference for complete parameter tables and behavioral notes.

## Key Types

### `SearchType` (enum) — `cognee.SearchType`

All modes accepted by `cognee.search(query_type=...)` and `cognee.recall(query_type=...)`:

| Mode | Use for |
|---|---|
| `HYBRID_COMPLETION` (default) | Document passages plus entity neighbourhoods, then LLM completion; defers to `GRAPH_COMPLETION` when the request needs graph-only features |
| `GRAPH_COMPLETION` | LLM answer backed by graph context — best for complex Q&A |
| `RAG_COMPLETION` | Traditional chunk-based RAG without graph structure |
| `CHUNKS` | Raw semantic chunk retrieval, no LLM |
| `CHUNKS_LEXICAL` | Token/BM25-style exact-term chunk search |
| `SUMMARIES` | Pre-generated hierarchical document summaries |
| `TRIPLET_COMPLETION` | Subject-predicate-object graph Q&A |
| `GRAPH_SUMMARY_COMPLETION` | Graph + summaries hybrid |
| `GRAPH_COMPLETION_COT` | Deeper reasoning with chain-of-thought over graph |
| `GRAPH_COMPLETION_CONTEXT_EXTENSION` | Broader graph context retrieval |
| `GRAPH_COMPLETION_DECOMPOSITION` | Decomposes complex questions into sub-queries for broader graph coverage |
| `AGENTIC_COMPLETION` | ReAct-style loop over memory retrieval, skills and tool calls; the only type that accepts `skills`/`tools`; needs exactly one explicit dataset |
| `CODE` | Deterministic, model-free queries and traversal over an Enola code graph; pairs with `code_query` |
| `GRAPH_REPORT` | Graph Insight Report (hub nodes and more) computed from the current graph |
| `SKILLS` | Semantic discovery of dataset-scoped Skill playbooks (metadata only); needs exactly one explicit dataset |
| `CYPHER` | Raw Cypher queries (enabled by default; set `ALLOW_CYPHER_QUERY=false` to block `CYPHER` and `NATURAL_LANGUAGE`) |
| `NATURAL_LANGUAGE` | Natural-language → graph query translation |
| `TEMPORAL` | Time-aware graph search (pairs with `temporal_cognify=True`) |
| `CODING_RULES` | Queries against the `coding_agent_rules` node_set by default |
| `FEELING_LUCKY` | Cognee auto-selects the best search type |

`[AST:cognee/modules/search/types/SearchType.py:L4]` · `[SRC:cognee/api/v1/search/search.py:L89-L93]` · `[SRC:cognee/modules/retrieval/agentic_retriever.py:L1-L7]` · `[SRC:cognee/api/v1/search/search.py:L115-L119]` · `[SRC:cognee/modules/retrieval/graph_report_retriever.py:L61-L66]` · `[SRC:cognee/modules/retrieval/skills_retriever.py:L46-L54]` · `[SRC:cognee/modules/search/methods/get_search_type_retriever_instance.py:L408-L412]` · `[SRC:cognee/modules/retrieval/coding_rules_retriever.py:L19-L20]`

### `Task` — `cognee.pipelines.Task` (or `cognee.modules.pipelines.Task`)

Constructor: `Task(executable, *args, task_config=None, batch_size=None, enriches=False, needs_llm=True, **kwargs)`. Wraps any callable (function, coroutine function, generator, or async generator). Detects type via `inspect` and picks the right execute path. `task_config={"batch_size": N}` (or `batch_size=N`) controls batching. `needs_llm=False` on tasks that never call the LLM lets `run_pipeline` skip the first-run LLM probe (`pipeline_needs_llm`); the flag is not forwarded to the executable. `[AST:cognee/modules/pipelines/tasks/task.py:L188]` · `[SRC:cognee/modules/pipelines/tasks/task.py:L201-L222]` · `[SRC:cognee/modules/pipelines/tasks/task.py:L253-L254]`

### `Drop` — `cognee.Drop` (or `from cognee.pipelines import Drop`)

Singleton sentinel. Returning `Drop` from any pipeline step filters that item out of the stream. `bool(Drop) is False`, `repr(Drop) == "Drop"`. `[SRC:cognee/pipelines/types.py:L32]`

### `RememberResult` — `cognee.RememberResult`

Promise-like result returned by `cognee.remember()`. Printable for a quick summary; awaitable to block until a background run finishes. Status values: `"running"`, `"completed"`, `"errored"`, `"session_stored"`; a blocking `remember()` (the default) raises `CognifyFailedError` when the graph build fails, so `"errored"` appears only with `run_in_background=True` or `raise_on_error=False`. Attributes: `dataset_name`, `dataset_id`, `session_ids` (+ `session_id` property), `pipeline_run_id`, `error`, `elapsed_seconds`, `content_hash`, `items_processed`, `items`, `raw_result`, `improve` (`ImproveResult` or `None`), `improve_error`, and `entry_type`/`entry_id` (set for typed `MemoryEntry` writes; shown in `to_dict()` but not in `repr`). `[AST:cognee/api/v1/remember/remember.py:L600]` · `[SRC:cognee/api/v1/remember/remember.py:L655-L675]` · `[SRC:cognee/api/v1/remember/remember.py:L1940-L1947]`

### `MemoryEntry`, `ExportResult`, `PushResult`, `ValidationReport`

Typed `remember()` payloads (`QAEntry`, `TraceEntry`, `FeedbackEntry`, plus `SkillRunEntry`, which is not exported from top-level `cognee`; import it from `cognee.memory`) and the result types of `export`, `push` and `validate` are summarized in the Further exports table above; full fields are in the reference. `[SRC:cognee/memory/__init__.py:L1-L9]`

### `DataPoint` — `cognee.infrastructure.engine.ExtendableDataPoint`

Pydantic base class for graph-native entities. Assigning one `DataPoint` instance to another's field creates an edge; the field name becomes the edge label. Use `metadata = {"index_fields": [...]}` to mark which fields should be embedded in the vector store. Also importable as `from cognee.low_level import DataPoint` (alias of `ExtendableDataPoint`). `cognee.infrastructure.engine` also exports the base class itself as `DataPoint`; `ExtendableDataPoint` subclasses it and adds nothing, so either import works for custom models. `[SRC:cognee/low_level.py:L2]` · `[SRC:cognee/infrastructure/engine/__init__.py:L1-L4]` · `[SRC:cognee/infrastructure/engine/models/ExtendableDataPoint.py:L4-L7]` · `[EXT:https://docs.cognee.ai/guides/custom-data-models]`

### Exceptions — `cognee.exceptions`

- `CogneeApiError` — base class (HTTP 500 default)
- `CogneeSystemError` — 500
- `CogneeValidationError` — 422
- `CogneeConfigurationError` — 500
- `CogneeTransientError` — 503

All six [`__init__` parameters](references/full-api-reference.md#cogneeexceptions--error-hierarchy) are optional; each class sets its own `message`, `name` and `status_code` defaults. `str(exc)` is `"<name>: <message> (Status code: <code>)"`, with `" Fix: <remediation>"` (`REMEDIATION_MARKER`) appended when set; the auto-log line is `"%s raised (Status code: %s): %s"`. `cognee.exceptions` also exports `REMEDIATION_MARKER`, `find_remediation` and `remediation_for`. `[AST:cognee/exceptions/exceptions.py:L10]` · `[SRC:cognee/exceptions/exceptions.py:L28-L66]` · `[SRC:cognee/exceptions/__init__.py:L15]`

## Architecture at a Glance

- **Three-layer storage with node_set-aware graph:** relational (provenance), vector (semantic), graph (entities + edges + `node_set` tagging). `node_set` tags passed to `cognee.add` become first-class graph nodes after `cognify`. `[EXT:https://docs.cognee.ai/core-concepts/overview]`
- **V1 vs V2 APIs coexist:** V1 (`add → cognify → search`) exposes the full graph-building primitives; V2 (`remember → recall`) is a thin, opinionated wrapper that folds the two most common calls into one per step, adds `improve`/`forget`/`serve`/`agent_memory` for agent workflows, and supports cloud routing via `serve()` (which also routes V1 `add`/`cognify`/`update`/`search`). Both share the same underlying pipelines.
- **Default backends (pinned in `pyproject.toml`):** LLM via `litellm` / `openai` / `instructor`; vector `lancedb` + `pylance`; graph `ladybug==0.19.0` (`>=0.17.0,<0.18` on macOS 13/14; default provider `"ladybug"`, `"kuzu"` still accepted; the graph DB runs in a subprocess by default) + `networkx`; relational `sqlalchemy` + `aiosqlite` + `alembic`. `fastembed` (the keyless default embedder, `BAAI/bge-small-en-v1.5`), `dlt[sqlalchemy]` and `enola-cli` are core dependencies. Optional extras: `neo4j`, `postgres` (`pgvector`+`asyncpg`), `scraping`, `gliner` (LLM-free extraction). `[SRC:pyproject.toml:L22-L119]` · `[SRC:pyproject.toml:L97-L100]` · `[SRC:cognee/infrastructure/databases/graph/config.py:L47]` · `[SRC:cognee/infrastructure/databases/graph/config.py:L62]` · `[SRC:cognee/infrastructure/databases/graph/get_graph_engine.py:L446]` · `[SRC:cognee/infrastructure/databases/vector/embeddings/config.py:L28-L29]` · `[SRC:pyproject.toml:L121-L146]` · `[SRC:pyproject.toml:L248]`
- **Async-first:** every ingestion/graph/search/memify/update/remember/recall/improve/forget/serve/push/export/report/validate function is a coroutine — call via `await` from inside an `async def` and drive with `asyncio.run(main())`. The exceptions are `start_ui`, `start_visualization_server.visualization_server`, `get_cognee_version`, `datasets.discover_datasets`, the `agent_memory` decorator factory, the `cognee.config` static methods, the `enable_tracing`/`disable_tracing`/`get_*_trace`/`clear_traces` family, and `cognee.migration`'s `read_manifest`, `read_archive`, `build_snapshot`, `datapoint_registry` and `rehydrate_node`.

## CLI

Cognee ships a CLI (`cognee-cli`) for terminal usage, but it lives outside this skill's scope. Quick reference from the upstream repo:

```bash
cognee-cli remember "Cognee turns documents into AI memory."   # add + cognify (+ improve)
cognee-cli recall "What does cognee do?"
cognee-cli add "Cognee turns documents into AI memory."
cognee-cli cognify
cognee-cli search "What does cognee do?"
cognee-cli -ui   # Launches UI, backend API, and MCP server together
```

`[SRC:AGENTS.md:L39-L46]` — use this skill for the Python API only; reach for `cognee-cli` or `cognee-mcp` for CLI/MCP flows.

<!-- [MANUAL:additional-notes] -->
<!-- Add custom notes here. This section is preserved during skill updates. -->
<!-- [/MANUAL:additional-notes] -->

---

**Full API details, complete type definitions, and integration patterns:** see [references/full-api-reference.md](references/full-api-reference.md). Detailed config setter reference: [references/config.md](references/config.md). Extended core-workflow walkthrough with env matrix: [references/core-workflow.md](references/core-workflow.md). Custom pipelines and DataPoint primitives: [references/pipelines-and-datapoints.md](references/pipelines-and-datapoints.md).
