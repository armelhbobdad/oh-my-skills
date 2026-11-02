# UI Primitives Reference (react-shadcn `src/ui/`)

The shadcn/ui primitives `@uitripled/react-shadcn` ships in `src/ui/` (Button, Card and Dialog among them), what the copied components import as `@/components/ui/<file>`. Most wrap a Radix UI primitive. `Button`, `Card`, `CardContent`, `CardHeader`, `Input`, `Dialog` and `DialogContent` appear in the subpath-import example of `references/integration.md`; this file lists the other exports. Signatures are copied from the source at `a5ffb45`.

## Contents

- [Install and import](#install-and-import)
- [Primitives by file](#primitives-by-file)

## Install and import

Install a component with `npx shadcn@latest add @uitripled/<install id>`: the CLI writes the entry's `files[].target`, `components/uitripled/<install id>.tsx`, which you import from `@/components/uitripled/<install id>` `[SRC:packages/registry/registry.json:L1]` `[SRC:apps/docs/public/llms-full.txt:L49]`. A consumer of the npm package imports a subpath instead (`@uitripled/react-shadcn/components/<path>`, `/ui/<file>`, `/src/<path>`), never the bare package: `src/index.ts` is `export {};` `[SRC:packages/components/react-shadcn/package.json:L8]` `[SRC:packages/components/react-shadcn/tsup.config.ts:L4]` `[SRC:packages/components/react-shadcn/src/index.ts:L2]`. The props types are in `references/types.md` → Component props types; a props type the signature names and that file does not list is not exported by the source.

Copied components import a primitive by its shadcn path `[SRC:packages/components/react-shadcn/src/components/native/native-button-shadcnui.tsx:L3]`:

```tsx
"use client";
import { Badge } from "@/components/ui/badge";
import { Separator } from "@/components/ui/separator";

export function Status() {
  return (
    <div>
      <Badge variant="secondary">beta</Badge>
      <Separator />
    </div>
  );
}
```

## Primitives by file

No `registry.json` entry ships these files: the shadcn CLI installs the upstream shadcn/ui primitive a registry entry names in `registryDependencies` (for example `button`, `card`), and the npm package exposes them as `@uitripled/react-shadcn/ui/<file>`.

```tsx
// ui/avatar.tsx
const Avatar = React.forwardRef<React.ElementRef<typeof AvatarPrimitive.Root>, React.ComponentPropsWithoutRef<typeof AvatarPrimitive.Root>>(…)
const AvatarFallback = React.forwardRef<React.ElementRef<typeof AvatarPrimitive.Fallback>, React.ComponentPropsWithoutRef<typeof AvatarPrimitive.Fallback>>(…)
const AvatarImage = React.forwardRef<React.ElementRef<typeof AvatarPrimitive.Image>, React.ComponentPropsWithoutRef<typeof AvatarPrimitive.Image>>(…)
// ui/badge.tsx
function Badge({ className, variant, ...props }: BadgeProps)
const badgeVariants = cva(…)
// ui/button.tsx
const buttonVariants = cva(…)
// ui/card.tsx
const CardDescription = React.forwardRef<HTMLParagraphElement, React.HTMLAttributes<HTMLParagraphElement>>(…)
const CardFooter = React.forwardRef<HTMLDivElement, React.HTMLAttributes<HTMLDivElement>>(…)
const CardTitle = React.forwardRef<HTMLParagraphElement, React.HTMLAttributes<HTMLHeadingElement>>(…)
// ui/checkbox.tsx
const Checkbox = React.forwardRef<React.ElementRef<typeof CheckboxPrimitive.Root>, React.ComponentPropsWithoutRef<typeof CheckboxPrimitive.Root>>(…)
// ui/dialog.tsx
const DialogClose = DialogPrimitive.Close;
const DialogDescription = React.forwardRef<React.ElementRef<typeof DialogPrimitive.Description>, React.ComponentPropsWithoutRef<typeof DialogPrimitive.Description>>(…)
const DialogFooter = ({ className, ...props }: React.HTMLAttributes<HTMLDivElement>) => …
const DialogHeader = ({ className, ...props }: React.HTMLAttributes<HTMLDivElement>) => …
const DialogOverlay = React.forwardRef<React.ElementRef<typeof DialogPrimitive.Overlay>, React.ComponentPropsWithoutRef<typeof DialogPrimitive.Overlay>>(…)
const DialogPortal = DialogPrimitive.Portal;
const DialogTitle = React.forwardRef<React.ElementRef<typeof DialogPrimitive.Title>, React.ComponentPropsWithoutRef<typeof DialogPrimitive.Title>>(…)
const DialogTrigger = DialogPrimitive.Trigger;
// ui/dropdown-menu.tsx
const DropdownMenu = DropdownMenuPrimitive.Root;
const DropdownMenuCheckboxItem = React.forwardRef<React.ElementRef<typeof DropdownMenuPrimitive.CheckboxItem>, React.ComponentPropsWithoutRef<typeof DropdownMenuPrimitive.CheckboxItem>>(…)
const DropdownMenuContent = React.forwardRef<React.ElementRef<typeof DropdownMenuPrimitive.Content>, React.ComponentPropsWithoutRef<typeof DropdownMenuPrimitive.Content>>(…)
const DropdownMenuGroup = DropdownMenuPrimitive.Group;
const DropdownMenuItem = React.forwardRef<React.ElementRef<typeof DropdownMenuPrimitive.Item>, React.ComponentPropsWithoutRef<typeof DropdownMenuPrimitive.Item> & { inset?: boolean; }>(…)
const DropdownMenuLabel = React.forwardRef<React.ElementRef<typeof DropdownMenuPrimitive.Label>, React.ComponentPropsWithoutRef<typeof DropdownMenuPrimitive.Label> & { inset?: boolean; }>(…)
const DropdownMenuPortal = DropdownMenuPrimitive.Portal;
const DropdownMenuRadioGroup = DropdownMenuPrimitive.RadioGroup;
const DropdownMenuRadioItem = React.forwardRef<React.ElementRef<typeof DropdownMenuPrimitive.RadioItem>, React.ComponentPropsWithoutRef<typeof DropdownMenuPrimitive.RadioItem>>(…)
const DropdownMenuSeparator = React.forwardRef<React.ElementRef<typeof DropdownMenuPrimitive.Separator>, React.ComponentPropsWithoutRef<typeof DropdownMenuPrimitive.Separator>>(…)
const DropdownMenuShortcut = ({ className, ...props }: React.HTMLAttributes<HTMLSpanElement>) => …
const DropdownMenuSub = DropdownMenuPrimitive.Sub;
const DropdownMenuSubContent = React.forwardRef<React.ElementRef<typeof DropdownMenuPrimitive.SubContent>, React.ComponentPropsWithoutRef<typeof DropdownMenuPrimitive.SubContent>>(…)
const DropdownMenuSubTrigger = React.forwardRef<React.ElementRef<typeof DropdownMenuPrimitive.SubTrigger>, React.ComponentPropsWithoutRef<typeof DropdownMenuPrimitive.SubTrigger> & { inset?: boolean; }>(…)
const DropdownMenuTrigger = DropdownMenuPrimitive.Trigger;
// ui/label.tsx
const Label = React.forwardRef<HTMLLabelElement, LabelProps>(…)
// ui/scroll-area.tsx
const ScrollArea = React.forwardRef<HTMLDivElement, React.HTMLAttributes<HTMLDivElement>>(…)
const ScrollBar = React.forwardRef<HTMLDivElement, React.HTMLAttributes<HTMLDivElement>>(…)
// ui/select.tsx
function Select({ ...props }: React.ComponentProps<typeof SelectPrimitive.Root>)
function SelectContent({ className, children, position = "popper", align = "center", ...props }: React.ComponentProps<typeof SelectPrimitive.Content>)
function SelectGroup({ ...props }: React.ComponentProps<typeof SelectPrimitive.Group>)
function SelectItem({ className, children, ...props }: React.ComponentProps<typeof SelectPrimitive.Item>)
function SelectLabel({ className, ...props }: React.ComponentProps<typeof SelectPrimitive.Label>)
function SelectScrollDownButton({ className, ...props }: React.ComponentProps<typeof SelectPrimitive.ScrollDownButton>)
function SelectScrollUpButton({ className, ...props }: React.ComponentProps<typeof SelectPrimitive.ScrollUpButton>)
function SelectSeparator({ className, ...props }: React.ComponentProps<typeof SelectPrimitive.Separator>)
function SelectTrigger({ className, size = "default", children, ...props }: React.ComponentProps<typeof SelectPrimitive.Trigger> & { size?: "sm" | "default"; })
function SelectValue({ ...props }: React.ComponentProps<typeof SelectPrimitive.Value>)
// ui/separator.tsx
const Separator = React.forwardRef<React.ElementRef<typeof SeparatorPrimitive.Root>, React.ComponentPropsWithoutRef<typeof SeparatorPrimitive.Root>>(…)
// ui/slider.tsx
const Slider = React.forwardRef<React.ElementRef<typeof SliderPrimitive.Root>, React.ComponentPropsWithoutRef<typeof SliderPrimitive.Root>>(…)
// ui/switch.tsx
const Switch = React.forwardRef<React.ElementRef<typeof SwitchPrimitives.Root>, React.ComponentPropsWithoutRef<typeof SwitchPrimitives.Root>>(…)
// ui/tabs.tsx
const Tabs = TabsPrimitive.Root;
const TabsContent = React.forwardRef<React.ElementRef<typeof TabsPrimitive.Content>, React.ComponentPropsWithoutRef<typeof TabsPrimitive.Content>>(…)
const TabsList = React.forwardRef<React.ElementRef<typeof TabsPrimitive.List>, React.ComponentPropsWithoutRef<typeof TabsPrimitive.List>>(…)
const TabsTrigger = React.forwardRef<React.ElementRef<typeof TabsPrimitive.Trigger>, React.ComponentPropsWithoutRef<typeof TabsPrimitive.Trigger>>(…)
// ui/textarea.tsx
const Textarea = React.forwardRef<HTMLTextAreaElement, TextareaProps>(…)
// ui/tooltip.tsx
const Tooltip = TooltipPrimitive.Root;
const TooltipContent = React.forwardRef<React.ElementRef<typeof TooltipPrimitive.Content>, React.ComponentPropsWithoutRef<typeof TooltipPrimitive.Content>>(…)
const TooltipProvider = TooltipPrimitive.Provider;
const TooltipTrigger = TooltipPrimitive.Trigger;
```

| Export | Purpose | Source |
|--------|---------|--------|
| `Avatar` | wraps `AvatarPrimitive.Root` from `@radix-ui/react-avatar` | `[SRC:packages/components/react-shadcn/src/ui/avatar.tsx:L50]` |
| `AvatarFallback` | wraps `AvatarPrimitive.Fallback` from `@radix-ui/react-avatar` | `[SRC:packages/components/react-shadcn/src/ui/avatar.tsx:L50]` |
| `AvatarImage` | wraps `AvatarPrimitive.Image` from `@radix-ui/react-avatar` | `[SRC:packages/components/react-shadcn/src/ui/avatar.tsx:L50]` |
| `Badge` | `<div>` styled by `badgeVariants({ variant })` | `[SRC:packages/components/react-shadcn/src/ui/badge.tsx:L34]` |
| `badgeVariants` | class-variance-authority classes; `variant`: `default`, `secondary`, `destructive`, `outline`; defaults `variant: default` | `[SRC:packages/components/react-shadcn/src/ui/badge.tsx:L34]` |
| `buttonVariants` | class-variance-authority classes; `variant`: `default`, `destructive`, `outline`, `secondary`, `ghost`, `link`; `size`: `default`, `sm`, `lg`, `icon`; defaults `variant: default`, `size: default` | `[SRC:packages/components/react-shadcn/src/ui/button.tsx:L55]` |
| `CardDescription` | part of the shadcn/ui `card` primitive | `[SRC:packages/components/react-shadcn/src/ui/card.tsx:L81]` |
| `CardFooter` | part of the shadcn/ui `card` primitive | `[SRC:packages/components/react-shadcn/src/ui/card.tsx:L82]` |
| `CardTitle` | part of the shadcn/ui `card` primitive | `[SRC:packages/components/react-shadcn/src/ui/card.tsx:L84]` |
| `Checkbox` | wraps `CheckboxPrimitive.Root` from `@radix-ui/react-checkbox` | `[SRC:packages/components/react-shadcn/src/ui/checkbox.tsx:L30]` |
| `DialogClose` | wraps `DialogPrimitive.Close` from `@radix-ui/react-dialog` | `[SRC:packages/components/react-shadcn/src/ui/dialog.tsx:L113]` |
| `DialogDescription` | wraps `DialogPrimitive.Description` from `@radix-ui/react-dialog` | `[SRC:packages/components/react-shadcn/src/ui/dialog.tsx:L115]` |
| `DialogFooter` | part of the shadcn/ui `dialog` primitive | `[SRC:packages/components/react-shadcn/src/ui/dialog.tsx:L116]` |
| `DialogHeader` | part of the shadcn/ui `dialog` primitive | `[SRC:packages/components/react-shadcn/src/ui/dialog.tsx:L117]` |
| `DialogOverlay` | wraps `DialogPrimitive.Overlay` from `@radix-ui/react-dialog` | `[SRC:packages/components/react-shadcn/src/ui/dialog.tsx:L118]` |
| `DialogPortal` | wraps `DialogPrimitive.Portal` from `@radix-ui/react-dialog` | `[SRC:packages/components/react-shadcn/src/ui/dialog.tsx:L119]` |
| `DialogTitle` | wraps `DialogPrimitive.Title` from `@radix-ui/react-dialog` | `[SRC:packages/components/react-shadcn/src/ui/dialog.tsx:L120]` |
| `DialogTrigger` | wraps `DialogPrimitive.Trigger` from `@radix-ui/react-dialog` | `[SRC:packages/components/react-shadcn/src/ui/dialog.tsx:L121]` |
| `DropdownMenu` | wraps `DropdownMenuPrimitive.Root` from `@radix-ui/react-dropdown-menu` | `[SRC:packages/components/react-shadcn/src/ui/dropdown-menu.tsx:L185]` |
| `DropdownMenuCheckboxItem` | wraps `DropdownMenuPrimitive.CheckboxItem` from `@radix-ui/react-dropdown-menu` | `[SRC:packages/components/react-shadcn/src/ui/dropdown-menu.tsx:L186]` |
| `DropdownMenuContent` | wraps `DropdownMenuPrimitive.Content` from `@radix-ui/react-dropdown-menu` | `[SRC:packages/components/react-shadcn/src/ui/dropdown-menu.tsx:L187]` |
| `DropdownMenuGroup` | wraps `DropdownMenuPrimitive.Group` from `@radix-ui/react-dropdown-menu` | `[SRC:packages/components/react-shadcn/src/ui/dropdown-menu.tsx:L188]` |
| `DropdownMenuItem` | wraps `DropdownMenuPrimitive.Item` from `@radix-ui/react-dropdown-menu` | `[SRC:packages/components/react-shadcn/src/ui/dropdown-menu.tsx:L189]` |
| `DropdownMenuLabel` | wraps `DropdownMenuPrimitive.Label` from `@radix-ui/react-dropdown-menu` | `[SRC:packages/components/react-shadcn/src/ui/dropdown-menu.tsx:L190]` |
| `DropdownMenuPortal` | wraps `DropdownMenuPrimitive.Portal` from `@radix-ui/react-dropdown-menu` | `[SRC:packages/components/react-shadcn/src/ui/dropdown-menu.tsx:L191]` |
| `DropdownMenuRadioGroup` | wraps `DropdownMenuPrimitive.RadioGroup` from `@radix-ui/react-dropdown-menu` | `[SRC:packages/components/react-shadcn/src/ui/dropdown-menu.tsx:L192]` |
| `DropdownMenuRadioItem` | wraps `DropdownMenuPrimitive.RadioItem` from `@radix-ui/react-dropdown-menu` | `[SRC:packages/components/react-shadcn/src/ui/dropdown-menu.tsx:L193]` |
| `DropdownMenuSeparator` | wraps `DropdownMenuPrimitive.Separator` from `@radix-ui/react-dropdown-menu` | `[SRC:packages/components/react-shadcn/src/ui/dropdown-menu.tsx:L194]` |
| `DropdownMenuShortcut` | part of the shadcn/ui `dropdown-menu` primitive | `[SRC:packages/components/react-shadcn/src/ui/dropdown-menu.tsx:L195]` |
| `DropdownMenuSub` | wraps `DropdownMenuPrimitive.Sub` from `@radix-ui/react-dropdown-menu` | `[SRC:packages/components/react-shadcn/src/ui/dropdown-menu.tsx:L196]` |
| `DropdownMenuSubContent` | wraps `DropdownMenuPrimitive.SubContent` from `@radix-ui/react-dropdown-menu` | `[SRC:packages/components/react-shadcn/src/ui/dropdown-menu.tsx:L197]` |
| `DropdownMenuSubTrigger` | wraps `DropdownMenuPrimitive.SubTrigger` from `@radix-ui/react-dropdown-menu` | `[SRC:packages/components/react-shadcn/src/ui/dropdown-menu.tsx:L198]` |
| `DropdownMenuTrigger` | wraps `DropdownMenuPrimitive.Trigger` from `@radix-ui/react-dropdown-menu` | `[SRC:packages/components/react-shadcn/src/ui/dropdown-menu.tsx:L199]` |
| `Label` | part of the shadcn/ui `label` primitive | `[SRC:packages/components/react-shadcn/src/ui/label.tsx:L22]` |
| `ScrollArea` | part of the shadcn/ui `scroll-area` primitive | `[SRC:packages/components/react-shadcn/src/ui/scroll-area.tsx:L32]` |
| `ScrollBar` | part of the shadcn/ui `scroll-area` primitive | `[SRC:packages/components/react-shadcn/src/ui/scroll-area.tsx:L32]` |
| `Select` | wraps `SelectPrimitive.Root` from `@radix-ui/react-select` | `[SRC:packages/components/react-shadcn/src/ui/select.tsx:L175]` |
| `SelectContent` | wraps `SelectPrimitive.Content` from `@radix-ui/react-select` | `[SRC:packages/components/react-shadcn/src/ui/select.tsx:L176]` |
| `SelectGroup` | wraps `SelectPrimitive.Group` from `@radix-ui/react-select` | `[SRC:packages/components/react-shadcn/src/ui/select.tsx:L177]` |
| `SelectItem` | wraps `SelectPrimitive.Item` from `@radix-ui/react-select` | `[SRC:packages/components/react-shadcn/src/ui/select.tsx:L178]` |
| `SelectLabel` | wraps `SelectPrimitive.Label` from `@radix-ui/react-select` | `[SRC:packages/components/react-shadcn/src/ui/select.tsx:L179]` |
| `SelectScrollDownButton` | wraps `SelectPrimitive.ScrollDownButton` from `@radix-ui/react-select` | `[SRC:packages/components/react-shadcn/src/ui/select.tsx:L180]` |
| `SelectScrollUpButton` | wraps `SelectPrimitive.ScrollUpButton` from `@radix-ui/react-select` | `[SRC:packages/components/react-shadcn/src/ui/select.tsx:L181]` |
| `SelectSeparator` | wraps `SelectPrimitive.Separator` from `@radix-ui/react-select` | `[SRC:packages/components/react-shadcn/src/ui/select.tsx:L182]` |
| `SelectTrigger` | wraps `SelectPrimitive.Trigger` from `@radix-ui/react-select` | `[SRC:packages/components/react-shadcn/src/ui/select.tsx:L183]` |
| `SelectValue` | wraps `SelectPrimitive.Value` from `@radix-ui/react-select` | `[SRC:packages/components/react-shadcn/src/ui/select.tsx:L184]` |
| `Separator` | wraps `SeparatorPrimitive.Root` from `@radix-ui/react-separator` | `[SRC:packages/components/react-shadcn/src/ui/separator.tsx:L31]` |
| `Slider` | wraps `SliderPrimitive.Root` from `@radix-ui/react-slider` | `[SRC:packages/components/react-shadcn/src/ui/slider.tsx:L28]` |
| `Switch` | wraps `SwitchPrimitives.Root` from `@radix-ui/react-switch` | `[SRC:packages/components/react-shadcn/src/ui/switch.tsx:L29]` |
| `Tabs` | wraps `TabsPrimitive.Root` from `@radix-ui/react-tabs` | `[SRC:packages/components/react-shadcn/src/ui/tabs.tsx:L54]` |
| `TabsContent` | wraps `TabsPrimitive.Content` from `@radix-ui/react-tabs` | `[SRC:packages/components/react-shadcn/src/ui/tabs.tsx:L54]` |
| `TabsList` | wraps `TabsPrimitive.List` from `@radix-ui/react-tabs` | `[SRC:packages/components/react-shadcn/src/ui/tabs.tsx:L54]` |
| `TabsTrigger` | wraps `TabsPrimitive.Trigger` from `@radix-ui/react-tabs` | `[SRC:packages/components/react-shadcn/src/ui/tabs.tsx:L54]` |
| `Textarea` | part of the shadcn/ui `textarea` primitive | `[SRC:packages/components/react-shadcn/src/ui/textarea.tsx:L22]` |
| `Tooltip` | wraps `TooltipPrimitive.Root` from `@radix-ui/react-tooltip` | `[SRC:packages/components/react-shadcn/src/ui/tooltip.tsx:L32]` |
| `TooltipContent` | wraps `TooltipPrimitive.Content` from `@radix-ui/react-tooltip` | `[SRC:packages/components/react-shadcn/src/ui/tooltip.tsx:L32]` |
| `TooltipProvider` | wraps `TooltipPrimitive.Provider` from `@radix-ui/react-tooltip` | `[SRC:packages/components/react-shadcn/src/ui/tooltip.tsx:L32]` |
| `TooltipTrigger` | wraps `TooltipPrimitive.Trigger` from `@radix-ui/react-tooltip` | `[SRC:packages/components/react-shadcn/src/ui/tooltip.tsx:L32]` |
