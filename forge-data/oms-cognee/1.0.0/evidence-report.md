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
