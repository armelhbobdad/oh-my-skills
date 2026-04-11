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
| `Canvas` | `{ of, meta, sourceState, withToolbar, className }` | Render story preview with optional source panel. `of` → story export from `import * as stories`. | `[AST:code/addons/docs/src/blocks.ts]` |
| `Story` | `{ of, expanded, ... }` | Render single story by import reference. | `[AST:code/addons/docs/src/blocks.ts]` |
| `Primary` | `{ of? }` | Render the first story (or specified meta's primary). | `[AST:code/addons/docs/src/blocks.ts]` |
| `Stories` | `{ of?, includePrimary?, title? }` | Render all stories from a CSF module as a list. | `[AST:code/addons/docs/src/blocks.ts]` |

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
| `Title` | `{ children? }` | Render page title (defaults to `meta.title`). |
| `Subtitle` | `{ children? }` | Render page subtitle (defaults to `parameters.docs.subtitle`). |
| `Description` | `{ of?, markdown? }` | Render auto-generated or custom description. Pulls from component JSDoc or `parameters.docs.description`. |

## Control blocks

| Component | Props | Purpose |
|---|---|---|
| `Controls` | `{ of?, include?, exclude?, sort? }` | Interactive controls panel for story args. |
| `ArgTypes` | `{ of?, include?, exclude?, sort? }` | Static arg types documentation table (read-only). |
| `Source` | `{ of?, code?, language?, dark?, format? }` | Formatted source code block for a story. |

## Content blocks

| Component | Props | Purpose |
|---|---|---|
| `Markdown` | `{ children }` | Render markdown content inside MDX. |
| `Heading` | `{ children }` | H2 with anchor link. |
| `Subheading` | `{ children }` | H3 with anchor link. |
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
| `Docs` | `{ context }` | Root docs container — rarely used directly. |
| `DocsPage` | — | Default Autodocs layout function. |
| `DocsContainer` | `{ context, children }` | MDX docs wrapper (provides context). |
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

Entry: `code/addons/docs/src/index.ts` exports `DocsRenderer` — the React component that renders an entire docs page. Rarely imported directly; registered via `addons: ['@storybook/addon-docs']` in `main.ts`. `[AST:code/addons/docs/src/index.ts:L1]`
