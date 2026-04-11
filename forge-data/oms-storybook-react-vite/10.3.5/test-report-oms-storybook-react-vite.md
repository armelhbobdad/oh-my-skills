---
workflowType: 'test-skill'
skillName: 'oms-storybook-react-vite'
skillDir: 'skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite'
testMode: 'naive'
forgeTier: 'Deep'
testResult: 'pass'
score: '99.49%'
threshold: '80%'
analysisConfidence: 'full'
testDate: '2026-04-11'
stepsCompleted: ['step-01-init', 'step-02-detect-mode', 'step-03-coverage-check', 'step-04-coherence-check', 'step-04b-external-validators', 'step-05-score', 'step-06-report']
nextWorkflow: 'export-skill'
---

# Test Report: oms-storybook-react-vite

## Test Summary

**Skill:** oms-storybook-react-vite
**Version:** 10.3.5
**Skill Type:** single
**Test Mode:** naive
**Forge Tier:** Deep
**Source:** /home/armel/.skf/workspace/repos/github.com/storybookjs/storybook (v10.3.5, commit e486d382)

**Mode Rationale:** `skill_type` is `single` in metadata.json — this is an individual skill wrapping the Storybook v10 public API surface. No stack cross-references to validate.

**Analysis Plan:**
- Coverage Check: Compare documented exports vs source API surface via AST analysis of source repo at v10.3.5 (e486d382). Tier=Deep enables full AST + QMD lookups.
- Coherence Check: Basic structural validation only — SKILL.md ↔ references file coherence, no cross-skill integration patterns.

Pre-check: SKILL.md frontmatter validation — PASS (0 issues).

## Coverage Analysis

**Tier:** Deep
**Source Access:** full (State 1 — local clone at `source_root`)
**Source Path:** /home/armel/.skf/workspace/repos/github.com/storybookjs/storybook (v10.3.5, e486d382)
**Files Analyzed:** SKILL.md (196 L) + 6 references (262+342+242+197+390+319 = 1,752 L); provenance-map (222 entries) as source-truth baseline
**Denominator:** stratified (effective_denominator: 216 from metadata.json.stats — authoring-surface subset of monorepo after GAP-005 scope narrowing; provenance-map canonicalized to 215 unique bases after folding 7 `_def`/`_exact` provenance-bookkeeping variants)

### Export Coverage

**Approach:** Compared the canonicalized provenance-map public API surface (215 unique base names, derived from 222 raw entries by folding `_def`/`_exact`/`a11y_*` provenance-bookkeeping variants) against the union of named exports documented across SKILL.md and its 6 reference files (338 unique documented names extracted by subagent). `DecoratorHelpers` is credited to docs via prose mention at `references/addons.md:121`.

**Per-library coverage (from provenance-map):**

| Source library | Pmap entries | Canonical | Documented | Missing |
|---|---|---|---|---|
| `@storybook/react` (renderer) | 15 | 15 | 15 | 0 |
| `@storybook/react-vite` (framework) | 3 | 3 | 3 | 0 |
| `@storybook/builder-vite` (builder) | 8 | 8 | 8 | 0 |
| `storybook` (core) | 37 | 37 | 37 | 0 |
| `storybook/preview-api` | 17 | 17 | 17 | 0 |
| `storybook/test` | 7 | 7 | 7 | 0 |
| `storybook/manager-api` | 9 | 9 | 9 | 0 |
| `storybook/viewport` | 5 | 5 | 5 | 0 |
| `storybook/theming` | 10 | 10 | 10 | 0 |
| `storybook/internal/types` | 8 | 8 | 8 | 0 |
| `@storybook/addon-docs` | 19 | 19 | 19 | 0 |
| `@storybook/addon-docs/blocks` | 49 | 49 | 49 | 0 |
| `@storybook/addon-themes` | 18 | 15 (folded) | 15 | 0 |
| `@storybook/addon-a11y` | 10 | 8 (folded) | 8 | 0 |
| `@storybook/addon-a11y/preview` | 4 | 3 (folded) | 3 | 0 |
| `@storybook/addon-vitest` | 3 | 3 | 3 | 0 |
| **TOTAL** | **222** | **215** | **215** | **0** |

### Coverage Summary

- **Exports Found (canonical):** 215 (after folding 7 `_def`/`_exact` and 1 `a11y_` dedup pair)
- **Documented:** 215 (100% of canonical pmap surface)
- **Missing Documentation:** 0
- **Signature Mismatches:** 0 (subagent cross-check between SKILL.md body and references returned `cross_check_mismatches: []`)
- **Stale Documentation (extras):** 127 names documented beyond the 215-entry pmap scope (addon control primitives, manager-api internals, theming subtypes, error classes — all from the same packages but beyond the curated provenance-map authoring subset)

### Citation Density

Total citation tags across the skill package:
- SKILL.md: 16 tags
- references/core-api.md: 92 tags
- references/doc-blocks.md: 44 tags
- references/addons.md: 33 tags
- references/story-types.md: 32 tags
- references/framework-config.md: 17 tags
- references/csf3-patterns.md: 5 tags

**Total: 239 citation tags** — 195 of 215 canonical exports carry at least one `[AST:...]` provenance tag (90.7%). The remainder are types that inherit citations via their containing section header.

### Metadata Drift Cross-Check (Step 3 §4b)

Collected export counts:

| Source | Count |
|---|---|
| `metadata.json.stats.exports_public_api` | 216 |
| `metadata.json.stats.exports_documented` | 216 |
| `metadata.json.exports[]` array length | 82 |
| `provenance-map.json` entry count | 222 |

**Divergence:** `exports[]` (82) vs `stats.exports_public_api` (216) disagree by 62% of the larger count — exceeds the 10% threshold. See Gap Report item **GAP-001** below (Medium severity).

### Category Scores

| Category | Score | Computation |
|----------|-------|-------------|
| Export Coverage | 99.54% | 215 documented / 216 declared denominator (215/215 canonical pmap bases = 100% but metadata stats count is 216, leaving 1 unreconciled) |
| Signature Accuracy | 100% | 0 mismatches in subagent cross-check; all provenance entries T1/`signature_source: T1` |
| Type Coverage | 100% | 97/97 type+interface exports in pmap are documented |

Note: Weight application is deferred to step-05.

## Coherence Analysis

**Mode:** naive (single skill — no cross-skill references, no integration patterns)

### Structural Validation

| Check | Result |
|---|---|
| SKILL.md required top-level sections (Overview, Quick Start, API Reference) | ✓ PASS |
| Section headers properly formatted | ✓ PASS |
| Code fences balanced in SKILL.md | ✓ PASS (10 markers, 5 open + 5 close) |
| Code fences balanced in all 6 reference files | ✓ PASS |
| All SKILL.md code blocks have language annotations | ✓ PASS (5/5 opening fences annotated) |
| Exports used in examples match documented exports | ✓ PASS (0 cross-check mismatches from §3 inventory) |
| `scripts/` or `assets/` directory present | ✗ absent → Section 7b NOT required |
| Skill directory contents match spec | ✓ PASS (SKILL.md, metadata.json, context-snippet.md, references/) |

**Structural issues found:** 0

### Section 4b (Migration & Deprecation Warnings) Verification

- Forge Tier: **Deep** ✓ (gate satisfied)
- `evidence-report.md`: **present** ✓ (gate satisfied)
- T2-future annotation count (per `evidence-report.md:52`): **0** ("no deprecation warnings or planned renames surfaced in the 100-issue/100-PR window")
- Section 4b ("Migration & Deprecation Warnings") in SKILL.md: **absent**

**Rule match:** T2-future = 0 AND Section 4b absent → no rule case matches → no finding. SKILL.md's historical-migration content (`v10 Import Corrections` §4, `Shipped v10.3.x fixes worth knowing` §4.5) is correctly scoped under dedicated headings rather than under a non-existent "Migration & Deprecation Warnings" heading. This aligns with the authoring rule that reserves Section 4b for forward-looking breaking changes.

### Reference Integrity (Subagent §3 Cross-Check)

| Check | Result |
|---|---|
| SKILL.md ↔ reference file signature consistency | ✓ 0 mismatches across 24 SKILL.md exports vs 362 reference exports |
| `[AST:...]` citation targets (sample) | 239 tags across 7 files; canonical types anchor to `code/renderers/react/src/public-types.ts:L29`/`L47`/`L80` — all valid lines in source |
| Split-body coverage (SKILL.md mentions → references) | `storybook/test`, `storybook/preview-api`, `storybook/theming`, `@storybook/addon-{a11y,docs,themes,vitest}` all resolve to reference files with full API tables |

### Coherence Summary

- Naive-mode structural issues: **0**
- Section 4b verification: **skipped** (no rule match)
- Cross-check mismatches: **0**

Coherence category is not separately scored in naive mode — weight redistributes to coverage per `scoring-rules.md`.

## External Validation

Cached results in `evidence-report.md §Validation Results` were flagged **stale** (they reflect the first gap-driven pass; current SKILL.md is post-2nd-pass per `metadata.last_update: 2026-04-11T22:30:00Z`). Fresh run follows.

### skill-check

- **Available:** yes (`npx skill-check check` v0.75.x)
- **Quality Score:** 100/100
- **Errors:** 0
- **Warnings:** 0
- **Diagnostics:** none
- **Breakdown:** frontmatter=30, description=30, body=20, links=10, file=10

### tessl

- **Available:** yes (`npx -y tessl` v0.75.0)
- **Validation:** PASSED (0 errors, 0 warnings)
- **Description Score:** 100%
- **Content Score:** 85% (up from 73% in first-pass validation)
- **Review Score:** 94% (up from 89%)

**Tessl Judge Breakdown:**
- **Description — 100%:** specificity 3/3, trigger_term_quality 3/3, completeness 3/3, distinctiveness_conflict_risk 3/3
- **Content — 85%:** conciseness 2/3, actionability 3/3, workflow_clarity 3/3, progressive_disclosure 3/3

**Suggestions:**
- Remove or consolidate the inline `[AST:...]` and `[QMD:...]` source citations — they consume tokens and are not actionable for Claude when writing stories. A single 'Sources' section or reference file would suffice.
- Trim the `Full Type Definitions` and `Full Integration Patterns` sections in SKILL.md to just the reference-file pointers — current prose restates what the reference files contain without adding new actionable guidance.

### Combined External Score

- **External Validation Score:** **97.0%** = (skill-check 100 + tessl review 94) / 2
- **Tools used:** skill-check, tessl

## Completeness Score

### Score Breakdown

| Category | Score | Weight | Weighted |
|----------|-------|--------|----------|
| Export Coverage | 99.54% | 45% | 44.79% |
| Signature Accuracy | 100.00% | 25% | 25.00% |
| Type Coverage | 100.00% | 20% | 20.00% |
| Coherence | — (naive mode) | 0% | 0.00% |
| External Validation | 97.00% | 10% | 9.70% |
| **Total** | | **100%** | **99.49%** |

### Result

**Score:** **99.49%**
**Threshold:** 80%
**Result:** **PASS**

**Weight Distribution:** naive (coherence weight redistributed across coverage/signature/type/external)
**Tier Adjustment:** none (Deep tier — all categories active)
**External Validators:** both available (skill-check 100, tessl review 94)
**Analysis Confidence:** full (State 1 — local clone at `source_root` + provenance-map cross-reference)

### Delta vs Prior Run

| Metric | 2026-04-11 prior run | Current run | Δ |
|---|---|---|---|
| Test Result | FAIL | **PASS** | ✓ |
| Score | 79.68% | **99.49%** | **+19.81 pp** |
| Export Coverage | 71.43% | 99.54% | +28.11 pp |
| Signature Accuracy | ~85% (est) | 100% | +~15 pp |
| Type Coverage | ~74% (est) | 100% | +~26 pp |
| External Validation | 90.0% | 97.0% | +7.0 pp |
| tessl Content Score | 73% | 85% | +12 pp |
| tessl Review Score | 89% | 94% | +5 pp |

## Gap Report

**Total Gaps:** 5
**Blocking (Critical + High):** 0
**Non-blocking (Medium + Low + Info):** 5

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|-----------------|
| Critical | 0 | — |
| High | 0 | — |
| Medium | 1 | 5 min — update metadata.json stats fields or regenerate from current provenance-map |
| Low | 0 | — |
| Info | 4 | 0–30 min — optional polish + discovery testing advisory |
| **Total** | **5** | |

### GAP-001: Metadata drift — 4 conflicting export counts

**Severity:** Medium
**Category:** Coverage (metadata coherence)
**Source:** `skills/oms-storybook-react-vite/active/oms-storybook-react-vite/metadata.json` + `forge-data/oms-storybook-react-vite/10.3.5/provenance-map.json`

**Issue:** Step 3 §4b metadata-drift cross-check found four export-count sources that disagree beyond the 10% tolerance:

| Source | Count |
|---|---|
| `metadata.json.stats.exports_public_api` | 216 |
| `metadata.json.stats.exports_documented` | 216 |
| `metadata.json.exports[]` array length | **82** |
| `provenance-map.json` entry count | 222 |

`exports[]` (82) disagrees with `stats.exports_public_api` (216) by 62% of the larger count. This is informational about data quality — it does not change the denominator used for this run (216) — but signals that `metadata.json.exports[]` is a curated headline list while `stats` reflects the full authoring surface, and the two are not consistently documented.

**Remediation:** Either (a) rename `metadata.json.exports[]` to `exports_headline[]` and add a `comment` field explaining it's a curated subset of `stats.exports_documented`; or (b) regenerate `exports[]` from the canonicalized provenance-map so both fields agree. Also reconcile the 1-count drift between `stats.effective_denominator` (216) and canonicalized provenance-map bases (215) — one of the 7 `_def`/`_exact` folds is likely double-counted in the stat.

### GAP-002: tessl — trim inline `[AST:...]` / `[QMD:...]` citations

**Severity:** Info
**Category:** Content quality (tessl suggestion)
**Source:** SKILL.md body + all 6 reference files (239 citation tags total)

**Issue:** tessl judge reported conciseness 2/3: "the `[AST:...]` and `[QMD:...]` source citations throughout add significant noise … A single 'Sources' section at the bottom or in a reference file would suffice." Content score improved from 73% → 85% after the first consolidation pass; further consolidation could close the remaining 15 points.

**Remediation:** Consolidate per-line AST citations into end-of-section "Sources:" footers. Aim to keep one provenance tag per distinct source file per section, not per named export. Preserve every distinct source reference — only collapse repetition.

### GAP-003: tessl — trim "Full Type Definitions" / "Full Integration Patterns" prose

**Severity:** Info
**Category:** Content quality (tessl suggestion)
**Source:** `SKILL.md:186-192` (`## Full Type Definitions` + `## Full Integration Patterns`)

**Issue:** tessl judge: "The current prose restates what the reference files contain without adding new actionable guidance." These sections serve as split-body pointers but currently narrate what lives in `references/story-types.md`, `references/framework-config.md`, `references/csf3-patterns.md` instead of just pointing to them.

**Remediation:** Replace each section body with a one-line pointer such as `See references/story-types.md for full generic signatures of Meta<T>, StoryObj<T>, StoryFn<T>, Decorator<T>, Loader<T>, StoryContext<T>, Preview, StorybookConfig.` Preserve the `[MANUAL:additional-notes-reference]` block verbatim.

### GAP-004: Canonical surface count drift — 215 canonical bases vs 216 stated denominator

**Severity:** Info
**Category:** Coverage (metadata precision)
**Source:** `metadata.json.stats.effective_denominator` (216) vs canonicalized provenance-map bases (215)

**Issue:** The stratified-scope resolution in step 3 used `metadata.json.stats.effective_denominator` = 216 as the authoritative count. However, canonicalizing the 222 provenance-map entries (folding 2 `_def` + 5 `_exact` + 3 `a11y_*` prefixed duplicates) yields exactly 215 unique base names, all documented. The 1-count gap is not a missing export — it is a metadata-stat stale value from the GAP-006 reconciliation note (`metadata.json.stats.reconciliation_note`).

**Remediation:** Re-run `skf-update-skill` stats-only pass or manually update `metadata.json.stats.effective_denominator` to 215 to match the canonicalized provenance-map surface. Update `stats.exports_public_api` and `stats.exports_documented` to 215 simultaneously.

### GAP-005: Discovery testing not performed

**Severity:** Info
**Category:** Discovery quality (advisory)
**Source:** test workflow — step 6 §4b

**Issue:** Automated testing cannot validate whether Claude actually triggers this skill on the prompts a real user would type. The description quality is excellent (tessl 100%), but in-vivo discovery testing with 3–5 realistic prompts has not been performed this run.

**Remediation:** Before running `skf-export-skill`, manually test with realistic prompts such as:
- "how do i write a storybook story for this Button component"
- "my preview.ts stopped working after upgrading storybook"
- "csf3 with satisfies — what's the right syntax"
- "why does `import { fn } from '@storybook/test'` fail on v10"
- "add a theme decorator globally to all my stories"

Record any prompts that failed to surface the skill and iterate on the `description` frontmatter.

### Discovery Quality

**Description optimization:** tessl `description_score` = 100% (specificity 3/3, trigger_term_quality 3/3, completeness 3/3, distinctiveness_conflict_risk 3/3). No description changes recommended.

**Discovery testing recommended.** Before export, test the skill with 3-5 realistic prompts phrased the way real users actually talk — with casual language, typos, incomplete context, and implicit references. A skill tested only with clean prompts may fail to trigger in production. Example realistic prompt patterns:
- Vague: "can you help me with these storybook tests that keep flaking"
- Implicit: "why did my play function stop getting called after the upgrade"
- Abbreviated: "storybook v10 correct imports for the test utils"

See GAP-005 for a concrete prompt suite.

---

## Next Step Recommendation

**Score: 99.49% — PASS** (threshold 80%). The 2nd gap-driven repair successfully closed every Critical/High/Medium finding from the prior 79.68% FAIL report. The remaining 5 gaps are all non-blocking (1 Medium informational metadata-drift + 4 Info polish items).

**Recommended next workflow:** `skf-export-skill` — the skill is ready for packaging and distribution. The Medium metadata-drift finding (GAP-001) is informational and can be resolved in a follow-up stats reconciliation pass without re-running the test.

