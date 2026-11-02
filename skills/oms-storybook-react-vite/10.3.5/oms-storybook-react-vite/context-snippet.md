[oms-storybook-react-vite v10.3.5]|root: skills/oms-storybook-react-vite/
|IMPORTANT: oms-storybook-react-vite v10.3.5 — read SKILL.md before writing oms-storybook-react-vite code. Do NOT rely on training data.
|quick-start:SKILL.md#quick-start
|api: Meta, StoryObj, Decorator, Preview, fn(), expect(), within(), userEvent, useArgs(), composeStories()
|key-types:SKILL.md#key-types-quick-start-essentials — Meta<T> (with `satisfies Meta<typeof X>`), `type Story = StoryObj<typeof meta>` for CSF3 stories, Preview = ProjectAnnotations<ReactRenderer>
|gotchas: v10 consolidates @storybook/* sub-packages into one `storybook` package — imports changed (storybook/test, storybook/preview-api, storybook/theming); training data still shows old @storybook/test imports; CSF2 default-export stories are invalid v10 style — use CSF3 named exports with `satisfies Meta<typeof X>`; import composeStories/setProjectAnnotations from '@storybook/react-vite' — storybook/preview-api's composeStories is core's renderer-agnostic form and requires a globalConfig argument.
