# SA-90: WooCommerce Legacy Site + Database

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Ops Lead | 1.0 | 2026-10-19 |

| SBB | Continuum | System of record | Lifecycle | Contract | Change refs |
|---|---|---|---|---|---|
| SBB-13 / APP-B1 / TEC-01 | (legacy) | Shared PHP hosting (cPanel) | **Deprecated**: read-only since 2026-09-14; decommission **2026-12-14** | [CTR-14](../contracts/contracts-register.md) | ADR-004, STD-01a (Retire), RQ-040 / DSP-003 (request pending) |

| Attribute | Value |
|---|---|
| State | Admin locked; checkout disabled; reachable at `old.nibandbarrel.co.uk` for staff lookups, protected by HTTP basic auth (`vault:1Password/Nib & Barrel/Admin/woo-readonly`) |
| Plugins | 31 (4 abandoned), all auto-updates off. **Not patched further**, which is why the site must not stay up longer than needed |
| Data | Orders 2019 → 2026-09-14 (DE-03, 6-year retention, REQ-06), customers (DE-04) |

## Decommission plan (2026-12-14)

1. Final DB dump plus a CSV/XLSX export of orders (header and lines) and customers → `NB-Exports/legacy/woocommerce/`, encrypted ([SA-04](../01-foundation/SA-04-export-drive.md)).
2. Build the Finance lookup sheet (order number → date, totals, VAT, refund status). This is the alternative offered against RQ-040.
3. Restore test: open the export and spot-check 20 orders against the live read-only site.
4. Remove the `old` DNS record (SA-01), cancel hosting (CTR-14), and record completion in the [governance repository](../../governance-repository/) audit trail.

Decommissioning deletes data and makes no production change, so it is allowed during the freeze. **Open question:** Finance has asked to keep the site until 2027-03-31 (RQ-040). The request conflicts with STD-01a, so it goes to the Board on 2026-11-05 as dispensation request DSP-003. The date above stands unless DSP-003 is approved.
