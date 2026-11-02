---
workflowType: 'test-skill'
skillName: 'oms-uitripled'
skillDir: 'skills/oms-uitripled/0.1.0/oms-uitripled'
runId: '20261102T194714Z-aff41a98'
testMode: 'naive'
forgeTier: 'Deep'
hardGate: 'passed'
testResult: 'pass'
score: '100%'
threshold: '80%'
thresholdSource: 'workflow default (80%)'
analysisConfidence: 'full'
toolingStatus: 'ok'
workspaceDrift: 'ok'
health_check_dispatched: true
testDate: '2026-11-02T19:47:14Z'
stepsCompleted: ['init', 'detect-mode', 'coverage-check', 'coherence-check', 'external-validators', 'hard-gate', 'score', 'report']
nextWorkflow: 'export-skill'
---

# Test Report: oms-uitripled

<!--
Each stage writes its section in place of the heading below that it owns and
the placeholder comment under that heading, so every heading occurs once.
Before the result files are written, report.md §4c checks that each heading
occurs exactly once and that no placeholder comment is left: a stage that
skipped its section stops the run there. Do not reorder or delete the
headings or their placeholder comments.

Heading / owning step:
  Test Summary        → detect-mode §2
  Coverage Analysis   → coverage-check §5
  Coherence Analysis  → coherence-check §6
  External Validation → external-validators §5
  (hard gate)         → step-hard-gate reads the gap ledger; it writes the
                        Completeness Score section only when it blocks the run
  Completeness Score  → score §6, or step-hard-gate §3 on a blocked run
  Gap Report          → report §4c, rendered from the gap ledger (with the
                        Discovery Quality subsection)
-->

## Test Summary

**Skill:** oms-uitripled
**Test Mode:** naive
**Forge Tier:** Deep

**Mode Rationale:** metadata.json records `skill_type: single`, so this is an individual skill: naive mode (API-surface coverage; coherence is structural only and not scored).

**Analysis Plan:**
- Coverage Check: every public export the source exposes at the pinned commit a5ffb45 (registry entries, provider/hook exports, `@uitripled/utils` helpers and types) checked against SKILL.md and its references, with AST-backed signature and type verification at Deep tier (ast-grep, gh, qmd, ccc available).
- Coherence Check: structural only: SKILL.md internal links to `references/*.md` resolve, cited names exist, and the reference files are consistent with SKILL.md (no scored coherence category in naive mode).

## Coverage Analysis

**Tier:** Deep
**Source Access:** full
**Source Path:** /home/armel/.skf/workspace/repos/github.com/moumen-soliman/uitripled
**Workspace Layout:** pnpm-workspaces (monorepo, 11 workspaces; the brief curates react-shadcn, registry, uitripled, utils and the docs app pages)
**Denominator:** Stratified scope, denominator: effective_denominator (233 files matched, 327 exports union)
**Denominator Candidates** (stratified-scope audit trail):
- `stats.effective_denominator`: 327  ← chosen on the scalar branch
- `scope.tier_a_include` union: absent
- `scope.include` union: 327
- exports-map subpath union: 426
- root barrel: 19                               (secondary candidate: root-barrel-vs-subpath-union audit)

**Files Analyzed:** 210

### Export Coverage

No per-export table: the scalar denominator (`stats.effective_denominator`) counts the exports without naming them. The summary below gives the counts.

### Coverage Summary

- **Exports Found:** 327
- **Documented:** 330 (100%)
- **Missing Documentation:** 0 (a floored residual: the numerator exceeds the denominator)
- **Signature Mismatches:** 0
- **Stale Documentation:** N/A: the scalar denominator (`stats.effective_denominator`) counts the exports without naming them
- **Numerator Surplus:** 3, uncapped coverage 100.92%
- **Scoped Out by the Brief:** `NativeAvatarExpandDefault` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx), `NativeAvatarExpandDemo` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx), `NativeAvatarExpandExtraLarge` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx), `NativeAvatarExpandLarge` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx), `NativeAvatarExpandNoImage` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx), `NativeAvatarExpandSmall` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx), `NativeAvatarWithNameDefault` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx), `NativeAvatarWithNameDemo` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx), `NativeAvatarWithNameLarge` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx), `NativeAvatarWithNameLeft` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx), `NativeAvatarWithNameNoImage` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx), `NativeAvatarWithNameRight` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx), `NativeAvatarWithNameSmall` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx), `NativeAvatarWithNameTop` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx), `NativeButtonDefault` (packages/components/react-shadcn/src/components/native/demo/native-button-demo.tsx), `NativeButtonDisabled` (packages/components/react-shadcn/src/components/native/demo/native-button-demo.tsx), `NativeButtonGlow` (packages/components/react-shadcn/src/components/native/demo/native-button-demo.tsx), `NativeButtonLoading` (packages/components/react-shadcn/src/components/native/demo/native-button-demo.tsx), `NativeButtonOutline` (packages/components/react-shadcn/src/components/native/demo/native-button-demo.tsx), `NativeDeleteCustomText` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx), `NativeDeleteDefault` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx), `NativeDeleteDemo` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx), `NativeDeleteDisabled` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx), `NativeDeleteLarge` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx), `NativeDeleteNoIcon` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx), `NativeDeleteSmall` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx), `NativeDialogDemo` (packages/components/react-shadcn/src/components/native/demo/native-dialog-demo.tsx), `NativeHoverCardBordered` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeHoverCardCustomButton` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeHoverCardCustomButtonText` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeHoverCardDefault` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeHoverCardDemo` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeHoverCardExtraLarge` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeHoverCardGlass` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeHoverCardLarge` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeHoverCardMinimal` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeHoverCardNoDescription` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeHoverCardNoUsername` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeHoverCardSmall` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeHoverCardWithFallback` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeImageCheckboxDefault` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx), `NativeImageCheckboxDemo` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx), `NativeImageCheckboxExtraLarge` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx), `NativeImageCheckboxGrid` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx), `NativeImageCheckboxLarge` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx), `NativeImageCheckboxSelected` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx), `NativeImageCheckboxSmall` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx), `NativeLikesCounterDefault` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx), `NativeLikesCounterDemo` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx), `NativeLikesCounterGhost` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx), `NativeLikesCounterInteractive` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx), `NativeLikesCounterOutline` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx), `NativeLikesCounterSizes` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx), `NativeLikesCounterSubtle` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx), `NativeLiquidButtonCustomColor` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx), `NativeLiquidButtonDefault` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx), `NativeLiquidButtonDemo` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx), `NativeLiquidButtonError` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx), `NativeLiquidButtonGlow` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx), `NativeLiquidButtonGradient` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx), `NativeLiquidButtonLoading` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx), `NativeLiquidButtonSizes` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx), `NativeLiquidButtonSuccess` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx), `NativeLiquidButtonVariants` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx), `NativeLiquidButtonWave` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx), `NativeLiquidButtonWithProgress` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx), `NativeMagneticDefault` (packages/components/react-shadcn/src/components/native/demo/native-magnetic-demo.tsx), `NativeMagneticDemo` (packages/components/react-shadcn/src/components/native/demo/native-magnetic-demo.tsx), `NativeMagneticLink` (packages/components/react-shadcn/src/components/native/demo/native-magnetic-demo.tsx), `NativeMagneticStrong` (packages/components/react-shadcn/src/components/native/demo/native-magnetic-demo.tsx), `NativeMorphingButtonCustomIcon` (packages/components/react-shadcn/src/components/native/demo/native-morphing-button-demo.tsx), `NativeMorphingButtonDefault` (packages/components/react-shadcn/src/components/native/demo/native-morphing-button-demo.tsx), `NativeMorphingButtonDemo` (packages/components/react-shadcn/src/components/native/demo/native-morphing-button-demo.tsx), `NativeNestedListDemo` (packages/components/react-shadcn/src/components/native/demo/native-nested-list-demo.tsx), `NativeNotchDefault` (packages/components/react-shadcn/src/components/native/demo/native-notch-demo.tsx), `NativeNotchLeftAlign` (packages/components/react-shadcn/src/components/native/demo/native-notch-demo.tsx), `NativeNotchRelative` (packages/components/react-shadcn/src/components/native/demo/native-notch-demo.tsx), `NativeNotificationBellCustomIcon` (packages/components/react-shadcn/src/components/native/demo/native-notification-bell-demo.tsx), `NativeNotificationBellDefault` (packages/components/react-shadcn/src/components/native/demo/native-notification-bell-demo.tsx), `NativeNotificationBellDemo` (packages/components/react-shadcn/src/components/native/demo/native-notification-bell-demo.tsx), `NativeNotificationBellEmpty` (packages/components/react-shadcn/src/components/native/demo/native-notification-bell-demo.tsx), `NativeProfileNotchDefault` (packages/components/react-shadcn/src/components/native/demo/native-profile-notch-demo.tsx), `NativeProfileNotchOverlay` (packages/components/react-shadcn/src/components/native/demo/native-profile-notch-demo.tsx), `NativeStartNowCustomLabels` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowDefault` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowDemo` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowDisabled` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowGradient` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowHeartIcon` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowLarge` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowNoSparkles` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowOutline` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowRocketIcon` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowSmall` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowSolid` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowStarIcon` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowZapIcon` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeTabsDemo` (packages/components/react-shadcn/src/components/native/demo/native-tabs-demo.tsx), `NativeTooltipBlur` (packages/components/react-shadcn/src/components/native/demo/native-tooltip-demo.tsx), `NativeTooltipDemo` (packages/components/react-shadcn/src/components/native/demo/native-tooltip-demo.tsx), `NativeTooltipScale` (packages/components/react-shadcn/src/components/native/demo/native-tooltip-demo.tsx), `NativeTypewriterDefault` (packages/components/react-shadcn/src/components/native/demo/native-typewriter-demo.tsx), `NativeTypewriterDemo` (packages/components/react-shadcn/src/components/native/demo/native-typewriter-demo.tsx), `NativeTypewriterLoop` (packages/components/react-shadcn/src/components/native/demo/native-typewriter-demo.tsx), `NativeTypewriterMultiline` (packages/components/react-shadcn/src/components/native/demo/native-typewriter-demo.tsx), `NativeUserCardDemo` (packages/components/react-shadcn/src/components/native/demo/native-user-card-demo.tsx), `NativeVerifiedBadgeCustomIcon` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx), `NativeVerifiedBadgeDefault` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx), `NativeVerifiedBadgeDemo` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx), `NativeVerifiedBadgeOutlineVariants` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx), `NativeVerifiedBadgeShield` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx), `NativeVerifiedBadgeSizes` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx), `NativeVerifiedBadgeWithLabel` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx), `NativeVerifiedBadgeWithTooltip` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx), `SocialButtonsGlow` (packages/components/react-shadcn/src/components/native/demo/social-login-demo.tsx), `SocialButtonsScale` (packages/components/react-shadcn/src/components/native/demo/social-login-demo.tsx), `SocialButtonsShine` (packages/components/react-shadcn/src/components/native/demo/social-login-demo.tsx), `SocialButtonsSlide` (packages/components/react-shadcn/src/components/native/demo/social-login-demo.tsx)

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 100% |
| Signature Accuracy | 100% |
| Type Coverage | 100% |

### Coverage Notes

- **Extraction:** the recipe runner (ast-grep 0.45.3, `component-library` recipe set) read 233 files in scope at a5ffb45 with status `ok` and no truncation. It reported tree-sitter syntax errors in 10 TSX files (`extraction.readByEye`, for example `components/blog/blog-typography.tsx:200`); the status stayed `ok`, so no by-eye pass ran. 22 names no recipe matched (`extractionGaps`, such as `useTheme`, `cn`, `GAP_VALUES`, `sanitizeSlug`) are on the surface, and the ones the skill documents with a signature were read at their file and line.
- **Inventory:** built in the main thread (no subagent available) from SKILL.md and all nine `references/*.md` files, since SKILL.md's `## Full` sections are pointers: 330 documented names (246 functions, 38 constants, 26 interfaces, 18 types, 2 hooks). The validator's spot-check passed. No export documented in both the SKILL.md body and a reference file contradicts itself (§1b: no split-body mismatch).
- **Signatures:** 127 compared, 127 match (components documented with no parameters, `export function X()`, carry no signature to compare). `ThemeProvider` and `UILibraryProvider` are documented as props tables (`children`, `defaultTheme?: ThemeMode` defaulting to `"system"`), matching `ThemeProviderProps` at `packages/components/react-shadcn/src/components/theme-provider.tsx:13` and `{ children: React.ReactNode }` at `ui-library-provider.tsx:31`; the `useTheme` and `useUILibrary` usage signatures name exactly the fields each returns; `sanitizeSlug`'s documented `string` return is the inferred type of its unannotated arrow (`packages/utils/src/builder-utils.ts:7`).
- **Name collisions on the surface:** `cn` resolves to `packages/components/react-shadcn/src/lib/utils.ts:3` (`cn(...inputs: any[])`, a wrapper that imports `cn as baseCn` from `@uitripled/utils`); the skill documents and cites `packages/utils/src/cn.ts:4` (`cn(...inputs: ClassValue[])`), which matches its documented signature, so the comparison was judged a match. `GridCell` resolves to a component function at `packages/components/react-shadcn/src/components/grid/grid-cell.tsx:14`, which the skill does not document as a component; it documents the `GridCell` interface (`packages/utils/src/grid-utils.ts:5`), whose fields match, so the name counts as documented.
- **Deep tier checks:** `gh api` confirms the pinned commit a5ffb45 exists upstream (committed 2026-03-21); upstream `master` has since moved to 05d1837 (pushed 2026-08-28), drift for audit-skill, outside this pinned-commit test. The documented versions match the source: `@uitripled/react-shadcn` 0.1.0 and `@uitripled/utils` 0.1.0, the `uitripled` CLI 1.1.0 (`packages/uitripled/package.json:3`). All 42 types of the scope.include set are documented (Type Coverage 100%); the documented field lists match their declarations, except that SKILL.md names 3 of the 11 `NativeHoverCardProps` fields as a representative sample and writes `size` as required where the source has `size?` (`native-hover-card-shadcnui.tsx:9`). Re-exports traced: `packages/utils/src/index.ts` star-re-exports `cn`, `grid-utils`, `merge-imports`, `builder-utils` and `types`; `packages/registry/src/index.tsx` re-exports `nativeComponents` and `uiComponents`.
- **Numerator surplus (3):** every one of the 327 scope.include names is documented by name (checked against `surface.json` `sets`); the 3 extra documented names are `add` (`packages/uitripled/src/commands/add.ts:8`) and `fetchComponent` (`packages/uitripled/src/utils/registry.ts:5`), CLI-internal functions no package entry point exports, and `UILibraryContextValue`, a non-exported type at `packages/components/react-shadcn/src/ui-library-provider.tsx:14`. The scalar branch classifies no stale name, so they raise no gap.
- **Guards:** `guards.staleScope` fires: `apps/docs/app/**/page.mdx` and `apps/docs/components/demos/**` match no file at a5ffb45 (no export restored). `guards.deflation` (re-derived 327 against the stored 327, 0%) and `guards.inflation` (scope.include union 327 against 311 provenance entries, 5.14%) do not fire; `guards.umbrella.umbrella` is true (18 of the 19 root-barrel names are re-exports).
- **Numerator ground truth:** skipped (no inflation signature: `stats.exports_documented` 311, `stats.effective_denominator` 327).
- **Metadata coherence:** `stats.exports_public_api` 445 against `exports[].length` 297 diverge 33% (Medium metadata drift), plus the Info multi-denominator note (barrel 445, documented 311). `metadata.json` `exports[]` still lists `RegistryItemType`, which the source does not declare and the skill no longer documents, and omits 32 surface names the skill documents (`ThemeMode`, `UILibrary`, `Component`, `GridCell`, `getGapSliderIndex`, `HeroSection`, `NativeHoverCard`, `Button` among them).
- **Provenance line check:** 311 map entries checked against 297 `exports[]` names: every recorded line is the definition line (0 stale). The helper also lists 14 map entries `exports[]` does not name (`orphaned`), which this section does not score.

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)

### Structural Findings

| # | Type | Severity | Detail | Line |
|---|------|----------|--------|------|
| - | - | - | no finding | - |

**Structural Issues:** 0

Checks with no finding: required sections (§2.1: `description` via `Overview`, `usage` via `Quick Start`, `api_surface` via `Component Catalog`), code fence balance (§2.2: 14 fences, balanced), opening fence language tags (§2.3: none bare), exports used in a usage-family section (§2.4: all 246 function exports are referenced in the usage-family scope or a reference file, `zero_usage` empty), async/sync consistency (§2.5: `fetchComponent`, declared `export async function`, is awaited in its `references/catalog.md` example; `generateGridCode`, sync, is called without `await`; the other 244 function exports appear in no fenced call), table syntax (§2.6: no column drift), Scripts & Assets section (§2.7: no `scripts/` or `assets/` folder).

### Reference Consistency (split-body)

| # | Reference File | Export | Issue | SKILL.md Line | Reference Line |
|---|---------------|--------|-------|---------------|---------------|
| - | - | - | no mismatch | - | - |

**Exports Cross-Checked:** 9 (`ThemeProvider`, `useTheme`, `UILibraryProvider`, `useUILibrary`, `cn`, `ThemeMode`, `UILibrary`, `HeroSection`, `fetchComponent`)
**Mismatches Found:** 0

### Cross-Reference Observations (non-blocking)

Naive mode does not validate references; these statements inside the skill package name content that is not where, or not what, they say, recorded as Info observations:

- `references/integration.md:45` and `references/integration.md:48` import `HeroSection` from `@uitripled/react-shadcn/components/page/hero/hero-section` and `@uitripled/react-shadcn/src/components/page/hero-section`; neither file exists at a5ffb45 (`src/components/page/hero/` holds only `staggered-text.tsx`), and `HeroSection` is defined at `packages/components/react-shadcn/src/components/sections/hero-section.tsx:7`.
- `SKILL.md:185` says every other export of `@uitripled/react-shadcn` `src/` is in the four component reference files with its signature and install id, but `HeroSection` (`src/components/sections/hero-section.tsx:7`, install id `hero-section-shadcnui`, `registry.json:2968`), `NativeHoverCard` (`src/components/native/native-hover-card-shadcnui.tsx:81`, install id `native-hover-card-shadcnui`, `registry.json:3806`) and the `GridCell` component (`src/components/grid/grid-cell.tsx:14`) have no row there; the skill names the first two only in examples.
- `SKILL.md:147` says `NativeHoverCardProps` is documented in `references/types.md`, which has no such entry (the interface is at `packages/components/react-shadcn/src/components/native/native-hover-card-shadcnui.tsx:9`, 11 fields, `size` optional).
- `references/types.md:192` points to a SKILL.md "Full API Reference → Registry schema" table that SKILL.md does not have.
- `references/utils.md:36` calls `packages/components/react-shadcn/src/lib/utils.ts` an identical implementation that removes the need for `@uitripled/utils`; that file imports `cn as baseCn` from `@uitripled/utils` and types its inputs `any[]` (`lib/utils.ts:1-4`).

### Migration & Deprecation (§2b)

Section 4b verification skipped: `evidence-report.md` has no YAML frontmatter, so no pinned `t2_future_count` (Case 4). SKILL.md carries no Migration & Deprecation Warnings section.

## External Validation

### skill-check
- **Available:** yes
- **Quality Score:** 100/100
- **Errors:** 0
- **Warnings:** 0
- **Diagnostics:** none

### Tessl Review
- **Result:** off — set tessl_review_workspace in preferences.yaml to enable

### Combined External Score
- **External Validation Score:** 100%
- **Tools used:** skill-check

## Completeness Score

### Score Breakdown

| Category | Score | Weight | Weighted |
|----------|-------|--------|----------|
| Export Coverage | 100% | 45% | 45% |
| Signature Accuracy | 100% | 25% | 25% |
| Type Coverage | 100% | 20% | 20% |
| Coherence | not scored (naive mode) | 0% | 0% |
| External Validation | 100% | 10% | 10% |
| **Total** | | **100%** | **100%** |

### Result

**Score:** 100%
**Threshold:** 80%
**Result:** **PASS**

**Threshold Source:** workflow default (80%)
**Weight Distribution:** naive (redistributed)
**Tier Adjustment:** none
**External Validators:** skill-check only
**Analysis Confidence:** full
**Tooling Status:** ok

## Gap Report

**Total Gaps:** 9
**Blocking (Critical + High):** 0
**Non-blocking (Medium + Low + Info):** 9

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|------------------|
| Critical | 0 | None |
| High | 0 | None |
| Medium | 2 | Add type definitions, interface docs or the missing section |
| Low | 0 | None |
| Info | 7 | Optional improvements, no action required |
| **Total** | **9** | |

### GAP-001: stale brief scope: scope.include globs match no source file

**Severity:** Medium
**Category:** Coverage (brief-scope-stale)
**Source:** forge-data/oms-uitripled/skill-brief.yaml

**Issue:** the `scope.include` globs `apps/docs/app/**/page.mdx`, `apps/docs/components/demos/**` match no file in the source tested; no root export was restored

**Remediation:** Edit `scope.include` in `forge-data/oms-uitripled/skill-brief.yaml` by hand so each glob matches the files it meant in this version of the source (update-skill does not rewrite an include glob), and add to `scope.exclude` any restored file the brief meant to leave out.

### GAP-002: metadata drift — barrel export counts diverge

**Severity:** Medium
**Category:** Coverage (metadata-drift)
**Source:** skills/oms-uitripled/0.1.0/oms-uitripled/metadata.json

**Issue:** stats.exports_public_api=445, exports[].length=297 → 33% drift

**Remediation:** Recount the exports and correct the diverging counts in `skills/oms-uitripled/0.1.0/oms-uitripled/metadata.json`; update-skill applies it as a metadata update.

### GAP-003: multi-denominator reporting — barrel vs documented surface

**Severity:** Info
**Category:** Coverage (multi-denominator)
**Source:** skills/oms-uitripled/0.1.0/oms-uitripled/metadata.json

**Issue:** barrel=445, documented=311

**Remediation:** No action required: the barrel and the documented surface measure different sets by design, and the report records both counts.

### GAP-004: Subpath import of HeroSection names files that do not exist

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/integration.md:45
**Export:** HeroSection

**Issue:** references/integration.md:45 and :48 import HeroSection from @uitripled/react-shadcn/components/page/hero/hero-section and @uitripled/react-shadcn/src/components/page/hero-section; neither file exists at a5ffb45, HeroSection is defined at packages/components/react-shadcn/src/components/sections/hero-section.tsx:7

**Remediation:** In references/integration.md lines 45 and 48, change the HeroSection import paths to @uitripled/react-shadcn/components/sections/hero-section and @uitripled/react-shadcn/src/components/sections/hero-section, matching packages/components/react-shadcn/src/components/sections/hero-section.tsx:7.

### GAP-005: HeroSection, NativeHoverCard and the GridCell component lack a component reference row

**Severity:** Info
**Category:** Structural (observation)
**Source:** SKILL.md:185

**Issue:** SKILL.md:185 says every other react-shadcn src/ export is in the four component reference files with signature and install id, but HeroSection (src/components/sections/hero-section.tsx:7, hero-section-shadcnui), NativeHoverCard (src/components/native/native-hover-card-shadcnui.tsx:81, native-hover-card-shadcnui) and the GridCell component (src/components/grid/grid-cell.tsx:14) have no signature line or table row there

**Remediation:** Add `export function HeroSection()` with install id @uitripled/hero-section-shadcnui to references/blocks-and-sections.md (Sections and blocks), the NativeHoverCard signature from packages/components/react-shadcn/src/components/native/native-hover-card-shadcnui.tsx:81 with install id @uitripled/native-hover-card-shadcnui to references/native-components.md, and the GridCell component from packages/components/react-shadcn/src/components/grid/grid-cell.tsx:14 to the Grid Generator panels of references/motion-components.md.

### GAP-006: SKILL.md points to a NativeHoverCardProps entry types.md lacks

**Severity:** Info
**Category:** Structural (observation)
**Source:** SKILL.md:147
**Export:** NativeHoverCardProps

**Issue:** SKILL.md:147 says NativeHoverCardProps (imageSrc, name, size) is documented in references/types.md, which has no such entry; the interface at packages/components/react-shadcn/src/components/native/native-hover-card-shadcnui.tsx:9 has 11 fields and size is optional

**Remediation:** Add a `NativeHoverCardProps` subsection to the Component props types of references/types.md with the interface copied from packages/components/react-shadcn/src/components/native/native-hover-card-shadcnui.tsx:9, and write `size?` in SKILL.md:147.

### GAP-007: types.md points to a Registry schema table SKILL.md does not have

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/types.md:192

**Issue:** references/types.md:192 says SKILL.md "Full API Reference → Registry schema" has the table form of the registry.json schema; SKILL.md has no such table

**Remediation:** In references/types.md:192, replace the pointer with the registry.json item fields (name, type, registryDependencies, dependencies, files[].path/target) cited from packages/registry/registry.json, or point to references/catalog.md#registry-types.

### GAP-008: utils.md calls the react-shadcn cn wrapper an identical implementation

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/utils.md:36
**Export:** cn

**Issue:** references/utils.md:36 says packages/components/react-shadcn/src/lib/utils.ts is an identical implementation and @uitripled/utils is not needed; that file imports cn as baseCn from @uitripled/utils and takes ...inputs: any[] (lib/utils.ts:1-4)

**Remediation:** In references/utils.md:36, say that packages/components/react-shadcn/src/lib/utils.ts wraps the @uitripled/utils cn (`cn(...inputs: any[])`, importing `cn as baseCn`), so code that keeps that file depends on @uitripled/utils.

### GAP-009: Discovery testing not performed: subagents unavailable, routing test requires isolated context

**Severity:** Info
**Category:** Discovery (discovery)
**Source:** SKILL.md frontmatter description

**Issue:** The catalog holds 4 skills (oms-cocoindex, oms-cognee, oms-storybook-react-vite, oms-uitripled), but this headless run cannot spawn isolated subagents, and a main-thread routing answer would self-route to the skill under test.

**Remediation:** Re-run test-skill for oms-uitripled in an environment that can spawn subagents so the three realistic prompts are routed against the 4-skill catalog in isolated contexts.

### Discovery Quality

**Discovery Test:** skipped: subagents unavailable, routing test requires isolated context

discovery: skipped, subagents unavailable, routing test requires isolated context (catalog of 4 skills: oms-cocoindex, oms-cognee, oms-storybook-react-vite, oms-uitripled). No description optimization hints: Tessl Review did not run and skill-check flagged no description issue (100/100).

