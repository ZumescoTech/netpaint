# 🧱 CLAUDE.md — NetPaint Website
## AI Agent Development Instructions

> **Read this file fully and completely before touching any code. Every decision — layout, copy, markup, component structure — must be evaluated against the conversion objective stated in Section 1. This is not a styleguide to reference loosely; it is the single source of truth for every pixel on every page.**

---

## 📌 Project Identity

| Field | Value |
|---|---|
| **Project** | NetPaint Website |
| **Type** | Conversion-first local business website |
| **Stack** | Pure HTML5 + CSS3 (no frameworks, no JS libraries unless vanilla) |
| **Stylesheet** | `css/styles.css` — already exists, do not recreate or override |
| **Primary Goal** | Generate phone calls, WhatsApp leads, and quote requests |
| **Location** | Cape Town, South Africa |
| **Business Phone** | +27 83 456 1909 |
| **WhatsApp** | https://wa.me/27834561909 |
| **Email** | info@netpaint.co.za |

---

## 🎯 1. The One Rule That Overrides All Others

> **Every element on every page must increase the probability that a visitor contacts NetPaint.**

This is not a portfolio. Not a brochure. Not a showcase of HTML skill.

Before writing any section, ask: *"Does this make it more likely someone picks up the phone or sends a WhatsApp?"*

If the answer is no — cut it, rewrite it, or replace it with a CTA.

---

## 📁 2. File Structure

```
/
├── index.html          # Home — hero, value prop, service previews, trust bar
├── services.html       # Services — primary SEO page, all service categories
├── gallery.html        # Gallery — visual proof, before/after, location tags
├── about.html          # About — credibility, story, team trust signals
├── faq.html            # FAQ — SEO + AEO structured Q&A with schema
├── contact.html        # Contact — lead capture, click-to-call, WhatsApp, form
├── css/
│   └── styles.css      # ✅ ALREADY EXISTS — master stylesheet, do not duplicate
├── images/
│   └── [project images — .webp preferred, .jpg fallback]
└── CLAUDE.md           # This file
```

**Critical file rules:**
- `styles.css` already exists with all tokens, components, and responsive rules. Read it before adding any CSS.
- Never create page-specific `.css` files.
- Never add `<style>` blocks in `<head>` of any HTML page.
- No inline styles except dynamically required values (e.g., JS-driven transforms).
- No CSS frameworks — Bootstrap, Tailwind, etc. are banned.
- All new CSS rules go into `css/styles.css` only.

---

## 🎨 3. Design System — Complete Source of Truth

The design system is **fully defined in `css/styles.css`**. All values below are extracted directly from that file. Use these tokens by name everywhere — **never hardcode a hex value, pixel value, or raw number that maps to a token**.

### 3.1 — Color Tokens (CSS Custom Properties defined in `:root`)

These are the exact variable names as they appear in `styles.css`. Always reference by variable name.

```css
/* ── Brand Greens ── primary palette */
--green:        #3D7A35;   /* Primary brand green. Use for: buttons, links, active states, icons, check marks, borders on focus. */
--green-dark:   #1A5C1A;   /* One shade darker. Use for: button hover states, dark section backgrounds (announcement bar), deep accents. */
--green-deep:   #0F3D0F;   /* Darkest green. Use for: cta-strip background, footer-adjacent dark sections, very deep overlays. */

/* ── Lime ── highlight accent, high-contrast CTA */
--lime:         #C8D480;   /* Warm yellow-green. Use for: accent text on dark backgrounds, .btn-cta background, gallery dots, badges, h1 <em> on dark backgrounds, lime underline. */
--lime-dark:    #A8B460;   /* Lime hover state. Use for: .btn-cta:hover background only. */

/* ── Sage ── softer green tones */
--sage:         #6E9E6E;   /* Muted mid-green. Use for: decorative elements, FAQ open-state border, connector arrows between steps. */
--sage-tint:    #F4F7F0;   /* Very light warm off-white with green tint. Use for: alternate section backgrounds (results section, about page values grid, FAQ accordion item base). */
--sage-light:   #EBF2E8;   /* Hover surfaces, subtle highlights on light backgrounds. */

/* ── Neutrals */
--near-black:   #1A1A1A;   /* Near-black dark. Use for: all h1-h3 headings on light, body text on dark (hero), .btn-cta text color. */
--charcoal:     #4A4A4A;   /* Medium dark gray. Use for: secondary body text, nav links default state, label text. */
--white:        #FFFFFF;   /* Pure white. Use for: page background, card backgrounds, button text on green. */
--off-white:    #F8FAF7;   /* Very slightly warm white. Use for: about section background, alternate section fills. */
--text-muted:   #6B7E6A;   /* Muted warm gray-green. Use for: captions, descriptions, paragraph text in cards, step descriptions. */

/* ── Borders */
--border:       #DDE8D8;   /* Default soft green-tinted border. Use for: card borders, dividers, nav bottom border, input default borders. */
--border-dark:  #C5D8BE;   /* Stronger border. Use for: .btn-nav-outline default border. */
```

**Color usage rules — strictly enforced:**
- Primary CTAs: `background: var(--green)`, hover: `var(--green-dark)`
- WhatsApp buttons: `background: #25D366`, hover: `#1FAD56` — these are the only two hardcoded hex values permitted (WhatsApp brand colors)
- Accent text/elements on dark backgrounds: `var(--lime)`
- `.btn-cta` (on dark green sections): `background: var(--lime)`, `color: var(--near-black)` — high contrast
- Section backgrounds alternate in order: `var(--white)` → `var(--off-white)` → `var(--sage-tint)` → `var(--near-black)` for gallery/dark sections
- `<em>` inside headings on light: `color: var(--green)` | on dark: `color: var(--lime)`
- **Never use a raw hex color in any HTML attribute or new CSS rule unless it is the WhatsApp green.**

### 3.2 — Typography Tokens

```css
--serif:  'Cormorant Garamond', Georgia, serif;   /* ALL headings: h1, h2, h3, .section-title, .about-title, .cta-title, .quality-headline, .svc-title, .logo-wordmark, .stat-n */
--sans:   'DM Sans', system-ui, sans-serif;        /* ALL body: nav, buttons, p, captions, labels, eyebrows, badges, form inputs, footer links */
```

**Font loading — copy this exactly into every page `<head>`:**
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,500;0,600;1,300;1,500&family=DM+Sans:wght@400;500;600;700&display=swap" rel="stylesheet">
```

**Typography rules:**
- All `<h1>`, `<h2>`, `.section-title`, `.about-title`, `.cta-title`, `.quality-headline`, `.logo-wordmark`, `.stat-n` → `font-family: var(--serif)`
- Everything else → `font-family: var(--sans)`
- Section titles and hero h1 use `font-weight: 300` (light — intentional elegance)
- `<em>` inside headings renders as italic serif. Always also apply color: `var(--green)` on light, `var(--lime)` on dark. Never leave `<em>` as default color.
- Use `clamp()` for all fluid font sizes — never use `px` font sizes at breakpoints

**Exact type scale (extracted from styles.css — do not deviate):**

| Element | CSS value |
|---|---|
| Hero `<h1>` | `font-size: clamp(3.36rem, 5.6vw, 5.04rem); font-weight: 300;` |
| Section `.section-title` | `font-size: clamp(2.66rem, 4.2vw, 3.64rem); font-weight: 300;` |
| About/CTA `.about-title`, `.cta-title` | `font-size: clamp(2.8rem, 4.2vw, 3.85rem); font-weight: 300;` |
| Quality `.quality-headline` | `font-size: clamp(3.5rem, 7vw, 6.3rem); font-weight: 600;` |
| Service card `.svc-title` | `font-size: 1.89rem; font-weight: 500;` |
| Step title `.step-title` | `font-size: 1.47rem; font-weight: 600;` |
| Body large `.about-desc`, `.hero-desc` | `font-size: 1.295rem; line-height: 1.75–1.8;` |
| Body default `p`, `.svc-desc`, `.faq-a` | `font-size: 1.225rem; line-height: 1.7;` |
| Body small `.step-desc`, `.section-sub` | `font-size: 1.19–1.26rem; line-height: 1.65–1.7;` |
| Captions, badges, `.faq-chevron` | `font-size: 1.008–1.092rem;` |
| Eyebrows `.section-eyebrow` | `font-size: 0.7rem; font-weight: 700; letter-spacing: .18em; text-transform: uppercase;` |
| Eyebrows `.about-eyebrow` | `font-size: 0.98rem; font-weight: 700; letter-spacing: .18em; text-transform: uppercase;` |
| Logo `.logo-wordmark` | `font-size: 2.1rem; font-weight: 600; letter-spacing: -.01em;` |
| Stat number `.stat-n` | `font-size: 3.92rem; font-weight: 300;` |
| Nav links | `font-size: 1.225rem; font-weight: 500;` |
| Nav buttons | `font-size: 1.12rem; font-weight: 600–700;` |

### 3.3 — Structural Tokens

```css
--max:    1200px;    /* Container max-width. Pattern: max-width: var(--max); margin: auto; */
--r:      6px;       /* Default border-radius for buttons, inputs */
--r-lg:   14px;      /* Larger radius for image containers, FAQ items, feature cards, contact items */

/* Shadows — always green-tinted (never grey) */
--shadow-sm: 0 2px 8px rgba(26,92,26,.08);     /* Subtle lift: floating tabs, small cards */
--shadow-md: 0 8px 32px rgba(26,92,26,.12);    /* Medium lift: image containers, about visual */
--shadow-lg: 0 24px 64px rgba(26,92,26,.16);   /* Strong lift: results image, about main image */
```

**Shadow rule:** Never use `rgba(0,0,0,...)` or grey shadows. Always use the green-tinted shadow tokens above.

### 3.4 — Spacing Rhythm

Sections use consistent internal padding. Do not deviate from these values:

| Context | Padding |
|---|---|
| Full page sections (`.about-section`, `.results-section`, `.faq-section`, `.cta-full`) | `padding: 5rem 2rem` |
| Tighter sections (`.hiw-section`) | `padding: 4.5rem 2rem` |
| Gallery header | `padding: 4rem 2rem 2.5rem` |
| CTA strip | `padding: 2.25rem 2rem` |
| Footer main | `padding: 4rem 2rem 3rem` |
| Announcement bar | `padding: .45rem 1rem` |

### 3.5 — Breakpoints (Established in `styles.css` — Do Not Add New Ones)

```css
@media (max-width: 1024px) { /* Tablet: footer 2-col, minor adjustments */ }
@media (max-width: 900px)  { /* Collapse: grids → single col, hide about-visual, adjust gallery */ }
@media (max-width: 600px)  { /* Mobile: hide nav links + outline button, single col everything, sticky-cta shows */ }
```

**Breakpoint rules:**
- Mobile-first base styles — scale up for larger screens
- `.sticky-cta` is `display: none` by default, becomes `display: flex` at `max-width: 600px`
- Never add new breakpoints — use only these three established widths

---

## 🧩 4. Component Library — Every Styled Class in `styles.css`

These components are **already fully styled**. Use the exact class names shown. Do not reinvent, rename, or override any of these. Read each component description carefully — it explains the visual behavior, not just the markup.

---

### 4.1 — Announcement Bar

**Visual:** Full-width top banner in `var(--green-dark)`. White text, lime-colored link on the right. Small, compact — designed for visibility above the fold.

```html
<div class="announcement-bar">
  Free quotes across Cape Town &amp; surrounds.
  <a href="tel:+27834561909">Call +27 83 456 1909</a>
</div>
```

**Rules:** Place above `<nav>` on every page. Do not modify or skip this element.

---

### 4.2 — Navigation

**Visual:** Sticky white nav with frosted glass blur effect. Logo on left, links in center, action buttons on right. Green underline animation on link hover. Primary "Get a Quote" button in green.

```html
<nav class="nav">
  <div class="nav-inner">
    <a href="index.html" class="logo">
      <div class="logo-icon">
        <!-- Paint brush SVG icon, 22×22px. Color: var(--green) -->
        <svg width="22" height="22" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M7 14c0 1.1-.9 2-2 2s-2 .9-2 2 .9 2 2 2c2.21 0 4-1.79 4-4v-2H7v2zm13-9c0-.55-.45-1-1-1h-2.59l-8.5 8.5-1.5-1.5L5 12.91V15h2.09l8.5-8.5H18c.55 0 1-.45 1-1V5z" fill="currentColor"/>
        </svg>
      </div>
      <span class="logo-wordmark">Net<span>Paint</span></span>
    </a>
    <ul class="nav-links">
      <li><a href="index.html">Home</a></li>
      <li><a href="services.html">Services</a></li>
      <li><a href="gallery.html">Gallery</a></li>
      <li><a href="about.html">About</a></li>
      <li><a href="faq.html">FAQ</a></li>
    </ul>
    <div class="nav-actions">
      <a href="tel:+27834561909" class="btn-nav-outline">+27 83 456 1909</a>
      <a href="contact.html" class="btn-nav-primary">Get a Quote →</a>
    </div>
  </div>
</nav>
```

**Rules:**
- `position: sticky; top: 0; z-index: 100` — already in stylesheet
- Logo: `Net` in `var(--near-black)`, inner `<span>Paint</span>` in `var(--green)`
- Mark the active page with `class="active"` on the correct `<a>` in `.nav-links`
- `.nav-links a.active { color: var(--green); }` is defined in stylesheet — just add the class
- On mobile (`max-width: 600px`): `.nav-links` and `.btn-nav-outline` are hidden via stylesheet

---

### 4.3 — Hero Section

**Visual:** Full-bleed dark section over `hero-bg.webp` with a 70% black overlay. Centered content layout. Stars badge in glassmorphism pill. Large serif H1 with italic lime `<em>`. Two CTA buttons side-by-side (green + WhatsApp green). Three badge items with lime checkmark SVGs below CTAs.

```html
<section class="hero">
  <div class="hero-content">
    <div class="hero-stars">
      <span class="stars-row">★★★★★</span>
      <span>Rated 5-stars across Cape Town</span>
    </div>
    <h1>Cape Town's <em>Trusted</em><br>Painting Specialists</h1>
    <p class="hero-desc">Professional interior and exterior painting for homeowners, property managers, and commercial clients across Cape Town and surrounds.</p>
    <div class="hero-cta">
      <a href="contact.html" class="btn-hero-primary">Get a Free Quote →</a>
      <a href="https://wa.me/27834561909?text=Hi%20NetPaint%2C%20I%27d%20like%20a%20quote"
         class="btn-hero-whatsapp" target="_blank" rel="noopener">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347z"/><path d="M12 0C5.373 0 0 5.373 0 12c0 2.126.555 4.124 1.526 5.864L0 24l6.293-1.505A11.947 11.947 0 0012 24c6.627 0 12-5.373 12-12S18.627 0 12 0zm0 21.818a9.818 9.818 0 01-5.01-1.373l-.36-.214-3.733.893.935-3.618-.235-.373A9.787 9.787 0 012.182 12C2.182 6.57 6.57 2.182 12 2.182c5.43 0 9.818 4.388 9.818 9.818 0 5.43-4.388 9.818-9.818 9.818z"/></svg>
        WhatsApp Us
      </a>
    </div>
    <div class="hero-badges">
      <span class="hero-badge-item">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M9 16.17L4.83 12l-1.42 1.41L9 19 21 7l-1.41-1.41L9 16.17z"/></svg>
        10+ Years Experience
      </span>
      <span class="hero-badge-item">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M9 16.17L4.83 12l-1.42 1.41L9 19 21 7l-1.41-1.41L9 16.17z"/></svg>
        850+ Projects
      </span>
      <span class="hero-badge-item">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M9 16.17L4.83 12l-1.42 1.41L9 19 21 7l-1.41-1.41L9 16.17z"/></svg>
        Fully Insured
      </span>
    </div>
  </div>
</section>
```

**Visual details:**
- Background: `var(--near-black) url('/images/hero-bg.webp') center/cover`
- `::before` overlay: `rgba(0,0,15,0.7)` full inset, z-index 1
- `.hero-content` is z-index 2, centered, max-width 600px
- `.hero-stars`: glassmorphism pill — `background: rgba(255,255,255,.12); backdrop-filter: blur(8px)`
- `.stars-row`: color `#F5C842` (gold), letter-spacing 2px
- `<h1>`: white, font-weight 300, `<em>` is lime + italic
- `.hero-desc`: `rgba(255,255,255,.6)` — intentionally muted
- `.btn-hero-primary`: green background, box-shadow `0 4px 20px rgba(61,122,53,.4)`, lifts on hover
- `.btn-hero-whatsapp`: `#25D366`, box-shadow `0 4px 20px rgba(37,211,102,.4)`
- `.hero-badge-item` SVG icons: `color: var(--lime)`

---

### 4.4 — Service Cards Strip

**Visual:** Full-width white section, 3-column grid (no gaps). Each card has a placeholder gradient image, green underline animation that sweeps left-to-right on hover, and a green CTA button. Three color variants for the placeholder images.

```html
<section class="services-strip">
  <div class="services-strip-inner">

    <div class="svc-card">
      <div class="svc-img-placeholder green" data-emoji="🖌️"></div>
      <h3 class="svc-title">Interior Painting</h3>
      <p class="svc-desc">Transform your interiors with premium finishes. We handle prep, priming, and application across all room types.</p>
      <a href="services.html#interior-painting" class="btn-svc">
        Learn More
        <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M8.59 16.58L13.17 12 8.59 7.41 10 6l6 6-6 6-1.41-1.42z"/></svg>
      </a>
    </div>

    <div class="svc-card">
      <div class="svc-img-placeholder dark" data-emoji="🏗️"></div>
      <h3 class="svc-title">Exterior Painting</h3>
      <p class="svc-desc">Weather-resistant coatings and flawless finishes for Cape Town's climate. Walls, fascias, and more.</p>
      <a href="services.html#exterior-painting" class="btn-svc">
        Learn More
        <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M8.59 16.58L13.17 12 8.59 7.41 10 6l6 6-6 6-1.41-1.42z"/></svg>
      </a>
    </div>

    <div class="svc-card">
      <div class="svc-img-placeholder lime" data-emoji="🔨"></div>
      <h3 class="svc-title">Surface Repairs</h3>
      <p class="svc-desc">Crack filling, plaster repairs, and waterproofing before every paint job. We fix it before we finish it.</p>
      <a href="services.html#surface-repairs" class="btn-svc">
        Learn More
        <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M8.59 16.58L13.17 12 8.59 7.41 10 6l6 6-6 6-1.41-1.42z"/></svg>
      </a>
    </div>

  </div>
</section>
```

**Visual details:**
- `.services-strip-inner`: `display: grid; grid-template-columns: repeat(3, 1fr)` — no border-radius, no padding between columns
- `.svc-card`: `padding: 2.5rem 2rem; border-right: 1px solid var(--border)` — last child has no right border
- Hover: `background` transitions to `var(--sage-tint)`
- `::after` pseudoelement: 3px green bar sweeps in from left on hover (transform-origin: left)
- `.svc-img-placeholder`: 160px height, `border-radius: var(--r-lg)`, emoji via `content: attr(data-emoji)` CSS pseudo, opacity 0.35
  - `.green`: `linear-gradient(135deg, #1A5C1A, #3D7A35, #6E9E6E)`
  - `.dark`: `linear-gradient(135deg, #2A2A2A, #4A4A4A, #3D7A35)`
  - `.lime`: `linear-gradient(135deg, #8BAA3A, #C8D480, #6E9E6E)`
- On `max-width: 900px`: collapses to 1 column, `border-right: none`, `border-bottom: 1px solid var(--border)`

---

### 4.5 — CTA Strip (Horizontal Dark Banner)

**Visual:** Full-width dark green section (`var(--green-deep)`) with a subtle diagonal lime stripe texture via `::before`. Left side has eyebrow + title, right side has two action buttons. Compact — intended for use between content sections.

```html
<section class="cta-strip">
  <div class="cta-strip-inner">
    <div>
      <p class="cta-strip-eyebrow">Free Quote — No Obligation</p>
      <h2 class="cta-strip-title">Ready to Transform Your Property?</h2>
    </div>
    <div class="cta-strip-actions">
      <a href="tel:+27834561909" class="btn-hero-primary">📞 Call Now</a>
      <a href="https://wa.me/27834561909?text=Hi%20NetPaint%2C%20I%27d%20like%20a%20quote"
         class="btn-hero-whatsapp" target="_blank" rel="noopener">💬 WhatsApp Us</a>
    </div>
  </div>
</section>
```

**Visual details:**
- `.cta-strip`: `background: var(--green-deep)`, `padding: 2.25rem 2rem`, `overflow: hidden`
- `::before`: `repeating-linear-gradient(45deg, transparent 0, transparent 30px, rgba(200,212,128,.04) 30px, rgba(200,212,128,.04) 31px)` — subtle diagonal texture
- `.cta-strip-inner`: `display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 2rem; max-width: var(--max); margin: auto`
- `.cta-strip-eyebrow`: `color: var(--lime)`, uppercase, letter-spaced — not a heading tag
- `.cta-strip-title`: `font-family: var(--serif); font-size: clamp(1.5rem, 2.4vw, 2rem); font-weight: 500; color: #fff`
- **Placement rule:** Insert `.cta-strip` between every 2 content sections. Never have 3+ sections in a row without a CTA.

---

### 4.6 — About / Stats Section

**Visual:** Two-column grid on `var(--off-white)`. Left column: eyebrow (with green line `::before`), large light serif title, description paragraph, three stat numbers in large green serif, and a "Meet the Team" text link. Right column: tall image container with a floating green "Fully Licensed & Insured" badge.

```html
<section class="about-section">
  <div class="about-inner">
    <div class="about-text">
      <p class="about-eyebrow">About NetPaint</p>
      <h2 class="about-title">Built on <em>craft</em>,<br>delivered with care</h2>
      <p class="about-desc">NetPaint is a professional painting company serving Cape Town and surrounding areas. With over 10 years of experience and 850+ completed projects, we bring consistent quality to every home and commercial property we work on.</p>
      <div class="stats-row">
        <div class="stat-item">
          <div class="stat-n">10<sup>+</sup></div>
          <div class="stat-l">Years Experience</div>
        </div>
        <div class="stat-item">
          <div class="stat-n">850<sup>+</sup></div>
          <div class="stat-l">Projects Completed</div>
        </div>
        <div class="stat-item">
          <div class="stat-n">100<sup>%</sup></div>
          <div class="stat-l">Insured & Licensed</div>
        </div>
      </div>
      <a href="about.html" class="meet-link">Meet the Team</a>
    </div>
    <div class="about-visual">
      <div class="about-main-img">
        <div class="about-img-placeholder"></div>
        <!-- Or: <img src="images/team.webp" alt="NetPaint team on a painting project in Cape Town" loading="lazy"> -->
      </div>
      <div class="licensed-float">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M12 1L3 5v6c0 5.55 3.84 10.74 9 12 5.16-1.26 9-6.45 9-12V5l-9-4z"/></svg>
        Fully Licensed & Insured
      </div>
    </div>
  </div>
</section>
```

**Visual details:**
- `.about-section`: `padding: 5rem 2rem; background: var(--off-white)`
- `.about-inner`: `display: grid; grid-template-columns: 1fr 1fr; gap: 5rem; align-items: center; max-width: var(--max); margin: auto`
- `.about-eyebrow`: green uppercase text with `::before` 28×2px green horizontal line pseudo
- `.about-title`: Cormorant Garamond 300, `<em>` in `var(--green)` italic
- `.stat-n`: Cormorant Garamond, `color: var(--green)`, 3.92rem, `<sup>` is 1.54rem bold
- `.stat-l`: uppercase, letter-spaced, `var(--text-muted)`
- `.meet-link`: uppercase sans, green, has `::after` arrow that shifts right on hover
- `.about-main-img`: `aspect-ratio: 4/3`, `border-radius: var(--r-lg)`, `box-shadow: var(--shadow-lg)`
- `.licensed-float`: `position: absolute; right: -1.5rem; bottom: 2rem; background: var(--green); color: #fff; border-radius: var(--r-lg); box-shadow: 0 8px 24px rgba(26,92,26,.4)`
- `.about-visual`: must have `position: relative` for `.licensed-float` to position correctly
- On `max-width: 900px`: `about-inner` becomes 1 column, `.about-visual` is `display: none`

---

### 4.7 — How It Works Steps

**Visual:** Centered section on white. 3-column step grid on `var(--sage-tint)` background with green bordered cards. Each step has a circular green numbered badge, emoji icon, bold title, and description. Connector `›` arrows between steps via CSS `::after`.

```html
<section class="hiw-section">
  <div class="hiw-inner">
    <p class="section-eyebrow">Our Process</p>
    <h2 class="section-title">How It <em>Works</em></h2>
    <p class="section-sub">Simple, professional, zero stress.</p>
    <div class="hiw-steps">

      <div class="hiw-step">
        <div class="step-circle">01<span>Step</span></div>
        <div class="hiw-icon">📋</div>
        <h3 class="step-title">Free Quote</h3>
        <p class="step-desc">We visit your property, assess the scope, and provide a detailed written quote — no obligation, no pressure.</p>
      </div>

      <div class="hiw-step">
        <div class="step-circle">02<span>Step</span></div>
        <div class="hiw-icon">🧹</div>
        <h3 class="step-title">Preparation</h3>
        <p class="step-desc">We protect your surfaces, repair defects, and prepare every area before a single drop of paint is applied.</p>
      </div>

      <div class="hiw-step">
        <div class="step-circle">03<span>Step</span></div>
        <div class="hiw-icon">🖌️</div>
        <h3 class="step-title">Paint & Finish</h3>
        <p class="step-desc">Premium paints, expert application, and a final quality walkthrough. We leave your space spotless.</p>
      </div>

    </div>
  </div>
</section>
```

**Visual details:**
- `.hiw-section`: `padding: 4.5rem 2rem; background: var(--white)`
- `.hiw-inner`: `max-width: 900px; margin: auto; text-align: center`
- `.hiw-steps`: `display: grid; grid-template-columns: repeat(3, 1fr); background: var(--sage-tint); border: 1px solid var(--border); border-radius: var(--r-lg); overflow: hidden`
- `.hiw-step`: `padding: 2.5rem 2rem; border-right: 1px solid var(--border); text-align: center` — last child no right border
- `::after` on each non-last step: `content: '›'`, positioned absolutely, `color: var(--sage)`, `top: 50%`, `right: -8px`
- `.step-circle`: 60×60px circle, `background: var(--green); color: #fff; box-shadow: 0 4px 16px rgba(61,122,53,.35); margin: 0 auto 1.25rem`
- On `max-width: 900px`: collapses to 1 column, border-right → border-bottom, `::after` arrows hidden

---

### 4.8 — Quality Banner (Full-Bleed Image)

**Visual:** Dramatic full-bleed section over `Modern-Living-Room-Fireplace-CAPE-TOWN.webp`. Dark gradient overlay with a subtle green tint on the right. Large display heading with lime italic. CTA button on right using lime style.

```html
<section class="quality-banner">
  <div class="quality-inner">
    <div class="quality-text">
      <p class="quality-label">Our standard</p>
      <h2 class="quality-headline">Premium<br><em>finishes</em></h2>
      <p class="quality-sub">Every time. Every project.</p>
    </div>
    <div class="cta-actions">
      <a href="contact.html" class="btn-cta">Get a Free Quote →</a>
    </div>
  </div>
</section>
```

**Visual details:**
- `background-image: url('/images/Modern-Living-Room-Fireplace-CAPE-TOWN.webp')`, `background-size: cover`, `background-position: center`
- `::before` overlay: `linear-gradient(135deg, rgba(26,26,26,.85) 0%, rgba(26,26,26,.6) 50%, rgba(61,122,53,.3) 100%)`
- `.quality-inner`: `display: flex; align-items: center; gap: 4rem; max-width: var(--max); margin: auto; position: relative; z-index: 1`
- `.quality-headline em`: `color: var(--lime); font-style: italic`
- `.quality-label`: Cormorant italic, `rgba(255,255,255,.5)`
- `.quality-sub`: uppercase, letter-spaced, `rgba(255,255,255,.5)`
- `.btn-cta`: `background: var(--lime); color: var(--near-black)` — high contrast on dark background
- On `max-width: 900px`: flex → column, text-align center

---

### 4.9 — Gallery Grid

**Visual:** Dark section (`var(--near-black)`). Header with lime eyebrow, white title. Below: tight 3×2 grid with color-gradient placeholder cells. Cells use `.wide` (2-col span) and `.tall` (2-row span). On hover: cell scales up + brightens + overlay label fades in showing project type and location.

```html
<section class="gallery-section">
  <div class="gallery-header">
    <p class="section-eyebrow">Our Work</p>
    <h2 class="section-title">Projects <em>Across Cape Town</em></h2>
    <p>Premium results delivered across Cape Town and the Western Cape.</p>
  </div>
  <div class="gallery-grid">

    <div class="g-cell wide">
      <div class="g-fill g-c1"><div class="g-scene">🏠</div></div>
      <div class="g-overlay">
        <div class="g-label"><span class="g-dot"></span>Interior Repaint</div>
        <div class="g-sub">Claremont, Cape Town</div>
      </div>
    </div>

    <div class="g-cell">
      <div class="g-fill g-c2"><div class="g-scene">🏗️</div></div>
      <div class="g-overlay">
        <div class="g-label"><span class="g-dot"></span>Exterior Repaint</div>
        <div class="g-sub">Stellenbosch</div>
      </div>
    </div>

    <div class="g-cell tall">
      <div class="g-fill g-c3"><div class="g-scene">🏡</div></div>
      <div class="g-overlay">
        <div class="g-label"><span class="g-dot"></span>Full Repaint</div>
        <div class="g-sub">Somerset West</div>
      </div>
    </div>

    <div class="g-cell">
      <div class="g-fill g-c4"><div class="g-scene">🖌️</div></div>
      <div class="g-overlay">
        <div class="g-label"><span class="g-dot"></span>Interior Painting</div>
        <div class="g-sub">Sea Point</div>
      </div>
    </div>

    <div class="g-cell">
      <div class="g-fill g-c5"><div class="g-scene">🏢</div></div>
      <div class="g-overlay">
        <div class="g-label"><span class="g-dot"></span>Commercial Paint</div>
        <div class="g-sub">Bellville</div>
      </div>
    </div>

    <div class="g-cell">
      <div class="g-fill g-c1"><div class="g-scene">🛠️</div></div>
      <div class="g-overlay">
        <div class="g-label"><span class="g-dot"></span>Surface Repairs</div>
        <div class="g-sub">Constantia</div>
      </div>
    </div>

  </div>
</section>
```

**Visual details:**
- `.gallery-section`: `padding: 0; background: var(--near-black)`
- `.gallery-header`: `padding: 4rem 2rem 2.5rem; text-align: center`
- `.gallery-grid`: `display: grid; grid-template-columns: repeat(3, 1fr); grid-template-rows: 240px 240px; gap: 3px`
- `.g-cell.wide`: `grid-column: span 2`, `.g-cell.tall`: `grid-row: span 2`
- Color variants `g-c1`–`g-c5`: each is a distinct green-toned gradient (see stylesheet for exact values)
- `.g-fill`: `filter: brightness(.8) saturate(.85)` default → hover brightens and scales 1.06
- `.g-overlay`: `opacity: 0` → `1` on cell hover. Gradient from black bottom.
- `.g-dot`: 6×6px lime circle bullet
- `.g-label`: uppercase, letter-spaced, white
- Location names for `.g-sub`: Claremont, Stellenbosch, Somerset West, Durbanville, Paarl, Sea Point, Constantia, Bellville
- On `max-width: 900px`: 2-col, `.wide`/`.tall` classes both become span 1, each cell 200px height
- On `max-width: 600px`: single column

---

### 4.10 — Full CTA Banner

**Visual:** Centered dark green section with radial glow behind content. Lime accent line at the very top. Pill badge, large light serif heading, muted subtext, two action buttons (lime CTA + green phone button).

```html
<section class="cta-full">
  <div class="cta-inner">
    <div class="cta-badge">✦ Cape Town's Trusted Painters</div>
    <h2 class="cta-title">Ready for a <em>fresh start?</em></h2>
    <p class="cta-sub">Get a free, no-obligation quote. We respond within 24 hours.</p>
    <div class="cta-actions">
      <a href="contact.html" class="btn-cta">Request a Free Quote →</a>
      <a href="tel:+27834561909" class="btn-hero-primary">📞 +27 83 456 1909</a>
    </div>
  </div>
</section>
```

**Visual details:**
- `background: linear-gradient(135deg, var(--green-dark) 0%, var(--green-deep) 100%)`
- `::after`: 4px lime gradient line at very top — `linear-gradient(90deg, transparent, var(--lime), transparent)`
- `::before`: radial glow — `radial-gradient(ellipse, rgba(200,212,128,.12), transparent)`
- `.cta-badge`: pill shape, `background: rgba(200,212,128,.2); color: var(--lime); border: 1px solid rgba(200,212,128,.3); border-radius: 999px`
- `.cta-title em`: `color: var(--lime); font-style: italic`
- `.cta-inner`: `max-width: 640px; margin: auto; text-align: center`
- `.btn-cta`: `background: var(--lime); color: var(--near-black)` — never use green text on lime
- **Placement rule:** Always the last section before `<footer>` on every page.

---

### 4.11 — Results / Why Us Section

**Visual:** Two-column grid on `var(--sage-tint)`. Left: tall portrait image container with lime border, three floating animated tab pills (slide in from right with staggered delay). Right: tag row, eyebrow, title, checklist with green circle checkmarks, green CTA button.

```html
<section class="results-section">
  <div class="results-inner">
    <div class="results-visual">
      <div class="results-img">
        <div class="results-img-fill">
          <span class="results-img-emoji">🏡</span>
        </div>
        <!-- Or: <img src="images/project.webp" alt="finished exterior painting project Stellenbosch NetPaint" loading="lazy"> -->
      </div>
      <div class="results-tabs-float">
        <span class="r-tab active">Interior</span>
        <span class="r-tab">Exterior</span>
        <span class="r-tab">Commercial</span>
      </div>
    </div>
    <div class="results-content">
      <div class="results-tag-row">
        <span class="r-tag">Fully Insured</span>
        <span class="r-tag">Cape Town Based</span>
        <span class="r-tag">Free Quotes</span>
      </div>
      <p class="about-eyebrow">Why Choose NetPaint</p>
      <h2 class="about-title">Results that <em>speak</em><br>for themselves</h2>
      <ul class="results-list">
        <li><span class="check-circle">✓</span> Premium paints — Dulux, Plascon, Prominent</li>
        <li><span class="check-circle">✓</span> Thorough surface preparation before every coat</li>
        <li><span class="check-circle">✓</span> Clean, punctual crew — we respect your home</li>
        <li><span class="check-circle">✓</span> Written workmanship warranty on all projects</li>
        <li><span class="check-circle">✓</span> Fully insured — residential and commercial</li>
      </ul>
      <a href="contact.html" class="btn-results">Get a Free Quote →</a>
    </div>
  </div>
</section>
```

**Visual details:**
- `.results-img`: `aspect-ratio: 3/4; border: 2px solid var(--lime); border-radius: var(--r-lg); box-shadow: var(--shadow-lg)`
- `.results-tabs-float`: `position: absolute; top: -1rem; right: -1rem; flex-direction: column; gap: .4rem`
- `.results-visual`: must have `position: relative` for floating tabs
- `.r-tab` animation: starts `transform: translateX(100%); opacity: 0`, animates to position via `@keyframes slideInFromRight`. Tab 1 at 0.5s, Tab 2 at 1s, Tab 3 at 1.5s delay
- `.r-tab.active`: `background: var(--green); color: #fff; border-color: var(--green)`
- `.r-tag`: `background: rgba(61,122,53,.1); color: var(--green); border: 1px solid rgba(61,122,53,.2); border-radius: 999px`
- `.check-circle`: 22×22px circle, `background: var(--green); color: #fff`
- On `max-width: 900px`: 1 column, `.results-tag-row { display: none }`, image becomes landscape

---

### 4.12 — FAQ Accordion

**Visual:** White section, narrow centered layout (820px max). Header centered above. Native `<details>/<summary>` accordion — no JS. Off-white cards with green-tinted open state. `+` chevron rotates 45° and turns green when open.

```html
<section class="faq-section">
  <div class="faq-inner">
    <div class="faq-header">
      <p class="section-eyebrow">Common Questions</p>
      <h2 class="section-title">Frequently Asked <em>Questions</em></h2>
    </div>
    <div class="faq-list">

      <details class="faq">
        <summary class="faq-q">
          How much does interior painting cost in Cape Town?
          <span class="faq-chevron">+</span>
        </summary>
        <div class="faq-a">
          Interior painting in Cape Town typically starts from R35 per square metre depending on surface condition, paint quality, and number of coats. NetPaint provides free, no-obligation written quotes. Call +27 83 456 1909 to arrange a site visit.
        </div>
      </details>

      <!-- Repeat pattern for additional FAQ items -->

    </div>
  </div>
</section>
```

**Visual details:**
- `.faq-section`: `padding: 5rem 2rem; background: var(--white)`
- `.faq-inner`: `max-width: 820px; margin: auto`
- `details.faq`: `background: var(--off-white); border: 1px solid var(--border); border-radius: var(--r-lg); overflow: hidden`
- `details.faq[open]`: `border-color: var(--sage); box-shadow: 0 4px 20px rgba(61,122,53,.1)`
- `summary.faq-q`: `padding: 1.1rem 1.5rem; display: flex; justify-content: space-between; gap: 1rem; font-size: 1.295rem; font-weight: 600`
- `::-webkit-details-marker { display: none }` — removes native browser arrow
- `.faq-chevron`: 28×28px circle, `background: rgba(61,122,53,.1); color: var(--green)` default → open state: `background: var(--green); color: #fff; transform: rotate(45deg)`
- `.faq-a`: `padding: 0 1.5rem 1.1rem; padding-top: .875rem; border-top: 1px solid var(--border); font-size: 1.225rem; color: var(--text-muted); line-height: 1.75`

---

### 4.13 — Footer

**Visual:** Dark `var(--near-black)` footer. 4-column grid: brand description, Pages nav, Services nav, Contact info. Bottom bar: copyright left, lime brand tagline right. Logo wordmark with lime "Paint" span.

```html
<footer>
  <div class="footer-main">
    <div class="footer-brand">
      <span class="logo-wordmark">Net<span>Paint</span></span>
      <p>Professional painting &amp; building repairs across Cape Town and surrounding areas. Quality finishes, reliable service.</p>
    </div>
    <div class="footer-col">
      <h4>Pages</h4>
      <ul>
        <li><a href="index.html">Home</a></li>
        <li><a href="services.html">Services</a></li>
        <li><a href="gallery.html">Gallery</a></li>
        <li><a href="about.html">About</a></li>
        <li><a href="faq.html">FAQ</a></li>
        <li><a href="contact.html">Contact</a></li>
      </ul>
    </div>
    <div class="footer-col">
      <h4>Services</h4>
      <ul>
        <li><a href="services.html#interior-painting">Interior Painting</a></li>
        <li><a href="services.html#exterior-painting">Exterior Painting</a></li>
        <li><a href="services.html#surface-repairs">Surface Repairs</a></li>
        <li><a href="services.html#protective-coatings">Protective Coatings</a></li>
        <li><a href="services.html#commercial-painting">Commercial Painting</a></li>
      </ul>
    </div>
    <div class="footer-col">
      <h4>Contact</h4>
      <ul>
        <li><a href="tel:+27834561909">+27 83 456 1909</a></li>
        <li><a href="https://wa.me/27834561909?text=Hi%20NetPaint%2C%20I%27d%20like%20a%20quote">WhatsApp</a></li>
        <li><a href="mailto:info@netpaint.co.za">info@netpaint.co.za</a></li>
        <li>123 Main Street, Cape Town, 8001</li>
      </ul>
    </div>
  </div>
  <div class="footer-bottom">
    <span>© 2025 NetPaint. All rights reserved.</span>
    <span class="footer-green">Cape Town's Trusted Painters</span>
  </div>
</footer>
```

**Visual details:**
- `background: var(--near-black); color: rgba(255,255,255,.65)`
- `.footer-main`: `display: grid; grid-template-columns: 1.6fr 1fr 1fr 1fr; gap: 3rem; padding: 4rem 2rem 3rem; border-bottom: 1px solid rgba(255,255,255,.08); max-width: var(--max); margin: auto`
- `.footer-brand .logo-wordmark span`: `color: var(--lime)` — in footer, logo accent is lime (not green)
- `.footer-col h4`: uppercase, `rgba(255,255,255,.35)` muted label
- `.footer-col a`: `rgba(255,255,255,.5)` → hover `var(--lime)`
- `.footer-green`: `color: var(--lime)`
- `@1024px`: 2 columns | `@600px`: 1 column
- **Footer must be byte-for-byte identical across all pages** — copy-paste, never rewrite

---

### 4.14 — Sticky Mobile CTA Bar

**Visual:** Fixed bar at bottom of screen on mobile only. Three equal buttons: green Call, WhatsApp green, lime Quote. Appears only at `max-width: 600px`.

```html
<div class="sticky-cta" id="stickyCta">
  <a href="tel:+27834561909" class="sticky-cta-btn call">📞 Call</a>
  <a href="https://wa.me/27834561909?text=Hi%20NetPaint%2C%20I%27d%20like%20a%20quote"
     class="sticky-cta-btn whatsapp" target="_blank" rel="noopener">💬 WhatsApp</a>
  <a href="contact.html" class="sticky-cta-btn quote">Get Quote</a>
</div>
```

**Visual details:**
- `position: fixed; bottom: 0; left: 0; right: 0; z-index: 90; display: none` (desktop)
- `@media (max-width: 600px) { .sticky-cta { display: flex; } }` — shows on mobile
- `background: #fff; border-top: 1px solid var(--border); box-shadow: 0 -4px 20px rgba(26,92,26,.12); padding: .6rem; gap: .5rem`
- `.call`: `background: var(--green); color: #fff`
- `.whatsapp`: `background: #25D366; color: #fff`
- `.quote`: `background: var(--lime); color: var(--near-black)`
- **Placement:** Immediately before `</body>` on every page — never inside `<main>` or `<section>`

---

## 📞 5. Conversion Elements — Mandatory on Every Page

### 5.1 — Contact Details (Copy Exactly — No Variations)

| Type | Exact Value |
|---|---|
| Phone display | `+27 83 456 1909` |
| Phone href | `tel:+27834561909` |
| WhatsApp URL | `https://wa.me/27834561909` |
| WhatsApp pre-fill text | `?text=Hi%20NetPaint%2C%20I%27d%20like%20a%20quote` |
| Full WhatsApp link | `https://wa.me/27834561909?text=Hi%20NetPaint%2C%20I%27d%20like%20a%20quote` |
| Email | `info@netpaint.co.za` |
| Email href | `mailto:info@netpaint.co.za` |
| Street address | `123 Main Street, Cape Town, 8001, South Africa` |
| Coordinates | `-33.9249, 18.4241` |

### 5.2 — Button Class Reference (Complete)

| Purpose | Class | Background | Text Color | Hover |
|---|---|---|---|---|
| Hero primary CTA | `btn-hero-primary` | `var(--green)` | `#fff` | `var(--green-dark)` + lift |
| WhatsApp | `btn-hero-whatsapp` | `#25D366` | `#fff` | `#1FAD56` + lift |
| On dark sections | `btn-cta` | `var(--lime)` | `var(--near-black)` | `var(--lime-dark)` + lift |
| Service card | `btn-svc` | `var(--green)` | `#fff` | `var(--green-dark)` + lift |
| Content section | `btn-results` | `var(--green)` | `#fff` | `var(--green-dark)` + lift |
| Nav phone link | `btn-nav-outline` | transparent | `var(--charcoal)` | border + text → `var(--green)` |
| Nav quote link | `btn-nav-primary` | `var(--green)` | `#fff` | `var(--green-dark)` + lift |
| Sticky mobile Call | `sticky-cta-btn call` | `var(--green)` | `#fff` | — |
| Sticky mobile WhatsApp | `sticky-cta-btn whatsapp` | `#25D366` | `#fff` | — |
| Sticky mobile Quote | `sticky-cta-btn quote` | `var(--lime)` | `var(--near-black)` | — |

### 5.3 — CTA Placement Rules (Non-Negotiable)

- **Above the fold:** Always — every page has a visible CTA in the hero
- **Between sections:** After every 1–2 content sections, insert `.cta-strip`
- **Before footer:** Always — `.cta-full` is the last section before `<footer>` on every page
- **Mobile:** `.sticky-cta` bar fixed at bottom on every page
- **Never:** Three or more content sections in a row without a CTA of some kind

### 5.4 — Button Copy Rules

Never use these: "Submit", "Click Here", "Read More", "Learn More" without context.

Always use specific action-oriented copy:

| Context | Required Copy |
|---|---|
| Main quote CTA | "Get a Free Quote →" or "Request My Free Quote →" |
| Phone | "📞 Call Now" or "📞 +27 83 456 1909" |
| WhatsApp | "💬 WhatsApp Us" |
| Service card | "Learn More →" (with service name implied from context) |
| Content section | "Get a Free Quote →" |

---

## 🔍 6. SEO Requirements

### 6.1 — `<head>` Template (Copy for Every Page — Replace PAGE-SPECIFIC Fields)

```html
<!DOCTYPE html>
<html lang="en-ZA">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <!-- PAGE-SPECIFIC: 50–60 characters total, include location keyword -->
  <title>Professional Painters Cape Town | NetPaint</title>

  <!-- PAGE-SPECIFIC: 140–160 characters, service + location + action verb -->
  <meta name="description" content="NetPaint offers professional interior and exterior painting services across Cape Town, Stellenbosch, Somerset West and Durbanville. Get a free quote today.">

  <!-- PAGE-SPECIFIC: full canonical URL -->
  <link rel="canonical" href="https://www.netpaint.co.za/index.html">

  <!-- Open Graph (update title/description/url per page, image stays same) -->
  <meta property="og:title" content="Professional Painters Cape Town | NetPaint">
  <meta property="og:description" content="Professional painting services across Cape Town. 10+ years experience. 850+ projects. Free quotes.">
  <meta property="og:image" content="https://www.netpaint.co.za/images/og-image.jpg">
  <meta property="og:url" content="https://www.netpaint.co.za/">
  <meta property="og:type" content="website">

  <!-- Local business geo signals — identical across all pages -->
  <meta name="geo.region" content="ZA-WC">
  <meta name="geo.placename" content="Cape Town">

  <!-- Fonts — identical across all pages -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,500;0,600;1,300;1,500&family=DM+Sans:wght@400;500;600;700&display=swap" rel="stylesheet">

  <!-- Stylesheet — single shared stylesheet -->
  <link rel="stylesheet" href="css/styles.css">

  <!-- PAGE-SPECIFIC: JSON-LD Schema (see Section 8) -->
  <script type="application/ld+json">
  { ... }
  </script>
</head>
```

### 6.2 — Per-Page SEO Targets

| Page | `<title>` (target) | H1 text | Primary keywords |
|---|---|---|---|
| `index.html` | Professional Painters Cape Town \| NetPaint | Cape Town's Trusted Painting Specialists | house painters Cape Town, painting services Cape Town |
| `services.html` | Painting Services Cape Town — Interior, Exterior & Repairs \| NetPaint | Professional Painting Services in Cape Town | painting contractors Cape Town, exterior painting Cape Town |
| `gallery.html` | Painting Projects Gallery Cape Town — Before & After \| NetPaint | Our Work Across Cape Town | painting gallery Cape Town |
| `about.html` | About NetPaint — Cape Town Painters Since 2014 \| NetPaint | About NetPaint | painting company Cape Town |
| `faq.html` | FAQ — Painting Services Cape Town \| Costs & Timelines \| NetPaint | Frequently Asked Questions About Our Painting Services | how much does painting cost Cape Town |
| `contact.html` | Contact NetPaint — Free Quote Cape Town \| NetPaint | Get Your Free Painting Quote | painting quote Cape Town, contact painters Cape Town |

### 6.3 — Heading Hierarchy Rules

- **One `<h1>` per page only** — must contain the primary keyword, placed in the hero section
- **`<h2>`** — each major section heading, secondary/related keywords
- **`<h3>`** — sub-sections, service names inside service sections, individual FAQ questions
- **Eyebrows** (`.section-eyebrow`, `.about-eyebrow`, `.cta-strip-eyebrow`) are always `<p>` tags — never headings
- **Never use a heading tag purely for visual sizing** — use CSS classes on the semantically correct tag

### 6.4 — Internal Linking (Every Page)

- Link to `services.html` at least once with descriptive anchor text ("interior painting services", "exterior painting")
- Link to `contact.html` at least twice — in CTA buttons, not just navigation
- `services.html` links to each service via `#id` anchors referenced from the homepage service cards
- `faq.html` answers link back to `services.html` and end with a link to `contact.html`
- **Never** use "click here", "read more", or "here" as link anchor text

---

## 🤖 7. AEO Requirements (Answer Engine Optimization)

The site must be accurately indexable and summarizable by AI systems: Google AI Overviews, ChatGPT, Perplexity, and similar.

### 7.1 — Entity Clarity Block (Required on Every Page)

Every page must contain a paragraph that plainly states all four of these facts:

1. What NetPaint is (type of business)
2. Where it operates (specific suburbs)
3. What services it offers
4. How to contact it

**Exact template — adapt slightly per page context:**
> *NetPaint is a professional painting and building repairs company based in Cape Town, South Africa. We serve homeowners, property managers, and commercial clients across Cape Town, Somerset West, Stellenbosch, and Durbanville. Our services include interior painting, exterior painting, surface repairs, and protective coatings. To request a free quote, call +27 83 456 1909 or WhatsApp us at wa.me/27834561909.*

This paragraph can appear in the `.about-section` intro, the hero subtext, or a visible body section. It must be **visible body text** — not hidden, not in meta tags only.

### 7.2 — Plain Language Rules for All Copy

Write facts, not fluff. These rules apply to all body copy:

| ❌ Don't write | ✅ Write instead |
|---|---|
| "We deliver exceptional results" | "NetPaint has completed 850+ projects across Cape Town" |
| "Our team is passionate about quality" | "We use Dulux, Plascon, and Prominent paints on every job" |
| "Transform your space" | "Interior repaints typically take 3–5 working days" |
| "Industry-leading service" | "Free written quotes, no obligation, we reply within 24 hours" |

- Lead with the most important information (inverted pyramid — conclusion first)
- Every service description must answer: What is it? Who is it for? What area? How to contact?
- Use specific numbers wherever available: years, project counts, price ranges, timelines, areas
- No lorem ipsum — ever

### 7.3 — FAQ Page AEO Requirements

- Questions must match exact user search phrasing, e.g.: "How much does exterior painting cost in Cape Town?" not "What are your prices?"
- Answers: 2–4 sentences, complete, self-contained — usable as a standalone featured snippet
- Every pricing or timeline answer ends with: "Call +27 83 456 1909 to arrange a free site visit."
- Minimum 15 Q&As across 7 categories (see Section 9.5)

---

## 📊 8. Schema Markup (JSON-LD — Mandatory Per Page)

Place all JSON-LD inside `<script type="application/ld+json">` in the `<head>`.

### 8.1 — LocalBusiness Schema (index.html and contact.html)

```json
{
  "@context": "https://schema.org",
  "@type": "LocalBusiness",
  "name": "NetPaint",
  "description": "Professional painting and building repairs company serving Cape Town and surrounding areas.",
  "url": "https://www.netpaint.co.za",
  "telephone": "+27834561909",
  "email": "info@netpaint.co.za",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "123 Main Street",
    "addressLocality": "Cape Town",
    "postalCode": "8001",
    "addressCountry": "ZA"
  },
  "geo": {
    "@type": "GeoCoordinates",
    "latitude": -33.9249,
    "longitude": 18.4241
  },
  "areaServed": ["Cape Town", "Somerset West", "Stellenbosch", "Durbanville"],
  "serviceType": ["Interior Painting", "Exterior Painting", "Surface Repairs", "Protective Coatings", "Commercial Painting"],
  "openingHoursSpecification": [
    {
      "@type": "OpeningHoursSpecification",
      "dayOfWeek": ["Monday","Tuesday","Wednesday","Thursday","Friday"],
      "opens": "08:00",
      "closes": "17:00"
    }
  ]
}
```

### 8.2 — FAQPage Schema (faq.html — expand with all Q&As)

```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "How much does interior painting cost in Cape Town?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Interior painting in Cape Town typically starts from R35 per square metre depending on surface condition, paint quality, and number of coats. NetPaint provides free, no-obligation written quotes. Call +27 83 456 1909 to arrange a site visit."
      }
    },
    {
      "@type": "Question",
      "name": "Which areas does NetPaint serve?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "NetPaint serves Cape Town and all surrounding areas within a 100km radius, including Somerset West, Stellenbosch, Durbanville, Paarl, and the Cape Winelands."
      }
    },
    {
      "@type": "Question",
      "name": "How long does a house painting project take?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "A standard 3-bedroom interior painting project typically takes 3 to 5 working days. Exterior projects depend on surface preparation and weather, but most complete within 5 to 7 working days. Timelines are confirmed in writing during your free quote."
      }
    },
    {
      "@type": "Question",
      "name": "Is NetPaint insured?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Yes. NetPaint is fully insured for public liability on all residential and commercial projects across Cape Town and surrounding areas."
      }
    },
    {
      "@type": "Question",
      "name": "Do you provide a warranty on your painting work?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "NetPaint provides a written workmanship warranty on all completed projects. Duration varies by paint system and surface type. Full warranty details are included in every written quote."
      }
    }
  ]
}
```

### 8.3 — Service Schema (services.html)

```json
{
  "@context": "https://schema.org",
  "@type": "Service",
  "serviceType": "Painting and Building Repairs",
  "provider": {
    "@type": "LocalBusiness",
    "name": "NetPaint",
    "telephone": "+27834561909",
    "url": "https://www.netpaint.co.za"
  },
  "areaServed": {
    "@type": "Place",
    "name": "Cape Town, South Africa"
  }
}
```

---

## 📋 9. Page-by-Page Build Specifications

### 9.1 — `index.html` (Home Page)

**Exact section order:**
1. `.announcement-bar`
2. `<nav class="nav">` — active link: Home
3. `<section class="hero">` — H1, star badge, dual CTA, hero-badges
4. `<section class="services-strip">` — 3 cards: Interior (.green), Exterior (.dark), Repairs (.lime)
5. `<section class="cta-strip">` — "Ready to Transform Your Property?"
6. `<section class="about-section">` — stats, company intro, visual with `.licensed-float`
7. `<section class="hiw-section">` — 3-step process
8. `<section class="quality-banner">` — full-bleed image with headline
9. `<section class="gallery-section">` — 6-cell grid, "View All Work →" link to `gallery.html`
10. `<section class="results-section">` — checklist, floating tabs
11. `<section class="faq-section">` — 4–5 items, "See all FAQs →" link to `faq.html`
12. `<section class="cta-full">` — final conversion CTA
13. `<footer>`
14. `<div class="sticky-cta">`

**Schema:** LocalBusiness JSON-LD

---

### 9.2 — `services.html` (Primary SEO Page)

**Exact section order:**
1. `.announcement-bar` + `<nav>` — active: Services
2. Page hero — dark with overlay, H1: "Professional Painting Services in Cape Town", breadcrumb, CTA button
3. AEO entity paragraph (all four entity facts — see 7.1)
4. Five service sections in this exact order, each using `.about-section` with anchor IDs:

```html
<section id="interior-painting" class="about-section">
  <div class="about-inner">
    <!-- Left: eyebrow, h2, description, checklist, CTA button -->
    <!-- Right: .about-visual with image -->
  </div>
</section>
```

| Section ID | H2 text | Background |
|---|---|---|
| `interior-painting` | Interior Painting<br>*Cape Town* | `var(--off-white)` |
| `exterior-painting` | Exterior Painting<br>*Cape Town* | `var(--white)` |
| `surface-repairs` | Surface Preparation<br>*& Repairs* | `var(--sage-tint)` |
| `protective-coatings` | Protective &<br>*Waterproofing Coatings* | `var(--off-white)` |
| `commercial-painting` | Commercial Painting<br>*Cape Town* | `var(--white)` |

- Alternate text/image left-right between sections
- Each section: eyebrow (service name), h2 title with `<em>`, 3–4 sentence description, 4–5 item `.results-list`, `.btn-results` linking to `contact.html`
- `.cta-strip` between every 2 service sections
- FAQ teaser: 3 questions in `.faq-list`, link to full `faq.html`
- `.cta-full` before footer

**Schema:** Service JSON-LD

---

### 9.3 — `gallery.html`

**Exact section order:**
1. `.announcement-bar` + `<nav>` — active: Gallery
2. Page hero — H1: "Our Work Across Cape Town", dark with overlay, CTA to `contact.html`
3. Filter bar (vanilla JS):
```html
<div class="gallery-filter">
  <button class="r-tag active" data-filter="all">All</button>
  <button class="r-tag" data-filter="interior">Interior</button>
  <button class="r-tag" data-filter="exterior">Exterior</button>
  <button class="r-tag" data-filter="repairs">Repairs</button>
  <button class="r-tag" data-filter="commercial">Commercial</button>
</div>
```
4. `.gallery-section` → `.gallery-grid` — minimum 9 cells, mix of `.wide`, `.tall`, default
5. Each cell has `data-category` attribute matching filter values
6. `.cta-full` — "Seen Enough? Let's Talk About Your Project."
7. `<footer>` + `.sticky-cta`

**Image alt pattern:**
```html
alt="interior painting project in Claremont Cape Town completed by NetPaint"
alt="exterior repaint of residential property in Stellenbosch by NetPaint"
```

**Location tags for `.g-sub`:**
Claremont, Stellenbosch, Somerset West, Durbanville, Paarl, Sea Point, Constantia, Bellville

---

### 9.4 — `about.html`

**Exact section order:**
1. `.announcement-bar` + `<nav>` — active: About
2. Page hero — H1: "About NetPaint — Cape Town's Painting Specialists", dark, CTA to `contact.html`
3. Company story — `.about-section`: narrative 3–4 paragraphs left, image right. Include entity paragraph (see 7.1).
4. Stats block — reuse `.stats-row` in an `.about-inner` layout: 10+ Years, 850+ Projects, 100% Insured, 4 Areas Served
5. `.hiw-section` — "How We Work" (identical 3-step component)
6. Values grid — use `.services-strip-inner` 3-col pattern on `var(--sage-tint)`:
   - 5 cards: Trust, Quality, Reliability, Cleanliness, Fair Pricing
   - Each card uses `.svc-card`, emoji, `.svc-title` for value name, `.svc-desc` for 2-sentence description
7. Insurance callout — use `.cta-strip` layout, list coverage details
8. `.cta-full`
9. `<footer>` + `.sticky-cta`

---

### 9.5 — `faq.html`

**Exact section order:**
1. `.announcement-bar` + `<nav>` — active: FAQ
2. Page hero — H1: "Frequently Asked Questions About Our Painting Services", AEO intro in subtext
3. Seven FAQ category sections, each:
```html
<div class="faq-category">
  <h2 class="section-title">Pricing &amp; <em>Quotes</em></h2>
  <div class="faq-list">
    <details class="faq">...</details>
  </div>
</div>
```

**Categories and minimum Q&As:**

| Category `<h2>` | Min Q&As | Required content |
|---|---|---|
| Pricing & Quotes | 3 | Starting price in Rands per m², free quote offer |
| Service Areas | 2 | Name specific suburbs: Claremont, Stellenbosch, Somerset West, Durbanville |
| Project Timelines | 2 | Days for 3-bed interior, days for exterior |
| Paint & Materials | 2 | Brand names: Dulux, Plascon, Prominent |
| Surface Preparation | 2 | What prep work is included |
| Warranties & Guarantees | 2 | Written warranty, what's covered |
| Commercial Services | 2 | Types of commercial work, contact method |

**Answer quality rules:**
- Minimum 2 sentences per answer — no one-liners
- Pricing answers must include: starting price in Rands + "Call +27 83 456 1909 to arrange a free site visit"
- Area answers must name at least 3 specific Cape Town suburbs
- Never end an answer without a fact or a contact nudge

4. `.cta-full` — "Still have questions? Call us directly."
5. `<footer>` + `.sticky-cta`

**Schema:** FAQPage JSON-LD with all Q&As included

---

### 9.6 — `contact.html`

**Exact section order:**
1. `.announcement-bar` + `<nav>` — active: Contact
2. Minimal hero — H1: "Get Your Free Painting Quote", short friction-removing subtext
3. Two-column contact layout:

**Left column — contact info and trust signals:**
```html
<div class="contact-left">
  <h2 class="about-title">Let's talk about <em>your project</em></h2>
  <p class="about-desc">No pushy sales. Just a straightforward chat about what you need and a free written quote within 24 hours.</p>
  <a href="tel:+27834561909" class="contact-item">📞 +27 83 456 1909</a>
  <a href="https://wa.me/27834561909?text=Hi%20NetPaint%2C%20I%27d%20like%20a%20quote" class="contact-item" target="_blank" rel="noopener">💬 WhatsApp Us</a>
  <a href="mailto:info@netpaint.co.za" class="contact-item">✉ info@netpaint.co.za</a>
  <div class="contact-item">📍 123 Main Street, Cape Town, 8001</div>
  <div class="results-tag-row" style="margin-top: 1.5rem;">
    <span class="r-tag">✓ Fully Insured</span>
    <span class="r-tag">✓ Free Quotes</span>
    <span class="r-tag">✓ Reply Within 24hrs</span>
  </div>
</div>
```

**Right column — quote request form:**
```html
<form class="quote-form" action="https://formspree.io/f/[FORM_ID]" method="POST">
  <label for="name">Full Name *</label>
  <input type="text" id="name" name="name" required placeholder="Your name">

  <label for="phone">Phone Number *</label>
  <input type="tel" id="phone" name="phone" required placeholder="+27 ...">

  <label for="email">Email Address</label>
  <input type="email" id="email" name="email" placeholder="your@email.com">

  <label for="service">Service Required</label>
  <select id="service" name="service">
    <option value="">Select a service...</option>
    <option>Interior Painting</option>
    <option>Exterior Painting</option>
    <option>Surface Repairs</option>
    <option>Protective Coatings</option>
    <option>Commercial Painting</option>
    <option>Other</option>
  </select>

  <label for="area">Your Location / Area</label>
  <input type="text" id="area" name="area" placeholder="e.g. Stellenbosch">

  <label for="message">Tell Us About Your Project</label>
  <textarea id="message" name="message" rows="4" placeholder="What needs painting? Size? Timeline?"></textarea>

  <button type="submit" class="btn-hero-primary" style="width:100%; justify-content:center;">
    Request My Free Quote →
  </button>
</form>
```

4. Google Maps embed — Cape Town service area. `width: 100%; height: 320px; border: none; border-radius: var(--r-lg)`
5. `<footer>` + `.sticky-cta`

**Form CSS — add to `styles.css` if not present:**
```css
.quote-form { display: flex; flex-direction: column; gap: 1rem; }
.quote-form label {
  font-size: .875rem; font-weight: 600;
  color: var(--charcoal); font-family: var(--sans);
}
.quote-form input,
.quote-form select,
.quote-form textarea {
  width: 100%; padding: .75rem 1rem;
  border: 1.5px solid var(--border);
  border-radius: var(--r);
  font-family: var(--sans); font-size: 1rem;
  color: var(--near-black); background: var(--white);
  transition: border-color .2s;
}
.quote-form input:focus,
.quote-form select:focus,
.quote-form textarea:focus {
  outline: none;
  border-color: var(--green);
  box-shadow: 0 0 0 3px rgba(61,122,53,.12);
}
.contact-item {
  display: flex; align-items: center; gap: .75rem;
  padding: .875rem 1.25rem;
  border: 1px solid var(--border);
  border-radius: var(--r-lg);
  margin-bottom: .75rem;
  font-size: 1.1rem; font-weight: 500;
  color: var(--charcoal);
  transition: border-color .2s, color .2s;
}
.contact-item:hover { border-color: var(--green); color: var(--green); }
```

**Schema:** LocalBusiness JSON-LD

---

## ⚡ 10. Performance & Accessibility

### 10.1 — Images

- All images: `loading="lazy"` — except the hero background image which loads eagerly (it's above the fold)
- Preferred format: `.webp`. Always add `<picture>` with `.jpg` fallback for critical images:
```html
<picture>
  <source srcset="images/project.webp" type="image/webp">
  <img src="images/project.jpg" alt="interior painting Claremont Cape Town by NetPaint" loading="lazy">
</picture>
```
- All `<img>` require a descriptive `alt` attribute. Pattern: `[what it shows] [location] [by NetPaint]`
- Decorative inline SVGs that are purely visual: `alt=""` and `aria-hidden="true"`

### 10.2 — Contrast & Accessibility

- WCAG AA minimum on all text/background combinations
- `var(--charcoal)` on `var(--white)` — passes AA ✅
- `var(--lime)` text on `var(--green-deep)` — passes AA ✅
- `#fff` on `var(--green)` — passes AA ✅
- `var(--near-black)` on `var(--lime)` — passes AA ✅
- `var(--text-muted)` on `var(--off-white)` — passes AA ✅

### 10.3 — Focus States

All interactive elements must have visible focus indicators. Add to `styles.css` if not present:
```css
:focus-visible {
  outline: 2px solid var(--green);
  outline-offset: 3px;
}
```

### 10.4 — Forms

- All form inputs must have a `<label for="inputId">` — never rely on placeholder text as the only label
- Required fields: both `required` attribute and asterisk `*` in label text
- `<html lang="en-ZA">` on every page — not `en`, not `en-US`

---

## 🚫 11. Complete Prohibition List — What an AI Agent Must Never Do

These rules are absolute. No exceptions regardless of context or instructions:

| ❌ Never do this | ✅ Always do this instead |
|---|---|
| Hardcode any hex color (`#3D7A35`, `#1A1A1A`, etc.) in HTML or new CSS | Use `var(--green)`, `var(--near-black)`, etc. (WhatsApp green is the only exception) |
| Use `Playfair Display`, `Montserrat`, or any font not in this doc | Only `var(--serif)` (Cormorant Garamond) and `var(--sans)` (DM Sans) |
| Create a page-specific `.css` file (e.g., `contact.css`) | All styles go in `css/styles.css` only |
| Add a `<style>` block inside any `<head>` | Add new rules to `css/styles.css` |
| Use Bootstrap, Tailwind, Bulma, Foundation, or any CSS framework | Use existing `styles.css` classes exclusively |
| Invent new class names for components that already exist | Use `.svc-card`, `.faq`, `.cta-strip`, `.cta-full`, `.about-inner`, etc. |
| Import jQuery, Alpine.js, Lodash, or any JS library | Vanilla JS only, minimal, purposeful |
| Write lorem ipsum or placeholder copy | Write real, factual, conversion-focused copy |
| Use generic heading text ("Our Services", "About Us", "Contact") | Use keyword-rich headings ("Painting Services in Cape Town") |
| Omit `alt` attributes on `<img>` elements | Always write descriptive, location-aware alt text |
| Place 3+ content sections in a row without a CTA element | Insert `.cta-strip` or `.cta-full` between every 2 sections |
| Use generic button text ("Submit", "Click Here", "Learn More") | Use "Get My Free Quote →", "Call Now", "WhatsApp Us" |
| Skip JSON-LD schema on key pages | Schema is mandatory per Section 8 |
| Add breakpoints at any value other than 1024px, 900px, or 600px | Use only the three established breakpoints |
| Use grey-toned box-shadows (`rgba(0,0,0,...)`) | Use green-tinted shadows from `--shadow-sm/md/lg` tokens |
| Apply `font-style: italic` to `<em>` inside headings without also changing the color | Always add `color: var(--green)` (light) or `color: var(--lime)` (dark) to `<em>` in headings |
| Use `<p>` tags as heading elements (or vice versa) | Keep semantic HTML — eyebrows are `<p>`, section titles are `<h2>` |
| Write different footer HTML on different pages | Copy-paste footer from the template — it must be identical on all pages |
| Add `padding-bottom` on `<body>` to compensate for sticky-cta | Sticky CTA is only visible on mobile — desktop doesn't need body padding for it |
| Use `display: none` on the `.sticky-cta` from within the HTML | The stylesheet already handles this via media query — do not override it |
| Forget `target="_blank" rel="noopener"` on external links (WhatsApp, Maps) | Always add both attributes to any link that opens a new tab |

---

## ✅ 12. Pre-Commit Checklist

Run through every item before marking any page complete. All must be checked.

**Conversion:**
- [ ] CTA visible above the fold in hero
- [ ] Phone link uses `href="tel:+27834561909"` — enables click-to-call
- [ ] WhatsApp links use full pre-filled URL (see Section 5.1)
- [ ] Minimum 2 CTA sections per page (`.cta-strip` + `.cta-full` at minimum)
- [ ] `.cta-full` is the last section before `<footer>`
- [ ] `.sticky-cta` bar is present as last element before `</body>`
- [ ] All button copy matches the approved copy from Section 5.4

**SEO:**
- [ ] `<title>` is unique, 50–60 characters, includes location keyword
- [ ] Meta description is unique, 140–160 characters, includes service + location + action
- [ ] `<link rel="canonical">` present with full correct URL
- [ ] Exactly one `<h1>` on the page — in the hero — includes primary keyword
- [ ] `alt` on every `<img>` — descriptive + location-aware per pattern
- [ ] At least one internal link to `services.html` with descriptive anchor text
- [ ] At least two internal links to `contact.html`

**AEO:**
- [ ] Entity clarity paragraph present in body copy (business name, type, location, contact)
- [ ] JSON-LD schema present in `<head>` for this page type
- [ ] FAQ section or link to `faq.html` present on this page

**Design System:**
- [ ] Zero hardcoded hex colors anywhere in the HTML file
- [ ] Zero new font families — only `var(--serif)` and `var(--sans)` used
- [ ] No new component class names invented for already-styled components
- [ ] All colors referenced via CSS custom properties
- [ ] Navigation shows correct `.active` state for current page
- [ ] Footer HTML is identical to all other pages (copy-paste verified)
- [ ] No `<style>` blocks in `<head>`

**Accessibility:**
- [ ] All form inputs paired with `<label for="...">`
- [ ] `:focus-visible` styles present in `styles.css`
- [ ] `<html lang="en-ZA">` on page
- [ ] No placeholder-only form labeling
- [ ] External links have `target="_blank" rel="noopener"`

**Responsive:**
- [ ] Layout verified at 375px mobile width (single column, sticky CTA visible)
- [ ] Layout verified at 1280px desktop width (full grid, sticky CTA hidden)

---

## 📎 13. Quick Reference

### Business Details

```
Name:            NetPaint
Phone display:   +27 83 456 1909
Tel href:        tel:+27834561909
WhatsApp URL:    https://wa.me/27834561909
WhatsApp fill:   ?text=Hi%20NetPaint%2C%20I%27d%20like%20a%20quote
Full WA link:    https://wa.me/27834561909?text=Hi%20NetPaint%2C%20I%27d%20like%20a%20quote
Email:           info@netpaint.co.za
Email href:      mailto:info@netpaint.co.za
Address:         123 Main Street, Cape Town, 8001, South Africa
Coordinates:     -33.9249, 18.4241
```

### Design Tokens — Full Reference

```css
/* Greens */
--green:        #3D7A35   Primary CTAs, buttons, links, icons, focus borders, checkmarks
--green-dark:   #1A5C1A   Hover states, announcement bar bg, deeper section fills
--green-deep:   #0F3D0F   cta-strip bg, darkest section backgrounds
--lime:         #C8D480   Accent on dark: .btn-cta bg, gallery dots, badges, <em> in dark headings
--lime-dark:    #A8B460   .btn-cta:hover only
--sage:         #6E9E6E   Decorative elements, FAQ open border, step connector arrows
--sage-tint:    #F4F7F0   Alternate section bg: results, FAQ items, values grid
--sage-light:   #EBF2E8   Hover surfaces, subtle highlights

/* Neutrals */
--near-black:   #1A1A1A   Headings on light bg, body text color, .btn-cta text
--charcoal:     #4A4A4A   Body copy, nav links default, form labels
--white:        #FFFFFF   Page background, card fills, button text on green
--off-white:    #F8FAF7   About section bg, accordion item bg
--text-muted:   #6B7E6A   Descriptions, captions, step text, FAQ answer text

/* Borders */
--border:       #DDE8D8   Card borders, input borders, dividers, nav bottom
--border-dark:  #C5D8BE   Stronger emphasis borders

/* Typography */
--serif:  'Cormorant Garamond', Georgia, serif   → ALL headings
--sans:   'DM Sans', system-ui, sans-serif        → ALL body, nav, buttons

/* Layout */
--max:    1200px   Container max-width
--r:      6px      Default border-radius
--r-lg:   14px     Card/image/modal border-radius

/* Shadows (green-tinted only) */
--shadow-sm: 0 2px 8px rgba(26,92,26,.08)     Floating tabs, small UI
--shadow-md: 0 8px 32px rgba(26,92,26,.12)    Image containers
--shadow-lg: 0 24px 64px rgba(26,92,26,.16)   Main images, hero-adjacent
```

### Image Filenames Referenced in Stylesheet

| CSS reference | Expected file |
|---|---|
| `.hero` background | `/images/hero-bg.webp` |
| `.quality-banner` background | `/images/Modern-Living-Room-Fireplace-CAPE-TOWN.webp` |

### Pages Build Status (Update As You Go)

- [ ] `css/styles.css` ✅ exists — do not recreate
- [ ] `index.html`
- [ ] `services.html`
- [ ] `gallery.html`
- [ ] `about.html`
- [ ] `faq.html`
- [ ] `contact.html`

---

*This file is the authoritative source of truth for all AI-assisted development on this project. Every decision must trace back to Section 1: increase the probability that a visitor contacts NetPaint.*