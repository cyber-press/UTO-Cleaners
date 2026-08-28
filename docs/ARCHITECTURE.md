# Production architecture

## Proposed stack

- Next.js with TypeScript
- Tailwind CSS compiled during the production build
- PostgreSQL
- Prisma ORM
- Auth.js or a compatible managed authentication service
- Paystack for payments
- Resend or an equivalent provider for transactional email
- WhatsApp Business Platform where automated messaging is required
- Vercel for the application and a managed PostgreSQL provider
- Sentry-compatible error monitoring and privacy-conscious analytics

## Main domains

### Catalogue

Branches, service categories, services, prices, turnaround estimates, availability, and delivery zones are database-backed and manageable by authorized staff.

### Customers and bookings

Bookings retain customer contact information, pickup address, preferred branch, pickup window, notes, selected services, consent records, and communication history.

### Orders

Each order has an internal identifier and a separate non-sequential tracking code. Status transitions are timestamped and attributed to the responsible staff account.

### Payments

The backend creates payment attempts, calculates totals from authoritative prices, verifies provider callbacks, processes signed webhooks idempotently, and records reconciliation data.

### Operations

Staff accounts use role-based authorization. Sensitive actions produce immutable audit events. Operational screens support search, filtering, controlled status changes, and exports.

## Initial data model

- User
- Role
- Customer
- Branch
- ServiceCategory
- Service
- DeliveryZone
- PickupWindow
- Booking
- Order
- OrderItem
- OrderStatusEvent
- Payment
- ContactSubmission
- NewsletterSubscription
- Notification
- AuditLog

## API boundaries

- `POST /api/bookings`
- `POST /api/contact`
- `POST /api/newsletter`
- `POST /api/payments/initialize`
- `GET /api/payments/verify`
- `POST /api/webhooks/paystack`
- `GET /api/tracking/:trackingCode`
- Authenticated staff endpoints for catalogue, branches, orders, payments, reporting, and users

All mutation endpoints validate requests on the server. Public endpoints use rate limiting and abuse protection. Administrative endpoints require authentication and explicit authorization.

## Security baseline

- Secrets stored only in managed environment configuration
- Server-side validation and output encoding
- Secure cookies and session rotation
- Least-privilege staff roles
- Content Security Policy and standard security headers
- Request size limits and rate limiting
- Paystack signature verification and webhook idempotency
- Audit logs for privileged actions
- Automated dependency and code-quality checks
- Encrypted managed database, backups, and tested recovery procedure

## Deployment flow

1. Feature work is committed to the rebuild branch.
2. Automated checks run for every change.
3. A staging preview is created for acceptance testing.
4. Database migrations are reviewed and applied to staging.
5. Payment and notification flows are tested with sandbox credentials.
6. Approved changes are merged and promoted to production.
