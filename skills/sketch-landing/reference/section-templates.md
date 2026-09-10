# Sketch Landing — Section Copy Formulas

Reusable patterns so generated copy stays consistent across products. Fill every slot with specific, finished language. Never leave brackets in the rendered page.

When a slot is unknown, invent a plausible value (see SKILL.md content rules).

---

## Nav

**Slots:** product name · 3–5 section anchors · primary CTA

**Formula:**

- Wordmark = product name in handwriting, optionally a 16–20px doodle to the left
- Links = Features, How it works, Pricing, FAQ (drop one if the page is short)
- Right CTA = short verb phrase matching the hero primary CTA (`Start free`, `Try {Product}`, `Get a demo`)

**Don't:** hamburger-only on desktop; more than one CTA in the bar.

---

## Hero

**Slots:** eyebrow · headline · subheadline · primary CTA · secondary CTA · sketch aside

**Headline formula** (pick one):

1. `{Do the job} without {the hated old way}`
2. `{Outcome} for {specific audience}, sketched simply`
3. `{Product} is {the category} that {feels human / stays out of the way}`

Keep to ~6–12 words. Handwriting will wrap — prefer two short lines over one long clause.

**Subheadline formula:**

`{One sentence: who it is for}. {One sentence: the mechanism in concrete nouns, not "leverage" / "unlock" / "empower"}.`

**CTAs:**

- Primary: `{Verb} {object}` — `Start a free board`, `Sketch your first brief`
- Secondary: `{See / Watch} {proof}` — `See a 60-second tour`, `Browse example boards`

**Eyebrow (optional):** `{Audience} · {category}` or a one-line product truth. Not a pill badge with tracking.

**Sketch aside:** a large doodle or a fake "notebook" card (wobbly box + handwritten annotation), not a screenshot of a glossy dashboard.

---

## Logo strip

**Label formula:** `Already in the margins at` / `Drawn up by teams at` / `Used in the notebooks of`

**Logos:** 5–7 fictional or real company names set in handwriting or simple wordmarks. No colorful SVG brand kits. If real logos would break the B/W rule, render names as sketched wordmarks.

**Don't:** "Trusted by 10,000+ companies" with no names.

---

## Features grid

Default: **6 cards** in 3×2 (stack to 1 col on mobile). 3 cards is acceptable for a very tight product.

**Card formula:**

| Slot | Rule |
|---|---|
| Doodle | One concrete object. Named in `doodles.tsx`. |
| Title | 2–4 words, a capability the user can picture |
| Benefit | **One sentence.** Outcome, not "powerful X". No stacked paragraphs. |

**Title patterns:** `{Noun} {noun}` (`Margin threads`), `{Verb}d {nouns}` (`Pinned decisions`), `{Noun} without {noun}` (`Feedback without Zoom`)

**Benefit patterns:**

- `{User} can {action}, so {result}.`
- `{Pain} becomes {replacement}.`
- `{Artifact} stays {quality} even when {messy condition}.`

**Don't:** icon + title + three bullet points. Don't title cards "Fast", "Secure", "Easy."

---

## How it works

**Section title formula:** `How {Product} works` or `From {mess} to {artifact} in {n} steps`

**Step formula (3 steps, sometimes 4):**

| Slot | Rule |
|---|---|
| Number | Hand-lettered `01` `02` `03` — not a filled circle badge |
| Title | Imperative, 2–5 words (`Drop the mockup`) |
| Body | Two short sentences: action, then what you get |
| Doodle | Unique per step, connecting visually if possible (arrow scribbles between steps on desktop) |

**Arc:** ingest → work → outcome. Example shape: *upload / invite* → *mark up / decide* → *export / ship*.

---

## Testimonials

**Section title formula:** `What {audience} scribble in the margins` / `Kind words, slightly crooked`

**Card formula (3 quotes):**

```
"{Specific situation + what changed. 1–3 sentences. Sound like a person, not a case study.}"
— {First Last}, {Role} at {Company}
```

**Rules:**

- Named humans (fictional is fine). Mix roles: IC designer, PM, founder, client.
- Mention a concrete artifact (`the v3 hero`, `our Series A deck`, `the onboarding flow`)
- Optional tiny doodle avatar (wobbly circle + initials), not photo headshots
- One quote may be slightly longer and span 2 columns if the grid allows

**Don't:** "Great product, highly recommend." Don't all be "CEO, TechCo."

---

## Pricing

**Section title formula:** `Pick a page in the notebook` / `Simple pricing, no fine-print maze`

**Default: 3 tiers.** Middle tier is recommended.

**Tier formula:**

| Slot | Rule |
|---|---|
| Name | Evocative, not "Basic / Pro / Enterprise" unless the product is extremely generic. Prefer `Page` / `Sketchbook` / `Studio`, or `{Job}-sized` names. |
| Price | `$N/mo` (or `/seat`). Annual toggle optional; if omitted, show monthly. |
| Blurb | One line: who this tier is for |
| Features | 4–6 lines, leading with a concrete limit (`3 boards`, `Unlimited comments`) |
| CTA | Free / starter = `Start {name}`. Paid = `Get {name}`. Featured = `Start {name}` matching hero. |
| Featured | Middle column: offset shadow 6px, optional handwritten `most teams` tag on the top edge |

**Feature-line formula:** `{Limit or capability} — {why it matters in 3–7 words}` or just the capability if obvious.

Include a one-line footnote: `Prices in USD. Cancel any time. We'll email a sketched receipt.`

---

## FAQ

**Section title formula:** `Questions we get in the margins`

**Item formula (5–7 pairs):**

- **Q:** The objection a skeptical buyer actually types into Slack
- **A:** 2–4 sentences. Direct first sentence, then the mechanism or caveat.

**Cover at least:**

1. What it is / who it is for
2. How it differs from `{obvious competitor category}`
3. Collaboration / seats / client access
4. Data / export / lock-in
5. Pricing / trial / "can I use it free"
6. Something product-specific and slightly human

**Don't:** "What is {Product}?" answered with the tagline restated. Don't accordion-dump a help center.

---

## Final CTA

**Headline formula:** `{Imperative} before {the next bad meeting / the next review cycle}`  
or `{Start {artifact}} — the pen is already on the table.`

**Sub:** One sentence repeating the mechanism, not a new feature dump.

**CTA:** Same primary as the hero. Optional quiet secondary: `or read the FAQ`.

Wrap in a large `SketchBox` with the 6px offset shadow so it feels like a drawn coupon / torn notebook page.

---

## Footer

**Slots:** wordmark · one-line descriptor · 3–4 link clusters · legal

**Formula:**

- Left: name + `{tagline, shorter than the hero}`
- Clusters: Product (Features, Pricing), Company (optional), Legal (Privacy, Terms)
- Bottom line: `© {year} {Product}. Drawn by hand, shipped as software.`

Keep it sparse. No newsletter form unless the user asked for one.

---

## Voice

- Concrete nouns (boards, comments, pencils, reviews, seats)
- Short sentences. Occasional fragment.
- Warm, slightly wry. Never "unlock your potential"
- First person plural is fine in FAQ/CTA (`we`, `we'll`)
- Product name used as a proper noun, not a verb, unless the brand is clearly a verb

## Density cheat sheet

| Section | Target length |
|---|---|
| Hero headline | 6–12 words |
| Hero sub | 20–40 words |
| Feature benefit | 12–22 words |
| How-it-works body | 2 sentences |
| Testimonial | 25–55 words |
| Pricing blurb | 8–16 words |
| FAQ answer | 30–70 words |
| Final CTA sub | 1 sentence |
