# Full API Reference

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
