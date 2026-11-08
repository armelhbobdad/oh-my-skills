---
workflowType: 'test-skill'
skillName: 'oms-cognee'
skillDir: 'skills/oms-cognee/1.6.2/oms-cognee'
runId: '20261108T095527Z-7a18a0bc'
testMode: 'naive'
forgeTier: 'Deep'
hardGate: 'blocked'
testResult: 'fail'
score: ''
threshold: '80%'
thresholdSource: 'workflow default (80%)'
analysisConfidence: 'full'
toolingStatus: 'ok'
workspaceDrift: 'ok'
health_check_dispatched: true
testDate: '2026-11-08T09:55:27Z'
stepsCompleted: ['init', 'detect-mode', 'coverage-check', 'coherence-check', 'external-validators', 'hard-gate', 'report']
nextWorkflow: 'update-skill'
---

# Test Report: oms-cognee

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

**Skill:** oms-cognee
**Test Mode:** naive
**Forge Tier:** Deep

**Mode Rationale:** metadata.json sets `skill_type: 'single'`, an individual skill, so the run checks API-surface coverage and structural coherence only (no coherence category in scoring).

**Analysis Plan:**
- Coverage Check: every public export of `cognee/__init__.py` at the pinned commit ba3631f (v1.6.2) against SKILL.md and its references, with AST-backed signature and type comparison (Deep tier).
- Coherence Check: structural only (naive mode): references resolve, sections the skill format requires are present, metadata agrees with the package.

## Coverage Analysis

**Tier:** Deep
**Source Access:** full
**Source Path:** /home/armel/.skf/workspace/repos/github.com/topoteretes/cognee
**Workspace Layout:** single package
**Denominator:** barrel (standard barrel, the `all` set: 92 exports)

**Files Analyzed:** 53

### Export Coverage

| Export | Type | Documented | Signature | Source Location | Status |
|--------|------|------------|-----------|-----------------|--------|
| `BoundTask` | - | yes | - | - | WARN |
| `COGXArchiveSource` | class | yes | yes | cognee/modules/migration/sources/cogx_archive.py:19 | PASS |
| `COGXDocument` | class | yes | yes | cognee/modules/migration/cogx.py:78 | PASS |
| `COGXEntity` | class | yes | yes | cognee/modules/migration/cogx.py:101 | PASS |
| `COGXEpisode` | class | yes | yes | cognee/modules/migration/cogx.py:93 | PASS |
| `COGXFact` | class | yes | yes | cognee/modules/migration/cogx.py:112 | PASS |
| `COGXManifest` | class | yes | yes | cognee/modules/migration/cogx.py:180 | PASS |
| `COGXMemory` | class | yes | yes | cognee/modules/migration/cogx.py:131 | PASS |
| `COGXMemoryBlock` | class | yes | yes | cognee/modules/migration/cogx.py:139 | PASS |
| `COGXRawNode` | class | yes | yes | cognee/modules/migration/cogx.py:148 | PASS |
| `COGXRecord` | - | yes | - | cognee/modules/migration/cogx.py:160 | PASS |
| `COGXScope` | class | yes | yes | cognee/modules/migration/cogx.py:60 | PASS |
| `COGXTurn` | class | yes | yes | cognee/modules/migration/cogx.py:87 | PASS |
| `COGX_VERSION` | - | yes | - | cognee/modules/migration/cogx.py:22 | PASS |
| `CogneeApiError` | - | yes | - | - | WARN |
| `CogneeConfigurationError` | - | yes | - | - | WARN |
| `CogneeSystemError` | - | yes | - | - | WARN |
| `CogneeTransientError` | - | yes | - | - | WARN |
| `CogneeValidationError` | - | yes | - | - | WARN |
| `DataPoint` | - | yes | - | - | WARN |
| `Dedup` | - | yes | - | - | WARN |
| `DistillationResult` | - | yes | - | - | WARN |
| `Drop` | - | yes | - | cognee/pipelines/types.py:32 | PASS |
| `EXPORT_FORMATS` | - | yes | - | cognee/modules/migration/export.py:35 | PASS |
| `Edge` | - | yes | - | - | WARN |
| `Embeddable` | - | yes | - | - | WARN |
| `EntitySpec` | - | yes | - | - | WARN |
| `ExportResult` | class | yes | yes | cognee/modules/migration/export.py:41 | PASS |
| `FeedbackEntry` | class | yes | - | cognee/memory/entries.py:62 | PASS |
| `FromIdentity` | - | yes | - | - | WARN |
| `GraphEdge` | class | yes | yes | cognee/modules/migration/snapshot.py:152 | PASS |
| `GraphSchemaSpec` | - | yes | - | - | WARN |
| `GraphSnapshot` | class | yes | yes | cognee/modules/migration/snapshot.py:161 | PASS |
| `GraphitiSource` | class | yes | yes | cognee/modules/migration/sources/zep.py:136 | PASS |
| `IMPORT_MODES` | - | yes | - | cognee/modules/migration/sources/base.py:19 | PASS |
| `ImproveKwargs` | - | yes | - | - | WARN |
| `ImproveResult` | - | yes | - | - | WARN |
| `LLMGateway` | - | yes | - | - | WARN |
| `LettaSource` | class | yes | yes | cognee/modules/migration/sources/letta.py:72 | PASS |
| `Mem0Source` | class | yes | yes | cognee/modules/migration/sources/mem0.py:26 | PASS |
| `MemoryEntry` | - | yes | - | cognee/memory/entries.py:129 | PASS |
| `MemorySource` | class | yes | yes | cognee/modules/migration/sources/base.py:36 | PASS |
| `PipelineRunCompleted` | - | yes | - | - | WARN |
| `PipelineRunErrored` | - | yes | - | - | WARN |
| `PipelineRunInfo` | - | yes | - | - | WARN |
| `PipelineRunStarted` | - | yes | - | - | WARN |
| `PushResult` | class | yes | yes | cognee/api/v1/push/push.py:26 | PASS |
| `QAEntry` | class | yes | - | cognee/memory/entries.py:24 | PASS |
| `REMEDIATION_MARKER` | - | yes | - | - | WARN |
| `RememberKwargs` | - | yes | - | - | WARN |
| `RememberResult` | class | yes | - | cognee/api/v1/remember/remember.py:600 | PASS |
| `SearchType` | class | yes | - | cognee/modules/search/types/SearchType.py:4 | PASS |
| `SessionModelUsage` | class | yes | - | cognee/modules/session_lifecycle/models.py:96 | PASS |
| `SessionRecord` | class | yes | - | cognee/modules/session_lifecycle/models.py:10 | PASS |
| `SkillRunEntry` | - | yes | - | - | WARN |
| `Task` | class | yes | yes | cognee/modules/pipelines/tasks/task.py:188 | PASS |
| `TaskSpec` | - | yes | - | - | WARN |
| `TraceEntry` | class | yes | - | cognee/memory/entries.py:40 | PASS |
| `UpdateResult` | - | yes | - | - | WARN |
| `ValidationIssue` | class | yes | yes | cognee/api/v1/validate/validate.py:99 | PASS |
| `ValidationReport` | class | yes | yes | cognee/api/v1/validate/validate.py:105 | PASS |
| `ValidationStatus` | class | yes | - | cognee/api/v1/validate/validate.py:93 | PASS |
| `ZepSource` | class | yes | yes | cognee/modules/migration/sources/zep.py:57 | PASS |
| `__version__` | - | yes | - | - | WARN |
| `add` | function | yes | yes | cognee/api/v1/add/add.py:39 | PASS |
| `add_data_points` | - | yes | - | - | WARN |
| `agent_memory` | function | yes | yes | cognee/modules/agent_memory/decorator.py:29 | PASS |
| `agents` | class | yes | - | cognee/api/v1/agents/agents.py:40 | PASS |
| `apply_write_proposal` | function | yes | no | cognee/api/v1/tools/tools.py:129 | FAIL |
| `build_snapshot` | function | yes | yes | cognee/modules/migration/snapshot.py:243 | PASS |
| `clear_traces` | function | yes | yes | cognee/modules/observability/trace_context.py:121 | PASS |
| `cognee_network_visualization` | function | yes | yes | cognee/modules/visualization/cognee_network_visualization.py:154 | PASS |
| `cognify` | function | yes | yes | cognee/api/v1/cognify/cognify.py:110 | PASS |
| `config` | class | yes | - | cognee/api/v1/config/config.py:171 | PASS |
| `datapoint_registry` | function | yes | yes | cognee/modules/migration/snapshot.py:39 | PASS |
| `datasets` | class | yes | - | cognee/api/v1/datasets/datasets.py:105 | PASS |
| `delete` | function | yes | yes | cognee/api/v1/delete/__init__.py:12 | PASS |
| `disable_tracing` | function | yes | yes | cognee/modules/observability/trace_context.py:43 | PASS |
| `disconnect` | function | yes | yes | cognee/api/v1/serve/disconnect.py:8 | PASS |
| `enable_tracing` | function | yes | yes | cognee/modules/observability/trace_context.py:18 | PASS |
| `export` | function | yes | yes | cognee/api/v1/export/export.py:16 | PASS |
| `export_dataset` | function | yes | yes | cognee/modules/migration/export.py:198 | PASS |
| `find_remediation` | - | yes | - | - | WARN |
| `forget` | function | yes | yes | cognee/api/v1/forget/forget.py:22 | PASS |
| `get_all_traces` | function | yes | yes | cognee/modules/observability/trace_context.py:112 | PASS |
| `get_cognee_version` | function | yes | yes | cognee/version.py:7 | PASS |
| `get_default_tasks` | - | yes | - | - | WARN |
| `get_errored_run_info` | - | yes | - | - | WARN |
| `get_last_trace` | function | yes | yes | cognee/modules/observability/trace_context.py:101 | PASS |
| `get_memory_provenance_graph` | function | yes | yes | cognee/api/v1/visualize/memory_provenance.py:645 | PASS |
| `get_schema_inventory` | function | yes | yes | cognee/api/v1/visualize/get_schema_inventory.py:77 | PASS |
| `graph_model_from_spec` | - | yes | - | - | WARN |
| `graph_model_to_graph_schema` | - | yes | - | - | WARN |
| `graph_schema_to_graph_model` | - | yes | - | - | WARN |
| `graph_spec_to_json_schema` | - | yes | - | - | WARN |
| `improve` | function | yes | yes | cognee/api/v1/improve/improve.py:101 | PASS |
| `is_tracing_enabled` | - | yes | - | - | WARN |
| `list_sql_connections` | function | yes | yes | cognee/api/v1/tools/tools.py:65 | PASS |
| `list_write_proposals` | function | yes | yes | cognee/api/v1/tools/tools.py:119 | PASS |
| `logger` | - | yes | - | cognee/__init__.py:34 | PASS |
| `memify` | function | yes | yes | cognee/modules/memify/memify.py:27 | PASS |
| `migration` | - | yes | - | - | WARN |
| `pipeline_needs_llm` | - | yes | - | - | WARN |
| `pipelines` | - | yes | - | - | WARN |
| `propose_corrections` | function | yes | no | cognee/api/v1/tools/tools.py:101 | FAIL |
| `propose_sql_write` | function | yes | no | cognee/api/v1/tools/tools.py:81 | FAIL |
| `prune` | class | yes | - | cognee/api/v1/prune/prune.py:5 | PASS |
| `push` | function | yes | yes | cognee/api/v1/push/push.py:96 | PASS |
| `read_archive` | function | yes | yes | cognee/modules/migration/cogx.py:322 | PASS |
| `read_manifest` | function | yes | yes | cognee/modules/migration/cogx.py:276 | PASS |
| `recall` | function | yes | yes | cognee/api/v1/recall/recall.py:347 | PASS |
| `register_sql_connection` | function | yes | no | cognee/api/v1/tools/tools.py:27 | FAIL |
| `rehydrate_node` | function | yes | yes | cognee/modules/migration/snapshot.py:116 | PASS |
| `reject_write_proposal` | function | yes | no | cognee/api/v1/tools/tools.py:146 | FAIL |
| `remediation_for` | - | yes | - | - | WARN |
| `remember` | function | yes | yes | cognee/api/v1/remember/remember.py:867 | PASS |
| `remove_sql_connection` | function | yes | no | cognee/api/v1/tools/tools.py:73 | FAIL |
| `report` | function | yes | yes | cognee/api/v1/report/report.py:13 | PASS |
| `run_custom_pipeline` | function | yes | yes | cognee/modules/run_custom_pipeline/run_custom_pipeline.py:14 | PASS |
| `run_migrations` | - | yes | - | - | WARN |
| `run_pipeline` | function | yes | yes | cognee/modules/pipelines/operations/pipeline.py:53 | PASS |
| `run_relational_migrations` | - | yes | - | - | WARN |
| `run_tasks` | function | yes | yes | cognee/modules/pipelines/operations/run_tasks.py:39 | PASS |
| `run_tasks_parallel` | function | yes | yes (Info) | cognee/modules/pipelines/operations/run_parallel.py:8 | WARN |
| `search` | function | yes | yes | cognee/api/v1/search/search.py:41 | PASS |
| `serve` | function | yes | yes | cognee/api/v1/serve/serve.py:17 | PASS |
| `session` | - | yes | - | cognee/api/v1/session/__init__.py:8 | PASS |
| `setup` | - | yes | - | - | WARN |
| `setup_logging` | - | yes | - | - | WARN |
| `start_ui` | function | yes | yes | cognee/api/v1/ui/ui.py:514 | PASS |
| `start_visualization_server` | - | yes | - | - | WARN |
| `task` | - | yes | - | - | WARN |
| `task_summary` | - | yes | - | - | WARN |
| `tools` | - | yes | - | - | WARN |
| `update` | function | yes | yes | cognee/api/v1/update/update.py:28 | PASS |
| `use_vector_adapter` | - | yes | - | - | WARN |
| `validate` | function | yes | yes | cognee/api/v1/validate/validate.py:198 | PASS |
| `visualization_server` | function | yes | yes | cognee/api/v1/visualize/start_visualization_server.py:6 | PASS |
| `visualize` | function | yes | yes | cognee/api/v1/visualize/visualize.py:193 | PASS |
| `visualize_graph` | function | yes | yes | cognee/api/v1/visualize/visualize.py:193 | PASS |
| `visualize_graph_json` | - | yes | - | - | WARN |
| `visualize_memory_provenance` | function | yes | yes | cognee/api/v1/visualize/memory_provenance.py:848 | PASS |
| `visualize_multi_user_graph` | - | yes | - | - | WARN |
| `visualize_semantic_json` | - | yes | - | - | WARN |
| `wait_for_background_tasks` | - | yes | - | - | WARN |

### Coverage Summary

- **Exports Found:** 92
- **Documented:** 92 (100%)
- **Missing Documentation:** 0
- **Signature Mismatches:** 6, plus 2 graded Low or Info and counted as matching
- **Stale Documentation:** 53, documented extras included
- **Scoped Out by the Brief:** `describe_resolution` (cognee/shared/env_file.py:127), `load_env_file` (cognee/shared/env_file.py:112), `run_migrations` (cognee/run_migrations.py:18), `setup_logging` (cognee/shared/logging_utils.py:345), `start_visualization_server` (cognee/shared/utils.py:481), `wait_for_background_tasks` (cognee/infrastructure/background_tasks.py:66)
- **Nested Entry Points:** `cognee/api/v1/api_keys/routers/__init__.py` inside `cognee/__init__.py`: `get_api_key_management_router`; `cognee/api/v1/cloud/routers/__init__.py` inside `cognee/__init__.py`: `get_checks_router`; `cognee/api/v1/permissions/routers/__init__.py` inside `cognee/__init__.py`: `get_permissions_router`; `cognee/api/v1/settings/routers/__init__.py` inside `cognee/__init__.py`: `get_settings_router`

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 100% |
| Signature Accuracy | 91.67% |
| Type Coverage | 100% |

### Coverage Notes

- **Inventory (§1, §1a):** the §1 inventory reader ran as a subagent over SKILL.md and all four `references/` files (`## Full` headings absent): 471 documented-form entries, 145 names written in two or more files. The validator passed with 0 violations and 0 warnings: no form was left unbound for want of a place (`at`). It kept all 47 names of the floor, and its spot check found every sampled name.
- **Split-body cross-check (§1b):** the reader's cross-check found 19 mismatches between the SKILL.md body and `references/full-api-reference.md`, each a High `split-body-mismatch` gap (see the borderline call below).
- **Extraction (§2):** the recipe runner read the pinned tree in full: no fallback, no file read by eye or unread, no unresolved star re-export. The 8 `extractionGaps` names (`COGXRecord`, `COGX_VERSION`, `Drop`, `EXPORT_FORMATS`, `IMPORT_MODES`, `MemoryEntry`, `logger`, `session`) were read by eye at their file and line, and their documentation agrees with the source.
- **Signature comparison (§2, §2b):** 39 signature-judge subagents (one per `files[]` entry of the plan) judged 72 checks (67 with `bound` forms, 37 with alternatives, none with candidates) by `signature-comparison-rules.md`. `score` recorded 6 Critical `signature-mismatch` gaps (the six `cognee.tools` functions, form 2 of 2: the shared SKILL.md:181 form) and 2 Info `Annotation contradicted: run_tasks_parallel` observations (the body returns `Task(parallel_run)` at `cognee/modules/pipelines/operations/run_parallel.py:15` against the declared `Callable[...]`), with no warnings.
- **Stale names (§2c):** 53 documented names lie outside the enumerated surface. `classify-stale` marks none fabricated; the ledger records each as an Info documented extra or a Medium `stale-documentation` gap, by its rules.
- **Numerator (§2b):** skipped (no inflation signature: `stats.exports_documented` 86 ≠ the denominator).
- **Metadata counts (§4b):** a Medium `metadata-drift` finding (`stats.exports_public_api` 102 against `exports[]` 86, 16% drift) and an Info `multi-denominator` finding.
- **Provenance lines (§4c):** pass: 86 entries checked, 0 stale lines.

#### Borderline call: a namespace row's bare member list read as forms

- **Exports:** `list_data`, `has_data`, `empty_dataset`, `delete_data` (documented form at `SKILL.md:140`, the `cognee.datasets` row); `add_feedback`, `delete_feedback`, `distill_session` (`SKILL.md:147`, the `cognee.session` row); `create`, `get`, `delete`, `register`, `unregister`, `get_connection` (`SKILL.md:170`, the `cognee.agents` row); `register_sql_connection`, `remove_sql_connection`, `propose_sql_write`, `propose_corrections`, `apply_write_proposal`, `reject_write_proposal` (`SKILL.md:181`, the `cognee.tools` row).
- **Documented form:** each row's "Key params" cell lists the member names bare (`.list_data`, `.has_data`, …), states once that they take "an optional `user`" ("each but `get_status`/`get_progress` with an optional `user`", "each ending in an optional `user`", "each with an optional `user`"), and links to "[Signatures]" in `references/full-api-reference.md`. The reader recorded each member's form there as the shared text alone (`params: "each with an optional user; "`), partial by the "Key params" header.
- **Source declarations:** each takes a required parameter the shared form leaves out, for example `cognee/api/v1/datasets/datasets.py:139` `list_data(dataset_id: UUID, user: User | None = None)`, `cognee/api/v1/agents/agents.py:123` `get(agent_id: str | UUID, user: User | None = None)` and `cognee/api/v1/tools/tools.py:27` `register_sql_connection(name: str, connection_string: str, *, …, user: object | None = None)`. Every `references/full-api-reference.md` form (lines 226–231, 395–397, 417–424, 510–517) matches its declaration.
- **The sentence that left it open:** inventory-contract.md: "Where the skill documents several names and states members they share once, in the same place (a table row, a paragraph) …, each name's entry carries that shared text in its `params` …: the shared text first, then `; `, then the name's own members as the skill writes them, without the name, never the name's own members alone." It does not say whether a name a row lists bare, with no parameter list of its own and a link to its signatures elsewhere, is documented there in a form at all. signature-comparison-rules.md defines a mention only as a name written with empty parentheses, and the earlier no-subagent run read these rows as giving no form.
- **How this run counted it:** as forms, as the clause's wording requires. Under the split-body rule ("a form its own file labels partial … may leave out a parameter the other form does not state as required"), each member with a required parameter is a High `split-body-mismatch` gap (19). Under §2 (a mismatch with no `difference`), each of the six `cognee.tools` functions the surface holds is a Critical `signature-mismatch` gap (6). The `datasets`, `session` and `agents` members are not on the surface, so §2 compares none of them. The hard gate blocks on these gaps.
- **Split-body Sources:** for the six `cognee.tools` functions, the declaration `surface.json` records settles the call (the reference form agrees, SKILL.md:181's does not), so each Source is `SKILL.md:181`. `surface.json` records no declaration for the other 13 (namespace methods; for `delete` it records the top-level `cognee.delete`, a different export, which neither form matches), so by the rule no source settled them and their Source is the reference line. Each of those records says in its issue that the declaration, read by hand, agrees with the reference.

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)
**Migration Section:** Section 4b verification skipped: evidence-report.md pins no `t2_future_count`. For a skill create-skill made, re-run create-skill to regenerate the report with the field (create-stack-skill does not write it).

### Structural Findings

| # | Type | Severity | Detail | Line |
|---|------|----------|--------|------|
| - | none | - | Required sections present (description: `Overview` L21, usage: `Quick Start` L32, API surface: `Key API Summary` L127); 6 fences, balanced, each opening fence tagged; no table drift; no `scripts/` or `assets/` folder; every function and method export appears in the usage-family scope (145 checked, 0 unused); async/sync: the 27 exports an example calls agree with their descriptions (10 awaited, none described as sync; 17 not awaited, none described as async) | - |

**Structural Issues:** 0

### Reference Consistency (split-body)

| # | Reference File | Export | Issue | Other Side | Reference Line | Contradicted Side |
|---|---------------|--------|-------|------------|---------------|-------------------|
| 1 | references/full-api-reference.md | `list_data` | SKILL.md shows list_data only as each but get_status/get_progress with an optional user (partial), references/full-api-reference.md states dataset_id as required, which the SKILL.md form leaves out | SKILL.md:140 | 226 | not settled |
| 2 | references/full-api-reference.md | `has_data` | SKILL.md shows has_data only as each but get_status/get_progress with an optional user (partial), references/full-api-reference.md states dataset_id as required, which the SKILL.md form leaves out | SKILL.md:140 | 227 | not settled |
| 3 | references/full-api-reference.md | `empty_dataset` | SKILL.md shows empty_dataset only as each but get_status/get_progress with an optional user (partial), references/full-api-reference.md states dataset_id as required, which the SKILL.md form leaves out | SKILL.md:140 | 230 | not settled |
| 4 | references/full-api-reference.md | `delete_data` | SKILL.md shows delete_data only as each but get_status/get_progress with an optional user (partial), references/full-api-reference.md states dataset_id and data_id as required, which the SKILL.md form leaves out | SKILL.md:140 | 231 | not settled |
| 5 | references/full-api-reference.md | `add_feedback` | SKILL.md shows add_feedback only as each ending in an optional user (partial), references/full-api-reference.md states session_id and qa_id as required, which the SKILL.md form leaves out | SKILL.md:147 | 395 | not settled |
| 6 | references/full-api-reference.md | `delete_feedback` | SKILL.md shows delete_feedback only as each ending in an optional user (partial), references/full-api-reference.md states session_id and qa_id as required, which the SKILL.md form leaves out | SKILL.md:147 | 396 | not settled |
| 7 | references/full-api-reference.md | `distill_session` | SKILL.md shows distill_session only as each ending in an optional user (partial), references/full-api-reference.md states session_id and dataset as required, which the SKILL.md form leaves out | SKILL.md:147 | 397 | not settled |
| 8 | references/full-api-reference.md | `create` | SKILL.md shows create only as each with an optional user (partial), references/full-api-reference.md states name as required, which the SKILL.md form leaves out | SKILL.md:170 | 417 | not settled |
| 9 | references/full-api-reference.md | `get` | SKILL.md shows get only as each with an optional user (partial), references/full-api-reference.md states agent_id as required, which the SKILL.md form leaves out | SKILL.md:170 | 419 | not settled |
| 10 | references/full-api-reference.md | `delete` | SKILL.md shows delete only as each with an optional user (partial), references/full-api-reference.md states agent_id as required, which the SKILL.md form leaves out | SKILL.md:170 | 420 | not settled |
| 11 | references/full-api-reference.md | `register` | SKILL.md shows register only as each with an optional user (partial), references/full-api-reference.md states agent_session_name as required, which the SKILL.md form leaves out | SKILL.md:170 | 421 | not settled |
| 12 | references/full-api-reference.md | `unregister` | SKILL.md shows unregister only as each with an optional user (partial), references/full-api-reference.md states agent_session_name as required, which the SKILL.md form leaves out | SKILL.md:170 | 422 | not settled |
| 13 | references/full-api-reference.md | `get_connection` | SKILL.md shows get_connection only as each with an optional user (partial), references/full-api-reference.md states agent_id as required, which the SKILL.md form leaves out | SKILL.md:170 | 424 | not settled |
| 14 | references/full-api-reference.md | `register_sql_connection` | SKILL.md shows register_sql_connection only as each with an optional user (partial), references/full-api-reference.md states name and connection_string as required, which the SKILL.md form leaves out | SKILL.md:181 | 510 | SKILL.md |
| 15 | references/full-api-reference.md | `remove_sql_connection` | SKILL.md shows remove_sql_connection only as each with an optional user (partial), references/full-api-reference.md states name as required, which the SKILL.md form leaves out | SKILL.md:181 | 512 | SKILL.md |
| 16 | references/full-api-reference.md | `propose_sql_write` | SKILL.md shows propose_sql_write only as each with an optional user (partial), references/full-api-reference.md states connection and instruction as required, which the SKILL.md form leaves out | SKILL.md:181 | 513 | SKILL.md |
| 17 | references/full-api-reference.md | `propose_corrections` | SKILL.md shows propose_corrections only as each with an optional user (partial), references/full-api-reference.md states connection as required, which the SKILL.md form leaves out | SKILL.md:181 | 514 | SKILL.md |
| 18 | references/full-api-reference.md | `apply_write_proposal` | SKILL.md shows apply_write_proposal only as each with an optional user (partial), references/full-api-reference.md states proposal_id as required, which the SKILL.md form leaves out | SKILL.md:181 | 516 | SKILL.md |
| 19 | references/full-api-reference.md | `reject_write_proposal` | SKILL.md shows reject_write_proposal only as each with an optional user (partial), references/full-api-reference.md states proposal_id as required, which the SKILL.md form leaves out | SKILL.md:181 | 517 | SKILL.md |

**Exports Cross-Checked:** 145
**Mismatches Found:** 19

## External Validation

### skill-check
- **Available:** yes
- **Quality Score:** 90/100
- **Errors:** 0
- **Warnings:** 1
- **Diagnostics:** `body.max_tokens` (warn) at `SKILL.md:1`: body token estimate 5700 exceeds max 5000. Suggestion: reduce body to ~5000 tokens or fewer (token count is a whitespace-split approximation).

### Tessl Review
- **Result:** off — set tessl_review_workspace in preferences.yaml to enable

### Combined External Score
- **External Validation Score:** 90%
- **Tools used:** skill-check

## Completeness Score

**Result:** **FAIL**, not scored: the hard gate blocked this run on 25 Critical or High gap(s), listed first in the Gap Report.

## Gap Report

**Total Gaps:** 83
**Blocking (Critical + High):** 25
**Non-blocking (Medium + Low + Info):** 58

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|------------------|
| Critical | 6 | Read the source code and write or correct the documentation |
| High | 19 | Read the source code and write or correct the documentation |
| Medium | 4 | Add type definitions, interface docs or the missing section |
| Low | 1 | Add examples or metadata |
| Info | 53 | Optional improvements, no action required |
| **Total** | **83** | |

### GAP-001: Signature mismatch: register_sql_connection (form 2 of 2)

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** cognee/api/v1/tools/tools.py:27
**Export:** register_sql_connection

**Issue:** documented `each with an optional user; `, source `(name: str, connection_string: str, *, provider: str | None = None, allowed_tables: list[str] | None = None, max_rows: int | None = None, description: str | None = None, allow_writes: bool = False, user: object | None = None) -> dict[str, Any]`: form writes only the optional user and leaves out the required parameters 'name' and 'connection_string' (documented form 2 of 2: `(each with an optional user; )`)

**Remediation:** Update the documented signature of `register_sql_connection` from `each with an optional user; ` to `(name: str, connection_string: str, *, provider: str | None = None, allowed_tables: list[str] | None = None, max_rows: int | None = None, description: str | None = None, allow_writes: bool = False, user: object | None = None) -> dict[str, Any]`, the signature the source defines at `cognee/api/v1/tools/tools.py:27`.

### GAP-002: Signature mismatch: remove_sql_connection (form 2 of 2)

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** cognee/api/v1/tools/tools.py:73
**Export:** remove_sql_connection

**Issue:** documented `each with an optional user; `, source `(name: str, user: object | None = None) -> bool`: form writes only the optional user and leaves out the required parameter 'name' (documented form 2 of 2: `(each with an optional user; )`)

**Remediation:** Update the documented signature of `remove_sql_connection` from `each with an optional user; ` to `(name: str, user: object | None = None) -> bool`, the signature the source defines at `cognee/api/v1/tools/tools.py:73`.

### GAP-003: Signature mismatch: propose_sql_write (form 2 of 2)

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** cognee/api/v1/tools/tools.py:81
**Export:** propose_sql_write

**Issue:** documented `each with an optional user; `, source `(connection: str, instruction: str, *, evidence: dict[str, Any] | None = None, user: object | None = None) -> dict[str, Any]`: form writes only the optional user and leaves out the required parameters 'connection' and 'instruction' (documented form 2 of 2: `(each with an optional user; )`)

**Remediation:** Update the documented signature of `propose_sql_write` from `each with an optional user; ` to `(connection: str, instruction: str, *, evidence: dict[str, Any] | None = None, user: object | None = None) -> dict[str, Any]`, the signature the source defines at `cognee/api/v1/tools/tools.py:81`.

### GAP-004: Signature mismatch: propose_corrections (form 2 of 2)

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** cognee/api/v1/tools/tools.py:101
**Export:** propose_corrections

**Issue:** documented `each with an optional user; `, source `(connection: str, *, limit: int = 10, user: object | None = None) -> list[dict[str, Any]]`: form writes only the optional user and leaves out the required parameter 'connection' (documented form 2 of 2: `(each with an optional user; )`)

**Remediation:** Update the documented signature of `propose_corrections` from `each with an optional user; ` to `(connection: str, *, limit: int = 10, user: object | None = None) -> list[dict[str, Any]]`, the signature the source defines at `cognee/api/v1/tools/tools.py:101`.

### GAP-005: Signature mismatch: apply_write_proposal (form 2 of 2)

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** cognee/api/v1/tools/tools.py:129
**Export:** apply_write_proposal

**Issue:** documented `each with an optional user; `, source `(proposal_id, user: object | None = None) -> dict[str, Any]`: form writes only the optional user and leaves out the required parameter 'proposal_id' (documented form 2 of 2: `(each with an optional user; )`)

**Remediation:** Update the documented signature of `apply_write_proposal` from `each with an optional user; ` to `(proposal_id, user: object | None = None) -> dict[str, Any]`, the signature the source defines at `cognee/api/v1/tools/tools.py:129`.

### GAP-006: Signature mismatch: reject_write_proposal (form 2 of 2)

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** cognee/api/v1/tools/tools.py:146
**Export:** reject_write_proposal

**Issue:** documented `each with an optional user; `, source `(proposal_id, user: object | None = None) -> dict[str, Any]`: form writes only the optional user and leaves out the required parameter 'proposal_id' (documented form 2 of 2: `(each with an optional user; )`)

**Remediation:** Update the documented signature of `reject_write_proposal` from `each with an optional user; ` to `(proposal_id, user: object | None = None) -> dict[str, Any]`, the signature the source defines at `cognee/api/v1/tools/tools.py:146`.

### GAP-064: Split-body mismatch: list_data (references/full-api-reference.md)

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** references/full-api-reference.md:226
**Export:** list_data

**Issue:** SKILL.md:140 documents `cognee.datasets.list_data` with only the shared text of its row (an optional `user`) and no parameter list of its own, partial by the "Key params" header, leaving out the required `dataset_id`; references/full-api-reference.md:226 writes `(dataset_id, user=None)`. Read by hand (not by the Split-Body Sources rule, which reads only a declaration surface.json records), the declaration at `cognee/api/v1/datasets/datasets.py:139`, `list_data(dataset_id: UUID, user: User | None = None)`, agrees with references/full-api-reference.md:226 and contradicts SKILL.md:140.

**Remediation:** No source settled it: surface.json records no declaration of `cognee.datasets.list_data` (a namespace member, not a root export). Edit references/full-api-reference.md line 226, taking the form SKILL.md:140 writes for `list_data` (only the shared text of its row (an optional `user`) and no parameter list of its own); the two forms differ in the required `dataset_id`, which SKILL.md:140 leaves out and references/full-api-reference.md:226 writes.

### GAP-065: Split-body mismatch: has_data (references/full-api-reference.md)

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** references/full-api-reference.md:227
**Export:** has_data

**Issue:** SKILL.md:140 documents `cognee.datasets.has_data` with only the shared text of its row (an optional `user`) and no parameter list of its own, partial by the "Key params" header, leaving out the required `dataset_id`; references/full-api-reference.md:227 writes `(dataset_id, user=None) -> bool`. Read by hand (not by the Split-Body Sources rule, which reads only a declaration surface.json records), the declaration at `cognee/api/v1/datasets/datasets.py:160`, `has_data(dataset_id: str, user: User | None = None) -> bool`, agrees with references/full-api-reference.md:227 and contradicts SKILL.md:140.

**Remediation:** No source settled it: surface.json records no declaration of `cognee.datasets.has_data` (a namespace member, not a root export). Edit references/full-api-reference.md line 227, taking the form SKILL.md:140 writes for `has_data` (only the shared text of its row (an optional `user`) and no parameter list of its own); the two forms differ in the required `dataset_id`, which SKILL.md:140 leaves out and references/full-api-reference.md:227 writes.

### GAP-066: Split-body mismatch: empty_dataset (references/full-api-reference.md)

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** references/full-api-reference.md:230
**Export:** empty_dataset

**Issue:** SKILL.md:140 documents `cognee.datasets.empty_dataset` with only the shared text of its row (an optional `user`) and no parameter list of its own, partial by the "Key params" header, leaving out the required `dataset_id`; references/full-api-reference.md:230 writes `(dataset_id, user=None)`. Read by hand (not by the Split-Body Sources rule, which reads only a declaration surface.json records), the declaration at `cognee/api/v1/datasets/datasets.py:184`, `empty_dataset(dataset_id: UUID, user: User | None = None)`, agrees with references/full-api-reference.md:230 and contradicts SKILL.md:140.

**Remediation:** No source settled it: surface.json records no declaration of `cognee.datasets.empty_dataset` (a namespace member, not a root export). Edit references/full-api-reference.md line 230, taking the form SKILL.md:140 writes for `empty_dataset` (only the shared text of its row (an optional `user`) and no parameter list of its own); the two forms differ in the required `dataset_id`, which SKILL.md:140 leaves out and references/full-api-reference.md:230 writes.

### GAP-067: Split-body mismatch: delete_data (references/full-api-reference.md)

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** references/full-api-reference.md:231
**Export:** delete_data

**Issue:** SKILL.md:140 documents `cognee.datasets.delete_data` with only the shared text of its row (an optional `user`) and no parameter list of its own, partial by the "Key params" header, leaving out the required `dataset_id` and `data_id`; references/full-api-reference.md:231 writes `(dataset_id, data_id, user=None, mode="soft", delete_dataset_if_empty=False)`. Read by hand (not by the Split-Body Sources rule, which reads only a declaration surface.json records), the declaration at `cognee/api/v1/datasets/datasets.py:218`, `delete_data(dataset_id: UUID, data_id: UUID, user: User | None = None, ...)`, agrees with references/full-api-reference.md:231 and contradicts SKILL.md:140.

**Remediation:** No source settled it: surface.json records no declaration of `cognee.datasets.delete_data` (a namespace member, not a root export). Edit references/full-api-reference.md line 231, taking the form SKILL.md:140 writes for `delete_data` (only the shared text of its row (an optional `user`) and no parameter list of its own); the two forms differ in the required `dataset_id` and `data_id`, which SKILL.md:140 leaves out and references/full-api-reference.md:231 writes.

### GAP-068: Split-body mismatch: add_feedback (references/full-api-reference.md)

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** references/full-api-reference.md:395
**Export:** add_feedback

**Issue:** SKILL.md:147 documents `cognee.session.add_feedback` with only the shared text of its row (an optional `user`) and no parameter list of its own, partial by the "Key params" header, leaving out the required `session_id` and `qa_id`; references/full-api-reference.md:395 writes `add_feedback(session_id: str, qa_id: str, feedback_text: str | None = None, feedback_score: int | None = None, user: User | None = None) -> bool`. Read by hand (not by the Split-Body Sources rule, which reads only a declaration surface.json records), the declaration at `cognee/api/v1/session/session.py:113`, `add_feedback(session_id: str, qa_id: str, feedback_text: str | None = None, feedback_score: int | None = None, user: User | None = None) -> bool`, agrees with references/full-api-reference.md:395 and contradicts SKILL.md:147.

**Remediation:** No source settled it: surface.json records no declaration of `cognee.session.add_feedback` (a namespace member, not a root export). Edit references/full-api-reference.md line 395, taking the form SKILL.md:147 writes for `add_feedback` (only the shared text of its row (an optional `user`) and no parameter list of its own); the two forms differ in the required `session_id` and `qa_id`, which SKILL.md:147 leaves out and references/full-api-reference.md:395 writes.

### GAP-069: Split-body mismatch: delete_feedback (references/full-api-reference.md)

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** references/full-api-reference.md:396
**Export:** delete_feedback

**Issue:** SKILL.md:147 documents `cognee.session.delete_feedback` with only the shared text of its row (an optional `user`) and no parameter list of its own, partial by the "Key params" header, leaving out the required `session_id` and `qa_id`; references/full-api-reference.md:396 writes `delete_feedback(session_id: str, qa_id: str, user: User | None = None) -> bool`. Read by hand (not by the Split-Body Sources rule, which reads only a declaration surface.json records), the declaration at `cognee/api/v1/session/session.py:147`, `delete_feedback(session_id: str, qa_id: str, user: User | None = None) -> bool`, agrees with references/full-api-reference.md:396 and contradicts SKILL.md:147.

**Remediation:** No source settled it: surface.json records no declaration of `cognee.session.delete_feedback` (a namespace member, not a root export). Edit references/full-api-reference.md line 396, taking the form SKILL.md:147 writes for `delete_feedback` (only the shared text of its row (an optional `user`) and no parameter list of its own); the two forms differ in the required `session_id` and `qa_id`, which SKILL.md:147 leaves out and references/full-api-reference.md:396 writes.

### GAP-070: Split-body mismatch: distill_session (references/full-api-reference.md)

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** references/full-api-reference.md:397
**Export:** distill_session

**Issue:** SKILL.md:147 documents `cognee.session.distill_session` with only the shared text of its row (an optional `user`) and no parameter list of its own, partial by the "Key params" header, leaving out the required `session_id` and `dataset`; references/full-api-reference.md:397 writes `distill_session(session_id: str, dataset: str | UUID, user: User | None = None) -> DistillationResult`. Read by hand (not by the Split-Body Sources rule, which reads only a declaration surface.json records), the declaration at `cognee/modules/session_distillation/distill.py:471`, `distill_session(session_id: str, dataset: str | UUID, user: User | None = None) -> DistillationResult`, agrees with references/full-api-reference.md:397 and contradicts SKILL.md:147.

**Remediation:** No source settled it: surface.json records no declaration of `cognee.session.distill_session` (a namespace member, not a root export). Edit references/full-api-reference.md line 397, taking the form SKILL.md:147 writes for `distill_session` (only the shared text of its row (an optional `user`) and no parameter list of its own); the two forms differ in the required `session_id` and `dataset`, which SKILL.md:147 leaves out and references/full-api-reference.md:397 writes.

### GAP-071: Split-body mismatch: create (references/full-api-reference.md)

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** references/full-api-reference.md:417
**Export:** create

**Issue:** SKILL.md:170 documents `cognee.agents.create` with only the shared text of its row (an optional `user`) and no parameter list of its own, partial by the "Key params" header, leaving out the required `name`; references/full-api-reference.md:417 writes `(name: str, datasets: list[str | UUID] | None = None, user=None) -> dict`. Read by hand (not by the Split-Body Sources rule, which reads only a declaration surface.json records), the declaration at `cognee/api/v1/agents/agents.py:64`, `create(name: str, datasets: list[str | UUID] | None = None, user: User | None = None) -> dict`, agrees with references/full-api-reference.md:417 and contradicts SKILL.md:170.

**Remediation:** No source settled it: surface.json records no declaration of `cognee.agents.create` (a namespace member, not a root export). Edit references/full-api-reference.md line 417, taking the form SKILL.md:170 writes for `create` (only the shared text of its row (an optional `user`) and no parameter list of its own); the two forms differ in the required `name`, which SKILL.md:170 leaves out and references/full-api-reference.md:417 writes.

### GAP-072: Split-body mismatch: get (references/full-api-reference.md)

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** references/full-api-reference.md:419
**Export:** get

**Issue:** SKILL.md:170 documents `cognee.agents.get` with only the shared text of its row (an optional `user`) and no parameter list of its own, partial by the "Key params" header, leaving out the required `agent_id`; references/full-api-reference.md:419 writes `(agent_id: str | UUID, user=None) -> dict`. Read by hand (not by the Split-Body Sources rule, which reads only a declaration surface.json records), the declaration at `cognee/api/v1/agents/agents.py:123`, `get(agent_id: str | UUID, user: User | None = None) -> dict`, agrees with references/full-api-reference.md:419 and contradicts SKILL.md:170.

**Remediation:** No source settled it: surface.json records no declaration of `cognee.agents.get` (a namespace member, not a root export). Edit references/full-api-reference.md line 419, taking the form SKILL.md:170 writes for `get` (only the shared text of its row (an optional `user`) and no parameter list of its own); the two forms differ in the required `agent_id`, which SKILL.md:170 leaves out and references/full-api-reference.md:419 writes.

### GAP-073: Split-body mismatch: delete (references/full-api-reference.md)

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** references/full-api-reference.md:420
**Export:** delete

**Issue:** SKILL.md:170 documents `cognee.agents.delete` with only the shared text of its row (an optional `user`) and no parameter list of its own, partial by the "Key params" header, leaving out the required `agent_id`; references/full-api-reference.md:420 writes `(agent_id: str | UUID, user=None) -> None`. Read by hand (not by the Split-Body Sources rule, which reads only a declaration surface.json records), the declaration at `cognee/api/v1/agents/agents.py:143`, `delete(agent_id: str | UUID, user: User | None = None) -> None`, agrees with references/full-api-reference.md:420 and contradicts SKILL.md:170.

**Remediation:** No source settled it: surface.json records no declaration of `cognee.agents.delete`: its only `delete` record is the top-level `cognee.delete` (cognee/api/v1/delete/__init__.py:12), a different export that neither form matches. Edit references/full-api-reference.md line 420, taking the form SKILL.md:170 writes for `delete` (only the shared text of its row (an optional `user`) and no parameter list of its own); the two forms differ in the required `agent_id`, which SKILL.md:170 leaves out and references/full-api-reference.md:420 writes.

### GAP-074: Split-body mismatch: register (references/full-api-reference.md)

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** references/full-api-reference.md:421
**Export:** register

**Issue:** SKILL.md:170 documents `cognee.agents.register` with only the shared text of its row (an optional `user`) and no parameter list of its own, partial by the "Key params" header, leaving out the required `agent_session_name`; references/full-api-reference.md:421 writes `(agent_session_name: str, user=None, type="api", memory_mode="unknown", ...) -> dict`. Read by hand (not by the Split-Body Sources rule, which reads only a declaration surface.json records), the declaration at `cognee/api/v1/agents/agents.py:157`, `register(agent_session_name: str, user: User | None = None, type="api", ...)`, agrees with references/full-api-reference.md:421 and contradicts SKILL.md:170.

**Remediation:** No source settled it: surface.json records no declaration of `cognee.agents.register` (a namespace member, not a root export). Edit references/full-api-reference.md line 421, taking the form SKILL.md:170 writes for `register` (only the shared text of its row (an optional `user`) and no parameter list of its own); the two forms differ in the required `agent_session_name`, which SKILL.md:170 leaves out and references/full-api-reference.md:421 writes.

### GAP-075: Split-body mismatch: unregister (references/full-api-reference.md)

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** references/full-api-reference.md:422
**Export:** unregister

**Issue:** SKILL.md:170 documents `cognee.agents.unregister` with only the shared text of its row (an optional `user`) and no parameter list of its own, partial by the "Key params" header, leaving out the required `agent_session_name`; references/full-api-reference.md:422 writes `(agent_session_name: str, user=None) -> int`. Read by hand (not by the Split-Body Sources rule, which reads only a declaration surface.json records), the declaration at `cognee/api/v1/agents/agents.py:204`, `unregister(agent_session_name: str, user: User | None = None) -> int`, agrees with references/full-api-reference.md:422 and contradicts SKILL.md:170.

**Remediation:** No source settled it: surface.json records no declaration of `cognee.agents.unregister` (a namespace member, not a root export). Edit references/full-api-reference.md line 422, taking the form SKILL.md:170 writes for `unregister` (only the shared text of its row (an optional `user`) and no parameter list of its own); the two forms differ in the required `agent_session_name`, which SKILL.md:170 leaves out and references/full-api-reference.md:422 writes.

### GAP-076: Split-body mismatch: get_connection (references/full-api-reference.md)

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** references/full-api-reference.md:424
**Export:** get_connection

**Issue:** SKILL.md:170 documents `cognee.agents.get_connection` with only the shared text of its row (an optional `user`) and no parameter list of its own, partial by the "Key params" header, leaving out the required `agent_id`; references/full-api-reference.md:424 writes `(agent_id: str | UUID, user=None, agent_session_name=None) -> dict | None`. Read by hand (not by the Split-Body Sources rule, which reads only a declaration surface.json records), the declaration at `cognee/api/v1/agents/agents.py:256`, `get_connection(agent_id: str | UUID, user: User | None = None, agent_session_name: str | None = None) -> dict | None`, agrees with references/full-api-reference.md:424 and contradicts SKILL.md:170.

**Remediation:** No source settled it: surface.json records no declaration of `cognee.agents.get_connection` (a namespace member, not a root export). Edit references/full-api-reference.md line 424, taking the form SKILL.md:170 writes for `get_connection` (only the shared text of its row (an optional `user`) and no parameter list of its own); the two forms differ in the required `agent_id`, which SKILL.md:170 leaves out and references/full-api-reference.md:424 writes.

### GAP-077: Split-body mismatch: register_sql_connection (references/full-api-reference.md)

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** SKILL.md:181
**Export:** register_sql_connection

**Issue:** SKILL.md:181 documents `cognee.tools.register_sql_connection` with only the shared text of its row (an optional `user`) and no parameter list of its own, partial by the "Key params" header, leaving out the required `name` and `connection_string`; references/full-api-reference.md:510 writes `(name: str, connection_string: str, *, provider: str | None = None, allowed_tables: list[str] | None = None, max_rows: int | None = None, description: str | None = None, allow_writes: bool = False, user: object | None = None) -> dict[str, Any]`. The declaration surface.json records at `cognee/api/v1/tools/tools.py:27`, `register_sql_connection(name: str, connection_string: str, *, provider: str | None = None, allowed_tables: list[str] | None = None, max_rows: int | None = None, description: str | None = None, allow_writes: bool = False, user: object | None = None) -> dict[str, Any]`, agrees with references/full-api-reference.md:510 and contradicts SKILL.md:181.

**Remediation:** Edit SKILL.md line 181 (the `cognee.tools` row): give `register_sql_connection` the form references/full-api-reference.md:510 writes, `(name: str, connection_string: str, *, provider: str | None = None, allowed_tables: list[str] | None = None, max_rows: int | None = None, description: str | None = None, allow_writes: bool = False, user: object | None = None) -> dict[str, Any]`, which matches the source declaration at `cognee/api/v1/tools/tools.py:27`. The row's shared form ("each with an optional `user`") leaves out the required `name` and `connection_string`.

### GAP-078: Split-body mismatch: remove_sql_connection (references/full-api-reference.md)

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** SKILL.md:181
**Export:** remove_sql_connection

**Issue:** SKILL.md:181 documents `cognee.tools.remove_sql_connection` with only the shared text of its row (an optional `user`) and no parameter list of its own, partial by the "Key params" header, leaving out the required `name`; references/full-api-reference.md:512 writes `(name: str, user: object | None = None) -> bool`. The declaration surface.json records at `cognee/api/v1/tools/tools.py:73`, `remove_sql_connection(name: str, user: object | None = None) -> bool`, agrees with references/full-api-reference.md:512 and contradicts SKILL.md:181.

**Remediation:** Edit SKILL.md line 181 (the `cognee.tools` row): give `remove_sql_connection` the form references/full-api-reference.md:512 writes, `(name: str, user: object | None = None) -> bool`, which matches the source declaration at `cognee/api/v1/tools/tools.py:73`. The row's shared form ("each with an optional `user`") leaves out the required `name`.

### GAP-079: Split-body mismatch: propose_sql_write (references/full-api-reference.md)

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** SKILL.md:181
**Export:** propose_sql_write

**Issue:** SKILL.md:181 documents `cognee.tools.propose_sql_write` with only the shared text of its row (an optional `user`) and no parameter list of its own, partial by the "Key params" header, leaving out the required `connection` and `instruction`; references/full-api-reference.md:513 writes `(connection: str, instruction: str, *, evidence: dict[str, Any] | None = None, user: object | None = None) -> dict[str, Any]`. The declaration surface.json records at `cognee/api/v1/tools/tools.py:81`, `propose_sql_write(connection: str, instruction: str, *, evidence: dict[str, Any] | None = None, user: object | None = None) -> dict[str, Any]`, agrees with references/full-api-reference.md:513 and contradicts SKILL.md:181.

**Remediation:** Edit SKILL.md line 181 (the `cognee.tools` row): give `propose_sql_write` the form references/full-api-reference.md:513 writes, `(connection: str, instruction: str, *, evidence: dict[str, Any] | None = None, user: object | None = None) -> dict[str, Any]`, which matches the source declaration at `cognee/api/v1/tools/tools.py:81`. The row's shared form ("each with an optional `user`") leaves out the required `connection` and `instruction`.

### GAP-080: Split-body mismatch: propose_corrections (references/full-api-reference.md)

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** SKILL.md:181
**Export:** propose_corrections

**Issue:** SKILL.md:181 documents `cognee.tools.propose_corrections` with only the shared text of its row (an optional `user`) and no parameter list of its own, partial by the "Key params" header, leaving out the required `connection`; references/full-api-reference.md:514 writes `(connection: str, *, limit: int = 10, user: object | None = None) -> list[dict[str, Any]]`. The declaration surface.json records at `cognee/api/v1/tools/tools.py:101`, `propose_corrections(connection: str, *, limit: int = 10, user: object | None = None) -> list[dict[str, Any]]`, agrees with references/full-api-reference.md:514 and contradicts SKILL.md:181.

**Remediation:** Edit SKILL.md line 181 (the `cognee.tools` row): give `propose_corrections` the form references/full-api-reference.md:514 writes, `(connection: str, *, limit: int = 10, user: object | None = None) -> list[dict[str, Any]]`, which matches the source declaration at `cognee/api/v1/tools/tools.py:101`. The row's shared form ("each with an optional `user`") leaves out the required `connection`.

### GAP-081: Split-body mismatch: apply_write_proposal (references/full-api-reference.md)

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** SKILL.md:181
**Export:** apply_write_proposal

**Issue:** SKILL.md:181 documents `cognee.tools.apply_write_proposal` with only the shared text of its row (an optional `user`) and no parameter list of its own, partial by the "Key params" header, leaving out the required `proposal_id`; references/full-api-reference.md:516 writes `(proposal_id, user: object | None = None) -> dict[str, Any]`. The declaration surface.json records at `cognee/api/v1/tools/tools.py:129`, `apply_write_proposal(proposal_id, user: object | None = None) -> dict[str, Any]`, agrees with references/full-api-reference.md:516 and contradicts SKILL.md:181.

**Remediation:** Edit SKILL.md line 181 (the `cognee.tools` row): give `apply_write_proposal` the form references/full-api-reference.md:516 writes, `(proposal_id, user: object | None = None) -> dict[str, Any]`, which matches the source declaration at `cognee/api/v1/tools/tools.py:129`. The row's shared form ("each with an optional `user`") leaves out the required `proposal_id`.

### GAP-082: Split-body mismatch: reject_write_proposal (references/full-api-reference.md)

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** SKILL.md:181
**Export:** reject_write_proposal

**Issue:** SKILL.md:181 documents `cognee.tools.reject_write_proposal` with only the shared text of its row (an optional `user`) and no parameter list of its own, partial by the "Key params" header, leaving out the required `proposal_id`; references/full-api-reference.md:517 writes `(proposal_id, user: object | None = None) -> dict[str, Any]`. The declaration surface.json records at `cognee/api/v1/tools/tools.py:146`, `reject_write_proposal(proposal_id, user: object | None = None) -> dict[str, Any]`, agrees with references/full-api-reference.md:517 and contradicts SKILL.md:181.

**Remediation:** Edit SKILL.md line 181 (the `cognee.tools` row): give `reject_write_proposal` the form references/full-api-reference.md:517 writes, `(proposal_id, user: object | None = None) -> dict[str, Any]`, which matches the source declaration at `cognee/api/v1/tools/tools.py:146`. The row's shared form ("each with an optional `user`") leaves out the required `proposal_id`.

### GAP-049: Stale documentation: run_migrations

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:29
**Export:** run_migrations

**Issue:** `SKILL.md:29` documents `run_migrations`, which the entry point `cognee/__init__.py` exports and `cognee/run_migrations.py:18` defines, a file `forge-data/oms-cognee/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `run_migrations` belongs on the surface: `forge-data/oms-cognee/skill-brief.yaml` scopes out `cognee/run_migrations.py:18`, where it is defined, since no `scope.include` glob covers that file and its `scope.exclude` glob `cognee/run_migrations.py` matches it. To keep its documentation, widen `scope.include` to cover that file and narrow `cognee/run_migrations.py` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `run_migrations` at SKILL.md:29.

### GAP-052: Stale documentation: setup_logging

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:28
**Export:** setup_logging

**Issue:** `SKILL.md:28` documents `setup_logging`, which the entry point `cognee/__init__.py` exports and `cognee/shared/logging_utils.py:345` defines, a file `forge-data/oms-cognee/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `setup_logging` belongs on the surface: `forge-data/oms-cognee/skill-brief.yaml` scopes out `cognee/shared/logging_utils.py:345`, where it is defined, since no `scope.include` glob covers that file and its `scope.exclude` glob `cognee/shared/**` matches it. To keep its documentation, widen `scope.include` to cover that file and narrow `cognee/shared/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `setup_logging` at SKILL.md:28.

### GAP-061: Stale documentation: wait_for_background_tasks

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/full-api-reference.md:622
**Export:** wait_for_background_tasks

**Issue:** `references/full-api-reference.md:622` documents `wait_for_background_tasks`, which the entry point `cognee/__init__.py` exports and `cognee/infrastructure/background_tasks.py:66` defines, a file `forge-data/oms-cognee/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `wait_for_background_tasks` belongs on the surface: `forge-data/oms-cognee/skill-brief.yaml` scopes out `cognee/infrastructure/background_tasks.py:66`, where it is defined, since no `scope.include` glob covers that file and its `scope.exclude` glob `cognee/infrastructure/**` matches it. To keep its documentation, widen `scope.include` to cover that file and narrow `cognee/infrastructure/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `wait_for_background_tasks` at references/full-api-reference.md:622.

### GAP-062: metadata drift — barrel export counts diverge

**Severity:** Medium
**Category:** Coverage (metadata-drift)
**Source:** skills/oms-cognee/1.6.2/oms-cognee/metadata.json

**Issue:** stats.exports_public_api=102, exports[].length=86 → 16% drift

**Remediation:** Re-run Create Skill, which rebuilds `exports[]` and `stats.exports_public_api` in `skills/oms-cognee/1.6.2/oms-cognee/metadata.json` from the source. Update Skill does not repair this drift: each time it writes the skill it recounts `stats.exports_public_api` from the source and keeps `exports[]`, adding or dropping only the names its provenance map changes, so a metadata patch does not hold.

### GAP-083: skill-check: body.max_tokens

**Severity:** Low
**Category:** External (external-validator)
**Source:** SKILL.md:1

**Issue:** body token estimate 5700 exceeds max 5000

**Remediation:** Reduce the SKILL.md body to about 5000 tokens or fewer (skill-check estimates 5700, by whitespace split), moving detail into the references/ files the body already links.

### GAP-007: Annotation contradicted: run_tasks_parallel (form 1 of 3)

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/operations/run_parallel.py:8
**Export:** run_tasks_parallel

**Issue:** the source annotates the return of `run_tasks_parallel` otherwise than the skill documents, and its body returns the documented type at `cognee/modules/pipelines/operations/run_parallel.py:15`: documented `(tasks) -> Task`, source `(tasks: list[Task]) -> Callable[[Any], Generator[Any, Any, Any]]`: documented return type 'Task' contradicts the declared annotation 'Callable[[Any], Generator[Any, Any, Any]]', but the body returns Task(parallel_run) at line 15 (documented form 1 of 3: `(tasks) -> Task`)

**Remediation:** No change to the skill: it documents what `run_tasks_parallel` returns, as `cognee/modules/pipelines/operations/run_parallel.py:15` shows. Report the return annotation at `cognee/modules/pipelines/operations/run_parallel.py:8` upstream, since the body contradicts it.

### GAP-008: Annotation contradicted: run_tasks_parallel (form 2 of 3)

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/operations/run_parallel.py:8
**Export:** run_tasks_parallel

**Issue:** the source annotates the return of `run_tasks_parallel` otherwise than the skill documents, and its body returns the documented type at `cognee/modules/pipelines/operations/run_parallel.py:15`: documented `(tasks: list[Task]) -> Task`, source `(tasks: list[Task]) -> Callable[[Any], Generator[Any, Any, Any]]`: documented return type 'Task' contradicts the declared annotation 'Callable[[Any], Generator[Any, Any, Any]]', but the body returns Task(parallel_run) at line 15 (documented form 2 of 3: `(tasks: list[Task]) -> Task`)

**Remediation:** No change to the skill: it documents what `run_tasks_parallel` returns, as `cognee/modules/pipelines/operations/run_parallel.py:15` shows. Report the return annotation at `cognee/modules/pipelines/operations/run_parallel.py:8` upstream, since the body contradicts it.

### GAP-009: Documented extra: BoundTask

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/tasks/task.py:8
**Export:** BoundTask

**Issue:** `SKILL.md:224` documents `BoundTask`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `BoundTask` is a documented extra, a name the source still declares at `cognee/modules/pipelines/tasks/task.py:8` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-010: Documented extra: CogneeApiError

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/exceptions.py:10
**Export:** CogneeApiError

**Issue:** `SKILL.md:288` documents `CogneeApiError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CogneeApiError` is a documented extra, a name the source still declares at `cognee/exceptions/exceptions.py:10` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-011: Documented extra: CogneeConfigurationError

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/exceptions.py:99
**Export:** CogneeConfigurationError

**Issue:** `SKILL.md:110` documents `CogneeConfigurationError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CogneeConfigurationError` is a documented extra, a name the source still declares at `cognee/exceptions/exceptions.py:99` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-012: Documented extra: CogneeSystemError

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/exceptions.py:69
**Export:** CogneeSystemError

**Issue:** `SKILL.md:289` documents `CogneeSystemError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CogneeSystemError` is a documented extra, a name the source still declares at `cognee/exceptions/exceptions.py:69` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-013: Documented extra: CogneeTransientError

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/exceptions.py:114
**Export:** CogneeTransientError

**Issue:** `SKILL.md:292` documents `CogneeTransientError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CogneeTransientError` is a documented extra, a name the source still declares at `cognee/exceptions/exceptions.py:114` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-014: Documented extra: CogneeValidationError

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/exceptions.py:84
**Export:** CogneeValidationError

**Issue:** `SKILL.md:227` documents `CogneeValidationError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CogneeValidationError` is a documented extra, a name the source still declares at `cognee/exceptions/exceptions.py:84` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-015: Documented extra: DataPoint

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/low_level.py:2
**Export:** DataPoint

**Issue:** `SKILL.md:282` documents `DataPoint`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `DataPoint` is a documented extra, a name the source still declares at `cognee/low_level.py:2` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-016: Documented extra: Dedup

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/infrastructure/engine/models/FieldAnnotations.py:82
**Export:** Dedup

**Issue:** `references/pipelines-and-datapoints.md:337` documents `Dedup`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Dedup` is a documented extra, a name the source still declares at `cognee/infrastructure/engine/models/FieldAnnotations.py:82` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-017: Documented extra: DistillationResult

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/session_distillation/models.py:94
**Export:** DistillationResult

**Issue:** `SKILL.md:147` documents `DistillationResult`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `DistillationResult` is a documented extra, a name the source still declares at `cognee/modules/session_distillation/models.py:94` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-018: Documented extra: Edge

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/infrastructure/engine/models/Edge.py:13
**Export:** Edge

**Issue:** `SKILL.md:221` documents `Edge`, which the enumerated source API surface lacks and the source still declares; of the 5 files that declare it, the skill cites only `cognee/infrastructure/engine/models/Edge.py`

**Remediation:** No change: `Edge` is a documented extra, a name the source still declares at `cognee/infrastructure/engine/models/Edge.py:13` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-019: Documented extra: Embeddable

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/infrastructure/engine/models/FieldAnnotations.py:56
**Export:** Embeddable

**Issue:** `references/pipelines-and-datapoints.md:337` documents `Embeddable`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Embeddable` is a documented extra, a name the source still declares at `cognee/infrastructure/engine/models/FieldAnnotations.py:56` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-020: Documented extra: EntitySpec

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/graph_models/spec.py:90
**Export:** EntitySpec

**Issue:** `references/full-api-reference.md:282` documents `EntitySpec`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `EntitySpec` is a documented extra, a name the source still declares at `cognee/modules/graph_models/spec.py:90` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-021: Documented extra: FromIdentity

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/infrastructure/engine/models/FieldAnnotations.py:95
**Export:** FromIdentity

**Issue:** `SKILL.md:221` documents `FromIdentity`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `FromIdentity` is a documented extra, a name the source still declares at `cognee/infrastructure/engine/models/FieldAnnotations.py:95` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-022: Documented extra: GraphSchemaSpec

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/graph_models/spec.py:108
**Export:** GraphSchemaSpec

**Issue:** `references/full-api-reference.md:282` documents `GraphSchemaSpec`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `GraphSchemaSpec` is a documented extra, a name the source still declares at `cognee/modules/graph_models/spec.py:108` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-023: Documented extra: ImproveKwargs

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/improve/improve.py:88
**Export:** ImproveKwargs

**Issue:** `SKILL.md:159` documents `ImproveKwargs`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ImproveKwargs` is a documented extra, a name the source still declares at `cognee/api/v1/improve/improve.py:88` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-024: Documented extra: ImproveResult

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/improve/result.py:187
**Export:** ImproveResult

**Issue:** `SKILL.md:104` documents `ImproveResult`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ImproveResult` is a documented extra, a name the source still declares at `cognee/modules/improve/result.py:187` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-025: Documented extra: LLMGateway

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/infrastructure/llm/LLMGateway.py:106
**Export:** LLMGateway

**Issue:** `references/pipelines-and-datapoints.md:418` documents `LLMGateway`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LLMGateway` is a documented extra, a name the source still declares at `cognee/infrastructure/llm/LLMGateway.py:106` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-026: Documented extra: PipelineRunCompleted

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/models/PipelineRunInfo.py:34
**Export:** PipelineRunCompleted

**Issue:** `references/full-api-reference.md:267` documents `PipelineRunCompleted`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PipelineRunCompleted` is a documented extra, a name the source still declares at `cognee/modules/pipelines/models/PipelineRunInfo.py:34` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-027: Documented extra: PipelineRunErrored

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/models/PipelineRunInfo.py:42
**Export:** PipelineRunErrored

**Issue:** `references/core-workflow.md:100` documents `PipelineRunErrored`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PipelineRunErrored` is a documented extra, a name the source still declares at `cognee/modules/pipelines/models/PipelineRunInfo.py:42` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-028: Documented extra: PipelineRunInfo

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/models/PipelineRunInfo.py:9
**Export:** PipelineRunInfo

**Issue:** `references/full-api-reference.md:566` documents `PipelineRunInfo`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PipelineRunInfo` is a documented extra, a name the source still declares at `cognee/modules/pipelines/models/PipelineRunInfo.py:9` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-029: Documented extra: PipelineRunStarted

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/models/PipelineRunInfo.py:26
**Export:** PipelineRunStarted

**Issue:** `references/full-api-reference.md:267` documents `PipelineRunStarted`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PipelineRunStarted` is a documented extra, a name the source still declares at `cognee/modules/pipelines/models/PipelineRunInfo.py:26` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-030: Documented extra: REMEDIATION_MARKER

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/remediation.py:52
**Export:** REMEDIATION_MARKER

**Issue:** `SKILL.md:294` documents `REMEDIATION_MARKER`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `REMEDIATION_MARKER` is a documented extra, a name the source still declares at `cognee/exceptions/remediation.py:52` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-031: Documented extra: RememberKwargs

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/remember/remember.py:90
**Export:** RememberKwargs

**Issue:** `SKILL.md:156` documents `RememberKwargs`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `RememberKwargs` is a documented extra, a name the source still declares at `cognee/api/v1/remember/remember.py:90` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-032: Documented extra: SkillRunEntry

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/memory/entries.py:82
**Export:** SkillRunEntry

**Issue:** `SKILL.md:280` documents `SkillRunEntry`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `SkillRunEntry` is a documented extra, a name the source still declares at `cognee/memory/entries.py:82` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-033: Documented extra: TaskSpec

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/tasks/task.py:35
**Export:** TaskSpec

**Issue:** `references/pipelines-and-datapoints.md:36` documents `TaskSpec`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `TaskSpec` is a documented extra, a name the source still declares at `cognee/modules/pipelines/tasks/task.py:35` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-034: Documented extra: UpdateResult

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/update/result.py:37
**Export:** UpdateResult

**Issue:** `references/core-workflow.md:390` documents `UpdateResult`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `UpdateResult` is a documented extra, a name the source still declares at `cognee/api/v1/update/result.py:37` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-035: Documented extra: __version__

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/__init__.py:22
**Export:** __version__

**Issue:** `SKILL.md:28` documents `__version__`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `__version__` is a documented extra, a name the source still declares at `cognee/__init__.py:22` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-036: Documented extra: add_data_points

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/tasks/storage/add_data_points.py:70
**Export:** add_data_points

**Issue:** `references/core-workflow.md:199` documents `add_data_points`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `add_data_points` is a documented extra, a name the source still declares at `cognee/tasks/storage/add_data_points.py:70` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-037: Documented extra: find_remediation

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/remediation.py:131
**Export:** find_remediation

**Issue:** `SKILL.md:294` documents `find_remediation`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `find_remediation` is a documented extra, a name the source still declares at `cognee/exceptions/remediation.py:131` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-038: Documented extra: get_default_tasks

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/cognify/cognify.py:565
**Export:** get_default_tasks

**Issue:** `references/core-workflow.md:183` documents `get_default_tasks`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_default_tasks` is a documented extra, a name the source still declares at `cognee/api/v1/cognify/cognify.py:565` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-039: Documented extra: get_errored_run_info

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/models/PipelineRunInfo.py:62
**Export:** get_errored_run_info

**Issue:** `references/full-api-reference.md:574` documents `get_errored_run_info`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_errored_run_info` is a documented extra, a name the source still declares at `cognee/modules/pipelines/models/PipelineRunInfo.py:62` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-040: Documented extra: graph_model_from_spec

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/graph_models/compiler.py:135
**Export:** graph_model_from_spec

**Issue:** `references/full-api-reference.md:282` documents `graph_model_from_spec`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `graph_model_from_spec` is a documented extra, a name the source still declares at `cognee/modules/graph_models/compiler.py:135` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-041: Documented extra: graph_model_to_graph_schema

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/shared/graph_model_utils.py:93
**Export:** graph_model_to_graph_schema

**Issue:** `references/full-api-reference.md:282` documents `graph_model_to_graph_schema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `graph_model_to_graph_schema` is a documented extra, a name the source still declares at `cognee/shared/graph_model_utils.py:93` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-042: Documented extra: graph_schema_to_graph_model

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/shared/graph_model_utils.py:44
**Export:** graph_schema_to_graph_model

**Issue:** `references/full-api-reference.md:282` documents `graph_schema_to_graph_model`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `graph_schema_to_graph_model` is a documented extra, a name the source still declares at `cognee/shared/graph_model_utils.py:44` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-043: Documented extra: graph_spec_to_json_schema

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/graph_models/compiler.py:119
**Export:** graph_spec_to_json_schema

**Issue:** `references/full-api-reference.md:282` documents `graph_spec_to_json_schema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `graph_spec_to_json_schema` is a documented extra, a name the source still declares at `cognee/modules/graph_models/compiler.py:119` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-044: Documented extra: is_tracing_enabled

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/observability/trace_context.py:62
**Export:** is_tracing_enabled

**Issue:** `references/full-api-reference.md:304` documents `is_tracing_enabled`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `is_tracing_enabled` is a documented extra, a name the source still declares at `cognee/modules/observability/trace_context.py:62` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-045: Documented extra: migration

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/migration/__init__.py:1
**Export:** migration

**Issue:** the skill documents `migration`, which the enumerated source API surface lacks and the source still declares; of the 3 files that declare it, the skill cites only `cognee/migration/__init__.py`

**Remediation:** No change: `migration` is a documented extra, a name the source still declares at `cognee/migration/__init__.py:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-046: Documented extra: pipeline_needs_llm

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/tasks/task.py:160
**Export:** pipeline_needs_llm

**Issue:** `SKILL.md:268` documents `pipeline_needs_llm`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `pipeline_needs_llm` is a documented extra, a name the source still declares at `cognee/modules/pipelines/tasks/task.py:160` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-047: Documented extra: pipelines

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/__init__.py:1
**Export:** pipelines

**Issue:** `SKILL.md:29` documents `pipelines`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `pipelines` is a documented extra, a name the source still declares at `cognee/modules/pipelines/__init__.py:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-048: Documented extra: remediation_for

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/remediation.py:146
**Export:** remediation_for

**Issue:** `SKILL.md:294` documents `remediation_for`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `remediation_for` is a documented extra, a name the source still declares at `cognee/exceptions/remediation.py:146` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-050: Documented extra: run_relational_migrations

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/run_migrations.py:11
**Export:** run_relational_migrations

**Issue:** the skill documents `run_relational_migrations`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `cognee/run_migrations.py`

**Remediation:** No change: `run_relational_migrations` is a documented extra, a name the source still declares at `cognee/run_migrations.py:11` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-051: Documented extra: setup

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/engine/operations/setup.py:9
**Export:** setup

**Issue:** `SKILL.md:221` documents `setup`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `setup` is a documented extra, a name the source still declares at `cognee/modules/engine/operations/setup.py:9` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-053: Documented extra: start_visualization_server

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/visualize/start_visualization_server.py:1
**Export:** start_visualization_server

**Issue:** `SKILL.md:29` documents `start_visualization_server`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `start_visualization_server` is a documented extra, a name the source still declares at `cognee/api/v1/visualize/start_visualization_server.py:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-054: Documented extra: task

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/tasks/task.py:124
**Export:** task

**Issue:** `references/pipelines-and-datapoints.md:35` documents `task`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `task` is a documented extra, a name the source still declares at `cognee/modules/pipelines/tasks/task.py:124` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-055: Documented extra: task_summary

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/tasks/task.py:169
**Export:** task_summary

**Issue:** `references/pipelines-and-datapoints.md:36` documents `task_summary`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `task_summary` is a documented extra, a name the source still declares at `cognee/modules/pipelines/tasks/task.py:169` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-056: Documented extra: tools

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/tools/tools.py:1
**Export:** tools

**Issue:** `SKILL.md:29` documents `tools`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `tools` is a documented extra, a name the source still declares at `cognee/api/v1/tools/tools.py:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-057: Documented extra: use_vector_adapter

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/infrastructure/databases/vector/use_vector_adapter.py:4
**Export:** use_vector_adapter

**Issue:** `references/config.md:55` documents `use_vector_adapter`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `use_vector_adapter` is a documented extra, a name the source still declares at `cognee/infrastructure/databases/vector/use_vector_adapter.py:4` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-058: Documented extra: visualize_graph_json

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/visualize/visualize.py:271
**Export:** visualize_graph_json

**Issue:** `references/full-api-reference.md:337` documents `visualize_graph_json`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `visualize_graph_json` is a documented extra, a name the source still declares at `cognee/api/v1/visualize/visualize.py:271` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-059: Documented extra: visualize_multi_user_graph

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/visualize/visualize.py:611
**Export:** visualize_multi_user_graph

**Issue:** `references/full-api-reference.md:339` documents `visualize_multi_user_graph`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `visualize_multi_user_graph` is a documented extra, a name the source still declares at `cognee/api/v1/visualize/visualize.py:611` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-060: Documented extra: visualize_semantic_json

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/visualize/visualize.py:317
**Export:** visualize_semantic_json

**Issue:** `references/full-api-reference.md:338` documents `visualize_semantic_json`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `visualize_semantic_json` is a documented extra, a name the source still declares at `cognee/api/v1/visualize/visualize.py:317` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-063: multi-denominator reporting — barrel vs documented surface

**Severity:** Info
**Category:** Coverage (multi-denominator)
**Source:** skills/oms-cognee/1.6.2/oms-cognee/metadata.json

**Issue:** barrel=102, documented=86

**Remediation:** No action required: the barrel and the documented surface measure different sets by design, and the report records both counts.

### Discovery Quality

**Discovery Test:** not run: the hard gate blocked the run

