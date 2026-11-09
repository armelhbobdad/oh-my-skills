---
workflowType: 'test-skill'
skillName: 'oms-cocoindex'
skillDir: 'skills/oms-cocoindex/1.0.0/oms-cocoindex'
runId: '20261109T195318Z-61d78f7a'
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
testDate: '2026-11-09T19:53:18Z'
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

**Mode Rationale:** metadata.json records `skill_type: "single"`, an individual skill, so the run tests its API surface coverage (naive mode); coherence is checked structurally and is not a scored category.

**Analysis Plan:**
- Coverage Check: every public export of cocoindex v1.0.0 (pinned commit 5fe4f37) is checked for documentation in SKILL.md and its references, with Deep-tier AST-backed signature and type comparison against the source.
- Coherence Check: structural checks only (references resolve, sections well formed); no cross-skill integration validation in naive mode.

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
| `ChildTargetDef` | class | yes | yes | python/cocoindex/_internal/target_state.py:95 | PASS |
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
| `GPURunner` | - | yes | - | - | WARN |
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
| `get_default_db_path` | - | yes | - | - | WARN |
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
- **Stale Documentation:** 48, documented extras included
- **Scoring Warnings:**
  - Type Coverage leaves out each name the stale-scope guard restored or the extraction recorded with no kind, such as an extraction gap (the provenance map, when one is given, gives it no kind Type Coverage reads at its file): `fn`
- **Borderline Calls:**
  - `declare_target_state_with_child` (SKILL.md:197), inventory reader: the floor signature's blank return_type is read from the same row's Purpose cell (`returns PendingTargetStateProvider[ValueT, OptChildHandlerT]`), so the floor entry carries it; left open by: a blank one is the reader's, left out when the place writes none, and a form the skill writes only in prose is an entry of its own; the other reading gives: a separate return-only entry with no `at` and a floor entry with no return_type; either way the return agrees with references/target-state.md:108, so no gap
  - `register_root_target_states_provider` (SKILL.md:198), inventory reader: the floor signature's blank return_type is read from the same row's Purpose cell (`returns TargetStateProvider`), so the floor entry carries it; left open by: a blank one is the reader's, left out when the place writes none, and a form the skill writes only in prose is an entry of its own; the other reading gives: a separate return-only entry with no `at`; either way `TargetStateProvider` agrees with references/target-state.md:120 (type arguments left out are not compared), so no gap
  - `Settings` (references/settings-cli.md:17), inventory reader: a fenced @dataclass or NamedTuple class body documents the generated constructor, so its fields are recorded in order as the class's `params`; applied likewise to AppConfig (component-api.md:11), GlobalExecutionOptions, ServerSettings, QueryHandlerResultFields, QueryHandlerInfo, QueryInfo, QueryOutput (settings-cli.md), TargetReconcileOutput and ChildTargetDef (target-state.md), TextPosition, Chunk, FileMetadata and VectorSchema (resources.md); field lists written in prose (Chunk at references/ops.md:83, MultiVectorSchema at references/resources.md:212) go in `fields` instead; left open by: a dataclass, attrs class, pydantic model or NamedTuple that declares no `__init__` with the fields it generates, in declaration order, base fields first, a default marking a field optional; the other reading gives: recorded as `fields` the bodies are not compared: no gap; as read, a field a body left out or mistyped would be a Critical signature-mismatch, and every body agrees with the SKILL.md row that writes the same class, so no split-body mismatch
  - `AppConfig` (SKILL.md:175), inventory reader: `AppConfig(name, environment=_default_env, max_inflight_components=None)` passes arguments and writes no type, `?`, bare `*` or `/`, so it is a call recorded in usage_signature; likewise `Settings(...)` at SKILL.md:211 and `ServerSettings(...)` at SKILL.md:212; left open by: in running text or a description cell, only a call that passes an argument and writes no parameter type, `?`, bare `*` or `/`, with or without such a prefix, and no return type unless such a prefix comes before the name, such as `add(componentName, options)` or `await coco.mount(fn) -> Handle`; the other reading gives: read as a parameter list with defaults it would claim to be complete (a left-out optional field a Critical omitted-optional); each names every field its reference body gives, so no gap either way
  - `GPU` (SKILL.md:190), inventory reader: the shared label `class / singleton` of the row `Runner` / `GPU` is read positionally: Runner is a `class`, GPU (a `GPURunner()` singleton) a `constant`; left open by: choosing its kind from the name's `kindLabel`, the skill's own label, when it has one; the other reading gives: kind `class` for GPU: the place writes no form, so no gap
  - `TargetHandler` (SKILL.md:193), inventory reader: the labels `Protocol`, `runtime Protocol` and `runtime Protocols` map to kind `interface` (TargetHandler, LiveComponent, LiveMapFeed, LiveMapView), and the references' other Protocol classes (FilePathMatcher, VectorSchemaProvider, MultiVectorSchemaProvider, Embedder, PairResolver, Function) take the same kind; left open by: choosing its kind from the name's `kindLabel`, the skill's own label, when it has one; the other reading gives: kind `class`: no gap (no class-level form is compared; the methods have their own entries)
  - `cli` (SKILL.md:218), inventory reader: the label `click.Group` names the object the `@click.group()`-decorated `def cli(...)` builds, read as kind `function`, so references/settings-cli.md:113's declaration keeps its params and return; left open by: choosing its kind from the name's `kindLabel`, the skill's own label, when it has one; the other reading gives: kind `constant` (a data constant) would carry no params or return, leaving settings-cli.md:113 uncompared: no gap
  - `fn` (SKILL.md:180), inventory reader: the label `decorator namespace` (a `_FunctionDecorator` instance) is read as kind `function`, so its calls are usage forms compared with the instance's `__call__`, and `as_async` is a `method` entry with owner `fn`; left open by: choosing its kind from the name's `kindLabel`, the skill's own label, when it has one; the other reading gives: kind `constant` would carry no usage_signature, leaving the calls uncompared: no gap
  - `fn` (SKILL.md:341), inventory reader: `@coco.fn(batching=True)` and `@coco.fn(runner=GPU)` (SKILL.md:190 and :341), which the skill says raise ValueError, are neither removed nor old-version, so they stay call forms of fn; left open by: A form the skill marks as removed, or as the form of a version before the one it covers (a migration table's old-version column, a cell or row labelled gone, removed, before or old), is not a form of the current export and gives no entry; the other reading gives: dropped, they give no entry: no gap; kept, they pass keywords references/component-api.md:172 says `@coco.fn(...)` declares, so no gap expected
  - `is_live_component_class` (SKILL.md:167), inventory reader: '**internal**, not exported on `coco`' reads as saying the source does not export it, so SKILL.md:167's `is_live_component_class(cls) -> bool` gives no entry; the fenced declaration at references/live-components.md:14 does; left open by: A name the skill presents only as a local import alias of another name, or says the source does not export, is not an export the skill documents either: it gets an entry only from a place `inventory-floor.json` gives it, a heading, an export table's first cell or a fenced declaration of it (an import is not one), never from a code span in prose or a description cell; the other reading gives: an entry at SKILL.md:167 (params `cls`, return `bool`) agreeing with live-components.md:14: no split-body mismatch, no gap
  - `AsyncCallable` (references/component-api.md:245), inventory reader: `AsyncCallable[P, R]` is `Callable[P, Coroutine[Any, Any, R]]` writes none of the listed forms, so AsyncCallable stays a type mention with no entry; likewise MountKind (component-api.md:324, only as `MountKind = Literal[...]` and a field type), AnyCallable, TargetActionSinkFn and AsyncTargetActionSinkFn; left open by: A name the skill writes only in a type position (a parameter type, a return type or a type argument inside another entry's documented type or signature, or a parameter table's Type cell) is a type mention, not an export the skill documents, even when its code span is exactly the name, and gets no entry, unless the skill also writes it as one outside a type position: a place `inventory-floor.json` gives it, a heading, an export table's first cell, a code span that is the name or the name then `(`, or a fenced declaration; the other reading gives: `type` entries with no compared form: no signature gap (only a stale-name gap if the source exports no such name)
  - `_default_env` (SKILL.md:175), inventory reader: names the skill calls private or writes as underscore-prefixed internals (`_default_env`, `_FunctionDecorator`, `_DualModeRuntime`, `_ItemsType`, `_TopicMapFeed`, `_SyncFunctionBuilder`, `_TypedTargetHandlerWrapper`, `_MountEachLiveComponent`, `_load_app`, `_get_persisted_app_names`, `_create_project_files`, `_ensure_metadata`) are not documented exports and get no entry; FileLike's abstract `_fetch_metadata` / `_read_impl` / `_compute_content_fingerprint` are kept as methods because its class body documents them for subclasses; left open by: A name the skill presents only as a local import alias of another name, or says the source does not export, is not an export the skill documents either: it gets an entry only from a place `inventory-floor.json` gives it, a heading, an export table's first cell or a fenced declaration of it (an import is not one), never from a code span in prose or a description cell; the other reading gives: mention entries with no form: no signature gap
  - `ComponentStats` (SKILL.md:244), inventory reader: the Key Types block's NamedTuple fields, properties and methods written in comments (ComponentStats, UpdateStats, UpdateSnapshot, MemoStateOutcome, UpdateHandle, DropHandle) are not recorded; the comment text serves only as description, and UpdateHandle / DropHandle get their entries at references/component-api.md:46 (which lists `stats()` and `result()`) rather than at SKILL.md:247-248; left open by: A comment in a fenced block is no place of its own and states no form or return type: a form or a return it writes (`// start: ({ options }: {...}) => Promise<void>`, `# returns the dataset's PipelineRunInfo`) is a note on the code, not a form of the name; the other reading gives: fields or methods recorded from the comments would still be uncompared: no gap
  - `register_memo_key_function` (SKILL.md:265), inventory reader: the Key Types line `register_memo_key_function(typ, key_fn, *, state_fn=None)` writes a bare `*`, so it is no call but a signature line and an entry of its own; `is_non_existence(obj)` (:259) and `memo_fingerprint(obj)` (:264) are calls in the fence and give no entry beside SKILL.md:164 / :165; left open by: A call or JSX element of a name that a fenced example writes is not a place of its own when the skill also writes that name's form at a place that is no example (a heading, a table row, a props table, running text or a fenced declaration), unless the nearest heading above the example names a usage, its text holding the word usage whatever qualifies it (`## Usage`, `### Basic usage`, `### Usage pattern`; a bold label line such as `**Usage:**` is no heading): it gives no entry, so it is never compared, and a name whose only forms are in fenced examples keeps them; the other reading gives: no entry at SKILL.md:265: no gap (it is identical to SKILL.md:165)
  - `__call__` (references/target-state.md:45), inventory reader: the two `__call__` defs under 'Sink-fn signature' are method entries whose owners, TargetActionSinkFn (sync, :45) and AsyncTargetActionSinkFn (async, :50), are inferred from the block's `[SRC:...target_state.py:L99] [:L121]` citations and the types on lines 36 and 38; those owners appear only in type positions and get no entry; left open by: A `method`'s `name` is the bare method name and its `owner` the class or object it is called on (`agents` for `cognee.agents.get`, where the skill documents `agents` as a class; the class for one reached through a property, `client.messages`); `owner` is not validated; the other reading gives: no method entries: no gap
  - `walk_dir` (SKILL.md:82), inventory reader: `walk_dir(..., live=True)` writes an argument beside the `...`, so it is a partial call form, and walk_dir's fenced-example calls (SKILL.md:75, references/connectors.md:197, references/resources.md:101) give no entry; left open by: A name written with empty parentheses, or with only `...` or `…` between them, in running text or a description cell is a mention, not a form; the other reading gives: as a mention, walk_dir's fenced-example calls would become its entries instead: no gap expected
  - `mount_table_target` (references/live-components.md:85), inventory reader: the sentence covers running text and description cells only, so in a fenced example `postgres.mount_table_target(...)` is a call whose `...` stands for omitted arguments: a partial usage entry, since the name's only forms are in fenced examples; left open by: A name written with empty parentheses, or with only `...` or `…` between them, in running text or a description cell is a mention, not a form; the other reading gives: a mention with no entry: no gap
  - `GPURunner` (SKILL.md:190), inventory reader: `GPURunner()` is the name then `(` outside a type position, so GPURunner is a documented export with a mention entry; likewise LazyEnvironment (SKILL.md:175), Function / SyncFunction / AsyncFunction (SKILL.md:275), get_default_db_path (references/component-api.md:82) and `R` (fenced declaration, references/settings-cli.md:93); left open by: A name the skill writes only in a type position (a parameter type, a return type or a type argument inside another entry's documented type or signature, or a parameter table's Type cell) is a type mention, not an export the skill documents, even when its code span is exactly the name, and gets no entry, unless the skill also writes it as one outside a type position: a place `inventory-floor.json` gives it, a heading, an export table's first cell, a code span that is the name or the name then `(`, or a fenced declaration; the other reading gives: no entries: no signature gap (a stale-name gap only if the source exports no such name)
  - `Chunk` (references/ops.md:83), inventory reader: prose that lists a name's members gives it an entry there: Chunk's `text`, `start: TextPosition`, `end: TextPosition` (ops.md:83, as fields), DirWalker's and S3Walker's `items()` (SKILL.md:346, connectors.md:218), UpdateHandle / DropHandle's `stats()` and `result()` (component-api.md:46), MultiVectorSchema / MultiVectorSchemaProvider (resources.md:212); a `Class.method()` mention (resources.md:28, component-api.md:311, live-components.md:65, settings-cli.md:65) is read as a mention of the method, not a member list of the class; left open by: A place that writes a name but no form of it, and no `methods`, `properties` or `fields` its entry would carry (a mention, a bare code span, an import, a heading or prose that names or describes it), gives it no entry when another place gives the name one, unless `inventory-floor.json` gives that place; of several such places of a name the skill documents and no other place gives an entry, the first alone gives one: in SKILL.md, else the file that sorts first by path, at its lowest line; the other reading gives: no gap either way (the members are not compared)
  - `File` (references/connectors.md:181), inventory reader: SKILL.md:346's `(relative_path, File)` is a type position, so File's first place is the connectors.md `__all__` line; every `__all__` string is read as a place that writes the name (the connector mention entries), and a receiver in a fenced call is a place too (TableSchema at SKILL.md:72, TableTarget at SKILL.md:326); left open by: of several such places of a name the skill documents and no other place gives an entry, the first alone gives one: in SKILL.md, else the file that sorts first by path, at its lowest line; the other reading gives: a different first line for these mention entries: no gap
  - `TargetState` (references/target-state.md:93), inventory reader: 'A `TargetState` bundles `(provider, key, value)`' describes what the instance bundles, not a parameter list written for the name, so it gives no entry beside the class body at target-state.md:83; left open by: while a class's form written as a parameter list or a signature that is not such a call stays in `params`; the other reading gives: an entry with params `provider, key, value` (bare names) matching target-state.md:83: no gap
  - `get_component_context` (SKILL.md:207), inventory reader: the first cell `get_component_context()` (and `runtime()` at SKILL.md:189), where the floor gives no signature, is an empty call recorded in usage_signature; left open by: a heading or an export table's first cell that writes `name()` is a form, recorded as written; the other reading gives: params `""` would claim it takes none; the references declare none, so no gap either way
  - `TargetStateProvider` (SKILL.md:192), inventory reader: `memo_key`, listed bare beside `target_state(key, value)` and `attachment(att_type)`, is recorded as a property (references/target-state.md:70 declares it with @property), not a methods item; left open by: Each `methods` item starts with the method's name, optionally after `async` (`async next_uuid(dep=None)`); the other reading gives: a methods item `memo_key`: uncompared, no gap
  - `watch` (SKILL.md:201), inventory reader: the row's single `watch(subscriber)`, written once for LiveMapFeed and LiveMapView, gives one method entry with owner LiveMapFeed (which declares it, live-components.md:52); LiveMapView lists it among its methods only; left open by: A method a place writes with a form of its own (a class body, a methods list, a row's cell, running text) gets a `method` entry there with that form, a call recorded in `usage_signature` as a function's is (`execute(args, kwargs, next_batch_size=None)` in a methods list), besides its class's `methods` item, and so does one the skill calls through an instance or the class it documents with that member; the other reading gives: a second method entry with owner LiveMapView, with no reference counterpart: no gap
  - `provide` (references/component-api.md:126), inventory reader: `provide(key, ctx.enter_context(cm))`, written as what provide_with is equivalent to, is a call of EnvironmentBuilder.provide in running text and a method usage entry; left open by: A method a place writes with a form of its own (a class body, a methods list, a row's cell, running text) gets a `method` entry there with that form; the other reading gives: no entry: no gap (two positional arguments match `provide(key, value)`)
  - `items` (SKILL.md:77), inventory reader: DirWalker's `items()` and ComponentContext's `attach()` are otherwise only mentioned (`files.items()`, `ctx.attach()` with empty parentheses in prose), so their fenced-example calls (SKILL.md:77, references/connectors.md:205; references/component-api.md:317) are kept as method usage entries; the same holds for postgres `mount_table_target` and `TableSchema.from_class`; left open by: A call or JSX element of a name that a fenced example writes is not a place of its own when the skill also writes that name's form at a place that is no example (a heading, a table row, a props table, running text or a fenced declaration), unless the nearest heading above the example names a usage, its text holding the word usage whatever qualifies it (`## Usage`, `### Basic usage`, `### Usage pattern`; a bold label line such as `**Usage:**` is no heading): it gives no entry, so it is never compared, and a name whose only forms are in fenced examples keeps them; the other reading gives: no entries for these example calls: no gap
  - `litellm` (SKILL.md:111), inventory reader: `litellm`, which the skill documents as a re-exported library in cocoindex.ops.litellm's `__all__`, gets a `constant` mention entry; package and submodule names (`text`, `sentence_transformers`, `entity_resolution`, the connector packages) are modules, not exports, and get none; left open by: A place that writes a name but no form of it, and no `methods`, `properties` or `fields` its entry would carry (a mention, a bare code span, an import, a heading or prose that names or describes it), gives it no entry when another place gives the name one, unless `inventory-floor.json` gives that place; of several such places of a name the skill documents and no other place gives an entry, the first alone gives one: in SKILL.md, else the file that sorts first by path, at its lowest line; the other reading gives: no entry for litellm, or entries for the submodules: no signature gap
  - `App` (SKILL.md:309), inventory reader: only the migration table's `v0.3.37 (gone)` column is dropped; calls in its `v1.0.0 (replacement)` column are current forms (App, AppConfig, mount_each, topic_as_map, map, mount, declare_row, App.update, SentenceTransformerEmbedder, LiteLLMEmbedder, detect_code_language, declare_vector_index, Settings, EnvironmentBuilder.provide, use_context); left open by: A form the skill marks as removed, or as the form of a version before the one it covers (a migration table's old-version column, a cell or row labelled gone, removed, before or old), is not a form of the current export and gives no entry; the other reading gives: dropping the replacement column too would remove those entries: no gap
  - `LlmPairResolver` (references/ops.md:201), inventory reader: the block that imports LlmPairResolver and then writes `class LlmPairResolver:` defines no undocumented name and does not decorate it with itself, so the class body is its form; likewise generate_id / generate_uuid (resources.md:140 / :146), decorated with `@coco.fn(memo=True)`, not with themselves; the Quick Start's DocEmbedding / process_chunk / process_file / app_main / env_lifespan and target-state.md's MyTableHandler block (with its `mount_table_target`) are reader code; left open by: A function or class an example defines is the reader's own code, not a form of a same-named export, only at a place `inventory-floor.json` gives no `signature` and only when its fenced block also defines names the skill does not document as exports or, whatever else the block defines, decorates the definition with, passes it to or registers it through that export itself, by its name or through a receiver or module path; the other reading gives: reader code would leave these forms uncompared: no gap
  - `use_mount` (python/cocoindex/_internal/api.py:194), signature judge: Form 0 (`processor_fn: AsyncCallable[P, ResolvesTo[ReturnT]] | Callable[P, ResolvesTo[ReturnT]] | AsyncCallable[P, ReturnT] | Callable[P, ReturnT], *args, **kwargs -> ReturnT`) matches no single overload and not the `(*pos_args: Any, **kwargs: Any) -> Any` implementation; I took the position-by-position union over the four overloads that share its shape (lines 222-244, no leading `subpath`), whose `processor_fn` types union to exactly the documented type, so no mismatch; left open by: A declaration opening an overload set (Python `@overload` stubs, TS bodiless signatures) is read through its implementation: a documented signature matching the implementation or any overload is no mismatch, and so is one whose parameter types are, position by position, the unions of the overloads' types; the other reading gives: Taking the union across all eight overloads, including the four leading with `subpath: ComponentSubpath` (lines 194-220), puts `subpath`/`processor_fn` at position 0 and `processor_fn`/`*args` at position 1, so the documented list would match no union position by position: a Critical mismatch (untagged) for form 0
  - `mount_target` (python/cocoindex/_internal/api.py:566), signature judge: Form 2's return `TargetStateProvider[ValueT, OptChildHandlerT]` (with a usage that writes no parameter types) against the source's `TargetStateProvider[_ValueT, _ChildHandlerT]`: I read `ValueT`->`_ValueT` and `OptChildHandlerT`->`_ChildHandlerT` as a consistent renaming of type variables, so no mismatch, although those names resolve to target_state.py's own TypeVars (`ValueT` with default=Any; `OptChildHandlerT` with the same bound but default=None, covariant=True), not api.py's `_ValueT`/`_ChildHandlerT`; left open by: Type variables renamed consistently: `(a: T) -> T` against `(a: U) -> U`, but not `(a: T, b: U)` against `(a: U, b: U)`; the other reading gives: Reading them as the distinct TypeVars target_state.py declares (different defaults and variance), not a rename, makes the return type differ: a Critical mismatch (untagged) for form 2
  - `exception_handler` (python/cocoindex/_internal/component_ctx.py:331), signature judge: Form 1 (`handler: ExceptionHandler` -> `AsyncIterator[None]`) was compared with the return annotation that the `async def` at line 331 declares, `AsyncIterator[None]`, so it matches. No rule says how the stdlib `@contextlib.asynccontextmanager` decorator, which is outside the source tree, enters the comparison. That decorator rebinds the name to a function returning an async context manager (`_AsyncGeneratorContextManager[None]`); left open by: The source's declaration decides: the documented form is compared with the parameters, the optionality and the annotations the signature declares, with one exception, a return annotation the body contradicts (Annotations); the other reading gives: If the decorated callable's return type were compared, form 1's `AsyncIterator[None]` would be a Critical return-type mismatch (no tag). If the decorator's out-of-tree return were left uncompared, it would be no mismatch
  - `fn` (python/cocoindex/_internal/function.py:1811), signature judge: Form 1 `coco.fn(version=N, logic_tracking="full"|"self"|None, deps=...)` is read as a usage (a call through the `coco.` module path passing `name=value` arguments whose values, the placeholder `N`, the value alternation `"full"|"self"|None` and the Ellipsis `...`, are not compared), so it is compared as a call with `_FunctionDecorator.__call__` (the instance-call rule): `version`, `logic_tracking` and `deps` all exist as keyword-only parameters of the implementation (line 1626) and of the first overload (line 1585), and no required parameter is left out, so it matches; left open by: An entry's `usage_signature` written as a usage is read this way, and each usage in a list of usages is compared as a form of its own, under its entry's `form` index; the other reading gives: Read instead as a signature whose `=` values are defaults (the literal union looking like a `Literal[...]` type), the form would claim a complete list and leave out `memo` against the nearest overload (line 1585), and `fn`, `memo`, `batching`, `max_batch_size` and `runner` against the implementation: a mismatch tagged omitted-optional, Critical against a full form
- **Nested Entry Points:** `python/cocoindex/connectors/amazon_s3/__init__.py` inside `python/cocoindex/__init__.py`: `S3File`, `S3FilePath`, `S3Walker`, `get_object`, `list_objects`, `read`; `python/cocoindex/connectors/doris/__init__.py` inside `python/cocoindex/__init__.py`: `ColumnDef`, `DorisConnectionConfig`, `DorisTableTarget`, `DorisType`, `InvertedIndexDef`, `ManagedConnection`, `RetryConfig`, `TableSchema`, `ValueEncoder`, `VectorIndexDef`, `build_vector_search_query`, `connect`, `connect_async`, `declare_table_target`, `mount_table_target`, `table_target`; `python/cocoindex/connectors/google_drive/__init__.py` inside `python/cocoindex/__init__.py`: `DriveFile`, `DriveFileInfo`, `GoogleDriveSource`, `GoogleDriveSourceSpec`, `list_files`; `python/cocoindex/connectors/kafka/__init__.py` inside `python/cocoindex/__init__.py`: `DeletionValueFn`, `IsDeleteFn`, `KafkaTopicTarget`, `declare_kafka_topic_target`, `kafka_topic_target`, `mount_kafka_topic_target`, `topic_as_map`; `python/cocoindex/connectors/lancedb/__init__.py` inside `python/cocoindex/__init__.py`: `ColumnDef`, `LanceAsyncConnection`, `LanceType`, `TableSchema`, `TableTarget`, `ValueEncoder`, `connect`, `connect_async`, `declare_table_target`, `mount_table_target`, `table_target`; `python/cocoindex/connectors/localfs/__init__.py` inside `python/cocoindex/__init__.py`: `DirTarget`, `DirWalker`, `File`, `FilePath`, `declare_dir_target`, `declare_file`, `dir_target`, `mount_dir_target`, `walk_dir`; `python/cocoindex/connectors/postgres/__init__.py` inside `python/cocoindex/__init__.py`: `ColumnDef`, `PgSourceSpec`, `PgTableSource`, `PgType`, `RowFetcher`, `TableSchema`, `TableTarget`, `ValueEncoder`, `create_pool`, `declare_table_target`, `mount_table_target`, `table_target`; `python/cocoindex/connectors/qdrant/__init__.py` inside `python/cocoindex/__init__.py`: `CollectionSchema`, `CollectionTarget`, `PointStruct`, `QdrantVectorDef`, `collection_target`, `create_client`, `declare_collection_target`, `mount_collection_target`; `python/cocoindex/connectors/sqlite/__init__.py` inside `python/cocoindex/__init__.py`: `ColumnDef`, `ManagedConnection`, `SqliteType`, `TableSchema`, `TableTarget`, `ValueEncoder`, `Vec0TableDef`, `connect`, `declare_table_target`, `managed_connection`, `mount_table_target`, `table_target`; `python/cocoindex/connectors/surrealdb/__init__.py` inside `python/cocoindex/__init__.py`: `ColumnDef`, `ConnectionFactory`, `RelationTarget`, `SurrealType`, `TableSchema`, `TableTarget`, `ValueEncoder`, `declare_relation_target`, `declare_table_target`, `mount_relation_target`, `mount_table_target`, `relation_target`, `table_target`
- **Extraction Gaps:** `DeletionValueFn` (python/cocoindex/connectors/kafka/_target.py:206), `ExceptionHandler` (python/cocoindex/_internal/component_ctx.py:25), `GPU` (python/cocoindex/_internal/runner.py:282), `IsDeleteFn` (python/cocoindex/connectors/kafka/_source.py:30), `LanceAsyncConnection` (not located), `LifespanFn` (python/cocoindex/_internal/environment.py:118), `LogicTracking` (python/cocoindex/_internal/function.py:65), `MaybePendingS` (python/cocoindex/_internal/pending_marker.py:115), `NON_EXISTENCE` (python/cocoindex/_internal/typing.py:60), `PendingTargetStateProvider` (python/cocoindex/_internal/target_state.py:243), `PointStruct` (python/cocoindex/connectors/qdrant/_target.py:42), `ROOT_PATH` (python/cocoindex/_internal/stable_path.py:59), `StableKey` (python/cocoindex/_internal/stable_path.py:9), `Symbol` (python/cocoindex/_internal/stable_path.py:7), `ValueEncoder` (python/cocoindex/connectors/doris/_target.py:79), `fn` (python/cocoindex/_internal/function.py:1811)

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 100% |
| Signature Accuracy | 100% |
| Type Coverage | 100% |

**Notes:**

- §1a: the subagent inventory passed schema validation, the ground-truth spot-check (`App`, `declare_kafka_topic_target`, `watch`) and the floor check (49 of 49 floor names kept); 410 entries over SKILL.md and 7 reference files; 0 forms left unbound for want of a place.
- §1b: the inventory reader cross-checked the SKILL.md body against the 7 reference files (149 names written in two or more files) and found no split-body mismatch.
- §2: the recipe runner read every in-scope file (no file read by eye, none unread, no fallback scan); no unresolved star re-export. The signature plan compared 43 names across 16 source files, judged by 16 subagents: 0 mismatches.
- §2b: numerator ground truth skipped (no inflation signature: 118 names declared in `exports[]`).
- §2c: 48 documented names lie outside the root barrel's `all` set; `classify-stale` finds 47 of them still declared in the source (documented extras) and 1, `R`, declared in 5 files with no single cited declaration.
- §4: no guard fires (deflation not applicable, inflation -9.74%, no stale `scope.include` glob).
- §4b: metadata count cross-check: one Medium finding, `stats.exports_public_api` = 140 against `exports[].length` = 118 (16% drift).
- §4c: provenance line check: 154 entries checked, 0 stale lines (12 line checks skipped by the helper).

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)

### Structural Findings

| # | Type | Severity | Detail | Line |
|---|------|----------|--------|------|
| - | none | - | No structural issue: §2.1 the `usage` family is served by `## Quick Start` (line 12) and the `api_surface` family by `## Key API Summary` (line 170); the `description` family is satisfied by the non-empty frontmatter `description`. §2.2 the 8 code fences are balanced; §2.3 no opening fence lacks a language tag; §2.4 each of the 116 function and method exports is referenced in the usage scope (no zero-usage export); §2.5 every export the skill describes as async is awaited in its examples and none described as sync is awaited (43 called exports read); §2.6 no table row drifts from its header; §2.7 no `scripts/` or `assets/` folder. §2b: the evidence report pins `t2_future_count: 0` and SKILL.md has no `## Migration & Deprecation Warnings` heading (`## Migration from v0.3.37` is not Section 4b), so no Case applies. | - |

**Structural Issues:** 0

### Reference Consistency (split-body)

| # | Reference File | Export | Issue | Other Side | Reference Line | Contradicted Side |
|---|---------------|--------|-------|------------|---------------|-------------------|
| - | none | - | No split-body mismatch | - | - | - |

**Exports Cross-Checked:** 149
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
**External Validators:** skill-check only
**Analysis Confidence:** full
**Tooling Status:** ok

## Gap Report

**Total Gaps:** 49
**Blocking (Critical + High):** 0
**Non-blocking (Medium + Low + Info):** 49

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|------------------|
| Critical | 0 | None |
| High | 0 | None |
| Medium | 2 | stale-documentation (1): check each name against the source and the brief's scope, then update or remove its documentation or fix the scope (Update Skill does not repair it); metadata-drift (1): re-run Create Skill or edit the brief's scope, as each remediation says (counts that differ only by `Type::method` entries need no fix, and a hand edit of the counts does not hold) |
| Low | 0 | None |
| Info | 47 | observation (47): apply each only when you agree, as its remediation says, since it is advisory (a documented extra needs no change) |
| **Total** | **49** | |

### GAP-027: Stale documentation: R

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/settings-cli.md:93
**Export:** R

**Issue:** `references/settings-cli.md:93` documents `R`, which the enumerated source API surface lacks

**Remediation:** Check `R` against the source and update or remove its documentation at references/settings-cli.md:93: the enumerated source surface does not export it.

### GAP-049: metadata drift — barrel export counts diverge

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

### GAP-011: Documented extra: GPURunner

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/runner.py:212
**Export:** GPURunner

**Issue:** `SKILL.md:190` documents `GPURunner`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `GPURunner` is a documented extra, a name the source still declares at `python/cocoindex/_internal/runner.py:212` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-012: Documented extra: GlobalExecutionOptions

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/setting.py:12
**Export:** GlobalExecutionOptions

**Issue:** `SKILL.md:213` documents `GlobalExecutionOptions`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `GlobalExecutionOptions` is a documented extra, a name the source still declares at `python/cocoindex/setting.py:12` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-013: Documented extra: IdGenerator

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/id.py:89
**Export:** IdGenerator

**Issue:** `SKILL.md:348` documents `IdGenerator`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `IdGenerator` is a documented extra, a name the source still declares at `python/cocoindex/resources/id.py:89` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-014: Documented extra: LazyEnvironment

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/environment.py:287
**Export:** LazyEnvironment

**Issue:** `SKILL.md:175` documents `LazyEnvironment`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LazyEnvironment` is a documented extra, a name the source still declares at `python/cocoindex/_internal/environment.py:287` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-015: Documented extra: LiteLLMEmbedder

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/litellm.py:22
**Export:** LiteLLMEmbedder

**Issue:** `SKILL.md:320` documents `LiteLLMEmbedder`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LiteLLMEmbedder` is a documented extra, a name the source still declares at `python/cocoindex/ops/litellm.py:22` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-016: Documented extra: LlmPairResolver

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/llm_resolver.py:49
**Export:** LlmPairResolver

**Issue:** `references/ops.md:195` documents `LlmPairResolver`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LlmPairResolver` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/llm_resolver.py:49` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-017: Documented extra: MatchAllFilePathMatcher

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/file.py:215
**Export:** MatchAllFilePathMatcher

**Issue:** `references/resources.md:89` documents `MatchAllFilePathMatcher`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MatchAllFilePathMatcher` is a documented extra, a name the source still declares at `python/cocoindex/resources/file.py:215` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

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

### GAP-043: Documented extra: get_default_db_path

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/setting.py:12
**Export:** get_default_db_path

**Issue:** `references/component-api.md:82` documents `get_default_db_path`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_default_db_path` is a documented extra, a name the source still declares at `python/cocoindex/_internal/setting.py:12` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-044: Documented extra: get_multi_vector_schema

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:58
**Export:** get_multi_vector_schema

**Issue:** `SKILL.md:168` documents `get_multi_vector_schema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_multi_vector_schema` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:58` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-045: Documented extra: get_vector_schema

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:33
**Export:** get_vector_schema

**Issue:** `SKILL.md:168` documents `get_vector_schema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_vector_schema` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:33` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-046: Documented extra: is_live_component_class

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/live_component.py:35
**Export:** is_live_component_class

**Issue:** `SKILL.md:167` documents `is_live_component_class`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `is_live_component_class` is a documented extra, a name the source still declares at `python/cocoindex/_internal/live_component.py:35` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-047: Documented extra: litellm

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/litellm.py:1
**Export:** litellm

**Issue:** `references/ops.md:150` documents `litellm`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `litellm` is a documented extra, a name the source still declares at `python/cocoindex/ops/litellm.py:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-048: Documented extra: resolve_entities

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
| 1 | can you help me set up something that keeps the embeddings for my docs folder in sync with a vector table, so only the files that changed get processed again? | oms-cocoindex (high) | PASS |
| 2 | why does my ingestion job re-embed every single file on each run when only one of them changed? | oms-cocoindex (medium) | PASS |
| 3 | run the incremental indexing thing on this folder and keep it watching for file changes | oms-cocoindex (high) | PASS |

Catalog: the 4 skills in `skills/` (oms-cocoindex, oms-cognee, oms-storybook-react-vite, oms-uitripled), each by its frontmatter description. The 3 prompts were synthesized (SKILL.md has no Triggers section or conversational example prompts) and name no export, skill or library. No description optimization hints: Tessl Review did not run and skill-check flagged no description issue.
