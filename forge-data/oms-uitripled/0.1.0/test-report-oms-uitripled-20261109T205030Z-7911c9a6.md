---
workflowType: 'test-skill'
skillName: 'oms-uitripled'
skillDir: 'skills/oms-uitripled/0.1.0/oms-uitripled'
runId: '20261109T205030Z-7911c9a6'
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
testDate: '2026-11-09T20:50:30Z'
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

**Mode Rationale:** metadata.json records `skill_type: "single"`, an individual skill, so the test runs in naive mode: API-surface coverage, with a structural-only coherence check and no coherence category in the score.

**Analysis Plan:**
- Coverage Check: every public export the skill documents and the source exports, checked at Deep tier against the pinned source (a5ffb45) with AST-backed signature comparison through the inventory reader and the signature judges.
- Coherence Check: structural only (naive mode): references named in SKILL.md resolve and the skill's sections are present.

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
  - `GridCell` (references/motion-components.md:229), inventory reader: The skill documents two GridCell exports, the Grid Generator component (motion-components.md:229 and :243) and the grid-utils interface (utils.md:65, types.md:122); keeping one kind per name, every GridCell entry is kind function, as the floor's only origin (the component row at motion-components.md:243) is the component, and the interface entries carry their four fields and no params; left open by: A name documented in several places is listed once per place, each entry with that place's form (`Card` above), and once per form at a place that writes several of its forms (two overloads in one row), each entry with that place as its `at`, never as one entry whose list `params` gives a form per item (the validator refuses a list of two or more items when one item holds several parameters or a whole form, or two items name the same parameter), and keeps one `kind` in every place; the other reading gives: kind interface on every GridCell entry, or one kind per declaration: the component form would sit on an interface entry but still matches the GridCell component, so no signature gap either way; a kind check reading the interface entries' function kind against the interface declaration could flag a kind difference
  - `GridCell` (references/motion-components.md:229), inventory reader: Two declarations: the component form's citations (motion-components.md:238 and :243) name components/grid/grid-cell.tsx, the interface's (types.md:137, utils.md's Grid helpers Source) name packages/utils/src/grid-utils.ts, and motion-components.md:238 calls the component a different export from the GridCell interface; so the component form is never paired with the interface forms (which agree field for field) and no cross_check_mismatches entry is recorded; left open by: A judge without the surface (coverage-check.md §1's reader) counts two declarations only when the two forms' own citations name two different files and the skill presents the forms as different things (another owner, module or import path); a citation of a re-export (a package `__init__` or index file the skill shows passing the name on) names no declaration, and when unsure the forms are compared as before; the other reading gives: a split-body mismatch: the interface fields row, col, rowSpan, colSpan against the component props cell, cols, rows, isInSelection, onPointerDown, onPointerEnter
  - `PasswordInput` (references/motion-components.md:140), inventory reader: ui-primitives.md:179 describes a different PasswordInput (src/ui/password-input.tsx, a forwardRef over PasswordInputProps, cited there) from the one motion-components.md:140 declares with no props (cited at components/inputs/password-input.tsx); the citations name two files and the skill calls them different, so they are two declarations never compared, and that prose, which writes no form and which the floor does not give, adds no entry; left open by: A judge without the surface (coverage-check.md §1's reader) counts two declarations only when the two forms' own citations name two different files and the skill presents the forms as different things (another owner, module or import path); a citation of a re-export (a package `__init__` or index file the skill shows passing the name on) names no declaration, and when unsure the forms are compared as before; the other reading gives: a split-body mismatch (PasswordInput() taking no props against a component taking PasswordInputProps), or an extra entry at references/ui-primitives.md:179
  - `NativeButton` (references/native-components.md:37), inventory reader: The const is bound to an arrow whose parameter list the skill writes (a destructured props object); the const-component sentence names a wrapper call or an alias, so the const-function sentence ("bound to an arrow ... carries the function form the skill writes for it as `params`") decides: params holds the destructured props as written, no usage_signature; left open by: A `const` holding a component (a `forwardRef`, `memo` or other wrapper call, or an alias like `const Tabs = TabsPrimitive.Root`) is a `constant` with the declaration or usage form the skill writes as `usage_signature`; a data constant carries no `usage_signature`, `params` or `return_type`; the other reading gives: the whole declaration in usage_signature instead of params; both read the same props against the component, so no gap
  - `NativeTooltip` (references/native-components.md:80), inventory reader: The const is bound to an arrow whose parameter list the skill writes (a destructured props object); the const-component sentence names a wrapper call or an alias, so the const-function sentence ("bound to an arrow ... carries the function form the skill writes for it as `params`") decides: params holds the destructured props as written, no usage_signature; left open by: A `const` holding a component (a `forwardRef`, `memo` or other wrapper call, or an alias like `const Tabs = TabsPrimitive.Root`) is a `constant` with the declaration or usage form the skill writes as `usage_signature`; a data constant carries no `usage_signature`, `params` or `return_type`; the other reading gives: the whole declaration in usage_signature instead of params; both read the same props against the component, so no gap
  - `NativeTooltipProvider` (references/native-components.md:82), inventory reader: The const is bound to an arrow whose parameter list the skill writes (a destructured props object); the const-component sentence names a wrapper call or an alias, so the const-function sentence ("bound to an arrow ... carries the function form the skill writes for it as `params`") decides: params holds the destructured props as written, no usage_signature; left open by: A `const` holding a component (a `forwardRef`, `memo` or other wrapper call, or an alias like `const Tabs = TabsPrimitive.Root`) is a `constant` with the declaration or usage form the skill writes as `usage_signature`; a data constant carries no `usage_signature`, `params` or `return_type`; the other reading gives: the whole declaration in usage_signature instead of params; both read the same props against the component, so no gap
  - `SocialLoginButton` (references/native-components.md:93), inventory reader: The const is bound to an arrow whose parameter list the skill writes (a destructured props object); the const-component sentence names a wrapper call or an alias, so the const-function sentence ("bound to an arrow ... carries the function form the skill writes for it as `params`") decides: params holds the destructured props as written, no usage_signature; left open by: A `const` holding a component (a `forwardRef`, `memo` or other wrapper call, or an alias like `const Tabs = TabsPrimitive.Root`) is a `constant` with the declaration or usage form the skill writes as `usage_signature`; a data constant carries no `usage_signature`, `params` or `return_type`; the other reading gives: the whole declaration in usage_signature instead of params; both read the same props against the component, so no gap
  - `DialogFooter` (references/ui-primitives.md:55), inventory reader: The const is bound to an arrow whose parameter list the skill writes (a destructured props object); the const-component sentence names a wrapper call or an alias, so the const-function sentence ("bound to an arrow ... carries the function form the skill writes for it as `params`") decides: params holds the destructured props as written, no usage_signature; left open by: A `const` holding a component (a `forwardRef`, `memo` or other wrapper call, or an alias like `const Tabs = TabsPrimitive.Root`) is a `constant` with the declaration or usage form the skill writes as `usage_signature`; a data constant carries no `usage_signature`, `params` or `return_type`; the other reading gives: the whole declaration in usage_signature instead of params; both read the same props against the component, so no gap
  - `DialogHeader` (references/ui-primitives.md:56), inventory reader: The const is bound to an arrow whose parameter list the skill writes (a destructured props object); the const-component sentence names a wrapper call or an alias, so the const-function sentence ("bound to an arrow ... carries the function form the skill writes for it as `params`") decides: params holds the destructured props as written, no usage_signature; left open by: A `const` holding a component (a `forwardRef`, `memo` or other wrapper call, or an alias like `const Tabs = TabsPrimitive.Root`) is a `constant` with the declaration or usage form the skill writes as `usage_signature`; a data constant carries no `usage_signature`, `params` or `return_type`; the other reading gives: the whole declaration in usage_signature instead of params; both read the same props against the component, so no gap
  - `DropdownMenuShortcut` (references/ui-primitives.md:72), inventory reader: The const is bound to an arrow whose parameter list the skill writes (a destructured props object); the const-component sentence names a wrapper call or an alias, so the const-function sentence ("bound to an arrow ... carries the function form the skill writes for it as `params`") decides: params holds the destructured props as written, no usage_signature; left open by: A `const` holding a component (a `forwardRef`, `memo` or other wrapper call, or an alias like `const Tabs = TabsPrimitive.Root`) is a `constant` with the declaration or usage form the skill writes as `usage_signature`; a data constant carries no `usage_signature`, `params` or `return_type`; the other reading gives: the whole declaration in usage_signature instead of params; both read the same props against the component, so no gap
  - `LiquidCursor` (references/motion-components.md:142), inventory reader: The const is bound to an arrow whose parameter list the skill writes (`() => …`); the const-component sentence names a wrapper call or an alias, so the const-function sentence ("bound to an arrow ... carries the function form the skill writes for it as `params`") decides: params `[]`, no usage_signature; left open by: A `const` holding a component (a `forwardRef`, `memo` or other wrapper call, or an alias like `const Tabs = TabsPrimitive.Root`) is a `constant` with the declaration or usage form the skill writes as `usage_signature`; a data constant carries no `usage_signature`, `params` or `return_type`; the other reading gives: the whole declaration in usage_signature instead of params; both read the same props (none) against the component, so no gap
  - `BrowseFolder` (references/blocks-and-sections.md:41), inventory reader: The const is bound to an arrow whose parameter list the skill writes (`() => …`); the const-component sentence names a wrapper call or an alias, so the const-function sentence ("bound to an arrow ... carries the function form the skill writes for it as `params`") decides: params `[]`, no usage_signature; left open by: A `const` holding a component (a `forwardRef`, `memo` or other wrapper call, or an alias like `const Tabs = TabsPrimitive.Root`) is a `constant` with the declaration or usage form the skill writes as `usage_signature`; a data constant carries no `usage_signature`, `params` or `return_type`; the other reading gives: the whole declaration in usage_signature instead of params; both read the same props (none) against the component, so no gap
  - `Avatar` (references/ui-primitives.md:38), inventory reader: In each `const X = React.forwardRef<...>(…)` declaration the `…` is forwardRef's argument of its own, standing in for the omitted render function, so the entry copies signature_form partial; the same reading gives partial to the other 31 forwardRef declarations (AvatarFallback, AvatarImage, CardDescription, CardFooter, CardTitle, Checkbox, DialogDescription, DialogOverlay, DialogTitle, DropdownMenuCheckboxItem, DropdownMenuContent, DropdownMenuItem, DropdownMenuLabel, DropdownMenuRadioItem, DropdownMenuSeparator, DropdownMenuSubContent, DropdownMenuSubTrigger, Label, ScrollArea, ScrollBar, Separator, Slider, Switch, TabsContent, TabsList, TabsTrigger, Textarea, TooltipContent, NativeDialogContent, NativeDialogOverlay, NativeTooltipContent); the `=> …` of the arrow consts is a body, not a member or argument, so labels nothing; left open by: An entry whose signature the skill labels partial (simplified, key parameters, a `...` standing in for omitted members as a member or argument of its own, not rest or variadic syntax nor an argument's value such as `api_key=...`; a label in a table's column header, such as `Props (simplified)`, labels each of its rows, every form their cells write included, a usage form or another name's form among them, but only as the whole header, `Key params`, or in parentheses after its word, as inventory-floor.json reads one, so `Purpose and key params` labels none) carries `signature_form: "partial"`, any other `"full"` or no key, and a form that writes only a `return_type` carries none: copy the label, never judge the form; the other reading gives: signature_form full or no key: the ellipsis claims nothing and the props type in the type arguments is read either way, so no gap
  - `GridPreviewProps` (references/types.md:222), inventory reader: The floor's heading origin (### `GridPreviewProps`) gives an entry with no fields, and the fenced `export interface GridPreviewProps {` below it (types.md:227) is a place of its own giving the entry with the fields; the same two entries are given for the other 18 floor heading names of types.md's Component props types (BadgeProps, ButtonProps, InputProps, LabelProps, NativeAvatarExpandProps, NativeAvatarProps, NativeButtonProps, NativeCounterUpProps, NativeDeleteProps, NativeHoverCardProps, NativeImageCheckboxProps, NativeLiquidButtonProps, NativeMagneticProps, NativeNotificationBellProps, NativeProfileNotchProps, NativeStartNowProps, PasswordInputProps, TextareaProps); left open by: A place that writes a name but no form of it, and no `methods`, `properties` or `fields` its entry would carry (a mention, a bare code span, an import, a heading or prose that names or describes it), gives it no entry when another place gives the name one, unless `inventory-floor.json` gives that place; of several such places of a name the skill documents and no other place gives an entry, the first alone gives one: in SKILL.md, else the file that sorts first by path, at its lowest line; the other reading gives: one entry at the heading carrying the declaration's fields; no compared form either way, so no gap
  - `badgeVariants` (references/ui-primitives.md:118), inventory reader: Badge's Purpose cell writes `badgeVariants({ variant })`, a call of the const's own name that passes an argument, so it is a badgeVariants usage at that row, besides the floor row at ui-primitives.md:119; the `const badgeVariants = cva(…)` line, the factory's form, gives no entry; left open by: A `const` whose value is a function (annotated with a function type, bound to an arrow, a `function` or a call that returns one, or written with a parameter list) carries the function form the skill writes for it as `params` (`[]`, never `""`, when it takes none) and `return_type`, whatever its kind (`constant` for the skill's `const` label), wherever the skill writes it, a description cell included, except a call expression of its name, which is recorded in `usage_signature` as a function's is (above); a bare `name()` there is still a mention; only a constant holding neither a component nor a function is a data constant; the other reading gives: a description of Badge giving badgeVariants no entry there; the call passes one props object to the function cva returns, so no gap either way
  - `sanitizeSlug` (references/utils.md:53), inventory reader: The prose on generateUniqueSlug writes `const baseSlug = sanitizeSlug(baseName) || "page"`, a call after an assignment that passes one argument, so it is recorded as a sanitizeSlug usage through the call's closing parenthesis; left open by: A function's, a method's or a class's form the skill writes as a call expression of its own name (after `await`, `new` or an assignment, through a receiver or module path such as `coco.`, or as a statement in a fenced example; in running text or a description cell, only a call that passes an argument and writes no parameter type, `?`, bare `*` or `/`, with or without such a prefix, and no return type unless such a prefix comes before the name, such as `add(componentName, options)` or `await coco.mount(fn) -> Handle`), at a place `inventory-floor.json` gives no `signature` (below), is recorded whole in `usage_signature`, as `inventory-floor.json` writes a usage (an assignment, `await`, `new`, a receiver or module path before the name kept, through the call's closing parenthesis or the element's end, never an `@`, a `with` or text after the call), never in `params`, whatever names its arguments use, and a return type the skill writes for it in `return_type`, while a class's form written as a parameter list or a signature that is not such a call stays in `params` (`Note` above, written in a Signature cell): signature-comparison-rules.md reads a usage as a call and a list of bare names in `params` as parameter names; the other reading gives: a code note on generateUniqueSlug giving no entry; the call passes the one parameter value: string, so no gap either way
  - `cn` (SKILL.md:106), inventory reader: `cn(className, "extra-classes")` is a call passing arguments in running text, so it is a cn usage, although the sentence says this cn comes from your project's @/lib/utils (the helper npx shadcn init writes) rather than from @uitripled/utils; left open by: A function's, a method's or a class's form the skill writes as a call expression of its own name (after `await`, `new` or an assignment, through a receiver or module path such as `coco.`, or as a statement in a fenced example; in running text or a description cell, only a call that passes an argument and writes no parameter type, `?`, bare `*` or `/`, with or without such a prefix, and no return type unless such a prefix comes before the name, such as `add(componentName, options)` or `await coco.mount(fn) -> Handle`), at a place `inventory-floor.json` gives no `signature` (below), is recorded whole in `usage_signature`, as `inventory-floor.json` writes a usage (an assignment, `await`, `new`, a receiver or module path before the name kept, through the call's closing parenthesis or the element's end, never an `@`, a `with` or text after the call), never in `params`, whatever names its arguments use, and a return type the skill writes for it in `return_type`, while a class's form written as a parameter list or a signature that is not such a call stays in `params` (`Note` above, written in a Signature cell): signature-comparison-rules.md reads a usage as a call and a list of bare names in `params` as parameter names; the other reading gives: no entry, the project's own helper not being a uitripled export; either way the call matches the variadic `...inputs: ClassValue[]`, so no gap
  - `useUILibrary` (references/setup.md:82), inventory reader: The **Return type** block under the same heading (setup.md:87-93) is the return type the skill writes for the usage, so the usage entry carries return_type UILibraryContextValue; left open by: A function's, a method's or a class's form the skill writes as a call expression of its own name (after `await`, `new` or an assignment, through a receiver or module path such as `coco.`, or as a statement in a fenced example; in running text or a description cell, only a call that passes an argument and writes no parameter type, `?`, bare `*` or `/`, with or without such a prefix, and no return type unless such a prefix comes before the name, such as `add(componentName, options)` or `await coco.mount(fn) -> Handle`), at a place `inventory-floor.json` gives no `signature` (below), is recorded whole in `usage_signature`, as `inventory-floor.json` writes a usage (an assignment, `await`, `new`, a receiver or module path before the name kept, through the call's closing parenthesis or the element's end, never an `@`, a `with` or text after the call), never in `params`, whatever names its arguments use, and a return type the skill writes for it in `return_type`, while a class's form written as a parameter list or a signature that is not such a call stays in `params` (`Note` above, written in a Signature cell): signature-comparison-rules.md reads a usage as a call and a list of bare names in `params` as parameter names; the other reading gives: no return_type on the usage (or a separate entry with only that return_type and no at): if the source hook declares another return type, the return_type this reading records could give a Critical signature-mismatch the other reading would not
  - `UILibraryContextValue` (references/setup.md:90), inventory reader: useUILibrary's Return type block writes the name as a fenced `type UILibraryContextValue = {...}` declaration, outside a type position, so it gets a type entry with its two fields; left open by: A name the skill writes only in a type position (a parameter type, a return type or a type argument inside another entry's documented type or signature, or a parameter table's Type cell) is a type mention, not an export the skill documents, even when its code span is exactly the name, and gets no entry, unless the skill also writes it as one outside a type position: a place `inventory-floor.json` gives it, a heading, an export table's first cell, a code span that is the name or the name then `(`, or a fenced declaration; the other reading gives: a type mention of the hook's return giving no entry; if the source exports no type by that name, this reading's entry is a stale-name gap
  - `setSelectedLibrary`, inventory reader: `setSelectedLibrary(library)` (setup.md:85) and `setSelectedLibrary("react")` (setup.md:96, types.md:33) call a member of useUILibrary's destructured return value, with no receiver and no class the skill documents with that member, so it gets no method or function entry; it is recorded as a field of UILibraryContextValue; left open by: A method a place writes with a form of its own (a class body, a methods list, a row's cell, running text) gets a `method` entry there with that form, a call recorded in `usage_signature` as a function's is (`execute(args, kwargs, next_batch_size=None)` in a methods list), besides its class's `methods` item, and so does one the skill calls through an instance or the class it documents with that member (`builder.provide(KEY, value)`, `canvas.getByRole('button')`), the class as `owner` and the call in `usage_signature`, never a usage of a same-named function; the other reading gives: a function or method entry with usage_signature setSelectedLibrary(library), a name the source does not export: a stale-name or unbound-form gap
  - `toggleTheme`, inventory reader: toggleTheme, written only as `toggleTheme()` mentions (SKILL.md:103, setup.md:51) and in useTheme's destructuring, is a member of useTheme's return value, not an export the skill documents, so it gets no entry; left open by: A place that writes a name but no form of it, and no `methods`, `properties` or `fields` its entry would carry (a mention, a bare code span, an import, a heading or prose that names or describes it), gives it no entry when another place gives the name one, unless `inventory-floor.json` gives that place; of several such places of a name the skill documents and no other place gives an entry, the first alone gives one: in SKILL.md, else the file that sorts first by path, at its lowest line; the other reading gives: one entry at SKILL.md:103 with no form, a name the source does not export: a stale-name gap
  - `Card` (SKILL.md:156), inventory reader: Card and Dialog, which no place gives a form, take their one entry from the first place that names them: the prose list `Button, Card, Dialog, etc.` at SKILL.md:156, prose that names them; left open by: A place that writes a name but no form of it, and no `methods`, `properties` or `fields` its entry would carry (a mention, a bare code span, an import, a heading or prose that names or describes it), gives it no entry when another place gives the name one, unless `inventory-floor.json` gives that place; of several such places of a name the skill documents and no other place gives an entry, the first alone gives one: in SKILL.md, else the file that sorts first by path, at its lowest line; the other reading gives: if only a code span or an import counts, the entries move to references/integration.md:39 (Card) and :41 (Dialog); no compared form, so no gap, only another cited line
  - `Input` (references/catalog.md:71), inventory reader: Input, which no place gives a form, takes its one entry from the first place that names it: catalog.md:71's description cell (shadcn/ui primitives — Button, Card, Dialog, Input, Label, etc.), which sorts before the import at integration.md:40 and the code span at ui-primitives.md:3; left open by: A place that writes a name but no form of it, and no `methods`, `properties` or `fields` its entry would carry (a mention, a bare code span, an import, a heading or prose that names or describes it), gives it no entry when another place gives the name one, unless `inventory-floor.json` gives that place; of several such places of a name the skill documents and no other place gives an entry, the first alone gives one: in SKILL.md, else the file that sorts first by path, at its lowest line; the other reading gives: the entry at references/integration.md:40 (an import) or references/ui-primitives.md:3 (the first code span); no compared form, so no gap
  - `Button` (SKILL.md:41), inventory reader: The skill writes no kind or declaration for Button, Card, CardContent, CardHeader, Dialog, DialogContent or Input; they take kind constant, as the sibling src/ui/ primitives the skill declares with const (CardTitle, DialogTitle, ...); left open by: The contract `validate-inventory.py` checks (coverage-check.md §1a): each `kind` is one of `function`, `class`, `type`, `constant`, `hook`, `interface`, `method`, `struct`, `enum`, `trait`, `macro` or `adapter`; every entry carries the `description` the skill gives it (an empty string when it gives none); a function or method carries `params` (`""` or `[]` when it takes none; any list `params` holds the members of one parameter list, one per item, never one form per item) and `return_type` as the skill documents them, and leaves a key out when the skill documents nothing for it; the other reading gives: kind function; no compared form, so no gap unless a kind check reads it
  - `ThemeProvider` (references/setup.md:11), inventory reader: The skill writes no declaration or kind for ThemeProvider or UILibraryProvider, only props tables under their headings; both take kind function (a component taking one props object); left open by: The contract `validate-inventory.py` checks (coverage-check.md §1a): each `kind` is one of `function`, `class`, `type`, `constant`, `hook`, `interface`, `method`, `struct`, `enum`, `trait`, `macro` or `adapter`; every entry carries the `description` the skill gives it (an empty string when it gives none); a function or method carries `params` (`""` or `[]` when it takes none; any list `params` holds the members of one parameter list, one per item, never one form per item) and `return_type` as the skill documents them, and leaves a key out when the skill documents nothing for it; the other reading gives: kind constant; the props table is compared as the component's props either way, so no gap
  - `AIGlowInputProps`, inventory reader: The code span `AIGlowInputProps` at references/motion-components.md:29 names a props type that references/types.md does not list, and the file's Install and import paragraph says "a props type the signature names and that file does not list is not exported by the source": the skill says the source does not export it, so the code span gives no entry; left open by: A name the skill presents only as a local import alias of another name, or says the source does not export, is not an export the skill documents either: it gets an entry only from a place `inventory-floor.json` gives it, a heading, an export table's first cell or a fenced declaration of it (an import is not one), never from a code span in prose or a description cell; the other reading gives: an entry at references/motion-components.md:29 for a name the source does not export: a stale-name gap
  - `NativeFlipTextProps`, inventory reader: The code span `NativeFlipTextProps` at references/native-components.md:113 names a props type that references/types.md does not list, and the file's Install and import paragraph says "a props type the signature names and that file does not list is not exported by the source": the skill says the source does not export it, so the code span gives no entry; left open by: A name the skill presents only as a local import alias of another name, or says the source does not export, is not an export the skill documents either: it gets an entry only from a place `inventory-floor.json` gives it, a heading, an export table's first cell or a fenced declaration of it (an import is not one), never from a code span in prose or a description cell; the other reading gives: an entry at references/native-components.md:113 for a name the source does not export: a stale-name gap
  - `NativeTypewriterProps`, inventory reader: The code span `NativeTypewriterProps` at references/native-components.md:130 names a props type that references/types.md does not list, and the file's Install and import paragraph says "a props type the signature names and that file does not list is not exported by the source": the skill says the source does not export it, so the code span gives no entry; left open by: A name the skill presents only as a local import alias of another name, or says the source does not export, is not an export the skill documents either: it gets an entry only from a place `inventory-floor.json` gives it, a heading, an export table's first cell or a fenced declaration of it (an import is not one), never from a code span in prose or a description cell; the other reading gives: an entry at references/native-components.md:130 for a name the source does not export: a stale-name gap
  - `CodeOutputProps`, inventory reader: The code span `CodeOutputProps` at references/motion-components.md:242 names a props type that references/types.md does not list, and the file's Install and import paragraph says "a props type the signature names and that file does not list is not exported by the source": the skill says the source does not export it, so the code span gives no entry; left open by: A name the skill presents only as a local import alias of another name, or says the source does not export, is not an export the skill documents either: it gets an entry only from a place `inventory-floor.json` gives it, a heading, an export table's first cell or a fenced declaration of it (an import is not one), never from a code span in prose or a description cell; the other reading gives: an entry at references/motion-components.md:242 for a name the source does not export: a stale-name gap
  - `PresetsPanelProps`, inventory reader: The code span `PresetsPanelProps` at references/motion-components.md:245 names a props type that references/types.md does not list, and the file's Install and import paragraph says "a props type the signature names and that file does not list is not exported by the source": the skill says the source does not export it, so the code span gives no entry; left open by: A name the skill presents only as a local import alias of another name, or says the source does not export, is not an export the skill documents either: it gets an entry only from a place `inventory-floor.json` gives it, a heading, an export table's first cell or a fenced declaration of it (an import is not one), never from a code span in prose or a description cell; the other reading gives: an entry at references/motion-components.md:245 for a name the source does not export: a stale-name gap
  - `SettingsPanelProps`, inventory reader: The code span `SettingsPanelProps` at references/motion-components.md:246 names a props type that references/types.md does not list, and the file's Install and import paragraph says "a props type the signature names and that file does not list is not exported by the source": the skill says the source does not export it, so the code span gives no entry; left open by: A name the skill presents only as a local import alias of another name, or says the source does not export, is not an export the skill documents either: it gets an entry only from a place `inventory-floor.json` gives it, a heading, an export table's first cell or a fenced declaration of it (an import is not one), never from a code span in prose or a description cell; the other reading gives: an entry at references/motion-components.md:246 for a name the source does not export: a stale-name gap
  - `TweetCardProps`, inventory reader: The code span `TweetCardProps` at references/blocks-and-sections.md:303 names a props type that references/types.md does not list, and the file's Install and import paragraph says "a props type the signature names and that file does not list is not exported by the source": the skill says the source does not export it, so the code span gives no entry; left open by: A name the skill presents only as a local import alias of another name, or says the source does not export, is not an export the skill documents either: it gets an entry only from a place `inventory-floor.json` gives it, a heading, an export table's first cell or a fenced declaration of it (an import is not one), never from a code span in prose or a description cell; the other reading gives: an entry at references/blocks-and-sections.md:303 for a name the source does not export: a stale-name gap
  - `twMerge`, inventory reader: twMerge and clsx (utils.md:28-32 and :36, SKILL.md:106) are the third-party functions cn wraps, not exports the skill documents for this library, so they get no entry; left open by: A place that writes a name but no form of it, and no `methods`, `properties` or `fields` its entry would carry (a mention, a bare code span, an import, a heading or prose that names or describes it), gives it no entry when another place gives the name one, unless `inventory-floor.json` gives that place; of several such places of a name the skill documents and no other place gives an entry, the first alone gives one: in SKILL.md, else the file that sorts first by path, at its lowest line; the other reading gives: entries for names the source does not export: stale-name gaps
  - `BottomModal` (references/motion-components.md:207), inventory reader: SKILL.md:114 puts the registry entry `bottom-modal` in the registry.json category native, while motion-components.md lists BottomModal under components/modals/ of its Interaction components by category (the src/components/<category>/ source folder); SKILL.md writes the registry name, not the export name, and the two groupings are different fields, so no contradiction is recorded; likewise cinema-ticket (SKILL.md cards against blocks-and-sections.md's sections folder) and profile-page (SKILL.md page against components/components/profile/); left open by: `validate-inventory.py` adds `crossChecked` to the inventory it writes, `{"count": <int>, "names": [<name>, ...]}`: each inventory name, once, that two or more of the files it reads write (SKILL.md and each file `references` lists), by the spot-check's name match outside `[AST:]`, `[SRC:]` and `[EXT:]` citations, so a mention in prose counts; the other reading gives: a split-body mismatch: registry category native against the modals group
  - `HeroSection` (references/blocks-and-sections.md:99), inventory reader: SKILL.md, which writes HeroSection only in its Quick Start example, puts `hero-section` in the registry category page (as types.md's registry.json entry does: type registry:page, category page), while blocks-and-sections.md lists HeroSection under Sections and blocks, the src/components/sections/ folder (integration.md:57 agrees on the file); the forms agree and the two groupings state different fields, so no mismatch is recorded; likewise faq-section and scroll-reveal; left open by: In the split-body cross-check both forms are documented: each is read by these rules, a type, return type or type arguments one of them leaves out are not compared, and a parameter's optionality is compared only when both forms state it; the other reading gives: a split-body mismatch: a page entry against a section or block
- **Scoped Out by the Brief:** `NativeAvatarExpandDefault` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx:5), `NativeAvatarExpandDemo` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx:57), `NativeAvatarExpandExtraLarge` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx:37), `NativeAvatarExpandLarge` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx:25), `NativeAvatarExpandNoImage` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx:49), `NativeAvatarExpandSmall` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx:13), `NativeAvatarWithNameDefault` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx:5), `NativeAvatarWithNameDemo` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx:84), `NativeAvatarWithNameLarge` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx:64), `NativeAvatarWithNameLeft` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx:28), `NativeAvatarWithNameNoImage` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx:76), `NativeAvatarWithNameRight` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx:40), `NativeAvatarWithNameSmall` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx:52), `NativeAvatarWithNameTop` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx:16), `NativeButtonDefault` (packages/components/react-shadcn/src/components/native/demo/native-button-demo.tsx:5), `NativeButtonDisabled` (packages/components/react-shadcn/src/components/native/demo/native-button-demo.tsx:21), `NativeButtonGlow` (packages/components/react-shadcn/src/components/native/demo/native-button-demo.tsx:9), `NativeButtonLoading` (packages/components/react-shadcn/src/components/native/demo/native-button-demo.tsx:17), `NativeButtonOutline` (packages/components/react-shadcn/src/components/native/demo/native-button-demo.tsx:13), `NativeDeleteCustomText` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx:71), `NativeDeleteDefault` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx:6), `NativeDeleteDemo` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx:124), `NativeDeleteDisabled` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx:116), `NativeDeleteLarge` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx:49), `NativeDeleteNoIcon` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx:94), `NativeDeleteSmall` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx:27), `NativeDialogDemo` (packages/components/react-shadcn/src/components/native/demo/native-dialog-demo.tsx:14), `NativeHoverCardBordered` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:38), `NativeHoverCardCustomButton` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:130), `NativeHoverCardCustomButtonText` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:156), `NativeHoverCardDefault` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:7), `NativeHoverCardDemo` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:200), `NativeHoverCardExtraLarge` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:86), `NativeHoverCardGlass` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:22), `NativeHoverCardLarge` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:70), `NativeHoverCardMinimal` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:172), `NativeHoverCardNoDescription` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:116), `NativeHoverCardNoUsername` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:102), `NativeHoverCardSmall` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:54), `NativeHoverCardWithFallback` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:185), `NativeImageCheckboxDefault` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx:6), `NativeImageCheckboxDemo` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx:117), `NativeImageCheckboxExtraLarge` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx:50), `NativeImageCheckboxGrid` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx:79), `NativeImageCheckboxLarge` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx:35), `NativeImageCheckboxSelected` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx:65), `NativeImageCheckboxSmall` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx:20), `NativeLikesCounterDefault` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx:38), `NativeLikesCounterDemo` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx:131), `NativeLikesCounterGhost` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx:62), `NativeLikesCounterInteractive` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx:91), `NativeLikesCounterOutline` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx:54), `NativeLikesCounterSizes` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx:70), `NativeLikesCounterSubtle` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx:46), `NativeLiquidButtonCustomColor` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:136), `NativeLiquidButtonDefault` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:6), `NativeLiquidButtonDemo` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:146), `NativeLiquidButtonError` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:88), `NativeLiquidButtonGlow` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:24), `NativeLiquidButtonGradient` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:14), `NativeLiquidButtonLoading` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:68), `NativeLiquidButtonSizes` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:98), `NativeLiquidButtonSuccess` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:78), `NativeLiquidButtonVariants` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:117), `NativeLiquidButtonWave` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:34), `NativeLiquidButtonWithProgress` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:44), `NativeMagneticDefault` (packages/components/react-shadcn/src/components/native/demo/native-magnetic-demo.tsx:6), `NativeMagneticDemo` (packages/components/react-shadcn/src/components/native/demo/native-magnetic-demo.tsx:42), `NativeMagneticLink` (packages/components/react-shadcn/src/components/native/demo/native-magnetic-demo.tsx:16), `NativeMagneticStrong` (packages/components/react-shadcn/src/components/native/demo/native-magnetic-demo.tsx:30), `NativeMorphingButtonCustomIcon` (packages/components/react-shadcn/src/components/native/demo/native-morphing-button-demo.tsx:32), `NativeMorphingButtonDefault` (packages/components/react-shadcn/src/components/native/demo/native-morphing-button-demo.tsx:6), `NativeMorphingButtonDemo` (packages/components/react-shadcn/src/components/native/demo/native-morphing-button-demo.tsx:54), `NativeNestedListDemo` (packages/components/react-shadcn/src/components/native/demo/native-nested-list-demo.tsx:88), `NativeNotchDefault` (packages/components/react-shadcn/src/components/native/demo/native-notch-demo.tsx:6), `NativeNotchLeftAlign` (packages/components/react-shadcn/src/components/native/demo/native-notch-demo.tsx:37), `NativeNotchRelative` (packages/components/react-shadcn/src/components/native/demo/native-notch-demo.tsx:69), `NativeNotificationBellCustomIcon` (packages/components/react-shadcn/src/components/native/demo/native-notification-bell-demo.tsx:22), `NativeNotificationBellDefault` (packages/components/react-shadcn/src/components/native/demo/native-notification-bell-demo.tsx:6), `NativeNotificationBellDemo` (packages/components/react-shadcn/src/components/native/demo/native-notification-bell-demo.tsx:33), `NativeNotificationBellEmpty` (packages/components/react-shadcn/src/components/native/demo/native-notification-bell-demo.tsx:14), `NativeProfileNotchDefault` (packages/components/react-shadcn/src/components/native/demo/native-profile-notch-demo.tsx:5), `NativeProfileNotchOverlay` (packages/components/react-shadcn/src/components/native/demo/native-profile-notch-demo.tsx:37), `NativeStartNowCustomLabels` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:82), `NativeStartNowDefault` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:6), `NativeStartNowDemo` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:150), `NativeStartNowDisabled` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:95), `NativeStartNowGradient` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:16), `NativeStartNowHeartIcon` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:128), `NativeStartNowLarge` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:60), `NativeStartNowNoSparkles` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:71), `NativeStartNowOutline` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:38), `NativeStartNowRocketIcon` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:139), `NativeStartNowSmall` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:49), `NativeStartNowSolid` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:27), `NativeStartNowStarIcon` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:106), `NativeStartNowZapIcon` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:117), `NativeTabsDemo` (packages/components/react-shadcn/src/components/native/demo/native-tabs-demo.tsx:5), `NativeTooltipBlur` (packages/components/react-shadcn/src/components/native/demo/native-tooltip-demo.tsx:9), `NativeTooltipDemo` (packages/components/react-shadcn/src/components/native/demo/native-tooltip-demo.tsx:29), `NativeTooltipScale` (packages/components/react-shadcn/src/components/native/demo/native-tooltip-demo.tsx:19), `NativeTypewriterDefault` (packages/components/react-shadcn/src/components/native/demo/native-typewriter-demo.tsx:5), `NativeTypewriterDemo` (packages/components/react-shadcn/src/components/native/demo/native-typewriter-demo.tsx:46), `NativeTypewriterLoop` (packages/components/react-shadcn/src/components/native/demo/native-typewriter-demo.tsx:32), `NativeTypewriterMultiline` (packages/components/react-shadcn/src/components/native/demo/native-typewriter-demo.tsx:16), `NativeUserCardDemo` (packages/components/react-shadcn/src/components/native/demo/native-user-card-demo.tsx:5), `NativeVerifiedBadgeCustomIcon` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx:128), `NativeVerifiedBadgeDefault` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx:30), `NativeVerifiedBadgeDemo` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx:153), `NativeVerifiedBadgeOutlineVariants` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx:80), `NativeVerifiedBadgeShield` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx:93), `NativeVerifiedBadgeSizes` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx:53), `NativeVerifiedBadgeWithLabel` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx:40), `NativeVerifiedBadgeWithTooltip` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx:103), `SocialButtonsGlow` (packages/components/react-shadcn/src/components/native/demo/social-login-demo.tsx:23), `SocialButtonsScale` (packages/components/react-shadcn/src/components/native/demo/social-login-demo.tsx:14), `SocialButtonsShine` (packages/components/react-shadcn/src/components/native/demo/social-login-demo.tsx:33), `SocialButtonsSlide` (packages/components/react-shadcn/src/components/native/demo/social-login-demo.tsx:5)
- **Extraction Gaps:** `GAP_VALUES` (packages/components/react-shadcn/src/lib/grid-utils.ts:23), `THEME_STORAGE_KEY` (packages/components/react-shadcn/src/components/theme-provider.tsx:11), `bentoPresets` (packages/components/react-shadcn/src/lib/grid-presets.ts:7), `cn` (packages/components/react-shadcn/src/lib/utils.ts:3), `componentsRegistry` (packages/registry/src/index.tsx:8), `countSavedProjectComponents` (packages/utils/src/builder-utils.ts:70), `createPage` (packages/utils/src/builder-utils.ts:33), `extractSavedPages` (packages/utils/src/builder-utils.ts:52), `generateGridCode` (packages/components/react-shadcn/src/lib/grid-utils.ts:47), `generateUniqueSlug` (packages/utils/src/builder-utils.ts:14), `getCellKey` (packages/components/react-shadcn/src/lib/grid-utils.ts:101), `getGapSliderIndex` (packages/components/react-shadcn/src/lib/grid-utils.ts:32), `getGapValueFromIndex` (packages/components/react-shadcn/src/lib/grid-utils.ts:40), `initializeCells` (packages/components/react-shadcn/src/lib/grid-utils.ts:76), `isCellInSelection` (packages/components/react-shadcn/src/lib/grid-utils.ts:106), `mergeComponentImports` (packages/utils/src/merge-imports.ts:6), `nativeComponents` (packages/registry/src/registry/native.tsx:218), `sanitizeSlug` (packages/utils/src/builder-utils.ts:7), `uiComponents` (packages/registry/src/registry/ui.tsx:179), `uiLibraryLabels` (packages/utils/src/types.ts:5), `useTheme` (packages/components/react-shadcn/src/components/theme-provider.tsx:35), `useUILibrary` (packages/components/react-shadcn/src/ui-library-provider.tsx:23)

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 100% |
| Signature Accuracy | 100% |
| Type Coverage | 100% |

**Coverage Notes:**
- **Read by eye:** the recipe runner reported syntax errors in 10 files, so their exports were read by eye and added to the surface as per-file results (one component each): `packages/components/react-shadcn/src/components/components/blog/blog-typography.tsx` (BlogTypography), `.../course-content/course-content-page.tsx` (CourseContentPage), `.../profile/profile-page.tsx` (ProfilePage), `.../resumes/shadcnui/professional-resume.tsx` (ProfessionalResume), `.../weather/weather-dashboard.tsx` (WeatherDashboard), `packages/components/react-shadcn/src/components/sections/bento-grid-block.tsx` (BentoGridBlock), `.../sections/cinema-ticket.tsx` (CinemaTicket), `.../sections/conference-ticket.tsx` (ConferenceTicket), `.../sections/glassmorphism-portfolio-block.tsx` (GlassmorphismPortfolioBlock), `.../sections/notion-blog-page.tsx` (NotionBlogPage). **Unread:** none.
- **Inventory (§1/§1a):** one inventory-reader subagent; the inventory validated on the first attempt (627 entries over 330 names, 9 reference files read, all 279 floor origins kept, 0 validator warnings), so no form was left unbound for want of a place.
- **Split-body cross-check (§1b):** the reader recorded 0 `cross_check_mismatches`; 90 names are written in two or more files (`crossChecked`). Its readings on the registry-category vs source-folder groupings (`BottomModal`, `HeroSection` and the names it lists with them) are among the Borderline Calls above.
- **Signature comparison (§2):** 202 signature-judge subagents, one per plan file, compared 270 checks (13 with candidates, 3 with alternatives, 1 with a `bound` list: `cn`, forms 0 and 2 bound to `packages/utils/src/cn.ts:4`); 0 mismatches and 0 undecided readings.
- **Stale names (§2c):** `UILibraryContextValue`, `add` and `fetchComponent` are documented names the counted set lacks; `classify-stale` finds each still declared in the source (`ui-library-provider.tsx:14`, `packages/uitripled/src/commands/add.ts:8`, `packages/uitripled/src/utils/registry.ts:5`), none scoped out: documented extras.
- **Stale scope guard (§4):** fires — the `scope.include` globs `apps/docs/app/**/page.mdx` and `apps/docs/components/demos/**` match no file; no export was restored.
- **Numerator ground truth (§2b):** skipped (no inflation signature).
- **Metadata count cross-check (§4b):** 1 Medium finding (`stats.exports_public_api` 445 vs `exports[]` 297, 33% drift) and 1 Info finding (barrel 445 vs documented 315).
- **Provenance line check (§4c):** 315 map entries checked against the pinned source, 0 stale lines (18 orphaned entries, which this section does not report).

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)
**Migration Section:** Section 4b verification skipped: evidence-report.md pins no `t2_future_count`. For a skill create-skill made, re-run create-skill to regenerate the report with the field (create-stack-skill does not write it).

### Structural Findings

| # | Type | Severity | Detail | Line |
|---|------|----------|--------|------|
| — | — | — | No structural issue: the description (`Overview`), usage (`Quick Start`) and API-surface (`Component Catalog`) families are present; 14 code fences, balanced, each opening fence tagged; no table drift; every function export (199) is used in the usage-family scope; the one example call of an async export (`fetchComponent`, references/catalog.md:123) awaits it; no `scripts/` or `assets/` folder | — |

**Structural Issues:** 0

### Reference Consistency (split-body)

| # | Reference File | Export | Issue | Other Side | Reference Line | Contradicted Side |
|---|---------------|--------|-------|------------|---------------|-------------------|
| — | — | — | No split-body mismatch recorded | — | — | — |

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
**External Validators:** skill-check only (from `skill-check`)
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

**Issue:** `SKILL.md:187` documents `fetchComponent`, which the enumerated source API surface lacks and the source still declares

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
| 1 | can you help me throw together a landing page for my startup? hero, features, pricing, footer, the usual, ideally with some ready-made animated sections I can just copy into the project | oms-uitripled (high) | PASS |
| 2 | why does my app's dashboard look so flat? I'd rather grab a prebuilt animated stats card and sidebar than code them from scratch | oms-uitripled (high) | PASS |
| 3 | run the component install thing to drop an animated glassmorphism pricing block into my site | oms-uitripled (high) | PASS |

SKILL.md holds no organic prompts, so the three were synthesized (§4b.1: vague, implicit and abbreviated patterns), naming no export, skill, library or package. Each was routed by an isolated subagent (an agent type with no file or shell tools) given only the 4-skill catalog (oms-cocoindex, oms-cognee, oms-storybook-react-vite, oms-uitripled: name and frontmatter description) and the prompt; none used a tool. No description optimization hints: Tessl Review did not run and skill-check flagged no description issue.
