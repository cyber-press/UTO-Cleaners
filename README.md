# UTO Cleaners - Company-Grade Rebuild

This branch is the staging area for rebuilding UTO Cleaners as a production-ready web application.

## Goals

- Maintainable frontend architecture
- Real bookings and order tracking
- PostgreSQL-backed customer, service, order, and payment records
- Paystack payment initialization and verified webhooks
- Secure staff dashboard with role-based access
- Transactional email and optional WhatsApp notifications
- Server-side validation, rate limiting, audit logs, monitoring, and backups
- Accessibility, SEO, responsive design, automated tests, and staged deployment

## Delivery phases

1. Foundation and application architecture
2. Database, services catalogue, bookings, and contact capture
3. Checkout, Paystack integration, and real order tracking
4. Staff dashboard and order operations
5. Notifications, analytics, security hardening, testing, and launch

## Environment strategy

- `main`: current public site
- `company-grade-rebuild`: development and staging work
- Production release only after acceptance testing

## Required configuration

Copy `.env.example` to `.env.local` and provide development credentials. Never commit real credentials.

## Decisions still required

- Final business name and brand assets
- Complete branches, addresses, hours, and coverage areas
- Approved services, prices, turnaround times, and pickup fees
- Paystack credentials
- Sender email and domain
- WhatsApp automation requirements
- Initial staff roles and administrator account
- Privacy, cancellation, refund, and garment-care policies
