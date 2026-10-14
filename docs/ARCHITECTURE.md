# Architecture — FreshMart Ops

## Current prototype
The app is a static single-page application in `index.html` with responsive CSS, JavaScript modules for navigation/POS/inventory/reporting and `localStorage` persistence. Records include products, transactions, suppliers, goods receipts, staff, settings and activity notes. It has no API or database server; demo charts are illustrative.

## Recommended production architecture

```text
Browser UI (web app)
        | HTTPS JSON API
        v
Backend service (Spring Boot or FastAPI)
  - Authentication and server-side RBAC
  - POS/checkout service
  - Inventory and stock movement service
  - Purchasing/supplier service
  - Reporting and audit event service
        |
        v
PostgreSQL
  products, categories, suppliers, batches, stock movements,
  sales, sale lines, payments, purchase orders, receipts,
  users, roles, permissions, audit events
```

## Production design considerations
- Make checkout atomic: validate and decrement inventory in a database transaction with row locks or optimistic concurrency control.
- Store price, cost, discount, tax rate/amount, SKU and product description snapshots on each sale line. Reports must not change when catalogue values are edited.
- Support batch-level inventory for perishables and FEFO (first-expiry-first-out) recommendations.
- Use unique invoice sequence constraints per store and financial year.
- Enforce server-side authorization on every sensitive operation. Hiding a button is not access control.
- Use password hashing and secure session lifecycle; require HTTPS and invalidate sessions on logout.
- Use compliant payment provider references only; never store raw card credentials.
- Use database migrations, encrypted backups, tested restores and monitoring.

## Deployment
GitHub Pages can host the static prototype, but not the backend or database. Production deployment needs an API host, managed PostgreSQL and secrets configured outside source control.
