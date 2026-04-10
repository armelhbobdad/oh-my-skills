# Evidence Report: oms-uitripled

**Generated:** 2026-04-11
**Forge Tier:** Deep
**Source:** https://github.com/moumen-soliman/uitripled @ a5ffb45be05335d2c547436664cfbfb8c22d04df (master HEAD)

## Tool Versions
- ast-grep: 0.42.0
- QMD: 2.0.1
- SKF: 1.0.0

## Extraction Summary
- Files scanned: ~250 (232 react-shadcn tsx/ts + 6 utils + 3 CLI + registry.json + 2 llms docs + READMEs)
- Exports found: 22 documented public-API entries (providers, hooks, utils, CLI surface, registry schema, 171 component catalog items)
- Confidence: T1=20, T1-low=2, T2=2, T3=0
- Registry items extracted: 171 (react-shadcn only; 88 baseui + 19 carbon excluded per brief)
- Registry content hash: `a51b64916a74283b364f5fe1b59aacd36a33134d6431565b3e2df732bff9f540` — **matches brief exactly, identity verified**
- Source commit: `a5ffb45be05335d2c547436664cfbfb8c22d04df` — **matches brief's `target_commit` exactly**
- Version reconciliation: `@uitripled/react-shadcn@0.1.0` matches brief `version: 0.1.0`. `uitripled` CLI is a separate package at `1.1.0` — noted in Overview but not conflated with skill version.

## Source Resolution
- Strategy: Workspace clone (`~/.skf/workspace/repos/github.com/moumen-soliman/uitripled/`)
- First-time clone (workspace root was created for this skill)
- HEAD verified against brief `target_commit` — identical
- CCC indexing deliberately skipped: highly targeted include patterns (~20 paths) made pre-ranking unnecessary. Same rationale as oms-cognee.

## Brief Deltas — Extraction Findings

1. **`registry:ui` type not mentioned in brief.** 20 entries globally (19 react-shadcn, 1 react-carbon) use `type: "registry:ui"` — leaf primitives. Promoted to the reference tier alongside `registry:component` in SKILL.md Component Catalog. Brief only named `registry:page`, `registry:block`, `registry:component` as tier classifiers.

2. **`apps/docs/components/demos/**` directory does not exist.** The brief's `notes` claimed this path held "validated compositions that teach the agent how real pages assemble registry items" and included it via `demo_patterns`. Only `apps/docs/app/**/page.tsx|mdx` (8 files) exist, and most are thin Next.js shells importing from `@/components/home/...` — they do NOT directly reference uitripled registry items. The brief's claim is speculative; treated as aspirational rather than factual.

3. **Authoritative CLI install path differs from brief.** Brief stated `uitripled add <name>` CLI is the primary API surface. In reality the project's own AI-optimized docs (`apps/docs/public/llms.txt`, 389 lines; `apps/docs/public/llms-full.txt`, 36908 lines, written by the maintainer specifically for AI assistants per issue #7 / PR #8) standardize on `npx shadcn@latest add @uitripled/<name>`. This is used across every one of the 171 entries documented in llms-full.txt. The standalone `uitripled` CLI still works but is not the documented-for-AI path. SKILL.md leads with the shadcn path and documents both.

4. **Subpath imports are first-class, not a fallback.** Brief stated subpath imports are "preview/fallback." In the workspace `apps/docs/` site, 28+ files actively use `@uitripled/react-shadcn/ui/button`, `.../ui/card`, etc. These are the primary reference pattern for direct workspace consumers. Brief's warning about barrel imports (via empty `src/index.ts`) stands and was verified — `src/index.ts:L2` is `export {};`.

5. **Upstream shadcn/ui resolution.** `registryDependencies` references `button` (95×) and `card` (5×) which are NOT uitripled registry items. They resolve against the upstream shadcn/ui registry when installed via `npx shadcn@latest add`. This is a composition mechanic the brief did not call out.

6. **Universal npm dependencies.** All 171 react-shadcn items declare `framer-motion` + `react` as dependencies in `registry.json`. Peer deps in `packages/components/react-shadcn/package.json`: React 19, React-DOM 19, Next.js 16. This is the stack requirement floor.

## Decision: Promoting `apps/docs/public/llms.txt` back into scope

The brief excluded `apps/docs/public/**` to filter noise. However, `llms.txt` and `llms-full.txt` in that directory are **project-authored AI documentation** — created by the maintainer (PR #8 on 2026-03-20) specifically in response to a user request (issue #7: "Add /llms.txt for AI coding assistants"). These files are the most authoritative install/usage reference for AI agents like this skill's consumers.

**Decision:** Promoted back into scope as T1 in-source evidence and indexed into QMD collection `oms-uitripled-docs` (2 files, 423 embeddings) for audit/update workflows. Cited in SKILL.md with `[SRC:apps/docs/public/llms.txt:...]` and `[SRC:apps/docs/public/llms-full.txt:...]` citations. Evidence: issue #7 + PR #8 establish intent and provenance.

## Enrichment Findings (Deep tier QMD)

Collections consulted: `oms-uitripled-temporal` (3 docs, 3 chunks), `oms-uitripled-docs` (2 docs, 423 chunks).

- **T2-past for CLI install path:** QMD search surfaced issue #7 + PR #8 establishing `npx shadcn@latest add @uitripled/<name>` as the authoritative AI install path. Cited as `[QMD:oms-uitripled-temporal:prs.md]` in SKILL.md Section 4b.
- **T2-past for copy-paste distribution model:** llms.txt explicitly states "Copy-paste components — not an installable npm package." Used to reinforce the brief's `src/index.ts` empty-by-design warning.
- **T2-past for stack requirements:** llms.txt lines 9-10 authoritatively name React 19, Next.js 16, TypeScript, Tailwind CSS 4, Framer Motion.

Targeted function searches: provider functions had no temporal signal (young project — 1 issue, 5 PRs, 0 releases). Enrichment annotations are deliberate rather than comprehensive.

## Validation Results
- Schema: PASS (quality score: 100/100, skill-check 2-pass)
- Frontmatter: PASS
- Body: PASS — Tier 2 sections kept inline as short pointers after tessl [A] structural trims. Final SKILL.md: 198 lines (under 300-line Tier 1 target and 500-line max).
- Security: SKIPPED — SNYK_TOKEN not configured (optional).
- Content Quality (tessl): PASS (Review Score 89%, Description 100%, Content 73%)
- Metadata: PASS (22 provenance entries cross-checked against extraction inventory)

## Quality Score Breakdown
- Frontmatter (30%): 30 | Description (30%): 30 | Body (20%): 20 | Links (10%): 10 | File (10%): 10

## tessl Judge Breakdown
- **Description** — specificity 3/3, trigger_term_quality 3/3, completeness 3/3, distinctiveness_conflict_risk 3/3
- **Content** — conciseness 2/3, actionability 3/3, workflow_clarity 2/3, progressive_disclosure 3/3

## Auto-Fixed Issues
- `skill-check --fix` renamed `name: oms-uitripled` → `oms-uitripled-skill` to match the staging directory name. Restored to `oms-uitripled` after the staging directory was renamed to match the final skill name.
- tessl initial run rejected angle-bracket placeholders (`<name>`) in the description as XML tags. Rewrote to use `COMPONENT_ID` plaintext instead — semantic meaning preserved.
- tessl [A] Apply fixes: trimmed Key Types section (removed the long legacy `Component` table and the full `NativeHoverCardProps` table — both preserved in `references/types.md`/`references/setup.md`). Trimmed `## Full API Reference`, `## Full Type Definitions`, `## Full Integration Patterns` to short pointer paragraphs since full detail lives in reference files. SKILL.md dropped from 341 → 198 lines. Content Score rose 50% → 73%, Review Score 80% → 89%.

## tessl Suggestions — Dismissed (per step-06 expected behavior)
- **"Add validation checkpoints to workflows"** (both runs): Dismissed — semantic suggestion that would introduce content not verified from source. No `verify installation` logic exists in uitripled source to cite.
- **"Remove inline source citations `[SRC:...]`/`[AST:...]`/`[QMD:...]`"** (both runs): Dismissed — conflicts with SKF zero-hallucination policy. Citations are mandatory provenance.
- **"Remove Architecture at a Glance"** (first run): Dismissed — required Tier 1 section per `assets/skill-sections.md`.
- **"Move Full API Reference to references"** (first run): Partially honored — SKILL.md now points to references/ for API details while the Tier 2 `## Full` headings remain inline as stubs for split-body compatibility.

## Remaining Warnings
- `registry:ui` type (20 entries) was not in the brief's tiering rule — documented as reference-tier alongside `registry:component`. Brief update recommended so future re-forges treat it consistently.
- Brief's `apps/docs/components/demos/**` glob matches zero files at commit `a5ffb45`. Can be removed on next brief update.
- Brief version `0.1.0` aligns only with `@uitripled/react-shadcn`. The standalone `uitripled` CLI package is at `1.1.0` — consumers should understand these are independent packages. Documented in SKILL.md Overview.
- `packages/components/react-shadcn/CHANGELOG.md` and root `CHANGELOG.md` do not exist (no `.changeset/` directory either). Release trail is thin — update-skill should diff against `source_commit`, not against a changelog.
- **Staging-directory name check friction:** `skill-check` enforces `frontmatter.name_matches_directory`, so the create-skill staging suffix convention (`_bmad-output/{name}-skill/`) is incompatible with strict validation. Worked around by renaming the staging dir to `_bmad-output/oms-uitripled/`. Consider updating create-skill step-05/step-07 to use the unsuffixed staging path, or passing a directory override to skill-check.
