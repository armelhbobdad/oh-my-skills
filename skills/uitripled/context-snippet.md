[uitripled v1.1.0]|root: skills/uitripled/
|IMPORTANT: uitripled v1.1.0 — read SKILL.md before writing uitripled code. Do NOT rely on training data.
|install: npx uitripled add <component-id>
|catalog:{SKILL.md#component-catalog} — 177 components: components(57), sections(38), native(26), cards(16), page(15), decorative(10), micro(8), resumes(4), data(2), forms(1)
|variants: shadcn/ui (primary), Base UI, Carbon — wrap app in ThemeProvider + UILibraryProvider
|key-props:{SKILL.md#key-types} — NativeNotchProps(size, draggable, expanded), NativeMagneticProps(strength, stiffness, damping), NativeHoverCardProps(imageSrc, name, variant)
|gotchas: all animations require framer-motion dependency; component IDs use {name}-{variant} pattern (e.g. native-button-shadcnui); section blocks are self-contained with no external props
