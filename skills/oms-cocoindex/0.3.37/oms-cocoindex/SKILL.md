---
name: oms-cocoindex
description: "Use when builds data transformation flows on top of cocoindex — a
  Python framework with a Rust engine for ultra-performant, incremental data
  indexing (ETL, RAG ingestion, knowledge graphs, vector search). Covers the
  flow-building public API: FlowBuilder, DataScope, DataSlice, Flow,
  FlowLiveUpdater, sources, targets
  (Postgres/Qdrant/Neo4j/Pinecone/LanceDB/etc.), functions (SplitRecursively,
  SentenceTransformerEmbed, ExtractByLlm, EmbedText, ColPali), LlmSpec, index
  defs, settings, and runtime lifecycle. Use for authoring indexing flows,
  chunking+embedding pipelines, LLM extraction, and live updates. Do NOT use for
  authoring custom Rust engine components — users write flows in Python via pyo3
  bindings."
---

# oms-cocoindex

## Overview

cocoindex is a Python ETL framework with a Rust engine for building incremental data indexes (embeddings, knowledge graphs, vector search, LLM extraction). Users author flows in Python; the Rust engine handles incremental recomputation and target state management.

- **Source:** [cocoindex-io/cocoindex](https://github.com/cocoindex-io/cocoindex) @ `v0.3.37` (commit `87c5dbf0`)
- **Forge tier:** Deep — AST structural extraction + QMD temporal/docs enrichment
- **Exports documented:** 102 public exports (T1 AST-verified) across `flow`, `lib`, `index`, `llm`, `setting`, `auth_registry`, `query_handler`, `typing`, `op`, `sources`, `targets`, `functions`, `cli`, `utils`
- **Confidence distribution:** T1 = 102, T2 = 15, T3 = 10 (docs), T1-low = 0

> **Note on stability:** cocoindex is Development Status 3 — Alpha. This skill is pinned to tag `v0.3.37`; upstream has since moved to `v1.0.0-alpha*`. Re-forge for newer versions.

## Quick Start

End-to-end text-embedding flow — read markdown files, chunk, embed with SentenceTransformer, export to Postgres + pgvector:

```python
import cocoindex

@cocoindex.flow_def(name="TextEmbedding")
def text_embedding_flow(
    flow_builder: cocoindex.FlowBuilder,
    data_scope: cocoindex.DataScope,
):
    data_scope["documents"] = flow_builder.add_source(
        cocoindex.sources.LocalFile(path="markdown_files")
    )
    doc_embeddings = data_scope.add_collector()

    with data_scope["documents"].row() as doc:
        doc["chunks"] = doc["content"].transform(
            cocoindex.functions.SplitRecursively(),
            language="markdown", chunk_size=2000, chunk_overlap=500,
        )
        with doc["chunks"].row() as chunk:
            chunk["embedding"] = chunk["text"].transform(
                cocoindex.functions.SentenceTransformerEmbed(
                    model="sentence-transformers/all-MiniLM-L6-v2"
                )
            )
            doc_embeddings.collect(
                filename=doc["filename"],
                location=chunk["location"],
                text=chunk["text"],
                embedding=chunk["embedding"],
            )

    doc_embeddings.export(
        "doc_embeddings",
        cocoindex.targets.Postgres(),
        primary_key_fields=["filename", "location"],
        vector_indexes=[
            cocoindex.VectorIndexDef(
                field_name="embedding",
                metric=cocoindex.VectorSimilarityMetric.COSINE_SIMILARITY,
            )
        ],
    )
```

Run with: `cocoindex update main.py` (one-time) or `cocoindex update main.py -L` (live). Requires `COCOINDEX_DATABASE_URL` env var. Source: [AST:python/cocoindex/__init__.py:L1] · [EXT:https://cocoindex.io/docs/getting_started/quickstart]

<!-- [MANUAL:quick-start-notes] -->
<!-- Add custom notes here. This section is preserved during skill updates. -->
<!-- [/MANUAL:quick-start-notes] -->

## Common Workflows

**Define and register a flow (recommended):**
`@cocoindex.flow_def(name="...")` wraps a function `(FlowBuilder, DataScope) -> None` and registers it. [AST:python/cocoindex/flow.py:L1011]

**Explicit flow registration (dynamic names):**
`cocoindex.open_flow(name, fl_def)` returns a `Flow`. Use when the name is computed at runtime. [AST:python/cocoindex/flow.py:L986]

**One-time vs live update:**
`demo_flow.update(print_stats=True)` — finishes when target is fresh. [AST:python/cocoindex/flow.py:L771]
`cocoindex.FlowLiveUpdater(demo_flow)` with `start()`/`wait()` or `with` context manager — continuous change capture. [AST:python/cocoindex/flow.py:L603]

**Setup / drop target backends:**
Per flow: `demo_flow.setup()` / `demo_flow.drop()` (+ `_async` variants). [AST:python/cocoindex/flow.py:L855] [AST:python/cocoindex/flow.py:L868]
All flows at once: `cocoindex.setup_all_flows()` / `cocoindex.drop_all_flows()`. [AST:python/cocoindex/flow.py:L1300] [AST:python/cocoindex/flow.py:L1309]

**Transient in-memory transform (no target):**
`@cocoindex.transform_flow()` on a function `(DataSlice[T], ...) -> DataSlice[U]`, then call `.eval(...)` / `.eval_async(...)`. [AST:python/cocoindex/flow.py:L1251]

**LLM structured extraction:**
`cocoindex.functions.ExtractByLlm(llm_spec=LlmSpec(...), output_type=MyDataclass, instruction=...)` → transforms text into a typed struct. [AST:python/cocoindex/functions/_engine_builtin_specs.py:L64]

## Key API Summary

| Export | Kind | Purpose | Provenance |
|---|---|---|---|
| `FlowBuilder` | class | Flow authoring helper (`add_source`, `transform`, `declare`) | [AST:python/cocoindex/flow.py:L495] |
| `DataScope` | class | Scope container for fields + collectors (top-level, per-row) | [AST:python/cocoindex/flow.py:L302] |
| `DataSlice` | class | Typed reference to scope field; `.row()`, `.transform()`, `.call()` | [AST:python/cocoindex/flow.py:L212] |
| `Flow` | class | Pipeline handle: `update`, `setup`, `drop`, `close`, `evaluate_and_dump` | [AST:python/cocoindex/flow.py:L705] |
| `flow_def(name=None)` | decorator | Wraps a flow function and registers it | [AST:python/cocoindex/flow.py:L1011] |
| `open_flow(name, fl_def)` | function | Explicit flow registration, returns `Flow` | [AST:python/cocoindex/flow.py:L986] |
| `transform_flow()` | decorator | Wraps a transient in-memory transform function | [AST:python/cocoindex/flow.py:L1251] |
| `FlowLiveUpdater` | class | Live updater with `start`/`wait`/`abort`/`next_status_updates` | [AST:python/cocoindex/flow.py:L603] |
| `init(settings=None)` | function | Explicit cocoindex initialization | [AST:python/cocoindex/lib.py:L58] |
| `start_server(settings)` | function | Start HTTP server (used by `cocoindex server` CLI) | [AST:python/cocoindex/lib.py:L67] |
| `LlmSpec` | dataclass | LLM target config: `api_type`, `model`, `address`, `api_config` | [AST:python/cocoindex/llm.py:L55] |
| `VectorIndexDef` | dataclass | `field_name`, `metric`, `method` (Hnsw/IvfFlat) | [AST:python/cocoindex/index.py:L33] |
| `FtsIndexDef` | dataclass | Full-text-search index (LanceDB only currently) | [AST:python/cocoindex/index.py:L44] |
| `add_auth_entry(key, value)` | function | Register stable-key auth (target backend identity) | [AST:python/cocoindex/auth_registry.py:L31] |
| `add_transient_auth_entry(value)` | function | Register ephemeral auth (sources/functions) | [AST:python/cocoindex/auth_registry.py:L25] |
| `Settings` | dataclass | Library settings (`database`, `app_namespace`, ...) | [AST:python/cocoindex/setting.py:L75] |

## Migration & Deprecation Warnings

- **`cocoindex.add_flow_def(name, fl_def)` is DEPRECATED** — use `cocoindex.open_flow(name, fl_def)` instead. Identical behavior; the old name is kept for compatibility only. [AST:python/cocoindex/flow.py:L997]
- **`cocoindex.remove_flow(fl)` is DEPRECATED** — use `fl.close()` instead. [AST:python/cocoindex/flow.py:L1004]
- **`cocoindex.storages` is a DEPRECATED alias for `cocoindex.targets`** — use `cocoindex.targets` in new code. [AST:python/cocoindex/__init__.py:L12]
- **`cocoindex.utils.get_target_storage_default_name` is DEPRECATED** — use `get_target_default_name`. [AST:python/cocoindex/utils.py:L18]
- **Retired `Kuzu` target** — `cocoindex.targets.Kuzu`, `KuzuConnection`, `KuzuDeclaration` are backward-compat aliases for `Ladybug`. New code should use `Ladybug`. [AST:python/cocoindex/targets/_engine_builtin_specs.py:L205]
- **Alpha stability:** cocoindex is Development Status 3 — Alpha. The public API may change across minor versions; this skill is pinned to `v0.3.37`. [QMD:oms-cocoindex-temporal:releases.md]

See [Full API Reference](references/flow-api.md) for migration details.

## Key Types

```python
# Index metrics
VectorSimilarityMetric.COSINE_SIMILARITY  # "CosineSimilarity"
VectorSimilarityMetric.L2_DISTANCE        # "L2Distance"
VectorSimilarityMetric.INNER_PRODUCT      # "InnerProduct"

# LLM API types (enum)
LlmApiType.OPENAI, AZURE_OPENAI, OLLAMA, GEMINI, VERTEX_AI,
ANTHROPIC, VOYAGE, LITE_LLM, OPEN_ROUTER, VLLM, BEDROCK, NOVITA

# Generated field markers
GeneratedField.UUID  # auto-generated UUID, stable across unchanged inputs

# Annotated typing aliases (attach schema info to python types)
Int64, Float32, Float64, LocalDateTime, OffsetDateTime, Range, Json
Vector[np.float32, Literal[384]]  # dimension-parameterized vector
```

Provenance: [AST:python/cocoindex/index.py:L6] [AST:python/cocoindex/llm.py:L7] [AST:python/cocoindex/flow.py:L359] [AST:python/cocoindex/typing.py:L37]

## Architecture at a Glance

- **Flow authoring (Python):** `flow.py` — `FlowBuilder`, `DataScope`, `DataSlice`, `DataCollector`, `Flow`, `FlowLiveUpdater`, `TransformFlow`, `flow_def` / `open_flow` / `transform_flow` decorators.
- **Runtime lifecycle:** `lib.py` — `init`, `start_server`, `stop`; implicit auto-init on first flow call.
- **Sources (built-in):** `sources/_engine_builtin_specs.py` — `LocalFile`, `GoogleDrive`, `AmazonS3`, `AzureBlob`, `Postgres`.
- **Targets (built-in):** `targets/_engine_builtin_specs.py` — `Postgres`, `Qdrant`, `Pinecone`, `Neo4j`, `FalkorDB`, `Ladybug` (+ retired `Kuzu` alias). Extended target modules: `targets/chromadb.py` (`ChromaDB`), `targets/lancedb.py` (`LanceDB`), `targets/doris.py` (`DorisTarget`), `targets/turbopuffer.py` (`Turbopuffer`), `targets/pinecone.py` (connector for built-in `Pinecone` spec).
- **Functions (built-in):** `functions/_engine_builtin_specs.py` — `ParseJson`, `DetectProgrammingLanguage`, `SplitRecursively`, `SplitBySeparators`, `EmbedText`, `ExtractByLlm`; plus `functions/sbert.py` (`SentenceTransformerEmbed`) and `functions/colpali.py` (`ColPaliEmbedImage`, `ColPaliEmbedQuery`).
- **Operation spec framework:** `op.py` — `FunctionSpec`, `SourceSpec`, `TargetSpec`, `TargetAttachmentSpec`, `DeclarationSpec` base classes; `@op.function`, `@op.executor_class`, `@op.source_connector`, `@op.target_connector` decorators for custom ops.
- **Auth, indexes, settings, typing:** `auth_registry.py`, `index.py`, `setting.py`, `typing.py` — orthogonal support modules.
- **CLI:** `cli.py` — `cocoindex` click entry point with `ls`, `show`, `setup`, `drop`, `update`, `evaluate`, `server` subcommands.

The Rust engine (`rust/` directory) is intentionally out of scope — users author in Python via pyo3-compiled bindings exposed as `cocoindex._engine`.

## CLI

The `cocoindex` CLI (click group [AST:python/cocoindex/cli.py:L122]):

```sh
cocoindex -e .env -d app_dir ls [APP_TARGET]                    # List flows
cocoindex show APP_FLOW_SPECIFIER [--verbose]                   # Show flow spec
cocoindex setup APP_TARGET [-f] [--reset]                       # Setup backends
cocoindex drop APP_TARGET [FLOW_NAME...] [-f]                   # Drop backends
cocoindex update APP_FLOW_SPECIFIER [-L] [--reexport]           # Build/update index
cocoindex evaluate APP_FLOW_SPECIFIER --output-dir ./eval [--no-cache]  # Dry-run
cocoindex server APP_TARGET [-a ADDR] [-L] [--reload] ...       # Start HTTP server
```

`APP_TARGET` = `path/to/app.py` or `installed_module`. `APP_FLOW_SPECIFIER` = `APP_TARGET` or `APP_TARGET:FLOW_NAME`. Provenance: [AST:python/cocoindex/cli.py:L143] [AST:python/cocoindex/cli.py:L195] [AST:python/cocoindex/cli.py:L337] [AST:python/cocoindex/cli.py:L364] [AST:python/cocoindex/cli.py:L456] [AST:python/cocoindex/cli.py:L522] [AST:python/cocoindex/cli.py:L642]

<!-- [MANUAL:api-notes] -->
<!-- Add custom notes here. This section is preserved during skill updates. -->
<!-- [/MANUAL:api-notes] -->

---

## Full API Reference

### Flow authoring — `cocoindex.flow`

See [references/flow-api.md](references/flow-api.md) for the complete API.

**`FlowBuilder`** [AST:python/cocoindex/flow.py:L495] — wraps `_FlowBuilderState`. Core methods:

- `add_source(spec, /, *, name=None, refresh_interval=None, max_inflight_rows=None, max_inflight_bytes=None) -> DataSlice[T]` [AST:python/cocoindex/flow.py:L511] — import from a source. `spec` must be a subclass of `op.SourceSpec`. `refresh_interval` (`datetime.timedelta`) triggers periodic list-and-diff in live mode. `max_inflight_rows`/`max_inflight_bytes` bound concurrent processing per source.
- `transform(fn_spec, *args, **kwargs) -> DataSlice[Any]` [AST:python/cocoindex/flow.py:L548] — apply a function spec to one or more data slices.
- `declare(spec: op.DeclarationSpec) -> None` [AST:python/cocoindex/flow.py:L566] — register a target declaration out-of-band (e.g., graph-target node labels referenced by relationships).

**`DataScope`** [AST:python/cocoindex/flow.py:L302]:

- `__getitem__(field_name) -> DataSlice[T]` / `__setitem__(field_name, value: DataSlice[T])` — get/add fields; cannot override existing fields.
- `add_collector(name=None) -> DataCollector` [AST:python/cocoindex/flow.py:L345]
- Context manager: `__enter__` / `__exit__` (used by `DataSlice.for_each` / `row()`).

**`DataSlice[T]`** [AST:python/cocoindex/flow.py:L212]:

- `row(*, max_inflight_rows=None, max_inflight_bytes=None) -> DataScope` [AST:python/cocoindex/flow.py:L232] — per-row child scope; use as `with slice.row() as row_scope:`.
- `for_each(f, *, max_inflight_rows=None, max_inflight_bytes=None) -> None` [AST:python/cocoindex/flow.py:L253] — apply a function to each row (uses `row()` internally).
- `transform(fn_spec, *args, **kwargs) -> DataSlice[Any]` [AST:python/cocoindex/flow.py:L270] — transform this slice, passing it as first positional argument.
- `call(func, *args, **kwargs) -> S` [AST:python/cocoindex/flow.py:L291] — apply a host-side callable (for composition).
- `__getitem__(field_name)` — select a sub-field (struct type).

**`DataCollector`** [AST:python/cocoindex/flow.py:L367]:

- `collect(**kwargs) -> None` [AST:python/cocoindex/flow.py:L381] — record an entry. Values may be `DataSlice` or `GeneratedField.UUID`.
- `export(target_name, target_spec, /, *, primary_key_fields, attachments=(), vector_indexes=(), fts_indexes=(), vector_index=(), setup_by_user=False) -> None` [AST:python/cocoindex/flow.py:L402] — export collected data to a target. Must be called at top level. `target_name` identifier must remain stable across runs — renaming causes drop+recreate. `vector_index` is a legacy alias; use `vector_indexes` in new code.

**`Flow`** [AST:python/cocoindex/flow.py:L705]:

- `name` / `full_name` (properties) [AST:python/cocoindex/flow.py:L758] [AST:python/cocoindex/flow.py:L765] — `full_name` is `{app_namespace}.{name}`.
- `update(*, reexport_targets=False, full_reprocess=False, print_stats=False) -> _engine.IndexUpdateInfo` [AST:python/cocoindex/flow.py:L771] — one-time update. Async: `update_async(...)` [AST:python/cocoindex/flow.py:L791].
- `setup(report_to_stdout=False) -> None` / `setup_async(...)` [AST:python/cocoindex/flow.py:L855] [AST:python/cocoindex/flow.py:L861]
- `drop(report_to_stdout=False) -> None` / `drop_async(...)` [AST:python/cocoindex/flow.py:L868] [AST:python/cocoindex/flow.py:L879] — drops backends; the `Flow` instance remains valid.
- `close() -> None` [AST:python/cocoindex/flow.py:L886] — remove from current process; instance invalid afterward. Does NOT touch backends.
- `evaluate_and_dump(options: EvaluateAndDumpOptions) -> _engine.IndexUpdateInfo` [AST:python/cocoindex/flow.py:L815] — run transformations to disk without updating target.
- `add_query_handler(name, handler, /, *, result_fields=None) -> None` [AST:python/cocoindex/flow.py:L898] — attach a named query handler (called via server).
- `query_handler(name=None, result_fields=None)` [AST:python/cocoindex/flow.py:L935] — decorator form.

**`FlowLiveUpdater`** [AST:python/cocoindex/flow.py:L603]:

- `__init__(fl: Flow, options: FlowLiveUpdaterOptions | None = None)` [AST:python/cocoindex/flow.py:L612]
- `start()` / `start_async()` — begin live update. [AST:python/cocoindex/flow.py:L632] [AST:python/cocoindex/flow.py:L638]
- `abort()` — stop the updater. [AST:python/cocoindex/flow.py:L677]
- `wait()` / `wait_async()` — block until updater finishes. [AST:python/cocoindex/flow.py:L646] [AST:python/cocoindex/flow.py:L652]
- `next_status_updates()` / `next_status_updates_async()` → `FlowUpdaterStatusUpdates` [AST:python/cocoindex/flow.py:L658] [AST:python/cocoindex/flow.py:L667]
- `update_stats() -> _engine.IndexUpdateInfo` [AST:python/cocoindex/flow.py:L683]
- Supports sync (`with`) and async (`async with`) context-manager usage (calls `start`/`abort`+`wait` on enter/exit). [AST:python/cocoindex/flow.py:L616] [AST:python/cocoindex/flow.py:L624]

**Module-level helpers:**

- `cocoindex.flow_def(name=None)` [AST:python/cocoindex/flow.py:L1011] — decorator wrapping a flow function.
- `cocoindex.open_flow(name, fl_def) -> Flow` [AST:python/cocoindex/flow.py:L986]
- `cocoindex.add_flow_def(name, fl_def) -> Flow` — DEPRECATED alias for `open_flow`. [AST:python/cocoindex/flow.py:L997]
- `cocoindex.remove_flow(fl) -> None` — DEPRECATED alias for `fl.close()`. [AST:python/cocoindex/flow.py:L1004]
- `cocoindex.update_all_flows_async(options: FlowLiveUpdaterOptions) -> dict[str, _engine.IndexUpdateInfo]` [AST:python/cocoindex/flow.py:L1068]
- `cocoindex.setup_all_flows(report_to_stdout=False) -> None` [AST:python/cocoindex/flow.py:L1300]
- `cocoindex.drop_all_flows(report_to_stdout=False) -> None` [AST:python/cocoindex/flow.py:L1309]
- `cocoindex.transform_flow() -> Callable[[Callable[..., DataSlice[T]]], TransformFlow[T]]` [AST:python/cocoindex/flow.py:L1251]

**Dataclasses exported to users:**

- `FlowLiveUpdaterOptions(live_mode=True, reexport_targets=False, full_reprocess=False, print_stats=False)` [AST:python/cocoindex/flow.py:L574]
- `FlowUpdaterStatusUpdates(active_sources: list[str], updated_sources: list[str])` [AST:python/cocoindex/flow.py:L591]
- `EvaluateAndDumpOptions(output_dir: str, use_cache: bool = True)` [AST:python/cocoindex/flow.py:L696]
- `GeneratedField(Enum)` — member `UUID = "Uuid"`. [AST:python/cocoindex/flow.py:L359]

### Library lifecycle — `cocoindex.lib`

- `cocoindex.settings(fn=None)` [AST:python/cocoindex/lib.py:L35] — decorator registering a function `() -> Settings` as the settings provider. Overrides env vars. Warns on re-registration.
- `cocoindex.init(settings: Settings | None = None) -> None` [AST:python/cocoindex/lib.py:L58] — explicit init. Optional — cocoindex auto-inits on first flow method call. Prefer explicit init at startup so errors surface early.
- `cocoindex.start_server(settings: ServerSettings) -> None` [AST:python/cocoindex/lib.py:L67] — starts HTTP server (used by `cocoindex server`). Ensures all flows are built first.
- `cocoindex.stop() -> None` [AST:python/cocoindex/lib.py:L73]

### Settings & auth — `cocoindex.setting`, `cocoindex.auth_registry`

See [references/settings-auth.md](references/settings-auth.md) for full field tables.

- `Settings(ignore_target_drop_failures=False, database=None, db_schema_name=None, app_namespace="", global_execution_options=None)` [AST:python/cocoindex/setting.py:L75] — classmethod `Settings.from_env()`.
- `DatabaseConnectionSpec(url, user=None, password=None, max_connections=25, min_connections=5)` [AST:python/cocoindex/setting.py:L29]
- `GlobalExecutionOptions(source_max_inflight_rows=1024, source_max_inflight_bytes=None)` [AST:python/cocoindex/setting.py:L43]
- `ServerSettings(address="127.0.0.1:49344", cors_origins=None)` [AST:python/cocoindex/setting.py:L149]
- `get_app_namespace(*, trailing_delimiter=None) -> str` [AST:python/cocoindex/setting.py:L12]
- `AuthEntryReference[T]` — dataclass with `key: str`, subclass of `TransientAuthEntryReference[T]`. [AST:python/cocoindex/auth_registry.py:L21]
- `add_auth_entry(key: str, value: T) -> AuthEntryReference[T]` [AST:python/cocoindex/auth_registry.py:L31]
- `add_transient_auth_entry(value: T) -> TransientAuthEntryReference[T]` [AST:python/cocoindex/auth_registry.py:L25]
- `ref_auth_entry(key: str) -> AuthEntryReference[T]` [AST:python/cocoindex/auth_registry.py:L37]

### Indexes — `cocoindex.index`

- `VectorSimilarityMetric(Enum)` — `COSINE_SIMILARITY`, `L2_DISTANCE`, `INNER_PRODUCT`. [AST:python/cocoindex/index.py:L6]
- `HnswVectorIndexMethod(kind="Hnsw", m=None, ef_construction=None)` [AST:python/cocoindex/index.py:L13]
- `IvfFlatVectorIndexMethod(kind="IvfFlat", lists=None)` [AST:python/cocoindex/index.py:L22]
- `VectorIndexDef(field_name: str, metric: VectorSimilarityMetric, method: VectorIndexMethod | None = None)` [AST:python/cocoindex/index.py:L33]
- `FtsIndexDef(field_name: str, parameters: dict[str, Any] | None = None)` — LanceDB only. [AST:python/cocoindex/index.py:L44]
- `IndexOptions(primary_key_fields: Sequence[str], vector_indexes=(), fts_indexes=())` [AST:python/cocoindex/index.py:L57]

### LLM — `cocoindex.llm`

- `LlmApiType(Enum)` — 12 members (OPENAI, OLLAMA, GEMINI, VERTEX_AI, ANTHROPIC, LITE_LLM, OPEN_ROUTER, VOYAGE, VLLM, BEDROCK, AZURE_OPENAI, NOVITA). [AST:python/cocoindex/llm.py:L7]
- `LlmSpec(api_type, model, address=None, api_key=None, api_config=None)` [AST:python/cocoindex/llm.py:L55]
- `VertexAiConfig(project, region=None)` [AST:python/cocoindex/llm.py:L25]
- `OpenAiConfig(org_id=None, project_id=None)` [AST:python/cocoindex/llm.py:L35]
- `AzureOpenAiConfig(deployment_id, api_version=None)` [AST:python/cocoindex/llm.py:L45]

See [references/sources-targets-functions.md](references/sources-targets-functions.md) for source / target / function specs and [EXT:https://cocoindex.io/docs/ai/llm] for integration details per provider.

### Sources — `cocoindex.sources`

- `LocalFile(path: str, binary=False, included_patterns=None, excluded_patterns=None, max_file_size=None)` — KTable with `filename` (key), `content`. [AST:python/cocoindex/sources/_engine_builtin_specs.py:L10]
- `GoogleDrive(service_account_credential_path, root_folder_ids, binary=False, included_patterns=None, excluded_patterns=None, max_file_size=None, recent_changes_poll_interval=None)` [AST:python/cocoindex/sources/_engine_builtin_specs.py:L30]
- `AmazonS3(bucket_name, prefix=None, binary=False, included_patterns=None, excluded_patterns=None, max_file_size=None, sqs_queue_url=None, redis=None, force_path_style=False)` [AST:python/cocoindex/sources/_engine_builtin_specs.py:L61]
- `AzureBlob(account_name, container_name, prefix=None, binary=False, included_patterns=None, excluded_patterns=None, max_file_size=None, sas_token=None, account_access_key=None)` [AST:python/cocoindex/sources/_engine_builtin_specs.py:L77]
- `Postgres(table_name, database=None, included_columns=None, ordinal_column=None, notification=None, filter=None)` [AST:python/cocoindex/sources/_engine_builtin_specs.py:L110]
- `RedisNotification(redis_url, redis_channel)` / `PostgresNotification(channel_name=None)` — change-capture config. [AST:python/cocoindex/sources/_engine_builtin_specs.py:L52] [AST:python/cocoindex/sources/_engine_builtin_specs.py:L102]

### Targets — `cocoindex.targets`

**Built-in specs:**

- `Postgres(database=None, table_name=None, schema=None, column_options=None)` — pgvector for fixed-dim float vectors; jsonb otherwise. [AST:python/cocoindex/targets/_engine_builtin_specs.py:L20]
- `PostgresSqlCommand(name, setup_sql, teardown_sql=None)` — attachment for arbitrary setup/teardown SQL. [AST:python/cocoindex/targets/_engine_builtin_specs.py:L29]
- `Qdrant(collection_name, connection=None)` / `QdrantConnection(grpc_url, api_key=None)` [AST:python/cocoindex/targets/_engine_builtin_specs.py:L46]
- `Pinecone(index_name, connection, namespace="", cloud="aws", region="us-east-1", batch_size=100)` / `PineconeConnection(api_key, environment=None)` [AST:python/cocoindex/targets/_engine_builtin_specs.py:L62]
- `Neo4j(connection, mapping)` / `Neo4jConnection(uri, user, password, db=None)` / `Neo4jDeclaration(connection, nodes_label, primary_key_fields, vector_indexes=())` [AST:python/cocoindex/targets/_engine_builtin_specs.py:L136]
- `FalkorDB(connection, mapping)` / `FalkorDBConnection(uri, graph=None)` / `FalkorDBDeclaration(...)` [AST:python/cocoindex/targets/_engine_builtin_specs.py:L163]
- `Ladybug(connection, mapping)` / `LadybugConnection(api_server_url)` / `LadybugDeclaration(connection, nodes_label, primary_key_fields)` [AST:python/cocoindex/targets/_engine_builtin_specs.py:L188]
- `Kuzu`, `KuzuConnection`, `KuzuDeclaration` — **retired**, aliases for `Ladybug*`. [AST:python/cocoindex/targets/_engine_builtin_specs.py:L205]

**Graph-mapping types:**

- `Nodes(label: str)` / `Relationships(rel_type: str, source: NodeFromFields, target: NodeFromFields)` [AST:python/cocoindex/targets/_engine_builtin_specs.py:L101] [AST:python/cocoindex/targets/_engine_builtin_specs.py:L110]
- `NodeFromFields(label, fields: list[TargetFieldMapping])` [AST:python/cocoindex/targets/_engine_builtin_specs.py:L84]
- `ReferencedNode(label, primary_key_fields, vector_indexes=())` [AST:python/cocoindex/targets/_engine_builtin_specs.py:L92]
- `TargetFieldMapping(source: str, target: str | None = None)` [AST:python/cocoindex/targets/_engine_builtin_specs.py:L74]
- Backward-compat aliases: `NodeMapping = Nodes`, `RelationshipMapping = Relationships`, `NodeReferenceMapping = NodeFromFields`. [AST:python/cocoindex/targets/_engine_builtin_specs.py:L121]

**Extended target modules:**

- `cocoindex.targets.chromadb.ChromaDB(collection_name, client_type=ClientType.PERSISTENT, path=None, host=None, port=None, ssl=False, api_key=None, tenant=..., database=..., hnsw_config=None, document_field=None)` [AST:python/cocoindex/targets/chromadb.py:L34] · `ClientType`, `HnswConfig` helpers.
- `cocoindex.targets.lancedb.LanceDB(db_uri, table_name, db_options=None, num_transactions_before_optimize=50)` [AST:python/cocoindex/targets/lancedb.py:L84] · `DatabaseOptions(storage_options=None)`.
- `cocoindex.targets.doris.DorisTarget(fe_host, database, table, fe_http_port=8080, query_port=9030, username="root", password="", ...)` [AST:python/cocoindex/targets/doris.py:L105] — with `DorisError` hierarchy (`DorisConnectionError`, `DorisAuthError`, `DorisStreamLoadError`, `DorisSchemaError`) and `RetryConfig`.
- `cocoindex.targets.turbopuffer.Turbopuffer(namespace_name, api_key, region="gcp-us-central1")` [AST:python/cocoindex/targets/turbopuffer.py:L36]
- `cocoindex.targets.pinecone` — provides the connector for the built-in `Pinecone` spec (no new public spec class).

### Functions — `cocoindex.functions`

- `ParseJson()` — parses text to JSON. [AST:python/cocoindex/functions/_engine_builtin_specs.py:L10]
- `DetectProgrammingLanguage()` — detects language from filename. [AST:python/cocoindex/functions/_engine_builtin_specs.py:L23]
- `SplitRecursively(custom_languages=[])` — hierarchical text splitter. Spec fields only; runtime args (`chunk_size`, `min_chunk_size`, `chunk_overlap`, `language`) are passed through `transform(...)`. Returns _KTable_ with `location`, `text`, `start`, `end`. [AST:python/cocoindex/functions/_engine_builtin_specs.py:L27]
- `SplitBySeparators(separators_regex=[], keep_separator="NONE", include_empty=False, trim=True)` [AST:python/cocoindex/functions/_engine_builtin_specs.py:L33]
- `EmbedText(api_type, model, address=None, output_dimension=None, expected_output_dimension=None, task_type=None, api_config=None, api_key=None)` [AST:python/cocoindex/functions/_engine_builtin_specs.py:L51]
- `ExtractByLlm(llm_spec: LlmSpec, output_type: type, instruction: str | None = None)` [AST:python/cocoindex/functions/_engine_builtin_specs.py:L64]
- `CustomLanguageSpec(language_name, separators_regex, aliases=[])` [AST:python/cocoindex/functions/_engine_builtin_specs.py:L15]
- `SentenceTransformerEmbed(model, args=None)` — requires `pip install 'cocoindex[embeddings]'`. [AST:python/cocoindex/functions/sbert.py:L12]
- `SentenceTransformerEmbedExecutor` — gpu+cache+batched executor (internal but exported for custom builds). [AST:python/cocoindex/functions/sbert.py:L38]
- `ColPaliEmbedImage(model)` / `ColPaliEmbedImageExecutor` — requires `pip install 'cocoindex[colpali]'`. [AST:python/cocoindex/functions/colpali.py:L99]
- `ColPaliEmbedQuery(model)` / `ColPaliEmbedQueryExecutor` [AST:python/cocoindex/functions/colpali.py:L178]

### Op framework — `cocoindex.op`

For authoring custom sources/functions/targets. See [references/op-framework.md](references/op-framework.md).

- `FunctionSpec`, `SourceSpec`, `TargetSpec`, `TargetAttachmentSpec`, `DeclarationSpec` — dataclass-like spec base classes via `SpecMeta`. [AST:python/cocoindex/op.py:L75] [AST:python/cocoindex/op.py:L71] [AST:python/cocoindex/op.py:L79] [AST:python/cocoindex/op.py:L83] [AST:python/cocoindex/op.py:L87]
- `OpCategory` Enum — FUNCTION, SOURCE, TARGET, DECLARATION, TARGET_ATTACHMENT. [AST:python/cocoindex/op.py:L40]
- `ArgRelationship` Enum — `EMBEDDING_ORIGIN_TEXT`, `CHUNKS_BASE_TEXT`, `RECTS_BASE_IMAGE`. [AST:python/cocoindex/op.py:L126]
- `OpArgs(gpu=False, cache=False, batching=False, max_batch_size=None, behavior_version=None, timeout=None, arg_relationship=None)` [AST:python/cocoindex/op.py:L135]
- `executor_class(**args)` — decorator turning a class into a function executor. Expects a `spec: YourSpecClass` class attribute with type annotation. [AST:python/cocoindex/op.py:L448]
- `function(**args)` — decorator wrapping a plain function as a CocoIndex function op. Converts snake_case to CamelCase for `op_kind`. [AST:python/cocoindex/op.py:L489]
- `source_connector(*, spec_cls, key_type=Any, value_type=Any)` — decorator registering a source connector class (`create`, `list`, `get_value`, optional `provides_ordinal`). [AST:python/cocoindex/op.py:L746]
- `target_connector(*, spec_cls, persistent_key_type=Any, setup_state_cls=None)` — decorator registering a target connector class. [AST:python/cocoindex/op.py:L1073]
- `SourceReadOptions(include_ordinal=False, include_content_version_fp=False, include_value=False)` [AST:python/cocoindex/op.py:L521]
- `PartialSourceRowData[V]` — dataclass with fields `value`, `ordinal`, `content_version_fp` (all default `None`). [AST:python/cocoindex/op.py:L556]
- `PartialSourceRow[K, V]` — dataclass with fields `key: K`, `data: PartialSourceRowData[V]`. [AST:python/cocoindex/op.py:L571]
- `TargetStateCompatibility` Enum — `COMPATIBLE`, `PARTIALLY_COMPATIBLE`, `NOT_COMPATIBLE`. [AST:python/cocoindex/op.py:L811]
- `EmptyFunctionSpec` — placeholder for `@op.function`-decorated bare functions. [AST:python/cocoindex/op.py:L478]

### Query handlers — `cocoindex.query_handler`

- `QueryHandlerResultFields(embedding=[], score=None)` — metadata for CocoInsight query result introspection. [AST:python/cocoindex/query_handler.py:L11]
- `QueryInfo(embedding=None, similarity_metric=None)` [AST:python/cocoindex/query_handler.py:L31]
- `QueryOutput[R]` — dataclass with fields `results: list[R]`, `query_info: QueryInfo` (default `QueryInfo()`). [AST:python/cocoindex/query_handler.py:L44]

### Schema typing — `cocoindex.typing`

Annotated aliases used on dataclass fields and function return types to attach CocoIndex schema information:

- `Int64 = Annotated[int, TypeKind("Int64")]`
- `Float32 = Annotated[float, TypeKind("Float32")]`
- `Float64 = Annotated[float, TypeKind("Float64")]`
- `Range = Annotated[tuple[int, int], TypeKind("Range")]`
- `Json = Annotated[Any, TypeKind("Json")]`
- `LocalDateTime = Annotated[datetime, TypeKind("LocalDateTime")]`
- `OffsetDateTime = Annotated[datetime, TypeKind("OffsetDateTime")]`
- `Vector[T, Dim]` — alias for `Annotated[NDArray[T] | list[T], VectorInfo(dim=Dim)]`. Usage: `Vector[np.float32]`, `Vector[np.float32, Literal[384]]`. [AST:python/cocoindex/typing.py:L49]

### Utils — `cocoindex.utils`

- `get_target_default_name(flow: Flow, target_name: str, delimiter: str = "__") -> str` [AST:python/cocoindex/utils.py:L5] — `{app_namespace}{delimiter}{flow.name}{delimiter}{target_name}`.
- `get_target_storage_default_name` — **DEPRECATED** alias. [AST:python/cocoindex/utils.py:L18]

## Full Type Definitions

See [references/flow-api.md](references/flow-api.md), [references/settings-auth.md](references/settings-auth.md), and [references/sources-targets-functions.md](references/sources-targets-functions.md) for the complete type reference.

## Full Integration Patterns

**LLM-aware extraction pipeline (source → split → embed → collect → export):**
This is the canonical cocoindex pattern, repeated across most examples: `flow_builder.add_source()` → `DataSlice.row()` (per-document scope) → `doc["content"].transform(SplitRecursively(), ...)` (per-chunk KTable) → `chunk["text"].transform(SentenceTransformerEmbed(...))` → `collector.collect(...)` → top-level `collector.export(target_spec, primary_key_fields=..., vector_indexes=[...])`. [EXT:https://cocoindex.io/docs/getting_started/quickstart]

**LLM structured extraction pattern:**
`collector.collect(..., extracted=doc["text"].transform(ExtractByLlm(llm_spec=LlmSpec(api_type=LlmApiType.OPENAI, model="gpt-4o"), output_type=MyDataclass, instruction="...")))`. Define clear dataclasses — `output_type` schema is fed to the LLM. [EXT:https://cocoindex.io/docs/ops/functions#extractbyllm]

**Graph target pattern (Neo4j / FalkorDB / Ladybug):**
Two collectors — one exports `Nodes(label="Document")`, another exports `Relationships(rel_type="MENTIONS", source=NodeFromFields(label="Document", fields=[...]), target=NodeFromFields(label="Entity", fields=[...]))`. Use `flow_builder.declare(Neo4jDeclaration(connection=..., nodes_label="Entity", primary_key_fields=[...], vector_indexes=[...]))` to configure referenced nodes that aren't produced by any specific collector. Connection via `cocoindex.add_auth_entry("my_graph_conn", Neo4jConnection(...))`. [AST:python/cocoindex/targets/_engine_builtin_specs.py:L136]

**Live update loop pattern:**
```python
with cocoindex.FlowLiveUpdater(demo_flow, FlowLiveUpdaterOptions(live_mode=True, print_stats=True)) as updater:
    while True:
        updates = updater.next_status_updates()
        for source in updates.updated_sources:
            run_downstream(source)
        if not updates.active_sources:
            break
```
Sources with change capture (Postgres logical-replication, S3 event notifications, Google Drive polling, or `refresh_interval`) continuously push updates; one-time sources complete after the initial update. [EXT:https://cocoindex.io/docs/core/flow_methods]

**Custom function (two forms):**
1. **Standalone** — `@cocoindex.op.function(cache=True, behavior_version=1)` on a typed function.
2. **Spec + executor** — `class FooSpec(cocoindex.op.FunctionSpec)` with parameter fields, plus `@cocoindex.op.executor_class(cache=True, behavior_version=1, gpu=True)` on a class with `spec: FooSpec`, optional `prepare(self)`, and required `__call__(self, ...) -> ...`. [EXT:https://cocoindex.io/docs/custom_ops/custom_functions]

**Attachment pattern (Postgres SQL hooks):**
`collector.export("doc_embeddings", Postgres(table_name="doc_embeddings"), primary_key_fields=["id"], attachments=[PostgresSqlCommand(name="fts", setup_sql="CREATE INDEX IF NOT EXISTS ... USING GIN (to_tsvector('english', text));", teardown_sql="DROP INDEX IF EXISTS ...;")])` — idempotent setup/teardown SQL for capabilities not native to the target spec. [EXT:https://cocoindex.io/docs/targets/postgres]

<!-- [MANUAL:integration-notes] -->
<!-- Add custom notes here. This section is preserved during skill updates. -->
<!-- [/MANUAL:integration-notes] -->
