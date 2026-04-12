---
nextStepFile: './step-02-detect-mode.md'
outputFile: '{forge_version}/test-report-{skill_name}.md'
templateFile: 'templates/test-report-template.md'
sidecarFile: '{sidecar_path}/forge-tier.yaml'
skillsOutputFolder: '{skills_output_folder}'
# frontmatterScript `shared/scripts/skf-validate-frontmatter.py` resolves
# relative to the SKF module root (`_bmad/skf/` when installed, `src/` during
# development), NOT relative to this step file.
frontmatterScript: 'shared/scripts/skf-validate-frontmatter.py'
versionPathsKnowledge: 'knowledge/version-paths.md'
---

# Step 1: Initialize Test

## STEP GOAL:

Discover and validate the target skill, load forge tier state to determine analysis depth, and create the test report document from template.

## Rules

- Focus only on input discovery and validation — do not begin analysis
- Validate all required files exist before proceeding

## MANDATORY SEQUENCE

**CRITICAL:** Follow this sequence exactly. Do not skip, reorder, or improvise unless user explicitly requests a change.

### 1. Receive Skill Path

If skill path was provided as workflow argument, use it directly.

**Recognized flags on the invocation:**
- `--allow-workspace-drift` — bypass the section 5b pre-flight guard that halts when local workspace HEAD does not match `metadata.source_commit`. Store `allow_workspace_drift: true` in workflow context when present. No effect when `source_commit` is unpinned or the source is not a git working tree.

If no path provided, ask:

"**Which skill would you like to test?**

Provide the skill path or name. I'll search in `{skillsOutputFolder}`.

**Path or name:**"

### 2. Validate Skill Exists (version-aware)

Resolve the skill path using version-aware resolution (see `{versionPathsKnowledge}`):

1. Read `{skillsOutputFolder}/.export-manifest.json` and look up the skill name in `exports` to get `active_version`
2. If found: resolve to `{skill_package}` = `{skillsOutputFolder}/{skill_name}/{active_version}/{skill_name}/`
3. If not in manifest: check for `active` symlink at `{skillsOutputFolder}/{skill_name}/active` — resolve to `{skill_group}/active/{skill_name}/`
4. If neither: fall back to flat path `{skillsOutputFolder}/{skill_name}/`. If SKILL.md exists at the flat path, auto-migrate per `{versionPathsKnowledge}` migration rules
5. Store the resolved path as `{resolved_skill_package}`

Check that the skill package contains required files:

**Required files:**
- `{resolved_skill_package}/SKILL.md` — the skill documentation
- `{resolved_skill_package}/metadata.json` — skill metadata

**If SKILL.md missing:**
"**Error: SKILL.md not found at `{resolved_skill_package}/SKILL.md`**

This skill has not been created yet. Run the **create-skill** workflow first."

HALT — do not proceed.

**If metadata.json missing:**
"**Warning:** metadata.json not found. Proceeding with limited metadata. Some checks may be skipped."

### 3. Validate Frontmatter Compliance

Run the deterministic frontmatter validator:

```bash
python3 {frontmatterScript} {resolved_skill_package}/SKILL.md --skill-dir-name {skill_name}
```

Where `{frontmatterScript}` resolves from the SKF module root (e.g., `_bmad/skf/shared/scripts/skf-validate-frontmatter.py` installed, or `src/shared/scripts/skf-validate-frontmatter.py` in development).

Parse the JSON output. If `status` is `"fail"` or `"warn"`, display:

"**Warning: SKILL.md frontmatter is non-compliant with agentskills.io specification.**

{list issues from the JSON output}

This skill will fail `npx skills add` and `npx skill-check check`. Consider fixing frontmatter before proceeding (run `npx skill-check check <skill-dir> --fix` to auto-fix deterministic issues)."

Log each issue as a pre-check finding. Continue with testing — frontmatter issues will be reported in the gap report alongside coverage/coherence findings.

**If the script is unavailable**, perform the checks manually: frontmatter delimiters present, `name` is lowercase alphanumeric + hyphens (1-64 chars) matching the directory name, `description` is non-empty (1-1024 chars), no unknown fields (only `name`, `description`, `license`, `compatibility`, `metadata`, `allowed-tools` permitted).

### 4. Load Forge Tier State

Read `{sidecarFile}` to determine available analysis depth.

**If forge-tier.yaml exists:**
- Read `tier` value (Quick, Forge, Forge+, or Deep)
- Read tool availability flags (ast_grep, gh_cli, qmd)

**If forge-tier.yaml missing:**
"**Cannot proceed.** forge-tier.yaml not found at `{sidecarFile}`. Please run the **setup** workflow first to configure your forge tier (Quick/Forge/Forge+/Deep)."

HALT — do not proceed.

### 4b. Apply Tier Override (if set)

Read `{sidecar_path}/preferences.yaml`. If `tier_override` is set and is a valid tier value (Quick, Forge, Forge+, or Deep), update `detected_tier` to the override value for use in subsequent steps and output documents.

### 5. Load Skill Metadata

Read `metadata.json` to extract:
- `name` — display name
- `skill_type` — single or stack (needed for mode detection)
- `source_path` — path to source code (if present)
- `source_commit` — pinned commit the skill was extracted against (may be null for docs-only skills, `"local"` for non-git sources, or a per-repo map for stack skills)
- `source_ref` — pinned ref (tag/branch/`HEAD`) used at extraction time
- `generation_date` — when skill was generated
- `confidence_tier` — tier used during creation

If source path override was provided as optional input, use that instead.

### 5b. Verify Workspace HEAD Matches Pinned Commit

Test-skill reads `source_path` during coverage and coherence analysis. If the local workspace has drifted from `metadata.source_commit`, gap and signature-mismatch findings will silently reflect the drifted tree, not the skill's pinned source — producing false positives that downstream update-skill runs may then "repair" by corrupting correct documentation.

- Resolve `pinned_commit` from `metadata.source_commit`.
- **If `pinned_commit` is null, empty, `"local"`, or a per-repo map (stack skills):** skip the guard; log `workspace_drift_check: skipped (no single pinned commit)` and continue to section 6.
- **If `source_path` is not a git working tree** (bare checkout, tarball extract, docs-only source) — detect by `git -C {source_path} rev-parse --is-inside-work-tree`, non-zero exit means skip: log `workspace_drift_check: skipped (not a git working tree)` and continue to section 6.
- **Otherwise** run `git -C {source_path} rev-parse HEAD` and compare to `pinned_commit`. Accept full-SHA or short-SHA-prefix match (stored pins are often 8-char short hashes — see `src/knowledge/provenance-tracking.md`).
  - **On match:** log `workspace_drift_check: ok ({short_sha})` and continue.
  - **On mismatch, AND the user did not pass `--allow-workspace-drift`:** HALT with exit status `halted-for-workspace-drift`. Display:

    ```
    Workspace HEAD does not match the commit this skill was pinned against.

      pinned (metadata.source_commit): {pinned_commit}
      pinned ref (metadata.source_ref): {source_ref or "unset"}
      workspace HEAD ({source_path}):  {head_sha}

    Test-skill verifies against the source the skill was extracted from.
    Testing against a drifted tree produces false gaps/mismatches. Re-sync:

      git -C {source_path} checkout {source_ref or pinned_commit}

    Or re-run test-skill with `--allow-workspace-drift` to test against the
    current workspace (accepts that findings reflect HEAD, not the pin).
    ```

    Do not proceed. The test report has not been created; no partial writes.
  - **On mismatch WITH `--allow-workspace-drift`:** log `workspace_drift_check: overridden (pinned={pinned_commit}, head={head_sha})` and carry the warning into the final report frontmatter (`workspaceDrift: overridden`) so downstream readers know the findings reflect HEAD rather than the pinned tree. Continue.

### 6. Create Output Document

Create `{outputFile}` from `{templateFile}` with initial frontmatter:

```yaml
---
workflowType: 'test-skill'
skillName: '{skill_name}'
skillDir: '{skill_path}'
testMode: ''
forgeTier: '{detected_tier}'
testResult: ''
score: ''
threshold: ''
analysisConfidence: ''
testDate: '{current_date}'
stepsCompleted: ['step-01-init']
nextWorkflow: ''
---
```

### 7. Report Initialization Status

"**Test initialization complete.**

**Skill:** {skill_name}
**Path:** {skill_path}
**Type:** {skill_type}
**Forge Tier:** {detected_tier}
**Source:** {source_path}

**Proceeding to mode detection...**"

### 8. Auto-Proceed

Display: "**Proceeding to mode detection...**"

#### Menu Handling Logic:

- After initialization is complete, update {outputFile} frontmatter stepsCompleted, then immediately load, read entire file, then execute {nextStepFile}

#### EXECUTION RULES:

- This is an auto-proceed initialization step with no user choices
- Proceed directly to next step after setup

## CRITICAL STEP COMPLETION NOTE

ONLY WHEN all required files are validated, forge tier is loaded, output document is created, and initialization status is reported, will you then load and read fully `{nextStepFile}` to execute mode detection.

