# Evidence Report: oms-cocoindex

**Generated:** 2026-04-11
**Forge Tier:** Deep
**Source:** https://github.com/cocoindex-io/cocoindex @ `87c5dbf087bfccca83791861db0d33519ef09677` (tag `v0.3.37`)

## Tool Versions

- ast-grep: 0.42.0
- QMD: 2.0.1
- SKF: 1.0.0

## Extraction Summary

- **Files scanned:** 25 Python source files + 1 promoted authoritative doc (CLAUDE.md)
- **Public exports found:** 102 (55 public-API from `__init__.py.__all__` + 47 internal/module-scoped)
- **Confidence distribution:** T1 = 102 (AST-verified), T1-low = 0, T2 = 15 (QMD enrichment), T3 = 10 (docs fetch)
- **AST extraction method:** `ast-grep run --json=stream` (ast-grep 0.42.0) on each source file individually, pattern `def $NAME($$$P)` + `class $NAME` filtered by `^[^_]` regex.

**Authoritative files scan (§2a):** 1 candidate, 1 promoted (`CLAUDE.md`), 0 skipped, 0 pre-decided.
**CCC discovery:** Deferred (remote source); not executed — brief include-patterns are highly targeted (~30 files), matching the pattern used by peer skills in this project where pre-ranking offers no value.
**Description sanitizations:** 0 (no angle brackets in assembled description).
**Version reconciliation:** `pyproject.toml` uses `dynamic = ["version"]`, so no source-side version found. Brief version `0.3.37` preserved. Source cloned at tag `v0.3.37` (commit `87c5dbf0`).

**QMD collections indexed during this run:**
- `oms-cocoindex-temporal` (4 files, 73 chunks) — issues, merged PRs, releases, targeted function searches
- `oms-cocoindex-docs` (11 files, 16 chunks) — quickstart, flow_def, flow_methods, basics, settings, functions, llm, custom_functions, postgres_target, localfile_source, INDEX

**Note on extraction method:** AST-grep CLI (`run -p ... --json=stream`) was used instead of the MCP tool path because the MCP `find_code_by_rule` failed on the protocol's YAML rule (metaclass kwarg parsing) and the simple `find_code` with no file scoping exceeded the MCP output size cap on the whole source tree. Streaming the scoped file list per-file produced clean JSON Lines output parsed by a one-off Python filter. All citations remain T1 (AST-verified). Log this as a toolchain observation for future refinement.

## Validation Results

- Schema: PASS (quality score 100/100, 0 errors, 0 warnings)
- Frontmatter: PASS
- Body: PASS (434 lines, well under 500-line split-body threshold)
- Security: skipped (--no-security-scan; SNYK_TOKEN not configured)
- Content Quality (tessl): WARN (review_score 80%, content_score 50%, description_score 100%)
- Metadata: PASS (provenance-map 114 entries, confidence distribution + stats reconciled)

## Quality Score Breakdown

- Frontmatter (30%): 30 | Description (30%): 30 | Body (20%): 20 | Links (10%): 10 | File (10%): 10

## Description Guard

- Restored: false
- Triggering tool: —
- Original description preserved: —
- Notes: —

## Auto-Fixed Issues

Round 1 (skill-check --fix): 4 false-positive "broken local link" warnings from `ClassName[T](...)` patterns being mis-parsed as markdown links inside code spans. Manually rewrote the 4 affected class signatures (AuthEntryReference, PartialSourceRowData, PartialSourceRow, QueryOutput) to put the generic brackets and the field list in separate backticked fragments. Re-validation: score 90 → 100, 4 warnings → 0.

## Dismissed tessl Suggestions

- **`move-full-api-reference` rule match** — tessl suggested: "Move the entire 'Full API Reference' section into the referenced files". Dismissed per rule: two-tier SKF design keeps Tier 2 sections inline by default; `skill-check split-body` relocates only when size limits are hit. Body is 434 lines (below 500 threshold).
- **`conciseness-redundancy-between-tiers` rule match** — tessl content_score 50% cited redundancy between Key API Summary and Full API Reference. Dismissed per rule: progressive disclosure is intentional design; Tier 1 summary is discoverability-optimized while Tier 2 is deep reference.
- **Novel: Remove AST provenance annotations** — tessl suggested removing `[AST:python/cocoindex/flow.py:Lxx]` citations from the main skill body, framing them as token overhead. Dismissed on design grounds: SKF's zero-hallucination tolerance requires every instruction to cite source. Removing provenance would break `skf-update-skill`'s drift detection (it uses citation line numbers to re-locate exports after source changes) and make `skf-audit-skill` unable to verify content against the source tree. Provenance is load-bearing infrastructure, not decorative metadata.
- **Novel: Add validation/error-recovery steps to workflows** — tessl suggested adding error-handling guidance (e.g., "if setup fails, try this"). Dismissed: SKF's zero-hallucination rule bars content not verified from source. cocoindex's actual error-recovery behavior is not documented in source — adding it would be hallucinated guidance marked with `[TESSL:auto-fix]`/`[TESSL:suggestion]`. Users who need error recovery can consult upstream issues and docs (indexed in the QMD temporal/docs collections, accessible via `mem-search`).
- **Novel: Trim the Key Types section** — tessl suggested pruning the inline enum lists. Dismissed: Key Types is already minimal (3 enum groups + 1 property + 8 type aliases); trimming further would remove the discoverability-critical inline summary of `VectorSimilarityMetric`, `LlmApiType`, and `GeneratedField.UUID` that the context-snippet directly references.

## Remaining Warnings

- **Tessl content_score 50% (below 60 floor)** — triggered by intentional two-tier design trade-off. Logged per dismissal-rules threshold table; no action required.
- MCP `find_code_by_rule` failed on the protocol YAML rule due to tree-sitter metaclass kwarg parsing; extraction used CLI streaming (`ast-grep run --json=stream`) instead. Both paths produce T1-confidence citations. [observed during step-03]
- ast-grep `class $NAME:` and `class $NAME($$$B):` patterns returned zero results on Python sources (apparent pattern-parser quirk). The plain `class $NAME` pattern worked when run per-file with explicit file args — extraction used this variant.

## Security Findings

- Skipped — `--no-security-scan` flag set; SNYK_TOKEN not configured in environment. Security scanning is optional and does not block compilation.

## Content Quality (tessl)

```
Overall:       PASSED (0 errors, 0 warnings)
Description:   100% (specificity 3/3, trigger_term_quality 3/3, completeness 3/3, distinctiveness 3/3)
Content:       50%  (conciseness 1/3, actionability 3/3, workflow_clarity 2/3, progressive_disclosure 2/3)
Review Score:  80%
```

Conciseness 1/3 is expected for Deep-tier full-library skills — the 102-line Full API Reference is the split-body target, not extraneous content. The score threshold table in `tessl-dismissal-rules.md` sets `content_score >= 60` as warning threshold; 50% is below but acceptable given the two-tier design rationale cited above.
