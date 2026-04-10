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

1. **LLM API key**: `LLM_API_KEY` env var (required for content processing, graph extraction, and LLM-backed search types).
2. **Database setup**: relational and vector databases must be reachable.
3. **User**: Cognee uses a default user (`default_user@example.com`) created automatically on first use when `user` is None.

Full env matrix: `[SRC:cognee/api/v1/add/add.py:L166]`

## cognee.add

### Signature

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
)
```

Provenance: `[AST:cognee/api/v1/add/add.py:L21]`

### Parameters

| Param | Type | Default | Required | Description |
|---|---|---|---|---|
| `data` | Union (many) | — | yes | Content to ingest. See "Accepted data types" below. |
| `dataset_name` | str | `"main_dataset"` | no | Logical dataset for organization. |
| `user` | User | None | no | Auth context. Uses default user if None. |
| `node_set` | List[str] | None | no | Tags that become first-class graph nodes after cognify — scope memory by customer/workflow/topic. |
| `vector_db_config` | dict | None | no | Per-call vector DB override. |
| `graph_db_config` | dict | None | no | Per-call graph DB override. |
| `dataset_id` | UUID | None | no | Specific dataset UUID (overrides `dataset_name`). |
| `preferred_loaders` | list[str]/dict | None | no | Loaders to prefer per file type. |
| `incremental_loading` | bool | True | no | Only process new or modified data (uses content hashing). |
| `data_per_batch` | int | 20 | no | Data items per parallel batch. |
| `importance_weight` | float | 0.5 | no | Weighting applied when storing ingested items. |
| `**kwargs` | — | — | — | Passed through to `resolve_dlt_sources` for DLT-specific config (e.g., `extraction_rules`, `tavily_config`, `soup_crawler_config` — documented in docstring only). |

### Accepted data types

- **Text strings** — raw content (any string not starting with `/` or `file://`).
- **Absolute file paths** — e.g., `"/path/to/document.pdf"`.
- **File URLs** — `"file:///absolute/path"` or `"file://relative/path"`.
- **S3 paths** — `"s3://bucket-name/path/to/file.pdf"`.
- **HTTP(S) URLs** — scraped via BeautifulSoup (extraction rules) or Tavily (API key required via `TAVILY_API_KEY`).
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

### Return value

`PipelineRunInfo | None` — includes `pipeline_run_id`, `dataset_id`, status, timestamps, and any errors from the ingestion pipeline. `None` only if the pipeline loop does not yield (should not happen in practice).

### Internal flow

1. Setup databases (`setup()`)
2. Resolve authorized dataset for the user (`resolve_authorized_user_dataset`)
3. Expand DLT resources into standard DataItems (`resolve_dlt_sources`)
4. Reset pipeline status for `add_pipeline` and `cognify_pipeline`
5. Run the `add_pipeline` with tasks: `resolve_data_directories` → `ingest_data`

Provenance: `[AST:cognee/api/v1/add/add.py:L180]`

## cognee.cognify

### Signature

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
)
```

Provenance: `[AST:cognee/api/v1/cognify/cognify.py:L44]`

### Key parameters

| Param | Type | Default | Description |
|---|---|---|---|
| `datasets` | str / list[str] / list[UUID] / None | None | Datasets to process. `None` → all datasets the user can access. |
| `graph_model` | Pydantic BaseModel | `KnowledgeGraph` | Custom graph schema (domain-specific models, e.g., `ScientificPaper`). |
| `chunker` | Class | `TextChunker` | Chunking strategy. `TextChunker` is paragraph-based (default). `LangchainChunker` is recursive character splitter. |
| `chunk_size` | int | None | Max tokens per chunk. Auto-calculated from LLM limits if None (roughly `min(embedding_max_completion_tokens, llm_max_completion_tokens // 2)`). |
| `chunks_per_batch` | int | None (→ 100) | Chunks per processing batch. |
| `custom_prompt` | str | None | Overrides default extraction prompts. |
| `temporal_cognify` | bool | False | Time-aware extraction — builds event chains with timestamps, pairs with `SearchType.TEMPORAL`. |
| `run_in_background` | bool | False | Async execution mode. Recommended for datasets > 100MB. |
| `data_per_batch` | int | 20 | Items per batch passed to the pipeline. |

### Default tasks

1. `classify_documents`
2. `extract_chunks_from_documents(max_chunk_size, chunker)`
3. `extract_graph_from_data(graph_model, config, custom_prompt, task_config={batch_size: chunks_per_batch})`
4. `summarize_text(task_config={batch_size: chunks_per_batch})`
5. `add_data_points(embed_triplets, task_config={batch_size: chunks_per_batch})`
6. `extract_dlt_fk_edges`

Provenance: `[AST:cognee/api/v1/cognify/cognify.py:L269]`

### Temporal pipeline (when `temporal_cognify=True`)

Uses a different task list:

1. `classify_documents`
2. `extract_chunks_from_documents`
3. `extract_events_and_timestamps(task_config={batch_size: chunks_per_batch})`
4. `extract_knowledge_graph_from_events`
5. `add_data_points(task_config={batch_size: chunks_per_batch})`

Provenance: `[AST:cognee/api/v1/cognify/cognify.py:L334]`

### Ontology config

If `config` is None and the environment has `ontology_file_path`, `ontology_resolver`, and `matching_strategy` set, `cognify` auto-loads `get_ontology_resolver_from_env(**ontology_config.to_dict())`. Otherwise uses `get_default_ontology_resolver()`.

Provenance: `[AST:cognee/api/v1/cognify/cognify.py:L205]`

### Return value

- **Blocking mode**: `dict` mapping `dataset_id → PipelineRunInfo`.
- **Background mode**: `list[PipelineRunInfo]` — track via `pipeline_run_id`.

## cognee.search

### Signature

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

Provenance: `[AST:cognee/api/v1/search/search.py:L27]`

### Key parameters

| Param | Type | Default | Description |
|---|---|---|---|
| `query_text` | str | — | The natural-language question or query. Required. |
| `query_type` | SearchType | GRAPH_COMPLETION | See Key Types in SKILL.md for full list. |
| `datasets` | list[str] / str | None | Dataset names to search. |
| `dataset_ids` | list[UUID] / UUID | None | Same but with UUIDs. Takes precedence over `datasets`. |
| `top_k` | int | 10 | Max results. |
| `node_type` | Type | NodeSet | Graph model to filter on (use with `node_name`). |
| `node_name` | list[str] | None | Names of nodes/node_sets to include. |
| `node_name_filter_operator` | str | `"OR"` | Must be `"OR"` or `"AND"` — otherwise raises `CogneeValidationError`. |
| `only_context` | bool | False | Skip LLM generation — return raw context. |
| `session_id` | str | None | Conversation session id — only honored by `GRAPH_COMPLETION`, `RAG_COMPLETION`, `TRIPLET_COMPLETION`. |
| `wide_search_top_k` | int | 100 | Initial candidate pool before ranking for graph-completion retrievers. |
| `triplet_distance_penalty` | float | 6.5 | Graph retrieval ranking penalty. |
| `feedback_influence` | float | 0.0 | Weight of feedback signals in ranking. |
| `verbose` | bool | False | Return `{text_result, context_result, objects_result}` instead of raw answer. |
| `retriever_specific_config` | dict | None | Per-retriever options (e.g., `response_model` for typed output, `max_iter` for COT, `context_extension_rounds` for context extension). |

### Result shapes by search type

| SearchType | Return shape |
|---|---|
| `GRAPH_COMPLETION`, `RAG_COMPLETION`, `TRIPLET_COMPLETION`, `GRAPH_COMPLETION_COT`, `GRAPH_COMPLETION_CONTEXT_EXTENSION`, `GRAPH_SUMMARY_COMPLETION` | LLM string answers (or dicts when `verbose=True`) |
| `CHUNKS` | list of dicts: `id`, `text`, `chunk_index`, `chunk_size`, `cut_type` |
| `SUMMARIES` | list of dicts: `id`, `text` |
| `CYPHER` | raw graph query results |
| `CODE` | structured code info with context |
| `CHUNKS_LEXICAL` | ranked text chunks (optionally with scores) |
| `FEELING_LUCKY` | auto-selected type's result shape |
| `TEMPORAL` | event-chain results |
| `CODING_RULES` | Rule nodes extracted by memify |

`[EXT:https://docs.cognee.ai/guides/search-basics]`

### ENABLE_BACKEND_ACCESS_CONTROL behavior

- **`=true`**: results wrapped per-dataset with `dataset_id`, `dataset_name`, `search_result` (and `dataset_tenant_id` when available). Multiple datasets searched concurrently via `asyncio.gather()`. Raises `PermissionDeniedError` (or `UnauthorizedDataAccessError`) if the user lacks access to any requested dataset.
- **`=false` (default)**: dataset filters are ignored — all data is searched. Results come back as a plain list; single-dataset searches may be unwrapped one level for backwards compatibility.

`[EXT:https://docs.cognee.ai/guides/search-basics]`

### Error handling

- `CogneeValidationError("Invalid node_name_filter_operator: ...")` — invalid filter operator. `[AST:cognee/api/v1/search/search.py:L201]`
- `CogneeValidationError(name="SearchPreconditionError")` — wraps `DatabaseNotCreatedError` / `UserNotFoundError` with an actionable message telling the caller to initialize via `add` + `cognify` first. `[AST:cognee/api/v1/search/search.py:L210]`
- `DatasetNotFoundError` — no datasets match the requested names for the user.

## cognee.update

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

Internal flow:

1. Resolve user (default user if None).
2. `datasets.delete_data(dataset_id, data_id, user=user)` — removes the old data.
3. `add(data, dataset_id=dataset_id, user=user, node_set=node_set, ...)` — ingest the replacement.
4. `cognify(datasets=[dataset_id], user=user, ...)` — rebuild the subgraph for the updated dataset.
5. Returns the result of the final `cognify` call.

Provenance: `[AST:cognee/api/v1/update/update.py:L12]`

## Environment variables

### Required

- `LLM_API_KEY` — API key for the LLM provider. Used for entity extraction during cognify and for LLM-backed search types (GRAPH_COMPLETION, RAG_COMPLETION, TRIPLET_COMPLETION, etc.).

### Optional LLM

- `LLM_PROVIDER` — `"openai"` (default), `"anthropic"`, `"gemini"`, `"ollama"`, `"mistral"`, `"bedrock"`.
- `LLM_MODEL` — Model identifier (default: `"gpt-5-mini"` per add.py docstring).
- `LLM_RATE_LIMIT_ENABLED` — Enable rate limiting (default: False).
- `LLM_RATE_LIMIT_REQUESTS` — Max requests per interval (default: 60).

### Optional databases

- `VECTOR_DB_PROVIDER` — `"lancedb"` (default), `"chromadb"`, `"pgvector"`.
- `GRAPH_DATABASE_PROVIDER` — `"kuzu"` (default), `"neo4j"`.

### User

- `DEFAULT_USER_EMAIL` — Custom default user email (default: `"default_user@example.com"`).
- `DEFAULT_USER_PASSWORD` — Custom default user password.

### Scraping (when add receives URLs)

- `TAVILY_API_KEY` — enables Tavily as an add-data ingestion method.

### Tracing / observability

- `COGNEE_TRACING_ENABLED` — `"true"` / `"1"` / `"yes"` enables OpenTelemetry tracing at runtime.
- Base config field: `cognee_tracing_enabled`.

### Distributed

- `COGNEE_DISTRIBUTED` — `"true"` switches `run_tasks` to its distributed variant (`run_tasks_distributed`). `[AST:cognee/modules/pipelines/operations/run_tasks.py:L38]`

### Access control

- `ENABLE_BACKEND_ACCESS_CONTROL` — `"true"` enables per-user dataset access filtering and the wrapped result shape described above.

### Structured output (custom pipeline authors)

- `STRUCTURED_OUTPUT_FRAMEWORK` — selects BAML or LiteLLM+Instructor for `LLMGateway.acreate_structured_output`. `[EXT:https://docs.cognee.ai/guides/custom-tasks-pipelines]`

Provenance for env-var list: `[SRC:cognee/api/v1/add/add.py:L166]` (Add) and `[SRC:cognee/api/v1/cognify/cognify.py:L193]` (Cognify), plus docs cross-reference.
