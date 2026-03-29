# Evidence Report: storybook-react-vite

**Generated:** 2026-03-29
**Forge Tier:** Deep
**Source:** storybookjs/storybook @ 06cb6a6 (v10.3.0)

## Tool Versions
- ast-grep: 0.42.0
- QMD: 2.0.1
- SKF: 0.8.1

## Extraction Summary
- Files scanned: 27 entry points, ~120 definition files traced
- Exports found: 730+
- Packages covered: 8 (storybook core, @storybook/react-vite, @storybook/react, @storybook/builder-vite, @storybook/addon-a11y, @storybook/addon-docs, @storybook/addon-themes, @storybook/addon-vitest)
- Confidence: T1=0, T1-low=730, T2=10, T3=25

## Extraction Method
- Entry-point-driven extraction via source reading with re-export tracing
- Ephemeral shallow clone from v10.3.0 tag with sparse-checkout
- AST extraction deferred in favor of entry-point tracing (more effective for monorepo barrel-file architecture)
- CCC post-clone discovery attempted but unavailable (indexing timeout)

## Temporal Context
- Collection: storybook-react-vite-temporal (5 files: issues, PRs, releases, changelog, targeted-issues)
- QMD enrichment: 7/10 top functions enriched with 10 T2 annotations

## Documentation Fetch
- 8 URLs fetched (4 original + 4 subpages from storybook.js.org/docs)
- Collection: storybook-react-vite-docs (5 files indexed)

## Version Reconciliation
- Brief version: 10.3.0
- Source version (next branch): 10.4.0-alpha.5 (mismatch)
- Resolution: Re-cloned from v10.3.0 tag — versions match

## Validation Results
- Schema: PASS (quality score: 100/100)
- Frontmatter: PASS (30/30)
- Description: PASS (30/30)
- Body: PASS (20/20) — selective split applied (Tier 2 → references/)
- Links: PASS (10/10)
- File: PASS (10/10)
- Security: skipped (--no-security-scan, SNYK_TOKEN not configured)
- Content Quality (tessl): PASS — 86% average (Description: 100%, Content: 73%)
- Metadata: PASS

## Quality Score Breakdown
- Frontmatter (30%): 30 | Description (30%): 30 | Body (20%): 20 | Links (10%): 10 | File (10%): 10

## Auto-Fixed Issues
- Selective split: Tier 2 sections extracted to references/ (full-api-reference.md, full-type-definitions.md, full-integration-patterns.md)
- Trailing newlines removed
- ThemeVars inline property list trimmed (tessl structural fix)
- Verification steps added to Common Workflows (tessl structural fix)

## Content Quality (tessl)
- Description score: 100% (specificity 3/3, trigger terms 3/3, completeness 3/3, distinctiveness 3/3)
- Content score: 73% (conciseness 2/3, actionability 3/3, workflow clarity 2/3, progressive disclosure 3/3)
- Structural fixes applied by user choice [A]

## Warnings
- CCC semantic discovery unavailable for ephemeral clone (indexing did not complete)
- All extraction is T1-low (source reading) — no AST verification performed due to monorepo barrel-file architecture favoring entry-point tracing
- storybook/test exports ~75 re-exports from @testing-library/dom (instrumented wrappers) — signatures are pass-through
- storybook/internal/types has 200+ type re-exports from 21 sub-modules — documented at summary level
- composeStories known bug #20026 with required props components

## Update Operation — 2026-03-30

**Trigger:** gap-driven (from test-report-storybook-react-vite.md, score 94.9%)
**Forge Tier:** Deep
**Mode:** gap-driven (test report remediation)

### Changes Detected
- Files modified: 0
- Files added: 0
- Files deleted: 0
- Exports affected: 4 (3 critical undocumented, 1 low-severity)

### Exports Remediated
| Export | Package | Confidence | Source |
|--------|---------|-----------|--------|
| `createGlobal` | storybook/theming | T1 | code/core/src/theming/global.ts:94 |
| `createReset` | storybook/theming | T1 | code/core/src/theming/global.ts:24 |
| `onMockCall` | storybook/test | T1 | code/core/src/test/spy.ts:35 |
| `sb` | storybook/test | T1 | code/core/src/test/index.ts:55 |

### Merge Results
- Exports updated: 0
- Exports added: 4 (documentation added to references/full-api-reference.md)
- Exports removed: 0
- [MANUAL] sections preserved: 3
- Conflicts resolved: 0

### Validation Summary
- Spec compliance: DEFERRED (post-write)
- [MANUAL] integrity: PASS (3/3 intact)
- Confidence tiers: PASS (4/4 T1 consistent)
- Provenance: PASS (4 entries updated T1-low → T1)
