---
workflowType: 'test-skill'
skillName: 'oms-cognee'
skillDir: 'skills/oms-cognee/1.6.2/oms-cognee'
runId: '20261103T121357Z-2a66250d'
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
testDate: '2026-11-03T12:13:57Z'
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

**Mode Rationale:** metadata.json sets `skill_type: 'single'`, an individual skill, so naive mode applies (API-surface coverage; coherence is structural only and not scored).

**Analysis Plan:**
- Coverage Check: every public export of `cognee/__init__.py` at the pinned commit ba3631f checked for documentation in SKILL.md and references/, with AST-backed signature verification (Deep tier: ast-grep, gh, QMD available) of each documented signature against the source, including the split-body cross-check between SKILL.md and references/.
- Coherence Check: structural checks only (internal references resolve, sections present), no coherence category in scoring.

## Coverage Analysis

**Tier:** Deep
**Source Access:** full
**Source Path:** /home/armel/.skf/workspace/repos/github.com/topoteretes/cognee
**Workspace Layout:** single package
**Denominator:** barrel (standard-barrel clause, `all` set: 66 exports)

**Files Analyzed:** 46

### Export Coverage

| Export | Type | Documented | Signature | Source Location | Status |
|--------|------|------------|-----------|-----------------|--------|
| `BoundTask` | - | yes | - | - | WARN |
| `COGXArchiveSource` | - | yes | - | - | WARN |
| `COGXDocument` | - | yes | - | - | WARN |
| `COGXEntity` | - | yes | - | - | WARN |
| `COGXEpisode` | - | yes | - | - | WARN |
| `COGXFact` | - | yes | - | - | WARN |
| `COGXManifest` | - | yes | - | - | WARN |
| `COGXMemory` | - | yes | - | - | WARN |
| `COGXMemoryBlock` | - | yes | - | - | WARN |
| `COGXRawNode` | - | yes | - | - | WARN |
| `COGXRecord` | - | yes | - | - | WARN |
| `COGXScope` | - | yes | - | - | WARN |
| `COGXTurn` | - | yes | - | - | WARN |
| `COGX_VERSION` | - | yes | - | - | WARN |
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
| `FeedbackEntry` | class | yes | yes | cognee/memory/entries.py:62 | PASS |
| `FromIdentity` | - | yes | - | - | WARN |
| `GraphEdge` | - | yes | - | - | WARN |
| `GraphSchemaSpec` | - | yes | - | - | WARN |
| `GraphSnapshot` | - | yes | - | - | WARN |
| `GraphitiSource` | - | yes | - | - | WARN |
| `IMPORT_MODES` | - | yes | - | - | WARN |
| `ImproveKwargs` | - | yes | - | - | WARN |
| `ImproveResult` | - | yes | - | - | WARN |
| `LettaSource` | - | yes | - | - | WARN |
| `Mem0Source` | - | yes | - | - | WARN |
| `MemoryEntry` | - | yes | - | cognee/memory/entries.py:129 | PASS |
| `MemorySource` | - | yes | - | - | WARN |
| `PipelineRunCompleted` | - | yes | - | - | WARN |
| `PipelineRunErrored` | - | yes | - | - | WARN |
| `PipelineRunInfo` | - | yes | - | - | WARN |
| `PipelineRunStarted` | - | yes | - | - | WARN |
| `PushResult` | class | yes | yes | cognee/api/v1/push/push.py:26 | PASS |
| `QAEntry` | class | yes | yes | cognee/memory/entries.py:24 | PASS |
| `REMEDIATION_MARKER` | - | yes | - | - | WARN |
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
| `ZepSource` | - | yes | - | - | WARN |
| `__version__` | - | yes | - | - | WARN |
| `add` | function | yes | yes | cognee/api/v1/add/add.py:39 | PASS |
| `add_data_points` | - | yes | - | - | WARN |
| `add_feedback` | - | yes | - | - | WARN |
| `agent_memory` | function | yes | yes | cognee/modules/agent_memory/decorator.py:29 | PASS |
| `agents` | class | yes | - | cognee/api/v1/agents/agents.py:40 | PASS |
| `apply_write_proposal` | function | yes | yes | cognee/api/v1/tools/tools.py:129 | PASS |
| `build_snapshot` | - | yes | - | - | WARN |
| `clear_traces` | function | yes | - | cognee/modules/observability/trace_context.py:121 | PASS |
| `cognee_network_visualization` | function | yes | yes | cognee/modules/visualization/cognee_network_visualization.py:154 | PASS |
| `cognify` | function | yes | yes | cognee/api/v1/cognify/cognify.py:110 | PASS |
| `config` | class | yes | - | cognee/api/v1/config/config.py:171 | PASS |
| `datapoint_registry` | - | yes | - | - | WARN |
| `datasets` | class | yes | - | cognee/api/v1/datasets/datasets.py:105 | PASS |
| `delete` | function | yes | yes | cognee/api/v1/delete/__init__.py:12 | PASS |
| `delete_feedback` | - | yes | - | - | WARN |
| `disable_tracing` | function | yes | - | cognee/modules/observability/trace_context.py:43 | PASS |
| `disconnect` | function | yes | yes | cognee/api/v1/serve/disconnect.py:8 | PASS |
| `distill_session` | - | yes | - | - | WARN |
| `enable_tracing` | function | yes | yes | cognee/modules/observability/trace_context.py:18 | PASS |
| `export` | function | yes | no | cognee/api/v1/export/export.py:16 | FAIL |
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
| `graph_spec_to_json_schema` | - | yes | - | - | WARN |
| `improve` | function | yes | yes | cognee/api/v1/improve/improve.py:101 | PASS |
| `is_tracing_enabled` | - | yes | - | - | WARN |
| `list_sql_connections` | function | yes | yes | cognee/api/v1/tools/tools.py:65 | PASS |
| `list_write_proposals` | function | yes | yes | cognee/api/v1/tools/tools.py:119 | PASS |
| `logger` | - | yes | - | cognee/__init__.py:34 | PASS |
| `memify` | function | yes | yes | cognee/modules/memify/memify.py:27 | PASS |
| `migration` | - | yes | - | - | WARN |
| `pipelines` | - | yes | - | - | WARN |
| `propose_corrections` | function | yes | yes | cognee/api/v1/tools/tools.py:101 | PASS |
| `propose_sql_write` | function | yes | yes | cognee/api/v1/tools/tools.py:81 | PASS |
| `prune` | class | yes | - | cognee/api/v1/prune/prune.py:5 | PASS |
| `push` | function | yes | yes | cognee/api/v1/push/push.py:96 | PASS |
| `read_archive` | - | yes | - | - | WARN |
| `read_manifest` | - | yes | - | - | WARN |
| `recall` | function | yes | yes | cognee/api/v1/recall/recall.py:347 | PASS |
| `register_sql_connection` | function | yes | yes | cognee/api/v1/tools/tools.py:27 | PASS |
| `rehydrate_node` | - | yes | - | - | WARN |
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
| `run_tasks_parallel` | function | yes | no | cognee/modules/pipelines/operations/run_parallel.py:8 | FAIL |
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
| `visualization_server` | function | yes | no | cognee/api/v1/visualize/start_visualization_server.py:6 | FAIL |
| `visualize` | function | yes | - | cognee/api/v1/visualize/visualize.py:193 | PASS |
| `visualize_graph` | function | yes | yes | cognee/api/v1/visualize/visualize.py:193 | PASS |
| `visualize_graph_json` | - | yes | - | - | WARN |
| `visualize_memory_provenance` | function | yes | yes | cognee/api/v1/visualize/memory_provenance.py:848 | PASS |
| `visualize_multi_user_graph` | - | yes | - | - | WARN |
| `visualize_semantic_json` | - | yes | - | - | WARN |

### Coverage Summary

- **Exports Found:** 66
- **Documented:** 66 (100%)
- **Missing Documentation:** 0
- **Signature Mismatches:** 3
- **Stale Documentation:** 74, documented extras included
- **Scoped Out by the Brief:** `COGXArchiveSource` (cognee/modules/migration/sources/cogx_archive.py), `COGXDocument` (cognee/modules/migration/cogx.py), `COGXEntity` (cognee/modules/migration/cogx.py), `COGXEpisode` (cognee/modules/migration/cogx.py), `COGXFact` (cognee/modules/migration/cogx.py), `COGXManifest` (cognee/modules/migration/cogx.py), `COGXMemory` (cognee/modules/migration/cogx.py), `COGXMemoryBlock` (cognee/modules/migration/cogx.py), `COGXRawNode` (cognee/modules/migration/cogx.py), `COGXRecord` (cognee/modules/migration/cogx.py), `COGXScope` (cognee/modules/migration/cogx.py), `COGXTurn` (cognee/modules/migration/cogx.py), `COGX_VERSION` (cognee/modules/migration/cogx.py), `GraphEdge` (cognee/modules/migration/snapshot.py), `GraphSnapshot` (cognee/modules/migration/snapshot.py), `GraphitiSource` (cognee/modules/migration/sources/zep.py), `IMPORT_MODES` (cognee/modules/migration/sources/base.py), `LettaSource` (cognee/modules/migration/sources/letta.py), `Mem0Source` (cognee/modules/migration/sources/mem0.py), `MemorySource` (cognee/modules/migration/sources/base.py), `ZepSource` (cognee/modules/migration/sources/zep.py), `build_snapshot` (cognee/modules/migration/snapshot.py), `datapoint_registry` (cognee/modules/migration/snapshot.py), `describe_resolution` (cognee/shared/env_file.py), `load_env_file` (cognee/shared/env_file.py), `read_archive` (cognee/modules/migration/cogx.py), `read_manifest` (cognee/modules/migration/cogx.py), `rehydrate_node` (cognee/modules/migration/snapshot.py), `run_migrations` (cognee/run_migrations.py), `setup_logging` (cognee/shared/logging_utils.py), `start_visualization_server` (cognee/shared/utils.py), `wait_for_background_tasks` (cognee/infrastructure/background_tasks.py)
- **Nested Entry Points:** `cognee/api/v1/api_keys/routers/__init__.py` inside `cognee/__init__.py`: `get_api_key_management_router`; `cognee/api/v1/cloud/routers/__init__.py` inside `cognee/__init__.py`: `get_checks_router`; `cognee/api/v1/permissions/routers/__init__.py` inside `cognee/__init__.py`: `get_permissions_router`; `cognee/api/v1/settings/routers/__init__.py` inside `cognee/__init__.py`: `get_settings_router`

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 100% |
| Signature Accuracy | 93.88% |
| Type Coverage | 100% |

**Notes:**

- **Inventory (§1, §1a):** this session has no subagent tool, so the main thread read SKILL.md and all four reference files (SKILL.md has no `## Full` headings) and built the §1 JSON itself: 158 documented items, schema-valid on the first pass; the spot-check found `BoundTask`, `disable_tracing` and `visualize_semantic_json`. Each function carries its most complete documented signature, from the reference that holds its Full section; class constructors and documented dataclass/pydantic field lists carry `params` and are compared like functions. The four bootstrap names the skill declares out of scope (`load_env_file`, `describe_resolution`, `setup_logging`, `wait_for_background_tasks`) are not inventoried.
- **Split-body cross-check (§1b): 0 mismatches.** After the hand fix, the SKILL.md `Key params` cells of `add`, `cognify`, `search`, `memify`, `update` and `run_custom_pipeline` give a parameter count and a link instead of a partial signature, and each count matches the reference (16 + `**kwargs`, 23 + `**kwargs`, 27, 10, 15, 12); the `datasets`, `session`, `agents` and `tools` rows name their members and state the optional `user`, as the reference tables do; the exceptions paragraph says all six `__init__` parameters are optional, as `full-api-reference.md:533-535` shows. Every signature written in both places (`prune_system`, `visualize_graph`, `cognee_network_visualization`, `push`, `PushResult`, `export`, `ExportResult`, `report`, `validate`, `ValidationReport`, `ValidationIssue`, `get_schema_inventory`, the provenance pair, `Task`, `run_migrations`, `get_cognee_version`, `distill_session`'s return) agrees on parameter names, order, optionality and return type. Recorded borderline and not as mismatches: SKILL.md writes untyped parameter lists where the reference adds the types (`visualize_graph`, `push`, `export`, `report`, `validate`, `get_schema_inventory`, the provenance pair, `cognee_network_visualization`), and states no return type for `add` and `cognee_network_visualization` where the reference does: silence, with no type that contradicts the reference.
- **Signature comparisons (§2): 49 checks over 33 files, 3 mismatches**, judged in the main thread with the step's rule verbatim (params: name, type, order, optionality; and the return type). All three are flagged BORDERLINE in their Issue: `export` (the plan's line 16 is the first `@overload`; the documented implementation signature matches `export.py:49-56` exactly and the reference documents that overload verbatim), `visualization_server` and `run_tasks_parallel` (the doc states the runtime return; the declared annotation is the wrong one). Recorded under `borderline` in `signatures-1.txt` and not scored: 13 signatures where the doc is silent on parameter types or a return annotation the source declares (`delete`, `forget`, `improve`, `PushResult`, `remember`, `serve`, `start_ui`, `ValidationIssue`, `agent_memory`, `ExportResult`, `export_dataset`, `enable_tracing`, `cognee_network_visualization`), with `start_ui`'s `Optional[subprocess.Popen]` against `subprocess.Popen | None` (one type, two spellings).
- **Deep-tier checks:** `gh api repos/topoteretes/cognee/git/ref/tags/v1.6.2` resolves to `ba3631f2ed363a6ea50d649c34c56885af6b36fe`, the workspace HEAD and `metadata.source_commit`; `pyproject.toml:4` reads `version = "1.6.2"`. The recipe runner traced every re-export to its defining file; the 17 surface types are all documented (Type Coverage 100%).
- **Brief scope:** the stale-scope guard does not fire: every `scope.include` glob matches a file at the pinned commit. The brief scopes out 32 root exports (`excluded.outsideScope` above), among them the 28 `cognee.migration` names, `run_migrations` and `start_visualization_server`; four routers in nested `__init__.py` files stay out of the `all` set.
- **Stale names:** 74 documented names lie outside the `all` set; `classify-stale` marks none fabricated: 70 are still declared at a `defined_at` line, and `Edge`, `distill_session`, `migration` and `run_relational_migrations` are declared in several files.
- **Metadata coherence (§4b):** Medium `metadata-drift`: `stats.exports_public_api`=102 against `exports[].length`=86 (16% drift); Info `multi-denominator`: barrel 102 against documented 86.
- **Numerator ground truth (§2b):** skipped (no inflation signature: declared 86, no stored `effective_denominator`).
- **Provenance line check (§4c):** `verify` passed: 86 entries checked, 0 missing, 0 orphaned, 0 stale lines (3 line checks skipped by the helper).

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)

### Structural Findings

| # | Type | Severity | Detail | Line |
|---|------|----------|--------|------|
| - | - | - | No structural issue: the three required families are present (`Overview` for description, `Quick Start` for usage, `Key API Summary` for the API surface); 6 code fences, balanced, each opening fence tagged; no table row drift; no `scripts/` or `assets/` folder; all 87 inventoried function and method exports are used in a usage-family section or reference file (`zero_usage` empty, split body); no async/sync contradiction (the awaited calls `add`, `cognify`, `search`, `remember`, `recall`, `prune_data`, `prune_system`, `add_data_points` and both `run_pipeline` forms are async in the skill and the source; the tracing functions, `run_tasks_parallel`, `task` and `task_summary` are sync and called without `await`; the one call located for `get`, inventoried as the async `agents.get`, is `cognee.config.get(...)` at `references/config.md:112`, a different, sync API) | - |

**Structural Issues:** 0

**Migration section (§2b):** Section 4b verification skipped (Case 4): `forge-data/oms-cognee/1.6.2/evidence-report.md` exists but carries no YAML frontmatter, so the detection contract reads no pinned `t2_future_count`. SKILL.md has no "Migration & Deprecation Warnings" section; its current-state notes sit under `## Deprecations & Gotchas`.

### Reference Consistency (split-body)

| # | Reference File | Export | Issue | SKILL.md Line | Reference Line |
|---|---------------|--------|-------|---------------|---------------|
| - | - | - | No mismatch | - | - |

**Exports Cross-Checked:** 69
**Mismatches Found:** 0

The 13 rows the previous strict run (20261103T100018Z-79591395) recorded are gone: SKILL.md's Key params cells for `add`, `cognify`, `search`, `memify`, `update` and `run_custom_pipeline` now give a parameter count and a link to the reference section, which matches each count; the `datasets`, `session`, `agents` and `tools` rows name the members and state the optional `user`; the Gotchas link to the lightweight `run_pipeline` signature instead of restating it; the exceptions paragraph says all six `__init__` parameters are optional. Borderline and not recorded (no contradicting type, only silence): untyped SKILL.md parameter lists where the reference adds types, and the missing return type of `add` and `cognee_network_visualization` in SKILL.md.

## External Validation

### skill-check
- **Available:** yes
- **Quality Score:** 90/100
- **Errors:** 0
- **Warnings:** 1
- **Diagnostics:** `body.max_tokens` (warn) at `SKILL.md:1`: body token estimate 5696 exceeds max 5000 (suggestion: reduce body to ~5000 tokens or fewer)

### Tessl Review
- **Result:** off — set tessl_review_workspace in preferences.yaml to enable

### Combined External Score
- **External Validation Score:** 90%
- **Tools used:** skill-check

## Completeness Score

**Result:** **FAIL**, not scored: the hard gate blocked this run on 3 Critical or High gap(s), listed first in the Gap Report.

## Gap Report

**Total Gaps:** 80
**Blocking (Critical + High):** 3
**Non-blocking (Medium + Low + Info):** 77

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|------------------|
| Critical | 3 | Read the source code and write or correct the documentation |
| High | 0 | None |
| Medium | 29 | Add type definitions, interface docs or the missing section |
| Low | 1 | Add examples or metadata |
| Info | 47 | Optional improvements, no action required |
| **Total** | **80** | |

### GAP-001: Signature mismatch: export

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** cognee/api/v1/export/export.py:16
**Export:** export

**Issue:** documented `(dataset: str | UUID = DEFAULT_DATASET_NAME, format: str = "pydantic", destination: str | Path | None = None, user=None, link_relations: bool = False, include_permissions: bool = False) -> ExportResult | GraphSnapshot`, source `@overload (dataset: str | UUID = DEFAULT_DATASET_NAME, format: Literal["pydantic"] = "pydantic", destination: str | Path | None = None, user=None, link_relations: bool = False, include_permissions: bool = False) -> GraphSnapshot`: BORDERLINE: line 16 is the first of three @overload stubs; against it `format` is documented as str where it declares Literal["pydantic"], and the return as ExportResult | GraphSnapshot where it declares GraphSnapshot. The documented signature is the implementation at export.py:49-56, which it matches exactly, and full-api-reference.md:433-436 documents this overload verbatim.

**Remediation:** Update the documented signature of `export` from `(dataset: str | UUID = DEFAULT_DATASET_NAME, format: str = "pydantic", destination: str | Path | None = None, user=None, link_relations: bool = False, include_permissions: bool = False) -> ExportResult | GraphSnapshot` to `@overload (dataset: str | UUID = DEFAULT_DATASET_NAME, format: Literal["pydantic"] = "pydantic", destination: str | Path | None = None, user=None, link_relations: bool = False, include_permissions: bool = False) -> GraphSnapshot`, the signature the source defines at `cognee/api/v1/export/export.py:16`.

### GAP-002: Signature mismatch: visualization_server

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** cognee/api/v1/visualize/start_visualization_server.py:6
**Export:** visualization_server

**Issue:** documented `(port) -> shutdown() callable, a no-argument function (Callable[[], None])`, source `(port) -> Callable[[], Callable[[], None]]`: BORDERLINE: return type differs: the doc states the runtime return, the no-argument shutdown function, where line 6 annotates Callable[[], Callable[[], None]]; line 19 returns cognee.shared.utils.start_visualization_server(port=port), which returns shutdown, so the declared annotation is the wrong one.

**Remediation:** Update the documented signature of `visualization_server` from `(port) -> shutdown() callable, a no-argument function (Callable[[], None])` to `(port) -> Callable[[], Callable[[], None]]`, the signature the source defines at `cognee/api/v1/visualize/start_visualization_server.py:6`.

### GAP-003: Signature mismatch: run_tasks_parallel

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** cognee/modules/pipelines/operations/run_parallel.py:8
**Export:** run_tasks_parallel

**Issue:** documented `(tasks) -> Task  [references/full-api-reference.md:268; references/pipelines-and-datapoints.md:278 gives the declared annotation with the note '# actually returns Task(parallel_run)']`, source `(tasks: list[Task]) -> Callable[[Any], Generator[Any, Any, Any]]`: BORDERLINE: return type differs: full-api-reference.md documents -> Task where line 8 annotates Callable[[Any], Generator[Any, Any, Any]]; line 15 returns Task(parallel_run), so the doc states the runtime return and the declared annotation is the wrong one. The two reference files also disagree with each other.

**Remediation:** Update the documented signature of `run_tasks_parallel` from `(tasks) -> Task  [references/full-api-reference.md:268; references/pipelines-and-datapoints.md:278 gives the declared annotation with the note '# actually returns Task(parallel_run)']` to `(tasks: list[Task]) -> Callable[[Any], Generator[Any, Any, Any]]`, the signature the source defines at `cognee/modules/pipelines/operations/run_parallel.py:8`.

### GAP-005: Stale documentation: COGXArchiveSource

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:125
**Export:** COGXArchiveSource

**Issue:** SKILL.md documents `COGXArchiveSource`, which the enumerated source API surface lacks

**Remediation:** Check `COGXArchiveSource` against the source and update or remove its documentation at SKILL.md:125: the enumerated source surface does not export it.

### GAP-006: Stale documentation: COGXDocument

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:196
**Export:** COGXDocument

**Issue:** SKILL.md documents `COGXDocument`, which the enumerated source API surface lacks

**Remediation:** Check `COGXDocument` against the source and update or remove its documentation at SKILL.md:196: the enumerated source surface does not export it.

### GAP-007: Stale documentation: COGXEntity

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:194
**Export:** COGXEntity

**Issue:** SKILL.md documents `COGXEntity`, which the enumerated source API surface lacks

**Remediation:** Check `COGXEntity` against the source and update or remove its documentation at SKILL.md:194: the enumerated source surface does not export it.

### GAP-008: Stale documentation: COGXEpisode

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:194
**Export:** COGXEpisode

**Issue:** SKILL.md documents `COGXEpisode`, which the enumerated source API surface lacks

**Remediation:** Check `COGXEpisode` against the source and update or remove its documentation at SKILL.md:194: the enumerated source surface does not export it.

### GAP-009: Stale documentation: COGXFact

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:194
**Export:** COGXFact

**Issue:** SKILL.md documents `COGXFact`, which the enumerated source API surface lacks

**Remediation:** Check `COGXFact` against the source and update or remove its documentation at SKILL.md:194: the enumerated source surface does not export it.

### GAP-010: Stale documentation: COGXManifest

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:204
**Export:** COGXManifest

**Issue:** SKILL.md documents `COGXManifest`, which the enumerated source API surface lacks

**Remediation:** Check `COGXManifest` against the source and update or remove its documentation at SKILL.md:204: the enumerated source surface does not export it.

### GAP-011: Stale documentation: COGXMemory

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:193
**Export:** COGXMemory

**Issue:** SKILL.md documents `COGXMemory`, which the enumerated source API surface lacks

**Remediation:** Check `COGXMemory` against the source and update or remove its documentation at SKILL.md:193: the enumerated source surface does not export it.

### GAP-012: Stale documentation: COGXMemoryBlock

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:196
**Export:** COGXMemoryBlock

**Issue:** SKILL.md documents `COGXMemoryBlock`, which the enumerated source API surface lacks

**Remediation:** Check `COGXMemoryBlock` against the source and update or remove its documentation at SKILL.md:196: the enumerated source surface does not export it.

### GAP-013: Stale documentation: COGXRawNode

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:202
**Export:** COGXRawNode

**Issue:** SKILL.md documents `COGXRawNode`, which the enumerated source API surface lacks

**Remediation:** Check `COGXRawNode` against the source and update or remove its documentation at SKILL.md:202: the enumerated source surface does not export it.

### GAP-014: Stale documentation: COGXRecord

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:203
**Export:** COGXRecord

**Issue:** SKILL.md documents `COGXRecord`, which the enumerated source API surface lacks

**Remediation:** Check `COGXRecord` against the source and update or remove its documentation at SKILL.md:203: the enumerated source surface does not export it.

### GAP-015: Stale documentation: COGXScope

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:199
**Export:** COGXScope

**Issue:** SKILL.md documents `COGXScope`, which the enumerated source API surface lacks

**Remediation:** Check `COGXScope` against the source and update or remove its documentation at SKILL.md:199: the enumerated source surface does not export it.

### GAP-016: Stale documentation: COGXTurn

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:201
**Export:** COGXTurn

**Issue:** SKILL.md documents `COGXTurn`, which the enumerated source API surface lacks

**Remediation:** Check `COGXTurn` against the source and update or remove its documentation at SKILL.md:201: the enumerated source surface does not export it.

### GAP-017: Stale documentation: COGX_VERSION

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:198
**Export:** COGX_VERSION

**Issue:** SKILL.md documents `COGX_VERSION`, which the enumerated source API surface lacks

**Remediation:** Check `COGX_VERSION` against the source and update or remove its documentation at SKILL.md:198: the enumerated source surface does not export it.

### GAP-028: Stale documentation: GraphEdge

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:209
**Export:** GraphEdge

**Issue:** SKILL.md documents `GraphEdge`, which the enumerated source API surface lacks

**Remediation:** Check `GraphEdge` against the source and update or remove its documentation at SKILL.md:209: the enumerated source surface does not export it.

### GAP-030: Stale documentation: GraphSnapshot

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:125
**Export:** GraphSnapshot

**Issue:** SKILL.md documents `GraphSnapshot`, which the enumerated source API surface lacks

**Remediation:** Check `GraphSnapshot` against the source and update or remove its documentation at SKILL.md:125: the enumerated source surface does not export it.

### GAP-031: Stale documentation: GraphitiSource

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:195
**Export:** GraphitiSource

**Issue:** SKILL.md documents `GraphitiSource`, which the enumerated source API surface lacks

**Remediation:** Check `GraphitiSource` against the source and update or remove its documentation at SKILL.md:195: the enumerated source surface does not export it.

### GAP-032: Stale documentation: IMPORT_MODES

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:191
**Export:** IMPORT_MODES

**Issue:** SKILL.md documents `IMPORT_MODES`, which the enumerated source API surface lacks

**Remediation:** Check `IMPORT_MODES` against the source and update or remove its documentation at SKILL.md:191: the enumerated source surface does not export it.

### GAP-035: Stale documentation: LettaSource

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:125
**Export:** LettaSource

**Issue:** SKILL.md documents `LettaSource`, which the enumerated source API surface lacks

**Remediation:** Check `LettaSource` against the source and update or remove its documentation at SKILL.md:125: the enumerated source surface does not export it.

### GAP-036: Stale documentation: Mem0Source

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:125
**Export:** Mem0Source

**Issue:** SKILL.md documents `Mem0Source`, which the enumerated source API surface lacks

**Remediation:** Check `Mem0Source` against the source and update or remove its documentation at SKILL.md:125: the enumerated source surface does not export it.

### GAP-037: Stale documentation: MemorySource

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:125
**Export:** MemorySource

**Issue:** SKILL.md documents `MemorySource`, which the enumerated source API surface lacks

**Remediation:** Check `MemorySource` against the source and update or remove its documentation at SKILL.md:125: the enumerated source surface does not export it.

### GAP-047: Stale documentation: ZepSource

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:125
**Export:** ZepSource

**Issue:** SKILL.md documents `ZepSource`, which the enumerated source API surface lacks

**Remediation:** Check `ZepSource` against the source and update or remove its documentation at SKILL.md:125: the enumerated source surface does not export it.

### GAP-051: Stale documentation: build_snapshot

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:211
**Export:** build_snapshot

**Issue:** SKILL.md documents `build_snapshot`, which the enumerated source API surface lacks

**Remediation:** Check `build_snapshot` against the source and update or remove its documentation at SKILL.md:211: the enumerated source surface does not export it.

### GAP-052: Stale documentation: datapoint_registry

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:212
**Export:** datapoint_registry

**Issue:** SKILL.md documents `datapoint_registry`, which the enumerated source API surface lacks

**Remediation:** Check `datapoint_registry` against the source and update or remove its documentation at SKILL.md:212: the enumerated source surface does not export it.

### GAP-064: Stale documentation: read_archive

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:206
**Export:** read_archive

**Issue:** SKILL.md documents `read_archive`, which the enumerated source API surface lacks

**Remediation:** Check `read_archive` against the source and update or remove its documentation at SKILL.md:206: the enumerated source surface does not export it.

### GAP-065: Stale documentation: read_manifest

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:198
**Export:** read_manifest

**Issue:** SKILL.md documents `read_manifest`, which the enumerated source API surface lacks

**Remediation:** Check `read_manifest` against the source and update or remove its documentation at SKILL.md:198: the enumerated source surface does not export it.

### GAP-066: Stale documentation: rehydrate_node

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:213
**Export:** rehydrate_node

**Issue:** SKILL.md documents `rehydrate_node`, which the enumerated source API surface lacks

**Remediation:** Check `rehydrate_node` against the source and update or remove its documentation at SKILL.md:213: the enumerated source surface does not export it.

### GAP-068: Stale documentation: run_migrations

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:13
**Export:** run_migrations

**Issue:** SKILL.md documents `run_migrations`, which the enumerated source API surface lacks

**Remediation:** Check `run_migrations` against the source and update or remove its documentation at SKILL.md:13: the enumerated source surface does not export it.

### GAP-071: Stale documentation: start_visualization_server

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:29
**Export:** start_visualization_server

**Issue:** SKILL.md documents `start_visualization_server`, which the enumerated source API surface lacks

**Remediation:** Check `start_visualization_server` against the source and update or remove its documentation at SKILL.md:29: the enumerated source surface does not export it.

### GAP-078: metadata drift — barrel export counts diverge

**Severity:** Medium
**Category:** Coverage (metadata-drift)
**Source:** skills/oms-cognee/1.6.2/oms-cognee/metadata.json

**Issue:** stats.exports_public_api=102, exports[].length=86 → 16% drift

**Remediation:** Recount the exports and correct the diverging counts in `skills/oms-cognee/1.6.2/oms-cognee/metadata.json`; update-skill applies it as a metadata update.

### GAP-080: skill-check: body.max_tokens

**Severity:** Low
**Category:** External (external-validator)
**Source:** skills/oms-cognee/1.6.2/oms-cognee/SKILL.md:1

**Issue:** body token estimate 5696 exceeds max 5000

**Remediation:** Reduce body to ~5000 tokens or fewer (skill-check's token count is a whitespace-split approximation).

### GAP-004: Documented extra: BoundTask

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/tasks/task.py:8
**Export:** BoundTask

**Issue:** `SKILL.md:224` documents `BoundTask`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `BoundTask` is a documented extra, a name the source still declares at `cognee/modules/pipelines/tasks/task.py:8` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-018: Documented extra: CogneeApiError

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/exceptions.py:10
**Export:** CogneeApiError

**Issue:** `SKILL.md:288` documents `CogneeApiError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CogneeApiError` is a documented extra, a name the source still declares at `cognee/exceptions/exceptions.py:10` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-019: Documented extra: CogneeConfigurationError

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/exceptions.py:99
**Export:** CogneeConfigurationError

**Issue:** `SKILL.md:110` documents `CogneeConfigurationError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CogneeConfigurationError` is a documented extra, a name the source still declares at `cognee/exceptions/exceptions.py:99` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-020: Documented extra: CogneeSystemError

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/exceptions.py:69
**Export:** CogneeSystemError

**Issue:** `SKILL.md:289` documents `CogneeSystemError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CogneeSystemError` is a documented extra, a name the source still declares at `cognee/exceptions/exceptions.py:69` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-021: Documented extra: CogneeTransientError

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/exceptions.py:114
**Export:** CogneeTransientError

**Issue:** `SKILL.md:292` documents `CogneeTransientError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CogneeTransientError` is a documented extra, a name the source still declares at `cognee/exceptions/exceptions.py:114` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-022: Documented extra: CogneeValidationError

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/exceptions.py:84
**Export:** CogneeValidationError

**Issue:** `SKILL.md:227` documents `CogneeValidationError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CogneeValidationError` is a documented extra, a name the source still declares at `cognee/exceptions/exceptions.py:84` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-023: Documented extra: DataPoint

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/low_level.py:2
**Export:** DataPoint

**Issue:** `SKILL.md:29` documents `DataPoint`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `DataPoint` is a documented extra, a name the source still declares at `cognee/low_level.py:2` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-024: Documented extra: DistillationResult

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/session_distillation/models.py:94
**Export:** DistillationResult

**Issue:** `SKILL.md:147` documents `DistillationResult`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `DistillationResult` is a documented extra, a name the source still declares at `cognee/modules/session_distillation/models.py:94` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-025: Documented extra: Edge

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/infrastructure/engine/models/Edge.py:13
**Export:** Edge

**Issue:** `SKILL.md:221` documents `Edge`, which the enumerated source API surface lacks and the source still declares; of the 5 files that declare it, the skill cites only `cognee/infrastructure/engine/models/Edge.py`

**Remediation:** No change: `Edge` is a documented extra, a name the source still declares at `cognee/infrastructure/engine/models/Edge.py:13` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-026: Documented extra: EntitySpec

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/graph_models/spec.py:90
**Export:** EntitySpec

**Issue:** `references/full-api-reference.md:279` documents `EntitySpec`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `EntitySpec` is a documented extra, a name the source still declares at `cognee/modules/graph_models/spec.py:90` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-027: Documented extra: FromIdentity

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/infrastructure/engine/models/FieldAnnotations.py:95
**Export:** FromIdentity

**Issue:** `SKILL.md:221` documents `FromIdentity`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `FromIdentity` is a documented extra, a name the source still declares at `cognee/infrastructure/engine/models/FieldAnnotations.py:95` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-029: Documented extra: GraphSchemaSpec

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/graph_models/spec.py:108
**Export:** GraphSchemaSpec

**Issue:** `references/full-api-reference.md:279` documents `GraphSchemaSpec`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `GraphSchemaSpec` is a documented extra, a name the source still declares at `cognee/modules/graph_models/spec.py:108` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-033: Documented extra: ImproveKwargs

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/improve/improve.py:88
**Export:** ImproveKwargs

**Issue:** `SKILL.md:159` documents `ImproveKwargs`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ImproveKwargs` is a documented extra, a name the source still declares at `cognee/api/v1/improve/improve.py:88` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-034: Documented extra: ImproveResult

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/improve/result.py:187
**Export:** ImproveResult

**Issue:** `SKILL.md:104` documents `ImproveResult`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ImproveResult` is a documented extra, a name the source still declares at `cognee/modules/improve/result.py:187` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-038: Documented extra: PipelineRunCompleted

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/models/PipelineRunInfo.py:34
**Export:** PipelineRunCompleted

**Issue:** `references/full-api-reference.md:267` documents `PipelineRunCompleted`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PipelineRunCompleted` is a documented extra, a name the source still declares at `cognee/modules/pipelines/models/PipelineRunInfo.py:34` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-039: Documented extra: PipelineRunErrored

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/models/PipelineRunInfo.py:42
**Export:** PipelineRunErrored

**Issue:** `references/core-workflow.md:100` documents `PipelineRunErrored`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PipelineRunErrored` is a documented extra, a name the source still declares at `cognee/modules/pipelines/models/PipelineRunInfo.py:42` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-040: Documented extra: PipelineRunInfo

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/models/PipelineRunInfo.py:9
**Export:** PipelineRunInfo

**Issue:** `SKILL.md:134` documents `PipelineRunInfo`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PipelineRunInfo` is a documented extra, a name the source still declares at `cognee/modules/pipelines/models/PipelineRunInfo.py:9` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-041: Documented extra: PipelineRunStarted

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/models/PipelineRunInfo.py:26
**Export:** PipelineRunStarted

**Issue:** `references/full-api-reference.md:267` documents `PipelineRunStarted`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PipelineRunStarted` is a documented extra, a name the source still declares at `cognee/modules/pipelines/models/PipelineRunInfo.py:26` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-042: Documented extra: REMEDIATION_MARKER

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/remediation.py:52
**Export:** REMEDIATION_MARKER

**Issue:** `SKILL.md:294` documents `REMEDIATION_MARKER`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `REMEDIATION_MARKER` is a documented extra, a name the source still declares at `cognee/exceptions/remediation.py:52` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-043: Documented extra: RememberKwargs

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/remember/remember.py:90
**Export:** RememberKwargs

**Issue:** `SKILL.md:156` documents `RememberKwargs`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `RememberKwargs` is a documented extra, a name the source still declares at `cognee/api/v1/remember/remember.py:90` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-044: Documented extra: SkillRunEntry

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/memory/entries.py:82
**Export:** SkillRunEntry

**Issue:** `SKILL.md:180` documents `SkillRunEntry`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `SkillRunEntry` is a documented extra, a name the source still declares at `cognee/memory/entries.py:82` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-045: Documented extra: TaskSpec

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/tasks/task.py:35
**Export:** TaskSpec

**Issue:** `references/pipelines-and-datapoints.md:36` documents `TaskSpec`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `TaskSpec` is a documented extra, a name the source still declares at `cognee/modules/pipelines/tasks/task.py:35` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-046: Documented extra: UpdateResult

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/update/result.py:37
**Export:** UpdateResult

**Issue:** `references/core-workflow.md:383` documents `UpdateResult`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `UpdateResult` is a documented extra, a name the source still declares at `cognee/api/v1/update/result.py:37` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-048: Documented extra: __version__

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/__init__.py:22
**Export:** __version__

**Issue:** `SKILL.md:28` documents `__version__`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `__version__` is a documented extra, a name the source still declares at `cognee/__init__.py:22` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-049: Documented extra: add_data_points

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/tasks/storage/add_data_points.py:70
**Export:** add_data_points

**Issue:** `SKILL.md:116` documents `add_data_points`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `add_data_points` is a documented extra, a name the source still declares at `cognee/tasks/storage/add_data_points.py:70` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-050: Documented extra: add_feedback

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/session/session.py:113
**Export:** add_feedback

**Issue:** `SKILL.md:147` documents `add_feedback`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `add_feedback` is a documented extra, a name the source still declares at `cognee/api/v1/session/session.py:113` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-053: Documented extra: delete_feedback

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/session/session.py:147
**Export:** delete_feedback

**Issue:** `SKILL.md:147` documents `delete_feedback`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `delete_feedback` is a documented extra, a name the source still declares at `cognee/api/v1/session/session.py:147` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-054: Documented extra: distill_session

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/session_distillation/distill.py:471
**Export:** distill_session

**Issue:** `SKILL.md:147` documents `distill_session`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `cognee/modules/session_distillation/distill.py`

**Remediation:** No change: `distill_session` is a documented extra, a name the source still declares at `cognee/modules/session_distillation/distill.py:471` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-055: Documented extra: find_remediation

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/remediation.py:131
**Export:** find_remediation

**Issue:** `SKILL.md:294` documents `find_remediation`, which the enumerated source API surface lacks and the source still declares

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

**Issue:** `SKILL.md:147` documents `get_session`, which the enumerated source API surface lacks and the source still declares

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

### GAP-062: Documented extra: migration

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/migration/__init__.py:1
**Export:** migration

**Issue:** `SKILL.md:28` documents `migration`, which the enumerated source API surface lacks and the source still declares; of the 3 files that declare it, the skill cites only `cognee/migration/__init__.py`

**Remediation:** No change: `migration` is a documented extra, a name the source still declares at `cognee/migration/__init__.py:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-063: Documented extra: pipelines

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/__init__.py:1
**Export:** pipelines

**Issue:** `SKILL.md:8` documents `pipelines`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `pipelines` is a documented extra, a name the source still declares at `cognee/modules/pipelines/__init__.py:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-067: Documented extra: remediation_for

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/remediation.py:146
**Export:** remediation_for

**Issue:** `SKILL.md:294` documents `remediation_for`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `remediation_for` is a documented extra, a name the source still declares at `cognee/exceptions/remediation.py:146` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-069: Documented extra: run_relational_migrations

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/run_migrations.py:11
**Export:** run_relational_migrations

**Issue:** `references/full-api-reference.md:409` documents `run_relational_migrations`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `cognee/run_migrations.py`

**Remediation:** No change: `run_relational_migrations` is a documented extra, a name the source still declares at `cognee/run_migrations.py:11` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-070: Documented extra: setup

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/engine/operations/setup.py:9
**Export:** setup

**Issue:** `SKILL.md:221` documents `setup`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `setup` is a documented extra, a name the source still declares at `cognee/modules/engine/operations/setup.py:9` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-072: Documented extra: task

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/tasks/task.py:124
**Export:** task

**Issue:** `SKILL.md:104` documents `task`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `task` is a documented extra, a name the source still declares at `cognee/modules/pipelines/tasks/task.py:124` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-073: Documented extra: task_summary

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/tasks/task.py:169
**Export:** task_summary

**Issue:** `references/full-api-reference.md:564` documents `task_summary`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `task_summary` is a documented extra, a name the source still declares at `cognee/modules/pipelines/tasks/task.py:169` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-074: Documented extra: tools

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/tools/tools.py:1
**Export:** tools

**Issue:** `SKILL.md:13` documents `tools`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `tools` is a documented extra, a name the source still declares at `cognee/api/v1/tools/tools.py:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-075: Documented extra: visualize_graph_json

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/visualize/visualize.py:271
**Export:** visualize_graph_json

**Issue:** `references/full-api-reference.md:337` documents `visualize_graph_json`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `visualize_graph_json` is a documented extra, a name the source still declares at `cognee/api/v1/visualize/visualize.py:271` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-076: Documented extra: visualize_multi_user_graph

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/visualize/visualize.py:611
**Export:** visualize_multi_user_graph

**Issue:** `references/full-api-reference.md:339` documents `visualize_multi_user_graph`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `visualize_multi_user_graph` is a documented extra, a name the source still declares at `cognee/api/v1/visualize/visualize.py:611` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-077: Documented extra: visualize_semantic_json

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/visualize/visualize.py:317
**Export:** visualize_semantic_json

**Issue:** `references/full-api-reference.md:338` documents `visualize_semantic_json`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `visualize_semantic_json` is a documented extra, a name the source still declares at `cognee/api/v1/visualize/visualize.py:317` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-079: multi-denominator reporting — barrel vs documented surface

**Severity:** Info
**Category:** Coverage (multi-denominator)
**Source:** skills/oms-cognee/1.6.2/oms-cognee/metadata.json

**Issue:** barrel=102, documented=86

**Remediation:** No action required: the barrel and the documented surface measure different sets by design, and the report records both counts.

### Discovery Quality

**Discovery Test:** not run: the hard gate blocked the run
