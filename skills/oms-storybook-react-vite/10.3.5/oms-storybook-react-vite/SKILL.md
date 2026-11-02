---
name: oms-storybook-react-vite
description: >
  Authors Storybook v10 stories using the consolidated `storybook` package
  import surface for React plus Vite. Use when writing or editing
  `*.stories.tsx`, `preview.ts`, or `.storybook/main.ts` files on a Storybook
  10.3+ project, including CSF3 story syntax, `play` functions with
  `storybook/test`, `preview-api` hooks, theming, MDX doc blocks from
  `@storybook/addon-docs/blocks`, and the a11y, themes, and vitest addons.
  Covers the `@storybook/react-vite` framework, `@storybook/react` renderer,
  and `@storybook/builder-vite` layer model so defects can be located at the
  right layer. Do NOT use for first-time project setup, framework selection,
  or upgrade migration (those flows are covered by the official upgrade CLI).
  Do NOT generate CSF2 default-export story arrays — v10 uses CSF3 named
  exports with the `satisfies` meta pattern, and training data frequently
  shows the wrong `@storybook/*` sub-package import paths that v10
  consolidated into the single `storybook` package.
---

## Overview

Storybook v10 **consolidates** what used to be ~40 separate `@storybook/*` packages into a single published `storybook` package exposing 40 subpath exports (including `./internal/*`). This skill grounds Claude in that consolidated import surface so it stops generating outdated `@storybook/addon-actions`, `@storybook/test`, `@storybook/preview-api` imports that training data still shows.

- **Scope:** day-90+ story author on a Storybook 10.3+ React+Vite project. Not a setup/install guide — `.storybook/main.ts` framework pick and addon registration are edited quarterly and covered by the official upgrade CLI.
- **Packages covered:** `storybook` (core, 40 subpaths), `@storybook/react-vite` (framework), `@storybook/react` (renderer), `@storybook/builder-vite` (builder), `@storybook/addon-{a11y,docs,themes,vitest}`.
- **Layer model:** `@storybook/react-vite` (framework) composes `@storybook/react` (renderer) + `@storybook/builder-vite` (builder). Defects go in the correct layer.
- **Source:** `github.com/storybookjs/storybook` @ tag `v10.3.5` (commit `e486d382`). `[AST:code/frameworks/react-vite/src/preset.ts:L1]` `[AST:code/core/package.json:L48]`

## Quick Start

**Preflight — ALWAYS do this first.** Before writing any Storybook code, read the user's project state to ground your answer:

```bash
cat .storybook/main.ts   # installed version, registered addons, framework in use
cat .storybook/preview.ts # parameters, decorators, globalTypes already set
cat package.json | grep -E '"storybook"|"@storybook/'  # resolved versions
```

If the user's `storybook` dep is `<10.0.0`, STOP and tell them — CSF3 + v10 imports below will not apply. `[EXT:https://storybook.js.org/docs/get-started/frameworks/react-vite/]`

**Write a CSF3 story** (the canonical v10 pattern):

```tsx
// Button.stories.tsx
import type { Meta, StoryObj } from '@storybook/react-vite';
import { fn, expect } from 'storybook/test';
import { Button } from './Button';

const meta = {
  component: Button,
  args: { onClick: fn() },
  tags: ['autodocs'],
} satisfies Meta<typeof Button>;

export default meta;
type Story = StoryObj<typeof meta>;

export const Primary: Story = {
  args: { label: 'Click me', variant: 'primary' },
};

export const Clicked: Story = {
  args: { label: 'Click me' },
  play: async ({ canvas, userEvent, args }) => {
    const button = canvas.getByRole('button', { name: /click me/i });
    await userEvent.click(button);
    await expect(args.onClick).toHaveBeenCalled();
  },
};
```

**Write a `preview.ts`** — the authoring surface for parameters, decorators, globalTypes, loaders:

```ts
// .storybook/preview.ts
import type { Preview } from '@storybook/react-vite';
import { withThemeByClassName } from '@storybook/addon-themes';

const preview: Preview = {
  parameters: {
    controls: { matchers: { color: /(background|color)$/i } },
    a11y: { test: 'todo' }, // 'off' | 'todo' | 'error'
  },
  decorators: [
    withThemeByClassName({
      themes: { light: '', dark: 'dark' },
      defaultTheme: 'light',
    }),
  ],
  tags: ['autodocs'],
};

export default preview;
```

Sources for the two templates above: `[AST:code/renderers/react/src/public-types.ts:L29]` (CSF types) `[AST:code/renderers/react/src/public-types.ts:L80]` (`Preview`) `[AST:code/core/src/test/index.ts:L139]` (`storybook/test`) `[AST:code/addons/themes/src/index.ts:L1]` (`withThemeByClassName`) `[AST:code/addons/a11y/src/preview.tsx:L1]` (a11y `parameters`) `[AST:code/renderers/react/template/stories/test-fn.stories.tsx:L1]` (sample).

<!-- [MANUAL:additional-notes-quickstart] -->
<!-- Add custom notes here. This section is preserved during skill updates. -->
<!-- [/MANUAL:additional-notes-quickstart] -->

## Common Workflows

**Author a story with a mock action:**
`import { fn } from 'storybook/test'` → `args: { onClick: fn() }` → assert in `play` with `expect(args.onClick).toHaveBeenCalled()` `[AST:code/core/src/test/index.ts:L139]`

**Write a `play` function (interaction test):**
`play: async ({ canvas, userEvent, args }) => { ... }` — destructure from `storybook/test` context. Use `canvas.getByRole` / `findByRole`, `await userEvent.click(...)`, `await expect(...)`. `[AST:code/renderers/react/template/stories/test-fn.stories.tsx:L1]`

**Add a theme decorator globally:**
`decorators: [withThemeByClassName({ themes, defaultTheme })]` in `preview.ts` — or `withThemeByDataAttribute` / `withThemeFromJSXProvider` for CSS-in-JS providers. `[AST:code/addons/themes/src/index.ts:L1]`

**Use preview-api hooks inside a decorator or render:**
`import { useState, useArgs, useParameter } from 'storybook/preview-api'` → `const [{ label }, updateArgs] = useArgs()` reads/writes current story args. `[AST:code/core/src/preview-api/index.ts:L5]`

**Use a component portably in Vitest:**
`import { composeStories } from 'storybook/preview-api'` (or `'@storybook/react'`) → `const { Primary } = composeStories(stories)` → `render(<Primary />)`. Requires `addon-vitest` + `setProjectAnnotations(projectAnnotations)` once in test setup. `[AST:code/core/src/preview-api/index.ts:L51]` `[QMD:oms-storybook-react-vite-temporal:changelog.md #28907]`

**Author an MDX docs page:**
`import { Meta, Canvas, Controls, Primary, Stories } from '@storybook/addon-docs/blocks'` → `<Meta of={ButtonStories} />` → `<Primary />` / `<Canvas of={ButtonStories.Secondary} />` / `<Controls />` / `<Stories />`. `[AST:code/addons/docs/src/blocks.ts:L1]`

**Verify a story after writing it:**
`npm run storybook` → open `http://localhost:6006` → confirm the story renders in the canvas with no console errors → if it has a `play` function, check the Interactions panel shows each step passing. For CI verification use `npm run test-storybook` (requires `addon-vitest` configured in `main.ts`). `[EXT:https://storybook.js.org/docs/writing-tests/test-runner]`

## v10 Import Corrections (the training-data drift this skill fixes)

Three rewrites carry almost all the value this skill provides. If a generated import uses the left column, rewrite it to the right column:

| Old (v9 / training data) | New (v10 canonical) | Why |
|---|---|---|
| `@storybook/test` | `storybook/test` | v10 consolidation — no scope prefix, no `-` separator. `[QMD:oms-storybook-react-vite-temporal:issues.md #9b8716]` |
| `@storybook/preview-api` | `storybook/preview-api` | Same consolidation. Hooks (`useArgs`, `useState`, …) all live here now. |
| `@storybook/theming` / `@storybook/actions` / `@storybook/manager-api` | `storybook/theming` / `storybook/actions` / `storybook/manager-api` | Same pattern — all core subpaths drop the `@` prefix. |

The full import surface (CSF types, test utilities, preview-api hooks, addon exports, MDX blocks) lives in `references/core-api.md` — the complete v10 consolidated import table is the first section of that file. See also `references/story-types.md`, `references/doc-blocks.md`, `references/addons.md`, `references/framework-config.md`.

<!-- [MANUAL:additional-notes-api] -->
<!-- Add custom notes here. This section is preserved during skill updates. -->
<!-- [/MANUAL:additional-notes-api] -->

## Shipped v10.3.x fixes worth knowing

> **Scope:** historical migration + recent shipped fixes. No forward-looking deprecations are announced for v10.3.5 — nothing scheduled to break in v11 yet at the time of extraction. The v10 consolidation itself is covered by the import-corrections table above.

- **`setProjectAnnotations` expanded** (PR #28907): available across more renderers/frameworks for portable stories. Always call it once in your Vitest/Jest setup — otherwise `composeStories` will miss project-level decorators and parameters. `[QMD:oms-storybook-react-vite-temporal:changelog.md #5defd6]`
- **Component manifest default changed in 10.3.5** (PR #34408): `docs.componentManifest` is now disabled by default. If your project uses `@storybook/addon-mcp < 0.5.0`, upgrade it — the MCP docs toolset re-enables manifests. `[QMD:oms-storybook-react-vite-temporal:changelog.md #5defd6]`
- **`addon-a11y` test flake fix** (PR #34203, v10.3.4): status transition timer is now cleared on unmount. If you saw intermittent a11y test failures on older 10.3.x, upgrading resolves them. `[QMD:oms-storybook-react-vite-temporal:changelog.md #5defd6]`

## Key Types (quick-start essentials)

The three types every CSF3 story file needs — just enough for the Quick Start above. `Decorator`, `Loader`, `StoryContext`, `A11yTestMode`, `Framework`, and the full generic shapes live in `references/story-types.md`.

```ts
// @storybook/react-vite re-exports these from @storybook/react
type Meta<TCmpOrArgs = Args>;      // component metadata — use with `satisfies Meta<typeof X>`
type StoryObj<TMeta>;              // CSF3 story — `export const X: Story = { args: {...} }`
type Preview = ProjectAnnotations<ReactRenderer>;  // shape of .storybook/preview.ts default export
```

`[AST:code/renderers/react/src/public-types.ts:L29]` `[AST:code/renderers/react/src/public-types.ts:L80]`

## Architecture at a Glance

Layer model: `@storybook/react-vite` (framework) composes `@storybook/react` (renderer) + `@storybook/builder-vite` (builder). Defect localization: story render failures → renderer; Vite HMR/build failures → builder; `main.ts` framework pick or addon auto-detect → framework; `play` function assertions → `storybook/test`; addon panel missing → the specific addon package. Full layer composition, `main.ts` contract, and `preview.ts` authoring surface live in `references/framework-config.md`. `[AST:code/frameworks/react-vite/src/index.ts:L1]` `[AST:code/renderers/react/src/public-types.ts:L1]` `[AST:code/builders/builder-vite/src/index.ts:L1]`

## CLI

Most Storybook interaction is through the project's own scripts (`npm run storybook`, `npm run build-storybook`). The skill does not add value for first-time setup — those flows are covered by the official CLI. Relevant commands:

```bash
npm run storybook           # dev server (via @storybook/builder-vite)
npm run build-storybook     # static build → storybook-static/
npx storybook@latest upgrade  # version bump + automigrations
```

`[EXT:https://storybook.js.org/docs/get-started/frameworks/react-vite/]`

<!-- [MANUAL:additional-notes-cli] -->
<!-- Add custom notes here. This section is preserved during skill updates. -->
<!-- [/MANUAL:additional-notes-cli] -->

## Full API Reference

The complete public API surface — ~430 extracted exports across core (`storybook` 28 subpaths ≈ 350 exports), framework/renderer/builder (~42 exports), and 4 addons (~65 exports) — lives in `references/core-api.md`, `references/story-types.md`, `references/doc-blocks.md`, and `references/addons.md`. Each entry carries `[AST:...]` provenance and indicates whether it is authoring surface (tier A), type surface (tier B), or infrastructure (tier C). T1 source: `[AST:code/core/src/test/index.ts:L1]` `[AST:code/core/src/preview-api/index.ts:L1]` `[AST:code/core/src/manager-api/index.ts:L1]` `[AST:code/core/src/theming/index.ts:L1]` `[AST:code/renderers/react/src/public-types.ts:L1]` `[AST:code/addons/docs/src/blocks.ts:L1]`.

## Full Type Definitions

Full generic signatures for `Meta<T>`, `StoryObj<T>`, `StoryFn<T>`, `Decorator<T>`, `Loader<T>`, `StoryContext<T>`, `Preview`, `StorybookConfig`, and the internal `ComponentAnnotations` / `StoryAnnotations` / `ProjectAnnotations` shapes (with field-level documentation on `args`, `argTypes`, `parameters`, `play`, `render`, `decorators`, `loaders`, `beforeAll`, `tags`) live in `references/story-types.md`. All T1 from `code/renderers/react/src/public-types.ts` and `code/core/src/types/index.ts`.

## Full Integration Patterns

Verbatim CSF3 and CSF4 sample stories from `code/renderers/react/template/stories/`, the full framework/renderer/builder layer composition detail, the `main.ts` / `preview.ts` config contract, addon registration patterns, and portable-stories integration (`composeStories` + `setProjectAnnotations`) with Vitest/Jest live in `references/framework-config.md` and `references/csf3-patterns.md`. T1 sources cited throughout.

<!-- [MANUAL:additional-notes-reference] -->
<!-- Add custom notes here. This section is preserved during skill updates. -->
<!-- [/MANUAL:additional-notes-reference] -->
