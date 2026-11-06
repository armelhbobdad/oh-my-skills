# `storybook` Core Package — Full API Reference

The consolidated `storybook` package exposes 40 subpath exports. This reference covers the 28 authoring-surface and type-surface subpaths extracted for v10.3.5. Source citations point at the pinned source: `[AST:]` at a line SKF's ast-grep extractor records, `[SRC:]` at one read by eye. The `storybook/test` bindings made by destructuring (`expect`, and every Testing Library query and helper) have no extractor record and cite `[SRC:]`, as do the entry files' module-level lines and the infrastructure subpaths outside the extraction scope; the Testing Library signatures are `@testing-library/dom`'s own types (`[EXT:]`).

## v10 Consolidated Imports Map (all packages in scope)

Every import this skill teaches, grouped by source package and subpath. Column 3 is the canonical v10 import path — **this is the load-bearing part** the skill corrects against training data.

| Import | Kind | From (v10 consolidated) |
|---|---|---|
| `Meta`, `StoryObj`, `StoryFn`, `Decorator`, `ArgTypes`, `StoryContext`, `Loader`, `Preview` | type | `@storybook/react-vite` *(or `@storybook/react`)* `[AST:code/renderers/react/src/public-types.ts:L29]` `[AST:code/renderers/react/src/public-types.ts:L47]` `[AST:code/renderers/react/src/public-types.ts:L38]` `[AST:code/renderers/react/src/public-types.ts:L77]` `[AST:code/renderers/react/src/public-types.ts:L21]` `[AST:code/core/src/csf/story.ts:L162]` `[AST:code/renderers/react/src/public-types.ts:L79]` `[AST:code/renderers/react/src/public-types.ts:L78]` `[AST:code/renderers/react/src/public-types.ts:L80]` |
| `Parameters`, `Args` | interface | `@storybook/react-vite` *(or `@storybook/react`)*, which re-exports them from `storybook/internal/types` `[AST:code/renderers/react/src/public-types.ts:L21]` `[AST:code/core/src/csf/story.ts:L32]` `[AST:code/core/src/csf/story.ts:L153]` |
| `StorybookConfig`, `FrameworkOptions` | type | `@storybook/react-vite` `[AST:code/frameworks/react-vite/src/types.ts:L66]` `[AST:code/frameworks/react-vite/src/types.ts:L14]` |
| `defineMain` | function | `@storybook/react-vite/node` `[AST:code/frameworks/react-vite/src/node/index.ts:L3]` |
| `expect`, `fn`, `within`, `screen`, `waitFor`, `userEvent`, `fireEvent`, `spyOn` | runtime | `storybook/test` `[SRC:code/core/src/test/index.ts:L24]` `[AST:code/core/src/test/spy.ts:L48]` `[SRC:code/core/src/test/testing-library.ts:L110]` `[SRC:code/core/src/test/testing-library.ts:L107]` `[SRC:code/core/src/test/testing-library.ts:L108]` `[SRC:code/core/src/test/testing-library.ts:L123]` `[SRC:code/core/src/test/testing-library.ts:L43]` `[AST:code/core/src/test/spy.ts:L41]` |
| `useState`, `useArgs`, `useParameter`, `useChannel`, `useEffect`, `useGlobals`, `useCallback`, `useMemo`, `useRef`, `useReducer`, `useStoryContext` | hook | `storybook/preview-api` `[AST:code/core/src/preview-api/index.ts:L5]` |
| `addons`, `makeDecorator`, `mockChannel` | runtime | `storybook/preview-api` `[AST:code/core/src/preview-api/index.ts:L21]` |
| `composeStories`, `composeStory`, `setProjectAnnotations` | runtime | **`@storybook/react-vite`** *(canonical for React+Vite — re-exported from `@storybook/react` where they're defined)* `[AST:code/renderers/react/src/portable-stories.tsx:L148]` `[AST:code/renderers/react/src/portable-stories.tsx:L106]` `[AST:code/renderers/react/src/portable-stories.tsx:L46]` |
| `definePreview` / `__definePreview` *(CSF4 factory — `@storybook/react-vite` exports `definePreview`, its alias for the renderer's `__definePreview`, and `__definePreview` itself through `export *`; `@storybook/react` exports only `__definePreview`. `storybook/preview-api` exports neither)* | runtime | `@storybook/react-vite` `[AST:code/frameworks/react-vite/src/index.ts:L2]` `[AST:code/renderers/react/src/preview.tsx:L55]` |
| `action` | runtime | `storybook/actions` `[AST:code/core/src/actions/runtime/action.ts:L50]` |
| `create`, `themes`, `styled`, `css`, `useTheme`, `ThemeProvider` | runtime | `storybook/theming` / `storybook/theming/create` `[AST:code/core/src/theming/create.ts:L29]` |
| `HIGHLIGHT`, `RESET_HIGHLIGHT` | const | `storybook/highlight` `[AST:code/core/src/highlight/index.ts:L1]` |
| `Canvas`, `Meta`, `Controls`, `Primary`, `Stories`, `Story`, `ArgTypes`, `Source`, `Description`, `Title`, `Markdown`, `Typeset`, `ColorPalette`, `IconGallery`, `Unstyled`, `DocsContainer`, `DocsPage` | component (MDX block) | `@storybook/addon-docs/blocks` `[SRC:code/addons/docs/src/blocks.ts:L8]`, each block at its declaration, in this order: `[AST:code/addons/docs/src/blocks/blocks/Canvas.tsx:L100]` `[AST:code/addons/docs/src/blocks/blocks/Meta.tsx:L15]` `[AST:code/addons/docs/src/blocks/blocks/Controls.tsx:L109]` `[AST:code/addons/docs/src/blocks/blocks/Primary.tsx:L16]` `[AST:code/addons/docs/src/blocks/blocks/Stories.tsx:L74]` `[AST:code/addons/docs/src/blocks/blocks/Story.tsx:L134]` `[AST:code/addons/docs/src/blocks/blocks/ArgTypes.tsx:L108]` `[AST:code/addons/docs/src/blocks/blocks/Source.tsx:L181]` `[AST:code/addons/docs/src/blocks/blocks/Description.tsx:L74]` `[AST:code/addons/docs/src/blocks/blocks/Title.tsx:L55]` `[AST:code/addons/docs/src/blocks/blocks/Markdown.tsx:L55]` `[AST:code/addons/docs/src/blocks/components/Typeset.tsx:L50]` `[AST:code/addons/docs/src/blocks/components/ColorPalette.tsx:L202]` `[AST:code/addons/docs/src/blocks/components/IconGallery.tsx:L74]` `[AST:code/addons/docs/src/blocks/blocks/Unstyled.tsx:L9]` `[AST:code/addons/docs/src/blocks/blocks/DocsContainer.tsx:L23]` `[AST:code/addons/docs/src/blocks/blocks/DocsPage.tsx:L12]` |
| `useOf` | hook | `@storybook/addon-docs/blocks` `[AST:code/addons/docs/src/blocks/blocks/useOf.ts:L18]` |
| `withThemeByClassName`, `withThemeByDataAttribute`, `withThemeFromJSXProvider` | function | `@storybook/addon-themes` `[AST:code/addons/themes/src/decorators/class-name.decorator.tsx:L19]` `[AST:code/addons/themes/src/decorators/data-attribute.decorator.tsx:L19]` `[AST:code/addons/themes/src/decorators/provider.decorator.tsx:L23]` |
| a11y `parameters: { a11y: { test: ... } }`, runtime `afterEach`, `decorators`, `initialGlobals` | param + runtime | `@storybook/addon-a11y` / `@storybook/addon-a11y/preview` — the runtime `afterEach(context)` runs axe-core per story and attaches an `A11yReport` to `context.reporting`; compose it manually in your `preview.ts` only when you need multiple `afterEach` hooks `[AST:code/addons/a11y/src/preview.tsx:L14]` |

The rest of this file documents each `storybook/*` subpath in detail. CSF types live in `story-types.md`; MDX blocks in `doc-blocks.md`; addon exports in `addons.md`; framework/renderer/builder layer in `framework-config.md`.

## Contents

- [`storybook/test`](#storybooktest) — Test utilities for `play` functions; every Testing Library query and helper is in [Testing Library queries and helpers](#testing-library-queries-and-helpers-storybooktest)
- [`storybook/preview-api`](#storybookpreview-api) — Hooks, decorators, portable stories, and the CSF, rendering and story-store helpers
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
| `expect` | const | Vitest/Chai-compatible assertion function with full matcher set: the instrumented copy `test/index.ts` makes of `expect.ts`'s `expect` | `[SRC:code/core/src/test/index.ts:L24]` |
| `fn` | function | `fn<T>(implementation?: T): Mock<T>` — create a mock function for `args` | `[AST:code/core/src/test/spy.ts:L48]` |
| `spyOn` | function | Declared `spyOn: typeof vitestSpyOn` (`@vitest/spy` 3.2.4), so it has vitest's overloads and return types: `spyOn(obj: T, methodName: M)` for a method or class, `spyOn(obj: T, methodName: S, accessType: 'get')` for a getter and `spyOn(obj: T, methodName: G, accessType: 'set')` for a setter — spy on an existing member | `[AST:code/core/src/test/spy.ts:L41]` |
| `within` | function | `within(element)` — scope DOM queries to a subtree | `[SRC:code/core/src/test/testing-library.ts:L110]` |
| `screen` | const proxy | Global DOM query object (warns inside docs mode) | `[SRC:code/core/src/test/testing-library.ts:L107]` |
| `waitFor` | function | Wait for an async DOM condition | `[SRC:code/core/src/test/testing-library.ts:L108]` |
| `fireEvent` | const | Promisified `@testing-library/dom` fireEvent | `[SRC:code/core/src/test/testing-library.ts:L43]` |
| `userEvent` | const | Full `@testing-library/user-event` API | `[SRC:code/core/src/test/testing-library.ts:L123]` |
| `getByRole` / `findByRole` / `queryByRole` (and the 45 other `getBy*`, `getAllBy*`, `queryBy*`, `queryAllBy*`, `findBy*` and `findAllBy*` queries) | function | DOM element query helpers, each taking the `container` element first: every query, with its signature, is in [Testing Library queries and helpers](#testing-library-queries-and-helpers-storybooktest) below | `[SRC:code/core/src/test/testing-library.ts:L39-112]` |
| `sb` | const | `{ mock }` — module-level mock utilities | `[AST:code/core/src/test/index.ts:L54]` |
| `Mock` | interface | `Mock<T extends Procedure = Procedure>`, which extends `MockInstance<T>` and is callable, and constructible with `new`, with the parameters of `T`, returning its `ReturnType`: the type `fn` returns. This row's type and the five below are `@vitest/spy` 3.2.4's, which `spy.ts` re-exports with `export type * from '@vitest/spy'` (with that package's other exported types); `Procedure` is that package's `(...args: any[]) => any`, which it does not export | `[SRC:code/core/src/test/spy.ts:L15]` `[SRC:code/core/src/test/spy.ts:L1]` `[EXT:https://unpkg.com/@vitest/spy@3.2.4/dist/index.d.ts]` |
| `MockInstance` | interface | `MockInstance<T extends Procedure = Procedure>`, which extends `Disposable`: the API of a mock (`mock`, `getMockName`, `mockName`, `mockClear`, `mockReset`, `mockRestore`, `getMockImplementation`, `mockImplementation`, `mockImplementationOnce`, `withImplementation`, `mockReturnThis`, `mockReturnValue`, `mockReturnValueOnce`, `mockResolvedValue`, `mockResolvedValueOnce`, `mockRejectedValue`, `mockRejectedValueOnce`); `spyOn` returns one | `[SRC:code/core/src/test/spy.ts:L15]` `[SRC:code/core/src/test/spy.ts:L1]` `[EXT:https://unpkg.com/@vitest/spy@3.2.4/dist/index.d.ts]` |
| `MaybeMocked` | type | `MaybeMocked<T> = T extends Procedure ? MockedFunction<T> : T extends object ? MockedObject<T> : T`: `T` typed as mocked one level deep, which `mocked` returns by default | `[SRC:code/core/src/test/spy.ts:L15]` `[SRC:code/core/src/test/spy.ts:L3]` `[EXT:https://unpkg.com/@vitest/spy@3.2.4/dist/index.d.ts]` |
| `MaybeMockedDeep` | type | `MaybeMockedDeep<T> = T extends Procedure ? MockedFunctionDeep<T> : T extends object ? MockedObjectDeep<T> : T`: `T` typed as mocked at every level, which `mocked` returns when `deep` is `true` | `[SRC:code/core/src/test/spy.ts:L15]` `[SRC:code/core/src/test/spy.ts:L4]` `[EXT:https://unpkg.com/@vitest/spy@3.2.4/dist/index.d.ts]` |
| `MaybePartiallyMocked` | type | `MaybePartiallyMocked<T> = T extends Procedure ? PartiallyMockedFunction<T> : T extends object ? MockedObject<T> : T`: like `MaybeMocked`, but a mocked function may return a `Partial` of its return type, which `mocked` returns when `partial` is `true` | `[SRC:code/core/src/test/spy.ts:L15]` `[SRC:code/core/src/test/spy.ts:L5]` `[EXT:https://unpkg.com/@vitest/spy@3.2.4/dist/index.d.ts]` |
| `MaybePartiallyMockedDeep` | type | `MaybePartiallyMockedDeep<T> = T extends Procedure ? PartiallyMockedFunctionDeep<T> : T extends object ? MockedObjectDeep<T> : T`: the deep form of `MaybePartiallyMocked`, which `mocked` returns when `partial` and `deep` are both `true` | `[SRC:code/core/src/test/spy.ts:L15]` `[SRC:code/core/src/test/spy.ts:L6]` `[EXT:https://unpkg.com/@vitest/spy@3.2.4/dist/index.d.ts]` |

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
| `useArgs` | hook | `[args, updateArgs, resetArgs]` — read/write current story args | `[AST:code/core/src/preview-api/index.ts:L5]` `[AST:code/core/src/preview-api/modules/addons/hooks.ts:L614]` |
| `useParameter` | hook | `useParameter<S>(parameterKey: string, defaultValue?: S): S \| undefined` — read the current story's `parameters[parameterKey]`, falling back to `defaultValue` | `[AST:code/core/src/preview-api/modules/addons/hooks.ts:L590]` `[AST:code/core/src/preview-api/index.ts:L11]` |
| `useGlobals` | hook | `[globals, updateGlobals]` — read/write globals (theme, locale) | `[AST:code/core/src/preview-api/index.ts:L9]` `[AST:code/core/src/preview-api/modules/addons/hooks.ts:L649]` |
| `useChannel` | hook | Subscribe to addon events | `[AST:code/core/src/preview-api/index.ts:L7]` `[AST:code/core/src/preview-api/modules/addons/hooks.ts:L530]` |
| `useStoryContext` | hook | Full story context object | `[AST:code/core/src/preview-api/index.ts:L15]` |

**Decorators, addons, and portable stories:**

| Export | Kind | Purpose | Source |
|---|---|---|---|
| `makeDecorator` | function | Create a reusable addon decorator | `[AST:code/core/src/preview-api/index.ts:L21]` |
| `applyHooks` | function | Apply a hooks context (experimental) | `[AST:code/core/src/preview-api/index.ts:L16]` |
| `addons` | const | Singleton `AddonStore` — register addon types, channels | `[AST:code/core/src/preview-api/index.ts:L28]` `[AST:code/core/src/preview-api/modules/addons/main.ts:L51]` |
| `mockChannel` | function | Create a mock channel for unit tests | `[AST:code/core/src/preview-api/index.ts:L28]` |
| `composeStory` | function | Core's renderer-agnostic form: `composeStory<TRenderer extends Renderer = Renderer, TArgs extends Args = Args>(storyAnnotations: LegacyStoryAnnotationsOrFn<TRenderer>, componentAnnotations: ComponentAnnotations<TRenderer, TArgs>, projectAnnotations?: ProjectAnnotations<TRenderer>, defaultConfig?: ProjectAnnotations<TRenderer>, exportsName?: string): ComposedStoryFn<TRenderer, Partial<TArgs>>`. `exportsName` is the fifth parameter here (the fourth binds to `defaultConfig`). Story authors on React+Vite import the four-parameter React wrapper from `@storybook/react-vite` instead; see `story-types.md` "Portable stories utilities". | `[AST:code/core/src/preview-api/modules/store/csf/portable-stories.ts:L90]` `[AST:code/core/src/preview-api/index.ts:L52]` |
| `composeStories` | function | Core's renderer-agnostic form: `composeStories<TModule extends Store_CSFExports>(storiesImport: TModule, globalConfig: ProjectAnnotations<Renderer>, composeStoryFn: ComposeStoryFn = defaultComposeStory)`, with `globalConfig` required and no annotated return type. Story authors on React+Vite import `composeStories(csfExports, projectAnnotations?)` from `@storybook/react-vite` instead; see `story-types.md` "Portable stories utilities". | `[AST:code/core/src/preview-api/modules/store/csf/portable-stories.ts:L274]` `[AST:code/core/src/preview-api/index.ts:L51]` |
| `setProjectAnnotations` | function | Core's renderer-agnostic form: set global project annotations for portable stories (call once in test setup). Story authors on React+Vite import the React one from `@storybook/react-vite` (`story-types.md`) | `[AST:code/core/src/preview-api/index.ts:L62]` `[AST:code/core/src/preview-api/modules/store/csf/portable-stories.ts:L73]` |
| `decorateStory`, `defaultDecorateStory`, `combineArgs`, `combineParameters`, `composeConfigs`, `composeStepRunners`, `normalizeArrays`, `normalizeStory`, `normalizeProjectAnnotations`, `prepareStory`, `prepareMeta`, `filterArgTypes`, `sanitizeStoryContextUpdate`, `setDefaultProjectAnnotations`, `inferControls`, `userOrAutoTitleFromSpecifier`, `userOrAutoTitle`, `sortStoriesV7` | function | Internal composition utilities (rarely imported by authors) | `[AST:code/core/src/preview-api/index.ts:L47-67]` |
| `HooksContext` | class | `HooksContext<TRenderer extends Renderer, TArgs extends Args = Args>`: the hook state of one story (its hook lists per decorator, the current phase and the pending effects), which `applyHooks` drives; the `StoryStore` keeps one per story | `[AST:code/core/src/preview-api/modules/addons/hooks.ts:L36]` `[AST:code/core/src/preview-api/index.ts:L17]` |
| `DocsContext` | class | `DocsContext<TRenderer extends Renderer>`, which implements `DocsContextProps<TRenderer>`: the context a docs entry renders with (it resolves `of` references to the CSF files and stories the entry attaches). The preview creates one per docs render; this is not the React context of the same name that `@storybook/addon-docs/blocks` exports (`doc-blocks.md`), which holds it | `[AST:code/core/src/preview-api/modules/preview-web/docs-context/DocsContext.ts:L20]` `[AST:code/core/src/preview-api/index.ts:L41]` |
| `Preview`, `PreviewWeb`, `PreviewWithSelection`, `StoryStore`, `UrlStore`, `WebView` | class | Preview runtime classes (internal). **Not to be confused with the `Preview` type** exported by `@storybook/react-vite` / `@storybook/react` (which is `ProjectAnnotations<ReactRenderer>` — the `.storybook/preview.ts` default-export shape). `Preview<TRenderer extends Renderer>` is the base runtime class; `PreviewWithSelection<TRenderer>` extends it with a `SelectionStore` and a `View`; `PreviewWeb<TRenderer>` extends `PreviewWithSelection`, passing it a `new UrlStore()` and a `new WebView()`, and sets itself as `global.__STORYBOOK_PREVIEW__`. `StoryStore<TRenderer>` holds the project annotations, the loaded CSF files and the prepared stories; `UrlStore` implements `SelectionStore` over the URL; `WebView` implements `View<HTMLElement>`. | `[AST:code/core/src/preview-api/modules/preview-web/Preview.tsx:L60]` `[AST:code/core/src/preview-api/modules/preview-web/PreviewWeb.tsx:L11]` `[AST:code/core/src/preview-api/modules/preview-web/PreviewWithSelection.tsx:L77]` `[AST:code/core/src/preview-api/modules/store/StoryStore.ts:L51]` `[AST:code/core/src/preview-api/modules/preview-web/UrlStore.ts:L94]` `[AST:code/core/src/preview-api/modules/preview-web/WebView.ts:L42]` |

**Migration note:** `setProjectAnnotations` was expanded to more renderers/frameworks in PR #28907. `[QMD:oms-storybook-react-vite-temporal:changelog.md #5defd6]`

### Preview-API composition utilities (declared locations)

The re-export table above lists the public surface; the rows below pin each symbol to its **actual declaration file** so you can step into source when a signature disagrees with the re-export row. Useful to portable-stories authors, test-harness maintainers, and anyone writing a custom preview runtime.

| Export | Kind | Signature | Source |
|---|---|---|---|
| `combineArgs` | function | `(value: any, update: any) => Args` — deep-merge two args objects | `[AST:code/core/src/preview-api/modules/store/args.ts:L84]` |
| `combineParameters` | function | `(...parameterSets: (Parameters \| undefined)[]) => Parameters` — recursively merge parameter bags preserving plain objects | `[AST:code/core/src/preview-api/modules/store/parameters.ts:L11]` |
| `composeConfigs` | function | `<R extends Renderer>(moduleExportList: ModuleExports[]) => NormalizedProjectAnnotations<R>` — fold config modules into a single normalized ProjectAnnotations | `[AST:code/core/src/preview-api/modules/store/csf/composeConfigs.ts:L43]` |
| `composeStepRunners` | function | `<R>(stepRunners: StepRunner<R>[]) => StepRunner<R>` — sequence step runners into one | `[AST:code/core/src/preview-api/modules/store/csf/stepRunners.ts:L27]` |
| `filterArgTypes` | function | `(argTypes: StrictArgTypes, include?: PropDescriptor, exclude?: PropDescriptor) => StrictArgTypes \| Partial<StrictArgTypes>` (return type not annotated, inferred) — returns `argTypes` itself when neither `include` nor `exclude` is given, else `argTypes && pickBy(argTypes, ...)` (es-toolkit, typed `Partial<T>`), keeping each arg type whose `name` (or key) matches `include` and not `exclude`; `PropDescriptor = string[] \| RegExp` | `[AST:code/core/src/preview-api/modules/store/filterArgTypes.ts:L10]` |
| `PropDescriptor` | type | `string[] \| RegExp`: what `filterArgTypes` takes as `include` and `exclude`, the arg names to keep or drop, or a pattern their names are matched against. `storybook/preview-api` exports it type-only (`export type { PropDescriptor }`), and the `Controls` and `ArgTypes` doc blocks type their `include` and `exclude` props with it | `[AST:code/core/src/preview-api/modules/store/filterArgTypes.ts:L5]` `[AST:code/core/src/preview-api/index.ts:L73]` |
| `inferControls` | function | `ArgTypesEnhancer<Renderer>` — auto-pick control types from runtime arg values + matchers | `[AST:code/core/src/preview-api/modules/store/inferControls.ts:L66]` |
| `normalizeStory` | function | `<R>(key: StoryId, storyAnnotations: StoryAnnotationsOrFn<R>, meta: NormalizedComponentAnnotations<R>) => NormalizedStoryAnnotations<R>` | `[AST:code/core/src/preview-api/modules/store/csf/normalizeStory.ts:L25]` |
| `normalizeArrays` | function | `<T>(array: T[] \| T \| undefined) => T[]` — coerce single/undefined to array | `[AST:code/core/src/preview-api/modules/store/csf/normalizeArrays.ts:L1]` |
| `normalizeProjectAnnotations` | function | `<TRenderer extends Renderer>({ argTypes, argTypesEnhancers, decorators, loaders, beforeEach, afterEach, initialGlobals, ...annotations }: ProjectAnnotations<TRenderer>) => NormalizedProjectAnnotations<TRenderer>` — normalizes `argTypes`, turns `decorators`, `loaders`, `beforeEach` and `afterEach` into arrays, appends the built-in arg-type enhancers (`inferArgTypes`, `inferControls`) to `argTypesEnhancers`, and keeps the rest | `[AST:code/core/src/preview-api/modules/store/csf/normalizeProjectAnnotations.ts:L17]` |
| `prepareStory` | function | `<R>(storyAnnotations, componentAnnotations, projectAnnotations) => PreparedStory<R>` — merge annotations + wire decorators/loaders/hooks | `[AST:code/core/src/preview-api/modules/store/csf/prepareStory.ts:L37]` |
| `prepareMeta` | function | `<R>(componentAnnotations, projectAnnotations, moduleExport) => PreparedMeta<R>` — component-level prep step | `[AST:code/core/src/preview-api/modules/store/csf/prepareStory.ts:L171]` |
| `sanitizeStoryContextUpdate` | function | `({ componentId, title, kind, id, name, story, parameters, initialArgs, argTypes, ...update }: StoryContextUpdate = {}) => StoryContextUpdate` — returns `update`, the context update without those nine keys, which a decorator may not overwrite | `[AST:code/core/src/preview-api/modules/store/decorators.ts:L30]` |
| `sortStoriesV7` | function | `(stories, storySortParameter, fileNameOrder) => IndexEntry[]` — apply `parameters.options.storySort` | `[AST:code/core/src/preview-api/modules/store/sortStories.ts:L37]` |
| `defaultDecorateStory` | function | `<R>(storyFn: LegacyStoryFn<R>, decorators: DecoratorFunction<R>[]) => LegacyStoryFn<R>` — chain decorators with context binding | `[AST:code/core/src/preview-api/modules/store/decorators.ts:L49]` |
| `decorateStory` | function | `<R>(storyFn, decorator, bindWithContext) => LegacyStoryFn<R>` — single-decorator variant | `[AST:code/core/src/preview-api/modules/store/decorators.ts:L10]` |
| `applyHooks` | function | `<R>(applyDecorators: DecoratorApplicator<R>) => DecoratorApplicator<R>` — wrap decorator applicator with hooks runtime | `[AST:code/core/src/preview-api/modules/addons/hooks.ts:L184]` |
| `mockChannel` | function | `() => Channel` — create a mock addon channel for tests | `[AST:code/core/src/preview-api/modules/addons/storybook-channel-mock.ts:L3]` |

### Preview-API CSF, rendering and story-store helpers (declared locations)

`storybook/preview-api` re-exports these from its entry: `simulatePageLoad` and `simulateDOMContentLoaded` under its simulation API, `createPlaywrightTest` and `getCsfFactoryAnnotations` under its CSF API, and the rest under its stories API (`StoryStore`, `Report` and `ReporterAPI`, then the preview-web exports, with `SelectionStore` and `View` as types) `[SRC:code/core/src/preview-api/index.ts:L44]` `[SRC:code/core/src/preview-api/index.ts:L71]` `[SRC:code/core/src/preview-api/index.ts:L78]` `[SRC:code/core/src/preview-api/index.ts:L89]`. Each row cites the declaration.

| Export | Kind | Signature | Source |
|---|---|---|---|
| `createPlaywrightTest` | function | `createPlaywrightTest<TFixture extends { extend: any }>(baseTest: TFixture): TFixture` — returns `baseTest.extend(...)` with a `mount` fixture that takes a story reference, and throws unless that reference is a JSX element (portable stories in Playwright CT). `@storybook/react/experimental-playwright` re-exports it as `createTest` (`framework-config.md`) | `[AST:code/core/src/preview-api/modules/store/csf/portable-stories.ts:L319]` |
| `getCsfFactoryAnnotations` | function | `getCsfFactoryAnnotations<TRenderer extends Renderer = Renderer, TArgs extends Args = Args>(story: LegacyStoryAnnotationsOrFn<TRenderer> \| Story<Renderer>, meta?: ComponentAnnotations<TRenderer, TArgs> \| Meta<Renderer>, projectAnnotations?: ProjectAnnotations<TRenderer>)` (return type not annotated) — returns `{ story, meta, preview }`: for a CSF factory story (`isStory(story)`) its `input`, its meta's `input` and its preview's `composed` annotations; otherwise `story`, `meta` (its `input` when `isMeta(meta)`) and `projectAnnotations` | `[AST:code/core/src/preview-api/modules/store/csf/csf-factory-utils.ts:L10]` |
| `emitTransformCode` | function | `emitTransformCode(source: string \| undefined, context: ReducedStoryContext)` (`async`, return type not annotated; `ReducedStoryContext` is the module-local `Omit<StoryContext<any, Args>, 'abortSignal' \| 'canvasElement' \| 'step' \| 'context'>`) — runs `context.parameters.docs.source.transform` on `source` when both are set, awaits the result, and emits `SNIPPET_RENDERED` with `{ id, source, args: unmappedArgs }` on the addons channel (the event the docs `SourceContainer` listens to) | `[AST:code/core/src/preview-api/modules/preview-web/emitTransformCode.ts:L15]` |
| `pauseAnimations` | function | `pauseAnimations(atEnd = true): CleanupCallback` — adds `<style>` rules that pause every CSS animation (in `reverse` direction when `atEnd`, else `normal`) and turn off transitions; the returned callback removes them. Without a `document` (React Native) it returns a no-op | `[AST:code/core/src/preview-api/modules/preview-web/render/animation-utils.ts:L18]` |
| `waitForAnimations` | function | `waitForAnimations(signal?: AbortSignal)` (`async`, return type not annotated) — waits, through the Web Animations API, until the running non-infinite animations of the document and its shadow roots finish, giving up after 5000 ms or once `signal` is aborted | `[AST:code/core/src/preview-api/modules/preview-web/render/animation-utils.ts:L54]` |
| `simulatePageLoad` | function | `simulatePageLoad($container: any)` — re-inserts the `<script>` tags inside `$container` that have no `type` or a JavaScript one into a `#scripts-root` element, one after another so they run in order, then calls `simulateDOMContentLoaded`; with no `<script>` tag at all it calls `simulateDOMContentLoaded` straight away | `[AST:code/core/src/preview-api/modules/preview-web/simulate-pageload.ts:L83]` |
| `simulateDOMContentLoaded` | function | `simulateDOMContentLoaded()` — dispatches a bubbling, cancelable `DOMContentLoaded` event on `document` | `[AST:code/core/src/preview-api/modules/preview-web/simulate-pageload.ts:L31]` |
| `ReporterAPI` | class | `{ reports: Report[] = []; async addReport(report: Report) }` — collects the reports of one story: `addReport` pushes onto `reports`. The story store creates one per story (`StoryStore.ts:L249`) and the portable-stories composer another (`portable-stories.ts:L142`); a composed story's `reporting` field is a `ReporterAPI` | `[AST:code/core/src/preview-api/modules/store/reporter-api.ts:L8]` `[SRC:code/core/src/types/modules/composedStory.ts:L52]` |
| `Report` | interface | `Report<T = unknown> { type: string; version?: number; result: T; status: 'failed' \| 'passed' \| 'warning' }` — one entry of `ReporterAPI.reports` | `[AST:code/core/src/preview-api/modules/store/reporter-api.ts:L1]` |
| `SelectionStore` | interface | `{ selectionSpecifier: SelectionSpecifier \| null; selection?: Selection; setSelection(selection: Selection): void; setQueryParams(queryParams: Record<PropertyKey, unknown>): void }`, with the interfaces `Selection { storyId: StoryId; viewMode: ViewMode }` and `SelectionSpecifier { storySpecifier: StorySpecifier; viewMode: ViewMode; args?: Args; globals?: Args }` — where the preview keeps the selected story (`UrlStore` is the URL-backed one) | `[AST:code/core/src/preview-api/modules/preview-web/SelectionStore.ts:L17]` |
| `View` | interface | `View<TStorybookRoot>`, the preview's display contract, with the methods `prepareForStory(story: PreparedStory<any>): TStorybookRoot` (comment: "Get ready to render a story, returning the element to render to"), `prepareForDocs(): TStorybookRoot`, `showErrorDisplay(err: { message?: string; stack?: string }): void`, `showNoPreview(): void`, `showPreparingStory(options?: { immediate: boolean }): void`, `showPreparingDocs(options?: { immediate: boolean }): void`, `showMain(): void`, `showDocs(): void`, `showStory(): void` and `showStoryDuringRender(): void` (`WebView` above implements it for the browser) | `[AST:code/core/src/preview-api/modules/preview-web/View.ts:L3]` |

### Test-harness mock utilities (`storybook/test`)

These mirror Vitest's `vi.*` mock helpers but are re-exported through `storybook/test` so play functions can manipulate mocks without importing Vitest directly.

| Export | Kind | Signature | Source |
|---|---|---|---|
| `onMockCall` | function | `(callback: Listener) => () => void` — register global listener on any mock-function call | `[AST:code/core/src/test/spy.ts:L35]` |
| `isMockFunction` | function | `isMockFunction(fn: any): fn is MockInstance` — whether `fn` is a mock; `@vitest/spy`'s function, re-exported by name (`export { isMockFunction, mocks }`) | `[AST:code/core/src/test/spy.ts:L17]` `[EXT:https://unpkg.com/@vitest/spy@3.2.4/dist/index.d.ts]` |
| `clearAllMocks` | function | `() => void` — clear call history, keep implementations | `[AST:code/core/src/test/spy.ts:L77]` |
| `resetAllMocks` | function | `() => void` — reset call history and return values to undefined | `[AST:code/core/src/test/spy.ts:L89]` |
| `restoreAllMocks` | function | `() => void` — restore original implementations (undo `spyOn`) | `[AST:code/core/src/test/spy.ts:L98]` |
| `mocked` | function | Overloaded TS type helper that returns `item` unchanged: `mocked<T>(item: T): MaybeMocked<T>`; `mocked<T>(item: T, deep?: false): MaybeMocked<T>`; `mocked<T>(item: T, deep: true): MaybeMockedDeep<T>`; `mocked<T>(item: T, options: { partial?: false; deep?: false }): MaybeMocked<T>`; `mocked<T>(item: T, options: { partial?: false; deep: true }): MaybeMockedDeep<T>`; `mocked<T>(item: T, options: { partial: true; deep?: false }): MaybePartiallyMocked<T>`; `mocked<T>(item: T, options: { partial: true; deep: true }): MaybePartiallyMockedDeep<T>` | `[AST:code/core/src/test/spy.ts:L119]` |
| `mocks` | const | `typeof mocks` — re-exported from `@vitest/spy`, set of active mocks | `[AST:code/core/src/test/spy.ts:L17]` |

### Testing Library queries and helpers (`storybook/test`)

`storybook/test` re-exports all of `testing-library.ts` (`export * from './testing-library'`) `[SRC:code/core/src/test/index.ts:L62]`. That file wraps a copy of `@testing-library/dom` in `instrument()`, whose `intercept` option takes `fireEvent` and every method whose name starts with `find` or `waitFor`, casts it to `Writable<Omit<TestingLibraryDom, 'fireEvent'>>` (`TestingLibraryDom = typeof domTestingLibrary`), and destructures each export from it `[SRC:code/core/src/test/testing-library.ts:L15]` `[SRC:code/core/src/test/testing-library.ts:L19]` `[SRC:code/core/src/test/testing-library.ts:L22]` `[SRC:code/core/src/test/testing-library.ts:L39]`. Every name below so keeps the type `@testing-library/dom` gives it: the signatures are those of `@testing-library/dom` 10.4.1, the version the repository's `yarn.lock` resolves `[EXT:https://unpkg.com/@testing-library/dom@10.4.1/types/index.d.ts]`. Their parameter types (`Matcher`, `MatcherOptions`, `SelectorMatcherOptions`, `ByRoleMatcher`, `ByRoleOptions`, `waitForOptions`, `Config`) are `@testing-library/dom` types that `storybook/test` does not export.

**`canvas` methods versus these functions:** every query here takes the `container` element as its first argument. Inside `play`, call the same queries as methods of the story's `canvas`: `test/index.ts` declares `type Queries = BoundFunctions<typeof queries>` and augments the CSF `Canvas` with `interface Canvas extends Queries {}`, so a `canvas` method such as `canvas.getByRole('button')` takes every argument of its query but `container` `[SRC:code/core/src/test/index.ts:L13]` `[SRC:code/core/src/test/index.ts:L18]`.

**Queries.** The six variants of a query take the same matcher arguments, `find*` also taking `waitFor`'s options last, and differ in what they return; `@testing-library/dom`'s `query-helpers.d.ts` puts it as "query methods have a common call signature. Only the return type differs." A row's signature is the signature of every name in that row.

| Queries | Kind | Signature (each name in the row) | Source |
|---|---|---|---|
| `getByRole` | function | `<T extends HTMLElement = HTMLElement>(container: HTMLElement, role: ByRoleMatcher, options?: ByRoleOptions) => T`: By ARIA role; returns the matching element | `[SRC:code/core/src/test/testing-library.ts:L72]` |
| `getByText`, `getByLabelText` | function | `<T extends HTMLElement = HTMLElement>(container: HTMLElement, id: Matcher, options?: SelectorMatcherOptions) => T`: By text content or label text; returns the matching element | `[SRC:code/core/src/test/testing-library.ts:L74]` `[SRC:code/core/src/test/testing-library.ts:L70]` |
| `getByAltText`, `getByDisplayValue`, `getByPlaceholderText`, `getByTestId`, `getByTitle` | function | `<T extends HTMLElement = HTMLElement>(container: HTMLElement, id: Matcher, options?: MatcherOptions) => T`: By alt text, display value, placeholder text, test id or title; returns the matching element | `[SRC:code/core/src/test/testing-library.ts:L68]` `[SRC:code/core/src/test/testing-library.ts:L69]` `[SRC:code/core/src/test/testing-library.ts:L71]` `[SRC:code/core/src/test/testing-library.ts:L73]` `[SRC:code/core/src/test/testing-library.ts:L75]` |
| `getAllByRole` | function | `<T extends HTMLElement = HTMLElement>(container: HTMLElement, role: ByRoleMatcher, options?: ByRoleOptions) => T[]`: By ARIA role; returns every matching element | `[SRC:code/core/src/test/testing-library.ts:L64]` |
| `getAllByText`, `getAllByLabelText` | function | `<T extends HTMLElement = HTMLElement>(container: HTMLElement, id: Matcher, options?: SelectorMatcherOptions) => T[]`: By text content or label text; returns every matching element | `[SRC:code/core/src/test/testing-library.ts:L66]` `[SRC:code/core/src/test/testing-library.ts:L62]` |
| `getAllByAltText`, `getAllByDisplayValue`, `getAllByPlaceholderText`, `getAllByTestId`, `getAllByTitle` | function | `<T extends HTMLElement = HTMLElement>(container: HTMLElement, id: Matcher, options?: MatcherOptions) => T[]`: By alt text, display value, placeholder text, test id or title; returns every matching element | `[SRC:code/core/src/test/testing-library.ts:L60]` `[SRC:code/core/src/test/testing-library.ts:L61]` `[SRC:code/core/src/test/testing-library.ts:L63]` `[SRC:code/core/src/test/testing-library.ts:L65]` `[SRC:code/core/src/test/testing-library.ts:L67]` |
| `queryByRole` | function | `<T extends HTMLElement = HTMLElement>(container: HTMLElement, role: ByRoleMatcher, options?: ByRoleOptions) => T \| null`: By ARIA role; returns the matching element or `null` | `[SRC:code/core/src/test/testing-library.ts:L102]` |
| `queryByText`, `queryByLabelText` | function | `<T extends HTMLElement = HTMLElement>(container: HTMLElement, id: Matcher, options?: SelectorMatcherOptions) => T \| null`: By text content or label text; returns the matching element or `null` | `[SRC:code/core/src/test/testing-library.ts:L104]` `[SRC:code/core/src/test/testing-library.ts:L100]` |
| `queryByAltText`, `queryByDisplayValue`, `queryByPlaceholderText`, `queryByTestId`, `queryByTitle` | function | `<T extends HTMLElement = HTMLElement>(container: HTMLElement, id: Matcher, options?: MatcherOptions) => T \| null`: By alt text, display value, placeholder text, test id or title; returns the matching element or `null` | `[SRC:code/core/src/test/testing-library.ts:L97]` `[SRC:code/core/src/test/testing-library.ts:L99]` `[SRC:code/core/src/test/testing-library.ts:L101]` `[SRC:code/core/src/test/testing-library.ts:L103]` `[SRC:code/core/src/test/testing-library.ts:L105]` |
| `queryAllByRole` | function | `<T extends HTMLElement = HTMLElement>(container: HTMLElement, role: ByRoleMatcher, options?: ByRoleOptions) => T[]`: By ARIA role; returns every matching element | `[SRC:code/core/src/test/testing-library.ts:L93]` |
| `queryAllByText`, `queryAllByLabelText` | function | `<T extends HTMLElement = HTMLElement>(container: HTMLElement, id: Matcher, options?: SelectorMatcherOptions) => T[]`: By text content or label text; returns every matching element | `[SRC:code/core/src/test/testing-library.ts:L95]` `[SRC:code/core/src/test/testing-library.ts:L91]` |
| `queryAllByAltText`, `queryAllByDisplayValue`, `queryAllByPlaceholderText`, `queryAllByTestId`, `queryAllByTitle` | function | `<T extends HTMLElement = HTMLElement>(container: HTMLElement, id: Matcher, options?: MatcherOptions) => T[]`: By alt text, display value, placeholder text, test id or title; returns every matching element | `[SRC:code/core/src/test/testing-library.ts:L88]` `[SRC:code/core/src/test/testing-library.ts:L90]` `[SRC:code/core/src/test/testing-library.ts:L92]` `[SRC:code/core/src/test/testing-library.ts:L94]` `[SRC:code/core/src/test/testing-library.ts:L96]` |
| `findByRole` | function | `<T extends HTMLElement = HTMLElement>(container: HTMLElement, role: ByRoleMatcher, options?: ByRoleOptions, waitForElementOptions?: waitForOptions) => Promise<T>`: By ARIA role; resolves to the matching element | `[SRC:code/core/src/test/testing-library.ts:L56]` |
| `findByText`, `findByLabelText` | function | `<T extends HTMLElement = HTMLElement>(container: HTMLElement, id: Matcher, options?: SelectorMatcherOptions, waitForElementOptions?: waitForOptions) => Promise<T>`: By text content or label text; resolves to the matching element | `[SRC:code/core/src/test/testing-library.ts:L58]` `[SRC:code/core/src/test/testing-library.ts:L54]` |
| `findByAltText`, `findByDisplayValue`, `findByPlaceholderText`, `findByTestId`, `findByTitle` | function | `<T extends HTMLElement = HTMLElement>(container: HTMLElement, id: Matcher, options?: MatcherOptions, waitForElementOptions?: waitForOptions) => Promise<T>`: By alt text, display value, placeholder text, test id or title; resolves to the matching element | `[SRC:code/core/src/test/testing-library.ts:L52]` `[SRC:code/core/src/test/testing-library.ts:L53]` `[SRC:code/core/src/test/testing-library.ts:L55]` `[SRC:code/core/src/test/testing-library.ts:L57]` `[SRC:code/core/src/test/testing-library.ts:L59]` |
| `findAllByRole` | function | `<T extends HTMLElement = HTMLElement>(container: HTMLElement, role: ByRoleMatcher, options?: ByRoleOptions, waitForElementOptions?: waitForOptions) => Promise<T[]>`: By ARIA role; resolves to every matching element | `[SRC:code/core/src/test/testing-library.ts:L48]` |
| `findAllByText`, `findAllByLabelText` | function | `<T extends HTMLElement = HTMLElement>(container: HTMLElement, id: Matcher, options?: SelectorMatcherOptions, waitForElementOptions?: waitForOptions) => Promise<T[]>`: By text content or label text; resolves to every matching element | `[SRC:code/core/src/test/testing-library.ts:L50]` `[SRC:code/core/src/test/testing-library.ts:L46]` |
| `findAllByAltText`, `findAllByDisplayValue`, `findAllByPlaceholderText`, `findAllByTestId`, `findAllByTitle` | function | `<T extends HTMLElement = HTMLElement>(container: HTMLElement, id: Matcher, options?: MatcherOptions, waitForElementOptions?: waitForOptions) => Promise<T[]>`: By alt text, display value, placeholder text, test id or title; resolves to every matching element | `[SRC:code/core/src/test/testing-library.ts:L44]` `[SRC:code/core/src/test/testing-library.ts:L45]` `[SRC:code/core/src/test/testing-library.ts:L47]` `[SRC:code/core/src/test/testing-library.ts:L49]` `[SRC:code/core/src/test/testing-library.ts:L51]` |
| `queryByAttribute` | function | `(attribute: string, container: HTMLElement, id: Matcher, options?: MatcherOptions) => HTMLElement \| null` (declared `const queryByAttribute: QueryByAttribute`): the element whose `attribute` matches `id`, or `null`; the attribute name comes before `container` | `[SRC:code/core/src/test/testing-library.ts:L98]` |
| `queryAllByAttribute` | function | `(attribute: string, container: HTMLElement, id: Matcher, options?: MatcherOptions) => HTMLElement[]` (declared `const queryAllByAttribute: AllByAttribute`): every element whose `attribute` matches `id` | `[SRC:code/core/src/test/testing-library.ts:L89]` |

The option types, all of whose members are optional: `MatcherOptions` is `{ exact?, trim?, collapseWhitespace?, normalizer?, suggest? }` (its comments say to pass `normalizer` with `getDefaultNormalizer` instead of `trim` and `collapseWhitespace`); `SelectorMatcherOptions` adds `selector?` and `ignore?` to it; `ByRoleOptions` is `{ suggest?, hidden?, selected?, busy?, checked?, pressed?, current?, expanded?, level?, value?, queryFallbacks?, name?, description? }`; and the `waitForOptions` that `find*` take as `waitForElementOptions` are `{ container?, timeout?, interval?, onTimeout?, mutationObserverOptions? }`. `Matcher` is `MatcherFunction \| RegExp \| number \| string`, and `ByRoleMatcher` is `ARIARole \| (string & {})`.

**Helpers:**

| Export | Kind | Signature / Purpose | Source |
|---|---|---|---|
| `buildQueries` | function | `buildQueries<Arguments extends any[]>(queryAllBy: GetAllBy<Arguments>, getMultipleError: GetErrorFunction<Arguments>, getMissingError: GetErrorFunction<Arguments>): BuiltQueryMethods<Arguments>`: build a custom query family from a `queryAllBy` function and the two error-message functions; `BuiltQueryMethods` is the tuple `[queryBy, getAllBy, getBy, findAllBy, findBy]` | `[SRC:code/core/src/test/testing-library.ts:L40]` |
| `configure` | function | `configure(configDelta: ConfigFn \| Partial<Config>): void`: change Testing Library's global `Config` (`testIdAttribute`, `asyncUtilTimeout`, `defaultHidden`, `defaultIgnore`, `throwSuggestions`, `getElementError`, ...), from a partial object or a function of the current config | `[SRC:code/core/src/test/testing-library.ts:L41]` |
| `getConfig` | function | `getConfig(): Config`: the current global `Config` | `[SRC:code/core/src/test/testing-library.ts:L76]` |
| `createEvent` | const | `CreateObject & CreateFunction`: callable as `(eventName: string, node: Document \| Element \| Window \| Node, init?: {}, options?: { EventType?: string; defaultInit?: {} }) => Event`, with one member per event name of `EventType` (`createEvent.click`, ...), each `(element: Document \| Element \| Window \| Node, options?: {}) => Event`: build a DOM `Event` for a node | `[SRC:code/core/src/test/testing-library.ts:L42]` |
| `getDefaultNormalizer` | function | `getDefaultNormalizer(options?: DefaultNormalizerOptions): NormalizerFn`: build the default text normalizer (`DefaultNormalizerOptions = { trim?: boolean; collapseWhitespace?: boolean }`, `NormalizerFn = (text: string) => string`) for a query's `normalizer` option | `[SRC:code/core/src/test/testing-library.ts:L77]` |
| `getElementError` | function | `getElementError(message: string \| null, container: HTMLElement): Error`: the `Error` for `message` about `container` | `[SRC:code/core/src/test/testing-library.ts:L78]` |
| `getNodeText` | function | `getNodeText(node: HTMLElement): string`: the text of `node` | `[SRC:code/core/src/test/testing-library.ts:L79]` |
| `getQueriesForElement` | function | `getQueriesForElement<QueriesToBind extends Queries = typeof queries, T extends QueriesToBind = QueriesToBind>(element: HTMLElement, queriesToBind?: T): BoundFunctions<T>`: every query of `queriesToBind` (by default `queries`) bound to `element`; `@testing-library/dom` declares `within` as `typeof getQueriesForElement` | `[SRC:code/core/src/test/testing-library.ts:L80]` |
| `getRoles` | function | `getRoles(container: HTMLElement): { [index: string]: HTMLElement[] }`: the elements under `container`, keyed by role | `[SRC:code/core/src/test/testing-library.ts:L81]` |
| `getSuggestedQuery` | function | `getSuggestedQuery(element: HTMLElement, variant?: Variant, method?: Method): Suggestion \| undefined`: the query Testing Library suggests for `element` (`Variant` is `'find' \| 'findAll' \| 'get' \| 'getAll' \| 'query' \| 'queryAll'`, `Method` a query family such as `'Role'` or `'Text'`) | `[SRC:code/core/src/test/testing-library.ts:L82]` |
| `isInaccessible` | function | `isInaccessible(element: Element): boolean`: whether `element` is inaccessible | `[SRC:code/core/src/test/testing-library.ts:L83]` |
| `logDOM` | function | `logDOM(dom?: Element \| HTMLDocument, maxLength?: number, options?: PrettyDOMOptions): void`: log the DOM tree (it takes `prettyDOM`'s arguments) | `[SRC:code/core/src/test/testing-library.ts:L84]` |
| `logRoles` | function | `logRoles(container: HTMLElement, options?: LogRolesOptions): string`: log the elements under `container` by role (`LogRolesOptions = { hidden?: boolean }`, not exported) | `[SRC:code/core/src/test/testing-library.ts:L85]` |
| `prettyDOM` | function | `prettyDOM(dom?: Element \| HTMLDocument, maxLength?: number, options?: PrettyDOMOptions): string \| false`: the DOM tree as a readable string (`PrettyDOMOptions` extends `pretty-format`'s options with `filterNode?: (node: Node) => boolean`, which by default leaves out `<style />`, `<script />` and comment nodes) | `[SRC:code/core/src/test/testing-library.ts:L86]` |
| `prettyFormat` | namespace | The `pretty-format` module, which `@testing-library/dom` re-exports (`import * as prettyFormat from 'pretty-format'`) | `[SRC:code/core/src/test/testing-library.ts:L111]` |
| `queries` | namespace | The module of the table's 48 `getBy*` to `findAllBy*` queries; the two `*ByAttribute` queries are in `queryHelpers` instead (`import * as queries from './queries'` in `@testing-library/dom`): the default set `getQueriesForElement` binds | `[SRC:code/core/src/test/testing-library.ts:L87]` |
| `queryHelpers` | namespace | `@testing-library/dom`'s `query-helpers` module: `queryByAttribute`, `queryAllByAttribute`, `getElementError` and `buildQueries`, with their types | `[SRC:code/core/src/test/testing-library.ts:L106]` |
| `waitForElementToBeRemoved` | function | `waitForElementToBeRemoved<T>(callback: T \| (() => T), options?: waitForOptions): Promise<void>`: resolve once the element or elements `callback` gives leave the DOM (`waitForOptions = { container?, timeout?, interval?, onTimeout?, mutationObserverOptions? }`); intercepted like `waitFor` | `[SRC:code/core/src/test/testing-library.ts:L109]` |

**User-event exports** (`testing-library.ts` imports `@testing-library/user-event` as `_userEvent`):

| Export | Kind | Type / Purpose | Source |
|---|---|---|---|
| `UserEvent` | interface | `interface UserEvent extends _UserEvent {}`, with `_UserEvent = typeof _userEvent`: the type of the `@testing-library/user-event` module. The instrumented `userEvent` above is declared `{ userEvent: UserEvent['userEvent'] }` | `[AST:code/core/src/test/testing-library.ts:L119]` `[SRC:code/core/src/test/testing-library.ts:L117]` |
| `uninstrumentedUserEvent` | const | `_userEvent.userEvent`: user-event's `userEvent` object as it is, not passed through `instrument()`, which wraps the `userEvent` export with `intercept: true` | `[AST:code/core/src/test/testing-library.ts:L121]` |
| `UserEventObject` | type | `ReturnType<typeof userEvent.setup>` (user-event's `userEvent`): the type of the `userEvent` a story context carries, which `test/index.ts` adds to `StoryContext` by module augmentation (`userEvent: UserEventObject`) | `[AST:code/core/src/test/index.ts:L15]` `[SRC:code/core/src/test/index.ts:L19]` |

## storybook/manager-api

Entry: `code/core/src/manager-api/index.ts`. Used when writing a **manager-side** addon (addon panels, toolbar buttons, sidebar items). Not needed for story authoring.

| Export | Kind | Purpose | Source |
|---|---|---|---|
| (re-exports `./root`) | — | Full addon manager API: story selection, notifications, refs, globals, settings | `[SRC:code/core/src/manager-api/index.ts:L1]` |
| `experimental_UniversalStore` | class | Cross-environment state store | `[AST:code/core/src/manager-api/index.ts:L3]` |
| `experimental_useUniversalStore` | hook | Access universal store in manager components. `storybook/manager-api` exports it only with the `experimental_` prefix | `[AST:code/core/src/manager-api/index.ts:L4]` |
| `experimental_MockUniversalStore` | class | Mock store for tests. `storybook/manager-api` exports the class only with the `experimental_` prefix (the unprefixed name is a type-only export of `storybook/internal/types`) | `[AST:code/core/src/manager-api/index.ts:L5]` |
| `experimental_useStatusStore`, `experimental_getStatusStore` | hook/func | Status store access (panel badges, test results); exported only with the `experimental_` prefix | `[AST:code/core/src/manager-api/index.ts:L9]` `[AST:code/core/src/manager-api/index.ts:L8]` |
| `experimental_useTestProviderStore`, `experimental_getTestProviderStore` | hook/func | Test provider state (addon-vitest); exported only with the `experimental_` prefix | `[AST:code/core/src/manager-api/index.ts:L16]` `[AST:code/core/src/manager-api/index.ts:L15]` |
| `Tag` | const | System tag names, a `const` object `{ AUTODOCS: 'autodocs', ATTACHED_MDX: 'attached-mdx', UNATTACHED_MDX: 'unattached-mdx', PLAY_FN: 'play-fn', TEST_FN: 'test-fn', DEV: 'dev', TEST: 'test', MANIFEST: 'manifest' }` (`as const`, not a TS `enum`), and the type `Tag = string` (any tag, system or custom) | `[AST:code/core/src/manager-api/index.ts:L26]` `[AST:code/core/src/shared/constants/tags.ts:L4]` |

## storybook/theming

Entry: `code/core/src/theming/index.ts`. Emotion-based styling used by Storybook's UI and addon panels.

| Export | Kind | Purpose | Source |
|---|---|---|---|
| `styled` | const | Emotion `styled` — `styled.div\`...\`` | `[AST:code/core/src/theming/index.ts:L6]` |
| `css` | function | Emotion `css` tagged template | `[AST:code/core/src/theming/index.ts:L13]` |
| `keyframes` | function | Emotion `keyframes` for animations | `[AST:code/core/src/theming/index.ts:L16]` |
| `Global` | component | Emotion `Global` styles | `[AST:code/core/src/theming/index.ts:L14]` |
| `ThemeProvider` | component | Emotion `ThemeProvider` with Storybook theme type | `[AST:code/core/src/theming/index.ts:L17]` |
| `useTheme` | hook | Access current theme | `[AST:code/core/src/theming/index.ts:L18]` |
| `withTheme` | HOC | HOC wrapper for class components | `[AST:code/core/src/theming/index.ts:L19]` |
| `jsx` | function | Emotion JSX runtime | `[AST:code/core/src/theming/index.ts:L15]` |
| `CacheProvider`, `ClassNames` | component | Emotion cache/classnames | `[AST:code/core/src/theming/index.ts:L11]` `[AST:code/core/src/theming/index.ts:L12]` |
| `createCache` | function | Create an emotion cache | `[AST:code/core/src/theming/index.ts:L33]` |
| `isPropValid` | function | `@emotion/is-prop-valid` filter | `[AST:code/core/src/theming/index.ts:L34]` |
| `createGlobal`, `createReset`, `srOnlyStyles` | function/const | Global style helpers | `[AST:code/core/src/theming/index.ts:L36]` |
| `lighten`, `darken`, `getPreferredColorScheme` | function | Color utilities | `[AST:code/core/src/theming/index.ts:L41]` |
| `ignoreSsrWarning` | const | SSR warning suppression string | `[AST:code/core/src/theming/index.ts:L43]` |
| `color` | const | Storybook's base palette (`export * from './base'`): brand colors (`primary: '#FF4785'`, `secondary: '#006DEB'`, `tertiary`, `ancillary`), complementary hues (`orange`, `gold`, `green`, `seafoam`, `purple`, `ultraviolet`), a monochrome scale from `lightest` to `darkest`, `border`, statuses (`positive`, `warning`, `negative`, `critical`) and text colors (`defaultText`, `inverseText`, `positiveText`, `warningText`, `negativeText`); the `Color` type is `typeof color` | `[AST:code/core/src/theming/base.ts:L1]` |
| `background` | const | Background tokens: `{ app, bar, content, preview, gridCellSize: 10, hoverable, positive, warning, negative, critical }` (`bar`, `content` and `preview` are `color.lightest`); the `Background` type is `typeof background` | `[AST:code/core/src/theming/base.ts:L44]` |
| `typography` | const | `{ fonts: { base, mono }, weight: { regular: 400, bold: 700 }, size: { s1: 12, s2: 14, s3: 16, m1: 20, m2: 24, m3: 28, l1: 32, l2: 40, l3: 48, code: 90 } }`, with `fonts.base` a `"Nunito Sans"` sans-serif stack and `fonts.mono` a `ui-monospace` stack; the `Typography` type is `typeof typography` | `[AST:code/core/src/theming/base.ts:L59]` |
| `tokens` | const | `{ light, dark }`, each a set of semantic colors `{ fgColor, bgColor, borderColor }` (keys such as `default`, `muted`, `positive`, `warning`, `negative`, `critical`); the theme `convert` builds spreads `tokens.dark` when `base` is `'dark'`, else `tokens.light` | `[AST:code/core/src/theming/base.ts:L104]` |
| `convert` | function | `convert(inherit: ThemeVars = themes[getPreferredColorScheme()]): StorybookTheme` — expand flat `ThemeVars` into the nested `StorybookTheme` (`color`, `background`, `typography`, `animation`, `easing`, `input`, `button`, `boolean`, `brand`, the bar colors, the code syntax colors, ...) | `[AST:code/core/src/theming/convert.ts:L78]` |
| `ensure` | function | `ensure(input: ThemeVars): StorybookTheme` — returns the converted light theme when `input` is falsy; otherwise logs a warning listing the properties `input` lacks compared with the light theme, and returns `input` converted | `[AST:code/core/src/theming/ensure.ts:L10]` |
| `Theme` | interface | `@emotion/react`'s `Theme` interface, re-exported type-only; `index.ts` augments it (`interface Theme extends StorybookTheme {}`), so the emotion theme is the Storybook theme | `[AST:code/core/src/theming/index.ts:L50]` `[SRC:code/core/src/theming/index.ts:L47]` |
| `CSSObject`, `StyledComponent` | interface | Emotion's `CSSObject` (`@emotion/react`, declared by `@emotion/serialize`) and `StyledComponent` (`@emotion/styled`), re-exported type-only | `[AST:code/core/src/theming/index.ts:L21]` `[AST:code/core/src/theming/index.ts:L8]` |
| `Keyframes`, `Interpolation`, `FunctionInterpolation` | type | Emotion's `Keyframes`, re-exported type-only; `Interpolation<T = {}>` and `FunctionInterpolation<T = {}>` are emotion's `Interpolation` and `FunctionInterpolation` over `T & { theme: StorybookTheme }`, declared in `index.ts` and exported under those names | `[AST:code/core/src/theming/index.ts:L21]` `[AST:code/core/src/theming/index.ts:L27]` `[SRC:code/core/src/theming/index.ts:L24]` `[AST:code/core/src/theming/index.ts:L26]` `[SRC:code/core/src/theming/index.ts:L23]` |

## storybook/theming/create

Entry: `code/core/src/theming/create.ts`. Used in `.storybook/manager.ts` or `preview.ts` to define a custom theme.

| Export | Kind | Signature | Source |
|---|---|---|---|
| `create` | function | `create(vars: ThemeVarsPartial = { base: preferredColorScheme }, rest?: Rest): ThemeVars` — build a theme from partial vars; `vars` is optional, so `create()` returns the theme for the preferred color scheme | `[AST:code/core/src/theming/create.ts:L29]` |
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
| `action` | function | `action(name: string, options: ActionOptions = {}): HandlerFunction` — create an action logger for an arg; `options` is optional | `[AST:code/core/src/actions/runtime/action.ts:L50]` |
| `configureActions` | function | Global action config (max depth, clearOnStoryChange) | `[AST:code/core/src/actions/runtime/configureActions.ts:L9]` |
| `ActionDisplay`, `ActionsFunction` | interface | Action payload types: `ActionDisplay` is one logged action, `ActionsFunction` the overloads of `actions` | `[AST:code/core/src/actions/models/ActionDisplay.ts:L3]` `[AST:code/core/src/actions/models/ActionsFunction.ts:L4]` |
| `ActionOptions`, `ActionsMap`, `HandlerFunction` | type | Action option and handler types: `ActionOptions = Partial<Options> & Partial<TelejsonOptions>`, `ActionsMap<T extends string = string> = Record<T, HandlerFunction>`, `HandlerFunction = (...args: any[]) => any` | `[AST:code/core/src/actions/models/ActionOptions.ts:L11]` `[AST:code/core/src/actions/models/ActionsMap.ts:L3]` `[AST:code/core/src/actions/models/HandlerFunction.ts:L1]` |
| `actions` | function | Declared `actions: ActionsFunction = (...args: any[]) => …`, so it has the `ActionsFunction` overloads: `actions<T extends string>(handlerMap: Record<T, string>, options?: ActionOptions): ActionsMap<T>`, `actions<T extends string>(...handlers: T[]): ActionsMap<T>`, and one overload per count of one to ten handler names followed by `options?: ActionOptions` — create one action handler per name and return them as `ActionsMap<T>` (`Record<T, HandlerFunction>`). With a map, each key names a handler and its value the action name; a single array argument is read as the list of names, and a last argument that is not a string, when there is more than one, as options spread over `config` | `[AST:code/core/src/actions/runtime/actions.ts:L5]` `[SRC:code/core/src/actions/models/ActionsFunction.ts:L4]` |
| `config` | const | `ActionOptions`, starting as `{ depth: 10, clearOnStoryChange: true, limit: 50 }`: the module-wide action options that `action` and `actions` spread under their own options, and that `configureActions` merges new options into (`Object.assign`) | `[AST:code/core/src/actions/runtime/configureActions.ts:L3]` |
| `PANEL_ID` | const | `'storybook/actions/panel'` (`` `${ADDON_ID}/panel` ``): the id the Actions panel is registered under in the manager | `[AST:code/core/src/actions/constants.ts:L3]` |
| `EVENT_ID` | const | `'storybook/actions/action-event'`: the channel event each action handler emits when it is called, and the Actions panel listens to | `[AST:code/core/src/actions/constants.ts:L4]` |
| `CLEAR_ID` | const | `'storybook/actions/action-clear'`: the channel event the Actions panel emits when it clears its log | `[AST:code/core/src/actions/constants.ts:L5]` |
| `CYCLIC_KEY` | const | `'$___storybook.isCyclic'`; nothing else in the repository's `code/` tree reads it | `[AST:code/core/src/actions/constants.ts:L6]` |

**Note:** Prefer `fn()` from `storybook/test` over `action()` in v10 — `fn()` records calls AND allows assertions in `play`. Use `action()` only when the arg is a plain callback with no `play` assertions.

## storybook/actions/decorator

Entry: `code/core/src/actions/decorator.ts`.

| Export | Kind | Purpose | Source |
|---|---|---|---|
| `withActions` | const | **Deprecated** (`@deprecated Will be removed in Storybook v10`) — a decorator, built with `makeDecorator` and typed `<T extends Renderer>(storyFn: PartialStoryFn<T>) => T['storyResult']`, that binds the legacy event handlers | `[AST:code/core/src/actions/decorator.ts:L59]` |

## storybook/highlight

Entry: `code/core/src/highlight/index.ts`.

| Export | Kind | Purpose | Source |
|---|---|---|---|
| `HIGHLIGHT` | const | Event name — emit to highlight a DOM node | `[AST:code/core/src/highlight/index.ts:L1]` |
| `REMOVE_HIGHLIGHT` | const | Event name — remove a specific highlight | `[AST:code/core/src/highlight/index.ts:L1]` |
| `RESET_HIGHLIGHT` | const | Event name — clear all highlights | `[AST:code/core/src/highlight/index.ts:L1]` |
| `SCROLL_INTO_VIEW` | const | Event name — scroll target into view | `[AST:code/core/src/highlight/index.ts:L1]` |
| `ClickEventDetails`, `HighlightMenuItem`, `HighlightOptions` | interface | Event payload types, re-exported type-only from `types.ts` | `[AST:code/core/src/highlight/index.ts:L2]` `[AST:code/core/src/highlight/types.ts:L60]` `[AST:code/core/src/highlight/types.ts:L24]` `[AST:code/core/src/highlight/types.ts:L41]` |
| `HighlightTypes` | interface | `{ parameters: HighlightParameters }`, with the interface `HighlightParameters { highlight?: { disable?: boolean } }` (`disable` removes the tool and turns the feature off): the highlight feature's type bundle. `storybook/highlight` does not export it; import it from `storybook/internal/csf`, whose `core-annotations.ts` re-exports it and folds it into `CoreTypes` | `[AST:code/core/src/highlight/types.ts:L3]` `[SRC:code/core/src/csf/core-annotations.ts:L17]` `[SRC:code/core/src/csf/index.ts:L96]` |

## storybook/viewport

Entry: `code/core/src/viewport/index.ts`. Viewport addon API — responsive viewport definitions, defaults.

| Export | Kind | Purpose | Source |
|---|---|---|---|
| (re-exports) | const/type | Viewport constants, defaults, responsive viewport definitions | `[SRC:code/core/src/viewport/index.ts]` |
| `INITIAL_VIEWPORTS` | const | The 28 built-in device viewports, `as const satisfies ViewportMap`: `iphone5`, `iphone6`, `iphone6p`, `iphone8p`, `iphonex`, `iphonexr`, `iphonexsmax`, `iphonese2`, `iphone12mini`, `iphone12`, `iphone12promax`, `iphoneSE3`, `iphone13`, `iphone13pro`, `iphone13promax`, `iphone14`, `iphone14pro`, `iphone14promax`, `ipad`, `ipad10p`, `ipad11p`, `ipad12p`, `galaxys5`, `galaxys9`, `nexus5x`, `nexus6p`, `pixel`, `pixelxl`, each `{ name, styles: { height, width }, type }` (`iphone5` is `{ name: 'iPhone 5', styles: { height: '568px', width: '320px' }, type: 'mobile' }`). Its keys are the `InitialViewportKeys` type | `[AST:code/core/src/viewport/defaults.ts:L3]` |
| `MINIMAL_VIEWPORTS` | const | Four generic viewports, `as const satisfies ViewportMap`: `mobile1` (`'Small mobile'`, 320×568), `mobile2` (`'Large mobile'`, 414×896), `tablet` (834×1112) and `desktop` (1280×1024), width × height in `px` | `[AST:code/core/src/viewport/defaults.ts:L234]` |
| `DEFAULT_VIEWPORT` | const | `'responsive'`; nothing else in the repository's `code/` tree reads it | `[AST:code/core/src/viewport/defaults.ts:L232]` |
| `responsiveViewport` | const | `Viewport`: `{ name: 'Reset viewport', styles: { height: '100%', width: '100%' }, type: 'desktop' }`; marked `@deprecated Will be removed in Storybook 11` | `[AST:code/core/src/viewport/responsiveViewport.tsx:L4]` |
| `TOOL_ID` | const | `'storybook/viewport/tool'` (`` `${ADDON_ID}/tool` ``): the id the viewport toolbar tool is registered under in the manager. The same `constants.ts` exports the viewport's `ADDON_ID` (`'storybook/viewport'`), `PARAM_KEY` (`'viewport'`) and `PANEL_ID` (`'storybook/viewport/panel'`), which are not the actions, a11y and vitest constants of the same names | `[AST:code/core/src/viewport/constants.ts:L4]` `[AST:code/core/src/viewport/constants.ts:L1]` `[AST:code/core/src/viewport/constants.ts:L2]` `[AST:code/core/src/viewport/constants.ts:L3]` |

The viewport types (`Viewport`, `ViewportMap`, `ViewportStyles`, `ViewportType`, `GlobalState`, `GlobalStateUpdate`, `ViewportParameters`, `ViewportGlobals`, `ViewportTypes`) are in `story-types.md`, "Viewport types".

## storybook/internal/types

Entry: `code/core/src/types/index.ts`. This is the canonical home of the **CSF types** on the core side — though most React authors import them from `@storybook/react-vite` or `@storybook/react`.

**CSF types re-exported from `storybook/internal/csf`** (`code/core/src/types/modules/csf.ts`, re-exported by `types/index.ts:L3`). This path has no `Meta`, `StoryObj`, `Decorator` or `Loader`: those are the React renderer's names (`@storybook/react-vite` / `@storybook/react`), and their core counterparts are, in that order, `ComponentAnnotations`, `StoryAnnotations`, `DecoratorFunction` and `LoaderFunction`.

`BaseProjectAnnotations` is CSF's `ProjectAnnotations` interface, re-exported under that name. Each row cites the re-export, then the declaration.

| Export | Kind | Source |
|---|---|---|
| `ComponentAnnotations` | interface | `[AST:code/core/src/types/modules/csf.ts:L19]` `[AST:code/core/src/csf/story.ts:L452]` |
| `StoryAnnotations` | type | `[AST:code/core/src/types/modules/csf.ts:L52]` `[AST:code/core/src/csf/story.ts:L543]` |
| `StoryFn` | type | `[AST:code/core/src/types/modules/csf.ts:L58]` `[AST:code/core/src/csf/story.ts:L327]` |
| `DecoratorFunction` | type | `[AST:code/core/src/types/modules/csf.ts:L24]` `[AST:code/core/src/csf/story.ts:L331]` |
| `LoaderFunction` | type | `[AST:code/core/src/types/modules/csf.ts:L32]` `[AST:code/core/src/csf/story.ts:L249]` |
| `Parameters` | interface | `[AST:code/core/src/types/modules/csf.ts:L33]` `[AST:code/core/src/csf/story.ts:L32]` |
| `ArgTypes` | type | `[AST:code/core/src/types/modules/csf.ts:L12]` `[AST:code/core/src/csf/story.ts:L162]` |
| `Args` | interface | `[AST:code/core/src/types/modules/csf.ts:L8]` `[AST:code/core/src/csf/story.ts:L153]` |
| `StoryContext` | interface | `[AST:code/core/src/types/modules/csf.ts:L54]` `[AST:code/core/src/csf/story.ts:L268]` |
| `PlayFunction` | type | `[AST:code/core/src/types/modules/csf.ts:L36]` `[AST:code/core/src/csf/story.ts:L302]` |
| `BaseProjectAnnotations` | interface | `[AST:code/core/src/types/modules/csf.ts:L38]` `[AST:code/core/src/csf/story.ts:L421]` |
| `Canvas` | interface | `[AST:code/core/src/types/modules/csf.ts:L17]` `[AST:code/core/src/csf/story.ts:L266]` |
| `Globals` | interface | `[AST:code/core/src/types/modules/csf.ts:L25]` `[AST:code/core/src/csf/story.ts:L165]` |

`storybook/internal/types` also declares its own interface `ProjectAnnotations<TRenderer>` `[AST:code/core/src/types/modules/story.ts:L43]`, which extends `BaseProjectAnnotations<TRenderer>` with `testingLibraryRender?` and `renderToCanvas?`; it is the type behind the React `Preview`.

**Additional rendering/runtime types:**

| Export | Kind | Purpose | Source |
|---|---|---|---|
| `ViewMode` | type | `OrString<'story' \| 'docs' \| 'settings'> \| undefined`: any string (`OrString<T> = T \| (string & {})`) or `undefined`, with `'story'`, `'docs'` and `'settings'` as the named values | `[AST:code/core/src/types/modules/csf.ts:L71]` |
| `StorybookParameters` | interface | Storybook-specific parameters | `[SRC:code/core/src/types/index.ts]` |
| `WebRenderer` | interface | Base renderer with `canvasElement` | `[SRC:code/core/src/types/index.ts]` |
| `RenderToCanvas` | type | Renderer render function signature | `[SRC:code/core/src/types/index.ts]` |
| `CSFFile` | type | Parsed CSF file structure | `[SRC:code/core/src/types/index.ts]` |
| `PreparedStory` | type | Story with decorators/loaders applied | `[SRC:code/core/src/types/index.ts]` |
| `NormalizedComponentAnnotations`, `NormalizedStoryAnnotations`, `NormalizedProjectAnnotations` | type | Internal normalized forms | `[SRC:code/core/src/types/index.ts]` |
| `RenderContext` | type | Renderer context passed to `render` | `[SRC:code/core/src/types/index.ts]` |

## storybook/internal/csf

Entry: `code/core/src/csf/index.ts`.

| Export | Kind | Purpose | Source |
|---|---|---|---|
| `toId` | function | `(kind: string, name?: string) => string` — generate a story ID | `[AST:code/core/src/csf/index.ts:L27]` |
| `toTestId` | function | Generate a test ID from a story ID and a test name (`parentId:test-name`) | `[AST:code/core/src/csf/index.ts:L31]` |
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

`[SRC:code/core/src/components/index.ts]`

## Infrastructure subpaths (tier C)

These are imported when building **custom addons**, NOT when authoring stories. Listed for completeness:

| Subpath | Purpose | Source |
|---|---|---|
| `storybook/internal/common` | Preset / config helpers (`loadMainConfig`, `normalizeStories`, `getStorybookInfo`) | `[AST:code/core/src/common/index.ts]` |
| `storybook/internal/channels` | `Channel`, `PostMessageTransport`, `WebsocketTransport`, `createBrowserChannel` | `[SRC:code/core/src/channels/index.ts]` |
| `storybook/internal/core-events` | 100+ event constants: `CHANNEL_CREATED`, `STORY_SPECIFIED`, `STORY_PREPARED`, `STORY_RENDERED`, `UPDATE_STORY_ARGS`, `GLOBALS_UPDATED`, `SELECT_STORY`, `PREVIEW_INITIALIZED`, etc. | `[SRC:code/core/src/core-events/index.ts]` |
| `storybook/internal/instrumenter` | `instrument()` wraps functions for tracking in `play` | `[AST:code/core/src/instrumenter/index.ts:L1]` |
| `storybook/internal/router` | Router utilities | `[SRC:code/core/src/router/index.ts]` |
| `storybook/internal/client-logger` | `logger`, `once`, `deprecate`, `pretty` — browser-side logging | `[AST:code/core/src/client-logger/index.ts:L23]` |
| `storybook/internal/node-logger` | Node-side logger + CLI helpers (`prompt`, `logTracker`, `colors`) | `[SRC:code/core/src/node-logger/index.ts:L67]` |
| `storybook/internal/telemetry` | `telemetry`, `getStorybookMetadata`, `getSessionId`, `addToGlobalContext` | `[SRC:code/core/src/telemetry/index.ts:L31]` |
| `storybook/internal/csf-tools` | `CsfFile`, `ConfigFile`, `babelParse`, `enrichCsf`, `getStorySortParameter`, `vitestTransform`, `componentTransform` | `[SRC:code/core/src/csf-tools/index.ts:L1]` |
| `storybook/internal/docs-tools` | ArgTypes utilities, shared docgen helpers | `[SRC:code/core/src/docs-tools/index.ts]` |
| `storybook/internal/mocking-utils` | The module-mocking helpers behind `sb.mock`. `index.ts` re-exports six modules (`export * from './automock'` and so on), whose exports are: from `automock.ts`, `getAutomockCode`, `automockModule` and the `__STORYBOOK_GLOBAL_THIS_ACCESSOR__` constant; from `extract.ts`, `extractMockCalls`, `rewriteSbMockImportCalls`, `babelParser`, `isModuleDirectory` and the `MockCall` type; from `resolve.ts`, `resolveMock`, `resolveExternalModule`, `resolveWithExtensions`, `getRealPath`, `getIsExternal` and `isExternal`; from `esmWalker.ts`, `esmWalker`, `isNodeInPattern`, `setIsNodeInPattern`, `isStaticProperty`, `isStaticPropertyKey`, `isFunctionNode`, `isInDestructuringAssignment`, `getArbitraryModuleIdentifier`, the `Positioned` and `Node` types and every `estree` type (`export type * from 'estree'`); from `runtime.ts`, `getMockerRuntime`; from `redirect.ts`, `findMockRedirect`, re-exported from `@vitest/mocker/redirect` | `[SRC:code/core/src/mocking-utils/index.ts:L1]` `[AST:code/core/src/mocking-utils/automock.ts:L17]` `[AST:code/core/src/mocking-utils/extract.ts:L85]` `[AST:code/core/src/mocking-utils/resolve.ts:L74]` `[AST:code/core/src/mocking-utils/esmWalker.ts:L71]` `[AST:code/core/src/mocking-utils/runtime.ts:L8]` `[AST:code/core/src/mocking-utils/redirect.ts:L3]` |
| `storybook/internal/core-server` | `StoryIndexGenerator`, `generateStoryFile`, `experimental_loadStorybook`, `getPreviewHeadTemplate`, `getPreviewBodyTemplate` | `[SRC:code/core/src/core-server/index.ts:L3]` |
| `storybook/internal/cli` | Framework detection, project type detection, ESLint plugin integration | `[SRC:code/core/src/cli/index.ts]` |
| `storybook/internal/babel` | Babel core (`core`, `generate`, `traverse`, `types`, `parser`, `transformSync`), `recast`, `BabelFile`, `NodePath` | `[SRC:code/core/src/babel/index.ts:L35]` |
