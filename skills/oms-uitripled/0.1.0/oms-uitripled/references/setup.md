# Setup Reference: Providers & Hooks

## Contents

- [ThemeProvider](#themeprovider)
- [useTheme](#usetheme)
- [UILibraryProvider](#uilibraryprovider)
- [useUILibrary](#useuilibrary)
- [Provider ordering rule](#provider-ordering-rule)

## ThemeProvider

**Source:** `packages/components/react-shadcn/src/components/theme-provider.tsx`
**Provenance:** `[AST:packages/components/react-shadcn/src/components/theme-provider.tsx:L17]`

Wraps `next-themes`' `ThemeProvider` with project-opinionated defaults.

```tsx
import { ThemeProvider } from "@/components/theme-provider";

<ThemeProvider defaultTheme="system">
  {children}
</ThemeProvider>
```

**Props**

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| children | ReactNode | — | Wrapped content |
| defaultTheme | `ThemeMode` (`"light" \| "dark" \| "system"`) | `"system"` | Initial theme |

**Hardcoded behavior** (cannot be overridden via props):

- `attribute="class"` — toggles `.dark` / `.light` class on the `html` element
- `enableSystem` — respects `prefers-color-scheme`
- `disableTransitionOnChange={false}` — animated theme transitions enabled
- `storageKey="uitripled-theme"` — constant is exported as `THEME_STORAGE_KEY`

## useTheme

**Source:** `packages/components/react-shadcn/src/components/theme-provider.tsx`
**Provenance:** `[SRC:packages/components/react-shadcn/src/components/theme-provider.tsx:L37]`

Extends `next-themes` `useTheme()` with a `toggleTheme` helper.

```ts
const { theme, setTheme, resolvedTheme, systemTheme, toggleTheme } = useTheme();
```

`toggleTheme()` flips between `"light"` and `"dark"` based on `resolvedTheme` (i.e., it unconditionally resolves `"system"` first). It does NOT rotate through `"system"`.

## UILibraryProvider

**Source:** `packages/components/react-shadcn/src/ui-library-provider.tsx`
**Provenance:** `[AST:packages/components/react-shadcn/src/ui-library-provider.tsx:L32]`

Tracks which design system variant is active (shadcn/Base UI/Carbon). Hydration-safe: returns `null` until localStorage is read.

```tsx
import { UILibraryProvider } from "@/components/ui-library-provider";

<UILibraryProvider>{children}</UILibraryProvider>
```

**Props**

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| children | ReactNode | — | Wrapped content |

**Storage:** `localStorage` key `"uitripled-selected-library"`. Only accepts `"shadcnui" | "baseui" | "carbon"` on read — other values fall back to `"shadcnui"`.

Because this is hydration-gated, the provider returns `null` on first render until `isHydrated` flips. Place it as **inner** provider (see Provider ordering rule below).

## useUILibrary

**Source:** `packages/components/react-shadcn/src/ui-library-provider.tsx`
**Provenance:** `[AST:packages/components/react-shadcn/src/ui-library-provider.tsx:L23]`

```ts
const { selectedLibrary, setSelectedLibrary } = useUILibrary();
```

Must be called inside `<UILibraryProvider>`. Throws `Error("useUILibrary must be used within a UILibraryProvider")` if the context is missing. `setSelectedLibrary(lib)` persists to localStorage.

**Return type**

```ts
type UILibraryContextValue = {
  selectedLibrary: UILibrary;
  setSelectedLibrary: (library: UILibrary) => void;
};
```

Note: at runtime this hook only surfaces the three reachable values `"shadcnui" | "baseui" | "carbon"` even though the `UILibrary` type in `@uitripled/utils` also includes `"react"`.

## Provider ordering rule

`ThemeProvider` must wrap `UILibraryProvider`:

```tsx
<ThemeProvider defaultTheme="system">
  <UILibraryProvider>
    {children}
  </UILibraryProvider>
</ThemeProvider>
```

**Why:** `ThemeProvider` mounts `next-themes` which injects the `class` attribute on the `html` element before any child renders. `UILibraryProvider` waits on its own hydration gate (reads localStorage in a `useEffect`), so it must sit inside the already-mounted theme context. Reversing them does not crash, but it races the hydration boundaries.
