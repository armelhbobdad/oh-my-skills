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
- [Memory provenance visualization and schema inventory](#memory-provenance-visualization-and-schema-inventory)
- [Pruning](#pruning--cogneeprune)
- [Sessions](#sessions--cogneesession)
- [Migrations](#migrations--cogneerun_migrations)
- [Agents — cognee.agents](#agents--cogneeagents)
- [Memory export, push, validation and reports](#memory-export-push-validation-and-reports)
- [Tool connections — cognee.tools](#tool-connections--cogneetools)
- [Version — cognee.get_cognee_version](#version--cogneeget_cognee_version)
- [Full Type Definitions](#full-type-definitions)
  - [cognee.exceptions](#cogneeexceptions--error-hierarchy)
  - [Task](#cogneepipelinestask--detailed)
  - [PipelineRunInfo](#pipelineruninfo--pipeline-status)
  - [Memory entry types](#memory-entry-types--cogneememoryentry)
  - [Session lifecycle models](#session-lifecycle-models--cogneesessionrecord-and-cogneesessionmodelusage)
- [Full Integration Patterns](#full-integration-patterns)

## Core workflow functions

#### `cognee.add(...)` — ingest data into a dataset

```python
async def add(
    data: BinaryIO | list[BinaryIO] | str | list[str] | DataItem | list[DataItem] | Any,
    dataset_name: str = DEFAULT_DATASET_NAME,  # "main_dataset"
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
)  # no return annotation; returns the dataset's PipelineRunInfo
```

**Accepted `data` forms:** raw text strings (anything not starting with `/` or `file://`), absolute file paths, `file://` URLs, `s3://` paths, HTTP(S) URLs, open binary file handles, lists of any of the above, or DLT `DataItem` objects. A GitHub/GitLab repository URL (or any URL ending in `.git`) is shallow-cloned and ingested as one code-repo item that cognify runs through the code graph pipeline; this requires `ALLOW_HTTP_REQUESTS` and `git` on PATH. `[SRC:cognee/api/v1/add/add.py:L84-L88]` Cognee auto-detects supported file formats: `.txt`, `.md`, `.csv`, `.pdf`, `.png/.jpg/.jpeg` (OCR/vision), `.mp3/.wav` (transcription), source files (`.py/.js/.ts/...`), Office docs (`.docx/.pptx`). `[SRC:cognee/api/v1/add/add.py:L91-L97]`

**add() never updates a document:** a file already in the dataset (same path, or same filename for an upload) with different content raises `DocumentUpdateRequiredError`; replace it with `cognee.update(data_id=..., data=..., dataset_id=...)`. Re-adding identical content is a no-op. `[SRC:cognee/api/v1/add/add.py:L70-L74]`

**Env:** `LLM_API_KEY` is optional. add() validates only the embedding side of the provider config `[SRC:cognee/api/v1/add/add.py:L248]`; with no key, cognify's default `GRAPH_EXTRACTOR=auto` extracts with the local GLiNER demo model and embeds with the local fastembed model `[SRC:cognee/api/v1/cognify/cognify.py:L308-L310]`. The GLiNER runtime installs itself on first use unless `GLINER_AUTO_INSTALL=false` `[SRC:cognee/modules/cognify/config.py:L29-L34]`. Cognee uses the default user `default_user@example.com` when `user` is None (auto-created on first use) `[SRC:cognee/api/v1/add/add.py:L119]`. See `references/core-workflow.md` for full env-var list.

**Returns:** the single dataset's `PipelineRunInfo` (the executor's `{dataset_id: info}` map is unwrapped) `[SRC:cognee/api/v1/add/add.py:L347-L348]`; while connected through `serve()`, a `SimpleNamespace` of the remote response `[SRC:cognee/api/v1/add/add.py:L221-L227]`.

Provenance: `[AST:cognee/api/v1/add/add.py:L39]`

#### `cognee.cognify(...)` — build the knowledge graph

```python
async def cognify(
    datasets: str | list[str] | list[UUID] | None = None,
    user: User = None,
    graph_model: BaseModel = KnowledgeGraph,
    chunker=TextChunker,
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
)  # no return annotation; dict, or DryRunEstimate with dry_run=True
```

**Pipeline:** document classification → text chunking → entity extraction → relationship detection → graph construction (with embeddings) → hierarchical summarization. Supports custom `graph_model` (Pydantic) for domain schemas and `custom_prompt` for extraction guidance. Use `temporal_cognify=True` to extract events with timestamps (pairs with `SearchType.TEMPORAL`).

**Parameter notes:**

- `functional_relationships` — relationship names that hold one target per source (e.g. `{"ceo_of"}`); conflicting assertions are resolved by recency and older ones are tagged as superseded, nothing is deleted. Off by default. `[SRC:cognee/api/v1/cognify/cognify.py:L204-L209]`
- `extractor` — `"llm"`, `"gliner_demo"` (`"gliner"` is an alias `[SRC:cognee/modules/cognify/config.py:L64]`) or None, which resolves to the `GRAPH_EXTRACTOR` setting (`"auto"`: `llm` with a usable LLM key, `gliner_demo` without) `[SRC:cognee/api/v1/cognify/cognify.py:L229-L239]`. `gliner_demo` raises with a custom `graph_model`, with `temporal_cognify=True` or with `dry_run=True`, and ignores `custom_prompt` with a warning. `[SRC:cognee/api/v1/cognify/cognify.py:L323-L332]` · `[SRC:cognee/api/v1/cognify/cognify.py:L435-L441]` While connected to a remote instance, any explicit `extractor` (including `"llm"`) raises. `[SRC:cognee/api/v1/cognify/cognify.py:L367-L373]`
- `chunk_attachment` — `"direct"` (same as None) or `"all"` (link each chunk to every stored node reachable from its extracted root). Requires a custom DataPoint `graph_model`; raises with `temporal_cognify=True` or while connected to a remote instance. `[SRC:cognee/api/v1/cognify/cognify.py:L334-L350]` · `[SRC:cognee/api/v1/cognify/cognify.py:L357-L361]`
- `dry_run` — return a stage-level estimate of LLM token usage and rough cost without LLM calls or graph writes. `[SRC:cognee/api/v1/cognify/cognify.py:L210-L212]`
- `raise_on_error` — see Returns.
- `ontology_file_path` — a path, or comma-separated paths, to the ontology used for extraction schema planning and graph integration. `[SRC:cognee/api/v1/cognify/cognify.py:L186-L187]`
- `llm_config`, `embedding_config`, `data_cache` — forwarded to `run_pipeline`. `[SRC:cognee/api/v1/cognify/cognify.py:L523-L525]`

**Returns:** in blocking mode, a dict mapping `dataset_id → PipelineRunInfo` `[SRC:cognee/modules/pipelines/layers/pipeline_execution_mode.py:L26-L53]`. An errored run raises `CognifyFailedError` by default (`raise_on_error=True`), and run-level exceptions are wrapped in it, except errors that are already `CogneeApiError` subclasses; pass `raise_on_error=False` to get the dict containing the `PipelineRunErrored` back (a run-level exception is then re-raised unwrapped). `[SRC:cognee/api/v1/cognify/cognify.py:L539-L550]` In background mode, a dict mapping `dataset_id → initial PipelineRunInfo` — use `pipeline_run_id` to track status `[SRC:cognee/modules/pipelines/layers/pipeline_execution_mode.py:L76]` · `[SRC:cognee/modules/pipelines/layers/pipeline_execution_mode.py:L129]`. With `dry_run=True`, a `DryRunEstimate` `[SRC:cognee/api/v1/cognify/cognify.py:L418]` · `[SRC:cognee/modules/cognify/estimator.py:L105-L115]`.

Provenance: `[AST:cognee/api/v1/cognify/cognify.py:L110]`

#### `cognee.search(...)` — query the knowledge graph

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

**Key behaviors:**

- **`query_type`** defaults to `SearchType.HYBRID_COMPLETION` `[SRC:cognee/api/v1/search/search.py:L43]` · `[SRC:cognee/modules/search/types/SearchType.py:L8]`. Hybrid defers to `GRAPH_COMPLETION` (logged only at INFO level `[SRC:cognee/modules/search/methods/get_retriever_output.py:L35-L42]`) for a custom `node_type` (or `node_name` with `node_type=None`), a set `neighborhood_depth`, `feedback_influence > 0`, or a missing `DocumentChunk_text` collection `[SRC:cognee/modules/search/methods/hybrid_deferral.py:L28-L74]`. Results do not name the type that ran, so pin `query_type` when the result shape matters. `[SRC:cognee/api/v1/search/search.py:L53-L55]`
- **`top_k`** defaults to 15, applied per dataset. `HYBRID_COMPLETION` gives each lane `min(top_k, 10)`; raise a lane with the `chunks_top_k`, `entities_top_k` or `facts_top_k` keys in `retriever_specific_config` (not capped). `[SRC:cognee/api/v1/search/search.py:L215-L218]` · `[SRC:cognee/modules/search/methods/get_search_type_retriever_instance.py:L41-L51]` A `top_k <= 0` raises `QueryValidationError`. `[SRC:cognee/modules/search/methods/get_search_type_retriever_instance.py:L77-L79]`
- **`wide_search_top_k`** and **`triplet_distance_penalty`** default to None; the graph retrievers apply 100 and 6.5 internally `[SRC:cognee/modules/retrieval/graph_completion_retriever.py:L66-L67]`. Any explicit value with `HYBRID_COMPLETION` raises `CogneeValidationError(name="InvalidHybridSearchConfig")`, so set `query_type=SearchType.GRAPH_COMPLETION` when you use them. `[SRC:cognee/modules/search/methods/hybrid_deferral.py:L20-L25]`
- **`feedback_influence`** defaults to `get_base_config().default_feedback_influence`, read once at import time from env `DEFAULT_FEEDBACK_INFLUENCE` (default `"0.0"`) `[SRC:cognee/base_config.py:L39]`. Any value `> 0` makes `HYBRID_COMPLETION` defer to `GRAPH_COMPLETION`.
- **`node_name_filter_operator`** must be `"OR"` or `"AND"` (case-insensitive) — anything else raises `CogneeValidationError`. `[SRC:cognee/api/v1/search/search.py:L311-L317]`
- **`neighborhood_depth`** and **`neighborhood_seed_top_k`** must each be a positive integer when set (non-None) — anything else raises `CogneeValidationError` (`InvalidNeighborhoodDepth` / `InvalidNeighborhoodSeedTopK`). `[SRC:cognee/api/v1/search/search.py:L237-L250]`
- **`skills`** / **`tools`** (agentic retriever skill names and tool whitelist) require `query_type=SearchType.AGENTIC_COMPLETION`, otherwise `InvalidAgenticSearchConfig` `[SRC:cognee/api/v1/search/search.py:L303-L309]`. **`max_iter`** caps agentic tool-call iterations (default 6 in the retriever) and must be a positive integer (`InvalidMaxIter`). `[SRC:cognee/api/v1/search/search.py:L251-L255]` · `[SRC:cognee/modules/search/methods/get_search_type_retriever_instance.py:L381]` `AGENTIC_COMPLETION` and `SKILLS` need exactly one explicit dataset (`InvalidAgenticDatasetScope` / `InvalidSkillsDatasetScope`). `[SRC:cognee/api/v1/search/search.py:L359-L372]`
- **`code_query`** carries the structured deterministic operation for `SearchType.CODE`; with any other type it raises `InvalidCodeSearchConfig`. `[SRC:cognee/api/v1/search/search.py:L256-L260]`
- **`include_references`** attaches structured `EvidenceReference` objects (edge evidence, source chunks) to completions that support them; **`llm_config`** / **`embedding_config`** are per-call provider overrides applied inside each dataset context. `[SRC:cognee/modules/search/methods/search.py:L135-L138]`
- **`only_context=True`** returns, without calling the LLM, the user prompt that the LLM would have received when the retriever built one, and the bare retrieved context otherwise. `[SRC:cognee/modules/retrieval/session_aware_completion.py:L452-L453]` · `[SRC:cognee/modules/search/models/SearchResultPayload.py:L96-L97]`
- **`session_id`** wires the search into a conversation session. It is passed to most completion retrievers, including `HYBRID_COMPLETION`, `RAG_COMPLETION`, `GRAPH_COMPLETION`, the `GRAPH_COMPLETION_*` variants, `TEMPORAL`, `SUMMARIES`, `CYPHER` and `AGENTIC_COMPLETION`. `[SRC:cognee/modules/search/methods/get_search_type_retriever_instance.py:L149]` · `[SRC:cognee/modules/search/methods/get_search_type_retriever_instance.py:L397]`
- **`ENABLE_BACKEND_ACCESS_CONTROL` env var** changes the result shape. When it is unset, access control is on whenever the graph and vector backends support multi-user mode, which includes the default ladybug + lancedb pair `[SRC:cognee/context_global_variables.py:L98-L105]`. Results are then wrapped per dataset with `dataset_id`, `dataset_name`, `dataset_tenant_id` and `search_result` fields `[SRC:cognee/modules/search/methods/search.py:L643-L650]`. A plain list (unwrapped) needs an explicit `ENABLE_BACKEND_ACCESS_CONTROL=false`.
- **`CHUNKS` result shape:** list of dicts with `id`, `text`, `chunk_index`, `chunk_size`, `cut_type` and `score` (the raw backend distance, lower is a better match); `CHUNKS` honors `node_name` and `node_name_filter_operator`. `[SRC:cognee/modules/retrieval/chunks_retriever.py:L78]` · `[SRC:cognee/modules/retrieval/chunks_retriever.py:L132]` **`SUMMARIES` result shape:** list of dicts with `id`, `text` and `score` (raw backend distance). `[SRC:cognee/modules/retrieval/summaries_retriever.py:L118]`
- Setting `verbose=True` returns `{text_result, context_result, objects_result, user_prompt_result, system_prompt_result, evidence}` per dataset; the two prompt keys are None unless an `only_context` call built them. Under access control, a per-dataset entry gains an `error` key when that dataset could not be searched. `[SRC:cognee/modules/search/methods/search.py:L654-L670]` · `[SRC:cognee/modules/search/methods/search.py:L679-L688]`

Provenance: `[AST:cognee/api/v1/search/search.py:L41]`

#### `cognee.memify(...)` — enrich an existing graph

```python
async def memify(
    extraction_tasks: Sequence[Task | str] | None = None,
    enrichment_tasks: Sequence[Task | str] | None = None,
    data: Any | None = None,
    dataset: str | UUID = DEFAULT_DATASET_NAME,  # "main_dataset"
    user: User = None,
    node_type: type | None = NodeSet,
    node_name: list[str] | None = None,
    vector_db_config: dict | None = None,
    graph_db_config: dict | None = None,
    run_in_background: bool = False,
)
```

Pulls a subgraph (or the full graph when `data=None`) through a small two-stage pipeline of extraction + enrichment tasks. With no tasks given, the defaults run `get_triplet_datapoints` (only when `triplet_embedding` is enabled in the cognify config) and then `index_data_points` `[SRC:cognee/memify_pipelines/memify_default_tasks.py:L6-L15]`; they do not create `Rule` nodes, whose logic lives in `cognee/tasks/codingagents` `[SRC:cognee/tasks/codingagents/coding_rule_associations.py:L20]`. Filter which subgraph to enrich with `node_type` + `node_name`. `[AST:cognee/modules/memify/memify.py:L27]`

**Task names:** string entries in `extraction_tasks` and `enrichment_tasks` resolve through a registry of 11 named tasks: `extract_subgraph`, `extract_subgraph_chunks`, `get_triplet_datapoints`, `extract_user_sessions`, `cognify_session`, `extract_agent_trace_feedbacks`, `cognify_agent_trace_feedback`, `apply_feedback_weights`, `detect_entity_duplicates`, `merge_entity_duplicates`, `index_data_points`. Unknown names raise `CogneeValidationError`. `[SRC:cognee/modules/memify/memify.py:L95-L96]` · `[SRC:cognee/memify_pipelines/memify_task_registry.py:L38-L52]`

#### `cognee.update(...)` — replace data inside a dataset

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

Requires both `data_id` and `dataset_id`, and replaces exactly one document: a list that does not hold exactly one item raises `IngestionError` `[SRC:cognee/api/v1/update/update.py:L179-L184]`. `data_id` is resolved first (exact, or the recorded pre-fork legacy id) and an id that matches nothing raises `UpdateTargetNotFoundError` — update() never creates documents `[SRC:cognee/api/v1/update/update.py:L193-L197]`. By default (`chunk_level_diff=True`) it diffs the new content against the stored text and replaces only the chunks the edit touched `[SRC:cognee/api/v1/update/update.py:L223]`. Otherwise, or when the chunk-level preconditions fail, it runs a full rebuild — `forget(memory_only=True)`, a re-add pinned to the same row, then `cognify` — and the document keeps its `data_id` on every path `[SRC:cognee/api/v1/update/update.py:L286-L322]`. A `node_set`, a non-default `graph_model` or `custom_prompt`, or a per-call `vector_db_config`/`graph_db_config` also forces the full rebuild `[SRC:cognee/api/v1/update/update.py:L361-L384]`. `chunker` and `policy` apply to the chunk-level path only.

**Returns:** one `UpdateResult` dict with `status` (`"incremental"`, `"unchanged"`, `"full_rebuild"` or `"failed"`), the chunk counters (None on a rebuild), `data_id`, `dataset_id`, `duration_seconds`, `pipeline_run_id`, `fallback` and `error`. A failed rebuild cognify is reported in the result, not raised. `[SRC:cognee/api/v1/update/update.py:L116-L133]` · `[AST:cognee/api/v1/update/update.py:L28]`

### Dataset management — `cognee.datasets`

Namespace class with static async methods. Use this instead of the deprecated top-level `cognee.delete`.

| Method | Signature | Purpose |
|---|---|---|
| `list_datasets` | `(user=None)` | Return all datasets the user can read |
| `discover_datasets` | `(directory_path)` (sync) | Scan a directory and return candidate dataset names |
| `list_data` | `(dataset_id, user=None)` | Return all data items in a dataset |
| `has_data` | `(dataset_id, user=None) -> bool` | Check whether a dataset has any data |
| `get_status` | `(dataset_ids, pipeline_names=None) -> dict` | Pipeline status per dataset: the flat cognify status by default (or for one pipeline name), a nested `{dataset_id: {pipeline: status}}` map for several |
| `get_progress` | `(dataset_ids, pipeline_names=None) -> dict` | Same flat-or-nested shapes as `get_status`, each value `{status, progress}` |
| `empty_dataset` | `(dataset_id, user=None)` | Deletes the dataset record with its data rows, graph/vector nodes and attributed sessions — the dataset is not preserved |
| `delete_data` | `(dataset_id, data_id, user=None, mode="soft", delete_dataset_if_empty=False)` | Remove one item — **never use `mode="hard"`**, it is dangerous |
| `delete_all` | `(user=None)` | Deletes every dataset the user can delete |

Provenance: `[AST:cognee/api/v1/datasets/datasets.py:L105]` · `[SRC:cognee/api/v1/datasets/datasets.py:L37-L62]` · `[SRC:cognee/api/v1/datasets/datasets.py:L201-L213]` · `[SRC:cognee/api/v1/datasets/datasets.py:L316-L323]`

### Configuration — `cognee.config`

Namespace class with 45 static methods that mutate global Cognee runtime state. Call before `add`/`cognify`:

```python
cognee.config.set_llm_provider("openai")        # or "anthropic", "gemini", "ollama", "mistral", "bedrock"
cognee.config.set_llm_model("gpt-4o-mini")
cognee.config.set_llm_api_key("sk-...")
cognee.config.set_embedding_provider("fastembed")
cognee.config.set_embedding_model("BAAI/bge-small-en-v1.5")
cognee.config.set_embedding_dimensions(384)
cognee.config.set_vector_db_provider("lancedb")  # default; or "pgvector", "neptune_analytics", "turso"
cognee.config.set_graph_database_provider("ladybug")  # default ("kuzu" is an alias); or "neo4j"
cognee.config.system_root_directory("/path/to/system")
```

**Providers:** the default graph provider is `ladybug` `[SRC:cognee/infrastructure/databases/graph/config.py:L47]`; `"kuzu"` is still accepted as an alias `[SRC:cognee/infrastructure/databases/graph/get_graph_engine.py:L446]`, and the graph DB runs in a subprocess by default `[SRC:cognee/infrastructure/databases/graph/config.py:L62]`. The built-in vector providers are `lancedb` (default, subprocess adapter by default), `pgvector`, `neptune_analytics` and `turso` `[SRC:cognee/infrastructure/databases/vector/config.py:L32]` · `[SRC:cognee/infrastructure/databases/vector/config.py:L37]`. ChromaDB and Qdrant need a registered community adapter; otherwise engine creation raises `OSError`. `[SRC:cognee/api/v1/config/config.py:L609]` · `[SRC:cognee/infrastructure/databases/vector/create_vector_engine.py:L316-L320]`

**Bulk setters:** `set_llm_config(dict)`, `set_embedding_config(dict)`, `set_vector_db_config(dict)`, `set_graph_db_config(dict)`, `set_relational_db_config(dict)`, `set_migration_db_config(dict)`, `set_translation_config(dict)`, `set_recall_config(dict)`. They route through `_update_config`, which coerces string values to the field's declared `bool`/`int`/`float` type and raises `InvalidConfigAttributeError` on unknown keys. `[SRC:cognee/api/v1/config/config.py:L398-L430]` · `[SRC:cognee/api/v1/config/config.py:L162-L167]`

**Generic setter:** `cognee.config.set(key, value, persist=False)` — maps to the right setter via the 30-key `_setter_mapping` table, which includes `graph_database_subprocess_enabled`, `kuzu_num_threads`, `kuzu_buffer_pool_size`, `kuzu_max_db_size`, `vector_db_subprocess_enabled`, `recall_warmup_shortcircuit`, `recall_warmup_threshold`, `recall_warmup_cache_ttl` `[SRC:cognee/api/v1/config/config.py:L794-L825]`. Useful for CLI-style config: unknown keys fall back to `set_embedding_config({key: value})` when the embedding config exposes that attribute; otherwise it raises `InvalidConfigAttributeError`. `persist=True` also writes the value into the `.env` this process loaded (else `.env` in the working directory) and returns `{path, created, env_var}`. `[SRC:cognee/api/v1/config/config.py:L948-L971]` · `[SRC:cognee/api/v1/config/config.py:L107]` Read values back with `cognee.config.get(key, reveal_secrets=False)` / `get_all(reveal_secrets=False)`; secrets are masked unless revealed. `[SRC:cognee/api/v1/config/config.py:L867-L913]`

**Important:** `set_embedding_dimensions` coerces `str` → `int` and raises `ValueError` if the value is not a positive integer. `[SRC:cognee/api/v1/config/config.py:L470-L496]`

See `references/config.md` for the full method list. Provenance: `[AST:cognee/api/v1/config/config.py:L171]`

### Pipelines primitives — `cognee.pipelines` and `cognee.modules.pipelines`

The top-level `pipelines` name is bound by `from .modules import pipelines` `[SRC:cognee/__init__.py:L67]` to `cognee.modules.pipelines`, which exports `Task`, `run_tasks`, `run_tasks_parallel` and `run_pipeline` `[SRC:cognee/modules/pipelines/__init__.py:L75-L78]`. The import statement `from cognee.pipelines import ...` loads the separate `cognee/pipelines` package instead: there `Task`, `run_tasks` and `run_tasks_parallel` are lazy re-exports of the same objects, but `run_pipeline` is the lightweight `BoundTask` runner `(steps, *, data=None, user=None, dataset=None, pipeline_name="pipeline", context=None) -> list`, with no dataset locking or run records `[SRC:cognee/pipelines/__init__.py:L22-L28]` · `[AST:cognee/modules/pipelines/operations/run_pipeline.py:L37]`. For the dataset-aware orchestrator, import from `cognee.modules.pipelines`.

- `Task(executable, *args, task_config=None, batch_size=None, enriches=False, needs_llm=True, **kwargs)` — class wrapping any callable (sync fn, coroutine fn, generator, async generator). Auto-detects type via `inspect` and runs with the right execution path. `task_config={"batch_size": N}` (or `batch_size=N`) controls batching. `needs_llm=False` on tasks that never call the LLM lets `run_pipeline` skip the first-run LLM probe (`pipeline_needs_llm`); the flag is not forwarded to the executable. `[AST:cognee/modules/pipelines/tasks/task.py:L188]` · `[SRC:cognee/modules/pipelines/tasks/task.py:L209-L218]` · `[SRC:cognee/modules/pipelines/tasks/task.py:L160]`
- `run_tasks(tasks, dataset_id, data=None, user=None, pipeline_name="unknown_pipeline", incremental_loading=False, data_per_batch=20, extras=None, rollback_handler=None, llm_config=None, embedding_config=None, data_cache=False)` — async generator. `tasks` may be a list or a per-item resolver callable. Yields `PipelineRunStarted` → `PipelineRunCompleted`/`PipelineRunErrored`. `[AST:cognee/modules/pipelines/operations/run_tasks.py:L39]`
- `run_tasks_parallel(tasks) -> Task` — wraps a list of tasks in a new `Task` that runs them concurrently via `asyncio.gather`. Returns the last result when more than one task ran, otherwise `[]`. `[AST:cognee/modules/pipelines/operations/run_parallel.py:L8]`
- `run_pipeline(tasks=None, data=None, datasets=None, user=None, pipeline_name="custom_pipeline", vector_db_config=None, graph_db_config=None, incremental_loading=False, data_per_batch=20, rollback_handler=None, llm_config=None, embedding_config=None, data_cache=False, skip_connection_test=False, needs_llm=True)` — top-level async generator. `tasks` may be a per-item resolver callable (then pass `needs_llm` yourself). Internally calls `validate_pipeline_tasks`, `setup_and_check_environment`, then iterates `run_pipeline_per_dataset` for each authorized dataset under the per-dataset lock (`get_dataset_lock`). `[AST:cognee/modules/pipelines/operations/pipeline.py:L53]`

**Pipeline naming:** run history does not gate runs — concurrent runs on one dataset are serialized by the per-dataset lock and already-processed documents are skipped by incremental loading `[SRC:cognee/modules/pipelines/operations/pipeline.py:L133-L135]`. Graph-writing custom pipelines should keep a name listed in `cognee.modules.improve.graph_changes.WRITE_PIPELINE_NAMES` (the default `"custom_pipeline"` is listed), because improve()'s enrichment gate ignores bespoke names and may report their writes as already enriched. `[SRC:cognee/modules/run_custom_pipeline/run_custom_pipeline.py:L62-L68]` · `[SRC:cognee/modules/improve/graph_changes.py:L39-L50]`

**Custom-pipeline entry point:** `cognee.run_custom_pipeline(tasks=None, data=None, dataset="main_dataset", ...)` — higher-level wrapper that hides the dataset-resolution and pipeline-executor selection from you. `[AST:cognee/modules/run_custom_pipeline/run_custom_pipeline.py:L14]`

### Data primitives — `cognee.low_level`

```python
from cognee.low_level import DataPoint, setup, Edge, FromIdentity
from cognee.low_level import EntitySpec, GraphSchemaSpec, graph_model_from_spec, graph_spec_to_json_schema
```

`cognee.low_level` exports exactly `DataPoint`, `Edge`, `FromIdentity`, `setup`, `EntitySpec`, `GraphSchemaSpec`, `graph_model_from_spec` and `graph_spec_to_json_schema`, plus `graph_schema_to_graph_model` and `graph_model_to_graph_schema`, which resolve lazily through a module `__getattr__`. `[SRC:cognee/low_level.py:L1-L21]`

- `DataPoint` — alias for `cognee.infrastructure.engine.ExtendableDataPoint`. Pydantic base class that becomes a graph node when added via `cognee.tasks.storage.add_data_points(...)`. Assigning another `DataPoint` to a field creates an edge labeled after the field name; use `Edge(weight=..., relationship_type=...)` (also exported here) for custom edge metadata. Set `metadata = {"index_fields": [...]}` to control which fields are embedded into the vector store.
- `FromIdentity()` — field annotation marking a nested DataPoint field that the LLM answers by identity string (`is_a: Annotated[Role, FromIdentity()]`). `[SRC:cognee/infrastructure/engine/models/FieldAnnotations.py:L95-L102]`
- `EntitySpec` / `GraphSchemaSpec` — the graph-schema DSL; `graph_spec_to_json_schema(spec)` compiles a spec (model or plain dict) into a graph-model JSON Schema, and `graph_model_from_spec(spec)` validates, compiles and generates the DataPoint-derived model class. `[SRC:cognee/modules/graph_models/compiler.py:L119-L120]` · `[SRC:cognee/modules/graph_models/compiler.py:L135-L136]`
- `setup()` — initializes the relational database + tables, then the PGVector database + tables `[SRC:cognee/modules/engine/operations/setup.py:L9-L17]`. `add` and `memify` call it internally `[SRC:cognee/api/v1/add/add.py:L250]` · `[SRC:cognee/modules/memify/memify.py:L104]`, and `run_pipeline` creates the same tables through `setup_and_check_environment` `[SRC:cognee/modules/pipelines/layers/setup_and_check_environment.py:L46-L48]`; custom code that inserts DataPoints outside a pipeline may need to call it explicitly.

Provenance: `[SRC:cognee/low_level.py:L1-L21]` · `[EXT:https://docs.cognee.ai/guides/custom-data-models]`

### Observability / Tracing — `cognee.enable_tracing` and friends

OpenTelemetry-based in-memory tracing. All sync functions.

```python
cognee.enable_tracing(console_output=False)   # TracerProvider + CogneeSpanExporter, MeterProvider, OTel log bridge
cognee.disable_tracing()                       # shuts down all three providers
trace = cognee.get_last_trace()                # CogneeTrace | None — most recent complete trace
traces = cognee.get_all_traces()               # list[CogneeTrace] — every trace in memory
cognee.clear_traces()                          # empties the in-memory buffer
```

- `enable_tracing()` also sets up a MeterProvider for metrics and an OTel log bridge, so all cognee loggers emit OTel log records; `disable_tracing()` shuts down all three. `[SRC:cognee/modules/observability/trace_context.py:L18-L59]`
- Module-level `_tracing_enabled` flag, also honored via `cognee_tracing_enabled` base-config field or `COGNEE_TRACING_ENABLED=true|1|yes` env var. Read the effective state with the sync `is_tracing_enabled()`, exported from `cognee.modules.observability` (not a top-level `cognee` name). `[AST:cognee/modules/observability/trace_context.py:L62]` · `[SRC:cognee/modules/observability/__init__.py:L6]`
- `COGNEE_TRACING_ENABLED=false|0|no` is an authoritative veto `[SRC:cognee/base_config.py:L16-L20]`. Setting both `LANGFUSE_PUBLIC_KEY` and `LANGFUSE_SECRET_KEY` points the OTLP exporter at Langfuse and turns tracing on unless vetoed; setting only one raises `ValueError`. `[SRC:cognee/base_config.py:L100-L127]`
- A direct `cognee.enable_tracing()` raises `ImportError` (`pip install cognee[tracing]`) when OpenTelemetry is missing `[SRC:cognee/modules/observability/tracing.py:L100-L105]`. Only the lazy env/config path in `is_tracing_enabled()` swallows that error and leaves spans as `_NullSpan` no-ops. `[SRC:cognee/modules/observability/trace_context.py:L90-L97]`
- Provenance: `[SRC:cognee/modules/observability/trace_context.py:L18]`

### Visualization — `cognee.visualize_graph`

```python
async def visualize_graph(
    destination_file_path: str | None = None,
    include_session_events: bool = True,
    session_ids: list | None = None,
    user: User | None = None,
    dataset: str | UUID | None = DEFAULT_DATASET_NAME,  # "main_dataset"
    *,
    full: bool = False,
    query: str | None = None,
    seed_node_ids: list[str] | None = None,
    recall_result: Any | None = None,
    neighborhood_depth: int = DEFAULT_NEIGHBORHOOD_DEPTH,  # 2
    neighborhood_seed_top_k: int = DEFAULT_SEED_TOP_K,  # 10
    max_nodes: int = DEFAULT_MAX_NODES,  # 500
) -> str
```

Renders a bounded subgraph of `dataset` around seed nodes rather than the whole graph: seeds come from `seed_node_ids`, then `recall_result` provenance, then `query` vector hits, then the highest-degree nodes; the subgraph is expanded `neighborhood_depth` hops and capped at `max_nodes`. `full=True` restores the legacy whole-graph render, and `dataset=None` renders the current context's graph. `[SRC:cognee/api/v1/visualize/visualize.py:L210-L241]` · `[SRC:cognee/modules/visualization/subgraph_data.py:L24-L26]` Returns the HTML string; also writes to `destination_file_path` when provided (otherwise saves `~/graph_visualization.html`). `[SRC:cognee/modules/visualization/cognee_network_visualization.py:L243-L244]` · `[AST:cognee/api/v1/visualize/visualize.py:L193]` `cognee.visualize` is an alias of this function. `[SRC:cognee/api/v1/__init__.py:L8]`

**Privacy:** with the default `include_session_events=True`, the HTML embeds the user's session search and feedback Q&A history on its Memory timeline; pass `include_session_events=False` before sharing the file. `[SRC:cognee/api/v1/visualize/visualize.py:L217-L222]`

Additional helper: `cognee.cognee_network_visualization(graph_data, destination_file_path=None, schema_data=None, search_events=None) -> str` (async) — same renderer, useful when you already have `(nodes, edges)` graph data. `schema_data` is an optional pre-built schema payload and `search_events` an optional list of Memory-tab events. It reads node embeddings from the vector store, best-effort, for a semantic map. `[AST:cognee/modules/visualization/cognee_network_visualization.py:L154]` · `[SRC:cognee/modules/visualization/cognee_network_visualization.py:L43-L68]`

Helpers that are not top-level `cognee` names (import them with `from cognee.api.v1.visualize import ...`) `[SRC:cognee/api/v1/visualize/__init__.py:L1-L10]`:

- `visualize_graph_json(include_session_events=True, session_ids=None, user=None, dataset="main_dataset", *, full=False, query=None, seed_node_ids=None, recall_result=None, neighborhood_depth=2, neighborhood_seed_top_k=10, max_nodes=500) -> dict` (async) — the same bounded subgraph that `visualize_graph` renders, as a JSON-safe dict without the semantic layout. `[AST:cognee/api/v1/visualize/visualize.py:L271]`
- `visualize_semantic_json(user=None, dataset="main_dataset", *, full=False, query=None, seed_node_ids=None, recall_result=None, neighborhood_depth=2, neighborhood_seed_top_k=10, max_nodes=500) -> dict` (async) — semantic positions and clusters for the same subgraph when given the same dataset/seed arguments as `visualize_graph_json`; the heavier embedding + PCA call. `[AST:cognee/api/v1/visualize/visualize.py:L317]`
- `visualize_multi_user_graph(user_dataset_pairs, destination_file_path=None) -> Any` (async) — HTML visualization combining the graphs of a list of `(User, Dataset)` tuples. `[AST:cognee/api/v1/visualize/visualize.py:L611]`

### Memory provenance visualization and schema inventory

#### `cognee.get_schema_inventory(...)` — summarize the graph by semantic type

```python
async def get_schema_inventory(
    dataset: str | UUID | None = None,
    samples_per_type: int = 5,
    sort: str = "count",
) -> list[dict[str, Any]]
```

Returns one dict per semantic type with `type`, `count`, `samples`, `sample_size` and `relationships` (each `{"to_type", "relation", "count"}`, incoming relations prefixed with `←`). An `Entity` node's type is resolved through its `is_a` edge to the `EntityType` name. `sort="count"` orders by descending count, `"none"` keeps discovery order; any other value, or a negative `samples_per_type`, raises `ValueError`. Only a UUID `dataset` scopes the graph databases; a dataset name skips scoping. `[AST:cognee/api/v1/visualize/get_schema_inventory.py:L77]` · `[SRC:cognee/api/v1/visualize/get_schema_inventory.py:L8-L11]` · `[SRC:cognee/api/v1/visualize/get_schema_inventory.py:L82-L101]` · `[SRC:cognee/api/v1/visualize/get_schema_inventory.py:L118-L119]` · `[SRC:cognee/api/v1/visualize/get_schema_inventory.py:L171]`

#### `cognee.get_memory_provenance_graph(...)` / `cognee.visualize_memory_provenance(...)`

```python
async def get_memory_provenance_graph(
    include_memory: bool = False,
    scope_tenant_ids: list[Any] | None = None,
    scope_user_ids: list[Any] | None = None,
    scope_dataset_ids: list[Any] | None = None,
) -> tuple[list[Node], list[EdgeData]]

async def visualize_memory_provenance(
    destination_file_path: str | None = None,
    include_memory: bool = False,
    scope_tenant_ids: list[Any] | None = None,
    scope_user_ids: list[Any] | None = None,
    scope_dataset_ids: list[Any] | None = None,
) -> str
```

Projects the relational actor/ownership/session metadata (Tenant → User → Agent → Dataset → Data/file, plus agent access and agent-written sessions) into a `(nodes, edges)` graph in the `get_graph_data()` shape. It reads only the relational store, so it needs no graph backend and no LLM; `include_memory=True` folds in the extracted entities/relationships from the relational `nodes`/`edges` tables. `[SRC:cognee/api/v1/visualize/memory_provenance.py:L1-L13]` `visualize_memory_provenance` renders the same graph through `cognee_network_visualization` and returns the HTML. `[SRC:cognee/api/v1/visualize/memory_provenance.py:L867-L873]`

**Multi-tenant warning:** with no scope the read is global (the single-user OSS default). Multi-tenant deployments must pass `scope_tenant_ids` (or `scope_user_ids` without a tenant context), and `scope_dataset_ids` for callers who do not administer the tenant, to avoid leaking other tenants' and members' data. `[SRC:cognee/api/v1/visualize/memory_provenance.py:L656-L672]`

Provenance: `[AST:cognee/api/v1/visualize/memory_provenance.py:L645]` · `[AST:cognee/api/v1/visualize/memory_provenance.py:L848]`

### Pruning — `cognee.prune`

```python
await cognee.prune.prune_data()                                # wipes user data
await cognee.prune.prune_system(graph=True, vector=True,       # wipes backing stores
                                metadata=False, cache=True)
```

Use before running isolated tests or between example runs. With the default `metadata=False` and access control off, `prune_system` re-raises `SharedDatabasePruneError` when PGVector shares the relational database; the vector prune runs before the graph prune, so nothing is deleted when it refuses. Pass `metadata=True` to skip the error. `[SRC:cognee/modules/data/deletion/prune_system.py:L73-L93]` · `[AST:cognee/api/v1/prune/prune.py:L5]`

### Sessions — `cognee.session`

`cognee.session` is a `types.SimpleNamespace` defined in `cognee/api/v1/session/__init__.py`, exposing four async functions; call `cognee.session.<fn>(...)`, because `import cognee.session` and `from cognee.session import ...` do not work. The same functions are importable from `cognee.api.v1.session`. `[SRC:cognee/api/v1/session/__init__.py:L8-L23]`

- `get_session(session_id: str | None = None, last_n: int | None = None, user: User | None = None) -> list[SessionQAEntry]` — load recent Q&A turns for a session. `session_id=None` resolves to the per-dataset default session (the active dataset, or `main_dataset` for a bare call) and raises `SessionPreconditionError` when no `main_dataset` exists; only the literal `"default_session"` still reads the legacy global session. `[AST:cognee/api/v1/session/session.py:L65]` · `[SRC:cognee/api/v1/session/session.py:L72-L88]`
- `add_feedback(session_id: str, qa_id: str, feedback_text: str | None = None, feedback_score: int | None = None, user: User | None = None) -> bool` — attach feedback to a cached Q&A entry. `[AST:cognee/api/v1/session/session.py:L113]`
- `delete_feedback(session_id: str, qa_id: str, user: User | None = None) -> bool` — clear feedback on a Q&A entry. `[AST:cognee/api/v1/session/session.py:L147]`
- `distill_session(session_id: str, dataset: str | UUID, user: User | None = None) -> DistillationResult` — distill one finished session's distillable learnings into its dataset's knowledge graph. A per-(session, dataset) watermark records what a completed run covered, so a re-run with nothing new returns status `"no_new_entries"` with zero LLM calls; failed curator/writer LLM calls raise `DistillationCallsFailedError` and leave the watermark untouched. `DistillationResult` carries `session_id`, `dataset_id`, `status` (`completed`, `no_gated_entries`, `no_new_entries`, `no_proposed_lessons`, `no_accepted_lessons`) and `documents`. `[SRC:cognee/modules/session_distillation/distill.py:L471-L481]` · `[SRC:cognee/modules/session_distillation/distill.py:L520]` · `[SRC:cognee/modules/session_distillation/models.py:L94-L106]`

`get_session`, `add_feedback` and `delete_feedback` resolve the user via an internal `_resolve_user` that prefers an explicit `user`, falls back to the session context-var, then to `get_default_user()`. Any of those failing raises `CogneeValidationError(name="SessionPreconditionError")` with an actionable message. `[SRC:cognee/api/v1/session/session.py:L17-L38]` They do not catch SessionManager errors: an unreachable cache or misconfigured backend raises, and the feedback helpers return `False` only when the QA entry is missing or caching is disabled. `[SRC:cognee/api/v1/session/session.py:L129-L132]` · `[SRC:cognee/api/v1/session/session.py:L162-L165]` · `[SRC:cognee/api/v1/session/session.py:L138]`

### Migrations — `cognee.run_migrations`

```python
async def run_migrations()  # shim has no return annotation; returns the orchestrator's list[str]
```

`cognee.run_migrations()` is the top-level async export `[SRC:cognee/__init__.py:L71]`, a lazy shim to `cognee.modules.migrations.startup.run_migrations` `[AST:cognee/run_migrations.py:L18]`. It runs all migrations under one global migration lock: the relational schema first (for an existing database, Alembic in a worker thread, not a subprocess; a fresh database is built from the migration chain), then the graph and vector revision chains. `[SRC:cognee/modules/migrations/startup.py:L310-L324]` · `[SRC:cognee/modules/migrations/startup.py:L177-L184]` It runs once per process (a failed run is retried on the next call) and returns the ids of the databases whose migration failed — an empty list means everything is at head. A relational failure raises `MigrationError`. `COGNEE_ALEMBIC_PATH` overrides the Alembic script location, and `ENABLE_AUTO_MIGRATIONS=false` turns the call into a logged no-op that returns `[]`. `[SRC:cognee/modules/migrations/startup.py:L386]` · `[SRC:cognee/modules/migrations/startup.py:L400-L440]` · `[SRC:cognee/modules/migrations/startup.py:L143-L146]` `add`, `cognify`, `remember`, `memify` and `improve` run it automatically before writing and abort the write if a database they target failed. `[SRC:cognee/api/v1/add/add.py:L257]` · `[SRC:cognee/api/v1/cognify/cognify.py:L400]` · `[SRC:cognee/api/v1/remember/remember.py:L1429]` · `[SRC:cognee/modules/memify/memify.py:L111]` · `[SRC:cognee/api/v1/improve/improve.py:L430]`

`cognee.run_startup_migrations` no longer exists at v1.6.2 — use `cognee.run_migrations()`. `[SRC:cognee/__init__.py:L70-L71]` The relational stage alone is available as `from cognee.run_migrations import run_relational_migrations`. `[SRC:cognee/run_migrations.py:L11-L15]`

### Agents — `cognee.agents`

Namespace class with static async methods for creating and managing agents (each agent is a user with its own API key) and their connections. Every method defaults `user` to the default user. `[AST:cognee/api/v1/agents/agents.py:L40]`

| Method | Signature | Purpose |
|---|---|---|
| `create` | `(name: str, datasets: list[str \| UUID] \| None = None, user=None) -> dict` | Mint an agent user and API key, then grant it read + write on each dataset (name or UUID). Every dataset is authorized for the caller first: an unknown name raises `ValueError`, an unreadable one `PermissionDeniedError`. Returns `{agent_id, agent_email, agent_api_key}`. |
| `list` | `(user=None) -> list[dict]` | The caller's agents as `{agent_id, agent_email, api_key_label}` |
| `get` | `(agent_id: str \| UUID, user=None) -> dict` | One agent; `ValueError` when not found, `PermissionDeniedError` when not authorized |
| `delete` | `(agent_id: str \| UUID, user=None) -> None` | Delete an agent; same errors as `get` |
| `register` | `(agent_session_name: str, user=None, type="api", memory_mode="unknown", session_id=None, dataset_ids=None, dataset_names=None, source="api", origin_function=None, metadata=None) -> dict` | Register an agent connection. The caller needs read on every listed dataset (`PermissionDeniedError`). `memory_mode` is one of `session`, `cognee`, `hybrid`, `none`, `unknown`; `source` one of `agent_memory`, `session_trace`, `serve`, `api_key`, `mcp`, `api`. |
| `unregister` | `(agent_session_name: str, user=None) -> int` | Deactivate a connection; returns the remaining in-process active-connection count |
| `list_connections` | `(user=None, agent_id=None, range_key="30d", status_filter=None, include_sources=True, active_only=True, limit=50, offset=0) -> dict` | Paginated connections (`range_key` one of `24h`, `7d`, `30d`, `all`); connections bound to neither a user nor a dataset are filtered out |
| `get_connection` | `(agent_id: str \| UUID, user=None, agent_session_name=None) -> dict \| None` | Connection detail, or None |

Provenance: `[SRC:cognee/api/v1/agents/agents.py:L63-L272]` · `[SRC:cognee/modules/agents/models.py:L31-L33]` · `[SRC:cognee/modules/agents/operations.py:L36]` · `[SRC:cognee/modules/agents/agent_mode.py:L110-L119]`

### Memory export, push, validation and reports

#### `cognee.export(...)` — export a dataset's knowledge graph

```python
@overload
async def export(dataset: str | UUID = DEFAULT_DATASET_NAME, format: Literal["pydantic"] = "pydantic",
                 destination: str | Path | None = None, user=None,
                 link_relations: bool = False, include_permissions: bool = False) -> GraphSnapshot: ...
@overload
async def export(dataset: str | UUID, format: Literal["cogx", "json", "graphml", "cypher"],
                 destination: str | Path | None = None, user=None,
                 link_relations: bool = False, include_permissions: bool = False) -> ExportResult: ...
# (a third overload takes format= as keyword-only with the default dataset)

async def export(
    dataset: str | UUID = DEFAULT_DATASET_NAME,  # "main_dataset"
    format: str = "pydantic",
    destination: str | Path | None = None,
    user=None,
    link_relations: bool = False,
    include_permissions: bool = False,
) -> ExportResult | GraphSnapshot
```

Requires read permission on the dataset; `user` defaults to the default user. `format="pydantic"` returns a `GraphSnapshot` of typed DataPoint instances (losslessly serializable; `destination` also saves it as JSON), and `link_relations=True` re-attaches edges as object references on declared relation fields. `"cogx"` writes a re-importable archive directory (default `<dataset>_cogx`); `"json"`, `"graphml"` and `"cypher"` write a file (default `<dataset>_export.<ext>` in the working directory). Every format other than `"pydantic"` returns an `ExportResult`. `[SRC:cognee/api/v1/export/export.py:L57-L79]` · `[SRC:cognee/modules/migration/export.py:L263-L265]` `include_permissions=True` (cogx only) also writes the owner and ACL grants with user credentials into `permissions.json`, so the archive contains password hashes — treat it as a secret. An unknown format raises `ValueError`; a missing or unreadable dataset raises `DatasetNotFoundError`. `[SRC:cognee/modules/migration/export.py:L208-L234]` · `[AST:cognee/api/v1/export/export.py:L16]` · `[SRC:cognee/api/v1/export/export.py:L49-L56]`

`ExportResult` is a dataclass with `format`, `destination`, `dataset_name`, `dataset_id`, `num_nodes`, `num_edges`. `[AST:cognee/modules/migration/export.py:L41]`

#### `cognee.push(...)` — upload a dataset's graph to Cognee Cloud

```python
async def push(
    dataset: str | UUID = DEFAULT_DATASET_NAME,  # "main_dataset"
    *,
    target_dataset: str | None = None,
    mode: str = "preserve",
    run_in_background: bool = False,
    url: str | None = None,
    api_key: str | None = None,
    user=None,
) -> PushResult
```

Exports the dataset with `export(format="cogx")`, packs it as a tarball and uploads it to the remote remember endpoint, which imports the graph instead of re-deriving it from raw files. `mode` is `"preserve"` (map the exported graph directly, zero LLM calls), `"hybrid"` (also cognify the raw content) or `"re-derive"` (rebuild from raw content); any other value raises `ValueError`. `target_dataset` defaults to the local dataset name. With `run_in_background=True` the call returns once the upload completes; poll the returned `pipeline_run_id`. `[SRC:cognee/api/v1/push/push.py:L106-L137]` The connection comes from `url`/`api_key`, else the live `serve()` connection, else `COGNEE_SERVICE_URL`/`COGNEE_API_KEY`, else the credentials saved by `cognee-cli serve`; with none it raises `RuntimeError`. `[SRC:cognee/api/v1/push/push.py:L47-L76]` It raises `ValueError` when the dataset exports 0 nodes and `RuntimeError` when the remote server did not run a COGX import (an older server version). `[SRC:cognee/api/v1/push/push.py:L153-L158]` · `[SRC:cognee/api/v1/push/push.py:L79-L93]` · `[AST:cognee/api/v1/push/push.py:L96]`

`PushResult` is a dataclass with `status`, `dataset_name`, `target_dataset`, `num_nodes`, `num_edges`, `remote_response` and `pipeline_run_id` (None unless the remote reports one). `[AST:cognee/api/v1/push/push.py:L26]`

#### `cognee.validate(...)` — graph/vector consistency check

```python
async def validate(
    dataset: str | list[str] | None = DEFAULT_DATASET_NAME,  # "main_dataset"
    user: User | None = None,
) -> ValidationReport
```

Read-only cross-check of a dataset's graph and vector stores through the standard adapter interfaces, so it works against every graph/vector backend. It reports orphaned edges (an endpoint id missing from the node set), identity-id mismatches (an `Entity`/`EntityType` node whose id differs from the id its identity fields derive) and missing vector entries (an `Entity`/`DocumentChunk` node with no point in its `{type}_{field}` collection). `[SRC:cognee/api/v1/validate/validate.py:L11-L30]` The first accessible dataset determines which graph is read; if any named dataset is not found or not readable it raises `DatasetNotFoundError`. `[SRC:cognee/api/v1/validate/validate.py:L220-L227]` · `[AST:cognee/api/v1/validate/validate.py:L198]`

- `ValidationReport` — `status: ValidationStatus`, `summary: dict` (`graph_nodes`, `graph_edges`, `node_type_distribution`), `issues: list[ValidationIssue]`. `[AST:cognee/api/v1/validate/validate.py:L105]`
- `ValidationIssue` — `severity` (`error` or `warning`), `type` (`orphaned_edge`, `identity_id_mismatch`, `missing_vector_entry`), `detail: str`. `[AST:cognee/api/v1/validate/validate.py:L99]`
- `ValidationStatus` — `str` enum: `HEALTHY`, `DEGRADED` (warnings only), `UNHEALTHY` (any error). `[AST:cognee/api/v1/validate/validate.py:L93]` · `[SRC:cognee/api/v1/validate/validate.py:L248-L255]`

#### `cognee.report(...)` — graph insight report

```python
async def report(
    datasets: str | list[str] | None = DEFAULT_DATASET_NAME,  # "main_dataset"
    output_path: str | None = "graph_report.md",
    top_n: int = 10,
    user: User | None = None,
) -> str
```

Generates a Markdown Graph Insight Report — hub ("god") nodes, surprising cross-node_set connections, edge provenance and LLM-suggested questions — reading only via `get_graph_data()`, with no storage changes. The first accessible dataset determines which graph is read; `top_n` sets how many hub nodes and connections to surface. Writes the report to `output_path` (pass None to skip writing) and returns the Markdown string. `[AST:cognee/api/v1/report/report.py:L13]` · `[SRC:cognee/api/v1/report/report.py:L19-L34]`

### Tool connections — `cognee.tools`

`cognee.tools` is the module `cognee/api/v1/tools/tools.py` `[SRC:cognee/__init__.py:L113]` · `[SRC:cognee/api/v1/tools/__init__.py:L1]`. It manages authorized external SQL databases that become usable via `cognee.recall(query, scope=["tools"])` once `TOOL_CALLS_ENABLED=true`. `[SRC:cognee/api/v1/tools/tools.py:L1-L14]` All functions are async and default `user` to the default user.

| Function | Signature | Purpose |
|---|---|---|
| `register_sql_connection` | `(name: str, connection_string: str, *, provider=None, allowed_tables=None, max_rows=None, description=None, allow_writes: bool = False, user=None) -> dict` | Register (or replace) a connection. The connection string is encrypted at rest and never returned; use a SELECT-only role. `allow_writes=True` opts into approval-gated write-back. `[AST:cognee/api/v1/tools/tools.py:L27]` |
| `list_sql_connections` | `(user=None) -> list[dict]` | The user's connections plus deployment-level ones, without secrets `[AST:cognee/api/v1/tools/tools.py:L65]` |
| `remove_sql_connection` | `(name: str, user=None) -> bool` | Remove a connection; `False` when nothing matched `[AST:cognee/api/v1/tools/tools.py:L73]` |
| `propose_sql_write` | `(connection: str, instruction: str, *, evidence=None, user=None) -> dict` | Draft a correction UPDATE as a reviewable proposal with a dry-run affected-row estimate; nothing executes. Needs `TOOL_WRITE_CALLS_ENABLED=true` and an `allow_writes=True` connection. `[AST:cognee/api/v1/tools/tools.py:L81]` |
| `propose_corrections` | `(connection: str, *, limit: int = 10, user=None) -> list[dict]` | Draft one proposal per graph `contradicts` edge that is correctable in the database `[AST:cognee/api/v1/tools/tools.py:L101]` |
| `list_write_proposals` | `(status=None, user=None) -> list[dict]` | The user's write proposals, optionally filtered by status `[AST:cognee/api/v1/tools/tools.py:L119]` |
| `apply_write_proposal` | `(proposal_id, user=None) -> dict` | The only path that commits a write; rolls back (and marks the proposal failed) when the affected rowcount exceeds the cap or no longer matches the dry-run estimate `[AST:cognee/api/v1/tools/tools.py:L129]` |
| `reject_write_proposal` | `(proposal_id, user=None) -> dict` | Mark a proposal rejected so it can never be applied `[AST:cognee/api/v1/tools/tools.py:L146]` |

### Version — `cognee.get_cognee_version`

```python
def get_cognee_version() -> str
```

Returns the `version` line of a nearby `pyproject.toml` with `-local` appended (a source checkout), else the installed `cognee` package version, else `"unknown"`. `cognee.__version__` is set from it at import time. `[AST:cognee/version.py:L7]` · `[SRC:cognee/version.py:L10-L26]` · `[SRC:cognee/__init__.py:L18]` · `[SRC:cognee/__init__.py:L22]`

## Full Type Definitions

### `cognee.exceptions` — error hierarchy

```python
class CogneeApiError(Exception):
    def __init__(self, message="Service is unavailable.", name="Cognee",
                 status_code=500, log=True, log_level="ERROR",
                 remediation: str | None = None): ...

class CogneeSystemError(CogneeApiError):          # status_code=500, name="CogneeSystemError"
class CogneeValidationError(CogneeApiError):      # status_code=422, name="CogneeValidationError"
class CogneeConfigurationError(CogneeApiError):   # status_code=500, name="CogneeConfigurationError"
class CogneeTransientError(CogneeApiError):       # status_code=503, name="CogneeTransientError"
```

Every subclass auto-logs on construction (level controlled by `log_level`) with the format `"%s raised (Status code: %s): %s"`. `__str__` formats as `"{name}: {message} (Status code: {status_code})"` and appends `" Fix: <remediation>"` (`REMEDIATION_MARKER`) when `remediation` is set. Imports `status` from `fastapi` so it pulls in the fastapi dependency transitively. `[AST:cognee/exceptions/exceptions.py:L10]` · `[SRC:cognee/exceptions/exceptions.py:L28-L66]` `cognee.exceptions` also exports `REMEDIATION_MARKER`, `find_remediation(message)` and `remediation_for(error)`. `[SRC:cognee/exceptions/__init__.py:L15]` · `[SRC:cognee/exceptions/remediation.py:L52]` · `[AST:cognee/exceptions/remediation.py:L131]` · `[AST:cognee/exceptions/remediation.py:L146]`

### `cognee.pipelines.Task` — detailed

Class attributes:

- `executable` — the wrapped callable (function / coroutine / generator / async-generator).
- `task_config: dict[str, Any] = {"batch_size": 1}` — default batch size 1 unless overridden at construction.
- `default_params: dict[str, Any]` — captured `*args` and `**kwargs` from construction.
- `task_type: str` — one of `"Function"`, `"Coroutine"`, `"Generator"`, `"Async Generator"`.
- `enriches: bool = False` — a task that mutates its input in place; when it returns None the runner passes the input through. `needs_llm: bool = True` — see the `Task` bullet above. `accepts_ctx` — whether the executable takes a `ctx` parameter (gets the `PipelineContext`). `[SRC:cognee/modules/pipelines/tasks/task.py:L200-L206]` · `[SRC:cognee/modules/pipelines/tasks/task.py:L246-L251]`

Methods:

- `run(*args, **kwargs)` — calls the executable with combined args/kwargs from construction and invocation.
- `with_config(**overrides) -> Task` — a new `Task` with overridden `batch_size`/`enriches`/`needs_llm`/kwargs. `[SRC:cognee/modules/pipelines/tasks/task.py:L256-L274]`
- `execute_async_generator` / `execute_generator` / `execute_coroutine` / `execute_function` — each `(self, args, kwargs, batch_size)`. `[SRC:cognee/modules/pipelines/tasks/task.py:L283-L334]`
- `execute(args, kwargs, next_batch_size=None)` — async generator that yields results; it hands `next_batch_size` to the `execute_*` method as its local `batch_size`, so a task's `batch_size` batches the **previous** task's output. `[SRC:cognee/modules/pipelines/tasks/task.py:L336-L341]` · `[SRC:cognee/modules/pipelines/__init__.py:L48-L51]`

Construction rejects unsupported callables with `ValueError(f"Unsupported task type: {executable}")`.

`@task_summary("Classified {n} document(s)")` decorator sets `func.__task_summary__` for human-readable task run summaries. `[AST:cognee/modules/pipelines/tasks/task.py:L169]` · `[AST:cognee/modules/pipelines/tasks/task.py:L188]`

### `PipelineRunInfo` — pipeline status

Imported from `cognee.modules.pipelines.models.PipelineRunInfo`. Subclasses yielded by `run_tasks` / `run_pipeline`:

- `PipelineRunStarted(pipeline_run_id, dataset_id, dataset_name, payload)`
- `PipelineRunCompleted(pipeline_run_id, dataset_id, dataset_name, data_ingestion_info)`
- `PipelineRunErrored(pipeline_run_id, payload, dataset_id, dataset_name, data_ingestion_info, error_class, error_message)` — `error_message` is PII-scrubbed. `payload` and the error fields carry the first failing item's root exception, not the `PipelineRunFailedError` wrapper. `[SRC:cognee/modules/pipelines/models/PipelineRunInfo.py:L42-L50]` · `[SRC:cognee/modules/pipelines/operations/run_tasks.py:L316-L346]`

`run_tasks` raises `PipelineRunFailedError` internally if any data item fails, then yields `PipelineRunErrored`; that per-item wrapper is not re-raised, while any other exception is re-raised after the errored status is yielded. `[SRC:cognee/modules/pipelines/operations/run_tasks.py:L250-L258]` · `[SRC:cognee/modules/pipelines/operations/run_tasks.py:L348-L350]` `get_errored_run_info(result)` in the same module returns the first `PipelineRunErrored` in a `cognify()`/`run_pipeline` result, or None. `[AST:cognee/modules/pipelines/models/PipelineRunInfo.py:L62]` · `[AST:cognee/modules/pipelines/models/PipelineRunInfo.py:L9]`

### Memory entry types — `cognee.MemoryEntry`

Typed payloads for `cognee.remember()`, each with a literal `type` discriminator. `MemoryEntry` is the union `QAEntry | TraceEntry | FeedbackEntry | SkillRunEntry`; `SkillRunEntry` is not a top-level `cognee` name (import it from `cognee.memory`). `[SRC:cognee/memory/entries.py:L129]` · `[SRC:cognee/__init__.py:L90]`

- `QAEntry` — `type="qa"`, `question: str`, `answer: str`, `context: str = ""`, `feedback_text: str | None`, `feedback_score: int | None`, `used_graph_element_ids: dict | None`. A Q&A turn for the session cache. `[AST:cognee/memory/entries.py:L24]`
- `TraceEntry` — `type="trace"`, `origin_function: str`, `status: "success" | "error" = "success"`, `method_params: dict | None`, `method_return_value: Any | None`, `memory_query: str = ""`, `memory_context: str = ""`, `error_message: str = ""`, `generate_feedback_with_llm: bool = False`. One agent trace step. `[AST:cognee/memory/entries.py:L40]`
- `FeedbackEntry` — `type="feedback"`, `qa_id: str` (the `entry_id` of a previous QA remember call), `feedback_text: str | None`, `feedback_score: int | None`. Feedback on an existing QA entry. `[AST:cognee/memory/entries.py:L62]`

### Session lifecycle models — `cognee.SessionRecord` and `cognee.SessionModelUsage`

SQLAlchemy models exported at the top level. `[SRC:cognee/__init__.py:L116]`

- `SessionRecord` (table `session_records`) — one row per `(session_id, user_id)` with `dataset_id`, `agent_id`, `status` (stored `running`/`completed`/`failed`; `abandoned` is inferred at read time from `last_activity_at`), `started_at`, `last_activity_at`, `ended_at`, `tokens_in`, `tokens_out`, `cost_usd`, `error_count`, `last_model`, and `to_dict()`. `[AST:cognee/modules/session_lifecycle/models.py:L10]`
- `SessionModelUsage` (table `session_model_usage`) — per-`(session_id, user_id, model)` `tokens_in`, `tokens_out`, `cost_usd`, `updated_at`, and `to_dict()`. `[AST:cognee/modules/session_lifecycle/models.py:L96]`

## Full Integration Patterns

### Co-import patterns (detected in source)

- **`Task` + `run_pipeline`** — the standard custom-pipeline pair, imported from `cognee.modules.pipelines` (or `Task` from `cognee.modules.pipelines.tasks.task`). Seen in `cognee/api/v1/add/add.py:L17`, `cognee/api/v1/cognify/cognify.py:L37` / `L39`, `cognee/modules/memify/memify.py:L14` / `L19`, and `cognee/modules/run_custom_pipeline/run_custom_pipeline.py:L5` / `L7`.
- **`SearchType` + `search`** — co-imported whenever search is called with a non-default mode: `from cognee import SearchType` + `cognee.search(...)` (the function is also importable as `from cognee.api.v1.search import search`). The `cognify()` docstring example uses this pair. `[SRC:cognee/api/v1/cognify/cognify.py:L256-L268]`
- **`DataPoint` + `add_data_points`** — paired for direct graph insertion without cognify: `from cognee.infrastructure.engine import DataPoint` + `from cognee.tasks.storage import add_data_points`. See `[EXT:https://docs.cognee.ai/guides/custom-data-models]`. The `cognee.low_level` shortcut gives you `DataPoint`, `Edge` and `setup` in a single import. `[SRC:cognee/low_level.py:L1-L3]`
- **`LLMGateway.acreate_structured_output` + custom Task** — pattern for LLM-backed extraction tasks: `from cognee.infrastructure.llm.LLMGateway import LLMGateway; await LLMGateway.acreate_structured_output(text, system_prompt, PydanticModel)`. Backend is controlled by the `STRUCTURED_OUTPUT_FRAMEWORK` env var: default `litellm_native` (plain litellm with schema-native `response_format` or a prompted-JSON fallback, no instructor); set `instructor` or `baml` to opt back. `[SRC:cognee/infrastructure/llm/config.py:L101-L107]` · `[SRC:cognee/infrastructure/llm/LLMGateway.py:L113-L118]`

### Default backends (from `pyproject.toml`)

- **LLM:** `litellm>=1.83.7,<1.97.0` + `openai>=1.80.1` + `instructor>=1.9.1,<1.15.3`. Provider routed via `cognee.config.set_llm_provider(...)`. `[SRC:pyproject.toml:L23]` · `[SRC:pyproject.toml:L45-L46]`
- **Vector store:** `lancedb>=0.24.3,<1.0.0` + `pylance`. Alternatives via `postgres` (pgvector), `neptune` and `turso` extras. `[SRC:pyproject.toml:L60]` · `[SRC:pyproject.toml:L79]` · `[SRC:pyproject.toml:L141-L152]`
- **Graph store:** `ladybug==0.19.0` (pinned; `ladybug>=0.17.0,<0.18` on macOS 13/14) + `networkx>=3.4.2,<4`. Alternatives via the `neo4j` or `neptune` extras. `[SRC:pyproject.toml:L97-L100]` · `[SRC:pyproject.toml:L140-L141]`
- **Embeddings:** `fastembed<=0.8.0` is a core dependency. With no LLM key and no `EMBEDDING_*` settings, embeddings use the local fastembed model `BAAI/bge-small-en-v1.5`, and `KeylessEmbedderNotInstalledError` is raised if fastembed is missing. `[SRC:pyproject.toml:L70]` · `[SRC:cognee/infrastructure/databases/vector/embeddings/config.py:L28-L29]` · `[SRC:cognee/infrastructure/databases/vector/embeddings/config.py:L216-L222]`
- **Also core:** `dlt[sqlalchemy]>=1.9.0,<2` (database, CSV and Google Drive/Gmail ingestion) and `enola-cli==0.4.26` (the deterministic code-graph route); the `fastembed`, `dlt` and `codegraph` extras are empty and kept only so those install names still work. `[SRC:pyproject.toml:L114-L116]` · `[SRC:pyproject.toml:L137-L138]` · `[SRC:pyproject.toml:L177-L178]` · `[SRC:pyproject.toml:L191-L192]`
- **Relational:** `sqlalchemy>=2.0.39` + `aiosqlite>=0.20.0` + `alembic>=1.13.3`. PostgreSQL via the `postgres` extra. `[SRC:pyproject.toml:L33-L34]` · `[SRC:pyproject.toml:L62]`
- **API server:** `fastapi>=0.116.2` + `uvicorn>=0.34.0` + `gunicorn` + `websockets`. Starts with `uv run python -m cognee.api.client`. `[SRC:AGENTS.md:L51]`
- **Auth:** `fastapi-users[sqlalchemy]>=15.0.2`.
- **Observability:** `structlog>=25.2.0`, plus OpenTelemetry-compatible tracing through `cognee.enable_tracing` (the `tracing` extra). `[SRC:pyproject.toml:L227-L232]`
- **Scraping (extra):** `tavily-python`, `beautifulsoup4`, `playwright`, `lxml`, `protego`, `APScheduler`. `[SRC:pyproject.toml:L124-L135]`
- **GLiNER (extra):** `gliner2[local]`, `torch`, `protobuf`, `sentencepiece` — the local demo extractor. `[SRC:pyproject.toml:L248]`

Provenance: `[SRC:pyproject.toml:L22]` · `[SRC:AGENTS.md:L51]`

### Related out-of-scope interfaces

- `cognee-mcp/` — Model Context Protocol server exposing cognee tools over stdio/SSE/HTTP.
- `cognee-frontend/` — Next.js UI that the `cognee.start_ui` function can launch.
- `cognee-cli` — terminal CLI (`add/cognify/search/-ui`).
- `cognee.api.client:app` — FastAPI application for HTTP REST access.
- Top-level bootstrap names not covered here: `load_env_file` and `describe_resolution` `[SRC:cognee/__init__.py:L27]`, `setup_logging` `[SRC:cognee/__init__.py:L32]`, `logger` `[SRC:cognee/__init__.py:L34]`, `wait_for_background_tasks` `[SRC:cognee/__init__.py:L94]`, the `migration` module `[SRC:cognee/__init__.py:L98]`.

This skill only covers the Python API — use the upstream docs for those other surfaces.
