# ParkPay

Pay-as-you-park: live slot availability, a fee calculator by rate blocks, card payments, sequential invoices and monthly rental contracts.

> **Status: in development.** This repo is the plan and the write-up; the interactive demo is being built next.
> **Demo preview:** https://julynard.github.io/parkpay/ (becomes the live demo when it ships).

Part of [Julynard Tago-on's portfolio](https://julynardtago-on.netlify.app/#projects). Based on the parking platform at CoreProc where I built the session payment API, invoicing and partner integrations.
Client code is private, so this is a clean-room demo with fictional data. No client names or real data.

## What the demo will show

- [ ] Parking areas with **live available slots** (simulated, with a "cached 60s" badge and countdown)
- [ ] Start a session; the fee calculator applies operating-hour rate blocks
- [ ] Pay with a saved card, or toggle "card declined" to see the failure path
- [ ] Receipt with a **sequential invoice number that resets** at a configurable maximum
- [ ] Monthly rental contract: create, monthly periods, renewal, failed-payment retry

Every key action will have an **"In production"** note explaining how the real system does it.

## How the production system works

The real system runs on Laravel. The demo simulates these behaviours in the browser so it can stay fast and always on.

- Laravel REST API for the mobile app (OAuth2 via Passport) plus a token-protected partner API
- Card charges through a payment-gateway repository with swappable fakes for QA
- Third-party slot availability cached for 60 seconds
- Polymorphic transactions so reservations and walk-in sessions share one payment model
- Async partner sync (REST uploads + a daily FTPS file) through Horizon jobs

## Planned stack

- Vue 3 + TypeScript + Vite
- Tailwind CSS v4
- Pinia (state saved in the browser, with a **Reset demo** button)
- Vitest for the domain logic, ESLint + Prettier + `vue-tsc` in CI
- GitHub Actions → GitHub Pages (free, always on)

## Roadmap

1. Project scaffold, CI (lint, type-check, test, build) and GitHub Pages deploy
2. Domain logic with Vitest tests
3. UI with seeded data, guided steps and "In production" notes
4. Screenshot/GIF in this README and the live demo link

## Author

**Julynard Tago-on**, Laravel / PHP full-stack engineer · [Portfolio](https://julynardtago-on.netlify.app) · [GitHub](https://github.com/Julynard) · [LinkedIn](https://www.linkedin.com/in/julynard-tago-on/)

## License

[MIT](LICENSE)
