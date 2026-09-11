---
name: sketch-landing
description: "Use this skill when the user asks for a landing page, marketing site, or SaaS website styled like a hand-drawn pencil sketch (black and white, wobbly borders, doodle icons, handwriting fonts). Triggers on phrases like 'sketch style site', 'hand-drawn landing page', 'pencil sketch website', 'wireframe/notebook aesthetic'."
---

# Sketch Landing Page Builder

Before writing any CSS, components, or marketing copy, read:

- [reference/style-guide.md](reference/style-guide.md) — colors, SVG wobble filter, fonts, buttons, icons, motion
- [reference/section-templates.md](reference/section-templates.md) — copy formulas per section
- [reference/example-prompt.md](reference/example-prompt.md) — one complete filled-out site to pattern-match

## Purpose

This skill exists to consistently produce hand-drawn, pencil-sketch landing pages without having to redescribe the visual style every time. The output should look like it was drawn in a notebook with a felt-tip pen — wobbly borders, doodle icons, handwriting headlines, paper grain — not a generic black-and-white Tailwind template.

## When to use it

- New SaaS landing page requests that should feel sketched / hand-drawn
- "Black and white sketch site", "pencil sketch website", "sketch style site"
- "Looks like it's drawn on paper", "notebook aesthetic", "wireframe that is actually designed"
- Rebrand of an existing landing page into sketch style
- Explicit invocation: "use the sketch-landing skill"

Do not use this skill for dashboards, app chrome, admin UIs, or full-color brand sites unless the user explicitly wants those surfaces in sketch style.

## Tech stack defaults

These are defaults, not hard requirements. If the repo already uses a different stack, adapt. If the stack is unspecified, use:

- Next.js 14 App Router + TypeScript
- Tailwind CSS
- Framer Motion
- Single page (`app/page.tsx` assembling section components)
- Mobile-first responsive

Ask only when the existing repo clearly conflicts (e.g. already Vite + Vue). Otherwise proceed with the defaults.

## Visual style rules (non-negotiable)

Summarized here. Full values, SVG, and CSS live in [reference/style-guide.md](reference/style-guide.md). Apply every rule — a grayscale Tailwind page without wobble, grain, and handwriting is a failed output.

- Pure black and white palette: off-white paper background (`#FAFAF7`), near-black ink (`#1A1A1A`). No accent colors, no gray-500 "soft UI."
- Hand-drawn wobble on every border via SVG filter (`feTurbulence` + `feDisplacementMap`). No clean straight lines. Filter the **border layer**, not the text.
- Handwriting font for headings (Caveat / Kalam / Architects Daughter). Readable sans (Inter) for body.
- Sketched double-line buttons. No `rounded-*`. No `shadow-md` / blur shadows — only hand-drawn offset rectangle shadows.
- Single-stroke doodle icons (`fill="none"`, round caps). Not filled Lucide / Heroicons / Material icons.
- Subtle paper-grain texture overlay (`pointer-events-none`, fixed, low opacity).
- Hover = slight wiggle / rotate, not color fills or scale-up pills.
- Scroll-triggered fade/slide animations, staggered children. GPU-safe (`transform` + `opacity` only).

## Standard page structure

Default section order. Copy patterns for each live in [reference/section-templates.md](reference/section-templates.md). Omit a section only if the user explicitly does not want it.

1. Nav
2. Hero
3. Logo strip
4. Features grid
5. How-it-works steps
6. Testimonials
7. Pricing
8. FAQ
9. Final CTA
10. Footer

Split one component per section. Assemble in `app/page.tsx`.

## Content generation rules

When the user has not supplied real copy, invent a plausible SaaS product — name, tagline, feature set, pricing tiers, testimonials — rather than using lorem ipsum or placeholder brackets.

- Real-sounding, specific, on-brand copy every time
- Named people and companies in testimonials (fictional but plausible)
- Concrete feature names, not "Feature 1"
- Pricing with actual numbers, seat/limits language, and a recommended tier
- Never `[Company]`, `Lorem ipsum`, `Your headline here`, or `TODO`

If the user *did* supply a product, use their name, audience, and claims. Invent only the gaps.

## Workflow

1. **Clarify or infer the product concept.** State a one-line read: product, audience, promise. If the brief is empty, invent the product and proceed.
2. **Generate full section-by-section copy** using [reference/section-templates.md](reference/section-templates.md), matching the density of [reference/example-prompt.md](reference/example-prompt.md).
3. **Scaffold the project** with the tech defaults (or adapt to the existing repo). Add fonts, Tailwind tokens, the SVG filter, and the paper-grain overlay before any sections.
4. **Build components section-by-section**, applying the visual style rules from [reference/style-guide.md](reference/style-guide.md). Shared primitives (`SketchFilter`, `SketchBox`, `SketchButton`, doodle icons) first, then sections.
5. **Verify the hand-drawn effect is actually visible.** Check: wobble on borders, double-line buttons, handwriting headings, grain overlay, doodle icons, hover wiggle, scroll stagger. If it just looks like black-and-white Tailwind, it is not done — add the missing sketch layers.
6. **Write `README.md` after the site is fully built.** Only after step 5 passes. This is a required output of every build, even if the user did not ask for docs. Document the site that actually exists (product, run commands, stack, sections, primitives). Replace a default Create Next App README. Do not declare the build done until this file is written.

## Output

Always a working Next.js project (or the adapted stack) with:

- Components split per section under `components/` (or `app/_components/`)
- Shared sketch primitives in their own files
- Page assembled in `app/page.tsx`
- Global filter + grain mounted once in the root layout or page
- `README.md` at the generated site's project root, written last

### README (required, last)

Write this after visual verification, using the real product name and files from this build — not a scaffold stub. This is the landing page's README, not documentation of the sketch-landing skill.

```markdown
# {Product}

{One-line promise from the product read}

## Run locally

npm install
npm run dev

Open http://localhost:3000.

## Stack

{Actual stack used, e.g. Next.js 14 · TypeScript · Tailwind CSS · Framer Motion}

## Page

{Section list that actually shipped, in order}

## Sketch primitives

Where `SketchFilter`, `SketchBox`, `SketchButton`, doodle icons, and paper grain live.
```

## Common mistakes (automatic fail)

| Mistake | Fix |
|---|---|
| Clean `border`, `rounded-lg`, `shadow-md` | Wobbly SVG-filtered border + offset ink rectangle, `rounded-none` |
| Filter applied to the whole card (blurry type) | Filter only the border/shadow layer |
| Inter (or system sans) for the H1 | Handwriting font on all headings |
| Filled Lucide icons | Inline stroke-only doodle SVGs |
| `#fff` + `zinc-900` only, no grain | Paper `#FAFAF7` + grain overlay |
| Hover = background fill / `scale-105` | 1–2° rotate wiggle |
| Lorem ipsum / `[Feature Name]` | Invent a real product and write finished copy |
| One giant `page.tsx` | One file per section |
| No site README, or the leftover Create Next App README | Write the product README after visual verification |
