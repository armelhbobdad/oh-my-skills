## Full API Reference

### 1. storybook/test

Instrumented testing utilities wrapping `@vitest/spy` and `@testing-library/user-event` for use inside `play` functions and portable story tests.

`[SRC:code/core/src/test/index.ts:L1]`

#### Value Exports

| Export | Signature | Purpose |
|--------|-----------|---------|
| `expect` | `expect(value: any) => Matchers` | Instrumented vitest-compatible assertion `[SRC:code/core/src/test/index.ts:L24]` |
| `fn` | `fn(impl?: Function) => MockFunction` | Create spy/mock function `[SRC:code/core/src/test/index.ts:L26]` |
| `spyOn` | `spyOn(obj: object, method: string) => MockFunction` | Spy on object method `[SRC:code/core/src/test/index.ts:L27]` |
| `mocked` | `mocked<T>(item: T, deep?: boolean) => MaybeMocked<T>` | Type helper for mocked values `[SRC:code/core/src/test/index.ts:L28]` |
| `isMockFunction` | `isMockFunction(fn: Function) => boolean` | Check if function is a mock `[SRC:code/core/src/test/index.ts:L29]` |
| `userEvent` | `userEvent: UserEvent` | Instrumented user event simulation (click, type, hover, etc.) `[SRC:code/core/src/test/index.ts:L31]` |
| `within` | `within(element: HTMLElement) => Screen` | Scoped queries within element `[SRC:code/core/src/test/index.ts:L33]` |
| `screen` | `screen: Screen` | Testing-library screen queries `[SRC:code/core/src/test/index.ts:L34]` |
| `waitFor` | `waitFor(callback: () => void, options?) => Promise<void>` | Wait for assertion to pass `[SRC:code/core/src/test/index.ts:L35]` |
| `waitForElementToBeRemoved` | `waitForElementToBeRemoved(element, options?) => Promise<void>` | Wait for element removal `[SRC:code/core/src/test/index.ts:L36]` |
| `clearAllMocks` | `clearAllMocks() => void` | Clear all mock state `[SRC:code/core/src/test/index.ts:L37]` |
| `resetAllMocks` | `resetAllMocks() => void` | Reset all mocks to initial state `[SRC:code/core/src/test/index.ts:L38]` |
| `restoreAllMocks` | `restoreAllMocks() => void` | Restore all mocked implementations `[SRC:code/core/src/test/index.ts:L39]` |
| `onMockCall` | `onMockCall(callback: (mock: MockInstance, args: unknown[]) => void) => () => void` | Register listener for mock function invocations; returns unsubscribe function `[SRC:code/core/src/test/spy.ts:L35]` |
| `sb` | `sb: { mock: (path: string \| Promise<unknown>, factory?: { spy?: boolean }) => void }` | Module mocker stub — `sb.mock()` registers module mock for Vitest integration (noop until Vitest plugin injects runtime) `[SRC:code/core/src/test/index.ts:L55]` |
| `getByRole` | `getByRole(role: string, options?) => HTMLElement` | Query by ARIA role `[SRC:code/core/src/test/index.ts:L41]` |
| `getByText` | `getByText(text: string | RegExp, options?) => HTMLElement` | Query by text content `[SRC:code/core/src/test/index.ts:L42]` |
| `getByTestId` | `getByTestId(testId: string) => HTMLElement` | Query by data-testid `[SRC:code/core/src/test/index.ts:L43]` |
| `getByLabelText` | `getByLabelText(text: string | RegExp, options?) => HTMLElement` | Query by label `[SRC:code/core/src/test/index.ts:L44]` |
| `getByPlaceholderText` | `getByPlaceholderText(text: string | RegExp) => HTMLElement` | Query by placeholder `[SRC:code/core/src/test/index.ts:L45]` |
| `getByAltText` | `getByAltText(text: string | RegExp) => HTMLElement` | Query by alt text `[SRC:code/core/src/test/index.ts:L46]` |
| `getByTitle` | `getByTitle(text: string | RegExp) => HTMLElement` | Query by title attribute `[SRC:code/core/src/test/index.ts:L47]` |
| `getByDisplayValue` | `getByDisplayValue(value: string | RegExp) => HTMLElement` | Query by display value `[SRC:code/core/src/test/index.ts:L48]` |
| `findByRole` | `findByRole(role: string, options?) => Promise<HTMLElement>` | Async query by role `[SRC:code/core/src/test/index.ts:L50]` |
| `findByText` | `findByText(text: string | RegExp, options?) => Promise<HTMLElement>` | Async query by text `[SRC:code/core/src/test/index.ts:L51]` |
| `findByTestId` | `findByTestId(testId: string) => Promise<HTMLElement>` | Async query by testid `[SRC:code/core/src/test/index.ts:L52]` |
| `findByLabelText` | `findByLabelText(text: string | RegExp) => Promise<HTMLElement>` | Async query by label `[SRC:code/core/src/test/index.ts:L53]` |
| `queryByRole` | `queryByRole(role: string, options?) => HTMLElement | null` | Nullable query by role `[SRC:code/core/src/test/index.ts:L55]` |
| `queryByText` | `queryByText(text: string | RegExp) => HTMLElement | null` | Nullable query by text `[SRC:code/core/src/test/index.ts:L56]` |
| `queryByTestId` | `queryByTestId(testId: string) => HTMLElement | null` | Nullable query by testid `[SRC:code/core/src/test/index.ts:L57]` |
| `queryByLabelText` | `queryByLabelText(text: string | RegExp) => HTMLElement | null` | Nullable query by label `[SRC:code/core/src/test/index.ts:L58]` |
| `getAllByRole` | `getAllByRole(role: string, options?) => HTMLElement[]` | Query all by role `[SRC:code/core/src/test/index.ts:L60]` |
| `getAllByText` | `getAllByText(text: string | RegExp) => HTMLElement[]` | Query all by text `[SRC:code/core/src/test/index.ts:L61]` |
| `findAllByRole` | `findAllByRole(role: string, options?) => Promise<HTMLElement[]>` | Async query all by role `[SRC:code/core/src/test/index.ts:L63]` |
| `findAllByText` | `findAllByText(text: string | RegExp) => Promise<HTMLElement[]>` | Async query all by text `[SRC:code/core/src/test/index.ts:L64]` |
| `configure` | `configure(options: { testIdAttribute?: string }) => void` | Configure testing-library `[SRC:code/core/src/test/index.ts:L66]` |

#### userEvent Methods

| Method | Signature | Purpose |
|--------|-----------|---------|
| `userEvent.click` | `click(element: Element) => Promise<void>` | Simulate click `[SRC:code/core/src/test/index.ts:L31]` |
| `userEvent.dblClick` | `dblClick(element: Element) => Promise<void>` | Simulate double click |
| `userEvent.tripleClick` | `tripleClick(element: Element) => Promise<void>` | Simulate triple click |
| `userEvent.hover` | `hover(element: Element) => Promise<void>` | Simulate hover |
| `userEvent.unhover` | `unhover(element: Element) => Promise<void>` | Remove hover |
| `userEvent.tab` | `tab(options?: { shift?: boolean }) => Promise<void>` | Simulate tab key |
| `userEvent.keyboard` | `keyboard(text: string) => Promise<void>` | Simulate keyboard input |
| `userEvent.type` | `type(element: Element, text: string, options?) => Promise<void>` | Type text into element |
| `userEvent.clear` | `clear(element: Element) => Promise<void>` | Clear input element |
| `userEvent.selectOptions` | `selectOptions(element: Element, values: string[]) => Promise<void>` | Select dropdown options |
| `userEvent.upload` | `upload(element: Element, file: File) => Promise<void>` | Upload file |
| `userEvent.setup` | `setup(options?) => UserEvent` | Create new userEvent instance |

#### Type Exports

| Type | Purpose |
|------|---------|
| `Mock` | Mock function type `[SRC:code/core/src/test/index.ts:L70]` |
| `MockInstance` | Mock instance type |
| `Mocked<T>` | Type for mocked objects |
| `MockedFunction<T>` | Type for mocked functions |
| `MockedObject<T>` | Type for mocked objects |
| `SpyInstance` | Spy instance type |

### 2. storybook/actions

Action logging for component callbacks — appears in the Actions panel.

`[SRC:code/core/src/actions/index.ts:L1]`

| Export | Signature | Purpose |
|--------|-----------|---------|
| `action` | `action(name: string, options?: ActionOptions) => HandlerFunction` | Create named action logger `[SRC:code/core/src/actions/runtime.ts:L15]` |
| `actions` | `actions(...names: string[]) => Record<string, HandlerFunction>` | Create multiple action loggers `[SRC:code/core/src/actions/runtime.ts:L28]` |
| `configureActions` | `configureActions(options: ActionOptions) => void` | Configure action defaults `[SRC:code/core/src/actions/configureActions.ts:L4]` |
| `PARAM_KEY` | `'actions'` | Parameter key constant `[SRC:code/core/src/actions/constants.ts:L1]` |
| `ADDON_ID` | `'storybook/actions'` | Addon identifier `[SRC:code/core/src/actions/constants.ts:L2]` |
| `PANEL_ID` | `'storybook/actions/panel'` | Panel identifier `[SRC:code/core/src/actions/constants.ts:L3]` |
| `EVENT_ID` | `'storybook/actions/action-event'` | Event channel key `[SRC:code/core/src/actions/constants.ts:L4]` |

#### Types

| Type | Definition |
|------|------------|
| `ActionOptions` | `{ implicit?: boolean, id?: string, depth?: number, clearOnStoryChange?: boolean, limit?: number }` `[SRC:code/core/src/actions/types.ts:L1]` |
| `HandlerFunction` | `(...args: any[]) => void` `[SRC:code/core/src/actions/types.ts:L8]` |
| `ActionsFunction` | `(...args: string[]) => Record<string, HandlerFunction>` `[SRC:code/core/src/actions/types.ts:L10]` |
| `ActionDisplay` | `{ id: string, count: number, data: { name: string, args: any[] }, options: ActionOptions }` `[SRC:code/core/src/actions/types.ts:L12]` |

### 3. storybook/theming

Theme creation, styled-components utilities, and design tokens for Storybook UI customization.

`[SRC:code/core/src/theming/index.ts:L1]`

| Export | Signature | Purpose |
|--------|-----------|---------|
| `create` | `create(vars?: ThemeVarsPartial) => ThemeVars` | Create custom Storybook theme `[SRC:code/core/src/theming/create.ts:L38]` |
| `themes` | `{ light: ThemeVars, dark: ThemeVars, normal: ThemeVars }` | Built-in theme presets `[SRC:code/core/src/theming/themes.ts:L1]` |
| `convert` | `convert(inherit?: ThemeVarsPartial) => Theme` | Convert ThemeVars to full emotion Theme `[SRC:code/core/src/theming/convert.ts:L8]` |
| `ensure` | `ensure(input: ThemeVarsPartial) => Theme` | Ensure valid theme (with defaults) `[SRC:code/core/src/theming/ensure.ts:L4]` |
| `styled` | `styled: CreateStyled` | Emotion styled-component factory `[SRC:code/core/src/theming/index.ts:L5]` |
| `css` | `css: CSSFunction` | Emotion css tagged template `[SRC:code/core/src/theming/index.ts:L6]` |
| `Global` | `Global: FC<{ styles: Interpolation }>` | Emotion Global styles component `[SRC:code/core/src/theming/index.ts:L7]` |
| `keyframes` | `keyframes: KeyframesFunction` | Emotion keyframes helper `[SRC:code/core/src/theming/index.ts:L8]` |
| `ThemeProvider` | `ThemeProvider: FC<{ theme: Theme, children: ReactNode }>` | Emotion theme provider `[SRC:code/core/src/theming/index.ts:L9]` |
| `useTheme` | `useTheme() => Theme` | Hook to access current theme `[SRC:code/core/src/theming/index.ts:L10]` |
| `withTheme` | `withTheme(component: Component) => Component` | HOC to inject theme prop `[SRC:code/core/src/theming/index.ts:L11]` |
| `lighten` | `lighten(color: string, amount: number) => string` | Lighten a color value `[SRC:code/core/src/theming/utils.ts:L5]` |
| `darken` | `darken(color: string, amount: number) => string` | Darken a color value `[SRC:code/core/src/theming/utils.ts:L8]` |
| `createReset` | `createReset({ typography }: { typography: Typography }) => { [key: string]: { [key: string]: string \| number } }` | Generate CSS reset styles for Storybook preview (body font, box-sizing, heading/input normalization, code/pre formatting) `[SRC:code/core/src/theming/global.ts:L24]` |
| `createGlobal` | `createGlobal({ color, background, typography }: { color: Color; background: Background; typography: Typography }) => { [key: string]: { [key: string]: string \| number } }` | Create global Storybook CSS styles (body positioning, screen reader utilities, landmark focus, scroll smoothing) `[SRC:code/core/src/theming/global.ts:L94]` |
| `color` | `color: { ...colorTokens }` | Color design tokens `[SRC:code/core/src/theming/tokens/color.ts:L1]` |
| `background` | `background: { ...bgTokens }` | Background design tokens `[SRC:code/core/src/theming/tokens/background.ts:L1]` |
| `typography` | `typography: { ...typographyTokens }` | Typography design tokens `[SRC:code/core/src/theming/tokens/typography.ts:L1]` |

#### Types

| Type | Definition |
|------|------------|
| `ThemeVars` | Full theme variables interface (30+ properties) `[SRC:code/core/src/theming/types.ts:L1]` |
| `ThemeVarsPartial` | `Partial<ThemeVars>` — for `create()` input `[SRC:code/core/src/theming/types.ts:L35]` |
| `StorybookTheme` | Union: `ThemeVars & { [key: string]: any }` `[SRC:code/core/src/theming/types.ts:L38]` |
| `Theme` | Resolved emotion Theme object `[SRC:code/core/src/theming/types.ts:L40]` |

### 4. storybook/highlight

Story element highlighting via the addon channel. Used for visual testing and addon panel interactions.

`[SRC:code/core/src/highlight/index.ts:L1]`

| Export | Signature | Purpose |
|--------|-----------|---------|
| `HIGHLIGHT` | `'storybook/highlight/set'` | Event: highlight elements `[SRC:code/core/src/highlight/index.ts:L3]` |
| `REMOVE_HIGHLIGHT` | `'storybook/highlight/remove'` | Event: remove specific highlights `[SRC:code/core/src/highlight/index.ts:L4]` |
| `RESET_HIGHLIGHT` | `'storybook/highlight/reset'` | Event: clear all highlights `[SRC:code/core/src/highlight/index.ts:L5]` |
| `SCROLL_INTO_VIEW` | `'storybook/highlight/scroll'` | Event: scroll to highlighted element `[SRC:code/core/src/highlight/index.ts:L6]` |

#### Types

| Type | Definition |
|------|------------|
| `HighlightOptions` | `{ elements: string[], color?: string, style?: 'outline' \| 'filled' \| 'double', id?: string }` `[SRC:code/core/src/highlight/types.ts:L1]` |
| `HighlightMenuItem` | `{ id: string, title: string, elements: string[] }` `[SRC:code/core/src/highlight/types.ts:L8]` |
| `ClickEventDetails` | `{ nodeId: string, position: { x: number, y: number } }` `[SRC:code/core/src/highlight/types.ts:L12]` |

### 5. storybook/viewport

Viewport simulation presets for responsive testing.

`[SRC:code/core/src/viewport/index.ts:L1]`

| Export | Signature | Purpose |
|--------|-----------|---------|
| `INITIAL_VIEWPORTS` | `ViewportMap` (28 devices) | Full device preset map `[SRC:code/core/src/viewport/defaults.ts:L4]` |
| `MINIMAL_VIEWPORTS` | `ViewportMap` (4 sizes) | Mobile/tablet/desktop presets `[SRC:code/core/src/viewport/defaults.ts:L120]` |
| `DEFAULT_VIEWPORT` | `'responsive'` | Default viewport key `[SRC:code/core/src/viewport/defaults.ts:L135]` |

#### Devices in INITIAL_VIEWPORTS

`iphone5` (320x568), `iphone6` (375x667), `iphone6p` (414x736), `iphone8p` (414x736), `iphonex` (375x812), `iphonexr` (414x896), `iphonexsmax` (414x896), `iphone12mini` (375x812), `iphone12` (390x844), `iphone12promax` (428x926), `iphone14` (393x852), `iphone14promax` (430x932), `iphoneSE2` (375x667), `ipad` (768x1024), `ipad10p` (834x1112), `ipad12p` (1024x1366), `galaxys5` (360x640), `galaxys9` (360x740), `nexus5x` (412x732), `nexus6p` (412x732), `pixel` (540x960), `pixelxl` (720x1280), `kindle` (complex viewport), `responsive` (auto) — plus 4 MINIMAL: `mobile1` (320x568), `mobile2` (414x896), `tablet` (834x1112), `desktop` (1280x800).

`[SRC:code/core/src/viewport/defaults.ts:L4]`

#### Types

| Type | Definition |
|------|------------|
| `Viewport` | `{ name: string, styles: ViewportStyles, type?: ViewportType }` `[SRC:code/core/src/viewport/types.ts:L1]` |
| `ViewportMap` | `Record<string, Viewport>` `[SRC:code/core/src/viewport/types.ts:L6]` |
| `ViewportStyles` | `{ width: string, height: string }` `[SRC:code/core/src/viewport/types.ts:L8]` |
| `ViewportType` | `'desktop' \| 'tablet' \| 'mobile' \| 'other'` `[SRC:code/core/src/viewport/types.ts:L10]` |
| `ViewportParameters` | `{ viewports?: ViewportMap, defaultViewport?: string, disable?: boolean }` `[SRC:code/core/src/viewport/types.ts:L12]` |
| `ViewportGlobals` | `{ viewport?: { value?: string, isRotated?: boolean } }` `[SRC:code/core/src/viewport/types.ts:L18]` |

### 6. storybook/manager-api

Manager-side API for building custom addons, panels, and tools.

`[SRC:code/core/src/manager-api/index.ts:L1]`

#### Hooks

| Export | Signature | Purpose |
|--------|-----------|---------|
| `useStorybookApi` | `useStorybookApi() => API` | Access full manager API `[SRC:code/core/src/manager-api/index.ts:L12]` |
| `useStorybookState` | `useStorybookState() => State` | Access manager state `[SRC:code/core/src/manager-api/index.ts:L13]` |
| `useChannel` | `useChannel(events: Record<string, Function>, deps?: any[]) => Channel` | Subscribe to addon channel events `[SRC:code/core/src/manager-api/index.ts:L14]` |
| `useArgs` | `useArgs() => [Args, (newArgs: Args) => void, (argNames?: string[]) => void]` | Read/update story args from manager `[SRC:code/core/src/manager-api/index.ts:L15]` |
| `useGlobals` | `useGlobals() => [Globals, (newGlobals: Globals) => void]` | Read/update Storybook globals `[SRC:code/core/src/manager-api/index.ts:L16]` |
| `useParameter` | `useParameter<T>(name: string, defaultValue?: T) => T` | Read story parameter `[SRC:code/core/src/manager-api/index.ts:L17]` |
| `useSharedState` | `useSharedState<T>(key: string, initial?: T) => [T, (val: T) => void]` | Shared state between manager panels `[SRC:code/core/src/manager-api/index.ts:L18]` |
| `useAddonState` | `useAddonState<T>(addonId: string, initial?: T) => [T, (val: T) => void]` | Per-addon persistent state `[SRC:code/core/src/manager-api/index.ts:L19]` |

#### Registration

| Export | Signature | Purpose |
|--------|-----------|---------|
| `addons` | `addons: AddonStore` | Addon registration singleton `[SRC:code/core/src/manager-api/index.ts:L22]` |
| `addons.register` | `register(addonId: string, callback: (api: API) => void) => void` | Register an addon `[SRC:code/core/src/manager-api/lib/addons.ts:L45]` |
| `addons.add` | `add(panelId: string, panel: Addon) => void` | Add panel/tab/tool `[SRC:code/core/src/manager-api/lib/addons.ts:L60]` |
| `addons.setConfig` | `setConfig(config: ManagerConfig) => void` | Set manager configuration `[SRC:code/core/src/manager-api/lib/addons.ts:L75]` |
| `addons.getChannel` | `getChannel() => Channel` | Get addon communication channel `[SRC:code/core/src/manager-api/lib/addons.ts:L80]` |

#### Utilities

| Export | Signature | Purpose |
|--------|-----------|---------|
| `types` | `{ TAB, PANEL, TOOL, PREVIEW, NOTES_ELEMENT }` | Addon type constants `[SRC:code/core/src/manager-api/index.ts:L25]` |
| `ActiveTabs` | `{ SIDEBAR, CANVAS, ADDONS }` | Active tab constants `[SRC:code/core/src/manager-api/index.ts:L26]` |
| `Consumer` | `Consumer: FC<{ filter: (combo: Combo) => any, children: (data: any) => ReactNode }>` | Render prop consumer `[SRC:code/core/src/manager-api/index.ts:L28]` |
| `Provider` | `Provider: FC<ProviderProps>` | Manager context provider `[SRC:code/core/src/manager-api/index.ts:L29]` |
| `RequestResponseError` | `class RequestResponseError extends Error` | Channel request error `[SRC:code/core/src/manager-api/index.ts:L30]` |

#### Key Types

| Type | Definition |
|------|------------|
| `State` | Manager state: `{ storyId, viewMode, layout, addons, refs, storiesHash, ... }` `[SRC:code/core/src/manager-api/types.ts:L1]` |
| `API` | Manager API: `{ selectStory, setOptions, getUrlState, togglePanel, ... }` `[SRC:code/core/src/manager-api/types.ts:L25]` |
| `Combo` | `{ api: API, state: State }` `[SRC:code/core/src/manager-api/types.ts:L50]` |

### 7. storybook/preview-api

Preview-side API for decorators, hooks, and portable story composition.

`[SRC:code/core/src/preview-api/index.ts:L1]`

#### Hooks

| Export | Signature | Purpose |
|--------|-----------|---------|
| `useArgs` | `useArgs() => [Args, (newArgs: Args) => void, (argNames?: string[]) => void]` | Read/update args in preview `[SRC:code/core/src/preview-api/index.ts:L8]` |
| `useChannel` | `useChannel(events: Record<string, Function>, deps?: any[]) => Channel` | Subscribe to channel from preview `[SRC:code/core/src/preview-api/index.ts:L9]` |
| `useEffect` | `useEffect(callback: () => void | (() => void), deps?: any[]) => void` | Storybook-aware useEffect `[SRC:code/core/src/preview-api/index.ts:L10]` |
| `useGlobals` | `useGlobals() => [Globals, (newGlobals: Globals) => void]` | Read/update globals in preview `[SRC:code/core/src/preview-api/index.ts:L11]` |
| `useMemo` | `useMemo<T>(factory: () => T, deps: any[]) => T` | Storybook-aware useMemo `[SRC:code/core/src/preview-api/index.ts:L12]` |
| `useParameter` | `useParameter<T>(name: string, defaultValue?: T) => T` | Read story parameter `[SRC:code/core/src/preview-api/index.ts:L13]` |
| `useCallback` | `useCallback<T>(callback: T, deps: any[]) => T` | Storybook-aware useCallback `[SRC:code/core/src/preview-api/index.ts:L14]` |
| `useRef` | `useRef<T>(initialValue: T) => { current: T }` | Storybook-aware useRef `[SRC:code/core/src/preview-api/index.ts:L15]` |
| `useState` | `useState<T>(initial: T) => [T, (val: T) => void]` | Storybook-aware useState `[SRC:code/core/src/preview-api/index.ts:L16]` |
| `useStoryContext` | `useStoryContext() => StoryContext` | Access full story context `[SRC:code/core/src/preview-api/index.ts:L17]` |

#### Composition Utilities

| Export | Signature | Purpose |
|--------|-----------|---------|
| `composeStories` | `composeStories<T>(module: T, globalConfig?) => ComposedStories<T>` | Compose all stories from module `[SRC:code/core/src/preview-api/index.ts:L20]` |
| `composeStory` | `composeStory(story, meta, globalConfig?, defaultConfig?) => ComposedStoryFn` | Compose single story `[SRC:code/core/src/preview-api/index.ts:L21]` |
| `composeConfigs` | `composeConfigs(configs: ProjectAnnotations[]) => ProjectAnnotations` | Merge multiple configs `[SRC:code/core/src/preview-api/index.ts:L22]` |
| `setProjectAnnotations` | `setProjectAnnotations(config: ProjectAnnotations) => void` | Set global project config `[SRC:code/core/src/preview-api/index.ts:L23]` |
| `decorateStory` | `decorateStory(story: StoryFn, decorators: DecoratorFunction[]) => StoryFn` | Apply decorators to story `[SRC:code/core/src/preview-api/index.ts:L24]` |

#### Preview Classes

| Export | Signature | Purpose |
|--------|-----------|---------|
| `Preview` | `class Preview` | Base preview class `[SRC:code/core/src/preview-api/index.ts:L27]` |
| `PreviewWeb` | `class PreviewWeb extends Preview` | Web preview with router `[SRC:code/core/src/preview-api/index.ts:L28]` |
| `PreviewWithSelection` | `class PreviewWithSelection extends PreviewWeb` | Preview with story selection `[SRC:code/core/src/preview-api/index.ts:L29]` |
| `DocsContext` | `class DocsContext` | Docs-mode context provider `[SRC:code/core/src/preview-api/index.ts:L30]` |
| `DocsRender` | `class DocsRender` | Docs rendering helper `[SRC:code/core/src/preview-api/index.ts:L31]` |
| `StoryRender` | `class StoryRender` | Story rendering helper `[SRC:code/core/src/preview-api/index.ts:L32]` |
| `CsfDocsRender` | `class CsfDocsRender` | CSF docs rendering `[SRC:code/core/src/preview-api/index.ts:L33]` |

#### Simulation Utilities

| Export | Signature | Purpose |
|--------|-----------|---------|
| `simulatePageLoad` | `simulatePageLoad(element: HTMLElement) => void` | Simulate page load event `[SRC:code/core/src/preview-api/index.ts:L36]` |
| `simulateDOMContentLoaded` | `simulateDOMContentLoaded() => void` | Simulate DOMContentLoaded `[SRC:code/core/src/preview-api/index.ts:L37]` |

### 8. storybook/internal/types

Core CSF and framework types shared across all packages.

`[SRC:code/core/src/types/index.ts:L1]`

#### CSF Types

| Type | Definition |
|------|------------|
| `Args` | `Record<string, any>` — story arguments `[SRC:code/core/src/types/csf.ts:L8]` |
| `ArgTypes<TArgs>` | `{ [key in keyof TArgs]: InputType }` — arg type definitions `[SRC:code/core/src/types/csf.ts:L12]` |
| `Parameters` | `Record<string, any>` — story parameters `[SRC:code/core/src/types/csf.ts:L15]` |
| `StoryAnnotations<TRenderer, TArgs>` | Base story config: args, argTypes, decorators, loaders, play, render, tags `[SRC:code/core/src/types/csf.ts:L18]` |
| `ComponentAnnotations<TRenderer, TArgs>` | Meta-level config: component, title, subcomponents, argTypes, decorators `[SRC:code/core/src/types/csf.ts:L45]` |
| `ProjectAnnotations<TRenderer>` | Global config: decorators, parameters, argTypes, globalTypes, loaders `[SRC:code/core/src/types/csf.ts:L72]` |
| `StoryContext<TRenderer, TArgs>` | `{ args, argTypes, globals, parameters, viewMode, canvas, loaded, mount, step, ... }` `[SRC:code/core/src/types/csf.ts:L95]` |
| `StoryContextForLoaders<TRenderer, TArgs>` | Context available to loaders (before play) `[SRC:code/core/src/types/csf.ts:L110]` |
| `StoryContextForEnhancers<TRenderer, TArgs>` | Context for arg enhancers `[SRC:code/core/src/types/csf.ts:L115]` |
| `DecoratorFunction<TRenderer, TArgs>` | `(story: StoryFn, context: StoryContext) => StoryFnReturnType` `[SRC:code/core/src/types/csf.ts:L120]` |
| `LoaderFunction<TRenderer, TArgs>` | `(context: StoryContextForLoaders) => Promise<Record<string, any>>` `[SRC:code/core/src/types/csf.ts:L125]` |
| `PlayFunction<TRenderer, TArgs>` | `(context: StoryContext) => Promise<void> \| void` `[SRC:code/core/src/types/csf.ts:L130]` |
| `PlayFunctionContext<TRenderer, TArgs>` | Extended context with `canvas`, `canvasElement`, `step`, `userEvent` `[SRC:code/core/src/types/csf.ts:L133]` |
| `ArgsEnhancer<TRenderer, TArgs>` | `(context: StoryContextForEnhancers) => TArgs` `[SRC:code/core/src/types/csf.ts:L138]` |
| `ArgTypesEnhancer<TRenderer, TArgs>` | `(context: StoryContextForEnhancers) => ArgTypes` `[SRC:code/core/src/types/csf.ts:L141]` |
| `StepFunction<TRenderer, TArgs>` | `(label: string, play: PlayFunction) => Promise<void>` `[SRC:code/core/src/types/csf.ts:L145]` |
| `StepRunner<TRenderer, TArgs>` | `(label: string, play: PlayFunction, context: StoryContext) => Promise<void>` `[SRC:code/core/src/types/csf.ts:L148]` |
| `Globals` | `Record<string, any>` — global state `[SRC:code/core/src/types/csf.ts:L152]` |
| `GlobalTypes` | `Record<string, InputType>` — global input types `[SRC:code/core/src/types/csf.ts:L154]` |
| `InputType` | `{ name?: string, description?: string, defaultValue?: any, type?: SBType, control?: ControlType, options?: any[], table?: { ... }, if?: Conditional, mapping?: Record<string, any> }` `[SRC:code/core/src/types/csf.ts:L158]` |
| `SBType` | `{ name: 'string' \| 'number' \| 'boolean' \| 'function' \| 'symbol' \| 'other' \| 'enum' \| 'array' \| 'object' \| 'union' \| 'intersection', value?: any, required?: boolean, raw?: string }` `[SRC:code/core/src/types/csf.ts:L175]` |
| `ControlType` | `'boolean' \| 'number' \| 'range' \| 'object' \| 'file' \| 'radio' \| 'inline-radio' \| 'check' \| 'inline-check' \| 'select' \| 'multi-select' \| 'text' \| 'color' \| 'date'` `[SRC:code/core/src/types/csf.ts:L185]` |
| `Conditional` | `{ arg?: string, global?: string, exists?: boolean, eq?: any, neq?: any, truthy?: boolean }` `[SRC:code/core/src/types/csf.ts:L190]` |
| `Tag` | `string` — story tag for filtering (e.g., `'autodocs'`, `'test'`, `'!dev'`) `[SRC:code/core/src/types/csf.ts:L195]` |

#### Addon Types

| Type | Definition |
|------|------------|
| `Addon_TypesEnum` | `TAB \| PANEL \| TOOL \| PREVIEW \| NOTES_ELEMENT` `[SRC:code/core/src/types/addon.ts:L1]` |
| `Addon_Config` | `{ type: Addon_TypesEnum, title: string \| (() => string), id: string, route?: Function, match?: Function, render: FC, paramKey?: string, disabled?: boolean, hidden?: boolean }` `[SRC:code/core/src/types/addon.ts:L8]` |
| `Addon_Collection` | `Record<string, Addon_Config>` `[SRC:code/core/src/types/addon.ts:L20]` |
| `Addon_BaseType` | Base addon registration shape `[SRC:code/core/src/types/addon.ts:L22]` |
| `Addon_WrapperType` | Addon that wraps preview content `[SRC:code/core/src/types/addon.ts:L30]` |
| `Addon_SidebarBottomType` | Addon in sidebar footer `[SRC:code/core/src/types/addon.ts:L35]` |
| `Addon_SidebarTopType` | Addon in sidebar header `[SRC:code/core/src/types/addon.ts:L38]` |
| `Addon_PageType` | Full-page addon `[SRC:code/core/src/types/addon.ts:L41]` |

#### Story Index Types

| Type | Definition |
|------|------------|
| `StoryIndex` | `{ v: number, entries: Record<string, StoryIndexEntry> }` `[SRC:code/core/src/types/storyIndex.ts:L1]` |
| `StoryIndexEntry` | `{ type: 'story' \| 'docs', id: string, name: string, title: string, importPath: string, tags: Tag[] }` `[SRC:code/core/src/types/storyIndex.ts:L5]` |
| `IndexEntry` | Union of StoryIndexEntry and DocsIndexEntry `[SRC:code/core/src/types/storyIndex.ts:L12]` |

#### Status Types

| Type | Definition |
|------|------------|
| `StatusValue` | `'pending' \| 'success' \| 'error' \| 'warn' \| 'unknown'` `[SRC:code/core/src/types/status.ts:L1]` |
| `StatusObject` | `{ status: StatusValue, title?: string, description?: string, data?: any }` `[SRC:code/core/src/types/status.ts:L4]` |
| `StatusState` | `Record<string, Record<string, StatusObject>>` `[SRC:code/core/src/types/status.ts:L10]` |

#### Builder Types

| Type | Definition |
|------|------------|
| `Builder` | `{ start: (options: BuilderOptions) => Promise<void>, build: (options: BuilderOptions) => Promise<void>, bail: () => Promise<void>, getConfig: (options: BuilderOptions) => Promise<any> }` `[SRC:code/core/src/types/builder.ts:L1]` |
| `BuilderOptions` | `{ configDir: string, outputDir: string, configType: 'DEVELOPMENT' \| 'PRODUCTION', ... }` `[SRC:code/core/src/types/builder.ts:L10]` |

#### Renderer Type

| Type | Definition |
|------|------------|
| `Renderer` | `{ component: any, storyResult: any, canvasElement: HTMLElement, mount: (...args: any[]) => Promise<any> }` `[SRC:code/core/src/types/renderer.ts:L1]` |

### 9. storybook/internal/csf

CSF (Component Story Format) factory utilities and helpers.

`[SRC:code/core/src/csf/index.ts:L1]`

| Export | Signature | Purpose |
|--------|-----------|---------|
| `definePreview` | `definePreview<TRenderer>(config: PreviewConfig<TRenderer>) => Preview<TRenderer>` | CSF factory: type-safe preview configuration `[SRC:code/core/src/csf/definePreview.ts:L8]` |
| `definePreviewAddon` | `definePreviewAddon<TRenderer>(config: PreviewAddonConfig) => PreviewAddon<TRenderer>` | Define a preview addon configuration `[SRC:code/core/src/csf/definePreviewAddon.ts:L5]` |
| `isStory` | `isStory(exp: any) => boolean` | Check if export is a valid story `[SRC:code/core/src/csf/isStory.ts:L3]` |
| `isMeta` | `isMeta(exp: any) => boolean` | Check if export is valid meta `[SRC:code/core/src/csf/isMeta.ts:L3]` |
| `toId` | `toId(kind: string, name?: string) => string` | Generate story ID from title/name `[SRC:code/core/src/csf/toId.ts:L5]` |
| `storyNameFromExport` | `storyNameFromExport(key: string) => string` | Convert export name to story name `[SRC:code/core/src/csf/storyNameFromExport.ts:L3]` |
| `combineTags` | `combineTags(...tagSets: Tag[][]) => Tag[]` | Merge tag arrays with deduplication `[SRC:code/core/src/csf/combineTags.ts:L3]` |
| `sanitize` | `sanitize(str: string) => string` | Sanitize string for ID use `[SRC:code/core/src/csf/sanitize.ts:L3]` |
| `parseKind` | `parseKind(kind: string, options?: { rootSeparator?: string, groupSeparator?: string }) => { root: string, groups: string[] }` | Parse story kind hierarchy `[SRC:code/core/src/csf/parseKind.ts:L3]` |
| `includeConditionalArg` | `includeConditionalArg(argType: InputType, args: Args, globals: Globals) => boolean` | Evaluate conditional arg visibility `[SRC:code/core/src/csf/includeConditionalArg.ts:L5]` |
| `composeArgsEnhancers` | `composeArgsEnhancers(enhancers: ArgsEnhancer[]) => ArgsEnhancer` | Compose multiple arg enhancers `[SRC:code/core/src/csf/composeArgsEnhancers.ts:L3]` |

#### Types

| Type | Definition |
|------|------------|
| `Preview<TRenderer>` | `{ decorators, parameters, globalTypes, loaders, tags, addons, meta: (meta) => Meta }` `[SRC:code/core/src/csf/types.ts:L1]` |
| `Meta<TRenderer, TArgs>` | CSF factory meta: `{ component, title, decorators, args, argTypes, story: (story) => Story }` `[SRC:code/core/src/csf/types.ts:L15]` |
| `Story<TRenderer, TArgs>` | CSF factory story: `{ args, play, render, decorators, tags, name }` `[SRC:code/core/src/csf/types.ts:L30]` |
| `PreviewAddon<TRenderer>` | `{ decorators, parameters, initialGlobals, afterEach }` `[SRC:code/core/src/csf/types.ts:L40]` |
| `InferTypes<T>` | Infer renderer and args types from component `[SRC:code/core/src/csf/types.ts:L45]` |

### 10. @storybook/react-vite

React-Vite framework package — provides Vite-based Storybook configuration for React projects.

`[SRC:code/frameworks/react-vite/src/index.ts:L1]`

#### Main Exports

| Export | Signature | Purpose |
|--------|-----------|---------|
| `definePreview` | Re-export from `storybook/internal/csf` with ReactRenderer bound | CSF factory for React-Vite preview `[SRC:code/frameworks/react-vite/src/index.ts:L3]` |

#### Node Exports (@storybook/react-vite/node)

| Export | Signature | Purpose |
|--------|-----------|---------|
| `defineMain` | `defineMain(config: StorybookConfig) => StorybookConfig` | Type-safe main.ts configuration `[SRC:code/frameworks/react-vite/src/node/index.ts:L1]` |

#### Preset (@storybook/react-vite/preset)

| Export | Signature | Purpose |
|--------|-----------|---------|
| `core` | `{ builder: '@storybook/builder-vite', renderer: '@storybook/react' }` | Framework core config `[SRC:code/frameworks/react-vite/src/preset.ts:L5]` |
| `viteFinal` | `viteFinal(config: ViteConfig, options: Options) => Promise<ViteConfig>` | Vite config transformer (adds React plugins) `[SRC:code/frameworks/react-vite/src/preset.ts:L12]` |

#### Types

| Type | Definition |
|------|------------|
| `FrameworkOptions` | `{ strictMode?: boolean, legacyRootApi?: boolean, builder?: BuilderOptions }` `[SRC:code/frameworks/react-vite/src/types.ts:L1]` |
| `StorybookConfig` | Core StorybookConfig + `{ framework: { name: '@storybook/react-vite', options?: FrameworkOptions } }` `[SRC:code/frameworks/react-vite/src/types.ts:L8]` |

### 11. @storybook/react

React renderer — provides React-specific types, portable stories, and Playwright CT support.

`[SRC:code/renderers/react/src/index.ts:L1]`

#### Type Exports

| Export | Signature | Purpose |
|--------|-----------|---------|
| `ReactRenderer` | `{ component: ComponentType, storyResult: StoryFnReactReturnType, mount: (ui?) => Promise<Canvas> }` | React renderer interface `[SRC:code/renderers/react/src/types.ts:L12]` |
| `Meta<T>` | `ComponentAnnotations<ReactRenderer, ComponentProps<T>>` | React story metadata type `[SRC:code/renderers/react/src/public-types.ts:L29]` |
| `StoryObj<T>` | `StoryAnnotations<ReactRenderer, ComponentProps<T>>` | React story object type `[SRC:code/renderers/react/src/public-types.ts:L34]` |
| `StoryFn<T>` | `(args: ComponentProps<T>, context: StoryContext) => StoryFnReactReturnType` | Story function type `[SRC:code/renderers/react/src/public-types.ts:L38]` |
| `Decorator<T>` | `DecoratorFunction<ReactRenderer, ComponentProps<T>>` | React decorator type `[SRC:code/renderers/react/src/public-types.ts:L42]` |
| `Loader<T>` | `LoaderFunction<ReactRenderer, ComponentProps<T>>` | React loader type `[SRC:code/renderers/react/src/public-types.ts:L45]` |
| `StoryContext` | `StoryContext<ReactRenderer>` | React story context `[SRC:code/renderers/react/src/public-types.ts:L48]` |
| `Preview` | CSF factory Preview with ReactRenderer `[SRC:code/renderers/react/src/public-types.ts:L50]` |

#### Portable Stories

| Export | Signature | Purpose |
|--------|-----------|---------|
| `composeStories` | `composeStories<T>(module: T, globalConfig?) => ComposedStories<T>` | Compose all stories for portable testing `[SRC:code/renderers/react/src/portable-stories.ts:L18]` |
| `composeStory` | `composeStory(story, meta, globalConfig?, defaultConfig?) => ComposedStoryFn` | Compose single story `[SRC:code/renderers/react/src/portable-stories.ts:L12]` |
| `setProjectAnnotations` | `setProjectAnnotations(config: ProjectAnnotations<ReactRenderer>) => void` | Set global config for portable tests `[SRC:code/renderers/react/src/portable-stories.ts:L8]` |

#### CSF Factory Exports

| Export | Signature | Purpose |
|--------|-----------|---------|
| `__definePreview` | Internal definePreview for React `[SRC:code/renderers/react/src/csf-factory.ts:L5]` |
| `ReactPreview` | CSF factory preview class `[SRC:code/renderers/react/src/csf-factory.ts:L8]` |
| `ReactMeta` | CSF factory meta class `[SRC:code/renderers/react/src/csf-factory.ts:L12]` |
| `ReactStory` | CSF factory story class `[SRC:code/renderers/react/src/csf-factory.ts:L16]` |

#### Playwright CT (@storybook/react/experimental-playwright)

| Export | Signature | Purpose |
|--------|-----------|---------|
| `createTest` | `createTest(options?: { page: Page }) => TestType` | Create Playwright CT test with Storybook stories `[SRC:code/renderers/react/src/experimental-playwright.ts:L5]` |

### 12. @storybook/builder-vite

Vite integration builder — handles dev server and production builds.

`[SRC:code/builders/builder-vite/src/index.ts:L1]`

| Export | Signature | Purpose |
|--------|-----------|---------|
| `start` | `start(options: BuilderOptions) => Promise<{ close: () => Promise<void> }>` | Start Vite dev server `[SRC:code/builders/builder-vite/src/index.ts:L8]` |
| `build` | `build(options: BuilderOptions) => Promise<void>` | Run Vite production build `[SRC:code/builders/builder-vite/src/index.ts:L15]` |
| `bail` | `bail() => Promise<void>` | Abort running build `[SRC:code/builders/builder-vite/src/index.ts:L20]` |
| `getConfig` | `getConfig(options: BuilderOptions) => Promise<ViteConfig>` | Get resolved Vite config `[SRC:code/builders/builder-vite/src/index.ts:L22]` |
| `withoutVitePlugins` | `withoutVitePlugins(plugins: PluginOption[], names: string[]) => PluginOption[]` | Remove specific Vite plugins by name `[SRC:code/builders/builder-vite/src/utils/without-vite-plugins.ts:L3]` |
| `hasVitePlugins` | `hasVitePlugins(plugins: PluginOption[], names: string[]) => boolean` | Check if plugins exist by name `[SRC:code/builders/builder-vite/src/utils/has-vite-plugins.ts:L3]` |

#### Types

| Type | Definition |
|------|------------|
| `ViteBuilder` | `Builder & { getConfig: (options) => Promise<ViteConfig> }` `[SRC:code/builders/builder-vite/src/types.ts:L1]` |
| `ViteFinal` | `(config: ViteConfig, options: Options) => ViteConfig \| Promise<ViteConfig>` `[SRC:code/builders/builder-vite/src/types.ts:L5]` |
| `StorybookConfigVite` | StorybookConfig with `viteFinal` field `[SRC:code/builders/builder-vite/src/types.ts:L8]` |
| `BuilderOptions` | `{ configDir: string, outputDir: string, configType: 'DEVELOPMENT' \| 'PRODUCTION', cache?: boolean, quiet?: boolean, ... }` `[SRC:code/builders/builder-vite/src/types.ts:L12]` |

### 13. @storybook/addon-a11y

Accessibility testing addon powered by axe-core. Provides decorators, panel UI, and test-time assertions.

`[SRC:code/addons/a11y/src/index.ts:L1]`

#### Exports

| Export | Signature | Purpose |
|--------|-----------|---------|
| `ADDON_ID` | `'storybook/a11y'` | Addon identifier `[SRC:code/addons/a11y/src/constants.ts:L1]` |
| `PANEL_ID` | `'storybook/a11y/panel'` | Panel identifier `[SRC:code/addons/a11y/src/constants.ts:L2]` |
| `PARAM_KEY` | `'a11y'` | Parameter key `[SRC:code/addons/a11y/src/constants.ts:L3]` |

#### Preview Exports (@storybook/addon-a11y/preview)

| Export | Signature | Purpose |
|--------|-----------|---------|
| `decorators` | `DecoratorFunction[]` | A11y decorators for preview `[SRC:code/addons/a11y/src/preview.ts:L5]` |
| `afterEach` | `(context: StoryContext) => Promise<void>` | Run axe audit after each story render `[SRC:code/addons/a11y/src/preview.ts:L12]` |
| `initialGlobals` | `{ a11y: { active: true, manual: false } }` | Default a11y globals `[SRC:code/addons/a11y/src/preview.ts:L18]` |

#### Types

| Type | Definition |
|------|------------|
| `A11yParameters` | `{ element?: string, context?: RunOptions['context'], options?: RunOptions['options'], config?: Spec, disable?: boolean, test?: 'todo' \| 'error' \| 'warn' }` `[SRC:code/addons/a11y/src/types.ts:L1]` |
| `A11yGlobals` | `{ a11y?: { active?: boolean, manual?: boolean } }` `[SRC:code/addons/a11y/src/types.ts:L10]` |

#### Usage Pattern

```tsx
// Per-story a11y configuration
export const Accessible: Story = {
  parameters: {
    a11y: {
      config: { rules: [{ id: 'color-contrast', enabled: true }] },
      test: 'error',  // fail test on a11y violation
    },
  },
};

// Disable a11y for a story
export const NoA11y: Story = {
  parameters: { a11y: { disable: true } },
};
```

`[SRC:code/addons/a11y/src/types.ts:L1]`

### 14. @storybook/addon-docs

Documentation addon — provides automatic docs pages, MDX support, and doc blocks.

`[SRC:code/addons/docs/src/index.ts:L1]`

#### DocsRenderer

| Export | Signature | Purpose |
|--------|-----------|---------|
| `DocsRenderer` | `class DocsRenderer { render(context, docsParameter, element): Promise<void>, unmount(element): void }` | Renders docs pages `[SRC:code/addons/docs/src/DocsRenderer.tsx:L8]` |

#### Doc Blocks (@storybook/addon-docs/blocks)

| Export | Signature | Purpose |
|--------|-----------|---------|
| `Canvas` | `FC<{ of?: StoryAnnotations, sourceState?: 'shown' \| 'hidden' \| 'none', layout?: 'padded' \| 'centered' \| 'fullscreen', additionalActions?: Action[], className?: string }>` | Story canvas with source toggle `[SRC:code/addons/docs/src/blocks/Canvas.tsx:L12]` |
| `Meta` | `FC<{ of: ModuleExports, name?: string }>` | Docs page meta reference `[SRC:code/addons/docs/src/blocks/Meta.tsx:L8]` |
| `Story` | `FC<{ of: StoryAnnotations, meta?: ModuleExports, inline?: boolean, height?: string, autoplay?: boolean }>` | Embed story in docs `[SRC:code/addons/docs/src/blocks/Story.tsx:L10]` |
| `ArgTypes` | `FC<{ of?: StoryAnnotations \| ModuleExports, include?: string[], exclude?: string[], sort?: 'alpha' \| 'requiredFirst' \| 'none' }>` | Arg types table `[SRC:code/addons/docs/src/blocks/ArgTypes.tsx:L8]` |
| `Controls` | `FC<{ of?: StoryAnnotations \| ModuleExports, include?: string[], exclude?: string[], sort?: 'alpha' \| 'requiredFirst' \| 'none' }>` | Interactive controls panel `[SRC:code/addons/docs/src/blocks/Controls.tsx:L8]` |
| `Source` | `FC<{ of?: StoryAnnotations, code?: string, language?: string, dark?: boolean, format?: boolean \| 'dedent', type?: 'auto' \| 'code' \| 'dynamic' }>` | Source code display `[SRC:code/addons/docs/src/blocks/Source.tsx:L10]` |
| `DocsContainer` | `FC<{ context: DocsContextProps, theme?: ThemeVars, children: ReactNode }>` | Container for automatic docs page `[SRC:code/addons/docs/src/blocks/DocsContainer.tsx:L22]` |
| `DocsPage` | `FC<{}>` | Default auto-generated docs page `[SRC:code/addons/docs/src/blocks/DocsPage.tsx:L5]` |
| `Title` | `FC<{ of?: ModuleExports, children?: ReactNode }>` | Story title block `[SRC:code/addons/docs/src/blocks/Title.tsx:L5]` |
| `Subtitle` | `FC<{ of?: ModuleExports, children?: ReactNode }>` | Story subtitle block `[SRC:code/addons/docs/src/blocks/Subtitle.tsx:L5]` |
| `Description` | `FC<{ of?: StoryAnnotations \| ModuleExports, markdown?: string }>` | Component/story description `[SRC:code/addons/docs/src/blocks/Description.tsx:L8]` |
| `Primary` | `FC<{}>` | Render primary (first) story `[SRC:code/addons/docs/src/blocks/Primary.tsx:L5]` |
| `Stories` | `FC<{ includePrimary?: boolean, title?: string }>` | Render all stories `[SRC:code/addons/docs/src/blocks/Stories.tsx:L5]` |
| `Heading` | `FC<{ children: ReactNode }>` | Styled heading `[SRC:code/addons/docs/src/blocks/Heading.tsx:L3]` |
| `Subheading` | `FC<{ children: ReactNode }>` | Styled subheading `[SRC:code/addons/docs/src/blocks/Subheading.tsx:L3]` |
| `Markdown` | `FC<{ children: string, options?: MarkdownOptions }>` | Render markdown content `[SRC:code/addons/docs/src/blocks/Markdown.tsx:L5]` |
| `ColorPalette` | `FC<{ children: ReactNode }>` | Color palette container `[SRC:code/addons/docs/src/blocks/ColorPalette.tsx:L3]` |
| `ColorItem` | `FC<{ title: string, subtitle: string, colors: string[] \| Record<string, string> }>` | Individual color swatch `[SRC:code/addons/docs/src/blocks/ColorPalette.tsx:L8]` |
| `IconGallery` | `FC<{ children: ReactNode }>` | Icon gallery container `[SRC:code/addons/docs/src/blocks/IconGallery.tsx:L3]` |
| `IconItem` | `FC<{ name: string, children: ReactNode }>` | Individual icon display `[SRC:code/addons/docs/src/blocks/IconGallery.tsx:L8]` |
| `Typeset` | `FC<{ fontFamily: string, fontSizes: string[], fontWeight?: number, sampleText?: string }>` | Typography showcase `[SRC:code/addons/docs/src/blocks/Typeset.tsx:L3]` |
| `Unstyled` | `FC<{ children: ReactNode }>` | Remove docs styling `[SRC:code/addons/docs/src/blocks/Unstyled.tsx:L3]` |
| `Wrapper` | `FC<{ children: ReactNode }>` | Docs wrapper component `[SRC:code/addons/docs/src/blocks/Wrapper.tsx:L3]` |
| `ExternalDocs` | `FC<ExternalDocsProps>` | External docs page component `[SRC:code/addons/docs/src/blocks/ExternalDocs.tsx:L5]` |
| `ExternalDocsContainer` | `FC<ExternalDocsContainerProps>` | Container for external docs `[SRC:code/addons/docs/src/blocks/ExternalDocsContainer.tsx:L5]` |

#### Controls (internal)

| Export | Signature | Purpose |
|--------|-----------|---------|
| `BooleanControl` | `FC<{ name: string, value: boolean, onChange: (val: boolean) => void }>` | Boolean toggle control `[SRC:code/addons/docs/src/controls/Boolean.tsx:L5]` |
| `ColorControl` | `FC<{ name: string, value: string, onChange: (val: string) => void, presetColors?: string[] }>` | Color picker control `[SRC:code/addons/docs/src/controls/Color.tsx:L8]` |
| `NumberControl` | `FC<{ name: string, value: number, onChange: (val: number) => void, min?: number, max?: number, step?: number }>` | Number input control `[SRC:code/addons/docs/src/controls/Number.tsx:L5]` |
| `RangeControl` | `FC<{ name: string, value: number, onChange: (val: number) => void, min: number, max: number, step?: number }>` | Range slider control `[SRC:code/addons/docs/src/controls/Range.tsx:L5]` |
| `TextControl` | `FC<{ name: string, value: string, onChange: (val: string) => void, maxLength?: number }>` | Text input control `[SRC:code/addons/docs/src/controls/Text.tsx:L5]` |
| `ObjectControl` | `FC<{ name: string, value: any, onChange: (val: any) => void }>` | JSON object editor control `[SRC:code/addons/docs/src/controls/Object.tsx:L5]` |
| `SelectControl` | `FC<{ name: string, value: any, options: any[], onChange: (val: any) => void }>` | Select dropdown control `[SRC:code/addons/docs/src/controls/Select.tsx:L5]` |
| `FilesControl` | `FC<{ name: string, value: string[], onChange: (val: string[]) => void, accept?: string }>` | File upload control `[SRC:code/addons/docs/src/controls/Files.tsx:L5]` |
| `DateControl` | `FC<{ name: string, value: Date, onChange: (val: Date) => void }>` | Date picker control `[SRC:code/addons/docs/src/controls/Date.tsx:L5]` |

#### Hooks

| Export | Signature | Purpose |
|--------|-----------|---------|
| `useOf` | `useOf(moduleExportOrMeta: any, validTypes?: string[]) => ResolvedOf` | Resolve story/meta from `of` prop `[SRC:code/addons/docs/src/blocks/useOf.ts:L8]` |

### 15. @storybook/addon-themes

Theme switching addon — supports CSS class, data attribute, and JSX provider strategies.

`[SRC:code/addons/themes/src/index.ts:L1]`

#### Decorators

| Export | Signature | Purpose |
|--------|-----------|---------|
| `withThemeByClassName` | `withThemeByClassName(config: { themes: Record<string, string>, defaultTheme: string, parentSelector?: string }) => DecoratorFunction` | Theme switching via CSS class on body/root `[SRC:code/addons/themes/src/decorators/class-name.ts:L8]` |
| `withThemeByDataAttribute` | `withThemeByDataAttribute(config: { themes: Record<string, string>, defaultTheme: string, attributeName?: string, parentSelector?: string }) => DecoratorFunction` | Theme switching via data attribute `[SRC:code/addons/themes/src/decorators/data-attribute.ts:L8]` |
| `withThemeFromJSXProvider` | `withThemeFromJSXProvider(config: { themes: Record<string, any>, defaultTheme: string, Provider?: ComponentType, GlobalStyles?: ComponentType }) => DecoratorFunction` | Theme switching via JSX context provider `[SRC:code/addons/themes/src/decorators/jsx-provider.ts:L8]` |

#### DecoratorHelpers

| Export | Signature | Purpose |
|--------|-----------|---------|
| `DecoratorHelpers.pluckThemeFromContext` | `pluckThemeFromContext(context: StoryContext) => string` | Extract selected theme from story context `[SRC:code/addons/themes/src/decorators/helpers.ts:L5]` |
| `DecoratorHelpers.useThemeParameters` | `useThemeParameters() => { themeOverride?: string }` | Read theme override from parameters `[SRC:code/addons/themes/src/decorators/helpers.ts:L12]` |
| `DecoratorHelpers.initializeThemeState` | `initializeThemeState(themes: string[], defaultTheme: string) => void` | Set up initial theme state `[SRC:code/addons/themes/src/decorators/helpers.ts:L18]` |

#### Types

| Type | Definition |
|------|------------|
| `ThemesGlobals` | `{ theme?: string }` `[SRC:code/addons/themes/src/types.ts:L1]` |
| `ThemesParameters` | `{ themeOverride?: string, disable?: boolean }` `[SRC:code/addons/themes/src/types.ts:L4]` |

#### Usage Pattern

```tsx
// .storybook/preview.ts — CSS class strategy
import { withThemeByClassName } from '@storybook/addon-themes';

export const decorators = [
  withThemeByClassName({
    themes: { light: 'light-theme', dark: 'dark-theme' },
    defaultTheme: 'light',
  }),
];

// JSX Provider strategy (e.g., styled-components, MUI)
import { withThemeFromJSXProvider } from '@storybook/addon-themes';
import { ThemeProvider } from 'styled-components';
import { lightTheme, darkTheme } from '../src/themes';

export const decorators = [
  withThemeFromJSXProvider({
    themes: { light: lightTheme, dark: darkTheme },
    defaultTheme: 'light',
    Provider: ThemeProvider,
  }),
];
```

`[SRC:code/addons/themes/src/decorators/class-name.ts:L8]`

### 16. @storybook/addon-vitest

Vitest plugin for running Storybook stories as tests.

`[SRC:code/addons/vitest/src/index.ts:L1]`

#### Main Export

| Export | Signature | Purpose |
|--------|-----------|---------|
| `storybookTest` | `storybookTest(options?: UserOptions) => VitePlugin` | Vitest plugin that transforms stories into tests `[SRC:code/addons/vitest/src/vitest-plugin/index.ts:L28]` |

#### Constants

| Export | Value | Purpose |
|--------|-------|---------|
| `ADDON_ID` | `'storybook/addon-vitest'` | Addon identifier `[SRC:code/addons/vitest/src/constants.ts:L1]` |
| `TEST_PROVIDER_ID` | `'storybook/addon-vitest/test-provider'` | Test provider ID `[SRC:code/addons/vitest/src/constants.ts:L2]` |

#### Types

| Type | Definition |
|------|------------|
| `UserOptions` | `{ configDir?: string, storybookScript?: string, storybookUrl?: string, tags?: { include?: string[], exclude?: string[], skip?: string[] }, disableAddonDocs?: boolean }` `[SRC:code/addons/vitest/src/vitest-plugin/index.ts:L12]` |

#### Usage Pattern

```ts
// vitest.config.ts
import { defineConfig } from 'vitest/config';
import { storybookTest } from '@storybook/addon-vitest/vitest-plugin';

export default defineConfig({
  plugins: [storybookTest()],
  test: {
    name: 'storybook',
    browser: {
      enabled: true,
      headless: true,
      name: 'chromium',
      provider: 'playwright',
    },
    setupFiles: ['.storybook/vitest.setup.ts'],
  },
});
```

```ts
// .storybook/vitest.setup.ts
import { setProjectAnnotations } from '@storybook/react';
import * as previewAnnotations from './.storybook/preview';

setProjectAnnotations([previewAnnotations]);
```

`[SRC:code/addons/vitest/src/vitest-plugin/index.ts:L28]`

---

