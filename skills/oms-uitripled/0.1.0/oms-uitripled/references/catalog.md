# Component Catalog Reference (react-shadcn variant, 171 entries)

## Contents

- [Registry types](#registry-types)
- [Categories & subcategories](#categories--subcategories)
- [Install each component](#install-each-component)
- [Manual import paths (workspace-mode)](#manual-import-paths-workspace-mode)
- [Upstream shadcn/ui resolution](#upstream-shadcnui-resolution)
- [Universal dependencies](#universal-dependencies)

## Registry types

Source: `packages/registry/registry.json` — 278 total items, 171 react-shadcn. `[SRC:packages/registry/registry.json:L1]`

| Type | Count (shadcn) | Role |
|------|----------------|------|
| `registry:page` | 15 | Index tier — full-page or section-level templates for a whole screen |
| `registry:block` | 38 | Index tier — larger composable sections (hero, footer, pricing) |
| `registry:component` | 99 | Reference tier — smaller composable components |
| `registry:ui` | 19 | Reference tier — leaf primitives (single-file UI elements) |

**Tiering rule for composition:** `page` and `block` entries are the discovery surface — browse by category. `component` and `ui` entries are the reference surface — they usually appear as `registryDependencies` of pages/blocks and are pulled in transitively by the shadcn CLI.

## Categories & subcategories

Source: `category` + `subcategory` fields in `registry.json`. `[SRC:packages/registry/registry.json:L1]`

| category | Count | Example subcategories |
|----------|-------|------------------------|
| components | 57 | chat(4), forms(10), inputs(3), modal(3), lists(2), tabs(1), buttons |
| sections | 38 | (mostly null — large hero/footer/pricing/blog blocks) |
| native | 21 | (mostly null — avatars, counters, notches, buttons, badges) |
| cards | 16 | (mostly null — ticket/credit/glass/project cards) |
| page | 15 | (mostly null — some are actually section-level templates) |
| decorative | 9 | background(3), other |
| micro | 8 | buttons(3), toggles(1), icons(1), links(1) |
| resumes | 4 | — |
| data | 2 | progress(1), charts(1) |
| forms | 1 | forms(1) (the wizard-form) |

## Install each component

Preferred (per project's own `apps/docs/public/llms.txt`):

```bash
npx shadcn@latest add @uitripled/<name>
# e.g.
npx shadcn@latest add @uitripled/hero-section-shadcnui
npx shadcn@latest add @uitripled/feature-cards-block-shadcnui
npx shadcn@latest add @uitripled/native-hover-card-shadcnui
```

Alternative (`uitripled` standalone CLI):

```bash
npx uitripled add <name>
npx uitripled add <name> --overwrite
```

Both install the same files. `[SRC:packages/uitripled/src/commands/add.ts:L8]` `[SRC:apps/docs/public/llms-full.txt:L49]`

## Manual import paths (workspace-mode)

Used by the project's own docs site (`apps/docs/`) and documented in `llms-full.txt`. For external consumers who `npm install @uitripled/react-shadcn` directly (instead of copy-paste), the project exposes these subpath exports `[SRC:packages/components/react-shadcn/package.json:L7]`:

| Subpath | Maps to | Use for |
|---------|---------|---------|
| `@uitripled/react-shadcn/ui/*` | `dist/ui/*` | shadcn/ui primitives — Button, Card, Dialog, Input, Label, etc. |
| `@uitripled/react-shadcn/components/*` | `dist/components/*` | Motion components (up to 5 path segments deep) |
| `@uitripled/react-shadcn/src/*` | `src/*` (unbuilt) | Direct-from-source imports (used by llms-full.txt examples) |
| `@uitripled/react-shadcn/lib/*` | `dist/lib/*` | `cn` and other local helpers |
| `@uitripled/react-shadcn/styles/*` | `dist/styles/*.css` | CSS files |
| `@uitripled/react-shadcn/ui-library-provider` | `dist/ui-library-provider.*` | The `UILibraryProvider` setup component |

**Do NOT use the bare `@uitripled/react-shadcn` barrel import** — `packages/components/react-shadcn/src/index.ts` is literally `export {};` by design `[SRC:packages/components/react-shadcn/src/index.ts:L2]`. The package forces consumers down either (a) the shadcn CLI copy-paste path, or (b) the subpath-import path. There is no tree-shakable root export.

## Upstream shadcn/ui resolution

`registryDependencies` entries that are NOT uitripled registry names are resolved by shadcn against its own upstream registry. For react-shadcn entries:

- `button` → 95 entries depend on upstream shadcn/ui `button`
- `card` → 5 entries depend on upstream shadcn/ui `card`

When `npx shadcn@latest add @uitripled/<name>` runs, shadcn walks the DAG and installs upstream shadcn/ui primitives into your project's `components/ui/` directory (or wherever your `components.json` points). `[SRC:packages/registry/registry.json:L1]`

## Universal dependencies

**Every one of the 171 react-shadcn entries** declares these npm dependencies in `registry.json`:

```json
{"dependencies": ["framer-motion", "react"]}
```

A minority also depend on `lucide-react` (7 entries). Every component must be rendered in a client component (`"use client"`), and every parent must load under React 19. `[SRC:packages/registry/registry.json:L1]`
