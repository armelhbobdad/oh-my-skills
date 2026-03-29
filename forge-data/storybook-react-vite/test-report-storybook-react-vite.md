---
workflowType: 'test-skill'
skillName: 'storybook-react-vite'
skillDir: 'skills/storybook-react-vite'
testMode: 'naive'
forgeTier: 'Deep'
testResult: 'pass'
score: '98.7%'
threshold: '80%'
analysisConfidence: 'provenance-map'
testDate: '2026-03-30'
stepsCompleted: ['step-01-init', 'step-02-detect-mode', 'step-03-coverage-check', 'step-04-coherence-check', 'step-04b-external-validators', 'step-05-score', 'step-06-report']
nextWorkflow: 'export-skill'
---

# Test Report: storybook-react-vite

## Test Summary

**Skill:** storybook-react-vite
**Test Mode:** naive
**Forge Tier:** Deep

**Mode Rationale:** metadata.json declares `skill_type: "single"` — this is an individual skill covering one source library (storybookjs/storybook), with no cross-references to other skills. Naive mode applies.

**Analysis Plan:**
- Coverage Check: documented exports vs source API surface across all 8 packages, with AST-backed signature verification (Deep tier)
- Coherence Check: basic structural validation only (no cross-references to verify in naive mode)

## Coverage Analysis

**Tier:** Deep
**Source Access:** provenance-map (73 entries: 4 T1, 69 T1-low — source-reading extraction at compilation time, 4 upgraded via gh-api-source-verified during update-skill)
**Source Path:** code/ (storybookjs/storybook @ v10.3.0)
**Files Analyzed:** provenance-map entries from 13 source files
**Denominator:** Union of provenance-map (73) + metadata.json exports (67) = 85 unique exports

> Provenance-map contains 73 entries but metadata.json lists 67 exports (12 in metadata not in pmap, 18 in pmap not in metadata). Coverage denominator uses the union (85).

### Export Coverage

| Export | Type | Documented | Source Location | Status |
|--------|------|-----------|-----------------|--------|
| A11yParameters | type | yes | code/addons/a11y/src/params.ts:5 | PASS |
| ArgTypes | component | yes | @storybook/addon-docs/blocks | PASS |
| Canvas | component | yes | @storybook/addon-docs/blocks | PASS |
| Controls | component | yes | @storybook/addon-docs/blocks | PASS |
| DEFAULT_VIEWPORT | const | yes | code/core/src/viewport/index.ts:3 | PASS |
| Description | component | yes | @storybook/addon-docs/blocks | PASS |
| DocsContainer | component | yes | @storybook/addon-docs/blocks | PASS |
| FrameworkOptions | type | yes | code/frameworks/react-vite/src/types.ts:3 | PASS |
| HIGHLIGHT | const | yes | code/core/src/highlight/index.ts:1 | PASS |
| INITIAL_VIEWPORTS | const | yes | code/core/src/viewport/index.ts:1 | PASS |
| MINIMAL_VIEWPORTS | const | yes | code/core/src/viewport/index.ts:2 | PASS |
| Meta | type | yes | code/renderers/react/src/public-types.ts:10 | PASS |
| Primary | component | yes | @storybook/addon-docs/blocks | PASS |
| REMOVE_HIGHLIGHT | const | yes | code/core/src/highlight/index.ts:2 | PASS |
| RESET_HIGHLIGHT | const | yes | code/core/src/highlight/index.ts:3 | PASS |
| ReactRenderer | type | yes | code/renderers/react/src/types.ts:5 | PASS |
| SCROLL_INTO_VIEW | const | yes | code/core/src/highlight/index.ts:4 | PASS |
| Source | component | yes | @storybook/addon-docs/blocks | PASS |
| Stories | component | yes | @storybook/addon-docs/blocks | PASS |
| StoryFn | type | yes | code/renderers/react/src/public-types.ts:38 | PASS |
| StoryObj | type | yes | code/renderers/react/src/public-types.ts:15 | PASS |
| StorybookConfig | type | yes | code/frameworks/react-vite/src/types.ts:8 | PASS |
| Subtitle | component | yes | @storybook/addon-docs/blocks | PASS |
| Tag | type | yes | code/core/src/types/index.ts:40 | PASS |
| ThemeProvider | const | yes | code/core/src/theming/index.ts:8 | PASS |
| ThemeVars | type | yes | code/core/src/theming/types.ts:3 | PASS |
| Title | component | yes | @storybook/addon-docs/blocks | PASS |
| UserOptions | type | yes | code/addons/vitest/src/types.ts:3 | PASS |
| action | function | yes | code/core/src/actions/index.ts:1 | PASS |
| actions | function | yes | code/core/src/actions/index.ts:2 | PASS |
| addons | const | yes | code/core/src/manager-api/index.ts:14 | PASS |
| bail | function | yes | code/builders/builder-vite/src/index.ts:7 | PASS |
| build | function | yes | code/builders/builder-vite/src/index.ts:9 | PASS |
| clearAllMocks | function | yes | code/core/src/test/index.ts:19 | PASS |
| combineTags | function | yes | code/core/src/csf/index.ts:25 | PASS |
| composeConfigs | function | yes | code/core/src/preview-api/index.ts:7 | PASS |
| composeStories | function | yes | code/core/src/preview-api/index.ts:5 | PASS |
| composeStory | function | yes | code/core/src/preview-api/index.ts:6 | PASS |
| configureActions | function | yes | code/core/src/actions/index.ts:3 | PASS |
| convert | function | yes | code/core/src/theming/convert.ts:5 | PASS |
| create | function | yes | code/core/src/theming/create.ts:18 | PASS |
| createGlobal | function | yes | code/core/src/theming/global.ts:94 | PASS |
| createReset | function | yes | code/core/src/theming/global.ts:24 | PASS |
| css | function | yes | code/core/src/theming/index.ts:4 | PASS |
| darken | function | yes | code/core/src/theming/utils.ts:4 | PASS |
| decorateStory | function | yes | code/core/src/preview-api/index.ts:9 | PASS |
| defineMain | function | yes | code/frameworks/react-vite/src/node/index.ts:1 | PASS |
| definePreview | function | yes | code/core/src/csf/index.ts:20 | PASS |
| definePreviewAddon | function | yes | code/core/src/csf/index.ts:21 | PASS |
| ensure | function | yes | code/core/src/theming/ensure.ts:3 | PASS |
| expect | function | yes | code/core/src/instrumenter/index.ts:1 | PASS |
| fn | function | yes | code/core/src/test/index.ts:12 | PASS |
| hasVitePlugins | function | yes | code/builders/builder-vite/src/index.ts:6 | PASS |
| isMeta | function | yes | code/core/src/csf/index.ts:23 | PASS |
| isStory | function | yes | code/core/src/csf/index.ts:22 | PASS |
| lighten | function | yes | code/core/src/theming/utils.ts:3 | PASS |
| mocked | function | yes | code/core/src/test/index.ts:18 | PASS |
| onMockCall | function | yes | code/core/src/test/spy.ts:35 | PASS |
| resetAllMocks | function | yes | code/core/src/test/index.ts:20 | PASS |
| restoreAllMocks | function | yes | code/core/src/test/index.ts:21 | PASS |
| sanitize | function | yes | code/core/src/csf/index.ts:26 | PASS |
| sb | const | yes | code/core/src/test/index.ts:55 | PASS |
| screen | const | yes | code/core/src/test/index.ts:15 | PASS |
| setProjectAnnotations | function | yes | code/core/src/preview-api/index.ts:8 | PASS |
| spyOn | function | yes | code/core/src/test/index.ts:13 | PASS |
| start | function | yes | code/builders/builder-vite/src/index.ts:8 | PASS |
| storybookTest | function | yes | code/addons/vitest/src/index.ts:1 | PASS |
| styled | function | yes | code/core/src/theming/index.ts:3 | PASS |
| themes | const | yes | code/core/src/theming/index.ts:5 | PASS |
| toId | function | yes | code/core/src/csf/index.ts:24 | PASS |
| useArgs | function | yes | code/core/src/preview-api/index.ts:15 | PASS |
| useChannel | function | yes | code/core/src/manager-api/index.ts:12 | PASS |
| useGlobals | function | yes | code/core/src/preview-api/index.ts:16 | PASS |
| useParameter | function | yes | code/core/src/preview-api/index.ts:17 | PASS |
| useStorybookApi | function | yes | code/core/src/manager-api/index.ts:10 | PASS |
| useStorybookState | function | yes | code/core/src/manager-api/index.ts:11 | PASS |
| useTheme | function | yes | code/core/src/theming/index.ts:9 | PASS |
| userEvent | const | yes | code/core/src/test/index.ts:14 | PASS |
| viteFinal | function | yes | @storybook/react-vite/preset | PASS |
| waitFor | function | yes | code/core/src/test/index.ts:17 | PASS |
| withThemeByClassName | function | yes | code/addons/themes/src/index.ts:1 | PASS |
| withThemeByDataAttribute | function | yes | code/addons/themes/src/index.ts:2 | PASS |
| withThemeFromJSXProvider | function | yes | code/addons/themes/src/index.ts:3 | PASS |
| within | function | yes | code/core/src/test/index.ts:16 | PASS |
| withoutVitePlugins | function | yes | code/builders/builder-vite/src/index.ts:5 | PASS |

### Split-Body Consistency

16 exports cross-checked between SKILL.md body and references/ files. No signature mismatches detected. SKILL.md body summaries are consistent with reference file detail.

### Coverage Summary

- **Exports Found:** 85 (union denominator)
- **Documented:** 85 (100%)
- **Missing Documentation:** 0
- **Signature Mismatches:** N/A (State 2 — string comparison only, not semantic AST)
- **Stale Documentation:** 0

### Category Scores

| Category | Score | Note |
|----------|-------|------|
| Export Coverage | 100% | 85/85 documented |
| Signature Accuracy | N/A | State 2 — no local source for AST re-verification |
| Type Coverage | N/A | State 2 — no local source for AST re-verification |

Resolved via: provenance-map (4 T1 gh-api-source-verified, 69 T1-low source-reading). Re-run with local clone to upgrade T1-low entries to full AST verification.

Note: Weight application is deferred to step-05 where all category weights are calculated after external validation availability is known.

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)

### Structural Findings

| # | Type | Detail | Line |
|---|------|--------|------|
| — | — | No structural issues detected | — |

**Structural Issues:** 0

SKILL.md is well-formed: all required sections present (Overview, Quick Start, Key API Summary, Key Types, Architecture, CLI, References), code blocks have language annotations, tables are properly formatted, no broken markdown, no self-contradictions.

### Reference Consistency (split-body)

| # | Reference File | Export | Issue | SKILL.md Line | Reference Line |
|---|---------------|--------|-------|---------------|---------------|
| — | — | No mismatches | — | — | — |

**Exports Cross-Checked:** 16
**Mismatches Found:** 0

### Migration/Deprecation Verification

No T2-future annotations in evidence report. No Migration & Deprecation section in SKILL.md. Match — no issue.

## External Validation

*Reused from create-skill evidence report (same workflow session, SKILL.md unmodified since generation).*

### skill-check
- **Available:** yes (reused)
- **Quality Score:** 100/100
- **Errors:** 0
- **Warnings:** 0
- **Diagnostics:** none

### tessl
- **Available:** yes (reused)
- **Validation:** PASSED
- **Description Score:** 100%
- **Content Score:** 73%
- **Average Score:** 86%
- **Suggestions:** tessl content score reflects post-split inline content only. Use the pre-split tessl score as the content quality baseline.

### Combined External Score
- **External Validation Score:** 93%
- **Tools used:** skill-check (reused), tessl (reused)

## Completeness Score

### Score Breakdown

| Category | Score | Weight | Weighted |
|----------|-------|--------|----------|
| Export Coverage | 100% | 81.82% | 81.82% |
| Signature Accuracy | N/A | 0% | — |
| Type Coverage | N/A | 0% | — |
| Coherence | N/A | 0% | — |
| External Validation | 93.0% | 18.18% | 16.91% |
| **Total** | | **100%** | **98.7%** |

### Result

**Score:** 98.7%
**Threshold:** 80%
**Result:** **PASS**

**Weight Distribution:** naive (redistributed — Signature, Type, Coherence weights → Export Coverage + External Validation)
**Tier Adjustment:** State 2 — Signature Accuracy and Type Coverage not scored (provenance-map only, no local source for AST re-verification)
**External Validators:** both available (reused from evidence report)
**Analysis Confidence:** provenance-map

### Access Degradation Notice

**Resolved via:** provenance-map (4 T1 gh-api-source-verified, 69 T1-low source-reading extraction at compilation time)
**Impact:** Signature checks limited to name-matching. Source file:line citations from provenance-map, not live AST. Export Coverage and name-matching data is high confidence (T1-low extraction from verified v10.3.0 tag, 4 entries upgraded to T1 via gh API during update-skill).
**Recommendation:** Re-run with local clone to upgrade T1-low entries to full AST verification.

## Gap Report

**Total Gaps:** 1
**Blocking (Critical + High):** 0
**Non-blocking (Medium + Low + Info):** 1

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|-----------------|
| Critical | 0 | — |
| High | 0 | — |
| Medium | 0 | — |
| Low | 0 | — |
| Info | 1 | Discovery testing recommendation (advisory) |
| **Total** | **1** | |

### GAP-001: Discovery testing not performed

**Severity:** Info
**Category:** Structural
**Source:** N/A

**Issue:** No discovery testing has been performed. Realistic prompt testing is recommended before export to verify the skill triggers correctly in production.

**Remediation:** N/A — advisory only.

### Discovery Quality

**Description optimization:** tessl description score is 100% — no optimization needed. Description is specific, includes trigger terms, and is distinctive.

**Discovery testing recommended.** Before export, test the skill with 3-5 realistic prompts phrased the way real users actually talk — with casual language, typos, incomplete context, and implicit references. A skill tested only with clean prompts may fail to trigger in production. Example realistic prompt patterns:
- Vague: "help me set up component testing in my react vite project"
- Implicit: "how do I write a story that tests a button click"
- Abbreviated: "add storybook vitest plugin to my config"
