# Full Type Definitions

### UILibrary

```typescript
type UILibrary = "shadcnui" | "baseui" | "carbon" | "react";
```

Controls which design system variant is active. `"react"` is a base variant without design system styling. `[AST:packages/utils/src/types.ts:L3]`

### ComponentCategory

```typescript
type ComponentCategory =
  | "microinteractions" | "components" | "page" | "data"
  | "decorative" | "blocks" | "resumes" | "forms" | "cards" | "native";
```

Registry classification for components. Maps to the `category` field in registry.json entries. `[AST:packages/utils/src/types.ts:L12]`

### NotchSize / NotchPosition

```typescript
type NotchSize = "sm" | "md" | "lg";
```

Used by NativeNotchProps for size configuration. `[AST:packages/components/react-shadcn/src/components/native/native-notch-shadcnui.tsx:L19]`

### SocialProvider / SocialAnimation

```typescript
type SocialProvider = "github" | "google" | "x" | "vercel" | "linkedin";
type SocialAnimation = "slide" | "scale" | "glow" | "shine" | "none";
```

Social login button configuration types. `[AST:packages/components/react-shadcn/src/components/native/social-login-button-shadcnui.tsx:L7]`

### ThemeMode

```typescript
type ThemeMode = "light" | "dark" | "system";
```

Theme provider configuration. `[AST:packages/components/react-shadcn/src/components/theme-provider.tsx:L9]`

### Form Element Types (shadcn/ui)

```typescript
type InputProps = React.InputHTMLAttributes<HTMLInputElement>;
type TextareaProps = React.TextareaHTMLAttributes<HTMLTextAreaElement>;
type LabelProps = React.LabelHTMLAttributes<HTMLLabelElement>;
type PasswordInputProps = Omit<React.InputHTMLAttributes<HTMLInputElement>, "type">;
```

Standard HTML element wrappers with Tailwind styling. `[AST:packages/components/react-shadcn/src/ui/input.tsx:L4]`
