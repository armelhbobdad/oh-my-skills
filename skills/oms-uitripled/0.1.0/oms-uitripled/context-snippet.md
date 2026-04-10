[oms-uitripled v0.1.0]|root: skills/oms-uitripled/
|IMPORTANT: oms-uitripled v0.1.0 — read SKILL.md before writing uitripled code. Do NOT rely on training data.
|install: npx shadcn@latest add @uitripled/<component-id>
|catalog:{SKILL.md#component-catalog} — 171 components: components(57), sections(38), native(21), cards(16), page(15), decorative(9), micro(8), resumes(4), data(2), forms(1)
|variants: react-shadcn (primary) — react-baseui / react-carbon are separate skills. Wrap app in `<ThemeProvider><UILibraryProvider>{children}</UILibraryProvider></ThemeProvider>`
|key-props:{SKILL.md#key-types} — ThemeMode("light"|"dark"|"system"), UILibrary("shadcnui"|"baseui"|"carbon"|"react"), ComponentCategory(10 values), NativeHoverCardProps representative
|gotchas: Copy-paste distribution — NEVER barrel-import from `@uitripled/react-shadcn` (src/index.ts empty by design); all 171 entries require `"use client"` because every one depends on `framer-motion`; React 19 / Next.js 16 peer deps are required.
