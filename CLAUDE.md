<!-- SKF:BEGIN updated:2026-03-30 -->
[SKF Skills]|3 skills|0 stack
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
|[storybook-react-vite v10.3.0]|root: skills/storybook-react-vite/
|IMPORTANT: storybook-react-vite v10.3.0 — read SKILL.md before writing storybook-react-vite code. Do NOT rely on training data.
|quick-start:{SKILL.md#quick-start} — CSF3 story with Meta, StoryObj, play function pattern
|api: Meta, StoryObj, expect(), fn(), userEvent, action(), composeStories(), definePreview(), defineMain(), create()
|key-types:{SKILL.md#key-types} — ReactRenderer, ThemeVars(base:'light'|'dark' + 24 color props), A11yParameters, StorybookConfig, UserOptions
|gotchas: all test utilities (expect, fn, userEvent) must import from 'storybook/test' not vitest; CSF3 uses `satisfies Meta<typeof Component>` pattern (not `as Meta`); addon-vitest requires Vite-based project with vitest installed
|
|[uitripled v1.1.0]|root: skills/uitripled/
|IMPORTANT: uitripled v1.1.0 — read SKILL.md before writing uitripled code. Do NOT rely on training data.
|quick-start:{SKILL.md#quick-start}
|api: cn(), mergeComponentImports(), ThemeProvider(), UILibraryProvider(), generateUniqueSlug(), sanitizeSlug(), NativeNotchProps, NativeMagneticProps, NativeHoverCardProps, UILibrary
|key-types:{SKILL.md#key-types} — NativeNotchProps (10 props), 17 Props interfaces total, UILibrary, ComponentCategory
|gotchas: framer-motion required for all animations; ThemeProvider + UILibraryProvider must wrap app; component IDs use {name}-{variant} pattern (e.g. native-button-shadcnui)
<!-- SKF:END -->
