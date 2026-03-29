# Full Integration Patterns

### Provider Wrapping

All UITripled components require `ThemeProvider` and `UILibraryProvider` at the app root:

```tsx
import { ThemeProvider, UILibraryProvider } from "@uitripled/react-shadcn";

function App() {
  return (
    <ThemeProvider>
      <UILibraryProvider>
        {/* Your components */}
      </UILibraryProvider>
    </ThemeProvider>
  );
}
```

`[SRC:packages/components/react-shadcn/src/components/theme-provider.tsx:L18]`
`[SRC:packages/components/react-shadcn/src/ui-library-provider.tsx:L31]`

### Framer Motion Integration

Every animated component depends on `framer-motion` and `react`. The registry declares these as dependencies per component:

```json
"dependencies": ["framer-motion", "react"]
```

Components use spring-based animations. Common spring params across native components: `stiffness` (default 150-300), `damping` (default 20-30).

### Multi-Variant Component Usage

Components are installed per variant. Same Props interface works across variants:

```bash
# shadcn/ui variant
npx uitripled add native-button-shadcnui

# Base UI variant (same Props, different styling)
npx uitripled add native-button-baseui
```

Registry IDs follow the pattern: `{component-name}-{variant}`. Strip the variant suffix to identify the base component.

### Tailwind CSS Integration

All components use Tailwind CSS classes. The `cn()` utility from `@uitripled/utils` merges classes with `tailwind-merge` to handle conflicts:

```tsx
import { cn } from "@uitripled/utils";

<div className={cn("px-4 py-2", isActive && "bg-primary", className)} />
```

`[SRC:packages/utils/src/cn.ts:L4]`

### Registry-Based Installation

The centralized registry at `packages/registry/registry.json` maps component IDs to source files, dependencies, and categories. The CLI reads this registry to resolve file paths during installation:

```typescript
// CLI fetches from registry
const componentData = await fetchComponent(componentName);
// Writes to detected component directory
await fs.writeFile(targetPath, componentData.files[0].content);
```

`[SRC:packages/uitripled/src/utils/registry.ts:L1]`
`[SRC:packages/uitripled/src/commands/add.ts:L8]`
