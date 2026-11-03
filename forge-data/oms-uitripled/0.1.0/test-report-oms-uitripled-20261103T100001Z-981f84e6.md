---
workflowType: 'test-skill'
skillName: 'oms-uitripled'
skillDir: 'skills/oms-uitripled/0.1.0/oms-uitripled'
runId: '20261103T100001Z-981f84e6'
testMode: 'naive'
forgeTier: 'Deep'
hardGate: 'blocked'
testResult: 'fail'
score: ''
threshold: '80%'
thresholdSource: 'workflow default (80%)'
analysisConfidence: ''
toolingStatus: 'ok'
workspaceDrift: 'ok'
health_check_dispatched: true
testDate: '2026-11-03T10:00:01Z'
stepsCompleted: ['init', 'detect-mode', 'coverage-check', 'coherence-check', 'external-validators', 'hard-gate', 'report']
nextWorkflow: 'update-skill'
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

**Mode Rationale:** metadata.json records `skill_type: 'single'`, an individual skill, so the test runs in naive mode (API-surface coverage; coherence is structural only and is not a scored category).

**Analysis Plan:**
- Coverage Check: every public export of the uitripled react-shadcn surface checked against SKILL.md and references/ for documentation presence, and, at Deep tier, a strict signature comparison (params: name, type, order, optionality; and the return type) against the source at the pinned commit a5ffb45, plus type coverage.
- Coherence Check: structural only (naive mode): references named in SKILL.md resolve, internal links and examples are consistent; no coherence category in scoring.

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
- **Signature Mismatches:** 1
- **Stale Documentation:** N/A: the scalar denominator (`stats.effective_denominator`) counts the exports without naming them
- **Numerator Surplus:** 3, uncapped coverage 100.92%
- **Scoped Out by the Brief:** `NativeAvatarExpandDefault` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx), `NativeAvatarExpandDemo` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx), `NativeAvatarExpandExtraLarge` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx), `NativeAvatarExpandLarge` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx), `NativeAvatarExpandNoImage` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx), `NativeAvatarExpandSmall` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx), `NativeAvatarWithNameDefault` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx), `NativeAvatarWithNameDemo` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx), `NativeAvatarWithNameLarge` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx), `NativeAvatarWithNameLeft` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx), `NativeAvatarWithNameNoImage` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx), `NativeAvatarWithNameRight` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx), `NativeAvatarWithNameSmall` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx), `NativeAvatarWithNameTop` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx), `NativeButtonDefault` (packages/components/react-shadcn/src/components/native/demo/native-button-demo.tsx), `NativeButtonDisabled` (packages/components/react-shadcn/src/components/native/demo/native-button-demo.tsx), `NativeButtonGlow` (packages/components/react-shadcn/src/components/native/demo/native-button-demo.tsx), `NativeButtonLoading` (packages/components/react-shadcn/src/components/native/demo/native-button-demo.tsx), `NativeButtonOutline` (packages/components/react-shadcn/src/components/native/demo/native-button-demo.tsx), `NativeDeleteCustomText` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx), `NativeDeleteDefault` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx), `NativeDeleteDemo` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx), `NativeDeleteDisabled` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx), `NativeDeleteLarge` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx), `NativeDeleteNoIcon` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx), `NativeDeleteSmall` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx), `NativeDialogDemo` (packages/components/react-shadcn/src/components/native/demo/native-dialog-demo.tsx), `NativeHoverCardBordered` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeHoverCardCustomButton` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeHoverCardCustomButtonText` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeHoverCardDefault` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeHoverCardDemo` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeHoverCardExtraLarge` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeHoverCardGlass` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeHoverCardLarge` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeHoverCardMinimal` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeHoverCardNoDescription` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeHoverCardNoUsername` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeHoverCardSmall` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeHoverCardWithFallback` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeImageCheckboxDefault` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx), `NativeImageCheckboxDemo` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx), `NativeImageCheckboxExtraLarge` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx), `NativeImageCheckboxGrid` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx), `NativeImageCheckboxLarge` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx), `NativeImageCheckboxSelected` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx), `NativeImageCheckboxSmall` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx), `NativeLikesCounterDefault` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx), `NativeLikesCounterDemo` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx), `NativeLikesCounterGhost` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx), `NativeLikesCounterInteractive` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx), `NativeLikesCounterOutline` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx), `NativeLikesCounterSizes` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx), `NativeLikesCounterSubtle` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx), `NativeLiquidButtonCustomColor` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx), `NativeLiquidButtonDefault` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx), `NativeLiquidButtonDemo` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx), `NativeLiquidButtonError` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx), `NativeLiquidButtonGlow` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx), `NativeLiquidButtonGradient` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx), `NativeLiquidButtonLoading` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx), `NativeLiquidButtonSizes` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx), `NativeLiquidButtonSuccess` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx), `NativeLiquidButtonVariants` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx), `NativeLiquidButtonWave` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx), `NativeLiquidButtonWithProgress` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx), `NativeMagneticDefault` (packages/components/react-shadcn/src/components/native/demo/native-magnetic-demo.tsx), `NativeMagneticDemo` (packages/components/react-shadcn/src/components/native/demo/native-magnetic-demo.tsx), `NativeMagneticLink` (packages/components/react-shadcn/src/components/native/demo/native-magnetic-demo.tsx), `NativeMagneticStrong` (packages/components/react-shadcn/src/components/native/demo/native-magnetic-demo.tsx), `NativeMorphingButtonCustomIcon` (packages/components/react-shadcn/src/components/native/demo/native-morphing-button-demo.tsx), `NativeMorphingButtonDefault` (packages/components/react-shadcn/src/components/native/demo/native-morphing-button-demo.tsx), `NativeMorphingButtonDemo` (packages/components/react-shadcn/src/components/native/demo/native-morphing-button-demo.tsx), `NativeNestedListDemo` (packages/components/react-shadcn/src/components/native/demo/native-nested-list-demo.tsx), `NativeNotchDefault` (packages/components/react-shadcn/src/components/native/demo/native-notch-demo.tsx), `NativeNotchLeftAlign` (packages/components/react-shadcn/src/components/native/demo/native-notch-demo.tsx), `NativeNotchRelative` (packages/components/react-shadcn/src/components/native/demo/native-notch-demo.tsx), `NativeNotificationBellCustomIcon` (packages/components/react-shadcn/src/components/native/demo/native-notification-bell-demo.tsx), `NativeNotificationBellDefault` (packages/components/react-shadcn/src/components/native/demo/native-notification-bell-demo.tsx), `NativeNotificationBellDemo` (packages/components/react-shadcn/src/components/native/demo/native-notification-bell-demo.tsx), `NativeNotificationBellEmpty` (packages/components/react-shadcn/src/components/native/demo/native-notification-bell-demo.tsx), `NativeProfileNotchDefault` (packages/components/react-shadcn/src/components/native/demo/native-profile-notch-demo.tsx), `NativeProfileNotchOverlay` (packages/components/react-shadcn/src/components/native/demo/native-profile-notch-demo.tsx), `NativeStartNowCustomLabels` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowDefault` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowDemo` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowDisabled` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowGradient` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowHeartIcon` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowLarge` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowNoSparkles` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowOutline` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowRocketIcon` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowSmall` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowSolid` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowStarIcon` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowZapIcon` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeTabsDemo` (packages/components/react-shadcn/src/components/native/demo/native-tabs-demo.tsx), `NativeTooltipBlur` (packages/components/react-shadcn/src/components/native/demo/native-tooltip-demo.tsx), `NativeTooltipDemo` (packages/components/react-shadcn/src/components/native/demo/native-tooltip-demo.tsx), `NativeTooltipScale` (packages/components/react-shadcn/src/components/native/demo/native-tooltip-demo.tsx), `NativeTypewriterDefault` (packages/components/react-shadcn/src/components/native/demo/native-typewriter-demo.tsx), `NativeTypewriterDemo` (packages/components/react-shadcn/src/components/native/demo/native-typewriter-demo.tsx), `NativeTypewriterLoop` (packages/components/react-shadcn/src/components/native/demo/native-typewriter-demo.tsx), `NativeTypewriterMultiline` (packages/components/react-shadcn/src/components/native/demo/native-typewriter-demo.tsx), `NativeUserCardDemo` (packages/components/react-shadcn/src/components/native/demo/native-user-card-demo.tsx), `NativeVerifiedBadgeCustomIcon` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx), `NativeVerifiedBadgeDefault` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx), `NativeVerifiedBadgeDemo` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx), `NativeVerifiedBadgeOutlineVariants` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx), `NativeVerifiedBadgeShield` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx), `NativeVerifiedBadgeSizes` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx), `NativeVerifiedBadgeWithLabel` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx), `NativeVerifiedBadgeWithTooltip` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx), `SocialButtonsGlow` (packages/components/react-shadcn/src/components/native/demo/social-login-demo.tsx), `SocialButtonsScale` (packages/components/react-shadcn/src/components/native/demo/social-login-demo.tsx), `SocialButtonsShine` (packages/components/react-shadcn/src/components/native/demo/social-login-demo.tsx), `SocialButtonsSlide` (packages/components/react-shadcn/src/components/native/demo/social-login-demo.tsx)

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 100% |
| Signature Accuracy | 99.62% |
| Type Coverage | 100% |

### Coverage Notes

- **Extraction:** the recipe runner (ast-grep 0.45.3, `component-library` recipe set) read 233 files in scope at a5ffb45 with status `ok` and no truncation. It reported tree-sitter syntax errors in 10 TSX files (`extraction.readByEye`); the status stayed `ok`, so no by-eye pass ran. 22 names no recipe matched (`extractionGaps`: `cn`, `useTheme`, `useUILibrary`, `sanitizeSlug`, `GAP_VALUES`, the grid and builder helpers, the registry arrays, `THEME_STORAGE_KEY`, `uiLibraryLabels`, `bentoPresets`) are on the surface; each one the skill documents with a signature was read at its file and line.
- **Inventory:** built in the main thread (this session has no subagent tool), from SKILL.md and all nine `references/*.md` files, since SKILL.md's `## Full` sections are pointers: 330 documented names (221 functions, 63 constants, 26 interfaces, 18 types, 2 hooks). Each declaration a reference signature block writes became that export's documented signature as written: function and arrow declarations as `params` (and `return_type` where the skill writes one), `const X = …` component declarations (forwardRef components, primitive aliases) as `usage_signature`, and a documented `()` as `params: []` (documented as taking none). The validator's schema check and spot-check passed. No export documented in both the SKILL.md body and a reference file contradicts itself (§1b: no split-body mismatch).
- **Signatures (strict comparison):** 266 documented signatures compared, in the main thread, against the full declaration in the source file of each check (for the 72 checks whose surface line is an `export { … }` list or one of its entries, the declaration in that same file), under the step's rule as written: params by name, type, order and optionality, and the return type, with an omitted optional parameter a mismatch and no added leniency for prop lists, omitted optional or keyword parameters, or return types. 265 match, 1 differs: `cn`, whose surface record is the react-shadcn wrapper `export function cn(...inputs: any[])` (`packages/components/react-shadcn/src/lib/utils.ts:3`), against the documented `cn(...inputs: ClassValue[]): string`. Every component the skill documents with a destructured props list writes the same bindings, defaults, rest element and props type as its source declaration, so no prop is left out. 117 of the 266 are documented `()` signatures (components that take no props), each matching a source `()`; of the other 149, 148 match. Four calls are borderline matches: `ThemeProvider` (props table against the non-exported alias `ThemeProviderProps`; `defaultTheme`'s optionality given by the Default column, not by `?`), `useTheme` (the usage form names exactly the five returned fields, with no field types), `useUILibrary` (the return type text matches `UILibraryContextValue`, but the source's `UILibrary` is the 3-member react-shadcn type at `src/types.ts:1`, which `references/setup.md:96` and `SKILL.md:136` describe as a runtime-only restriction of the 4-member type) and `sanitizeSlug` (documented `=> string`, the source arrow infers it). `add` and `fetchComponent` carry signatures but are not on the surface, so they were not scored; read by eye, both match (`packages/uitripled/src/commands/add.ts:8`, `packages/uitripled/src/utils/registry.ts:5`).
- **Name collisions on the surface:** the surface keeps one record for each name. `cn` resolves to the react-shadcn wrapper (above), not to the `@uitripled/utils` `cn` the skill documents and cites (`packages/utils/src/cn.ts:4`, `cn(...inputs: ClassValue[])`, which matches). `references/utils.md:36` calls the wrapper an identical implementation and `references/integration.md:54` imports it. `GridCell` resolves to a component function at `packages/components/react-shadcn/src/components/grid/grid-cell.tsx:14`, which the skill does not document as a component; the skill documents the `GridCell` interface (`packages/utils/src/grid-utils.ts:5`), whose fields match, so the name counts as documented. The grid helpers resolve to `packages/components/react-shadcn/src/lib/grid-utils.ts`, which is byte-identical to `packages/utils/src/grid-utils.ts`, as `references/utils.md:82` says.
- **Deep tier checks:** `gh api` confirms the pinned commit a5ffb45 exists upstream (committed 2026-03-21); upstream `master` has moved to 05d1837 (2026-08-28), drift for audit-skill, outside this pinned-commit test. The documented versions match the source: `@uitripled/react-shadcn` 0.1.0, `@uitripled/utils` 0.1.0, the `uitripled` CLI 1.1.0 (`packages/uitripled/package.json:3`). All 42 types of the scope.include set are documented (Type Coverage 100%). The documented member lists match their declarations, except `NativeHoverCardProps`: SKILL.md:147 names 3 of its 11 fields as a representative sample and writes `size` as required, where the source has `size?` (`native-hover-card-shadcnui.tsx:9`). Re-exports traced: `packages/utils/src/index.ts` star-re-exports `cn`, `grid-utils`, `merge-imports`, `builder-utils` and `types`; `packages/registry/src/index.tsx` re-exports `nativeComponents` and `uiComponents` and defines `componentsRegistry`; `packages/components/react-shadcn/src/index.ts` is `export {};`.
- **Numerator surplus (3):** every one of the 327 scope.include names is documented by name (checked against `surface.json` `sets`). The 3 extra documented names are `add` and `fetchComponent`, CLI-internal functions no package entry point exports, and `UILibraryContextValue`, a non-exported type (`packages/components/react-shadcn/src/ui-library-provider.tsx:14`). The scalar branch classifies no stale name, so they raise no gap.
- **Guards:** `guards.staleScope` fires: `apps/docs/app/**/page.mdx` and `apps/docs/components/demos/**` match no file at a5ffb45 (no export restored). `guards.deflation` (re-derived 327 against the stored 327, 0%) and `guards.inflation` (scope.include union 327 against 311 provenance entries, 5.14%) do not fire; `guards.umbrella.umbrella` is true (18 of the 19 root-barrel names are re-exports).
- **Numerator ground truth:** skipped (no inflation signature: `stats.exports_documented` 311, `stats.effective_denominator` 327).
- **Metadata coherence:** `stats.exports_public_api` 445 against `exports[].length` 297 diverge 33% (Medium metadata drift), plus the Info multi-denominator note (barrel 445, documented 311).
- **Provenance line check:** 311 map entries checked against 297 `exports[]` names: every recorded line is the definition line (0 stale). The helper also lists 14 map entries `exports[]` does not name (`orphaned`), which this section does not score.

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)

### Structural Findings

| # | Type | Severity | Detail | Line |
|---|------|----------|--------|------|
| - | - | - | no finding | - |

**Structural Issues:** 0

Checks with no finding: required sections (§2.1: `description` via `Overview`, `usage` via `Quick Start`, `api_surface` via `Component Catalog`), code fence balance (§2.2: 14 fences, balanced), opening fence language tags (§2.3: none bare), exports used in a usage-family section (§2.4: all 221 function exports are referenced in the usage-family scope or a reference file, `zero_usage` empty), async/sync consistency (§2.5: `fetchComponent`, declared `export async function`, is awaited in its `references/catalog.md:123` example; `generateGridCode`, a sync arrow returning `string`, is called without `await` at `references/utils.md:101`; the other 219 function exports appear in no fenced call), table syntax (§2.6: no column drift), Scripts & Assets section (§2.7: no `scripts/` or `assets/` folder).

### Reference Consistency (split-body)

| # | Reference File | Export | Issue | SKILL.md Line | Reference Line |
|---|---------------|--------|-------|---------------|---------------|
| - | - | - | no mismatch | - | - |

**Exports Cross-Checked:** 9 (`ThemeProvider`, `useTheme`, `UILibraryProvider`, `useUILibrary`, `cn`, `ThemeMode`, `UILibrary`, `HeroSection`, `fetchComponent`)
**Mismatches Found:** 0

### Cross-Reference Observations (non-blocking)

Naive mode does not validate references; these statements inside the skill package name content that is not where, or not what, they say, recorded as Info observations (GAP-005 to GAP-010):

- `references/integration.md:45` and `:48` import `HeroSection` from `@uitripled/react-shadcn/components/page/hero/hero-section` and `@uitripled/react-shadcn/src/components/page/hero-section`; neither file exists at a5ffb45 (`src/components/page/hero/` holds only `staggered-text.tsx`), and `HeroSection` is defined at `packages/components/react-shadcn/src/components/sections/hero-section.tsx:7`.
- `SKILL.md:185` says every other export of `@uitripled/react-shadcn` `src/` is in the four component reference files with its signature and install id, but `HeroSection`, `NativeHoverCard` and the `GridCell` component (`src/components/grid/grid-cell.tsx:14`) have no row there; the skill names the first two only in examples.
- `SKILL.md:147` says `NativeHoverCardProps` is documented in `references/types.md`, which has no such entry (the interface is at `native-hover-card-shadcnui.tsx:9`, 11 fields, `size` optional).
- `references/types.md:192` points to a SKILL.md "Full API Reference → Registry schema" table that SKILL.md does not have.
- `references/utils.md:36` calls `packages/components/react-shadcn/src/lib/utils.ts` an identical implementation that removes the need for `@uitripled/utils`; that file imports `cn as baseCn` from `@uitripled/utils` and types its inputs `any[]` (`lib/utils.ts:1-4`).
- `references/setup.md:96` and `SKILL.md:136` call the 3-value `UILibrary` of the provider a runtime restriction; it is the type itself (`packages/components/react-shadcn/src/types.ts:1`, imported at `ui-library-provider.tsx:3`), so `setSelectedLibrary("react")` does not type-check.

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

**Result:** **FAIL**, not scored: the hard gate blocked this run on 1 Critical or High gap(s), listed first in the Gap Report.

## Gap Report

**Total Gaps:** 10
**Blocking (Critical + High):** 1
**Non-blocking (Medium + Low + Info):** 9

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|------------------|
| Critical | 1 | Read the source code and write or correct the documentation |
| High | 0 | None |
| Medium | 2 | Add type definitions, interface docs or the missing section |
| Low | 0 | None |
| Info | 7 | Optional improvements, no action required |
| **Total** | **10** | |

### GAP-001: Signature mismatch: cn

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** packages/components/react-shadcn/src/lib/utils.ts:3
**Export:** cn

**Issue:** documented `cn(...inputs: ClassValue[]): string`, source `cn(...inputs: any[]) (no return annotation; returns baseCn(...inputs), the @uitripled/utils cn, so string)`: parameter 'inputs' type differs: source any[], documented ClassValue[]. The declaration at this line is the react-shadcn wrapper (lib/utils.ts imports cn as baseCn from @uitripled/utils); the skill documents and cites the @uitripled/utils cn (packages/utils/src/cn.ts:4, (...inputs: ClassValue[]), which matches) and calls this file an identical implementation (references/utils.md:36), importing it in references/integration.md:54

**Remediation:** Update the documented signature of `cn` from `cn(...inputs: ClassValue[]): string` to `cn(...inputs: any[]) (no return annotation; returns baseCn(...inputs), the @uitripled/utils cn, so string)`, the signature the source defines at `packages/components/react-shadcn/src/lib/utils.ts:3`.

### GAP-002: stale brief scope: scope.include globs match no source file

**Severity:** Medium
**Category:** Coverage (brief-scope-stale)
**Source:** forge-data/oms-uitripled/skill-brief.yaml

**Issue:** the `scope.include` globs `apps/docs/app/**/page.mdx`, `apps/docs/components/demos/**` match no file in the source tested; no root export was restored

**Remediation:** Edit `scope.include` in `forge-data/oms-uitripled/skill-brief.yaml` by hand so each glob matches the files it meant in this version of the source (update-skill does not rewrite an include glob), and add to `scope.exclude` any restored file the brief meant to leave out.

### GAP-003: metadata drift — barrel export counts diverge

**Severity:** Medium
**Category:** Coverage (metadata-drift)
**Source:** skills/oms-uitripled/0.1.0/oms-uitripled/metadata.json

**Issue:** stats.exports_public_api=445, exports[].length=297 → 33% drift

**Remediation:** Recount the exports and correct the diverging counts in `skills/oms-uitripled/0.1.0/oms-uitripled/metadata.json`; update-skill applies it as a metadata update.

### GAP-004: multi-denominator reporting — barrel vs documented surface

**Severity:** Info
**Category:** Coverage (multi-denominator)
**Source:** skills/oms-uitripled/0.1.0/oms-uitripled/metadata.json

**Issue:** barrel=445, documented=311

**Remediation:** No action required: the barrel and the documented surface measure different sets by design, and the report records both counts.

### GAP-005: Subpath import of HeroSection names files that do not exist

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/integration.md:45
**Export:** HeroSection

**Issue:** references/integration.md:45 and :48 import HeroSection from @uitripled/react-shadcn/components/page/hero/hero-section and @uitripled/react-shadcn/src/components/page/hero-section; neither file exists at a5ffb45 (src/components/page/hero/ holds only staggered-text.tsx); HeroSection is defined at packages/components/react-shadcn/src/components/sections/hero-section.tsx:7

**Remediation:** In references/integration.md lines 45 and 48, change the HeroSection import paths to @uitripled/react-shadcn/components/sections/hero-section and @uitripled/react-shadcn/src/components/sections/hero-section, matching packages/components/react-shadcn/src/components/sections/hero-section.tsx:7.

### GAP-006: HeroSection, NativeHoverCard and the GridCell component lack a component reference row

**Severity:** Info
**Category:** Structural (observation)
**Source:** SKILL.md:185

**Issue:** SKILL.md:185 says every other react-shadcn src/ export is in the four component reference files with its signature and install id, but HeroSection (src/components/sections/hero-section.tsx:7, install id hero-section-shadcnui), NativeHoverCard (src/components/native/native-hover-card-shadcnui.tsx:81, install id native-hover-card-shadcnui) and the GridCell component (src/components/grid/grid-cell.tsx:14) have no signature line or table row there; the skill names the first two only in examples

**Remediation:** Add `export function HeroSection()` with install id @uitripled/hero-section-shadcnui to the Sections and blocks list of references/blocks-and-sections.md, the NativeHoverCard signature from packages/components/react-shadcn/src/components/native/native-hover-card-shadcnui.tsx:81 with install id @uitripled/native-hover-card-shadcnui to references/native-components.md, and the GridCell component from packages/components/react-shadcn/src/components/grid/grid-cell.tsx:14 to the Grid Generator panels of references/motion-components.md.

### GAP-007: SKILL.md points to a NativeHoverCardProps entry types.md lacks

**Severity:** Info
**Category:** Structural (observation)
**Source:** SKILL.md:147
**Export:** NativeHoverCardProps

**Issue:** SKILL.md:147 says NativeHoverCardProps (with imageSrc, name, size: "sm"|"md"|"lg"|"xl") is documented in references/types.md, which has no such entry; the interface is at packages/components/react-shadcn/src/components/native/native-hover-card-shadcnui.tsx:9 with 11 fields, and size is optional there (size?)

**Remediation:** Add a NativeHoverCardProps entry to the Component props types section of references/types.md, copied from packages/components/react-shadcn/src/components/native/native-hover-card-shadcnui.tsx:9 (11 fields, size optional), and change `size:` to `size?:` in SKILL.md line 147.

### GAP-008: types.md points to a SKILL.md Registry schema table that does not exist

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/types.md:192

**Issue:** references/types.md:192 sends the reader to SKILL.md "Full API Reference -> Registry schema" for the registry.json table form; SKILL.md's Full API Reference section has no such table

**Remediation:** In references/types.md line 192, replace the pointer with the registry.json entry fields (type, registryDependencies, dependencies, files) read from packages/registry/registry.json, or remove the sentence that names the SKILL.md table.

### GAP-009: utils.md calls the react-shadcn cn an identical implementation

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/utils.md:36
**Export:** cn

**Issue:** references/utils.md:36 says packages/components/react-shadcn/src/lib/utils.ts ships an identical cn and removes the need for @uitripled/utils; that file is a wrapper that imports cn as baseCn from @uitripled/utils and types its inputs any[] (lib/utils.ts:1-4)

**Remediation:** In references/utils.md line 36, say that packages/components/react-shadcn/src/lib/utils.ts defines `cn(...inputs: any[])`, a wrapper that calls the @uitripled/utils cn it imports, so the copied helper still depends on @uitripled/utils.

### GAP-010: The react-shadcn UILibrary restriction is described as runtime-only

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/setup.md:96
**Export:** useUILibrary

**Issue:** references/setup.md:96 and SKILL.md:136 say UILibraryProvider and useUILibrary reach only shadcnui, baseui and carbon at runtime even though the @uitripled/utils UILibrary includes react; the provider imports the 3-member UILibrary of packages/components/react-shadcn/src/types.ts:1 (ui-library-provider.tsx:3), so setSelectedLibrary("react") is a type error, not only a runtime limit

**Remediation:** In references/setup.md line 96 and SKILL.md line 136, say that useUILibrary's UILibrary is the 3-member type of packages/components/react-shadcn/src/types.ts:1 ("shadcnui" | "baseui" | "carbon"), imported at ui-library-provider.tsx:3, so the restriction is in the type.

### Discovery Quality

**Discovery Test:** not run: the hard gate blocked the run
