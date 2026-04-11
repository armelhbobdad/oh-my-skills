[oms-storybook-react-vite v10.3.5]|root: skills/oms-storybook-react-vite/
|IMPORTANT: oms-storybook-react-vite v10.3.5 — read SKILL.md before writing Storybook code. Do NOT rely on training data.
|quick-start:SKILL.md#quick-start — CSF3 story + preview.ts template; run preflight (cat .storybook/main.ts) first
|api: Meta, StoryObj, Decorator, Preview from '@storybook/react-vite'; fn(), expect(), within(), userEvent from 'storybook/test'; useArgs(), useState(), composeStories() from 'storybook/preview-api'; action() from 'storybook/actions'; withThemeByClassName() from '@storybook/addon-themes'; Canvas, Meta, Controls, Primary, Stories from '@storybook/addon-docs/blocks'
|key-types:SKILL.md#key-types — Preview = ProjectAnnotations<ReactRenderer>; Meta<T> infers args from component props; StoryObj<typeof meta> for CSF3 stories; framework: '@storybook/react-vite'
|gotchas: v10 consolidates @storybook/* sub-packages into one `storybook` package — imports changed (storybook/test, storybook/preview-api, storybook/theming); training data still shows old @storybook/test imports; CSF2 default-export stories are invalid v10 style — use CSF3 named exports with `satisfies Meta<typeof X>`
