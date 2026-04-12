# Full API Reference — oms-cognee

Progressive-disclosure detail for every `cognee/__init__.py` public export plus the pipeline and type primitives. Companion to `SKILL.md`; Tier 1 summary tables there contain name/purpose/key-params only.

## Contents

- [Core workflow functions](#core-workflow-functions)
  - [cognee.add](#cogneeadd--ingest-data-into-a-dataset)
  - [cognee.cognify](#cogneecognify--build-the-knowledge-graph)
  - [cognee.search](#cogneesearch--query-the-knowledge-graph)
  - [cognee.memify](#cogneememify--enrich-an-existing-graph)
  - [cognee.update](#cogneeupdate--replace-data-inside-a-dataset)
- [Dataset management — cognee.datasets](#dataset-management--cogneedatasets)
- [Configuration — cognee.config](#configuration--cogneeconfig)
- [Pipelines primitives](#pipelines-primitives--cogneepipelines-and-cogneemodulespipelines)
- [Data primitives — cognee.low_level](#data-primitives--cogneelow_level)
- [Observability / Tracing](#observability--tracing--cogneeenable_tracing-and-friends)
- [Visualization](#visualization--cogneevisualize_graph)
- [Pruning](#pruning--cogneeprune)
- [Sessions](#sessions--cogneesession)
- [Migrations](#migrations--cogneerun_migrations)
- [Full Type Definitions](#full-type-definitions)
- [Full Integration Patterns](#full-integration-patterns)

## Core workflow functions

#### `cognee.add(...)` — ingest data into a dataset

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
    importance_weight: Optional[float] = 0.5,
    **kwargs,
) -> PipelineRunInfo | None
```

**Accepted `data` forms:** raw text strings (anything not starting with `/` or `file://`), absolute file paths, `file://` URLs, `s3://` paths, HTTP(S) URLs, open binary file handles, lists of any of the above, or DLT `DataItem` objects. Cognee auto-detects supported file formats: `.txt`, `.md`, `.csv`, `.pdf`, `.png/.jpg/.jpeg` (OCR/vision), `.mp3/.wav` (transcription), source files (`.py/.js/.ts/...`), Office docs (`.docx/.pptx`).

**Required env:** `LLM_API_KEY` for content processing. Cognee uses the default user `default_user@example.com` when `user` is None (auto-created on first use). See `references/core-workflow.md` for full env-var list.

Provenance: `[AST:cognee/api/v1/add/add.py:L21]`

#### `cognee.cognify(...)` — build the knowledge graph

```python
async def cognify(
    datasets: Union[str, list[str], list[UUID]] = None,
    user: User = None,
    graph_model: BaseModel = KnowledgeGraph,
    chunker = TextChunker,
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
) -> Union[dict, list[PipelineRunInfo]]
```

**Pipeline:** document classification → text chunking → entity extraction → relationship detection → graph construction (with embeddings) → hierarchical summarization. Supports custom `graph_model` (Pydantic) for domain schemas and `custom_prompt` for extraction guidance. Use `temporal_cognify=True` to extract events with timestamps (pairs with `SearchType.TEMPORAL`).

**Returns:** in blocking mode, a dict mapping `dataset_id → PipelineRunInfo`. In background mode, a list of `PipelineRunInfo` — use `pipeline_run_id` to track status.

Provenance: `[AST:cognee/api/v1/cognify/cognify.py:L44]`

#### `cognee.search(...)` — query the knowledge graph

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
    node_name_filter_operator: str = "OR",
    only_context: bool = False,
    session_id: Optional[str] = None,
    wide_search_top_k: Optional[int] = 100,
    triplet_distance_penalty: Optional[float] = 6.5,
    feedback_influence: float = 0.0,
    verbose: bool = False,
    retriever_specific_config: Optional[dict] = None,
) -> List[SearchResult]
```

**Key behaviors:**

- **`node_name_filter_operator`** must be `"OR"` or `"AND"` — anything else raises `CogneeValidationError`. `[AST:cognee/api/v1/search/search.py:L198]`
- **`only_context=True`** returns the raw retrieved context as `Union[str, List[str]]` without calling the LLM — useful for debugging or custom prompt construction. `[EXT:https://docs.cognee.ai/guides/search-basics]`
- **`session_id`** wires the search into a conversation session — only honored by `GRAPH_COMPLETION`, `RAG_COMPLETION`, `TRIPLET_COMPLETION`. Other search types ignore it.
- **`ENABLE_BACKEND_ACCESS_CONTROL` env var** changes the result shape: when `=true`, results are wrapped per-dataset with `dataset_id`, `dataset_name`, `search_result` fields; when `=false` (default), results are a plain list (unwrapped for single-dataset searches). `[EXT:https://docs.cognee.ai/guides/search-basics]`
- **`CHUNKS` result shape:** list of dicts with `id`, `text`, `chunk_index`, `chunk_size`, `cut_type`. **`SUMMARIES` result shape:** list of dicts with `id`, `text`.
- Setting `verbose=True` on LLM-completion modes returns `{text_result, context_result, objects_result}` per dataset.

Provenance: `[AST:cognee/api/v1/search/search.py:L27]`

#### `cognee.memify(...)` — enrich an existing graph

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

Pulls a subgraph (or the full graph when `data=None`) through a small two-stage pipeline of extraction + enrichment tasks. Defaults create `Rule` nodes with `rule_associated_from` edges grouped under the `coding_agent_rules` node_set — queryable via `SearchType.CODING_RULES`. Filter which subgraph to enrich with `node_type` + `node_name`. `[AST:cognee/modules/memify/memify.py:L25]` · `[EXT:https://docs.cognee.ai/guides/memify-quickstart]`

#### `cognee.update(...)` — replace data inside a dataset

```python
async def update(
    data_id: UUID,
    data: Union[BinaryIO, list[BinaryIO], str, list[str]],
    dataset_id: UUID,
    user: User = None,
    node_set: Optional[List[str]] = None,
    vector_db_config: dict = None,
    graph_db_config: dict = None,
    preferred_loaders: dict[str, dict[str, Any]] = None,
    incremental_loading: bool = True,
) -> Union[Dict[str, PipelineRunInfo], List[PipelineRunInfo]]
```

Implemented as `datasets.delete_data → add → cognify` — this is the standard replace pattern. Requires both `data_id` and `dataset_id`. `[AST:cognee/api/v1/update/update.py:L12]`

### Dataset management — `cognee.datasets`

Namespace class with static async methods. Use this instead of the deprecated top-level `cognee.delete`.

| Method | Signature | Purpose |
|---|---|---|
| `list_datasets` | `(user=None)` | Return all datasets the user can read |
| `discover_datasets` | `(directory_path)` (sync) | Scan a directory and return candidate dataset names |
| `list_data` | `(dataset_id, user=None)` | Return all data items in a dataset |
| `has_data` | `(dataset_id, user=None) -> bool` | Check whether a dataset has any data |
| `get_status` | `([dataset_ids]) -> dict` | Cognify pipeline status for each dataset |
| `empty_dataset` | `(dataset_id, user=None)` | Delete all data + graph/edge nodes, preserve dataset |
| `delete_data` | `(dataset_id, data_id, user=None, mode="soft", delete_dataset_if_empty=False)` | Remove one item — **never use `mode="hard"`**, it is dangerous |
| `delete_all` | `(user=None)` | Empty every dataset the user owns |

Provenance: `[AST:cognee/api/v1/datasets/datasets.py:L25]`

### Configuration — `cognee.config`

Namespace class with 32 static setters that mutate global Cognee runtime state. Call before `add`/`cognify`:

```python
cognee.config.set_llm_provider("openai")        # or "anthropic", "gemini", "ollama", "mistral", "bedrock"
cognee.config.set_llm_model("gpt-4o-mini")
cognee.config.set_llm_api_key("sk-...")
cognee.config.set_embedding_provider("fastembed")
cognee.config.set_embedding_model("BAAI/bge-small-en-v1.5")
cognee.config.set_embedding_dimensions(384)
cognee.config.set_vector_db_provider("lancedb")  # or "chromadb", "pgvector", etc.
cognee.config.set_graph_database_provider("kuzu")  # or "neo4j"
cognee.config.system_root_directory("/path/to/system")
```

**Bulk setters:** `set_llm_config(dict)`, `set_embedding_config(dict)`, `set_vector_db_config(dict)`, `set_graph_db_config(dict)`, `set_relational_db_config(dict)`, `set_migration_db_config(dict)`, `set_translation_config(dict)`. They route through `_update_config` which raises `InvalidConfigAttributeError` on unknown keys.

**Generic setter:** `cognee.config.set(key, value)` — maps to the right setter via an internal dispatch table. Useful for CLI-style config: unknown keys fall back to `set_embedding_config({key: value})` when the embedding config exposes that attribute; otherwise it raises `InvalidConfigAttributeError`.

**Important:** `set_embedding_dimensions` coerces `str` → `int` and raises `ValueError` if the value is not a positive integer.

See `references/config.md` for the full method list. Provenance: `[AST:cognee/api/v1/config/config.py:L18]`

### Pipelines primitives — `cognee.pipelines` and `cognee.modules.pipelines`

`cognee.pipelines` is a convenience module that re-exports everything from `cognee.modules.pipelines`:

- `Task(executable, *args, task_config=None, **kwargs)` — class wrapping any callable (sync fn, coroutine fn, generator, async generator). Auto-detects type via `inspect` and runs with the right execution path. `task_config={"batch_size": N}` controls batching. `[AST:cognee/modules/pipelines/tasks/task.py:L24]`
- `run_tasks(tasks, dataset_id, data=None, user=None, pipeline_name="unknown_pipeline", context=None, incremental_loading=False, data_per_batch=20)` — async generator. Respects `COGNEE_DISTRIBUTED=true` env var (swaps to `run_tasks_distributed`). Yields `PipelineRunStarted` → `PipelineRunCompleted`/`PipelineRunErrored`. `[AST:cognee/modules/pipelines/operations/run_tasks.py:L54]`
- `run_tasks_parallel(tasks) -> Task` — wraps a list of tasks in a new `Task` that runs them concurrently via `asyncio.gather`. Returns the last result if multiple. `[AST:cognee/modules/pipelines/operations/run_parallel.py:L6]`
- `run_pipeline(tasks, data=None, datasets=None, user=None, pipeline_name="custom_pipeline", use_pipeline_cache=False, vector_db_config=None, graph_db_config=None, incremental_loading=False, context=None, data_per_batch=20)` — top-level async generator. Internally calls `validate_pipeline_tasks`, `setup_and_check_environment`, then iterates `run_pipeline_per_dataset` for each authorized dataset. `[AST:cognee/modules/pipelines/operations/pipeline.py:L33]`

**Reserved pipeline names:** `cognify_pipeline` and `add_pipeline`. Default for custom pipelines is `"custom_pipeline"` — give each custom pipeline a distinct name so their completion states stay separate. `[EXT:https://docs.cognee.ai/guides/custom-tasks-pipelines]`

**Custom-pipeline entry point:** `cognee.run_custom_pipeline(tasks, data, dataset="main_dataset", ...)` — higher-level wrapper that hides the dataset-resolution and pipeline-executor selection from you. `[AST:cognee/modules/run_custom_pipeline/run_custom_pipeline.py:L14]`

### Data primitives — `cognee.low_level`

```python
from cognee.low_level import DataPoint, setup
```

- `DataPoint` — alias for `cognee.infrastructure.engine.ExtendableDataPoint`. Pydantic base class that becomes a graph node when added via `cognee.tasks.storage.add_data_points(...)`. Assigning another `DataPoint` to a field creates an edge labeled after the field name; use `Edge(weight=..., relationship_type=...)` from `cognee.infrastructure.engine.models.Edge` for custom edge metadata. Set `metadata = {"index_fields": [...]}` to control which fields are embedded into the vector store.
- `setup()` — initializes databases + tables. `add`, `cognify`, and `memify` each call it internally, but custom pipelines may need to call it explicitly before inserting DataPoints.

Provenance: `[AST:cognee/low_level.py:L1]` · `[EXT:https://docs.cognee.ai/guides/custom-data-models]`

### Observability / Tracing — `cognee.enable_tracing` and friends

OpenTelemetry-based in-memory tracing. All sync functions.

```python
cognee.enable_tracing(console_output=False)   # sets up TracerProvider with CogneeSpanExporter
cognee.disable_tracing()                       # shuts down the TracerProvider
trace = cognee.get_last_trace()                # Optional[CogneeTrace] — most recent complete trace
traces = cognee.get_all_traces()               # list[CogneeTrace] — every trace in memory
cognee.clear_traces()                          # empties the in-memory buffer
```

- Module-level `_tracing_enabled` flag, also honored via `cognee_tracing_enabled` base-config field or `COGNEE_TRACING_ENABLED=true|1|yes` env var.
- If OpenTelemetry is not installed, enable silently sets the flag but spans become no-ops via `_NullSpan` — the tracing API never raises ImportError.
- Provenance: `[AST:cognee/modules/observability/trace_context.py:L16]`

### Visualization — `cognee.visualize_graph`

```python
async def visualize_graph(destination_file_path: str = None) -> str
```

Fetches the full graph via `graph_engine.get_graph_data()` and renders it through `cognee_network_visualization(graph_data, destination_file_path)`. Returns the HTML string; also writes to `destination_file_path` when provided (otherwise saves to the user's home directory). `[AST:cognee/api/v1/visualize/visualize.py:L17]`

Additional helper: `cognee.cognee_network_visualization(graph_data, destination_file_path=None)` — same renderer, useful when you already have graph data. `[AST:cognee/modules/visualization/cognee_network_visualization.py:L22]`

### Pruning — `cognee.prune`

```python
await cognee.prune.prune_data()                                # wipes user data
await cognee.prune.prune_system(graph=True, vector=True,       # wipes backing stores
                                metadata=False, cache=True)
```

Use before running isolated tests or between example runs. `[AST:cognee/api/v1/prune/prune.py:L4]`

### Sessions — `cognee.session`

`cognee.session` is the submodule `cognee.api.v1.session.session`, exposing three async functions (not re-exported as top-level cognee names — access via `cognee.session.<fn>`):

- `get_session(session_id="default_session", last_n=None, user=None) -> List[SessionQAEntry]` — load recent Q&A turns for a session id.
- `add_feedback(session_id, qa_id, feedback_text=None, feedback_score=None, user=None) -> bool` — attach feedback to a cached Q&A entry.
- `delete_feedback(session_id, qa_id, user=None) -> bool` — clear feedback on a Q&A entry.

All three resolve the user via an internal `_resolve_user` that prefers an explicit `user`, falls back to the session context-var, then to `get_default_user()`. Any of those failing raises `CogneeValidationError(name="SessionPreconditionError")` with an actionable message. `[AST:cognee/api/v1/session/session.py:L16]`

### Migrations — `cognee.run_migrations`

```python
async def run_migrations()
```

Locates the installed `cognee` package root, finds `alembic.ini` and the `alembic/` migrations folder inside it, then runs `python -m alembic upgrade head` via subprocess. Raises `FileNotFoundError` if either is missing; logs the captured stdout/stderr and `sys.exit(1)` on migration failure. Pair this with a fresh database or after upgrading cognee. `[AST:cognee/run_migrations.py:L16]`

## Full Type Definitions

### `cognee.exceptions` — error hierarchy

```python
class CogneeApiError(Exception):
    def __init__(self, message="Service is unavailable.", name="Cognee",
                 status_code=418, log=True, log_level="ERROR"): ...

class CogneeSystemError(CogneeApiError):          # status_code=500, name="CogneeSystemError"
class CogneeValidationError(CogneeApiError):      # status_code=422, name="CogneeValidationError"
class CogneeConfigurationError(CogneeApiError):   # status_code=500, name="CogneeConfigurationError"
class CogneeTransientError(CogneeApiError):       # status_code=503, name="CogneeTransientError"
```

Every subclass auto-logs on construction (level controlled by `log_level`). `__str__` formats as `"{name}: {message} (Status code: {status_code})"`. Imports `status` from `fastapi` so it pulls in the fastapi dependency transitively. `[AST:cognee/exceptions/exceptions.py:L7]`

### `cognee.pipelines.Task` — detailed

Class attributes:

- `executable` — the wrapped callable (function / coroutine / generator / async-generator).
- `task_config: dict[str, Any] = {"batch_size": 1}` — default batch size 1 unless overridden at construction.
- `default_params: dict[str, Any]` — captured `*args` and `**kwargs` from construction.
- `task_type: str` — one of `"Function"`, `"Coroutine"`, `"Generator"`, `"Async Generator"`.

Methods:

- `run(*args, **kwargs)` — calls the executable with combined args/kwargs from construction and invocation.
- `execute(args, kwargs, next_batch_size=None)` — async generator that yields results; supports batching via `_next_batch_size`.

Construction rejects unsupported callables with `ValueError(f"Unsupported task type: {executable}")`.

`@task_summary("Classified {n} document(s)")` decorator sets `func.__task_summary__` for human-readable task run summaries. `[AST:cognee/modules/pipelines/tasks/task.py:L1]`

### `PipelineRunInfo` — pipeline status

Imported from `cognee.modules.pipelines.models.PipelineRunInfo`. Subclasses yielded by `run_tasks` / `run_pipeline`:

- `PipelineRunStarted(pipeline_run_id, dataset_id, dataset_name, payload)`
- `PipelineRunCompleted(pipeline_run_id, dataset_id, dataset_name, data_ingestion_info)`
- `PipelineRunErrored(pipeline_run_id, payload, dataset_id, dataset_name, data_ingestion_info)`

`run_tasks` raises `PipelineRunFailedError` internally if any data item yields a `PipelineRunErrored` — but still yields the errored status first. `[AST:cognee/modules/pipelines/operations/run_tasks.py:L17]`

## Full Integration Patterns

### Co-import patterns (detected in source)

- **`Task` + `run_pipeline` + `run_tasks_parallel`** — the standard custom-pipeline trio. Always imported together from `cognee.modules.pipelines` or the `cognee.pipelines` convenience re-export. Seen in `cognee/api/v1/add/add.py:L5`, `cognee/api/v1/cognify/cognify.py:L12`, `cognee/modules/memify/memify.py:L9`, and `cognee/modules/run_custom_pipeline/run_custom_pipeline.py:L6`.
- **`SearchType` + `search`** — co-imported whenever search is called with a non-default mode: `from cognee import SearchType` + `from cognee.api.v1.search import search`. Used across `cognify.py`, the memify quickstart, and `cognee/api/v1/update/update.py`.
- **`DataPoint` + `add_data_points`** — paired for direct graph insertion without cognify: `from cognee.infrastructure.engine import DataPoint` + `from cognee.tasks.storage import add_data_points`. See `[EXT:https://docs.cognee.ai/guides/custom-data-models]`. The `cognee.low_level` shortcut gives you `DataPoint` + `setup` in a single import.
- **`LLMGateway.acreate_structured_output` + custom Task** — pattern for LLM-backed extraction tasks: `from cognee.infrastructure.llm.LLMGateway import LLMGateway; await LLMGateway.acreate_structured_output(text, system_prompt, PydanticModel)`. Backend is controlled by the `STRUCTURED_OUTPUT_FRAMEWORK` env var (BAML or LiteLLM+Instructor). `[EXT:https://docs.cognee.ai/guides/custom-tasks-pipelines]`

### Default backends (from `pyproject.toml`)

- **LLM:** `litellm>=1.76.0` + `openai>=1.80.1` + `instructor>=1.9.1`. Provider routed via `cognee.config.set_llm_provider(...)`.
- **Vector store:** `lancedb>=0.24.0` + `pylance`. Alternatives via `fastembed`, `postgres` (pgvector), `neptune` extras.
- **Graph store:** `kuzu==0.11.3` (pinned) + `networkx>=3.4.2`. Alternatives via the `neo4j` or `neptune` extras.
- **Relational:** `sqlalchemy>=2.0.39` + `aiosqlite>=0.20.0` + `alembic>=1.13.3`. PostgreSQL via the `postgres` extra.
- **API server:** `fastapi>=0.116.2` + `uvicorn>=0.34.0` + `gunicorn` + `websockets`. Starts with `uv run python -m cognee.api.client`.
- **Auth:** `fastapi-users[sqlalchemy]>=15.0.2`.
- **Observability:** `structlog>=25.2.0`, plus OpenTelemetry-compatible tracing through `cognee.enable_tracing`.
- **Scraping (extra):** `tavily-python`, `beautifulsoup4`, `playwright`, `lxml`, `protego`, `APScheduler`.
- **Distributed (extra):** `modal>=1.0.5`.

Provenance: `[SRC:pyproject.toml:L22]` · `[SRC:AGENTS.md:L7]`

### Related out-of-scope interfaces

- `cognee-mcp/` — Model Context Protocol server exposing cognee tools over stdio/SSE/HTTP.
- `cognee-frontend/` — Next.js UI that the `cognee.start_ui` function can launch.
- `cognee-cli` — terminal CLI (`add/cognify/search/-ui`).
- `cognee.api.client:app` — FastAPI application for HTTP REST access.

This skill only covers the Python API — use the upstream docs for those other surfaces.
