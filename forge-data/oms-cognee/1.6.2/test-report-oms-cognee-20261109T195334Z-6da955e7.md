---
workflowType: 'test-skill'
skillName: 'oms-cognee'
skillDir: 'skills/oms-cognee/1.6.2/oms-cognee'
runId: '20261109T195334Z-6da955e7'
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
testDate: '2026-11-09T19:53:34Z'
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

**Mode Rationale:** metadata.json records `skill_type: 'single'`: an individual skill, so naive mode (API-surface coverage; coherence is structural only and not a scored category).

**Analysis Plan:**
- Coverage Check: every public export cognee v1.6.2 ships from `cognee/__init__.py` (source at the pinned commit ba3631f) checked for documentation in SKILL.md and its references; Deep tier, so signatures are compared against the AST-backed source and type coverage is scored.
- Coherence Check: structural only (naive mode): references resolve, internal links work, no coherence category in the score.

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
| `COGXRecord` | type | yes | - | cognee/modules/migration/cogx.py:160 | PASS |
| `COGXScope` | class | yes | yes | cognee/modules/migration/cogx.py:60 | PASS |
| `COGXTurn` | class | yes | yes | cognee/modules/migration/cogx.py:87 | PASS |
| `COGX_VERSION` | const | yes | - | cognee/modules/migration/cogx.py:22 | PASS |
| `CogneeApiError` | - | yes | - | - | WARN |
| `CogneeConfigurationError` | - | yes | - | - | WARN |
| `CogneeSystemError` | - | yes | - | - | WARN |
| `CogneeTransientError` | - | yes | - | - | WARN |
| `CogneeValidationError` | - | yes | - | - | WARN |
| `DataPoint` | - | yes | - | - | WARN |
| `Dedup` | - | yes | - | - | WARN |
| `DistillationResult` | - | yes | - | - | WARN |
| `Drop` | const | yes | - | cognee/pipelines/types.py:32 | PASS |
| `EXPORT_FORMATS` | const | yes | - | cognee/modules/migration/export.py:35 | PASS |
| `Edge` | - | yes | - | - | WARN |
| `Embeddable` | - | yes | - | - | WARN |
| `EntitySpec` | - | yes | - | - | WARN |
| `ExportResult` | class | yes | yes | cognee/modules/migration/export.py:41 | PASS |
| `ExtendableDataPoint` | - | yes | - | - | WARN |
| `FeedbackEntry` | class | yes | - | cognee/memory/entries.py:62 | PASS |
| `FromIdentity` | - | yes | - | - | WARN |
| `GraphEdge` | class | yes | yes | cognee/modules/migration/snapshot.py:152 | PASS |
| `GraphSchemaSpec` | - | yes | - | - | WARN |
| `GraphSnapshot` | class | yes | yes | cognee/modules/migration/snapshot.py:161 | PASS |
| `GraphitiSource` | class | yes | - | cognee/modules/migration/sources/zep.py:136 | PASS |
| `IMPORT_MODES` | const | yes | - | cognee/modules/migration/sources/base.py:19 | PASS |
| `INTERNAL_PROPERTY` | - | yes | - | - | WARN |
| `ImproveKwargs` | - | yes | - | - | WARN |
| `InternalDataPoint` | - | yes | - | - | WARN |
| `LLMContext` | - | yes | - | - | WARN |
| `LLMGateway` | - | yes | - | - | WARN |
| `LettaSource` | class | yes | yes | cognee/modules/migration/sources/letta.py:72 | PASS |
| `Mem0Source` | class | yes | yes | cognee/modules/migration/sources/mem0.py:26 | PASS |
| `MemoryEntry` | type | yes | - | cognee/memory/entries.py:129 | PASS |
| `MemorySource` | class | yes | yes | cognee/modules/migration/sources/base.py:36 | PASS |
| `PipelineContext` | - | yes | - | - | WARN |
| `PipelineRunCompleted` | - | yes | - | - | WARN |
| `PipelineRunErrored` | - | yes | - | - | WARN |
| `PipelineRunInfo` | - | yes | - | - | WARN |
| `PipelineRunStarted` | - | yes | - | - | WARN |
| `PushResult` | class | yes | yes | cognee/api/v1/push/push.py:26 | PASS |
| `QAEntry` | class | yes | - | cognee/memory/entries.py:24 | PASS |
| `REMEDIATION_MARKER` | - | yes | - | - | WARN |
| `RememberKwargs` | - | yes | - | - | WARN |
| `RememberResult` | class | yes | - | cognee/api/v1/remember/remember.py:600 | PASS |
| `SearchType` | class | yes | - | cognee/modules/search/types/SearchType.py:4 | PASS |
| `SessionModelUsage` | class | yes | - | cognee/modules/session_lifecycle/models.py:96 | PASS |
| `SessionRecord` | class | yes | - | cognee/modules/session_lifecycle/models.py:10 | PASS |
| `SkillRunEntry` | - | yes | - | - | WARN |
| `Task` | class | yes | yes | cognee/modules/pipelines/tasks/task.py:188 | PASS |
| `TaskSpec` | - | yes | - | - | WARN |
| `TraceEntry` | class | yes | - | cognee/memory/entries.py:40 | PASS |
| `UpdateResult` | - | yes | - | - | WARN |
| `ValidationIssue` | class | yes | yes | cognee/api/v1/validate/validate.py:99 | PASS |
| `ValidationReport` | class | yes | yes | cognee/api/v1/validate/validate.py:105 | PASS |
| `ValidationStatus` | class | yes | - | cognee/api/v1/validate/validate.py:93 | PASS |
| `WRITE_PIPELINE_NAMES` | - | yes | - | - | WARN |
| `ZepSource` | class | yes | yes | cognee/modules/migration/sources/zep.py:57 | PASS |
| `__version__` | - | yes | - | - | WARN |
| `add` | function | yes | yes | cognee/api/v1/add/add.py:39 | PASS |
| `add_data_points` | - | yes | - | - | WARN |
| `add_feedback` | - | yes | - | - | WARN |
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
| `delete_feedback` | - | yes | - | - | WARN |
| `disable_tracing` | function | yes | yes | cognee/modules/observability/trace_context.py:43 | PASS |
| `disconnect` | function | yes | yes | cognee/api/v1/serve/disconnect.py:8 | PASS |
| `distill_session` | - | yes | - | - | WARN |
| `enable_tracing` | function | yes | yes | cognee/modules/observability/trace_context.py:18 | PASS |
| `exceptions` | - | yes | - | - | WARN |
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
| `get_session` | - | yes | - | - | WARN |
| `graph_model_from_spec` | - | yes | - | - | WARN |
| `graph_model_to_graph_schema` | - | yes | - | - | WARN |
| `graph_schema_to_graph_model` | - | yes | - | - | WARN |
| `graph_spec_to_json_schema` | - | yes | - | - | WARN |
| `improve` | function | yes | yes | cognee/api/v1/improve/improve.py:101 | PASS |
| `is_internal_node` | - | yes | - | - | WARN |
| `is_tracing_enabled` | - | yes | - | - | WARN |
| `list_sql_connections` | function | yes | yes | cognee/api/v1/tools/tools.py:65 | PASS |
| `list_write_proposals` | function | yes | yes | cognee/api/v1/tools/tools.py:119 | PASS |
| `logger` | const | yes | - | cognee/__init__.py:34 | PASS |
| `low_level` | - | yes | - | - | WARN |
| `memify` | function | yes | yes | cognee/modules/memify/memify.py:27 | PASS |
| `migration` | - | yes | - | - | WARN |
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
| `setup_logging` | - | yes | - | - | WARN |
| `start_ui` | function | yes | yes | cognee/api/v1/ui/ui.py:514 | PASS |
| `start_visualization_server` | - | yes | - | - | WARN |
| `task` | - | yes | - | - | WARN |
| `task_summary` | - | yes | - | - | WARN |
| `tools` | - | yes | - | - | WARN |
| `update` | function | yes | yes | cognee/api/v1/update/update.py:28 | PASS |
| `use_vector_adapter` | - | yes | - | - | WARN |
| `validate` | function | yes | yes | cognee/api/v1/validate/validate.py:198 | PASS |
| `visualization_server` | function | yes | yes | cognee/api/v1/visualize/start_visualization_server.py:6 | PASS |
| `visualize` | function | yes | - | cognee/api/v1/visualize/visualize.py:193 | PASS |
| `visualize_graph` | function | yes | yes | cognee/api/v1/visualize/visualize.py:193 | PASS |
| `visualize_graph_json` | - | yes | - | - | WARN |
| `visualize_memory_provenance` | function | yes | yes | cognee/api/v1/visualize/memory_provenance.py:848 | PASS |
| `visualize_multi_user_graph` | - | yes | - | - | WARN |
| `visualize_semantic_json` | - | yes | - | - | WARN |
| `wait_for_background_tasks` | - | yes | - | - | WARN |

### Coverage Summary

- **Exports Found:** 92
- **Documented:** 92 (100%)
- **Missing Documentation:** 0
- **Signature Mismatches:** 0, plus 2 graded Low or Info and counted as matching
- **Stale Documentation:** 65, documented extras included
- **Scoring Warnings:**
  - Type Coverage leaves out each name the stale-scope guard restored or the extraction recorded with no kind, such as an extraction gap (the provenance map, when one is given, gives it no kind Type Coverage reads at its file): `session`
- **Borderline Calls:**
  - `remember` (SKILL.md:180), inventory reader: the Key params column is read as a Params-role column for the row's own leading form, while the prose sentences inside its cells are read as running text, so `Pass one to remember()` is a mention and gives remember no entry at this row (likewise `await cognee.wait_for_background_tasks()` at SKILL.md:157, `records()` at SKILL.md:191 and `to_dict()` at SKILL.md:182); left open by: A description cell is any table cell but an export table's first cell and a cell whose column writes the call or signature, by its role (Signature, Props, Params, Parameters, Arguments, Usage, Syntax, Example and the like); a heading or an export table's first cell that writes `name()` is a form, recorded as written; the other reading gives: read as a form in a Params-role column, remember() is an empty call that leaves out the required data argument: a Critical signature-mismatch
  - `search` (SKILL.md:135), inventory reader: `query_type=SearchType.HYBRID_COMPLETION` by default, after the link to the 27 params, states a default in prose rather than a parameter list, so this row's entry writes only return_type list[SearchResult] (no params, no at); left open by: a function or method carries `params` (`""` or `[]` when it takes none; ...) and `return_type` as the skill documents them, and leaves a key out when the skill documents nothing for it; the other reading gives: read as a partial parameter list `query_type=SearchType.HYBRID_COMPLETION`, the form leaves out the required query_text: a Critical signature-mismatch and a split-body mismatch against references/core-workflow.md:230 and references/full-api-reference.md:121
  - `cognify` (SKILL.md:134), inventory reader: the arrow `-> {dataset_id: PipelineRunInfo} ..., or DryRunEstimate with dry_run=True` after the link to the 23 params is a form that writes only a return_type, recorded with no at (likewise search at SKILL.md:135 and update at SKILL.md:137); left open by: a form that writes only a `return_type` gives no `at`, so it is compared as one whose citations name no declaration; the other reading gives: read as prose, these rows give no entry: no gap (cognify's return is unannotated in the source, search's and update's match)
  - `update` (SKILL.md:137), inventory reader: `data_id`, `data`, `dataset_id` required are three separate code spans in prose naming the required parameters, not a parameter list, so the entry writes only return_type dict; left open by: A list of bare names, with no type, default or `?` (`connect(host, port)`, `({ themes, defaultTheme })`), names parameters without claiming the list is complete: an optional member it leaves out is no difference, a required one is a mismatch; the other reading gives: read as the bare-name list data_id, data, dataset_id (partial), it names the source's three required leading parameters: no gap
  - `start_ui` (SKILL.md:230), inventory reader: `Signature: start_ui(pid_callback, port=3000, ...)` on a prose line writes no type, `?`, bare `*` or return, so it is recorded as a usage (call) despite its Signature label, and the prose `returns Optional[subprocess.Popen]` is not recorded as return_type; left open by: A name written with arguments in running text or a description cell is a call (below), not a list of bare names, whatever comes before the name, unless it writes a parameter type, a `?`, a bare `*` or `/` (no call writes one), or a return type with no `await`, `new`, assignment, receiver or module path before the name; the other reading gives: read as a parameter list in params (its defaults state optionality, so it claims to be complete), any optional parameter of the source it leaves out would be a Critical omitted-optional signature-mismatch; with return_type Optional[subprocess.Popen] recorded, a source annotation naming another type would be a mismatch too
  - `Task` (SKILL.md:268), inventory reader: `Constructor: Task(executable, *args, task_config=None, ...)` writes no type (`*args` is no bare `*`), so it is a usage, not the class's params (likewise the bullet at references/full-api-reference.md:266); left open by: A name written with arguments in running text or a description cell is a call (below), not a list of bare names, whatever comes before the name, unless it writes a parameter type, a `?`, a bare `*` or `/` (no call writes one), or a return type with no `await`, `new`, assignment, receiver or module path before the name; the other reading gives: read as the class's params, it is the same list as the __init__ at references/pipelines-and-datapoints.md:62: no gap
  - `PipelineRunStarted` (references/full-api-reference.md:570), inventory reader: the bullet lead `PipelineRunStarted(pipeline_run_id, dataset_id, dataset_name, payload)` writes no types, so it is a call with positional arguments recorded in usage_signature; left open by: A name written with arguments in running text or a description cell is a call (below), not a list of bare names, whatever comes before the name, unless it writes a parameter type, a `?`, a bare `*` or `/` (no call writes one), or a return type with no `await`, `new`, assignment, receiver or module path before the name; the other reading gives: read as a list of the model's field names in params, no mismatch; as a call, if the source class is a pydantic model (keyword-only constructor), its positional arguments are a Critical signature-mismatch
  - `PipelineRunCompleted` (references/full-api-reference.md:571), inventory reader: the bullet lead `PipelineRunCompleted(pipeline_run_id, dataset_id, dataset_name, data_ingestion_info)` writes no types, so it is a call with positional arguments recorded in usage_signature; left open by: A name written with arguments in running text or a description cell is a call (below), not a list of bare names, whatever comes before the name, unless it writes a parameter type, a `?`, a bare `*` or `/` (no call writes one), or a return type with no `await`, `new`, assignment, receiver or module path before the name; the other reading gives: read as a list of the model's field names in params, no mismatch; as a call, if the source class is a pydantic model (keyword-only constructor), its positional arguments are a Critical signature-mismatch
  - `PipelineRunErrored` (references/full-api-reference.md:572), inventory reader: the bullet lead `PipelineRunErrored(pipeline_run_id, dataset_id, dataset_name, payload, data_ingestion_info, error_class, error_message)` writes no types, so it is a call with positional arguments recorded in usage_signature; left open by: A name written with arguments in running text or a description cell is a call (below), not a list of bare names, whatever comes before the name, unless it writes a parameter type, a `?`, a bare `*` or `/` (no call writes one), or a return type with no `await`, `new`, assignment, receiver or module path before the name; the other reading gives: read as a list of the model's field names in params, no mismatch; as a call, if the source class is a pydantic model (keyword-only constructor), its positional arguments are a Critical signature-mismatch
  - `ValidationReport` (SKILL.md:177), inventory reader: the Key params cell is a Params-role column, neither running text nor a description cell, so `ValidationReport(status, summary, issues)` with no prefix is a signature, recorded as params `status, summary, issues` (bare names), as inventory-floor.json reads `MemorySource(mode="re-derive")` at SKILL.md:191; left open by: A function's, a method's or a class's form the skill writes as a call expression of its own name (after `await`, `new` or an assignment, through a receiver or module path such as `coco.`, or as a statement in a fenced example; in running text or a description cell, only a call that passes an argument and writes no parameter type, `?`, bare `*` or `/`, ...) ... is recorded whole in `usage_signature`; the other reading gives: read as a call in the cell's prose, its positional arguments to a pydantic model's keyword-only constructor are a Critical signature-mismatch
  - `ValidationIssue` (SKILL.md:177), inventory reader: `ValidationIssue(severity, type, detail)` in the Params-role Key params cell is a signature, recorded as params `severity, type, detail` (bare names); left open by: A function's, a method's or a class's form the skill writes as a call expression of its own name (after `await`, `new` or an assignment, through a receiver or module path such as `coco.`, or as a statement in a fenced example; in running text or a description cell, only a call that passes an argument and writes no parameter type, `?`, bare `*` or `/`, ...) ... is recorded whole in `usage_signature`; the other reading gives: read as a call in the cell's prose, its positional arguments to a pydantic model's keyword-only constructor are a Critical signature-mismatch
  - `COGXDocument` (SKILL.md:200), inventory reader: the forms after the shared base-field sentence are each name's own form in the Params-role Key params cell, recorded as params with the shared text first and `; ` (as the contract's Note example); left open by: Where the skill documents several names and states members they share once, in the same place (a table row, a paragraph) ..., each name's entry carries that shared text in its `params` (in its `usage_signature`, for a usage form); the other reading gives: read as calls in the cell's prose (usage_signature), the positional external_id and content arguments to a pydantic model's keyword-only constructor are a Critical signature-mismatch
  - `COGXEpisode` (SKILL.md:200), inventory reader: `COGXEpisode(kind="episode", turns=[], title=None)` is read as its own params after the shared base fields and `; `; left open by: Where the skill documents several names and states members they share once, in the same place (a table row, a paragraph) ..., each name's entry carries that shared text in its `params` (in its `usage_signature`, for a usage form); the other reading gives: read as a call (usage_signature), the shared text's positional external_id argument to a pydantic model's keyword-only constructor is a Critical signature-mismatch
  - `COGXEntity` (SKILL.md:200), inventory reader: `COGXEntity(kind="entity", name, ...)` is read as its own params after the shared base fields and `; `; left open by: Where the skill documents several names and states members they share once, in the same place (a table row, a paragraph) ..., each name's entry carries that shared text in its `params` (in its `usage_signature`, for a usage form); the other reading gives: read as a call (usage_signature), the positional external_id and name arguments to a pydantic model's keyword-only constructor are a Critical signature-mismatch
  - `COGXFact` (SKILL.md:200), inventory reader: `COGXFact(kind="fact", subject_ref, predicate, object_ref, ...)` is read as its own params after the shared base fields and `; `; left open by: Where the skill documents several names and states members they share once, in the same place (a table row, a paragraph) ..., each name's entry carries that shared text in its `params` (in its `usage_signature`, for a usage form); the other reading gives: read as a call (usage_signature), the positional external_id, subject_ref, predicate and object_ref arguments to a pydantic model's keyword-only constructor are a Critical signature-mismatch
  - `COGXMemory` (SKILL.md:200), inventory reader: `COGXMemory(kind="memory", content, categories=[])` is read as its own params after the shared base fields and `; `; left open by: Where the skill documents several names and states members they share once, in the same place (a table row, a paragraph) ..., each name's entry carries that shared text in its `params` (in its `usage_signature`, for a usage form); the other reading gives: read as a call (usage_signature), the positional external_id and content arguments to a pydantic model's keyword-only constructor are a Critical signature-mismatch
  - `COGXMemoryBlock` (SKILL.md:200), inventory reader: `COGXMemoryBlock(kind="memory_block", label, value, limit=None)` is read as its own params after the shared base fields and `; `; left open by: Where the skill documents several names and states members they share once, in the same place (a table row, a paragraph) ..., each name's entry carries that shared text in its `params` (in its `usage_signature`, for a usage form); the other reading gives: read as a call (usage_signature), the positional external_id, label and value arguments to a pydantic model's keyword-only constructor are a Critical signature-mismatch
  - `GraphitiSource` (SKILL.md:195), inventory reader: the row writes no form of GraphitiSource's own: `same ZepSource(data, mode="hybrid") constructor` is ZepSource's form, recorded as a ZepSource usage at SKILL.md:195, so GraphitiSource's entry has no params; left open by: A place `inventory-floor.json` gives a `signature` ... has that form as its entry, with that place as its `at`, whatever its kind, its non-blank fields kept as given ...; a blank one is the reader's, left out when the place writes none; the other reading gives: read as GraphitiSource's own params `data, mode="hybrid"`, it matches the ZepSource constructor the subclass inherits: no gap
  - `recall` (SKILL.md:181), inventory reader: `recall(query_text, scope=["tools"])` inside the tools row's prose is another name's form in running text, a call recorded as a recall usage, partial by the Key params header; left open by: A description cell is any table cell but an export table's first cell and a cell whose column writes the call or signature, by its role (Signature, Props, Params, Parameters, Arguments, Usage, Syntax, Example and the like); the other reading gives: read as recall's params `query_text, scope=["tools"]` in a Params-role cell, the partial list names the required query_text and the keyword scope: no gap
  - `prune_data` (SKILL.md:139), inventory reader: `.prune_data()` in the prune row's methods list (a Params-role cell, not a description cell) is the method's empty-call form, recorded as usage `prune_data()` with the bare leading `.` dropped; left open by: A name written with empty parentheses, or with only `...` or `…` between them, in running text or a description cell is a mention, not a form, whatever comes before the name; the other reading gives: read as a mention, prune_data gets no entry at this row: no gap
  - `get_session` (references/full-api-reference.md:394), inventory reader: cognee.session is a types.SimpleNamespace whose four members the skill calls functions, importable from cognee.api.v1.session, so get_session, add_feedback, delete_feedback and distill_session are bare functions; left open by: A function the skill documents in a module is a `function` named bare, never a `method`, even when it is called through the module's name; the other reading gives: read as methods with owner session, the forms bind to the namespace's members instead: no gap
  - `pipelines` (SKILL.md:29), inventory reader: no kind names a module or namespace, so the modules pipelines, tools, migration, start_visualization_server, low_level and exceptions and the session namespace are listed as constant; left open by: each `kind` is one of `function`, `class`, `type`, `constant`, `hook`, `interface`, `method`, `struct`, `enum`, `trait`, `macro` or `adapter`; the other reading gives: another kind such as class: no gap
  - `Drop` (SKILL.md:29), inventory reader: the Overview's Confidence line is Drop's lowest SKILL.md line, so its entry sits there rather than at its export-table row SKILL.md:146 (likewise __version__ and logger at SKILL.md:28, and MemoryEntry, pipelines, tools, session and start_visualization_server at SKILL.md:29); left open by: of several such places of a name the skill documents and no other place gives an entry, the first alone gives one: in SKILL.md, else the file that sorts first by path, at its lowest line; the other reading gives: the export-table row as at: no gap; only the line a stale-name gap would cite changes
  - `DataPoint` (SKILL.md:282), inventory reader: the Key Types section headed `### DataPoint` writes its metadata attribute, so it gives DataPoint an entry carrying it (as do references/full-api-reference.md:284 and references/pipelines-and-datapoints.md:340), and the Confidence-line mention at SKILL.md:29 gives none; left open by: A place that writes a name but no form of it, and no methods, properties or fields its entry would carry (a mention, a bare code span, an import, a heading or prose that names or describes it), gives it no entry when another place gives the name one; the other reading gives: read as prose with no member, DataPoint's single entry falls to SKILL.md:29: no gap
  - `visualize` (SKILL.md:163), inventory reader: visualize is presented only as an alias of visualize_graph, so its entry comes from the export table's first cell SKILL.md:163; left open by: A name the skill presents only as a local import alias of another name, or says the source does not export, is not an export the skill documents either: it gets an entry only from a place `inventory-floor.json` gives it, a heading, an export table's first cell or a fenced declaration of it; the other reading gives: read as a re-export rather than a local import alias, its first mention SKILL.md:29 gives the entry: no gap
  - `add` (references/full-api-reference.md:37), inventory reader: a heading writing `cognee.add(...)` is a form too, a call through the module path recorded in usage_signature and labelled partial by its `...` (likewise the cognify, search, memify, update, get_schema_inventory, get_memory_provenance_graph, visualize_memory_provenance, export, push, validate and report headings); left open by: a heading or an export table's first cell that writes `name()` is a form, recorded as written; the other reading gives: read as a mention, as `(...)` is in running text, the headings give no entry: no gap, since an ellipsis claims nothing
  - `ValidationReport` (references/full-api-reference.md:487), inventory reader: the bullet `ValidationReport — status: ValidationStatus, summary: dict[str, Any] (...), issues: list[ValidationIssue]` lists the model's fields in separate code spans, recorded as properties rather than params (likewise PushResult at :474, ExportResult at :455 and QAEntry/TraceEntry/FeedbackEntry at :580-582), so none of them is cross-checked against SKILL.md's forms; left open by: while a class's form written as a parameter list or a signature that is not such a call stays in `params`; the other reading gives: read as typed params, they agree with SKILL.md's bare-name forms and the generated constructors' fields: no gap
  - `task` (references/pipelines-and-datapoints.md:129), inventory reader: `returns a TaskSpec` after the signature code span is prose, not a written return type, so return_type is left out (likewise the prose Returns sections of add and cognify and start_ui's prose return); left open by: a function or method carries `params` (...) and `return_type` as the skill documents them, and leaves a key out when the skill documents nothing for it; the other reading gives: with return_type TaskSpec recorded, it is compared with the source's return: a gap only if the source annotates another type
  - `DryRunEstimate` (SKILL.md:134), inventory reader: result and error types the skill names only as returns or raised errors in prose (DryRunEstimate, ImproveResult, RecallResponse, SearchResult, CloudClient, PresortReport, CognifyFailedError, MigrationError, DatasetNotFoundError and the like) are not read as exports the skill documents, so they get no entry; left open by: A name the skill writes only in a type position (...) is a type mention, not an export the skill documents, even when its code span is exactly the name, and gets no entry, unless the skill also writes it as one outside a type position: a place `inventory-floor.json` gives it, a heading, an export table's first cell, a code span that is the name or the name then `(`, or a fenced declaration; the other reading gives: listed from their prose code spans as mention-only entries: possible stale-name gaps for names outside the export surface, no signature gap
  - `export` (cognee/api/v1/export/export.py:16), signature judge: Form 6 is bound to line 16, the first @overload stub (-> GraphSnapshot), which opens the overload set at lines 16/27/38/49. Read 'its bound declaration alone' as excluding the check's candidates, not the overload set, so line 16 is read through its implementation (line 49, -> ExportResult | GraphSnapshot, every parameter defaulted). Form 6's defaulted untyped list of all six parameters matches it, and its return 'GraphSnapshot for "pydantic", ExportResult for "cogx"/"json"/"graphml"/"cypher"' states the union GraphSnapshot | ExportResult, which matches the implementation's return: no mismatch; left open by: "A form the check binds (`bound`: its own citations name one declaration of the name) is compared with its bound declaration alone, and its mismatch is reported there, at that declaration's file and line, whatever the check's location and candidates." against "A declaration opening an overload set (Python `@overload` stubs, TS bodiless signatures) is read through its implementation: a documented signature matching the implementation or any overload is no mismatch, and so is one whose parameter types are, position by position, the unions of the overloads' types."; the other reading gives: Read as the line-16 stub alone, form 6's return GraphSnapshot | ExportResult names ExportResult, a member the stub's -> GraphSnapshot never returns: a Critical mismatch on the return type, untagged (the parameters still match, all six optional)
  - `get_schema_inventory` (cognee/api/v1/visualize/get_schema_inventory.py:77), signature judge: Form 1's return_type "list of {type, count, samples, sample_size, relationships} dicts" is read as the type `list` whose items are `dict` (list[dict]), the braced key names being description; against the declared `-> list[dict[str, Any]]` the type arguments it leaves out are not compared, so it matches (the body returns `inventory`, a list of dicts, at line 197); left open by: A bracketed or braced list of value names, such as `→ [state, setState]` or `=> { data, error }`, likewise states none, while a single name (`→ result`), a list that writes a type among its names (`(nodes: list[Node], edges)`) and a description followed by a type (`HTML str`) each state one; the other reading gives: Read as a description ("list of {...}") followed by the type `dicts`, it would state `dict` alone, a return-type mismatch with `list[dict[str, Any]]` and no difference tag (a Critical mismatch)
  - `datapoint_registry` (cognee/modules/migration/snapshot.py:39), signature judge: The documented return `dict[str, type[DataPoint]]` reads `DataPoint` as the base class `cognee.infrastructure.engine.DataPoint` (cognee/infrastructure/engine/models/DataPoint.py:28). The package exports that class under the name, the skill documents it too ("`cognee.infrastructure.engine` also exports the base class itself as `DataPoint`"), and snapshot.py imports the same declaration, so the return matches. The rule does not say which type wins when the skill and the package give the name to two declarations: the skill's SKILL.md key type `DataPoint` is `cognee.low_level`'s alias of `ExtendableDataPoint`; left open by: A type name a form writes means the type the skill documents or the package exports under that name, and the source file's own declaration of it only when there is none, or when the file declares the name other than as an alias (a local `interface Options`); the other reading gives: Reading `DataPoint` as `ExtendableDataPoint` (the skill's key-type `DataPoint`, cognee/low_level.py:2) gives a written type argument `type[ExtendableDataPoint]` that differs from the source's `type[DataPoint]`. That is a Critical mismatch on the return type, with no difference tag
  - `rehydrate_node` (cognee/modules/migration/snapshot.py:116), signature judge: The documented return `DataPoint` reads as the base class `cognee.infrastructure.engine.DataPoint` (cognee/infrastructure/engine/models/DataPoint.py:28). The package exports that class under the name, the skill documents it too, and snapshot.py imports and declares the same class as the return, so the return matches. The parameters `properties, registry=None` match `(properties: dict[str, Any], registry: dict[str, type[DataPoint]] | None = None)`. The rule does not say which type wins when the skill and the package give the name to two declarations: the skill's key type `DataPoint` is `cognee.low_level`'s alias of `ExtendableDataPoint`; left open by: A type name a form writes means the type the skill documents or the package exports under that name, and the source file's own declaration of it only when there is none, or when the file declares the name other than as an alias (a local `interface Options`); the other reading gives: Reading `DataPoint` as `ExtendableDataPoint` (cognee/low_level.py:2) gives a documented return that does not cover the base `DataPoint` the source declares. The source can return registered subclasses of the base and the `_DynamicDataPoint(DataPoint)` fallback, neither of which is an ExtendableDataPoint. That is a Critical mismatch on the return type, with no difference tag
- **Scoped Out by the Brief:** `describe_resolution` (cognee/shared/env_file.py:127), `load_env_file` (cognee/shared/env_file.py:112), `run_migrations` (cognee/run_migrations.py:18), `setup_logging` (cognee/shared/logging_utils.py:345), `start_visualization_server` (cognee/shared/utils.py:481), `wait_for_background_tasks` (cognee/infrastructure/background_tasks.py:66)
- **Nested Entry Points:** `cognee/api/v1/api_keys/routers/__init__.py` inside `cognee/__init__.py`: `get_api_key_management_router`; `cognee/api/v1/cloud/routers/__init__.py` inside `cognee/__init__.py`: `get_checks_router`; `cognee/api/v1/permissions/routers/__init__.py` inside `cognee/__init__.py`: `get_permissions_router`; `cognee/api/v1/settings/routers/__init__.py` inside `cognee/__init__.py`: `get_settings_router`
- **Extraction Gaps:** `COGXRecord` (cognee/modules/migration/cogx.py:160), `COGX_VERSION` (cognee/modules/migration/cogx.py:22), `Drop` (cognee/pipelines/types.py:32), `EXPORT_FORMATS` (cognee/modules/migration/export.py:35), `IMPORT_MODES` (cognee/modules/migration/sources/base.py:19), `MemoryEntry` (cognee/memory/entries.py:129), `logger` (cognee/__init__.py:34), `session` (cognee/api/v1/session/__init__.py:8)

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 100% |
| Signature Accuracy | 100% |
| Type Coverage | 100% |

**Notes:**

- Inventory (§1a): the inventory reader subagent listed 383 entries from SKILL.md and the four reference files; `validate-inventory.py` accepted it on the first pass (spot-check and floor check clean, all 47 floor names kept) with no warnings, so no form was left unbound for want of a place (`at`).
- Split-body cross-check (§1b): 156 names are written in two or more files; the reader found no split-body mismatch.
- Extraction (§2): the recipe runner read the source at the pinned commit ba3631f with no fallback, no file read by eye and none unread; no star re-export is unresolved.
- Signatures (§2): 39 signature-judge subagents compared 70 checks (93 documented forms); the 2 mismatches are `annotation-contradicted` on `run_tasks_parallel` (body returns `Task(...)` at cognee/modules/pipelines/operations/run_parallel.py:15), graded Info by `score-signatures.py`.
- Metadata counts (§4b): `stats.exports_public_api` = 102 against `exports[]` = 86 (16% drift, Medium `metadata-drift`); barrel 102 against documented 86 (Info `multi-denominator`). The numerator ground truth was skipped (no inflation signature).
- Provenance lines (§4c): every provenance-map line checked is a definition line (no `stale[]` item).

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)
**Migration Section:** Section 4b verification skipped: evidence-report.md pins no `t2_future_count`. For a skill create-skill made, re-run create-skill to regenerate the report with the field (create-stack-skill does not write it).

### Structural Findings

| # | Type | Severity | Detail | Line |
|---|------|----------|--------|------|
| - | none | - | Required sections served (`Overview` for description, `Quick Start` for usage, `Key API Summary` for API surface); fences balanced (6) with language tags; no table drift; no scripts/ or assets/ folder; every function and method export is referenced in a usage-family section or reference file; async/sync claims agree with every example call (27 called exports checked) | - |

**Structural Issues:** 0

### Reference Consistency (split-body)

| # | Reference File | Export | Issue | Other Side | Reference Line | Contradicted Side |
|---|---------------|--------|-------|------------|---------------|-------------------|
| - | - | - | none | - | - | - |

**Exports Cross-Checked:** 156
**Mismatches Found:** 0

## External Validation

### skill-check
- **Available:** yes
- **Quality Score:** 90/100
- **Errors:** 0
- **Warnings:** 1
- **Diagnostics:** `body.max_tokens` (warn) at skills/oms-cognee/1.6.2/oms-cognee/SKILL.md:1: body token estimate 5681 exceeds max 5000 (suggestion: reduce body to ~5000 tokens or fewer; token count is a whitespace-split approximation)

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
| Coherence | not scored | 0% | 0% |
| External Validation | 90% | 10% | 9% |
| **Total** | | **100%** | **99%** |

### Result

**Score:** 99%
**Threshold:** 80%
**Result:** **PASS**

**Threshold Source:** workflow default (80%)
**Weight Distribution:** naive (redistributed)
**Tier Adjustment:** none
**External Validators:** skill-check only (from `skill-check`; `tessl` is Tessl Review)
**Analysis Confidence:** full
**Tooling Status:** ok

## Gap Report

**Total Gaps:** 70
**Blocking (Critical + High):** 0
**Non-blocking (Medium + Low + Info):** 70

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|------------------|
| Critical | 0 | None |
| High | 0 | None |
| Medium | 4 | stale-documentation (3): check each name against the source and the brief's scope, then update or remove its documentation or fix the scope (Update Skill does not repair it); metadata-drift (1): re-run Create Skill or edit the brief's scope, as each remediation says (counts that differ only by `Type::method` entries need no fix, and a hand edit of the counts does not hold) |
| Low | 1 | external-validator (1): apply each skill-check diagnostic or Tessl Review suggestion to SKILL.md as its remediation says |
| Info | 65 | observation (64): apply each only when you agree, as its remediation says, since it is advisory (a documented extra needs no change); multi-denominator (1): none, since the barrel and the documented surface measure different sets by design |
| **Total** | **70** | |

### GAP-055: Stale documentation: run_migrations

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:148
**Export:** run_migrations

**Issue:** `SKILL.md:148` documents `run_migrations`, which the entry point `cognee/__init__.py` exports and `cognee/run_migrations.py:18` defines, a file `forge-data/oms-cognee/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `run_migrations` belongs on the surface: `forge-data/oms-cognee/skill-brief.yaml` scopes out `cognee/run_migrations.py:18`, where it is defined, since no `scope.include` glob covers that file and its `scope.exclude` glob `cognee/run_migrations.py` matches it. To keep its documentation, widen `scope.include` to cover that file and narrow `cognee/run_migrations.py` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `run_migrations` at SKILL.md:148.

### GAP-058: Stale documentation: setup_logging

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:28
**Export:** setup_logging

**Issue:** `SKILL.md:28` documents `setup_logging`, which the entry point `cognee/__init__.py` exports and `cognee/shared/logging_utils.py:345` defines, a file `forge-data/oms-cognee/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `setup_logging` belongs on the surface: `forge-data/oms-cognee/skill-brief.yaml` scopes out `cognee/shared/logging_utils.py:345`, where it is defined, since no `scope.include` glob covers that file and its `scope.exclude` glob `cognee/shared/**` matches it. To keep its documentation, widen `scope.include` to cover that file and narrow `cognee/shared/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `setup_logging` at SKILL.md:28.

### GAP-067: Stale documentation: wait_for_background_tasks

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:157
**Export:** wait_for_background_tasks

**Issue:** `SKILL.md:157` documents `wait_for_background_tasks`, which the entry point `cognee/__init__.py` exports and `cognee/infrastructure/background_tasks.py:66` defines, a file `forge-data/oms-cognee/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `wait_for_background_tasks` belongs on the surface: `forge-data/oms-cognee/skill-brief.yaml` scopes out `cognee/infrastructure/background_tasks.py:66`, where it is defined, since no `scope.include` glob covers that file and its `scope.exclude` glob `cognee/infrastructure/**` matches it. To keep its documentation, widen `scope.include` to cover that file and narrow `cognee/infrastructure/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `wait_for_background_tasks` at SKILL.md:157.

### GAP-068: metadata drift — barrel export counts diverge

**Severity:** Medium
**Category:** Coverage (metadata-drift)
**Source:** skills/oms-cognee/1.6.2/oms-cognee/metadata.json

**Issue:** stats.exports_public_api=102, exports[].length=86 → 16% drift

**Remediation:** Re-run Create Skill, which rebuilds `exports[]` and `stats.exports_public_api` in `skills/oms-cognee/1.6.2/oms-cognee/metadata.json` from the source. Update Skill does not repair this drift: each time it writes the skill it recounts `stats.exports_public_api` from the source and keeps `exports[]`, adding or dropping only the names its provenance map changes, so a metadata patch does not hold.

### GAP-070: skill-check: body.max_tokens

**Severity:** Low
**Category:** External (external-validator)
**Source:** SKILL.md:1

**Issue:** body token estimate 5681 exceeds max 5000

**Remediation:** Reduce the body of skills/oms-cognee/1.6.2/oms-cognee/SKILL.md to about 5000 tokens or fewer (skill-check's whitespace-split estimate), moving detail into the references/ files it already links.

### GAP-001: Annotation contradicted: run_tasks_parallel (form 1 of 2)

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/operations/run_parallel.py:8
**Export:** run_tasks_parallel

**Issue:** the source annotates the return of `run_tasks_parallel` otherwise than the skill documents, and its body returns the documented type at `cognee/modules/pipelines/operations/run_parallel.py:15`: documented `(tasks) -> Task`, source `(tasks: list[Task]) -> Callable[[Any], Generator[Any, Any, Any]]`: documented return type 'Task' differs from the declared annotation 'Callable[[Any], Generator[Any, Any, Any]]', but the body returns Task(parallel_run) at line 15 (Task imported from ..tasks.task, the runtime Task the skill documents); the bare name 'tasks' is not compared on type (documented form 1 of 2: `(tasks) -> Task`)

**Remediation:** No change to the skill: it documents what `run_tasks_parallel` returns, as `cognee/modules/pipelines/operations/run_parallel.py:15` shows. Report the return annotation at `cognee/modules/pipelines/operations/run_parallel.py:8` upstream, since the body contradicts it.

### GAP-002: Annotation contradicted: run_tasks_parallel (form 2 of 2)

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/operations/run_parallel.py:8
**Export:** run_tasks_parallel

**Issue:** the source annotates the return of `run_tasks_parallel` otherwise than the skill documents, and its body returns the documented type at `cognee/modules/pipelines/operations/run_parallel.py:15`: documented `(tasks: list[Task]) -> Task`, source `(tasks: list[Task]) -> Callable[[Any], Generator[Any, Any, Any]]`: documented return type 'Task' differs from the declared annotation 'Callable[[Any], Generator[Any, Any, Any]]', but the body returns Task(parallel_run) at line 15 (Task imported from ..tasks.task, the runtime Task the skill documents); parameters match (documented form 2 of 2: `(tasks: list[Task]) -> Task`)

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

### GAP-010: Documented extra: Dedup

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/infrastructure/engine/models/FieldAnnotations.py:82
**Export:** Dedup

**Issue:** `references/pipelines-and-datapoints.md:337` documents `Dedup`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Dedup` is a documented extra, a name the source still declares at `cognee/infrastructure/engine/models/FieldAnnotations.py:82` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-011: Documented extra: DistillationResult

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/session_distillation/models.py:94
**Export:** DistillationResult

**Issue:** `references/full-api-reference.md:397` documents `DistillationResult`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `DistillationResult` is a documented extra, a name the source still declares at `cognee/modules/session_distillation/models.py:94` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-012: Documented extra: Edge

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/migration/formats.py:15
**Export:** Edge

**Issue:** `SKILL.md:221` documents `Edge`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Edge` is a documented extra, a name the source still declares at `cognee/modules/migration/formats.py:15` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-013: Documented extra: Embeddable

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/infrastructure/engine/models/FieldAnnotations.py:56
**Export:** Embeddable

**Issue:** `references/pipelines-and-datapoints.md:337` documents `Embeddable`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `Embeddable` is a documented extra, a name the source still declares at `cognee/infrastructure/engine/models/FieldAnnotations.py:56` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-014: Documented extra: EntitySpec

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/graph_models/spec.py:90
**Export:** EntitySpec

**Issue:** `references/full-api-reference.md:282` documents `EntitySpec`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `EntitySpec` is a documented extra, a name the source still declares at `cognee/modules/graph_models/spec.py:90` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-015: Documented extra: ExtendableDataPoint

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/infrastructure/engine/models/ExtendableDataPoint.py:4
**Export:** ExtendableDataPoint

**Issue:** `SKILL.md:282` documents `ExtendableDataPoint`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ExtendableDataPoint` is a documented extra, a name the source still declares at `cognee/infrastructure/engine/models/ExtendableDataPoint.py:4` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-016: Documented extra: FromIdentity

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/infrastructure/engine/models/FieldAnnotations.py:95
**Export:** FromIdentity

**Issue:** `SKILL.md:221` documents `FromIdentity`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `FromIdentity` is a documented extra, a name the source still declares at `cognee/infrastructure/engine/models/FieldAnnotations.py:95` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-017: Documented extra: GraphSchemaSpec

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/graph_models/spec.py:108
**Export:** GraphSchemaSpec

**Issue:** `references/full-api-reference.md:282` documents `GraphSchemaSpec`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `GraphSchemaSpec` is a documented extra, a name the source still declares at `cognee/modules/graph_models/spec.py:108` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-018: Documented extra: INTERNAL_PROPERTY

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/infrastructure/engine/models/InternalDataPoint.py:18
**Export:** INTERNAL_PROPERTY

**Issue:** `references/pipelines-and-datapoints.md:337` documents `INTERNAL_PROPERTY`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `INTERNAL_PROPERTY` is a documented extra, a name the source still declares at `cognee/infrastructure/engine/models/InternalDataPoint.py:18` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-019: Documented extra: ImproveKwargs

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/improve/improve.py:88
**Export:** ImproveKwargs

**Issue:** `SKILL.md:159` documents `ImproveKwargs`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ImproveKwargs` is a documented extra, a name the source still declares at `cognee/api/v1/improve/improve.py:88` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-020: Documented extra: InternalDataPoint

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/infrastructure/engine/models/InternalDataPoint.py:21
**Export:** InternalDataPoint

**Issue:** `references/pipelines-and-datapoints.md:337` documents `InternalDataPoint`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `InternalDataPoint` is a documented extra, a name the source still declares at `cognee/infrastructure/engine/models/InternalDataPoint.py:21` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-021: Documented extra: LLMContext

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/infrastructure/engine/models/FieldAnnotations.py:69
**Export:** LLMContext

**Issue:** `references/pipelines-and-datapoints.md:337` documents `LLMContext`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LLMContext` is a documented extra, a name the source still declares at `cognee/infrastructure/engine/models/FieldAnnotations.py:69` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-022: Documented extra: LLMGateway

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/infrastructure/llm/LLMGateway.py:106
**Export:** LLMGateway

**Issue:** `references/pipelines-and-datapoints.md:418` documents `LLMGateway`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LLMGateway` is a documented extra, a name the source still declares at `cognee/infrastructure/llm/LLMGateway.py:106` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-023: Documented extra: PipelineContext

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/models/PipelineContext.py:6
**Export:** PipelineContext

**Issue:** `references/full-api-reference.md:553` documents `PipelineContext`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PipelineContext` is a documented extra, a name the source still declares at `cognee/modules/pipelines/models/PipelineContext.py:6` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-024: Documented extra: PipelineRunCompleted

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/models/PipelineRunInfo.py:34
**Export:** PipelineRunCompleted

**Issue:** `references/full-api-reference.md:267` documents `PipelineRunCompleted`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PipelineRunCompleted` is a documented extra, a name the source still declares at `cognee/modules/pipelines/models/PipelineRunInfo.py:34` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-025: Documented extra: PipelineRunErrored

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/models/PipelineRunInfo.py:42
**Export:** PipelineRunErrored

**Issue:** `references/core-workflow.md:100` documents `PipelineRunErrored`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PipelineRunErrored` is a documented extra, a name the source still declares at `cognee/modules/pipelines/models/PipelineRunInfo.py:42` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-026: Documented extra: PipelineRunInfo

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/models/PipelineRunInfo.py:9
**Export:** PipelineRunInfo

**Issue:** `references/full-api-reference.md:566` documents `PipelineRunInfo`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PipelineRunInfo` is a documented extra, a name the source still declares at `cognee/modules/pipelines/models/PipelineRunInfo.py:9` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-027: Documented extra: PipelineRunStarted

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/models/PipelineRunInfo.py:26
**Export:** PipelineRunStarted

**Issue:** `references/full-api-reference.md:267` documents `PipelineRunStarted`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PipelineRunStarted` is a documented extra, a name the source still declares at `cognee/modules/pipelines/models/PipelineRunInfo.py:26` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-028: Documented extra: REMEDIATION_MARKER

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/remediation.py:52
**Export:** REMEDIATION_MARKER

**Issue:** `SKILL.md:294` documents `REMEDIATION_MARKER`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `REMEDIATION_MARKER` is a documented extra, a name the source still declares at `cognee/exceptions/remediation.py:52` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-029: Documented extra: RememberKwargs

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/remember/remember.py:90
**Export:** RememberKwargs

**Issue:** `SKILL.md:156` documents `RememberKwargs`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `RememberKwargs` is a documented extra, a name the source still declares at `cognee/api/v1/remember/remember.py:90` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-030: Documented extra: SkillRunEntry

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/memory/entries.py:82
**Export:** SkillRunEntry

**Issue:** `SKILL.md:280` documents `SkillRunEntry`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `SkillRunEntry` is a documented extra, a name the source still declares at `cognee/memory/entries.py:82` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-031: Documented extra: TaskSpec

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/tasks/task.py:35
**Export:** TaskSpec

**Issue:** `references/pipelines-and-datapoints.md:36` documents `TaskSpec`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `TaskSpec` is a documented extra, a name the source still declares at `cognee/modules/pipelines/tasks/task.py:35` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-032: Documented extra: UpdateResult

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/update/result.py:37
**Export:** UpdateResult

**Issue:** `references/core-workflow.md:390` documents `UpdateResult`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `UpdateResult` is a documented extra, a name the source still declares at `cognee/api/v1/update/result.py:37` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-033: Documented extra: WRITE_PIPELINE_NAMES

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/improve/graph_changes.py:39
**Export:** WRITE_PIPELINE_NAMES

**Issue:** `references/full-api-reference.md:271` documents `WRITE_PIPELINE_NAMES`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `WRITE_PIPELINE_NAMES` is a documented extra, a name the source still declares at `cognee/modules/improve/graph_changes.py:39` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-034: Documented extra: __version__

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/__init__.py:22
**Export:** __version__

**Issue:** `SKILL.md:149` documents `__version__`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `__version__` is a documented extra, a name the source still declares at `cognee/__init__.py:22` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-035: Documented extra: add_data_points

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/tasks/storage/add_data_points.py:70
**Export:** add_data_points

**Issue:** `references/core-workflow.md:199` documents `add_data_points`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `add_data_points` is a documented extra, a name the source still declares at `cognee/tasks/storage/add_data_points.py:70` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-036: Documented extra: add_feedback

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/session/session.py:113
**Export:** add_feedback

**Issue:** `SKILL.md:147` documents `add_feedback`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `add_feedback` is a documented extra, a name the source still declares at `cognee/api/v1/session/session.py:113` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-037: Documented extra: delete_feedback

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/session/session.py:147
**Export:** delete_feedback

**Issue:** `SKILL.md:147` documents `delete_feedback`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `delete_feedback` is a documented extra, a name the source still declares at `cognee/api/v1/session/session.py:147` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-038: Documented extra: distill_session

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/session_distillation/distill.py:471
**Export:** distill_session

**Issue:** `SKILL.md:147` documents `distill_session`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `cognee/modules/session_distillation/distill.py`

**Remediation:** No change: `distill_session` is a documented extra, a name the source still declares at `cognee/modules/session_distillation/distill.py:471` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-039: Documented extra: exceptions

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/__init__.py:1
**Export:** exceptions

**Issue:** `SKILL.md:286` documents `exceptions`, which the enumerated source API surface lacks and the source still declares; of the 7 files that declare it, the skill cites only the package `cognee/exceptions/__init__.py` and its same-named module `cognee/exceptions/exceptions.py`, so the gap is at the package

**Remediation:** No change: `exceptions` is a documented extra, a name the source still declares at `cognee/exceptions/__init__.py:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-040: Documented extra: find_remediation

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/remediation.py:131
**Export:** find_remediation

**Issue:** `SKILL.md:294` documents `find_remediation`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `find_remediation` is a documented extra, a name the source still declares at `cognee/exceptions/remediation.py:131` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-041: Documented extra: get_default_tasks

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/cognify/cognify.py:565
**Export:** get_default_tasks

**Issue:** `references/core-workflow.md:183` documents `get_default_tasks`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_default_tasks` is a documented extra, a name the source still declares at `cognee/api/v1/cognify/cognify.py:565` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-042: Documented extra: get_errored_run_info

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/models/PipelineRunInfo.py:62
**Export:** get_errored_run_info

**Issue:** `references/full-api-reference.md:574` documents `get_errored_run_info`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_errored_run_info` is a documented extra, a name the source still declares at `cognee/modules/pipelines/models/PipelineRunInfo.py:62` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-043: Documented extra: get_session

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/session/session.py:65
**Export:** get_session

**Issue:** `SKILL.md:147` documents `get_session`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_session` is a documented extra, a name the source still declares at `cognee/api/v1/session/session.py:65` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-044: Documented extra: graph_model_from_spec

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/graph_models/compiler.py:135
**Export:** graph_model_from_spec

**Issue:** `references/full-api-reference.md:282` documents `graph_model_from_spec`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `graph_model_from_spec` is a documented extra, a name the source still declares at `cognee/modules/graph_models/compiler.py:135` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-045: Documented extra: graph_model_to_graph_schema

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/shared/graph_model_utils.py:93
**Export:** graph_model_to_graph_schema

**Issue:** `references/full-api-reference.md:282` documents `graph_model_to_graph_schema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `graph_model_to_graph_schema` is a documented extra, a name the source still declares at `cognee/shared/graph_model_utils.py:93` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-046: Documented extra: graph_schema_to_graph_model

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/shared/graph_model_utils.py:44
**Export:** graph_schema_to_graph_model

**Issue:** `references/full-api-reference.md:282` documents `graph_schema_to_graph_model`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `graph_schema_to_graph_model` is a documented extra, a name the source still declares at `cognee/shared/graph_model_utils.py:44` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-047: Documented extra: graph_spec_to_json_schema

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/graph_models/compiler.py:119
**Export:** graph_spec_to_json_schema

**Issue:** `references/full-api-reference.md:282` documents `graph_spec_to_json_schema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `graph_spec_to_json_schema` is a documented extra, a name the source still declares at `cognee/modules/graph_models/compiler.py:119` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-048: Documented extra: is_internal_node

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/infrastructure/engine/models/InternalDataPoint.py:27
**Export:** is_internal_node

**Issue:** `references/pipelines-and-datapoints.md:337` documents `is_internal_node`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `is_internal_node` is a documented extra, a name the source still declares at `cognee/infrastructure/engine/models/InternalDataPoint.py:27` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-049: Documented extra: is_tracing_enabled

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/observability/trace_context.py:62
**Export:** is_tracing_enabled

**Issue:** `references/full-api-reference.md:304` documents `is_tracing_enabled`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `is_tracing_enabled` is a documented extra, a name the source still declares at `cognee/modules/observability/trace_context.py:62` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-050: Documented extra: low_level

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/low_level.py:1
**Export:** low_level

**Issue:** `references/full-api-reference.md:275` documents `low_level`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `low_level` is a documented extra, a name the source still declares at `cognee/low_level.py:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-051: Documented extra: migration

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/migration/__init__.py:1
**Export:** migration

**Issue:** `SKILL.md:185` documents `migration`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `cognee/migration/__init__.py`

**Remediation:** No change: `migration` is a documented extra, a name the source still declares at `cognee/migration/__init__.py:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-052: Documented extra: pipeline_needs_llm

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/tasks/task.py:160
**Export:** pipeline_needs_llm

**Issue:** `SKILL.md:268` documents `pipeline_needs_llm`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `pipeline_needs_llm` is a documented extra, a name the source still declares at `cognee/modules/pipelines/tasks/task.py:160` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-053: Documented extra: pipelines

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/__init__.py:1
**Export:** pipelines

**Issue:** `SKILL.md:145` documents `pipelines`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `pipelines` is a documented extra, a name the source still declares at `cognee/modules/pipelines/__init__.py:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-054: Documented extra: remediation_for

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/remediation.py:146
**Export:** remediation_for

**Issue:** `SKILL.md:294` documents `remediation_for`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `remediation_for` is a documented extra, a name the source still declares at `cognee/exceptions/remediation.py:146` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-056: Documented extra: run_relational_migrations

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/run_migrations.py:11
**Export:** run_relational_migrations

**Issue:** `references/full-api-reference.md:409` documents `run_relational_migrations`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `cognee/run_migrations.py`

**Remediation:** No change: `run_relational_migrations` is a documented extra, a name the source still declares at `cognee/run_migrations.py:11` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-057: Documented extra: setup

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/engine/operations/setup.py:9
**Export:** setup

**Issue:** `SKILL.md:221` documents `setup`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `setup` is a documented extra, a name the source still declares at `cognee/modules/engine/operations/setup.py:9` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-059: Documented extra: start_visualization_server

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/visualize/start_visualization_server.py:1
**Export:** start_visualization_server

**Issue:** `SKILL.md:29` documents `start_visualization_server`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `start_visualization_server` is a documented extra, a name the source still declares at `cognee/api/v1/visualize/start_visualization_server.py:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-060: Documented extra: task

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/tasks/task.py:124
**Export:** task

**Issue:** `references/pipelines-and-datapoints.md:35` documents `task`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `task` is a documented extra, a name the source still declares at `cognee/modules/pipelines/tasks/task.py:124` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-061: Documented extra: task_summary

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/tasks/task.py:169
**Export:** task_summary

**Issue:** `references/pipelines-and-datapoints.md:36` documents `task_summary`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `task_summary` is a documented extra, a name the source still declares at `cognee/modules/pipelines/tasks/task.py:169` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-062: Documented extra: tools

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/tools/tools.py:1
**Export:** tools

**Issue:** `SKILL.md:181` documents `tools`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `tools` is a documented extra, a name the source still declares at `cognee/api/v1/tools/tools.py:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-063: Documented extra: use_vector_adapter

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/infrastructure/databases/vector/use_vector_adapter.py:4
**Export:** use_vector_adapter

**Issue:** `references/config.md:55` documents `use_vector_adapter`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `use_vector_adapter` is a documented extra, a name the source still declares at `cognee/infrastructure/databases/vector/use_vector_adapter.py:4` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-064: Documented extra: visualize_graph_json

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/visualize/visualize.py:271
**Export:** visualize_graph_json

**Issue:** `references/full-api-reference.md:337` documents `visualize_graph_json`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `visualize_graph_json` is a documented extra, a name the source still declares at `cognee/api/v1/visualize/visualize.py:271` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-065: Documented extra: visualize_multi_user_graph

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/visualize/visualize.py:611
**Export:** visualize_multi_user_graph

**Issue:** `references/full-api-reference.md:339` documents `visualize_multi_user_graph`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `visualize_multi_user_graph` is a documented extra, a name the source still declares at `cognee/api/v1/visualize/visualize.py:611` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-066: Documented extra: visualize_semantic_json

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/visualize/visualize.py:317
**Export:** visualize_semantic_json

**Issue:** `references/full-api-reference.md:338` documents `visualize_semantic_json`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `visualize_semantic_json` is a documented extra, a name the source still declares at `cognee/api/v1/visualize/visualize.py:317` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-069: multi-denominator reporting — barrel vs documented surface

**Severity:** Info
**Category:** Coverage (multi-denominator)
**Source:** skills/oms-cognee/1.6.2/oms-cognee/metadata.json

**Issue:** barrel=102, documented=86

**Remediation:** No action required: the barrel and the documented surface measure different sets by design, and the report records both counts.

### Discovery Quality

**Discovery Test:** PASS (3/3)

| # | Prompt | Selected Skill | Result |
|---|--------|----------------|--------|
| 1 | can you help me with these support transcripts my boss sent? I want our assistant to keep them as long-term memory and pull up the relevant bits when a customer asks something | oms-cognee (high) | PASS |
| 2 | why does my agent lose everything a customer told it once the chat ends? I need it to hold on to what each customer said across conversations, kept separate per customer | oms-cognee (high) | PASS |
| 3 | run the memory thing on this folder of PDFs so my agent can answer questions about the people and companies in them and how they're linked | oms-cognee (high) | PASS |

Catalog: the 4 skills in `skills/` (oms-cocoindex, oms-cognee, oms-storybook-react-vite, oms-uitripled), each with its frontmatter description. SKILL.md holds no conversational prompt (its Common Workflows labels name exports), so the three prompts were synthesized by the vague, implicit and abbreviated patterns, naming no export, skill or library. Each went to an isolated subagent with no prior context and no file or shell tools (WebFetch only; it used none).
