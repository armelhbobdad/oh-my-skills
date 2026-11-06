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
- [Component props types](#component-props-types)

## ThemeMode

**Source:** `packages/components/react-shadcn/src/components/theme-provider.tsx:L9`

```ts
export type ThemeMode = "light" | "dark" | "system";
```

Used as the type of `ThemeProvider`'s `defaultTheme` prop. `[AST:packages/components/react-shadcn/src/components/theme-provider.tsx:L9]`

## UILibrary

**Source:** `packages/utils/src/types.ts:L3`

```ts
export type UILibrary = "shadcnui" | "baseui" | "carbon" | "react";
```

The react-shadcn package declares its own `UILibrary` in `packages/components/react-shadcn/src/types.ts` with three members (`"shadcnui" | "baseui" | "carbon"`). That narrower type is the one `UILibraryProvider` and `useUILibrary` import, so the restriction is in the type, not only at runtime: `selectedLibrary` is typed without `"react"`, and `setSelectedLibrary("react")` does not type-check. `[AST:packages/components/react-shadcn/src/types.ts:L1]` `[SRC:packages/components/react-shadcn/src/ui-library-provider.tsx:L3]`

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

Note the superset semantics: `category` values in `registry.json` do NOT include `"microinteractions"` (they use `"micro"`) or `"blocks"` (they use `"sections"`). The `ComponentCategory` type is used by the legacy in-memory registry, not by `registry.json` directly. `[AST:packages/utils/src/types.ts:L12]`

## Component (utils)

**Source:** `packages/utils/src/types.ts:L24`

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

`[AST:packages/utils/src/types.ts:L24]`

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

`[AST:packages/registry/src/types.ts:L4]`

The type of the `@uitripled/registry` arrays (`componentsRegistry`, `nativeComponents`, `uiComponents`). Against the `@uitripled/utils` definition it adds `componentName`, `baseuiVariants` and `baseuiCodePath`, has no `carbonComponent`, `code` or `isFree`, and types `variants` as `any[]`. Both declare `tags` as required, and both have `baseuiComponent`, `duration` and `easing`. `[SRC:packages/registry/src/index.tsx:L1]`

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

**Source:** `packages/utils/src/types.ts:L52`

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

`[SRC:packages/utils/src/types.ts:L52]`

## Registry schema (registry.json)

Not a TypeScript type: this is the JSON the `shadcn` and `uitripled` CLIs read. `packages/registry/registry.json` is one object whose `items` array holds the 278 entries (171 react-shadcn), and every entry carries the same nine fields. The `hero-section-shadcnui` entry (its `dependencies` array joined onto one line):

```json
{
  "name": "hero-section-shadcnui",
  "type": "registry:page",
  "title": "Hero Section",
  "description": "Hero section with staggered text and button reveal",
  "registryDependencies": [],
  "dependencies": ["framer-motion", "react"],
  "files": [
    {
      "path": "@uitripled/react-shadcn/src/components/sections/hero-section.tsx",
      "type": "registry:page",
      "target": "components/uitripled/hero-section-shadcnui.tsx"
    }
  ],
  "category": "page",
  "subcategory": "hero"
}
```

`registryDependencies` lists shadcn registry items, which the shadcn CLI also installs: the react-shadcn entries name only the upstream shadcn/ui `button` (95 entries) and `card` (5). `dependencies` lists npm packages: `framer-motion` and `react` in all 171, plus `lucide-react` in 7. Each entry ships one file, written at its `target`. `[SRC:packages/registry/registry.json:L1]` `[SRC:packages/registry/registry.json:L2968]`

The `type` counts, the categories and the upstream shadcn/ui resolution are in `references/catalog.md` (Registry types, Categories & subcategories, Upstream shadcn/ui resolution); the install walk is in `references/integration.md` → Page ← block ← component composition.

## Component props types

The props interfaces and type aliases `packages/components/react-shadcn/src/` exports, copied from the source at `a5ffb45`. The components that take them are in `references/ui-primitives.md`, `references/native-components.md` and `references/motion-components.md`.

### `GridPreviewProps`

**Source:** `packages/components/react-shadcn/src/components/grid/grid-preview.tsx`

```ts
export interface GridPreviewProps {
  cells: GridCellType[];
  cols: number;
  rows: number;
  gap: number;
  selectedCells: string[];
  onPointerDown: (row: number, col: number) => void;
  onPointerEnter: (row: number, col: number) => void;
  onPointerUp: () => void;
  onPointerLeave: () => void;
  onAddCell: (row: number, col: number) => void;
  onResetGrid: () => void;
  onUndo: () => void;
  onRedo: () => void;
  canUndo: boolean;
  canRedo: boolean;
}
```

`[SRC:packages/components/react-shadcn/src/components/grid/grid-preview.tsx:L10]`

### `NativeAvatarExpandProps`

**Source:** `packages/components/react-shadcn/src/components/native/native-avatar-expand-shadcnui.tsx`

```ts
export interface NativeAvatarExpandProps {
  /**
   * URL of the avatar image
   */
  src?: string;
  /**
   * Name of the person or entity
   */
  name: string;
  /**
   * Size variant
   * @default "md"
   */
  size?: "sm" | "md" | "lg" | "xl";
  /**
   * Additional classes for the container
   */
  className?: string;
  /**
   * Additional classes for the avatar
   */
  avatarClassName?: string;
  /**
   * Additional classes for the name text
   */
  nameClassName?: string;
}
```

`[SRC:packages/components/react-shadcn/src/components/native/native-avatar-expand-shadcnui.tsx:L8]`

### `NativeAvatarProps`

**Source:** `packages/components/react-shadcn/src/components/native/native-avatar-with-name-shadcnui.tsx`

```ts
export interface NativeAvatarProps {
  /**
   * URL of the avatar image
   */
  src?: string;
  /**
   * Name to display on hover
   */
  name: string;
  /**
   * Fallback text when image fails to load (usually initials)
   */
  fallback?: string;
  /**
   * Size variant of the avatar
   * Default: "md"
   */
  size?: "sm" | "md" | "lg" | "xl";
  /**
   * Direction from which the name appears
   * Default: "bottom"
   */
  direction?: "top" | "bottom" | "left" | "right";
  /**
   * Additional class names for the container
   */
  className?: string;
  /**
   * Additional class names for the name label
   */
  nameClassName?: string;
  /**
   * Additional class names for the motion container
   */
  motionClassName?: string;
}
```

`[SRC:packages/components/react-shadcn/src/components/native/native-avatar-with-name-shadcnui.tsx:L8]`

### `NativeButtonProps`

**Source:** `packages/components/react-shadcn/src/components/native/native-button-shadcnui.tsx`

```ts
export interface NativeButtonProps extends ButtonProps {
  children: ReactNode;
  loading?: boolean;
  glow?: boolean;
}
```

`[SRC:packages/components/react-shadcn/src/components/native/native-button-shadcnui.tsx:L9]`

### `NativeCounterUpProps`

**Source:** `packages/components/react-shadcn/src/components/native/native-counter-up-shadcnui.tsx`

```ts
export interface NativeCounterUpProps {
  /**
   * The target number to count up to.
   */
  value: number;
  /**
   * Duration of the animation in seconds.
   * Default: 2
   */
  duration?: number;
  /**
   * Text to display before the number (e.g., "$").
   */
  prefix?: string;
  /**
   * Text to display after the number (e.g., "+", "%").
   */
  suffix?: string;
  /**
   * Number of decimal places to show.
   * Default: 0
   */
  decimals?: number;
  /**
   * Accessible label describing what the counter represents.
   */
  label?: string;
  /**
   * Whether to start the animation on mount.
   * Default: true
   */
  autoStart?: boolean;
  className?: string;
}
```

`[SRC:packages/components/react-shadcn/src/components/native/native-counter-up-shadcnui.tsx:L7]`

### `NativeDeleteProps`

**Source:** `packages/components/react-shadcn/src/components/native/native-delete-shadcnui.tsx`

```ts
export interface NativeDeleteProps {
  /**
   * Callback when delete button is first clicked (shows confirmation)
   */
  onConfirm: () => void;
  /**
   * Callback when delete is confirmed
   */
  onDelete: () => void;
  /**
   * Text to show on the delete button
   * Default: "Delete"
   */
  buttonText?: string;
  /**
   * Text to show on the confirm button
   * Default: "Confirm"
   */
  confirmText?: string;
  /**
   * Size variant
   * Default: "md"
   */
  size?: "sm" | "md" | "lg";
  /**
   * Show icon in button
   * Default: true
   */
  showIcon?: boolean;
  /**
   * Additional class names for the container
   */
  className?: string;
  /**
   * Disable the button
   */
  disabled?: boolean;
}
```

`[SRC:packages/components/react-shadcn/src/components/native/native-delete-shadcnui.tsx:L9]`

### `NativeHoverCardProps`

**Source:** `packages/components/react-shadcn/src/components/native/native-hover-card-shadcnui.tsx`

```ts
export interface NativeHoverCardProps {
  /**
   * Image source URL
   */
  imageSrc: string;
  /**
   * Alt text for the image
   */
  imageAlt?: string;
  /**
   * Display name
   */
  name: string;
  /**
   * Username or handle
   */
  username?: string;
  /**
   * Description or bio text
   */
  description?: string;
  /**
   * Button text
   * Default: "View Profile"
   */
  buttonText?: string;
  /**
   * Button click handler
   */
  onButtonClick?: () => void;
  /**
   * Custom button component
   */
  buttonContent?: ReactNode;
  /**
   * Size of the image when collapsed
   * Default: "md"
   */
  size?: "sm" | "md" | "lg" | "xl";
  /**
   * Additional class names for the container
   */
  className?: string;
  /**
   * Card variant style
   */
  variant?: "default" | "glass" | "bordered";
}
```

`[AST:packages/components/react-shadcn/src/components/native/native-hover-card-shadcnui.tsx:L9]`

`packages/components/react-shadcn/src/components/native/native-hover-card.tsx` declares the same interface, member for member, for its own `NativeHoverCard` `[AST:packages/components/react-shadcn/src/components/native/native-hover-card.tsx:L9]`.

### `NativeImageCheckboxProps`

**Source:** `packages/components/react-shadcn/src/components/native/native-image-checkbox-shadcnui.tsx`

```ts
export interface NativeImageCheckboxProps {
  /**
   * URL of the image
   */
  src: string;
  /**
   * Alt text for the image
   */
  alt: string;
  /**
   * Whether the checkbox is selected
   */
  selected: boolean;
  /**
   * Callback when the checkbox is clicked
   */
  onSelect: (selected: boolean) => void;
  /**
   * Size variant
   * @default "md"
   */
  size?: "sm" | "md" | "lg" | "xl";
  /**
   * Additional classes for the container
   */
  className?: string;
  /**
   * Additional classes for the image
   */
  imageClassName?: string;
}
```

`[SRC:packages/components/react-shadcn/src/components/native/native-image-checkbox-shadcnui.tsx:L8]`

### `LikeUser`, `NativeLikesCounterProps`

**Source:** `packages/components/react-shadcn/src/components/native/native-likes-counter-shadcnui.tsx`

```ts
export interface LikeUser {
  id: string
  name: string
  avatar?: string
}

export interface NativeLikesCounterProps {
  count: number
  users?: LikeUser[]
  variant?: "default" | "subtle" | "outline" | "ghost"
  size?: "sm" | "default" | "lg"
  liked?: boolean
  onLike?: () => void
  onLoadMore?: () => Promise<LikeUser[]> | LikeUser[]
  hasMore?: boolean
  maxAvatars?: number
  maxVisibleInPopup?: number
  className?: string
}
```

`[SRC:packages/components/react-shadcn/src/components/native/native-likes-counter-shadcnui.tsx:L9]` `[SRC:packages/components/react-shadcn/src/components/native/native-likes-counter-shadcnui.tsx:L15]`

### `NativeLiquidButtonProps`

**Source:** `packages/components/react-shadcn/src/components/native/native-liquid-button-shadcnui.tsx`

```ts
export interface NativeLiquidButtonProps
  extends Omit<NativeButtonProps, "onClick" | "loading"> {
  /**
   * Progress value (0-100)
   */
  progress?: number;
  /**
   * Loading state
   */
  loading?: boolean;
  /**
   * Callback when button is clicked
   */
  onClick?: () => void | Promise<void>;
  /**
   * Visual variant
   * Default: "default"
   */
  liquidVariant?: "default" | "gradient" | "glow" | "wave";
  /**
   * Liquid color
   */
  liquidColor?: string;
  /**
   * Show percentage text
   * Default: false
   */
  showPercentage?: boolean;
  /**
   * Auto-simulate loading (for demo purposes)
   */
  autoSimulate?: boolean;
  /**
   * Success state
   */
  success?: boolean;
  /**
   * Error state
   */
  error?: boolean;
}
```

`[SRC:packages/components/react-shadcn/src/components/native/native-liquid-button-shadcnui.tsx:L12]`

### `NativeMagneticProps`

**Source:** `packages/components/react-shadcn/src/components/native/native-magnetic-shadcnui.tsx`

```ts
export interface NativeMagneticProps {
  /**
   * Content to apply the magnetic effect to.
   */
  children: React.ReactNode;
  /**
   * Strength of the magnetic pull (0-1 range recommended).
   * Default: 0.3
   */
  strength?: number;
  /**
   * Spring stiffness for the animation.
   * Default: 300
   */
  stiffness?: number;
  /**
   * Spring damping for the animation.
   * Default: 30
   */
  damping?: number;
  /**
   * Whether to scale up on hover.
   * Default: true
   */
  scaleOnHover?: boolean;
  /**
   * Wrapper element type.
   * Default: 'div'
   */
  as?: "div" | "button" | "a";
  /**
   * Link href (only applies when as="a").
   */
  href?: string;
  /**
   * Click handler.
   */
  onClick?: () => void;
  className?: string;
}
```

`[SRC:packages/components/react-shadcn/src/components/native/native-magnetic-shadcnui.tsx:L14]`

### `MorphingButtonAction`, `NativeMorphingButtonProps`

**Source:** `packages/components/react-shadcn/src/components/native/native-morphing-button-shadcnui.tsx`

```ts
export interface MorphingButtonAction {
  /**
   * Display label for the action.
   */
  label: string;
  /**
   * Icon to display alongside the label.
   */
  icon: React.ReactNode;
  /**
   * Callback when action is clicked.
   */
  onClick: () => void;
}

export interface NativeMorphingButtonProps {
  /**
   * Array of actions to display in the expanded menu.
   */
  actions: MorphingButtonAction[];
  /**
   * Position of the FAB.
   * Default: 'bottom-right'
   */
  position?: "bottom-right" | "bottom-left" | "top-right" | "top-left";
  /**
   * Whether to use fixed positioning.
   * Default: false (relative to container)
   */
  fixed?: boolean;
  /**
   * Custom icon when collapsed.
   */
  icon?: React.ReactNode;
  /**
   * Custom close icon when expanded.
   */
  closeIcon?: React.ReactNode;
  className?: string;
}
```

`[SRC:packages/components/react-shadcn/src/components/native/native-morphing-button-shadcnui.tsx:L14]` `[SRC:packages/components/react-shadcn/src/components/native/native-morphing-button-shadcnui.tsx:L29]`

### `ListItem`, `NativeNestedListProps`

**Source:** `packages/components/react-shadcn/src/components/native/native-nested-list-shadcnui.tsx`

```ts
export interface ListItem {
  /**
   * Unique identifier for the list item
   */
  id: string;
  /**
   * Display label for the list item
   */
  label: string;
  /**
   * Optional icon component
   */
  icon?: React.ReactNode;
  /**
   * Nested children items
   */
  children?: ListItem[];
  /**
   * Additional metadata
   */
  metadata?: Record<string, any>;
  /**
   * Optional URL to navigate to
   */
  href?: string;
  /**
   * Optional click handler
   */
  onClick?: (e: React.MouseEvent) => void;
}

export interface NativeNestedListProps {
  items: ListItem[];
  activeId?: string;
  onItemClick?: (item: ListItem) => void;
  size?: "sm" | "md" | "lg";
  showExpandIcon?: boolean;
  defaultExpanded?: boolean;
  className?: string;
  indentSize?: number;
}
```

`[SRC:packages/components/react-shadcn/src/components/native/native-nested-list-shadcnui.tsx:L11]` `[SRC:packages/components/react-shadcn/src/components/native/native-nested-list-shadcnui.tsx:L43]`

### `NotchSize`, `NotchPosition`, `NativeNotchProps`

**Source:** `packages/components/react-shadcn/src/components/native/native-notch-shadcnui.tsx`

```ts
export type NotchSize = "sm" | "md" | "lg";

export interface NotchPosition {
  /**
   * Top offset in pixels
   */
  top?: number;
  /**
    * Bottom offset in pixels
    */
  bottom?: number;
  /**
   * Horizontal alignment
   */
  align?: "left" | "center" | "right";
}

export interface NativeNotchProps {
  /**
   * Content to display when the notch is open
   */
  children?: React.ReactNode;
  /**
   * Custom content/icon to display when the notch is closed
   */
  collapsedIcon?: React.ReactNode;
  /**
   * Size variant
   * @default "md"
   */
  size?: NotchSize;
  /**
   * Initial position configuration
   */
  position?: NotchPosition;
  /**
   * Whether the notch is draggable
   * @default true
   */
  draggable?: boolean;
  /**
   * Default expanded state
   * @default false
   */
  defaultExpanded?: boolean;
  /**
   * Controlled expanded state
   */
  expanded?: boolean;
  /**
   * Callback when expanded state changes
   */
  onExpandedChange?: (expanded: boolean) => void;
  /**
   * Callback when notch is clicked
   */
  onClick?: (e: React.MouseEvent) => void;
  /**
   * Additional CSS classes
   */
  className?: string;
}
```

`[SRC:packages/components/react-shadcn/src/components/native/native-notch-shadcnui.tsx:L19]` `[SRC:packages/components/react-shadcn/src/components/native/native-notch-shadcnui.tsx:L24]` `[SRC:packages/components/react-shadcn/src/components/native/native-notch-shadcnui.tsx:L39]`

### `NativeNotificationBellProps`

**Source:** `packages/components/react-shadcn/src/components/native/native-notification-bell-shadcnui.tsx`

```ts
export interface NativeNotificationBellProps {
  /**
   * Number of notifications to display.
   * Default: 0
   */
  count?: number;
  /**
   * Whether to show the notification badge.
   * Automatically true if count > 0.
   */
  showBadge?: boolean;
  /**
   * Callback when the bell is clicked.
   */
  onClick?: () => void;
  /**
   * Callback when the bell rings (on mount if has notifications).
   */
  onRing?: () => void;
  /**
   * Custom icon to replace the bell.
   */
  icon?: React.ReactNode;
  /**
   * Size variant.
   * Default: 'md'
   */
  size?: "sm" | "md" | "lg";
  className?: string;
}
```

`[SRC:packages/components/react-shadcn/src/components/native/native-notification-bell-shadcnui.tsx:L8]`

### `NativeProfileNotchProps`

**Source:** `packages/components/react-shadcn/src/components/native/native-profile-notch-shadcnui.tsx`

```ts
export interface NativeProfileNotchProps {
  /**
   * Url of the user image
   */
  imageSrc: string;
  /**
   * Name of the user
   */
  name: string;
  /**
   * Handle or role of the user
   */
  username: string;
  /**
   * Custom content to show in expanded state
   */
  children?: React.ReactNode;
  /**
   * Size of the notch
   * @default "md"
   */
  size?: "sm" | "md" | "lg";
  /**
   * Class name for the container
   */
  className?: string;
  /**
   * Variant of the notch.
   * "default": expands and pushes content.
   * "overlay": expands over content (absolute positioning).
   * @default "default"
   */
  variant?: "default" | "overlay";
}
```

`[SRC:packages/components/react-shadcn/src/components/native/native-profile-notch-shadcnui.tsx:L9]`

### `NativeStartNowProps`

**Source:** `packages/components/react-shadcn/src/components/native/native-start-now-shadcnui.tsx`

```ts
export interface NativeStartNowProps {
  /**
   * Callback when start button is clicked
   */
  onStart: () => void | Promise<void>;
  /**
   * Text to show on the button
   * Default: "Start Now"
   */
  label?: string;
  /**
   * Loading text during async action
   * Default: "Starting..."
   */
  loadingLabel?: string;
  /**
   * Success text after completion
   * Default: "Let's Go!"
   */
  successLabel?: string;
  /**
   * Size variant
   * Default: "md"
   */
  size?: "sm" | "md" | "lg";
  /**
   * Show sparkle animation on hover
   * Default: true
   */
  showRocket?: boolean;
  /**
   * Icon to use for Rocket and success state
   * Default: Rocket icon
   */
  icon?: ReactNode;
  /**
   * Additional class names for the container
   */
  className?: string;
  /**
   * Disable the button
   */
  disabled?: boolean;
  /**
   * Variant style
   * Default: "gradient"
   */
  variant?: "gradient" | "solid" | "outline";
}
```

`[SRC:packages/components/react-shadcn/src/components/native/native-start-now-shadcnui.tsx:L9]`

### `SocialProvider`, `SocialAnimation`, `SocialLoginButtonProps`

**Source:** `packages/components/react-shadcn/src/components/native/social-login-button-shadcnui.tsx`

```ts
export type SocialProvider = "github" | "google" | "x" | "vercel" | "linkedin";

export type SocialAnimation = "slide" | "scale" | "glow" | "shine" | "none";

export interface SocialLoginButtonProps extends ButtonProps {
  provider: SocialProvider;
  animation?: SocialAnimation;
  children?: ReactNode; // Optional, defaults to "Continue with [Provider]"
}
```

`[SRC:packages/components/react-shadcn/src/components/native/social-login-button-shadcnui.tsx:L7]` `[SRC:packages/components/react-shadcn/src/components/native/social-login-button-shadcnui.tsx:L8]` `[SRC:packages/components/react-shadcn/src/components/native/social-login-button-shadcnui.tsx:L10]`

### `BadgeProps`

**Source:** `packages/components/react-shadcn/src/ui/badge.tsx`

```ts
export interface BadgeProps
  extends React.HTMLAttributes<HTMLDivElement>,
    VariantProps<typeof badgeVariants> {}
```

`[SRC:packages/components/react-shadcn/src/ui/badge.tsx:L24]`

### `ButtonProps`

**Source:** `packages/components/react-shadcn/src/ui/button.tsx`

```ts
export interface ButtonProps
  extends React.ButtonHTMLAttributes<HTMLButtonElement>,
    VariantProps<typeof buttonVariants> {
  asChild?: boolean;
}
```

`[SRC:packages/components/react-shadcn/src/ui/button.tsx:L35]`

### `InputProps`

**Source:** `packages/components/react-shadcn/src/ui/input.tsx`

```ts
export type InputProps = React.InputHTMLAttributes<HTMLInputElement>;
```

`[SRC:packages/components/react-shadcn/src/ui/input.tsx:L4]`

### `LabelProps`

**Source:** `packages/components/react-shadcn/src/ui/label.tsx`

```ts
export type LabelProps = React.LabelHTMLAttributes<HTMLLabelElement>;
```

`[SRC:packages/components/react-shadcn/src/ui/label.tsx:L4]`

### `PasswordInputProps`

**Source:** `packages/components/react-shadcn/src/ui/password-input.tsx`

```ts
export type PasswordInputProps = Omit<
  React.InputHTMLAttributes<HTMLInputElement>,
  "type"
>;
```

`[SRC:packages/components/react-shadcn/src/ui/password-input.tsx:L9]`

### `TextareaProps`

**Source:** `packages/components/react-shadcn/src/ui/textarea.tsx`

```ts
export type TextareaProps = React.TextareaHTMLAttributes<HTMLTextAreaElement>;
```

`[SRC:packages/components/react-shadcn/src/ui/textarea.tsx:L4]`
