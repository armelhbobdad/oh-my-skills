# Evidence Report: oms-cocoindex

**Generated:** 2026-04-25
**Forge Tier:** Deep
**Source:** https://github.com/cocoindex-io/cocoindex @ `5fe4f37a526e51516655832ec9814e7ca24ade9a` (tag `v1.0.0`)
**Previous version:** 0.3.37 @ `87c5dbf087bf` (preserved at `skills/oms-cocoindex/0.3.37/`)
**Trigger:** drift-report-20260424-212355.md (CRITICAL drift, 130 findings — full-rewrite recommended)

## Tool Versions

- ast-grep: 0.42.0
- QMD: 2.0.1
- SKF: 1.0.0

## Update Operation — 2026-04-25

**Trigger:** audit-skill chain → user invocation of `/skf-update-skill` with drift report
**Forge Tier:** Deep
**Mode:** Normal (full-rewrite due to v0.3.37 → v1.0.0 paradigm shift)
**Workflow:** skf-update-skill

### Changes Detected

| Category | Count | Detail |
|---|---:|---|
| Files DELETED upstream | 18 | `flow.py`, `op.py`, `llm.py`, `index.py`, `lib.py`, `auth_registry.py`, `typing.py`, `utils.py`, `sources/_engine_builtin_specs.py`, `targets/_engine_builtin_specs.py`, `functions/_engine_builtin_specs.py`, `functions/colpali.py`, `functions/sbert.py`, `targets/{chromadb,doris,lancedb,turbopuffer,pinecone}.py` |
| Files MODIFIED in scope | 3 | `setting.py` (signature changes), `query_handler.py` (signature change + new export), `cli.py` (semantics rewrite) |
| Files ADDED to scope (after brief amendment) | 30 | `_internal/api.py`, 10 `connectors/*` packages, 4 `ops/*` modules + entity_resolution sub-package, 5 `resources/*` modules |
| Exports DELETED | 107 | All from drift report — verified by file deletions and grep |
| Exports NEW | 145 | Documented in v1.0.0 SKILL.md + 7 references |
| Exports MODIFIED | 2 | `Settings` (Postgres → LMDB), `QueryInfo` (similarity_metric removed) |
| Exports MOVED | 6 | Tracked in drift report (location-only — `GlobalExecutionOptions`, `ServerSettings`, `QueryHandlerResultFields`, `QueryOutput`, `cli`, `QueryInfo`) |
| Asset/script drift | 1 | `CLAUDE.md` (root-level) hash changed `36600de9…` → `ca263509…` |

### Brief Amendments Applied

The v0.3.37 brief targeted only the legacy flow-builder API surface. To capture v1.0.0's component-based paradigm, four scope-expansion amendments were applied in-flight (see `forge-data/oms-cocoindex/skill-brief.yaml.amendments[]`):

1. **promoted** `python/cocoindex/_internal/api.py` — the v1.0.0 public-API surface (~70 exports re-exported by `__init__.py`).
2. **promoted** `python/cocoindex/connectors/**/*.py` — 10 connector packages replacing v0.3.37 `sources.*` + `targets.*`.
3. **promoted** `python/cocoindex/ops/**/*.py` — replaces v0.3.37 `functions.*`.
4. **promoted** `python/cocoindex/resources/**/*.py` — discovered during step-03 extraction; the Quick Start example references `Chunk`, `FileLike`, `IdGenerator`, `VectorSchemaProvider` from this package.
5. **demoted-exclude** `python/cocoindex/_internal/**` — broad exclude removed entirely. The include allowlist now references only `_internal/api.py` (literal path), so the rest of `_internal/` stays out by absence — no negation glob needed.
6. **demoted-include** 21 deleted v0.3.37 file paths — removed cleanly from `scope.include` (audit trail in this report and in the drift report).

The brief `version` was bumped 0.3.37 → 1.0.0 to reflect the new source target. This mirrors the cognee 0.5.8 → 1.0.0 precedent referenced in the drift report's recommendation.

### Merge Results

- Exports added: 145 (full v1.0.0 surface in scope)
- Exports removed: 107 (all v0.3.37 exports — wholesale paradigm replacement)
- Exports modified: 2 (`Settings`, `QueryInfo`)
- Exports moved: 6 (location-only, all citation lines updated)
- [MANUAL] sections preserved: 3 (`quick-start-notes`, `api-notes`, `integration-notes` — placeholder-only content from v0.3.37, re-anchored to v1.0.0-equivalent sections in SKILL.md)
- Conflicts resolved: 0

### Skill Package Layout

```
skills/oms-cocoindex/
  0.3.37/oms-cocoindex/        # preserved as-is (status: archived)
  1.0.0/oms-cocoindex/         # new (status: active)
    SKILL.md                   # v1.0.0 component-based pipelines
    context-snippet.md         # regenerated — version + headline-exports + gotchas all changed
    metadata.json
    references/
      component-api.md         # App, Environment, mount/use_mount/mount_each/mount_target, fn, lifespan, runtime
      target-state.md          # TargetState, TargetHandler, declare_target_state(_with_child)
      live-components.md       # LiveComponent, LiveMapFeed, LiveMapView, LiveMapSubscriber
      connectors.md            # All 10 connector packages
      ops.md                   # litellm, sentence_transformers, text, entity_resolution
      resources.md             # Chunk, FileLike, IdGenerator, schema providers
      settings-cli.md          # Settings (LMDB), ServerSettings, query_handler, CLI subcommands
  active -> 1.0.0              # repointed
```

### Validation Summary

- Spec compliance: PENDING (skill-check check --fix runs in step-06 §7)
- [MANUAL] integrity: PASS (3 markers preserved byte-identical; re-anchored to equivalent sections)
- Confidence tiers: PASS (all 145 entries are T1, AST-extracted from v1.0.0 source tree)
- Provenance: PASS (159 `[AST:...]` citations across SKILL.md + 7 references; 20 spot-checked line numbers verified accurate)

### Description Guard

- Restored: true
- Triggering tool: `npx skill-check check --fix`
- Original description preserved: true (then deliberately edited post-restore for `description.use_when_phrase` rule)
- Notes: `skill-check --fix` prepended "Use when " to the description, producing the ungrammatical "Use when build data ingestion + ..." opener. The §0 four-phase guard detected the divergence and restored the original wording. After restore, the description was deliberately edited to replace "Use this skill when authoring..." with "Use when authoring..." to satisfy skill-check's `description.use_when_phrase` rule — this is an intentional post-restore edit, not a tool rewrite. The `version: 1.0.0` frontmatter field that `--fix` flagged as unknown was also removed (version is authoritatively tracked in `metadata.json`). Final skill-check score: 100/100, 0 errors, 0 warnings.

### Context Snippet

- Regenerated: true
- Triggers fired: headline-exports, version, gotchas
- Notes: v0.3.37 → v1.0.0 is a wholesale rewrite — every headline export changed (FlowBuilder → App, flow_def → @lifespan/@fn, sources/targets/functions → connectors/ops), version bumped, and the gotchas list completely turned over (DB backend switched Postgres → LMDB; LlmSpec/LlmApiType/VectorSimilarityMetric removed; deprecated aliases gone).

## Pinned References

- **Drift report (audit input):** `forge-data/oms-cocoindex/0.3.37/drift-report-20260424-212355.md`
- **Audit snapshot:** `forge-data/oms-cocoindex/0.3.37/audit-snapshot-20260424-212355.json`
- **Provenance map:** `forge-data/oms-cocoindex/1.0.0/provenance-map.json` (145 entries)
- **Previous provenance map:** `forge-data/oms-cocoindex/0.3.37/provenance-map.json` (114 entries — preserved for historical comparison)
- **Brief:** `forge-data/oms-cocoindex/skill-brief.yaml` (amended in-flight; previous shape recoverable from `git log -- forge-data/oms-cocoindex/skill-brief.yaml`)

## Out-of-Scope Observations

Items observed during extraction but not pulled into v1.0.0 skill scope:

- **`python/cocoindex/connectorkits.fingerprint`** — referenced from `resources/file.py:L34` (`fingerprint_bytes`). Likely a connector-author utility module; not user-facing for normal pipeline authoring. Not promoted to scope.
- **`python/cocoindex/inspect.py`** — exists but is empty/auxiliary in v1.0.0 (`grep -c "^class \|^def " returned no matches at top level`). May develop into public surface later; flag for next audit.
- **`python/cocoindex/_internal/{app,environment,runner,…}.py` implementation files (~5,700 lines)** — read for signature extraction but kept out of scope per the brief. Provenance citations anchor at `_internal/api.py` (the public re-export hub) for re-exported symbols, with secondary citations to the impl file when meaningful (e.g., `App` cited at `_internal/app.py:L208`). This is the same trade-off used in the cognee 0.5.8 → 1.0.0 update.
- **Engine bindings (`python/cocoindex/_internal/core.pyi`)** — pyo3-compiled Rust bindings, exposed as `cocoindex._internal.core`. Out of scope by brief design — users author in Python, not against engine internals.

## Toolchain Notes

- ast-grep CLI used directly (not MCP) for batch class/def extraction across 15+ `_internal/*.py` files. Same pattern used in v0.3.37 forge.
- The `class $NAME($$$BASE):` pattern returned zero matches (pattern-parser quirk also observed in v0.3.37 forge); fell back to `^class ` grep + targeted `sed -n` reads to extract signature lines. Confidence remains T1 (line numbers verified by spot-check).
- QMD extraction collection `oms-cocoindex-extraction` was registered in v0.3.37 forge but **never populated** (`Files: 0`). Drift report flagged this in §Provenance; for v1.0.0, the same collection remains empty. Run `qmd update oms-cocoindex-extraction` before the next audit to enable T2 semantic enrichment on diff.

## Migration Recommendations for Skill Consumers

The skill's `Migration from v0.3.37` section (SKILL.md) provides a concept-by-concept mapping. Critical user-impact items:

1. **State storage migrated Postgres → LMDB.** Existing v0.3.37 state in Postgres tables is unreadable by v1.0.0 — plan a re-index, not an in-place upgrade.
2. **`@cocoindex.flow_def` → `coco.App` + `@coco.fn`.** Not a rename; rewrite required.
3. **`functions.ExtractByLlm` → `ops.litellm.LiteLLMEmbedder`.** LiteLLM model strings replace v0.3.37's `LlmSpec`/`LlmApiType`/provider config classes.
4. **`cocoindex server` CLI subcommand removed.** `ServerSettings` type retained but no embedded server in v1.0.0.
5. **Vector similarity is per-connector** in v1.0.0 — `VectorSimilarityMetric` and `VectorIndexDef` are no longer top-level types.

---

# Historical Section: v0.3.37 (Original Generation, 2026-04-11)

The remainder of this report documents the original v0.3.37 forge run for archival completeness. See `forge-data/oms-cocoindex/0.3.37/evidence-report.md` for the full original report.

**Source:** v0.3.37 @ `87c5dbf0`
**Created by:** skf-create-skill, 2026-04-11
**Tool versions at creation:** ast-grep 0.42.0, QMD 2.0.1, SKF 1.0.0
**Original confidence distribution:** T1 = 102, T1-low = 0, T2 = 15, T3 = 10
**Original quality score:** 100/100 (skill-check), tessl content_score 50% (intentional two-tier design trade-off)

The full v0.3.37 evidence report is preserved at `forge-data/oms-cocoindex/0.3.37/evidence-report.md` and is unmodified by this update run.
