# RB-02: Restore Drill from Weekly Export

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Ops Lead | 1.1 | 2026-10-06 |

| Implements | Requirement | Frequency | Last / next |
|---|---|---|---|
| PAT-03 Weekly open-format export | REQ-13 (RPO 7 days SaaS / 24 h APP-09) | Twice a year | **2026-10-06** (closed the CA-2026-001 condition) / 2027-04 |

## Steps

1. **Pick the export:** take the latest `NB-Exports/shopify/weekly/` folder ([SA-04](../01-foundation/SA-04-export-drive.md)) and note its age, which is the effective RPO.
2. **Open test:** open `products.csv`, `customers.csv` and `orders.csv` in Google Sheets. Check UTF-8 (accented engraving names display correctly) and that IDs, SKUs and order numbers are intact (exit test, PR-06).
3. **Restore test (Shopify):** import 25 products and 25 customers into the dev store `nib-and-barrel-dev` with Matrixify ([SA-13](../02-common-systems/SA-13-matrixify.md)). Compare 5 records field by field against production.
4. **Restore test (Engraving Queue):** in staging, restore `eq-staging` D1 to a point 24 h earlier using point-in-time recovery, and confirm the job count matches. Prod PITR is verified by listing the available bookmarks only (no prod restore).
5. **Timing:** record the elapsed time. Target: a usable product and customer dataset within 4 h.
6. **Clean up:** delete the imported customers from the dev store, because test data can contain real personal data.
7. **Evidence:** write the drill notes to `NB-Exports/restore-drills/YYYY-MM-DD/` and add an evidence item in the [governance repository](../../governance-repository/).

## 2026-10-06 result
Export age 1 day. 25/25 products and customers restored. Spot-check 5/5 match. D1 PITR restored in staging in 4 min. Total 2 h 10 min. **Pass.**
