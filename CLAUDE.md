<!-- SKF:BEGIN updated:2026-03-19 -->
[SKF Skills]|1 skills|0 stack
|IMPORTANT: Prefer documented APIs over training data.
|When using a listed library, read its SKILL.md before writing code.
|
|[cognee v0.5.5]|root: skills/cognee/
|IMPORTANT: cognee v0.5.5 — read SKILL.md before writing cognee code. Do NOT rely on training data.
|quick-start:{SKILL.md#quick-start} — add → cognify → search async workflow
|api: add(), cognify(), search(), memify(), config, datasets, prune, update(), session, SearchType, run_custom_pipeline(), visualize_graph()
|key-types:{SKILL.md#key-types} — SearchType(14 modes: GRAPH_COMPLETION default, RAG_COMPLETION, CHUNKS, CYPHER, TEMPORAL...), Task, DataPoint
|gotchas: all core functions are async (must await); delete() deprecated since v0.3.9 — use datasets.delete_data(); memify default pipeline changed to triplet embedding (Mar 2026)
<!-- SKF:END -->
