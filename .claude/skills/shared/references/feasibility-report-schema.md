# Feasibility Report Schema

**Purpose:** Canonical contract shared between `skf-create-stack-skill` (consumer) and `skf-verify-stack` (producer). Any change here must be applied to both skills in lockstep.

## Filename

```
{forge_data_folder}/feasibility-report-{project_slug}-{YYYYMMDD-HHmmss}.md
```

`{project_slug}` is the slugified `project_name` (lowercase, hyphens only, no unicode). A stable `feasibility-report-{project_slug}-latest.md` copy (not symlink) is written next to the timestamped file for pipeline consumers.

## Frontmatter (required)

```yaml
---
schemaVersion: "1.0"
reportType: feasibility
projectName: "{project_name}"
projectSlug: "{project_slug}"
generatedAt: "{ISO-8601 UTC}"
generatedBy: skf-verify-stack
overallVerdict: "FEASIBLE|CONDITIONALLY_FEASIBLE|NOT_FEASIBLE"
coveragePercentage: <0..100 integer>
pairsVerified: <non-negative integer>
pairsPlausible: <non-negative integer>
pairsRisky: <non-negative integer>
pairsBlocked: <non-negative integer>
recommendationCount: <non-negative integer>
prdAvailable: <true|false>
---
```

**Unknown `schemaVersion` MUST fail loudly in consumers — never silently proceed.** Consumers check `schemaVersion == "1.0"` and emit an explicit error if mismatched.

## Per-pair verdict tokens (case-sensitive)

Exactly one of:

| Token | Meaning | Required evidence |
|---|---|---|
| `Verified` | All compatibility checks pass with declared evidence in both skills | Documentation cross-reference (Check 4) MUST pass with literal substring/name citation; language + protocol + type checks all pass |
| `Plausible` | Checks pass but at least one relies on inferred rather than declared evidence | Language + protocol + type checks pass; Check 4 weak or missing |
| `Risky` | At least one check produced incompatibility that a workaround may resolve | Any single check fails; workaround cited in recommendation |
| `Blocked` | Fundamental incompatibility that cannot be worked around | Language mismatch, protocol mismatch with no bridge, or type mismatch with no adapter |

## Overall verdict tokens (case-sensitive)

Exactly one of `FEASIBLE`, `CONDITIONALLY_FEASIBLE`, `NOT_FEASIBLE`.

- `FEASIBLE` — 100% coverage AND zero Blocked pairs AND zero pairs with Check 4 missing.
- `NOT_FEASIBLE` — Any Blocked pair OR zero coverage.
- `CONDITIONALLY_FEASIBLE` — Everything else.

## Body section headings (required, in order)

```markdown
## Executive Summary
## Coverage Analysis
## Integration Verdicts
## Recommendations
## Evidence Sources
```

Consumers grep for `## Integration Verdicts` to locate the pair table. The table header is fixed:

```markdown
| lib_a | lib_b | verdict | rationale |
```

## Producer obligations (skf-verify-stack)

- Set `schemaVersion: "1.0"` in frontmatter.
- Never emit a verdict token outside the defined set.
- When Check 4 (documentation cross-reference) produces weak/missing evidence, cap the per-pair verdict at `Plausible`.
- When `coveragePercentage == 0`, force `overallVerdict: NOT_FEASIBLE` regardless of pair results.

## Consumer obligations (skf-create-stack-skill)

- Verify `schemaVersion == "1.0"`; halt with explicit error on mismatch.
- Treat any unknown verdict token as a hard error (do not silently drop or map).
- Use filename pattern above when referencing prior reports.

## Versioning policy

Any change to the verdict token set, frontmatter keys, or section headers is a schema-breaking change and MUST bump `schemaVersion`. Additive changes (new optional frontmatter keys) bump the minor version; breaking changes bump the major version.
