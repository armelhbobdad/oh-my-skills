# `storybook` Core Package — Full API Reference

The consolidated `storybook` package exposes 40 subpath exports. This reference covers the 28 authoring-surface and type-surface subpaths extracted for v10.3.5. All provenance is T1 — read from source via AST.

## v10 Consolidated Imports Map (all packages in scope)

Every import this skill teaches, grouped by source package and subpath. Column 3 is the canonical v10 import path — **this is the load-bearing part** the skill corrects against training data.

| Import | Kind | From (v10 consolidated) |
|---|---|---|
| `Meta`, `StoryObj`, `StoryFn`, `Decorator`, `Parameters`, `ArgTypes`, `Args`, `StoryContext`, `Loader`, `Preview` | type | `@storybook/react-vite` *(or `@storybook/react`)* `[AST:code/renderers/react/src/public-types.ts:L29]` |
| `StorybookConfig`, `FrameworkOptions` | type | `@storybook/react-vite` `[AST:code/frameworks/react-vite/src/types.ts:L1]` |
| `defineMain` | function | `@storybook/react-vite/node` `[AST:code/frameworks/react-vite/src/node/index.ts:L3]` |
| `expect`, `fn`, `within`, `screen`, `waitFor`, `userEvent`, `fireEvent`, `spyOn` | runtime | `storybook/test` `[AST:code/core/src/test/index.ts:L54]` |
| `useState`, `useArgs`, `useParameter`, `useChannel`, `useEffect`, `useGlobals`, `useCallback`, `useMemo`, `useRef`, `useReducer`, `useStoryContext` | hook | `storybook/preview-api` `[AST:code/core/src/preview-api/index.ts:L5]` |
| `addons`, `makeDecorator`, `mockChannel` | runtime | `storybook/preview-api` `[AST:code/core/src/preview-api/index.ts:L21]` |
| `composeStories`, `composeStory`, `setProjectAnnotations` | runtime | **`@storybook/react-vite`** *(canonical for React+Vite — re-exported from `@storybook/react` where they're defined)* `[AST:code/renderers/react/src/portable-stories.tsx:L148]` |
| `__definePreview` *(CSF4 factory — the double-underscore form is the canonical public export name in `@storybook/react-vite` / `@storybook/react`; `definePreview` is a user-facing alias in the docs but the symbol emitted from the framework package is `__definePreview`)* | runtime | `@storybook/react-vite` `[AST:code/renderers/react/src/preview.tsx:L55]` |
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
- [`storybook/internal/components`](#storybookinternalcomponents) — Addon panel UI components
- [Infrastructure subpaths (tier C)](#infrastructure-subpaths-tier-c) — channels, router, loggers, etc.

## storybook/test

Entry: `code/core/src/test/index.ts`. These are the `play` function utilities — imported anywhere you write assertions or simulate user interactions.

| Export | Kind | Signature / Purpose | Source |
|---|---|---|---|
| `expect` | const | Vitest/Chai-compatible assertion function with full matcher set | `[AST:code/core/src/test/expect.ts:L139]` |
| `fn` | function | `fn<T>(impl?: T): Mock<T>` — create a mock function for `args` | `[AST:code/core/src/test/spy.ts:L48]` |
| `spyOn` | function | `spyOn(obj, method)` — spy on an existing method | `[AST:code/core/src/test/spy.ts]` |
| `within` | function | `within(element)` — scope DOM queries to a subtree | `[AST:code/core/src/test/testing-library.ts:L110]` |
| `screen` | const proxy | Global DOM query object (warns inside docs mode) | `[AST:code/core/src/test/testing-library.ts:L107]` |
| `waitFor` | function | Wait for an async DOM condition | `[AST:code/core/src/test/testing-library.ts:L108]` |
| `fireEvent` | const | Promisified `@testing-library/dom` fireEvent | `[AST:code/core/src/test/testing-library.ts:L43]` |
| `userEvent` | const | Full `@testing-library/user-event` API | `[AST:code/core/src/test/testing-library.ts:L123]` |
| `getByRole` / `findByRole` / `queryByRole` (+ 30 other `*ByText`, `*ByLabelText`, `*ByPlaceholderText`, `*ByTestId` queries) | function | DOM element query helpers | `[AST:code/core/src/test/testing-library.ts:L39-112]` |
| `sb` | const | `{ mock }` — module-level mock utilities | `[AST:code/core/src/test/index.ts:L54]` |
| `Mock`, `MockInstance`, `MaybeMocked` | type | Mock function type helpers | `[AST:code/core/src/test/spy.ts]` |

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
| `composeStory` | function | `composeStory(story, componentAnnotations, projectAnnotations?, exportsName?)` — compose a single story for testing. Generic form with `<TArgs extends Args = Args>` lives at `code/renderers/react/src/portable-stories.tsx:106` — see `story-types.md` "Portable stories utilities" for the full parameterized signature. | `[AST:code/core/src/preview-api/index.ts:L52]` `[AST:code/renderers/react/src/portable-stories.tsx:L106]` |
| `composeStories` | function | `composeStories(csfExports, projectAnnotations?)` — compose all stories from a CSF module | `[AST:code/core/src/preview-api/index.ts:L51]` |
| `setProjectAnnotations` | function | Set global project annotations for portable stories (call once in test setup) | `[AST:code/core/src/preview-api/index.ts:L46]` |
| `definePreview` | function | Define a typed preview (CSF factory API) | `[AST:code/core/src/preview-api/index.ts]` |
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
| `mocked` | function | `(item: T, options?: { partial?: boolean; deep?: boolean }) => MaybeMocked<T>` — TS type assertion helper | `[AST:code/core/src/test/spy.ts:L119]` |
| `mocks` | const | `typeof mocks` — re-exported from `@vitest/spy`, set of active mocks | `[AST:code/core/src/test/spy.ts:L17]` |

## storybook/manager-api

Entry: `code/core/src/manager-api/index.ts`. Used when writing a **manager-side** addon (addon panels, toolbar buttons, sidebar items). Not needed for story authoring.

| Export | Kind | Purpose | Source |
|---|---|---|---|
| (re-exports `./root`) | — | Full addon manager API: story selection, notifications, refs, globals, settings | `[AST:code/core/src/manager-api/index.ts]` |
| `experimental_UniversalStore` | class | Cross-environment state store | `[AST:code/core/src/manager-api/index.ts:L3]` |
| `useUniversalStore` | hook | Access universal store in manager components | `[AST:code/core/src/manager-api/index.ts:L4]` |
| `MockUniversalStore` | class | Mock store for tests | `[AST:code/core/src/manager-api/index.ts:L5]` |
| `useStatusStore`, `experimental_getStatusStore` | hook/func | Status store access (panel badges, test results) | `[AST:code/core/src/manager-api/index.ts:L7]` |
| `useTestProviderStore`, `experimental_getTestProviderStore` | hook/func | Test provider state (addon-vitest) | `[AST:code/core/src/manager-api/index.ts:L14]` |
| `Tag` | enum | Story tagging system | `[AST:code/core/src/manager-api/index.ts:L26]` |

## storybook/theming

Entry: `code/core/src/theming/index.ts`. Emotion-based styling used by Storybook's UI and addon panels.

| Export | Kind | Purpose | Source |
|---|---|---|---|
| `styled` | const | Emotion `styled` — `styled.div\`...\`` | `[AST:code/core/src/theming/index.ts:L6]` |
| `css` | function | Emotion `css` tagged template | `[AST:code/core/src/theming/index.ts:L10]` |
| `keyframes` | function | Emotion `keyframes` for animations | `[AST:code/core/src/theming/index.ts:L10]` |
| `Global` | component | Emotion `Global` styles | `[AST:code/core/src/theming/index.ts:L10]` |
| `ThemeProvider` | component | Emotion `ThemeProvider` with Storybook theme type | `[AST:code/core/src/theming/index.ts:L10]` |
| `useTheme` | hook | Access current theme | `[AST:code/core/src/theming/index.ts:L10]` |
| `withTheme` | HOC | HOC wrapper for class components | `[AST:code/core/src/theming/index.ts:L10]` |
| `jsx` | function | Emotion JSX runtime | `[AST:code/core/src/theming/index.ts:L10]` |
| `CacheProvider`, `ClassNames` | component | Emotion cache/classnames | `[AST:code/core/src/theming/index.ts:L10]` |
| `createCache` | function | Create an emotion cache | `[AST:code/core/src/theming/index.ts:L33]` |
| `isPropValid` | function | `@emotion/is-prop-valid` filter | `[AST:code/core/src/theming/index.ts:L34]` |
| `createGlobal`, `createReset`, `srOnlyStyles` | function/const | Global style helpers | `[AST:code/core/src/theming/index.ts:L36]` |
| `lighten`, `darken`, `getPreferredColorScheme` | function | Color utilities | `[AST:code/core/src/theming/index.ts:L41]` |
| `ignoreSsrWarning` | const | SSR warning suppression string | `[AST:code/core/src/theming/index.ts:L43]` |
| `Theme` | type | Augmented theme type | `[AST:code/core/src/theming/index.ts:L50]` |
| `CSSObject`, `Keyframes`, `Interpolation`, `FunctionInterpolation`, `StyledComponent` | type | Emotion types with Storybook theme binding | `[AST:code/core/src/theming/index.ts:L21-28]` |

## storybook/theming/create

Entry: `code/core/src/theming/create.ts`. Used in `.storybook/manager.ts` or `preview.ts` to define a custom theme.

| Export | Kind | Signature | Source |
|---|---|---|---|
| `create` | function | `create(vars: ThemeVarsPartial, rest?: Rest): ThemeVars` — build a theme from partial vars | `[AST:code/core/src/theming/create.ts:L29]` |
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
| `action` | function | `action(name: string)` — create an action logger for an arg | `[AST:code/core/src/actions/runtime/action.ts]` |
| `configureActions` | function | Global action config (max depth, clearOnStoryChange) | `[AST:code/core/src/actions/runtime/configureActions.ts]` |
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

Entry: `code/core/src/components/index.ts`. **80+ UI components** used by Storybook's own manager UI and by addon panels. Imported when building manager-side addon UI. Never imported in story files.

Categories:
- **Typography:** `A`, `Blockquote`, `Code`, `Div`, `H1`–`H6`, `HR`, `P`, `Pre`, `Span`, `Table`, `UL`, `OL`, `LI`, `DL`, `Badge`
- **UI controls:** `Button`, `IconButton`, `ToggleButton`, `Select`, `Form`
- **Panels:** `AddonPanel`, `Card`, `Modal`, `Collapsible`, `ScrollArea`
- **Tabs system:** `Tabs`, `TabBar`, `TabButton`, `TabWrapper`, `TabList`, `TabPanel`, `TabsView`, `useTabsState`
- **Overlays:** `Popover`, `PopoverProvider`, `Tooltip`, `TooltipNote`, `WithTooltip`, `TooltipLinkList`
- **Bars:** `Bar`, `FlexBar`, `Toolbar`, `ActionBar`, `ActionList`
- **Utilities:** `ErrorFormatter`, `SyntaxHighlighter`, `Placeholder`, `Zoom`, `Spaced`, `getStoryHref`
- **Brand:** `StorybookLogo`, `StorybookIcon`

`[AST:code/core/src/components/index.ts:L1]`

## Infrastructure subpaths (tier C)

These are imported when building **custom addons**, NOT when authoring stories. Listed for completeness:

| Subpath | Purpose | Source |
|---|---|---|
| `storybook/internal/common` | Preset / config helpers (`loadMainConfig`, `normalizeStories`, `getStorybookInfo`) | `[AST:code/core/src/common/index.ts]` |
| `storybook/internal/channels` | `Channel`, `PostMessageTransport`, `WebsocketTransport`, `createBrowserChannel` | `[AST:code/core/src/channels/index.ts:L5]` |
| `storybook/internal/core-events` | 100+ event constants: `CHANNEL_CREATED`, `STORY_SPECIFIED`, `STORY_PREPARED`, `STORY_RENDERED`, `UPDATE_STORY_ARGS`, `GLOBALS_UPDATED`, `SELECT_STORY`, `PREVIEW_INITIALIZED`, etc. | `[AST:code/core/src/core-events/index.ts]` |
| `storybook/internal/instrumenter` | `instrument()` wraps functions for tracking in `play` | `[AST:code/core/src/instrumenter/index.ts:L1]` |
| `storybook/internal/router` | Router utilities | `[AST:code/core/src/router/index.ts]` |
| `storybook/internal/client-logger` | `logger`, `once`, `deprecate`, `pretty` — browser-side logging | `[AST:code/core/src/client-logger/index.ts:L23]` |
| `storybook/internal/node-logger` | Node-side logger + CLI helpers (`prompt`, `logTracker`, `colors`) | `[AST:code/core/src/node-logger/index.ts:L67]` |
| `storybook/internal/telemetry` | `telemetry`, `getStorybookMetadata`, `getSessionId`, `addToGlobalContext` | `[AST:code/core/src/telemetry/index.ts:L31]` |
| `storybook/internal/csf-tools` | `CsfFile`, `ConfigFile`, `babelParse`, `enrichCsf`, `getStorySortParameter`, `vitestTransform`, `componentTransform` | `[AST:code/core/src/csf-tools/index.ts:L1]` |
| `storybook/internal/docs-tools` | ArgTypes utilities, shared docgen helpers | `[AST:code/core/src/docs-tools/index.ts]` |
| `storybook/internal/mocking-utils` | `automock`, `extract`, `resolve`, `esmWalker`, `runtime`, `redirect` | `[AST:code/core/src/mocking-utils/index.ts:L1]` |
| `storybook/internal/core-server` | `StoryIndexGenerator`, `generateStoryFile`, `experimental_loadStorybook`, `getPreviewHeadTemplate`, `getPreviewBodyTemplate` | `[AST:code/core/src/core-server/index.ts:L3]` |
| `storybook/internal/cli` | Framework detection, project type detection, ESLint plugin integration | `[AST:code/core/src/cli/index.ts]` |
| `storybook/internal/babel` | Babel core (`core`, `generate`, `traverse`, `types`, `parser`, `transformSync`), `recast`, `BabelFile`, `NodePath` | `[AST:code/core/src/babel/index.ts:L35]` |
