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
- **Workspace drift check:** ok (HEAD 3c048aa4 matches `metadata.source_commit`)
- **Frontmatter validation:** PASS (0 issues)

**Mode Rationale:** `skill_type: 'single'` in metadata — no cross-skill integration surface to validate, so naive mode (API-surface coverage) is the right fit.

**Analysis Plan:**
- Coverage Check: documented exports vs. source `cognee/__init__.py` public API surface (AST-verified against local clone, Deep tier)
- Coherence Check: structural validation of SKILL.md + cross-reference consistency against `references/` (naive mode — no cross-skill patterns to verify)
- Scoring: naive-mode weight distribution (coherence weight redistributed into coverage)

> **Re-run note (2026-04-13):** This report replaces an earlier same-day report. The prior run flagged `cognee.search` at SKILL.md:129 as having "ghost params" (`neighborhood_depth`, `neighborhood_seed_top_k`). That finding was incorrect — those params exist in source at `cognee/api/v1/search/search.py:46-47`. This re-run correctly locates the signature drift in `references/full-api-reference.md:83-102` instead, where the full signature block stops at `retriever_specific_config` and is missing those two trailing params.

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

All 34 top-level exports in `cognee/__init__.py` are documented in `SKILL.md` + `references/full-api-reference.md`. Condensed status table:

| Export | Kind | Documented | Signature | Source | Status |
|---|---|---|---|---|---|
| `add` | async fn | yes | match | `cognee/api/v1/add/add.py:22` | PASS |
| `delete` | async fn (deprecated) | yes (flagged deprecated) | match | `cognee/api/v1/delete/__init__.py:11` | PASS |
| `cognify` | async fn | yes | match | `cognee/api/v1/cognify/cognify.py:44` | PASS |
| `memify` | async fn | yes | match (summary simplified) | `cognee/modules/memify/memify.py:25` | PASS |
| `run_custom_pipeline` | async fn | yes | match | `cognee/modules/run_custom_pipeline/run_custom_pipeline.py:14` | PASS |
| `update` | async fn | yes | match | `cognee/api/v1/update/update.py:12` | PASS |
| `search` | async fn | yes (SKILL.md summary is subset of 10/20 source params) | **drift in references/ full signature block** (18/20 params — missing `neighborhood_depth`, `neighborhood_seed_top_k`) | `cognee/api/v1/search/search.py:27` | **WARN** |
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
- **Signature Mismatches (doc vs source):** 1 (`search` — full signature block in `references/full-api-reference.md:83-102` is missing 2 trailing params that exist in source)
- **Stale Documentation (documented but not in source):** 0
- **Cross-reference consistency (SKILL.md body vs references/):** 1 High finding — SKILL.md:129 summary correctly lists `neighborhood_depth=None, neighborhood_seed_top_k=None`, but the canonical full-signature block in `references/full-api-reference.md:83-102` omits them. Per workflow rule "SKILL.md body is authoritative," the references file is the one to update.
- **Provenance-map drift vs source:** none detected — provenance entry for `search` reflects 21 params (20 real + 1 return annotation entry) that align with source `cognee/api/v1/search/search.py:27-48`.

### Category Scores

| Category | Score |
|---|---|
| Export Coverage | 100% (34/34) |
| Signature Accuracy | 97% (33/34 full-signature blocks match source — `search` full-signature drift in references file) |
| Type Coverage | 100% (`SearchType` enum 15/15 variants documented; `RememberResult` 8/8 attrs documented) |

Note: Category weights applied in step-05 after external validation.

### Coverage findings (feed into Gap Report)

1. **HIGH — references/full-api-reference.md `search` signature block missing 2 trailing params** (GAP-001): lines 83-102 show 18 params ending at `retriever_specific_config`. Source at `cognee/api/v1/search/search.py:46-47` adds `neighborhood_depth: Optional[int] = None` and `neighborhood_seed_top_k: Optional[int] = None`. SKILL.md:129 summary row correctly includes them, so an agent reading the Tier-1 summary will call correctly, but an agent drilling into `references/full-api-reference.md` for the canonical signature will believe the function has only 18 params. Fix: add both params (and the validation caveats at `search.py:49-62`) to the reference file signature block.

2. **INFO — `memify` summary row omits 4 optional params**: `SKILL.md:130` summary row shows 6 params; source has 10 (`user`, `node_type=NodeSet`, `vector_db_config`, `graph_db_config` omitted from summary). Per authoring protocol "brief vs detailed is acceptable when not contradictory" — `references/full-api-reference.md:119+` carries the complete 10-param signature. No action required.

3. **INFO — `search` summary row is a 10-of-20 subset**: `SKILL.md:129` lists 10 most-commonly-tuned params; source has 20. Same acceptable summarization pattern as `memify`. No action required for the summary row itself.

## Coherence Analysis

**Mode:** naive (basic structural validation — coherence not scored in naive mode; its weight is redistributed to coverage per scoring rules)

### Structural checks (SKILL.md)

| Check | Result |
|---|---|
| Frontmatter present and valid | PASS (validator §0 pass, 0 issues) |
| Top-level sections present (Overview, Quick Start, Common Workflows, Key API Summary, Deprecations & Gotchas, Key Types, Architecture at a Glance, CLI) | PASS |
| Section headers properly formatted (`#`, `##`, …) | PASS |
| Code examples language-annotated | PASS (all ```python / ```bash blocks annotated) |
| Markdown well-formed (no unclosed code fences, tables balanced) | PASS |
| `scripts/` or `assets/` directory check | N/A — neither directory exists; Section 7b not required. Only `references/` is present, and SKILL.md correctly links all four reference files. |
| Internal consistency — exports cited in Common Workflows match the exports list | PASS — all names referenced in examples (add, cognify, search, memify, config, SearchType, remember, recall, forget, serve, disconnect, agent_memory, start_ui) are documented exports. |
| Internal consistency — no sync/async contradiction | PASS — `start_ui` correctly documented as sync; `start_visualization_server` correctly documented as a module with a sync call; all other async exports used with `await` in examples. |

### §2b — Migration/Deprecation section gate (Deep tier + evidence-report.md present → gate runs)

- **T2-future annotation count** (read from `forge-data/oms-cognee/1.0.0/evidence-report.md`): **0**.
- **Canonical Section 4b heading** (`## Migration & Deprecation Warnings`): **absent**.
- **Gate trigger condition** (T2-future > 0 AND Section 4b absent): **not met** → no Medium gap.
- **Adjacent finding (Info):** SKILL.md carries an equivalent section titled `## Deprecations & Gotchas` at line 159 that mixes *historical-migration* content (v0.3.9 `delete` deprecation; v1.0.0 `low_level` removal; v1.0.0 `run_migrations` → `run_startup_migrations`; v1.0.0 `pipelines` restructuring) with *current-state signature gotchas* (`start_ui` is sync; `start_visualization_server` is a module; `serve()` triggers Auth0). Hybrid-section content is acceptable but obscures the split — recommendation (Info) in gap report.

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

No access degradation — analysis ran against local source with AST-verified signatures.

## Gap Report

**Total Gaps:** 5
**Blocking (Critical + High):** 1
**Non-blocking (Medium + Low + Info):** 4

### Remediation Summary

| Severity | Count | Estimated Effort |
|---|---|---|
| Critical | 0 | — |
| High | 1 | ~5 min — append 2 params to a single signature block in the reference file |
| Medium | 0 | — |
| Low | 0 | — |
| Info | 4 | Optional — author judgement |
| **Total** | **5** | |

### GAP-001: `references/full-api-reference.md` `search()` signature block missing 2 params

**Severity:** High
**Category:** Coverage (signature accuracy — split-body consistency)
**Source:** `skills/oms-cognee/1.0.0/oms-cognee/references/full-api-reference.md:83-102`

**Issue:** The canonical full-signature block for `cognee.search(...)` stops at `retriever_specific_config: Optional[dict] = None` (18 params). The actual v1.0.0 source signature at `cognee/api/v1/search/search.py:27-48` has 20 params — two additional trailing params exist:

```python
neighborhood_depth: Optional[int] = None,
neighborhood_seed_top_k: Optional[int] = None,
```

Source also validates these at lines 49-62 (`CogneeValidationError` if non-None and not a positive integer). SKILL.md:129's summary row correctly includes both — the drift is confined to the references file. An agent drilling into the canonical reference for the full signature will believe those params don't exist.

**Remediation:** In `references/full-api-reference.md`, after line 101 (`retriever_specific_config: Optional[dict] = None,`) and before the closing `) -> List[SearchResult]` at line 102, append:

```python
    neighborhood_depth: Optional[int] = None,
    neighborhood_seed_top_k: Optional[int] = None,
```

Optionally add a "Key behaviors" bullet noting both must be positive integers when set (`CogneeValidationError` otherwise) — see `cognee/api/v1/search/search.py:49-62`.

### GAP-002: `memify` summary row omits 4 optional params (acceptable summarization)

**Severity:** Info
**Category:** Coverage (summary simplification)
**Source:** `skills/oms-cognee/1.0.0/oms-cognee/SKILL.md:130`

**Issue:** The Key API Summary row for `cognee.memify` shows 6 params; source has 10. Omitted from the summary: `user`, `node_type: Optional[Type] = NodeSet`, `vector_db_config`, `graph_db_config`. Per SKF authoring convention "brief vs detailed is acceptable when not contradictory" this is acceptable because `references/full-api-reference.md:119+` carries the complete 10-param signature.

**Remediation:** None required. Optional: if you want the summary row to signal the default `node_type=NodeSet` filter (load-bearing for the default Rule-node behaviour), add `node_type=NodeSet` to the summary row.

### GAP-003: `Deprecations & Gotchas` section mixes historical migration with current-state gotchas

**Severity:** Info
**Category:** Structural (section scope)
**Source:** `skills/oms-cognee/1.0.0/oms-cognee/SKILL.md:159-172`

**Issue:** The section titled `## Deprecations & Gotchas` carries two distinct content types: (a) historical-migration content (v0.3.9 `delete` deprecation, v1.0.0 `low_level` removal, v1.0.0 `run_migrations` → `run_startup_migrations`, v1.0.0 `pipelines` restructuring) — load-bearing for correcting model training-data drift; and (b) current-state signature gotchas (`start_ui` is sync; `start_visualization_server` is a module; `serve()` triggers Auth0; `agent_memory` requires async wrapped function). Per SKF authoring rule the canonical Section 4b is scoped to forward-looking/historical migration only; current-state gotchas belong alongside their function in Full API Reference. T2-future annotation count is 0, so the Section 4b gate does not fire — this is Info, not Medium.

**Remediation (optional, for a future skill revision):** Split the section into `## Import Corrections` (historical migration, items 1-4) and move items 5-8 (async/sync gotchas) into their respective function entries in `references/full-api-reference.md`. Keep the dual listing here if you prefer a single "what will surprise agents" bucket — the authoring rule is a recommendation, not a hard gate when T2-future=0.

### GAP-004: tessl judge — add workflow validation checkpoints

**Severity:** Info
**Category:** Structural (content actionability)
**Source:** tessl review (Content 73%, workflow_clarity 2/3)

**Issue:** Workflows (`Common Workflows` section) chain `remember → recall` or `add → cognify → search` without explicit validation checkpoints: there is no guidance on checking `RememberResult.status`, handling `CogneeApiError` in `try/except`, or verifying cognify completion before searching. Since cognify pipelines can fail or run in background mode, an agent following the workflow verbatim may search against an incomplete graph and silently produce empty results.

**Remediation (optional):** In `Common Workflows`, after the `remember()` / `cognify()` calls add a 1-2 line example showing result-status inspection — or wrap the V1 chain with `try/except CogneeApiError`. The existing references already cover `RememberResult` attributes; adding a worked example in the workflow narrative would close the gap.

### GAP-005: tessl judge — source-citation token overhead

**Severity:** Info
**Category:** Structural (conciseness)
**Source:** tessl review (Content 73%, conciseness 2/3)

**Issue:** SKILL.md carries `[AST:path:L##]` and `[EXT:url]` provenance markers on nearly every claim. These are load-bearing for the SKF audit workflow (`skf-audit-skill` follows them) but add token overhead for the consuming agent.

**Remediation (optional, not recommended):** If token budget becomes a constraint, move `[AST:...]` / `[EXT:...]` markers to a footnotes section at the end of SKILL.md. **Caveat:** SKF's `skf-audit-skill` and `skf-update-skill` workflows rely on inline provenance markers for drift detection — stripping them degrades auditability. Recommend **keeping markers inline** and accepting the 73% content score as a known split-body artifact rather than a real quality issue.

### Discovery Quality

**Description optimization:** tessl `description_score` is **100%** (specificity 3/3, trigger terms 3/3, completeness 3/3, distinctiveness 3/3) and skill-check raised zero description issues. No action recommended.

**Discovery testing recommended.** Before export, test the skill with 3-5 realistic prompts phrased the way real users actually talk — with casual language, typos, incomplete context, and implicit references. Example realistic prompt patterns:

- Vague: "can you help me remember this pdf my PM sent"
- Implicit: "what did we decide about embeddings last month"
- Abbreviated: "stick this in cognee and let me ask about it"
- Deprecated-surface: "use cognee.delete to remove that record" (tests whether the skill steers the agent toward `forget` / `datasets.delete_data`)
- V1-vs-V2 ambiguous: "set up cognee memory for my agent" (tests whether the skill distinguishes `@agent_memory` + `remember` over raw `add` / `cognify`)
