---
workflowType: 'test-skill'
skillName: 'uitripled'
skillDir: 'skills/uitripled'
testMode: 'naive'
forgeTier: 'Quick'
testResult: 'pass'
score: '91.8%'
threshold: '80%'
analysisConfidence: 'provenance-map'
testDate: '2026-03-29'
stepsCompleted: ['step-01-init', 'step-02-detect-mode', 'step-03-coverage-check', 'step-04-coherence-check', 'step-04b-external-validators', 'step-05-score', 'step-06-report']
nextWorkflow: 'export-skill'
---

# Test Report: uitripled

## Test Summary

**Skill:** uitripled
**Test Mode:** naive
**Forge Tier:** Quick

**Mode Rationale:** metadata.json declares `skill_type: "single"` — single source library with self-contained API surface and no cross-references to other skills.

**Analysis Plan:**
- Coverage Check: Documented exports vs metadata export list. Quick tier — structural checks only (no AST verification of signatures or types).
- Coherence Check: Basic structural validation only (no cross-references to verify in naive mode). Reference file existence and internal link integrity.

## Coverage Analysis

**Tier:** Quick
**Source Access:** provenance-map (10 T1, 7 T1-low)
**Source Path:** packages/ (remote — https://github.com/moumen-soliman/uitripled)
**Files Analyzed:** provenance-map (17 entries) + metadata.json (35 exports) → union denominator: 35

> Provenance-map contains 17 entries but metadata.json lists 35 exports (18 gap). Coverage denominator uses the union.

### Export Coverage

| Export | Type | Documented | Signature | Source Location | Status |
|--------|------|-----------|-----------|-----------------|--------|
| NativeNotchProps | interface | yes | unverified | native-notch-shadcnui.tsx:39 | PASS |
| NativeMagneticProps | interface | yes | unverified | native-magnetic-shadcnui.tsx:14 | PASS |
| NativeHoverCardProps | interface | yes | unverified | native-hover-card-shadcnui.tsx:9 | PASS |
| NativeStartNowProps | interface | yes | unverified | native-start-now-shadcnui.tsx:9 | PASS |
| NativeMorphingButtonProps | interface | yes | unverified | native-morphing-button-shadcnui.tsx:29 | PASS |
| NativeNotificationBellProps | interface | yes | unverified | native-notification-bell-shadcnui.tsx:8 | PASS |
| NativeDeleteProps | interface | yes | unverified | native-delete-shadcnui.tsx:9 | PASS |
| NativeCounterUpProps | interface | yes | unverified | native-counter-up-shadcnui.tsx:7 | PASS |
| NativeProfileNotchProps | interface | yes | unverified | native-profile-notch-shadcnui.tsx:9 | PASS |
| NativeFollowCursorProps | interface | yes | unverified | native-follow-cursor-carbon.tsx:14 | PASS |
| NativeAvatarProps | interface | yes | unverified | metadata-only | PASS |
| NativeAvatarExpandProps | interface | yes | unverified | metadata-only | PASS |
| NativeImageCheckboxProps | interface | yes | unverified | metadata-only | PASS |
| NativeLikesCounterProps | interface | yes | unverified | metadata-only | PASS |
| NativeNestedListProps | interface | yes | unverified | metadata-only | PASS |
| NativeFollowCursorAreaProps | interface | yes | unverified | metadata-only | PASS |
| GridPreviewProps | interface | **no** | — | metadata-only | **FAIL** |
| SocialLoginButtonProps | interface | yes | unverified | metadata-only | PASS |
| UILibrary | type | yes | unverified | types.ts:3 | PASS |
| ComponentCategory | type | yes | unverified | types.ts:12 | PASS |
| Component | type | yes | unverified | types.ts:24 | PASS |
| ThemeMode | type | yes | unverified | metadata-only | PASS |
| NotchSize | type | yes | unverified | metadata-only | PASS |
| SocialProvider | type | yes | unverified | metadata-only | PASS |
| SocialAnimation | type | yes | unverified | metadata-only | PASS |
| InputProps | type | yes | unverified | metadata-only | PASS |
| TextareaProps | type | yes | unverified | metadata-only | PASS |
| LabelProps | type | yes | unverified | metadata-only | PASS |
| PasswordInputProps | type | yes | unverified | metadata-only | PASS |
| cn | function | yes | unverified | cn.ts:4 | PASS |
| mergeComponentImports | function | yes | unverified | merge-imports.ts:5 | PASS |
| generateUniqueSlug | function | **no** | — | metadata-only | **FAIL** |
| sanitizeSlug | function | **no** | — | metadata-only | **FAIL** |
| ThemeProvider | function | yes | unverified | theme-provider.tsx:18 | PASS |
| UILibraryProvider | function | yes | unverified | ui-library-provider.tsx:31 | PASS |

### Split-Body Cross-Check

NativeNotchProps appears in SKILL.md body (line 105) and references/native-components.md (line 31):
- **Mismatch (High):** SKILL.md body shows 9 props (no `onClick`), reference shows 10 props (includes `onClick: (e: React.MouseEvent) => void`). SKILL.md body is authoritative — reference file needs updating, or body needs the missing prop.
- `size` type: body uses inline `"sm" | "md" | "lg"`, ref uses `NotchSize` — semantically equivalent, acceptable.

Exports cross-checked: 1 | Mismatches found: 1

### Coverage Summary

- **Exports Found (union):** 35
- **Documented:** 32 (91.4%)
- **Missing Documentation:** 3 (GridPreviewProps, generateUniqueSlug, sanitizeSlug)
- **Signature Mismatches:** N/A (Quick tier)
- **Stale Documentation:** 0
- **Split-Body Mismatches:** 1 (High — NativeNotchProps onClick prop)

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 91.4% |
| Signature Accuracy | N/A (Quick tier) |
| Type Coverage | N/A (Quick tier) |

Note: Weight application is deferred to step-05 where all category weights are calculated after external validation availability is known.

Resolved via: provenance-map (10 T1, 7 T1-low). Re-run with local clone to upgrade T1-low entries to full AST verification.

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)

### Structural Findings

| # | Type | Detail | Line |
|---|------|--------|------|
| 1 | count_inconsistency | SKILL.md claims "All 18 Props interfaces" but references/native-components.md contains only 17 (GridPreviewProps missing from reference file) | SKILL.md:120 |

**Structural Issues:** 1

### Reference Consistency (split-body)

| # | Reference File | Export | Issue | SKILL.md Line | Reference Line |
|---|---------------|--------|-------|---------------|---------------|
| 1 | references/native-components.md | NativeNotchProps | SKILL.md body shows 9 props (no onClick), reference shows 10 props (includes onClick) | 105 | 31 |

**Exports Cross-Checked:** 1
**Mismatches Found:** 1

## External Validation

External validation: reused from create-skill evidence report (2026-03-29, same session).

### skill-check
- **Available:** yes (cached)
- **Quality Score:** 100/100
- **Errors:** 0
- **Warnings:** 0
- **Diagnostics:** none
- **Breakdown:** Frontmatter 30/30, Description 30/30, Body 20/20, Links 10/10, File 10/10

### tessl
- **Available:** yes (cached)
- **Validation:** PASSED
- **Description Score:** 100%
- **Content Score:** 73%
- **Average Score:** 86.5%
- **Suggestions:**
  - Applied (structural): trim overview metadata, consolidate Props tables to reference
  - Skipped (semantic): add validation steps to workflows — would introduce unverified content

Note: tessl content score reflects post-split inline content only. This is a split-body skill — Content 73% is expected after extracting 3 Tier 2 sections to references/.

### Combined External Score
- **External Validation Score:** 93.3%
- **Tools used:** skill-check (cached), tessl (cached)

## Completeness Score

### Score Breakdown

| Category | Score | Weight | Weighted |
|----------|-------|--------|----------|
| Export Coverage | 91.4% | 81.8% | 74.8% |
| Signature Accuracy | N/A | 0% (skipped) | — |
| Type Coverage | N/A | 0% (skipped) | — |
| Coherence | N/A | 0% (naive) | — |
| External Validation | 93.3% | 18.2% | 17.0% |
| **Total** | | **100%** | **91.8%** |

### Result

**Score:** 91.8%
**Threshold:** 80%
**Result:** **PASS**

**Weight Distribution:** naive (redistributed — coherence weight merged into coverage + external)
**Tier Adjustment:** Quick tier — Signature Accuracy and Type Coverage not scored, weights redistributed proportionally
**External Validators:** both available (skill-check + tessl, cached from create-skill)
**Analysis Confidence:** provenance-map

### Access Degradation Notice

**Resolved via:** provenance-map (10 T1, 7 T1-low)
**Impact:** Signature checks limited to name-matching. Source file:line citations from provenance-map, not live AST. 7 T1-low entries (cn, mergeComponentImports, ThemeProvider, UILibraryProvider + 3 others) were extracted via source-reading, not AST.
**Recommendation:** Re-run with local clone to upgrade T1-low entries to full AST verification.

## Gap Report

**Total Gaps:** 6
**Blocking (Critical + High):** 3
**Non-blocking (Medium + Low + Info):** 3

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|-----------------|
| Critical | 2 | Read source, add function docs to references/full-api-reference.md |
| High | 1 | Add 1 prop row to SKILL.md body table |
| Medium | 1 | Extract GridPreviewProps from source, add to references/native-components.md |
| Low | 1 | Fix count claim in SKILL.md body |
| Info | 1 | Advisory — discovery testing recommended |
| **Total** | **6** | |

---

### GAP-001: generateUniqueSlug — missing function documentation

**Severity:** Critical
**Category:** Coverage
**Source:** metadata.json exports[] — not found in SKILL.md or any references/*.md

**Issue:** `generateUniqueSlug` is listed in metadata.json `exports[]` as a public API function but has no documentation anywhere in SKILL.md body or reference files.

**Remediation:** Add `generateUniqueSlug` documentation to `references/full-api-reference.md` under the Utility Functions section. Include function signature with parameters, return type, and 1-line description. Source: locate in `packages/utils/` via the source repository.

### GAP-002: sanitizeSlug — missing function documentation

**Severity:** Critical
**Category:** Coverage
**Source:** metadata.json exports[] — not found in SKILL.md or any references/*.md

**Issue:** `sanitizeSlug` is listed in metadata.json `exports[]` as a public API function but has no documentation anywhere in SKILL.md body or reference files.

**Remediation:** Add `sanitizeSlug` documentation to `references/full-api-reference.md` under the Utility Functions section. Include function signature with parameters, return type, and 1-line description. Source: locate in `packages/utils/` via the source repository.

### GAP-003: NativeNotchProps split-body mismatch — onClick prop

**Severity:** High
**Category:** Coherence
**Source:** SKILL.md:105 vs references/native-components.md:43

**Issue:** SKILL.md body NativeNotchProps table (9 props) is missing `onClick?: (e: React.MouseEvent) => void` which is present in the reference file (10 props) and in the provenance-map. SKILL.md body is authoritative but incomplete relative to the source.

**Remediation:** Add `onClick` row to the NativeNotchProps table in SKILL.md body at line 117 (before className): `| onClick | \`(e: React.MouseEvent) => void\` | — | no |`

### GAP-004: GridPreviewProps — missing interface documentation

**Severity:** Medium
**Category:** Coverage
**Source:** metadata.json exports[] — not found in SKILL.md or references/native-components.md

**Issue:** `GridPreviewProps` is listed in metadata.json `exports[]` as a public API interface but has no documentation in SKILL.md body or any reference file. Also causes the "18 Props" count claim (GAP-005) to be incorrect since only 17 are documented.

**Remediation:** Extract `GridPreviewProps` interface from the source repository and add a new section to `references/native-components.md` with full Props table. Update the Table of Contents in that file accordingly.

### GAP-005: SKILL.md count claim inconsistency

**Severity:** Low
**Category:** Structural
**Source:** SKILL.md:120

**Issue:** SKILL.md line 120 states "All 18 Props interfaces with full field details" but references/native-components.md contains only 17 Props interfaces (GridPreviewProps is absent).

**Remediation:** Either: (a) add GridPreviewProps to references/native-components.md (see GAP-004), which makes the "18" count correct; or (b) update line 120 to "All 17 Props interfaces" to match the current reference content.

### GAP-006: Discovery testing not performed

**Severity:** Info
**Category:** Discovery
**Source:** Advisory

**Issue:** No discovery testing was performed. The skill has not been validated with realistic, imperfect user prompts.

**Remediation:** Test with 3-5 realistic prompts before export. See Discovery Quality section below.

---

### Discovery Quality

**Description optimization:** tessl description score is 100% — no optimization needed. The description uses appropriate trigger keywords and negative scope boundaries ("Do NOT use for non-React frameworks or static HTML sites.").

**Discovery testing recommended.** Before export, test the skill with 3-5 realistic prompts phrased the way real users actually talk — with casual language, typos, incomplete context, and implicit references. A skill tested only with clean prompts may fail to trigger in production. Example realistic prompt patterns:
- Vague: "I need some animated UI components for my React project"
- Implicit: "add a notification bell with a badge counter to the header"
- Abbreviated: "run the uitripled thing to install that magnetic hover effect"
