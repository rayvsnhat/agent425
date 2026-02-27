# Product Requirements Document (PRD) for Seattle AI Consultants Landing Page

## 1. Overview

### Project Summary

This landing page serves as the digital storefront for Seattle AI Consultants, an AI consulting firm founded by Nhat and Ebrima in Seattle, Washington. The company specializes in helping businesses in Washington state—specifically law firms and home services providers (e.g., HVAC, plumbing, electrical)—evaluate their workflows, identify pain points, and implement existing AI tools to improve operational efficiency, quality of life, and ROI. The page emphasizes education and value demonstration over hard selling, guiding users through a multi-page structure: a main entry page for industry selection, followed by tailored landing pages for law firms or home services.

### Key Objectives

- Educate visitors on AI's potential to address industry-specific pain points and capture missed ROI.
- Capture leads via email sign-ups for free AI resources and "book a call" CTAs linked to a scheduling tool like Calendly.
- Drive conversions toward the service cycle (Report → On-Site Audit → Implementation) without displaying pricing.
- Achieve a seamless, modern user experience that builds trust and positions the company as AI experts for local businesses.
- Target: Increase email sign-ups by 15-20% and call bookings by 10% in the first quarter post-launch.

### Scope

- In Scope: Main entry page with industry selector; two dedicated landing pages (one for law firms, one for home services) with shared structure but tailored content; email capture forms; "book a call" integration; dark/light mode toggle; smooth animations/transitions; interactive slide decks/carousels for data/demos; borders for section contrast.
- Out of Scope: Full backend for report generation (handle via external tools like Google Forms initially); e-commerce or payment processing; advanced personalization beyond industry selection; mobile apps or additional sub-pages.

## 2. Target Audience

- Primary: Business owners and decision-makers in Washington state law firms (e.g., small to mid-sized practices dealing with case management, research, and client interactions) and home services companies (e.g., HVAC, plumbing, electrical firms managing scheduling, customer service, and field operations). Demographics: Ages 35-60, tech-adopters open to innovation but overwhelmed by daily operations.
- Pain Points: Inefficient workflows leading to missed revenue (e.g., manual scheduling in home services causing delays; repetitive research in law firms wasting billable hours); lack of awareness about accessible AI tools like autonomous agents or AI briefs that could automate tasks and boost ROI.
- User Journey: Visitors arrive via local SEO, ads, or social media; select industry on main page; explore tailored content; sign up for emails or book a call within 1-2 minutes. Assume good intent for quick value delivery, focusing on empowerment.

## 3. Functional Requirements

### Core Features/Sections

The site uses a branched structure:

- **Main Entry Page**: Hero section only, exactly matching the reference screenshot (large bold headline like "We build AI tools for your business.", subheadline, CTA button)—adapt with catchy slogan (e.g., "Unlock AI-Powered Efficiency for Your Washington Business"), email sign-up form for free AI tips, and two prominent buttons/choices: "Law Firms" and "Home Services" to redirect to dedicated pages. Make sure the color scheme of this hero section matches with the overal color scheme of the website. The reference screenshot for this hero section is in the "website design reference" folder, named "hero-section-reference.png"
- **Dedicated Landing Pages (Law Firms or Home Services)**: Tailored content starting from:
  1. Mission Statement
  2. Data/Facts/Key Points/ROI Section (interactive slide deck/carousel)
  3. Services Section (with "Book a Call" button)
  4. Demo Section (carousel with next/prev)
  5. About Us Section
  6. FAQ Section
  7. Join Emailing List Section
  8. Footer

### Technical Requirements

- Built with HTML/CSS/JS; use **Tailwind CSS via CDN** (`<script src="https://cdn.tailwindcss.com"></script>`) for rapid development and styling.
- **Mobile-first responsive design**: Start all layouts for smallest screens (phones ~320-480px), then use Tailwind breakpoints (`sm:`, `md:`, `lg:`, `xl:`) to enhance for tablets and desktops. Default styles = mobile; prefixed classes add tablet/desktop improvements.
- **Performance & Speed Optimization** (critical for mobile users):
  - Aim for <2s load time (ideally <1.5s on 3G/4G).
  - Lazy-load images, demos, and embeds (`loading="lazy"` on `<img>`, iframes).
  - Use placeholder images (`https://placehold.co/...`) initially; optimize real images (WebP format, compressed <100KB where possible).
  - Minimize heavy animations (only transform + opacity; short durations).
  - Avoid bloated class lists — reuse patterns/components to limit unique utilities.
  - In production mindset: Even with CDN, write code that would purge well (avoid unnecessary variants).
  - Ensure fast perceived load: Hero loads first, critical content above fold, defer non-critical JS.
- Features: Dark/light mode toggle (top-right, persist via localStorage); smooth scroll transitions (fade-ins); consistent button states (see Design section).
- Integrations: Email forms (Mailchimp/Google Forms); Calendly embed (lazy-loaded).
- Accessibility: Alt text, ARIA labels, keyboard nav, sufficient touch targets (min 44×44px for buttons/taps).

## 4. Design and Branding Guidelines

### Brand Style

- **Colors**: Primary: #002244 (College Navy); Secondary/CTAs: #69BE28 (Action Green); Neutral: #A5ACAF (Wolf Gray); Light bg: #FFFFFF; Dark mode: navy base + green highlights.
- **Button Interaction States (consistent across ALL buttons)**:

  - Default: White/transparent bg, navy/white text.
  - Hover: bg #69BE28, text white, scale(1.05), subtle shadow/glow.
  - Active/Clicked: bg #5AA023 (darker green), scale(0.98).
  - Focus: green outline.
    Use: `hover:bg-[#69BE28] hover:text-white active:bg-[#5AA023] active:scale-95 transition-colors duration-200 ease-out`
- **Mobile-First & Performance Design Principles** (MANDATORY):

  - **Mobile-first approach**: Design & code for phones/tablets first (single-column, large tappable buttons ≥44px, thumb-friendly navigation, prioritized content above fold). Use Tailwind's mobile-default utilities, then add `md:`, `lg:` prefixes only for enhancements.
  - Breakpoints: Follow Tailwind defaults (sm:640px, md:768px, lg:1024px, xl:1280px) — test at 320-480px (small phones), 768px (tablets), up.
  - Layout: Fluid/flexible grids (Tailwind flex/grid), relative units (rem/em/%/vw), container queries if needed for component-level responsiveness.
  - Touch optimization: Large touch targets, no hover-only interactions (use focus/active too), avoid tiny text (<16px body).
  - Speed focus: Prioritize fast load — hero critical CSS first, lazy non-visible assets, minimal JS, no heavy fonts (system + Inter/Roboto subset if needed), compressed assets.
  - Testing mindset: Ensure smooth experience on real mobile devices (fast scroll, no layout shifts, quick interactions).
- **Typography**: Inter Bold headings, Roboto body; min 16px body text on mobile.
- **Imagery**: Abstract AI visuals; lazy-load + responsive sizes (`srcset` if possible).
- **Tone and Voice**: Professional, empowering.
- **Layout Principles**: Simplistic, modern, white space, borders for contrast (Alia-inspired), subtle animations.

### UX Best Practices

- Navigation: Simple, thumb-reachable on mobile.
- CTAs: Prominent, green, with defined states.
- Flow: Seamless branching; fast mobile load & interaction.

## 5. Inspirations from Other Websites

- **HubSpot's Landing Pages**: For branched industry selectors and ROI-focused data sections; adapt their clean forms and CTAs for your email captures.
- **Accenture AI Consulting**: Inspired by mission-driven heroes and service breakdowns; use their demo-style tool showcases for your carousel.
- **Local Seattle Vibes (e.g., Microsoft Landing Pages)**: Pull energetic, tech-forward designs with blue-green palettes; incorporate smooth animations like their scroll transitions.
- **SaaS Examples like Zapier**: For AI tool demos in action (horizontal scrolls showing integrations); tailor to law/home services pain points.
- **Calendly's Own Site**: Simple booking embeds; ensure your "book a call" flows similarly.
- **Alia Popups (https://www.aliapopups.com/)**: For animations, interactive scroll/click through slide decks/information, borders around sections for contrast, color scheme (matching Seahawks), fonts, strategic sizing/bolding.
- **Sathi Group AI (https://www.sathigroup.ai/)**: For overall format, styling, font choices, simplicity; especially the hero section (exact match required, except the color scheme, as stated above, match it with the website overal color scheme. and come up with a catchy slogan).
- Visual Inspirations: Seahawks-themed glows (e.g., stadium lights for section transitions). For modern simplicity, reference Minimalist AI sites like Anthropic's clean layouts.

## 6. Success Metrics

- Conversion Rate: >10% email sign-ups; >5% call bookings.
- Bounce Rate: <35% on dedicated pages.
- Engagement: Average time on page >1 minute; demo interactions tracked.
- Performance: PageSpeed Insights mobile score >85; load time <2s.
