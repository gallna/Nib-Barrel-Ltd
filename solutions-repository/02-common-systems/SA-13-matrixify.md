# SA-13: Matrixify Export & Import Jobs

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Ops Lead | 1.2 | 2026-10-06 |

| SBB | Continuum | System of record | Lifecycle | Contract | Change refs |
|---|---|---|---|---|---|
| SBB-12 / INT-10 | Common systems | Matrixify (Shopify app). **The baseline here is authoritative.** | Active | [CTR-07](../contracts/contracts-register.md) | PAT-03, REQ-13, minor decision 2026-05-02 |

## A. Scheduled exports (PAT-03)

```yaml
destination: Google Drive → NB-Exports/shopify/ (SA-04)
format: CSV (UTF-8), one file per sheet   # open format (PR-06)
jobs:
  - name: weekly-core
    schedule: "Sundays 03:00 Europe/London"
    sheets: [Products, Metafields (SA-33), Smart/Custom Collections, Customers, Orders (last 8 days), Inventory levels]
    path: weekly/{YYYY-MM-DD}/
  - name: monthly-full-orders
    schedule: "1st Sunday of month 04:00"
    sheets: [Orders (all time), Refunds, Transactions (references only, no card data)]
    path: monthly-full/{YYYY-MM}/
alerting: email ops@ on failure; the Ops Lead checks the folder on Monday mornings
```

## B. Import templates: supplier product onboarding (BP-01)

Matrixify templates replace a custom "SKU import script". Under [PR-03](../../architecture-repository/01-architecture-capability/architecture-principles.md) only engraving is approved for custom code, so supplier data is mapped by configuration instead.

| Template | Supplier group | Maps | Notes |
|---|---|---|---|
| `import-fountain-pens.xlsx` | 6 main pen brands | Title, vendor, SKU, barcode, price, metafields `pen.nib_size`, `pen.fill_system`, `pen.material`, `engraving.eligible`, `engraving.max_chars` | Rows without `engraving.max_chars` are rejected for engravable SKUs |
| `import-inks.xlsx` | Ink makers | SKU, volume, colour family, `ink.type` | |
| `import-refills.xlsx` | Ballpoint/rollerball refills | SKU, compatibility list | |

Templates are stored at `NB-Exports/templates/`. The column dictionary is [SA-33](../04-organisation-specific/SA-33-pen-product-data-model.md).

## Restore
Restore is tested with [RB-02](../runbooks/RB-02-restore-drill.md). The last drill was 2026-10-06 (closes the CA-2026-001 condition).
