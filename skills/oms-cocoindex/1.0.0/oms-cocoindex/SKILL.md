---
name: oms-cocoindex
description: Build data ingestion + transformation pipelines on top of cocoindex v1.0.0 — a Python framework with a Rust engine for ultra-performant, incremental indexing (ETL, RAG, knowledge graphs, vector search). Use when authoring cocoindex v1.0.0 components — App / Environment / @lifespan / @fn / mount + TargetState reconciliation + connectors + ops. **This is a complete paradigm change from v0.3.37**; the old FlowBuilder/DataScope/DataSlice/flow_def API was wholly removed in v1.0.0 — do NOT mix vocabularies.
---

# Cocoindex v1.0.0 — Component-based Pipelines

Cocoindex authors data pipelines as Python *components* mounted into an *Environment* and orchestrated by an *App*. State is reconciled into target connectors via a `TargetState` / `TargetHandler` declarative API. Functions are decorated with `@coco.fn` (memoized, batchable, optionally GPU-runner-isolated). Lifespan-scoped resources (DB pools, embedders) are provided via `@coco.lifespan` and retrieved with `coco.use_context(KEY)`. Persistent state lives in a local LMDB store at `Settings.db_path`.

**v0.3.37 → v1.0.0 paradigm shift:** the old API (`FlowBuilder`, `DataScope`, `DataSlice`, `flow_def`, `open_flow`, `transform_flow`, `cocoindex.sources.*`, `cocoindex.targets.*`, `cocoindex.functions.*`, `LlmSpec`, `LlmApiType`, `VectorSimilarityMetric`, `DatabaseConnectionSpec`, `Postgres`-backed state) is **entirely removed**. There is no `flow.py`, no `op.py`, no `index.py`, no `llm.py`, no `lib.py`, no `auth_registry.py`. Migration is a full rewrite, not a rename pass — see the [migration section](#migration-from-v0337) for the new vocabulary.

## Quick Start

```python
# pip install cocoindex
import asyncio, pathlib
from typing import AsyncIterator, Annotated
from dataclasses import dataclass

import asyncpg
import cocoindex as coco
from cocoindex.connectors import localfs, postgres
from cocoindex.ops.text import RecursiveSplitter
from cocoindex.ops.sentence_transformers import SentenceTransformerEmbedder
from cocoindex.resources.chunk import Chunk
from cocoindex.resources.file import FileLike, PatternFilePathMatcher
from cocoindex.resources.id import IdGenerator
from numpy.typing import NDArray

# Lifespan-scoped resources (created once per environment, reused across components)
PG_DB    = coco.ContextKey[asyncpg.Pool]("pg_db")
EMBEDDER = coco.ContextKey[SentenceTransformerEmbedder]("embedder", detect_change=True)

@coco.lifespan
async def env_lifespan(builder: coco.EnvironmentBuilder) -> AsyncIterator[None]:
    async with await asyncpg.create_pool("postgres://localhost/mydb") as pool:
        builder.provide(PG_DB, pool)
        builder.provide(EMBEDDER, SentenceTransformerEmbedder("sentence-transformers/all-MiniLM-L6-v2"))
        yield

@dataclass
class DocEmbedding:
    id: int; filename: str; chunk_start: int; chunk_end: int
    text: str
    embedding: Annotated[NDArray, EMBEDDER]   # vector schema resolved from the ContextKey

# Per-chunk component (memoization implicit via memo=True on the parent)
@coco.fn
async def process_chunk(chunk: Chunk, filename: pathlib.PurePath, id_gen: IdGenerator,
                        table: postgres.TableTarget[DocEmbedding]) -> None:
    table.declare_row(row=DocEmbedding(
        id=await id_gen.next_id(chunk.text),
        filename=str(filename),
        chunk_start=chunk.start.char_offset,
        chunk_end=chunk.end.char_offset,
        text=chunk.text,
        embedding=await coco.use_context(EMBEDDER).embed(chunk.text),
    ))

@coco.fn(memo=True)
async def process_file(file: FileLike, table: postgres.TableTarget[DocEmbedding]) -> None:
    text = await file.read_text()
    chunks = RecursiveSplitter().split(text, chunk_size=2000, chunk_overlap=500, language="markdown")
    id_gen = IdGenerator()
    await coco.map(process_chunk, chunks, file.file_path.path, id_gen, table)

@coco.fn
async def app_main(sourcedir: pathlib.Path) -> None:
    target = await postgres.mount_table_target(
        PG_DB,
        table_name="doc_embeddings",
        table_schema=await postgres.TableSchema.from_class(DocEmbedding, primary_key=["id"]),
    )
    target.declare_vector_index(column="embedding")
    files = localfs.walk_dir(sourcedir, recursive=True,
                             path_matcher=PatternFilePathMatcher(included_patterns=["**/*.md"]))
    await coco.mount_each(process_file, files.items(), target)

app = coco.App(coco.AppConfig(name="MyApp"), app_main, sourcedir=pathlib.Path("./docs"))
```

Run with: `cocoindex update main.py` (one-shot) or `cocoindex update main.py -L` (live). Set `COCOINDEX_DB=/path/to/state.lmdb` for the local state store. Source: [AST:python/cocoindex/__init__.py:L13] · [AST:examples/text_embedding/main.py:L1]

<!-- [MANUAL:quick-start-notes] -->
<!-- Add custom notes here. This section is preserved during skill updates. -->
<!-- [/MANUAL:quick-start-notes] -->

## Common Workflows

**Define and mount a top-level `App`:**
`coco.App(coco.AppConfig(name="..."), app_main, *args, **kwargs)` — `app_main` is a `@coco.fn`-decorated function. Run via `app.update()` (returns `UpdateHandle`) or `app.update_blocking()`. [AST:python/cocoindex/_internal/app.py:L208]

**Lifespan-scoped resources:**
`@coco.lifespan` decorates a function `(EnvironmentBuilder) -> Iterator[None] | AsyncIterator[None]`. Use `builder.provide(KEY, value)` (or `provide_async_with(KEY, async_cm)`) to register resources. Retrieve with `coco.use_context(KEY)` from inside any `@coco.fn`. [AST:python/cocoindex/_internal/environment.py:L452] · [AST:python/cocoindex/_internal/component_ctx.py:L273]

**Mount a sub-component:**
`await coco.mount(process_fn, *args)` — runs in background, returns `ComponentMountHandle`.
`await coco.mount_each(process_fn, items, ...)` — one component per item; `items` is `Iterable[(key, value)]`, `AsyncIterable`, `LiveMapFeed`, or `LiveMapView`.
`result = await coco.use_mount(processor_fn, *args)` — mount and wait for the result; the child cannot refresh independently of the parent.
[AST:python/cocoindex/_internal/api.py:L349] · [:L445] · [:L245]

**Mount a target (declarative state reconciliation):**
`provider = await coco.mount_target(target_state)` — sugar over `use_mount` + `declare_target_state_with_child`. Connector-specific helpers (`postgres.mount_table_target`, `qdrant.mount_collection_target`, `lancedb.mount_table_target`, …) wrap this. [AST:python/cocoindex/_internal/api.py:L566]

**Concurrent map (no component, no checkpoint):**
`await coco.map(fn, items, *passthrough)` — pure async TaskGroup over an iterable; results returned as a list. Use when you need parallelism but not memoization or sub-component lifecycle. [AST:python/cocoindex/_internal/api.py:L532]

**LLM extraction (LiteLLM-based):**
`from cocoindex.ops.litellm import LiteLLMEmbedder; embedder = LiteLLMEmbedder("text-embedding-ada-002")`. Replaces v0.3.37's `cocoindex.functions.ExtractByLlm` + `LlmSpec`. [AST:python/cocoindex/ops/litellm.py:L22]

**Sentence-transformers embedding:**
`from cocoindex.ops.sentence_transformers import SentenceTransformerEmbedder; SentenceTransformerEmbedder("model-name")`. Replaces v0.3.37's `cocoindex.functions.SentenceTransformerEmbed`. [AST:python/cocoindex/ops/sentence_transformers.py:L25]

**Text chunking:**
`from cocoindex.ops.text import RecursiveSplitter, SeparatorSplitter, CustomLanguageConfig, detect_code_language`. Replaces v0.3.37's `cocoindex.functions.SplitRecursively` / `SplitBySeparators`. [AST:python/cocoindex/ops/text.py:L19]

**Lifecycle & utilities:**
```python
# Dual-mode runtime context manager — same call works for sync and async drivers
with coco.runtime():
    app.update_blocking()
# or:
async with coco.runtime():
    await app.update()

# Sync entry points for non-async callers
coco.start_blocking()
try:
    app.update_blocking()
finally:
    coco.stop_blocking()

# Async equivalents and direct env access
await coco.start()                # start default environment + enter lifespan
env = await coco.default_env()    # the default environment (starting it if needed)
await coco.stop()                 # exit lifespan + stop default environment

# Stream progress for a long-running update (consumes the handle)
handle = app.update()
result = await coco.show_progress(handle)

# Deterministic identifiers from content dependencies (memoized; idempotent)
chunk_id   = await coco.resources.id.generate_id(_dep=chunk.text)
chunk_uuid = await coco.resources.id.generate_uuid(_dep=chunk.text)

# Detect a source file's language (for splitter pipelines)
lang = coco.ops.text.detect_code_language(filename="foo.py")
```
Provenance: [AST:python/cocoindex/_internal/api.py:L603] [:L608] [:L613] [:L618] [:L623] [:L655] · [AST:python/cocoindex/_internal/app.py:L194] · [AST:python/cocoindex/resources/id.py:L31] [:L61] · [AST:python/cocoindex/ops/text.py:L19]

**Component-context helpers (inside `@coco.fn`):**
`ctx = coco.get_component_context()` returns the current `ComponentContext`; raises `RuntimeError` outside a component. Build scoped keys with `subpath = coco.component_subpath(*key_parts)` — pass as the first positional argument to `mount` / `use_mount`, or use it as a context manager. Push a scoped error handler with `async with coco.exception_handler(handler): ...` to catch exceptions raised by background-mounted children within the block. [AST:python/cocoindex/_internal/component_ctx.py:L305] [:L198] [:L331]

**Advanced extension hooks** (most callers don't need these — they exist for connector / runtime authors):

- `coco.register_root_target_states_provider(name, handler)` — register a new root `TargetStateProvider` (used by connector authors building target backends). [AST:python/cocoindex/_internal/target_state.py:L305]
- `coco.is_non_existence(obj)` — `TypeIs` guard for the `NON_EXISTENCE` sentinel when implementing memo-state branches. [AST:python/cocoindex/_internal/typing.py:L63]
- `coco.memo_fingerprint(obj)` and `coco.register_memo_key_function(typ, key_fn, *, state_fn=None)` — customize which fields participate in memoization keys for a custom type. [AST:python/cocoindex/_internal/memo_fingerprint.py:L361] [:L155]
- `coco.unpickle_safe(cls)` and `coco.serialize_by_pickle(cls)` — class decorators for pickle-safe round-trips of component state. [AST:python/cocoindex/_internal/serde.py:L128] [:L151]
- `coco.is_live_component_class(cls)` — runtime test for `LiveComponent`-shaped classes. [AST:python/cocoindex/_internal/live_component.py:L35]
- `coco.resources.schema.get_vector_schema(obj)` and `get_multi_vector_schema(obj)` — introspect a vector-schema provider attached to an `Annotated[...]` type (used when wiring a custom `Embedder` to a target column). [AST:python/cocoindex/resources/schema.py:L33] [:L58]

## Key API Summary

| Export | Kind | Purpose | Provenance |
|---|---|---|---|
| `App[P, R]` | class | Top-level pipeline runner. `App(name_or_config, main_fn, *args, **kwargs)`. Methods: `update()`, `update_blocking()`, `drop()`, `drop_blocking()`. | [AST:python/cocoindex/_internal/app.py:L208] |
| `AppConfig` | dataclass | `AppConfig(name, environment=default_env, max_inflight_components=None)`. | [AST:python/cocoindex/_internal/app.py:L202] |
| `Environment` | class | CocoIndex runtime environment. Owns settings, context provider, event loop, and exception handler. `__init__(settings, *, name=None, context_provider=None, event_loop=None, exception_handler=None, info=None)`. | [AST:python/cocoindex/_internal/environment.py:L183] |
| `EnvironmentBuilder` | class | Lifespan builder. `provide(key, value)`, `provide_with(key, ctxmgr)`, `provide_async_with(key, async_ctxmgr)`, `set_exception_handler(handler)`. | [AST:python/cocoindex/_internal/environment.py:L87] |
| `LifespanFn` | type alias | `Callable[[EnvironmentBuilder], Iterator[None] \| AsyncIterator[None]]`. | [AST:python/cocoindex/_internal/environment.py:L118] |
| `lifespan` | decorator | `@coco.lifespan` registers an environment lifespan. Optional parens. | [AST:python/cocoindex/_internal/environment.py:L452] |
| `fn` | decorator namespace | `@coco.fn` (preserves sync/async), `@coco.fn(memo=True)`, `@coco.fn(batching=True, max_batch_size=N, runner=GPU)`, `@coco.fn(version=N, logic_tracking="full"\|"self"\|None, deps=...)`. `@coco.fn.as_async(...)` always yields async. | [AST:python/cocoindex/_internal/function.py:L1578] [AST:python/cocoindex/_internal/function.py:L1811] |
| `LogicTracking` | type alias | `Literal["full", "self"] \| None` — value type of the `logic_tracking=` kwarg on `@coco.fn`. `"full"` (default) tracks own code + transitive children, `"self"` tracks own code only, `None` disables tracking (incompatible with `deps`). | [AST:python/cocoindex/_internal/function.py:L65] |
| `mount` | async fn | `await coco.mount(processor_fn, *args, **kwargs) -> ComponentMountHandle`. | [AST:python/cocoindex/_internal/api.py:L349] |
| `mount_each` | async fn | `await coco.mount_each(fn, items, *args) -> ComponentMountHandle`. | [AST:python/cocoindex/_internal/api.py:L445] |
| `mount_target` | async fn | `await coco.mount_target(target_state) -> TargetStateProvider[ValueT, OptChildHandlerT]`. | [AST:python/cocoindex/_internal/api.py:L566] |
| `use_mount` | async fn | `result = await coco.use_mount(processor_fn, *args) -> R`. Result-bearing mount. | [AST:python/cocoindex/_internal/api.py:L245] |
| `map` | async fn | `await coco.map(fn, items, *args) -> list[R]`. Concurrent fan-out, no component. | [AST:python/cocoindex/_internal/api.py:L532] |
| `start` / `stop` | async fns | Start/stop the default environment. | [AST:python/cocoindex/_internal/api.py:L603] [:L608] |
| `start_blocking` / `stop_blocking` | fns | Sync variants. | [AST:python/cocoindex/_internal/api.py:L613] [:L618] |
| `runtime()` | dual-mode ctxmgr | `with coco.runtime(): ...` or `async with coco.runtime(): ...`. | [AST:python/cocoindex/_internal/api.py:L655] |
| `Runner` / `GPU` | class / singleton | Abstract base for execution runners. `GPU` is a `GPURunner()` singleton — pass `runner=GPU` to `@coco.fn`. Enable subprocess isolation with `COCOINDEX_RUN_GPU_IN_SUBPROCESS=1`. | [AST:python/cocoindex/_internal/runner.py:L34] [:L282] |
| `TargetState[OptChildHandlerT]` | class | Bundled (provider, key, value) triple. Built via `TargetStateProvider.target_state(key, value)`. | [AST:python/cocoindex/_internal/target_state.py:L248] |
| `TargetStateProvider[ValueT, OptChildHandlerT, MaybePendingS]` | class | Provider for target states. `target_state(key, value)`, `attachment(att_type)`, `memo_key`. | [AST:python/cocoindex/_internal/target_state.py:L208] |
| `TargetHandler[ValueT_contra, TrackingRecordT, OptChildHandlerT_co]` | Protocol | `reconcile(key, desired_target_state, prev_possible_records, prev_may_be_missing) -> TargetReconcileOutput \| None`. | [AST:python/cocoindex/_internal/target_state.py:L197] |
| `TargetActionSink[ActionT, OptChildHandlerT]` | class | Wraps a sink fn. `from_fn(fn)` / `from_async_fn(async_fn)` static constructors. | [AST:python/cocoindex/_internal/target_state.py:L143] |
| `TargetReconcileOutput[ActionT, TrackingRecordT, OptChildHandlerT]` | NamedTuple | `(action, sink, tracking_record, child_invalidation)`. | [AST:python/cocoindex/_internal/target_state.py:L188] |
| `declare_target_state(target_state)` | fn | Declare a state in the current component context. | [AST:python/cocoindex/_internal/target_state.py:L265] |
| `declare_target_state_with_child(target_state)` | fn | Declare with a child handler; returns `PendingTargetStateProvider[ValueT, OptChildHandlerT]`. | [AST:python/cocoindex/_internal/target_state.py:L282] |
| `register_root_target_states_provider(name, handler)` | fn | Register a root provider; returns `TargetStateProvider`. | [AST:python/cocoindex/_internal/target_state.py:L305] |
| `LiveComponent` | runtime Protocol | `process()` and `process_live(operator)` methods. | [AST:python/cocoindex/_internal/live_component.py:L28] |
| `LiveComponentOperator` | class | `update_full()`, `update(subpath, fn, *args)`, `delete(subpath)`, `mark_ready()`. | [AST:python/cocoindex/_internal/live_component.py:L46] |
| `LiveMapFeed[K, V]` / `LiveMapView[K, V]` | runtime Protocols | `watch(subscriber)`; `LiveMapView` adds `__aiter__`. | [AST:python/cocoindex/_internal/live_component.py:L108] [:L119] |
| `LiveMapSubscriber[K, V]` | class | `update_all`, `mark_ready`, `update(key, value)`, `delete(key)`. | [AST:python/cocoindex/_internal/live_component.py:L130] |
| `ComponentContext` | dataclass | Internal context (frozen, slots). Use `coco.get_component_context()` to obtain; `ctx.attach()` to re-bind on another thread. | [AST:python/cocoindex/_internal/component_ctx.py:L55] |
| `ComponentSubpath` | class | `coco.component_subpath(*key_parts)`. Pass as first arg to `mount`/`use_mount`, or use as a context manager. Supports `/` chaining. | [AST:python/cocoindex/_internal/component_ctx.py:L142] |
| `component_subpath(*key_parts)` | fn | Convenience wrapper around `ComponentSubpath(...)`. | [AST:python/cocoindex/_internal/component_ctx.py:L198] |
| `use_context(key)` | fn | Retrieve a value provided in lifespan via `ContextKey`. Tracks change if `key.detect_change=True`. | [AST:python/cocoindex/_internal/component_ctx.py:L273] |
| `get_component_context()` | fn | Get current `ComponentContext`. Raises `RuntimeError` outside a component. | [AST:python/cocoindex/_internal/component_ctx.py:L305] |
| `exception_handler(handler)` | async ctxmgr | Push an exception handler for background-mounted components within scope. | [AST:python/cocoindex/_internal/component_ctx.py:L331] |
| `ContextKey[T]` | class | Generic `ContextKey` parametrized by `T`; constructor takes `(key: str, *, detect_change: bool = False)`. Keys are globally unique per process. | [AST:python/cocoindex/_internal/context_keys.py:L99] |
| `ContextProvider` | class | Internal — owned by `Environment`. `provide(key, value)`, `get(key)`, `provide_with`, `provide_async_with`. | [AST:python/cocoindex/_internal/context_keys.py:L124] |
| `Settings` | dataclass | `Settings(db_path=None, global_execution_options=None, lmdb_max_dbs=1024, lmdb_map_size=4 GiB)`. `Settings.from_env(db_path=None)` reads `COCOINDEX_*` env vars. | [AST:python/cocoindex/setting.py:L44] |
| `ServerSettings` | dataclass | `ServerSettings(address="127.0.0.1:49344", cors_origins=None)`. `from_env()` and static `parse_cors_origins(s)`. | [AST:python/cocoindex/setting.py:L93] |
| `GlobalExecutionOptions` | dataclass | `(source_max_inflight_rows=1024, source_max_inflight_bytes=None)`. | [AST:python/cocoindex/setting.py:L12] |
| `QueryHandlerInfo` | dataclass | `(result_fields: QueryHandlerResultFields \| None = None)`. **NEW in v1.0.0.** | [AST:python/cocoindex/query_handler.py:L21] |
| `QueryHandlerResultFields` | dataclass | `(embedding: list[str] = [], score: str \| None = None)`. | [AST:python/cocoindex/query_handler.py:L10] |
| `QueryInfo` | dataclass | `(embedding: list[float] \| NDArray[np.float32] \| None = None)`. v0.3.37's `similarity_metric` field is **removed**. | [AST:python/cocoindex/query_handler.py:L30] |
| `QueryOutput[R]` | dataclass | `(results: list[R], query_info: QueryInfo = QueryInfo())`. | [AST:python/cocoindex/query_handler.py:L43] |
| `cli` | click.Group | The `cocoindex` CLI entry point. Subcommands: `ls`, `show`, `update`, `drop`, `init`. | [AST:python/cocoindex/cli.py:L505] |

See:
- [Component API reference](references/component-api.md) — App, Environment, mount, fn, lifespan, runtime
- [Target state reconciliation](references/target-state.md) — TargetState, TargetHandler, declare_target_state
- [Live components](references/live-components.md) — LiveComponent, LiveMapFeed, LiveMapView
- [Connectors](references/connectors.md) — postgres, qdrant, lancedb, surrealdb, sqlite, doris, kafka, localfs, amazon_s3, google_drive
- [Ops](references/ops.md) — litellm, sentence_transformers, text, entity_resolution
- [Resources](references/resources.md) — Chunk, FileLike, IdGenerator, schema providers
- [Settings & CLI](references/settings-cli.md) — Settings, ServerSettings, query_handler, cocoindex CLI

<!-- [MANUAL:api-notes] -->
<!-- Add custom notes here. This section is preserved during skill updates. -->
<!-- [/MANUAL:api-notes] -->

## Key Types

```python
# Component-context plumbing
StableKey = None | bool | int | str | bytes | uuid.UUID | Symbol | tuple[StableKey, ...]
StablePath              # core.StablePath wrapper; supports / chaining
ROOT_PATH               # singleton StablePath()
Symbol                  # core.Symbol — opaque marker (used in subpaths)

# Update lifecycle
UpdateStatus            # StrEnum: "running" | "ready"
ComponentStats          # NamedTuple(num_execution_starts, num_unchanged, num_adds, num_deletes, num_reprocesses, num_errors). Properties: num_processed, num_finished, num_in_progress
UpdateStats             # NamedTuple(by_component: dict[str, ComponentStats]). Property: total
UpdateSnapshot[R]       # NamedTuple(stats, status, result)
UpdateHandle[R]         # Awaitable[R]; .stats(), .watch() (AsyncIterator[UpdateSnapshot])
DropHandle              # returned by App.drop()

# Typestate (static-only — phantom types)
PendingS                # marker for "pending" target state providers
ResolvedS               # marker for "resolved"
MaybePendingS           # TypeVar(PendingS, ResolvedS, default=ResolvedS)
ResolvesTo[ResolvedT]   # generic mixin used in use_mount() return-type bridge

# Non-existence sentinel
NonExistenceType        # singleton type
NON_EXISTENCE           # the singleton instance
is_non_existence(obj)   # TypeIs[NonExistenceType]
MemoStateOutcome        # NamedTuple(state, memo_valid=False)

# Memoization
NotMemoKeyable          # base for types that must not be used as memo keys
memo_fingerprint(obj)   # core.Fingerprint
register_memo_key_function(typ, key_fn, *, state_fn=None)
```

Provenance: [AST:python/cocoindex/_internal/stable_path.py:L9] [:L16] [:L59] · [AST:python/cocoindex/_internal/typing.py:L11] [:L47] [:L67] · [AST:python/cocoindex/_internal/update_stats.py:L9] · [AST:python/cocoindex/_internal/pending_marker.py:L74] [:L89] [:L115] [:L118] · [AST:python/cocoindex/_internal/memo_fingerprint.py:L136] [:L155] [:L361]

## Architecture at a Glance

- **Public API entry point:** `python/cocoindex/__init__.py` does `from ._internal.api import *` and re-exports `_internal.api.__all__` (~74 symbols). Always import as `import cocoindex as coco`. [AST:python/cocoindex/__init__.py:L13]
- **API hub:** `python/cocoindex/_internal/api.py` is the canonical re-export module. It defines `mount`, `mount_each`, `mount_target`, `use_mount`, `map`, `start`, `stop`, `start_blocking`, `stop_blocking`, `default_env`, `runtime`, `ComponentMountHandle`, and re-exports the rest. [AST:python/cocoindex/_internal/api.py:L669]
- **Component runtime:** `_internal/app.py` (App, AppConfig, UpdateHandle, DropHandle, show_progress), `_internal/environment.py` (Environment, EnvironmentBuilder, lifespan, start/stop), `_internal/runner.py` (Runner, GPU singleton).
- **Component model:** `_internal/function.py` (`@coco.fn` builder + SyncFunction/AsyncFunction Protocols), `_internal/component_ctx.py` (ComponentContext, ComponentSubpath, exception_handler, use_context).
- **Target reconciliation:** `_internal/target_state.py` — TargetState/TargetStateProvider/TargetHandler/TargetActionSink + declare_target_state / declare_target_state_with_child / register_root_target_states_provider.
- **Live components:** `_internal/live_component.py` — LiveComponent, LiveComponentOperator, LiveMapFeed/View, LiveMapSubscriber.
- **Plumbing:** `_internal/context_keys.py` (ContextKey, ContextProvider), `_internal/stable_path.py` (StablePath/StableKey/Symbol), `_internal/memo_fingerprint.py` (memo_fingerprint, NotMemoKeyable), `_internal/serde.py` (unpickle_safe, serialize_by_pickle).
- **Connectors:** `python/cocoindex/connectors/{amazon_s3,doris,google_drive,kafka,lancedb,localfs,postgres,qdrant,sqlite,surrealdb}` — each package re-exports its `_source.py` and/or `_target.py` `__all__`. Replaces v0.3.37 `sources.*` + `targets.*`.
- **Ops:** `python/cocoindex/ops/{litellm,sentence_transformers,text}` + `ops/entity_resolution/`. Replaces v0.3.37 `functions.*`.
- **Resources:** `python/cocoindex/resources/{chunk,embedder,file,id,schema}.py` — first-class data types referenced from connectors and `@coco.fn` signatures.
- **Storage:** state lives in **LMDB** at `Settings.db_path` (`COCOINDEX_DB` env var). v0.3.37's Postgres-backed state via `DatabaseConnectionSpec` is gone.
- **Rust engine:** `rust/` — out of scope; users author components in Python via pyo3 bindings exposed as `cocoindex._internal.core`.

## CLI

The `cocoindex` CLI is a click group ([AST:python/cocoindex/cli.py:L505]) with five subcommands ([AST:python/cocoindex/cli.py:L522] [:L561] [:L652] [:L745] [:L811]):

```sh
cocoindex -e .env -d app_dir <subcommand> ...

cocoindex ls   [APP_TARGET] [--db PATH]                 # List apps registered in the LMDB store
cocoindex show APP_TARGET [--verbose] [--persisted]     # Show app details / persisted state
cocoindex update APP_TARGET [-L|--live] [--full-reprocess] [--quiet]  # Run an update (one-shot or live)
cocoindex drop APP_TARGET [-f|--force] [--quiet]        # Drop an app's target states + state DB
cocoindex init [PROJECT_NAME] [--dir PATH]              # Scaffold a new project
```

`APP_TARGET` is a path to a `.py` file or an installed module name. The CLI resolves it via `_load_app()` ([AST:python/cocoindex/cli.py:L274]) which expects a top-level `App` instance (not a flow). `cocoindex update main.py:flow_name` syntax from v0.3.37 is **not** supported in v1.0.0.

## Migration from v0.3.37

The 0.3.37 → 1.0.0 transition is **not a rename** — every public module from v0.3.37 was deleted and replaced with a different paradigm. There is no automatic migration tool. The mapping is conceptual, not mechanical:

| v0.3.37 (gone) | v1.0.0 (replacement) |
|---|---|
| `@cocoindex.flow_def(name="...")` over `(FlowBuilder, DataScope) -> None` | `coco.App(coco.AppConfig(name="..."), main_fn, *args)` where `main_fn` is `@coco.fn`-decorated |
| `cocoindex.open_flow(name, fl_def)` | `coco.App(coco.AppConfig(name=name), main_fn, ...)` |
| `cocoindex.transform_flow()` | `@coco.fn` decorator (component-level transform) |
| `FlowBuilder.add_source(spec)` | `coco.mount_each(process_fn, source.items())` over `localfs.walk_dir`, `postgres.PgTableSource`, `kafka.topic_as_map`, etc. |
| `DataSlice.transform(fn_spec)` / `DataSlice.row()` | `await coco.map(fn, items)` for fan-out, or `await coco.mount(child_fn, *args)` for sub-components |
| `DataCollector.collect(...)` / `.export(target_name, target_spec, ...)` | `await postgres.mount_table_target(...).declare_row(row)` (or per-connector equivalent) |
| `Flow.update()` / `Flow.update_async()` | `app.update_blocking()` / `await app.update()` |
| `Flow.setup()` / `Flow.drop()` | `app.update_blocking()` (setup is implicit on first run); `app.drop()` / `app.drop_blocking()` |
| `FlowLiveUpdater(fl)` with `start()`/`wait()` | `app.update(live=True)` returns an `UpdateHandle`; iterate `handle.watch()` for `UpdateSnapshot`s |
| `cocoindex.functions.SplitRecursively` / `SplitBySeparators` | `cocoindex.ops.text.RecursiveSplitter` / `SeparatorSplitter` |
| `cocoindex.functions.SentenceTransformerEmbed(model=...)` | `cocoindex.ops.sentence_transformers.SentenceTransformerEmbedder("model")` |
| `cocoindex.functions.ExtractByLlm(llm_spec=LlmSpec(api_type=LlmApiType.OPENAI, model=..., api_key=...))` | `cocoindex.ops.litellm.LiteLLMEmbedder("text-embedding-ada-002", api_key=...)` (LiteLLM-based dispatch; provider config is per-model string) |
| `cocoindex.functions.ParseJson` / `DetectProgrammingLanguage` | regular Python (`json.loads`); `cocoindex.ops.text.detect_code_language(filename=...)` |
| `cocoindex.sources.LocalFile` / `GoogleDrive` / `AmazonS3` / `AzureBlob` / `Postgres` | `cocoindex.connectors.{localfs,google_drive,amazon_s3,…,postgres}.*` (no built-in AzureBlob; use `localfs` patterns or write a connector) |
| `cocoindex.targets.Postgres` / `Qdrant` / `Pinecone` / `Neo4j` / `FalkorDB` / `Ladybug` / `LanceDB` / `ChromaDB` / `DorisTarget` / `Turbopuffer` | `cocoindex.connectors.{postgres,qdrant,lancedb,doris,sqlite,surrealdb,kafka}` (no built-in Pinecone, Neo4j, FalkorDB, ChromaDB, Turbopuffer in v1.0.0 — write a connector or upstream a request) |
| `LlmSpec` / `LlmApiType` / `VertexAiConfig` / `OpenAiConfig` / `AzureOpenAiConfig` | LiteLLM model strings (`"vertex_ai/textembedding-gecko"`, `"azure/<deployment>"`, etc.) passed to `LiteLLMEmbedder`. Provider config flows through `**kwargs` (e.g., `api_key`, `api_base`). |
| `VectorSimilarityMetric` / `VectorIndexDef` / `FtsIndexDef` / `IndexOptions` | per-connector. E.g., `postgres.TableTarget.declare_vector_index(column="embedding")` lives on the target itself, not as a top-level type. |
| `Settings(database=DatabaseConnectionSpec(url=...))` | `Settings(db_path=os.PathLike)` — state moved from Postgres to local LMDB. `COCOINDEX_DB` env var. |
| `cocoindex.auth_registry.add_auth_entry / ref_auth_entry` | gone; pass credentials directly via `EnvironmentBuilder.provide(KEY, …)` and `coco.use_context(KEY)` |
| `cocoindex.utils.get_target_default_name` / `get_target_storage_default_name` | gone; connectors expose names via their target-spec helpers |
| `add_flow_def(name, fl_def)` (deprecated in v0.3.37) | gone; no replacement needed |
| `remove_flow(fl)` (deprecated in v0.3.37) / `Flow.close()` | gone; `app.drop()` handles teardown |
| `cocoindex.storages` (deprecated alias for `cocoindex.targets`) | gone; both `targets` and `storages` are removed |
| `cocoindex.cli` subcommand semantics (`ls`, `show`, `setup`, `drop`, `update`, `evaluate`, `server`) | reduced to `ls`, `show`, `update`, `drop`, `init`. `setup`/`evaluate`/`server` are gone; `update` does setup implicitly. |

**Storage migration:** v0.3.37 stored flow state in Postgres tables. v1.0.0 stores everything in a local LMDB file at `Settings.db_path` (`COCOINDEX_DB` env var). Existing v0.3.37 state cannot be read by v1.0.0 — plan a re-index, not an in-place upgrade.

## Gotchas

- **Cocoindex v1.0.0 does NOT preserve API stability across minor versions** despite the 1.0 tag. The 0.3 → 1.0 jump itself was a wholesale rewrite; treat future minor versions cautiously and pin in your `requirements.txt` / `pyproject.toml`.
- **All `mount*`, `App.update`, `App.drop`, `start`/`stop`, `coco.map` are async** — wrap in `asyncio.run()` or use `app.update_blocking()` / `app.drop_blocking()` / `start_blocking()` / `stop_blocking()` for sync entry points.
- **`@coco.fn` preserves sync/async** — sync function → `SyncFunction`, async function → `AsyncFunction`. `@coco.fn(batching=True)` requires async; for sync underlying fns that need batching, use `@coco.fn.as_async(batching=True)`.
- **`logic_tracking` controls memoization invalidation:** `"full"` (default) tracks own code + transitive children; `"self"` tracks own code only; `None` disables tracking (incompatible with `deps`).
- **`deps` is snapshotted at decoration time**, not per-call. For per-call values pass them as regular function arguments; reserve `deps` for module-level constants like prompts or model identifiers.
- **`ContextKey` keys must be globally unique per process** — re-using a key string raises `ValueError`. Use module-qualified names (`"my_module.PG_DB"`) or namespaced strings.
- **`use_mount` requires the child's result to satisfy `ResolvesTo[T]`** — the static type checker uses `ResolvesTo` to bridge "pending provider returned by child" to "resolved provider visible to parent." If you build custom wrappers, inherit from `ResolvesTo` and parameterize over `MaybePendingS`.
- **`LiveMapFeed` requires live mode** — passing a feed (no scannable snapshot, like `kafka.topic_as_map`) to `mount_each` without `app.update(live=True)` raises `TypeError`. `LiveMapView` (e.g. `localfs.walk_dir`) supports both modes.
- **`COCOINDEX_RUN_GPU_IN_SUBPROCESS=1`** opts the `GPU` runner into subprocess isolation; default is in-process on a single-worker thread pool.
- **`cocoindex.resources.*` is first-class public API** — `Chunk`, `TextPosition`, `FileLike`, `FilePath`, `FileMetadata`, `PatternFilePathMatcher`, `IdGenerator`, `UuidGenerator`, `Embedder` Protocol, `VectorSchemaProvider`, `VectorSchema`. Always import from there, not from `connectors/*` internals.
- **`cocoindex.connectorkits.*` and `cocoindex.inspect`** also exist and are referenced from connector implementations — these are not yet documented in this skill (added scope candidates for a follow-up).

<!-- [MANUAL:integration-notes] -->
<!-- Add custom notes here. This section is preserved during skill updates. -->
<!-- [/MANUAL:integration-notes] -->
