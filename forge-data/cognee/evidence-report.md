# Evidence Report: cognee

**Generated:** 2026-03-19
**Forge Tier:** Deep
**Source:** topoteretes/cognee @ main

## Tool Versions
- ast-grep: 0.38.5 (CLI streaming --json=stream)
- QMD: 0.1.0 (3 collections: cognee-brief, cognee-temporal, cognee-docs)
- SKF: 1.0.0

## Extraction Summary
- Files scanned: 954 Python files (from 2,202 total in repo)
- Exports found: 837 (302 functions, 535 classes)
- Public API surface: 22 named exports from cognee/__init__.py
- Confidence: T1=837 (AST-verified), T1-low=0, T2=14 (QMD-enriched), T3=10 (doc-fetched)
- Extraction method: CLI streaming (>500 files in scope)
- Ephemeral clone: sparse-checkout --no-cone with include/exclude patterns
- Version reconciliation: source 0.5.5 = brief 0.5.5 (match)

## Temporal Context
- Issues fetched: 100
- Merged PRs fetched: 100
- Releases fetched: 10
- Targeted function searches: 10/10 completed
- QMD collection: cognee-temporal (4 files, 66 chunks)

## Documentation Fetch
- Root URL: https://docs.cognee.ai/ (Mintlify site)
- Subpages discovered: 24 (via firecrawl_map)
- Subpages fetched: 10 (API-relevant selection)
- QMD collection: cognee-docs (10 files, 10 chunks)

## Enrichment Summary
- Functions enriched: 7 of 10 top public API exports
- T2 annotations: 14 (10 T2-past historical, 4 T2-future forward-looking)

## Validation Results
- Schema: PASS (quality score: 100/100)
- Frontmatter: PASS (auto-fixed: description trigger format)
- Body: PASS (353 lines, under 500 limit)
- Security: skipped — SNYK_TOKEN not configured
- Content Quality (tessl): 83% average (Description: 100%, Content: 65%)
- Metadata: PASS

## Quality Score Breakdown
- Frontmatter (30%): 30 | Description (30%): 30 | Body (20%): 20 | Links (10%): 10 | File (10%): 10

## Auto-Fixed Issues
- Description reformatted to trigger-optimized "Use when" prefix by skill-check --fix

## Content Quality (tessl)
- tessl suggestions: 3 received, 0 applied
- All structural suggestions conflict with SKF spec (split-body handles reference splitting; [MANUAL] markers required for update-skill)
- Semantic suggestion (add validation steps) skipped — would add unverified content
- User selected [A] Apply structural fixes; no applicable fixes found

## Warnings
- No CHANGELOG.md found in repository root
- security_scan unavailable (SNYK_TOKEN not configured)
- delete() is deprecated since v0.3.9 — included with deprecation notice
- session namespace uses SimpleNamespace (not a class) — cited as T1-low
