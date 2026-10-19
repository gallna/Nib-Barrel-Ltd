# SA-04: Backup Shared Drive "NB-Exports"

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Ops Lead | 1.0 | 2026-09-14 |

| Realises | Continuum | System of record | Lifecycle | Contract | Change refs |
|---|---|---|---|---|---|
| TEC-07 Backup storage | Foundation | Google Drive. **The baseline here is authoritative.** | Active | [CTR-02](../contracts/contracts-register.md) | PR-06, PAT-03, STD-07, REQ-13 |

## Structure

```text
NB-Exports/                         (shared drive; external sharing blocked)
├─ shopify/weekly/YYYY-MM-DD/       products.csv, customers.csv, orders.csv, inventory.csv   ← SA-13, every Sunday
├─ shopify/monthly-full/YYYY-MM/    full orders history (first Sunday of the month)
├─ engraving-queue/weekly/          jobs.json (DE-05 within the 90-day window only)            ← SA-30 export cron
├─ xero/quarterly/                  trial balance + contacts (Finance, manual)
├─ legacy/woocommerce/              final encrypted DB export (SA-90, due 2026-12-14)
├─ legacy/mailchimp/                audience + consent log (due 2026-11-20)
└─ restore-drills/YYYY-MM-DD/       drill notes (evidence is indexed in the governance repository)
```

## Access and retention

| Role | Access |
|---|---|
| Ops Lead, MD | Manager |
| Finance Manager | Content manager (`xero/`, `legacy/woocommerce/`) |
| Matrixify service connection | Contributor (write only to `shopify/`) |
| Everyone else | None |

| Folder | Retention |
|---|---|
| `shopify/weekly/` | 13 weeks rolling, so erased customers age out within 13 weeks (see [RB-01](../runbooks/RB-01-dsar-and-erasure.md)) |
| `shopify/monthly-full/` | 6 years (REQ-06) |
| `engraving-queue/weekly/` | 4 weeks rolling (keeps the REQ-09 90-day purge meaningful) |
| `legacy/woocommerce/` | 6 years from 2026-12-14, encrypted; key at `vault:1Password/Nib & Barrel/Admin/woo-final-export-key` |
