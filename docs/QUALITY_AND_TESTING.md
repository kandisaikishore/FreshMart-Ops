# Operations QA, Backup, and Data-Integrity Guide

FreshMart Ops is a browser-based supermarket operations MVP. The README states that data persists in the same browser profile using `localStorage`; this is not a shared or server-backed database.

## Run locally

Open `index.html` in a modern browser. For static hosting, follow the README's GitHub Pages instructions and verify the deployment workflow succeeded before describing the site as live.

## Critical workflows to test

- POS product search, cart quantity changes, discounts, tax estimates, checkout, and receipt printing
- Product create/edit/delete and SKU uniqueness where required
- Goods receiving and stock updates
- Reorder-point and expiry-date boundaries
- CSV exports and JSON backup/restore
- Staff, supplier, store settings, and reports where implemented
- Browser refresh, malformed saved state, and storage quota/security failures

## Data integrity

Test that a completed checkout updates inventory consistently and that repeated submissions do not double-decrement stock. Failed operations must not leave a false success state. Use deterministic fixture products and test amounts.

## Demo and financial boundary

Tax is configured as an estimate, and tender methods are recorded by the prototype; do not imply that a payment gateway actually processes funds. Browser-local storage can be cleared or lost and is not a secure multi-user persistence layer. Do not use fictional/demo totals for real financial decisions.

## Backup and recovery

Before destructive reset tests, export a JSON backup. Verify valid backup/restore round trips and reject malformed imports before replacing current data. Make reset actions explicit and test that cancellation does not clear data.

## Pull-request checklist

- [ ] Test core POS and inventory workflows.
- [ ] Verify CSV/JSON export behavior and malformed imports.
- [ ] Check responsive layout and keyboard accessibility.
- [ ] Confirm data remains labeled as demo/local where appropriate.
- [ ] Record manual and automated checks accurately.
