# FreshMart Ops — Supermarket Management System

A responsive supermarket operations MVP for Indian retail workflows. Includes POS billing, inventory, purchasing, suppliers, reports, staff directory, store settings, receipt printing, CSV exports, and browser-local persistence.

## Features
- Dashboard with sales and inventory alerts.
- POS product search, editable cart, discounts, configured estimated tax, tender method recording, checkout and printable receipts.
- Product management: SKU, category, selling/cost price, tax rate, stock, reorder point, supplier, batch and expiry.
- Goods receiving, suppliers, reports, CSV exports, staff directory, JSON backup and reset.

## Run locally
Open `index.html` in a modern browser. No build step is needed. Changes persist in the same browser profile through `localStorage`.

## GitHub Pages deployment
Open **Settings → Pages**, select **Deploy from a branch**, choose `main` and `/(root)`, then save. The published URL will be shown in Pages settings once deployment completes.

## Documentation
- [PRD](docs/PRD.md)
- [Architecture](docs/ARCHITECTURE.md)
- [Test plan](docs/TEST-PLAN.md)
- [References](docs/REFERENCES.md)

## Demo limitations
This is a client-side prototype. It has no backend database, authentication, server-side role enforcement, real payment processing, barcode hardware integration, or GST filing integration. Do not use as a production POS or store sensitive data. Tax rates and calculations are configurable estimates, not a GST compliance guarantee. Check current invoice obligations with a qualified professional. Official guidance: [CBIC GST invoice rules](https://cbic-gst.gov.in/gst-invoice-rules.html).

Production security references: [OWASP Authentication Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html) and [OWASP Session Management Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Session_Management_Cheat_Sheet.html).
