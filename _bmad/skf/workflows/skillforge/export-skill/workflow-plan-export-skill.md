---
conversionFrom: 'src/workflows/export-skill/export-skill.spec.md'
originalFormat: 'Workflow Specification (pre-implementation blueprint)'
stepsCompleted: ['step-00-conversion', 'step-02-classification', 'step-03-requirements', 'step-04-tools', 'step-05-plan-review', 'step-06-design', 'step-07-foundation', 'step-08-build-step-01', 'step-09-build-steps-02-06', 'step-10-confirmation', 'step-11-completion']
created: 2026-02-26
completionDate: 2026-02-26
status: COMPLETE
approvedDate: 2026-02-26
confirmationDate: 2026-02-26
confirmationType: conversion
coverageStatus: complete
validationStatus: PASS
---

# Workflow Creation Plan

## Conversion Source

**Original Path:** src/workflows/export-skill/export-skill.spec.md
**Original Format:** Workflow Specification — pre-implementation blueprint (no step files exist yet)
**Detected Structure:** 6-step create-only utility workflow defined as a spec with planned steps, inputs, outputs, and implementation notes. Enriched with module brief ADR decisions (J, K, L) and dual-output delivery strategy.

---

## Original Workflow Analysis

### Goal (from source)

Package a skill for distribution + platform-aware context injection. Final delivery workflow that packages a skill as an agentskills.io-compliant package ready for `npx skills publish`. Generates/updates context-snippet.md. Updates the managed `<!-- SKF:BEGIN/END -->` section in CLAUDE.md/AGENTS.md with compressed skill index. Platform-aware formatting via `--platform` flag.

### Original Steps (Complete List)

**Step 1:** load-skill - Load skill and validate spec compliance
**Step 2:** package - Prepare agentskills.io-compliant package structure
**Step 3:** generate-snippet - Create/update context-snippet.md
**Step 4:** update-context - Update managed section in CLAUDE.md/AGENTS.md
**Step 5:** token-report - Calculate and report token counts
**Step 6:** summary - Display export summary with distribution instructions

### Output / Deliverable

- Updated `{skills_output_folder}/{name}/context-snippet.md`
- Updated CLAUDE.md/AGENTS.md managed section (`<!-- SKF:BEGIN/END -->`)
- agentskills.io-compliant package (ready for `npx skills publish`)

### Input Requirements

**Required:**
- Skill path (`{skills_output_folder}/{name}/`)

**Optional:**
- `--platform` flag (Claude/Cursor/Copilot) for formatting
- `--dry-run` to preview without writing

### Key Instructions to LLM

- Primary agent: Ferris (Delivery mode — packaging, ecosystem-ready)
- Workflow type: Utility — delivery and distribution
- Create-only mode (steps-c/ only, no validation or edit modes)
- Document-producing workflow (context-snippet.md + managed section)

### ADR Decisions (from module brief)

- **ADR-J:** Managed section with `<!-- SKF:BEGIN/END -->` markers. Auto-inject between markers. Developer controls placement. Ferris controls content.
- **ADR-K:** Snippet updates only at export. Create/update are draft operations. Export publishes to skills/ and CLAUDE.md. Prevents half-baked snippets.
- **ADR-L:** One snippet format always — ADR-L v2 multi-line per skill (~50-80 tokens each). No adaptive format switching. Consistent for agent parsing.

### Dual-Output Delivery Strategy (from module brief)

Every skill generates both:
1. **SKILL.md** — Active skill (loaded on trigger, full instructions)
2. **context-snippet.md** — Passive context (compressed index, always-on in CLAUDE.md)

Managed section format:
```markdown
<!-- SKF:BEGIN updated:{date} -->
[SKF Skills]|{n} skills|{m} stack
|IMPORTANT: Prefer documented APIs over training data.
|
|{skill-name} → skills/{skill-name}/
|  exports: {top-5-exports}
<!-- SKF:END -->
```

Three CLAUDE.md cases:
1. **Create** — No CLAUDE.md file exists → create with managed section
2. **Append** — File exists but no `<!-- SKF:BEGIN -->` section → append section
3. **Regenerate** — Existing `<!-- SKF:BEGIN/END -->` section → replace content between markers

### Ownership Model Context

| Context | `source_authority` | Distribution |
|---------|-------------------|-------------|
| OSS library (maintainer generates) | `official` | `npx skills publish` → agentskills ecosystem |
| Internal service (team generates) | `internal` | `skills/` in repo, ships with code |
| External dependency (consumer generates) | `community` | Local `skills/`, marked as community |

### Progressive Disclosure Context

- context-snippet has T1-now only (AST-current)
- SKILL.md has T1-now + lightweight annotations
- references/ has full temporal context

---

## Conversion Notes

**What works well in original:**
- Clear 6-step linear progression from loading through packaging to reporting
- Well-defined inputs (skill path) and outputs (package, snippet, context section)
- Platform-aware design with `--platform` flag
- ADR references (J, K, L) provide solid architectural decisions for managed sections, snippet timing, and format consistency
- Three CLAUDE.md cases explicitly identified: create, append, regenerate
- Position in workflow chain: downstream of create-skill/update-skill, final delivery step

**What needs improvement:**
- Spec is a blueprint only — no step files, templates, or data files exist yet
- No detailed step-level instructions, menus, or execution protocols defined
- No error handling or validation logic specified
- No dry-run implementation details
- No detail on agentskills.io package structure requirements
- No specification of how platform-specific formatting differs between Claude/Cursor/Copilot

**Compliance gaps identified:**
- No step files exist (need full creation from spec)
- No frontmatter with step metadata
- No menu handling or continuation logic
- No data files or templates defined (snippet format template, package structure template needed)
- No subprocess/agent delegation patterns specified

---

## Classification Decisions

**Workflow Name:** export-skill
**Target Path:** {project-root}/_bmad/skf/workflows/export-skill/

**4 Key Decisions:**
1. **Document Output:** false (action-based — produces files as side effects of packaging actions, not progressive document building)
2. **Module Affiliation:** SKF (Skill Forge module — access to skills_output_folder, forge tier, sidecar state)
3. **Session Type:** single-session (fast utility workflow — load, package, write, report)
4. **Lifecycle Support:** create-only (steps-c/ only — deterministic utility, re-export to fix)

**Structure Implications:**
- `steps-c/` directory only (no steps-e/ or steps-v/)
- Standard `step-01-init.md` (no continuation logic, no step-01b-continue.md)
- No `stepsCompleted` tracking in output frontmatter
- Action-based step pattern — steps perform file operations rather than building a document
- Data folder needed for snippet format template and package structure reference
- Ferris Delivery mode activated (only workflow using this mode)

---

## Requirements

**Flow Structure:**
- Pattern: Linear (Step 1 → Step 2 → Step 3 → Step 4 → Step 5 → Step 6)
- Phases: Load & Validate → Package & Generate → Publish → Report
- Estimated steps: 6
- No branching — three CLAUDE.md cases (create/append/regenerate) handled as conditional logic within step-04

**User Interaction:**
- Style: Mostly autonomous with targeted checkpoints
- Decision points: After step-01 (confirm correct skill loaded), after step-04 (confirm CLAUDE.md changes)
- Checkpoint frequency: 2 checkpoints in 6 steps
- `--dry-run` flag converts entire workflow to preview mode (no writes)

**Inputs Required:**
- Required: Skill path (`{skills_output_folder}/{name}/`) containing SKILL.md, metadata.json
- Optional: `--platform` flag (Claude/Cursor/Copilot), `--dry-run` flag
- Prerequisites: Skill must exist (created by create-skill or update-skill). test-skill recommended but advisory.
- Implicit: forge-config.yaml for `passive_context` opt-out check, existing CLAUDE.md/AGENTS.md content

**Output Specifications:**
- Type: Action-based (file writes + console output)
- Files written:
  1. `{skills_output_folder}/{name}/context-snippet.md` — ADR-L v2 format (~50-80 tokens/skill)
  2. CLAUDE.md or AGENTS.md — managed `<!-- SKF:BEGIN/END -->` section per ADR-J (3 cases: create/append/regenerate)
  3. agentskills.io package structure — ready for `npx skills publish`
- Console output: Token count report + export summary with distribution instructions
- Frequency: Single skill per run (batch mode deferred)

**Success Criteria:**
- Skill loaded and validated against agentskills.io spec
- context-snippet.md generated with correct ADR-L v2 format
- CLAUDE.md managed section correctly handles all three cases without corrupting existing content
- Token counts calculated and reported for all generated artifacts
- Package structure ready for `npx skills publish`
- `--dry-run` shows preview with zero file writes
- Zero data loss — existing CLAUDE.md content outside markers preserved

**Instruction Style:**
- Overall: Prescriptive (deterministic utility, exact file operations)
- Notes: Auto-proceed between most steps (P3 pattern). Confirmation gates only at step-01 (skill loaded) and step-04 (CLAUDE.md changes). Similar to create-skill's compile/generate-artifacts prescriptive pattern.

---

## Tools Configuration

**Core BMAD Tools:**
- **Party Mode:** Excluded — deterministic utility workflow, no creative exploration needed
- **Advanced Elicitation:** Excluded — no complex decision-making requiring deep probing
- **Brainstorming:** Excluded — no ideation phases

**LLM Features:**
- **File I/O:** Included — Core requirement. Reads skill artifacts, writes context-snippet.md, modifies CLAUDE.md/AGENTS.md, creates package files
- **Web-Browsing:** Excluded — all data is local
- **Sub-Agents:** Excluded — linear pipeline, no parallelization
- **Sub-Processes:** Excluded — sequential dependency chain

**Memory:**
- Type: Single-session (no sidecar, no continuation tracking)
- State: In-context only — skill metadata and generated content passed between steps

**External Integrations:**
- None required. All operations are local file system.

**Installation Requirements:**
- None. All tools are built-in LLM capabilities.

## Workflow Structure Preview

**Phase 1: Load & Validate (step-01-load-skill)**
- Load skill from `{skills_output_folder}/{name}/`
- Validate SKILL.md, metadata.json, references/ exist
- Check agentskills.io spec compliance
- Read metadata for skill type, source_authority, exports
- **Checkpoint:** Confirm correct skill loaded, show metadata summary

**Phase 2: Package (step-02-package)**
- Build agentskills.io-compliant package structure
- Validate package completeness
- Auto-proceed

**Phase 3: Generate Snippet (step-03-generate-snippet)**
- Generate context-snippet.md in ADR-L v2 format
- T1-now content only — top-5 exports, pointer to skill path
- ~50-80 tokens per skill target
- Auto-proceed

**Phase 4: Update Context (step-04-update-context)**
- Check `passive_context` opt-out in forge-config.yaml
- Detect platform (Claude → CLAUDE.md, Cursor → .cursorrules, Copilot → AGENTS.md)
- Execute three-case logic: create file / append section / regenerate section
- Parse existing `<!-- SKF:BEGIN/END -->` markers, preserve all content outside
- **Checkpoint:** Show diff of changes before writing

**Phase 5: Token Report (step-05-token-report)**
- Calculate token counts for context-snippet.md, managed section, SKILL.md, full package
- Auto-proceed

**Phase 6: Summary (step-06-summary)**
- Display export summary: files written, token counts, distribution instructions
- Show `npx skills publish` command if source_authority is `official`
- Show internal distribution path if `internal`

---

## Workflow Design

### Step Sequence

| Step | Name | Type | Menu Pattern | Goal |
|------|------|------|-------------|------|
| 01 | load-skill | Init (Input Discovery) | P2: C only | Load skill artifacts, validate spec compliance, confirm with user |
| 02 | package | Middle (Simple) | P3: Auto-proceed | Build agentskills.io package structure |
| 03 | generate-snippet | Middle (Simple) | P3: Auto-proceed | Generate context-snippet.md in ADR-L v2 format |
| 04 | update-context | Middle (Standard) | P2: C only | Update managed section in CLAUDE.md/AGENTS.md (3-case logic) |
| 05 | token-report | Middle (Simple) | P3: Auto-proceed | Calculate and report token counts |
| 06 | summary | Final | No next step | Display export summary with distribution instructions |

### Step Action Plans

**Step 01 — load-skill (Init with Input Discovery):**
- Discover skill at `{skills_output_folder}/{name}/`
- Validate required files: SKILL.md, metadata.json
- Validate optional: references/ directory
- Read metadata.json for: skill_type, source_authority, exports list, generation date
- Check forge-config.yaml for `passive_context` opt-out
- Parse `--platform` flag (default: Claude → CLAUDE.md)
- Parse `--dry-run` flag
- Present skill summary to user, confirm correct skill
- Menu: [C] Continue

**Step 02 — package (Middle Simple, auto-proceed):**
- Assemble agentskills.io package structure from skill artifacts
- Validate package contains: SKILL.md, metadata.json, references/
- Generate package manifest if needed
- Verify metadata.json has required agentskills.io fields
- Auto-proceed to step-03

**Step 03 — generate-snippet (Middle Simple, auto-proceed):**
- Load data/snippet-format.md template (ADR-L)
- Generate context-snippet.md from metadata: skill name, path, top-5 exports
- ADR-L v2 format, ~50-80 tokens target, T1-now content only
- Write to `{skills_output_folder}/{name}/context-snippet.md` (or preview if dry-run)
- Auto-proceed to step-04

**Step 04 — update-context (Middle Standard, confirmation gate):**
- Load data/managed-section-format.md template (ADR-J)
- Determine target file based on platform flag (Claude→CLAUDE.md, Cursor→.cursorrules, Copilot→AGENTS.md)
- Execute three-case detection: Create / Append / Regenerate
- For regenerate: scan ALL skills in `{skills_output_folder}/*/context-snippet.md` to rebuild complete index
- Show diff preview of changes
- Menu: [C] Continue to write (or skip if dry-run)

**Step 05 — token-report (Middle Simple, auto-proceed):**
- Calculate token counts: context-snippet.md, managed section, SKILL.md, full package
- Display token report table
- Auto-proceed to step-06

**Step 06 — summary (Final):**
- Display export summary: files written/previewed, token counts
- Distribution instructions based on source_authority (official/internal/community)
- If dry-run: remind no files written, show command for real run
- Recommend next: audit-skill, update-skill
- No next step file

### Data Flow

```
step-01 → skill_metadata, platform, dry_run, passive_context_enabled
step-02 → package_structure (validated)
step-03 → context-snippet.md written
step-04 → CLAUDE.md/AGENTS.md updated
step-05 → token_counts
step-06 → console summary (terminal)
```

### File Structure

```
export-skill/
├── workflow.md
├── data/
│   ├── snippet-format.md
│   └── managed-section-format.md
└── steps-c/
    ├── step-01-load-skill.md
    ├── step-02-package.md
    ├── step-03-generate-snippet.md
    ├── step-04-update-context.md
    ├── step-05-token-report.md
    └── step-06-summary.md
```

### Error Handling

| Scenario | Response |
|----------|----------|
| Skill path doesn't exist | Hard halt — "Run create-skill first" |
| SKILL.md or metadata.json missing | Hard halt — "Incomplete skill" |
| passive_context: false | Skip steps 03-04, package-only export |
| CLAUDE.md write failure | Hard halt, no partial writes |
| --dry-run mode | All writes become preview-only |
| No exports in metadata | Graceful — snippet shows name + path only |

### Subprocess Optimization

None needed — lightweight linear pipeline, small files (~50-80 tokens per snippet).

### Workflow Chaining

- **Prerequisites:** create-skill or update-skill (required), test-skill (advisory)
- **Downstream:** None required — terminal workflow. Optional: audit-skill, update-skill

### Role and Persona

Ferris Delivery mode — precise, efficient, ecosystem-ready packaging. Brief forge metaphor at completion.
