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

**Signature checks depend partly on judgment.** Since Skill Forge 6.0.0, every signature judge reads one rules file, `signature-comparison-rules.md`. It settles the cases 4.0.0 left open:
- each form a skill gives a name is compared, a brief one in `SKILL.md` and a detailed one in a reference file alike ([#826](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/826));
- component props have their own rules ([#827](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/827));
- equivalent type spellings, and return annotations the function's own body contradicts, are spelled out ([#835](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/835));
- a parameter listed without its default, and a return type one side leaves out, have rules ([#843](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/843));
- an overloaded function is read through its implementation ([#845](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/845)).

The test also pins the names a skill writes in a fixed form (since 6.0.0, [#790](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/790)) and, since 7.0.0, the signature some of those forms write: a declaration in a cited code block, a `Signature` cell, or a heading or first cell that writes the full call. Two runs agree on those. Props and Params cells and usage forms are still read by each run ([#888](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/888), open). 8.0.0 settles four more forms the judges used to decide alone, among them a parameter list typed in another package and a rest element in a destructured props form ([#925](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/925), [#928](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/928), [#930](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/930), [#932](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/932)), and stops counting the names an `export *` from another package brings in ([#926](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/926)).

Judges still read some cases differently. The runs behind the reports we publish apply the rules file word for word and write down, in each report's Coverage Notes, each call it leaves open and how they counted it. We filed the open cases our verification found could change a verdict; those still open include [#916](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/916), [#917](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/917), [#927](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/927), [#931](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/931), [#967](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/967), [#968](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/968), [#970](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/970) and [#973](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/973). The reports also record calls we judged settled by the rules as written, such as a `—` Default cell read as empty, and names written only on import lines counted as documented, which we have not filed. The variance is real:
- Three oms-uitripled lines that copy the source's destructuring defaults were matches in one run (report `06c47fb4`) and Critical gaps in the next (report `8774ab64`), with no change to the lines. The rules support the second reading: a default marks its prop optional, which the props type contradicts. We fixed the lines.
- Two oms-cognee sentences, unchanged since November 3, were left as prose in one run (report `d1bc353b`) and read as call forms missing a required argument in the next (report `1e68a210`). We fixed them.
- The oms-storybook-react-vite tier A set held 376 names in one run (report `7bb97bf8`, 100%) and 389 in the next (report `cc17d5d0`, 98.23%), with one row changed between them, because the two runs read `export type * from '@vitest/spy'` differently ([#926](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/926)). 8.0.0's rule settles it: such a star adds no name.
- oms-cocoindex's `ExceptionContext`, named only inside the exception handler's type, was counted as documented by a 7.0.0 run and as undocumented by the first 8.0.0 run, on the same text ([#967](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/967)). We documented it.

Full method: [Skill Forge → Completeness Scoring](https://armelhbobdad.github.io/bmad-module-skill-forge/how-it-works/#completeness-scoring).

### Reproducing the score

The scoring script lives in Skill Forge. To re-run it against this repo's pinned source trees:

1. Install [Skill Forge](https://github.com/armelhbobdad/bmad-module-skill-forge).
2. Check out the pinned upstream commit named in `skills/<name>/<version>/<name>/metadata.json` → `source_commit`.
3. Run `skf-test-skill` against the skill directory. It re-extracts the public surface from source, diffs against the skill, and emits the same numeric score the test report records.

If the score you compute differs from the one in this repo's test report by more than rounding, that is a bug. [Open an issue.](https://github.com/armelhbobdad/oh-my-skills/issues)

---

## Per-skill denominator disclosures

Three skills pass Skill Forge 8.0.0's gate on a strict test of exactly what ships, all at **100%**: oms-cocoindex, oms-storybook-react-vite and oms-uitripled. oms-cognee is blocked by the hard gate and has no score. Each skill's `metadata.json` stats pass `skf-render-metadata-stats.py --check` against its provenance map. Each report shows its math; each report discloses its own ambiguities. Each provenance entry is labeled by the tool that read its signature, `T1` for an ast-grep match and `T1-low` for a read of the source by eye. The counts:
- oms-cocoindex: 98 `T1` / 56 `T1-low`.
- oms-cognee: 36 / 50. Five entries an ast-grep rule located have signatures read by eye.
- oms-storybook-react-vite: 247 / 131. 52 entries an ast-grep rule located have signatures read by eye. Most `T1-low` entries were added in the 7.0.0 rounds, for newly documented names whose signatures were read from the source by eye.
- oms-uitripled: 10 / 305. Its component and UI-primitive exports were added by a repair that reads new exports by eye.

- **oms-cocoindex** 1.0.0 — **100%**. A strict 8.0.0 test of the version that ships passed with no Critical or High gap.

  Category scores:
  - Export Coverage: 72/72, the root `cocoindex` barrel at pinned commit `5fe4f37a`. The 4.0.0 run counted the brief's `scope.include` union (79 names), because it read the source as a Cargo workspace; 7.0.0 and later apply the brief's `scope.exclude` first and read a single Python package.
  - Signature Accuracy: 48/48.
  - Type Coverage: 1/1. Only one surface record is a type, the class `ComponentMountHandle`. The 60 root exports Skill Forge restores, because the brief's doc globs match no file, carry no kind, so this category measures almost nothing for cocoindex ([#913](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/913)).
  - External Validation: 100%.

  The report records four calls the rules leave open. Two are read as matches: the `@coco.fn(...)` forms, compared with the decorator instance's `__call__`, and `Symbol(...)`, read through its alias. A user-code `mount_table_target` in the connector-authoring example is left out as no form of the library export ([#973](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/973)). A migration table under a heading the migration check does not look for is counted as no migration section. Read the other way, each of the first three would be a Critical gap that blocks the gate, and the fourth would add one Info gap.

  What the 7.0.0 rounds fixed (`e05fa06`, `5381bef`, `4361c08`, `301a6f4`):
  - Three forms a strict judge would block on: `mount` and `mount_each` synopses with the wrong parameter names, and `use_mount`'s callable type.
  - The twelve reference-file errors [#17](https://github.com/armelhbobdad/oh-my-skills/issues/17) tracked, among them `FileLike.metadata()` and `FilePathMatcher.matches`, which do not exist, and `UuidGenerator.next_uuid`, which is not async.
  - `@coco.fn(batching=True, ...)` and `@coco.fn(runner=GPU)`. The skill showed them as working decorators. At the pinned commit, any of `batching`, `runner` or `max_batch_size` sends `@coco.fn` to a builder that raises `ValueError` for an async function, whatever its docstring says. It also raises for a sync function when `batching` or a `runner` is set; with `max_batch_size` alone, a sync function gets a `SyncFunction` that ignores it (`python/cocoindex/_internal/function.py:1479`, `:1519`, `:1690-1707`). The skill now documents `@coco.fn.as_async`, as cocoindex's own `ops` package does.
  - CLI flags (`-d` adds a directory to `sys.path` and changes no working directory), two classes described as Protocols, and an S3 walker said to yield `(key, S3File)` pairs: iterating it yields `S3File` objects, and only its `items()` yields pairs.

  Under 8.0.0 (`15cefa0`): `ExceptionContext`, which the skill named only inside the exception handler's type, is now documented from its dataclass and from what the handler chain passes in it. The first 8.0.0 run counted it as undocumented (99.37%).

  Left open: 11 Medium stale-documentation gaps on connector exports, which are false positives ([#912](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/912)); a brief glob that matches no file and a barrel count (both Medium). → [test report](forge-data/oms-cocoindex/1.0.0/test-report-oms-cocoindex-20261107T115927Z-5db1615d.md)
- **oms-cognee** 1.6.2 — **blocked, unscored**. Its only blocking gaps are two Critical false positives. The skill documents the lightweight `cognee.pipelines.run_pipeline` (`run_pipeline.py:37`) in two forms, and both match it. The test compares them with the dataset orchestrator of the same name (`pipeline.py:53`), the only `run_pipeline` its surface holds ([#918](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/918)). We left the documentation right and the block visible. The fix, [#956](https://github.com/armelhbobdad/bmad-module-skill-forge/pull/956), compares each form with the declaration its own citation names; it is not in 8.0.0, and one of the two forms will also need a citation the skill does not give it yet.

  The blocked 8.0.0 run's category figures:
  - Export Coverage: 92/92, the `cognee/__init__.py` barrel at pinned commit `ba3631f2` (v1.6.2), including the `cognee.migration` members it re-exports.
  - Signature Accuracy: 74 of 75 names (98.67%); the one miss is `run_pipeline`.
  - Type Coverage: 35/35.
  - External Validation: 90%. skill-check rates the `SKILL.md` body at about 5,700 tokens, over its 5,000-token budget.

  The report records four calls the rules leave open, each read as a match: a constructor call compared without `__init__`'s `self`, a keyword that only `**kwargs` receives, classes compared by the fields their dataclass or model generates ([#968](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/968)), and the two `run_pipeline` functions kept apart in the split-body check ([#927](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/927)).

  What the 7.0.0 rounds fixed (`47fa2aa`, `fa19ee4`, `d25ff9f`):
  - Six COGX migration record types documented as requiring `kind`, which has a default.
  - `run_tasks_parallel`, given two different return types in two reference files. Both now write `-> Task`, what the body returns; its annotation says otherwise, which the report records as an Info observation to report upstream.
  - `visualize_memory_provenance` with its first parameter out of place, and `LLMGateway.acreate_structured_output`'s parameter names.
  - Prose calls to `search` and `recall` that left out the required `query_text`, and a parameter table missing six optional parameters.

  Left open: two Medium stale-documentation gaps for names whose files the brief scopes out (the docs are right), a barrel count (Medium) and the token budget (Low). → [test report](forge-data/oms-cognee/1.6.2/test-report-oms-cognee-20261107T112455Z-eec853d0.md)
- **oms-storybook-react-vite** 10.3.5 — **100%**. Its brief's `scope.tier_a_include` names the story-authoring entry points (`storybook/test`, `preview-api`, `actions`, `theming`, `viewport`, `highlight`, `@storybook/react-vite`, `@storybook/react`, the addon-docs blocks, the a11y/themes/vitest addons, the builder-vite config helpers). Since 5.0.0, Export Coverage counts only the documented names in that set ([#792](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/792)), and the extractor reads the destructured and per-package names 4.0.0 missed ([#786](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/786), [#830](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/830)).

  Category scores:
  - Export Coverage: 370/370, against `stats.effective_denominator` 370, the size of the set this run read.
  - Signature Accuracy: 180/180. 114 forms were compared with their declaration and matched. The other 66 are Testing Library bindings whose parameters are typed in `@testing-library/dom`, outside the source tree: 8.0.0's rule leaves them uncompared and counts them as matching ([#925](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/925)). The 7.0.0 run compared them with that package's declarations.
  - Type Coverage: 128/128. Under 7.0.0 it was 134/147 (98.23% overall): the run read `export type * from '@vitest/spy'` as 19 names, 13 of them undocumented. 8.0.0 counts no name for a star from another package ([#926](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/926)).
  - External Validation: 100%.

  The pass turns on how the split-body check reads names the skill documents as two different exports, such as core's and React's `composeStories`. This run paired each form with its own package's, as the skill labels them; read as one export, they would be a High gap that blocks ([#927](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/927)). Its report writes that call down, with the others it made.

  What the 7.0.0 rounds fixed (`e0415b5`, `9265cff`, `c71172d`, `bdc326f`, `fdb1a81`, `ac98bed`):
  - `afterEach`'s return type, the react-vite preset's `viteFinal` type and `useParameter`'s parameters, the last two tracked in [#17](https://github.com/armelhbobdad/oh-my-skills/issues/17).
  - Names documented under entry points that do not export them: `MockUniversalStore` and three store hooks, which `storybook/manager-api` exports only with the `experimental_` prefix; four CSF types listed under `storybook/internal/types`; `createTest` from `storybook/preview-api`; module file names listed as exports; and `ColorControlProps`.
  - Classes labeled as types, a `PreviewWeb` alias that is a subclass, and parameter forms that differed from the source's destructuring.
  - 134 tier A names the skill did not document, which took Export Coverage from 63.78% to 100%. `stats.effective_denominator` went from 280 to 370, the size of the tier A set.

  Left open: 85 Medium stale-documentation gaps. 79 are names the brief scopes out (internal subpaths such as `storybook/internal/components`); 6 are the `@vitest/spy` types the skill documents, which 8.0.0's star rule no longer puts on the surface ([#912](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/912) for the first, [#926](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/926) for the second). Also a barrel count (Medium). Under 4.0.0 we estimated the authored list by hand (391 names, [`tier-a-fuller-count.json`](forge-data/oms-storybook-react-vite/10.3.5/tier-a-fuller-count.json)); Skill Forge's own set replaces that estimate. → [test report](forge-data/oms-storybook-react-vite/10.3.5/test-report-oms-storybook-react-vite-20261107T112449Z-0cc4693c.md)
- **oms-uitripled** 0.1.0 — **100%**. The 4.0.0 run was blocked by a false positive on `cn`. Since 7.0.0 the test keeps one record per declaring file and compares the declaration the skill cites, so it is gone.

  Category scores:
  - Export Coverage: 327/327, the stored count for the brief's `scope.include` union.
  - Signature Accuracy: 269/269.
  - Type Coverage: 42/42.
  - External Validation: 100%.

  8.0.0 settles the three forms the 7.0.0 pass rested on without recording them: `NativeButton`, `NativeLiquidButton` and `SocialLoginButton` are documented with their source declarations, rest element `...props` included, and the rules now read a rest element as standing for every prop the form does not name ([#932](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/932)). The 8.0.0 report records the call the pass rests on now, and one the 100% rests on:
  - A `—` in the Default column of the `ThemeProvider` and `UILibraryProvider` props tables, read as an empty cell, as Skill Forge's own props-table format writes it. Read as a value, it would mark the required `children` optional: two Critical gaps.
  - Seven primitives (`Button`, `Card`, `CardContent`, `CardHeader`, `Input`, `Dialog`, `DialogContent`) named only on import lines in an example, counted as documented. Without them, Export Coverage would be 97.86% and, by our arithmetic, the score 99.04%: still a pass.

  What the 7.0.0 rounds fixed (`97951c3`, `bd2c805`, `2e6e9e7`, `2ca0ff8`):
  - The six errors [#17](https://github.com/armelhbobdad/oh-my-skills/issues/17) tracked: `HeroSection` import paths, `NativeHoverCardProps.size`, two pointers to entries that did not exist, three components with no reference row, and the `cn` and `UILibrary` descriptions.
  - Three motion components documented with the source's destructuring defaults on props their type requires.
  - The registry `Component`'s fields, a catalog claim that react-shadcn ships `NativeCounterUp`, and two completeness claims that left out `PasswordInput`, `AnimatedCheckbox`, a second `NativeLiquidButton` with different props and a copy of `NativeStartNow`.

  Left open: a stale brief glob and a barrel count (both Medium). → [test report](forge-data/oms-uitripled/0.1.0/test-report-oms-uitripled-20261107T112452Z-65994952.md)

Every older report stays in `forge-data/` next to the one that replaced it, the failing runs included: each round is a test report, fix commits and a re-test, in that order, in the git history. The reverted storybook repair's reports are in that history too (`35d506b`).

---

## The points we lost

**oms-cognee: no score.** Two false positives block it ([#918](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/918)). We could have dodged them by documenting the lightweight runner under another name, or by dropping one of its forms. We kept the documentation right and the block visible. The fix is open as [#956](https://github.com/armelhbobdad/bmad-module-skill-forge/pull/956) and not in 8.0.0. Its `SKILL.md` body is also over skill-check's 5,000-token budget, which will cost a point once it is scored.

**Why the numbers changed under 7.0.0.** Under 4.0.0 we published 100% for oms-cocoindex and 99% for oms-cognee; oms-storybook-react-vite and oms-uitripled were blocked. The first 7.0.0 tests, on the same skills:
- oms-cocoindex: PASS 100%.
- oms-uitripled: PASS 100%, its `cn` false positive gone.
- oms-cognee: blocked on 8 Critical and 1 High gaps: seven real errors and the two `run_pipeline` false positives.
- oms-storybook-react-vite: blocked on one real error, with Export Coverage at 63.78% of its 370 tier A names.

Two rounds of fixes followed for oms-cocoindex, oms-cognee and oms-uitripled, and three for oms-storybook-react-vite. In each round one agent fixed the errors by hand against the pinned source, and a strict test re-measured the result. A separate read-only agent reviewed each round's changes before its test, except the last one-row storybook fix (`ac98bed`), which went straight to its re-test. The rounds found real errors in all four skills, including in the two that passed: three cocoindex forms a strict judge would block on and the `@coco.fn` decorator forms that raise, and the three uitripled lines a later run blocked. Before that, under 4.0.0 and earlier, we published 100%, 99.00%, 100% and 95.17%. Three of those runs read the signature rules leniently; uitripled's 100% did not. Storybook's also rested on a stored count that credited every documented name. That history, and the 4.0.0 version of this page, are in the git history (`64a8681`).

**What changed under 8.0.0.** On the same skill text, oms-storybook-react-vite went from 98.23% to 100%, because 8.0.0 counts no name for an `export type *` from another package ([#926](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/926)), and oms-uitripled's three `...props` forms went from calls its report never wrote down to a written rule ([#932](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/932)), its score unchanged at 100%. The first 8.0.0 test of oms-cocoindex counted `ExceptionContext` as undocumented (99.37%), a reader's call the contract does not settle ([#967](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/967)); we documented it (`15cefa0`), the only change to a skill under 8.0.0, and the re-test passed at 100%. oms-cognee is blocked by the same two false positives.

The Skill Forge defects these runs ran into are filed upstream: [#912](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/912) to [#932](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/932) from the 7.0.0 runs, many of them fixed in 8.0.0, and [#965](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/965) to [#973](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/973) from the 8.0.0 runs.

We didn't hide the rough edges. We wrote them down. Read them yourself, starting with the reports for the versions that ship:
- [`oms-cocoindex`](forge-data/oms-cocoindex/1.0.0/test-report-oms-cocoindex-20261107T115927Z-5db1615d.md)
- [`oms-cognee`](forge-data/oms-cognee/1.6.2/test-report-oms-cognee-20261107T112455Z-eec853d0.md)
- [`oms-storybook-react-vite`](forge-data/oms-storybook-react-vite/10.3.5/test-report-oms-storybook-react-vite-20261107T112449Z-0cc4693c.md)
- [`oms-uitripled`](forge-data/oms-uitripled/0.1.0/test-report-oms-uitripled-20261107T112452Z-65994952.md)

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
