# Utils Reference: `@uitripled/utils`

## Contents

- [cn](#cn)
- [Landing Builder helpers](#landing-builder-helpers)
- [Grid helpers](#grid-helpers)
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
**Provenance:** `[AST:packages/utils/src/cn.ts:L4]`

```ts
import { clsx, type ClassValue } from "clsx";
import { twMerge } from "tailwind-merge";

export function cn(...inputs: ClassValue[]): string {
  return twMerge(clsx(inputs));
}
```

Standard shadcn/ui class-merging helper. Identical implementation shipped at `packages/components/react-shadcn/src/lib/utils.ts` under a local path — if you copy-paste a component the helper comes with it; you don't need `@uitripled/utils` as a separate dependency.

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
- `generateUniqueSlug`: produces `{sanitizeSlug(baseName)}` if unique, else `{slug}-2`, `-3`, ... until it finds a free slot.
- `createPage`: builds a fresh `BuilderProjectPage` with `crypto.randomUUID()` (falls back to `page-{timestamp}-{random}`) and a unique slug derived from `name` via `generateUniqueSlug`. Empty `components` array.
- `extractSavedPages`: normalizes a `SavedProject` into `SavedProjectPage[]`. If the project already has `pages[]`, returns it as-is. Otherwise synthesizes a single `"Landing"` page using `project.entryPageId` (or a slugified project name) as the id, `project.components ?? []` as content, and `project.code` if present — this handles the legacy single-page project shape.
- `countSavedProjectComponents`: totals the `components.length` across all pages (via `extractSavedPages`) for display in project lists.

Used by the Landing Builder (`apps/docs/app/builder/`) to name and manage saved pages. `[AST:packages/utils/src/builder-utils.ts:L7]` `[AST:packages/utils/src/builder-utils.ts:L33]` `[AST:packages/utils/src/builder-utils.ts:L52]` `[AST:packages/utils/src/builder-utils.ts:L70]`

## Grid helpers

**Source:** `packages/utils/src/grid-utils.ts`

```ts
export interface GridCell { row: number; col: number; rowSpan: number; colSpan: number; }
export interface BentoPreset { name: string; cols: number; rows: number; cells: GridCell[]; }

export const GAP_VALUES: number[] = [0, 1, 2, 3, 4, 5, 6, 8, 10, 12];
export const getGapSliderIndex: (value: number) => number;
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

`GAP_VALUES` deliberately skips `7`, `9`, and `11` (Tailwind's non-canonical gap steps). `[AST:packages/utils/src/grid-utils.ts:L23]`

Used by the Grid Generator (`apps/docs/app/grid-generator/`) and Background Builder.

## Import merging

**Source:** `packages/utils/src/merge-imports.ts`

```ts
export function mergeComponentImports(code: string): string;  // L6
```

Takes a concatenated blob of multiple React component files (what the Landing Builder produces when exporting a landing page) and returns the same code with:

1. All `import` statements moved to the top
2. Duplicate imports merged (default / named / namespace / side-effect)
3. A single `"use client"` directive at the top if any source file had one

`[AST:packages/utils/src/merge-imports.ts:L6]`

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

1. The one above from `@uitripled/utils` (used by the Landing Builder's in-memory `componentsRegistry`).
2. A slightly different one in `packages/registry/src/types.ts` that extends with `baseuiVariants`, `duration`, `easing`, `baseuiComponent`, `baseuiCodePath`. `[SRC:packages/registry/src/types.ts:L4]`

Both are distinct from the **shadcn-compatible schema in `registry.json`** — that uses `type` / `registryDependencies` / `dependencies` / `files` fields and is what the `shadcn` and `uitripled` CLIs consume. Don't confuse them.
