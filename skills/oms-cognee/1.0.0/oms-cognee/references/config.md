# cognee.config — Full Method Reference

`cognee.config` is a namespace class with 32 static methods. All methods mutate Cognee's global runtime state — call them before any `add`/`cognify`/`search` invocation.

Source: `[AST:cognee/api/v1/config/config.py:L18]`

## Contents

- [System paths](#system-paths)
- [LLM configuration](#llm-configuration)
- [Embedding configuration](#embedding-configuration)
- [Chunking configuration](#chunking-configuration)
- [Vector database configuration](#vector-database-configuration)
- [Graph database configuration](#graph-database-configuration)
- [Relational and migration DB configuration](#relational-and-migration-db-configuration)
- [Translation configuration](#translation-configuration)
- [Models / monitoring](#models-monitoring)
- [Generic setter](#generic-setter)

## System paths

- `system_root_directory(system_root_directory: str)` — Sets the base directory and cascades to relational/graph/vector DB paths. When `vector_db_provider == "lancedb"`, updates `vector_db_url` to `{databases_directory_path}/cognee.lancedb`. `[AST:cognee/api/v1/config/config.py:L41]`
- `data_root_directory(data_root_directory: str)` — Sets the ingestion data root. `[AST:cognee/api/v1/config/config.py:L69]`

## LLM configuration

- `set_llm_provider(llm_provider: str)` — e.g., `"openai"`, `"anthropic"`, `"gemini"`, `"ollama"`, `"mistral"`, `"bedrock"`, `"litellm"`. `[AST:cognee/api/v1/config/config.py:L141]`
- `set_llm_endpoint(llm_endpoint: str)` — Custom base URL for the LLM API. `[AST:cognee/api/v1/config/config.py:L153]`
- `set_llm_model(llm_model: str)` — Model identifier (e.g., `"gpt-4o-mini"`, `"claude-3-sonnet"`). `[AST:cognee/api/v1/config/config.py:L165]`
- `set_llm_api_key(llm_api_key: str)` — API key for the LLM provider. `[AST:cognee/api/v1/config/config.py:L177]`
- `set_llm_config(config_dict: dict)` — Bulk update of LLM config. Raises `InvalidConfigAttributeError` on unknown keys. `[AST:cognee/api/v1/config/config.py:L218]`

## Embedding configuration

- `set_embedding_provider(embedding_provider: str)` — e.g., `"openai"`, `"fastembed"`, `"azure"`, `"litellm"`. `[AST:cognee/api/v1/config/config.py:L231]`
- `set_embedding_model(embedding_model: str)` — Model name (e.g., `"openai/text-embedding-3-large"`, `"BAAI/bge-small-en-v1.5"`). `[AST:cognee/api/v1/config/config.py:L243]`
- `set_embedding_dimensions(embedding_dimensions: int)` — Vector size (e.g., `3072` for text-embedding-3-large, `384` for bge-small). Coerces string → int and raises `ValueError` for non-positive values. `[AST:cognee/api/v1/config/config.py:L255]`
- `set_embedding_endpoint(embedding_endpoint: str)` — Custom embedding API URL. `[AST:cognee/api/v1/config/config.py:L283]`
- `set_embedding_api_key(embedding_api_key: str)` — API key for the embedding provider. `[AST:cognee/api/v1/config/config.py:L295]`
- `set_embedding_config(config_dict: dict)` — Bulk update. Routes `embedding_dimensions` through its dedicated setter to keep the integer-coercion + positive-value validation in place. Valid keys include: `embedding_provider`, `embedding_model`, `embedding_dimensions`, `embedding_endpoint`, `embedding_api_key`, `embedding_api_version`, `embedding_max_completion_tokens`, `embedding_batch_size`, `huggingface_tokenizer`. `[AST:cognee/api/v1/config/config.py:L307]`

## Chunking configuration

- `set_chunk_strategy(chunk_strategy: object)` — Object controlling chunk strategy. `[AST:cognee/api/v1/config/config.py:L338]`
- `set_chunk_engine(chunk_engine: object)` — Object controlling chunk engine. `[AST:cognee/api/v1/config/config.py:L350]`
- `set_chunk_overlap(chunk_overlap: object)` — Overlap between chunks. `[AST:cognee/api/v1/config/config.py:L362]`
- `set_chunk_size(chunk_size: object)` — Target chunk size. `[AST:cognee/api/v1/config/config.py:L374]`

## Vector database configuration

- `set_vector_db_provider(vector_db_provider: str)` — e.g., `"lancedb"` (default), `"chromadb"`, `"qdrant"`. `[AST:cognee/api/v1/config/config.py:L386]`
- `set_vector_db_config(config_dict: dict)` — Bulk vector DB config update. `[AST:cognee/api/v1/config/config.py:L431]`
- `set_vector_db_key(db_key: str)` — API key for the vector DB provider. `[AST:cognee/api/v1/config/config.py:L442]`
- `set_vector_db_url(db_url: str)` — Database URL. `[AST:cognee/api/v1/config/config.py:L454]`

## Graph database configuration

- `set_graph_database_provider(graph_database_provider: str)` — e.g., `"kuzu"` (default), `"neo4j"`, `"networkx"`. `[AST:cognee/api/v1/config/config.py:L129]`
- `set_graph_db_config(config_dict: dict)` — Bulk graph DB config update. `[AST:cognee/api/v1/config/config.py:L420]`
- `set_graph_model(graph_model: object)` — Graph extraction model instance. `[AST:cognee/api/v1/config/config.py:L117]`

## Relational and migration DB configuration

- `set_relational_db_config(config_dict: dict)` — Bulk relational DB config update. `[AST:cognee/api/v1/config/config.py:L398]`
- `set_migration_db_config(config_dict: dict)` — Bulk migration DB config update. `[AST:cognee/api/v1/config/config.py:L409]`

## Translation configuration

- `set_translation_provider(provider: str)` — e.g., `"llm"`, `"google"`, `"azure"`. `[AST:cognee/api/v1/config/config.py:L468]`
- `set_translation_target_language(target_language: str)` — e.g., `"en"`, `"es"`, `"fr"`. `[AST:cognee/api/v1/config/config.py:L480]`
- `set_translation_config(config_dict: dict)` — Bulk translation config update. `[AST:cognee/api/v1/config/config.py:L492]`

## Models / monitoring

- `monitoring_tool(monitoring_tool: object)` — Observability tool instance. `[AST:cognee/api/v1/config/config.py:L81]`
- `set_classification_model(classification_model: object)` — Classification model used during cognification. `[AST:cognee/api/v1/config/config.py:L93]`
- `set_summarization_model(summarization_model: object)` — Summarization model used during cognification. `[AST:cognee/api/v1/config/config.py:L105]`

## Generic setter

```python
cognee.config.set(key: str, value)
```

Maps well-known keys to specific setter methods via a dispatch table. Unknown keys that correspond to an attribute on `EmbeddingConfig` fall back through `set_embedding_config({key: value})`. Anything else raises `InvalidConfigAttributeError`.

**Known keys in the dispatch table:** `llm_provider`, `llm_model`, `llm_api_key`, `llm_endpoint`, `embedding_provider`, `embedding_model`, `embedding_dimensions`, `embedding_endpoint`, `embedding_api_key`, `graph_database_provider`, `vector_db_provider`, `vector_db_url`, `vector_db_key`, `chunk_size`, `chunk_overlap`, `chunk_strategy`, `chunk_engine`, `classification_model`, `summarization_model`, `graph_model`, `system_root_directory`, `data_root_directory`.

Provenance: `[AST:cognee/api/v1/config/config.py:L503]`
