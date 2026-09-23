# Design System: Raafi Syarahil Azhar Portfolio

## Brand Identity

**Name:** Raafi Syarahil Azhar
**Role:** Backend Developer (Laravel, PHP, Python)
**Focus:** Scalable, secure, efficient web applications with real-world impact
**Audience:** Potential employers, clients, technical peers
**Tone:** Professional, competent, builder-focused — not "creative" or "playful"

## Color Palette

**Core Colors (3 + neutral):**
- **Primary:** `#1a1a2e` — Deep navy/near-black. Used for primary text, key headings, primary actions.
- **Secondary:** `#2d3748` — Slate gray. Used for secondary text, borders, subtle backgrounds.
- **Accent:** `#d97706` — Amber 600. Used ONLY for primary CTA, active nav state, key link hover. One deliberate accent.
- **Neutral Base:** `#fafafa` (light) / `#0f0f0f` (dark) — Page background.
- **Surface:** `#ffffff` (light) / `#1a1a2e` (dark) — Card/panel backgrounds.
- **Muted:** `#71717a` — Placeholder text, disabled states, subtle dividers.

**Usage Rules:**
- Accent appears at most 2x per page: primary CTA + one secondary moment (active nav, key link).
- No gradients as backgrounds. Solid colors only.
- Dark mode is a real toggle, not a default. Light is default for content-first readability.

## Typography

**Font Stack:** System UI stack (no external font load)
- `font-sans: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif`
- `font-mono: ui-monospace, SFMono-Regular, "SF Mono", Menlo, monospace`

**Scale (clamped, fluid):**
- Display: `clamp(2.5rem, 5vw, 4rem)` / 1.1 leading / 700 weight
- H1: `clamp(2rem, 4vw, 3rem)` / 1.2 leading / 700 weight
- H2: `clamp(1.5rem, 3vw, 2.25rem)` / 1.3 leading / 600 weight
- H3: `1.25rem` / 1.4 leading / 600 weight
- Body: `1rem` / 1.6 leading / 400 weight
- Small: `0.875rem` / 1.5 leading / 400 weight
- Mono (code): `0.875rem` / 1.6 leading / 400 weight

**No:** Monospace headings, uppercase tracking, decorative type.

## Spacing Scale

Base unit: `4px` (0.25rem)

| Token | Value | Use Case |
|-------|-------|----------|
| space-1 | 4px | Inline gaps, icon-text |
| space-2 | 8px | Tight component padding |
| space-3 | 12px | Form field gaps |
| space-4 | 16px | Standard card padding |
| space-5 | 20px | Section inner padding |
| space-6 | 24px | Component margins |
| space-8 | 32px | Section vertical rhythm |
| space-10 | 40px | Major section separation |
| space-12 | 48px | Page-level rhythm |
| space-16 | 64px | Hero/landing breathing room |

**Rhythm Rule:** Sections alternate density. Not every section uses space-12. Dense sections (lists, tables) use space-6. Breathing sections (hero, CV header) use space-12 to space-16.

## Border Radius

**Three radii only:**
- `radius-sm: 4px` — Inputs, buttons, badges, inline elements
- `radius-md: 8px` — Cards, panels, dropdowns, modals
- `radius-lg: 16px` — Hero image, primary featured container (max 1 per page)

**No:** Pill/radius-full on everything. No uniform rounding.

## Shadows

**Two elevations only:**
- `shadow-low: 0 1px 3px rgba(0,0,0,0.08), 0 1px 2px rgba(0,0,0,0.06)` — Default card/panel (most surfaces)
- `shadow-high: 0 10px 25px rgba(0,0,0,0.1), 0 4px 10px rgba(0,0,0,0.06)` — ONE elevated element per page (hero card, primary modal, featured project)

**No:** Shadow on every card. No large diffuse shadows. Most surfaces sit flat.

## Glass/Blur

**Dose cap: 1 element per page.**
- Used only on sticky header (backdrop-blur + semi-transparent surface) for scroll context.
- Never on cards, modals, sidebars simultaneously.

## Motion

**MOTION dial: 2 (Purposeful transitions only)**
- `transition-colors: 150ms ease` — Hover/focus on interactive elements
- `transition-transform: 200ms ease` — Pressed state on buttons (scale 0.98)
- `transition-opacity: 200ms ease` — Fade in/out for modals, dropdowns
- **No:** Endless loops, floating, bounce, fade-up on scroll, stagger animations.

## Icons

**Set:** Inline SVG, custom-drawn or from a single curated set (Heroicons outline style).
- Used only when they add meaning (external link, download, email, GitHub, LinkedIn).
- No decorative icons on headings, feature lists, or section labels.
- Size: 16px inline, 20px standalone, 24px feature callout.

## Components

### Button
- Primary: `bg-[accent] text-white px-5 py-2.5 rounded-sm font-medium transition-colors hover:bg-amber-700 active:scale-[0.98]`
- Secondary: `bg-transparent border border-[secondary] text-[primary] px-5 py-2.5 rounded-sm font-medium transition-colors hover:bg-[secondary]/10`
- Ghost: `text-[primary] px-3 py-2 font-medium transition-colors hover:text-[accent]`
- **No:** Arrows on every button. No glow. No pill radius.

### Card
- `bg-[surface] border border-[muted]/20 rounded-md shadow-low p-4 md:p-5`
- Featured card (max 1): `shadow-high rounded-lg`
- **No:** Hover scale, hover shadow escalation, decorative left stripe.

### Nav Link
- `text-[secondary] font-medium transition-colors hover:text-[primary]`
- Active: `text-[accent] font-semibold`

### Section Header
- H2 + optional 1-line description (max 60 chars)
- No eyebrow badge, no decorative line, no emoji.

## Page Templates

### Homepage (index.html)
**Structure:** Hero → Selected Projects (3 max) → Skills Summary → CV Link → Footer
**Rhythm:** Hero (space-16) → Projects (space-10) → Skills (space-8) → CTA (space-12)

### Portfolio Index (portfolio.html)
**Structure:** Header → Project Grid (all 6) → Footer
**Rhythm:** Dense grid, uniform cards, no hero.

### Project Detail (preview-*.html)
**Structure:** Header (project title + back link) → Overview → Two-column: Features / Tech Stack → Gallery → Footer
**Rhythm:** Overview (space-8) → Two-col (space-10) → Gallery (space-8)

### CV (cv.html)
**Structure:** Header (name/role/contact) → Education → Experience → Projects (grouped) → Skills → Certifications → Languages → Download
**Rhythm:** Dense lists, clear hierarchy, scannable. No cards — use typography and spacing.

## Antislop Compliance Notes

- **R-01:** No default gradients. Solid colors from palette.
- **R-04:** No decorative emoji. Icons only for external links, download, contact.
- **R-05:** Section order follows content priority, not template.
- **R-06:** System font stack, no decorative type.
- **R-07:** No background grids/texture.
- **R-09:** No eyebrow badges, no AI capsule badges.
- **R-10:** Glass only on sticky header.
- **R-11:** Three radii only, applied deliberately.
- **R-12:** Two shadows only, most surfaces flat.
- **R-13:** No glow. Accent only on primary CTA + active nav.
- **R-14:** Project cards vary by content weight (featured vs standard).
- **R-17/18/38:** All numbers, metrics, content are real. No filler.
- **R-19:** Motion only on interaction, no loops.
- **R-21:** Light default, dark toggle works.
- **R-23/27:** Empty states honest. No fake data.
- **R-24/26:** All links functional. Back links work. No dead ends.
- **R-29:** 3 core colors + 1 accent. Restraint.
- **R-31:** Accent at key moments only.
- **R-34/36/C-4/C-5:** Keyboard accessible, real content, honest states.