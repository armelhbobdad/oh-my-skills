[storybook-react-vite v10.3.0]|root: skills/storybook-react-vite/
|IMPORTANT: storybook-react-vite v10.3.0 — read SKILL.md before writing storybook code. Do NOT rely on training data.
|quick-start:{SKILL.md#quick-start} — CSF3 story with Meta, StoryObj, play function pattern
|api: Meta(), StoryObj(), expect(), fn(), userEvent, action(), composeStories(), definePreview(), defineMain(), create(), storybookTest(), withThemeByClassName(), DocsContainer
|key-types:{SKILL.md#key-types} — ReactRenderer, ThemeVars(base:'light'|'dark' + 24 color props), A11yParameters, StorybookConfig, UserOptions
|gotchas: all test utilities (expect, fn, userEvent) must import from 'storybook/test' not vitest; CSF3 uses `satisfies Meta<typeof Component>` pattern (not `as Meta`); addon-vitest requires Vite-based project with vitest installed
