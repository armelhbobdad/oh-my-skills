# Motion Components Reference (react-shadcn `src/components/`)

The motion-core components, the smaller interaction components grouped by category folder, and the Grid Generator panels of `@uitripled/react-shadcn`, with their install ids. Signatures are copied from the source at `a5ffb45`; the purpose is the entry's `description` in `packages/registry/registry.json`.

## Contents

- [Install and import](#install-and-import)
- [Motion-core components](#motion-core-components)
- [Interaction components by category](#interaction-components-by-category)
- [Grid Generator panels](#grid-generator-panels)

## Install and import

Install a component with `npx shadcn@latest add @uitripled/<install id>`: the CLI writes the entry's `files[].target`, `components/uitripled/<install id>.tsx`, which you import from `@/components/uitripled/<install id>` `[SRC:packages/registry/registry.json:L1]` `[SRC:apps/docs/public/llms-full.txt:L49]`. A consumer of the npm package imports a subpath instead (`@uitripled/react-shadcn/components/<path>`, `/ui/<file>`, `/src/<path>`), never the bare package: `src/index.ts` is `export {};` `[SRC:packages/components/react-shadcn/package.json:L8]` `[SRC:packages/components/react-shadcn/tsup.config.ts:L4]` `[SRC:packages/components/react-shadcn/src/index.ts:L2]`. The props types are in `references/types.md` → Component props types; a props type the signature names and that file does not list is not exported by the source.

```bash
npx shadcn@latest add @uitripled/ai-glow-input-shadcnui
```

```tsx
"use client";
import { AIGlowInput } from "@/components/uitripled/ai-glow-input-shadcnui";

export function Prompt() {
  return <AIGlowInput placeholder="Ask anything" />;
}
```

`placeholder` is an `AIGlowInputProps` field `[SRC:packages/components/react-shadcn/src/components/motion-core/ai-glow-input.tsx:L25]`.

## Motion-core components

`src/components/motion-core/`: configurable motion components; most take an optional props object whose defaults the signature shows.

```tsx
// components/motion-core/ai-glow-input.tsx
export function AIGlowInput({ placeholder = "Ask AI anything…", onValueChange, glowColor }: AIGlowInputProps)
// components/motion-core/ai-loading-skeleton.tsx
export function AILoadingSkeleton({ lines = 4 }: AILoadingSkeletonProps)
// components/motion-core/ai-response-typing.tsx
export function AIResponseTyping({ text = "Hello! I'm an AI assistant. I can help you with questions, provide information, and assist with various tasks. Feel free to ask me anything!", speed = 30, showCursor = true, onComplete, thinkingState = "typing" }: AIResponseTypingProps)
// components/motion-core/ai-unlock-animation.tsx
export function AIUnlockAnimation({ autoPlay = true }: AIUnlockAnimationProps)
// components/motion-core/animated-quote-block.tsx
export function AnimatedQuoteBlock({ quote = "The only way to do great work is to love what you do.", author = "Steve Jobs", typingSpeed = 50 }: AnimatedQuoteBlockProps)
// components/motion-core/auto-revealing-heading.tsx
export function AutoRevealingHeading({ text = "Auto Revealing Heading", splitBy = "word", delay = 0.1, className = "" }: AutoRevealingHeadingProps)
// components/motion-core/context-menu-bubble.tsx
export function ContextMenuBubble({ items = [{ label: "Edit", icon: <Edit className="h-4 w-4" />, onClick: () => {} }, { label: "Copy", icon: <Copy className="h-4 w-4" />, onClick: () => {} }, { label: "Share", icon: <Share2 className="h-4 w-4" />, onClick: () => {} }, { label: "Delete", icon: <Trash2 className="h-4 w-4" />, onClick: () => {}, danger: true }] }: ContextMenuBubbleProps)
// components/motion-core/drag-to-confirm-slider.tsx
export function DragToConfirmSlider({ onConfirm, label = "Drag to confirm", confirmText = "Confirmed!" }: DragToConfirmSliderProps)
// components/motion-core/dynamic-spotlight-cta.tsx
export function DynamicSpotlightCTA({ text = "Unlock Your Motion Power", intensity = 0.85, radius = 240, showBlur = true }: DynamicSpotlightCTAProps)
// components/motion-core/dynamic-tag-cloud.tsx
export function DynamicTagCloud({ tags = [{ id: "1", label: "React" }, { id: "2", label: "TypeScript" }, { id: "3", label: "Framer Motion" }, { id: "4", label: "TailwindCSS" }, { id: "5", label: "Next.js" }, { id: "6", label: "Design" }] }: DynamicTagCloudProps)
// components/motion-core/expanding-search-dock.tsx
export function ExpandingSearchDock({ onSearch, placeholder = "Search..." }: ExpandingSearchDockProps)
// components/motion-core/floating-info-panel.tsx
export function FloatingInfoPanel({ title = "Info Panel", description = "This is a floating information panel that gently drifts", icon }: FloatingInfoPanelProps)
// components/motion-core/fluid-modal-transition.tsx
export function FluidModalTransition({ trigger, title = "Modal Title", children }: FluidModalTransitionProps)
// components/motion-core/holographic-wall.tsx
export function HolographicWall({ intensity = 0.8, radius = 200 }: HolographicWallProps)
// components/motion-core/interactive-timeline.tsx
export function InteractiveTimeline({ items = [{ id: "1", title: "Started", description: "Project began", date: "2024" }, { id: "2", title: "Development", description: "Active development phase", date: "2024" }, { id: "3", title: "Launch", description: "Project launched", date: "2024" }] }: InteractiveTimelineProps)
// components/motion-core/magnetic-avatar-group.tsx
export function MagneticAvatarGroup({ avatars = [{ id: "1", name: "John Doe", initials: "JD", color: "bg-primary" }, { id: "2", name: "Jane Smith", initials: "JS", color: "bg-primary/80" }, { id: "3", name: "Bob Wilson", initials: "BW", color: "bg-primary/60" }, { id: "4", name: "Alice Brown", initials: "AB", color: "bg-primary/40" }], maxVisible = 4 }: MagneticAvatarGroupProps)
// components/motion-core/mood-gradient-button.tsx
export function MoodGradientButton({ children = "Hover Me", onClick, className = "" }: MoodGradientButtonProps)
// components/motion-core/reactive-background-grid.tsx
export function ReactiveBackgroundGrid({ dots = true, density = 20 }: ReactiveBackgroundGridProps)
// components/motion-core/scroll-progress-tracker.tsx
export function ScrollProgressTracker({ sections = [], height = 4 }: ScrollProgressTrackerProps)
// components/motion-core/smart-hover-card.tsx
export function SmartHoverCard({ title = "Smart Hover Card", description = "Hover from different directions to see content reveal", children }: SmartHoverCardProps)
// components/motion-core/spotlight-section.tsx
export function SpotlightSection({ children = (<div className="text-center"> <h3 className="text-xl font-semibold">Spotlight Section</h3> <p className="mt-2 text-sm text-muted-foreground"> Move your mouse around to see the spotlight effect </p> </div>), intensity = 0.6, size = 300 }: SpotlightSectionProps)
// components/motion-core/stacked-card-carousel.tsx
export function StackedCardCarousel({ cards = [{ id: "1", title: "Card One", description: "Description for card one", color: "bg-primary" }, { id: "2", title: "Card Two", description: "Description for card two", color: "bg-primary/80" }, { id: "3", title: "Card Three", description: "Description for card three", color: "bg-primary/60" }] }: StackedCardCarouselProps)
// components/motion-core/synced-lyric-captions.tsx
export function SyncedLyricCaptions({ script = DEFAULT_SCRIPT, audioSrc, title = "Enhanced Synced Captions" }: SyncedLyricCaptionsProps)
```

| Export | Install id | Purpose | Source |
|--------|------------|---------|--------|
| `AIGlowInput` | `@uitripled/ai-glow-input-shadcnui` | Input field with dynamic glow that pulses based on typing speed - smart motion feedback `[SRC:packages/registry/registry.json:L90]` | `[SRC:packages/components/react-shadcn/src/components/motion-core/ai-glow-input.tsx:L25]` |
| `AILoadingSkeleton` | `@uitripled/ai-loading-skeleton-shadcnui` | Loading state with diagonal shimmer gradient and opacity wave `[SRC:packages/registry/registry.json:L112]` | `[SRC:packages/components/react-shadcn/src/components/motion-core/ai-loading-skeleton.tsx:L41]` |
| `AIResponseTyping` | `@uitripled/ai-response-typing-shadcnui` | Character-by-character typing animation with natural pauses and thinking states `[SRC:packages/registry/registry.json:L134]` | `[SRC:packages/components/react-shadcn/src/components/motion-core/ai-response-typing.tsx:L14]` |
| `AIUnlockAnimation` | `@uitripled/ai-unlock-animation-shadcnui` | Premium unlock animation with particles, ripples, and loading states `[SRC:packages/registry/registry.json:L156]` | `[SRC:packages/components/react-shadcn/src/components/motion-core/ai-unlock-animation.tsx:L10]` |
| `AnimatedQuoteBlock` | `@uitripled/animated-quote-block-shadcnui` | Quote that types itself in, pauses, then subtly breathes `[SRC:packages/registry/registry.json:L395]` | `[SRC:packages/components/react-shadcn/src/components/motion-core/animated-quote-block.tsx:L12]` |
| `AutoRevealingHeading` | `@uitripled/auto-revealing-heading-shadcnui` | Heading that reveals each letter/word with staggered motion on scroll `[SRC:packages/registry/registry.json:L527]` | `[SRC:packages/components/react-shadcn/src/components/motion-core/auto-revealing-heading.tsx:L13]` |
| `ContextMenuBubble` | `@uitripled/context-menu-bubble-shadcnui` | Right-click reveals circular expanding radial menu with icons `[SRC:packages/registry/registry.json:L1021]` | `[SRC:packages/components/react-shadcn/src/components/motion-core/context-menu-bubble.tsx:L18]` |
| `DragToConfirmSlider` | `@uitripled/drag-to-confirm-slider-shadcnui` | Slider that activates action only when fully dragged to end `[SRC:packages/registry/registry.json:L1391]` | `[SRC:packages/components/react-shadcn/src/components/motion-core/drag-to-confirm-slider.tsx:L13]` |
| `DynamicSpotlightCTA` | `@uitripled/dynamic-spotlight-cta-shadcnui` | Floating spotlight follows cursor to reveal gradient CTA text with premium effects `[SRC:packages/registry/registry.json:L1435]` | `[SRC:packages/components/react-shadcn/src/components/motion-core/dynamic-spotlight-cta.tsx:L22]` |
| `DynamicTagCloud` | `@uitripled/dynamic-tag-cloud-shadcnui` | Floating cluster of tags that drift and rearrange when hovered `[SRC:packages/registry/registry.json:L1455]` | `[SRC:packages/components/react-shadcn/src/components/motion-core/dynamic-tag-cloud.tsx:L15]` |
| `ExpandingSearchDock` | `@uitripled/expanding-search-dock-shadcnui` | Minimal search icon that expands into full input with blur `[SRC:packages/registry/registry.json:L1537]` | `[SRC:packages/components/react-shadcn/src/components/motion-core/expanding-search-dock.tsx:L12]` |
| `FloatingInfoPanel` | `@uitripled/floating-info-panel-shadcnui` | Info tooltip that drifts up/down while fading in/out intermittently `[SRC:packages/registry/registry.json:L1840]` | `[SRC:packages/components/react-shadcn/src/components/motion-core/floating-info-panel.tsx:L12]` |
| `FluidModalTransition` | `@uitripled/fluid-modal-transition-shadcnui` | Modal that expands smoothly from clicked trigger element using layoutId `[SRC:packages/registry/registry.json:L1882]` | `[SRC:packages/components/react-shadcn/src/components/motion-core/fluid-modal-transition.tsx:L13]` |
| `HolographicWall` | `@uitripled/holographic-wall-shadcnui` | Black wall with Pharaonic hieroglyphs and golden cursor light reflection `[SRC:packages/registry/registry.json:L2988]` | `[SRC:packages/components/react-shadcn/src/components/motion-core/holographic-wall.tsx:L35]` |
| `InteractiveTimeline` | `@uitripled/interactive-timeline-shadcnui` | Vertical timeline where elements animate and connect with lines on scroll `[SRC:packages/registry/registry.json:L3114]` | `[SRC:packages/components/react-shadcn/src/components/motion-core/interactive-timeline.tsx:L64]` |
| `MagneticAvatarGroup` | `@uitripled/magnetic-avatar-group-shadcnui` | Stacked avatars that spread apart on hover showing tooltips `[SRC:packages/registry/registry.json:L3200]` | `[SRC:packages/components/react-shadcn/src/components/motion-core/magnetic-avatar-group.tsx:L18]` |
| `MoodGradientButton` | `@uitripled/mood-gradient-button-shadcnui` | Button with background gradient that shifts based on hover angle `[SRC:packages/registry/registry.json:L3286]` | `[SRC:packages/components/react-shadcn/src/components/motion-core/mood-gradient-button.tsx:L12]` |
| `ReactiveBackgroundGrid` | `@uitripled/reactive-background-grid-shadcnui` | Background pattern that reacts to mouse movement and click ripples `[SRC:packages/registry/registry.json:L5048]` | `[SRC:packages/components/react-shadcn/src/components/motion-core/reactive-background-grid.tsx:L11]` |
| `ScrollProgressTracker` | `@uitripled/scroll-progress-tracker-shadcnui` | Fixed progress bar that follows scroll and glows on section changes `[SRC:packages/registry/registry.json:L5150]` | `[SRC:packages/components/react-shadcn/src/components/motion-core/scroll-progress-tracker.tsx:L11]` |
| `SmartHoverCard` | `@uitripled/smart-hover-card-shadcnui` | Card that detects cursor direction and reveals content from that side `[SRC:packages/registry/registry.json:L5298]` | `[SRC:packages/components/react-shadcn/src/components/motion-core/smart-hover-card.tsx:L14]` |
| `SpotlightSection` | `@uitripled/spotlight-section-shadcnui` | Container where mouse creates soft radial spotlight following cursor `[SRC:packages/registry/registry.json:L5363]` | `[SRC:packages/components/react-shadcn/src/components/motion-core/spotlight-section.tsx:L12]` |
| `StackedCardCarousel` | `@uitripled/stacked-card-carousel-shadcnui` | Three stacked cards that shift and tilt dynamically on hover `[SRC:packages/registry/registry.json:L5383]` | `[SRC:packages/components/react-shadcn/src/components/motion-core/stacked-card-carousel.tsx:L17]` |
| `SyncedLyricCaptions` | `@uitripled/synced-lyric-captions-shadcnui` | Bottom-to-top timed captions with play/pause controls and optional audio sync for songs or voiceovers. `[SRC:packages/registry/registry.json:L5598]` | `[SRC:packages/components/react-shadcn/src/components/motion-core/synced-lyric-captions.tsx:L66]` |

## Interaction components by category

`src/components/<category>/` (avatars, data, decorative, disclosure, forms, inputs, micro, modals, navigation, page, search, tooltips, web-performance) and `src/components/liquid-cursor.tsx`.

```tsx
// components/avatars/avatar-group.tsx
export function AvatarGroup()
// components/data/charts/cash-flow-chart.tsx
export function CashFlowChart()
// components/data/progress/animated-progress.tsx
export function AnimatedProgress()
// components/decorative/background/floating-gradient.tsx
export function FloatingGradient()
// components/decorative/backgrounds/gradient-animation.tsx
export function GradientAnimation()
// components/disclosure/animated-accordion.tsx
export function AnimatedAccordion()
// components/forms/animated-checkbox.tsx
export function AnimatedCheckbox()
// components/forms/animated-radio.tsx
export function AnimatedRadio()
// components/forms/animated-select.tsx
export function AnimatedSelect()
// components/forms/simple-calendar.tsx
export function SimpleCalendar()
// components/forms/wizard-form.tsx
export function WizardForm()
// components/inputs/password-input.tsx
export function PasswordInput()
// components/liquid-cursor.tsx
export const LiquidCursor = () => …
// components/micro/buttons/ripple-click.tsx
export function RippleClickButton()
// components/micro/buttons/scale-hover.tsx
export function ScaleHoverButton()
// components/micro/buttons/shimmer-button.tsx
export function ShimmerButton()
// components/micro/icons/heart-favorite.tsx
export function HeartFavorite()
// components/micro/links/preview-details-card.tsx
export function PreviewDetailsCard()
// components/micro/toggles/elastic-switch.tsx
export function ElasticSwitch()
// components/modals/animated-dialog.tsx
export function AnimatedDialog()
// components/modals/bottom-modal.tsx
export function BottomModal()
// components/navigation/animated-navbar.tsx
export function AnimatedNavbar()
// components/navigation/animated-pagination.tsx
export function AnimatedPagination()
// components/navigation/animated-profile-menu.tsx
export function AnimatedProfileMenu()
// components/navigation/animated-sidebar.tsx
export function AnimatedSidebar()
// components/navigation/context-menu.tsx
export function ContextMenu()
// components/page/about/about-us-page.tsx
export function AboutUsPage()
// components/page/hero/staggered-text.tsx
export function StaggeredHero()
// components/page/notifications/toast-notification.tsx
export function ToastNotification()
// components/search/command-palette.tsx
export function CommandPalette()
// components/search/mac-searchbar.tsx
export function MacSearchbar()
// components/tooltips/animated-tooltip.tsx
export function AnimatedTooltip()
// components/web-performance/web-performance-page.tsx
export function WebPerformancePage()
```

| Export | Install id | Purpose | Source |
|--------|------------|---------|--------|
| `AvatarGroup` | `@uitripled/avatar-group-shadcnui` | Stacked avatar group with hover reveal and tooltips `[SRC:packages/registry/registry.json:L547]` | `[SRC:packages/components/react-shadcn/src/components/avatars/avatar-group.tsx:L27]` |
| `CashFlowChart` | `@uitripled/cash-flow-chart` (writes `components/uitripled/cash-flow-chart-carbon.tsx`) | Interactive cash flow bar chart with keyboard focus, tooltips, and screen reader support `[SRC:packages/registry/registry.json:L763]` | `[SRC:packages/components/react-shadcn/src/components/data/charts/cash-flow-chart.tsx:L135]` |
| `AnimatedProgress` | `@uitripled/animated-progress-shadcnui` | Progress bar with smooth animation `[SRC:packages/registry/registry.json:L375]` | `[SRC:packages/components/react-shadcn/src/components/data/progress/animated-progress.tsx:L7]` |
| `FloatingGradient` | `@uitripled/floating-gradient-shadcnui` | Animated floating gradient background effect `[SRC:packages/registry/registry.json:L1820]` | `[SRC:packages/components/react-shadcn/src/components/decorative/background/floating-gradient.tsx:L5]` |
| `GradientAnimation` | `@uitripled/gradient-animation-shadcnui` | Smoothly transitioning gradient background `[SRC:packages/registry/registry.json:L2861]` | `[SRC:packages/components/react-shadcn/src/components/decorative/backgrounds/gradient-animation.tsx:L5]` |
| `AnimatedAccordion` | `@uitripled/animated-accordion-shadcnui` | Accordion with smooth expand/collapse and rotate arrow `[SRC:packages/registry/registry.json:L176]` | `[SRC:packages/components/react-shadcn/src/components/disclosure/animated-accordion.tsx:L25]` |
| `AnimatedCheckbox` | `@uitripled/animated-checkbox-shadcnui` | Checkbox with checkmark animation `[SRC:packages/registry/registry.json:L240]` | `[SRC:packages/components/react-shadcn/src/components/forms/animated-checkbox.tsx:L7]` |
| `AnimatedRadio` | `@uitripled/animated-radio-shadcnui` | Radio button group with selection ripple `[SRC:packages/registry/registry.json:L415]` | `[SRC:packages/components/react-shadcn/src/components/forms/animated-radio.tsx:L8]` |
| `AnimatedSelect` | `@uitripled/animated-select-shadcnui` | Select dropdown with smooth open/close animation `[SRC:packages/registry/registry.json:L437]` | `[SRC:packages/components/react-shadcn/src/components/forms/animated-select.tsx:L9]` |
| `SimpleCalendar` | `@uitripled/simple-calendar-shadcnui` | Calendar picker with date selection animation `[SRC:packages/registry/registry.json:L5276]` | `[SRC:packages/components/react-shadcn/src/components/forms/simple-calendar.tsx:L10]` |
| `WizardForm` | `@uitripled/wizard-form-shadcnui` | Multi-step wizard form with animated transitions, validation, and progress tracking `[SRC:packages/registry/registry.json:L5922]` | `[SRC:packages/components/react-shadcn/src/components/forms/wizard-form.tsx:L165]` |
| `PasswordInput` | `@uitripled/password-input-shadcnui` | Password input with toggle visibility and strength indicator `[SRC:packages/registry/registry.json:L4816]` | `[SRC:packages/components/react-shadcn/src/components/inputs/password-input.tsx:L7]` |
| `LiquidCursor` | `@uitripled/liquid-cursor-shadcnui` | A liquid-like cursor effect that mixes colors on movement `[SRC:packages/registry/registry.json:L3158]` | `[SRC:packages/components/react-shadcn/src/components/liquid-cursor.tsx:L25]` |
| `RippleClickButton` | `@uitripled/ripple-click-button-shadcnui` | Material design inspired ripple effect on click `[SRC:packages/registry/registry.json:L5110]` | `[SRC:packages/components/react-shadcn/src/components/micro/buttons/ripple-click.tsx:L12]` |
| `ScaleHoverButton` | `@uitripled/scale-hover-button-shadcnui` | A button that scales up smoothly on hover `[SRC:packages/registry/registry.json:L5130]` | `[SRC:packages/components/react-shadcn/src/components/micro/buttons/scale-hover.tsx:L5]` |
| `ShimmerButton` | `@uitripled/shimmer-button-shadcnui` | Button with continuous shimmer effect `[SRC:packages/registry/registry.json:L5256]` | `[SRC:packages/components/react-shadcn/src/components/micro/buttons/shimmer-button.tsx:L6]` |
| `HeartFavorite` | `@uitripled/heart-favorite-shadcnui` | Animated heart icon for like/favorite actions `[SRC:packages/registry/registry.json:L2881]` | `[SRC:packages/components/react-shadcn/src/components/micro/icons/heart-favorite.tsx:L7]` |
| `PreviewDetailsCard` | `@uitripled/preview-details-card-shadcnui` | Link card that reveals a smooth detail preview box on hover `[SRC:packages/registry/registry.json:L4838]` | `[SRC:packages/components/react-shadcn/src/components/micro/links/preview-details-card.tsx:L19]` |
| `ElasticSwitch` | `@uitripled/elastic-switch-shadcnui` | Toggle switch with elastic spring animation `[SRC:packages/registry/registry.json:L1517]` | `[SRC:packages/components/react-shadcn/src/components/micro/toggles/elastic-switch.tsx:L6]` |
| `AnimatedDialog` | `@uitripled/animated-dialog-shadcnui` | Modal dialog with backdrop fade and spring animation `[SRC:packages/registry/registry.json:L262]` | `[SRC:packages/components/react-shadcn/src/components/modals/animated-dialog.tsx:L8]` |
| `BottomModal` | `@uitripled/bottom-modal` | Cute bottom-centered modal with smooth slide-up animation and glassmorphism design `[SRC:packages/registry/registry.json:L679]` | `[SRC:packages/components/react-shadcn/src/components/modals/bottom-modal.tsx:L8]` |
| `AnimatedNavbar` | `@uitripled/animated-navbar-shadcnui` | Navigation bar with animated underline indicator `[SRC:packages/registry/registry.json:L306]` | `[SRC:packages/components/react-shadcn/src/components/navigation/animated-navbar.tsx:L8]` |
| `AnimatedPagination` | `@uitripled/animated-pagination-shadcnui` | Pagination with smooth page transition indicator `[SRC:packages/registry/registry.json:L329]` | `[SRC:packages/components/react-shadcn/src/components/navigation/animated-pagination.tsx:L7]` |
| `AnimatedProfileMenu` | `@uitripled/animated-profile-menu-shadcnui` | Floating profile avatar that reveals quick action cards with smooth motion `[SRC:packages/registry/registry.json:L352]` | `[SRC:packages/components/react-shadcn/src/components/navigation/animated-profile-menu.tsx:L74]` |
| `AnimatedSidebar` | `@uitripled/animated-sidebar-shadcnui` | Sidebar with slide-in animation and overlay `[SRC:packages/registry/registry.json:L459]` | `[SRC:packages/components/react-shadcn/src/components/navigation/animated-sidebar.tsx:L14]` |
| `ContextMenu` | `@uitripled/context-menu-shadcnui` | Right-click context menu with nested items animation `[SRC:packages/registry/registry.json:L1043]` | `[SRC:packages/components/react-shadcn/src/components/navigation/context-menu.tsx:L14]` |
| `AboutUsPage` | `@uitripled/about-us-page-shadcnui` | Glassmorphism about page showcasing mission, values, and leadership with motion accents. `[SRC:packages/registry/registry.json:L4]` | `[SRC:packages/components/react-shadcn/src/components/page/about/about-us-page.tsx:L131]` |
| `StaggeredHero` | `@uitripled/staggered-hero-shadcnui` | Hero section with staggered text reveal `[SRC:packages/registry/registry.json:L5428]` | `[SRC:packages/components/react-shadcn/src/components/page/hero/staggered-text.tsx:L30]` |
| `ToastNotification` | `@uitripled/toast-notification-shadcnui` | Animated toast notification popup `[SRC:packages/registry/registry.json:L5836]` | `[SRC:packages/components/react-shadcn/src/components/page/notifications/toast-notification.tsx:L9]` |
| `CommandPalette` | `@uitripled/command-palette-shadcnui` | Command palette with search and keyboard navigation `[SRC:packages/registry/registry.json:L847]` | `[SRC:packages/components/react-shadcn/src/components/search/command-palette.tsx:L49]` |
| `MacSearchbar` | `@uitripled/mac-searchbar-shadcnui` | Mac-style searchbar with animated dropdown, glassmorphism effects, and smooth transitions `[SRC:packages/registry/registry.json:L3178]` | `[SRC:packages/components/react-shadcn/src/components/search/mac-searchbar.tsx:L16]` |
| `AnimatedTooltip` | `@uitripled/animated-tooltip-shadcnui` | Tooltip with delay and slide animation `[SRC:packages/registry/registry.json:L504]` | `[SRC:packages/components/react-shadcn/src/components/tooltips/animated-tooltip.tsx:L7]` |
| `WebPerformancePage` | `@uitripled/web-performance-page-shadcnui` | Real-time analysis of web vitals and performance metrics `[SRC:packages/registry/registry.json:L5900]` | `[SRC:packages/components/react-shadcn/src/components/web-performance/web-performance-page.tsx:L394]` |

## Grid Generator panels

`src/components/grid/`: the panels of the docs site's Grid Generator. No `registry.json` entry ships these files: import them from `@uitripled/react-shadcn/components/grid/<file>`. They pair with the grid helpers and `bentoPresets` in `references/utils.md`.

```tsx
// components/grid/code-output.tsx
export function CodeOutput({ code, copied, onCopyCode, options }: CodeOutputProps)
// components/grid/grid-cell.tsx
export function GridCell({ cell, cols, rows, isInSelection, onPointerDown, onPointerEnter }: GridCellProps)
// components/grid/grid-preview.tsx
export function GridPreview({ cells, cols, rows, gap, selectedCells, onPointerDown, onPointerEnter, onPointerUp, onPointerLeave, onAddCell, onResetGrid, onUndo, onRedo, canUndo, canRedo }: GridPreviewProps)
// components/grid/presets-panel.tsx
export function PresetsPanel({ onApplyPreset }: PresetsPanelProps)
// components/grid/settings-panel.tsx
export function SettingsPanel({ cols, maxCols = 12, maxGap = 12, gap, onColsChange, onGapChange }: SettingsPanelProps)
```

The `GridCell` line lists the props of its props type, `GridCellProps`, which `grid-cell.tsx` declares but does not export: `cell`, `cols`, `rows`, `isInSelection`, `onPointerDown` and `onPointerEnter`, all six required. The function's own parameter destructures five of them and never reads `rows`, but a caller must still pass it, as `GridPreview` does. This component is a different export from the `GridCell` interface of `references/utils.md` → Grid helpers, which `grid-cell.tsx` imports as `GridCellType` for its `cell` prop. `[SRC:packages/components/react-shadcn/src/components/grid/grid-cell.tsx:L5]` `[AST:packages/components/react-shadcn/src/components/grid/grid-cell.tsx:L14]` `[SRC:packages/components/react-shadcn/src/components/grid/grid-cell.tsx:L3]`

| Export | Install id | Purpose | Source |
|--------|------------|---------|--------|
| `CodeOutput` | none | no `registry.json` entry ships this file; props `CodeOutputProps` | `[SRC:packages/components/react-shadcn/src/components/grid/code-output.tsx:L14]` |
| `GridCell` | none | no `registry.json` entry ships this file; one cell of the grid `GridPreview` renders `[SRC:packages/components/react-shadcn/src/components/grid/grid-preview.tsx:L132]` | `[AST:packages/components/react-shadcn/src/components/grid/grid-cell.tsx:L14]` |
| `GridPreview` | none | no `registry.json` entry ships this file; props `GridPreviewProps` | `[SRC:packages/components/react-shadcn/src/components/grid/grid-preview.tsx:L28]` |
| `PresetsPanel` | none | no `registry.json` entry ships this file; props `PresetsPanelProps` | `[SRC:packages/components/react-shadcn/src/components/grid/presets-panel.tsx:L12]` |
| `SettingsPanel` | none | no `registry.json` entry ships this file; props `SettingsPanelProps` | `[SRC:packages/components/react-shadcn/src/components/grid/settings-panel.tsx:L15]` |
