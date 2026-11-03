---
workflowType: 'test-skill'
skillName: 'oms-cognee'
skillDir: 'skills/oms-cognee/1.6.2/oms-cognee'
runId: '20261103T134151Z-12e5ccdf'
testMode: 'naive'
forgeTier: 'Deep'
hardGate: 'passed'
testResult: 'pass'
score: '99%'
threshold: '80%'
thresholdSource: 'workflow default (80%)'
analysisConfidence: 'full'
toolingStatus: 'ok'
workspaceDrift: 'ok'
health_check_dispatched: true
testDate: '2026-11-03T13:41:51Z'
stepsCompleted: ['init', 'detect-mode', 'coverage-check', 'coherence-check', 'external-validators', 'hard-gate', 'score', 'report']
nextWorkflow: 'export-skill'
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

**Mode Rationale:** metadata.json sets `skill_type: 'single'`, so this individual skill is tested in naive mode (API-surface coverage; coherence is structural only and carries no scored category).

**Analysis Plan:**
- Coverage Check: every public export of `cognee/__init__.py` (and the brief's scoped files) checked for documentation in SKILL.md and references/, with AST-backed signature and type verification at Deep tier against the local source at the pinned commit ba3631f.
- Coherence Check: structural only: internal references and links in SKILL.md resolve to files in the package, and the split-body cross-check compares SKILL.md signatures with references/.

## Coverage Analysis

**Tier:** Deep
**Source Access:** full
**Source Path:** /home/armel/.skf/workspace/repos/github.com/topoteretes/cognee
**Workspace Layout:** single package
**Denominator:** barrel (standard-barrel clause, `all` set: 92 exports)

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
| `DistillationResult` | - | yes | - | - | WARN |
| `Drop` | - | yes | - | cognee/pipelines/types.py:32 | PASS |
| `EXPORT_FORMATS` | - | yes | - | cognee/modules/migration/export.py:35 | PASS |
| `Edge` | - | yes | - | - | WARN |
| `EntitySpec` | - | yes | - | - | WARN |
| `ExportResult` | class | yes | yes | cognee/modules/migration/export.py:41 | PASS |
| `ExtendableDataPoint` | - | yes | - | - | WARN |
| `FeedbackEntry` | class | yes | yes | cognee/memory/entries.py:62 | PASS |
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
| `QAEntry` | class | yes | yes | cognee/memory/entries.py:24 | PASS |
| `REMEDIATION_MARKER` | - | yes | - | - | WARN |
| `RecallResponse` | - | yes | - | - | WARN |
| `RememberKwargs` | - | yes | - | - | WARN |
| `RememberResult` | class | yes | - | cognee/api/v1/remember/remember.py:600 | PASS |
| `SearchType` | class | yes | - | cognee/modules/search/types/SearchType.py:4 | PASS |
| `SessionModelUsage` | class | yes | - | cognee/modules/session_lifecycle/models.py:96 | PASS |
| `SessionRecord` | class | yes | - | cognee/modules/session_lifecycle/models.py:10 | PASS |
| `SkillRunEntry` | - | yes | - | - | WARN |
| `Task` | class | yes | yes | cognee/modules/pipelines/tasks/task.py:188 | PASS |
| `TaskSpec` | - | yes | - | - | WARN |
| `TraceEntry` | class | yes | yes | cognee/memory/entries.py:40 | PASS |
| `UpdateResult` | - | yes | - | - | WARN |
| `ValidationIssue` | class | yes | yes | cognee/api/v1/validate/validate.py:99 | PASS |
| `ValidationReport` | class | yes | yes | cognee/api/v1/validate/validate.py:105 | PASS |
| `ValidationStatus` | class | yes | - | cognee/api/v1/validate/validate.py:93 | PASS |
| `ZepSource` | class | yes | yes | cognee/modules/migration/sources/zep.py:57 | PASS |
| `__version__` | - | yes | - | - | WARN |
| `add` | function | yes | yes | cognee/api/v1/add/add.py:39 | PASS |
| `add_data_points` | - | yes | - | - | WARN |
| `add_feedback` | - | yes | - | - | WARN |
| `agent_memory` | function | yes | yes | cognee/modules/agent_memory/decorator.py:29 | PASS |
| `agents` | class | yes | - | cognee/api/v1/agents/agents.py:40 | PASS |
| `apply_write_proposal` | function | yes | yes | cognee/api/v1/tools/tools.py:129 | PASS |
| `build_snapshot` | function | yes | yes | cognee/modules/migration/snapshot.py:243 | PASS |
| `clear_traces` | function | yes | - | cognee/modules/observability/trace_context.py:121 | PASS |
| `cognee_network_visualization` | function | yes | yes | cognee/modules/visualization/cognee_network_visualization.py:154 | PASS |
| `cognify` | function | yes | yes | cognee/api/v1/cognify/cognify.py:110 | PASS |
| `config` | class | yes | - | cognee/api/v1/config/config.py:171 | PASS |
| `datapoint_registry` | function | yes | yes | cognee/modules/migration/snapshot.py:39 | PASS |
| `datasets` | class | yes | - | cognee/api/v1/datasets/datasets.py:105 | PASS |
| `delete` | function | yes | yes | cognee/api/v1/delete/__init__.py:12 | PASS |
| `delete_feedback` | - | yes | - | - | WARN |
| `disable_tracing` | function | yes | - | cognee/modules/observability/trace_context.py:43 | PASS |
| `disconnect` | function | yes | yes | cognee/api/v1/serve/disconnect.py:8 | PASS |
| `distill_session` | - | yes | - | - | WARN |
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
| `get_session` | - | yes | - | - | WARN |
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
| `propose_corrections` | function | yes | yes | cognee/api/v1/tools/tools.py:101 | PASS |
| `propose_sql_write` | function | yes | yes | cognee/api/v1/tools/tools.py:81 | PASS |
| `prune` | class | yes | - | cognee/api/v1/prune/prune.py:5 | PASS |
| `push` | function | yes | yes | cognee/api/v1/push/push.py:96 | PASS |
| `read_archive` | function | yes | yes | cognee/modules/migration/cogx.py:322 | PASS |
| `read_manifest` | function | yes | yes | cognee/modules/migration/cogx.py:276 | PASS |
| `recall` | function | yes | yes | cognee/api/v1/recall/recall.py:347 | PASS |
| `register_sql_connection` | function | yes | yes | cognee/api/v1/tools/tools.py:27 | PASS |
| `rehydrate_node` | function | yes | yes | cognee/modules/migration/snapshot.py:116 | PASS |
| `reject_write_proposal` | function | yes | yes | cognee/api/v1/tools/tools.py:146 | PASS |
| `remediation_for` | - | yes | - | - | WARN |
| `remember` | function | yes | yes | cognee/api/v1/remember/remember.py:867 | PASS |
| `remove_sql_connection` | function | yes | yes | cognee/api/v1/tools/tools.py:73 | PASS |
| `report` | function | yes | yes | cognee/api/v1/report/report.py:13 | PASS |
| `run_custom_pipeline` | function | yes | yes | cognee/modules/run_custom_pipeline/run_custom_pipeline.py:14 | PASS |
| `run_migrations` | - | yes | - | - | WARN |
| `run_pipeline` | function | yes | yes | cognee/modules/pipelines/operations/pipeline.py:53 | PASS |
| `run_relational_migrations` | - | yes | - | - | WARN |
| `run_tasks` | function | yes | yes | cognee/modules/pipelines/operations/run_tasks.py:39 | PASS |
| `run_tasks_parallel` | function | yes | yes | cognee/modules/pipelines/operations/run_parallel.py:8 | PASS |
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
| `validate` | function | yes | yes | cognee/api/v1/validate/validate.py:198 | PASS |
| `visualization_server` | function | yes | yes | cognee/api/v1/visualize/start_visualization_server.py:6 | PASS |
| `visualize` | function | yes | - | cognee/api/v1/visualize/visualize.py:193 | PASS |
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
- **Signature Mismatches:** 0
- **Stale Documentation:** 56, documented extras included
- **Scoped Out by the Brief:** `describe_resolution` (cognee/shared/env_file.py), `load_env_file` (cognee/shared/env_file.py), `run_migrations` (cognee/run_migrations.py), `setup_logging` (cognee/shared/logging_utils.py), `start_visualization_server` (cognee/shared/utils.py), `wait_for_background_tasks` (cognee/infrastructure/background_tasks.py)
- **Nested Entry Points:** `cognee/api/v1/api_keys/routers/__init__.py` inside `cognee/__init__.py`: `get_api_key_management_router`; `cognee/api/v1/cloud/routers/__init__.py` inside `cognee/__init__.py`: `get_checks_router`; `cognee/api/v1/permissions/routers/__init__.py` inside `cognee/__init__.py`: `get_permissions_router`; `cognee/api/v1/settings/routers/__init__.py` inside `cognee/__init__.py`: `get_settings_router`

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 100% |
| Signature Accuracy | 100% |
| Type Coverage | 100% |

**Notes (§2 to §4b):**

- **Inventory (§1, §1a):** this session has no subagent tool, so the main thread read SKILL.md and all four reference files (SKILL.md has no `## Full` headings) and built the §1 JSON itself: 148 documented items, schema-valid on the first pass; the spot-check found `BoundTask`, `config` and `wait_for_background_tasks`. Each function carries its most complete documented signature (the reference's code block where one exists, else SKILL.md's); documented constructor signatures and dataclass/pydantic field lists carry `params` and are compared like functions. Namespace-class members (`config`, `datasets`, `prune`, `agents`) are listed as the class entry's methods. `load_env_file` and `describe_resolution` are not inventoried: the skill names them only as out of scope and describes neither; `setup_logging` and `wait_for_background_tasks` are, because the skill describes what each does (recorded as borderline).
- **Split-body cross-check (§1b):** every export written both in the SKILL.md body and in a reference was compared on parameter name, type, order and optionality, return type and contradicting descriptions: no mismatch (SKILL.md mostly states parameter counts that equal the references' lists, or repeats them verbatim). Borderline: SKILL.md writes `cognee_network_visualization(graph_data, destination_file_path=None, schema_data=None, search_events=None)` with no return type while full-api-reference.md gives `-> str`; an omitted return type is not a contradicting one, so it is not counted.
- **Signature comparison (§2):** no subagent tool, so the main thread compared all 72 checks of the 40 `signature-plan.json` files in one pass, under one rule for every check (the full declaration at the check's line against the documented signature: parameter name, type, order and optionality, and the return type; a missing optional parameter is a mismatch), and saved the per-file results as one JSON list in `signatures-1.txt`. No batching was needed. A documented parameter with no type annotation is compared on name, order and optionality only (the documentation makes no type claim). Three calls are recorded as borderline, each decided as a match: `export` (the check line 16 is the first of three `@overload`s; the documented implementation signature matches lines 49-56 exactly and the references document the overloads too), `visualization_server` (documented "a shutdown() callable"; the source annotates `-> Callable[[], Callable[[], None]]`, whose outer zero-argument callable agrees, while the body returns `shutdown`, which returns None), `run_tasks_parallel` (the compared pipelines-and-datapoints.md signature repeats the annotation verbatim; full-api-reference.md writes `-> Task`, the runtime value both references name).
- **Deep-tier checks:** `gh api repos/topoteretes/cognee/git/ref/tags/v1.6.2` resolves to `ba3631f2ed363a6ea50d649c34c56885af6b36fe`, the workspace HEAD and `metadata.source_commit`; `pyproject.toml:4` reads `version = "1.6.2"`. Type definitions cross-checked against their declarations: `SearchType` (20 members, SearchType.py:4-24), `ValidationStatus` (validate.py:93-96), `MemoryEntry` (entries.py:129), `COGXRecord` (cogx.py:160-162), `IMPORT_MODES` (base.py:19), `EXPORT_FORMATS` (export.py:35), `COGX_VERSION` (cogx.py:22), `Drop` (types.py:32), `session` (session/__init__.py:8-13), `RememberResult` attributes and `SessionRecord`/`SessionModelUsage` columns all match. The recipe runner traced every re-export to its defining file.
- **Stale names:** 56 documented names lie outside the `all` set; `classify-stale` marks none fabricated: 48 are still declared at a `defined_at` line, `pipelines`, `tools` and `start_visualization_server` resolve to modules, and `Edge`, `distill_session`, `migration` and `run_relational_migrations` are declared in several files. Four (`run_migrations`, `setup_logging`, `start_visualization_server`, `wait_for_background_tasks`) are in files the brief scopes out.
- **Metadata coherence (§4b):** `stats.exports_public_api` 102 against `exports[]` 86 (16% drift, Medium); barrel 102 against documented 86 (Info).
- **Numerator (§2b):** `skipped`: metadata.json stores no `stats.effective_denominator`, so the inflation signature (`exports_documented == effective_denominator`) cannot occur.
- **Provenance lines (§4c):** `verify` passes: 86 exports checked, 0 stale lines.

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)

### Structural Findings

| # | Type | Severity | Detail | Line |
|---|------|----------|--------|------|
| - | - | - | No structural finding: §2.1 required sections satisfied (description: `Overview`, usage: `Quick Start`, API surface: `Key API Summary`); §2.2 6 fences, balanced; §2.3 no bare opening fence; §2.4 every function export of the inventory is used in a usage-family section or reference file (`zero_usage` empty); §2.5 every called export's await use matches its description (awaited: `add`, `cognify`, `search`, `remember`, `recall`, `run_pipeline` x2, `add_data_points`; called without await and described sync: the five tracing functions, `run_tasks_parallel`, `task`, `task_summary`); §2.6 no table drift; §2.7 no `scripts/` or `assets/` folder | - |

**Structural Issues:** 0

**Migration section (§2b):** Deep tier and `forge-data/oms-cognee/1.6.2/evidence-report.md` exists, but the report has no YAML frontmatter, so `t2_future_count` cannot be read: the rules treat this as Case 4 and skip. (The Case 4 note's wording, "evidence-report.md not found", does not fit here: the file exists without the pinned field.) SKILL.md has no "Migration & Deprecation Warnings" section; its `## Deprecations & Gotchas` section carries current-state notes.

### Reference Consistency (split-body)

| # | Reference File | Export | Issue | SKILL.md Line | Reference Line |
|---|---------------|--------|-------|---------------|---------------|
| - | - | - | No mismatch | - | - |

**Exports Cross-Checked:** 93
**Mismatches Found:** 0

## External Validation

### skill-check
- **Available:** yes
- **Quality Score:** 90/100
- **Errors:** 0
- **Warnings:** 1
- **Diagnostics:** `body.max_tokens` (warn) at `SKILL.md:1`: body token estimate 5696 exceeds max 5000 (suggestion: reduce body to ~5000 tokens or fewer; the count is a whitespace-split approximation)

### Tessl Review
- **Result:** off — set tessl_review_workspace in preferences.yaml to enable

### Combined External Score
- **External Validation Score:** 90%
- **Tools used:** skill-check

## Completeness Score

### Score Breakdown

| Category | Score | Weight | Weighted |
|----------|-------|--------|----------|
| Export Coverage | 100% | 45% | 45% |
| Signature Accuracy | 100% | 25% | 25% |
| Type Coverage | 100% | 20% | 20% |
| Coherence | not scored | 0% | 0% |
| External Validation | 90% | 10% | 9% |
| **Total** | | **100%** | **99%** |

### Result

**Score:** 99%
**Threshold:** 80%
**Result:** **PASS**

**Threshold Source:** workflow default (80%)
**Weight Distribution:** naive (redistributed)
**Tier Adjustment:** none
**External Validators:** skill-check only
**Analysis Confidence:** full
**Tooling Status:** ok

## Gap Report

**Total Gaps:** 60
**Blocking (Critical + High):** 0
**Non-blocking (Medium + Low + Info):** 60

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|------------------|
| Critical | 0 | None |
| High | 0 | None |
| Medium | 5 | Add type definitions, interface docs or the missing section |
| Low | 1 | Add examples or metadata |
| Info | 54 | Optional improvements, no action required |
| **Total** | **60** | |

### GAP-045: Stale documentation: run_migrations

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:13
**Export:** run_migrations

**Issue:** SKILL.md documents `run_migrations`, which the enumerated source API surface lacks

**Remediation:** Check `run_migrations` against the source and update or remove its documentation at SKILL.md:13: the enumerated source surface does not export it.

### GAP-048: Stale documentation: setup_logging

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:28
**Export:** setup_logging

**Issue:** SKILL.md documents `setup_logging`, which the enumerated source API surface lacks

**Remediation:** Check `setup_logging` against the source and update or remove its documentation at SKILL.md:28: the enumerated source surface does not export it.

### GAP-049: Stale documentation: start_visualization_server

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:29
**Export:** start_visualization_server

**Issue:** SKILL.md documents `start_visualization_server`, which the enumerated source API surface lacks

**Remediation:** Check `start_visualization_server` against the source and update or remove its documentation at SKILL.md:29: the enumerated source surface does not export it.

### GAP-056: Stale documentation: wait_for_background_tasks

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:157
**Export:** wait_for_background_tasks

**Issue:** SKILL.md documents `wait_for_background_tasks`, which the enumerated source API surface lacks

**Remediation:** Check `wait_for_background_tasks` against the source and update or remove its documentation at SKILL.md:157: the enumerated source surface does not export it.

### GAP-057: metadata drift — barrel export counts diverge

**Severity:** Medium
**Category:** Coverage (metadata-drift)
**Source:** skills/oms-cognee/1.6.2/oms-cognee/metadata.json

**Issue:** stats.exports_public_api=102, exports[].length=86 → 16% drift

**Remediation:** Recount the exports and correct the diverging counts in `skills/oms-cognee/1.6.2/oms-cognee/metadata.json`; update-skill applies it as a metadata update.

### GAP-059: skill-check: body.max_tokens

**Severity:** Low
**Category:** External (external-validator)
**Source:** SKILL.md:1

**Issue:** body token estimate 5696 exceeds max 5000 (skill-check whitespace-split approximation)

**Remediation:** Shorten the SKILL.md body to about 5000 whitespace-split tokens or fewer, for example by moving detail from the Key API Summary and Deprecations & Gotchas sections of skills/oms-cognee/1.6.2/oms-cognee/SKILL.md into references/full-api-reference.md, then re-run skill-check.

### GAP-001: Documented extra: BoundTask

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/tasks/task.py:8
**Export:** BoundTask

**Issue:** `SKILL.md:224` documents `BoundTask`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `BoundTask` is a documented extra, a name the source still declares at `cognee/modules/pipelines/tasks/task.py:8` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-002: Documented extra: CogneeApiError

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/exceptions.py:10
**Export:** CogneeApiError

**Issue:** `SKILL.md:288` documents `CogneeApiError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CogneeApiError` is a documented extra, a name the source still declares at `cognee/exceptions/exceptions.py:10` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-003: Documented extra: CogneeConfigurationError

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/exceptions.py:99
**Export:** CogneeConfigurationError

**Issue:** `SKILL.md:110` documents `CogneeConfigurationError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CogneeConfigurationError` is a documented extra, a name the source still declares at `cognee/exceptions/exceptions.py:99` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-004: Documented extra: CogneeSystemError

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/exceptions.py:69
**Export:** CogneeSystemError

**Issue:** `SKILL.md:289` documents `CogneeSystemError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CogneeSystemError` is a documented extra, a name the source still declares at `cognee/exceptions/exceptions.py:69` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-005: Documented extra: CogneeTransientError

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/exceptions.py:114
**Export:** CogneeTransientError

**Issue:** `SKILL.md:292` documents `CogneeTransientError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CogneeTransientError` is a documented extra, a name the source still declares at `cognee/exceptions/exceptions.py:114` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-006: Documented extra: CogneeValidationError

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/exceptions.py:84
**Export:** CogneeValidationError

**Issue:** `SKILL.md:227` documents `CogneeValidationError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CogneeValidationError` is a documented extra, a name the source still declares at `cognee/exceptions/exceptions.py:84` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-007: Documented extra: DataPoint

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/low_level.py:2
**Export:** DataPoint

**Issue:** `SKILL.md:29` documents `DataPoint`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `DataPoint` is a documented extra, a name the source still declares at `cognee/low_level.py:2` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-008: Documented extra: DistillationResult

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/session_distillation/models.py:94
**Export:** DistillationResult

**Issue:** `SKILL.md:147` documents `DistillationResult`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `DistillationResult` is a documented extra, a name the source still declares at `cognee/modules/session_distillation/models.py:94` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-009: Documented extra: Edge

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/infrastructure/engine/models/Edge.py:13
**Export:** Edge

**Issue:** `SKILL.md:221` documents `Edge`, which the enumerated source API surface lacks and the source still declares; of the 5 files that declare it, the skill cites only `cognee/infrastructure/engine/models/Edge.py`

**Remediation:** No change: `Edge` is a documented extra, a name the source still declares at `cognee/infrastructure/engine/models/Edge.py:13` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-010: Documented extra: EntitySpec

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/graph_models/spec.py:90
**Export:** EntitySpec

**Issue:** `references/full-api-reference.md:279` documents `EntitySpec`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `EntitySpec` is a documented extra, a name the source still declares at `cognee/modules/graph_models/spec.py:90` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-011: Documented extra: ExtendableDataPoint

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/infrastructure/engine/models/ExtendableDataPoint.py:4
**Export:** ExtendableDataPoint

**Issue:** `SKILL.md:221` documents `ExtendableDataPoint`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ExtendableDataPoint` is a documented extra, a name the source still declares at `cognee/infrastructure/engine/models/ExtendableDataPoint.py:4` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-012: Documented extra: FromIdentity

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/infrastructure/engine/models/FieldAnnotations.py:95
**Export:** FromIdentity

**Issue:** `SKILL.md:221` documents `FromIdentity`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `FromIdentity` is a documented extra, a name the source still declares at `cognee/infrastructure/engine/models/FieldAnnotations.py:95` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-013: Documented extra: GraphSchemaSpec

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/graph_models/spec.py:108
**Export:** GraphSchemaSpec

**Issue:** `references/full-api-reference.md:279` documents `GraphSchemaSpec`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `GraphSchemaSpec` is a documented extra, a name the source still declares at `cognee/modules/graph_models/spec.py:108` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-014: Documented extra: ImproveKwargs

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/improve/improve.py:88
**Export:** ImproveKwargs

**Issue:** `SKILL.md:159` documents `ImproveKwargs`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ImproveKwargs` is a documented extra, a name the source still declares at `cognee/api/v1/improve/improve.py:88` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-015: Documented extra: ImproveResult

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/improve/result.py:187
**Export:** ImproveResult

**Issue:** `SKILL.md:104` documents `ImproveResult`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ImproveResult` is a documented extra, a name the source still declares at `cognee/modules/improve/result.py:187` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-016: Documented extra: LLMGateway

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/infrastructure/llm/LLMGateway.py:106
**Export:** LLMGateway

**Issue:** `references/core-workflow.md:444` documents `LLMGateway`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LLMGateway` is a documented extra, a name the source still declares at `cognee/infrastructure/llm/LLMGateway.py:106` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-017: Documented extra: PipelineRunCompleted

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/models/PipelineRunInfo.py:34
**Export:** PipelineRunCompleted

**Issue:** `references/full-api-reference.md:267` documents `PipelineRunCompleted`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PipelineRunCompleted` is a documented extra, a name the source still declares at `cognee/modules/pipelines/models/PipelineRunInfo.py:34` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-018: Documented extra: PipelineRunErrored

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/models/PipelineRunInfo.py:42
**Export:** PipelineRunErrored

**Issue:** `references/core-workflow.md:100` documents `PipelineRunErrored`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PipelineRunErrored` is a documented extra, a name the source still declares at `cognee/modules/pipelines/models/PipelineRunInfo.py:42` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-019: Documented extra: PipelineRunInfo

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/models/PipelineRunInfo.py:9
**Export:** PipelineRunInfo

**Issue:** `SKILL.md:134` documents `PipelineRunInfo`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PipelineRunInfo` is a documented extra, a name the source still declares at `cognee/modules/pipelines/models/PipelineRunInfo.py:9` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-020: Documented extra: PipelineRunStarted

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/models/PipelineRunInfo.py:26
**Export:** PipelineRunStarted

**Issue:** `references/full-api-reference.md:267` documents `PipelineRunStarted`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PipelineRunStarted` is a documented extra, a name the source still declares at `cognee/modules/pipelines/models/PipelineRunInfo.py:26` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-021: Documented extra: REMEDIATION_MARKER

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/remediation.py:52
**Export:** REMEDIATION_MARKER

**Issue:** `SKILL.md:294` documents `REMEDIATION_MARKER`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `REMEDIATION_MARKER` is a documented extra, a name the source still declares at `cognee/exceptions/remediation.py:52` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-022: Documented extra: RecallResponse

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/recall/types/RecallResponse.py:91
**Export:** RecallResponse

**Issue:** `SKILL.md:75` documents `RecallResponse`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `RecallResponse` is a documented extra, a name the source still declares at `cognee/modules/recall/types/RecallResponse.py:91` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-023: Documented extra: RememberKwargs

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/remember/remember.py:90
**Export:** RememberKwargs

**Issue:** `SKILL.md:156` documents `RememberKwargs`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `RememberKwargs` is a documented extra, a name the source still declares at `cognee/api/v1/remember/remember.py:90` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-024: Documented extra: SkillRunEntry

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/memory/entries.py:82
**Export:** SkillRunEntry

**Issue:** `SKILL.md:180` documents `SkillRunEntry`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `SkillRunEntry` is a documented extra, a name the source still declares at `cognee/memory/entries.py:82` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-025: Documented extra: TaskSpec

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/tasks/task.py:35
**Export:** TaskSpec

**Issue:** `references/pipelines-and-datapoints.md:36` documents `TaskSpec`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `TaskSpec` is a documented extra, a name the source still declares at `cognee/modules/pipelines/tasks/task.py:35` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-026: Documented extra: UpdateResult

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/update/result.py:37
**Export:** UpdateResult

**Issue:** `references/core-workflow.md:383` documents `UpdateResult`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `UpdateResult` is a documented extra, a name the source still declares at `cognee/api/v1/update/result.py:37` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-027: Documented extra: __version__

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/__init__.py:22
**Export:** __version__

**Issue:** `SKILL.md:28` documents `__version__`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `__version__` is a documented extra, a name the source still declares at `cognee/__init__.py:22` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-028: Documented extra: add_data_points

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/tasks/storage/add_data_points.py:70
**Export:** add_data_points

**Issue:** `SKILL.md:116` documents `add_data_points`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `add_data_points` is a documented extra, a name the source still declares at `cognee/tasks/storage/add_data_points.py:70` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-029: Documented extra: add_feedback

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/session/session.py:113
**Export:** add_feedback

**Issue:** `SKILL.md:147` documents `add_feedback`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `add_feedback` is a documented extra, a name the source still declares at `cognee/api/v1/session/session.py:113` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-030: Documented extra: delete_feedback

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/session/session.py:147
**Export:** delete_feedback

**Issue:** `SKILL.md:147` documents `delete_feedback`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `delete_feedback` is a documented extra, a name the source still declares at `cognee/api/v1/session/session.py:147` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-031: Documented extra: distill_session

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/session_distillation/distill.py:471
**Export:** distill_session

**Issue:** `SKILL.md:147` documents `distill_session`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `cognee/modules/session_distillation/distill.py`

**Remediation:** No change: `distill_session` is a documented extra, a name the source still declares at `cognee/modules/session_distillation/distill.py:471` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-032: Documented extra: find_remediation

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/remediation.py:131
**Export:** find_remediation

**Issue:** `SKILL.md:294` documents `find_remediation`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `find_remediation` is a documented extra, a name the source still declares at `cognee/exceptions/remediation.py:131` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-033: Documented extra: get_default_tasks

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/cognify/cognify.py:565
**Export:** get_default_tasks

**Issue:** `references/core-workflow.md:183` documents `get_default_tasks`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_default_tasks` is a documented extra, a name the source still declares at `cognee/api/v1/cognify/cognify.py:565` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-034: Documented extra: get_errored_run_info

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/models/PipelineRunInfo.py:62
**Export:** get_errored_run_info

**Issue:** `references/full-api-reference.md:574` documents `get_errored_run_info`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_errored_run_info` is a documented extra, a name the source still declares at `cognee/modules/pipelines/models/PipelineRunInfo.py:62` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-035: Documented extra: get_session

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/session/session.py:65
**Export:** get_session

**Issue:** `SKILL.md:147` documents `get_session`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_session` is a documented extra, a name the source still declares at `cognee/api/v1/session/session.py:65` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-036: Documented extra: graph_model_from_spec

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/graph_models/compiler.py:135
**Export:** graph_model_from_spec

**Issue:** `references/full-api-reference.md:279` documents `graph_model_from_spec`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `graph_model_from_spec` is a documented extra, a name the source still declares at `cognee/modules/graph_models/compiler.py:135` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-037: Documented extra: graph_model_to_graph_schema

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/shared/graph_model_utils.py:93
**Export:** graph_model_to_graph_schema

**Issue:** `references/full-api-reference.md:282` documents `graph_model_to_graph_schema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `graph_model_to_graph_schema` is a documented extra, a name the source still declares at `cognee/shared/graph_model_utils.py:93` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-038: Documented extra: graph_schema_to_graph_model

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/shared/graph_model_utils.py:44
**Export:** graph_schema_to_graph_model

**Issue:** `references/full-api-reference.md:282` documents `graph_schema_to_graph_model`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `graph_schema_to_graph_model` is a documented extra, a name the source still declares at `cognee/shared/graph_model_utils.py:44` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-039: Documented extra: graph_spec_to_json_schema

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/graph_models/compiler.py:119
**Export:** graph_spec_to_json_schema

**Issue:** `references/full-api-reference.md:279` documents `graph_spec_to_json_schema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `graph_spec_to_json_schema` is a documented extra, a name the source still declares at `cognee/modules/graph_models/compiler.py:119` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-040: Documented extra: is_tracing_enabled

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/observability/trace_context.py:62
**Export:** is_tracing_enabled

**Issue:** `references/full-api-reference.md:304` documents `is_tracing_enabled`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `is_tracing_enabled` is a documented extra, a name the source still declares at `cognee/modules/observability/trace_context.py:62` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-041: Documented extra: migration

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/migration/__init__.py:1
**Export:** migration

**Issue:** `SKILL.md:28` documents `migration`, which the enumerated source API surface lacks and the source still declares; of the 3 files that declare it, the skill cites only `cognee/migration/__init__.py`

**Remediation:** No change: `migration` is a documented extra, a name the source still declares at `cognee/migration/__init__.py:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-042: Documented extra: pipeline_needs_llm

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/tasks/task.py:160
**Export:** pipeline_needs_llm

**Issue:** `SKILL.md:268` documents `pipeline_needs_llm`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `pipeline_needs_llm` is a documented extra, a name the source still declares at `cognee/modules/pipelines/tasks/task.py:160` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-043: Documented extra: pipelines

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/__init__.py:1
**Export:** pipelines

**Issue:** `SKILL.md:8` documents `pipelines`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `pipelines` is a documented extra, a name the source still declares at `cognee/modules/pipelines/__init__.py:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-044: Documented extra: remediation_for

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/remediation.py:146
**Export:** remediation_for

**Issue:** `SKILL.md:294` documents `remediation_for`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `remediation_for` is a documented extra, a name the source still declares at `cognee/exceptions/remediation.py:146` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-046: Documented extra: run_relational_migrations

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/run_migrations.py:11
**Export:** run_relational_migrations

**Issue:** `references/full-api-reference.md:409` documents `run_relational_migrations`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `cognee/run_migrations.py`

**Remediation:** No change: `run_relational_migrations` is a documented extra, a name the source still declares at `cognee/run_migrations.py:11` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-047: Documented extra: setup

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/engine/operations/setup.py:9
**Export:** setup

**Issue:** `SKILL.md:221` documents `setup`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `setup` is a documented extra, a name the source still declares at `cognee/modules/engine/operations/setup.py:9` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-050: Documented extra: task

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/tasks/task.py:124
**Export:** task

**Issue:** `SKILL.md:104` documents `task`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `task` is a documented extra, a name the source still declares at `cognee/modules/pipelines/tasks/task.py:124` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-051: Documented extra: task_summary

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/tasks/task.py:169
**Export:** task_summary

**Issue:** `references/full-api-reference.md:564` documents `task_summary`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `task_summary` is a documented extra, a name the source still declares at `cognee/modules/pipelines/tasks/task.py:169` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-052: Documented extra: tools

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/tools/tools.py:1
**Export:** tools

**Issue:** `SKILL.md:13` documents `tools`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `tools` is a documented extra, a name the source still declares at `cognee/api/v1/tools/tools.py:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-053: Documented extra: visualize_graph_json

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/visualize/visualize.py:271
**Export:** visualize_graph_json

**Issue:** `references/full-api-reference.md:337` documents `visualize_graph_json`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `visualize_graph_json` is a documented extra, a name the source still declares at `cognee/api/v1/visualize/visualize.py:271` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-054: Documented extra: visualize_multi_user_graph

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/visualize/visualize.py:611
**Export:** visualize_multi_user_graph

**Issue:** `references/full-api-reference.md:339` documents `visualize_multi_user_graph`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `visualize_multi_user_graph` is a documented extra, a name the source still declares at `cognee/api/v1/visualize/visualize.py:611` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-055: Documented extra: visualize_semantic_json

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/visualize/visualize.py:317
**Export:** visualize_semantic_json

**Issue:** `references/full-api-reference.md:338` documents `visualize_semantic_json`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `visualize_semantic_json` is a documented extra, a name the source still declares at `cognee/api/v1/visualize/visualize.py:317` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-058: multi-denominator reporting — barrel vs documented surface

**Severity:** Info
**Category:** Coverage (multi-denominator)
**Source:** skills/oms-cognee/1.6.2/oms-cognee/metadata.json

**Issue:** barrel=102, documented=86

**Remediation:** No action required: the barrel and the documented surface measure different sets by design, and the report records both counts.

### GAP-060: Discovery testing not performed: subagents unavailable, routing test requires isolated context

**Severity:** Info
**Category:** Discovery (discovery)
**Source:** SKILL.md:3

**Issue:** The catalog holds 4 skills (oms-cocoindex, oms-cognee, oms-storybook-react-vite, oms-uitripled), but this headless session cannot spawn isolated subagents, so the routing test was not run and is not counted PASS or FAIL.

**Remediation:** Re-run skf-test-skill for oms-cognee in an environment that can spawn subagents, so §4b.2 can route three realistic prompts against the 4-skill catalog using the description in skills/oms-cognee/1.6.2/oms-cognee/SKILL.md frontmatter.

### Discovery Quality

**Discovery Test:** skipped: subagents unavailable, routing test requires isolated context

discovery: skipped, subagents unavailable, routing test requires isolated context (catalog: 4 skills; the main thread knows the skill under test, so it does not answer the routing itself). No description hints: Tessl Review did not run and skill-check flagged no description issue.
