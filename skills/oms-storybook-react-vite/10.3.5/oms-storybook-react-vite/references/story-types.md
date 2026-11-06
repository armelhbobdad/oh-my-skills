# CSF Story Types — Full Type Definitions

This reference captures the full generic signatures for CSF types defined in `@storybook/react` (renderer) and re-exported by `@storybook/react-vite` (framework). All T1 from `code/renderers/react/src/public-types.ts` and `code/core/src/types/index.ts`.

## Contents

- [Import source resolution](#import-source-resolution) — where to import from
- [`Preview`](#preview) — `.storybook/preview.ts` default export type
- [`Meta<T>`](#metat) — component metadata type
- [`StoryObj<T>`](#storyobjt) — CSF3 story object type
- [`StoryFn<T>`](#storyfnt) — CSF2 story function type
- [`Decorator<T>`](#decoratort) — story decorator function
- [`Loader<T>`](#loadert) — async data loader
- [`StoryContext<T>`](#storycontextt) — context passed to play/render
- [`ReactRenderer`](#reactrenderer) — renderer type param
- [`Args`, `ArgTypes`, `Parameters`, `StrictArgs`](#args-argtypes-parameters-strictargs) — re-exported base types
- [Portable stories utilities](#portable-stories-utilities) — `composeStory`, `composeStories`, `setProjectAnnotations`
- [CSF4 factory API](#csf4-factory-api) — `__definePreview`, `ReactPreview`, `ReactMeta`, `ReactStory`

## Import source resolution

**For story files, prefer `@storybook/react-vite`:**

```ts
import type { Meta, StoryObj, Decorator, Parameters } from '@storybook/react-vite';
```

This package re-exports every CSF type from `@storybook/react` and adds framework-specific types (`StorybookConfig`, `FrameworkOptions`). Framework-aligned imports make intent explicit and let you swap frameworks (e.g., `@storybook/nextjs-vite`) without changing story code structure. `[AST:code/frameworks/react-vite/src/index.ts:L1]`

**Importing from `@storybook/react` is also valid** — the types are physically defined there, and this form is common in the Storybook repo's own template stories. `[AST:code/renderers/react/template/stories/decorators.stories.tsx:L3]`

**Do NOT import CSF types from `storybook/internal/types`** — that path exists but is an internal re-export aimed at non-React renderers. For React authoring, use `@storybook/react-vite` or `@storybook/react`.

## `Preview`

Type for `.storybook/preview.ts` default export.

```ts
// code/renderers/react/src/public-types.ts:80
export type Preview = ProjectAnnotations<ReactRenderer>;
```

`ProjectAnnotations<R>` here is the `storybook/internal/types` interface (`types/modules/story.ts:43`), which extends CSF's `ProjectAnnotations` (re-exported from `storybook/internal/types` as `BaseProjectAnnotations`) with two renderer hooks. Every field is optional: the `BaseAnnotations` ones (`decorators`, `parameters`, `args`, `argTypes`, `loaders`, `beforeEach`, `afterEach`, `render`, `tags`, `mount`), CSF's project-level ones (`argsEnhancers`, `argTypesEnhancers`, `beforeAll`, `initialGlobals`, `globalTypes`, `applyDecorators`, `runStep`) and the interface's own `testingLibraryRender` and `renderToCanvas`. `[AST:code/renderers/react/src/public-types.ts:L80]` `[AST:code/core/src/types/modules/story.ts:L43]` `[AST:code/core/src/csf/story.ts:L421]` `[AST:code/core/src/csf/story.ts:L347]`

**Usage:**
```ts
import type { Preview } from '@storybook/react-vite';
const preview: Preview = { parameters: {}, decorators: [], tags: ['autodocs'] };
export default preview;
```

## `Meta<T>`

```ts
// code/renderers/react/src/public-types.ts:29-31
export type Meta<TCmpOrArgs = Args> = [TCmpOrArgs] extends [ComponentType<any>]
  ? ComponentAnnotations<ReactRenderer, ComponentProps<TCmpOrArgs>>
  : ComponentAnnotations<ReactRenderer, TCmpOrArgs>;
```

Metadata to configure stories for a component. When passed a component, infers `args` from `ComponentProps<T>`; otherwise uses the provided args type directly.

**The `satisfies` vs `as` choice:**

```ts
// PREFERRED — use `satisfies` so `meta.args` retains literal types for StoryObj<typeof meta>
const meta = { component: Button, args: { label: 'x' } } satisfies Meta<typeof Button>;

// Older pattern — still valid but loses narrow arg types
const meta: Meta<typeof Button> = { component: Button, args: { label: 'x' } };
const meta2 = { component: Button } as Meta<typeof Button>;
```

`ComponentAnnotations<R, Args>` — the underlying interface — has these fields, all optional: its own `title`, `id`, `includeStories`, `excludeStories`, `component`, `subcomponents`, `play`, `globals`, and the `BaseAnnotations` ones, `decorators`, `parameters`, `args`, `argTypes`, `loaders`, `beforeEach`, `afterEach`, `render`, `tags`, `mount`. `beforeAll` is not one of them: it is a `ProjectAnnotations` field, set in `preview.ts`. Field-level docs live in `code/core/src/csf/story.ts`, which declares the interface (`code/core/src/types/modules/csf.ts` only re-exports it). `[AST:code/core/src/csf/story.ts:L452]` `[AST:code/core/src/csf/story.ts:L347]` `[SRC:code/core/src/csf/story.ts:L442]`

## `StoryObj<T>`

```ts
// code/renderers/react/src/public-types.ts:47-66
export type StoryObj<TMetaOrCmpOrArgs = Args> = [TMetaOrCmpOrArgs] extends [
  { render?: ArgsStoryFn<ReactRenderer, any>; component?: infer Component; args?: infer DefaultArgs }
]
  ? Simplify<
      (Component extends ComponentType<any> ? ComponentProps<Component> : unknown) &
      ArgsFromMeta<ReactRenderer, TMetaOrCmpOrArgs>
    > extends infer TArgs
    ? StoryAnnotations<ReactRenderer, AddMocks<TArgs, DefaultArgs>, SetOptional<TArgs, keyof TArgs & keyof DefaultArgs>>
    : never
  : TMetaOrCmpOrArgs extends ComponentType<any>
    ? StoryAnnotations<ReactRenderer, ComponentProps<TMetaOrCmpOrArgs>>
    : StoryAnnotations<ReactRenderer, TMetaOrCmpOrArgs>;
```

The CSF3 story object type. Three overload paths:
1. **Meta-aware:** pass `typeof meta` — args are inferred from the meta's `component` and narrowed by its `args` (via `AddMocks` + `SetOptional`). This is the **preferred v10 pattern**.
2. **Component-aware:** pass `typeof Component` — args are `ComponentProps<Component>`.
3. **Raw args:** pass an args type directly.

`StoryAnnotations<R, Args, RequiredArgs>` has these fields: the `BaseAnnotations` ones (`decorators`, `parameters`, `args`, `argTypes`, `loaders`, `beforeEach`, `afterEach`, `render`, `tags`, `mount`) and its own `name`, `storyName`, `play`, `globals`, `story`. All are optional except `args`, which is required when `RequiredArgs` has a required member (the component args the meta does not supply). Same shape as meta minus `title`/`id`/`component`/`subcomponents`/`includeStories`/`excludeStories`, plus `name`, `storyName` and `story`. `[AST:code/core/src/csf/story.ts:L543]`

**Canonical v10 story file:**
```ts
import type { Meta, StoryObj } from '@storybook/react-vite';
import { Button } from './Button';

const meta = { component: Button, args: { label: 'x' } } satisfies Meta<typeof Button>;
export default meta;
type Story = StoryObj<typeof meta>;

export const Primary: Story = { args: { label: 'Click me' } };
```

`[AST:code/renderers/react/src/public-types.ts:L47]`

## `StoryFn<T>`

```ts
// code/renderers/react/src/public-types.ts
export type StoryFn<TCmpOrArgs = Args> = [TCmpOrArgs] extends [ComponentType<any>]
  ? AnnotatedStoryFn<ReactRenderer, ComponentProps<TCmpOrArgs>>
  : AnnotatedStoryFn<ReactRenderer, TCmpOrArgs>;
```

The **CSF2** story function type. Still exported for backwards compat and for stories that need a function form (e.g., `useState` directly in the story body, without going through `render`). In v10, prefer `StoryObj` + `render` unless you specifically need CSF2 semantics.

## `Decorator<T>`

```ts
// code/renderers/react/src/public-types.ts
export type Decorator<TArgs = StrictArgs> = DecoratorFunction<ReactRenderer, TArgs>;
```

Function signature (from `DecoratorFunction<R, Args>`):
```ts
(storyFn: PartialStoryFn<R, Args>, context: StoryContext<R, Args>) => R['storyResult'];
```

For React: returns `ReactNode`. A decorator wraps the story — it receives a function that renders the next decorator (or the story) and the full story context.

**Usage:**
```ts
import type { Decorator } from '@storybook/react-vite';

const withPadding: Decorator = (Story) => <div style={{ padding: 16 }}><Story /></div>;
```

## `Loader<T>`

```ts
export type Loader<TArgs = StrictArgs> = LoaderFunction<ReactRenderer, TArgs>;
```

Async function called before a story renders. Returns an object merged into the story context's `loaded` field. Used for fetching data, mocking API state, seeding fixtures. `[AST:code/renderers/react/src/public-types.ts]`

## `StoryContext<T>`

```ts
export type StoryContext<TArgs = StrictArgs> = GenericStoryContext<ReactRenderer, TArgs>;
```

The full context object passed to `play`, `render`, `loaders`, and decorators. `GenericStoryContext` is CSF's `StoryContext` interface, whose fields are: from `StoryIdentifier`, `componentId`, `title`, `kind` (deprecated), `id`, `name`, `story` (deprecated), `tags`; from `StoryContextForEnhancers`, `component?`, `subcomponents?`, `parameters`, `initialArgs`, `argTypes`; from `Required<StoryContextUpdate>`, `args`, `globals` (plus its `[key: string]: any` index signature); and its own `loaded`, `abortSignal`, `canvasElement`, `hooks`, `originalStoryFn`, `viewMode`, `step`, `context`, `canvas` (testing-library query object), `mount` (for component testing), `reporting`. Importing `storybook/test` adds `userEvent` by module augmentation. There is no `playUntil` field: that is instrumenter state for the interaction debugger, not story context. `[AST:code/renderers/react/src/public-types.ts:L79]` `[AST:code/core/src/csf/story.ts:L268]` `[AST:code/core/src/csf/story.ts:L18]` `[SRC:code/core/src/test/index.ts:L19]`

## `ReactRenderer`

The renderer type parameter for React. It binds `storyResult` to `ReactNode`, `canvasElement` to `HTMLElement`, etc. Exported for users who need to type generic helpers but rarely referenced in story files. `[AST:code/renderers/react/src/types.ts]`

## `Args`, `ArgTypes`, `Parameters`, `StrictArgs`

```ts
// Re-exported from storybook/internal/types (declared in code/core/src/csf/story.ts)
interface Args { [name: string]: any }
interface StrictArgs { [name: string]: unknown }
type ArgTypes<TArgs = Args> = { [name in keyof TArgs]: InputType };
interface Parameters { [name: string]: any }
```

`Args` is the loose form used for backward compatibility. `StrictArgs` is used inside generic decorators where arg types are not known. `ArgTypes` describes the control schema (input type, options, description, default) per arg; its mapped keys are not optional, so the `argTypes` annotation of a meta or story takes `Partial<ArgTypes<TArgs>>`. `Parameters` is a free-form config bag keyed by addon name (e.g., `parameters.a11y`, `parameters.docs`, `parameters.viewport`). `[AST:code/renderers/react/src/public-types.ts:L21]` `[AST:code/core/src/csf/story.ts:L153]` `[AST:code/core/src/csf/story.ts:L157]` `[AST:code/core/src/csf/story.ts:L162]` `[AST:code/core/src/csf/story.ts:L32]`

## Portable stories utilities

**Canonical import path:** these symbols are **defined** in `code/renderers/react/src/portable-stories.tsx` (the renderer package) and re-exported from `@storybook/react` (`code/renderers/react/src/index.ts:5`) and `@storybook/react-vite` (`code/frameworks/react-vite/src/index.ts:1`). For story-authoring code on a React+Vite project, prefer `import { composeStories, setProjectAnnotations } from '@storybook/react-vite'` — framework-aligned and stable across renderer upgrades. `storybook/preview-api` does not re-export these: its `composeStory`, `composeStories` and `setProjectAnnotations` are core's renderer-agnostic functions (`code/core/src/preview-api/index.ts:51-62`), with different signatures (see `core-api.md`), meant for non-renderer infrastructure code.

```ts
// code/renderers/react/src/portable-stories.tsx:46
export function setProjectAnnotations(
  projectAnnotations: NamedOrDefaultProjectAnnotations<any> | NamedOrDefaultProjectAnnotations<any>[]
): NormalizedProjectAnnotations<ReactRenderer>;

// code/renderers/react/src/portable-stories.tsx:106
export function composeStory<TArgs extends Args = Args>(
  story: StoryAnnotationsOrFn<ReactRenderer, TArgs>,
  componentAnnotations: Meta<TArgs | any>,
  projectAnnotations?: ProjectAnnotations<ReactRenderer>,
  exportsName?: string
): ComposedStoryFn<ReactRenderer, Partial<TArgs>>;

// code/renderers/react/src/portable-stories.tsx:148
export function composeStories<TModule extends Store_CSFExports<ReactRenderer, any>>(
  csfExports: TModule,
  projectAnnotations?: ProjectAnnotations<ReactRenderer>
): Omit<StoriesWithPartialProps<ReactRenderer, TModule>, keyof Store_CSFExports>;
// `Store_CSFExports` is the internal CSF module shape — narrows `TModule` to a
// real story module (default meta + named story exports) rather than any object
// with a `default: Meta`. The `Omit` key is `keyof Store_CSFExports` (not
// `keyof TModule`) so only the CSF bookkeeping fields are stripped from the
// returned object while the story names are preserved.

export const INTERNAL_DEFAULT_PROJECT_ANNOTATIONS: ProjectAnnotations<ReactRenderer>;
```

**Usage (Vitest setup once):**
```ts
// test-setup.ts
import { setProjectAnnotations } from '@storybook/react';
import * as projectAnnotations from './.storybook/preview';

setProjectAnnotations([projectAnnotations]);
```

**Usage (per test file):**
```ts
import { composeStories } from '@storybook/react';
import * as stories from './Button.stories';
const { Primary } = composeStories(stories);

test('renders', () => {
  render(<Primary />);
  // assertions...
});
```

`setProjectAnnotations` was expanded to more renderers/frameworks in PR #28907. `[QMD:oms-storybook-react-vite-temporal:changelog.md #5defd6]` `[AST:code/renderers/react/src/portable-stories.tsx:L46]`

## Manager / Store types (custom panel & toolbar authoring)

These types are needed when you're **writing a manager-side addon** — a toolbar button, sidebar entry, custom panel, or status-store consumer — not when authoring stories. Imported from `storybook/manager-api`, `storybook/internal/types`, or `storybook/viewport` depending on which the symbol lives in.

### Manager API context and state

| Export | Kind | Signature | Source |
|---|---|---|---|
| `Combo` | interface | `{ api: API; state: State }` — the payload `ManagerConsumer` renders its children with | `[AST:code/core/src/manager-api/root.tsx:L116]` |
| `State` | type | `layout.SubState & stories.SubState & refs.SubState & …` — intersection of every manager slice | `[AST:code/core/src/manager-api/root.tsx:L82]` |
| `StoreOptions` | type | `Options` — persistence options passed to `store.set` | `[AST:code/core/src/manager-api/root.tsx:L77]` |
| `ManagerContext` | const | `React.Context<{ api: API; state: State }>` — underlying context that `ManagerConsumer` / `useStorybookApi` read | `[AST:code/core/src/manager-api/root.tsx:L80]` |
| `ManagerProviderProps` | type | `RouterData & API_ProviderData<API> & { children: ReactNode \| FC<Combo> }` — `children` is a node or a component that receives the `Combo` | `[AST:code/core/src/manager-api/root.tsx:L121]` |
| `Refs` | type | `API_Refs` — map of composed refs keyed by ref ID | `[AST:code/core/src/manager-api/root.tsx:L314]` |
| `API_EventMap` | interface | `{ [eventId: string]: Listener }` — `api.on(eventId, listener)` event registry | `[AST:code/core/src/manager-api/root.tsx:L318]` |
| `API_KeyCollection` | type | `string[]` — shortcut key sequence representation | `[AST:code/core/src/manager-api/modules/shortcuts.ts:L99]` |
| `StoriesHash` | type | `API_IndexHash` — manager-side story index (deprecated alias, use `IndexHash`) | `[AST:code/core/src/manager-api/root.tsx:L304]` |

### Story hierarchy (index hash)

Every story/doc/component in the manager is represented as a `HashEntry` keyed by ID. Walking this tree is how toolbar filters, sidebar rendering, and story-picker UIs work.

Import these names from `storybook/manager-api`: its `root.tsx` re-exports the `API_*` types that `code/core/src/types/modules/api-stories.ts` declares under these shorter names (`export type { API_IndexHash as IndexHash, ... }`). `storybook/internal/types` exports only the `API_*` names. Each row cites the alias, then the declaration.

| Export | Kind | Signature | Source |
|---|---|---|---|
| `IndexHash` | interface | `{ [id: string]: API_HashEntry }` — flat manager-side story index (`API_IndexHash`) | `[AST:code/core/src/manager-api/root.tsx:L305]` `[AST:code/core/src/types/modules/api-stories.ts:L80]` |
| `HashEntry` | type | `RootEntry \| GroupEntry \| ComponentEntry \| DocsEntry \| StoryEntry \| API_TestEntry` — union of all entry kinds (`API_HashEntry`; the test entry has no short alias) | `[AST:code/core/src/manager-api/root.tsx:L311]` `[AST:code/core/src/types/modules/api-stories.ts:L67]` |
| `LeafEntry` | type | `DocsEntry \| StoryEntry \| API_TestEntry` — entries with no children (`API_LeafEntry`) | `[AST:code/core/src/manager-api/root.tsx:L312]` `[AST:code/core/src/types/modules/api-stories.ts:L66]` |
| `RootEntry` | interface | `extends API_BaseEntry { type: 'root'; … }` — top of the hierarchy (`API_RootEntry`) | `[AST:code/core/src/manager-api/root.tsx:L306]` `[AST:code/core/src/types/modules/api-stories.ts:L15]` |
| `GroupEntry` | interface | `extends API_BaseEntry { type: 'group'; … }` — folder/group node (`API_GroupEntry`) | `[AST:code/core/src/manager-api/root.tsx:L307]` `[AST:code/core/src/types/modules/api-stories.ts:L21]` |
| `ComponentEntry` | interface | `extends API_BaseEntry { type: 'component'; … }` — component node grouping its stories (`API_ComponentEntry`) | `[AST:code/core/src/manager-api/root.tsx:L308]` `[AST:code/core/src/types/modules/api-stories.ts:L27]` |
| `DocsEntry` | interface | `extends API_BaseEntry { type: 'docs'; … }` — MDX / Autodocs entry (`API_DocsEntry`) | `[AST:code/core/src/manager-api/root.tsx:L309]` `[AST:code/core/src/types/modules/api-stories.ts:L34]` |
| `StoryEntry` | interface | `extends API_BaseEntry { type: 'story'; … }` — single story (`API_StoryEntry`) | `[AST:code/core/src/manager-api/root.tsx:L310]` `[AST:code/core/src/types/modules/api-stories.ts:L45]` |

### Viewport types (`storybook/viewport`)

| Export | Kind | Signature | Source |
|---|---|---|---|
| `GlobalState` | type | `{ value: string \| undefined; isRotated?: boolean }` — viewport toolbar global state | `[AST:code/core/src/viewport/types.ts:L16]` |
| `ViewportParameters` | interface | `{ viewport?: { disable?: boolean; options: Record<string, Viewport> } }` — story-level viewport config; `options` maps a key to one `Viewport` (`{ name: string; styles: ViewportStyles; type?: ViewportType }`), so it is itself a `ViewportMap` (`Record<string, Viewport>`, `types.ts:L14`) | `[AST:code/core/src/viewport/types.ts:L33]` `[AST:code/core/src/viewport/types.ts:L1]` |
| `ViewportStyles` | interface | `{ height: string; width: string }` — CSS dimensions | `[AST:code/core/src/viewport/types.ts:L9]` |
| `ViewportType` | type | `'desktop' \| 'mobile' \| 'tablet' \| 'watch' \| 'other'` | `[AST:code/core/src/viewport/types.ts:L7]` |
| `InitialViewportKeys` | type | `keyof typeof INITIAL_VIEWPORTS` — keys of the built-in viewport map | `[AST:code/core/src/viewport/defaults.ts:L230]` |

## CSF4 factory API

CSF4 (introduced in v10) offers a factory-based alternative to the CSF3 object form. Use it when you want typed `meta.story()` calls with stronger type inference and per-story `test()` methods.

```ts
// code/renderers/react/src/preview.tsx
export function __definePreview<Addons extends PreviewAddon<never>[]>(
  input: { addons: Addons } & ProjectAnnotations<ReactTypes & InferTypes<Addons>>
): ReactPreview<ReactTypes & InferTypes<Addons>>;

export interface ReactPreview<T extends AddonTypes> extends Preview<ReactTypes & T> {  // :102
  type<R>(): ReactPreview<T & R>;  // narrows the preview with extra types, e.g. args not inferred from the component
  meta<TArgs extends Args, Decorators extends DecoratorFunction<ReactTypes & T, any>, TMetaArgs extends Partial<TArgs & T['args']>>(
    meta: { render?; component?: ComponentType<TArgs>; decorators?: Decorators | Decorators[]; args?: TMetaArgs }
      & Omit<ComponentAnnotations<ReactTypes & T, TArgs>, 'decorators' | 'component' | 'args' | 'render'>
  ): ReactMeta<InferReactTypes<T, TArgs, Decorators>, /* component annotations with the meta's args */>;
}

export interface ReactMeta<T extends ReactTypes, MetaInput extends ComponentAnnotations<T>>  // :147
  extends Meta<T, MetaInput> {
  story(/* a story object or a render function */): ReactStory<T, /* the story input */>;  // several overloads
}

export interface ReactStory<T extends ReactTypes, TInput extends StoryAnnotations<T, T['args']>>  // :249
  extends Story<T, TInput> {
  Component: ComponentType<Partial<T['args']>>;  // for portable stories
}
```

**Usage (CSF4):**
```ts
// .storybook/preview.ts
import { definePreview } from '@storybook/react-vite';  // @storybook/react exports it only as __definePreview
const preview = definePreview({ /* config */ });
export default preview;

// Button.stories.ts
import preview from '../.storybook/preview';
import { Button } from './Button';
import { expect, fn } from 'storybook/test';

const meta = preview.meta({ component: Button, args: { onClick: fn() } });
export const Primary = meta.story({ args: { label: 'x' } });
Primary.test('clicks', async ({ canvas, userEvent, args }) => {
  await userEvent.click(canvas.getByRole('button'));
  await expect(args.onClick).toHaveBeenCalled();
});
```

`[AST:code/renderers/react/src/preview.tsx]` `[AST:code/renderers/react/template/stories/test-fn.stories.tsx:L1]`
