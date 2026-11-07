---
workflowType: 'test-skill'
skillName: 'oms-cocoindex'
skillDir: 'skills/oms-cocoindex/1.0.0/oms-cocoindex'
runId: '20261107T112453Z-e8d82695'
testMode: 'naive'
forgeTier: 'Deep'
hardGate: 'passed'
testResult: 'pass'
score: '99.37%'
threshold: '80%'
thresholdSource: 'workflow default (80%)'
analysisConfidence: 'full'
toolingStatus: 'ok'
workspaceDrift: 'ok'
health_check_dispatched: true
testDate: '2026-11-07T11:24:53Z'
stepsCompleted: ['init', 'detect-mode', 'coverage-check', 'coherence-check', 'external-validators', 'hard-gate', 'score', 'report']
nextWorkflow: 'export-skill'
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

**Mode Rationale:** metadata.json records `skill_type: "single"`, an individual library skill, so the run takes Naive Mode: API-surface coverage, with a structural coherence check that is not scored as a category.

**Analysis Plan:**
- Coverage Check: Deep tier, full source access to the pinned cocoindex v1.0.0 clone (5fe4f37); every public export of the source is matched against SKILL.md and its references, and every documented signature is compared with its source declaration (AST-backed).
- Coherence Check: structural only (Naive Mode): references named in SKILL.md resolve to files in the package, and the documented examples and types are consistent with the documented API.

## Coverage Analysis

**Tier:** Deep
**Source Access:** full
**Source Path:** /home/armel/.skf/workspace/repos/github.com/cocoindex-io/cocoindex
**Workspace Layout:** single package
**Denominator:** barrel (standard-barrel clause: the root barrel `python/cocoindex/__init__.py`, the `all` set, 72 exports)

**Files Analyzed:** 30

### Export Coverage

| Export | Type | Documented | Signature | Source Location | Status |
|--------|------|------------|-----------|-----------------|--------|
| `App` | - | yes | yes | python/cocoindex/_internal/app.py:208 | PASS |
| `AppConfig` | - | yes | yes | python/cocoindex/_internal/app.py:202 | PASS |
| `AsyncCallable` | - | yes | - | - | WARN |
| `AsyncFunction` | - | yes | - | - | WARN |
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
| `ExceptionContext` | - | no | - | python/cocoindex/_internal/component_ctx.py:43 | WARN |
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
| `Symbol` | - | yes | - | python/cocoindex/_internal/stable_path.py:7 | PASS |
| `SyncFunction` | - | yes | - | - | WARN |
| `TableSchema` | class | yes | - | python/cocoindex/connectors/doris/_target.py:339 | WARN |
| `TableTarget` | class | yes | - | python/cocoindex/connectors/lancedb/_target.py:732 | WARN |
| `TargetActionSink` | - | yes | - | python/cocoindex/_internal/target_state.py:143 | PASS |
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
- **Documented:** 71 (98.61%)
- **Missing Documentation:** 1
- **Signature Mismatches:** 0
- **Stale Documentation:** 113, documented extras included
- **Nested Entry Points:** `python/cocoindex/connectors/amazon_s3/__init__.py` inside `python/cocoindex/__init__.py`: `S3File`, `S3FilePath`, `S3Walker`, `get_object`, `list_objects`, `read`; `python/cocoindex/connectors/doris/__init__.py` inside `python/cocoindex/__init__.py`: `ColumnDef`, `DorisConnectionConfig`, `DorisTableTarget`, `DorisType`, `InvertedIndexDef`, `ManagedConnection`, `RetryConfig`, `TableSchema`, `ValueEncoder`, `VectorIndexDef`, `build_vector_search_query`, `connect`, `connect_async`, `declare_table_target`, `mount_table_target`, `table_target`; `python/cocoindex/connectors/google_drive/__init__.py` inside `python/cocoindex/__init__.py`: `DriveFile`, `DriveFileInfo`, `GoogleDriveSource`, `GoogleDriveSourceSpec`, `list_files`; `python/cocoindex/connectors/kafka/__init__.py` inside `python/cocoindex/__init__.py`: `DeletionValueFn`, `IsDeleteFn`, `KafkaTopicTarget`, `declare_kafka_topic_target`, `kafka_topic_target`, `mount_kafka_topic_target`, `topic_as_map`; `python/cocoindex/connectors/lancedb/__init__.py` inside `python/cocoindex/__init__.py`: `ColumnDef`, `LanceAsyncConnection`, `LanceType`, `TableSchema`, `TableTarget`, `ValueEncoder`, `connect`, `connect_async`, `declare_table_target`, `mount_table_target`, `table_target`; `python/cocoindex/connectors/localfs/__init__.py` inside `python/cocoindex/__init__.py`: `DirTarget`, `DirWalker`, `File`, `FilePath`, `declare_dir_target`, `declare_file`, `dir_target`, `mount_dir_target`, `walk_dir`; `python/cocoindex/connectors/postgres/__init__.py` inside `python/cocoindex/__init__.py`: `ColumnDef`, `PgSourceSpec`, `PgTableSource`, `PgType`, `RowFetcher`, `TableSchema`, `TableTarget`, `ValueEncoder`, `create_pool`, `declare_table_target`, `mount_table_target`, `table_target`; `python/cocoindex/connectors/qdrant/__init__.py` inside `python/cocoindex/__init__.py`: `CollectionSchema`, `CollectionTarget`, `PointStruct`, `QdrantVectorDef`, `collection_target`, `create_client`, `declare_collection_target`, `mount_collection_target`; `python/cocoindex/connectors/sqlite/__init__.py` inside `python/cocoindex/__init__.py`: `ColumnDef`, `ManagedConnection`, `SqliteType`, `TableSchema`, `TableTarget`, `ValueEncoder`, `Vec0TableDef`, `connect`, `declare_table_target`, `managed_connection`, `mount_table_target`, `table_target`; `python/cocoindex/connectors/surrealdb/__init__.py` inside `python/cocoindex/__init__.py`: `ColumnDef`, `ConnectionFactory`, `RelationTarget`, `SurrealType`, `TableSchema`, `TableTarget`, `ValueEncoder`, `declare_relation_target`, `declare_table_target`, `mount_relation_target`, `mount_table_target`, `relation_target`, `table_target`
- **Restored by the Stale-Scope Guard:** `App` (python/cocoindex/_internal/app.py:208), `AppConfig` (python/cocoindex/_internal/app.py:202), `ChildTargetDef` (python/cocoindex/_internal/target_state.py:95), `ComponentContext` (python/cocoindex/_internal/component_ctx.py:55), `ComponentStats` (python/cocoindex/_internal/update_stats.py:14), `ComponentSubpath` (python/cocoindex/_internal/component_ctx.py:142), `ContextKey` (python/cocoindex/_internal/context_keys.py:99), `ContextProvider` (python/cocoindex/_internal/context_keys.py:124), `DropHandle` (python/cocoindex/_internal/app.py:143), `Environment` (python/cocoindex/_internal/environment.py:183), `EnvironmentBuilder` (python/cocoindex/_internal/environment.py:87), `ExceptionContext` (python/cocoindex/_internal/component_ctx.py:43), `ExceptionHandler` (python/cocoindex/_internal/component_ctx.py:25), `GPU` (python/cocoindex/_internal/runner.py:282), `LifespanFn` (python/cocoindex/_internal/environment.py:118), `LiveComponent` (python/cocoindex/_internal/live_component.py:28), `LiveComponentOperator` (python/cocoindex/_internal/live_component.py:46), `LiveMapFeed` (python/cocoindex/_internal/live_component.py:108), `LiveMapSubscriber` (python/cocoindex/_internal/live_component.py:130), `LiveMapView` (python/cocoindex/_internal/live_component.py:119), `LogicTracking` (python/cocoindex/_internal/function.py:65), `MaybePendingS` (python/cocoindex/_internal/pending_marker.py:115), `MemoStateOutcome` (python/cocoindex/_internal/typing.py:67), `NON_EXISTENCE` (python/cocoindex/_internal/typing.py:60), `NonExistenceType` (python/cocoindex/_internal/typing.py:47), `NotMemoKeyable` (python/cocoindex/_internal/memo_fingerprint.py:136), `PendingS` (python/cocoindex/_internal/pending_marker.py:74), `PendingTargetStateProvider` (python/cocoindex/_internal/target_state.py:243), `ROOT_PATH` (python/cocoindex/_internal/stable_path.py:59), `ResolvedS` (python/cocoindex/_internal/pending_marker.py:89), `ResolvesTo` (python/cocoindex/_internal/pending_marker.py:118), `Runner` (python/cocoindex/_internal/runner.py:34), `Settings` (python/cocoindex/_internal/setting.py:56), `StableKey` (python/cocoindex/_internal/stable_path.py:9), `StablePath` (python/cocoindex/_internal/stable_path.py:16), `Symbol` (python/cocoindex/_internal/stable_path.py:7), `TargetActionSink` (python/cocoindex/_internal/target_state.py:143), `TargetHandler` (python/cocoindex/_internal/target_state.py:197), `TargetReconcileOutput` (python/cocoindex/_internal/target_state.py:188), `TargetState` (python/cocoindex/_internal/target_state.py:248), `TargetStateProvider` (python/cocoindex/_internal/target_state.py:208), `UpdateHandle` (python/cocoindex/_internal/app.py:49), `UpdateSnapshot` (python/cocoindex/_internal/update_stats.py:59), `UpdateStats` (python/cocoindex/_internal/update_stats.py:39), `UpdateStatus` (python/cocoindex/_internal/update_stats.py:9), `component_subpath` (python/cocoindex/_internal/component_ctx.py:198), `declare_target_state` (python/cocoindex/_internal/target_state.py:265), `declare_target_state_with_child` (python/cocoindex/_internal/target_state.py:282), `exception_handler` (python/cocoindex/_internal/component_ctx.py:331), `fn` (python/cocoindex/_internal/function.py:1811), `get_component_context` (python/cocoindex/_internal/component_ctx.py:305), `is_non_existence` (python/cocoindex/_internal/typing.py:63), `lifespan` (python/cocoindex/_internal/environment.py:449), `memo_fingerprint` (python/cocoindex/_internal/memo_fingerprint.py:361), `register_memo_key_function` (python/cocoindex/_internal/memo_fingerprint.py:155), `register_root_target_states_provider` (python/cocoindex/_internal/target_state.py:305), `serialize_by_pickle` (python/cocoindex/_internal/serde.py:151), `show_progress` (python/cocoindex/_internal/app.py:194), `unpickle_safe` (python/cocoindex/_internal/serde.py:128), `use_context` (python/cocoindex/_internal/component_ctx.py:273)

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 98.61% |
| Signature Accuracy | 100% |
| Type Coverage | 100% |

### Coverage Notes

- **Reader and judges.** This session had no subagent tool, so the workflow's own no-subagent provisions applied: the main thread built the §1 inventory from SKILL.md and all seven `references/*.md` files (SKILL.md has no `## Full` headings) under `references/inventory-contract.md`, and judged all 45 planned signature checks (16 source files, one results file `signatures-1.txt`) under `references/signature-comparison-rules.md`, loaded once and applied unchanged to every file. No leniency rule was added. The §1b split-body cross-check compared every export documented in SKILL.md and a reference file under the same rules and found no mismatch.
- **Extraction.** Recipe runner over 73 in-scope Python files, status `ok`, no fallback, nothing read by eye, nothing unread, no unresolved star re-export. `extractionGaps` (on the surface, no recipe found): `DeletionValueFn` (python/cocoindex/connectors/kafka/_target.py:206), `IsDeleteFn` (python/cocoindex/connectors/kafka/_source.py:30), `LanceAsyncConnection` (no file), `PointStruct` (python/cocoindex/connectors/qdrant/_target.py:42), `ValueEncoder` (python/cocoindex/connectors/doris/_target.py:79). None carries a documented signature, so none entered the signature plan.
- **Guards.** Deflation not applicable (no stored `effective_denominator`); inflation did not fire (79 scope.include names against 154 provenance entries); the stale-scope guard fired: `scope.include` globs `docs/docs/**/*.md` and `docs/docs/**/*.mdx` match no file, and 60 root exports defined in `_internal/` files no include glob covers are restored to the `all` set (Medium `brief-scope-stale`).
- **Numerator check:** skipped (the declared count is not the inflation signature).
- **Metadata count cross-check:** one Medium finding, `stats.exports_public_api` 140 against `exports[]` 118 (16% drift); Cluster B agrees (154 documented, 154 provenance entries, 154 confidence total).
- **Provenance line check (§4c):** 118 exports and 154 entries checked, no stale line (12 line checks skipped by the helper's own rules; its 36 orphaned entries are not reported by this section).
- **Deep-tier observations:** the documented forms of the names outside the signature universe (ops, resources, `cocoindex.setting`, `query_handler`, `cli`, live components, entity resolution, connector methods named in the skill) were read against their declarations at the pinned commit; no documentation error was found, so no `Not checked by script` record was written.
- **Borderline call 1 (signature rules): `fn`.** Documented forms: `@coco.fn(memo=True)` (SKILL.md:60, SKILL.md:180), `@coco.fn(version=N, logic_tracking="full"|"self"|None, deps=...)` (SKILL.md:180), `@coco.fn(version=2)`, `@coco.fn(logic_tracking="full"|"self"|None)`, `@coco.fn(deps={"prompt": SYSTEM_PROMPT, "model": MODEL_NAME})` (references/component-api.md:159-162) and `coco.fn(logic_tracking=tracking)` (references/component-api.md:199). Source declaration: `fn = _FunctionDecorator()` (python/cocoindex/_internal/function.py:1811), whose callable parameters are `_FunctionDecorator.__call__`'s overloads (function.py:1584-1638: keyword-only `memo`, `batching`, `max_batch_size`, `runner`, `version`, `logic_tracking`, `deps`). The sentence that leaves it open: signature-comparison-rules.md:27, "The source's declaration decides: the documented form is compared with the parameters, the optionality and the annotations the signature declares": the declaration at 1811 is an instance assignment with no signature, and the rules provide only for a const annotated with a function type (signature-comparison-rules.md:29). Counted as: **match**, reading the instance's call through its class's `__call__`, where every keyword the forms pass exists. Read as declaring no parameters, each call form would be a mismatch.
- **Borderline call 2 (inventory contract): `ExceptionContext`.** The skill names it only inside the documented type of `ExceptionHandler`, "The handler signature is `Callable[[BaseException, ExceptionContext], None | Awaitable[None]]`" (references/component-api.md:324); it gives it no form, field or description. Source: `@dataclass(frozen=True, slots=True) class ExceptionContext` (python/cocoindex/_internal/component_ctx.py:43), on the root barrel. The sentence that leaves it open: references/inventory-contract.md:3, the reader writes "every export the skill documents", which does not say whether a name that appears only as a type argument of another export's documented type is documented. Counted as: **not documented** (the one Medium `missing-export`, Export Coverage 71/72). Counted as documented, Export Coverage would be 72/72.
- **Borderline call 3 (migration rules, coherence §2b): `## Migration from v0.3.37`.** `t2_future_count: 0` (forge-data/oms-cocoindex/1.0.0/evidence-report.md:11). SKILL.md:303 opens `## Migration from v0.3.37`, a table of v0.3.37 names and their v1.0.0 replacements, historical migration content. The sentence that leaves it open: references/migration-section-rules.md:50, "Check whether SKILL.md contains a 'Migration & Deprecation Warnings' section (Section 4b)", which does not say whether a migration section under another heading is Section 4b. Counted as: **Section 4b absent** (no case applies, no gap). Read as present, Case 2 would apply: one Info `migration-section` gap, which changes neither the score nor the gate.

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)

### Structural Findings

| # | Type | Severity | Detail | Line |
|---|------|----------|--------|------|
| - | none | - | §2.1 required sections: `usage` served by `Quick Start`, `api_surface` by `Key API Summary`, `description` by the frontmatter description; §2.2 fences balanced (8 fences); §2.3 no bare opening fence; §2.4 every function and method export of the inventory is used in a usage-family section or reference file (63 counted, 0 unused); §2.5 every export the skill describes as async is awaited in its examples and none it describes as sync is directly awaited (43 called exports read); §2.6 no table row drift; §2.7 no `scripts/` or `assets/` folder | - |

**Structural Issues:** 0

**Migration/Deprecation check (§2b):** gate met (Deep tier, evidence report bound); `t2_future_count: 0` in `forge-data/oms-cocoindex/1.0.0/evidence-report.md`; SKILL.md has no `Migration & Deprecation Warnings` section (its `## Migration from v0.3.37` section, SKILL.md:303, is historical migration guidance under its own heading), so no case applies and no gap is recorded (Coverage Notes, borderline call 3).

### Reference Consistency (split-body)

| # | Reference File | Export | Issue | Other Side | Reference Line | Contradicted Side |
|---|---------------|--------|-------|------------|---------------|-------------------|
| - | - | - | no mismatch | - | - | - |

**Exports Cross-Checked:** 69
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
| Export Coverage | 98.61% | 45% | 44.37% |
| Signature Accuracy | 100% | 25% | 25% |
| Type Coverage | 100% | 20% | 20% |
| Coherence | not scored (naive mode) | 0% | 0% |
| External Validation | 100% | 10% | 10% |
| **Total** | | **100%** | **99.37%** |

### Result

**Score:** 99.37%
**Threshold:** 80%
**Result:** **PASS**

**Threshold Source:** workflow default (80%)
**Weight Distribution:** naive (redistributed)
**Tier Adjustment:** none
**External Validators:** skill-check only
**Analysis Confidence:** full
**Tooling Status:** ok

## Gap Report

**Total Gaps:** 117
**Blocking (Critical + High):** 0
**Non-blocking (Medium + Low + Info):** 117

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|------------------|
| Critical | 0 | None |
| High | 0 | None |
| Medium | 14 | Add type definitions, interface docs or the missing section |
| Low | 0 | None |
| Info | 103 | Optional improvements, no action required |
| **Total** | **117** | |

### GAP-001: Missing export: ExceptionContext

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** python/cocoindex/_internal/component_ctx.py:43
**Export:** ExceptionContext

**Issue:** `ExceptionContext` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `ExceptionContext` in SKILL.md: read its definition at `python/cocoindex/_internal/component_ctx.py:43` and add its signature, its purpose and a usage example.

### GAP-008: Stale documentation: ColumnDef

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/connectors.md:9
**Export:** ColumnDef

**Issue:** `references/connectors.md:9` documents `ColumnDef`, which the enumerated source API surface lacks

**Remediation:** Check `ColumnDef` against the source and update or remove its documentation at references/connectors.md:9: the enumerated source surface does not export it.

### GAP-024: Stale documentation: FilePath

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/resources.md:113
**Export:** FilePath

**Issue:** `references/resources.md:113` documents `FilePath`, which the enumerated source API surface lacks

**Remediation:** Check `FilePath` against the source and update or remove its documentation at references/resources.md:113: the enumerated source surface does not export it.

### GAP-038: Stale documentation: ManagedConnection

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md
**Export:** ManagedConnection

**Issue:** the skill documents `ManagedConnection`, which the enumerated source API surface lacks

**Remediation:** Check `ManagedConnection` against the source and update or remove its documentation at SKILL.md: the enumerated source surface does not export it.

### GAP-069: Stale documentation: TableSchema

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/connectors.md:9
**Export:** TableSchema

**Issue:** `references/connectors.md:9` documents `TableSchema`, which the enumerated source API surface lacks

**Remediation:** Check `TableSchema` against the source and update or remove its documentation at references/connectors.md:9: the enumerated source surface does not export it.

### GAP-070: Stale documentation: TableTarget

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/connectors.md:241
**Export:** TableTarget

**Issue:** `references/connectors.md:241` documents `TableTarget`, which the enumerated source API surface lacks

**Remediation:** Check `TableTarget` against the source and update or remove its documentation at references/connectors.md:241: the enumerated source surface does not export it.

### GAP-073: Stale documentation: ValueEncoder

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/connectors.md:9
**Export:** ValueEncoder

**Issue:** `references/connectors.md:9` documents `ValueEncoder`, which the enumerated source API surface lacks

**Remediation:** Check `ValueEncoder` against the source and update or remove its documentation at references/connectors.md:9: the enumerated source surface does not export it.

### GAP-081: Stale documentation: connect

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md
**Export:** connect

**Issue:** the skill documents `connect`, which the enumerated source API surface lacks

**Remediation:** Check `connect` against the source and update or remove its documentation at SKILL.md: the enumerated source surface does not export it.

### GAP-082: Stale documentation: connect_async

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md
**Export:** connect_async

**Issue:** the skill documents `connect_async`, which the enumerated source API surface lacks

**Remediation:** Check `connect_async` against the source and update or remove its documentation at SKILL.md: the enumerated source surface does not export it.

### GAP-090: Stale documentation: declare_table_target

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md
**Export:** declare_table_target

**Issue:** the skill documents `declare_table_target`, which the enumerated source API surface lacks

**Remediation:** Check `declare_table_target` against the source and update or remove its documentation at SKILL.md: the enumerated source surface does not export it.

### GAP-108: Stale documentation: mount_table_target

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/target-state.md:163
**Export:** mount_table_target

**Issue:** `references/target-state.md:163` documents `mount_table_target`, which the enumerated source API surface lacks

**Remediation:** Check `mount_table_target` against the source and update or remove its documentation at references/target-state.md:163: the enumerated source surface does not export it.

### GAP-112: Stale documentation: table_target

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md
**Export:** table_target

**Issue:** the skill documents `table_target`, which the enumerated source API surface lacks

**Remediation:** Check `table_target` against the source and update or remove its documentation at SKILL.md: the enumerated source surface does not export it.

### GAP-115: stale brief scope: scope.include globs match no source file

**Severity:** Medium
**Category:** Coverage (brief-scope-stale)
**Source:** forge-data/oms-cocoindex/skill-brief.yaml

**Issue:** the `scope.include` globs `docs/docs/**/*.md`, `docs/docs/**/*.mdx` match no file in the source tested; the `all` set restores 60 root exports, defined in files no include glob covers: `App` in `python/cocoindex/_internal/app.py`, `AppConfig` in `python/cocoindex/_internal/app.py`, `ChildTargetDef` in `python/cocoindex/_internal/target_state.py`, `ComponentContext` in `python/cocoindex/_internal/component_ctx.py`, `ComponentStats` in `python/cocoindex/_internal/update_stats.py`, `ComponentSubpath` in `python/cocoindex/_internal/component_ctx.py`, `ContextKey` in `python/cocoindex/_internal/context_keys.py`, `ContextProvider` in `python/cocoindex/_internal/context_keys.py`, `DropHandle` in `python/cocoindex/_internal/app.py`, `Environment` in `python/cocoindex/_internal/environment.py`, `EnvironmentBuilder` in `python/cocoindex/_internal/environment.py`, `ExceptionContext` in `python/cocoindex/_internal/component_ctx.py`, `ExceptionHandler` in `python/cocoindex/_internal/component_ctx.py`, `GPU` in `python/cocoindex/_internal/runner.py`, `LifespanFn` in `python/cocoindex/_internal/environment.py`, `LiveComponent` in `python/cocoindex/_internal/live_component.py`, `LiveComponentOperator` in `python/cocoindex/_internal/live_component.py`, `LiveMapFeed` in `python/cocoindex/_internal/live_component.py`, `LiveMapSubscriber` in `python/cocoindex/_internal/live_component.py`, `LiveMapView` in `python/cocoindex/_internal/live_component.py`, `LogicTracking` in `python/cocoindex/_internal/function.py`, `MaybePendingS` in `python/cocoindex/_internal/pending_marker.py`, `MemoStateOutcome` in `python/cocoindex/_internal/typing.py`, `NON_EXISTENCE` in `python/cocoindex/_internal/typing.py`, `NonExistenceType` in `python/cocoindex/_internal/typing.py`, `NotMemoKeyable` in `python/cocoindex/_internal/memo_fingerprint.py`, `PendingS` in `python/cocoindex/_internal/pending_marker.py`, `PendingTargetStateProvider` in `python/cocoindex/_internal/target_state.py`, `ROOT_PATH` in `python/cocoindex/_internal/stable_path.py`, `ResolvedS` in `python/cocoindex/_internal/pending_marker.py`, `ResolvesTo` in `python/cocoindex/_internal/pending_marker.py`, `Runner` in `python/cocoindex/_internal/runner.py`, `Settings` in `python/cocoindex/_internal/setting.py`, `StableKey` in `python/cocoindex/_internal/stable_path.py`, `StablePath` in `python/cocoindex/_internal/stable_path.py`, `Symbol` in `python/cocoindex/_internal/stable_path.py`, `TargetActionSink` in `python/cocoindex/_internal/target_state.py`, `TargetHandler` in `python/cocoindex/_internal/target_state.py`, `TargetReconcileOutput` in `python/cocoindex/_internal/target_state.py`, `TargetState` in `python/cocoindex/_internal/target_state.py`, `TargetStateProvider` in `python/cocoindex/_internal/target_state.py`, `UpdateHandle` in `python/cocoindex/_internal/app.py`, `UpdateSnapshot` in `python/cocoindex/_internal/update_stats.py`, `UpdateStats` in `python/cocoindex/_internal/update_stats.py`, `UpdateStatus` in `python/cocoindex/_internal/update_stats.py`, `component_subpath` in `python/cocoindex/_internal/component_ctx.py`, `declare_target_state` in `python/cocoindex/_internal/target_state.py`, `declare_target_state_with_child` in `python/cocoindex/_internal/target_state.py`, `exception_handler` in `python/cocoindex/_internal/component_ctx.py`, `fn` in `python/cocoindex/_internal/function.py`, `get_component_context` in `python/cocoindex/_internal/component_ctx.py`, `is_non_existence` in `python/cocoindex/_internal/typing.py`, `lifespan` in `python/cocoindex/_internal/environment.py`, `memo_fingerprint` in `python/cocoindex/_internal/memo_fingerprint.py`, `register_memo_key_function` in `python/cocoindex/_internal/memo_fingerprint.py`, `register_root_target_states_provider` in `python/cocoindex/_internal/target_state.py`, `serialize_by_pickle` in `python/cocoindex/_internal/serde.py`, `show_progress` in `python/cocoindex/_internal/app.py`, `unpickle_safe` in `python/cocoindex/_internal/serde.py`, `use_context` in `python/cocoindex/_internal/component_ctx.py`

**Remediation:** Edit `scope.include` in `forge-data/oms-cocoindex/skill-brief.yaml` by hand so each glob matches the files it meant in this version of the source (update-skill does not rewrite an include glob), and add to `scope.exclude` any restored file the brief meant to leave out.

### GAP-116: metadata drift — barrel export counts diverge

**Severity:** Medium
**Category:** Coverage (metadata-drift)
**Source:** skills/oms-cocoindex/1.0.0/oms-cocoindex/metadata.json

**Issue:** stats.exports_public_api=140, exports[].length=118 → 16% drift

**Remediation:** Re-run Create Skill, which rebuilds `exports[]` and `stats.exports_public_api` in `skills/oms-cocoindex/1.0.0/oms-cocoindex/metadata.json` from the source. Update Skill does not repair this drift: each time it writes the skill it recounts `stats.exports_public_api` from the source and keeps `exports[]`, adding or dropping only the names its provenance map changes, so a metadata patch does not hold.

### GAP-002: Documented extra: AsyncCallable

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/function.py:62
**Export:** AsyncCallable

**Issue:** the skill documents `AsyncCallable`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `AsyncCallable` is a documented extra, a name the source still declares at `python/cocoindex/_internal/function.py:62` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-003: Documented extra: AsyncFunction

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/function.py:903
**Export:** AsyncFunction

**Issue:** `SKILL.md:275` documents `AsyncFunction`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `AsyncFunction` is a documented extra, a name the source still declares at `python/cocoindex/_internal/function.py:903` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

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

**Issue:** `references/resources.md:21` documents `Chunk`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `python/cocoindex/resources/chunk.py`

**Remediation:** No change: `Chunk` is a documented extra, a name the source still declares at `python/cocoindex/resources/chunk.py:26` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-006: Documented extra: CollectionSchema

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/qdrant/_target.py:108
**Export:** CollectionSchema

**Issue:** the skill documents `CollectionSchema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CollectionSchema` is a documented extra, a name the source still declares at `python/cocoindex/connectors/qdrant/_target.py:108` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-007: Documented extra: CollectionTarget

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/qdrant/_target.py:453
**Export:** CollectionTarget

**Issue:** the skill documents `CollectionTarget`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CollectionTarget` is a documented extra, a name the source still declares at `python/cocoindex/connectors/qdrant/_target.py:453` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-009: Documented extra: ConnectionFactory

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/surrealdb/_target.py:105
**Export:** ConnectionFactory

**Issue:** the skill documents `ConnectionFactory`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ConnectionFactory` is a documented extra, a name the source still declares at `python/cocoindex/connectors/surrealdb/_target.py:105` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-010: Documented extra: CustomLanguageConfig

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/text.py:87
**Export:** CustomLanguageConfig

**Issue:** `references/ops.md:90` documents `CustomLanguageConfig`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `python/cocoindex/ops/text.py`

**Remediation:** No change: `CustomLanguageConfig` is a documented extra, a name the source still declares at `python/cocoindex/ops/text.py:87` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-011: Documented extra: DeletionValueFn

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/kafka/_target.py:206
**Export:** DeletionValueFn

**Issue:** the skill documents `DeletionValueFn`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `DeletionValueFn` is a documented extra, a name the source still declares at `python/cocoindex/connectors/kafka/_target.py:206` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-012: Documented extra: DirTarget

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/localfs/_target.py:282
**Export:** DirTarget

**Issue:** the skill documents `DirTarget`, which the enumerated source API surface lacks and the source still declares

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

**Issue:** the skill documents `DorisConnectionConfig`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `DorisConnectionConfig` is a documented extra, a name the source still declares at `python/cocoindex/connectors/doris/_target.py:434` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-015: Documented extra: DorisTableTarget

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/doris/_target.py:1250
**Export:** DorisTableTarget

**Issue:** the skill documents `DorisTableTarget`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `DorisTableTarget` is a documented extra, a name the source still declares at `python/cocoindex/connectors/doris/_target.py:1250` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-016: Documented extra: DorisType

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/doris/_target.py:282
**Export:** DorisType

**Issue:** the skill documents `DorisType`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `DorisType` is a documented extra, a name the source still declares at `python/cocoindex/connectors/doris/_target.py:282` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-017: Documented extra: DriveFile

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/google_drive/_source.py:83
**Export:** DriveFile

**Issue:** the skill documents `DriveFile`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `DriveFile` is a documented extra, a name the source still declares at `python/cocoindex/connectors/google_drive/_source.py:83` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-018: Documented extra: DriveFileInfo

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/google_drive/_source.py:75
**Export:** DriveFileInfo

**Issue:** the skill documents `DriveFileInfo`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `DriveFileInfo` is a documented extra, a name the source still declares at `python/cocoindex/connectors/google_drive/_source.py:75` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-019: Documented extra: Embedder

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/embedder.py:15
**Export:** Embedder

**Issue:** `references/resources.md:231` documents `Embedder`, which the enumerated source API surface lacks and the source still declares

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

**Issue:** `references/connectors.md:209` documents `File`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `File` is a documented extra, a name the source still declares at `python/cocoindex/connectors/localfs/_source.py:34` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-022: Documented extra: FileLike

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/file.py:56
**Export:** FileLike

**Issue:** `references/resources.md:56` documents `FileLike`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `FileLike` is a documented extra, a name the source still declares at `python/cocoindex/resources/file.py:56` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-023: Documented extra: FileMetadata

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/file.py:40
**Export:** FileMetadata

**Issue:** `references/resources.md:44` documents `FileMetadata`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `FileMetadata` is a documented extra, a name the source still declares at `python/cocoindex/resources/file.py:40` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-025: Documented extra: FilePathMatcher

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/file.py:205
**Export:** FilePathMatcher

**Issue:** `references/resources.md:85` documents `FilePathMatcher`, which the enumerated source API surface lacks and the source still declares

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

**Issue:** the skill documents `GoogleDriveSource`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `GoogleDriveSource` is a documented extra, a name the source still declares at `python/cocoindex/connectors/google_drive/_source.py:215` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-029: Documented extra: GoogleDriveSourceSpec

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/google_drive/_source.py:145
**Export:** GoogleDriveSourceSpec

**Issue:** the skill documents `GoogleDriveSourceSpec`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `GoogleDriveSourceSpec` is a documented extra, a name the source still declares at `python/cocoindex/connectors/google_drive/_source.py:145` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-030: Documented extra: IdGenerator

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/id.py:89
**Export:** IdGenerator

**Issue:** `references/resources.md:155` documents `IdGenerator`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `IdGenerator` is a documented extra, a name the source still declares at `python/cocoindex/resources/id.py:89` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-031: Documented extra: InvertedIndexDef

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/doris/_target.py:723
**Export:** InvertedIndexDef

**Issue:** the skill documents `InvertedIndexDef`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `InvertedIndexDef` is a documented extra, a name the source still declares at `python/cocoindex/connectors/doris/_target.py:723` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-032: Documented extra: IsDeleteFn

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/kafka/_source.py:30
**Export:** IsDeleteFn

**Issue:** the skill documents `IsDeleteFn`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `IsDeleteFn` is a documented extra, a name the source still declares at `python/cocoindex/connectors/kafka/_source.py:30` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-033: Documented extra: KafkaTopicTarget

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/kafka/_target.py:209
**Export:** KafkaTopicTarget

**Issue:** the skill documents `KafkaTopicTarget`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `KafkaTopicTarget` is a documented extra, a name the source still declares at `python/cocoindex/connectors/kafka/_target.py:209` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-034: Documented extra: LanceAsyncConnection

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/lancedb/_target.py:33
**Export:** LanceAsyncConnection

**Issue:** the skill documents `LanceAsyncConnection`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LanceAsyncConnection` is a documented extra, a name the source still declares at `python/cocoindex/connectors/lancedb/_target.py:33` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-035: Documented extra: LanceType

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/lancedb/_target.py:63
**Export:** LanceType

**Issue:** the skill documents `LanceType`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LanceType` is a documented extra, a name the source still declares at `python/cocoindex/connectors/lancedb/_target.py:63` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-036: Documented extra: LiteLLMEmbedder

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/litellm.py:22
**Export:** LiteLLMEmbedder

**Issue:** `references/ops.md:158` documents `LiteLLMEmbedder`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LiteLLMEmbedder` is a documented extra, a name the source still declares at `python/cocoindex/ops/litellm.py:22` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-037: Documented extra: LlmPairResolver

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/llm_resolver.py:49
**Export:** LlmPairResolver

**Issue:** `references/ops.md:201` documents `LlmPairResolver`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LlmPairResolver` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/llm_resolver.py:49` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-039: Documented extra: MatchAllFilePathMatcher

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/file.py:215
**Export:** MatchAllFilePathMatcher

**Issue:** `references/resources.md:89` documents `MatchAllFilePathMatcher`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MatchAllFilePathMatcher` is a documented extra, a name the source still declares at `python/cocoindex/resources/file.py:215` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-040: Documented extra: MultiVectorSchema

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:49
**Export:** MultiVectorSchema

**Issue:** `references/resources.md:212` documents `MultiVectorSchema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MultiVectorSchema` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:49` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-041: Documented extra: MultiVectorSchemaProvider

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:43
**Export:** MultiVectorSchemaProvider

**Issue:** `references/connectors.md:68` documents `MultiVectorSchemaProvider`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MultiVectorSchemaProvider` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:43` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-042: Documented extra: PairDecision

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:46
**Export:** PairDecision

**Issue:** `references/ops.md:185` documents `PairDecision`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PairDecision` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:46` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-043: Documented extra: PairResolver

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:97
**Export:** PairResolver

**Issue:** `references/ops.md:188` documents `PairResolver`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PairResolver` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:97` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-044: Documented extra: PatternFilePathMatcher

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/file.py:227
**Export:** PatternFilePathMatcher

**Issue:** `references/resources.md:90` documents `PatternFilePathMatcher`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PatternFilePathMatcher` is a documented extra, a name the source still declares at `python/cocoindex/resources/file.py:227` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-045: Documented extra: PgSourceSpec

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/postgres/_source.py:54
**Export:** PgSourceSpec

**Issue:** the skill documents `PgSourceSpec`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PgSourceSpec` is a documented extra, a name the source still declares at `python/cocoindex/connectors/postgres/_source.py:54` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-046: Documented extra: PgTableSource

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/postgres/_source.py:130
**Export:** PgTableSource

**Issue:** `SKILL.md:312` documents `PgTableSource`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PgTableSource` is a documented extra, a name the source still declares at `python/cocoindex/connectors/postgres/_source.py:130` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-047: Documented extra: PgType

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/postgres/_target.py:77
**Export:** PgType

**Issue:** the skill documents `PgType`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PgType` is a documented extra, a name the source still declares at `python/cocoindex/connectors/postgres/_target.py:77` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-048: Documented extra: PointStruct

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/qdrant/_target.py:42
**Export:** PointStruct

**Issue:** the skill documents `PointStruct`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PointStruct` is a documented extra, a name the source still declares at `python/cocoindex/connectors/qdrant/_target.py:42` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-049: Documented extra: QdrantVectorDef

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/qdrant/_target.py:50
**Export:** QdrantVectorDef

**Issue:** `references/connectors.md:68` documents `QdrantVectorDef`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `QdrantVectorDef` is a documented extra, a name the source still declares at `python/cocoindex/connectors/qdrant/_target.py:50` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-050: Documented extra: QueryHandlerInfo

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/query_handler.py:21
**Export:** QueryHandlerInfo

**Issue:** `SKILL.md:214` documents `QueryHandlerInfo`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `QueryHandlerInfo` is a documented extra, a name the source still declares at `python/cocoindex/query_handler.py:21` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-051: Documented extra: QueryHandlerResultFields

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/query_handler.py:10
**Export:** QueryHandlerResultFields

**Issue:** `SKILL.md:215` documents `QueryHandlerResultFields`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `QueryHandlerResultFields` is a documented extra, a name the source still declares at `python/cocoindex/query_handler.py:10` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-052: Documented extra: QueryInfo

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/query_handler.py:30
**Export:** QueryInfo

**Issue:** `SKILL.md:216` documents `QueryInfo`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `QueryInfo` is a documented extra, a name the source still declares at `python/cocoindex/query_handler.py:30` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-053: Documented extra: QueryOutput

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/query_handler.py:43
**Export:** QueryOutput

**Issue:** `SKILL.md:217` documents `QueryOutput`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `QueryOutput` is a documented extra, a name the source still declares at `python/cocoindex/query_handler.py:43` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-054: Documented extra: RecursiveSplitter

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/text.py:120
**Export:** RecursiveSplitter

**Issue:** `references/ops.md:64` documents `RecursiveSplitter`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `python/cocoindex/ops/text.py`

**Remediation:** No change: `RecursiveSplitter` is a documented extra, a name the source still declares at `python/cocoindex/ops/text.py:120` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-055: Documented extra: RelationTarget

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/surrealdb/_target.py:1153
**Export:** RelationTarget

**Issue:** the skill documents `RelationTarget`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `RelationTarget` is a documented extra, a name the source still declares at `python/cocoindex/connectors/surrealdb/_target.py:1153` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-056: Documented extra: ResolutionEvent

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:70
**Export:** ResolutionEvent

**Issue:** `references/ops.md:187` documents `ResolutionEvent`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ResolutionEvent` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:70` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-057: Documented extra: ResolvedEntities

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:114
**Export:** ResolvedEntities

**Issue:** `references/ops.md:189` documents `ResolvedEntities`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ResolvedEntities` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:114` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-058: Documented extra: RetryConfig

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/doris/_target.py:178
**Export:** RetryConfig

**Issue:** the skill documents `RetryConfig`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `RetryConfig` is a documented extra, a name the source still declares at `python/cocoindex/connectors/doris/_target.py:178` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-059: Documented extra: RowFetcher

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/postgres/_source.py:62
**Export:** RowFetcher

**Issue:** the skill documents `RowFetcher`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `RowFetcher` is a documented extra, a name the source still declares at `python/cocoindex/connectors/postgres/_source.py:62` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-060: Documented extra: S3File

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/amazon_s3/_source.py:89
**Export:** S3File

**Issue:** `references/connectors.md:218` documents `S3File`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `S3File` is a documented extra, a name the source still declares at `python/cocoindex/connectors/amazon_s3/_source.py:89` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-061: Documented extra: S3FilePath

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/amazon_s3/_source.py:46
**Export:** S3FilePath

**Issue:** the skill documents `S3FilePath`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `S3FilePath` is a documented extra, a name the source still declares at `python/cocoindex/connectors/amazon_s3/_source.py:46` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-062: Documented extra: S3Walker

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/amazon_s3/_source.py:247
**Export:** S3Walker

**Issue:** `references/connectors.md:218` documents `S3Walker`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `S3Walker` is a documented extra, a name the source still declares at `python/cocoindex/connectors/amazon_s3/_source.py:247` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-063: Documented extra: SentenceTransformerEmbedder

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/sentence_transformers.py:25
**Export:** SentenceTransformerEmbedder

**Issue:** `references/ops.md:113` documents `SentenceTransformerEmbedder`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `SentenceTransformerEmbedder` is a documented extra, a name the source still declares at `python/cocoindex/ops/sentence_transformers.py:25` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-064: Documented extra: SeparatorSplitter

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/text.py:39
**Export:** SeparatorSplitter

**Issue:** `references/ops.md:40` documents `SeparatorSplitter`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `python/cocoindex/ops/text.py`

**Remediation:** No change: `SeparatorSplitter` is a documented extra, a name the source still declares at `python/cocoindex/ops/text.py:39` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-065: Documented extra: ServerSettings

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/setting.py:93
**Export:** ServerSettings

**Issue:** `SKILL.md:212` documents `ServerSettings`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ServerSettings` is a documented extra, a name the source still declares at `python/cocoindex/setting.py:93` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-066: Documented extra: SqliteType

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/sqlite/_target.py:154
**Export:** SqliteType

**Issue:** the skill documents `SqliteType`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `SqliteType` is a documented extra, a name the source still declares at `python/cocoindex/connectors/sqlite/_target.py:154` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-067: Documented extra: SurrealType

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/surrealdb/_target.py:171
**Export:** SurrealType

**Issue:** the skill documents `SurrealType`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `SurrealType` is a documented extra, a name the source still declares at `python/cocoindex/connectors/surrealdb/_target.py:171` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-068: Documented extra: SyncFunction

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/function.py:491
**Export:** SyncFunction

**Issue:** `SKILL.md:275` documents `SyncFunction`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `SyncFunction` is a documented extra, a name the source still declares at `python/cocoindex/_internal/function.py:491` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-071: Documented extra: TextPosition

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/chunk.py:9
**Export:** TextPosition

**Issue:** `references/resources.md:14` documents `TextPosition`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `TextPosition` is a documented extra, a name the source still declares at `python/cocoindex/resources/chunk.py:9` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-072: Documented extra: UuidGenerator

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/id.py:152
**Export:** UuidGenerator

**Issue:** `references/resources.md:162` documents `UuidGenerator`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `UuidGenerator` is a documented extra, a name the source still declares at `python/cocoindex/resources/id.py:152` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-074: Documented extra: Vec0TableDef

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/sqlite/_target.py:121
**Export:** Vec0TableDef

**Issue:** `references/connectors.md:108` documents `Vec0TableDef`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Vec0TableDef` is a documented extra, a name the source still declares at `python/cocoindex/connectors/sqlite/_target.py:121` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-075: Documented extra: VectorIndexDef

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/doris/_target.py:709
**Export:** VectorIndexDef

**Issue:** `SKILL.md:326` documents `VectorIndexDef`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `VectorIndexDef` is a documented extra, a name the source still declares at `python/cocoindex/connectors/doris/_target.py:709` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-076: Documented extra: VectorSchema

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:23
**Export:** VectorSchema

**Issue:** `references/resources.md:198` documents `VectorSchema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `VectorSchema` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:23` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-077: Documented extra: VectorSchemaProvider

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:17
**Export:** VectorSchemaProvider

**Issue:** `references/resources.md:194` documents `VectorSchemaProvider`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `VectorSchemaProvider` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:17` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-078: Documented extra: build_vector_search_query

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/doris/_target.py:1317
**Export:** build_vector_search_query

**Issue:** the skill documents `build_vector_search_query`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `build_vector_search_query` is a documented extra, a name the source still declares at `python/cocoindex/connectors/doris/_target.py:1317` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-079: Documented extra: cli

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/cli.py:505
**Export:** cli

**Issue:** `SKILL.md:218` documents `cli`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `cli` is a documented extra, a name the source still declares at `python/cocoindex/cli.py:505` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-080: Documented extra: collection_target

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/qdrant/_target.py:510
**Export:** collection_target

**Issue:** the skill documents `collection_target`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `collection_target` is a documented extra, a name the source still declares at `python/cocoindex/connectors/qdrant/_target.py:510` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-083: Documented extra: create_client

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/qdrant/_target.py:294
**Export:** create_client

**Issue:** the skill documents `create_client`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `create_client` is a documented extra, a name the source still declares at `python/cocoindex/connectors/qdrant/_target.py:294` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-084: Documented extra: create_pool

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/postgres/_target.py:1367
**Export:** create_pool

**Issue:** the skill documents `create_pool`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `create_pool` is a documented extra, a name the source still declares at `python/cocoindex/connectors/postgres/_target.py:1367` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-085: Documented extra: declare_collection_target

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/qdrant/_target.py:537
**Export:** declare_collection_target

**Issue:** the skill documents `declare_collection_target`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `declare_collection_target` is a documented extra, a name the source still declares at `python/cocoindex/connectors/qdrant/_target.py:537` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-086: Documented extra: declare_dir_target

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/localfs/_target.py:356
**Export:** declare_dir_target

**Issue:** the skill documents `declare_dir_target`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `declare_dir_target` is a documented extra, a name the source still declares at `python/cocoindex/connectors/localfs/_target.py:356` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-087: Documented extra: declare_file

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/localfs/_target.py:451
**Export:** declare_file

**Issue:** the skill documents `declare_file`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `declare_file` is a documented extra, a name the source still declares at `python/cocoindex/connectors/localfs/_target.py:451` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-088: Documented extra: declare_kafka_topic_target

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/kafka/_target.py:277
**Export:** declare_kafka_topic_target

**Issue:** the skill documents `declare_kafka_topic_target`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `declare_kafka_topic_target` is a documented extra, a name the source still declares at `python/cocoindex/connectors/kafka/_target.py:277` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-089: Documented extra: declare_relation_target

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/surrealdb/_target.py:1357
**Export:** declare_relation_target

**Issue:** the skill documents `declare_relation_target`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `declare_relation_target` is a documented extra, a name the source still declares at `python/cocoindex/connectors/surrealdb/_target.py:1357` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-091: Documented extra: detect_code_language

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/text.py:19
**Export:** detect_code_language

**Issue:** `references/ops.md:23` documents `detect_code_language`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `python/cocoindex/ops/text.py`

**Remediation:** No change: `detect_code_language` is a documented extra, a name the source still declares at `python/cocoindex/ops/text.py:19` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-092: Documented extra: dir_target

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/localfs/_target.py:391
**Export:** dir_target

**Issue:** the skill documents `dir_target`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `dir_target` is a documented extra, a name the source still declares at `python/cocoindex/connectors/localfs/_target.py:391` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-093: Documented extra: generate_id

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/id.py:31
**Export:** generate_id

**Issue:** `references/resources.md:140` documents `generate_id`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `generate_id` is a documented extra, a name the source still declares at `python/cocoindex/resources/id.py:31` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-094: Documented extra: generate_uuid

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/id.py:61
**Export:** generate_uuid

**Issue:** `references/resources.md:146` documents `generate_uuid`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `generate_uuid` is a documented extra, a name the source still declares at `python/cocoindex/resources/id.py:61` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-095: Documented extra: get_multi_vector_schema

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:58
**Export:** get_multi_vector_schema

**Issue:** the skill documents `get_multi_vector_schema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_multi_vector_schema` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:58` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-096: Documented extra: get_object

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/amazon_s3/_source.py:159
**Export:** get_object

**Issue:** the skill documents `get_object`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_object` is a documented extra, a name the source still declares at `python/cocoindex/connectors/amazon_s3/_source.py:159` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-097: Documented extra: get_vector_schema

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:33
**Export:** get_vector_schema

**Issue:** `references/resources.md:206` documents `get_vector_schema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_vector_schema` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:33` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-098: Documented extra: is_live_component_class

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/live_component.py:35
**Export:** is_live_component_class

**Issue:** `references/live-components.md:14` documents `is_live_component_class`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `is_live_component_class` is a documented extra, a name the source still declares at `python/cocoindex/_internal/live_component.py:35` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-099: Documented extra: kafka_topic_target

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/kafka/_target.py:250
**Export:** kafka_topic_target

**Issue:** the skill documents `kafka_topic_target`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `kafka_topic_target` is a documented extra, a name the source still declares at `python/cocoindex/connectors/kafka/_target.py:250` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-100: Documented extra: list_files

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/google_drive/_source.py:199
**Export:** list_files

**Issue:** the skill documents `list_files`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `list_files` is a documented extra, a name the source still declares at `python/cocoindex/connectors/google_drive/_source.py:199` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-101: Documented extra: list_objects

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/amazon_s3/_source.py:351
**Export:** list_objects

**Issue:** `references/connectors.md:218` documents `list_objects`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `list_objects` is a documented extra, a name the source still declares at `python/cocoindex/connectors/amazon_s3/_source.py:351` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-102: Documented extra: litellm

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/litellm.py:1
**Export:** litellm

**Issue:** `SKILL.md:111` documents `litellm`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `litellm` is a documented extra, a name the source still declares at `python/cocoindex/ops/litellm.py:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-103: Documented extra: managed_connection

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/sqlite/_target.py:1282
**Export:** managed_connection

**Issue:** the skill documents `managed_connection`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `managed_connection` is a documented extra, a name the source still declares at `python/cocoindex/connectors/sqlite/_target.py:1282` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-104: Documented extra: mount_collection_target

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/qdrant/_target.py:561
**Export:** mount_collection_target

**Issue:** `references/connectors.md:58` documents `mount_collection_target`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `mount_collection_target` is a documented extra, a name the source still declares at `python/cocoindex/connectors/qdrant/_target.py:561` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-105: Documented extra: mount_dir_target

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/localfs/_target.py:424
**Export:** mount_dir_target

**Issue:** the skill documents `mount_dir_target`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `mount_dir_target` is a documented extra, a name the source still declares at `python/cocoindex/connectors/localfs/_target.py:424` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-106: Documented extra: mount_kafka_topic_target

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/kafka/_target.py:301
**Export:** mount_kafka_topic_target

**Issue:** the skill documents `mount_kafka_topic_target`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `mount_kafka_topic_target` is a documented extra, a name the source still declares at `python/cocoindex/connectors/kafka/_target.py:301` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-107: Documented extra: mount_relation_target

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/surrealdb/_target.py:1382
**Export:** mount_relation_target

**Issue:** the skill documents `mount_relation_target`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `mount_relation_target` is a documented extra, a name the source still declares at `python/cocoindex/connectors/surrealdb/_target.py:1382` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-109: Documented extra: read

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/amazon_s3/_source.py:221
**Export:** read

**Issue:** the skill documents `read`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `read` is a documented extra, a name the source still declares at `python/cocoindex/connectors/amazon_s3/_source.py:221` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-110: Documented extra: relation_target

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/surrealdb/_target.py:1329
**Export:** relation_target

**Issue:** the skill documents `relation_target`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `relation_target` is a documented extra, a name the source still declares at `python/cocoindex/connectors/surrealdb/_target.py:1329` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-111: Documented extra: resolve_entities

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:186
**Export:** resolve_entities

**Issue:** `references/ops.md:191` documents `resolve_entities`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `resolve_entities` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:186` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-113: Documented extra: topic_as_map

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/kafka/_source.py:361
**Export:** topic_as_map

**Issue:** `references/connectors.md:153` documents `topic_as_map`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `topic_as_map` is a documented extra, a name the source still declares at `python/cocoindex/connectors/kafka/_source.py:361` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-114: Documented extra: walk_dir

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/localfs/_source.py:234
**Export:** walk_dir

**Issue:** `SKILL.md:82` documents `walk_dir`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `walk_dir` is a documented extra, a name the source still declares at `python/cocoindex/connectors/localfs/_source.py:234` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-117: Discovery testing not performed: subagents unavailable, routing test requires isolated context

**Severity:** Info
**Category:** Discovery (discovery)
**Source:** SKILL.md:3

**Issue:** The discovery catalog holds 4 skills (oms-cocoindex, oms-cognee, oms-storybook-react-vite, oms-uitripled), but this run could not spawn subagents, so the three realistic prompts were not routed in an isolated context; the main thread knows the skill under test and does not self-route.

**Remediation:** Re-run test-skill for oms-cocoindex in an environment that can spawn subagents, so three realistic prompts drawn from the SKILL.md frontmatter description (SKILL.md:3) are routed against the 4-skill catalog in isolated context before export.

### Discovery Quality

**Discovery Test:** skipped: subagents unavailable, routing test requires isolated context

discovery: skipped, subagents unavailable, routing test requires isolated context (catalog of 4 skills: oms-cocoindex, oms-cognee, oms-storybook-react-vite, oms-uitripled; recorded as GAP-117, Info, excluded from Discovery Quality scoring). No description optimization hints: Tessl Review did not run and skill-check flagged no description issue.
