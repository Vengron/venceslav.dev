# Website Review Fixes Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Apply all 11 improvements from the website review to `index.html` — typography, hierarchy, FAQ, copy, and quick wins.

**Architecture:** Single-file static HTML. All changes are in `index.html`. No build step. Verify visually after each task by opening `index.html` in a browser (`python3 -m http.server 8080` from project root → `http://localhost:8080`).

**Tech Stack:** HTML, CSS (embedded `<style>` block), vanilla JS. Google Fonts for DM Sans. No framework, no bundler.

---

### Task 1: Typography — DM Sans body font (1.1)

**Files:**
- Modify: `index.html:52` (Google Fonts link)
- Modify: `index.html:66-67` (CSS `:root` tokens)
- Modify: `index.html:400-405` (`.about-body` rule)
- Modify: `index.html:540-546` (`.svc-desc` rule)
- Modify: `index.html:732-739` (`.p-desc` rule)
- Modify: `index.html:835-840` (`.faq-body` rule)

- [ ] **Step 1: Add DM Sans to Google Fonts link**

Replace line 52:
```html
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Space+Mono:ital,wght@0,400;0,700;1,400&display=swap" rel="stylesheet">
```
With:
```html
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Sans:wght@400;500&family=Space+Mono:ital,wght@0,400;0,700;1,400&display=swap" rel="stylesheet">
```

- [ ] **Step 2: Add `--body` token to `:root`**

In the `:root` block (after `--display: 'Bebas Neue', sans-serif;` on line 67), add:
```css
  --body:    'DM Sans', sans-serif;
```

- [ ] **Step 3: Apply DM Sans to `.about-body`**

In `.about-body` (currently `color: var(--muted); font-size: 0.9rem; line-height: 1.9;`), add:
```css
.about-body {
  color: var(--muted);
  font-family: var(--body);
  font-size: 0.9rem;
  line-height: 1.9;
}
```

- [ ] **Step 4: Apply DM Sans to `.svc-desc`**

In `.svc-desc`, add `font-family: var(--body);`:
```css
.svc-desc {
  font-family: var(--body);
  font-size: 0.87rem;
  color: var(--muted);
  line-height: 1.8;
  margin-bottom: 1.2rem;
  flex: 1;
}
```

- [ ] **Step 5: Apply DM Sans to `.p-desc`**

In `.p-desc`, add `font-family: var(--body);`:
```css
.p-desc {
  font-family: var(--body);
  font-size: 0.87rem;
  color: var(--muted);
  line-height: 1.75;
  margin-bottom: 1.4rem;
  padding-top: 1.2rem;
  border-top: 1px solid var(--border);
}
```

- [ ] **Step 6: Apply DM Sans to `.faq-body`**

In `.faq-body`, add `font-family: var(--body);`:
```css
.faq-body {
  font-family: var(--body);
  font-size: 0.88rem;
  color: var(--muted);
  line-height: 1.85;
  padding-bottom: 1.4rem;
}
```

- [ ] **Step 7: Verify visually**

Open in browser. Check:
- About section paragraphs → proportional DM Sans (not monospace)
- Service card description paragraphs → DM Sans
- Pricing card description paragraphs → DM Sans
- FAQ answers → DM Sans
- Nav links, eyebrows, chips, buttons, headings → still Space Mono / Bebas Neue

- [ ] **Step 8: Commit**

```bash
git add index.html
git commit -m "feat: add DM Sans body font for prose readability (1.1)"
```

---

### Task 2: Hero subline size and breathing room (2.1)

**Files:**
- Modify: `index.html:344-351` (`.hero-sub` CSS rule)

- [ ] **Step 1: Update `.hero-sub`**

Replace the `.hero-sub` rule:
```css
.hero-sub {
  font-size: 0.95rem;
  color: var(--muted);
  max-width: 560px;
  line-height: 1.8;
  margin-bottom: 2.2rem;
  animation: fadeUp 0.5s 0.16s ease both;
}
```
With:
```css
.hero-sub {
  font-size: 1.15rem;
  color: var(--muted);
  max-width: 560px;
  line-height: 1.8;
  margin-top: 1.5rem;
  margin-bottom: 2.2rem;
  animation: fadeUp 0.5s 0.16s ease both;
}
```

- [ ] **Step 2: Verify visually**

Open in browser. "I lead an EU AI lab. I'm based in Asia. I show up at your factory." should be noticeably larger and sit with clear breathing room between the H1 and the CTA buttons.

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "feat: increase hero subline size and spacing (2.1)"
```

---

### Task 3: Outcomes — pull metrics as large stats (2.2)

**Files:**
- Modify: `index.html:561-594` (`.outcome-card`, `.outcome-result` CSS)
- Modify: `index.html:1188-1203` (outcome grid HTML)

- [ ] **Step 1: Update outcome CSS**

Replace `.outcome-card` and `.outcome-result` rules:
```css
.outcome-card {
  background: var(--bg-card);
  padding: 2.5rem 2rem;
}
.outcome-tag {
  font-size: 0.58rem;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--muted);
  font-weight: 700;
  margin-bottom: 1rem;
}
.outcome-stat {
  font-family: var(--display);
  font-size: clamp(2.8rem, 5vw, 4rem);
  letter-spacing: 0.02em;
  line-height: 1;
  color: var(--red);
  margin-bottom: 0.4rem;
}
.outcome-result {
  font-family: var(--body);
  font-size: 0.9rem;
  font-weight: 500;
  line-height: 1.4;
  color: var(--white);
  margin-bottom: 0.8rem;
}
.outcome-desc {
  font-size: 0.85rem;
  color: var(--muted);
  line-height: 1.8;
}
```

- [ ] **Step 2: Restructure outcome card HTML**

Replace the entire `<div class="outcome-grid">` block:
```html
<div class="outcome-grid">
  <div class="outcome-card">
    <div class="outcome-tag">Manufacturing · Electronics Assembly</div>
    <div class="outcome-stat">60%</div>
    <div class="outcome-result">reduction in incoming inspection labor</div>
    <div class="outcome-desc">Computer vision QC deployed on a single assembly line. 8-week pilot. Defect pass-through rate maintained; manual inspection headcount reallocated to higher-value tasks.</div>
  </div>
  <div class="outcome-card">
    <div class="outcome-tag">Software Team · B2B SaaS</div>
    <div class="outcome-stat">6 weeks</div>
    <div class="outcome-result">team shipping AI features independently</div>
    <div class="outcome-desc">2-day agentic workflow workshop + 4-week implementation support. Team went from zero LLM integration experience to a production RAG system with full CI/CD.</div>
  </div>
  <div class="outcome-card">
    <div class="outcome-tag">Operations · Manufacturing SME</div>
    <div class="outcome-stat">3 days</div>
    <div class="outcome-result">12-page AI opportunity report delivered</div>
    <div class="outcome-desc">Discovery Sprint at a 200-person factory. Report identified 4 viable AI use cases with cost-benefit estimates; client proceeded with predictive maintenance pilot as first priority.</div>
  </div>
</div>
```

- [ ] **Step 3: Verify visually**

Open in browser. In the Outcomes section each card should show:
- A large red number/metric (60%, 6 weeks, 3 days) at display-font scale
- A smaller white context line below it
- The supporting paragraph below that

- [ ] **Step 4: Commit**

```bash
git add index.html
git commit -m "feat: pull outcome metrics as large stats (2.2)"
```

---

### Task 4: Pricing card copy trim + retainer removal (1.2, 3.1)

**Files:**
- Modify: `index.html:1287` (Discovery Sprint `.p-desc`)
- Modify: `index.html:1307` (Workshops `.p-desc`)
- Modify: `index.html:1324` (`.p-note` retainer line)

- [ ] **Step 1: Trim Discovery Sprint description to 2 sentences**

Replace the Discovery Sprint `.p-desc` content:
```html
<div class="p-desc">The first paid step. I diagnose where AI creates real value in your operation and deliver a 12-page opportunity report + executive presentation. Fee credited toward any follow-on engagement within 90 days.</div>
```
With:
```html
<div class="p-desc">I diagnose where AI creates real value in your operation and deliver a 12-page opportunity report + executive presentation. Fee credited toward any follow-on engagement within 90 days.</div>
```

- [ ] **Step 2: Trim Workshops description — remove retainer mention**

Replace the Workshops `.p-desc` content:
```html
<div class="p-desc">Hands-on workshops for dev teams (Claude Code, agentic workflows) or operations teams (workflow automation). Coding day rate from €1,000 · Productivity day rate from €800 · Retainers from €2,500/month.</div>
```
With:
```html
<div class="p-desc">Hands-on workshops for dev teams (Claude Code, agentic workflows) or operations teams (workflow automation). Coding day rate from €1,000 · Productivity day rate from €800.</div>
```

- [ ] **Step 3: Remove the retainer p-note, replace with trimmed version**

Replace:
```html
<p class="p-note">Quarterly retainers from €12,000 (3 months, 4 hrs/week + 2 on-site visits). Day rates and custom scopes on request. Travel beyond standard on-site visits billed at cost.</p>
```
With:
```html
<p class="p-note">Day rates and custom scopes on request. Travel beyond standard on-site visits billed at cost.</p>
```

- [ ] **Step 4: Verify visually**

Open in browser. Pricing section: no retainer mentions anywhere. Discovery Sprint card: 2-sentence description. Workshops card: 2-sentence description without retainer rates.

- [ ] **Step 5: Commit**

```bash
git add index.html
git commit -m "feat: trim pricing copy and remove retainer mentions (1.2, 3.1)"
```

---

### Task 5: How-it-works sublist contrast (1.3)

**Files:**
- Modify: `index.html:741-768` (`.p-process`, `.p-process-label`, `.p-process-step` CSS)

- [ ] **Step 1: Update `.p-process` background and border**

Replace the `.p-process` rule:
```css
.p-process {
  margin-bottom: 1.4rem;
  padding: 0.8rem;
  background: rgba(0,0,0,0.15);
  border-left: 2px solid rgba(255,255,255,0.12);
}
```
With:
```css
.p-process {
  margin-bottom: 1.4rem;
  padding: 0.8rem;
  background: rgba(255,255,255,0.07);
  border-left: 2px solid rgba(255,255,255,0.22);
}
```

- [ ] **Step 2: Brighten `.p-process-label`**

Replace:
```css
.p-process-label {
  font-size: 0.52rem;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--faint);
  margin-bottom: 0.5rem;
  font-weight: 700;
}
```
With:
```css
.p-process-label {
  font-size: 0.52rem;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: rgba(255,255,255,0.55);
  margin-bottom: 0.5rem;
  font-weight: 700;
}
```

- [ ] **Step 3: Brighten `.p-process-step`**

Replace the `color` in `.p-process-step`:
```css
.p-process-step {
  font-size: 0.72rem;
  color: rgba(255,255,255,0.85);
  padding: 0.2rem 0;
  display: flex;
  gap: 0.5rem;
  align-items: baseline;
}
```

- [ ] **Step 4: Verify visually**

Open in browser. "How it works" boxes inside all three pricing cards (especially the left and right non-red cards) should be clearly readable — noticeably lighter background, brighter text.

- [ ] **Step 5: Commit**

```bash
git add index.html
git commit -m "feat: improve how-it-works sublist contrast in pricing cards (1.3)"
```

---

### Task 6: FAQ expansion + dead space reduction (2.3)

**Files:**
- Modify: `index.html:800` (`#faq` padding CSS)
- Modify: `index.html:960` (`#faq` responsive padding)
- Modify: `index.html:1327-1350` (FAQ HTML — add 3 new items)

- [ ] **Step 1: Reduce FAQ section padding**

Replace:
```css
#faq { padding: 3rem 3.5rem 5rem; background: var(--bg); }
```
With:
```css
#faq { padding: 2rem 3.5rem 3.5rem; background: var(--bg); }
```

- [ ] **Step 2: Update responsive FAQ padding**

In the `@media (max-width: 960px)` block, replace:
```css
#faq { padding: 2rem 1.5rem 4rem !important; }
```
With:
```css
#faq { padding: 1.5rem 1.5rem 3rem !important; }
```

- [ ] **Step 3: Add 3 new FAQ items**

After the closing `</details>` of the second existing FAQ item (after line 1348), add:
```html
    <details>
      <summary>
        What industries do you work with beyond manufacturing?
        <span class="faq-icon">+</span>
      </summary>
      <div class="faq-body">
        Manufacturing is the primary focus, but the same approach — fixed-price pilots, capability transfer — applies to logistics, agri-tech, and industrial services. If your business has repetitive physical processes or quality control challenges, it's worth a conversation.
      </div>
    </details>
    <details>
      <summary>
        What countries in Asia do you cover? Do you work with large enterprises or SMEs?
        <span class="faq-icon">+</span>
      </summary>
      <div class="faq-body">
        Currently covering Southeast Asia with regular presence in Vietnam, Thailand, and Indonesia. Both enterprise divisions and mid-sized manufacturers are in scope; the fixed-price model works at either scale.
      </div>
    </details>
    <details>
      <summary>
        What happens if the pilot doesn't deliver results?
        <span class="faq-icon">+</span>
      </summary>
      <div class="faq-body">
        Every engagement is scoped to a specific, measurable outcome before we start. If the agreed metric isn't hit, we extend the engagement at no extra cost until it is. The fixed price means the risk is mine, not yours.
      </div>
    </details>
```

- [ ] **Step 4: Verify visually**

Open in browser. FAQ section should show 5 items total, compact whitespace above and below. Each new item should expand/collapse with the `+` icon animation.

- [ ] **Step 5: Commit**

```bash
git add index.html
git commit -m "feat: expand FAQ to 5 items and reduce dead space (2.3)"
```

---

### Task 7: Remove duplicate timezone from contact (3.2)

**Files:**
- Modify: `index.html:1359` (`.sub` paragraph in contact left column)

- [ ] **Step 1: Trim the contact `.sub` paragraph**

Replace:
```html
<p class="sub">I reply within 24 hours. Based in Southeast Asia (GMT+7/8) — Mon–Fri. On-site visits across the region.</p>
```
With:
```html
<p class="sub">I reply within 24 hours, Monday through Friday.</p>
```

The timezone/region info stays in the `.c-tz` line below the booking button (line 1388) — do not touch that.

- [ ] **Step 2: Verify visually**

Open in browser. Contact section left column: timezone info gone from body. Right column booking card: timezone info still present below the button.

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "fix: remove duplicate timezone from contact left column (3.2)"
```

---

### Task 8: Wire coding card to user-supplied image (3.3)

**Files:**
- Modify: `index.html:1140` (Coding service card `svc-img` background)

- [ ] **Step 1: Update the Coding card image src**

Replace:
```html
<div class="svc-img" style="background-image:url('https://images.unsplash.com/photo-1677442135703-1787eea5ce01?w=800&q=80')">
```
With:
```html
<div class="svc-img" style="background-image:url('coding-screenshot.jpg')">
```

- [ ] **Step 2: Note on the asset**

The file `coding-screenshot.jpg` must be placed in the project root (same directory as `index.html` and `profile_foto.jpg`). Until the file is provided, the card will display a gradient overlay on a blank background — do not deploy to production until the asset is ready.

- [ ] **Step 3: Verify (with placeholder)**

Open in browser. Coding card image area will show as a dark gradient — this is expected until the asset is provided. Confirm the other two service card images are unaffected.

- [ ] **Step 4: Commit**

```bash
git add index.html
git commit -m "feat: wire coding service card to user-supplied image (3.3)"
```

---

### Task 9: MSc end date + email address (3.4, 4.1)

**Files:**
- Modify: `index.html:1227` (MSc credential year)
- Modify: `index.html:31` (JSON-LD structured data)
- Modify: `index.html:1361` (email `href` in contact channels)
- Modify: `index.html:1365` (email display value)
- Modify: `index.html:1399` (footer email link)

- [ ] **Step 1: Update MSc expected end date**

Replace:
```html
<div class="cred-year">March 2026 –</div>
```
With:
```html
<div class="cred-year">March 2026 – Expected 2028</div>
```

- [ ] **Step 2: Update email in JSON-LD structured data**

Replace:
```json
"email": "venceslav.ch@outlook.com",
```
With:
```json
"email": "venceslav.chumchal@gmail.com",
```

- [ ] **Step 3: Update email link in contact channels**

Replace:
```html
<a href="mailto:venceslav.ch@outlook.com" class="c-row">
```
With:
```html
<a href="mailto:venceslav.chumchal@gmail.com" class="c-row">
```

- [ ] **Step 4: Update email display value**

Replace:
```html
<div class="c-val">venceslav.ch@outlook.com</div>
```
With:
```html
<div class="c-val">venceslav.chumchal@gmail.com</div>
```

- [ ] **Step 5: Update footer email link**

Replace:
```html
<a href="mailto:venceslav.ch@outlook.com">Email</a>
```
With:
```html
<a href="mailto:venceslav.chumchal@gmail.com">Email</a>
```

- [ ] **Step 6: Verify**

In browser: contact section email channel shows `venceslav.chumchal@gmail.com`. Footer email link updated. MSc credential shows "March 2026 – Expected 2028".

Run a quick grep to confirm no outlook.com references remain:
```bash
grep -n "outlook.com" index.html
```
Expected: no output.

- [ ] **Step 7: Commit**

```bash
git add index.html
git commit -m "fix: add MSc expected end date and update email address (3.4, 4.1)"
```

---

## Post-implementation checklist

- [ ] All 9 tasks committed
- [ ] `grep -n "outlook.com" index.html` → empty
- [ ] `grep -n "retainer" index.html` → only in "Workshops & Retainers" card name (acceptable)
- [ ] `coding-screenshot.jpg` provided before merging to main / deploying production
- [ ] Open site in browser, scroll full page — no visual regressions
- [ ] Check mobile view at 375px width — responsive layout intact
