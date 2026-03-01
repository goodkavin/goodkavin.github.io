# Personal Website — Design Specification

**Repo:** `goodkavin.github.io` | **Updated:** 2026-03-01 | **Status:** Live

---

## 1. Goal

A minimal, warm-gray personal site. Communicates who I am, what I do, what I've built, and how to reach me. Fast to parse. Honest. Tasteful. No noise.

---

## 2. Design Principles

| Preferred | Over |
|---|---|
| Easy to get the point | Long text / noise |
| Minimal | Maximal |
| Raw & honest | Fake |
| Good structure | Unstructured |
| Tasteful | Normal |

---

## 3. Aesthetic Direction

Industrial-functional with geeky undertones. Not cold/corporate, not creative agency, not developer blog. A person who cares about craft, function, and taste. Confident without performing.

Typography is the primary design element. The font pairing does all the personality work.

---

## 4. Tech Stack

| Layer | Choice |
|---|---|
| Framework | Plain HTML + CSS — no JS, no build step |
| Styling | Single `style.css` with CSS custom properties |
| Fonts | Self-hosted woff2 |
| Deploy | Push to `main` → GitHub Pages |

---

## 5. File Structure

```
goodkavin.github.io/
├── index.html
├── work.html
├── approach.html
├── interests.html
├── contact.html
├── style.css
├── fonts/
│   ├── Michroma-Regular.woff2
│   └── GeistMono-Regular.woff2
├── assets/
│   └── good.jpg             ← profile photo
├── favicon.gif
├── SPEC.md
└── CLAUDE.md
```

---

## 6. Visual Specification

### Colors

```css
--color-bg:     #c8c5c0;   /* warm gray */
--color-text-1: #0e0e0e;   /* near-black */
--color-text-2: #555555;   /* secondary / meta */
--color-link:   #2d6b8a;   /* blue — all links */
--color-accent: #7a5c42;   /* brown — hover state */
```

Single link color (`--color-link`) for all links. Hover transitions to `--color-accent`.

### Typography

Two fonts only:

| Role | Font | Usage |
|---|---|---|
| **Display** | Michroma (400, 0.20em letter-spacing) | Name, page titles, nav links, CTAs |
| **Body** | Geist Mono (400) | All body text, intro paragraph |

```css
--ls-display: 0.20em;   /* name, page titles */
--ls-tagline: 0.12em;   /* tagline */
--ls-nav:     0.15em;   /* nav links, CTAs */

--michroma-stroke: 0.8px;   /* -webkit-text-stroke for faux-bold */
```

**Fluid type scale:**

```css
--text-xs:   clamp(0.7rem,  0.65rem + 0.25vw, 0.8rem);
--text-sm:   clamp(0.8rem,  0.75rem + 0.25vw, 0.9rem);
--text-base: clamp(0.85rem, 0.8rem  + 0.25vw, 0.95rem);
--text-lg:   clamp(1.1rem,  1rem    + 0.5vw,  1.5rem);
--text-xl:   clamp(1.5rem,  1.2rem  + 1.2vw,  2.5rem);
```

### Layout

```css
--padding-x:   clamp(1rem, 3vw, 2rem);
--section-gap: clamp(1rem, 2.5vw, 1.75rem);
```

Full-width, no max-width container. Left-aligned. Linear reading flow. Body text blocks capped at `max-width: 60ch`.

### Navigation

- All pages: "HOME" link top-left (Michroma, `--text-sm`, `--color-link`)
- Homepage has a link list to subpages
- No nav bar, no hamburger

### Copy conventions

- **Headings / nav labels / CTAs → ALL CAPS** (`MY WORKS`, `CONTACT`, `GET IN TOUCH`)
- **Body copy → normal sentence case**
- **Numbered lists → plain `[n]` prefix** as text (not `<ol>` or CSS counters), matching keliz.xyz

---

## 7. Page Specs

### Homepage (index.html)

```
HOME

GOOD KAVIN S.                       ← Michroma, --text-xl
I help companies operate digitally. ← Michroma, --text-lg, --color-text-2

[profile photo]

Hi, I'm Good. ... I co-founded [MineERP](link): ERP software ...
                                    ← Geist Mono, MineERP is inline link

MY APPROACH                         ← Michroma, --text-sm
MY WORKS
INTERESTS
CONTACT

MORE PROFESSIONAL VERSION           ← Michroma, --text-sm, links to LinkedIn
```

### Work (work.html)

```
HOME

MY WORKS

[2022–PRESENT] COO, NPR Digital Partner (MineERP)
– bullet
– bullet

[2019–2022] Data Engineer, Accenture
– bullet

[2018] Software Engineer Intern, Digital Ventures (SCB 10X)
– bullet

GET IN TOUCH
```

Work entry header format: `[YEAR–YEAR] Title, Company` as a plain `<p>`. Bullets use CSS `–` prefix (not `<ul>` markers).

### Approach (approach.html)

```
HOME

MY APPROACH

[1] Creativity without structure is chaos...
[2] Minimal is powerful...
[3] Teach a man to fish...
[4] A fun, feel-good work style...

GET IN TOUCH
```

### Interests (interests.html)

```
HOME

INTERESTS

This is gonna be long.

[1] Tech: ...
[2] Audio: ...
[3] Mechanical Keyboards: ...
[4] Classic Menswear: ...
[5] Anime: ...
[6] Hiking and Camping: ...
[7] Tennis and golf...
[8] Learning: ...

GET IN TOUCH
```

### Contact (contact.html)

```
HOME

CONTACT

hello@goodkav.in
linkedin.com/in/kavins
```

---

## 8. Decisions Log

| Decision | Chosen | Rationale |
|---|---|---|
| Framework | Plain HTML + CSS | Zero dependencies, no build step, raw |
| Structure | Multi-page | Like keliz.xyz — each page focused |
| Layout | Full-width | No artificial container |
| Display font | Michroma + 0.20em | Wide geometric industrial feel |
| Body font | Geist Mono | Clean monospace; replaced CMU Serif after testing |
| Label font | None (dropped) | Geist Mono covers all body roles; three fonts was one too many |
| Background | Warm gray #c8c5c0 | Black-on-gray > white-on-dark for this feel |
| Link colors | Single blue (#2d6b8a) | Simpler than two-color system; brown accent kept for hover |
| Nav list | No MINEERP entry | MineERP linked inline in intro text instead |
| LinkedIn | Single "MORE PROFESSIONAL VERSION" link | Replaces two-line label + link pattern |
| Faux bold | `-webkit-text-stroke: 0.8px` | Michroma has no bold weight |
| List format | `[n]` plain text prefix | Matches keliz.xyz raw aesthetic |
