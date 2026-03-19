---
workflowType: 'test-skill'
skillName: 'cognee'
skillDir: 'skills/cognee'
testMode: 'naive'
forgeTier: 'Deep'
testResult: 'pass'
score: '95.1%'
analysisConfidence: 'provenance-map'
testDate: '2026-03-19'
stepsCompleted: ['step-01-init', 'step-02-detect-mode', 'step-03-coverage-check', 'step-04-coherence-check', 'step-04b-external-validators', 'step-05-score', 'step-06-report']
nextWorkflow: 'export-skill'
---

# Test Report: cognee

## Test Summary

**Skill:** cognee
**Test Mode:** naive
**Forge Tier:** Deep

**Mode Rationale:** metadata.json `skill_type: "single"` — individual skill with self-contained API surface, no cross-references to other skills.

**Analysis Plan:**
- Coverage Check: documented exports vs source API surface (provenance-map baseline at Deep tier)
- Coherence Check: structural validation only (no cross-references to verify in single skill)

## Coverage Analysis

**Tier:** Deep
**Source Access:** provenance-map (T1 confidence)
**Source:** topoteretes/cognee @ main
**Exports Analyzed:** 22

### Export Coverage

| Export | Type | Documented | Signature | Source Location | Status |
|--------|------|-----------|-----------|-----------------|--------|
| `add` | function | Yes | Full | `cognee/api/v1/add/add.py:L22` | PASS |
| `cognify` | function | Yes | Full | `cognee/api/v1/cognify/cognify.py:L47` | PASS |
| `search` | function | Yes | Full | `cognee/api/v1/search/search.py:L26` | PASS |
| `SearchType` | class | Yes | Full | `cognee/modules/search/types/SearchType.py:L4` | PASS |
| `memify` | function | Yes | Full | `cognee/modules/memify/memify.py:L27` | PASS |
| `run_custom_pipeline` | function | Yes | Key params | `cognee/modules/run_custom_pipeline/run_custom_pipeline.py:L16` | PASS |
| `update` | function | Yes | Key params | `cognee/api/v1/update/update.py:L13` | PASS |
| `delete` | function | Yes | Deprecated | `cognee/api/v1/delete/__init__.py:L13` | PASS |
| `config` | class | Yes | Methods | `cognee/api/v1/config/config.py:L18` | PASS |
| `datasets` | class | Yes | Methods | `cognee/api/v1/datasets/datasets.py:L26` | PASS |
| `prune` | class | Yes | Methods | `cognee/api/v1/prune/prune.py:L4` | PASS |
| `session` | namespace | Yes | Methods | `cognee/api/v1/session/__init__.py:L8` | PASS |
| `visualize_graph` | function | Yes | Signature | `cognee/api/v1/visualize/visualize.py:L18` | PASS |
| `enable_tracing` | function | Yes | Signature | `cognee/modules/observability/trace_context.py:L14` | PASS |
| `disable_tracing` | function | Yes | Inline | `cognee/modules/observability/trace_context.py:L23` | PASS |
| `get_last_trace` | function | Yes | Inline | `cognee/modules/observability/trace_context.py:L55` | PASS |
| `get_all_traces` | function | Yes | Inline | `cognee/modules/observability/trace_context.py:L63` | PASS |
| `clear_traces` | function | Yes | Inline | `cognee/modules/observability/trace_context.py` | PASS |
| `run_migrations` | function | Yes | Signature | `cognee/run_migrations.py:L18` | PASS |
| `pipelines` | module | Partial | Re-exports | `cognee/modules/pipelines/__init__.py:L1` | WARN |
| `start_ui` | function | No | — | `cognee/api/v1/ui/ui.py` | FAIL |
| `cognee_network_visualization` | function | No | — | `cognee/modules/visualization/cognee_network_visualization.py:L17` | FAIL |

### Coverage Summary

- **Exports Found:** 22
- **Documented:** 19 (86.4%)
- **Partially Documented:** 1 (pipelines — re-export list only)
- **Missing Documentation:** 2 (start_ui, cognee_network_visualization)
- **Signature Mismatches:** 0
- **Stale Documentation:** 0

### Category Scores

| Category | Score | Weight | Weighted |
|----------|-------|--------|----------|
| Export Coverage | 90.9% | 45% | 40.9% |
| Signature Accuracy | 100% | 25% | 25.0% |
| Type Coverage | 100% | 20% | 20.0% |
| External Validation | 100% | 10% | 10.0% |

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)

### Structural Findings

| # | Type | Detail | Line |
|---|------|--------|------|
| 1 | section_4b_verified | Migration & Deprecation Warnings section present; T2-future annotations exist (4) — match confirmed | L96 |

**Structural Issues:** 0

### Structural Validation Summary

- All required sections present (Overview through Full Integration Patterns)
- All code blocks properly fenced with language annotations (7 python, 1 bash)
- All markdown balanced (0 unclosed fences)
- All `await` calls consistent with async function declarations
- Section 4b correctly present (Deep tier, T2-future annotations exist)
- No self-contradictions detected

## External Validation

### skill-check
- **Available:** yes
- **Quality Score:** 100/100
- **Errors:** 0
- **Warnings:** 0
- **Diagnostics:** none

### tessl
- **Available:** yes
- **Validation:** PASSED
- **Description Score:** 100%
- **Content Score:** 65%
- **Average Score:** 83%
- **Suggestions:** Add validation steps to workflows; move Full API Reference to separate file; remove [MANUAL] placeholders (all deferred — spec conflicts)

### Combined External Score
- **External Validation Score:** 91.5%
- **Tools used:** skill-check, tessl

## Completeness Score

### Score Breakdown

| Category | Score | Weight | Weighted |
|----------|-------|--------|----------|
| Export Coverage | 90.9% | 45% | 40.9% |
| Signature Accuracy | 100% | 25% | 25.0% |
| Type Coverage | 100% | 20% | 20.0% |
| Coherence | N/A | 0% | 0% |
| External Validation | 91.5% | 10% | 9.2% |
| **Total** | | **100%** | **95.1%** |

### Result

**Score:** 95.1%
**Threshold:** 80%
**Result:** **PASS**

**Weight Distribution:** naive (redistributed — no coherence category)
**Tier Adjustment:** none (Deep tier — full scoring)
**External Validators:** both available (skill-check + tessl)
**Analysis Confidence:** provenance-map

### Access Degradation Notice

**Resolved via:** provenance-map
**Impact:** Signature checks used provenance-map param data, not live AST. Source file:line citations from compilation-time extraction, not re-verified.
**Recommendation:** Re-run with local clone for full AST-backed verification.

## Gap Report

**Total Gaps:** 3
**Blocking (Critical + High):** 2
**Non-blocking (Medium + Low + Info):** 1

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|-----------------|
| Critical | 2 | Add function documentation with signature and description |
| Low | 1 | Expand module re-export documentation |
| **Total** | **3** | |

### GAP-001: Missing documentation for `start_ui`

**Severity:** Critical
**Category:** Coverage
**Source:** `cognee/api/v1/ui/ui.py` (provenance-map entry)

**Issue:** `start_ui` is exported from `cognee/__init__.py` but has no dedicated documentation in SKILL.md. It only appears in the CLI section as `cognee --ui`.

**Remediation:** Add `start_ui` to the Key API Summary table and Full API Reference with signature `def start_ui(...)`, description "Launches local Cognee UI (frontend + backend servers)", and source citation `[AST:cognee/api/v1/ui/ui.py]`.

### GAP-002: Missing documentation for `cognee_network_visualization`

**Severity:** Critical
**Category:** Coverage
**Source:** `cognee/modules/visualization/cognee_network_visualization.py:L17` (provenance-map entry)

**Issue:** `cognee_network_visualization` is exported from `cognee/__init__.py` but has no documentation in SKILL.md.

**Remediation:** Add `cognee_network_visualization` to the Key API Summary table with signature `async def cognee_network_visualization(graph_data, destination_file_path=None)`, description "Renders knowledge graph to interactive HTML visualization", and source citation `[AST:cognee/modules/visualization/cognee_network_visualization.py:L17]`.

### GAP-003: Partial documentation for `pipelines` module re-export

**Severity:** Low
**Category:** Coverage
**Source:** `cognee/modules/pipelines/__init__.py:L1` (provenance-map entry)

**Issue:** `pipelines` module is mentioned in Full Integration Patterns with its re-exports listed (`Task`, `run_tasks`, `run_tasks_parallel`, `run_pipeline`), but lacks a dedicated entry in the Key API Summary table.

**Remediation:** Add a `pipelines` row to the Key API Summary table: "Module re-export: Task, run_tasks, run_tasks_parallel, run_pipeline" with citation `[SRC:cognee/modules/pipelines/__init__.py:L1]`.
