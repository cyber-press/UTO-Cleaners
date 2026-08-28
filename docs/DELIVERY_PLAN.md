# UTO Cleaners delivery plan

## Phase 1: Foundation

- [ ] Confirm business requirements and production content
- [ ] Scaffold Next.js with TypeScript and production Tailwind build
- [ ] Add linting, formatting, tests, and CI checks
- [ ] Build reusable layout, navigation, footer, buttons, forms, and feedback components
- [ ] Migrate public pages while preserving the established brand
- [ ] Add metadata, sitemap, robots directives, social cards, and structured data
- [ ] Establish staging and production environments

## Phase 2: Core backend

- [ ] Design PostgreSQL schema and migrations
- [ ] Add customers, branches, service categories, services, and pricing
- [ ] Add bookings, orders, order items, pickup windows, and status history
- [ ] Generate unique, non-sequential public tracking codes
- [ ] Connect booking form with server-side validation
- [ ] Connect contact and newsletter submissions
- [ ] Add rate limiting, anti-spam protection, structured logging, and error handling

## Phase 3: Payments and tracking

- [ ] Calculate order totals exclusively on the server
- [ ] Initialize Paystack transactions securely
- [ ] Verify callback transactions on the server
- [ ] Verify webhook signatures
- [ ] Add webhook idempotency and payment reconciliation
- [ ] Replace simulated tracking with persisted order status history
- [ ] Add booking, payment, and status notifications

## Phase 4: Staff operations

- [ ] Add secure staff authentication
- [ ] Define administrator, manager, attendant, and courier permissions
- [ ] Build order list, filters, search, and order-detail views
- [ ] Add controlled status transitions
- [ ] Add catalogue, pricing, branch, service-area, and pickup-window management
- [ ] Add staff action audit logs
- [ ] Add reporting and CSV export

## Phase 5: Launch readiness

- [ ] Complete mobile, browser, accessibility, and keyboard testing
- [ ] Add unit, integration, and end-to-end tests
- [ ] Test payment success, failure, replay, and delayed-webhook scenarios
- [ ] Configure monitoring, alerts, analytics, backups, and recovery procedures
- [ ] Add privacy, terms, cancellation, refund, and garment-care policies
- [ ] Perform staging acceptance testing
- [ ] Configure custom domain and production release

## Acceptance criteria

A release is production-ready only when:

- Bookings and payments create verifiable database records
- Tracking displays persisted status history and never generated demo data
- Staff access is authenticated and authorized by role
- Prices and totals cannot be changed from the browser
- Payment webhooks are signature-verified and idempotent
- Contact and subscription requests are stored or delivered reliably
- Critical workflows have automated tests
- Monitoring, backups, security headers, and rate limits are enabled
- Placeholder branch and policy content has been replaced
