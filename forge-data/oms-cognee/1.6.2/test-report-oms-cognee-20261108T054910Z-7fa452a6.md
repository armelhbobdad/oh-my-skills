---
workflowType: 'test-skill'
skillName: 'oms-cognee'
skillDir: 'skills/oms-cognee/1.6.2/oms-cognee'
runId: '20261108T054910Z-7fa452a6'
testMode: 'naive'
forgeTier: 'Deep'
hardGate: 'passed'
testResult: 'pass'
score: '99%'
threshold: '80%'
thresholdSource: 'workflow default (80%)'
analysisConfidence: 'full'
toolingStatus: 'ok'
workspaceDrift: 'ok'
health_check_dispatched: true
testDate: '2026-11-08T05:49:10Z'
stepsCompleted: ['init', 'detect-mode', 'coverage-check', 'coherence-check', 'external-validators', 'hard-gate', 'score', 'report']
nextWorkflow: 'export-skill'
---

# Test Report: oms-cognee

<!--
Each stage writes its section in place of the heading below that it owns and
the placeholder comment under that heading, so every heading occurs once.
Before the result files are written, report.md §4c checks that each heading
occurs exactly once, that no placeholder comment is left and that the title
above names the skill (init.md §6c fills it): a stage that skipped its
section stops the run there. Do not change the title line, and do not
reorder or delete the headings or their placeholder comments.

Heading / owning step:
  Test Summary        → detect-mode §2
  Coverage Analysis   → coverage-check §5
  Coherence Analysis  → coherence-check §6
  External Validation → external-validators §5
  (hard gate)         → step-hard-gate reads the gap ledger; it writes the
                        Completeness Score section only when it blocks the run
  Completeness Score  → score §6, or step-hard-gate §3 on a blocked run
  Gap Report          → report §4c, rendered from the gap ledger (with the
                        Discovery Quality subsection)
-->

## Test Summary

**Skill:** oms-cognee
**Test Mode:** naive
**Forge Tier:** Deep

**Mode Rationale:** metadata.json records `skill_type: "single"`, an individual library skill, so the run tests it in naive mode: API-surface coverage, with structural-only coherence and no coherence category in the score.

**Analysis Plan:**
- Coverage Check: every public export of cognee v1.6.2 (`cognee/__init__.py` at the pinned commit ba3631f) against SKILL.md and its references, with Deep-tier AST-backed signature and type checks of each documented form against its source declaration.
- Coherence Check: structural checks only (internal references resolve, sections present, migration section rules), no cross-skill integration scoring.

## Coverage Analysis

**Tier:** Deep
**Source Access:** full
**Source Path:** /home/armel/.skf/workspace/repos/github.com/topoteretes/cognee
**Workspace Layout:** single package
**Denominator:** barrel

**Files Analyzed:** 53

### Export Coverage

| Export | Type | Documented | Signature | Source Location | Status |
|--------|------|------------|-----------|-----------------|--------|
| `BoundTask` | - | yes | - | - | WARN |
| `COGXArchiveSource` | class | yes | yes | cognee/modules/migration/sources/cogx_archive.py:19 | PASS |
| `COGXDocument` | class | yes | yes | cognee/modules/migration/cogx.py:78 | PASS |
| `COGXEntity` | class | yes | yes | cognee/modules/migration/cogx.py:101 | PASS |
| `COGXEpisode` | class | yes | yes | cognee/modules/migration/cogx.py:93 | PASS |
| `COGXFact` | class | yes | yes | cognee/modules/migration/cogx.py:112 | PASS |
| `COGXManifest` | class | yes | yes | cognee/modules/migration/cogx.py:180 | PASS |
| `COGXMemory` | class | yes | yes | cognee/modules/migration/cogx.py:131 | PASS |
| `COGXMemoryBlock` | class | yes | yes | cognee/modules/migration/cogx.py:139 | PASS |
| `COGXRawNode` | class | yes | yes | cognee/modules/migration/cogx.py:148 | PASS |
| `COGXRecord` | - | yes | - | cognee/modules/migration/cogx.py:160 | PASS |
| `COGXScope` | class | yes | yes | cognee/modules/migration/cogx.py:60 | PASS |
| `COGXTurn` | class | yes | yes | cognee/modules/migration/cogx.py:87 | PASS |
| `COGX_VERSION` | - | yes | - | cognee/modules/migration/cogx.py:22 | PASS |
| `CogneeApiError` | - | yes | - | - | WARN |
| `CogneeConfigurationError` | - | yes | - | - | WARN |
| `CogneeSystemError` | - | yes | - | - | WARN |
| `CogneeTransientError` | - | yes | - | - | WARN |
| `CogneeValidationError` | - | yes | - | - | WARN |
| `DataPoint` | - | yes | - | - | WARN |
| `Drop` | - | yes | - | cognee/pipelines/types.py:32 | PASS |
| `EXPORT_FORMATS` | - | yes | - | cognee/modules/migration/export.py:35 | PASS |
| `Edge` | - | yes | - | - | WARN |
| `EntitySpec` | - | yes | - | - | WARN |
| `ExportResult` | class | yes | yes | cognee/modules/migration/export.py:41 | PASS |
| `FeedbackEntry` | class | yes | - | cognee/memory/entries.py:62 | PASS |
| `FromIdentity` | - | yes | - | - | WARN |
| `GraphEdge` | class | yes | yes | cognee/modules/migration/snapshot.py:152 | PASS |
| `GraphSchemaSpec` | - | yes | - | - | WARN |
| `GraphSnapshot` | class | yes | yes | cognee/modules/migration/snapshot.py:161 | PASS |
| `GraphitiSource` | class | yes | yes | cognee/modules/migration/sources/zep.py:136 | PASS |
| `IMPORT_MODES` | - | yes | - | cognee/modules/migration/sources/base.py:19 | PASS |
| `LettaSource` | class | yes | yes | cognee/modules/migration/sources/letta.py:72 | PASS |
| `Mem0Source` | class | yes | yes | cognee/modules/migration/sources/mem0.py:26 | PASS |
| `MemoryEntry` | - | yes | - | cognee/memory/entries.py:129 | PASS |
| `MemorySource` | class | yes | yes | cognee/modules/migration/sources/base.py:36 | PASS |
| `PipelineRunCompleted` | - | yes | - | - | WARN |
| `PipelineRunErrored` | - | yes | - | - | WARN |
| `PipelineRunInfo` | - | yes | - | - | WARN |
| `PipelineRunStarted` | - | yes | - | - | WARN |
| `PushResult` | class | yes | yes | cognee/api/v1/push/push.py:26 | PASS |
| `QAEntry` | class | yes | - | cognee/memory/entries.py:24 | PASS |
| `REMEDIATION_MARKER` | - | yes | - | - | WARN |
| `RememberResult` | class | yes | - | cognee/api/v1/remember/remember.py:600 | PASS |
| `SearchType` | class | yes | - | cognee/modules/search/types/SearchType.py:4 | PASS |
| `SessionModelUsage` | class | yes | - | cognee/modules/session_lifecycle/models.py:96 | PASS |
| `SessionRecord` | class | yes | - | cognee/modules/session_lifecycle/models.py:10 | PASS |
| `Task` | class | yes | yes | cognee/modules/pipelines/tasks/task.py:188 | PASS |
| `TaskSpec` | - | yes | - | - | WARN |
| `TraceEntry` | class | yes | - | cognee/memory/entries.py:40 | PASS |
| `UpdateResult` | - | yes | - | - | WARN |
| `ValidationIssue` | class | yes | yes | cognee/api/v1/validate/validate.py:99 | PASS |
| `ValidationReport` | class | yes | yes | cognee/api/v1/validate/validate.py:105 | PASS |
| `ValidationStatus` | class | yes | - | cognee/api/v1/validate/validate.py:93 | PASS |
| `ZepSource` | class | yes | yes | cognee/modules/migration/sources/zep.py:57 | PASS |
| `__version__` | - | yes | - | - | WARN |
| `add` | function | yes | yes | cognee/api/v1/add/add.py:39 | PASS |
| `add_data_points` | - | yes | - | - | WARN |
| `agent_memory` | function | yes | yes | cognee/modules/agent_memory/decorator.py:29 | PASS |
| `agents` | class | yes | - | cognee/api/v1/agents/agents.py:40 | PASS |
| `apply_write_proposal` | function | yes | yes | cognee/api/v1/tools/tools.py:129 | PASS |
| `build_snapshot` | function | yes | yes | cognee/modules/migration/snapshot.py:243 | PASS |
| `clear_traces` | function | yes | yes | cognee/modules/observability/trace_context.py:121 | PASS |
| `cognee_network_visualization` | function | yes | yes | cognee/modules/visualization/cognee_network_visualization.py:154 | PASS |
| `cognify` | function | yes | yes | cognee/api/v1/cognify/cognify.py:110 | PASS |
| `config` | class | yes | - | cognee/api/v1/config/config.py:171 | PASS |
| `datapoint_registry` | function | yes | yes | cognee/modules/migration/snapshot.py:39 | PASS |
| `datasets` | class | yes | - | cognee/api/v1/datasets/datasets.py:105 | PASS |
| `delete` | function | yes | yes | cognee/api/v1/delete/__init__.py:12 | PASS |
| `disable_tracing` | function | yes | yes | cognee/modules/observability/trace_context.py:43 | PASS |
| `disconnect` | function | yes | yes | cognee/api/v1/serve/disconnect.py:8 | PASS |
| `enable_tracing` | function | yes | yes | cognee/modules/observability/trace_context.py:18 | PASS |
| `export` | function | yes | yes | cognee/api/v1/export/export.py:16 | PASS |
| `export_dataset` | function | yes | yes | cognee/modules/migration/export.py:198 | PASS |
| `find_remediation` | - | yes | - | - | WARN |
| `forget` | function | yes | yes | cognee/api/v1/forget/forget.py:22 | PASS |
| `get_all_traces` | function | yes | yes | cognee/modules/observability/trace_context.py:112 | PASS |
| `get_cognee_version` | function | yes | yes | cognee/version.py:7 | PASS |
| `get_default_tasks` | - | yes | - | - | WARN |
| `get_errored_run_info` | - | yes | - | - | WARN |
| `get_last_trace` | function | yes | yes | cognee/modules/observability/trace_context.py:101 | PASS |
| `get_memory_provenance_graph` | function | yes | yes | cognee/api/v1/visualize/memory_provenance.py:645 | PASS |
| `get_schema_inventory` | function | yes | yes | cognee/api/v1/visualize/get_schema_inventory.py:77 | PASS |
| `graph_model_from_spec` | - | yes | - | - | WARN |
| `graph_spec_to_json_schema` | - | yes | - | - | WARN |
| `improve` | function | yes | yes | cognee/api/v1/improve/improve.py:101 | PASS |
| `is_tracing_enabled` | - | yes | - | - | WARN |
| `list_sql_connections` | function | yes | yes | cognee/api/v1/tools/tools.py:65 | PASS |
| `list_write_proposals` | function | yes | yes | cognee/api/v1/tools/tools.py:119 | PASS |
| `logger` | - | yes | - | cognee/__init__.py:34 | PASS |
| `memify` | function | yes | yes | cognee/modules/memify/memify.py:27 | PASS |
| `pipeline_needs_llm` | - | yes | - | - | WARN |
| `pipelines` | - | yes | - | - | WARN |
| `propose_corrections` | function | yes | yes | cognee/api/v1/tools/tools.py:101 | PASS |
| `propose_sql_write` | function | yes | yes | cognee/api/v1/tools/tools.py:81 | PASS |
| `prune` | class | yes | - | cognee/api/v1/prune/prune.py:5 | PASS |
| `push` | function | yes | yes | cognee/api/v1/push/push.py:96 | PASS |
| `read_archive` | function | yes | yes | cognee/modules/migration/cogx.py:322 | PASS |
| `read_manifest` | function | yes | yes | cognee/modules/migration/cogx.py:276 | PASS |
| `recall` | function | yes | yes | cognee/api/v1/recall/recall.py:347 | PASS |
| `register_sql_connection` | function | yes | yes | cognee/api/v1/tools/tools.py:27 | PASS |
| `rehydrate_node` | function | yes | yes | cognee/modules/migration/snapshot.py:116 | PASS |
| `reject_write_proposal` | function | yes | yes | cognee/api/v1/tools/tools.py:146 | PASS |
| `remediation_for` | - | yes | - | - | WARN |
| `remember` | function | yes | yes | cognee/api/v1/remember/remember.py:867 | PASS |
| `remove_sql_connection` | function | yes | yes | cognee/api/v1/tools/tools.py:73 | PASS |
| `report` | function | yes | yes | cognee/api/v1/report/report.py:13 | PASS |
| `run_custom_pipeline` | function | yes | yes | cognee/modules/run_custom_pipeline/run_custom_pipeline.py:14 | PASS |
| `run_migrations` | - | yes | - | - | WARN |
| `run_pipeline` | function | yes | yes | cognee/modules/pipelines/operations/pipeline.py:53 | PASS |
| `run_relational_migrations` | - | yes | - | - | WARN |
| `run_tasks` | function | yes | yes | cognee/modules/pipelines/operations/run_tasks.py:39 | PASS |
| `run_tasks_parallel` | function | yes | yes (Info) | cognee/modules/pipelines/operations/run_parallel.py:8 | WARN |
| `search` | function | yes | yes | cognee/api/v1/search/search.py:41 | PASS |
| `serve` | function | yes | yes | cognee/api/v1/serve/serve.py:17 | PASS |
| `session` | - | yes | - | cognee/api/v1/session/__init__.py:8 | PASS |
| `setup` | - | yes | - | - | WARN |
| `start_ui` | function | yes | yes | cognee/api/v1/ui/ui.py:514 | PASS |
| `start_visualization_server` | - | yes | - | - | WARN |
| `task` | - | yes | - | - | WARN |
| `task_summary` | - | yes | - | - | WARN |
| `tools` | - | yes | - | - | WARN |
| `update` | function | yes | yes | cognee/api/v1/update/update.py:28 | PASS |
| `validate` | function | yes | yes | cognee/api/v1/validate/validate.py:198 | PASS |
| `visualization_server` | function | yes | yes | cognee/api/v1/visualize/start_visualization_server.py:6 | PASS |
| `visualize` | function | yes | yes | cognee/api/v1/visualize/visualize.py:193 | PASS |
| `visualize_graph` | function | yes | yes | cognee/api/v1/visualize/visualize.py:193 | PASS |
| `visualize_graph_json` | - | yes | - | - | WARN |
| `visualize_memory_provenance` | function | yes | yes | cognee/api/v1/visualize/memory_provenance.py:848 | PASS |
| `visualize_multi_user_graph` | - | yes | - | - | WARN |
| `visualize_semantic_json` | - | yes | - | - | WARN |

### Coverage Summary

- **Exports Found:** 92
- **Documented:** 92 (100%)
- **Missing Documentation:** 0
- **Signature Mismatches:** 0, plus 2 graded Low or Info and counted as matching
- **Stale Documentation:** 39, documented extras included
- **Scoped Out by the Brief:** `describe_resolution` (cognee/shared/env_file.py:127), `load_env_file` (cognee/shared/env_file.py:112), `run_migrations` (cognee/run_migrations.py:18), `setup_logging` (cognee/shared/logging_utils.py:345), `start_visualization_server` (cognee/shared/utils.py:481), `wait_for_background_tasks` (cognee/infrastructure/background_tasks.py:66)
- **Nested Entry Points:** `cognee/api/v1/api_keys/routers/__init__.py` inside `cognee/__init__.py`: `get_api_key_management_router`; `cognee/api/v1/cloud/routers/__init__.py` inside `cognee/__init__.py`: `get_checks_router`; `cognee/api/v1/permissions/routers/__init__.py` inside `cognee/__init__.py`: `get_permissions_router`; `cognee/api/v1/settings/routers/__init__.py` inside `cognee/__init__.py`: `get_settings_router`

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 100% |
| Signature Accuracy | 100% |
| Type Coverage | 100% |

**Notes:**

- **Inventory (§1, §1a):** this session has no subagent tool, so the main thread read SKILL.md and all four `references/*.md` files (SKILL.md has no `## Full` headings) and built the inventory itself from `inventory-contract.md` and `inventory-floor.json`, then judged every signature by `signature-comparison-rules.md` loaded verbatim, the same text for the §1b cross-check and every §2 check. `validate-inventory.py`: valid, 257 entries, 0 violations, 0 warnings, so no form was left unbound for want of a place (`at`); the floor's 47 names (all table rows; the 8 `cognee.tools` rows with a Signature cell) are all kept with their pinned signatures; spot-check sample `BoundTask`, `distill_session`, `visualize_semantic_json`, none absent; `crossChecked` 97 names.
- **Split-body cross-check (§1b):** 0 `cross_check_mismatches`. Every export documented in two or more files was compared (body against each reference, and references against each other where the body agrees with both): `add`, `cognify`, `search`, `update` (fenced forms and the `| Param | Type | Default |` tables of references/core-workflow.md), `memify`, `run_custom_pipeline`, `visualize_graph`, `cognee_network_visualization`, `get_schema_inventory`, `get_memory_provenance_graph`, `visualize_memory_provenance`, `export`, `push`, `validate`, `report`, `get_cognee_version`, `run_migrations`, `Task`, `run_pipeline` (two declarations: the orchestrator forms and the lightweight-runner forms cite different files and import paths, so each set was compared only within itself), `run_tasks`, `run_tasks_parallel`, `Drop` and the namespace members of `datasets`, `prune`, `config`, `agents` and `session`.
- **Extraction (§2):** complete (`fallback.needed` false), 255 files in scope, no file read by eye and none unread, no `export *` from another package. `extractionGaps` (on the surface, read by eye at their line): `COGXRecord`, `COGX_VERSION`, `Drop`, `EXPORT_FORMATS`, `IMPORT_MODES`, `MemoryEntry`, `logger`, `session`, all constants or type aliases for which the skill writes no signature form, so nothing was compared for them.
- **Signatures (§2, §2b):** 72 checks over 39 source files, every one with a `bound` list but `update` and the five tracing functions (their forms carry no own citation that names one declaration, so each was compared with the check's declaration). Every binding names the declaration the form documents: the lightweight `run_pipeline` forms (references/full-api-reference.md:264, references/pipelines-and-datapoints.md:208 and :227) are bound to `cognee/modules/pipelines/operations/run_pipeline.py:37` (an `otherDeclarations` record) and the orchestrator forms to `cognee/modules/pipelines/operations/pipeline.py:53`; `export` form 0 is bound to the first `@overload` at `cognee/api/v1/export/export.py:16` and read through the implementation at line 49. Result: 0 Critical mismatches; `run_tasks_parallel` forms 0 and 1 (`-> Task`) are `annotation-contradicted` against `-> Callable[[Any], Generator[Any, Any, Any]]` (`cognee/modules/pipelines/operations/run_parallel.py:8`; the body returns `Task(parallel_run)` at line 15), graded Info. `score-signatures.py` warnings: none.
- **Numerator ground truth (§2b):** skipped (`stats.exports_documented` 86 is not the denominator 92).
- **Stale names (§2c):** 39 documented names outside the enumerated surface; `classify-stale` marked none fabricated. Modules and namespaces the skill documents by name (`pipelines`, `tools`, `start_visualization_server`), `__version__`, the scoped-out `run_migrations`, and helpers the skill documents with their import path (`cognee.low_level`, `cognee.exceptions`, `cognee.modules.pipelines.tasks.task`, `cognee.api.v1.visualize`, `cognee.api.v1.update`, ...).
- **Metadata counts (§4b):** `stats.exports_public_api` 102 against `exports[].length` 86 (16% drift, a Medium `metadata-drift` gap) and barrel 102 against documented 86 (an Info `multi-denominator` gap).
- **Provenance line check (§4c):** pass, 86 entries checked, 0 stale (3 line checks skipped by the helper).
- **Deep tier hand check:** every import path the skill names that was spot-checked (`cognee.low_level`, `cognee.api.v1.visualize`, `cognee.api.v1.update`, `cognee.api.v1.remember`, `cognee.api.v1.improve`, `cognee.memory`, `cognee.run_migrations`, `cognee.modules.observability`, `cognee.exceptions`, `cognee.pipelines`, `cognee.modules.pipelines`, `cognee.infrastructure.engine`, `cognee.infrastructure.databases.vector`, `cognee.tasks.storage`, `cognee.api.v1.session`) exports the names it is cited for, and the documented members of `QAEntry`, `TraceEntry`, `FeedbackEntry`, `SessionRecord`, `SessionModelUsage`, `ValidationIssue`, `ValidationReport`, `PipelineRunInfo` and its subclasses, and `RememberResult` match their declarations: no `Not checked by script` observation.

#### Coverage Notes: borderline calls

Each call below is one the rules leave open; the run counted it as stated, and this report records it (in_report: yes).

| # | Export | Documented form (file:line) | Source declaration | Sentence that left it open | Counted as |
|---|--------|-----------------------------|--------------------|----------------------------|------------|
| 1 | `export` | SKILL.md:173 `dataset="main_dataset", format="pydantic", ...` (both optional) against the second `@overload` stub at references/full-api-reference.md:438 (`dataset: str \| UUID, format: Literal[...]`, both required) | `cognee/api/v1/export/export.py:16`, `:27`, `:38` (`@overload`) and `:49` (implementation) | signature-comparison-rules.md, Overload sets: "A declaration opening an overload set ... is read through its implementation: a documented signature matching the implementation or any overload is no mismatch" speaks of source declarations; the split-body paragraph does not say whether a reference's documented overload stubs are read through its documented implementation | No split-body mismatch: the body agrees with the reference's implementation form (references/full-api-reference.md:443) and its first stub |
| 2 | `export` | SKILL.md:173 return `GraphSnapshot for "pydantic", ExportResult for "cogx"/"json"/"graphml"/"cypher"` | `-> ExportResult \| GraphSnapshot` (`cognee/api/v1/export/export.py:56`) | Annotations: "a description followed by a type (`HTML str`) each state one" and "a documented return type must cover every member the source can return" do not say how a per-argument prose return is read against a union | Match: it names both members |
| 3 | `get_schema_inventory` | SKILL.md:178 return `list of {type, count, samples, sample_size, relationships} dicts` | `-> list[dict[str, Any]]` (`cognee/api/v1/visualize/get_schema_inventory.py:81`) | Annotations: a description that states a type is not given a reading rule beyond `HTML str` | Match: read as `list[dict]`, whose type arguments the form leaves out |
| 4 | `remember` | SKILL.md:156 return `RememberResult (DryRunEstimate with dry_run=True, PresortReport with dry_run="presort", or dict)` | `-> Union["RememberResult", "DryRunEstimate", "PresortReport", dict]` (`cognee/api/v1/remember/remember.py:893`) | as row 2 | Match: it names all four members |
| 5 | `add`, `cognify`, `search`, `update` | the four `\| Param \| Type \| Default \| ... \|` tables, read at references/core-workflow.md:23, :117, :225 and :340 (their headings), including the rows the fix commit changed (`node_name` at :276, `preferred_loaders` at :62) | `cognee/api/v1/add/add.py:39`, `cognee/api/v1/cognify/cognify.py:110`, `cognee/api/v1/search/search.py:41`, `cognee/api/v1/update/update.py:28` | inventory-contract.md: "A table that documents one export's props, a row per prop with its type (Create Skill's `\| Prop \| Type \| Default \| Description \|`, or one with a Required column), is a place of its own" names props, not a function's parameters | Each table read as a place of its own (an object type of its rows, no optionality) and compared in §1b and §2: all four match their fenced forms and their declarations |
| 6 | `improve`, `serve`, `recall`, `export`, `cognify`, `forget` | bare calls with arguments in running text: SKILL.md:113 and :227 `improve(session_ids=...)`, SKILL.md:228 `serve(url=...)`, SKILL.md:181 `recall(query_text, scope=["tools"])`, references/full-api-reference.md:472 `export(format="cogx")`, references/core-workflow.md:388 `cognify(datasets=[dataset_id], ..., raise_on_error=False)` and `forget(data_id=..., memory_only=True)` | the declarations above, plus `cognee/api/v1/improve/improve.py:101`, `cognee/api/v1/serve/serve.py:17`, `cognee/api/v1/recall/recall.py:347`, `cognee/api/v1/forget/forget.py:22` | inventory-contract.md lists a call expression "after `await`, `new` or an assignment, through a receiver or module path ..., or as a statement in a fenced example"; a bare call in a running-text code span is in none of those | Recorded as usage forms and compared as calls: all match |
| 7 | `get_session`, `add_feedback`, `delete_feedback`, `distill_session` | references/full-api-reference.md:394-397 | `cognee/api/v1/session/session.py:65`, `:113`, `:147`; `cognee/modules/session_distillation/distill.py:471` | inventory-contract.md gives a `method` "the class or object it is called on" as `owner` and a function "the skill documents in a module" a bare `function`; `cognee.session` is a `types.SimpleNamespace`, neither a class nor a module | Methods of `session` (not compared). Read against the source by hand, all four signatures match, so the choice changes no result |

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)
**Migration Section:** Section 4b verification skipped: evidence-report.md pins no `t2_future_count`. For a skill create-skill made, re-run create-skill to regenerate the report with the field (create-stack-skill does not write it).

### Structural Findings

| # | Type | Severity | Detail | Line |
|---|------|----------|--------|------|
| - | none | - | Required sections satisfied (description: `Overview`, usage: `Quick Start`, API surface: `Key API Summary`); 6 fences, balanced, none without a language tag; no table row drift; no `scripts/` or `assets/` folder; every function and method export of the inventory is used in the usage-family scope (Quick Start, Common Workflows, Key API Summary and the four reference files); every async or sync claim agrees with its examples (27 exports with example calls: the async ones awaited directly or through `async for`, the sync tracing, `task`, `task_summary`, `run_tasks_parallel` and `cognee.config` calls not awaited) | - |

**Structural Issues:** 0

### Reference Consistency (split-body)

| # | Reference File | Export | Issue | Other Side | Reference Line | Contradicted Side |
|---|---------------|--------|-------|------------|---------------|-------------------|
| - | - | - | none | - | - | - |

**Exports Cross-Checked:** 97
**Mismatches Found:** 0

## External Validation

### skill-check
- **Available:** yes
- **Quality Score:** 90/100
- **Errors:** 0
- **Warnings:** 1
- **Diagnostics:** `body.max_tokens` (warn) at skills/oms-cognee/1.6.2/oms-cognee/SKILL.md:1: body token estimate 5700 exceeds max 5000 (suggestion: reduce body to ~5000 tokens or fewer; the count is a whitespace-split approximation)

### Tessl Review
- **Result:** off — set tessl_review_workspace in preferences.yaml to enable

### Combined External Score
- **External Validation Score:** 90%
- **Tools used:** skill-check

## Completeness Score

### Score Breakdown

| Category | Score | Weight | Weighted |
|----------|-------|--------|----------|
| Export Coverage | 100% | 45% | 45% |
| Signature Accuracy | 100% | 25% | 25% |
| Type Coverage | 100% | 20% | 20% |
| Coherence | not scored (naive mode) | 0% | 0% |
| External Validation | 90% | 10% | 9% |
| **Total** | | **100%** | **99%** |

### Result

**Score:** 99%
**Threshold:** 80%
**Result:** **PASS**

**Threshold Source:** workflow default (80%)
**Weight Distribution:** naive (redistributed)
**Tier Adjustment:** none
**External Validators:** skill-check only
**Analysis Confidence:** full
**Tooling Status:** ok

## Gap Report

**Total Gaps:** 45
**Blocking (Critical + High):** 0
**Non-blocking (Medium + Low + Info):** 45

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|------------------|
| Critical | 0 | None |
| High | 0 | None |
| Medium | 2 | Add type definitions, interface docs or the missing section |
| Low | 1 | Add examples or metadata |
| Info | 42 | Optional improvements, no action required |
| **Total** | **45** | |

### GAP-032: Stale documentation: run_migrations

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:29
**Export:** run_migrations

**Issue:** `SKILL.md:29` documents `run_migrations`, which the entry point `cognee/__init__.py` exports and `cognee/run_migrations.py:18` defines, a file `forge-data/oms-cognee/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `run_migrations` belongs on the surface: `forge-data/oms-cognee/skill-brief.yaml` scopes out `cognee/run_migrations.py:18`, where it is defined, since no `scope.include` glob covers that file and its `scope.exclude` glob `cognee/run_migrations.py` matches it. To keep its documentation, widen `scope.include` to cover that file and narrow `cognee/run_migrations.py` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `run_migrations` at SKILL.md:29.

### GAP-042: metadata drift — barrel export counts diverge

**Severity:** Medium
**Category:** Coverage (metadata-drift)
**Source:** skills/oms-cognee/1.6.2/oms-cognee/metadata.json

**Issue:** stats.exports_public_api=102, exports[].length=86 → 16% drift

**Remediation:** Re-run Create Skill, which rebuilds `exports[]` and `stats.exports_public_api` in `skills/oms-cognee/1.6.2/oms-cognee/metadata.json` from the source. Update Skill does not repair this drift: each time it writes the skill it recounts `stats.exports_public_api` from the source and keeps `exports[]`, adding or dropping only the names its provenance map changes, so a metadata patch does not hold.

### GAP-044: skill-check: body.max_tokens

**Severity:** Low
**Category:** External (external-validator)
**Source:** SKILL.md:1

**Issue:** body token estimate 5700 exceeds max 5000

**Remediation:** Shorten the SKILL.md body to about 5000 tokens or fewer (skill-check's whitespace-split estimate), for example by moving detail from SKILL.md into the references/ files, then re-run skill-check.

### GAP-001: Annotation contradicted: run_tasks_parallel (form 1 of 3)

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/operations/run_parallel.py:8
**Export:** run_tasks_parallel

**Issue:** the source annotates the return of `run_tasks_parallel` otherwise than the skill documents, and its body returns the documented type at `cognee/modules/pipelines/operations/run_parallel.py:15`: documented `run_tasks_parallel(tasks) -> Task`, source `def run_tasks_parallel(tasks: list[Task]) -> Callable[[Any], Generator[Any, Any, Any]]`: Only the return differs: the documented Task is what the body returns at line 15 (return Task(parallel_run)), while the declared annotation is Callable[[Any], Generator[Any, Any, Any]] (documented form 1 of 3: `(tasks) -> Task`)

**Remediation:** No change to the skill: it documents what `run_tasks_parallel` returns, as `cognee/modules/pipelines/operations/run_parallel.py:15` shows. Report the return annotation at `cognee/modules/pipelines/operations/run_parallel.py:8` upstream, since the body contradicts it.

### GAP-002: Annotation contradicted: run_tasks_parallel (form 2 of 3)

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/operations/run_parallel.py:8
**Export:** run_tasks_parallel

**Issue:** the source annotates the return of `run_tasks_parallel` otherwise than the skill documents, and its body returns the documented type at `cognee/modules/pipelines/operations/run_parallel.py:15`: documented `run_tasks_parallel(tasks: list[Task]) -> Task`, source `def run_tasks_parallel(tasks: list[Task]) -> Callable[[Any], Generator[Any, Any, Any]]`: Only the return differs: the documented Task is what the body returns at line 15 (return Task(parallel_run)), while the declared annotation is Callable[[Any], Generator[Any, Any, Any]] (documented form 2 of 3: `(tasks: list[Task]) -> Task`)

**Remediation:** No change to the skill: it documents what `run_tasks_parallel` returns, as `cognee/modules/pipelines/operations/run_parallel.py:15` shows. Report the return annotation at `cognee/modules/pipelines/operations/run_parallel.py:8` upstream, since the body contradicts it.

### GAP-003: Documented extra: BoundTask

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/tasks/task.py:8
**Export:** BoundTask

**Issue:** `SKILL.md:224` documents `BoundTask`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `BoundTask` is a documented extra, a name the source still declares at `cognee/modules/pipelines/tasks/task.py:8` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-004: Documented extra: CogneeApiError

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/exceptions.py:10
**Export:** CogneeApiError

**Issue:** `SKILL.md:288` documents `CogneeApiError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CogneeApiError` is a documented extra, a name the source still declares at `cognee/exceptions/exceptions.py:10` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-005: Documented extra: CogneeConfigurationError

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/exceptions.py:99
**Export:** CogneeConfigurationError

**Issue:** `SKILL.md:110` documents `CogneeConfigurationError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CogneeConfigurationError` is a documented extra, a name the source still declares at `cognee/exceptions/exceptions.py:99` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-006: Documented extra: CogneeSystemError

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/exceptions.py:69
**Export:** CogneeSystemError

**Issue:** `SKILL.md:289` documents `CogneeSystemError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CogneeSystemError` is a documented extra, a name the source still declares at `cognee/exceptions/exceptions.py:69` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-007: Documented extra: CogneeTransientError

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/exceptions.py:114
**Export:** CogneeTransientError

**Issue:** `SKILL.md:292` documents `CogneeTransientError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CogneeTransientError` is a documented extra, a name the source still declares at `cognee/exceptions/exceptions.py:114` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-008: Documented extra: CogneeValidationError

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/exceptions.py:84
**Export:** CogneeValidationError

**Issue:** `SKILL.md:227` documents `CogneeValidationError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CogneeValidationError` is a documented extra, a name the source still declares at `cognee/exceptions/exceptions.py:84` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-009: Documented extra: DataPoint

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/low_level.py:2
**Export:** DataPoint

**Issue:** `SKILL.md:282` documents `DataPoint`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `DataPoint` is a documented extra, a name the source still declares at `cognee/low_level.py:2` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-010: Documented extra: Edge

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/infrastructure/engine/models/Edge.py:13
**Export:** Edge

**Issue:** `SKILL.md:221` documents `Edge`, which the enumerated source API surface lacks and the source still declares; of the 5 files that declare it, the skill cites only `cognee/infrastructure/engine/models/Edge.py`

**Remediation:** No change: `Edge` is a documented extra, a name the source still declares at `cognee/infrastructure/engine/models/Edge.py:13` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-011: Documented extra: EntitySpec

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/graph_models/spec.py:90
**Export:** EntitySpec

**Issue:** `references/full-api-reference.md:282` documents `EntitySpec`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `EntitySpec` is a documented extra, a name the source still declares at `cognee/modules/graph_models/spec.py:90` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-012: Documented extra: FromIdentity

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/infrastructure/engine/models/FieldAnnotations.py:95
**Export:** FromIdentity

**Issue:** `SKILL.md:221` documents `FromIdentity`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `FromIdentity` is a documented extra, a name the source still declares at `cognee/infrastructure/engine/models/FieldAnnotations.py:95` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-013: Documented extra: GraphSchemaSpec

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/graph_models/spec.py:108
**Export:** GraphSchemaSpec

**Issue:** `references/full-api-reference.md:282` documents `GraphSchemaSpec`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `GraphSchemaSpec` is a documented extra, a name the source still declares at `cognee/modules/graph_models/spec.py:108` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-014: Documented extra: PipelineRunCompleted

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/models/PipelineRunInfo.py:34
**Export:** PipelineRunCompleted

**Issue:** `references/full-api-reference.md:267` documents `PipelineRunCompleted`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PipelineRunCompleted` is a documented extra, a name the source still declares at `cognee/modules/pipelines/models/PipelineRunInfo.py:34` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-015: Documented extra: PipelineRunErrored

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/models/PipelineRunInfo.py:42
**Export:** PipelineRunErrored

**Issue:** `references/core-workflow.md:100` documents `PipelineRunErrored`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PipelineRunErrored` is a documented extra, a name the source still declares at `cognee/modules/pipelines/models/PipelineRunInfo.py:42` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-016: Documented extra: PipelineRunInfo

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/models/PipelineRunInfo.py:9
**Export:** PipelineRunInfo

**Issue:** `references/full-api-reference.md:566` documents `PipelineRunInfo`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PipelineRunInfo` is a documented extra, a name the source still declares at `cognee/modules/pipelines/models/PipelineRunInfo.py:9` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-017: Documented extra: PipelineRunStarted

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/models/PipelineRunInfo.py:26
**Export:** PipelineRunStarted

**Issue:** `references/full-api-reference.md:267` documents `PipelineRunStarted`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PipelineRunStarted` is a documented extra, a name the source still declares at `cognee/modules/pipelines/models/PipelineRunInfo.py:26` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-018: Documented extra: REMEDIATION_MARKER

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/remediation.py:52
**Export:** REMEDIATION_MARKER

**Issue:** `SKILL.md:294` documents `REMEDIATION_MARKER`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `REMEDIATION_MARKER` is a documented extra, a name the source still declares at `cognee/exceptions/remediation.py:52` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-019: Documented extra: TaskSpec

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/tasks/task.py:35
**Export:** TaskSpec

**Issue:** `references/pipelines-and-datapoints.md:36` documents `TaskSpec`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `TaskSpec` is a documented extra, a name the source still declares at `cognee/modules/pipelines/tasks/task.py:35` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-020: Documented extra: UpdateResult

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/update/result.py:37
**Export:** UpdateResult

**Issue:** `references/core-workflow.md:390` documents `UpdateResult`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `UpdateResult` is a documented extra, a name the source still declares at `cognee/api/v1/update/result.py:37` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-021: Documented extra: __version__

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/__init__.py:22
**Export:** __version__

**Issue:** `SKILL.md:28` documents `__version__`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `__version__` is a documented extra, a name the source still declares at `cognee/__init__.py:22` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-022: Documented extra: add_data_points

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/tasks/storage/add_data_points.py:70
**Export:** add_data_points

**Issue:** `references/core-workflow.md:199` documents `add_data_points`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `add_data_points` is a documented extra, a name the source still declares at `cognee/tasks/storage/add_data_points.py:70` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-023: Documented extra: find_remediation

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/remediation.py:131
**Export:** find_remediation

**Issue:** `SKILL.md:294` documents `find_remediation`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `find_remediation` is a documented extra, a name the source still declares at `cognee/exceptions/remediation.py:131` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-024: Documented extra: get_default_tasks

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/cognify/cognify.py:565
**Export:** get_default_tasks

**Issue:** `references/core-workflow.md:183` documents `get_default_tasks`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_default_tasks` is a documented extra, a name the source still declares at `cognee/api/v1/cognify/cognify.py:565` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-025: Documented extra: get_errored_run_info

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/models/PipelineRunInfo.py:62
**Export:** get_errored_run_info

**Issue:** `references/full-api-reference.md:574` documents `get_errored_run_info`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_errored_run_info` is a documented extra, a name the source still declares at `cognee/modules/pipelines/models/PipelineRunInfo.py:62` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-026: Documented extra: graph_model_from_spec

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/graph_models/compiler.py:135
**Export:** graph_model_from_spec

**Issue:** `references/full-api-reference.md:282` documents `graph_model_from_spec`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `graph_model_from_spec` is a documented extra, a name the source still declares at `cognee/modules/graph_models/compiler.py:135` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-027: Documented extra: graph_spec_to_json_schema

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/graph_models/compiler.py:119
**Export:** graph_spec_to_json_schema

**Issue:** `references/full-api-reference.md:282` documents `graph_spec_to_json_schema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `graph_spec_to_json_schema` is a documented extra, a name the source still declares at `cognee/modules/graph_models/compiler.py:119` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-028: Documented extra: is_tracing_enabled

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/observability/trace_context.py:62
**Export:** is_tracing_enabled

**Issue:** `references/full-api-reference.md:304` documents `is_tracing_enabled`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `is_tracing_enabled` is a documented extra, a name the source still declares at `cognee/modules/observability/trace_context.py:62` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-029: Documented extra: pipeline_needs_llm

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/tasks/task.py:160
**Export:** pipeline_needs_llm

**Issue:** `SKILL.md:268` documents `pipeline_needs_llm`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `pipeline_needs_llm` is a documented extra, a name the source still declares at `cognee/modules/pipelines/tasks/task.py:160` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-030: Documented extra: pipelines

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/__init__.py:1
**Export:** pipelines

**Issue:** `SKILL.md:29` documents `pipelines`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `pipelines` is a documented extra, a name the source still declares at `cognee/modules/pipelines/__init__.py:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-031: Documented extra: remediation_for

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/remediation.py:146
**Export:** remediation_for

**Issue:** `SKILL.md:294` documents `remediation_for`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `remediation_for` is a documented extra, a name the source still declares at `cognee/exceptions/remediation.py:146` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-033: Documented extra: run_relational_migrations

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/run_migrations.py:11
**Export:** run_relational_migrations

**Issue:** the skill documents `run_relational_migrations`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `cognee/run_migrations.py`

**Remediation:** No change: `run_relational_migrations` is a documented extra, a name the source still declares at `cognee/run_migrations.py:11` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-034: Documented extra: setup

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/engine/operations/setup.py:9
**Export:** setup

**Issue:** `SKILL.md:221` documents `setup`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `setup` is a documented extra, a name the source still declares at `cognee/modules/engine/operations/setup.py:9` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-035: Documented extra: start_visualization_server

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/visualize/start_visualization_server.py:1
**Export:** start_visualization_server

**Issue:** `SKILL.md:29` documents `start_visualization_server`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `start_visualization_server` is a documented extra, a name the source still declares at `cognee/api/v1/visualize/start_visualization_server.py:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-036: Documented extra: task

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/tasks/task.py:124
**Export:** task

**Issue:** `references/pipelines-and-datapoints.md:35` documents `task`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `task` is a documented extra, a name the source still declares at `cognee/modules/pipelines/tasks/task.py:124` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-037: Documented extra: task_summary

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/tasks/task.py:169
**Export:** task_summary

**Issue:** `references/pipelines-and-datapoints.md:36` documents `task_summary`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `task_summary` is a documented extra, a name the source still declares at `cognee/modules/pipelines/tasks/task.py:169` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-038: Documented extra: tools

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/tools/tools.py:1
**Export:** tools

**Issue:** `SKILL.md:29` documents `tools`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `tools` is a documented extra, a name the source still declares at `cognee/api/v1/tools/tools.py:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-039: Documented extra: visualize_graph_json

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/visualize/visualize.py:271
**Export:** visualize_graph_json

**Issue:** `references/full-api-reference.md:337` documents `visualize_graph_json`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `visualize_graph_json` is a documented extra, a name the source still declares at `cognee/api/v1/visualize/visualize.py:271` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-040: Documented extra: visualize_multi_user_graph

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/visualize/visualize.py:611
**Export:** visualize_multi_user_graph

**Issue:** `references/full-api-reference.md:339` documents `visualize_multi_user_graph`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `visualize_multi_user_graph` is a documented extra, a name the source still declares at `cognee/api/v1/visualize/visualize.py:611` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-041: Documented extra: visualize_semantic_json

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/visualize/visualize.py:317
**Export:** visualize_semantic_json

**Issue:** `references/full-api-reference.md:338` documents `visualize_semantic_json`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `visualize_semantic_json` is a documented extra, a name the source still declares at `cognee/api/v1/visualize/visualize.py:317` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-043: multi-denominator reporting — barrel vs documented surface

**Severity:** Info
**Category:** Coverage (multi-denominator)
**Source:** skills/oms-cognee/1.6.2/oms-cognee/metadata.json

**Issue:** barrel=102, documented=86

**Remediation:** No action required: the barrel and the documented surface measure different sets by design, and the report records both counts.

### GAP-045: Discovery testing not performed: subagents unavailable, routing test requires isolated context

**Severity:** Info
**Category:** Discovery (discovery)
**Source:** SKILL.md frontmatter description

**Issue:** This run's environment could not spawn the isolated routing subagents §4b.2 needs (catalog of 4 skills: oms-cocoindex, oms-cognee, oms-storybook-react-vite, oms-uitripled), so the three realistic prompts were not routed and the discovery check is excluded from scoring.

**Remediation:** Re-run test-skill for oms-cognee in an environment that can spawn subagents so §4b.2 routes three realistic prompts against the 4-skill catalog in skills/.

### Discovery Quality

**Discovery Test:** skipped: subagents unavailable, routing test requires isolated context

discovery: skipped, subagents unavailable, routing test requires isolated context (catalog of 4 skills in `skills/`: oms-cocoindex, oms-cognee, oms-storybook-react-vite, oms-uitripled). The check is excluded from scoring. No description optimization hints: Tessl Review did not run and skill-check flagged no description issue.
