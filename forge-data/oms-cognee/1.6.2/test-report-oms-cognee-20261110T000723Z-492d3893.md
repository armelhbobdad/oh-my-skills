---
workflowType: 'test-skill'
skillName: 'oms-cognee'
skillDir: 'skills/oms-cognee/1.6.2/oms-cognee'
runId: '20261110T000723Z-492d3893'
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
testDate: '2026-11-10T00:07:23Z'
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

**Mode Rationale:** metadata.json sets `skill_type: 'single'`: an individual skill, so naive mode applies (API-surface coverage; coherence is structural only and is not a scored category).

**Analysis Plan:**
- Coverage Check: every public export of cognee v1.6.2 (`cognee/__init__.py` at ba3631f, the pinned commit) checked for documentation in SKILL.md and references/; Deep tier, so signatures and types are compared against the AST-backed source with the inventory reader and signature-judge subagents.
- Coherence Check: structural only (naive mode): references named in SKILL.md resolve, and the documented examples and sections are internally consistent.

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
- **Stale Documentation:** 61, documented extras included
- **Scoring Warnings:**
  - Type Coverage leaves out each name the stale-scope guard restored or the extraction recorded with no kind, such as an extraction gap (the provenance map, when one is given, gives it no kind Type Coverage reads at its file): `session`
- **Borderline Calls:**
  - `get_memory_provenance_graph` (SKILL.md:179), inventory reader: the Key params column is read as a Params column by its role, not a description cell, so a bare name and parameter group it writes for its row (get_memory_provenance_graph(include_memory=False, ...) -> (nodes, edges), visualize_memory_provenance(...), ValidationReport(*, ...), ValidationIssue(*, ...)) is a signature kept in params, as inventory-floor.json reads the same shape at SKILL.md:191-213; left open by: A description cell is any table cell but an export table's first cell and a cell whose column writes the call or signature, by its role (Signature, Props, Params, Parameters, Arguments, Usage, Syntax, Example and the like); a heading or an export table's first cell that writes `name()` is a form, recorded as written; the other reading gives: read as a description cell, (nodes, edges) states no return type, so get_memory_provenance_graph's form would be a call recorded in usage_signature; no gap either way, since both readings are partial under the Key params header
  - `wait_for_background_tasks` (SKILL.md:157), inventory reader: the prose sentences inside a Key params cell are read as running text, so await cognee.wait_for_background_tasks() is a mention; its entry (the only place that documents it, since references/full-api-reference.md:622 says it is not covered) carries no form; left open by: A name written with empty parentheses, or with only `...` or `…` between them, in running text or a description cell is a mention, not a form, whatever comes before the name (`await`, `new`, an assignment, a receiver or a module path): its entry leaves `params` and `usage_signature` out; the other reading gives: read as an empty call in a call column, usage_signature await cognee.wait_for_background_tasks(): a Critical signature-mismatch only if the source requires a parameter, otherwise no gap
  - `setup_logging` (SKILL.md:183), inventory reader: logger = setup_logging() inside the logger row's Key params prose is a mention; setup_logging still gets an entry at SKILL.md:183 because that cell describes it, while SKILL.md:28 only says it is out of scope; left open by: A name written with empty parentheses, or with only `...` or `…` between them, in running text or a description cell is a mention, not a form, whatever comes before the name (`await`, `new`, an assignment, a receiver or a module path): its entry leaves `params` and `usage_signature` out; the other reading gives: an empty-call usage logger = setup_logging(): a Critical signature-mismatch only if setup_logging requires a parameter, otherwise no gap
  - `prune_data` (SKILL.md:139), inventory reader: owner prune: .prune_data() and .prune_system(...) are the prune row's method list in the Key params (params) column, so each is a form recorded as a usage through its receiver (the leading dot kept as written), and the fenced calls at SKILL.md:41-42 and references/full-api-reference.md:383-384 give no entry; left open by: An empty call `X()` written as a call example (in a heading, an export table's first cell, a call or signature column or a fenced example, never a mention) is one too, so it matches a source whose parameters are all optional; the other reading gives: read as mentions, the fenced example calls await cognee.prune.prune_data() / prune_system(...) would be their only forms and give the entries; no gap either way unless prune_data requires a parameter
  - `visualize` (SKILL.md:29), inventory reader: the YAML frontmatter (SKILL.md:1-17) is read as metadata, not a place, and an export-table row that writes no form is one more no-form place, so names with no form anywhere take their lowest body line: SKILL.md:29 for visualize, pipelines, tools, session, Drop, DataPoint, MemoryEntry and start_visualization_server, SKILL.md:28 for __version__, logger and migration, SKILL.md:110 for CogneeConfigurationError; left open by: A place that writes a name but no form of it, and no `methods`, `properties` or `fields` its entry would carry (a mention, a bare code span, an import, a heading or prose that names or describes it), gives it no entry when another place gives the name one, unless `inventory-floor.json` gives that place; of several such places of a name the skill documents and no other place gives an entry, the first alone gives one: in SKILL.md, else the file that sorts first by path, at its lowest line; the other reading gives: no gap: counting the frontmatter would move several entries to SKILL.md:13-15, and taking the export-table row as the documenting place would move them to the row (e.g. SKILL.md:163); only the line a stale-name gap cites changes
  - `get_session` (references/full-api-reference.md:394), inventory reader: cognee.session is a types.SimpleNamespace, neither a module nor a class; its four helpers (get_session, add_feedback, delete_feedback, distill_session), which the skill calls async functions importable from cognee.api.v1.session, are recorded as functions named bare; left open by: A function the skill documents in a module is a `function` named bare, never a `method`, even when it is called through the module's name (`register_sql_connection` for `cognee.tools.register_sql_connection`, where the skill documents `tools` as a module); the other reading gives: as methods with owner session, the split-body Source would look for a member of the namespace object; no signature gap expected either way
  - `pipelines` (SKILL.md:29), inventory reader: no kind names a module, so the modules the skill documents (pipelines, tools, migration, start_visualization_server) and the SimpleNamespace session are recorded as constant, with no form; left open by: The contract `validate-inventory.py` checks (coverage-check.md §1a): each `kind` is one of `function`, `class`, `type`, `constant`, `hook`, `interface`, `method`, `struct`, `enum`, `trait`, `macro` or `adapter`; the other reading gives: no gap: none of them carries a compared form
  - `QAEntry` (references/full-api-reference.md:580), inventory reader: a model's field list written as separate code spans in prose is no parameter list, so it is kept in properties, uncompared: QAEntry, TraceEntry, FeedbackEntry (580-582), ValidationReport and ValidationIssue (487-488), PushResult (474), ExportResult (455), SessionRecord and SessionModelUsage (588-589), DistillationResult (397) and Task's attributes (549-553); left open by: while a class's form written as a parameter list or a signature that is not such a call stays in `params`; the other reading gives: read as the model's constructor in params, a typed field list claims to be complete: a field it leaves out, or one the source lacks, would be a Critical signature-mismatch
  - `GraphitiSource` (SKILL.md:195), inventory reader: ZepSource(data, mode="hybrid"), quoted in GraphitiSource's row as the constructor it shares, is a call of ZepSource's own name, so it is a ZepSource usage at SKILL.md:195 and GraphitiSource's entry there carries no form; left open by: A function's, a method's or a class's form the skill writes as a call expression of its own name (after `await`, `new` or an assignment, through a receiver or module path such as `coco.`, or as a statement in a fenced example; in running text or a description cell, only a call that passes an argument and writes no parameter type, `?`, bare `*` or `/`, with or without such a prefix, and no return type unless such a prefix comes before the name, such as `add(componentName, options)` or `await coco.mount(fn) -> Handle`), at a place `inventory-floor.json` gives no `signature` (below), is recorded whole in `usage_signature`; the other reading gives: read as GraphitiSource's own constructor, params data, mode="hybrid" on GraphitiSource, compared with its inherited ZepSource constructor (no gap expected), and no ZepSource entry at line 195
  - `add` (SKILL.md:95), inventory reader: the arrows chaining the Common Workflows calls (add -> cognify -> search at 95 and 101, remember -> recall at 98, add -> cognify -> memify at 104) are workflow arrows, not return types, so each call is recorded as a usage with no return_type; left open by: in running text or a description cell, only a call that passes an argument and writes no parameter type, `?`, bare `*` or `/`, with or without such a prefix, and no return type unless such a prefix comes before the name; the other reading gives: read as return types, add would carry return_type await cognee.cognify(...), which names no type and is compared as none; no gap either way
  - `remember` (SKILL.md:125), inventory reader: each call a place writes is recorded as a form of its own: three remember calls and two export calls at SKILL.md:125, two Task calls at SKILL.md:116; left open by: A name documented in several places is listed once per place (`Card` above), and once per form at a place that writes several of its forms (two overloads in one row), each entry with that place as its `at`; the other reading gives: no gap: one entry per place would drop calls of the same shape, which compare the same way
  - `set` (references/config.md:98), inventory reader: owner config: cognee.config.set(key: str, value, persist: bool = False) in a fenced block writes parameter types, which no call writes, so it is read as a signature kept in params, as are cognee.config.get(...) and cognee.config.get_all(...) -> dict at config.md:112-113; left open by: A function's, a method's or a class's form the skill writes as a call expression of its own name (after `await`, `new` or an assignment, through a receiver or module path such as `coco.`, or as a statement in a fenced example; ...) ... is recorded whole in `usage_signature`; the other reading gives: read as a fenced-example call, it would be a usage compared as a call (an optional parameter it leaves out is no difference); as a typed signature it claims to be complete, so a parameter the source adds would be an omitted-optional Critical signature-mismatch
  - `start_ui` (SKILL.md:230), inventory reader: the bullet's prose 'the function returns Optional[subprocess.Popen] synchronously' is a return type the skill writes for start_ui at that place, so the Signature: start_ui(...) usage carries return_type Optional[subprocess.Popen]; left open by: is recorded whole in `usage_signature`, as `inventory-floor.json` writes a usage (an assignment, `await`, `new`, a receiver or module path before the name kept, through the call's closing parenthesis or the element's end, never an `@`, a `with` or text after the call), never in `params`, whatever names its arguments use, and a return type the skill writes for it in `return_type`; the other reading gives: left out, the return would not be compared; kept, a source return other than Optional[subprocess.Popen] would be a signature-mismatch
  - `task` (references/pipelines-and-datapoints.md:129), inventory reader: 'task(fn=None, *, ...) returns a TaskSpec' documents the return in the same sentence as the form, so the entry carries return_type TaskSpec; left open by: a function or method carries `params` (`""` or `[]` when it takes none; any list `params` holds the members of one parameter list, one per item, never one form per item) and `return_type` as the skill documents them, and leaves a key out when the skill documents nothing for it; the other reading gives: read as prose about the result, no return_type and the return uncompared; with it, a source return annotation other than TaskSpec would be a signature-mismatch
  - `update`, inventory reader: update's row writes data_id, data and dataset_id as separate code spans described as required, not as a parameter list, so its form writes only -> dict and is a return-only entry with no at; left open by: a form that writes only a `return_type` gives no `at`, so it is compared as one whose citations name no declaration; the other reading gives: read as a list of bare names data_id, data, dataset_id at SKILL.md:137, compared as names that need not be complete: no gap, since all three are update's required parameters
  - `cognify`, inventory reader: cognify's row writes no parameter list but writes -> {dataset_id: PipelineRunInfo} ... or DryRunEstimate with dry_run=True, so it is a return-only entry with no at; left open by: a form that writes only a `return_type` gives no `at`, so it is compared as one whose citations name no declaration; the other reading gives: read as prose about the result, no entry from SKILL.md:134; no gap either way, since no reference form writes a return for cognify and its source return is unannotated
  - `DataPoint` (SKILL.md:29), inventory reader: the skill presents DataPoint both as cognee.low_level's alias of ExtendableDataPoint and as the base class cognee.infrastructure.engine exports under that name (SKILL.md:284), so it is not only an alias and takes the general first-place rule's lowest body line, SKILL.md:29; left open by: A name the skill presents only as a local import alias of another name, or says the source does not export, is not an export the skill documents either: it gets an entry only from a place `inventory-floor.json` gives it, a heading, an export table's first cell or a fenced declaration of it (an import is not one), never from a code span in prose or a description cell; the other reading gives: read as an alias only, its entry would come from the heading at SKILL.md:282; no gap either way, only the cited line changes
  - `validate_provider_config` (references/core-workflow.md:105), inventory reader: internal helpers named only as steps of an internal flow (validate_provider_config(needs_llm=False), raise_if_cognify_errored(result), validate_pipeline_tasks(tasks), setup_and_check_environment(...), resolve_authorized_user_datasets(...), generate_pipeline_id(...), get_pipeline_executor(...), authorized_search, get_graph_data()) and result or error types named only as what a call returns or raises (ImproveResult, CloudClient, SearchResult, RecallResponse, DryRunEstimate, PresortReport, MigrationError, DatasetNotFoundError and the like) are read as not documented exports and get no entry; left open by: The JSON coverage-check.md §1's reader writes to `{run_dir}/inventory-response.txt`: every export the skill documents, in this shape; the other reading gives: given entries, their calls would be compared with their declarations (a Critical signature-mismatch where a call passes an argument the helper lacks) and a name the surface lacks would draw a stale-name gap
  - `InternalDataPoint` (references/pipelines-and-datapoints.md:337), inventory reader: names a sentence lists as what a module provides (cognee.infrastructure.engine's InternalDataPoint, INTERNAL_PROPERTY, is_internal_node, Embeddable, Dedup and LLMContext; cognee.low_level's EntitySpec, GraphSchemaSpec and lazy graph_schema_to_graph_model / graph_model_to_graph_schema; use_vector_adapter at config.md:55) are read as exports the skill documents, each an entry with no form; left open by: The JSON coverage-check.md §1's reader writes to `{run_dir}/inventory-response.txt`: every export the skill documents, in this shape; the other reading gives: read as mere mentions, no entry: no gap, except a stale-name gap such an entry could draw if the source lacks the name
  - `run_pipeline` (references/pipelines-and-datapoints.md:199), inventory reader: the Usage pattern call at pipelines-and-datapoints.md:199 and the orchestrator declaration at 155 (its Provenance at 187 citing operations/pipeline.py) are attributed, by their section and its import from cognee.modules.pipelines, to the orchestrator, which the skill presents as a different function from the lightweight runner (full-api-reference.md:264 and pipelines-and-datapoints.md:208, citing operations/run_pipeline.py), so the two run_pipeline declarations' forms are never paired and no cross_check_mismatches entry is recorded; left open by: A judge without the surface (coverage-check.md §1's reader) counts two declarations only when the two forms' own citations name two different files and the skill presents the forms as different things (another owner, module or import path); a citation of a re-export (a package `__init__` or index file the skill shows passing the name on) names no declaration, and when unsure the forms are compared as before; the other reading gives: compared as one export, run_pipeline(tasks=tasks, data=text, datasets=[...]) against (steps, *, data=None, user=None, dataset=None, pipeline_name="pipeline", context=None) -> list passes keywords the runner lacks and leaves out the required steps: a split-body mismatch
  - `add` (references/full-api-reference.md:37), inventory reader: a heading that writes cognee.add(...) (and the other #### cognee.X(...) headings at full-api-reference.md:71, 118, 171, 192, 343, 355, 430, 457, 476, 491) is a form, recorded as a usage whose ... stands for omitted arguments and so labels it partial; left open by: A description cell is any table cell but an export table's first cell and a cell whose column writes the call or signature, by its role (Signature, Props, Params, Parameters, Arguments, Usage, Syntax, Example and the like); a heading or an export table's first cell that writes `name()` is a form, recorded as written; the other reading gives: read as a mention under the running-text rule for (...), these headings give no entry; no gap either way, since an ellipsis claims nothing
  - `Task` (SKILL.md:268), inventory reader: 'Constructor: Task(executable, *args, ...)' writes a call of the class's own name in running text, not a constructor declaration, so it is a usage under the call rule; left open by: A constructor a place writes (`def __init__(self, ...)`, `constructor(...)`, in a class body, a methods list, a row's cell or running text) is its class's form, never a `method` entry: the class's `params`, at the `class` line in a class body, else at the nearest line of that place that writes the class's name (a label line such as `**FlowLiveUpdater**`); the other reading gives: read as a constructor declaration, the same list in params with defaults would claim to be complete; it matches Task's __init__ either way, so no gap expected
  - `RememberKwargs` (SKILL.md:156), inventory reader: the skill gives RememberKwargs, ImproveKwargs and UpdateResult no kind label and documents them as keyword or result dicts with named keys, so they are recorded as type with fields; left open by: The contract `validate-inventory.py` checks (coverage-check.md §1a): each `kind` is one of `function`, `class`, `type`, `constant`, `hook`, `interface`, `method`, `struct`, `enum`, `trait`, `macro` or `adapter`; the other reading gives: as class, no gap: neither kind carries a compared form
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

- Inventory (§1, §1a): the §1 reader subagent's inventory validated on its first pass (376 entries, floor 47 of 47 names kept, spot-check sample `BoundTask`, `get_cognee_version`, `with_config` all found, nothing rejected). One `at` was dropped by the validator: `RememberResult` at `SKILL.md:276`, a line that does not write the name (the heading above it, `SKILL.md:274`, does); that entry carries no compared form, so no form is left unbound for want of a place (0 forms unbound). The validator cross-checked 151 names that two or more files write.
- Split-body cross-check (§1b): the reader recorded no `cross_check_mismatches` entry, so §1b records no `split-body-mismatch` gap.
- Signature check (§2): 39 `files[]` entries in the signature plan, 70 checks; one signature-judge subagent per entry, each reading the rules file in full. 38 judges reported no mismatch; the `run_parallel.py` judge reported two `annotation-contradicted` mismatches on `run_tasks_parallel` (evidence line 15), which `score` checked and graded Info. No judge recorded an `undecided` reading.
- Extraction: the recipe runner read every file (no `readByEye`, no `unread` file, no fallback scan, no unresolved star re-export).
- Numerator ground truth (§2b): skipped (no inflation signature: `exports_documented` 86 differs from the denominator).
- Provenance line check (§4c): no stale provenance line.

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)
**Migration Section:** Section 4b verification skipped: evidence-report.md pins no `t2_future_count`. For a skill create-skill made, re-run create-skill to regenerate the report with the field (create-stack-skill does not write it).

### Structural Findings

| # | Type | Severity | Detail | Line |
|---|------|----------|--------|------|
| - | none | - | No structural issue in §§2.1-2.7: the description, usage and API-surface families are served by `## Overview`, `## Quick Start` and `## Key API Summary`; 6 code fences, balanced, each with a language tag; no table row drifts from its header; every function and method export is used in a usage-family section or reference file (split body: Quick Start, Common Workflows, Key API Summary and the 4 reference files); no export is described as async with an unawaited example or as sync with an awaited one; no `scripts/` or `assets/` folder. | - |

**Structural Issues:** 0

### Reference Consistency (split-body)

| # | Reference File | Export | Issue | Other Side | Reference Line | Contradicted Side |
|---|---------------|--------|-------|------------|---------------|-------------------|
| - | - | - | No split-body mismatch: the reader's cross-check recorded no `cross_check_mismatches` entry. | - | - | - |

**Exports Cross-Checked:** 151
**Mismatches Found:** 0

## External Validation

### skill-check
- **Available:** yes
- **Quality Score:** 90/100
- **Errors:** 0
- **Warnings:** 1
- **Diagnostics:** `body.max_tokens` (warn) at `skills/oms-cognee/1.6.2/oms-cognee/SKILL.md:1`: body token estimate 5736 exceeds max 5000 (suggestion: reduce body to ~5000 tokens or fewer; the token count is a whitespace-split approximation)

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

**Total Gaps:** 66
**Blocking (Critical + High):** 0
**Non-blocking (Medium + Low + Info):** 66

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|------------------|
| Critical | 0 | None |
| High | 0 | None |
| Medium | 4 | stale-documentation (3): check each name against the source and the brief's scope, then update or remove its documentation or fix the scope (Update Skill does not repair it); metadata-drift (1): re-run Create Skill or edit the brief's scope, as each remediation says (counts that differ only by `Type::method` entries need no fix, and a hand edit of the counts does not hold) |
| Low | 1 | external-validator (1): apply each skill-check diagnostic or Tessl Review suggestion to SKILL.md as its remediation says |
| Info | 61 | observation (60): apply each only when you agree, as its remediation says, since it is advisory (a documented extra needs no change); multi-denominator (1): none, since the barrel and the documented surface measure different sets by design |
| **Total** | **66** | |

### GAP-051: Stale documentation: run_migrations

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:148
**Export:** run_migrations

**Issue:** `SKILL.md:148` documents `run_migrations`, which the entry point `cognee/__init__.py` exports and `cognee/run_migrations.py:18` defines, a file `forge-data/oms-cognee/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `run_migrations` belongs on the surface: `forge-data/oms-cognee/skill-brief.yaml` scopes out `cognee/run_migrations.py:18`, where it is defined, since no `scope.include` glob covers that file and its `scope.exclude` glob `cognee/run_migrations.py` matches it. To keep its documentation, widen `scope.include` to cover that file and narrow `cognee/run_migrations.py` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `run_migrations` at SKILL.md:148.

### GAP-054: Stale documentation: setup_logging

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:28
**Export:** setup_logging

**Issue:** `SKILL.md:28` documents `setup_logging`, which the entry point `cognee/__init__.py` exports and `cognee/shared/logging_utils.py:345` defines, a file `forge-data/oms-cognee/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `setup_logging` belongs on the surface: `forge-data/oms-cognee/skill-brief.yaml` scopes out `cognee/shared/logging_utils.py:345`, where it is defined, since no `scope.include` glob covers that file and its `scope.exclude` glob `cognee/shared/**` matches it. To keep its documentation, widen `scope.include` to cover that file and narrow `cognee/shared/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `setup_logging` at SKILL.md:28.

### GAP-063: Stale documentation: wait_for_background_tasks

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:157
**Export:** wait_for_background_tasks

**Issue:** `SKILL.md:157` documents `wait_for_background_tasks`, which the entry point `cognee/__init__.py` exports and `cognee/infrastructure/background_tasks.py:66` defines, a file `forge-data/oms-cognee/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `wait_for_background_tasks` belongs on the surface: `forge-data/oms-cognee/skill-brief.yaml` scopes out `cognee/infrastructure/background_tasks.py:66`, where it is defined, since no `scope.include` glob covers that file and its `scope.exclude` glob `cognee/infrastructure/**` matches it. To keep its documentation, widen `scope.include` to cover that file and narrow `cognee/infrastructure/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `wait_for_background_tasks` at SKILL.md:157.

### GAP-064: metadata drift — barrel export counts diverge

**Severity:** Medium
**Category:** Coverage (metadata-drift)
**Source:** skills/oms-cognee/1.6.2/oms-cognee/metadata.json

**Issue:** stats.exports_public_api=102, exports[].length=86 → 16% drift

**Remediation:** Re-run Create Skill, which rebuilds `exports[]` and `stats.exports_public_api` in `skills/oms-cognee/1.6.2/oms-cognee/metadata.json` from the source. Update Skill does not repair this drift: each time it writes the skill it recounts `stats.exports_public_api` from the source and keeps `exports[]`, adding or dropping only the names its provenance map changes, so a metadata patch does not hold.

### GAP-066: skill-check: body.max_tokens

**Severity:** Low
**Category:** External (external-validator)
**Source:** skills/oms-cognee/1.6.2/oms-cognee/SKILL.md:1

**Issue:** body token estimate 5736 exceeds max 5000

**Remediation:** Reduce the SKILL.md body (skills/oms-cognee/1.6.2/oms-cognee/SKILL.md) to about 5000 tokens or fewer by moving detail into the references/ files, as skill-check's body.max_tokens rule suggests (its count is a whitespace-split approximation).

### GAP-001: Annotation contradicted: run_tasks_parallel (form 1 of 2)

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/operations/run_parallel.py:8
**Export:** run_tasks_parallel

**Issue:** the source annotates the return of `run_tasks_parallel` otherwise than the skill documents, and its body returns the documented type at `cognee/modules/pipelines/operations/run_parallel.py:15`: documented `run_tasks_parallel(tasks) -> Task`, source `def run_tasks_parallel(tasks: list[Task]) -> Callable[[Any], Generator[Any, Any, Any]]`: Documented return type Task differs from the declared return annotation Callable[[Any], Generator[Any, Any, Any]]; the body returns Task(parallel_run) at line 15 (Task declares no __call__), so the annotation is contradicted by the body. Parameters match (tasks, untyped in the form, is not compared on type). (documented form 1 of 2: `(tasks) -> Task`)

**Remediation:** No change to the skill: it documents what `run_tasks_parallel` returns, as `cognee/modules/pipelines/operations/run_parallel.py:15` shows. Report the return annotation at `cognee/modules/pipelines/operations/run_parallel.py:8` upstream, since the body contradicts it.

### GAP-002: Annotation contradicted: run_tasks_parallel (form 2 of 2)

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/operations/run_parallel.py:8
**Export:** run_tasks_parallel

**Issue:** the source annotates the return of `run_tasks_parallel` otherwise than the skill documents, and its body returns the documented type at `cognee/modules/pipelines/operations/run_parallel.py:15`: documented `run_tasks_parallel(tasks: list[Task]) -> Task`, source `def run_tasks_parallel(tasks: list[Task]) -> Callable[[Any], Generator[Any, Any, Any]]`: Documented return type Task differs from the declared return annotation Callable[[Any], Generator[Any, Any, Any]]; the body returns Task(parallel_run) at line 15 (Task declares no __call__), so the annotation is contradicted by the body. Parameters match exactly. (documented form 2 of 2: `(tasks: list[Task]) -> Task`)

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

### GAP-023: Documented extra: PipelineRunCompleted

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/models/PipelineRunInfo.py:34
**Export:** PipelineRunCompleted

**Issue:** `references/full-api-reference.md:267` documents `PipelineRunCompleted`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PipelineRunCompleted` is a documented extra, a name the source still declares at `cognee/modules/pipelines/models/PipelineRunInfo.py:34` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-024: Documented extra: PipelineRunErrored

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/models/PipelineRunInfo.py:42
**Export:** PipelineRunErrored

**Issue:** `references/core-workflow.md:100` documents `PipelineRunErrored`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PipelineRunErrored` is a documented extra, a name the source still declares at `cognee/modules/pipelines/models/PipelineRunInfo.py:42` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-025: Documented extra: PipelineRunInfo

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/models/PipelineRunInfo.py:9
**Export:** PipelineRunInfo

**Issue:** `references/full-api-reference.md:566` documents `PipelineRunInfo`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PipelineRunInfo` is a documented extra, a name the source still declares at `cognee/modules/pipelines/models/PipelineRunInfo.py:9` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-026: Documented extra: PipelineRunStarted

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/models/PipelineRunInfo.py:26
**Export:** PipelineRunStarted

**Issue:** `references/full-api-reference.md:267` documents `PipelineRunStarted`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `PipelineRunStarted` is a documented extra, a name the source still declares at `cognee/modules/pipelines/models/PipelineRunInfo.py:26` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-027: Documented extra: REMEDIATION_MARKER

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/remediation.py:52
**Export:** REMEDIATION_MARKER

**Issue:** `SKILL.md:294` documents `REMEDIATION_MARKER`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `REMEDIATION_MARKER` is a documented extra, a name the source still declares at `cognee/exceptions/remediation.py:52` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-028: Documented extra: RememberKwargs

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/remember/remember.py:90
**Export:** RememberKwargs

**Issue:** `SKILL.md:156` documents `RememberKwargs`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `RememberKwargs` is a documented extra, a name the source still declares at `cognee/api/v1/remember/remember.py:90` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-029: Documented extra: SkillRunEntry

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/memory/entries.py:82
**Export:** SkillRunEntry

**Issue:** `SKILL.md:280` documents `SkillRunEntry`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `SkillRunEntry` is a documented extra, a name the source still declares at `cognee/memory/entries.py:82` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-030: Documented extra: TaskSpec

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/tasks/task.py:35
**Export:** TaskSpec

**Issue:** `references/pipelines-and-datapoints.md:36` documents `TaskSpec`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `TaskSpec` is a documented extra, a name the source still declares at `cognee/modules/pipelines/tasks/task.py:35` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-031: Documented extra: UpdateResult

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/update/result.py:37
**Export:** UpdateResult

**Issue:** `references/core-workflow.md:390` documents `UpdateResult`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `UpdateResult` is a documented extra, a name the source still declares at `cognee/api/v1/update/result.py:37` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-032: Documented extra: __version__

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/__init__.py:22
**Export:** __version__

**Issue:** `SKILL.md:149` documents `__version__`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `__version__` is a documented extra, a name the source still declares at `cognee/__init__.py:22` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-033: Documented extra: add_data_points

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/tasks/storage/add_data_points.py:70
**Export:** add_data_points

**Issue:** `references/core-workflow.md:199` documents `add_data_points`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `add_data_points` is a documented extra, a name the source still declares at `cognee/tasks/storage/add_data_points.py:70` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-034: Documented extra: add_feedback

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/session/session.py:113
**Export:** add_feedback

**Issue:** `SKILL.md:147` documents `add_feedback`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `add_feedback` is a documented extra, a name the source still declares at `cognee/api/v1/session/session.py:113` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-035: Documented extra: delete_feedback

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/session/session.py:147
**Export:** delete_feedback

**Issue:** `SKILL.md:147` documents `delete_feedback`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `delete_feedback` is a documented extra, a name the source still declares at `cognee/api/v1/session/session.py:147` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-036: Documented extra: distill_session

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/session_distillation/distill.py:471
**Export:** distill_session

**Issue:** `SKILL.md:147` documents `distill_session`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `cognee/modules/session_distillation/distill.py`

**Remediation:** No change: `distill_session` is a documented extra, a name the source still declares at `cognee/modules/session_distillation/distill.py:471` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-037: Documented extra: find_remediation

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/remediation.py:131
**Export:** find_remediation

**Issue:** `SKILL.md:294` documents `find_remediation`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `find_remediation` is a documented extra, a name the source still declares at `cognee/exceptions/remediation.py:131` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-038: Documented extra: get_default_tasks

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/cognify/cognify.py:565
**Export:** get_default_tasks

**Issue:** `references/core-workflow.md:183` documents `get_default_tasks`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_default_tasks` is a documented extra, a name the source still declares at `cognee/api/v1/cognify/cognify.py:565` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-039: Documented extra: get_errored_run_info

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/models/PipelineRunInfo.py:62
**Export:** get_errored_run_info

**Issue:** `references/full-api-reference.md:574` documents `get_errored_run_info`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_errored_run_info` is a documented extra, a name the source still declares at `cognee/modules/pipelines/models/PipelineRunInfo.py:62` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-040: Documented extra: get_session

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/session/session.py:65
**Export:** get_session

**Issue:** `SKILL.md:147` documents `get_session`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_session` is a documented extra, a name the source still declares at `cognee/api/v1/session/session.py:65` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-041: Documented extra: graph_model_from_spec

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/graph_models/compiler.py:135
**Export:** graph_model_from_spec

**Issue:** `references/full-api-reference.md:282` documents `graph_model_from_spec`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `graph_model_from_spec` is a documented extra, a name the source still declares at `cognee/modules/graph_models/compiler.py:135` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-042: Documented extra: graph_model_to_graph_schema

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/shared/graph_model_utils.py:93
**Export:** graph_model_to_graph_schema

**Issue:** `references/full-api-reference.md:282` documents `graph_model_to_graph_schema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `graph_model_to_graph_schema` is a documented extra, a name the source still declares at `cognee/shared/graph_model_utils.py:93` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-043: Documented extra: graph_schema_to_graph_model

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/shared/graph_model_utils.py:44
**Export:** graph_schema_to_graph_model

**Issue:** `references/full-api-reference.md:282` documents `graph_schema_to_graph_model`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `graph_schema_to_graph_model` is a documented extra, a name the source still declares at `cognee/shared/graph_model_utils.py:44` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-044: Documented extra: graph_spec_to_json_schema

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/graph_models/compiler.py:119
**Export:** graph_spec_to_json_schema

**Issue:** `references/full-api-reference.md:282` documents `graph_spec_to_json_schema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `graph_spec_to_json_schema` is a documented extra, a name the source still declares at `cognee/modules/graph_models/compiler.py:119` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-045: Documented extra: is_internal_node

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/infrastructure/engine/models/InternalDataPoint.py:27
**Export:** is_internal_node

**Issue:** `references/pipelines-and-datapoints.md:337` documents `is_internal_node`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `is_internal_node` is a documented extra, a name the source still declares at `cognee/infrastructure/engine/models/InternalDataPoint.py:27` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-046: Documented extra: is_tracing_enabled

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/observability/trace_context.py:62
**Export:** is_tracing_enabled

**Issue:** `references/full-api-reference.md:304` documents `is_tracing_enabled`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `is_tracing_enabled` is a documented extra, a name the source still declares at `cognee/modules/observability/trace_context.py:62` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-047: Documented extra: migration

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/migration/__init__.py:1
**Export:** migration

**Issue:** `SKILL.md:185` documents `migration`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `cognee/migration/__init__.py`

**Remediation:** No change: `migration` is a documented extra, a name the source still declares at `cognee/migration/__init__.py:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-048: Documented extra: pipeline_needs_llm

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/tasks/task.py:160
**Export:** pipeline_needs_llm

**Issue:** `SKILL.md:268` documents `pipeline_needs_llm`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `pipeline_needs_llm` is a documented extra, a name the source still declares at `cognee/modules/pipelines/tasks/task.py:160` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-049: Documented extra: pipelines

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/__init__.py:1
**Export:** pipelines

**Issue:** `SKILL.md:145` documents `pipelines`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `pipelines` is a documented extra, a name the source still declares at `cognee/modules/pipelines/__init__.py:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-050: Documented extra: remediation_for

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/remediation.py:146
**Export:** remediation_for

**Issue:** `SKILL.md:294` documents `remediation_for`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `remediation_for` is a documented extra, a name the source still declares at `cognee/exceptions/remediation.py:146` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-052: Documented extra: run_relational_migrations

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/run_migrations.py:11
**Export:** run_relational_migrations

**Issue:** `references/full-api-reference.md:409` documents `run_relational_migrations`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `cognee/run_migrations.py`

**Remediation:** No change: `run_relational_migrations` is a documented extra, a name the source still declares at `cognee/run_migrations.py:11` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-053: Documented extra: setup

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/engine/operations/setup.py:9
**Export:** setup

**Issue:** `SKILL.md:221` documents `setup`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `setup` is a documented extra, a name the source still declares at `cognee/modules/engine/operations/setup.py:9` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-055: Documented extra: start_visualization_server

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/visualize/start_visualization_server.py:1
**Export:** start_visualization_server

**Issue:** `SKILL.md:29` documents `start_visualization_server`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `start_visualization_server` is a documented extra, a name the source still declares at `cognee/api/v1/visualize/start_visualization_server.py:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-056: Documented extra: task

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/tasks/task.py:124
**Export:** task

**Issue:** `references/pipelines-and-datapoints.md:35` documents `task`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `task` is a documented extra, a name the source still declares at `cognee/modules/pipelines/tasks/task.py:124` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-057: Documented extra: task_summary

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/tasks/task.py:169
**Export:** task_summary

**Issue:** `references/pipelines-and-datapoints.md:36` documents `task_summary`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `task_summary` is a documented extra, a name the source still declares at `cognee/modules/pipelines/tasks/task.py:169` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-058: Documented extra: tools

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/tools/tools.py:1
**Export:** tools

**Issue:** `SKILL.md:181` documents `tools`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `tools` is a documented extra, a name the source still declares at `cognee/api/v1/tools/tools.py:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-059: Documented extra: use_vector_adapter

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/infrastructure/databases/vector/use_vector_adapter.py:4
**Export:** use_vector_adapter

**Issue:** `references/config.md:55` documents `use_vector_adapter`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `use_vector_adapter` is a documented extra, a name the source still declares at `cognee/infrastructure/databases/vector/use_vector_adapter.py:4` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-060: Documented extra: visualize_graph_json

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/visualize/visualize.py:271
**Export:** visualize_graph_json

**Issue:** `references/full-api-reference.md:337` documents `visualize_graph_json`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `visualize_graph_json` is a documented extra, a name the source still declares at `cognee/api/v1/visualize/visualize.py:271` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-061: Documented extra: visualize_multi_user_graph

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/visualize/visualize.py:611
**Export:** visualize_multi_user_graph

**Issue:** `references/full-api-reference.md:339` documents `visualize_multi_user_graph`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `visualize_multi_user_graph` is a documented extra, a name the source still declares at `cognee/api/v1/visualize/visualize.py:611` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-062: Documented extra: visualize_semantic_json

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/visualize/visualize.py:317
**Export:** visualize_semantic_json

**Issue:** `references/full-api-reference.md:338` documents `visualize_semantic_json`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `visualize_semantic_json` is a documented extra, a name the source still declares at `cognee/api/v1/visualize/visualize.py:317` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-065: multi-denominator reporting — barrel vs documented surface

**Severity:** Info
**Category:** Coverage (multi-denominator)
**Source:** skills/oms-cognee/1.6.2/oms-cognee/metadata.json

**Issue:** barrel=102, documented=86

**Remediation:** No action required: the barrel and the documented surface measure different sets by design, and the report records both counts.

### Discovery Quality

**Discovery Test:** PASS (3/3)

| # | Prompt | Selected Skill | Result |
|---|--------|----------------|--------|
| 1 | can you help me load this folder of support tickets my boss sent into my agent's long-term memory so it can answer questions about them later? | oms-cognee (high) | PASS |
| 2 | why does my assistant keep mixing up what different customers told it? I want each customer's memories kept separate when it looks things up | oms-cognee (high) | PASS |
| 3 | run the memory thing on these meeting notes and then show me a picture of how the people and projects in them connect | oms-cognee (high) | PASS |

Catalog: the 4 skills in `skills/` (oms-cocoindex, oms-cognee, oms-storybook-react-vite, oms-uitripled), each given by name and frontmatter description. SKILL.md holds no organic, name-free prompt (its Common Workflows lines are code), so the three prompts were synthesized from the vague, implicit and abbreviated patterns of report.md §4b.4, naming no export, skill or library. Each went to an isolated subagent with no file or shell tool (Claude Code's `web-fetch` agent type, the only one without them; none is tool-less), which used no tool. No description-optimization hint applies: Tessl Review did not run and skill-check flagged no description issue.
