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

`[SRC:packages/components/react-shadcn/src/components/theme-provider.tsx:L17]` `[SRC:packages/components/react-shadcn/src/ui-library-provider.tsx:L32]`

## Subpath import patterns

Valid subpath imports (from `packages/components/react-shadcn/package.json` `exports` field) `[SRC:packages/components/react-shadcn/package.json:L7]`:

```tsx
// shadcn/ui primitives (19 in src/ui/)
import { Button } from "@uitripled/react-shadcn/ui/button";
import { Card, CardContent, CardHeader } from "@uitripled/react-shadcn/ui/card";
import { Input } from "@uitripled/react-shadcn/ui/input";
import { Dialog, DialogContent } from "@uitripled/react-shadcn/ui/dialog";

// Motion components (from registry; up to 5 path segments)
import { NativeHoverCard } from "@uitripled/react-shadcn/components/native/native-hover-card";
import { HeroSection } from "@uitripled/react-shadcn/components/page/hero/hero-section";

// Direct from source (what llms-full.txt recommends)
import { HeroSection } from "@uitripled/react-shadcn/src/components/page/hero-section";

// Provider (top-level subpath)
import { UILibraryProvider, useUILibrary } from "@uitripled/react-shadcn/ui-library-provider";

// Local utils
import { cn } from "@uitripled/react-shadcn/lib/utils";
```

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

When you install `hero-section-shadcnui`, the shadcn CLI walks its `registryDependencies`:

```
@uitripled/hero-section-shadcnui
  └── (upstream) button       (shadcn/ui primitive — not uitripled)
      └── (npm) framer-motion
      └── (npm) react
```

For `feature-cards-block-shadcnui`:

```
@uitripled/feature-cards-block-shadcnui
  ├── (upstream) button       (shadcn/ui primitive)
  └── (upstream) card          (shadcn/ui primitive)
```

The uitripled registry does **not** contain entries for `button` or `card` — shadcn resolves them against its own upstream registry. `[SRC:packages/registry/registry.json:L1]`

For composing larger pages, inspect each entry's `registryDependencies` list in `registry.json` before `shadcn add` — you'll usually end up pulling in 1-3 shadcn/ui primitives and the full set of Framer Motion components for the target page.

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

`next-themes@^0.4.6` is declared in `packages/components/react-shadcn/package.json` dependencies. If you `npx uitripled add` any themed component, you need to install `next-themes` yourself — the CLI prints the dependency list as an install hint after copying files. `[SRC:packages/uitripled/src/commands/add.ts:L109]`

## Tailwind CSS 4 requirement

The project targets Tailwind CSS 4 (per `apps/docs/public/llms.txt`) `[SRC:apps/docs/public/llms.txt:L9]`. Components emit CSS custom properties (`bg-background`, `text-foreground`, `border-input`, etc.) that depend on a Tailwind v4 theme configuration. Before installing components:

1. Upgrade your project to Tailwind CSS v4
2. Ensure your `globals.css` declares the same CSS custom properties shadcn/ui expects (shadcn's `npx shadcn init` will scaffold them)
3. Configure your `components.json` with the same utils path alias (`@/lib/utils`) that the copied files use
