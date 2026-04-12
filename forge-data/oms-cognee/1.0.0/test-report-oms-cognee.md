---
workflowType: 'test-skill'
skillName: 'oms-cognee'
skillDir: 'skills/oms-cognee/1.0.0/oms-cognee'
testMode: 'naive'
forgeTier: 'Deep'
testResult: 'pass'
score: '99.00%'
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
- Coverage Check: documented exports vs source API surface (`cognee/__init__.py` public symbols) via AST (ast-grep, tier=Deep).
- Coherence Check: basic structural validation of SKILL.md sections and split-body consistency with references files.
- External Validators: `npx skill-check check` + `npx tessl skill review`.
- Scoring: naive-mode weights.

## Coverage Analysis

**Tier:** Deep
**Source Access:** full (local git working tree at pinned commit `3c048aa4`)
**Source Path:** /home/armel/.skf/workspace/repos/github.com/topoteretes/cognee
**Entry Point:** `cognee/__init__.py` (61 lines, 34 public exports)
**Denominator:** barrel (`cognee/__init__.py` re-exports) — 34

### Export Coverage

All 34 barrel exports from `cognee/__init__.py` are documented in SKILL.md (V1/V2 Key API tables, Deprecations & Gotchas, or Key Types).

| Export | Kind | Documented | Signature vs source | Source | Status |
|---|---|---|---|---|---|
| `__version__` | str | SKILL.md:L143 | matches | `cognee/__init__.py:L6` | PASS |
| `add` | async fn | SKILL.md:L127 · ref:L30 | matches (13 params, all types + defaults) | `cognee/api/v1/add/add.py:L22` | PASS |
| `delete` | async fn (deprecated) | SKILL.md:L165 | correctly flagged `@deprecated(version="0.3.9")` | `cognee/api/v1/delete/__init__.py:L1` | PASS |
| `cognify` | async fn | SKILL.md:L128 · ref:L56 | matches (15 params) | `cognee/api/v1/cognify/cognify.py:L44` | PASS |
| `memify` | async fn | SKILL.md:L130 · ref:L123 | matches (10 params) | `cognee/modules/memify/memify.py:L25` | PASS |
| `run_custom_pipeline` | async fn | SKILL.md:L132 · ref:L209 | matches (11 params) | `cognee/modules/run_custom_pipeline/run_custom_pipeline.py:L14` | PASS |
| `update` | async fn | SKILL.md:L131 · ref:L142 | matches (9 params) | `cognee/api/v1/update/update.py:L12` | PASS |
| `config` | namespace class | SKILL.md:L135 · ref:L174 | 32 setters enumerated; config.md has full list | `cognee/api/v1/config/config.py:L18` | PASS |
| `datasets` | namespace class | SKILL.md:L134 · ref:L157 | 8 async methods enumerated | `cognee/api/v1/datasets/datasets.py:L25` | PASS |
| `prune` | namespace class | SKILL.md:L133 · ref:L248 | matches | `cognee/api/v1/prune/prune.py:L4` | PASS |
| `SearchType` | enum (15 modes) | SKILL.md:L136,L176 | all 15 modes enumerated | `cognee/modules/search/types/SearchType.py:L4` | PASS |
| `search` | async fn | SKILL.md:L129 · ref:L84 | matches (20 params; keyword behaviors documented) | `cognee/api/v1/search/search.py:L27` | PASS |
| `visualize_graph` | async fn | SKILL.md:L137 · ref:L241 | matches | `cognee/api/v1/visualize/visualize.py:L17` | PASS |
| `start_visualization_server` | module | SKILL.md:L170 | documented as module exposing `visualization_server(port)` | `cognee/api/v1/visualize/start_visualization_server.py:L6` | PASS |
| `cognee_network_visualization` | fn | SKILL.md:L137 · ref:L246 | matches | `cognee/modules/visualization/cognee_network_visualization.py:L22` | PASS |
| `start_ui` | sync fn | SKILL.md:L169 | matches (8 params incl. required `pid_callback`) | `cognee/api/v1/ui/ui.py:L369` | PASS |
| `session` | module | SKILL.md:L141 · ref:L259 | 3 async fns with signatures | `cognee/api/v1/session/session.py:L1` | PASS |
| `pipelines` | module | SKILL.md:L139 · ref:L198 | Task/run_tasks/run_tasks_parallel/run_pipeline signatures | `cognee/modules/pipelines/__init__.py:L1` | PASS |
| `Drop` | sentinel | SKILL.md:L140,L204 | matches (singleton `_Drop()`, `bool(Drop) is False`) | `cognee/pipelines/types.py:L32` | PASS |
| `run_startup_migrations` | async fn | SKILL.md:L142,L164 | documented in SKILL.md; **references/full-api-reference.md §Migrations does not document the public export** (see GAP-001) | `cognee/run_migrations.py:L80` | WARN |
| `remember` | async fn | SKILL.md:L149 | matches (2 positional + 8 keyword-only + `**kwargs: Unpack[RememberKwargs]`) | `cognee/api/v1/remember/remember.py:L339` | PASS |
| `RememberResult` | class | SKILL.md:L150,L208 | matches (status values + 7 attrs) | `cognee/api/v1/remember/remember.py:L139` | PASS |
| `recall` | async fn | SKILL.md:L151 | matches (2 positional + 3 keyword-only + `**kwargs: Unpack[RecallKwargs]`) | `cognee/api/v1/recall/recall.py:L122` | PASS |
| `improve` | async fn | SKILL.md:L152 | matches (1 positional + 3 keyword-only + `**kwargs: Unpack[ImproveKwargs]`) | `cognee/api/v1/improve/improve.py:L36` | PASS |
| `forget` | async fn | SKILL.md:L153 | matches (4 keyword-only params) | `cognee/api/v1/forget/forget.py:L15` | PASS |
| `serve` | async fn | SKILL.md:L154 | matches (2 positional + 4 keyword-only) | `cognee/api/v1/serve/serve.py:L17` | PASS |
| `disconnect` | async fn | SKILL.md:L155 | matches (`clear_saved: bool = False`) | `cognee/api/v1/serve/disconnect.py:L8` | PASS |
| `visualize` | async fn (alias) | SKILL.md:L156 | documented as V2 alias for `visualize_graph` | `cognee/api/v1/__init__.py` | PASS |
| `enable_tracing` | sync fn | SKILL.md:L138 · ref:L227 | matches | `cognee/modules/observability/trace_context.py` | PASS |
| `disable_tracing` | sync fn | SKILL.md:L138 · ref:L228 | matches | same file | PASS |
| `get_last_trace` | sync fn | SKILL.md:L138 · ref:L229 | matches | same file | PASS |
| `get_all_traces` | sync fn | SKILL.md:L138 · ref:L230 | matches | same file | PASS |
| `clear_traces` | sync fn | SKILL.md:L138 · ref:L231 | matches | same file | PASS |
| `agent_memory` | decorator | SKILL.md:L157 | matches (8 keyword-only params) | `cognee/modules/agent_memory/decorator.py:L22` | PASS |

### Coverage Summary

- **Exports Found (barrel):** 34
- **Documented in SKILL.md:** 34 (100%)
- **Missing Documentation:** 0
- **Signature Mismatches (SKILL.md body):** 0 — all 34 signatures in the V1/V2 Key API tables, Key Types, and Deprecations sections match the source signatures at the pinned commit.
- **Split-body Inconsistency:** 1 (`run_startup_migrations` — SKILL.md documents the public export correctly; references/full-api-reference.md §Migrations instead describes the internal helper `run_migrations()` at L16. See GAP-001.)
- **Stale Documentation:** 0

### Metadata Export-Count Coherence Cross-Check

**Cluster A (public-barrel surface):**
- `stats.exports_public_api`: 34
- `exports[]` length: 34
- Intra-cluster divergence: 0% → no finding.

**Cluster B (documented surface):**
- `stats.exports_documented`: 34
- Provenance-map entry count: 35 (`cognee/api/v1/visualize/start_visualization_server.py` also lists the submodule-level function `visualization_server` as a separate entry)
- Intra-cluster divergence: 1/35 = 2.86% < 10% → no Medium finding.

**Cross-cluster:** barrel=34 vs documented=35 — 2.94% difference, within 10% → no multi-denominator Info note.

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 100% (34/34) |
| Signature Accuracy | 100% (34/34) — every SKILL.md-body signature matches source exactly |
| Type Coverage | 100% (SearchType 15/15 modes; Task, Drop, RememberResult, DataPoint, 5 Cognee* exceptions all documented) |

Weight application is deferred to step-05.

## Coherence Analysis

**Mode:** naive (basic structural validation; single-source skill with no cross-skill integrations).

### Document Structure

- SKILL.md frontmatter has `name` + `description` (agentskills.io compliant) ✓ (validator output: PASS, 0 issues)
- Required sections present: Overview, Quick Start, Common Workflows, Key API Summary (V1 + V2), Deprecations & Gotchas, Key Types, Architecture at a Glance, CLI ✓
- Code examples are language-annotated (` ```python `) ✓
- No broken markdown (tables close cleanly; 252 lines, no dangling fences) ✓
- No `scripts/` or `assets/` directory alongside SKILL.md → "Scripts & Assets" section not required ✓
- `references/` directory (4 files: config.md, core-workflow.md, full-api-reference.md, pipelines-and-datapoints.md) linked from the footer (L252) ✓

### Internal Consistency

- Every export name referenced in Quick Start / Common Workflows examples resolves to an entry in Key API tables or Deprecations section (20 names checked) ✓
- SearchType modes referenced (15 total) match source enum exactly (verified against `cognee/modules/search/types/SearchType.py`) ✓
- Async/sync annotations consistent: V1/V2 workflow fns documented as async; `start_ui`, `start_visualization_server.visualization_server`, and tracing fns explicitly called out as sync ✓
- Quick Start example signatures align with Key API Summary (no self-contradictions) ✓
- All `[AST:...]` line citations for V1/V2 core functions verified against source (see spot-check below)

### Line-Citation Spot-Check (Deep tier, local source)

| Citation | File | Observed line | Source line | Match |
|---|---|---|---|---|
| `[AST:cognee/api/v1/add/add.py:L22]` | SKILL.md:L127, ref:L51 | L22 | `async def add(` @ L22 | ✓ |
| `[AST:cognee/api/v1/cognify/cognify.py:L44]` | SKILL.md:L128, ref:L79 | L44 | `async def cognify(` @ L44 | ✓ |
| `[AST:cognee/api/v1/search/search.py:L27]` | SKILL.md:L81,L129, ref:L118, core-workflow:L199 | L27 | `async def search(` @ L27 | ✓ |
| `[AST:cognee/modules/memify/memify.py:L25]` | SKILL.md:L130 | L25 | `async def memify(` @ L25 | ✓ |
| `[AST:cognee/api/v1/update/update.py:L12]` | SKILL.md:L131 | L12 | `async def update(` @ L12 | ✓ |
| `[AST:cognee/api/v1/remember/remember.py:L339]` | SKILL.md:L149 | L339 | `async def remember(` @ L339 | ✓ |
| `[AST:cognee/api/v1/recall/recall.py:L122]` | SKILL.md:L151 | L122 | `async def recall(` @ L122 | ✓ |
| `[AST:cognee/api/v1/improve/improve.py:L36]` | SKILL.md:L152 | L36 | `async def improve(` @ L36 | ✓ |
| `[AST:cognee/api/v1/forget/forget.py:L15]` | SKILL.md:L153 | L15 | `async def forget(` @ L15 | ✓ |
| `[AST:cognee/api/v1/serve/serve.py:L17]` | SKILL.md:L154 | L17 | `async def serve(` @ L17 | ✓ |
| `[AST:cognee/api/v1/serve/disconnect.py:L8]` | SKILL.md:L155 | L8 | `async def disconnect(` @ L8 | ✓ |
| `[AST:cognee/modules/agent_memory/decorator.py:L22]` | SKILL.md:L157 | L22 | `def agent_memory(` @ L22 | ✓ |
| `[AST:cognee/api/v1/ui/ui.py:L369]` | SKILL.md:L169 | L369 | `def start_ui(` @ L369 | ✓ |
| `[AST:cognee/run_migrations.py:L80]` | SKILL.md:L142,L164 | L80 | `async def run_startup_migrations(` @ L80 | ✓ |

All 14 spot-checked citations are on their exact source line. The previous test run's GAP-001/002 (line drifts on `add` and `search` citations) were repaired in the last gap-driven update and no longer reproduce.

### Split-Body Consistency (SKILL.md vs references/)

- `run_startup_migrations` — **mismatch** (see GAP-001): SKILL.md body documents the public export `run_startup_migrations` (L142, L164). references/full-api-reference.md §Migrations (L268-L274) instead documents the internal `run_migrations()` function at L16 under a section header `### Migrations — cognee.run_migrations` and a TOC anchor `#migrations--cogneerun_migrations`. `cognee.run_migrations` is **not** in `cognee/__init__.py` — the top-level export is `run_startup_migrations` which wraps the internal helper. The reference file's navigation therefore advertises an export that does not exist while omitting the one that does.
- All other core functions (`add`, `cognify`, `search`, `memify`, `update`, visualization, datasets, config, prune, pipelines, sessions) have signatures in both SKILL.md and references/ that agree param-for-param and on return types.

### Section 4b Migration/Deprecation Gate (Deep tier, evidence-report.md present)

- **T2-future annotation count in `evidence-report.md`:** 0 — evidence-report enumerates past updates (v0.5.8 → v1.0.0 export changes) only; no forward-looking T2-future annotations were produced.
- **Section 4b present in SKILL.md:** yes — "Deprecations & Gotchas" at SKILL.md L159 serves the Section 4b role.
- **Content classification:** Mixed.
  - Historical-migration (load-bearing for training-data drift): `cognee.low_level` no-longer-exported, `run_migrations` → `run_startup_migrations` cutover, `cognee.delete` deprecation since v0.3.9, `cognee.pipelines` package restructure.
  - Current-state signature gotchas: `agent_memory` must wrap async, `serve()` Auth0 Device Code Flow, `start_ui` is sync with required `pid_callback`, `start_visualization_server` is a module.
- **Gate verdict:** **Info** severity per rule (a) — historical migration content dominates and remains load-bearing for correcting model knowledge. No action required; optional future revision could move the four current-state gotchas inline to the Full API Reference entries for each function.

### Coherence Summary

- Structural issues: 1 Medium (GAP-001, split-body inconsistency on `run_startup_migrations`).
- No Low-severity line-citation drifts (previously reported GAP-001/002 repaired in prior update cycle).
- Coherence category is not scored in naive mode (weight redistributed to coverage + signature + type + external).

## External Validation

### skill-check (npx skill-check check)

- **Available:** yes
- **Status:** PASS
- **Quality Score:** 100/100
- **Errors:** 0 · **Warnings:** 0 · **Diagnostics:** 0
- **Files flagged:** 0
- **Security scan:** 0 findings (agent-scan / mcp-scan via uvx)
- Runtime: ~4.2s

### tessl (npx tessl skill review)

- **Available:** yes
- **Validation Checks:** PASSED (0 errors, 0 warnings; 11/11 checks passed)
- **Description Score:** 100% (specificity 3/3, trigger_term_quality 3/3, completeness 3/3, distinctiveness 3/3)
- **Content Score:** 50% (conciseness 1/3, actionability 3/3, workflow_clarity 2/3, progressive_disclosure 2/3)
- **Review Score:** 80%
- **Suggestions (advisory, not acted on):**
  - Move full V1/V2 API tables into `references/full-api-reference.md`; keep only 5-6 essential fns inline. *Note: SKILL.md already links to the full-api-reference.md and keeps the inline tables intentionally per skf authoring (Tier 1 summary with Tier 2 progressive disclosure). Do not act without re-evaluating the tier boundary.*
  - Move Key Types (SearchType, Task, Drop, RememberResult, DataPoint, Exceptions) into a reference file — *same caveat*.
  - Add validation/error-handling steps: check `RememberResult.status` after `remember()`, handle `CogneeApiError` in try/except, verify `cognify` completion before `search`.
  - Trim Overview/Architecture paragraph — Claude already knows what a vector store / graph store / three-layer architecture is.

### Combined External Score

- **External Validation Score:** 90.0% = (skill-check 100 + tessl review 80) / 2
- **Tools used:** skill-check, tessl

## Completeness Score

### Score Breakdown

| Category | Score | Weight | Weighted |
|----------|-------|--------|----------|
| Export Coverage | 100% | 45% | 45.00 |
| Signature Accuracy | 100% | 25% | 25.00 |
| Type Coverage | 100% | 20% | 20.00 |
| Coherence | n/a (naive) | 0% | 0.00 |
| External Validation | 90% | 10% | 9.00 |
| **Total** | | **100%** | **99.00%** |

### Result

- **Score:** 99.00%
- **Threshold:** 80%
- **Result:** **PASS**

**Weight Distribution:** naive (coherence weight redistributed across coverage/signature/type/external).
**Tier Adjustment:** none — Deep tier with AST-backed signature and type coverage scoring.
**External Validators:** both available (skill-check 100/100 + tessl review 80%).
**Analysis Confidence:** full (local git working tree at pinned commit `3c048aa4`, HEAD match verified).

## Gap Report

**Summary:** 2 findings (0 Critical · 0 High · 1 Medium · 0 Low · 1 Info). No blocking issues. PASS.

### Medium

**GAP-001** — `references/full-api-reference.md` §Migrations documents non-exported internal `run_migrations()` instead of the public `run_startup_migrations()` export

- **Location:** `skills/oms-cognee/1.0.0/oms-cognee/references/full-api-reference.md:21` (TOC anchor `#migrations--cogneerun_migrations`), `L268-L274` (section header `### Migrations — cognee.run_migrations` + signature block `async def run_migrations()` + description citing `[AST:cognee/run_migrations.py:L16]`).
- **Observed:** Reference file's Migrations section describes `cognee.run_migrations()` — an internal helper at `cognee/run_migrations.py:L16`. `cognee.run_migrations` is **not** in the `cognee/__init__.py` barrel.
- **Expected:** The public export is `cognee.run_startup_migrations()` at `cognee/run_migrations.py:L80`, which internally calls `run_migrations()` after applying vector schema migrations. SKILL.md body (L142, L164) correctly documents this. The reference file should lead with `run_startup_migrations` (matching the barrel) and footnote the internal `run_migrations` helper rather than vice versa.
- **Impact:** Readers landing on `#migrations--cogneerun_migrations` from the TOC see a public-API-style signature for a non-exported function. They may then try `import cognee; cognee.run_migrations()` and hit `AttributeError`. SKILL.md's Deprecations section (L164) catches the happy path ("`cognee.run_migrations` is no longer exported — replaced by `cognee.run_startup_migrations()`"), so the consequence is limited to a confusing reference page, not a broken workflow — hence Medium rather than High.
- **Remediation:**
  1. Rename TOC entry on L21: `- [Migrations](#migrations--cogneerun_startup_migrations)` and update the corresponding section heading on L268 to `### Migrations — cognee.run_startup_migrations`.
  2. Replace the signature block on L270-L272 with the public export:

     ```python
     async def run_startup_migrations()
     ```

     Provenance: `[AST:cognee/run_migrations.py:L80]`.
  3. Keep the one-paragraph description of the Alembic subprocess mechanics but clarify that `run_startup_migrations` wraps both `run_migrations()` (relational / Alembic) and the vector-engine migration step — cite the internal helper at `[AST:cognee/run_migrations.py:L16]` as a footnote.
- **Effort:** ~5 min (targeted edit to 3 lines + 1 paragraph; no source change needed).
- **Classification:** Medium severity — split-body inconsistency between SKILL.md body (correct) and reference file (stale). Not a source-signature mismatch (both documented signatures are technically real), but the reference file's public-facing navigation advertises a non-exported symbol.

### Info

**GAP-002** — "Deprecations & Gotchas" section mixes historical migration with current-state gotchas

- **Location:** `skills/oms-cognee/1.0.0/oms-cognee/SKILL.md:159-172`
- **Observed:** Section contains 4 historical-migration entries (low_level removal, run_migrations → run_startup_migrations cutover, delete deprecation, pipelines restructure) alongside 4 current-state signature gotchas (agent_memory async requirement, serve() Auth0 trigger, start_ui sync, start_visualization_server is a module).
- **Rule:** skf authoring scope for Section 4b (Migration & Deprecation Warnings) is forward-looking breaking changes only; current-state signature gotchas should live inline with the function in Full API Reference.
- **Gate verdict:** Info (rule-(a) historical-migration exception — training-data-drift correction is load-bearing).
- **Remediation (optional, not required to export):** In a future revision, move the four current-state gotchas to inline notes under their respective full-api-reference.md entries and consider renaming the SKILL.md section to "Import Corrections & Ecosystem Notes" to free "Migration & Deprecation Warnings" for its forward-looking contract.
- **Effort:** ~15 min if addressed.

### Discovery Quality

**Description optimization:** tessl `description_score` = 100% (specificity 3/3, trigger_term_quality 3/3, completeness 3/3, distinctiveness 3/3). No description improvements needed — the description already uses concrete trigger terms ("knowledge graph", "memory", "cognify", "remember", "search", "RAG"), third-person voice, explicit "Use when..." clause, and a "Do NOT use for" negative-trigger list that references alternatives (cognee-mcp, FastAPI server).

**Discovery testing recommended before export.** Test the skill with 3-5 realistic prompts phrased the way real users actually talk — casual language, typos, incomplete context, and implicit references. A skill tested only with clean prompts may fail to trigger in production. Suggested prompt patterns for this skill:

- Vague: "can you help me set up cognee memory for my agent"
- Implicit: "how do i make my llm remember what i told it yesterday"
- Abbreviated: "run cognee remember on these docs and then recall"
- Mixed: "upgrade cognee 0.5 code to v1 — what changed with run_migrations"
- Typo-laden: "need grpah memroy for ai agent, using congee"

### Remediation Summary

| Severity | Count | Blocking? | Total effort |
|---|---|---|---|
| Critical | 0 | — | — |
| High | 0 | — | — |
| Medium | 1 | No (score 99% ≥ 80% threshold) | ~5 min |
| Low | 0 | — | — |
| Info | 1 | No | Optional (~15 min) |

**Net blockers:** 0. Skill passes the 80% threshold at 99.00% and is ready to export. GAP-001 is a references-file polish item — can be folded into the next `update-skill` run without blocking export. GAP-002 is an authoring-style preference with no user-visible impact.

**Recommended next workflow:** `export-skill` (optionally preceded by a targeted `update-skill --gap GAP-001` to clean up the references §Migrations section).
