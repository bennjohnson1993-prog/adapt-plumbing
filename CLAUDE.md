# Adapt Plumbing Website — Project Instructions

## Overview

This project is a **multi-page static website** for **Adapt Plumbing | Drainage | Gas**, a licensed plumbing business on the Gold Coast and Brisbane. The site is hand-coded HTML/CSS/JS — no frameworks, no CMS, no build tools. The developer (Ben) handles all edits directly. Deployed on **Netlify** via Git.

The goal of every page is **lead generation**: get the visitor to call, email, or submit a quote request. Every design and content decision serves that goal.

---

## Stack

- **HTML5 / CSS3 / Vanilla JS** — no React, no templating engines, no SSG
- **Hosting:** Netlify (free tier, deployed from Git repo)
- **Fonts:** DM Sans (weights 400, 500, 600, 700, 800) loaded via Google Fonts
- **Forms:** Netlify Forms (native, no backend needed — just add `netlify` attribute to `<form>`)
- **Analytics:** Google Analytics 4 (GA4) via `<script>` tag
- **No dependencies.** No npm, no package.json, no node_modules.

---

## Project Structure

```
/
├── index.html                  # Homepage
├── contact.html                # Contact page with quote request form
├── contact-success.html        # Form submission confirmation
├── 404.html                    # Custom 404 page
├── services/
│   └── index.html              # Services overview page
├── areas/
│   └── index.html              # Service areas overview
├── css/
│   └── styles.css              # Single stylesheet, all pages share it
├── js/
│   └── main.js                 # Minimal JS (mobile nav toggle)
├── img/
│   ├── logo.png                # Logo (PNG with transparent background)
│   ├── job-1.jpg ... job-12.jpg # Job site photos from Squarespace
│   └── ...
├── robots.txt
├── sitemap.xml
├── _headers                    # Netlify custom headers (caching, security)
└── CLAUDE.md
```

### Naming conventions
- All filenames: **lowercase, hyphen-separated** (e.g. `hot-water-systems.html`, `surfers-paradise.html`)
- Image filenames: **descriptive, hyphenated** (e.g. `blocked-drain-repair-gold-coast.jpg`)
- No spaces, no underscores, no capitals in any filename or folder

---

## Design System

### Current Design: Dark Theme

The site uses a **dark navy/blue design** — no white backgrounds anywhere.

### Font
- **DM Sans** for everything (headings and body)
- Weights: 400, 500, 600, 700, 800
- Google Fonts link: `https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600;700;800&display=swap`

### Colours
- Body/dark background: `#091625`
- Darker background (nav, footer): `#070F1C`
- Alt section background: `#0C1F36`
- Blue gradient from: `#0E2A4E`
- Blue gradient to: `#1360A6`
- Blue mid: `#1A6FC4`
- Blue bright: `#2182DB`
- Orange (CTA/brand): `#F2911E`
- Orange hover: `#E68315`
- White text: `rgba(255,255,255,0.85)` body, pure `#fff` headings
- Muted text: `rgba(255,255,255,0.4)`
- Card bg: `rgba(255,255,255,0.03)`
- Card border: `rgba(255,255,255,0.06)`

### Design Principles
1. **Dark gradient backgrounds throughout.** Sections alternate between navy-to-blue gradients and flat navy. No white backgrounds.
2. **Rounded but not pill-shaped.** Cards use 8px border-radius. Buttons use 6px. Process number circles stay round. No 50px pill shapes.
3. **Soft and warm, not futuristic.** Approachable trades business, not tech startup.
4. **Mobile-first.** Every page must work on 375px. Most visitors are on mobile.
5. **Job photos as subtle backgrounds.** Hero, services, process, and CTA sections use real job photos behind dark gradient overlays for texture.
6. **Orange is the action colour.** All CTAs, buttons, section labels, and interactive highlights use `#F2911E`.

### Layout
- `.wrap` class: `max-width: 1140px; margin: 0 auto; padding: 0 24px;` — used for all content sections
- Nav spans full viewport width with its own padding (`20px 40px`), does NOT use `.wrap`
- `.sec` sections: `padding: 64px 0` on desktop, `48px 0` on mobile
- `.sec-alt` for alternating section backgrounds

### Component Patterns
- **Nav:** Sticky, full-width, `#070F1C` background. Logo (80px height, image only — branding text baked into logo.png) hard left, nav links + orange phone text hard right. Phone is styled text, not a button.
- **Service cards:** `.card .svc` — dark glass cards in 3-column grid, blue number, hover lifts up
- **Trust bar:** Solid orange `#F2911E` background with dark text credentials
- **CTA banners:** `.cta-mid` — blue gradient strips with white/outline buttons, used after service and review grids
- **Process steps:** `.card .proc` — dark cards with orange circle numbers
- **Review cards:** `.card .rev` — dark cards with orange stars, blockquote text
- **Gallery:** `.gallery-grid` — 3-column grid of job photos, 240px height, object-fit cover
- **Final CTA:** `.fbox` — blue gradient rounded box with orange button
- **Info card:** `.info-card` — dark card for hours/contact sidebar
- **Quote form:** Netlify Forms with dark-styled inputs

### Button Classes
- `.btn-o` — solid orange (primary CTA)
- `.btn-g` — transparent with white border (ghost/outline)
- `.btn-w` — white solid (used inside blue CTA banners)
- `.btn-wg` — white outline (used inside blue CTA banners)

---

## SEO Requirements

### Every page MUST have:
1. **Unique `<title>` tag** — format: `[Page Topic] | [Business Name] | [Location]`
2. **Unique `<meta name="description">`** — compelling, includes primary keyword + location, under 155 characters
3. **One `<h1>` tag per page** — contains the primary keyword naturally
4. **Logical heading hierarchy** — h1 → h2 → h3, never skip levels
5. **Internal links** — every page links to related services and the contact page
6. **Image alt text** — descriptive, includes keyword where natural (not stuffed)
7. **Canonical URL** — `<link rel="canonical" href="https://www.adaptim.com.au/[page]">`

### Schema Markup (JSON-LD)
Homepage includes Plumber schema. Service pages should additionally include `Service` schema. FAQ sections should use `FAQPage` schema.

### Service Pages Strategy
Each service gets its own page targeting: `[service] + [location]`
- Unique h1 with service + location
- 300–600 words of unique content
- Internal links to related services
- CTA with phone number and quote form link
- At least one relevant image with descriptive alt text

### Suburb Pages Strategy
Each suburb page targets: `plumber + [suburb name]`
- Unique content mentioning the suburb naturally
- Reference to common plumbing issues in that area
- Link back to main services
- Minimum 250 words unique content

---

## Page Templates

### Homepage (index.html)
- Hero with background job photo, gradient overlay, h1, subtitle, orange CTA + outline CTA, credentials line
- Solid orange trust bar with licence numbers and hours
- "Who we are" two-column section with team photo
- Services grid (6 cards) with blue CTA banner below
- Process section (4 steps) with background job photo texture
- Reviews section (3 cards) with blue CTA banner below
- Gallery section (6 job photos in 3-column grid)
- About section with checklist and info card sidebar
- Areas section listing suburbs
- Final CTA box with background job photo
- Footer

### Contact Page
- Hero with call + email buttons
- Two-column: quote form on left, hours/contact info card on right
- Netlify Forms integration

### Other Pages
- Services overview, Areas overview, 404, contact-success all share the same nav/footer/styles

---

## Netlify Configuration

### Netlify Forms
```html
<form name="quote-request" method="POST" data-netlify="true" netlify-honeypot="bot-field">
  <input type="hidden" name="form-name" value="quote-request">
  <p class="hidden"><label>Don't fill this out: <input name="bot-field"></label></p>
  <!-- form fields -->
</form>
```

### _headers file
```
/*
  X-Frame-Options: DENY
  X-Content-Type-Options: nosniff
  Referrer-Policy: strict-origin-when-cross-origin

/css/*
  Cache-Control: public, max-age=31536000

/img/*
  Cache-Control: public, max-age=31536000

/js/*
  Cache-Control: public, max-age=31536000
```

---

## Content Guidelines

- **Write like a human, not a marketer.** Write how the tradie actually talks. First person where appropriate.
- **Short paragraphs.** Max 3–4 lines.
- **Lead with the benefit, not the feature.** "No surprise invoices" beats "transparent pricing methodology."
- **Always include the location naturally.** Gold Coast and Brisbane mentioned where it reads naturally.
- **Every page needs a clear next action.** Call, email, or submit the form.
- **Testimonials:** Use real first names and suburbs. "— Sarah M. · Robina"
- **Image optimisation:** All images compressed, descriptive filenames and alt text for SEO.

---

## Pre-Launch Checklist

- [ ] All pages have unique title + meta description
- [ ] h1 on every page, heading hierarchy correct
- [ ] Schema markup validated
- [ ] All internal links working (no 404s)
- [ ] Mobile responsive at 375px, 768px, 1024px, 1440px
- [ ] Forms submitting correctly via Netlify
- [ ] favicon and og-image in place
- [ ] Google Analytics 4 tag installed
- [ ] Google Search Console verified and sitemap submitted
- [ ] Google Business Profile claimed and optimised
- [ ] robots.txt and sitemap.xml present and correct
- [ ] Images compressed and using descriptive filenames
- [ ] Phone numbers are clickable `tel:` links on mobile
- [ ] Page speed: aim for 90+ on Google PageSpeed Insights
- [ ] 404 page exists and is helpful
- [ ] _headers file configured for caching and security
- [ ] SSL active (automatic on Netlify)
