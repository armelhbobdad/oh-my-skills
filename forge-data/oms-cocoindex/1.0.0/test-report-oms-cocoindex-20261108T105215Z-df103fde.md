---
workflowType: 'test-skill'
skillName: 'oms-cocoindex'
skillDir: 'skills/oms-cocoindex/1.0.0/oms-cocoindex'
runId: '20261108T105215Z-df103fde'
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
testDate: '2026-11-08T10:52:15Z'
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

**Mode Rationale:** metadata.json records `skill_type: "single"`, an individual skill, so naive mode applies: API-surface coverage, with a structural-only coherence check and no coherence category in the score.

**Analysis Plan:**
- Coverage Check: every public export of the cocoindex v1.0.0 source (pinned commit 5fe4f37) checked for documentation in SKILL.md and its references; at Deep tier, signatures and types of the documented exports are compared against the AST-backed source declarations.
- Coherence Check: structural only (naive mode): references named in SKILL.md resolve, and the documented sections are internally consistent.

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
| `Function` | - | yes | - | - | WARN |
| `GPU` | - | yes | - | python/cocoindex/_internal/runner.py:282 | PASS |
| `GPURunner` | - | yes | - | - | WARN |
| `GlobalExecutionOptions` | - | yes | - | - | WARN |
| `IdGenerator` | - | yes | - | - | WARN |
| `LazyEnvironment` | - | yes | - | - | WARN |
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
| `MountKind` | - | yes | - | - | WARN |
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
| `StablePath` | class | yes | - | python/cocoindex/_internal/stable_path.py:16 | PASS |
| `Symbol` | - | yes | yes | python/cocoindex/_internal/stable_path.py:7 | PASS |
| `SyncFunction` | - | yes | - | - | WARN |
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
| `sentence_transformers` | - | yes | - | - | WARN |
| `serialize_by_pickle` | function | yes | yes | python/cocoindex/_internal/serde.py:151 | PASS |
| `show_progress` | function | yes | yes | python/cocoindex/_internal/app.py:194 | PASS |
| `start` | function | yes | yes | python/cocoindex/_internal/api.py:603 | PASS |
| `start_blocking` | function | yes | yes | python/cocoindex/_internal/api.py:613 | PASS |
| `stop` | function | yes | yes | python/cocoindex/_internal/api.py:608 | PASS |
| `stop_blocking` | function | yes | yes | python/cocoindex/_internal/api.py:618 | PASS |
| `text` | - | yes | - | - | WARN |
| `unpickle_safe` | function | yes | yes | python/cocoindex/_internal/serde.py:128 | PASS |
| `use_context` | function | yes | yes | python/cocoindex/_internal/component_ctx.py:273 | PASS |
| `use_mount` | function | yes | yes | python/cocoindex/_internal/api.py:194 | PASS |

### Coverage Summary

- **Exports Found:** 72
- **Documented:** 72 (100%)
- **Missing Documentation:** 0
- **Signature Mismatches:** 0
- **Stale Documentation:** 50, documented extras included
- **Nested Entry Points:** `python/cocoindex/connectors/amazon_s3/__init__.py` inside `python/cocoindex/__init__.py`: `S3File`, `S3FilePath`, `S3Walker`, `get_object`, `list_objects`, `read`; `python/cocoindex/connectors/doris/__init__.py` inside `python/cocoindex/__init__.py`: `ColumnDef`, `DorisConnectionConfig`, `DorisTableTarget`, `DorisType`, `InvertedIndexDef`, `ManagedConnection`, `RetryConfig`, `TableSchema`, `ValueEncoder`, `VectorIndexDef`, `build_vector_search_query`, `connect`, `connect_async`, `declare_table_target`, `mount_table_target`, `table_target`; `python/cocoindex/connectors/google_drive/__init__.py` inside `python/cocoindex/__init__.py`: `DriveFile`, `DriveFileInfo`, `GoogleDriveSource`, `GoogleDriveSourceSpec`, `list_files`; `python/cocoindex/connectors/kafka/__init__.py` inside `python/cocoindex/__init__.py`: `DeletionValueFn`, `IsDeleteFn`, `KafkaTopicTarget`, `declare_kafka_topic_target`, `kafka_topic_target`, `mount_kafka_topic_target`, `topic_as_map`; `python/cocoindex/connectors/lancedb/__init__.py` inside `python/cocoindex/__init__.py`: `ColumnDef`, `LanceAsyncConnection`, `LanceType`, `TableSchema`, `TableTarget`, `ValueEncoder`, `connect`, `connect_async`, `declare_table_target`, `mount_table_target`, `table_target`; `python/cocoindex/connectors/localfs/__init__.py` inside `python/cocoindex/__init__.py`: `DirTarget`, `DirWalker`, `File`, `FilePath`, `declare_dir_target`, `declare_file`, `dir_target`, `mount_dir_target`, `walk_dir`; `python/cocoindex/connectors/postgres/__init__.py` inside `python/cocoindex/__init__.py`: `ColumnDef`, `PgSourceSpec`, `PgTableSource`, `PgType`, `RowFetcher`, `TableSchema`, `TableTarget`, `ValueEncoder`, `create_pool`, `declare_table_target`, `mount_table_target`, `table_target`; `python/cocoindex/connectors/qdrant/__init__.py` inside `python/cocoindex/__init__.py`: `CollectionSchema`, `CollectionTarget`, `PointStruct`, `QdrantVectorDef`, `collection_target`, `create_client`, `declare_collection_target`, `mount_collection_target`; `python/cocoindex/connectors/sqlite/__init__.py` inside `python/cocoindex/__init__.py`: `ColumnDef`, `ManagedConnection`, `SqliteType`, `TableSchema`, `TableTarget`, `ValueEncoder`, `Vec0TableDef`, `connect`, `declare_table_target`, `managed_connection`, `mount_table_target`, `table_target`; `python/cocoindex/connectors/surrealdb/__init__.py` inside `python/cocoindex/__init__.py`: `ColumnDef`, `ConnectionFactory`, `RelationTarget`, `SurrealType`, `TableSchema`, `TableTarget`, `ValueEncoder`, `declare_relation_target`, `declare_table_target`, `mount_relation_target`, `mount_table_target`, `relation_target`, `table_target`

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 100% |
| Signature Accuracy | 100% |
| Type Coverage | 100% |

### Run Notes

- **Inventory (§1, one reader subagent):** 435 documented forms across 190 names in SKILL.md and the 7 reference files; the floor's 49 names all listed (49 checked, none missing); 110 names written in two or more files cross-checked (§1b): 0 split-body mismatches. The validator listed 0 warnings, so no form was left unbound for want of a place (`at`).
- **Extraction (§2):** recipe runner status `ok`, 92 files in scope (Python), no fallback scan. No file read by eye, no file unread, no unresolved star re-export. `extractionGaps` (exports no recipe matched, on the surface and read at their declarations): `DeletionValueFn`, `ExceptionHandler`, `GPU`, `IsDeleteFn`, `LanceAsyncConnection`, `LifespanFn`, `LogicTracking`, `MaybePendingS`, `NON_EXISTENCE`, `PendingTargetStateProvider`, `PointStruct`, `ROOT_PATH`, `StableKey`, `Symbol`, `ValueEncoder`, `fn`; the two with a compared documented form (`fn` at function.py:1811, `Symbol` at stable_path.py:7) were judged at those lines.
- **Signatures (§2, 17 judge subagents, one per plan file):** 48 names compared over 17 source files, 0 mismatches; `score` raised no warning. Signature Accuracy 100% (48/48), Type Coverage 100% (36/36 types of the `all` set).
- **Numerator ground truth (§2b):** skipped (no inflation signature: `stats.exports_documented` 154 is not the denominator).
- **Stale names (§2c):** 50 documented names the root surface (`all` set, 72) does not hold, mostly connector, ops and resources names behind nested `__init__.py` entry points (`excluded.nestedEntries`). `classify-stale`: 0 fabricated, 45 with a `defined_at`, 5 declared in two files each (a `core.pyi` stub and the module): `Chunk`, `CustomLanguageConfig`, `RecursiveSplitter`, `SeparatorSplitter`, `detect_code_language`.
- **Metadata count cross-check (§4b):** one Medium finding, `stats.exports_public_api` 140 against `exports[].length` 118 (16% drift, threshold 10%); recorded as a `metadata-drift` gap. It changes no denominator.
- **Provenance line check (§4c):** 118 exports and 154 map entries checked against the pinned source: 0 stale lines (36 orphaned map entries are outside this check's scope).

### Coverage Notes

Calls the signature rules left undecided in this run. None changed the score as counted; the first would have, counted the other way.

1. **`Settings`, removed v0.3.37 form not compared.** Documented form: `Settings(database=DatabaseConnectionSpec(url=...))`, the "v0.3.37 (gone)" column of the migration table at `SKILL.md:327` (the same row's v1.0.0 column, `coco.Settings(db_path=pathlib.Path("state.lmdb"))`, is compared). Source: `@dataclass class Settings` at `python/cocoindex/_internal/setting.py:56`, fields `db_path`, `global_execution_options`, `lmdb_max_dbs`, `lmdb_map_size`, no `database` and no `**kwargs`. Rule text that left it open: inventory-contract.md, "A name documented in several places is listed once per place, each entry with that place's form", with no sentence on a migration table's removed-API column. Counted as: not a form of the 1.0.0 export (the inventory reader left it out; nothing compared). Counted as a form, it would be a call passing a keyword the constructor lacks: a Critical `signature-mismatch` (Python) that blocks the hard gate.
2. **`default_env`, module-qualified return type.** Documented form: `params ""`, return `Environment` at `references/component-api.md:135`. Source: `async def default_env() -> environment.Environment:` at `python/cocoindex/_internal/api.py:623`. Rule text that left it open: Equivalent spellings, "A name with or without its `typing.`, `collections.abc.` or `React.` prefix", which names no project-module prefix. Counted as: match (the same class, imported from `.environment`).
3. **`use_mount`, union over overloads.** Documented form: `processor_fn: AsyncCallable[P, ResolvesTo[ReturnT]] | Callable[P, ResolvesTo[ReturnT]] | AsyncCallable[P, ReturnT] | Callable[P, ReturnT], *args, **kwargs` returning `ReturnT` at `references/component-api.md:237`. Source: the overload set at `python/cocoindex/_internal/api.py:194` (implementation at :245). Rule text that left it open: Overload sets, "and so is one whose parameter types are, position by position, the unions of the overloads' types", which does not say whether the union spans all 8 overloads or the 4 that take no `subpath`. Counted as: match (the 4 no-`subpath` overloads, lines 222/228/234/240, union exactly to the documented type).
4. **`mount_target`, type variables renamed in the return only.** Documented form: return `TargetStateProvider[ValueT, OptChildHandlerT]` with usage `await coco.mount_target(target_state)` at `SKILL.md:184`. Source: `-> TargetStateProvider[_ValueT, _ChildHandlerT]` at `python/cocoindex/_internal/api.py:566`. Rule text that left it open: Equivalent spellings, "Type variables renamed consistently: `(a: T) -> T` against `(a: U) -> U`", whose example renames across parameters and return, not in a return alone. Counted as: match (a one-to-one renaming to `TargetStateProvider`'s own type parameters, target_state.py:35 and :42).
5. **`register_memo_key_function`, bare `*` inside a call.** Documented form: `coco.register_memo_key_function(typ, key_fn, *, state_fn=None)` at `SKILL.md:165`, recorded as a usage because it is written through `coco.` (inventory-contract.md: "is recorded whole in `usage_signature` ... whatever names its arguments use"). Source: `(typ: type, key_fn: _KeyFn, *, state_fn: _StateFn | None = None) -> None` at `python/cocoindex/_internal/memo_fingerprint.py:155`. Rule text that left it open: "A call written with placeholder names ... its names are arguments at their positions", which does not cover a `*` marker inside a call. Counted as: match (read as a call, and as the keyword-only marker the source also writes; either way it matches).
6. **`runtime` and `get_component_context`, empty calls in an export table's first cell.** Documented forms: `runtime()` at `SKILL.md:189` and `get_component_context()` at `SKILL.md:207`, recorded as usages. Source: `def runtime() -> _DualModeRuntime` at `python/cocoindex/_internal/api.py:655` and `def get_component_context() -> ComponentContext` at `python/cocoindex/_internal/component_ctx.py:305`. Rule text that left it open: "a heading or an export table's first cell that writes `name()` is a form, an empty call", while inventory-contract.md's usage contexts do not list a table's first cell. Counted as: match (both declarations take no parameter, so the forms match as an empty call or as `params ""`).
7. **`get_component_context`, call after an assignment in prose.** Text: `ctx = coco.get_component_context()` at `SKILL.md:159`. Rule text that left it open: "A name written with empty parentheses in running text ... is a mention", against inventory-contract.md's "a call expression (after `await`, `new` or an assignment ...) is recorded whole in `usage_signature`". Counted as: a mention (not compared); as a form it would be an empty call against a declaration with no parameter, so a match.
8. **Key Types comments.** The `# NamedTuple(...)` field lists at `SKILL.md:244`–`246` and `:260` were recorded as `params`, and `# TypeIs[NonExistenceType]` (`:259`) and `# core.Fingerprint` (`:264`) as return types. Rule text that left it open: Annotations, "the form writes one: after `->`, `=>`, `→` or `):`, or in its language's own position", silent on a comment. Counted as: compared; each matched its declaration (`MemoStateOutcome` typing.py:67, `is_non_existence` typing.py:63, `memo_fingerprint` memo_fingerprint.py:361, the update-stats NamedTuples).
9. **Migration section, Section 4b or not.** Text: `## Migration from v0.3.37` at `SKILL.md:303`, a table of v0.3.37 names (column "v0.3.37 (gone)") against their v1.0.0 replacements. Evidence report: `t2_future_count: 0`. Rule text that left it open: migration-section-rules.md, "Check whether SKILL.md contains a "Migration & Deprecation Warnings" section (Section 4b)", with Case 2 covering "historical migration content" in Section 4b; the rules do not say whether a migration section under another heading is Section 4b. Counted as: Section 4b absent, no migration-section gap. Counted the other way it is Case 2, an Info gap that changes no score.

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)

### Structural Findings

| # | Type | Severity | Detail | Line |
|---|------|----------|--------|------|
| - | none | - | No structural issue: the `description` family is served by the non-empty frontmatter description (the `usage` family matched `Quick Start`, line 12; `api_surface` matched `Key API Summary`, line 170); 8 code fences, balanced, none without a language tag; no table row off its header's column count; no `scripts/` or `assets/` folder; every one of the 63 function and method exports the usage scope counts (split body: Quick Start, Common Workflows, Key API Summary and the 7 reference files) is used there; the async/sync check found every export described as async awaited in its examples and no export described as sync awaited or handed to a runner. | - |

**Structural Issues:** 0

**Migration section (§2b):** the gate ran (Deep tier, evidence report present) and the evidence report pins `t2_future_count: 0`. SKILL.md has no Section 4b ("Migration & Deprecation Warnings"); its `## Migration from v0.3.37` (line 303) is a v0.3.37-to-v1.0.0 mapping table. With no T2-future annotation and no Section 4b, no case of the migration-section rules applies: no gap (see Coverage Notes item 9).

### Reference Consistency (split-body)

| # | Reference File | Export | Issue | Other Side | Reference Line | Contradicted Side |
|---|---------------|--------|-------|------------|---------------|-------------------|
| - | - | - | none | - | - | - |

**Exports Cross-Checked:** 110
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

**Total Gaps:** 51
**Blocking (Critical + High):** 0
**Non-blocking (Medium + Low + Info):** 51

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|------------------|
| Critical | 0 | None |
| High | 0 | None |
| Medium | 1 | Add type definitions, interface docs or the missing section |
| Low | 0 | None |
| Info | 50 | Optional improvements, no action required |
| **Total** | **51** | |

### GAP-051: metadata drift — barrel export counts diverge

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

**Issue:** `SKILL.md:348` documents `Chunk`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `python/cocoindex/resources/chunk.py`

**Remediation:** No change: `Chunk` is a documented extra, a name the source still declares at `python/cocoindex/resources/chunk.py:26` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-004: Documented extra: CustomLanguageConfig

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/text.py:87
**Export:** CustomLanguageConfig

**Issue:** `references/ops.md:85` documents `CustomLanguageConfig`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `python/cocoindex/ops/text.py`

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

**Issue:** `SKILL.md:325` documents `LiteLLMEmbedder`, which the enumerated source API surface lacks and the source still declares

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

### GAP-018: Documented extra: MountKind

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/component_ctx.py:39
**Export:** MountKind

**Issue:** the skill documents `MountKind`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MountKind` is a documented extra, a name the source still declares at `python/cocoindex/_internal/component_ctx.py:39` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-019: Documented extra: MultiVectorSchema

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:49
**Export:** MultiVectorSchema

**Issue:** `references/resources.md:212` documents `MultiVectorSchema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MultiVectorSchema` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:49` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-020: Documented extra: MultiVectorSchemaProvider

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:43
**Export:** MultiVectorSchemaProvider

**Issue:** `references/connectors.md:68` documents `MultiVectorSchemaProvider`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MultiVectorSchemaProvider` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:43` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-021: Documented extra: PairDecision

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:46
**Export:** PairDecision

**Issue:** `references/ops.md:211` documents `PairDecision`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PairDecision` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:46` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-022: Documented extra: PairResolver

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:97
**Export:** PairResolver

**Issue:** `references/ops.md:195` documents `PairResolver`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PairResolver` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:97` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-023: Documented extra: PatternFilePathMatcher

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/file.py:227
**Export:** PatternFilePathMatcher

**Issue:** `SKILL.md:348` documents `PatternFilePathMatcher`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PatternFilePathMatcher` is a documented extra, a name the source still declares at `python/cocoindex/resources/file.py:227` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-024: Documented extra: QueryHandlerInfo

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/query_handler.py:21
**Export:** QueryHandlerInfo

**Issue:** `SKILL.md:214` documents `QueryHandlerInfo`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `QueryHandlerInfo` is a documented extra, a name the source still declares at `python/cocoindex/query_handler.py:21` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-025: Documented extra: QueryHandlerResultFields

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/query_handler.py:10
**Export:** QueryHandlerResultFields

**Issue:** `SKILL.md:215` documents `QueryHandlerResultFields`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `QueryHandlerResultFields` is a documented extra, a name the source still declares at `python/cocoindex/query_handler.py:10` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-026: Documented extra: QueryInfo

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/query_handler.py:30
**Export:** QueryInfo

**Issue:** `SKILL.md:216` documents `QueryInfo`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `QueryInfo` is a documented extra, a name the source still declares at `python/cocoindex/query_handler.py:30` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-027: Documented extra: QueryOutput

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

**Issue:** `references/ops.md:59` documents `RecursiveSplitter`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `python/cocoindex/ops/text.py`

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

**Issue:** `references/resources.md:220` documents `SentenceTransformerEmbedder`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `SentenceTransformerEmbedder` is a documented extra, a name the source still declares at `python/cocoindex/ops/sentence_transformers.py:25` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-032: Documented extra: SeparatorSplitter

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/text.py:39
**Export:** SeparatorSplitter

**Issue:** `references/ops.md:35` documents `SeparatorSplitter`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `python/cocoindex/ops/text.py`

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

**Issue:** `references/ops.md:20` documents `detect_code_language`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `python/cocoindex/ops/text.py`

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

**Issue:** `references/resources.md:187` documents `get_multi_vector_schema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_multi_vector_schema` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:58` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-045: Documented extra: get_vector_schema

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:33
**Export:** get_vector_schema

**Issue:** `references/resources.md:210` documents `get_vector_schema`, which the enumerated source API surface lacks and the source still declares

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

**Issue:** `SKILL.md:111` documents `litellm`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `litellm` is a documented extra, a name the source still declares at `python/cocoindex/ops/litellm.py:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-048: Documented extra: resolve_entities

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:186
**Export:** resolve_entities

**Issue:** `references/ops.md:211` documents `resolve_entities`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `resolve_entities` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:186` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-049: Documented extra: sentence_transformers

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/sentence_transformers.py:1
**Export:** sentence_transformers

**Issue:** `references/ops.md:7` documents `sentence_transformers`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `sentence_transformers` is a documented extra, a name the source still declares at `python/cocoindex/ops/sentence_transformers.py:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-050: Documented extra: text

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/text.py:1
**Export:** text

**Issue:** `references/ops.md:83` documents `text`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `text` is a documented extra, a name the source still declares at `python/cocoindex/ops/text.py:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### Discovery Quality

**Discovery Test:** PASS (3/3)

| # | Prompt | Selected Skill | Result |
|---|--------|----------------|--------|
| 1 | can you help me port this old flow_def pipeline my teammate wrote? we bumped cocoindex to 1.0 and nothing imports anymore | oms-cocoindex (high) | PASS |
| 2 | how do i keep a pgvector table of chunk embeddings in sync incrementally as files in a folder get added or deleted, with a component mounted per file? | oms-cocoindex (high) | PASS |
| 3 | set up the lifespan thing so my embedder and db pool get provided once and every @fn can grab them via use_context | oms-cocoindex (high) | PASS |

Catalog: the 4 skills in `skills/` (oms-cocoindex, oms-cognee, oms-storybook-react-vite, oms-uitripled), each given to an isolated routing subagent as name + description only. SKILL.md has no Triggers section or organic example prompts, so the three prompts were synthesized from its capability summary (vague, implicit and abbreviated patterns); two of them do not name the library.
