# Core API Reference — cognee

## add() `[AST:cognee/api/v1/add/add.py:L22]`

Full signature and parameter details in SKILL.md § Full API Reference.

**Supported file formats:** .txt, .md, .csv, .pdf, .png, .jpg, .mp3, .wav, .py, .js, .ts, .docx, .pptx

**Data input formats:**
- Text strings (not starting with `/` or `file://`)
- Absolute paths: `/path/to/document.pdf`
- File URLs: `file:///path/to/document.pdf`
- S3 paths: `s3://bucket-name/path/to/file.pdf`
- Binary file objects: `open("file.txt", "rb")`
- Lists of mixed types

**Related:** `update()`, `datasets.list_data()`, `cognify()`

---

## cognify() `[AST:cognee/api/v1/cognify/cognify.py:L47]`

**Pipeline tasks (ordered):**
1. `classify_documents` — wraps Data rows into Document objects
2. Check permissions — verifies write access
3. `extract_chunks_from_documents` — splits into DocumentChunks via chunker
4. `extract_graph_from_data` — LLM entity/relationship extraction
5. `summarize_text` — generates TextSummary DataPoints
6. `add_data_points` — embeds into vector store, persists to graph

**T2-past:** Summarization tasks lack test coverage. `[QMD:cognee-temporal:targeted-issues.md]`
**T2-past:** Re-add + re-cognify after delete may not re-ingest (pipeline state issue). `[QMD:cognee-temporal:issues.md]`

---

## search() `[AST:cognee/api/v1/search/search.py:L26]`

**SearchType mode details:**

| Mode | Retriever | LLM Required | Session Support |
|------|-----------|-------------|-----------------|
| GRAPH_COMPLETION | GraphCompletionRetriever | Yes | Yes |
| RAG_COMPLETION | ChunksRetriever + LLM | Yes | Yes |
| TRIPLET_COMPLETION | BruteForce triplet | Yes | Yes |
| CHUNKS | ChunksRetriever | No | No |
| SUMMARIES | SummariesRetriever | No | No |
| CYPHER | CypherSearchRetriever | No | No |
| TEMPORAL | TemporalRetriever | Yes | No |
| CODING_RULES | CodingRulesRetriever | No | No |
| CHUNKS_LEXICAL | BM25 keyword search | No | No |

**T2-past:** Multiquery triplet search and usage frequency tracking introduced. `[QMD:cognee-temporal:releases.md]`

---

## memify() `[AST:cognee/modules/memify/memify.py:L27]`

**Default extraction tasks:** `get_default_memify_extraction_tasks()` `[AST:cognee/memify_pipelines/memify_default_tasks.py:L8]`
**Default enrichment tasks:** `get_default_memify_enrichment_tasks()` `[AST:cognee/memify_pipelines/memify_default_tasks.py:L12]`

**T2-future:** Default pipeline changed from coding rules to triplet embedding (PR #2286, Mar 2026). `[QMD:cognee-temporal:prs.md]`

---

## run_custom_pipeline() `[AST:cognee/modules/run_custom_pipeline/run_custom_pipeline.py:L16]`

Custom pipeline execution with full control over tasks, data, and execution mode. Supports `use_pipeline_cache` and `incremental_loading` for repeat runs. Pipeline IDs are generated from task configuration — reset with `reset_dataset_pipeline_run_status`.
