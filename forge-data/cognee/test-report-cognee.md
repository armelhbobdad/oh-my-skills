---
workflowType: 'test-skill'
skillName: 'cognee'
skillDir: 'skills/cognee'
testMode: 'naive'
forgeTier: 'Deep'
testResult: 'pass'
score: '99.2%'
analysisConfidence: 'provenance-map'
testDate: '2026-03-20'
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
| `start_ui` | function | Yes | Full | `cognee/api/v1/ui/ui.py` | PASS |
| `cognee_network_visualization` | function | Yes | Signature | `cognee/modules/visualization/cognee_network_visualization.py:L17` | PASS |
| `pipelines` | module | Yes | Re-exports | `cognee/modules/pipelines/__init__.py:L1` | PASS |
| `run_migrations` | function | Yes | Signature | `cognee/run_migrations.py:L18` | PASS |
| `enable_tracing` | function | Yes | Signature | `cognee/modules/observability/trace_context.py:L14` | PASS |
| `disable_tracing` | function | Yes | Inline | `cognee/modules/observability/trace_context.py:L23` | PASS |
| `get_last_trace` | function | Yes | Inline | `cognee/modules/observability/trace_context.py:L55` | PASS |
| `get_all_traces` | function | Yes | Inline | `cognee/modules/observability/trace_context.py:L63` | PASS |
| `clear_traces` | function | Yes | Inline | `cognee/modules/observability/trace_context.py` | PASS |

### Coverage Summary

- **Exports Found:** 22
- **Documented:** 22 (100%)
- **Missing Documentation:** 0
- **Signature Mismatches:** 0
- **Stale Documentation:** 0

### Category Scores

| Category | Score | Weight | Weighted |
|----------|-------|--------|----------|
| Export Coverage | 100% | 45% | 45.0% |
| Signature Accuracy | 100% | 25% | 25.0% |
| Type Coverage | 100% | 20% | 20.0% |

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)

### Structural Findings

| # | Type | Detail | Line |
|---|------|--------|------|
| 1 | section_4b_verified | Migration & Deprecation Warnings section present; T2-future annotations exist (4) — match confirmed | L99 |

**Structural Issues:** 0

### Structural Validation Summary

- All required sections present (Overview through Full Integration Patterns)
- All code blocks properly fenced with language annotations (9 python, 1 bash)
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
- **Suggestions:** Extract Full API Reference to separate file; add validation steps to prune workflows; remove duplicate [MANUAL] placeholders; condense parameter tables (all deferred — spec conflicts)

### Combined External Score
- **External Validation Score:** 91.5%
- **Tools used:** skill-check, tessl

## Completeness Score

### Score Breakdown

| Category | Score | Weight | Weighted |
|----------|-------|--------|----------|
| Export Coverage | 100% | 45% | 45.0% |
| Signature Accuracy | 100% | 25% | 25.0% |
| Type Coverage | 100% | 20% | 20.0% |
| Coherence | N/A | 0% | 0% |
| External Validation | 91.5% | 10% | 9.2% |
| **Total** | | **100%** | **99.2%** |

### Result

**Score:** 99.2%
**Threshold:** 80%
**Result:** **PASS**

**Weight Distribution:** naive (redistributed — no coherence category)
**Tier Adjustment:** none (Deep tier — full scoring)
**External Validators:** both available (skill-check + tessl)
**Analysis Confidence:** provenance-map

### Access Degradation Notice

**Resolved via:** provenance-map (19 T1 AST-verified, 3 T1-low source-reading)
**Impact:** Signature checks used provenance-map param data, not live AST. T1-low entries (session, delete, pipelines) have reduced signature confidence. Source file:line citations from compilation-time extraction, not re-verified.
**Recommendation:** Re-run with local clone to upgrade 3 T1-low entries to full AST verification. T1 entries are already at highest confidence.

## Gap Report

**Total Gaps:** 0
**Blocking (Critical + High):** 0
**Non-blocking (Medium + Low + Info):** 0

All 3 gaps from previous test (95.1%) have been resolved:
- GAP-001 (Critical): `start_ui` — now fully documented with signature, params, T2 annotation
- GAP-002 (Critical): `cognee_network_visualization` — now documented with signature, T2 annotation
- GAP-003 (Low): `pipelines` — now in Key API Summary with re-export list

### tessl Suggestions (Deferred)

The following tessl suggestions were acknowledged but deferred due to SKF spec conflicts:
- Extract Full API Reference to separate file → split-body handles reference splitting at export time
- Add validation steps to prune workflows → would add unverified content
- Remove duplicate [MANUAL] placeholders → required by update-skill for section preservation
- Condense parameter tables → full params needed for agent consumption accuracy
