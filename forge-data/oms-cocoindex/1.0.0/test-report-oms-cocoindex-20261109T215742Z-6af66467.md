---
workflowType: 'test-skill'
skillName: 'oms-cocoindex'
skillDir: 'skills/oms-cocoindex/1.0.0/oms-cocoindex'
runId: '20261109T215742Z-6af66467'
testMode: 'naive'
forgeTier: 'Deep'
hardGate: 'passed'
testResult: 'pass'
score: '100%'
threshold: '80%'
thresholdSource: 'workflow default (80%)'
analysisConfidence: 'full'
toolingStatus: 'ok'
workspaceDrift: 'ok'
health_check_dispatched: true
testDate: '2026-11-09T21:57:42Z'
stepsCompleted: ['init', 'detect-mode', 'coverage-check', 'coherence-check', 'external-validators', 'hard-gate', 'score', 'report']
nextWorkflow: 'export-skill'
---

# Test Report: oms-cocoindex

<!--
Each stage writes its section in place of the heading below that it owns and
the placeholder comment under that heading, so every heading occurs once.
Before the result files are written, report.md §4c checks that each heading
occurs exactly once, that no placeholder comment is left and that the title
above names the skill (init.md §6c fills it): a stage that skipped its
section stops the run there. Do not change the title line, and do not
reorder or delete the headings or their placeholder comments.

Heading / owning step:
  Test Summary        → detect-mode §2
  Coverage Analysis   → coverage-check §5
  Coherence Analysis  → coherence-check §6
  External Validation → external-validators §5
  (hard gate)         → step-hard-gate reads the gap ledger; it writes the
                        Completeness Score section only when it blocks the run
  Completeness Score  → score §6, or step-hard-gate §3 on a blocked run
  Gap Report          → report §4c, rendered from the gap ledger (with the
                        Discovery Quality subsection)
-->

## Test Summary

**Skill:** oms-cocoindex
**Test Mode:** naive
**Forge Tier:** Deep

**Mode Rationale:** metadata.json records `skill_type: "single"`: an individual skill, so naive mode (API-surface coverage; coherence is structural only and not a scored category).

**Analysis Plan:**
- Coverage Check: every public export named in metadata.json and the provenance map, checked for documentation in SKILL.md and its references; at Deep tier the documented signatures are compared against the AST-backed source at the pinned commit 5fe4f37, with the inventory reader, the split-body judge and the signature judges dispatched as subagents.
- Coherence Check: structural only (naive mode): the references SKILL.md cites resolve, and the files it ships are internally consistent.

## Coverage Analysis

**Tier:** Deep
**Source Access:** full
**Source Path:** /home/armel/.skf/workspace/repos/github.com/cocoindex-io/cocoindex
**Workspace Layout:** single package
**Denominator:** barrel

**Files Analyzed:** 30

### Export Coverage

| Export | Type | Documented | Signature | Source Location | Status |
|--------|------|------------|-----------|-----------------|--------|
| `App` | class | yes | yes | python/cocoindex/_internal/app.py:208 | PASS |
| `AppConfig` | class | yes | yes | python/cocoindex/_internal/app.py:202 | PASS |
| `AsyncFunction` | - | yes | - | - | WARN |
| `CanonicalSide` | - | yes | - | - | WARN |
| `ChildTargetDef` | class | yes | - | python/cocoindex/_internal/target_state.py:95 | PASS |
| `Chunk` | - | yes | - | - | WARN |
| `ComponentContext` | class | yes | - | python/cocoindex/_internal/component_ctx.py:55 | PASS |
| `ComponentMountHandle` | class | yes | - | python/cocoindex/_internal/api.py:170 | PASS |
| `ComponentStats` | class | yes | - | python/cocoindex/_internal/update_stats.py:14 | PASS |
| `ComponentSubpath` | class | yes | yes | python/cocoindex/_internal/component_ctx.py:142 | PASS |
| `ContextKey` | class | yes | yes | python/cocoindex/_internal/context_keys.py:99 | PASS |
| `ContextProvider` | class | yes | - | python/cocoindex/_internal/context_keys.py:124 | PASS |
| `CustomLanguageConfig` | - | yes | - | - | WARN |
| `DropHandle` | class | yes | - | python/cocoindex/_internal/app.py:143 | PASS |
| `Embedder` | - | yes | - | - | WARN |
| `Environment` | class | yes | yes | python/cocoindex/_internal/environment.py:183 | PASS |
| `EnvironmentBuilder` | class | yes | yes | python/cocoindex/_internal/environment.py:87 | PASS |
| `ExceptionContext` | class | yes | yes | python/cocoindex/_internal/component_ctx.py:43 | PASS |
| `ExceptionHandler` | type | yes | - | python/cocoindex/_internal/component_ctx.py:25 | PASS |
| `ExistingCanonicalPolicy` | - | yes | - | - | WARN |
| `FileLike` | - | yes | - | - | WARN |
| `FileMetadata` | - | yes | - | - | WARN |
| `FilePathMatcher` | - | yes | - | - | WARN |
| `Function` | - | yes | - | - | WARN |
| `GPU` | const | yes | - | python/cocoindex/_internal/runner.py:282 | PASS |
| `GlobalExecutionOptions` | - | yes | - | - | WARN |
| `IdGenerator` | - | yes | - | - | WARN |
| `LazyEnvironment` | - | yes | - | - | WARN |
| `LifespanFn` | type | yes | - | python/cocoindex/_internal/environment.py:118 | PASS |
| `LiteLLMEmbedder` | - | yes | - | - | WARN |
| `LiveComponent` | class | yes | - | python/cocoindex/_internal/live_component.py:28 | PASS |
| `LiveComponentOperator` | class | yes | - | python/cocoindex/_internal/live_component.py:46 | PASS |
| `LiveMapFeed` | class | yes | - | python/cocoindex/_internal/live_component.py:108 | PASS |
| `LiveMapSubscriber` | class | yes | - | python/cocoindex/_internal/live_component.py:130 | PASS |
| `LiveMapView` | class | yes | - | python/cocoindex/_internal/live_component.py:119 | PASS |
| `LlmPairResolver` | - | yes | - | - | WARN |
| `LogicTracking` | type | yes | - | python/cocoindex/_internal/function.py:65 | PASS |
| `MatchAllFilePathMatcher` | - | yes | - | - | WARN |
| `MaybePendingS` | const | yes | - | python/cocoindex/_internal/pending_marker.py:115 | PASS |
| `MemoStateOutcome` | class | yes | - | python/cocoindex/_internal/typing.py:67 | PASS |
| `MountKind` | - | yes | - | - | WARN |
| `MultiVectorSchema` | - | yes | - | - | WARN |
| `MultiVectorSchemaProvider` | - | yes | - | - | WARN |
| `NON_EXISTENCE` | const | yes | - | python/cocoindex/_internal/typing.py:60 | PASS |
| `NonExistenceType` | class | yes | - | python/cocoindex/_internal/typing.py:47 | PASS |
| `NotMemoKeyable` | class | yes | - | python/cocoindex/_internal/memo_fingerprint.py:136 | PASS |
| `PairDecision` | - | yes | - | - | WARN |
| `PairResolver` | - | yes | - | - | WARN |
| `PatternFilePathMatcher` | - | yes | - | - | WARN |
| `PendingS` | class | yes | - | python/cocoindex/_internal/pending_marker.py:74 | PASS |
| `PendingTargetStateProvider` | type | yes | - | python/cocoindex/_internal/target_state.py:243 | PASS |
| `QueryHandlerInfo` | - | yes | - | - | WARN |
| `QueryHandlerResultFields` | - | yes | - | - | WARN |
| `QueryInfo` | - | yes | - | - | WARN |
| `QueryOutput` | - | yes | - | - | WARN |
| `R` | - | yes | - | - | WARN |
| `ROOT_PATH` | const | yes | - | python/cocoindex/_internal/stable_path.py:59 | PASS |
| `RecursiveSplitter` | - | yes | - | - | WARN |
| `ResolutionEvent` | - | yes | - | - | WARN |
| `ResolvedEntities` | - | yes | - | - | WARN |
| `ResolvedS` | class | yes | - | python/cocoindex/_internal/pending_marker.py:89 | PASS |
| `ResolvesTo` | class | yes | - | python/cocoindex/_internal/pending_marker.py:118 | PASS |
| `Runner` | class | yes | - | python/cocoindex/_internal/runner.py:34 | PASS |
| `SentenceTransformerEmbedder` | - | yes | - | - | WARN |
| `SeparatorSplitter` | - | yes | - | - | WARN |
| `ServerSettings` | - | yes | - | - | WARN |
| `Settings` | class | yes | yes | python/cocoindex/_internal/setting.py:56 | PASS |
| `StableKey` | type | yes | - | python/cocoindex/_internal/stable_path.py:9 | PASS |
| `StablePath` | class | yes | - | python/cocoindex/_internal/stable_path.py:16 | PASS |
| `Symbol` | type | yes | yes | python/cocoindex/_internal/stable_path.py:7 | PASS |
| `SyncFunction` | - | yes | - | - | WARN |
| `TargetActionSink` | class | yes | - | python/cocoindex/_internal/target_state.py:143 | PASS |
| `TargetHandler` | class | yes | - | python/cocoindex/_internal/target_state.py:197 | PASS |
| `TargetReconcileOutput` | class | yes | yes | python/cocoindex/_internal/target_state.py:188 | PASS |
| `TargetState` | class | yes | yes | python/cocoindex/_internal/target_state.py:248 | PASS |
| `TargetStateProvider` | class | yes | - | python/cocoindex/_internal/target_state.py:208 | PASS |
| `TextPosition` | - | yes | - | - | WARN |
| `UpdateHandle` | class | yes | - | python/cocoindex/_internal/app.py:49 | PASS |
| `UpdateSnapshot` | class | yes | - | python/cocoindex/_internal/update_stats.py:59 | PASS |
| `UpdateStats` | class | yes | - | python/cocoindex/_internal/update_stats.py:39 | PASS |
| `UpdateStatus` | class | yes | - | python/cocoindex/_internal/update_stats.py:9 | PASS |
| `UuidGenerator` | - | yes | - | - | WARN |
| `VectorSchema` | - | yes | - | - | WARN |
| `VectorSchemaProvider` | - | yes | - | - | WARN |
| `cli` | - | yes | - | - | WARN |
| `component_subpath` | function | yes | yes | python/cocoindex/_internal/component_ctx.py:198 | PASS |
| `declare_target_state` | function | yes | yes | python/cocoindex/_internal/target_state.py:265 | PASS |
| `declare_target_state_with_child` | function | yes | yes | python/cocoindex/_internal/target_state.py:282 | PASS |
| `default_env` | function | yes | yes | python/cocoindex/_internal/api.py:623 | PASS |
| `detect_code_language` | - | yes | - | - | WARN |
| `exception_handler` | function | yes | yes | python/cocoindex/_internal/component_ctx.py:331 | PASS |
| `fn` | - | yes | yes | python/cocoindex/_internal/function.py:1811 | PASS |
| `generate_id` | - | yes | - | - | WARN |
| `generate_uuid` | - | yes | - | - | WARN |
| `get_component_context` | function | yes | yes | python/cocoindex/_internal/component_ctx.py:305 | PASS |
| `get_multi_vector_schema` | - | yes | - | - | WARN |
| `get_vector_schema` | - | yes | - | - | WARN |
| `is_live_component_class` | - | yes | - | - | WARN |
| `is_non_existence` | function | yes | yes | python/cocoindex/_internal/typing.py:63 | PASS |
| `lifespan` | function | yes | yes | python/cocoindex/_internal/environment.py:449 | PASS |
| `litellm` | - | yes | - | - | WARN |
| `map` | function | yes | yes | python/cocoindex/_internal/api.py:532 | PASS |
| `memo_fingerprint` | function | yes | yes | python/cocoindex/_internal/memo_fingerprint.py:361 | PASS |
| `mount` | function | yes | yes | python/cocoindex/_internal/api.py:333 | PASS |
| `mount_each` | function | yes | yes | python/cocoindex/_internal/api.py:427 | PASS |
| `mount_target` | function | yes | yes | python/cocoindex/_internal/api.py:566 | PASS |
| `register_memo_key_function` | function | yes | yes | python/cocoindex/_internal/memo_fingerprint.py:155 | PASS |
| `register_root_target_states_provider` | function | yes | yes | python/cocoindex/_internal/target_state.py:305 | PASS |
| `resolve_entities` | - | yes | - | - | WARN |
| `runtime` | function | yes | yes | python/cocoindex/_internal/api.py:655 | PASS |
| `serialize_by_pickle` | function | yes | yes | python/cocoindex/_internal/serde.py:151 | PASS |
| `show_progress` | function | yes | yes | python/cocoindex/_internal/app.py:194 | PASS |
| `start` | function | yes | yes | python/cocoindex/_internal/api.py:603 | PASS |
| `start_blocking` | function | yes | yes | python/cocoindex/_internal/api.py:613 | PASS |
| `stop` | function | yes | yes | python/cocoindex/_internal/api.py:608 | PASS |
| `stop_blocking` | function | yes | yes | python/cocoindex/_internal/api.py:618 | PASS |
| `unpickle_safe` | function | yes | yes | python/cocoindex/_internal/serde.py:128 | PASS |
| `use_context` | function | yes | yes | python/cocoindex/_internal/component_ctx.py:273 | PASS |
| `use_mount` | function | yes | yes | python/cocoindex/_internal/api.py:194 | PASS |

### Coverage Summary

- **Exports Found:** 72
- **Documented:** 72 (100%)
- **Missing Documentation:** 0
- **Signature Mismatches:** 0
- **Stale Documentation:** 47, documented extras included
- **Scoring Warnings:**
  - Type Coverage leaves out each name the stale-scope guard restored or the extraction recorded with no kind, such as an extraction gap (the provenance map, when one is given, gives it no kind Type Coverage reads at its file): `fn`
- **Borderline Calls:**
  - `TargetHandler` (SKILL.md:193), inventory reader: kindLabels `Protocol` / `runtime Protocol(s)` (TargetHandler, LiveComponent, LiveMapFeed, LiveMapView) and the skill's other Protocols (Function, PairResolver, FilePathMatcher, VectorSchemaProvider, MultiVectorSchemaProvider, Embedder) read as `interface`; `dataclass`, `NamedTuple` and `class` labels as `class`; StrEnum classes (UpdateStatus, CanonicalSide, ExistingCanonicalPolicy) as `enum`; left open by: each `kind` is one of `function`, `class`, `type`, `constant`, `hook`, `interface`, `method`, `struct`, `enum`, `trait`, `macro` or `adapter`; the other reading gives: kind `class` for the Protocols (or `class` for the StrEnums): no gap, kind is not compared and the forms are unchanged
  - `GPU` (SKILL.md:190), inventory reader: the shared kindLabel `class / singleton` read positionally for the row `Runner` / `GPU`: Runner a `class`, GPU (described as a `GPURunner()` singleton) a `constant`; left open by: each `kind` is one of `function`, `class`, `type`, `constant`, `hook`, `interface`, `method`, `struct`, `enum`, `trait`, `macro` or `adapter`; the other reading gives: GPU as `class`: no gap, the row writes no form for it
  - `cli` (references/settings-cli.md:113), inventory reader: kindLabel `click.Group` read as `function`, since the skill writes `def cli(env_file: str | None = None, app_dir: str | None = "") -> None` under `@click.group()`, so that form is kept and compared; left open by: each `kind` is one of `function`, `class`, `type`, `constant`, `hook`, `interface`, `method`, `struct`, `enum`, `trait`, `macro` or `adapter`; the other reading gives: `constant` (a data constant carries no params): the settings-cli.md form would be dropped, no gap
  - `fn` (SKILL.md:180), inventory reader: kindLabel `decorator namespace` (a `_FunctionDecorator` instance) read as `function`, so each `@coco.fn(...)` call with arguments (SKILL.md:180 twice, :190, :341 twice; component-api.md:193) is a usage compared as a call to the instance's `__call__`, and `coco.fn.as_async(...)` is a `method` with owner `fn`; left open by: A function's, a method's or a class's form the skill writes as a call expression of its own name (... in running text or a description cell, only a call that passes an argument and writes no parameter type, `?`, bare `*` or `/` ...) ... is recorded whole in `usage_signature`; the other reading gives: `constant`: the usages would carry no form, so no comparison and no gap
  - `AppConfig` (references/component-api.md:11), inventory reader: a dataclass, NamedTuple or msgspec.Struct body that writes fields and no `__init__` (AppConfig, TextPosition, Chunk, FileMetadata, VectorSchema, GlobalExecutionOptions, Settings, ServerSettings, QueryHandlerResultFields, QueryHandlerInfo, QueryInfo, QueryOutput, TargetReconcileOutput, ChildTargetDef) is recorded in `fields`, not `params`: no sentence makes a field list a constructor form; left open by: A constructor a place writes (`def __init__(self, ...)`, `constructor(...)`, in a class body, a methods list, a row's cell or running text) is its class's form, never a `method` entry; the other reading gives: the field lists as typed `params` compared with the generated constructor: a Critical signature-mismatch only if the source's fields differ; against the SKILL.md rows' forms they agree, so no split-body mismatch
  - `TargetReconcileOutput` (SKILL.md:195), inventory reader: a Purpose cell that is only a nameless parenthesized list (TargetReconcileOutput, GlobalExecutionOptions, QueryHandlerInfo, QueryHandlerResultFields, QueryInfo, QueryOutput) is the row's class form, recorded in `params`; left open by: a class's form written as a parameter list or a signature that is not such a call stays in `params`; the other reading gives: no form at those rows: no gap (the lists agree with the reference fields and, by their defaults, with the constructors)
  - `lifespan` (SKILL.md:94), inventory reader: `@coco.lifespan` decorates a function `(EnvironmentBuilder) -> Iterator[None] | AsyncIterator[None]` describes the decorated function's type, not a form of `lifespan` (the span writes no name), so SKILL.md:94 gives lifespan no entry; left open by: A place that writes a name but no form of it, and no `methods`, `properties` or `fields` its entry would carry (a mention, a bare code span, an import, a heading or prose that names or describes it), gives it no entry when another place gives the name one; the other reading gives: a lifespan form `(EnvironmentBuilder) -> Iterator[None] | AsyncIterator[None]`: a Critical signature-mismatch against `lifespan(fn: LifespanFn | None = None) -> Any` and a split-body mismatch with references/component-api.md:110
  - `declare_target_state_with_child` (SKILL.md:197), inventory reader: a return the skill writes in prose beside a form (`returns PendingTargetStateProvider[ValueT, OptChildHandlerT]` here; `returns TargetStateProvider` at SKILL.md:198; `returns ComponentMountHandle` at SKILL.md:97; `returns an UpdateHandle` at SKILL.md:317) is that form's `return_type`; the floor's blank return_type is the reader's; left open by: is recorded whole in `usage_signature`, as `inventory-floor.json` writes a usage ..., and a return type the skill writes for it in `return_type`; the other reading gives: no return_type on those entries: no gap, each prose return agrees with the reference declarations (type arguments left out are not compared)
  - `is_live_component_class` (SKILL.md:167), inventory reader: SKILL.md:167 says it is internal and not exported on `coco`, so its prose form `is_live_component_class(cls) -> bool` gives no entry; the fenced declaration at references/live-components.md:14 gives one; left open by: A name the skill presents only as a local import alias of another name, or says the source does not export, is not an export the skill documents either: it gets an entry only from a place `inventory-floor.json` gives it, a heading, an export table's first cell or a fenced declaration of it (an import is not one), never from a code span in prose or a description cell; the other reading gives: a SKILL.md:167 entry with params `cls`, return `bool`: no gap, it matches `(cls: Any) -> bool`
  - `runtime` (SKILL.md:189), inventory reader: the first cells `runtime()` (SKILL.md:189) and `get_component_context()` (SKILL.md:207) are empty calls recorded in `usage_signature`; left open by: a heading or an export table's first cell that writes `name()` is a form, recorded as written; the other reading gives: `params: ""` (claims it takes none): no gap, both reference declarations take no parameter
  - `update_blocking` (SKILL.md:315), inventory reader: the migration table's `v1.0.0 (replacement)` column is a description cell, so its empty calls (`app.update_blocking()`, `await app.update()`, `app.drop()`, `app.drop_blocking()`, `walker.items()`, `pg_source.fetch_rows()`) are mentions while its calls with arguments are usages; left open by: A description cell is any table cell but an export table's first cell and a cell whose column writes the call or signature, by its role (Signature, Props, Params, Parameters, Arguments, Usage, Syntax, Example and the like); the other reading gives: a call column: those empty calls become forms of App.update / update_blocking / drop / drop_blocking and DirWalker.items, each matching a declaration whose parameters are all optional: no gap
  - `mount_each` (SKILL.md:312), inventory reader: `.items(key_fn)` on the result of `pg_source.fetch_rows()` is called on an object whose class the skill does not name, so it gets no `method` entry (only the enclosing mount_each usage is recorded); left open by: and so does one the skill calls through an instance or the class it documents with that member (`builder.provide(KEY, value)`, `canvas.getByRole('button')`), the class as `owner` and the call in `usage_signature`; the other reading gives: an `items` method entry with owner RowFetcher and usage `items(key_fn)`: compared with that class's `items`, no gap known
  - `litellm` (SKILL.md:111), inventory reader: the re-exported `litellm` module is one `constant` entry; the third-party calls the skill names through it (`acompletion(model=..., messages=[...], response_format=...)` at SKILL.md:111, `litellm.completion`, `litellm.acompletion`, `litellm.aembedding`), sub-module names (`sentence_transformers`, `text`, `entity_resolution`, the connector packages) and internal or private names it only mentions (`GPURunner`, `LiveComponentController`, `get_default_db_path`, `_load_app`, `_FunctionDecorator`, `_default_env`, `AsyncCallable`) get no entry; left open by: A place that writes a name but no form of it, and no `methods`, `properties` or `fields` its entry would carry (a mention, a bare code span, an import, a heading or prose that names or describes it), gives it no entry when another place gives the name one, unless `inventory-floor.json` gives that place; of several such places of a name the skill documents and no other place gives an entry, the first alone gives one; the other reading gives: entries for them: an `acompletion` usage is a declaration outside the source tree and counts as matching; a mention-only entry for a name the surface lacks would be a stale-name gap
  - `PgType` (references/connectors.md:20), inventory reader: each name the connectors' `__all__` lists writes only as a string is a documented export with one mention entry at its first place, its kind read from its spelling (CamelCase `class`, snake_case `function`, `*Fn` `type`), since the skill gives it no kind label; a name shared by several connectors (`mount_table_target`, `TableSchema`, `TableTarget`, `ColumnDef`, `connect`) is listed by its bare name; left open by: of several such places of a name the skill documents and no other place gives an entry, the first alone gives one: in SKILL.md, else the file that sorts first by path, at its lowest line; the other reading gives: another kind for those names: no gap, they carry no form
  - `TargetState` (SKILL.md:191), inventory reader: `Bundled (provider, key, value) triple` (SKILL.md:191) and `bundles (provider, key, value)` (references/target-state.md:93) describe the class's contents, not a form; left open by: A place that writes a name but no form of it, and no `methods`, `properties` or `fields` its entry would carry (a mention, a bare code span, an import, a heading or prose that names or describes it), gives it no entry when another place gives the name one; the other reading gives: a bare-names params form `provider, key, value`: no gap, it matches the constructor's three parameters
  - `__call__` (references/target-state.md:45), inventory reader: the sink-fn `def __call__` (sync) and `async def __call__` (async) declarations are methods of the types `from_fn` and `from_async_fn` take, owners TargetActionSinkFn and AsyncTargetActionSinkFn, two methods with different owners, never a pair; left open by: A `method`'s `name` is the bare method name and its `owner` the class or object it is called on; the other reading gives: no entries (the block names no class), or one owner for both (an overload set): no gap
  - `is_non_existence` (SKILL.md:164), inventory reader: the Key Types block's `is_non_existence(obj)` (SKILL.md:259) and `memo_fingerprint(obj)` (SKILL.md:264) lines are calls in a fenced block and give no entry, the same calls being written in running text at SKILL.md:164-165; `register_memo_key_function(typ, key_fn, *, state_fn=None)` (SKILL.md:265) writes a bare `*`, so it is no call and keeps an entry; left open by: A call or JSX element of a name that a fenced example writes is not a place of its own when the skill also writes that name's form at a place that is no example; the other reading gives: the block as a declaration listing: two more entries with the same forms as SKILL.md:164-165, no gap
  - `UpdateHandle` (references/component-api.md:46), inventory reader: component-api.md:46 writes members (`stats()`, `result()`) for UpdateHandle and DropHandle, so it gives their entries; the SKILL.md:247-248 listing lines, whose members sit in comments, give none; left open by: A place that writes a name but no form of it, and no `methods`, `properties` or `fields` its entry would carry (a mention, a bare code span, an import, a heading or prose that names or describes it), gives it no entry when another place gives the name one; the other reading gives: entries at SKILL.md:247-248 too: no gap, no form
  - `AppConfig` (SKILL.md:175), inventory reader: constructor spellings in Purpose cells with `name=value` defaults (`AppConfig(name, environment=_default_env, max_inflight_components=None)`, `Settings(db_path=None, ...)`, `ServerSettings(address="127.0.0.1:49344", cors_origins=None)`) are calls, recorded in `usage_signature`; left open by: in running text or a description cell, only a call that passes an argument and writes no parameter type, `?`, bare `*` or `/`, with or without such a prefix, and no return type unless such a prefix comes before the name; the other reading gives: parameter lists with defaults in `params` (claiming a complete list, `name` required): no gap, they agree with the reference fields
- **Nested Entry Points:** `python/cocoindex/connectors/amazon_s3/__init__.py` inside `python/cocoindex/__init__.py`: `S3File`, `S3FilePath`, `S3Walker`, `get_object`, `list_objects`, `read`; `python/cocoindex/connectors/doris/__init__.py` inside `python/cocoindex/__init__.py`: `ColumnDef`, `DorisConnectionConfig`, `DorisTableTarget`, `DorisType`, `InvertedIndexDef`, `ManagedConnection`, `RetryConfig`, `TableSchema`, `ValueEncoder`, `VectorIndexDef`, `build_vector_search_query`, `connect`, `connect_async`, `declare_table_target`, `mount_table_target`, `table_target`; `python/cocoindex/connectors/google_drive/__init__.py` inside `python/cocoindex/__init__.py`: `DriveFile`, `DriveFileInfo`, `GoogleDriveSource`, `GoogleDriveSourceSpec`, `list_files`; `python/cocoindex/connectors/kafka/__init__.py` inside `python/cocoindex/__init__.py`: `DeletionValueFn`, `IsDeleteFn`, `KafkaTopicTarget`, `declare_kafka_topic_target`, `kafka_topic_target`, `mount_kafka_topic_target`, `topic_as_map`; `python/cocoindex/connectors/lancedb/__init__.py` inside `python/cocoindex/__init__.py`: `ColumnDef`, `LanceAsyncConnection`, `LanceType`, `TableSchema`, `TableTarget`, `ValueEncoder`, `connect`, `connect_async`, `declare_table_target`, `mount_table_target`, `table_target`; `python/cocoindex/connectors/localfs/__init__.py` inside `python/cocoindex/__init__.py`: `DirTarget`, `DirWalker`, `File`, `FilePath`, `declare_dir_target`, `declare_file`, `dir_target`, `mount_dir_target`, `walk_dir`; `python/cocoindex/connectors/postgres/__init__.py` inside `python/cocoindex/__init__.py`: `ColumnDef`, `PgSourceSpec`, `PgTableSource`, `PgType`, `RowFetcher`, `TableSchema`, `TableTarget`, `ValueEncoder`, `create_pool`, `declare_table_target`, `mount_table_target`, `table_target`; `python/cocoindex/connectors/qdrant/__init__.py` inside `python/cocoindex/__init__.py`: `CollectionSchema`, `CollectionTarget`, `PointStruct`, `QdrantVectorDef`, `collection_target`, `create_client`, `declare_collection_target`, `mount_collection_target`; `python/cocoindex/connectors/sqlite/__init__.py` inside `python/cocoindex/__init__.py`: `ColumnDef`, `ManagedConnection`, `SqliteType`, `TableSchema`, `TableTarget`, `ValueEncoder`, `Vec0TableDef`, `connect`, `declare_table_target`, `managed_connection`, `mount_table_target`, `table_target`; `python/cocoindex/connectors/surrealdb/__init__.py` inside `python/cocoindex/__init__.py`: `ColumnDef`, `ConnectionFactory`, `RelationTarget`, `SurrealType`, `TableSchema`, `TableTarget`, `ValueEncoder`, `declare_relation_target`, `declare_table_target`, `mount_relation_target`, `mount_table_target`, `relation_target`, `table_target`
- **Extraction Gaps:** `DeletionValueFn` (python/cocoindex/connectors/kafka/_target.py:206), `ExceptionHandler` (python/cocoindex/_internal/component_ctx.py:25), `GPU` (python/cocoindex/_internal/runner.py:282), `IsDeleteFn` (python/cocoindex/connectors/kafka/_source.py:30), `LanceAsyncConnection` (not located), `LifespanFn` (python/cocoindex/_internal/environment.py:118), `LogicTracking` (python/cocoindex/_internal/function.py:65), `MaybePendingS` (python/cocoindex/_internal/pending_marker.py:115), `NON_EXISTENCE` (python/cocoindex/_internal/typing.py:60), `PendingTargetStateProvider` (python/cocoindex/_internal/target_state.py:243), `PointStruct` (python/cocoindex/connectors/qdrant/_target.py:42), `ROOT_PATH` (python/cocoindex/_internal/stable_path.py:59), `StableKey` (python/cocoindex/_internal/stable_path.py:9), `Symbol` (python/cocoindex/_internal/stable_path.py:7), `ValueEncoder` (python/cocoindex/connectors/doris/_target.py:79), `fn` (python/cocoindex/_internal/function.py:1811)

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 100% |
| Signature Accuracy | 100% |
| Type Coverage | 100% |

**Notes:**

- §1a: the inventory validated on the first pass (411 entries, floor 49 of 49, spot-check 3 of 3 found); no form was left unbound for want of a place (0 `at` warnings).
- §1b: the inventory reader's split-body cross-check (148 names written in two or more files) found no `cross_check_mismatches`, so no split-body gap is recorded.
- §2: the recipe runner read all 92 in-scope files (status `ok`, no fallback); no file was read by eye and none was left unread; no `export *` star was unresolved. 16 signature judges (one per `files[]` entry of the plan, 42 checks) compared the documented forms with their declarations and reported no mismatch and no undecided reading.
- §2b: the numerator ground truth was skipped (no inflation signature: `stats.exports_documented` 154 is not the denominator).
- §2c: 47 documented names lie outside the root barrel's `all` set; `classify-stale` found none fabricated.
- §4b: the metadata count cross-check found one Medium drift: `stats.exports_public_api` 140 against `exports[]` 118 (16%).
- §4c: the provenance line check found no stale line.

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)

### Structural Findings

| # | Type | Severity | Detail | Line |
|---|------|----------|--------|------|
| - | none | - | No structural issue: the `usage` family is served by `## Quick Start` (line 12) and the `api_surface` family by `## Key API Summary` (line 170); the `description` family by the non-empty frontmatter description; 8 code fences, balanced, each with a language tag; no table row drifts from its header; no `scripts/` or `assets/` folder; every function and method export is used in a usage-family section or reference file; no export's description and examples disagree on async/sync. Migration check (Deep tier, evidence report pins `t2_future_count: 0`): SKILL.md has no `## Migration & Deprecation Warnings` heading (`## Migration from v0.3.37` is not Section 4b), so no Case applies. | - |

**Structural Issues:** 0

### Reference Consistency (split-body)

| # | Reference File | Export | Issue | Other Side | Reference Line | Contradicted Side |
|---|---------------|--------|-------|------------|---------------|-------------------|
| - | - | - | none | - | - | - |

**Exports Cross-Checked:** 148
**Mismatches Found:** 0

## External Validation

### skill-check
- **Available:** yes
- **Quality Score:** 100/100
- **Errors:** 0
- **Warnings:** 0
- **Diagnostics:** none

### Tessl Review
- **Result:** off — set tessl_review_workspace in preferences.yaml to enable

### Combined External Score
- **External Validation Score:** 100%
- **Tools used:** skill-check

## Completeness Score

### Score Breakdown

| Category | Score | Weight | Weighted |
|----------|-------|--------|----------|
| Export Coverage | 100% | 45% | 45% |
| Signature Accuracy | 100% | 25% | 25% |
| Type Coverage | 100% | 20% | 20% |
| Coherence | not scored (naive mode) | 0% | 0% |
| External Validation | 100% | 10% | 10% |
| **Total** | | **100%** | **100%** |

### Result

**Score:** 100%
**Threshold:** 80%
**Result:** **PASS**

**Threshold Source:** workflow default (80%)
**Weight Distribution:** naive (redistributed)
**Tier Adjustment:** none
**External Validators:** skill-check only (from `skill-check`; Tessl Review is off)
**Analysis Confidence:** full
**Tooling Status:** ok

## Gap Report

**Total Gaps:** 48
**Blocking (Critical + High):** 0
**Non-blocking (Medium + Low + Info):** 48

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|------------------|
| Critical | 0 | None |
| High | 0 | None |
| Medium | 2 | stale-documentation (1): check each name against the source and the brief's scope, then update or remove its documentation or fix the scope (Update Skill does not repair it); metadata-drift (1): re-run Create Skill or edit the brief's scope, as each remediation says (counts that differ only by `Type::method` entries need no fix, and a hand edit of the counts does not hold) |
| Low | 0 | None |
| Info | 46 | observation (46): apply each only when you agree, as its remediation says, since it is advisory (a documented extra needs no change) |
| **Total** | **48** | |

### GAP-027: Stale documentation: R

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/settings-cli.md:93
**Export:** R

**Issue:** `references/settings-cli.md:93` documents `R`, which the enumerated source API surface lacks

**Remediation:** Check `R` against the source and update or remove its documentation at references/settings-cli.md:93: the enumerated source surface does not export it.

### GAP-048: metadata drift — barrel export counts diverge

**Severity:** Medium
**Category:** Coverage (metadata-drift)
**Source:** skills/oms-cocoindex/1.0.0/oms-cocoindex/metadata.json

**Issue:** stats.exports_public_api=140, exports[].length=118 → 16% drift

**Remediation:** Re-run Create Skill, which rebuilds `exports[]` and `stats.exports_public_api` in `skills/oms-cocoindex/1.0.0/oms-cocoindex/metadata.json` from the source. Update Skill does not repair this drift: each time it writes the skill it recounts `stats.exports_public_api` from the source and keeps `exports[]`, adding or dropping only the names its provenance map changes, so a metadata patch does not hold.

### GAP-001: Documented extra: AsyncFunction

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/function.py:903
**Export:** AsyncFunction

**Issue:** `SKILL.md:275` documents `AsyncFunction`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `AsyncFunction` is a documented extra, a name the source still declares at `python/cocoindex/_internal/function.py:903` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-002: Documented extra: CanonicalSide

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:35
**Export:** CanonicalSide

**Issue:** `references/ops.md:184` documents `CanonicalSide`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CanonicalSide` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:35` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-003: Documented extra: Chunk

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/chunk.py:26
**Export:** Chunk

**Issue:** `SKILL.md:348` documents `Chunk`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Chunk` is a documented extra, a name the source still declares at `python/cocoindex/resources/chunk.py:26` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-004: Documented extra: CustomLanguageConfig

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/text.py:87
**Export:** CustomLanguageConfig

**Issue:** `references/ops.md:85` documents `CustomLanguageConfig`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CustomLanguageConfig` is a documented extra, a name the source still declares at `python/cocoindex/ops/text.py:87` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-005: Documented extra: Embedder

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/embedder.py:15
**Export:** Embedder

**Issue:** `SKILL.md:168` documents `Embedder`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Embedder` is a documented extra, a name the source still declares at `python/cocoindex/resources/embedder.py:15` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-006: Documented extra: ExistingCanonicalPolicy

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:57
**Export:** ExistingCanonicalPolicy

**Issue:** `references/ops.md:211` documents `ExistingCanonicalPolicy`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ExistingCanonicalPolicy` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:57` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-007: Documented extra: FileLike

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/file.py:56
**Export:** FileLike

**Issue:** `references/resources.md:51` documents `FileLike`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `FileLike` is a documented extra, a name the source still declares at `python/cocoindex/resources/file.py:56` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-008: Documented extra: FileMetadata

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/file.py:40
**Export:** FileMetadata

**Issue:** `references/resources.md:41` documents `FileMetadata`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `FileMetadata` is a documented extra, a name the source still declares at `python/cocoindex/resources/file.py:40` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-009: Documented extra: FilePathMatcher

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/file.py:205
**Export:** FilePathMatcher

**Issue:** `references/resources.md:80` documents `FilePathMatcher`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `FilePathMatcher` is a documented extra, a name the source still declares at `python/cocoindex/resources/file.py:205` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-010: Documented extra: Function

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/function.py:138
**Export:** Function

**Issue:** `SKILL.md:275` documents `Function`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Function` is a documented extra, a name the source still declares at `python/cocoindex/_internal/function.py:138` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-011: Documented extra: GlobalExecutionOptions

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/setting.py:12
**Export:** GlobalExecutionOptions

**Issue:** `SKILL.md:213` documents `GlobalExecutionOptions`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `GlobalExecutionOptions` is a documented extra, a name the source still declares at `python/cocoindex/setting.py:12` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-012: Documented extra: IdGenerator

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/id.py:89
**Export:** IdGenerator

**Issue:** `SKILL.md:348` documents `IdGenerator`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `IdGenerator` is a documented extra, a name the source still declares at `python/cocoindex/resources/id.py:89` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-013: Documented extra: LazyEnvironment

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/environment.py:287
**Export:** LazyEnvironment

**Issue:** `SKILL.md:175` documents `LazyEnvironment`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LazyEnvironment` is a documented extra, a name the source still declares at `python/cocoindex/_internal/environment.py:287` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-014: Documented extra: LiteLLMEmbedder

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/litellm.py:22
**Export:** LiteLLMEmbedder

**Issue:** `SKILL.md:320` documents `LiteLLMEmbedder`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LiteLLMEmbedder` is a documented extra, a name the source still declares at `python/cocoindex/ops/litellm.py:22` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-015: Documented extra: LlmPairResolver

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/llm_resolver.py:49
**Export:** LlmPairResolver

**Issue:** `references/ops.md:195` documents `LlmPairResolver`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LlmPairResolver` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/llm_resolver.py:49` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-016: Documented extra: MatchAllFilePathMatcher

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/file.py:215
**Export:** MatchAllFilePathMatcher

**Issue:** `references/resources.md:89` documents `MatchAllFilePathMatcher`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MatchAllFilePathMatcher` is a documented extra, a name the source still declares at `python/cocoindex/resources/file.py:215` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-017: Documented extra: MountKind

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/component_ctx.py:39
**Export:** MountKind

**Issue:** `references/component-api.md:324` documents `MountKind`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MountKind` is a documented extra, a name the source still declares at `python/cocoindex/_internal/component_ctx.py:39` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-018: Documented extra: MultiVectorSchema

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:49
**Export:** MultiVectorSchema

**Issue:** `references/resources.md:212` documents `MultiVectorSchema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MultiVectorSchema` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:49` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-019: Documented extra: MultiVectorSchemaProvider

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:43
**Export:** MultiVectorSchemaProvider

**Issue:** `references/connectors.md:68` documents `MultiVectorSchemaProvider`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MultiVectorSchemaProvider` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:43` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-020: Documented extra: PairDecision

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:46
**Export:** PairDecision

**Issue:** `references/ops.md:211` documents `PairDecision`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PairDecision` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:46` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-021: Documented extra: PairResolver

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:97
**Export:** PairResolver

**Issue:** `references/ops.md:195` documents `PairResolver`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PairResolver` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:97` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-022: Documented extra: PatternFilePathMatcher

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/file.py:227
**Export:** PatternFilePathMatcher

**Issue:** `SKILL.md:348` documents `PatternFilePathMatcher`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PatternFilePathMatcher` is a documented extra, a name the source still declares at `python/cocoindex/resources/file.py:227` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-023: Documented extra: QueryHandlerInfo

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/query_handler.py:21
**Export:** QueryHandlerInfo

**Issue:** `SKILL.md:214` documents `QueryHandlerInfo`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `QueryHandlerInfo` is a documented extra, a name the source still declares at `python/cocoindex/query_handler.py:21` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-024: Documented extra: QueryHandlerResultFields

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/query_handler.py:10
**Export:** QueryHandlerResultFields

**Issue:** `SKILL.md:215` documents `QueryHandlerResultFields`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `QueryHandlerResultFields` is a documented extra, a name the source still declares at `python/cocoindex/query_handler.py:10` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-025: Documented extra: QueryInfo

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/query_handler.py:30
**Export:** QueryInfo

**Issue:** `SKILL.md:216` documents `QueryInfo`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `QueryInfo` is a documented extra, a name the source still declares at `python/cocoindex/query_handler.py:30` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-026: Documented extra: QueryOutput

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/query_handler.py:43
**Export:** QueryOutput

**Issue:** `SKILL.md:217` documents `QueryOutput`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `QueryOutput` is a documented extra, a name the source still declares at `python/cocoindex/query_handler.py:43` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-028: Documented extra: RecursiveSplitter

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/text.py:120
**Export:** RecursiveSplitter

**Issue:** `references/ops.md:59` documents `RecursiveSplitter`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `RecursiveSplitter` is a documented extra, a name the source still declares at `python/cocoindex/ops/text.py:120` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-029: Documented extra: ResolutionEvent

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:70
**Export:** ResolutionEvent

**Issue:** `references/ops.md:187` documents `ResolutionEvent`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ResolutionEvent` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:70` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-030: Documented extra: ResolvedEntities

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:114
**Export:** ResolvedEntities

**Issue:** `references/ops.md:211` documents `ResolvedEntities`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ResolvedEntities` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:114` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-031: Documented extra: SentenceTransformerEmbedder

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/sentence_transformers.py:25
**Export:** SentenceTransformerEmbedder

**Issue:** `SKILL.md:319` documents `SentenceTransformerEmbedder`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `SentenceTransformerEmbedder` is a documented extra, a name the source still declares at `python/cocoindex/ops/sentence_transformers.py:25` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-032: Documented extra: SeparatorSplitter

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/text.py:39
**Export:** SeparatorSplitter

**Issue:** `references/ops.md:35` documents `SeparatorSplitter`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `SeparatorSplitter` is a documented extra, a name the source still declares at `python/cocoindex/ops/text.py:39` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-033: Documented extra: ServerSettings

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/setting.py:93
**Export:** ServerSettings

**Issue:** `SKILL.md:212` documents `ServerSettings`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ServerSettings` is a documented extra, a name the source still declares at `python/cocoindex/setting.py:93` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-034: Documented extra: SyncFunction

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/function.py:491
**Export:** SyncFunction

**Issue:** `SKILL.md:275` documents `SyncFunction`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `SyncFunction` is a documented extra, a name the source still declares at `python/cocoindex/_internal/function.py:491` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-035: Documented extra: TextPosition

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/chunk.py:9
**Export:** TextPosition

**Issue:** `SKILL.md:348` documents `TextPosition`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `TextPosition` is a documented extra, a name the source still declares at `python/cocoindex/resources/chunk.py:9` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-036: Documented extra: UuidGenerator

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/id.py:152
**Export:** UuidGenerator

**Issue:** `SKILL.md:348` documents `UuidGenerator`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `UuidGenerator` is a documented extra, a name the source still declares at `python/cocoindex/resources/id.py:152` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-037: Documented extra: VectorSchema

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:23
**Export:** VectorSchema

**Issue:** `SKILL.md:348` documents `VectorSchema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `VectorSchema` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:23` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-038: Documented extra: VectorSchemaProvider

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:17
**Export:** VectorSchemaProvider

**Issue:** `SKILL.md:348` documents `VectorSchemaProvider`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `VectorSchemaProvider` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:17` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-039: Documented extra: cli

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/cli.py:505
**Export:** cli

**Issue:** `SKILL.md:218` documents `cli`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `cli` is a documented extra, a name the source still declares at `python/cocoindex/cli.py:505` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-040: Documented extra: detect_code_language

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/text.py:19
**Export:** detect_code_language

**Issue:** `references/ops.md:20` documents `detect_code_language`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `detect_code_language` is a documented extra, a name the source still declares at `python/cocoindex/ops/text.py:19` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-041: Documented extra: generate_id

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/id.py:31
**Export:** generate_id

**Issue:** `references/resources.md:140` documents `generate_id`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `generate_id` is a documented extra, a name the source still declares at `python/cocoindex/resources/id.py:31` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-042: Documented extra: generate_uuid

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/id.py:61
**Export:** generate_uuid

**Issue:** `references/resources.md:168` documents `generate_uuid`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `generate_uuid` is a documented extra, a name the source still declares at `python/cocoindex/resources/id.py:61` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-043: Documented extra: get_multi_vector_schema

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:58
**Export:** get_multi_vector_schema

**Issue:** `SKILL.md:168` documents `get_multi_vector_schema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_multi_vector_schema` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:58` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-044: Documented extra: get_vector_schema

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:33
**Export:** get_vector_schema

**Issue:** `SKILL.md:168` documents `get_vector_schema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_vector_schema` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:33` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-045: Documented extra: is_live_component_class

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/live_component.py:35
**Export:** is_live_component_class

**Issue:** `SKILL.md:167` documents `is_live_component_class`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `is_live_component_class` is a documented extra, a name the source still declares at `python/cocoindex/_internal/live_component.py:35` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-046: Documented extra: litellm

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/litellm.py:1
**Export:** litellm

**Issue:** `references/ops.md:150` documents `litellm`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `litellm` is a documented extra, a name the source still declares at `python/cocoindex/ops/litellm.py:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-047: Documented extra: resolve_entities

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:186
**Export:** resolve_entities

**Issue:** `references/ops.md:211` documents `resolve_entities`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `resolve_entities` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:186` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### Discovery Quality

**Discovery Test:** PASS (3/3)

| # | Prompt | Selected Skill | Result |
|---|--------|----------------|--------|
| 1 | can you help me with this ingestion script my lead sent? it's supposed to only re-embed the docs that changed since the last run and keep the chunks in our vector store up to date | oms-cocoindex (medium) | PASS |
| 2 | why does my indexing job reprocess every single file from scratch each time it runs instead of just the ones I edited since yesterday? | oms-cocoindex (medium) | PASS |
| 3 | run the incremental indexing thing on this folder of markdown notes: chunk them, embed them, and drop the rows for files I delete | oms-cocoindex (high) | PASS |

Catalog: 4 skills (oms-cocoindex, oms-cognee, oms-storybook-react-vite, oms-uitripled). SKILL.md holds no conversational trigger prompts, so the three prompts were synthesized from the §4b.4 patterns (vague, implicit, abbreviated), naming no export, skill or library. Each was routed by an isolated subagent given only the catalog and the prompt; none used a tool. No description optimization hints: Tessl Review did not run and skill-check flagged no description issue.
