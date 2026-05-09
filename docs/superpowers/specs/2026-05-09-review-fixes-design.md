# Design Spec: Website Review Fixes
**Date:** 2026-05-09  
**Source:** `venceslav-tech-review.md`  
**Scope:** All 11 remaining issues from the review (4.2 already fixed)

---

## 1. Typography System (1.1)

Add DM Sans as a second font for body prose. Space Mono is retained for all short callout text, labels, nav, buttons, and mono-feel elements.

**Implementation:**
- Add DM Sans to the existing Google Fonts `<link>`: `family=DM+Sans:wght@400;500`
- Add CSS token: `--body: 'DM Sans', sans-serif;`
- Add `.prose` utility class: `font-family: var(--body); line-height: 1.8;`
- Apply `.prose` to:
  - About section: the three bio `<p>` elements
  - Services section: each card's description `<p>`
  - Pricing section: each card's description `<p>`
  - FAQ section: all answer `<p>` elements

Everything else (headings, nav, metric strip, credential tags, "How it works" lists, buttons, footer) stays Space Mono.

---

## 2. Pricing Card Fixes (1.2, 1.3, 3.1)

**1.2 — Trim card descriptions:**  
Each pricing card description trimmed to 2 sentences maximum. Verbose detail removed; the copy should be punchy enough to push the reader to book a call, not inform them of everything.

**1.3 — Sublist contrast:**  
"How it Works" sublist boxes inside pricing cards: increase background lightness by ~12% (e.g. `#2A3350` → `#323D5E` or equivalent). Text color on non-highlighted cards bumped to `rgba(255,255,255,0.85)` minimum.

**3.1 — Remove retainer line:**  
Delete the fine-print italic line "Quarterly retainers from €12,000…" entirely. Rationale: retainers contradict the brand positioning — *"Every engagement ends with your team owning the capability. I don't create dependencies."* No replacement needed.

---

## 3. Hero & Outcomes Hierarchy (2.1, 2.2)

**2.1 — Hero subline:**  
"I lead an EU AI lab. I'm based in Asia. I show up at your factory." is the most differentiating line on the page.
- Font size: increase by ~20% (e.g. `1rem` → `1.2rem` or `clamp`-adjusted)
- Add `margin-block: 1.5rem` around the line to give it breathing room between the H1 and the CTA buttons

**2.2 — Outcomes metrics:**  
Treat the key metric in each outcome card as a large stat, not a card header.
- Pull the percentage/number out as a display-size element (e.g. `font-family: var(--display); font-size: clamp(2.5rem, 6vw, 4rem); color: var(--red);`)
- Context line (e.g. "reduction in incoming inspection labor") sits below in `.prose` at normal size
- Cards get more vertical padding to let the numbers breathe

---

## 4. FAQ Expansion (2.3)

Add 3 new FAQ items below the existing 2. Answers to be written inline during implementation based on Venceslav's actual positioning. Placeholder answers provided here as starting points:

**Q: What industries do you work with beyond manufacturing?**  
A: Focus is on manufacturing, but the same approach — fixed-price pilots, capability transfer — applies to logistics, agri-tech, and industrial services. If your business has repetitive physical processes or quality control challenges, it's worth a conversation.

**Q: What countries in Asia do you cover for on-site visits? Do you work with large enterprises or SMEs?**  
A: Currently covering Southeast Asia with regular presence in [countries TBD — Venceslav to fill]. Both enterprise divisions and mid-sized manufacturers are in scope; the fixed-price model works at either scale.

**Q: What happens if the pilot doesn't deliver results?**  
A: Every engagement is scoped to a specific, measurable outcome before we start. If the agreed metric isn't hit, we extend the engagement at no extra cost until it is. The fixed price means the risk is mine, not yours.

> **Note:** Venceslav should review and rewrite the FAQ answers in his own voice before shipping.

Remove excess whitespace above/below the FAQ section (reduce `padding-block` by ~30%).

---

## 5. Contact Section (3.2)

**3.2 — Timezone duplication:**  
Remove the timezone mention from the left-column body text. Keep it only in the small print below the CTA button on the right, where it functions as a reassurance next to the call-to-action.

---

## 6. Services Section (3.3)

**3.3 — Coding card image:**  
Replace the generic AI brain circuit graphic with a user-supplied real photo/screenshot.
- Expected filename: `coding-screenshot.jpg` (in project root, alongside `profile_foto.jpg`)
- Update the `<img src="...">` in the Coding service card to point to this file
- Alt text: `"Claude Code session / AI coding project"`
- User is responsible for providing the asset before deploying

---

## 7. Credentials (3.4)

**3.4 — MSc end date:**  
Update the MSc credential entry from `"March 2026 –"` to `"March 2026 – Expected 2028"`.

---

## 8. Email Address (4.1)

Replace all instances of `venceslav.ch@outlook.com` with `venceslav.chumchal@gmail.com`.

Locations:
- Contact section (visible link/button)
- Footer
- `<script type="application/ld+json">` structured data block

---

## Summary of Changes

| # | Change | File | Effort |
|---|--------|------|--------|
| 1.1 | Add DM Sans + `.prose` class | `index.html` | Medium |
| 1.2 | Trim pricing card copy | `index.html` | Low |
| 1.3 | Lift sublist box contrast | `index.html` | Low |
| 2.1 | Hero subline size + spacing | `index.html` | Low |
| 2.2 | Outcomes metrics as large stats | `index.html` | Medium |
| 2.3 | Add 3 FAQ items, reduce dead space | `index.html` | Low |
| 3.1 | Delete retainer fine print | `index.html` | Low |
| 3.2 | Remove duplicate timezone | `index.html` | Low |
| 3.3 | Wire coding-screenshot.jpg | `index.html` | Low |
| 3.4 | Add MSc expected end date | `index.html` | Low |
| 4.1 | Swap email to gmail | `index.html` | Low |

All changes are in `index.html` only. No new files except the user-supplied `coding-screenshot.jpg`.
