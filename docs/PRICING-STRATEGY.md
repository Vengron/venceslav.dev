# Pricing & Positioning Strategy — Decision Record

**Source:** `reports/Pricing Research Report.pdf` (April 2026, local-only — `reports/` is gitignored)
**Implemented in:** commit `0c3730a` on `dev` (April 2026)

This document distills the *why* behind the current pricing and positioning of [`index.html`](../index.html) so future edits don't accidentally undo decisions that were made deliberately. The full source report is the authoritative reference; this file is a quick-reference summary.

---

## Core Strategic Frame

The website targets **upper-tier small and medium-sized SMEs in ASEAN** (USD 5M-50M revenue) — they have AI budgets of USD 50K-250K/year but cannot afford Big-4/McKinsey rates. Sweet spot: medium-sized clients in **Vietnam, Indonesia, Thailand**.

The positioning is **"EU AI expert physically based in ASEAN."** This is the unique combination:
- **EU credibility** — Czech AI Lab Lead, EU AI Act / GDPR-compliant delivery, 2-3× premium over local consultants is justified
- **In-region physical presence** — undercuts EU-based competitors who must fly in; on-site manufacturing work is feasible same-week
- **Manufacturing-first specialization** — the report's strongest pricing lever; CNC-to-AI background is a rare differentiator (3-5× local rate premium)

A network of partner researchers/developers gets pulled in for larger engagements. This is mentioned explicitly so the consultant scales beyond personal hours.

---

## Pricing Model Decisions

### Why not hourly billing as primary model

ASEAN SME clients perceive hourly billing as **risky and uncapped**. It also caps the consultant's earnings and undermines EU-expert positioning. The report is explicit: *"Avoid hourly billing as primary model."*

The site therefore leads with **fixed-price productized engagements**, with day rates and hourly listed only inside card descriptions, never as headline prices.

### Why these specific rates (Recommended trajectory)

| Service line | Day rate | Entry product | Retainer |
|---|---|---|---|
| AI for Manufacturing | from €1,500 | Pilot from €25,000 | from €5,000/mo |
| AI for Coding | from €1,000 | Workshop from €6,000 | from €4,500/mo |
| AI for Productivity | from €800 | Workshop from €3,500 | from €2,500/mo |

**Floors (never display publicly):** Mfg €1,100/day, Coding €800/day, Productivity €650/day. The displayed "from" prices already include 15-25% concession room — ASEAN business culture *expects* price negotiation, so the published rate must absorb at least one concession round without falling through the floor.

**Anchor reasoning:** these rates are 2-3× local ASEAN consulting rates (the EU-expert premium) but well below Singapore/Big-4 firms (€2,500-3,500/day) — affordable for the target SMEs. The report identified the previous rates (€175/€120/€85 per session = ~€80/€65/€50/hr) as **dramatically underpriced even for ASEAN SMEs**, leaving €40K-€80K/year of revenue on the table at typical utilization.

### Three productized starter bundles

The report's specific engagements that the website embeds:

1. **AI Discovery Sprint — €4,500, 3 days.** *Front-door product.* Deliverable: 12-page AI opportunity report + executive presentation. Fee credited toward any follow-on engagement within 90 days. This bypasses the "give me a free pilot" trap (face-culture risk) while still being affordable for SMEs.
2. **Manufacturing Quick-Win Pilot — €18,000-25,000 fixed, 6-12 weeks.** Deliverable: one production-ready predictive-maintenance or quality-control model on a single line/machine.
3. **AI Adoption Quarterly Retainer — €12,000 (3 months).** 2 on-site visits + 4 hrs/week consulting + final transformation roadmap.

### Why no "20% introductory discount"

The previous site advertised a 20% intro discount. **Removed deliberately.** In face-conscious ASEAN markets, advertised discounts permanently anchor perceived value low and undermine premium positioning. If a discount is needed for the first 2-3 clients per country, frame it as *"ASEAN market entry rate"* or *"founding client rate"* — never as a discount.

### Free vs. paid entry

- **Free 20-min discovery call:** kept. Low-friction qualifier, zero-commitment.
- **€4,500 Discovery Sprint:** added as the first *paid* step. The report is explicit: *"Free work permanently devalues the relationship in face cultures. Offer paid €4,500 Discovery Sprint instead."*
- The website makes clear that the Sprint is the typical step after the free call.

---

## Cultural & Sales Norms (Why proposals work the way they do)

These aren't reflected on the public site (they belong in proposals/quotes) but they shape *how* the site is written:

- **Quote 15-25% above floor.** Negotiation is expected; clients use foreigners' time pressure to extract concessions.
- **"We will study it"** is often a polite *no*, especially in Thailand (kreng jai / saving face). Watch for indirect language.
- **Indonesia requires a perantara (intermediary).** A 2025 Springer study found backchannel agents are essential to progress to face-to-face negotiation. Budget 10-20% commission for a local agent.
- **Thailand: hierarchy is paramount.** Pitch and negotiate at the appropriate seniority level — pitching the CFO directly may bypass mid-level gatekeepers and stall the deal.
- **Vietnam: personal trust > company trust.** Relationships transfer poorly between people, so the consultant himself is the brand, not the firm.
- **Sales cycles are slow.** Indonesia 6-12 months is normal; Thailand and Vietnam faster but still 4-8 weeks for workshops, 4-8 months for implementation.
- **Quote in EUR, not local currency.** IDR, VND, THB are all volatile; FX risk should not sit with the consultant. Build 3-5% FX buffer into multi-month contracts.
- **Withholding tax:** Thailand, Indonesia, Vietnam all withhold 5-20% on foreign service fees unless covered by EU double-tax treaties. Czech Republic has bilateral treaties with all three — invoice via Czech entity to claim relief.
- **Travel costs:** billed at cost or as a fixed per-trip allowance (typical: €1,500-2,500 per on-site visit including flights). The website note *"travel beyond standard on-site visits billed at cost"* covers this without exposing detail.

---

## Phased Strategy (Where rates go from here)

The report defines a 3-phase trajectory. The current site implements **Phase 1-2**:

- **Phase 1 (Months 1-6):** Lead with workshops, not implementation. Workshops have shorter sales cycles (4-8 weeks vs. 4-8 months) and serve as paid marketing. Price the first 2-3 engagements per country at ~75% of full rate as "founding client rate."
- **Phase 2 (Months 6-18):** Specialize loudly — *"AI for CNC manufacturing in Southeast Asia"* is dramatically more powerful than *"AI consultant."* Move 60% of revenue to retainer/project-based pricing. Increase rates by 15-25% on each new client cohort until pushback emerges, then hold.
- **Phase 3 (18+ months):** Introduce productized offerings ("PdM-in-30-Days™" at fixed €25,000) to scale beyond hours. Begin value-based pricing (10-25% of measurable annual savings) only with clients who already have ROI data from prior engagements. Selectively raise rates to €220/hr / €1,800/day for manufacturing — the practical EU-import ceiling for ASEAN SMEs (above this, clients prefer Singapore/Hong Kong firms).

---

## Risks & Mitigations Already Built In

| Risk | How the site handles it |
|---|---|
| Client cites local $25/hr rate | Site does not display hourly headline; positions as EU expert; references EU AI Act / GDPR compliance |
| Local AI agencies undercut on price | Site competes on outcomes, EU regulatory expertise, IP transfer — never on price |
| Long sales cycles erode hourly margins | Productized fixed-price packages (Discovery Sprint, Pilot) bypass hourly negotiation |
| EU rates pressure ("you charge less in Europe") | Old €80/hr rate is removed from public site; framed as historic CZ domestic rate if asked |
| Client requests free pilot to "prove value" | €4,500 Discovery Sprint is offered explicitly as the first paid step |
| Currency depreciation (IDR, VND) | All rates quoted in EUR; site does not list local-currency equivalents |

---

## What Is Deliberately NOT On the Site

- Country-specific (Vietnam/Thailand/Indonesia) callouts — the user preferred a more inclusive "based in Asia" framing that doesn't lock out other markets (Singapore, Malaysia, Philippines, etc.)
- Hourly rates as headline numbers — only mentioned inside card descriptions
- Withholding tax / EUR-quoting / travel cost detail — operational details belong in proposals, not the public site
- Discount language ("introductory", "limited time", etc.)
- The €18,000 Manufacturing Quick-Win price — replaced with "From €25,000" on the public card so clients ask before assuming the floor; the €18,000 floor is the negotiation room

---

## Year-1 Targets

Per the Recommended trajectory: **€220K-€350K ARR** from 4-6 SME clients across 3 countries. The Conservative trajectory (€120K-€180K) is the floor; the Aggressive trajectory (€350K-€500K) is what selective rate increases in Phase 2 can unlock.

---

## How To Use This Document

- Before changing pricing, positioning, or service-line copy on `index.html`: re-read the relevant section here to understand the constraint.
- If a decision was made for a reason listed here, prefer to adjust within the constraint rather than reverting it.
- If the constraint no longer applies (e.g., the user moves out of ASEAN, or starts targeting a different SME tier), update this file *and* the site together.
- The full PDF report is the authoritative source for any detail not captured here.
