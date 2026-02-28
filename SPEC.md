# Personal Website 2026 — Design Specification (SDD)

**Repo:** `goodkavin.github.io` | **Date:** 2026-02-28 | **Status:** Draft v3 — Under Review

---

## 1. Context & Goal

Kavin S. is rebuilding his personal website from scratch. The old site (Bootstrap 3 + jQuery) was wiped in commit `7f37a51`. Full greenfield build targeting GitHub Pages.

**Goal:** A minimal, gray, personal site — communicates who I am, what I do, what I've built, and how to reach me. Fast to parse. Honest. Tasteful. No noise.

---

## 2. Design Principles

| Preferred | Over |
|---|---|
| Dark mode | Light |
| Easy to get the point | Long text / noise |
| Clean simple shapes | 3D graphics |
| Minimal | Maximal |
| Good structure | Unstructured |
| Organic | Techy |
| Creative | Template |
| Geeky aesthetic | Conventional beauty |
| Raw & honest | Fake |
| Tasteful | Normal |
| Modern | Traditional |
| Credible | Nobody |

---

## 3. Aesthetic Direction

Industrial-functional with geeky undertones. Not cold/corporate, not creative agency, not developer blog. A person who cares about craft, function, and taste. Confident without performing.

Mood references: industrial core, retro futurism, brutalist typography, functionalism, gorp core, nature, classic menswear (proportion), Oakley core. The tension between warm/organic materials and cold/precise engineering.

Typography is the primary design element. No images, no illustrations, no decorative elements. The font pairing does all the personality work.

---

## 4. Reference Sites

| Site | Key Takeaway | Influence |
|---|---|---|
| **keliz.xyz** (primary) | Multi-page; display font + Times New Roman body; "home" link only; raw, person-not-service feel | Structure, typography formula, layout approach |
| **gnuhr.com** | Monospace catalog layout; structured data as design; functional typography | Mono labels, catalog aesthetic |
| abdussalam.pk | Highly parseable; raw workflow showcase; refined accent on dark | Parseability |
| gabewolford.com | Dark theme; mono labels; pulsing availability dot | Dark theme reference |
| gaby.gold | Profile-first; precise spacing; confident & credible | Confidence, spacing |
| every.sdf.org | Authentic geeky aesthetic; rejects web trends; raw | Raw geeky spirit |
| getcoleman.com | Specialist clarity — you know what he does immediately | Clarity of purpose |

---

## 5. Content Structure

**Multi-page site** (like keliz.xyz). Homepage with intro + link list to subpages.

```
goodkavin.github.io
│
├── index.html          ← Homepage: name, tagline, intro, link list
├── work.html           ← MineERP + other projects
├── approach.html       ← How I work (copy TBD)
├── interests.html      ← What I care about (copy TBD)
└── contact.html        ← Email + LinkedIn
```

### Homepage layout

```
HOME                                    ← top-left, links back to self

GOOD KAVIN S.
I help companies operate digitally.

[Content below]

MY APPROACH
MINEERP
OTHER WORKS
INTERESTS
CONTACT

MORE PROFESSIONAL VERSION:
LinkedIn
```

Each subpage has:
- "home" link (top-left)
- Page title in display font
- Content in body serif
- "get in touch" or similar link at bottom
- Footer

**Copy tone:** First-person. Short sentences. No buzzwords. Specific and confident. Body copy uses normal sentence case. Section headings and nav labels use ALL CAPS (e.g. `MY WORK`, `CONTACT`).

---

## 6. Tech Stack

| Layer | Choice | Rationale |
|---|---|---|
| Framework | **None — hand-written HTML + CSS** | Multi-page, zero JS. No build step, no dependencies. Raw & honest. Deploys directly to GitHub Pages. |
| Styling | Single shared CSS file with custom properties | All design tokens in `:root`, no preprocessor needed |
| Fonts | Self-hosted | No Google Fonts runtime dependency, faster load |
| Icons | Inline SVG or none | |
| JS | Zero | No interactions require it |
| Deploy | Push to `main` → GitHub Pages serves directly | No build pipeline, no GitHub Actions |
| Domain | `goodkavin.github.io` | No custom domain |

### File Structure

```
goodkavin.github.io/
├── index.html          ← homepage
├── work.html           ← work page
├── approach.html       ← approach page
├── interests.html      ← interests page
├── contact.html        ← contact page
├── style.css           ← all styles (shared)
├── fonts/
│   ├── Michroma-Regular.woff2
│   ├── CMUSerif-Roman.woff2
│   ├── CMUSerif-Italic.woff2
│   ├── CMUSerif-Bold.woff2
│   ├── JetBrainsMono-Regular.woff2
│   └── JetBrainsMono-Medium.woff2
├── favicon.svg         ← text-based SVG favicon
├── og-image.png        ← social sharing image
├── SPEC.md             ← this file
├── font-test.html      ← (dev only, remove before launch)
└── heading-test.html   ← (dev only, remove before launch)
```

Five HTML files. One CSS file. Self-hosted fonts. That's the site.

---

## 7. Visual Specification

### Colors

```css
:root {
  --color-bg:         #0e0e0e;                    /* near-black */
  --color-surface:    #141414;                    /* 1 step up — use sparingly */
  --color-border:     rgba(255, 255, 255, 0.07);  /* ultra-subtle dividers */
  --color-text-1:     #f0ede8;                    /* warm off-white — primary text */
  --color-text-2:     #888888;                    /* secondary / meta text */
  --color-link:       #6ba3be;                    /* cool blue — nav links (like keliz.xyz) */
  --color-accent:     #a0785a;                    /* warm brown — project links, arrows */
  --color-accent-dim: #6b5240;                    /* accent hover/muted state */
}
```

Two link colors: cool blue (`--color-link`) for navigation (like keliz.xyz), warm brown (`--color-accent`) for project/external links and arrow glyphs. This gives visual hierarchy — nav links are wayfinding, accent links are destinations.

### Typography

**Three-font system. Decided.**

| Role | Font | Usage |
|---|---|---|
| **Display** | Michroma (letter-spacing: 0.20em) | Name, page titles, project names. Wide, geometric, industrial — NSX/Eurostile energy. |
| **Body** | Computer Modern Serif (CMU Serif) | All body text, link lists, descriptions. The LaTeX font — peak early IT academia. Raw. |
| **Labels** | JetBrains Mono | Section labels (WORK, CONTACT), meta text (2025 · Live), footer. Catalog/functional feel. |

All three fonts are free (OFL), self-hosted as woff2.

```css
:root {
  --font-display: 'Michroma', system-ui, sans-serif;
  --font-body:    'Computer Modern Serif', 'CMU Serif', 'Times New Roman', Times, serif;
  --font-mono:    'JetBrains Mono', 'Courier New', monospace;

  /* Display font letter-spacing */
  --ls-display:   0.20em;   /* name, page titles */
  --ls-tagline:   0.12em;   /* tagline, smaller display text */
  --ls-label:     0.20em;   /* section labels in display font */

  /* Fluid type scale */
  --text-xs:   clamp(0.7rem,   0.65rem + 0.25vw, 0.8rem);   /* meta labels */
  --text-sm:   clamp(0.875rem, 0.8rem  + 0.35vw, 1rem);     /* small body */
  --text-base: clamp(1rem,     0.95rem + 0.25vw, 1.125rem);  /* body */
  --text-lg:   clamp(1.25rem,  1.1rem  + 0.75vw, 1.75rem);  /* section titles */
  --text-xl:   clamp(1.75rem,  1.4rem  + 1.5vw,  3rem);     /* hero name */
}
```

### Layout

```css
:root {
  --padding-x:   clamp(1.25rem, 5vw, 2.5rem);
  --section-gap: clamp(3rem, 8vw, 6rem);
}
```

- **Full-width layout** — no max-width container. Text goes edge to edge with horizontal padding. Like keliz.xyz.
- Left-aligned everything
- No cards, no grid-of-boxes — linear reading flow
- Body text naturally wraps at comfortable reading width due to font size + viewport
- Subtle `1px` rules between sections using `--color-border` (optional, may omit for rawer feel)

### Navigation

- **All pages:** "home" link in top-left corner. That's it. No nav bar, no hamburger, no section links.
- Homepage has a link list to subpages (my work, my approach, interests, contact)
- Each subpage links back to home
- Links use `--color-link` (cool blue), hover to `--color-accent` (warm brown)

### Motion

- Default: none
- Links: `color` transition, `0.15s ease`
- No scroll animations, no parallax, no GSAP, no fade-in

---

## 8. Page Specs

### Homepage (index.html)

```
HOME                                            ← --font-body, --color-link

GOOD KAVIN S.                                   ← --font-display, --text-xl, --ls-display
I help companies operate digitally.             ← --font-display, --text-lg, --ls-tagline, --color-text-2

Hi, I'm Good. I have a background in enterprise digital transformation.
Now I'm a co-founder of MineERP, an ERP for Thai SME, especially manufacturers.
I focus on building a software for complex business, but simple to use like modern application.
I lead my team of developers and designers and also contribute as a product manager.
I am passionate about efficiency and want to generate a positive impact to local community and the world.

MY WORK                                         ← --font-body, --color-link
MY APPROACH                                     ← --font-body, --color-link
INTERESTS                                       ← --font-body, --color-link
CONTACT                                         ← --font-body, --color-link

@Claude """
revise to:
MINEERP (link to mineerp.com)
MY APPROACH
MY WORKS
INTERESTS
CONTACT
"""

ELSEWHERE:                                      ← --font-body, --color-text-2
LinkedIn                                        ← --font-body, --color-link
```

### Work (work.html)

```
HOME                                            ← --font-body, --color-link

MY WORKS                                        ← --font-display, --text-lg, --ls-display

[1–2 line context paragraph]                    ← --font-body
2022-PRESENT
COO, NPR Digital Partner (MineERP)
- Currently focusing on scaling MineERP to more users
- Worked on ground with Thai SME shop floor workers, delivery drivers, warehouse staff, production planners, managers, executive, to truly understand their needs 
- Build culture and manage a team of 7-12 people including developers, designers, and QA
- Researched a lot of ERPs and iterate MineERP over and over to find the best and truly unique way to solve problem with MineERP
- Set UX direction of MineERP
- Experience digital transformation in Manufacturing, Trading, Retail, E-Commerce, Logistics, Construction Material
- Also did a lot of customized projects including: data platform, dashboard, E-Commerce automation, WMS, CRM, Mini-ERP, Retail ERP, website, government projects, and other things to keep the company running and feed myself (and my team)
- Shout out to my team (and ex-members), and also my early clients, they are the best <3


2019-2022
Data Engineer, Accenture
- Industry: Banking, Retail, Insurance
- My work is basically understand which data is required for business, identify data source, and build a pipeline to deliver data to user
- Built real-time data framework (Databricks, Azure, Kafka)
- Researched and implemented Delta Lake (unified batch and streaming data)
- Developed Voice AI chatbot for customer service POC - This is pretty cool, LLM probably helped a lot now
- Part of a big data migration team from legacy data platform on-premise in UK to cloud in Singapore

2018
Software Engineer Intern, Digital Ventures (SCB 10X)
- Learned about blockchain and practical applications (it's mostly hype)
- Learned software development process in enterprise scale
- Coded some Kotlin/Smart Contract
- Documented API and business process


GET IN TOUCH                                    ← --font-body, --color-link
```

### Approach (approach.html)

```
HOME

MY APPROACH                                     ← --font-display

1. I take creative work into a structured system, utilizing both spectrum of design discovery and engineering mindset. - Turns creativity structured.
I work with process and frameworks. everything even non-coding is verifiable, trackable, and valuable. Also, no unecessary/repetitive works.
2. To be Minimal is be powerful. A good user manual is no need for user manual. A good code documentation is no need for code documentation.
3. Teach a man how to fish instead of giving them fish. I value coaching so much and I will make everyone’s encounter with me valuable. I believe that people have untapped potential and I apply it to both my internal team and customer(SMEs).
4. A fun and feel good work style, culture, environment is both good for now and sustainable for the future.

GET IN TOUCH
```

### Interests (interests.html)

```
HOME

INTERESTS                                       ← --font-display

This is gonna be long.
- Tech: Mostly PC and server, I use both Mac/Windows/Linux and just recently started a home server to host my media services and POC projects.
- Audio: I enjoyed hi-fi audio since I got my first Shure SE215 and hooked to the quality of live concert flooding through my ears. Now I rotate HD6XX, Hifiman HE500, Etymotics ER4XR, Crinear Meta, Artti T10 Pro. I'm also objective+science first, so I still rock the JDS Labs O2/ODAC DIY. I also use KEF R100/Emotiva A100. Almost all of this is bought used. (which you'll see is a recurring theme)
- Mechanical Keyboards: Started with Anne Pro, then dove in to custom keyboard scene and now...bought and sold a lot. Currently mainly use HHKB pro 2, Kei (60% is goated), KFE CE (silver so good), MGA Standard (alice also goated), a lot of GMK/CRP keycaps.
- Classic Menswear: From London Brown loafer which I still wear after 10 years, I enjoy soft-tailoring, effortless styles, emphasize on proportions, and also value. My favorites brands are Ring Jacket, Spier & Mackay, Kamakura Shirts, Echizenya pants, and vintage stuffs. Some of my shoes are from Meermin, Carmina, John Lobb, Allen Edmonds. Most of them is used. My grail is Edward Green, but let's wait after I exited my startup first (no consultant money now)
- Anime: let's just say as of this writinng, I've watched 317 animes... some of my favourits: Ping Pong the animation, Attack on Titan, A Place Further than the Universe, Akira, Monogatari Series, Cowboy Bebop and a lot of KyotoAni works.
- Hiking and Camping: I just started getting into (ultralight) backpacking. I love walking through wilderness. Never felt more free. I love brands like Gnuhr and equipments from Gossamer Gear
- I also play tennis and golf. I think I'll play golf for my whole life (and still couldn't break 80s)
- Learning: learning new things, new skills, mostly in tech/science/engineering/design, but I never reject trying new things, life is short.

GET IN TOUCH
```

### Contact (contact.html)

```
HOME

CONTACT                                         ← --font-display

hello@goodkav.in                                 ← --font-body, --color-link
linkedin.com/in/kavins                               ← --font-body, --color-link

```

---

## 9. SEO & Meta

Each page gets its own `<title>` and meta description:

```html
<!-- Homepage -->
<title>Kavin S. — I help companies operate digitally</title>
<meta name="description" content="Personal site of Kavin S. Digital operations, ERP, and more.">

<!-- Subpages: "Kavin S. — [Page Name]" -->
<title>Kavin S. — My Work</title>
```

Shared across all pages:

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta charset="utf-8">

<!-- Open Graph -->
<meta property="og:title" content="Kavin S.">
<meta property="og:description" content="I help companies operate digitally.">
<meta property="og:image" content="https://goodkavin.github.io/og-image.png">
<meta property="og:url" content="https://goodkavin.github.io">
<meta property="og:type" content="website">

<!-- Twitter -->
<meta name="twitter:card" content="summary_large_image">
```

OG image: Simple dark card with name + tagline in Michroma. Generated as a static PNG.

---

## 10. Accessibility

- All text meets WCAG AA contrast on `#0e0e0e` background:
  - `#f0ede8` on `#0e0e0e` → ~16.5:1 ✓
  - `#888888` on `#0e0e0e` → ~5.2:1 ✓ (AA normal text)
  - `#6ba3be` on `#0e0e0e` → ~6.1:1 ✓ (AA normal text)
  - `#a0785a` on `#0e0e0e` → ~4.5:1 — borderline AA, may need slight lightening
- Semantic HTML: `<header>`, `<main>`, `<footer>`, `<nav>`
- All links have visible focus states using `outline` (not removed)
- `prefers-reduced-motion` media query respects system settings
- `lang="en"` on `<html>`
- No images = no alt text needed (except OG image)

---

## 11. Performance Targets

- **Total page weight:** < 150KB per page (HTML + CSS + fonts)
- **Requests:** ≤ 8 (HTML, CSS, ~6 font files)
- **Lighthouse:** 95+ across all categories
- **No JavaScript** = no JS parse/execute cost
- **Font loading:** `font-display: swap` with system font fallback stack
- **Fonts cached:** After first page load, CSS + fonts are cached for all subpages

---

## 12. Open Items

| Item | Status | Notes |
|---|---|---|
| Homepage intro copy (3–5 lines) | Owner to write | Placeholder in build -> done |
| Approach page copy | Owner to write | Placeholder in build |
| Interests page copy | Owner to write | Placeholder in build |
| Full project list (work page) | Content only | Structure supports adding more |
| Contact email | Owner to confirm | `hello@kavin.xyz` or other -> hello@goodkav.in |
| LinkedIn URL | Owner to provide | https://www.linkedin.com/in/kavins/ |
| OG image | Generate after build | Dark card with name in Michroma |
| Accent contrast verify | During build | `#a0785a` may need slight lightening for AA |
| Favicon | During build | Text-based SVG, "K" or "KS" in Michroma |

---

## 13. Decisions Log

| Decision | Options Considered | Chosen | Rationale |
|---|---|---|---|
| Site structure | Single page vs. multi-page | **Multi-page** (like keliz.xyz) | Rawer, each page focused, simple "home" nav |
| Layout width | 720px max vs. 960px vs. full-width | **Full-width** (like keliz.xyz) | Raw, no artificial container, text breathes |
| Display font | Geist, IBM Plex, Space Grotesk, Orbitron, Audiowide, Turret Road, others | **Michroma + 0.20em letter-spacing** | Wide geometric industrial feel, closest to NSX/Eurostile energy, free (OFL) |
| Body font | Times New Roman, Source Serif, Newsreader, Lora, Charter, IBM Plex Serif, Tinos | **Computer Modern Serif (CMU Serif)** | The LaTeX font — peak early IT/CS academia. Raw, geeky, readable. OFL free. |
| Label font | Space Mono, IBM Plex Mono, Courier | **JetBrains Mono** | Developer-native mono, clean, functional. Catalog/gnuhr.com energy. OFL free. |
| Nav style | Sticky bar, hamburger, link list | **"home" link only** (like keliz.xyz) | Minimal, raw, each page is its own destination |
| Accent color | Silver (#c0c0c0), blue, olive, none | **Warm brown (#a0785a) + cool blue (#6ba3be)** | Brown for project links (organic/industrial), blue for nav (keliz.xyz influence) |
| Framework | Astro, Hugo, Next.js, plain HTML | **Plain HTML + CSS** | Zero dependencies, raw, geeky, honest. No build step. |
| Heading case | Lowercase (initial assumption), ALL CAPS | **ALL CAPS** | Owner confirmed: section headings, nav labels, and display text are ALL CAPS. Body copy uses normal sentence case. |

---

*Spec v3 complete. Review, adjust, approve — then we build.*
