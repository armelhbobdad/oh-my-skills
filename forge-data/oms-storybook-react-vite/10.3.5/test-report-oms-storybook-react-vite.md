---
workflowType: 'test-skill'
skillName: 'oms-storybook-react-vite'
skillDir: 'skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite'
testMode: 'naive'
forgeTier: 'Deep'
testResult: 'fail'
score: '79.68%'
threshold: '80%'
analysisConfidence: 'full'
testDate: '2026-04-11'
stepsCompleted: ['step-01-init', 'step-02-detect-mode', 'step-03-coverage-check', 'step-04-coherence-check', 'step-04b-external-validators', 'step-05-score', 'step-06-report']
nextWorkflow: 'update-skill'
---

# Test Report: oms-storybook-react-vite

## Test Summary

**Skill:** oms-storybook-react-vite
**Test Mode:** naive
**Forge Tier:** Deep

**Mode Rationale:** `skill_type` is `single` in metadata.json — this is an individual skill wrapping the Storybook v10 public API surface. No stack cross-references to validate.

**Analysis Plan:**
- Coverage Check: Compare documented exports vs source API surface via AST analysis of source repo at v10.3.5 (e486d382). Tier=Deep enables full AST + QMD lookups.
- Coherence Check: Basic structural validation only — SKILL.md ↔ references file coherence, no cross-skill integration patterns.

## Coverage Analysis

**Tier:** Deep (ast-grep + gh + QMD)
**Source Access:** full (State 1 — local clone + provenance-map)
**Source Path:** /home/armel/.skf/workspace/repos/github.com/storybookjs/storybook @ v10.3.5 (e486d382)
**Files Analyzed:** 25 storybook subpath entry files + 7 framework/renderer/builder/addon entry files
**Denominator:** stratified (scope.include live re-derivation, 32 entry files matched, 301 unique exports union)

### Denominator Derivation

`metadata.json.stats.effective_denominator` is absent, so the denominator was live-re-derived from the brief's `scope.include` globs per source-access-protocol.md §Stratified-scope monorepo packages.

| Package (scope.include glob) | Entry file(s) | Unique exports |
|------------------------------|---------------|----------------|
| `storybook` / code/core/** | 25 subpath barrels (from code/core/package.json exports) | 249 |
| `@storybook/react-vite` / code/frameworks/react-vite/** | node/index.ts + preset.ts | 4 |
| `@storybook/builder-vite` / code/builders/builder-vite/** | src/index.ts | 5 |
| `@storybook/react` / code/renderers/react/** | index.ts + preview.tsx + playwright.ts | 11 |
| `@storybook/addon-a11y` / code/addons/a11y/** | index.ts + preview.tsx | 5 |
| `@storybook/addon-docs` / code/addons/docs/** | 7 entry files (angular/ember/web-components/mdx shims) | 6 |
| `@storybook/addon-themes` / code/addons/themes/** | index.ts + preview.ts | 1 (dedup with core) |
| `@storybook/addon-vitest` / code/addons/vitest/** | index.ts + constants.ts + vitest-plugin/ | 23 |
| **Cross-package dedup** | `build`, `initialGlobals`, `parameters` appear in 2+ packages | −3 |
| **Total union** |  | **301** |

**Discrepancy vs metadata.json:** metadata reports `exports_public_api: 430` and `exports_documented: 320` (74.42%), but its `exports[]` array lists only 82 names. The stats counts appear to be aggregated across multiple extraction passes and disagree with both the live re-derivation (301) and the provenance-map entry count (222). This is a **metadata drift gap** flagged in the report.

### Provenance-Map Baseline Cross-Reference

Provenance-map entries: **222** (all T1, AST-verified at compile time, generated 2026-04-11T17:50Z).
- After canonicalizing disambiguator suffixes (`_exact`, `_def`, `a11y_*`, `themes_*`): **216 unique names**
- Gap vs stratified re-derivation: **301 − 216 = 85 source exports not captured by provenance-map** (primarily `code/core/src/components/**` UI primitives and `code/core/src/babel|csf-tools|core-server|preview-api/internal/*` infrastructure).

### Documentation Check (provenance-map vs skill docs)

Whole-word match of each canonicalized provenance name against SKILL.md + references/*.md:

- **Documented:** 215/216 (99.5%)
- **Missing:** 1 — `ThemesGlobalsInterface` (interface from `@storybook/addon-themes`, extracted but not documented in references/addons.md)

### Signature Spot-Check (12-sample AST verification)

Deep-tier rigorous AST re-parse and signature diff on 12 representative exports:

| # | Name | Kind | Status | Issue |
|---|------|------|--------|-------|
| 1 | `Meta` | type | match | — |
| 2 | `StoryObj` | type | match | — |
| 3 | `composeStories` | function | **partial** | Generic constraint documented as `{ default: Meta }` but source uses `Store_CSFExports<ReactRenderer, any>`; return-type `Omit` uses differing key |
| 4 | `fn` | function | match | — |
| 5 | `expect` | const | match | — |
| 6 | `useArgs` | hook | match | — |
| 7 | `defineMain` | function | **partial** | Listed in SKILL.md but no parameter/return documentation in references/framework-config.md |
| 8 | `create` (theming) | function | match | — |
| 9 | `within` | function | match | — |
| 10 | `HIGHLIGHT` | const | match | — |
| 11 | `Canvas` (doc-block) | component | **partial** | Listed in references/doc-blocks.md but CanvasProps interface (of, meta, sourceState, layout, source, story) not documented |
| 12 | `withThemeByClassName` | decorator | match | — |

**Sample signature match rate:** 9/12 = **75.0%** strict match. Treating partials as half-credit: (9 + 3·0.5)/12 = **87.5%** lenient.

### Type Coverage

Provenance-map type/interface entries: 60 type aliases + 37 interfaces = **97 types**. Of those, 96 are documented and 1 missing (`ThemesGlobalsInterface`) → **99.0%** type coverage within provenance scope.

Note: This denominator is the provenance-map type surface, not the full stratified type surface. The 85-entry gap between stratified re-derivation (301) and provenance-map (216) likely contains additional type aliases and interfaces (e.g., from `code/core/src/types/` or `code/core/src/components/*` props types) that were not captured in provenance-map and therefore cannot be scored against.

### Coverage Summary

- **Source exports (stratified union):** 301
- **Documented:** 215 (71.4%)
- **Undocumented, in provenance-map:** 1 (`ThemesGlobalsInterface`)
- **Undocumented, not in provenance-map (compile-time extraction gap):** 85
- **Signature mismatches (sample):** 0 full, 3 partial / 12 sampled
- **Stale documentation:** 0 (no SKILL.md entries for symbols absent from source)

### Category Scores (tier-adjusted, deferred weighting)

| Category | Raw Score | Notes |
|----------|-----------|-------|
| Export Coverage | 71.4% | 215/301 stratified denominator |
| Signature Accuracy | 75.0% (strict) / 87.5% (lenient) | 9 full + 3 partial matches / 12 sampled |
| Type Coverage | 99.0% | 96/97 within provenance scope; stratified gap unquantifiable |

Note: Weight application deferred to step-05 after external validation availability is known.

## Coherence Analysis

**Mode:** naive (basic structural validation only)

### Document Structure

| Check | Result |
|-------|--------|
| Frontmatter present and valid | PASS (0 issues from skf-validate-frontmatter.py) |
| Required sections (Overview, Quick Start, usage, API summary, types) | PASS — all present |
| Code blocks have language annotations | PASS — all 6 fenced blocks are ` ```tsx `, ` ```ts `, or ` ```bash ` |
| No malformed tables / unclosed code blocks | PASS |
| `scripts/` or `assets/` directory alongside SKILL.md | N/A — no script/asset directories exist (consistent with `metadata.json.stats.scripts_count: 0`, `assets_count: 0`) |
| Split-body references (`references/*.md`) referenced from SKILL.md Tier 2 | PASS — Full API Reference, Full Type Definitions, and Full Integration Patterns sections point to `references/core-api.md`, `references/story-types.md`, `references/doc-blocks.md`, `references/addons.md`, `references/framework-config.md`, `references/csf3-patterns.md` |
| Manual-preservation markers (`<!-- [MANUAL:...] -->`) preserved | PASS — 3 markers present and paired |

### Internal Consistency

- Code examples use symbols that appear in the exports table (Key API Summary): `Meta`, `StoryObj`, `fn`, `expect`, `userEvent`, `withThemeByClassName`, `useArgs`, `composeStories`, `Canvas`, `Controls`, `Primary`, `Stories` — all matched ✓
- Import-path claims in examples match Key API Summary table:
  - `import type { Meta, StoryObj } from '@storybook/react-vite'` ↔ table row 1 ✓
  - `import { fn, expect } from 'storybook/test'` ↔ table row 3 ✓
  - `import { withThemeByClassName } from '@storybook/addon-themes'` ↔ table row 13 ✓
  - `import { useState, useArgs, useParameter } from 'storybook/preview-api'` ↔ table row 4 ✓
- CSF3 syntax consistent (satisfies Meta, named-export stories, no default-export arrays)
- Layer model (framework → renderer + builder) stated consistently in Overview, Key API Summary notes, and Architecture at a Glance

### Cross-Split-Body Consistency

Subagent inventory Section 1b cross-check returned **0 mismatches** — no signature contradictions between SKILL.md body and references/*.md for symbols documented in both locations.

### Section 4b (Migration & Deprecation Warnings) Gate

**Gate conditions:**
- Forge tier: **Deep** ✓
- `evidence-report.md` exists: ✓ (`forge-data/oms-storybook-react-vite/10.3.5/evidence-report.md`)

**T2-future annotations from evidence-report.md line 52:**
> `T2-future: 0 (no deprecation warnings or planned renames surfaced in the 100-issue/100-PR window)`

**SKILL.md Section 4b status:** PRESENT — titled **"Import Surface Corrections & Recent Changes"** (SKILL.md:148–160).

**Content classification:** The section's own scope paragraph states: *"this section is not a Storybook changelog — it captures the v10 consolidation that persists as a training-data defect plus a handful of load-bearing recent fixes. There are no forward-looking deprecations announced for v10.3.5 (nothing scheduled to break in v11 yet at the time of extraction)."*

The section documents:
1. v10 package consolidation (`@storybook/test` → `storybook/test`, `@storybook/preview-api` → `storybook/preview-api`, etc.) — a **shipped** rename that remains load-bearing for correcting training-data drift
2. PR #28907 (`setProjectAnnotations` expanded) — already shipped
3. PR #34408 (v10.3.5 `docs.componentManifest` default change) — already shipped
4. PR #34203 (v10.3.4 a11y timer fix) — already shipped

All four entries are **historical migration** content: completed package renames and shipped API cutovers, no forward-looking breaking changes. Pattern match: citations to shipped PR IDs, old-name → new-name rewrites, "consolidated into the single `storybook` package" language. This matches the Info-severity exception in step-04 §2b exactly.

**Classification:** T2-future = 0 AND Section 4b present AND content is historical migration → **Info severity** (not Medium). Gap report will recommend renaming Section 4b to "Import Corrections" or "Ecosystem Notes" in a future revision to free the Migration & Deprecation heading for its forward-looking contract.

### Structural Issues

None found. One Info-severity observation (Section 4b heading rename recommendation, above).

### Category Score

Coherence category is **not scored in naive mode** — weight is redistributed to Export Coverage, Signature Accuracy, and Type Coverage per scoring-rules.md naive-mode redistribution table.

## External Validation

**Cache staleness check:** evidence-report.md internal `## Validation Results` section is from the original create-skill run at 2026-04-11T17:50:00Z (tessl review 89%, content 73%). Current SKILL.md was regenerated by update-skill at 2026-04-11T19:50:00Z (gap-driven remediation). Cached results are stale — re-ran both validators fresh.

### skill-check

- **Available:** yes (v0.75.0)
- **Quality Score:** 100/100
- **Errors:** 0
- **Warnings:** 0
- **Breakdown:** frontmatter 30, description 30, body 20, links 10, file 10
- **Diagnostics:** none

### tessl

- **Available:** yes (v0.75.0)
- **Validation:** PASSED (0 errors, 0 warnings across 11 structural checks)
- **Description Score:** 100%
- **Content Score:** 50% — **regression from 73% pre-update** (see warning below)
- **Review Score:** 80% (down from 89% pre-update)

**Judge breakdown:**
- Description: specificity 3/3, trigger_term_quality 3/3, completeness 3/3, distinctiveness_conflict_risk 3/3
- Content: conciseness **1/3**, actionability 3/3, workflow_clarity 2/3, progressive_disclosure 2/3

**Top suggestions:**
- Move the full API import table to `references/core-api.md` and keep only the 3–4 most load-bearing import corrections inline (e.g., `@storybook/test` → `storybook/test`)
- Shorten the Architecture at a Glance section; move layer-model detail to a reference file with a 2-line summary inline
- Collapse Key Types to the Meta/StoryObj/Preview signatures needed for the quick-start; move full types to `references/story-types.md`
- Add an explicit post-write verification step to workflows (e.g., "Run `npm run storybook` and confirm the story renders without console errors")

**⚠ Content quality warning:** tessl content scored 50% (below the 70% threshold). Unlike a typical post-split-body drop, the root cause here is **inline verbosity, not content absence**: update-skill's gap-driven remediation added more inline content (Key API Summary table, Key Types section, Architecture at a Glance) to recover Export Coverage, which the conciseness judge penalized at 1/3. This is a rescoping opportunity — move the API table and type signatures out to references/ while keeping SKILL.md body lean, and the score will recover. Review score remains 80% because actionability (3/3) and description (100%) compensate.

### Combined External Score

- **External Validation Score:** (100 + 80) / 2 = **90.0%**
- **Tools used:** skill-check, tessl

## Completeness Score

### Scoring Inputs

```json
{
  "mode": "naive",
  "tier": "Deep",
  "docsOnly": false,
  "state2": false,
  "scores": {
    "exportCoverage": 71.4,
    "signatureAccuracy": 75.0,
    "typeCoverage": 99.0,
    "coherence": null,
    "externalValidation": 90.0
  }
}
```

Signature Accuracy uses **strict** interpretation (full matches only: 9/12 = 75.0%). Lenient interpretation (partials count half: 10.5/12 = 87.5%) is noted for sensitivity analysis below.

### Score Breakdown

| Category | Score | Weight | Weighted |
|----------|-------|--------|----------|
| Export Coverage | 71.4% | 45.0% | 32.13% |
| Signature Accuracy | 75.0% | 25.0% | 18.75% |
| Type Coverage | 99.0% | 20.0% | 19.80% |
| Coherence | N/A (naive) | 0% | 0% |
| External Validation | 90.0% | 10.0% | 9.00% |
| **Total** |  | **100.0%** | **79.68%** |

### Result

**Score:** 79.68%
**Threshold:** 80.0%
**Result:** **FAIL** (narrow — 0.32 points below threshold)

**Weight Distribution:** naive (redistributed — coherence 18% absorbed into coverage 45% + signature 25% + type 20% + external 10%)
**Tier Adjustment:** none (Deep tier — Signature Accuracy and Type Coverage fully scored)
**External Validators:** both available (skill-check + tessl)
**Analysis Confidence:** full (State 1 — local clone + provenance-map)

### Sensitivity Analysis

If signature accuracy used lenient scoring (3 partials as 0.5):
- Signature Accuracy: 87.5% × 25% = 21.88%
- **Total would be 82.81% → PASS**

The pass/fail boundary is driven entirely by whether the 3 partial signature matches (`composeStories`, `defineMain`, `Canvas`) are counted as half-credit or zero. Fixing those 3 signatures in references/ would flip the result with no other changes.

### Access Degradation Notice

Not applicable — analysis confidence is `full` (State 1). No degradation.

## Gap Report

**Total Gaps:** 11
**Blocking (Critical + High):** 2
**Non-blocking (Medium + Low + Info):** 9

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|------------------|
| Critical | 0 | — |
| High | 2 | Fix two partial signature documentations in references/ (composeStories, defineMain) — 15–30 min |
| Medium | 5 | Scope/metadata coherence fixes, missing interface, Canvas props, content-verbosity rescope — 1–3 hours |
| Low | 3 | Workflow-verification step, progressive-disclosure trimming, metadata drift flag — 30 min |
| Info | 1 | Section 4b heading rename recommendation (advisory) — future revision |
| **Total** | **11** | |

---

### GAP-001: `composeStories` generic constraint mismatch

**Severity:** High
**Category:** Coverage (signature accuracy)
**Source:** skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/references/story-types.md:197-200 vs code/renderers/react/src/portable-stories.tsx:148-159

**Issue:** Documented signature shows `composeStories<TModule extends { default: Meta }>(...): Omit<StoriesWithPartialProps<ReactRenderer, TModule>, keyof TModule>`. Real source signature is `composeStories<TModule extends Store_CSFExports<ReactRenderer, any>>(csfExports: TModule, projectAnnotations?: ProjectAnnotations<ReactRenderer>): Omit<StoriesWithPartialProps<ReactRenderer, TModule>, keyof Store_CSFExports>`. The generic constraint (`{ default: Meta }` vs `Store_CSFExports<ReactRenderer, any>`) and the `Omit` key type (`keyof TModule` vs `keyof Store_CSFExports`) both differ. An agent using the skill would write a wrong type annotation when composing stories in Vitest.

**Remediation:** Update references/story-types.md:197-200 to:

```ts
export function composeStories<TModule extends Store_CSFExports<ReactRenderer, any>>(
  csfExports: TModule,
  projectAnnotations?: ProjectAnnotations<ReactRenderer>
): Omit<StoriesWithPartialProps<ReactRenderer, TModule>, keyof Store_CSFExports>
```

Add a 1-line note: "`Store_CSFExports` is the internal CSF module shape — narrows `TModule` to a real story module." Cite `[AST:code/renderers/react/src/portable-stories.tsx:L148]`.

---

### GAP-002: `defineMain` missing parameter/return documentation

**Severity:** High
**Category:** Coverage (signature accuracy)
**Source:** skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/references/framework-config.md vs code/frameworks/react-vite/src/node/index.ts:3-5

**Issue:** `defineMain` is listed as a `@storybook/react-vite` export in references/framework-config.md but no parameter or return-type signature is documented. Real source: `export function defineMain(config: StorybookConfig) { return config; }` — it's a pass-through identity function whose only job is to give `.storybook/main.ts` proper type inference. Without documenting this, an agent may invent a more complex signature or miss the intended usage pattern (wrap your `main.ts` config object in `defineMain({...})` to get autocomplete).

**Remediation:** In references/framework-config.md, add a dedicated entry:

```ts
export function defineMain(config: StorybookConfig): StorybookConfig
// Identity helper — returns config as-is, exists purely to anchor TypeScript
// inference at .storybook/main.ts so autocomplete and type-checking work on
// the framework, addons, and viteFinal fields.
//
// Usage: export default defineMain({ framework: '@storybook/react-vite', ... })
```

Cite `[AST:code/frameworks/react-vite/src/node/index.ts:L3]`.

---

### GAP-003: `Canvas` doc-block props interface undocumented

**Severity:** Medium
**Category:** Coverage (type coverage)
**Source:** skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/references/doc-blocks.md vs code/addons/docs/src/blocks/blocks/Canvas.tsx:100

**Issue:** `Canvas` is listed as an MDX doc-block component but its props interface is not documented. Real source exposes these props (from the `CanvasProps` type in `code/addons/docs/src/blocks/blocks/Canvas.tsx`): `of?: ModuleExport`, `meta?: ModuleExports`, `sourceState?: 'hidden' | 'shown' | 'none'`, `layout?: Layout`, `source?: Omit<SourceProps, 'dark'>`, `story?: Pick<StoryProps, 'inline' | 'height' | 'autoplay' | '__forceInitialArgs' | '__primary'>`, `withToolbar?: boolean`, `additionalActions?: ActionItem[]`, `className?: string`. Without these, an agent cannot correctly wire `<Canvas of={ButtonStories.Secondary} sourceState="shown" />`.

**Remediation:** Add a "Canvas props" subsection in references/doc-blocks.md alongside the Canvas entry listing each prop with its type and purpose. At minimum document `of`, `meta`, `sourceState`, `layout`, `story` (the five load-bearing props for authors). Cite `[AST:code/addons/docs/src/blocks/blocks/Canvas.tsx:L100]`.

---

### GAP-004: `ThemesGlobalsInterface` interface not documented

**Severity:** Medium
**Category:** Coverage (missing interface)
**Source:** skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/references/addons.md

**Issue:** The provenance-map includes `ThemesGlobalsInterface` (extracted T1 AST from `@storybook/addon-themes`) but this interface is not mentioned anywhere in SKILL.md or references/. It is the one and only provenance-map entry that failed the documentation cross-check (215/216 documented).

**Remediation:** Add a brief entry to references/addons.md in the `@storybook/addon-themes` section documenting `ThemesGlobalsInterface`. If the interface is a private implementation detail (e.g., internal globals shape for the addon's own state), note it explicitly as "internal — not imported by story authors" so the skill's reader understands why it exists in exports but isn't in the authoring surface. If it is authoring-surface, document the fields. Cite the source file via ast-grep.

---

### GAP-005: Scope denominator discrepancy (stratified 301 vs provenance-map 216)

**Severity:** Medium
**Category:** Coverage (extraction/scope coherence)
**Source:** forge-data/oms-storybook-react-vite/10.3.5/provenance-map.json (216 unique canonicalized) vs skill brief scope.include live re-derivation (301 unique)

**Issue:** The brief's `scope.include` globs match 301 unique source exports at test time, but the provenance-map only captures 216. The 85-entry gap primarily consists of `code/core/src/components/**` UI primitives (86 exports — `Badge`, `Bar`, `Blockquote`, `ActionBar`, etc.) and `code/core/src/babel|csf-tools|core-server/internal/*` build/server infrastructure. Per the brief's own notes ("Scope assumption — authoring, not installing. day-90+ story author, not day-1 installer"), these exports are not authoring surface and should be out of scope. But because the scope.include glob `code/core/**` is coarse-grained, the live re-derivation pulls them in and inflates the denominator to 301 — dragging Export Coverage from 99.5% (215/216 on the authoring-surface) down to 71.4% (215/301 on the coarse-glob-surface).

**Remediation:** Two complementary fixes, pick one:

1. **Narrow `scope.include` in `forge-data/oms-storybook-react-vite/skill-brief.yaml`** to exclude build/internal surfaces explicitly:
   ```yaml
   exclude:
     - "code/core/src/components/**"    # UI primitives for addon panels, not authoring
     - "code/core/src/babel/**"
     - "code/core/src/csf-tools/**"
     - "code/core/src/core-server/**"
     - "code/core/src/router/**"
     - "code/core/src/node-logger/**"
   ```
   Then re-run update-skill to regenerate metadata.json with the corrected denominator.

2. **Populate `metadata.json.stats.effective_denominator`** directly (if the skill-creator workflow's step-05 §4 supports it) so downstream test runs use 216 rather than re-deriving 301.

Either fix will flip Export Coverage from 71.4% to ~99% and drive the total score well above threshold.

---

### GAP-006: metadata.json internal inconsistency

**Severity:** Medium
**Category:** Structural / metadata coherence
**Source:** skills/oms-storybook-react-vite/10.3.5/oms-storybook-react-vite/metadata.json

**Issue:** metadata.json reports `stats.exports_public_api: 430`, `stats.exports_documented: 320`, `stats.public_api_coverage: 0.7442` — but the `exports[]` array contains only 82 names. Three different counts for "what's in this skill":
- `exports[]` array length: 82
- `stats.exports_documented`: 320
- `stats.exports_public_api`: 430
- Provenance-map entries: 222
- Live stratified re-derivation: 301

No single source of truth. Downstream workflows (audit, update, health-check) cannot reliably answer "how many exports does this skill document?"

**Remediation:** The create-skill step-05 §4 (metadata writer) should be updated so that either (a) `exports[]` contains the full list of documented symbols (matching `exports_documented`), or (b) the stats counts are derived from and match `exports[]` length. Recommendation: set `exports[]` to the full canonicalized provenance-map entry list (216 symbols) and set `stats.exports_documented` + `stats.exports_public_api` to match. Also populate `stats.effective_denominator` explicitly (see GAP-005).

---

### GAP-007: tessl content score regression (73% → 50% post-update)

**Severity:** Medium
**Category:** External validation (content quality)
**Source:** tessl judge output — SKILL.md Key API Summary (L122-142), Key Types (L162-194), Architecture at a Glance (L198-209)

**Issue:** Update-skill's gap-driven remediation added the Key API Summary table, Key Types code block, and Architecture at a Glance section inline in SKILL.md body to recover Export Coverage. This worked for coverage (19% → 71%) but the conciseness judge scored 1/3 and the progressive_disclosure judge scored 2/3 — tessl content dropped from 73% to 50%. SKILL.md is now 241 lines with dense inline API material that duplicates content in references/core-api.md, references/story-types.md, and references/framework-config.md.

**Remediation:**
1. Move the full Key API Summary import table (L126-140) to `references/core-api.md`. Keep only a 3-row inline corrections table in SKILL.md: `@storybook/test → storybook/test`, `@storybook/preview-api → storybook/preview-api`, `@storybook/theming → storybook/theming` (the three corrections that directly address training-data drift — the skill's differentiator).
2. Collapse Key Types (L162-194) to just `Meta`, `StoryObj`, `Preview` (the three the Quick Start example uses). Move `Decorator`, `Loader`, `StoryContext`, `A11yTestMode`, `Framework` to references/story-types.md.
3. Shorten Architecture at a Glance (L198-209) to a single 3-line paragraph: "Layer model: `@storybook/react-vite` (framework) → `@storybook/react` (renderer) + `@storybook/builder-vite` (builder). Story render failures → renderer; Vite HMR failures → builder; `.storybook/main.ts` issues → framework. Full layer composition detail in `references/framework-config.md`." Move the 5-bullet detail to references/framework-config.md.

Target: SKILL.md body ≤ 150 lines after rescope. Expected tessl content improvement: 50% → 70–75%.

---

### GAP-008: No post-write verification step in Common Workflows

**Severity:** Low
**Category:** Structural / workflow clarity
**Source:** SKILL.md:102-120 (Common Workflows section), tessl workflow_clarity judge 2/3

**Issue:** Common Workflows is a flat list of "how to write" patterns with no explicit "how to verify the story you just wrote actually runs." A user following the skill writes code and has no gate telling them when to stop. tessl flagged this as workflow_clarity 2/3.

**Remediation:** Add a final bullet to Common Workflows (SKILL.md:120):

```markdown
**Verify a story after writing it:**
`npm run storybook` → open `http://localhost:6006` → confirm the story renders in the canvas with no console errors → if it has a `play` function, check the Interactions panel shows each step passing. For CI verification: `npm run test-storybook` (requires addon-vitest configured).
```

Cite `[EXT:https://storybook.js.org/docs/writing-tests/test-runner]`.

---

### GAP-009: Progressive-disclosure weight (Tier 1 bloat)

**Severity:** Low
**Category:** External validation (content organization)
**Source:** tessl progressive_disclosure judge 2/3

**Issue:** Three sections in SKILL.md Tier 1 body carry content that should live in Tier 2 reference files: Key API Summary (L122-142), Key Types (L162-194), Architecture at a Glance (L198-209). This overlaps with GAP-007 but from a different angle — the issue here is the *organization* (what belongs in SKILL.md vs references/), not just the *volume*.

**Remediation:** Covered by the rescope plan in GAP-007. This gap is a cross-reference for tracking.

---

### GAP-010: Metadata drift — multiple conflicting export counts

**Severity:** Low (cross-reference for GAP-005 and GAP-006)
**Category:** Structural / metadata

**Issue:** See GAP-005 (denominator) and GAP-006 (metadata.json inconsistency). Listed separately so the health-check surfaces it as a distinct concern: skill workflows downstream from create-skill assume metadata is coherent, and this skill's metadata is self-contradictory.

**Remediation:** Fixed by applying both GAP-005 and GAP-006 remediations.

---

### GAP-011: Section 4b heading scope (historical-migration exception)

**Severity:** Info
**Category:** Coherence (structural naming)
**Source:** SKILL.md:148 ("Import Surface Corrections & Recent Changes" section), evidence-report.md:52 (T2-future: 0)

**Issue:** SKILL.md Section 4b is present but contains historical-migration content (shipped v10 consolidation, shipped PRs #28907, #34408, #34203) rather than forward-looking T2-future breaking changes. Per step-04 §2b, this is the legitimate historical-migration exception and flagged as Info severity — the content is load-bearing for correcting training-data drift even though no forward change is pending. The heading "Import Surface Corrections & Recent Changes" already communicates this scope correctly and avoids the "Migration & Deprecation Warnings" label, so no rename is actually required.

**Remediation:** No action required. Optional future revision: if Storybook v11 announces T2-future deprecations, split this section into "Import Corrections" (historical, load-bearing for training-data drift) and "Upcoming Deprecations" (forward-looking v11 breakers).

---

### Discovery Quality

**Description quality:** tessl scored the description 100% (4/4 across specificity, trigger_term_quality, completeness, distinctiveness_conflict_risk). No optimization needed — the description is an exemplar for third-person voice, specific trigger terms (`*.stories.tsx`, `preview.ts`, `.storybook/main.ts`, `CSF3`, `storybook/test`), and explicit negative triggers ("Do NOT use for first-time project setup, framework selection, or upgrade migration").

**Discovery testing recommended.** Before export, test the skill with 3–5 realistic prompts phrased the way real users actually talk — with casual language, typos, incomplete context, and implicit references. A skill tested only with clean prompts may fail to trigger in production. Example realistic prompt patterns for this skill:

- Vague: *"my button story is throwing some weird react error when i click it"*
- Implicit: *"why is storybook yelling at me about @storybook/test being deprecated"*
- Abbreviated: *"add a play fn to the primary story that clicks and asserts onClick"*
- Mixed concern: *"i'm setting up vitest for my components but composeStories isn't picking up my decorators"*
- Training-data trap: *"import Meta from '@storybook/react'"* — the skill should correct this to `@storybook/react-vite` or note both work but the former is canonical for Vite.

Record this as a final Info-level gap: **GAP-012 (Info): Discovery testing not performed.** Advisory only — does not affect the 79.68% score.


