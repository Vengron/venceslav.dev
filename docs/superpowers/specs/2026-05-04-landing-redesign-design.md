# Landing Page Redesign — Design Spec
**Date:** 2026-05-04  
**File:** `index.html` (static, pure HTML/CSS/JS — no build step)

---

## Overview

Full redesign of venceslav.tech. Same file, new visual identity and restructured page. Includes copy rewrite. Goal: industrial dark-slate aesthetic, minimalist, high information density. Drop from 11 sections to 6.

---

## Visual Identity

### Colour Palette

| Token | Value | Usage |
|---|---|---|
| `--bg` | `#1A2035` | Primary background (all sections) |
| `--bg-deep` | `#131929` | Alternating sections, card interiors |
| `--bg-card` | `#1F2740` | Card surface |
| `--red` | `#FF3333` | Sole accent — CTAs, eyebrows, highlights |
| `--red-dark` | `#CC1F1F` | Button hover state |
| `--white` | `#FFFFFF` | Primary text |
| `--muted` | `rgba(255,255,255,0.45)` | Body text, descriptions |
| `--faint` | `rgba(255,255,255,0.15)` | Secondary labels, chips |
| `--border` | `rgba(255,255,255,0.07)` | All dividers, card borders |
| `--grid` | `rgba(255,255,255,0.022)` | Subtle grid overlay texture |

No warm cream palette. No gold. Pure industrial.

### Typography

| Role | Font | Weight | Usage |
|---|---|---|---|
| Display / Headlines | Bebas Neue | 400 | Hero H1, section H2, card titles, stat numbers |
| UI / Body | Space Mono | 400 / 700 | All body text, nav, labels, buttons, chips |

Google Fonts load: `Bebas+Neue` + `Space+Mono:wght@400;700`

**Type scale:**
- Hero H1: `clamp(4rem, 8vw, 7rem)`, line-height 0.88, letter-spacing 0.03em
- Section H2: `clamp(2rem, 4vw, 3.2rem)`, Bebas, line-height 0.92
- Card title: `1.2–1.5rem`, Bebas
- Body: `0.9rem`, Space Mono, line-height 1.75
- Label/eyebrow: `0.65rem`, Space Mono, letter-spacing 0.2em, uppercase
- Button: `0.72rem`, Space Mono 700, letter-spacing 0.12em, uppercase

### Texture & Details

- **Grid overlay**: `background-image` of 22×22px cross-hatch lines at `--grid` opacity, applied to hero and contact sections
- **Red accent bar**: 2px `background: #FF3333` horizontal line used as section separator and card top-border on hover
- **Section rhythm**: All sections share `--bg`. Alt sections use `--bg-deep` for contrast. No light/cream sections — the design lives entirely in the dark palette.
- **Borders**: All card/grid borders at `--border`. No drop shadows — borders only.

### Interactions & Animation

- **Page load**: Staggered `fadeUp` on hero elements (eyebrow → H1 → sub → CTAs → metric strip), delays 0.05s apart
- **Scroll reveal**: `IntersectionObserver` triggers `fadeUp` for each section as it enters viewport (threshold 0.1, `animation-fill-mode: both`)
- **Nav**: Transparent on load, gains `background: rgba(26,32,53,0.92)` + `backdrop-filter: blur(16px)` + bottom border on scroll
- **Buttons**: `background` transition 0.2s, `translateY(-1px)` on hover
- **Cards**: Border brightens to `rgba(255,255,255,0.18)` on hover, `transition: border-color 0.25s`
- **Nav links**: Red underline `scaleX` from left on hover (same as current)
- **Contact channel rows**: `gap` expands on hover (same as current)

---

## Page Structure (6 sections)

### 1 · Hero

**Layout**: Full viewport height, centered content, fixed nav, grid overlay, metric strip pinned to bottom.

**Nav:**
- Logo: `V_CHUMCHAL` in Bebas Neue, links to `#`
- Links: Services · Proof · Pricing · Contact — Space Mono, 0.65rem, uppercase, muted
- CTA: `BOOK A CALL` — red filled button, Space Mono

**Hero content (centered, z-index above grid):**
- Eyebrow: `— EU AI EXPERT · BASED IN ASIA · MANUFACTURING-FIRST —` (Space Mono, tiny, red, centered, with em-dashes)
- H1 (Bebas Neue, massive, centered, 3 lines):
  ```
  REAL AI.
  REAL EXPERTISE.
  REAL RESULTS.
  ```
  "REAL RESULTS." in red.
- Sub (Space Mono, muted, centered, max-width 580px):  
  `"I lead an EU AI lab. I'm based in Asia. I show up at your factory."`
- Two CTAs side by side:
  - Primary: `BOOK FREE DISCOVERY CALL →` (red filled)
  - Secondary: `SEE SERVICES` (border only, white)

**Metric strip (full-width, bottom of hero, border-top):**  
4 items separated by vertical `--border` lines:
```
30+                    €4,500              5+ yr              EU AI Act
AI Projects / Year     Discovery Sprint    Applied AI          GDPR-Compliant
```
Numbers in Bebas Neue, labels in Space Mono 0.6rem muted.

---

### 2 · About

**Layout**: 2-column grid (text 3fr / photo 2fr), `--bg-deep` background.

**Text column:**
- Eyebrow: `ABOUT`
- H2 (Bebas): `FROM CNC MACHINIST TO AI LAB LEAD.`
- Bio (Space Mono, 3 tight paragraphs — rewritten for density):
  - P1: Who he is + current role (AI Lab Head, CXI/TU Liberec, 10–15 engineers, 30+ projects/year)
  - P2: Background and edge (shop floor → data engineering → ML research → lab lead + IPF Industry co-founder)
  - P3: The offer (fixed-price, skill transfer, EU credentials, Asia presence)
- 3 philosophy callouts as a horizontal strip below bio (no standalone section):
  ```
  🍞 Skills, Not Dependencies   🏭 Practitioner, Not Theorist   🌏 EU Discipline, Asia Proximity
  ```
  Each: icon + bold title + 1-line explanation. Space Mono 0.75rem. Separated by `--border` vertical lines.
- Credential chips below: `AI Lab Head · CXI / TU Liberec` · `Co-Founder · IPF Industry` · `MSc AI · Univ. Lübeck` · `EU AI Act / GDPR`

**Photo column:**
- `profile_foto.jpg`, full height, `object-fit: cover`, `filter: grayscale(20%) brightness(0.8)`
- Diagonal red overlay strip at bottom-left corner (decorative, `clip-path: polygon(...)`)
- Name + role bar overlaid at bottom: `VĚNCESLAV CHUMCHAL` / `AI Lab Head · EU · Based in Asia`

---

### 3 · Services

**Layout**: Section header row + 3-column card grid. `--bg` background.

**Section header (2-col: title left, sub right):**
- Eyebrow: `SERVICES`
- H2: `THREE NICHES. ONE PRACTITIONER.`
- Sub (right): "Every engagement is built around your processes, your codebase, your industry."

**3 service cards** (`--bg-card`, border `--border`):

Each card contains (top to bottom):
1. Background image (existing Unsplash URLs), 200px height, dark gradient overlay, service name overlaid in Bebas
2. Card body:
   - Number: `01` / `02` / `03` — Bebas 3rem, faded
   - Title (Bebas): Manufacturing / Coding / Productivity headline
   - "For": 1-line Space Mono italic muted — who this is for (replaces standalone Who It's For section)
   - Description: 2–3 tight sentences, outcome-first. Rewritten copy (see below)
   - Price anchor: `From €25,000` / `From €4,500` / `From €3,500` — Bebas, red
   - Chip tags (same as current, but trimmed to 4 max)

**Rewritten card copy:**

*Manufacturing:*  
"Predictive maintenance, computer vision QC, and Industry 4.0 readiness — deployed on your factory floor. One electronics-sector pilot cut incoming inspection labor by 60% in 8 weeks."  
*For: Manufacturing SMEs, operations leads, plant managers.*

*Coding:*  
"Take your team from prompting to engineering. Claude Code, agentic workflows, and the discipline that makes AI-generated code production-safe. Teams reach confident autonomous deployment within 2 days."  
*For: Software teams, CTOs, dev leads.*

*Productivity:*  
"A practical audit of what's worth automating — then the skills to keep optimising independently. Most audits surface 3–5 automations saving 2+ hours per person per week."  
*For: Knowledge workers, founders, operations teams.*

---

### 4 · Proof

**Layout**: Two-part section, `--bg-deep`. Top: outcome cards. Divider. Bottom: credential grid.

**Top — Outcomes:**
- Eyebrow: `OUTCOMES`
- H2: `WHAT THIS LOOKS LIKE IN PRACTICE.`
- 3 outcome cards in grid (same content as current Results section, rewritten tighter):
  - Tag (industry + type)
  - Bold result headline
  - 2-sentence description (no "Engagement type:" label — fold into description)

**Divider**: full-width 1px `--border` line with `CREDENTIALS` label centered on it (like a chapter break).

**Bottom — Credentials:**
- 5 credential cards in a 3-column grid (`grid-template-columns: repeat(3, 1fr)`; items 4–5 fill second row left-aligned):
  - Tag (role category)
  - Title (Bebas)
  - Sub (Space Mono, muted, 1–2 lines)
  - Year (red, Space Mono)
- Same 5 credentials as current (Current Role, Co-Founder, Education, Research, EU Grants/Certs)

---

### 5 · Pricing

**Layout**: Section header + 3-column card grid + footnote. `--bg` background.

**Section header:**
- Eyebrow: `ENGAGEMENTS`
- H2: `FIXED SCOPE. PREDICTABLE COST.`
- Sub: "Fixed-price packages. All rates in EUR. On-site across Asia included."

**3 pricing cards** (same tier structure as current — Manufacturing / Discovery Sprint / Workshops):
- Featured card (Discovery Sprint): `--red` background
- Each card includes:
  - Tier name (Space Mono, uppercase, muted)
  - Price (Bebas, large)
  - Period/scope (Space Mono, small, muted)
  - Description (2 sentences max — rewritten)
  - **"How it works" note** (2-line embedded process, replaces standalone Process section):
    e.g., `01 → Free 20-min discovery call  02 → Scoped Sprint or Workshop  03 → You own the result`
  - Feature list (checkmarks, 4–5 items)
  - CTA button

**Below grid:**  
`Quarterly retainers from €12,000. Day rates on request. Travel billed at cost.` (Space Mono, muted, centered)

**FAQ (2 items only, slim accordion below pricing):**  
Keep only the 2 highest-signal questions:
1. "Are you actually available on-site next week?" 
2. "We tried AI tools before and they didn't stick."  
Cut: messy data question, post-engagement question (answered in pricing cards).

---

### 6 · Contact

**Layout**: 2-column (channels left / booking card right). `--bg-deep`. Grid overlay.

**Left — Channels:**
- Eyebrow: `CONTACT`
- H2: `READY TO START? LET'S TALK.`
- Sub: "I reply within 24 hours. Based in Asia — Mon–Fri."
- 3 channel rows (same as current): Email · WhatsApp · LinkedIn
  - Hover: icon fills red, row gap expands

**Right — Booking card** (`--bg-card`, border `--border`):
- Italic serif-style headline (use Space Mono italic): *"Not sure where to start? The first call is free."*
- Body: brief description of Discovery Sprint + 90-day credit
- CTA: `BOOK DISCOVERY CALL →` (red button, full width)
- Timezone note: `Based in Asia · Mon–Fri · On-site visits across the region`

---

## Copy Rewrite Principles

1. **Headline-first**: Every section H2 is an all-caps Bebas statement. Short. Punchy. No subordinate clauses.
2. **Outcome-first descriptions**: Lead every service/card description with the measured result, then what produces it.
3. **Cut hedging**: Remove "I work at the intersection of..." style phrasing. Replace with direct statements.
4. **Tighten bio**: Current bio is 4 paragraphs. Target: 3 tight paragraphs, ~40 words each.
5. **Numbers always visible**: Any stat (60%, 8 weeks, 30+, €4,500) stays in the first sentence, not buried.

---

## Navigation

- **Desktop**: Fixed top nav with logo + links + CTA. 7 links reduced to 4: Services · Proof · Pricing · Contact.
- **Mobile**: Hamburger → full-screen overlay (same pattern as current). Nav links in Bebas Neue, large.
- **Scroll behaviour**: Nav background appears on scroll (same as current JS).

---

## Responsive Breakpoints

| Breakpoint | Changes |
|---|---|
| `> 960px` | Full desktop layout |
| `≤ 960px` | Nav collapses to hamburger; hero metric strip wraps to 2×2 grid; all 2-col grids → 1-col; service/pricing/credential grids → 1-col |
| `≤ 480px` | Hero H1 reduces further via `clamp`; metric strip → 2-col; philosophy callouts → stacked |

---

## What's Removed

| Removed | Disposition |
|---|---|
| Philosophy section (standalone) | Folded into About as 3-item inline strip |
| Who It's For section | "For: X" line on each service card |
| Process section | "How it works" 3-step note embedded in each pricing card |
| Not For section | Cut entirely |
| FAQ (4 items) | 2 items kept as slim accordion below Pricing |
| Results section (standalone) | Top half of merged Proof section |
| Credentials section (standalone) | Bottom half of merged Proof section |

---

## Files Affected

- `index.html` — full rewrite (only file; no external CSS or JS files)
- `profile_foto.jpg` — referenced as-is, no change
- `favicon.svg` — unchanged

All meta tags, JSON-LD structured data, Vercel Analytics/Speed Insights scripts, and canonical URL carry over unchanged from the current file.
