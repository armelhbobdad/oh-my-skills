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
- [Block internals and MDX helpers](#block-internals-and-mdx-helpers) — the MDX element overrides, the `Source` block plumbing, the story, title, anchor and heading helpers, external docs, the block types and constants, and the block props types

## Import source

```ts
import { Meta, Canvas, Controls, Primary, Stories } from '@storybook/addon-docs/blocks';
```

`[SRC:code/addons/docs/src/blocks.ts:L8]`

**Do NOT import from** `@storybook/blocks` — that was the v9 path and does not exist in v10's consolidated package layout. The blocks live under `@storybook/addon-docs/blocks`.

## Story-referencing blocks

| Component | Props (simplified) | Purpose | Source |
|---|---|---|---|
| `Canvas` | `{ of?, meta?, sourceState?, layout?, source?, story?, withToolbar?, additionalActions?, className? }` (all optional) | Render story preview with optional source panel. `of` → story export from `import * as stories`. See [`Canvas` props detail](#canvas-props-detail) below. | `[AST:code/addons/docs/src/blocks/blocks/Canvas.tsx:L100]` |
| `Story` | `{ of?, meta?, inline?, height?, autoplay? }` (`StoryProps`; also the internal `__forceInitialArgs?`, `__primary?`) | Render a single story by import reference (`of`; defaults to the current story). Pass `meta` (all exports of the CSF file) when the MDX page is unattached. `expanded` is a `DocsStory` prop, not a `Story` prop. | `[AST:code/addons/docs/src/blocks/blocks/Story.tsx:L134]` |
| `Primary` | none (`FC` with no props) | Render the primary story of the attached CSF file (`usePrimaryStory()`); it takes no `of`. | `[AST:code/addons/docs/src/blocks/blocks/Primary.tsx:L16]` |
| `Stories` | `{ title?: ReactElement \| string; includePrimary?: boolean }` | Render every story of the attached CSF file (`DocsContext.componentStories()`) as a list; it takes no `of`. `title` defaults to `'Stories'`, `includePrimary` to `true`. | `[AST:code/addons/docs/src/blocks/blocks/Stories.tsx:L74]` |

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

`[SRC:code/addons/docs/src/blocks/blocks/Canvas.tsx:L18]` `[AST:code/addons/docs/src/blocks/blocks/Canvas.tsx:L100]`

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
| `Meta` | `MetaProps = BaseAnnotations & { of?: ModuleExports; title?: string }` (`FC<MetaProps>`): `of?`, `title?`, plus every optional `BaseAnnotations` field (`decorators?`, `parameters?`, `args?`, `argTypes?`, `loaders?`, `beforeEach?`, `afterEach?`, `render?`, `tags?`, `mount?`). The component itself reads only `of`. | Declare component metadata in an MDX doc — connects the MDX page to a CSF module. Required once per doc. This is the doc block; the React `Meta` type is in `story-types.md`. `[SRC:code/addons/docs/src/blocks/blocks/Meta.tsx:L9]` `[AST:code/addons/docs/src/blocks/blocks/Meta.tsx:L15]` `[AST:code/core/src/csf/story.ts:L347]` |
| `Title` | `TitleProps = { of?: Of; children?: ReactNode }` | Render page title: `children` when given, else the last path segment of the meta's `title`. `of` names the CSF file's default export (meta) to read the title from (the attached meta when omitted); `of={undefined}` throws. `[SRC:code/addons/docs/src/blocks/blocks/Title.tsx:L11]` `[AST:code/addons/docs/src/blocks/blocks/Title.tsx:L55]` |
| `Subtitle` | `SubtitleProps = { children?: ReactNode; of?: Of }` | Render page subtitle: `children` when given, else the meta's `parameters.docs.subtitle` (or the deprecated `parameters.componentSubtitle`). `of` names the meta to read it from (the attached CSF file's meta when omitted); `of={undefined}` throws. `[SRC:code/addons/docs/src/blocks/blocks/Subtitle.tsx:L11]` `[AST:code/addons/docs/src/blocks/blocks/Subtitle.tsx:L55]` |
| `Description` | `{ of?: Of }` | Render the description of the resolved `of` (the attached meta when omitted): `parameters.docs.description.story` for a story, `parameters.docs.description.component` or the component's docgen description for a meta or component. There is no `markdown` prop. `[AST:code/addons/docs/src/blocks/blocks/Description.tsx:L74]` |

## Control blocks

| Component | Props | Purpose |
|---|---|---|
| `Controls` | `{ of?, include?, exclude?, sort? }` | Interactive controls panel for story args. `[AST:code/addons/docs/src/blocks/blocks/Controls.tsx:L109]` |
| `ArgTypes` | `{ of?, include?, exclude?, sort? }` | Static arg types documentation table (read-only). This is the doc block `@storybook/addon-docs/blocks` exports; the CSF type of the same name is in `story-types.md`. `[AST:code/addons/docs/src/blocks/blocks/ArgTypes.tsx:L108]` |
| `Source` | `SourceProps` (full list below): `{ of?, code?, language?, format?, dark?, copyable?, type?, transform?, originalSource?, __forceInitialArgs? }` | Formatted source code block for a story. See [`Source` props detail](#source-props-detail) below. `[AST:code/addons/docs/src/blocks/blocks/Source.tsx:L181]` |

### `Source` props detail

`SourceProps = SourceParameters & { of?: ModuleExport; __forceInitialArgs?: boolean }`, where `SourceParameters = SourceCodeProps & { type?; transform?; originalSource? }` and `SourceCodeProps` comes from the `Source` component. Every prop is optional.

| Prop | Type | Purpose |
|---|---|---|
| `of` | `ModuleExport` | Story export whose source to render: `<Source of={ButtonStories.Primary} />`. |
| `code` | `string` | Override the content of the source block. |
| `language` | `SupportedLanguage` | Language the syntax highlighter uses. |
| `format` | `ComponentProps<typeof SyntaxHighlighter>['format']` | Formatter the syntax highlighter uses. |
| `dark` | `boolean` | Display the snippet in dark mode. |
| `copyable` | `boolean` | Show the copy button (defaults to `true`). |
| `type` | `SourceType` | Where to read the source from: `'auto'` (default), `'code'` (the code csf-plugin extracted) or `'dynamic'` (snippet rendered from the story's virtual DOM, React only). |
| `transform` | `(code: string, storyContext) => string \| Promise<string>` | Transform the detected source before display; `storyContext` is the docs context's story context. |
| `originalSource` | `string` | Internal: set by the CSF loader (`enrichCsf` in `storybook/internal/csf-tools`). |
| `__forceInitialArgs` | `boolean` | Internal: controls whether the story re-renders on args updates. |

`[AST:code/addons/docs/src/blocks/blocks/Source.tsx:L16]` `[AST:code/addons/docs/src/blocks/blocks/Source.tsx:L28]` `[AST:code/addons/docs/src/blocks/components/Source.tsx:L39]` `[SRC:code/core/src/docs-tools/shared.ts:L7]`

## Content blocks

| Component | Props | Purpose |
|---|---|---|
| `Markdown` | `MarkdownProps`, the props of `markdown-to-jsx`'s default export mirrored: `children` (a single string), `options?` (markdown-to-jsx options) and the rest of that component's props, all spread onto it | Render markdown content inside MDX. No `children` renders nothing; a non-string child throws (wrap the markdown in a template string). `options` is spread last over the block's own `{ forceBlock: true, overrides }`, so a key you pass wins. `[SRC:code/addons/docs/src/blocks/blocks/Markdown.tsx:L11]` `[AST:code/addons/docs/src/blocks/blocks/Markdown.tsx:L55]` |
| `Heading` | `{ children?: ReactNode; disableAnchor?: boolean }` (`PropsWithChildren<HeadingProps>`, the interface `HeadingProps { disableAnchor?: boolean }`) | H2 with an anchor id slugged from a string child. `disableAnchor` (or a non-string child) renders a plain H2 with no anchor. `[AST:code/addons/docs/src/blocks/blocks/Heading.tsx:L11]` `[AST:code/addons/docs/src/blocks/blocks/Heading.tsx:L33]` |
| `Subheading` | `{ children?: ReactNode; disableAnchor?: boolean }` (`PropsWithChildren<HeadingProps>`, the `Heading` props type) | H3 with an anchor id slugged from a string child. `disableAnchor` (or a non-string child) renders a plain H3 with no anchor. `[AST:code/addons/docs/src/blocks/blocks/Subheading.tsx:L23]` |
| `Anchor` | `{ storyId: string; children?: ReactNode }` (`FC<PropsWithChildren<AnchorProps>>`, the interface `AnchorProps { storyId: string }`) | Create an anchor for a story: wraps `children` in `<div id="anchor--{storyId}" className="sb-anchor">`. `[AST:code/addons/docs/src/blocks/blocks/Anchor.tsx:L6]` `[AST:code/addons/docs/src/blocks/blocks/Anchor.tsx:L10]` |
| `Unstyled` | `React.DetailedHTMLProps<React.HTMLAttributes<HTMLDivElement>, HTMLDivElement>`: every optional `<div>` prop (`children`, `id`, `style`, `ref`, event handlers, ...) | Wrapper that removes Storybook's docs styling — use for custom-styled sections. Spreads its props onto a `<div>` whose `className` is always `sb-unstyled` (a `className` you pass is replaced). `[AST:code/addons/docs/src/blocks/blocks/Unstyled.tsx:L9]` |

## Visual blocks

| Component | Props | Purpose |
|---|---|---|
| `Typeset` | `{ fontSizes: (string \| number)[]; fontFamily?: string; fontWeight?: number; sampleText?: string }` (only `fontSizes` is required) | Font family / size display for design system docs. `[SRC:code/addons/docs/src/blocks/components/Typeset.tsx:L39]` |
| `ColorPalette` | `{ children?: React.ReactNode }` | Color swatch collection: pass `ColorItem` elements as its children. `[AST:code/addons/docs/src/blocks/components/ColorPalette.tsx:L202]` |
| `ColorItem` | `{ title, subtitle, colors }` | Single color swatch with label. |
| `IconGallery` | `{ children?: React.ReactNode }` | Icon grid: pass `IconItem` elements as its children. `[AST:code/addons/docs/src/blocks/components/IconGallery.tsx:L74]` |
| `IconItem` | `{ name: string; children?: React.ReactNode }` | Single icon display: a caption (`name`) and the icon passed as `children`. `[SRC:code/addons/docs/src/blocks/components/IconGallery.tsx:L62]` |

## Container blocks

| Component | Props | Purpose |
|---|---|---|
| `Docs` | `{ context, docsParameter }: DocsProps<TRenderer>`, both required: `Docs<TRenderer extends Renderer = Renderer>({ context, docsParameter }: DocsProps<TRenderer>)` with `DocsProps = { docsParameter: Parameters; context: DocsContextProps<TRenderer> }` | Root docs container: renders `docsParameter.page` (default `DocsPage`) inside `docsParameter.container` (default `DocsContainer`). Rarely used directly. `[AST:code/addons/docs/src/blocks/blocks/Docs.tsx:L17]` |
| `DocsPage` | — | Default Autodocs layout function. |
| `DocsContainer` | `{ context: DocsContextProps<Renderer>; theme?: ThemeVars; children?: ReactNode }` (`FC<PropsWithChildren<DocsContainerProps>>`: the component is not generic, so it takes `DocsContainerProps` at its default, the interface `DocsContainerProps<TFramework extends Renderer = Renderer> { context: DocsContextProps<TFramework>; theme?: ThemeVars }`) | MDX docs wrapper: provides `context` through `DocsContext` and renders `children` inside a `ThemeProvider` for `theme` (passed through `ensure`). `[AST:code/addons/docs/src/blocks/blocks/DocsContainer.tsx:L18]` `[AST:code/addons/docs/src/blocks/blocks/DocsContainer.tsx:L23]` |
| `DocsStory` | `DocsStoryProps = { of: ModuleExport; expanded?: boolean; withToolbar?: boolean; __forceInitialArgs?: boolean; __primary?: boolean }`, defaults `expanded = true`, `withToolbar = false`, `__forceInitialArgs = false`, `__primary = false` (the two `__` props are internal) | Internal story renderer used by `Primary`/`Stories`. `parameters.docs.canvas.withToolbar` overrides the `withToolbar` prop. `[AST:code/addons/docs/src/blocks/blocks/types.ts:L9]` `[AST:code/addons/docs/src/blocks/blocks/DocsStory.tsx:L42]` |

## Utilities

| Export | Kind | Purpose |
|---|---|---|
| `useOf` | hook | Resolve CSF export references within MDX (`of={ButtonStories.Primary}`). `[AST:code/addons/docs/src/blocks/blocks/useOf.ts:L18]` |
| `DocsContext` | const | `Context<DocsContextProps<Renderer>>`, a React context (kept on `globalThis.__DOCS_CONTEXT__`, so one copy is shared even when the module loads twice) that provides story/component metadata to blocks. Access via `const ctx = useContext(DocsContext)`. This is the doc blocks' context; `storybook/preview-api` exports a `DocsContext` class (`core-api.md`), the object such a context holds. `[AST:code/addons/docs/src/blocks/blocks/DocsContext.ts:L18]` |
| `PureArgsTable` | component | ArgsTable without Storybook integration: the `ArgsTable` component (`FC<ArgsTableProps>`), re-exported under this name. `ArgsTableProps = ArgsTableOptionProps & (ArgsTableDataProps \| ArgsTableErrorProps \| ArgsTableLoadingProps)`. Options, all optional: `{ children?: ReactNode; updateArgs?: (args: Args) => void; resetArgs?: (argNames?: string[]) => void; compact?: boolean; inAddonPanel?: boolean; inTabPanel?: boolean; initialExpandedArgs?: boolean; isLoading?: boolean; sort?: SortType }` (`sort` defaults to `'none'`). Plus one of: `{ rows: ArgTypes; args?: Args; globals?: Globals }` (the table data), `{ error: ArgsTableError }` or `{ isLoading: boolean }`. `[SRC:code/addons/docs/src/blocks/components/ArgsTable/ArgsTable.tsx:L320]` `[AST:code/addons/docs/src/blocks/components/ArgsTable/ArgsTable.tsx:L197]` `[AST:code/addons/docs/src/blocks/components/ArgsTable/ArgsTable.tsx:L222]` `[AST:code/addons/docs/src/blocks.ts:L3]` |
| `TableOfContents` | component | Auto-generated TOC from docs headings. Enable via `parameters.docs.toc`. `[AST:code/addons/docs/src/blocks/components/TableOfContents.tsx:L158]` `[AST:code/addons/docs/src/blocks.ts:L4]` |
| `SortType` | type | `'alpha' \| 'requiredFirst' \| 'none'` (no function form) for the `sort` prop on `Controls`/`ArgTypes`. `[AST:code/addons/docs/src/blocks/components/ArgsTable/ArgsTable.tsx:L186]` |

`[AST:code/addons/docs/src/blocks.ts]`

## Block internals and MDX helpers

The rest of what `@storybook/addon-docs/blocks` exports: `blocks.ts` re-exports `blocks/blocks/index.ts`, which re-exports every block module, the two external-docs modules, `SourceContainer.tsx`, `types.ts` and `mdx.tsx` `[SRC:code/addons/docs/src/blocks.ts:L8]` `[SRC:code/addons/docs/src/blocks/blocks/index.ts:L13]` `[SRC:code/addons/docs/src/blocks/blocks/index.ts:L31]`. The blocks above are built from these; an MDX page rarely imports them.

### MDX element overrides (`mdx.tsx`)

Components that stand in for MDX's own elements, and two helpers. Where a row says a click navigates, the component emits the `NAVIGATE_URL` event with that URL on the docs channel.

| Export | Kind | Props / Usage | Purpose | Source |
|---|---|---|---|---|
| `AnchorMdx` | component | `{ href: string; target: string; children?: ReactNode }` (`FC<PropsWithChildren<AnchorMdxProps>>`, `AnchorMdxProps` module-local) | MDX link. It renders a plain link when `href` is empty, `target` is `'_blank'` or `href` starts with `http://` or `https://`, and an in-page anchor for a `#hash` (a click navigates when the target element exists); any other link navigates on a plain left click (no modifier key) instead of being followed, because, the comment says, links to other Storybook pages "should use the base URL of the top level iframe" | `[AST:code/addons/docs/src/blocks/blocks/mdx.tsx:L98]` |
| `CodeOrSourceMdx` | component | `{ className?: string; children?: ReactNode }` (`FC<PropsWithChildren<CodeOrSourceMdxProps>>`) | MDX code. It renders inline `Code` when `className` is not a string and `children` is not a string holding a line break (the comment: markdown-to-jsx adds no `className` to inline code); otherwise a `Source` block with the language of a `lang-<language>` `className` (default `'text'`), `format={false}` and `children` as its code, the other props passed through | `[AST:code/addons/docs/src/blocks/blocks/mdx.tsx:L39]` |
| `HeaderMdx` | component | `{ as: string; id: string; children?: ReactNode }` (`FC<PropsWithChildren<HeaderMdxProps>>`) | MDX heading. With an `id` (which, the comment says, the `remark-slug` plugin adds to every heading) it renders the `as` heading with a hover link icon to `#id` whose click navigates; without one, a plain `as` element | `[AST:code/addons/docs/src/blocks/blocks/mdx.tsx:L215]` |
| `HeadersMdx` | const | — | `{ h1, h2, h3, h4, h5, h6 }`, each mapping its tag to `HeaderMdx` with that `as`; typed `{}`, its `reduce` seed | `[AST:code/addons/docs/src/blocks/blocks/mdx.tsx:L232]` |
| `Wrapper` | component | `<Wrapper>{children}</Wrapper>` (props `React.DetailedHTMLProps<React.HTMLAttributes<HTMLDivElement>, HTMLDivElement>`, of which it reads `children`) | Renders `children` in a `<div style={{ fontFamily: 'sans-serif' }}>`. Like `Title`, `Heading` and the other blocks `withMdxComponentOverride` wraps, an MDX `components.Wrapper` override takes its place | `[AST:code/addons/docs/src/blocks/blocks/Wrapper.tsx:L10]` |
| `AddContext` | component | `<AddContext {...docsContextProps}>{children}</AddContext>` (props `PropsWithChildren<DocsContextProps>`) | Provides `DocsContext` to `children` with its props spread over the enclosing context's value; the comment calls it a "hacky utility for adding mdxStoryToId to the default context" | `[AST:code/addons/docs/src/blocks/blocks/mdx.tsx:L27]` |
| `assertIsFn` | function | `assertIsFn(val: any)` (return type not annotated) | Returns `val` when it is a function, else throws `` Expected story function, got: ${val} ``; the comment calls it a "hacky utility for asserting identifiers in MDX Story elements" | `[AST:code/addons/docs/src/blocks/blocks/mdx.tsx:L19]` |

### Source block plumbing (`SourceContainer.tsx`, `Source.tsx`)

How the `Source` block, and `Canvas`, which calls the same hook, find the snippet a story rendered.

| Export | Kind | Props / Signature | Purpose | Source |
|---|---|---|---|---|
| `SourceContainer` | component | `{ channel: DocsContextProps['channel']; children?: ReactNode }` | Listens for `SNIPPET_RENDERED` on `channel`, stores each snippet under its story id and the hash of its args (`UNKNOWN_ARGS_HASH` when the event carries none), and provides `{ sources }` to `children` through `SourceContext` | `[AST:code/addons/docs/src/blocks/blocks/SourceContainer.tsx:L38]` |
| `SourceContext` | const | `Context<SourceContextProps>` | `createContext({ sources: {} })`, the context `SourceContainer` fills | `[AST:code/addons/docs/src/blocks/blocks/SourceContainer.tsx:L27]` |
| `SourceContextProps` | interface | `{ sources: StorySources; setSource?: (id: StoryId, item: SourceItem) => void }` | The `SourceContext` value | `[AST:code/addons/docs/src/blocks/blocks/SourceContainer.tsx:L22]` |
| `SourceItem` | interface | `{ code: string; format?: SyntaxHighlighterFormatTypes }` | One stored snippet | `[AST:code/addons/docs/src/blocks/blocks/SourceContainer.tsx:L15]` |
| `StorySources` | type | `Record<StoryId, Record<ArgsHash, SourceItem>>` (`ArgsHash = string`, module-local) | Snippets by story id, then by args hash | `[AST:code/addons/docs/src/blocks/blocks/SourceContainer.tsx:L20]` |
| `argsHash` | function | `argsHash(args: Args): ArgsHash` | telejson's `stringify(args, { maxDepth: 50 })`: the key a snippet is stored under for those args | `[AST:code/addons/docs/src/blocks/blocks/SourceContainer.tsx:L11]` |
| `UNKNOWN_ARGS_HASH` | const | `'--unknown--'` | The key of a snippet whose event carries no args; `Source` falls back to it when no snippet matches the story's args | `[AST:code/addons/docs/src/blocks/blocks/SourceContainer.tsx:L36]` |
| `useSourceProps` | function | `useSourceProps(props: SourceProps, docsContext: DocsContextProps<any>, sourceContext: SourceContextProps): PureSourceProps` (`PureSourceProps`: the pure `Source` component's props) | Computes what the `Source` block renders: resolves `of` (else the primary story), takes that story's snippet from `sourceContext` and applies `type` and `transform`. With neither a `code` prop nor a story it returns `{ error: SourceError.SOURCE_UNAVAILABLE }`, else `{ code, format, language, dark }` (`language` defaults to `'jsx'`, `dark` to `false`); it throws on `of={undefined}` | `[AST:code/addons/docs/src/blocks/blocks/Source.tsx:L101]` |

### Story, title, anchor and heading helpers

| Export | Kind | Signature | Purpose | Source |
|---|---|---|---|---|
| `getStoryId` | function | `getStoryId(props: StoryProps, context: DocsContextProps): StoryId` | The `Story` block's story id: throws on `of={undefined}`, registers `meta` with `context.referenceMeta(meta, false)` when it is given, then resolves `of` (`'story'` when it is absent) to a story and returns its `id` | `[AST:code/addons/docs/src/blocks/blocks/Story.tsx:L62]` |
| `getStoryProps` | function | `getStoryProps<TFramework extends Renderer>(props: StoryParameters, story: PreparedStory<TFramework>, context: DocsContextProps<TFramework>): PureStoryProps` (`StoryParameters`, module-local, is `{ inline?, height?, autoplay?, __forceInitialArgs?, __primary? }`; `PureStoryProps` the pure `Story` component's props) | The `Story` block's render props, the block's props taking precedence over `parameters.docs.story`: `null` when `parameters.docs.disable` is set; inline (`inline` defaults to `false`) `{ story, inline: true, height, autoplay, forceInitialArgs, primary, renderStoryToElement }`; otherwise `{ story, inline: false, height, primary }`, `height` falling back to `docs.story.iframeHeight`, then `'100px'` | `[AST:code/addons/docs/src/blocks/blocks/Story.tsx:L75]` |
| `extractTitle` | function | `extractTitle(title: ComponentTitle)` (return type not annotated) | The last `/`-separated segment of the trimmed `title` (or `title` itself when that segment is empty): what `Title` shows for a meta's title | `[AST:code/addons/docs/src/blocks/blocks/Title.tsx:L24]` |
| `anchorBlockIdFromId` | function | `anchorBlockIdFromId(storyId: string)` (return type not annotated) | Returns `` `anchor--${storyId}` ``, the id `Anchor` gives its `div` | `[AST:code/addons/docs/src/blocks/blocks/Anchor.tsx:L4]` |
| `slugs` | const | `GithubSlugger` (`new GithubSlugger()`) | The one `github-slugger` instance `Heading` and `Subheading` share to turn a string child, lowercased, into the heading's anchor id | `[AST:code/addons/docs/src/blocks/blocks/Heading.tsx:L15]` |

### External docs

Doc blocks rendered from project annotations through an `ExternalPreview`, a `Preview` subclass in `blocks/external/`.

| Export | Kind | Props / Type | Purpose | Source |
|---|---|---|---|---|
| `ExternalDocs` | component | `ExternalDocs<TRenderer extends Renderer = Renderer>({ projectAnnotationsList, children }: PropsWithChildren<ExternalDocsProps<TRenderer>>)` | Composes `projectAnnotationsList` (`composeConfigs`), keeps one `ExternalPreview` of the result across renders, and renders the `Docs` block with the preview's docs context and a page that renders `children` | `[AST:code/addons/docs/src/blocks/blocks/external/ExternalDocs.tsx:L26]` |
| `ExternalDocsProps` | type | `ExternalDocsProps<TRenderer extends Renderer = Renderer> = { projectAnnotationsList: ProjectAnnotations<TRenderer>[] }` | `ExternalDocs`'s own props | `[AST:code/addons/docs/src/blocks/blocks/external/ExternalDocs.tsx:L11]` |
| `ExternalDocsContainer` | component | `{ projectAnnotations: any; children?: ReactNode }` (`React.FC<React.PropsWithChildren<{ projectAnnotations: any }>>`) | Creates a module-level `ExternalPreview` from `projectAnnotations` on its first render (later renders reuse it), provides the preview's docs context through `DocsContext`, and renders `children` in a `ThemeProvider` with `ensure(themes.light)` | `[AST:code/addons/docs/src/blocks/blocks/external/ExternalDocsContainer.tsx:L12]` |

### Block types and constants

| Export | Kind | Type / Value | Purpose | Source |
|---|---|---|---|---|
| `Of` | type | `Parameters<DocsContextProps['resolveOf']>[0]`, that is `ModuleExport \| 'component' \| 'meta' \| 'story'` | What an `of` prop takes: `Title`, `Subtitle` and `Description` take `of?: Of`, and `useOf` takes an `Of` first | `[AST:code/addons/docs/src/blocks/blocks/useOf.ts:L11]` |
| `Component` | type | `any` | Declared `export type Component = any`, under a `// TODO` comment | `[AST:code/addons/docs/src/blocks/blocks/types.ts:L7]` |
| `PRIMARY_STORY` | const | `'^'` | Nothing else in the repository's `code/` tree reads it | `[AST:code/addons/docs/src/blocks/blocks/types.ts:L3]` |
| `DescriptionType` | enum | `{ INFO = 'info', NOTES = 'notes', DOCGEN = 'docgen', AUTO = 'auto' }` | Declared in `Description.tsx`; the `Description` block's props hold only `of`, and nothing else in `code/` reads the enum | `[AST:code/addons/docs/src/blocks/blocks/Description.tsx:L9]` |

### Block props types

The props types the block modules export, each at its declaration. `blocks/blocks/index.ts` re-exports every block module, so `@storybook/addon-docs/blocks` exports these with the blocks.

| Export | Kind | Type | Purpose | Source |
|---|---|---|---|---|
| `AnchorProps` | interface | `{ storyId: string }` | The `Anchor` block's own props; the block takes `PropsWithChildren<AnchorProps>`, so `children` too | `[AST:code/addons/docs/src/blocks/blocks/Anchor.tsx:L6]` |
| `DocsContainerProps` | interface | `DocsContainerProps<TFramework extends Renderer = Renderer> { context: DocsContextProps<TFramework>; theme?: ThemeVars }` | The `DocsContainer` block's own props; the block takes `PropsWithChildren<DocsContainerProps>`, at the default `Renderer`, so `children` too | `[AST:code/addons/docs/src/blocks/blocks/DocsContainer.tsx:L18]` |
| `DocsProps` | type | `DocsProps<TRenderer extends Renderer = Renderer> = { docsParameter: Parameters; context: DocsContextProps<TRenderer> }` | The `Docs` block's props, both required | `[AST:code/addons/docs/src/blocks/blocks/Docs.tsx:L12]` |
| `DocsStoryProps` | type | `{ of: ModuleExport; expanded?: boolean; withToolbar?: boolean; __forceInitialArgs?: boolean; __primary?: boolean }` | The `DocsStory` block's props: `of` is required, and the two `__` props are internal | `[AST:code/addons/docs/src/blocks/blocks/types.ts:L9]` |
| `HeadingProps` | interface | `{ disableAnchor?: boolean }` | The own props of `Heading` and `Subheading`, which take `PropsWithChildren<HeadingProps>`, so `children` too | `[AST:code/addons/docs/src/blocks/blocks/Heading.tsx:L11]` |
| `SourceParameters` | type | `SourceCodeProps & { type?: SourceType; transform?: (code: string, storyContext: ReturnType<DocsContextProps['getStoryContext']>) => string \| Promise<string>; originalSource?: string }`, with `SourceCodeProps` the pure `Source` component's `{ language?: SupportedLanguage; code?: string; format?: ComponentProps<typeof SyntaxHighlighter>['format']; dark?: boolean; copyable?: boolean }`, which the blocks entry does not export | The type `useSourceProps` reads a story's `parameters.docs.source` as (it falls back to its `language` and `dark` when the props leave them out), and the base of `SourceProps` | `[AST:code/addons/docs/src/blocks/blocks/Source.tsx:L16]` `[AST:code/addons/docs/src/blocks/components/Source.tsx:L39]` `[SRC:code/addons/docs/src/blocks/blocks/Source.tsx:L141]` |
| `SourceProps` | type | `SourceParameters & { of?: ModuleExport; __forceInitialArgs?: boolean }` | The `Source` block's props, every one optional (each listed in [`Source` props detail](#source-props-detail)) | `[AST:code/addons/docs/src/blocks/blocks/Source.tsx:L28]` |
| `StoryProps` | type | `StoryRefProps & StoryParameters`, with the module-local `StoryRefProps = { of?: ModuleExport; meta?: ModuleExports }` and `StoryParameters = { inline?: boolean; height?: string; autoplay?: boolean; __forceInitialArgs?: boolean; __primary?: boolean }` | The `Story` block's props, every one optional (the two `__` props are internal); `getStoryId` takes them first | `[AST:code/addons/docs/src/blocks/blocks/Story.tsx:L60]` |

## DocsRenderer

Entry: `code/addons/docs/src/index.ts` exports `DocsRenderer`, a plain class, not a React component: `class DocsRenderer<TRenderer extends Renderer>` with two members, `render: DocsRenderFunction<TRenderer>`, which mounts the `Docs` block for a docs entry (inside an `MDXProvider` and an error boundary) into a DOM element through React, and `unmount: (element: HTMLElement) => void`, which unmounts it. The docs preview instantiates it; rarely imported directly; registered via `addons: ['@storybook/addon-docs']` in `main.ts`. `[AST:code/addons/docs/src/DocsRenderer.tsx:L48]` `[AST:code/addons/docs/src/index.ts:L8]`

## Control Primitives

The primitive control components that back `Controls` / `ArgTypes` panels. Imported as `import { BooleanControl, ... } from '@storybook/addon-docs/blocks'` when building a **custom controls panel** (addon UI). For normal story authoring the `Controls` doc-block is sufficient — these are the lower-level renderers it composes.

### Control value / config types

| Export | Kind | Signature | Source |
|---|---|---|---|
| `ControlProps<T>` | interface | `{ name: string; value?: T; defaultValue?: T; argType?: ArgType; onChange: (value?: T) => T \| void; onFocus?: (evt: any) => void; onBlur?: (evt: any) => void }` — base props shared by all control components | `[AST:code/addons/docs/src/blocks/controls/types.ts:L3]` |
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
| `BooleanControl` | component | `FC<BooleanProps>` — toggle switch | `[AST:code/addons/docs/src/blocks/controls/Boolean.tsx:L117]` |
| `ColorControlProps` | type | `ControlProps<ColorValue> & ColorConfig` | `[AST:code/addons/docs/src/blocks/controls/Color.tsx:L360]` |
| `ColorProps` | type | `ColorControlProps` — the controls barrel's alias for the color control's props | `[AST:code/addons/docs/src/blocks/controls/index.tsx:L10]` |
| `ColorControl` | component | `(props: ColorControlProps) => JSX.Element` — color picker with color-space cycling | `[AST:code/addons/docs/src/blocks/controls/Color.tsx:L361]` |
| `DateProps` | type | `ControlProps<DateValue> & DateConfig` | `[AST:code/addons/docs/src/blocks/controls/Date.tsx:L68]` |
| `DateControl` | component | `FC<DateProps>` — date + time picker | `[AST:code/addons/docs/src/blocks/controls/Date.tsx:L69]` |
| `parseDate` | function | `(value: string) => Date` — YYYY-MM-DD parse helper | `[AST:code/addons/docs/src/blocks/controls/Date.tsx:L11]` |
| `parseTime` | function | `(value: string) => Date` — HH:MM parse helper | `[AST:code/addons/docs/src/blocks/controls/Date.tsx:L18]` |
| `formatDate` | function | `(value: Date \| number) => string` | `[AST:code/addons/docs/src/blocks/controls/Date.tsx:L26]` |
| `formatTime` | function | `(value: Date \| number) => string` | `[AST:code/addons/docs/src/blocks/controls/Date.tsx:L34]` |
| `FilesControlProps` | interface | `extends ControlProps<string[]> { accept?: string }` | `[AST:code/addons/docs/src/blocks/controls/Files.tsx:L11]` |
| `FilesControl` | component | `FC<FilesControlProps>` — file input | `[AST:code/addons/docs/src/blocks/controls/Files.tsx:L40]` |
| `NumberControl` | component | `FC<NumberProps>`, with the module-local `NumberProps = ControlProps<NumberValue \| null> & NumberConfig` — number input with min/max/step | `[AST:code/addons/docs/src/blocks/controls/Number.tsx:L28]` |
| `parse` | function | `(value: string) => number \| undefined` — Number control parse helper | `[AST:code/addons/docs/src/blocks/controls/Number.tsx:L17]` |
| `format` | function | `(value: NumberValue) => string` — Number control format helper | `[AST:code/addons/docs/src/blocks/controls/Number.tsx:L22]` |
| `ObjectProps` | type | `ControlProps<ObjectValue> & ObjectConfig` | `[AST:code/addons/docs/src/blocks/controls/Object.tsx:L164]` |
| `ObjectControl` | component | `FC<ObjectProps>` — JSON tree editor | `[AST:code/addons/docs/src/blocks/controls/Object.tsx:L166]` |
| `RangeControl` | component | `FC<RangeProps>`, with the module-local `RangeProps = ControlProps<NumberValue \| null> & RangeConfig` — slider with min/max labels | `[AST:code/addons/docs/src/blocks/controls/Range.tsx:L178]` |
| `TextProps` | type | `ControlProps<TextValue \| undefined> & TextConfig` | `[AST:code/addons/docs/src/blocks/controls/Text.tsx:L11]` |
| `TextControl` | component | `FC<TextProps>` — textarea with max-length | `[AST:code/addons/docs/src/blocks/controls/Text.tsx:L23]` |
| `OptionsProps` | type | `ControlProps<OptionsSelection> & OptionsConfig` | `[AST:code/addons/docs/src/blocks/controls/options/Options.tsx:L40]` |
| `OptionsControl` | component | `FC<OptionsProps>` — dispatcher → CheckboxControl / RadioControl / SelectControl | `[AST:code/addons/docs/src/blocks/controls/options/Options.tsx:L41]` |
| `CheckboxControl` | component (internal, not importable) | `FC<CheckboxProps>` (module-local props) — multi-select checkbox group that `OptionsControl` renders for `check` / `inline-check`. The controls barrel re-exports only `OptionsControl` and `OptionsProps` from `options/` (`controls/options/index.ts:1` → `Options.tsx`). | `[AST:code/addons/docs/src/blocks/controls/options/Checkbox.tsx:L57]` |
| `RadioControl` | component (internal, not importable) | `FC<RadioProps>` (module-local props) — single-select radio group that `OptionsControl` renders for `radio` / `inline-radio`; import `OptionsControl` instead. | `[AST:code/addons/docs/src/blocks/controls/options/Radio.tsx:L57]` |
| `SelectControl` | component (internal, not importable) | `FC<SelectProps>` (module-local props) — dropdown that `OptionsControl` renders for `select` / `multi-select`; import `OptionsControl` instead. | `[AST:code/addons/docs/src/blocks/controls/options/Select.tsx:L170]` |

**Custom controls panel usage:** You rarely need to import these individually — the `Controls` doc-block handles dispatching automatically based on `argTypes[key].control.type`. Reach for the primitives only when building an addon that renders its own controls UI (e.g., a visual-testing panel that needs inline range sliders).
