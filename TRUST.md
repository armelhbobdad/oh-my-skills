# TRUST.md — How to verify Oh-My-Skills

The [README](README.md) makes a single promise: every claim in every skill traces back to a commit SHA, and you can prove it in 60 seconds. This document is the long form — the scoring math, the disclosed gaps, and the deeper audit trails for readers who want to drill past the headline.

If you haven't read the README's [Don't trust us. Audit us.](README.md#dont-trust-us-audit-us) section yet, start there. This file picks up where it leaves off.

---

## How the score is computed

The final score isn't a vibe — it's a weighted average of five deterministic measurements, run by a Python script that guarantees *"the same inputs always produce the same score."* Because every skill in this repo runs in **naive mode** (individual skills, no cross-stack integration to check), the normally 18%-weighted Coherence dimension is redistributed across the other four categories:

| Weight  | Dimension             | What it measures                                                                                                    |
| ------- | --------------------- | ------------------------------------------------------------------------------------------------------------------- |
| **45%** | Export Coverage       | `(documented exports / source exports) × 100` — what fraction of the library's public API is in `SKILL.md`?         |
| **25%** | Signature Accuracy    | Do documented function signatures match the real ones at the pinned commit — parameter names, types, order, return? |
| **20%** | Type Coverage         | Are the types and interfaces referenced in exports fully documented?                                                |
| **10%** | External Validation   | [`skill-check`](https://github.com/thedaviddias/skill-check) quality score, averaged with the [`tessl`](https://tessl.io) content score when Tessl Review is configured (it was off for the current reports) |

Each category is computed as `(items_passing / items_total) × 100`. The final score is `sum(category_weight × category_score)`. **Default pass threshold: 80%** — anything below that fails the gate and triggers `update-skill`, not `export-skill`. A Critical or High gap (a wrong signature, say) blocks the test before it is scored, whatever the arithmetic would say. A score is only meaningful because the denominators are disclosed (in each skill's test report) and the arithmetic is reproducible from each skill's [`forge-data/<ver>/test-report-*.md`](forge-data/).

**Signature checks depend partly on judgment.** Skill Forge 4.0.0's written rule compares each documented signature's parameters (name, type, order, optionality) and return type with the source. It has no written case for:
- a prop list that leaves out optional props ([#827](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/827));
- type spellings such as `dict` against `dict[str, Any]`, or a declared annotation that the function's own body contradicts ([#835](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/835));
- a parameter listed without its default, or a return type one side leaves out ([#843](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/843));
- an overloaded function, whose first `@overload` stub the plan may compare instead of the implementation ([#845](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/845)).

So two runs can judge the same documentation differently. Three of our four earlier passes read these cases leniently. The reports we publish now apply the written rule, write down how they read the cases it does not decide, and say which calls they counted. They do not all read those cases alike. The cognee and storybook runs compare a documented parameter given without a type on name, order and optionality only. The cocoindex run records the same case as borderline and does not count it. The variance is real:
- One strict oms-cognee run counted three such calls as Critical gaps and was blocked (report `2a66250d`). The published run judged the same three as matches on the same documentation and passed (report `12e5ccdf`).
- The storybook `useParameter(key, default)` row, unchanged since April, was called a match in re-test `c861c18d` and a Critical mismatch in the published run (report `6e2b972a`).

Skill Forge's main branch has since graded an optional member that a form labeled partial leaves out as Info, and a renamed TypeScript parameter as Low ([#834](https://github.com/armelhbobdad/bmad-module-skill-forge/pull/834)); the 4.0.0 release these reports used does not.

Full method: [Skill Forge → Completeness Scoring](https://armelhbobdad.github.io/bmad-module-skill-forge/how-it-works/#completeness-scoring).

### Reproducing the score

The scoring script lives in Skill Forge. To re-run it against this repo's pinned source trees:

1. Install [Skill Forge](https://github.com/armelhbobdad/bmad-module-skill-forge).
2. Check out the pinned upstream commit named in `skills/<name>/<version>/<name>/metadata.json` → `source_commit`.
3. Run `skf-test-skill` against the skill directory. It re-extracts the public surface from source, diffs against the skill, and emits the same numeric score the test report records.

If the score you compute differs from the one in this repo's test report by more than rounding, that is a bug. [Open an issue.](https://github.com/armelhbobdad/oh-my-skills/issues)

---

## Per-skill denominator disclosures

Two skills pass Skill Forge 4.0.0's gate on a strict test of exactly what ships: oms-cocoindex at **100%** and oms-cognee at **99%**. oms-storybook-react-vite and oms-uitripled are blocked by the hard gate and have no score. Each skill's `metadata.json` stats pass `skf-render-metadata-stats.py --check` against its provenance map. Each report shows its math; each report discloses its own ambiguities. Each provenance entry is labeled by the tool that read its signature, `T1` for an ast-grep match and `T1-low` for a read of the source by eye. The counts:
- oms-cocoindex: 101 `T1` / 54 `T1-low`. A review relabeled 45 entries that no Python recipe could have matched.
- oms-cognee: 37 / 49. Five entries an ast-grep rule located have signatures read by eye.
- oms-storybook-react-vite: 220 / 8. That is one older entry, five added by a gap-driven repair, and two from corrections made by hand.
- oms-uitripled: 18 / 293. Its component and UI-primitive exports were added by a repair that reads new exports by eye.

- **oms-cocoindex** 1.0.0 — **100%**. A strict test of the version that ships passed with no Critical or High gap.

  Category scores:
  - Export Coverage: 79/79 on the brief's `scope.include` union (95 files).
  - Signature Accuracy: 27/27. Nine borderline calls were recorded and not counted, such as bare `*args`/`**kwargs` where the source annotates `P.args`/`P.kwargs`. Counted as mismatches, they would be nine Critical gaps (18/27), and the gate would block the run before scoring. So this pass, like cognee's, turns on the report's borderline calls.
  - Type Coverage: 36/36.
  - External Validation: 100%.

  We used to publish 100% for it (report `bf06d70f`) on a lenient reading: that run found no mismatch between `SKILL.md` and its references. The first strict test, on the same text, found 7, all real: misnamed parameters in three, a missing `**kwargs` in four (one gap had both), and a missing optional parameter in one. While we fixed those by hand (`e2d9f28`), a review found 16 more errors, which we also fixed (`c16c74d`). Among them were CLI flags that do not exist, a function the package does not export, and 45 provenance entries labeled as ast-grep matches no Python recipe can make. The next strict test found one more real gap, a field shown without its `None` default, which we fixed (`d19368a`) before the test of the version that ships.

  Left open:
  - a brief glob that matches no file and a barrel count (both Medium);
  - nine method signatures in the reference files, which the report records as warnings without a gap, and two false descriptions it records as observations, one of them also in `SKILL.md` ([#17](https://github.com/armelhbobdad/oh-my-skills/issues/17)). For example, `FileLike.metadata()` and `FilePathMatcher.matches` do not exist, and `UuidGenerator.next_uuid` is not async;
  - two more reference-file errors the report notes: `FileLike.read_text`'s default `errors` is `"replace"`, not `"strict"`, and `PatternFilePathMatcher.__init__`'s parameters are not keyword-only.

  → [test report](forge-data/oms-cocoindex/1.0.0/test-report-oms-cocoindex-20261103T131524Z-5907fba9.md)
- **oms-cognee** 1.6.2 — **99%**. A strict test of the version that ships passed with no Critical or High gap.

  Category scores:
  - Export Coverage: 92/92, the `cognee/__init__.py` barrel at pinned commit `ba3631f2` (v1.6.2), including the `cognee.migration` members it re-exports.
  - Signature Accuracy: 72/72.
  - Type Coverage: 35/35.
  - External Validation: 90%, the point lost below.

  The pass turns on borderline calls that the report writes down:
  - It judged `export`, `visualization_server` and `run_tasks_parallel` as matches. `export` is compared at its first `@overload` stub. The other two declare return annotations their own bodies contradict, and the skill documents what they really return. An earlier strict run counted the same three as Critical gaps and was blocked (report `2a66250d`; [#845](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/845), [#835](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/835)).
  - It left uncounted one `SKILL.md` signature that omits a return type its reference states (`cognee_network_visualization`). Counted, it would block the gate ([#843](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/843)).

  We used to publish 99.00% for it (report `d56413cb`) on a lenient reading: that run judged short `SKILL.md` signatures, and `dict` against `dict[str, Any]`, as matches. The first strict test found 24 real gaps, all fixed by hand (`8311884`, `87b7590`). Among them were `cognify` and `run_custom_pipeline` parameters in the wrong order, and entry classes whose optional fields read as required.

  While fixing them, a repair corrected two stale globs in the brief. That stopped the stale-scope guard from restoring the whole barrel, so 26 `cognee.migration` names fell out of the count for one run (92 to 66). We added the migration package to the brief's `scope.include` so they are measured again (`9cb7983`). Both changes are recorded as brief amendments.

  Left open: four Medium stale-documentation gaps for documented names whose files the brief scopes out (the docs are right), a barrel count (Medium) and the token budget (Low). → [test report](forge-data/oms-cognee/1.6.2/test-report-oms-cognee-20261103T134151Z-12e5ccdf.md)
- **oms-storybook-react-vite** 10.3.5 — **blocked, unscored**. Its brief's `scope.tier_a_include` names the story-authoring entry points (`storybook/test`, `preview-api`, `actions`, `theming`, `viewport`, `highlight`, `@storybook/react-vite`, `@storybook/react`, the addon-docs blocks, the a11y/themes/vitest addons, the builder-vite config helpers). A strict test of the version that ships was blocked by 4 Critical signature gaps:
  - Two compare the React portable-stories wrappers the skill documents (`setProjectAnnotations`, `composeStories`) with core's renderer-agnostic functions. These are false positives ([bmad-module-skill-forge#781](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/781)).
  - Two are real errors, written in April and not fixed yet ([#17](https://github.com/armelhbobdad/oh-my-skills/issues/17)). `references/framework-config.md` types the react-vite preset's `viteFinal` as `PresetProperty<'viteFinal'>`, a type with no `viteFinal` key. `references/core-api.md` gives `useParameter(key, default)`, where the source has `(parameterKey: string, defaultValue?: S)`.

  A blocked run is never scored. Its category scores are:
  - Signature Accuracy: 82/86 (95.35%).
  - Type Coverage: 98/120 (81.67%).
  - External Validation: 100%.
  - Export Coverage: 100%, but only because the stored count credits every documented name ([#792](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/792); [#813](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/813) tracks why the stored count, not the brief, decides the denominator). The run names no tier A export. Re-test `970f8905` (before the last repairs) did not either, but its notes intersect its inventory with the 280 names and find 204 documented (72.86%). The last run that named each undocumented name as a gap, `bad58550`, found 206 (73.57%).

  The 280-name list is itself short of the authored surface:
  - 13 names that tier A files define are credited to another file's declaration of the same name, because Skill Forge 4.0.0's extractor keeps one record per name across Storybook's packages and the first package by path wins. Among them are `StoryObj`, `Decorator`, `StorybookConfig`, `FrameworkOptions` and `defineMain`, credited to Angular's, and `StoryFn` and `StoryContext`, credited to core's ([#830](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/830)).
  - Another 20 names that tier A entries re-export are recorded with no defining file.
  - 4 more are counted at definitions outside tier A, as Skill Forge's protocol says.

  The 4.0.0 extractor also cannot read the 74 names `storybook/test` exports by destructuring, such as `expect`, `screen`, `within` and `waitFor` ([#786](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/786)). That is fixed on Skill Forge's main branch by PR #829 (2026-11-03), but every report here ran on the 4.0.0 release.

  Counting all of these gives a fuller list of 391 names. Reading a name as documented when it has a provenance entry or appears inside a backtick span, 268 of them are documented (69%); counting any whole-word mention, 275 (70%). By the same readings, the 280-name list alone is about 80% documented. Skill Forge's own inventory credited 204 of the 280 in re-test `970f8905`, before the last repairs. Adding the 45 other fuller-list names the backtick reading finds documented gives 249 of 391, about 64%. This count is ours, not a Skill Forge measurement. The name lists and both readings are in [`tier-a-fuller-count.json`](forge-data/oms-storybook-react-vite/10.3.5/tier-a-fuller-count.json). → [test report](forge-data/oms-storybook-react-vite/10.3.5/test-report-oms-storybook-react-vite-20261103T131516Z-6e2b972a.md)
- **oms-uitripled** 0.1.0 — **blocked, unscored**. A strict test was blocked by one Critical gap, a false positive. Two exports share the name `cn`, and the test compared the one the skill documents (`@uitripled/utils`) with the other ([#781](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/781), [#830](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/830)). Under the strict rule, 265 of its 266 signatures match, and every destructured props list matches its source. So its earlier 100% (report `aff41a98`) did not rest on lenient prop judging. The test did record six non-blocking documentation errors as Info gaps, which we have not fixed yet ([#17](https://github.com/armelhbobdad/oh-my-skills/issues/17)):
  - `HeroSection` import paths that name files that do not exist;
  - `NativeHoverCardProps.size` shown as required;
  - pointers to a `types.md` entry and a `SKILL.md` table that do not exist;
  - three components with no reference row;
  - two false descriptions: the react-shadcn `cn` as an identical implementation, and the `UILibrary` restriction as runtime-only.

  Category scores:
  - Export Coverage: 100%, with 330 names documented against the stored count of 327 for the brief's `scope.include` union.
  - Signature Accuracy: 265/266 (99.62%).
  - Type Coverage: 42/42.
  - External Validation: 100%.

  Also left open: a stale brief glob and a barrel count (both Medium). → [strict test report](forge-data/oms-uitripled/0.1.0/test-report-oms-uitripled-20261103T100001Z-981f84e6.md)

Every older report stays in `forge-data/` next to the one that replaced it, the failing first runs under 4.0.0 included: each repair is a test report, an update-skill commit and a re-test, in that order, in the git history. The reverted storybook repair's reports are in that history too.

---

## The points we lost

**oms-cognee: 99%.** skill-check rates its `SKILL.md` body at about 5,696 tokens, over its 5,000-token budget, and logs that as a Low gap (`body.max_tokens`). External Validation is therefore 90%, and the weighted score loses one point. Moving detail into `references/` would recover it; we left it visible instead of trimming the body to chase the number.

**Why the old numbers changed.** We used to publish 100% for oms-cocoindex, 99.00% for oms-cognee, 100% for oms-uitripled and 95.17% for oms-storybook-react-vite. Strict tests, which apply Skill Forge's written signature rule with no leniency, blocked all four at first:
- **oms-cocoindex and oms-cognee:** the earlier runs counted short `SKILL.md` signatures that left out parameters, and imprecise types, as matches. The strict tests found real errors, and we fixed them by hand against the pinned source. Both now pass a strict test of what ships. For the split-body gaps, where the reference was right and `SKILL.md` wrong, Skill Forge's own repair would have copied `SKILL.md`'s errors into the reference files ([#779](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/779)).
- **oms-uitripled:** it held up under the strict signature rule, and its only blocking gap is a false positive. Six non-blocking documentation errors the test recorded are still open ([#17](https://github.com/armelhbobdad/oh-my-skills/issues/17)).

**oms-storybook-react-vite: no score.** We used to publish **95.17%** for it (report `a5890950`). That number was too high, for two reasons. Its Export Coverage was 100% only because Skill Forge's stored count credits every documented name. And its signature judges read the doc-block prop lists leniently, which no Skill Forge rule permits or forbids ([#827](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/827)).

Re-testing it showed what that number hid. We removed the stored count so the test would name each undocumented name, and that run measured 206 of 280 names documented (73.57%). It also found real errors, among them `definePreview` listed under `storybook/preview-api`, which exports no `definePreview`. A stricter re-test then flagged prop lists that left out optional props, a misnamed `fn` parameter and a misdescribed theme decorator. While reading the source, the agents found two more errors no test flagged: a `SortType` form that does not exist, and three option controls that cannot be imported. A review of a later report (`aac3d053`) confirmed its `DocsContainer` gap as a real error, and found a few more:
- A CSF4 type sketch that names a type that does not exist.
- Two theme types the addon does not export.
- 18 provenance entries citing a comment line.

Before all this, a first round of three repairs had passed at 99.93% by documenting about 800 internal names. It was reverted and the skill re-scoped (`35d506b`), and its reports are kept in git history. Two blocked re-tests and two repairs followed before the 95.17% run.

We fixed those errors against the pinned source:
- **Through Skill Forge:** one gap-driven `update-skill` run repaired 22 signatures and 2 split-body errors.
- **By hand:** every other fix, each in a labeled commit.
  - Two were needed because Skill Forge's own repair halted (`e78cbef`, `474e431`). The test cites Angular's `definePreview`, and repairing from that citation would have written Angular's signature into a React skill ([#824](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/824), [#830](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/830)).
  - The others fixed errors no test gap covered, and that later report's `DocsContainer` and Canvas gaps (`d0e0b3b`, `f186e4d`, `2c08df3`, `ddfcff9`).

A strict test of the version that ships (`6e2b972a`) covers all of these fixes. It found two older real errors no earlier run had flagged, the `viteFinal` type and `useParameter`'s parameters, which are not fixed yet ([#17](https://github.com/armelhbobdad/oh-my-skills/issues/17)).

The authored names the skill does not document stay undocumented, because Skill Forge cannot route them to a repair until those defects are fixed. When re-test `970f8905` last counted them, there were 76 of the 280. Every one of these reports is kept, failing ones included: in `forge-data/`, or for the reverted repair, in git history.

We didn't hide the rough edges. We wrote them down. Read them yourself, starting with the reports for the versions that ship:
- [`oms-cocoindex`](forge-data/oms-cocoindex/1.0.0/test-report-oms-cocoindex-20261103T131524Z-5907fba9.md)
- [`oms-cognee`](forge-data/oms-cognee/1.6.2/test-report-oms-cognee-20261103T134151Z-12e5ccdf.md)
- [`oms-storybook-react-vite`](forge-data/oms-storybook-react-vite/10.3.5/test-report-oms-storybook-react-vite-20261103T131516Z-6e2b972a.md)
- [`oms-uitripled`](forge-data/oms-uitripled/0.1.0/test-report-oms-uitripled-20261103T100001Z-981f84e6.md)

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
