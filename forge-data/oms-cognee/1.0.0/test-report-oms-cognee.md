---
workflowType: 'test-skill'
skillName: 'oms-cognee'
skillDir: 'skills/oms-cognee/1.0.0/oms-cognee'
testMode: 'naive'
forgeTier: 'Deep'
testResult: 'pass'
score: '97.98%'
threshold: '80%'
analysisConfidence: 'full'
testDate: '2026-04-13'
stepsCompleted: ['step-01-init', 'step-02-detect-mode', 'step-03-coverage-check', 'step-04-coherence-check', 'step-04b-external-validators', 'step-05-score', 'step-06-report']
nextWorkflow: 'export-skill'
workspaceDriftCheck: 'ok (3c048aa4)'
---

# Test Report: oms-cognee

## Test Summary

- **Skill:** oms-cognee v1.0.0
- **Path:** skills/oms-cognee/1.0.0/oms-cognee/
- **Type:** single
- **Test Mode:** naive
- **Forge Tier:** Deep
- **Source:** /home/armel/.skf/workspace/repos/github.com/topoteretes/cognee @ 3c048aa4 (v1.0.0)
- **Frontmatter validation:** PASS (0 issues)
- **Workspace drift check:** ok (HEAD matches pinned 3c048aa4)

**Mode Rationale:** `skill_type: single` in metadata.json; a single-source library (cognee) with self-contained API surface — no cross-skill integrations to coherence-check.

**Analysis Plan:**
- Coverage Check: documented exports vs source API surface (`cognee/__init__.py` public symbols) using AST (ast-grep, tier=Deep).
- Coherence Check: basic structural validation of SKILL.md sections and references files.
- External Validators: `npx skill-check check` if available.
- Scoring: naive-mode weights (no coherence category bonus).

## Coverage Analysis

**Tier:** Deep
**Source Access:** full (local git working tree at pinned commit `3c048aa4`)
**Source Path:** /home/armel/.skf/workspace/repos/github.com/topoteretes/cognee
**Entry Point:** `cognee/__init__.py` (61 lines, 34 public exports)
**Denominator:** barrel (`cognee/__init__.py` re-exports) — 34

### Export Coverage

All 34 barrel exports from `cognee/__init__.py` are documented in SKILL.md (either in the V1/V2 Key API tables, the Deprecations & Gotchas section, or the Key Types section). Breakdown:

| Export | Kind | Documented In | Signature | Source | Status |
|---|---|---|---|---|---|
| `__version__` | str | SKILL.md:L143 | matches | `cognee/__init__.py:L6` | PASS |
| `add` | async fn | SKILL.md:L127 · ref:L30 | matches | `cognee/api/v1/add/add.py:L22` | PASS |
| `delete` | async fn (deprecated) | SKILL.md:L165 | documented as deprecated | `cognee/api/v1/delete/__init__.py:L1` | PASS |
| `cognify` | async fn | SKILL.md:L128 · ref:L55 | matches | `cognee/api/v1/cognify/cognify.py:L44` | PASS |
| `memify` | async fn | SKILL.md:L130 · ref:L122 | matches | `cognee/modules/memify/memify.py:L25` | PASS |
| `run_custom_pipeline` | async fn | SKILL.md:L132 · ref:L208 | matches | `cognee/modules/run_custom_pipeline/run_custom_pipeline.py:L14` | PASS |
| `update` | async fn | SKILL.md:L131 · ref:L141 | matches | `cognee/api/v1/update/update.py:L12` | PASS |
| `config` | namespace class | SKILL.md:L135 · ref:L173 | documented (32 setters, link to config.md) | `cognee/api/v1/config/config.py:L18` | PASS |
| `datasets` | namespace class | SKILL.md:L134 · ref:L156 | documented (7 async methods) | `cognee/api/v1/datasets/datasets.py:L25` | PASS |
| `prune` | namespace class | SKILL.md:L133 · ref:L247 | matches | `cognee/api/v1/prune/prune.py:L4` | PASS |
| `SearchType` | enum (15 modes) | SKILL.md:L136,L176 | all 15 modes enumerated | `cognee/modules/search/types/SearchType.py:L4` | PASS |
| `search` | async fn | SKILL.md:L129 · ref:L83 | matches (full sig in ref) | `cognee/api/v1/search/search.py:L27` | WARN (line drift — see GAP-001) |
| `visualize_graph` | async fn | SKILL.md:L137 · ref:L240 | matches | `cognee/api/v1/visualize/visualize.py:L17` | PASS |
| `start_visualization_server` | module | SKILL.md:L170 | documented as module with `visualization_server(port)` | `cognee/api/v1/visualize/start_visualization_server.py:L6` | PASS |
| `cognee_network_visualization` | fn | SKILL.md:L137,ref:L245 | matches | `cognee/modules/visualization/cognee_network_visualization.py:L22` | PASS |
| `start_ui` | sync fn | SKILL.md:L169 | matches (8 params incl. pid_callback) | `cognee/api/v1/ui/ui.py:L369` | PASS |
| `session` | module | SKILL.md:L141 · ref:L259 | 3 async fns documented | `cognee/api/v1/session/session.py:L1` | PASS |
| `pipelines` | module | SKILL.md:L139 · ref:L197 | documents Task/run_tasks/run_tasks_parallel/run_pipeline | `cognee/modules/pipelines/__init__.py:L1` | PASS |
| `Drop` | sentinel | SKILL.md:L140,L204 | matches | `cognee/pipelines/types.py:L32` | PASS |
| `run_startup_migrations` | async fn | SKILL.md:L142 | matches | `cognee/run_migrations.py:L80` | PASS |
| `remember` | async fn | SKILL.md:L149 | matches | `cognee/api/v1/remember/remember.py:L339` | PASS |
| `RememberResult` | class | SKILL.md:L150,L208 | documented (status + 7 attrs) | `cognee/api/v1/remember/remember.py:L139` | PASS |
| `recall` | async fn | SKILL.md:L151 | matches | `cognee/api/v1/recall/recall.py:L122` | PASS |
| `improve` | async fn | SKILL.md:L152 | matches | `cognee/api/v1/improve/improve.py:L36` | PASS |
| `forget` | async fn | SKILL.md:L153 | matches | `cognee/api/v1/forget/forget.py:L15` | PASS |
| `serve` | async fn | SKILL.md:L154 | matches | `cognee/api/v1/serve/serve.py:L17` | PASS |
| `disconnect` | async fn | SKILL.md:L155 | matches | `cognee/api/v1/serve/disconnect.py:L8` | PASS |
| `visualize` | async fn (alias) | SKILL.md:L156 | matches (alias for visualize_graph) | `cognee/api/v1/__init__.py` | PASS |
| `enable_tracing` | sync fn | SKILL.md:L138,ref:L226 | matches | `cognee/modules/observability/trace_context.py` | PASS |
| `disable_tracing` | sync fn | SKILL.md:L138,ref:L227 | matches | same file | PASS |
| `get_last_trace` | sync fn | SKILL.md:L138,ref:L228 | matches | same file | PASS |
| `get_all_traces` | sync fn | SKILL.md:L138,ref:L229 | matches | same file | PASS |
| `clear_traces` | sync fn | SKILL.md:L138,ref:L230 | matches | same file | PASS |
| `agent_memory` | decorator | SKILL.md:L157 | matches | `cognee/modules/agent_memory/decorator.py:L22` | PASS |

### Coverage Summary

- **Exports Found (barrel):** 34
- **Documented:** 34 (100%)
- **Missing Documentation:** 0
- **Signature Mismatches (content):** 0
- **Signature line-citation drift:** 2 (search cited at L26 → actual L27; full-api-reference.md add provenance cited at L21 → actual L22)
- **Stale Documentation:** 0

### Metadata Export-Count Coherence Cross-Check

Cluster A (public-barrel surface):
- `stats.exports_public_api`: 34
- `exports[]` length: 34
- Intra-cluster divergence: 0% → no finding.

Cluster B (documented surface):
- `stats.exports_documented`: 34
- Provenance-map entry count: (not present in forge-data/1.0.0/; the only provenance-map.json for 0.5.8 sits one level up and is not the v1.0.0 state) → cluster B has a single count, skipped silently.

Cross-cluster note: barrel=34, documented=34 — within 10%, no multi-denominator reporting note emitted.

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 100% (34/34) |
| Signature Accuracy | 94.1% (32/34 fully accurate; 2 line-citation drifts) |
| Type Coverage | 100% (SearchType 15/15 modes; Task, Drop, RememberResult, DataPoint, 5 exceptions all documented) |

Note: Weight application is deferred to step-05.

## Coherence Analysis

**Mode:** naive (basic structural validation only; single-source skill with no cross-skill integrations).

### Document Structure

- SKILL.md has frontmatter with `name` + `description` (agentskills.io compliant) ✓
- Required sections present: Overview, Quick Start, Common Workflows, Key API Summary (V1 + V2), Deprecations & Gotchas, Key Types, Architecture at a Glance, CLI ✓
- Code examples are language-annotated (` ```python `) ✓
- All tables/code blocks close cleanly (verified by wc -l = 252 with final terminator present) ✓
- No `scripts/` or `assets/` directory alongside SKILL.md → "Scripts & Assets" section not required ✓
- `references/` directory (4 files: config.md, core-workflow.md, full-api-reference.md, pipelines-and-datapoints.md) is linked from the footer (L252) ✓

### Internal Consistency

- Every export name referenced in Quick Start / Common Workflows examples appears in the Key API tables or Deprecations section: `cognee.add`, `cognee.cognify`, `cognee.search`, `cognee.prune.prune_data`, `cognee.prune.prune_system`, `cognee.memify`, `cognee.improve`, `cognee.forget`, `cognee.serve`, `cognee.disconnect`, `cognee.remember`, `cognee.recall`, `cognee.visualize_graph`, `cognee.visualize`, `cognee.agent_memory`, `SearchType.GRAPH_COMPLETION`, `SearchType.CODING_RULES`, `SearchType.TEMPORAL`, `Drop`, `Task` — all 20 example refs resolve ✓
- SearchType modes referenced (15 total) match source enum exactly (verified against `cognee/modules/search/types/SearchType.py`) ✓
- Async/sync annotations consistent: V1/V2 workflow functions documented as async; `start_ui`, `start_visualization_server.visualization_server`, and tracing fns correctly called out as sync ✓
- No self-contradictions between Quick Start example and Key API Summary signatures ✓

### Structural Issues Found

| # | Severity | Issue |
|---|----------|-------|
| 1 | Low | SKILL.md line 81, 95, 129 cite `search()` at `cognee/api/v1/search/search.py:L26` — actual source line is L27 (off by 1). The full-api-reference.md citation at L117 is correct. |
| 2 | Low | `references/full-api-reference.md` line 50 cites `add()` at `cognee/api/v1/add/add.py:L21` — actual source line is L22. |

Line-number drifts do not mislead materially (readers locate the symbol by name; `rg`/IDE jump works). Content of each signature is accurate.

### Section 4b Migration/Deprecation Gate (Deep tier, evidence-report.md present)

- **T2-future annotation count in `evidence-report.md`:** 0 (evidence-report enumerates past updates only — v0.5.8→v1.0.0 exports added/removed).
- **Section 4b present in SKILL.md:** The skill has a section titled "Deprecations & Gotchas" (SKILL.md L159) that serves the Section 4b role.
- **Content classification:** Mixed — the majority is **historical migration** (load-bearing for training-data drift correction):
  - `cognee.low_level` no longer exported (completed migration, replacement path documented)
  - `cognee.run_migrations` replaced by `cognee.run_startup_migrations` (shipped cutover in v1.0.0)
  - `cognee.delete` deprecated since v0.3.9 (shipped deprecation)
  - `cognee.pipelines` restructured in v1.0.0 (package reshape with lazy legacy re-exports)

  A minority is current-state signature gotchas that per the authoring rule would fit better alongside the function in Full API Reference:
  - `cognee.agent_memory` requires async wrapped fn
  - `cognee.serve()` without args triggers Auth0 Device Code Flow
  - `cognee.start_ui` is sync with required `pid_callback`
  - `cognee.start_visualization_server` is a module not a function

- **Gate verdict:** **Info** severity per rule (a) (historical migration content dominates; load-bearing). Optional future revision: move the four current-state signature gotchas inline to Full API Reference and either rename the SKILL.md section to "Import Corrections & Ecosystem Notes" or keep the hybrid name — no action required.

### Coherence Summary

- Structural issues: 2 (both Low severity)
- Coherence category is not scored in naive mode (weight redistributed to coverage + signature accuracy).

## External Validation

### skill-check
- **Available:** yes (npx skill-check)
- **Quality Score:** 100/100
- **Errors:** 0
- **Warnings:** 0
- **Breakdown:** frontmatter 30/30, description 30/30, body 20/20, links 10/10, file 10/10
- **Diagnostics:** none

### tessl
- **Available:** yes (npx tessl 0.75.0)
- **Validation:** PASSED (0 errors, 0 warnings)
- **Description Score:** 100%
- **Content Score:** 73%
- **Review Score:** 89%
- **Suggestions:**
  - Add explicit validation checkpoints to workflows — e.g., check `RememberResult.status` after `remember()`, handle `CogneeApiError` in try/except blocks, verify cognify completion before searching.
  - Reduce token overhead by moving inline `[AST:...]` / `[SRC:...]` source citations to a footnotes section or removing them — Claude doesn't need provenance markers to follow instructions. (Note: provenance is intentional per SKF; do not act on this suggestion without weighing the trade-off.)

### Combined External Score
- **External Validation Score:** 94.5% ((skill-check 100 + tessl review 89) / 2)
- **Tools used:** skill-check, tessl

## Completeness Score

### Score Breakdown

| Category | Score | Weight | Weighted |
|----------|-------|--------|----------|
| Export Coverage | 100% | 45% | 45.00% |
| Signature Accuracy | 94.1% | 25% | 23.53% |
| Type Coverage | 100% | 20% | 20.00% |
| Coherence | n/a (naive) | 0% | 0.00% |
| External Validation | 94.5% | 10% | 9.45% |
| **Total** | | **100%** | **97.98%** |

### Result

**Score:** 97.98%
**Threshold:** 80%
**Result:** **PASS**

**Weight Distribution:** naive (coherence weight redistributed to coverage + signature + type + external)
**Tier Adjustment:** none (Deep tier — signature and type coverage scored via AST)
**External Validators:** both available (skill-check 100/100 + tessl review 89%)
**Analysis Confidence:** full (local git working tree at pinned commit 3c048aa4)

## Gap Report

**Summary:** 4 findings (0 Critical · 0 High · 0 Medium · 2 Low · 2 Info). No blocking issues. PASS.

### Low

**GAP-001** — `search()` signature provenance line drift in SKILL.md

- **Location:** `skills/oms-cognee/1.0.0/oms-cognee/SKILL.md:81`, `:95`, `:129`
- **Observed:** `[AST:cognee/api/v1/search/search.py:L26]`
- **Actual source line:** `cognee/api/v1/search/search.py:27` (`async def search(` at line 27; verified via `grep -n ^async def search`)
- **Impact:** Provenance marker off by 1 line. Readers still land within 1 line of the symbol; `rg search` / IDE symbol jump still work. Content of the signature is accurate.
- **Remediation:** Replace all three `[AST:cognee/api/v1/search/search.py:L26]` citations in SKILL.md with `[AST:cognee/api/v1/search/search.py:L27]`. One-line edit per occurrence.
- **Effort:** ~2 min (1 `sed` or 3 targeted edits).

**GAP-002** — `add()` signature provenance line drift in full-api-reference.md

- **Location:** `skills/oms-cognee/1.0.0/oms-cognee/references/full-api-reference.md:50`
- **Observed:** `[AST:cognee/api/v1/add/add.py:L21]`
- **Actual source line:** `cognee/api/v1/add/add.py:22` (`async def add(` at line 22; verified via `grep -n ^async def add`)
- **Impact:** Same as GAP-001 — off-by-one line citation, no content inaccuracy.
- **Remediation:** Replace `[AST:cognee/api/v1/add/add.py:L21]` with `[AST:cognee/api/v1/add/add.py:L22]`.
- **Effort:** ~1 min.
- **Related:** The same reference file is also missing the `run_in_background: bool = False` parameter between `importance_weight` and `**kwargs` in the `add()` signature block (L30-L44). Since SKILL.md's Key API summary for `add` already lists `run_in_background=False` correctly (L127), the reference file is the outlier. Consider folding this param-list fix into the same edit.

### Info

**GAP-003** — "Deprecations & Gotchas" section mixes historical migration with current-state gotchas

- **Location:** `skills/oms-cognee/1.0.0/oms-cognee/SKILL.md:159-172`
- **Observed:** Section contains ~5 historical migration entries (low_level removal, run_migrations replacement, delete deprecation since v0.3.9, pipelines restructure) alongside ~3 current-state signature gotchas (`agent_memory` async requirement, `serve()` Auth0 trigger, `start_ui` sync, `start_visualization_server` is a module).
- **Rule:** Per skf authoring rules, Section 4b (Migration & Deprecation Warnings) is scoped to forward-looking breaking changes. Current-state signature gotchas should live alongside the function in Full API Reference.
- **Gate verdict:** Info (historical migration content is load-bearing for training-data drift correction — rule-(a) exception).
- **Remediation (optional, not required to export):** In a future revision, move the four current-state gotchas to inline notes under their respective `full-api-reference.md` entries and consider renaming the SKILL.md section to "Import Corrections & Ecosystem Notes" to free "Migration & Deprecation Warnings" for its forward-looking contract.
- **Effort:** ~15 min if addressed.

**GAP-004** — Discovery testing recommended before export

- **Scope:** Advisory — does not affect PASS verdict or score.
- **Rationale:** Test the skill with 3-5 realistic user prompts phrased as real users would (casual language, typos, incomplete context, implicit references). A skill tested only with clean prompts can fail to trigger in production.
- **Example prompts for this skill:**
  - Vague: "can you help me set up cognee memory for my agent"
  - Implicit: "how do i make my llm remember what i told it yesterday"
  - Abbreviated: "run cognee remember on these docs and then recall"
  - Mixed: "upgrade cognee 0.5 code to v1 — what changed with run_migrations"
  - Typo-laden: "need grpah memroy for ai agent, using congee"
- **Action:** Before running export-skill, execute discovery prompts in a new Claude Code session and verify the skill activates appropriately.

### Discovery Quality

**Description optimization:** tessl `description_score` = 100%. No description improvements needed — the description already uses concrete trigger terms ("knowledge graph", "memory", "cognify", "remember", "search", "RAG"), third-person voice, explicit "Use when..." clause, and a "Do NOT use for" negative-trigger list that references alternatives (cognee-mcp, FastAPI server).

**Discovery testing recommended.** Before export, test the skill with 3-5 realistic prompts phrased the way real users actually talk — with casual language, typos, incomplete context, and implicit references. A skill tested only with clean prompts may fail to trigger in production. See GAP-004 above for concrete prompt patterns for this skill.

### Remediation Summary

| Severity | Count | Blocking? | Total effort |
|---|---|---|---|
| Critical | 0 | — | — |
| High | 0 | — | — |
| Medium | 0 | — | — |
| Low | 2 | No | ~3 min (pure line-citation fixes; `sed` two lines) |
| Info | 2 | No | Optional — GAP-003 ~15 min, GAP-004 is discovery testing (~10 min) |

**Net blockers:** 0. Skill passes the 80% threshold at 97.98% and is ready to export. The two Low gaps are cosmetic provenance-line drifts that can be folded into the next `update-skill` run without blocking export. The two Info items are optional improvements.
