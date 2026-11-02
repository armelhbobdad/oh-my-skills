[oms-cocoindex v1.0.0]|root: skills/oms-cocoindex/
|IMPORTANT: oms-cocoindex v1.0.0 — read SKILL.md before writing oms-cocoindex code. Do NOT rely on training data.
|quick-start:SKILL.md#quick-start
|api: App, Environment, lifespan(), fn(), mount(), mount_each(), mount_target(), TargetState, declare_target_state(), Settings
|key-types:SKILL.md#key-types — UpdateStatus ("running"|"ready"), UpdateStats, UpdateHandle, StableKey, StablePath, NON_EXISTENCE
|gotchas: v0.3.37 → v1.0.0 is a wholesale rewrite, NOT a rename — FlowBuilder/DataScope/DataSlice/@flow_def are gone (107 exports deleted); rewrite as coco.App + @coco.fn. Settings moved from Postgres (DatabaseConnectionSpec) to local LMDB (db_path): plan a re-index, not an in-place upgrade. LlmSpec/LlmApiType/VectorSimilarityMetric removed — use cocoindex.ops.litellm and per-connector vector specs; the `cocoindex server` subcommand is gone. cocoindex stays pre-1.x-stable in spirit despite the 1.0 tag — pin precisely. All mount*/App.update/coco.map are async; use the *_blocking variants from sync code.
