---
name: uitripled
description: >
  Provides UITripled animated React component library with 177 unique components
  across shadcn/ui, Base UI, and Carbon design system variants. Covers registry-based
  installation via CLI, Framer Motion animations, glassmorphism patterns, native
  interactive components with typed Props interfaces, section blocks, page templates,
  and micro-interactions. Use when building animated UI for React frameworks (Vite,
  Next.js, TanStack Start). Do NOT use for non-React frameworks or static HTML sites.
---

## Overview

UITripled is a TypeScript component library offering 177 unique animated UI components across three design system variants: shadcn/ui (primary, 171 entries), Base UI (88 entries), and Carbon (10 entries). Components are distributed via a centralized registry and installed through the `uitripled` CLI. All animations are powered by Framer Motion.

- **Source:** [moumen-soliman/uitripled](https://github.com/moumen-soliman/uitripled) @ master
- **Version:** 1.1.0
- **Language:** TypeScript (TSX)

`[SRC:packages/registry/registry.json:L1]`

## Quick Start

Install a component:

```bash
npx uitripled add native-button-shadcnui
```

Set up providers (required for theme and variant switching):

```tsx
import { ThemeProvider, UILibraryProvider } from "@uitripled/react-shadcn";

<ThemeProvider>
  <UILibraryProvider>
    <YourApp />
  </UILibraryProvider>
</ThemeProvider>
```

`[SRC:packages/components/react-shadcn/src/components/theme-provider.tsx:L18]`
`[SRC:packages/components/react-shadcn/src/ui-library-provider.tsx:L31]`

Use a native component with Props:

```tsx
import { NativeMagnetic } from "@uitripled/react-shadcn";

<NativeMagnetic strength={0.3} scaleOnHover>
  <button>Hover me</button>
</NativeMagnetic>
```

`[AST:packages/components/react-shadcn/src/components/native/native-magnetic-shadcnui.tsx:L14]`

<!-- [MANUAL:after-quick-start] -->
<!-- Add custom quick start notes here. This section is preserved during skill updates. -->
<!-- [/MANUAL:after-quick-start] -->

## Common Workflows

**Install and use a component:**
`npx uitripled add {component-id} → import Component from "components/uitripled/{component-id}" → render <Component />`

**Switch design system variants:**
`npx uitripled add native-button-baseui` (same component, Base UI styling) — all variants share the same Props interfaces

**Compose section blocks into pages:**
`npx uitripled add hero-section-shadcnui` → `npx uitripled add pricing-section-shadcnui` → combine in page layout

**Use native interactive components:**
Import component → pass typed Props (size, variant, callbacks) → Framer Motion handles animations automatically

**Merge multiple component imports:**
`import { mergeComponentImports } from "@uitripled/utils"` → `mergeComponentImports(combinedCode)` deduplicates imports across components

## Component Catalog

| Category | Count | Key Components |
|----------|-------|---------------|
| components | 57 | AI Chat Interface, AI Glow Input, Expanding Search Dock, Glass Sign-In Card, Multiple Accounts Switcher |
| sections | 38 | Hero Section, Pricing Section, Testimonials Block, Footer Block, Stats Section |
| native | 26 | NativeMagnetic, NativeNotch, NativeHoverCard, NativeStartNow, NativeProfileNotch |
| cards | 16 | Glassmorphism Statistics Card, Glassmorphism Portfolio Block |
| page | 15 | About Us Page, Notion Blog Page, Web Performance Page |
| decorative | 10 | Liquid Cursor, Glowy Waves Hero, Scroll Reveal |
| micro | 8 | Shimmer Button, Ripple Click, Mood Gradient Button |
| resumes | 4 | Resume templates |
| data | 2 | Interactive Logs Table |
| forms | 1 | Glass Sign-In |

**Design system variants:** shadcn/ui (primary), Base UI, Carbon
**Total components:** 177 unique | **With shadcn/ui:** 171 | **With Base UI:** 88 | **With Carbon:** 10

`[SRC:packages/registry/registry.json:L1]`

<!-- [MANUAL:after-catalog] -->
<!-- Add custom catalog notes here. This section is preserved during skill updates. -->
<!-- [/MANUAL:after-catalog] -->

## Key Types

### NativeNotchProps

| Prop | Type | Default | Required |
|------|------|---------|----------|
| children | `React.ReactNode` | — | no |
| collapsedIcon | `React.ReactNode` | — | no |
| size | `"sm" \| "md" \| "lg"` | `"md"` | no |
| position | `NotchPosition` | — | no |
| draggable | `boolean` | `true` | no |
| defaultExpanded | `boolean` | `false` | no |
| expanded | `boolean` | — | no |
| onExpandedChange | `(expanded: boolean) => void` | — | no |
| className | `string` | — | no |

`[AST:packages/components/react-shadcn/src/components/native/native-notch-shadcnui.tsx:L39]`

All 18 Props interfaces with full field details: see [references/native-components.md](references/native-components.md).

## Architecture at a Glance

- **Component variants:** 3 design systems — shadcn/ui (primary), Base UI, Carbon — each in `packages/components/react-{variant}/`
- **Registry:** Centralized at `packages/registry/registry.json` — 278 entries with category, dependencies, file paths
- **CLI tool:** `packages/uitripled/` — `npx uitripled add <component>` fetches from registry
- **Shared utilities:** `packages/utils/` — `cn()` (Tailwind merge), `mergeComponentImports()`, grid utils, builder utils
- **Types:** `UILibrary`, `ComponentCategory`, `Component` — shared across variants in `packages/utils/src/types.ts`
- **Animation layer:** Framer Motion powers all animations — universal dependency across all components

## CLI

```bash
# Install a component
npx uitripled add <component-id>

# Install with overwrite
npx uitripled add <component-id> --overwrite
```

Component IDs follow the pattern `{component-name}-{variant}` (e.g., `native-button-shadcnui`, `hero-section-baseui`). The CLI auto-detects your project's component directory (`src/components`, `app/components`, or `components`).

`[SRC:packages/uitripled/src/index.ts:L1]`
`[SRC:packages/uitripled/src/commands/add.ts:L8]`

## Full API Reference

> Extracted to [references/full-api-reference.md](references/full-api-reference.md). Full Props tables at [references/native-components.md](references/native-components.md).

## Full Type Definitions

> Extracted to [references/full-type-definitions.md](references/full-type-definitions.md).

## Full Integration Patterns

> Extracted to [references/full-integration-patterns.md](references/full-integration-patterns.md).
