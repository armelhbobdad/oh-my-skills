# Full Type Definitions

## Contents

- [ThemeMode](#thememode)
- [UILibrary](#uilibrary)
- [ComponentCategory](#componentcategory)
- [Component (utils)](#component-utils)
- [Component (registry)](#component-registry)
- [GridCell / BentoPreset](#gridcell--bentopreset)
- [Builder types](#builder-types)
- [Registry schema (registry.json)](#registry-schema-registryjson)

## ThemeMode

**Source:** `packages/components/react-shadcn/src/components/theme-provider.tsx:L9`

```ts
export type ThemeMode = "light" | "dark" | "system";
```

Used as the type of `ThemeProvider`'s `defaultTheme` prop. `[SRC:packages/components/react-shadcn/src/components/theme-provider.tsx:L9]`

## UILibrary

**Source:** `packages/utils/src/types.ts:L3`

```ts
export type UILibrary = "shadcnui" | "baseui" | "carbon" | "react";
```

Also re-declared in `packages/components/react-shadcn/src/types.ts` as a subset of 3 values (`"shadcnui" | "baseui" | "carbon"`) — that is the runtime-reachable set in `UILibraryProvider`. `[SRC:packages/components/react-shadcn/src/types.ts:L1]`

## ComponentCategory

**Source:** `packages/utils/src/types.ts:L12`

```ts
export type ComponentCategory =
  | "microinteractions"
  | "components"
  | "page"
  | "data"
  | "decorative"
  | "blocks"
  | "resumes"
  | "forms"
  | "cards"
  | "native";
```

Note the superset semantics: `category` values in `registry.json` do NOT include `"microinteractions"` (they use `"micro"`) or `"blocks"` (they use `"sections"`). The `ComponentCategory` type is used by the legacy in-memory registry, not by `registry.json` directly. `[SRC:packages/utils/src/types.ts:L12]`

## Component (utils)

**Source:** `packages/utils/src/types.ts:L25`

```ts
export type Component = {
  id: string;
  name: string;
  description: string;
  category: ComponentCategory;
  tags: string[];
  component: React.ComponentType<any>;
  baseuiComponent?: React.ComponentType<any>;
  carbonComponent?: React.ComponentType<any>;
  variants?: Array<{
    id: string;
    name: string;
    description: string;
    component: React.ComponentType<any>;
    code?: string;
  }>;
  code?: string;
  codePath: string;
  duration?: string;
  easing?: string;
  isFree?: boolean;
  display?: boolean;
  availableIn?: UILibrary[];
};
```

`[SRC:packages/utils/src/types.ts:L25]`

## Component (registry)

**Source:** `packages/registry/src/types.ts:L4`

```ts
export type Component = {
  id: string;
  name: string;
  description: string;
  category: ComponentCategory;
  component: ComponentType<any>;
  codePath: string;
  availableIn?: UILibrary[];
  componentName?: string;
  tags: string[];
  display?: boolean;
  variants?: any[];
  baseuiVariants?: any[];
  duration?: string;
  easing?: string;
  baseuiComponent?: React.ComponentType<any>;
  baseuiCodePath?: string;
};
```

`[SRC:packages/registry/src/types.ts:L4]`

Nearly identical to the `@uitripled/utils` definition but adds `baseuiVariants`, `baseuiCodePath`, and omits `isFree`, `tags` required.

## GridCell / BentoPreset

**Source:** `packages/utils/src/grid-utils.ts:L5`

```ts
export interface GridCell {
  row: number;
  col: number;
  rowSpan: number;
  colSpan: number;
}

export interface BentoPreset {
  name: string;
  cols: number;
  rows: number;
  cells: GridCell[];
}
```

`[SRC:packages/utils/src/grid-utils.ts:L5]`

## Builder types

**Source:** `packages/utils/src/types.ts:L55`

```ts
export type TextContentEntry = { original: string; value: string };

export type BuilderComponent = {
  id: string;
  animationId: string;
  animation: Component;
  textContent?: Record<string, TextContentEntry>;
};

export type BuilderProjectPage = {
  id: string;
  name: string;
  slug: string;
  components: BuilderComponent[];
};

export type SavedProjectComponent = {
  id: string;
  animationId: string;
  textContent?: Record<string, TextContentEntry>;
};

export type SavedProjectPage = {
  id: string;
  name: string;
  slug: string;
  components: SavedProjectComponent[];
  code?: string;
};

export type SavedProject = {
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

`[SRC:packages/utils/src/types.ts:L55]`

## Registry schema (registry.json)

Not a TypeScript type — this is the shape the CLI expects. See SKILL.md "Full API Reference → Registry schema" for the table form. Source: `packages/registry/registry.json`. `[SRC:packages/registry/registry.json:L1]`
