---
workflowType: 'test-skill'
skillName: 'oms-uitripled'
skillDir: 'skills/oms-uitripled/0.1.0/oms-uitripled'
runId: '20261102T190559Z-00c1915d'
testMode: 'naive'
forgeTier: 'Deep'
hardGate: 'blocked'
testResult: 'fail'
score: ''
threshold: '80%'
thresholdSource: 'workflow default (80%)'
analysisConfidence: ''
toolingStatus: 'ok'
workspaceDrift: 'ok'
health_check_dispatched: true
testDate: '2026-11-02T19:05:59Z'
stepsCompleted: ['init', 'detect-mode', 'coverage-check', 'coherence-check', 'external-validators', 'hard-gate', 'report']
nextWorkflow: 'update-skill'
---

# Test Report: oms-uitripled

<!--
Each stage writes its section in place of the heading below that it owns and
the placeholder comment under that heading, so every heading occurs once.
Before the result files are written, report.md §4c checks that each heading
occurs exactly once and that no placeholder comment is left: a stage that
skipped its section stops the run there. Do not reorder or delete the
headings or their placeholder comments.

Heading / owning step:
  Test Summary        → detect-mode §2
  Coverage Analysis   → coverage-check §5
  Coherence Analysis  → coherence-check §6
  External Validation → external-validators §5
  (hard gate)         → step-hard-gate reads the gap ledger; it writes the
                        Completeness Score section only when it blocks the run
  Completeness Score  → score §6, or step-hard-gate §3 on a blocked run
  Gap Report          → report §4c, rendered from the gap ledger (with the
                        Discovery Quality subsection)
-->

## Test Summary

**Skill:** oms-uitripled
**Test Mode:** naive
**Forge Tier:** Deep

**Mode Rationale:** metadata.json records `skill_type: "single"`, an individual skill, so the run checks API-surface coverage (naive mode); coherence is structural only and is not a scored category.

**Analysis Plan:**
- Coverage Check: every export in the skill's public API surface (11 metadata exports, the 171-entry registry catalog) checked against the pinned source at a5ffb45 with AST-backed extraction (Deep tier: ast-grep, gh, QMD), with signature and type coverage scored.
- Coherence Check: structural only: SKILL.md references to `references/*.md` resolve, internal links and section structure are intact; no cross-skill integration validation.

## Coverage Analysis

**Tier:** Deep
**Source Access:** full
**Source Path:** /home/armel/.skf/workspace/repos/github.com/moumen-soliman/uitripled
**Workspace Layout:** pnpm-workspaces (monorepo, 11 workspaces; the brief curates react-shadcn, registry, uitripled, utils and the docs app pages)
**Denominator:** Stratified scope, denominator: scope.include union (233 files matched, 327 exports union)
**Denominator Candidates** (stratified-scope audit trail):
- `stats.effective_denominator`: absent
- `scope.tier_a_include` union: absent
- `scope.include` union: 327    ← chosen (the barrel branch's set)
- exports-map subpath union: 426
- root barrel: 19                               (secondary candidate: root-barrel-vs-subpath-union audit)

**Files Analyzed:** 210

### Export Coverage

| Export | Type | Documented | Signature | Source Location | Status |
|--------|------|------------|-----------|-----------------|--------|
| `AIChatInterface` | function | no | - | packages/components/react-shadcn/src/components/components/chat/ai-chat-interface.tsx:54 | WARN |
| `AIGlowInput` | function | no | - | packages/components/react-shadcn/src/components/motion-core/ai-glow-input.tsx:25 | WARN |
| `AILoadingSkeleton` | function | no | - | packages/components/react-shadcn/src/components/motion-core/ai-loading-skeleton.tsx:41 | WARN |
| `AIResponseTyping` | function | no | - | packages/components/react-shadcn/src/components/motion-core/ai-response-typing.tsx:14 | WARN |
| `AIUnlockAnimation` | function | no | - | packages/components/react-shadcn/src/components/motion-core/ai-unlock-animation.tsx:10 | WARN |
| `AboutUsPage` | function | no | - | packages/components/react-shadcn/src/components/page/about/about-us-page.tsx:131 | WARN |
| `AboutUsSection` | function | no | - | packages/components/react-shadcn/src/components/sections/about-us-section.tsx:35 | WARN |
| `AnimatedAccordion` | function | no | - | packages/components/react-shadcn/src/components/disclosure/animated-accordion.tsx:25 | WARN |
| `AnimatedCardStack` | function | no | - | packages/components/react-shadcn/src/components/components/cards/shadcnui/animated-card-stack.tsx:18 | WARN |
| `AnimatedCheckbox` | function | no | - | packages/components/react-shadcn/src/components/forms/animated-checkbox.tsx:7 | WARN |
| `AnimatedDialog` | function | no | - | packages/components/react-shadcn/src/components/modals/animated-dialog.tsx:8 | WARN |
| `AnimatedList` | function | no | - | packages/components/react-shadcn/src/components/components/lists/animated-list.tsx:43 | WARN |
| `AnimatedNavbar` | function | no | - | packages/components/react-shadcn/src/components/navigation/animated-navbar.tsx:8 | WARN |
| `AnimatedPagination` | function | no | - | packages/components/react-shadcn/src/components/navigation/animated-pagination.tsx:7 | WARN |
| `AnimatedProfileMenu` | function | no | - | packages/components/react-shadcn/src/components/navigation/animated-profile-menu.tsx:74 | WARN |
| `AnimatedProgress` | function | no | - | packages/components/react-shadcn/src/components/data/progress/animated-progress.tsx:7 | WARN |
| `AnimatedQuoteBlock` | function | no | - | packages/components/react-shadcn/src/components/motion-core/animated-quote-block.tsx:12 | WARN |
| `AnimatedRadio` | function | no | - | packages/components/react-shadcn/src/components/forms/animated-radio.tsx:8 | WARN |
| `AnimatedSelect` | function | no | - | packages/components/react-shadcn/src/components/forms/animated-select.tsx:9 | WARN |
| `AnimatedSidebar` | function | no | - | packages/components/react-shadcn/src/components/navigation/animated-sidebar.tsx:14 | WARN |
| `AnimatedTabs` | function | no | - | packages/components/react-shadcn/src/components/components/tabs/animated-tabs.tsx:7 | WARN |
| `AnimatedTooltip` | function | no | - | packages/components/react-shadcn/src/components/tooltips/animated-tooltip.tsx:7 | WARN |
| `AutoRevealingHeading` | function | no | - | packages/components/react-shadcn/src/components/motion-core/auto-revealing-heading.tsx:13 | WARN |
| `Avatar` | const | no | - | packages/components/react-shadcn/src/ui/avatar.tsx:50 | WARN |
| `AvatarFallback` | const | no | - | packages/components/react-shadcn/src/ui/avatar.tsx:50 | WARN |
| `AvatarGroup` | function | no | - | packages/components/react-shadcn/src/components/avatars/avatar-group.tsx:27 | WARN |
| `AvatarImage` | const | no | - | packages/components/react-shadcn/src/ui/avatar.tsx:50 | WARN |
| `Badge` | function | no | - | packages/components/react-shadcn/src/ui/badge.tsx:34 | WARN |
| `BadgeProps` | interface | no | - | packages/components/react-shadcn/src/ui/badge.tsx:24 | WARN |
| `BentoGridBlock` | function | no | - | packages/components/react-shadcn/src/components/sections/bento-grid-block.tsx:125 | WARN |
| `BentoPreset` | interface | yes | - | packages/components/react-shadcn/src/lib/grid-utils.ts:12 | PASS |
| `BlogBlock` | function | no | - | packages/components/react-shadcn/src/components/sections/blog-block.tsx:55 | WARN |
| `BlogTypography` | function | no | - | packages/components/react-shadcn/src/components/components/blog/blog-typography.tsx:132 | WARN |
| `BottomModal` | function | no | - | packages/components/react-shadcn/src/components/modals/bottom-modal.tsx:8 | WARN |
| `BrowseFolder` | function | no | - | packages/components/react-shadcn/src/components/sections/browse-folder.tsx:111 | WARN |
| `BuilderComponent` | type | yes | - | packages/utils/src/types.ts:57 | PASS |
| `BuilderProjectPage` | type | yes | - | packages/utils/src/types.ts:64 | PASS |
| `Button` | const | yes | - | packages/components/react-shadcn/src/ui/button.tsx:55 | PASS |
| `ButtonProps` | interface | no | - | packages/components/react-shadcn/src/ui/button.tsx:35 | WARN |
| `CTABannerSection` | function | no | - | packages/components/react-shadcn/src/components/sections/cta-banner-section.tsx:35 | WARN |
| `CTABlock` | function | no | - | packages/components/react-shadcn/src/components/sections/cta-block.tsx:8 | WARN |
| `CTAHeroBlock` | function | no | - | packages/components/react-shadcn/src/components/sections/cta-hero-block.tsx:17 | WARN |
| `Card` | const | yes | - | packages/components/react-shadcn/src/ui/card.tsx:79 | PASS |
| `CardContent` | const | yes | - | packages/components/react-shadcn/src/ui/card.tsx:80 | PASS |
| `CardDescription` | const | no | - | packages/components/react-shadcn/src/ui/card.tsx:81 | WARN |
| `CardFooter` | const | no | - | packages/components/react-shadcn/src/ui/card.tsx:82 | WARN |
| `CardHeader` | const | yes | - | packages/components/react-shadcn/src/ui/card.tsx:83 | PASS |
| `CardTitle` | const | no | - | packages/components/react-shadcn/src/ui/card.tsx:84 | WARN |
| `CardsSlider` | function | no | - | packages/components/react-shadcn/src/components/components/sliders/cards-slider.tsx:87 | WARN |
| `CashFlowChart` | function | no | - | packages/components/react-shadcn/src/components/data/charts/cash-flow-chart.tsx:135 | WARN |
| `ChatApp` | function | no | - | packages/components/react-shadcn/src/components/components/chat/chat-app.tsx:39 | WARN |
| `Checkbox` | const | no | - | packages/components/react-shadcn/src/ui/checkbox.tsx:30 | WARN |
| `CinemaTicket` | function | no | - | packages/components/react-shadcn/src/components/sections/cinema-ticket.tsx:7 | WARN |
| `CodeOutput` | function | no | - | packages/components/react-shadcn/src/components/grid/code-output.tsx:14 | WARN |
| `CommandPalette` | function | no | - | packages/components/react-shadcn/src/components/search/command-palette.tsx:49 | WARN |
| `CommentThread` | function | no | - | packages/components/react-shadcn/src/components/components/comments/comment-thread.tsx:533 | WARN |
| `Component` | type | yes | - | packages/utils/src/types.ts:24 | PASS |
| `ComponentCategory` | type | yes | - | packages/utils/src/types.ts:12 | PASS |
| `ConferenceTicket` | function | no | - | packages/components/react-shadcn/src/components/sections/conference-ticket.tsx:8 | WARN |
| `ContactBlock` | function | no | - | packages/components/react-shadcn/src/components/sections/contact-block.tsx:32 | WARN |
| `ContactFormSection` | function | no | - | packages/components/react-shadcn/src/components/sections/contact-form-section.tsx:38 | WARN |
| `ContextMenu` | function | no | - | packages/components/react-shadcn/src/components/navigation/context-menu.tsx:14 | WARN |
| `ContextMenuBubble` | function | no | - | packages/components/react-shadcn/src/components/motion-core/context-menu-bubble.tsx:18 | WARN |
| `CourseContentPage` | function | no | - | packages/components/react-shadcn/src/components/components/course-content/course-content-page.tsx:786 | WARN |
| `CreditCard` | function | no | - | packages/components/react-shadcn/src/components/components/cards/shadcnui/credit-card.tsx:31 | WARN |
| `CurrencyConverterCard` | function | no | - | packages/components/react-shadcn/src/components/sections/currency-converter-card.tsx:41 | WARN |
| `DashboardPage` | function | no | - | packages/components/react-shadcn/src/components/components/stocks-dashboard/dashboard.tsx:605 | WARN |
| `DetailTaskCard` | function | no | - | packages/components/react-shadcn/src/components/components/cards/shadcnui/detail-task.tsx:115 | WARN |
| `Dialog` | const | yes | - | packages/components/react-shadcn/src/ui/dialog.tsx:112 | PASS |
| `DialogClose` | const | no | - | packages/components/react-shadcn/src/ui/dialog.tsx:113 | WARN |
| `DialogContent` | const | yes | - | packages/components/react-shadcn/src/ui/dialog.tsx:114 | PASS |
| `DialogDescription` | const | no | - | packages/components/react-shadcn/src/ui/dialog.tsx:115 | WARN |
| `DialogFooter` | function | no | - | packages/components/react-shadcn/src/ui/dialog.tsx:116 | WARN |
| `DialogHeader` | function | no | - | packages/components/react-shadcn/src/ui/dialog.tsx:117 | WARN |
| `DialogOverlay` | const | no | - | packages/components/react-shadcn/src/ui/dialog.tsx:118 | WARN |
| `DialogPortal` | const | no | - | packages/components/react-shadcn/src/ui/dialog.tsx:119 | WARN |
| `DialogTitle` | const | no | - | packages/components/react-shadcn/src/ui/dialog.tsx:120 | WARN |
| `DialogTrigger` | const | no | - | packages/components/react-shadcn/src/ui/dialog.tsx:121 | WARN |
| `DragToConfirmSlider` | function | no | - | packages/components/react-shadcn/src/components/motion-core/drag-to-confirm-slider.tsx:13 | WARN |
| `DraggableList` | function | no | - | packages/components/react-shadcn/src/components/components/lists/draggable-list.tsx:14 | WARN |
| `DropdownMenu` | const | no | - | packages/components/react-shadcn/src/ui/dropdown-menu.tsx:185 | WARN |
| `DropdownMenuCheckboxItem` | const | no | - | packages/components/react-shadcn/src/ui/dropdown-menu.tsx:186 | WARN |
| `DropdownMenuContent` | const | no | - | packages/components/react-shadcn/src/ui/dropdown-menu.tsx:187 | WARN |
| `DropdownMenuGroup` | const | no | - | packages/components/react-shadcn/src/ui/dropdown-menu.tsx:188 | WARN |
| `DropdownMenuItem` | const | no | - | packages/components/react-shadcn/src/ui/dropdown-menu.tsx:189 | WARN |
| `DropdownMenuLabel` | const | no | - | packages/components/react-shadcn/src/ui/dropdown-menu.tsx:190 | WARN |
| `DropdownMenuPortal` | const | no | - | packages/components/react-shadcn/src/ui/dropdown-menu.tsx:191 | WARN |
| `DropdownMenuRadioGroup` | const | no | - | packages/components/react-shadcn/src/ui/dropdown-menu.tsx:192 | WARN |
| `DropdownMenuRadioItem` | const | no | - | packages/components/react-shadcn/src/ui/dropdown-menu.tsx:193 | WARN |
| `DropdownMenuSeparator` | const | no | - | packages/components/react-shadcn/src/ui/dropdown-menu.tsx:194 | WARN |
| `DropdownMenuShortcut` | function | no | - | packages/components/react-shadcn/src/ui/dropdown-menu.tsx:195 | WARN |
| `DropdownMenuSub` | const | no | - | packages/components/react-shadcn/src/ui/dropdown-menu.tsx:196 | WARN |
| `DropdownMenuSubContent` | const | no | - | packages/components/react-shadcn/src/ui/dropdown-menu.tsx:197 | WARN |
| `DropdownMenuSubTrigger` | const | no | - | packages/components/react-shadcn/src/ui/dropdown-menu.tsx:198 | WARN |
| `DropdownMenuTrigger` | const | no | - | packages/components/react-shadcn/src/ui/dropdown-menu.tsx:199 | WARN |
| `DynamicSpotlightCTA` | function | no | - | packages/components/react-shadcn/src/components/motion-core/dynamic-spotlight-cta.tsx:22 | WARN |
| `DynamicTagCloud` | function | no | - | packages/components/react-shadcn/src/components/motion-core/dynamic-tag-cloud.tsx:15 | WARN |
| `EcommerceHighlightCard` | function | no | - | packages/components/react-shadcn/src/components/components/cards/shadcnui/ecommerce-highlight-card.tsx:64 | WARN |
| `ElasticSwitch` | function | no | - | packages/components/react-shadcn/src/components/micro/toggles/elastic-switch.tsx:6 | WARN |
| `ExpandingSearchDock` | function | no | - | packages/components/react-shadcn/src/components/motion-core/expanding-search-dock.tsx:12 | WARN |
| `FAQAccordionBlock` | function | no | - | packages/components/react-shadcn/src/components/sections/faq-accordion-block.tsx:43 | WARN |
| `FAQSection` | function | no | - | packages/components/react-shadcn/src/components/sections/faq-section.tsx:36 | WARN |
| `FadeSlideModal` | function | no | - | packages/components/react-shadcn/src/components/components/modal/fade-slide.tsx:7 | WARN |
| `FeatureCardsBlock` | function | no | - | packages/components/react-shadcn/src/components/sections/feature-cards-block.tsx:6 | WARN |
| `FeatureComparisonBlock` | function | no | - | packages/components/react-shadcn/src/components/sections/feature-comparison-block.tsx:90 | WARN |
| `FeatureGridSection` | function | no | - | packages/components/react-shadcn/src/components/sections/feature-grid-section.tsx:47 | WARN |
| `FloatingChatWidget` | function | no | - | packages/components/react-shadcn/src/components/components/chat/floating-chat-widget.tsx:112 | WARN |
| `FloatingGradient` | function | no | - | packages/components/react-shadcn/src/components/decorative/background/floating-gradient.tsx:5 | WARN |
| `FloatingInfoPanel` | function | no | - | packages/components/react-shadcn/src/components/motion-core/floating-info-panel.tsx:12 | WARN |
| `FloatingLabelInput` | function | no | - | packages/components/react-shadcn/src/components/components/inputs/floating-label-input.tsx:7 | WARN |
| `FluidModalTransition` | function | no | - | packages/components/react-shadcn/src/components/motion-core/fluid-modal-transition.tsx:13 | WARN |
| `FolderBrowser` | function | no | - | packages/components/react-shadcn/src/components/sections/browse-folder.tsx:21 | WARN |
| `FooterBlock` | function | no | - | packages/components/react-shadcn/src/components/sections/footer-block.tsx:47 | WARN |
| `GAP_VALUES` | - | yes | - | packages/components/react-shadcn/src/lib/grid-utils.ts:23 | PASS |
| `GalleryGridBlock` | function | no | - | packages/components/react-shadcn/src/components/sections/gallery-grid-block.tsx:49 | WARN |
| `GlassAccountSettingsCard` | function | no | - | packages/components/react-shadcn/src/components/components/forms/glass-account-settings.tsx:17 | WARN |
| `GlassBlogCard` | function | no | - | packages/components/react-shadcn/src/components/components/cards/shadcnui/glass-blog-card.tsx:39 | WARN |
| `GlassCheckoutCard` | function | no | - | packages/components/react-shadcn/src/components/components/cards/shadcnui/glass-checkout-card.tsx:17 | WARN |
| `GlassForgotPasswordCard` | function | no | - | packages/components/react-shadcn/src/components/components/forms/glass-forgot-password.tsx:9 | WARN |
| `GlassOrderSummary` | function | no | - | packages/components/react-shadcn/src/components/components/cards/shadcnui/glass-order-summary.tsx:49 | WARN |
| `GlassProfileSettingsCard` | function | no | - | packages/components/react-shadcn/src/components/components/forms/glass-profile-settings.tsx:14 | WARN |
| `GlassSignInCard` | function | no | - | packages/components/react-shadcn/src/components/components/forms/glass-sign-in.tsx:17 | WARN |
| `GlassSignUpCard` | function | no | - | packages/components/react-shadcn/src/components/components/forms/glass-sign-up.tsx:17 | WARN |
| `GlassVerificationCodeCard` | function | no | - | packages/components/react-shadcn/src/components/components/forms/glass-verification-code.tsx:10 | WARN |
| `GlassWalletCard` | function | no | - | packages/components/react-shadcn/src/components/components/cards/shadcnui/glass-wallet-card.tsx:36 | WARN |
| `GlassmorphismCTABlock` | function | no | - | packages/components/react-shadcn/src/components/sections/glassmorphism-cta-block.tsx:6 | WARN |
| `GlassmorphismHeroBlock` | function | no | - | packages/components/react-shadcn/src/components/sections/glassmorphism-hero-block.tsx:6 | WARN |
| `GlassmorphismLaunchTimelineBlock` | function | no | - | packages/components/react-shadcn/src/components/sections/glassmorphism-launch-timeline-block.tsx:65 | WARN |
| `GlassmorphismListenAppBlock` | function | no | - | packages/components/react-shadcn/src/components/sections/glassmorphism-listen-app-block.tsx:78 | WARN |
| `GlassmorphismLogoShowcaseBlock` | function | no | - | packages/components/react-shadcn/src/components/sections/glassmorphism-logo-showcase-block.tsx:26 | WARN |
| `GlassmorphismMinimalMetricsBlock` | function | no | - | packages/components/react-shadcn/src/components/sections/glassmorphism-minimal-metrics-block.tsx:42 | WARN |
| `GlassmorphismPortfolioBlock` | function | no | - | packages/components/react-shadcn/src/components/sections/glassmorphism-portfolio-block.tsx:95 | WARN |
| `GlassmorphismPricingBlock` | function | no | - | packages/components/react-shadcn/src/components/sections/glassmorphism-pricing-block.tsx:7 | WARN |
| `GlassmorphismProductUpdateBlock` | function | no | - | packages/components/react-shadcn/src/components/sections/glassmorphism-product-update-block.tsx:37 | WARN |
| `GlassmorphismStatisticsCard` | function | no | - | packages/components/react-shadcn/src/components/sections/glassmorphism-statistics-card.tsx:22 | WARN |
| `GlassmorphismTestimonialsBlock` | function | no | - | packages/components/react-shadcn/src/components/sections/glassmorphism-testimonials-block.tsx:6 | WARN |
| `GlowyWavesHero` | function | no | - | packages/components/react-shadcn/src/components/sections/glowy-waves-hero.tsx:61 | WARN |
| `GradientAnimation` | function | no | - | packages/components/react-shadcn/src/components/decorative/backgrounds/gradient-animation.tsx:5 | WARN |
| `GridCell` | function | yes | - | packages/components/react-shadcn/src/components/grid/grid-cell.tsx:14 | PASS |
| `GridPreview` | function | no | - | packages/components/react-shadcn/src/components/grid/grid-preview.tsx:28 | WARN |
| `GridPreviewProps` | interface | no | - | packages/components/react-shadcn/src/components/grid/grid-preview.tsx:10 | WARN |
| `HeartFavorite` | function | no | - | packages/components/react-shadcn/src/components/micro/icons/heart-favorite.tsx:7 | WARN |
| `HeroBlock` | function | no | - | packages/components/react-shadcn/src/components/sections/hero-block.tsx:7 | WARN |
| `HeroSection` | function | yes | - | packages/components/react-shadcn/src/components/sections/hero-section.tsx:7 | PASS |
| `HolographicWall` | function | no | - | packages/components/react-shadcn/src/components/motion-core/holographic-wall.tsx:35 | WARN |
| `HoverExpandCard` | function | no | - | packages/components/react-shadcn/src/components/components/cards/shadcnui/hover-expand.tsx:6 | WARN |
| `ImageSliderCard` | function | no | - | packages/components/react-shadcn/src/components/components/cards/image-slider-card.tsx:43 | WARN |
| `Input` | const | yes | - | packages/components/react-shadcn/src/ui/input.tsx:24 | PASS |
| `InputProps` | type | no | - | packages/components/react-shadcn/src/ui/input.tsx:4 | WARN |
| `InteractiveLogsTable` | function | no | - | packages/components/react-shadcn/src/components/sections/interactive-logs-table.tsx:398 | WARN |
| `InteractiveTimeline` | function | no | - | packages/components/react-shadcn/src/components/motion-core/interactive-timeline.tsx:64 | WARN |
| `KanbanBoard` | function | no | - | packages/components/react-shadcn/src/components/components/kanban/kanban-board.tsx:142 | WARN |
| `Label` | const | no | - | packages/components/react-shadcn/src/ui/label.tsx:22 | WARN |
| `LabelProps` | type | no | - | packages/components/react-shadcn/src/ui/label.tsx:4 | WARN |
| `LikeUser` | interface | no | - | packages/components/react-shadcn/src/components/native/native-likes-counter-shadcnui.tsx:9 | WARN |
| `LiquidCursor` | function | no | - | packages/components/react-shadcn/src/components/liquid-cursor.tsx:25 | WARN |
| `ListItem` | interface | no | - | packages/components/react-shadcn/src/components/native/native-nested-list-shadcnui.tsx:11 | WARN |
| `MacSearchbar` | function | no | - | packages/components/react-shadcn/src/components/search/mac-searchbar.tsx:16 | WARN |
| `MagneticAvatarGroup` | function | no | - | packages/components/react-shadcn/src/components/motion-core/magnetic-avatar-group.tsx:18 | WARN |
| `Messenger` | function | no | - | packages/components/react-shadcn/src/components/components/chat/messenger.tsx:162 | WARN |
| `MinimalResume` | function | no | - | packages/components/react-shadcn/src/components/components/resumes/shadcnui/minimal-resume.tsx:83 | WARN |
| `MoodGradientButton` | function | no | - | packages/components/react-shadcn/src/components/motion-core/mood-gradient-button.tsx:12 | WARN |
| `MorphingButtonAction` | interface | no | - | packages/components/react-shadcn/src/components/native/native-morphing-button-shadcnui.tsx:14 | WARN |
| `MultipleAccounts` | function | no | - | packages/components/react-shadcn/src/components/components/account-switcher/multiple-accounts.tsx:42 | WARN |
| `N8nWorkflowBlock` | function | no | - | packages/components/react-shadcn/src/components/sections/n8n-workflow-block.tsx:161 | WARN |
| `NativeAvatarExpand` | function | no | - | packages/components/react-shadcn/src/components/native/native-avatar-expand-shadcnui.tsx:55 | WARN |
| `NativeAvatarExpandProps` | interface | no | - | packages/components/react-shadcn/src/components/native/native-avatar-expand-shadcnui.tsx:8 | WARN |
| `NativeAvatarProps` | interface | no | - | packages/components/react-shadcn/src/components/native/native-avatar-with-name-shadcnui.tsx:8 | WARN |
| `NativeAvatarWithName` | function | no | - | packages/components/react-shadcn/src/components/native/native-avatar-with-name-shadcnui.tsx:59 | WARN |
| `NativeButton` | function | no | - | packages/components/react-shadcn/src/components/native/native-button-shadcnui.tsx:88 | WARN |
| `NativeButtonProps` | interface | no | - | packages/components/react-shadcn/src/components/native/native-button-shadcnui.tsx:9 | WARN |
| `NativeCounterUp` | function | no | - | packages/components/react-shadcn/src/components/native/native-counter-up-shadcnui.tsx:42 | WARN |
| `NativeCounterUpProps` | interface | no | - | packages/components/react-shadcn/src/components/native/native-counter-up-shadcnui.tsx:7 | WARN |
| `NativeDelete` | function | no | - | packages/components/react-shadcn/src/components/native/native-delete-shadcnui.tsx:73 | WARN |
| `NativeDeleteProps` | interface | no | - | packages/components/react-shadcn/src/components/native/native-delete-shadcnui.tsx:9 | WARN |
| `NativeDialog` | const | no | - | packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:86 | WARN |
| `NativeDialogClose` | const | no | - | packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:87 | WARN |
| `NativeDialogContent` | const | no | - | packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:88 | WARN |
| `NativeDialogDescription` | const | no | - | packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:89 | WARN |
| `NativeDialogFooter` | const | no | - | packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:90 | WARN |
| `NativeDialogHeader` | const | no | - | packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:91 | WARN |
| `NativeDialogOverlay` | const | no | - | packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:92 | WARN |
| `NativeDialogPortal` | const | no | - | packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:93 | WARN |
| `NativeDialogTitle` | const | no | - | packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:94 | WARN |
| `NativeDialogTrigger` | const | no | - | packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:95 | WARN |
| `NativeFlipText` | function | no | - | packages/components/react-shadcn/src/components/native/native-flip-text-shadcnui.tsx:20 | WARN |
| `NativeHoverCard` | function | yes | - | packages/components/react-shadcn/src/components/native/native-hover-card-shadcnui.tsx:81 | PASS |
| `NativeHoverCardProps` | interface | yes | - | packages/components/react-shadcn/src/components/native/native-hover-card-shadcnui.tsx:9 | PASS |
| `NativeImageCheckbox` | function | no | - | packages/components/react-shadcn/src/components/native/native-image-checkbox-shadcnui.tsx:63 | WARN |
| `NativeImageCheckboxProps` | interface | no | - | packages/components/react-shadcn/src/components/native/native-image-checkbox-shadcnui.tsx:8 | WARN |
| `NativeLikesCounter` | function | no | - | packages/components/react-shadcn/src/components/native/native-likes-counter-shadcnui.tsx:56 | WARN |
| `NativeLikesCounterProps` | interface | no | - | packages/components/react-shadcn/src/components/native/native-likes-counter-shadcnui.tsx:15 | WARN |
| `NativeLiquidButton` | function | no | - | packages/components/react-shadcn/src/components/native/native-liquid-button-shadcnui.tsx:61 | WARN |
| `NativeLiquidButtonProps` | interface | no | - | packages/components/react-shadcn/src/components/native/native-liquid-button-shadcnui.tsx:12 | WARN |
| `NativeMagnetic` | function | no | - | packages/components/react-shadcn/src/components/native/native-magnetic-shadcnui.tsx:61 | WARN |
| `NativeMagneticProps` | interface | no | - | packages/components/react-shadcn/src/components/native/native-magnetic-shadcnui.tsx:14 | WARN |
| `NativeMorphingButton` | function | no | - | packages/components/react-shadcn/src/components/native/native-morphing-button-shadcnui.tsx:69 | WARN |
| `NativeMorphingButtonProps` | interface | no | - | packages/components/react-shadcn/src/components/native/native-morphing-button-shadcnui.tsx:29 | WARN |
| `NativeNestedList` | function | no | - | packages/components/react-shadcn/src/components/native/native-nested-list-shadcnui.tsx:230 | WARN |
| `NativeNestedListProps` | interface | no | - | packages/components/react-shadcn/src/components/native/native-nested-list-shadcnui.tsx:43 | WARN |
| `NativeNotch` | function | no | - | packages/components/react-shadcn/src/components/native/native-notch-shadcnui.tsx:106 | WARN |
| `NativeNotchProps` | interface | no | - | packages/components/react-shadcn/src/components/native/native-notch-shadcnui.tsx:39 | WARN |
| `NativeNotificationBell` | function | no | - | packages/components/react-shadcn/src/components/native/native-notification-bell-shadcnui.tsx:68 | WARN |
| `NativeNotificationBellProps` | interface | no | - | packages/components/react-shadcn/src/components/native/native-notification-bell-shadcnui.tsx:8 | WARN |
| `NativeProfileNotch` | function | no | - | packages/components/react-shadcn/src/components/native/native-profile-notch-shadcnui.tsx:44 | WARN |
| `NativeProfileNotchProps` | interface | no | - | packages/components/react-shadcn/src/components/native/native-profile-notch-shadcnui.tsx:9 | WARN |
| `NativeStartNow` | function | no | - | packages/components/react-shadcn/src/components/native/native-start-now-shadcnui.tsx:78 | WARN |
| `NativeStartNowProps` | interface | no | - | packages/components/react-shadcn/src/components/native/native-start-now-shadcnui.tsx:9 | WARN |
| `NativeTabs` | function | no | - | packages/components/react-shadcn/src/components/native/native-tabs-shadcnui.tsx:18 | WARN |
| `NativeTooltip` | function | no | - | packages/components/react-shadcn/src/components/native/native-tooltip-shadcnui.tsx:92 | WARN |
| `NativeTooltipContent` | const | no | - | packages/components/react-shadcn/src/components/native/native-tooltip-shadcnui.tsx:93 | WARN |
| `NativeTooltipProvider` | function | no | - | packages/components/react-shadcn/src/components/native/native-tooltip-shadcnui.tsx:94 | WARN |
| `NativeTooltipTrigger` | const | no | - | packages/components/react-shadcn/src/components/native/native-tooltip-shadcnui.tsx:95 | WARN |
| `NativeTypewriter` | function | no | - | packages/components/react-shadcn/src/components/native/native-typewriter-shadcnui.tsx:43 | WARN |
| `NativeUserCard` | function | no | - | packages/components/react-shadcn/src/components/native/native-user-card-shadcnui.tsx:19 | WARN |
| `NewHeroSection` | function | no | - | packages/components/react-shadcn/src/components/sections/new-hero-section.tsx:7 | WARN |
| `NewsFeed` | function | no | - | packages/components/react-shadcn/src/components/components/news-feed/news-feed.tsx:243 | WARN |
| `NewsletterSignupBlock` | function | no | - | packages/components/react-shadcn/src/components/sections/newsletter-signup-block.tsx:11 | WARN |
| `NotchPosition` | interface | no | - | packages/components/react-shadcn/src/components/native/native-notch-shadcnui.tsx:24 | WARN |
| `NotchSize` | type | no | - | packages/components/react-shadcn/src/components/native/native-notch-shadcnui.tsx:19 | WARN |
| `NotificationCenter` | function | no | - | packages/components/react-shadcn/src/components/components/notifications/notification-center.tsx:86 | WARN |
| `NotionBlogPage` | function | no | - | packages/components/react-shadcn/src/components/sections/notion-blog-page.tsx:62 | WARN |
| `OurPartnersSection` | function | no | - | packages/components/react-shadcn/src/components/sections/our-partners-section.tsx:15 | WARN |
| `OurServicesSection` | function | no | - | packages/components/react-shadcn/src/components/sections/our-services-section.tsx:61 | WARN |
| `PasswordInput` | function | no | - | packages/components/react-shadcn/src/components/inputs/password-input.tsx:7 | WARN |
| `PasswordInputProps` | type | no | - | packages/components/react-shadcn/src/ui/password-input.tsx:9 | WARN |
| `PresetsPanel` | function | no | - | packages/components/react-shadcn/src/components/grid/presets-panel.tsx:12 | WARN |
| `PreviewDetailsCard` | function | no | - | packages/components/react-shadcn/src/components/micro/links/preview-details-card.tsx:19 | WARN |
| `PricingSection` | function | no | - | packages/components/react-shadcn/src/components/sections/pricing-section.tsx:61 | WARN |
| `ProfessionalResume` | function | no | - | packages/components/react-shadcn/src/components/components/resumes/shadcnui/professional-resume.tsx:59 | WARN |
| `ProfilePage` | function | no | - | packages/components/react-shadcn/src/components/components/profile/profile-page.tsx:16 | WARN |
| `ProjectCard` | function | no | - | packages/components/react-shadcn/src/components/components/cards/shadcnui/project-card.tsx:31 | WARN |
| `ProjectsBlock` | function | no | - | packages/components/react-shadcn/src/components/sections/projects-block.tsx:18 | WARN |
| `ReactiveBackgroundGrid` | function | no | - | packages/components/react-shadcn/src/components/motion-core/reactive-background-grid.tsx:11 | WARN |
| `RegistryItemType` | - | yes | - | - | WARN |
| `ResumeCard` | function | no | - | packages/components/react-shadcn/src/components/components/resumes/shadcnui/resume-card.tsx:138 | WARN |
| `RippleClickButton` | function | no | - | packages/components/react-shadcn/src/components/micro/buttons/ripple-click.tsx:12 | WARN |
| `SavedProject` | type | yes | - | packages/utils/src/types.ts:85 | PASS |
| `SavedProjectComponent` | type | yes | - | packages/utils/src/types.ts:71 | PASS |
| `SavedProjectPage` | type | yes | - | packages/utils/src/types.ts:77 | PASS |
| `ScaleHoverButton` | function | no | - | packages/components/react-shadcn/src/components/micro/buttons/scale-hover.tsx:5 | WARN |
| `ScrollArea` | const | no | - | packages/components/react-shadcn/src/ui/scroll-area.tsx:32 | WARN |
| `ScrollBar` | const | no | - | packages/components/react-shadcn/src/ui/scroll-area.tsx:32 | WARN |
| `ScrollProgressTracker` | function | no | - | packages/components/react-shadcn/src/components/motion-core/scroll-progress-tracker.tsx:11 | WARN |
| `ScrollReveal` | function | no | - | packages/components/react-shadcn/src/components/sections/scroll-reveal.tsx:47 | WARN |
| `Select` | function | no | - | packages/components/react-shadcn/src/ui/select.tsx:175 | WARN |
| `SelectContent` | function | no | - | packages/components/react-shadcn/src/ui/select.tsx:176 | WARN |
| `SelectGroup` | function | no | - | packages/components/react-shadcn/src/ui/select.tsx:177 | WARN |
| `SelectItem` | function | no | - | packages/components/react-shadcn/src/ui/select.tsx:178 | WARN |
| `SelectLabel` | function | no | - | packages/components/react-shadcn/src/ui/select.tsx:179 | WARN |
| `SelectScrollDownButton` | function | no | - | packages/components/react-shadcn/src/ui/select.tsx:180 | WARN |
| `SelectScrollUpButton` | function | no | - | packages/components/react-shadcn/src/ui/select.tsx:181 | WARN |
| `SelectSeparator` | function | no | - | packages/components/react-shadcn/src/ui/select.tsx:182 | WARN |
| `SelectTrigger` | function | no | - | packages/components/react-shadcn/src/ui/select.tsx:183 | WARN |
| `SelectValue` | function | no | - | packages/components/react-shadcn/src/ui/select.tsx:184 | WARN |
| `Separator` | const | no | - | packages/components/react-shadcn/src/ui/separator.tsx:31 | WARN |
| `ServicesGridBlock` | function | no | - | packages/components/react-shadcn/src/components/sections/services-grid-block.tsx:92 | WARN |
| `SettingsPanel` | function | no | - | packages/components/react-shadcn/src/components/grid/settings-panel.tsx:15 | WARN |
| `ShimmerButton` | function | no | - | packages/components/react-shadcn/src/components/micro/buttons/shimmer-button.tsx:6 | WARN |
| `SimpleCalendar` | function | no | - | packages/components/react-shadcn/src/components/forms/simple-calendar.tsx:10 | WARN |
| `Slider` | const | no | - | packages/components/react-shadcn/src/ui/slider.tsx:28 | WARN |
| `SmartHoverCard` | function | no | - | packages/components/react-shadcn/src/components/motion-core/smart-hover-card.tsx:14 | WARN |
| `SocialAnimation` | type | no | - | packages/components/react-shadcn/src/components/native/social-login-button-shadcnui.tsx:8 | WARN |
| `SocialLoginButton` | function | no | - | packages/components/react-shadcn/src/components/native/social-login-button-shadcnui.tsx:127 | WARN |
| `SocialLoginButtonProps` | interface | no | - | packages/components/react-shadcn/src/components/native/social-login-button-shadcnui.tsx:10 | WARN |
| `SocialProvider` | type | no | - | packages/components/react-shadcn/src/components/native/social-login-button-shadcnui.tsx:7 | WARN |
| `SpotlightSection` | function | no | - | packages/components/react-shadcn/src/components/motion-core/spotlight-section.tsx:12 | WARN |
| `StackedCardCarousel` | function | no | - | packages/components/react-shadcn/src/components/motion-core/stacked-card-carousel.tsx:17 | WARN |
| `StaggeredDropdown` | function | no | - | packages/components/react-shadcn/src/components/components/dropdown/staggered-items.tsx:9 | WARN |
| `StaggeredHero` | function | no | - | packages/components/react-shadcn/src/components/page/hero/staggered-text.tsx:30 | WARN |
| `StandardResume` | function | no | - | packages/components/react-shadcn/src/components/components/resumes/shadcnui/standard-resume.tsx:98 | WARN |
| `StatsCounterBlock` | function | no | - | packages/components/react-shadcn/src/components/sections/stats-counter-block.tsx:82 | WARN |
| `StatsSection` | function | no | - | packages/components/react-shadcn/src/components/sections/stats-section.tsx:40 | WARN |
| `StocksDashboard` | function | no | - | packages/components/react-shadcn/src/components/components/stocks-dashboard/stocks-dashboard.tsx:454 | WARN |
| `Switch` | const | no | - | packages/components/react-shadcn/src/ui/switch.tsx:29 | WARN |
| `SyncedLyricCaptions` | function | no | - | packages/components/react-shadcn/src/components/motion-core/synced-lyric-captions.tsx:66 | WARN |
| `THEME_STORAGE_KEY` | - | yes | - | packages/components/react-shadcn/src/components/theme-provider.tsx:11 | PASS |
| `Tabs` | const | no | - | packages/components/react-shadcn/src/ui/tabs.tsx:54 | WARN |
| `TabsContent` | const | no | - | packages/components/react-shadcn/src/ui/tabs.tsx:54 | WARN |
| `TabsList` | const | no | - | packages/components/react-shadcn/src/ui/tabs.tsx:54 | WARN |
| `TabsTrigger` | const | no | - | packages/components/react-shadcn/src/ui/tabs.tsx:54 | WARN |
| `TeamSectionBlock` | function | no | - | packages/components/react-shadcn/src/components/sections/team-section-block.tsx:326 | WARN |
| `TestimonialSection` | function | no | - | packages/components/react-shadcn/src/components/sections/testimonial-section.tsx:41 | WARN |
| `TestimonialsBlock` | function | no | - | packages/components/react-shadcn/src/components/sections/testimonials-block.tsx:55 | WARN |
| `TextContentEntry` | type | yes | - | packages/utils/src/types.ts:52 | PASS |
| `Textarea` | const | no | - | packages/components/react-shadcn/src/ui/textarea.tsx:22 | WARN |
| `TextareaProps` | type | no | - | packages/components/react-shadcn/src/ui/textarea.tsx:4 | WARN |
| `TheaterTicket` | function | no | - | packages/components/react-shadcn/src/components/sections/theater-ticket.tsx:7 | WARN |
| `ThemeMode` | type | yes | - | packages/components/react-shadcn/src/components/theme-provider.tsx:9 | PASS |
| `ThemeProvider` | function | yes | yes | packages/components/react-shadcn/src/components/theme-provider.tsx:18 | PASS |
| `TimelineBlock` | function | no | - | packages/components/react-shadcn/src/components/sections/timeline-block.tsx:47 | WARN |
| `ToastNotification` | function | no | - | packages/components/react-shadcn/src/components/page/notifications/toast-notification.tsx:9 | WARN |
| `Tooltip` | const | no | - | packages/components/react-shadcn/src/ui/tooltip.tsx:32 | WARN |
| `TooltipContent` | const | no | - | packages/components/react-shadcn/src/ui/tooltip.tsx:32 | WARN |
| `TooltipProvider` | const | no | - | packages/components/react-shadcn/src/ui/tooltip.tsx:32 | WARN |
| `TooltipTrigger` | const | no | - | packages/components/react-shadcn/src/ui/tooltip.tsx:32 | WARN |
| `TweetCard` | function | no | - | packages/components/react-shadcn/src/components/components/cards/tweet-card.tsx:17 | WARN |
| `UILibrary` | type | yes | - | packages/utils/src/types.ts:3 | PASS |
| `UILibraryContextValue` | - | yes | - | - | WARN |
| `UILibraryProvider` | function | yes | yes | packages/components/react-shadcn/src/ui-library-provider.tsx:31 | PASS |
| `VerifiedBadge` | function | no | - | packages/components/react-shadcn/src/components/native/native-verified-badge-shadcnui.tsx:104 | WARN |
| `VerifiedBadgeOutline` | function | no | - | packages/components/react-shadcn/src/components/native/native-verified-badge-shadcnui.tsx:162 | WARN |
| `VerifiedShieldBadge` | function | no | - | packages/components/react-shadcn/src/components/native/native-verified-badge-shadcnui.tsx:247 | WARN |
| `VolumeComponent` | function | no | - | packages/components/react-shadcn/src/components/components/sliders/volume-component.tsx:17 | WARN |
| `WeatherDashboard` | function | no | - | packages/components/react-shadcn/src/components/components/weather/weather-dashboard.tsx:390 | WARN |
| `WebPerformancePage` | function | no | - | packages/components/react-shadcn/src/components/web-performance/web-performance-page.tsx:394 | WARN |
| `WizardForm` | function | no | - | packages/components/react-shadcn/src/components/forms/wizard-form.tsx:165 | WARN |
| `add` | - | yes | - | - | WARN |
| `badgeVariants` | const | no | - | packages/components/react-shadcn/src/ui/badge.tsx:34 | WARN |
| `bentoPresets` | - | no | - | packages/components/react-shadcn/src/lib/grid-presets.ts:7 | WARN |
| `buttonVariants` | const | no | - | packages/components/react-shadcn/src/ui/button.tsx:55 | WARN |
| `cn` | - | yes | yes | packages/components/react-shadcn/src/lib/utils.ts:3 | PASS |
| `componentsRegistry` | - | no | - | packages/registry/src/index.tsx:8 | WARN |
| `countSavedProjectComponents` | - | yes | yes | packages/utils/src/builder-utils.ts:70 | PASS |
| `createPage` | - | yes | yes | packages/utils/src/builder-utils.ts:33 | PASS |
| `extractSavedPages` | - | yes | yes | packages/utils/src/builder-utils.ts:52 | PASS |
| `fetchComponent` | - | yes | - | - | WARN |
| `generateGridCode` | - | yes | yes | packages/components/react-shadcn/src/lib/grid-utils.ts:47 | PASS |
| `generateUniqueSlug` | - | yes | yes | packages/utils/src/builder-utils.ts:14 | PASS |
| `getCellKey` | - | yes | yes | packages/components/react-shadcn/src/lib/grid-utils.ts:101 | PASS |
| `getGapSliderIndex` | - | yes | no | packages/components/react-shadcn/src/lib/grid-utils.ts:32 | FAIL |
| `getGapValueFromIndex` | - | yes | yes | packages/components/react-shadcn/src/lib/grid-utils.ts:40 | PASS |
| `initializeCells` | - | yes | yes | packages/components/react-shadcn/src/lib/grid-utils.ts:76 | PASS |
| `isCellInSelection` | - | yes | yes | packages/components/react-shadcn/src/lib/grid-utils.ts:106 | PASS |
| `mergeComponentImports` | - | yes | yes | packages/utils/src/merge-imports.ts:6 | PASS |
| `nativeComponents` | - | no | - | packages/registry/src/registry/native.tsx:218 | WARN |
| `sanitizeSlug` | - | yes | yes | packages/utils/src/builder-utils.ts:7 | PASS |
| `uiComponents` | - | no | - | packages/registry/src/registry/ui.tsx:179 | WARN |
| `uiLibraryLabels` | - | yes | - | packages/utils/src/types.ts:5 | PASS |
| `useTheme` | - | yes | yes | packages/components/react-shadcn/src/components/theme-provider.tsx:35 | PASS |
| `useUILibrary` | - | yes | yes | packages/components/react-shadcn/src/ui-library-provider.tsx:23 | PASS |

### Coverage Summary

- **Exports Found:** 327
- **Documented:** 42 (12.84%)
- **Missing Documentation:** 285
- **Signature Mismatches:** 1
- **Stale Documentation:** 4, documented extras included
- **Scoped Out by the Brief:** `NativeAvatarExpandDefault` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx), `NativeAvatarExpandDemo` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx), `NativeAvatarExpandExtraLarge` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx), `NativeAvatarExpandLarge` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx), `NativeAvatarExpandNoImage` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx), `NativeAvatarExpandSmall` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx), `NativeAvatarWithNameDefault` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx), `NativeAvatarWithNameDemo` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx), `NativeAvatarWithNameLarge` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx), `NativeAvatarWithNameLeft` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx), `NativeAvatarWithNameNoImage` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx), `NativeAvatarWithNameRight` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx), `NativeAvatarWithNameSmall` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx), `NativeAvatarWithNameTop` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx), `NativeButtonDefault` (packages/components/react-shadcn/src/components/native/demo/native-button-demo.tsx), `NativeButtonDisabled` (packages/components/react-shadcn/src/components/native/demo/native-button-demo.tsx), `NativeButtonGlow` (packages/components/react-shadcn/src/components/native/demo/native-button-demo.tsx), `NativeButtonLoading` (packages/components/react-shadcn/src/components/native/demo/native-button-demo.tsx), `NativeButtonOutline` (packages/components/react-shadcn/src/components/native/demo/native-button-demo.tsx), `NativeDeleteCustomText` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx), `NativeDeleteDefault` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx), `NativeDeleteDemo` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx), `NativeDeleteDisabled` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx), `NativeDeleteLarge` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx), `NativeDeleteNoIcon` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx), `NativeDeleteSmall` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx), `NativeDialogDemo` (packages/components/react-shadcn/src/components/native/demo/native-dialog-demo.tsx), `NativeHoverCardBordered` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeHoverCardCustomButton` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeHoverCardCustomButtonText` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeHoverCardDefault` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeHoverCardDemo` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeHoverCardExtraLarge` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeHoverCardGlass` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeHoverCardLarge` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeHoverCardMinimal` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeHoverCardNoDescription` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeHoverCardNoUsername` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeHoverCardSmall` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeHoverCardWithFallback` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx), `NativeImageCheckboxDefault` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx), `NativeImageCheckboxDemo` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx), `NativeImageCheckboxExtraLarge` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx), `NativeImageCheckboxGrid` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx), `NativeImageCheckboxLarge` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx), `NativeImageCheckboxSelected` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx), `NativeImageCheckboxSmall` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx), `NativeLikesCounterDefault` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx), `NativeLikesCounterDemo` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx), `NativeLikesCounterGhost` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx), `NativeLikesCounterInteractive` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx), `NativeLikesCounterOutline` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx), `NativeLikesCounterSizes` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx), `NativeLikesCounterSubtle` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx), `NativeLiquidButtonCustomColor` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx), `NativeLiquidButtonDefault` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx), `NativeLiquidButtonDemo` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx), `NativeLiquidButtonError` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx), `NativeLiquidButtonGlow` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx), `NativeLiquidButtonGradient` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx), `NativeLiquidButtonLoading` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx), `NativeLiquidButtonSizes` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx), `NativeLiquidButtonSuccess` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx), `NativeLiquidButtonVariants` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx), `NativeLiquidButtonWave` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx), `NativeLiquidButtonWithProgress` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx), `NativeMagneticDefault` (packages/components/react-shadcn/src/components/native/demo/native-magnetic-demo.tsx), `NativeMagneticDemo` (packages/components/react-shadcn/src/components/native/demo/native-magnetic-demo.tsx), `NativeMagneticLink` (packages/components/react-shadcn/src/components/native/demo/native-magnetic-demo.tsx), `NativeMagneticStrong` (packages/components/react-shadcn/src/components/native/demo/native-magnetic-demo.tsx), `NativeMorphingButtonCustomIcon` (packages/components/react-shadcn/src/components/native/demo/native-morphing-button-demo.tsx), `NativeMorphingButtonDefault` (packages/components/react-shadcn/src/components/native/demo/native-morphing-button-demo.tsx), `NativeMorphingButtonDemo` (packages/components/react-shadcn/src/components/native/demo/native-morphing-button-demo.tsx), `NativeNestedListDemo` (packages/components/react-shadcn/src/components/native/demo/native-nested-list-demo.tsx), `NativeNotchDefault` (packages/components/react-shadcn/src/components/native/demo/native-notch-demo.tsx), `NativeNotchLeftAlign` (packages/components/react-shadcn/src/components/native/demo/native-notch-demo.tsx), `NativeNotchRelative` (packages/components/react-shadcn/src/components/native/demo/native-notch-demo.tsx), `NativeNotificationBellCustomIcon` (packages/components/react-shadcn/src/components/native/demo/native-notification-bell-demo.tsx), `NativeNotificationBellDefault` (packages/components/react-shadcn/src/components/native/demo/native-notification-bell-demo.tsx), `NativeNotificationBellDemo` (packages/components/react-shadcn/src/components/native/demo/native-notification-bell-demo.tsx), `NativeNotificationBellEmpty` (packages/components/react-shadcn/src/components/native/demo/native-notification-bell-demo.tsx), `NativeProfileNotchDefault` (packages/components/react-shadcn/src/components/native/demo/native-profile-notch-demo.tsx), `NativeProfileNotchOverlay` (packages/components/react-shadcn/src/components/native/demo/native-profile-notch-demo.tsx), `NativeStartNowCustomLabels` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowDefault` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowDemo` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowDisabled` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowGradient` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowHeartIcon` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowLarge` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowNoSparkles` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowOutline` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowRocketIcon` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowSmall` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowSolid` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowStarIcon` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeStartNowZapIcon` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx), `NativeTabsDemo` (packages/components/react-shadcn/src/components/native/demo/native-tabs-demo.tsx), `NativeTooltipBlur` (packages/components/react-shadcn/src/components/native/demo/native-tooltip-demo.tsx), `NativeTooltipDemo` (packages/components/react-shadcn/src/components/native/demo/native-tooltip-demo.tsx), `NativeTooltipScale` (packages/components/react-shadcn/src/components/native/demo/native-tooltip-demo.tsx), `NativeTypewriterDefault` (packages/components/react-shadcn/src/components/native/demo/native-typewriter-demo.tsx), `NativeTypewriterDemo` (packages/components/react-shadcn/src/components/native/demo/native-typewriter-demo.tsx), `NativeTypewriterLoop` (packages/components/react-shadcn/src/components/native/demo/native-typewriter-demo.tsx), `NativeTypewriterMultiline` (packages/components/react-shadcn/src/components/native/demo/native-typewriter-demo.tsx), `NativeUserCardDemo` (packages/components/react-shadcn/src/components/native/demo/native-user-card-demo.tsx), `NativeVerifiedBadgeCustomIcon` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx), `NativeVerifiedBadgeDefault` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx), `NativeVerifiedBadgeDemo` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx), `NativeVerifiedBadgeOutlineVariants` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx), `NativeVerifiedBadgeShield` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx), `NativeVerifiedBadgeSizes` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx), `NativeVerifiedBadgeWithLabel` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx), `NativeVerifiedBadgeWithTooltip` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx), `SocialButtonsGlow` (packages/components/react-shadcn/src/components/native/demo/social-login-demo.tsx), `SocialButtonsScale` (packages/components/react-shadcn/src/components/native/demo/social-login-demo.tsx), `SocialButtonsShine` (packages/components/react-shadcn/src/components/native/demo/social-login-demo.tsx), `SocialButtonsSlide` (packages/components/react-shadcn/src/components/native/demo/social-login-demo.tsx)

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 12.84% |
| Signature Accuracy | 94.12% |
| Type Coverage | 28.57% |

### Coverage Notes

- **Extraction:** the recipe runner (ast-grep 0.45.3, `component-library` recipe set) read 233 files in scope at a5ffb45 with status `ok` and no truncation. It reported tree-sitter syntax errors in 10 TSX files (`extraction.readByEye`, for example `components/blog/blog-typography.tsx:200`); the status stayed `ok`, so no by-eye pass ran. 22 names no recipe matched (`extractionGaps`, such as `useTheme`, `cn`, `GAP_VALUES`, `sanitizeSlug`) are on the surface; the 15 of them the skill documents with a signature were read by eye at their file and line.
- **Signatures:** 17 compared, 16 match. `getGapSliderIndex` names its parameter `gapValue` at `packages/components/react-shadcn/src/lib/grid-utils.ts:32` (byte-identical to `packages/utils/src/grid-utils.ts`), while `references/utils.md:257` documents `(value: number) => number`: type, order, optionality and return type match, the name does not.
- **Name collisions on the surface:** `cn` resolves to `packages/components/react-shadcn/src/lib/utils.ts:3` (`cn(...inputs: any[])`, a wrapper that imports `cn as baseCn` from `@uitripled/utils`); the skill documents and cites `packages/utils/src/cn.ts:4` (`cn(...inputs: ClassValue[])`), which matches its documented signature, so the comparison was judged a match. `references/utils.md:226` calls the react-shadcn copy an "identical implementation" and says a copied component needs no `@uitripled/utils` dependency, while `packages/components/react-shadcn/src/lib/utils.ts:1` imports from `@uitripled/utils`. `GridCell` resolves to a component function at `packages/components/react-shadcn/src/components/grid/grid-cell.tsx:14`; the skill documents the `GridCell` interface (`packages/utils/src/grid-utils.ts:5`), which matches.
- **Deep tier checks:** `gh api` confirms the pinned commit a5ffb45 exists upstream (committed 2026-03-21); upstream `master` has since moved to 05d1837 (pushed 2026-08-28), drift for audit-skill, outside this pinned-commit test. The documented versions match the source: `@uitripled/react-shadcn` 0.1.0 (`packages/components/react-shadcn/package.json:3`) and the `uitripled` CLI 1.1.0 (`packages/uitripled/package.json:3`). Type definitions cross-checked against their declarations: `ThemeMode`, `UILibrary` (4 members in `packages/utils/src/types.ts:3`, 3 in `packages/components/react-shadcn/src/types.ts:1`), `ComponentCategory`, both `Component` shapes, `GridCell`, `BentoPreset`, the Builder types and the `NativeHoverCardProps` fields all match. Re-exports traced: `packages/utils/src/index.ts` star-re-exports `cn`, `grid-utils`, `merge-imports`, `builder-utils` and `types`.
- **Stale names (4):** `RegistryItemType` has no declaration in the source (it names the `type` values of `registry.json` entries); `UILibraryContextValue` is a non-exported type at `packages/components/react-shadcn/src/ui-library-provider.tsx:14`; `add` (`packages/uitripled/src/commands/add.ts:8`) and `fetchComponent` (`packages/uitripled/src/utils/registry.ts:5`) are CLI-internal functions no package entry point exports. classify-stale found the last three declared at those lines (documented extras).
- **Guards:** `guards.inflation` fires: the scope.include union (327) exceeds the provenance map's 25 entries by 1208%, and `guards.umbrella.umbrella` is true (18 of the 19 root-barrel names are re-exports), so `stats.effective_denominator` is the recommended fix rather than `scope.tier_a_include`. `guards.staleScope` fires: `apps/docs/app/**/page.mdx` and `apps/docs/components/demos/**` match no file at a5ffb45 (no export restored). `guards.deflation` does not apply (no stored `effective_denominator`).
- **Numerator ground truth:** skipped (no inflation signature: `stats.exports_documented` 11, no `effective_denominator`).
- **Metadata coherence:** documented-surface counts diverge 97% (`stats.exports_documented` 11, provenance named exports 25, `confidence_distribution` sum 345): Medium metadata drift, plus the Info multi-denominator note (barrel 11, documented 345).
- **Provenance line check:** 4 map entries cite a line that is not the definition: `Component` (types.ts:25, defined at 24), `ThemeProvider` (theme-provider.tsx:17, at 18), `UILibraryProvider` (ui-library-provider.tsx:32, at 31), `useTheme` (theme-provider.tsx:37, at 35). The helper also lists 14 map entries metadata `exports[]` does not name (`orphaned`), which this section does not score.

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)

### Structural Findings

| # | Type | Severity | Detail | Line |
|---|------|----------|--------|------|
| 1 | export_not_in_usage | Medium | naive-coherence: exported function `fetchComponent` is not referenced in any usage-family section or reference file (named only in the SKILL.md `## Full API Reference` pointer) | 183 |

**Structural Issues:** 1

Checks with no finding: required sections (§2.1: `description` via `Overview`, `usage` via `Quick Start`, `api_surface` via `Component Catalog`), code fence balance (§2.2: 14 fences, balanced), opening fence language tags (§2.3: none bare), async/sync consistency (§2.5: none of the 26 function exports is called in a fenced example, so no claim is contradicted), table syntax (§2.6: no column drift), Scripts & Assets section (§2.7: no `scripts/` or `assets/` folder).

### Reference Consistency (split-body)

| # | Reference File | Export | Issue | SKILL.md Line | Reference Line |
|---|---------------|--------|-------|---------------|---------------|
| - | - | - | no mismatch | - | - |

**Exports Cross-Checked:** 10 (`ThemeProvider`, `useTheme`, `UILibraryProvider`, `useUILibrary`, `cn`, `ThemeMode`, `UILibrary`, `add`, `HeroSection`, `NativeHoverCardProps`)
**Mismatches Found:** 0

### Cross-Reference Observations (non-blocking)

Naive mode does not validate references; these pointers inside the skill package name content that is not where they say, recorded as Info observations:

- `SKILL.md:147` says `NativeHoverCardProps` is documented in `references/types.md`, which has no such entry (the interface is at `packages/components/react-shadcn/src/components/native/native-hover-card-shadcnui.tsx:9`).
- `SKILL.md:183` says the standalone CLI implementation notes and the `fetchComponent` helper are in `references/catalog.md`; `catalog.md` documents neither (the CLI comparison lives in `references/integration.md:104-118`).
- `references/types.md:191` points to a SKILL.md "Full API Reference → Registry schema" table that SKILL.md does not have.
- `references/utils.md:35` calls `packages/components/react-shadcn/src/lib/utils.ts` an identical implementation that removes the need for `@uitripled/utils`; that file imports `cn as baseCn` from `@uitripled/utils` and types its inputs `any[]` (`lib/utils.ts:1-4`).

### Migration & Deprecation (§2b)

Section 4b verification skipped: `evidence-report.md` (2026-04-11, SKF 1.0.0) has no YAML frontmatter, so no pinned `t2_future_count` (Case 4). SKILL.md carries no Migration & Deprecation Warnings section.

## External Validation

### skill-check
- **Available:** yes
- **Quality Score:** 100/100
- **Errors:** 0
- **Warnings:** 0
- **Diagnostics:** none

### Tessl Review
- **Result:** off — set tessl_review_workspace in preferences.yaml to enable

### Combined External Score
- **External Validation Score:** 100%
- **Tools used:** skill-check

## Completeness Score

**Result:** **FAIL**, not scored: the hard gate blocked this run on 1 Critical or High gap(s), listed first in the Gap Report.

## Gap Report

**Total Gaps:** 303
**Blocking (Critical + High):** 1
**Non-blocking (Medium + Low + Info):** 302

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|------------------|
| Critical | 1 | Read the source code and write or correct the documentation |
| High | 0 | None |
| Medium | 290 | Add type definitions, interface docs or the missing section |
| Low | 4 | Add examples or metadata |
| Info | 8 | Optional improvements, no action required |
| **Total** | **303** | |

### GAP-001: Signature mismatch: getGapSliderIndex

**Severity:** Critical
**Category:** Coverage (signature-mismatch)
**Source:** packages/components/react-shadcn/src/lib/grid-utils.ts:32
**Export:** getGapSliderIndex

**Issue:** documented `(value: number) => number`, source `(gapValue: number): number`: parameter name differs: documented 'value', source 'gapValue' (type, order, optionality and return type match)

**Remediation:** Update the documented signature of `getGapSliderIndex` from `(value: number) => number` to `(gapValue: number): number`, the signature the source defines at `packages/components/react-shadcn/src/lib/grid-utils.ts:32`.

### GAP-002: Missing export: AIChatInterface

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/chat/ai-chat-interface.tsx:54
**Export:** AIChatInterface

**Issue:** `AIChatInterface` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `AIChatInterface` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/chat/ai-chat-interface.tsx:54` and add its signature, its purpose and a usage example.

### GAP-003: Missing export: AIGlowInput

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/motion-core/ai-glow-input.tsx:25
**Export:** AIGlowInput

**Issue:** `AIGlowInput` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `AIGlowInput` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/motion-core/ai-glow-input.tsx:25` and add its signature, its purpose and a usage example.

### GAP-004: Missing export: AILoadingSkeleton

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/motion-core/ai-loading-skeleton.tsx:41
**Export:** AILoadingSkeleton

**Issue:** `AILoadingSkeleton` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `AILoadingSkeleton` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/motion-core/ai-loading-skeleton.tsx:41` and add its signature, its purpose and a usage example.

### GAP-005: Missing export: AIResponseTyping

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/motion-core/ai-response-typing.tsx:14
**Export:** AIResponseTyping

**Issue:** `AIResponseTyping` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `AIResponseTyping` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/motion-core/ai-response-typing.tsx:14` and add its signature, its purpose and a usage example.

### GAP-006: Missing export: AIUnlockAnimation

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/motion-core/ai-unlock-animation.tsx:10
**Export:** AIUnlockAnimation

**Issue:** `AIUnlockAnimation` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `AIUnlockAnimation` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/motion-core/ai-unlock-animation.tsx:10` and add its signature, its purpose and a usage example.

### GAP-007: Missing export: AboutUsPage

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/page/about/about-us-page.tsx:131
**Export:** AboutUsPage

**Issue:** `AboutUsPage` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `AboutUsPage` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/page/about/about-us-page.tsx:131` and add its signature, its purpose and a usage example.

### GAP-008: Missing export: AboutUsSection

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/about-us-section.tsx:35
**Export:** AboutUsSection

**Issue:** `AboutUsSection` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `AboutUsSection` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/about-us-section.tsx:35` and add its signature, its purpose and a usage example.

### GAP-009: Missing export: AnimatedAccordion

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/disclosure/animated-accordion.tsx:25
**Export:** AnimatedAccordion

**Issue:** `AnimatedAccordion` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `AnimatedAccordion` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/disclosure/animated-accordion.tsx:25` and add its signature, its purpose and a usage example.

### GAP-010: Missing export: AnimatedCardStack

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/cards/shadcnui/animated-card-stack.tsx:18
**Export:** AnimatedCardStack

**Issue:** `AnimatedCardStack` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `AnimatedCardStack` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/cards/shadcnui/animated-card-stack.tsx:18` and add its signature, its purpose and a usage example.

### GAP-011: Missing export: AnimatedCheckbox

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/forms/animated-checkbox.tsx:7
**Export:** AnimatedCheckbox

**Issue:** `AnimatedCheckbox` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `AnimatedCheckbox` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/forms/animated-checkbox.tsx:7` and add its signature, its purpose and a usage example.

### GAP-012: Missing export: AnimatedDialog

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/modals/animated-dialog.tsx:8
**Export:** AnimatedDialog

**Issue:** `AnimatedDialog` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `AnimatedDialog` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/modals/animated-dialog.tsx:8` and add its signature, its purpose and a usage example.

### GAP-013: Missing export: AnimatedList

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/lists/animated-list.tsx:43
**Export:** AnimatedList

**Issue:** `AnimatedList` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `AnimatedList` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/lists/animated-list.tsx:43` and add its signature, its purpose and a usage example.

### GAP-014: Missing export: AnimatedNavbar

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/navigation/animated-navbar.tsx:8
**Export:** AnimatedNavbar

**Issue:** `AnimatedNavbar` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `AnimatedNavbar` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/navigation/animated-navbar.tsx:8` and add its signature, its purpose and a usage example.

### GAP-015: Missing export: AnimatedPagination

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/navigation/animated-pagination.tsx:7
**Export:** AnimatedPagination

**Issue:** `AnimatedPagination` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `AnimatedPagination` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/navigation/animated-pagination.tsx:7` and add its signature, its purpose and a usage example.

### GAP-016: Missing export: AnimatedProfileMenu

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/navigation/animated-profile-menu.tsx:74
**Export:** AnimatedProfileMenu

**Issue:** `AnimatedProfileMenu` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `AnimatedProfileMenu` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/navigation/animated-profile-menu.tsx:74` and add its signature, its purpose and a usage example.

### GAP-017: Missing export: AnimatedProgress

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/data/progress/animated-progress.tsx:7
**Export:** AnimatedProgress

**Issue:** `AnimatedProgress` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `AnimatedProgress` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/data/progress/animated-progress.tsx:7` and add its signature, its purpose and a usage example.

### GAP-018: Missing export: AnimatedQuoteBlock

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/motion-core/animated-quote-block.tsx:12
**Export:** AnimatedQuoteBlock

**Issue:** `AnimatedQuoteBlock` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `AnimatedQuoteBlock` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/motion-core/animated-quote-block.tsx:12` and add its signature, its purpose and a usage example.

### GAP-019: Missing export: AnimatedRadio

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/forms/animated-radio.tsx:8
**Export:** AnimatedRadio

**Issue:** `AnimatedRadio` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `AnimatedRadio` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/forms/animated-radio.tsx:8` and add its signature, its purpose and a usage example.

### GAP-020: Missing export: AnimatedSelect

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/forms/animated-select.tsx:9
**Export:** AnimatedSelect

**Issue:** `AnimatedSelect` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `AnimatedSelect` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/forms/animated-select.tsx:9` and add its signature, its purpose and a usage example.

### GAP-021: Missing export: AnimatedSidebar

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/navigation/animated-sidebar.tsx:14
**Export:** AnimatedSidebar

**Issue:** `AnimatedSidebar` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `AnimatedSidebar` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/navigation/animated-sidebar.tsx:14` and add its signature, its purpose and a usage example.

### GAP-022: Missing export: AnimatedTabs

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/tabs/animated-tabs.tsx:7
**Export:** AnimatedTabs

**Issue:** `AnimatedTabs` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `AnimatedTabs` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/tabs/animated-tabs.tsx:7` and add its signature, its purpose and a usage example.

### GAP-023: Missing export: AnimatedTooltip

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/tooltips/animated-tooltip.tsx:7
**Export:** AnimatedTooltip

**Issue:** `AnimatedTooltip` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `AnimatedTooltip` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/tooltips/animated-tooltip.tsx:7` and add its signature, its purpose and a usage example.

### GAP-024: Missing export: AutoRevealingHeading

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/motion-core/auto-revealing-heading.tsx:13
**Export:** AutoRevealingHeading

**Issue:** `AutoRevealingHeading` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `AutoRevealingHeading` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/motion-core/auto-revealing-heading.tsx:13` and add its signature, its purpose and a usage example.

### GAP-025: Missing export: Avatar

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/avatar.tsx:50
**Export:** Avatar

**Issue:** `Avatar` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `Avatar` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/avatar.tsx:50` and add its signature, its purpose and a usage example.

### GAP-026: Missing export: AvatarFallback

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/avatar.tsx:50
**Export:** AvatarFallback

**Issue:** `AvatarFallback` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `AvatarFallback` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/avatar.tsx:50` and add its signature, its purpose and a usage example.

### GAP-027: Missing export: AvatarGroup

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/avatars/avatar-group.tsx:27
**Export:** AvatarGroup

**Issue:** `AvatarGroup` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `AvatarGroup` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/avatars/avatar-group.tsx:27` and add its signature, its purpose and a usage example.

### GAP-028: Missing export: AvatarImage

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/avatar.tsx:50
**Export:** AvatarImage

**Issue:** `AvatarImage` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `AvatarImage` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/avatar.tsx:50` and add its signature, its purpose and a usage example.

### GAP-029: Missing export: Badge

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/badge.tsx:34
**Export:** Badge

**Issue:** `Badge` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `Badge` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/badge.tsx:34` and add its signature, its purpose and a usage example.

### GAP-030: Missing type: BadgeProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** packages/components/react-shadcn/src/ui/badge.tsx:24
**Export:** BadgeProps

**Issue:** the type `BadgeProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `BadgeProps` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/badge.tsx:24` and list its fields or members.

### GAP-031: Missing export: BentoGridBlock

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/bento-grid-block.tsx:125
**Export:** BentoGridBlock

**Issue:** `BentoGridBlock` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `BentoGridBlock` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/bento-grid-block.tsx:125` and add its signature, its purpose and a usage example.

### GAP-032: Missing export: BlogBlock

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/blog-block.tsx:55
**Export:** BlogBlock

**Issue:** `BlogBlock` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `BlogBlock` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/blog-block.tsx:55` and add its signature, its purpose and a usage example.

### GAP-033: Missing export: BlogTypography

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/blog/blog-typography.tsx:132
**Export:** BlogTypography

**Issue:** `BlogTypography` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `BlogTypography` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/blog/blog-typography.tsx:132` and add its signature, its purpose and a usage example.

### GAP-034: Missing export: BottomModal

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/modals/bottom-modal.tsx:8
**Export:** BottomModal

**Issue:** `BottomModal` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `BottomModal` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/modals/bottom-modal.tsx:8` and add its signature, its purpose and a usage example.

### GAP-035: Missing export: BrowseFolder

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/browse-folder.tsx:111
**Export:** BrowseFolder

**Issue:** `BrowseFolder` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `BrowseFolder` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/browse-folder.tsx:111` and add its signature, its purpose and a usage example.

### GAP-036: Missing type: ButtonProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** packages/components/react-shadcn/src/ui/button.tsx:35
**Export:** ButtonProps

**Issue:** the type `ButtonProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ButtonProps` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/button.tsx:35` and list its fields or members.

### GAP-037: Missing export: CTABannerSection

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/cta-banner-section.tsx:35
**Export:** CTABannerSection

**Issue:** `CTABannerSection` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `CTABannerSection` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/cta-banner-section.tsx:35` and add its signature, its purpose and a usage example.

### GAP-038: Missing export: CTABlock

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/cta-block.tsx:8
**Export:** CTABlock

**Issue:** `CTABlock` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `CTABlock` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/cta-block.tsx:8` and add its signature, its purpose and a usage example.

### GAP-039: Missing export: CTAHeroBlock

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/cta-hero-block.tsx:17
**Export:** CTAHeroBlock

**Issue:** `CTAHeroBlock` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `CTAHeroBlock` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/cta-hero-block.tsx:17` and add its signature, its purpose and a usage example.

### GAP-040: Missing export: CardDescription

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/card.tsx:81
**Export:** CardDescription

**Issue:** `CardDescription` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `CardDescription` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/card.tsx:81` and add its signature, its purpose and a usage example.

### GAP-041: Missing export: CardFooter

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/card.tsx:82
**Export:** CardFooter

**Issue:** `CardFooter` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `CardFooter` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/card.tsx:82` and add its signature, its purpose and a usage example.

### GAP-042: Missing export: CardTitle

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/card.tsx:84
**Export:** CardTitle

**Issue:** `CardTitle` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `CardTitle` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/card.tsx:84` and add its signature, its purpose and a usage example.

### GAP-043: Missing export: CardsSlider

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/sliders/cards-slider.tsx:87
**Export:** CardsSlider

**Issue:** `CardsSlider` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `CardsSlider` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/sliders/cards-slider.tsx:87` and add its signature, its purpose and a usage example.

### GAP-044: Missing export: CashFlowChart

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/data/charts/cash-flow-chart.tsx:135
**Export:** CashFlowChart

**Issue:** `CashFlowChart` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `CashFlowChart` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/data/charts/cash-flow-chart.tsx:135` and add its signature, its purpose and a usage example.

### GAP-045: Missing export: ChatApp

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/chat/chat-app.tsx:39
**Export:** ChatApp

**Issue:** `ChatApp` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `ChatApp` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/chat/chat-app.tsx:39` and add its signature, its purpose and a usage example.

### GAP-046: Missing export: Checkbox

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/checkbox.tsx:30
**Export:** Checkbox

**Issue:** `Checkbox` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `Checkbox` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/checkbox.tsx:30` and add its signature, its purpose and a usage example.

### GAP-047: Missing export: CinemaTicket

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/cinema-ticket.tsx:7
**Export:** CinemaTicket

**Issue:** `CinemaTicket` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `CinemaTicket` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/cinema-ticket.tsx:7` and add its signature, its purpose and a usage example.

### GAP-048: Missing export: CodeOutput

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/grid/code-output.tsx:14
**Export:** CodeOutput

**Issue:** `CodeOutput` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `CodeOutput` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/grid/code-output.tsx:14` and add its signature, its purpose and a usage example.

### GAP-049: Missing export: CommandPalette

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/search/command-palette.tsx:49
**Export:** CommandPalette

**Issue:** `CommandPalette` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `CommandPalette` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/search/command-palette.tsx:49` and add its signature, its purpose and a usage example.

### GAP-050: Missing export: CommentThread

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/comments/comment-thread.tsx:533
**Export:** CommentThread

**Issue:** `CommentThread` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `CommentThread` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/comments/comment-thread.tsx:533` and add its signature, its purpose and a usage example.

### GAP-051: Missing export: ConferenceTicket

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/conference-ticket.tsx:8
**Export:** ConferenceTicket

**Issue:** `ConferenceTicket` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `ConferenceTicket` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/conference-ticket.tsx:8` and add its signature, its purpose and a usage example.

### GAP-052: Missing export: ContactBlock

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/contact-block.tsx:32
**Export:** ContactBlock

**Issue:** `ContactBlock` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `ContactBlock` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/contact-block.tsx:32` and add its signature, its purpose and a usage example.

### GAP-053: Missing export: ContactFormSection

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/contact-form-section.tsx:38
**Export:** ContactFormSection

**Issue:** `ContactFormSection` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `ContactFormSection` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/contact-form-section.tsx:38` and add its signature, its purpose and a usage example.

### GAP-054: Missing export: ContextMenu

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/navigation/context-menu.tsx:14
**Export:** ContextMenu

**Issue:** `ContextMenu` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `ContextMenu` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/navigation/context-menu.tsx:14` and add its signature, its purpose and a usage example.

### GAP-055: Missing export: ContextMenuBubble

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/motion-core/context-menu-bubble.tsx:18
**Export:** ContextMenuBubble

**Issue:** `ContextMenuBubble` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `ContextMenuBubble` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/motion-core/context-menu-bubble.tsx:18` and add its signature, its purpose and a usage example.

### GAP-056: Missing export: CourseContentPage

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/course-content/course-content-page.tsx:786
**Export:** CourseContentPage

**Issue:** `CourseContentPage` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `CourseContentPage` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/course-content/course-content-page.tsx:786` and add its signature, its purpose and a usage example.

### GAP-057: Missing export: CreditCard

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/cards/shadcnui/credit-card.tsx:31
**Export:** CreditCard

**Issue:** `CreditCard` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `CreditCard` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/cards/shadcnui/credit-card.tsx:31` and add its signature, its purpose and a usage example.

### GAP-058: Missing export: CurrencyConverterCard

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/currency-converter-card.tsx:41
**Export:** CurrencyConverterCard

**Issue:** `CurrencyConverterCard` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `CurrencyConverterCard` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/currency-converter-card.tsx:41` and add its signature, its purpose and a usage example.

### GAP-059: Missing export: DashboardPage

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/stocks-dashboard/dashboard.tsx:605
**Export:** DashboardPage

**Issue:** `DashboardPage` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `DashboardPage` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/stocks-dashboard/dashboard.tsx:605` and add its signature, its purpose and a usage example.

### GAP-060: Missing export: DetailTaskCard

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/cards/shadcnui/detail-task.tsx:115
**Export:** DetailTaskCard

**Issue:** `DetailTaskCard` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `DetailTaskCard` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/cards/shadcnui/detail-task.tsx:115` and add its signature, its purpose and a usage example.

### GAP-061: Missing export: DialogClose

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/dialog.tsx:113
**Export:** DialogClose

**Issue:** `DialogClose` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `DialogClose` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/dialog.tsx:113` and add its signature, its purpose and a usage example.

### GAP-062: Missing export: DialogDescription

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/dialog.tsx:115
**Export:** DialogDescription

**Issue:** `DialogDescription` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `DialogDescription` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/dialog.tsx:115` and add its signature, its purpose and a usage example.

### GAP-063: Missing export: DialogFooter

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/dialog.tsx:116
**Export:** DialogFooter

**Issue:** `DialogFooter` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `DialogFooter` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/dialog.tsx:116` and add its signature, its purpose and a usage example.

### GAP-064: Missing export: DialogHeader

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/dialog.tsx:117
**Export:** DialogHeader

**Issue:** `DialogHeader` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `DialogHeader` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/dialog.tsx:117` and add its signature, its purpose and a usage example.

### GAP-065: Missing export: DialogOverlay

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/dialog.tsx:118
**Export:** DialogOverlay

**Issue:** `DialogOverlay` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `DialogOverlay` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/dialog.tsx:118` and add its signature, its purpose and a usage example.

### GAP-066: Missing export: DialogPortal

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/dialog.tsx:119
**Export:** DialogPortal

**Issue:** `DialogPortal` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `DialogPortal` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/dialog.tsx:119` and add its signature, its purpose and a usage example.

### GAP-067: Missing export: DialogTitle

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/dialog.tsx:120
**Export:** DialogTitle

**Issue:** `DialogTitle` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `DialogTitle` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/dialog.tsx:120` and add its signature, its purpose and a usage example.

### GAP-068: Missing export: DialogTrigger

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/dialog.tsx:121
**Export:** DialogTrigger

**Issue:** `DialogTrigger` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `DialogTrigger` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/dialog.tsx:121` and add its signature, its purpose and a usage example.

### GAP-069: Missing export: DragToConfirmSlider

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/motion-core/drag-to-confirm-slider.tsx:13
**Export:** DragToConfirmSlider

**Issue:** `DragToConfirmSlider` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `DragToConfirmSlider` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/motion-core/drag-to-confirm-slider.tsx:13` and add its signature, its purpose and a usage example.

### GAP-070: Missing export: DraggableList

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/lists/draggable-list.tsx:14
**Export:** DraggableList

**Issue:** `DraggableList` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `DraggableList` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/lists/draggable-list.tsx:14` and add its signature, its purpose and a usage example.

### GAP-071: Missing export: DropdownMenu

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/dropdown-menu.tsx:185
**Export:** DropdownMenu

**Issue:** `DropdownMenu` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `DropdownMenu` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/dropdown-menu.tsx:185` and add its signature, its purpose and a usage example.

### GAP-072: Missing export: DropdownMenuCheckboxItem

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/dropdown-menu.tsx:186
**Export:** DropdownMenuCheckboxItem

**Issue:** `DropdownMenuCheckboxItem` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `DropdownMenuCheckboxItem` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/dropdown-menu.tsx:186` and add its signature, its purpose and a usage example.

### GAP-073: Missing export: DropdownMenuContent

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/dropdown-menu.tsx:187
**Export:** DropdownMenuContent

**Issue:** `DropdownMenuContent` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `DropdownMenuContent` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/dropdown-menu.tsx:187` and add its signature, its purpose and a usage example.

### GAP-074: Missing export: DropdownMenuGroup

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/dropdown-menu.tsx:188
**Export:** DropdownMenuGroup

**Issue:** `DropdownMenuGroup` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `DropdownMenuGroup` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/dropdown-menu.tsx:188` and add its signature, its purpose and a usage example.

### GAP-075: Missing export: DropdownMenuItem

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/dropdown-menu.tsx:189
**Export:** DropdownMenuItem

**Issue:** `DropdownMenuItem` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `DropdownMenuItem` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/dropdown-menu.tsx:189` and add its signature, its purpose and a usage example.

### GAP-076: Missing export: DropdownMenuLabel

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/dropdown-menu.tsx:190
**Export:** DropdownMenuLabel

**Issue:** `DropdownMenuLabel` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `DropdownMenuLabel` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/dropdown-menu.tsx:190` and add its signature, its purpose and a usage example.

### GAP-077: Missing export: DropdownMenuPortal

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/dropdown-menu.tsx:191
**Export:** DropdownMenuPortal

**Issue:** `DropdownMenuPortal` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `DropdownMenuPortal` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/dropdown-menu.tsx:191` and add its signature, its purpose and a usage example.

### GAP-078: Missing export: DropdownMenuRadioGroup

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/dropdown-menu.tsx:192
**Export:** DropdownMenuRadioGroup

**Issue:** `DropdownMenuRadioGroup` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `DropdownMenuRadioGroup` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/dropdown-menu.tsx:192` and add its signature, its purpose and a usage example.

### GAP-079: Missing export: DropdownMenuRadioItem

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/dropdown-menu.tsx:193
**Export:** DropdownMenuRadioItem

**Issue:** `DropdownMenuRadioItem` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `DropdownMenuRadioItem` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/dropdown-menu.tsx:193` and add its signature, its purpose and a usage example.

### GAP-080: Missing export: DropdownMenuSeparator

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/dropdown-menu.tsx:194
**Export:** DropdownMenuSeparator

**Issue:** `DropdownMenuSeparator` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `DropdownMenuSeparator` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/dropdown-menu.tsx:194` and add its signature, its purpose and a usage example.

### GAP-081: Missing export: DropdownMenuShortcut

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/dropdown-menu.tsx:195
**Export:** DropdownMenuShortcut

**Issue:** `DropdownMenuShortcut` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `DropdownMenuShortcut` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/dropdown-menu.tsx:195` and add its signature, its purpose and a usage example.

### GAP-082: Missing export: DropdownMenuSub

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/dropdown-menu.tsx:196
**Export:** DropdownMenuSub

**Issue:** `DropdownMenuSub` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `DropdownMenuSub` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/dropdown-menu.tsx:196` and add its signature, its purpose and a usage example.

### GAP-083: Missing export: DropdownMenuSubContent

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/dropdown-menu.tsx:197
**Export:** DropdownMenuSubContent

**Issue:** `DropdownMenuSubContent` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `DropdownMenuSubContent` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/dropdown-menu.tsx:197` and add its signature, its purpose and a usage example.

### GAP-084: Missing export: DropdownMenuSubTrigger

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/dropdown-menu.tsx:198
**Export:** DropdownMenuSubTrigger

**Issue:** `DropdownMenuSubTrigger` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `DropdownMenuSubTrigger` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/dropdown-menu.tsx:198` and add its signature, its purpose and a usage example.

### GAP-085: Missing export: DropdownMenuTrigger

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/dropdown-menu.tsx:199
**Export:** DropdownMenuTrigger

**Issue:** `DropdownMenuTrigger` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `DropdownMenuTrigger` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/dropdown-menu.tsx:199` and add its signature, its purpose and a usage example.

### GAP-086: Missing export: DynamicSpotlightCTA

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/motion-core/dynamic-spotlight-cta.tsx:22
**Export:** DynamicSpotlightCTA

**Issue:** `DynamicSpotlightCTA` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `DynamicSpotlightCTA` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/motion-core/dynamic-spotlight-cta.tsx:22` and add its signature, its purpose and a usage example.

### GAP-087: Missing export: DynamicTagCloud

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/motion-core/dynamic-tag-cloud.tsx:15
**Export:** DynamicTagCloud

**Issue:** `DynamicTagCloud` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `DynamicTagCloud` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/motion-core/dynamic-tag-cloud.tsx:15` and add its signature, its purpose and a usage example.

### GAP-088: Missing export: EcommerceHighlightCard

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/cards/shadcnui/ecommerce-highlight-card.tsx:64
**Export:** EcommerceHighlightCard

**Issue:** `EcommerceHighlightCard` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `EcommerceHighlightCard` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/cards/shadcnui/ecommerce-highlight-card.tsx:64` and add its signature, its purpose and a usage example.

### GAP-089: Missing export: ElasticSwitch

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/micro/toggles/elastic-switch.tsx:6
**Export:** ElasticSwitch

**Issue:** `ElasticSwitch` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `ElasticSwitch` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/micro/toggles/elastic-switch.tsx:6` and add its signature, its purpose and a usage example.

### GAP-090: Missing export: ExpandingSearchDock

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/motion-core/expanding-search-dock.tsx:12
**Export:** ExpandingSearchDock

**Issue:** `ExpandingSearchDock` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `ExpandingSearchDock` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/motion-core/expanding-search-dock.tsx:12` and add its signature, its purpose and a usage example.

### GAP-091: Missing export: FAQAccordionBlock

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/faq-accordion-block.tsx:43
**Export:** FAQAccordionBlock

**Issue:** `FAQAccordionBlock` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `FAQAccordionBlock` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/faq-accordion-block.tsx:43` and add its signature, its purpose and a usage example.

### GAP-092: Missing export: FAQSection

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/faq-section.tsx:36
**Export:** FAQSection

**Issue:** `FAQSection` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `FAQSection` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/faq-section.tsx:36` and add its signature, its purpose and a usage example.

### GAP-093: Missing export: FadeSlideModal

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/modal/fade-slide.tsx:7
**Export:** FadeSlideModal

**Issue:** `FadeSlideModal` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `FadeSlideModal` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/modal/fade-slide.tsx:7` and add its signature, its purpose and a usage example.

### GAP-094: Missing export: FeatureCardsBlock

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/feature-cards-block.tsx:6
**Export:** FeatureCardsBlock

**Issue:** `FeatureCardsBlock` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `FeatureCardsBlock` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/feature-cards-block.tsx:6` and add its signature, its purpose and a usage example.

### GAP-095: Missing export: FeatureComparisonBlock

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/feature-comparison-block.tsx:90
**Export:** FeatureComparisonBlock

**Issue:** `FeatureComparisonBlock` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `FeatureComparisonBlock` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/feature-comparison-block.tsx:90` and add its signature, its purpose and a usage example.

### GAP-096: Missing export: FeatureGridSection

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/feature-grid-section.tsx:47
**Export:** FeatureGridSection

**Issue:** `FeatureGridSection` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `FeatureGridSection` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/feature-grid-section.tsx:47` and add its signature, its purpose and a usage example.

### GAP-097: Missing export: FloatingChatWidget

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/chat/floating-chat-widget.tsx:112
**Export:** FloatingChatWidget

**Issue:** `FloatingChatWidget` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `FloatingChatWidget` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/chat/floating-chat-widget.tsx:112` and add its signature, its purpose and a usage example.

### GAP-098: Missing export: FloatingGradient

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/decorative/background/floating-gradient.tsx:5
**Export:** FloatingGradient

**Issue:** `FloatingGradient` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `FloatingGradient` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/decorative/background/floating-gradient.tsx:5` and add its signature, its purpose and a usage example.

### GAP-099: Missing export: FloatingInfoPanel

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/motion-core/floating-info-panel.tsx:12
**Export:** FloatingInfoPanel

**Issue:** `FloatingInfoPanel` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `FloatingInfoPanel` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/motion-core/floating-info-panel.tsx:12` and add its signature, its purpose and a usage example.

### GAP-100: Missing export: FloatingLabelInput

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/inputs/floating-label-input.tsx:7
**Export:** FloatingLabelInput

**Issue:** `FloatingLabelInput` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `FloatingLabelInput` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/inputs/floating-label-input.tsx:7` and add its signature, its purpose and a usage example.

### GAP-101: Missing export: FluidModalTransition

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/motion-core/fluid-modal-transition.tsx:13
**Export:** FluidModalTransition

**Issue:** `FluidModalTransition` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `FluidModalTransition` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/motion-core/fluid-modal-transition.tsx:13` and add its signature, its purpose and a usage example.

### GAP-102: Missing export: FolderBrowser

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/browse-folder.tsx:21
**Export:** FolderBrowser

**Issue:** `FolderBrowser` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `FolderBrowser` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/browse-folder.tsx:21` and add its signature, its purpose and a usage example.

### GAP-103: Missing export: FooterBlock

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/footer-block.tsx:47
**Export:** FooterBlock

**Issue:** `FooterBlock` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `FooterBlock` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/footer-block.tsx:47` and add its signature, its purpose and a usage example.

### GAP-104: Missing export: GalleryGridBlock

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/gallery-grid-block.tsx:49
**Export:** GalleryGridBlock

**Issue:** `GalleryGridBlock` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `GalleryGridBlock` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/gallery-grid-block.tsx:49` and add its signature, its purpose and a usage example.

### GAP-105: Missing export: GlassAccountSettingsCard

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/forms/glass-account-settings.tsx:17
**Export:** GlassAccountSettingsCard

**Issue:** `GlassAccountSettingsCard` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `GlassAccountSettingsCard` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/forms/glass-account-settings.tsx:17` and add its signature, its purpose and a usage example.

### GAP-106: Missing export: GlassBlogCard

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/cards/shadcnui/glass-blog-card.tsx:39
**Export:** GlassBlogCard

**Issue:** `GlassBlogCard` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `GlassBlogCard` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/cards/shadcnui/glass-blog-card.tsx:39` and add its signature, its purpose and a usage example.

### GAP-107: Missing export: GlassCheckoutCard

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/cards/shadcnui/glass-checkout-card.tsx:17
**Export:** GlassCheckoutCard

**Issue:** `GlassCheckoutCard` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `GlassCheckoutCard` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/cards/shadcnui/glass-checkout-card.tsx:17` and add its signature, its purpose and a usage example.

### GAP-108: Missing export: GlassForgotPasswordCard

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/forms/glass-forgot-password.tsx:9
**Export:** GlassForgotPasswordCard

**Issue:** `GlassForgotPasswordCard` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `GlassForgotPasswordCard` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/forms/glass-forgot-password.tsx:9` and add its signature, its purpose and a usage example.

### GAP-109: Missing export: GlassOrderSummary

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/cards/shadcnui/glass-order-summary.tsx:49
**Export:** GlassOrderSummary

**Issue:** `GlassOrderSummary` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `GlassOrderSummary` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/cards/shadcnui/glass-order-summary.tsx:49` and add its signature, its purpose and a usage example.

### GAP-110: Missing export: GlassProfileSettingsCard

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/forms/glass-profile-settings.tsx:14
**Export:** GlassProfileSettingsCard

**Issue:** `GlassProfileSettingsCard` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `GlassProfileSettingsCard` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/forms/glass-profile-settings.tsx:14` and add its signature, its purpose and a usage example.

### GAP-111: Missing export: GlassSignInCard

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/forms/glass-sign-in.tsx:17
**Export:** GlassSignInCard

**Issue:** `GlassSignInCard` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `GlassSignInCard` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/forms/glass-sign-in.tsx:17` and add its signature, its purpose and a usage example.

### GAP-112: Missing export: GlassSignUpCard

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/forms/glass-sign-up.tsx:17
**Export:** GlassSignUpCard

**Issue:** `GlassSignUpCard` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `GlassSignUpCard` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/forms/glass-sign-up.tsx:17` and add its signature, its purpose and a usage example.

### GAP-113: Missing export: GlassVerificationCodeCard

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/forms/glass-verification-code.tsx:10
**Export:** GlassVerificationCodeCard

**Issue:** `GlassVerificationCodeCard` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `GlassVerificationCodeCard` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/forms/glass-verification-code.tsx:10` and add its signature, its purpose and a usage example.

### GAP-114: Missing export: GlassWalletCard

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/cards/shadcnui/glass-wallet-card.tsx:36
**Export:** GlassWalletCard

**Issue:** `GlassWalletCard` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `GlassWalletCard` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/cards/shadcnui/glass-wallet-card.tsx:36` and add its signature, its purpose and a usage example.

### GAP-115: Missing export: GlassmorphismCTABlock

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/glassmorphism-cta-block.tsx:6
**Export:** GlassmorphismCTABlock

**Issue:** `GlassmorphismCTABlock` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `GlassmorphismCTABlock` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/glassmorphism-cta-block.tsx:6` and add its signature, its purpose and a usage example.

### GAP-116: Missing export: GlassmorphismHeroBlock

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/glassmorphism-hero-block.tsx:6
**Export:** GlassmorphismHeroBlock

**Issue:** `GlassmorphismHeroBlock` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `GlassmorphismHeroBlock` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/glassmorphism-hero-block.tsx:6` and add its signature, its purpose and a usage example.

### GAP-117: Missing export: GlassmorphismLaunchTimelineBlock

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/glassmorphism-launch-timeline-block.tsx:65
**Export:** GlassmorphismLaunchTimelineBlock

**Issue:** `GlassmorphismLaunchTimelineBlock` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `GlassmorphismLaunchTimelineBlock` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/glassmorphism-launch-timeline-block.tsx:65` and add its signature, its purpose and a usage example.

### GAP-118: Missing export: GlassmorphismListenAppBlock

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/glassmorphism-listen-app-block.tsx:78
**Export:** GlassmorphismListenAppBlock

**Issue:** `GlassmorphismListenAppBlock` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `GlassmorphismListenAppBlock` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/glassmorphism-listen-app-block.tsx:78` and add its signature, its purpose and a usage example.

### GAP-119: Missing export: GlassmorphismLogoShowcaseBlock

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/glassmorphism-logo-showcase-block.tsx:26
**Export:** GlassmorphismLogoShowcaseBlock

**Issue:** `GlassmorphismLogoShowcaseBlock` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `GlassmorphismLogoShowcaseBlock` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/glassmorphism-logo-showcase-block.tsx:26` and add its signature, its purpose and a usage example.

### GAP-120: Missing export: GlassmorphismMinimalMetricsBlock

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/glassmorphism-minimal-metrics-block.tsx:42
**Export:** GlassmorphismMinimalMetricsBlock

**Issue:** `GlassmorphismMinimalMetricsBlock` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `GlassmorphismMinimalMetricsBlock` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/glassmorphism-minimal-metrics-block.tsx:42` and add its signature, its purpose and a usage example.

### GAP-121: Missing export: GlassmorphismPortfolioBlock

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/glassmorphism-portfolio-block.tsx:95
**Export:** GlassmorphismPortfolioBlock

**Issue:** `GlassmorphismPortfolioBlock` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `GlassmorphismPortfolioBlock` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/glassmorphism-portfolio-block.tsx:95` and add its signature, its purpose and a usage example.

### GAP-122: Missing export: GlassmorphismPricingBlock

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/glassmorphism-pricing-block.tsx:7
**Export:** GlassmorphismPricingBlock

**Issue:** `GlassmorphismPricingBlock` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `GlassmorphismPricingBlock` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/glassmorphism-pricing-block.tsx:7` and add its signature, its purpose and a usage example.

### GAP-123: Missing export: GlassmorphismProductUpdateBlock

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/glassmorphism-product-update-block.tsx:37
**Export:** GlassmorphismProductUpdateBlock

**Issue:** `GlassmorphismProductUpdateBlock` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `GlassmorphismProductUpdateBlock` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/glassmorphism-product-update-block.tsx:37` and add its signature, its purpose and a usage example.

### GAP-124: Missing export: GlassmorphismStatisticsCard

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/glassmorphism-statistics-card.tsx:22
**Export:** GlassmorphismStatisticsCard

**Issue:** `GlassmorphismStatisticsCard` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `GlassmorphismStatisticsCard` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/glassmorphism-statistics-card.tsx:22` and add its signature, its purpose and a usage example.

### GAP-125: Missing export: GlassmorphismTestimonialsBlock

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/glassmorphism-testimonials-block.tsx:6
**Export:** GlassmorphismTestimonialsBlock

**Issue:** `GlassmorphismTestimonialsBlock` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `GlassmorphismTestimonialsBlock` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/glassmorphism-testimonials-block.tsx:6` and add its signature, its purpose and a usage example.

### GAP-126: Missing export: GlowyWavesHero

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/glowy-waves-hero.tsx:61
**Export:** GlowyWavesHero

**Issue:** `GlowyWavesHero` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `GlowyWavesHero` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/glowy-waves-hero.tsx:61` and add its signature, its purpose and a usage example.

### GAP-127: Missing export: GradientAnimation

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/decorative/backgrounds/gradient-animation.tsx:5
**Export:** GradientAnimation

**Issue:** `GradientAnimation` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `GradientAnimation` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/decorative/backgrounds/gradient-animation.tsx:5` and add its signature, its purpose and a usage example.

### GAP-128: Missing export: GridPreview

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/grid/grid-preview.tsx:28
**Export:** GridPreview

**Issue:** `GridPreview` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `GridPreview` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/grid/grid-preview.tsx:28` and add its signature, its purpose and a usage example.

### GAP-129: Missing type: GridPreviewProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** packages/components/react-shadcn/src/components/grid/grid-preview.tsx:10
**Export:** GridPreviewProps

**Issue:** the type `GridPreviewProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `GridPreviewProps` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/grid/grid-preview.tsx:10` and list its fields or members.

### GAP-130: Missing export: HeartFavorite

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/micro/icons/heart-favorite.tsx:7
**Export:** HeartFavorite

**Issue:** `HeartFavorite` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `HeartFavorite` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/micro/icons/heart-favorite.tsx:7` and add its signature, its purpose and a usage example.

### GAP-131: Missing export: HeroBlock

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/hero-block.tsx:7
**Export:** HeroBlock

**Issue:** `HeroBlock` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `HeroBlock` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/hero-block.tsx:7` and add its signature, its purpose and a usage example.

### GAP-132: Missing export: HolographicWall

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/motion-core/holographic-wall.tsx:35
**Export:** HolographicWall

**Issue:** `HolographicWall` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `HolographicWall` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/motion-core/holographic-wall.tsx:35` and add its signature, its purpose and a usage example.

### GAP-133: Missing export: HoverExpandCard

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/cards/shadcnui/hover-expand.tsx:6
**Export:** HoverExpandCard

**Issue:** `HoverExpandCard` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `HoverExpandCard` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/cards/shadcnui/hover-expand.tsx:6` and add its signature, its purpose and a usage example.

### GAP-134: Missing export: ImageSliderCard

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/cards/image-slider-card.tsx:43
**Export:** ImageSliderCard

**Issue:** `ImageSliderCard` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `ImageSliderCard` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/cards/image-slider-card.tsx:43` and add its signature, its purpose and a usage example.

### GAP-135: Missing type: InputProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** packages/components/react-shadcn/src/ui/input.tsx:4
**Export:** InputProps

**Issue:** the type `InputProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `InputProps` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/input.tsx:4` and list its fields or members.

### GAP-136: Missing export: InteractiveLogsTable

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/interactive-logs-table.tsx:398
**Export:** InteractiveLogsTable

**Issue:** `InteractiveLogsTable` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `InteractiveLogsTable` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/interactive-logs-table.tsx:398` and add its signature, its purpose and a usage example.

### GAP-137: Missing export: InteractiveTimeline

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/motion-core/interactive-timeline.tsx:64
**Export:** InteractiveTimeline

**Issue:** `InteractiveTimeline` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `InteractiveTimeline` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/motion-core/interactive-timeline.tsx:64` and add its signature, its purpose and a usage example.

### GAP-138: Missing export: KanbanBoard

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/kanban/kanban-board.tsx:142
**Export:** KanbanBoard

**Issue:** `KanbanBoard` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `KanbanBoard` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/kanban/kanban-board.tsx:142` and add its signature, its purpose and a usage example.

### GAP-139: Missing export: Label

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/label.tsx:22
**Export:** Label

**Issue:** `Label` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `Label` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/label.tsx:22` and add its signature, its purpose and a usage example.

### GAP-140: Missing type: LabelProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** packages/components/react-shadcn/src/ui/label.tsx:4
**Export:** LabelProps

**Issue:** the type `LabelProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `LabelProps` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/label.tsx:4` and list its fields or members.

### GAP-141: Missing type: LikeUser

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** packages/components/react-shadcn/src/components/native/native-likes-counter-shadcnui.tsx:9
**Export:** LikeUser

**Issue:** the type `LikeUser` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `LikeUser` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-likes-counter-shadcnui.tsx:9` and list its fields or members.

### GAP-142: Missing export: LiquidCursor

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/liquid-cursor.tsx:25
**Export:** LiquidCursor

**Issue:** `LiquidCursor` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `LiquidCursor` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/liquid-cursor.tsx:25` and add its signature, its purpose and a usage example.

### GAP-143: Missing type: ListItem

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** packages/components/react-shadcn/src/components/native/native-nested-list-shadcnui.tsx:11
**Export:** ListItem

**Issue:** the type `ListItem` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `ListItem` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-nested-list-shadcnui.tsx:11` and list its fields or members.

### GAP-144: Missing export: MacSearchbar

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/search/mac-searchbar.tsx:16
**Export:** MacSearchbar

**Issue:** `MacSearchbar` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `MacSearchbar` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/search/mac-searchbar.tsx:16` and add its signature, its purpose and a usage example.

### GAP-145: Missing export: MagneticAvatarGroup

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/motion-core/magnetic-avatar-group.tsx:18
**Export:** MagneticAvatarGroup

**Issue:** `MagneticAvatarGroup` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `MagneticAvatarGroup` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/motion-core/magnetic-avatar-group.tsx:18` and add its signature, its purpose and a usage example.

### GAP-146: Missing export: Messenger

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/chat/messenger.tsx:162
**Export:** Messenger

**Issue:** `Messenger` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `Messenger` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/chat/messenger.tsx:162` and add its signature, its purpose and a usage example.

### GAP-147: Missing export: MinimalResume

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/resumes/shadcnui/minimal-resume.tsx:83
**Export:** MinimalResume

**Issue:** `MinimalResume` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `MinimalResume` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/resumes/shadcnui/minimal-resume.tsx:83` and add its signature, its purpose and a usage example.

### GAP-148: Missing export: MoodGradientButton

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/motion-core/mood-gradient-button.tsx:12
**Export:** MoodGradientButton

**Issue:** `MoodGradientButton` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `MoodGradientButton` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/motion-core/mood-gradient-button.tsx:12` and add its signature, its purpose and a usage example.

### GAP-149: Missing type: MorphingButtonAction

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** packages/components/react-shadcn/src/components/native/native-morphing-button-shadcnui.tsx:14
**Export:** MorphingButtonAction

**Issue:** the type `MorphingButtonAction` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `MorphingButtonAction` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-morphing-button-shadcnui.tsx:14` and list its fields or members.

### GAP-150: Missing export: MultipleAccounts

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/account-switcher/multiple-accounts.tsx:42
**Export:** MultipleAccounts

**Issue:** `MultipleAccounts` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `MultipleAccounts` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/account-switcher/multiple-accounts.tsx:42` and add its signature, its purpose and a usage example.

### GAP-151: Missing export: N8nWorkflowBlock

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/n8n-workflow-block.tsx:161
**Export:** N8nWorkflowBlock

**Issue:** `N8nWorkflowBlock` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `N8nWorkflowBlock` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/n8n-workflow-block.tsx:161` and add its signature, its purpose and a usage example.

### GAP-152: Missing export: NativeAvatarExpand

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/native/native-avatar-expand-shadcnui.tsx:55
**Export:** NativeAvatarExpand

**Issue:** `NativeAvatarExpand` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `NativeAvatarExpand` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-avatar-expand-shadcnui.tsx:55` and add its signature, its purpose and a usage example.

### GAP-153: Missing type: NativeAvatarExpandProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** packages/components/react-shadcn/src/components/native/native-avatar-expand-shadcnui.tsx:8
**Export:** NativeAvatarExpandProps

**Issue:** the type `NativeAvatarExpandProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `NativeAvatarExpandProps` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-avatar-expand-shadcnui.tsx:8` and list its fields or members.

### GAP-154: Missing type: NativeAvatarProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** packages/components/react-shadcn/src/components/native/native-avatar-with-name-shadcnui.tsx:8
**Export:** NativeAvatarProps

**Issue:** the type `NativeAvatarProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `NativeAvatarProps` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-avatar-with-name-shadcnui.tsx:8` and list its fields or members.

### GAP-155: Missing export: NativeAvatarWithName

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/native/native-avatar-with-name-shadcnui.tsx:59
**Export:** NativeAvatarWithName

**Issue:** `NativeAvatarWithName` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `NativeAvatarWithName` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-avatar-with-name-shadcnui.tsx:59` and add its signature, its purpose and a usage example.

### GAP-156: Missing export: NativeButton

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/native/native-button-shadcnui.tsx:88
**Export:** NativeButton

**Issue:** `NativeButton` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `NativeButton` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-button-shadcnui.tsx:88` and add its signature, its purpose and a usage example.

### GAP-157: Missing type: NativeButtonProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** packages/components/react-shadcn/src/components/native/native-button-shadcnui.tsx:9
**Export:** NativeButtonProps

**Issue:** the type `NativeButtonProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `NativeButtonProps` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-button-shadcnui.tsx:9` and list its fields or members.

### GAP-158: Missing export: NativeCounterUp

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/native/native-counter-up-shadcnui.tsx:42
**Export:** NativeCounterUp

**Issue:** `NativeCounterUp` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `NativeCounterUp` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-counter-up-shadcnui.tsx:42` and add its signature, its purpose and a usage example.

### GAP-159: Missing type: NativeCounterUpProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** packages/components/react-shadcn/src/components/native/native-counter-up-shadcnui.tsx:7
**Export:** NativeCounterUpProps

**Issue:** the type `NativeCounterUpProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `NativeCounterUpProps` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-counter-up-shadcnui.tsx:7` and list its fields or members.

### GAP-160: Missing export: NativeDelete

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/native/native-delete-shadcnui.tsx:73
**Export:** NativeDelete

**Issue:** `NativeDelete` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `NativeDelete` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-delete-shadcnui.tsx:73` and add its signature, its purpose and a usage example.

### GAP-161: Missing type: NativeDeleteProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** packages/components/react-shadcn/src/components/native/native-delete-shadcnui.tsx:9
**Export:** NativeDeleteProps

**Issue:** the type `NativeDeleteProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `NativeDeleteProps` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-delete-shadcnui.tsx:9` and list its fields or members.

### GAP-162: Missing export: NativeDialog

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:86
**Export:** NativeDialog

**Issue:** `NativeDialog` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `NativeDialog` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:86` and add its signature, its purpose and a usage example.

### GAP-163: Missing export: NativeDialogClose

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:87
**Export:** NativeDialogClose

**Issue:** `NativeDialogClose` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `NativeDialogClose` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:87` and add its signature, its purpose and a usage example.

### GAP-164: Missing export: NativeDialogContent

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:88
**Export:** NativeDialogContent

**Issue:** `NativeDialogContent` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `NativeDialogContent` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:88` and add its signature, its purpose and a usage example.

### GAP-165: Missing export: NativeDialogDescription

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:89
**Export:** NativeDialogDescription

**Issue:** `NativeDialogDescription` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `NativeDialogDescription` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:89` and add its signature, its purpose and a usage example.

### GAP-166: Missing export: NativeDialogFooter

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:90
**Export:** NativeDialogFooter

**Issue:** `NativeDialogFooter` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `NativeDialogFooter` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:90` and add its signature, its purpose and a usage example.

### GAP-167: Missing export: NativeDialogHeader

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:91
**Export:** NativeDialogHeader

**Issue:** `NativeDialogHeader` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `NativeDialogHeader` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:91` and add its signature, its purpose and a usage example.

### GAP-168: Missing export: NativeDialogOverlay

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:92
**Export:** NativeDialogOverlay

**Issue:** `NativeDialogOverlay` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `NativeDialogOverlay` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:92` and add its signature, its purpose and a usage example.

### GAP-169: Missing export: NativeDialogPortal

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:93
**Export:** NativeDialogPortal

**Issue:** `NativeDialogPortal` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `NativeDialogPortal` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:93` and add its signature, its purpose and a usage example.

### GAP-170: Missing export: NativeDialogTitle

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:94
**Export:** NativeDialogTitle

**Issue:** `NativeDialogTitle` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `NativeDialogTitle` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:94` and add its signature, its purpose and a usage example.

### GAP-171: Missing export: NativeDialogTrigger

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:95
**Export:** NativeDialogTrigger

**Issue:** `NativeDialogTrigger` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `NativeDialogTrigger` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:95` and add its signature, its purpose and a usage example.

### GAP-172: Missing export: NativeFlipText

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/native/native-flip-text-shadcnui.tsx:20
**Export:** NativeFlipText

**Issue:** `NativeFlipText` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `NativeFlipText` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-flip-text-shadcnui.tsx:20` and add its signature, its purpose and a usage example.

### GAP-173: Missing export: NativeImageCheckbox

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/native/native-image-checkbox-shadcnui.tsx:63
**Export:** NativeImageCheckbox

**Issue:** `NativeImageCheckbox` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `NativeImageCheckbox` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-image-checkbox-shadcnui.tsx:63` and add its signature, its purpose and a usage example.

### GAP-174: Missing type: NativeImageCheckboxProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** packages/components/react-shadcn/src/components/native/native-image-checkbox-shadcnui.tsx:8
**Export:** NativeImageCheckboxProps

**Issue:** the type `NativeImageCheckboxProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `NativeImageCheckboxProps` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-image-checkbox-shadcnui.tsx:8` and list its fields or members.

### GAP-175: Missing export: NativeLikesCounter

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/native/native-likes-counter-shadcnui.tsx:56
**Export:** NativeLikesCounter

**Issue:** `NativeLikesCounter` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `NativeLikesCounter` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-likes-counter-shadcnui.tsx:56` and add its signature, its purpose and a usage example.

### GAP-176: Missing type: NativeLikesCounterProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** packages/components/react-shadcn/src/components/native/native-likes-counter-shadcnui.tsx:15
**Export:** NativeLikesCounterProps

**Issue:** the type `NativeLikesCounterProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `NativeLikesCounterProps` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-likes-counter-shadcnui.tsx:15` and list its fields or members.

### GAP-177: Missing export: NativeLiquidButton

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/native/native-liquid-button-shadcnui.tsx:61
**Export:** NativeLiquidButton

**Issue:** `NativeLiquidButton` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `NativeLiquidButton` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-liquid-button-shadcnui.tsx:61` and add its signature, its purpose and a usage example.

### GAP-178: Missing type: NativeLiquidButtonProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** packages/components/react-shadcn/src/components/native/native-liquid-button-shadcnui.tsx:12
**Export:** NativeLiquidButtonProps

**Issue:** the type `NativeLiquidButtonProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `NativeLiquidButtonProps` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-liquid-button-shadcnui.tsx:12` and list its fields or members.

### GAP-179: Missing export: NativeMagnetic

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/native/native-magnetic-shadcnui.tsx:61
**Export:** NativeMagnetic

**Issue:** `NativeMagnetic` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `NativeMagnetic` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-magnetic-shadcnui.tsx:61` and add its signature, its purpose and a usage example.

### GAP-180: Missing type: NativeMagneticProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** packages/components/react-shadcn/src/components/native/native-magnetic-shadcnui.tsx:14
**Export:** NativeMagneticProps

**Issue:** the type `NativeMagneticProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `NativeMagneticProps` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-magnetic-shadcnui.tsx:14` and list its fields or members.

### GAP-181: Missing export: NativeMorphingButton

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/native/native-morphing-button-shadcnui.tsx:69
**Export:** NativeMorphingButton

**Issue:** `NativeMorphingButton` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `NativeMorphingButton` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-morphing-button-shadcnui.tsx:69` and add its signature, its purpose and a usage example.

### GAP-182: Missing type: NativeMorphingButtonProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** packages/components/react-shadcn/src/components/native/native-morphing-button-shadcnui.tsx:29
**Export:** NativeMorphingButtonProps

**Issue:** the type `NativeMorphingButtonProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `NativeMorphingButtonProps` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-morphing-button-shadcnui.tsx:29` and list its fields or members.

### GAP-183: Missing export: NativeNestedList

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/native/native-nested-list-shadcnui.tsx:230
**Export:** NativeNestedList

**Issue:** `NativeNestedList` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `NativeNestedList` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-nested-list-shadcnui.tsx:230` and add its signature, its purpose and a usage example.

### GAP-184: Missing type: NativeNestedListProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** packages/components/react-shadcn/src/components/native/native-nested-list-shadcnui.tsx:43
**Export:** NativeNestedListProps

**Issue:** the type `NativeNestedListProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `NativeNestedListProps` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-nested-list-shadcnui.tsx:43` and list its fields or members.

### GAP-185: Missing export: NativeNotch

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/native/native-notch-shadcnui.tsx:106
**Export:** NativeNotch

**Issue:** `NativeNotch` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `NativeNotch` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-notch-shadcnui.tsx:106` and add its signature, its purpose and a usage example.

### GAP-186: Missing type: NativeNotchProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** packages/components/react-shadcn/src/components/native/native-notch-shadcnui.tsx:39
**Export:** NativeNotchProps

**Issue:** the type `NativeNotchProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `NativeNotchProps` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-notch-shadcnui.tsx:39` and list its fields or members.

### GAP-187: Missing export: NativeNotificationBell

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/native/native-notification-bell-shadcnui.tsx:68
**Export:** NativeNotificationBell

**Issue:** `NativeNotificationBell` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `NativeNotificationBell` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-notification-bell-shadcnui.tsx:68` and add its signature, its purpose and a usage example.

### GAP-188: Missing type: NativeNotificationBellProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** packages/components/react-shadcn/src/components/native/native-notification-bell-shadcnui.tsx:8
**Export:** NativeNotificationBellProps

**Issue:** the type `NativeNotificationBellProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `NativeNotificationBellProps` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-notification-bell-shadcnui.tsx:8` and list its fields or members.

### GAP-189: Missing export: NativeProfileNotch

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/native/native-profile-notch-shadcnui.tsx:44
**Export:** NativeProfileNotch

**Issue:** `NativeProfileNotch` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `NativeProfileNotch` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-profile-notch-shadcnui.tsx:44` and add its signature, its purpose and a usage example.

### GAP-190: Missing type: NativeProfileNotchProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** packages/components/react-shadcn/src/components/native/native-profile-notch-shadcnui.tsx:9
**Export:** NativeProfileNotchProps

**Issue:** the type `NativeProfileNotchProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `NativeProfileNotchProps` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-profile-notch-shadcnui.tsx:9` and list its fields or members.

### GAP-191: Missing export: NativeStartNow

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/native/native-start-now-shadcnui.tsx:78
**Export:** NativeStartNow

**Issue:** `NativeStartNow` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `NativeStartNow` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-start-now-shadcnui.tsx:78` and add its signature, its purpose and a usage example.

### GAP-192: Missing type: NativeStartNowProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** packages/components/react-shadcn/src/components/native/native-start-now-shadcnui.tsx:9
**Export:** NativeStartNowProps

**Issue:** the type `NativeStartNowProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `NativeStartNowProps` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-start-now-shadcnui.tsx:9` and list its fields or members.

### GAP-193: Missing export: NativeTabs

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/native/native-tabs-shadcnui.tsx:18
**Export:** NativeTabs

**Issue:** `NativeTabs` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `NativeTabs` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-tabs-shadcnui.tsx:18` and add its signature, its purpose and a usage example.

### GAP-194: Missing export: NativeTooltip

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/native/native-tooltip-shadcnui.tsx:92
**Export:** NativeTooltip

**Issue:** `NativeTooltip` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `NativeTooltip` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-tooltip-shadcnui.tsx:92` and add its signature, its purpose and a usage example.

### GAP-195: Missing export: NativeTooltipContent

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/native/native-tooltip-shadcnui.tsx:93
**Export:** NativeTooltipContent

**Issue:** `NativeTooltipContent` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `NativeTooltipContent` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-tooltip-shadcnui.tsx:93` and add its signature, its purpose and a usage example.

### GAP-196: Missing export: NativeTooltipProvider

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/native/native-tooltip-shadcnui.tsx:94
**Export:** NativeTooltipProvider

**Issue:** `NativeTooltipProvider` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `NativeTooltipProvider` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-tooltip-shadcnui.tsx:94` and add its signature, its purpose and a usage example.

### GAP-197: Missing export: NativeTooltipTrigger

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/native/native-tooltip-shadcnui.tsx:95
**Export:** NativeTooltipTrigger

**Issue:** `NativeTooltipTrigger` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `NativeTooltipTrigger` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-tooltip-shadcnui.tsx:95` and add its signature, its purpose and a usage example.

### GAP-198: Missing export: NativeTypewriter

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/native/native-typewriter-shadcnui.tsx:43
**Export:** NativeTypewriter

**Issue:** `NativeTypewriter` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `NativeTypewriter` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-typewriter-shadcnui.tsx:43` and add its signature, its purpose and a usage example.

### GAP-199: Missing export: NativeUserCard

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/native/native-user-card-shadcnui.tsx:19
**Export:** NativeUserCard

**Issue:** `NativeUserCard` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `NativeUserCard` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-user-card-shadcnui.tsx:19` and add its signature, its purpose and a usage example.

### GAP-200: Missing export: NewHeroSection

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/new-hero-section.tsx:7
**Export:** NewHeroSection

**Issue:** `NewHeroSection` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `NewHeroSection` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/new-hero-section.tsx:7` and add its signature, its purpose and a usage example.

### GAP-201: Missing export: NewsFeed

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/news-feed/news-feed.tsx:243
**Export:** NewsFeed

**Issue:** `NewsFeed` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `NewsFeed` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/news-feed/news-feed.tsx:243` and add its signature, its purpose and a usage example.

### GAP-202: Missing export: NewsletterSignupBlock

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/newsletter-signup-block.tsx:11
**Export:** NewsletterSignupBlock

**Issue:** `NewsletterSignupBlock` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `NewsletterSignupBlock` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/newsletter-signup-block.tsx:11` and add its signature, its purpose and a usage example.

### GAP-203: Missing type: NotchPosition

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** packages/components/react-shadcn/src/components/native/native-notch-shadcnui.tsx:24
**Export:** NotchPosition

**Issue:** the type `NotchPosition` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `NotchPosition` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-notch-shadcnui.tsx:24` and list its fields or members.

### GAP-204: Missing type: NotchSize

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** packages/components/react-shadcn/src/components/native/native-notch-shadcnui.tsx:19
**Export:** NotchSize

**Issue:** the type `NotchSize` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `NotchSize` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-notch-shadcnui.tsx:19` and list its fields or members.

### GAP-205: Missing export: NotificationCenter

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/notifications/notification-center.tsx:86
**Export:** NotificationCenter

**Issue:** `NotificationCenter` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `NotificationCenter` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/notifications/notification-center.tsx:86` and add its signature, its purpose and a usage example.

### GAP-206: Missing export: NotionBlogPage

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/notion-blog-page.tsx:62
**Export:** NotionBlogPage

**Issue:** `NotionBlogPage` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `NotionBlogPage` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/notion-blog-page.tsx:62` and add its signature, its purpose and a usage example.

### GAP-207: Missing export: OurPartnersSection

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/our-partners-section.tsx:15
**Export:** OurPartnersSection

**Issue:** `OurPartnersSection` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `OurPartnersSection` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/our-partners-section.tsx:15` and add its signature, its purpose and a usage example.

### GAP-208: Missing export: OurServicesSection

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/our-services-section.tsx:61
**Export:** OurServicesSection

**Issue:** `OurServicesSection` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `OurServicesSection` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/our-services-section.tsx:61` and add its signature, its purpose and a usage example.

### GAP-209: Missing export: PasswordInput

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/inputs/password-input.tsx:7
**Export:** PasswordInput

**Issue:** `PasswordInput` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `PasswordInput` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/inputs/password-input.tsx:7` and add its signature, its purpose and a usage example.

### GAP-210: Missing type: PasswordInputProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** packages/components/react-shadcn/src/ui/password-input.tsx:9
**Export:** PasswordInputProps

**Issue:** the type `PasswordInputProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `PasswordInputProps` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/password-input.tsx:9` and list its fields or members.

### GAP-211: Missing export: PresetsPanel

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/grid/presets-panel.tsx:12
**Export:** PresetsPanel

**Issue:** `PresetsPanel` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `PresetsPanel` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/grid/presets-panel.tsx:12` and add its signature, its purpose and a usage example.

### GAP-212: Missing export: PreviewDetailsCard

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/micro/links/preview-details-card.tsx:19
**Export:** PreviewDetailsCard

**Issue:** `PreviewDetailsCard` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `PreviewDetailsCard` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/micro/links/preview-details-card.tsx:19` and add its signature, its purpose and a usage example.

### GAP-213: Missing export: PricingSection

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/pricing-section.tsx:61
**Export:** PricingSection

**Issue:** `PricingSection` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `PricingSection` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/pricing-section.tsx:61` and add its signature, its purpose and a usage example.

### GAP-214: Missing export: ProfessionalResume

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/resumes/shadcnui/professional-resume.tsx:59
**Export:** ProfessionalResume

**Issue:** `ProfessionalResume` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `ProfessionalResume` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/resumes/shadcnui/professional-resume.tsx:59` and add its signature, its purpose and a usage example.

### GAP-215: Missing export: ProfilePage

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/profile/profile-page.tsx:16
**Export:** ProfilePage

**Issue:** `ProfilePage` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `ProfilePage` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/profile/profile-page.tsx:16` and add its signature, its purpose and a usage example.

### GAP-216: Missing export: ProjectCard

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/cards/shadcnui/project-card.tsx:31
**Export:** ProjectCard

**Issue:** `ProjectCard` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `ProjectCard` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/cards/shadcnui/project-card.tsx:31` and add its signature, its purpose and a usage example.

### GAP-217: Missing export: ProjectsBlock

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/projects-block.tsx:18
**Export:** ProjectsBlock

**Issue:** `ProjectsBlock` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `ProjectsBlock` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/projects-block.tsx:18` and add its signature, its purpose and a usage example.

### GAP-218: Missing export: ReactiveBackgroundGrid

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/motion-core/reactive-background-grid.tsx:11
**Export:** ReactiveBackgroundGrid

**Issue:** `ReactiveBackgroundGrid` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `ReactiveBackgroundGrid` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/motion-core/reactive-background-grid.tsx:11` and add its signature, its purpose and a usage example.

### GAP-219: Missing export: ResumeCard

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/resumes/shadcnui/resume-card.tsx:138
**Export:** ResumeCard

**Issue:** `ResumeCard` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `ResumeCard` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/resumes/shadcnui/resume-card.tsx:138` and add its signature, its purpose and a usage example.

### GAP-220: Missing export: RippleClickButton

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/micro/buttons/ripple-click.tsx:12
**Export:** RippleClickButton

**Issue:** `RippleClickButton` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `RippleClickButton` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/micro/buttons/ripple-click.tsx:12` and add its signature, its purpose and a usage example.

### GAP-221: Missing export: ScaleHoverButton

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/micro/buttons/scale-hover.tsx:5
**Export:** ScaleHoverButton

**Issue:** `ScaleHoverButton` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `ScaleHoverButton` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/micro/buttons/scale-hover.tsx:5` and add its signature, its purpose and a usage example.

### GAP-222: Missing export: ScrollArea

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/scroll-area.tsx:32
**Export:** ScrollArea

**Issue:** `ScrollArea` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `ScrollArea` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/scroll-area.tsx:32` and add its signature, its purpose and a usage example.

### GAP-223: Missing export: ScrollBar

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/scroll-area.tsx:32
**Export:** ScrollBar

**Issue:** `ScrollBar` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `ScrollBar` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/scroll-area.tsx:32` and add its signature, its purpose and a usage example.

### GAP-224: Missing export: ScrollProgressTracker

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/motion-core/scroll-progress-tracker.tsx:11
**Export:** ScrollProgressTracker

**Issue:** `ScrollProgressTracker` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `ScrollProgressTracker` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/motion-core/scroll-progress-tracker.tsx:11` and add its signature, its purpose and a usage example.

### GAP-225: Missing export: ScrollReveal

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/scroll-reveal.tsx:47
**Export:** ScrollReveal

**Issue:** `ScrollReveal` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `ScrollReveal` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/scroll-reveal.tsx:47` and add its signature, its purpose and a usage example.

### GAP-226: Missing export: Select

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/select.tsx:175
**Export:** Select

**Issue:** `Select` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `Select` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/select.tsx:175` and add its signature, its purpose and a usage example.

### GAP-227: Missing export: SelectContent

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/select.tsx:176
**Export:** SelectContent

**Issue:** `SelectContent` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `SelectContent` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/select.tsx:176` and add its signature, its purpose and a usage example.

### GAP-228: Missing export: SelectGroup

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/select.tsx:177
**Export:** SelectGroup

**Issue:** `SelectGroup` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `SelectGroup` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/select.tsx:177` and add its signature, its purpose and a usage example.

### GAP-229: Missing export: SelectItem

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/select.tsx:178
**Export:** SelectItem

**Issue:** `SelectItem` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `SelectItem` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/select.tsx:178` and add its signature, its purpose and a usage example.

### GAP-230: Missing export: SelectLabel

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/select.tsx:179
**Export:** SelectLabel

**Issue:** `SelectLabel` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `SelectLabel` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/select.tsx:179` and add its signature, its purpose and a usage example.

### GAP-231: Missing export: SelectScrollDownButton

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/select.tsx:180
**Export:** SelectScrollDownButton

**Issue:** `SelectScrollDownButton` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `SelectScrollDownButton` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/select.tsx:180` and add its signature, its purpose and a usage example.

### GAP-232: Missing export: SelectScrollUpButton

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/select.tsx:181
**Export:** SelectScrollUpButton

**Issue:** `SelectScrollUpButton` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `SelectScrollUpButton` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/select.tsx:181` and add its signature, its purpose and a usage example.

### GAP-233: Missing export: SelectSeparator

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/select.tsx:182
**Export:** SelectSeparator

**Issue:** `SelectSeparator` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `SelectSeparator` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/select.tsx:182` and add its signature, its purpose and a usage example.

### GAP-234: Missing export: SelectTrigger

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/select.tsx:183
**Export:** SelectTrigger

**Issue:** `SelectTrigger` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `SelectTrigger` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/select.tsx:183` and add its signature, its purpose and a usage example.

### GAP-235: Missing export: SelectValue

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/select.tsx:184
**Export:** SelectValue

**Issue:** `SelectValue` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `SelectValue` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/select.tsx:184` and add its signature, its purpose and a usage example.

### GAP-236: Missing export: Separator

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/separator.tsx:31
**Export:** Separator

**Issue:** `Separator` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `Separator` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/separator.tsx:31` and add its signature, its purpose and a usage example.

### GAP-237: Missing export: ServicesGridBlock

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/services-grid-block.tsx:92
**Export:** ServicesGridBlock

**Issue:** `ServicesGridBlock` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `ServicesGridBlock` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/services-grid-block.tsx:92` and add its signature, its purpose and a usage example.

### GAP-238: Missing export: SettingsPanel

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/grid/settings-panel.tsx:15
**Export:** SettingsPanel

**Issue:** `SettingsPanel` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `SettingsPanel` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/grid/settings-panel.tsx:15` and add its signature, its purpose and a usage example.

### GAP-239: Missing export: ShimmerButton

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/micro/buttons/shimmer-button.tsx:6
**Export:** ShimmerButton

**Issue:** `ShimmerButton` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `ShimmerButton` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/micro/buttons/shimmer-button.tsx:6` and add its signature, its purpose and a usage example.

### GAP-240: Missing export: SimpleCalendar

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/forms/simple-calendar.tsx:10
**Export:** SimpleCalendar

**Issue:** `SimpleCalendar` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `SimpleCalendar` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/forms/simple-calendar.tsx:10` and add its signature, its purpose and a usage example.

### GAP-241: Missing export: Slider

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/slider.tsx:28
**Export:** Slider

**Issue:** `Slider` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `Slider` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/slider.tsx:28` and add its signature, its purpose and a usage example.

### GAP-242: Missing export: SmartHoverCard

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/motion-core/smart-hover-card.tsx:14
**Export:** SmartHoverCard

**Issue:** `SmartHoverCard` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `SmartHoverCard` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/motion-core/smart-hover-card.tsx:14` and add its signature, its purpose and a usage example.

### GAP-243: Missing type: SocialAnimation

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** packages/components/react-shadcn/src/components/native/social-login-button-shadcnui.tsx:8
**Export:** SocialAnimation

**Issue:** the type `SocialAnimation` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SocialAnimation` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/social-login-button-shadcnui.tsx:8` and list its fields or members.

### GAP-244: Missing export: SocialLoginButton

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/native/social-login-button-shadcnui.tsx:127
**Export:** SocialLoginButton

**Issue:** `SocialLoginButton` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `SocialLoginButton` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/social-login-button-shadcnui.tsx:127` and add its signature, its purpose and a usage example.

### GAP-245: Missing type: SocialLoginButtonProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** packages/components/react-shadcn/src/components/native/social-login-button-shadcnui.tsx:10
**Export:** SocialLoginButtonProps

**Issue:** the type `SocialLoginButtonProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SocialLoginButtonProps` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/social-login-button-shadcnui.tsx:10` and list its fields or members.

### GAP-246: Missing type: SocialProvider

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** packages/components/react-shadcn/src/components/native/social-login-button-shadcnui.tsx:7
**Export:** SocialProvider

**Issue:** the type `SocialProvider` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `SocialProvider` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/social-login-button-shadcnui.tsx:7` and list its fields or members.

### GAP-247: Missing export: SpotlightSection

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/motion-core/spotlight-section.tsx:12
**Export:** SpotlightSection

**Issue:** `SpotlightSection` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `SpotlightSection` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/motion-core/spotlight-section.tsx:12` and add its signature, its purpose and a usage example.

### GAP-248: Missing export: StackedCardCarousel

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/motion-core/stacked-card-carousel.tsx:17
**Export:** StackedCardCarousel

**Issue:** `StackedCardCarousel` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `StackedCardCarousel` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/motion-core/stacked-card-carousel.tsx:17` and add its signature, its purpose and a usage example.

### GAP-249: Missing export: StaggeredDropdown

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/dropdown/staggered-items.tsx:9
**Export:** StaggeredDropdown

**Issue:** `StaggeredDropdown` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `StaggeredDropdown` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/dropdown/staggered-items.tsx:9` and add its signature, its purpose and a usage example.

### GAP-250: Missing export: StaggeredHero

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/page/hero/staggered-text.tsx:30
**Export:** StaggeredHero

**Issue:** `StaggeredHero` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `StaggeredHero` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/page/hero/staggered-text.tsx:30` and add its signature, its purpose and a usage example.

### GAP-251: Missing export: StandardResume

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/resumes/shadcnui/standard-resume.tsx:98
**Export:** StandardResume

**Issue:** `StandardResume` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `StandardResume` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/resumes/shadcnui/standard-resume.tsx:98` and add its signature, its purpose and a usage example.

### GAP-252: Missing export: StatsCounterBlock

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/stats-counter-block.tsx:82
**Export:** StatsCounterBlock

**Issue:** `StatsCounterBlock` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `StatsCounterBlock` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/stats-counter-block.tsx:82` and add its signature, its purpose and a usage example.

### GAP-253: Missing export: StatsSection

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/stats-section.tsx:40
**Export:** StatsSection

**Issue:** `StatsSection` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `StatsSection` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/stats-section.tsx:40` and add its signature, its purpose and a usage example.

### GAP-254: Missing export: StocksDashboard

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/stocks-dashboard/stocks-dashboard.tsx:454
**Export:** StocksDashboard

**Issue:** `StocksDashboard` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `StocksDashboard` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/stocks-dashboard/stocks-dashboard.tsx:454` and add its signature, its purpose and a usage example.

### GAP-255: Missing export: Switch

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/switch.tsx:29
**Export:** Switch

**Issue:** `Switch` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `Switch` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/switch.tsx:29` and add its signature, its purpose and a usage example.

### GAP-256: Missing export: SyncedLyricCaptions

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/motion-core/synced-lyric-captions.tsx:66
**Export:** SyncedLyricCaptions

**Issue:** `SyncedLyricCaptions` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `SyncedLyricCaptions` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/motion-core/synced-lyric-captions.tsx:66` and add its signature, its purpose and a usage example.

### GAP-257: Missing export: Tabs

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/tabs.tsx:54
**Export:** Tabs

**Issue:** `Tabs` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `Tabs` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/tabs.tsx:54` and add its signature, its purpose and a usage example.

### GAP-258: Missing export: TabsContent

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/tabs.tsx:54
**Export:** TabsContent

**Issue:** `TabsContent` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `TabsContent` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/tabs.tsx:54` and add its signature, its purpose and a usage example.

### GAP-259: Missing export: TabsList

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/tabs.tsx:54
**Export:** TabsList

**Issue:** `TabsList` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `TabsList` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/tabs.tsx:54` and add its signature, its purpose and a usage example.

### GAP-260: Missing export: TabsTrigger

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/tabs.tsx:54
**Export:** TabsTrigger

**Issue:** `TabsTrigger` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `TabsTrigger` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/tabs.tsx:54` and add its signature, its purpose and a usage example.

### GAP-261: Missing export: TeamSectionBlock

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/team-section-block.tsx:326
**Export:** TeamSectionBlock

**Issue:** `TeamSectionBlock` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `TeamSectionBlock` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/team-section-block.tsx:326` and add its signature, its purpose and a usage example.

### GAP-262: Missing export: TestimonialSection

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/testimonial-section.tsx:41
**Export:** TestimonialSection

**Issue:** `TestimonialSection` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `TestimonialSection` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/testimonial-section.tsx:41` and add its signature, its purpose and a usage example.

### GAP-263: Missing export: TestimonialsBlock

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/testimonials-block.tsx:55
**Export:** TestimonialsBlock

**Issue:** `TestimonialsBlock` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `TestimonialsBlock` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/testimonials-block.tsx:55` and add its signature, its purpose and a usage example.

### GAP-264: Missing export: Textarea

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/textarea.tsx:22
**Export:** Textarea

**Issue:** `Textarea` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `Textarea` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/textarea.tsx:22` and add its signature, its purpose and a usage example.

### GAP-265: Missing type: TextareaProps

**Severity:** Medium
**Category:** Coverage (missing-type)
**Source:** packages/components/react-shadcn/src/ui/textarea.tsx:4
**Export:** TextareaProps

**Issue:** the type `TextareaProps` is on the source API surface, and the skill does not document it

**Remediation:** Document the type `TextareaProps` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/textarea.tsx:4` and list its fields or members.

### GAP-266: Missing export: TheaterTicket

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/theater-ticket.tsx:7
**Export:** TheaterTicket

**Issue:** `TheaterTicket` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `TheaterTicket` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/theater-ticket.tsx:7` and add its signature, its purpose and a usage example.

### GAP-267: Missing export: TimelineBlock

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/sections/timeline-block.tsx:47
**Export:** TimelineBlock

**Issue:** `TimelineBlock` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `TimelineBlock` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/sections/timeline-block.tsx:47` and add its signature, its purpose and a usage example.

### GAP-268: Missing export: ToastNotification

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/page/notifications/toast-notification.tsx:9
**Export:** ToastNotification

**Issue:** `ToastNotification` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `ToastNotification` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/page/notifications/toast-notification.tsx:9` and add its signature, its purpose and a usage example.

### GAP-269: Missing export: Tooltip

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/tooltip.tsx:32
**Export:** Tooltip

**Issue:** `Tooltip` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `Tooltip` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/tooltip.tsx:32` and add its signature, its purpose and a usage example.

### GAP-270: Missing export: TooltipContent

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/tooltip.tsx:32
**Export:** TooltipContent

**Issue:** `TooltipContent` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `TooltipContent` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/tooltip.tsx:32` and add its signature, its purpose and a usage example.

### GAP-271: Missing export: TooltipProvider

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/tooltip.tsx:32
**Export:** TooltipProvider

**Issue:** `TooltipProvider` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `TooltipProvider` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/tooltip.tsx:32` and add its signature, its purpose and a usage example.

### GAP-272: Missing export: TooltipTrigger

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/tooltip.tsx:32
**Export:** TooltipTrigger

**Issue:** `TooltipTrigger` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `TooltipTrigger` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/tooltip.tsx:32` and add its signature, its purpose and a usage example.

### GAP-273: Missing export: TweetCard

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/cards/tweet-card.tsx:17
**Export:** TweetCard

**Issue:** `TweetCard` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `TweetCard` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/cards/tweet-card.tsx:17` and add its signature, its purpose and a usage example.

### GAP-274: Missing export: VerifiedBadge

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/native/native-verified-badge-shadcnui.tsx:104
**Export:** VerifiedBadge

**Issue:** `VerifiedBadge` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `VerifiedBadge` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-verified-badge-shadcnui.tsx:104` and add its signature, its purpose and a usage example.

### GAP-275: Missing export: VerifiedBadgeOutline

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/native/native-verified-badge-shadcnui.tsx:162
**Export:** VerifiedBadgeOutline

**Issue:** `VerifiedBadgeOutline` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `VerifiedBadgeOutline` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-verified-badge-shadcnui.tsx:162` and add its signature, its purpose and a usage example.

### GAP-276: Missing export: VerifiedShieldBadge

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/native/native-verified-badge-shadcnui.tsx:247
**Export:** VerifiedShieldBadge

**Issue:** `VerifiedShieldBadge` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `VerifiedShieldBadge` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/native/native-verified-badge-shadcnui.tsx:247` and add its signature, its purpose and a usage example.

### GAP-277: Missing export: VolumeComponent

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/sliders/volume-component.tsx:17
**Export:** VolumeComponent

**Issue:** `VolumeComponent` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `VolumeComponent` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/sliders/volume-component.tsx:17` and add its signature, its purpose and a usage example.

### GAP-278: Missing export: WeatherDashboard

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/components/weather/weather-dashboard.tsx:390
**Export:** WeatherDashboard

**Issue:** `WeatherDashboard` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `WeatherDashboard` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/components/weather/weather-dashboard.tsx:390` and add its signature, its purpose and a usage example.

### GAP-279: Missing export: WebPerformancePage

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/web-performance/web-performance-page.tsx:394
**Export:** WebPerformancePage

**Issue:** `WebPerformancePage` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `WebPerformancePage` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/web-performance/web-performance-page.tsx:394` and add its signature, its purpose and a usage example.

### GAP-280: Missing export: WizardForm

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/components/forms/wizard-form.tsx:165
**Export:** WizardForm

**Issue:** `WizardForm` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `WizardForm` in SKILL.md: read its definition at `packages/components/react-shadcn/src/components/forms/wizard-form.tsx:165` and add its signature, its purpose and a usage example.

### GAP-281: Missing export: badgeVariants

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/badge.tsx:34
**Export:** badgeVariants

**Issue:** `badgeVariants` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `badgeVariants` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/badge.tsx:34` and add its signature, its purpose and a usage example.

### GAP-282: Missing export: bentoPresets

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/lib/grid-presets.ts:7
**Export:** bentoPresets

**Issue:** `bentoPresets` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `bentoPresets` in SKILL.md: read its definition at `packages/components/react-shadcn/src/lib/grid-presets.ts:7` and add its signature, its purpose and a usage example.

### GAP-283: Missing export: buttonVariants

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/components/react-shadcn/src/ui/button.tsx:55
**Export:** buttonVariants

**Issue:** `buttonVariants` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `buttonVariants` in SKILL.md: read its definition at `packages/components/react-shadcn/src/ui/button.tsx:55` and add its signature, its purpose and a usage example.

### GAP-284: Missing export: componentsRegistry

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/registry/src/index.tsx:8
**Export:** componentsRegistry

**Issue:** `componentsRegistry` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `componentsRegistry` in SKILL.md: read its definition at `packages/registry/src/index.tsx:8` and add its signature, its purpose and a usage example.

### GAP-285: Missing export: nativeComponents

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/registry/src/registry/native.tsx:218
**Export:** nativeComponents

**Issue:** `nativeComponents` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `nativeComponents` in SKILL.md: read its definition at `packages/registry/src/registry/native.tsx:218` and add its signature, its purpose and a usage example.

### GAP-286: Missing export: uiComponents

**Severity:** Medium
**Category:** Coverage (missing-export)
**Source:** packages/registry/src/registry/ui.tsx:179
**Export:** uiComponents

**Issue:** `uiComponents` is on the source API surface, and SKILL.md and references/ do not document it

**Remediation:** Document `uiComponents` in SKILL.md: read its definition at `packages/registry/src/registry/ui.tsx:179` and add its signature, its purpose and a usage example.

### GAP-287: Stale documentation: RegistryItemType

**Severity:** Medium
**Category:** Coverage (stale-documentation)
**Source:** SKILL.md:139
**Export:** RegistryItemType

**Issue:** SKILL.md documents `RegistryItemType`, which the enumerated source API surface lacks

**Remediation:** Check `RegistryItemType` against the source and update or remove its documentation at SKILL.md:139: the enumerated source surface does not export it.

### GAP-291: denominator inflation: coarse scope.include union exceeds authored surface

**Severity:** Medium
**Category:** Coverage (denominator-inflation)
**Source:** forge-data/oms-uitripled/skill-brief.yaml

**Issue:** the `scope.include` union counts 327 exports, 1208.0% above the 25 provenance entries, and the brief has no `scope.tier_a_include`

**Remediation:** Set `stats.effective_denominator` in `skills/oms-uitripled/0.1.0/oms-uitripled/metadata.json` to the authored surface: the root barrel is an umbrella of re-exports, so a `scope.tier_a_include` glob would still count them.

### GAP-292: stale brief scope: scope.include globs match no source file

**Severity:** Medium
**Category:** Coverage (brief-scope-stale)
**Source:** forge-data/oms-uitripled/skill-brief.yaml

**Issue:** the `scope.include` globs `apps/docs/app/**/page.mdx`, `apps/docs/components/demos/**` match no file in the source tested; no root export was restored

**Remediation:** Edit `scope.include` in `forge-data/oms-uitripled/skill-brief.yaml` by hand so each glob matches the files it meant in this version of the source (update-skill does not rewrite an include glob), and add to `scope.exclude` any restored file the brief meant to leave out.

### GAP-293: metadata drift — documented-surface export counts diverge

**Severity:** Medium
**Category:** Coverage (metadata-drift)
**Source:** skills/oms-uitripled/0.1.0/oms-uitripled/metadata.json

**Issue:** stats.exports_documented=11, provenance named-exports=25, confidence_distribution sum=345 → 97% drift

**Remediation:** Recount the exports and correct the diverging counts in `skills/oms-uitripled/0.1.0/oms-uitripled/metadata.json`; update-skill applies it as a metadata update.

### GAP-299: naive-coherence: exported function `fetchComponent` is not referenced in any usage-family section or reference file

**Severity:** Medium
**Category:** Structural (structural)
**Source:** SKILL.md
**Export:** fetchComponent

**Remediation:** Add an example that calls `fetchComponent` to SKILL.md's usage section (or to a references/ file for a split body).

### GAP-295: Provenance line is not the definition of Component

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** packages/utils/src/types.ts:25
**Export:** Component

**Issue:** the provenance map records `Component` at `packages/utils/src/types.ts:25`, which is not the line that defines it; the lines that define it are 24.

**Remediation:** Set the provenance `source_line` of `Component` in `packages/utils/src/types.ts` to its definition line (24) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-296: Provenance line is not the definition of ThemeProvider

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** packages/components/react-shadcn/src/components/theme-provider.tsx:17
**Export:** ThemeProvider

**Issue:** the provenance map records `ThemeProvider` at `packages/components/react-shadcn/src/components/theme-provider.tsx:17`, which is not the line that defines it; the lines that define it are 18.

**Remediation:** Set the provenance `source_line` of `ThemeProvider` in `packages/components/react-shadcn/src/components/theme-provider.tsx` to its definition line (18) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-297: Provenance line is not the definition of UILibraryProvider

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** packages/components/react-shadcn/src/ui-library-provider.tsx:32
**Export:** UILibraryProvider

**Issue:** the provenance map records `UILibraryProvider` at `packages/components/react-shadcn/src/ui-library-provider.tsx:32`, which is not the line that defines it; the lines that define it are 31.

**Remediation:** Set the provenance `source_line` of `UILibraryProvider` in `packages/components/react-shadcn/src/ui-library-provider.tsx` to its definition line (31) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-298: Provenance line is not the definition of useTheme

**Severity:** Low
**Category:** Coverage (provenance-line)
**Source:** packages/components/react-shadcn/src/components/theme-provider.tsx:37
**Export:** useTheme

**Issue:** the provenance map records `useTheme` at `packages/components/react-shadcn/src/components/theme-provider.tsx:37`, which is not the line that defines it; the lines that define it are 35.

**Remediation:** Set the provenance `source_line` of `useTheme` in `packages/components/react-shadcn/src/components/theme-provider.tsx` to its definition line (35) and move its citations to that line; update-skill `--from-test-report` applies this when the file defines it on one line.

### GAP-288: Documented extra: UILibraryContextValue

**Severity:** Info
**Category:** Structural (observation)
**Source:** packages/components/react-shadcn/src/ui-library-provider.tsx:14
**Export:** UILibraryContextValue

**Issue:** `references/setup.md:90` documents `UILibraryContextValue`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `UILibraryContextValue` is a documented extra, a name the source still declares at `packages/components/react-shadcn/src/ui-library-provider.tsx:14` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-289: Documented extra: add

**Severity:** Info
**Category:** Structural (observation)
**Source:** packages/uitripled/src/commands/add.ts:8
**Export:** add

**Issue:** `SKILL.md:7` documents `add`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `add` is a documented extra, a name the source still declares at `packages/uitripled/src/commands/add.ts:8` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-290: Documented extra: fetchComponent

**Severity:** Info
**Category:** Structural (observation)
**Source:** packages/uitripled/src/utils/registry.ts:5
**Export:** fetchComponent

**Issue:** `SKILL.md:183` documents `fetchComponent`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `fetchComponent` is a documented extra, a name the source still declares at `packages/uitripled/src/utils/registry.ts:5` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-294: multi-denominator reporting — barrel vs documented surface

**Severity:** Info
**Category:** Coverage (multi-denominator)
**Source:** skills/oms-uitripled/0.1.0/oms-uitripled/metadata.json

**Issue:** barrel=11, documented=345

**Remediation:** No action required: the barrel and the documented surface measure different sets by design, and the report records both counts.

### GAP-300: Dangling pointer: NativeHoverCardProps in references/types.md

**Severity:** Info
**Category:** Structural (observation)
**Source:** SKILL.md:147
**Export:** NativeHoverCardProps

**Issue:** SKILL.md says NativeHoverCardProps is documented in references/types.md, which has no NativeHoverCardProps entry

**Remediation:** Add a `NativeHoverCardProps` section to `references/types.md` from its declaration at `packages/components/react-shadcn/src/components/native/native-hover-card-shadcnui.tsx:9` (imageSrc, imageAlt?, name, username?, size?: "sm" | "md" | "lg" | "xl", ...), or drop the claim from SKILL.md:147.

### GAP-301: Dangling pointer: CLI notes and fetchComponent in references/catalog.md

**Severity:** Info
**Category:** Structural (observation)
**Source:** SKILL.md:183
**Export:** fetchComponent

**Issue:** SKILL.md says the standalone CLI implementation notes and the fetchComponent helper are in references/catalog.md; catalog.md documents neither

**Remediation:** Point SKILL.md:183 at `references/integration.md` (where the CLI comparison lives) or add a CLI section to `references/catalog.md` documenting `add(componentName: string | undefined, options: { overwrite: boolean })` (`packages/uitripled/src/commands/add.ts:8`) and `fetchComponent(componentName: string)` (`packages/uitripled/src/utils/registry.ts:5`).

### GAP-302: Dangling pointer: Registry schema table in SKILL.md

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/types.md:191

**Issue:** references/types.md points to a SKILL.md "Full API Reference -> Registry schema" table that SKILL.md does not have

**Remediation:** Add the registry.json entry schema (`name`, `type`, `registryDependencies`, `dependencies`, `files`, `category`, `subcategory`) to `references/types.md:191` from `packages/registry/registry.json`, or remove the pointer to SKILL.md.

### GAP-303: Inaccurate claim: react-shadcn lib/utils.ts cn is identical and standalone

**Severity:** Info
**Category:** Structural (observation)
**Source:** references/utils.md:35
**Export:** cn

**Issue:** references/utils.md calls packages/components/react-shadcn/src/lib/utils.ts an identical implementation that removes the need for @uitripled/utils; that file is a wrapper `cn(...inputs: any[])` importing `cn as baseCn` from @uitripled/utils

**Remediation:** Reword `references/utils.md:35`: the react-shadcn copy at `packages/components/react-shadcn/src/lib/utils.ts:1-4` is a wrapper `cn(...inputs: any[])` that imports `cn` from `@uitripled/utils`, not an identical standalone implementation.

### Discovery Quality

**Discovery Test:** not run: the hard gate blocked the run
