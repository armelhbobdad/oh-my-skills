# Integration Patterns

## Contents

- [Provider ordering rule](#provider-ordering-rule)
- [Subpath import patterns](#subpath-import-patterns)
- [Why src/index.ts is empty](#why-srcindexts-is-empty)
- [Page ← block ← component composition](#page--block--component-composition)
- [shadcn CLI vs uitripled CLI](#shadcn-cli-vs-uitripled-cli)
- [next-themes integration](#next-themes-integration)
- [Tailwind CSS 4 requirement](#tailwind-css-4-requirement)

## Provider ordering rule

**Rule:** `ThemeProvider` must be the outer provider, `UILibraryProvider` must be inner.

```tsx
<ThemeProvider defaultTheme="system">
  <UILibraryProvider>
    {children}
  </UILibraryProvider>
</ThemeProvider>
```

**Why:**

- `ThemeProvider` is a thin wrapper over `next-themes`' provider (with `attribute="class"` hardcoded). It mounts synchronously and sets the `class` attribute on `html` before children render.
- `UILibraryProvider` gates rendering on `isHydrated` — it returns `null` from the first render until a `useEffect` reads `localStorage`. If it sits outside `ThemeProvider`, the theme attribute is injected into a subtree that hasn't mounted yet, which triggers a flash of unthemed content when the library provider hydrates.

`[AST:packages/components/react-shadcn/src/components/theme-provider.tsx:L18]` `[AST:packages/components/react-shadcn/src/ui-library-provider.tsx:L31]`

## Subpath import patterns

Valid subpath imports (from `packages/components/react-shadcn/package.json` `exports` field) `[SRC:packages/components/react-shadcn/package.json:L8]`:

```tsx
// shadcn/ui primitives (19 in src/ui/)
import { Button } from "@uitripled/react-shadcn/ui/button";
import { Card, CardContent, CardHeader } from "@uitripled/react-shadcn/ui/card";
import { Input } from "@uitripled/react-shadcn/ui/input";
import { Dialog, DialogContent } from "@uitripled/react-shadcn/ui/dialog";

// Motion components (built from src/components/; up to 5 path segments)
import { NativeHoverCard } from "@uitripled/react-shadcn/components/native/native-hover-card";
import { HeroSection } from "@uitripled/react-shadcn/components/sections/hero-section";

// Direct from source (the ./src/* export maps the path as written, so keep the .tsx, as llms-full.txt does)
import { HeroSection } from "@uitripled/react-shadcn/src/components/sections/hero-section.tsx";

// Provider (top-level subpath)
import { UILibraryProvider, useUILibrary } from "@uitripled/react-shadcn/ui-library-provider";

// Local utils
import { cn } from "@uitripled/react-shadcn/lib/utils";
```

`HeroSection` is declared in `src/components/sections/hero-section.tsx` (there is no `src/components/page/hero-section.tsx`, and `src/components/page/hero/` holds only `staggered-text.tsx`); the `./src/*` export maps `./src/components/sections/hero-section` to a path with no file, so the direct-from-source import keeps the `.tsx`, as `llms-full.txt` writes it `[AST:packages/components/react-shadcn/src/components/sections/hero-section.tsx:L7]` `[SRC:packages/components/react-shadcn/package.json:L14]` `[SRC:apps/docs/public/llms-full.txt:L32724]`. `packages/registry/src/registry/ui.tsx` imports it without the extension, which resolves only through the workspace's tsconfig `paths` alias for `@uitripled/react-shadcn/src/*` (`apps/docs/tsconfig.json` declares the same), not through the package's `exports` `[SRC:packages/registry/src/registry/ui.tsx:L116]` `[SRC:packages/registry/tsconfig.json:L9]` `[SRC:apps/docs/tsconfig.json:L28]`. The `native/native-hover-card` subpath is built from `src/components/native/native-hover-card.tsx`, which declares a `NativeHoverCard` with the same signature and props as the `native-hover-card-shadcnui.tsx` file the registry ships (it memoizes the avatar element; the shipped file does not) `[AST:packages/components/react-shadcn/src/components/native/native-hover-card.tsx:L81]` `[AST:packages/components/react-shadcn/src/components/native/native-hover-card-shadcnui.tsx:L81]` `[SRC:packages/components/react-shadcn/src/components/native/native-hover-card.tsx:L108]`. The `lib/utils` `cn` wraps `@uitripled/utils`' `cn` (see `references/utils.md` → cn) `[SRC:packages/components/react-shadcn/src/lib/utils.ts:L1]`.

**Important:** These patterns work in the workspace dev loop (the `apps/docs/` site uses them heavily — 28+ call sites). They are **not** the primary distribution model. External consumers of the skill should prefer the CLI copy-paste path so the components land directly in their project.

## Why src/index.ts is empty

`packages/components/react-shadcn/src/index.ts` is literally:

```ts
// Export main components or keep empty if using subpath exports
export {};
```

`[SRC:packages/components/react-shadcn/src/index.ts:L2]`

This is deliberate. If the barrel re-exported everything, `import { Button } from "@uitripled/react-shadcn"` would pull in tree-shake-hostile code (all 232 source files share module-level imports of `framer-motion`, and most are `"use client"` components). The empty barrel forces consumers to either:

1. Use the CLI (`npx shadcn@latest add @uitripled/<name>`) — files land in your project, so there is nothing to tree-shake.
2. Use subpath imports (`@uitripled/react-shadcn/ui/button`) — only the requested file is loaded.

**Do not hand-write barrel imports from `@uitripled/react-shadcn`.** Compilers will succeed silently and resolve to `{}`.

## Page ← block ← component composition

When you install an entry, the shadcn CLI walks its `registryDependencies` and installs its npm `dependencies`. For `feature-cards-block-shadcnui` `[SRC:packages/registry/registry.json:L1689]`:

```
@uitripled/feature-cards-block-shadcnui
  ├── (upstream) button       (shadcn/ui primitive)
  ├── (upstream) card         (shadcn/ui primitive)
  └── (npm) framer-motion, react
      (not declared: lucide-react, which the file imports its icons from)
```

**Most entries under-declare.** 138 of the 171 react-shadcn entries import a shadcn/ui primitive or an npm package their entry does not declare, most often `lucide-react`; the primitives most often missing are `badge`, `card`, `button`, `avatar` and `input`. `feature-cards-block.tsx` imports its icons from `lucide-react`, which its entry leaves out `[SRC:packages/components/react-shadcn/src/components/sections/feature-cards-block.tsx:L4]`. After installing, check the copied file's imports and add the missing primitives (`npx shadcn@latest add <primitive>`) and packages (`npm install lucide-react`) yourself. `hero-section-shadcnui` declares no `registryDependencies` (`[]`) and only `framer-motion` and `react`, but `hero-section.tsx` imports `Button` from `@/components/ui/button` and icons from `lucide-react`, so it needs `npx shadcn@latest add button` and `npm install lucide-react` `[SRC:packages/registry/registry.json:L2968]` `[SRC:packages/components/react-shadcn/src/components/sections/hero-section.tsx:L3]`:

```
@uitripled/hero-section-shadcnui
  ├── registryDependencies: none   (the file imports button)
  └── (npm) framer-motion, react   (the file imports lucide-react)
```

`native-hover-card-shadcnui` likewise declares no `registryDependencies`, but `native-hover-card-shadcnui.tsx` imports `@/components/ui/avatar` and `@/components/ui/button` `[SRC:packages/registry/registry.json:L3806]` `[SRC:packages/components/react-shadcn/src/components/native/native-hover-card-shadcnui.tsx:L3]`.

The uitripled registry does **not** contain entries for `button` or `card` — shadcn resolves them against its own upstream registry. No `registryDependencies` value names a uitripled entry, so installing a page or block pulls in no other uitripled component. `[SRC:packages/registry/registry.json:L1]`

For composing larger pages, install each section, block or component by its own name, then read each copied file's imports: you'll usually add a few shadcn/ui primitives and `lucide-react` that the entries do not declare.

## shadcn CLI vs uitripled CLI

Two CLI paths exist — both consume the same `registry.json` but via different conventions.

| Property | `npx shadcn@latest add @uitripled/<name>` | `npx uitripled add <name>` |
|----------|-------------------------------------------|-----------------------------|
| Namespace | `@uitripled/<name>` (shadcn multi-registry) | bare `<name>` |
| Source | documented in `apps/docs/public/llms.txt` | documented in `packages/uitripled/README.md` |
| Registry URL | shadcn-managed | `https://ui.tripled.work/r/{name}.json` |
| Walks `registryDependencies` | yes (recursive) | no — single component only |
| Prompt for component | no | yes (interactive if name omitted) |
| `--overwrite` flag | via shadcn's defaults | explicit flag |
| Authoritative per project docs | **yes** | alternative |

`[SRC:packages/uitripled/src/commands/add.ts:L8]` `[SRC:packages/uitripled/src/utils/registry.ts:L3]` `[QMD:oms-uitripled-temporal:prs.md]` `[QMD:oms-uitripled-docs:llms-full.md]`

## next-themes integration

`ThemeProvider` delegates to `next-themes` with fixed options:

- `attribute="class"` — adds `class="dark"` / `class="light"` to `<html>`
- `enableSystem` — respects `prefers-color-scheme`
- `disableTransitionOnChange={false}` — keeps CSS transitions during theme changes
- `storageKey="uitripled-theme"`

`next-themes@^0.4.6` is declared in `packages/components/react-shadcn/package.json` dependencies. If you `npx uitripled add` any themed component, you need to install `next-themes` yourself — the CLI prints the dependency list as an install hint after copying files. `[SRC:packages/uitripled/src/commands/add.ts:L110]`

## Tailwind CSS 4 requirement

The project targets Tailwind CSS 4 (per `apps/docs/public/llms.txt`) `[SRC:apps/docs/public/llms.txt:L9]`. Components emit CSS custom properties (`bg-background`, `text-foreground`, `border-input`, etc.) that depend on a Tailwind v4 theme configuration. Before installing components:

1. Upgrade your project to Tailwind CSS v4
2. Ensure your `globals.css` declares the same CSS custom properties shadcn/ui expects (shadcn's `npx shadcn init` will scaffold them)
3. Configure your `components.json` with the same utils path alias (`@/lib/utils`) that the copied files use
