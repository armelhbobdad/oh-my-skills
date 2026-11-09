# Utils Reference: `@uitripled/utils`

## Contents

- [cn](#cn)
- [Landing Builder helpers](#landing-builder-helpers)
- [Grid helpers](#grid-helpers)
- [Bento presets](#bento-presets)
- [Import merging](#import-merging)
- [Types re-exported from utils](#types-re-exported-from-utils)

Source package: `packages/utils/`. Barrel at `packages/utils/src/index.ts` re-exports from every sub-module `[SRC:packages/utils/src/index.ts:L1]`:

```ts
export * from "./cn";
export * from "./grid-utils";
export * from "./merge-imports";
export * from "./builder-utils";
export * from "./types";
```

## cn

**Source:** `packages/utils/src/cn.ts`
**Provenance:** `[SRC:packages/utils/src/cn.ts:L4]`

```ts
import { clsx, type ClassValue } from "clsx";
import { twMerge } from "tailwind-merge";

export function cn(...inputs: ClassValue[]) {
  return twMerge(clsx(inputs));
}
```

The source leaves the return type to inference: `twMerge` returns a `string`.

Standard shadcn/ui class-merging helper. `packages/components/react-shadcn/src/lib/utils.ts` is not a copy of it: that file imports this function as `baseCn` from `@uitripled/utils` and exports its own `cn`, a wrapper that passes every argument on to `baseCn`, so the `@uitripled/react-shadcn/lib/utils` subpath depends on `@uitripled/utils` (a `workspace:*` dependency of the react-shadcn package) `[SRC:packages/components/react-shadcn/src/lib/utils.ts:L1]` `[SRC:packages/components/react-shadcn/src/lib/utils.ts:L3]` `[SRC:packages/components/react-shadcn/package.json:L85]`. A component the CLI copies brings neither file: each react-shadcn entry ships one file, and the 40 of those 171 files that use `cn` import it from your project's `@/lib/utils` (the helper `npx shadcn init` writes); the other 131 import no `cn`. The react-baseui and react-carbon entries, outside this skill, import `cn` from `@uitripled/utils` instead `[SRC:packages/registry/registry.json:L1]` `[SRC:packages/components/react-shadcn/src/components/native/native-hover-card-shadcnui.tsx:L5]` `[SRC:packages/components/react-baseui/src/components/native/native-button-baseui.tsx:L3]`.

## Landing Builder helpers

**Source:** `packages/utils/src/builder-utils.ts`

```ts
export const sanitizeSlug = (value: string) => string;                        // L7
export function generateUniqueSlug(baseName: string, existingSlugs: string[]): string; // L14
export function createPage(name: string, existingSlugs: string[]): BuilderProjectPage; // L33
export function extractSavedPages(project: SavedProject): SavedProjectPage[]; // L52
export function countSavedProjectComponents(project: SavedProject): number;   // L70
```

- `sanitizeSlug`: lowercases, replaces non-alphanumerics with `-`, trims leading/trailing `-`, caps length at 48 chars.
- `generateUniqueSlug`: computes `const baseSlug = sanitizeSlug(baseName) || "page"` and returns `baseSlug` when `existingSlugs` does not include it, else `{baseSlug}-2`, `-3`, ... until it finds a free slot.
- `createPage`: builds a fresh `BuilderProjectPage` with `crypto.randomUUID()` (falls back to `page-{timestamp}-{random}`) and a unique slug derived from `name` via `generateUniqueSlug`. Empty `components` array.
- `extractSavedPages`: normalizes a `SavedProject` into `SavedProjectPage[]`. If the project already has `pages[]`, returns it as-is. Otherwise synthesizes a single `"Landing"` page using `project.entryPageId` (or a slugified project name) as the id, `project.components ?? []` as content, and `project.code` if present — this handles the legacy single-page project shape.
- `countSavedProjectComponents`: totals the `components.length` across all pages (via `extractSavedPages`). Nothing in the repo calls it: the Landing Builder's Load Project dialog computes the same total inline.

The Landing Builder (`apps/docs/app/builder/`) runs the docs app's own copy of this file, `apps/docs/lib/builder-utils.ts`, which differs only in importing its types from `@/types/builder`, and calls `createPage`, `extractSavedPages` and `generateUniqueSlug` from it to name and manage saved pages. Nothing imports these helpers from `@uitripled/utils`. `[SRC:packages/utils/src/builder-utils.ts:L7]` `[SRC:packages/utils/src/builder-utils.ts:L33]` `[SRC:packages/utils/src/builder-utils.ts:L52]` `[SRC:packages/utils/src/builder-utils.ts:L70]`

## Grid helpers

**Source:** `packages/utils/src/grid-utils.ts`

```ts
export interface GridCell { row: number; col: number; rowSpan: number; colSpan: number; }
export interface BentoPreset { name: string; cols: number; rows: number; cells: GridCell[]; }

export const GAP_VALUES: number[] = [0, 1, 2, 3, 4, 5, 6, 8, 10, 12];
export const getGapSliderIndex: (gapValue: number) => number;
export const getGapValueFromIndex: (index: number) => number;
export const generateGridCode: (
  cells: GridCell[],
  cols: number,
  gap: number,
  options?: { useClassName?: boolean; includeBg?: boolean }
) => string;
export const initializeCells: (cols: number, rows: number) => GridCell[];
export const getCellKey: (row: number, col: number) => string;
export const isCellInSelection: (row: number, col: number, selectedCells: string[]) => boolean;
```

`GAP_VALUES` deliberately skips `7`, `9`, and `11` (Tailwind's non-canonical gap steps). `[SRC:packages/utils/src/grid-utils.ts:L23]`

`getGapSliderIndex(gapValue)` returns the index of `gapValue` in `GAP_VALUES`, or `0` when it is not one of them. `packages/components/react-shadcn/src/lib/grid-utils.ts` is a byte-identical copy of this file, so the react-shadcn subpath `@uitripled/react-shadcn/lib/grid-utils` exports the same helpers. `[SRC:packages/utils/src/grid-utils.ts:L32]` `[SRC:packages/components/react-shadcn/src/lib/grid-utils.ts:L32]`

Nothing outside `packages/utils/` imports this file. The Grid Generator (`apps/docs/app/grid-generator/page.tsx`) imports `generateGridCode`, `getCellKey` and `initializeCells` from the react-shadcn copy (`@uitripled/react-shadcn/lib/grid-utils`), and the Grid Generator panels in `packages/components/react-shadcn/src/components/grid/` import the same copy: `SettingsPanel` uses `getGapSliderIndex` and `getGapValueFromIndex`, and `GridPreview` uses `isCellInSelection`.

## Bento presets

**Source:** `packages/components/react-shadcn/src/lib/grid-presets.ts`

```ts
export const bentoPresets: BentoPreset[] = [ … ];
```

8 Grid Generator presets, each a `BentoPreset` (`name`, `cols`, `rows`, `cells`; see Grid helpers above): Classic Bento, Feature Hero, Dashboard Pro, Masonry Style, Portfolio Grid, Magazine Layout, App Interface, Content Hub. The react-shadcn package ships it beside its own copy of the grid helpers, so import both from the `@uitripled/react-shadcn/lib/<file>` subpath. `[SRC:packages/components/react-shadcn/src/lib/grid-presets.ts:L7]`

```ts
import { bentoPresets } from "@uitripled/react-shadcn/lib/grid-presets";
import { generateGridCode } from "@uitripled/react-shadcn/lib/grid-utils";

const preset = bentoPresets[0];
const code = generateGridCode(preset.cells, preset.cols, 4);
```

## Import merging

**Source:** `packages/utils/src/merge-imports.ts`

```ts
export function mergeComponentImports(code: string): string;  // L6
```

Takes a concatenated blob of multiple React component files (what the Landing Builder produces when exporting a landing page) and returns the same code with:

1. All `import` statements moved to the top
2. Duplicate imports merged (default / named / namespace / side-effect)
3. A single `"use client"` directive at the top if any source file had one

`[SRC:packages/utils/src/merge-imports.ts:L6]`

The Landing Builder's code view (`apps/docs/components/builder-code-view.tsx`) calls a byte-identical copy, `apps/docs/lib/merge-imports.ts`; nothing imports this function from `@uitripled/utils`.

## Types re-exported from utils

**Source:** `packages/utils/src/types.ts`

```ts
type UILibrary = "shadcnui" | "baseui" | "carbon" | "react";

const uiLibraryLabels: Record<UILibrary, string>;

type ComponentCategory =
  | "microinteractions" | "components" | "page" | "data"
  | "decorative" | "blocks" | "resumes" | "forms" | "cards" | "native";

type Component = {
  id: string;
  name: string;
  description: string;
  category: ComponentCategory;
  tags: string[];
  component: React.ComponentType<any>;
  baseuiComponent?: React.ComponentType<any>;
  carbonComponent?: React.ComponentType<any>;
  variants?: Array<{ id: string; name: string; description: string; component: React.ComponentType<any>; code?: string }>;
  code?: string;
  codePath: string;
  duration?: string;
  easing?: string;
  isFree?: boolean;
  display?: boolean;
  availableIn?: UILibrary[];
};

type TextContentEntry = { original: string; value: string };
type BuilderComponent = { id: string; animationId: string; animation: Component; textContent?: Record<string, TextContentEntry> };
type BuilderProjectPage = { id: string; name: string; slug: string; components: BuilderComponent[] };
type SavedProjectComponent = { id: string; animationId: string; textContent?: Record<string, TextContentEntry> };
type SavedProjectPage = { id: string; name: string; slug: string; components: SavedProjectComponent[]; code?: string };
type SavedProject = {
  name: string;
  uuid?: string;
  deploymentSlug?: string;
  pages?: SavedProjectPage[];
  entryPageId?: string;
  components?: SavedProjectComponent[];
  code?: string;
  savedAt: string;
  deploymentId?: string;
  deploymentUrl?: string;
};
```

`[AST:packages/utils/src/types.ts:L3]`

**Note — two `Component` definitions exist:**

1. The one above from `@uitripled/utils`, the type of this package's `BuilderComponent.animation` `[SRC:packages/utils/src/types.ts:L60]`. The docs app's Landing Builder uses its own `BuilderComponent` (`apps/docs/types/builder.ts`), whose `animation` is the docs app's own `Component` (`apps/docs/types/index.ts`).
2. A different one in `packages/registry/src/types.ts` (the type of the `@uitripled/registry` arrays). It adds `componentName`, `baseuiVariants` and `baseuiCodePath`, has no `carbonComponent`, `code` or `isFree`, and types `variants` as `any[]`; both types declare `baseuiComponent`, `duration` and `easing`. Its full shape is in `references/types.md` → Component (registry). `[AST:packages/registry/src/types.ts:L4]` `[AST:packages/utils/src/types.ts:L24]`

Both are distinct from the **shadcn-compatible schema in `registry.json`** — that uses `type` / `registryDependencies` / `dependencies` / `files` fields and is what the `shadcn` and `uitripled` CLIs consume. Don't confuse them.
