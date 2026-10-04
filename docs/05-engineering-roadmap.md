# Engineering roadmap

## Phase status

| Phase | Scope | Status |
|---|---|---|
| 0. Product design | Concept, naming, design system, 25 screens, interactive prototype | **Done (this repo)** |
| 1. Frontend (customer app) | Flutter app with mock data, full booking journey | Next |
| 2. Backend | API, auth, matching, payments, tracking, notifications | After frontend approval |
| 3. Pro app, admin, hardening | Pro-side app, ops console, production readiness | Later |

**Rule: do not start backend work until the frontend is walked through and approved.** The prototype in `design/` defines the expected behaviour.

## Phase 1: Frontend (Flutter, mock data only)

Goal: "I can open the app and complete an entire booking as a customer."

- Route-driven navigation (central route table; no navigation logic inside widgets).
- Reusable page templates: page header, service cards, pro card, price breakdown, address card, date/time selector, booking status card, bottom action bar, confirmation card, rating, empty / loading / error states, skeleton loaders, bottom sheets.
- Design tokens from `design/tokens.css` mapped 1:1 (colour scheme seeded from `#146B52`).
- State layer for: selected service, selected pro, date/time, address, booking state, payment method, tracking, completion. One place (e.g. Riverpod or equivalent), never inside widgets.
- Mock repositories and data for: services, categories, pros, availability, addresses, bookings, pricing, booking status, reviews. Mock data stays separate from UI code.
- Strings centralised for future Hindi; keep ~30% text headroom.
- Responsive checks: small and large phones, tablets where reasonable. No overflow at 360dp width.

**Definition of done:** the whole happy path plus key empty / error / loading states run offline with mock data; no backend calls.

## Phase 2: Backend (scope proposal, to be refined)

- **Auth:** phone OTP (SMS provider), JWT sessions.
- **Catalog:** trades, services, prices, zones.
- **Bookings & matching:** booking lifecycle (created -> matching -> assigned -> started -> completed / cancelled); offer fan-out to nearby pros with countdown; fallback radius expansion.
- **Payments:** UPI first (Razorpay or similar); pay-after-service flow; coupons; wallet ledger; refunds; tips.
- **Tracking:** ETA updates and status stream (polling or websocket).
- **Notifications:** push and SMS for booking updates and OTP.
- **Reviews, support tickets, admin panel** for ops (pro verification, zones, refunds).

Suggested sequencing: auth -> catalog -> booking + mock matching -> payments -> tracking -> notifications -> admin.

## Data model draft (starting point)

- **user**: id, phone, name, default_address_id, language, wallet_balance, membership (none / plus, expiry)
- **address**: id, user_id, label, line, landmark, geo, gate_code_note
- **service**: id, trade (electrician / carpenter / plumber), name, description, hourly_rate, min_minutes, warranty_days
- **pro**: id, name, trade, kyc_status, rating, jobs_done, availability, geo, vehicle_info
- **booking**: id, user_id, service_id, pro_id, address_id, slot (now / scheduled), status, start_code, started_at, ended_at, billable_minutes, rate, visit_fee, coupon_id, tip, payment_status, total
- **payment**: id, booking_id, method (upi / card / cash), status, provider_ref, amounts
- **coupon**: code, type, value, cap, conditions, expiry
- **review**: booking_id, rating, tags, text, tip
- **membership**: user_id, plan, started_at, renews_at
- **referral**: code, inviter_id, invitee_id, status, reward_amount
- **chat_message**: booking_id, sender, text, sent_at
- **ticket**: user_id, booking_id, topic, status

## Integrations to plan

SMS / OTP, UPI payments (for example Razorpay), maps and geocoding, push notifications, analytics, crash reporting.

## Open questions

- Zone density rules for "Instant" vs "Schedule" (polygons, minimum pro count).
- Final rate card and visit fee per city; whether surge pricing exists.
- Pro KYC depth and payout cadence.
- Cancellation fee edges (after the code is entered).
- Hindi copy review and language switch behaviour.

## Phase 3+ (later)

Pro app (offers, navigation, earnings, availability), admin console, production hardening, real-time tracking at scale.
