---
workflowType: 'test-skill'
skillName: 'uitripled'
skillDir: 'skills/uitripled'
testMode: 'naive'
forgeTier: 'Deep'
testResult: 'pass'
score: '98.7%'
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
**Forge Tier:** Deep

**Mode Rationale:** metadata.json declares `skill_type: "single"` — single source library with self-contained API surface and no cross-references to other skills.

**Analysis Plan:**
- Coverage Check: Documented exports vs metadata export list. Deep tier — structural checks with AST verification where provenance available.
- Coherence Check: Basic structural validation only (no cross-references to verify in naive mode). Reference file existence and internal link integrity.

## Coverage Analysis

**Tier:** Deep
**Source Access:** provenance-map (19 entries: 10 T1, 9 T1-low)
**Source Path:** packages/ (remote — https://github.com/moumen-soliman/uitripled)
**Files Analyzed:** provenance-map (19 entries) + metadata.json (34 exports) → union denominator: 34

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
| generateUniqueSlug | function | yes | unverified | lib/builder-utils.ts | PASS |
| sanitizeSlug | function | yes | unverified | lib/builder-utils.ts | PASS |
| ThemeProvider | function | yes | unverified | theme-provider.tsx:18 | PASS |
| UILibraryProvider | function | yes | unverified | ui-library-provider.tsx:31 | PASS |

### Split-Body Cross-Check

NativeNotchProps appears in SKILL.md body (line 104) and references/native-components.md (line 31):
- **Match:** Both show 10 props (children, collapsedIcon, size, position, draggable, defaultExpanded, expanded, onExpandedChange, onClick, className). Consistent after update-skill remediation.
- `size` type: body uses inline `"sm" | "md" | "lg"`, ref uses `NotchSize` — semantically equivalent, acceptable.

Exports cross-checked: 1 | Mismatches found: 0

### Coverage Summary

- **Exports Found (union):** 34
- **Documented:** 34 (100%)
- **Missing Documentation:** 0
- **Signature Mismatches:** N/A (State 2 — string comparison only, not AST re-parse)
- **Stale Documentation:** 0
- **Split-Body Mismatches:** 0

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 100% |
| Signature Accuracy | N/A (State 2 — no local AST) |
| Type Coverage | N/A (State 2 — no local AST) |

Note: Weight application is deferred to step-05 where all category weights are calculated after external validation availability is known.

Resolved via: provenance-map (10 T1, 9 T1-low). Re-run with local clone to upgrade T1-low entries to full AST verification.

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)

### Structural Findings

| # | Type | Detail | Line |
|---|------|--------|------|
| — | — | No structural issues found | — |

**Structural Issues:** 0

### Reference Consistency (split-body)

| # | Reference File | Export | Issue | SKILL.md Line | Reference Line |
|---|---------------|--------|-------|---------------|---------------|
| — | — | — | No mismatches | — | — |

**Exports Cross-Checked:** 1
**Mismatches Found:** 0

## External Validation

### skill-check
- **Available:** yes
- **Quality Score:** 100/100
- **Errors:** 0
- **Warnings:** 0
- **Diagnostics:** none
- **Breakdown:** Frontmatter 30/30, Description 30/30, Body 20/20, Links 10/10, File 10/10

### tessl
- **Available:** yes
- **Validation:** PASSED
- **Description Score:** 100%
- **Content Score:** 73%
- **Average Score:** 86%
- **Suggestions:**
  - Add validation/verification steps to workflows (e.g., confirm component installed correctly)
  - Trim component catalog table — brief category mention with reference link would save tokens

Note: tessl content score reflects post-split inline content only. This is a split-body skill — Content 73% is expected after extracting 3 Tier 2 sections to references/.

### Combined External Score
- **External Validation Score:** 93%
- **Tools used:** skill-check, tessl

## Completeness Score

### Score Breakdown

| Category | Score | Weight | Weighted |
|----------|-------|--------|----------|
| Export Coverage | 100% | 81.8% | 81.8% |
| Signature Accuracy | N/A | 0% (skipped) | — |
| Type Coverage | N/A | 0% (skipped) | — |
| Coherence | N/A | 0% (naive) | — |
| External Validation | 93% | 18.2% | 16.9% |
| **Total** | | **100%** | **98.7%** |

### Result

**Score:** 98.7%
**Threshold:** 80%
**Result:** **PASS**

**Weight Distribution:** naive (redistributed — coherence weight merged into coverage + external; Signature Accuracy and Type Coverage skipped at State 2)
**Tier Adjustment:** Deep tier — Signature Accuracy and Type Coverage not scored due to State 2 source access (no local AST), weights redistributed proportionally
**External Validators:** both available (skill-check + tessl, fresh run)
**Analysis Confidence:** provenance-map

### Access Degradation Notice

**Resolved via:** provenance-map (10 T1, 9 T1-low)
**Impact:** Signature checks limited to name-matching. Source file:line citations from provenance-map, not live AST. 9 T1-low entries were extracted via source-reading or MCP, not AST.
**Recommendation:** Re-run with local clone to upgrade T1-low entries to full AST verification.

## Gap Report

**Total Gaps:** 3
**Blocking (Critical + High):** 0
**Non-blocking (Medium + Low + Info):** 3

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|-----------------|
| Critical | 0 | — |
| High | 0 | — |
| Medium | 0 | — |
| Low | 0 | — |
| Info | 3 | Optional content and testing improvements |
| **Total** | **3** | |

---

### GAP-001: Workflow validation steps missing

**Severity:** Info
**Category:** Content Quality
**Source:** tessl judge suggestion

**Issue:** Common Workflows section lacks validation checkpoints — no guidance on confirming component installation succeeded or handling `npx uitripled add` failures.

**Remediation:** Add a brief troubleshooting note to the Common Workflows section, e.g., "Verify installation: check that `components/uitripled/{component-id}.tsx` was created."

### GAP-002: Component catalog table verbosity

**Severity:** Info
**Category:** Content Quality
**Source:** tessl judge suggestion

**Issue:** Component Catalog table includes exact counts per category (57 components, 38 sections, etc.) which consumes tokens without aiding agent task completion.

**Remediation:** Consider condensing the catalog table to category names with a reference link. Current format is valid and comprehensive — this is a token optimization, not a correctness issue.

### GAP-003: Discovery testing not performed

**Severity:** Info
**Category:** Discovery
**Source:** Advisory

**Issue:** No discovery testing was performed. The skill has not been validated with realistic, imperfect user prompts.

**Remediation:** Test with 3-5 realistic prompts before export. See Discovery Quality section below.

---

### Discovery Quality

**Description optimization:** tessl description score is 100% — no optimization needed. The description uses appropriate trigger keywords, third-person voice, and negative scope boundaries ("Do NOT use for non-React frameworks or static HTML sites.").

**Discovery testing recommended.** Before export, test the skill with 3-5 realistic prompts phrased the way real users actually talk — with casual language, typos, incomplete context, and implicit references. A skill tested only with clean prompts may fail to trigger in production. Example realistic prompt patterns:
- Vague: "I need some animated UI components for my React project"
- Implicit: "add a notification bell with a badge counter to the header"
- Abbreviated: "run the uitripled thing to install that magnetic hover effect"
