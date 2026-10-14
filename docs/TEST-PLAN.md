# Test Plan

## Manual smoke tests
1. Load `index.html` and verify dashboard plus demo-mode notice.
2. Open POS, search by name/SKU, and add two products.
3. Change quantity, remove a line, apply discount and verify subtotal/tax/total.
4. Try a discount larger than subtotal and verify the discount is capped.
5. Complete checkout; verify transaction is recorded and stock decremented.
6. Add/edit a product, refresh, and verify browser-local persistence.
7. Adjust stock with positive and negative changes; negative final stock must be rejected.
8. Receive goods; confirm stock increases and receipt appears in purchasing.
9. Export inventory CSV, transaction CSV and JSON backup.
10. Verify navigation and forms at mobile width.
11. Reset demo data and verify original sample products return.

## Current automated checks
GitHub Actions verifies required project files and checks inline JavaScript syntax with Node.js.

## Known test gaps
- No browser automation runner is currently included.
- No API/database integration tests because the MVP has no backend.
- No authentication, authorization, payment, concurrency or hardware tests.
- Tax math is a simplified estimate and needs review for the target business's tax/pricing model.
