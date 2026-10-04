# FixIn10

**Home repairs, fixed in minutes.** FixIn10 is an on-demand home-services app for India: customers book a verified electrician, carpenter or plumber, get matched with a nearby pro in about 10 minutes, track the visit live, and pay by the hour actually worked.

> **Status: design complete (v2).** Next phase: frontend (Flutter, mock data) followed by backend. See [docs/05-engineering-roadmap.md](docs/05-engineering-roadmap.md).

## Repository map

| Path | What it is |
|---|---|
| [`design/fixin10-interactive-prototype.html`](design/fixin10-interactive-prototype.html) | Working end-to-end prototype of the customer journey. Open in a browser, no setup. |
| [`design/fixin10-infinite-canvas.html`](design/fixin10-infinite-canvas.html) | The full design board: product context, design system and all 25 screens by journey stage. |
| [`design/tokens.css`](design/tokens.css) | Design tokens as CSS variables (ready to port to Flutter/Dart). |
| [`docs/01-product-overview.md`](docs/01-product-overview.md) | The idea: problem, users, service model, market context. |
| [`docs/02-naming.md`](docs/02-naming.md) | Why it is called FixIn10, with the research behind it. |
| [`docs/03-design-system.md`](docs/03-design-system.md) | Visual language, tokens, components, states, accessibility. |
| [`docs/04-screens-and-flows.md`](docs/04-screens-and-flows.md) | All 25 screens, journey stages, flows and state coverage. |
| [`docs/05-engineering-roadmap.md`](docs/05-engineering-roadmap.md) | Frontend and backend plan, data model draft, open questions. |

## Core facts

- **Trades (v1):** electrician, carpenter, plumber. Customer app first, pro app after.
- **Market:** India. Prices in ₹. English first; Hindi (Devanagari) planned, strings centralised for it.
- **The promise:** matched with a verified nearby pro in about 10 minutes. "Instant" vs "Schedule" depends on local supply density.
- **Pricing model:** hourly rate + small visit fee, billed only for time actually worked in 15-minute steps. Coupons, wallet, tips, Plus membership (zero visit fee) and referral rewards.
- **Platform:** cross-platform mobile (Flutter target). Warm light theme, a single green accent, serif display type.

## For AI agents reading this repo

1. Read `docs/01-product-overview.md` first, then `docs/03-design-system.md` and `docs/04-screens-and-flows.md`.
2. The HTML files in `design/` are the source of truth for UI look and behaviour. The prototype is clickable end to end; match its flows and states.
3. Current phase: **frontend with mock data only.** Do not add backend, API, auth or payment integrations until the frontend is approved (see roadmap).
4. Use the tokens in `design/tokens.css`. Keep user-facing strings centralised for future Hindi support.
5. When unsure, prefer what the prototype does. Every state shown there has a reason.

## Viewing the design files

Open the two HTML files directly in any browser. No server, no dependencies.

- **Canvas:** drag to pan, scroll to zoom.
- **Prototype:** start at the splash screen and walk through; use the "Demo:" chips below the phone to advance the service-day states.
