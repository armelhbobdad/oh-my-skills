---
workflowType: 'test-skill'
skillName: 'oms-cocoindex'
skillDir: 'skills/oms-cocoindex/1.0.0/oms-cocoindex'
runId: '20261108T055052Z-019a0d7f'
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
testDate: '2026-11-08T05:50:52Z'
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

**Mode Rationale:** metadata.json records `skill_type: "single"`, so this is an individual skill: naive mode (API-surface coverage; structural coherence only, no coherence category in scoring).

**Analysis Plan:**
- Coverage Check: Deep tier — enumerate the public API surface from the pinned source (5fe4f37, v1.0.0) under the skill brief's scope with AST-backed extraction, check each export is documented in SKILL.md and its references, compare documented signatures against the source declarations, and check type coverage.
- Coherence Check: structural only (naive mode) — references cited in SKILL.md resolve, internal links and section structure are sound; no cross-skill integration scoring.

## Coverage Analysis

**Tier:** Deep
**Source Access:** full
**Source Path:** /home/armel/.skf/workspace/repos/github.com/cocoindex-io/cocoindex
**Workspace Layout:** single package
**Denominator:** barrel (standard-barrel clause, `all` set: the 72 root exports python/cocoindex/__init__.py re-exports from python/cocoindex/_internal/api.py)

**Files Analyzed:** 30

### Export Coverage

| Export | Type | Documented | Signature | Source Location | Status |
|--------|------|------------|-----------|-----------------|--------|
| `App` | class | yes | yes | python/cocoindex/_internal/app.py:208 | PASS |
| `AppConfig` | class | yes | yes | python/cocoindex/_internal/app.py:202 | PASS |
| `CanonicalSide` | - | yes | - | - | WARN |
| `ChildTargetDef` | class | yes | yes | python/cocoindex/_internal/target_state.py:95 | PASS |
| `Chunk` | - | yes | - | - | WARN |
| `ComponentContext` | class | yes | - | python/cocoindex/_internal/component_ctx.py:55 | PASS |
| `ComponentMountHandle` | class | yes | - | python/cocoindex/_internal/api.py:170 | PASS |
| `ComponentStats` | class | yes | yes | python/cocoindex/_internal/update_stats.py:14 | PASS |
| `ComponentSubpath` | class | yes | yes | python/cocoindex/_internal/component_ctx.py:142 | PASS |
| `ContextKey` | class | yes | yes | python/cocoindex/_internal/context_keys.py:99 | PASS |
| `ContextProvider` | class | yes | - | python/cocoindex/_internal/context_keys.py:124 | PASS |
| `CustomLanguageConfig` | - | yes | - | - | WARN |
| `DropHandle` | class | yes | - | python/cocoindex/_internal/app.py:143 | PASS |
| `Embedder` | - | yes | - | - | WARN |
| `Environment` | class | yes | yes | python/cocoindex/_internal/environment.py:183 | PASS |
| `EnvironmentBuilder` | class | yes | yes | python/cocoindex/_internal/environment.py:87 | PASS |
| `ExceptionContext` | class | yes | yes | python/cocoindex/_internal/component_ctx.py:43 | PASS |
| `ExceptionHandler` | - | yes | - | python/cocoindex/_internal/component_ctx.py:25 | PASS |
| `ExistingCanonicalPolicy` | - | yes | - | - | WARN |
| `FileLike` | - | yes | - | - | WARN |
| `FileMetadata` | - | yes | - | - | WARN |
| `FilePathMatcher` | - | yes | - | - | WARN |
| `GPU` | - | yes | - | python/cocoindex/_internal/runner.py:282 | PASS |
| `GlobalExecutionOptions` | - | yes | - | - | WARN |
| `IdGenerator` | - | yes | - | - | WARN |
| `LifespanFn` | - | yes | - | python/cocoindex/_internal/environment.py:118 | PASS |
| `LiteLLMEmbedder` | - | yes | - | - | WARN |
| `LiveComponent` | class | yes | - | python/cocoindex/_internal/live_component.py:28 | PASS |
| `LiveComponentOperator` | class | yes | - | python/cocoindex/_internal/live_component.py:46 | PASS |
| `LiveMapFeed` | class | yes | - | python/cocoindex/_internal/live_component.py:108 | PASS |
| `LiveMapSubscriber` | class | yes | - | python/cocoindex/_internal/live_component.py:130 | PASS |
| `LiveMapView` | class | yes | - | python/cocoindex/_internal/live_component.py:119 | PASS |
| `LlmPairResolver` | - | yes | - | - | WARN |
| `LogicTracking` | - | yes | - | python/cocoindex/_internal/function.py:65 | PASS |
| `MatchAllFilePathMatcher` | - | yes | - | - | WARN |
| `MaybePendingS` | - | yes | - | python/cocoindex/_internal/pending_marker.py:115 | PASS |
| `MemoStateOutcome` | class | yes | yes | python/cocoindex/_internal/typing.py:67 | PASS |
| `MultiVectorSchema` | - | yes | - | - | WARN |
| `MultiVectorSchemaProvider` | - | yes | - | - | WARN |
| `NON_EXISTENCE` | - | yes | - | python/cocoindex/_internal/typing.py:60 | PASS |
| `NonExistenceType` | class | yes | - | python/cocoindex/_internal/typing.py:47 | PASS |
| `NotMemoKeyable` | class | yes | - | python/cocoindex/_internal/memo_fingerprint.py:136 | PASS |
| `PairDecision` | - | yes | - | - | WARN |
| `PairResolver` | - | yes | - | - | WARN |
| `PatternFilePathMatcher` | - | yes | - | - | WARN |
| `PendingS` | class | yes | - | python/cocoindex/_internal/pending_marker.py:74 | PASS |
| `PendingTargetStateProvider` | - | yes | - | python/cocoindex/_internal/target_state.py:243 | PASS |
| `QueryHandlerInfo` | - | yes | - | - | WARN |
| `QueryHandlerResultFields` | - | yes | - | - | WARN |
| `QueryInfo` | - | yes | - | - | WARN |
| `QueryOutput` | - | yes | - | - | WARN |
| `ROOT_PATH` | - | yes | - | python/cocoindex/_internal/stable_path.py:59 | PASS |
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
| `StableKey` | - | yes | - | python/cocoindex/_internal/stable_path.py:9 | PASS |
| `StablePath` | class | yes | yes | python/cocoindex/_internal/stable_path.py:16 | PASS |
| `Symbol` | - | yes | yes | python/cocoindex/_internal/stable_path.py:7 | PASS |
| `TargetActionSink` | class | yes | - | python/cocoindex/_internal/target_state.py:143 | PASS |
| `TargetHandler` | class | yes | - | python/cocoindex/_internal/target_state.py:197 | PASS |
| `TargetReconcileOutput` | class | yes | yes | python/cocoindex/_internal/target_state.py:188 | PASS |
| `TargetState` | class | yes | yes | python/cocoindex/_internal/target_state.py:248 | PASS |
| `TargetStateProvider` | class | yes | - | python/cocoindex/_internal/target_state.py:208 | PASS |
| `TextPosition` | - | yes | - | - | WARN |
| `UpdateHandle` | class | yes | - | python/cocoindex/_internal/app.py:49 | PASS |
| `UpdateSnapshot` | class | yes | yes | python/cocoindex/_internal/update_stats.py:59 | PASS |
| `UpdateStats` | class | yes | yes | python/cocoindex/_internal/update_stats.py:39 | PASS |
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
- **Stale Documentation:** 41, documented extras included
- **Nested Entry Points:** `python/cocoindex/connectors/amazon_s3/__init__.py` inside `python/cocoindex/__init__.py`: `S3File`, `S3FilePath`, `S3Walker`, `get_object`, `list_objects`, `read`; `python/cocoindex/connectors/doris/__init__.py` inside `python/cocoindex/__init__.py`: `ColumnDef`, `DorisConnectionConfig`, `DorisTableTarget`, `DorisType`, `InvertedIndexDef`, `ManagedConnection`, `RetryConfig`, `TableSchema`, `ValueEncoder`, `VectorIndexDef`, `build_vector_search_query`, `connect`, `connect_async`, `declare_table_target`, `mount_table_target`, `table_target`; `python/cocoindex/connectors/google_drive/__init__.py` inside `python/cocoindex/__init__.py`: `DriveFile`, `DriveFileInfo`, `GoogleDriveSource`, `GoogleDriveSourceSpec`, `list_files`; `python/cocoindex/connectors/kafka/__init__.py` inside `python/cocoindex/__init__.py`: `DeletionValueFn`, `IsDeleteFn`, `KafkaTopicTarget`, `declare_kafka_topic_target`, `kafka_topic_target`, `mount_kafka_topic_target`, `topic_as_map`; `python/cocoindex/connectors/lancedb/__init__.py` inside `python/cocoindex/__init__.py`: `ColumnDef`, `LanceAsyncConnection`, `LanceType`, `TableSchema`, `TableTarget`, `ValueEncoder`, `connect`, `connect_async`, `declare_table_target`, `mount_table_target`, `table_target`; `python/cocoindex/connectors/localfs/__init__.py` inside `python/cocoindex/__init__.py`: `DirTarget`, `DirWalker`, `File`, `FilePath`, `declare_dir_target`, `declare_file`, `dir_target`, `mount_dir_target`, `walk_dir`; `python/cocoindex/connectors/postgres/__init__.py` inside `python/cocoindex/__init__.py`: `ColumnDef`, `PgSourceSpec`, `PgTableSource`, `PgType`, `RowFetcher`, `TableSchema`, `TableTarget`, `ValueEncoder`, `create_pool`, `declare_table_target`, `mount_table_target`, `table_target`; `python/cocoindex/connectors/qdrant/__init__.py` inside `python/cocoindex/__init__.py`: `CollectionSchema`, `CollectionTarget`, `PointStruct`, `QdrantVectorDef`, `collection_target`, `create_client`, `declare_collection_target`, `mount_collection_target`; `python/cocoindex/connectors/sqlite/__init__.py` inside `python/cocoindex/__init__.py`: `ColumnDef`, `ManagedConnection`, `SqliteType`, `TableSchema`, `TableTarget`, `ValueEncoder`, `Vec0TableDef`, `connect`, `declare_table_target`, `managed_connection`, `mount_table_target`, `table_target`; `python/cocoindex/connectors/surrealdb/__init__.py` inside `python/cocoindex/__init__.py`: `ColumnDef`, `ConnectionFactory`, `RelationTarget`, `SurrealType`, `TableSchema`, `TableTarget`, `ValueEncoder`, `declare_relation_target`, `declare_table_target`, `mount_relation_target`, `mount_table_target`, `relation_target`, `table_target`

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 100% |
| Signature Accuracy | 100% |
| Type Coverage | 100% |

### Coverage Notes

- **Reader and judges ran in the main thread.** This session had no subagent tool, so coverage-check §1's documented inventory and §2's 48 signature checks (17 `files[]` entries) were built and judged in the main thread, as the step's "without subagents" path says, by `references/inventory-contract.md` and `references/signature-comparison-rules.md` word for word. The inventory has 328 entries over 131 names (the floor's 49 names all kept, every compared form placed with an `at`); `validate-inventory.py` passed it with 0 violations and 0 warnings, so no form was left unbound for want of a place. `crossChecked`: 99 names.
- **Split-body cross-check (§1b):** no mismatch recorded (see borderline call 1, which decides whether `lifespan` has one).
- **Extraction:** recipe runner status `ok`, 92 files in scope, no file read by eye (`readByEye` empty), none unread, no fallback scan, no unresolved star re-export. `extractionGaps` (names no recipe found, on the surface, read by eye at their line): `DeletionValueFn`, `ExceptionHandler`, `GPU`, `IsDeleteFn`, `LanceAsyncConnection` (no file: an import alias in `connectors/lancedb`), `LifespanFn`, `LogicTracking`, `MaybePendingS`, `NON_EXISTENCE`, `PendingTargetStateProvider`, `PointStruct`, `ROOT_PATH`, `StableKey`, `Symbol`, `ValueEncoder`, `fn`. Of these only `fn` (`fn = _FunctionDecorator()`, compared with `_FunctionDecorator.__call__` at python/cocoindex/_internal/function.py:1585-1637) and `Symbol` (`Symbol = core.Symbol`, compared with `core.pyi:26` `__new__(cls, name: str)`) carry a documented form; both match.
- **Denominator:** clause `standard-barrel`, set `all` = `root` = 72 names, the `__all__` of python/cocoindex/_internal/api.py that python/cocoindex/__init__.py re-exports. The `scope.include` set holds 139 names (30 files); 10 nested connector entry points leave `all` (listed above). Guards: deflation not applicable (no stored `effective_denominator`), inflation does not fire (139 against 154 provenance entries, -9.74%), stale scope does not fire (no unmatched `scope.include` or `scope.tier_a_include` glob, nothing restored). No name is restored, so every `all`-set kind comes from the extraction: 61 of the 72 names carry one (36 `class`, 25 `function`), and the 11 `extractionGaps` names on the surface (`ExceptionHandler`, `GPU`, `LifespanFn`, `LogicTracking`, `MaybePendingS`, `NON_EXISTENCE`, `PendingTargetStateProvider`, `ROOT_PATH`, `StableKey`, `Symbol`, `fn`: five type aliases, a TypeVar, an alias of the class `core.Symbol`, three constants and the `fn` decorator instance) carry none. Type Coverage counts the 36 classes, all documented, and `score-signatures.py` gives no warning; the five type aliases, the TypeVar and `Symbol` among the 11 are documented too (Key Types block, component-api.md, target-state.md), but Type Coverage does not count them.
- **Stale names (41):** documented names outside the 72-name surface (`ops.*`, `resources.*`, `cocoindex.setting`, `cocoindex.query_handler`, `cli`, the internal `is_live_component_class`, `litellm`). `classify-stale` found none fabricated; each has a `defined_at`, or several declaring files of which the skill's citations on a line naming it cite exactly one (`Chunk`, `CustomLanguageConfig`, `RecursiveSplitter`, `SeparatorSplitter`, `detect_code_language`, each also stubbed in `_internal/core.pyi`), and the brief scopes none out, so §5b records them as Info documented extras.
- **Metadata counts (§4b):** `stats.exports_public_api` 140 against `exports[].length` 118 (16% drift), one Medium `metadata-drift` gap; the documented cluster agrees (154 / 154 / 154). Numerator check skipped (no inflation signature).
- **Provenance line check (§4c):** no stale line.

#### Borderline calls (rules leave these undecided; how this run counted each)

1. **`lifespan`, references/settings-cli.md:43** — documented: `async def lifespan(builder: coco.EnvironmentBuilder):`, decorated `@coco.lifespan` at :42, in a block (:41-47) that defines no other name. Source: python/cocoindex/_internal/environment.py:449-451, `def lifespan(fn: LifespanFn) -> LifespanFn`, `def lifespan(fn: None) -> Callable[[LifespanFn], LifespanFn]`, implementation `def lifespan(fn: LifespanFn | None = None) -> Any`. Open sentence: inventory-contract.md:27, "A function or class an example defines as the reader's own code is not a form of a same-named export: when its fenced block also defines names the skill does not document as exports, ... its entry there leaves `params`, `return_type` and `usage_signature` out". The lead clause covers this def (it is the reader's own lifespan); the operational clause names only a block that also defines another undocumented name, which this block does not. **Counted:** not a form (the lead clause), so it is never compared and no split-body pair is formed. **Other reading:** a form, giving a Critical `signature-mismatch` (`builder: coco.EnvironmentBuilder` against `fn: LifespanFn`) and a High `split-body-mismatch` against references/component-api.md:107-110; the hard gate would block.
2. **`default_env`, references/component-api.md:135** — documented: `async def default_env() -> Environment: ...`. Source: python/cocoindex/_internal/api.py:623, `async def default_env() -> environment.Environment:` (api.py imports `from . import environment`; the class is `coco.Environment`). Open sentence: signature-comparison-rules.md Equivalent spellings, "Two spellings of one type are no mismatch:", whose prefix bullet lists only `typing.`, `collections.abc.` and `React.` (SKF #999). **Counted:** match (two spellings of one class). **Other reading:** a return-type mismatch with no difference tag, a Critical `signature-mismatch`; the hard gate would block.
3. **`AppConfig`, references/component-api.md:36** — documented in running text: `AppConfig(name=name_or_config)`. Source: python/cocoindex/_internal/app.py:202-205, dataclass fields `name: str`, `environment: Environment | LazyEnvironment = _default_env`, `max_inflight_components: int | None = None`. Open sentence: inventory-contract.md:25 records a call expression in `usage_signature` "after `await`, `new` or an assignment, through a receiver or module path such as `coco.`, or as a statement in a fenced example", and running text is none of these; signature-comparison-rules.md "Reading a form" reads a form that passes values (`name=value`) as a call. **Counted:** a call (`usage_signature`), which matches. **Other reading:** `params` "name=name_or_config", which states `name` optional against a required field, a Critical `signature-mismatch`.
4. **`Symbol`, SKILL.md:100 and references/component-api.md:221** — documented in running text: `Symbol(fn.__name__)` and `Symbol(processor_fn.__name__)`. Source: python/cocoindex/_internal/stable_path.py:7, `Symbol = core.Symbol`, stub python/cocoindex/_internal/core.pyi:26 `def __new__(cls, name: str) -> Symbol`. Open sentence: the same inventory-contract.md:25 call-expression clause. **Counted:** calls passing one value, which match. **Other reading:** `params` "fn.__name__" as a bare parameter name against `name`, a Critical `signature-mismatch`.
5. **Not decisive (recorded for completeness):** the Key Types listing (SKILL.md:244-246, :259-265) was read as forms, including the `# NamedTuple(...)` comment forms of `ComponentStats`, `UpdateStats`, `UpdateSnapshot` and `MemoStateOutcome`, and `VectorSchema(dtype=..., size=...)` at references/connectors.md:68 as a call; each matches its declaration under either reading, or names a symbol outside the surface that is never compared.

Calls 1 to 4 each decide the hard gate: under the other reading of any one of them, the run gets a Critical gap and the hard gate blocks it.

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)

### Structural Findings

| # | Type | Severity | Detail | Line |
|---|------|----------|--------|------|
| - | none | - | No structural issue: the `description` family is served by the frontmatter `description`, `usage` by `## Quick Start`, `api_surface` by `## Key API Summary`; 8 fences, balanced, each opening fence tagged; no table row drifts from its header; no `scripts/` or `assets/` folder; all 39 function and method exports are used in the usage-family scope (SKILL.md body and the 7 reference files); no export described as async lacks an `await` in its examples, and none described as sync is awaited | - |

**Structural Issues:** 0

**Async/sync check (§2.5):** 38 exports and methods have a call in fenced code. The async-described ones are each directly awaited at least once: `mount`, `mount_each`, `mount_target`, `map`, `start`, `stop`, `default_env`, `show_progress`, `generate_id`, `mount_table_target`, `mount_collection_target`, `resolve_entities`, `App.update` (2 of 3 calls; the third, `handle = app.update()` at SKILL.md:141, hands the handle to `await coco.show_progress(handle)`), the `LiveComponentOperator` methods, `FileLike.read_text`, `IdGenerator.next_id` and `Embedder.embed`. No sync-described export is directly awaited. The indirect awaits are `async with coco.runtime()` (a consumer), `coco.component_subpath(...)` inside the arguments of an awaited `coco.mount` or `operator.update`, and `await coco.use_context(EMBEDDER).embed(...)` (a chain), and none of these raises a finding.

**Migration section (§2b):** Deep tier, and the evidence report pins `t2_future_count: 0`. SKILL.md has no section titled "Migration & Deprecation Warnings". Its `## Migration from v0.3.37` (SKILL.md:303) is historical v0.3.37 to v1.0.0 mapping content. Read as Section 4b, it would be Case 2, an Info gap; read by its title, as this run reads it, Section 4b is absent, which no case flags. Neither reading blocks (SKF #1000 tracks the open question).

### Reference Consistency (split-body)

| # | Reference File | Export | Issue | Other Side | Reference Line | Contradicted Side |
|---|---------------|--------|-------|------------|---------------|-------------------|
| - | - | - | none: no form contradicts another across SKILL.md and the 7 reference files (borderline call 1 in Coverage Notes decides `lifespan`) | - | - | - |

**Exports Cross-Checked:** 99
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
**Scoring Notes:** this PASS depends on borderline calls 1 to 4 in the Coverage Analysis section's Coverage Notes; under the other reading of any one of them the hard gate blocks the run and it is not scored.

## Gap Report

**Total Gaps:** 43
**Blocking (Critical + High):** 0
**Non-blocking (Medium + Low + Info):** 43

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|------------------|
| Critical | 0 | None |
| High | 0 | None |
| Medium | 1 | Add type definitions, interface docs or the missing section |
| Low | 0 | None |
| Info | 42 | Optional improvements, no action required |
| **Total** | **43** | |

### GAP-042: metadata drift — barrel export counts diverge

**Severity:** Medium
**Category:** Coverage (metadata-drift)
**Source:** skills/oms-cocoindex/1.0.0/oms-cocoindex/metadata.json

**Issue:** stats.exports_public_api=140, exports[].length=118 → 16% drift

**Remediation:** Re-run Create Skill, which rebuilds `exports[]` and `stats.exports_public_api` in `skills/oms-cocoindex/1.0.0/oms-cocoindex/metadata.json` from the source. Update Skill does not repair this drift: each time it writes the skill it recounts `stats.exports_public_api` from the source and keeps `exports[]`, adding or dropping only the names its provenance map changes, so a metadata patch does not hold.

### GAP-001: Documented extra: CanonicalSide

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:35
**Export:** CanonicalSide

**Issue:** `references/ops.md:184` documents `CanonicalSide`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CanonicalSide` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:35` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-002: Documented extra: Chunk

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/chunk.py:26
**Export:** Chunk

**Issue:** `SKILL.md:348` documents `Chunk`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `python/cocoindex/resources/chunk.py`

**Remediation:** No change: `Chunk` is a documented extra, a name the source still declares at `python/cocoindex/resources/chunk.py:26` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-003: Documented extra: CustomLanguageConfig

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/text.py:87
**Export:** CustomLanguageConfig

**Issue:** `references/ops.md:85` documents `CustomLanguageConfig`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `python/cocoindex/ops/text.py`

**Remediation:** No change: `CustomLanguageConfig` is a documented extra, a name the source still declares at `python/cocoindex/ops/text.py:87` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-004: Documented extra: Embedder

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/embedder.py:15
**Export:** Embedder

**Issue:** `SKILL.md:168` documents `Embedder`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Embedder` is a documented extra, a name the source still declares at `python/cocoindex/resources/embedder.py:15` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-005: Documented extra: ExistingCanonicalPolicy

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:57
**Export:** ExistingCanonicalPolicy

**Issue:** `references/ops.md:211` documents `ExistingCanonicalPolicy`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ExistingCanonicalPolicy` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:57` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-006: Documented extra: FileLike

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/file.py:56
**Export:** FileLike

**Issue:** `references/resources.md:51` documents `FileLike`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `FileLike` is a documented extra, a name the source still declares at `python/cocoindex/resources/file.py:56` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-007: Documented extra: FileMetadata

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/file.py:40
**Export:** FileMetadata

**Issue:** `references/resources.md:41` documents `FileMetadata`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `FileMetadata` is a documented extra, a name the source still declares at `python/cocoindex/resources/file.py:40` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-008: Documented extra: FilePathMatcher

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/file.py:205
**Export:** FilePathMatcher

**Issue:** `references/resources.md:80` documents `FilePathMatcher`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `FilePathMatcher` is a documented extra, a name the source still declares at `python/cocoindex/resources/file.py:205` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-009: Documented extra: GlobalExecutionOptions

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/setting.py:12
**Export:** GlobalExecutionOptions

**Issue:** `SKILL.md:213` documents `GlobalExecutionOptions`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `GlobalExecutionOptions` is a documented extra, a name the source still declares at `python/cocoindex/setting.py:12` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-010: Documented extra: IdGenerator

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/id.py:89
**Export:** IdGenerator

**Issue:** `SKILL.md:348` documents `IdGenerator`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `IdGenerator` is a documented extra, a name the source still declares at `python/cocoindex/resources/id.py:89` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-011: Documented extra: LiteLLMEmbedder

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/litellm.py:22
**Export:** LiteLLMEmbedder

**Issue:** `SKILL.md:325` documents `LiteLLMEmbedder`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LiteLLMEmbedder` is a documented extra, a name the source still declares at `python/cocoindex/ops/litellm.py:22` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-012: Documented extra: LlmPairResolver

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/llm_resolver.py:49
**Export:** LlmPairResolver

**Issue:** `references/ops.md:195` documents `LlmPairResolver`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LlmPairResolver` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/llm_resolver.py:49` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-013: Documented extra: MatchAllFilePathMatcher

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/file.py:215
**Export:** MatchAllFilePathMatcher

**Issue:** `references/resources.md:89` documents `MatchAllFilePathMatcher`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MatchAllFilePathMatcher` is a documented extra, a name the source still declares at `python/cocoindex/resources/file.py:215` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-014: Documented extra: MultiVectorSchema

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:49
**Export:** MultiVectorSchema

**Issue:** `references/resources.md:212` documents `MultiVectorSchema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MultiVectorSchema` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:49` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-015: Documented extra: MultiVectorSchemaProvider

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:43
**Export:** MultiVectorSchemaProvider

**Issue:** `references/connectors.md:68` documents `MultiVectorSchemaProvider`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MultiVectorSchemaProvider` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:43` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-016: Documented extra: PairDecision

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:46
**Export:** PairDecision

**Issue:** `references/ops.md:211` documents `PairDecision`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PairDecision` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:46` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-017: Documented extra: PairResolver

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:97
**Export:** PairResolver

**Issue:** `references/ops.md:195` documents `PairResolver`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PairResolver` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:97` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-018: Documented extra: PatternFilePathMatcher

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/file.py:227
**Export:** PatternFilePathMatcher

**Issue:** `SKILL.md:348` documents `PatternFilePathMatcher`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PatternFilePathMatcher` is a documented extra, a name the source still declares at `python/cocoindex/resources/file.py:227` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-019: Documented extra: QueryHandlerInfo

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/query_handler.py:21
**Export:** QueryHandlerInfo

**Issue:** `SKILL.md:214` documents `QueryHandlerInfo`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `QueryHandlerInfo` is a documented extra, a name the source still declares at `python/cocoindex/query_handler.py:21` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-020: Documented extra: QueryHandlerResultFields

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/query_handler.py:10
**Export:** QueryHandlerResultFields

**Issue:** `SKILL.md:215` documents `QueryHandlerResultFields`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `QueryHandlerResultFields` is a documented extra, a name the source still declares at `python/cocoindex/query_handler.py:10` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-021: Documented extra: QueryInfo

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/query_handler.py:30
**Export:** QueryInfo

**Issue:** `SKILL.md:216` documents `QueryInfo`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `QueryInfo` is a documented extra, a name the source still declares at `python/cocoindex/query_handler.py:30` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-022: Documented extra: QueryOutput

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/query_handler.py:43
**Export:** QueryOutput

**Issue:** `SKILL.md:217` documents `QueryOutput`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `QueryOutput` is a documented extra, a name the source still declares at `python/cocoindex/query_handler.py:43` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-023: Documented extra: RecursiveSplitter

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/text.py:120
**Export:** RecursiveSplitter

**Issue:** `references/ops.md:59` documents `RecursiveSplitter`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `python/cocoindex/ops/text.py`

**Remediation:** No change: `RecursiveSplitter` is a documented extra, a name the source still declares at `python/cocoindex/ops/text.py:120` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-024: Documented extra: ResolutionEvent

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:70
**Export:** ResolutionEvent

**Issue:** `references/ops.md:187` documents `ResolutionEvent`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ResolutionEvent` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:70` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-025: Documented extra: ResolvedEntities

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:114
**Export:** ResolvedEntities

**Issue:** `references/ops.md:211` documents `ResolvedEntities`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ResolvedEntities` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:114` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-026: Documented extra: SentenceTransformerEmbedder

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/sentence_transformers.py:25
**Export:** SentenceTransformerEmbedder

**Issue:** `references/resources.md:220` documents `SentenceTransformerEmbedder`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `SentenceTransformerEmbedder` is a documented extra, a name the source still declares at `python/cocoindex/ops/sentence_transformers.py:25` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-027: Documented extra: SeparatorSplitter

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/text.py:39
**Export:** SeparatorSplitter

**Issue:** `references/ops.md:35` documents `SeparatorSplitter`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `python/cocoindex/ops/text.py`

**Remediation:** No change: `SeparatorSplitter` is a documented extra, a name the source still declares at `python/cocoindex/ops/text.py:39` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-028: Documented extra: ServerSettings

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/setting.py:93
**Export:** ServerSettings

**Issue:** `SKILL.md:212` documents `ServerSettings`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ServerSettings` is a documented extra, a name the source still declares at `python/cocoindex/setting.py:93` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-029: Documented extra: TextPosition

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/chunk.py:9
**Export:** TextPosition

**Issue:** `SKILL.md:348` documents `TextPosition`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `TextPosition` is a documented extra, a name the source still declares at `python/cocoindex/resources/chunk.py:9` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-030: Documented extra: UuidGenerator

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/id.py:152
**Export:** UuidGenerator

**Issue:** `SKILL.md:348` documents `UuidGenerator`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `UuidGenerator` is a documented extra, a name the source still declares at `python/cocoindex/resources/id.py:152` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-031: Documented extra: VectorSchema

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:23
**Export:** VectorSchema

**Issue:** `SKILL.md:348` documents `VectorSchema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `VectorSchema` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:23` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-032: Documented extra: VectorSchemaProvider

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:17
**Export:** VectorSchemaProvider

**Issue:** `SKILL.md:348` documents `VectorSchemaProvider`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `VectorSchemaProvider` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:17` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-033: Documented extra: cli

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/cli.py:505
**Export:** cli

**Issue:** `SKILL.md:218` documents `cli`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `cli` is a documented extra, a name the source still declares at `python/cocoindex/cli.py:505` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-034: Documented extra: detect_code_language

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/text.py:19
**Export:** detect_code_language

**Issue:** `references/ops.md:20` documents `detect_code_language`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `python/cocoindex/ops/text.py`

**Remediation:** No change: `detect_code_language` is a documented extra, a name the source still declares at `python/cocoindex/ops/text.py:19` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-035: Documented extra: generate_id

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/id.py:31
**Export:** generate_id

**Issue:** `references/resources.md:140` documents `generate_id`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `generate_id` is a documented extra, a name the source still declares at `python/cocoindex/resources/id.py:31` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-036: Documented extra: generate_uuid

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/id.py:61
**Export:** generate_uuid

**Issue:** `references/resources.md:168` documents `generate_uuid`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `generate_uuid` is a documented extra, a name the source still declares at `python/cocoindex/resources/id.py:61` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-037: Documented extra: get_multi_vector_schema

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:58
**Export:** get_multi_vector_schema

**Issue:** `references/resources.md:187` documents `get_multi_vector_schema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_multi_vector_schema` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:58` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-038: Documented extra: get_vector_schema

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:33
**Export:** get_vector_schema

**Issue:** `references/resources.md:210` documents `get_vector_schema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_vector_schema` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:33` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-039: Documented extra: is_live_component_class

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/live_component.py:35
**Export:** is_live_component_class

**Issue:** `SKILL.md:167` documents `is_live_component_class`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `is_live_component_class` is a documented extra, a name the source still declares at `python/cocoindex/_internal/live_component.py:35` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-040: Documented extra: litellm

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/litellm.py:1
**Export:** litellm

**Issue:** `SKILL.md:111` documents `litellm`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `litellm` is a documented extra, a name the source still declares at `python/cocoindex/ops/litellm.py:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-041: Documented extra: resolve_entities

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:186
**Export:** resolve_entities

**Issue:** `references/ops.md:211` documents `resolve_entities`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `resolve_entities` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:186` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-043: Discovery testing not performed: subagents unavailable, routing test requires isolated context

**Severity:** Info
**Category:** Discovery (discovery)
**Source:** SKILL.md:3

**Issue:** This session could not spawn subagents; the main thread knows which skill is under test, so it may not route the prompts itself (report.md §4b.2).

**Remediation:** Re-run test-skill in an environment that can spawn subagents, so each of the three realistic prompts is routed against the 4-skill catalog in an isolated context.

### Discovery Quality

**Discovery Test:** skipped: subagents unavailable, routing test requires isolated context

discovery: skipped, subagents unavailable, routing test requires isolated context (catalog: 4 skills, oms-cocoindex, oms-cognee, oms-storybook-react-vite, oms-uitripled; this session cannot spawn subagents, so the main thread, which knows the skill under test, did not route the prompts). No description optimization hints: Tessl Review did not run and skill-check flagged no description issue.
