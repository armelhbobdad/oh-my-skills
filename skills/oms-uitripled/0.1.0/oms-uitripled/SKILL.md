---
name: oms-uitripled
description: >
  Installs React 19 and Next.js 16 UI components, blocks, and pages from the
  uitripled shadcn-compatible registry (the react-shadcn variant). Use when
  composing landing pages, dashboards, or UI from 171 animated Framer Motion
  components via "npx shadcn@latest add @uitripled/COMPONENT_ID". Covers the
  registry catalog, CLI install paths, ThemeProvider and UILibraryProvider
  setup, shadcn/ui primitives, and the @uitripled/utils helpers. Do NOT use
  this skill for the deferred react-baseui or react-carbon variants (they
  will ship as separate skills), and do NOT generate barrel imports from the
  react-shadcn package — its src/index.ts file is empty by design.
---

## Overview

uitripled is a Turborepo monorepo that distributes 171 animated React components
(shadcn/ui variant) via a **copy-paste** model: the CLI copies source files into
your project — it is not an installable npm package for direct imports. All
components are built with React 19, Next.js 16, TypeScript, Tailwind CSS 4, and
Framer Motion.

- **Source:** `github.com/moumen-soliman/uitripled` @ `a5ffb45b` (master)
- **Version:** `@uitripled/react-shadcn@0.1.0` | `uitripled` CLI `@1.1.0`
- **Tier:** Deep — AST-verified extraction + QMD enrichment
- **Scope:** `react-shadcn` variant only (171/278 registry items). react-baseui (88) and react-carbon (19) are deferred to separate skills.
- **Registry catalog:** 171 entries — 15 pages, 38 blocks, 99 components, 19 UI leaves. `[SRC:packages/registry/registry.json:L1]`

## Quick Start

**Install a component** — the authoritative path per the project's own LLM docs
uses the `shadcn` CLI with the `@uitripled/` namespace:

```bash
npx shadcn@latest add @uitripled/hero-section-shadcnui
# the entry declares neither of these, but hero-section.tsx imports both:
npx shadcn@latest add button
npm install lucide-react
```

`[SRC:apps/docs/public/llms-full.txt:L49]` — confirmed across all 171 shadcn entries. The `hero-section-shadcnui` entry declares no `registryDependencies` and only the npm `dependencies` `framer-motion` and `react`, but `hero-section.tsx` imports `Button` from `@/components/ui/button` and icons from `lucide-react`, so the example compiles only once both are added. Most entries under-declare like this: check each copied file's imports (`references/integration.md` → Page ← block ← component composition). `[SRC:packages/registry/registry.json:L2968]` `[SRC:packages/components/react-shadcn/src/components/sections/hero-section.tsx:L3]`

**Alternative CLI path** (standalone `uitripled` package, same output):

```bash
npx uitripled add hero-section-shadcnui
npx uitripled add hero-section-shadcnui --overwrite
```

`[SRC:packages/uitripled/src/index.ts:L15]` `[SRC:packages/uitripled/README.md:L16]`

**Wrap your app in the mandatory providers** (both are required for
theme-aware and variant-aware components):

```tsx
// app/providers.tsx
"use client";
import { ThemeProvider } from "@/components/theme-provider";
import { UILibraryProvider } from "@/components/ui-library-provider";

export function Providers({ children }: { children: React.ReactNode }) {
  return (
    <ThemeProvider defaultTheme="system">
      <UILibraryProvider>{children}</UILibraryProvider>
    </ThemeProvider>
  );
}
```

`[AST:packages/components/react-shadcn/src/components/theme-provider.tsx:L18]`
`[AST:packages/components/react-shadcn/src/ui-library-provider.tsx:L31]`

**Use a component.** Every installed component requires `"use client"` because
all 171 shadcn entries depend on `framer-motion` and `react`:

```tsx
"use client";
import { HeroSection } from "@/components/uitripled/hero-section-shadcnui";

export default function Page() {
  return <HeroSection />;
}
```

`[SRC:apps/docs/public/llms-full.txt:L77]`

<!-- [MANUAL:additional-notes-quickstart] -->
<!-- Add custom notes here. This section is preserved during skill updates. -->
<!-- [/MANUAL:additional-notes-quickstart] -->

## Common Workflows

**Compose a landing page from blocks:**
`hero-section-shadcnui → feature-cards-block-shadcnui → testimonials-block-shadcnui → pricing-section-shadcnui → cta-block-shadcnui → footer-block-shadcnui`

**Install a page with its dependency graph:**
`npx shadcn@latest add @uitripled/<page>` → shadcn CLI walks `registryDependencies` (e.g., upstream shadcn/ui `button`, `card`) → also installs npm `dependencies` (`framer-motion`, `react`) `[SRC:packages/registry/registry.json:L7]` → then add the shadcn/ui primitives and npm packages (most often `lucide-react`) the copied file imports but the entry does not declare (`references/integration.md`)

**Switch design system variant at runtime:**
`UILibraryProvider (default shadcnui) → useUILibrary() → setSelectedLibrary("baseui" | "carbon")` — persists to `localStorage` under key `uitripled-selected-library` `[SRC:packages/components/react-shadcn/src/ui-library-provider.tsx:L12]`

**Toggle dark mode:**
`ThemeProvider → useTheme() → toggleTheme()` — wraps `next-themes`, persists to `uitripled-theme` key `[SRC:packages/components/react-shadcn/src/components/theme-provider.tsx:L11]`

**Merge Tailwind classes in copied components:**
`cn(className, "extra-classes")` from your project's `@/lib/utils`, the helper `npx shadcn init` writes: the copied react-shadcn files that use `cn` import it from there `[SRC:packages/components/react-shadcn/src/components/native/native-hover-card-shadcnui.tsx:L5]`. `@uitripled/utils`' `cn`, a thin wrapper over `clsx` + `tailwind-merge`, is the private workspace implementation that react-shadcn's own `src/lib/utils.ts` wraps `[SRC:packages/utils/src/cn.ts:L4]` `[SRC:packages/components/react-shadcn/src/lib/utils.ts:L1]` `[SRC:packages/utils/package.json:L4]`

## Component Catalog

| Category | Count | Key components |
|----------|-------|----------------|
| components | 57 | ai-chat-interface, ai-glow-input, animated-accordion, animated-dialog, animated-navbar |
| sections | 38 | hero-block, about-us-section, feature-cards-block, cta-hero-block, footer-block |
| native | 21 | native-hover-card, native-button, native-avatar-with-name, native-counter-up, bottom-modal |
| cards | 16 | animated-card-stack, credit-card, cinema-ticket, glass-blog-card, project-card |
| page | 15 | about-us-page, profile-page, hero-section, faq-section, scroll-reveal |
| decorative | 9 | floating-gradient, gradient-animation, dynamic-tag-cloud, holographic-wall, spotlight-section |
| micro | 8 | ripple-click-button, shimmer-button, elastic-switch, heart-favorite, ai-unlock-animation |
| resumes | 4 | minimal-resume, professional-resume, resume-card, standard-resume |
| data | 2 | animated-progress, cash-flow-chart |
| forms | 1 | wizard-form |

**Registry types (role):** `registry:page` (15) and `registry:block` (38) are the **index surface** — browse by category/subcategory. `registry:component` (99) and `registry:ui` (19) are the **reference surface** — smaller pieces, each installed by its own name: `registryDependencies` name only the upstream shadcn/ui `button` and `card`, never a uitripled entry, so composing a page or block pulls in no other uitripled component. `[SRC:packages/registry/registry.json:L1]`

**Design system variant:** react-shadcn (primary, 171 entries). react-baseui (88) and react-carbon (19) exist in the upstream repo but are out of scope for this skill.

<!-- [MANUAL:additional-notes-catalog] -->
<!-- Add custom notes here. This section is preserved during skill updates. -->
<!-- [/MANUAL:additional-notes-catalog] -->

## Key Types

```ts
// ThemeProvider's defaultTheme prop
type ThemeMode = "light" | "dark" | "system";

// @uitripled/utils exports the full 4-member union
type UILibrary = "shadcnui" | "baseui" | "carbon" | "react";
// NOTE: the react-shadcn package declares its own 3-member UILibrary ("shadcnui" | "baseui" | "carbon",
// src/types.ts), and UILibraryProvider / useUILibrary are typed with it: "react" is not assignable

// registry.json entry `type` values: a JSON field, not an exported TypeScript type
// "registry:page" | "registry:block" | "registry:component" | "registry:ui"

// Tailwind class composer return
cn(...inputs: ClassValue[]): string
```

`[AST:packages/components/react-shadcn/src/components/theme-provider.tsx:L9]` `[AST:packages/utils/src/types.ts:L3]` `[AST:packages/components/react-shadcn/src/types.ts:L1]` `[SRC:packages/components/react-shadcn/src/ui-library-provider.tsx:L3]` `[SRC:packages/registry/registry.json:L1]` `[SRC:packages/utils/src/cn.ts:L4]`

The component props interfaces (e.g., `NativeHoverCardProps`, the props of `NativeHoverCard`: `imageSrc` and `name` required, its nine other members optional), the full `Component` shapes from `@uitripled/utils` and `@uitripled/registry`, the Landing Builder types (`BuilderComponent`, `SavedProject`, etc.) and the grid types (`GridCell`, `BentoPreset`) are documented in `references/types.md`. `[AST:packages/components/react-shadcn/src/components/native/native-hover-card-shadcnui.tsx:L9]`

## Architecture at a Glance

- **`packages/registry/registry.json`** — Source of truth for the 278-item catalog (278 total, 171 react-shadcn). Shadcn-compatible format with `type`, `registryDependencies`, `dependencies`, `files`.
- **`packages/components/react-shadcn/`** — Component source. Subtrees: `src/ui/` (19 shadcn/ui primitives — Button, Card, Dialog, etc.), `src/components/` (171 motion components grouped by category), `src/components/theme-provider.tsx`, `src/ui-library-provider.tsx` (setup entry points), `src/lib/utils.ts` (a `cn` wrapper over `@uitripled/utils`' `cn`).
- **`packages/uitripled/`** — Standalone CLI (`npx uitripled add <name>`). Fetches from `https://ui.tripled.work/r/<name>.json`. Independent from the shadcn CLI path.
- **`packages/utils/`** — `@uitripled/utils` workspace package exporting `cn` (Tailwind class merger), `UILibrary`/`ComponentCategory`/`Component` types, and the Landing Builder helpers (`sanitizeSlug`, `generateGridCode`, `mergeComponentImports`, etc.).
- **`apps/docs/public/llms.txt` + `llms-full.txt`** — Project-authored AI-optimized docs shipped alongside the gallery site. Authoritative CLI install command source.

## CLI

**Preferred (shadcn namespace — per project AI docs):**
```bash
npx shadcn@latest add @uitripled/<component-id>
```
`[SRC:apps/docs/public/llms-full.txt:L49]`

**Preferred path rationale:** The project's authoritative AI docs (`apps/docs/public/llms.txt`, introduced in PR #8 per issue #7) standardized on `npx shadcn@latest add @uitripled/<name>` across all 171 entries. Both CLI paths still work and both fetch from `https://ui.tripled.work/r/<name>.json`, but the shadcn path is the documented one. `[QMD:oms-uitripled-temporal:prs.md]`

**Alternative (standalone `uitripled` CLI):**
```bash
npx uitripled                             # show usage
npx uitripled add <component-id>          # install a component
npx uitripled add <component-id> --overwrite  # overwrite existing files
```
`[SRC:packages/uitripled/src/index.ts:L10]` `[SRC:packages/uitripled/bin/cli.js:L7]`

The standalone CLI fetches JSON from `https://ui.tripled.work/r/{component}.json` and writes files to `src/components/`, `app/components/`, or `components/` (first that exists) `[SRC:packages/uitripled/src/utils/registry.ts:L3]` `[SRC:packages/uitripled/src/commands/add.ts:L45]`.

<!-- [MANUAL:additional-notes-api] -->
<!-- Add custom notes here. This section is preserved during skill updates. -->
<!-- [/MANUAL:additional-notes-api] -->

## Full API Reference

Detailed provider signatures, prop tables, hook return shapes, hydration behavior, and usage examples live in `references/setup.md` (`ThemeProvider`, `useTheme`, `UILibraryProvider`, `useUILibrary`) and `references/utils.md` (`cn` + Landing Builder helpers: `sanitizeSlug`, `generateUniqueSlug`, `GAP_VALUES`, `generateGridCode`, `initializeCells`, `mergeComponentImports`). The standalone `uitripled add` CLI implementation notes (interactive prompt, install-path priority `src/components` → `app/components` → `components`, `--overwrite` semantics, dependency hinting) and the `fetchComponent` helper pulling `https://ui.tripled.work/r/{name}.json` are in `references/catalog.md`. Provenance: `[AST:packages/components/react-shadcn/src/components/theme-provider.tsx:L18]` `[AST:packages/components/react-shadcn/src/ui-library-provider.tsx:L31]` `[SRC:packages/utils/src/cn.ts:L4]` `[SRC:packages/uitripled/src/commands/add.ts:L8]`.

**Component API.** Every other export of `@uitripled/react-shadcn` `src/`, with its signature copied from the source, its install id and its purpose, is in four files: `references/ui-primitives.md` (the shadcn/ui primitives: `Avatar`, `Badge`, `Checkbox`, `Dialog*`, `DropdownMenu*`, `Select*`, `Tabs*`, `Tooltip*`, `badgeVariants`, `buttonVariants`, ...), `references/native-components.md` (the `Native*` components, `VerifiedBadge`, `SocialLoginButton`), `references/motion-components.md` (motion-core and category components, the Grid Generator panels and the `GridCell` component they render) and `references/blocks-and-sections.md` (sections, blocks and composite components such as `AIChatInterface` and `KanbanBoard`). `bentoPresets` is in `references/utils.md`, and the `@uitripled/registry` arrays (`componentsRegistry`, `nativeComponents`, `uiComponents`) are in `references/catalog.md`. `[SRC:packages/components/react-shadcn/src/components/components/chat/ai-chat-interface.tsx:L54]` `[SRC:packages/registry/src/index.tsx:L8]`

<!-- [MANUAL:additional-notes-reference] -->
<!-- Add custom notes here. This section is preserved during skill updates. -->
<!-- [/MANUAL:additional-notes-reference] -->

## Full Type Definitions

Full field details for `Component` (both the `@uitripled/utils` and `@uitripled/registry` variants), `BuilderComponent`, `BuilderProjectPage`, `SavedProject`, `GridCell`, `BentoPreset`, the full `UILibrary`/`ComponentCategory` enumerations, and the complete `registry.json` schema (including `registryDependencies` vs `dependencies` distinction and the upstream shadcn/ui `button`/`card` resolution) live in `references/types.md`, cited from `packages/utils/src/types.ts`, `packages/components/react-shadcn/src/types.ts`, and `packages/registry/registry.json`. The props types the components take (`NativeButtonProps`, `NativeNotchProps`, `SocialProvider`, `GridPreviewProps`, `BadgeProps`, `ButtonProps`, ...) are in its "Component props types" section, copied from `packages/components/react-shadcn/src/`.

## Full Integration Patterns

Provider ordering rule, subpath import patterns (`@uitripled/react-shadcn/ui/<primitive>`, `.../src/components/...`), per-category composition recipes, `next-themes` integration + hydration timing, shadcn-CLI-vs-`uitripled`-CLI comparison, Tailwind CSS 4 prerequisite, and the rationale for `src/index.ts` being empty by design all live in `references/integration.md`.
