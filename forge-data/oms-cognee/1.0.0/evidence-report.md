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
