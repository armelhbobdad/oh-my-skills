---
name: oms-storybook-react-vite
description: >
  Grounds Claude in Storybook v10's consolidated `storybook` package import
  surface for React plus Vite story authoring. Use when writing or editing
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

## Key API Summary

Imports are grouped by source package. Column 3 is the subpath to import from — **this is the load-bearing part** the skill corrects against training data.

| Import | Kind | From (v10 consolidated) |
|---|---|---|
| `Meta`, `StoryObj`, `StoryFn`, `Decorator`, `Parameters`, `ArgTypes`, `Args`, `StoryContext`, `Loader`, `Preview` | type | `@storybook/react-vite` *(or `@storybook/react`)* `[AST:code/renderers/react/src/public-types.ts:L29]` |
| `StorybookConfig`, `FrameworkOptions` | type | `@storybook/react-vite` `[AST:code/frameworks/react-vite/src/types.ts:L1]` |
| `expect`, `fn`, `within`, `screen`, `waitFor`, `userEvent`, `fireEvent`, `spyOn` | runtime | `storybook/test` `[AST:code/core/src/test/index.ts:L54]` |
| `useState`, `useArgs`, `useParameter`, `useChannel`, `useEffect`, `useGlobals`, `useCallback`, `useMemo`, `useRef`, `useReducer`, `useStoryContext` | hook | `storybook/preview-api` `[AST:code/core/src/preview-api/index.ts:L5]` |
| `addons`, `makeDecorator`, `mockChannel` | runtime | `storybook/preview-api` `[AST:code/core/src/preview-api/index.ts:L21]` |
| `composeStories`, `composeStory`, `setProjectAnnotations` | runtime | **`@storybook/react-vite`** *(canonical for React+Vite — re-exported from `@storybook/react` where they're defined)* `[AST:code/renderers/react/src/portable-stories.tsx:L46]` |
| `__definePreview` *(CSF4 factory — the double-underscore form is the canonical public export name in `@storybook/react-vite` / `@storybook/react`; `definePreview` is a user-facing alias in the docs but the symbol emitted from the framework package is `__definePreview`)* | runtime | `@storybook/react-vite` `[AST:code/renderers/react/src/preview.tsx:L55]` |
| `action` | runtime | `storybook/actions` `[AST:code/core/src/actions/index.ts:L1]` |
| `create`, `themes`, `styled`, `css`, `useTheme`, `ThemeProvider` | runtime | `storybook/theming` / `storybook/theming/create` `[AST:code/core/src/theming/create.ts:L29]` |
| `HIGHLIGHT`, `RESET_HIGHLIGHT` | const | `storybook/highlight` `[AST:code/core/src/highlight/index.ts:L1]` |
| `Canvas`, `Meta`, `Controls`, `Primary`, `Stories`, `Story`, `ArgTypes`, `Source`, `Description`, `Title`, `Markdown`, `Typeset`, `ColorPalette`, `IconGallery`, `Unstyled`, `useOf`, `DocsContainer`, `DocsPage` | MDX block | `@storybook/addon-docs/blocks` `[AST:code/addons/docs/src/blocks.ts:L1]` |
| `withThemeByClassName`, `withThemeByDataAttribute`, `withThemeFromJSXProvider` | decorator | `@storybook/addon-themes` `[AST:code/addons/themes/src/index.ts:L1]` |
| a11y `parameters: { a11y: { test: ... } }`, runtime `afterEach`, `decorators`, `initialGlobals` | param + runtime | `@storybook/addon-a11y` / `@storybook/addon-a11y/preview` — the runtime `afterEach(context)` at `[AST:code/addons/a11y/src/preview.tsx:L14]` runs axe-core per story and attaches an `A11yReport` to `context.reporting`; compose it manually in your `preview.ts` only when you need multiple `afterEach` hooks | `[AST:code/addons/a11y/src/preview.tsx:L14]` |

Full signatures, parameter tables, and return types live in `references/core-api.md` (storybook/* subpaths), `references/story-types.md` (CSF types), `references/doc-blocks.md` (MDX blocks), and `references/addons.md`.

<!-- [MANUAL:additional-notes-api] -->
<!-- Add custom notes here. This section is preserved during skill updates. -->
<!-- [/MANUAL:additional-notes-api] -->

## Import Surface Corrections & Recent Changes

> **Section scope:** this section is not a Storybook changelog — it captures the *v10 consolidation* that persists as a training-data defect plus a handful of load-bearing recent fixes. There are **no forward-looking deprecations** announced for v10.3.5 (nothing scheduled to break in v11 yet at the time of extraction).

**v10 consolidation (the big one — this is the skill's core value prop):** The package `@storybook/test` is deprecated. Import from `storybook/test` instead (no `@` prefix, no `-` separator). The same applies to `@storybook/preview-api` → `storybook/preview-api`, `@storybook/manager-api` → `storybook/manager-api`, `@storybook/theming` → `storybook/theming`, `@storybook/actions` → `storybook/actions`. Training data and `eslint-plugin-storybook` older versions still suggest the `@storybook/*` forms — override them. `[QMD:oms-storybook-react-vite-temporal:issues.md #9b8716]` `[AST:code/core/package.json:L48]`

**`setProjectAnnotations` expanded** (PR #28907): available across more renderers/frameworks for portable stories. Always call it once in your Vitest/Jest setup — otherwise `composeStories` will miss project-level decorators and parameters. `[QMD:oms-storybook-react-vite-temporal:changelog.md #5defd6]`

**Component manifest default changed in 10.3.5** (PR #34408): `docs.componentManifest` is now disabled by default. If your project uses `@storybook/addon-mcp < 0.5.0`, upgrade it — the MCP docs toolset re-enables manifests. `[QMD:oms-storybook-react-vite-temporal:changelog.md #5defd6]`

**`addon-a11y` test flake fix** (PR #34203, v10.3.4): status transition timer is now cleared on unmount. If you saw intermittent a11y test failures on older 10.3.x, upgrading resolves them. `[QMD:oms-storybook-react-vite-temporal:changelog.md #5defd6]`

See Full API Reference and `references/framework-config.md` for migration details and the full v10 import mapping.

## Key Types

```ts
// @storybook/react-vite re-exports these from @storybook/react
// (BOTH import paths work; prefer @storybook/react-vite for framework alignment)

type Preview = ProjectAnnotations<ReactRenderer>;
// Shape of .storybook/preview.ts default export.
// ⚠️ Not the same as the runtime `Preview` CLASS exported from
// `storybook/preview-api` (aliased to `PreviewWeb`, the browser runtime at
// code/core/src/preview-api/modules/preview-web/Preview.tsx:L60). The class
// is an internal runtime; story authors only ever use the type.

type Meta<TCmpOrArgs = Args> = [TCmpOrArgs] extends [ComponentType<any>]
  ? ComponentAnnotations<ReactRenderer, ComponentProps<TCmpOrArgs>>
  : ComponentAnnotations<ReactRenderer, TCmpOrArgs>;
// Component metadata — pass a component and args are inferred from props

type StoryObj<TMetaOrCmpOrArgs = Args> = /* CSF3 story; see references/story-types.md */;
// CSF3 story object — use `satisfies Meta<typeof X>` on meta, then `StoryObj<typeof meta>` on stories

type Decorator<TArgs = StrictArgs> = DecoratorFunction<ReactRenderer, TArgs>;
type Loader<TArgs = StrictArgs> = LoaderFunction<ReactRenderer, TArgs>;
type StoryContext<TArgs = StrictArgs> = GenericStoryContext<ReactRenderer, TArgs>;

// Addon-a11y test mode (set in parameters.a11y.test)
type A11yTestMode = 'off' | 'todo' | 'error';

// .storybook/main.ts framework field — string OR object-with-options
type Framework = '@storybook/react-vite' | { name: '@storybook/react-vite'; options: FrameworkOptions };
```

`[AST:code/renderers/react/src/public-types.ts:L29]` `[AST:code/renderers/react/src/public-types.ts:L80]` `[AST:code/frameworks/react-vite/src/types.ts:L1]`

Full type definitions with inline generics, `StoryAnnotations` / `ComponentAnnotations` internal shapes, and all addon parameter types live in `references/story-types.md`.

## Architecture at a Glance

- **`storybook` core package** — 40 subpath exports. Authoring-surface tier A: `test`, `preview-api`, `manager-api`, `theming`, `theming/create`, `actions`, `actions/decorator`, `highlight`, `viewport`. Type tier B: `internal/types`, `internal/csf`, `internal/preview-errors`, `internal/server-errors`, `internal/components`. `internal/*` is not private — it is declared in the package's `exports` field.
- **`@storybook/react-vite` (framework)** — Thin layer that re-exports all CSF types from `@storybook/react`, adds `StorybookConfig`, and wires the Vite builder. Imports in stories should target this package for framework-aligned type inference.
- **`@storybook/react` (renderer)** — Defines `Meta`, `StoryObj`, `StoryFn`, `Decorator`, `Loader`, `StoryContext`, `Preview` in `public-types.ts`. Houses `composeStory`/`composeStories` (portable stories) and CSF4 factory API (`__definePreview`, `ReactPreview`, `ReactMeta`, `ReactStory`).
- **`@storybook/builder-vite` (builder)** — Vite dev/build backend. Exports `start`, `build`, `ViteBuilder`, `ViteFinal`, `StorybookConfigVite`. Users rarely import from it directly — `react-vite` drives it via `viteFinal` in `main.ts`.
- **Addons (4 essentials in scope)** — `@storybook/addon-a11y`, `@storybook/addon-docs`, `@storybook/addon-themes`, `@storybook/addon-vitest`. Registered in `main.ts` `addons: []`; expose `parameters`/`decorators` via `./preview` subpath entries.
- **Template stories** — `code/renderers/react/template/stories/*.stories.tsx` — the repo's own canonical CSF3/CSF4 exemplars. When in doubt, `references/csf3-patterns.md` has verbatim extracts.

Sources: `[AST:code/core/package.json:L48]` `[AST:code/frameworks/react-vite/src/index.ts:L1]` `[AST:code/renderers/react/src/public-types.ts:L1]` `[AST:code/builders/builder-vite/src/index.ts:L1]` `[AST:code/addons/a11y/src/preview.tsx:L1]` `[AST:code/renderers/react/template/stories/decorators.stories.tsx:L1]`.

**Defect localization by layer:** a failing story render → renderer (`@storybook/react`); a failing Vite dev server / HMR → builder (`@storybook/builder-vite`); a failing `main.ts` framework pick → framework (`@storybook/react-vite`); a failing `play` function assertion → `storybook/test`; a failing addon panel → the specific addon package.

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
