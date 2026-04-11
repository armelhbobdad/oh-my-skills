---
workflowType: 'test-skill'
skillName: 'oms-storybook-react-vite'
skillDir: 'skills/oms-storybook-react-vite/active/oms-storybook-react-vite'
testMode: 'naive'
forgeTier: 'Deep'
testResult: 'fail'
score: '63.84%'
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

**Mode Rationale:** metadata.json declares `skill_type: 'single'` — this is an individual library skill (Storybook v10.3.5 authoring surface), with no cross-skill references. Naive mode is the correct scope.

**Analysis Plan:**
- Coverage Check: documented exports vs Storybook v10.3.5 public API surface (AST-backed with ast-grep, Deep tier)
- Coherence Check: basic structural validation — SKILL.md frontmatter, sections, reference file existence
- Scoring: naive-mode weights (no cross-reference coherence category)

## Coverage Analysis

**Tier:** Deep
**Source Access:** full (State 1 — local clone present at `/home/armel/.skf/workspace/repos/github.com/storybookjs/storybook` @ tag `v10.3.5`, commit `e486d382`)
**Analysis Confidence:** full
**Mode:** naive (single-library skill; no cross-skill references to verify)
**Files Analyzed:** 20+ entry points across 8 monorepo packages in scope

### Source API Surface — Packages Scanned

Storybook is a monorepo. The skill brief's `scope.include` globs define the authoring-surface subset of packages. Named exports were extracted via regex-assisted AST scanning of each package's declared entry points (internals excluded per source-access-protocol).

| Package | Entry points | Source exports | Documented | Coverage |
|---|---|---|---|---|
| `storybook` (core — `test`, `preview-api`, `manager-api`, `theming`, `theming/create`, `actions`, `highlight`, `viewport`) | 8 subpaths | 205 | 135 (incl. 95 strict matches + internal/types items deferred to references) | 46.3% |
| `@storybook/react-vite` | 2 files | 4 | 3 | 75.0% |
| `@storybook/react` | 2 files | 20 | 18 | 75.0% |
| `@storybook/builder-vite` | 1 file | 10 | 10 | 100.0% |
| `@storybook/addon-docs` | 2 files | 116 | 32 | 27.6% |
| `@storybook/addon-themes` | 1 file | 9 | 5 | 55.6% |
| `@storybook/addon-a11y` | 2 files | 12 | 4 | 33.3% |
| `@storybook/addon-vitest` | 1 file | 0 (default export only) | 12 (via internal constants) | N/A |

**Denominator convention:** `metadata.stats.exports_public_api = 430` is the creation-time AST-authoritative total (counted by `create-skill` with the same extraction patterns). The fresh scan above gave 368 (internals-filtered) or 378 (unfiltered) for comparison — the gap is `internal/types` subpaths and `experimental_*`/`internal_*` symbols. We use `430` as the scoring denominator to match the skill's own self-reported coverage baseline.

**Numerator convention:** `187` unique exports documented across SKILL.md body + all six `references/*.md` files (subagent split-body traversal). This is higher than `metadata.stats.exports_documented = 82` because metadata counts only SKILL.md body; the 187 figure includes the full Tier-2 content in references.

### Coverage Summary

- **Source API (authoritative, metadata.json):** 430 exports
- **Documented (SKILL.md + references, de-duplicated):** 187 exports
- **Union name-match coverage:** 187 / 430 = **43.5%**
- **Strict name match (fresh AST scan, internals excluded):** 162 / 368 = 44.0% (confirms ~44% ballpark)
- **Signature-bearing entries:** 187 / 187 = 100% (all documented items carry an `[AST:path:line]` citation)
- **Provenance-map entries:** 92 / 92 are T1 AST-verified (`signature_source: "T1"` on every entry)
- **Documented but not found in fresh source scan:** 51 items — these are largely:
  - `storybook/internal/types` public subpath items (`ComponentAnnotations`, `StoryAnnotations`, `ProjectAnnotations`, `PlayFunction`, `WebRenderer`, `CSFFile`, `Globals`, `ViewMode`, `ComponentAnnotations`, etc.) — intentionally excluded from the fresh scan because I filtered `internal/*` subpaths, but Storybook declares them as public
  - `@storybook/addon-vitest` internal constants (`A11Y_ADDON_ID`, `STORYBOOK_ADDON_TEST_CHANNEL`, `TEST_PROVIDER_ID`, `FULL_RUN_TRIGGERS`, `TriggerTestRun*`) — the addon's public surface is a preset, not a barrel, so the fresh scan found 0 exports
  - `experimental_UniversalStore`, `useStatusStore`, `useTestProviderStore`, `useUniversalStore` — experimental APIs legitimately documented for advanced use cases
  - These are not stale documentation — they're cases where the fresh scan under-counted the authoritative source surface

### Split-Body Cross-Check (SKILL.md ↔ references/*.md)

All 6 reference files were read and cross-checked against SKILL.md. Five granularity-level mismatches were flagged — **none are hard conflicts**; all are cases where one file gives a more specific signature than the other. SKILL.md body is authoritative per protocol.

| # | Export | SKILL.md | Reference | Issue | Severity |
|---|---|---|---|---|---|
| 1 | `setProjectAnnotations` | listed under `storybook/preview-api` (runtime) | `story-types.md:183` pins to `@storybook/react` with `ProjectAnnotations<ReactRenderer>` | Source library attribution differs; runtime surface is shared. | Low |
| 2 | `composeStory` | `core-api.md:71` positional signature | `story-types.md:185-190` gives generic form `<TMeta, TArgs>` | Compatible — story-types.md is strictly more specific. | Info |
| 3 | `definePreview` | Key API Summary lists as `storybook/preview-api` runtime | `framework-config.md:54` shows `@storybook/react-vite` re-exports as `__definePreview` | Public alias vs. internal symbol name unresolved. | Low |
| 4 | `Preview` | `SKILL.md:167` type `ProjectAnnotations<ReactRenderer>` | `core-api.md:78` also lists a `Preview` runtime CLASS under `storybook/preview-api` | Same name, different kinds across subpaths — intentional but potentially confusing. | Info |
| 5 | `afterEach` (`addon-a11y`) | Key API Summary mentions addon-a11y only as "config only" | `addons.md:57` documents runtime `afterEach` export from `@storybook/addon-a11y/preview` | Minor omission in SKILL.md body. | Low |

### Category Scores (raw — weight application deferred to step-05)

| Category | Score | Basis |
|---|---|---|
| Export Coverage | **43.5%** | 187 documented / 430 source API (metadata.json authoritative) |
| Signature Accuracy | **97.3%** | (187 − 5 cross-check mismatches) / 187. All mismatches are granularity-only, not hard signature conflicts. Provenance-map entries are 100% T1 AST-verified. |
| Type Coverage | **52.4%** | 77 unique type/interface/class items documented / ~147 type-kind items in source (per subagent kind breakdown). |

**Note:** The 43.5% Export Coverage reflects the skill's stratified-by-design scope: the skill brief's `scope.notes` explicitly documents a three-tier extraction strategy (Tier A authoring surface fully documented, Tier B type/internal deferred to references, Tier C infrastructure out of scope). This will be surfaced in the Gap Report as a mitigating factor — the low coverage is an authored decision, not a defect — but the raw numbers are reported as measured per scoring-rules.md.

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed to Export Coverage, Signature Accuracy, Type Coverage per naive-mode rules)

### Structural Findings

| # | Type | Detail | Line |
|---|------|--------|------|
| 1 | migration-section-unexpected | Section 4b ("Migration & Deprecation Warnings") is present, but evidence-report.md reports **0 T2-future annotations**. Per scoring-rules, Section 4b is scoped to forward-looking breaking changes. The section's current content (v10 consolidation, PR #28907, PR #34408, PR #34203) describes **historical** migrations that have already shipped. | 146-156 |

**Downgrade justification for finding #1:** The v10 consolidation note (`@storybook/test` → `storybook/test`, etc.) is the skill's primary value proposition — it corrects training-data-induced wrong imports. While technically this is a "past" migration, it functions as an ongoing remediation guide for day-to-day story authoring. Per the Section 4b downgrade rule ("if the skill has a legitimate exception where Section 4b was manually populated with non-migration content, downgrade this gap to Low with inline justification"), **this finding is downgraded to Low severity**. Recommend renaming the section to "Import Surface Corrections" or moving this content into an inline callout of Key API Summary to avoid future confusion.

### Structural Checks (all pass)

| Check | Result | Detail |
|---|---|---|
| Top-level sections present | ✅ | 11 `##` sections — Overview, Quick Start, Common Workflows, Key API Summary, Migration & Deprecation Warnings, Key Types, Architecture at a Glance, CLI, Full API Reference, Full Type Definitions, Full Integration Patterns |
| Code fences balanced | ✅ | 5 open / 5 close (10 total ```) |
| Code fence language annotations | ✅ | All 5 fences carry a language (`tsx`, `ts`, `bash`) |
| `[MANUAL:...]` / `[/MANUAL:...]` markers balanced | ✅ | 4 open / 4 close — additional-notes-quickstart, -api, -cli, -reference |
| Tier-2 stub sections present (split-body architecture) | ✅ | Full API Reference (63 words), Full Type Definitions (43 words), Full Integration Patterns (59 words) all stubbed with `references/*.md` pointers |
| `references/` directory referenced | ✅ | All 6 files on disk (`addons.md`, `core-api.md`, `csf3-patterns.md`, `doc-blocks.md`, `framework-config.md`, `story-types.md`) are mentioned in SKILL.md |
| Reference files exist for every mention | ✅ | 0 broken `references/*.md` links |
| `scripts/` / `assets/` directory | N/A | Neither present — Section 7b ("Scripts & Assets") correctly absent |
| Internal consistency (examples use documented exports) | ✅ | Quick Start, Common Workflows, and Key Types code samples reference exports that appear in the Key API Summary table (Meta, StoryObj, Preview, fn, expect, userEvent, withThemeByClassName, useArgs, composeStories, setProjectAnnotations) |

### Reference Consistency (split-body)

See the **Split-Body Cross-Check** table in the Coverage Analysis section above. 5 granularity-level mismatches flagged (all Low/Info), none are hard signature conflicts.

**Exports Cross-Checked:** 187
**Mismatches Found:** 5 (all soft/granularity)

**Structural Issues:** 1 (Low, downgraded per documented exception)

## External Validation

**Source:** Reused from `forge-data/oms-storybook-react-vite/10.3.5/evidence-report.md` (create-skill `## Validation Results` section).
**Freshness check:** Pass — evidence-report `Generated: 2026-04-11T17:50:00Z` equals `metadata.json.generation_date: 2026-04-11T17:50:00Z`. SKILL.md has no uncommitted changes since commit `3747e82 Add oms-storybook-react-vite skill compiled from Storybook v10.3.5`. No re-run required.

### skill-check
- **Available:** yes (reused)
- **Quality Score:** 100/100
- **Schema:** PASS
- **Frontmatter:** PASS
- **Body:** PASS (235 lines, within 500-line budget)
- **Metadata:** PASS
- **Security:** skipped (SNYK_TOKEN not configured)
- **Errors:** 0
- **Warnings:** 0
- **Diagnostics:** none

### tessl
- **Available:** yes (reused)
- **Validation:** PASSED
- **Description Score:** 100%
- **Content Score:** 73%
- **Review Score:** 89%
- **Judge Breakdown:**
  - Description — 100%: specificity 3/3, trigger_term_quality 3/3, completeness 3/3, distinctiveness_conflict_risk 3/3
  - Content — 73%: conciseness 2/3 (expected SKF floor for two-tier + provenance design), actionability 3/3, workflow_clarity 2/3, progressive_disclosure 3/3
  - Review score: 89% (above the 60% SKF warning floor)

**Content quality note:** tessl content at 73% is in the expected range for a split-body skill — tessl evaluates only the SKILL.md body, not `references/*.md` files. The skill intentionally moves Tier-2 content (full API reference, full type definitions, full integration patterns) into reference files per SKF architecture. No warning raised because 73% > 70% floor.

### Combined External Score

- **External Validation Score:** **94.5%** (= (skill-check 100 + tessl review 89) / 2)
- **Tools used:** skill-check, tessl (both via evidence-report reuse)

## Completeness Score

### Score Breakdown

| Category | Score | Weight | Weighted |
|----------|-------|--------|----------|
| Export Coverage | 43.5% | 45% | 19.58% |
| Signature Accuracy | 97.3% | 25% | 24.33% |
| Type Coverage | 52.4% | 20% | 10.48% |
| Coherence (naive — not scored) | — | 0% | 0.00% |
| External Validation | 94.5% | 10% | 9.45% |
| **Total** | | **100%** | **63.84%** |

### Result

**Score:** 63.84%
**Threshold:** 80%
**Result:** **FAIL**

**Weight Distribution:** naive (coherence redistributed: Export Coverage 45, Signature Accuracy 25, Type Coverage 20, External Validation 10)
**Tier Adjustment:** none (Deep tier — Signature Accuracy and Type Coverage both active)
**External Validators:** both available (skill-check + tessl, reused from evidence-report)
**Analysis Confidence:** full (State 1 — local clone available at `~/.skf/workspace/repos/github.com/storybookjs/storybook` @ v10.3.5)

**Dominant drag:** Export Coverage at 43.5% contributes only 19.58 of a possible 45 weighted points — a 25.42-point shortfall that alone would prevent a PASS even if every other category scored 100%. The secondary drag is Type Coverage at 52.4% (10.48 / 20 weighted points).

## Gap Report

**Total Gaps:** 9
**Blocking (Critical + High):** 1
**Non-blocking (Medium + Low + Info):** 8

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|-----------------|
| Critical | 1 | Substantial content addition — 150–200 undocumented authoring-surface exports need at least a one-line entry in the appropriate `references/*.md` file with `[AST:path:line]` citation |
| High | 0 | — |
| Medium | 2 | Targeted — ~20 type/interface items from `@storybook/addon-docs` control system; Section 4b content re-scoping |
| Low | 5 | Quick edits — split-body granularity mismatches, alias/rename disambiguation |
| Info | 1 | Advisory — run realistic-prompt discovery tests before export |
| **Total** | **9** | |

### GAP-001: Export Coverage below 50% — 243 source API exports undocumented

**Severity:** Critical
**Category:** Coverage
**Source:** `SKILL.md` + `references/*.md` (all 6 files); source at `code/core/**`, `code/renderers/react/**`, `code/addons/**`

**Issue:** Coverage is 187 / 430 = **43.5%** against the authoritative `metadata.json.stats.exports_public_api` denominator. The dominant undocumented regions are:
- **`@storybook/addon-docs` control primitives** (~84 items): `BooleanControl`, `ColorControl`, `DateControl`, `FilesControl`, `NumberControl`, `ObjectControl`, `OptionsControl`, `RangeControl`, `TextControl` plus their `*Config`/`*Props`/`*Value` support types. The skill documents only the MDX block subset (`Canvas`, `Controls`, `Primary`, `Stories`, etc.) and skips the doc-block control primitives used when writing a custom `Controls` panel.
- **`storybook` core utility exports** (~110 items): `combineArgs`, `combineParameters`, `composeConfigs`, `composeStepRunners`, `filterArgTypes`, `inferControls`, `normalizeStory`, `prepareStory`, `prepareMeta`, `mockChannel`, `sanitizeStoryContextUpdate`, `sortStoriesV7`, `defaultDecorateStory`, `decorateStory`, `applyHooks`, `onMockCall`, `isMockFunction`, `clearAllMocks`, `resetAllMocks`, `restoreAllMocks`, `mocked`, `mocks` — useful for portable-stories and test-harness authors but absent from `references/core-api.md`.
- **`@storybook/addon-themes` support types** (4 items): `ClassNameStrategyConfiguration`, `DataAttributeStrategyConfiguration`, `ProviderStrategyConfiguration`, `DecoratorHelpers`.
- **`@storybook/addon-a11y` runtime surface** (7 items): `A11yGlobals`, `A11yParameters`, `A11yReport`, `ContextObjectWithoutNode`, `ContextSpecWithoutNode`, `SelectorWithoutNode`, `decorators`, `initialGlobals` — only `afterEach` and `parameters.a11y.test` are currently covered.

**Remediation:** The skill brief's `scope.notes` documents a three-tier stratification strategy (Tier A authoring, Tier B types, Tier C infrastructure). To close the Export Coverage gap without abandoning that strategy, run the **update-skill** workflow targeting:
1. `references/doc-blocks.md` — extend with a "Control Primitives" subsection enumerating the ~84 `*Control` / `*Config` / `*Props` / `*Value` types imported from `@storybook/addon-docs/blocks`, each with one-line description and `[AST:code/addons/docs/src/blocks.ts:Lnn]` citation.
2. `references/core-api.md` — extend with a "Test Harness Utilities" subsection enumerating `combineArgs`, `combineParameters`, `composeConfigs`, `mockChannel`, `prepareStory`, and the ~10 `mocked`/`mocks` family of functions with one-line descriptions.
3. `references/addons.md` — extend `@storybook/addon-themes` and `@storybook/addon-a11y` sections with the runtime/support types enumerated above.
4. Alternatively, if the stratified scope is intentional and the authoring surface is complete, **override the scoring threshold** (pass as `--threshold 60` to `skf-test-skill`) and document the rationale in `_bmad/_memory/forger-sidecar/preferences.yaml`. This is only appropriate if the undocumented ~240 exports are truly out-of-scope for the target day-90+ story author.

**Effort:** ~2 hours — one targeted `update-skill` run producing ~240 one-liner entries in three reference files. Source material is already extracted in `forge-data/oms-storybook-react-vite/10.3.5/provenance-map.json` for the 92 T1 entries; remaining ~150 can be re-extracted by pointing ast-grep at the listed files.

---

### GAP-002: Type Coverage at 52.4% — ~70 type-kind items undocumented

**Severity:** Medium
**Category:** Coverage
**Source:** `references/story-types.md`, `references/doc-blocks.md`

**Issue:** 77 of ~147 type/interface/class items in source are documented. Most of the gap sits in `@storybook/addon-docs` (~35 type aliases + ~15 interfaces not documented) and `storybook` core (~46 types, only ~30 documented — missing `Combo`, `StoreOptions`, `StoriesHash`, `HashEntry`, `RootEntry`, `GroupEntry`, `ComponentEntry`, `StoryEntry`, `LeafEntry`, `DocsEntry`, `IndexHash`, `State`, `GlobalState`, `ViewportParameters`, `ViewportStyles`, `ViewportType`, `InitialViewportKeys`, `ManagerContext`, `ManagerProviderProps`, `Refs`, `API_EventMap`, `API_KeyCollection`, `StorybookTheme`, `ThemeVars`, `ThemeVarsColors`, `ThemeVarsPartial`, `Typography`, `TextSize`, `Brand`, `Animation`, `Background`, `Color`).

**Remediation:** Extend `references/story-types.md` with a "Manager/Store Types" subsection covering the `StoriesHash`, `HashEntry`, `IndexHash`, `ComponentEntry`, `StoryEntry` family — these are needed by anyone writing a custom toolbar or panel. Extend `references/framework-config.md` with a "Theme Types" subsection for `StorybookTheme`, `ThemeVars`, `ThemeVarsColors`, `Typography`, `TextSize`, `Brand` (load-bearing for `storybook/theming/create`). Extend `references/doc-blocks.md` with a "Control Types" subsection (see GAP-001).

**Effort:** ~45 min — targeted extension of three reference files.

---

### GAP-003: Section 4b "Migration & Deprecation Warnings" contains historical content, not T2-future annotations

**Severity:** Medium (downgraded to Low — see justification)
**Category:** Structural
**Source:** `SKILL.md:146-156`

**Issue:** Per scoring-rules and `skf-create-skill/assets/skill-sections.md`, Section 4b is scoped to *forward-looking* breaking changes captured by T2-future annotations in `evidence-report.md`. The evidence report shows `T2-future: 0` (no deprecation warnings or planned renames). Section 4b is nevertheless present, populated with four historical shipped-in-v10 migration notes (v10 consolidation, PR #28907, PR #34408, PR #34203).

**Downgrade rationale:** The v10 consolidation note is the skill's core value proposition — it corrects training-data-induced wrong imports that persist 18+ months after the consolidation shipped. Per the Section 4b downgrade rule, this is a "legitimate exception where Section 4b was manually populated with non-migration content" — **downgraded to Low**.

**Remediation:** Two acceptable paths:
1. **Rename and keep** — rename Section 4b to "Import Surface Corrections" or "v10 Consolidation Notes". Keep the four bullets. This signals to future maintainers that the section is intentionally off the Section 4b contract.
2. **Move and delete** — fold the v10 consolidation bullet into an inline callout at the top of "Key API Summary", fold the PR notes into the appropriate reference file (`framework-config.md` or `addons.md`), then delete Section 4b entirely. This restores the evidence-report contract.

**Effort:** 10 min (path 1) or 20 min (path 2).

---

### GAP-004: SKILL.md Key API Summary attributes `setProjectAnnotations` to `storybook/preview-api` but story-types.md pins it to `@storybook/react`

**Severity:** Low
**Category:** Coverage (split-body cross-check)
**Source:** `SKILL.md:132` vs `references/story-types.md:183`

**Issue:** The runtime surface is shared (both subpaths re-export the same symbol), but the user-facing library attribution differs. A reader following the Key API Summary will import from `storybook/preview-api`; a reader following the type section will import from `@storybook/react`. Both work, but the inconsistency undermines the skill's "canonical import" guarantee.

**Remediation:** Pick `@storybook/react-vite` (framework-aligned) as the canonical import in `SKILL.md:132` Key API Summary, add a note in `references/story-types.md:183` that `storybook/preview-api` also re-exports the symbol. `[AST:code/renderers/react/src/portable-stories.ts:L1]`.

**Effort:** 5 min.

---

### GAP-005: `composeStory` signature granularity differs between core-api.md and story-types.md

**Severity:** Low
**Category:** Coverage (split-body cross-check)
**Source:** `references/core-api.md:71` vs `references/story-types.md:185-190`

**Issue:** `core-api.md` shows the positional form `composeStory(story, componentAnnotations, projectAnnotations?, exportsName?)`. `story-types.md` shows the generic form `composeStory<TMeta extends Meta, TArgs extends Args>(story, ..., exportsName?): ComposedStoryFn<ReactRenderer, TArgs>`. Signatures are compatible — the second is strictly more specific — but there is no cross-pointer between the two definitions.

**Remediation:** In `references/core-api.md:71`, add `See references/story-types.md for the generic form with `<TMeta, TArgs>` type parameters.` Or, better, replace with the generic form and cite `[AST:code/renderers/react/src/portable-stories.ts:L1]`.

**Effort:** 5 min.

---

### GAP-006: `definePreview` public name vs `__definePreview` internal symbol unresolved

**Severity:** Low
**Category:** Coverage (split-body cross-check)
**Source:** `SKILL.md:132` vs `references/framework-config.md:54` vs `references/story-types.md:229`

**Issue:** SKILL.md Key API Summary lists `definePreview` as runtime export from `storybook/preview-api`. `framework-config.md:54` shows `@storybook/react-vite` re-exports it under the internal name `__definePreview`. `story-types.md:229` documents `__definePreview` as the canonical CSF4 factory entry. A reader writing a CSF4 factory preview will be unsure which symbol name to import.

**Remediation:** Add a one-line clarification in SKILL.md line 132 Key API Summary: `definePreview` / `__definePreview` *(CSF4 factory — the double-underscore form is the current canonical export name in `@storybook/react-vite`)*. Cite `[AST:code/renderers/react/src/preview.tsx:L1]`.

**Effort:** 5 min.

---

### GAP-007: `Preview` symbol is both a type and a runtime class — disambiguate by subpath

**Severity:** Low
**Category:** Coverage (split-body cross-check)
**Source:** `SKILL.md:167` vs `references/core-api.md:78`

**Issue:** `SKILL.md:167` Key Types defines `Preview = ProjectAnnotations<ReactRenderer>` (the shape of `.storybook/preview.ts` default export). `core-api.md:78` separately lists a `Preview` runtime **class** under `storybook/preview-api` (the `PreviewWeb` runtime). Same name, different kinds, different subpaths — intentional but potentially confusing to a reader who imports `Preview` expecting the type.

**Remediation:** In `references/core-api.md:78`, rename the entry to `Preview (runtime class, aliased from PreviewWeb)` and add `Not to be confused with the `Preview` **type** in @storybook/react-vite — see SKILL.md:167`. Similarly, add a cross-pointer from `SKILL.md:167` to the runtime class.

**Effort:** 10 min.

---

### GAP-008: addon-a11y `afterEach` runtime export missing from Key API Summary

**Severity:** Low
**Category:** Coverage
**Source:** `SKILL.md:138` vs `references/addons.md:57`

**Issue:** SKILL.md Key API Summary mentions addon-a11y only as "config only — parameters.a11y.test". `references/addons.md:57` additionally documents a runtime `afterEach` export from `@storybook/addon-a11y/preview` (async function running axe-core per-story) that is not referenced in SKILL.md. Story authors calling `afterEach` in their own `preview.ts` will not discover this from the Tier 1 body.

**Remediation:** In `SKILL.md:138`, extend the addon-a11y row: `| a11y \`parameters: { a11y: { test: ... } }\`, `afterEach()` | param + runtime | `@storybook/addon-a11y/preview` `[AST:code/addons/a11y/src/preview.tsx:L1]` |`.

**Effort:** 3 min.

---

### GAP-009: Discovery testing not yet performed

**Severity:** Info
**Category:** Discovery
**Source:** workflow advisory

**Issue:** The skill has not been tested against realistic, noisy user prompts. A skill that passes structural and AST checks can still fail to trigger in production if its description keywords don't match how real users phrase requests.

**Remediation:** Before export, run 3–5 realistic prompts against the skill via `claude` CLI or the SKF discovery harness. Suggested prompts:
- `"why does my storybook import @storybook/test throw an error in v10?"` (should trigger — targets the skill's core v10 consolidation value prop)
- `"how do I write a play function with userEvent.click?"` (should trigger — core CSF3 authoring)
- `"can you set up storybook for the first time in this react app?"` (should NOT trigger — excluded by "Do NOT use for first-time project setup" in the description)
- `"my story's args aren't updating when I call updateArgs"` (should trigger — preview-api hook surface)
- `"how do I test my stories in vitest?"` (should trigger — composeStories + setProjectAnnotations portable-stories)

**Effort:** ~15 min for a discovery pass.

### Discovery Quality

**Description:** tessl description score is **100%** (specificity 3/3, trigger_term_quality 3/3, completeness 3/3, distinctiveness_conflict_risk 3/3). No description optimization required — the description already uses third-person voice, concrete trigger filenames (`*.stories.tsx`, `preview.ts`, `.storybook/main.ts`), version gating (`10.3+`), negative triggers (`Do NOT use for first-time project setup`), and alternative skill references (the upgrade CLI).

**Discovery testing recommended.** Before export, test the skill with 3–5 realistic prompts phrased the way real users actually talk — with casual language, typos, incomplete context, and implicit references. See GAP-009 above for a suggested prompt set.

### Mitigating Context for the FAIL Score

The 63.84% FAIL is driven almost entirely by Export Coverage (43.5% × 45% weight = 19.58 / 45 possible points). This is not a defect in the skill — it is a consequence of the authored stratification strategy documented in `forge-data/oms-storybook-react-vite/skill-brief.yaml` `scope.notes`:

- Storybook v10 consolidates ~40 packages into a single `storybook` package (~430 public exports across the monorepo).
- The skill deliberately covers **authoring tier A** (`test`, `preview-api`, hooks, theming, docs blocks, essential addons) with depth, and defers **type tier B** and **infrastructure tier C** to reference files (or omits them entirely).
- The skill's intended audience is the day-90+ story author, not the toolbar/panel/plugin author — the latter is explicitly out of scope per scope.notes.
- By this curated-surface measure, the skill's effective coverage of its stated audience is much higher than 43.5%.

**Two paths forward:**
1. **Run `update-skill` to lift coverage** toward 70–80% by filling reference files with the additional 150–200 one-line entries — this preserves the stratified architecture while crossing the scoring threshold. Recommended if the skill will be distributed via `agentskills.io` where the scoring floor matters.
2. **Override the threshold to 60%** in `_bmad/_memory/forger-sidecar/preferences.yaml` and document the rationale — appropriate if this skill is for internal use where the stratified scope is understood and the FAIL score is a known false negative. Only viable if `skf-test-skill` is amended to support a persisted threshold override (currently the default is 80%).

Path 1 is the documented workflow and is recommended. Path 2 requires workflow changes.

---

**Test complete for oms-storybook-react-vite.**

**Result:** **FAIL** — **63.84%** (threshold: 80%)

**Gaps Found:** 9
- Critical: 1
- High: 0
- Medium: 2 (1 downgraded to Low per documented exception)
- Low: 5
- Info: 1

**Recommended next step:** **update-skill** — run the update-skill workflow to address GAP-001 (Export Coverage lift) and optionally GAP-002 through GAP-008 for a cleaner release.
