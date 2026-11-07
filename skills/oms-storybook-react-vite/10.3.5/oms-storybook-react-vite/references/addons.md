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

`[AST:code/frameworks/react-vite/src/types.ts:L66]`

## `@storybook/addon-a11y`

Accessibility testing via axe-core. Runs checks in the browser during story render and reports results in the a11y panel. Optionally integrates with Vitest for test-mode enforcement.

**Package entries:**
- `@storybook/addon-a11y` — `src/index.ts`
- `@storybook/addon-a11y/preview` — `src/preview.tsx`

### Main entry exports

| Export | Kind | Purpose | Source |
|---|---|---|---|
| `PARAM_KEY` | const | `'a11y'`, the key of the a11y parameters (used internally); not the actions or viewport `PARAM_KEY` | `[AST:code/addons/a11y/src/index.ts:L6]` `[AST:code/addons/a11y/src/constants.ts:L3]` |
| `A11yParameters` | interface | `{ context?: ContextSpecWithoutNode; options?: RunOptions; config?: Spec; disable?: boolean; test?: A11yTest }` — per-story a11y config | `[AST:code/addons/a11y/src/params.ts:L20]` |
| `A11yGlobals` | interface | `{ a11y?: { manual?: boolean } }` — global a11y settings (manual vs auto run) | `[AST:code/addons/a11y/src/types.ts:L16]` |
| `A11yTypes` | interface | `{ parameters: A11yParameters; globals: A11yGlobals }` — addon type bundle. Its `parameters` type is not the `A11yParameters` row above but the wrapper of the same name at `types.ts:L7`, which the package root does not re-export (its `index.ts:L8` re-exports only `A11yGlobals`, `A11yTypes` and `A11yReport` from `types.ts`), whose one field `a11y?` holds that interface | `[AST:code/addons/a11y/src/types.ts:L55]` |
| `A11yReport` | type | `EnhancedResults \| { error: Error }` — axe run result or error wrapper | `[AST:code/addons/a11y/src/types.ts:L5]` |
| `SelectorWithoutNode` | type | `Omit<Selector, 'Node'> \| Omit<SelectorList, 'NodeList'>` — axe selector minus DOM-Node refs (safe to serialize in parameters) | `[AST:code/addons/a11y/src/params.ts:L3]` |
| `ContextObjectWithoutNode` | type | `{ include: SelectorWithoutNode; exclude?: SelectorWithoutNode } \| { exclude: SelectorWithoutNode; include?: SelectorWithoutNode }` | `[AST:code/addons/a11y/src/params.ts:L6]` |
| `ContextSpecWithoutNode` | type | `SelectorWithoutNode \| ContextObjectWithoutNode` — shape of `parameters.a11y.context` | `[AST:code/addons/a11y/src/params.ts:L16]` |

### Preview entry exports

Runtime subpath: `@storybook/addon-a11y/preview`. These are imported as `import { afterEach } from '@storybook/addon-a11y/preview'` in a user's `.storybook/preview.ts` only when composing multiple preview hooks manually.

| Export | Kind | Value/Shape | Source |
|---|---|---|---|
| `decorators` | const | `[withVisionSimulator]` (unannotated, so an array, `(typeof withVisionSimulator)[]`, not a tuple) — auto-applied vision-simulation decorator | `[AST:code/addons/a11y/src/preview.tsx:L12]` |
| `afterEach` | function | `AfterEach<any>` — async hook `({ id, reporting, parameters, globals, viewMode }) => Awaitable<void>` (the return `AfterEach` declares, `Awaitable<T> = T \| PromiseLike<T>`) that runs axe-core per story and attaches an `A11yReport` to `reporting` | `[AST:code/addons/a11y/src/preview.tsx:L14]` `[SRC:code/core/src/csf/story.ts:L262]` `[SRC:code/core/src/csf/story.ts:L253]` |
| `initialGlobals` | const | `{ a11y: { manual: false }; vision: undefined }` | `[AST:code/addons/a11y/src/preview.tsx:L98]` |
| `parameters` | const | `{ a11y: A11yParameters }` — default a11y parameters (`test: 'todo'`, etc.) | `[AST:code/addons/a11y/src/preview.tsx:L105]` |

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

**`test` values** (`A11yParameters['test']`, typed by `type A11yTest = 'off' | 'todo' | 'error'`, which `params.ts` declares without exporting it, so there is no importable test-mode type) `[SRC:code/addons/a11y/src/params.ts:L18]`:
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
| `withThemeByClassName` | function | `<TRenderer extends Renderer = Renderer>({ themes, defaultTheme, parentSelector = DEFAULT_ELEMENT_SELECTOR }: ClassNameStrategyConfiguration) => DecoratorFunction<TRenderer>` — toggles the selected theme's CSS class on the parent element (`parentSelector` defaults to the module-local `DEFAULT_ELEMENT_SELECTOR`, `'html'`) | `[AST:code/addons/themes/src/decorators/class-name.decorator.tsx:L19]` |
| `ClassNameStrategyConfiguration` | interface | `{ themes: Record<string, string>; defaultTheme: string; parentSelector?: string }` — strategy config for `withThemeByClassName` | `[AST:code/addons/themes/src/decorators/class-name.decorator.tsx:L8]` |
| `withThemeByDataAttribute` | function | `<TRenderer extends Renderer = any>({ themes, defaultTheme, parentSelector = DEFAULT_ELEMENT_SELECTOR, attributeName = DEFAULT_DATA_ATTRIBUTE }: DataAttributeStrategyConfiguration) => DecoratorFunction<TRenderer>` — sets a `data-*` attribute on the parent element to the selected theme (`parentSelector` defaults to the module-local `DEFAULT_ELEMENT_SELECTOR`, `'html'`, and `attributeName` to `DEFAULT_DATA_ATTRIBUTE`, `'data-theme'`) | `[AST:code/addons/themes/src/decorators/data-attribute.decorator.tsx:L19]` |
| `DataAttributeStrategyConfiguration` | interface | `{ themes: Record<string, string>; defaultTheme: string; parentSelector?: string; attributeName?: string }` | `[AST:code/addons/themes/src/decorators/data-attribute.decorator.tsx:L8]` |
| `withThemeFromJSXProvider` | function | `<TRenderer extends Renderer = any>({ Provider, GlobalStyles, defaultTheme, themes = {} }: ProviderStrategyConfiguration) => DecoratorFunction<TRenderer>` — when `Provider` is given, wraps the story in it (emotion / styled-components / MUI `ThemeProvider`) with the selected theme as its `theme`, and renders `GlobalStyles` before the story when given | `[AST:code/addons/themes/src/decorators/provider.decorator.tsx:L23]` |
| `ProviderStrategyConfiguration` | interface | `{ Provider?: any; GlobalStyles?: any; defaultTheme?: string; themes?: ThemeMap }` | `[AST:code/addons/themes/src/decorators/provider.decorator.tsx:L13]` |
| `ThemeAddonState` | interface | `{ themesList: string[]; themeDefault?: string }` — registered theme state. Declared in `types.ts` but not re-exported: `@storybook/addon-themes` exports only the `ThemesGlobals` and `ThemesTypes` types (`index.ts:L6`) | `[AST:code/addons/themes/src/types.ts:L1]` |
| `ThemesParameters` | interface | `{ themes?: { disable?: boolean; themeOverride?: string } }` — per-story theme override. Declared in `types.ts` but not re-exported; reach it as `ThemesTypes['parameters']` | `[AST:code/addons/themes/src/types.ts:L6]` |
| `ThemesGlobals` | interface | `{ theme?: string }` — global toolbar selection | `[AST:code/addons/themes/src/types.ts:L20]` |
| `ThemesTypes` | interface | `{ parameters: ThemesParameters; globals: ThemesGlobals }` — bundle | `[AST:code/addons/themes/src/types.ts:L25]` |

### Decorator helpers (namespace export)

Exposed as the `DecoratorHelpers` namespace export from `@storybook/addon-themes` (`decorators/index.ts:L5`) — useful when authoring a custom theme decorator that needs to read the active theme or register themes with the toolbar.

| Helper | Kind | Signature | Source |
|---|---|---|---|
| `pluckThemeFromContext` | function | `({ globals }: StoryContext) => string` — extract current theme key from globals | `[AST:code/addons/themes/src/decorators/helpers.ts:L16]` |
| `useThemeParameters` | function | `(context?: StoryContext) => ThemesParameters['themes']` — returns the inner `{ disable?: boolean; themeOverride?: string } \| undefined` (the helper's local alias `ThemesParameters = Parameters['themes']`, `helpers.ts:L10`), not the `ThemesParameters` interface declared at `types.ts:L6` (deprecated — prefer `context.parameters.themes` directly) | `[AST:code/addons/themes/src/decorators/helpers.ts:L20]` |
| `initializeThemeState` | function | `(themeNames: string[], defaultTheme: string) => void` — register the themes list with the toolbar channel | `[AST:code/addons/themes/src/decorators/helpers.ts:L34]` |

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
| `ADDON_ID` | const | `'storybook/test'` | `[AST:code/addons/vitest/src/constants.ts:L11]` |
| `TEST_PROVIDER_ID` | const | `'storybook/test/test-provider'` | `[AST:code/addons/vitest/src/constants.ts:L12]` |
| `STORYBOOK_ADDON_TEST_CHANNEL` | const | `'storybook/test/channel'` | `[AST:code/addons/vitest/src/constants.ts:L13]` |
| `COMPONENT_TESTING_PANEL_ID` | const | (core's component-testing `PANEL_ID`, re-exported under this name) | `[AST:code/addons/vitest/src/constants.ts:L5]` |
| `A11Y_PANEL_ID`, `A11Y_ADDON_ID` | const | (addon-a11y's `PANEL_ID` and `ADDON_ID`, re-exported under these names) | `[AST:code/addons/vitest/src/constants.ts:L7]` `[AST:code/addons/vitest/src/constants.ts:L8]` |
| `storeOptions` | const | Store config, `satisfies StoreOptions<StoreState>` (the universal store's options type, which `storybook/internal/types` exports under that name, not the manager-api `StoreOptions` of `story-types.md`): `{ id: ADDON_ID, initialState: { config: { coverage, a11y }, watching, cancelling, fatalError, index, previewAnnotations, currentRun: { triggeredBy, config: { coverage, a11y }, componentTestStatuses, a11yStatuses, a11yReports, componentTestCount, a11yCount, storyIds, totalTestCount, startedAt, finishedAt, unhandledErrors, coverageSummary } } }`. `coverage` and `a11y` sit under `initialState.config` (and `currentRun.config`), the status lists under `initialState.currentRun` | `[AST:code/addons/vitest/src/constants.ts:L21]` `[AST:code/core/src/shared/universal-store/types.ts:L67]` |
| `FULL_RUN_TRIGGERS` | const | `RunTrigger[]`, the value `['global', 'run-all']`: the triggers that count as a full run | `[AST:code/addons/vitest/src/constants.ts:L61]` |
| `TriggerTestRunRequestPayload` | type | `{ requestId, actor, storyIds?, config? }` | `[AST:code/addons/vitest/src/constants.ts:L74]` |
| `TestRunResult` | type | `CurrentRun` | `[AST:code/addons/vitest/src/constants.ts:L81]` |
| `TriggerTestRunResponsePayload` | type | `{ requestId, status, result?, error? }` | `[AST:code/addons/vitest/src/constants.ts:L83]` |

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

### Vitest plugin entry: default export

| Export | Kind | Purpose | Source |
|---|---|---|---|
| `default` | default export | `export default storybookTest`: the default export of `@storybook/addon-vitest/vitest-plugin` is its named `storybookTest` plugin factory, so `import storybookTest from '@storybook/addon-vitest/vitest-plugin'` gives the same function as the named import above | `[SRC:code/addons/vitest/src/vitest-plugin/index.ts:L531]` |

The addons' `./postinstall` entries default-export a function as well (tier B, run when the addon is added, not imported by stories): `@storybook/addon-a11y/postinstall`'s is an `async` function of `options: PostinstallOptions` (a type from the CLI's `add` command) that runs `storybook automigrate addon-a11y-addon-test` through the project's package manager. `[SRC:code/addons/a11y/src/postinstall.ts:L5]`

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
| `DocsRenderer` | class | `DocsRenderer<TRenderer extends Renderer>`, a plain class (not a React component) with two members, `render: DocsRenderFunction<TRenderer>` (mounts the `Docs` block for a docs entry into a DOM element through React) and `unmount: (element: HTMLElement) => void` | `[AST:code/addons/docs/src/DocsRenderer.tsx:L48]` `[AST:code/addons/docs/src/index.ts:L8]` |
| `DocsTypes` | interface | `{ parameters: DocsParameters }`, the addon's type bundle (`DocsParameters` holds the `docs` parameter's options), exported type-only | `[AST:code/addons/docs/src/index.ts:L9]` `[AST:code/addons/docs/src/types.ts:L254]` |

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
