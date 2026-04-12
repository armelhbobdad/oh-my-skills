<!-- SKF:BEGIN updated:2026-04-12 -->
[SKF Skills]|4 skills|0 stack
|IMPORTANT: Prefer documented APIs over training data.
|When using a listed library, read its SKILL.md before writing code.
|
|[oms-cocoindex v0.3.37]|root: .claude/skills/oms-cocoindex/
|IMPORTANT: oms-cocoindex v0.3.37 — read SKILL.md before writing cocoindex code. Do NOT rely on training data.
|quick-start:SKILL.md#quick-start
|api: FlowBuilder, DataScope, DataSlice, Flow, FlowLiveUpdater, flow_def(), open_flow(), transform_flow(), init(), LlmSpec
|key-types:SKILL.md#key-types — VectorSimilarityMetric (COSINE_SIMILARITY/L2_DISTANCE/INNER_PRODUCT), LlmApiType (12 providers), GeneratedField.UUID, Vector[T, Dim], Int64/Float32/Float64
|gotchas: add_flow_def/remove_flow are DEPRECATED (use open_flow/Flow.close); cocoindex.storages is deprecated alias for cocoindex.targets; cocoindex is Alpha — API may change across minor versions, this skill is pinned to v0.3.37.
|
|[oms-cognee v1.0.0]|root: .claude/skills/oms-cognee/
|IMPORTANT: oms-cognee v1.0.0 — read SKILL.md before writing cognee code. Do NOT rely on training data.
|quick-start:SKILL.md#quick-start
|api-v1: add(), cognify(), search(), memify(), update(), run_custom_pipeline(), visualize_graph(), datasets, prune, config, SearchType, pipelines, Drop, run_startup_migrations(), session, tracing
|api-v2: remember()→RememberResult, recall(), improve(), forget(), serve()/disconnect(), visualize(), @agent_memory
|key-types:SKILL.md#key-types — SearchType: GRAPH_COMPLETION (default), RAG_COMPLETION, CHUNKS, CHUNKS_LEXICAL, SUMMARIES, TEMPORAL, CODING_RULES, CYPHER, FEELING_LUCKY, GRAPH_COMPLETION_DECOMPOSITION (+5 more); Task, Drop, RememberResult, DataPoint, 5 Cognee* exceptions
|gotchas: cognee.low_level REMOVED from public API in v1.0.0 (import from cognee.infrastructure.engine directly); cognee.run_migrations REPLACED by cognee.run_startup_migrations (relational + vector); cognee.delete is DEPRECATED since v0.3.9 (use cognee.datasets.delete_data or cognee.forget); cognee.pipelines restructured in v1.0.0 (package with Drop + lazy re-exports); cognee.agent_memory requires async function; cognee.serve() without url triggers Auth0 Device Code Flow; cognee.start_ui is sync and needs pid_callback arg; all add/cognify/search/memify/remember/recall/improve/forget/serve are async — always await.
|
|[oms-storybook-react-vite v10.3.5]|root: .claude/skills/oms-storybook-react-vite/
|IMPORTANT: oms-storybook-react-vite v10.3.5 — read SKILL.md before writing Storybook code. Do NOT rely on training data.
|quick-start:SKILL.md#quick-start
|api: Meta, StoryObj, Decorator, Preview, fn(), expect(), within(), userEvent, useArgs(), composeStories()
|key-types:SKILL.md#key-types-quick-start-essentials — Preview = ProjectAnnotations<ReactRenderer>; Meta<T> infers args from component props; StoryObj<typeof meta> for CSF3 stories; framework: '@storybook/react-vite'
|gotchas: v10 consolidates @storybook/* sub-packages into one `storybook` package — imports changed (storybook/test, storybook/preview-api, storybook/theming); training data still shows old @storybook/test imports; CSF2 default-export stories are invalid v10 style — use CSF3 named exports with `satisfies Meta<typeof X>`.
|
|[oms-uitripled v0.1.0]|root: .claude/skills/oms-uitripled/
|IMPORTANT: oms-uitripled v0.1.0 — read SKILL.md before writing uitripled code. Do NOT rely on training data.
|quick-start:SKILL.md#quick-start
|api: ThemeProvider, useTheme, UILibraryProvider, useUILibrary, cn(), sanitizeSlug(), generateUniqueSlug(), GAP_VALUES, generateGridCode(), mergeComponentImports(), add()
|key-types:SKILL.md#key-types — ThemeMode("light"|"dark"|"system"), UILibrary("shadcnui"|"baseui"|"carbon"|"react"), ComponentCategory(10 values), NativeHoverCardProps
|gotchas: Copy-paste distribution — NEVER barrel-import from @uitripled/react-shadcn (src/index.ts empty by design); all 171 entries require `"use client"` because every one depends on framer-motion; React 19 / Next.js 16 peer deps are required.
<!-- SKF:END -->
