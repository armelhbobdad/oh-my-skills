# TRUST.md — How to verify Oh-My-Skills

The [README](README.md) makes a single promise: every claim in every skill traces back to a commit SHA, and you can prove it in 60 seconds. This document is the long form — the scoring math, the disclosed gaps, and the deeper audit trails for readers who want to drill past the headline.

If you haven't read the README's [Don't trust us. Audit us.](README.md#dont-trust-us-audit-us) section yet, start there. This file picks up where it leaves off.

---

## How the score is computed

The final score isn't a vibe — it's a weighted average of five measurements, computed by a Python script that guarantees *"the same inputs always produce the same score."* Because every skill in this repo runs in **naive mode** (individual skills, no cross-stack integration to check), the normally 18%-weighted Coherence dimension is redistributed across the other four categories:

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

The test also pins the names a skill writes in a fixed form (since 6.0.0, [#790](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/790)) and the signature some of those forms write: since 7.0.0 a declaration in a cited code block, a `Signature` cell, or a heading or first cell that writes the full call, and since 9.0.0 a `Props`, `Params` or `Parameters` cell and a usage form ([#888](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/888)). Two runs agree on those; the forms the floor leaves to the reader can still differ between runs ([#997](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/997), open). 8.0.0 settles four more forms the judges used to decide alone, among them a parameter list typed in another package and a rest element in a destructured props form ([#925](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/925), [#928](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/928), [#930](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/930), [#932](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/932)), and stops counting the names an `export *` from another package brings in ([#926](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/926)). 9.0.0 compares each documented form with the declaration its own citation names ([#918](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/918)), compares a props table as one form ([#931](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/931)), says how a call to a class is compared ([#968](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/968)) and counts a name a skill writes only inside another export's type as undocumented ([#967](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/967)).

Judges and readers still read some cases differently. The reports we publish come from runs of Test Skill as designed, with its subagents: one reader lists what the skill documents, one judge per source file compares the signatures under the rules file word for word, and isolated routers run the discovery test. Each report writes down, in its Coverage Notes, each call the run left open and how it counted it. Our first 9.0.0 runs did not work that way. They ran from agents that cannot start subagents, so Test Skill fell back to one agent doing all of it; an independent judge then re-read each call they left open. Their reports stay in `forge-data/`. Re-run with subagents on the same files, two of the four passes became blocked runs (below). We filed every open case our verification found: [#998](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/998) to [#1021](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/1021) and [#1034](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/1034) to [#1050](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/1050) from the 9.0.0 runs. Those a pass here rests on are [#999](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/999) (oms-cocoindex: a type written without its module prefix, `environment.Environment`), [#1045](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/1045) (oms-cognee: a receiver only one of two documented forms writes), [#1050](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/1050) (oms-storybook-react-vite: a type name its source file declares twice) and [#1003](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/1003) (oms-uitripled: a type cell written with its expansion). oms-uitripled's pass also rests on a reading of one loose `SKILL.md` line we have not yet fixed ([oh-my-skills#21](https://github.com/armelhbobdad/oh-my-skills/issues/21)). The reports also record calls we judged settled by the rules as written, which we have not filed. The variance is real:
- Three oms-uitripled lines that copy the source's destructuring defaults were matches in one run (report `06c47fb4`) and Critical gaps in the next (report `8774ab64`), with no change to the lines. The rules support the second reading: a default marks its prop optional, which the props type contradicts. We fixed the lines.
- Two oms-cognee sentences, unchanged since November 3, were left as prose in one run (report `d1bc353b`) and read as call forms missing a required argument in the next (report `1e68a210`). We fixed them.
- The oms-storybook-react-vite tier A set held 376 names in one run (report `7bb97bf8`, 100%) and 389 in the next (report `cc17d5d0`, 98.23%), with one row changed between them, because the two runs read `export type * from '@vitest/spy'` differently ([#926](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/926)). 8.0.0's rule settles it: such a star adds no name.
- oms-cocoindex's `ExceptionContext`, named only inside the exception handler's type, was counted as documented by a 7.0.0 run and as undocumented by the first 8.0.0 run, on the same text ([#967](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/967)). We documented it, and 9.0.0 settles it: such a name now counts as undocumented.
- Under 9.0.0, two strict oms-cognee runs on text that differed in two table rows listed different sets of documented names, 47 gaps and 45, with the same scores (reports `f7c9d9b8` and `7fa452a6`).
- On identical oms-cognee files, the run without subagents passed at 99% (report `7fa452a6`) and the first run with them blocked on 6 Critical and 19 High gaps (report `7a18a0bc`). Its reader took "an optional `user`", stated once in each of four namespace rows that list methods by name and link to their signatures, as a partial form of each method, under the inventory contract's shared-members clause ([#1034](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/1034)). The wording was correct, and the run said so. Unlike the [#918](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/918) block, this one could be cleared without making the skill less accurate: we removed the phrase from the rows (`bd2a419`), and the reference file still gives every signature.
- On identical oms-storybook-react-vite files, the run without subagents passed at 100% (report `ff52d336`) and the run with them blocked on one Critical gap (report `7349a3c4`). The `actions` row wrote two correct overloads in one cell; the reader recorded them as one list, which `score-signatures.py` joins into a parameter list that matches neither ([#1043](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/1043)). We gave each overload its own row (`fe2242b`).
- oms-cocoindex's first pass with subagents (report `df103fde`) rested on its reader leaving out a migration-table cell that wrote the removed v0.3.37 call `Settings(database=...)`; recorded, it blocks ([#1038](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/1038)). We rewrote the cell (`c5c345d`).

Full method: [Skill Forge → Completeness Scoring](https://armelhbobdad.github.io/bmad-module-skill-forge/how-it-works/#completeness-scoring).

### Reproducing the score

The scoring script lives in Skill Forge. To re-run it against this repo's pinned source trees:

1. Install [Skill Forge](https://github.com/armelhbobdad/bmad-module-skill-forge).
2. Check out the pinned upstream commit named in `skills/<name>/<version>/<name>/metadata.json` → `source_commit`.
3. Run `skf-test-skill` against the skill directory. It re-extracts the public surface from source, diffs against the skill, and emits the same numeric score the test report records.

If the score you compute differs from the one in this repo's test report by more than rounding, that is a bug. [Open an issue.](https://github.com/armelhbobdad/oh-my-skills/issues)

---

## Per-skill denominator disclosures

All four skills pass Skill Forge 9.0.0's gate on a strict test of exactly what ships, run with Test Skill's subagents: oms-cocoindex, oms-storybook-react-vite and oms-uitripled at **100%**, oms-cognee at **99%**. Each skill's `metadata.json` stats pass `skf-render-metadata-stats.py --check` against its provenance map. Each report shows its math; each report discloses its own ambiguities. Each provenance entry is labeled by the tool that read its signature, `T1` for an ast-grep match and `T1-low` for a read of the source by eye. The counts:
- oms-cocoindex: 98 `T1` / 56 `T1-low`.
- oms-cognee: 36 / 50. Five entries an ast-grep rule located have signatures read by eye.
- oms-storybook-react-vite: 247 / 131. 52 entries an ast-grep rule located have signatures read by eye. Most `T1-low` entries were added in the 7.0.0 rounds, for newly documented names whose signatures were read from the source by eye.
- oms-uitripled: 10 / 305. Its component and UI-primitive exports were added by a repair that reads new exports by eye.

- **oms-cocoindex** 1.0.0 — **100%**. A strict 9.0.0 test of the version that ships passed with no Critical or High gap.

  Category scores:
  - Export Coverage: 72/72, the root `cocoindex` barrel at pinned commit `5fe4f37a`. The 4.0.0 run counted the brief's `scope.include` union (79 names), because it read the source as a Cargo workspace; 7.0.0 and later apply the brief's `scope.exclude` first and read a single Python package. 60 of the 72 names are defined in `python/cocoindex/_internal/` files other than `api.py`, which the brief did not include until `9049338`. Until then they counted only because two of the brief's doc globs matched no file, which makes Skill Forge put back root exports defined outside the brief's scope; acting on the gap's advice to fix those globs would have dropped them from the count ([#1009](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/1009)). The brief now includes those files and drops the stale globs, and the count is the same 72 names.
  - Signature Accuracy: 48/48, from 17 judges, one per source file. 32 of the 48 checks bind a form to the declaration its own citation names.
  - Type Coverage: 36/36. 8.0.0 counted one type, because the names Skill Forge put back carried no kind ([#913](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/913), fixed in 9.0.0). Six type aliases the extraction does not list, among them `ExceptionHandler` and `Symbol`, carry no kind and are left out without a warning ([#1020](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/1020)).
  - External Validation: 100%.

  The report records ten calls the rules leave open, and none changes the verdict as the run counted them. One decides the gate: `default_env`'s return, written `Environment` where the source writes `environment.Environment`. The rules list the `typing.`, `collections.abc.` and `React.` prefixes as equivalent spellings and name no module prefix, so read as a complete list it would be a Critical gap ([#999](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/999)). The run before it, also with subagents, passed on one more such call: a migration-table cell that wrote the removed v0.3.37 call `Settings(database=DatabaseConnectionSpec(url=...))`, a name 1.0.0 still exports. That run's reader left the cell out of its inventory on its own judgment; recorded, it blocks ([#1038](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/1038)). The cell was correct as history. We rewrote it so it no longer calls `Settings` (`c5c345d`) and re-tested.

  What the 7.0.0 rounds fixed (`e05fa06`, `5381bef`, `4361c08`, `301a6f4`):
  - Three forms a strict judge would block on: `mount` and `mount_each` synopses with the wrong parameter names, and `use_mount`'s callable type.
  - The twelve reference-file errors [#17](https://github.com/armelhbobdad/oh-my-skills/issues/17) tracked, among them `FileLike.metadata()` and `FilePathMatcher.matches`, which do not exist, and `UuidGenerator.next_uuid`, which is not async.
  - `@coco.fn(batching=True, ...)` and `@coco.fn(runner=GPU)`. The skill showed them as working decorators. At the pinned commit, any of `batching`, `runner` or `max_batch_size` sends `@coco.fn` to a builder that raises `ValueError` for an async function, whatever its docstring says. It also raises for a sync function when `batching` or a `runner` is set; with `max_batch_size` alone, a sync function gets a `SyncFunction` that ignores it (`python/cocoindex/_internal/function.py:1479`, `:1519`, `:1690-1707`). The skill now documents `@coco.fn.as_async`, as cocoindex's own `ops` package does.
  - CLI flags (`-d` adds a directory to `sys.path` and changes no working directory), two classes described as Protocols, and an S3 walker said to yield `(key, S3File)` pairs: iterating it yields `S3File` objects, and only its `items()` yields pairs.

  Under 8.0.0 (`15cefa0`): `ExceptionContext`, which the skill named only inside the exception handler's type, is now documented from its dataclass and from what the handler chain passes in it. The first 8.0.0 run counted it as undocumented (99.37%).

  Under 9.0.0 (`66b64a6`, `73048b4`): `ExceptionHandler`, the handler type the skill wrote only inside other signatures, is named and quoted from its alias (the first 9.0.0 run counted it as undocumented: 98.89%); `SKILL.md`'s "~74 symbols" is now the 72 names the source lists; and three examples are written in forms the rules read one way: a user's lifespan function, named `lifespan` like the export that decorates it, is renamed `env_lifespan`, as the rest of the skill names it ([#1010](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/1010)); the assignment the source makes, `config = AppConfig(name=name_or_config)`, replaces a bare call in prose; and the subpath default is written through the root export, `coco.Symbol(fn.__name__)`. Two `Settings` examples are now calls through the root export, `coco.Settings(db_path=pathlib.Path("state.lmdb"))` (`92c8bad`).

  Left open: a metadata count (Medium). → [test report](forge-data/oms-cocoindex/1.0.0/test-report-oms-cocoindex-20261108T135352Z-27b92a60.md)
- **oms-cognee** 1.6.2 — **99%**. A strict 9.0.0 test of the version that ships, with Test Skill's subagents, passed with no Critical or High gap. Under 7.0.0, once the real errors below were fixed, and under 8.0.0, it was blocked by two Critical false positives: the skill documents the lightweight `cognee.pipelines.run_pipeline` (`run_pipeline.py:37`), and the test compared its forms with the dataset orchestrator of the same name (`pipeline.py:53`), the only `run_pipeline` its surface held ([#918](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/918)). 9.0.0 compares each form with the declaration its own citation names: 69 of the run's 75 checks carry such a binding, the lightweight forms bound to `run_pipeline.py:37` and the orchestrator forms to `pipeline.py:53`. One lightweight form needed a citation the skill did not give it, which `925f195` adds.

  Category scores:
  - Export Coverage: 92/92, the `cognee/__init__.py` barrel at pinned commit `ba3631f2` (v1.6.2), including the `cognee.migration` members it re-exports.
  - Signature Accuracy: 75/75, from 40 judges, one per source file. Two `run_tasks_parallel` forms write `-> Task`, what its body returns, against an annotation that says otherwise; the rules count that as matching, and the report records it as an Info observation to report upstream.
  - Type Coverage: 35/35.
  - External Validation: 90%. skill-check rates the `SKILL.md` body at about 5,700 tokens, over its 5,000-token budget: the one point lost.

  The report records three calls the rules leave open. One decides the gate: `Task.execute`, written with `self` in one reference file and without it in another. Both forms match the source, which leads with `self`, and the run found no mismatch. But the rules drop a receiver only against the source, so read literally the pair is a High split-body gap that blocks ([#1045](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/1045)). The other two change no result either way: the four parameter tables, each read as one form ([#1002](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/1002)), and a `setup_logging()` call in prose, whose file the brief scopes out. The run's inventory reader started from the previous run's inventory, still on disk, and re-checked each entry against the skill's files: Test Skill does not confine the reader to those files ([#1036](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/1036)). The run without subagents (report `7fa452a6`) passed on a different call, `export`'s overload stubs ([#1017](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/1017)); this run's reader found the `SKILL.md` form agreeing with the implementation, as the rules read overloads.

  What the 7.0.0 rounds fixed (`47fa2aa`, `fa19ee4`, `d25ff9f`):
  - Six COGX migration record types documented as requiring `kind`, which has a default.
  - `run_tasks_parallel`, given two different return types in two reference files. Both now write `-> Task`, what the body returns; its annotation says otherwise, which the report records as an Info observation to report upstream.
  - `visualize_memory_provenance` with its first parameter out of place, and `LLMGateway.acreate_structured_output`'s parameter names.
  - Prose calls to `search` and `recall` that left out the required `query_text`, and a parameter table missing six optional parameters.

  Under 9.0.0 (`925f195`, `f27f228`, `3380efd`): the lightweight runner's citation; the `add`, `cognify`, `search` and `update` parameter tables, which wrote unions with `/` such as `str / list[str] / None`, which an independent judge found the rules do not read as types, and descriptions such as `Union (many)` and `Pydantic BaseModel`, which the rules leave open ([#1003](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/1003)), now copy their declarations; and the `search` table's `node_name`, written `list[str]` where the source and both fenced forms write `list[str] | None`. After the runs with subagents (`bd2a419`, `5a6e2e2`, `80b9ba0`): the "optional `user`" phrase in four namespace rows, which was correct, is gone, because a reader took it as a partial form of each method ([#1034](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/1034)); and `remember`'s return is now the union the source declares, `RememberResult | DryRunEstimate | PresortReport | dict`, where a parenthetical named the other types ([#1042](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/1042)).

  Left open: three Medium stale-documentation gaps for `run_migrations`, `setup_logging` and `wait_for_background_tasks`, root exports whose files the brief scopes out (the docs are right, and each gap cites a passing mention, not the line that documents the name, [#1041](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/1041)), a metadata count (Medium) and the token budget (Low). → [test report](forge-data/oms-cognee/1.6.2/test-report-oms-cognee-20261108T144709Z-e7157ac9.md)
- **oms-storybook-react-vite** 10.3.5 — **100%**. Its brief's `scope.tier_a_include` names the story-authoring entry points (`storybook/test`, `preview-api`, `actions`, `theming`, `viewport`, `highlight`, `@storybook/react-vite`, `@storybook/react`, the addon-docs blocks, the a11y/themes/vitest addons, the builder-vite config helpers). Since 5.0.0, Export Coverage counts only the documented names in that set ([#792](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/792)), and the extractor reads the destructured and per-package names 4.0.0 missed ([#786](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/786), [#830](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/830)).

  Category scores:
  - Export Coverage: 370/370, against `stats.effective_denominator` 370, the size of the set this run read.
  - Signature Accuracy: 170/170, from 68 judges, one per source file. 155 of the 170 checks bind a form to the declaration its own citation names.
  - Type Coverage: 128/128. Under 7.0.0 it was 134/147 (98.23% overall): the run read `export type * from '@vitest/spy'` as 19 names, 13 of them undocumented. 8.0.0 and later count no name for a star from another package ([#926](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/926)).
  - External Validation: 100%.

  9.0.0 settles the call the 8.0.0 pass turned on: names the skill documents as two different exports, such as core's and React's `composeStories`, are no longer compared with each other ([#927](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/927)). The report records three calls the rules leave open. One decides the gate: `useThemeParameters`'s return, written `ThemesParameters['themes']`. Its source file imports the interface `ThemesParameters` (as `Parameters`) and also declares a local alias `ThemesParameters` over it. The judge read the documented name as the interface, a match; read as the local alias, it would be a Critical return mismatch ([#1050](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/1050)). The other two change no score: `Story`'s `?`-marked props list, graded Info because it is labelled partial, and the Key API Summary's "Purpose and key params" column, read as a partial label. The run's inventory reader matched an earlier run's set of names beyond the ones the test pins, so it drew on that run's output ([#1036](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/1036)).

  What the 7.0.0 rounds fixed (`e0415b5`, `9265cff`, `c71172d`, `bdc326f`, `fdb1a81`, `ac98bed`):
  - `afterEach`'s return type, the react-vite preset's `viteFinal` type and `useParameter`'s parameters, the last two tracked in [#17](https://github.com/armelhbobdad/oh-my-skills/issues/17).
  - Names documented under entry points that do not export them: `MockUniversalStore` and three store hooks, which `storybook/manager-api` exports only with the `experimental_` prefix; four CSF types listed under `storybook/internal/types`; `createTest` from `storybook/preview-api`; module file names listed as exports; and `ColorControlProps`.
  - Classes labeled as types, a `PreviewWeb` alias that is a subclass, and parameter forms that differed from the source's destructuring.
  - 134 tier A names the skill did not document, which took Export Coverage from 63.78% to 100%. `stats.effective_denominator` went from 280 to 370, the size of the tier A set.

  The skill did not change under 8.0.0. Under 9.0.0, after the first run with subagents (`fe2242b`): the two `actions` overloads that one cell wrote now each have a row, because the reader had joined them into one parameter list that matches neither ([#1043](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/1043)).

  Left open: 81 Medium stale-documentation gaps, none of them an error in the text. 75 are names the brief scopes out as tier C (internal subpaths such as `storybook/internal/components`); six are the `@vitest/spy` types the skill documents, which `storybook/test` passes on through an `export type *` that adds no name ([#1005](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/1005)). Also a metadata count (Medium). Under 4.0.0 we estimated the authored list by hand (391 names, [`tier-a-fuller-count.json`](forge-data/oms-storybook-react-vite/10.3.5/tier-a-fuller-count.json)); Skill Forge's own set replaces that estimate. → [test report](forge-data/oms-storybook-react-vite/10.3.5/test-report-oms-storybook-react-vite-20261108T143553Z-31d5d0c1.md)
- **oms-uitripled** 0.1.0 — **100%**. The 4.0.0 run was blocked by a false positive on `cn`. Since 7.0.0 the test keeps one record per declaring file and compares the declaration the skill cites, so it is gone.

  Category scores:
  - Export Coverage: 327/327, the stored count for the brief's `scope.include` union.
  - Signature Accuracy: 270/270, from 202 judges, one per source file.
  - Type Coverage: 42/42.
  - External Validation: 100%.

  The report records seven calls the rules leave open. Two would block read the other way: a `ThemeMode` cell written with its expansion, read as the alias (read as a type the source does not write, a Critical gap, [#1003](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/1003)); and three grid helpers, `GAP_VALUES`, `generateGridCode` and `initializeCells`, which `SKILL.md` groups with the Landing Builder helpers while `references/utils.md` says the Grid Generator and Background Builder use them, read as brief against detailed (read as a contradiction, a High split-body gap). The reference file is right: the source's grid generator, not the Landing Builder, uses them. We have not changed `SKILL.md` after this last test; [#21](https://github.com/armelhbobdad/oh-my-skills/issues/21) tracks it. Among the others: thirty-three `React.forwardRef<…>(…)` rows, compared as full forms; `badgeVariants({ variant })`, compared as a usage form; and eight unexported `*Props` types written as code spans, given no entry ([#1008](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/1008)). The run before it, without subagents, gave those eight spans entries, recorded as eight Info observations, and could not run the discovery test; those are the only differences between the two gap lists.

  What the 7.0.0 rounds fixed (`97951c3`, `bd2c805`, `2e6e9e7`, `2ca0ff8`):
  - The six errors [#17](https://github.com/armelhbobdad/oh-my-skills/issues/17) tracked: `HeroSection` import paths, `NativeHoverCardProps.size`, two pointers to entries that did not exist, three components with no reference row, and the `cn` and `UILibrary` descriptions.
  - Three motion components documented with the source's destructuring defaults on props their type requires.
  - The registry `Component`'s fields, a catalog claim that react-shadcn ships `NativeCounterUp`, and two completeness claims that left out `PasswordInput`, `AnimatedCheckbox`, a second `NativeLiquidButton` with different props and a copy of `NativeStartNow`.

  Under 9.0.0 (`af956ec`, `b0e0c99`, `1778b7e`): `generateUniqueSlug` is now documented with the `page` fallback it uses when a name sanitizes to an empty string, which the skill left out; a `GridCellType` code span, which the test read as a documented name though it is only an import alias, now quotes the import; and three prose calls are written as the source writes them, among them `setSelectedLibrary(library)`, whose parameter the skill had named `lib`.

  Left open: a false Medium stale-documentation gap on `UILibraryContextValue`, which the skill documents right ([#1006](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/1006), [#1007](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/1007)), a stale brief scope, two `scope.include` globs that match no file, and a metadata count (both Medium). → [test report](forge-data/oms-uitripled/0.1.0/test-report-oms-uitripled-20261108T115013Z-3e4fdad8.md)

Every older report stays in `forge-data/` next to the one that replaced it, the failing runs included: each round is a test report, fix commits and a re-test, in that order, in the git history. The reverted storybook repair's reports are in that history too (`35d506b`).

---

## The points we lost

**oms-cognee: 99%.** It loses one point to skill-check's 5,000-token budget for a `SKILL.md` body: its body is about 5,700 tokens. Under 7.0.0 and 8.0.0 it had no score: two false positives blocked it ([#918](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/918)). We could have dodged them by documenting the lightweight runner under another name, or by dropping one of its forms. We kept the documentation right and the block visible until Skill Forge 9.0.0 fixed the comparison.

**Why the numbers changed under 7.0.0.** Under 4.0.0 we published 100% for oms-cocoindex and 99% for oms-cognee; oms-storybook-react-vite and oms-uitripled were blocked. The first 7.0.0 tests, on the same skills:
- oms-cocoindex: PASS 100%.
- oms-uitripled: PASS 100%, its `cn` false positive gone.
- oms-cognee: blocked on 8 Critical and 1 High gaps: seven real errors and the two `run_pipeline` false positives.
- oms-storybook-react-vite: blocked on one real error, with Export Coverage at 63.78% of its 370 tier A names.

Two rounds of fixes followed for oms-cocoindex, oms-cognee and oms-uitripled, and three for oms-storybook-react-vite. In each round one agent fixed the errors by hand against the pinned source, and a strict test re-measured the result. A separate read-only agent reviewed each round's changes before its test, except the last one-row storybook fix (`ac98bed`), which went straight to its re-test. The rounds found real errors in all four skills, including in the two that passed: three cocoindex forms a strict judge would block on and the `@coco.fn` decorator forms that raise, and the three uitripled lines a later run blocked. Before that, under 4.0.0 and earlier, we published 100%, 99.00%, 100% and 95.17%. Three of those runs read the signature rules leniently; uitripled's 100% did not. Storybook's also rested on a stored count that credited every documented name. That history, and the 4.0.0 version of this page, are in the git history (`64a8681`).

**What changed under 8.0.0.** On the same skill text, oms-storybook-react-vite went from 98.23% to 100%, because 8.0.0 counts no name for an `export type *` from another package ([#926](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/926)), and oms-uitripled's three `...props` forms went from calls its report never wrote down to a written rule ([#932](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/932)), its score unchanged at 100%. The first 8.0.0 test of oms-cocoindex counted `ExceptionContext` as undocumented (99.37%), a reader's call the contract does not settle ([#967](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/967)); we documented it (`15cefa0`), the only change to a skill under 8.0.0, and the re-test passed at 100%. oms-cognee stayed blocked by the same two false positives.

**What changed under 9.0.0.** 9.0.0 binds each form to the declaration its own citation names, compares props tables and the usage forms a skill writes, and counts a name the skill writes only inside another export's type as undocumented. On the skills as they stood under 8.0.0, plus the `run_pipeline` citation (`925f195`), the first 9.0.0 tests passed all four: oms-cocoindex at 98.89% (`ExceptionHandler`), oms-cognee at 99%, oms-storybook-react-vite and oms-uitripled at 100%. An independent judge then re-read every call each run left open against the pinned source, and we fixed the lines it found wrong, or open to a reading that blocks, in three skills, re-testing after every fix. We also scoped cocoindex's brief to the files that define its root exports, so its count no longer rests on two globs that match nothing ([#1009](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/1009)). Apart from cocoindex's `ExceptionHandler`, which took it from 98.89% back to 100%, no score moved; what the fixes changed is how many of the passes rest on a judge's call.

Those runs had no subagents, as [How the score is computed](#how-the-score-is-computed) says. Re-run with them, oms-cocoindex and oms-uitripled passed at 100% again, oms-cocoindex after one more fix to two `Settings` lines (`92c8bad`). On the same files, oms-cognee and oms-storybook-react-vite were blocked, each by a reading of correct text ([#1034](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/1034), [#1043](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/1043)). We rewrote those lines, and two more that a pass with subagents rested on (oms-cocoindex's removed `Settings` call, [#1038](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/1038); oms-cognee's `remember` return, [#1042](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/1042)), so that each says the same thing in a form the rules read one way, and re-tested each skill with subagents. One rewrite broke a table row; the next test caught it, and we fixed it (`80b9ba0`). We stopped there: each published report is the last run of its skill, and the calls a pass still rests on are listed above.

The Skill Forge defects these runs ran into are filed upstream: [#912](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/912) to [#932](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/932) from the 7.0.0 runs and [#965](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/965) to [#973](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/973) from the 8.0.0 runs, all closed by 9.0.0, and [#998](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/998) to [#1021](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/1021) and [#1034](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/1034) to [#1050](https://github.com/armelhbobdad/bmad-module-skill-forge/issues/1050) from the 9.0.0 runs.

We didn't hide the rough edges. We wrote them down. Read them yourself, starting with the reports for the versions that ship:
- [`oms-cocoindex`](forge-data/oms-cocoindex/1.0.0/test-report-oms-cocoindex-20261108T135352Z-27b92a60.md)
- [`oms-cognee`](forge-data/oms-cognee/1.6.2/test-report-oms-cognee-20261108T144709Z-e7157ac9.md)
- [`oms-storybook-react-vite`](forge-data/oms-storybook-react-vite/10.3.5/test-report-oms-storybook-react-vite-20261108T143553Z-31d5d0c1.md)
- [`oms-uitripled`](forge-data/oms-uitripled/0.1.0/test-report-oms-uitripled-20261108T115013Z-3e4fdad8.md)

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
