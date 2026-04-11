---
workflowType: 'test-skill'
skillName: 'oms-uitripled'
skillDir: 'skills/oms-uitripled/0.1.0/oms-uitripled'
testMode: 'naive'
forgeTier: 'Deep'
testResult: 'pass'
score: '93.07%'
threshold: '80%'
analysisConfidence: 'full'
testDate: '2026-04-11'
stepsCompleted: ['step-01-init', 'step-02-detect-mode', 'step-03-coverage-check', 'step-04-coherence-check', 'step-04b-external-validators', 'step-05-score', 'step-06-report']
nextWorkflow: 'export-skill'
---

# Test Report: oms-uitripled

## Test Summary

**Skill:** oms-uitripled
**Test Mode:** naive
**Forge Tier:** Deep

**Mode Rationale:** `metadata.json` declares `skill_type: "single"` — this is an individual skill that wraps one source (the uitripled `react-shadcn` registry), with no cross-skill integration patterns. Naive mode is therefore the correct path: coverage-focused API surface validation without the stack-skill cross-reference checks.

**Analysis Plan:**
- Coverage Check: Documented exports vs. source public API surface (ThemeProvider, useTheme, UILibraryProvider, useUILibrary, cn, sanitizeSlug, generateUniqueSlug, GAP_VALUES, generateGridCode, mergeComponentImports, add), plus the 171 registry components the skill claims to catalog.
- Coherence Check: Basic structural validation — frontmatter already validated in step-01 (PASS); will verify internal references/link integrity within SKILL.md + references/.
- External Validators: agentskills.io spec compliance (Deep tier).
- Scoring: Naive-mode weight distribution (no coherence cross-reference weight).

## Coverage Analysis

**Tier:** Deep
**Source Access:** full (State 1 — local clone)
**Source Path:** `/home/armel/.skf/workspace/repos/github.com/moumen-soliman/uitripled` @ `a5ffb45`
**Analysis Confidence:** T1 (full AST re-verification against live source)
**Files Analyzed:** 9 entry-point source files (packages/utils/src/{cn,grid-utils,merge-imports,builder-utils,types}.ts, packages/components/react-shadcn/src/components/theme-provider.tsx, packages/components/react-shadcn/src/ui-library-provider.tsx, packages/uitripled/src/commands/add.ts, packages/uitripled/src/utils/registry.ts)
**Denominator Reconciliation:** provenance-map.json lists 22 entries; metadata.json `exports[]` lists 11; live AST surface is **34** non-component exports. Coverage denominator = 34 (source AST union is the authoritative baseline at Deep tier with State 1 access — see source-access-protocol.md).

### Export Coverage

| Export | Type | Source Location | Documented | Signature | Status |
|---|---|---|---|---|---|
| `ThemeProvider` | function | `packages/components/react-shadcn/src/components/theme-provider.tsx:18` | SKILL.md + references/setup.md | match | PASS |
| `useTheme` | const | `packages/components/react-shadcn/src/components/theme-provider.tsx:35` | SKILL.md + references/setup.md | match | PASS |
| `ThemeMode` | type | `packages/components/react-shadcn/src/components/theme-provider.tsx:9` | SKILL.md `Key Types` + references/types.md | match | PASS |
| `THEME_STORAGE_KEY` | const | `packages/components/react-shadcn/src/components/theme-provider.tsx:11` | references/setup.md | match | PASS |
| `UILibraryProvider` | function | `packages/components/react-shadcn/src/ui-library-provider.tsx:31` | SKILL.md + references/setup.md | match | PASS |
| `useUILibrary` | function | `packages/components/react-shadcn/src/ui-library-provider.tsx:23` | SKILL.md + references/setup.md | match | PASS |
| `cn` | function | `packages/utils/src/cn.ts:4` | SKILL.md + references/utils.md | match | PASS |
| `GAP_VALUES` | const | `packages/utils/src/grid-utils.ts:23` | SKILL.md + references/utils.md | match | PASS |
| `getGapSliderIndex` | const | `packages/utils/src/grid-utils.ts:32` | references/utils.md | match (declaration only) | PASS |
| `getGapValueFromIndex` | const | `packages/utils/src/grid-utils.ts:40` | references/utils.md | match (declaration only) | PASS |
| `generateGridCode` | const | `packages/utils/src/grid-utils.ts:47` | SKILL.md + references/utils.md | match (declaration only) | PASS |
| `initializeCells` | const | `packages/utils/src/grid-utils.ts:76` | references/utils.md:63 | **MISMATCH** — doc shows `(rows: number, cols: number)`; source is `(cols: number, rows: number)` | **FAIL** |
| `getCellKey` | const | `packages/utils/src/grid-utils.ts:101` | references/utils.md:64 | **MISMATCH** — doc shows `(cell: GridCell) => string`; source is `(row: number, col: number) => string` | **FAIL** |
| `isCellInSelection` | const | `packages/utils/src/grid-utils.ts:106` | references/utils.md:65 | **MISMATCH** — doc shows `(cell: GridCell, sel: unknown) => boolean`; source is `(row: number, col: number, selectedCells: string[]) => boolean` | **FAIL** |
| `GridCell` | interface | `packages/utils/src/grid-utils.ts:5` | references/types.md + references/utils.md:56 | match | PASS |
| `BentoPreset` | interface | `packages/utils/src/grid-utils.ts:12` | references/types.md + references/utils.md:57 | match | PASS |
| `mergeComponentImports` | function | `packages/utils/src/merge-imports.ts:6` | SKILL.md + references/utils.md | match | PASS |
| `sanitizeSlug` | const | `packages/utils/src/builder-utils.ts:7` | references/utils.md | match | PASS |
| `generateUniqueSlug` | function | `packages/utils/src/builder-utils.ts:14` | references/utils.md | match | PASS |
| `createPage` | function | `packages/utils/src/builder-utils.ts:33` | — | — | **MISSING** |
| `extractSavedPages` | function | `packages/utils/src/builder-utils.ts:52` | — | — | **MISSING** |
| `countSavedProjectComponents` | function | `packages/utils/src/builder-utils.ts:70` | — | — | **MISSING** |
| `UILibrary` | type | `packages/utils/src/types.ts:3` | SKILL.md (narrowed) + references/types.md + references/utils.md | **partial** — SKILL.md `Key Types` block shows `"shadcnui" \| "baseui" \| "carbon"` with an inline comment noting `"react"` is present in `@uitripled/utils`; full source union is in references/utils.md:93 | WARN |
| `uiLibraryLabels` | const | `packages/utils/src/types.ts:5` | references/utils.md:95 | declaration only (no prose) | PASS |
| `ComponentCategory` | type | `packages/utils/src/types.ts:12` | references/types.md + references/utils.md | match | PASS |
| `Component` | type | `packages/utils/src/types.ts:24` | references/types.md + references/utils.md | match | PASS |
| `TextContentEntry` | type | `packages/utils/src/types.ts:52` | references/types.md + references/utils.md | match | PASS |
| `BuilderComponent` | type | `packages/utils/src/types.ts:57` | references/types.md + references/utils.md | match | PASS |
| `BuilderProjectPage` | type | `packages/utils/src/types.ts:64` | references/types.md + references/utils.md | match | PASS |
| `SavedProjectComponent` | type | `packages/utils/src/types.ts:71` | references/types.md + references/utils.md | match | PASS |
| `SavedProjectPage` | type | `packages/utils/src/types.ts:77` | references/types.md + references/utils.md | match | PASS |
| `SavedProject` | type | `packages/utils/src/types.ts:85` | references/types.md + references/utils.md | match | PASS |
| `add` | function | `packages/uitripled/src/commands/add.ts:8` | SKILL.md `CLI` + references/catalog.md | match | PASS |
| `fetchComponent` | function | `packages/uitripled/src/utils/registry.ts:5` | SKILL.md `CLI` + references/catalog.md | match | PASS |

**Registry catalog coverage (secondary surface):**

| Claim | Source | Verified |
|---|---|---|
| `packages/registry/registry.json` total = 278 items | registry.json line counts | YES (161 component / 74 block / 23 page / 20 ui) |
| `react-shadcn` subset = 171 items | filter by `files[].path` containing `react-shadcn` | YES |
| 15 pages / 38 blocks / 99 components / 19 UI leaves | filter by `type` within react-shadcn subset | YES (15 / 38 / 99 / 19) |
| 10 category buckets with counts (57/38/21/16/15/9/8/4/2/1) | SKILL.md Component Catalog table | Not re-verified at AST level — counts come from the extraction workflow's provenance. Flagged as Info (would require a registry.json re-aggregation pass). |

### Coverage Summary

- **Exports in source (non-registry-component):** 34
- **Documented:** 31 (91.2%)
- **Missing documentation:** 3 — `createPage`, `extractSavedPages`, `countSavedProjectComponents` (all Landing Builder internals in `packages/utils/src/builder-utils.ts`)
- **Signature mismatches:** 3 — `initializeCells`, `getCellKey`, `isCellInSelection` (all in `packages/utils/src/grid-utils.ts`, all wrong in `references/utils.md` AND already wrong in `provenance-map.json`, so the mismatches trace back to a systematic extraction bug rather than post-compile drift)
- **Type labeling partial:** 1 — `UILibrary` narrowed in SKILL.md body (with clarifying comment; full superset in references)
- **Stale documentation:** 0 (no symbols documented that don't exist in source)
- **Registry catalog fidelity:** 171 react-shadcn entries, category breakdown verified against filtered registry.json ✓

### Category Scores

| Category | Calculation | Score |
|---|---|---|
| Export Coverage | 31 / 34 | **91.2%** |
| Signature Accuracy | 28 / 31 verified signatures match | **90.3%** |
| Type Coverage | 12 / 12 exported types documented (ThemeMode, UILibrary, ComponentCategory, Component, TextContentEntry, BuilderComponent, BuilderProjectPage, SavedProjectComponent, SavedProjectPage, SavedProject, GridCell, BentoPreset) | **100%** |

Note: Weight application is deferred to step-05 where all category weights are calculated after external validation availability is known.

## Coherence Analysis

**Mode:** naive (basic structural validation only — no cross-skill references to verify)

### Document Structure

| Check | Result |
|---|---|
| Frontmatter compliance (agentskills.io) | PASS (skf-validate-frontmatter.py step-01: 0 issues) |
| Required sections present | PASS — Overview, Quick Start, Common Workflows, Component Catalog, Migration & Deprecation Warnings, Key Types, Architecture at a Glance, CLI, Full API Reference, Full Type Definitions, Full Integration Patterns |
| Section headers well-formed | PASS |
| Code fences have language annotations | PASS (`bash`, `tsx`, `ts`) |
| Malformed markdown / unclosed fences / broken tables | PASS (none detected) |
| `scripts/` or `assets/` directory presence | NEITHER EXISTS — Section 7b (Scripts & Assets) not required |
| References directory (`references/`) present | PASS (5 files: catalog.md, integration.md, setup.md, types.md, utils.md) |
| Split-body pointers resolve | PASS — `## Full API Reference`, `## Full Type Definitions`, `## Full Integration Patterns` each point at a references/*.md file that exists |

### Internal Consistency

| Check | Result |
|---|---|
| Provider examples use documented symbols | PASS — `ThemeProvider`, `UILibraryProvider`, `useTheme`, `useUILibrary` all declared in exports and referenced consistently in Quick Start / Common Workflows |
| `useTheme` destructure in Common Workflows (`toggleTheme`) matches source return shape | PASS (`theme, setTheme, resolvedTheme, systemTheme, toggleTheme`) |
| `useUILibrary` destructure (`setSelectedLibrary("baseui" \| "carbon")`) matches the narrower runtime `UILibrary` variant | PASS |
| `cn` example (`cn(className, "extra-classes")`) compatible with `(...inputs: ClassValue[]) => string` | PASS |
| `Component Catalog` category counts (57/38/21/16/15/9/8/4/2/1) sum to the claimed `171` total | PASS (57+38+21+16+15+9+8+4+2+1 = 171) |
| `Overview` claim "171/278" + per-type breakdown (15/38/99/19) internally consistent | PASS (15+38+99+19 = 171) |
| `Key Types` vs `references/types.md` — `UILibrary` type union | **PARTIAL** — SKILL.md `Key Types` (line 141) declares `"shadcnui" \| "baseui" \| "carbon"` as `UILibrary` with a trailing inline comment noting `"react"` is in `@uitripled/utils`; references/types.md + references/utils.md authoritatively include `"react"`. The inline comment clarifies intent (runtime subset), but a reader consuming SKILL.md body alone sees a narrower type than the exported symbol — low-confusion risk. Flagged as **Low** severity. |

### Section 4b (Migration & Deprecation) Verification

**Gate check:** Deep tier ✓ AND `forge-data/oms-uitripled/0.1.0/evidence-report.md` exists ✓ → execute.

- Section 4b present in SKILL.md: **YES** (line 128, "Migration & Deprecation Warnings")
- T2-future annotations in evidence-report.md: **0** (evidence-report lists `T2=2` but both are explicitly labeled `T2-past` — historical CLI install path + copy-paste distribution model; no forward-looking breaking-change annotations)
- Rule: "If T2-future annotations = 0 AND Section 4b is present → flag as **Medium** severity"

**Finding:** Section 4b is populated with CLI path evolution content that describes a **past** change (PR #8 that introduced `llms.txt` standardizing on `npx shadcn@latest add @uitripled/<name>`). Per `skf-create-skill/assets/skill-sections.md`, Section 4b is scoped to *forward-looking* breaking changes. Current-state CLI choice guidance and historical path rationale belong inline with the `## CLI` section, not Section 4b. There is no legitimate forward-looking migration to warn agents about — both CLI paths still work.

**Severity:** **Medium** (authoring-rule violation, but the content itself is accurate and useful — not misinformation). Recommended remediation: relocate the paragraph into the `## CLI` section as a "Preferred path rationale" note and remove Section 4b entirely (Deep-tier gate allows Section 4b to be absent when T2-future count is 0).

### Structural Findings Summary

- **Critical:** 0
- **High:** 0
- **Medium:** 1 (Section 4b presence with zero T2-future annotations)
- **Low:** 1 (SKILL.md `Key Types` narrows `UILibrary` relative to source superset)
- **Info:** 0

Coherence category not scored in naive mode — weight redistributed to Export Coverage / Signature Accuracy / Type Coverage / External Validation per `scoring-rules.md` naive-mode table.

## External Validation

**Source:** Auto-reused from `forge-data/oms-uitripled/0.1.0/evidence-report.md` `## Validation Results` section.

**Staleness check:**
- SKILL.md last commit: `2026-04-11T01:51:20+04:00` (git tracked, no uncommitted or staged diffs)
- Evidence report generated: `2026-04-11` (same session as create-skill)
- Result: **non-stale** — create-skill completed validators and SKILL.md has not been touched since. Fresh re-run would be identical.

### skill-check
- **Available:** yes (reused)
- **Quality Score:** 100/100
- **Errors:** 0
- **Warnings:** 0
- **Breakdown:** Frontmatter 30/30 · Description 30/30 · Body 20/20 · Links 10/10 · File 10/10
- **Diagnostics:** none
- **Run context:** 2-pass run during create-skill; `--fix` initially renamed `name` to match staging directory, then reverted after staging dir was renamed to `oms-uitripled` (recorded in evidence-report "Auto-Fixed Issues").

### tessl
- **Available:** yes (reused)
- **Validation:** PASSED
- **Description Score:** 100%
- **Content Score:** 73% (post-split; 50% → 73% after Apply-fixes trim per evidence-report)
- **Review Score:** 89% (80% → 89% after Apply-fixes)
- **Judge Breakdown:**
  - Description — specificity 3/3, trigger_term_quality 3/3, completeness 3/3, distinctiveness_conflict_risk 3/3
  - Content — conciseness 2/3, actionability 3/3, workflow_clarity 2/3, progressive_disclosure 3/3
- **Dismissed Suggestions (per step-06 expected behavior):**
  - "Add validation checkpoints to workflows" — no `verify installation` logic exists in uitripled source
  - "Remove inline source citations" — conflicts with SKF zero-hallucination policy
  - "Remove Architecture at a Glance" — required Tier 1 section per `skill-sections.md`
  - "Move Full API Reference to references" — partially honored via split-body stubs
- **Content quality warning:** N/A — 73% is above the 70% warning threshold. Note: tessl evaluates SKILL.md body only; split-body Tier 2 content lives in `references/*.md` and is not reflected in this score. A pre-split-body baseline would be higher.

### Combined External Score

- **External Validation Score:** (100 + 89) / 2 = **94.5%**
- **Tools used:** skill-check, tessl
- **Reuse recorded:** "External validation: reused from create-skill evidence report (same-session, non-stale)."

## Completeness Score

### Score Breakdown

| Category | Score | Weight | Weighted |
|---|---|---|---|
| Export Coverage | 91.2% | 45.0% | 41.04% |
| Signature Accuracy | 90.3% | 25.0% | 22.58% |
| Type Coverage | 100% | 20.0% | 20.00% |
| Coherence | — | 0% | 0.00% |
| External Validation | 94.5% | 10.0% | 9.45% |
| **Total** | | **100%** | **93.07%** |

### Result

**Score:** 93.07%
**Threshold:** 80%
**Result:** **PASS**

**Weight Distribution:** naive (coherence redistributed per `scoring-rules.md` naive-mode table — Export 45% / Signature 25% / Type 20% / External 10%)
**Tier Adjustment:** none (Deep tier, State 1 full source access — all categories scored with AST verification)
**External Validators:** both available (skill-check 100/100, tessl review 89%, combined 94.5%)
**Analysis Confidence:** full (State 1 — local clone at `~/.skf/workspace/repos/github.com/moumen-soliman/uitripled` @ `a5ffb45`)

**Active categories:** exportCoverage, signatureAccuracy, typeCoverage, externalValidation
**Skipped categories:** coherence (naive mode — weight = 0, redistributed into naive-mode weight table)
**Weight sum:** 100.0

No Access Degradation Notice required — analysis confidence is `full`.

## Gap Report

**Total Gaps:** 8
**Blocking (Critical + High):** 3
**Non-blocking (Medium + Low + Info):** 5

### Remediation Summary

| Severity | Count | Estimated Effort |
|---|---|---|
| Critical | 0 | — |
| High | 3 | ~30 min — edit 3 signatures in `references/utils.md` + regenerate 3 provenance-map entries from live source |
| Medium | 2 | ~20 min — relocate Section 4b content into `## CLI`, document 3 missing Landing Builder helpers |
| Low | 2 | ~5 min — clarify `UILibrary` type narrowing, verify category-count aggregation |
| Info | 1 | advisory — perform discovery testing before export |
| **Total** | **8** | |

---

### GAP-001: `initializeCells` parameter order mismatch

**Severity:** High
**Category:** Coverage (signature accuracy)
**Source:** `references/utils.md:63` vs source `packages/utils/src/grid-utils.ts:76`

**Issue:** `references/utils.md:63` declares `initializeCells: (rows: number, cols: number) => GridCell[]`. Source at `packages/utils/src/grid-utils.ts:76` is `(cols: number, rows: number): GridCell[]`. Parameter order is swapped. An agent following the docs would produce a grid with transposed dimensions. The same wrong order is stored in `provenance-map.json` entry for `initializeCells` (confidence `T1`), so the mismatch originated during extraction — not post-compile drift.

**Remediation:** Update `references/utils.md:63` to `export const initializeCells: (cols: number, rows: number) => GridCell[];` to match source. Also update `forge-data/oms-uitripled/0.1.0/provenance-map.json` entry `initializeCells.params` from `["rows: number", "cols: number"]` to `["cols: number", "rows: number"]`. Re-run create-skill step-03 AST extraction to prevent recurrence, or file a bug against the extraction pattern that populated the wrong order.

---

### GAP-002: `getCellKey` signature completely wrong

**Severity:** High
**Category:** Coverage (signature accuracy)
**Source:** `references/utils.md:64` vs source `packages/utils/src/grid-utils.ts:101`

**Issue:** `references/utils.md:64` declares `getCellKey: (cell: GridCell) => string`. Source at `packages/utils/src/grid-utils.ts:101` is `(row: number, col: number): string => \`${row}-${col}\``. An agent would attempt to call `getCellKey(someCell)` and get a TypeScript error or runtime `undefined-undefined`. `provenance-map.json` contains the same wrong signature (T1 confidence) — extraction bug, not drift.

**Remediation:** Update `references/utils.md:64` to `export const getCellKey: (row: number, col: number) => string;`. Update `provenance-map.json` entry `getCellKey.params` from `["cell: GridCell"]` to `["row: number", "col: number"]`.

---

### GAP-003: `isCellInSelection` signature completely wrong

**Severity:** High
**Category:** Coverage (signature accuracy)
**Source:** `references/utils.md:65` vs source `packages/utils/src/grid-utils.ts:106`

**Issue:** `references/utils.md:65` declares `isCellInSelection: (cell: GridCell, sel: unknown) => boolean`. Source at `packages/utils/src/grid-utils.ts:106-112` is `(row: number, col: number, selectedCells: string[]): boolean => selectedCells.includes(getCellKey(row, col))`. An agent would pass the wrong arguments. Same wrong signature in `provenance-map.json` (T1 confidence).

**Remediation:** Update `references/utils.md:65` to `export const isCellInSelection: (row: number, col: number, selectedCells: string[]) => boolean;`. Update `provenance-map.json` entry `isCellInSelection.params` from `["cell: GridCell", "sel: unknown"]` to `["row: number", "col: number", "selectedCells: string[]"]`.

---

### GAP-004: Section 4b present without T2-future annotations

**Severity:** Medium
**Category:** Coherence (structural — authoring rule)
**Source:** `skills/oms-uitripled/0.1.0/oms-uitripled/SKILL.md:128-132` ("Migration & Deprecation Warnings"); `forge-data/oms-uitripled/0.1.0/evidence-report.md:50-53`

**Issue:** SKILL.md Section 4b is populated with CLI path evolution content describing PR #8 (a historical change that introduced `llms.txt`). Evidence-report records `T2=2` but both are explicitly labeled **T2-past** — no T2-future annotations exist. Per `skf-create-skill/assets/skill-sections.md`, Section 4b is scoped to *forward-looking* breaking changes. Current-state CLI preference guidance belongs inline with `## CLI`. Both CLI paths (`npx shadcn@latest add @uitripled/<name>` and `npx uitripled add <name>`) still work — there is no forward migration to warn agents about.

**Remediation:** Relocate the Migration & Deprecation Warnings paragraph (SKILL.md:130) into the `## CLI` section as a "Preferred path" note under the `Preferred (shadcn namespace — per project AI docs)` block, and remove the `## Migration & Deprecation Warnings` section entirely. The Deep-tier gate in `scoring-rules.md` accepts absent Section 4b when T2-future count is 0.

---

### GAP-005: Three Landing Builder helpers undocumented

**Severity:** Medium
**Category:** Coverage (missing documentation)
**Source:** `packages/utils/src/builder-utils.ts:33` / `:52` / `:70`

**Issue:** Three public functions in `@uitripled/utils` are exported from the workspace `builder-utils.ts` module but are not mentioned in SKILL.md, `references/utils.md`, or `provenance-map.json`:
- `createPage(...)` — `builder-utils.ts:33`
- `extractSavedPages(project: SavedProject): SavedProjectPage[]` — `builder-utils.ts:52`
- `countSavedProjectComponents(project: SavedProject): number` — `builder-utils.ts:70`

These are Landing Builder internals used by `apps/docs/app/builder/`. The brief's include glob `packages/utils/src/**` placed them in scope, but the extraction workflow picked only `sanitizeSlug` and `generateUniqueSlug`. Not strictly blocking (secondary API surface), but the coverage denominator counts them as missing.

**Remediation:** Either (a) add a "Landing Builder project helpers" subsection to `references/utils.md` describing `createPage`, `extractSavedPages`, `countSavedProjectComponents` with their signatures read from `packages/utils/src/builder-utils.ts:33-76` and add entries to `provenance-map.json`; or (b) if these are deliberately out of scope, document the scope decision in the skill brief's `scope.notes` and add them to an exclude list so future test runs do not flag them. Option (a) is preferred since the brief did not explicitly exclude them.

---

### GAP-006: `UILibrary` type narrowed in SKILL.md `Key Types` block

**Severity:** Low
**Category:** Coherence (internal consistency — split-body type drift)
**Source:** `skills/oms-uitripled/0.1.0/oms-uitripled/SKILL.md:141` vs `references/types.md` + `references/utils.md:93`

**Issue:** SKILL.md `Key Types` (line 141) declares `type UILibrary = "shadcnui" | "baseui" | "carbon"` with a trailing inline comment `// + "react" in @uitripled/utils`. The source-of-truth export at `packages/utils/src/types.ts:3` is the 4-member union `"shadcnui" | "baseui" | "carbon" | "react"`, which is correctly reproduced in `references/types.md` and `references/utils.md:93`. The narrowed form in SKILL.md body reflects the runtime subset used by `packages/components/react-shadcn/src/types.ts:1`, but since both type aliases share the name `UILibrary`, readers of SKILL.md body alone see a narrower type than what `@uitripled/utils` exports.

**Remediation:** Either (a) replace line 141 with the full 4-member union and add a 1-line note about the runtime-reachable subset for the react-shadcn package; or (b) rename the narrowed form to `type RuntimeUILibrary` so the two aliases are distinguishable. Option (a) is simpler and matches the split-body consistency rule (SKILL.md body as authoritative).

---

### GAP-007: Component Catalog category counts not re-verified at AST level

**Severity:** Low
**Category:** Coverage (registry fidelity)
**Source:** `skills/oms-uitripled/0.1.0/oms-uitripled/SKILL.md:107-118`

**Issue:** SKILL.md Component Catalog table lists category counts `components 57 / sections 38 / native 21 / cards 16 / page 15 / decorative 9 / micro 8 / resumes 4 / data 2 / forms 1` summing to 171. The sum is internally consistent and the total matches `metadata.json` `stats.components_registered=171`, but the per-category breakdown was not re-verified against a live aggregation of `packages/registry/registry.json` filtered by `files[].path contains "react-shadcn"` and grouped by the registry's custom `category` / `subcategory` fields. This is advisory, not blocking.

**Remediation:** Optional — add a one-time re-aggregation pass in `update-skill` that verifies the category-count table against registry.json and flags drift. Not required for export.

---

### GAP-008: Discovery testing not performed

**Severity:** Info
**Category:** Advisory (discovery quality)

**Issue:** The skill has not been tested with realistic user prompts to verify that its description and keyword set actually trigger the skill in production conditions.

**Remediation:** See Discovery Quality section below.

---

### Discovery Quality

**Description optimization:** tessl scored Description at **100%** (all four sub-metrics 3/3: specificity, trigger_term_quality, completeness, distinctiveness_conflict_risk). skill-check raised 0 description warnings. No description changes are recommended.

**Discovery testing recommended.** Before export, test the skill with 3-5 realistic prompts phrased the way real users actually talk — with casual language, typos, incomplete context, and implicit references. A skill tested only with clean prompts may fail to trigger in production. Example realistic prompt patterns for oms-uitripled:

- Vague: "i need a landing page with hero and pricing and testimonials, got anything"
- Implicit: "install that uitripled hero thing"
- Abbreviated: "add the shadcn-ish animated component pack"
- Typo: "uitripeld cli install hero-section"
- Negative-trigger test: "use react-baseui from uitripled" — should NOT route to this skill (baseui variant is out of scope per brief)
- Conflict test: "shadcn hero section" — is oms-uitripled preferred over a vanilla shadcn/ui skill for the `@uitripled/` namespace? Description already covers this with "171 animated Framer Motion components via npx shadcn@latest add @uitripled/..."

Record the 3-5 prompts you test and their routing decisions as a follow-up note in the skill's `forge-data/oms-uitripled/0.1.0/` directory before running export-skill.

---

### Blocking Summary

- **Critical:** 0
- **High (blocks export):** 3 (GAP-001, GAP-002, GAP-003 — all signature mismatches in Grid helpers, all traceable to the same extraction bug in `provenance-map.json`)

**Important:** Despite the **PASS** score (93.07% > 80% threshold), the 3 High-severity signature mismatches in Grid helpers should be remediated before export even though the arithmetic weighting does not push the score below threshold. Signature mismatches produce *silent* agent failures — an LLM will call `initializeCells(rows, cols)` following the docs and get transposed output that does not throw. The scoring system is designed to let this through because only 3 of 31 verified signatures fail, but the blast radius per mismatch is high. Recommended: fix GAP-001/002/003 in a quick pass, then re-run skf-test-skill to confirm 0 High gaps, then run export-skill.

