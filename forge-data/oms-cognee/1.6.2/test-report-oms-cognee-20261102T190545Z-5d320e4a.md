---
workflowType: 'test-skill'
skillName: 'oms-cognee'
skillDir: 'skills/oms-cognee/1.6.2/oms-cognee'
runId: '20261102T190545Z-5d320e4a'
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
testDate: '2026-11-02T19:05:45Z'
stepsCompleted: ['init', 'detect-mode', 'coverage-check', 'coherence-check', 'external-validators', 'hard-gate', 'report']
nextWorkflow: 'update-skill'
---

# Test Report: oms-cognee

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

**Skill:** oms-cognee
**Test Mode:** naive
**Forge Tier:** Deep

**Mode Rationale:** metadata.json declares `skill_type: "single"`, an individual library skill, so naive mode applies (API-surface coverage; coherence is structural only and is not a scored category).

**Analysis Plan:**
- Coverage Check: every public export of cognee v1.6.2 (`cognee/__init__.py` at ba3631f) checked for documentation in SKILL.md and references/, with AST-backed signature and type verification at Deep tier (ast-grep available, local source pinned and drift-free).
- Coherence Check: structural only: internal references in SKILL.md resolve to files in the package, and the SKILL.md sections follow the skill-sections contract; no cross-skill integration checks.

## Coverage Analysis

**Tier:** Deep
**Source Access:** full
**Source Path:** /home/armel/.skf/workspace/repos/github.com/topoteretes/cognee (HEAD `ba3631f`, tag `v1.6.2`)
**Workspace Layout:** single package
**Denominator:** barrel (standard-barrel clause, `all` set: 92 names; root barrel 98, `scope.include` union 62)

**Files Analyzed:** 53

### Export Coverage

| Export | Type | Documented | Signature | Source Location | Status |
|--------|------|------------|-----------|-----------------|--------|
| `BoundTask` | - | yes | - | - | WARN |
| `COGXArchiveSource` | - | no | - | cognee/modules/migration/sources/cogx_archive.py:19 | WARN |
| `COGXDocument` | - | no | - | cognee/modules/migration/cogx.py:78 | WARN |
| `COGXEntity` | - | no | - | cognee/modules/migration/cogx.py:101 | WARN |
| `COGXEpisode` | - | no | - | cognee/modules/migration/cogx.py:93 | WARN |
| `COGXFact` | - | no | - | cognee/modules/migration/cogx.py:112 | WARN |
| `COGXManifest` | - | no | - | cognee/modules/migration/cogx.py:180 | WARN |
| `COGXMemory` | - | no | - | cognee/modules/migration/cogx.py:131 | WARN |
| `COGXMemoryBlock` | - | no | - | cognee/modules/migration/cogx.py:139 | WARN |
| `COGXRawNode` | - | no | - | cognee/modules/migration/cogx.py:148 | WARN |
| `COGXRecord` | - | no | - | cognee/modules/migration/cogx.py:160 | WARN |
| `COGXScope` | - | no | - | cognee/modules/migration/cogx.py:60 | WARN |
| `COGXTurn` | - | no | - | cognee/modules/migration/cogx.py:87 | WARN |
| `COGX_VERSION` | - | no | - | cognee/modules/migration/cogx.py:22 | WARN |
| `CogneeApiError` | - | yes | - | - | WARN |
| `CogneeConfigurationError` | - | yes | - | - | WARN |
| `CogneeSystemError` | - | yes | - | - | WARN |
| `CogneeTransientError` | - | yes | - | - | WARN |
| `CogneeValidationError` | - | yes | - | - | WARN |
| `DataPoint` | - | yes | - | - | WARN |
| `Drop` | - | yes | - | cognee/pipelines/types.py:32 | PASS |
| `EXPORT_FORMATS` | - | no | - | cognee/modules/migration/export.py:35 | WARN |
| `Edge` | - | yes | - | - | WARN |
| `EntitySpec` | - | yes | - | - | WARN |
| `ExportResult` | class | yes | - | cognee/modules/migration/export.py:41 | PASS |
| `FeedbackEntry` | class | yes | - | cognee/memory/entries.py:62 | PASS |
| `FromIdentity` | - | yes | - | - | WARN |
| `GraphEdge` | - | no | - | cognee/modules/migration/snapshot.py:152 | WARN |
| `GraphSchemaSpec` | - | yes | - | - | WARN |
| `GraphSnapshot` | - | no | - | cognee/modules/migration/snapshot.py:161 | WARN |
| `GraphitiSource` | - | no | - | cognee/modules/migration/sources/zep.py:136 | WARN |
| `IMPORT_MODES` | - | no | - | cognee/modules/migration/sources/base.py:19 | WARN |
| `LLMGateway` | - | yes | - | - | WARN |
| `LettaSource` | - | no | - | cognee/modules/migration/sources/letta.py:72 | WARN |
| `Mem0Source` | - | no | - | cognee/modules/migration/sources/mem0.py:26 | WARN |
| `MemoryEntry` | - | yes | - | cognee/memory/entries.py:129 | PASS |
| `MemorySource` | - | no | - | cognee/modules/migration/sources/base.py:36 | WARN |
| `PipelineRunCompleted` | - | yes | - | - | WARN |
| `PipelineRunErrored` | - | yes | - | - | WARN |
| `PipelineRunInfo` | - | yes | - | - | WARN |
| `PipelineRunStarted` | - | yes | - | - | WARN |
| `PushResult` | class | yes | - | cognee/api/v1/push/push.py:26 | PASS |
| `QAEntry` | class | yes | - | cognee/memory/entries.py:24 | PASS |
| `REMEDIATION_MARKER` | - | yes | - | - | WARN |
| `RememberResult` | class | yes | - | cognee/api/v1/remember/remember.py:600 | PASS |
| `SearchType` | - | yes | - | cognee/modules/search/types/SearchType.py:4 | PASS |
| `SessionModelUsage` | class | yes | - | cognee/modules/session_lifecycle/models.py:96 | PASS |
| `SessionRecord` | class | yes | - | cognee/modules/session_lifecycle/models.py:10 | PASS |
| `Task` | class | yes | - | cognee/modules/pipelines/tasks/task.py:188 | PASS |
| `TaskSpec` | - | yes | - | - | WARN |
| `TraceEntry` | class | yes | - | cognee/memory/entries.py:40 | PASS |
| `UpdateResult` | - | yes | - | - | WARN |
| `ValidationIssue` | class | yes | - | cognee/api/v1/validate/validate.py:99 | PASS |
| `ValidationReport` | class | yes | - | cognee/api/v1/validate/validate.py:105 | PASS |
| `ValidationStatus` | class | yes | - | cognee/api/v1/validate/validate.py:93 | PASS |
| `ZepSource` | - | no | - | cognee/modules/migration/sources/zep.py:57 | WARN |
| `__version__` | - | yes | - | - | WARN |
| `add` | function | yes | yes | cognee/api/v1/add/add.py:39 | PASS |
| `add_data_points` | - | yes | - | - | WARN |
| `add_feedback` | - | yes | - | - | WARN |
| `agent_memory` | - | yes | yes | cognee/modules/agent_memory/decorator.py:29 | PASS |
| `agents` | class | yes | - | cognee/api/v1/agents/agents.py:40 | PASS |
| `apply_write_proposal` | function | yes | yes | cognee/api/v1/tools/tools.py:129 | PASS |
| `build_snapshot` | - | no | - | cognee/modules/migration/snapshot.py:243 | WARN |
| `clear_traces` | - | yes | - | cognee/modules/observability/trace_context.py:121 | PASS |
| `cognee_network_visualization` | function | yes | yes | cognee/modules/visualization/cognee_network_visualization.py:154 | PASS |
| `cognify` | function | yes | yes | cognee/api/v1/cognify/cognify.py:110 | PASS |
| `config` | class | yes | - | cognee/api/v1/config/config.py:171 | PASS |
| `datapoint_registry` | - | no | - | cognee/modules/migration/snapshot.py:39 | WARN |
| `datasets` | class | yes | - | cognee/api/v1/datasets/datasets.py:105 | PASS |
| `delete` | function | yes | yes | cognee/api/v1/delete/__init__.py:12 | PASS |
| `delete_feedback` | - | yes | - | - | WARN |
| `disable_tracing` | - | yes | - | cognee/modules/observability/trace_context.py:43 | PASS |
| `disconnect` | function | yes | yes | cognee/api/v1/serve/disconnect.py:8 | PASS |
| `distill_session` | - | yes | - | - | WARN |
| `enable_tracing` | - | yes | yes | cognee/modules/observability/trace_context.py:18 | PASS |
| `export` | function | yes | yes | cognee/api/v1/export/export.py:16 | PASS |
| `export_dataset` | function | no | - | cognee/modules/migration/export.py:198 | WARN |
| `find_remediation` | - | yes | - | - | WARN |
| `forget` | function | yes | yes | cognee/api/v1/forget/forget.py:22 | PASS |
| `get_all_traces` | - | yes | yes | cognee/modules/observability/trace_context.py:112 | PASS |
| `get_cognee_version` | function | yes | yes | cognee/version.py:7 | PASS |
| `get_default_tasks` | - | yes | - | - | WARN |
| `get_errored_run_info` | - | yes | - | - | WARN |
| `get_last_trace` | - | yes | yes | cognee/modules/observability/trace_context.py:101 | PASS |
| `get_memory_provenance_graph` | function | yes | yes | cognee/api/v1/visualize/memory_provenance.py:645 | PASS |
| `get_schema_inventory` | function | yes | yes | cognee/api/v1/visualize/get_schema_inventory.py:77 | PASS |
| `get_session` | - | yes | - | - | WARN |
| `graph_model_from_spec` | - | yes | - | - | WARN |
| `graph_spec_to_json_schema` | - | yes | - | - | WARN |
| `improve` | function | yes | yes | cognee/api/v1/improve/improve.py:101 | PASS |
| `is_tracing_enabled` | - | yes | - | - | WARN |
| `list_sql_connections` | function | yes | yes | cognee/api/v1/tools/tools.py:65 | PASS |
| `list_write_proposals` | function | yes | yes | cognee/api/v1/tools/tools.py:119 | PASS |
| `logger` | - | no | - | cognee/__init__.py:34 | WARN |
| `low_level` | - | yes | - | - | WARN |
| `memify` | function | yes | yes | cognee/modules/memify/memify.py:27 | PASS |
| `pipeline_needs_llm` | - | yes | - | - | WARN |
| `pipelines` | - | yes | - | - | WARN |
| `propose_corrections` | function | yes | yes | cognee/api/v1/tools/tools.py:101 | PASS |
| `propose_sql_write` | function | yes | yes | cognee/api/v1/tools/tools.py:81 | PASS |
| `prune` | class | yes | - | cognee/api/v1/prune/prune.py:5 | PASS |
| `push` | function | yes | yes | cognee/api/v1/push/push.py:96 | PASS |
| `read_archive` | - | no | - | cognee/modules/migration/cogx.py:322 | WARN |
| `read_manifest` | - | no | - | cognee/modules/migration/cogx.py:276 | WARN |
| `recall` | function | yes | no | cognee/api/v1/recall/recall.py:347 | FAIL |
| `register_sql_connection` | function | yes | yes | cognee/api/v1/tools/tools.py:27 | PASS |
| `rehydrate_node` | - | no | - | cognee/modules/migration/snapshot.py:116 | WARN |
| `reject_write_proposal` | function | yes | yes | cognee/api/v1/tools/tools.py:146 | PASS |
| `remediation_for` | - | yes | - | - | WARN |
| `remember` | function | yes | yes | cognee/api/v1/remember/remember.py:867 | PASS |
| `remove_sql_connection` | function | yes | yes | cognee/api/v1/tools/tools.py:73 | PASS |
| `report` | function | yes | yes | cognee/api/v1/report/report.py:13 | PASS |
| `run_custom_pipeline` | function | yes | yes | cognee/modules/run_custom_pipeline/run_custom_pipeline.py:14 | PASS |
| `run_migrations` | - | yes | - | - | WARN |
| `run_pipeline` | function | yes | yes | cognee/modules/pipelines/operations/pipeline.py:53 | PASS |
| `run_tasks` | function | yes | yes | cognee/modules/pipelines/operations/run_tasks.py:39 | PASS |
| `run_tasks_parallel` | function | yes | yes | cognee/modules/pipelines/operations/run_parallel.py:8 | PASS |
| `search` | function | yes | yes | cognee/api/v1/search/search.py:41 | PASS |
| `serve` | function | yes | yes | cognee/api/v1/serve/serve.py:17 | PASS |
| `session` | - | yes | - | cognee/api/v1/session/__init__.py:8 | PASS |
| `setup` | - | yes | - | - | WARN |
| `start_ui` | function | yes | yes | cognee/api/v1/ui/ui.py:514 | PASS |
| `start_visualization_server` | - | yes | - | - | WARN |
| `task` | - | yes | - | - | WARN |
| `task_summary` | - | yes | - | - | WARN |
| `tools` | - | yes | - | - | WARN |
| `update` | function | yes | yes | cognee/api/v1/update/update.py:28 | PASS |
| `validate` | function | yes | yes | cognee/api/v1/validate/validate.py:198 | PASS |
| `visualization_server` | function | yes | yes | cognee/api/v1/visualize/start_visualization_server.py:6 | PASS |
| `visualize` | function | yes | - | cognee/api/v1/visualize/visualize.py:193 | PASS |
| `visualize_graph` | function | yes | yes | cognee/api/v1/visualize/visualize.py:193 | PASS |
| `visualize_graph_json` | - | yes | - | - | WARN |
| `visualize_memory_provenance` | function | yes | yes | cognee/api/v1/visualize/memory_provenance.py:848 | PASS |
| `visualize_multi_user_graph` | - | yes | - | - | WARN |
| `visualize_semantic_json` | - | yes | - | - | WARN |

### Coverage Summary

- **Exports Found:** 92
- **Documented:** 63 (68.48%)
- **Missing Documentation:** 29
- **Signature Mismatches:** 1
- **Stale Documentation:** 44, documented extras included
- **Scoped Out by the Brief:** `describe_resolution` (cognee/shared/env_file.py), `load_env_file` (cognee/shared/env_file.py), `run_migrations` (cognee/run_migrations.py), `setup_logging` (cognee/shared/logging_utils.py), `start_visualization_server` (cognee/shared/utils.py), `wait_for_background_tasks` (cognee/infrastructure/background_tasks.py)
- **Nested Entry Points:** `cognee/api/v1/api_keys/routers/__init__.py` inside `cognee/__init__.py`: `get_api_key_management_router`; `cognee/api/v1/cloud/routers/__init__.py` inside `cognee/__init__.py`: `get_checks_router`; `cognee/api/v1/permissions/routers/__init__.py` inside `cognee/__init__.py`: `get_permissions_router`; `cognee/api/v1/settings/routers/__init__.py` inside `cognee/__init__.py`: `get_settings_router`
- **Restored by the Stale-Scope Guard:** `COGXArchiveSource` (cognee/modules/migration/sources/cogx_archive.py:19), `COGXDocument` (cognee/modules/migration/cogx.py:78), `COGXEntity` (cognee/modules/migration/cogx.py:101), `COGXEpisode` (cognee/modules/migration/cogx.py:93), `COGXFact` (cognee/modules/migration/cogx.py:112), `COGXManifest` (cognee/modules/migration/cogx.py:180), `COGXMemory` (cognee/modules/migration/cogx.py:131), `COGXMemoryBlock` (cognee/modules/migration/cogx.py:139), `COGXRawNode` (cognee/modules/migration/cogx.py:148), `COGXRecord` (cognee/modules/migration/cogx.py:160), `COGXScope` (cognee/modules/migration/cogx.py:60), `COGXTurn` (cognee/modules/migration/cogx.py:87), `COGX_VERSION` (cognee/modules/migration/cogx.py:22), `Drop` (cognee/pipelines/types.py:32), `GraphEdge` (cognee/modules/migration/snapshot.py:152), `GraphSnapshot` (cognee/modules/migration/snapshot.py:161), `GraphitiSource` (cognee/modules/migration/sources/zep.py:136), `IMPORT_MODES` (cognee/modules/migration/sources/base.py:19), `LettaSource` (cognee/modules/migration/sources/letta.py:72), `Mem0Source` (cognee/modules/migration/sources/mem0.py:26), `MemorySource` (cognee/modules/migration/sources/base.py:36), `SearchType` (cognee/modules/search/types/SearchType.py:4), `ZepSource` (cognee/modules/migration/sources/zep.py:57), `agent_memory` (cognee/modules/agent_memory/decorator.py:29), `build_snapshot` (cognee/modules/migration/snapshot.py:243), `clear_traces` (cognee/modules/observability/trace_context.py:121), `datapoint_registry` (cognee/modules/migration/snapshot.py:39), `disable_tracing` (cognee/modules/observability/trace_context.py:43), `enable_tracing` (cognee/modules/observability/trace_context.py:18), `get_all_traces` (cognee/modules/observability/trace_context.py:112), `get_last_trace` (cognee/modules/observability/trace_context.py:101), `read_archive` (cognee/modules/migration/cogx.py:322), `read_manifest` (cognee/modules/migration/cogx.py:276), `rehydrate_node` (cognee/modules/migration/snapshot.py:116)

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 68.48% |
| Signature Accuracy | 97.5% |
| Type Coverage | 100% |

### Notes

- **Deep-tier checks:** `gh api repos/topoteretes/cognee/git/ref/tags/v1.6.2` resolves to `ba3631f2ed363a6ea50d649c34c56885af6b36fe`, which is the workspace HEAD and `metadata.source_commit`, and `pyproject.toml:4` reads `version = "1.6.2"`. Type cross-check: the 16 surface types are all documented (Type Coverage 100%), and the documented fields of `PushResult` (`cognee/api/v1/push/push.py:26`), `ExportResult` (`cognee/modules/migration/export.py:41`), `ValidationStatus`/`ValidationIssue`/`ValidationReport` (`cognee/api/v1/validate/validate.py:93-108`), `QAEntry`/`TraceEntry`/`FeedbackEntry` (`cognee/memory/entries.py:24-75`), the `MemoryEntry` alias (`cognee/memory/entries.py:129`) and the 20 `SearchType` members (`cognee/modules/search/types/SearchType.py:4-24`) match their source declarations. Re-exports were traced to their definitions by the recipe runner (`reexport_targets`), for example `remember` → `cognee/api/v1/remember/remember.py:867` and `ExportResult` → `cognee/modules/migration/export.py:41`.
- **Signature comparisons (40 checks, 1 mismatch).** `recall` (`cognee/api/v1/recall/recall.py:347`): SKILL.md:155, the only place the skill documents its parameters, ends in `...` and leaves out 11 optional keyword-only parameters the source declares (`system_prompt`, `system_prompt_path`, `node_name_filter_operator`, `wide_search_top_k`, `triplet_distance_penalty`, `feedback_influence`, `verbose`, `retriever_specific_config`, `neighborhood_depth`, `neighborhood_seed_top_k`, `user`). The 18 parameters it does list match. Judged equivalent, not mismatches: `export`, where the plan points at the first `@overload` (`export.py:16`) and the documented signature is the implementation at `export.py:49`, which it matches exactly; the tool functions' `dict`/`list[dict]` against `dict[str, Any]`/`list[dict[str, Any]]`; `start_ui`'s `Optional[subprocess.Popen]` against `subprocess.Popen | None`; `run_tasks_parallel`, whose `-> Task` matches what it returns (`run_parallel.py:15` `return Task(parallel_run)`), while its annotation reads `Callable[[Any], Generator[Any, Any, Any]]` (references/pipelines-and-datapoints.md:278 quotes both); and `visualization_server`, whose "shutdown callable" matches `cognee/shared/utils.py:520` (`return shutdown`), while its annotation reads `Callable[[], Callable[[], None]]`.
- **Namespace members on the surface.** `from .modules import pipelines`, `from . import migration` and `from .api.v1.tools import tools` (`cognee/__init__.py:67,98,113`) and the `start_visualization_server` submodule (`cognee/__init__.py:55`) bind modules, so the surface counts their members, the names users reach as `cognee.<module>.<name>`: `Task`, `run_pipeline`, `run_tasks`, `run_tasks_parallel`, the 8 tool functions, `visualization_server`, and 28 `cognee.migration` names. The skill documents every member except the `cognee.migration` names. It declares the `migration` module out of scope (SKILL.md:28; references/full-api-reference.md:622), but the brief does not exclude it, so 28 of the 29 missing names are `cognee.migration` members. The 29th is `logger` (`cognee/__init__.py:34`), which the skill names only as out of scope.
- **Stale names (44):** `classify-stale` finds none fabricated. 39 are sub-module APIs the skill documents on purpose (the `cognee.exceptions` classes, the `cognee.session` helpers, `cognee.low_level` and its exports, the pipeline `task`/`TaskSpec`/`BoundTask`/`PipelineRunInfo` family, `add_data_points`, `LLMGateway`, the non-top-level visualize helpers and others), each still declared at the pinned commit. Plus `__version__` (`cognee/__init__.py:22`) and the module names `pipelines`, `tools` and `start_visualization_server`. `run_migrations` (`cognee/run_migrations.py:18`) and `start_visualization_server` are top-level names whose files the brief's `scope.exclude` scopes out. `DataPoint`, `Edge` and `distill_session` have more than one declaring file.
- **Stale brief scope:** `scope.include` globs `cognee/pipelines.py` (now the `cognee/pipelines/` package) and `cognee/modules/observability/trace_context/**` (now the `trace_context.py` file) match no file at the pinned commit, so the stale-scope guard restored 34 root exports defined in files no glob covers. Among them are the documented `Drop`, `SearchType`, `agent_memory` and the 5 tracing functions, and also the 28 undocumented `cognee.migration` names.
- **Metadata coherence (§4b):** Medium `metadata-drift`: `stats.exports_public_api`=64 against `exports[].length`=56 (12% drift). Info `multi-denominator`: barrel 64 against documented 56.
- **Numerator ground truth (§2b):** skipped, because `stats.effective_denominator` is absent, so the inflation signature cannot occur.
- **Provenance lines (§4c):** `verify` passes: 56 exports and 56 map entries checked, 0 stale lines, 3 line checks skipped by export type.

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)

### Structural Findings

| # | Type | Severity | Detail | Line |
|---|------|----------|--------|------|
| - | none | - | No structural issue: the description (`Overview`, line 21), usage (`Quick Start`, line 32) and API surface (`Key API Summary`, line 124) families are all present; 6 fences, balanced, every opening fence tagged; no table row drifts from its header; no `scripts/` or `assets/` folder. | - |

**Structural Issues:** 0

- **Exports in a usage-family section (§2.4):** every one of the 63 function exports in the inventory is named in `Quick Start`, `Common Workflows` or `Key API Summary` (split body), or in one of the four reference files (`zero_usage`: none).
- **Async/sync consistency (§2.5):** every example call of an async export is awaited (`add`, `cognify`, `search`, `remember`, `recall`, `run_pipeline`, `add_data_points`). The unawaited calls are of exports the skill describes as sync: the five tracing functions ("All sync functions", references/full-api-reference.md:293), `run_tasks_parallel`, the `task` deferred-call sugar and the `task_summary` decorator. No finding.
- **Migration section (§2b):** Deep tier and the evidence report exists, but `forge-data/oms-cognee/1.6.2/evidence-report.md` has no YAML frontmatter, so `t2_future_count` is absent. Case 4: Section 4b verification skipped. (SKILL.md has no "Migration & Deprecation Warnings" section; its `Deprecations & Gotchas` section holds current-state notes.)

### Reference Consistency (split-body)

| # | Reference File | Export | Issue | SKILL.md Line | Reference Line |
|---|---------------|--------|-------|---------------|---------------|
| - | - | - | No mismatch: wherever the SKILL.md body and a reference file both document an export, the reference adds detail and contradicts nothing. | - | - |

**Exports Cross-Checked:** 107 (SKILL.md against references/full-api-reference.md, config.md, core-workflow.md, pipelines-and-datapoints.md)
**Mismatches Found:** 0

## External Validation

### skill-check
- **Available:** yes
- **Quality Score:** 100/100 (frontmatter 30, description 30, body 20, links 10, file 10)
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

**Total Gaps:** 77
**Blocking (Critical + High):** 1
**Non-blocking (Medium + Low + Info):** 76

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|------------------|
| Critical | 1 | Read the source code and write or correct the documentation |
| High | 0 | None |
| Medium | 34 | Add type definitions, interface docs or the missing section |
| Low | 0 | None |
| Info | 42 | Optional improvements, no action required |
| **Total** | **77** | |

### GAP-001: Signature mismatch: recall

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** cognee/api/v1/recall/recall.py:347
**Export:** recall

**Issue:** documented `recall(query_text, query_type=None, *, datasets=None, dataset_ids=None, top_k=15, auto_route=True, scope=None, node_name=None, session_id=None, context_profile='qa', only_context=False, response_model=None, include_references=False, tool_connections=None, tools_trigger='always', code_query=None, llm_config=None, embedding_config=None, ...) -> list[RecallResponse]`, source `async def recall(query_text: str, query_type: SearchType | None = None, *, datasets: list[str] | None = None, dataset_ids: list[UUID] | None = None, top_k: int = 15, auto_route: bool = True, scope: str | list[str] | None = None, system_prompt: str | None = None, system_prompt_path: str = 'answer_simple_question.txt', node_name: list[str] | None = None, node_name_filter_operator: str = 'OR', only_context: bool = False, session_id: str | None = None, context_profile: str = 'qa', wide_search_top_k: int | None = None, triplet_distance_penalty: float | None = None, feedback_influence: float = get_base_config().default_feedback_influence, verbose: bool = False, retriever_specific_config: dict | None = None, response_model: type | None = None, neighborhood_depth: int | None = None, neighborhood_seed_top_k: int | None = None, include_references: bool = False, tool_connections: list[str] | None = None, tools_trigger: str = 'always', code_query: dict | None = None, user: object | None = None, llm_config: LLMConfig | None = None, embedding_config: EmbeddingConfig | None = None) -> list[RecallResponse]`: documented signature (SKILL.md:155, the only place the skill documents recall's parameters) ends in '...' and omits 11 optional keyword-only parameters the source declares: system_prompt, system_prompt_path, node_name_filter_operator, wide_search_top_k, triplet_distance_penalty, feedback_influence, verbose, retriever_specific_config, neighborhood_depth, neighborhood_seed_top_k, user; the 18 documented parameters match the source in name, default and keyword-only kind

**Remediation:** Update the documented signature of `recall` from `recall(query_text, query_type=None, *, datasets=None, dataset_ids=None, top_k=15, auto_route=True, scope=None, node_name=None, session_id=None, context_profile='qa', only_context=False, response_model=None, include_references=False, tool_connections=None, tools_trigger='always', code_query=None, llm_config=None, embedding_config=None, ...) -> list[RecallResponse]` to `async def recall(query_text: str, query_type: SearchType | None = None, *, datasets: list[str] | None = None, dataset_ids: list[UUID] | None = None, top_k: int = 15, auto_route: bool = True, scope: str | list[str] | None = None, system_prompt: str | None = None, system_prompt_path: str = 'answer_simple_question.txt', node_name: list[str] | None = None, node_name_filter_operator: str = 'OR', only_context: bool = False, session_id: str | None = None, context_profile: str = 'qa', wide_search_top_k: int | None = None, triplet_distance_penalty: float | None = None, feedback_influence: float = get_base_config().default_feedback_influence, verbose: bool = False, retriever_specific_config: dict | None = None, response_model: type | None = None, neighborhood_depth: int | None = None, neighborhood_seed_top_k: int | None = None, include_references: bool = False, tool_connections: list[str] | None = None, tools_trigger: str = 'always', code_query: dict | None = None, user: object | None = None, llm_config: LLMConfig | None = None, embedding_config: EmbeddingConfig | None = None) -> list[RecallResponse]`, the signature the source defines at `cognee/api/v1/recall/recall.py:347`.

### GAP-002: Missing export: COGXArchiveSource

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** cognee/modules/migration/sources/cogx_archive.py:19
**Export:** COGXArchiveSource

**Issue:** `COGXArchiveSource` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `COGXArchiveSource` in SKILL.md: read its definition at `cognee/modules/migration/sources/cogx_archive.py:19` and add its signature, its purpose and a usage example.

### GAP-003: Missing export: COGXDocument

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** cognee/modules/migration/cogx.py:78
**Export:** COGXDocument

**Issue:** `COGXDocument` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `COGXDocument` in SKILL.md: read its definition at `cognee/modules/migration/cogx.py:78` and add its signature, its purpose and a usage example.

### GAP-004: Missing export: COGXEntity

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** cognee/modules/migration/cogx.py:101
**Export:** COGXEntity

**Issue:** `COGXEntity` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `COGXEntity` in SKILL.md: read its definition at `cognee/modules/migration/cogx.py:101` and add its signature, its purpose and a usage example.

### GAP-005: Missing export: COGXEpisode

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** cognee/modules/migration/cogx.py:93
**Export:** COGXEpisode

**Issue:** `COGXEpisode` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `COGXEpisode` in SKILL.md: read its definition at `cognee/modules/migration/cogx.py:93` and add its signature, its purpose and a usage example.

### GAP-006: Missing export: COGXFact

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** cognee/modules/migration/cogx.py:112
**Export:** COGXFact

**Issue:** `COGXFact` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `COGXFact` in SKILL.md: read its definition at `cognee/modules/migration/cogx.py:112` and add its signature, its purpose and a usage example.

### GAP-007: Missing export: COGXManifest

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** cognee/modules/migration/cogx.py:180
**Export:** COGXManifest

**Issue:** `COGXManifest` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `COGXManifest` in SKILL.md: read its definition at `cognee/modules/migration/cogx.py:180` and add its signature, its purpose and a usage example.

### GAP-008: Missing export: COGXMemory

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** cognee/modules/migration/cogx.py:131
**Export:** COGXMemory

**Issue:** `COGXMemory` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `COGXMemory` in SKILL.md: read its definition at `cognee/modules/migration/cogx.py:131` and add its signature, its purpose and a usage example.

### GAP-009: Missing export: COGXMemoryBlock

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** cognee/modules/migration/cogx.py:139
**Export:** COGXMemoryBlock

**Issue:** `COGXMemoryBlock` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `COGXMemoryBlock` in SKILL.md: read its definition at `cognee/modules/migration/cogx.py:139` and add its signature, its purpose and a usage example.

### GAP-010: Missing export: COGXRawNode

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** cognee/modules/migration/cogx.py:148
**Export:** COGXRawNode

**Issue:** `COGXRawNode` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `COGXRawNode` in SKILL.md: read its definition at `cognee/modules/migration/cogx.py:148` and add its signature, its purpose and a usage example.

### GAP-011: Missing export: COGXRecord

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** cognee/modules/migration/cogx.py:160
**Export:** COGXRecord

**Issue:** `COGXRecord` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `COGXRecord` in SKILL.md: read its definition at `cognee/modules/migration/cogx.py:160` and add its signature, its purpose and a usage example.

### GAP-012: Missing export: COGXScope

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** cognee/modules/migration/cogx.py:60
**Export:** COGXScope

**Issue:** `COGXScope` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `COGXScope` in SKILL.md: read its definition at `cognee/modules/migration/cogx.py:60` and add its signature, its purpose and a usage example.

### GAP-013: Missing export: COGXTurn

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** cognee/modules/migration/cogx.py:87
**Export:** COGXTurn

**Issue:** `COGXTurn` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `COGXTurn` in SKILL.md: read its definition at `cognee/modules/migration/cogx.py:87` and add its signature, its purpose and a usage example.

### GAP-014: Missing export: COGX_VERSION

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** cognee/modules/migration/cogx.py:22
**Export:** COGX_VERSION

**Issue:** `COGX_VERSION` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `COGX_VERSION` in SKILL.md: read its definition at `cognee/modules/migration/cogx.py:22` and add its signature, its purpose and a usage example.

### GAP-015: Missing export: EXPORT_FORMATS

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** cognee/modules/migration/export.py:35
**Export:** EXPORT_FORMATS

**Issue:** `EXPORT_FORMATS` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `EXPORT_FORMATS` in SKILL.md: read its definition at `cognee/modules/migration/export.py:35` and add its signature, its purpose and a usage example.

### GAP-016: Missing export: GraphEdge

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** cognee/modules/migration/snapshot.py:152
**Export:** GraphEdge

**Issue:** `GraphEdge` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `GraphEdge` in SKILL.md: read its definition at `cognee/modules/migration/snapshot.py:152` and add its signature, its purpose and a usage example.

### GAP-017: Missing export: GraphSnapshot

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** cognee/modules/migration/snapshot.py:161
**Export:** GraphSnapshot

**Issue:** `GraphSnapshot` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `GraphSnapshot` in SKILL.md: read its definition at `cognee/modules/migration/snapshot.py:161` and add its signature, its purpose and a usage example.

### GAP-018: Missing export: GraphitiSource

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** cognee/modules/migration/sources/zep.py:136
**Export:** GraphitiSource

**Issue:** `GraphitiSource` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `GraphitiSource` in SKILL.md: read its definition at `cognee/modules/migration/sources/zep.py:136` and add its signature, its purpose and a usage example.

### GAP-019: Missing export: IMPORT_MODES

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** cognee/modules/migration/sources/base.py:19
**Export:** IMPORT_MODES

**Issue:** `IMPORT_MODES` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `IMPORT_MODES` in SKILL.md: read its definition at `cognee/modules/migration/sources/base.py:19` and add its signature, its purpose and a usage example.

### GAP-020: Missing export: LettaSource

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** cognee/modules/migration/sources/letta.py:72
**Export:** LettaSource

**Issue:** `LettaSource` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `LettaSource` in SKILL.md: read its definition at `cognee/modules/migration/sources/letta.py:72` and add its signature, its purpose and a usage example.

### GAP-021: Missing export: Mem0Source

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** cognee/modules/migration/sources/mem0.py:26
**Export:** Mem0Source

**Issue:** `Mem0Source` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `Mem0Source` in SKILL.md: read its definition at `cognee/modules/migration/sources/mem0.py:26` and add its signature, its purpose and a usage example.

### GAP-022: Missing export: MemorySource

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** cognee/modules/migration/sources/base.py:36
**Export:** MemorySource

**Issue:** `MemorySource` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `MemorySource` in SKILL.md: read its definition at `cognee/modules/migration/sources/base.py:36` and add its signature, its purpose and a usage example.

### GAP-023: Missing export: ZepSource

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** cognee/modules/migration/sources/zep.py:57
**Export:** ZepSource

**Issue:** `ZepSource` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `ZepSource` in SKILL.md: read its definition at `cognee/modules/migration/sources/zep.py:57` and add its signature, its purpose and a usage example.

### GAP-024: Missing export: build_snapshot

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** cognee/modules/migration/snapshot.py:243
**Export:** build_snapshot

**Issue:** `build_snapshot` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `build_snapshot` in SKILL.md: read its definition at `cognee/modules/migration/snapshot.py:243` and add its signature, its purpose and a usage example.

### GAP-025: Missing export: datapoint_registry

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** cognee/modules/migration/snapshot.py:39
**Export:** datapoint_registry

**Issue:** `datapoint_registry` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `datapoint_registry` in SKILL.md: read its definition at `cognee/modules/migration/snapshot.py:39` and add its signature, its purpose and a usage example.

### GAP-026: Missing export: export_dataset

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** cognee/modules/migration/export.py:198
**Export:** export_dataset

**Issue:** `export_dataset` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `export_dataset` in SKILL.md: read its definition at `cognee/modules/migration/export.py:198` and add its signature, its purpose and a usage example.

### GAP-027: Missing export: logger

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** cognee/__init__.py:34
**Export:** logger

**Issue:** `logger` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `logger` in SKILL.md: read its definition at `cognee/__init__.py:34` and add its signature, its purpose and a usage example.

### GAP-028: Missing export: read_archive

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** cognee/modules/migration/cogx.py:322
**Export:** read_archive

**Issue:** `read_archive` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `read_archive` in SKILL.md: read its definition at `cognee/modules/migration/cogx.py:322` and add its signature, its purpose and a usage example.

### GAP-029: Missing export: read_manifest

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** cognee/modules/migration/cogx.py:276
**Export:** read_manifest

**Issue:** `read_manifest` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `read_manifest` in SKILL.md: read its definition at `cognee/modules/migration/cogx.py:276` and add its signature, its purpose and a usage example.

### GAP-030: Missing export: rehydrate_node

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** cognee/modules/migration/snapshot.py:116
**Export:** rehydrate_node

**Issue:** `rehydrate_node` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `rehydrate_node` in SKILL.md: read its definition at `cognee/modules/migration/snapshot.py:116` and add its signature, its purpose and a usage example.

### GAP-037: Stale documentation: DataPoint

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:185
**Export:** DataPoint

**Issue:** SKILL.md documents `DataPoint`, which the enumerated source API surface lacks

**Remediation:** Check `DataPoint` against the source and update or remove its documentation at SKILL.md:185: the enumerated source surface does not export it.

### GAP-066: Stale documentation: run_migrations

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:13
**Export:** run_migrations

**Issue:** SKILL.md documents `run_migrations`, which the enumerated source API surface lacks

**Remediation:** Check `run_migrations` against the source and update or remove its documentation at SKILL.md:13: the enumerated source surface does not export it.

### GAP-068: Stale documentation: start_visualization_server

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:122
**Export:** start_visualization_server

**Issue:** SKILL.md documents `start_visualization_server`, which the enumerated source API surface lacks

**Remediation:** Check `start_visualization_server` against the source and update or remove its documentation at SKILL.md:122: the enumerated source surface does not export it.

### GAP-075: stale brief scope: scope.include globs match no source file

**Severity:** Medium
**Category:** Coverage (brief-scope-stale)
**Source:** forge-data/oms-cognee/skill-brief.yaml

**Issue:** the `scope.include` globs `cognee/pipelines.py`, `cognee/modules/observability/trace_context/**` match no file in the source tested; the `all` set restores 34 root exports, defined in files no include glob covers: `COGXArchiveSource` in `cognee/modules/migration/sources/cogx_archive.py`, `COGXDocument` in `cognee/modules/migration/cogx.py`, `COGXEntity` in `cognee/modules/migration/cogx.py`, `COGXEpisode` in `cognee/modules/migration/cogx.py`, `COGXFact` in `cognee/modules/migration/cogx.py`, `COGXManifest` in `cognee/modules/migration/cogx.py`, `COGXMemory` in `cognee/modules/migration/cogx.py`, `COGXMemoryBlock` in `cognee/modules/migration/cogx.py`, `COGXRawNode` in `cognee/modules/migration/cogx.py`, `COGXRecord` in `cognee/modules/migration/cogx.py`, `COGXScope` in `cognee/modules/migration/cogx.py`, `COGXTurn` in `cognee/modules/migration/cogx.py`, `COGX_VERSION` in `cognee/modules/migration/cogx.py`, `Drop` in `cognee/pipelines/types.py`, `GraphEdge` in `cognee/modules/migration/snapshot.py`, `GraphSnapshot` in `cognee/modules/migration/snapshot.py`, `GraphitiSource` in `cognee/modules/migration/sources/zep.py`, `IMPORT_MODES` in `cognee/modules/migration/sources/base.py`, `LettaSource` in `cognee/modules/migration/sources/letta.py`, `Mem0Source` in `cognee/modules/migration/sources/mem0.py`, `MemorySource` in `cognee/modules/migration/sources/base.py`, `SearchType` in `cognee/modules/search/types/SearchType.py`, `ZepSource` in `cognee/modules/migration/sources/zep.py`, `agent_memory` in `cognee/modules/agent_memory/decorator.py`, `build_snapshot` in `cognee/modules/migration/snapshot.py`, `clear_traces` in `cognee/modules/observability/trace_context.py`, `datapoint_registry` in `cognee/modules/migration/snapshot.py`, `disable_tracing` in `cognee/modules/observability/trace_context.py`, `enable_tracing` in `cognee/modules/observability/trace_context.py`, `get_all_traces` in `cognee/modules/observability/trace_context.py`, `get_last_trace` in `cognee/modules/observability/trace_context.py`, `read_archive` in `cognee/modules/migration/cogx.py`, `read_manifest` in `cognee/modules/migration/cogx.py`, `rehydrate_node` in `cognee/modules/migration/snapshot.py`

**Remediation:** Edit `scope.include` in `forge-data/oms-cognee/skill-brief.yaml` by hand so each glob matches the files it meant in this version of the source (update-skill does not rewrite an include glob), and add to `scope.exclude` any restored file the brief meant to leave out.

### GAP-076: metadata drift — barrel export counts diverge

**Severity:** Medium
**Category:** Coverage (metadata-drift)
**Source:** skills/oms-cognee/1.6.2/oms-cognee/metadata.json

**Issue:** stats.exports_public_api=64, exports[].length=56 → 12% drift

**Remediation:** Recount the exports and correct the diverging counts in `skills/oms-cognee/1.6.2/oms-cognee/metadata.json`; update-skill applies it as a metadata update.

### GAP-031: Documented extra: BoundTask

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/tasks/task.py:8
**Export:** BoundTask

**Issue:** `SKILL.md:188` documents `BoundTask`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `BoundTask` is a documented extra, a name the source still declares at `cognee/modules/pipelines/tasks/task.py:8` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-032: Documented extra: CogneeApiError

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/exceptions.py:10
**Export:** CogneeApiError

**Issue:** `SKILL.md:252` documents `CogneeApiError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CogneeApiError` is a documented extra, a name the source still declares at `cognee/exceptions/exceptions.py:10` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-033: Documented extra: CogneeConfigurationError

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/exceptions.py:99
**Export:** CogneeConfigurationError

**Issue:** `SKILL.md:110` documents `CogneeConfigurationError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CogneeConfigurationError` is a documented extra, a name the source still declares at `cognee/exceptions/exceptions.py:99` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-034: Documented extra: CogneeSystemError

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/exceptions.py:69
**Export:** CogneeSystemError

**Issue:** `SKILL.md:253` documents `CogneeSystemError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CogneeSystemError` is a documented extra, a name the source still declares at `cognee/exceptions/exceptions.py:69` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-035: Documented extra: CogneeTransientError

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/exceptions.py:114
**Export:** CogneeTransientError

**Issue:** `SKILL.md:256` documents `CogneeTransientError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CogneeTransientError` is a documented extra, a name the source still declares at `cognee/exceptions/exceptions.py:114` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-036: Documented extra: CogneeValidationError

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/exceptions.py:84
**Export:** CogneeValidationError

**Issue:** `SKILL.md:191` documents `CogneeValidationError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CogneeValidationError` is a documented extra, a name the source still declares at `cognee/exceptions/exceptions.py:84` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-038: Documented extra: Edge

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/infrastructure/engine/models/Edge.py:13
**Export:** Edge

**Issue:** `SKILL.md:185` documents `Edge`, which the enumerated source API surface lacks and the source still declares; of the 5 files that declare it, the skill cites only `cognee/infrastructure/engine/models/Edge.py`

**Remediation:** No change: `Edge` is a documented extra, a name the source still declares at `cognee/infrastructure/engine/models/Edge.py:13` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-039: Documented extra: EntitySpec

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/graph_models/spec.py:90
**Export:** EntitySpec

**Issue:** `references/full-api-reference.md:279` documents `EntitySpec`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `EntitySpec` is a documented extra, a name the source still declares at `cognee/modules/graph_models/spec.py:90` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-040: Documented extra: FromIdentity

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/infrastructure/engine/models/FieldAnnotations.py:95
**Export:** FromIdentity

**Issue:** `SKILL.md:185` documents `FromIdentity`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `FromIdentity` is a documented extra, a name the source still declares at `cognee/infrastructure/engine/models/FieldAnnotations.py:95` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-041: Documented extra: GraphSchemaSpec

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/graph_models/spec.py:108
**Export:** GraphSchemaSpec

**Issue:** `references/full-api-reference.md:279` documents `GraphSchemaSpec`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `GraphSchemaSpec` is a documented extra, a name the source still declares at `cognee/modules/graph_models/spec.py:108` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-042: Documented extra: LLMGateway

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/infrastructure/llm/LLMGateway.py:106
**Export:** LLMGateway

**Issue:** `references/core-workflow.md:444` documents `LLMGateway`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LLMGateway` is a documented extra, a name the source still declares at `cognee/infrastructure/llm/LLMGateway.py:106` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-043: Documented extra: PipelineRunCompleted

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/models/PipelineRunInfo.py:34
**Export:** PipelineRunCompleted

**Issue:** `references/full-api-reference.md:267` documents `PipelineRunCompleted`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PipelineRunCompleted` is a documented extra, a name the source still declares at `cognee/modules/pipelines/models/PipelineRunInfo.py:34` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-044: Documented extra: PipelineRunErrored

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/models/PipelineRunInfo.py:42
**Export:** PipelineRunErrored

**Issue:** `references/core-workflow.md:100` documents `PipelineRunErrored`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PipelineRunErrored` is a documented extra, a name the source still declares at `cognee/modules/pipelines/models/PipelineRunInfo.py:42` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-045: Documented extra: PipelineRunInfo

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/models/PipelineRunInfo.py:9
**Export:** PipelineRunInfo

**Issue:** `SKILL.md:131` documents `PipelineRunInfo`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PipelineRunInfo` is a documented extra, a name the source still declares at `cognee/modules/pipelines/models/PipelineRunInfo.py:9` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-046: Documented extra: PipelineRunStarted

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/models/PipelineRunInfo.py:26
**Export:** PipelineRunStarted

**Issue:** `references/full-api-reference.md:267` documents `PipelineRunStarted`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PipelineRunStarted` is a documented extra, a name the source still declares at `cognee/modules/pipelines/models/PipelineRunInfo.py:26` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-047: Documented extra: REMEDIATION_MARKER

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/remediation.py:52
**Export:** REMEDIATION_MARKER

**Issue:** `SKILL.md:258` documents `REMEDIATION_MARKER`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `REMEDIATION_MARKER` is a documented extra, a name the source still declares at `cognee/exceptions/remediation.py:52` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-048: Documented extra: TaskSpec

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/tasks/task.py:35
**Export:** TaskSpec

**Issue:** `references/pipelines-and-datapoints.md:36` documents `TaskSpec`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `TaskSpec` is a documented extra, a name the source still declares at `cognee/modules/pipelines/tasks/task.py:35` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-049: Documented extra: UpdateResult

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/update/result.py:37
**Export:** UpdateResult

**Issue:** `references/core-workflow.md:383` documents `UpdateResult`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `UpdateResult` is a documented extra, a name the source still declares at `cognee/api/v1/update/result.py:37` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-050: Documented extra: __version__

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/__init__.py:22
**Export:** __version__

**Issue:** `SKILL.md:28` documents `__version__`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `__version__` is a documented extra, a name the source still declares at `cognee/__init__.py:22` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-051: Documented extra: add_data_points

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/tasks/storage/add_data_points.py:70
**Export:** add_data_points

**Issue:** `SKILL.md:116` documents `add_data_points`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `add_data_points` is a documented extra, a name the source still declares at `cognee/tasks/storage/add_data_points.py:70` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-052: Documented extra: add_feedback

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/session/session.py:113
**Export:** add_feedback

**Issue:** `SKILL.md:144` documents `add_feedback`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `add_feedback` is a documented extra, a name the source still declares at `cognee/api/v1/session/session.py:113` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-053: Documented extra: delete_feedback

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/session/session.py:147
**Export:** delete_feedback

**Issue:** `SKILL.md:144` documents `delete_feedback`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `delete_feedback` is a documented extra, a name the source still declares at `cognee/api/v1/session/session.py:147` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-054: Documented extra: distill_session

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/session_distillation/distill.py:471
**Export:** distill_session

**Issue:** `SKILL.md:144` documents `distill_session`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `cognee/modules/session_distillation/distill.py`

**Remediation:** No change: `distill_session` is a documented extra, a name the source still declares at `cognee/modules/session_distillation/distill.py:471` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-055: Documented extra: find_remediation

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/remediation.py:131
**Export:** find_remediation

**Issue:** `SKILL.md:258` documents `find_remediation`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `find_remediation` is a documented extra, a name the source still declares at `cognee/exceptions/remediation.py:131` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-056: Documented extra: get_default_tasks

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/cognify/cognify.py:565
**Export:** get_default_tasks

**Issue:** `references/core-workflow.md:183` documents `get_default_tasks`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_default_tasks` is a documented extra, a name the source still declares at `cognee/api/v1/cognify/cognify.py:565` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-057: Documented extra: get_errored_run_info

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/models/PipelineRunInfo.py:62
**Export:** get_errored_run_info

**Issue:** `references/full-api-reference.md:574` documents `get_errored_run_info`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_errored_run_info` is a documented extra, a name the source still declares at `cognee/modules/pipelines/models/PipelineRunInfo.py:62` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-058: Documented extra: get_session

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/session/session.py:65
**Export:** get_session

**Issue:** `SKILL.md:144` documents `get_session`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_session` is a documented extra, a name the source still declares at `cognee/api/v1/session/session.py:65` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-059: Documented extra: graph_model_from_spec

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/graph_models/compiler.py:135
**Export:** graph_model_from_spec

**Issue:** `references/full-api-reference.md:279` documents `graph_model_from_spec`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `graph_model_from_spec` is a documented extra, a name the source still declares at `cognee/modules/graph_models/compiler.py:135` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-060: Documented extra: graph_spec_to_json_schema

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/graph_models/compiler.py:119
**Export:** graph_spec_to_json_schema

**Issue:** `references/full-api-reference.md:279` documents `graph_spec_to_json_schema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `graph_spec_to_json_schema` is a documented extra, a name the source still declares at `cognee/modules/graph_models/compiler.py:119` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-061: Documented extra: is_tracing_enabled

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/observability/trace_context.py:62
**Export:** is_tracing_enabled

**Issue:** `references/full-api-reference.md:304` documents `is_tracing_enabled`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `is_tracing_enabled` is a documented extra, a name the source still declares at `cognee/modules/observability/trace_context.py:62` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-062: Documented extra: low_level

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/low_level.py:1
**Export:** low_level

**Issue:** `SKILL.md:185` documents `low_level`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `low_level` is a documented extra, a name the source still declares at `cognee/low_level.py:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-063: Documented extra: pipeline_needs_llm

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/tasks/task.py:160
**Export:** pipeline_needs_llm

**Issue:** `SKILL.md:232` documents `pipeline_needs_llm`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `pipeline_needs_llm` is a documented extra, a name the source still declares at `cognee/modules/pipelines/tasks/task.py:160` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-064: Documented extra: pipelines

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/__init__.py:1
**Export:** pipelines

**Issue:** `SKILL.md:8` documents `pipelines`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `pipelines` is a documented extra, a name the source still declares at `cognee/modules/pipelines/__init__.py:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-065: Documented extra: remediation_for

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/remediation.py:146
**Export:** remediation_for

**Issue:** `SKILL.md:258` documents `remediation_for`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `remediation_for` is a documented extra, a name the source still declares at `cognee/exceptions/remediation.py:146` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-067: Documented extra: setup

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/engine/operations/setup.py:9
**Export:** setup

**Issue:** `SKILL.md:185` documents `setup`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `setup` is a documented extra, a name the source still declares at `cognee/modules/engine/operations/setup.py:9` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-069: Documented extra: task

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/tasks/task.py:124
**Export:** task

**Issue:** `SKILL.md:104` documents `task`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `task` is a documented extra, a name the source still declares at `cognee/modules/pipelines/tasks/task.py:124` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-070: Documented extra: task_summary

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/tasks/task.py:169
**Export:** task_summary

**Issue:** `references/full-api-reference.md:564` documents `task_summary`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `task_summary` is a documented extra, a name the source still declares at `cognee/modules/pipelines/tasks/task.py:169` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-071: Documented extra: tools

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/tools/tools.py:1
**Export:** tools

**Issue:** `SKILL.md:13` documents `tools`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `tools` is a documented extra, a name the source still declares at `cognee/api/v1/tools/tools.py:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-072: Documented extra: visualize_graph_json

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/visualize/visualize.py:271
**Export:** visualize_graph_json

**Issue:** `references/full-api-reference.md:337` documents `visualize_graph_json`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `visualize_graph_json` is a documented extra, a name the source still declares at `cognee/api/v1/visualize/visualize.py:271` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-073: Documented extra: visualize_multi_user_graph

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/visualize/visualize.py:611
**Export:** visualize_multi_user_graph

**Issue:** `references/full-api-reference.md:339` documents `visualize_multi_user_graph`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `visualize_multi_user_graph` is a documented extra, a name the source still declares at `cognee/api/v1/visualize/visualize.py:611` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-074: Documented extra: visualize_semantic_json

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/visualize/visualize.py:317
**Export:** visualize_semantic_json

**Issue:** `references/full-api-reference.md:338` documents `visualize_semantic_json`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `visualize_semantic_json` is a documented extra, a name the source still declares at `cognee/api/v1/visualize/visualize.py:317` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-077: multi-denominator reporting — barrel vs documented surface

**Severity:** Info
**Category:** Coverage (multi-denominator)
**Source:** skills/oms-cognee/1.6.2/oms-cognee/metadata.json

**Issue:** barrel=64, documented=56

**Remediation:** No action required: the barrel and the documented surface measure different sets by design, and the report records both counts.

### Discovery Quality

**Discovery Test:** not run: the hard gate blocked the run
