---
workflowType: 'test-skill'
skillName: 'oms-cognee'
skillDir: 'skills/oms-cognee/1.0.0/oms-cognee'
runId: '20261006T155152Z-0731f756'
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
testDate: '2026-10-06T15:51:52Z'
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

**Mode Rationale:** `metadata.json` declares `skill_type: "single"` — an individual library skill, so naive mode applies (API-surface coverage; coherence is structural only and not scored).

**Analysis Plan:**
- Coverage Check: every public export in `metadata.exports` (34) and the `cognee/__init__.py` surface at pinned commit `3c048aa` (v1.0.0) is checked for documentation in SKILL.md or references/; at Deep tier, signatures and types are verified against AST-extracted source (ast-grep) with file:line citations.
- Coherence Check: structural only — every reference link in SKILL.md resolves to a file in the package, section anchors exist, and no references/ file is orphaned; no cross-skill integration checks (single skill).

## Coverage Analysis

**Tier:** Deep
**Source Access:** full
**Source Path:** /home/armel/.skf/workspace/repos/github.com/topoteretes/cognee (HEAD `3c048aa`, tag `v1.0.0`)
**Workspace Layout:** single package
**Files Analyzed:** 116 (python, in scope)
**Denominator:** barrel (`root` set: the 36 non-private names `cognee/__init__.py` exports)

**Denominator audit trail** (standard-barrel clause: single-package repo, `scope.type: public-api`, no monorepo, no multi-subpath exports map):
- `root` barrel: 36 ← chosen · `all`: 27 · `scope.include` union: 26 · `stats.effective_denominator`: absent · `tier_a_include`: absent · provenance-map entries: 35
- **Why `root`, not `all`:** `all` drops the 9 names whose defining file the brief scopes out (`excluded.outsideScope`: `Drop` → `cognee/pipelines/types.py`, `agent_memory` → `cognee/modules/agent_memory/decorator.py`, `enable_tracing`/`disable_tracing`/`get_last_trace`/`get_all_traces`/`clear_traces` → `cognee/modules/observability/trace_context.py`, `run_startup_migrations` → `cognee/run_migrations.py`, `setup_logging` → `cognee/shared/logging_utils.py`). Those exclusions are artifacts of the brief's v0.5.8-era globs, not curation: the runner reports `scope.include pattern 'cognee/pipelines.py' matches no file` and `'cognee/modules/observability/trace_context/**' matches no file` at the pinned commit (the first is now the `cognee/pipelines/` package, the second the `trace_context.py` file), and `cognee/__init__.py:40-60` exports all nine. Scoring against `all` would have recorded these documented, exported names as stale.
- **Runner scope:** `forge-data/oms-cognee/skill-brief.yaml` fails to parse as one YAML document (a trailing `---` makes it a two-document stream), so the extraction runner got the brief's `scope.include`/`scope.exclude`/`scope.type`/`language` verbatim through its flags rather than `--brief`, plus `--exclude 'cognee/api/v1/*/routers/**'`. Without that exclude, the brief's `cognee/api/v1/**` glob turns five FastAPI router `__init__.py` files into extra barrels (`get_settings_router`, `get_permissions_router`, `get_notebooks_router`, `get_checks_router`, `get_api_key_management_router`). Under the Source API Surface Definition those are not reachable from `import cognee`, and the skill scopes out the HTTP API. With the exclude, `cognee/__init__.py` is the only entry point.
- **Read by eye:** `logger`, which no recipe matched (`extractionGaps`): `cognee/__init__.py:16` `logger = setup_logging()`.
- **Not on the surface:** `__version__` (`cognee/__init__.py:6`, an assignment of a dunder name, which the recipes treat as private).

### Export Coverage

| Export | Type | Documented | Signature | Source Location | Status |
|--------|------|-----------|-----------|-----------------|--------|
| `add` | function | yes | yes | `cognee/api/v1/add/add.py:22` | PASS |
| `agent_memory` | function | yes | unverified | `cognee/modules/agent_memory/decorator.py:22` | WARN |
| `clear_traces` | function | yes | unverified | `cognee/modules/observability/trace_context.py:85` | WARN |
| `cognee_network_visualization` | function | yes | no | `cognee/modules/visualization/cognee_network_visualization.py:22` | FAIL |
| `cognify` | function | yes | yes | `cognee/api/v1/cognify/cognify.py:44` | PASS |
| `config` | class | yes | unverified | `cognee/api/v1/config/config.py:18` | WARN |
| `datasets` | class | yes | unverified | `cognee/api/v1/datasets/datasets.py:25` | WARN |
| `delete` | function | yes | yes | `cognee/api/v1/delete/__init__.py:13` (surface records the empty `delete/delete.py`; definition traced) | PASS |
| `disable_tracing` | function | yes | unverified | `cognee/modules/observability/trace_context.py:27` | WARN |
| `disconnect` | function | yes | yes | `cognee/api/v1/serve/disconnect.py:8` | PASS |
| `Drop` | constant | yes | unverified | `cognee/pipelines/types.py:32` | WARN |
| `enable_tracing` | function | yes | unverified | `cognee/modules/observability/trace_context.py:16` | WARN |
| `forget` | function | yes | yes | `cognee/api/v1/forget/__init__.py` | PASS |
| `get_all_traces` | function | yes | unverified | `cognee/modules/observability/trace_context.py:76` | WARN |
| `get_cognee_version` | function | no | — | `cognee/version.py:7` | FAIL |
| `get_last_trace` | function | yes | unverified | `cognee/modules/observability/trace_context.py:65` | WARN |
| `improve` | function | yes | yes | `cognee/api/v1/improve/__init__.py` | PASS |
| `logger` | — | no | — | `cognee/__init__.py:16` | FAIL |
| `memify` | function | yes | yes | `cognee/modules/memify/memify.py:25` | PASS |
| `pipelines` | constant | yes | unverified | `cognee/modules/pipelines/__init__.py:1` | WARN |
| `prune` | class | yes | unverified | `cognee/api/v1/prune/prune.py:4` | WARN |
| `recall` | function | yes | yes | `cognee/api/v1/recall/__init__.py` | PASS |
| `remember` | function | yes | yes | `cognee/api/v1/remember/__init__.py` | PASS |
| `RememberResult` | class | yes | unverified | `cognee/api/v1/remember/remember.py:139` | WARN |
| `run_custom_pipeline` | function | yes | yes | `cognee/modules/run_custom_pipeline/run_custom_pipeline.py:14` | PASS |
| `run_startup_migrations` | function | yes | unverified | `cognee/run_migrations.py:80` | WARN |
| `search` | function | yes | yes | `cognee/api/v1/search/search.py:27` | PASS |
| `SearchType` | enum | yes | unverified | `cognee/modules/search/types/SearchType.py:4` | WARN |
| `serve` | function | yes | yes | `cognee/api/v1/serve/__init__.py` | PASS |
| `session` | constant | yes | unverified | `cognee/api/v1/session/session.py:1` | WARN |
| `setup_logging` | — | no | — | `cognee/shared/logging_utils.py` | FAIL |
| `start_ui` | function | yes | yes | `cognee/api/v1/ui/ui.py:369` | PASS |
| `start_visualization_server` | constant | yes | unverified | `cognee/api/v1/visualize/start_visualization_server.py:6` | WARN |
| `update` | function | yes | yes | `cognee/api/v1/update/update.py:12` | PASS |
| `visualize` | function | yes | yes | `cognee/api/v1/visualize/__init__.py` | PASS |
| `visualize_graph` | function | yes | yes | `cognee/api/v1/visualize/visualize.py:17` | PASS |

`unverified` marks a documented export with no signature to compare: a namespace object, enum or class (`config`, `datasets`, `prune`, `SearchType`, `RememberResult`, `pipelines`, `session`, `start_visualization_server`, `Drop`), or one of the 7 brief-out-of-scope functions the signature plan leaves out (`agent_memory`, the 5 tracing functions, `run_startup_migrations`).

### Coverage Summary

- **Exports Found:** 36
- **Documented:** 33 (91.67%)
- **Missing Documentation:** 3: `get_cognee_version` (`cognee/version.py:7`), `logger` (`cognee/__init__.py:16`), `setup_logging` (`cognee/shared/logging_utils.py`). These are bootstrap imports the top-level module re-binds. `metadata.exports` leaves them out too.
- **Signature Mismatches:** 1: `cognee_network_visualization`, where the source (`cognee/modules/visualization/cognee_network_visualization.py:22`) has a third parameter, `schema_data: dict = None`, that SKILL.md:137 and references/full-api-reference.md:246 leave out.
- **Stale Documentation:** 26. These are documented names outside the top-level barrel, and none is fabricated (`classify-stale`). 24 are sub-module APIs that the skill documents on purpose, and each is defined at the pinned commit: `CogneeApiError`/`CogneeSystemError`/`CogneeValidationError`/`CogneeConfigurationError`/`CogneeTransientError` (`cognee/exceptions/exceptions.py:7,38,52,66,80`); `Task`/`task_summary` (`cognee/modules/pipelines/tasks/task.py:172,153`); `run_tasks` (`cognee/modules/pipelines/operations/run_tasks.py:55`); `run_tasks_parallel` (`…/run_parallel.py:6`); `run_pipeline` (`…/pipeline.py:33`); `PipelineRunInfo`/`Started`/`Completed`/`Errored` (`cognee/modules/pipelines/models/PipelineRunInfo.py:7,24,34,44`); `get_session`/`add_feedback`/`delete_feedback` (`cognee/api/v1/session/session.py:40,77,101`); `DataPoint`/`setup` (`cognee/low_level.py:1-2`); `Edge` (`cognee/infrastructure/engine/models/Edge.py`); `LLMGateway` (`cognee/infrastructure/llm/LLMGateway.py:21`); `add_data_points` (`cognee/tasks/storage/add_data_points.py:30`); `run_migrations` (`cognee/run_migrations.py:16`); `visualization_server` (`cognee/api/v1/visualize/start_visualization_server.py:6`). The other two are notes, not APIs: `__version__` is defined at `cognee/__init__.py:6`, and `low_level` is documented only as "no longer exported". The ledger records them as Medium `stale-documentation`, as the Gap Severity table requires. They are documented extras, not removed exports: **do not delete them.** Their remediation is to label each with its sub-module import path.
- **Metadata coherence (§4b):** Medium `metadata-drift`: `stats.exports_documented`=34, provenance named-exports=35, `confidence_distribution` sum=60 (43% drift). Info `multi-denominator`: barrel 34 vs documented 60.
- **Numerator ground truth (§2b):** skipped, because `stats.effective_denominator` is absent, so the inflation signature cannot occur.
- **Provenance lines (§4c):** 2 Low `provenance-line` entries: `delete`, where the map cites `cognee/api/v1/delete/__init__.py:11` and the definition is at line 13; and `search`, where the map cites `cognee/api/v1/search/search.py:26` and the definition is at line 27.
- **Deep-tier checks:** `gh api repos/topoteretes/cognee/git/ref/tags/v1.0.0` resolves to `3c048aa4147776f14d4546704f986242554a9ef3`, which is the workspace HEAD and `metadata.source_commit`, and `pyproject.toml:4` reads `version = "1.0.0"`. Type cross-check: 4/4 barrel types are documented. Re-exports were traced to their definitions for `delete`, `forget`, `improve`, `recall`, `remember`, `serve` and `visualize`.

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 91.67% |
| Signature Accuracy | 94.12% |
| Type Coverage | 100.0% |

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)

### Structural Findings

| # | Type | Severity | Detail | Line |
|---|------|----------|--------|------|
| 1 | bare_opening_fence | Medium | naive-coherence: opening code fence at line 237 missing language tag (the `cognee-cli` command block under `## CLI`; `bash` fits) | 237 |
| 2 | export_not_in_usage | Medium | naive-coherence: exported function `visualization_server` is not referenced in any usage-family section or reference file (it appears only in `## Architecture at a Glance`, SKILL.md:231) | — |

**Structural Issues:** 2

Checks that passed:
- **§2.1 Required sections:** description → `## Overview` (SKILL.md:20), usage → `## Quick Start` (SKILL.md:31), API surface → `## Key API Summary` (SKILL.md:121).
- **§2.2 Fence balance:** balanced (6 fences).
- **§2.5 Async/sync:** 14 documented functions are called in examples. Every async function the skill documents (`add`, `cognify`, `search`, `remember`, `recall`, `add_data_points`, `run_pipeline`) is awaited. Every sync function (`enable_tracing`, `disable_tracing`, `get_last_trace`, `get_all_traces`, `clear_traces`, `run_tasks_parallel`, `task_summary`) is called without `await`. No contradictions. 21 exports appear in no example.
- **§2.6 Table syntax:** no column drift.
- **§2.7 Scripts & Assets:** no `scripts/` or `assets/` folder.
- **§2b Migration/Deprecation:** Section 4b verification skipped: `forge-data/oms-cognee/1.0.0/evidence-report.md` has no YAML frontmatter, so it carries no pinned `t2_future_count` (Case 4). SKILL.md has `## Deprecations & Gotchas` (SKILL.md:159), not a "Migration & Deprecation Warnings" section.

### Reference Consistency (split-body)

| # | Reference File | Export | Issue | SKILL.md Line | Reference Line |
|---|---------------|--------|-------|---------------|---------------|
| 1 | references/core-workflow.md | `add` | The full signature (L27-L40) and the parameter table (L47-L60) leave out `run_in_background: bool = False`. SKILL.md and the source (`cognee/api/v1/add/add.py:42`) have it. | 127 | 27 |
| 2 | references/core-workflow.md | `search` | The full signature (L177-L196) and the key-parameters table leave out `neighborhood_depth` and `neighborhood_seed_top_k`. The source (`cognee/api/v1/search/search.py:46-47`) has them. | 129 | 177 |
| 3 | references/core-workflow.md | `SearchType` | The result-shapes table documents a `CODE` member. The enum (`cognee/modules/search/types/SearchType.py:5-19`) has 15 members and no `CODE`. | 136 | 229 |
| 4 | references/full-api-reference.md | `DataPoint` | The reference gives `from cognee.low_level import DataPoint, setup`. SKILL.md says it is no longer re-exported. **The source sides with the reference:** `cognee/low_level.py:1-2` still re-exports it, so fix SKILL.md:214. | 214 | 214 |
| 5 | references/pipelines-and-datapoints.md | `DataPoint` | Same contradiction as row 4. The source (`cognee/low_level.py:1`) sides with the reference. | 214 | 224 |
| 6 | references/full-api-reference.md | `run_migrations` | The reference documents `cognee.run_migrations` as a current top-level API. At v1.0.0, `cognee/__init__.py:43` exports only `run_startup_migrations`. | 164 | 268 |

**Exports Cross-Checked:** 39 (of the 59 documented items, the ones that both SKILL.md and a `references/` file name)
**Mismatches Found:** 6 (coverage-check §1b recorded them as High `split-body-mismatch` gaps)

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

**Result:** **FAIL**, not scored: the hard gate blocked this run on 7 Critical or High gap(s), listed first in the Gap Report.

## Gap Report

**Total Gaps:** 42
**Blocking (Critical + High):** 7
**Non-blocking (Medium + Low + Info):** 35

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|------------------|
| Critical | 1 | Read the source code and write or correct the documentation |
| High | 6 | Read the source code and write or correct the documentation |
| Medium | 32 | Add type definitions, interface docs or the missing section |
| Low | 2 | Add examples or metadata |
| Info | 1 | Optional improvements, no action required |
| **Total** | **42** | |

### GAP-001: Signature mismatch: cognee_network_visualization

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** cognee/modules/visualization/cognee_network_visualization.py:22
**Export:** cognee_network_visualization

**Issue:** documented `(graph_data, destination_file_path=None)`, source `async def cognee_network_visualization(graph_data, destination_file_path: str = None, schema_data: dict = None)`: The source has a third parameter, `schema_data: dict = None`, that the documented signature leaves out.

**Remediation:** Update the documented signature of `cognee_network_visualization` from `(graph_data, destination_file_path=None)` to `async def cognee_network_visualization(graph_data, destination_file_path: str = None, schema_data: dict = None)`, the signature the source defines at `cognee/modules/visualization/cognee_network_visualization.py:22`.

### GAP-035: Split-body mismatch: add

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** references/core-workflow.md:27
**Export:** add

**Issue:** SKILL.md:127 (and references/full-api-reference.md:42) list `run_in_background: bool = False` as an add() parameter; the full add() signature in references/core-workflow.md (L27-L40) goes from `importance_weight` straight to `**kwargs`, and its parameter table (L47-L60) omits it too.

**Remediation:** In references/core-workflow.md, add `run_in_background: bool = False,` after `importance_weight: Optional[float] = 0.5,` in the add() signature (L27-L40) and add a `run_in_background` row to the parameter table (L47-L60), matching SKILL.md:127 and source cognee/api/v1/add/add.py:42.

### GAP-036: Split-body mismatch: search

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** references/core-workflow.md:177
**Export:** search

**Issue:** SKILL.md:129 (and references/full-api-reference.md:103-104) list `neighborhood_depth` and `neighborhood_seed_top_k` as search() parameters; the full search() signature in references/core-workflow.md (L177-L196) ends at `retriever_specific_config` and its key-parameters table (L201-L219) omits both.

**Remediation:** In references/core-workflow.md, append `neighborhood_depth: Optional[int] = None,` and `neighborhood_seed_top_k: Optional[int] = None,` after `retriever_specific_config` in the search() signature (L177-L196) and add both to the key-parameters table (L201-L219), noting they must be positive ints when set, matching SKILL.md:129 and source cognee/api/v1/search/search.py:46-47.

### GAP-037: Split-body mismatch: SearchType

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** references/core-workflow.md:229
**Export:** SearchType

**Issue:** SKILL.md:136 documents exactly 15 SearchType members with no CODE; references/core-workflow.md:229 documents a `CODE` SearchType ('structured code info with context') in its result-shapes table. The enum at cognee/modules/search/types/SearchType.py:5-19 has 15 members and no CODE.

**Remediation:** Delete the `CODE` row at references/core-workflow.md:229 from the result-shapes table: SearchType has no CODE member at v1.0.0 (cognee/modules/search/types/SearchType.py:5-19).

### GAP-038: Split-body mismatch: DataPoint

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** references/full-api-reference.md:214
**Export:** DataPoint

**Issue:** SKILL.md:214 says DataPoint is 'no longer re-exported via cognee.low_level; import directly', while references/full-api-reference.md:214 gives `from cognee.low_level import DataPoint, setup`. The source sides with the reference: cognee/low_level.py:1-2 still re-exports `ExtendableDataPoint as DataPoint` and `setup` at the pinned commit; v1.0.0 only dropped `low_level` from the top-level cognee/__init__.py exports.

**Remediation:** Fix SKILL.md:214, not the reference: replace 'In v1.0.0 this is no longer re-exported via `cognee.low_level`; import directly.' with 'In v1.0.0 `low_level` is no longer re-exported from the top-level `cognee` package, but the `cognee.low_level` module still provides `DataPoint` and `setup` (`from cognee.low_level import DataPoint, setup`).' (source cognee/low_level.py:1-2). Keep references/full-api-reference.md:214 as is.

### GAP-039: Split-body mismatch: DataPoint

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** references/pipelines-and-datapoints.md:224
**Export:** DataPoint

**Issue:** SKILL.md:214 says DataPoint is no longer re-exported via cognee.low_level, while references/pipelines-and-datapoints.md:224 shows `from cognee.low_level import DataPoint, setup` as a valid shortcut. The source sides with the reference: cognee/low_level.py:1 still re-exports `ExtendableDataPoint as DataPoint`.

**Remediation:** Fix SKILL.md:214 (see the full-api-reference.md:214 record); keep references/pipelines-and-datapoints.md:224 and its alias note at L227, which match source cognee/low_level.py:1-2.

### GAP-040: Split-body mismatch: run_migrations

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** references/full-api-reference.md:268
**Export:** run_migrations

**Issue:** SKILL.md:164 says cognee.run_migrations is no longer a top-level export and is replaced by cognee.run_startup_migrations(); references/full-api-reference.md:268 documents it as current API under 'Migrations — cognee.run_migrations' (contents entry at L21) and never mentions run_startup_migrations. Source: cognee/__init__.py:43 exports only `run_startup_migrations` (defined at cognee/run_migrations.py:80); `run_migrations` is defined at cognee/run_migrations.py:16 but not re-exported.

**Remediation:** Rewrite the section at references/full-api-reference.md:268 (and its contents link at L21) as 'Migrations — cognee.run_startup_migrations': document `await cognee.run_startup_migrations()` (cognee/run_migrations.py:80, relational + vector migrations) and state that `run_migrations` is no longer a top-level export and must be imported as `from cognee.run_migrations import run_migrations` (cognee/run_migrations.py:16).

### GAP-002: Missing export: get_cognee_version

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** cognee/version.py:7
**Export:** get_cognee_version

**Issue:** `get_cognee_version` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `get_cognee_version` in SKILL.md: read its definition at `cognee/version.py:7` and add its signature, its purpose and a usage example.

### GAP-003: Missing export: logger

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** cognee/__init__.py:16
**Export:** logger

**Issue:** `logger` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `logger` in SKILL.md: read its definition at `cognee/__init__.py:16` and add its signature, its purpose and a usage example.

### GAP-004: Missing export: setup_logging

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** skills/oms-cognee/1.0.0/oms-cognee/metadata.json
**Export:** setup_logging

**Issue:** `setup_logging` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `setup_logging` in SKILL.md: find its definition in the source (`skills/oms-cognee/1.0.0/oms-cognee/metadata.json` lists it) and add its signature, its purpose and a usage example.

### GAP-005: Stale documentation: CogneeApiError

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:218
**Export:** CogneeApiError

**Issue:** SKILL.md documents `CogneeApiError`, which the enumerated source API surface lacks

**Remediation:** Check `CogneeApiError` against the source and update or remove its documentation at SKILL.md:218: the enumerated source surface does not export it.

### GAP-006: Stale documentation: CogneeConfigurationError

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:221
**Export:** CogneeConfigurationError

**Issue:** SKILL.md documents `CogneeConfigurationError`, which the enumerated source API surface lacks

**Remediation:** Check `CogneeConfigurationError` against the source and update or remove its documentation at SKILL.md:221: the enumerated source surface does not export it.

### GAP-007: Stale documentation: CogneeSystemError

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:219
**Export:** CogneeSystemError

**Issue:** SKILL.md documents `CogneeSystemError`, which the enumerated source API surface lacks

**Remediation:** Check `CogneeSystemError` against the source and update or remove its documentation at SKILL.md:219: the enumerated source surface does not export it.

### GAP-008: Stale documentation: CogneeTransientError

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:222
**Export:** CogneeTransientError

**Issue:** SKILL.md documents `CogneeTransientError`, which the enumerated source API surface lacks

**Remediation:** Check `CogneeTransientError` against the source and update or remove its documentation at SKILL.md:222: the enumerated source surface does not export it.

### GAP-009: Stale documentation: CogneeValidationError

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:167
**Export:** CogneeValidationError

**Issue:** SKILL.md documents `CogneeValidationError`, which the enumerated source API surface lacks

**Remediation:** Check `CogneeValidationError` against the source and update or remove its documentation at SKILL.md:167: the enumerated source surface does not export it.

### GAP-010: Stale documentation: DataPoint

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:163
**Export:** DataPoint

**Issue:** SKILL.md documents `DataPoint`, which the enumerated source API surface lacks

**Remediation:** Check `DataPoint` against the source and update or remove its documentation at SKILL.md:163: the enumerated source surface does not export it.

### GAP-011: Stale documentation: Edge

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/full-api-reference.md:217
**Export:** Edge

**Issue:** SKILL.md documents `Edge`, which the enumerated source API surface lacks

**Remediation:** Check `Edge` against the source and update or remove its documentation at references/full-api-reference.md:217: the enumerated source surface does not export it.

### GAP-012: Stale documentation: LLMGateway

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-workflow.md:318
**Export:** LLMGateway

**Issue:** SKILL.md documents `LLMGateway`, which the enumerated source API surface lacks

**Remediation:** Check `LLMGateway` against the source and update or remove its documentation at references/core-workflow.md:318: the enumerated source surface does not export it.

### GAP-013: Stale documentation: PipelineRunCompleted

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/full-api-reference.md:203
**Export:** PipelineRunCompleted

**Issue:** SKILL.md documents `PipelineRunCompleted`, which the enumerated source API surface lacks

**Remediation:** Check `PipelineRunCompleted` against the source and update or remove its documentation at references/full-api-reference.md:203: the enumerated source surface does not export it.

### GAP-014: Stale documentation: PipelineRunErrored

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/full-api-reference.md:203
**Export:** PipelineRunErrored

**Issue:** SKILL.md documents `PipelineRunErrored`, which the enumerated source API surface lacks

**Remediation:** Check `PipelineRunErrored` against the source and update or remove its documentation at references/full-api-reference.md:203: the enumerated source surface does not export it.

### GAP-015: Stale documentation: PipelineRunInfo

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/core-workflow.md:86
**Export:** PipelineRunInfo

**Issue:** SKILL.md documents `PipelineRunInfo`, which the enumerated source API surface lacks

**Remediation:** Check `PipelineRunInfo` against the source and update or remove its documentation at references/core-workflow.md:86: the enumerated source surface does not export it.

### GAP-016: Stale documentation: PipelineRunStarted

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/full-api-reference.md:203
**Export:** PipelineRunStarted

**Issue:** SKILL.md documents `PipelineRunStarted`, which the enumerated source API surface lacks

**Remediation:** Check `PipelineRunStarted` against the source and update or remove its documentation at references/full-api-reference.md:203: the enumerated source surface does not export it.

### GAP-017: Stale documentation: Task

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:113
**Export:** Task

**Issue:** SKILL.md documents `Task`, which the enumerated source API surface lacks

**Remediation:** Check `Task` against the source and update or remove its documentation at SKILL.md:113: the enumerated source surface does not export it.

### GAP-018: Stale documentation: __version__

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:143
**Export:** __version__

**Issue:** SKILL.md documents `__version__`, which the enumerated source API surface lacks

**Remediation:** Check `__version__` against the source and update or remove its documentation at SKILL.md:143: the enumerated source surface does not export it.

### GAP-019: Stale documentation: add_data_points

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:113
**Export:** add_data_points

**Issue:** SKILL.md documents `add_data_points`, which the enumerated source API surface lacks

**Remediation:** Check `add_data_points` against the source and update or remove its documentation at SKILL.md:113: the enumerated source surface does not export it.

### GAP-020: Stale documentation: add_feedback

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:141
**Export:** add_feedback

**Issue:** SKILL.md documents `add_feedback`, which the enumerated source API surface lacks

**Remediation:** Check `add_feedback` against the source and update or remove its documentation at SKILL.md:141: the enumerated source surface does not export it.

### GAP-021: Stale documentation: delete_feedback

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:141
**Export:** delete_feedback

**Issue:** SKILL.md documents `delete_feedback`, which the enumerated source API surface lacks

**Remediation:** Check `delete_feedback` against the source and update or remove its documentation at SKILL.md:141: the enumerated source surface does not export it.

### GAP-022: Stale documentation: get_session

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:141
**Export:** get_session

**Issue:** SKILL.md documents `get_session`, which the enumerated source API surface lacks

**Remediation:** Check `get_session` against the source and update or remove its documentation at SKILL.md:141: the enumerated source surface does not export it.

### GAP-023: Stale documentation: low_level

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:163
**Export:** low_level

**Issue:** SKILL.md documents `low_level`, which the enumerated source API surface lacks

**Remediation:** Check `low_level` against the source and update or remove its documentation at SKILL.md:163: the enumerated source surface does not export it.

### GAP-024: Stale documentation: run_migrations

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:142
**Export:** run_migrations

**Issue:** SKILL.md documents `run_migrations`, which the enumerated source API surface lacks

**Remediation:** Check `run_migrations` against the source and update or remove its documentation at SKILL.md:142: the enumerated source surface does not export it.

### GAP-025: Stale documentation: run_pipeline

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:113
**Export:** run_pipeline

**Issue:** SKILL.md documents `run_pipeline`, which the enumerated source API surface lacks

**Remediation:** Check `run_pipeline` against the source and update or remove its documentation at SKILL.md:113: the enumerated source surface does not export it.

### GAP-026: Stale documentation: run_tasks

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:139
**Export:** run_tasks

**Issue:** SKILL.md documents `run_tasks`, which the enumerated source API surface lacks

**Remediation:** Check `run_tasks` against the source and update or remove its documentation at SKILL.md:139: the enumerated source surface does not export it.

### GAP-027: Stale documentation: run_tasks_parallel

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:139
**Export:** run_tasks_parallel

**Issue:** SKILL.md documents `run_tasks_parallel`, which the enumerated source API surface lacks

**Remediation:** Check `run_tasks_parallel` against the source and update or remove its documentation at SKILL.md:139: the enumerated source surface does not export it.

### GAP-028: Stale documentation: setup

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:142
**Export:** setup

**Issue:** SKILL.md documents `setup`, which the enumerated source API surface lacks

**Remediation:** Check `setup` against the source and update or remove its documentation at SKILL.md:142: the enumerated source surface does not export it.

### GAP-029: Stale documentation: task_summary

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** references/full-api-reference.md:309
**Export:** task_summary

**Issue:** SKILL.md documents `task_summary`, which the enumerated source API surface lacks

**Remediation:** Check `task_summary` against the source and update or remove its documentation at references/full-api-reference.md:309: the enumerated source surface does not export it.

### GAP-030: Stale documentation: visualization_server

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:170
**Export:** visualization_server

**Issue:** SKILL.md documents `visualization_server`, which the enumerated source API surface lacks

**Remediation:** Check `visualization_server` against the source and update or remove its documentation at SKILL.md:170: the enumerated source surface does not export it.

### GAP-031: metadata drift — documented-surface export counts diverge

**Severity:** Medium
**Category:** Coverage (metadata-drift)
**Source:** skills/oms-cognee/1.0.0/oms-cognee/metadata.json

**Issue:** stats.exports_documented=34, provenance named-exports=35, confidence_distribution sum=60 → 43% drift

**Remediation:** Recount the exports and correct the diverging counts in `skills/oms-cognee/1.0.0/oms-cognee/metadata.json`; update-skill applies it as a metadata update.

### GAP-041: naive-coherence: opening code fence at line 237 missing language tag

**Severity:** Medium
**Category:** Structural (structural)
**Source:** SKILL.md:237

**Remediation:** Add a language tag (such as `bash` or `python`) to the opening fence at SKILL.md line 237.

### GAP-042: naive-coherence: exported function `visualization_server` is not referenced in any usage-family section or reference file

**Severity:** Medium
**Category:** Structural (structural)
**Source:** SKILL.md
**Export:** visualization_server

**Remediation:** Add an example that calls `visualization_server` to SKILL.md's usage section (or to a references/ file for a split body).

### GAP-033: Provenance line is not the definition of delete

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** cognee/api/v1/delete/__init__.py:11
**Export:** delete

**Issue:** the provenance map records `delete` at `cognee/api/v1/delete/__init__.py:11`, which is not the line that defines it; the lines that define it are 13.

**Remediation:** Set the provenance `source_line` of `delete` in `cognee/api/v1/delete/__init__.py` to its definition line (13) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-034: Provenance line is not the definition of search

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** cognee/api/v1/search/search.py:26
**Export:** search

**Issue:** the provenance map records `search` at `cognee/api/v1/search/search.py:26`, which is not the line that defines it; the lines that define it are 27.

**Remediation:** Set the provenance `source_line` of `search` in `cognee/api/v1/search/search.py` to its definition line (27) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-032: multi-denominator reporting — barrel vs documented surface

**Severity:** Info
**Category:** Coverage (multi-denominator)
**Source:** skills/oms-cognee/1.0.0/oms-cognee/metadata.json

**Issue:** barrel=34, documented=60

**Remediation:** No action required: the barrel and the documented surface measure different sets by design, and the report records both counts.

### Discovery Quality

**Discovery Test:** not run: the hard gate blocked the run
