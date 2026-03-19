# agentskills.io Specification

## Principle

Skills produced by Skill Forge comply with the agentskills.io specification — a format designed for agent consumption through progressive disclosure. The format prioritizes discoverability at low token cost, deterministic procedural instructions, and just-in-time resource loading.

## Rationale

Agent skills are not documentation for humans. They are instructions consumed by AI agents that treat every statement as actionable truth. The agentskills.io format was designed around this constraint: minimal metadata for discovery, structured instructions for activation, and on-demand resources for execution.

Without format compliance:
- Skills are not portable across agent platforms
- Discovery requires loading full skill content, wasting context tokens
- Agents cannot distinguish skills from general documentation

With format compliance:
- Skills are discoverable from ~100 tokens of frontmatter metadata
- Full activation loads < 500 lines of structured instructions
- Resources load on demand, keeping context lean during execution

## Format Structure

### Required: SKILL.md

The minimum viable skill is a single `SKILL.md` file containing:

**Frontmatter** (YAML between `---` markers):
```yaml
---
name: library-name
description: >
  What the skill does and when to use it. Include specific keywords
  for agent discovery. Mention what NOT to use it for.
---
```

**Frontmatter constraints:**
- `name`: 1-64 characters, lowercase alphanumeric + hyphens, must match parent directory name
- `description`: 1-1024 characters, trigger-optimized for agent matching

**Body:** Free-form markdown — no structural restrictions, but Skill Forge follows a consistent section order (see skill-sections.md in create-skill/data/).

### Optional: Supporting Directories

```
skill-name/
├── SKILL.md              # Instructions and API reference
├── scripts/              # Executable automation
├── references/           # Detailed reference material
└── assets/               # Templates, schemas, configs
```

All subdirectories are exactly one level deep. Files are loaded on demand when SKILL.md directs — never automatically.

## Progressive Disclosure Model

The format implements a three-phase loading model:

| Phase | What Loads | Token Cost | When |
| --- | --- | --- | --- |
| Discovery | `name` + `description` from frontmatter | ~50-100 tokens | Agent startup, all skills |
| Activation | Full `SKILL.md` body | < 5000 tokens | Task matches skill description |
| Execution | Files from `scripts/`, `references/`, `assets/` | Variable | SKILL.md directs agent to load |

## Pattern Examples

### Example 1: Trigger-Optimized Description

**Context:** Writing a skill description that agents can match to user tasks.

**Implementation:**
```yaml
description: >
  Extract and transform data from PostgreSQL databases using pg client.
  Use for database queries, schema inspection, connection management,
  and migration execution. NOT for: MongoDB, Redis, or other non-SQL stores.
  NOT for: ORM-level abstractions (use typeorm-skill or prisma-skill instead).
```

**Key Points:**
- Leads with what the skill does (positive triggers)
- Includes negative triggers to prevent false matches
- References alternative skills for excluded use cases
- Specific keywords: "PostgreSQL", "pg client", "schema inspection"

### Example 2: Just-in-Time Resource Loading

**Context:** A skill needs to reference a complex schema during execution.

**Implementation:**
```markdown
## Configuration

The library accepts a configuration object matching the schema in
`references/config-schema.md`. Load that file now to validate
the user's configuration against the expected structure.
```

**Key Points:**
- The directive is explicit: "Load that file now"
- Agents do not pre-load reference files — they follow the instruction when they reach it
- Relative paths use forward slashes, one level deep only

### Example 3: Procedural Instructions for Agents

**Context:** Writing skill instructions that agents execute deterministically.

**Implementation:**
```markdown
## Setup

1. Check if `pg` is installed: run `npm list pg` in the project directory.
2. If not installed, run `npm install pg`.
3. Locate the database configuration:
   - Check `src/config/database.ts` first
   - If not found, check environment variables: `DATABASE_URL`, `PG_HOST`
   - If neither exists, ask the user for connection details
4. Validate the connection by running the health check in `scripts/health-check.sql`.
```

**Key Points:**
- Step-by-step numbering with decision trees
- Third-person imperative voice ("Check if..." not "You should check...")
- Concrete file paths and commands, not vague guidance
- Fallback paths explicitly mapped

### Example 4: Skill Forge Compliance Checks

**Context:** The validate step in create-skill checks agentskills.io compliance.

**Implementation:** Validation covers:
1. Frontmatter present with required `name` and `description` fields
2. `name` matches parent directory name and formatting rules
3. `description` length within 1-1024 characters
4. SKILL.md body under 500 lines (warning, not failure)
5. All relative paths resolve to existing files
6. No deeply nested subdirectories (max one level)

**Key Points:**
- Compliance is checked during create-skill, not as a post-hoc audit
- Line count is a guideline — exceeding 500 lines produces a warning
- Path validation prevents broken references in the published skill

## Anti-Patterns

- Writing skills as documentation (README-style) instead of procedural agent instructions
- Deeply nested directory structures — one level maximum from skill root
- Vague descriptions ("helps with databases") — descriptions must be specific and trigger-optimized
- Including redundant content that duplicates what the agent already knows (standard language features, basic CLI commands)
- Bundling large library code inside skills — skills reference existing tools, not replace them

## Related Fragments

- [skill-lifecycle.md](skill-lifecycle.md) — where agentskills.io compliance fits in the pipeline
- [confidence-tiers.md](confidence-tiers.md) — how citations appear within the formatted output
- [zero-hallucination.md](zero-hallucination.md) — the integrity principle that shapes skill content

_Source: synthesized from agentskills.io specification, what-are-skills.mdx, integrate-skills.mdx, and Best Practices for Creating Agent Skills_
