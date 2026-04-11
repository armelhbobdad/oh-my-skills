---
workflowType: 'test-skill'
skillName: 'oms-cocoindex'
skillDir: 'skills/oms-cocoindex/0.3.37/oms-cocoindex'
testMode: 'naive'
forgeTier: 'Deep'
testResult: 'pass'
score: '99.0%'
threshold: '80%'
analysisConfidence: 'full'
testDate: '2026-04-11'
stepsCompleted: ['step-01-init', 'step-02-detect-mode', 'step-03-coverage-check', 'step-04-coherence-check', 'step-04b-external-validators', 'step-05-score', 'step-06-report']
nextWorkflow: 'export-skill'
---

# Test Report: oms-cocoindex

## Test Summary

- **Skill:** oms-cocoindex
- **Version:** 0.3.37
- **Source:** https://github.com/cocoindex-io/cocoindex @ v0.3.37 (87c5dbf0)
- **Language:** python
- **Confidence Tier (creation):** Deep
- **Test Tier:** Deep
- **Test Mode:** naive
- **Frontmatter validator:** PASS (0 issues)

**Mode Rationale:** `skill_type: single` in metadata.json — individual skill compiled from one source library (cocoindex). No cross-skill references to validate, so we run in naive mode: coverage-driven validation of the documented public API against the upstream source.

**Analysis Plan:**
- Coverage Check: AST-backed enumeration of the public API surface in the source repo vs. the exports documented in SKILL.md and references; flag undocumented public symbols, documented-but-missing symbols, and signature/type mismatches.
- Coherence Check: basic structural validation — references exist at declared paths, internal cross-links resolve, frontmatter compliance, citation format sanity.
- External Validation: `skf-validate-frontmatter.py`, license/compatibility surface checks.

## Coverage Analysis

**Tier:** Deep
**Source Access:** full (State 1 — local clone at `/home/armel/.skf/workspace/repos/github.com/cocoindex-io/cocoindex` @ commit 87c5dbf0)
**Source Path:** python/cocoindex/
**Files Analyzed:** 11 (`__init__.py`, `flow.py`, `lib.py`, `setting.py`, `auth_registry.py`, `llm.py`, `index.py`, `query_handler.py`, `op.py`, `typing.py`, `functions/_engine_builtin_specs.py`)
**Denominator:** standard barrel (`python/cocoindex/__init__.py` `__all__` — 55 public symbols after excluding `__version__` and `_engine`)

### Export Coverage — Barrel Surface (55/55)

All 55 public barrel symbols from `python/cocoindex/__init__.py` `__all__` are documented in SKILL.md + references. Category breakdown:

| Category | Documented / Total | Source | Status |
|----------|---------------------|--------|--------|
| Flow core (FlowBuilder, DataScope, DataSlice, Flow, FlowLiveUpdater, FlowLiveUpdaterOptions, FlowUpdaterStatusUpdates, EvaluateAndDumpOptions, GeneratedField) | 9/9 | flow.py:212–815 | PASS |
| Flow functions (flow_def, open_flow, transform_flow, add_flow_def, remove_flow, update_all_flows_async, setup_all_flows, drop_all_flows) | 8/8 | flow.py:986–1309 | PASS |
| Lifecycle (settings, init, start_server, stop) | 4/4 | lib.py:35+ | PASS |
| LLM (LlmSpec, LlmApiType) | 2/2 | llm.py | PASS |
| Index (VectorSimilarityMetric, VectorIndexDef, FtsIndexDef, IndexOptions, HnswVectorIndexMethod, IvfFlatVectorIndexMethod) | 6/6 | index.py | PASS |
| Settings (DatabaseConnectionSpec, GlobalExecutionOptions, Settings, ServerSettings, get_app_namespace) | 5/5 | setting.py | PASS |
| Auth registry (AuthEntryReference, add_auth_entry, add_transient_auth_entry, ref_auth_entry) | 4/4 | auth_registry.py | PASS |
| Query handler (QueryHandlerResultFields, QueryInfo, QueryOutput) | 3/3 | query_handler.py | PASS |
| Typing aliases (Int64, Float32, Float64, LocalDateTime, OffsetDateTime, Range, Vector, Json) | 8/8 | typing.py | PASS |
| Submodules (functions, sources, targets, storages, cli, op, utils) | 7/7 | submodule files | PASS |

### Provenance-Map Cross-Reference (114/114)

The provenance-map lists 114 T1-verified entries (barrel symbols + methods + submodule members + op framework primitives). All 114 names resolved to documented content across SKILL.md body and the four reference files:

- **FlowBuilder:** 3 methods documented (`add_source`, `transform`, `declare`)
- **DataScope:** `add_collector` + dunder context-manager methods documented
- **DataSlice:** 4 methods documented (`row`, `for_each`, `transform`, `call`)
- **DataCollector:** 2 methods documented (`collect`, `export`)
- **Flow:** 11+ methods documented (`update`, `update_async`, `setup`, `drop`, `close`, `evaluate_and_dump`, `add_query_handler`, `query_handler`, etc.)
- **FlowLiveUpdater:** 5 methods + async variants + context-manager dunders documented
- **op framework primitives:** `FunctionSpec`, `SourceSpec`, `TargetSpec`, `TargetAttachmentSpec`, `DeclarationSpec`, `OpCategory`, `ArgRelationship`, `OpArgs`, `function`, `executor_class`, `source_connector`, `target_connector`, `SourceReadOptions`, `PartialSourceRowData`, `PartialSourceRow`, `TargetStateCompatibility`, `EmptyFunctionSpec` — all documented in `op-framework.md`
- **sources.*:** `LocalFile`, `GoogleDrive`, `AmazonS3`, `AzureBlob`, `Postgres` + notification helpers documented in `sources-targets-functions.md`
- **targets.*:** `Postgres`, `Qdrant`, `Pinecone`, `Neo4j`, `FalkorDB`, `Ladybug`, `ChromaDB`, `LanceDB`, `DorisTarget`, `Turbopuffer`, `Nodes`, `Relationships`, `PostgresSqlCommand` + connection specs + graph mapping specs — all documented
- **functions.*:** `ParseJson`, `DetectProgrammingLanguage`, `SplitRecursively`, `SplitBySeparators`, `EmbedText`, `ExtractByLlm`, `SentenceTransformerEmbed`, `ColPaliEmbedImage`, `ColPaliEmbedQuery` + executors — all documented

### Signature Accuracy — Spot-Check Sample (20/20)

AST-verified spot check against the source tree (commit 87c5dbf0). All 20 sampled signatures matched the source exactly for parameter names, types, defaults, positional/keyword-only markers, and return types:

| # | Export | Source:Line | Result |
|---|--------|-------------|--------|
| 1 | `FlowBuilder.add_source` | flow.py:511 | MATCH |
| 2 | `FlowBuilder.transform` | flow.py:548 | MATCH |
| 3 | `FlowBuilder.declare` | flow.py:566 | MATCH |
| 4 | `DataScope.add_collector` | flow.py:345 | MATCH |
| 5 | `DataSlice.row` | flow.py:232 | MATCH |
| 6 | `DataSlice.for_each` | flow.py:253 | MATCH |
| 7 | `DataSlice.transform` | flow.py:270 | MATCH |
| 8 | `DataCollector.export` | flow.py:402 | MATCH |
| 9 | `Flow.update` | flow.py:771 | MATCH |
| 10 | `Flow.evaluate_and_dump` | flow.py:815 | MATCH |
| 11 | `Flow.add_query_handler` | flow.py:898 | MATCH |
| 12 | `FlowLiveUpdater.__init__` | flow.py:603 | MATCH |
| 13 | `flow_def` | flow.py:1011 | MATCH |
| 14 | `open_flow` | flow.py:986 | MATCH |
| 15 | `update_all_flows_async` | flow.py:1068 | MATCH |
| 16 | `settings` | lib.py:35 | MATCH |
| 17 | `init` | lib.py | MATCH |
| 18 | `add_auth_entry` | auth_registry.py | MATCH |
| 19 | `LlmSpec` | llm.py | MATCH |
| 20 | `ExtractByLlm` | functions/_engine_builtin_specs.py | MATCH |

All 114 provenance-map entries carry `signature_source: T1` (AST-extracted at compile time) — the spot-check confirms compile-time fidelity was preserved through enrichment and split-body assembly.

### Type Coverage

All 8 typing aliases (`Int64`, `Float32`, `Float64`, `LocalDateTime`, `OffsetDateTime`, `Range`, `Vector`, `Json`) are documented in `settings-auth.md`. Generic parameters (`DataSlice[T]`, `AuthEntryReference[T]`, `Vector[T, N]`) surface in the documented signatures and in `flow-api.md`'s type-system section. Return types on all 20 spot-checked entries matched source.

### Split-Body Cross-Check

Subagent reviewed every export documented in BOTH SKILL.md body and a references file. **0 signature mismatches found.** SKILL.md body signatures for `FlowBuilder`, `Flow`, `FlowLiveUpdater`, `open_flow`, `flow_def`, `ExtractByLlm`, `SplitRecursively`, etc. agree with the corresponding entries in the reference files.

### Coverage Summary

- **Exports Found (barrel):** 55
- **Documented:** 55 (100%)
- **Missing Documentation:** 0
- **Signature Mismatches (sample):** 0
- **Stale Documentation:** 0 (no documented symbols missing from source)
- **Provenance-map reconciliation:** 114/114 entries resolved to documented content

### Metadata Export-Count Coherence Cross-Check

Four count sources collected:

| Source | Count |
|--------|-------|
| `metadata.json.stats.exports_public_api` | 55 |
| `metadata.json.stats.exports_documented` | 114 |
| `metadata.json.exports[]` array length | 55 |
| Provenance-map entry count | 114 |

Two clusters: the barrel cluster (55, 55) and the documented-entries cluster (114, 114). Each cluster is internally consistent, but the 55 vs 114 gap exceeds 10% divergence per the deterministic rule.

**Finding — Info (re-labelled from Medium by field semantics):** The divergence is intentional by field definition — `exports_public_api` measures the barrel symbols, while `exports_documented` measures the full provenance-map entry surface (barrel symbols + methods + op primitives + submodule members). Both measurements are accurate; the stats schema simply exposes two denominators for different purposes. No upstream extraction drift is present. Reported here for auditability, not as a real data-quality gap.

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 100% (55/55 barrel) |
| Signature Accuracy | 100% (20/20 sampled; 114/114 T1 at compile) |
| Type Coverage | 100% (8/8 aliases + return types match) |

Note: Weight application is deferred to step-05.

## Coherence Analysis

**Mode:** naive (basic structural validation; coherence weight is redistributed to coverage per scoring-rules.md)

### Document Structure

| Check | Result |
|-------|--------|
| Top-level sections present (Overview, Quick Start, Common Workflows, Key API Summary, Key Types, Architecture at a Glance, CLI, Full API Reference, Full Type Definitions, Full Integration Patterns) | PASS — all present |
| Migration & Deprecation Warnings (Section 4b) present | PASS — present at line 126 |
| Code blocks paired (open/close) | PASS — 4 blocks, all balanced (lines 33/75, 139/155, 176/184, 414/422) |
| Code examples have language annotations | PASS — all 4 blocks tagged (`python`, `sh`) |
| Frontmatter compliance | PASS (validator 0 issues) |
| Scripts/assets directory present? | NO — no `scripts/` or `assets/` alongside SKILL.md → Section 7b not required |

### References Directory Cross-Links

SKILL.md links to `references/*.md` in 6 places. All targets exist on disk:

| Link (SKILL.md line) | Target | Exists |
|----------------------|--------|--------|
| L135 → `references/flow-api.md` | flow-api.md | YES |
| L198 → `references/flow-api.md` | flow-api.md | YES |
| L273 → `references/settings-auth.md` | settings-auth.md | YES |
| L302 → `references/sources-targets-functions.md` | sources-targets-functions.md | YES |
| L358 → `references/op-framework.md` | op-framework.md | YES |
| L400 → `references/flow-api.md` + `references/settings-auth.md` + `references/sources-targets-functions.md` | 3 files | YES, YES, YES |

All 4 files in `references/` (flow-api.md, op-framework.md, settings-auth.md, sources-targets-functions.md) are referenced at least once from SKILL.md. No orphan reference files, no broken links.

### Internal Consistency

| Check | Result |
|-------|--------|
| Exports in usage examples match documented exports | PASS — `FlowBuilder`, `DataSlice`, `flow_def`, `add_source`, `SplitRecursively`, `SentenceTransformerEmbed`, `ExtractByLlm`, `LlmSpec`, `LlmApiType`, `Neo4j`, `Nodes`, `Relationships`, `NodeFromFields`, `FlowLiveUpdater`, `FlowLiveUpdaterOptions`, `collector.collect`, `collector.export` all appear in both body and Full API Reference |
| Type names in examples match documented types | PASS — `VectorSimilarityMetric.COSINE_SIMILARITY`, `LlmApiType.OPENAI`, `GeneratedField.UUID`, `Vector[np.float32, Literal[384]]` all match Key Types section |
| Deprecated API mentions consistent | PASS — `add_flow_def`, `remove_flow`, `storages`, `get_target_storage_default_name`, `Kuzu` all flagged deprecated in both Migration section and Full API Reference |
| Async/sync semantics consistent | PASS — `Flow.update_async`, `update_all_flows_async`, `FlowLiveUpdater.wait_async`, etc. are documented as async; `Flow.update`, `setup_all_flows`, etc. as sync |

### Migration & Deprecation Verification (Deep tier, Section 2b)

Gate: Deep tier ✓, `evidence-report.md` present ✓ → execute.

- **T2-future annotations in evidence-report.md:** 0
- **Section 4b present in SKILL.md:** YES (line 126)
- **Section 4b content type:** historical migration — five bullets all cover *shipped* deprecations / renames / retirements load-bearing for correcting training-data drift:
  1. `add_flow_def` → `open_flow` (shipped rename; AST provenance)
  2. `remove_flow` → `fl.close()` (shipped API consolidation; AST provenance)
  3. `cocoindex.storages` → `cocoindex.targets` (shipped import-path consolidation; AST provenance)
  4. `get_target_storage_default_name` → `get_target_default_name` (shipped utility rename; AST provenance)
  5. `Kuzu` → `Ladybug` (shipped target retirement with backward-compat alias; AST provenance)
  6. "Alpha stability" bullet — stability caveat, not a migration, but documented inline with the historical-migration content
- **Classification:** 4b present + 0 T2-future annotations + historical-migration content → **Info** severity per step-04 §2b exception (a). No inline justification required.

**Recommendation (advisory, not blocking):** A future revision could rename Section 4b to "Import Corrections" or "Ecosystem Notes" to free the Migration & Deprecation heading for forward-looking-only content, and relocate the "Alpha stability" bullet to Section 1/Overview where it already lives.

### Coherence Findings

| # | Severity | Finding |
|---|----------|---------|
| 1 | Info | Section 4b present with 0 T2-future annotations — historical-migration content load-bearing for training-data drift correction (rule-exception (a)). No action required; optional future rename to "Import Corrections". |

**Structural issues found:** 0
**Coherence score:** N/A (naive mode; weight redistributed to coverage)

## External Validation

**Source:** reused from `forge-data/oms-cocoindex/0.3.37/evidence-report.md` (produced by create-skill on 2026-04-11, same workflow session). Staleness check: SKILL.md is committed at `2026-04-11T23:21:33+04:00` with no uncommitted or staged changes; evidence report is current; `metadata.json.generation_date = 2026-04-11T22:50:00Z`; cached results are non-stale per step-04b §1b rules. No fresh run needed.

### skill-check

- **Available:** yes
- **Quality Score:** 100/100
- **Errors:** 0
- **Warnings:** 0 (after auto-fix round: 4 false-positive "broken local link" warnings on `ClassName[T](...)` patterns were resolved by rewriting AuthEntryReference, PartialSourceRowData, PartialSourceRow, and QueryOutput class signatures to separate generic brackets from field lists)
- **Diagnostics:** none
- **Body check:** PASS (434 lines, below 500-line split-body threshold)
- **Schema breakdown:** Frontmatter 30/30, Description 30/30, Body 20/20, Links 10/10, File 10/10

### tessl

- **Available:** yes
- **Validation:** PASSED (0 errors, 0 warnings)
- **Description Score:** 100% (specificity 3/3, trigger_term_quality 3/3, completeness 3/3, distinctiveness 3/3)
- **Content Score:** 50% (conciseness 1/3, actionability 3/3, workflow_clarity 2/3, progressive_disclosure 2/3) — WARN (below 60% floor)
- **Review Score:** 80%
- **Dismissed suggestions** (all recorded with per-rule justification in evidence-report.md):
  - `move-full-api-reference` — dismissed: two-tier SKF design keeps Tier 2 inline below split threshold (body 434 lines < 500)
  - `conciseness-redundancy-between-tiers` — dismissed: progressive disclosure is intentional (Tier 1 summary vs Tier 2 deep reference)
  - `remove-AST-provenance-annotations` — dismissed: `[AST:...]` citations are load-bearing for update-skill drift detection and audit verification
  - `add-validation-error-recovery` — dismissed: SKF zero-hallucination rule bars content not verified from source
  - `trim-Key-Types-section` — dismissed: section is already minimal and discoverability-critical for the context snippet

**Content-quality warning:** tessl content_score 50% is below the 60% floor. Per scoring-rules.md, this reflects inline-content quantity rather than quality — the Full API Reference section (102 lines of T1 AST-verified content) is intentional two-tier design, not waste. The warning is dismissed in evidence-report.md with justification; documented here for auditability.

### Combined External Score

- **Formula:** `(skill_check + tessl_review) / 2`
- **External Validation Score:** `(100 + 80) / 2 = 90%`
- **Tools used:** skill-check, tessl

## Completeness Score

### Score Breakdown

| Category | Score | Weight | Weighted |
|----------|-------|--------|----------|
| Export Coverage | 100% | 45% | 45.0% |
| Signature Accuracy | 100% | 25% | 25.0% |
| Type Coverage | 100% | 20% | 20.0% |
| Coherence | N/A | 0% | 0.0% (naive mode — redistributed) |
| External Validation | 90% | 10% | 9.0% |
| **Total** | | **100%** | **99.0%** |

### Result

**Score:** 99.0%
**Threshold:** 80%
**Result:** **PASS**

**Weight Distribution:** naive (coherence 18% redistributed proportionally: Export Coverage 36→45, Signature Accuracy 22→25, Type Coverage 14→20, External Validation 10→10)
**Tier Adjustment:** none — Deep tier, all AST-backed categories scored
**External Validators:** both available (skill-check 100 + tessl review 80 → 90 combined)
**Analysis Confidence:** full (State 1 — local source clone)
**Scoring Source:** deterministic compute-score.py output

**Next Workflow:** `export-skill` — skill passes the 80% threshold with 19 points of headroom. Ready for packaging.

## Gap Report

**Total Gaps:** 2
**Blocking (Critical + High):** 0
**Non-blocking (Medium + Low + Info):** 2

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|-----------------|
| Critical | 0 | — |
| High | 0 | — |
| Medium | 0 | — |
| Low | 0 | — |
| Info | 2 | Advisory only; no action required |
| **Total** | **2** | |

No blocking gaps. The skill passes with 19 points above the 80% threshold and zero Critical/High/Medium/Low findings.

### GAP-001: Section 4b contains historical migration with 0 T2-future annotations

**Severity:** Info
**Category:** Coherence
**Source:** SKILL.md:126 — `## Migration & Deprecation Warnings`

**Issue:** SKILL.md Tier 1 contains a Migration & Deprecation Warnings section (5 deprecation bullets + 1 alpha-stability note), but `forge-data/oms-cocoindex/0.3.37/evidence-report.md` reports 0 T2-future annotations. The content consists entirely of *shipped* deprecations/renames/retirements: `add_flow_def` → `open_flow` (flow.py:L997), `remove_flow` → `fl.close()` (flow.py:L1004), `cocoindex.storages` → `cocoindex.targets` (`__init__.py`:L12), `get_target_storage_default_name` → `get_target_default_name` (utils.py:L18), and `Kuzu` → `Ladybug` (targets/_engine_builtin_specs.py:L205). All five are load-bearing for correcting model training-data drift, which is the step-04 §2b historical-migration exception (rule case a). The gate rule reserves the "Migration & Deprecation Warnings" heading for *forward-looking* breaking changes.

**Remediation:** Optional, non-blocking. A future skill revision could:
1. Rename Section 4b from "Migration & Deprecation Warnings" to "Import Corrections" or "Ecosystem Notes" to free the forward-looking heading.
2. Move the "Alpha stability" bullet (line 133) up to Section 1 (Overview) where a near-identical note already lives at line 27 — the current placement duplicates the alpha caveat inside a section otherwise focused on API deprecations.
3. Leave all five shipped-deprecation bullets in place regardless of the rename — they remain critical training-data correction signal.

**Why keep it as Info:** The content is accurate, AST-cited, and useful to agents. The gate exception (a) formalizes that historical-migration content in Section 4b is acceptable without justification. No action is required to pass.

### GAP-002: Metadata export-count cluster divergence (informational)

**Severity:** Info (field-semantic rather than drift)
**Category:** Structural
**Source:** `skills/oms-cocoindex/0.3.37/oms-cocoindex/metadata.json` + `forge-data/oms-cocoindex/0.3.37/provenance-map.json`

**Issue:** The four export-count sources form two consistent clusters that disagree by ~52% across clusters:

- Barrel cluster: `stats.exports_public_api = 55`, `exports[].length = 55`
- Documented-entries cluster: `stats.exports_documented = 114`, provenance-map entry count = 114

Per step-03 §4b the >10% pair divergence triggers a deterministic metadata-drift emission. However, the divergence is intentional by field definition: `exports_public_api` measures the `__init__.py` `__all__` barrel, while `exports_documented` measures the full per-method/per-member provenance surface (barrel + methods + op framework primitives + submodule members). Both clusters are internally consistent; no extraction drift is present.

**Remediation:** No content fix required. A future upstream improvement to `skf-create-skill` could either (a) add a `stats.exports_denominator_source` field that explicitly declares which count the denominator uses, or (b) rename `exports_documented` to `exports_documented_with_members` to make the distinction unambiguous. Until then, log this as an informational field-semantic divergence rather than a data-quality gap.

### Discovery Quality

**Description score:** 100% (tessl description_score). Trigger keywords strong: "cocoindex", "data indexing", "ETL", "RAG ingestion", "knowledge graphs", "vector search", "flow-building", "FlowBuilder", "DataScope", plus explicit negative trigger ("Do NOT use for authoring custom Rust engine components"). Specificity 3/3, trigger-term quality 3/3, completeness 3/3, distinctiveness 3/3. No description optimization needed.

### GAP-003: Discovery testing not performed

**Severity:** Info
**Category:** Coherence
**Source:** workflow state — no discovery testing run prior to this report.

**Issue:** Realistic prompt testing was not performed during this test workflow. A skill that passes static coverage and coherence checks can still fail to trigger in production if the description's trigger keywords don't match how users actually phrase requests (casual language, typos, abbreviations, implicit references).

**Remediation:** Before running `export-skill`, manually test the skill with 3–5 realistic prompts. Suggested patterns for cocoindex:

- Vague: "I need to build an embedding pipeline from a bunch of markdown files into postgres"
- Implicit: "how do I keep my vector DB in sync when documents change upstream"
- Abbreviated: "wire up cocoindex for a rag ingest flow with openai embeddings"
- Adjacent-domain: "what's the best way to do incremental indexing with LLM extraction and knowledge graph output to neo4j"
- Error-recovery: "my cocoindex flow_def isn't registering, what am I missing"

If the skill triggers on 4+ of 5 realistic prompts, it's production-ready. If it misfires on more than one, tune the description's trigger phrases before export.

This advisory is standard per step-04b §4b and does not affect the 99.0% score.

---

### Final Gap Counts

| Severity | Count |
|----------|-------|
| Critical | 0 |
| High | 0 |
| Medium | 0 |
| Low | 0 |
| Info | 3 (GAP-001, GAP-002, GAP-003) |

**Result:** **PASS** — **99.0%** (threshold 80%, headroom 19 points). Next workflow: **export-skill**.
