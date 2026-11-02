# TRUST.md — How to verify Oh-My-Skills

The [README](README.md) makes a single promise: every claim in every skill traces back to a commit SHA, and you can prove it in 60 seconds. This document is the long form — the scoring math, the disclosed gaps, and the deeper audit trails for readers who want to drill past the headline.

If you haven't read the README's [Don't trust us. Audit us.](README.md#dont-trust-us-audit-us) section yet, start there. This file picks up where it leaves off.

---

## How the 99% is computed

The final score isn't a vibe — it's a weighted average of five deterministic measurements, run by a Python script that guarantees *"the same inputs always produce the same score."* Because every skill in this repo runs in **naive mode** (individual skills, no cross-stack integration to check), the normally 18%-weighted Coherence dimension is redistributed across the other four categories:

| Weight  | Dimension             | What it measures                                                                                                    |
| ------- | --------------------- | ------------------------------------------------------------------------------------------------------------------- |
| **45%** | Export Coverage       | `(documented exports / source exports) × 100` — what fraction of the library's public API is in `SKILL.md`?         |
| **25%** | Signature Accuracy    | Do documented function signatures match the real ones at the pinned commit — parameter names, types, order, return? |
| **20%** | Type Coverage         | Are the types and interfaces referenced in exports fully documented?                                                |
| **10%** | External Validation   | [`skill-check`](https://github.com/thedaviddias/skill-check) quality score, averaged with the [`tessl`](https://tessl.io) content score when Tessl Review is configured (it was off for the current reports) |

Each category is computed as `(items_passing / items_total) × 100`. The final score is `sum(category_weight × category_score)`. **Default pass threshold: 80%** — anything below that fails the gate and triggers `update-skill`, not `export-skill`. A Critical or High gap (a wrong signature, say) blocks the test before it is scored, whatever the arithmetic would say. A 99% score is only meaningful because the denominators are disclosed (in each skill's test report) and the arithmetic is reproducible from each skill's [`forge-data/<ver>/test-report-*.md`](forge-data/).

Full method: [Skill Forge → Completeness Scoring](https://armelhbobdad.github.io/bmad-module-skill-forge/how-it-works/#completeness-scoring).

### Reproducing the score

The scoring script lives in Skill Forge. To re-run it against this repo's pinned source trees:

1. Install [Skill Forge](https://github.com/armelhbobdad/bmad-module-skill-forge).
2. Check out the pinned upstream commit named in `skills/<name>/<version>/<name>/metadata.json` → `source_commit`.
3. Run `skf-test-skill` against the skill directory. It re-extracts the public surface from source, diffs against the skill, and emits the same numeric score the test report records.

If the score you compute differs from the one in this repo's test report by more than rounding, that is a bug. [Open an issue.](https://github.com/armelhbobdad/oh-my-skills/issues)

---

## Per-skill denominator disclosures

The lowest score in this repo is **95.17%**. The highest is **100%**. All four reports come from Skill Forge 4.0.0, and each skill's `metadata.json` stats pass `skf-render-metadata-stats.py --check` against its provenance map. Each report shows its math; each report discloses its own ambiguities. Each provenance entry is labeled by the tool that read it, `T1` for an ast-grep match and `T1-low` for a read of the source by eye: oms-cocoindex 146 `T1` / 9 `T1-low`, oms-cognee 42 / 44, oms-storybook-react-vite 222 / 1, oms-uitripled 18 / 293 (its component and UI-primitive exports were added by a repair that reads new exports by eye).

- **oms-cocoindex** 1.0.0 — **100%**. 79/79 exports documented; the denominator is the brief's `scope.include` union (95 files, 79 exports), disclosed as a stratified scope with its candidates. 27/27 documented signatures match. Left open: two Medium gaps (a brief glob that matches no file, a barrel count in `metadata.json` that differs from `exports[]`) and one Low provenance line. → [test report](forge-data/oms-cocoindex/1.0.0/test-report-oms-cocoindex-20261102T201851Z-bf06d70f.md)
- **oms-cognee** 1.6.2 — **99.00%**. 92/92 exports documented; the denominator is the `cognee/__init__.py` barrel at pinned commit `ba3631f2` (v1.6.2), including the `cognee.migration` members it re-exports. 54 signature checks, 0 mismatches. External Validation is 90%, the point lost below. Left open: five Medium gaps (three names whose files the brief scopes out, a stale brief glob, a barrel count) and the Low token-budget warning. → [test report](forge-data/oms-cognee/1.6.2/test-report-oms-cognee-20261102T194852Z-d56413cb.md)
- **oms-storybook-react-vite** 10.3.5 — **95.17%**. Its brief's `scope.tier_a_include` names the story-authoring entry points (`storybook/test`, `preview-api`, `actions`, `theming`, `viewport`, `highlight`, `@storybook/react-vite`, `@storybook/react`, the addon-docs blocks, the a11y/themes/vitest addons, the builder-vite config helpers): 280 public names, the denominator. 83/83 signatures match. Type Coverage is 91/120, the points lost below. Export Coverage reads 100%, but only because the count credits every documented name (a Skill Forge defect, [bmad-module-skill-forge#792](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/792); [#813](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/813) tracks why the stored count, not the brief, decides the denominator): 207 of the 280 authored names are documented. A first repair under 4.0.0 reached 99.93% by documenting about 800 internal exports the brief's wide `code/core/**` glob pulled in; it was reverted and the skill re-scoped instead. → [test report](forge-data/oms-storybook-react-vite/10.3.5/test-report-oms-storybook-react-vite-20261102T231406Z-a5890950.md)
- **oms-uitripled** 0.1.0 — **100%**. 327/327 on the `stats.effective_denominator` of the brief's `scope.include` union (233 files), with 330 names documented. 127/127 signatures match. Left open: two Medium gaps (a stale brief glob, a barrel count) and Info notes on cross-references between SKILL.md and its references. → [test report](forge-data/oms-uitripled/0.1.0/test-report-oms-uitripled-20261102T194714Z-aff41a98.md)

Every older report stays in `forge-data/` next to the one that replaced it, the failing first runs under 4.0.0 included: each repair is a test report, an update-skill commit and a re-test, in that order, in the git history. The reverted storybook repair's reports are in that history too.

---

## The points we lost

**oms-cognee: 99.00%.** skill-check estimates the `SKILL.md` body at 5,646 tokens, over its 5,000-token budget, and logs it as a warning, so External Validation is 90% and the weighted score loses one point. The report lists it as a Low gap (`body.max_tokens`). Moving detail into `references/` would recover it; we left it visible instead of trimming the body to chase the number.

**oms-storybook-react-vite: 95.17%.** Type Coverage is 91 of the 120 types in the skill's authored tier, so the weighted score loses 4.8 points. The report lists the 29 undocumented types, and it is also where to see that 73 of the 280 authored names are not documented yet, which Export Coverage, as Skill Forge counts it today, does not show.

We didn't hide the rough edges. We wrote them down. Read them yourself: [`oms-cognee`'s report](forge-data/oms-cognee/1.6.2/test-report-oms-cognee-20261102T194852Z-d56413cb.md) and [`oms-storybook-react-vite`'s report](forge-data/oms-storybook-react-vite/10.3.5/test-report-oms-storybook-react-vite-20261102T231406Z-a5890950.md).

A promise of perfection is suspicious. A promise of visible fallibility is trustworthy.

---

## Further audit trails

For readers who want to verify a specific aspect of a skill's compilation, the receipts are split across these files:

| Question                                       | File                                              |
| ---------------------------------------------- | ------------------------------------------------- |
| What AST patterns were used?                   | `forge-data/<name>/<ver>/extraction-rules.yaml`   |
| What did the extractor actually capture?       | `forge-data/<name>/<ver>/evidence-report.md`      |
| How was the skill scored? Show me the math.    | `forge-data/<name>/<ver>/test-report-<name>-<run_id>.md` (the newest counts) |
| How was the skill scoped?                      | `forge-data/<name>/skill-brief.yaml`              |
| What symbol came from where?                   | `forge-data/<name>/<ver>/provenance-map.json`     |
| What commit does the skill anchor to?          | `skills/<name>/<version>/<name>/metadata.json`    |

The split between `skills/` and `forge-data/` is intentional: `skills/` ships to consumers, `forge-data/` is the audit trail. You don't need `forge-data/` to use a skill — you need it to verify one.

---

## Found a drift?

If a documented signature doesn't match the source at the pinned commit, that is a bug, not a footnote. [Open an issue](https://github.com/armelhbobdad/oh-my-skills/issues) with the file and line. We fix it publicly, with a new commit SHA and a new provenance map. That is the entire deal.
