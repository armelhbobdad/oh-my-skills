# Evidence Report: uitripled

**Generated:** 2026-03-29
**Forge Tier:** Deep
**Source:** moumen-soliman/uitripled @ a5ffb45b

## Tool Versions
- ast-grep: 0.41.1
- QMD: unknown
- SKF: 0.8.0

## Extraction Summary
- Files scanned: 515 (571 total, 56 demo files excluded)
- Registry entries: 278 items → 177 unique components
- Exports found: 349 (311 component functions, 18 Props interfaces, 20 shared types)
- Confidence: T1=74, T1-low=311, T2=0, T3=0
- Extraction mode: component-library (registry-first, Props-focused)
- Design variants: shadcn/ui (171), Base UI (88), Carbon (10)

## Extraction Notes
- TSX `export function` pattern returned 0 AST results (ast-grep 0.41.x known limitation #5) — fell back to source reading for 311 component exports (T1-low)
- Props interfaces successfully extracted via AST with full JSDoc annotations (T1)
- Shared types extracted via AST from .ts files (T1)
- CCC semantic discovery post-clone: 20 relevant regions across 6 unique files
- Ephemeral clone with sparse-checkout (--no-cone mode) used for source access
- Version reconciliation: source v1.1.0 matches brief v1.1.0

## Enrichment Summary
- QMD enrichment attempted: temporal and docs collections searched
- Functions enriched: 0 of 18 (no matching results in QMD collections)
- T2 annotations: 0

## Validation Results
- Schema: PASS (score: 100/100)
- Frontmatter: PASS
- Body: PASS (156 lines after selective Tier 2 split to references/)
- Security: skipped (--no-security-scan, SNYK_TOKEN not configured)
- Content Quality (tessl): PASS (Description: 100%, Content: 73%, Average: ~86.5%)
- Metadata: PASS

## Quality Score Breakdown
- Frontmatter (30%): 30 | Description (30%): 30 | Body (20%): 20 | Links (10%): 10 | File (10%): 10

## Auto-Fixed Issues
- Selective split-body: extracted 3 Tier 2 sections (Full API Reference, Full Type Definitions, Full Integration Patterns) to references/
- tessl structural fix applied: trimmed overview metadata, consolidated 4 of 5 Props tables to native-components.md reference

## tessl Suggestions
- Applied (structural): trim overview metadata, consolidate Props tables to reference
- Skipped (semantic): add validation steps to workflows — would introduce unverified content

## Update Operation — 2026-03-29

**Trigger:** gap-driven (from test-report-uitripled.md)
**Forge Tier:** Deep
**Mode:** gap-driven

### Changes Detected
- Files modified: 0 (source unchanged)
- Exports new (undocumented): 3 (generateUniqueSlug, sanitizeSlug, GridPreviewProps)
- Exports modified (signature gap): 1 (NativeNotchProps onClick)
- Metadata updates: 1 (count claim)

### Extraction Findings
- `generateUniqueSlug` and `sanitizeSlug` located in `lib/builder-utils.ts` via DeepWiki MCP (T1-low)
- `GridPreviewProps` confirmed **phantom export** — not found in source repository (removed from metadata)
- NativeNotchProps `onClick` already in provenance-map (T1) — SKILL.md body was incomplete

### Merge Results
- Exports updated: 1 (NativeNotchProps — added onClick prop)
- Exports added: 2 (generateUniqueSlug, sanitizeSlug → references/full-api-reference.md)
- Exports removed: 1 (GridPreviewProps — phantom, removed from metadata.json)
- [MANUAL] sections preserved: 2 (after-quick-start, after-catalog)
- Conflicts resolved: 0

### Validation Summary
- Spec compliance: PASS (structural pre-check)
- [MANUAL] integrity: PASS (2/2 intact)
- Confidence tiers: PASS (2 exports at T1-low — remote MCP fallback)
- Provenance: PASS (2 new entries added)

## Warnings
- QMD version could not be detected (pip show qmd-plugin and pip show qmd both failed)
- No T2 enrichment annotations — uitripled temporal context returned empty QMD results
- 311 component function exports at T1-low confidence due to ast-grep TSX limitation
- Section blocks and page components have no external Props interfaces (self-contained with embedded data)
