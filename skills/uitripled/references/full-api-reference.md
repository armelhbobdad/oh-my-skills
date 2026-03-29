# Full API Reference

## Contents

- [Native Components (Interactive)](#native-components-interactive)
- [Section Blocks](#section-blocks)
- [Micro-Interactions](#micro-interactions)
- [Utility Functions](#utility-functions)
- [Shared Types](#shared-types)

### Native Components (Interactive)

Native components are the richest API surface — each has typed Props interfaces with JSDoc documentation, size variants, and Framer Motion animations.

See [references/native-components.md](native-components.md) for full Props tables per component.

#### NativeNotch

**Install:** `npx uitripled add native-notch-shadcnui`
**Available in:** shadcn/ui, Base UI
**Props:** `NativeNotchProps` — draggable expandable notch with controlled/uncontrolled modes
**Provenance:** `[AST:packages/components/react-shadcn/src/components/native/native-notch-shadcnui.tsx:L39]`

#### NativeMagnetic

**Install:** `npx uitripled add native-magnetic-shadcnui`
**Available in:** shadcn/ui, Base UI, Carbon
**Props:** `NativeMagneticProps` — magnetic cursor-attraction with spring animation
**Provenance:** `[AST:packages/components/react-shadcn/src/components/native/native-magnetic-shadcnui.tsx:L14]`

#### NativeHoverCard

**Install:** `npx uitripled add native-hover-card-shadcnui`
**Available in:** shadcn/ui, Base UI
**Props:** `NativeHoverCardProps` — profile card expanding from image on hover
**Provenance:** `[AST:packages/components/react-shadcn/src/components/native/native-hover-card-shadcnui.tsx:L9]`

#### NativeStartNow

**Install:** `npx uitripled add native-start-now-shadcnui`
**Available in:** shadcn/ui, Base UI
**Props:** `NativeStartNowProps` — animated CTA with loading/success states
**Provenance:** `[AST:packages/components/react-shadcn/src/components/native/native-start-now-shadcnui.tsx:L9]`

#### NativeProfileNotch

**Install:** `npx uitripled add native-profile-notch-shadcnui`
**Available in:** shadcn/ui, Base UI
**Props:** `NativeProfileNotchProps` — user profile expansion with overlay/push modes
**Provenance:** `[AST:packages/components/react-shadcn/src/components/native/native-profile-notch-shadcnui.tsx:L9]`

#### NativeMorphingButton

**Install:** `npx uitripled add native-morphing-button-shadcnui`
**Available in:** shadcn/ui, Base UI, Carbon
**Props:** `NativeMorphingButtonProps` — FAB that morphs into action menu
**Provenance:** `[AST:packages/components/react-shadcn/src/components/native/native-morphing-button-shadcnui.tsx:L29]`

#### NativeNotificationBell

**Install:** `npx uitripled add native-notification-bell-shadcnui`
**Available in:** shadcn/ui, Base UI, Carbon
**Props:** `NativeNotificationBellProps` — animated bell with badge count
**Provenance:** `[AST:packages/components/react-shadcn/src/components/native/native-notification-bell-shadcnui.tsx:L8]`

#### NativeDelete

**Install:** `npx uitripled add native-delete-shadcnui`
**Available in:** shadcn/ui, Base UI
**Props:** `NativeDeleteProps` — two-step confirmation delete button
**Provenance:** `[AST:packages/components/react-shadcn/src/components/native/native-delete-shadcnui.tsx:L9]`

#### NativeCounterUp

**Install:** `npx uitripled add native-counter-up-shadcnui`
**Available in:** shadcn/ui, Carbon
**Props:** `NativeCounterUpProps` — animated number counter
**Provenance:** `[AST:packages/components/react-shadcn/src/components/native/native-counter-up-shadcnui.tsx:L7]`

#### NativeFollowCursor

**Install:** `npx uitripled add native-follow-cursor-carbon`
**Available in:** Carbon
**Props:** `NativeFollowCursorProps`, `NativeFollowCursorAreaProps` — cursor-following label with spring animation
**Provenance:** `[AST:packages/components/react-carbon/src/components/native/carbon/native-follow-cursor-carbon.tsx:L14]`

### Section Blocks

Section blocks are self-contained page sections with no external Props — they embed sample data internally. Install and render directly.

Key sections: `HeroSection`, `PricingSection`, `TestimonialsBlock`, `FooterBlock`, `StatsSection`, `GlassmorphismHeroBlock`, `TeamSectionBlock`, `NewsletterSignupBlock`, `GalleryGridBlock`, `ServicesGridBlock`

`[SRC:packages/components/react-shadcn/src/components/sections/hero-section.tsx:L7]`

### Micro-Interactions

Micro-interactions are small, focused animation components: `ShimmerButton`, `RippleClick`, `MoodGradientButton`, `StackedCardCarousel`

`[SRC:packages/registry/registry.json:L1]`

### Utility Functions

#### cn(...inputs: ClassValue[]): string

Tailwind CSS class merger — combines `clsx` and `tailwind-merge`.

```tsx
import { cn } from "@uitripled/utils";
cn("px-4 py-2", condition && "bg-blue-500", "text-white");
```

`[SRC:packages/utils/src/cn.ts:L4]`

#### mergeComponentImports(code: string): string

Deduplicates and organizes imports when combining multiple component files.

`[SRC:packages/utils/src/merge-imports.ts:L5]`

#### generateUniqueSlug(baseName: string, existingSlugs: string[]): string

Generates a URL-friendly slug from `baseName` using `sanitizeSlug`, then appends a numeric suffix (`-2`, `-3`, ...) if the slug already exists in `existingSlugs`.

```tsx
import { generateUniqueSlug } from "@uitripled/utils";
const slug = generateUniqueSlug("My Page", ["my-page"]); // "my-page-2"
```

`[SRC:lib/builder-utils.ts]`

#### sanitizeSlug(value: string): string

Converts a string to a lowercase URL slug: strips non-alphanumeric characters, replaces with hyphens, removes leading/trailing hyphens, and truncates to 48 characters.

```tsx
import { sanitizeSlug } from "@uitripled/utils";
const slug = sanitizeSlug("Hello World!"); // "hello-world"
```

`[SRC:lib/builder-utils.ts]`

### Shared Types

```typescript
type UILibrary = "shadcnui" | "baseui" | "carbon" | "react";

type ComponentCategory =
  | "microinteractions" | "components" | "page" | "data"
  | "decorative" | "blocks" | "resumes" | "forms" | "cards" | "native";

type Component = {
  id: string; name: string; description: string;
  category: ComponentCategory; tags: string[];
  component: React.ComponentType<any>;
  codePath: string; availableIn?: UILibrary[];
};
```

`[AST:packages/utils/src/types.ts:L3]`
`[AST:packages/utils/src/types.ts:L12]`
`[AST:packages/utils/src/types.ts:L24]`
