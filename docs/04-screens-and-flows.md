# Screens and flows

25 screens across five journey stages. Every screen exists in `design/fixin10-infinite-canvas.html`; all of them are also implemented in `design/fixin10-interactive-prototype.html`, where the full path is clickable.

## Journey stages (screen list)

**1. Getting started**

| Screen | Purpose |
|---|---|
| Splash | Brand moment; auto-advances after ~1.5s |
| Onboarding | Value prop; "Get started" or skip |
| Login | Phone entry, +91, terms |
| Verify OTP | 4-digit code, auto-read hint, resend timer |
| Set address | Search, map pin, current location, saved home |

**2. Find and book**

| Screen | Purpose |
|---|---|
| Home | Services, top pros, the "~10 min" promise |
| Service list | The trade's tasks with hourly prices and "Instant" tags |
| Service detail | What's included, how pricing works, top pro preview |
| Schedule | Now vs Schedule, day and window chips, address row |
| Review & pay | Estimate, coupon, payment method; pay after service |

**3. Service day**

| Screen | Purpose |
|---|---|
| Matching | Live progress ring; three pros pinged with offer timers; cancel |
| Live tracking | Map, ETA, steps, call / chat / share / SOS |
| Start code | 4-digit code the pro enters; free cancellation until then |
| In progress | Live hourly meter, extend, note, call / chat, raise issue |
| Bill | Actual hours (15-min steps), coupon, tip, pay |
| Rate & review | Stars, quick tags, note, submit |

**4. Manage**

| Screen | Purpose |
|---|---|
| Bookings | Ongoing vs Completed; receipts; rebook |
| Receipt | Timeline, full breakdown, download, rebook, chat |
| Chat | Conversation with the pro |
| Wallet | Balance, coupons, activity (refunds, referrals) |
| Membership | FixIn10 Plus plans and benefits |

**5. Account and help**

| Screen | Purpose |
|---|---|
| Referral | Code, share, rewards status |
| Profile | Identity, shortcuts (wallet / Plus / invite), settings rows |
| Settings | Notification toggles, language (English / हिंदी), legal |
| Support | Common topics, chat / call / SOS, recent tickets |

## The happy path (as implemented in the prototype)

Splash -> Onboarding -> Login -> Verify -> Address -> Home -> pick a trade -> Service list -> Service detail -> Schedule -> Review & pay -> Matching (auto) -> Tracking ("Demo: pro has arrived") -> Start code ("Demo: code entered") -> In progress (live meter) -> Bill (choose tip, pay) -> Rate & review -> back Home with the booking saved in Bookings, the receipt updated, and amounts carried through the money flow.

## State coverage

| State | Where it appears |
|---|---|
| Loading | OTP sending and verifying (button spinners); matching progress ring; paying state on the bill |
| Empty | Bookings -> Ongoing tab ("No ongoing bookings" with a Book now CTA) |
| Error / recovery | Represented in the design system (canvas row 2: payment retry pattern); toasts handle transient notices |
| Success | Paid toast, review toast, welcome-to-Plus toast |
| Edge | Cancelled booking row with refund; coupon applied vs removed; tip none / ₹50 / ₹100 |

## Practical notes

- **Timers:** the in-progress meter ticks live in the prototype; the bill is computed from actual elapsed time in 15-minute steps (minimum 1 hour) plus visit fee, coupon and tip.
- **Amounts:** sample numbers stay consistent through the flow (₹498 labour estimate, ₹49 visit fee, -₹50 coupon, totals update live; estimated ₹497 vs final ₹435-485 depending on time worked and tip).
- **Copy:** Indian names and cities (Ananya, Rajesh, Imran, Lakshmi; Bengaluru / Indiranagar), ₹ currency, UPI payments.
