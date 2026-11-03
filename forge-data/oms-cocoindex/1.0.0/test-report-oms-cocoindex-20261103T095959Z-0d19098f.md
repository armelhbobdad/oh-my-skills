---
workflowType: 'test-skill'
skillName: 'oms-cocoindex'
skillDir: 'skills/oms-cocoindex/1.0.0/oms-cocoindex'
runId: '20261103T095959Z-0d19098f'
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
testDate: '2026-11-03T09:59:59Z'
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

**Mode Rationale:** metadata.json records `skill_type: "single"`, an individual skill, so naive mode applies (API-surface coverage; coherence is structural only and is not a scored category).

**Analysis Plan:**
- Coverage Check: Deep tier, full source access to the workspace clone at the pinned commit 5fe4f37: enumerate the public API surface, check each export is documented in SKILL.md or its references, and compare every documented signature against the source declaration (params: name, type, order, optionality; and the return type) with AST-backed verification.
- Coherence Check: structural only (naive mode): references named from SKILL.md resolve, examples are consistent with the documented signatures, and the package layout is sound.

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
| `fn` | - | yes | - | python/cocoindex/_internal/function.py:1811 | WARN |
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
| `mount_table_target` | function | yes | - | python/cocoindex/connectors/doris/_target.py:1228 | PASS |
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
| `walk_dir` | function | yes | - | python/cocoindex/connectors/localfs/_source.py:234 | PASS |

### Coverage Summary

- **Exports Found:** 79
- **Documented:** 79 (100%)
- **Missing Documentation:** 0
- **Signature Mismatches:** 0
- **Stale Documentation:** 102, documented extras included
- **Scoring Warnings:**
  - python/cocoindex/_internal/component_ctx.py:180: a signature mismatch for `ComponentSubpath`, which is no documented signature on the source surface: not scored, no gap
  - python/cocoindex/_internal/live_component.py:70: a signature mismatch for `LiveComponentOperator`, which is no documented signature on the source surface: not scored, no gap
- **Nested Entry Points:** `python/cocoindex/connectors/amazon_s3/__init__.py` inside `python/cocoindex/__init__.py`: `S3File`, `S3FilePath`, `S3Walker`, `get_object`, `list_objects`, `read`; `python/cocoindex/connectors/doris/__init__.py` inside `python/cocoindex/__init__.py`: `ColumnDef`, `DorisConnectionConfig`, `DorisTableTarget`, `DorisType`, `InvertedIndexDef`, `ManagedConnection`, `RetryConfig`, `TableSchema`, `ValueEncoder`, `VectorIndexDef`, `build_vector_search_query`, `connect`, `connect_async`, `declare_table_target`, `mount_table_target`, `table_target`; `python/cocoindex/connectors/google_drive/__init__.py` inside `python/cocoindex/__init__.py`: `DriveFile`, `DriveFileInfo`, `GoogleDriveSource`, `GoogleDriveSourceSpec`, `list_files`; `python/cocoindex/connectors/kafka/__init__.py` inside `python/cocoindex/__init__.py`: `DeletionValueFn`, `IsDeleteFn`, `KafkaTopicTarget`, `declare_kafka_topic_target`, `kafka_topic_target`, `mount_kafka_topic_target`, `topic_as_map`; `python/cocoindex/connectors/lancedb/__init__.py` inside `python/cocoindex/__init__.py`: `LanceAsyncConnection`, `LanceType`, `TableTarget`; `python/cocoindex/connectors/localfs/__init__.py` inside `python/cocoindex/__init__.py`: `DirTarget`, `DirWalker`, `File`, `FilePath`, `declare_dir_target`, `declare_file`, `dir_target`, `mount_dir_target`, `walk_dir`; `python/cocoindex/connectors/postgres/__init__.py` inside `python/cocoindex/__init__.py`: `PgSourceSpec`, `PgTableSource`, `PgType`, `RowFetcher`, `create_pool`; `python/cocoindex/connectors/qdrant/__init__.py` inside `python/cocoindex/__init__.py`: `CollectionSchema`, `CollectionTarget`, `PointStruct`, `QdrantVectorDef`, `collection_target`, `create_client`, `declare_collection_target`, `mount_collection_target`; `python/cocoindex/connectors/sqlite/__init__.py` inside `python/cocoindex/__init__.py`: `SqliteType`, `Vec0TableDef`, `managed_connection`; `python/cocoindex/connectors/surrealdb/__init__.py` inside `python/cocoindex/__init__.py`: `ConnectionFactory`, `RelationTarget`, `SurrealType`, `declare_relation_target`, `mount_relation_target`, `relation_target`
- **Restored by the Stale-Scope Guard:** `App` (python/cocoindex/_internal/app.py:208), `AppConfig` (python/cocoindex/_internal/app.py:202), `ChildTargetDef` (python/cocoindex/_internal/target_state.py:95), `ComponentContext` (python/cocoindex/_internal/component_ctx.py:55), `ComponentStats` (python/cocoindex/_internal/update_stats.py:14), `ComponentSubpath` (python/cocoindex/_internal/component_ctx.py:142), `ContextKey` (python/cocoindex/_internal/context_keys.py:99), `ContextProvider` (python/cocoindex/_internal/context_keys.py:124), `DropHandle` (python/cocoindex/_internal/app.py:143), `Environment` (python/cocoindex/_internal/environment.py:183), `EnvironmentBuilder` (python/cocoindex/_internal/environment.py:87), `ExceptionContext` (python/cocoindex/_internal/component_ctx.py:43), `ExceptionHandler` (python/cocoindex/_internal/component_ctx.py:25), `GPU` (python/cocoindex/_internal/runner.py:282), `LifespanFn` (python/cocoindex/_internal/environment.py:118), `LiveComponent` (python/cocoindex/_internal/live_component.py:28), `LiveComponentOperator` (python/cocoindex/_internal/live_component.py:46), `LiveMapFeed` (python/cocoindex/_internal/live_component.py:108), `LiveMapSubscriber` (python/cocoindex/_internal/live_component.py:130), `LiveMapView` (python/cocoindex/_internal/live_component.py:119), `LogicTracking` (python/cocoindex/_internal/function.py:65), `MaybePendingS` (python/cocoindex/_internal/pending_marker.py:115), `MemoStateOutcome` (python/cocoindex/_internal/typing.py:67), `NON_EXISTENCE` (python/cocoindex/_internal/typing.py:60), `NonExistenceType` (python/cocoindex/_internal/typing.py:47), `NotMemoKeyable` (python/cocoindex/_internal/memo_fingerprint.py:136), `PendingS` (python/cocoindex/_internal/pending_marker.py:74), `PendingTargetStateProvider` (python/cocoindex/_internal/target_state.py:243), `ROOT_PATH` (python/cocoindex/_internal/stable_path.py:59), `ResolvedS` (python/cocoindex/_internal/pending_marker.py:89), `ResolvesTo` (python/cocoindex/_internal/pending_marker.py:118), `Runner` (python/cocoindex/_internal/runner.py:34), `StableKey` (python/cocoindex/_internal/stable_path.py:9), `StablePath` (python/cocoindex/_internal/stable_path.py:16), `Symbol` (python/cocoindex/_internal/stable_path.py:7), `TargetActionSink` (python/cocoindex/_internal/target_state.py:143), `TargetHandler` (python/cocoindex/_internal/target_state.py:197), `TargetReconcileOutput` (python/cocoindex/_internal/target_state.py:188), `TargetState` (python/cocoindex/_internal/target_state.py:248), `TargetStateProvider` (python/cocoindex/_internal/target_state.py:208), `UpdateHandle` (python/cocoindex/_internal/app.py:49), `UpdateSnapshot` (python/cocoindex/_internal/update_stats.py:59), `UpdateStats` (python/cocoindex/_internal/update_stats.py:39), `UpdateStatus` (python/cocoindex/_internal/update_stats.py:9), `component_subpath` (python/cocoindex/_internal/component_ctx.py:198), `declare_target_state` (python/cocoindex/_internal/target_state.py:265), `declare_target_state_with_child` (python/cocoindex/_internal/target_state.py:282), `exception_handler` (python/cocoindex/_internal/component_ctx.py:331), `fn` (python/cocoindex/_internal/function.py:1811), `get_component_context` (python/cocoindex/_internal/component_ctx.py:305), `is_non_existence` (python/cocoindex/_internal/typing.py:63), `memo_fingerprint` (python/cocoindex/_internal/memo_fingerprint.py:361), `register_memo_key_function` (python/cocoindex/_internal/memo_fingerprint.py:155), `register_root_target_states_provider` (python/cocoindex/_internal/target_state.py:305), `serialize_by_pickle` (python/cocoindex/_internal/serde.py:151), `show_progress` (python/cocoindex/_internal/app.py:194), `unpickle_safe` (python/cocoindex/_internal/serde.py:128), `use_context` (python/cocoindex/_internal/component_ctx.py:273)

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 100% |
| Signature Accuracy | 100% |
| Type Coverage | 100% |

### Coverage Notes

- **Deep-tier source verification:** `gh api repos/cocoindex-io/cocoindex/git/ref/tags/v1.0.0` resolves to commit `5fe4f37a526e51516655832ec9814e7ca24ade9a`, equal to `metadata.source_commit` and to the workspace HEAD (init §5b: `workspace_drift_check: ok (5fe4f37)`).
- **How the comparisons ran (strict re-test):** this session has no subagent-spawning tool, so §1 and §2 ran in the main thread by their "without subagents" fallback: the main thread read SKILL.md and all seven reference files (SKILL.md has no `## Full` headings), built the §1 inventory (181 exports, validated, spot-check `App`, `S3Walker`, `walk_dir` all present), and compared every one of the 27 planned signatures against its full source declaration, one result file per source file (10 files, plus one Deep-tier type file). The comparison rule applied was the step's own, word for word: params (name, type, order, optionality) and the return type, a missing optional parameter being a mismatch. No leniency rule was added: an omitted parameter of any kind (optional, keyword-only, `*args`, `**kwargs`) counts as a mismatch, and so does a differing return type. Calls the rule's words do not decide are recorded below as borderline and are not counted.
- **Signatures compared:** 27 on the signature universe; 0 strict mismatches. 18 match exactly (`mount_target`, `start`, `stop`, `start_blocking`, `stop_blocking`, `default_env`, `runtime`, `show_progress`, `component_subpath`, `use_context`, `get_component_context`, `exception_handler`, `lifespan`, `declare_target_state`, `declare_target_state_with_child`, `register_root_target_states_provider`, `topic_as_map`, `mount_collection_target`).
- **Borderline signature calls (recorded, not counted):** (a) parameter annotations the documentation leaves out, with name, order and optionality matching: `*args`/`**kwargs` written bare where the source declares `*args: P.args, **kwargs: P.kwargs` (`map` api.py:532, `mount` api.py:333/342, `mount_each` api.py:427/437 whose subpath overload also leaves `subpath, fn, items` bare, `use_mount` api.py:194-244 whose subpath form leaves `processor_fn` bare), and `obj` / `typ, key_fn, state_fn` / `cls` written bare (`is_non_existence` typing.py:63 `obj: Any`, `memo_fingerprint` memo_fingerprint.py:361 `obj: object`, `register_memo_key_function` memo_fingerprint.py:155, `unpickle_safe` serde.py:128 `cls: type`, `serialize_by_pickle` serde.py:151 `cls: type`); (b) return types the documentation does not state at all (`register_memo_key_function` -> None, `unpickle_safe` -> type, `serialize_by_pickle` -> type; the inventory leaves `return_type` out per the §1 contract, and validate-inventory marks the three incomplete); (c) `use_mount`'s documented `processor_fn: AnyCallable[P, ResolvesTo[ReturnT] | ReturnT]`, which condenses the eight overloads at api.py:194-244 (AsyncCallable/Callable x ResolvesTo[ReturnT]/ReturnT) into one union type the source never writes. Counting every borderline call would make 9 of the 27 mismatches (Signature Accuracy 66.67%); it would not change this run's verdict, which the split-body gaps already decide.
- **Functions documented by call example only (not compared):** `walk_dir`, `mount_table_target`, `CollectionSchema.create` and the `__all__`-listed connector factories carry no signature in the skill, only call examples or names, so the inventory gives them no `params` (the §1 contract). Two notes for a reader who would count call examples: `localfs.walk_dir(sourcedir, recursive=True, path_matcher=...)` omits the `live` keyword of `walk_dir(path, *, live=False, recursive=False, path_matcher=None)` (connectors/localfs/_source.py:234), and the plan keys signatures by bare name, so a documented `mount_table_target` would be checked against the doris declaration (connectors/doris/_target.py:1228, first by file) rather than the postgres one the example calls (connectors/postgres/_target.py:1332).
- **Split-body cross-check (§1b):** 7 strict mismatches between the SKILL.md body and a reference file, each a High `split-body-mismatch` gap: `EnvironmentBuilder` (SKILL.md:170 `ctxmgr`/`async_ctxmgr` vs component-api.md:94 `cm`), `mount_each` (SKILL.md:176 no `**kwargs`), `use_mount` (SKILL.md:178 no `**kwargs`), `map` (SKILL.md:179 no `**kwargs`), `TargetActionSink` (SKILL.md:187 `async_fn` vs target-state.md:38 `fn`), `LiveComponentOperator` (SKILL.md:193 `update(subpath, fn, *args)` vs live-components.md:27 `processor_fn`, `**kwargs`), `ContextProvider` (SKILL.md:203 `get(key)` vs settings-cli.md:171 `get(key, t=None)`). In all seven the reference agrees with the source and SKILL.md does not (environment.py:106/109-110, api.py:427-449/194-244/532-537, target_state.py:158-160, live_component.py:70-76, context_keys.py:254), though `get(key)` is the source's first overload (context_keys.py:249).
- **Borderline cross-check calls (recorded, not counted):** `App` "Methods: `update()`, `update_blocking()`, `drop()`, `drop_blocking()`" (SKILL.md:167) names the methods with empty parentheses while the reference gives their keyword-only optional parameters (component-api.md:29-32); whether empty parentheses claim an empty parameter list is not decided by the rule. Also borderline: the `/` positional-only marker SKILL.md omits for `App` (SKILL.md:167) and `TargetHandler.reconcile` (SKILL.md:186), the bare `TargetReconcileOutput | None` return (SKILL.md:186) against the parameterized one (target-state.md:16), `LifespanFn` written as `Callable[[EnvironmentBuilder], Iterator[None] | AsyncIterator[None]]` (SKILL.md:171) against the union of two callables (component-api.md:101-104), the subpath overloads the SKILL.md rows of `mount`/`mount_each`/`use_mount` leave out (SKILL.md:152 documents the subpath form in prose), `AppConfig`'s default written `default_env` (SKILL.md:168) against `_default_env` (component-api.md:13), type-variable spellings (`ValueT`/`_ValueT`, `R`/`ReturnT`, `T`/`T_co`), and `*passthrough` (SKILL.md:106) against `*args`.
- **Deep-tier type cross-check:** the documented type definitions match their declarations (Key Types block against stable_path.py:7-59, update_stats.py:9-62, pending_marker.py:115, typing.py:47-74; `AppConfig`, `App` methods, `Environment`, `EnvironmentBuilder`, `ContextKey`, `ContextProvider`, the target-state classes, `QdrantVectorDef` fields, `CollectionSchema.create`, the `@coco.fn` keyword set memo/batching/max_batch_size/runner/version/logic_tracking/deps at function.py:1585-1632), except two method-level mismatches, which the scoring script lists as warnings with no gap because their names carry no compared signature: `ComponentSubpath.__exit__(self, *exc)` (component-api.md:273) against `(self, exc_type, exc_val, exc_tb)` (component_ctx.py:180), and `LiveComponentOperator.update`/`.delete` documented `-> ComponentMountHandle` (live-components.md:33-34) against `-> Any` (live_component.py:76, :93). Borderline: `QdrantVectorDef.schema` described as a `VectorSchemaProvider` (connectors.md:68) where the source also accepts `MultiVectorSchemaProvider` and a `ContextKey` (qdrant/_target.py:59-66); `App.__init__`'s `main_fn: AsyncCallable[P, R] | Callable[P, R]` condensing two overloads (app.py:221-237).
- **Re-export trace (Deep tier):** `cocoindex/__init__.py` star-imports `_internal.api`, whose `__all__` (api.py:669-759) omits `is_live_component_class`, so SKILL.md:160's `coco.is_live_component_class(cls)` names an attribute the package does not export (api.py:109 imports it only for internal use); the coverage machinery classes the name as a documented extra (Info). `coco.Settings` is re-exported from `_internal/setting.py:56`, while the skill cites the separate `cocoindex.setting` module (setting.py:44), whose class is the same apart from `get_default_db_path`.
- **Stale names:** 102 documented names lie outside the `scope.include` set. `classify-stale` marks none fabricated; 97 are declared at the line it reports (documented extras), and 5 (`Chunk`, `CustomLanguageConfig`, `RecursiveSplitter`, `SeparatorSplitter`, `detect_code_language`) are declared both in `python/cocoindex/_internal/core.pyi` and in their public module.
- **Numerator ground truth:** skipped (no inflation signature).
- **Metadata count coherence:** one Medium finding, `stats.exports_public_api=140` vs `exports[].length=119` (15% drift).
- **Provenance line check:** 1 `line-not-definition` entry, `ServerSettings.parse_cors_origins` recorded at `python/cocoindex/setting.py:123` (definition lines 117, 121, 124).

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)

### Structural Findings

| # | Type | Severity | Detail | Line |
|---|------|----------|--------|------|
| - | - | - | No structural finding | - |

**Structural Issues:** 0

Checks run (§2.0 to §2.7):
- §2.1 Required sections: `usage` is satisfied by `## Quick Start` (line 12) and `api_surface` by `## Key API Summary` (line 163). `description` matches no heading, but the non-empty frontmatter `description` satisfies the family. No finding.
- §2.2 Code fences: balanced (8 fences). §2.3 No opening fence lacks a language tag. §2.6 No table row drifts from its header. §2.7 No `scripts/` or `assets/` folder.
- §2.4 Usage scope (split body: Quick Start, Common Workflows, Key API Summary, plus the seven reference files): every function export of the inventory is referenced; `zero_usage[]` is empty.
- §2.5 Async/sync: 27 function exports are called in examples (34 appear in none). Every awaited call matches an async declaration, except calls whose line carries the `await` of another call, which raise no finding: `component_subpath` passed as an argument inside `await coco.mount(...)` / `await operator.update(...)` (references/component-api.md:284, :289, references/live-components.md:102, :110), `use_context` before the awaited `.embed(...)` (SKILL.md:57, `chainedMember: embed`), `asyncpg.create_pool` (SKILL.md:36, references/component-api.md:120, not the postgres connector's `create_pool`), and `async with coco.runtime()` (SKILL.md:123, references/component-api.md:146, the documented async form of the dual-mode context manager). Sync exports (`start_blocking`, `stop_blocking`, `generate_uuid`, `detect_code_language`, `topic_as_map`, `walk_dir`, `get_component_context`, `register_root_target_states_provider`, `is_non_existence`, `memo_fingerprint`, `register_memo_key_function`) are called without `await`.
- §2b Migration/deprecation (Deep tier, evidence report present): `t2_future_count: 0` from the frontmatter, and SKILL.md has no "Migration & Deprecation Warnings" section, so no case applies. `## Migration from v0.3.37` (line 294) is historical cutover content, a different heading outside the Section 4b contract.

### Reference Consistency (split-body)

| # | Reference File | Export | Issue | SKILL.md Line | Reference Line |
|---|---------------|--------|-------|---------------|---------------|
| 1 | references/component-api.md | `EnvironmentBuilder` | context-manager parameter named `ctxmgr` / `async_ctxmgr` in SKILL.md, `cm` in the reference (and the source) | 170 | 94 |
| 2 | references/component-api.md | `mount_each` | SKILL.md `(fn, items, *args)` omits the `**kwargs` the reference shows | 176 | 223 |
| 3 | references/component-api.md | `use_mount` | SKILL.md `(processor_fn, *args) -> R` omits the `**kwargs` the reference shows | 178 | 234 |
| 4 | references/component-api.md | `map` | SKILL.md `(fn, items, *args) -> list[R]` omits the `**kwargs` the reference shows | 179 | 255 |
| 5 | references/target-state.md | `TargetActionSink` | `from_async_fn(async_fn)` in SKILL.md, `from_async_fn(fn: ...)` in the reference | 187 | 38 |
| 6 | references/live-components.md | `LiveComponentOperator` | SKILL.md `update(subpath, fn, *args)`: `fn` vs `processor_fn`, and no `**kwargs` | 193 | 27 |
| 7 | references/settings-cli.md | `ContextProvider` | SKILL.md `get(key)` omits the optional `t: type[T] \| None = None` the reference shows | 203 | 171 |

**Exports Cross-Checked:** 97
**Mismatches Found:** 7

Coverage-check §1b recorded these seven as High `split-body-mismatch` gaps (GAP-106 to GAP-112). The borderline cross-check calls (not counted) are listed in the Coverage Notes.

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

**Result:** **FAIL**, not scored: the hard gate blocked this run on 7 Critical or High gap(s), listed first in the Gap Report.

## Gap Report

**Total Gaps:** 112
**Blocking (Critical + High):** 7
**Non-blocking (Medium + Low + Info):** 105

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|------------------|
| Critical | 0 | None |
| High | 7 | Read the source code and write or correct the documentation |
| Medium | 2 | Add type definitions, interface docs or the missing section |
| Low | 1 | Add examples or metadata |
| Info | 102 | Optional improvements, no action required |
| **Total** | **112** | |

### GAP-106: Split-body mismatch: EnvironmentBuilder

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** references/component-api.md:94
**Export:** EnvironmentBuilder

**Issue:** SKILL.md:170 lists provide_with(key, ctxmgr) and provide_async_with(key, async_ctxmgr); references/component-api.md:94-95 declares provide_with(self, key: ContextKey[Any], cm: ContextManager[Any]) -> Any and provide_async_with(self, key: ContextKey[Any], cm: AsyncContextManager[Any]) -> Any. The context-manager parameter name differs (ctxmgr / async_ctxmgr vs cm).

**Remediation:** Make SKILL.md:170 and references/component-api.md:94-95 agree. The source names the parameter cm (python/cocoindex/_internal/environment.py:106 and :109-110), as the reference does, so change SKILL.md:170 `provide_with(key, ctxmgr)` to `provide_with(key, cm)` and `provide_async_with(key, async_ctxmgr)` to `provide_async_with(key, cm)`; leave references/component-api.md:94-95 as it is.

### GAP-107: Split-body mismatch: mount_each

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** references/component-api.md:223
**Export:** mount_each

**Issue:** SKILL.md:176 shows mount_each(fn, items, *args) -> ComponentMountHandle; references/component-api.md:223 shows mount_each(fn: AnyCallable[Concatenate[T, P], Any], items: _ItemsType[T], *args, **kwargs) -> ComponentMountHandle. SKILL.md is missing the **kwargs parameter.

**Remediation:** Make SKILL.md:176 and references/component-api.md:223 agree. The source declares `**kwargs: P.kwargs` (python/cocoindex/_internal/api.py:437-442), as the reference does, so change SKILL.md:176 `await coco.mount_each(fn, items, *args) -> ComponentMountHandle` to `await coco.mount_each(fn, items, *args, **kwargs) -> ComponentMountHandle`; leave references/component-api.md:223 as it is.

### GAP-108: Split-body mismatch: use_mount

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** references/component-api.md:234
**Export:** use_mount

**Issue:** SKILL.md:178 shows use_mount(processor_fn, *args) -> R; references/component-api.md:234 shows use_mount(processor_fn: AnyCallable[P, ResolvesTo[ReturnT] | ReturnT], *args, **kwargs) -> ReturnT. SKILL.md is missing the **kwargs parameter.

**Remediation:** Make SKILL.md:178 and references/component-api.md:234 agree. Every source overload declares `**kwargs: P.kwargs` (python/cocoindex/_internal/api.py:194-244), as the reference does, so change SKILL.md:178 `result = await coco.use_mount(processor_fn, *args) -> R` to `result = await coco.use_mount(processor_fn, *args, **kwargs) -> R`; leave references/component-api.md:234 as it is.

### GAP-109: Split-body mismatch: map

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** references/component-api.md:255
**Export:** map

**Issue:** SKILL.md:179 shows map(fn, items, *args) -> list[R]; references/component-api.md:255-259 shows map(fn: Callable[Concatenate[T, P], Coroutine[Any, Any, ReturnT]], items: Iterable[T] | AsyncIterable[T], *args, **kwargs) -> list[ReturnT]. SKILL.md is missing the **kwargs parameter.

**Remediation:** Make SKILL.md:179 and references/component-api.md:255-259 agree. The source declares `**kwargs: P.kwargs` (python/cocoindex/_internal/api.py:536), as the reference does, so change SKILL.md:179 `await coco.map(fn, items, *args) -> list[R]` to `await coco.map(fn, items, *args, **kwargs) -> list[R]`; leave references/component-api.md:255-259 as it is.

### GAP-110: Split-body mismatch: TargetActionSink

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** references/target-state.md:38
**Export:** TargetActionSink

**Issue:** SKILL.md:187 lists from_async_fn(async_fn); references/target-state.md:38 declares from_async_fn(fn: AsyncTargetActionSinkFn[ActionT_contra, OptChildHandlerT_co]). The parameter name differs (async_fn vs fn).

**Remediation:** Make SKILL.md:187 and references/target-state.md:38 agree. The source names the parameter fn (python/cocoindex/_internal/target_state.py:158-160), as the reference does, so change SKILL.md:187 `from_async_fn(async_fn)` to `from_async_fn(fn)`; leave references/target-state.md:38 as it is.

### GAP-111: Split-body mismatch: LiveComponentOperator

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** references/live-components.md:27
**Export:** LiveComponentOperator

**Issue:** SKILL.md:193 lists update(subpath, fn, *args); references/live-components.md:27-33 declares update(self, subpath: ComponentSubpath, processor_fn: AnyCallable[_P, Any], *args: _P.args, **kwargs: _P.kwargs) -> ComponentMountHandle. The second parameter is named fn in SKILL.md and processor_fn in the reference, and SKILL.md is missing the **kwargs parameter.

**Remediation:** Make SKILL.md:193 and references/live-components.md:27-33 agree. The source declares `update(self, subpath, processor_fn, *args, **kwargs)` (python/cocoindex/_internal/live_component.py:70-76), as the reference does, so change SKILL.md:193 `update(subpath, fn, *args)` to `update(subpath, processor_fn, *args, **kwargs)`; leave references/live-components.md:27-33 as it is (its prose bullet at references/live-components.md:40 repeats the short form and can be aligned the same way).

### GAP-112: Split-body mismatch: ContextProvider

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** references/settings-cli.md:171
**Export:** ContextProvider

**Issue:** SKILL.md:203 lists get(key); references/settings-cli.md:171 declares get(self, key: ContextKey[T] | str, t: type[T] | None = None) -> Any. SKILL.md is missing the optional parameter t.

**Remediation:** Make SKILL.md:203 and references/settings-cli.md:171 agree. The source implementation is `get(self, key: ContextKey[T] | str, t: type[T] | None = None) -> Any` (python/cocoindex/_internal/context_keys.py:254, with overloads at :249-253), as the reference does, so change SKILL.md:203 `get(key)` to `get(key, t=None)`; leave references/settings-cli.md:171 as it is.

### GAP-103: stale brief scope: scope.include globs match no source file

**Severity:** Medium
**Category:** Coverage (brief-scope-stale)
**Source:** forge-data/oms-cocoindex/skill-brief.yaml

**Issue:** the `scope.include` globs `docs/docs/**/*.md`, `docs/docs/**/*.mdx` match no file in the source tested; the `all` set restores 58 root exports, defined in files no include glob covers: `App` in `python/cocoindex/_internal/app.py`, `AppConfig` in `python/cocoindex/_internal/app.py`, `ChildTargetDef` in `python/cocoindex/_internal/target_state.py`, `ComponentContext` in `python/cocoindex/_internal/component_ctx.py`, `ComponentStats` in `python/cocoindex/_internal/update_stats.py`, `ComponentSubpath` in `python/cocoindex/_internal/component_ctx.py`, `ContextKey` in `python/cocoindex/_internal/context_keys.py`, `ContextProvider` in `python/cocoindex/_internal/context_keys.py`, `DropHandle` in `python/cocoindex/_internal/app.py`, `Environment` in `python/cocoindex/_internal/environment.py`, `EnvironmentBuilder` in `python/cocoindex/_internal/environment.py`, `ExceptionContext` in `python/cocoindex/_internal/component_ctx.py`, `ExceptionHandler` in `python/cocoindex/_internal/component_ctx.py`, `GPU` in `python/cocoindex/_internal/runner.py`, `LifespanFn` in `python/cocoindex/_internal/environment.py`, `LiveComponent` in `python/cocoindex/_internal/live_component.py`, `LiveComponentOperator` in `python/cocoindex/_internal/live_component.py`, `LiveMapFeed` in `python/cocoindex/_internal/live_component.py`, `LiveMapSubscriber` in `python/cocoindex/_internal/live_component.py`, `LiveMapView` in `python/cocoindex/_internal/live_component.py`, `LogicTracking` in `python/cocoindex/_internal/function.py`, `MaybePendingS` in `python/cocoindex/_internal/pending_marker.py`, `MemoStateOutcome` in `python/cocoindex/_internal/typing.py`, `NON_EXISTENCE` in `python/cocoindex/_internal/typing.py`, `NonExistenceType` in `python/cocoindex/_internal/typing.py`, `NotMemoKeyable` in `python/cocoindex/_internal/memo_fingerprint.py`, `PendingS` in `python/cocoindex/_internal/pending_marker.py`, `PendingTargetStateProvider` in `python/cocoindex/_internal/target_state.py`, `ROOT_PATH` in `python/cocoindex/_internal/stable_path.py`, `ResolvedS` in `python/cocoindex/_internal/pending_marker.py`, `ResolvesTo` in `python/cocoindex/_internal/pending_marker.py`, `Runner` in `python/cocoindex/_internal/runner.py`, `StableKey` in `python/cocoindex/_internal/stable_path.py`, `StablePath` in `python/cocoindex/_internal/stable_path.py`, `Symbol` in `python/cocoindex/_internal/stable_path.py`, `TargetActionSink` in `python/cocoindex/_internal/target_state.py`, `TargetHandler` in `python/cocoindex/_internal/target_state.py`, `TargetReconcileOutput` in `python/cocoindex/_internal/target_state.py`, `TargetState` in `python/cocoindex/_internal/target_state.py`, `TargetStateProvider` in `python/cocoindex/_internal/target_state.py`, `UpdateHandle` in `python/cocoindex/_internal/app.py`, `UpdateSnapshot` in `python/cocoindex/_internal/update_stats.py`, `UpdateStats` in `python/cocoindex/_internal/update_stats.py`, `UpdateStatus` in `python/cocoindex/_internal/update_stats.py`, `component_subpath` in `python/cocoindex/_internal/component_ctx.py`, `declare_target_state` in `python/cocoindex/_internal/target_state.py`, `declare_target_state_with_child` in `python/cocoindex/_internal/target_state.py`, `exception_handler` in `python/cocoindex/_internal/component_ctx.py`, `fn` in `python/cocoindex/_internal/function.py`, `get_component_context` in `python/cocoindex/_internal/component_ctx.py`, `is_non_existence` in `python/cocoindex/_internal/typing.py`, `memo_fingerprint` in `python/cocoindex/_internal/memo_fingerprint.py`, `register_memo_key_function` in `python/cocoindex/_internal/memo_fingerprint.py`, `register_root_target_states_provider` in `python/cocoindex/_internal/target_state.py`, `serialize_by_pickle` in `python/cocoindex/_internal/serde.py`, `show_progress` in `python/cocoindex/_internal/app.py`, `unpickle_safe` in `python/cocoindex/_internal/serde.py`, `use_context` in `python/cocoindex/_internal/component_ctx.py`

**Remediation:** Edit `scope.include` in `forge-data/oms-cocoindex/skill-brief.yaml` by hand so each glob matches the files it meant in this version of the source (update-skill does not rewrite an include glob), and add to `scope.exclude` any restored file the brief meant to leave out.

### GAP-104: metadata drift — barrel export counts diverge

**Severity:** Medium
**Category:** Coverage (metadata-drift)
**Source:** skills/oms-cocoindex/1.0.0/oms-cocoindex/metadata.json

**Issue:** stats.exports_public_api=140, exports[].length=119 → 15% drift

**Remediation:** Recount the exports and correct the diverging counts in `skills/oms-cocoindex/1.0.0/oms-cocoindex/metadata.json`; update-skill applies it as a metadata update.

### GAP-105: Provenance line is not the definition of ServerSettings.parse_cors_origins

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

### GAP-003: Documented extra: CanonicalSide

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:35
**Export:** CanonicalSide

**Issue:** `references/ops.md:177` documents `CanonicalSide`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CanonicalSide` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:35` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-004: Documented extra: ChildTargetDef

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/target_state.py:95
**Export:** ChildTargetDef

**Issue:** `references/target-state.md:47` documents `ChildTargetDef`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ChildTargetDef` is a documented extra, a name the source still declares at `python/cocoindex/_internal/target_state.py:95` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-005: Documented extra: Chunk

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/chunk.py:26
**Export:** Chunk

**Issue:** `SKILL.md:25` documents `Chunk`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `python/cocoindex/resources/chunk.py`

**Remediation:** No change: `Chunk` is a documented extra, a name the source still declares at `python/cocoindex/resources/chunk.py:26` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-006: Documented extra: ComponentContext

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/component_ctx.py:55
**Export:** ComponentContext

**Issue:** `SKILL.md:152` documents `ComponentContext`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ComponentContext` is a documented extra, a name the source still declares at `python/cocoindex/_internal/component_ctx.py:55` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-007: Documented extra: ComponentStats

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/update_stats.py:14
**Export:** ComponentStats

**Issue:** `SKILL.md:237` documents `ComponentStats`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ComponentStats` is a documented extra, a name the source still declares at `python/cocoindex/_internal/update_stats.py:14` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-008: Documented extra: ComponentSubpath

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/component_ctx.py:142
**Export:** ComponentSubpath

**Issue:** `SKILL.md:197` documents `ComponentSubpath`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ComponentSubpath` is a documented extra, a name the source still declares at `python/cocoindex/_internal/component_ctx.py:142` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-009: Documented extra: ContextKey

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/context_keys.py:99
**Export:** ContextKey

**Issue:** `SKILL.md:31` documents `ContextKey`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ContextKey` is a documented extra, a name the source still declares at `python/cocoindex/_internal/context_keys.py:99` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-010: Documented extra: ContextProvider

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/context_keys.py:124
**Export:** ContextProvider

**Issue:** `SKILL.md:203` documents `ContextProvider`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ContextProvider` is a documented extra, a name the source still declares at `python/cocoindex/_internal/context_keys.py:124` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-011: Documented extra: CustomLanguageConfig

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/text.py:87
**Export:** CustomLanguageConfig

**Issue:** `SKILL.md:115` documents `CustomLanguageConfig`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `python/cocoindex/ops/text.py`

**Remediation:** No change: `CustomLanguageConfig` is a documented extra, a name the source still declares at `python/cocoindex/ops/text.py:87` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-012: Documented extra: DropHandle

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/app.py:143
**Export:** DropHandle

**Issue:** `SKILL.md:241` documents `DropHandle`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `DropHandle` is a documented extra, a name the source still declares at `python/cocoindex/_internal/app.py:143` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-013: Documented extra: Embedder

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/embedder.py:15
**Export:** Embedder

**Issue:** `SKILL.md:161` documents `Embedder`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Embedder` is a documented extra, a name the source still declares at `python/cocoindex/resources/embedder.py:15` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-014: Documented extra: Environment

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/environment.py:183
**Export:** Environment

**Issue:** `SKILL.md:3` documents `Environment`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Environment` is a documented extra, a name the source still declares at `python/cocoindex/_internal/environment.py:183` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-015: Documented extra: EnvironmentBuilder

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/environment.py:87
**Export:** EnvironmentBuilder

**Issue:** `SKILL.md:35` documents `EnvironmentBuilder`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `EnvironmentBuilder` is a documented extra, a name the source still declares at `python/cocoindex/_internal/environment.py:87` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-016: Documented extra: ExceptionContext

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/component_ctx.py:43
**Export:** ExceptionContext

**Issue:** `references/component-api.md:316` documents `ExceptionContext`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ExceptionContext` is a documented extra, a name the source still declares at `python/cocoindex/_internal/component_ctx.py:43` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-017: Documented extra: ExceptionHandler

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/component_ctx.py:25
**Export:** ExceptionHandler

**Issue:** `references/component-api.md:61` documents `ExceptionHandler`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ExceptionHandler` is a documented extra, a name the source still declares at `python/cocoindex/_internal/component_ctx.py:25` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-018: Documented extra: ExistingCanonicalPolicy

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:57
**Export:** ExistingCanonicalPolicy

**Issue:** `references/ops.md:179` documents `ExistingCanonicalPolicy`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ExistingCanonicalPolicy` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:57` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-019: Documented extra: FileLike

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/file.py:56
**Export:** FileLike

**Issue:** `SKILL.md:26` documents `FileLike`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `FileLike` is a documented extra, a name the source still declares at `python/cocoindex/resources/file.py:56` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-020: Documented extra: FileMetadata

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/file.py:40
**Export:** FileMetadata

**Issue:** `SKILL.md:338` documents `FileMetadata`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `FileMetadata` is a documented extra, a name the source still declares at `python/cocoindex/resources/file.py:40` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-021: Documented extra: FilePathMatcher

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/file.py:205
**Export:** FilePathMatcher

**Issue:** `references/resources.md:35` documents `FilePathMatcher`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `FilePathMatcher` is a documented extra, a name the source still declares at `python/cocoindex/resources/file.py:205` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-022: Documented extra: GPU

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/runner.py:282
**Export:** GPU

**Issue:** `SKILL.md:8` documents `GPU`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `GPU` is a documented extra, a name the source still declares at `python/cocoindex/_internal/runner.py:282` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-023: Documented extra: GlobalExecutionOptions

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/setting.py:12
**Export:** GlobalExecutionOptions

**Issue:** `SKILL.md:206` documents `GlobalExecutionOptions`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `GlobalExecutionOptions` is a documented extra, a name the source still declares at `python/cocoindex/setting.py:12` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-024: Documented extra: IdGenerator

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/id.py:89
**Export:** IdGenerator

**Issue:** `SKILL.md:27` documents `IdGenerator`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `IdGenerator` is a documented extra, a name the source still declares at `python/cocoindex/resources/id.py:89` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-025: Documented extra: LanceAsyncConnection

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/connectors/lancedb/_target.py:33
**Export:** LanceAsyncConnection

**Issue:** `references/connectors.md:86` documents `LanceAsyncConnection`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LanceAsyncConnection` is a documented extra, a name the source still declares at `python/cocoindex/connectors/lancedb/_target.py:33` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-026: Documented extra: LifespanFn

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/environment.py:118
**Export:** LifespanFn

**Issue:** `SKILL.md:171` documents `LifespanFn`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LifespanFn` is a documented extra, a name the source still declares at `python/cocoindex/_internal/environment.py:118` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-027: Documented extra: LiteLLMEmbedder

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/litellm.py:22
**Export:** LiteLLMEmbedder

**Issue:** `SKILL.md:109` documents `LiteLLMEmbedder`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LiteLLMEmbedder` is a documented extra, a name the source still declares at `python/cocoindex/ops/litellm.py:22` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-028: Documented extra: LiveComponent

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/live_component.py:28
**Export:** LiveComponent

**Issue:** `SKILL.md:160` documents `LiveComponent`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LiveComponent` is a documented extra, a name the source still declares at `python/cocoindex/_internal/live_component.py:28` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-029: Documented extra: LiveComponentOperator

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/live_component.py:46
**Export:** LiveComponentOperator

**Issue:** `SKILL.md:193` documents `LiveComponentOperator`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LiveComponentOperator` is a documented extra, a name the source still declares at `python/cocoindex/_internal/live_component.py:46` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-030: Documented extra: LiveMapFeed

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/live_component.py:108
**Export:** LiveMapFeed

**Issue:** `SKILL.md:98` documents `LiveMapFeed`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LiveMapFeed` is a documented extra, a name the source still declares at `python/cocoindex/_internal/live_component.py:108` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-031: Documented extra: LiveMapSubscriber

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/live_component.py:130
**Export:** LiveMapSubscriber

**Issue:** `SKILL.md:195` documents `LiveMapSubscriber`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LiveMapSubscriber` is a documented extra, a name the source still declares at `python/cocoindex/_internal/live_component.py:130` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-032: Documented extra: LiveMapView

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/live_component.py:119
**Export:** LiveMapView

**Issue:** `SKILL.md:98` documents `LiveMapView`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LiveMapView` is a documented extra, a name the source still declares at `python/cocoindex/_internal/live_component.py:119` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-033: Documented extra: LlmPairResolver

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/llm_resolver.py:49
**Export:** LlmPairResolver

**Issue:** `references/ops.md:188` documents `LlmPairResolver`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LlmPairResolver` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/llm_resolver.py:49` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-034: Documented extra: LogicTracking

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/function.py:65
**Export:** LogicTracking

**Issue:** `SKILL.md:174` documents `LogicTracking`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LogicTracking` is a documented extra, a name the source still declares at `python/cocoindex/_internal/function.py:65` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-035: Documented extra: MatchAllFilePathMatcher

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/file.py:215
**Export:** MatchAllFilePathMatcher

**Issue:** `references/resources.md:36` documents `MatchAllFilePathMatcher`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MatchAllFilePathMatcher` is a documented extra, a name the source still declares at `python/cocoindex/resources/file.py:215` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-036: Documented extra: MaybePendingS

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/pending_marker.py:115
**Export:** MaybePendingS

**Issue:** `SKILL.md:185` documents `MaybePendingS`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MaybePendingS` is a documented extra, a name the source still declares at `python/cocoindex/_internal/pending_marker.py:115` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-037: Documented extra: MemoStateOutcome

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/typing.py:67
**Export:** MemoStateOutcome

**Issue:** `SKILL.md:253` documents `MemoStateOutcome`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MemoStateOutcome` is a documented extra, a name the source still declares at `python/cocoindex/_internal/typing.py:67` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-038: Documented extra: MultiVectorSchema

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:49
**Export:** MultiVectorSchema

**Issue:** `references/resources.md:173` documents `MultiVectorSchema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MultiVectorSchema` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:49` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-039: Documented extra: MultiVectorSchemaProvider

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:43
**Export:** MultiVectorSchemaProvider

**Issue:** `references/resources.md:173` documents `MultiVectorSchemaProvider`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `MultiVectorSchemaProvider` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:43` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-040: Documented extra: NON_EXISTENCE

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/typing.py:60
**Export:** NON_EXISTENCE

**Issue:** `SKILL.md:157` documents `NON_EXISTENCE`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `NON_EXISTENCE` is a documented extra, a name the source still declares at `python/cocoindex/_internal/typing.py:60` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-041: Documented extra: NonExistenceType

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/typing.py:47
**Export:** NonExistenceType

**Issue:** `SKILL.md:250` documents `NonExistenceType`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `NonExistenceType` is a documented extra, a name the source still declares at `python/cocoindex/_internal/typing.py:47` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-042: Documented extra: NotMemoKeyable

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/memo_fingerprint.py:136
**Export:** NotMemoKeyable

**Issue:** `SKILL.md:256` documents `NotMemoKeyable`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `NotMemoKeyable` is a documented extra, a name the source still declares at `python/cocoindex/_internal/memo_fingerprint.py:136` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-043: Documented extra: PairDecision

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:46
**Export:** PairDecision

**Issue:** `references/ops.md:178` documents `PairDecision`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PairDecision` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:46` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-044: Documented extra: PairResolver

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:97
**Export:** PairResolver

**Issue:** `references/ops.md:181` documents `PairResolver`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PairResolver` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:97` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-045: Documented extra: PatternFilePathMatcher

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/file.py:227
**Export:** PatternFilePathMatcher

**Issue:** `SKILL.md:26` documents `PatternFilePathMatcher`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PatternFilePathMatcher` is a documented extra, a name the source still declares at `python/cocoindex/resources/file.py:227` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-046: Documented extra: PendingS

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/pending_marker.py:74
**Export:** PendingS

**Issue:** `SKILL.md:244` documents `PendingS`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PendingS` is a documented extra, a name the source still declares at `python/cocoindex/_internal/pending_marker.py:74` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-047: Documented extra: PendingTargetStateProvider

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/target_state.py:243
**Export:** PendingTargetStateProvider

**Issue:** `SKILL.md:190` documents `PendingTargetStateProvider`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PendingTargetStateProvider` is a documented extra, a name the source still declares at `python/cocoindex/_internal/target_state.py:243` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-048: Documented extra: QueryHandlerInfo

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/query_handler.py:21
**Export:** QueryHandlerInfo

**Issue:** `SKILL.md:207` documents `QueryHandlerInfo`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `QueryHandlerInfo` is a documented extra, a name the source still declares at `python/cocoindex/query_handler.py:21` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-049: Documented extra: QueryHandlerResultFields

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/query_handler.py:10
**Export:** QueryHandlerResultFields

**Issue:** `SKILL.md:207` documents `QueryHandlerResultFields`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `QueryHandlerResultFields` is a documented extra, a name the source still declares at `python/cocoindex/query_handler.py:10` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-050: Documented extra: QueryInfo

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/query_handler.py:30
**Export:** QueryInfo

**Issue:** `SKILL.md:209` documents `QueryInfo`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `QueryInfo` is a documented extra, a name the source still declares at `python/cocoindex/query_handler.py:30` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-051: Documented extra: QueryOutput

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/query_handler.py:43
**Export:** QueryOutput

**Issue:** `SKILL.md:210` documents `QueryOutput`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `QueryOutput` is a documented extra, a name the source still declares at `python/cocoindex/query_handler.py:43` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-052: Documented extra: ROOT_PATH

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/stable_path.py:59
**Export:** ROOT_PATH

**Issue:** `SKILL.md:232` documents `ROOT_PATH`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ROOT_PATH` is a documented extra, a name the source still declares at `python/cocoindex/_internal/stable_path.py:59` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-053: Documented extra: RecursiveSplitter

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/text.py:120
**Export:** RecursiveSplitter

**Issue:** `SKILL.md:23` documents `RecursiveSplitter`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `python/cocoindex/ops/text.py`

**Remediation:** No change: `RecursiveSplitter` is a documented extra, a name the source still declares at `python/cocoindex/ops/text.py:120` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-054: Documented extra: ResolutionEvent

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:70
**Export:** ResolutionEvent

**Issue:** `references/ops.md:180` documents `ResolutionEvent`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ResolutionEvent` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:70` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-055: Documented extra: ResolvedEntities

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:114
**Export:** ResolvedEntities

**Issue:** `references/ops.md:182` documents `ResolvedEntities`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ResolvedEntities` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:114` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-056: Documented extra: ResolvedS

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/pending_marker.py:89
**Export:** ResolvedS

**Issue:** `SKILL.md:245` documents `ResolvedS`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ResolvedS` is a documented extra, a name the source still declares at `python/cocoindex/_internal/pending_marker.py:89` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-057: Documented extra: ResolvesTo

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/pending_marker.py:118
**Export:** ResolvesTo

**Issue:** `SKILL.md:247` documents `ResolvesTo`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ResolvesTo` is a documented extra, a name the source still declares at `python/cocoindex/_internal/pending_marker.py:118` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-058: Documented extra: Runner

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/runner.py:34
**Export:** Runner

**Issue:** `SKILL.md:183` documents `Runner`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Runner` is a documented extra, a name the source still declares at `python/cocoindex/_internal/runner.py:34` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-059: Documented extra: SentenceTransformerEmbedder

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/sentence_transformers.py:25
**Export:** SentenceTransformerEmbedder

**Issue:** `SKILL.md:24` documents `SentenceTransformerEmbedder`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `SentenceTransformerEmbedder` is a documented extra, a name the source still declares at `python/cocoindex/ops/sentence_transformers.py:25` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-060: Documented extra: SeparatorSplitter

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/text.py:39
**Export:** SeparatorSplitter

**Issue:** `SKILL.md:115` documents `SeparatorSplitter`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `python/cocoindex/ops/text.py`

**Remediation:** No change: `SeparatorSplitter` is a documented extra, a name the source still declares at `python/cocoindex/ops/text.py:39` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-061: Documented extra: ServerSettings

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/setting.py:93
**Export:** ServerSettings

**Issue:** `SKILL.md:205` documents `ServerSettings`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ServerSettings` is a documented extra, a name the source still declares at `python/cocoindex/setting.py:93` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-062: Documented extra: Settings

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/setting.py:44
**Export:** Settings

**Issue:** `SKILL.md:8` documents `Settings`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Settings` is a documented extra, a name the source still declares at `python/cocoindex/setting.py:44` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-063: Documented extra: StableKey

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/stable_path.py:9
**Export:** StableKey

**Issue:** `SKILL.md:230` documents `StableKey`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `StableKey` is a documented extra, a name the source still declares at `python/cocoindex/_internal/stable_path.py:9` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-064: Documented extra: StablePath

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/stable_path.py:16
**Export:** StablePath

**Issue:** `SKILL.md:231` documents `StablePath`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `StablePath` is a documented extra, a name the source still declares at `python/cocoindex/_internal/stable_path.py:16` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-065: Documented extra: Symbol

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/stable_path.py:7
**Export:** Symbol

**Issue:** `SKILL.md:230` documents `Symbol`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Symbol` is a documented extra, a name the source still declares at `python/cocoindex/_internal/stable_path.py:7` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-066: Documented extra: TargetActionSink

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/target_state.py:143
**Export:** TargetActionSink

**Issue:** `SKILL.md:187` documents `TargetActionSink`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `TargetActionSink` is a documented extra, a name the source still declares at `python/cocoindex/_internal/target_state.py:143` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-067: Documented extra: TargetHandler

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/target_state.py:197
**Export:** TargetHandler

**Issue:** `SKILL.md:8` documents `TargetHandler`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `TargetHandler` is a documented extra, a name the source still declares at `python/cocoindex/_internal/target_state.py:197` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-068: Documented extra: TargetReconcileOutput

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/target_state.py:188
**Export:** TargetReconcileOutput

**Issue:** `SKILL.md:186` documents `TargetReconcileOutput`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `TargetReconcileOutput` is a documented extra, a name the source still declares at `python/cocoindex/_internal/target_state.py:188` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-069: Documented extra: TargetState

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/target_state.py:248
**Export:** TargetState

**Issue:** `SKILL.md:3` documents `TargetState`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `TargetState` is a documented extra, a name the source still declares at `python/cocoindex/_internal/target_state.py:248` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-070: Documented extra: TargetStateProvider

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/target_state.py:208
**Export:** TargetStateProvider

**Issue:** `SKILL.md:156` documents `TargetStateProvider`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `TargetStateProvider` is a documented extra, a name the source still declares at `python/cocoindex/_internal/target_state.py:208` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-071: Documented extra: TextPosition

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/chunk.py:9
**Export:** TextPosition

**Issue:** `SKILL.md:338` documents `TextPosition`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `TextPosition` is a documented extra, a name the source still declares at `python/cocoindex/resources/chunk.py:9` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-072: Documented extra: UpdateHandle

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/app.py:49
**Export:** UpdateHandle

**Issue:** `SKILL.md:91` documents `UpdateHandle`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `UpdateHandle` is a documented extra, a name the source still declares at `python/cocoindex/_internal/app.py:49` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-073: Documented extra: UpdateSnapshot

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/update_stats.py:59
**Export:** UpdateSnapshot

**Issue:** `SKILL.md:239` documents `UpdateSnapshot`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `UpdateSnapshot` is a documented extra, a name the source still declares at `python/cocoindex/_internal/update_stats.py:59` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-074: Documented extra: UpdateStats

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/update_stats.py:39
**Export:** UpdateStats

**Issue:** `SKILL.md:238` documents `UpdateStats`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `UpdateStats` is a documented extra, a name the source still declares at `python/cocoindex/_internal/update_stats.py:39` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-075: Documented extra: UpdateStatus

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/update_stats.py:9
**Export:** UpdateStatus

**Issue:** `SKILL.md:236` documents `UpdateStatus`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `UpdateStatus` is a documented extra, a name the source still declares at `python/cocoindex/_internal/update_stats.py:9` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-076: Documented extra: UuidGenerator

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/id.py:152
**Export:** UuidGenerator

**Issue:** `SKILL.md:338` documents `UuidGenerator`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `UuidGenerator` is a documented extra, a name the source still declares at `python/cocoindex/resources/id.py:152` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-077: Documented extra: VectorSchema

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:23
**Export:** VectorSchema

**Issue:** `SKILL.md:338` documents `VectorSchema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `VectorSchema` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:23` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-078: Documented extra: VectorSchemaProvider

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:17
**Export:** VectorSchemaProvider

**Issue:** `SKILL.md:338` documents `VectorSchemaProvider`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `VectorSchemaProvider` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:17` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-079: Documented extra: cli

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/cli.py:505
**Export:** cli

**Issue:** `SKILL.md:211` documents `cli`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `cli` is a documented extra, a name the source still declares at `python/cocoindex/cli.py:505` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-080: Documented extra: component_subpath

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/component_ctx.py:198
**Export:** component_subpath

**Issue:** `SKILL.md:152` documents `component_subpath`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `component_subpath` is a documented extra, a name the source still declares at `python/cocoindex/_internal/component_ctx.py:198` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-081: Documented extra: declare_target_state

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/target_state.py:265
**Export:** declare_target_state

**Issue:** `SKILL.md:189` documents `declare_target_state`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `declare_target_state` is a documented extra, a name the source still declares at `python/cocoindex/_internal/target_state.py:265` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-082: Documented extra: declare_target_state_with_child

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/target_state.py:282
**Export:** declare_target_state_with_child

**Issue:** `SKILL.md:103` documents `declare_target_state_with_child`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `declare_target_state_with_child` is a documented extra, a name the source still declares at `python/cocoindex/_internal/target_state.py:282` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-083: Documented extra: detect_code_language

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/text.py:19
**Export:** detect_code_language

**Issue:** `SKILL.md:115` documents `detect_code_language`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `python/cocoindex/ops/text.py`

**Remediation:** No change: `detect_code_language` is a documented extra, a name the source still declares at `python/cocoindex/ops/text.py:19` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-084: Documented extra: exception_handler

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/component_ctx.py:331
**Export:** exception_handler

**Issue:** `SKILL.md:152` documents `exception_handler`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `exception_handler` is a documented extra, a name the source still declares at `python/cocoindex/_internal/component_ctx.py:331` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-085: Documented extra: fn

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/function.py:1811
**Export:** fn

**Issue:** `SKILL.md:3` documents `fn`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `fn` is a documented extra, a name the source still declares at `python/cocoindex/_internal/function.py:1811` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-086: Documented extra: generate_id

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/id.py:31
**Export:** generate_id

**Issue:** `SKILL.md:143` documents `generate_id`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `generate_id` is a documented extra, a name the source still declares at `python/cocoindex/resources/id.py:31` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-087: Documented extra: generate_uuid

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/id.py:61
**Export:** generate_uuid

**Issue:** `SKILL.md:144` documents `generate_uuid`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `generate_uuid` is a documented extra, a name the source still declares at `python/cocoindex/resources/id.py:61` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-088: Documented extra: get_component_context

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/component_ctx.py:305
**Export:** get_component_context

**Issue:** `SKILL.md:152` documents `get_component_context`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_component_context` is a documented extra, a name the source still declares at `python/cocoindex/_internal/component_ctx.py:305` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-089: Documented extra: get_multi_vector_schema

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:58
**Export:** get_multi_vector_schema

**Issue:** `SKILL.md:161` documents `get_multi_vector_schema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_multi_vector_schema` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:58` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-090: Documented extra: get_vector_schema

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/resources/schema.py:33
**Export:** get_vector_schema

**Issue:** `SKILL.md:161` documents `get_vector_schema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_vector_schema` is a documented extra, a name the source still declares at `python/cocoindex/resources/schema.py:33` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-091: Documented extra: is_live_component_class

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/live_component.py:35
**Export:** is_live_component_class

**Issue:** `SKILL.md:160` documents `is_live_component_class`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `is_live_component_class` is a documented extra, a name the source still declares at `python/cocoindex/_internal/live_component.py:35` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-092: Documented extra: is_non_existence

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/typing.py:63
**Export:** is_non_existence

**Issue:** `SKILL.md:157` documents `is_non_existence`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `is_non_existence` is a documented extra, a name the source still declares at `python/cocoindex/_internal/typing.py:63` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-093: Documented extra: lifespan

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/environment.py:449
**Export:** lifespan

**Issue:** `SKILL.md:3` documents `lifespan`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `lifespan` is a documented extra, a name the source still declares at `python/cocoindex/_internal/environment.py:449` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-094: Documented extra: litellm

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/litellm.py:1
**Export:** litellm

**Issue:** `SKILL.md:109` documents `litellm`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `litellm` is a documented extra, a name the source still declares at `python/cocoindex/ops/litellm.py:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-095: Documented extra: memo_fingerprint

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/memo_fingerprint.py:361
**Export:** memo_fingerprint

**Issue:** `SKILL.md:158` documents `memo_fingerprint`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `memo_fingerprint` is a documented extra, a name the source still declares at `python/cocoindex/_internal/memo_fingerprint.py:361` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-096: Documented extra: register_memo_key_function

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/memo_fingerprint.py:155
**Export:** register_memo_key_function

**Issue:** `SKILL.md:158` documents `register_memo_key_function`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `register_memo_key_function` is a documented extra, a name the source still declares at `python/cocoindex/_internal/memo_fingerprint.py:155` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-097: Documented extra: register_root_target_states_provider

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/target_state.py:305
**Export:** register_root_target_states_provider

**Issue:** `SKILL.md:156` documents `register_root_target_states_provider`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `register_root_target_states_provider` is a documented extra, a name the source still declares at `python/cocoindex/_internal/target_state.py:305` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-098: Documented extra: resolve_entities

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/ops/entity_resolution/__init__.py:186
**Export:** resolve_entities

**Issue:** `references/ops.md:184` documents `resolve_entities`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `resolve_entities` is a documented extra, a name the source still declares at `python/cocoindex/ops/entity_resolution/__init__.py:186` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-099: Documented extra: serialize_by_pickle

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/serde.py:151
**Export:** serialize_by_pickle

**Issue:** `SKILL.md:159` documents `serialize_by_pickle`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `serialize_by_pickle` is a documented extra, a name the source still declares at `python/cocoindex/_internal/serde.py:151` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-100: Documented extra: show_progress

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/app.py:194
**Export:** show_progress

**Issue:** `SKILL.md:140` documents `show_progress`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `show_progress` is a documented extra, a name the source still declares at `python/cocoindex/_internal/app.py:194` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-101: Documented extra: unpickle_safe

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/serde.py:128
**Export:** unpickle_safe

**Issue:** `SKILL.md:159` documents `unpickle_safe`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `unpickle_safe` is a documented extra, a name the source still declares at `python/cocoindex/_internal/serde.py:128` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### GAP-102: Documented extra: use_context

**Severity:** Info
**Category:** Structural (observation)
**Source:** python/cocoindex/_internal/component_ctx.py:273
**Export:** use_context

**Issue:** `SKILL.md:8` documents `use_context`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `use_context` is a documented extra, a name the source still declares at `python/cocoindex/_internal/component_ctx.py:273` outside the enumerated surface, and its documentation stays. Signature scoring compares its documented signature with the surface's record of it.

### Discovery Quality

**Discovery Test:** not run: the hard gate blocked the run
