# Evidence Report: oms-cognee

## Update Operation — 2026-04-12

**Trigger:** audit-skill chain (from `drift-report-20260412-191200.md`, CRITICAL score)
**Forge Tier:** Deep
**Mode:** normal
**Source version:** v0.5.8 → **v1.0.0** (commit `b51dcce1` → `3c048aa4`)

### Changes Detected
- Files modified: 6 (`__init__.py`, `add.py`, `search.py`, `SearchType.py`, `delete/`, `run_migrations.py`)
- Files added: 9 (V2 API: `remember.py`, `recall.py`, `improve.py`, `forget.py`, `serve.py`, `disconnect.py`; `agent_memory/decorator.py`; `pipelines/types.py`; `pipelines/__init__.py`)
- Files deleted: 1 (`cognee/pipelines.py` — relocated)
- Exports affected: 16 (11 added, 2 removed, 3 modified signatures, 2 relocated)

### Merge Results
- Exports updated: 3 (`add`, `search`, `SearchType`)
- Exports added: 11 (`Drop`, `run_startup_migrations`, `remember`, `RememberResult`, `recall`, `improve`, `forget`, `serve`, `disconnect`, `visualize`, `agent_memory`)
- Exports removed: 2 (`low_level`, `run_migrations`)
- Exports relocated: 2 (`delete`, `pipelines`)
- [MANUAL] sections preserved: 2 (`quick-start-notes`, `additional-notes`) — byte-identical
- Conflicts resolved: 0 (clean merge)

### Validation Summary
- Spec compliance: PASS (quality score: 100/100)
- [MANUAL] integrity: PASS (2 sections verified byte-identical)
- Confidence tiers: PASS (34 exports all T1)
- Provenance: PASS (all exports have file:line citations)

### Description Guard
- Restored: false
- Triggering tool: —
- Original description preserved: true
- Notes: description was shortened in-workflow to meet 1024-char spec limit before any external tool touched the file

### Context Snippet
- Regenerated: true
- Triggers fired: headline-exports, version, gotchas
- Notes: Major version bump v0.5.8 → v1.0.0 with 11 new exports (V2 API, Drop, agent_memory); gotchas section added entries for low_level removal and run_migrations replacement.

## Update Operation — 2026-04-13

**Trigger:** from-test-report (`forge-data/oms-cognee/1.0.0/test-report-oms-cognee.md`, PASS 98.7% with 1 High gap)
**Forge Tier:** Deep
**Mode:** gap-driven
**Source version:** v1.0.0 (unchanged — commit `3c048aa4`)
**Workspace drift check:** ok (HEAD `3c048aa4` matches pinned)

### Changes Detected
- Files modified: 0 (source unchanged)
- Files added: 0
- Files deleted: 0
- Exports affected: 1 (GAP-001: `search` signature drift in references file)

### Merge Results
- Exports updated: 1 (`search` — references/full-api-reference.md signature block)
- Exports added: 0
- Exports removed: 0
- [MANUAL] sections preserved: 2 (`quick-start-notes`, `additional-notes`) — untouched (SKILL.md not modified)
- Conflicts resolved: 0 (clean merge)
- Gaps addressed: GAP-001 (High — appended `neighborhood_depth`, `neighborhood_seed_top_k` + validation caveat)
- Gaps deferred: GAP-002, GAP-003, GAP-004, GAP-005 (all Info, marked optional/not-recommended by the test report)

### Validation Summary
- Spec compliance: PASS (deferred to post-write; see §7)
- [MANUAL] integrity: PASS (2 sections verified, byte-identical — SKILL.md untouched)
- Confidence tiers: PASS (`search` T1, AST-verified, Deep tier consistent)
- Provenance: PASS (`search` citation spot-check verified at `cognee/api/v1/search/search.py:27`)

### Description Guard
- Restored: false
- Triggering tool: —
- Original description preserved: true
- Notes: gap-driven run did not touch SKILL.md frontmatter — only references/full-api-reference.md modified

### Context Snippet
- Regenerated: false
- Triggers fired: —
- Notes: Gap-driven repair in references/ file — headline exports, version, and gotchas unchanged; snippet remains valid against prior surface

## Update Operation — 2026-04-13T01:56Z

**Trigger:** test-report (forge-data/oms-cognee/1.0.0/test-report-oms-cognee.md, PASS 97.98%)
**Forge Tier:** Deep
**Mode:** gap-driven
**Workspace drift check:** ok (HEAD 3c048aa4 matches pinned 3c048aa4)

### Changes Detected
- Files modified: 3 (SKILL.md, references/full-api-reference.md, references/core-workflow.md)
- Files added: 0
- Files deleted: 0
- Exports affected: 2 (`search`, `add`)
- Gaps addressed: GAP-001 (Low — search() line drift L26→L27), GAP-002 (Low — add() line drift L21→L22 + missing `run_in_background` param in full-api-reference.md)
- Gaps deferred: GAP-003 (Info — section classification, optional), GAP-004 (Info — discovery testing, advisory)

### Spot-check Verification (live source at pinned commit 3c048aa4)
- `async def search(` at `cognee/api/v1/search/search.py:27` → verified
- `async def add(` at `cognee/api/v1/add/add.py:22` → verified
- `run_in_background: bool = False` at `cognee/api/v1/add/add.py:42` → verified (confirmed present in live signature between `importance_weight` and `**kwargs`)

### Merge Results
- Exports updated: 2 (provenance-line fixes + 1 missing-param backfill in ref file)
- Exports added: 0
- Exports removed: 0
- [MANUAL] sections preserved: 2 (quick-start-notes @ SKILL.md:85, additional-notes @ SKILL.md:246 — byte-identical)
- Conflicts resolved: 0

### Edits Applied
- `SKILL.md:81` — `search/search.py:L26` → `L27`
- `SKILL.md:129` — `search/search.py:L26` → `L27`
- `references/full-api-reference.md:30-44` — inserted `run_in_background: bool = False,` between `importance_weight` and `**kwargs` in `add()` signature block
- `references/full-api-reference.md:51` — `add/add.py:L21` → `L22`
- `references/core-workflow.md:43` — `add/add.py:L21` → `L22`

### Validation Summary
- Spec compliance: PASS (structural; post-write skill-check deferred to test re-run)
- [MANUAL] integrity: PASS (2/2 blocks byte-identical)
- Confidence tiers: PASS (2/2 exports T1 AST-verified)
- Provenance: PASS (0 stale L26/L21 references remain across SKILL.md + references/)

### Description Guard
- Restored: false
- Triggering tool: —
- Original description preserved: true
- Notes: —

### Context Snippet
- Regenerated: false
- Triggers fired: —
- Notes: Gap-driven line-drift repair — headline exports, version, and gotchas unchanged; snippet remains valid against prior surface

## Update Operation — 2026-10-07

**Trigger:** manual (`@Ferris US oms-cognee --target-ref v1.6.2`), following audit-skill drift report `drift-report-20261007-000457.md` (CRITICAL, 163 findings)
**Forge Tier:** Deep
**Mode:** normal
**Source commit:** 3c048aa4 → ba3631f2 (2298 added, 1155 modified, 340 deleted files); re-pinned from `v1.0.0` to `v1.6.2`

### Changes Detected
- Files modified: 26
- Files added: 171
- Files deleted: 0
- Exports affected: 69 (23 modified, 38 new, 2 deleted, 6 moved, 0 renamed)

### Merge Results
- Exports updated: 23
- Exports added: 38 in modified files (37 internal helpers left untracked by the public-surface provenance policy, `run_migrations` tracked), plus 22 new top-level public names from added files
- Exports removed: 2 (`run_startup_migrations`; the `session` module entry, re-homed as the `cognee/api/v1/session/__init__.py` SimpleNamespace)
- [MANUAL] sections preserved: 2 (quick-start-notes, additional-notes — byte-identical)
- Conflicts resolved: 0
- Audit remediation rows applied: 199 row-file applications (SKILL.md 72, full-api-reference.md 71, core-workflow.md 40, pipelines-and-datapoints.md 11, config.md 5); metadata.json and context-snippet.md rows applied in §2 and §5
- Independent review: 44 corrections across the five files; cross-file consistency sweep fixed 10 SKILL.md-vs-reference contradictions
- Provenance policy: public surface only (56 entries) by user decision; `apply` run literally would have written 437 entries

### Scope and Targeted Re-Extraction
- Authoritative files: {"candidates": 2, "promoted": 0, "skipped": 0, "deferred": 0, "pre_decided": 2, "already_tracked": 0, "decisions": [{"path": "AGENTS.md", "action": "in-scope", "heuristic": "agents.md", "reason": "brief scope.include already matches; scheduled for file_entries write"}, {"path": "CLAUDE.md", "action": "in-scope", "heuristic": "claude.md", "reason": "brief scope.include already matches; scheduled for file_entries write"}]}
- Scope reconciliation before detection: {"drift_report": "forge-data/oms-cognee/1.0.0/drift-report-20261007-000457.md", "candidates": 11, "promoted": 8, "skipped": 3, "deferred": 0, "pre_decided": 0, "decisions": [{"path": "cognee/api/v1/agents/agents.py", "action": "promoted", "evidence": "exports `agents` through `cognee/__init__.py`"}, {"path": "cognee/api/v1/push/push.py", "action": "promoted", "evidence": "exports `PushResult` through `cognee/__init__.py`"}, {"path": "cognee/api/v1/validate/validate.py", "action": "promoted", "evidence": "exports `ValidationIssue`, `ValidationReport`, `ValidationStatus` through `cognee/__init__.py`"}, {"path": "cognee/api/v1/visualize/memory_provenance.py", "action": "promoted", "evidence": "exports `get_memory_provenance_graph`, `visualize_memory_provenance` through `cognee/__init__.py`"}, {"path": "cognee/memory/entries.py", "action": "promoted", "evidence": "exports `FeedbackEntry`, `MemoryEntry`, `QAEntry`, `TraceEntry` through `cognee/__init__.py`"}, {"path": "cognee/modules/migration/export.py", "action": "promoted", "evidence": "exports `ExportResult` through `cognee/__init__.py`"}, {"path": "cognee/modules/session_lifecycle/models.py", "action": "promoted", "evidence": "exports `SessionModelUsage`, `SessionRecord` through `cognee/__init__.py`"}, {"path": "cognee/version.py", "action": "promoted", "evidence": "exports `get_cognee_version` through `cognee/__init__.py`"}, {"path": "cognee/infrastructure/background_tasks.py", "action": "skipped", "evidence": "exports `wait_for_background_tasks` through `cognee/__init__.py`"}, {"path": "cognee/shared/env_file.py", "action": "skipped", "evidence": "exports `describe_resolution`, `load_env_file` through `cognee/__init__.py`"}, {"path": "cognee/shared/logging_utils.py", "action": "skipped", "evidence": "exports `setup_logging` through `cognee/__init__.py`"}]}
- Scope reconciliation after detection: none (deletion ratio 0.057 = 2/35, below the 0.50 trigger)
- Targeted re-extraction: none

### Validation Summary
- Spec compliance: PASS (quality score 100/100: frontmatter 30, description 30, body 20, links 10, file 10; 0 errors, 0 warnings, nothing to --fix)
- [MANUAL] integrity: PASS (2/2 blocks byte-identical; staged and published checks both ok)
- Confidence tiers: WARN (relabeled to T1-low by the Relabel Rule: start_visualization_server, visualization_server, Drop, disconnect, visualize, enable_tracing, disable_tracing, get_all_traces, clear_traces, __version__)
- Provenance: PASS (56/56 entries, 0 missing/orphaned/stale, 42 node kinds checked; fixed 2 citation prefixes for enable_tracing [AST:]→[SRC:] after its Relabel Rule downgrade; 3 module/alias entries have no definition line to check)
- Diff: 0 new, 0 fixed issues (skill-check diff 1.0.0 vs 1.6.2)
- Security: SKIP (SNYK_TOKEN not configured)

### Description Guard
- Restored: false
- Triggering tool: —
- Original description preserved: true
- Notes: —

### Context Snippet
- Regenerated: true
- Triggers fired: headline-exports, version, gotchas
- Notes: Version bumped 1.0.0 → 1.6.2; run_startup_migrations replaced by run_migrations and the v1.6 public API (agents, push, export, report, validate, tools, memory entries) added to the api lines; SearchType default and the low_level/run_migrations/serve gotchas rewritten (wait_for_background_tasks left out: out of scope by user decision)


- Active symlink: active_symlink_update: flipped (1.0.0 -> 1.6.2); verify: ok (1.6.2)
- Workspace clone: source_tree_advance: advanced 3c048aa -> ba3631f
