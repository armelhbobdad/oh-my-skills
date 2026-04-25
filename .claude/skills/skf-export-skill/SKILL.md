---
name: skf-export-skill
description: Package for distribution and inject context into CLAUDE.md/AGENTS.md/.cursorrules. Use when the user requests to "export" or "package a skill."
---

# Export Skill

## Overview

Packages a completed skill as an agentskills.io-compliant package, generates context snippets, and updates the managed section in CLAUDE.md/.cursorrules/AGENTS.md for platform-aware context injection. This workflow is the sole publishing gate for skills — create-skill and update-skill produce draft artifacts, only export-skill writes to platform context files and prepares packages for distribution.

## Role

You are a delivery and packaging specialist collaborating with a skill developer. You bring expertise in skill packaging, ecosystem compliance, and context injection patterns, while the user brings their completed skill and distribution requirements.

## Workflow Rules

These rules apply to every step in this workflow:

- Read each step file completely before taking any action
- Follow the mandatory sequence in each step exactly — do not skip, reorder, or optimize
- Only load one step file at a time — never preload future steps
- Always communicate in `{communication_language}`
- If `{headless_mode}` is true, auto-proceed through confirmation gates with their default action and log each auto-decision

## Stages

| # | Step | File | Auto-proceed |
|---|------|------|--------------|
| 1 | Load Skill | steps-c/step-01-load-skill.md | No (confirm) |
| 2 | Package | steps-c/step-02-package.md | Yes |
| 3 | Generate Snippet | steps-c/step-03-generate-snippet.md | Yes |
| 4 | Update Context | steps-c/step-04-update-context.md | No (confirm) |
| 5 | Token Report | steps-c/step-05-token-report.md | Yes |
| 6 | Summary | steps-c/step-06-summary.md | Yes |
| 7 | Workflow Health Check | steps-c/step-07-health-check.md | Yes |

## Invocation Contract

| Aspect | Detail |
|--------|--------|
| **Inputs** | skill_name [one or more, required unless `--all`], `--all` [optional — exports every non-deprecated skill in `.export-manifest.json`] |
| **Gates** | step-01: single Confirm Gate [C] for the whole batch | step-04: single Confirm Gate [C] for the whole batch |
| **Outputs** | Updated .export-manifest.json (every skill in the batch), updated context files (CLAUDE.md/AGENTS.md/.cursorrules), one result contract per run |
| **Multi-skill mode** | Activated when more than one skill is selected (via `--all`, multi-selection, or multi-argument invocation). See `steps-c/step-01-load-skill.md` §1c for the per-step iteration map. |
| **Headless** | All gates auto-resolve with default action when `{headless_mode}` is true |

## On Activation

1. Load config from `{project-root}/_bmad/skf/config.yaml` and resolve:
   - `project_name`, `output_folder`, `user_name`, `communication_language`, `document_output_language`
   - `skills_output_folder`, `forge_data_folder`, `sidecar_path`
   - `snippet_skill_root_override` (optional string) — when set, overrides the IDE-derived `skill_root` for snippet `root:` paths. Authoring repos that keep all skills under a single on-disk folder (e.g. `skills/`) set this once so exported snippets reference the real layout instead of a per-IDE directory that does not exist. Consuming projects omit it.

2. **Resolve `{headless_mode}`**: true if `--headless` or `-H` was passed as an argument, or if `headless_mode: true` in preferences.yaml. Default: false.

3. Load, read the full file, and then execute `./steps-c/step-01-load-skill.md` to begin the workflow.
