[oms-uitripled v0.1.0]|root: skills/oms-uitripled/
|IMPORTANT: oms-uitripled v0.1.0 — read SKILL.md before writing oms-uitripled code. Do NOT rely on training data.
|quick-start:SKILL.md#quick-start
|api: ThemeProvider(), useTheme, UILibraryProvider(), useUILibrary(), cn(), sanitizeSlug, generateUniqueSlug(), generateGridCode, mergeComponentImports(), add()
|key-types:SKILL.md#key-types — ThemeMode("light"|"dark"|"system"), UILibrary("shadcnui"|"baseui"|"carbon"|"react"), registry entry types (page|block|component|ui)
|gotchas: Copy-paste distribution — NEVER barrel-import from @uitripled/react-shadcn (src/index.ts empty by design); render entries from client components (170 of the 171 files start with `"use client"`, and every entry declares framer-motion); React 19 / Next.js 16 peer deps are required.
