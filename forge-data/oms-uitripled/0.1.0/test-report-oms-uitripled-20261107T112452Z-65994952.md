---
workflowType: 'test-skill'
skillName: 'oms-uitripled'
skillDir: 'skills/oms-uitripled/0.1.0/oms-uitripled'
runId: '20261107T112452Z-65994952'
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
testDate: '2026-11-07T11:24:52Z'
stepsCompleted: ['init', 'detect-mode', 'coverage-check', 'coherence-check', 'external-validators', 'hard-gate', 'score', 'report']
nextWorkflow: 'export-skill'
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

**Mode Rationale:** metadata.json records `skill_type: "single"`, an individual skill, so the run takes Naive Mode: API-surface coverage, with a structural-only coherence check and no coherence category in scoring.

**Analysis Plan:**
- Coverage Check: every public export of the uitripled react-shadcn source at the pinned commit a5ffb45 is checked for documentation in SKILL.md and its references, with Deep-tier AST-backed signature and type comparison against the workspace clone.
- Coherence Check: structural only (naive mode): the references SKILL.md cites resolve and the examples are internally consistent; no cross-skill integration checks.

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
- root barrel: 29

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
| `GAP_VALUES` | - | yes | - | packages/components/react-shadcn/src/lib/grid-utils.ts:23 | PASS |
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
| `THEME_STORAGE_KEY` | - | yes | - | packages/components/react-shadcn/src/components/theme-provider.tsx:11 | PASS |
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
| `UILibraryProvider` | function | yes | yes | packages/components/react-shadcn/src/ui-library-provider.tsx:31 | PASS |
| `VerifiedBadge` | function | yes | yes | packages/components/react-shadcn/src/components/native/native-verified-badge-shadcnui.tsx:104 | PASS |
| `VerifiedBadgeOutline` | function | yes | yes | packages/components/react-shadcn/src/components/native/native-verified-badge-shadcnui.tsx:162 | PASS |
| `VerifiedShieldBadge` | function | yes | yes | packages/components/react-shadcn/src/components/native/native-verified-badge-shadcnui.tsx:247 | PASS |
| `VolumeComponent` | function | yes | yes | packages/components/react-shadcn/src/components/components/sliders/volume-component.tsx:17 | PASS |
| `WeatherDashboard` | function | yes | yes | packages/components/react-shadcn/src/components/components/weather/weather-dashboard.tsx:390 | PASS |
| `WebPerformancePage` | function | yes | yes | packages/components/react-shadcn/src/components/web-performance/web-performance-page.tsx:394 | PASS |
| `WizardForm` | function | yes | yes | packages/components/react-shadcn/src/components/forms/wizard-form.tsx:165 | PASS |
| `add` | - | yes | - | - | WARN |
| `badgeVariants` | const | yes | - | packages/components/react-shadcn/src/ui/badge.tsx:5 | PASS |
| `bentoPresets` | - | yes | - | packages/components/react-shadcn/src/lib/grid-presets.ts:7 | PASS |
| `buttonVariants` | const | yes | - | packages/components/react-shadcn/src/ui/button.tsx:6 | PASS |
| `cn` | - | yes | yes | packages/components/react-shadcn/src/lib/utils.ts:3 | PASS |
| `componentsRegistry` | - | yes | - | packages/registry/src/index.tsx:8 | PASS |
| `countSavedProjectComponents` | - | yes | yes | packages/utils/src/builder-utils.ts:70 | PASS |
| `createPage` | - | yes | yes | packages/utils/src/builder-utils.ts:33 | PASS |
| `extractSavedPages` | - | yes | yes | packages/utils/src/builder-utils.ts:52 | PASS |
| `fetchComponent` | - | yes | - | - | WARN |
| `generateGridCode` | - | yes | yes | packages/components/react-shadcn/src/lib/grid-utils.ts:47 | PASS |
| `generateUniqueSlug` | - | yes | yes | packages/utils/src/builder-utils.ts:14 | PASS |
| `getCellKey` | - | yes | yes | packages/components/react-shadcn/src/lib/grid-utils.ts:101 | PASS |
| `getGapSliderIndex` | - | yes | yes | packages/components/react-shadcn/src/lib/grid-utils.ts:32 | PASS |
| `getGapValueFromIndex` | - | yes | yes | packages/components/react-shadcn/src/lib/grid-utils.ts:40 | PASS |
| `initializeCells` | - | yes | yes | packages/components/react-shadcn/src/lib/grid-utils.ts:76 | PASS |
| `isCellInSelection` | - | yes | yes | packages/components/react-shadcn/src/lib/grid-utils.ts:106 | PASS |
| `mergeComponentImports` | - | yes | yes | packages/utils/src/merge-imports.ts:6 | PASS |
| `nativeComponents` | - | yes | - | packages/registry/src/registry/native.tsx:218 | PASS |
| `sanitizeSlug` | - | yes | yes | packages/utils/src/builder-utils.ts:7 | PASS |
| `uiComponents` | - | yes | - | packages/registry/src/registry/ui.tsx:179 | PASS |
| `uiLibraryLabels` | - | yes | - | packages/utils/src/types.ts:5 | PASS |
| `useTheme` | - | yes | yes | packages/components/react-shadcn/src/components/theme-provider.tsx:35 | PASS |
| `useUILibrary` | - | yes | yes | packages/components/react-shadcn/src/ui-library-provider.tsx:23 | PASS |

### Coverage Summary

- **Exports Found:** 327
- **Documented:** 327 (100%)
- **Missing Documentation:** 0
- **Signature Mismatches:** 0
- **Stale Documentation:** 2, documented extras included
- **Scoped Out by the Brief:** `NativeAvatarExpandDefault` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx:5), `NativeAvatarExpandDemo` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx:57), `NativeAvatarExpandExtraLarge` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx:37), `NativeAvatarExpandLarge` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx:25), `NativeAvatarExpandNoImage` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx:49), `NativeAvatarExpandSmall` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx:13), `NativeAvatarWithNameDefault` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx:5), `NativeAvatarWithNameDemo` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx:84), `NativeAvatarWithNameLarge` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx:64), `NativeAvatarWithNameLeft` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx:28), `NativeAvatarWithNameNoImage` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx:76), `NativeAvatarWithNameRight` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx:40), `NativeAvatarWithNameSmall` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx:52), `NativeAvatarWithNameTop` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx:16), `NativeButtonDefault` (packages/components/react-shadcn/src/components/native/demo/native-button-demo.tsx:5), `NativeButtonDisabled` (packages/components/react-shadcn/src/components/native/demo/native-button-demo.tsx:21), `NativeButtonGlow` (packages/components/react-shadcn/src/components/native/demo/native-button-demo.tsx:9), `NativeButtonLoading` (packages/components/react-shadcn/src/components/native/demo/native-button-demo.tsx:17), `NativeButtonOutline` (packages/components/react-shadcn/src/components/native/demo/native-button-demo.tsx:13), `NativeDeleteCustomText` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx:71), `NativeDeleteDefault` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx:6), `NativeDeleteDemo` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx:124), `NativeDeleteDisabled` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx:116), `NativeDeleteLarge` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx:49), `NativeDeleteNoIcon` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx:94), `NativeDeleteSmall` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx:27), `NativeDialogDemo` (packages/components/react-shadcn/src/components/native/demo/native-dialog-demo.tsx:14), `NativeHoverCardBordered` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:38), `NativeHoverCardCustomButton` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:130), `NativeHoverCardCustomButtonText` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:156), `NativeHoverCardDefault` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:7), `NativeHoverCardDemo` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:200), `NativeHoverCardExtraLarge` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:86), `NativeHoverCardGlass` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:22), `NativeHoverCardLarge` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:70), `NativeHoverCardMinimal` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:172), `NativeHoverCardNoDescription` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:116), `NativeHoverCardNoUsername` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:102), `NativeHoverCardSmall` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:54), `NativeHoverCardWithFallback` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:185), `NativeImageCheckboxDefault` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx:6), `NativeImageCheckboxDemo` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx:117), `NativeImageCheckboxExtraLarge` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx:50), `NativeImageCheckboxGrid` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx:79), `NativeImageCheckboxLarge` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx:35), `NativeImageCheckboxSelected` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx:65), `NativeImageCheckboxSmall` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx:20), `NativeLikesCounterDefault` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx:38), `NativeLikesCounterDemo` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx:131), `NativeLikesCounterGhost` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx:62), `NativeLikesCounterInteractive` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx:91), `NativeLikesCounterOutline` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx:54), `NativeLikesCounterSizes` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx:70), `NativeLikesCounterSubtle` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx:46), `NativeLiquidButtonCustomColor` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:136), `NativeLiquidButtonDefault` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:6), `NativeLiquidButtonDemo` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:146), `NativeLiquidButtonError` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:88), `NativeLiquidButtonGlow` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:24), `NativeLiquidButtonGradient` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:14), `NativeLiquidButtonLoading` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:68), `NativeLiquidButtonSizes` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:98), `NativeLiquidButtonSuccess` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:78), `NativeLiquidButtonVariants` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:117), `NativeLiquidButtonWave` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:34), `NativeLiquidButtonWithProgress` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:44), `NativeMagneticDefault` (packages/components/react-shadcn/src/components/native/demo/native-magnetic-demo.tsx:6), `NativeMagneticDemo` (packages/components/react-shadcn/src/components/native/demo/native-magnetic-demo.tsx:42), `NativeMagneticLink` (packages/components/react-shadcn/src/components/native/demo/native-magnetic-demo.tsx:16), `NativeMagneticStrong` (packages/components/react-shadcn/src/components/native/demo/native-magnetic-demo.tsx:30), `NativeMorphingButtonCustomIcon` (packages/components/react-shadcn/src/components/native/demo/native-morphing-button-demo.tsx:32), `NativeMorphingButtonDefault` (packages/components/react-shadcn/src/components/native/demo/native-morphing-button-demo.tsx:6), `NativeMorphingButtonDemo` (packages/components/react-shadcn/src/components/native/demo/native-morphing-button-demo.tsx:54), `NativeNestedListDemo` (packages/components/react-shadcn/src/components/native/demo/native-nested-list-demo.tsx:88), `NativeNotchDefault` (packages/components/react-shadcn/src/components/native/demo/native-notch-demo.tsx:6), `NativeNotchLeftAlign` (packages/components/react-shadcn/src/components/native/demo/native-notch-demo.tsx:37), `NativeNotchRelative` (packages/components/react-shadcn/src/components/native/demo/native-notch-demo.tsx:69), `NativeNotificationBellCustomIcon` (packages/components/react-shadcn/src/components/native/demo/native-notification-bell-demo.tsx:22), `NativeNotificationBellDefault` (packages/components/react-shadcn/src/components/native/demo/native-notification-bell-demo.tsx:6), `NativeNotificationBellDemo` (packages/components/react-shadcn/src/components/native/demo/native-notification-bell-demo.tsx:33), `NativeNotificationBellEmpty` (packages/components/react-shadcn/src/components/native/demo/native-notification-bell-demo.tsx:14), `NativeProfileNotchDefault` (packages/components/react-shadcn/src/components/native/demo/native-profile-notch-demo.tsx:5), `NativeProfileNotchOverlay` (packages/components/react-shadcn/src/components/native/demo/native-profile-notch-demo.tsx:37), `NativeStartNowCustomLabels` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:82), `NativeStartNowDefault` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:6), `NativeStartNowDemo` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:150), `NativeStartNowDisabled` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:95), `NativeStartNowGradient` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:16), `NativeStartNowHeartIcon` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:128), `NativeStartNowLarge` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:60), `NativeStartNowNoSparkles` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:71), `NativeStartNowOutline` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:38), `NativeStartNowRocketIcon` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:139), `NativeStartNowSmall` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:49), `NativeStartNowSolid` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:27), `NativeStartNowStarIcon` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:106), `NativeStartNowZapIcon` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:117), `NativeTabsDemo` (packages/components/react-shadcn/src/components/native/demo/native-tabs-demo.tsx:5), `NativeTooltipBlur` (packages/components/react-shadcn/src/components/native/demo/native-tooltip-demo.tsx:9), `NativeTooltipDemo` (packages/components/react-shadcn/src/components/native/demo/native-tooltip-demo.tsx:29), `NativeTooltipScale` (packages/components/react-shadcn/src/components/native/demo/native-tooltip-demo.tsx:19), `NativeTypewriterDefault` (packages/components/react-shadcn/src/components/native/demo/native-typewriter-demo.tsx:5), `NativeTypewriterDemo` (packages/components/react-shadcn/src/components/native/demo/native-typewriter-demo.tsx:46), `NativeTypewriterLoop` (packages/components/react-shadcn/src/components/native/demo/native-typewriter-demo.tsx:32), `NativeTypewriterMultiline` (packages/components/react-shadcn/src/components/native/demo/native-typewriter-demo.tsx:16), `NativeUserCardDemo` (packages/components/react-shadcn/src/components/native/demo/native-user-card-demo.tsx:5), `NativeVerifiedBadgeCustomIcon` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx:128), `NativeVerifiedBadgeDefault` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx:30), `NativeVerifiedBadgeDemo` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx:153), `NativeVerifiedBadgeOutlineVariants` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx:80), `NativeVerifiedBadgeShield` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx:93), `NativeVerifiedBadgeSizes` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx:53), `NativeVerifiedBadgeWithLabel` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx:40), `NativeVerifiedBadgeWithTooltip` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx:103), `SocialButtonsGlow` (packages/components/react-shadcn/src/components/native/demo/social-login-demo.tsx:23), `SocialButtonsScale` (packages/components/react-shadcn/src/components/native/demo/social-login-demo.tsx:14), `SocialButtonsShine` (packages/components/react-shadcn/src/components/native/demo/social-login-demo.tsx:33), `SocialButtonsSlide` (packages/components/react-shadcn/src/components/native/demo/social-login-demo.tsx:5)

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 100% |
| Signature Accuracy | 100% |
| Type Coverage | 100% |

### Coverage Notes

- **Inventory and judges (how the run was batched).** This session had no subagent tool, so the main thread did every subagent's work, as coverage-check.md §1 and §2 allow. It read SKILL.md and all nine reference files (SKILL.md's `## Full` headings only point to them), wrote the documented inventory (702 entries, 329 names) and validated it: the schema check, the spot-check and the floor check of 276 names passed. The §1b split-body cross-check found no mismatch. It then judged all 269 planned signature comparisons over 202 source files in one batch, by the installed `references/signature-comparison-rules.md` with no added rule, and saved the result as `signatures-1.txt`. No comparison is a mismatch.
- **Files read by eye.** ast-grep reported syntax errors in 10 files, so the run read them by eye: `components/components/blog/blog-typography.tsx`, `components/components/course-content/course-content-page.tsx`, `components/components/profile/profile-page.tsx`, `components/components/resumes/shadcnui/professional-resume.tsx`, `components/components/weather/weather-dashboard.tsx`, `components/sections/bento-grid-block.tsx`, `components/sections/cinema-ticket.tsx`, `components/sections/conference-ticket.tsx`, `components/sections/glassmorphism-portfolio-block.tsx` and `components/sections/notion-blog-page.tsx`, all under `packages/components/react-shadcn/src/`. Each file exports one function, and its per-file result went back to `surface` once. No file was left unread (`extraction.unread` is empty).
- **Extraction gaps.** No recipe found 22 names, but they are on the surface, and the run read each declaration at its file and line. The 15 that carry a documented form were compared, and all match: `cn`, `useTheme`, `useUILibrary`, the six grid helpers, the five builder helpers and `mergeComponentImports`. The other 7 are data constants with no documented form: `GAP_VALUES`, `THEME_STORAGE_KEY`, `bentoPresets`, `componentsRegistry`, `nativeComponents`, `uiComponents` and `uiLibraryLabels`.
- **Stale names (documented extras).** The source still defines `add` (`packages/uitripled/src/commands/add.ts:8`) and `fetchComponent` (`packages/uitripled/src/utils/registry.ts:5`), but they are not on the counted surface. Each is recorded as an Info observation. Their documented signatures in `references/catalog.md:L110-111` agree with those declarations, but they are outside the signature universe, so they are not scored.
- **Guards.** The stale-scope guard fires: the `scope.include` globs `apps/docs/app/**/page.mdx` and `apps/docs/components/demos/**` match no file, which is a Medium `brief-scope-stale` gap. The deflation guard (327 against 327) and the inflation guard (3.81%) do not fire.
- **Metadata count cross-check.** It records a Medium metadata drift (`stats.exports_public_api` 445 against `exports[].length` 297, 33%) and an Info multi-denominator note (445 against 315 documented).
- **Numerator ground truth.** Skipped: there is no inflation signature, because `stats.exports_documented` (315) differs from `stats.effective_denominator` (327).
- **Provenance line check.** It checked 315 map entries and found no stale line.
- **Inventory judgment (not a signature rule).** The inventory counts `Button`, `Card`, `CardContent`, `CardHeader`, `Input`, `Dialog` and `DialogContent` as documented. Their only documentation is the import lines at `references/integration.md:L38-41`, plus `references/ui-primitives.md:L3`, which points to those lines as their documentation. They have no signature form and no purpose row, and `references/inventory-contract.md` ("every export the skill documents") does not say whether an import line documents a name. Counted as documented, they are 7 of the 327 names. Without them, Export Coverage would be 320/327 = 97.86%.
- **Borderline signature call: a `—` Default cell.** In the props tables at `references/setup.md:L30` (ThemeProvider) and `references/setup.md:L70` (UILibraryProvider), the Default cell of the `children` row is `—`. The deciding source lines declare `children` required: `packages/components/react-shadcn/src/components/theme-provider.tsx:L14` (`children: ReactNode;` in `ThemeProviderProps`) and `packages/components/react-shadcn/src/ui-library-provider.tsx:L31` (`{ children }: { children: React.ReactNode }`). The rules file says: "A Default cell with a value marks only its own row optional and an empty one states nothing". It does not say whether `—` is a value or an empty cell. The run counted `—` as an empty cell that states nothing, so both forms match. Had `—` been read as a value, it would mark `children` optional, which the source contradicts, and the run would record two Critical `signature-mismatch` gaps: ThemeProvider form 0 and UILibraryProvider form 0. This report records the call.
- **Rest elements (SKF #932), settled.** `NativeButton` (`references/native-components.md:L37` against `native-button-shadcnui.tsx:L15`), `NativeLiquidButton` (`:L62` against `native-liquid-button-shadcnui.tsx:L61`) and `SocialLoginButton` (`:L93` against `social-login-button-shadcnui.tsx:L57`) write `...props` in their destructured props form. The 8.0.0 rule decides these calls: "A rest element in a component's destructured props form ... stands for every prop of P the form does not name, own or inherited, required ones included". All three match, so they are not borderline.
- **Same-named exports.** Two names belong to two different exports each. `GridCell` is a component in `components/grid/grid-cell.tsx` and an interface in both `grid-utils.ts` files. `PasswordInput` is a function in `components/inputs/password-input.tsx` and a forwardRef in `ui/password-input.tsx`. The inventory gives each name one kind, as the contract asks. The signature check offered every declaring file as a candidate.

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)
**Migration Section:** Section 4b verification skipped: evidence-report.md pins no `t2_future_count`. For a skill create-skill made, re-run create-skill to regenerate the report with the field (create-stack-skill does not write it).

### Structural Findings

| # | Type | Severity | Detail | Line |
|---|------|----------|--------|------|
| - | none | - | No structural issue. §2.1: every required family is satisfied (description by `Overview`, usage by `Quick Start`, API surface by `Component Catalog`). §2.2: the 14 fences are balanced. §2.3: no opening fence lacks a language tag. §2.4: none of the 214 function exports in the usage scope (Quick Start, Common Workflows and the 9 reference files) has zero uses. §2.5: two exports have calls in an example, and they agree with their descriptions: `fetchComponent` is async and awaited at `references/catalog.md:123`; `generateGridCode` is sync and not awaited at `references/utils.md:103`. §2.6: no table row's column count drifts from its header. §2.7: there is no `scripts/` or `assets/` folder. | - |

**Structural Issues:** 0

### Reference Consistency (split-body)

| # | Reference File | Export | Issue | Other Side | Reference Line | Contradicted Side |
|---|---------------|--------|-------|------------|---------------|-------------------|
| - | - | - | No split-body mismatch: coverage-check §1b compared the forms of every export documented in more than one file and found none that contradict. | - | - | - |

**Exports Cross-Checked:** 88 (inventory names written in two or more of the package's 10 files)
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
**External Validators:** skill-check only
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
| Medium | 2 | Add type definitions, interface docs or the missing section |
| Low | 0 | None |
| Info | 4 | Optional improvements, no action required |
| **Total** | **6** | |

### GAP-003: stale brief scope: scope.include globs match no source file

**Severity:** Medium
**Category:** Coverage (brief-scope-stale)
**Source:** forge-data/oms-uitripled/skill-brief.yaml

**Issue:** the `scope.include` globs `apps/docs/app/**/page.mdx`, `apps/docs/components/demos/**` match no file in the source tested; no root export was restored

**Remediation:** Edit `scope.include` in `forge-data/oms-uitripled/skill-brief.yaml` by hand so each glob matches the files it meant in this version of the source (update-skill does not rewrite an include glob), and add to `scope.exclude` any restored file the brief meant to leave out.

### GAP-004: metadata drift — barrel export counts diverge

**Severity:** Medium
**Category:** Coverage (metadata-drift)
**Source:** skills/oms-uitripled/0.1.0/oms-uitripled/metadata.json

**Issue:** stats.exports_public_api=445, exports[].length=297 → 33% drift

**Remediation:** Re-run Create Skill, which rebuilds `exports[]` and `stats.exports_public_api` in `skills/oms-uitripled/0.1.0/oms-uitripled/metadata.json` from the source. Update Skill does not repair this drift: each time it writes the skill it recounts `stats.exports_public_api` from the source and keeps `exports[]`, adding or dropping only the names its provenance map changes, so a metadata patch does not hold.

### GAP-001: Documented extra: add

**Severity:** Info
**Category:** Structural (observation)
**Source:** packages/uitripled/src/commands/add.ts:8
**Export:** add

**Issue:** `references/catalog.md:110` documents `add`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `add` is a documented extra, a name the source still declares at `packages/uitripled/src/commands/add.ts:8` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-002: Documented extra: fetchComponent

**Severity:** Info
**Category:** Structural (observation)
**Source:** packages/uitripled/src/utils/registry.ts:5
**Export:** fetchComponent

**Issue:** `references/catalog.md:111` documents `fetchComponent`, which the enumerated source API surface lacks and the source still declares

**Remediation:** No change: `fetchComponent` is a documented extra, a name the source still declares at `packages/uitripled/src/utils/registry.ts:5` outside the enumerated surface, and its documentation stays. Its documented signature was not checked against that declaration.

### GAP-005: multi-denominator reporting — barrel vs documented surface

**Severity:** Info
**Category:** Coverage (multi-denominator)
**Source:** skills/oms-uitripled/0.1.0/oms-uitripled/metadata.json

**Issue:** barrel=445, documented=315

**Remediation:** No action required: the barrel and the documented surface measure different sets by design, and the report records both counts.

### GAP-006: Discovery testing not performed: subagents unavailable, routing test requires isolated context

**Severity:** Info
**Category:** Discovery (discovery)
**Source:** SKILL.md:3

**Issue:** The discovery catalog holds 4 skills, but this session could not spawn subagents, and the main thread knows the skill under test, so the routing test was not run and is neither PASS nor FAIL.

**Remediation:** Re-run test-skill for oms-uitripled in an environment that can spawn subagents, so the three routing prompts run in isolated context against the 4-skill catalog in skills/ (oms-cocoindex, oms-cognee, oms-storybook-react-vite, oms-uitripled); no change to SKILL.md is implied.

### Discovery Quality

**Discovery Test:** skipped: subagents unavailable, routing test requires isolated context

discovery: skipped, subagents unavailable, routing test requires isolated context (the catalog holds 4 skills; the main thread knows the skill under test, so it did not answer the routing itself)
