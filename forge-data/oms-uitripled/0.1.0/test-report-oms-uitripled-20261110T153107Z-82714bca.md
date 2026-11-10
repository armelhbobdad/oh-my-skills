---
workflowType: 'test-skill'
skillName: 'oms-uitripled'
skillDir: 'skills/oms-uitripled/0.1.0/oms-uitripled'
runId: '20261110T153107Z-82714bca'
testMode: 'naive'
forgeTier: 'Deep'
hardGate: 'passed'
testResult: 'pass'
score: '100%'
threshold: '80%'
thresholdSource: 'workflow default (80%)'
analysisConfidence: 'full'
toolingStatus: 'ok'
workspaceDrift: 'ok'
health_check_dispatched: true
testDate: '2026-11-10T15:31:07Z'
stepsCompleted: ['init', 'detect-mode', 'coverage-check', 'coherence-check', 'external-validators', 'hard-gate', 'score', 'report']
nextWorkflow: 'export-skill'
---

# Test Report: oms-uitripled

<!--
Each stage writes its section in place of the heading below that it owns and
the placeholder comment under that heading, so every heading occurs once.
Before the result files are written, report.md §4c checks that each heading
occurs exactly once, that no placeholder comment is left and that the title
above names the skill (init.md §6c fills it): a stage that skipped its
section stops the run there. Do not change the title line, and do not
reorder or delete the headings or their placeholder comments.

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

**Mode Rationale:** metadata.json sets `skill_type: 'single'`, so this is an individual skill: naive mode checks API-surface coverage, coherence stays structural and is not scored.

**Analysis Plan:**
- Coverage Check: every documented export in SKILL.md and references/ against the pinned source (a5ffb45) of the uitripled workspace clone; at Deep tier, signatures and types are checked with AST-backed reads of the source.
- Coherence Check: structural only (naive mode): internal references and links resolve, the reference files named by SKILL.md exist; no coherence category in the score.

## Coverage Analysis

**Tier:** Deep
**Source Access:** full
**Source Path:** /home/armel/.skf/workspace/repos/github.com/moumen-soliman/uitripled
**Workspace Layout:** pnpm-workspaces
**Denominator:** Stratified scope, denominator: effective_denominator (216 files define its names, 327 exports union)

**Denominator Candidates** (stratified-scope audit trail):
- `stats.effective_denominator`: 327  ← chosen on the scalar branch
- `scope.tier_a_include` union: absent
- `scope.include` union: 327
- exports-map subpath union: 426
- root barrel: 29                               (secondary candidate: root-barrel-vs-subpath-union audit)

**Files Analyzed:** 216

### Export Coverage

| Export | Type | Documented | Signature | Source Location | Status |
|--------|------|------------|-----------|-----------------|--------|
| `AIChatInterface` | function | yes | yes | packages/components/react-shadcn/src/components/components/chat/ai-chat-interface.tsx:54 | PASS |
| `AIGlowInput` | function | yes | yes | packages/components/react-shadcn/src/components/motion-core/ai-glow-input.tsx:25 | PASS |
| `AILoadingSkeleton` | function | yes | yes | packages/components/react-shadcn/src/components/motion-core/ai-loading-skeleton.tsx:41 | PASS |
| `AIResponseTyping` | function | yes | yes | packages/components/react-shadcn/src/components/motion-core/ai-response-typing.tsx:14 | PASS |
| `AIUnlockAnimation` | function | yes | yes | packages/components/react-shadcn/src/components/motion-core/ai-unlock-animation.tsx:10 | PASS |
| `AboutUsPage` | function | yes | yes | packages/components/react-shadcn/src/components/page/about/about-us-page.tsx:131 | PASS |
| `AboutUsSection` | function | yes | yes | packages/components/react-shadcn/src/components/sections/about-us-section.tsx:35 | PASS |
| `AnimatedAccordion` | function | yes | yes | packages/components/react-shadcn/src/components/disclosure/animated-accordion.tsx:25 | PASS |
| `AnimatedCardStack` | function | yes | yes | packages/components/react-shadcn/src/components/components/cards/shadcnui/animated-card-stack.tsx:18 | PASS |
| `AnimatedCheckbox` | function | yes | yes | packages/components/react-shadcn/src/components/forms/animated-checkbox.tsx:7 | PASS |
| `AnimatedDialog` | function | yes | yes | packages/components/react-shadcn/src/components/modals/animated-dialog.tsx:8 | PASS |
| `AnimatedList` | function | yes | yes | packages/components/react-shadcn/src/components/components/lists/animated-list.tsx:43 | PASS |
| `AnimatedNavbar` | function | yes | yes | packages/components/react-shadcn/src/components/navigation/animated-navbar.tsx:8 | PASS |
| `AnimatedPagination` | function | yes | yes | packages/components/react-shadcn/src/components/navigation/animated-pagination.tsx:7 | PASS |
| `AnimatedProfileMenu` | function | yes | yes | packages/components/react-shadcn/src/components/navigation/animated-profile-menu.tsx:74 | PASS |
| `AnimatedProgress` | function | yes | yes | packages/components/react-shadcn/src/components/data/progress/animated-progress.tsx:7 | PASS |
| `AnimatedQuoteBlock` | function | yes | yes | packages/components/react-shadcn/src/components/motion-core/animated-quote-block.tsx:12 | PASS |
| `AnimatedRadio` | function | yes | yes | packages/components/react-shadcn/src/components/forms/animated-radio.tsx:8 | PASS |
| `AnimatedSelect` | function | yes | yes | packages/components/react-shadcn/src/components/forms/animated-select.tsx:9 | PASS |
| `AnimatedSidebar` | function | yes | yes | packages/components/react-shadcn/src/components/navigation/animated-sidebar.tsx:14 | PASS |
| `AnimatedTabs` | function | yes | yes | packages/components/react-shadcn/src/components/components/tabs/animated-tabs.tsx:7 | PASS |
| `AnimatedTooltip` | function | yes | yes | packages/components/react-shadcn/src/components/tooltips/animated-tooltip.tsx:7 | PASS |
| `AutoRevealingHeading` | function | yes | yes | packages/components/react-shadcn/src/components/motion-core/auto-revealing-heading.tsx:13 | PASS |
| `Avatar` | const | yes | yes | packages/components/react-shadcn/src/ui/avatar.tsx:8 | PASS |
| `AvatarFallback` | const | yes | yes | packages/components/react-shadcn/src/ui/avatar.tsx:35 | PASS |
| `AvatarGroup` | function | yes | yes | packages/components/react-shadcn/src/components/avatars/avatar-group.tsx:27 | PASS |
| `AvatarImage` | const | yes | yes | packages/components/react-shadcn/src/ui/avatar.tsx:23 | PASS |
| `Badge` | function | yes | yes | packages/components/react-shadcn/src/ui/badge.tsx:28 | PASS |
| `BadgeProps` | interface | yes | - | packages/components/react-shadcn/src/ui/badge.tsx:24 | PASS |
| `BentoGridBlock` | function | yes | yes | packages/components/react-shadcn/src/components/sections/bento-grid-block.tsx:125 | PASS |
| `BentoPreset` | interface | yes | - | packages/components/react-shadcn/src/lib/grid-utils.ts:12 | PASS |
| `BlogBlock` | function | yes | yes | packages/components/react-shadcn/src/components/sections/blog-block.tsx:55 | PASS |
| `BlogTypography` | function | yes | yes | packages/components/react-shadcn/src/components/components/blog/blog-typography.tsx:132 | PASS |
| `BottomModal` | function | yes | yes | packages/components/react-shadcn/src/components/modals/bottom-modal.tsx:8 | PASS |
| `BrowseFolder` | function | yes | yes | packages/components/react-shadcn/src/components/sections/browse-folder.tsx:111 | PASS |
| `BuilderComponent` | type | yes | - | packages/utils/src/types.ts:57 | PASS |
| `BuilderProjectPage` | type | yes | - | packages/utils/src/types.ts:64 | PASS |
| `Button` | const | yes | - | packages/components/react-shadcn/src/ui/button.tsx:41 | PASS |
| `ButtonProps` | interface | yes | - | packages/components/react-shadcn/src/ui/button.tsx:35 | PASS |
| `CTABannerSection` | function | yes | yes | packages/components/react-shadcn/src/components/sections/cta-banner-section.tsx:35 | PASS |
| `CTABlock` | function | yes | yes | packages/components/react-shadcn/src/components/sections/cta-block.tsx:8 | PASS |
| `CTAHeroBlock` | function | yes | yes | packages/components/react-shadcn/src/components/sections/cta-hero-block.tsx:17 | PASS |
| `Card` | const | yes | - | packages/components/react-shadcn/src/ui/card.tsx:4 | PASS |
| `CardContent` | const | yes | - | packages/components/react-shadcn/src/ui/card.tsx:58 | PASS |
| `CardDescription` | const | yes | yes | packages/components/react-shadcn/src/ui/card.tsx:46 | PASS |
| `CardFooter` | const | yes | yes | packages/components/react-shadcn/src/ui/card.tsx:66 | PASS |
| `CardHeader` | const | yes | - | packages/components/react-shadcn/src/ui/card.tsx:19 | PASS |
| `CardTitle` | const | yes | yes | packages/components/react-shadcn/src/ui/card.tsx:31 | PASS |
| `CardsSlider` | function | yes | yes | packages/components/react-shadcn/src/components/components/sliders/cards-slider.tsx:87 | PASS |
| `CashFlowChart` | function | yes | yes | packages/components/react-shadcn/src/components/data/charts/cash-flow-chart.tsx:135 | PASS |
| `ChatApp` | function | yes | yes | packages/components/react-shadcn/src/components/components/chat/chat-app.tsx:39 | PASS |
| `Checkbox` | const | yes | yes | packages/components/react-shadcn/src/ui/checkbox.tsx:9 | PASS |
| `CinemaTicket` | function | yes | yes | packages/components/react-shadcn/src/components/sections/cinema-ticket.tsx:7 | PASS |
| `CodeOutput` | function | yes | yes | packages/components/react-shadcn/src/components/grid/code-output.tsx:14 | PASS |
| `CommandPalette` | function | yes | yes | packages/components/react-shadcn/src/components/search/command-palette.tsx:49 | PASS |
| `CommentThread` | function | yes | yes | packages/components/react-shadcn/src/components/components/comments/comment-thread.tsx:533 | PASS |
| `Component` | type | yes | - | packages/utils/src/types.ts:24 | PASS |
| `ComponentCategory` | type | yes | - | packages/utils/src/types.ts:12 | PASS |
| `ConferenceTicket` | function | yes | yes | packages/components/react-shadcn/src/components/sections/conference-ticket.tsx:8 | PASS |
| `ContactBlock` | function | yes | yes | packages/components/react-shadcn/src/components/sections/contact-block.tsx:32 | PASS |
| `ContactFormSection` | function | yes | yes | packages/components/react-shadcn/src/components/sections/contact-form-section.tsx:38 | PASS |
| `ContextMenu` | function | yes | yes | packages/components/react-shadcn/src/components/navigation/context-menu.tsx:14 | PASS |
| `ContextMenuBubble` | function | yes | yes | packages/components/react-shadcn/src/components/motion-core/context-menu-bubble.tsx:18 | PASS |
| `CourseContentPage` | function | yes | yes | packages/components/react-shadcn/src/components/components/course-content/course-content-page.tsx:786 | PASS |
| `CreditCard` | function | yes | yes | packages/components/react-shadcn/src/components/components/cards/shadcnui/credit-card.tsx:31 | PASS |
| `CurrencyConverterCard` | function | yes | yes | packages/components/react-shadcn/src/components/sections/currency-converter-card.tsx:41 | PASS |
| `DashboardPage` | function | yes | yes | packages/components/react-shadcn/src/components/components/stocks-dashboard/dashboard.tsx:605 | PASS |
| `DetailTaskCard` | function | yes | yes | packages/components/react-shadcn/src/components/components/cards/shadcnui/detail-task.tsx:115 | PASS |
| `Dialog` | const | yes | - | packages/components/react-shadcn/src/ui/dialog.tsx:9 | PASS |
| `DialogClose` | const | yes | yes | packages/components/react-shadcn/src/ui/dialog.tsx:15 | PASS |
| `DialogContent` | const | yes | - | packages/components/react-shadcn/src/ui/dialog.tsx:32 | PASS |
| `DialogDescription` | const | yes | yes | packages/components/react-shadcn/src/ui/dialog.tsx:99 | PASS |
| `DialogFooter` | function | yes | yes | packages/components/react-shadcn/src/ui/dialog.tsx:70 | PASS |
| `DialogHeader` | function | yes | yes | packages/components/react-shadcn/src/ui/dialog.tsx:56 | PASS |
| `DialogOverlay` | const | yes | yes | packages/components/react-shadcn/src/ui/dialog.tsx:17 | PASS |
| `DialogPortal` | const | yes | yes | packages/components/react-shadcn/src/ui/dialog.tsx:13 | PASS |
| `DialogTitle` | const | yes | yes | packages/components/react-shadcn/src/ui/dialog.tsx:84 | PASS |
| `DialogTrigger` | const | yes | yes | packages/components/react-shadcn/src/ui/dialog.tsx:11 | PASS |
| `DragToConfirmSlider` | function | yes | yes | packages/components/react-shadcn/src/components/motion-core/drag-to-confirm-slider.tsx:13 | PASS |
| `DraggableList` | function | yes | yes | packages/components/react-shadcn/src/components/components/lists/draggable-list.tsx:14 | PASS |
| `DropdownMenu` | const | yes | yes | packages/components/react-shadcn/src/ui/dropdown-menu.tsx:9 | PASS |
| `DropdownMenuCheckboxItem` | const | yes | yes | packages/components/react-shadcn/src/ui/dropdown-menu.tsx:95 | PASS |
| `DropdownMenuContent` | const | yes | yes | packages/components/react-shadcn/src/ui/dropdown-menu.tsx:59 | PASS |
| `DropdownMenuGroup` | const | yes | yes | packages/components/react-shadcn/src/ui/dropdown-menu.tsx:13 | PASS |
| `DropdownMenuItem` | const | yes | yes | packages/components/react-shadcn/src/ui/dropdown-menu.tsx:77 | PASS |
| `DropdownMenuLabel` | const | yes | yes | packages/components/react-shadcn/src/ui/dropdown-menu.tsx:141 | PASS |
| `DropdownMenuPortal` | const | yes | yes | packages/components/react-shadcn/src/ui/dropdown-menu.tsx:15 | PASS |
| `DropdownMenuRadioGroup` | const | yes | yes | packages/components/react-shadcn/src/ui/dropdown-menu.tsx:19 | PASS |
| `DropdownMenuRadioItem` | const | yes | yes | packages/components/react-shadcn/src/ui/dropdown-menu.tsx:119 | PASS |
| `DropdownMenuSeparator` | const | yes | yes | packages/components/react-shadcn/src/ui/dropdown-menu.tsx:159 | PASS |
| `DropdownMenuShortcut` | function | yes | yes | packages/components/react-shadcn/src/ui/dropdown-menu.tsx:171 | PASS |
| `DropdownMenuSub` | const | yes | yes | packages/components/react-shadcn/src/ui/dropdown-menu.tsx:17 | PASS |
| `DropdownMenuSubContent` | const | yes | yes | packages/components/react-shadcn/src/ui/dropdown-menu.tsx:43 | PASS |
| `DropdownMenuSubTrigger` | const | yes | yes | packages/components/react-shadcn/src/ui/dropdown-menu.tsx:21 | PASS |
| `DropdownMenuTrigger` | const | yes | yes | packages/components/react-shadcn/src/ui/dropdown-menu.tsx:11 | PASS |
| `DynamicSpotlightCTA` | function | yes | yes | packages/components/react-shadcn/src/components/motion-core/dynamic-spotlight-cta.tsx:22 | PASS |
| `DynamicTagCloud` | function | yes | yes | packages/components/react-shadcn/src/components/motion-core/dynamic-tag-cloud.tsx:15 | PASS |
| `EcommerceHighlightCard` | function | yes | yes | packages/components/react-shadcn/src/components/components/cards/shadcnui/ecommerce-highlight-card.tsx:64 | PASS |
| `ElasticSwitch` | function | yes | yes | packages/components/react-shadcn/src/components/micro/toggles/elastic-switch.tsx:6 | PASS |
| `ExpandingSearchDock` | function | yes | yes | packages/components/react-shadcn/src/components/motion-core/expanding-search-dock.tsx:12 | PASS |
| `FAQAccordionBlock` | function | yes | yes | packages/components/react-shadcn/src/components/sections/faq-accordion-block.tsx:43 | PASS |
| `FAQSection` | function | yes | yes | packages/components/react-shadcn/src/components/sections/faq-section.tsx:36 | PASS |
| `FadeSlideModal` | function | yes | yes | packages/components/react-shadcn/src/components/components/modal/fade-slide.tsx:7 | PASS |
| `FeatureCardsBlock` | function | yes | yes | packages/components/react-shadcn/src/components/sections/feature-cards-block.tsx:6 | PASS |
| `FeatureComparisonBlock` | function | yes | yes | packages/components/react-shadcn/src/components/sections/feature-comparison-block.tsx:90 | PASS |
| `FeatureGridSection` | function | yes | yes | packages/components/react-shadcn/src/components/sections/feature-grid-section.tsx:47 | PASS |
| `FloatingChatWidget` | function | yes | yes | packages/components/react-shadcn/src/components/components/chat/floating-chat-widget.tsx:112 | PASS |
| `FloatingGradient` | function | yes | yes | packages/components/react-shadcn/src/components/decorative/background/floating-gradient.tsx:5 | PASS |
| `FloatingInfoPanel` | function | yes | yes | packages/components/react-shadcn/src/components/motion-core/floating-info-panel.tsx:12 | PASS |
| `FloatingLabelInput` | function | yes | yes | packages/components/react-shadcn/src/components/components/inputs/floating-label-input.tsx:7 | PASS |
| `FluidModalTransition` | function | yes | yes | packages/components/react-shadcn/src/components/motion-core/fluid-modal-transition.tsx:13 | PASS |
| `FolderBrowser` | function | yes | yes | packages/components/react-shadcn/src/components/sections/browse-folder.tsx:21 | PASS |
| `FooterBlock` | function | yes | yes | packages/components/react-shadcn/src/components/sections/footer-block.tsx:47 | PASS |
| `GAP_VALUES` | const | yes | - | packages/components/react-shadcn/src/lib/grid-utils.ts:23 | PASS |
| `GalleryGridBlock` | function | yes | yes | packages/components/react-shadcn/src/components/sections/gallery-grid-block.tsx:49 | PASS |
| `GlassAccountSettingsCard` | function | yes | yes | packages/components/react-shadcn/src/components/components/forms/glass-account-settings.tsx:17 | PASS |
| `GlassBlogCard` | function | yes | yes | packages/components/react-shadcn/src/components/components/cards/shadcnui/glass-blog-card.tsx:39 | PASS |
| `GlassCheckoutCard` | function | yes | yes | packages/components/react-shadcn/src/components/components/cards/shadcnui/glass-checkout-card.tsx:17 | PASS |
| `GlassForgotPasswordCard` | function | yes | yes | packages/components/react-shadcn/src/components/components/forms/glass-forgot-password.tsx:9 | PASS |
| `GlassOrderSummary` | function | yes | yes | packages/components/react-shadcn/src/components/components/cards/shadcnui/glass-order-summary.tsx:49 | PASS |
| `GlassProfileSettingsCard` | function | yes | yes | packages/components/react-shadcn/src/components/components/forms/glass-profile-settings.tsx:14 | PASS |
| `GlassSignInCard` | function | yes | yes | packages/components/react-shadcn/src/components/components/forms/glass-sign-in.tsx:17 | PASS |
| `GlassSignUpCard` | function | yes | yes | packages/components/react-shadcn/src/components/components/forms/glass-sign-up.tsx:17 | PASS |
| `GlassVerificationCodeCard` | function | yes | yes | packages/components/react-shadcn/src/components/components/forms/glass-verification-code.tsx:10 | PASS |
| `GlassWalletCard` | function | yes | yes | packages/components/react-shadcn/src/components/components/cards/shadcnui/glass-wallet-card.tsx:36 | PASS |
| `GlassmorphismCTABlock` | function | yes | yes | packages/components/react-shadcn/src/components/sections/glassmorphism-cta-block.tsx:6 | PASS |
| `GlassmorphismHeroBlock` | function | yes | yes | packages/components/react-shadcn/src/components/sections/glassmorphism-hero-block.tsx:6 | PASS |
| `GlassmorphismLaunchTimelineBlock` | function | yes | yes | packages/components/react-shadcn/src/components/sections/glassmorphism-launch-timeline-block.tsx:65 | PASS |
| `GlassmorphismListenAppBlock` | function | yes | yes | packages/components/react-shadcn/src/components/sections/glassmorphism-listen-app-block.tsx:78 | PASS |
| `GlassmorphismLogoShowcaseBlock` | function | yes | yes | packages/components/react-shadcn/src/components/sections/glassmorphism-logo-showcase-block.tsx:26 | PASS |
| `GlassmorphismMinimalMetricsBlock` | function | yes | yes | packages/components/react-shadcn/src/components/sections/glassmorphism-minimal-metrics-block.tsx:42 | PASS |
| `GlassmorphismPortfolioBlock` | function | yes | yes | packages/components/react-shadcn/src/components/sections/glassmorphism-portfolio-block.tsx:95 | PASS |
| `GlassmorphismPricingBlock` | function | yes | yes | packages/components/react-shadcn/src/components/sections/glassmorphism-pricing-block.tsx:7 | PASS |
| `GlassmorphismProductUpdateBlock` | function | yes | yes | packages/components/react-shadcn/src/components/sections/glassmorphism-product-update-block.tsx:37 | PASS |
| `GlassmorphismStatisticsCard` | function | yes | yes | packages/components/react-shadcn/src/components/sections/glassmorphism-statistics-card.tsx:22 | PASS |
| `GlassmorphismTestimonialsBlock` | function | yes | yes | packages/components/react-shadcn/src/components/sections/glassmorphism-testimonials-block.tsx:6 | PASS |
| `GlowyWavesHero` | function | yes | yes | packages/components/react-shadcn/src/components/sections/glowy-waves-hero.tsx:61 | PASS |
| `GradientAnimation` | function | yes | yes | packages/components/react-shadcn/src/components/decorative/backgrounds/gradient-animation.tsx:5 | PASS |
| `GridCell` | function | yes | yes | packages/components/react-shadcn/src/components/grid/grid-cell.tsx:14 | PASS |
| `GridPreview` | function | yes | yes | packages/components/react-shadcn/src/components/grid/grid-preview.tsx:28 | PASS |
| `GridPreviewProps` | interface | yes | - | packages/components/react-shadcn/src/components/grid/grid-preview.tsx:10 | PASS |
| `HeartFavorite` | function | yes | yes | packages/components/react-shadcn/src/components/micro/icons/heart-favorite.tsx:7 | PASS |
| `HeroBlock` | function | yes | yes | packages/components/react-shadcn/src/components/sections/hero-block.tsx:7 | PASS |
| `HeroSection` | function | yes | yes | packages/components/react-shadcn/src/components/sections/hero-section.tsx:7 | PASS |
| `HolographicWall` | function | yes | yes | packages/components/react-shadcn/src/components/motion-core/holographic-wall.tsx:35 | PASS |
| `HoverExpandCard` | function | yes | yes | packages/components/react-shadcn/src/components/components/cards/shadcnui/hover-expand.tsx:6 | PASS |
| `ImageSliderCard` | function | yes | yes | packages/components/react-shadcn/src/components/components/cards/image-slider-card.tsx:43 | PASS |
| `Input` | const | yes | - | packages/components/react-shadcn/src/ui/input.tsx:6 | PASS |
| `InputProps` | type | yes | - | packages/components/react-shadcn/src/ui/input.tsx:4 | PASS |
| `InteractiveLogsTable` | function | yes | yes | packages/components/react-shadcn/src/components/sections/interactive-logs-table.tsx:398 | PASS |
| `InteractiveTimeline` | function | yes | yes | packages/components/react-shadcn/src/components/motion-core/interactive-timeline.tsx:64 | PASS |
| `KanbanBoard` | function | yes | yes | packages/components/react-shadcn/src/components/components/kanban/kanban-board.tsx:142 | PASS |
| `Label` | const | yes | yes | packages/components/react-shadcn/src/ui/label.tsx:6 | PASS |
| `LabelProps` | type | yes | - | packages/components/react-shadcn/src/ui/label.tsx:4 | PASS |
| `LikeUser` | interface | yes | - | packages/components/react-shadcn/src/components/native/native-likes-counter-shadcnui.tsx:9 | PASS |
| `LiquidCursor` | function | yes | yes | packages/components/react-shadcn/src/components/liquid-cursor.tsx:25 | PASS |
| `ListItem` | interface | yes | - | packages/components/react-shadcn/src/components/native/native-nested-list-shadcnui.tsx:11 | PASS |
| `MacSearchbar` | function | yes | yes | packages/components/react-shadcn/src/components/search/mac-searchbar.tsx:16 | PASS |
| `MagneticAvatarGroup` | function | yes | yes | packages/components/react-shadcn/src/components/motion-core/magnetic-avatar-group.tsx:18 | PASS |
| `Messenger` | function | yes | yes | packages/components/react-shadcn/src/components/components/chat/messenger.tsx:162 | PASS |
| `MinimalResume` | function | yes | yes | packages/components/react-shadcn/src/components/components/resumes/shadcnui/minimal-resume.tsx:83 | PASS |
| `MoodGradientButton` | function | yes | yes | packages/components/react-shadcn/src/components/motion-core/mood-gradient-button.tsx:12 | PASS |
| `MorphingButtonAction` | interface | yes | - | packages/components/react-shadcn/src/components/native/native-morphing-button-shadcnui.tsx:14 | PASS |
| `MultipleAccounts` | function | yes | yes | packages/components/react-shadcn/src/components/components/account-switcher/multiple-accounts.tsx:42 | PASS |
| `N8nWorkflowBlock` | function | yes | yes | packages/components/react-shadcn/src/components/sections/n8n-workflow-block.tsx:161 | PASS |
| `NativeAvatarExpand` | function | yes | yes | packages/components/react-shadcn/src/components/native/native-avatar-expand-shadcnui.tsx:55 | PASS |
| `NativeAvatarExpandProps` | interface | yes | - | packages/components/react-shadcn/src/components/native/native-avatar-expand-shadcnui.tsx:8 | PASS |
| `NativeAvatarProps` | interface | yes | - | packages/components/react-shadcn/src/components/native/native-avatar-with-name-shadcnui.tsx:8 | PASS |
| `NativeAvatarWithName` | function | yes | yes | packages/components/react-shadcn/src/components/native/native-avatar-with-name-shadcnui.tsx:59 | PASS |
| `NativeButton` | function | yes | yes | packages/components/react-shadcn/src/components/native/native-button-shadcnui.tsx:15 | PASS |
| `NativeButtonProps` | interface | yes | - | packages/components/react-shadcn/src/components/native/native-button-shadcnui.tsx:9 | PASS |
| `NativeCounterUp` | function | yes | yes | packages/components/react-shadcn/src/components/native/native-counter-up-shadcnui.tsx:42 | PASS |
| `NativeCounterUpProps` | interface | yes | - | packages/components/react-shadcn/src/components/native/native-counter-up-shadcnui.tsx:7 | PASS |
| `NativeDelete` | function | yes | yes | packages/components/react-shadcn/src/components/native/native-delete-shadcnui.tsx:73 | PASS |
| `NativeDeleteProps` | interface | yes | - | packages/components/react-shadcn/src/components/native/native-delete-shadcnui.tsx:9 | PASS |
| `NativeDialog` | const | yes | yes | packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:19 | PASS |
| `NativeDialogClose` | const | yes | yes | packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:25 | PASS |
| `NativeDialogContent` | const | yes | yes | packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:45 | PASS |
| `NativeDialogDescription` | const | yes | yes | packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:82 | PASS |
| `NativeDialogFooter` | const | yes | yes | packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:76 | PASS |
| `NativeDialogHeader` | const | yes | yes | packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:73 | PASS |
| `NativeDialogOverlay` | const | yes | yes | packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:27 | PASS |
| `NativeDialogPortal` | const | yes | yes | packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:23 | PASS |
| `NativeDialogTitle` | const | yes | yes | packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:79 | PASS |
| `NativeDialogTrigger` | const | yes | yes | packages/components/react-shadcn/src/components/native/native-dialog-shadcnui.tsx:21 | PASS |
| `NativeFlipText` | function | yes | yes | packages/components/react-shadcn/src/components/native/native-flip-text-shadcnui.tsx:20 | PASS |
| `NativeHoverCard` | function | yes | yes | packages/components/react-shadcn/src/components/native/native-hover-card-shadcnui.tsx:81 | PASS |
| `NativeHoverCardProps` | interface | yes | - | packages/components/react-shadcn/src/components/native/native-hover-card-shadcnui.tsx:9 | PASS |
| `NativeImageCheckbox` | function | yes | yes | packages/components/react-shadcn/src/components/native/native-image-checkbox-shadcnui.tsx:63 | PASS |
| `NativeImageCheckboxProps` | interface | yes | - | packages/components/react-shadcn/src/components/native/native-image-checkbox-shadcnui.tsx:8 | PASS |
| `NativeLikesCounter` | function | yes | yes | packages/components/react-shadcn/src/components/native/native-likes-counter-shadcnui.tsx:56 | PASS |
| `NativeLikesCounterProps` | interface | yes | - | packages/components/react-shadcn/src/components/native/native-likes-counter-shadcnui.tsx:15 | PASS |
| `NativeLiquidButton` | function | yes | yes | packages/components/react-shadcn/src/components/native/native-liquid-button-shadcnui.tsx:61 | PASS |
| `NativeLiquidButtonProps` | interface | yes | - | packages/components/react-shadcn/src/components/native/native-liquid-button-shadcnui.tsx:12 | PASS |
| `NativeMagnetic` | function | yes | yes | packages/components/react-shadcn/src/components/native/native-magnetic-shadcnui.tsx:61 | PASS |
| `NativeMagneticProps` | interface | yes | - | packages/components/react-shadcn/src/components/native/native-magnetic-shadcnui.tsx:14 | PASS |
| `NativeMorphingButton` | function | yes | yes | packages/components/react-shadcn/src/components/native/native-morphing-button-shadcnui.tsx:69 | PASS |
| `NativeMorphingButtonProps` | interface | yes | - | packages/components/react-shadcn/src/components/native/native-morphing-button-shadcnui.tsx:29 | PASS |
| `NativeNestedList` | function | yes | yes | packages/components/react-shadcn/src/components/native/native-nested-list-shadcnui.tsx:230 | PASS |
| `NativeNestedListProps` | interface | yes | - | packages/components/react-shadcn/src/components/native/native-nested-list-shadcnui.tsx:43 | PASS |
| `NativeNotch` | function | yes | yes | packages/components/react-shadcn/src/components/native/native-notch-shadcnui.tsx:106 | PASS |
| `NativeNotchProps` | interface | yes | - | packages/components/react-shadcn/src/components/native/native-notch-shadcnui.tsx:39 | PASS |
| `NativeNotificationBell` | function | yes | yes | packages/components/react-shadcn/src/components/native/native-notification-bell-shadcnui.tsx:68 | PASS |
| `NativeNotificationBellProps` | interface | yes | - | packages/components/react-shadcn/src/components/native/native-notification-bell-shadcnui.tsx:8 | PASS |
| `NativeProfileNotch` | function | yes | yes | packages/components/react-shadcn/src/components/native/native-profile-notch-shadcnui.tsx:44 | PASS |
| `NativeProfileNotchProps` | interface | yes | - | packages/components/react-shadcn/src/components/native/native-profile-notch-shadcnui.tsx:9 | PASS |
| `NativeStartNow` | function | yes | yes | packages/components/react-shadcn/src/components/native/native-start-now-shadcnui.tsx:78 | PASS |
| `NativeStartNowProps` | interface | yes | - | packages/components/react-shadcn/src/components/native/native-start-now-shadcnui.tsx:9 | PASS |
| `NativeTabs` | function | yes | yes | packages/components/react-shadcn/src/components/native/native-tabs-shadcnui.tsx:18 | PASS |
| `NativeTooltip` | function | yes | yes | packages/components/react-shadcn/src/components/native/native-tooltip-shadcnui.tsx:68 | PASS |
| `NativeTooltipContent` | const | yes | yes | packages/components/react-shadcn/src/components/native/native-tooltip-shadcnui.tsx:20 | PASS |
| `NativeTooltipProvider` | function | yes | yes | packages/components/react-shadcn/src/components/native/native-tooltip-shadcnui.tsx:9 | PASS |
| `NativeTooltipTrigger` | const | yes | yes | packages/components/react-shadcn/src/components/native/native-tooltip-shadcnui.tsx:18 | PASS |
| `NativeTypewriter` | function | yes | yes | packages/components/react-shadcn/src/components/native/native-typewriter-shadcnui.tsx:43 | PASS |
| `NativeUserCard` | function | yes | yes | packages/components/react-shadcn/src/components/native/native-user-card-shadcnui.tsx:19 | PASS |
| `NewHeroSection` | function | yes | yes | packages/components/react-shadcn/src/components/sections/new-hero-section.tsx:7 | PASS |
| `NewsFeed` | function | yes | yes | packages/components/react-shadcn/src/components/components/news-feed/news-feed.tsx:243 | PASS |
| `NewsletterSignupBlock` | function | yes | yes | packages/components/react-shadcn/src/components/sections/newsletter-signup-block.tsx:11 | PASS |
| `NotchPosition` | interface | yes | - | packages/components/react-shadcn/src/components/native/native-notch-shadcnui.tsx:24 | PASS |
| `NotchSize` | type | yes | - | packages/components/react-shadcn/src/components/native/native-notch-shadcnui.tsx:19 | PASS |
| `NotificationCenter` | function | yes | yes | packages/components/react-shadcn/src/components/components/notifications/notification-center.tsx:86 | PASS |
| `NotionBlogPage` | function | yes | yes | packages/components/react-shadcn/src/components/sections/notion-blog-page.tsx:62 | PASS |
| `OurPartnersSection` | function | yes | yes | packages/components/react-shadcn/src/components/sections/our-partners-section.tsx:15 | PASS |
| `OurServicesSection` | function | yes | yes | packages/components/react-shadcn/src/components/sections/our-services-section.tsx:61 | PASS |
| `PasswordInput` | function | yes | yes | packages/components/react-shadcn/src/components/inputs/password-input.tsx:7 | PASS |
| `PasswordInputProps` | type | yes | - | packages/components/react-shadcn/src/ui/password-input.tsx:9 | PASS |
| `PresetsPanel` | function | yes | yes | packages/components/react-shadcn/src/components/grid/presets-panel.tsx:12 | PASS |
| `PreviewDetailsCard` | function | yes | yes | packages/components/react-shadcn/src/components/micro/links/preview-details-card.tsx:19 | PASS |
| `PricingSection` | function | yes | yes | packages/components/react-shadcn/src/components/sections/pricing-section.tsx:61 | PASS |
| `ProfessionalResume` | function | yes | yes | packages/components/react-shadcn/src/components/components/resumes/shadcnui/professional-resume.tsx:59 | PASS |
| `ProfilePage` | function | yes | yes | packages/components/react-shadcn/src/components/components/profile/profile-page.tsx:16 | PASS |
| `ProjectCard` | function | yes | yes | packages/components/react-shadcn/src/components/components/cards/shadcnui/project-card.tsx:31 | PASS |
| `ProjectsBlock` | function | yes | yes | packages/components/react-shadcn/src/components/sections/projects-block.tsx:18 | PASS |
| `ReactiveBackgroundGrid` | function | yes | yes | packages/components/react-shadcn/src/components/motion-core/reactive-background-grid.tsx:11 | PASS |
| `ResumeCard` | function | yes | yes | packages/components/react-shadcn/src/components/components/resumes/shadcnui/resume-card.tsx:138 | PASS |
| `RippleClickButton` | function | yes | yes | packages/components/react-shadcn/src/components/micro/buttons/ripple-click.tsx:12 | PASS |
| `SavedProject` | type | yes | - | packages/utils/src/types.ts:85 | PASS |
| `SavedProjectComponent` | type | yes | - | packages/utils/src/types.ts:71 | PASS |
| `SavedProjectPage` | type | yes | - | packages/utils/src/types.ts:77 | PASS |
| `ScaleHoverButton` | function | yes | yes | packages/components/react-shadcn/src/components/micro/buttons/scale-hover.tsx:5 | PASS |
| `ScrollArea` | const | yes | yes | packages/components/react-shadcn/src/ui/scroll-area.tsx:4 | PASS |
| `ScrollBar` | const | yes | yes | packages/components/react-shadcn/src/ui/scroll-area.tsx:20 | PASS |
| `ScrollProgressTracker` | function | yes | yes | packages/components/react-shadcn/src/components/motion-core/scroll-progress-tracker.tsx:11 | PASS |
| `ScrollReveal` | function | yes | yes | packages/components/react-shadcn/src/components/sections/scroll-reveal.tsx:47 | PASS |
| `Select` | function | yes | yes | packages/components/react-shadcn/src/ui/select.tsx:9 | PASS |
| `SelectContent` | function | yes | yes | packages/components/react-shadcn/src/ui/select.tsx:53 | PASS |
| `SelectGroup` | function | yes | yes | packages/components/react-shadcn/src/ui/select.tsx:15 | PASS |
| `SelectItem` | function | yes | yes | packages/components/react-shadcn/src/ui/select.tsx:103 | PASS |
| `SelectLabel` | function | yes | yes | packages/components/react-shadcn/src/ui/select.tsx:90 | PASS |
| `SelectScrollDownButton` | function | yes | yes | packages/components/react-shadcn/src/ui/select.tsx:156 | PASS |
| `SelectScrollUpButton` | function | yes | yes | packages/components/react-shadcn/src/ui/select.tsx:138 | PASS |
| `SelectSeparator` | function | yes | yes | packages/components/react-shadcn/src/ui/select.tsx:125 | PASS |
| `SelectTrigger` | function | yes | yes | packages/components/react-shadcn/src/ui/select.tsx:27 | PASS |
| `SelectValue` | function | yes | yes | packages/components/react-shadcn/src/ui/select.tsx:21 | PASS |
| `Separator` | const | yes | yes | packages/components/react-shadcn/src/ui/separator.tsx:8 | PASS |
| `ServicesGridBlock` | function | yes | yes | packages/components/react-shadcn/src/components/sections/services-grid-block.tsx:92 | PASS |
| `SettingsPanel` | function | yes | yes | packages/components/react-shadcn/src/components/grid/settings-panel.tsx:15 | PASS |
| `ShimmerButton` | function | yes | yes | packages/components/react-shadcn/src/components/micro/buttons/shimmer-button.tsx:6 | PASS |
| `SimpleCalendar` | function | yes | yes | packages/components/react-shadcn/src/components/forms/simple-calendar.tsx:10 | PASS |
| `Slider` | const | yes | yes | packages/components/react-shadcn/src/ui/slider.tsx:8 | PASS |
| `SmartHoverCard` | function | yes | yes | packages/components/react-shadcn/src/components/motion-core/smart-hover-card.tsx:14 | PASS |
| `SocialAnimation` | type | yes | - | packages/components/react-shadcn/src/components/native/social-login-button-shadcnui.tsx:8 | PASS |
| `SocialLoginButton` | function | yes | yes | packages/components/react-shadcn/src/components/native/social-login-button-shadcnui.tsx:57 | PASS |
| `SocialLoginButtonProps` | interface | yes | - | packages/components/react-shadcn/src/components/native/social-login-button-shadcnui.tsx:10 | PASS |
| `SocialProvider` | type | yes | - | packages/components/react-shadcn/src/components/native/social-login-button-shadcnui.tsx:7 | PASS |
| `SpotlightSection` | function | yes | yes | packages/components/react-shadcn/src/components/motion-core/spotlight-section.tsx:12 | PASS |
| `StackedCardCarousel` | function | yes | yes | packages/components/react-shadcn/src/components/motion-core/stacked-card-carousel.tsx:17 | PASS |
| `StaggeredDropdown` | function | yes | yes | packages/components/react-shadcn/src/components/components/dropdown/staggered-items.tsx:9 | PASS |
| `StaggeredHero` | function | yes | yes | packages/components/react-shadcn/src/components/page/hero/staggered-text.tsx:30 | PASS |
| `StandardResume` | function | yes | yes | packages/components/react-shadcn/src/components/components/resumes/shadcnui/standard-resume.tsx:98 | PASS |
| `StatsCounterBlock` | function | yes | yes | packages/components/react-shadcn/src/components/sections/stats-counter-block.tsx:82 | PASS |
| `StatsSection` | function | yes | yes | packages/components/react-shadcn/src/components/sections/stats-section.tsx:40 | PASS |
| `StocksDashboard` | function | yes | yes | packages/components/react-shadcn/src/components/components/stocks-dashboard/stocks-dashboard.tsx:454 | PASS |
| `Switch` | const | yes | yes | packages/components/react-shadcn/src/ui/switch.tsx:8 | PASS |
| `SyncedLyricCaptions` | function | yes | yes | packages/components/react-shadcn/src/components/motion-core/synced-lyric-captions.tsx:66 | PASS |
| `THEME_STORAGE_KEY` | const | yes | - | packages/components/react-shadcn/src/components/theme-provider.tsx:11 | PASS |
| `Tabs` | const | yes | yes | packages/components/react-shadcn/src/ui/tabs.tsx:7 | PASS |
| `TabsContent` | const | yes | yes | packages/components/react-shadcn/src/ui/tabs.tsx:39 | PASS |
| `TabsList` | const | yes | yes | packages/components/react-shadcn/src/ui/tabs.tsx:9 | PASS |
| `TabsTrigger` | const | yes | yes | packages/components/react-shadcn/src/ui/tabs.tsx:24 | PASS |
| `TeamSectionBlock` | function | yes | yes | packages/components/react-shadcn/src/components/sections/team-section-block.tsx:326 | PASS |
| `TestimonialSection` | function | yes | yes | packages/components/react-shadcn/src/components/sections/testimonial-section.tsx:41 | PASS |
| `TestimonialsBlock` | function | yes | yes | packages/components/react-shadcn/src/components/sections/testimonials-block.tsx:55 | PASS |
| `TextContentEntry` | type | yes | - | packages/utils/src/types.ts:52 | PASS |
| `Textarea` | const | yes | yes | packages/components/react-shadcn/src/ui/textarea.tsx:6 | PASS |
| `TextareaProps` | type | yes | - | packages/components/react-shadcn/src/ui/textarea.tsx:4 | PASS |
| `TheaterTicket` | function | yes | yes | packages/components/react-shadcn/src/components/sections/theater-ticket.tsx:7 | PASS |
| `ThemeMode` | type | yes | - | packages/components/react-shadcn/src/components/theme-provider.tsx:9 | PASS |
| `ThemeProvider` | function | yes | yes | packages/components/react-shadcn/src/components/theme-provider.tsx:18 | PASS |
| `TimelineBlock` | function | yes | yes | packages/components/react-shadcn/src/components/sections/timeline-block.tsx:47 | PASS |
| `ToastNotification` | function | yes | yes | packages/components/react-shadcn/src/components/page/notifications/toast-notification.tsx:9 | PASS |
| `Tooltip` | const | yes | yes | packages/components/react-shadcn/src/ui/tooltip.tsx:10 | PASS |
| `TooltipContent` | const | yes | yes | packages/components/react-shadcn/src/ui/tooltip.tsx:14 | PASS |
| `TooltipProvider` | const | yes | yes | packages/components/react-shadcn/src/ui/tooltip.tsx:8 | PASS |
| `TooltipTrigger` | const | yes | yes | packages/components/react-shadcn/src/ui/tooltip.tsx:12 | PASS |
| `TweetCard` | function | yes | yes | packages/components/react-shadcn/src/components/components/cards/tweet-card.tsx:17 | PASS |
| `UILibrary` | type | yes | - | packages/utils/src/types.ts:3 | PASS |
| `UILibraryContextValue` | - | yes | - | - | WARN |
| `UILibraryProvider` | function | yes | yes | packages/components/react-shadcn/src/ui-library-provider.tsx:31 | PASS |
| `VerifiedBadge` | function | yes | yes | packages/components/react-shadcn/src/components/native/native-verified-badge-shadcnui.tsx:104 | PASS |
| `VerifiedBadgeOutline` | function | yes | yes | packages/components/react-shadcn/src/components/native/native-verified-badge-shadcnui.tsx:162 | PASS |
| `VerifiedShieldBadge` | function | yes | yes | packages/components/react-shadcn/src/components/native/native-verified-badge-shadcnui.tsx:247 | PASS |
| `VolumeComponent` | function | yes | yes | packages/components/react-shadcn/src/components/components/sliders/volume-component.tsx:17 | PASS |
| `WeatherDashboard` | function | yes | yes | packages/components/react-shadcn/src/components/components/weather/weather-dashboard.tsx:390 | PASS |
| `WebPerformancePage` | function | yes | yes | packages/components/react-shadcn/src/components/web-performance/web-performance-page.tsx:394 | PASS |
| `WizardForm` | function | yes | yes | packages/components/react-shadcn/src/components/forms/wizard-form.tsx:165 | PASS |
| `add` | - | yes | - | - | WARN |
| `badgeVariants` | const | yes | yes | packages/components/react-shadcn/src/ui/badge.tsx:5 | PASS |
| `bentoPresets` | const | yes | - | packages/components/react-shadcn/src/lib/grid-presets.ts:7 | PASS |
| `buttonVariants` | const | yes | - | packages/components/react-shadcn/src/ui/button.tsx:6 | PASS |
| `cn` | function | yes | yes | packages/components/react-shadcn/src/lib/utils.ts:3 | PASS |
| `componentsRegistry` | const | yes | - | packages/registry/src/index.tsx:8 | PASS |
| `countSavedProjectComponents` | function | yes | yes | packages/utils/src/builder-utils.ts:70 | PASS |
| `createPage` | function | yes | yes | packages/utils/src/builder-utils.ts:33 | PASS |
| `extractSavedPages` | function | yes | yes | packages/utils/src/builder-utils.ts:52 | PASS |
| `fetchComponent` | - | yes | - | - | WARN |
| `generateGridCode` | const | yes | yes | packages/components/react-shadcn/src/lib/grid-utils.ts:47 | PASS |
| `generateUniqueSlug` | function | yes | yes | packages/utils/src/builder-utils.ts:14 | PASS |
| `getCellKey` | const | yes | yes | packages/components/react-shadcn/src/lib/grid-utils.ts:101 | PASS |
| `getGapSliderIndex` | const | yes | yes | packages/components/react-shadcn/src/lib/grid-utils.ts:32 | PASS |
| `getGapValueFromIndex` | const | yes | yes | packages/components/react-shadcn/src/lib/grid-utils.ts:40 | PASS |
| `initializeCells` | const | yes | yes | packages/components/react-shadcn/src/lib/grid-utils.ts:76 | PASS |
| `isCellInSelection` | const | yes | yes | packages/components/react-shadcn/src/lib/grid-utils.ts:106 | PASS |
| `mergeComponentImports` | function | yes | yes | packages/utils/src/merge-imports.ts:6 | PASS |
| `nativeComponents` | const | yes | - | packages/registry/src/registry/native.tsx:218 | PASS |
| `sanitizeSlug` | const | yes | yes | packages/utils/src/builder-utils.ts:7 | PASS |
| `uiComponents` | const | yes | - | packages/registry/src/registry/ui.tsx:179 | PASS |
| `uiLibraryLabels` | - | yes | - | packages/utils/src/types.ts:5 | PASS |
| `useTheme` | const | yes | yes | packages/components/react-shadcn/src/components/theme-provider.tsx:35 | PASS |
| `useUILibrary` | function | yes | yes | packages/components/react-shadcn/src/ui-library-provider.tsx:23 | PASS |

### Coverage Summary

- **Exports Found:** 327
- **Documented:** 327 (100%)
- **Missing Documentation:** 0
- **Signature Mismatches:** 0
- **Stale Documentation:** 3, documented extras included
- **Scoring Warnings:**
  - Type Coverage leaves out each name the stale-scope guard restored or the extraction recorded with no kind, such as an extraction gap (the provenance map, when one is given, gives it no kind Type Coverage reads at its file): `uiLibraryLabels`
- **Borderline Calls:**
  - `Avatar` (references/ui-primitives.md:38), inventory reader: the `(…)` that is `React.forwardRef<…>`'s whole argument list is a `…` written as an argument of its own, standing in for the omitted render function, so the declaration recorded as usage_signature is labelled partial; left open by: An entry whose signature the skill labels partial (simplified, key parameters, a `...` standing in for omitted members as a member or argument of its own, not rest or variadic syntax nor an argument's value such as `api_key=...`; …) carries `signature_form: "partial"`, any other `"full"` or no key, and a form that writes only a `return_type` carries none: copy the label, never judge the form; the other reading gives: signature_form full: the form sets no props (they come only from its type arguments), so a full reading flags no omitted prop either; no gap
  - `AvatarFallback` (references/ui-primitives.md:39), inventory reader: the `(…)` that is `React.forwardRef<…>`'s whole argument list is a `…` written as an argument of its own, so the declaration is labelled partial; left open by: An entry whose signature the skill labels partial (simplified, key parameters, a `...` standing in for omitted members as a member or argument of its own, not rest or variadic syntax nor an argument's value such as `api_key=...`; …) carries `signature_form: "partial"`, any other `"full"` or no key; the other reading gives: signature_form full; the form sets no props, so no gap
  - `AvatarImage` (references/ui-primitives.md:40), inventory reader: the `(…)` that is `React.forwardRef<…>`'s whole argument list is a `…` written as an argument of its own, so the declaration is labelled partial; left open by: An entry whose signature the skill labels partial (simplified, key parameters, a `...` standing in for omitted members as a member or argument of its own, not rest or variadic syntax nor an argument's value such as `api_key=...`; …) carries `signature_form: "partial"`, any other `"full"` or no key; the other reading gives: signature_form full; the form sets no props, so no gap
  - `CardDescription` (references/ui-primitives.md:47), inventory reader: the `(…)` that is `React.forwardRef<…>`'s whole argument list is a `…` written as an argument of its own, so the declaration is labelled partial; left open by: An entry whose signature the skill labels partial (simplified, key parameters, a `...` standing in for omitted members as a member or argument of its own, not rest or variadic syntax nor an argument's value such as `api_key=...`; …) carries `signature_form: "partial"`, any other `"full"` or no key; the other reading gives: signature_form full; the form sets no props, so no gap
  - `CardFooter` (references/ui-primitives.md:48), inventory reader: the `(…)` that is `React.forwardRef<…>`'s whole argument list is a `…` written as an argument of its own, so the declaration is labelled partial; left open by: An entry whose signature the skill labels partial (simplified, key parameters, a `...` standing in for omitted members as a member or argument of its own, not rest or variadic syntax nor an argument's value such as `api_key=...`; …) carries `signature_form: "partial"`, any other `"full"` or no key; the other reading gives: signature_form full; the form sets no props, so no gap
  - `CardTitle` (references/ui-primitives.md:49), inventory reader: the `(…)` that is `React.forwardRef<…>`'s whole argument list is a `…` written as an argument of its own, so the declaration is labelled partial; left open by: An entry whose signature the skill labels partial (simplified, key parameters, a `...` standing in for omitted members as a member or argument of its own, not rest or variadic syntax nor an argument's value such as `api_key=...`; …) carries `signature_form: "partial"`, any other `"full"` or no key; the other reading gives: signature_form full; the form sets no props, so no gap
  - `Checkbox` (references/ui-primitives.md:51), inventory reader: the `(…)` that is `React.forwardRef<…>`'s whole argument list is a `…` written as an argument of its own, so the declaration is labelled partial; left open by: An entry whose signature the skill labels partial (simplified, key parameters, a `...` standing in for omitted members as a member or argument of its own, not rest or variadic syntax nor an argument's value such as `api_key=...`; …) carries `signature_form: "partial"`, any other `"full"` or no key; the other reading gives: signature_form full; the form sets no props, so no gap
  - `DialogDescription` (references/ui-primitives.md:54), inventory reader: the `(…)` that is `React.forwardRef<…>`'s whole argument list is a `…` written as an argument of its own, so the declaration is labelled partial; left open by: An entry whose signature the skill labels partial (simplified, key parameters, a `...` standing in for omitted members as a member or argument of its own, not rest or variadic syntax nor an argument's value such as `api_key=...`; …) carries `signature_form: "partial"`, any other `"full"` or no key; the other reading gives: signature_form full; the form sets no props, so no gap
  - `DialogOverlay` (references/ui-primitives.md:57), inventory reader: the `(…)` that is `React.forwardRef<…>`'s whole argument list is a `…` written as an argument of its own, so the declaration is labelled partial; left open by: An entry whose signature the skill labels partial (simplified, key parameters, a `...` standing in for omitted members as a member or argument of its own, not rest or variadic syntax nor an argument's value such as `api_key=...`; …) carries `signature_form: "partial"`, any other `"full"` or no key; the other reading gives: signature_form full; the form sets no props, so no gap
  - `DialogTitle` (references/ui-primitives.md:59), inventory reader: the `(…)` that is `React.forwardRef<…>`'s whole argument list is a `…` written as an argument of its own, so the declaration is labelled partial; left open by: An entry whose signature the skill labels partial (simplified, key parameters, a `...` standing in for omitted members as a member or argument of its own, not rest or variadic syntax nor an argument's value such as `api_key=...`; …) carries `signature_form: "partial"`, any other `"full"` or no key; the other reading gives: signature_form full; the form sets no props, so no gap
  - `DropdownMenuCheckboxItem` (references/ui-primitives.md:63), inventory reader: the `(…)` that is `React.forwardRef<…>`'s whole argument list is a `…` written as an argument of its own, so the declaration is labelled partial; left open by: An entry whose signature the skill labels partial (simplified, key parameters, a `...` standing in for omitted members as a member or argument of its own, not rest or variadic syntax nor an argument's value such as `api_key=...`; …) carries `signature_form: "partial"`, any other `"full"` or no key; the other reading gives: signature_form full; the form sets no props, so no gap
  - `DropdownMenuContent` (references/ui-primitives.md:64), inventory reader: the `(…)` that is `React.forwardRef<…>`'s whole argument list is a `…` written as an argument of its own, so the declaration is labelled partial; left open by: An entry whose signature the skill labels partial (simplified, key parameters, a `...` standing in for omitted members as a member or argument of its own, not rest or variadic syntax nor an argument's value such as `api_key=...`; …) carries `signature_form: "partial"`, any other `"full"` or no key; the other reading gives: signature_form full; the form sets no props, so no gap
  - `DropdownMenuItem` (references/ui-primitives.md:66), inventory reader: the `(…)` that is `React.forwardRef<…>`'s whole argument list is a `…` written as an argument of its own, so the declaration is labelled partial; left open by: An entry whose signature the skill labels partial (simplified, key parameters, a `...` standing in for omitted members as a member or argument of its own, not rest or variadic syntax nor an argument's value such as `api_key=...`; …) carries `signature_form: "partial"`, any other `"full"` or no key; the other reading gives: signature_form full; the form sets no props (its own optional `inset` is written only in a type argument), so no gap
  - `DropdownMenuLabel` (references/ui-primitives.md:67), inventory reader: the `(…)` that is `React.forwardRef<…>`'s whole argument list is a `…` written as an argument of its own, so the declaration is labelled partial; left open by: An entry whose signature the skill labels partial (simplified, key parameters, a `...` standing in for omitted members as a member or argument of its own, not rest or variadic syntax nor an argument's value such as `api_key=...`; …) carries `signature_form: "partial"`, any other `"full"` or no key; the other reading gives: signature_form full; the form sets no props (its own optional `inset` is written only in a type argument), so no gap
  - `DropdownMenuRadioItem` (references/ui-primitives.md:70), inventory reader: the `(…)` that is `React.forwardRef<…>`'s whole argument list is a `…` written as an argument of its own, so the declaration is labelled partial; left open by: An entry whose signature the skill labels partial (simplified, key parameters, a `...` standing in for omitted members as a member or argument of its own, not rest or variadic syntax nor an argument's value such as `api_key=...`; …) carries `signature_form: "partial"`, any other `"full"` or no key; the other reading gives: signature_form full; the form sets no props, so no gap
  - `DropdownMenuSeparator` (references/ui-primitives.md:71), inventory reader: the `(…)` that is `React.forwardRef<…>`'s whole argument list is a `…` written as an argument of its own, so the declaration is labelled partial; left open by: An entry whose signature the skill labels partial (simplified, key parameters, a `...` standing in for omitted members as a member or argument of its own, not rest or variadic syntax nor an argument's value such as `api_key=...`; …) carries `signature_form: "partial"`, any other `"full"` or no key; the other reading gives: signature_form full; the form sets no props, so no gap
  - `DropdownMenuSubContent` (references/ui-primitives.md:74), inventory reader: the `(…)` that is `React.forwardRef<…>`'s whole argument list is a `…` written as an argument of its own, so the declaration is labelled partial; left open by: An entry whose signature the skill labels partial (simplified, key parameters, a `...` standing in for omitted members as a member or argument of its own, not rest or variadic syntax nor an argument's value such as `api_key=...`; …) carries `signature_form: "partial"`, any other `"full"` or no key; the other reading gives: signature_form full; the form sets no props, so no gap
  - `DropdownMenuSubTrigger` (references/ui-primitives.md:75), inventory reader: the `(…)` that is `React.forwardRef<…>`'s whole argument list is a `…` written as an argument of its own, so the declaration is labelled partial; left open by: An entry whose signature the skill labels partial (simplified, key parameters, a `...` standing in for omitted members as a member or argument of its own, not rest or variadic syntax nor an argument's value such as `api_key=...`; …) carries `signature_form: "partial"`, any other `"full"` or no key; the other reading gives: signature_form full; the form sets no props (its own optional `inset` is written only in a type argument), so no gap
  - `Label` (references/ui-primitives.md:78), inventory reader: the `(…)` that is `React.forwardRef<…>`'s whole argument list is a `…` written as an argument of its own, so the declaration is labelled partial; left open by: An entry whose signature the skill labels partial (simplified, key parameters, a `...` standing in for omitted members as a member or argument of its own, not rest or variadic syntax nor an argument's value such as `api_key=...`; …) carries `signature_form: "partial"`, any other `"full"` or no key; the other reading gives: signature_form full; the form sets no props (LabelProps is an alias of React.LabelHTMLAttributes, all inherited), so no gap
  - `ScrollArea` (references/ui-primitives.md:80), inventory reader: the `(…)` that is `React.forwardRef<…>`'s whole argument list is a `…` written as an argument of its own, so the declaration is labelled partial; left open by: An entry whose signature the skill labels partial (simplified, key parameters, a `...` standing in for omitted members as a member or argument of its own, not rest or variadic syntax nor an argument's value such as `api_key=...`; …) carries `signature_form: "partial"`, any other `"full"` or no key; the other reading gives: signature_form full; the form sets no props, so no gap
  - `ScrollBar` (references/ui-primitives.md:81), inventory reader: the `(…)` that is `React.forwardRef<…>`'s whole argument list is a `…` written as an argument of its own, so the declaration is labelled partial; left open by: An entry whose signature the skill labels partial (simplified, key parameters, a `...` standing in for omitted members as a member or argument of its own, not rest or variadic syntax nor an argument's value such as `api_key=...`; …) carries `signature_form: "partial"`, any other `"full"` or no key; the other reading gives: signature_form full; the form sets no props, so no gap
  - `Separator` (references/ui-primitives.md:94), inventory reader: the `(…)` that is `React.forwardRef<…>`'s whole argument list is a `…` written as an argument of its own, so the declaration is labelled partial; left open by: An entry whose signature the skill labels partial (simplified, key parameters, a `...` standing in for omitted members as a member or argument of its own, not rest or variadic syntax nor an argument's value such as `api_key=...`; …) carries `signature_form: "partial"`, any other `"full"` or no key; the other reading gives: signature_form full; the form sets no props, so no gap
  - `Slider` (references/ui-primitives.md:96), inventory reader: the `(…)` that is `React.forwardRef<…>`'s whole argument list is a `…` written as an argument of its own, so the declaration is labelled partial; left open by: An entry whose signature the skill labels partial (simplified, key parameters, a `...` standing in for omitted members as a member or argument of its own, not rest or variadic syntax nor an argument's value such as `api_key=...`; …) carries `signature_form: "partial"`, any other `"full"` or no key; the other reading gives: signature_form full; the form sets no props, so no gap
  - `Switch` (references/ui-primitives.md:98), inventory reader: the `(…)` that is `React.forwardRef<…>`'s whole argument list is a `…` written as an argument of its own, so the declaration is labelled partial; left open by: An entry whose signature the skill labels partial (simplified, key parameters, a `...` standing in for omitted members as a member or argument of its own, not rest or variadic syntax nor an argument's value such as `api_key=...`; …) carries `signature_form: "partial"`, any other `"full"` or no key; the other reading gives: signature_form full; the form sets no props, so no gap
  - `TabsContent` (references/ui-primitives.md:101), inventory reader: the `(…)` that is `React.forwardRef<…>`'s whole argument list is a `…` written as an argument of its own, so the declaration is labelled partial; left open by: An entry whose signature the skill labels partial (simplified, key parameters, a `...` standing in for omitted members as a member or argument of its own, not rest or variadic syntax nor an argument's value such as `api_key=...`; …) carries `signature_form: "partial"`, any other `"full"` or no key; the other reading gives: signature_form full; the form sets no props, so no gap
  - `TabsList` (references/ui-primitives.md:102), inventory reader: the `(…)` that is `React.forwardRef<…>`'s whole argument list is a `…` written as an argument of its own, so the declaration is labelled partial; left open by: An entry whose signature the skill labels partial (simplified, key parameters, a `...` standing in for omitted members as a member or argument of its own, not rest or variadic syntax nor an argument's value such as `api_key=...`; …) carries `signature_form: "partial"`, any other `"full"` or no key; the other reading gives: signature_form full; the form sets no props, so no gap
  - `TabsTrigger` (references/ui-primitives.md:103), inventory reader: the `(…)` that is `React.forwardRef<…>`'s whole argument list is a `…` written as an argument of its own, so the declaration is labelled partial; left open by: An entry whose signature the skill labels partial (simplified, key parameters, a `...` standing in for omitted members as a member or argument of its own, not rest or variadic syntax nor an argument's value such as `api_key=...`; …) carries `signature_form: "partial"`, any other `"full"` or no key; the other reading gives: signature_form full; the form sets no props, so no gap
  - `Textarea` (references/ui-primitives.md:105), inventory reader: the `(…)` that is `React.forwardRef<…>`'s whole argument list is a `…` written as an argument of its own, so the declaration is labelled partial; left open by: An entry whose signature the skill labels partial (simplified, key parameters, a `...` standing in for omitted members as a member or argument of its own, not rest or variadic syntax nor an argument's value such as `api_key=...`; …) carries `signature_form: "partial"`, any other `"full"` or no key; the other reading gives: signature_form full; the form sets no props (TextareaProps is an alias of React.TextareaHTMLAttributes, all inherited), so no gap
  - `TooltipContent` (references/ui-primitives.md:108), inventory reader: the `(…)` that is `React.forwardRef<…>`'s whole argument list is a `…` written as an argument of its own, so the declaration is labelled partial; left open by: An entry whose signature the skill labels partial (simplified, key parameters, a `...` standing in for omitted members as a member or argument of its own, not rest or variadic syntax nor an argument's value such as `api_key=...`; …) carries `signature_form: "partial"`, any other `"full"` or no key; the other reading gives: signature_form full; the form sets no props, so no gap
  - `NativeDialogContent` (references/native-components.md:45), inventory reader: the `(…)` that is `React.forwardRef<…>`'s whole argument list is a `…` written as an argument of its own, so the declaration is labelled partial; left open by: An entry whose signature the skill labels partial (simplified, key parameters, a `...` standing in for omitted members as a member or argument of its own, not rest or variadic syntax nor an argument's value such as `api_key=...`; …) carries `signature_form: "partial"`, any other `"full"` or no key; the other reading gives: signature_form full; the form sets no props, so no gap
  - `NativeDialogOverlay` (references/native-components.md:49), inventory reader: the `(…)` that is `React.forwardRef<…>`'s whole argument list is a `…` written as an argument of its own, so the declaration is labelled partial; left open by: An entry whose signature the skill labels partial (simplified, key parameters, a `...` standing in for omitted members as a member or argument of its own, not rest or variadic syntax nor an argument's value such as `api_key=...`; …) carries `signature_form: "partial"`, any other `"full"` or no key; the other reading gives: signature_form full; the form sets no props, so no gap
  - `NativeTooltipContent` (references/native-components.md:81), inventory reader: the `(…)` that is `React.forwardRef<…>`'s whole argument list is a `…` written as an argument of its own, so the declaration is labelled partial; left open by: An entry whose signature the skill labels partial (simplified, key parameters, a `...` standing in for omitted members as a member or argument of its own, not rest or variadic syntax nor an argument's value such as `api_key=...`; …) carries `signature_form: "partial"`, any other `"full"` or no key; the other reading gives: signature_form full; the form sets no props (its own optional `animation` is written only in a type argument), so no gap
  - `DialogFooter` (references/ui-primitives.md:55), inventory reader: an arrow-bound component const is neither the wrapper call nor the alias that the sentence on a `const` holding a component names, so this sentence applies and its destructured, typed parameter list is `params` (`=> …` writes no return type); left open by: A `const` whose value is a function (annotated with a function type, bound to an arrow, a `function` or a call that returns one, or written with a parameter list) carries the function form the skill writes for it as `params` (`[]`, never `""`, when it takes none) and `return_type`, whatever its kind (`constant` for the skill's `const` label), wherever the skill writes it, …; the other reading gives: the whole declaration in usage_signature under the component-const sentence; the destructuring ends in a rest element, which leaves no prop out under either reading, so no gap
  - `DialogHeader` (references/ui-primitives.md:56), inventory reader: an arrow-bound component const, not a wrapper call or alias, so its destructured, typed parameter list is `params`; left open by: A `const` whose value is a function (annotated with a function type, bound to an arrow, a `function` or a call that returns one, or written with a parameter list) carries the function form the skill writes for it as `params` (…) and `return_type`, whatever its kind (`constant` for the skill's `const` label), wherever the skill writes it, …; the other reading gives: the whole declaration in usage_signature; its rest element leaves no prop out either way, so no gap
  - `DropdownMenuShortcut` (references/ui-primitives.md:72), inventory reader: an arrow-bound component const, not a wrapper call or alias, so its destructured, typed parameter list is `params`; left open by: A `const` whose value is a function (annotated with a function type, bound to an arrow, a `function` or a call that returns one, or written with a parameter list) carries the function form the skill writes for it as `params` (…) and `return_type`, whatever its kind (`constant` for the skill's `const` label), wherever the skill writes it, …; the other reading gives: the whole declaration in usage_signature; its rest element leaves no prop out either way, so no gap
  - `NativeButton` (references/native-components.md:37), inventory reader: an arrow-bound component const, not a wrapper call or alias, so its destructured, typed parameter list is `params`; left open by: A `const` whose value is a function (annotated with a function type, bound to an arrow, a `function` or a call that returns one, or written with a parameter list) carries the function form the skill writes for it as `params` (…) and `return_type`, whatever its kind (`constant` for the skill's `const` label), wherever the skill writes it, …; the other reading gives: the whole declaration in usage_signature, read as a usage; its rest element leaves no prop out either way, so no gap
  - `NativeTooltip` (references/native-components.md:80), inventory reader: an arrow-bound component const, not a wrapper call or alias, so its destructured, typed parameter list is `params`; left open by: A `const` whose value is a function (annotated with a function type, bound to an arrow, a `function` or a call that returns one, or written with a parameter list) carries the function form the skill writes for it as `params` (…) and `return_type`, whatever its kind (`constant` for the skill's `const` label), wherever the skill writes it, …; the other reading gives: the whole declaration in usage_signature; its rest element leaves no prop out either way, so no gap
  - `NativeTooltipProvider` (references/native-components.md:82), inventory reader: an arrow-bound component const, not a wrapper call or alias, so its destructured, typed parameter list is `params`; left open by: A `const` whose value is a function (annotated with a function type, bound to an arrow, a `function` or a call that returns one, or written with a parameter list) carries the function form the skill writes for it as `params` (…) and `return_type`, whatever its kind (`constant` for the skill's `const` label), wherever the skill writes it, …; the other reading gives: the whole declaration in usage_signature; its rest element leaves no prop out either way, so no gap
  - `SocialLoginButton` (references/native-components.md:93), inventory reader: an arrow-bound component const, not a wrapper call or alias, so its destructured, typed parameter list is `params`; left open by: A `const` whose value is a function (annotated with a function type, bound to an arrow, a `function` or a call that returns one, or written with a parameter list) carries the function form the skill writes for it as `params` (…) and `return_type`, whatever its kind (`constant` for the skill's `const` label), wherever the skill writes it, …; the other reading gives: the whole declaration in usage_signature; its rest element leaves no prop out either way, so no gap
  - `LiquidCursor` (references/motion-components.md:142), inventory reader: `export const LiquidCursor = () => …` is an arrow-bound component const with an empty parameter list, so `params` is `[]` (it takes none); left open by: A `const` whose value is a function (annotated with a function type, bound to an arrow, a `function` or a call that returns one, or written with a parameter list) carries the function form the skill writes for it as `params` (`[]`, never `""`, when it takes none) and `return_type`, whatever its kind (`constant` for the skill's `const` label), wherever the skill writes it, …; the other reading gives: the declaration in usage_signature, read as an empty call; both readings claim no required prop, so a gap arises only if the source requires one, under either reading
  - `BrowseFolder` (references/blocks-and-sections.md:41), inventory reader: `export const BrowseFolder = () => …` is an arrow-bound component const with an empty parameter list, so `params` is `[]` (it takes none); left open by: A `const` whose value is a function (annotated with a function type, bound to an arrow, a `function` or a call that returns one, or written with a parameter list) carries the function form the skill writes for it as `params` (`[]`, never `""`, when it takes none) and `return_type`, whatever its kind (`constant` for the skill's `const` label), wherever the skill writes it, …; the other reading gives: the declaration in usage_signature, read as an empty call; both readings claim no required prop, so a gap arises only if the source requires one, under either reading
  - `badgeVariants` (references/ui-primitives.md:119), inventory reader: the fenced `const badgeVariants = cva(…)` (ui-primitives.md:43) writes no form of badgeVariants, and the floor gives its export-table row an entry, so by the formless-place sentence the fenced line gives none; left open by: A `const` holding a function, not a component, that a place writes only as the call that builds it (`const badgeVariants = cva(…)`), with no parameter list, function type or return type of its own, carries no `params`, `return_type` or `usage_signature` there: that call is the factory's form, not the const's; the other reading gives: a second formless entry at references/ui-primitives.md:43; nothing is compared, so no gap
  - `buttonVariants` (references/ui-primitives.md:120), inventory reader: the fenced `const buttonVariants = cva(…)` (ui-primitives.md:45) writes no form of buttonVariants, and the floor gives its export-table row an entry, so the fenced line gives none; left open by: A `const` holding a function, not a component, that a place writes only as the call that builds it (`const badgeVariants = cva(…)`), with no parameter list, function type or return type of its own, carries no `params`, `return_type` or `usage_signature` there: that call is the factory's form, not the const's; the other reading gives: a second formless entry at references/ui-primitives.md:45; nothing is compared, so no gap
  - `badgeVariants` (references/ui-primitives.md:118), inventory reader: `badgeVariants({ variant })` in Badge's Purpose cell is a description-cell call that passes an argument and writes no type, so it is a usage form of badgeVariants (a const holding the function cva returns) at that row; left open by: A function's, a method's or a class's form the skill writes as a call expression of its own name (…; in running text or a description cell, only a call that passes an argument and writes no parameter type, `?`, bare `*` or `/`, …), at a place `inventory-floor.json` gives no `signature` (below), is recorded whole in `usage_signature`, …; the other reading gives: a description of how Badge renders, giving badgeVariants no form there: no gap; as a usage it passes `variant`, which the skill lists among badgeVariants' variants, so no gap is expected either
  - `GridCell` (references/motion-components.md:229), inventory reader: motion-components.md:238 says the GridCell component is a different export from the GridCell interface of grid-utils, so the name is two exports and each keeps its own kind: `function` for the component (motion-components.md:229, :243), `interface` for the interface (utils.md:65, types.md:122); left open by: A name documented in several places is listed once per place, each entry with that place's form (`Card` above), and once per form at a place that writes several of its forms (two overloads in one row), each entry with that place as its `at`, never as one entry whose list `params` gives a form per item (…), and keeps one `kind` in every place; the other reading gives: one kind for all four GridCell entries; the component's params are unchanged and the interface entries carry only fields, so no gap
  - `PasswordInput` (references/motion-components.md:140), inventory reader: the src/ui PasswordInput (a forwardRef component taking PasswordInputProps, a different declaration from the motion component) is described only in prose at ui-primitives.md:179, and the name has entries at motion-components.md:140 and :198, so the prose gives none; left open by: A place that writes a name but no form of it, and no `methods`, `properties` or `fields` its entry would carry (a mention, a bare code span, an import, a heading or prose that names or describes it), gives it no entry when another place gives the name one, unless `inventory-floor.json` gives that place; …; the other reading gives: a separate formless entry for the src/ui PasswordInput at references/ui-primitives.md:179; it writes no form, so no gap
  - `AnimatedCheckbox` (references/motion-components.md:130), inventory reader: the byte-identical src/ui AnimatedCheckbox is described only in prose at ui-primitives.md:178, which says motion-components.md's signature holds for both; the name has entries there, so the prose gives none; left open by: A place that writes a name but no form of it, and no `methods`, `properties` or `fields` its entry would carry (a mention, a bare code span, an import, a heading or prose that names or describes it), gives it no entry when another place gives the name one, unless `inventory-floor.json` gives that place; …; the other reading gives: a separate formless entry at references/ui-primitives.md:178: no gap
  - `NativeLiquidButton` (references/native-components.md:117), inventory reader: the row is the floor's place and gives the shipped NativeLiquidButton's entry; the second NativeLiquidButton (native-liquid-button.tsx) it describes in its Purpose cell, with different props, is written without a form and gets no entry of its own; left open by: A place that writes a name but no form of it, and no `methods`, `properties` or `fields` its entry would carry (a mention, a bare code span, an import, a heading or prose that names or describes it), gives it no entry when another place gives the name one, unless `inventory-floor.json` gives that place; …; the other reading gives: a second formless NativeLiquidButton entry for that declaration: no gap
  - `Button` (SKILL.md:41), inventory reader: ui-primitives.md:3 counts Button among the src/ui exports covered by integration.md's import example, so the skill documents it; no place writes its form, so its first place, SKILL.md:41, gives one formless entry (kind `constant`; the skill gives none); left open by: A place that writes a name but no form of it, and no `methods`, `properties` or `fields` its entry would carry (…), gives it no entry when another place gives the name one, unless `inventory-floor.json` gives that place; of several such places of a name the skill documents and no other place gives an entry, the first alone gives one: in SKILL.md, else the file that sorts first by path, at its lowest line; the other reading gives: no entry, reading the mentions and imports as not documenting an export: no gap, as nothing is compared
  - `Card` (SKILL.md:160), inventory reader: ui-primitives.md:3 counts Card among the src/ui exports covered by integration.md's import example; its first place is SKILL.md:160's plain-text primitives list, which gives one formless entry; left open by: … of several such places of a name the skill documents and no other place gives an entry, the first alone gives one: in SKILL.md, else the file that sorts first by path, at its lowest line; the other reading gives: no entry, or one at references/integration.md:39 (its first code-span place): no gap
  - `Dialog` (SKILL.md:160), inventory reader: ui-primitives.md:3 counts Dialog among the src/ui exports covered by integration.md's import example; its first place is SKILL.md:160, which gives one formless entry (native-components.md:43 writes it only as NativeDialog's aliased value); left open by: … of several such places of a name the skill documents and no other place gives an entry, the first alone gives one: in SKILL.md, else the file that sorts first by path, at its lowest line; the other reading gives: no entry, or one at references/integration.md:41: no gap
  - `CardContent` (references/integration.md:39), inventory reader: SKILL.md never writes CardContent; the first file by path that does is integration.md, whose import at line 39 gives one formless entry; left open by: … of several such places of a name the skill documents and no other place gives an entry, the first alone gives one: in SKILL.md, else the file that sorts first by path, at its lowest line; the other reading gives: no entry, reading the import as not documenting an export: no gap
  - `CardHeader` (references/integration.md:39), inventory reader: SKILL.md never writes CardHeader; the first file by path that does is integration.md, whose import at line 39 gives one formless entry; left open by: … of several such places of a name the skill documents and no other place gives an entry, the first alone gives one: in SKILL.md, else the file that sorts first by path, at its lowest line; the other reading gives: no entry: no gap
  - `DialogContent` (references/integration.md:41), inventory reader: SKILL.md never writes DialogContent; the first file by path that does is integration.md, whose import at line 41 gives one formless entry; left open by: … of several such places of a name the skill documents and no other place gives an entry, the first alone gives one: in SKILL.md, else the file that sorts first by path, at its lowest line; the other reading gives: no entry: no gap
  - `Input` (references/catalog.md:71), inventory reader: SKILL.md never writes Input; blocks-and-sections.md:317, the first file by path with the token, uses it only as the English word opening FloatingLabelInput's purpose, so the first place naming the primitive is catalog.md:71; left open by: … of several such places of a name the skill documents and no other place gives an entry, the first alone gives one: in SKILL.md, else the file that sorts first by path, at its lowest line; the other reading gives: the entry at references/blocks-and-sections.md:317 (the first token match), or no entry: no gap
  - `ThemeMode` (SKILL.md:139), inventory reader: a union alias carries no form (a `type` alias carries no `usage_signature`, `params` or `return_type`) and no fields, so its fenced declarations are formless places; the first, SKILL.md:139, gives the one entry and types.md:20 gives none; left open by: A place that writes a name but no form of it, and no `methods`, `properties` or `fields` its entry would carry (…), gives it no entry when another place gives the name one, unless `inventory-floor.json` gives that place; of several such places of a name the skill documents and no other place gives an entry, the first alone gives one: in SKILL.md, else the file that sorts first by path, at its lowest line; the other reading gives: a further type entry at references/types.md:20: no gap, as a type entry is never compared
  - `UILibrary` (SKILL.md:142), inventory reader: the 4-member union alias writes no form or fields, so SKILL.md:142 gives the one entry and types.md:30 and utils.md:129 give none; the react-shadcn package's 3-member UILibrary, written only in prose and a code comment, gets no entry of its own; left open by: A place that writes a name but no form of it, and no `methods`, `properties` or `fields` its entry would carry (…), gives it no entry when another place gives the name one, unless `inventory-floor.json` gives that place; of several such places …, the first alone gives one: in SKILL.md, …; the other reading gives: entries at references/types.md:30 and references/utils.md:129, or a separate one for the 3-member declaration: no gap
  - `ComponentCategory` (SKILL.md:162), inventory reader: every place writes no form and no fields (types.md:40 and utils.md:133 are union aliases), so the first, the SKILL.md:162 mention, gives the one entry; left open by: … of several such places of a name the skill documents and no other place gives an entry, the first alone gives one: in SKILL.md, else the file that sorts first by path, at its lowest line; the other reading gives: the entry at references/types.md:40 (the fenced declaration) instead or as well: no gap
  - `SocialProvider` (SKILL.md:207), inventory reader: every place writes no form and no fields (types.md:978 is a union alias, types.md:973 a heading, types.md:983 a type position), so the first, the SKILL.md:207 mention, gives the one entry; left open by: … of several such places of a name the skill documents and no other place gives an entry, the first alone gives one: in SKILL.md, else the file that sorts first by path, at its lowest line; the other reading gives: the entry at references/types.md:978 instead or as well: no gap
  - `NotchSize` (references/types.md:760), inventory reader: the heading (760) and the fenced union alias (765) both write no form or fields, and SKILL.md never writes the name, so the lowest line, the heading, gives the entry; left open by: … of several such places of a name the skill documents and no other place gives an entry, the first alone gives one: in SKILL.md, else the file that sorts first by path, at its lowest line; the other reading gives: the entry at references/types.md:765: no gap
  - `SocialAnimation` (references/types.md:973), inventory reader: the heading (973) and the fenced union alias (980) both write no form or fields, so the lowest line, the heading, gives the entry; left open by: … of several such places of a name the skill documents and no other place gives an entry, the first alone gives one: in SKILL.md, else the file that sorts first by path, at its lowest line; the other reading gives: the entry at references/types.md:980: no gap
  - `BadgeProps` (references/types.md:991), inventory reader: the floor gives the heading an entry; the fenced `export interface BadgeProps … {}` below it declares no members of its own, so it writes no fields and gives none; left open by: A place that writes a name but no form of it, and no `methods`, `properties` or `fields` its entry would carry (…), gives it no entry when another place gives the name one, unless `inventory-floor.json` gives that place; …; the other reading gives: a second, fieldless interface entry at references/types.md:996: no gap
  - `InputProps` (references/types.md:1017), inventory reader: the fenced alias at types.md:1022 writes no form or fields, so only the floor's heading gives an entry; left open by: A place that writes a name but no form of it, and no `methods`, `properties` or `fields` its entry would carry (…), gives it no entry when another place gives the name one, unless `inventory-floor.json` gives that place; …; the other reading gives: a second type entry at references/types.md:1022: no gap
  - `LabelProps` (references/types.md:1027), inventory reader: the fenced alias at types.md:1032 writes no form or fields, so only the floor's heading gives an entry; left open by: A place that writes a name but no form of it, and no `methods`, `properties` or `fields` its entry would carry (…), gives it no entry when another place gives the name one, unless `inventory-floor.json` gives that place; …; the other reading gives: a second type entry at references/types.md:1032: no gap
  - `PasswordInputProps` (references/types.md:1037), inventory reader: the fenced alias at types.md:1042 writes no form or fields, so only the floor's heading gives an entry; left open by: A place that writes a name but no form of it, and no `methods`, `properties` or `fields` its entry would carry (…), gives it no entry when another place gives the name one, unless `inventory-floor.json` gives that place; …; the other reading gives: a second type entry at references/types.md:1042: no gap
  - `TextareaProps` (references/types.md:1050), inventory reader: the fenced alias at types.md:1055 writes no form or fields, so only the floor's heading gives an entry; left open by: A place that writes a name but no form of it, and no `methods`, `properties` or `fields` its entry would carry (…), gives it no entry when another place gives the name one, unless `inventory-floor.json` gives that place; …; the other reading gives: a second type entry at references/types.md:1055: no gap
  - `NativeDeleteProps` (references/types.md:386), inventory reader: native-components.md:27 names three NativeDeleteProps members (onConfirm and onDelete required, size "sm" | "md" | "lg") in prose; prose that describes a name is listed as formless and types.md gives the name entries, so it gives none; left open by: A place that writes a name but no form of it, and no `methods`, `properties` or `fields` its entry would carry (a mention, a bare code span, an import, a heading or prose that names or describes it), gives it no entry when another place gives the name one, unless `inventory-floor.json` gives that place; …; the other reading gives: an interface entry at references/native-components.md:27 with those three fields; fields are never compared, so no gap
  - `AIGlowInput` (references/motion-components.md:37), inventory reader: motion-components.md:14 says a props type a signature names that types.md does not list is not exported; types.md does not list AIGlowInputProps, so its prose code span at motion-components.md:29 gives it no entry, and likewise CodeOutputProps, PresetsPanelProps, SettingsPanelProps, NativeFlipTextProps, NativeTypewriterProps, TweetCardProps, VerifiedBadgeProps and the other unlisted props types named in signatures and Purpose cells; GridCellProps, which motion-components.md:238 says grid-cell.tsx does not export, and the local alias GridCellType get none either; left open by: A name the skill presents only as a local import alias of another name, or says the source does not export, is not an export the skill documents either: it gets an entry only from a place `inventory-floor.json` gives it, a heading, an export table's first cell or a fenced declaration of it (an import is not one), never from a code span in prose or a description cell; the other reading gives: type entries for those props types at their prose or description-cell code spans: no gap, as type entries are never compared
  - `useUILibrary` (references/setup.md:82), inventory reader: the **Return type** block under useUILibrary (setup.md:87-94) is a place that writes only a return type for it, so it gives a second hook entry with `return_type` `UILibraryContextValue` and no `at`; the usage at setup.md:82 carries no return_type; left open by: … a form that writes only a `return_type` gives no `at`, so it is compared as one whose citations name no declaration; the other reading gives: the return type folded into the setup.md:82 usage entry: the same return is compared either way, so no gap
  - `UILibraryProvider` (references/setup.md:53), inventory reader: `<UILibraryProvider>` in running text at setup.md:85 sets no props, the JSX counterpart of an empty call, so it is a mention and gives no entry (the props table under setup.md:53 gives the name one); left open by: A name written with empty parentheses, or with only `...` or `…` between them, in running text or a description cell is a mention, not a form, whatever comes before the name (`await`, `new`, an assignment, a receiver or a module path): its entry leaves `params` and `usage_signature` out (…); the other reading gives: a usage_signature `<UILibraryProvider>` at references/setup.md:85, read as a usage that sets no props; an opening tag passes children, so no gap
- **Scoped Out by the Brief:** `NativeAvatarExpandDefault` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx:5), `NativeAvatarExpandDemo` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx:57), `NativeAvatarExpandExtraLarge` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx:37), `NativeAvatarExpandLarge` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx:25), `NativeAvatarExpandNoImage` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx:49), `NativeAvatarExpandSmall` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx:13), `NativeAvatarWithNameDefault` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx:5), `NativeAvatarWithNameDemo` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx:84), `NativeAvatarWithNameLarge` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx:64), `NativeAvatarWithNameLeft` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx:28), `NativeAvatarWithNameNoImage` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx:76), `NativeAvatarWithNameRight` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx:40), `NativeAvatarWithNameSmall` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx:52), `NativeAvatarWithNameTop` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx:16), `NativeButtonDefault` (packages/components/react-shadcn/src/components/native/demo/native-button-demo.tsx:5), `NativeButtonDisabled` (packages/components/react-shadcn/src/components/native/demo/native-button-demo.tsx:21), `NativeButtonGlow` (packages/components/react-shadcn/src/components/native/demo/native-button-demo.tsx:9), `NativeButtonLoading` (packages/components/react-shadcn/src/components/native/demo/native-button-demo.tsx:17), `NativeButtonOutline` (packages/components/react-shadcn/src/components/native/demo/native-button-demo.tsx:13), `NativeDeleteCustomText` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx:71), `NativeDeleteDefault` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx:6), `NativeDeleteDemo` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx:124), `NativeDeleteDisabled` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx:116), `NativeDeleteLarge` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx:49), `NativeDeleteNoIcon` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx:94), `NativeDeleteSmall` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx:27), `NativeDialogDemo` (packages/components/react-shadcn/src/components/native/demo/native-dialog-demo.tsx:14), `NativeHoverCardBordered` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:38), `NativeHoverCardCustomButton` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:130), `NativeHoverCardCustomButtonText` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:156), `NativeHoverCardDefault` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:7), `NativeHoverCardDemo` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:200), `NativeHoverCardExtraLarge` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:86), `NativeHoverCardGlass` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:22), `NativeHoverCardLarge` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:70), `NativeHoverCardMinimal` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:172), `NativeHoverCardNoDescription` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:116), `NativeHoverCardNoUsername` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:102), `NativeHoverCardSmall` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:54), `NativeHoverCardWithFallback` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:185), `NativeImageCheckboxDefault` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx:6), `NativeImageCheckboxDemo` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx:117), `NativeImageCheckboxExtraLarge` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx:50), `NativeImageCheckboxGrid` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx:79), `NativeImageCheckboxLarge` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx:35), `NativeImageCheckboxSelected` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx:65), `NativeImageCheckboxSmall` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx:20), `NativeLikesCounterDefault` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx:38), `NativeLikesCounterDemo` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx:131), `NativeLikesCounterGhost` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx:62), `NativeLikesCounterInteractive` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx:91), `NativeLikesCounterOutline` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx:54), `NativeLikesCounterSizes` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx:70), `NativeLikesCounterSubtle` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx:46), `NativeLiquidButtonCustomColor` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:136), `NativeLiquidButtonDefault` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:6), `NativeLiquidButtonDemo` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:146), `NativeLiquidButtonError` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:88), `NativeLiquidButtonGlow` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:24), `NativeLiquidButtonGradient` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:14), `NativeLiquidButtonLoading` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:68), `NativeLiquidButtonSizes` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:98), `NativeLiquidButtonSuccess` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:78), `NativeLiquidButtonVariants` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:117), `NativeLiquidButtonWave` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:34), `NativeLiquidButtonWithProgress` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:44), `NativeMagneticDefault` (packages/components/react-shadcn/src/components/native/demo/native-magnetic-demo.tsx:6), `NativeMagneticDemo` (packages/components/react-shadcn/src/components/native/demo/native-magnetic-demo.tsx:42), `NativeMagneticLink` (packages/components/react-shadcn/src/components/native/demo/native-magnetic-demo.tsx:16), `NativeMagneticStrong` (packages/components/react-shadcn/src/components/native/demo/native-magnetic-demo.tsx:30), `NativeMorphingButtonCustomIcon` (packages/components/react-shadcn/src/components/native/demo/native-morphing-button-demo.tsx:32), `NativeMorphingButtonDefault` (packages/components/react-shadcn/src/components/native/demo/native-morphing-button-demo.tsx:6), `NativeMorphingButtonDemo` (packages/components/react-shadcn/src/components/native/demo/native-morphing-button-demo.tsx:54), `NativeNestedListDemo` (packages/components/react-shadcn/src/components/native/demo/native-nested-list-demo.tsx:88), `NativeNotchDefault` (packages/components/react-shadcn/src/components/native/demo/native-notch-demo.tsx:6), `NativeNotchLeftAlign` (packages/components/react-shadcn/src/components/native/demo/native-notch-demo.tsx:37), `NativeNotchRelative` (packages/components/react-shadcn/src/components/native/demo/native-notch-demo.tsx:69), `NativeNotificationBellCustomIcon` (packages/components/react-shadcn/src/components/native/demo/native-notification-bell-demo.tsx:22), `NativeNotificationBellDefault` (packages/components/react-shadcn/src/components/native/demo/native-notification-bell-demo.tsx:6), `NativeNotificationBellDemo` (packages/components/react-shadcn/src/components/native/demo/native-notification-bell-demo.tsx:33), `NativeNotificationBellEmpty` (packages/components/react-shadcn/src/components/native/demo/native-notification-bell-demo.tsx:14), `NativeProfileNotchDefault` (packages/components/react-shadcn/src/components/native/demo/native-profile-notch-demo.tsx:5), `NativeProfileNotchOverlay` (packages/components/react-shadcn/src/components/native/demo/native-profile-notch-demo.tsx:37), `NativeStartNowCustomLabels` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:82), `NativeStartNowDefault` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:6), `NativeStartNowDemo` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:150), `NativeStartNowDisabled` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:95), `NativeStartNowGradient` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:16), `NativeStartNowHeartIcon` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:128), `NativeStartNowLarge` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:60), `NativeStartNowNoSparkles` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:71), `NativeStartNowOutline` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:38), `NativeStartNowRocketIcon` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:139), `NativeStartNowSmall` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:49), `NativeStartNowSolid` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:27), `NativeStartNowStarIcon` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:106), `NativeStartNowZapIcon` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:117), `NativeTabsDemo` (packages/components/react-shadcn/src/components/native/demo/native-tabs-demo.tsx:5), `NativeTooltipBlur` (packages/components/react-shadcn/src/components/native/demo/native-tooltip-demo.tsx:9), `NativeTooltipDemo` (packages/components/react-shadcn/src/components/native/demo/native-tooltip-demo.tsx:29), `NativeTooltipScale` (packages/components/react-shadcn/src/components/native/demo/native-tooltip-demo.tsx:19), `NativeTypewriterDefault` (packages/components/react-shadcn/src/components/native/demo/native-typewriter-demo.tsx:5), `NativeTypewriterDemo` (packages/components/react-shadcn/src/components/native/demo/native-typewriter-demo.tsx:46), `NativeTypewriterLoop` (packages/components/react-shadcn/src/components/native/demo/native-typewriter-demo.tsx:32), `NativeTypewriterMultiline` (packages/components/react-shadcn/src/components/native/demo/native-typewriter-demo.tsx:16), `NativeUserCardDemo` (packages/components/react-shadcn/src/components/native/demo/native-user-card-demo.tsx:5), `NativeVerifiedBadgeCustomIcon` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx:128), `NativeVerifiedBadgeDefault` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx:30), `NativeVerifiedBadgeDemo` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx:153), `NativeVerifiedBadgeOutlineVariants` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx:80), `NativeVerifiedBadgeShield` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx:93), `NativeVerifiedBadgeSizes` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx:53), `NativeVerifiedBadgeWithLabel` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx:40), `NativeVerifiedBadgeWithTooltip` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx:103), `SocialButtonsGlow` (packages/components/react-shadcn/src/components/native/demo/social-login-demo.tsx:23), `SocialButtonsScale` (packages/components/react-shadcn/src/components/native/demo/social-login-demo.tsx:14), `SocialButtonsShine` (packages/components/react-shadcn/src/components/native/demo/social-login-demo.tsx:33), `SocialButtonsSlide` (packages/components/react-shadcn/src/components/native/demo/social-login-demo.tsx:5)
- **Extraction Gaps:** `GAP_VALUES` (packages/components/react-shadcn/src/lib/grid-utils.ts:23), `THEME_STORAGE_KEY` (packages/components/react-shadcn/src/components/theme-provider.tsx:11), `bentoPresets` (packages/components/react-shadcn/src/lib/grid-presets.ts:7), `cn` (packages/components/react-shadcn/src/lib/utils.ts:3), `componentsRegistry` (packages/registry/src/index.tsx:8), `countSavedProjectComponents` (packages/utils/src/builder-utils.ts:70), `createPage` (packages/utils/src/builder-utils.ts:33), `extractSavedPages` (packages/utils/src/builder-utils.ts:52), `generateGridCode` (packages/components/react-shadcn/src/lib/grid-utils.ts:47), `generateUniqueSlug` (packages/utils/src/builder-utils.ts:14), `getCellKey` (packages/components/react-shadcn/src/lib/grid-utils.ts:101), `getGapSliderIndex` (packages/components/react-shadcn/src/lib/grid-utils.ts:32), `getGapValueFromIndex` (packages/components/react-shadcn/src/lib/grid-utils.ts:40), `initializeCells` (packages/components/react-shadcn/src/lib/grid-utils.ts:76), `isCellInSelection` (packages/components/react-shadcn/src/lib/grid-utils.ts:106), `mergeComponentImports` (packages/utils/src/merge-imports.ts:6), `nativeComponents` (packages/registry/src/registry/native.tsx:218), `sanitizeSlug` (packages/utils/src/builder-utils.ts:7), `uiComponents` (packages/registry/src/registry/ui.tsx:179), `uiLibraryLabels` (packages/utils/src/types.ts:5), `useTheme` (packages/components/react-shadcn/src/components/theme-provider.tsx:35), `useUILibrary` (packages/components/react-shadcn/src/ui-library-provider.tsx:23)

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 100% |
| Signature Accuracy | 100% |
| Type Coverage | 100% |

### Coverage Notes

- **Inventory (§1, §1a):** one inventory-reader subagent read SKILL.md and all nine `references/*.md` files and wrote 619 entries (the floor's 276 names at all their origins), 0 `cross_check_mismatches` and 70 `undecided` readings. `validate-inventory.py` accepted it on the first pass (0 violations, 0 warnings), so no form was left unbound for want of a place. `crossChecked`: 90 names that two or more of the files write.
- **Split-body cross-check (§1b):** `references` lists 9 files; the reader compared every export two or more files document and found no split-body mismatch, so no `split-body-mismatch` gap is recorded and no Split-Body Sources judge was needed.
- **Surface (§2):** the recipe runner (`skf-extract-public-api.py --mode full --head-cap 0`) needed no fallback. Read by eye (ast-grep reported syntax errors in each): `packages/components/react-shadcn/src/components/components/blog/blog-typography.tsx`, `.../course-content/course-content-page.tsx`, `.../profile/profile-page.tsx`, `.../resumes/shadcnui/professional-resume.tsx`, `.../weather/weather-dashboard.tsx`, `packages/components/react-shadcn/src/components/sections/bento-grid-block.tsx`, `.../sections/cinema-ticket.tsx`, `.../sections/conference-ticket.tsx`, `.../sections/glassmorphism-portfolio-block.tsx`, `.../sections/notion-blog-page.tsx` — one export each (`BlogTypography`, `CourseContentPage`, `ProfilePage`, `ProfessionalResume`, `WeatherDashboard`, `BentoGridBlock`, `CinemaTicket`, `ConferenceTicket`, `GlassmorphismPortfolioBlock`, `NotionBlogPage`), given to `surface` as per-file results in one second pass. Unread: none. Unresolved star re-exports: none.
- **Signatures (§2, §2b):** `score-signatures.py plan` planned 270 checks over 202 source files (13 with `candidates`, 4 with `alternatives`, 1 with `bound`: `cn`, forms 0 and 2 bound to `packages/utils/src/cn.ts:4`). 202 signature-judge subagents, one per `files[]` entry, each read signature-comparison-rules.md in full and returned 0 mismatches and 0 `undecided` items; `score` graded 270/270 matching (Signature Accuracy 100%), Type Coverage 42/42.
- **Numerator ground truth (§2b):** skipped (no inflation signature: `stats.exports_documented` 315 ≠ `stats.effective_denominator` 327).
- **Stale names (§2c):** `UILibraryContextValue`, `add`, `fetchComponent` are documented names outside the `scope.include` set; `classify-stale` finds each still declared (`packages/components/react-shadcn/src/ui-library-provider.tsx:14`, `packages/uitripled/src/commands/add.ts:8`, `packages/uitripled/src/utils/registry.ts:5`), none scoped out: Info documented-extra observations.
- **Guards (§4):** deflation does not fire (327 re-derived against 327 stored, basis `scope.include`); inflation does not fire (3.81%); the stale-scope guard fires: `scope.include` globs `apps/docs/app/**/page.mdx` and `apps/docs/components/demos/**` match no file (Medium `brief-scope-stale`), restoring no name.
- **Metadata count cross-check (§4b):** Medium `metadata-drift` (stats.exports_public_api=445 against exports[].length=297, 33% drift) and Info `multi-denominator` (barrel 445, documented 315).
- **Provenance line check (§4c):** run (full access, map present, no drift): 0 `stale[]` items, so no `provenance-line` or `provenance-unverified` gap.

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)
**Migration Section:** Section 4b verification skipped: evidence-report.md pins no `t2_future_count`. For a skill create-skill made, re-run create-skill to regenerate the report with the field (create-stack-skill does not write it).

### Structural Findings

| # | Type | Severity | Detail | Line |
|---|------|----------|--------|------|

**Structural Issues:** 0

Checks run (`skf-scan-skill-md-structure.py` and `locate-export-segments.py`): §2.1 required sections all satisfied (`description` by `## Overview`, `usage` by `## Quick Start`, `api_surface` by `## Component Catalog`); §2.2 fences balanced (14 fences); §2.3 no bare opening fence; §2.4 all 199 function exports appear in the usage-family scope (body, sections and reference files; `zero_usage` empty); §2.5 one export is called in fenced code (`fetchComponent`, `export async function` at `references/catalog.md:111`, directly awaited), no async/sync mismatch; §2.6 no table drift; §2.7 no `scripts/` or `assets/` folder.

### Reference Consistency (split-body)

| # | Reference File | Export | Issue | Other Side | Reference Line | Contradicted Side |
|---|---------------|--------|-------|------------|---------------|-------------------|

**Exports Cross-Checked:** 90
**Mismatches Found:** 0

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

### Score Breakdown

| Category | Score | Weight | Weighted |
|----------|-------|--------|----------|
| Export Coverage | 100% | 45% | 45% |
| Signature Accuracy | 100% | 25% | 25% |
| Type Coverage | 100% | 20% | 20% |
| Coherence | not scored (naive mode) | 0% | 0% |
| External Validation | 100% | 10% | 10% |
| **Total** | | **100%** | **100%** |

### Result

**Score:** 100%
**Threshold:** 80%
**Result:** **PASS**

**Threshold Source:** workflow default (80%)
**Weight Distribution:** naive (redistributed)
**Tier Adjustment:** none
**External Validators:** skill-check only (from `skill-check`; Tessl Review is off)
**Analysis Confidence:** full
**Tooling Status:** ok

## Gap Report

**Total Gaps:** 6
**Blocking (Critical + High):** 0
**Non-blocking (Medium + Low + Info):** 6

### Remediation Summary

| Severity | Count | Estimated Effort |
|----------|-------|------------------|
| Critical | 0 | None |
| High | 0 | None |
| Medium | 2 | brief-scope-stale (1): edit the brief's stale scope globs by hand so each matches the files it meant, and add a `scope.include` glob over each restored file the skill documents (a `scope.exclude` one for each it leaves out), as each remediation says (Update Skill does not rewrite them); metadata-drift (1): re-run Create Skill or edit the brief's scope, as each remediation says (counts that differ only by `Type::method` entries need no fix, and a hand edit of the counts does not hold) |
| Low | 0 | None |
| Info | 4 | observation (3): apply each only when you agree, as its remediation says, since it is advisory (a documented extra needs no change); multi-denominator (1): none, since the barrel and the documented surface measure different sets by design |
| **Total** | **6** | |

### GAP-004: stale brief scope: scope.include globs match no source file

**Severity:** Medium
**Category:** Coverage (brief-scope-stale)
**Source:** forge-data/oms-uitripled/skill-brief.yaml

**Issue:** the `scope.include` globs `apps/docs/app/**/page.mdx`, `apps/docs/components/demos/**` match no file in the source tested; no root export was restored

**Remediation:** Edit `scope.include` in `forge-data/oms-uitripled/skill-brief.yaml` by hand so each glob matches the files it meant in this version of the source (update-skill does not rewrite an include glob).

### GAP-005: metadata drift — barrel export counts diverge

**Severity:** Medium
**Category:** Coverage (metadata-drift)
**Source:** skills/oms-uitripled/0.1.0/oms-uitripled/metadata.json

**Issue:** stats.exports_public_api=445, exports[].length=297 → 33% drift

**Remediation:** Re-run Create Skill, which rebuilds `exports[]` and `stats.exports_public_api` in `skills/oms-uitripled/0.1.0/oms-uitripled/metadata.json` from the source. Update Skill does not repair this drift: each time it writes the skill it recounts `stats.exports_public_api` from the source and keeps `exports[]`, adding or dropping only the names its provenance map changes, so a metadata patch does not hold.

### GAP-001: Documented extra: UILibraryContextValue

**Severity:** Info
**Category:** Structural (observation)
**Source:** packages/components/react-shadcn/src/ui-library-provider.tsx:14
**Export:** UILibraryContextValue

**Issue:** `references/setup.md:90` documents `UILibraryContextValue`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `UILibraryContextValue` is a documented extra, a name the source still declares at `packages/components/react-shadcn/src/ui-library-provider.tsx:14` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-002: Documented extra: add

**Severity:** Info
**Category:** Structural (observation)
**Source:** packages/uitripled/src/commands/add.ts:8
**Export:** add

**Issue:** `references/catalog.md:115` documents `add`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `add` is a documented extra, a name the source still declares at `packages/uitripled/src/commands/add.ts:8` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-003: Documented extra: fetchComponent

**Severity:** Info
**Category:** Structural (observation)
**Source:** packages/uitripled/src/utils/registry.ts:5
**Export:** fetchComponent

**Issue:** `SKILL.md:197` documents `fetchComponent`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `fetchComponent` is a documented extra, a name the source still declares at `packages/uitripled/src/utils/registry.ts:5` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-006: multi-denominator reporting — barrel vs documented surface

**Severity:** Info
**Category:** Coverage (multi-denominator)
**Source:** skills/oms-uitripled/0.1.0/oms-uitripled/metadata.json

**Issue:** barrel=445, documented=315

**Remediation:** No action required: the barrel and the documented surface measure different sets by design, and the report records both counts.

### Discovery Quality

**Discovery Test:** PASS (3/3)

| # | Prompt | Selected Skill | Result |
|---|--------|----------------|--------|
| 1 | can you help me throw together a landing page for my startup with some fancy animated sections, like a hero, a pricing table and testimonials, pulled in from that copy-paste component registry? | oms-uitripled (high) | PASS |
| 2 | why do the dashboard cards I copied in show the wrong colors when I switch to dark mode? did I miss some provider setup around the app? | oms-uitripled (medium) | PASS |
| 3 | run the add-a-component thing so I get an animated sign-in card and an FAQ accordion block dropped into my app | oms-uitripled (high) | PASS |

Catalog: 4 skills (`oms-cocoindex`, `oms-cognee`, `oms-storybook-react-vite`, `oms-uitripled`), each given as its name and frontmatter description. The prompts are synthesized (SKILL.md has no Triggers section or organic example prompt) and name no export, skill or library. Each went to an isolated subagent with no file or shell tools (the `web-fetch` agent type, WebFetch only; no tool was used), with no context about the skill under test.
