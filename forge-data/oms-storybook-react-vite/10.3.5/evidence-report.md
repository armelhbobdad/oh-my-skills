# Evidence Report: oms-storybook-react-vite

**Generated:** 2026-04-11T17:50:00Z
**Forge Tier:** Deep
**Source:** https://github.com/storybookjs/storybook @ e486d3826bcd40c52db1c766966d1c8ec16df6cb (tag v10.3.5)

## Tool Versions

- ast-grep: 0.42.0
- QMD: 2.0.1
- SKF: 1.0.0

## Extraction Summary

- Source workspace: `/home/armel/.skf/workspace/repos/github.com/storybookjs/storybook` (newly cloned, persists for future re-forges)
- Files scanned: ~70 targeted entry files (selected from 1175 files in-scope; targeted extraction via `package.json exports` authoritative surface)
- Exports extracted: ~430 (documented in SKILL.md + references: 82 primary entries in provenance-map.json, rest referenced by count)
  - Core (`storybook` 28 subpaths): ~350
  - `@storybook/react-vite` framework: 12
  - `@storybook/react` renderer: 22
  - `@storybook/builder-vite` builder: 8
  - Addons (a11y/docs/themes/vitest): ~65 (23 MDX doc blocks)
- Confidence distribution: T1=430, T1-low=0, T2=5, T3=4
- Top exports by authoring relevance: `Meta`, `StoryObj`, `Decorator`, `Preview`, `fn`, `expect`, `within`, `userEvent`, `composeStories`, `setProjectAnnotations`, `withThemeByClassName`, `Canvas`, `Controls`, `Primary`

**CSF type verification (brief requirement #5):** All 7 required types confirmed present and exported from `@storybook/react`:
- `Meta` @ `code/renderers/react/src/public-types.ts:29` ✓
- `StoryObj` @ `code/renderers/react/src/public-types.ts:47` ✓
- `StoryFn` @ `code/renderers/react/src/public-types.ts:35` ✓
- `Decorator` @ `code/renderers/react/src/public-types.ts:55` ✓
- `Parameters` @ (re-exported from storybook/internal/types) ✓
- `ArgTypes` @ (re-exported from storybook/internal/types) ✓
- `Args` @ (re-exported from storybook/internal/types) ✓

Bonus types also confirmed: `Loader`, `StoryContext`, `Preview`, `ReactRenderer`. All 9 are also re-exported from `@storybook/react-vite` (confirmed via `code/frameworks/react-vite/src/index.ts` star re-export).

## Extraction Strategy Notes

**Why targeted entry-file extraction (not full AST walk):** Storybook's source tree has ~1175 in-scope `.ts`/`.tsx` files after exclusions — too large for a practical full AST pass. But the `package.json` `exports` field in each package is the **authoritative public contract**, and it maps each subpath to a specific entry file. Reading the ~70 entry files (and one level of re-export chases where needed) produces a complete public surface with zero wasted effort on internal helpers. This is the same strategy used for `oms-cognee` and `oms-uitripled`.

**CCC semantic index:** Deliberately skipped. CCC pre-ranking offers no value when the extraction queue is derived from authoritative package.json exports — we already know exactly which files to read. The workspace clone is retained for future re-forges; CCC can be initialized there later if a subsequent workflow needs semantic search.

## QMD Collections

- `oms-storybook-react-vite-temporal` — 5 files (issues, prs, releases, changelog, targeted-issues), 440 embedded chunks from 100 issues + 100 PRs + 10 releases + 442KB changelog
- `oms-storybook-react-vite-docs` — 4 files (react-vite-setup, api-reference, addon-catalog, docs-landing), 4 embedded chunks from 4 doc URLs

## Enrichment (T2)

- Functions with T2 annotations: 5 of 10 top functions searched
- T2-past: 5 (v10 import consolidation, setProjectAnnotations expansion, component manifest default change, addon-a11y flake fix, CSF factories re-process skip)
- T2-future: 0 (no deprecation warnings or planned renames surfaced in the 100-issue/100-PR window)

Key finding: A community issue explicitly notes `@storybook/test` deprecation with migration to `storybook/test` in v10, confirming the skill's core value proposition is not hypothetical.

## Validation Results

- Schema: **PASS** (quality score: 100/100)
- Frontmatter: **PASS**
- Body: **PASS** (235 lines, within 500-line budget — no split-body required)
- Security: skipped — SNYK_TOKEN not configured
- Content Quality (tessl): **PASS** (review score: 89%, description 100%, content 73%)
- Metadata: **PASS**

## Quality Score Breakdown

- Frontmatter (30%): 30 | Description (30%): 30 | Body (20%): 20 | Links (10%): 10 | File (10%): 10

## tessl Judge Breakdown

- **Description — 100%:** specificity 3/3, trigger_term_quality 3/3, completeness 3/3, distinctiveness_conflict_risk 3/3
- **Content — 73%:** conciseness 2/3 (expected SKF floor for two-tier + provenance design), actionability 3/3, workflow_clarity 2/3, progressive_disclosure 3/3
- **Review score:** 89% (above the 60% SKF warning floor)

## Description Guard

- Restored: false
- Triggering tool: —
- Original description preserved: —
- Notes: —

## Auto-Fixed Issues

- **Description XML-tag failure on first tessl pass:** tessl's `description_field` deterministic validator rejected the phrase `` `Meta<typeof X>` `` inside the frontmatter description, despite being backticked (skill-check accepts backticked generics; tessl does not). Per step-05 §2a's rule, backticked content should be safe — but tessl applies a stricter rule. Description was rewritten to `"CSF3 named exports with the `satisfies` meta pattern"` which conveys the same information without angle brackets. Re-validation passed (description 100%). **Action item for step-05 §2a:** extend the sanitizer to strip backticked angle-bracket generics from the description too, since tessl overrides the "backtick is safe" rule.

## Applied Structural Fixes (tessl §6b user selected [A])

User chose [A] Apply structural fixes in response to 2 novel tessl suggestions:

1. **"Trim or consolidate provenance tags"** — applied structurally. Consolidated repeated per-line citations in Overview, Quick Start (both code-block tags aggregated into one trailing line), and Architecture (bullets' trailing tags aggregated into one "Sources:" line after the list). Retained all Key API Summary table per-row citations (one per row is already minimal and load-bearing for audit). No provenance information was removed — every distinct `[AST:...]` / `[QMD:...]` / `[EXT:...]` citation still appears. Re-validation: score unchanged (89% review), confirming the consolidation was semantics-preserving.
2. **"Add explicit validation steps to Common Workflows"** — NOT applied. This is a semantic suggestion (new content), not structural. Per §6b gate rule, [A] applies structural only. The `play` function's `expect()` assertions already constitute the validation step (documented verbatim in `references/csf3-patterns.md` Sample 2), and `npm run storybook` / `npx vitest` appear in the CLI section and `references/framework-config.md`. Recording as skipped.

## Dismissed tessl Suggestions

None matched the `tessl-dismissal-rules.md` catalog — both novel suggestions surfaced to the user per §6b.

## Remaining Warnings

- Some extraction entries in provenance-map.json have `source_line: 1` as a placeholder because they were traced via re-export barrels rather than AST line extraction. The source file is accurate; the line is not load-bearing for downstream audit/update workflows as long as hash comparison is used.
- Total coverage of 19% reflects the intentional authoring-focused scope (82 exports documented in SKILL.md+references out of ~430 extracted). The brief deliberately excludes non-authoring infrastructure (CLI, codemods, eslint-plugin, core-server internals).
