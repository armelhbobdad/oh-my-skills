## Full Type Definitions

### ThemeVars (complete)

```ts
interface ThemeVars {
  base: 'light' | 'dark';

  // Brand
  brandTitle?: string;
  brandUrl?: string;
  brandImage?: string;
  brandTarget?: '_self' | '_blank';

  // Colors
  colorPrimary: string;
  colorSecondary: string;

  // App chrome
  appBg: string;
  appContentBg: string;
  appPreviewBg: string;
  appBorderColor: string;
  appBorderRadius: number;

  // Typography
  fontBase: string;
  fontCode: string;

  // Text
  textColor: string;
  textInverseColor: string;
  textMutedColor: string;

  // Toolbar
  barTextColor: string;
  barHoverColor: string;
  barSelectedColor: string;
  barBg: string;

  // Controls
  buttonBg: string;
  buttonBorder: string;
  booleanBg: string;
  booleanSelectedBg: string;
  inputBg: string;
  inputBorder: string;
  inputTextColor: string;
  inputBorderRadius: number;

  // Grid
  gridCellSize: number;
}
```

`[SRC:code/core/src/theming/types.ts:L1]`

### StoryContext (complete)

```ts
interface StoryContext<TRenderer extends Renderer = Renderer, TArgs = Args> {
  id: string;
  name: string;
  title: string;
  kind: string;  // alias for title
  story: string;  // alias for name

  // Data
  args: TArgs;
  argTypes: ArgTypes<TArgs>;
  globals: Globals;
  parameters: Parameters;
  initialArgs: TArgs;

  // UI
  viewMode: 'story' | 'docs';
  abortSignal: AbortSignal;
  canvasElement: HTMLElement;
  canvas: ReturnType<typeof within>;  // scoped queries

  // Lifecycle
  loaded: Record<string, any>;  // loader results
  mount: TRenderer['mount'];
  step: StepFunction<TRenderer, TArgs>;
  context: StoryContext<TRenderer, TArgs>;  // self-reference

  // Testing
  userEvent: UserEvent;
  tags: Tag[];
  reporting: { addReport: (report: Report) => void };

  // Hooks
  hooks: HooksContext<TRenderer>;
  originalStoryFn: StoryFn<TRenderer>;
  undecoratedStoryFn: StoryFn<TRenderer>;
  unboundStoryFn: StoryFn<TRenderer>;
  componentId: string;
  moduleExport: ModuleExport;
}
```

`[SRC:code/core/src/types/csf.ts:L95]`

### A11yParameters (complete)

```ts
interface A11yParameters {
  /** CSS selector for the element to audit (default: '#storybook-root') */
  element?: string;
  /** axe-core context configuration */
  context?: RunOptions['context'];
  /** axe-core run options */
  options?: RunOptions['options'];
  /** axe-core Spec configuration */
  config?: Spec;
  /** Disable a11y checks entirely for this story */
  disable?: boolean;
  /** Test behavior: 'todo' = warn, 'error' = fail test, 'warn' = soft warning */
  test?: 'todo' | 'error' | 'warn';
}
```

`[SRC:code/addons/a11y/src/types.ts:L1]`

### StorybookConfig (react-vite, complete)

```ts
interface StorybookConfig {
  stories: StoriesEntry[];
  addons?: AddonEntry[];
  framework: {
    name: '@storybook/react-vite';
    options?: {
      strictMode?: boolean;
      legacyRootApi?: boolean;
      builder?: {
        viteConfigPath?: string;
        lazyCompilation?: boolean;
      };
    };
  };
  docs?: {
    autodocs?: boolean | 'tag';
    defaultName?: string;
  };
  typescript?: {
    check?: boolean;
    reactDocgen?: 'react-docgen' | 'react-docgen-typescript' | false;
    reactDocgenTypescriptOptions?: Record<string, any>;
  };
  staticDirs?: (string | { from: string; to: string })[];
  viteFinal?: (config: ViteConfig, options: Options) => ViteConfig | Promise<ViteConfig>;
  core?: {
    disableTelemetry?: boolean;
    enableCrashReports?: boolean;
  };
  features?: Record<string, boolean>;
  env?: (config: Record<string, string>) => Record<string, string>;
  refs?: Record<string, { title: string; url: string }>;
  logLevel?: 'silly' | 'verbose' | 'info' | 'warn' | 'error' | 'silent';
  build?: {
    test?: {
      disabledAddons?: string[];
      disableBlocks?: boolean;
      disableAutoDocs?: boolean;
      disableMDXEntries?: boolean;
      disableDocgen?: boolean;
    };
  };
}

type StoriesEntry = string | {
  directory: string;
  files?: string;
  titlePrefix?: string;
};

type AddonEntry = string | {
  name: string;
  options?: Record<string, any>;
};
```

`[SRC:code/frameworks/react-vite/src/types.ts:L1]`
`[SRC:code/core/src/types/config.ts:L1]`

### UserOptions (addon-vitest, complete)

```ts
interface UserOptions {
  /** Path to Storybook config directory (default: '.storybook') */
  configDir?: string;
  /** Shell command to start Storybook (for automatic startup) */
  storybookScript?: string;
  /** URL of running Storybook instance */
  storybookUrl?: string;
  /** Tag-based filtering for story tests */
  tags?: {
    /** Tags that must be present on a story for it to be tested (default: ['test']) */
    include?: string[];
    /** Tags that exclude a story from testing */
    exclude?: string[];
    /** Tags that skip a story (mark as todo) */
    skip?: string[];
  };
  /** Disable addon-docs entries in test file generation */
  disableAddonDocs?: boolean;
}
```

`[SRC:code/addons/vitest/src/vitest-plugin/index.ts:L12]`

### ReactRenderer (complete)

```ts
interface ReactRenderer extends Renderer {
  component: ComponentType<any>;
  storyResult: StoryFnReactReturnType;
  mount: (ui?: JSX.Element) => Promise<Canvas>;
  canvasElement: HTMLElement;
}

type StoryFnReactReturnType = JSX.Element | null;
type Canvas = ReturnType<typeof within>;
```

`[SRC:code/renderers/react/src/types.ts:L12]`

### InputType (complete)

```ts
interface InputType {
  name?: string;
  description?: string;
  defaultValue?: any;
  type?: SBType;
  control?: ControlType | { type: ControlType; [key: string]: any } | false;
  options?: any[];
  mapping?: Record<string, any>;
  if?: Conditional;
  table?: {
    type?: { summary?: string; detail?: string };
    defaultValue?: { summary?: string; detail?: string };
    category?: string;
    subcategory?: string;
    disable?: boolean;
    readonly?: boolean;
  };
}
```

`[SRC:code/core/src/types/csf.ts:L158]`

### DecoratorFunction (complete)

```ts
type DecoratorFunction<TRenderer extends Renderer = Renderer, TArgs = Args> = (
  story: StoryFn<TRenderer, TArgs>,
  context: StoryContext<TRenderer, TArgs>
) => TRenderer['storyResult'];
```

`[SRC:code/core/src/types/csf.ts:L120]`

### PlayFunction (complete)

```ts
type PlayFunction<TRenderer extends Renderer = Renderer, TArgs = Args> = (
  context: PlayFunctionContext<TRenderer, TArgs>
) => Promise<void> | void;

interface PlayFunctionContext<TRenderer extends Renderer = Renderer, TArgs = Args>
  extends StoryContext<TRenderer, TArgs> {
  canvas: ReturnType<typeof within>;
  canvasElement: HTMLElement;
  step: StepFunction<TRenderer, TArgs>;
  userEvent: UserEvent;
}
```

`[SRC:code/core/src/types/csf.ts:L130]`

---

