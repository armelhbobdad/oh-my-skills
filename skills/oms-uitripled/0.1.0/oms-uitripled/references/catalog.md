# Component Catalog Reference (react-shadcn variant, 171 entries)

## Contents

- [Registry types](#registry-types)
- [Categories & subcategories](#categories--subcategories)
- [Install each component](#install-each-component)
- [Manual import paths (workspace-mode)](#manual-import-paths-workspace-mode)
- [Registry arrays (`@uitripled/registry`)](#registry-arrays-uitripledregistry)
- [Standalone CLI internals (`uitripled add`)](#standalone-cli-internals-uitripled-add)
- [Upstream shadcn/ui resolution](#upstream-shadcnui-resolution)
- [Universal dependencies](#universal-dependencies)

## Registry types

Source: `packages/registry/registry.json` — 278 total items, 171 react-shadcn. `[SRC:packages/registry/registry.json:L1]`

| Type | Count (shadcn) | Role |
|------|----------------|------|
| `registry:page` | 15 | Index tier — full-page or section-level templates for a whole screen |
| `registry:block` | 38 | Index tier — larger composable sections (hero, footer, pricing) |
| `registry:component` | 99 | Reference tier — smaller composable components |
| `registry:ui` | 19 | Reference tier — small animated pieces: 8 micro-interactions, 9 decorative effects and 2 data displays (`ai-unlock-animation-shadcnui`, `cash-flow-chart`, ...), not shadcn/ui primitives |

**Tiering rule for composition:** `page` and `block` entries are the discovery surface — browse by category. `component` and `ui` entries are the reference surface — install each by its own name: `registryDependencies` name only the upstream shadcn/ui `button` and `card`, never a uitripled entry, so the shadcn CLI does not pull one in transitively.

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

Used by the project's own docs site (`apps/docs/`) and documented in `llms-full.txt`. For external consumers who `npm install @uitripled/react-shadcn` directly (instead of copy-paste), the project exposes these subpath exports `[SRC:packages/components/react-shadcn/package.json:L8]`:

| Subpath | Maps to | Use for |
|---------|---------|---------|
| `@uitripled/react-shadcn/ui/*` | `dist/ui/*` | shadcn/ui primitives — Button, Card, Dialog, Input, Label, etc. |
| `@uitripled/react-shadcn/components/*` | `dist/components/*` | Motion components (up to 5 path segments deep) |
| `@uitripled/react-shadcn/src/*` | `src/*` (unbuilt) | Direct-from-source imports (used by llms-full.txt examples) |
| `@uitripled/react-shadcn/lib/*` | `dist/lib/*` | `cn` and other local helpers |
| `@uitripled/react-shadcn/styles/*` | `dist/styles/*.css` | CSS files |
| `@uitripled/react-shadcn/ui-library-provider` | `dist/ui-library-provider.*` | The `UILibraryProvider` setup component |

**Do NOT use the bare `@uitripled/react-shadcn` barrel import** — `packages/components/react-shadcn/src/index.ts` is literally `export {};` by design `[SRC:packages/components/react-shadcn/src/index.ts:L2]`. The package forces consumers down either (a) the shadcn CLI copy-paste path, or (b) the subpath-import path. There is no tree-shakable root export.

## Registry arrays (`@uitripled/registry`)

The in-memory component lists of the `@uitripled/registry` package (not the `registry.json` file the CLIs read). Its build entry is `src/index.tsx`, which defines `componentsRegistry` and re-exports both arrays `[SRC:packages/registry/src/index.tsx:L5]`. Each record is the registry package's `Component` type (see `references/types.md` → Component (registry)).

```ts
// packages/registry/src/index.tsx
export const componentsRegistry: Component[] = [ … ];
// packages/registry/src/registry/native.tsx
export const nativeComponents: Component[] = [ … ];
// packages/registry/src/registry/ui.tsx
export const uiComponents: Component[] = [ … ];
```

| Export | Holds | Source |
|--------|-------|--------|
| `componentsRegistry` | `[...nativeComponents, ...uiComponents]` | `[SRC:packages/registry/src/index.tsx:L8]` |
| `nativeComponents` | 77 `Component` records | `[SRC:packages/registry/src/registry/native.tsx:L218]` |
| `uiComponents` | 151 `Component` records | `[SRC:packages/registry/src/registry/ui.tsx:L179]` |

```ts
import { componentsRegistry } from "@uitripled/registry";

const ids = componentsRegistry.map((c) => c.id);
```

## Standalone CLI internals (`uitripled add`)

**Source:** `packages/uitripled/src/commands/add.ts`, `packages/uitripled/src/utils/registry.ts`

```ts
export async function add(componentName: string | undefined, options: { overwrite: boolean })
export async function fetchComponent(componentName: string)
```

- `fetchComponent(componentName)` requests `https://ui.tripled.work/r/{componentName}.json` and resolves to the parsed JSON, or to `null` on a 404; any other failed status throws `Failed to fetch component: {statusText}`. `[SRC:packages/uitripled/src/utils/registry.ts:L5]`
- `add(componentName, options)` prompts for a name when none is given, fetches the item with `fetchComponent`, and stops when it has no `files`. It installs under the first of `src/components`, `app/components` and `components` that exists (`components` when none does), asks for confirmation, then writes each file at its `target` (else `path`) less the first segment; an existing file is skipped unless `options.overwrite` is true. It ends with an `npm install` hint for the item's `dependencies`. `[SRC:packages/uitripled/src/commands/add.ts:L8]` `[SRC:packages/uitripled/src/commands/add.ts:L45]`
- `npx uitripled add [component] [-o, --overwrite]` calls `await add(component, options)`. `[SRC:packages/uitripled/src/index.ts:L15]`

The `uitripled` package publishes only its `dist` bin, so `fetchComponent` is called from inside `packages/uitripled/src/`, as `add` does:

```ts
import { fetchComponent } from "./utils/registry";

const item = await fetchComponent("hero-section-shadcnui");
if (item === null) {
  console.log("hero-section-shadcnui is not in the registry");
} else {
  console.log(item.files.length, "file(s) to install");
}
```

## Upstream shadcn/ui resolution

`registryDependencies` entries that are NOT uitripled registry names are resolved by shadcn against its own upstream registry. For react-shadcn entries:

- `button` → 95 entries depend on upstream shadcn/ui `button`
- `card` → 5 entries depend on upstream shadcn/ui `card`

When `npx shadcn@latest add @uitripled/<name>` runs, shadcn walks the DAG and installs the upstream shadcn/ui primitives the entry names into your project's `components/ui/` directory (or wherever your `components.json` points). Many files import primitives their entry does not name (`references/integration.md` → Page ← block ← component composition), so add those yourself. `[SRC:packages/registry/registry.json:L1]`

## Universal dependencies

**Every one of the 171 react-shadcn entries** declares these npm dependencies in `registry.json`:

```json
{"dependencies": ["framer-motion", "react"]}
```

Only 7 entries also declare `lucide-react`, although 127 of the 171 files import it: install it yourself. Every component must be rendered in a client component (`"use client"`), and every parent must load under React 19. `[SRC:packages/registry/registry.json:L1]`
