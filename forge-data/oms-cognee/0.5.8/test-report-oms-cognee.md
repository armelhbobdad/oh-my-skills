---
workflowType: 'test-skill'
skillName: 'oms-cognee'
skillDir: 'skills/oms-cognee/0.5.8/oms-cognee'
testMode: 'naive'
forgeTier: 'Deep'
testResult: 'pass'
score: '97.65%'
threshold: '80%'
analysisConfidence: 'full'
testDate: '2026-04-10'
stepsCompleted: ['step-01-init', 'step-02-detect-mode', 'step-03-coverage-check', 'step-04-coherence-check', 'step-04b-external-validators', 'step-05-score', 'step-06-report']
nextWorkflow: 'export-skill'
---

# Test Report: oms-cognee

## Test Summary

- **Skill:** oms-cognee
- **Version:** 0.5.8
- **Skill Type:** single
- **Test Mode:** naive
- **Path:** `skills/oms-cognee/0.5.8/oms-cognee/`
- **Source:** [topoteretes/cognee](https://github.com/topoteretes/cognee) @ `v0.5.8` (commit `b51dcce`)
- **Source clone:** `/home/armel/.skf/workspace/repos/github.com/topoteretes/cognee`
- **Forge Tier:** Deep (ast-grep + ccc + QMD + gh)
- **Test Date:** 2026-04-10
- **Frontmatter validation:** PASS (agentskills.io spec)

**Mode Rationale:** `skill_type: single` in metadata.json — self-contained library wrap of `cognee/__init__.py`. No cross-skill integration patterns to validate.

**Analysis Plan:**
- Coverage Check: documented exports vs AST-derived public API of `cognee/__init__.py` (Deep tier → ast-grep)
- Coherence Check: basic structural validation only (sections, citations format, reference file linkage)
- External Validators: `skf-validate-output.py` structural lint + citation check
- Scoring: naive-mode weight distribution (no coherence category)

## Coverage Analysis

**Tier:** Deep (ast-grep + gh + QMD available)
**Source Access:** `full` (State 1 — local clone at `/home/armel/.skf/workspace/repos/github.com/topoteretes/cognee`)
**Analysis Confidence:** T1 (AST-verified against v0.5.8 @ `b51dcce`)
**Denominator:** 25 top-level public exports in `cognee/__init__.py` (matches `metadata.json` `stats.exports_public_api`)
**Files Analyzed:** 23 source files backing the 25 public exports + entry point
**Baseline:** provenance-map.json (26 entries, 25 public + `visualization_server` helper) cross-checked against live source via citation spot-check

### Export Coverage

| Export | Type | In SKILL.md | In references/ | Signature | Description | Citation | Status |
|---|---|---|---|---|---|---|---|
| `add` | async fn | yes (L96) | full-api, core-workflow | yes | yes | `[AST:cognee/api/v1/add/add.py:L21]` | PASS |
| `delete` | async fn | yes (L114) | full-api | yes | yes (deprecated notice) | `[AST:cognee/api/v1/delete/delete.py:L10]` | PASS |
| `cognify` | async fn | yes (L97) | full-api, core-workflow | yes | yes | `[AST:cognee/api/v1/cognify/cognify.py:L44]` | PASS |
| `search` | async fn | yes (L98) | full-api, core-workflow | yes | yes | `[AST:cognee/api/v1/search/search.py:L27]` | PASS |
| `memify` | async fn | yes (L99) | full-api | yes | yes | `[AST:cognee/modules/memify/memify.py:L25]` | PASS |
| `update` | async fn | yes (L100) | full-api, core-workflow | yes | yes | `[AST:cognee/api/v1/update/update.py:L12]` | PASS |
| `run_custom_pipeline` | async fn | yes (L101) | full-api, pipelines-and-datapoints | yes | yes | `[AST:.../run_custom_pipeline.py:L14]` | PASS |
| `config` | class (ns) | yes (L104) | full-api, config | yes | yes | `[AST:cognee/api/v1/config/config.py:L18]` | PASS |
| `datasets` | class (ns) | yes (L103) | full-api | yes | yes | `[AST:cognee/api/v1/datasets/datasets.py:L25]` | PASS |
| `prune` | class (ns) | yes (L102) | full-api | yes | yes | `[AST:cognee/api/v1/prune/prune.py:L4]` | PASS |
| `SearchType` | enum | yes (L105, L123) | full-api, core-workflow | yes (14 modes) | yes | `[AST:cognee/modules/search/types/SearchType.py:L4]` | PASS |
| `visualize_graph` | async fn | yes (L106) | full-api | yes | yes | `[AST:cognee/api/v1/visualize/visualize.py:L17]` | PASS |
| `start_visualization_server` | module | yes (L117) | — | yes | yes (Migration warning) | `[AST:.../start_visualization_server.py:L6]` | PASS |
| `cognee_network_visualization` | async fn | **no** | full-api | yes | yes | `[AST:.../cognee_network_visualization.py:L22]` | WARN |
| `start_ui` | sync fn | yes (L116) | full-api | yes | yes (Migration warning) | `[AST:cognee/api/v1/ui/ui.py:L369]` | PASS |
| `session` | module | **no** | full-api | yes | yes | `[AST:cognee/api/v1/session/session.py:L1]` | WARN |
| `pipelines` | module | yes (L108) | full-api, pipelines-and-datapoints | yes (Task, run_tasks, run_tasks_parallel, run_pipeline) | yes | `[AST:cognee/pipelines.py:L5]` | PASS |
| `low_level` | module | yes (L109) | full-api, pipelines-and-datapoints | yes (DataPoint, setup) | yes | `[AST:cognee/low_level.py:L1]` | PASS |
| `run_migrations` | async fn | yes (L110) | full-api | yes | yes | `[AST:cognee/run_migrations.py:L16]` | PASS |
| `enable_tracing` | sync fn | yes (L107) | full-api | yes | yes | `[AST:.../trace_context.py:L16]` | PASS |
| `disable_tracing` | sync fn | yes (L107) | full-api | yes | yes | `[AST:.../trace_context.py:L27]` | PASS |
| `get_last_trace` | sync fn | yes (L107) | full-api | yes | yes | `[AST:.../trace_context.py:L65]` | PASS |
| `get_all_traces` | sync fn | yes (L107) | full-api | yes | yes | `[AST:.../trace_context.py:L76]` | PASS |
| `clear_traces` | sync fn | yes (L107) | full-api | yes | yes | `[AST:.../trace_context.py:L85]` | PASS |
| `__version__` | variable | **no** | **no** | no | no | — | **FAIL** |

### Coverage Summary

- **Public API exports (denominator):** 25
- **Documented anywhere (body + references):** 24 (96%)
- **Documented in SKILL.md body:** 22
- **In references only (not body):** 2 — `session`, `cognee_network_visualization`
- **Missing entirely:** 1 — `__version__`
- **Signature mismatches:** 0 (all 24 documented signatures match provenance-map byte-for-byte)
- **Stale docs:** 0 (no phantom exports)
- **Deprecated exports properly flagged:** 1/1 (`delete`)

### Citation Spot-Check (7/7 resolved)

| Citation | Resolved | Notes |
|---|---|---|
| `[AST:cognee/api/v1/add/add.py:L21]` | ✓ | `async def add(` at L21 |
| `[AST:cognee/api/v1/cognify/cognify.py:L44]` | ✓ | `async def cognify(` at L44 |
| `[AST:cognee/api/v1/search/search.py:L27]` | ✓ | `async def search(` at L27 |
| `[AST:cognee/modules/memify/memify.py:L25]` | ✓ | `async def memify(` at L25 |
| `[AST:cognee/api/v1/visualize/visualize.py:L17]` | ✓ | `async def visualize_graph(...)` at L17 |
| `[AST:cognee/modules/search/types/SearchType.py:L4]` | ✓ | `class SearchType(str, Enum)` at L4, all 14 modes present |
| `[AST:cognee/api/v1/config/config.py:L18]` | ✓ | `class config:` at L18 |

### Signature Fidelity Note

Provenance-map entries are all `signature_source: "T1"` (AST-extracted at compile time). SKILL.md's "Key API Summary" table is deliberately abbreviated ("Key params"), while the full parameter lists in `references/full-api-reference.md` / `core-workflow.md` / `pipelines-and-datapoints.md` match the provenance-map exactly. This is a summary-vs-full-ref pattern, not a mismatch.

### Category Scores (pre-weighting)

| Category | Score | Basis |
|----------|-------|-------|
| Export Coverage | 96% | 24/25 documented (1 missing: `__version__`) |
| Signature Accuracy | 100% | 24/24 documented signatures match provenance |
| Type Coverage | 100% | SearchType (14 modes), Task, DataPoint, Exceptions (5), node_set/Dataset semantics all covered |

_Weight application deferred to step-05._

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed per naive-mode rules)

### Structural Findings

| # | Type | Detail | Line |
|---|------|--------|------|
| 1 | section_mismatch_info | Section 4b "Migration & Deprecation Warnings" is present, but `evidence-report.md` reports zero T2-future annotations (no forward-looking breaking changes in v0.5.8). Section content is nevertheless well-justified — it documents the `delete` deprecation (real `@deprecated` decorator) plus two source-vs-`skill.md` signature gotchas (`start_ui` sync-not-async, `start_visualization_server` is a module). Classified Info, not Medium, because the section is populated from legitimate current-state source discrepancies, not empty or spurious. | L112–L117 |

**Structural checks passed:**
- Frontmatter valid (agentskills.io spec, PASS)
- H1 matches skill name (`# oms-cognee`)
- Required sections present: Overview, Quick Start, Common Workflows, Key API Summary, Migration & Deprecation Warnings, Key Types, Architecture at a Glance, CLI, Full API Reference link
- All code blocks are language-tagged (`` ```python ``)
- All tables well-formed (no ragged rows)
- No unclosed fences / malformed markdown
- Two `[MANUAL:...]` sections preserved per template
- No `scripts/` or `assets/` directory alongside SKILL.md → no "Scripts & Assets" section required (check skipped)
- Exports referenced in Quick Start (`cognee.add`, `cognee.cognify`, `cognee.search`, `SearchType`, `cognee.prune.prune_data`, `cognee.prune.prune_system`) are all in the documented exports set
- Async/sync consistency: all async fns are `await`ed in examples; `start_ui` and the tracing family are correctly shown as sync

**Structural Issues:** 1 (Info-level)

### Reference Consistency (split-body)

| # | Reference File | Export | Issue | SKILL.md Line | Reference Line |
|---|---------------|--------|-------|---------------|---------------|
| — | — | — | _(none)_ | — | — |

**Exports Cross-Checked:** 22 (exports appearing in both SKILL.md body and any `references/*.md`)
**Mismatches Found:** 0

SKILL.md body and `references/full-api-reference.md` + `references/config.md` + `references/core-workflow.md` + `references/pipelines-and-datapoints.md` are signature-consistent. The SKILL.md "Key API Summary" table is deliberately abbreviated ("Key params"); full parameter lists in the reference files match the provenance-map byte-for-byte.

## External Validation

**Source:** auto-reused from `forge-data/oms-cognee/0.5.8/evidence-report.md` (generated 2026-04-10T21:18:00Z during create-skill; SKILL.md last commit 2026-04-10T22:05:10+04:00 — evidence report is newer, not stale)

### skill-check
- **Available:** yes
- **Quality Score:** 100/100
- **Errors:** 0
- **Warnings:** 0
- **Diagnostics:** none (after selective split of Full API Reference / Full Type Definitions / Full Integration Patterns into `references/full-api-reference.md`)
- **Quality breakdown:** Frontmatter 30/30 · Description 30/30 · Body 20/20 · Links 10/10 · File 10/10

### tessl
- **Available:** yes
- **Validation:** PASSED
- **Description Score:** 100%
- **Content Score:** 73%
- **Average Score:** 89%
- **Suggestions:** addressed during create-skill (Architecture section trimmed per tessl suggestion #3 — removed vector/relational/graph store definitions that Claude can infer, kept non-obvious node_set integration and default-backend pinning)

### Combined External Score
- **External Validation Score:** 94.5%  _(= (100 + 89) / 2)_
- **Tools used:** skill-check + tessl

_No content-quality warning: tessl content score 73% ≥ 70% threshold._

## Completeness Score

### Score Breakdown

| Category | Score | Weight | Weighted |
|----------|-------|--------|----------|
| Export Coverage | 96% | 45% | 43.20% |
| Signature Accuracy | 100% | 25% | 25.00% |
| Type Coverage | 100% | 20% | 20.00% |
| Coherence | — (naive) | 0% | 0.00% |
| External Validation | 94.5% | 10% | 9.45% |
| **Total** | | **100%** | **97.65%** |

### Result

**Score:** 97.65%
**Threshold:** 80%
**Result:** **PASS**

**Weight Distribution:** naive (redistributed — coherence weight 18% reallocated into coverage/signature/type per `scoring-rules.md`)
**Tier Adjustment:** none (Deep tier — ast-grep + gh + QMD all available)
**External Validators:** both available (skill-check 100/100 + tessl 89% average)
**Analysis Confidence:** full (State 1 — local source clone at `~/.skf/workspace/repos/github.com/topoteretes/cognee` @ commit `b51dcce`)

_No Access Degradation Notice: `analysis_confidence = full` — source was re-verified against live AST and all 7 spot-checked citations resolved._

## Gap Report

**Total Gaps:** 6
**Blocking (Critical + High):** 0
**Non-blocking (Medium + Low + Info):** 6

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|-----------------|
| Critical | 0 | — |
| High | 0 | — |
| Medium | 0 | — |
| Low | 4 | ~15 min total — small SKILL.md additions |
| Info | 2 | Advisory only — no action required |
| **Total** | **6** | |

### GAP-001: `__version__` is an undocumented public export

**Severity:** Low
**Category:** Coverage
**Source:** `cognee/__init__.py:L6` (provenance-map entry; T1)

**Issue:** `cognee.__version__` is one of the 25 top-level public exports in `cognee/__init__.py` but is not mentioned anywhere in SKILL.md body or the four `references/*.md` files. Users who rely on version-gated code paths (`if cognee.__version__ >= "0.5.8"`) get no hint from the skill that this attribute exists.

**Remediation:** Add a one-liner in SKILL.md "Key API Summary" table, e.g.:
```markdown
| `cognee.__version__` | str | Package version (e.g., `"0.5.8"`) — derived at import time via `get_cognee_version()` | `[AST:cognee/__init__.py:L6]` |
```
Or add a bullet under "Architecture at a Glance" noting the version attribute.

### GAP-002: `cognee.session` module is not mentioned in SKILL.md body

**Severity:** Low
**Category:** Coverage
**Source:** `cognee/api/v1/session/session.py:L1` (provenance-map entry); documented in `references/full-api-reference.md:L256` only

**Issue:** `cognee.session` is a top-level module export with its own public surface but appears only in the split-body reference file. SKILL.md Quick Start, Common Workflows, and Key API Summary table never mention `session`, so an agent skimming SKILL.md will not discover it exists and will not follow the reference link for session lifecycle patterns.

**Remediation:** Add a row to the "Key API Summary" table in SKILL.md pointing to the reference:
```markdown
| `cognee.session` | module | Session scope helpers — see `references/full-api-reference.md` | `[AST:cognee/api/v1/session/session.py:L1]` |
```

### GAP-003: `cognee.cognee_network_visualization` is not mentioned in SKILL.md body

**Severity:** Low
**Category:** Coverage
**Source:** `cognee/modules/visualization/cognee_network_visualization.py:L22`; documented in `references/full-api-reference.md:L242` only

**Issue:** Same pattern as GAP-002. Only discoverable through the reference file. Given that `cognee.visualize_graph` IS in the Key API Summary (L106), a reader might reasonably expect all visualization exports to be listed there.

**Remediation:** Either (a) add a Key API Summary row next to `visualize_graph`, or (b) extend the `visualize_graph` description to cross-reference the lower-level `cognee_network_visualization` for programmatic graph-network rendering.

### GAP-004: Migration section present with zero T2-future annotations

**Severity:** Low (downgraded from the mechanical Medium default)
**Category:** Structural
**Source:** SKILL.md L112–L117; `forge-data/oms-cognee/0.5.8/evidence-report.md` ("No T2-future annotations generated")

**Issue:** Per `scoring-rules.md`, Migration section present/absent mismatch with T2-future annotation data is normally a Medium gap in Deep tier. Evidence report reports zero T2-future annotations (v0.5.8 has no forward-looking breaking changes), yet Section 4b "Migration & Deprecation Warnings" is present.

**Why it's downgraded:** The section content is semantically valid — it covers the `delete` deprecation (real `@deprecated` decorator), the `start_ui` sync-vs-async gotcha, and the `start_visualization_server` module-not-callable gotcha. These are current-state source discrepancies drawn from evidence-report.md's "Source/Docs Discrepancies" section, not empty or fabricated future-warnings. Keeping the section helps users; removing it would lose value.

**Remediation:** No code change required. Optionally rename the section header from "Migration & Deprecation Warnings" to "Deprecations & Gotchas" to more accurately describe its content, or add an Info-level note at the top of the section clarifying its scope ("Current-state deprecations and source/docs discrepancies — not forward-looking breaking changes").

### GAP-005: Discovery testing not performed — realistic prompt testing recommended

**Severity:** Info
**Category:** Advisory
**Source:** n/a

**Issue:** No record of realistic-prompt discovery testing in the create-skill or test-skill runs for `oms-cognee`. A skill tested only with clean prompts may fail to trigger in production.

**Remediation:** Before export, test the skill with 3-5 realistic prompts like:
- Vague: "can you add this pdf to my agent's memory so it can answer questions later"
- Implicit: "why can't my rag agent find the stuff I uploaded yesterday"
- Abbreviated: "build me a knowledge graph from these docs"
- With typo: "use cogne to ingest this then do a graph search"
- Integration-flavored: "set up persistent memory for my claude agent using cognee"

Confirm the skill's `description` (which is already ~170 words and keyword-dense) triggers reliably for all five phrasings.

### GAP-006: Description trigger optimization — tessl content score 73%

**Severity:** Info
**Category:** Advisory
**Source:** `evidence-report.md` tessl review (description 100%, content 73%, average 89%)

**Issue:** tessl description score is 100% (excellent), but content score is 73%. This is the expected drop after selective split — tessl evaluates SKILL.md body only, not `references/*.md`, so split-body skills see content scores fall. Per `scoring-rules.md`, this is documented expected behavior, not a real regression. For reference, the pre-split content score would have been ~85–90%.

**Remediation:** None required — the 73% score is an artifact of the selective-split design pattern, not a quality issue. If a higher tessl content score is desired for marketing reasons, consider inlining one or two of the Common Workflows examples from `references/core-workflow.md` into SKILL.md — but this will bloat SKILL.md back over the 500-line limit and undo the split. Not recommended.

---

### Discovery Quality

**Description optimization:** tessl `description_score` is **100%** (above the 90% recommendation threshold). Description uses third-person voice, opens with the primary trigger ("Builds apps on top of cognee v0.5.8..."), lists specific use cases ("ingesting text/files/URLs into persistent agent memory, building knowledge graphs..."), and includes an explicit negative-trigger ("Do NOT use for: cognee internals, the HTTP REST API, non-cognee memory or RAG libraries"). No further description changes are recommended.

**Discovery testing recommended.** Before export, test the skill with 3-5 realistic prompts phrased the way real users actually talk — with casual language, typos, incomplete context, and implicit references. See GAP-005 for concrete prompt suggestions. This is advisory — it does not affect the score.
