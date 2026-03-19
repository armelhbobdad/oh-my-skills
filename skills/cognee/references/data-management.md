# Data Management Reference — cognee

## config `[AST:cognee/api/v1/config/config.py:L18]`

Static methods for runtime configuration:

| Method | Purpose |
|--------|---------|
| `set_llm_api_key(key)` | Set LLM API key |
| `set_llm_model(model)` | Set LLM model name |
| `set_llm_provider(provider)` | Set LLM provider (openai/azure/gemini/anthropic/ollama/custom) |
| `system_root_directory(path)` | Set system root (databases, configs) |
| `data_root_directory(path)` | Set data storage root |
| `set_vector_db_provider(provider)` | Set vector store (lancedb/pgvector/qdrant/redis/chromadb) |
| `set_graph_db_provider(provider)` | Set graph DB (kuzu/neo4j/neptune/memgraph) |
| `set_embedding_provider(provider)` | Set embedding provider |
| `monitoring_tool(tool)` | Set monitoring tool |

**T2-past:** Custom LLM endpoint fix for GenericAPIAdapter in `LLM_PROVIDER=custom` path. `[QMD:cognee-temporal:prs.md]`

---

## datasets `[AST:cognee/api/v1/datasets/datasets.py:L26]`

| Method | Signature | Description |
|--------|-----------|-------------|
| `list_datasets` | `async (user=None)` | List all accessible datasets |
| `discover_datasets` | `(directory_path: str)` | List datasets in a directory (sync) |
| `list_data` | `async (dataset_id, user=None)` | List data items in a dataset |
| `get_status` | `async (datasets, user=None)` | Get cognify processing status |
| `delete_data` | `async (dataset_id, data_id, mode, user)` | Delete specific data item |
| `delete_dataset` | `async (dataset_id, user)` | Delete entire dataset |
| `empty_dataset` | `async (dataset_id, user)` | Remove all data from dataset |

---

## prune `[AST:cognee/api/v1/prune/prune.py:L4]`

- `prune.prune_data()` — remove all user data
- `prune.prune_system(graph=True, vector=True, metadata=False, cache=True)` — reset system state

---

## update() `[AST:cognee/api/v1/update/update.py:L13]`

Updates existing data by data_id within a dataset. Internally calls `add()` + `cognify()` after deleting old data.

**T2-past:** Bug: PATCH updates timestamps but GET raw returns old data. `[QMD:cognee-temporal:issues.md]`

---

## session `[SRC:cognee/api/v1/session/__init__.py:L8]`

- `get_session(session_id="default_session", last_n=None, user=None)` → `List[SessionQAEntry]`
- `add_feedback(session_id, qa_id, feedback_text=None, score=None, user=None)`
- `delete_feedback(session_id, qa_id, user=None)`

Entries are chronological (oldest first). Use `entries[-1]` for most recent.

---

## Tracing `[AST:cognee/modules/observability/trace_context.py]`

- `enable_tracing(console_output=False)` — setup TracerProvider with in-memory CogneeSpanExporter
- `disable_tracing()` — shutdown TracerProvider
- `is_tracing_enabled()` — checks module flag, config, then env var `COGNEE_TRACING_ENABLED`
- `get_last_trace() -> Optional[CogneeTrace]` — most recent completed trace
- `get_all_traces() -> list[CogneeTrace]` — all buffered traces
- `clear_traces()` — flush buffer
