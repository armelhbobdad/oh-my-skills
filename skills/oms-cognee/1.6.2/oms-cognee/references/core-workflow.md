# Core Workflow: add → cognify → search

Full reference for cognee's three primary async functions plus environment variable requirements.

## Contents

- [Prerequisites](#prerequisites)
- [cognee.add](#cogneeadd)
- [cognee.cognify](#cogneecognify)
- [cognee.search](#cogneesearch)
- [cognee.update](#cogneeupdate)
- [Environment variables](#environment-variables)

## Prerequisites

1. **LLM API key (optional)**: `LLM_API_KEY` is no longer required. `add()` validates only the embedding side of the provider config, with or without a key. With a usable key, cognify extracts the graph with the LLM. Without one (and with no embedding settings configured), cognify (`GRAPH_EXTRACTOR=auto`) extracts with the local GLiNER demo model and embeds with the local fastembed model. `[SRC:cognee/api/v1/cognify/cognify.py:L307-L310]` `[SRC:cognee/api/v1/add/add.py:L238-L248]` `[SRC:cognee/modules/cognify/config.py:L23-L28]` The GLiNER runtime (CPU torch plus the `gliner` extra) installs itself on first use unless `GLINER_AUTO_INSTALL=false`, which raises `KeylessExtractorNotInstalledError` instead. `[SRC:cognee/modules/cognify/config.py:L29-L34]` LLM-backed search types still need a key. `[SRC:cognee/api/v1/search/search.py:L227-L229]`
2. **Settings file**: importing cognee loads a single `.env`: the file named by `COGNEE_ENV_FILE` if set (an exact file; a path that is not a file is an error), else `.env` in the working directory or its parents up to the project root (`.git` or `pyproject.toml`), else the cognee package tree. Its values override variables already set in the shell, and the chosen path is logged. `[SRC:cognee/__init__.py:L27-L35]` `[SRC:cognee/shared/env_file.py:L13-L29]` `[SRC:cognee/shared/env_file.py:L112-L124]`
3. **Database setup**: relational and vector databases must be reachable.
4. **User**: Cognee uses a default user (`default_user@example.com`) created automatically on first use when `user` is None. `[SRC:cognee/modules/users/methods/create_default_user.py:L5]`

Full env matrix: `[SRC:cognee/api/v1/add/add.py:L203-L215]`

## cognee.add

### Signature

```python
async def add(
    data: BinaryIO | list[BinaryIO] | str | list[str] | DataItem | list[DataItem] | Any,
    dataset_name: str = DEFAULT_DATASET_NAME,
    user: User = None,
    node_set: list[str] | None = None,
    vector_db_config: dict | None = None,
    graph_db_config: dict | None = None,
    dataset_id: UUID | None = None,
    preferred_loaders: list[str | dict[str, dict[str, Any]]] | None = None,
    incremental_loading: bool = True,
    data_per_batch: int | None = 20,
    importance_weight: float | None = 0.5,
    run_in_background: bool = False,
    llm_config: LLMConfig | None = None,
    embedding_config: EmbeddingConfig | None = None,
    data_cache: bool = True,
    skip_connection_test: bool = False,
    **kwargs,
)
```

Provenance: `[AST:cognee/api/v1/add/add.py:L39]`

### Parameters

| Param | Type | Default | Required | Description |
|---|---|---|---|---|
| `data` | BinaryIO \| list[BinaryIO] \| str \| list[str] \| DataItem \| list[DataItem] \| Any | — | yes | Content to ingest. See "Accepted data types" below. |
| `dataset_name` | str | `DEFAULT_DATASET_NAME` (`"main_dataset"`) | no | Logical dataset for organization. `[SRC:cognee/modules/data/constants.py:L8]` |
| `user` | User | None | no | Auth context. Uses default user if None. |
| `node_set` | list[str] \| None | None | no | Tags that become first-class graph nodes after cognify — scope memory by customer/workflow/topic. |
| `vector_db_config` | dict \| None | None | no | Per-call vector DB override. |
| `graph_db_config` | dict \| None | None | no | Per-call graph DB override. |
| `dataset_id` | UUID \| None | None | no | Specific dataset UUID (overrides `dataset_name`). |
| `preferred_loaders` | list[str \| dict] \| None | None | no | Loaders to prefer per file type: loader names or `{loader: config}` dicts, merged into one mapping. `[SRC:cognee/api/v1/add/add.py:L229-L236]` |
| `incremental_loading` | bool | True | no | Skip items the pipeline already processed (`[SRC:cognee/modules/pipelines/operations/run_tasks_data_item.py:L142]`). `add()` never updates a document: a file already in the dataset (same path, or same upload filename) with different content raises `DocumentUpdateRequiredError` for the whole request before anything is written — change it with `cognee.update()`. Re-adding identical content does nothing. `[SRC:cognee/api/v1/add/add.py:L70-L74]` `[SRC:cognee/api/v1/add/add.py:L308-L311]` |
| `data_per_batch` | int \| None | 20 | no | Data items per parallel batch. |
| `importance_weight` | float \| None | 0.5 | no | Weighting applied when storing ingested items. |
| `run_in_background` | bool | False | no | Start ingestion and return immediately. Stream inputs are first buffered in memory, and DLT orphan cleanup is skipped (upstream deletions need a successful foreground run). `[SRC:cognee/api/v1/add/add.py:L126-L129]` `[SRC:cognee/api/v1/add/add.py:L313-L324]` |
| `llm_config` | LLMConfig \| None | None | no | Per-call LLM provider override, applied inside the pipeline's dataset context. `[SRC:cognee/modules/pipelines/operations/run_tasks.py:L93-L98]` |
| `embedding_config` | EmbeddingConfig \| None | None | no | Per-call embedding provider override, applied the same way. `[SRC:cognee/modules/pipelines/operations/run_tasks.py:L93-L98]` |
| `data_cache` | bool | True | no | Route items through the incremental (cached) per-item path; either this or `incremental_loading` enables it, so both must be False to force full reprocessing. `[SRC:cognee/modules/pipelines/operations/run_tasks_data_item.py:L365]` `[SRC:cognee/modules/pipelines/operations/run_tasks_data_item.py:L377]` |
| `skip_connection_test` | bool | False | no | Skip the first-use LLM/embedding connection probes for this pipeline only (nothing is marked as checked). `COGNEE_SKIP_CONNECTION_TEST` is the process-wide switch. `[SRC:cognee/modules/pipelines/layers/setup_and_check_environment.py:L57-L78]` |
| `**kwargs` | — | — | — | Passed through to `resolve_dlt_sources` for DLT-specific config (e.g., `extraction_rules`, `tavily_config`, `soup_crawler_config` — documented in docstring only). `[SRC:cognee/api/v1/add/add.py:L300-L306]` |

### Accepted data types

- **Text strings** — raw content (any string not starting with `/` or `file://`).
- **Absolute file paths** — e.g., `"/path/to/document.pdf"`.
- **File URLs** — `"file:///absolute/path"` or `"file://relative/path"`.
- **S3 paths** — `"s3://bucket-name/path/to/file.pdf"`.
- **HTTP(S) URLs** — fetched and ingested as a page. Every fetch passes an SSRF guard: `ALLOW_HTTP_REQUESTS` (default true) must allow outbound requests, only `http`/`https` are accepted, and a host that resolves to a loopback, private, link-local (e.g. cloud metadata), reserved, multicast or unspecified address is refused with `SSRFProtectionError`. The scraping backend is BeautifulSoup (extraction rules), Tavily (`TAVILY_API_KEY`) or Keenable (`KEENABLE_API_KEY`); Tavily wins when both keys are set. `[SRC:cognee/api/v1/add/add.py:L83]` `[SRC:cognee/tasks/web_scraper/ssrf_protection.py:L13-L21]` `[SRC:cognee/tasks/web_scraper/ssrf_protection.py:L41]` `[SRC:cognee/tasks/web_scraper/utils.py:L55-L61]`
- **Code repository URLs** — `https://github.com/<owner>/<repo>`, a gitlab.com project, or any URL ending in `.git` is shallow-cloned and ingested as one code-repo item (plus the repo's documents) that cognify runs through the code graph pipeline. Needs `ALLOW_HTTP_REQUESTS` and `git` on PATH. `[SRC:cognee/api/v1/add/add.py:L84-L88]`
- **Binary file objects** — `open("file.txt", "rb")`.
- **DLT DataItems** — from `cognee.tasks.ingestion.data_item.DataItem`, including dlt resources that are automatically expanded by `resolve_dlt_sources`.
- **Lists** — any mix of the above.

### Supported file formats (auto-detected)

| Type | Extensions | Processing |
|---|---|---|
| Text | `.txt`, `.md`, `.csv` | direct read |
| PDFs | `.pdf` | pypdf |
| Images | `.png`, `.jpg`, `.jpeg` | OCR/vision models |
| Audio | `.mp3`, `.wav` | transcription |
| Source code | `.py`, `.js`, `.ts`, etc. | syntax-aware parsing |
| Office docs | `.docx`, `.pptx` | format-specific loaders |

`[SRC:cognee/api/v1/add/add.py:L91-L97]`

### Return value

A single `PipelineRunInfo` (`status`, `pipeline_run_id`, `dataset_id`, `dataset_name`, `payload`, `data_ingestion_info`; the `PipelineRunErrored` subclass adds `error_class` and `error_message`). The executor's one-entry `{dataset_id: PipelineRunInfo}` dict is unwrapped because `add` always processes one dataset; in background mode this is the initial run info. While connected to a remote instance via `serve()`, `add` returns the server's response wrapped in a `SimpleNamespace`. `[AST:cognee/modules/pipelines/models/PipelineRunInfo.py:L9]` `[SRC:cognee/modules/pipelines/models/PipelineRunInfo.py:L42-L50]` `[SRC:cognee/api/v1/add/add.py:L345-L348]` `[SRC:cognee/api/v1/add/add.py:L218-L227]`

### Internal flow

1. Route to the remote instance when connected via `serve()` (`get_remote_client`).
2. Validate the provider config for the embedding side only (`validate_provider_config(needs_llm=False)`).
3. Setup databases (`setup()`).
4. Bring an existing database to the current migration head (`run_migrations_and_block`).
5. Resolve authorized dataset for the user (`resolve_authorized_user_dataset`).
6. Expand DLT resources into standard DataItems (`resolve_dlt_sources`, which also returns a deferred `orphan_cleanup`).
7. Refuse the whole request if any input changes a document the dataset already holds (`refuse_changed_existing_documents` → `DocumentUpdateRequiredError`).
8. When `run_in_background=True`, buffer stream inputs in memory and drop the DLT orphan cleanup.
9. Run the `add_pipeline` with tasks: `resolve_data_directories` → `ingest_data`.
10. After a successful foreground run only, run the DLT orphan cleanup.

Provenance: `[SRC:cognee/api/v1/add/add.py:L218-L355]` `[AST:cognee/api/v1/exceptions/exceptions.py:L70]`

## cognee.cognify

### Signature

```python
async def cognify(
    datasets: str | list[str] | list[UUID] | None = None,
    user: User = None,
    graph_model: BaseModel = KnowledgeGraph,
    chunker = TextChunker,
    chunk_size: int | None = None,
    chunks_per_batch: int | None = None,
    config: Config = None,
    vector_db_config: dict | None = None,
    graph_db_config: dict | None = None,
    run_in_background: bool = False,
    incremental_loading: bool = True,
    custom_prompt: str | None = None,
    temporal_cognify: bool = False,
    functional_relationships: Collection[str] | None = None,
    data_per_batch: int = 20,
    llm_config: LLMConfig | None = None,
    embedding_config: EmbeddingConfig | None = None,
    data_cache: bool = True,
    dry_run: bool = False,
    raise_on_error: bool = True,
    chunk_attachment: Literal["direct", "all"] | None = None,
    extractor: Literal["llm", "gliner_demo", "gliner"] | None = None,
    ontology_file_path: str | None = None,
    **kwargs,
)
```

Provenance: `[AST:cognee/api/v1/cognify/cognify.py:L110]`

### Key parameters

| Param | Type | Default | Description |
|---|---|---|---|
| `datasets` | str \| list[str] \| list[UUID] \| None | None | Datasets to process. `None` → all datasets the user can access. |
| `user` | User | None | Auth context. Uses default user if None. |
| `graph_model` | BaseModel | `KnowledgeGraph` | Custom graph schema (domain-specific models, e.g., `ScientificPaper`). |
| `chunker` | Class | `TextChunker` | Chunking strategy. `TextChunker` is paragraph-based (default). `LangchainChunker` is recursive character splitter. |
| `chunk_size` | int \| None | None | Max tokens per chunk. Auto-calculated if None (roughly `min(embedding max tokens, llm_max_completion_tokens // 2)`). An explicit value above the embedding model's input limit (or `EMBEDDING_MAX_COMPLETION_TOKENS` when lower) is lowered to that limit with a warning; a negative value raises `ValueError`. `[SRC:cognee/infrastructure/llm/utils.py:L55-L58]` `[SRC:cognee/infrastructure/llm/utils.py:L68-L91]` |
| `chunks_per_batch` | int \| None | None (→ configured `chunks_per_batch`, else 2000 on the standard route; 100 on the DLT route, 10 on the temporal route) | Chunks per processing batch. `[SRC:cognee/api/v1/cognify/cognify.py:L582-L585]` `[SRC:cognee/api/v1/cognify/cognify.py:L663-L666]` `[SRC:cognee/api/v1/cognify/cognify.py:L720-L722]` `[SRC:cognee/tasks/graph/gliner_demo/tasks.py:L320-L322]` |
| `config` | Config | None | Ontology config: `{"ontology_config": {"ontology_resolver": ..., "ontology_mode": ...}}`. See "Ontology config" below. `[SRC:cognee/modules/ontology/get_default_ontology_resolver.py:L29-L33]` `[SRC:cognee/modules/ontology/get_default_ontology_resolver.py:L56-L59]` |
| `vector_db_config` | dict \| None | None | Per-call vector DB override. |
| `graph_db_config` | dict \| None | None | Per-call graph DB override. |
| `run_in_background` | bool | False | Async execution mode. Recommended for datasets > 100MB. |
| `incremental_loading` | bool | True | Skip data items the pipeline already processed. `[SRC:cognee/modules/pipelines/operations/run_tasks_data_item.py:L142]` |
| `custom_prompt` | str \| None | None | Overrides default extraction prompts. Ignored (with a warning) by the `gliner_demo` extractor. `[SRC:cognee/api/v1/cognify/cognify.py:L440-L441]` |
| `temporal_cognify` | bool | False | Time-aware extraction — builds event chains with timestamps, pairs with `SearchType.TEMPORAL`. |
| `functional_relationships` | Collection[str] \| None | None | Relationship names that hold one target per source (e.g. `{"ceo_of"}`); conflicting assertions are resolved by recency (older ones tagged superseded, nothing deleted) by an extra `resolve_temporal_contradictions` task. `[SRC:cognee/api/v1/cognify/cognify.py:L204-L209]` `[SRC:cognee/api/v1/cognify/cognify.py:L632-L640]` |
| `data_per_batch` | int | 20 | Items per batch passed to the pipeline. |
| `llm_config` | LLMConfig \| None | None | Per-call LLM provider override, applied inside the pipeline's dataset context. `[SRC:cognee/modules/pipelines/operations/run_tasks.py:L93-L98]` |
| `embedding_config` | EmbeddingConfig \| None | None | Per-call embedding provider override. `[SRC:cognee/modules/pipelines/operations/run_tasks.py:L93-L98]` |
| `data_cache` | bool | True | Incremental (cached) per-item processing; either this or `incremental_loading` enables it. `[SRC:cognee/modules/pipelines/operations/run_tasks_data_item.py:L377]` |
| `dry_run` | bool | False | Return a `DryRunEstimate` (stage-level LLM token and rough cost estimate over all data in the selected datasets) without LLM calls or graph writes. Not supported with `temporal_cognify`, the `gliner_demo` extractor, or a remote instance. `[SRC:cognee/api/v1/cognify/cognify.py:L210-L212]` `[SRC:cognee/api/v1/cognify/cognify.py:L328-L332]` `[SRC:cognee/api/v1/cognify/cognify.py:L362-L366]` `[SRC:cognee/api/v1/cognify/cognify.py:L413-L425]` |
| `raise_on_error` | bool | True | Raise `CognifyFailedError` when a foreground run errors (see "Return value"). |
| `chunk_attachment` | Literal["direct", "all"] \| None | None (same as `"direct"`) | How widely each chunk links into the graph extracted from it; `"all"` links the chunk to every stored node reachable from the extracted root. Requires a custom `DataPoint` `graph_model`; raises `ValueError` with `KnowledgeGraph`, with `temporal_cognify=True`, or on a remote instance. `[SRC:cognee/api/v1/cognify/cognify.py:L213-L228]` `[SRC:cognee/api/v1/cognify/cognify.py:L334-L350]` |
| `extractor` | Literal["llm", "gliner_demo", "gliner"] \| None | None (→ `GRAPH_EXTRACTOR`, default `"auto"`) | Which implementation fills the extract-and-summarize step. `"auto"` picks `"llm"` with a usable LLM key and `"gliner_demo"` without; `"gliner"` is an alias of `"gliner_demo"`. `gliner_demo` builds the generic `KnowledgeGraph` with the local GLiNER demo model (no LLM call for extraction or summaries) and raises `ValueError` with a custom `graph_model`, `temporal_cognify=True`, `dry_run=True` or extra `**kwargs`; any explicit `extractor` raises on a remote instance. `[SRC:cognee/api/v1/cognify/cognify.py:L229-L239]` `[SRC:cognee/api/v1/cognify/cognify.py:L367-L373]` `[SRC:cognee/modules/cognify/config.py:L62-L64]` `[SRC:cognee/api/v1/cognify/cognify.py:L323-L332]` `[SRC:cognee/api/v1/cognify/cognify.py:L434-L446]` |
| `ontology_file_path` | str \| None | None | Path, or comma-separated paths, to the ontology used for extraction schema planning and graph integration. Wins over `config` and the environment. `[SRC:cognee/api/v1/cognify/cognify.py:L186-L187]` `[SRC:cognee/modules/ontology/get_default_ontology_resolver.py:L23-L28]` |
| `**kwargs` | — | — | Forwarded to the `extract_graph_and_summarize` task on the LLM route. `[SRC:cognee/api/v1/cognify/cognify.py:L461-L473]` `[SRC:cognee/api/v1/cognify/cognify.py:L603-L611]` |

### Default tasks

Built by the async `get_default_tasks(user=..., graph_model=..., chunker=..., chunk_size=..., config=..., custom_prompt=..., chunks_per_batch=..., functional_relationships=..., chunk_attachment=..., **kwargs) -> list[Task]` (await it). `cognee/api/v1/cognify/__init__.py` re-exports only `cognify`, so import it with `from cognee.api.v1.cognify.cognify import get_default_tasks` to compose a custom cognify pipeline. `[AST:cognee/api/v1/cognify/cognify.py:L565]` `[SRC:cognee/api/v1/cognify/__init__.py:L1]` `[SRC:examples/demos/custom_pipelines/custom_cognify_pipeline_example.py:L66-L68]`

Each step is a `Task`: its keyword arguments other than the `Task` options (`task_config`, `batch_size`, `enriches`, `needs_llm`) are bound to the task function, and the runner passes the previous step's output (the input data, for the first step) as the function's first argument (`data_documents`, `documents`, `data_chunks`, `data_points`).

1. `Task(classify_documents, needs_llm=False)`
2. `Task(extract_chunks_from_documents, max_chunk_size=max_chunk_size, chunker=chunker, needs_llm=False)`
3. `Task(extract_graph_and_summarize, graph_model=graph_model, config=config, custom_prompt=custom_prompt, chunk_attachment=chunk_attachment, task_config={"batch_size": chunks_per_batch}, **kwargs)` — graph extraction and per-chunk summaries in one LLM step
4. `Task(add_data_points, embed_triplets=embed_triplets, task_config={"batch_size": chunks_per_batch}, needs_llm=False)`
5. Optional `record_provenance` when `provenance_tracking` is on (env `PROVENANCE_TRACKING`)
6. Optional `detect_contradictions` when `contradiction_detection` is on
7. Optional `resolve_temporal_contradictions` when `functional_relationships` is given

Provenance: `[SRC:cognee/api/v1/cognify/cognify.py:L588-L640]` `[SRC:cognee/modules/cognify/config.py:L17-L22]` `[SRC:cognee/modules/pipelines/tasks/task.py:L209-L222]` `[SRC:cognee/modules/pipelines/tasks/task.py:L276-L281]` `[SRC:cognee/modules/pipelines/operations/run_tasks_base.py:L273]` `[SRC:cognee/tasks/documents/classify_documents.py:L138]` `[SRC:cognee/tasks/documents/extract_chunks_from_documents.py:L32-L36]` `[SRC:cognee/tasks/graph/extract_graph_and_summarize.py:L13-L22]` `[SRC:cognee/tasks/storage/add_data_points.py:L70-L76]`

With `extractor="gliner_demo"`, `get_gliner_demo_tasks` builds the standard-route list instead: a GLiNER schema step is added and the GLiNER demo extraction task takes the place of step 3. `[SRC:cognee/api/v1/cognify/cognify.py:L448-L460]` `[SRC:cognee/tasks/graph/gliner_demo/tasks.py:L355-L371]`

**Per-item routing**: each data item runs the task list of its route — `STANDARD` (the list above, or the temporal list), `DLT_SOURCE` (`get_dlt_tasks`: `classify_documents` → `purge_stale_dlt_source_artifacts` → `extract_chunks_from_documents` → `add_data_points` → `extract_dlt_source_edges`, no LLM), `CODE` (`get_code_file_tasks()`) and `CODE_REPO` (`get_code_repo_tasks()`). `[SRC:cognee/api/v1/cognify/cognify.py:L490-L500]` `[AST:cognee/api/v1/cognify/cognify.py:L645]` `[SRC:cognee/api/v1/cognify/cognify.py:L668-L692]` `[SRC:cognee/modules/cognify/routing.py:L23-L29]`

### Temporal pipeline (when `temporal_cognify=True`)

Uses a different task list, each step a `Task` built as above:

1. `classify_documents`, with no bound arguments
2. `Task(extract_chunks_from_documents, max_chunk_size=..., chunker=chunker)`
3. `Task(extract_events_and_timestamps, task_config={"batch_size": chunks_per_batch})`
4. `extract_knowledge_graph_from_events`, with no bound arguments
5. `Task(add_data_points, task_config={"batch_size": chunks_per_batch})`

Provenance: `[AST:cognee/api/v1/cognify/cognify.py:L695]` `[SRC:cognee/api/v1/cognify/cognify.py:L724-L739]`

### Ontology config

The resolver is chosen in this order: an explicit `ontology_file_path` (rdflib resolver, fuzzy matching); else, when `config` is given, its `ontology_config["ontology_resolver"]` (None if absent); else the environment, when `ontology_file_path`, `ontology_resolver` and `matching_strategy` are all set (the last two default to `rdflib` / `fuzzy`). With nothing configured the resolver is None — there is no `get_default_ontology_resolver()` fallback. The ontology mode (`ONTOLOGY_MODE`: `annotate` by default, or `strict`) is applied, a per-call `ontology_mode` in `config` winning; strict mode fails before any pipeline work when the environment's ontology is empty.

Provenance: `[SRC:cognee/api/v1/cognify/cognify.py:L402-L411]` `[SRC:cognee/modules/ontology/get_default_ontology_resolver.py:L18-L61]` `[SRC:cognee/modules/ontology/ontology_env_config.py:L12-L13]` `[SRC:cognee/modules/ontology/ontology_env_config.py:L50-L53]`

### Return value

- **Blocking mode**: `dict` mapping `dataset_id → PipelineRunInfo`. With `raise_on_error=True` (default), an errored run raises `CognifyFailedError` (checked by `raise_if_cognify_errored(result)`), and a run-level exception is wrapped in `CognifyFailedError` too (typed cognee API errors such as `PermissionDeniedError` pass through unchanged). Pass `raise_on_error=False` to get back the dict containing `PipelineRunErrored` (and the raw exception on the run-level path). `[SRC:cognee/modules/pipelines/layers/pipeline_execution_mode.py:L26-L53]` `[SRC:cognee/api/v1/cognify/cognify.py:L527-L550]` `[AST:cognee/api/v1/cognify/cognify.py:L83]` `[AST:cognee/modules/pipelines/exceptions/exceptions.py:L21]`
- **Background mode**: `dict` mapping `dataset_id → initial PipelineRunInfo` (payload stripped) — track via `pipeline_run_id`. Errors are not raised; they land on the run record. `[SRC:cognee/api/v1/cognify/cognify.py:L543-L550]` `[SRC:cognee/modules/pipelines/layers/pipeline_execution_mode.py:L56-L77]` `[SRC:cognee/modules/pipelines/layers/pipeline_execution_mode.py:L113-L129]`
- **`dry_run=True`**: a `DryRunEstimate`. `[SRC:cognee/modules/cognify/estimator.py:L106]`

## cognee.search

### Signature

```python
async def search(
    query_text: str,
    query_type: SearchType = SearchType.HYBRID_COMPLETION,
    user: User | None = None,
    datasets: list[str] | str | None = None,
    dataset_ids: list[UUID] | UUID | None = None,
    system_prompt_path: str = "answer_simple_question.txt",
    system_prompt: str | None = None,
    top_k: int = 15,
    node_type: type | None = NodeSet,
    node_name: list[str] | None = None,
    node_name_filter_operator: str = "OR",
    only_context: bool = False,
    session_id: str | None = None,
    wide_search_top_k: int | None = None,
    triplet_distance_penalty: float | None = None,
    feedback_influence: float = get_base_config().default_feedback_influence,
    verbose: bool = False,
    retriever_specific_config: dict | None = None,
    neighborhood_depth: int | None = None,
    neighborhood_seed_top_k: int | None = None,
    skills: list[str | Skill] | None = None,
    tools: list[str] | None = None,
    max_iter: int | None = None,
    include_references: bool = False,
    llm_config: LLMConfig | None = None,
    embedding_config: EmbeddingConfig | None = None,
    code_query: dict[str, Any] | None = None,
) -> list[SearchResult]
```

Provenance: `[AST:cognee/api/v1/search/search.py:L41]`

### Key parameters

| Param | Type | Default | Description |
|---|---|---|---|
| `query_text` | str | — | The natural-language question or query. Required. |
| `query_type` | SearchType | `HYBRID_COMPLETION` | See Key Types in SKILL.md for full list. Hybrid (document passages plus entity neighbourhoods, then LLM completion) silently defers to `GRAPH_COMPLETION` for a custom `node_type`, `node_name` with `node_type=None`, `neighborhood_depth`, `feedback_influence > 0`, or a missing `DocumentChunk_text` collection. Results do not name the type that ran, so pin `query_type` when the result shape matters. `[SRC:cognee/api/v1/search/search.py:L89-L93]` `[SRC:cognee/modules/search/methods/hybrid_deferral.py:L28-L74]` `[SRC:cognee/api/v1/search/search.py:L53-L55]` |
| `user` | User \| None | None | Auth context. Uses the default user if None. `[SRC:cognee/api/v1/search/search.py:L319-L321]` |
| `datasets` | list[str] \| str \| None | None | Dataset names to search. |
| `dataset_ids` | list[UUID] \| UUID \| None | None | Same but with UUIDs. Takes precedence over `datasets`. |
| `system_prompt_path` | str | `"answer_simple_question.txt"` | Prompt template file for completion types. |
| `system_prompt` | str \| None | None | Inline system prompt; overrides `system_prompt_path`. `[SRC:cognee/modules/search/methods/search.py:L104-L105]` |
| `top_k` | int | 15 | Max results, applied per dataset. `HYBRID_COMPLETION` gives each lane `min(top_k, 10)`; raise a lane with the `chunks_top_k`, `entities_top_k` or `facts_top_k` keys in `retriever_specific_config` (not capped). `top_k <= 0` raises `QueryValidationError`. `[SRC:cognee/api/v1/search/search.py:L215-L218]` `[SRC:cognee/modules/search/methods/get_search_type_retriever_instance.py:L41-L51]` `[SRC:cognee/modules/search/methods/get_search_type_retriever_instance.py:L77-L79]` |
| `node_type` | type \| None | NodeSet | Graph model to filter on (use with `node_name`). |
| `node_name` | list[str] | None | Names of nodes/node_sets to include. |
| `node_name_filter_operator` | str | `"OR"` | `"OR"` or `"AND"` (case-insensitive) — otherwise raises `CogneeValidationError`. `[SRC:cognee/api/v1/search/search.py:L311-L317]` |
| `only_context` | bool | False | Skip LLM generation. For completion types the result is the user prompt the LLM would receive (conversation history, then the question plus context through the retriever's template, then session guidance); the system prompt comes back as `system_prompt_result` under `verbose=True`. Raw context is returned only when no prompt was built. `[SRC:cognee/modules/search/methods/search.py:L112-L119]` `[SRC:cognee/modules/search/models/SearchResultPayload.py:L96-L97]` |
| `session_id` | str \| None | None | Conversation session whose history is added to the completion context and that receives the QA entry. Passed to most completion retrievers, including `HYBRID_COMPLETION`, `GRAPH_COMPLETION_COT`, `TEMPORAL`, `SUMMARIES`, `CYPHER` and `AGENTIC_COMPLETION`. `[SRC:cognee/modules/search/methods/search.py:L120-L122]` `[SRC:cognee/modules/search/methods/get_search_type_retriever_instance.py:L97-L355]` `[SRC:cognee/modules/search/methods/get_search_type_retriever_instance.py:L397]` |
| `wide_search_top_k` | int \| None | None | Initial candidate pool before ranking for graph-completion retrievers; the graph retriever applies 100 when None. Any explicit value with `HYBRID_COMPLETION` raises `CogneeValidationError(name="InvalidHybridSearchConfig")` — set `query_type=GRAPH_COMPLETION` to use it. `[SRC:cognee/modules/retrieval/graph_completion_retriever.py:L82]` `[SRC:cognee/modules/search/methods/hybrid_deferral.py:L14-L25]` |
| `triplet_distance_penalty` | float \| None | None | Graph retrieval ranking penalty; the graph retriever applies 6.5 when None. Rejected on `HYBRID_COMPLETION` like `wide_search_top_k`. `[SRC:cognee/modules/retrieval/graph_completion_retriever.py:L86-L88]` |
| `feedback_influence` | float | `get_base_config().default_feedback_influence` | Weight of feedback signals in ranking. The default comes from env `DEFAULT_FEEDBACK_INFLUENCE` (default `"0.0"`), read once at import. Any value > 0 makes `HYBRID_COMPLETION` defer to `GRAPH_COMPLETION`. `[SRC:cognee/base_config.py:L39]` `[SRC:cognee/modules/search/methods/hybrid_deferral.py:L49-L50]` |
| `verbose` | bool | False | Return `{text_result, context_result, objects_result, user_prompt_result, system_prompt_result, evidence}` per entry instead of the raw answer. A per-dataset entry gains an `error` key when that dataset could not be searched. `[SRC:cognee/modules/search/methods/search.py:L652-L670]` `[SRC:cognee/modules/search/methods/search.py:L676-L690]` |
| `retriever_specific_config` | dict \| None | None | Per-retriever options (e.g., `response_model` for typed output, `max_iter` for COT, `context_extension_rounds` for context extension, hybrid lane `top_k` keys). |
| `neighborhood_depth` | int \| None | None | Graph neighbourhood expansion depth; must be a positive int (`InvalidNeighborhoodDepth`). Setting it defers hybrid to `GRAPH_COMPLETION`. `[SRC:cognee/api/v1/search/search.py:L237-L243]` `[SRC:cognee/modules/search/methods/hybrid_deferral.py:L46-L47]` |
| `neighborhood_seed_top_k` | int \| None | None | Seeds for neighbourhood expansion; must be a positive int (`InvalidNeighborhoodSeedTopK`). `[SRC:cognee/api/v1/search/search.py:L244-L250]` |
| `skills` | list[str \| Skill] \| None | None | Skill names or `Skill` objects to load into the agentic retriever; `AGENTIC_COMPLETION` only. `[SRC:cognee/api/v1/search/search.py:L182]` |
| `tools` | list[str] \| None | None | Whitelist of tool names for the agentic retriever; `AGENTIC_COMPLETION` only. `[SRC:cognee/api/v1/search/search.py:L183]` |
| `max_iter` | int \| None | None | Max agentic tool-call iterations before a final answer (`AGENTIC_COMPLETION`; retriever default 6); must be a positive int. It is merged into `retriever_specific_config["max_iter"]`, which `GRAPH_COMPLETION_COT` also reads. `[SRC:cognee/api/v1/search/search.py:L251-L255]` `[SRC:cognee/api/v1/search/search.py:L374-L378]` `[SRC:cognee/modules/search/methods/get_search_type_retriever_instance.py:L381]` `[SRC:cognee/modules/search/methods/get_search_type_retriever_instance.py:L242]` |
| `include_references` | bool | False | Attach structured `EvidenceReference` objects (edge evidence, source chunks) to completions that support them. `[SRC:cognee/modules/search/methods/search.py:L135-L136]` |
| `llm_config` | LLMConfig \| None | None | Per-call LLM provider override applied inside each dataset context. `[SRC:cognee/modules/search/methods/search.py:L137-L138]` |
| `embedding_config` | EmbeddingConfig \| None | None | Per-call embedding provider override, same scope. |
| `code_query` | dict[str, Any] \| None | None | Structured deterministic `CODE` operation and arguments (`query_facts`, `explore` (default), `traverse`, `find_path`, `impact_analysis`, `insights`, `architecture`, `delta`; add `"diagram": "mermaid"` or `"dot"`); requires `query_type=SearchType.CODE`. `[SRC:cognee/api/v1/search/search.py:L173-L181]` `[SRC:cognee/modules/retrieval/code_retriever.py:L816]` |

### Result shapes by search type

Shapes below are for `verbose=False`. Under `only_context=True`, completion types return the rendered user prompt instead (see above).

| SearchType | Return shape |
|---|---|
| `HYBRID_COMPLETION` (default) | LLM answer from document passages plus entity neighbourhoods (or the `GRAPH_COMPLETION` shape when it defers). `[SRC:cognee/api/v1/search/search.py:L89-L93]` |
| `GRAPH_COMPLETION` | LLM answer (`str`, or the `response_model` type) from graph context. `[SRC:cognee/modules/retrieval/graph_completion_retriever.py:L363]` |
| `RAG_COMPLETION` | LLM answer from document chunks, without graph structure. `[SRC:cognee/api/v1/search/search.py:L100-L103]` |
| `TRIPLET_COMPLETION` | LLM answer from retrieved triplets (no answer when no triplets are found). `[SRC:cognee/modules/retrieval/triplet_retriever.py:L19-L29]` |
| `GRAPH_COMPLETION_COT` | LLM answer after chain-of-thought validation/follow-up rounds (`max_iter`, default 4). `[SRC:cognee/modules/search/methods/get_search_type_retriever_instance.py:L242]` |
| `GRAPH_COMPLETION_CONTEXT_EXTENSION` | LLM answer after context-extension rounds (`context_extension_rounds`, default 4). `[SRC:cognee/modules/search/methods/get_search_type_retriever_instance.py:L274-L276]` |
| `GRAPH_COMPLETION_DECOMPOSITION` | LLM answer over decomposed sub-queries (`decomposition_mode`, default `"answer_per_subquery"`). `[SRC:cognee/modules/search/methods/get_search_type_retriever_instance.py:L224-L226]` |
| `GRAPH_SUMMARY_COMPLETION` | LLM answer over summarized graph context. `[SRC:cognee/modules/retrieval/graph_summary_completion_retriever.py:L6-L12]` |
| `CHUNKS` | list of dicts: the stored chunk payload (DocumentChunk fields such as `id`, `text`, `chunk_index`, `chunk_size`, `cut_type`) plus `score` (raw backend distance, lower is better). Honors `node_name` and `node_name_filter_operator`. `[SRC:cognee/modules/chunking/models/DocumentChunk.py:L36-L39]` `[SRC:cognee/infrastructure/databases/vector/lancedb/LanceDBAdapter.py:L511-L514]` `[SRC:cognee/modules/retrieval/chunks_retriever.py:L71-L80]` `[SRC:cognee/modules/retrieval/chunks_retriever.py:L127-L134]` |
| `SUMMARIES` | list of dicts: the stored summary payload (`id`, `text`, ...) plus `score` (raw vector-backend distance, lower is a better match). `[SRC:cognee/tasks/summarization/models.py:L32]` `[SRC:cognee/modules/retrieval/summaries_retriever.py:L111-L119]` |
| `CHUNKS_LEXICAL` | ranked text chunk payloads (optionally `(payload, score)` pairs). `[SRC:cognee/modules/retrieval/lexical_retriever.py:L137-L139]` |
| `CYPHER` | raw graph query results (`query_text` is the Cypher query). `[SRC:cognee/modules/retrieval/cypher_search_retriever.py:L38-L64]` |
| `NATURAL_LANGUAGE` | results of an LLM-generated Cypher query. `[SRC:cognee/modules/retrieval/natural_language_retriever.py:L164-L185]` |
| `TEMPORAL` | LLM answer grounded in time-filtered events (falls back to triplet context when no timestamps or events match). `[SRC:cognee/modules/retrieval/temporal_retriever.py:L124-L163]` |
| `CODING_RULES` | rule texts from the node set(s) named by `node_name` (default `coding_agent_rules`). `[SRC:cognee/modules/retrieval/coding_rules_retriever.py:L15-L33]` |
| `FEELING_LUCKY` | the shape of the type an LLM selects (`HYBRID_COMPLETION` on an empty graph). `[SRC:cognee/modules/search/methods/get_retriever_output.py:L27-L31]` |
| `AGENTIC_COMPLETION` | LLM answer after a tool-calling loop over the loaded skills and tools. `[SRC:cognee/modules/retrieval/agentic_retriever.py:L212]` |
| `CODE` | dict result of the selected code-graph operation (facts, nodes, edges, paths, traversal statistics; `diagram` when requested), no LLM. `[SRC:cognee/api/v1/search/search.py:L115-L119]` `[SRC:cognee/modules/retrieval/code_retriever.py:L870-L895]` |
| `GRAPH_REPORT` | one-element list: a graph report followed by LLM-suggested questions (`top_k` sets the report's `top_n`). `[SRC:cognee/modules/retrieval/graph_report_retriever.py:L182-L190]` `[SRC:cognee/modules/search/methods/get_search_type_retriever_instance.py:L350]` |
| `SKILLS` | list of skill metadata dicts plus `score`; no LLM completion. `[SRC:cognee/modules/retrieval/skills_retriever.py:L155-L175]` |

`[AST:cognee/modules/search/types/SearchType.py:L4]`

### ENABLE_BACKEND_ACCESS_CONTROL behavior

- **Unset**: access control is on whenever the configured graph and vector backends support multi-user mode, which includes the default ladybug + lancedb. Results are then wrapped per dataset. An unsupported dataset-handler/provider pairing does not switch it off: the support check raises `OSError` (set `ENABLE_BACKEND_ACCESS_CONTROL=false` to opt out). `[SRC:cognee/context_global_variables.py:L98-L107]` `[SRC:cognee/context_global_variables.py:L58-L93]` `[SRC:cognee/infrastructure/databases/graph/config.py:L61]` `[SRC:cognee/infrastructure/databases/vector/config.py:L33]` `[SRC:cognee/infrastructure/databases/dataset_database_handler/supported_dataset_database_handlers.py:L50]` `[SRC:cognee/infrastructure/databases/dataset_database_handler/supported_dataset_database_handlers.py:L73-L80]`
- **On (`=true`, or unset as above)**: results wrapped per-dataset with `dataset_id`, `dataset_name`, `dataset_tenant_id`, `search_result` (plus `error` when that dataset could not be searched). Multiple datasets searched concurrently via `asyncio.gather()`. Raises `PermissionDeniedError` if the user lacks read access to any explicitly requested dataset. `[SRC:cognee/modules/search/methods/search.py:L643-L673]` `[SRC:cognee/modules/search/methods/search.py:L428-L503]` `[SRC:cognee/modules/users/permissions/methods/get_specific_user_permission_datasets.py:L35-L36]`
- **`=false`**: all datasets share one context and the search runs once, so dataset scoping is lost. Results come back as a plain list; a single list result is unwrapped one level for backwards compatibility. A plain list therefore needs an explicit `ENABLE_BACKEND_ACCESS_CONTROL=false`. `[SRC:cognee/modules/search/methods/search.py:L85-L89]` `[SRC:cognee/modules/search/methods/search.py:L148-L150]` `[SRC:cognee/modules/search/methods/search.py:L691-L702]`

### Error handling

- `CogneeValidationError("Invalid node_name_filter_operator: ...")` — invalid filter operator. `[SRC:cognee/api/v1/search/search.py:L311-L317]`
- `CogneeValidationError(name="SearchPreconditionError")` — wraps `DatabaseNotCreatedError` / `UserNotFoundError` with an actionable message telling the caller to initialize via `add` + `cognify` first. `[SRC:cognee/api/v1/search/search.py:L319-L331]`
- `DatasetNotFoundError` — raised when any requested dataset name does not resolve; the message lists the missing names. Names resolve only among datasets the caller owns in the current tenant, so pass shared datasets via `dataset_ids`. `recall` applies the same rule. `[SRC:cognee/api/v1/search/search.py:L338-L347]` `[SRC:cognee/modules/data/methods/get_dataset_ids.py:L35-L43]` `[SRC:cognee/api/v1/recall/recall.py:L680]`
- `NoDataError` — raised only when every searched dataset lacks searchable memory; it names each dataset and what it lacks. Otherwise a dataset with no data returns empty results plus an `error` reason and the other datasets still answer. Any other exception fails the whole search. `[SRC:cognee/modules/search/methods/search.py:L547-L605]` `[SRC:cognee/modules/search/methods/search.py:L608-L631]`
- `CogneeValidationError` argument checks: `InvalidNeighborhoodDepth`, `InvalidNeighborhoodSeedTopK`, `InvalidMaxIter` (non-positive values), `InvalidCodeSearchConfig` (`code_query` without `CODE`), `InvalidAgenticSearchConfig` (`skills`/`tools` without `AGENTIC_COMPLETION`), `InvalidAgenticDatasetScope` / `InvalidSkillsDatasetScope` (`AGENTIC_COMPLETION` / `SKILLS` without exactly one explicit dataset), `InvalidHybridSearchConfig` (`wide_search_top_k` / `triplet_distance_penalty` on hybrid). `[SRC:cognee/api/v1/search/search.py:L237-L260]` `[SRC:cognee/api/v1/search/search.py:L303-L309]` `[SRC:cognee/api/v1/search/search.py:L359-L372]` `[SRC:cognee/modules/search/methods/hybrid_deferral.py:L20-L25]`
- `QueryValidationError` — `top_k <= 0`. `[SRC:cognee/modules/search/methods/get_search_type_retriever_instance.py:L77-L79]`
- `UnsupportedSearchTypeError` — `CYPHER` / `NATURAL_LANGUAGE` while `ALLOW_CYPHER_QUERY=false`. `[SRC:cognee/modules/search/methods/get_search_type_retriever_instance.py:L408-L412]`

## cognee.update

```python
async def update(
    data_id: UUID,
    data: BinaryIO | list[BinaryIO] | str | list[str],
    dataset_id: UUID,
    user: User = None,
    node_set: list[str] | None = None,
    vector_db_config: dict | None = None,
    graph_db_config: dict | None = None,
    preferred_loaders: dict[str, dict[str, Any]] | None = None,
    incremental_loading: bool = True,
    data_cache: bool = True,
    chunk_level_diff: bool = True,
    graph_model: type[BaseModel] = KnowledgeGraph,
    custom_prompt: str | None = None,
    chunker: type = TextChunker,
    policy: ChunkPolicy = DEFAULT_CHUNK_POLICY,
) -> dict
```

| Param | Type | Default | Description |
|---|---|---|---|
| `data_id` | UUID | — | Document to replace (its current id or recorded pre-fork id). `[SRC:cognee/api/v1/update/update.py:L77]` |
| `data` | BinaryIO \| list[BinaryIO] \| str \| list[str] | — | Exactly one replacement document (a list must hold one item); a list of any other length raises `IngestionError`. `[SRC:cognee/api/v1/update/update.py:L179-L184]` |
| `dataset_id` | UUID | — | Dataset holding the document. Required. `[SRC:cognee/api/v1/update/update.py:L87]` |
| `user` | User | None | Auth context. Uses the default user if None. `[SRC:cognee/api/v1/update/update.py:L171-L172]` |
| `node_set` | list[str] \| None | None | Tags forwarded to the rebuild's `add`; a non-empty value forces the full rebuild. `[SRC:cognee/api/v1/update/update.py:L301]` `[SRC:cognee/api/v1/update/update.py:L367-L371]` |
| `vector_db_config` | dict \| None | None | Per-call vector DB override for the rebuild's `add` and `cognify`; any value forces the full rebuild. `[SRC:cognee/api/v1/update/update.py:L302]` `[SRC:cognee/api/v1/update/update.py:L312]` `[SRC:cognee/api/v1/update/update.py:L377-L384]` |
| `graph_db_config` | dict \| None | None | Per-call graph DB override, handled like `vector_db_config`. `[SRC:cognee/api/v1/update/update.py:L303]` `[SRC:cognee/api/v1/update/update.py:L313]` `[SRC:cognee/api/v1/update/update.py:L377-L384]` |
| `preferred_loaders` | dict[str, dict[str, Any]] \| None | None | Loader settings for the chunk-level path and the rebuild's `add`. `[SRC:cognee/api/v1/update/update.py:L229]` `[SRC:cognee/api/v1/update/update.py:L304]` |
| `incremental_loading` | bool | True | Forwarded to the rebuild's `add` and `cognify`. `[SRC:cognee/api/v1/update/update.py:L305]` `[SRC:cognee/api/v1/update/update.py:L314]` |
| `data_cache` | bool | True | Forwarded to the rebuild's `add` and `cognify`. `[SRC:cognee/api/v1/update/update.py:L297-L316]` |
| `chunk_level_diff` | bool | True | Diff the new content against the stored text and replace only the chunks the edit touched; falls back to the full rebuild when its preconditions fail. `[SRC:cognee/api/v1/update/update.py:L101-L108]` |
| `graph_model` | type[BaseModel] | `KnowledgeGraph` | Extraction model for the rebuild; a non-default value forces the full rebuild. `[SRC:cognee/api/v1/update/update.py:L372-L376]` |
| `custom_prompt` | str \| None | None | Extraction prompt for the rebuild; any value forces the full rebuild. `[SRC:cognee/api/v1/update/update.py:L372-L376]` |
| `chunker` | type | `TextChunker` | Must match the chunker that built the stored chunks (chunk-level path only). `[SRC:cognee/api/v1/update/update.py:L109-L111]` |
| `policy` | ChunkPolicy | `DEFAULT_CHUNK_POLICY` | Decides which chunks exist after the edit (chunk-level path only). `[SRC:cognee/api/v1/update/update.py:L112-L114]` |

Internal flow:

1. Route to the remote instance when connected via `serve()`.
2. Resolve user (default user if None).
3. Reject a list that does not hold exactly one item (`IngestionError`).
4. Resolve `data_id` (exact, or the recorded pre-fork `legacy_id`); an id that matches nothing raises `UpdateTargetNotFoundError` — `update()` never creates documents.
5. Run the full rebuild instead of the chunk-level path when `chunk_level_diff=False`, a `node_set` or DataItem metadata is given, a custom `graph_model` / `custom_prompt` is given, or a per-call `vector_db_config` / `graph_db_config` is given.
6. Otherwise try the chunk-level incremental update, which replaces only the touched chunks in place; if the engine refuses (first ingestion, non-text content, chunker mismatch, ...), fall back to the full rebuild.
7. Full rebuild: `forget(data_id=..., memory_only=True)` drops the document's graph and vectors but keeps the row, a re-add pinned to the same `data_id` refreshes it, then `cognify(datasets=[dataset_id], ..., raise_on_error=False)` rebuilds the graph. The `data_id` is kept on every path.

Return value: one `UpdateResult` dict on every path — `status` (`"incremental"`, `"unchanged"`, `"full_rebuild"` or `"failed"`), the chunk counters (`regions`, `deleted_chunks`, `added_chunks`, `reused_chunks`, `kept_chunks`, `reindexed_chunks`, `total_chunks`; None on a rebuild), `data_id`, `dataset_id`, `duration_seconds`, `pipeline_run_id`, `fallback` (`reason`, `detail`; set on every rebuild) and `error` (`error_class`, `message`). A failed rebuild cognify is reported as `status="failed"`, not raised. `UpdateResult` is importable from `cognee.api.v1.update`. `[AST:cognee/api/v1/update/result.py:L37]` `[SRC:cognee/api/v1/update/result.py:L55-L68]` `[SRC:cognee/api/v1/update/update.py:L324-L336]` `[SRC:cognee/api/v1/update/__init__.py:L1]`

Provenance: `[AST:cognee/api/v1/update/update.py:L28]` `[SRC:cognee/api/v1/update/update.py:L139-L322]` `[SRC:cognee/api/v1/update/update.py:L339-L385]` `[AST:cognee/api/v1/exceptions/exceptions.py:L47]`

## Environment variables

### LLM key

- `LLM_API_KEY` — API key for the LLM provider. Optional at v1.6.2: without it ingestion runs on local models (GLiNER extraction, fastembed embeddings); LLM-backed search types (HYBRID_COMPLETION, GRAPH_COMPLETION, RAG_COMPLETION, TRIPLET_COMPLETION, etc.) still need it. `[SRC:cognee/api/v1/cognify/cognify.py:L307-L310]` `[SRC:cognee/api/v1/add/add.py:L203-L205]` `[SRC:cognee/api/v1/search/search.py:L227-L229]`

### Optional LLM

- `LLM_PROVIDER` — `"openai"` (default), `"anthropic"`, `"gemini"`, `"ollama"`, `"mistral"`, `"bedrock"`, `"azure"`, `"custom"`, `"llama_cpp"`, `"mcp-sampling"`. `[SRC:cognee/infrastructure/llm/config.py:L19-L32]` `[SRC:cognee/infrastructure/llm/config.py:L109]` `[SRC:cognee/api/v1/add/add.py:L208]`
- `LLM_MODEL` — Model identifier (default: `"openai/gpt-5.6-luna"`). `[SRC:cognee/infrastructure/llm/config.py:L110]`
- `LLM_RATE_LIMIT_ENABLED` — Enable rate limiting (default: False). `[SRC:cognee/infrastructure/llm/config.py:L171]`
- `LLM_RATE_LIMIT_REQUESTS` — Max requests per interval (default: 60; local inference providers such as ollama get 10 when it is not set). `[SRC:cognee/infrastructure/llm/config.py:L172-L174]` `[SRC:cognee/infrastructure/llm/config.py:L40-L45]`

### Cognify extraction

- `GRAPH_EXTRACTOR` — `"auto"` (default: LLM with a usable key, GLiNER demo without), `"llm"` or `"gliner_demo"`; the `extractor=` argument wins. `[SRC:cognee/modules/cognify/config.py:L23-L28]`
- `GLINER_AUTO_INSTALL` — `false` raises `KeylessExtractorNotInstalledError` instead of installing the GLiNER runtime on first use (default true). `[SRC:cognee/modules/cognify/config.py:L29-L34]`
- `EMBEDDING_MAX_COMPLETION_TOKENS` — lowers the cap applied to an explicit `chunk_size`. `[SRC:cognee/infrastructure/llm/utils.py:L71-L76]`

### Optional databases

- `VECTOR_DB_PROVIDER` — built-ins: `"lancedb"` (default, subprocess adapter), `"pgvector"`, `"neptune_analytics"`, `"turso"`. ChromaDB and Qdrant need a registered community adapter; otherwise engine creation raises `OSError`. `[SRC:cognee/infrastructure/databases/vector/config.py:L32]` `[SRC:cognee/infrastructure/databases/vector/config.py:L37]` `[SRC:cognee/infrastructure/databases/vector/create_vector_engine.py:L146-L148]` `[SRC:cognee/infrastructure/databases/vector/create_vector_engine.py:L316-L320]`
- `GRAPH_DATABASE_PROVIDER` — `"ladybug"` (default; `"kuzu"` still accepted as an alias; runs in a subprocess by default), `"neo4j"`. `[SRC:cognee/infrastructure/databases/graph/config.py:L47]` `[SRC:cognee/infrastructure/databases/graph/config.py:L62]` `[SRC:cognee/infrastructure/databases/graph/get_graph_engine.py:L446]`

### User

- `DEFAULT_USER_EMAIL` — Custom default user email (default: `"default_user@example.com"`). `[SRC:cognee/base_config.py:L137]` `[SRC:cognee/modules/users/methods/create_default_user.py:L36]`
- `DEFAULT_USER_PASSWORD` — Custom default user password. `[SRC:cognee/base_config.py:L138]`

### Settings file

- `COGNEE_ENV_FILE` — exact `.env` file to load at import (no search; error if not a file). `[SRC:cognee/shared/env_file.py:L76-L84]`

### Scraping (when add receives URLs)

- `TAVILY_API_KEY` — enables Tavily as an add-data ingestion method (takes precedence over Keenable). `[SRC:cognee/tasks/web_scraper/utils.py:L55-L61]`
- `KEENABLE_API_KEY` — enables Keenable when no Tavily key is set. `[SRC:cognee/tasks/web_scraper/utils.py:L55-L61]`
- `ALLOW_HTTP_REQUESTS` — `false` disables remote URL ingestion (default true). `[SRC:cognee/tasks/web_scraper/ssrf_protection.py:L53-L55]`

### Search defaults

- `DEFAULT_FEEDBACK_INFLUENCE` — default `feedback_influence` (default `"0.0"`, read once at import); a value > 0 defers every hybrid search to graph completion. `[SRC:cognee/base_config.py:L39]` `[SRC:cognee/base_config.py:L129-L133]`
- `ALLOW_CYPHER_QUERY` — `false` disables `CYPHER` and `NATURAL_LANGUAGE`. `[SRC:cognee/modules/search/methods/get_search_type_retriever_instance.py:L408-L412]`

### Tracing / observability

- `COGNEE_TRACING_ENABLED` — `"true"` / `"1"` / `"yes"` enables OpenTelemetry tracing at runtime; `"false"` / `"0"` / `"no"` is an authoritative veto. `[SRC:cognee/base_config.py:L16-L20]` `[SRC:cognee/modules/observability/trace_context.py:L62-L78]`
- Base config field: `cognee_tracing_enabled`. `[SRC:cognee/base_config.py:L141-L145]`
- `LANGFUSE_PUBLIC_KEY` + `LANGFUSE_SECRET_KEY` (both required together) — auto-enable tracing with OTLP pointed at Langfuse (`LANGFUSE_HOST`, then `LANGFUSE_BASE_URL`, else Langfuse cloud), unless vetoed. `[SRC:cognee/base_config.py:L100-L127]`
- `enable_tracing()` also sets up a MeterProvider and an OTel log bridge, so all cognee loggers emit OTel logs; `disable_tracing()` shuts down all three. `[SRC:cognee/modules/observability/trace_context.py:L18-L59]`

### Access control

- `ENABLE_BACKEND_ACCESS_CONTROL` — `"true"` enables per-user dataset access filtering and the wrapped result shape described above; when unset it is on whenever the backends support multi-user mode (including the defaults), and any other set value (e.g. `"false"`) turns it off. `[SRC:cognee/context_global_variables.py:L98-L107]`

### Structured output (custom pipeline authors)

- `STRUCTURED_OUTPUT_FRAMEWORK` — selects the backend for `LLMGateway.acreate_structured_output`: default `litellm_native` (plain litellm with schema-native `response_format`, or a prompted-JSON fallback, no instructor); set `instructor` or `baml` to opt back. `[SRC:cognee/infrastructure/llm/config.py:L101-L107]` `[SRC:cognee/infrastructure/llm/LLMGateway.py:L113-L154]`

Provenance for env-var list: `[SRC:cognee/api/v1/add/add.py:L203-L215]` (Add) and `[SRC:cognee/api/v1/cognify/cognify.py:L307-L315]` (Cognify), plus the config sources cited above.
