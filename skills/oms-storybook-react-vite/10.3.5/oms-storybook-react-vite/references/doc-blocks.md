# `@storybook/addon-docs/blocks` — MDX Doc Blocks Reference

All doc blocks are React components imported from `@storybook/addon-docs/blocks` and used inside `*.mdx` files (Autodocs or custom MDX pages). Entry: `code/addons/docs/src/blocks.ts`. All T1.

## Contents

- [Import source](#import-source)
- [Story-referencing blocks](#story-referencing-blocks) — `Canvas`, `Story`, `Primary`, `Stories`
- [Metadata blocks](#metadata-blocks) — `Meta`, `Title`, `Subtitle`, `Description`
- [Control blocks](#control-blocks) — `Controls`, `ArgTypes`, `Source`
- [Content blocks](#content-blocks) — `Markdown`, `Heading`, `Subheading`, `Anchor`, `Unstyled`
- [Visual blocks](#visual-blocks) — `Typeset`, `ColorPalette`, `ColorItem`, `IconGallery`, `IconItem`
- [Container blocks](#container-blocks) — `Docs`, `DocsPage`, `DocsContainer`, `DocsStory`
- [Utilities](#utilities) — `useOf`, `DocsContext`, `PureArgsTable`, `TableOfContents`

## Import source

```ts
import { Meta, Canvas, Controls, Primary, Stories } from '@storybook/addon-docs/blocks';
```

`[AST:code/addons/docs/src/blocks.ts:L1]`

**Do NOT import from** `@storybook/blocks` — that was the v9 path and does not exist in v10's consolidated package layout. The blocks live under `@storybook/addon-docs/blocks`.

## Story-referencing blocks

| Component | Props (simplified) | Purpose | Source |
|---|---|---|---|
| `Canvas` | `{ of, meta, sourceState, layout, source, story, withToolbar, additionalActions, className }` | Render story preview with optional source panel. `of` → story export from `import * as stories`. See [`Canvas` props detail](#canvas-props-detail) below. | `[AST:code/addons/docs/src/blocks/blocks/Canvas.tsx:L100]` |
| `Story` | `FC<StoryProps>`, `StoryProps = { of?: ModuleExport; meta?: ModuleExports } & { inline?: boolean; height?: string; autoplay?: boolean }` | Render single story by import reference. `expanded` is not a `Story` prop: it belongs to the internal `DocsStory`. | `[SRC:code/addons/docs/src/blocks/blocks/Story.tsx:L134]` `[AST:code/addons/docs/src/blocks.ts]` |
| `Primary` | `FC` (no props) | Render the attached meta's primary (first) story. It takes no `of`: use `<Canvas of={...} />` or `<Story of={...} />` to render a specific story. | `[SRC:code/addons/docs/src/blocks/blocks/Primary.tsx:L16]` `[AST:code/addons/docs/src/blocks.ts]` |
| `Stories` | `FC<StoriesProps>`, `StoriesProps = { title?: ReactElement \| string; includePrimary?: boolean }` | Render all stories of the attached CSF file as a list. It takes no `of`. | `[SRC:code/addons/docs/src/blocks/blocks/Stories.tsx:L74]` `[AST:code/addons/docs/src/blocks.ts]` |

### `Canvas` props detail

The full prop shape accepted by `<Canvas>` in MDX. Defined inline in `code/addons/docs/src/blocks/blocks/Canvas.tsx:L18` as a module-local `type CanvasProps` (not exported — these are the fields you pass to the JSX element, not an importable type).

| Prop | Type | Default | Purpose |
|---|---|---|---|
| `of` | `ModuleExport` | — | Story export to render. `<Canvas of={ButtonStories.Primary} />`. Throwing `of={undefined}` is caught at render time. |
| `meta` | `ModuleExports` | — | All exports of the CSF file when the MDX page is **unattached** (no `<Meta of={...} />`). Example: `<Canvas of={ButtonStories.Primary} meta={ButtonStories} />`. |
| `sourceState` | `'hidden' \| 'shown' \| 'none'` | `'hidden'` | Initial source panel state. `'none'` hides the reveal button entirely. |
| `layout` | `Layout` | `'padded'` | How the story is framed within the canvas: `'padded'`, `'fullscreen'`, or `'centered'`. Falls back to `parameters.layout` → `parameters.docs.canvas.layout`. |
| `source` | `Omit<SourceProps, 'dark'>` | — | Pass-through props for the underlying `Source` block (language, code override, format). `dark` is inherited from the docs theme. |
| `story` | `Pick<StoryProps, 'inline' \| 'height' \| 'autoplay' \| '__forceInitialArgs' \| '__primary'>` | `{ inline: framework default }` | Story renderer options. `inline: false` forces iframe; `height` sets the iframe height; `autoplay` re-runs the `play` fn when the story mounts in docs. |
| `withToolbar` | `boolean` | `false` | Show the canvas toolbar (zoom, background, grid controls). |
| `additionalActions` | `ActionItem[]` | — | Extra buttons rendered into the canvas toolbar. |
| `className` | `string` | — | Forwarded to the canvas wrapper element for custom styling. |

`[AST:code/addons/docs/src/blocks/blocks/Canvas.tsx:L18]` `[AST:code/addons/docs/src/blocks/blocks/Canvas.tsx:L100]`

**MDX usage:**
```mdx
import { Meta, Primary, Canvas, Controls, Stories } from '@storybook/addon-docs/blocks';
import * as ButtonStories from './Button.stories';

<Meta of={ButtonStories} />

<Primary />
<Controls />

## Secondary
<Canvas of={ButtonStories.Secondary} />

## All Stories
<Stories />
```

## Metadata blocks

| Component | Props | Purpose |
|---|---|---|
| `Meta` | `{ of?, title? }` | Declare component metadata in an MDX doc — connects the MDX page to a CSF module. Required once per doc. |
| `Title` | `withMdxComponentOverride('Title', TitleImpl)`, `TitleImpl: FunctionComponent<TitleProps>`, `TitleProps = { of?: Of; children?: ReactNode }` | Render the page title: `children` when given, else the last `/` segment of the title of the CSF file `of` names (a CSF file's default export), else of the attached meta. `of={undefined}` throws. `[SRC:code/addons/docs/src/blocks/blocks/Title.tsx:L55]` |
| `Subtitle` | `withMdxComponentOverride('Subtitle', SubtitleImpl)`, `SubtitleImpl: FunctionComponent<SubtitleProps>`, `SubtitleProps = { children?: ReactNode; of?: Of }` | Render the page subtitle: `children` when given, else `parameters.docs.subtitle` (then the deprecated `parameters.componentSubtitle`) of the CSF file `of` names, else of the attached meta. `of={undefined}` throws. `[SRC:code/addons/docs/src/blocks/blocks/Subtitle.tsx:L55]` |
| `Description` | `FC<DescriptionProps>`, `DescriptionProps = { of?: Of }` | Render the description of a component, CSF file or story (`of`), else of the attached meta. Pulls from JSDoc or `parameters.docs.description`; it has no `markdown` prop (use `<Markdown>` for custom text). `[SRC:code/addons/docs/src/blocks/blocks/Description.tsx:L74]` |

## Control blocks

| Component | Props | Purpose |
|---|---|---|
| `Controls` | `{ of?, include?, exclude?, sort? }` | Interactive controls panel for story args. |
| `ArgTypes` | `{ of?, include?, exclude?, sort? }` | Static arg types documentation table (read-only). |
| `Source` | `withMdxComponentOverride('Source', SourceImpl)` over `SourceProps = SourceParameters & { of?: ModuleExport }`, `SourceParameters = SourceCodeProps & { type?: SourceType; transform?: (code: string, storyContext) => string \| Promise<string> }`, `SourceCodeProps = { language?: SupportedLanguage; code?: string; format?; dark?: boolean; copyable?: boolean }` | Formatted source code block for a story (`of`). `type` picks where the code is read from (`SourceType`: `'auto'`, the default, `'code'` or `'dynamic'`); `transform` rewrites the detected code for display (it overrides `parameters.docs.source.transform`); `copyable` shows the copy button (default `true`); `code` overrides the content. `[SRC:code/addons/docs/src/blocks/blocks/Source.tsx:L181]` |

## Content blocks

| Component | Props | Purpose |
|---|---|---|
| `Markdown` | `{ children }` | Render markdown content inside MDX. |
| `Heading` | `withMdxComponentOverride('Heading', HeadingImpl)`, `HeadingImpl: FC<PropsWithChildren<HeadingProps>>`, `HeadingProps = { disableAnchor?: boolean }` | H2 with anchor link. `disableAnchor` (or non-string `children`) renders a plain H2 with no anchor. `[SRC:code/addons/docs/src/blocks/blocks/Heading.tsx:L33]` |
| `Subheading` | `withMdxComponentOverride('Subheading', SubheadingImpl)`, `SubheadingImpl: FC<PropsWithChildren<HeadingProps>> = ({ children, disableAnchor })` | H3 with anchor link. `disableAnchor` (or non-string `children`) renders a plain H3 with no anchor. `[SRC:code/addons/docs/src/blocks/blocks/Subheading.tsx:L23]` |
| `Anchor` | `{ storyId }` | Create an anchor link to a story. |
| `Unstyled` | `{ children }` | Wrapper that removes Storybook's docs styling — use for custom-styled sections. |

## Visual blocks

| Component | Props | Purpose |
|---|---|---|
| `Typeset` | `{ fontSizes, fontWeight, sampleText, fontFamily }` | Font family / size display for design system docs. |
| `ColorPalette` | `{ children: ColorItem[] }` | Color swatch collection. |
| `ColorItem` | `{ title, subtitle, colors }` | Single color swatch with label. |
| `IconGallery` | `{ children: IconItem[] }` | Icon collection display. |
| `IconItem` | `{ name, children }` | Single icon display. |

## Container blocks

| Component | Props | Purpose |
|---|---|---|
| `Docs` | `Docs<TRenderer>({ context, docsParameter }: DocsProps<TRenderer>)`, `DocsProps = { docsParameter: Parameters; context: DocsContextProps<TRenderer> }` | Root docs container — rarely used directly. `docsParameter` is required: its `container`, `page` and `theme` pick the container and page it renders. `[SRC:code/addons/docs/src/blocks/blocks/Docs.tsx:L17]` |
| `DocsPage` | — | Default Autodocs layout function. |
| `DocsContainer` | `FC<PropsWithChildren<DocsContainerProps>>`, `DocsContainerProps<TFramework extends Renderer = Renderer> = { context: DocsContextProps<TFramework>; theme?: ThemeVars }` | MDX docs wrapper: provides `context` to the blocks it wraps and applies `theme` (a `ThemeVars`, for example `themes.dark` from `storybook/theming`) to the docs page. `[SRC:code/addons/docs/src/blocks/blocks/DocsContainer.tsx:L23]` |
| `DocsStory` | `{ of, expanded?, withToolbar? }` | Internal story renderer used by `Primary`/`Stories`. |

## Utilities

| Export | Kind | Purpose |
|---|---|---|
| `useOf` | hook | Resolve CSF export references within MDX (`of={ButtonStories.Primary}`). |
| `DocsContext` | React context | Provides story/component metadata to blocks. Access via `const ctx = useContext(DocsContext)`. |
| `PureArgsTable` | component | ArgsTable without Storybook integration — accepts `rows` directly. |
| `TableOfContents` | component | Auto-generated TOC from docs headings. Enable via `parameters.docs.toc`. |
| `SortType` | type | `'alpha' \| 'requiredFirst' \| 'none' \| ((a, b) => number)` for `sort` prop on `Controls`/`ArgTypes`. |

`[AST:code/addons/docs/src/blocks.ts]`

## DocsRenderer

Entry: `code/addons/docs/src/index.ts` exports `DocsRenderer` — the React component that renders an entire docs page. Rarely imported directly; registered via `addons: ['@storybook/addon-docs']` in `main.ts`. `[AST:code/addons/docs/src/index.ts:L8]`

## Control Primitives

The primitive control components that back `Controls` / `ArgTypes` panels. Imported as `import { BooleanControl, ... } from '@storybook/addon-docs/blocks'` when building a **custom controls panel** (addon UI). For normal story authoring the `Controls` doc-block is sufficient — these are the lower-level renderers it composes.

### Control value / config types

| Export | Kind | Signature | Source |
|---|---|---|---|
| `ControlProps<T>` | type | `{ name: string; value?: T; defaultValue?: T; argType?: ArgType; onChange(v?: T): T \| void; onFocus?(e: any): void; onBlur?(e: any): void }` — base props shared by all control components | `[AST:code/addons/docs/src/blocks/controls/types.ts:L3]` |
| `BooleanValue` | type | `boolean` | `[AST:code/addons/docs/src/blocks/controls/types.ts:L13]` |
| `BooleanConfig` | interface | `{}` — no boolean-specific config | `[AST:code/addons/docs/src/blocks/controls/types.ts:L14]` |
| `ColorValue` | type | `string` — hex / rgb / hsl / named | `[AST:code/addons/docs/src/blocks/controls/types.ts:L16]` |
| `PresetColor` | type | `ColorValue \| { color: ColorValue; title?: string }` | `[AST:code/addons/docs/src/blocks/controls/types.ts:L17]` |
| `ColorConfig` | interface | `{ presetColors?: PresetColor[]; startOpen?: boolean }` | `[AST:code/addons/docs/src/blocks/controls/types.ts:L18]` |
| `DateValue` | type | `Date \| number` (timestamp) | `[AST:code/addons/docs/src/blocks/controls/types.ts:L28]` |
| `DateConfig` | interface | `{}` — no date-specific config | `[AST:code/addons/docs/src/blocks/controls/types.ts:L29]` |
| `NumberValue` | type | `number` | `[AST:code/addons/docs/src/blocks/controls/types.ts:L31]` |
| `NumberConfig` | interface | `{ min?: number; max?: number; step?: number }` | `[AST:code/addons/docs/src/blocks/controls/types.ts:L32]` |
| `RangeConfig` | type | `NumberConfig` (alias) | `[AST:code/addons/docs/src/blocks/controls/types.ts:L38]` |
| `ObjectValue` | type | `any` | `[AST:code/addons/docs/src/blocks/controls/types.ts:L40]` |
| `ObjectConfig` | interface | `{}` | `[AST:code/addons/docs/src/blocks/controls/types.ts:L41]` |
| `OptionsSingleSelection` | type | `any` — single-value form | `[AST:code/addons/docs/src/blocks/controls/types.ts:L43]` |
| `OptionsMultiSelection` | type | `any[]` — multi-value form | `[AST:code/addons/docs/src/blocks/controls/types.ts:L44]` |
| `OptionsSelection` | type | `OptionsSingleSelection \| OptionsMultiSelection` | `[AST:code/addons/docs/src/blocks/controls/types.ts:L45]` |
| `OptionsArray` | type | `any[]` — array shape for options | `[AST:code/addons/docs/src/blocks/controls/types.ts:L46]` |
| `OptionsObject` | type | `Record<string, any>` — labeled shape | `[AST:code/addons/docs/src/blocks/controls/types.ts:L47]` |
| `Options` | type | `OptionsArray \| OptionsObject` | `[AST:code/addons/docs/src/blocks/controls/types.ts:L48]` |
| `OptionsControlType` | type | `'radio' \| 'inline-radio' \| 'check' \| 'inline-check' \| 'select' \| 'multi-select'` | `[AST:code/addons/docs/src/blocks/controls/types.ts:L49]` |
| `OptionsConfig` | interface | `{ labels?: Record<any, string>; type: OptionsControlType }` | `[AST:code/addons/docs/src/blocks/controls/types.ts:L57]` |
| `NormalizedOptionsConfig` | interface | `{ options: OptionsObject }` | `[AST:code/addons/docs/src/blocks/controls/types.ts:L62]` |
| `TextValue` | type | `string` | `[AST:code/addons/docs/src/blocks/controls/types.ts:L66]` |
| `TextConfig` | interface | `{ maxLength?: number }` | `[AST:code/addons/docs/src/blocks/controls/types.ts:L67]` |
| `ControlType` | type | `'array' \| 'boolean' \| 'color' \| 'date' \| 'number' \| 'range' \| 'object' \| OptionsControlType \| 'text'` | `[AST:code/addons/docs/src/blocks/controls/types.ts:L71]` |
| `Control` | type | `BooleanConfig \| ColorConfig \| DateConfig \| NumberConfig \| ObjectConfig \| OptionsConfig \| RangeConfig \| TextConfig` — full union | `[AST:code/addons/docs/src/blocks/controls/types.ts:L82]` |

### Control components (props + renderer pairs)

| Component / Props | Kind | Signature | Source |
|---|---|---|---|
| `BooleanProps` | type | `ControlProps<BooleanValue> & BooleanConfig` | `[AST:code/addons/docs/src/blocks/controls/Boolean.tsx:L104]` |
| `BooleanControl` | component | `(props: BooleanProps) => JSX.Element` — toggle switch | `[AST:code/addons/docs/src/blocks/controls/Boolean.tsx:L117]` |
| `ColorControlProps` | type | `ControlProps<ColorValue> & ColorConfig`. Not exported from `@storybook/addon-docs/blocks`: the blocks entry exports it as `ColorProps` (`export type ColorProps = ColorControlProps`, `controls/index.tsx:10`) | `[AST:code/addons/docs/src/blocks/controls/Color.tsx:L360]` |
| `ColorControl` | component | `(props: ColorControlProps) => JSX.Element` — color picker with color-space cycling. The blocks entry exports a lazy-loading wrapper of the same name (`controls/index.tsx:14`) | `[AST:code/addons/docs/src/blocks/controls/Color.tsx:L361]` |
| `DateProps` | type | `ControlProps<DateValue> & DateConfig` | `[AST:code/addons/docs/src/blocks/controls/Date.tsx:L68]` |
| `DateControl` | component | `(props: DateProps) => JSX.Element` — date + time picker | `[AST:code/addons/docs/src/blocks/controls/Date.tsx:L69]` |
| `parseDate` | function | `(value: string) => Date` — YYYY-MM-DD parse helper | `[AST:code/addons/docs/src/blocks/controls/Date.tsx:L11]` |
| `parseTime` | function | `(value: string) => Date` — HH:MM parse helper | `[AST:code/addons/docs/src/blocks/controls/Date.tsx:L18]` |
| `formatDate` | function | `(value: Date \| number) => string` | `[AST:code/addons/docs/src/blocks/controls/Date.tsx:L26]` |
| `formatTime` | function | `(value: Date \| number) => string` | `[AST:code/addons/docs/src/blocks/controls/Date.tsx:L34]` |
| `FilesControlProps` | interface | `extends ControlProps<string[]> { accept?: string }` | `[AST:code/addons/docs/src/blocks/controls/Files.tsx:L11]` |
| `FilesControl` | component | `(props: FilesControlProps) => JSX.Element` — file input | `[AST:code/addons/docs/src/blocks/controls/Files.tsx:L40]` |
| `NumberControl` | component | `(props: NumberProps) => JSX.Element` — number input with min/max/step | `[AST:code/addons/docs/src/blocks/controls/Number.tsx:L28]` |
| `parse` | function | `(value: string) => number \| undefined` — Number control parse helper | `[AST:code/addons/docs/src/blocks/controls/Number.tsx:L17]` |
| `format` | function | `(value: NumberValue) => string` — Number control format helper | `[AST:code/addons/docs/src/blocks/controls/Number.tsx:L22]` |
| `ObjectProps` | type | `ControlProps<ObjectValue> & ObjectConfig` | `[AST:code/addons/docs/src/blocks/controls/Object.tsx:L164]` |
| `ObjectControl` | component | `(props: ObjectProps) => JSX.Element` — JSON tree editor | `[AST:code/addons/docs/src/blocks/controls/Object.tsx:L166]` |
| `RangeControl` | component | `(props: RangeProps) => JSX.Element` — slider with min/max labels | `[AST:code/addons/docs/src/blocks/controls/Range.tsx:L178]` |
| `TextProps` | type | `ControlProps<TextValue \| undefined> & TextConfig` | `[AST:code/addons/docs/src/blocks/controls/Text.tsx:L11]` |
| `TextControl` | component | `(props: TextProps) => JSX.Element` — textarea with max-length | `[AST:code/addons/docs/src/blocks/controls/Text.tsx:L23]` |
| `OptionsProps` | type | `ControlProps<OptionsSelection> & OptionsConfig` | `[AST:code/addons/docs/src/blocks/controls/options/Options.tsx:L40]` |
| `OptionsControl` | component | `(props: OptionsProps) => JSX.Element` — dispatcher → CheckboxControl / RadioControl / SelectControl | `[AST:code/addons/docs/src/blocks/controls/options/Options.tsx:L41]` |
| `CheckboxControl` | component | `(props: CheckboxProps) => JSX.Element` — multi-select checkbox group. Internal renderer `OptionsControl` dispatches to: `controls/options/index.ts` exports only `./Options`, so it is not importable from `@storybook/addon-docs/blocks` | `[AST:code/addons/docs/src/blocks/controls/options/Checkbox.tsx:L57]` |
| `RadioControl` | component | `(props: RadioProps) => JSX.Element` — single-select radio group. Internal renderer, not importable from `@storybook/addon-docs/blocks` | `[AST:code/addons/docs/src/blocks/controls/options/Radio.tsx:L57]` |
| `SelectControl` | component | `(props: SelectProps) => JSX.Element` — dropdown select (single or multi). Internal renderer, not importable from `@storybook/addon-docs/blocks` | `[AST:code/addons/docs/src/blocks/controls/options/Select.tsx:L170]` |

**Custom controls panel usage:** You rarely need to import these individually — the `Controls` doc-block handles dispatching automatically based on `argTypes[key].control.type`. Reach for the primitives only when building an addon that renders its own controls UI (e.g., a visual-testing panel that needs inline range sliders).
