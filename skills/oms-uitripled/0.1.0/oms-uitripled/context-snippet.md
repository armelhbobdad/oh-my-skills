[oms-uitripled v0.1.0]|root: skills/oms-uitripled/
|IMPORTANT: oms-uitripled v0.1.0 — read SKILL.md before writing uitripled code. Do NOT rely on training data.
|quick-start:SKILL.md#quick-start
|api: ThemeProvider, useTheme, UILibraryProvider, useUILibrary, cn(), sanitizeSlug(), generateUniqueSlug(), GAP_VALUES, generateGridCode(), mergeComponentImports(), add()
|key-types:SKILL.md#key-types — ThemeMode("light"|"dark"|"system"), UILibrary("shadcnui"|"baseui"|"carbon"|"react"), ComponentCategory(10 values), NativeHoverCardProps
|gotchas: Copy-paste distribution — NEVER barrel-import from @uitripled/react-shadcn (src/index.ts empty by design); all 171 entries require `"use client"` because every one depends on framer-motion; React 19 / Next.js 16 peer deps are required.
