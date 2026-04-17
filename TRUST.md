# TRUST.md — How to verify Oh-My-Skills

The [README](README.md) makes a single promise: every claim in every skill traces back to a commit SHA, and you can prove it in 60 seconds. This document is the long form — the scoring math, the disclosed gap, and the deeper audit trails for readers who want to drill past the headline.

If you haven't read the README's [Don't trust us. Audit us.](README.md#dont-trust-us-audit-us) section yet, start there. This file picks up where it leaves off.

---

## How the 99% is computed

The final score isn't a vibe — it's a weighted average of five deterministic measurements, run by a Python script that guarantees *"the same inputs always produce the same score."* Because every skill in this repo runs in **naive mode** (individual skills, no cross-stack integration to check), the normally 18%-weighted Coherence dimension is redistributed across the other four categories:

| Weight  | Dimension             | What it measures                                                                                                    |
| ------- | --------------------- | ------------------------------------------------------------------------------------------------------------------- |
| **45%** | Export Coverage       | `(documented exports / source exports) × 100` — what fraction of the library's public API is in `SKILL.md`?         |
| **25%** | Signature Accuracy    | Do documented function signatures match the real ones at the pinned commit — parameter names, types, order, return? |
| **20%** | Type Coverage         | Are the types and interfaces referenced in exports fully documented?                                                |
| **10%** | External Validation   | Average of [`skill-check`](https://github.com/thedaviddias/skill-check) quality score and [`tessl`](https://tessl.io) content score |

Each category is computed as `(items_passing / items_total) × 100`. The final score is `sum(category_weight × category_score)`. **Default pass threshold: 80%** — anything below that fails the gate and triggers `update-skill`, not `export-skill`. A 99% score is only meaningful because the denominators are disclosed (in each skill's test report) and the arithmetic is reproducible from each skill's [`forge-data/<ver>/test-report-*.md`](forge-data/).

Full method: [Skill Forge → Completeness Scoring](https://armelhbobdad.github.io/bmad-module-skill-forge/how-it-works/#completeness-scoring).

### Reproducing the score

The scoring script lives in Skill Forge. To re-run it against this repo's pinned source trees:

1. Install [Skill Forge](https://github.com/armelhbobdad/bmad-module-skill-forge).
2. Check out the pinned upstream commit named in `skills/<name>/<version>/<name>/metadata.json` → `source_commit`.
3. Run `skf-test-skill` against the skill directory. It re-extracts the public surface from source, diffs against the skill, and emits the same numeric score the test report records.

If the score you compute differs from the one in this repo's test report by more than rounding, that is a bug. [Open an issue.](https://github.com/armelhbobdad/oh-my-skills/issues)

---

## Per-skill denominator disclosures

The lowest score in this repo is **99.0%**. The highest is **99.49%**. Each report shows its math; each report discloses its own ambiguities.

- **oms-cocoindex** — 114/114 provenance entries; 55 public-API denominator from `__init__.py` `__all__`; 20/20 sampled signatures matched at the exact pinned line. Two denominators (barrel vs. full surface) are both disclosed with rationale. → [test report](forge-data/oms-cocoindex/0.3.37/test-report-oms-cocoindex.md)
- **oms-cognee** — 34/34 exports documented; denominator is the `cognee/__init__.py` barrel (61 lines, 34 public re-exports) at pinned commit `3c048aa4` (v1.0.0). → [test report](forge-data/oms-cognee/1.0.0/test-report-oms-cognee.md)
- **oms-storybook-react-vite** — **215/216.** The 1-entry drift is GAP-004, documented below. → [test report](forge-data/oms-storybook-react-vite/10.3.5/test-report-oms-storybook-react-vite.md)
- **oms-uitripled** — 34-entry denominator (not 11, not 25) with the full reconciliation reasoning in the report. → [test report](forge-data/oms-uitripled/0.1.0/test-report-oms-uitripled.md)

---

## GAP-004: the one we lost

The oms-storybook-react-vite test report scores **215/216**, not 216/216. The missing entry is logged openly as **GAP-004** in the test report: a 1-entry drift where the canonical export surface (via the provenance map) diverges from the stated denominator. The report names the gap, shows the math, and leaves the drift visible for the next recompilation pass.

We didn't hide the rough edge. We wrote it down. Read it yourself: [`forge-data/oms-storybook-react-vite/10.3.5/test-report-oms-storybook-react-vite.md`](forge-data/oms-storybook-react-vite/10.3.5/test-report-oms-storybook-react-vite.md).

A promise of perfection is suspicious. A promise of visible fallibility is trustworthy.

---

## Further audit trails

For readers who want to verify a specific aspect of a skill's compilation, the receipts are split across these files:

| Question                                       | File                                              |
| ---------------------------------------------- | ------------------------------------------------- |
| What AST patterns were used?                   | `forge-data/<name>/<ver>/extraction-rules.yaml`   |
| What did the extractor actually capture?       | `forge-data/<name>/<ver>/evidence-report.md`      |
| How was the skill scored? Show me the math.    | `forge-data/<name>/<ver>/test-report-<name>.md`   |
| How was the skill scoped?                      | `forge-data/<name>/skill-brief.yaml`              |
| What symbol came from where?                   | `forge-data/<name>/<ver>/provenance-map.json`     |
| What commit does the skill anchor to?          | `skills/<name>/<version>/<name>/metadata.json`    |

The split between `skills/` and `forge-data/` is intentional: `skills/` ships to consumers, `forge-data/` is the audit trail. You don't need `forge-data/` to use a skill — you need it to verify one.

---

## Found a drift?

If a documented signature doesn't match the source at the pinned commit, that is a bug, not a footnote. [Open an issue](https://github.com/armelhbobdad/oh-my-skills/issues) with the file and line. We fix it publicly, with a new commit SHA and a new provenance map. That is the entire deal.
