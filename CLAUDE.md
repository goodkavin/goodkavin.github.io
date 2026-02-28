# CLAUDE.md — goodkavin.github.io

## What this is
Personal website rebuild. Plain HTML + CSS, GitHub Pages, zero JS. Full spec: `SPEC.md`.

## Method
SDD — spec before code. Get confirmation at each step before building or making changes.

## Local dev folder
`_dev/` — gitignored. Holds test/scratch files (font-test.html, heading-test.html, skill files, eval output). Don't commit or clean up without checking.

## Key decisions (quick ref)
- **Fonts:** Michroma (display, 0.20em letter-spacing) + CMU Serif (body) + JetBrains Mono (labels)
- **Colors:** `#0e0e0e` bg · `#f0ede8` text · `#6ba3be` nav links · `#a0785a` accent
- **Layout:** Full-width, no max-width container, horizontal padding via `clamp()`
- **Structure:** Multi-page (index, work, approach, interests, contact)
- **Nav:** "HOME" link top-left only — no nav bar

## Conventions to remember
- **Headings/labels → ALL CAPS** (`MY WORK`, `CONTACT`, `KAVIN S.`). Not title case, not lowercase.
- **Body copy → normal sentence case** with proper punctuation. Never all lowercase.
- **Tagline stays as-is:** "I help companies operate digitally."
- Links: blue (`--color-link`) for nav, brown (`--color-accent`) for project/external

## Corrections log
| My mistake | Correct behaviour |
|---|---|
| Wrote body copy in all lowercase | Body is normal sentence case — ALL CAPS is for headings only |

## Skills
- `go-direct` — for writing homepage intro, approach/interests copy, LinkedIn, bios. Installed from `_dev/go-direct.skill`.
