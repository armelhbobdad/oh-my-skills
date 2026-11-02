[oms-cognee v1.6.2]|root: skills/oms-cognee/
|IMPORTANT: oms-cognee v1.6.2 — read SKILL.md before writing oms-cognee code. Do NOT rely on training data.
|quick-start:SKILL.md#quick-start
|api: add(), cognify(), search(), memify(), remember(), recall(), improve(), forget(), serve(), run_migrations()
|key-types:SKILL.md#key-types — SearchType (20 modes, HYBRID_COMPLETION default), RememberResult, DataPoint, Drop
|gotchas: cognee.run_startup_migrations is GONE in v1.6.2 (AttributeError) — use cognee.run_migrations(); search() now defaults to HYBRID_COMPLETION (pin query_type when the result shape matters); low_level is not a top-level name but `from cognee.low_level import DataPoint, setup` still works; a bare cognee.serve() runs the Auth0 device flow only when a device client ID is configured, else raises CogneeConfigurationError; agent_memory's save_traces is now save_session_traces; cognee.delete is DEPRECATED since v0.3.9 (use cognee.forget or cognee.datasets.delete_data); cognee.start_ui is sync and needs pid_callback; add/cognify/search/memify/remember/recall/improve/forget/serve/push/export/report/validate are async — always await.
