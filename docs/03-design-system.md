# Design system

The visual language is called **"Neighbour"**: warm and trusted. Deep green on warm paper, serif headlines, flat honest surfaces, generous air. Three visual directions (Neighbour, Sunrise, Clay) were explored during design; Neighbour was chosen as the closest to the brand's trust-first positioning.

Authoritative sources: `design/fixin10-infinite-canvas.html` (row 2 shows this system live) and `design/tokens.css` (machine-readable). The interactive prototype implements it.

## Colour tokens

| Token | Hex | Role |
|---|---|---|
| `--fx-bg` | `#F7F6F0` | Warm paper background |
| `--fx-surface` | `#FFFFFF` | Cards and sheets |
| `--fx-ink` | `#1F1B16` | Primary text and icons |
| `--fx-muted` | `#6E675C` | Secondary text, labels |
| `--fx-border` | `#E7E2D6` | Hairlines and outlines |
| `--fx-accent` | `#146B52` | The single accent: CTAs and selected states |
| `--fx-accent-soft` | `#E1EFE8` | Tinted chips and icon tiles |
| `--fx-accent-deep` | `#0F5741` | Accent text on tinted surfaces |
| `--fx-success` | `#16A34A` | Runtime states only |
| `--fx-danger` | `#DC2626` | Runtime states only |

Rules: one accent per screen, at most two visible uses (typically the primary CTA plus one selected state). No gradients inside app screens. Key contrast pairs meet WCAG AA.

## Typography

- **Display:** serif stack (Iowan Old Style / Charter / Georgia). H1 25px, H2 21-23px, tracking -0.02em.
- **Body:** system sans (-apple-system / Segoe UI / system-ui) at 15px; secondary 13.5px; meta 12px.
- **Numerals:** monospace, tabular (prices, timers, ETAs, codes).
- **Hindi:** Noto Sans Devanagari as the Devanagari fallback; keep strings centralised.
- **Scale:** 25 / 21 / 15 / 13.5 / 12 / 10 px. Uppercase micro-labels use 0.09em tracking.

## Shape, spacing, elevation

- Radii: cards 16px, buttons 14px, chips pill, OTP cells 12px.
- Grid: 4px base. Tap targets: 48px minimum.
- Elevation: flat by default; borders define surfaces. Floating moments (the tracking sheet) use one soft shadow.

## Motion

- 150-200ms, easing `cubic-bezier(0.2, 0, 0, 1)`.
- Motion confirms state (OTP verified, matched, paid). No decorative animation.
- `prefers-reduced-motion` fully honoured.

## Core components

Buttons (default / pressed / disabled / loading), service cards with selection state, chips and segmented controls, OTP cells, map card with route and pins, bottom sheet, tab bar, switches, radio rows, star rating, coupon ticket, plan cards, code box, toast, timeline.

## Required states

Every fetching or input surface covers: loading (skeleton or button spinner), empty (composed, with a way forward), error (plain cause plus recovery), success, and edge cases (cancelled jobs, coupon removed, long names). See `docs/04-screens-and-flows.md` for where each state appears.

## Accessibility

- Semantic buttons everywhere; icon-only buttons carry aria labels.
- Visible focus rings; keyboard reachable controls.
- Colour is never the only signal (icons and text accompany selection and errors).
- Text contrast >= 4.5:1 on key pairs; CTAs verified.

## Layout and responsiveness

- Authored at 390 x 844 (iPhone-class); scales to tablet and desktop via responsive constraints.
- Screens are Figma-friendly: clean rectangles, real text, no effects inside pages.
