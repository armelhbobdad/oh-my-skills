---
nextStepFile: './step-10-health-check.md'
---

# Step 9: Stack Skill Report

## STEP GOAL:

Display the final summary of the forged stack skill with confidence distribution, output file listing, and next workflow recommendations.

## Rules

- Do not write or modify any files — report is console output only
- Lead with the positive summary, then details, then warnings
- Recommend next workflows based on what was produced
- Chains to the local health-check step via `{nextStepFile}` after completion — the user-facing report is NOT the terminal step

## MANDATORY SEQUENCE

**CRITICAL:** Follow this sequence exactly. Do not skip, reorder, or improvise.

### 1. Display Stack Forged Banner

"**Stack forged: {project_name}-stack — {lib_count} libraries, {integration_count} integration patterns**

Forge tier: **{tier}**"

### 2. Display Confidence Distribution

"**Confidence distribution:**

| Tier | Count | Description |
|------|-------|-------------|
| T1 | {count} | AST-verified structural extraction |
| T1-low | {count} | Source reading inference |
| T2 | {count} | QMD-enriched temporal context |

{IF compose_mode:}
*Note: Confidence tiers above are inherited from source skills — they reflect the extraction method used when those skills were originally generated, not the current compose run.*
{END IF}"

### 3. Display Output File Summary

"**Output files:**

**Deliverables** (`{skill_package}`):
- SKILL.md — Integration patterns, library summaries, conventions
- context-snippet.md — Compressed stack index ({token_estimate} tokens)
- metadata.json — Skill metadata and library registry
- references/ — {lib_count} per-library reference files
{If integrations:} - references/integrations/ — {pair_count} integration pair files

**Workspace** (`{forge_version}`):
- provenance-map.json — Extraction source tracking
- evidence-report.md — Evidence and confidence breakdown

**Symlink:** `{skill_group}/active` -> `{version}`"

### 4. Display Validation Summary

**If validation passed with no findings:**

"**Validation:** All checks passed"

**If validation had findings:**

"**Validation:** {warning_count} warning(s) found
{For each finding:}
- ⚠ {description}"

### 5. Display Warnings (Conditional)

**Only display if warnings exist from any step:**

"**Warnings:**
{For each warning from steps 04, 05, 07, 08:}
- {warning_description}"

**If no warnings:** Skip this section entirely.

### 6. Recommend Next Workflows

"**Next steps:**
- **[TS] test-skill** — Validate the stack skill against its own assertions
- **[EX] export-skill** — Package for distribution or agent loading

- **[VS] verify-stack** — Validate the stack's integration feasibility against your architecture document{IF compose_mode:} (re-run to confirm feasibility after any architecture changes from **[RA] refine-architecture**){END IF}"

### 6b. Result Contract

Write the result contract per `shared/references/output-contract-schema.md`: the per-run record at `{forge_version}/create-stack-skill-result-{YYYYMMDD-HHmmss}.json` (UTC timestamp, resolution to seconds) and a copy at `{forge_version}/create-stack-skill-result-latest.json` (stable path for pipeline consumers — copy, not symlink). Include `SKILL.md`, `context-snippet.md`, and `metadata.json` paths in `outputs`; include `lib_count`, `integration_count`, and confidence distribution in `summary`.

### 7. Chain to Health Check

ONLY WHEN the forge banner, confidence distribution, output file summary, validation summary, warnings (if any), next-workflow recommendations, and result contract have all been handled will you then load, read the full file, and execute `{nextStepFile}`. The health-check step is the true terminal step — do not stop here even though the report reads as final.

