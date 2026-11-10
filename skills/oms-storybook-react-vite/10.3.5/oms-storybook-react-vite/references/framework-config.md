# `@storybook/react-vite` Framework, Renderer, and Builder Layers

The v10 React+Vite stack has **three distinct layers**. Defects and configuration belong in the correct layer — knowing which one prevents tail-chasing when a story fails to render or a `main.ts` option is not picked up. All T1 from `code/frameworks/react-vite/`, `code/renderers/react/`, `code/builders/builder-vite/`.

## Contents

- [Layer model](#layer-model)
- [`@storybook/react-vite` — framework](#storybookreact-vite--framework)
- [`@storybook/react` — renderer](#storybookreact--renderer)
- [`@storybook/builder-vite` — builder](#storybookbuilder-vite--builder)
- [`main.ts` configuration contract](#maints-configuration-contract)
- [`preview.ts` authoring surface](#previewts-authoring-surface)
- [Portable stories with Vitest/Jest](#portable-stories-with-vitestjest)

## Layer model

```
┌──────────────────────────────────────────────────────────┐
│ @storybook/react-vite  (framework — the thing you pick)  │
│  ├── Composes @storybook/react  (renderer)               │
│  └── Drives @storybook/builder-vite  (builder)           │
└──────────────────────────────────────────────────────────┘
```

- **Framework** = the `framework` field in `main.ts`. Picks a renderer + builder pair and wires them together. Re-exports all CSF types from the renderer.
- **Renderer** = the React-specific rendering code. Defines `Meta`, `StoryObj`, `Decorator`, etc. Hosts `composeStories`/`composeStory` for portable stories.
- **Builder** = the Vite dev server + production build. Runs `viteFinal`, handles HMR, bundles `preview.js`.

**Defect localization:**
- Story renders blank or errors mid-render → **renderer** (`@storybook/react`)
- HMR doesn't update, build fails, Vite plugins conflict → **builder** (`@storybook/builder-vite`)
- `main.ts` framework field wrong, addon auto-detection fails, docgen not applied → **framework** (`@storybook/react-vite`)
- `play` function assertion fails → **`storybook/test`** (not a layer — it's a core subpath)
- Addon panel missing → the specific **addon** package

## `@storybook/react-vite` — framework

Source: `code/frameworks/react-vite/`

**Entries:**
- `.` → `src/index.ts`
- `./node` → `src/node/index.ts`
- `./preset` → `src/preset.ts`

### Main entry (`@storybook/react-vite`)

Re-exports **everything** from `@storybook/react`, plus framework-specific additions:

```ts
// code/frameworks/react-vite/src/index.ts
export * from '@storybook/react';
export { __definePreview as definePreview } from '@storybook/react';

export * from './types';
```

`definePreview` is the framework's name for the renderer's `__definePreview`; `@storybook/react` itself exports only `__definePreview`. `./types` supplies `StorybookConfig` and `FrameworkOptions`.

Types verified as re-exported from `@storybook/react`: `Meta`, `StoryObj`, `StoryFn`, `Decorator`, `Loader`, `StoryContext`, `Args`, `ArgTypes`, `Parameters`, `StrictArgs`, `ReactRenderer`, `Preview`. Plus portable-stories utilities (`composeStory`, `composeStories`, `setProjectAnnotations`) and CSF4 factory API.

### `./node` entry

For `main.ts` type safety:
```ts
import { defineMain } from '@storybook/react-vite/node';
// or
import type { StorybookConfig } from '@storybook/react-vite';
```

#### `defineMain`

```ts
// code/frameworks/react-vite/src/node/index.ts:3
export function defineMain(config: StorybookConfig): StorybookConfig
```

Identity helper — returns `config` as-is. Exists purely to anchor TypeScript inference at `.storybook/main.ts` so autocomplete and type-checking work on the `framework`, `addons`, and `viteFinal` fields without the user having to annotate the export explicitly.

**Usage:**

```ts
// .storybook/main.ts
import { defineMain } from '@storybook/react-vite/node';

export default defineMain({
  framework: '@storybook/react-vite',
  stories: ['../src/**/*.stories.@(ts|tsx|mdx)'],
  addons: ['@storybook/addon-docs', '@storybook/addon-a11y'],
  viteFinal: async (config) => {
    // config is now typed as InlineConfig — autocomplete works
    return config;
  },
});
```

Equivalent annotation without `defineMain` (also valid, slightly noisier):

```ts
import type { StorybookConfig } from '@storybook/react-vite';
const config: StorybookConfig = { /* ... */ };
export default config;
```

`[AST:code/frameworks/react-vite/src/node/index.ts:L3]`

#### `StorybookConfig`

The `main.ts` config interface (framework-augmented — `framework`, `addons`, `stories`, `viteFinal`, `docs`, `typescript`, `staticDirs`, …). `[AST:code/frameworks/react-vite/src/types.ts:L66]`

### `./preset` entry (internal)

```ts
// code/frameworks/react-vite/src/preset.ts
export const core: PresetProperty<'core'> = {
  builder: import.meta.resolve('@storybook/builder-vite'),
  renderer: import.meta.resolve('@storybook/react/preset'),
};
export const viteFinal: NonNullable<StorybookConfig['viteFinal']> = async (config, { presets }) => {
  // Reads `typescript.reactDocgen` through presets.apply('typescript'), adds the
  // react-docgen-typescript plugin (when that option is 'react-docgen-typescript' and
  // typescript resolves) and the react-docgen plugin (when the option is a string)
  // ...
  return { ...config, plugins };
};
```

`core` gives the builder and renderer as resolved module URLs (`import.meta.resolve(...)`), not as bare package names. `viteFinal` is typed by the framework's own `StorybookConfig` (`./types`), and destructures `presets` from its second argument. Storybook itself calls this preset during setup — rarely imported by users. `[AST:code/frameworks/react-vite/src/preset.ts:L5]` `[AST:code/frameworks/react-vite/src/preset.ts:L10]`

## `@storybook/react` — renderer

Source: `code/renderers/react/`

**Entries:**
- `.` → `src/index.ts`
- `./preview` → `src/preview.tsx`
- `./experimental-playwright` → `src/playwright.ts`

### Main entry (`@storybook/react`)

Definitive source for CSF story types — `Meta`, `StoryObj`, `StoryFn`, `Decorator`, `Loader`, `StoryContext`, `Preview` (see `story-types.md` for full signatures). Also exports:

- `composeStory`, `composeStories`, `setProjectAnnotations`, `INTERNAL_DEFAULT_PROJECT_ANNOTATIONS` (portable stories)
- `__definePreview`, `ReactPreview`, `ReactMeta`, `ReactStory` (CSF4 factory API)

`[SRC:code/renderers/react/src/index.ts]` `[SRC:code/renderers/react/src/public-types.ts]`

### `./experimental-playwright`

```ts
// code/renderers/react/src/playwright.ts
export { createPlaywrightTest as createTest } from 'storybook/preview-api';
```

Helper for portable stories in Playwright CT. `storybook/preview-api` exports it as `createPlaywrightTest<TFixture extends { extend: any }>(baseTest: TFixture): TFixture`, which extends a Playwright CT `test` with a `mount` fixture that accepts story references; the renderer re-exports it under the name `createTest`. `[AST:code/renderers/react/src/playwright.ts:L1]` `[AST:code/core/src/preview-api/index.ts:L71]` `[AST:code/core/src/preview-api/modules/store/csf/portable-stories.ts:L319]`

## `@storybook/builder-vite` — builder

Source: `code/builders/builder-vite/`. Users rarely import from here — the framework drives the builder via `main.ts` `viteFinal`.

### Main entry exports

```ts
// code/builders/builder-vite/src/index.ts
export async function bail(): Promise<void>;                         // L37
export const start: ViteBuilder['start'] = async ({ startTime, options, router, server }) => …;  // L41 (binds server as devServer)
export const build: ViteBuilder['build'] = async ({ options }) => …;  // L63
export const corePresets: string[];
export { withoutVitePlugins } from './utils/without-vite-plugins';    // L14
export { hasVitePlugins } from './utils/has-vite-plugins';            // L15

// ViteBuilder = Builder<UserConfig, ViteStats>, so start and build each take ONE object, typed by
// Builder (code/core/src/types/modules/core-common.ts:259), and destructure it:
//   start: ({ startTime, options, router, server }: { options: Options; startTime: ReturnType<typeof process.hrtime>; router: ServerApp;
//                   server: HttpServer; channel: ChannelLike })
//     => Promise<void | { stats?: ViteStats; totalTime: ReturnType<typeof process.hrtime>; bail: (e?: Error) => Promise<void> }>
//   build: ({ options }: { options: Options; startTime: ReturnType<typeof process.hrtime> }) => Promise<void | ViteStats>

// code/builders/builder-vite/src/utils/without-vite-plugins.ts:2
export const withoutVitePlugins = async <TPlugin>(plugins: TPlugin[] = [], namesToRemove: string[]): Promise<TPlugin[]> => …;
// code/builders/builder-vite/src/utils/has-vite-plugins.ts:13
export async function hasVitePlugins(plugins: PluginOption[], names: string[]): Promise<boolean>;

export type ViteBuilder = Builder<UserConfig, ViteStats>;
export type ViteFinal = (config: InlineConfig, options: Options) => InlineConfig | Promise<InlineConfig>;
export type StorybookConfigVite = { viteFinal?: ViteFinal };
export type BuilderOptions = { viteConfigPath?: string };
```

Both plugin helpers work on a plugin array (they resolve async plugins and recurse into nested arrays), not on an `InlineConfig`. The builder's own build uses them this way: `await hasVitePlugins(finalConfig.plugins, [turbosnapPluginName])` resolves to a boolean, and `finalConfig.plugins = await withoutVitePlugins(finalConfig.plugins, [turbosnapPluginName])` replaces the array with the filtered one. `[SRC:code/builders/builder-vite/src/build.ts:L82]` `[SRC:code/builders/builder-vite/src/build.ts:L89]`

`[AST:code/builders/builder-vite/src/index.ts:L37]` `[AST:code/builders/builder-vite/src/index.ts:L41]` `[AST:code/builders/builder-vite/src/index.ts:L63]` `[SRC:code/builders/builder-vite/src/utils/without-vite-plugins.ts:L2]` `[SRC:code/builders/builder-vite/src/utils/has-vite-plugins.ts:L13]` `[AST:code/builders/builder-vite/src/types.ts:L10]` `[AST:code/builders/builder-vite/src/types.ts:L12]` `[AST:code/builders/builder-vite/src/types.ts:L17]` `[AST:code/builders/builder-vite/src/types.ts:L21]` `[AST:code/core/src/types/modules/core-common.ts:L259]`

## `main.ts` configuration contract

```ts
// .storybook/main.ts
import type { StorybookConfig } from '@storybook/react-vite';

const config: StorybookConfig = {
  framework: '@storybook/react-vite',
  stories: [
    '../src/**/*.mdx',
    '../src/**/*.stories.@(js|jsx|ts|tsx)',
  ],
  addons: [
    '@storybook/addon-docs',
    '@storybook/addon-a11y',
    '@storybook/addon-themes',
    '@storybook/addon-vitest',
  ],
  typescript: {
    reactDocgen: 'react-docgen-typescript',
  },
  viteFinal: async (config) => {
    // Customize Vite config
    return config;
  },
};

export default config;
```

### Framework field variants

```ts
// String form — simplest
framework: '@storybook/react-vite';

// Object form — framework options
framework: {
  name: '@storybook/react-vite',
  options: {
    builder: {
      // Vite builder options
    },
  },
};
```

The object form's `options` is `FrameworkOptions = { builder?: BuilderOptions; strictMode?: boolean; legacyRootApi?: boolean }`, where `BuilderOptions = { viteConfigPath?: string }` (builder-vite) and `legacyRootApi` (default `false`) mounts with React's legacy root API.

`[EXT:https://storybook.js.org/docs/get-started/frameworks/react-vite/]` `[AST:code/frameworks/react-vite/src/types.ts:L14]` `[AST:code/builders/builder-vite/src/types.ts:L21]`

### Available `main.ts` keys (partial)

From the API reference (T3): `framework`, `stories`, `addons`, `babel`, `babelDefault`, `build`, `core`, `docs`, `env`, `features`, `indexers`, `logLevel`, `managerHead`, `previewAnnotations`, `previewBody`, `previewHead`, `refs`, `staticDirs`, `swc`, `tags`, `typescript`, `viteFinal`, `webpackFinal`. `[EXT:https://storybook.js.org/docs/api]`

## `preview.ts` authoring surface

The brief treats `preview.ts` as **authoring surface**, not config — it is edited weekly during story authoring (not quarterly like `main.ts`).

```ts
// .storybook/preview.ts
import type { Preview, Decorator } from '@storybook/react-vite';
import { withThemeByClassName } from '@storybook/addon-themes';

const withPadding: Decorator = (Story) => (
  <div style={{ padding: 16 }}>
    <Story />
  </div>
);

const preview: Preview = {
  // parameters apply to every story unless overridden
  parameters: {
    controls: { matchers: { color: /(background|color)$/i, date: /Date$/ } },
    backgrounds: { default: 'light' },
    a11y: { test: 'todo' },
    docs: { toc: true },
  },

  // decorators wrap every story
  decorators: [
    withPadding,
    withThemeByClassName({ themes: { light: '', dark: 'dark' }, defaultTheme: 'light' }),
  ],

  // globalTypes create toolbar selectors for cross-story globals
  globalTypes: {
    locale: {
      description: 'Locale',
      defaultValue: 'en',
      toolbar: { icon: 'globe', items: ['en', 'fr', 'ja'] },
    },
  },

  // initialGlobals seeds values for globalTypes
  initialGlobals: { locale: 'en' },

  // loaders run before every story (data fetching, mocks)
  loaders: [
    async () => ({ currentUser: { name: 'Alice' } }),
  ],

  // tags propagate to every story
  tags: ['autodocs'],

  // beforeEach runs before each story's play function
  beforeEach: async () => {
    // setup
  },

  // beforeAll runs once when preview initializes
  beforeAll: async () => {
    // setup
  },
};

export default preview;
```

`[AST:code/renderers/react/src/public-types.ts:L80]` `[SRC:code/core/src/types/index.ts]`

**Preview vs meta vs story:** parameters, decorators, loaders, and tags cascade preview → meta → story, with later levels overriding. Use `preview.ts` for global concerns (theming, a11y, top-level mocks); use meta for per-component concerns; use story for per-variant concerns.

## Portable stories with Vitest/Jest

Portable stories let you reuse stories as test subjects in Vitest, Jest, or Playwright CT.

### Vitest setup (2 files)

```ts
// .storybook/vitest.setup.ts — runs ONCE before all tests
import { setProjectAnnotations } from '@storybook/react';
import * as projectAnnotations from './preview';

setProjectAnnotations([projectAnnotations]);
```

```ts
// vitest.config.ts
import { defineConfig } from 'vitest/config';

export default defineConfig({
  test: {
    setupFiles: ['./.storybook/vitest.setup.ts'],
    // ...
  },
});
```

### Per-test-file usage

```ts
// Button.test.ts
import { test, expect } from 'vitest';
import { render, screen } from '@testing-library/react';
import { composeStories } from '@storybook/react';
import * as stories from './Button.stories';

const { Primary, Clicked } = composeStories(stories);

test('Primary renders', () => {
  render(<Primary />);
  expect(screen.getByRole('button')).toBeInTheDocument();
});

test('Clicked runs play function', async () => {
  await Clicked.run();  // executes the story's play function
});
```

`composeStories` applies:
1. The project annotations from `setProjectAnnotations` (globalTypes, top-level decorators, loaders)
2. The meta's annotations (component, args, argTypes, decorators)
3. The story's own annotations

Result: each story export becomes a React component that renders exactly as it would in Storybook. `[AST:code/renderers/react/src/portable-stories.tsx:L46]` `[QMD:oms-storybook-react-vite-temporal:changelog.md #5defd6]`

## Theming types (`storybook/theming`)

Needed when you're authoring a **custom Storybook theme** — either for the manager UI (`.storybook/manager.ts`) or for a custom docs theme. Most story authors never import these — `import { create } from 'storybook/theming/create'` and pass a partial is enough.

| Export | Kind | Signature | Source |
|---|---|---|---|
| `StorybookTheme` | interface | `{ color: Color; background: Background; typography: Typography; … }` — complete theme object that `convert` and `ensure` build from a `ThemeVars` | `[AST:code/core/src/theming/types.ts:L71]` |
| `ThemeVars` | interface | `extends ThemeVarsBase, ThemeVarsColors {}` — the full theme input object (base + colors) | `[AST:code/core/src/theming/types.ts:L4]` |
| `ThemeVarsPartial` | interface | `extends ThemeVarsBase, Partial<ThemeVarsColors> {}` — partial override accepted by `create()` | `[AST:code/core/src/theming/types.ts:L6]` |
| `ThemeVarsColors` | interface | `{ colorPrimary: string; colorSecondary: string; … }` — complete color palette | `[AST:code/core/src/theming/types.ts:L12]` |
| `Typography` | type | `typeof typography` — fonts, weights, sizes namespace | `[AST:code/core/src/theming/types.ts:L59]` |
| `TextSize` | type | `number \| string` — pixel count or CSS unit | `[AST:code/core/src/theming/types.ts:L63]` |
| `Brand` | interface | `{ title: string \| undefined; url: string \| null \| undefined; image: string \| null \| undefined; target: string \| null \| undefined }` — sidebar brand block; all four keys are required, each accepting `undefined` | `[AST:code/core/src/theming/types.ts:L64]` |
| `Color` | type | `typeof color` — named color tokens (primary, secondary, gold, green, etc.) | `[AST:code/core/src/theming/types.ts:L57]` |
| `Background` | type | `typeof background` — background color tokens (app, bar, content, critical, warning, hoverable) | `[AST:code/core/src/theming/types.ts:L58]` |
| `Animation` | type | `typeof animation` — keyframes and motion tokens | `[AST:code/core/src/theming/types.ts:L60]` |
| `Easing` | type | `typeof easing` — the easing tokens of `theming/animation.ts`, `{ rubber: 'cubic-bezier(0.175, 0.885, 0.335, 1.05)' }`, the type of the theme's `easing` field (`storybook/theming` exports the type, not the `easing` value) | `[AST:code/core/src/theming/types.ts:L61]` |

**Building a custom theme:**

```ts
// .storybook/custom-theme.ts
import { create } from 'storybook/theming/create';
import type { ThemeVarsPartial } from 'storybook/theming';

const overrides: ThemeVarsPartial = {
  base: 'light',
  colorPrimary: '#ff4785',
  colorSecondary: '#1ea7fd',
  brandTitle: 'My Design System',
  brandUrl: 'https://example.com',
  fontBase: '"Helvetica Neue", sans-serif',
};

export default create(overrides);
```

```ts
// .storybook/manager.ts
import { addons } from 'storybook/manager-api';
import customTheme from './custom-theme';

addons.setConfig({ theme: customTheme });
```

`[AST:code/core/src/theming/create.ts:L29]`
