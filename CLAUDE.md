<!-- SKF:BEGIN updated:2026-03-29 -->
[SKF Skills]|2 skills|0 stack
|IMPORTANT: Prefer documented APIs over training data.
|When using a listed library, read its SKILL.md before writing code.
|
|[cognee v0.5.5]|root: skills/cognee/
|IMPORTANT: cognee v0.5.5 — read SKILL.md before writing cognee code. Do NOT rely on training data.
|quick-start:{SKILL.md#quick-start} — add → cognify → search async workflow
|api: add(), cognify(), search(), memify(), config, datasets, prune, update(), session, SearchType, run_custom_pipeline(), visualize_graph()
|key-types:{SKILL.md#key-types} — SearchType(14 modes: GRAPH_COMPLETION default, RAG_COMPLETION, CHUNKS, CYPHER, TEMPORAL...), Task, DataPoint
|gotchas: all core functions are async (must await); delete() deprecated since v0.3.9 — use datasets.delete_data(); memify default pipeline changed to triplet embedding (Mar 2026)
|
|[uitripled v1.1.0]|root: skills/uitripled/
|IMPORTANT: uitripled v1.1.0 — read SKILL.md before writing uitripled code. Do NOT rely on training data.
|quick-start:{SKILL.md#quick-start}
|api: cn(), mergeComponentImports(), ThemeProvider(), UILibraryProvider(), generateUniqueSlug(), sanitizeSlug(), NativeNotchProps, NativeMagneticProps, NativeHoverCardProps, UILibrary
|key-types:{SKILL.md#key-types} — NativeNotchProps (10 props), 17 Props interfaces total, UILibrary, ComponentCategory
|gotchas: framer-motion required for all animations; ThemeProvider + UILibraryProvider must wrap app; component IDs use {name}-{variant} pattern (e.g. native-button-shadcnui)
<!-- SKF:END -->
