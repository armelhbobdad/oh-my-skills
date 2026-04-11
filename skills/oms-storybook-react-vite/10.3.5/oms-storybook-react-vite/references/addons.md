# Essential Addons — a11y / themes / vitest / docs

The 4 addons in scope for this skill. Each addon is a separate npm package, registered in `.storybook/main.ts` `addons: []` and expose `parameters`/`decorators`/`globals` via a `./preview` subpath. All T1.

## Contents

- [Registration in `main.ts`](#registration-in-maints)
- [`@storybook/addon-a11y`](#storybookaddon-a11y)
- [`@storybook/addon-themes`](#storybookaddon-themes)
- [`@storybook/addon-vitest`](#storybookaddon-vitest)
- [`@storybook/addon-docs`](#storybookaddon-docs)

## Registration in `main.ts`

```ts
// .storybook/main.ts
import type { StorybookConfig } from '@storybook/react-vite';

const config: StorybookConfig = {
  framework: '@storybook/react-vite',
  stories: ['../src/**/*.stories.@(ts|tsx|mdx)'],
  addons: [
    '@storybook/addon-docs',
    '@storybook/addon-a11y',
    '@storybook/addon-themes',
    '@storybook/addon-vitest',
  ],
};

export default config;
```

`[AST:code/frameworks/react-vite/src/types.ts:L1]`

## `@storybook/addon-a11y`

Accessibility testing via axe-core. Runs checks in the browser during story render and reports results in the a11y panel. Optionally integrates with Vitest for test-mode enforcement.

**Package entries:**
- `@storybook/addon-a11y` — `src/index.ts`
- `@storybook/addon-a11y/preview` — `src/preview.tsx`

### Main entry exports

| Export | Kind | Purpose | Source |
|---|---|---|---|
| `PARAM_KEY` | const | String identifier for a11y parameters (used internally) | `[AST:code/addons/a11y/src/index.ts]` |
| `A11yGlobals` | type | Accessibility global configuration | `[AST:code/addons/a11y/src/index.ts]` |
| `A11yTypes` | type | Addon type definitions (parameters + globals) | `[AST:code/addons/a11y/src/index.ts]` |
| `A11yReport` | type | Enhanced Axe results or error object | `[AST:code/addons/a11y/src/index.ts]` |

### Preview entry exports

| Export | Kind | Value/Shape | Source |
|---|---|---|---|
| `decorators` | array | `[withVisionSimulator]` — vision simulator decorator | `[AST:code/addons/a11y/src/preview.tsx]` |
| `afterEach` | async function | Runs a11y tests via axe-core; integrates with the Vitest matcher | `[AST:code/addons/a11y/src/preview.tsx]` |
| `initialGlobals` | object | `{ a11y: { manual: false }, vision: undefined }` | `[AST:code/addons/a11y/src/preview.tsx]` |
| `parameters` | object | `{ a11y: { test: 'todo' } }` — default a11y parameters | `[AST:code/addons/a11y/src/preview.tsx]` |

### Story-level usage

```ts
// Button.stories.tsx
import type { Meta, StoryObj } from '@storybook/react-vite';
import { Button } from './Button';

const meta = {
  component: Button,
  parameters: {
    a11y: {
      test: 'error',  // 'off' | 'todo' | 'error'
      config: {
        rules: [
          { id: 'color-contrast', enabled: true },
        ],
      },
    },
  },
} satisfies Meta<typeof Button>;
```

**`test` values:**
- `'off'` — do not run a11y checks
- `'todo'` — run checks, show violations in panel, do NOT fail tests (default)
- `'error'` — run checks, fail any Vitest integration tests on violations

**Recent fix** (PR #34203, v10.3.4): status transition timer is now cleared on unmount, preventing test flake. `[QMD:oms-storybook-react-vite-temporal:changelog.md #5defd6]`

## `@storybook/addon-themes`

Theme switching decorators. Register once in `preview.ts` and toggle themes from the toolbar.

**Package entries:**
- `@storybook/addon-themes` — `src/index.ts`
- `@storybook/addon-themes/preview` — `src/preview.ts`

### Main entry exports

| Export | Kind | Signature | Source |
|---|---|---|---|
| `withThemeByClassName` | decorator factory | `<R>(config: { themes: Record<string, string>; defaultTheme: string; parentSelector?: string }) => Decorator<R>` — toggles CSS class on the parent element | `[AST:code/addons/themes/src/index.ts:L1]` |
| `withThemeByDataAttribute` | decorator factory | `<R>(config: { themes: Record<string, string>; defaultTheme: string; parentSelector?: string; attributeName?: string }) => Decorator<R>` — toggles `data-*` attribute (default `data-theme`) | `[AST:code/addons/themes/src/index.ts:L1]` |
| `withThemeFromJSXProvider` | decorator factory | `<R>(config: { Provider?: ComponentType; GlobalStyles?: ComponentType; defaultTheme?: string; themes?: Record<string, Theme> }) => Decorator<R>` — wraps story in a JSX provider (emotion / styled-components / MUI ThemeProvider) | `[AST:code/addons/themes/src/index.ts:L1]` |
| `ThemesGlobals` | type | `{ theme?: string }` | `[AST:code/addons/themes/src/index.ts]` |
| `ThemesTypes` | type | Addon type definitions (parameters + globals) | `[AST:code/addons/themes/src/index.ts]` |

### Usage

**Class-based themes (Tailwind dark mode, etc.):**
```ts
// .storybook/preview.ts
import type { Preview } from '@storybook/react-vite';
import { withThemeByClassName } from '@storybook/addon-themes';

const preview: Preview = {
  decorators: [
    withThemeByClassName({
      themes: { light: '', dark: 'dark' },
      defaultTheme: 'light',
    }),
  ],
};

export default preview;
```

**Data-attribute themes:**
```ts
withThemeByDataAttribute({
  themes: { light: 'light', dark: 'dark' },
  defaultTheme: 'light',
  attributeName: 'data-theme',
})
```

**JSX provider (emotion, styled-components, MUI):**
```tsx
import { ThemeProvider } from '@emotion/react';
import { lightTheme, darkTheme } from './themes';

withThemeFromJSXProvider({
  themes: { light: lightTheme, dark: darkTheme },
  defaultTheme: 'light',
  Provider: ThemeProvider,
  GlobalStyles,
})
```

## `@storybook/addon-vitest`

Integrates Storybook stories with Vitest as portable test subjects. Provides the test provider, test UI in the Storybook panel, and glue code for `composeStories` to run under Vitest.

**Package entries:**
- `@storybook/addon-vitest` — `src/index.ts`
- `@storybook/addon-vitest/constants` — `src/constants.ts`
- `@storybook/addon-vitest/vitest-plugin` — Vitest plugin entry

### Main entry

```ts
// code/addons/vitest/src/index.ts — minimal
export default definePreviewAddon({});
```

The main entry is deliberately thin — test execution happens in the vitest-plugin path.

### Constants entry exports

| Export | Kind | Value | Source |
|---|---|---|---|
| `ADDON_ID` | const | `'storybook/test'` | `[AST:code/addons/vitest/src/constants.ts]` |
| `TEST_PROVIDER_ID` | const | `'storybook/test/test-provider'` | `[AST:code/addons/vitest/src/constants.ts]` |
| `STORYBOOK_ADDON_TEST_CHANNEL` | const | `'storybook/test/channel'` | `[AST:code/addons/vitest/src/constants.ts]` |
| `COMPONENT_TESTING_PANEL_ID` | const | (re-exported from core) | `[AST:code/addons/vitest/src/constants.ts]` |
| `A11Y_PANEL_ID`, `A11Y_ADDON_ID` | const | (re-exported from addon-a11y) | `[AST:code/addons/vitest/src/constants.ts]` |
| `storeOptions` | object | Store config: `{ initialState: { coverage, a11y, watching, componentTestStatuses, ... } }` | `[AST:code/addons/vitest/src/constants.ts]` |
| `FULL_RUN_TRIGGERS` | type | `('global' \| 'run-all')[]` | `[AST:code/addons/vitest/src/constants.ts]` |
| `TriggerTestRunRequestPayload` | type | `{ requestId, actor, storyIds?, config? }` | `[AST:code/addons/vitest/src/constants.ts]` |
| `TestRunResult` | type | `CurrentRun` | `[AST:code/addons/vitest/src/constants.ts]` |
| `TriggerTestRunResponsePayload` | type | `{ requestId, status, result?, error? }` | `[AST:code/addons/vitest/src/constants.ts]` |

### Vitest setup wiring

```ts
// vitest.config.ts
import { defineConfig } from 'vitest/config';
import { storybookTest } from '@storybook/addon-vitest/vitest-plugin';

export default defineConfig({
  plugins: [storybookTest({ configDir: './.storybook' })],
  test: {
    browser: { enabled: true, provider: 'playwright', instances: [{ browser: 'chromium' }] },
  },
});
```

```ts
// .storybook/vitest.setup.ts
import { setProjectAnnotations } from '@storybook/react';
import * as previewAnnotations from './preview';

setProjectAnnotations([previewAnnotations]);
```

`[AST:code/addons/vitest/src/vitest-plugin/setup-file.ts]`

## `@storybook/addon-docs`

Powers Autodocs and MDX. Registered once in `main.ts`; story files gain automatic docs when tagged with `tags: ['autodocs']`, and `*.mdx` files can reference stories via the blocks API.

**Package entries:**
- `@storybook/addon-docs` — `src/index.ts`
- `@storybook/addon-docs/blocks` — `src/blocks.ts` — **see `doc-blocks.md`**
- `@storybook/addon-docs/preview` — internal
- `@storybook/addon-docs/angular` / `/ember` / `/html` / `/vue3` / `/web-components` — per-renderer subpaths (NOT used with React+Vite)

### Main entry exports

| Export | Kind | Purpose | Source |
|---|---|---|---|
| `DocsRenderer` | component | Main renderer for docs pages | `[AST:code/addons/docs/src/index.ts:L1]` |
| `DocsTypes` | type | Addon type definitions | `[AST:code/addons/docs/src/index.ts:L1]` |

### `parameters.docs` (story-level config)

```ts
const meta = {
  parameters: {
    docs: {
      description: { component: 'Button docs' },
      source: { language: 'tsx', excludeDecorators: true },
      toc: true, // enable auto-TOC
      story: { inline: true, iframeHeight: 400 },
      canvas: { sourceState: 'shown' },
    },
  },
} satisfies Meta<typeof Button>;
```

Full MDX block API lives in `doc-blocks.md`.
