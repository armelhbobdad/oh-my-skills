# Native Components Reference (react-shadcn `src/components/native/`)

The `Native*` components (native-OS-inspired buttons, dialogs, notches, tooltips and badges) of `@uitripled/react-shadcn`, with their install ids. Signatures are copied from the source at `a5ffb45`; the purpose is the entry's `description` in `packages/registry/registry.json`.

## Contents

- [Install and import](#install-and-import)
- [Native components by file](#native-components-by-file)

## Install and import

Install a component with `npx shadcn@latest add @uitripled/<install id>`: the CLI writes the entry's `files[].target`, `components/uitripled/<install id>.tsx`, which you import from `@/components/uitripled/<install id>` `[SRC:packages/registry/registry.json:L1]` `[SRC:apps/docs/public/llms-full.txt:L49]`. A consumer of the npm package imports a subpath instead (`@uitripled/react-shadcn/components/<path>`, `/ui/<file>`, `/src/<path>`), never the bare package: `src/index.ts` is `export {};` `[SRC:packages/components/react-shadcn/package.json:L8]` `[SRC:packages/components/react-shadcn/tsup.config.ts:L4]` `[SRC:packages/components/react-shadcn/src/index.ts:L2]`. The props types are in `references/types.md` → Component props types; a props type the signature names and that file does not list is not exported by the source.

```bash
npx shadcn@latest add @uitripled/native-delete-shadcnui
```

```tsx
"use client";
import { NativeDelete } from "@/components/uitripled/native-delete-shadcnui";

export function RemoveRow({ onRemove }: { onRemove: () => void }) {
  return <NativeDelete onConfirm={() => {}} onDelete={onRemove} size="sm" />;
}
```

`onConfirm` (first click, shows the confirm button) and `onDelete` (confirmed) are required `NativeDeleteProps` fields; `size` is `"sm" | "md" | "lg"` `[SRC:packages/components/react-shadcn/src/components/native/native-delete-shadcnui.tsx:L9]`.

## Native components by file

```tsx
// components/native/native-avatar-expand-shadcnui.tsx
export function NativeAvatarExpand({ src, name, size = "md", className, avatarClassName, nameClassName }: NativeAvatarExpandProps)
// components/native/native-avatar-with-name-shadcnui.tsx
export function NativeAvatarWithName({ src, name, fallback, size = "md", direction = "bottom", className, nameClassName, motionClassName }: NativeAvatarProps)
// components/native/native-button-shadcnui.tsx
const NativeButton = ({ className, variant = "default", size = "lg", children, loading = false, glow = false, disabled, ...props }: NativeButtonProps) => …
// components/native/native-counter-up-shadcnui.tsx
export function NativeCounterUp({ value, duration = 2, prefix = "", suffix = "", decimals = 0, label, autoStart = true, className }: NativeCounterUpProps)
// components/native/native-delete-shadcnui.tsx
export function NativeDelete({ onConfirm, onDelete, buttonText = "Delete", confirmText = "Confirm", size = "md", showIcon = true, className, disabled = false }: NativeDeleteProps)
// components/native/native-dialog-shadcnui.tsx
const NativeDialog = Dialog;
const NativeDialogClose = DialogClose;
const NativeDialogContent = React.forwardRef<React.ElementRef<typeof DialogPrimitive.Content>, React.ComponentPropsWithoutRef<typeof DialogPrimitive.Content>>(…)
const NativeDialogDescription = BaseDialogDescription;
const NativeDialogFooter = DialogFooter;
const NativeDialogHeader = DialogHeader;
const NativeDialogOverlay = React.forwardRef<React.ElementRef<typeof DialogPrimitive.Overlay>, React.ComponentPropsWithoutRef<typeof DialogPrimitive.Overlay>>(…)
const NativeDialogPortal = DialogPortal;
const NativeDialogTitle = BaseDialogTitle;
const NativeDialogTrigger = DialogTrigger;
// components/native/native-flip-text-shadcnui.tsx
export function NativeFlipText({ words, duration = 2000, className }: NativeFlipTextProps)
// components/native/native-hover-card-shadcnui.tsx
export function NativeHoverCard({ imageSrc, imageAlt, name, username, description, buttonText = "View Profile", onButtonClick, buttonContent, size = "md", className, variant = "default" }: NativeHoverCardProps)
// components/native/native-image-checkbox-shadcnui.tsx
export function NativeImageCheckbox({ src, alt, selected, onSelect, size = "md", className, imageClassName }: NativeImageCheckboxProps)
// components/native/native-likes-counter-shadcnui.tsx
export function NativeLikesCounter({ count, users = [], variant = "default", size = "default", liked = false, onLike, onLoadMore, hasMore = false, maxAvatars = 5, maxVisibleInPopup = 5, className }: NativeLikesCounterProps)
// components/native/native-liquid-button-shadcnui.tsx
export function NativeLiquidButton({ children, className, variant = "default", size = "default", progress = 0, loading = false, onClick, disabled, liquidVariant = "default", liquidColor, showPercentage = false, autoSimulate = false, success = false, error = false, ...props }: NativeLiquidButtonProps)
// components/native/native-magnetic-shadcnui.tsx
export function NativeMagnetic({ children, strength = 0.3, stiffness = 300, damping = 30, scaleOnHover = true, as = "div", href, onClick, className }: NativeMagneticProps)
// components/native/native-morphing-button-shadcnui.tsx
export function NativeMorphingButton({ actions, position = "bottom-right", fixed = false, icon, closeIcon, className }: NativeMorphingButtonProps)
// components/native/native-nested-list-shadcnui.tsx
export function NativeNestedList({ items, activeId, onItemClick, size = "md", showExpandIcon = true, defaultExpanded = false, className, indentSize = 16 }: NativeNestedListProps)
// components/native/native-notch-shadcnui.tsx
export function NativeNotch({ children, collapsedIcon, size = "md", position = { top: 32, align: "center" }, draggable = true, defaultExpanded = false, expanded: controlledExpanded, onExpandedChange, onClick, className }: NativeNotchProps)
// components/native/native-notification-bell-shadcnui.tsx
export function NativeNotificationBell({ count = 0, showBadge, onClick, onRing, icon, size = "md", className }: NativeNotificationBellProps)
// components/native/native-profile-notch-shadcnui.tsx
export function NativeProfileNotch({ imageSrc, name, username, children, size = "md", className, variant = "default" }: NativeProfileNotchProps)
// components/native/native-start-now-shadcnui.tsx
export function NativeStartNow({ onStart, label = "Start Now", loadingLabel = "Starting...", successLabel = "Let's Go!", size = "md", showRocket = true, icon, className, disabled = false, variant = "gradient" }: NativeStartNowProps)
// components/native/native-tabs-shadcnui.tsx
export function NativeTabs({ items, defaultValue, className }: NativeTabsProps)
// components/native/native-tooltip-shadcnui.tsx
const NativeTooltip = ({ content, children, animation, ...props }: React.ComponentProps<typeof TooltipPrimitive.Root> & { content?: React.ReactNode; animation?: "blur" | "scale"; }) => …
const NativeTooltipContent = React.forwardRef<React.ElementRef<typeof TooltipPrimitive.Content>, React.ComponentPropsWithoutRef<typeof TooltipPrimitive.Content> & { animation?: "blur" | "scale"; }>(…)
const NativeTooltipProvider = ({ delayDuration = 100, ...props }: React.ComponentProps<typeof TooltipPrimitive.Provider>) => …
const NativeTooltipTrigger = TooltipPrimitive.Trigger;
// components/native/native-typewriter-shadcnui.tsx
export function NativeTypewriter({ content, speed = "medium", cursor = true, loop = false, startDelay = 0, morph = true, className }: NativeTypewriterProps)
// components/native/native-user-card-shadcnui.tsx
export function NativeUserCard({ imageSrc, name, handle, href = "#", onClick, className }: NativeUserCardProps)
// components/native/native-verified-badge-shadcnui.tsx
export function VerifiedBadge({ variant = "default", size = "md", className, showLabel = false, label = "Verified", icon, tooltip }: VerifiedBadgeProps)
export function VerifiedBadgeOutline({ variant = "default", size = "md", className, icon, tooltip }: Omit<VerifiedBadgeProps, "showLabel" | "label">)
export function VerifiedShieldBadge({ variant = "default", size = "md", className, icon, tooltip }: Omit<VerifiedBadgeProps, "showLabel" | "label">)
// components/native/social-login-button-shadcnui.tsx
const SocialLoginButton = ({ className, provider, animation = "none", children, ...props }: SocialLoginButtonProps) => …
```

| Export | Install id | Purpose | Source |
|--------|------------|---------|--------|
| `NativeAvatarExpand` | `@uitripled/native-avatar-expand-shadcnui` | Avatar component that expands to reveal the name on click with smooth animations. `[SRC:packages/registry/registry.json:L3394]` | `[SRC:packages/components/react-shadcn/src/components/native/native-avatar-expand-shadcnui.tsx:L55]` |
| `NativeAvatarWithName` | `@uitripled/native-avatar-with-name-shadcnui` | Avatar component that displays a name tooltip on hover with directional animations. `[SRC:packages/registry/registry.json:L3436]` | `[SRC:packages/components/react-shadcn/src/components/native/native-avatar-with-name-shadcnui.tsx:L59]` |
| `NativeButton` | `@uitripled/native-button-shadcnui` | Glassmorphism-inspired button component based on shadcn/ui with smooth animations and modern styling `[SRC:packages/registry/registry.json:L3518]` | `[SRC:packages/components/react-shadcn/src/components/native/native-button-shadcnui.tsx:L88]` |
| `NativeCounterUp` | none | no `registry.json` entry ships this file; the registry's same-named entries copy the react-carbon file; props `NativeCounterUpProps` | `[SRC:packages/components/react-shadcn/src/components/native/native-counter-up-shadcnui.tsx:L42]` |
| `NativeDelete` | `@uitripled/native-delete-shadcnui` | Delete button that expands to show a confirmation button with smooth animations. `[SRC:packages/registry/registry.json:L3600]` | `[SRC:packages/components/react-shadcn/src/components/native/native-delete-shadcnui.tsx:L73]` |
| `NativeDialog` | `@uitripled/native-dialog-shadcnui` | A glassmorphism-styled dialog component with backdrop blur and smooth animations, inspired by native OS modals. `[SRC:packages/registry/registry.json:L3642]` | `[SRC:packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:L86]` |
| `NativeDialogClose` | `@uitripled/native-dialog-shadcnui` | exported with `NativeDialog`, same registry entry | `[SRC:packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:L87]` |
| `NativeDialogContent` | `@uitripled/native-dialog-shadcnui` | exported with `NativeDialog`, same registry entry | `[SRC:packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:L88]` |
| `NativeDialogDescription` | `@uitripled/native-dialog-shadcnui` | exported with `NativeDialog`, same registry entry | `[SRC:packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:L89]` |
| `NativeDialogFooter` | `@uitripled/native-dialog-shadcnui` | exported with `NativeDialog`, same registry entry | `[SRC:packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:L90]` |
| `NativeDialogHeader` | `@uitripled/native-dialog-shadcnui` | exported with `NativeDialog`, same registry entry | `[SRC:packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:L91]` |
| `NativeDialogOverlay` | `@uitripled/native-dialog-shadcnui` | exported with `NativeDialog`, same registry entry | `[SRC:packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:L92]` |
| `NativeDialogPortal` | `@uitripled/native-dialog-shadcnui` | exported with `NativeDialog`, same registry entry | `[SRC:packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:L93]` |
| `NativeDialogTitle` | `@uitripled/native-dialog-shadcnui` | exported with `NativeDialog`, same registry entry | `[SRC:packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:L94]` |
| `NativeDialogTrigger` | `@uitripled/native-dialog-shadcnui` | exported with `NativeDialog`, same registry entry | `[SRC:packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:L95]` |
| `NativeFlipText` | none | no `registry.json` entry ships this file; the registry's same-named entries copy the react-carbon file; props `NativeFlipTextProps` | `[SRC:packages/components/react-shadcn/src/components/native/native-flip-text-shadcnui.tsx:L20]` |
| `NativeHoverCard` | `@uitripled/native-hover-card-shadcnui` | Avatar card that expands on hover to reveal profile information with smooth animations. `[SRC:packages/registry/registry.json:L3806]`; `native-hover-card.tsx`, which the `@uitripled/react-shadcn/components/native/native-hover-card` subpath builds, declares the same component and props `[AST:packages/components/react-shadcn/src/components/native/native-hover-card.tsx:L81]` | `[AST:packages/components/react-shadcn/src/components/native/native-hover-card-shadcnui.tsx:L81]` |
| `NativeImageCheckbox` | `@uitripled/native-image-checkbox-shadcnui` | Image checkbox component with grayscale filter and checkmark indicator. `[SRC:packages/registry/registry.json:L3868]` | `[SRC:packages/components/react-shadcn/src/components/native/native-image-checkbox-shadcnui.tsx:L63]` |
| `NativeLikesCounter` | `@uitripled/native-likes-counter-shadcnui` | An interactive likes counter with avatar stack, popup details, and smooth animations. `[SRC:packages/registry/registry.json:L3910]` | `[SRC:packages/components/react-shadcn/src/components/native/native-likes-counter-shadcnui.tsx:L56]` |
| `NativeLiquidButton` | `@uitripled/native-liquid-button-shadcnui` | Button with animated liquid fill effect, progress tracking, and multiple visual variants for engaging interactions. `[SRC:packages/registry/registry.json:L3952]` | `[SRC:packages/components/react-shadcn/src/components/native/native-liquid-button-shadcnui.tsx:L61]` |
| `NativeMagnetic` | `@uitripled/native-magnetic-shadcnui` | Magnetic wrapper that applies a cursor-following effect to any content. `[SRC:packages/registry/registry.json:L4034]` | `[SRC:packages/components/react-shadcn/src/components/native/native-magnetic-shadcnui.tsx:L61]` |
| `NativeMorphingButton` | `@uitripled/native-morphing-button-shadcnui` | Floating action button that morphs into a menu of actions. `[SRC:packages/registry/registry.json:L4096]` | `[SRC:packages/components/react-shadcn/src/components/native/native-morphing-button-shadcnui.tsx:L69]` |
| `NativeNestedList` | `@uitripled/native-nested-list-shadcnui` | A nested list component with smooth expand/collapse animations, perfect for file explorers or navigation menus. `[SRC:packages/registry/registry.json:L4138]` | `[SRC:packages/components/react-shadcn/src/components/native/native-nested-list-shadcnui.tsx:L230]` |
| `NativeNotch` | `@uitripled/native-notch-shadcnui` | Dynamic Island-inspired notch component with smooth spring animations, draggable physics, and expandable content area `[SRC:packages/registry/registry.json:L4180]` | `[SRC:packages/components/react-shadcn/src/components/native/native-notch-shadcnui.tsx:L106]` |
| `NativeNotificationBell` | `@uitripled/native-notification-bell-shadcnui` | Animated notification bell with badge and ringing effect. `[SRC:packages/registry/registry.json:L4242]` | `[SRC:packages/components/react-shadcn/src/components/native/native-notification-bell-shadcnui.tsx:L68]` |
| `NativeProfileNotch` | `@uitripled/native-profile-notch-shadcnui` | A dynamic expanding notch component for displaying user profiles with smooth spring animations. `[SRC:packages/registry/registry.json:L4284]` | `[SRC:packages/components/react-shadcn/src/components/native/native-profile-notch-shadcnui.tsx:L44]` |
| `NativeStartNow` | `@uitripled/native-start-now-shadcnui` | Animated button with sparkle effects, loading states, and smooth transitions for starting actions. `[SRC:packages/registry/registry.json:L4326]` | `[SRC:packages/components/react-shadcn/src/components/native/native-start-now-shadcnui.tsx:L78]` |
| `NativeTabs` | `@uitripled/native-tabs-shadcnui` | A sleek tabs component with a smooth sliding background indicator using Framer Motion layout animations. `[SRC:packages/registry/registry.json:L4388]` | `[SRC:packages/components/react-shadcn/src/components/native/native-tabs-shadcnui.tsx:L18]` |
| `NativeTooltip` | `@uitripled/native-tooltip-shadcnui` | A glassmorphism-styled tooltip with smooth spring animations using Framer Motion. `[SRC:packages/registry/registry.json:L4430]` | `[SRC:packages/components/react-shadcn/src/components/native/native-tooltip-shadcnui.tsx:L92]` |
| `NativeTooltipContent` | `@uitripled/native-tooltip-shadcnui` | exported with `NativeTooltip`, same registry entry | `[SRC:packages/components/react-shadcn/src/components/native/native-tooltip-shadcnui.tsx:L93]` |
| `NativeTooltipProvider` | `@uitripled/native-tooltip-shadcnui` | exported with `NativeTooltip`, same registry entry | `[SRC:packages/components/react-shadcn/src/components/native/native-tooltip-shadcnui.tsx:L94]` |
| `NativeTooltipTrigger` | `@uitripled/native-tooltip-shadcnui` | exported with `NativeTooltip`, same registry entry | `[SRC:packages/components/react-shadcn/src/components/native/native-tooltip-shadcnui.tsx:L95]` |
| `NativeTypewriter` | none | no `registry.json` entry ships this file; the registry's same-named entries copy the react-carbon file; props `NativeTypewriterProps` | `[SRC:packages/components/react-shadcn/src/components/native/native-typewriter-shadcnui.tsx:L43]` |
| `NativeUserCard` | `@uitripled/native-user-card-shadcnui` | Compact user profile card with avatar, name, handle, and action button with spring animations `[SRC:packages/registry/registry.json:L4534]` | `[SRC:packages/components/react-shadcn/src/components/native/native-user-card-shadcnui.tsx:L19]` |
| `VerifiedBadge` | `@uitripled/native-verified-badge-shadcnui` | Verified badge component with multiple variants, sizes, and styles including outline and shield designs. `[SRC:packages/registry/registry.json:L4576]` | `[SRC:packages/components/react-shadcn/src/components/native/native-verified-badge-shadcnui.tsx:L104]` |
| `VerifiedBadgeOutline` | `@uitripled/native-verified-badge-shadcnui` | exported with `VerifiedBadge`, same registry entry | `[SRC:packages/components/react-shadcn/src/components/native/native-verified-badge-shadcnui.tsx:L162]` |
| `VerifiedShieldBadge` | `@uitripled/native-verified-badge-shadcnui` | exported with `VerifiedBadge`, same registry entry | `[SRC:packages/components/react-shadcn/src/components/native/native-verified-badge-shadcnui.tsx:L247]` |
| `SocialLoginButton` | `@uitripled/social-login-button-shadcnui` | A set of animated social login buttons for major platforms (Github, Google, X, etc.) with various effects. `[SRC:packages/registry/registry.json:L5343]` | `[SRC:packages/components/react-shadcn/src/components/native/social-login-button-shadcnui.tsx:L127]` |
