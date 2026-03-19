# Tier Calculation Rules

## Tool Detection Commands

| Tool | Verification Command | What Confirms Availability |
|------|---------------------|---------------------------|
| ast-grep | `ast-grep --version` | Returns version string without error |
| gh | `gh --version` | Returns version string without error |
| qmd | `qmd status` | Returns status indicating initialized and operational |

**Important:** Use verification commands, not existence checks (`which`, `command -v`). A tool must be functional, not just present on PATH.

## Tier Calculation

| Tier | Required Tools | Rule |
|------|---------------|------|
| Quick | None | Default when no tools are available |
| Forge | ast-grep | ast-grep available, regardless of gh/qmd |
| Deep | ast-grep + gh + qmd | All three tools available and functional |

**Override:** If `tier_override` is set in preferences.yaml, use that value instead of calculated tier.

**Edge cases:**
- gh available but no ast-grep → Quick (gh alone doesn't unlock Forge)
- ast-grep + gh but no qmd → Forge (qmd required for Deep)
- ast-grep + qmd but no gh → Forge (gh required for Deep)

## Tier Capability Descriptions

Use these for positive-framing in the report step. Describe what the tier GIVES, never what it lacks.

### Quick Tier
"Quick tier active. You have fast, template-driven skill generation with package-name resolution. Perfect for getting started quickly."

### Forge Tier
"Forge tier active. You have AST-backed structural code analysis with line-level citations, plus template-driven generation. Every skill instruction traces to verified source code."

### Deep Tier
"Deep tier active. Full capability unlocked — AST-backed code analysis, GitHub repository exploration, and QMD knowledge search with cross-repository synthesis. Maximum provenance and intelligence."

## Re-run Tier Change Messages

### Upgrade
"Tier upgraded from {previous} to {current}. {newly available tool(s)} now detected — expanded capabilities unlocked."

### Downgrade
"Tier changed from {previous} to {current}. {tool} no longer detected. Run the tool's installation to restore capabilities."

### Same
"Tier unchanged: {current}. All previously detected tools confirmed."
