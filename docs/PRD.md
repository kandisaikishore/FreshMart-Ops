# Product Requirements Document — FreshMart Ops

## Product summary
FreshMart Ops is a supermarket operations MVP for Indian retail stores, focused on checkout, inventory visibility, supplier operations and reports.

## Users
- **Administrator:** store profile, staff and master data.
- **Manager:** inventory, purchasing, suppliers and reports.
- **Cashier:** product search, cart, checkout and receipt.
- **Inventory associate (future):** receive deliveries, stock counts and expiry tracking.

The prototype has a staff directory but does not authenticate users or enforce roles.

## Functional requirements
### FR-01 Point of Sale
Search products by name or SKU, filter categories, add/remove products, adjust quantities, prevent quantities above current stock, apply discount, estimate tax from configured percentages, record tender method, decrement stock and print receipt.

### FR-02 Product catalogue
Create/edit products with SKU/barcode, name, category, selling price, cost, tax rate, quantity, reorder point, supplier, batch, expiry and emoji/icon.

### FR-03 Inventory
Flag low stock and soon-to-expire items, allow stock adjustment with a reason and update stock on goods receipt.

### FR-04 Purchasing and suppliers
Keep supplier contact details/payment terms and record goods received with product, quantity, cost, batch and expiry. Purchase approvals and vendor integrations are out of scope.

### FR-05 Reporting
Show transaction ledger, payment method totals, top-selling products, inventory cost estimate, CSV exports and estimated gross margin. Current prototype estimates margin using current product costs, not historical cost snapshots.

### FR-06 Store settings
Store name/address, optional GSTIN, receipt footer and default reorder threshold. GSTIN is a plain field and is not verified against government services.

### FR-07 Data
Persist demo state in browser `localStorage`; provide JSON backup and reset. Data is not shared between browsers or devices.

## Non-functional requirements
- Responsive desktop/tablet/mobile UI.
- Keyboard-accessible controls and visible focus styles.
- Prevent negative inventory and clamp discount to the subtotal.
- Do not place secrets in client-side source.
- Production requires server-side authorization, transactional database writes, audit trail, backups, monitoring and tested restore procedures.

## Business rules in MVP
- Currency: INR.
- Checkout decrements inventory after validating quantities.
- Estimated tax is sum of line price × quantity × configured percentage. Tax-inclusive vs tax-exclusive behavior must be decided for the actual business.
- Expiry alert window: today through the next seven days.
- Demo transactions are illustrative, not accounting records.

## Acceptance criteria
1. Modules are navigable on desktop and mobile.
2. POS cart totals update after quantity/discount edits.
3. Checkout records transaction and decrements inventory.
4. Product changes persist after refresh in the same browser.
5. Goods receiving increases stock and records a receipt.
6. Inventory/transactions export to CSV and state can be backed up to JSON.
7. Low-stock, expiry, empty and demo-mode states are visible.
8. Documentation explains missing backend, auth, payment integration and legal tax validation.

## Out of scope
Live payments, loyalty accounts, online ordering, delivery management, accounting integrations, GST return filing, e-invoice/e-way bill integration, government verification, multi-store synchronization and production authentication.

## References
- CBIC GST invoice rules: https://cbic-gst.gov.in/gst-invoice-rules.html
- OWASP Authentication Cheat Sheet: https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html
- OWASP Session Management Cheat Sheet: https://cheatsheetseries.owasp.org/cheatsheets/Session_Management_Cheat_Sheet.html
