# RB-01: Data-Subject Request (DSAR) & Erasure

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | CS Lead + Ops Lead | 1.2 | 2026-10-16 |

| Implements | Requirement | Target | Systems |
|---|---|---|---|
| BP-09 Fulfil data-subject request | REQ-08 (≤ 7 days), LEG-01, RL-08 (ICO guidance) | Complete within **7 calendar days** (the legal maximum is 1 month) | SA-20 Shopify → SA-11 Klaviyo → SA-12 Gorgias → SA-30 Engraving Queue |

The order of systems follows the [data architecture §4](../../architecture-repository/02-architecture-landscape/strategic/data-architecture.md): **Shopify first**, then propagate. Xero and order records are **kept for 6 years** under a legal-obligation basis (LEG-06, REQ-06).

## Steps

| # | Who | Step | Record in DSAR log |
|---|---|---|---|
| 0 | CS Lead | Log the request in the DSAR log (`NB-Governance/DSAR/`, restricted) and reply with the Gorgias "DSAR acknowledgement" macro. **Day 0 starts now.** | Ref, date, type (access / erasure / rectification) |
| 1 | CS Lead | Verify identity: the request must come from the email address on the account, or the person must confirm 2 order details. Never ask for ID documents by email | Method |
| 2 | CS Lead | **Access requests:** export the Shopify customer and orders, the Klaviyo profile, Gorgias tickets and any open EQ job, then send them as an encrypted PDF/CSV through Google Drive with an expiring link | Date sent |
| 3 | Ops Lead | **Shopify (SA-20).** If the customer has an order in the last 6 years: do **not** use "Erase personal data", because it redacts order records needed under LEG-06. Instead remove saved addresses, tags and notes, set marketing consent to "unsubscribed", and add the note `Erasure restricted to legal retention until <last order + 6 yrs>`. If there are no orders in the last 6 years, use **Erase personal data** | Option used |
| 4 | Marketing Manager | **Klaviyo (SA-11):** Profile → *Delete & request GDPR erasure*. The suppression record is kept automatically so that the person is never re-mailed | Done |
| 5 | CS Lead | **Gorgias (SA-12):** delete the customer and their tickets, except the DSAR ticket itself (kept 2 years as proof of compliance) | Done |
| 6 | Ops Lead | **Engraving Queue (SA-30):** run the admin action "Purge by order" for each of the customer's orders that is still within the 90-day window | Jobs purged |
| 7 | Ops Lead | **Not erased (legal basis):** Xero ledger (no customer contacts by design, SA-10), Click & Drop shipments (DE-07, 2 years, then auto-deleted), Amazon (their controller, so refer the customer to Amazon) | Noted |
| 8 | Ops Lead | **Backups:** weekly exports age out after 13 weeks ([SA-04](../01-foundation/SA-04-export-drive.md)). If a restore happens within that window, replay the DSAR log erasures before the restored data is used | Noted |
| 9 | CS Lead | Confirm to the customer, then close the log entry with the elapsed days | Days taken |

## Quarterly drill
Run steps 0–9 on a test customer ("Drill Tester", a `+drill` email alias) with orders on the dev store and production test records. The last drill was **2026-10-01: 3 days**, which meets REQ-08. Evidence is indexed in the [governance repository](../../governance-repository/).
