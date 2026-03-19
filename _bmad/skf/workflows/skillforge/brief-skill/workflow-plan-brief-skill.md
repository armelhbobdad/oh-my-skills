---
conversionFrom: 'src/workflows/brief-skill/brief-skill.spec.md'
originalFormat: 'specification-document'
stepsCompleted: ['step-00-conversion', 'step-02-classification', 'step-03-requirements', 'step-04-tools', 'step-05-plan-review', 'step-06-design', 'step-07-foundation', 'step-08-build-step-01', 'step-09-build-all-steps', 'step-10-confirmation']
created: 2026-02-27
status: CONFIRMED
approvedDate: 2026-02-27
confirmationDate: 2026-02-27
confirmationType: conversion
coverageStatus: complete
validationStatus: COMPLETE
validationDate: 2026-02-27
validationReport: './validation-report.md'
---

# Workflow Creation Plan

## Conversion Source

**Original Path:** src/workflows/brief-skill/brief-skill.spec.md
**Original Format:** Specification document (placeholder — not yet built)
**Detected Structure:** Single spec file defining a 5-step create-only workflow with entry point frontmatter, planned step table, input/output definitions, and agent integration notes

---

## Original Workflow Analysis

### Goal (from source)

Scope and design a skill through guided discovery. Interactive workflow that helps the user define what to skill — target repo, scope (full library vs subset), language, inclusion/exclusion patterns. Produces a skill-brief.yaml that drives create-skill.

### Original Steps (Complete List)

**Step 1:** gather-intent - Understand what the user wants to skill
**Step 2:** analyze-target - Examine source repo structure and exports
**Step 3:** scope-definition - Define inclusion/exclusion boundaries
**Step 4:** confirm-brief - Present brief summary for user confirmation
**Step 5:** write-brief - Generate skill-brief.yaml

### Output / Deliverable

- `{forge_data_folder}/{skill-name}/skill-brief.yaml` — Compilation config that drives the create-skill workflow

### Input Requirements

**Required:**
- Target repo (GitHub URL or local path)
- User intent (what to skill and why)

**Optional:**
- Scope hints (specific directories, files, or patterns)
- Language override

### Key Instructions to LLM

- Spec designates Ferris (Architect mode) as the primary agent
- Create-only mode (steps-c/ only) — no edit or validate modes specified
- Document-producing workflow (outputs skill-brief.yaml)
- No explicit collaborative style defined yet — to be designed during conversion

---

## Conversion Notes

**What works well in original:**
- Clear 5-step progression from intent gathering through output generation
- Clean separation of concerns: gather → analyze → scope → confirm → write
- Well-defined input/output contract (repo path in, skill-brief.yaml out)
- Sensible agent assignment (Ferris in Architect mode)

**What needs improvement:**
- No step file content exists — only step names and one-line goals
- No menu handling, continuation logic, or user interaction patterns defined
- No frontmatter variable definitions for the step files
- No collaborative facilitation approach specified
- Output path uses `{forge_data_folder}` which needs resolution against module config
- No validation or error handling patterns

**Compliance gaps identified:**
- Missing: Complete step files with BMAD step-file architecture
- Missing: Frontmatter with proper variables (nextStepFile, etc.)
- Missing: Menu handling and continuation patterns
- Missing: Mandatory execution rules per step
- Missing: State tracking via stepsCompleted
- Missing: workflow.md entry point file
- Missing: Step processing rules and critical rules sections

---

## Memory-Informed Discovery Notes

### Preserve
- 5-step interactive discovery pipeline (gather → analyze → scope → confirm → write)
- Input contract: GitHub URL or local path + user intent
- Confirm-before-write gate (step 04 → 05) as collaborative checkpoint
- Phase 1b Entry Point positioning feeding into create-skill pipeline

### Address
- skill-brief.yaml must produce fields create-skill step-01-load-brief validates: name, version, source_repo, language, scope
- {forge_data_folder} path variable needs resolution against SKF sidecar/config
- No error handling patterns defined (inaccessible repo, failed analysis)
- No collaborative facilitation style specified

### Add
- Forge tier awareness: detect available tier from forge-tier.yaml to scope appropriately
- Ecosystem check: verify if official skill already exists (pattern from create-skill/quick-skill step-02)
- Multi-language detection: auto-detect primary language during analyze-target
- Scope templates: common scoping patterns as selectable options (full library, specific modules, public API only)

### Audience
- Developers using SKF module to create agent skills
- Ferris in Architect mode (exploratory, collaborative) — interactive discovery workflow
- Phase 1b Entry Points build priority

---

## Classification Decisions

**Workflow Name:** brief-skill
**Target Path:** {project-root}/_bmad/skf/workflows/brief-skill/

**4 Key Decisions:**
1. **Document Output:** true — produces skill-brief.yaml as persistent compilation config
2. **Module Affiliation:** SKF (Skill Forge module)
3. **Session Type:** single-session — focused scoping conversation, ~10-15 minutes
4. **Lifecycle Support:** create-only — steps-c/ only

**Structure Implications:**
- Single `steps-c/` directory for create steps
- No `step-01b-continue.md` needed (single-session)
- No `steps-e/` or `steps-v/` directories
- Document-producing: each step contributes progressively toward skill-brief.yaml
- SKF module variables available (forge_data_folder, forge tier config)
- Standard init step without continuation detection

---

## Requirements

**Flow Structure:**
- Pattern: Linear — 5 steps in sequence with confirmation gate at step 04
- Phases: Discovery (01) → Analysis (02) → Scoping (03) → Confirmation (04) → Output (05)
- Estimated steps: 5

**User Interaction:**
- Style: Guided session with collaborative discovery (Ferris Architect mode)
- Steps 01, 03: Highly collaborative — open-ended discovery facilitation
- Step 02: Mostly autonomous — Ferris reads repo, reports findings
- Step 04: Mandatory user checkpoint (P2 confirmation gate)
- Step 05: Autonomous — write YAML output
- Decision points: Target repo + intent (01), scope boundaries (03), approve brief (04)
- Checkpoint frequency: Menus at steps 01, 03, 04

**Inputs Required:**
- Required: Target repo (GitHub URL or local path), user intent (what to skill and why)
- Optional: Scope hints (directories, files, patterns), language override, forge tier preference
- Prerequisites: setup-forge completed (provides forge-tier.yaml with tier and tool availability)

**Output Specifications:**
- Type: Document (skill-brief.yaml)
- Format: Structured YAML with required fields
- Required fields: name, version, source_repo, language, scope (type, include, exclude), description, forge_tier, created, created_by
- Output path: {forge_data_folder}/{skill-name}/skill-brief.yaml
- Pattern: Direct-to-final — steps progressively gather data, step 05 writes complete YAML
- Frequency: Single output per run

**Success Criteria:**
- Valid skill-brief.yaml written to {forge_data_folder}/{skill-name}/
- All required fields present and valid (name, version, source_repo, language, scope)
- Source repo accessible (GitHub URL resolves or local path exists)
- Language correctly identified (auto-detected or user-specified)
- Scope boundaries clear and actionable for create-skill consumption
- User confirmed the brief before writing (step 04 gate passed)

**Instruction Style:**
- Overall: Mixed
- Intent-based: Steps 01, 03 — open-ended discovery ("What interests you about this library?", "Which parts are most relevant?")
- Prescriptive: Step 02 — exact analysis instructions (read repo structure, detect language, list exports)
- Prescriptive: Steps 04, 05 — exact presentation format and YAML generation rules
- Notes: Ferris Architect persona — exploratory, collaborative, zero-hallucination for analysis results

---

## Tools Configuration

**Core BMAD Tools:**
- **Party Mode:** excluded — focused discovery pipeline, not creative brainstorming
- **Advanced Elicitation:** included as menu option [A] — available at steps 01, 03 for deeper intent/scope exploration
- **Brainstorming:** excluded — scoping is analytical, not generative

**LLM Features:**
- **Web-Browsing:** included — Step 02 may resolve GitHub URLs, read READMEs, check package registries
- **File I/O:** included — Step 02 reads repo structure (local paths), Step 05 writes skill-brief.yaml, reads forge-tier.yaml
- **Sub-Agents:** excluded — linear 5-step pipeline with no parallelizable work
- **Sub-Processes:** excluded — no parallel workflows needed

**Memory:**
- Type: single-session
- Tracking: No sidecar-file needed; skill-brief.yaml is the persistent artifact
- State: Minimal — data accumulated across steps, written at step 05

**External Integrations:**
- gh CLI — reading GitHub repository structures (pre-detected by setup-forge)

**Installation Requirements:**
- None — all tools are built-in or pre-detected by setup-forge

## Workflow Structure Preview

**Phase 1: Initialization (Step 01 - gather-intent)**
- Welcome user, explain brief-skill purpose
- Ask target repo URL/path and user intent
- Capture scope hints upfront
- Collaborative facilitation — open-ended discovery

**Phase 2: Analysis (Step 02 - analyze-target)**
- Load forge-tier.yaml for tier capabilities
- Read target repo structure (gh CLI or local filesystem)
- Auto-detect primary language
- List top-level modules, directories, exports
- Report findings to user (mostly autonomous)

**Phase 3: Scoping (Step 03 - scope-definition)**
- Present scope templates (full library / specific modules / public API only)
- Discuss inclusion/exclusion patterns
- Define boundaries collaboratively

**Phase 4: Confirmation (Step 04 - confirm-brief)**
- Present complete brief in human-readable format
- Show all fields for YAML output
- P2 confirmation gate — approve or revise

**Phase 5: Output (Step 05 - write-brief)**
- Generate skill-brief.yaml with all fields
- Write to {forge_data_folder}/{skill-name}/
- Report success, suggest create-skill as next step

---

## Workflow Design

### File Structure

```
brief-skill/
├── workflow.md                          # Entry point
├── data/
│   └── skill-brief-schema.md           # Required fields, validation rules, YAML template
└── steps-c/
    ├── step-01-gather-intent.md
    ├── step-02-analyze-target.md
    ├── step-03-scope-definition.md
    ├── step-04-confirm-brief.md
    └── step-05-write-brief.md
```

### Step Sequence Table

| # | Step Name | Type | Menu Pattern | Frontmatter Refs |
|---|-----------|------|-------------|-----------------|
| 01 | gather-intent | Init (with Input Discovery) | P2 (C only) | nextStepFile, forgeTierFile |
| 02 | analyze-target | Middle (Simple) | P3 (Auto-proceed) | nextStepFile |
| 03 | scope-definition | Middle (Standard) | P1 (A/P/C) | nextStepFile, advancedElicitationTask, partyModeWorkflow |
| 04 | confirm-brief | Middle (Standard) | Custom (R/A/P/C) | nextStepFile, reviseStepFile, briefSchemaFile, advancedElicitationTask, partyModeWorkflow |
| 05 | write-brief | Final | None | briefSchemaFile |

### Step Action Plans

**Step 01 — gather-intent:**
1. Load forge-tier.yaml from Ferris sidecar (input discovery pattern)
2. If missing → warn, default to Quick tier
3. Welcome user, explain brief-skill purpose and pipeline position
4. Ask: "What do you want to skill?" — target repo URL or local path
5. Ask: "What's your intent?" — why this skill, what use case
6. Capture any upfront scope hints
7. Derive skill name from target (user can override)
8. Menu: [C] Continue

**Step 02 — analyze-target:**
1. Resolve target: GitHub URL via gh api or validate local path
2. If inaccessible → halt with actionable error
3. Read repo structure (top-level files, directories)
4. Detect primary language from file extensions and config files
5. If language ambiguous → flag for user in step 03
6. List top-level modules/directories and public exports
7. Report findings summary to user
8. Auto-proceed to step 03

**Step 03 — scope-definition:**
1. Present analysis findings as context
2. Offer scope templates: [F] Full library, [M] Specific modules, [P] Public API only
3. Based on selection, guide inclusion/exclusion pattern definition
4. For "Specific modules" → present directory list, let user select
5. For "Public API only" → show detected exports, confirm boundaries
6. Summarize scope decisions
7. Menu: [A] Advanced Elicitation [P] Party Mode [C] Continue

**Step 04 — confirm-brief:**
1. Load skill-brief-schema.md for field reference
2. Present complete brief in human-readable format showing all YAML fields
3. Highlight any fields with low confidence or defaults
4. Menu: [R] Revise (→ reload step 03) [A] Advanced Elicitation [P] Party Mode [C] Continue

**Step 05 — write-brief:**
1. Load skill-brief-schema.md for YAML template
2. Generate complete skill-brief.yaml
3. Create directory {forge_data_folder}/{skill-name}/
4. Write skill-brief.yaml
5. Display success summary
6. Recommend next: "Run create-skill to compile your skill from this brief"
7. Mark workflow complete

### Data Flow

```
Step 01: user_intent, target_repo, scope_hints, skill_name, forge_tier
    ↓
Step 02: detected_language, repo_structure, export_list, module_list
    ↓
Step 03: scope_type, include_patterns, exclude_patterns
    ↓
Step 04: complete_brief_preview → user confirmation (or [R] revise → step 03)
    ↓
Step 05: all accumulated state → skill-brief.yaml file
```

### Error Handling

| Error Scenario | Step | Response |
|---------------|------|----------|
| forge-tier.yaml missing | 01 | Warn, default to Quick tier, continue |
| Target repo inaccessible | 02 | Hard halt with actionable error |
| Language can't be detected | 02 | Flag for manual override in step 03 |
| No exports found | 02 | Warn, suggest full-library scope |
| User rejects brief | 04 | [R] loops back to step 03 |
| Write failure | 05 | Hard halt with error |

### Workflow Chaining

**Prerequisites:**
- setup-forge → provides forge-tier.yaml (optional, defaults to Quick if missing)

**Next workflows:**
- create-skill → consumes skill-brief.yaml (recommended)
- test-skill → after create-skill completes

**Alternative entry:**
- quick-skill → brief-less path, skips entire brief-skill workflow

### Subprocess Optimization

No high-priority subprocess opportunities. Linear interactive workflow against a single repo — main thread execution appropriate for all steps.

### Role and Persona

- Ferris in Architect mode — exploratory, collaborative, warm
- Zero-hallucination for analysis results (step 02 reports only what's found)
- Guiding tone for discovery (steps 01, 03)
- Precise, structured presentation for confirmation (step 04)
- Efficient and clean for output (step 05)
