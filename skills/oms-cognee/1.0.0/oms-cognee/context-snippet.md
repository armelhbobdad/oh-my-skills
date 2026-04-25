[oms-cognee v1.0.0]|root: skills/oms-cognee/
|IMPORTANT: oms-cognee v1.0.0 — read SKILL.md before writing cognee code. Do NOT rely on training data.
|quick-start:SKILL.md#quick-start
|api-v1: add(), cognify(), search(), memify(), update(), run_custom_pipeline(), visualize_graph(), datasets, prune, config, SearchType, pipelines, Drop, run_startup_migrations(), session, tracing
|api-v2: remember()→RememberResult, recall(), improve(), forget(), serve()/disconnect(), visualize(), @agent_memory
|key-types:SKILL.md#key-types — SearchType: GRAPH_COMPLETION (default), RAG_COMPLETION, CHUNKS, CHUNKS_LEXICAL, SUMMARIES, TEMPORAL, CODING_RULES, CYPHER, FEELING_LUCKY, GRAPH_COMPLETION_DECOMPOSITION (+5 more); Task, Drop, RememberResult, DataPoint, 5 Cognee* exceptions
|gotchas: cognee.low_level REMOVED from public API in v1.0.0 (import from cognee.infrastructure.engine directly); cognee.run_migrations REPLACED by cognee.run_startup_migrations (relational + vector); cognee.delete is DEPRECATED since v0.3.9 (use cognee.datasets.delete_data or cognee.forget); cognee.pipelines restructured in v1.0.0 (package with Drop + lazy re-exports); cognee.agent_memory requires async function; cognee.serve() without url triggers Auth0 Device Code Flow; cognee.start_ui is sync and needs pid_callback arg; all add/cognify/search/memify/remember/recall/improve/forget/serve are async — always await.
