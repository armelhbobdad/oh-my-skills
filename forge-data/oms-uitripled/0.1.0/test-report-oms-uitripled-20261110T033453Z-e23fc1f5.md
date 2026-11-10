---
workflowType: 'test-skill'
skillName: 'oms-uitripled'
skillDir: 'skills/oms-uitripled/0.1.0/oms-uitripled'
runId: '20261110T033453Z-e23fc1f5'
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
testDate: '2026-11-10T03:34:53Z'
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

**Mode Rationale:** metadata.json sets `skill_type: 'single'`, so this individual skill is tested in naive mode: API-surface coverage, with a structural coherence check and no coherence category in the score.

**Analysis Plan:**
- Coverage Check: the documented exports of SKILL.md and references/ against the source's public API at the pinned commit a5ffb45, with Deep-tier AST-backed signature and type checks (inventory reader, split-body judge and signature judges as subagents).
- Coherence Check: structural only (naive mode): references resolve, sections are present and internally consistent; no cross-skill integration checks.

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
  - `NativeButton` (references/native-components.md:37), inventory reader: a const bound to an arrow that renders a component (`const NativeButton = ({ ... }: NativeButtonProps) => …`) is read by this sentence, not by the `const` holding a component sentence, whose parenthetical names only a `forwardRef`, `memo` or other wrapper call or an alias: its destructured parameter is `params` and `=> …` writes no return type; the same reading gives NativeTooltip (native-components.md:80), NativeTooltipProvider (:82), SocialLoginButton (:93), DialogFooter (ui-primitives.md:55), DialogHeader (:56), DropdownMenuShortcut (:72), LiquidCursor (motion-components.md:142, `params` []) and BrowseFolder (blocks-and-sections.md:41, `params` []) their forms; left open by: A `const` whose value is a function (annotated with a function type, bound to an arrow, a `function` or a call that returns one, or written with a parameter list) carries the function form the skill writes for it as `params` (`[]`, never `""`, when it takes none) and `return_type`, whatever its kind (`constant` for the skill's `const` label), wherever the skill writes it, a description cell included, except a call expression of its name, which is recorded in `usage_signature` as a function's is (above); a bare `name()` there is still a mention; only a constant holding neither a component nor a function is a data constant; the other reading gives: read as a `const` holding a component, each whole declaration would be the entry's `usage_signature`, compared as a usage rather than a props list; no gap expected either way, since each destructuring either names props its props type declares or ends in a rest element
  - `Avatar` (references/ui-primitives.md:38), inventory reader: the `(…)` closing `const Avatar = React.forwardRef<…>(…)` stands for the render function passed to `forwardRef`, the body, not for members of Avatar's props, which the type arguments write whole: no partial label; the same holds for every `React.forwardRef<…>(…)` declaration of ui-primitives.md (AvatarFallback, AvatarImage, CardDescription, CardFooter, CardTitle, Checkbox, DialogDescription, DialogOverlay, DialogTitle, DropdownMenuCheckboxItem, DropdownMenuContent, DropdownMenuItem, DropdownMenuLabel, DropdownMenuRadioItem, DropdownMenuSeparator, DropdownMenuSubContent, DropdownMenuSubTrigger, Label, ScrollArea, ScrollBar, Separator, Slider, Switch, TabsContent, TabsList, TabsTrigger, Textarea, TooltipContent) and of native-components.md (NativeDialogContent, NativeDialogOverlay, NativeTooltipContent); left open by: An entry whose signature the skill labels partial (simplified, key parameters, a `...` standing in for omitted members as a member or argument of its own, not rest or variadic syntax nor an argument's value such as `api_key=...`; a label in a table's column header, such as `Props (simplified)`, labels each of its rows, every form their cells write included, a usage form or another name's form among them, but only as the whole header, `Key params`, or in parentheses after its word, as inventory-floor.json reads one, so `Purpose and key params` labels none) carries `signature_form: "partial"`, any other `"full"` or no key, and a form that writes only a `return_type` carries none: copy the label, never judge the form; the other reading gives: with `signature_form` partial no gap either: the props these forms name are a Radix primitive's or React's HTML attributes, inherited from another package and left uncompared
  - `GridCell` (references/utils.md:65), inventory reader: the skill documents two exports named GridCell and says they are different: the grid-utils `GridCell` interface (utils.md:65, types.md:122) gets `interface` with `fields`, and the components/grid/grid-cell.tsx `GridCell` component (motion-components.md:229, :243) gets `function` with `params`; one kind is kept per declaration, not per name; left open by: A name documented in several places is listed once per place, each entry with that place's form (`Card` above), and once per form at a place that writes several of its forms (two overloads in one row), each entry with that place as its `at`, never as one entry whose list `params` gives a form per item (the validator refuses a list of two or more items when one item holds several parameters or a whole form, or two items name the same parameter), and keeps one `kind` in every place; the other reading gives: one kind for all four entries would give the interface a function kind or the component an interface kind; no gap expected, since the two declarations are never compared with each other
  - `CodeOutputProps` (references/motion-components.md:242), inventory reader: each reference file's Install and import section says "a props type the signature names and that file does not list is not exported by the source", so the props types that types.md does not list and that the skill writes only in signatures and description cells get no entry: CodeOutputProps, PresetsPanelProps and SettingsPanelProps (motion-components.md:242, :245, :246), AIGlowInputProps (motion-components.md:29), TweetCardProps (blocks-and-sections.md:303), NativeFlipTextProps and NativeTypewriterProps (native-components.md:113, :130); GridCellProps, which motion-components.md:238 says grid-cell.tsx does not export, gets none either, and GridCellType is a local import alias; left open by: A name the skill presents only as a local import alias of another name, or says the source does not export, is not an export the skill documents either: it gets an entry only from a place `inventory-floor.json` gives it, a heading, an export table's first cell or a fenced declaration of it (an import is not one), never from a code span in prose or a description cell; the other reading gives: entries for them at those description cells would list names the skill says the source does not export: a stale-name gap for each one the source indeed does not export
  - `Button` (SKILL.md:41), inventory reader: ui-primitives.md:3 names Button, Card, CardContent, CardHeader, Input, Dialog and DialogContent as src/ui exports the skill documents only through references/integration.md's subpath-import example, so each is a documented name with no form, entered at its first place: Button at SKILL.md:41, Card and Dialog at SKILL.md:160, Input at references/catalog.md:71 (blocks-and-sections.md:317 and motion-components.md:88 write the English word Input, not the export), CardContent and CardHeader at references/integration.md:39, DialogContent at references/integration.md:41; each takes the kind `constant` of the other src/ui forwardRef and alias primitives, as the skill gives them no kind; left open by: A place that writes a name but no form of it, and no `methods`, `properties` or `fields` its entry would carry (a mention, a bare code span, an import, a heading or prose that names or describes it), gives it no entry when another place gives the name one, unless `inventory-floor.json` gives that place; of several such places of a name the skill documents and no other place gives an entry, the first alone gives one: in SKILL.md, else the file that sorts first by path, at its lowest line; the other reading gives: read as names the skill does not document, they get no entry and the source's Button, Card, CardContent, CardHeader, Input, Dialog and DialogContent count as undocumented exports: a coverage gap instead of no gap
  - `badgeVariants` (references/ui-primitives.md:118), inventory reader: Badge's Purpose cell writes `badgeVariants({ variant })`, a call of badgeVariants (a const holding the function `cva` returns) that passes an argument, so that row is also a place of badgeVariants with this usage form, besides the floor's badgeVariants row at line 119; left open by: A function's, a method's or a class's form the skill writes as a call expression of its own name (after `await`, `new` or an assignment, through a receiver or module path such as `coco.`, or as a statement in a fenced example; in running text or a description cell, only a call that passes an argument and writes no parameter type, `?`, bare `*` or `/`, with or without such a prefix, and no return type unless such a prefix comes before the name, such as `add(componentName, options)` or `await coco.mount(fn) -> Handle`), at a place `inventory-floor.json` gives no `signature` (below), is recorded whole in `usage_signature`; the other reading gives: read as a mention it gives no entry; no gap either way, since the function `cva` returns declares its parameters in class-variance-authority, outside the source tree
  - `badgeVariants` (references/ui-primitives.md:43), inventory reader: "carries no ... there" reads as an entry at that place with no form, so the fenced `const badgeVariants = cva(…)` (line 43) and `const buttonVariants = cva(…)` (line 45) each give an entry with only `name`, `kind`, `description` and `at`, beside the floor's rows at lines 119 and 120; left open by: A `const` holding a function, not a component, that a place writes only as the call that builds it (`const badgeVariants = cva(…)`), with no parameter list, function type or return type of its own, carries no `params`, `return_type` or `usage_signature` there: that call is the factory's form, not the const's; the other reading gives: read as places that write the name but no form, they give no entry; no gap either way
  - `sanitizeSlug` (references/utils.md:53), inventory reader: the code span `const baseSlug = sanitizeSlug(baseName) || "page"` in generateUniqueSlug's bullet is a call of sanitizeSlug in running text that passes an argument, recorded as `const baseSlug = sanitizeSlug(baseName)` (the assignment kept, the `|| "page"` after the call dropped); left open by: A function's, a method's or a class's form the skill writes as a call expression of its own name (after `await`, `new` or an assignment, through a receiver or module path such as `coco.`, or as a statement in a fenced example; in running text or a description cell, only a call that passes an argument and writes no parameter type, `?`, bare `*` or `/`, with or without such a prefix, and no return type unless such a prefix comes before the name, such as `add(componentName, options)` or `await coco.mount(fn) -> Handle`), at a place `inventory-floor.json` gives no `signature` (below), is recorded whole in `usage_signature`; the other reading gives: read as a description of generateUniqueSlug's body rather than a form of sanitizeSlug, it gives no entry; no gap either way, since the call passes the one parameter `value: string`
  - `useUILibrary` (references/setup.md:82), inventory reader: the **Return type** block under useUILibrary is a fenced declaration of its own, giving UILibraryContextValue a `type` entry with fields at setup.md:90 (the skill does not say the source leaves it unexported); the hook's usage form at line 82 writes no return type, so the hook entry carries no `return_type`; left open by: a function or method carries `params` (`""` or `[]` when it takes none; any list `params` holds the members of one parameter list, one per item, never one form per item) and `return_type` as the skill documents them, and leaves a key out when the skill documents nothing for it; the other reading gives: with `return_type` `UILibraryContextValue` on the hook entry the return would be compared with the source's; no gap expected, as the hook returns the context value of that type
  - `cn` (SKILL.md:110), inventory reader: `cn(className, "extra-classes")` is a usage form of cn, although the sentence calls the copy in the reader's own `@/lib/utils` (which `npx shadcn init` writes) rather than `@uitripled/utils`' cn; left open by: A function's, a method's or a class's form the skill writes as a call expression of its own name (after `await`, `new` or an assignment, through a receiver or module path such as `coco.`, or as a statement in a fenced example; in running text or a description cell, only a call that passes an argument and writes no parameter type, `?`, bare `*` or `/`, with or without such a prefix, and no return type unless such a prefix comes before the name, such as `add(componentName, options)` or `await coco.mount(fn) -> Handle`), at a place `inventory-floor.json` gives no `signature` (below), is recorded whole in `usage_signature`; the other reading gives: read as a form of a function outside the package it would give no entry; no gap either way, since the call matches `cn(...inputs: ClassValue[])`
- **Scoped Out by the Brief:** `NativeAvatarExpandDefault` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx:5), `NativeAvatarExpandDemo` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx:57), `NativeAvatarExpandExtraLarge` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx:37), `NativeAvatarExpandLarge` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx:25), `NativeAvatarExpandNoImage` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx:49), `NativeAvatarExpandSmall` (packages/components/react-shadcn/src/components/native/demo/native-avatar-expand-demo.tsx:13), `NativeAvatarWithNameDefault` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx:5), `NativeAvatarWithNameDemo` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx:84), `NativeAvatarWithNameLarge` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx:64), `NativeAvatarWithNameLeft` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx:28), `NativeAvatarWithNameNoImage` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx:76), `NativeAvatarWithNameRight` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx:40), `NativeAvatarWithNameSmall` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx:52), `NativeAvatarWithNameTop` (packages/components/react-shadcn/src/components/native/demo/native-avatar-with-name-demo.tsx:16), `NativeButtonDefault` (packages/components/react-shadcn/src/components/native/demo/native-button-demo.tsx:5), `NativeButtonDisabled` (packages/components/react-shadcn/src/components/native/demo/native-button-demo.tsx:21), `NativeButtonGlow` (packages/components/react-shadcn/src/components/native/demo/native-button-demo.tsx:9), `NativeButtonLoading` (packages/components/react-shadcn/src/components/native/demo/native-button-demo.tsx:17), `NativeButtonOutline` (packages/components/react-shadcn/src/components/native/demo/native-button-demo.tsx:13), `NativeDeleteCustomText` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx:71), `NativeDeleteDefault` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx:6), `NativeDeleteDemo` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx:124), `NativeDeleteDisabled` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx:116), `NativeDeleteLarge` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx:49), `NativeDeleteNoIcon` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx:94), `NativeDeleteSmall` (packages/components/react-shadcn/src/components/native/demo/native-delete-demo.tsx:27), `NativeDialogDemo` (packages/components/react-shadcn/src/components/native/demo/native-dialog-demo.tsx:14), `NativeHoverCardBordered` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:38), `NativeHoverCardCustomButton` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:130), `NativeHoverCardCustomButtonText` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:156), `NativeHoverCardDefault` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:7), `NativeHoverCardDemo` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:200), `NativeHoverCardExtraLarge` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:86), `NativeHoverCardGlass` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:22), `NativeHoverCardLarge` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:70), `NativeHoverCardMinimal` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:172), `NativeHoverCardNoDescription` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:116), `NativeHoverCardNoUsername` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:102), `NativeHoverCardSmall` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:54), `NativeHoverCardWithFallback` (packages/components/react-shadcn/src/components/native/demo/native-hover-card-demo.tsx:185), `NativeImageCheckboxDefault` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx:6), `NativeImageCheckboxDemo` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx:117), `NativeImageCheckboxExtraLarge` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx:50), `NativeImageCheckboxGrid` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx:79), `NativeImageCheckboxLarge` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx:35), `NativeImageCheckboxSelected` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx:65), `NativeImageCheckboxSmall` (packages/components/react-shadcn/src/components/native/demo/native-image-checkbox-demo.tsx:20), `NativeLikesCounterDefault` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx:38), `NativeLikesCounterDemo` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx:131), `NativeLikesCounterGhost` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx:62), `NativeLikesCounterInteractive` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx:91), `NativeLikesCounterOutline` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx:54), `NativeLikesCounterSizes` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx:70), `NativeLikesCounterSubtle` (packages/components/react-shadcn/src/components/native/demo/native-likes-counter-demo.tsx:46), `NativeLiquidButtonCustomColor` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:136), `NativeLiquidButtonDefault` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:6), `NativeLiquidButtonDemo` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:146), `NativeLiquidButtonError` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:88), `NativeLiquidButtonGlow` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:24), `NativeLiquidButtonGradient` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:14), `NativeLiquidButtonLoading` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:68), `NativeLiquidButtonSizes` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:98), `NativeLiquidButtonSuccess` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:78), `NativeLiquidButtonVariants` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:117), `NativeLiquidButtonWave` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:34), `NativeLiquidButtonWithProgress` (packages/components/react-shadcn/src/components/native/demo/native-liquid-button-demo.tsx:44), `NativeMagneticDefault` (packages/components/react-shadcn/src/components/native/demo/native-magnetic-demo.tsx:6), `NativeMagneticDemo` (packages/components/react-shadcn/src/components/native/demo/native-magnetic-demo.tsx:42), `NativeMagneticLink` (packages/components/react-shadcn/src/components/native/demo/native-magnetic-demo.tsx:16), `NativeMagneticStrong` (packages/components/react-shadcn/src/components/native/demo/native-magnetic-demo.tsx:30), `NativeMorphingButtonCustomIcon` (packages/components/react-shadcn/src/components/native/demo/native-morphing-button-demo.tsx:32), `NativeMorphingButtonDefault` (packages/components/react-shadcn/src/components/native/demo/native-morphing-button-demo.tsx:6), `NativeMorphingButtonDemo` (packages/components/react-shadcn/src/components/native/demo/native-morphing-button-demo.tsx:54), `NativeNestedListDemo` (packages/components/react-shadcn/src/components/native/demo/native-nested-list-demo.tsx:88), `NativeNotchDefault` (packages/components/react-shadcn/src/components/native/demo/native-notch-demo.tsx:6), `NativeNotchLeftAlign` (packages/components/react-shadcn/src/components/native/demo/native-notch-demo.tsx:37), `NativeNotchRelative` (packages/components/react-shadcn/src/components/native/demo/native-notch-demo.tsx:69), `NativeNotificationBellCustomIcon` (packages/components/react-shadcn/src/components/native/demo/native-notification-bell-demo.tsx:22), `NativeNotificationBellDefault` (packages/components/react-shadcn/src/components/native/demo/native-notification-bell-demo.tsx:6), `NativeNotificationBellDemo` (packages/components/react-shadcn/src/components/native/demo/native-notification-bell-demo.tsx:33), `NativeNotificationBellEmpty` (packages/components/react-shadcn/src/components/native/demo/native-notification-bell-demo.tsx:14), `NativeProfileNotchDefault` (packages/components/react-shadcn/src/components/native/demo/native-profile-notch-demo.tsx:5), `NativeProfileNotchOverlay` (packages/components/react-shadcn/src/components/native/demo/native-profile-notch-demo.tsx:37), `NativeStartNowCustomLabels` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:82), `NativeStartNowDefault` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:6), `NativeStartNowDemo` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:150), `NativeStartNowDisabled` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:95), `NativeStartNowGradient` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:16), `NativeStartNowHeartIcon` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:128), `NativeStartNowLarge` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:60), `NativeStartNowNoSparkles` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:71), `NativeStartNowOutline` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:38), `NativeStartNowRocketIcon` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:139), `NativeStartNowSmall` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:49), `NativeStartNowSolid` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:27), `NativeStartNowStarIcon` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:106), `NativeStartNowZapIcon` (packages/components/react-shadcn/src/components/native/demo/native-start-now-demo.tsx:117), `NativeTabsDemo` (packages/components/react-shadcn/src/components/native/demo/native-tabs-demo.tsx:5), `NativeTooltipBlur` (packages/components/react-shadcn/src/components/native/demo/native-tooltip-demo.tsx:9), `NativeTooltipDemo` (packages/components/react-shadcn/src/components/native/demo/native-tooltip-demo.tsx:29), `NativeTooltipScale` (packages/components/react-shadcn/src/components/native/demo/native-tooltip-demo.tsx:19), `NativeTypewriterDefault` (packages/components/react-shadcn/src/components/native/demo/native-typewriter-demo.tsx:5), `NativeTypewriterDemo` (packages/components/react-shadcn/src/components/native/demo/native-typewriter-demo.tsx:46), `NativeTypewriterLoop` (packages/components/react-shadcn/src/components/native/demo/native-typewriter-demo.tsx:32), `NativeTypewriterMultiline` (packages/components/react-shadcn/src/components/native/demo/native-typewriter-demo.tsx:16), `NativeUserCardDemo` (packages/components/react-shadcn/src/components/native/demo/native-user-card-demo.tsx:5), `NativeVerifiedBadgeCustomIcon` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx:128), `NativeVerifiedBadgeDefault` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx:30), `NativeVerifiedBadgeDemo` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx:153), `NativeVerifiedBadgeOutlineVariants` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx:80), `NativeVerifiedBadgeShield` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx:93), `NativeVerifiedBadgeSizes` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx:53), `NativeVerifiedBadgeWithLabel` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx:40), `NativeVerifiedBadgeWithTooltip` (packages/components/react-shadcn/src/components/native/demo/native-verified-badge-demo.tsx:103), `SocialButtonsGlow` (packages/components/react-shadcn/src/components/native/demo/social-login-demo.tsx:23), `SocialButtonsScale` (packages/components/react-shadcn/src/components/native/demo/social-login-demo.tsx:14), `SocialButtonsShine` (packages/components/react-shadcn/src/components/native/demo/social-login-demo.tsx:33), `SocialButtonsSlide` (packages/components/react-shadcn/src/components/native/demo/social-login-demo.tsx:5)
- **Extraction Gaps:** `GAP_VALUES` (packages/components/react-shadcn/src/lib/grid-utils.ts:23), `THEME_STORAGE_KEY` (packages/components/react-shadcn/src/components/theme-provider.tsx:11), `bentoPresets` (packages/components/react-shadcn/src/lib/grid-presets.ts:7), `cn` (packages/components/react-shadcn/src/lib/utils.ts:3), `componentsRegistry` (packages/registry/src/index.tsx:8), `countSavedProjectComponents` (packages/utils/src/builder-utils.ts:70), `createPage` (packages/utils/src/builder-utils.ts:33), `extractSavedPages` (packages/utils/src/builder-utils.ts:52), `generateGridCode` (packages/components/react-shadcn/src/lib/grid-utils.ts:47), `generateUniqueSlug` (packages/utils/src/builder-utils.ts:14), `getCellKey` (packages/components/react-shadcn/src/lib/grid-utils.ts:101), `getGapSliderIndex` (packages/components/react-shadcn/src/lib/grid-utils.ts:32), `getGapValueFromIndex` (packages/components/react-shadcn/src/lib/grid-utils.ts:40), `initializeCells` (packages/components/react-shadcn/src/lib/grid-utils.ts:76), `isCellInSelection` (packages/components/react-shadcn/src/lib/grid-utils.ts:106), `mergeComponentImports` (packages/utils/src/merge-imports.ts:6), `nativeComponents` (packages/registry/src/registry/native.tsx:218), `sanitizeSlug` (packages/utils/src/builder-utils.ts:7), `uiComponents` (packages/registry/src/registry/ui.tsx:179), `uiLibraryLabels` (packages/utils/src/types.ts:5), `useTheme` (packages/components/react-shadcn/src/components/theme-provider.tsx:35), `useUILibrary` (packages/components/react-shadcn/src/ui-library-provider.tsx:23)

### Category Scores

| Category | Score |
|----------|-------|
| Export Coverage | 100% |
| Signature Accuracy | 100% |
| Type Coverage | 100% |

**Notes:**

- **Inventory (§1, §1a):** the inventory reader subagent listed 629 entries from SKILL.md and 9 reference files; `validate-inventory.py` accepted it with no violation and no warning (floor: 276 of 276 names kept; spot-check: no absent name). No form is left unbound for want of a place. The reader recorded 10 `undecided` readings, listed under Borderline Calls above.
- **Split-body cross-check (§1b):** the reader found no `cross_check_mismatches` among the 90 names two or more files write, so no split-body gap is recorded and the Split-Body Sources judgment had nothing to settle.
- **Read by eye (§2):
  - `packages/components/react-shadcn/src/components/components/blog/blog-typography.tsx` (read by eye: the runner reported syntax errors; one export found)
  - `packages/components/react-shadcn/src/components/components/course-content/course-content-page.tsx` (read by eye: the runner reported syntax errors; one export found)
  - `packages/components/react-shadcn/src/components/components/profile/profile-page.tsx` (read by eye: the runner reported syntax errors; one export found)
  - `packages/components/react-shadcn/src/components/components/resumes/shadcnui/professional-resume.tsx` (read by eye: the runner reported syntax errors; one export found)
  - `packages/components/react-shadcn/src/components/components/weather/weather-dashboard.tsx` (read by eye: the runner reported syntax errors; one export found)
  - `packages/components/react-shadcn/src/components/sections/bento-grid-block.tsx` (read by eye: the runner reported syntax errors; one export found)
  - `packages/components/react-shadcn/src/components/sections/cinema-ticket.tsx` (read by eye: the runner reported syntax errors; one export found)
  - `packages/components/react-shadcn/src/components/sections/conference-ticket.tsx` (read by eye: the runner reported syntax errors; one export found)
  - `packages/components/react-shadcn/src/components/sections/glassmorphism-portfolio-block.tsx` (read by eye: the runner reported syntax errors; one export found)
  - `packages/components/react-shadcn/src/components/sections/notion-blog-page.tsx` (read by eye: the runner reported syntax errors; one export found)
- **Unread files:** none. **Unresolved star re-exports:** none.
- **Signature comparison (§2):** `score-signatures.py plan` planned 270 checks over 202 source files; one signature judge subagent per `files[]` entry (202 judges) compared each against its declaration by signature-comparison-rules.md, the `cn` check's `bound` forms against `packages/utils/src/cn.ts:4`. They reported no mismatch and no `undecided` reading; `score` graded 270 of 270 as matching and recorded no signature gap.
- **Stale names (§2c):** `UILibraryContextValue` (`packages/components/react-shadcn/src/ui-library-provider.tsx:14`), `add` (`packages/uitripled/src/commands/add.ts:8`) and `fetchComponent` (`packages/uitripled/src/utils/registry.ts:5`) are documented names the enumerated surface lacks; `classify-stale` finds each still declared there and the brief scopes none out, so each is an Info `observation` (documented extra), not a `stale-documentation` gap.
- **Guards (§4):** the deflation guard (327 stored vs 327 re-derived) and the inflation guard (3.81%) do not fire. The stale-scope guard fires: the `scope.include` globs `apps/docs/app/**/page.mdx` and `apps/docs/components/demos/**` match no file (a Medium `brief-scope-stale` gap at the brief); it restores no name.
- **Metadata count cross-check (§4b):** `stats.exports_public_api` 445 against `exports[].length` 297 (33% drift) is a Medium `metadata-drift` gap; barrel 445 against documented 315 is an Info `multi-denominator` note. The numerator ground truth is `skipped` (no inflation signature: declared 297, denominator 327).
- **Provenance line check (§4c):** 315 entries checked, no `stale[]` item; the helper's 18 `orphaned` entries are not reported by this section.

## Coherence Analysis

**Mode:** Naive (structural validation only)
**Coherence category:** Not scored (weight redistributed)
**Migration Section:** Section 4b verification skipped: evidence-report.md pins no `t2_future_count`. For a skill create-skill made, re-run create-skill to regenerate the report with the field (create-stack-skill does not write it).

### Structural Findings

| # | Type | Severity | Detail | Line |
|---|------|----------|--------|------|
| — | — | — | No structural finding: the required section families are served (`description` by `## Overview` at line 15, `usage` by `## Quick Start` at line 29, `api_surface` by `## Component Catalog` at line 112); the 14 fences are balanced and each opening fence carries a language tag; no table row drifts from its header; no `scripts/` or `assets/` folder exists; every one of the 199 function and method exports is referenced in a usage-family section or a reference file (split-body scope: the `## Full*` sections of SKILL.md are pointers to `references/`); the one fenced call of an async export (`fetchComponent`, `references/catalog.md:123`) awaits it, and no other function or method has a fenced call. | — |

**Structural Issues:** 0

### Reference Consistency (split-body)

| # | Reference File | Export | Issue | Other Side | Reference Line | Contradicted Side |
|---|---------------|--------|-------|------------|---------------|-------------------|
| — | — | — | No split-body mismatch | — | — | — |

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

**Issue:** `SKILL.md:191` documents `fetchComponent`, which the enumerated source API surface lacks and the source still declares

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
| 1 | can you throw together a landing page for my web app — hero up top, feature cards, testimonials, pricing and a footer — out of ready-made animated sections instead of me coding it all by hand? | oms-uitripled (high) | PASS |
| 2 | i pasted in that animated hero section from the component registry but the build's complaining about a missing button and some icon package, what else do i need to install? | oms-uitripled (high) | PASS |
| 3 | how do i set up the dark mode provider and the ui library switcher at the root of my app so the animated components i copied in actually follow them? | oms-uitripled (high) | PASS |

Catalog: the 4 skills in `skills/` (oms-cocoindex, oms-cognee, oms-storybook-react-vite, oms-uitripled), each by its frontmatter name and description. SKILL.md has no Triggers section, so the three prompts were synthesized from its Common Workflows and description, naming no export, skill or library. Each was routed by an isolated subagent given only the catalog and the prompt, with no file or shell tool (the `web-fetch` agent type, which has only WebFetch; it used no tool). No description optimization hint applies: Tessl Review did not run and skill-check flagged no description issue.
