# `storybook` Core Package — Full API Reference

The consolidated `storybook` package exposes 40 subpath exports. This reference covers the 28 authoring-surface and type-surface subpaths extracted for v10.3.5. All provenance is T1 — read from source via AST.

## v10 Consolidated Imports Map (all packages in scope)

Every import this skill teaches, grouped by source package and subpath. Column 3 is the canonical v10 import path — **this is the load-bearing part** the skill corrects against training data.

| Import | Kind | From (v10 consolidated) |
|---|---|---|
| `Meta`, `StoryObj`, `StoryFn`, `Decorator`, `Parameters`, `ArgTypes`, `Args`, `StoryContext`, `Loader`, `Preview` | type | `@storybook/react-vite` *(or `@storybook/react`)* `[AST:code/renderers/react/src/public-types.ts:L29]` |
| `StorybookConfig`, `FrameworkOptions` | type | `@storybook/react-vite` `[AST:code/frameworks/react-vite/src/types.ts:L66]` `[AST:code/frameworks/react-vite/src/types.ts:L14]` |
| `defineMain` | function | `@storybook/react-vite/node` `[AST:code/frameworks/react-vite/src/node/index.ts:L3]` |
| `expect`, `fn`, `within`, `screen`, `waitFor`, `userEvent`, `fireEvent`, `spyOn` | runtime | `storybook/test` `[AST:code/core/src/test/index.ts:L54]` |
| `useState`, `useArgs`, `useParameter`, `useChannel`, `useEffect`, `useGlobals`, `useCallback`, `useMemo`, `useRef`, `useReducer`, `useStoryContext` | hook | `storybook/preview-api` `[AST:code/core/src/preview-api/index.ts:L5]` |
| `addons`, `makeDecorator`, `mockChannel` | runtime | `storybook/preview-api` `[AST:code/core/src/preview-api/index.ts:L21]` |
| `composeStories`, `composeStory`, `setProjectAnnotations` | runtime | **`@storybook/react-vite`** *(canonical for React+Vite — re-exported from `@storybook/react` where they're defined)* `[AST:code/renderers/react/src/portable-stories.tsx:L148]` |
| `definePreview` *(CSF4 factory: `@storybook/react` exports it as `__definePreview`, and `@storybook/react-vite` re-exports that function under the name `definePreview`)* | runtime | `@storybook/react-vite` `[SRC:code/frameworks/react-vite/src/index.ts:L2]` `[AST:code/renderers/react/src/preview.tsx:L55]` |
| `action` | runtime | `storybook/actions` `[AST:code/core/src/actions/index.ts:L1]` |
| `create`, `themes`, `styled`, `css`, `useTheme`, `ThemeProvider` | runtime | `storybook/theming` / `storybook/theming/create` `[AST:code/core/src/theming/create.ts:L29]` |
| `HIGHLIGHT`, `RESET_HIGHLIGHT` | const | `storybook/highlight` `[AST:code/core/src/highlight/index.ts:L1]` |
| `Canvas`, `Meta`, `Controls`, `Primary`, `Stories`, `Story`, `ArgTypes`, `Source`, `Description`, `Title`, `Markdown`, `Typeset`, `ColorPalette`, `IconGallery`, `Unstyled`, `useOf`, `DocsContainer`, `DocsPage` | MDX block | `@storybook/addon-docs/blocks` `[AST:code/addons/docs/src/blocks.ts:L1]` |
| `withThemeByClassName`, `withThemeByDataAttribute`, `withThemeFromJSXProvider` | decorator | `@storybook/addon-themes` `[AST:code/addons/themes/src/index.ts:L1]` |
| a11y `parameters: { a11y: { test: ... } }`, runtime `afterEach`, `decorators`, `initialGlobals` | param + runtime | `@storybook/addon-a11y` / `@storybook/addon-a11y/preview` — the runtime `afterEach(context)` at `[AST:code/addons/a11y/src/preview.tsx:L14]` runs axe-core per story and attaches an `A11yReport` to `context.reporting`; compose it manually in your `preview.ts` only when you need multiple `afterEach` hooks | `[AST:code/addons/a11y/src/preview.tsx:L14]` |

The rest of this file documents each `storybook/*` subpath in detail. CSF types live in `story-types.md`; MDX blocks in `doc-blocks.md`; addon exports in `addons.md`; framework/renderer/builder layer in `framework-config.md`.

## Contents

- [`storybook/test`](#storybooktest) — Test utilities for `play` functions
- [`storybook/preview-api`](#storybookpreview-api) — Hooks, decorators, portable stories
- [`storybook/manager-api`](#storybookmanager-api) — Manager-side addon API
- [`storybook/theming`](#storybooktheming) — Theme utilities, styled components
- [`storybook/theming/create`](#storybookthemingcreate) — Theme builder
- [`storybook/actions`](#storybookactions) — Action logger
- [`storybook/actions/decorator`](#storybookactionsdecorator) — `withActions`
- [`storybook/highlight`](#storybookhighlight) — Highlight events
- [`storybook/viewport`](#storybookviewport) — Viewport addon API
- [`storybook/internal/types`](#storybookinternaltypes) — CSF type re-exports
- [`storybook/internal/csf`](#storybookinternalcsf) — CSF helpers
- [`storybook/internal/preview-errors`](#storybookinternalpreview-errors) — Preview error classes
- [`storybook/internal/server-errors`](#storybookinternalserver-errors) — Server error classes
- [`storybook/internal/components`](#storybookinternalcomponents) — Addon panel UI components (outside this skill's scope)
- [Infrastructure subpaths (tier C)](#infrastructure-subpaths-tier-c) — channels, router, loggers, etc.

The full export lists of these subpaths, with declarations and source lines, are in `api-index-core.md` and `api-index-types.md`.

## storybook/test

Entry: `code/core/src/test/index.ts`. These are the `play` function utilities — imported anywhere you write assertions or simulate user interactions.

| Export | Kind | Signature / Purpose | Source |
|---|---|---|---|
| `expect` | const | Vitest/Chai-compatible assertion function with full matcher set; the public export is the instrumented one, destructured as `export const { expect } = instrument({ expect: createExpect() }, …)` | `[SRC:code/core/src/test/index.ts:L24]` `[AST:code/core/src/test/expect.ts:L139]` |
| `fn` | function | `fn<T>(impl?: T): Mock<T>` — create a mock function for `args` | `[AST:code/core/src/test/spy.ts:L48]` |
| `spyOn` | function | `spyOn(obj, method)` — spy on an existing method (typed as Vitest's `spyOn`) | `[AST:code/core/src/test/spy.ts:L41]` |
| `within` | function | `within(element)` — scope DOM queries to a subtree; destructured from the instrumented `@testing-library/dom` namespace (`export const { …, within, … } = testingLibrary`, opened at line 39) | `[AST:code/core/src/test/testing-library.ts:L110]` |
| `screen` | const proxy | Global DOM query object (warns inside docs mode); destructured from the same instrumented namespace | `[AST:code/core/src/test/testing-library.ts:L107]` |
| `waitFor` | function | Wait for an async DOM condition; destructured from the same instrumented namespace | `[AST:code/core/src/test/testing-library.ts:L108]` |
| `fireEvent` | const | Promisified `@testing-library/dom` fireEvent; destructured from the same instrumented namespace | `[AST:code/core/src/test/testing-library.ts:L43]` |
| `userEvent` | const | Full `@testing-library/user-event` API, destructured as `export const { userEvent } = instrument({ userEvent: _userEvent.userEvent }, …)` | `[AST:code/core/src/test/testing-library.ts:L123]` |
| `getByRole` / `findByRole` / `queryByRole` (+ 30 other `*ByText`, `*ByLabelText`, `*ByPlaceholderText`, `*ByTestId` queries) | function | DOM element query helpers, destructured from the instrumented namespace in the statement that opens at line 39 | `[AST:code/core/src/test/testing-library.ts:L39]` |
| `sb` | const | `{ mock }` — module-level mock utilities | `[AST:code/core/src/test/index.ts:L54]` |
| `Mock`, `MockInstance`, `MaybeMocked` | type | Mock function type helpers, re-exported from `@vitest/spy` by `export type * from '@vitest/spy'` | `[SRC:code/core/src/test/spy.ts:L15]` |

**Migration note:** `@storybook/test` is the v9-and-earlier package name and is **deprecated**. Always import from `storybook/test` in v10. `[QMD:oms-storybook-react-vite-temporal:issues.md #9b8716]`

## storybook/preview-api

Entry: `code/core/src/preview-api/index.ts`. Hooks run inside decorators and `render` functions; the `composeStories` / `setProjectAnnotations` pair enables portable stories in Vitest/Jest.

**Hooks:**

| Export | Kind | Purpose | Source |
|---|---|---|---|
| `useState` | hook | Local state inside a decorator or `render` | `[AST:code/core/src/preview-api/index.ts:L14]` |
| `useEffect` | hook | Side effects keyed by deps | `[AST:code/core/src/preview-api/index.ts:L8]` |
| `useCallback` | hook | Memoized callback | `[AST:code/core/src/preview-api/index.ts:L6]` |
| `useMemo` | hook | Memoized value | `[AST:code/core/src/preview-api/index.ts:L10]` |
| `useRef` | hook | Mutable ref persisted across renders | `[AST:code/core/src/preview-api/index.ts:L13]` |
| `useReducer` | hook | State reducer | `[AST:code/core/src/preview-api/index.ts:L12]` |
| `useArgs` | hook | `[args, updateArgs, resetArgs]` — read/write current story args | `[AST:code/core/src/preview-api/index.ts:L5]` |
| `useParameter` | hook | `useParameter(key, default)` — read story parameters | `[AST:code/core/src/preview-api/index.ts:L11]` |
| `useGlobals` | hook | `[globals, updateGlobals]` — read/write globals (theme, locale) | `[AST:code/core/src/preview-api/index.ts:L9]` |
| `useChannel` | hook | Subscribe to addon events | `[AST:code/core/src/preview-api/index.ts:L7]` |
| `useStoryContext` | hook | Full story context object | `[AST:code/core/src/preview-api/index.ts:L15]` |

**Decorators, addons, and portable stories:**

| Export | Kind | Purpose | Source |
|---|---|---|---|
| `makeDecorator` | function | Create a reusable addon decorator | `[AST:code/core/src/preview-api/index.ts:L21]` |
| `applyHooks` | function | Apply a hooks context (experimental) | `[AST:code/core/src/preview-api/index.ts:L16]` |
| `addons` | const | Singleton `AddonStore` — register addon types, channels | `[AST:code/core/src/preview-api/index.ts:L28]` |
| `mockChannel` | function | Create a mock channel for unit tests | `[AST:code/core/src/preview-api/index.ts:L28]` |
| `composeStory` | function | `composeStory<TRenderer, TArgs>(storyAnnotations: LegacyStoryAnnotationsOrFn<TRenderer>, componentAnnotations: ComponentAnnotations<TRenderer, TArgs>, projectAnnotations?: ProjectAnnotations<TRenderer>, defaultConfig?: ProjectAnnotations<TRenderer>, exportsName?: string): ComposedStoryFn<TRenderer, Partial<TArgs>>` — the renderer-agnostic primitive. React+Vite story tests use the four-parameter `composeStory(story, componentAnnotations, projectAnnotations?, exportsName?)` from `@storybook/react-vite` instead (`story-types.md` "Portable stories utilities"). | `[SRC:code/core/src/preview-api/modules/store/csf/portable-stories.ts:L90]` `[AST:code/core/src/preview-api/index.ts:L52]` |
| `composeStories` | function | `composeStories<TModule extends Store_CSFExports>(storiesImport: TModule, globalConfig: ProjectAnnotations<Renderer>, composeStoryFn: ComposeStoryFn = defaultComposeStory)` — the renderer-agnostic primitive; `globalConfig` is required. React+Vite story tests use `composeStories(csfExports, projectAnnotations?)` from `@storybook/react-vite` instead. | `[SRC:code/core/src/preview-api/modules/store/csf/portable-stories.ts:L274]` `[AST:code/core/src/preview-api/index.ts:L51]` |
| `setProjectAnnotations` | function | Set global project annotations for portable stories (call once in test setup) | `[AST:code/core/src/preview-api/index.ts:L46]` |
| `definePreview` | function | **Not exported by `storybook/preview-api`.** The CSF4 factory comes from `@storybook/react-vite` (`definePreview`, the renderer's `__definePreview` re-exported under that name) for React+Vite projects; the renderer-agnostic `definePreview` is in `storybook/internal/csf` | `[SRC:code/frameworks/react-vite/src/index.ts:L2]` `[SRC:code/core/src/csf/csf-factories.ts:L45]` |
| `decorateStory`, `defaultDecorateStory`, `combineArgs`, `combineParameters`, `composeConfigs`, `composeStepRunners`, `normalizeArrays`, `normalizeStory`, `normalizeProjectAnnotations`, `prepareStory`, `prepareMeta`, `filterArgTypes`, `sanitizeStoryContextUpdate`, `setDefaultProjectAnnotations`, `inferControls`, `userOrAutoTitleFromSpecifier`, `userOrAutoTitle`, `sortStoriesV7` | function | Internal composition utilities (rarely imported by authors) | `[AST:code/core/src/preview-api/index.ts:L46-68]` |
| `HooksContext` | type | Hooks context shape | `[AST:code/core/src/preview-api/index.ts:L17]` |
| `DocsContext` | type | Autodocs rendering context | `[AST:code/core/src/preview-api/index.ts:L41]` |
| `Preview`, `PreviewWeb`, `PreviewWithSelection`, `StoryStore`, `UrlStore`, `WebView` | class | Preview runtime classes (internal). **Not to be confused with the `Preview` type** exported by `@storybook/react-vite` / `@storybook/react` (which is `ProjectAnnotations<ReactRenderer>` — the `.storybook/preview.ts` default-export shape). The runtime `Preview` class lives at `code/core/src/preview-api/modules/preview-web/Preview.tsx:60` and is aliased to `PreviewWeb` at `PreviewWeb.tsx:11`. | `[AST:code/core/src/preview-api/modules/preview-web/Preview.tsx:L60]` |

**Migration note:** `setProjectAnnotations` was expanded to more renderers/frameworks in PR #28907. `[QMD:oms-storybook-react-vite-temporal:changelog.md #5defd6]`

### Preview-API composition utilities (declared locations)

The re-export table above lists the public surface; the rows below pin each symbol to its **actual declaration file** so you can step into source when a signature disagrees with the re-export row. Useful to portable-stories authors, test-harness maintainers, and anyone writing a custom preview runtime.

| Export | Kind | Signature | Source |
|---|---|---|---|
| `combineArgs` | const | `(value: any, update: any) => Args` — deep-merge two args objects | `[AST:code/core/src/preview-api/modules/store/args.ts:L84]` |
| `combineParameters` | const | `(...parameterSets: (Parameters \| undefined)[]) => Parameters` — recursively merge parameter bags preserving plain objects | `[AST:code/core/src/preview-api/modules/store/parameters.ts:L11]` |
| `composeConfigs` | function | `<R extends Renderer>(moduleExportList: ModuleExports[]) => NormalizedProjectAnnotations<R>` — fold config modules into a single normalized ProjectAnnotations | `[AST:code/core/src/preview-api/modules/store/csf/composeConfigs.ts:L43]` |
| `composeStepRunners` | function | `<R>(stepRunners: StepRunner<R>[]) => StepRunner<R>` — sequence step runners into one | `[AST:code/core/src/preview-api/modules/store/csf/stepRunners.ts:L27]` |
| `filterArgTypes` | const | `(argTypes: StrictArgTypes, include?: PropDescriptor, exclude?: PropDescriptor) => StrictArgTypes` — filter by regex array or name list | `[AST:code/core/src/preview-api/modules/store/filterArgTypes.ts:L10]` |
| `inferControls` | const | `ArgTypesEnhancer<Renderer>` — auto-pick control types from runtime arg values + matchers | `[AST:code/core/src/preview-api/modules/store/inferControls.ts:L66]` |
| `normalizeStory` | function | `<R>(key: StoryId, storyAnnotations: StoryAnnotationsOrFn<R>, meta: NormalizedComponentAnnotations<R>) => NormalizedStoryAnnotations<R>` | `[AST:code/core/src/preview-api/modules/store/csf/normalizeStory.ts:L25]` |
| `normalizeArrays` | const | `<T>(array: T[] \| T \| undefined) => T[]` — coerce single/undefined to array | `[AST:code/core/src/preview-api/modules/store/csf/normalizeArrays.ts:L1]` |
| `normalizeProjectAnnotations` | function | `<R>(annotations: ProjectAnnotations<R>) => NormalizedProjectAnnotations<R>` — run arg-type enhancement pipeline | `[AST:code/core/src/preview-api/modules/store/csf/normalizeProjectAnnotations.ts:L17]` |
| `prepareStory` | function | `<R>(storyAnnotations, componentAnnotations, projectAnnotations) => PreparedStory<R>` — merge annotations + wire decorators/loaders/hooks | `[AST:code/core/src/preview-api/modules/store/csf/prepareStory.ts:L37]` |
| `prepareMeta` | function | `<R>(componentAnnotations, projectAnnotations, moduleExport) => PreparedMeta<R>` — component-level prep step | `[AST:code/core/src/preview-api/modules/store/csf/prepareStory.ts:L171]` |
| `sanitizeStoryContextUpdate` | function | `(inputContextUpdate?: StoryContextUpdate) => StoryContextUpdate` — strip immutable keys (id, name, story, kind, …) | `[AST:code/core/src/preview-api/modules/store/decorators.ts:L30]` |
| `sortStoriesV7` | const | `(stories, storySortParameter, fileNameOrder) => IndexEntry[]` — apply `parameters.options.storySort` | `[AST:code/core/src/preview-api/modules/store/sortStories.ts:L37]` |
| `defaultDecorateStory` | function | `<R>(storyFn: LegacyStoryFn<R>, decorators: DecoratorFunction<R>[]) => LegacyStoryFn<R>` — chain decorators with context binding | `[AST:code/core/src/preview-api/modules/store/decorators.ts:L49]` |
| `decorateStory` | function | `<R>(storyFn, decorator, bindWithContext) => LegacyStoryFn<R>` — single-decorator variant | `[AST:code/core/src/preview-api/modules/store/decorators.ts:L10]` |
| `applyHooks` | const | `<R>(applyDecorators: DecoratorApplicator<R>) => DecoratorApplicator<R>` — wrap decorator applicator with hooks runtime | `[AST:code/core/src/preview-api/modules/addons/hooks.ts:L184]` |
| `mockChannel` | function | `() => Channel` — create a mock addon channel for tests | `[AST:code/core/src/preview-api/modules/addons/storybook-channel-mock.ts:L3]` |

### Test-harness mock utilities (`storybook/test`)

These mirror Vitest's `vi.*` mock helpers but are re-exported through `storybook/test` so play functions can manipulate mocks without importing Vitest directly.

| Export | Kind | Signature | Source |
|---|---|---|---|
| `onMockCall` | function | `(callback: Listener) => () => void` — register global listener on any mock-function call | `[AST:code/core/src/test/spy.ts:L35]` |
| `isMockFunction` | const | `typeof isMockFunction` — re-exported from `@vitest/spy` | `[AST:code/core/src/test/spy.ts:L17]` |
| `clearAllMocks` | function | `() => void` — clear call history, keep implementations | `[AST:code/core/src/test/spy.ts:L77]` |
| `resetAllMocks` | function | `() => void` — reset call history and return values to undefined | `[AST:code/core/src/test/spy.ts:L89]` |
| `restoreAllMocks` | function | `() => void` — restore original implementations (undo `spyOn`) | `[AST:code/core/src/test/spy.ts:L98]` |
| `mocked` | function | overloads: `mocked<T>(item: T, deep?: false): MaybeMocked<T>`; `mocked<T>(item: T, deep: true): MaybeMockedDeep<T>`; `mocked<T>(item: T, options: { partial?: false; deep?: false }): MaybeMocked<T>`; `mocked<T>(item: T, options: { partial?: false; deep: true }): MaybeMockedDeep<T>`; `mocked<T>(item: T, options: { partial: true; deep?: false }): MaybePartiallyMocked<T>`; `mocked<T>(item: T, options: { partial: true; deep: true }): MaybePartiallyMockedDeep<T>`; `mocked<T>(item: T): MaybeMocked<T>` — TS type helper that returns `item` unchanged; the return type follows `deep` (boolean second argument or option) and `partial` | `[AST:code/core/src/test/spy.ts:L119]` |
| `mocks` | const | `typeof mocks` — re-exported from `@vitest/spy`, set of active mocks | `[AST:code/core/src/test/spy.ts:L17]` |

## storybook/manager-api

Entry: `code/core/src/manager-api/index.ts`. Used when writing a **manager-side** addon (addon panels, toolbar buttons, sidebar items). Not needed for story authoring.

| Export | Kind | Purpose | Source |
|---|---|---|---|
| (re-exports `./root`) | — | Full addon manager API: story selection, notifications, refs, globals, settings | `[AST:code/core/src/manager-api/index.ts]` |
| `experimental_UniversalStore` | class | Cross-environment state store | `[AST:code/core/src/manager-api/index.ts:L3]` |
| `experimental_useUniversalStore` | hook | Access a universal store in manager components (`useUniversalStore` exported under this name) | `[SRC:code/core/src/shared/universal-store/use-universal-store-manager.ts:L16]` |
| `experimental_MockUniversalStore` | class | Mock store for tests (`MockUniversalStore` exported under this name) | `[SRC:code/core/src/shared/universal-store/mock.ts:L40]` |
| `experimental_useStatusStore`, `experimental_getStatusStore` | hook/func | Status store access (panel badges, test results): `useStatusStore` and `getStatusStoreByTypeId`, destructured from the manager's status store and exported under these names | `[SRC:code/core/src/manager-api/stores/status.ts:L15]` |
| `experimental_useTestProviderStore`, `experimental_getTestProviderStore` | hook/func | Test provider state (addon-vitest): `useTestProviderStore` and `getTestProviderStoreById`, exported under these names | `[SRC:code/core/src/manager-api/stores/test-provider.ts:L17]` |
| `Tag` | enum | Story tagging system | `[AST:code/core/src/manager-api/index.ts:L26]` |

## storybook/theming

Entry: `code/core/src/theming/index.ts`. Emotion-based styling used by Storybook's UI and addon panels.

| Export | Kind | Purpose | Source |
|---|---|---|---|
| `styled` | const | Emotion `styled` — `styled.div\`...\`` | `[AST:code/core/src/theming/index.ts:L6]` |
| `css` | function | Emotion `css` tagged template (re-exported from `@emotion/react`) | `[AST:code/core/src/theming/index.ts:L13]` |
| `keyframes` | function | Emotion `keyframes` for animations (re-exported from `@emotion/react`) | `[AST:code/core/src/theming/index.ts:L16]` |
| `Global` | component | Emotion `Global` styles (re-exported from `@emotion/react`) | `[SRC:code/core/src/theming/index.ts:L14]` |
| `ThemeProvider` | component | Emotion `ThemeProvider` with Storybook theme type (re-exported from `@emotion/react`) | `[AST:code/core/src/theming/index.ts:L17]` |
| `useTheme` | hook | Access current theme (re-exported from `@emotion/react`) | `[AST:code/core/src/theming/index.ts:L18]` |
| `withTheme` | HOC | HOC wrapper for class components (re-exported from `@emotion/react`) | `[SRC:code/core/src/theming/index.ts:L19]` |
| `jsx` | function | Emotion JSX runtime (re-exported from `@emotion/react`) | `[SRC:code/core/src/theming/index.ts:L15]` |
| `CacheProvider`, `ClassNames` | component | Emotion cache/classnames (re-exported from `@emotion/react`) | `[SRC:code/core/src/theming/index.ts:L11]` `[SRC:code/core/src/theming/index.ts:L12]` |
| `createCache` | function | Create an emotion cache | `[AST:code/core/src/theming/index.ts:L33]` |
| `isPropValid` | function | `@emotion/is-prop-valid` filter | `[AST:code/core/src/theming/index.ts:L34]` |
| `createGlobal`, `createReset`, `srOnlyStyles` | function/const | Global style helpers | `[AST:code/core/src/theming/index.ts:L36]` |
| `lighten`, `darken`, `getPreferredColorScheme` | function | Color utilities | `[AST:code/core/src/theming/index.ts:L41]` |
| `ignoreSsrWarning` | const | SSR warning suppression string | `[AST:code/core/src/theming/index.ts:L43]` |
| `Theme` | type | Augmented theme type | `[AST:code/core/src/theming/index.ts:L50]` |
| `CSSObject`, `Keyframes` | type | Emotion types, re-exported by `export type { CSSObject, Keyframes } from '@emotion/react'` | `[SRC:code/core/src/theming/index.ts:L21]` |
| `Interpolation`, `FunctionInterpolation`, `StyledComponent` | type | Emotion types with Storybook theme binding (`StyledComponent` from `@emotion/styled`) | `[SRC:code/core/src/theming/index.ts:L25]` `[SRC:code/core/src/theming/index.ts:L8]` |

## storybook/theming/create

Entry: `code/core/src/theming/create.ts`. Used in `.storybook/manager.ts` or `preview.ts` to define a custom theme.

| Export | Kind | Signature | Source |
|---|---|---|---|
| `create` | function | `create = (vars: ThemeVarsPartial = { base: preferredColorScheme }, rest?: Rest): ThemeVars` — build a theme from partial vars; `vars` is optional and defaults to `{ base: preferredColorScheme }` (`'light'` or `'dark'`, as the OS prefers) | `[AST:code/core/src/theming/create.ts:L29]` |
| `themes` | const | `{ light: ThemeVars; dark: ThemeVars; normal: ThemeVars }` — built-in themes | `[AST:code/core/src/theming/create.ts:L20]` |

**Example:**
```ts
// .storybook/theme.ts
import { create } from 'storybook/theming/create';

export default create({
  base: 'light',
  brandTitle: 'My UI Kit',
  brandUrl: 'https://example.com',
  brandImage: 'https://example.com/logo.svg',
});
```

## storybook/actions

Entry: `code/core/src/actions/index.ts`. The `action()` function logs events to the Actions panel.

| Export | Kind | Purpose | Source |
|---|---|---|---|
| `action` | function | `action(name: string, options: ActionOptions = {}): HandlerFunction` — create an action logger for an arg; `options` overrides the global action config for this handler | `[AST:code/core/src/actions/runtime/action.ts:L50]` |
| `configureActions` | function | Global action config (max depth, clearOnStoryChange) | `[AST:code/core/src/actions/runtime/configureActions.ts:L9]` |
| `ActionDisplay`, `ActionsFunction`, `ActionOptions`, `ActionsMap`, `HandlerFunction` | type | Action payload types | `[AST:code/core/src/actions/models/index.ts:L1]` |

**Note:** Prefer `fn()` from `storybook/test` over `action()` in v10 — `fn()` records calls AND allows assertions in `play`. Use `action()` only when the arg is a plain callback with no `play` assertions.

## storybook/actions/decorator

Entry: `code/core/src/actions/decorator.ts`.

| Export | Kind | Purpose | Source |
|---|---|---|---|
| `withActions` | decorator | **Deprecated** — legacy event-handler binding | `[AST:code/core/src/actions/decorator.ts:L59]` |

## storybook/highlight

Entry: `code/core/src/highlight/index.ts`.

| Export | Kind | Purpose | Source |
|---|---|---|---|
| `HIGHLIGHT` | const | Event name — emit to highlight a DOM node | `[AST:code/core/src/highlight/index.ts:L1]` |
| `REMOVE_HIGHLIGHT` | const | Event name — remove a specific highlight | `[AST:code/core/src/highlight/index.ts:L1]` |
| `RESET_HIGHLIGHT` | const | Event name — clear all highlights | `[AST:code/core/src/highlight/index.ts:L1]` |
| `SCROLL_INTO_VIEW` | const | Event name — scroll target into view | `[AST:code/core/src/highlight/index.ts:L1]` |
| `ClickEventDetails`, `HighlightMenuItem`, `HighlightOptions` | type | Event payload types | `[AST:code/core/src/highlight/index.ts:L2]` |

## storybook/viewport

Entry: `code/core/src/viewport/index.ts`. Viewport addon API — responsive viewport definitions, defaults.

| Export | Kind | Purpose | Source |
|---|---|---|---|
| (re-exports) | const/type | Viewport constants, defaults, responsive viewport definitions | `[AST:code/core/src/viewport/index.ts:L1]` |

## storybook/internal/types

Entry: `code/core/src/types/index.ts`. This is the canonical home of the **CSF types** on the core side — though most React authors import them from `@storybook/react-vite` or `@storybook/react`.

**CSF types re-exported from `storybook/internal/csf`:**

| Export | Kind | Source |
|---|---|---|
| `Meta` (via `ComponentAnnotations`) | type | `[AST:code/core/src/types/index.ts]` |
| `StoryObj` (via `StoryAnnotations`) | type | `[AST:code/core/src/types/index.ts]` |
| `StoryFn` | type | `[AST:code/core/src/types/index.ts]` |
| `Decorator` (via `DecoratorFunction`) | type | `[AST:code/core/src/types/index.ts]` |
| `Parameters` | type | `[AST:code/core/src/types/index.ts]` |
| `ArgTypes` | type | `[AST:code/core/src/types/index.ts]` |
| `Args` | type | `[AST:code/core/src/types/index.ts]` |
| `Loader` (via `LoaderFunction`) | type | `[AST:code/core/src/types/index.ts]` |
| `StoryContext` | type | `[AST:code/core/src/types/index.ts]` |
| `PlayFunction` | type | `[AST:code/core/src/types/index.ts]` |
| `ComponentAnnotations` | type | `[AST:code/core/src/types/index.ts]` |
| `StoryAnnotations` | type | `[AST:code/core/src/types/index.ts]` |
| `ProjectAnnotations` (renamed `BaseProjectAnnotations`) | type | `[AST:code/core/src/types/index.ts]` |
| `Canvas` | type | `[AST:code/core/src/types/index.ts]` |
| `Globals` | type | `[AST:code/core/src/types/index.ts]` |

**Additional rendering/runtime types:**

| Export | Kind | Purpose | Source |
|---|---|---|---|
| `ViewMode` | type | `'story' \| 'docs' \| 'settings' \| undefined` | `[AST:code/core/src/types/index.ts]` |
| `StorybookParameters` | interface | Storybook-specific parameters | `[AST:code/core/src/types/index.ts]` |
| `WebRenderer` | interface | Base renderer with `canvasElement` | `[AST:code/core/src/types/index.ts]` |
| `RenderToCanvas` | type | Renderer render function signature | `[AST:code/core/src/types/index.ts]` |
| `CSFFile` | type | Parsed CSF file structure | `[AST:code/core/src/types/index.ts]` |
| `PreparedStory` | type | Story with decorators/loaders applied | `[AST:code/core/src/types/index.ts]` |
| `NormalizedComponentAnnotations`, `NormalizedStoryAnnotations`, `NormalizedProjectAnnotations` | type | Internal normalized forms | `[AST:code/core/src/types/index.ts]` |
| `RenderContext` | type | Renderer context passed to `render` | `[AST:code/core/src/types/index.ts]` |

## storybook/internal/csf

Entry: `code/core/src/csf/index.ts`.

| Export | Kind | Purpose | Source |
|---|---|---|---|
| `toId` | function | `(kind: string, name?: string) => string` — generate a story ID | `[AST:code/core/src/csf/index.ts:L27]` |
| `toTestId` | function | Generate a test ID from a story name | `[AST:code/core/src/csf/index.ts:L31]` |
| `storyNameFromExport` | function | Convert an export name to a readable story name | `[AST:code/core/src/csf/index.ts:L35]` |
| `isExportStory` | function | Check if an export is a valid story (respects `includeStories`/`excludeStories`) | `[AST:code/core/src/csf/index.ts:L51]` |
| `parseKind` | function | Parse a story kind/path | `[AST:code/core/src/csf/index.ts:L69]` |
| `combineTags` | function | Merge and deduplicate story tags | `[AST:code/core/src/csf/index.ts:L81]` |
| `sanitize` | function | Sanitize a story ID string | `[AST:code/core/src/csf/index.ts:L8]` |
| `IncludeExcludeOptions` | interface | Story filtering options | `[AST:code/core/src/csf/index.ts:L38]` |
| `SeparatorOptions` | interface | Story path separators | `[AST:code/core/src/csf/index.ts:L63]` |

## storybook/internal/preview-errors

Entry: `code/core/src/preview-errors.ts`. Preview-side error classes. Catch these to distinguish user errors from Storybook framework issues.

Sample (20+ total): `MissingStoryAfterHmrError`, `ImplicitActionsDuringRendering`, `CalledExtractOnStoreError`, `MissingRenderToCanvasError`, `CalledPreviewMethodBeforeInitializationError`, `StoryIndexFetchError`, `MdxFileWithNoCsfReferencesError`, `EmptyIndexError`, `NoStoryMatchError`, `MissingStoryFromCsfFileError`, `StoryStoreAccessedBeforeInitializationError`, `MountMustBeDestructuredError`, `NoRenderFunctionError`, `NoStoryMountedError`, `StatusTypeIdMismatchError`. All extend `StorybookError`. `[AST:code/core/src/preview-errors.ts:L39-313]`

`Category` enum — error categorization. `[AST:code/core/src/preview-errors.ts:L15]`

## storybook/internal/server-errors

Entry: `code/core/src/server-errors.ts`. Server-side error classes (60+ total) — `NxProjectDetectedError`, `MissingFrameworkFieldError`, `InvalidFrameworkNameError`, and many more. Base class: `StorybookError` from `./storybook-error`. `[AST:code/core/src/server-errors.ts:L8]`

## storybook/internal/components

Entry: `code/core/src/components/index.ts`. UI components used by Storybook's own manager UI and by addon panels, imported when building manager-side addon UI and never in story files. Its source, `code/core/src/components/**`, is outside this skill's scope (the skill brief's `scope.exclude`, amended for GAP-005: addon-panel UI primitives are not story-authoring surface), so its exports are not documented here.

## Infrastructure subpaths (tier C)

These are imported when building **custom addons**, NOT when authoring stories. Listed for completeness. The rows marked "outside this skill's scope" are subpaths whose source the skill brief excludes (`scope.exclude`, GAP-005 amendment): their exports are not documented in this skill.

| Subpath | Purpose | Source |
|---|---|---|
| `storybook/internal/common` | Preset / config helpers (`loadMainConfig`, `normalizeStories`, `getStorybookInfo`) | `[AST:code/core/src/common/index.ts]` |
| `storybook/internal/channels` | Addon channel and transports (source outside this skill's scope) | — |
| `storybook/internal/core-events` | 100+ event constants: `CHANNEL_CREATED`, `STORY_SPECIFIED`, `STORY_PREPARED`, `STORY_RENDERED`, `UPDATE_STORY_ARGS`, `GLOBALS_UPDATED`, `SELECT_STORY`, `PREVIEW_INITIALIZED`, etc., declared in the `events` enum and destructured as `export const { CHANNEL_CREATED, … } = events` | `[SRC:code/core/src/core-events/index.ts:L110]` |
| `storybook/internal/instrumenter` | `instrument()` wraps functions for tracking in `play` | `[AST:code/core/src/instrumenter/index.ts:L1]` |
| `storybook/internal/router` | Router utilities (source outside this skill's scope) | — |
| `storybook/internal/client-logger` | `logger`, `once`, `deprecate`, `pretty` — browser-side logging | `[AST:code/core/src/client-logger/index.ts:L23]` |
| `storybook/internal/node-logger` | Node-side logger and CLI prompt helpers (source outside this skill's scope) | — |
| `storybook/internal/telemetry` | Telemetry collection (source outside this skill's scope) | — |
| `storybook/internal/csf-tools` | CSF and main-config parsing and transforms (source outside this skill's scope) | — |
| `storybook/internal/docs-tools` | ArgTypes utilities, shared docgen helpers | `[AST:code/core/src/docs-tools/index.ts]` |
| `storybook/internal/mocking-utils` | Module-mocking helpers behind `sb.mock`, re-exported with `export *` from six submodules; its exports are listed in `api-index-core.md` | `[AST:code/core/src/mocking-utils/index.ts:L1]` |
| `storybook/internal/core-server` | Dev-server internals (source outside this skill's scope) | — |
| `storybook/internal/cli` | Framework detection, project type detection, ESLint plugin integration | `[AST:code/core/src/cli/index.ts]` |
| `storybook/internal/babel` | Babel and recast re-exports (source outside this skill's scope) | — |
