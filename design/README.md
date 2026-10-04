# Design files

Two self-contained HTML files carry the whole design. Open them in any browser; no server, no dependencies.

## 1. `fixin10-interactive-prototype.html` - the working prototype

The complete customer journey, clickable end to end with working states:

- Splash -> onboarding -> OTP login -> set address
- Home -> pick a trade -> service list -> service detail -> schedule -> review & pay (coupon toggles, payment selection)
- Matching (animated) -> live tracking -> start code -> in-progress with a **live hourly meter** -> bill (tip selector updates the total) -> rating -> back home
- Bookings / wallet / profile tabs; chat (send messages); membership, referral, settings and support screens

Use the **"Demo:" chips below the phone** to advance the service-day steps (pro arrives -> code entered -> finish the job). Amounts and receipts carry through the flow.

## 2. `fixin10-infinite-canvas.html` - the full design board

A draggable, zoomable canvas (drag to pan, scroll to zoom) in three rows:

1. **Project context** - what FixIn10 is, who it is for, the naming research, the core flow.
2. **Design system** - final tokens, typography, components and states (dev handoff notes included).
3. **Deliverables** - all 25 screens in five journey stages, with arrows showing the flow.

## 3. `tokens.css`

The design tokens as CSS variables. Use it as the source of truth when porting the system to Flutter/Dart (map each token to its theme equivalent). See `docs/03-design-system.md` for roles and rules.
