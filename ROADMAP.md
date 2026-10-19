# BookNow Roadmap

BookNow currently runs entirely on mock data in both the web app (`web/`) and the mobile app (`mobile/`). This roadmap moves it from a clickable proof of concept to a working booking platform. All development uses made-up sample providers and customers; no real personal data.

## Phase 0: Web app updates and code cleanup
- [ ] Add a "Demo, sample data" banner to the live web app, and stop the hard-coded counters ("847 bookings this week", "75 providers live") looking like real usage
- [ ] Bring the web provider side up to par with mobile: split `ProviderDashboard` into separate Bookings, Slots and Account screens like `mobile/app/(provider-tabs)/`
- [ ] Match the customer flow between web and mobile (activity calendar view, services list, help screens)
- [ ] Remove the duplicate `web/vite.config.js` (`vite.config.ts` is the real config)
- [ ] Code-split routes to shrink the 695 kB main bundle (Vite warns above 500 kB)
- [ ] Move repeated inline styles into shared style helpers or a styling library
- [ ] Update the README project structure (it lists 5 screens; the web app now has 13 plus TanStack Router)
- [ ] Responsive check of every web screen at phone, tablet and desktop widths

## Phase 1: Foundations
- [ ] Shared package for types, mock data and the chat engine, so `web/` and `mobile/` stop duplicating `data.ts` and `chat-engine.ts`
- [ ] Set up npm workspaces at the repo root
- [ ] ESLint + Prettier config shared across both apps
- [ ] Unit tests (Vitest for web, Jest for mobile) for booking and slot logic
- [ ] GitHub Actions CI: type-check, lint and test on every push

## Phase 2: Backend
- [ ] Choose and set up the backend (Supabase or Node + PostgreSQL)
- [ ] Database schema: users, providers, services, time slots, bookings, waitlist
- [ ] Seed script with fake Halifax providers (replaces the hard-coded mock data)
- [ ] API layer used by both web and mobile
- [ ] `.env.example` files documenting required config

## Phase 3: Real accounts and bookings
- [ ] Email sign-up / login for customers and providers (replace mock auth)
- [ ] Customer booking flow writes real bookings; confirmation and cancellation rules (2-hour cutoff)
- [ ] Waitlist: auto-notify the next customer when a slot frees up
- [ ] Provider dashboard reads and updates live data (go live / pause, accept / decline, slot editor)

## Phase 4: Real-time
- [ ] Live slot availability on the map (subscriptions instead of polling)
- [ ] In-app notifications for booking requests, confirmations and waitlist openings
- [ ] Push notifications on mobile (expo-notifications)

## Phase 5: Provider billing
- [ ] $1-per-confirmed-booking billing for providers (Stripe test mode)
- [ ] Billing history backed by real data
- [ ] Monthly invoice summary for providers

## Phase 6: Polish and release
- [ ] Accessibility pass (screen reader labels, contrast, keyboard navigation on web)
- [ ] Loading, empty and error states on every screen
- [ ] Offline handling on mobile
- [ ] Search and filtering improvements (distance, price, rating)
- [ ] Web deploy to Vercel with a preview build per pull request
- [ ] Mobile builds with EAS (internal testing track)
