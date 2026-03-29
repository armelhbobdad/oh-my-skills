---
name: storybook-react-vite
description: >
  Storybook React-Vite skill covering the full component development workflow — CSF story format,
  testing (expect, fn, userEvent), theming, manager/preview APIs, doc blocks, accessibility,
  and Vite builder configuration. Scoped to React-Vite framework with essential addons
  (a11y, docs, themes, vitest). Use when writing Storybook stories, tests, or configuration
  for React projects using Vite.
---

## Overview

Storybook v10.3.0 — component development environment for React projects using the Vite builder. Enables isolated UI development, visual testing, documentation, and accessibility auditing.

- **Source:** [storybookjs/storybook](https://github.com/storybookjs/storybook) @ v10.3.0 (commit 06cb6a6)
- **Language:** TypeScript (TSX)
- **Forge tier:** Deep (source + docs)
- **Public exports:** 730+ across 8 packages (storybook core, @storybook/react-vite, @storybook/react, @storybook/builder-vite, @storybook/addon-a11y, @storybook/addon-docs, @storybook/addon-themes, @storybook/addon-vitest)

`[SRC:code/core/package.json:L1]`

## Quick Start

A typical React-Vite story file using CSF3 format:

```tsx
import type { Meta, StoryObj } from '@storybook/react';
import { expect, fn, userEvent } from 'storybook/test';
import { MyComponent } from './MyComponent';

const meta = {
  component: MyComponent,
} satisfies Meta<typeof MyComponent>;
export default meta;
type Story = StoryObj<typeof meta>;

export const Default: Story = {
  args: { label: 'Click me' },
};

export const WithInteraction: Story = {
  args: { onClick: fn() },
  play: async ({ args, canvas }) => {
    await userEvent.click(canvas.getByRole('button'));
    await expect(args.onClick).toHaveBeenCalled();
  },
};
```

`[SRC:code/core/src/test/index.ts:L24]`
`[SRC:code/renderers/react/src/public-types.ts:L29]`

<!-- [MANUAL:after-quick-start] -->
<!-- Add custom quick start notes here. This section is preserved during skill updates. -->
<!-- [/MANUAL:after-quick-start] -->

## Common Workflows

**Write a CSF3 story:**
`import type { Meta, StoryObj } from '@storybook/react'` → `const meta = { component: MyComp } satisfies Meta<typeof MyComp>` → `export default meta` → `export const Primary: Story = { args: {...} }`

**Test interactions:**
`import { expect, fn, userEvent } from 'storybook/test'` → `play: async ({ canvas }) => { await userEvent.click(canvas.getByRole('button')); await expect(...).toHaveBeenCalled(); }`

**Apply theming:**
`import { create } from 'storybook/theming'` → `create({ base: 'dark', brandTitle: 'My App', colorPrimary: '#ff4785' })` — use in `.storybook/manager.ts` or `preview.ts`

**Configure main.ts:**
`import type { StorybookConfig } from '@storybook/react-vite'` → `const config: StorybookConfig = { framework: '@storybook/react-vite', stories: ['../src/**/*.stories.@(ts|tsx)'], addons: [...] }` → Verify: `npm run storybook` starts without errors

**Add Vitest testing:**
`npx storybook add @storybook/addon-vitest` → `import { storybookTest } from '@storybook/addon-vitest/vitest-plugin'` → add `storybookTest()` to `vitest.config.ts` plugins → Verify: `vitest --project=storybook` discovers stories

**Portable stories for unit tests:**
`import { composeStories } from '@storybook/react'` → `const { Primary } = composeStories(stories)` → `render(<Primary />)` → assert

## Key API Summary

| Function | Package | Purpose |
|----------|---------|---------|
| `Meta<T>` | @storybook/react | Component metadata type for CSF stories `[SRC:code/renderers/react/src/public-types.ts:L29]` |
| `StoryObj<T>` | @storybook/react | Story object type for CSF3 `[SRC:code/renderers/react/src/public-types.ts:L34]` |
| `expect` | storybook/test | Instrumented assertion (vitest-compatible) `[SRC:code/core/src/test/index.ts:L24]` |
| `fn()` | storybook/test | Create mock function (spy) `[SRC:code/core/src/test/index.ts:L26]` |
| `userEvent` | storybook/test | Instrumented user event simulation `[SRC:code/core/src/test/index.ts:L28]` |
| `action(name)` | storybook/actions | Create action logger for callbacks `[SRC:code/core/src/actions/index.ts:L1]` |
| `composeStories(module)` | @storybook/react | Compose all stories for portable testing `[SRC:code/renderers/react/src/portable-stories.ts:L18]` |
| `composeStory(story, meta)` | @storybook/react | Compose single story for testing `[SRC:code/renderers/react/src/portable-stories.ts:L12]` |
| `definePreview(config)` | storybook/internal/csf | CSF factory for preview configuration `[SRC:code/core/src/csf/definePreview.ts:L8]` |
| `defineMain(config)` | @storybook/react-vite/node | Type-safe main.ts configuration `[SRC:code/frameworks/react-vite/src/node/index.ts:L1]` |
| `create(vars?)` | storybook/theming | Create custom Storybook theme `[SRC:code/core/src/theming/create.ts:L38]` |
| `themes` | storybook/theming | Built-in light/dark/normal themes `[SRC:code/core/src/theming/themes.ts:L1]` |
| `storybookTest(options?)` | @storybook/addon-vitest | Vitest plugin for story-based testing `[SRC:code/addons/vitest/src/vitest-plugin/index.ts:L28]` |
| `withThemeByClassName(config)` | @storybook/addon-themes | Theme switching via CSS class `[SRC:code/addons/themes/src/decorators/class-name.ts:L8]` |
| `DocsContainer` | @storybook/addon-docs/blocks | Container for automatic docs page `[SRC:code/addons/docs/src/blocks/DocsContainer.tsx:L22]` |

<!-- [MANUAL:after-api-summary] -->
<!-- Add custom API notes here. This section is preserved during skill updates. -->
<!-- [/MANUAL:after-api-summary] -->

## Key Types

**ReactRenderer** `[SRC:code/renderers/react/src/types.ts:L12]`:
`{ component: ComponentType, storyResult: StoryFnReactReturnType, mount: (ui?: JSX.Element) => Promise<Canvas> }` — the renderer interface binding Storybook's core to React.

**ThemeVars** `[SRC:code/core/src/theming/types.ts:L1]`:
`{ base: 'light' | 'dark', colorPrimary, colorSecondary, appBg, brandTitle }` — 24+ color/UI properties. Most commonly customized: `base`, `colorPrimary`, `brandTitle`, `appBg`. See [Full Type Definitions](references/full-type-definitions.md) for complete property list.

**A11yParameters** `[SRC:code/addons/a11y/src/types.ts:L1]`:
`{ element?: string, context?: RunOptions['context'], options?: RunOptions['options'], config?: Spec, disable?: boolean, test?: 'todo' | 'error' | 'warn' }` — per-story accessibility configuration.

**StorybookConfig** (react-vite) `[SRC:code/frameworks/react-vite/src/types.ts:L1]`:
Framework-specific config extending core StorybookConfig with `framework: { name: '@storybook/react-vite', options?: FrameworkOptions }`, `viteFinal`, `stories`, `addons`, `docs`.

**UserOptions** (addon-vitest) `[SRC:code/addons/vitest/src/vitest-plugin/index.ts:L12]`:
`{ configDir?: string, storybookScript?: string, storybookUrl?: string, tags?: { include?, exclude?, skip? }, disableAddonDocs?: boolean }` — configuration for the `storybookTest()` Vitest plugin.

## Architecture at a Glance

- **Core:** `storybook` — test, actions, highlight, viewport, theming, manager-api, preview-api, types, csf
- **Framework:** `@storybook/react-vite` — preset configuration, node-side config, Vite integration
- **Renderer:** `@storybook/react` — React types, portable stories, Playwright CT support
- **Builder:** `@storybook/builder-vite` — Vite dev server/build integration, plugin composition
- **Addons:** a11y (axe-core accessibility auditing), docs (MDX documentation blocks), themes (CSS class/data-attribute/JSX theme switching), vitest (story-based test runner)

`[SRC:code/core/package.json:L1]`

## CLI

```bash
npm create storybook@latest              # Initialize Storybook in a project
npm run storybook                        # Start dev server (default: port 6006)
npm run build-storybook                  # Production static build
npx storybook add @storybook/addon-vitest  # Add vitest addon
vitest --project=storybook               # Run story tests in CI
npx storybook doctor                     # Diagnose configuration issues
```

`[SRC:code/lib/cli/src/initiate.ts:L1]`

<!-- [MANUAL:additional-notes] -->
<!-- Add custom notes here. This section is preserved during skill updates. -->
<!-- [/MANUAL:additional-notes] -->

---


## References

Detailed API documentation is available in the `references/` directory:

- [Full API Reference](references/full-api-reference.md)
- [Full Type Definitions](references/full-type-definitions.md)
- [Full Integration Patterns](references/full-integration-patterns.md)
