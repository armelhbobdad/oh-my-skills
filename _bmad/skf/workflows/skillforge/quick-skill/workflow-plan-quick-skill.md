---
conversionFrom: 'src/workflows/quick-skill/quick-skill.spec.md'
originalFormat: 'Workflow Specification (spec.md)'
stepsCompleted: ['step-00-conversion', 'step-02-classification', 'step-03-requirements', 'step-04-tools', 'step-05-plan-review', 'step-06-design', 'step-07-foundation', 'step-08-build-step-01', 'step-09-build-steps-02-06']
created: 2026-02-26
status: VALIDATED
approvedDate: 2026-02-27
confirmationDate: 2026-02-27
confirmationType: conversion
coverageStatus: complete
validationDate: 2026-02-27
validationStatus: COMPLETE
validationReport: './validation-report.md'
---

# Workflow Creation Plan

## Conversion Source

**Original Path:** src/workflows/quick-skill/quick-skill.spec.md
**Original Format:** Workflow Specification (spec.md) — pre-designed blueprint with step table, inputs/outputs, and agent integration
**Detected Structure:** Single specification document defining a 6-step create-only workflow for brief-less skill generation from package names or GitHub URLs

---

## Original Workflow Analysis

### Goal (from source)

Brief-less fast skill with package-to-repo resolution. The fastest path to a skill — accepts a GitHub URL or package name, resolves to source, reads exports via source reading (no AST required), and produces a best-effort SKILL.md. No brief needed. Package-to-repo resolution handles npm/PyPI/crates.io names.

### Original Steps (Complete List)

**Step 1:** resolve-target - Resolve package name or URL to GitHub repo
**Step 2:** ecosystem-check - Search if official skill already exists
**Step 3:** quick-extract - Read source, extract public API surface
**Step 4:** compile - Assemble best-effort SKILL.md
**Step 5:** validate - Validate against spec
**Step 6:** write - Write skill files

### Output / Deliverable

Document-producing workflow generating three files:
- `{skills_output_folder}/{name}/SKILL.md` — Best-effort skill document
- `{skills_output_folder}/{name}/context-snippet.md` — Passive context for platform injection
- `{skills_output_folder}/{name}/metadata.json` — With `source_authority: community`

### Input Requirements

**Required:**
- GitHub URL or package name (npm/PyPI/crates.io)

**Optional:**
- Language hint
- Scope hint (specific directories)

### Key Instructions to LLM

- Uses Ferris agent persona (Architect mode) as primary agent
- No brief needed — this is a speed-first entry point
- Package-to-repo resolution via `manifest_reader` internal utility
- Source reading approach (no AST required) — reads exports directly
- Best-effort output quality — not full-depth skill analysis
- `source_authority: community` designation for all outputs

---

## Conversion Notes

**What works well in original:**
- Clear 6-step pipeline with well-defined boundaries between steps
- Smart input flexibility (URL or package name from multiple registries)
- Explicit output file list with metadata conventions
- Ecosystem-aware (checks for existing official skills before duplicating work)

**What needs improvement:**
- Spec only — no step-level implementation details exist yet
- No menu structures or user interaction points defined
- No data files or templates specified
- Step granularity may need adjustment during build (e.g., resolve-target could be complex)

**Compliance gaps identified:**
- No step files exist (need full creation, not conversion)
- No frontmatter definitions for steps
- No workflow.md entry point
- No data/ folder templates
- No validation mode steps defined (spec says create-only, which is valid)
- Need to define critical path and state tracking across steps

---

## Memory-Informed Discovery Notes

**Preserve:**
- 6-step linear pipeline matches proven create-skill pattern
- Ecosystem-check advisory gate pattern (5s timeout, graceful degradation, P/I/A menu only on match)
- `source_authority: community` correctly positions output in SKF authority hierarchy
- No-brief differentiator — alternative entry point to create-skill pipeline

**Address:**
- `manifest_reader` utility doesn't exist — need self-contained resolution logic or clear tool requirements
- No tier awareness needed — operates at fixed Quick-tier equivalent (best-effort)
- Need explicit error handling table (hard halt, graceful degradation, silent skip patterns)
- Step 03 "source reading" needs clear definition: README, manifest files, top-level exports

**Add:**
- Graceful fallback chain for resolution: GitHub URL direct > registry API lookup > web search > fail gracefully
- Advisory ecosystem-check following create-skill step-02 exact pattern
- Lighter validation for community source_authority tier
- Ferris Architect mode with tier-aware acknowledgment

**Audience:** Same SKF users — developers wanting fast community skill generation without full brief-skill > create-skill pipeline. Phase 1b (Entry Points) build priority.

---

## Classification Decisions

**Workflow Name:** quick-skill
**Target Path:** {project-root}/_bmad/skf/workflows/quick-skill/
**Build Path:** {bmb_creations_output_folder}/workflows/quick-skill/

**4 Key Decisions:**
1. **Document Output:** true — produces SKILL.md, context-snippet.md, metadata.json
2. **Module Affiliation:** skf — part of Skills Knowledge Framework module
3. **Session Type:** single-session — speed-first, 6 focused steps, best-effort output
4. **Lifecycle Support:** create-only — steps-c/ only, no edit/validate modes

**Structure Implications:**
- Needs `steps-c/` directory only (no steps-e/ or steps-v/)
- Standard `step-01` init (no continuation logic, no step-01b-continue)
- Document-producing: steps contribute progressively to output files
- Module-based: has access to SKF-specific variables (skills_output_folder, forge-tier, etc.)
- No stepsCompleted tracking needed in output document (single-session)

---

## Requirements

**Flow Structure:**
- Pattern: linear
- Phases: resolve input (01), dedup check (02), extraction (03), compilation (04), validation (05), output (06)
- Estimated steps: 6
- Conditional branch: step-02 ecosystem-check shows P/I/A menu only if match found, otherwise auto-proceeds

**User Interaction:**
- Style: mostly autonomous
- Decision points: step-01 (user provides input), step-02 (conditional — only if ecosystem match), step-04 (optional checkpoint to review compiled SKILL.md)
- Checkpoint frequency: minimal — speed-first design, most steps auto-proceed (P3)

**Inputs Required:**
- Required: GitHub URL or package name (npm/PyPI/crates.io)
- Optional: language hint, scope hint (specific directories)
- Prerequisites: none — this is the brief-less entry point, no setup-forge or brief-skill needed

**Output Specifications:**
- Type: multi-file document output
- Files:
  - `{skills_output_folder}/{name}/SKILL.md` — structured template following agentskills.io spec sections
  - `{skills_output_folder}/{name}/context-snippet.md` — ADR-L v2 format (~50-80 tokens)
  - `{skills_output_folder}/{name}/metadata.json` — strict JSON with `source_authority: community`
- Format: structured (SKILL.md), strict (context-snippet.md, metadata.json)
- Frequency: single run per skill

**Success Criteria:**
- Package/URL successfully resolved to GitHub repo source
- Public exports documented (best-effort, may be incomplete)
- Valid SKILL.md with core sections populated
- context-snippet.md in correct ADR-L v2 format
- metadata.json with `source_authority: community` and required fields
- No ecosystem duplicate if official skill already exists (user chose to proceed)

**Instruction Style:**
- Overall: prescriptive
- Notes: mechanical pipeline with exact operations per step. Ferris Architect mode provides precision execution. Matches Tax Organizer / SOP Writer pattern — focused questions, specific operations, no creative facilitation.

---

## Tools Configuration

**Core BMAD Tools:**
- **Party Mode:** excluded — prescriptive pipeline, no creative facilitation needed
- **Advanced Elicitation:** excluded — mechanical steps, no deep exploration needed
- **Brainstorming:** excluded — no ideation phases

**LLM Features:**
- **Web-Browsing:** included — critical for step-01 (registry API lookups, package-to-repo resolution), step-02 (ecosystem search), step-03 (reading GitHub source)
- **File I/O:** included — step-03 reads source files, step-06 writes three output files
- **Sub-Agents:** excluded — linear pipeline, no parallelization needed
- **Sub-Processes:** excluded — linear pipeline, no parallelization needed

**Memory:**
- Type: single-session
- Tracking: none — no complex state management needed

**External Integrations:**
- None required — web-browsing handles registry lookups and GitHub access

**Installation Requirements:**
- None — all selected tools are built-in

**Workflow Structure Preview:**

| Phase | Step | Name | Purpose | Menu |
|-------|------|------|---------|------|
| 1 | 01 | resolve-target | Accept input, resolve package/URL to GitHub repo | Init — user provides input |
| 2 | 02 | ecosystem-check | Query agentskills.io for existing official skill | Conditional P/I/A (match only) |
| 3 | 03 | quick-extract | Read source, extract public API surface | P3 auto-proceed |
| 4 | 04 | compile | Assemble SKILL.md, context-snippet, metadata | P2 checkpoint (review output) |
| 5 | 05 | validate | Validate against agentskills.io spec (community tier) | P3 auto-proceed |
| 6 | 06 | write | Write files to output folder, display summary | Final step |

---

## Workflow Design

### File Structure

```
quick-skill/
├── workflow.md                         # Entry point
├── data/
│   ├── skill-template.md              # SKILL.md section template
│   └── registry-resolution.md         # Package-to-repo resolution patterns
└── steps-c/
    ├── step-01-resolve-target.md
    ├── step-02-ecosystem-check.md
    ├── step-03-quick-extract.md
    ├── step-04-compile.md
    ├── step-05-validate.md
    └── step-06-write.md
```

### Step Sequence Table

| # | Name | Type | Menu | Frontmatter Refs |
|---|------|------|------|-----------------|
| 01 | resolve-target | Init (non-continuable) | User input → auto-proceed | nextStepFile, registryResolutionData |
| 02 | ecosystem-check | Middle (Simple) | Conditional P/I/A if match, else P3 | nextStepFile |
| 03 | quick-extract | Middle (Simple) | P3 auto-proceed | nextStepFile |
| 04 | compile | Middle (Simple) | P2 (C only) checkpoint | nextStepFile, skillTemplateData |
| 05 | validate | Middle (Simple) | P3 auto-proceed | nextStepFile |
| 06 | write | Final | No next step | — |

### Step Action Plans

**Step 01 — resolve-target (Init):**
- Accept user input: GitHub URL or package name
- If GitHub URL: validate URL format, extract org/repo
- If package name: resolution fallback chain (from registry-resolution.md data):
  1. npm registry API → extract `repository.url`
  2. PyPI API → extract `project_urls.Source`
  3. crates.io API → extract `repository`
  4. Web search fallback → find GitHub repo
- Accept optional: language hint, scope hint
- Set state: resolved_url, repo_name, language_hint, scope_hint
- Auto-proceed to step-02

**Step 02 — ecosystem-check (Conditional):**
- Query agentskills.io ecosystem for repo_name skill
- 5-second timeout, tool unavailability = silent skip
- No match: auto-proceed to step-03 (no user interaction)
- Match found: conditional menu P/I/A
  - [P] Proceed — compile custom skill anyway
  - [I] Install — install existing official skill (exit workflow)
  - [A] Abort — cancel compilation

**Step 03 — quick-extract (Auto-proceed):**
- Read repo README.md for description, features, usage
- Read manifest file (package.json / pyproject.toml / Cargo.toml)
- Scan top-level exports (index.js/ts, __init__.py, lib.rs)
- If scope hint: focus on specified directories
- Extract: export names, function signatures, type definitions (surface-level)
- No AST — grep/pattern-based extraction
- Set state: extraction_inventory
- Auto-proceed to step-04

**Step 04 — compile (Checkpoint):**
- Load skill-template.md from data/
- Assemble SKILL.md from extraction_inventory
- Generate context-snippet.md in ADR-L v2 format (~50-80 tokens)
- Generate metadata.json with source_authority: community
- Present compiled SKILL.md for review
- [C] Continue to validation

**Step 05 — validate (Auto-proceed):**
- Check SKILL.md has required sections populated
- Check context-snippet.md format compliance (ADR-L v2)
- Check metadata.json has required fields
- Community-tier validation (lighter than official)
- Report any gaps/issues
- Auto-proceed to step-06

**Step 06 — write (Final):**
- Create output directory: {skills_output_folder}/{name}/
- Write SKILL.md, context-snippet.md, metadata.json
- Display summary: files written, paths, token estimate
- Recommend next: test-skill (advisory), export-skill

### Data Flow

```
step-01 → resolved_url, repo_name, language_hint, scope_hint
    ↓
step-02 → ecosystem_status (match/no-match/skip)
    ↓
step-03 → extraction_inventory (exports, description, manifest_data)
    ↓
step-04 → skill_content (SKILL.md), context_snippet, metadata_json
    ↓
step-05 → validation_result (pass/fail, issues_list)
    ↓
step-06 → writes files, displays summary
```

### Error Handling

| Error | Response |
|-------|----------|
| Unresolvable package name | Hard halt — cannot proceed without source |
| GitHub repo inaccessible | Hard halt — need source to extract |
| Ecosystem check tool unavailable | Silent skip — proceed as no-match |
| Ecosystem check timeout (>5s) | Silent skip — proceed as no-match |
| No exports found in source | Graceful — minimal SKILL.md from README |
| Validation failures | Advisory — report issues, allow proceed |
| File write failure | Hard halt — cannot complete without output |

### Workflow Chaining

- **Prerequisites:** none (brief-less entry point)
- **Alternative to:** brief-skill → create-skill pipeline
- **Recommended next:** test-skill (advisory), export-skill
- **Output contract:** {skills_output_folder}/{name}/ with SKILL.md, context-snippet.md, metadata.json

### Subprocess Optimization

No subprocess optimization needed — linear pipeline, no parallelization opportunities.

### Role and Persona

Ferris — Architect mode. Prescriptive precision execution, speed-first, no creative facilitation.

---

## Foundation Build Complete

**Created:**
- Folder structure at: {bmb_creations_output_folder}/workflows/quick-skill/
- workflow.md — entry point with SKF config loading, Ferris rapid compiler role
- data/skill-template.md — SKILL.md section structure, context-snippet format (ADR-L), metadata.json format
- data/registry-resolution.md — package-to-repo resolution fallback chain (npm/PyPI/crates.io/web search)
- steps-c/ directory — ready for step file creation

**Configuration:**
- Workflow name: quick-skill
- Continuable: no (single-session)
- Document output: yes — multi-file (SKILL.md, context-snippet.md, metadata.json)
- Mode: create-only (steps-c/ only)
- Module config: {project-root}/_bmad/skf/config.yaml
- Module variables: skills_output_folder, forge_data_folder

**Next Steps:**
- Step 8: Build step-01-resolve-target (Init)
- Step 9: Build remaining steps 02-06 (repeatable)

---

## Step 01 Build Complete

**Created:**
- steps-c/step-01-resolve-target.md

**Step Configuration:**
- Type: Init (non-continuable, no input discovery)
- Menu: Auto-proceed after successful resolution
- Next Step: step-02-ecosystem-check
- Data ref: registry-resolution.md for fallback chain
- No step-01b (single-session workflow)

**Supporting Files:**
- data/registry-resolution.md (created in foundation)

---

## Steps 02-06 Build Complete

**Created:**
- steps-c/step-02-ecosystem-check.md (143 lines) — Conditional advisory gate, P/I/A on match, auto-proceed on no-match/skip
- steps-c/step-03-quick-extract.md (177 lines) — Surface-level source reading, extraction inventory, auto-proceed
- steps-c/step-04-compile.md (180 lines) — Assembles SKILL.md/snippet/metadata from inventory, P2 checkpoint for review
- steps-c/step-05-validate.md (150 lines) — Community-tier advisory validation, auto-proceed
- steps-c/step-06-write.md (160 lines) — Final step, writes files, displays summary, recommends next workflows

**All step files within size limits except step-01 (165 vs 150 Init guideline — minor, 15 lines over)**

**Complete file manifest:**
- workflow.md (56 lines)
- data/skill-template.md (66 lines)
- data/registry-resolution.md (91 lines)
- steps-c/step-01-resolve-target.md (165 lines)
- steps-c/step-02-ecosystem-check.md (143 lines)
- steps-c/step-03-quick-extract.md (177 lines)
- steps-c/step-04-compile.md (180 lines)
- steps-c/step-05-validate.md (150 lines)
- steps-c/step-06-write.md (160 lines)
- Total: 10 files, 1188 lines
