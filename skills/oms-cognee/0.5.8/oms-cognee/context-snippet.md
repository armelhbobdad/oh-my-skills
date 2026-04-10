[oms-cognee v0.5.8]|root: skills/oms-cognee/
|IMPORTANT: oms-cognee v0.5.8 — read SKILL.md before writing cognee code. Do NOT rely on training data.
|quick-start:{SKILL.md#quick-start} — async add → cognify → search; set LLM_API_KEY first
|api: add(), cognify(), search(), memify(), update(), run_custom_pipeline(), visualize_graph(), run_migrations(), datasets, prune, config, SearchType, pipelines, low_level, session, enable_tracing(), disable_tracing(), get_last_trace(), get_all_traces(), clear_traces(), __version__
|key-types:{SKILL.md#key-types} — SearchType: GRAPH_COMPLETION (default), RAG_COMPLETION, CHUNKS, CHUNKS_LEXICAL, SUMMARIES, TEMPORAL, CODING_RULES, CYPHER, FEELING_LUCKY (+5 more); Task, DataPoint, 5 Cognee* exceptions
|gotchas:{SKILL.md#deprecations--gotchas} — cognee.delete is DEPRECATED since v0.3.9 — use cognee.datasets.delete_data; cognee.start_ui is sync (not async) and needs a pid_callback arg; cognee.start_visualization_server is a module, call .visualization_server(port) on it; all add/cognify/search/memify are async — always await
