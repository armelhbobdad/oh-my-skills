---
workflowType: 'test-skill'
skillName: 'oms-cognee'
skillDir: 'skills/oms-cognee/1.0.0/oms-cognee'
testMode: 'naive'
forgeTier: 'Deep'
testResult: 'pass'
score: '98.7%'
threshold: '80%'
analysisConfidence: 'full'
testDate: '2026-04-13'
stepsCompleted: ['step-01-init', 'step-02-detect-mode', 'step-03-coverage-check', 'step-04-coherence-check', 'step-04b-external-validators', 'step-05-score', 'step-06-report']
nextWorkflow: 'export-skill'
---

# Test Report: oms-cognee

## Test Summary

- **Skill:** oms-cognee
- **Version:** 1.0.0 (active)
- **Path:** `skills/oms-cognee/1.0.0/oms-cognee/`
- **Type:** single
- **Test Mode:** naive
- **Forge Tier:** Deep
- **Source:** `/home/armel/.skf/workspace/repos/github.com/topoteretes/cognee` @ `3c048aa4` (v1.0.0)
- **Frontmatter validation:** PASS (0 issues)

**Mode Rationale:** `skill_type: 'single'` in metadata — no cross-skill integration surface to validate, so naive mode (API-surface coverage) is the right fit.

**Analysis Plan:**
- Coverage Check: documented exports vs. source `cognee/__init__.py` public API surface (AST-backed, Deep tier)
- Coherence Check: structural validation of SKILL.md and references/ (no cross-skill integration patterns to verify in naive mode)
- Scoring: naive-mode weight distribution (no coherence/integration category)

## Coverage Analysis

**Tier:** Deep
**Source Access:** full (State 1 — local clone at `/home/armel/.skf/workspace/repos/github.com/topoteretes/cognee` @ `3c048aa4`)
**Analysis Confidence:** T1 (full source + provenance-map, all provenance entries T1 AST-verified)
**Source Path:** `cognee/` package
**Files Analyzed:** 34 public exports (provenance-map §entries — 34 entries, matches `metadata.json.exports[]` length 34)
**Denominator:** standard barrel (`cognee/__init__.py` re-exports) — 34 top-level public names. Stratified-scope clause does not apply (single-package repo).

### Metadata coherence (§4b intra/cross-cluster)

- **Cluster A (barrel):** `stats.exports_public_api=34`, `exports[].length=34` → 0% drift. No finding.
- **Cluster B (documented surface):** `stats.exports_documented=34`, provenance-map entries=34 → 0% drift. No finding.
- **Cross-cluster:** barrel=34, documented=34 → within 10%, no multi-denominator note needed.

### Export Coverage (per-export)

All 34 top-level exports in `cognee/__init__.py` are documented in `SKILL.md` + `references/full-api-reference.md`. A condensed status table follows; full per-export detail matches the provenance-map entry list at `forge-data/oms-cognee/1.0.0/provenance-map.json`.

| Export | Kind | Documented | Signature | Source | Status |
|---|---|---|---|---|---|
| `add` | async fn | yes | match | `cognee/api/v1/add/add.py:22` | PASS |
| `delete` | async fn (deprecated) | yes (flagged deprecated) | match | `cognee/api/v1/delete/__init__.py:11` | PASS |
| `cognify` | async fn | yes | match | `cognee/api/v1/cognify/cognify.py:44` | PASS |
| `memify` | async fn | yes | match (summary simplified) | `cognee/modules/memify/memify.py:25` | PASS |
| `run_custom_pipeline` | async fn | yes | match | `cognee/modules/run_custom_pipeline/run_custom_pipeline.py:14` | PASS |
| `update` | async fn | yes | match | `cognee/api/v1/update/update.py:12` | PASS |
| `search` | async fn | yes | **drift** | `cognee/api/v1/search/search.py:26` | **WARN** |
| `visualize_graph` | async fn | yes | match | `cognee/api/v1/visualize/visualize.py:17` | PASS |
| `start_visualization_server` | module | yes | match | `cognee/api/v1/visualize/start_visualization_server.py:6` | PASS |
| `cognee_network_visualization` | async fn | yes | match | `cognee/modules/visualization/cognee_network_visualization.py:22` | PASS |
| `start_ui` | sync fn | yes | match | `cognee/api/v1/ui/ui.py:369` | PASS |
| `session` | module | yes | match | `cognee/api/v1/session/session.py:1` | PASS |
| `pipelines` | module | yes | match | `cognee/modules/pipelines/__init__.py:1` | PASS |
| `Drop` | sentinel | yes | match | `cognee/pipelines/types.py:32` | PASS |
| `run_startup_migrations` | async fn | yes | match | `cognee/run_migrations.py:80` | PASS |
| `remember` | async fn | yes | match | `cognee/api/v1/remember/remember.py:339` | PASS |
| `RememberResult` | class | yes | match (8/8 attrs) | `cognee/api/v1/remember/remember.py:139` | PASS |
| `recall` | async fn | yes | match | `cognee/api/v1/recall/recall.py:122` | PASS |
| `improve` | async fn | yes | match | `cognee/api/v1/improve/improve.py:36` | PASS |
| `forget` | async fn | yes | match | `cognee/api/v1/forget/forget.py:15` | PASS |
| `serve` | async fn | yes | match | `cognee/api/v1/serve/serve.py:17` | PASS |
| `disconnect` | async fn | yes | match | `cognee/api/v1/serve/disconnect.py:8` | PASS |
| `visualize` | async fn (alias) | yes | match | `cognee/api/v1/__init__.py:6` | PASS |
| `enable_tracing` | sync fn | yes | match | `cognee/modules/observability/trace_context.py:16` | PASS |
| `disable_tracing` | sync fn | yes | match | `cognee/modules/observability/trace_context.py:27` | PASS |
| `get_last_trace` | sync fn | yes | match | `cognee/modules/observability/trace_context.py:65` | PASS |
| `get_all_traces` | sync fn | yes | match | `cognee/modules/observability/trace_context.py:76` | PASS |
| `clear_traces` | sync fn | yes | match | `cognee/modules/observability/trace_context.py:85` | PASS |
| `agent_memory` | decorator | yes | match | `cognee/modules/agent_memory/decorator.py:22` | PASS |
| `SearchType` | enum | yes | match (15/15 variants) | `cognee/modules/search/types/SearchType.py:4` | PASS |
| `config` | class/namespace | yes | match (32 setters + `set()`) | `cognee/api/v1/config/config.py:18` | PASS |
| `datasets` | class/namespace | yes | match (8 methods) | `cognee/api/v1/datasets/datasets.py:25` | PASS |
| `prune` | class/namespace | yes | match (2 methods) | `cognee/api/v1/prune/prune.py:4` | PASS |
| `__version__` | variable | yes | match | `cognee/__init__.py:6` | PASS |

### Coverage Summary

- **Exports Found (source barrel):** 34
- **Documented:** 34 (100%)
- **Missing Documentation:** 0
- **Signature Mismatches (doc vs source):** 1 (`search` summary row at SKILL.md:129)
- **Stale Documentation (documented but not in source):** 0
- **Cross-reference consistency (SKILL.md body vs references/):** 1 High finding (search signature divergence between SKILL.md summary and references/full-api-reference.md signature block)
- **Provenance-map drift vs source:** 2 ghost params (`neighborhood_depth`, `neighborhood_seed_top_k`) in provenance entry for `search` — same drift as SKILL.md:129 summary row. Provenance-map drift is not a SKILL.md coverage gap but is noted for update-skill.

### Category Scores

| Category | Score |
|---|---|
| Export Coverage | 100% (34/34) |
| Signature Accuracy | 97% (33/34 documented signatures match source — search summary row has 2 ghost params) |
| Type Coverage | 100% (`SearchType` enum 15/15 variants documented; `RememberResult` 8/8 attrs documented) |

Note: Category weights applied in step-05 after external validation.

### Coverage findings (feed into Gap Report)

1. **HIGH — signature drift (`search` summary row vs source)**: `SKILL.md:129` lists `neighborhood_depth=None, neighborhood_seed_top_k=None` as part of the `cognee.search` summary signature; the source signature at `cognee/api/v1/search/search.py:26` ends at `retriever_specific_config` (19 params, no neighborhood params). `references/full-api-reference.md:83` signature block is correct. The SKILL.md summary table drifted — likely a stale artifact from a pre-v1.0.0 extraction or a mislabelled extension. Fix: drop both params from the SKILL.md:129 summary row, OR add them to source if they're intended.

2. **LOW — provenance-map drift (`search` entry)**: `forge-data/oms-cognee/1.0.0/provenance-map.json` entry for `search` includes the same 2 ghost params (`neighborhood_depth`, `neighborhood_seed_top_k`) at positions 19–20. Not a SKILL.md coverage gap, but should be reconciled on next `skf-update-skill` re-extraction run.

3. **INFO — memify summary simplification**: `SKILL.md:130` summary row omits 4 optional params present in source (`user`, `node_type`, `vector_db_config`, `graph_db_config`). Per protocol "brief vs detailed is acceptable when not contradictory" — signatures block in `references/full-api-reference.md:119` carries the full 10-param signature. No action required.

## Coherence Analysis

**Mode:** naive (basic structural validation — coherence not scored in naive mode; its weight is redistributed to coverage per scoring rules)

### Structural checks (SKILL.md)

| Check | Result |
|---|---|
| Frontmatter present and valid | PASS (validator §0 pass) |
| Top-level sections present (Overview, Quick Start, Common Workflows, Key API Summary, Deprecations & Gotchas, Key Types, Architecture at a Glance, CLI) | PASS |
| Section headers properly formatted (`#`, `##`, …) | PASS |
| Code examples language-annotated | PASS (all ```python / ```bash blocks annotated — spot-checked Quick Start, Common Workflows, Config examples) |
| Markdown well-formed (no unclosed code fences, tables balanced) | PASS |
| `scripts/` or `assets/` directory check | N/A — neither directory exists; Section 7b not required. Only `references/` is present, and SKILL.md:252 correctly links all four reference files. |
| Internal consistency — exports cited in Common Workflows match the exports list | PASS — all names referenced in examples (add, cognify, search, memify, config, SearchType, remember, recall, forget, serve, disconnect, agent_memory, start_ui) are documented exports. |
| Internal consistency — no sync/async contradiction | PASS — `start_ui` correctly documented as sync (Deprecations & Gotchas line 169); `start_visualization_server` correctly documented as a module with a sync call (line 170); all other async exports used with `await` in examples. |

### §2b — Migration/Deprecation section gate (Deep tier + evidence-report.md present → gate runs)

- **T2-future annotation count** (read from `forge-data/oms-cognee/1.0.0/evidence-report.md`): **0**.
- **Canonical Section 4b heading** (`## Migration & Deprecation Warnings`): **absent**.
- **Gate trigger condition** (T2-future > 0 AND Section 4b absent): **not met** → no Medium gap.
- **Adjacent finding (Info):** SKILL.md carries an equivalent section titled `## Deprecations & Gotchas` at line 159 that mixes *historical-migration* content (v0.3.9 `delete` deprecation; v1.0.0 `low_level` removal; v1.0.0 `run_migrations` → `run_startup_migrations`; v1.0.0 `pipelines` restructuring) with *current-state signature gotchas* (`start_ui` is sync; `start_visualization_server` is a module; `serve()` triggers Auth0). Per authoring rule, forward-looking migration content belongs under Section 4b and current-state gotchas belong alongside their function in Full API Reference. Since T2-future=0 no gate is triggered, but the hybrid title obscures the split — recommendation (Info) in gap report.

### Structural issues summary

```
{
  "structural_issues": [],
  "section_name_observation": "Deprecations & Gotchas mixes historical-migration with current-state gotchas (Info only)",
  "issues_found": 0
}
```

No blocking structural issues. Naive coherence category is not scored; its weight redistributes to Export Coverage / Signature / Type per scoring rules.

## External Validation

### skill-check

- **Available:** yes (`npx skill-check`)
- **Quality Score:** **100 / 100**
- **Errors:** 0
- **Warnings:** 0
- **Breakdown:** frontmatter 30/30 · description 30/30 · body 20/20 · links 10/10 · file 10/10
- **Diagnostics:** none

### tessl

- **Available:** yes (`npx -y tessl skill review`)
- **Validation:** PASSED (0 errors, 0 warnings)
- **Description Score:** **100%** (specificity 3/3, trigger-term quality 3/3, completeness 3/3, distinctiveness 3/3)
- **Content Score:** **73%** (conciseness 2/3, actionability 3/3, workflow-clarity 2/3, progressive-disclosure 3/3)
- **Review Score:** **89%**
- **Judge Suggestions:**
  - Add explicit validation checkpoints to workflows — e.g. check `RememberResult.status` after `remember()`, handle `CogneeApiError` in try/except, verify cognify completion before searching.
  - Reduce token overhead by moving inline `[AST:…]` / `[SRC:…]` source citations to a footnote section or removing them — Claude doesn't need provenance markers to follow instructions.

### Combined External Score

- **External Validation Score:** (100 + 89) / 2 = **94.5%**
- **Tools used:** skill-check, tessl
- **Content-quality threshold (70%):** tessl content = 73% → above threshold, no warning.

## Completeness Score

### Score Breakdown

| Category | Score | Weight | Weighted |
|---|---|---|---|
| Export Coverage | 100% | 45.0% | 45.00% |
| Signature Accuracy | 97% | 25.0% | 24.25% |
| Type Coverage | 100% | 20.0% | 20.00% |
| Coherence (naive) | N/A | 0% | 0.00% |
| External Validation | 94.5% | 10.0% | 9.45% |
| **Total** | | **100.0%** | **98.70%** |

### Result

- **Score:** **98.7%**
- **Threshold:** 80%
- **Result:** **PASS**
- **Weight Distribution:** naive (coherence weight already redistributed into coverage per scoring rules)
- **Tier Adjustment:** none (Deep tier — Signature Accuracy and Type Coverage fully scored against local source)
- **External Validators:** both available (skill-check 100/100, tessl review 89%)
- **Analysis Confidence:** full (State 1 — local clone + all-T1 provenance-map)

No access degradation — analysis ran against local source with AST-verified signatures. No degradation notice required.

## Gap Report

**Total Gaps:** 6
**Blocking (Critical + High):** 1
**Non-blocking (Medium + Low + Info):** 5

### Remediation Summary

| Severity | Count | Estimated Effort |
|---|---|---|
| Critical | 0 | — |
| High | 1 | ~5 min — single summary-row edit in SKILL.md |
| Medium | 0 | — |
| Low | 1 | ~10 min — next `skf-update-skill` run will reconcile automatically |
| Info | 4 | Optional — author judgement |
| **Total** | **6** | |

### GAP-001: `cognee.search` summary row lists 2 params not present in source

**Severity:** High
**Category:** Coverage (signature accuracy)
**Source:** `skills/oms-cognee/1.0.0/oms-cognee/SKILL.md:129`

**Issue:** The Key API Summary row for `cognee.search` ends the parameter list with `neighborhood_depth=None, neighborhood_seed_top_k=None`. These two params do not exist in the actual v1.0.0 source signature at `cognee/api/v1/search/search.py:26` (last param is `retriever_specific_config: Optional[dict] = None`). The full signature block in `references/full-api-reference.md:83-102` is correct and contains 19 params. Source of drift: the SKILL.md summary row (and provenance-map entry — see GAP-003) retained two params that were either removed before v1.0.0 shipped or never existed. Agents using the SKILL.md Tier 1 summary will call `search(..., neighborhood_depth=N)` and hit `TypeError: search() got an unexpected keyword argument`.

**Remediation:** Edit `SKILL.md:129`. Replace the parameter list cell `` `query_text, query_type=SearchType.GRAPH_COMPLETION, datasets=None, top_k=10, node_name=None, only_context=False, session_id=None, verbose=False, neighborhood_depth=None, neighborhood_seed_top_k=None` `` with `` `query_text, query_type=SearchType.GRAPH_COMPLETION, datasets=None, top_k=10, node_name=None, only_context=False, session_id=None, verbose=False` ``. Keep the provenance citation `[AST:cognee/api/v1/search/search.py:L26]` unchanged.

### GAP-002: provenance-map `search` entry carries the same 2 ghost params

**Severity:** Low
**Category:** Coverage (data-quality — provenance artifact, not SKILL.md)
**Source:** `forge-data/oms-cognee/1.0.0/provenance-map.json` entries[6] (`export_name: "search"`), params indices 18–19

**Issue:** The provenance-map entry for `search` lists 21 params including `neighborhood_depth: Optional[int] = None` and `neighborhood_seed_top_k: Optional[int] = None`, but the on-disk v1.0.0 source at `cognee/api/v1/search/search.py:26` has only 19 params. This is the origin of GAP-001 — the SKILL.md summary row was generated from this provenance entry. Not a SKILL.md gap per se, but leaving it unreconciled will cause the same drift to resurface on the next `skf-update-skill` regeneration.

**Remediation:** Run `skf-update-skill oms-cognee` after fixing GAP-001 — the update workflow will re-extract the signature from source and overwrite the stale provenance entry. Alternatively, edit `provenance-map.json` manually to drop params indices 18–19 from the `search` entry.

### GAP-003: `memify` summary row omits 4 optional params (acceptable summarization)

**Severity:** Info
**Category:** Coverage (summary simplification)
**Source:** `skills/oms-cognee/1.0.0/oms-cognee/SKILL.md:130`

**Issue:** The Key API Summary row for `cognee.memify` shows 6 params; source has 10. Omitted from the summary: `user`, `node_type: Optional[Type] = NodeSet`, `vector_db_config`, `graph_db_config`. Per SKF authoring convention "brief vs detailed is acceptable when not contradictory" this is acceptable because the full signature block at `references/full-api-reference.md:119-131` carries the complete 10-param signature.

**Remediation:** None required. Optional: if you want the summary row to signal the default `node_type=NodeSet` filter (load-bearing for the default Rule-node behaviour), add `node_type=NodeSet` to the summary row.

### GAP-004: `Deprecations & Gotchas` section mixes historical migration with current-state gotchas

**Severity:** Info
**Category:** Structural (section scope)
**Source:** `skills/oms-cognee/1.0.0/oms-cognee/SKILL.md:159-172`

**Issue:** The section titled `## Deprecations & Gotchas` carries two distinct content types: (a) historical-migration content (v0.3.9 `delete` deprecation, v1.0.0 `low_level` removal, v1.0.0 `run_migrations` → `run_startup_migrations`, v1.0.0 `pipelines` restructuring) — load-bearing for correcting model training-data drift; and (b) current-state signature gotchas (`start_ui` is sync; `start_visualization_server` is a module; `serve()` triggers Auth0; `agent_memory` requires async wrapped function). Per SKF authoring rule the canonical Section 4b is scoped to forward-looking/historical migration only; current-state gotchas belong alongside their function in Full API Reference. T2-future annotation count is 0, so the Section 4b gate does not fire — this is Info, not Medium.

**Remediation (optional, for a future skill revision):** Split the section into `## Import Corrections` (historical migration, items 1-4) and move items 5-8 (async/sync gotchas) into their respective function entries in `references/full-api-reference.md`. Keep the dual listing here if you prefer a single "what will surprise agents" bucket — the authoring rule is a recommendation, not a hard gate when T2-future=0.

### GAP-005: tessl judge — add workflow validation checkpoints

**Severity:** Info
**Category:** Structural (content actionability)
**Source:** tessl review (Content 73%, workflow_clarity 2/3)

**Issue:** Workflows (`Common Workflows` section) chain `remember → recall` or `add → cognify → search` without explicit validation checkpoints: there is no guidance on checking `RememberResult.status`, handling `CogneeApiError` in `try/except`, or verifying cognify completion before searching. Since cognify pipelines can fail or run in background mode, an agent following the workflow verbatim may search against an incomplete graph and silently produce empty results.

**Remediation (optional):** In `Common Workflows`, after the `remember()` / `cognify()` calls add a 1-2 line example showing `result = await remember(...); await result; if result.status != "completed": raise RuntimeError(result.error)` — or wrap the V1 chain with `try/except CogneeApiError`. The existing references already cover `RememberResult` attributes; adding a worked example in the workflow narrative would close the gap.

### GAP-006: tessl judge — source-citation token overhead

**Severity:** Info
**Category:** Structural (conciseness)
**Source:** tessl review (Content 73%, conciseness 2/3)

**Issue:** SKILL.md carries `[AST:path:L##]` and `[EXT:url]` provenance markers on nearly every claim (visible throughout Deprecations & Gotchas and Key API Summary). These are load-bearing for the SKF audit workflow (`skf-audit-skill` follows them) but add token overhead for the consuming agent.

**Remediation (optional, not recommended):** If token budget becomes a constraint, move `[AST:...]` / `[EXT:...]` markers to a footnotes section at the end of SKILL.md. **Caveat:** SKF's `skf-audit-skill` and `skf-update-skill` workflows rely on inline provenance markers for drift detection — stripping them degrades auditability. Recommend **keeping markers inline** and accepting the 73% content score as a known split-body artifact rather than a real quality issue.

### Discovery Quality

**Description optimization:** tessl `description_score` is **100%** (specificity 3/3, trigger terms 3/3, completeness 3/3, distinctiveness 3/3) and skill-check raised zero description issues. No action recommended.

**Discovery testing recommended.** Before export, test the skill with 3-5 realistic prompts phrased the way real users actually talk — with casual language, typos, incomplete context, and implicit references. A skill tested only with clean prompts may fail to trigger in production. Example realistic prompt patterns:

- Vague: "can you help me remember this pdf my PM sent"
- Implicit: "what did we decide about embeddings last month"
- Abbreviated: "stick this in cognee and let me ask about it"
- Deprecated-surface: "use cognee.delete to remove that record" (tests whether the skill steers the agent toward `forget`/`datasets.delete_data`)
- V1-vs-V2 ambiguous: "set up cognee memory for my agent" (tests whether the skill distinguishes `@agent_memory` + `remember` over raw `add`/`cognify`)

### GAP-007: Discovery testing not yet performed

**Severity:** Info
**Category:** Structural (discovery readiness)
**Source:** test-skill workflow scope

**Issue:** This test ran spec-compliance and API-surface coverage only. Realistic-prompt trigger testing has not been executed in this workflow run.

**Remediation:** Perform 3-5 realistic-prompt invocations after export (or in a sandbox Claude session) and verify the skill activates. Advisory only — does not block export.
