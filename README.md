# Sketch Landing Page Builder

**Skill name:** `sketch-landing`

A reusable Cursor / Claude Code skill for building hand-drawn, pencil-sketch style black-and-white SaaS landing pages. The page should look like it was drawn in a notebook with a felt-tip pen — wobbly borders, doodle icons, handwriting headlines, paper grain — not a generic grayscale Tailwind template.

## Skill identity

| | |
|---|---|
| **Name** | `sketch-landing` |
| **Display name** | Sketch Landing Page Builder |
| **Location** | [`skills/sketch-landing/`](skills/sketch-landing/) |
| **Entry file** | [`skills/sketch-landing/SKILL.md`](skills/sketch-landing/SKILL.md) |

## When it runs

The skill activates automatically when a request matches the trigger description: a landing page, marketing site, or SaaS website in hand-drawn pencil-sketch style.

Trigger phrases include:

- "sketch style site"
- "hand-drawn landing page"
- "pencil sketch website"
- "wireframe / notebook aesthetic"
- "black and white sketch site"

You can also invoke it explicitly:

```
use the sketch-landing skill
```

Do not use it for dashboards, app chrome, admin UIs, or full-color brand sites unless those surfaces are explicitly requested in sketch style.

## What it produces

A working single-page marketing site with:

- One component per section, assembled in `app/page.tsx`
- Shared sketch primitives (`SketchFilter`, `SketchBox`, `SketchButton`, doodle icons)
- Finished, product-specific copy (no lorem ipsum)
- A `README.md` written after the site is fully built (how to run, stack, sections)

Default section order: Nav → Hero → Logo strip → Features → How it works → Testimonials → Pricing → FAQ → Final CTA → Footer.

## Tech stack defaults

These are defaults, not hard requirements. Adapt if the repo already uses a different stack.

- Next.js 14 App Router + TypeScript
- Tailwind CSS
- Framer Motion
- Mobile-first responsive

## Visual style (non-negotiable)

| Rule | Spec |
|---|---|
| Palette | Paper `#FAFAF7`, ink `#1A1A1A` — no accent colors |
| Borders | SVG wobble (`feTurbulence` + `feDisplacementMap`) on the border layer, not the text |
| Type | Caveat (or Kalam / Architects Daughter) for headings; Inter for body |
| Buttons | Sketched double-line, no border-radius, hand-drawn offset shadows |
| Icons | Single-stroke doodles, not filled icon sets |
| Texture | Subtle paper-grain overlay |
| Hover | Slight wiggle / rotate (±1–2°) |
| Scroll | Staggered fade/slide, `transform` + `opacity` only |

Full values live in [`skills/sketch-landing/reference/style-guide.md`](skills/sketch-landing/reference/style-guide.md).

## Contents

```
skills/sketch-landing/
  SKILL.md                          # Instructions the agent follows
  reference/
    style-guide.md                  # Colors, SVG filter, fonts, buttons, motion
    section-templates.md            # Copy formulas per section
    example-prompt.md               # Worked example (Margin, a design-review SaaS)
```

| File | Role |
|---|---|
| [`SKILL.md`](skills/sketch-landing/SKILL.md) | Purpose, triggers, workflow, output contract |
| [`style-guide.md`](skills/sketch-landing/reference/style-guide.md) | Visual spec to copy, not approximate |
| [`section-templates.md`](skills/sketch-landing/reference/section-templates.md) | Headline / feature / pricing / FAQ formulas |
| [`example-prompt.md`](skills/sketch-landing/reference/example-prompt.md) | End-to-end filled example to pattern-match |

## Install

**Cursor (this project):** keep the skill at `skills/sketch-landing/`. For project-wide auto-discovery you can also copy it to `.cursor/skills/sketch-landing/`.

**Cursor (all projects):** copy the folder to `~/.cursor/skills/sketch-landing/`.

**Claude Code:** copy the folder to `.claude/skills/sketch-landing/` in the target repo.

## Example prompt

```
Build a sketch-style SaaS landing page for a design-review tool.
Black and white, looks hand-drawn.
```

The worked result for that brief (product name **Margin**, full copy, file map) is in [`example-prompt.md`](skills/sketch-landing/reference/example-prompt.md).
