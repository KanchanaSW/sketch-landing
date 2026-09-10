# Sketch Landing — Visual Spec

Standalone technical reference. Copy these values; do not approximate.

## Palette

| Token | Hex | Tailwind | Use |
|---|---|---|---|
| `paper` | `#FAFAF7` | `bg-paper` | Page background |
| `ink` | `#1A1A1A` | `text-ink`, `border-ink` | Type, borders, icons, shadows |
| `ink-muted` | `#4A4A4A` | `text-ink-muted` | Body secondary, captions |
| `paper-shade` | `#F0EFEA` | `bg-paper-shade` | Alternate section bands only |

No other colors. No blue links, no yellow highlights, no gray-400 hairlines. Links are ink + underline.

```js
// tailwind.config.ts theme.extend.colors
paper: "#FAFAF7",
ink: "#1A1A1A",
"ink-muted": "#4A4A4A",
"paper-shade": "#F0EFEA",
```

```css
html, body {
  background: #FAFAF7;
  color: #1A1A1A;
}
```

## SVG wobble filter

Mount **once** in the root layout (hidden SVG). Every border, button outline, and offset shadow references `url(#sketch-wobble)`.

```tsx
export function SketchFilter() {
  return (
    <svg className="absolute h-0 w-0" aria-hidden="true" focusable="false">
      <defs>
        <filter id="sketch-wobble" x="-20%" y="-20%" width="140%" height="140%">
          <feTurbulence
            type="turbulence"
            baseFrequency="0.04"
            numOctaves="2"
            seed="2"
            result="noise"
          />
          <feDisplacementMap
            in="SourceGraphic"
            in2="noise"
            scale="3"
            xChannelSelector="R"
            yChannelSelector="G"
          />
        </filter>
      </defs>
    </svg>
  );
}
```

Knobs: `baseFrequency` 0.03–0.05 (higher = tighter jitter). `scale` 2.5–4 (higher = more warp). Keep seed stable so layout does not shimmer between renders.

### Apply to the border layer only

Never `filter: url(#sketch-wobble)` on a node that contains text — displacement makes type look drunk.

```tsx
export function SketchBox({
  children,
  className = "",
}: {
  children: React.ReactNode;
  className?: string;
}) {
  return (
    <div className={`relative ${className}`}>
      <span
        aria-hidden
        className="pointer-events-none absolute inset-0 border-2 border-ink"
        style={{ filter: "url(#sketch-wobble)", borderRadius: 0 }}
      />
      <div className="relative">{children}</div>
    </div>
  );
}
```

Every card, input, avatar frame, and pricing column is a `SketchBox` (or the same pattern). `border-radius: 0` everywhere. No `rounded-*` utilities.

## Typography

| Role | Family | Weight | Size |
|---|---|---|---|
| H1 | Caveat | 700 | `text-5xl`–`text-7xl` (mobile `text-4xl`) |
| H2 / H3 | Caveat | 600–700 | `text-3xl`–`text-5xl` |
| Nav / buttons / labels | Caveat | 600 | `text-xl`–`text-2xl` |
| Body | Inter | 400–500 | `text-base` leading-relaxed |
| Fine print | Inter | 400 | `text-sm` `text-ink-muted` |

Primary handwriting: **Caveat**. Fallbacks if a brief calls for a different sketch hand: Kalam, Architects Daughter. Never mix two handwriting fonts on one page.

```ts
import { Caveat, Inter } from "next/font/google";

const caveat = Caveat({
  subsets: ["latin"],
  weight: ["400", "600", "700"],
  variable: "--font-hand",
});

const inter = Inter({
  subsets: ["latin"],
  weight: ["400", "500"],
  variable: "--font-sans",
});
```

```js
// tailwind.config.ts theme.extend.fontFamily
hand: ["var(--font-hand)", "Caveat", "cursive"],
sans: ["var(--font-sans)", "Inter", "system-ui", "sans-serif"],
```

Headings: `font-hand tracking-tight`. Body: `font-sans`. Do not uppercase handwriting; it reads as shouting.

Google Fonts fallback (non-Next):

```html
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link
  href="https://fonts.googleapis.com/css2?family=Caveat:wght@400;600;700&family=Inter:wght@400;500&display=swap"
  rel="stylesheet"
/>
```

## Buttons

Sketched double-line, square corners, ink fill on primary, paper fill on secondary.

```tsx
export function SketchButton({
  children,
  variant = "primary",
  className = "",
  ...props
}: React.ButtonHTMLAttributes<HTMLButtonElement> & {
  variant?: "primary" | "secondary";
}) {
  const filled = variant === "primary";
  return (
    <button
      className={`group relative inline-flex items-center justify-center px-7 py-3 font-hand text-2xl leading-none ${className}`}
      {...props}
    >
      {filled && (
        <span
          aria-hidden
          className="absolute inset-0 bg-ink"
          style={{ filter: "url(#sketch-wobble)" }}
        />
      )}
      <span
        aria-hidden
        className="pointer-events-none absolute inset-0 border-2 border-ink"
        style={{ filter: "url(#sketch-wobble)" }}
      />
      <span
        aria-hidden
        className="pointer-events-none absolute inset-[4px] border border-ink"
        style={{ filter: "url(#sketch-wobble)" }}
      />
      <span
        className={`relative ${filled ? "text-paper" : "text-ink"}`}
      >
        {children}
      </span>
    </button>
  );
}
```

Rules:

- No `rounded-*`, no `shadow-*` utilities, no gradient fills
- Primary = ink fill + paper label. Secondary = paper fill + double ink outline
- Padding `px-6`–`px-8`, `py-2.5`–`py-3`. Handwriting at `text-xl` or `text-2xl`

## Hand-drawn offset shadows

A second ink rectangle, offset down-right, sitting behind the box. Filter the shadow the same way.

```tsx
<span
  aria-hidden
  className="absolute inset-0 translate-x-[4px] translate-y-[4px] bg-ink"
  style={{ filter: "url(#sketch-wobble)" }}
/>
```

Offset: **4px / 4px** default, **6px / 6px** on hero/pricing featured cards. Never `box-shadow: 0 10px 30px rgba(...)`.

## Icons

Single-stroke doodles. Inline SVG, not an icon font.

- `fill="none"`
- `stroke="currentColor"` (`#1A1A1A`)
- `strokeWidth={1.75}` (range 1.5–2)
- `strokeLinecap="round"` `strokeLinejoin="round"`
- Viewbox 24×24, rendered at 28–36px in feature cards, 20–24px in UI chrome
- Paths may be slightly imperfect (a bump, a non-closed corner) — that is the point
- One metaphor per icon (pencil, mug, paper plane, tick in a wobbly box). No abstract geometric logos

Do not use Lucide, Heroicons, Phosphor, Font Awesome, or emoji as the primary icon set. A tiny inline doodle sprite file (`components/doodles.tsx`) is the right shape.

## Paper grain

Fixed overlay, pointer-events none, above the background and below interactive content (or on top at very low opacity).

```tsx
export function PaperGrain() {
  return (
    <div
      aria-hidden
      className="pointer-events-none fixed inset-0 z-[1] opacity-[0.045]"
      style={{
        backgroundImage: `url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.85' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E")`,
        backgroundRepeat: "repeat",
        backgroundSize: "180px 180px",
      }}
    />
  );
}
```

Do not attach grain to scrolling containers. Keep opacity 0.035–0.055 so type stays readable.

## Motion

Framer Motion. Animate `transform` and `opacity` only.

### Hover wiggle

```ts
const wiggle = {
  rest: { rotate: 0 },
  hover: {
    rotate: [0, -1.4, 1.2, -0.6, 0],
    transition: { duration: 0.45, ease: "easeInOut" },
  },
};
```

- Buttons, cards, logo marks, doodle icons: `whileHover="hover"` `initial="rest"` `animate="rest"`
- Rotation envelope: **±1° to ±2°**. Never 8–15°.
- Duration **400–500ms**. No infinite CSS wiggle on idle elements.

### Scroll reveal

```ts
const fadeUp = {
  hidden: { opacity: 0, y: 24 },
  show: {
    opacity: 1,
    y: 0,
    transition: { duration: 0.55, ease: [0.22, 1, 0.36, 1] },
  },
};

const stagger = {
  hidden: {},
  show: { transition: { staggerChildren: 0.08 } },
};
```

- Sections: `whileInView="show"` `viewport={{ once: true, margin: "-80px" }}`
- Grids (features, testimonials, pricing, FAQ): parent `stagger`, children `fadeUp`
- Do not animate `top` / `left` / `width` / `height`

### Reduced motion

Honor `prefers-reduced-motion: reduce` — skip wiggle and scroll travel; keep a 150ms fade if anything.

## Layout notes

- Max content width `max-w-5xl` or `max-w-6xl`, generous section padding `py-20`–`py-28` (`py-14` on mobile)
- Nav: static or sticky paper bar with a wobbly bottom border — not a glass pill
- Alternate `paper` / `paper-shade` bands so long pages do not flatten
- Mobile: single column, full-width buttons, no overlapping rotated cards

## Implementation checklist

- [ ] `SketchFilter` in the layout
- [ ] `PaperGrain` overlay mounted
- [ ] Tailwind colors `paper` / `ink` / `ink-muted`
- [ ] Caveat on headings, Inter on body
- [ ] Every box/button uses the wobble border layer
- [ ] Double-line buttons, `rounded-none`
- [ ] Offset ink shadows, not blur shadows
- [ ] Stroke-only doodles
- [ ] Hover wiggle ±2°
- [ ] Staggered `whileInView` on grids
