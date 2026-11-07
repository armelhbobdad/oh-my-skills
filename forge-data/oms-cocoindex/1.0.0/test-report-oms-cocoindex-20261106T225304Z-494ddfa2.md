---
workflowType: 'test-skill'
skillName: 'oms-cocoindex'
skillDir: 'skills/oms-cocoindex/1.0.0/oms-cocoindex'
runId: '20261106T225304Z-494ddfa2'
testMode: 'naive'
forgeTier: 'Deep'
hardGate: 'passed'
testResult: 'pass'
score: '100.0%'
threshold: '80%'
thresholdSource: 'workflow default (80%)'
analysisConfidence: 'full'
toolingStatus: 'ok'
workspaceDrift: 'ok'
health_check_dispatched: true
testDate: '2026-11-06T22:53:04Z'
stepsCompleted: ['init', 'detect-mode', 'coverage-check', 'coherence-check', 'external-validators', 'hard-gate', 'score', 'report']
nextWorkflow: 'export-skill'
---

# Test Report: {{skillName}}

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

**Mode Rationale:** metadata.json records `skill_type: "single"`, an individual skill, so the run checks API-surface coverage (naive mode); coherence is structural only and carries no scored category.

**Analysis Plan:**
- Coverage Check: every public export of the pinned cocoindex v1.0.0 source (5fe4f37) checked against SKILL.md and references/*.md, with Deep-tier AST-backed signature and type comparison against the source declarations
- Coherence Check: structural only (references resolve, documented files and links exist, metadata coherence), no integration-pattern scoring

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
| `App` | - | yes | yes | python/cocoindex/_internal/app.py:208 | PASS |
| `AppConfig` | - | yes | yes | python/cocoindex/_internal/app.py:202 | PASS |
| `AsyncCallable` | - | yes | - | - | WARN |
| `AsyncFunction` | - | yes | - | - | WARN |
| `AsyncTargetActionSinkFn` | - | yes | - | - | WARN |
| `CanonicalSide` | - | yes | - | - | WARN |
| `ChildTargetDef` | - | yes | yes | python/cocoindex/_internal/target_state.py:95 | PASS |
| `Chunk` | - | yes | - | - | WARN |
| `CollectionSchema` | class | yes | - | python/cocoindex/connectors/qdrant/_target.py:108 | WARN |
| `CollectionTarget` | class | yes | - | python/cocoindex/connectors/qdrant/_target.py:453 | WARN |
| `ColumnDef` | class | yes | - | python/cocoindex/connectors/doris/_target.py:330 | WARN |
| `ComponentContext` | - | yes | - | python/cocoindex/_internal/component_ctx.py:55 | PASS |
| `ComponentMountHandle` | class | yes | - | python/cocoindex/_internal/api.py:170 | PASS |
| `ComponentStats` | - | yes | yes | python/cocoindex/_internal/update_stats.py:14 | PASS |
| `ComponentSubpath` | - | yes | yes | python/cocoindex/_internal/component_ctx.py:142 | PASS |
| `ConnectionFactory` | class | yes | - | python/cocoindex/connectors/surrealdb/_target.py:105 | WARN |
| `ContextKey` | - | yes | yes | python/cocoindex/_internal/context_keys.py:99 | PASS |
| `ContextProvider` | - | yes | - | python/cocoindex/_internal/context_keys.py:124 | PASS |
| `CustomLanguageConfig` | - | yes | - | - | WARN |
| `DeletionValueFn` | - | yes | - | python/cocoindex/connectors/kafka/_target.py:206 | WARN |
| `DirTarget` | class | yes | - | python/cocoindex/connectors/localfs/_target.py:282 | WARN |
| `DirWalker` | class | yes | - | python/cocoindex/connectors/localfs/_source.py:68 | WARN |
| `DorisConnectionConfig` | class | yes | - | python/cocoindex/connectors/doris/_target.py:434 | WARN |
| `DorisTableTarget` | class | yes | - | python/cocoindex/connectors/doris/_target.py:1250 | WARN |
| `DorisType` | class | yes | - | python/cocoindex/connectors/doris/_target.py:282 | WARN |
| `DriveFile` | class | yes | - | python/cocoindex/connectors/google_drive/_source.py:83 | WARN |
| `DriveFileInfo` | class | yes | - | python/cocoindex/connectors/google_drive/_source.py:75 | WARN |
| `DropHandle` | - | yes | - | python/cocoindex/_internal/app.py:143 | PASS |
| `Embedder` | - | yes | - | - | WARN |
| `Environment` | - | yes | yes | python/cocoindex/_internal/environment.py:183 | PASS |
| `EnvironmentBuilder` | - | yes | yes | python/cocoindex/_internal/environment.py:87 | PASS |
| `ExceptionContext` | - | yes | - | python/cocoindex/_internal/component_ctx.py:43 | PASS |
| `ExceptionHandler` | - | yes | - | python/cocoindex/_internal/component_ctx.py:25 | PASS |
| `ExistingCanonicalPolicy` | - | yes | - | - | WARN |
| `File` | class | yes | - | python/cocoindex/connectors/localfs/_source.py:34 | WARN |
| `FileLike` | - | yes | - | - | WARN |
| `FileMetadata` | - | yes | - | - | WARN |
| `FilePath` | class | yes | - | python/cocoindex/connectors/localfs/_common.py:12 | WARN |
| `FilePathMatcher` | - | yes | - | - | WARN |
| `Function` | - | yes | - | - | WARN |
| `GPU` | - | yes | - | python/cocoindex/_internal/runner.py:282 | PASS |
| `GlobalExecutionOptions` | - | yes | - | - | WARN |
| `GoogleDriveSource` | class | yes | - | python/cocoindex/connectors/google_drive/_source.py:215 | WARN |
| `GoogleDriveSourceSpec` | class | yes | - | python/cocoindex/connectors/google_drive/_source.py:145 | WARN |
| `IdGenerator` | - | yes | - | - | WARN |
| `InvertedIndexDef` | class | yes | - | python/cocoindex/connectors/doris/_target.py:723 | WARN |
| `IsDeleteFn` | - | yes | - | python/cocoindex/connectors/kafka/_source.py:30 | WARN |
| `KafkaTopicTarget` | class | yes | - | python/cocoindex/connectors/kafka/_target.py:209 | WARN |
| `LanceAsyncConnection` | - | yes | - | - | WARN |
| `LanceType` | class | yes | - | python/cocoindex/connectors/lancedb/_target.py:63 | WARN |
| `LazyEnvironment` | - | yes | - | - | WARN |
| `LifespanFn` | - | yes | - | python/cocoindex/_internal/environment.py:118 | PASS |
| `LiteLLMEmbedder` | - | yes | - | - | WARN |
| `LiveComponent` | - | yes | - | python/cocoindex/_internal/live_component.py:28 | PASS |
| `LiveComponentOperator` | - | yes | - | python/cocoindex/_internal/live_component.py:46 | PASS |
| `LiveMapFeed` | - | yes | - | python/cocoindex/_internal/live_component.py:108 | PASS |
| `LiveMapSubscriber` | - | yes | - | python/cocoindex/_internal/live_component.py:130 | PASS |
| `LiveMapView` | - | yes | - | python/cocoindex/_internal/live_component.py:119 | PASS |
| `LlmPairResolver` | - | yes | - | - | WARN |
| `LogicTracking` | - | yes | - | python/cocoindex/_internal/function.py:65 | PASS |
| `ManagedConnection` | class | yes | - | python/cocoindex/connectors/doris/_target.py:457 | WARN |
| `MatchAllFilePathMatcher` | - | yes | - | - | WARN |
| `MaybePendingS` | - | yes | - | python/cocoindex/_internal/pending_marker.py:115 | PASS |
| `MemoStateOutcome` | - | yes | yes | python/cocoindex/_internal/typing.py:67 | PASS |
| `MultiVectorSchema` | - | yes | - | - | WARN |
| `MultiVectorSchemaProvider` | - | yes | - | - | WARN |
| `NON_EXISTENCE` | - | yes | - | python/cocoindex/_internal/typing.py:60 | PASS |
| `NonExistenceType` | - | yes | - | python/cocoindex/_internal/typing.py:47 | PASS |
| `NotMemoKeyable` | - | yes | - | python/cocoindex/_internal/memo_fingerprint.py:136 | PASS |
| `PairDecision` | - | yes | - | - | WARN |
| `PairResolver` | - | yes | - | - | WARN |
| `PatternFilePathMatcher` | - | yes | - | - | WARN |
| `PendingS` | - | yes | - | python/cocoindex/_internal/pending_marker.py:74 | PASS |
| `PendingTargetStateProvider` | - | yes | - | python/cocoindex/_internal/target_state.py:243 | PASS |
| `PgSourceSpec` | class | yes | - | python/cocoindex/connectors/postgres/_source.py:54 | WARN |
| `PgTableSource` | class | yes | - | python/cocoindex/connectors/postgres/_source.py:130 | WARN |
| `PgType` | class | yes | - | python/cocoindex/connectors/postgres/_target.py:77 | WARN |
| `PointStruct` | - | yes | - | python/cocoindex/connectors/qdrant/_target.py:42 | WARN |
| `QdrantVectorDef` | class | yes | yes | python/cocoindex/connectors/qdrant/_target.py:50 | WARN |
| `QueryHandlerInfo` | - | yes | - | - | WARN |
| `QueryHandlerResultFields` | - | yes | - | - | WARN |
| `QueryInfo` | - | yes | - | - | WARN |
| `QueryOutput` | - | yes | - | - | WARN |
| `ROOT_PATH` | - | yes | - | python/cocoindex/_internal/stable_path.py:59 | PASS |
| `RecursiveSplitter` | - | yes | - | - | WARN |
| `RelationTarget` | class | yes | - | python/cocoindex/connectors/surrealdb/_target.py:1153 | WARN |
| `ResolutionEvent` | - | yes | - | - | WARN |
| `ResolvedEntities` | - | yes | - | - | WARN |
| `ResolvedS` | - | yes | - | python/cocoindex/_internal/pending_marker.py:89 | PASS |
| `ResolvesTo` | - | yes | - | python/cocoindex/_internal/pending_marker.py:118 | PASS |
| `RetryConfig` | class | yes | - | python/cocoindex/connectors/doris/_target.py:178 | WARN |
| `RowFetcher` | class | yes | - | python/cocoindex/connectors/postgres/_source.py:62 | WARN |
| `Runner` | - | yes | - | python/cocoindex/_internal/runner.py:34 | PASS |
| `S3File` | class | yes | - | python/cocoindex/connectors/amazon_s3/_source.py:89 | WARN |
| `S3FilePath` | class | yes | - | python/cocoindex/connectors/amazon_s3/_source.py:46 | WARN |
| `S3Walker` | class | yes | - | python/cocoindex/connectors/amazon_s3/_source.py:247 | WARN |
| `SentenceTransformerEmbedder` | - | yes | - | - | WARN |
| `SeparatorSplitter` | - | yes | - | - | WARN |
| `ServerSettings` | - | yes | - | - | WARN |
| `Settings` | - | yes | yes | python/cocoindex/_internal/setting.py:56 | PASS |
| `SqliteType` | class | yes | - | python/cocoindex/connectors/sqlite/_target.py:154 | WARN |
| `StableKey` | - | yes | - | python/cocoindex/_internal/stable_path.py:9 | PASS |
| `StablePath` | - | yes | - | python/cocoindex/_internal/stable_path.py:16 | PASS |
| `SurrealType` | class | yes | - | python/cocoindex/connectors/surrealdb/_target.py:171 | WARN |
| `Symbol` | - | yes | yes | python/cocoindex/_internal/stable_path.py:7 | PASS |
| `SyncFunction` | - | yes | - | - | WARN |
| `TableSchema` | class | yes | - | python/cocoindex/connectors/doris/_target.py:339 | WARN |
| `TableTarget` | class | yes | - | python/cocoindex/connectors/lancedb/_target.py:732 | WARN |
| `TargetActionSink` | - | yes | - | python/cocoindex/_internal/target_state.py:143 | PASS |
| `TargetActionSinkFn` | - | yes | - | - | WARN |
| `TargetHandler` | - | yes | - | python/cocoindex/_internal/target_state.py:197 | PASS |
| `TargetReconcileOutput` | - | yes | yes | python/cocoindex/_internal/target_state.py:188 | PASS |
| `TargetState` | - | yes | yes | python/cocoindex/_internal/target_state.py:248 | PASS |
| `TargetStateProvider` | - | yes | - | python/cocoindex/_internal/target_state.py:208 | PASS |
| `TextPosition` | - | yes | - | - | WARN |
| `UpdateHandle` | - | yes | - | python/cocoindex/_internal/app.py:49 | PASS |
| `UpdateSnapshot` | - | yes | yes | python/cocoindex/_internal/update_stats.py:59 | PASS |
| `UpdateStats` | - | yes | yes | python/cocoindex/_internal/update_stats.py:39 | PASS |
| `UpdateStatus` | - | yes | - | python/cocoindex/_internal/update_stats.py:9 | PASS |
| `UuidGenerator` | - | yes | - | - | WARN |
| `ValueEncoder` | - | yes | - | python/cocoindex/connectors/doris/_target.py:79 | WARN |
| `Vec0TableDef` | class | yes | - | python/cocoindex/connectors/sqlite/_target.py:121 | WARN |
| `VectorIndexDef` | class | yes | - | python/cocoindex/connectors/doris/_target.py:709 | WARN |
| `VectorSchema` | - | yes | - | - | WARN |
| `VectorSchemaProvider` | - | yes | - | - | WARN |
| `build_vector_search_query` | function | yes | - | python/cocoindex/connectors/doris/_target.py:1317 | WARN |
| `cli` | - | yes | - | - | WARN |
| `collection_target` | function | yes | - | python/cocoindex/connectors/qdrant/_target.py:510 | WARN |
| `component_subpath` | - | yes | yes | python/cocoindex/_internal/component_ctx.py:198 | PASS |
| `connect` | function | yes | - | python/cocoindex/connectors/doris/_target.py:478 | WARN |
| `connect_async` | function | yes | - | python/cocoindex/connectors/doris/_target.py:1292 | WARN |
| `create_client` | function | yes | - | python/cocoindex/connectors/qdrant/_target.py:294 | WARN |
| `create_pool` | function | yes | - | python/cocoindex/connectors/postgres/_target.py:1367 | WARN |
| `declare_collection_target` | function | yes | - | python/cocoindex/connectors/qdrant/_target.py:537 | WARN |
| `declare_dir_target` | function | yes | - | python/cocoindex/connectors/localfs/_target.py:356 | WARN |
| `declare_file` | function | yes | - | python/cocoindex/connectors/localfs/_target.py:451 | WARN |
| `declare_kafka_topic_target` | function | yes | - | python/cocoindex/connectors/kafka/_target.py:277 | WARN |
| `declare_relation_target` | function | yes | - | python/cocoindex/connectors/surrealdb/_target.py:1357 | WARN |
| `declare_table_target` | function | yes | - | python/cocoindex/connectors/doris/_target.py:1206 | WARN |
| `declare_target_state` | - | yes | yes | python/cocoindex/_internal/target_state.py:265 | PASS |
| `declare_target_state_with_child` | - | yes | yes | python/cocoindex/_internal/target_state.py:282 | PASS |
| `default_env` | function | yes | yes | python/cocoindex/_internal/api.py:623 | PASS |
| `detect_code_language` | - | yes | - | - | WARN |
| `dir_target` | function | yes | - | python/cocoindex/connectors/localfs/_target.py:391 | WARN |
| `exception_handler` | - | yes | yes | python/cocoindex/_internal/component_ctx.py:331 | PASS |
| `fn` | - | yes | yes | python/cocoindex/_internal/function.py:1811 | PASS |
| `generate_id` | - | yes | - | - | WARN |
| `generate_uuid` | - | yes | - | - | WARN |
| `get_component_context` | - | yes | yes | python/cocoindex/_internal/component_ctx.py:305 | PASS |
| `get_default_db_path` | - | yes | - | - | WARN |
| `get_multi_vector_schema` | - | yes | - | - | WARN |
| `get_object` | function | yes | - | python/cocoindex/connectors/amazon_s3/_source.py:159 | WARN |
| `get_vector_schema` | - | yes | - | - | WARN |
| `is_live_component_class` | - | yes | - | - | WARN |
| `is_non_existence` | - | yes | yes | python/cocoindex/_internal/typing.py:63 | PASS |
| `kafka_topic_target` | function | yes | - | python/cocoindex/connectors/kafka/_target.py:250 | WARN |
| `lifespan` | - | yes | yes | python/cocoindex/_internal/environment.py:449 | PASS |
| `list_files` | function | yes | - | python/cocoindex/connectors/google_drive/_source.py:199 | WARN |
| `list_objects` | function | yes | - | python/cocoindex/connectors/amazon_s3/_source.py:351 | WARN |
| `litellm` | - | yes | - | - | WARN |
| `managed_connection` | function | yes | - | python/cocoindex/connectors/sqlite/_target.py:1282 | WARN |
| `map` | function | yes | yes | python/cocoindex/_internal/api.py:532 | PASS |
| `memo_fingerprint` | - | yes | yes | python/cocoindex/_internal/memo_fingerprint.py:361 | PASS |
| `mount` | function | yes | yes | python/cocoindex/_internal/api.py:333 | PASS |
| `mount_collection_target` | function | yes | yes | python/cocoindex/connectors/qdrant/_target.py:561 | WARN |
| `mount_dir_target` | function | yes | - | python/cocoindex/connectors/localfs/_target.py:424 | WARN |
| `mount_each` | function | yes | yes | python/cocoindex/_internal/api.py:427 | PASS |
| `mount_kafka_topic_target` | function | yes | - | python/cocoindex/connectors/kafka/_target.py:301 | WARN |
| `mount_relation_target` | function | yes | - | python/cocoindex/connectors/surrealdb/_target.py:1382 | WARN |
| `mount_table_target` | function | yes | yes | python/cocoindex/connectors/doris/_target.py:1228 | WARN |
| `mount_target` | function | yes | yes | python/cocoindex/_internal/api.py:566 | PASS |
| `read` | function | yes | - | python/cocoindex/connectors/amazon_s3/_source.py:221 | WARN |
| `register_memo_key_function` | - | yes | yes | python/cocoindex/_internal/memo_fingerprint.py:155 | PASS |
| `register_root_target_states_provider` | - | yes | yes | python/cocoindex/_internal/target_state.py:305 | PASS |
| `relation_target` | function | yes | - | python/cocoindex/connectors/surrealdb/_target.py:1329 | WARN |
| `resolve_entities` | - | yes | - | - | WARN |
| `runtime` | function | yes | yes | python/cocoindex/_internal/api.py:655 | PASS |
| `serialize_by_pickle` | - | yes | yes | python/cocoindex/_internal/serde.py:151 | PASS |
| `show_progress` | - | yes | yes | python/cocoindex/_internal/app.py:194 | PASS |
| `start` | function | yes | yes | python/cocoindex/_internal/api.py:603 | PASS |
| `start_blocking` | function | yes | yes | python/cocoindex/_internal/api.py:613 | PASS |
| `stop` | function | yes | yes | python/cocoindex/_internal/api.py:608 | PASS |
| `stop_blocking` | function | yes | yes | python/cocoindex/_internal/api.py:618 | PASS |
| `table_target` | function | yes | - | python/cocoindex/connectors/doris/_target.py:1187 | WARN |
| `topic_as_map` | function | yes | yes | python/cocoindex/connectors/kafka/_source.py:361 | WARN |
| `unpickle_safe` | - | yes | yes | python/cocoindex/_internal/serde.py:128 | PASS |
| `use_context` | - | yes | yes | python/cocoindex/_internal/component_ctx.py:273 | PASS |
| `use_mount` | function | yes | yes | python/cocoindex/_internal/api.py:194 | PASS |
| `walk_dir` | function | yes | yes | python/cocoindex/connectors/localfs/_source.py:234 | WARN |

### Coverage Summary

- **Exports Found:** 72
- **Documented:** 72 (100%)
- **Missing Documentation:** 0
- **Signature Mismatches:** 0
- **Stale Documentation:** 117, documented extras included
- **Nested Entry Points:** `python/cocoindex/connectors/amazon_s3/__init__.py` inside `python/cocoindex/__init__.py`: `S3File`, `S3FilePath`, `S3Walker`, `get_object`, `list_objects`, `read`; `python/cocoindex/connectors/doris/__init__.py` inside `python/cocoindex/__init__.py`: `ColumnDef`, `DorisConnectionConfig`, `DorisTableTarget`, `DorisType`, `InvertedIndexDef`, `ManagedConnection`, `RetryConfig`, `TableSchema`, `ValueEncoder`, `VectorIndexDef`, `build_vector_search_query`, `connect`, `connect_async`, `declare_table_target`, `mount_table_target`, `table_target`; `python/cocoindex/connectors/google_drive/__init__.py` inside `python/cocoindex/__init__.py`: `DriveFile`, `DriveFileInfo`, `GoogleDriveSource`, `GoogleDriveSourceSpec`, `list_files`; `python/cocoindex/connectors/kafka/__init__.py` inside `python/cocoindex/__init__.py`: `DeletionValueFn`, `IsDeleteFn`, `KafkaTopicTarget`, `declare_kafka_topic_target`, `kafka_topic_target`, `mount_kafka_topic_target`, `topic_as_map`; `python/cocoindex/connectors/lancedb/__init__.py` inside `python/cocoindex/__init__.py`: `ColumnDef`, `LanceAsyncConnection`, `LanceType`, `TableSchema`, `TableTarget`, `ValueEncoder`, `connect`, `connect_async`, `declare_table_target`, `mount_table_target`, `table_target`; `python/cocoindex/connectors/localfs/__init__.py` inside `python/cocoindex/__init__.py`: `DirTarget`, `DirWalker`, `File`, `FilePath`, `declare_dir_target`, `declare_file`, `dir_target`, `mount_dir_target`, `walk_dir`; `python/cocoindex/connectors/postgres/__init__.py` inside `python/cocoindex/__init__.py`: `ColumnDef`, `PgSourceSpec`, `PgTableSource`, `PgType`, `RowFetcher`, `TableSchema`, `TableTarget`, `ValueEncoder`, `create_pool`, `declare_table_target`, `mount_table_target`, `table_target`; `python/cocoindex/connectors/qdrant/__init__.py` inside `python/cocoindex/__init__.py`: `CollectionSchema`, `CollectionTarget`, `PointStruct`, `QdrantVectorDef`, `collection_target`, `create_client`, `declare_collection_target`, `mount_collection_target`; `python/cocoindex/connectors/sqlite/__init__.py` inside `python/cocoindex/__init__.py`: `ColumnDef`, `ManagedConnection`, `SqliteType`, `TableSchema`, `TableTarget`, `ValueEncoder`, `Vec0TableDef`, `connect`, `declare_table_target`, `managed_connection`, `mount_table_target`, `table_target`; `python/cocoindex/connectors/surrealdb/__init__.py` inside `python/cocoindex/__init__.py`: `ColumnDef`, `ConnectionFactory`, `RelationTarget`, `SurrealType`, `TableSchema`, `TableTarget`, `ValueEncoder`, `declare_relation_target`, `declare_table_target`, `mount_relation_target`, `mount_table_target`, `relation_target`, `table_target`
- **Restored by the Stale-Scope Guard:** `App` (python/cocoindex/_internal/app.py:208), `AppConfig` (python/cocoindex/_internal/app.py:202), `ChildTargetDef` (python/cocoindex/_internal/target_state.py:95), `ComponentContext` (python/cocoindex/_internal/component_ctx.py:55), `ComponentStats` (python/cocoindex/_internal/update_stats.py:14), `ComponentSubpath` (python/cocoindex/_internal/component_ctx.py:142), `ContextKey` (python/cocoindex/_internal/context_keys.py:99), `ContextProvider` (python/cocoindex/_internal/context_keys.py:124), `DropHandle` (python/cocoindex/_internal/app.py:143), `Environment` (python/cocoindex/_internal/environment.py:183), `EnvironmentBuilder` (python/cocoindex/_internal/environment.py:87), `ExceptionContext` (python/cocoindex/_internal/component_ctx.py:43), `ExceptionHandler` (python/cocoindex/_internal/component_ctx.py:25), `GPU` (python/cocoindex/_internal/runner.py:282), `LifespanFn` (python/cocoindex/_internal/environment.py:118), `LiveComponent` (python/cocoindex/_internal/live_component.py:28), `LiveComponentOperator` (python/cocoindex/_internal/live_component.py:46), `LiveMapFeed` (python/cocoindex/_internal/live_component.py:108), `LiveMapSubscriber` (python/cocoindex/_internal/live_component.py:130), `LiveMapView` (python/cocoindex/_internal/live_component.py:119), `LogicTracking` (python/cocoindex/_internal/function.py:65), `MaybePendingS` (python/cocoindex/_internal/pending_marker.py:115), `MemoStateOutcome` (python/cocoindex/_internal/typing.py:67), `NON_EXISTENCE` (python/cocoindex/_internal/typing.py:60), `NonExistenceType` (python/cocoindex/_internal/typing.py:47), `NotMemoKeyable` (python/cocoindex/_internal/memo_fingerprint.py:136), `PendingS` (python/cocoindex/_internal/pending_marker.py:74), `PendingTargetStateProvider` (python/cocoindex/_internal/target_state.py:243), `ROOT_PATH` (python/cocoindex/_internal/stable_path.py:59), `ResolvedS` (python/cocoindex/_internal/pending_marker.py:89), `ResolvesTo` (python/cocoindex/_internal/pending_marker.py:118), `Runner` (python/cocoindex/_internal/runner.py:34), `Settings` (python/cocoindex/_internal/setting.py:56), `StableKey` (python/cocoindex/_internal/stable_path.py:9), `StablePath` (python/cocoindex/_internal/stable_path.py:16), `Symbol` (python/cocoindex/_internal/stable_path.py:7), `TargetActionSink` (python/cocoindex/_internal/target_state.py:143), `TargetHandler` (python/cocoindex/_internal/target_state.py:197), `TargetReconcileOutput` (python/cocoindex/_internal/target_state.py:188), `TargetState` (python/cocoindex/_internal/target_state.py:248), `TargetStateProvider` (python/cocoindex/_internal/target_state.py:208), `UpdateHandle` (python/cocoindex/_internal/app.py:49), `UpdateSnapshot` (python/cocoindex/_internal/update_stats.py:59), `UpdateStats` (python/cocoindex/_internal/update_stats.py:39), `UpdateStatus` (python/cocoindex/_internal/update_stats.py:9), `component_subpath` (python/cocoindex/_internal/component_ctx.py:198), `declare_target_state` (python/cocoindex/_internal/target_state.py:265), `declare_target_state_with_child` (python/cocoindex/_internal/target_state.py:282), `exception_handler` (python/cocoindex/_internal/component_ctx.py:331), `fn` (python/cocoindex/_internal/function.py:1811), `get_component_context` (python/cocoindex/_internal/component_ctx.py:305), `is_non_existence` (python/cocoindex/_internal/typing.py:63), `lifespan` (python/cocoindex/_internal/environment.py:449), `memo_fingerprint` (python/cocoindex/_internal/memo_fingerprint.py:361), `register_memo_key_function` (python/cocoindex/_internal/memo_fingerprint.py:155), `register_root_target_states_provider` (python/cocoindex/_internal/target_state.py:305), `serialize_by_pickle` (python/cocoindex/_internal/serde.py:151), `show_progress` (python/cocoindex/_internal/app.py:194), `unpickle_safe` (python/cocoindex/_internal/serde.py:128), `use_context` (python/cocoindex/_internal/component_ctx.py:273)

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 100% |
| Signature Accuracy | 100% |
| Type Coverage | 100% |

**Notes:**

- Extraction: the recipe runner read all 73 in-scope files (`status: ok`, no fallback). No file was read by eye (`readByEye` empty) and none was left unread (`unread` empty).
- Extraction gaps: no recipe found `DeletionValueFn` (python/cocoindex/connectors/kafka/_target.py:206), `IsDeleteFn` (python/cocoindex/connectors/kafka/_source.py:30), `LanceAsyncConnection` (no file recorded), `PointStruct` (python/cocoindex/connectors/qdrant/_target.py:42) or `ValueEncoder` (python/cocoindex/connectors/doris/_target.py:79). They are on the surface as nested-entry names. The skill documents a signature only for `IsDeleteFn`: `Callable[[Message], bool]` (references/connectors.md:151) matches the alias at kafka/_source.py:30, read by eye.
- Documented inventory: built in the main thread (no subagent could be started in this session, the step's "Without subagents" path) from SKILL.md and all 7 reference files, since SKILL.md has no `## Full` headings: 379 entries, the floor's 38 names all kept with their pinned signatures, spot-check clean.
- Signature comparison: the plan listed 46 checks over 17 files. Each file's checks were judged in the main thread under references/signature-comparison-rules.md, the same rules text for every file, one result per file in `signatures-1.txt` to `signatures-17.txt`. Every check matched: Signature Accuracy 46/46. Two calls the rules file leaves open were counted as matches and recorded as borderline: `fn` (call forms compared through `_FunctionDecorator.__call__`, the declaration at function.py:1811 being an instance) and `Symbol` (call form read through the alias `Symbol = core.Symbol` to `core.pyi`'s `__new__(cls, name: str)`).
- Split-body cross-check (§1b): every export documented in two or more files was compared, SKILL.md body against each reference file. No forms contradict, so `cross_check_mismatches` is empty.
- Numerator ground truth: skipped (no inflation signature: `stats.exports_documented` 154 differs from any stored effective denominator, which is absent).
- Stale names: `classify-stale` read all 117 at the pinned commit. None is fabricated. 101 have one defining file (`defined_at`). 16 are declared in several files (connector homonyms, or an ops/resources class that `core.pyi` also declares); the ledger records 106 documented extras in all (Info `observation`) and 11 Medium `stale-documentation` gaps for `ColumnDef`, `FilePath`, `ManagedConnection`, `TableSchema`, `TableTarget`, `ValueEncoder`, `connect`, `connect_async`, `declare_table_target`, `mount_table_target` and `table_target`, homonyms with no single cited declaring file (§2c).
- Guards: the stale-scope guard fires (`docs/docs/**/*.md` and `docs/docs/**/*.mdx` match no file) and restores the root exports. Deflation is not applicable and inflation does not fire.
- Metadata count cross-check: `stats.exports_public_api` 140 against `exports[].length` 118 is a 16% drift (Medium `metadata-drift`).
- Provenance line check (§4c): 118 exports and 154 entries checked, `stale` empty, so no line gap.
- Deep tier, not checked by script: the claims read while judging (handle methods, live-component operator and subscriber returns, connector and resource `__all__` lists, LiteLLM `input_type` override, `@coco.fn` batching/runner behavior, default-environment `COCOINDEX_DB` fallback, CLI group options) agree with the pinned source; no `Not checked by script` observation is recorded.

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)

### Structural Findings

| # | Type | Severity | Detail | Line |
|---|------|----------|--------|------|
| - | none | - | No structural issue: §2.1 description is served by the frontmatter `description` (no Description/Overview heading), usage by `## Quick Start` (SKILL.md:12) and API surface by `## Key API Summary` (SKILL.md:170). §2.2 has 8 fences, balanced. §2.3 has no bare opening fence. §2.4 has no function or method export with zero usage (split-body scope: SKILL.md usage sections and the 7 reference files, 64 exports counted). §2.5 has no async/sync contradiction across the 43 called exports. §2.6 has no table drift. §2.7 has no scripts/ or assets/ folder. | - |

**Structural Issues:** 0

- **Migration section (§2b):** the run is Deep tier and the evidence report pins `t2_future_count: 0` (forge-data/oms-cocoindex/1.0.0/evidence-report.md frontmatter). SKILL.md has no Section 4b ("Migration & Deprecation Warnings") heading: its `## Migration from v0.3.37` at SKILL.md:303 is a different section. So none of Cases 1 to 3 applies and no gap is recorded.

### Reference Consistency (split-body)

| # | Reference File | Export | Issue | Other Side | Reference Line | Contradicted Side |
|---|---------------|--------|-------|------------|---------------|-------------------|
| - | - | - | no split-body mismatch | - | - | - |

**Exports Cross-Checked:** 108
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
- **External Validation Score:** 100.0%
- **Tools used:** skill-check

## Completeness Score

### Score Breakdown

| Category | Score | Weight | Weighted |
|----------|-------|--------|----------|
| Export Coverage | 100.0% | 45.0% | 45.0% |
| Signature Accuracy | 100.0% | 25.0% | 25.0% |
| Type Coverage | 100.0% | 20.0% | 20.0% |
| Coherence | not scored | 0% | 0% |
| External Validation | 100.0% | 10.0% | 10.0% |
| **Total** | | **100%** | **100.0%** |

### Result

**Score:** 100.0%
**Threshold:** 80%
**Result:** **PASS**

**Threshold Source:** workflow default (80%)
**Weight Distribution:** naive (redistributed)
**Tier Adjustment:** none
**External Validators:** skill-check only
**Analysis Confidence:** full
**Tooling Status:** ok

## Gap Report

**Total Gaps:** 120
**Blocking (Critical + High):** 0
**Non-blocking (Medium + Low + Info):** 120

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|------------------|
| Critical | 0 | None |
| High | 0 | None |
| Medium | 13 | Add type definitions, interface docs or the missing section |
| Low | 0 | None |
| Info | 107 | Optional improvements, no action required |
| **Total** | **120** | |

### GAP-008: Stale documentation: ColumnDef

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/connectors.md:9
**Export:** ColumnDef

**Issue:** SKILL.md documents `ColumnDef`, which the enumerated source API surface lacks

**Remediation:** Check `ColumnDef` against the source and update or remove its documentation at references/connectors.md:9: the enumerated source surface does not export it.

### GAP-024: Stale documentation: FilePath

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:348
**Export:** FilePath

**Issue:** SKILL.md documents `FilePath`, which the enumerated source API surface lacks

**Remediation:** Check `FilePath` against the source and update or remove its documentation at SKILL.md:348: the enumerated source surface does not export it.

### GAP-039: Stale documentation: ManagedConnection

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/connectors.md:111
**Export:** ManagedConnection

**Issue:** SKILL.md documents `ManagedConnection`, which the enumerated source API surface lacks

**Remediation:** Check `ManagedConnection` against the source and update or remove its documentation at references/connectors.md:111: the enumerated source surface does not export it.

### GAP-070: Stale documentation: TableSchema

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:72
**Export:** TableSchema

**Issue:** SKILL.md documents `TableSchema`, which the enumerated source API surface lacks

**Remediation:** Check `TableSchema` against the source and update or remove its documentation at SKILL.md:72: the enumerated source surface does not export it.

### GAP-071: Stale documentation: TableTarget

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:50
**Export:** TableTarget

**Issue:** SKILL.md documents `TableTarget`, which the enumerated source API surface lacks

**Remediation:** Check `TableTarget` against the source and update or remove its documentation at SKILL.md:50: the enumerated source surface does not export it.

### GAP-075: Stale documentation: ValueEncoder

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/connectors.md:9
**Export:** ValueEncoder

**Issue:** SKILL.md documents `ValueEncoder`, which the enumerated source API surface lacks

**Remediation:** Check `ValueEncoder` against the source and update or remove its documentation at references/connectors.md:9: the enumerated source surface does not export it.

### GAP-083: Stale documentation: connect

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/connectors.md:88
**Export:** connect

**Issue:** SKILL.md documents `connect`, which the enumerated source API surface lacks

**Remediation:** Check `connect` against the source and update or remove its documentation at references/connectors.md:88: the enumerated source surface does not export it.

### GAP-084: Stale documentation: connect_async

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/connectors.md:88
**Export:** connect_async

**Issue:** SKILL.md documents `connect_async`, which the enumerated source API surface lacks

**Remediation:** Check `connect_async` against the source and update or remove its documentation at references/connectors.md:88: the enumerated source surface does not export it.

### GAP-092: Stale documentation: declare_table_target

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/connectors.md:21
**Export:** declare_table_target

**Issue:** SKILL.md documents `declare_table_target`, which the enumerated source API surface lacks

**Remediation:** Check `declare_table_target` against the source and update or remove its documentation at references/connectors.md:21: the enumerated source surface does not export it.

### GAP-111: Stale documentation: mount_table_target

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:69
**Export:** mount_table_target

**Issue:** SKILL.md documents `mount_table_target`, which the enumerated source API surface lacks

**Remediation:** Check `mount_table_target` against the source and update or remove its documentation at SKILL.md:69: the enumerated source surface does not export it.

### GAP-115: Stale documentation: table_target

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/connectors.md:21
**Export:** table_target

**Issue:** SKILL.md documents `table_target`, which the enumerated source API surface lacks

**Remediation:** Check `table_target` against the source and update or remove its documentation at references/connectors.md:21: the enumerated source surface does not export it.

### GAP-118: stale brief scope: scope.include globs match no source file

**Severity:** Medium
**Category:** Coverage (brief-scope-stale)
**Source:** forge-data/oms-cocoindex/skill-brief.yaml

**Issue:** the `scope.include` globs `docs/docs/**/*.md`, `docs/docs/**/*.mdx` match no file in the source tested; the `all` set restores 60 root exports, defined in files no include glob covers: `App` in `python/cocoindex/_internal/app.py`, `AppConfig` in `python/cocoindex/_internal/app.py`, `ChildTargetDef` in `python/cocoindex/_internal/target_state.py`, `ComponentContext` in `python/cocoindex/_internal/component_ctx.py`, `ComponentStats` in `python/cocoindex/_internal/update_stats.py`, `ComponentSubpath` in `python/cocoindex/_internal/component_ctx.py`, `ContextKey` in `python/cocoindex/_internal/context_keys.py`, `ContextProvider` in `python/cocoindex/_internal/context_keys.py`, `DropHandle` in `python/cocoindex/_internal/app.py`, `Environment` in `python/cocoindex/_internal/environment.py`, `EnvironmentBuilder` in `python/cocoindex/_internal/environment.py`, `ExceptionContext` in `python/cocoindex/_internal/component_ctx.py`, `ExceptionHandler` in `python/cocoindex/_internal/component_ctx.py`, `GPU` in `python/cocoindex/_internal/runner.py`, `LifespanFn` in `python/cocoindex/_internal/environment.py`, `LiveComponent` in `python/cocoindex/_internal/live_component.py`, `LiveComponentOperator` in `python/cocoindex/_internal/live_component.py`, `LiveMapFeed` in `python/cocoindex/_internal/live_component.py`, `LiveMapSubscriber` in `python/cocoindex/_internal/live_component.py`, `LiveMapView` in `python/cocoindex/_internal/live_component.py`, `LogicTracking` in `python/cocoindex/_internal/function.py`, `MaybePendingS` in `python/cocoindex/_internal/pending_marker.py`, `MemoStateOutcome` in `python/cocoindex/_internal/typing.py`, `NON_EXISTENCE` in `python/cocoindex/_internal/typing.py`, `NonExistenceType` in `python/cocoindex/_internal/typing.py`, `NotMemoKeyable` in `python/cocoindex/_internal/memo_fingerprint.py`, `PendingS` in `python/cocoindex/_internal/pending_marker.py`, `PendingTargetStateProvider` in `python/cocoindex/_internal/target_state.py`, `ROOT_PATH` in `python/cocoindex/_internal/stable_path.py`, `ResolvedS` in `python/cocoindex/_internal/pending_marker.py`, `ResolvesTo` in `python/cocoindex/_internal/pending_marker.py`, `Runner` in `python/cocoindex/_internal/runner.py`, `Settings` in `python/cocoindex/_internal/setting.py`, `StableKey` in `python/cocoindex/_internal/stable_path.py`, `StablePath` in `python/cocoindex/_internal/stable_path.py`, `Symbol` in `python/cocoindex/_internal/stable_path.py`, `TargetActionSink` in `python/cocoindex/_internal/target_state.py`, `TargetHandler` in `python/cocoindex/_internal/target_state.py`, `TargetReconcileOutput` in `python/cocoindex/_internal/target_state.py`, `TargetState` in `python/cocoindex/_internal/target_state.py`, `TargetStateProvider` in `python/cocoindex/_internal/target_state.py`, `UpdateHandle` in `python/cocoindex/_internal/app.py`, `UpdateSnapshot` in `python/cocoindex/_internal/update_stats.py`, `UpdateStats` in `python/cocoindex/_internal/update_stats.py`, `UpdateStatus` in `python/cocoindex/_internal/update_stats.py`, `component_subpath` in `python/cocoindex/_internal/component_ctx.py`, `declare_target_state` in `python/cocoindex/_internal/target_state.py`, `declare_target_state_with_child` in `python/cocoindex/_internal/target_state.py`, `exception_handler` in `python/cocoindex/_internal/component_ctx.py`, `fn` in `python/cocoindex/_internal/function.py`, `get_component_context` in `python/cocoindex/_internal/component_ctx.py`, `is_non_existence` in `python/cocoindex/_internal/typing.py`, `lifespan` in `python/cocoindex/_internal/environment.py`, `memo_fingerprint` in `python/cocoindex/_internal/memo_fingerprint.py`, `register_memo_key_function` in `python/cocoindex/_internal/memo_fingerprint.py`, `register_root_target_states_provider` in `python/cocoindex/_internal/target_state.py`, `serialize_by_pickle` in `python/cocoindex/_internal/serde.py`, `show_progress` in `python/cocoindex/_internal/app.py`, `unpickle_safe` in `python/cocoindex/_internal/serde.py`, `use_context` in `python/cocoindex/_internal/component_ctx.py`

**Remediation:** Edit `scope.include` in `forge-data/oms-cocoindex/skill-brief.yaml` by hand so each glob matches the files it meant in this version of the source (update-skill does not rewrite an include glob), and add to `scope.exclude` any restored file the brief meant to leave out.

### GAP-119: metadata drift — barrel export counts diverge

**Severity:** Medium
**Category:** Coverage (metadata-drift)
**Source:** skills/oms-cocoindex/1.0.0/oms-cocoindex/metadata.json

**Issue:** stats.exports_public_api=140, exports[].length=118 → 16% drift

**Remediation:** Re-run Create Skill, which rebuilds `exports[]` and `stats.exports_public_api` in `skills/oms-cocoindex/1.0.0/oms-cocoindex/metadata.json` from the source. Update Skill does not repair this drift: each time it writes the skill it recounts `stats.exports_public_api` from the source and keeps `exports[]`, adding or dropping only the names its provenance map changes, so a metadata patch does not hold.

### GAP-001: Documented extra: AsyncCallable

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/function.py:62
**Export:** AsyncCallable

**Issue:** `references/component-api.md:23` documents `AsyncCallable`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `AsyncCallable` is a documented extra, a name the source still declares at `python/cocoindex/_internal/function.py:62` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-002: Documented extra: AsyncFunction

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/function.py:903
**Export:** AsyncFunction

**Issue:** `SKILL.md:275` documents `AsyncFunction`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `AsyncFunction` is a documented extra, a name the source still declares at `python/cocoindex/_internal/function.py:903` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-003: Documented extra: AsyncTargetActionSinkFn

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/target_state.py:121
**Export:** AsyncTargetActionSinkFn

**Issue:** `references/target-state.md:38` documents `AsyncTargetActionSinkFn`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `AsyncTargetActionSinkFn` is a documented extra, a name the source still declares at `python/cocoindex/_internal/target_state.py:121` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-004: Documented extra: CanonicalSide

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:35
**Export:** CanonicalSide

**Issue:** `references/ops.md:184` documents `CanonicalSide`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CanonicalSide` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:35` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-005: Documented extra: Chunk

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/chunk.py:26
**Export:** Chunk

**Issue:** `SKILL.md:25` documents `Chunk`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `python/cocoindex/resources/chunk.py`

**Remediation:** No change: `Chunk` is a documented extra, a name the source still declares at `python/cocoindex/resources/chunk.py:26` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-006: Documented extra: CollectionSchema

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/qdrant/_target.py:108
**Export:** CollectionSchema

**Issue:** `references/connectors.md:51` documents `CollectionSchema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CollectionSchema` is a documented extra, a name the source still declares at `python/cocoindex/connectors/qdrant/_target.py:108` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-007: Documented extra: CollectionTarget

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/qdrant/_target.py:453
**Export:** CollectionTarget

**Issue:** `references/connectors.md:51` documents `CollectionTarget`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CollectionTarget` is a documented extra, a name the source still declares at `python/cocoindex/connectors/qdrant/_target.py:453` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-009: Documented extra: ConnectionFactory

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/surrealdb/_target.py:105
**Export:** ConnectionFactory

**Issue:** `references/connectors.md:98` documents `ConnectionFactory`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ConnectionFactory` is a documented extra, a name the source still declares at `python/cocoindex/connectors/surrealdb/_target.py:105` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-010: Documented extra: CustomLanguageConfig

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/text.py:87
**Export:** CustomLanguageConfig

**Issue:** `SKILL.md:117` documents `CustomLanguageConfig`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `python/cocoindex/ops/text.py`

**Remediation:** No change: `CustomLanguageConfig` is a documented extra, a name the source still declares at `python/cocoindex/ops/text.py:87` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-011: Documented extra: DeletionValueFn

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/kafka/_target.py:206
**Export:** DeletionValueFn

**Issue:** `references/connectors.md:145` documents `DeletionValueFn`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `DeletionValueFn` is a documented extra, a name the source still declares at `python/cocoindex/connectors/kafka/_target.py:206` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-012: Documented extra: DirTarget

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/localfs/_target.py:282
**Export:** DirTarget

**Issue:** `references/connectors.md:187` documents `DirTarget`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `DirTarget` is a documented extra, a name the source still declares at `python/cocoindex/connectors/localfs/_target.py:282` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-013: Documented extra: DirWalker

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/localfs/_source.py:68
**Export:** DirWalker

**Issue:** `SKILL.md:346` documents `DirWalker`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `DirWalker` is a documented extra, a name the source still declares at `python/cocoindex/connectors/localfs/_source.py:68` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-014: Documented extra: DorisConnectionConfig

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/doris/_target.py:434
**Export:** DorisConnectionConfig

**Issue:** `references/connectors.md:125` documents `DorisConnectionConfig`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `DorisConnectionConfig` is a documented extra, a name the source still declares at `python/cocoindex/connectors/doris/_target.py:434` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-015: Documented extra: DorisTableTarget

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/doris/_target.py:1250
**Export:** DorisTableTarget

**Issue:** `references/connectors.md:125` documents `DorisTableTarget`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `DorisTableTarget` is a documented extra, a name the source still declares at `python/cocoindex/connectors/doris/_target.py:1250` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-016: Documented extra: DorisType

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/doris/_target.py:282
**Export:** DorisType

**Issue:** `references/connectors.md:125` documents `DorisType`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `DorisType` is a documented extra, a name the source still declares at `python/cocoindex/connectors/doris/_target.py:282` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-017: Documented extra: DriveFile

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/google_drive/_source.py:83
**Export:** DriveFile

**Issue:** `references/connectors.md:225` documents `DriveFile`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `DriveFile` is a documented extra, a name the source still declares at `python/cocoindex/connectors/google_drive/_source.py:83` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-018: Documented extra: DriveFileInfo

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/google_drive/_source.py:75
**Export:** DriveFileInfo

**Issue:** `references/connectors.md:225` documents `DriveFileInfo`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `DriveFileInfo` is a documented extra, a name the source still declares at `python/cocoindex/connectors/google_drive/_source.py:75` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-019: Documented extra: Embedder

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/embedder.py:15
**Export:** Embedder

**Issue:** `SKILL.md:168` documents `Embedder`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Embedder` is a documented extra, a name the source still declares at `python/cocoindex/resources/embedder.py:15` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-020: Documented extra: ExistingCanonicalPolicy

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:57
**Export:** ExistingCanonicalPolicy

**Issue:** `references/ops.md:186` documents `ExistingCanonicalPolicy`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ExistingCanonicalPolicy` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:57` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-021: Documented extra: File

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/localfs/_source.py:34
**Export:** File

**Issue:** `SKILL.md:346` documents `File`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `File` is a documented extra, a name the source still declares at `python/cocoindex/connectors/localfs/_source.py:34` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-022: Documented extra: FileLike

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/file.py:56
**Export:** FileLike

**Issue:** `SKILL.md:26` documents `FileLike`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `FileLike` is a documented extra, a name the source still declares at `python/cocoindex/resources/file.py:56` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-023: Documented extra: FileMetadata

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/file.py:40
**Export:** FileMetadata

**Issue:** `SKILL.md:348` documents `FileMetadata`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `FileMetadata` is a documented extra, a name the source still declares at `python/cocoindex/resources/file.py:40` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-025: Documented extra: FilePathMatcher

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/file.py:205
**Export:** FilePathMatcher

**Issue:** `references/resources.md:35` documents `FilePathMatcher`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `FilePathMatcher` is a documented extra, a name the source still declares at `python/cocoindex/resources/file.py:205` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-026: Documented extra: Function

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/function.py:138
**Export:** Function

**Issue:** `SKILL.md:275` documents `Function`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Function` is a documented extra, a name the source still declares at `python/cocoindex/_internal/function.py:138` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-027: Documented extra: GlobalExecutionOptions

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/setting.py:12
**Export:** GlobalExecutionOptions

**Issue:** `SKILL.md:213` documents `GlobalExecutionOptions`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `GlobalExecutionOptions` is a documented extra, a name the source still declares at `python/cocoindex/setting.py:12` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-028: Documented extra: GoogleDriveSource

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/google_drive/_source.py:215
**Export:** GoogleDriveSource

**Issue:** `references/connectors.md:226` documents `GoogleDriveSource`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `GoogleDriveSource` is a documented extra, a name the source still declares at `python/cocoindex/connectors/google_drive/_source.py:215` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-029: Documented extra: GoogleDriveSourceSpec

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/google_drive/_source.py:145
**Export:** GoogleDriveSourceSpec

**Issue:** `references/connectors.md:226` documents `GoogleDriveSourceSpec`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `GoogleDriveSourceSpec` is a documented extra, a name the source still declares at `python/cocoindex/connectors/google_drive/_source.py:145` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-030: Documented extra: IdGenerator

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/id.py:89
**Export:** IdGenerator

**Issue:** `SKILL.md:27` documents `IdGenerator`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `IdGenerator` is a documented extra, a name the source still declares at `python/cocoindex/resources/id.py:89` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-031: Documented extra: InvertedIndexDef

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/doris/_target.py:723
**Export:** InvertedIndexDef

**Issue:** `references/connectors.md:126` documents `InvertedIndexDef`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `InvertedIndexDef` is a documented extra, a name the source still declares at `python/cocoindex/connectors/doris/_target.py:723` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-032: Documented extra: IsDeleteFn

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/kafka/_source.py:30
**Export:** IsDeleteFn

**Issue:** `references/connectors.md:139` documents `IsDeleteFn`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `IsDeleteFn` is a documented extra, a name the source still declares at `python/cocoindex/connectors/kafka/_source.py:30` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-033: Documented extra: KafkaTopicTarget

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/kafka/_target.py:209
**Export:** KafkaTopicTarget

**Issue:** `references/connectors.md:145` documents `KafkaTopicTarget`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `KafkaTopicTarget` is a documented extra, a name the source still declares at `python/cocoindex/connectors/kafka/_target.py:209` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-034: Documented extra: LanceAsyncConnection

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/lancedb/_target.py:33
**Export:** LanceAsyncConnection

**Issue:** `references/connectors.md:86` documents `LanceAsyncConnection`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LanceAsyncConnection` is a documented extra, a name the source still declares at `python/cocoindex/connectors/lancedb/_target.py:33` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-035: Documented extra: LanceType

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/lancedb/_target.py:63
**Export:** LanceType

**Issue:** `references/connectors.md:86` documents `LanceType`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LanceType` is a documented extra, a name the source still declares at `python/cocoindex/connectors/lancedb/_target.py:63` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-036: Documented extra: LazyEnvironment

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/environment.py:287
**Export:** LazyEnvironment

**Issue:** `SKILL.md:175` documents `LazyEnvironment`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LazyEnvironment` is a documented extra, a name the source still declares at `python/cocoindex/_internal/environment.py:287` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-037: Documented extra: LiteLLMEmbedder

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/litellm.py:22
**Export:** LiteLLMEmbedder

**Issue:** `SKILL.md:110` documents `LiteLLMEmbedder`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LiteLLMEmbedder` is a documented extra, a name the source still declares at `python/cocoindex/ops/litellm.py:22` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-038: Documented extra: LlmPairResolver

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/llm_resolver.py:49
**Export:** LlmPairResolver

**Issue:** `references/ops.md:195` documents `LlmPairResolver`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LlmPairResolver` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/llm_resolver.py:49` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-040: Documented extra: MatchAllFilePathMatcher

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/file.py:215
**Export:** MatchAllFilePathMatcher

**Issue:** `references/resources.md:36` documents `MatchAllFilePathMatcher`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MatchAllFilePathMatcher` is a documented extra, a name the source still declares at `python/cocoindex/resources/file.py:215` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-041: Documented extra: MultiVectorSchema

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:49
**Export:** MultiVectorSchema

**Issue:** `references/resources.md:185` documents `MultiVectorSchema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MultiVectorSchema` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:49` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-042: Documented extra: MultiVectorSchemaProvider

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:43
**Export:** MultiVectorSchemaProvider

**Issue:** `references/connectors.md:68` documents `MultiVectorSchemaProvider`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MultiVectorSchemaProvider` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:43` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-043: Documented extra: PairDecision

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:46
**Export:** PairDecision

**Issue:** `references/ops.md:185` documents `PairDecision`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PairDecision` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:46` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-044: Documented extra: PairResolver

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:97
**Export:** PairResolver

**Issue:** `references/ops.md:188` documents `PairResolver`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PairResolver` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:97` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-045: Documented extra: PatternFilePathMatcher

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/file.py:227
**Export:** PatternFilePathMatcher

**Issue:** `SKILL.md:26` documents `PatternFilePathMatcher`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PatternFilePathMatcher` is a documented extra, a name the source still declares at `python/cocoindex/resources/file.py:227` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-046: Documented extra: PgSourceSpec

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/postgres/_source.py:54
**Export:** PgSourceSpec

**Issue:** `references/connectors.md:27` documents `PgSourceSpec`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PgSourceSpec` is a documented extra, a name the source still declares at `python/cocoindex/connectors/postgres/_source.py:54` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-047: Documented extra: PgTableSource

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/postgres/_source.py:130
**Export:** PgTableSource

**Issue:** `SKILL.md:312` documents `PgTableSource`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PgTableSource` is a documented extra, a name the source still declares at `python/cocoindex/connectors/postgres/_source.py:130` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-048: Documented extra: PgType

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/postgres/_target.py:77
**Export:** PgType

**Issue:** `references/connectors.md:20` documents `PgType`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PgType` is a documented extra, a name the source still declares at `python/cocoindex/connectors/postgres/_target.py:77` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-049: Documented extra: PointStruct

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/qdrant/_target.py:42
**Export:** PointStruct

**Issue:** `references/connectors.md:51` documents `PointStruct`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PointStruct` is a documented extra, a name the source still declares at `python/cocoindex/connectors/qdrant/_target.py:42` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-050: Documented extra: QdrantVectorDef

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/qdrant/_target.py:50
**Export:** QdrantVectorDef

**Issue:** `references/connectors.md:51` documents `QdrantVectorDef`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `QdrantVectorDef` is a documented extra, a name the source still declares at `python/cocoindex/connectors/qdrant/_target.py:50` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-051: Documented extra: QueryHandlerInfo

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/query_handler.py:21
**Export:** QueryHandlerInfo

**Issue:** `SKILL.md:214` documents `QueryHandlerInfo`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `QueryHandlerInfo` is a documented extra, a name the source still declares at `python/cocoindex/query_handler.py:21` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-052: Documented extra: QueryHandlerResultFields

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/query_handler.py:10
**Export:** QueryHandlerResultFields

**Issue:** `SKILL.md:214` documents `QueryHandlerResultFields`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `QueryHandlerResultFields` is a documented extra, a name the source still declares at `python/cocoindex/query_handler.py:10` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-053: Documented extra: QueryInfo

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/query_handler.py:30
**Export:** QueryInfo

**Issue:** `SKILL.md:216` documents `QueryInfo`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `QueryInfo` is a documented extra, a name the source still declares at `python/cocoindex/query_handler.py:30` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-054: Documented extra: QueryOutput

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/query_handler.py:43
**Export:** QueryOutput

**Issue:** `SKILL.md:217` documents `QueryOutput`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `QueryOutput` is a documented extra, a name the source still declares at `python/cocoindex/query_handler.py:43` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-055: Documented extra: RecursiveSplitter

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/text.py:120
**Export:** RecursiveSplitter

**Issue:** `SKILL.md:23` documents `RecursiveSplitter`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `python/cocoindex/ops/text.py`

**Remediation:** No change: `RecursiveSplitter` is a documented extra, a name the source still declares at `python/cocoindex/ops/text.py:120` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-056: Documented extra: RelationTarget

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/surrealdb/_target.py:1153
**Export:** RelationTarget

**Issue:** `references/connectors.md:99` documents `RelationTarget`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `RelationTarget` is a documented extra, a name the source still declares at `python/cocoindex/connectors/surrealdb/_target.py:1153` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-057: Documented extra: ResolutionEvent

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:70
**Export:** ResolutionEvent

**Issue:** `references/ops.md:187` documents `ResolutionEvent`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ResolutionEvent` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:70` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-058: Documented extra: ResolvedEntities

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:114
**Export:** ResolvedEntities

**Issue:** `references/ops.md:189` documents `ResolvedEntities`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ResolvedEntities` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:114` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-059: Documented extra: RetryConfig

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/doris/_target.py:178
**Export:** RetryConfig

**Issue:** `references/connectors.md:128` documents `RetryConfig`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `RetryConfig` is a documented extra, a name the source still declares at `python/cocoindex/connectors/doris/_target.py:178` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-060: Documented extra: RowFetcher

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/postgres/_source.py:62
**Export:** RowFetcher

**Issue:** `references/connectors.md:27` documents `RowFetcher`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `RowFetcher` is a documented extra, a name the source still declares at `python/cocoindex/connectors/postgres/_source.py:62` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-061: Documented extra: S3File

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/amazon_s3/_source.py:89
**Export:** S3File

**Issue:** `references/connectors.md:215` documents `S3File`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `S3File` is a documented extra, a name the source still declares at `python/cocoindex/connectors/amazon_s3/_source.py:89` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-062: Documented extra: S3FilePath

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/amazon_s3/_source.py:46
**Export:** S3FilePath

**Issue:** `references/connectors.md:215` documents `S3FilePath`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `S3FilePath` is a documented extra, a name the source still declares at `python/cocoindex/connectors/amazon_s3/_source.py:46` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-063: Documented extra: S3Walker

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/amazon_s3/_source.py:247
**Export:** S3Walker

**Issue:** `references/connectors.md:215` documents `S3Walker`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `S3Walker` is a documented extra, a name the source still declares at `python/cocoindex/connectors/amazon_s3/_source.py:247` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-064: Documented extra: SentenceTransformerEmbedder

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/sentence_transformers.py:25
**Export:** SentenceTransformerEmbedder

**Issue:** `SKILL.md:24` documents `SentenceTransformerEmbedder`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `SentenceTransformerEmbedder` is a documented extra, a name the source still declares at `python/cocoindex/ops/sentence_transformers.py:25` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-065: Documented extra: SeparatorSplitter

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/text.py:39
**Export:** SeparatorSplitter

**Issue:** `SKILL.md:117` documents `SeparatorSplitter`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `python/cocoindex/ops/text.py`

**Remediation:** No change: `SeparatorSplitter` is a documented extra, a name the source still declares at `python/cocoindex/ops/text.py:39` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-066: Documented extra: ServerSettings

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/setting.py:93
**Export:** ServerSettings

**Issue:** `SKILL.md:212` documents `ServerSettings`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ServerSettings` is a documented extra, a name the source still declares at `python/cocoindex/setting.py:93` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-067: Documented extra: SqliteType

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/sqlite/_target.py:154
**Export:** SqliteType

**Issue:** `references/connectors.md:112` documents `SqliteType`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `SqliteType` is a documented extra, a name the source still declares at `python/cocoindex/connectors/sqlite/_target.py:154` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-068: Documented extra: SurrealType

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/surrealdb/_target.py:171
**Export:** SurrealType

**Issue:** `references/connectors.md:99` documents `SurrealType`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `SurrealType` is a documented extra, a name the source still declares at `python/cocoindex/connectors/surrealdb/_target.py:171` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-069: Documented extra: SyncFunction

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/function.py:491
**Export:** SyncFunction

**Issue:** `SKILL.md:275` documents `SyncFunction`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `SyncFunction` is a documented extra, a name the source still declares at `python/cocoindex/_internal/function.py:491` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-072: Documented extra: TargetActionSinkFn

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/target_state.py:99
**Export:** TargetActionSinkFn

**Issue:** `references/target-state.md:36` documents `TargetActionSinkFn`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `TargetActionSinkFn` is a documented extra, a name the source still declares at `python/cocoindex/_internal/target_state.py:99` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-073: Documented extra: TextPosition

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/chunk.py:9
**Export:** TextPosition

**Issue:** `SKILL.md:348` documents `TextPosition`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `TextPosition` is a documented extra, a name the source still declares at `python/cocoindex/resources/chunk.py:9` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-074: Documented extra: UuidGenerator

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/id.py:152
**Export:** UuidGenerator

**Issue:** `SKILL.md:348` documents `UuidGenerator`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `UuidGenerator` is a documented extra, a name the source still declares at `python/cocoindex/resources/id.py:152` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-076: Documented extra: Vec0TableDef

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/sqlite/_target.py:121
**Export:** Vec0TableDef

**Issue:** `references/connectors.md:108` documents `Vec0TableDef`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Vec0TableDef` is a documented extra, a name the source still declares at `python/cocoindex/connectors/sqlite/_target.py:121` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-077: Documented extra: VectorIndexDef

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/doris/_target.py:709
**Export:** VectorIndexDef

**Issue:** `SKILL.md:326` documents `VectorIndexDef`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `VectorIndexDef` is a documented extra, a name the source still declares at `python/cocoindex/connectors/doris/_target.py:709` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-078: Documented extra: VectorSchema

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:23
**Export:** VectorSchema

**Issue:** `SKILL.md:348` documents `VectorSchema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `VectorSchema` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:23` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-079: Documented extra: VectorSchemaProvider

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:17
**Export:** VectorSchemaProvider

**Issue:** `SKILL.md:348` documents `VectorSchemaProvider`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `VectorSchemaProvider` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:17` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-080: Documented extra: build_vector_search_query

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/doris/_target.py:1317
**Export:** build_vector_search_query

**Issue:** `references/connectors.md:124` documents `build_vector_search_query`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `build_vector_search_query` is a documented extra, a name the source still declares at `python/cocoindex/connectors/doris/_target.py:1317` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-081: Documented extra: cli

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/cli.py:505
**Export:** cli

**Issue:** `SKILL.md:218` documents `cli`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `cli` is a documented extra, a name the source still declares at `python/cocoindex/cli.py:505` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-082: Documented extra: collection_target

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/qdrant/_target.py:510
**Export:** collection_target

**Issue:** `references/connectors.md:52` documents `collection_target`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `collection_target` is a documented extra, a name the source still declares at `python/cocoindex/connectors/qdrant/_target.py:510` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-085: Documented extra: create_client

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/qdrant/_target.py:294
**Export:** create_client

**Issue:** `references/connectors.md:52` documents `create_client`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `create_client` is a documented extra, a name the source still declares at `python/cocoindex/connectors/qdrant/_target.py:294` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-086: Documented extra: create_pool

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/postgres/_target.py:1367
**Export:** create_pool

**Issue:** `SKILL.md:36` documents `create_pool`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `create_pool` is a documented extra, a name the source still declares at `python/cocoindex/connectors/postgres/_target.py:1367` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-087: Documented extra: declare_collection_target

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/qdrant/_target.py:537
**Export:** declare_collection_target

**Issue:** `references/connectors.md:53` documents `declare_collection_target`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `declare_collection_target` is a documented extra, a name the source still declares at `python/cocoindex/connectors/qdrant/_target.py:537` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-088: Documented extra: declare_dir_target

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/localfs/_target.py:356
**Export:** declare_dir_target

**Issue:** `references/connectors.md:187` documents `declare_dir_target`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `declare_dir_target` is a documented extra, a name the source still declares at `python/cocoindex/connectors/localfs/_target.py:356` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-089: Documented extra: declare_file

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/localfs/_target.py:451
**Export:** declare_file

**Issue:** `references/connectors.md:187` documents `declare_file`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `declare_file` is a documented extra, a name the source still declares at `python/cocoindex/connectors/localfs/_target.py:451` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-090: Documented extra: declare_kafka_topic_target

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/kafka/_target.py:277
**Export:** declare_kafka_topic_target

**Issue:** `references/connectors.md:146` documents `declare_kafka_topic_target`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `declare_kafka_topic_target` is a documented extra, a name the source still declares at `python/cocoindex/connectors/kafka/_target.py:277` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-091: Documented extra: declare_relation_target

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/surrealdb/_target.py:1357
**Export:** declare_relation_target

**Issue:** `references/connectors.md:100` documents `declare_relation_target`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `declare_relation_target` is a documented extra, a name the source still declares at `python/cocoindex/connectors/surrealdb/_target.py:1357` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-093: Documented extra: detect_code_language

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/text.py:19
**Export:** detect_code_language

**Issue:** `SKILL.md:117` documents `detect_code_language`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `python/cocoindex/ops/text.py`

**Remediation:** No change: `detect_code_language` is a documented extra, a name the source still declares at `python/cocoindex/ops/text.py:19` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-094: Documented extra: dir_target

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/localfs/_target.py:391
**Export:** dir_target

**Issue:** `references/connectors.md:188` documents `dir_target`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `dir_target` is a documented extra, a name the source still declares at `python/cocoindex/connectors/localfs/_target.py:391` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-095: Documented extra: generate_id

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/id.py:31
**Export:** generate_id

**Issue:** `SKILL.md:146` documents `generate_id`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `generate_id` is a documented extra, a name the source still declares at `python/cocoindex/resources/id.py:31` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-096: Documented extra: generate_uuid

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/id.py:61
**Export:** generate_uuid

**Issue:** `SKILL.md:146` documents `generate_uuid`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `generate_uuid` is a documented extra, a name the source still declares at `python/cocoindex/resources/id.py:61` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-097: Documented extra: get_default_db_path

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/setting.py:12
**Export:** get_default_db_path

**Issue:** `references/component-api.md:82` documents `get_default_db_path`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_default_db_path` is a documented extra, a name the source still declares at `python/cocoindex/_internal/setting.py:12` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-098: Documented extra: get_multi_vector_schema

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:58
**Export:** get_multi_vector_schema

**Issue:** `SKILL.md:168` documents `get_multi_vector_schema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_multi_vector_schema` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:58` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-099: Documented extra: get_object

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/amazon_s3/_source.py:159
**Export:** get_object

**Issue:** `references/connectors.md:215` documents `get_object`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_object` is a documented extra, a name the source still declares at `python/cocoindex/connectors/amazon_s3/_source.py:159` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-100: Documented extra: get_vector_schema

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:33
**Export:** get_vector_schema

**Issue:** `SKILL.md:168` documents `get_vector_schema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_vector_schema` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:33` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-101: Documented extra: is_live_component_class

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/live_component.py:35
**Export:** is_live_component_class

**Issue:** `SKILL.md:167` documents `is_live_component_class`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `is_live_component_class` is a documented extra, a name the source still declares at `python/cocoindex/_internal/live_component.py:35` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-102: Documented extra: kafka_topic_target

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/kafka/_target.py:250
**Export:** kafka_topic_target

**Issue:** `references/connectors.md:146` documents `kafka_topic_target`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `kafka_topic_target` is a documented extra, a name the source still declares at `python/cocoindex/connectors/kafka/_target.py:250` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-103: Documented extra: list_files

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/google_drive/_source.py:199
**Export:** list_files

**Issue:** `references/connectors.md:227` documents `list_files`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `list_files` is a documented extra, a name the source still declares at `python/cocoindex/connectors/google_drive/_source.py:199` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-104: Documented extra: list_objects

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/amazon_s3/_source.py:351
**Export:** list_objects

**Issue:** `references/connectors.md:215` documents `list_objects`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `list_objects` is a documented extra, a name the source still declares at `python/cocoindex/connectors/amazon_s3/_source.py:351` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-105: Documented extra: litellm

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/litellm.py:1
**Export:** litellm

**Issue:** `SKILL.md:110` documents `litellm`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `litellm` is a documented extra, a name the source still declares at `python/cocoindex/ops/litellm.py:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-106: Documented extra: managed_connection

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/sqlite/_target.py:1282
**Export:** managed_connection

**Issue:** `references/connectors.md:113` documents `managed_connection`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `managed_connection` is a documented extra, a name the source still declares at `python/cocoindex/connectors/sqlite/_target.py:1282` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-107: Documented extra: mount_collection_target

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/qdrant/_target.py:561
**Export:** mount_collection_target

**Issue:** `SKILL.md:104` documents `mount_collection_target`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `mount_collection_target` is a documented extra, a name the source still declares at `python/cocoindex/connectors/qdrant/_target.py:561` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-108: Documented extra: mount_dir_target

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/localfs/_target.py:424
**Export:** mount_dir_target

**Issue:** `references/connectors.md:188` documents `mount_dir_target`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `mount_dir_target` is a documented extra, a name the source still declares at `python/cocoindex/connectors/localfs/_target.py:424` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-109: Documented extra: mount_kafka_topic_target

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/kafka/_target.py:301
**Export:** mount_kafka_topic_target

**Issue:** `references/connectors.md:146` documents `mount_kafka_topic_target`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `mount_kafka_topic_target` is a documented extra, a name the source still declares at `python/cocoindex/connectors/kafka/_target.py:301` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-110: Documented extra: mount_relation_target

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/surrealdb/_target.py:1382
**Export:** mount_relation_target

**Issue:** `references/connectors.md:101` documents `mount_relation_target`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `mount_relation_target` is a documented extra, a name the source still declares at `python/cocoindex/connectors/surrealdb/_target.py:1382` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-112: Documented extra: read

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/amazon_s3/_source.py:221
**Export:** read

**Issue:** `SKILL.md:335` documents `read`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `read` is a documented extra, a name the source still declares at `python/cocoindex/connectors/amazon_s3/_source.py:221` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-113: Documented extra: relation_target

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/surrealdb/_target.py:1329
**Export:** relation_target

**Issue:** `references/connectors.md:102` documents `relation_target`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `relation_target` is a documented extra, a name the source still declares at `python/cocoindex/connectors/surrealdb/_target.py:1329` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-114: Documented extra: resolve_entities

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:186
**Export:** resolve_entities

**Issue:** `references/ops.md:191` documents `resolve_entities`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `resolve_entities` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:186` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-116: Documented extra: topic_as_map

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/kafka/_source.py:361
**Export:** topic_as_map

**Issue:** `SKILL.md:312` documents `topic_as_map`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `topic_as_map` is a documented extra, a name the source still declares at `python/cocoindex/connectors/kafka/_source.py:361` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-117: Documented extra: walk_dir

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/localfs/_source.py:234
**Export:** walk_dir

**Issue:** `SKILL.md:75` documents `walk_dir`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `walk_dir` is a documented extra, a name the source still declares at `python/cocoindex/connectors/localfs/_source.py:234` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-120: Discovery testing not performed: subagents unavailable, routing test requires isolated context

**Severity:** Info
**Category:** Discovery (discovery)
**Source:** SKILL.md:3

**Issue:** The run could not spawn isolated subagents, so the three realistic-prompt routing checks against the 4-skill catalog (oms-cocoindex, oms-cognee, oms-storybook-react-vite, oms-uitripled) did not run; the main thread knows the skill under test and may not stand in for them.

**Remediation:** Re-run test-skill in an environment that can spawn subagents so the discovery routing test runs against the SKILL.md frontmatter description (SKILL.md:3); no change to the skill is implied.

### Discovery Quality

**Discovery Test:** skipped: subagents unavailable, routing test requires isolated context

discovery: skipped, subagents unavailable, routing test requires isolated context (catalog of 4 skills: oms-cocoindex, oms-cognee, oms-storybook-react-vite, oms-uitripled). The skip is recorded as GAP-120 and is not counted PASS or FAIL. No description optimization hints: Tessl Review did not run and skill-check flagged no description issue.

