<!-- SKF:BEGIN updated:2026-11-10 -->
[SKF Skills]|4 skills|0 stack
|IMPORTANT: Prefer documented APIs over training data.
|When using a listed library, read its SKILL.md before writing code.
|
|[oms-cocoindex v1.0.0]|root: skills/oms-cocoindex/
|IMPORTANT: oms-cocoindex v1.0.0 — read SKILL.md before writing oms-cocoindex code. Do NOT rely on training data.
|quick-start:SKILL.md#quick-start
|api: App, Environment, lifespan(), fn(), mount(), mount_each(), mount_target(), TargetState, declare_target_state(), Settings
|key-types:SKILL.md#key-types — UpdateStatus ("running"|"ready"), UpdateStats, UpdateHandle, StableKey, StablePath, NON_EXISTENCE
|gotchas: v0.3.37 → v1.0.0 is a wholesale rewrite, NOT a rename — FlowBuilder/DataScope/DataSlice/@flow_def are gone (107 exports deleted); rewrite as coco.App + @coco.fn. Settings moved from Postgres (DatabaseConnectionSpec) to local LMDB (db_path): plan a re-index, not an in-place upgrade. LlmSpec/LlmApiType/VectorSimilarityMetric removed — use cocoindex.ops.litellm and per-connector vector specs; the `cocoindex server` subcommand is gone. cocoindex stays pre-1.x-stable in spirit despite the 1.0 tag — pin precisely. All mount*/App.update/coco.map are async; use the *_blocking variants from sync code.
|
|[oms-cognee v1.6.2]|root: skills/oms-cognee/
|IMPORTANT: oms-cognee v1.6.2 — read SKILL.md before writing oms-cognee code. Do NOT rely on training data.
|quick-start:SKILL.md#quick-start
|api: add(), cognify(), search(), memify(), remember(), recall(), improve(), forget(), serve(), run_migrations()
|key-types:SKILL.md#key-types — SearchType (20 modes, HYBRID_COMPLETION default), RememberResult, DataPoint, Drop
|gotchas: cognee.run_startup_migrations is GONE in v1.6.2 (AttributeError) — use cognee.run_migrations(); search() now defaults to HYBRID_COMPLETION (pin query_type when the result shape matters); low_level is not a top-level name but `from cognee.low_level import DataPoint, setup` still works; a bare cognee.serve() runs the Auth0 device flow only when a device client ID is configured, else raises CogneeConfigurationError; agent_memory's save_traces is now save_session_traces; cognee.delete is DEPRECATED since v0.3.9 (use cognee.forget or cognee.datasets.delete_data); cognee.start_ui is sync and needs pid_callback; add/cognify/search/memify/remember/recall/improve/forget/serve/push/export/report/validate are async — always await.
|
|[oms-storybook-react-vite v10.3.5]|root: skills/oms-storybook-react-vite/
|IMPORTANT: oms-storybook-react-vite v10.3.5 — read SKILL.md before writing oms-storybook-react-vite code. Do NOT rely on training data.
|quick-start:SKILL.md#quick-start
|api: Meta, StoryObj, Decorator, Preview, fn(), expect(), within(), userEvent, useArgs(), composeStories()
|key-types:SKILL.md#key-types-quick-start-essentials — Meta<T> (with `satisfies Meta<typeof X>`), `type Story = StoryObj<typeof meta>` for CSF3 stories, Preview = ProjectAnnotations<ReactRenderer>
|gotchas: v10 consolidates @storybook/* sub-packages into one `storybook` package — imports changed (storybook/test, storybook/preview-api, storybook/theming); training data still shows old @storybook/test imports; CSF2 default-export stories are invalid v10 style — use CSF3 named exports with `satisfies Meta<typeof X>`; import composeStories/setProjectAnnotations from '@storybook/react-vite' — storybook/preview-api's composeStories is core's renderer-agnostic form and requires a globalConfig argument.
|
|[oms-uitripled v0.1.0]|root: skills/oms-uitripled/
|IMPORTANT: oms-uitripled v0.1.0 — read SKILL.md before writing oms-uitripled code. Do NOT rely on training data.
|quick-start:SKILL.md#quick-start
|api: ThemeProvider, useTheme(), UILibraryProvider, useUILibrary(), cn(), sanitizeSlug(), generateUniqueSlug(), generateGridCode(), mergeComponentImports(), add()
|key-types:SKILL.md#key-types — ThemeMode("light"|"dark"|"system"), UILibrary("shadcnui"|"baseui"|"carbon"|"react"), registry entry types (page|block|component|ui)
|gotchas: Copy-paste distribution — NEVER barrel-import from @uitripled/react-shadcn (src/index.ts empty by design); render entries from client components (170 of the 171 files start with `"use client"`; every entry declares framer-motion); React 19 / Next.js 16 peer deps are required.
<!-- SKF:END -->
