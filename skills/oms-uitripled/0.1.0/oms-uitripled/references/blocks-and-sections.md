# Blocks and Sections Reference (react-shadcn `src/components/`)

The landing-page sections and blocks (`src/components/sections/`) and the composite components (`src/components/components/`: chat apps, dashboards, cards, forms, resumes) of `@uitripled/react-shadcn`, with their install ids. Most take no props and render a complete section from built-in content. Signatures are copied from the source at `a5ffb45`; the purpose is the entry's `description` in `packages/registry/registry.json`.

## Contents

- [Install and import](#install-and-import)
- [Sections and blocks](#sections-and-blocks)
- [Composite components](#composite-components)

## Install and import

Install a component with `npx shadcn@latest add @uitripled/<install id>`: the CLI writes the entry's `files[].target`, `components/uitripled/<install id>.tsx`, which you import from `@/components/uitripled/<install id>` `[SRC:packages/registry/registry.json:L1]` `[SRC:apps/docs/public/llms-full.txt:L49]`. A consumer of the npm package imports a subpath instead (`@uitripled/react-shadcn/components/<path>`, `/ui/<file>`, `/src/<path>`), never the bare package: `src/index.ts` is `export {};` `[SRC:packages/components/react-shadcn/package.json:L8]` `[SRC:packages/components/react-shadcn/tsup.config.ts:L4]` `[SRC:packages/components/react-shadcn/src/index.ts:L2]`. The props types are in `references/types.md` → Component props types; a props type the signature names and that file does not list is not exported by the source.

```bash
npx shadcn@latest add @uitripled/ai-chat-interface-shadcnui
```

```tsx
"use client";
import { AIChatInterface } from "@/components/uitripled/ai-chat-interface-shadcnui";

export default function Page() {
  return <AIChatInterface />;
}
```

`AIChatInterface` takes no props `[SRC:packages/components/react-shadcn/src/components/components/chat/ai-chat-interface.tsx:L54]`.

## Sections and blocks

```tsx
// components/sections/about-us-section.tsx
export function AboutUsSection()
// components/sections/bento-grid-block.tsx
export function BentoGridBlock()
// components/sections/blog-block.tsx
export function BlogBlock()
// components/sections/browse-folder.tsx
export function FolderBrowser({ folders = [], initialFolder }: FolderBrowserProps)
export const BrowseFolder = () => …
// components/sections/cinema-ticket.tsx
export function CinemaTicket()
// components/sections/conference-ticket.tsx
export function ConferenceTicket()
// components/sections/contact-block.tsx
export function ContactBlock()
// components/sections/contact-form-section.tsx
export function ContactFormSection()
// components/sections/cta-banner-section.tsx
export function CTABannerSection({ motionPreset = "smooth", className }: CTABannerSectionProps)
// components/sections/cta-block.tsx
export function CTABlock()
// components/sections/cta-hero-block.tsx
export function CTAHeroBlock()
// components/sections/currency-converter-card.tsx
export function CurrencyConverterCard()
// components/sections/faq-accordion-block.tsx
export function FAQAccordionBlock()
// components/sections/faq-section.tsx
export function FAQSection()
// components/sections/feature-cards-block.tsx
export function FeatureCardsBlock()
// components/sections/feature-comparison-block.tsx
export function FeatureComparisonBlock()
// components/sections/feature-grid-section.tsx
export function FeatureGridSection()
// components/sections/footer-block.tsx
export function FooterBlock()
// components/sections/gallery-grid-block.tsx
export function GalleryGridBlock()
// components/sections/glassmorphism-cta-block.tsx
export function GlassmorphismCTABlock()
// components/sections/glassmorphism-hero-block.tsx
export function GlassmorphismHeroBlock()
// components/sections/glassmorphism-launch-timeline-block.tsx
export function GlassmorphismLaunchTimelineBlock()
// components/sections/glassmorphism-listen-app-block.tsx
export function GlassmorphismListenAppBlock()
// components/sections/glassmorphism-logo-showcase-block.tsx
export function GlassmorphismLogoShowcaseBlock()
// components/sections/glassmorphism-minimal-metrics-block.tsx
export function GlassmorphismMinimalMetricsBlock()
// components/sections/glassmorphism-portfolio-block.tsx
export function GlassmorphismPortfolioBlock()
// components/sections/glassmorphism-pricing-block.tsx
export function GlassmorphismPricingBlock()
// components/sections/glassmorphism-product-update-block.tsx
export function GlassmorphismProductUpdateBlock()
// components/sections/glassmorphism-statistics-card.tsx
export function GlassmorphismStatisticsCard()
// components/sections/glassmorphism-testimonials-block.tsx
export function GlassmorphismTestimonialsBlock()
// components/sections/glowy-waves-hero.tsx
export function GlowyWavesHero()
// components/sections/hero-block.tsx
export function HeroBlock()
// components/sections/hero-section.tsx
export function HeroSection()
// components/sections/interactive-logs-table.tsx
export function InteractiveLogsTable()
// components/sections/n8n-workflow-block.tsx
export function N8nWorkflowBlock()
// components/sections/new-hero-section.tsx
export function NewHeroSection()
// components/sections/newsletter-signup-block.tsx
export function NewsletterSignupBlock()
// components/sections/notion-blog-page.tsx
export function NotionBlogPage()
// components/sections/our-partners-section.tsx
export function OurPartnersSection()
// components/sections/our-services-section.tsx
export function OurServicesSection()
// components/sections/pricing-section.tsx
export function PricingSection()
// components/sections/projects-block.tsx
export function ProjectsBlock()
// components/sections/scroll-reveal.tsx
export function ScrollReveal({ motionPreset = "smooth", className }: ScrollRevealProps)
// components/sections/services-grid-block.tsx
export function ServicesGridBlock()
// components/sections/stats-counter-block.tsx
export function StatsCounterBlock()
// components/sections/stats-section.tsx
export function StatsSection()
// components/sections/team-section-block.tsx
export function TeamSectionBlock()
// components/sections/testimonial-section.tsx
export function TestimonialSection()
// components/sections/testimonials-block.tsx
export function TestimonialsBlock()
// components/sections/theater-ticket.tsx
export function TheaterTicket()
// components/sections/timeline-block.tsx
export function TimelineBlock()
```

| Export | Install id | Purpose | Source |
|--------|------------|---------|--------|
| `AboutUsSection` | `@uitripled/about-us-section-shadcnui` | About us section with value cards, icons, and animated reveal effects `[SRC:packages/registry/registry.json:L46]` | `[SRC:packages/components/react-shadcn/src/components/sections/about-us-section.tsx:L35]` |
| `BentoGridBlock` | `@uitripled/bento-grid-block-shadcnui` | Layered bento grid with imagery, metrics, and smooth motion reveals `[SRC:packages/registry/registry.json:L591]` | `[SRC:packages/components/react-shadcn/src/components/sections/bento-grid-block.tsx:L125]` |
| `BlogBlock` | `@uitripled/blog-block-shadcnui` | Animated blog posts grid with staggered cards, date/time indicators, and hover effects `[SRC:packages/registry/registry.json:L635]` | `[SRC:packages/components/react-shadcn/src/components/sections/blog-block.tsx:L55]` |
| `FolderBrowser` | `@uitripled/browse-folder-shadcnui` | Folder browser with animated tabs and content `[SRC:packages/registry/registry.json:L721]` | `[SRC:packages/components/react-shadcn/src/components/sections/browse-folder.tsx:L21]` |
| `BrowseFolder` | `@uitripled/browse-folder-shadcnui` | exported with `FolderBrowser`, same registry entry | `[SRC:packages/components/react-shadcn/src/components/sections/browse-folder.tsx:L111]` |
| `CinemaTicket` | `@uitripled/cinema-ticket-shadcnui` | Cinematic theater ticket with rip effect and barcode `[SRC:packages/registry/registry.json:L827]` | `[SRC:packages/components/react-shadcn/src/components/sections/cinema-ticket.tsx:L7]` |
| `ConferenceTicket` | `@uitripled/conference-ticket-shadcnui` | Animated conference ticket with glassmorphism effects and holographic details `[SRC:packages/registry/registry.json:L913]` | `[SRC:packages/components/react-shadcn/src/components/sections/conference-ticket.tsx:L8]` |
| `ContactBlock` | `@uitripled/contact-block-shadcnui` | Contact form with animated contact info cards, working hours, and interactive icons `[SRC:packages/registry/registry.json:L955]` | `[SRC:packages/components/react-shadcn/src/components/sections/contact-block.tsx:L32]` |
| `ContactFormSection` | `@uitripled/contact-form-section-shadcnui` | Contact form section with animated inputs, validation, and form handling `[SRC:packages/registry/registry.json:L999]` | `[SRC:packages/components/react-shadcn/src/components/sections/contact-form-section.tsx:L38]` |
| `CTABannerSection` | `@uitripled/cta-banner-section-shadcnui` | Animated call-to-action banner with gradient background and button animations `[SRC:packages/registry/registry.json:L1152]` | `[SRC:packages/components/react-shadcn/src/components/sections/cta-banner-section.tsx:L35]` |
| `CTABlock` | `@uitripled/cta-block-shadcnui` | Call-to-action section with gradient overlay, animated buttons, and status indicator `[SRC:packages/registry/registry.json:L1194]` | `[SRC:packages/components/react-shadcn/src/components/sections/cta-block.tsx:L8]` |
| `CTAHeroBlock` | `@uitripled/cta-hero-block-shadcnui` | Engaging hero section with email signup, video preview, and social proof `[SRC:packages/registry/registry.json:L1238]` | `[SRC:packages/components/react-shadcn/src/components/sections/cta-hero-block.tsx:L17]` |
| `CurrencyConverterCard` | `@uitripled/currency-converter-card-shadcnui` | Finance conversion widget with animated inputs, simulated exchange updates, and contextual feedback `[SRC:packages/registry/registry.json:L1282]` | `[SRC:packages/components/react-shadcn/src/components/sections/currency-converter-card.tsx:L41]` |
| `FAQAccordionBlock` | `@uitripled/faq-accordion-block-shadcnui` | Expandable FAQ section with smooth accordion animations `[SRC:packages/registry/registry.json:L1603]` | `[SRC:packages/components/react-shadcn/src/components/sections/faq-accordion-block.tsx:L43]` |
| `FAQSection` | `@uitripled/faq-section-shadcnui` | Animated FAQ section with expandable questions and smooth transitions `[SRC:packages/registry/registry.json:L1647]` | `[SRC:packages/components/react-shadcn/src/components/sections/faq-section.tsx:L36]` |
| `FeatureCardsBlock` | `@uitripled/feature-cards-block-shadcnui` | Three feature cards with icons, hover effects, and glassmorphism styling `[SRC:packages/registry/registry.json:L1689]` | `[SRC:packages/components/react-shadcn/src/components/sections/feature-cards-block.tsx:L6]` |
| `FeatureComparisonBlock` | `@uitripled/feature-comparison-block-shadcnui` | Interactive pricing comparison table with animated checkmarks and plan highlights `[SRC:packages/registry/registry.json:L1734]` | `[SRC:packages/components/react-shadcn/src/components/sections/feature-comparison-block.tsx:L90]` |
| `FeatureGridSection` | `@uitripled/feature-grid-section-shadcnui` | Animated feature grid with staggered card animations and icon reveals `[SRC:packages/registry/registry.json:L1778]` | `[SRC:packages/components/react-shadcn/src/components/sections/feature-grid-section.tsx:L47]` |
| `FooterBlock` | `@uitripled/footer-block-shadcnui` | Comprehensive footer with links, newsletter signup, social icons, and scroll-to-top `[SRC:packages/registry/registry.json:L1966]` | `[SRC:packages/components/react-shadcn/src/components/sections/footer-block.tsx:L47]` |
| `GalleryGridBlock` | `@uitripled/gallery-grid-block-shadcnui` | Filterable image gallery with animated lightbox and navigation `[SRC:packages/registry/registry.json:L2010]` | `[SRC:packages/components/react-shadcn/src/components/sections/gallery-grid-block.tsx:L49]` |
| `GlassmorphismCTABlock` | `@uitripled/glassmorphism-cta-block-shadcnui` | Call-to-action section with glassy card, gradient background, and animated buttons `[SRC:packages/registry/registry.json:L2354]` | `[SRC:packages/components/react-shadcn/src/components/sections/glassmorphism-cta-block.tsx:L6]` |
| `GlassmorphismHeroBlock` | `@uitripled/glassmorphism-hero-block-shadcnui` | Modern hero section with glassmorphism effects, animated background orbs, and CTA buttons `[SRC:packages/registry/registry.json:L2398]` | `[SRC:packages/components/react-shadcn/src/components/sections/glassmorphism-hero-block.tsx:L6]` |
| `GlassmorphismLaunchTimelineBlock` | `@uitripled/glassmorphism-launch-timeline-block-shadcnui` | Frictionless launch roadmap with staggered motion, glassmorphism milestones, and paired CTA actions `[SRC:packages/registry/registry.json:L2442]` | `[SRC:packages/components/react-shadcn/src/components/sections/glassmorphism-launch-timeline-block.tsx:L65]` |
| `GlassmorphismListenAppBlock` | `@uitripled/glassmorphism-listen-app-block-shadcnui` | Music streaming block with glassmorphism player, curated highlights, and animated controls `[SRC:packages/registry/registry.json:L2486]` | `[SRC:packages/components/react-shadcn/src/components/sections/glassmorphism-listen-app-block.tsx:L78]` |
| `GlassmorphismLogoShowcaseBlock` | `@uitripled/glassmorphism-logo-showcase-block-shadcnui` | Glassmorphism partner grid with floating motion, brand hints, and collaborative call-to-action `[SRC:packages/registry/registry.json:L2530]` | `[SRC:packages/components/react-shadcn/src/components/sections/glassmorphism-logo-showcase-block.tsx:L26]` |
| `GlassmorphismMinimalMetricsBlock` | `@uitripled/glassmorphism-minimal-metrics-block-shadcnui` | Focused metric cards with glass surfaces, subtle motion, and concierge insight CTA banner `[SRC:packages/registry/registry.json:L2574]` | `[SRC:packages/components/react-shadcn/src/components/sections/glassmorphism-minimal-metrics-block.tsx:L42]` |
| `GlassmorphismPortfolioBlock` | `@uitripled/glassmorphism-portfolio-block-shadcnui` | Personal portfolio spotlight with profile portrait, narrative highlights, and animated social links `[SRC:packages/registry/registry.json:L2618]` | `[SRC:packages/components/react-shadcn/src/components/sections/glassmorphism-portfolio-block.tsx:L95]` |
| `GlassmorphismPricingBlock` | `@uitripled/glassmorphism-pricing-block-shadcnui` | Pricing cards with glassmorphism effects, hover animations, and feature lists `[SRC:packages/registry/registry.json:L2662]` | `[SRC:packages/components/react-shadcn/src/components/sections/glassmorphism-pricing-block.tsx:L7]` |
| `GlassmorphismProductUpdateBlock` | `@uitripled/glassmorphism-product-update-block-shadcnui` | Multi-state changelog cards with glass overlays, status badges, and GitHub integration banner `[SRC:packages/registry/registry.json:L2706]` | `[SRC:packages/components/react-shadcn/src/components/sections/glassmorphism-product-update-block.tsx:L37]` |
| `GlassmorphismStatisticsCard` | `@uitripled/glassmorphism-statistics-card-shadcnui` | Interactive statistics card with hover reveal and smooth transitions `[SRC:packages/registry/registry.json:L2750]` | `[SRC:packages/components/react-shadcn/src/components/sections/glassmorphism-statistics-card.tsx:L22]` |
| `GlassmorphismTestimonialsBlock` | `@uitripled/glassmorphism-testimonials-block-shadcnui` | Customer testimonials with glassmorphism cards, star ratings, and hover effects `[SRC:packages/registry/registry.json:L2795]` | `[SRC:packages/components/react-shadcn/src/components/sections/glassmorphism-testimonials-block.tsx:L6]` |
| `GlowyWavesHero` | `@uitripled/glowy-waves-hero-shadcnui` | Hero section with glowy waves effect `[SRC:packages/registry/registry.json:L2839]` | `[SRC:packages/components/react-shadcn/src/components/sections/glowy-waves-hero.tsx:L61]` |
| `HeroBlock` | `@uitripled/hero-block-shadcnui` | Personal portfolio hero section with animated avatar, staggered text, social links, and scroll indicator `[SRC:packages/registry/registry.json:L2924]` | `[SRC:packages/components/react-shadcn/src/components/sections/hero-block.tsx:L7]` |
| `HeroSection` | `@uitripled/hero-section-shadcnui` | Hero section with staggered text and button reveal `[SRC:packages/registry/registry.json:L2968]`; its entry lists no `registryDependencies`, but the file imports `@/components/ui/button` and `lucide-react` | `[AST:packages/components/react-shadcn/src/components/sections/hero-section.tsx:L7]` |
| `InteractiveLogsTable` | `@uitripled/interactive-logs-table-shadcnui` | Observability logs panel with animated filters, search, and expandable rows `[SRC:packages/registry/registry.json:L3092]` | `[SRC:packages/components/react-shadcn/src/components/sections/interactive-logs-table.tsx:L398]` |
| `N8nWorkflowBlock` | `@uitripled/n8n-workflow-block-shadcnui` | Visual workflow automation builder with animated nodes, connections, and real-time execution monitoring `[SRC:packages/registry/registry.json:L3350]` | `[SRC:packages/components/react-shadcn/src/components/sections/n8n-workflow-block.tsx:L161]` |
| `NewHeroSection` | `@uitripled/new-hero-section-shadcnui` | Modern hero section with gradient background, animated stats, and call-to-action buttons `[SRC:packages/registry/registry.json:L4618]` | `[SRC:packages/components/react-shadcn/src/components/sections/new-hero-section.tsx:L7]` |
| `NewsletterSignupBlock` | `@uitripled/newsletter-signup-block-shadcnui` | Animated newsletter subscription form with success state and gradient background `[SRC:packages/registry/registry.json:L4684]` | `[SRC:packages/components/react-shadcn/src/components/sections/newsletter-signup-block.tsx:L11]` |
| `NotionBlogPage` | `@uitripled/notion-blog-page-shadcnui` | Notion-style publishing playbook with rich text, toggles, and supporting visuals `[SRC:packages/registry/registry.json:L4750]` | `[SRC:packages/components/react-shadcn/src/components/sections/notion-blog-page.tsx:L62]` |
| `OurPartnersSection` | none | no `registry.json` entry ships this file | `[SRC:packages/components/react-shadcn/src/components/sections/our-partners-section.tsx:L15]` |
| `OurServicesSection` | `@uitripled/our-services-section-shadcnui` | Services section with service cards, badges, icons, and hover animations `[SRC:packages/registry/registry.json:L4794]` | `[SRC:packages/components/react-shadcn/src/components/sections/our-services-section.tsx:L61]` |
| `PricingSection` | `@uitripled/pricing-section-shadcnui` | Animated pricing cards with hover effects and feature lists `[SRC:packages/registry/registry.json:L4880]` | `[SRC:packages/components/react-shadcn/src/components/sections/pricing-section.tsx:L61]` |
| `ProjectsBlock` | `@uitripled/projects-block-shadcnui` | Animated project card with hover effects, image zoom, and link buttons `[SRC:packages/registry/registry.json:L5026]` | `[SRC:packages/components/react-shadcn/src/components/sections/projects-block.tsx:L18]` |
| `ScrollReveal` | `@uitripled/scroll-reveal-shadcnui` | Section that animates into view on scroll with intersection observer `[SRC:packages/registry/registry.json:L5192]` | `[SRC:packages/components/react-shadcn/src/components/sections/scroll-reveal.tsx:L47]` |
| `ServicesGridBlock` | `@uitripled/services-grid-block-shadcnui` | 8-column responsive services grid with icons, features, and hover effects `[SRC:packages/registry/registry.json:L5234]` | `[SRC:packages/components/react-shadcn/src/components/sections/services-grid-block.tsx:L92]` |
| `StatsCounterBlock` | `@uitripled/stats-counter-block-shadcnui` | Animated statistics counters with icons and gradient backgrounds `[SRC:packages/registry/registry.json:L5512]` | `[SRC:packages/components/react-shadcn/src/components/sections/stats-counter-block.tsx:L82]` |
| `StatsSection` | `@uitripled/stats-section-shadcnui` | Animated statistics section with cards and counters `[SRC:packages/registry/registry.json:L5556]` | `[SRC:packages/components/react-shadcn/src/components/sections/stats-section.tsx:L40]` |
| `TeamSectionBlock` | `@uitripled/team-section-block-shadcnui` | Animated team member cards with avatars, roles, and social links `[SRC:packages/registry/registry.json:L5642]` | `[SRC:packages/components/react-shadcn/src/components/sections/team-section-block.tsx:L326]` |
| `TestimonialSection` | `@uitripled/testimonial-section-shadcnui` | Carousel-style testimonial section with smooth transitions `[SRC:packages/registry/registry.json:L5686]` | `[SRC:packages/components/react-shadcn/src/components/sections/testimonial-section.tsx:L41]` |
| `TestimonialsBlock` | `@uitripled/testimonials-block-shadcnui` | Animated testimonials grid with staggered cards, star ratings, and hover effects `[SRC:packages/registry/registry.json:L5728]` | `[SRC:packages/components/react-shadcn/src/components/sections/testimonials-block.tsx:L55]` |
| `TheaterTicket` | `@uitripled/theater-ticket-shadcnui` | Cinematic theater ticket with rip effect and barcode `[SRC:packages/registry/registry.json:L5772]` | `[SRC:packages/components/react-shadcn/src/components/sections/theater-ticket.tsx:L7]` |
| `TimelineBlock` | `@uitripled/timeline-block-shadcnui` | Vertical timeline with alternating cards and animated progress line `[SRC:packages/registry/registry.json:L5814]` | `[SRC:packages/components/react-shadcn/src/components/sections/timeline-block.tsx:L47]` |

## Composite components

```tsx
// components/components/account-switcher/multiple-accounts.tsx
export function MultipleAccounts()
// components/components/blog/blog-typography.tsx
export function BlogTypography()
// components/components/cards/image-slider-card.tsx
export function ImageSliderCard()
// components/components/cards/shadcnui/animated-card-stack.tsx
export function AnimatedCardStack()
// components/components/cards/shadcnui/credit-card.tsx
export function CreditCard({ cardNumber = "4532 1234 5678 9010", cardholderName = "JORDAN PARK", expiryDate = "09/27", cvv = "123" }: CreditCardProps)
// components/components/cards/shadcnui/detail-task.tsx
export function DetailTaskCard()
// components/components/cards/shadcnui/ecommerce-highlight-card.tsx
export function EcommerceHighlightCard()
// components/components/cards/shadcnui/glass-blog-card.tsx
export function GlassBlogCard({ title = defaultPost.title, excerpt = defaultPost.excerpt, image = defaultPost.image, author = defaultPost.author, date = defaultPost.date, readTime = defaultPost.readTime, tags = defaultPost.tags, className }: GlassBlogCardProps)
// components/components/cards/shadcnui/glass-checkout-card.tsx
export function GlassCheckoutCard({ amount = 85.8, className }: GlassCheckoutCardProps)
// components/components/cards/shadcnui/glass-order-summary.tsx
export function GlassOrderSummary({ items = defaultItems, subtotal = 78.0, tax = 7.8, shipping = 0, total = 85.8, className }: GlassOrderSummaryProps)
// components/components/cards/shadcnui/glass-wallet-card.tsx
export function GlassWalletCard({ balance = defaultWallet.balance, currency = defaultWallet.currency, address = defaultWallet.address, trend = defaultWallet.trend, trendUp = defaultWallet.trendUp, cardHolder = defaultWallet.cardHolder, expiry = defaultWallet.expiry, className }: GlassWalletCardProps)
// components/components/cards/shadcnui/hover-expand.tsx
export function HoverExpandCard()
// components/components/cards/shadcnui/project-card.tsx
export function ProjectCard({ title = defaultProject.title, description = defaultProject.description, tags = defaultProject.tags, image = defaultProject.image, links = defaultProject.links, className }: ProjectCardProps)
// components/components/cards/tweet-card.tsx
export function TweetCard({ author, content, url, className }: TweetCardProps)
// components/components/chat/ai-chat-interface.tsx
export function AIChatInterface()
// components/components/chat/chat-app.tsx
export function ChatApp()
// components/components/chat/floating-chat-widget.tsx
export function FloatingChatWidget()
// components/components/chat/messenger.tsx
export function Messenger()
// components/components/comments/comment-thread.tsx
export function CommentThread()
// components/components/course-content/course-content-page.tsx
export function CourseContentPage()
// components/components/dropdown/staggered-items.tsx
export function StaggeredDropdown()
// components/components/forms/glass-account-settings.tsx
export function GlassAccountSettingsCard()
// components/components/forms/glass-forgot-password.tsx
export function GlassForgotPasswordCard()
// components/components/forms/glass-profile-settings.tsx
export function GlassProfileSettingsCard()
// components/components/forms/glass-sign-in.tsx
export function GlassSignInCard()
// components/components/forms/glass-sign-up.tsx
export function GlassSignUpCard()
// components/components/forms/glass-verification-code.tsx
export function GlassVerificationCodeCard()
// components/components/inputs/floating-label-input.tsx
export function FloatingLabelInput()
// components/components/kanban/kanban-board.tsx
export function KanbanBoard()
// components/components/lists/animated-list.tsx
export function AnimatedList()
// components/components/lists/draggable-list.tsx
export function DraggableList()
// components/components/modal/fade-slide.tsx
export function FadeSlideModal()
// components/components/news-feed/news-feed.tsx
export function NewsFeed()
// components/components/notifications/notification-center.tsx
export function NotificationCenter()
// components/components/profile/profile-page.tsx
export function ProfilePage()
// components/components/resumes/shadcnui/minimal-resume.tsx
export function MinimalResume()
// components/components/resumes/shadcnui/professional-resume.tsx
export function ProfessionalResume()
// components/components/resumes/shadcnui/resume-card.tsx
export function ResumeCard()
// components/components/resumes/shadcnui/standard-resume.tsx
export function StandardResume()
// components/components/sliders/cards-slider.tsx
export function CardsSlider()
// components/components/sliders/volume-component.tsx
export function VolumeComponent({ min = 0, max = 100, step = 1, defaultValue = 0, onChange, className, label = "Volume" }: SliderProps)
// components/components/stocks-dashboard/dashboard.tsx
export function DashboardPage()
// components/components/stocks-dashboard/stocks-dashboard.tsx
export function StocksDashboard()
// components/components/tabs/animated-tabs.tsx
export function AnimatedTabs()
// components/components/weather/weather-dashboard.tsx
export function WeatherDashboard(): React.ReactElement
```

| Export | Install id | Purpose | Source |
|--------|------------|---------|--------|
| `MultipleAccounts` | `@uitripled/multiple-accounts-shadcnui` | Glassmorphic account switcher with animated dropdown and accessible listbox controls `[SRC:packages/registry/registry.json:L3306]` | `[SRC:packages/components/react-shadcn/src/components/components/account-switcher/multiple-accounts.tsx:L42]` |
| `BlogTypography` | `@uitripled/blog-typography-shadcnui` | Beautiful blog post typography with text, links, images, blockquotes, and code examples `[SRC:packages/registry/registry.json:L657]` | `[SRC:packages/components/react-shadcn/src/components/components/blog/blog-typography.tsx:L132]` |
| `ImageSliderCard` | `@uitripled/image-slider-card-shadcnui` | Image carousel card with keyboard support, reduced motion handling, and screen reader-friendly labels `[SRC:packages/registry/registry.json:L3050]` | `[SRC:packages/components/react-shadcn/src/components/components/cards/image-slider-card.tsx:L43]` |
| `AnimatedCardStack` | `@uitripled/animated-card-stack-shadcnui` | Stacked cards that expand on hover `[SRC:packages/registry/registry.json:L220]` | `[SRC:packages/components/react-shadcn/src/components/components/cards/shadcnui/animated-card-stack.tsx:L18]` |
| `CreditCard` | `@uitripled/credit-card-shadcnui` | 3D animated credit card with flip animation to show CVV `[SRC:packages/registry/registry.json:L1110]` | `[SRC:packages/components/react-shadcn/src/components/components/cards/shadcnui/credit-card.tsx:L31]` |
| `DetailTaskCard` | `@uitripled/detail-task-card-shadcnui` | Task management detail panel with animated assignee chips and editor controls `[SRC:packages/registry/registry.json:L1371]` | `[SRC:packages/components/react-shadcn/src/components/components/cards/shadcnui/detail-task.tsx:L115]` |
| `EcommerceHighlightCard` | `@uitripled/ecommerce-highlight-card-shadcnui` | Product spotlight card with blurred border, bundle selector, and fulfillment details `[SRC:packages/registry/registry.json:L1497]` | `[SRC:packages/components/react-shadcn/src/components/components/cards/shadcnui/ecommerce-highlight-card.tsx:L64]` |
| `GlassBlogCard` | `@uitripled/glass-blog-card-shadcnui` | Glassmorphism blog card with image zoom, author info, and read action `[SRC:packages/registry/registry.json:L2076]` | `[SRC:packages/components/react-shadcn/src/components/components/cards/shadcnui/glass-blog-card.tsx:L39]` |
| `GlassCheckoutCard` | `@uitripled/glass-checkout-card-shadcnui` | Glassmorphism checkout card with payment method selector and input fields `[SRC:packages/registry/registry.json:L2118]` | `[SRC:packages/components/react-shadcn/src/components/components/cards/shadcnui/glass-checkout-card.tsx:L17]` |
| `GlassOrderSummary` | `@uitripled/glass-order-summary-shadcnui` | Glassmorphism order summary card with item list and checkout button `[SRC:packages/registry/registry.json:L2182]` | `[SRC:packages/components/react-shadcn/src/components/components/cards/shadcnui/glass-order-summary.tsx:L49]` |
| `GlassWalletCard` | `@uitripled/glass-wallet-card-shadcnui` | Glassmorphism crypto wallet card with balance, trend, and action buttons `[SRC:packages/registry/registry.json:L2312]` | `[SRC:packages/components/react-shadcn/src/components/components/cards/shadcnui/glass-wallet-card.tsx:L36]` |
| `HoverExpandCard` | `@uitripled/hover-expand-card-shadcnui` | Card that lifts and expands on hover `[SRC:packages/registry/registry.json:L3030]` | `[SRC:packages/components/react-shadcn/src/components/components/cards/shadcnui/hover-expand.tsx:L6]` |
| `ProjectCard` | `@uitripled/project-card-shadcnui` | Glassmorphism project card with links, tags, and hover effects `[SRC:packages/registry/registry.json:L4984]` | `[SRC:packages/components/react-shadcn/src/components/components/cards/shadcnui/project-card.tsx:L31]` |
| `TweetCard` | none | no `registry.json` entry ships this file; props `TweetCardProps` | `[SRC:packages/components/react-shadcn/src/components/components/cards/tweet-card.tsx:L17]` |
| `AIChatInterface` | `@uitripled/ai-chat-interface-shadcnui` | Chat input with attachments, model selector, and accessible controls `[SRC:packages/registry/registry.json:L68]` | `[SRC:packages/components/react-shadcn/src/components/components/chat/ai-chat-interface.tsx:L54]` |
| `ChatApp` | `@uitripled/chat-app-shadcnui` | Fully functional chat interface with animated messages `[SRC:packages/registry/registry.json:L783]` | `[SRC:packages/components/react-shadcn/src/components/components/chat/chat-app.tsx:L39]` |
| `FloatingChatWidget` | `@uitripled/floating-chat-widget-shadcnui` | Floating chat widget with AI agent selection dropdown and animations `[SRC:packages/registry/registry.json:L1798]` | `[SRC:packages/components/react-shadcn/src/components/components/chat/floating-chat-widget.tsx:L112]` |
| `Messenger` | `@uitripled/messenger-shadcnui` | Glassmorphism messenger workspace with accessible motion and quick replies `[SRC:packages/registry/registry.json:L3222]` | `[SRC:packages/components/react-shadcn/src/components/components/chat/messenger.tsx:L162]` |
| `CommentThread` | `@uitripled/comment-thread-shadcnui` | Nested comment thread with rich interactions and animations `[SRC:packages/registry/registry.json:L869]` | `[SRC:packages/components/react-shadcn/src/components/components/comments/comment-thread.tsx:L533]` |
| `CourseContentPage` | `@uitripled/course-content-page-shadcnui` | Interactive course page with video player, instructor details, curriculum sections, and progress tracking `[SRC:packages/registry/registry.json:L1066]` | `[SRC:packages/components/react-shadcn/src/components/components/course-content/course-content-page.tsx:L786]` |
| `StaggeredDropdown` | `@uitripled/staggered-dropdown-shadcnui` | Dropdown menu with staggered item animations `[SRC:packages/registry/registry.json:L5406]` | `[SRC:packages/components/react-shadcn/src/components/components/dropdown/staggered-items.tsx:L9]` |
| `GlassAccountSettingsCard` | `@uitripled/glass-account-settings-card-shadcnui` | Account management card with subscription overview and billing actions in glassmorphic style `[SRC:packages/registry/registry.json:L2032]` | `[SRC:packages/components/react-shadcn/src/components/components/forms/glass-account-settings.tsx:L17]` |
| `GlassForgotPasswordCard` | `@uitripled/glass-forgot-password-card-shadcnui` | Reset-password screen with glassmorphic styling and status messaging `[SRC:packages/registry/registry.json:L2138]` | `[SRC:packages/components/react-shadcn/src/components/components/forms/glass-forgot-password.tsx:L9]` |
| `GlassProfileSettingsCard` | `@uitripled/glass-profile-settings-card-shadcnui` | Glassmorphic profile settings form with avatar upload, bio, and notification preferences `[SRC:packages/registry/registry.json:L2202]` | `[SRC:packages/components/react-shadcn/src/components/components/forms/glass-profile-settings.tsx:L14]` |
| `GlassSignInCard` | `@uitripled/glass-sign-in-card-shadcnui` | Glassmorphic sign-in panel with social auth buttons and email form `[SRC:packages/registry/registry.json:L2224]` | `[SRC:packages/components/react-shadcn/src/components/components/forms/glass-sign-in.tsx:L17]` |
| `GlassSignUpCard` | `@uitripled/glass-sign-up-card-shadcnui` | Glassmorphic sign-up flow with social providers, email fields, and terms checkbox `[SRC:packages/registry/registry.json:L2246]` | `[SRC:packages/components/react-shadcn/src/components/components/forms/glass-sign-up.tsx:L17]` |
| `GlassVerificationCodeCard` | `@uitripled/glass-verification-code-card-shadcnui` | Verification code entry with glassmorphic inputs, status messaging, and reduced-motion support `[SRC:packages/registry/registry.json:L2268]` | `[SRC:packages/components/react-shadcn/src/components/components/forms/glass-verification-code.tsx:L10]` |
| `FloatingLabelInput` | `@uitripled/floating-label-input-shadcnui` | Input with animated floating label `[SRC:packages/registry/registry.json:L1860]` | `[SRC:packages/components/react-shadcn/src/components/components/inputs/floating-label-input.tsx:L7]` |
| `KanbanBoard` | `@uitripled/kanban-board-shadcnui` | Interactive Kanban board with drag-and-drop, glassmorphism styling, and task management features `[SRC:packages/registry/registry.json:L3136]` | `[SRC:packages/components/react-shadcn/src/components/components/kanban/kanban-board.tsx:L142]` |
| `AnimatedList` | `@uitripled/animated-list-shadcnui` | List with staggered item animations `[SRC:packages/registry/registry.json:L284]` | `[SRC:packages/components/react-shadcn/src/components/components/lists/animated-list.tsx:L43]` |
| `DraggableList` | `@uitripled/draggable-list-shadcnui` | Reorderable list with drag and drop spring physics `[SRC:packages/registry/registry.json:L1413]` | `[SRC:packages/components/react-shadcn/src/components/components/lists/draggable-list.tsx:L14]` |
| `FadeSlideModal` | `@uitripled/fade-slide-modal-shadcnui` | Modal with fade backdrop and slide-up animation `[SRC:packages/registry/registry.json:L1559]` | `[SRC:packages/components/react-shadcn/src/components/components/modal/fade-slide.tsx:L7]` |
| `NewsFeed` | `@uitripled/news-feed-shadcnui` | Interactive news feed with categories, search, and animated cards `[SRC:packages/registry/registry.json:L4640]` | `[SRC:packages/components/react-shadcn/src/components/components/news-feed/news-feed.tsx:L243]` |
| `NotificationCenter` | `@uitripled/notification-center-shadcnui` | Multi-variant notification stack with accessible announcements, actions, and motion states `[SRC:packages/registry/registry.json:L4706]` | `[SRC:packages/components/react-shadcn/src/components/components/notifications/notification-center.tsx:L86]` |
| `ProfilePage` | `@uitripled/profile-page-shadcnui` | User profile with gradient cover, stats, and posts feed `[SRC:packages/registry/registry.json:L4942]` | `[SRC:packages/components/react-shadcn/src/components/components/profile/profile-page.tsx:L16]` |
| `MinimalResume` | `@uitripled/minimal-resume-shadcnui` | Vercel-inspired minimal resume with clean typography and grid layout `[SRC:packages/registry/registry.json:L3266]` | `[SRC:packages/components/react-shadcn/src/components/components/resumes/shadcnui/minimal-resume.tsx:L83]` |
| `ProfessionalResume` | `@uitripled/professional-resume-shadcnui` | Clean, formal resume template suitable for corporate applications `[SRC:packages/registry/registry.json:L4922]` | `[SRC:packages/components/react-shadcn/src/components/components/resumes/shadcnui/professional-resume.tsx:L59]` |
| `ResumeCard` | `@uitripled/resume-card-shadcnui` | Professional resume template with animated sections and interactive elements `[SRC:packages/registry/registry.json:L5090]` | `[SRC:packages/components/react-shadcn/src/components/components/resumes/shadcnui/resume-card.tsx:L138]` |
| `StandardResume` | `@uitripled/standard-resume-shadcnui` | A standard, professional resume layout with a sidebar, suitable for most industries. `[SRC:packages/registry/registry.json:L5470]` | `[SRC:packages/components/react-shadcn/src/components/components/resumes/shadcnui/standard-resume.tsx:L98]` |
| `CardsSlider` | `@uitripled/cards-slider-shadcnui` | Liquid smooth draggable cards slider with shadcn/ui styling and framer-motion animations `[SRC:packages/registry/registry.json:L743]` | `[SRC:packages/components/react-shadcn/src/components/components/sliders/cards-slider.tsx:L87]` |
| `VolumeComponent` | `@uitripled/volume-component-shadcnui` | A smooth, draggable volume slider component with framer-motion animations and shadcn styling. `[SRC:packages/registry/registry.json:L5856]` | `[SRC:packages/components/react-shadcn/src/components/components/sliders/volume-component.tsx:L17]` |
| `DashboardPage` | `@uitripled/dashboard-shadcnui` | Interactive stock portfolio dashboard with status cards, data table, and detailed stock information modal `[SRC:packages/registry/registry.json:L1327]` | `[SRC:packages/components/react-shadcn/src/components/components/stocks-dashboard/dashboard.tsx:L605]` |
| `StocksDashboard` | `@uitripled/stocks-dashboard-shadcnui` | Interactive stock portfolio dashboard with status cards, data table, and detailed stock information modal `[SRC:packages/registry/registry.json:L5576]` | `[SRC:packages/components/react-shadcn/src/components/components/stocks-dashboard/stocks-dashboard.tsx:L454]` |
| `AnimatedTabs` | `@uitripled/animated-tabs-shadcnui` | Tabs with sliding indicator animation `[SRC:packages/registry/registry.json:L482]` | `[SRC:packages/components/react-shadcn/src/components/components/tabs/animated-tabs.tsx:L7]` |
| `WeatherDashboard` | `@uitripled/weather-dashboard-shadcnui` | Immersive weather dashboard with hourly charting, weekly outlook, and live air-quality alerts `[SRC:packages/registry/registry.json:L5878]` | `[SRC:packages/components/react-shadcn/src/components/components/weather/weather-dashboard.tsx:L390]` |
