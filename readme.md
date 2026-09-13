# Amprator Shipping — Landing Page (Rebuild)

A pixel-faithful, single-page landing page for **Amprator Shipping** (vehicle
shipping from USA & Canada to Afghanistan), rebranded around the provided
logo and its extracted color palette (navy `#0E1F45` + metallic gold `#C9A24C`).
Rebuilt from the original reference site's design system — everything runs
locally, no build step.

## Run / Open

No dependencies. Just open the entry file in any modern browser:

- **Entry file:** `index.html` (double-click, or drag into Chrome/Edge)
- Internet is only needed for the Cairo webfont (Google Fonts) — the page
  falls back to the system font stack when offline.
- `assets/hero.mp4` is the original site's hero background video (local copy).

## What's inside

```
jacxi-landing/
├── index.html          ← the entire landing page (HTML + CSS + JS, self-contained)
├── assets/
│   ├── logo.png        ← Amprator logo, optimized to display size (39KB)
│   ├── logo-full.png   ← full-res emblem (569KB, source for og-image)
│   ├── favicon.png     ← navy favicon generated from the emblem
│   ├── poster.jpg      ← branded hero video poster (first paint)
│   ├── og-image.jpg    ← 1200×630 social share card
│   ├── hero.mp4        ← the original site's cinematic car-scene hero video
│   └── world-map.svg   ← map texture used in phone mockups + route map
│   └── logos/          ← auction partner marks: Copart (official) · Manheim (official) · ADESA (official) · IAAI (wordmark)
└── README.md
```

## Page structure (mirrors the original landing page)

| # | Section | Anchor | Content |
|---|---------|--------|---------|
| 1 | Navbar (glass, fixed) | — | Logo, Routes/Services/Process/Quote/Reviews/FAQ/Contact, Track + Get a free quote |
| 2 | Hero | `#home` | Video background, word-by-word headline, phone dashboard mockup, floating "Live routes active" / "Avg Transit Time 30–45 Days" cards, 4 corridor cards |
| 3 | Global routing | `#routes` | "Precision paths to Afghanistan", origin→hub→final timeline, animated SVG route map (Canada/USA → Mersin/UAE → Afghanistan) |
| 4 | Services | `#services` | "End-to-end logistics. Simplified." — 4 alternating rows with SVG scene panels |
| 5 | Process | `#process` | "Five milestones. Zero friction." — draggable horizontal scroller, 01–05 cards + End of process cap |
| 6 | Estimator | `#quote` | "Instant lane pricing." — live lane calculator (origin + destination + vehicle type → subtotal) |
| 7 | Customer portal | `#portal` | "Shipment visibility from the browser in your pocket." — features + milestone-tracker phone mockup |
| 8 | Hubs marquee | — | "Serving all major hubs" — 10 Afghan cities scrolling |
| 9 | Testimonials | `#reviews` | "Reputation built on flawless delivery." + TRUSTED watermark, scrolling review cards |
| 10 | FAQ | `#faq` | 5 accordion items (exact original copy) |
| 11 | Quote form | `#get-quote` | "Precision pricing. Guaranteed lanes." — floating-label form with validation + success state |
| 12 | About | `#about` | "Our story", 4 check pills, 3 trust cards |
| 13 | Contact | `#contact` | Phone / WhatsApp / Email / Address cards, social pills, message form with validation |
| 14 | Footer | — | Quick links, corridors, contact, socials, copyright |
| — | Auction partner strip | — | Copart · IAAI · Manheim · ADESA chips (grayscale → color on hover, linked) under "Direct buying access" |
| — | Sticky mobile CTA bar | — | Call / WhatsApp / Get a quote — fixed bottom on phones |
| — | WhatsApp FAB + back-to-top | — | Desktop floating buttons (FAB appears ≥768px, top button after 700px scroll) |

## Design tokens (extracted from the logo + original)

- Brand navy: `#0E1F45` (deep `#0A1330`), metallic gold: `#C9A24C` (light `#E8C06A`)
- `--gold-text:#8A6D1F` — darker gold for small text labels (WCAG AA on white); bright gold stays on graphics/dark backgrounds
- Background `#F9FAFB`, panel `#FFFFFF`, border `#E5E7EB`
- Text primary `#1C1C1E`, secondary `#5F6368`
- Headlines: Cairo 900, tracking −0.03em; accent words: Georgia italic light
- Labels: monospace uppercase, 0.2em tracking, gold, with 24px dashes
- Cards: 1.5–2rem radius, 1px rgba(0,0,0,.07) border, soft shadow
- Buttons: full-round navy pills, gold sheen sweep on hover
- Motion: 0.72s `cubic-bezier(.22,1,.36,1)` scroll reveals; `prefers-reduced-motion` respected

## How to modify

| Change | Where |
|--------|-------|
| Colors / brand navy & gold | `:root` CSS variables at the top of `index.html` |
| Headline / section copy | Search the visible text in `index.html` — every string is inline HTML |
| Lane prices / corridors / vehicle multipliers | `ORIGINS`, `DESTS`, `VEHICLES` arrays in the `<script>` block |
| Testimonials | `REVIEWS` array in the `<script>` block (cards render automatically) |
| FAQ items | `<details class="qa">` blocks |
| Phones / emails / socials | Search `tel:+1`, `wa.me`, `info@jacxi.com`, `.soc` links |
| Hero video | Replace `assets/hero.mp4` (page falls back to a gold/charcoal gradient if missing) |
| Route map shape | SVG paths in the `#routes` section (`M 250 168 Q …` — original coordinates kept) |
| Fonts | `<link>` to Google Fonts + `--sans` variable |

## Quality notes

- Responsive: 4→2→1 column grids, hero stacks below 1024px, process cards sized
  to 82vw on mobile; nav collapses to a slide-in panel.
- Interactive states: hover lifts on cards, gold focus rings, button disabled +
  "Processing..."/"Sending..." states, inline field errors, success panels,
  single-open FAQ accordion, drag-scrollable milestone strip with progress bar.
- Empty/error states: video error → gradient fallback; forms validate every
  field with the original site's exact error messages.
- Accessibility: landmarks, aria-labels, aria-pressed on vehicle chips,
  aria-expanded on menu, keyboard Escape closes the menu, reduced-motion support.
- Verified: HTML tags balanced (12 sections, 240 div pairs), JS passes
  `node --check`, all 3 asset references resolve to real local files.

## Notes / next steps

### SEO / launch checklist
- `og:url` and the JSON-LD `url`/`logo` use the placeholder domain `https://amprator.com/` — replace with the real domain before going live. For maximum crawler support, also give `og:image`/`twitter:image` their absolute live URLs.
- ✅ DONE: phone numbers (+1 647 447 1814 / +93 700 006 284 / +93 705 000 118), WhatsApp, and email (info@amprator.com) are now real. Still placeholders: office address and the four customer testimonials — swap before launch.

### What's wired in
- **Awwwards layer:** brand preloader with counter, animated film grain, custom gold cursor (dot + trailing ring), lerp-smoothed wheel scrolling, scroll progress bar, masked clip-path heading reveals, cursor spotlight on all cards, magnetic CTAs, velocity-skewed marquees, stats band with count-ups, navy final CTA act, giant outlined footer wordmark + live Herat clock. Desktop niceties auto-disable on touch/reduced-motion.
- **Animated route map** — scroll-drawn paths that switch to flowing dashes, two traveling shipment dots (SMIL), drifting world-map backdrop, pulsing destination ring.
- **Dark mode** — navbar sun/moon toggle, system-preference detection, pre-paint theme script (no flash), 71 dark overrides, choice persisted in localStorage.
- Scrollspy: the active nav link gets a gold underline + `aria-current="true"` as you scroll.
- SVG card microinteractions (Services): truck drives the lane on hover, ship bobs/sails with rising smoke + hopping containers, customs check redraws and the OK stamp slams, warehouse boxes hop in sequence — plus ambient loops (flowing dashes, pulsing pins, breathing dot grids, drifting waves). Row-level: icon flips to navy/gold, gold divider grows, card lifts with gold ring. All disabled under `prefers-reduced-motion`.
- Skip-to-content link (Tab on page load), back-to-top button (desktop, after 700px), WhatsApp FAB (desktop), sticky Call/WhatsApp/Quote bar (mobile).
- Hero video has a branded poster frame for instant first paint; logo is served at display size (39KB vs 583KB before).

- This is a static rebuild for your own landing page — forms simulate submit
  client-side. Wire `#quoteForm` / `#contactForm` to a backend or a service
  (Formspree, your Next.js API, etc.) when you go live.
- The original "Sign in" / dashboard links point to an auth app — replaced here
  with "Track shipment" (→ `#portal`) so nothing links to a dead page. Re-add
  `/auth/signin` when the dashboard exists.
- If you later want this as a Next.js/Tailwind project (like the original),
  the section order, copy, and token table above map 1:1 to components.
