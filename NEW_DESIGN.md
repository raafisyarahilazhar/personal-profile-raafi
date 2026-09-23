# NEW_DESIGN.md — Raafi Syarahil Azhar Portfolio
**Dark-first, technical-editorial. Near-black surfaces, amber accent, strict grid.**

---

## Brand Identity
**Name:** Raafi Syarahil Azhar
**Role:** Backend Developer — Laravel, PHP, Python
**Focus:** Scalable, secure, efficient systems.
**Audience:** Engineering leads, CTOs, technical founders.
**Tone:** Precise, confident, no fluff.

---

## Color Palette (Dark Default)
**2 Core + 1 Accent + Semantic**

| Token | Hex | Role |
|-------|-----|------|
| `bg` | `#0a0a0a` | Page background |
| `bg-elevated` | `#141414` | Cards, panels, modals |
| `border` | `#262626` | Dividers, borders, input borders |
| `border-hover` | `#3d3d3d` | Hover borders |
| `fg` | `#fafafa` | Primary text, headings |
| `fg-muted` | `#a3a3a3` | Secondary text, descriptions |
| `fg-subtle` | `#737373` | Placeholders, meta, timestamps |
| `accent` | `#fbbf24` | **One accent** — primary CTA, active nav, key links, focus rings |
| `accent-hover` | `#f59e0b` | Hover/active |
| `accent-dim` | `#78350f` | Subtle backgrounds (badges, tags) |
| `success` | `#4ade80` | Positive states only |
| `warning` | `#fbbf24` | Caution states only |
| `error` | `#f87171` | Destructive states only |

**Rules:**
- **Dark is default.** No light mode toggle needed unless requested.
- Accent = `#fbbf24` (amber-400). Appears **max 2× per page**: primary CTA + one secondary (active nav, key link).
- No gradients. Solid colors only.
- Semantic colors only for real states.

---

## Typography
**Stack: System UI (no external requests)**

```css
font-sans: ui-sans-serif, system-ui, -apple-system, "Segoe UI", Roboto, sans-serif;
font-mono: ui-monospace, SFMono-Regular, "SF Mono", Menlo, monospace;
```

**Scale (fluid, clamped):**

| Token | Size | Line | Weight | Use |
|-------|------|------|--------|-----|
| `display` | `clamp(2.5rem, 6vw, 5rem)` | 1.05 | 700 | Hero headline (homepage only) |
| `h1` | `clamp(2rem, 4.5vw, 3.5rem)` | 1.1 | 700 | Page titles |
| `h2` | `clamp(1.5rem, 3vw, 2.25rem)` | 1.2 | 600 | Section headers |
| `h3` | `1.125rem` | 1.35 | 600 | Card titles, subsection |
| `body` | `1rem` | 1.65 | 400 | Body copy |
| `body-sm` | `0.875rem` | 1.6 | 400 | Secondary copy, meta |
| `mono` | `0.8125rem` | 1.65 | 400 | Code, technical specs |
| `caption` | `0.75rem` | 1.5 | 500 | Labels, tags, timestamps |

**No:** Monospace headings, uppercase tracking, decorative type.

---

## Spacing Scale
**Base: 4px. Intent-named.**

| Token | Value | Intent |
|-------|-------|--------|
| `space-xs` | 4px | Inline gaps (icon+text) |
| `space-sm` | 8px | Tight component padding |
| `space-md` | 16px | Standard card/panel padding |
| `space-lg` | 24px | Component margins, form gaps |
| `space-xl` | 32px | Section inner rhythm |
| `space-2xl` | 48px | Major section separation |
| `space-3xl` | 72px | Page-level breathing (hero, CV header) |

**Rhythm Rule:** Alternate density. Dense sections (lists, tables) use `space-lg`. Breathing sections (hero, featured project) use `space-2xl` to `space-3xl`. **Strict 12-col grid.**

---

## Border Radius
**Three radii. By hierarchy.**

| Token | Value | Use |
|-------|-------|-----|
| `radius-sm` | 4px | Buttons, inputs, badges, tags |
| `radius-md` | 8px | Cards, panels, dropdowns, modals, images |
| `radius-lg` | 16px | **One featured container per page max** |

**No:** `rounded-full` / pill shapes. No uniform radius.

---

## Shadows & Elevation
**One elevation. Most surfaces flat with border.**

| Token | Value | Use |
|-------|-------|-----|
| `shadow-card` | `0 0 0 1px rgb(255 255 255 / 0.03), 0 4px 12px rgb(0 0 0 / 0.4)` | Featured card only (1/page) |
| `shadow-focus` | `0 0 0 2px #fbbf24` | Focus rings |

**Default card:** `bg-elevated` + `border` (1px solid `#262626`). **No shadow.**

---

## Glass / Blur
**None.** No backdrop-blur. No glass.

---

## Motion
**MOTION dial: 1 (Hover/focus only)**

| Transition | Duration | Easing | Use |
|------------|----------|--------|-----|
| `transition-colors` | 150ms | ease | Hover/focus on interactive |
| `transition-transform` | 100ms | ease-out | Pressed (`active:scale-[0.98]`) |

**No:** Opacity transitions, fade in/out, loops, float, bounce, scroll-triggered.

---

## Icons
**Inline SVG only. Heroicons outline (24×24).**
- Only for meaning: external link, download, email, GitHub, LinkedIn, chevron.
- **Never** decorative on headings, lists, labels.
- Sizes: `16px` inline, `20px` standalone, `24px` feature.

---

## Components

### Button
```css
/* Primary — ONE per page max */
.btn-primary {
  @apply bg-accent text-bg px-5 py-2.5 rounded-sm font-medium
         transition-colors duration-150 hover:bg-accent-hover
         active:scale-[0.98] focus:outline-none focus-visible:ring-2 focus-visible:ring-accent focus-visible:ring-offset-2 focus-visible:ring-offset-bg;
}

/* Secondary — supporting actions */
.btn-secondary {
  @apply border border-border-hover text-fg px-5 py-2.5 rounded-sm font-medium
         transition-colors duration-150 hover:bg-bg-elevated hover:border-accent
         active:scale-[0.98] focus:outline-none focus-visible:ring-2 focus-visible:ring-accent focus-visible:ring-offset-2 focus-visible:ring-offset-bg;
}

/* Ghost — tertiary */
.btn-ghost {
  @apply text-fg-muted px-3 py-2 font-medium
         transition-colors duration-150 hover:text-accent
         focus:outline-none focus-visible:ring-2 focus-visible:ring-accent focus-visible:ring-offset-2 focus-visible:ring-offset-bg;
}
```

**No:** Arrows on every button. No glow. No pill radius.

### Card (Default — 95% of cards)
```css
.card {
  @apply bg-bg-elevated border border-border rounded-md p-4 md:p-5;
}
```
**No hover effects. No shadow. Border only.**

### Card (Featured — ONE per page max)
```css
.card-featured {
  @apply bg-bg-elevated border border-border rounded-lg shadow-card p-6 md:p-8;
}
```

### Nav Link
```css
.nav-link {
  @apply text-fg-muted font-medium transition-colors duration-150
         hover:text-fg focus:outline-none focus-visible:ring-2 focus-visible:ring-accent focus-visible:ring-offset-2 focus-visible:ring-offset-bg rounded-sm px-2 py-1 -mx-1;
}
.nav-link-active {
  @apply text-accent font-semibold;
}
```

### Section Header
- H2 (`section-title`) + optional 1-line description (`section-desc`, max 60 chars)
- **No** eyebrow badge, no line, no emoji, no icon.

### Tag / Badge
```css
.tag {
  @apply px-2 py-0.5 text-xs font-medium rounded-sm bg-accent-dim text-accent border border-accent/30;
}
```
**No:** Glow, pulse, colored dots without real state.

### Divider
```css
.divider { @apply h-px bg-border w-full; }
```

---

## Layout: Strict 12-Column Grid

### Container
- Max-width: `72rem` (1152px) content pages, `80rem` (1280px) homepage.
- Padding: `1.5rem` (24px) mobile, `2.5rem` (40px) desktop.

### Grid System
```css
.grid-12 { @apply grid grid-cols-12 gap-6; } /* 24px gap = space-lg */
```
- All macro layout uses `.grid-12` with explicit `col-span-*`.
- No flexbox for page layout. Flexbox only inside components.

### Breakpoints
- `sm`: 640px, `md`: 768px, `lg`: 1024px, `xl`: 1280px
- Mobile-first. Enhance at `md`/`lg`.

---

## Page Templates

### Homepage (index.html)
**Structure:** Hero (full-width) → Featured Project (8+4 col) → 2 Cards (4+4+4) → Skills (4+4+4) → CV CTA (centered) → Footer
**Rhythm:** `space-3xl` → `space-2xl` → `space-xl` → `space-2xl`

### Portfolio Index (portfolio.html)
**Structure:** Header → Project Grid (3-col: `col-span-4` each) → Footer
**Rhythm:** Dense. `space-xl` between rows.

### Project Detail (preview-*.html)
**Structure:** Header → Overview (full) → Features (6) / Tech (6) → Gallery (3+3+3+3 or 6+6) → CTA
**Rhythm:** `space-xl` → `space-2xl` → `space-xl`

### CV (cv.html)
**Structure:** Header → Education → Experience → Projects (grouped) → Skills (4-col) → Certs → Languages → Download
**Rhythm:** Dense typographic. `space-xl` between sections. **No cards.**

---

## Antislop Compliance (Non-Negotiable)

| Rule | Enforcement |
|------|-------------|
| R-01 | No gradients. Solid dark palette. |
| R-04 | No emoji. Icons only for external/download/contact. |
| R-05 | Section order = content priority. Strict grid rhythm. |
| R-06 | System fonts. No decorative type. |
| R-07 | No background grids/texture. |
| R-09 | No eyebrow badges, no AI capsules. |
| R-10 | No glass. |
| R-11 | 3 radii by hierarchy. |
| R-12 | Border-only cards. One shadow max/page. |
| R-13 | No glow. Accent 2×/page max. |
| R-14 | Featured project = 8+4 asymmetric. Others = 4-col. |
| R-17/18/38 | All content real. No filler. |
| R-19 | Motion: hover/focus only. No loops. |
| R-21 | Dark default. No toggle. |
| R-23/27 | Honest empty states. |
| R-24/26 | All links functional. |
| R-29 | 2 core + 1 accent. Restraint. |
| R-31 | Accent at key moments only. |
| R-34/36/C-4/C-5 | Keyboard accessible, real content, honest states. |

---

## Implementation
- All pages: same Tailwind config (embedded).
- CSS custom properties for color tokens.
- No external deps except Tailwind CDN.
- Images from `assets/image/` — real screenshots only.
- PDF at `assets/document/CV Raafi Syarahil Azhar.pdf`.