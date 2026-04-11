[oms-cognee v0.5.8]|root: .claude/skills/oms-cognee/
|IMPORTANT: oms-cognee v0.5.8 — read SKILL.md before writing cognee code. Do NOT rely on training data.
|quick-start:SKILL.md#quick-start
|api: add(), cognify(), search(), memify(), update(), run_custom_pipeline(), visualize_graph(), datasets, prune, SearchType
|key-types:SKILL.md#key-types — SearchType: GRAPH_COMPLETION (default), RAG_COMPLETION, CHUNKS, CHUNKS_LEXICAL, SUMMARIES, TEMPORAL, CODING_RULES, CYPHER, FEELING_LUCKY (+5 more); Task, DataPoint, 5 Cognee* exceptions
|gotchas: cognee.delete is DEPRECATED since v0.3.9 (use cognee.datasets.delete_data); cognee.start_ui is sync (not async) and needs pid_callback arg; cognee.start_visualization_server is a module, call .visualization_server(port) on it; all add/cognify/search/memify are async — always await.
