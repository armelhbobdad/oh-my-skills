---
workflowType: 'test-skill'
skillName: 'oms-cognee'
skillDir: 'skills/oms-cognee/1.6.2/oms-cognee'
runId: '20261106T185511Z-d1bc353b'
testMode: 'naive'
forgeTier: 'Deep'
hardGate: 'blocked'
testResult: 'fail'
score: ''
threshold: '80%'
thresholdSource: 'workflow default (80%)'
analysisConfidence: 'full'
toolingStatus: 'ok'
workspaceDrift: 'ok'
health_check_dispatched: true
testDate: '2026-11-06T18:55:11Z'
stepsCompleted: ['init', 'detect-mode', 'coverage-check', 'coherence-check', 'external-validators', 'hard-gate', 'report']
nextWorkflow: 'update-skill'
---

# Test Report: oms-cognee

<!--
Each stage writes its section in place of the heading below that it owns and
the placeholder comment under that heading, so every heading occurs once.
Before the result files are written, report.md §4c checks that each heading
occurs exactly once and that no placeholder comment is left: a stage that
skipped its section stops the run there. Do not reorder or delete the
headings or their placeholder comments.

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

**Mode Rationale:** metadata.json records `skill_type: "single"`, so this is an individual skill: naive mode checks API-surface coverage, and coherence is structural only (no coherence category in scoring).

**Analysis Plan:**
- Coverage Check: every public export of `cognee/__init__.py` at the pinned commit ba3631f (v1.6.2), read from the local workspace clone, checked for documentation in SKILL.md and references/; at Deep tier, signatures and types of documented exports are compared against the AST-backed source declarations under `references/signature-comparison-rules.md`.
- Coherence Check: structural only (naive mode): every reference link from SKILL.md resolves, references are internally consistent, and metadata.json agrees with the package; no cross-skill integration checks.

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
| `COGXDocument` | class | yes | no | cognee/modules/migration/cogx.py:78 | FAIL |
| `COGXEntity` | class | yes | no | cognee/modules/migration/cogx.py:101 | FAIL |
| `COGXEpisode` | class | yes | no | cognee/modules/migration/cogx.py:93 | FAIL |
| `COGXFact` | class | yes | no | cognee/modules/migration/cogx.py:112 | FAIL |
| `COGXManifest` | class | yes | yes | cognee/modules/migration/cogx.py:180 | PASS |
| `COGXMemory` | class | yes | no | cognee/modules/migration/cogx.py:131 | FAIL |
| `COGXMemoryBlock` | class | yes | no | cognee/modules/migration/cogx.py:139 | FAIL |
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
| `DistillationResult` | - | yes | - | - | WARN |
| `Drop` | - | yes | - | cognee/pipelines/types.py:32 | PASS |
| `EXPORT_FORMATS` | - | yes | - | cognee/modules/migration/export.py:35 | PASS |
| `Edge` | - | yes | - | - | WARN |
| `EntitySpec` | - | yes | - | - | WARN |
| `ExportResult` | class | yes | yes | cognee/modules/migration/export.py:41 | PASS |
| `ExtendableDataPoint` | - | yes | - | - | WARN |
| `FeedbackEntry` | class | yes | yes | cognee/memory/entries.py:62 | PASS |
| `FromIdentity` | - | yes | - | - | WARN |
| `GraphEdge` | class | yes | yes | cognee/modules/migration/snapshot.py:152 | PASS |
| `GraphSchemaSpec` | - | yes | - | - | WARN |
| `GraphSnapshot` | class | yes | yes | cognee/modules/migration/snapshot.py:161 | PASS |
| `GraphitiSource` | class | yes | yes | cognee/modules/migration/sources/zep.py:136 | PASS |
| `IMPORT_MODES` | - | yes | - | cognee/modules/migration/sources/base.py:19 | PASS |
| `LLMGateway` | - | yes | - | - | WARN |
| `LettaSource` | class | yes | yes | cognee/modules/migration/sources/letta.py:72 | PASS |
| `Mem0Source` | class | yes | yes | cognee/modules/migration/sources/mem0.py:26 | PASS |
| `MemoryEntry` | - | yes | - | cognee/memory/entries.py:129 | PASS |
| `MemorySource` | class | yes | yes | cognee/modules/migration/sources/base.py:36 | PASS |
| `PipelineRunCompleted` | - | yes | - | - | WARN |
| `PipelineRunErrored` | - | yes | - | - | WARN |
| `PipelineRunInfo` | - | yes | - | - | WARN |
| `PipelineRunStarted` | - | yes | - | - | WARN |
| `PushResult` | class | yes | yes | cognee/api/v1/push/push.py:26 | PASS |
| `QAEntry` | class | yes | yes | cognee/memory/entries.py:24 | PASS |
| `REMEDIATION_MARKER` | - | yes | - | - | WARN |
| `RememberResult` | class | yes | - | cognee/api/v1/remember/remember.py:600 | PASS |
| `SearchType` | class | yes | - | cognee/modules/search/types/SearchType.py:4 | PASS |
| `SessionModelUsage` | class | yes | - | cognee/modules/session_lifecycle/models.py:96 | PASS |
| `SessionRecord` | class | yes | - | cognee/modules/session_lifecycle/models.py:10 | PASS |
| `SkillRunEntry` | - | yes | - | - | WARN |
| `Task` | class | yes | yes | cognee/modules/pipelines/tasks/task.py:188 | PASS |
| `TaskSpec` | - | yes | - | - | WARN |
| `TraceEntry` | class | yes | yes | cognee/memory/entries.py:40 | PASS |
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
| `graph_model_to_graph_schema` | - | yes | - | - | WARN |
| `graph_schema_to_graph_model` | - | yes | - | - | WARN |
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
| `run_pipeline` | function | yes | no | cognee/modules/pipelines/operations/pipeline.py:53 | FAIL |
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
| `validate` | function | yes | yes | cognee/api/v1/validate/validate.py:198 | PASS |
| `visualization_server` | function | yes | yes | cognee/api/v1/visualize/start_visualization_server.py:6 | PASS |
| `visualize` | function | yes | - | cognee/api/v1/visualize/visualize.py:193 | PASS |
| `visualize_graph` | function | yes | yes | cognee/api/v1/visualize/visualize.py:193 | PASS |
| `visualize_graph_json` | - | yes | - | - | WARN |
| `visualize_memory_provenance` | function | yes | yes | cognee/api/v1/visualize/memory_provenance.py:848 | PASS |
| `visualize_multi_user_graph` | - | yes | - | - | WARN |
| `visualize_semantic_json` | - | yes | - | - | WARN |

### Coverage Summary

- **Exports Found:** 92
- **Documented:** 92 (100%)
- **Missing Documentation:** 0
- **Signature Mismatches:** 8, plus 1 graded Low or Info and counted as matching
- **Stale Documentation:** 46, documented extras included
- **Scoped Out by the Brief:** `describe_resolution` (cognee/shared/env_file.py:127), `load_env_file` (cognee/shared/env_file.py:112), `run_migrations` (cognee/run_migrations.py:18), `setup_logging` (cognee/shared/logging_utils.py:345), `start_visualization_server` (cognee/shared/utils.py:481), `wait_for_background_tasks` (cognee/infrastructure/background_tasks.py:66)
- **Nested Entry Points:** `cognee/api/v1/api_keys/routers/__init__.py` inside `cognee/__init__.py`: `get_api_key_management_router`; `cognee/api/v1/cloud/routers/__init__.py` inside `cognee/__init__.py`: `get_checks_router`; `cognee/api/v1/permissions/routers/__init__.py` inside `cognee/__init__.py`: `get_permissions_router`; `cognee/api/v1/settings/routers/__init__.py` inside `cognee/__init__.py`: `get_settings_router`

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 100% |
| Signature Accuracy | 90.54% |
| Type Coverage | 100% |

**Notes (coverage-check §1 to §4c):**

- **Inventory (§1, §1a):** this session had no subagent tool, so the main thread built the documented inventory from SKILL.md and all four `references/*.md` files (SKILL.md has no `## Full` headings), following `references/inventory-contract.md` and `inventory-floor.json`: 244 entries over 142 name/kind items, one entry per documented place. Call examples are `usage_signature` forms, and shared-text rows (the COGX record kinds, the memory-provenance pair) carry the shared text, then `; `, then the name's own members. `validate-inventory.py` accepted it on the first pass: schema clean, spot-check `BoundTask`, `datasets`, `visualize_semantic_json` all found, floor 47/47 names kept with their 8 pinned `references/full-api-reference.md` signatures. No inventory was refused or re-dispatched.
- **Split-body cross-check (§1b):** one mismatch, `run_tasks_parallel`: `references/full-api-reference.md:268` writes `-> Task`, `references/pipelines-and-datapoints.md:278` writes `-> Callable[[Any], Generator[Any, Any, Any]]` (its trailing comment says it actually returns `Task(parallel_run)`). The two `run_pipeline` functions the skill documents under one bare name (the `cognee.modules.pipelines` orchestrator and the lightweight `cognee.pipelines` runner) were compared like with like. That is a borderline call, not counted as a split-body mismatch (see **Borderline calls** below).
- **Signature judging (§2):** the main thread judged all 40 `signature-plan.json` files (74 checks) in one pass, against the full declaration at each check's `file:line` (multi-line signatures read whole, a class through its fields and `__init__`, an overload set through its implementation), using the rules of `references/signature-comparison-rules.md` as written. The results are in one file, `signatures-1.txt`, with one object per `files[]` entry.
- **Extraction:** the runner's status is `ok`, with 255 files in scope. `readByEye` and `unread` are both empty, and no fallback scan ran. `extractionGaps` lists `COGXRecord`, `COGX_VERSION`, `Drop`, `EXPORT_FORMATS`, `IMPORT_MODES`, `MemoryEntry`, `logger` and `session`. Each was read by eye at its file and line: they are constants, aliases and a namespace the skill documents with no signature, so there was nothing to compare.
- **Numerator ground truth (§2b):** skipped, since `stats.exports_documented` (86) is not the stored denominator (none). No finding.
- **Stale names (§2c):** 46 documented names lie outside the `all` set. `classify-stale` marks none fabricated. The documented extras the source still declares are Info observations. `run_migrations`, `setup_logging` and `start_visualization_server` are names the brief scopes out (`excluded.outsideScope`), so each stays a Medium `stale-documentation` gap.
- **Guards (§4):** deflation is not applicable (no stored `effective_denominator`). Inflation does not fire (96 against 86 provenance entries, 11.63%), and neither does stale scope (every `scope.include` glob matches).
- **Metadata count cross-check (§4b):** one Medium `metadata-drift` (`stats.exports_public_api`=102 against `exports[].length`=86, 16% drift) and one Info `multi-denominator` (barrel 102, documented 86).
- **Provenance line check (§4c):** `verify` ran against the version folder's map, at `analysis_confidence` full and `workspaceDrift` ok. It found 0 stale lines.
- **Borderline calls** (the cases where `references/signature-comparison-rules.md` leaves the call open, recorded with the way this run counted them):
  1. `run_pipeline`, §1b pairing. The forms are `SKILL.md:116` `run_pipeline(tasks=tasks, data=text, datasets=["people_demo"])` (the orchestrator) against `references/full-api-reference.md:264` and `references/pipelines-and-datapoints.md:208` (the lightweight `cognee.pipelines.run_pipeline`, which `SKILL.md:224` itself names as a different function). The source declarations are `cognee/modules/pipelines/operations/pipeline.py:53` (orchestrator) and `cognee/modules/pipelines/operations/run_pipeline.py:37` (lightweight). The rules file never says how to pair the forms of two functions that share one bare name: "Each export's form is read alone: what the rows of other exports write, in the same table or file, states nothing about it." Counted as no split-body mismatch, since each file documents both functions consistently. The §2 comparison of the same forms was not borderline: the plan offers them as alternatives of the one surface record, and the rules file says "Compare the declaration with each form the check offers ... and report a mismatch for each form that does not match", so they are GAP-007 and GAP-008.
  2. `visualize_memory_provenance` form 1 (`SKILL.md:179`): shared text `include_memory=False, scope_tenant_ids=None, scope_user_ids=None, scope_dataset_ids=None` and own member "+ leading `destination_file_path=None`", against `cognee/api/v1/visualize/memory_provenance.py:848` (`destination_file_path` first). The rules file says "the members the shared text states are members that form writes, read before its own", while the form writes that its own member leads ("A form claims only what it writes"). Counted as a match. Form 2 (`references/full-api-reference.md:365`) matches outright.
  3. `run_tasks_parallel`, §1b: `references/pipelines-and-datapoints.md:278` writes `-> Callable[[Any], Generator[Any, Any, Any]]  # actually returns Task(parallel_run)`. Whether the trailing comment states a return type is the open question; the Annotations rule names the positions that state one ("after `->`, `=>`, `→` or `):`"), and a comment is not among them. Counted as a mismatch (GAP-058, High).
  4. COGX record kinds (`SKILL.md:200`, shared text "each with a literal `kind` and the base fields ..."): whether a field the shared text names in prose ("a literal `kind`") is a member the form writes with no mark. The rules file says "the members the shared text states are members that form writes", and "Optionality is stated only by a default, a `?` ... or an optional marker ... A type never states it". Counted as a mismatch: the form claims `kind` is required, while each source `kind` has a default (GAP-001 to GAP-006, Critical).
- **Not checked by script (Deep tier):** by eye, `cognee.config`'s 45 static methods, the `datasets`, `agents` and `prune` methods, the four `cognee.session` functions, `SearchType`'s 20 members, `ValidationStatus`, `GraphSnapshot` and `Task` methods, the `SessionRecord`, `SessionModelUsage`, `UpdateResult`, `DistillationResult`, `PipelineRunInfo` and `Edge` fields, and the documented import paths of `cognee.low_level`, `cognee.memory`, `cognee.exceptions`, `cognee.api.v1.update`, `cognee.api.v1.remember`, `cognee.api.v1.improve`, `cognee.run_migrations` and `cognee.api.v1.session` all match the source. One difference is recorded as an Info observation: `LLMGateway.acreate_structured_output` is written `(text, system_prompt, PydanticModel, **kwargs)` at `references/pipelines-and-datapoints.md:431`, while the source declares `acreate_structured_output(text_input: str, system_prompt: str, response_model: type[T], **kwargs)` (`cognee/infrastructure/llm/LLMGateway.py:113`).

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)
**Migration Section:** Section 4b verification skipped: evidence-report.md pins no `t2_future_count`. For a skill create-skill made, re-run create-skill to regenerate the report with the field (create-stack-skill does not write it).

### Structural Findings

| # | Type | Severity | Detail | Line |
|---|------|----------|--------|------|
| - | none | - | §2.1 required sections all satisfied (`Overview`, `Quick Start`, `Key API Summary`); §2.2 fences balanced (6); §2.3 no bare opening fence; §2.4 no function or method export with zero usage; §2.5 every async export is awaited where called and no sync one is; §2.6 no table drift; §2.7 no `scripts/` or `assets/` folder | - |

**Structural Issues:** 0

### Reference Consistency (split-body)

| # | Reference File | Export | Issue | Other Side | Reference Line | Contradicted Side |
|---|---------------|--------|-------|------------|---------------|-------------------|
| 1 | references/pipelines-and-datapoints.md | `run_tasks_parallel` | `references/full-api-reference.md` shows `run_tasks_parallel(tasks) -> Task`, `references/pipelines-and-datapoints.md` shows `run_tasks_parallel(tasks: list[Task]) -> Callable[[Any], Generator[Any, Any, Any]]` (its trailing comment says it actually returns `Task(parallel_run)`): the two forms state different return types | references/full-api-reference.md:268 | 278 | none |

**Exports Cross-Checked:** 99 (the inventory names that two or more of the five package files write)
**Mismatches Found:** 1

## External Validation

### skill-check
- **Available:** yes
- **Quality Score:** 90/100
- **Errors:** 0
- **Warnings:** 1
- **Diagnostics:** `body.max_tokens` (warn) at `skills/oms-cognee/1.6.2/oms-cognee/SKILL.md:1`: body token estimate 5696 exceeds max 5000. Suggestion: reduce the body to ~5000 tokens or fewer (the token count is a whitespace-split approximation).

### Tessl Review
- **Result:** off — set tessl_review_workspace in preferences.yaml to enable

### Combined External Score
- **External Validation Score:** 90.0%
- **Tools used:** skill-check

## Completeness Score

**Result:** **FAIL**, not scored: the hard gate blocked this run on 9 Critical or High gap(s), listed first in the Gap Report.

## Gap Report

**Total Gaps:** 60
**Blocking (Critical + High):** 9
**Non-blocking (Medium + Low + Info):** 51

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|------------------|
| Critical | 8 | Read the source code and write or correct the documentation |
| High | 1 | Read the source code and write or correct the documentation |
| Medium | 4 | Add type definitions, interface docs or the missing section |
| Low | 1 | Add examples or metadata |
| Info | 46 | Optional improvements, no action required |
| **Total** | **60** | |

### GAP-001: Signature mismatch: COGXDocument

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** cognee/modules/migration/cogx.py:78
**Export:** COGXDocument

**Issue:** documented `COGXDocument(each with a literal kind and the base fields external_system="unknown", external_id, scope=COGXScope(), created_at=None, updated_at=None, metadata={}; content, title=None, mime_type=None)`, source `class COGXDocument(COGXRecordBase): external_system: str = "unknown", external_id: str, scope: COGXScope = Field(default_factory=COGXScope), created_at: datetime | None = None, updated_at: datetime | None = None, metadata: dict[str, Any] = Field(default_factory=dict), kind: Literal["document"] = "document", content: str, title: str | None = None, mime_type: str | None = None`: the shared text writes kind with no default in a list that states optionality, so the form claims kind is required; the declaration gives kind the default "document" (cogx.py:81)

**Remediation:** Update the documented signature of `COGXDocument` from `COGXDocument(each with a literal kind and the base fields external_system="unknown", external_id, scope=COGXScope(), created_at=None, updated_at=None, metadata={}; content, title=None, mime_type=None)` to `class COGXDocument(COGXRecordBase): external_system: str = "unknown", external_id: str, scope: COGXScope = Field(default_factory=COGXScope), created_at: datetime | None = None, updated_at: datetime | None = None, metadata: dict[str, Any] = Field(default_factory=dict), kind: Literal["document"] = "document", content: str, title: str | None = None, mime_type: str | None = None`, the signature the source defines at `cognee/modules/migration/cogx.py:78`.

### GAP-002: Signature mismatch: COGXEpisode

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** cognee/modules/migration/cogx.py:93
**Export:** COGXEpisode

**Issue:** documented `COGXEpisode(each with a literal kind and the base fields external_system="unknown", external_id, scope=COGXScope(), created_at=None, updated_at=None, metadata={}; turns=[], title=None)`, source `class COGXEpisode(COGXRecordBase): external_system: str = "unknown", external_id: str, scope: COGXScope = Field(default_factory=COGXScope), created_at: datetime | None = None, updated_at: datetime | None = None, metadata: dict[str, Any] = Field(default_factory=dict), kind: Literal["episode"] = "episode", turns: list[COGXTurn] = Field(default_factory=list), title: str | None = None`: the shared text writes kind with no default in a list that states optionality, so the form claims kind is required; the declaration gives kind the default "episode" (cogx.py:96)

**Remediation:** Update the documented signature of `COGXEpisode` from `COGXEpisode(each with a literal kind and the base fields external_system="unknown", external_id, scope=COGXScope(), created_at=None, updated_at=None, metadata={}; turns=[], title=None)` to `class COGXEpisode(COGXRecordBase): external_system: str = "unknown", external_id: str, scope: COGXScope = Field(default_factory=COGXScope), created_at: datetime | None = None, updated_at: datetime | None = None, metadata: dict[str, Any] = Field(default_factory=dict), kind: Literal["episode"] = "episode", turns: list[COGXTurn] = Field(default_factory=list), title: str | None = None`, the signature the source defines at `cognee/modules/migration/cogx.py:93`.

### GAP-003: Signature mismatch: COGXEntity

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** cognee/modules/migration/cogx.py:101
**Export:** COGXEntity

**Issue:** documented `COGXEntity(each with a literal kind and the base fields external_system="unknown", external_id, scope=COGXScope(), created_at=None, updated_at=None, metadata={}; name, entity_type=None, description=None, aliases=[], attributes={})`, source `class COGXEntity(COGXRecordBase): external_system: str = "unknown", external_id: str, scope: COGXScope = Field(default_factory=COGXScope), created_at: datetime | None = None, updated_at: datetime | None = None, metadata: dict[str, Any] = Field(default_factory=dict), kind: Literal["entity"] = "entity", name: str, entity_type: str | None = None, description: str | None = None, aliases: list[str] = Field(default_factory=list), attributes: dict[str, Any] = Field(default_factory=dict)`: the shared text writes kind with no default in a list that states optionality, so the form claims kind is required; the declaration gives kind the default "entity" (cogx.py:104)

**Remediation:** Update the documented signature of `COGXEntity` from `COGXEntity(each with a literal kind and the base fields external_system="unknown", external_id, scope=COGXScope(), created_at=None, updated_at=None, metadata={}; name, entity_type=None, description=None, aliases=[], attributes={})` to `class COGXEntity(COGXRecordBase): external_system: str = "unknown", external_id: str, scope: COGXScope = Field(default_factory=COGXScope), created_at: datetime | None = None, updated_at: datetime | None = None, metadata: dict[str, Any] = Field(default_factory=dict), kind: Literal["entity"] = "entity", name: str, entity_type: str | None = None, description: str | None = None, aliases: list[str] = Field(default_factory=list), attributes: dict[str, Any] = Field(default_factory=dict)`, the signature the source defines at `cognee/modules/migration/cogx.py:101`.

### GAP-004: Signature mismatch: COGXFact

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** cognee/modules/migration/cogx.py:112
**Export:** COGXFact

**Issue:** documented `COGXFact(each with a literal kind and the base fields external_system="unknown", external_id, scope=COGXScope(), created_at=None, updated_at=None, metadata={}; subject_ref, predicate, object_ref, fact_text=None, valid_at=None, invalid_at=None, confidence=None, provenance=[])`, source `class COGXFact(COGXRecordBase): external_system: str = "unknown", external_id: str, scope: COGXScope = Field(default_factory=COGXScope), created_at: datetime | None = None, updated_at: datetime | None = None, metadata: dict[str, Any] = Field(default_factory=dict), kind: Literal["fact"] = "fact", subject_ref: str, predicate: str, object_ref: str, fact_text: str | None = None, valid_at: datetime | None = None, invalid_at: datetime | None = None, confidence: float | None = None, provenance: list[str] = Field(default_factory=list)`: the shared text writes kind with no default in a list that states optionality, so the form claims kind is required; the declaration gives kind the default "fact" (cogx.py:120)

**Remediation:** Update the documented signature of `COGXFact` from `COGXFact(each with a literal kind and the base fields external_system="unknown", external_id, scope=COGXScope(), created_at=None, updated_at=None, metadata={}; subject_ref, predicate, object_ref, fact_text=None, valid_at=None, invalid_at=None, confidence=None, provenance=[])` to `class COGXFact(COGXRecordBase): external_system: str = "unknown", external_id: str, scope: COGXScope = Field(default_factory=COGXScope), created_at: datetime | None = None, updated_at: datetime | None = None, metadata: dict[str, Any] = Field(default_factory=dict), kind: Literal["fact"] = "fact", subject_ref: str, predicate: str, object_ref: str, fact_text: str | None = None, valid_at: datetime | None = None, invalid_at: datetime | None = None, confidence: float | None = None, provenance: list[str] = Field(default_factory=list)`, the signature the source defines at `cognee/modules/migration/cogx.py:112`.

### GAP-005: Signature mismatch: COGXMemory

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** cognee/modules/migration/cogx.py:131
**Export:** COGXMemory

**Issue:** documented `COGXMemory(each with a literal kind and the base fields external_system="unknown", external_id, scope=COGXScope(), created_at=None, updated_at=None, metadata={}; content, categories=[])`, source `class COGXMemory(COGXRecordBase): external_system: str = "unknown", external_id: str, scope: COGXScope = Field(default_factory=COGXScope), created_at: datetime | None = None, updated_at: datetime | None = None, metadata: dict[str, Any] = Field(default_factory=dict), kind: Literal["memory"] = "memory", content: str, categories: list[str] = Field(default_factory=list)`: the shared text writes kind with no default in a list that states optionality, so the form claims kind is required; the declaration gives kind the default "memory" (cogx.py:134)

**Remediation:** Update the documented signature of `COGXMemory` from `COGXMemory(each with a literal kind and the base fields external_system="unknown", external_id, scope=COGXScope(), created_at=None, updated_at=None, metadata={}; content, categories=[])` to `class COGXMemory(COGXRecordBase): external_system: str = "unknown", external_id: str, scope: COGXScope = Field(default_factory=COGXScope), created_at: datetime | None = None, updated_at: datetime | None = None, metadata: dict[str, Any] = Field(default_factory=dict), kind: Literal["memory"] = "memory", content: str, categories: list[str] = Field(default_factory=list)`, the signature the source defines at `cognee/modules/migration/cogx.py:131`.

### GAP-006: Signature mismatch: COGXMemoryBlock

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** cognee/modules/migration/cogx.py:139
**Export:** COGXMemoryBlock

**Issue:** documented `COGXMemoryBlock(each with a literal kind and the base fields external_system="unknown", external_id, scope=COGXScope(), created_at=None, updated_at=None, metadata={}; label, value, limit=None)`, source `class COGXMemoryBlock(COGXRecordBase): external_system: str = "unknown", external_id: str, scope: COGXScope = Field(default_factory=COGXScope), created_at: datetime | None = None, updated_at: datetime | None = None, metadata: dict[str, Any] = Field(default_factory=dict), kind: Literal["memory_block"] = "memory_block", label: str, value: str, limit: int | None = None`: the shared text writes kind with no default in a list that states optionality, so the form claims kind is required; the declaration gives kind the default "memory_block" (cogx.py:142)

**Remediation:** Update the documented signature of `COGXMemoryBlock` from `COGXMemoryBlock(each with a literal kind and the base fields external_system="unknown", external_id, scope=COGXScope(), created_at=None, updated_at=None, metadata={}; label, value, limit=None)` to `class COGXMemoryBlock(COGXRecordBase): external_system: str = "unknown", external_id: str, scope: COGXScope = Field(default_factory=COGXScope), created_at: datetime | None = None, updated_at: datetime | None = None, metadata: dict[str, Any] = Field(default_factory=dict), kind: Literal["memory_block"] = "memory_block", label: str, value: str, limit: int | None = None`, the signature the source defines at `cognee/modules/migration/cogx.py:139`.

### GAP-007: Signature mismatch: run_pipeline (form 1 of 6)

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** cognee/modules/pipelines/operations/pipeline.py:53
**Export:** run_pipeline

**Issue:** documented `(steps, *, data=None, user=None, dataset=None, pipeline_name="pipeline", context=None) -> list`, source `async def run_pipeline(tasks: list[Task] | Callable[[Any], list[Task]] | None = None, data=None, datasets: str | list[str] | list[UUID] | None = None, user: User | None = None, pipeline_name: str = "custom_pipeline", vector_db_config: dict | None = None, graph_db_config: dict | None = None, incremental_loading: bool = False, data_per_batch: int = 20, rollback_handler: Callable[..., Awaitable[None]] | None = None, llm_config: LLMConfig | None = None, embedding_config: EmbeddingConfig | None = None, data_cache: bool = False, skip_connection_test: bool = False, needs_llm: bool = True)`: the form lists steps, dataset and context, which this declaration lacks, and leaves out tasks, datasets and nine other optional parameters; it is the lightweight cognee.pipelines.run_pipeline (cognee/modules/pipelines/operations/run_pipeline.py:37), which the plan compares with the cognee.modules.pipelines orchestrator (documented form 1 of 6: `(steps, *, data=None, user=None, dataset=None, pipeline_name="pipeline", context=None) -> list`)

**Remediation:** Update the documented signature of `run_pipeline` from `(steps, *, data=None, user=None, dataset=None, pipeline_name="pipeline", context=None) -> list` to `async def run_pipeline(tasks: list[Task] | Callable[[Any], list[Task]] | None = None, data=None, datasets: str | list[str] | list[UUID] | None = None, user: User | None = None, pipeline_name: str = "custom_pipeline", vector_db_config: dict | None = None, graph_db_config: dict | None = None, incremental_loading: bool = False, data_per_batch: int = 20, rollback_handler: Callable[..., Awaitable[None]] | None = None, llm_config: LLMConfig | None = None, embedding_config: EmbeddingConfig | None = None, data_cache: bool = False, skip_connection_test: bool = False, needs_llm: bool = True)`, the signature the source defines at `cognee/modules/pipelines/operations/pipeline.py:53`.

### GAP-008: Signature mismatch: run_pipeline (form 4 of 6)

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** cognee/modules/pipelines/operations/pipeline.py:53
**Export:** run_pipeline

**Issue:** documented `(steps: list[BoundTask], *, data: Any = None, user: User | None = None, dataset: str | None = None, pipeline_name: str = "pipeline", context: dict | None = None) -> list`, source `async def run_pipeline(tasks: list[Task] | Callable[[Any], list[Task]] | None = None, data=None, datasets: str | list[str] | list[UUID] | None = None, user: User | None = None, pipeline_name: str = "custom_pipeline", vector_db_config: dict | None = None, graph_db_config: dict | None = None, incremental_loading: bool = False, data_per_batch: int = 20, rollback_handler: Callable[..., Awaitable[None]] | None = None, llm_config: LLMConfig | None = None, embedding_config: EmbeddingConfig | None = None, data_cache: bool = False, skip_connection_test: bool = False, needs_llm: bool = True)`: the form lists steps, dataset and context, which this declaration lacks, and leaves out tasks, datasets and nine other optional parameters; it is the lightweight cognee.pipelines.run_pipeline (cognee/modules/pipelines/operations/run_pipeline.py:37), which the plan compares with the cognee.modules.pipelines orchestrator (documented form 4 of 6: `(steps: list[BoundTask], *, data: Any = None, user: User | None = None, dataset: str | None = None, pipeline_name: str = "pipeline", context: dict | None = None) -> list`)

**Remediation:** Update the documented signature of `run_pipeline` from `(steps: list[BoundTask], *, data: Any = None, user: User | None = None, dataset: str | None = None, pipeline_name: str = "pipeline", context: dict | None = None) -> list` to `async def run_pipeline(tasks: list[Task] | Callable[[Any], list[Task]] | None = None, data=None, datasets: str | list[str] | list[UUID] | None = None, user: User | None = None, pipeline_name: str = "custom_pipeline", vector_db_config: dict | None = None, graph_db_config: dict | None = None, incremental_loading: bool = False, data_per_batch: int = 20, rollback_handler: Callable[..., Awaitable[None]] | None = None, llm_config: LLMConfig | None = None, embedding_config: EmbeddingConfig | None = None, data_cache: bool = False, skip_connection_test: bool = False, needs_llm: bool = True)`, the signature the source defines at `cognee/modules/pipelines/operations/pipeline.py:53`.

### GAP-058: Split-body mismatch: run_tasks_parallel (references/full-api-reference.md, references/pipelines-and-datapoints.md)

**Severity:** High
**Category:** Coherence (split-body-mismatch)
**Source:** references/pipelines-and-datapoints.md:278
**Export:** run_tasks_parallel

**Issue:** references/full-api-reference.md:268 shows run_tasks_parallel(tasks) -> Task, references/pipelines-and-datapoints.md:278 shows run_tasks_parallel(tasks: list[Task]) -> Callable[[Any], Generator[Any, Any, Any]] (its trailing comment says it actually returns Task(parallel_run)): the two forms state different return types

**Remediation:** Both forms agree with the declaration at cognee/modules/pipelines/operations/run_parallel.py:8: references/pipelines-and-datapoints.md:278 writes its annotation -> Callable[[Any], Generator[Any, Any, Any]], and references/full-api-reference.md:268 writes -> Task, the value the body returns at cognee/modules/pipelines/operations/run_parallel.py:15. They differ only in the return type they state. Edit references/pipelines-and-datapoints.md:278 to state the return type references/full-api-reference.md:268 states (-> Task), keeping the declared annotation in its comment, so the two files state one return type.

### GAP-045: Stale documentation: run_migrations

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:13
**Export:** run_migrations

**Issue:** `SKILL.md:13` documents `run_migrations`, which the entry point `cognee/__init__.py` exports and `cognee/run_migrations.py:18` defines, a file `forge-data/oms-cognee/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `run_migrations` belongs on the surface: `forge-data/oms-cognee/skill-brief.yaml` scopes out `cognee/run_migrations.py:18`, where it is defined, since no `scope.include` glob covers that file and its `scope.exclude` glob `cognee/run_migrations.py` matches it. To keep its documentation, widen `scope.include` to cover that file and narrow `cognee/run_migrations.py` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `run_migrations` at SKILL.md:13.

### GAP-048: Stale documentation: setup_logging

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:28
**Export:** setup_logging

**Issue:** `SKILL.md:28` documents `setup_logging`, which the entry point `cognee/__init__.py` exports and `cognee/shared/logging_utils.py:345` defines, a file `forge-data/oms-cognee/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `setup_logging` belongs on the surface: `forge-data/oms-cognee/skill-brief.yaml` scopes out `cognee/shared/logging_utils.py:345`, where it is defined, since no `scope.include` glob covers that file and its `scope.exclude` glob `cognee/shared/**` matches it. To keep its documentation, widen `scope.include` to cover that file and narrow `cognee/shared/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `setup_logging` at SKILL.md:28.

### GAP-049: Stale documentation: start_visualization_server

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:29
**Export:** start_visualization_server

**Issue:** `SKILL.md:29` documents `start_visualization_server`, which the entry point `cognee/__init__.py` exports and `cognee/shared/utils.py:481` defines, a file `forge-data/oms-cognee/skill-brief.yaml` scopes out (`excluded.outsideScope`)

**Remediation:** Decide whether `start_visualization_server` belongs on the surface: `forge-data/oms-cognee/skill-brief.yaml` scopes out `cognee/shared/utils.py:481`, where it is defined, since no `scope.include` glob covers that file and its `scope.exclude` glob `cognee/shared/**` matches it. To keep its documentation, widen `scope.include` to cover that file and narrow `cognee/shared/**` so it no longer matches that file (to remove the glob instead, record a `demoted-exclude` scope-expansion amendment in the brief); else remove the documentation of `start_visualization_server` at SKILL.md:29.

### GAP-056: metadata drift — barrel export counts diverge

**Severity:** Medium
**Category:** Coverage (metadata-drift)
**Source:** skills/oms-cognee/1.6.2/oms-cognee/metadata.json

**Issue:** stats.exports_public_api=102, exports[].length=86 → 16% drift

**Remediation:** Re-run Create Skill, which rebuilds `exports[]` and `stats.exports_public_api` in `skills/oms-cognee/1.6.2/oms-cognee/metadata.json` from the source. Update Skill does not repair this drift: each time it writes the skill it recounts `stats.exports_public_api` from the source and keeps `exports[]`, adding or dropping only the names its provenance map changes, so a metadata patch does not hold.

### GAP-060: skill-check: body.max_tokens

**Severity:** Low
**Category:** External (external-validator)
**Source:** SKILL.md:1

**Issue:** body token estimate 5696 exceeds max 5000

**Remediation:** Reduce the SKILL.md body to about 5000 tokens or fewer (skill-check's whitespace-split estimate is 5696), by moving detail from SKILL.md into the references/ files it already links.

### GAP-009: Annotation contradicted: run_tasks_parallel (form 1 of 3)

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/operations/run_parallel.py:8
**Export:** run_tasks_parallel

**Issue:** the source annotates the return of `run_tasks_parallel` otherwise than the skill documents, and its body returns the documented type at `cognee/modules/pipelines/operations/run_parallel.py:15`: documented `run_tasks_parallel(tasks) -> Task`, source `def run_tasks_parallel(tasks: list[Task]) -> Callable[[Any], Generator[Any, Any, Any]]`: only the return type differs: the documented Task is what the body returns at line 15 (return Task(parallel_run)), while the declared annotation says Callable[[Any], Generator[Any, Any, Any]] (documented form 1 of 3: `(tasks) -> Task`)

**Remediation:** No change to the skill: it documents what `run_tasks_parallel` returns, as `cognee/modules/pipelines/operations/run_parallel.py:15` shows. Report the return annotation at `cognee/modules/pipelines/operations/run_parallel.py:8` upstream, since the body contradicts it.

### GAP-010: Documented extra: BoundTask

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/tasks/task.py:8
**Export:** BoundTask

**Issue:** `SKILL.md:224` documents `BoundTask`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `BoundTask` is a documented extra, a name the source still declares at `cognee/modules/pipelines/tasks/task.py:8` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-011: Documented extra: CogneeApiError

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/exceptions.py:10
**Export:** CogneeApiError

**Issue:** `SKILL.md:288` documents `CogneeApiError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CogneeApiError` is a documented extra, a name the source still declares at `cognee/exceptions/exceptions.py:10` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-012: Documented extra: CogneeConfigurationError

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/exceptions.py:99
**Export:** CogneeConfigurationError

**Issue:** `SKILL.md:110` documents `CogneeConfigurationError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CogneeConfigurationError` is a documented extra, a name the source still declares at `cognee/exceptions/exceptions.py:99` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-013: Documented extra: CogneeSystemError

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/exceptions.py:69
**Export:** CogneeSystemError

**Issue:** `SKILL.md:289` documents `CogneeSystemError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CogneeSystemError` is a documented extra, a name the source still declares at `cognee/exceptions/exceptions.py:69` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-014: Documented extra: CogneeTransientError

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/exceptions.py:114
**Export:** CogneeTransientError

**Issue:** `SKILL.md:292` documents `CogneeTransientError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CogneeTransientError` is a documented extra, a name the source still declares at `cognee/exceptions/exceptions.py:114` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-015: Documented extra: CogneeValidationError

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/exceptions.py:84
**Export:** CogneeValidationError

**Issue:** `SKILL.md:227` documents `CogneeValidationError`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `CogneeValidationError` is a documented extra, a name the source still declares at `cognee/exceptions/exceptions.py:84` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-016: Documented extra: DataPoint

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/low_level.py:2
**Export:** DataPoint

**Issue:** `SKILL.md:29` documents `DataPoint`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `DataPoint` is a documented extra, a name the source still declares at `cognee/low_level.py:2` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-017: Documented extra: DistillationResult

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/session_distillation/models.py:94
**Export:** DistillationResult

**Issue:** `SKILL.md:147` documents `DistillationResult`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `DistillationResult` is a documented extra, a name the source still declares at `cognee/modules/session_distillation/models.py:94` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-018: Documented extra: Edge

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/infrastructure/engine/models/Edge.py:13
**Export:** Edge

**Issue:** `SKILL.md:221` documents `Edge`, which the enumerated source API surface lacks and the source still declares; of the 5 files that declare it, the skill cites only `cognee/infrastructure/engine/models/Edge.py`

**Remediation:** No change: `Edge` is a documented extra, a name the source still declares at `cognee/infrastructure/engine/models/Edge.py:13` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-019: Documented extra: EntitySpec

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/graph_models/spec.py:90
**Export:** EntitySpec

**Issue:** `references/full-api-reference.md:279` documents `EntitySpec`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `EntitySpec` is a documented extra, a name the source still declares at `cognee/modules/graph_models/spec.py:90` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-020: Documented extra: ExtendableDataPoint

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/infrastructure/engine/models/ExtendableDataPoint.py:4
**Export:** ExtendableDataPoint

**Issue:** `SKILL.md:221` documents `ExtendableDataPoint`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `ExtendableDataPoint` is a documented extra, a name the source still declares at `cognee/infrastructure/engine/models/ExtendableDataPoint.py:4` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-021: Documented extra: FromIdentity

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/infrastructure/engine/models/FieldAnnotations.py:95
**Export:** FromIdentity

**Issue:** `SKILL.md:221` documents `FromIdentity`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `FromIdentity` is a documented extra, a name the source still declares at `cognee/infrastructure/engine/models/FieldAnnotations.py:95` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-022: Documented extra: GraphSchemaSpec

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/graph_models/spec.py:108
**Export:** GraphSchemaSpec

**Issue:** `references/full-api-reference.md:279` documents `GraphSchemaSpec`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `GraphSchemaSpec` is a documented extra, a name the source still declares at `cognee/modules/graph_models/spec.py:108` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-023: Documented extra: LLMGateway

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/infrastructure/llm/LLMGateway.py:106
**Export:** LLMGateway

**Issue:** `references/core-workflow.md:444` documents `LLMGateway`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `LLMGateway` is a documented extra, a name the source still declares at `cognee/infrastructure/llm/LLMGateway.py:106` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

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

**Issue:** `SKILL.md:134` documents `PipelineRunInfo`, which the enumerated source API surface lacks and the source still declares

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

### GAP-029: Documented extra: SkillRunEntry

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/memory/entries.py:82
**Export:** SkillRunEntry

**Issue:** `SKILL.md:180` documents `SkillRunEntry`, which the enumerated source API surface lacks and the source still declares

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

**Issue:** `references/core-workflow.md:383` documents `UpdateResult`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `UpdateResult` is a documented extra, a name the source still declares at `cognee/api/v1/update/result.py:37` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-032: Documented extra: __version__

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/__init__.py:22
**Export:** __version__

**Issue:** `SKILL.md:28` documents `__version__`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `__version__` is a documented extra, a name the source still declares at `cognee/__init__.py:22` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-033: Documented extra: add_data_points

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/tasks/storage/add_data_points.py:70
**Export:** add_data_points

**Issue:** `SKILL.md:116` documents `add_data_points`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `add_data_points` is a documented extra, a name the source still declares at `cognee/tasks/storage/add_data_points.py:70` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-034: Documented extra: find_remediation

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/remediation.py:131
**Export:** find_remediation

**Issue:** `SKILL.md:294` documents `find_remediation`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `find_remediation` is a documented extra, a name the source still declares at `cognee/exceptions/remediation.py:131` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-035: Documented extra: get_default_tasks

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/cognify/cognify.py:565
**Export:** get_default_tasks

**Issue:** `references/core-workflow.md:183` documents `get_default_tasks`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_default_tasks` is a documented extra, a name the source still declares at `cognee/api/v1/cognify/cognify.py:565` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-036: Documented extra: get_errored_run_info

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/models/PipelineRunInfo.py:62
**Export:** get_errored_run_info

**Issue:** `references/full-api-reference.md:574` documents `get_errored_run_info`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `get_errored_run_info` is a documented extra, a name the source still declares at `cognee/modules/pipelines/models/PipelineRunInfo.py:62` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-037: Documented extra: graph_model_from_spec

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/graph_models/compiler.py:135
**Export:** graph_model_from_spec

**Issue:** `references/full-api-reference.md:279` documents `graph_model_from_spec`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `graph_model_from_spec` is a documented extra, a name the source still declares at `cognee/modules/graph_models/compiler.py:135` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-038: Documented extra: graph_model_to_graph_schema

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/shared/graph_model_utils.py:93
**Export:** graph_model_to_graph_schema

**Issue:** `references/full-api-reference.md:282` documents `graph_model_to_graph_schema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `graph_model_to_graph_schema` is a documented extra, a name the source still declares at `cognee/shared/graph_model_utils.py:93` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-039: Documented extra: graph_schema_to_graph_model

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/shared/graph_model_utils.py:44
**Export:** graph_schema_to_graph_model

**Issue:** `references/full-api-reference.md:282` documents `graph_schema_to_graph_model`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `graph_schema_to_graph_model` is a documented extra, a name the source still declares at `cognee/shared/graph_model_utils.py:44` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-040: Documented extra: graph_spec_to_json_schema

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/graph_models/compiler.py:119
**Export:** graph_spec_to_json_schema

**Issue:** `references/full-api-reference.md:279` documents `graph_spec_to_json_schema`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `graph_spec_to_json_schema` is a documented extra, a name the source still declares at `cognee/modules/graph_models/compiler.py:119` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-041: Documented extra: is_tracing_enabled

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/observability/trace_context.py:62
**Export:** is_tracing_enabled

**Issue:** `references/full-api-reference.md:304` documents `is_tracing_enabled`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `is_tracing_enabled` is a documented extra, a name the source still declares at `cognee/modules/observability/trace_context.py:62` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-042: Documented extra: pipeline_needs_llm

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/tasks/task.py:160
**Export:** pipeline_needs_llm

**Issue:** `SKILL.md:268` documents `pipeline_needs_llm`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `pipeline_needs_llm` is a documented extra, a name the source still declares at `cognee/modules/pipelines/tasks/task.py:160` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-043: Documented extra: pipelines

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/__init__.py:1
**Export:** pipelines

**Issue:** `SKILL.md:8` documents `pipelines`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `pipelines` is a documented extra, a name the source still declares at `cognee/modules/pipelines/__init__.py:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-044: Documented extra: remediation_for

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/exceptions/remediation.py:146
**Export:** remediation_for

**Issue:** `SKILL.md:294` documents `remediation_for`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `remediation_for` is a documented extra, a name the source still declares at `cognee/exceptions/remediation.py:146` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-046: Documented extra: run_relational_migrations

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/run_migrations.py:11
**Export:** run_relational_migrations

**Issue:** `references/full-api-reference.md:409` documents `run_relational_migrations`, which the enumerated source API surface lacks and the source still declares; of the 2 files that declare it, the skill cites only `cognee/run_migrations.py`

**Remediation:** No change: `run_relational_migrations` is a documented extra, a name the source still declares at `cognee/run_migrations.py:11` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-047: Documented extra: setup

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/engine/operations/setup.py:9
**Export:** setup

**Issue:** `SKILL.md:221` documents `setup`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `setup` is a documented extra, a name the source still declares at `cognee/modules/engine/operations/setup.py:9` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-050: Documented extra: task

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/tasks/task.py:124
**Export:** task

**Issue:** `SKILL.md:104` documents `task`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `task` is a documented extra, a name the source still declares at `cognee/modules/pipelines/tasks/task.py:124` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-051: Documented extra: task_summary

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/modules/pipelines/tasks/task.py:169
**Export:** task_summary

**Issue:** `references/full-api-reference.md:564` documents `task_summary`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `task_summary` is a documented extra, a name the source still declares at `cognee/modules/pipelines/tasks/task.py:169` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-052: Documented extra: tools

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/tools/tools.py:1
**Export:** tools

**Issue:** `SKILL.md:13` documents `tools`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `tools` is a documented extra, a name the source still declares at `cognee/api/v1/tools/tools.py:1` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-053: Documented extra: visualize_graph_json

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/visualize/visualize.py:271
**Export:** visualize_graph_json

**Issue:** `references/full-api-reference.md:337` documents `visualize_graph_json`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `visualize_graph_json` is a documented extra, a name the source still declares at `cognee/api/v1/visualize/visualize.py:271` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-054: Documented extra: visualize_multi_user_graph

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/visualize/visualize.py:611
**Export:** visualize_multi_user_graph

**Issue:** `references/full-api-reference.md:339` documents `visualize_multi_user_graph`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `visualize_multi_user_graph` is a documented extra, a name the source still declares at `cognee/api/v1/visualize/visualize.py:611` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-055: Documented extra: visualize_semantic_json

**Severity:** Info
**Category:** Structural (observation)
**Source:** cognee/api/v1/visualize/visualize.py:317
**Export:** visualize_semantic_json

**Issue:** `references/full-api-reference.md:338` documents `visualize_semantic_json`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `visualize_semantic_json` is a documented extra, a name the source still declares at `cognee/api/v1/visualize/visualize.py:317` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-057: multi-denominator reporting — barrel vs documented surface

**Severity:** Info
**Category:** Coverage (multi-denominator)
**Source:** skills/oms-cognee/1.6.2/oms-cognee/metadata.json

**Issue:** barrel=102, documented=86

**Remediation:** No action required: the barrel and the documented surface measure different sets by design, and the report records both counts.

### GAP-059: Not checked by script: LLMGateway

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/pipelines-and-datapoints.md:431
**Export:** LLMGateway

**Issue:** references/pipelines-and-datapoints.md:431 writes acreate_structured_output(text, system_prompt, PydanticModel, **kwargs); the source declares acreate_structured_output(text_input: str, system_prompt: str, response_model: type[T], **kwargs) at cognee/infrastructure/llm/LLMGateway.py:113, so a caller who passes text= or PydanticModel= by keyword fails

**Remediation:** Correct the documentation to match the source; no script checks this.

### Discovery Quality

**Discovery Test:** not run: the hard gate blocked the run
