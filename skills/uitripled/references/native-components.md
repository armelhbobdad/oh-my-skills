# Native Components Reference

## Contents

- [NativeNotch](#nativenotch)
- [NativeMagnetic](#nativemagnetic)
- [NativeHoverCard](#nativehovercard)
- [NativeStartNow](#nativestartnow)
- [NativeProfileNotch](#nativeprofilenotch)
- [NativeMorphingButton](#nativemorphingbutton)
- [NativeNotificationBell](#nativenotificationbell)
- [NativeDelete](#nativedelete)
- [NativeCounterUp](#nativecounterup)
- [NativeFollowCursor](#nativefollowcursor)
- [NativeAvatarWithName](#nativeavatarwithname)
- [NativeAvatarExpand](#nativeavatarexpand)
- [NativeImageCheckbox](#nativeimagecheckbox)
- [NativeLikesCounter](#nativelikescounter)
- [NativeNestedList](#nativenestedlist)
- [SocialLoginButton](#socialloginbutton)

---

## NativeNotch

Dynamic Island-style expandable notch with draggable positioning and controlled/uncontrolled modes.

**Install:** `npx uitripled add native-notch-shadcnui`
**Available in:** shadcn/ui, Base UI

### NativeNotchProps

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| children | `React.ReactNode` | — | Content to display when the notch is open |
| collapsedIcon | `React.ReactNode` | — | Custom content/icon to display when the notch is closed |
| size | `NotchSize` | `"md"` | Size variant: `"sm" \| "md" \| "lg"` |
| position | `NotchPosition` | — | Initial position configuration |
| draggable | `boolean` | `true` | Whether the notch is draggable |
| defaultExpanded | `boolean` | `false` | Default expanded state |
| expanded | `boolean` | — | Controlled expanded state |
| onExpandedChange | `(expanded: boolean) => void` | — | Callback when expanded state changes |
| onClick | `(e: React.MouseEvent) => void` | — | Callback when notch is clicked |
| className | `string` | — | Additional CSS classes |

`[AST:packages/components/react-shadcn/src/components/native/native-notch-shadcnui.tsx:L39]`

---

## NativeMagnetic

Magnetic cursor-attraction effect on child elements with spring-based animation.

**Install:** `npx uitripled add native-magnetic-shadcnui`
**Available in:** shadcn/ui, Base UI, Carbon

### NativeMagneticProps

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| children | `React.ReactNode` | — | Content to apply the magnetic effect to |
| strength | `number` | `0.3` | Strength of the magnetic pull (0-1 range recommended) |
| stiffness | `number` | `300` | Spring stiffness for the animation |
| damping | `number` | `30` | Spring damping for the animation |
| scaleOnHover | `boolean` | `true` | Whether to scale up on hover |
| as | `"div" \| "button" \| "a"` | `"div"` | Wrapper element type |
| href | `string` | — | Link href (only applies when as="a") |
| onClick | `() => void` | — | Click handler |
| className | `string` | — | Additional CSS classes |

`[AST:packages/components/react-shadcn/src/components/native/native-magnetic-shadcnui.tsx:L14]`

---

## NativeHoverCard

Profile hover card that expands from an image to show user details with configurable variant styles.

**Install:** `npx uitripled add native-hover-card-shadcnui`
**Available in:** shadcn/ui, Base UI

### NativeHoverCardProps

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| imageSrc | `string` | — | Image source URL |
| imageAlt | `string` | — | Alt text for the image |
| name | `string` | — | Display name |
| username | `string` | — | Username or handle |
| description | `string` | — | Description or bio text |
| buttonText | `string` | `"View Profile"` | Button text |
| onButtonClick | `() => void` | — | Button click handler |
| buttonContent | `ReactNode` | — | Custom button component |
| size | `"sm" \| "md" \| "lg" \| "xl"` | `"md"` | Size of the image when collapsed |
| className | `string` | — | Additional class names for the container |
| variant | `"default" \| "glass" \| "bordered"` | — | Card variant style |

`[AST:packages/components/react-shadcn/src/components/native/native-hover-card-shadcnui.tsx:L9]`

---

## NativeStartNow

Animated CTA button with loading, success states and rocket animation.

**Install:** `npx uitripled add native-start-now-shadcnui`
**Available in:** shadcn/ui, Base UI

### NativeStartNowProps

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| onStart | `() => void \| Promise<void>` | — | Callback when start button is clicked |
| label | `string` | `"Start Now"` | Text to show on the button |
| loadingLabel | `string` | `"Starting..."` | Loading text during async action |
| successLabel | `string` | `"Let's Go!"` | Success text after completion |
| size | `"sm" \| "md" \| "lg"` | `"md"` | Size variant |
| showRocket | `boolean` | `true` | Show sparkle animation on hover |
| icon | `ReactNode` | — | Icon to use for rocket and success state |
| className | `string` | — | Additional class names for the container |
| disabled | `boolean` | — | Disable the button |
| variant | `"gradient" \| "solid" \| "outline"` | `"gradient"` | Variant style |

`[AST:packages/components/react-shadcn/src/components/native/native-start-now-shadcnui.tsx:L9]`

---

## NativeProfileNotch

Animated user profile notch that expands to show user details with two expansion behaviors.

**Install:** `npx uitripled add native-profile-notch-shadcnui`
**Available in:** shadcn/ui, Base UI

### NativeProfileNotchProps

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| imageSrc | `string` | — | URL of the user image |
| name | `string` | — | Name of the user |
| username | `string` | — | Handle or role of the user |
| children | `React.ReactNode` | — | Custom content to show in expanded state |
| size | `"sm" \| "md" \| "lg"` | `"md"` | Size of the notch |
| className | `string` | — | Class name for the container |
| variant | `"default" \| "overlay"` | `"default"` | `"default"` expands and pushes content; `"overlay"` expands over content (absolute positioning) |

`[AST:packages/components/react-shadcn/src/components/native/native-profile-notch-shadcnui.tsx:L9]`

---

## NativeMorphingButton

Floating action button that morphs into an expanded menu with configurable actions.

**Install:** `npx uitripled add native-morphing-button-shadcnui`
**Available in:** shadcn/ui, Base UI, Carbon

### NativeMorphingButtonProps

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| actions | `MorphingButtonAction[]` | — | Array of actions to display in the expanded menu |
| position | `"bottom-right" \| "bottom-left" \| "top-right" \| "top-left"` | `"bottom-right"` | Position of the FAB |
| fixed | `boolean` | `false` | Whether to use fixed positioning |
| icon | `React.ReactNode` | — | Custom icon when collapsed |
| closeIcon | `React.ReactNode` | — | Custom close icon when expanded |
| className | `string` | — | Additional CSS classes |

`[AST:packages/components/react-shadcn/src/components/native/native-morphing-button-shadcnui.tsx:L29]`

---

## NativeNotificationBell

Animated notification bell with badge count and ring callback.

**Install:** `npx uitripled add native-notification-bell-shadcnui`
**Available in:** shadcn/ui, Base UI, Carbon

### NativeNotificationBellProps

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| count | `number` | `0` | Number of notifications to display |
| showBadge | `boolean` | — | Whether to show the notification badge (auto-true if count > 0) |
| onClick | `() => void` | — | Callback when the bell is clicked |
| onRing | `() => void` | — | Callback when the bell rings (on mount if has notifications) |
| icon | `React.ReactNode` | — | Custom icon to replace the bell |
| size | `"sm" \| "md" \| "lg"` | `"md"` | Size variant |
| className | `string` | — | Additional CSS classes |

`[AST:packages/components/react-shadcn/src/components/native/native-notification-bell-shadcnui.tsx:L8]`

---

## NativeDelete

Two-step delete confirmation button with animated state transitions.

**Install:** `npx uitripled add native-delete-shadcnui`
**Available in:** shadcn/ui, Base UI

### NativeDeleteProps

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| onConfirm | `() => void` | — | Callback when delete button is first clicked (shows confirmation) |
| onDelete | `() => void` | — | Callback when delete is confirmed |
| buttonText | `string` | `"Delete"` | Text to show on the delete button |
| confirmText | `string` | `"Confirm"` | Text to show on the confirm button |
| size | `"sm" \| "md" \| "lg"` | `"md"` | Size variant |
| showIcon | `boolean` | `true` | Show icon in button |
| className | `string` | — | Additional class names for the container |
| disabled | `boolean` | — | Disable the button |

`[AST:packages/components/react-shadcn/src/components/native/native-delete-shadcnui.tsx:L9]`

---

## NativeCounterUp

Animated number counter that counts from 0 to a target value.

**Install:** `npx uitripled add native-counter-up-shadcnui`
**Available in:** shadcn/ui, Carbon

### NativeCounterUpProps

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| value | `number` | — | The target number to count up to |
| duration | `number` | `2` | Duration of the animation in seconds |
| prefix | `string` | — | Text to display before the number (e.g., "$") |
| suffix | `string` | — | Text to display after the number (e.g., "+", "%") |
| decimals | `number` | `0` | Number of decimal places to show |
| label | `string` | — | Accessible label describing what the counter represents |
| autoStart | `boolean` | `true` | Whether to start the animation on mount |
| className | `string` | — | Additional CSS classes |

`[AST:packages/components/react-shadcn/src/components/native/native-counter-up-shadcnui.tsx:L7]`

---

## NativeFollowCursor

Cursor-following label/content with spring-based animation. Includes an area component for scoped tracking.

**Install:** `npx uitripled add native-follow-cursor-carbon`
**Available in:** Carbon

### NativeFollowCursorProps

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| name | `string` | — | Text to display (deprecated — use children) |
| children | `React.ReactNode` | — | Custom content to display |
| size | `"sm" \| "md" \| "lg"` | `"md"` | Size variant of the label |
| variant | `"default" \| "glass" \| "solid" \| "minimal"` | `"default"` | Visual variant |
| offset | `{ x: number; y: number }` | `{ x: 12, y: 12 }` | Offset from cursor in pixels |
| stiffness | `number` | `150` | Spring stiffness for smooth following |
| damping | `number` | `20` | Spring damping for smooth following |
| className | `string` | — | Additional class names for the label |
| showDot | `boolean` | `true` | Show decorative dot indicator |

### NativeFollowCursorAreaProps

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| children | `React.ReactNode` | — | Content area to track cursor within |
| cursorContent | `React.ReactNode` | — | Content that follows the cursor |
| size | `"sm" \| "md" \| "lg"` | `"md"` | Size variant of the cursor label |
| variant | `"default" \| "glass" \| "solid" \| "minimal"` | `"default"` | Visual variant |
| offset | `{ x: number; y: number }` | `{ x: 12, y: 12 }` | Offset from cursor in pixels |
| stiffness | `number` | `150` | Spring stiffness |
| damping | `number` | `20` | Spring damping |
| className | `string` | — | Additional class names for the area wrapper |
| cursorClassName | `string` | — | Additional class names for the cursor label |
| showDot | `boolean` | `false` | Show decorative dot indicator |

`[AST:packages/components/react-carbon/src/components/native/carbon/native-follow-cursor-carbon.tsx:L14]`

---

## NativeAvatarWithName

Avatar with animated name reveal on hover in configurable directions.

**Install:** `npx uitripled add native-avatar-with-name-shadcnui`
**Available in:** shadcn/ui, Base UI

### NativeAvatarProps

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| src | `string` | — | URL of the avatar image |
| name | `string` | — | Name to display on hover |
| fallback | `string` | — | Fallback text when image fails to load (usually initials) |
| size | `"sm" \| "md" \| "lg" \| "xl"` | `"md"` | Size variant of the avatar |
| direction | `"top" \| "bottom" \| "left" \| "right"` | `"bottom"` | Direction from which the name appears |
| className | `string` | — | Additional class names for the container |
| nameClassName | `string` | — | Additional class names for the name label |

`[AST:packages/components/react-shadcn/src/components/native/native-avatar-with-name-shadcnui.tsx:L8]`

---

## NativeAvatarExpand

Avatar that expands to reveal the name on hover/focus.

**Install:** `npx uitripled add native-avatar-expand-shadcnui`
**Available in:** shadcn/ui, Base UI

### NativeAvatarExpandProps

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| src | `string` | — | URL of the avatar image |
| name | `string` | — | Name of the person or entity |
| size | `"sm" \| "md" \| "lg" \| "xl"` | `"md"` | Size variant |
| className | `string` | — | Additional classes for the container |
| avatarClassName | `string` | — | Additional classes for the avatar |
| nameClassName | `string` | — | Additional classes for the name text |

`[AST:packages/components/react-shadcn/src/components/native/native-avatar-expand-shadcnui.tsx:L8]`

---

## NativeImageCheckbox

Image-based checkbox with animated selection state.

**Install:** `npx uitripled add native-image-checkbox-shadcnui`
**Available in:** shadcn/ui, Base UI, Carbon

### NativeImageCheckboxProps

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| src | `string` | — | URL of the image |
| alt | `string` | — | Alt text for the image |
| selected | `boolean` | — | Whether the checkbox is selected |
| onSelect | `(selected: boolean) => void` | — | Callback when the checkbox is clicked |
| size | `"sm" \| "md" \| "lg" \| "xl"` | `"md"` | Size variant |
| className | `string` | — | Additional classes for the container |
| imageClassName | `string` | — | Additional classes for the image |

`[AST:packages/components/react-shadcn/src/components/native/native-image-checkbox-shadcnui.tsx:L8]`

---

## NativeLikesCounter

Social likes counter with avatar stack and expandable popup.

**Install:** `npx uitripled add native-likes-counter-shadcnui`
**Available in:** shadcn/ui, Base UI

### NativeLikesCounterProps

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| count | `number` | — | Total like count |
| users | `LikeUser[]` | — | Array of users who liked |
| variant | `"default" \| "subtle" \| "outline" \| "ghost"` | — | Visual variant |
| size | `"sm" \| "default" \| "lg"` | — | Size variant |
| liked | `boolean` | — | Whether the current user has liked |
| onLike | `() => void` | — | Like toggle callback |
| onLoadMore | `() => Promise<LikeUser[]> \| LikeUser[]` | — | Load more users callback |
| hasMore | `boolean` | — | Whether more users can be loaded |
| maxAvatars | `number` | — | Maximum avatar count to display |
| maxVisibleInPopup | `number` | — | Maximum visible users in popup |
| className | `string` | — | Additional CSS classes |

`[AST:packages/components/react-shadcn/src/components/native/native-likes-counter-shadcnui.tsx:L15]`

---

## NativeNestedList

Animated collapsible nested list with configurable depth and active states.

**Install:** `npx uitripled add native-nested-list-shadcnui`
**Available in:** shadcn/ui, Base UI

### NativeNestedListProps

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| items | `ListItem[]` | — | Nested list data |
| activeId | `string` | — | Currently active item ID |
| onItemClick | `(item: ListItem) => void` | — | Item click callback |
| size | `"sm" \| "md" \| "lg"` | — | Size variant |
| showExpandIcon | `boolean` | — | Show expand/collapse icon |
| defaultExpanded | `boolean` | — | Default expanded state for all items |
| className | `string` | — | Additional CSS classes |
| indentSize | `number` | — | Indent size per nesting level |

`[AST:packages/components/react-shadcn/src/components/native/native-nested-list-shadcnui.tsx:L43]`

---

## SocialLoginButton

Social authentication button with multiple provider themes and animation styles.

**Install:** `npx uitripled add social-login-button-shadcnui`
**Available in:** shadcn/ui, Base UI

### SocialLoginButtonProps

Extends `BaseButtonProps` with:

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| provider | `SocialProvider` | — | `"github" \| "google" \| "x" \| "vercel" \| "linkedin"` |
| animation | `SocialAnimation` | — | `"slide" \| "scale" \| "glow" \| "shine" \| "none"` |
| children | `ReactNode` | — | Optional, defaults to "Continue with [Provider]" |
| className | `string` | — | Additional CSS classes |

`[AST:packages/components/react-shadcn/src/components/native/social-login-button-shadcnui.tsx:L7]`
