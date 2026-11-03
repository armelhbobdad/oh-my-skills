# cognee.config — Full Method Reference

`cognee.config` is a namespace class with 45 static methods: 44 public ones plus the private `_update_config` helper the bulk setters share. The setters mutate Cognee's global runtime state — call them before any `add`/`cognify`/`search` invocation. `get`/`get_all` read it back.

Source: `[AST:cognee/api/v1/config/config.py:L171]`

Every bulk `set_*_config(config_dict)` setter goes through `_update_config`, which raises `InvalidConfigAttributeError` on unknown keys and coerces string values to the field's declared `bool`/`int`/`float` type (so `"true"` or `"4"` land as `True` / `4`). `[SRC:cognee/api/v1/config/config.py:L418-L428]` `[SRC:cognee/api/v1/config/config.py:L135-L168]`

## Contents

- [System paths](#system-paths)
- [LLM configuration](#llm-configuration)
- [Embedding configuration](#embedding-configuration)
- [Chunking configuration](#chunking-configuration)
- [Vector database configuration](#vector-database-configuration)
- [Graph database configuration](#graph-database-configuration)
- [Relational and migration DB configuration](#relational-and-migration-db-configuration)
- [Translation configuration](#translation-configuration)
- [Recall configuration](#recall-configuration)
- [Models / monitoring](#models--monitoring)
- [Generic setter](#generic-setter)
- [Generic getters](#generic-getters)

## System paths

- `system_root_directory(system_root_directory: str)` — Sets the base directory and cascades to relational/graph/vector DB paths. When `vector_db_provider == "lancedb"`, updates `vector_db_url` to `{databases_directory_path}/cognee.lancedb`. `[SRC:cognee/api/v1/config/config.py:L194]`
- `data_root_directory(data_root_directory: str)` — Sets the ingestion data root. `[SRC:cognee/api/v1/config/config.py:L222]`

## LLM configuration

- `set_llm_provider(llm_provider: str)` — One of `"openai"` (default), `"anthropic"`, `"gemini"`, `"ollama"`, `"mistral"`, `"bedrock"`, `"azure"`, `"custom"`, `"llama_cpp"`, `"mcp-sampling"`. The setter docstring's `'litellm'` example is not in that set. `[SRC:cognee/infrastructure/llm/config.py:L19-L32]` `[SRC:cognee/infrastructure/llm/config.py:L109]` `[SRC:cognee/api/v1/config/config.py:L350]`
- `set_llm_endpoint(llm_endpoint: str)` — Custom base URL for the LLM API. `[SRC:cognee/api/v1/config/config.py:L362]`
- `set_llm_model(llm_model: str)` — Model identifier (e.g., `"gpt-4o-mini"`, `"claude-3-sonnet"`). `[SRC:cognee/api/v1/config/config.py:L374]`
- `set_llm_api_key(llm_api_key: str)` — API key for the LLM provider. `[SRC:cognee/api/v1/config/config.py:L386]`
- `set_llm_config(config_dict: dict)` — Bulk update of LLM config. Raises `InvalidConfigAttributeError` on unknown keys. `[SRC:cognee/api/v1/config/config.py:L433]`

## Embedding configuration

- `set_embedding_provider(embedding_provider: str)` — e.g., `"openai"`, `"fastembed"`, `"azure"`, `"litellm"`. `[SRC:cognee/api/v1/config/config.py:L446]`
- `set_embedding_model(embedding_model: str)` — Model name (e.g., `"openai/text-embedding-3-large"`, `"BAAI/bge-small-en-v1.5"`). `[SRC:cognee/api/v1/config/config.py:L458]`
- `set_embedding_dimensions(embedding_dimensions: int)` — Vector size (e.g., `3072` for text-embedding-3-large, `384` for bge-small). Coerces string → int and raises `ValueError` for non-positive values. `[SRC:cognee/api/v1/config/config.py:L470]`
- `set_embedding_endpoint(embedding_endpoint: str)` — Custom embedding API URL. `[SRC:cognee/api/v1/config/config.py:L498]`
- `set_embedding_api_key(embedding_api_key: str)` — API key for the embedding provider. `[SRC:cognee/api/v1/config/config.py:L510]`
- `set_embedding_config(config_dict: dict)` — Bulk update. Routes `embedding_dimensions` through its dedicated setter to keep the integer-coercion + positive-value validation in place. Valid keys include: `embedding_provider`, `embedding_model`, `embedding_dimensions`, `embedding_endpoint`, `embedding_api_key`, `embedding_api_version`, `embedding_max_completion_tokens`, `embedding_batch_size`, `embedding_max_concurrent_data_points`, `huggingface_tokenizer`. `[SRC:cognee/api/v1/config/config.py:L522]` `[SRC:cognee/api/v1/config/config.py:L532-L536]`

## Chunking configuration

- `set_chunk_strategy(chunk_strategy: object)` — Object controlling chunk strategy. `[SRC:cognee/api/v1/config/config.py:L554]`
- `set_chunk_engine(chunk_engine: object)` — Object controlling chunk engine. `[SRC:cognee/api/v1/config/config.py:L566]`
- `set_chunk_overlap(chunk_overlap: object)` — Overlap between chunks. `[SRC:cognee/api/v1/config/config.py:L578]`
- `set_chunk_size(chunk_size: object)` — Target chunk size. `[SRC:cognee/api/v1/config/config.py:L590]`

## Vector database configuration

- `set_vector_db_provider(vector_db_provider: str)` — Built-ins: `"lancedb"` (default, subprocess adapter), `"pgvector"`, `"neptune_analytics"`, `"turso"` (needs the `turso` extra). ChromaDB and Qdrant are not built in: they need a community adapter registered through `use_vector_adapter` (imported from `cognee.infrastructure.databases.vector`, not top-level `cognee`), otherwise engine creation raises `OSError`. `[SRC:cognee/api/v1/config/config.py:L602]` `[SRC:cognee/infrastructure/databases/vector/config.py:L32]` `[SRC:cognee/infrastructure/databases/vector/create_vector_engine.py:L146-L148]` `[SRC:cognee/infrastructure/databases/vector/__init__.py:L6]` `[SRC:cognee/infrastructure/databases/vector/create_vector_engine.py:L296-L305]` `[SRC:cognee/infrastructure/databases/vector/create_vector_engine.py:L316-L320]`
- `set_vector_db_subprocess_enabled(vector_db_subprocess_enabled)` — Runs the LanceDB client in a dedicated worker process. Accepts a `bool` or a boolean-like string; on by default. `[SRC:cognee/api/v1/config/config.py:L615]` `[SRC:cognee/infrastructure/databases/vector/config.py:L37]` `[SRC:cognee/infrastructure/databases/vector/create_vector_engine.py:L280-L288]`
- `set_vector_db_config(config_dict: dict)` — Bulk vector DB config update. `[SRC:cognee/api/v1/config/config.py:L663]`
- `set_vector_db_key(db_key: str)` — API key for the vector DB provider. `[SRC:cognee/api/v1/config/config.py:L674]`
- `set_vector_db_url(db_url: str)` — Database URL. `[SRC:cognee/api/v1/config/config.py:L686]`

## Graph database configuration

- `set_graph_database_provider(graph_database_provider: str)` — e.g., `"ladybug"` (default; `"kuzu"` is still accepted as an alias), `"neo4j"`, `"postgres_demo"` (demo only, not production-ready; `"postgres"` is still accepted), `"neptune"`, `"neptune_analytics"`, `"turso"`. The embedded Ladybug DB runs in a subprocess by default. The setter docstring's `'networkx'` example is not a supported provider. `[SRC:cognee/api/v1/config/config.py:L282]` `[SRC:cognee/api/v1/config/config.py:L288]` `[SRC:cognee/infrastructure/databases/graph/get_graph_engine.py:L383-L387]` `[SRC:cognee/infrastructure/databases/graph/config.py:L47]` `[SRC:cognee/infrastructure/databases/graph/get_graph_engine.py:L446-L458]` `[SRC:cognee/infrastructure/databases/graph/get_graph_engine.py:L556-L567]`
- `set_graph_database_subprocess_enabled(graph_database_subprocess_enabled)` — Runs the embedded Ladybug (Kuzu) client in a dedicated worker process, isolating its memory and file locks; only the `ladybug`/`kuzu` provider reads it. Accepts a `bool` or a boolean-like string; on by default. `[SRC:cognee/api/v1/config/config.py:L294]` `[SRC:cognee/infrastructure/databases/graph/config.py:L62]` `[SRC:cognee/infrastructure/databases/graph/get_graph_engine.py:L446-L458]`
- `set_kuzu_num_threads(kuzu_num_threads)` — Max threads per query; `0` (default) keeps Kuzu's own default of one per CPU. Accepts `int` or a digit string, must be `>= 0`. `[SRC:cognee/api/v1/config/config.py:L313]` `[SRC:cognee/infrastructure/databases/graph/config.py:L65]`
- `set_kuzu_buffer_pool_size(kuzu_buffer_pool_size)` — Buffer pool size in bytes, `>= 1`. Default `1 << 35` (32 GB). `[SRC:cognee/api/v1/config/config.py:L326]` `[SRC:cognee/infrastructure/databases/graph/ladybug/adapter.py:L70]`
- `set_kuzu_max_db_size(kuzu_max_db_size)` — Max on-disk DB size in bytes, `>= 1`. Default `1 << 35` (32 GB); the method docstring's "4 GB" is stale. `[SRC:cognee/api/v1/config/config.py:L338]` `[SRC:cognee/infrastructure/databases/graph/ladybug/adapter.py:L71]`
- `set_graph_db_config(config_dict: dict) -> None` — Bulk graph DB config update. `[SRC:cognee/api/v1/config/config.py:L652]`
- `set_graph_model(graph_model: object)` — Graph extraction model instance. `[SRC:cognee/api/v1/config/config.py:L270]`

## Relational and migration DB configuration

- `set_relational_db_config(config_dict: dict)` — Bulk relational DB config update. `[SRC:cognee/api/v1/config/config.py:L630]`
- `set_migration_db_config(config_dict: dict)` — Bulk migration DB config update. `[SRC:cognee/api/v1/config/config.py:L641]`

## Translation configuration

- `set_translation_provider(provider: str)` — e.g., `"llm"`, `"google"`, `"azure"`. `[SRC:cognee/api/v1/config/config.py:L700]`
- `set_translation_target_language(target_language: str)` — e.g., `"en"`, `"es"`, `"fr"`. `[SRC:cognee/api/v1/config/config.py:L712]`
- `set_translation_config(config_dict: dict)` — Bulk translation config update. `[SRC:cognee/api/v1/config/config.py:L724]`

## Recall configuration

- `set_recall_warmup_shortcircuit(recall_warmup_shortcircuit)` — On by default: a graph-only recall against datasets whose knowledge graph has never been built returns an instant "memory warming up" marker instead of running graph search plus an LLM call. When the recall scope includes other sources, the cold graph lane contributes no results instead, and `only_context=True` calls skip the check. Accepts a `bool` or a boolean-like string. `[SRC:cognee/api/v1/config/config.py:L737]` `[SRC:cognee/modules/recall/config.py:L16]` `[SRC:cognee/api/v1/recall/recall.py:L701-L705]` `[SRC:cognee/api/v1/recall/recall.py:L753-L759]` `[SRC:cognee/api/v1/recall/recall.py:L770-L786]`
- `set_recall_warmup_threshold(recall_warmup_threshold)` — Minimum datapoint count considered "warm" (default `1`, must be `>= 1`). `[SRC:cognee/api/v1/config/config.py:L755]` `[SRC:cognee/modules/recall/config.py:L22]`
- `set_recall_warmup_cache_ttl(recall_warmup_cache_ttl)` — Seconds a warm verdict is cached in-process (default `60.0`, must be `>= 0`). `[SRC:cognee/api/v1/config/config.py:L769]` `[SRC:cognee/modules/recall/config.py:L28]`
- `set_recall_config(config_dict: dict)` — Bulk recall config update. `[SRC:cognee/api/v1/config/config.py:L783]`

## Models / monitoring

- `monitoring_tool(monitoring_tool: object)` — Observability tool instance. `[SRC:cognee/api/v1/config/config.py:L234]`
- `set_classification_model(classification_model: object)` — Classification model used during cognification. `[SRC:cognee/api/v1/config/config.py:L246]`
- `set_summarization_model(summarization_model: object)` — Summarization model used during cognification. `[SRC:cognee/api/v1/config/config.py:L258]`

## Generic setter

```python
cognee.config.set(key: str, value, persist: bool = False)
```

Maps well-known keys to specific setter methods via a dispatch table. Unknown keys that correspond to an attribute on `EmbeddingConfig` fall back through `set_embedding_config({key: value})`. Anything else raises `InvalidConfigAttributeError`.

With `persist=True` it also writes the resulting value as an env var (the field's alias, else `key.upper()`) into the `.env` this process loaded, or into `.env` in the current directory, creating it if needed. It then returns `{"path": ..., "created": ..., "env_var": ...}`. With the default `persist=False` it returns `None`. `[SRC:cognee/api/v1/config/config.py:L958-L971]` `[SRC:cognee/api/v1/config/config.py:L93-L112]` `[SRC:cognee/api/v1/config/config.py:L63-L81]`

**Known keys in the dispatch table (30):** `llm_provider`, `llm_model`, `llm_api_key`, `llm_endpoint`, `embedding_provider`, `embedding_model`, `embedding_dimensions`, `embedding_endpoint`, `embedding_api_key`, `graph_database_provider`, `graph_database_subprocess_enabled`, `kuzu_num_threads`, `kuzu_buffer_pool_size`, `kuzu_max_db_size`, `vector_db_provider`, `vector_db_subprocess_enabled`, `vector_db_url`, `vector_db_key`, `chunk_size`, `chunk_overlap`, `chunk_strategy`, `chunk_engine`, `classification_model`, `summarization_model`, `graph_model`, `recall_warmup_shortcircuit`, `recall_warmup_threshold`, `recall_warmup_cache_ttl`, `system_root_directory`, `data_root_directory`. `[SRC:cognee/api/v1/config/config.py:L794-L825]`

Provenance: `[SRC:cognee/api/v1/config/config.py:L915]`

## Generic getters

```python
cognee.config.get(key: str, reveal_secrets: bool = False)
cognee.config.get_all(reveal_secrets: bool = False) -> dict
```

`get` reads any key `set` accepts (`_getter_mapping` mirrors the dispatch table) and falls back to `EmbeddingConfig` attributes. Anything else raises `InvalidConfigAttributeError`. `get_all` returns every mapped key plus the remaining `EmbeddingConfig` fields. `[SRC:cognee/api/v1/config/config.py:L885-L896]` `[SRC:cognee/api/v1/config/config.py:L907-L912]`

Secrets (`llm_api_key`, `embedding_api_key`, `vector_db_key`) are masked unless `reveal_secrets=True`. A value of 8 characters or fewer becomes all `*`; a longer one keeps its first 3 and last 4 characters (`abc...wxyz`). `[SRC:cognee/api/v1/config/config.py:L867]` `[SRC:cognee/api/v1/config/config.py:L84-L90]`

Provenance: `[SRC:cognee/api/v1/config/config.py:L870]` `[SRC:cognee/api/v1/config/config.py:L899]`
