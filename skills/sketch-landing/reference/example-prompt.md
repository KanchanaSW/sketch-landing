# Worked example — Margin

Pattern-match against this filled-out site when generating a new one. Swap the product; keep the density, specificity, and sketch treatment.

---

## Incoming brief

> Build a sketch-style SaaS landing page for a design-review tool. Black and white, looks hand-drawn.

No extra copy supplied — invent the product and write finished language.

---

## Product read

**Margin** — async design review for product teams who are tired of feedback dying in Zoom chats and 47-comment Figma threads. Designers drop a mockup, teammates scribble in the literal margins, and the board becomes the source of truth for what shipped.

Audience: product designers, design-team leads, and the PMs/founders who review their work. Promise: fewer review meetings, decisions that stay attached to the frame.

---

## Full page copy

### Nav

- Wordmark: `Margin` + doodle of a folded page corner
- Links: Features · How it works · Pricing · FAQ
- CTA: `Start free`

### Hero

- Eyebrow: `Design review · without the stand-up`
- Headline: `Leave notes in the margins. Ship work that actually got approved.`
- Subheadline: `Margin is a shared review board for mockups, decks, and flows. Teammates scribble next to the frame instead of burying you in a Figma comment graveyard.`
- Primary CTA: `Start a free board`
- Secondary CTA: `See a 60-second tour`
- Sketch aside: wobbly "notebook" card showing a fake mobile mockup with three handwritten callouts (`type too shy`, `move CTA up`, `ship this`) and a checked box reading `v3 — approved`

### Logo strip

- Label: `Already in the margins at`
- Marks (sketched wordmarks): `Northbeam` · `Kite & Co` · `Harbor LMS` · `Sable` · `Campfire` · `Runnel`

### Features (6)

1. **Doodle:** fountain pen  
   **Title:** Margin threads  
   **Benefit:** Every scribble sits beside the frame it belongs to, so "make it pop" finally has a home.

2. **Doodle:** stacked papers  
   **Title:** Version timeline  
   **Benefit:** Drop v2 next to v1. Reviewers see what changed without a 20-minute archaeology session.

3. **Doodle:** paper plane  
   **Title:** Client review links  
   **Benefit:** Send a guest link. Clients comment in the margins — no seat, no tutorial, no Slack reconnect.

4. **Doodle:** mug  
   **Title:** Slack digest  
   **Benefit:** Unresolved notes land in Slack once a day, not every time someone sneezes on a sticker.

5. **Doodle:** wobbly checkbox  
   **Title:** Pinned decisions  
   **Benefit:** Mark a thread resolved and it stays pinned to the frame as the thing you agreed, not a feeling you had.

6. **Doodle:** binder clip  
   **Title:** Export the trail  
   **Benefit:** Download a PDF of the board — frames, notes, and who said what — for the people who live in email.

### How it works

**Title:** `From messy feedback to a marked-up board in three steps`

1. **01 · Drop the mockup**  
   Upload a PNG, PDF, or a Figma frame. Margin lays it on a notebook page with empty margins on purpose.

2. **02 · Invite the red pens**  
   Teammates and clients get a link. They scribble, pin, and argue in the margins instead of starting another meeting.

3. **03 · Pin what shipped**  
   Resolve threads, pin the decision, export the trail. The next version starts from what you actually agreed.

### Testimonials

**Title:** `What teams scribble in the margins`

> "We killed the Thursday design review. The board is the review. I still get spicy notes — they just live next to the hero instead of in a Google Doc named 'feedback FINAL v7.'"
> — Priya Nandakumar, Design lead at Harbor LMS

> "I sent a guest link to a founder who refuses Figma. He left seven notes on the pricing page and approved v3 the same afternoon. That's the whole product for me."
> — Evan Cole, Freelance product designer

> "Pinned decisions saved us during the rebrand. Six weeks later we could still see *why* the wordmark sat left-aligned, in the founder's own crooked handwriting."
> — Lina Ortiz, PM at Northbeam

### Pricing

**Title:** `Pick a page in the notebook`  
**Footnote:** `Prices in USD. Cancel any time. We'll email a sketched receipt.`

| | **Page** | **Sketchbook** (most teams) | **Studio** |
|---|---|---|---|
| Price | `$0/mo` | `$16/seat/mo` | `$29/seat/mo` |
| Blurb | Solo designers trying one board | Product teams living in review | Agencies + client-heavy shops |
| Features | 1 board · 3 pages · Margin threads · Watermarked guest links · 7-day version history | Unlimited boards · Unlimited pages · Guest links, no watermark · Slack digest · Pinned decisions · 90-day history · PDF export | Everything in Sketchbook · Client workspaces · Custom wordmark on guest links · SSO · Priority support (actual humans) · Unlimited history |
| CTA | `Start Page` | `Start Sketchbook` | `Get Studio` |

Sketchbook is featured: 6px offset shadow, handwritten `most teams` along the top edge.

### FAQ

**Title:** `Questions we get in the margins`

**Is this just Figma comments with extra steps?**  
No. Figma comments are for the people already in the file. Margin is the review surface you send to PMs, founders, and clients who will never install Figma. Designers still build in Figma; they drop frames here when they want a decision.

**Can clients comment without paying for a seat?**  
Yes. Guest links are free on every paid plan (and available, watermarked, on Page). Guests scribble and pin. They do not get a dashboard, and they do not eat a seat.

**Do you store our mockups?**  
Boards live on our side so guest links work. You can export a PDF of the trail and delete a board whenever. We are not a DAM and we do not train models on your frames.

**What happens if we cancel?**  
You keep PDF exports of every board. The guest links go cold. We keep a 30-day frozen copy if you change your mind; after that it is gone.

**Is there a free way to try this with a real client?**  
Page is free forever for one board. If you want a clean guest link without our wordmark, Sketchbook starts when you invite a second teammate.

**Can we brand the guest link?**  
Studio lets you put your wordmark on the notebook. Sketchbook uses Margin's. Most product teams do not care; agencies do.

### Final CTA

- Headline: `Start a board before the next review meeting.`
- Sub: `Drop a frame, send a link, and let the margins do the talking.`
- CTA: `Start a free board`

### Footer

- Descriptor: `Margin — design review that stays next to the work.`
- Product: Features, How it works, Pricing, FAQ
- Legal: Privacy, Terms
- Bottom: `© 2026 Margin. Drawn by hand, shipped as software.`

---

## File map

```
README.md             # written last, after visual verification — product, run, stack, sections
app/
  layout.tsx          # Caveat + Inter, SketchFilter, PaperGrain, bg-paper
  page.tsx            # section assembly in default order
  globals.css         # paper/ink tokens, rounded-none default
components/
  SketchFilter.tsx
  PaperGrain.tsx
  SketchBox.tsx
  SketchButton.tsx
  doodles.tsx         # stroke-only icons used above
  Nav.tsx
  Hero.tsx
  LogoStrip.tsx
  Features.tsx
  HowItWorks.tsx
  Testimonials.tsx
  Pricing.tsx
  FAQ.tsx
  FinalCta.tsx
  Footer.tsx
```

`app/page.tsx` only imports and stacks these. No marketing copy inlined in the page file.

---

## Style application (what "done" looks like on this site)

- Page background `#FAFAF7`, grain overlay visible when you squint
- `SketchFilter` in `layout.tsx`; every card/button outline uses `filter: url(#sketch-wobble)` on a **border span**, not on the text
- H1 / H2 / nav / buttons: Caveat. Body / FAQ answers / pricing feature lines: Inter
- Hero CTA and pricing CTAs are double-line `SketchButton`s, `rounded-none`, primary filled ink
- Feature cards: `SketchBox` + 4px offset ink shadow + doodle from `doodles.tsx` (pen, papers, plane, mug, checkbox, clip)
- Featured Sketchbook column: 6px offset shadow + handwritten `most teams`
- Hover on buttons, cards, and logo wordmarks: ±1.4° wiggle, ~450ms
- Features / testimonials / pricing / FAQ: `staggerChildren: 0.08` on `whileInView`
- No Lucide, no `rounded-xl`, no `shadow-lg`, no blue links, no lorem, no `[Feature]`

Use this density of copy and this component split for whatever product you invent or receive next.
