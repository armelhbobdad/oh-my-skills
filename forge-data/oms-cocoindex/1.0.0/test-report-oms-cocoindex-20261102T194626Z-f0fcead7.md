---
workflowType: 'test-skill'
skillName: 'oms-cocoindex'
skillDir: 'skills/oms-cocoindex/1.0.0/oms-cocoindex'
runId: '20261102T194626Z-f0fcead7'
testMode: 'naive'
forgeTier: 'Deep'
hardGate: 'blocked'
testResult: 'fail'
score: ''
threshold: '80%'
thresholdSource: 'workflow default (80%)'
analysisConfidence: ''
toolingStatus: 'ok'
workspaceDrift: 'ok'
health_check_dispatched: true
testDate: '2026-11-02T19:46:26Z'
stepsCompleted: ['init', 'detect-mode', 'coverage-check', 'coherence-check', 'external-validators', 'hard-gate', 'report']
nextWorkflow: 'update-skill'
---

# Test Report: oms-cocoindex

<!--
Each stage writes its section in place of the heading below that it owns and
the placeholder comment under that heading, so every heading occurs once.
Before the result files are written, report.md §4c checks that each heading
occurs exactly once and that no placeholder comment is left: a stage that
skipped its section stops the run there. Do not reorder or delete the
headings or their placeholder comments.

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

**Mode Rationale:** metadata.json declares `skill_type: "single"` (an individual library skill, cocoindex v1.0.0), so the run uses naive mode: API-surface coverage, with a structural-only coherence check and no coherence category in scoring.

**Analysis Plan:**
- Coverage Check: Deep tier — the documented public API (SKILL.md + references/) against the exports of the cocoindex v1.0.0 source at the pinned commit 5fe4f37 (workspace clone, AST-backed via ast-grep), with signature and type verification and the provenance-map line check.
- Coherence Check: naive (structural) — internal references, section structure and the metadata/provenance coherence of the package; no cross-skill integration validation.

## Coverage Analysis

**Tier:** Deep
**Source Access:** full
**Source Path:** /home/armel/.skf/workspace/repos/github.com/cocoindex-io/cocoindex
**Workspace Layout:** cargo-workspace
**Denominator:** Stratified scope, denominator: scope.include union (95 files matched, 79 exports union)

**Denominator Candidates** (stratified-scope audit trail):
- `stats.effective_denominator`: absent
- `scope.tier_a_include` union: absent
- `scope.include` union: 79    ← chosen (the barrel branch's set)
- exports-map subpath union: absent
- root barrel: 72                               (secondary candidate: root-barrel-vs-subpath-union audit)

**Files Analyzed:** 30

### Export Coverage

| Export | Type | Documented | Signature | Source Location | Status |
|--------|------|------------|-----------|-----------------|--------|
| `App` | - | yes | - | python/cocoindex/_internal/app.py:208 | WARN |
| `AppConfig` | - | yes | - | python/cocoindex/_internal/app.py:202 | WARN |
| `AsyncFunction` | - | yes | - | - | WARN |
| `CanonicalSide` | - | yes | - | - | WARN |
| `ChildTargetDef` | - | yes | - | python/cocoindex/_internal/target_state.py:95 | WARN |
| `Chunk` | - | yes | - | - | WARN |
| `CollectionSchema` | class | yes | - | python/cocoindex/connectors/qdrant/_target.py:108 | PASS |
| `CollectionTarget` | class | yes | - | python/cocoindex/connectors/qdrant/_target.py:453 | PASS |
| `ColumnDef` | class | yes | - | python/cocoindex/connectors/doris/_target.py:330 | PASS |
| `ComponentContext` | - | yes | - | python/cocoindex/_internal/component_ctx.py:55 | WARN |
| `ComponentMountHandle` | class | yes | - | python/cocoindex/_internal/api.py:170 | PASS |
| `ComponentStats` | - | yes | - | python/cocoindex/_internal/update_stats.py:14 | WARN |
| `ComponentSubpath` | - | yes | - | python/cocoindex/_internal/component_ctx.py:142 | WARN |
| `ConnectionFactory` | class | yes | - | python/cocoindex/connectors/surrealdb/_target.py:105 | PASS |
| `ContextKey` | - | yes | - | python/cocoindex/_internal/context_keys.py:99 | WARN |
| `ContextProvider` | - | yes | - | python/cocoindex/_internal/context_keys.py:124 | WARN |
| `CustomLanguageConfig` | - | yes | - | - | WARN |
| `DeletionValueFn` | - | yes | - | python/cocoindex/connectors/kafka/_target.py:206 | PASS |
| `DirTarget` | class | yes | - | python/cocoindex/connectors/localfs/_target.py:282 | PASS |
| `DirWalker` | class | yes | - | python/cocoindex/connectors/localfs/_source.py:68 | PASS |
| `DorisConnectionConfig` | class | yes | - | python/cocoindex/connectors/doris/_target.py:434 | PASS |
| `DorisTableTarget` | class | yes | - | python/cocoindex/connectors/doris/_target.py:1250 | PASS |
| `DorisType` | class | yes | - | python/cocoindex/connectors/doris/_target.py:282 | PASS |
| `DriveFile` | class | yes | - | python/cocoindex/connectors/google_drive/_source.py:83 | PASS |
| `DriveFileInfo` | class | yes | - | python/cocoindex/connectors/google_drive/_source.py:75 | PASS |
| `DropHandle` | - | yes | - | python/cocoindex/_internal/app.py:143 | WARN |
| `Embedder` | - | yes | - | - | WARN |
| `Environment` | - | yes | - | python/cocoindex/_internal/environment.py:183 | WARN |
| `EnvironmentBuilder` | - | yes | - | python/cocoindex/_internal/environment.py:87 | WARN |
| `ExceptionContext` | - | yes | - | python/cocoindex/_internal/component_ctx.py:43 | WARN |
| `ExceptionHandler` | - | yes | - | python/cocoindex/_internal/component_ctx.py:25 | WARN |
| `ExistingCanonicalPolicy` | - | yes | - | - | WARN |
| `File` | class | yes | - | python/cocoindex/connectors/localfs/_source.py:34 | PASS |
| `FileLike` | - | yes | - | - | WARN |
| `FileMetadata` | - | yes | - | - | WARN |
| `FilePath` | class | yes | - | python/cocoindex/connectors/localfs/_common.py:12 | PASS |
| `FilePathMatcher` | - | yes | - | - | WARN |
| `GPU` | - | yes | - | python/cocoindex/_internal/runner.py:282 | WARN |
| `GlobalExecutionOptions` | - | yes | - | - | WARN |
| `GoogleDriveSource` | class | yes | - | python/cocoindex/connectors/google_drive/_source.py:215 | PASS |
| `GoogleDriveSourceSpec` | class | yes | - | python/cocoindex/connectors/google_drive/_source.py:145 | PASS |
| `IdGenerator` | - | yes | - | - | WARN |
| `InvertedIndexDef` | class | yes | - | python/cocoindex/connectors/doris/_target.py:723 | PASS |
| `IsDeleteFn` | - | yes | - | python/cocoindex/connectors/kafka/_source.py:30 | PASS |
| `KafkaTopicTarget` | class | yes | - | python/cocoindex/connectors/kafka/_target.py:209 | PASS |
| `LanceAsyncConnection` | - | yes | - | - | WARN |
| `LanceType` | class | yes | - | python/cocoindex/connectors/lancedb/_target.py:63 | PASS |
| `LifespanFn` | - | yes | - | python/cocoindex/_internal/environment.py:118 | WARN |
| `LiteLLMEmbedder` | - | yes | - | - | WARN |
| `LiveComponent` | - | yes | - | python/cocoindex/_internal/live_component.py:28 | WARN |
| `LiveComponentOperator` | - | yes | - | python/cocoindex/_internal/live_component.py:46 | WARN |
| `LiveMapFeed` | - | yes | - | python/cocoindex/_internal/live_component.py:108 | WARN |
| `LiveMapSubscriber` | - | yes | - | python/cocoindex/_internal/live_component.py:130 | WARN |
| `LiveMapView` | - | yes | - | python/cocoindex/_internal/live_component.py:119 | WARN |
| `LlmPairResolver` | - | yes | - | - | WARN |
| `LogicTracking` | - | yes | - | python/cocoindex/_internal/function.py:65 | WARN |
| `ManagedConnection` | class | yes | - | python/cocoindex/connectors/doris/_target.py:457 | PASS |
| `MatchAllFilePathMatcher` | - | yes | - | - | WARN |
| `MaybePendingS` | - | yes | - | python/cocoindex/_internal/pending_marker.py:115 | WARN |
| `MemoStateOutcome` | - | yes | - | python/cocoindex/_internal/typing.py:67 | WARN |
| `MultiVectorSchema` | - | yes | - | - | WARN |
| `MultiVectorSchemaProvider` | - | yes | - | - | WARN |
| `NON_EXISTENCE` | - | yes | - | python/cocoindex/_internal/typing.py:60 | WARN |
| `NonExistenceType` | - | yes | - | python/cocoindex/_internal/typing.py:47 | WARN |
| `NotMemoKeyable` | - | yes | - | python/cocoindex/_internal/memo_fingerprint.py:136 | WARN |
| `PairDecision` | - | yes | - | - | WARN |
| `PairResolver` | - | yes | - | - | WARN |
| `PatternFilePathMatcher` | - | yes | - | - | WARN |
| `PendingS` | - | yes | - | python/cocoindex/_internal/pending_marker.py:74 | WARN |
| `PendingTargetStateProvider` | - | yes | - | python/cocoindex/_internal/target_state.py:243 | WARN |
| `PgSourceSpec` | class | yes | - | python/cocoindex/connectors/postgres/_source.py:54 | PASS |
| `PgTableSource` | class | yes | - | python/cocoindex/connectors/postgres/_source.py:130 | PASS |
| `PgType` | class | yes | - | python/cocoindex/connectors/postgres/_target.py:77 | PASS |
| `PointStruct` | - | yes | - | python/cocoindex/connectors/qdrant/_target.py:42 | PASS |
| `QdrantVectorDef` | class | yes | - | python/cocoindex/connectors/qdrant/_target.py:50 | PASS |
| `QueryHandlerInfo` | - | yes | - | - | WARN |
| `QueryHandlerResultFields` | - | yes | - | - | WARN |
| `QueryInfo` | - | yes | - | - | WARN |
| `QueryOutput` | - | yes | - | - | WARN |
| `ROOT_PATH` | - | yes | - | python/cocoindex/_internal/stable_path.py:59 | WARN |
| `RecursiveSplitter` | - | yes | - | - | WARN |
| `RelationTarget` | class | yes | - | python/cocoindex/connectors/surrealdb/_target.py:1153 | PASS |
| `ResolutionEvent` | - | yes | - | - | WARN |
| `ResolvedEntities` | - | yes | - | - | WARN |
| `ResolvedS` | - | yes | - | python/cocoindex/_internal/pending_marker.py:89 | WARN |
| `ResolvesTo` | - | yes | - | python/cocoindex/_internal/pending_marker.py:118 | WARN |
| `RetryConfig` | class | yes | - | python/cocoindex/connectors/doris/_target.py:178 | PASS |
| `RowFetcher` | class | yes | - | python/cocoindex/connectors/postgres/_source.py:62 | PASS |
| `Runner` | - | yes | - | python/cocoindex/_internal/runner.py:34 | WARN |
| `S3File` | class | yes | - | python/cocoindex/connectors/amazon_s3/_source.py:89 | PASS |
| `S3FilePath` | class | yes | - | python/cocoindex/connectors/amazon_s3/_source.py:46 | PASS |
| `S3Walker` | class | yes | - | python/cocoindex/connectors/amazon_s3/_source.py:247 | PASS |
| `SentenceTransformerEmbedder` | - | yes | - | - | WARN |
| `SeparatorSplitter` | - | yes | - | - | WARN |
| `ServerSettings` | - | yes | - | - | WARN |
| `Settings` | - | yes | - | python/cocoindex/_internal/setting.py:56 | WARN |
| `SqliteType` | class | yes | - | python/cocoindex/connectors/sqlite/_target.py:154 | PASS |
| `StableKey` | - | yes | - | python/cocoindex/_internal/stable_path.py:9 | WARN |
| `StablePath` | - | yes | - | python/cocoindex/_internal/stable_path.py:16 | WARN |
| `SurrealType` | class | yes | - | python/cocoindex/connectors/surrealdb/_target.py:171 | PASS |
| `Symbol` | - | yes | - | python/cocoindex/_internal/stable_path.py:7 | WARN |
| `SyncFunction` | - | yes | - | - | WARN |
| `TableSchema` | class | yes | - | python/cocoindex/connectors/doris/_target.py:339 | PASS |
| `TableTarget` | class | yes | - | python/cocoindex/connectors/lancedb/_target.py:732 | PASS |
| `TargetActionSink` | - | yes | - | python/cocoindex/_internal/target_state.py:143 | WARN |
| `TargetHandler` | - | yes | - | python/cocoindex/_internal/target_state.py:197 | WARN |
| `TargetReconcileOutput` | - | yes | - | python/cocoindex/_internal/target_state.py:188 | WARN |
| `TargetState` | - | yes | - | python/cocoindex/_internal/target_state.py:248 | WARN |
| `TargetStateProvider` | - | yes | - | python/cocoindex/_internal/target_state.py:208 | WARN |
| `TextPosition` | - | yes | - | - | WARN |
| `UpdateHandle` | - | yes | - | python/cocoindex/_internal/app.py:49 | WARN |
| `UpdateSnapshot` | - | yes | - | python/cocoindex/_internal/update_stats.py:59 | WARN |
| `UpdateStats` | - | yes | - | python/cocoindex/_internal/update_stats.py:39 | WARN |
| `UpdateStatus` | - | yes | - | python/cocoindex/_internal/update_stats.py:9 | WARN |
| `UuidGenerator` | - | yes | - | - | WARN |
| `ValueEncoder` | - | yes | - | python/cocoindex/connectors/doris/_target.py:79 | PASS |
| `Vec0TableDef` | class | yes | - | python/cocoindex/connectors/sqlite/_target.py:121 | PASS |
| `VectorIndexDef` | class | yes | - | python/cocoindex/connectors/doris/_target.py:709 | PASS |
| `VectorSchema` | - | yes | - | - | WARN |
| `VectorSchemaProvider` | - | yes | - | - | WARN |
| `build_vector_search_query` | function | yes | - | python/cocoindex/connectors/doris/_target.py:1317 | PASS |
| `cli` | - | yes | - | - | WARN |
| `collection_target` | function | yes | - | python/cocoindex/connectors/qdrant/_target.py:510 | PASS |
| `component_subpath` | - | yes | yes | python/cocoindex/_internal/component_ctx.py:198 | WARN |
| `connect` | function | yes | - | python/cocoindex/connectors/doris/_target.py:478 | PASS |
| `connect_async` | function | yes | - | python/cocoindex/connectors/doris/_target.py:1292 | PASS |
| `create_client` | function | yes | - | python/cocoindex/connectors/qdrant/_target.py:294 | PASS |
| `create_pool` | function | yes | - | python/cocoindex/connectors/postgres/_target.py:1367 | PASS |
| `declare_collection_target` | function | yes | - | python/cocoindex/connectors/qdrant/_target.py:537 | PASS |
| `declare_dir_target` | function | yes | - | python/cocoindex/connectors/localfs/_target.py:356 | PASS |
| `declare_file` | function | yes | - | python/cocoindex/connectors/localfs/_target.py:451 | PASS |
| `declare_kafka_topic_target` | function | yes | - | python/cocoindex/connectors/kafka/_target.py:277 | PASS |
| `declare_relation_target` | function | yes | - | python/cocoindex/connectors/surrealdb/_target.py:1357 | PASS |
| `declare_table_target` | function | yes | - | python/cocoindex/connectors/doris/_target.py:1206 | PASS |
| `declare_target_state` | - | yes | yes | python/cocoindex/_internal/target_state.py:265 | WARN |
| `declare_target_state_with_child` | - | yes | yes | python/cocoindex/_internal/target_state.py:282 | WARN |
| `default_env` | function | yes | yes | python/cocoindex/_internal/api.py:623 | PASS |
| `detect_code_language` | - | yes | - | - | WARN |
| `dir_target` | function | yes | - | python/cocoindex/connectors/localfs/_target.py:391 | PASS |
| `exception_handler` | - | yes | yes | python/cocoindex/_internal/component_ctx.py:331 | WARN |
| `fn` | - | yes | yes | python/cocoindex/_internal/function.py:1811 | WARN |
| `generate_id` | - | yes | - | - | WARN |
| `generate_uuid` | - | yes | - | - | WARN |
| `get_component_context` | - | yes | yes | python/cocoindex/_internal/component_ctx.py:305 | WARN |
| `get_multi_vector_schema` | - | yes | - | - | WARN |
| `get_object` | function | yes | - | python/cocoindex/connectors/amazon_s3/_source.py:159 | PASS |
| `get_vector_schema` | - | yes | - | - | WARN |
| `is_live_component_class` | - | yes | - | - | WARN |
| `is_non_existence` | - | yes | yes | python/cocoindex/_internal/typing.py:63 | WARN |
| `kafka_topic_target` | function | yes | - | python/cocoindex/connectors/kafka/_target.py:250 | PASS |
| `lifespan` | - | yes | yes | python/cocoindex/_internal/environment.py:449 | WARN |
| `list_files` | function | yes | - | python/cocoindex/connectors/google_drive/_source.py:199 | PASS |
| `list_objects` | function | yes | - | python/cocoindex/connectors/amazon_s3/_source.py:351 | PASS |
| `litellm` | - | yes | - | - | WARN |
| `managed_connection` | function | yes | - | python/cocoindex/connectors/sqlite/_target.py:1282 | PASS |
| `map` | function | yes | yes | python/cocoindex/_internal/api.py:532 | PASS |
| `memo_fingerprint` | - | yes | yes | python/cocoindex/_internal/memo_fingerprint.py:361 | WARN |
| `mount` | function | yes | yes | python/cocoindex/_internal/api.py:333 | PASS |
| `mount_collection_target` | function | yes | yes | python/cocoindex/connectors/qdrant/_target.py:561 | PASS |
| `mount_dir_target` | function | yes | - | python/cocoindex/connectors/localfs/_target.py:424 | PASS |
| `mount_each` | function | yes | yes | python/cocoindex/_internal/api.py:427 | PASS |
| `mount_kafka_topic_target` | function | yes | - | python/cocoindex/connectors/kafka/_target.py:301 | PASS |
| `mount_relation_target` | function | yes | - | python/cocoindex/connectors/surrealdb/_target.py:1382 | PASS |
| `mount_table_target` | function | yes | yes | python/cocoindex/connectors/doris/_target.py:1228 | PASS |
| `mount_target` | function | yes | yes | python/cocoindex/_internal/api.py:566 | PASS |
| `read` | function | yes | - | python/cocoindex/connectors/amazon_s3/_source.py:221 | PASS |
| `register_memo_key_function` | - | yes | yes | python/cocoindex/_internal/memo_fingerprint.py:155 | WARN |
| `register_root_target_states_provider` | - | yes | yes | python/cocoindex/_internal/target_state.py:305 | WARN |
| `relation_target` | function | yes | - | python/cocoindex/connectors/surrealdb/_target.py:1329 | PASS |
| `resolve_entities` | - | yes | - | - | WARN |
| `runtime` | function | yes | yes | python/cocoindex/_internal/api.py:655 | PASS |
| `serialize_by_pickle` | - | yes | yes | python/cocoindex/_internal/serde.py:151 | WARN |
| `show_progress` | - | yes | yes | python/cocoindex/_internal/app.py:194 | WARN |
| `start` | function | yes | yes | python/cocoindex/_internal/api.py:603 | PASS |
| `start_blocking` | function | yes | yes | python/cocoindex/_internal/api.py:613 | PASS |
| `stop` | function | yes | yes | python/cocoindex/_internal/api.py:608 | PASS |
| `stop_blocking` | function | yes | yes | python/cocoindex/_internal/api.py:618 | PASS |
| `table_target` | function | yes | - | python/cocoindex/connectors/doris/_target.py:1187 | PASS |
| `topic_as_map` | function | yes | yes | python/cocoindex/connectors/kafka/_source.py:361 | PASS |
| `unpickle_safe` | - | yes | yes | python/cocoindex/_internal/serde.py:128 | WARN |
| `use_context` | - | yes | yes | python/cocoindex/_internal/component_ctx.py:273 | WARN |
| `use_mount` | function | yes | yes | python/cocoindex/_internal/api.py:194 | PASS |
| `walk_dir` | function | yes | yes | python/cocoindex/connectors/localfs/_source.py:234 | PASS |

### Coverage Summary

- **Exports Found:** 79
- **Documented:** 79 (100%)
- **Missing Documentation:** 0
- **Signature Mismatches:** 0
- **Stale Documentation:** 104, documented extras included
- **Nested Entry Points:** `python/cocoindex/connectors/amazon_s3/__init__.py` inside `python/cocoindex/__init__.py`: `S3File`, `S3FilePath`, `S3Walker`, `get_object`, `list_objects`, `read`; `python/cocoindex/connectors/doris/__init__.py` inside `python/cocoindex/__init__.py`: `ColumnDef`, `DorisConnectionConfig`, `DorisTableTarget`, `DorisType`, `InvertedIndexDef`, `ManagedConnection`, `RetryConfig`, `TableSchema`, `ValueEncoder`, `VectorIndexDef`, `build_vector_search_query`, `connect`, `connect_async`, `declare_table_target`, `mount_table_target`, `table_target`; `python/cocoindex/connectors/google_drive/__init__.py` inside `python/cocoindex/__init__.py`: `DriveFile`, `DriveFileInfo`, `GoogleDriveSource`, `GoogleDriveSourceSpec`, `list_files`; `python/cocoindex/connectors/kafka/__init__.py` inside `python/cocoindex/__init__.py`: `DeletionValueFn`, `IsDeleteFn`, `KafkaTopicTarget`, `declare_kafka_topic_target`, `kafka_topic_target`, `mount_kafka_topic_target`, `topic_as_map`; `python/cocoindex/connectors/lancedb/__init__.py` inside `python/cocoindex/__init__.py`: `LanceAsyncConnection`, `LanceType`, `TableTarget`; `python/cocoindex/connectors/localfs/__init__.py` inside `python/cocoindex/__init__.py`: `DirTarget`, `DirWalker`, `File`, `FilePath`, `declare_dir_target`, `declare_file`, `dir_target`, `mount_dir_target`, `walk_dir`; `python/cocoindex/connectors/postgres/__init__.py` inside `python/cocoindex/__init__.py`: `PgSourceSpec`, `PgTableSource`, `PgType`, `RowFetcher`, `create_pool`; `python/cocoindex/connectors/qdrant/__init__.py` inside `python/cocoindex/__init__.py`: `CollectionSchema`, `CollectionTarget`, `PointStruct`, `QdrantVectorDef`, `collection_target`, `create_client`, `declare_collection_target`, `mount_collection_target`; `python/cocoindex/connectors/sqlite/__init__.py` inside `python/cocoindex/__init__.py`: `SqliteType`, `Vec0TableDef`, `managed_connection`; `python/cocoindex/connectors/surrealdb/__init__.py` inside `python/cocoindex/__init__.py`: `ConnectionFactory`, `RelationTarget`, `SurrealType`, `declare_relation_target`, `mount_relation_target`, `relation_target`
- **Restored by the Stale-Scope Guard:** `App` (python/cocoindex/_internal/app.py:208), `AppConfig` (python/cocoindex/_internal/app.py:202), `ChildTargetDef` (python/cocoindex/_internal/target_state.py:95), `ComponentContext` (python/cocoindex/_internal/component_ctx.py:55), `ComponentStats` (python/cocoindex/_internal/update_stats.py:14), `ComponentSubpath` (python/cocoindex/_internal/component_ctx.py:142), `ContextKey` (python/cocoindex/_internal/context_keys.py:99), `ContextProvider` (python/cocoindex/_internal/context_keys.py:124), `DropHandle` (python/cocoindex/_internal/app.py:143), `Environment` (python/cocoindex/_internal/environment.py:183), `EnvironmentBuilder` (python/cocoindex/_internal/environment.py:87), `ExceptionContext` (python/cocoindex/_internal/component_ctx.py:43), `ExceptionHandler` (python/cocoindex/_internal/component_ctx.py:25), `GPU` (python/cocoindex/_internal/runner.py:282), `LifespanFn` (python/cocoindex/_internal/environment.py:118), `LiveComponent` (python/cocoindex/_internal/live_component.py:28), `LiveComponentOperator` (python/cocoindex/_internal/live_component.py:46), `LiveMapFeed` (python/cocoindex/_internal/live_component.py:108), `LiveMapSubscriber` (python/cocoindex/_internal/live_component.py:130), `LiveMapView` (python/cocoindex/_internal/live_component.py:119), `LogicTracking` (python/cocoindex/_internal/function.py:65), `MaybePendingS` (python/cocoindex/_internal/pending_marker.py:115), `MemoStateOutcome` (python/cocoindex/_internal/typing.py:67), `NON_EXISTENCE` (python/cocoindex/_internal/typing.py:60), `NonExistenceType` (python/cocoindex/_internal/typing.py:47), `NotMemoKeyable` (python/cocoindex/_internal/memo_fingerprint.py:136), `PendingS` (python/cocoindex/_internal/pending_marker.py:74), `PendingTargetStateProvider` (python/cocoindex/_internal/target_state.py:243), `ROOT_PATH` (python/cocoindex/_internal/stable_path.py:59), `ResolvedS` (python/cocoindex/_internal/pending_marker.py:89), `ResolvesTo` (python/cocoindex/_internal/pending_marker.py:118), `Runner` (python/cocoindex/_internal/runner.py:34), `StableKey` (python/cocoindex/_internal/stable_path.py:9), `StablePath` (python/cocoindex/_internal/stable_path.py:16), `Symbol` (python/cocoindex/_internal/stable_path.py:7), `TargetActionSink` (python/cocoindex/_internal/target_state.py:143), `TargetHandler` (python/cocoindex/_internal/target_state.py:197), `TargetReconcileOutput` (python/cocoindex/_internal/target_state.py:188), `TargetState` (python/cocoindex/_internal/target_state.py:248), `TargetStateProvider` (python/cocoindex/_internal/target_state.py:208), `UpdateHandle` (python/cocoindex/_internal/app.py:49), `UpdateSnapshot` (python/cocoindex/_internal/update_stats.py:59), `UpdateStats` (python/cocoindex/_internal/update_stats.py:39), `UpdateStatus` (python/cocoindex/_internal/update_stats.py:9), `component_subpath` (python/cocoindex/_internal/component_ctx.py:198), `declare_target_state` (python/cocoindex/_internal/target_state.py:265), `declare_target_state_with_child` (python/cocoindex/_internal/target_state.py:282), `exception_handler` (python/cocoindex/_internal/component_ctx.py:331), `fn` (python/cocoindex/_internal/function.py:1811), `get_component_context` (python/cocoindex/_internal/component_ctx.py:305), `is_non_existence` (python/cocoindex/_internal/typing.py:63), `memo_fingerprint` (python/cocoindex/_internal/memo_fingerprint.py:361), `register_memo_key_function` (python/cocoindex/_internal/memo_fingerprint.py:155), `register_root_target_states_provider` (python/cocoindex/_internal/target_state.py:305), `serialize_by_pickle` (python/cocoindex/_internal/serde.py:151), `show_progress` (python/cocoindex/_internal/app.py:194), `unpickle_safe` (python/cocoindex/_internal/serde.py:128), `use_context` (python/cocoindex/_internal/component_ctx.py:273)

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 100% |
| Signature Accuracy | 100% |
| Type Coverage | 100% |

**Notes (§1b to §4c):**

- **Inventory (§1):** no subagent tool in this session, so the parent read SKILL.md and all seven `references/*.md` files and built the inventory itself (183 documented names); `validate-inventory.py` passed it, spot-check included.
- **Split-body consistency (§1b):** one SKILL.md/reference contradiction. `DropHandle`: SKILL.md:241 says it is "returned by App.drop()", references/component-api.md:31 declares `async def drop(self) -> None`. The pinned source (`python/cocoindex/_internal/app.py:368`) returns `None` and no Python code constructs a `DropHandle`, so the reference is correct and the SKILL.md line is the wrong side. Recorded as a High `split-body-mismatch` gap (GAP-108), with a remediation that corrects SKILL.md:241 and keeps the reference.
- **Signature comparisons (§2):** 30 documented signatures compared in the main thread, 30 match (the round-1 mismatches `topic_as_map` and `mount_collection_target` are fixed). `mount_table_target` is defined in five connectors; the surface compares it at `connectors/doris/_target.py:1228`, but the skill documents only the postgres form (`PG_DB, table_name, table_schema, pg_schema_name`), which matches `connectors/postgres/_target.py:1332`, so the check counts as a match. `walk_dir` is documented as a call (`sourcedir, recursive=True, path_matcher=...`), which the source `(path, *, live=False, recursive=False, path_matcher=None) -> DirWalker` accepts.
- **Extraction gaps (§2):** no recipe found `DeletionValueFn`, `IsDeleteFn`, `PointStruct`, `ValueEncoder` or `LanceAsyncConnection`. Only `IsDeleteFn` carries a documented shape (`Callable[[Message], bool]`), which matches `connectors/kafka/_source.py:30`.
- **Deep tier (§2):** `gh api repos/cocoindex-io/cocoindex/commits/v1.0.0` resolves to `5fe4f37a526e51516655832ec9814e7ca24ade9a`, equal to `metadata.source_commit`. Re-exports trace to their defining files (the runner counts each name once, where it is defined). Type cross-check against source declarations (notes only: coverage-check names no ledger record for Deep-tier type findings):
  - `UuidGenerator.next_uuid` is a sync `def` (`resources/id.py:190`); references/resources.md:152 still documents it as `async def` (carried over from round 1).
  - The root `coco.Settings` is re-exported from `_internal/setting.py:56` (`_internal/api.py:149`); the skill cites the identical public module `python/cocoindex/setting.py:44`. Both `from_env` bodies read the same variables and neither reads `COCOINDEX_DB` (only `_internal/setting.py:get_default_db_path` does), which references/settings-cli.md:37 states correctly.
  - Minor documented subsets, not errors: `PatternFilePathMatcher.__init__` (`resources/file.py:240`) also accepts its patterns positionally; `FileLike.read` takes `size: int = -1` (`resources/file.py:122`).
  - The qdrant `CollectionSchema.create(vectors=...)` / `QdrantVectorDef(schema, distance, multivector_comparator)` documentation now matches `connectors/qdrant/_target.py:50` and `:150`.
- **Documented extras (§2c):** 104 documented names lie outside the `scope.include` set. classify-stale finds none fabricated; 103 are Info observations (a single source declaration, or one cited declaring file). `Chunk` is declared in both `_internal/core.pyi:333` and `resources/chunk.py:26`, and no citation on a line naming it picks one, so it stays a Medium `stale-documentation` gap at SKILL.md:25. Round 1's `LLMResolver` stale gap is gone (the skill now documents `LlmPairResolver`).
- **Denominator clause:** the source root holds a cargo workspace (the Rust engine under `rust/`, which the brief excludes), so the run is monorepo and the stratified-scope clause takes the `scope.include` set (79). The 58 root exports defined under `python/cocoindex/_internal/` outside `api.py` fall outside that set; the skill documents every one of them, so the score is unaffected.
- **Guards (§4):** `guards.staleScope` fires: the brief's `scope.include` globs `docs/docs/**/*.md` and `docs/docs/**/*.mdx` match no file at v1.0.0. Recorded as a Medium `brief-scope-stale` gap (edit the brief by hand). `guards.inflation` does not fire (79 vs 155 provenance entries). `guards.deflation` does not apply (no `stats.effective_denominator`).
- **Metadata coherence (§4b):** Medium drift: `stats.exports_public_api` = 140 vs `exports[]` length = 119 (15%).
- **Numerator ground truth (§2b):** skipped (no `stats.effective_denominator`, so no inflation signature).
- **Provenance line check (§4c):** 155 map entries checked, 1 records a line that is not the definition: `ServerSettings.parse_cors_origins` at `python/cocoindex/setting.py:123` (definition lines 117, 121, 124), a Low `provenance-line` gap.

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)

### Structural Findings

| # | Type | Severity | Detail | Line |
|---|------|----------|--------|------|
| - | - | - | No structural finding | - |

**Structural Issues:** 0

Checks run (§2.0 to §2.7):
- §2.1 Required sections: `usage` is served by `## Quick Start` (line 12) and `api_surface` by `## Key API Summary` (line 163). `description` has no heading, but the non-empty frontmatter `description` serves it. No finding.
- §2.2 Code fences: balanced (8 fences). §2.3 No opening fence lacks a language tag. §2.6 No table row drifts from its header. §2.7 No `scripts/` or `assets/` folder.
- §2.4 Usage scope (split body: Quick Start, Common Workflows, Key API Summary, plus the seven reference files): every function export of the inventory is referenced; `zero_usage[]` is empty.
- §2.5 Async/sync: 28 function exports are called in examples (34 appear in none). Every awaited call matches an async declaration, and `generate_uuid` (round 1's finding) is now called without `await` (SKILL.md:144). Some calls the locator marks awaited carry the `await` of another call, so they raise no finding: `component_subpath` passed as an argument inside `await coco.mount(...)` / `await operator.update(...)` (references/component-api.md:284, :289, references/live-components.md:102, :110), `use_context` before `.embed(...)` (SKILL.md:57, `chainedMember: embed`), `asyncpg.create_pool` (not the postgres connector's `create_pool`), and `async with coco.runtime()` (the documented async form of the dual-mode context manager).
- §2b Migration/deprecation (Deep tier, evidence report present): `t2_future_count: 0`, and SKILL.md has no "Migration & Deprecation Warnings" section, so no case applies. `## Migration from v0.3.37` (line 294) is historical v0.3.37 to v1.0.0 cutover content, outside the Section 4b contract.

### Reference Consistency (split-body)

| # | Reference File | Export | Issue | SKILL.md Line | Reference Line |
|---|---------------|--------|-------|---------------|---------------|
| 1 | references/component-api.md | `DropHandle` | SKILL.md says `DropHandle` is "returned by App.drop()"; the reference declares `async def drop(self) -> None`. The pinned source (`python/cocoindex/_internal/app.py:368`) agrees with the reference. Recorded by coverage-check §1b as GAP-108. | 241 | 31 |

**Exports Cross-Checked:** 97
**Mismatches Found:** 1

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

**Result:** **FAIL**, not scored: the hard gate blocked this run on 1 Critical or High gap(s), listed first in the Gap Report.

## Gap Report

**Total Gaps:** 108
**Blocking (Critical + High):** 1
**Non-blocking (Medium + Low + Info):** 107

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|------------------|
| Critical | 0 | None |
| High | 1 | Read the source code and write or correct the documentation |
| Medium | 3 | Add type definitions, interface docs or the missing section |
| Low | 1 | Add examples or metadata |
| Info | 103 | Optional improvements, no action required |
| **Total** | **108** | |

### GAP-108: Split-body mismatch: DropHandle

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** references/component-api.md:31
**Export:** DropHandle

**Issue:** SKILL.md:241 (Key Types) says `DropHandle` is "returned by App.drop()", while references/component-api.md:31 declares `async def drop(self) -> None` on `App`, so the two files disagree on what `App.drop()` returns. The pinned source `python/cocoindex/_internal/app.py:368` is `async def drop(self) -> None` (it awaits an internal core drop handle and returns nothing), so the reference is correct and the SKILL.md line is the wrong side.

**Remediation:** In SKILL.md line 241, replace the comment `# returned by App.drop()` with one that matches the source, e.g. `DropHandle  # drop-operation handle (stats(), watch(), awaitable result()); App.drop() itself returns None`, since `App.drop` is `async def drop(self) -> None` at `python/cocoindex/_internal/app.py:368`. Keep references/component-api.md line 31 (`async def drop(self) -> None: ...`) unchanged: it already matches the source.

### GAP-006: Stale documentation: Chunk

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:25
**Export:** Chunk

**Issue:** SKILL.md documents `Chunk`, which the enumerated source API surface lacks

**Remediation:** Check `Chunk` against the source and update or remove its documentation at SKILL.md:25: the enumerated source surface does not export it.

### GAP-105: stale brief scope: scope.include globs match no source file

**Severity:** Medium
**Category:** Coverage (brief-scope-stale)
**Source:** forge-data/oms-cocoindex/skill-brief.yaml

**Issue:** the `scope.include` globs `docs/docs/**/*.md`, `docs/docs/**/*.mdx` match no file in the source tested; the `all` set restores 58 root exports, defined in files no include glob covers: `App` in `python/cocoindex/_internal/app.py`, `AppConfig` in `python/cocoindex/_internal/app.py`, `ChildTargetDef` in `python/cocoindex/_internal/target_state.py`, `ComponentContext` in `python/cocoindex/_internal/component_ctx.py`, `ComponentStats` in `python/cocoindex/_internal/update_stats.py`, `ComponentSubpath` in `python/cocoindex/_internal/component_ctx.py`, `ContextKey` in `python/cocoindex/_internal/context_keys.py`, `ContextProvider` in `python/cocoindex/_internal/context_keys.py`, `DropHandle` in `python/cocoindex/_internal/app.py`, `Environment` in `python/cocoindex/_internal/environment.py`, `EnvironmentBuilder` in `python/cocoindex/_internal/environment.py`, `ExceptionContext` in `python/cocoindex/_internal/component_ctx.py`, `ExceptionHandler` in `python/cocoindex/_internal/component_ctx.py`, `GPU` in `python/cocoindex/_internal/runner.py`, `LifespanFn` in `python/cocoindex/_internal/environment.py`, `LiveComponent` in `python/cocoindex/_internal/live_component.py`, `LiveComponentOperator` in `python/cocoindex/_internal/live_component.py`, `LiveMapFeed` in `python/cocoindex/_internal/live_component.py`, `LiveMapSubscriber` in `python/cocoindex/_internal/live_component.py`, `LiveMapView` in `python/cocoindex/_internal/live_component.py`, `LogicTracking` in `python/cocoindex/_internal/function.py`, `MaybePendingS` in `python/cocoindex/_internal/pending_marker.py`, `MemoStateOutcome` in `python/cocoindex/_internal/typing.py`, `NON_EXISTENCE` in `python/cocoindex/_internal/typing.py`, `NonExistenceType` in `python/cocoindex/_internal/typing.py`, `NotMemoKeyable` in `python/cocoindex/_internal/memo_fingerprint.py`, `PendingS` in `python/cocoindex/_internal/pending_marker.py`, `PendingTargetStateProvider` in `python/cocoindex/_internal/target_state.py`, `ROOT_PATH` in `python/cocoindex/_internal/stable_path.py`, `ResolvedS` in `python/cocoindex/_internal/pending_marker.py`, `ResolvesTo` in `python/cocoindex/_internal/pending_marker.py`, `Runner` in `python/cocoindex/_internal/runner.py`, `StableKey` in `python/cocoindex/_internal/stable_path.py`, `StablePath` in `python/cocoindex/_internal/stable_path.py`, `Symbol` in `python/cocoindex/_internal/stable_path.py`, `TargetActionSink` in `python/cocoindex/_internal/target_state.py`, `TargetHandler` in `python/cocoindex/_internal/target_state.py`, `TargetReconcileOutput` in `python/cocoindex/_internal/target_state.py`, `TargetState` in `python/cocoindex/_internal/target_state.py`, `TargetStateProvider` in `python/cocoindex/_internal/target_state.py`, `UpdateHandle` in `python/cocoindex/_internal/app.py`, `UpdateSnapshot` in `python/cocoindex/_internal/update_stats.py`, `UpdateStats` in `python/cocoindex/_internal/update_stats.py`, `UpdateStatus` in `python/cocoindex/_internal/update_stats.py`, `component_subpath` in `python/cocoindex/_internal/component_ctx.py`, `declare_target_state` in `python/cocoindex/_internal/target_state.py`, `declare_target_state_with_child` in `python/cocoindex/_internal/target_state.py`, `exception_handler` in `python/cocoindex/_internal/component_ctx.py`, `fn` in `python/cocoindex/_internal/function.py`, `get_component_context` in `python/cocoindex/_internal/component_ctx.py`, `is_non_existence` in `python/cocoindex/_internal/typing.py`, `memo_fingerprint` in `python/cocoindex/_internal/memo_fingerprint.py`, `register_memo_key_function` in `python/cocoindex/_internal/memo_fingerprint.py`, `register_root_target_states_provider` in `python/cocoindex/_internal/target_state.py`, `serialize_by_pickle` in `python/cocoindex/_internal/serde.py`, `show_progress` in `python/cocoindex/_internal/app.py`, `unpickle_safe` in `python/cocoindex/_internal/serde.py`, `use_context` in `python/cocoindex/_internal/component_ctx.py`

**Remediation:** Edit `scope.include` in `forge-data/oms-cocoindex/skill-brief.yaml` by hand so each glob matches the files it meant in this version of the source (update-skill does not rewrite an include glob), and add to `scope.exclude` any restored file the brief meant to leave out.

### GAP-106: metadata drift — barrel export counts diverge

**Severity:** Medium
**Category:** Coverage (metadata-drift)
**Source:** skills/oms-cocoindex/1.0.0/oms-cocoindex/metadata.json

**Issue:** stats.exports_public_api=140, exports[].length=119 → 15% drift

**Remediation:** Recount the exports and correct the diverging counts in `skills/oms-cocoindex/1.0.0/oms-cocoindex/metadata.json`; update-skill applies it as a metadata update.

### GAP-107: Provenance line is not the definition of ServerSettings.parse_cors_origins

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** python/cocoindex/setting.py:123
**Export:** ServerSettings.parse_cors_origins

**Issue:** the provenance map records `ServerSettings.parse_cors_origins` at `python/cocoindex/setting.py:123`, which is not the line that defines it; the lines that define it are 117, 121, 124.

**Remediation:** Set the provenance `source_line` of `ServerSettings.parse_cors_origins` in `python/cocoindex/setting.py` to its definition line (117, 121, 124) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-001: Documented extra: App

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/app.py:208
**Export:** App

**Issue:** `SKILL.md:3` documents `App`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `App` is a documented extra, a name the source still declares at `python/cocoindex/_internal/app.py:208` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-002: Documented extra: AppConfig

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/app.py:202
**Export:** AppConfig

**Issue:** `SKILL.md:79` documents `AppConfig`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `AppConfig` is a documented extra, a name the source still declares at `python/cocoindex/_internal/app.py:202` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-003: Documented extra: AsyncFunction

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/function.py:903
**Export:** AsyncFunction

**Issue:** `SKILL.md:268` documents `AsyncFunction`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `AsyncFunction` is a documented extra, a name the source still declares at `python/cocoindex/_internal/function.py:903` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-004: Documented extra: CanonicalSide

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:35
**Export:** CanonicalSide

**Issue:** `references/ops.md:177` documents `CanonicalSide`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CanonicalSide` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:35` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-005: Documented extra: ChildTargetDef

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/target_state.py:95
**Export:** ChildTargetDef

**Issue:** `references/target-state.md:47` documents `ChildTargetDef`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ChildTargetDef` is a documented extra, a name the source still declares at `python/cocoindex/_internal/target_state.py:95` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-007: Documented extra: ComponentContext

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/component_ctx.py:55
**Export:** ComponentContext

**Issue:** `SKILL.md:152` documents `ComponentContext`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ComponentContext` is a documented extra, a name the source still declares at `python/cocoindex/_internal/component_ctx.py:55` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-008: Documented extra: ComponentStats

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/update_stats.py:14
**Export:** ComponentStats

**Issue:** `SKILL.md:237` documents `ComponentStats`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ComponentStats` is a documented extra, a name the source still declares at `python/cocoindex/_internal/update_stats.py:14` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-009: Documented extra: ComponentSubpath

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/component_ctx.py:142
**Export:** ComponentSubpath

**Issue:** `SKILL.md:197` documents `ComponentSubpath`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ComponentSubpath` is a documented extra, a name the source still declares at `python/cocoindex/_internal/component_ctx.py:142` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-010: Documented extra: ContextKey

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/context_keys.py:99
**Export:** ContextKey

**Issue:** `SKILL.md:31` documents `ContextKey`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ContextKey` is a documented extra, a name the source still declares at `python/cocoindex/_internal/context_keys.py:99` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-011: Documented extra: ContextProvider

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/context_keys.py:124
**Export:** ContextProvider

**Issue:** `SKILL.md:203` documents `ContextProvider`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ContextProvider` is a documented extra, a name the source still declares at `python/cocoindex/_internal/context_keys.py:124` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-012: Documented extra: CustomLanguageConfig

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/text.py:87
**Export:** CustomLanguageConfig

**Issue:** `SKILL.md:115` documents `CustomLanguageConfig`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `python/cocoindex/ops/text.py`

**Remediation:** No change: `CustomLanguageConfig` is a documented extra, a name the source still declares at `python/cocoindex/ops/text.py:87` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-013: Documented extra: DropHandle

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/app.py:143
**Export:** DropHandle

**Issue:** `SKILL.md:241` documents `DropHandle`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `DropHandle` is a documented extra, a name the source still declares at `python/cocoindex/_internal/app.py:143` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-014: Documented extra: Embedder

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/embedder.py:15
**Export:** Embedder

**Issue:** `SKILL.md:161` documents `Embedder`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Embedder` is a documented extra, a name the source still declares at `python/cocoindex/resources/embedder.py:15` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-015: Documented extra: Environment

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/environment.py:183
**Export:** Environment

**Issue:** `SKILL.md:3` documents `Environment`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Environment` is a documented extra, a name the source still declares at `python/cocoindex/_internal/environment.py:183` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-016: Documented extra: EnvironmentBuilder

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/environment.py:87
**Export:** EnvironmentBuilder

**Issue:** `SKILL.md:35` documents `EnvironmentBuilder`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `EnvironmentBuilder` is a documented extra, a name the source still declares at `python/cocoindex/_internal/environment.py:87` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-017: Documented extra: ExceptionContext

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/component_ctx.py:43
**Export:** ExceptionContext

**Issue:** `references/component-api.md:316` documents `ExceptionContext`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ExceptionContext` is a documented extra, a name the source still declares at `python/cocoindex/_internal/component_ctx.py:43` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-018: Documented extra: ExceptionHandler

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/component_ctx.py:25
**Export:** ExceptionHandler

**Issue:** `references/component-api.md:61` documents `ExceptionHandler`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ExceptionHandler` is a documented extra, a name the source still declares at `python/cocoindex/_internal/component_ctx.py:25` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-019: Documented extra: ExistingCanonicalPolicy

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:57
**Export:** ExistingCanonicalPolicy

**Issue:** `references/ops.md:179` documents `ExistingCanonicalPolicy`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ExistingCanonicalPolicy` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:57` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-020: Documented extra: FileLike

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/file.py:56
**Export:** FileLike

**Issue:** `SKILL.md:26` documents `FileLike`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `FileLike` is a documented extra, a name the source still declares at `python/cocoindex/resources/file.py:56` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-021: Documented extra: FileMetadata

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/file.py:40
**Export:** FileMetadata

**Issue:** `SKILL.md:338` documents `FileMetadata`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `FileMetadata` is a documented extra, a name the source still declares at `python/cocoindex/resources/file.py:40` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-022: Documented extra: FilePathMatcher

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/file.py:205
**Export:** FilePathMatcher

**Issue:** `references/resources.md:35` documents `FilePathMatcher`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `FilePathMatcher` is a documented extra, a name the source still declares at `python/cocoindex/resources/file.py:205` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-023: Documented extra: GPU

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/runner.py:282
**Export:** GPU

**Issue:** `SKILL.md:8` documents `GPU`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `GPU` is a documented extra, a name the source still declares at `python/cocoindex/_internal/runner.py:282` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-024: Documented extra: GlobalExecutionOptions

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/setting.py:12
**Export:** GlobalExecutionOptions

**Issue:** `SKILL.md:206` documents `GlobalExecutionOptions`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `GlobalExecutionOptions` is a documented extra, a name the source still declares at `python/cocoindex/setting.py:12` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-025: Documented extra: IdGenerator

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/id.py:89
**Export:** IdGenerator

**Issue:** `SKILL.md:27` documents `IdGenerator`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `IdGenerator` is a documented extra, a name the source still declares at `python/cocoindex/resources/id.py:89` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-026: Documented extra: LanceAsyncConnection

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/lancedb/_target.py:33
**Export:** LanceAsyncConnection

**Issue:** `references/connectors.md:86` documents `LanceAsyncConnection`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LanceAsyncConnection` is a documented extra, a name the source still declares at `python/cocoindex/connectors/lancedb/_target.py:33` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-027: Documented extra: LifespanFn

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/environment.py:118
**Export:** LifespanFn

**Issue:** `SKILL.md:171` documents `LifespanFn`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LifespanFn` is a documented extra, a name the source still declares at `python/cocoindex/_internal/environment.py:118` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-028: Documented extra: LiteLLMEmbedder

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/litellm.py:22
**Export:** LiteLLMEmbedder

**Issue:** `SKILL.md:109` documents `LiteLLMEmbedder`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LiteLLMEmbedder` is a documented extra, a name the source still declares at `python/cocoindex/ops/litellm.py:22` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-029: Documented extra: LiveComponent

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/live_component.py:28
**Export:** LiveComponent

**Issue:** `SKILL.md:160` documents `LiveComponent`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LiveComponent` is a documented extra, a name the source still declares at `python/cocoindex/_internal/live_component.py:28` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-030: Documented extra: LiveComponentOperator

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/live_component.py:46
**Export:** LiveComponentOperator

**Issue:** `SKILL.md:193` documents `LiveComponentOperator`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LiveComponentOperator` is a documented extra, a name the source still declares at `python/cocoindex/_internal/live_component.py:46` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-031: Documented extra: LiveMapFeed

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/live_component.py:108
**Export:** LiveMapFeed

**Issue:** `SKILL.md:98` documents `LiveMapFeed`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LiveMapFeed` is a documented extra, a name the source still declares at `python/cocoindex/_internal/live_component.py:108` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-032: Documented extra: LiveMapSubscriber

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/live_component.py:130
**Export:** LiveMapSubscriber

**Issue:** `SKILL.md:195` documents `LiveMapSubscriber`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LiveMapSubscriber` is a documented extra, a name the source still declares at `python/cocoindex/_internal/live_component.py:130` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-033: Documented extra: LiveMapView

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/live_component.py:119
**Export:** LiveMapView

**Issue:** `SKILL.md:98` documents `LiveMapView`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LiveMapView` is a documented extra, a name the source still declares at `python/cocoindex/_internal/live_component.py:119` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-034: Documented extra: LlmPairResolver

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/llm_resolver.py:49
**Export:** LlmPairResolver

**Issue:** `references/ops.md:188` documents `LlmPairResolver`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LlmPairResolver` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/llm_resolver.py:49` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-035: Documented extra: LogicTracking

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/function.py:65
**Export:** LogicTracking

**Issue:** `SKILL.md:174` documents `LogicTracking`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LogicTracking` is a documented extra, a name the source still declares at `python/cocoindex/_internal/function.py:65` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-036: Documented extra: MatchAllFilePathMatcher

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/file.py:215
**Export:** MatchAllFilePathMatcher

**Issue:** `references/resources.md:36` documents `MatchAllFilePathMatcher`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MatchAllFilePathMatcher` is a documented extra, a name the source still declares at `python/cocoindex/resources/file.py:215` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-037: Documented extra: MaybePendingS

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/pending_marker.py:115
**Export:** MaybePendingS

**Issue:** `SKILL.md:185` documents `MaybePendingS`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MaybePendingS` is a documented extra, a name the source still declares at `python/cocoindex/_internal/pending_marker.py:115` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-038: Documented extra: MemoStateOutcome

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/typing.py:67
**Export:** MemoStateOutcome

**Issue:** `SKILL.md:253` documents `MemoStateOutcome`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MemoStateOutcome` is a documented extra, a name the source still declares at `python/cocoindex/_internal/typing.py:67` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-039: Documented extra: MultiVectorSchema

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:49
**Export:** MultiVectorSchema

**Issue:** `references/resources.md:173` documents `MultiVectorSchema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MultiVectorSchema` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:49` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-040: Documented extra: MultiVectorSchemaProvider

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:43
**Export:** MultiVectorSchemaProvider

**Issue:** `references/resources.md:173` documents `MultiVectorSchemaProvider`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MultiVectorSchemaProvider` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:43` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-041: Documented extra: NON_EXISTENCE

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/typing.py:60
**Export:** NON_EXISTENCE

**Issue:** `SKILL.md:157` documents `NON_EXISTENCE`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `NON_EXISTENCE` is a documented extra, a name the source still declares at `python/cocoindex/_internal/typing.py:60` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-042: Documented extra: NonExistenceType

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/typing.py:47
**Export:** NonExistenceType

**Issue:** `SKILL.md:250` documents `NonExistenceType`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `NonExistenceType` is a documented extra, a name the source still declares at `python/cocoindex/_internal/typing.py:47` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-043: Documented extra: NotMemoKeyable

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/memo_fingerprint.py:136
**Export:** NotMemoKeyable

**Issue:** `SKILL.md:256` documents `NotMemoKeyable`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `NotMemoKeyable` is a documented extra, a name the source still declares at `python/cocoindex/_internal/memo_fingerprint.py:136` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-044: Documented extra: PairDecision

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:46
**Export:** PairDecision

**Issue:** `references/ops.md:178` documents `PairDecision`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PairDecision` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:46` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-045: Documented extra: PairResolver

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:97
**Export:** PairResolver

**Issue:** `references/ops.md:181` documents `PairResolver`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PairResolver` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:97` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-046: Documented extra: PatternFilePathMatcher

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/file.py:227
**Export:** PatternFilePathMatcher

**Issue:** `SKILL.md:26` documents `PatternFilePathMatcher`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PatternFilePathMatcher` is a documented extra, a name the source still declares at `python/cocoindex/resources/file.py:227` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-047: Documented extra: PendingS

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/pending_marker.py:74
**Export:** PendingS

**Issue:** `SKILL.md:244` documents `PendingS`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PendingS` is a documented extra, a name the source still declares at `python/cocoindex/_internal/pending_marker.py:74` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-048: Documented extra: PendingTargetStateProvider

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/target_state.py:243
**Export:** PendingTargetStateProvider

**Issue:** `SKILL.md:190` documents `PendingTargetStateProvider`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PendingTargetStateProvider` is a documented extra, a name the source still declares at `python/cocoindex/_internal/target_state.py:243` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-049: Documented extra: QueryHandlerInfo

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/query_handler.py:21
**Export:** QueryHandlerInfo

**Issue:** `SKILL.md:207` documents `QueryHandlerInfo`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `QueryHandlerInfo` is a documented extra, a name the source still declares at `python/cocoindex/query_handler.py:21` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-050: Documented extra: QueryHandlerResultFields

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/query_handler.py:10
**Export:** QueryHandlerResultFields

**Issue:** `SKILL.md:207` documents `QueryHandlerResultFields`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `QueryHandlerResultFields` is a documented extra, a name the source still declares at `python/cocoindex/query_handler.py:10` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-051: Documented extra: QueryInfo

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/query_handler.py:30
**Export:** QueryInfo

**Issue:** `SKILL.md:209` documents `QueryInfo`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `QueryInfo` is a documented extra, a name the source still declares at `python/cocoindex/query_handler.py:30` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-052: Documented extra: QueryOutput

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/query_handler.py:43
**Export:** QueryOutput

**Issue:** `SKILL.md:210` documents `QueryOutput`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `QueryOutput` is a documented extra, a name the source still declares at `python/cocoindex/query_handler.py:43` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-053: Documented extra: ROOT_PATH

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/stable_path.py:59
**Export:** ROOT_PATH

**Issue:** `SKILL.md:232` documents `ROOT_PATH`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ROOT_PATH` is a documented extra, a name the source still declares at `python/cocoindex/_internal/stable_path.py:59` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-054: Documented extra: RecursiveSplitter

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/text.py:120
**Export:** RecursiveSplitter

**Issue:** `SKILL.md:23` documents `RecursiveSplitter`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `python/cocoindex/ops/text.py`

**Remediation:** No change: `RecursiveSplitter` is a documented extra, a name the source still declares at `python/cocoindex/ops/text.py:120` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-055: Documented extra: ResolutionEvent

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:70
**Export:** ResolutionEvent

**Issue:** `references/ops.md:180` documents `ResolutionEvent`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ResolutionEvent` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:70` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-056: Documented extra: ResolvedEntities

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:114
**Export:** ResolvedEntities

**Issue:** `references/ops.md:182` documents `ResolvedEntities`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ResolvedEntities` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:114` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-057: Documented extra: ResolvedS

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/pending_marker.py:89
**Export:** ResolvedS

**Issue:** `SKILL.md:245` documents `ResolvedS`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ResolvedS` is a documented extra, a name the source still declares at `python/cocoindex/_internal/pending_marker.py:89` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-058: Documented extra: ResolvesTo

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/pending_marker.py:118
**Export:** ResolvesTo

**Issue:** `SKILL.md:247` documents `ResolvesTo`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ResolvesTo` is a documented extra, a name the source still declares at `python/cocoindex/_internal/pending_marker.py:118` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-059: Documented extra: Runner

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/runner.py:34
**Export:** Runner

**Issue:** `SKILL.md:183` documents `Runner`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Runner` is a documented extra, a name the source still declares at `python/cocoindex/_internal/runner.py:34` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-060: Documented extra: SentenceTransformerEmbedder

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/sentence_transformers.py:25
**Export:** SentenceTransformerEmbedder

**Issue:** `SKILL.md:24` documents `SentenceTransformerEmbedder`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `SentenceTransformerEmbedder` is a documented extra, a name the source still declares at `python/cocoindex/ops/sentence_transformers.py:25` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-061: Documented extra: SeparatorSplitter

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/text.py:39
**Export:** SeparatorSplitter

**Issue:** `SKILL.md:115` documents `SeparatorSplitter`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `python/cocoindex/ops/text.py`

**Remediation:** No change: `SeparatorSplitter` is a documented extra, a name the source still declares at `python/cocoindex/ops/text.py:39` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-062: Documented extra: ServerSettings

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/setting.py:93
**Export:** ServerSettings

**Issue:** `SKILL.md:205` documents `ServerSettings`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ServerSettings` is a documented extra, a name the source still declares at `python/cocoindex/setting.py:93` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-063: Documented extra: Settings

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/setting.py:44
**Export:** Settings

**Issue:** `SKILL.md:8` documents `Settings`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Settings` is a documented extra, a name the source still declares at `python/cocoindex/setting.py:44` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-064: Documented extra: StableKey

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/stable_path.py:9
**Export:** StableKey

**Issue:** `SKILL.md:230` documents `StableKey`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `StableKey` is a documented extra, a name the source still declares at `python/cocoindex/_internal/stable_path.py:9` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-065: Documented extra: StablePath

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/stable_path.py:16
**Export:** StablePath

**Issue:** `SKILL.md:231` documents `StablePath`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `StablePath` is a documented extra, a name the source still declares at `python/cocoindex/_internal/stable_path.py:16` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-066: Documented extra: Symbol

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/stable_path.py:7
**Export:** Symbol

**Issue:** `SKILL.md:230` documents `Symbol`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Symbol` is a documented extra, a name the source still declares at `python/cocoindex/_internal/stable_path.py:7` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-067: Documented extra: SyncFunction

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/function.py:491
**Export:** SyncFunction

**Issue:** `SKILL.md:268` documents `SyncFunction`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `SyncFunction` is a documented extra, a name the source still declares at `python/cocoindex/_internal/function.py:491` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-068: Documented extra: TargetActionSink

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/target_state.py:143
**Export:** TargetActionSink

**Issue:** `SKILL.md:187` documents `TargetActionSink`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `TargetActionSink` is a documented extra, a name the source still declares at `python/cocoindex/_internal/target_state.py:143` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-069: Documented extra: TargetHandler

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/target_state.py:197
**Export:** TargetHandler

**Issue:** `SKILL.md:8` documents `TargetHandler`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `TargetHandler` is a documented extra, a name the source still declares at `python/cocoindex/_internal/target_state.py:197` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-070: Documented extra: TargetReconcileOutput

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/target_state.py:188
**Export:** TargetReconcileOutput

**Issue:** `SKILL.md:186` documents `TargetReconcileOutput`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `TargetReconcileOutput` is a documented extra, a name the source still declares at `python/cocoindex/_internal/target_state.py:188` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-071: Documented extra: TargetState

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/target_state.py:248
**Export:** TargetState

**Issue:** `SKILL.md:3` documents `TargetState`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `TargetState` is a documented extra, a name the source still declares at `python/cocoindex/_internal/target_state.py:248` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-072: Documented extra: TargetStateProvider

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/target_state.py:208
**Export:** TargetStateProvider

**Issue:** `SKILL.md:156` documents `TargetStateProvider`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `TargetStateProvider` is a documented extra, a name the source still declares at `python/cocoindex/_internal/target_state.py:208` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-073: Documented extra: TextPosition

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/chunk.py:9
**Export:** TextPosition

**Issue:** `SKILL.md:338` documents `TextPosition`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `TextPosition` is a documented extra, a name the source still declares at `python/cocoindex/resources/chunk.py:9` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-074: Documented extra: UpdateHandle

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/app.py:49
**Export:** UpdateHandle

**Issue:** `SKILL.md:91` documents `UpdateHandle`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `UpdateHandle` is a documented extra, a name the source still declares at `python/cocoindex/_internal/app.py:49` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-075: Documented extra: UpdateSnapshot

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/update_stats.py:59
**Export:** UpdateSnapshot

**Issue:** `SKILL.md:239` documents `UpdateSnapshot`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `UpdateSnapshot` is a documented extra, a name the source still declares at `python/cocoindex/_internal/update_stats.py:59` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-076: Documented extra: UpdateStats

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/update_stats.py:39
**Export:** UpdateStats

**Issue:** `SKILL.md:238` documents `UpdateStats`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `UpdateStats` is a documented extra, a name the source still declares at `python/cocoindex/_internal/update_stats.py:39` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-077: Documented extra: UpdateStatus

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/update_stats.py:9
**Export:** UpdateStatus

**Issue:** `SKILL.md:236` documents `UpdateStatus`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `UpdateStatus` is a documented extra, a name the source still declares at `python/cocoindex/_internal/update_stats.py:9` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-078: Documented extra: UuidGenerator

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/id.py:152
**Export:** UuidGenerator

**Issue:** `SKILL.md:338` documents `UuidGenerator`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `UuidGenerator` is a documented extra, a name the source still declares at `python/cocoindex/resources/id.py:152` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-079: Documented extra: VectorSchema

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:23
**Export:** VectorSchema

**Issue:** `SKILL.md:338` documents `VectorSchema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `VectorSchema` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:23` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-080: Documented extra: VectorSchemaProvider

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:17
**Export:** VectorSchemaProvider

**Issue:** `SKILL.md:338` documents `VectorSchemaProvider`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `VectorSchemaProvider` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:17` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-081: Documented extra: cli

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/cli.py:505
**Export:** cli

**Issue:** `SKILL.md:211` documents `cli`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `cli` is a documented extra, a name the source still declares at `python/cocoindex/cli.py:505` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-082: Documented extra: component_subpath

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/component_ctx.py:198
**Export:** component_subpath

**Issue:** `SKILL.md:152` documents `component_subpath`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `component_subpath` is a documented extra, a name the source still declares at `python/cocoindex/_internal/component_ctx.py:198` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-083: Documented extra: declare_target_state

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/target_state.py:265
**Export:** declare_target_state

**Issue:** `SKILL.md:189` documents `declare_target_state`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `declare_target_state` is a documented extra, a name the source still declares at `python/cocoindex/_internal/target_state.py:265` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-084: Documented extra: declare_target_state_with_child

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/target_state.py:282
**Export:** declare_target_state_with_child

**Issue:** `SKILL.md:103` documents `declare_target_state_with_child`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `declare_target_state_with_child` is a documented extra, a name the source still declares at `python/cocoindex/_internal/target_state.py:282` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-085: Documented extra: detect_code_language

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/text.py:19
**Export:** detect_code_language

**Issue:** `SKILL.md:115` documents `detect_code_language`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `python/cocoindex/ops/text.py`

**Remediation:** No change: `detect_code_language` is a documented extra, a name the source still declares at `python/cocoindex/ops/text.py:19` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-086: Documented extra: exception_handler

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/component_ctx.py:331
**Export:** exception_handler

**Issue:** `SKILL.md:152` documents `exception_handler`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `exception_handler` is a documented extra, a name the source still declares at `python/cocoindex/_internal/component_ctx.py:331` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-087: Documented extra: fn

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/function.py:1811
**Export:** fn

**Issue:** `SKILL.md:3` documents `fn`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `fn` is a documented extra, a name the source still declares at `python/cocoindex/_internal/function.py:1811` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-088: Documented extra: generate_id

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/id.py:31
**Export:** generate_id

**Issue:** `SKILL.md:143` documents `generate_id`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `generate_id` is a documented extra, a name the source still declares at `python/cocoindex/resources/id.py:31` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-089: Documented extra: generate_uuid

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/id.py:61
**Export:** generate_uuid

**Issue:** `SKILL.md:144` documents `generate_uuid`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `generate_uuid` is a documented extra, a name the source still declares at `python/cocoindex/resources/id.py:61` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-090: Documented extra: get_component_context

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/component_ctx.py:305
**Export:** get_component_context

**Issue:** `SKILL.md:152` documents `get_component_context`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_component_context` is a documented extra, a name the source still declares at `python/cocoindex/_internal/component_ctx.py:305` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-091: Documented extra: get_multi_vector_schema

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:58
**Export:** get_multi_vector_schema

**Issue:** `SKILL.md:161` documents `get_multi_vector_schema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_multi_vector_schema` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:58` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-092: Documented extra: get_vector_schema

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:33
**Export:** get_vector_schema

**Issue:** `SKILL.md:161` documents `get_vector_schema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_vector_schema` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:33` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-093: Documented extra: is_live_component_class

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/live_component.py:35
**Export:** is_live_component_class

**Issue:** `SKILL.md:160` documents `is_live_component_class`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `is_live_component_class` is a documented extra, a name the source still declares at `python/cocoindex/_internal/live_component.py:35` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-094: Documented extra: is_non_existence

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/typing.py:63
**Export:** is_non_existence

**Issue:** `SKILL.md:157` documents `is_non_existence`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `is_non_existence` is a documented extra, a name the source still declares at `python/cocoindex/_internal/typing.py:63` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-095: Documented extra: lifespan

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/environment.py:449
**Export:** lifespan

**Issue:** `SKILL.md:3` documents `lifespan`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `lifespan` is a documented extra, a name the source still declares at `python/cocoindex/_internal/environment.py:449` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-096: Documented extra: litellm

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/litellm.py:1
**Export:** litellm

**Issue:** `SKILL.md:109` documents `litellm`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `litellm` is a documented extra, a name the source still declares at `python/cocoindex/ops/litellm.py:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-097: Documented extra: memo_fingerprint

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/memo_fingerprint.py:361
**Export:** memo_fingerprint

**Issue:** `SKILL.md:158` documents `memo_fingerprint`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `memo_fingerprint` is a documented extra, a name the source still declares at `python/cocoindex/_internal/memo_fingerprint.py:361` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-098: Documented extra: register_memo_key_function

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/memo_fingerprint.py:155
**Export:** register_memo_key_function

**Issue:** `SKILL.md:158` documents `register_memo_key_function`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `register_memo_key_function` is a documented extra, a name the source still declares at `python/cocoindex/_internal/memo_fingerprint.py:155` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-099: Documented extra: register_root_target_states_provider

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/target_state.py:305
**Export:** register_root_target_states_provider

**Issue:** `SKILL.md:156` documents `register_root_target_states_provider`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `register_root_target_states_provider` is a documented extra, a name the source still declares at `python/cocoindex/_internal/target_state.py:305` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-100: Documented extra: resolve_entities

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:186
**Export:** resolve_entities

**Issue:** `references/ops.md:184` documents `resolve_entities`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `resolve_entities` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:186` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-101: Documented extra: serialize_by_pickle

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/serde.py:151
**Export:** serialize_by_pickle

**Issue:** `SKILL.md:159` documents `serialize_by_pickle`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `serialize_by_pickle` is a documented extra, a name the source still declares at `python/cocoindex/_internal/serde.py:151` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-102: Documented extra: show_progress

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/app.py:194
**Export:** show_progress

**Issue:** `SKILL.md:140` documents `show_progress`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `show_progress` is a documented extra, a name the source still declares at `python/cocoindex/_internal/app.py:194` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-103: Documented extra: unpickle_safe

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/serde.py:128
**Export:** unpickle_safe

**Issue:** `SKILL.md:159` documents `unpickle_safe`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `unpickle_safe` is a documented extra, a name the source still declares at `python/cocoindex/_internal/serde.py:128` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-104: Documented extra: use_context

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/component_ctx.py:273
**Export:** use_context

**Issue:** `SKILL.md:8` documents `use_context`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `use_context` is a documented extra, a name the source still declares at `python/cocoindex/_internal/component_ctx.py:273` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### Discovery Quality

**Discovery Test:** not run: the hard gate blocked the run
