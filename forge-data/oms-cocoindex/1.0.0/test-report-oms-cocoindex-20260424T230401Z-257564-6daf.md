---
workflowType: 'test-skill'
skillName: 'oms-cocoindex'
skillDir: 'skills/oms-cocoindex/1.0.0/oms-cocoindex'
runId: '20260424T230401Z-257564-6daf'
testMode: 'naive'
forgeTier: 'Deep'
testResult: 'pass'
score: '98.37%'
threshold: '80%'
analysisConfidence: 'full'
toolingStatus: 'ok'
workspaceDrift: 'ok'
health_check_dispatched: true
testDate: '2026-04-24T23:04:01Z'
stepsCompleted: ['step-01-init', 'step-02-detect-mode', 'step-03-coverage-check', 'step-04-coherence-check', 'step-04b-external-validators', 'step-05-score', 'step-06-report']
nextWorkflow: 'export-skill'
---

# Test Report: oms-cocoindex

<!--
Section order is LOAD-BEARING: step-05 §5 enforces it, step-06 §5 verifies
stepsCompleted against the canonical chain. Do not reorder or delete anchors.

Anchor / Step mapping:
  Test Summary       → step-02-detect-mode
  Coverage Analysis  → step-03-coverage-check
  Coherence Analysis → step-04-coherence-check
  External Validation→ step-04b-external-validators
  Completeness Score → step-05-score
  Gap Report         → step-06-report (includes Discovery Quality subsection)
-->

## Test Summary

**Skill:** oms-cocoindex
**Test Mode:** naive
**Forge Tier:** Deep

**Mode Rationale:** `metadata.json` declares `skill_type: 'single'` — the skill wraps one library (cocoindex v1.0.0) with a self-contained API surface and no cross-skill references. Naive mode applies.

**Analysis Plan:**
- Coverage Check: documented exports (145 in metadata) vs source public-API surface at `python/cocoindex/` (pinned commit 5fe4f37a). All exports must exist in source; AST-backed signature comparison runs because tier is Deep (ast-grep available).
- Coherence Check: structural validation only — SKILL.md sections present, references files exist, examples parse — no cross-skill integration to verify.
- Scoring: redistributed weights with no coherence category contribution from cross-references; Signature Accuracy + Type Coverage active (Deep tier).

## Coverage Analysis

**Tier:** Deep
**Source Access:** full (State 1 — local source available, AST-backed)
**Source Path:** `/home/armel/.skf/workspace/repos/github.com/cocoindex-io/cocoindex` @ `5fe4f37a` (v1.0.0)
**Files Analyzed:** 38 source files (per provenance-map distinct `source_file` count)
**Denominator:** standard barrel — `python/cocoindex/_internal/api.py::__all__` (72 names)

The package barrel is `python/cocoindex/__init__.py`, which executes `from ._internal.api import *` and `__all__ = _internal.api.__all__`. Single-package layout; no monorepo (no `packages/`, `workspaces`, `lerna.json`); barrel is non-empty (72 names) → stratified-scope and pattern-reference clauses do not apply. Standard barrel-based denominator selected.

### Export Coverage

Documented inventory built by subagent over `SKILL.md` + 7 reference files (296 + 1397 lines). Inventory size: 104 entries (71 from the 72-name barrel + 33 sub-package extras: connectors, ops, resources, query handlers, CLI). Every barrel export EXCEPT `LogicTracking` is covered.

| Export | Type | Documented | Signature | Source Location | Status |
|--------|------|-----------|-----------|-----------------|--------|
| App | class | yes | matches (T1 spot-check) | `python/cocoindex/_internal/app.py:208` | PASS |
| AppConfig | dataclass | yes | matches | `python/cocoindex/_internal/app.py:202` | PASS |
| DropHandle | class | yes | matches | `python/cocoindex/_internal/app.py:143` | PASS |
| UpdateHandle | class | yes | matches | `python/cocoindex/_internal/app.py:49` | PASS |
| show_progress | function | yes | matches | `python/cocoindex/_internal/app.py:194` | PASS |
| ComponentStats | dataclass | yes | matches | provenance-map T1 | PASS |
| UpdateSnapshot | class | yes | matches | provenance-map T1 | PASS |
| UpdateStats | dataclass | yes | matches | provenance-map T1 | PASS |
| UpdateStatus | type | yes | matches | provenance-map T1 | PASS |
| fn | namespace | yes | matches | `python/cocoindex/_internal/function.py` | PASS |
| **LogicTracking** | type | **NO** | unverified | `python/cocoindex/_internal/function.py` | **FAIL — missing documentation** |
| ContextKey | class | yes | matches | provenance-map T1 | PASS |
| ContextProvider | class | yes | matches | provenance-map T1 | PASS |
| ChildTargetDef | dataclass | yes | matches | provenance-map T1 | PASS |
| TargetState | class | yes | matches | provenance-map T1 | PASS |
| TargetStateProvider | class | yes | matches | provenance-map T1 | PASS |
| TargetReconcileOutput | dataclass | yes | matches | provenance-map T1 | PASS |
| TargetHandler | interface | yes | matches | provenance-map T1 | PASS |
| TargetActionSink | class | yes | matches | provenance-map T1 | PASS |
| PendingTargetStateProvider | class | yes | matches | provenance-map T1 | PASS |
| declare_target_state | function | yes | matches | provenance-map T1 | PASS |
| declare_target_state_with_child | function | yes | matches | provenance-map T1 | PASS |
| register_root_target_states_provider | function | yes | matches | provenance-map T1 | PASS |
| Environment | class | yes | matches | provenance-map T1 | PASS |
| EnvironmentBuilder | class | yes | matches | provenance-map T1 | PASS |
| LifespanFn | type | yes | matches | provenance-map T1 | PASS |
| lifespan | decorator | yes | matches | provenance-map T1 | PASS |
| GPU | class | yes | matches | provenance-map T1 | PASS |
| Runner | class | yes | matches | provenance-map T1 | PASS |
| unpickle_safe | function | yes | matches | provenance-map T1 | PASS |
| serialize_by_pickle | function | yes | matches | provenance-map T1 | PASS |
| memo_fingerprint | function | yes | matches | provenance-map T1 | PASS |
| register_memo_key_function | function | yes | matches | provenance-map T1 | PASS |
| NotMemoKeyable | class | yes | matches | provenance-map T1 | PASS |
| MaybePendingS | type | yes | matches | provenance-map T1 | PASS |
| PendingS | type | yes | matches | provenance-map T1 | PASS |
| ResolvedS | type | yes | matches | provenance-map T1 | PASS |
| ResolvesTo | interface | yes | matches | provenance-map T1 | PASS |
| ComponentContext | dataclass | yes | matches | provenance-map T1 | PASS |
| ComponentSubpath | class | yes | matches | provenance-map T1 | PASS |
| ExceptionContext | class | yes | matches | provenance-map T1 | PASS |
| ExceptionHandler | interface | yes | matches | provenance-map T1 | PASS |
| component_subpath | function | yes | matches | provenance-map T1 | PASS |
| exception_handler | function | yes | matches | provenance-map T1 | PASS |
| use_context | function | yes | matches | provenance-map T1 | PASS |
| get_component_context | function | yes | matches | provenance-map T1 | PASS |
| Settings | dataclass | yes | matches | provenance-map T1 | PASS |
| ROOT_PATH | constant | yes | matches | provenance-map T1 | PASS |
| StablePath | class | yes | matches | provenance-map T1 | PASS |
| StableKey | type | yes | matches | provenance-map T1 | PASS |
| Symbol | class | yes | matches | provenance-map T1 | PASS |
| NON_EXISTENCE | constant | yes | matches | provenance-map T1 | PASS |
| NonExistenceType | type | yes | matches | provenance-map T1 | PASS |
| is_non_existence | function | yes | matches | provenance-map T1 | PASS |
| MemoStateOutcome | dataclass | yes | matches | provenance-map T1 | PASS |
| LiveComponent | interface | yes | matches | provenance-map T1 | PASS |
| LiveComponentOperator | class | yes | matches | provenance-map T1 | PASS |
| LiveMapFeed | interface | yes | matches | provenance-map T1 | PASS |
| LiveMapView | interface | yes | matches | provenance-map T1 | PASS |
| LiveMapSubscriber | class | yes | matches | provenance-map T1 | PASS |
| ComponentMountHandle | class | yes | matches | `python/cocoindex/_internal/api.py:171` | PASS |
| mount | function | yes | matches (T1 spot-check, async + 8 overloads) | `python/cocoindex/_internal/api.py:333` | PASS |
| mount_each | function | yes | matches | `python/cocoindex/_internal/api.py:427` | PASS |
| mount_target | function | yes | matches | `python/cocoindex/_internal/api.py:566` | PASS |
| map | function | yes | matches | provenance-map T1 | PASS |
| use_mount | function | yes | matches (T1 spot-check, async + 8 overloads) | `python/cocoindex/_internal/api.py:194` | PASS |
| start | function | yes | matches | provenance-map T1 | PASS |
| stop | function | yes | matches | provenance-map T1 | PASS |
| start_blocking | function | yes | matches | provenance-map T1 | PASS |
| stop_blocking | function | yes | matches | provenance-map T1 | PASS |
| default_env | function | yes | matches | provenance-map T1 | PASS |
| runtime | function | yes | matches | provenance-map T1 | PASS |

Sub-package extras (33 documented beyond barrel — counted as documented extras, not denominator additions per source-access-protocol §Source API Surface Definition): connectors (PgTableSource, QdrantVectorDef, KafkaTopicTarget, S3Walker, walk_dir, table_target, etc.), ops (LiteLLMEmbedder, SentenceTransformerEmbedder, RecursiveSplitter, SeparatorSplitter, CustomLanguageConfig, detect_code_language), resources (Chunk, TextPosition, FileMetadata, FileLike, FilePathMatcher, IdGenerator, UuidGenerator, generate_id, generate_uuid, VectorSchema, VectorSchemaProvider, MultiVectorSchema, MultiVectorSchemaProvider, get_vector_schema, get_multi_vector_schema, Embedder), query-handler types (QueryHandlerInfo, QueryHandlerResultFields, QueryInfo, QueryOutput), settings extras (GlobalExecutionOptions, ServerSettings), CLI (cli), live-component utility (is_live_component_class).

### Coverage Summary

- **Exports Found (barrel `__all__`):** 72
- **Documented:** 71 (98.6%)
- **Missing Documentation:** 1 — `LogicTracking` (listed in metadata.exports[] line 24 but absent from SKILL.md and all references/*.md)
- **Signature Mismatches:** 0 (3/3 high-risk overload-bearing exports spot-checked at source line; remainder relied on T1 AST-verified provenance-map at zero source-commit drift)
- **Stale Documentation:** 0 (no documented exports absent from source; 33 sub-package extras are intentionally documented)
- **Documented Extras (out of barrel scope, in scope per brief):** 33

### Metadata Coherence Cross-Check (§4b)

**Cluster A — public-barrel surface:**
- `metadata.json.stats.exports_public_api`: 74
- `metadata.json.exports[]` length: 115
- Divergence: |115−74|/115 = **35.6% (Medium)** — counts disagree on what "barrel" means. The `exports[]` array enumerates 79 top-level names (5 over the 74 public-api count: `cli`, `GlobalExecutionOptions`, `ServerSettings`, `QueryHandlerInfo`, `QueryHandlerResultFields`, `QueryInfo`, `QueryOutput`) plus 36 namespaced sub-package entries. Either `stats.exports_public_api` is undercounted relative to the enumerated list, or `exports[]` is overscoped relative to the barrel. A re-compile should reconcile.

**Cluster B — documented surface:**
- `metadata.json.stats.exports_documented`: 145
- provenance-map entries: 151
- Divergence: |151−145|/151 = 4.0% (within 10% — silent skip, no finding)

**Cross-cluster:**
- Cluster A representative (max): 115 (`exports[]`)
- Cluster B representative (max): 151 (provenance-map)
- Divergence: |151−115|/151 = 23.8% — **Info note: multi-denominator reporting — barrel vs documented surface**. Expected for a skill whose documented surface intentionally exceeds the barrel via documented submodule members (connectors/*, ops/*, resources/*, methods on classes). No action required.

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 98.6% (71/72) |
| Signature Accuracy | 100% (3 spot-checked T1 + 68 inherited from T1 AST-verified provenance @ pinned commit) |
| Type Coverage | 100% (all typed exports documented; 1 missing — `LogicTracking` — counted under Export Coverage) |

Note: Weight application is deferred to step-05 where all category weights are calculated after external validation availability is known.

### Coverage Findings (carried to Gap Report)

1. **High** — `LogicTracking` missing from documentation. Listed in `metadata.exports[]` and re-exported from the barrel via `__all__`, but no entry in `SKILL.md` or any `references/*.md`. Source location: provenance-map points at `python/cocoindex/_internal/function.py`. Fix: add a row to the appropriate Tier 2 section (likely `references/component-api.md` near the `fn` decorator namespace, since `LogicTracking` is the typed handle for `@coco.fn(logic_tracking=…)`).

2. **Medium** — `metadata drift — barrel export counts diverge`. `stats.exports_public_api=74` vs `exports[].length=115` (35.6% drift). Re-run a compile or have skf-update-skill reconcile the two fields against the canonical barrel.

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed in step-05)

### Structural Findings

| # | Type | Severity | Detail | Line |
|---|------|----------|--------|------|
| 1 | required_section | — | All required sections satisfied: `description` (frontmatter), `## Quick Start` (line 12) + `## Common Workflows` (line 88), `## Key API Summary` (line 117) | — |
| 2 | fence_balance | — | 6 triple-backtick fences (even, balanced) | — |
| 3 | bare_opening_fence | — | All opening fences carry a language tag | — |
| 4 | export_not_in_usage | High | 20 documented functions/methods are absent from the Usage span (Quick Start lines 12-87 + Common Workflows lines 88-116). See list below. | — |
| 5 | async_mismatch | — | Spot-check passed: every "async fn" entry in the Key API table that appears in Usage uses `await` (mount, mount_each, use_mount, mount_target, map). No async-described export shown without `await`. | — |
| 6 | table_columns | — | All Markdown tables in SKILL.md have consistent column counts (4 cols throughout the Key API Summary block, lines 119-178; pipe-escaping check applied) | — |
| 7 | scripts_assets | — | Skipped — neither `scripts/` nor `assets/` directory exists alongside SKILL.md | — |

### §2.4 Detail — Functions documented but not referenced in Usage

20 functions/methods from the barrel are documented (in Key API Summary table or references files) but never referenced — by string match — in the Usage span (`## Quick Start` lines 12-87 ∪ `## Common Workflows` lines 88-116):

`stop`, `start_blocking`, `stop_blocking`, `default_env`, `runtime`, `register_root_target_states_provider`, `exception_handler`, `component_subpath`, `get_component_context`, `show_progress`, `is_non_existence`, `memo_fingerprint`, `register_memo_key_function`, `unpickle_safe`, `serialize_by_pickle`, `is_live_component_class`, `detect_code_language`, `generate_id`, `generate_uuid`, `get_vector_schema`, `get_multi_vector_schema`.

Per §2.4 each is **High severity** because absence from the Usage section trivially fails discovery testing — an agent grepping the Usage section for `start_blocking()` will find nothing and conclude the function does not exist. Severity is rule-mandated, not negotiable.

**Note for the gap report (§6):** the 20 missing references will be aggregated into a **single GAP entry** to keep the gap report readable, but each underlying instance retains High severity for scoring. The realistic remediation is a small "Lifecycle & Utilities" subsection in `## Common Workflows` showing `coco.runtime()` / `start_blocking` / `stop_blocking` / `default_env` / `show_progress` / `generate_id` / `generate_uuid` / `detect_code_language` in code, plus inline mentions of the rest in the relevant existing prose paragraphs.

### §2b — Migration & Deprecation Verification

Gate conditions: Forge tier `Deep` ✓, `evidence-report.md` exists ✓.

`evidence-report.md` does **not** carry YAML frontmatter (it begins with `# Evidence Report: oms-cocoindex` directly, with no `---` delimiter pair) — therefore `t2_future_count` is absent. Per `references/migration-section-rules.md` §"Detection contract": **Case 4 — skip silently** (legacy / pre-pinned-field evidence-report).

Note: SKILL.md *does* contain a `## Migration from v0.3.37` section at line 247 documenting historical migration content (the v0.3.37 → v1.0.0 paradigm cutover). Without `t2_future_count`, the rule cannot determine whether this is Case 2 (historical → Info) or Case 3 (non-migration → Medium). Recommend the next `skf-update-skill` cycle write `t2_future_count` into evidence-report.md frontmatter so this verification is no longer skipped.

### Issue Summary

- **Structural Issues:** 21 (1 consolidated High covering 20 missing function-in-usage references + 1 informational note about migration verification skip)
- **Issue weight to scoring:** Coherence is not scored in naive mode (weight redistributed to coverage per scoring-rules.md naive-mode redistribution).

## External Validation

### skill-check
- **Available:** yes (probe + run via `npx skill-check check`)
- **Quality Score:** 100/100
- **Errors:** 0
- **Warnings:** 0
- **Diagnostics:** none
- **Breakdown:** frontmatter 30, description 30, body 20, links 10, file 10

### tessl
- **Available:** yes (`tessl 0.76.0`; 0.77.0 available upstream — informational, no action)
- **Validation:** PASSED (0 errors, 0 warnings across 11 deterministic checks: line count 297 ≤ 500, frontmatter valid, name/description/optional fields valid)
- **Description Score:** 100% (specificity 3/3, trigger-term quality 3/3, completeness 3/3, distinctiveness 3/3)
- **Content Score:** 50% (conciseness 1/3, actionability 3/3, workflow clarity 2/3, progressive disclosure 2/3)
- **Review Score:** 80%
- **Suggestions:**
  - Move the Key API Summary table, Key Types section, and Architecture at a Glance into the referenced files (`references/component-api.md`, etc.) and keep only a 2-3 line summary with links in SKILL.md.
  - Remove provenance annotations (`[AST:...]`) from the main skill body — these are internal references that consume tokens without helping Claude execute tasks.
  - Add explicit step-by-step workflows with validation checkpoints for common operations like "setting up a new pipeline" or "migrating from v0.3.37", including how to verify each step succeeded.
  - Trim the migration table to the 8-10 most common mappings and move the full table to a separate migration reference file.

### Combined External Score
- **External Validation Score:** 90% (= (100 + 80) / 2)
- **Tools used:** skill-check, tessl

### Content Quality Warning (tessl content = 50% < 70%)

> **Content quality warning:** tessl scored content at 50%. SKILL.md is 297 lines and inlines the entire Key API Summary table (~60 rows), Key Types block, Architecture overview, and a 22-row Migration table — content the judge says belongs in `references/*.md`. The seven `references/*.md` files exist (1397 lines total) but the SKILL.md body redundantly inlines material rather than delegating. Consider relocating the API table and migration table into references and replacing them with 2-3 line summaries + links. This is **not** a split-body false-positive — references already exist; the issue is duplication.

## Completeness Score

### Score Breakdown

| Category | Score | Weight | Weighted |
|----------|-------|--------|----------|
| Export Coverage | 98.6% | 45.0% | 44.37% |
| Signature Accuracy | 100% | 25.0% | 25.00% |
| Type Coverage | 100% | 20.0% | 20.00% |
| Coherence | — | 0% (naive — redistributed) | 0.00% |
| External Validation | 90% | 10.0% | 9.00% |
| **Total** | | **100%** | **98.37%** |

### Result

**Score:** 98.37%
**Threshold:** 80%
**Result:** **PASS**

**Weight Distribution:** naive (coherence weight redistributed to coverage + signature + type + external)
**Tier Adjustment:** none (Deep tier — Signature Accuracy and Type Coverage active)
**External Validators:** both available (skill-check + tessl)
**Analysis Confidence:** full
**Caps applied:** none (no tooling-degraded cap, no docs-only cap)
**Floor checks:** active categories = 4 (≥2) — minimum-evidence floor not tripped

### Active Categories: 4
`exportCoverage`, `signatureAccuracy`, `typeCoverage`, `externalValidation`

### Skipped Categories: 1
`coherence` — naive mode, weight redistributed

## Gap Report

**Total Gaps:** 6 (1 grouped High covers 21 sub-instances)
**Blocking (Critical + High):** 2
**Non-blocking (Medium + Low + Info):** 4

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|-----------------|
| Critical | 0 | — |
| High | 2 | ~1h — add `LogicTracking` reference docs (small) + add 1 "Lifecycle & Utilities" subsection (~30 lines) covering 20 missing-from-Usage functions |
| Medium | 1 | ~15min — re-run skf-update-skill (or manual edit) to reconcile `stats.exports_public_api` and `exports[].length` against the canonical barrel |
| Low | 1 | ~1h — apply tessl judge suggestions (move API table + migration table out of SKILL.md body into `references/`, remove inline `[AST:...]` provenance) |
| Info | 2 | optional — multi-denominator reporting note + migration-verification frontmatter pin recommendation |
| **Total** | **6** | **~2h** for blocking; ~3h with all remediations |

---

### GAP-001: `LogicTracking` missing from documentation

**Severity:** High
**Category:** Coverage
**Source:** `metadata.json` line 24 (declared in `exports`); `python/cocoindex/_internal/api.py:683` (re-exported via `__all__`); provenance-map `python/cocoindex/_internal/function.py`

**Issue:** `LogicTracking` is one of the 72 names in the package barrel (`__all__`) and is listed in `metadata.exports[]`, but it is not documented anywhere — no row in any `references/*.md`, no mention in `SKILL.md`. An agent looking up `LogicTracking` (which is the typed handle for `@coco.fn(logic_tracking=…)`) will find no documentation.

**Remediation:** Add a row to `references/component-api.md` near the `fn` decorator namespace (currently around line 154). Use the provenance-map signature: `LogicTracking` is exported from `python/cocoindex/_internal/function.py`. Suggested entry:

```markdown
| `LogicTracking` | type | Typed handle returned by `@coco.fn(logic_tracking="full"\|"self"\|None)`. Tracks per-component logic version for memo invalidation. | [AST:python/cocoindex/_internal/function.py] |
```

Also append `LogicTracking` to the SKILL.md `## Key API Summary` table near the `fn` entry (currently line 127) so the symbol is reachable from the Tier 1 surface.

---

### GAP-002: 20 functions/methods documented but never referenced in Usage section

**Severity:** High (consolidated — 20 sub-instances all High per §2.4 rule)
**Category:** Coherence (structural)
**Source:** `SKILL.md` lines 12-116 (Quick Start ∪ Common Workflows); each function has an entry in `## Key API Summary` (line 117+) or `references/*.md`

**Issue:** The following 20 documented exports do not appear (by string match) anywhere in the Quick Start or Common Workflows sections, the only sections naive-mode §2.4 considers as "Usage":

`stop`, `start_blocking`, `stop_blocking`, `default_env`, `runtime`, `register_root_target_states_provider`, `exception_handler`, `component_subpath`, `get_component_context`, `show_progress`, `is_non_existence`, `memo_fingerprint`, `register_memo_key_function`, `unpickle_safe`, `serialize_by_pickle`, `is_live_component_class`, `detect_code_language`, `generate_id`, `generate_uuid`, `get_vector_schema`, `get_multi_vector_schema`.

An agent grepping the Usage span for any of these will find nothing and may conclude the function does not exist.

**Remediation:** Add a "Lifecycle & Utilities" subsection inside `## Common Workflows` (between line 88 and 116) with code snippets demonstrating:

1. `coco.runtime()` dual-mode context manager (`with coco.runtime(): app.update_blocking()` and `async with coco.runtime(): await app.update()`).
2. Sync entry point: `coco.start_blocking(); app.update_blocking(); coco.stop_blocking()` — for non-async callers.
3. Default env access: `env = coco.default_env()`.
4. Progress reporting: `result = await coco.show_progress(handle)`.
5. ID generation: `uid = coco.generate_id(seed)`; `u = coco.generate_uuid(seed)`.
6. Code-language detection in a splitter pipeline: `lang = coco.ops.text.detect_code_language(filename="foo.py")`.

Then add one or two lines of prose in the existing `@coco.lifespan` paragraph (line 83) mentioning `coco.exception_handler(handler)` for background error capture, and in the `coco.use_context` paragraph mentioning `coco.get_component_context()` and `coco.component_subpath(...)`.

The remaining tail (`is_non_existence`, `memo_fingerprint`, `register_memo_key_function`, `unpickle_safe`, `serialize_by_pickle`, `is_live_component_class`, `register_root_target_states_provider`, `get_vector_schema`, `get_multi_vector_schema`) are advanced/internal-extension APIs; one Common Workflows paragraph titled "Advanced extension hooks" briefly listing them with one-line "use when…" hints will satisfy the structural rule and serve real readers.

---

### GAP-003: metadata drift — barrel export counts diverge (Cluster A)

**Severity:** Medium
**Category:** Structural / metadata coherence
**Source:** `metadata.json` — `stats.exports_public_api: 74` vs `exports[].length: 115`

**Issue:** Within the public-barrel cluster, `stats.exports_public_api` reports 74 and `exports[].length` reports 115 — a 35.6% divergence. The two fields should mirror the same `__all__` surface but disagree. The `exports[]` array contains 79 top-level names (5 over the 74 public-api count) plus 36 namespaced sub-package entries. Either `stats.exports_public_api` is undercounted relative to the enumerated list, or `exports[]` is overscoped relative to the barrel.

**Remediation:** Re-run `skf-update-skill` (it produced this metadata) and let its step-05 compile pass reconcile the counts. If a quicker fix is preferred, manually update `metadata.json` so `stats.exports_public_api` matches the actual barrel-only count from `python/cocoindex/_internal/api.py::__all__` (= 72), and either (a) trim `exports[]` to barrel-only entries, or (b) add `stats.exports_documented_in_array: 115` to make the dual-count intentional and machine-readable.

---

### GAP-004: tessl content score 50% — SKILL.md inlines material that already lives in references

**Severity:** Low (tessl judge guidance; the skill still passes overall)
**Category:** External validation / content quality
**Source:** tessl review (run during step-04b) — Content 50% (conciseness 1/3, progressive disclosure 2/3)

**Issue:** SKILL.md is 297 lines and inlines (1) the entire Key API Summary table (~60 rows, lines 119-178), (2) the full Key Types block (lines 179-215), (3) Architecture at a Glance (lines 216-230), and (4) a 22-row Migration table (lines 247-279). The seven `references/*.md` files (1397 lines total) already exist; the body redundantly inlines material rather than delegating.

**Remediation (4 actionable items from tessl judge):**

1. Move the `## Key API Summary` table (lines 117-178) into a new `references/api-summary.md` (or fold into `references/component-api.md`) and replace the SKILL.md body with a 3-line summary + link.
2. Remove `[AST:python/cocoindex/...]` provenance annotations from the SKILL.md body — they consume tokens without helping Claude execute tasks. Keep them in references files where they aid auditability.
3. Add explicit step-by-step workflows with validation checkpoints in `## Common Workflows` for "set up a new pipeline" and "migrating from v0.3.37" — show how to verify each step succeeded (e.g., "run `coco-cli ls` and confirm component appears").
4. Trim the `## Migration from v0.3.37` table (lines 252-278) to the 8-10 most common mappings; move the full table to a new `references/migration-v0.3.37.md`.

These suggestions are advisory (skill PASSES overall at 98.37%) but addressing them would lift the tessl content score and reduce the SKILL.md token footprint by an estimated 40-50%.

---

### GAP-005: multi-denominator reporting — barrel vs documented surface (Info)

**Severity:** Info
**Category:** Structural (informational)
**Source:** Cross-cluster cross-check in step-03 §4b: Cluster A (barrel) representative = 115 vs Cluster B (documented) representative = 151 — 23.8% divergence

**Issue:** The skill's documented surface intentionally exceeds the barrel via documented submodule members (connectors/*, ops/*, resources/*, methods on classes). This is by design for `oms-cocoindex` — the brief explicitly includes `connectors/**`, `ops/**`, and `resources/**`. The dual-denominator design is correct; this Info note exists only so the report makes it auditable.

**Remediation:** None required. Optionally, add `metadata.json.stats.documented_surface_components: 36` (enumerating the namespaced sub-package entry count) to make the dual reporting explicit.

---

### GAP-006: Migration verification skipped — evidence-report.md lacks YAML frontmatter

**Severity:** Info
**Category:** Tooling / evidence-report schema drift
**Source:** `forge-data/oms-cocoindex/1.0.0/evidence-report.md` — file begins with `# Evidence Report: oms-cocoindex` (no `---` delimiter pair)

**Issue:** Per `references/migration-section-rules.md` §"Detection contract", `t2_future_count` MUST be parsed from the evidence report's YAML frontmatter; reading it from prose is rejected to avoid drift. This evidence-report.md predates the pinned-field convention (Case 4 — skip silently). The §2b migration verification therefore did not run, even though SKILL.md does contain a `## Migration from v0.3.37` section that the rule could have classified.

**Remediation:** When the next `skf-update-skill` run regenerates `evidence-report.md`, ensure step-05 §7 writes the `t2_future_count` frontmatter field. For this snapshot, no action is needed — the verification skip is rule-compliant.

---

## Discovery Quality

**Catalog size:** 4 skills in `skills/` (oms-cocoindex, oms-cognee, oms-storybook-react-vite, oms-uitripled) — ≥2 candidates required for §4b discovery testing satisfied.

### Realistic Prompt Routing (3 isolated subagents, no prior context)

| # | Prompt | Selected | Confidence | Outcome |
|---|--------|----------|------------|---------|
| 1 | "Help me build a vector search pipeline that ingests PDFs from S3 into Postgres with sentence-transformers embeddings" | `oms-cocoindex` | high | PASS |
| 2 | "I need to rewrite my old flow_def code with the new App and mount stuff after upgrading" | `oms-cocoindex` | high | PASS |
| 3 | "set up an incremental indexer that processes a folder of markdown docs through chunking + embedding into qdrant" | `oms-cocoindex` | high | PASS |

**Discovery Check:** 3/3 PASS — Info severity note, no gap. Description triggers ("data ingestion", "ETL", "RAG", "vector search", "incremental indexing", "App / mount") successfully discriminated `oms-cocoindex` against `oms-cognee` (knowledge-graph memory), `oms-storybook-react-vite` (component stories), and `oms-uitripled` (Next.js shadcn UI).

### Description Optimization (§4b.4)

tessl `description_score` = 100% (above the 90% threshold). skill-check raised no description issues. **No optimization recommendations** — description already scores at the ceiling on specificity, trigger-term quality, completeness, and distinctiveness. The version-specific anti-trigger (`do NOT mix vocabularies`) is a strong distinctiveness booster the judge highlighted.

## Workflow Provenance

- **workspace_drift_check**: ok (5fe4f37a — exact match against pinned source_commit)
- **frontmatter_validator**: pass (0 issues)
- **python3**: /usr/bin/python3 (3.13.5)
- **forge_tier**: Deep (ast_grep ✓, gh_cli ✓, qmd ✓, ccc ✓)
- **lock**: acquired forge-data/oms-cocoindex/1.0.0/.test-skill.lock
