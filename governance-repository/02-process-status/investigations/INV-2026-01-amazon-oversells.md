# INV-2026-01: Amazon Oversells during Connector Cut-over

| Status | Opened | Raised by | Lead investigator | Target close |
|---|---|---|---|---|
| **Open**: root cause identified, actions in progress | 2026-10-05 | Operations Lead | Fractional architect | 2026-10-26 |

**Process:** business control. **Related:** GOL-03 (no oversells), REQ-15 / RQ-029, WP-02, SBB-08, SA-22 (connector configuration baseline in the [solutions repository](../../../solutions-repository/)). **Blocks:** CA-2026-003.

## 1. What happened

Two Amazon orders were accepted for SKUs whose last unit had already been sold on the web shop. Both customers had their orders cancelled and refunded on 2026-10-04 and received an apology with a discount code. Amazon recorded 2 seller-cancellations against our account metrics.

## 2. Timeline

| Time (BST) | Event |
|---|---|
| 2026-10-03 08:00 | Marketplace connector switched from the 20-SKU trial to the full catalogue (~420 SKUs) |
| 2026-10-03 08:00 | Stock buffer left at **0** for all SKUs (the trial setting) |
| 2026-10-03 13:10 | The connector's Amazon SP-API authorisation failed to refresh. Stock sync stopped; nobody was alerted. |
| 2026-10-03 13:22 | Web order takes the last unit of SKU FP-0412 |
| 2026-10-03 13:41 | Web order takes the last unit of SKU INK-0088 |
| 2026-10-03 13:30–13:52 | Amazon accepts 1 order each for FP-0412 and INK-0088 |
| 2026-10-03 13:55 | The connector retried and refreshed its authorisation; sync resumed (45 minutes without sync) |
| 2026-10-04 09:15 | Ops Lead finds the oversells during the morning stock check |
| 2026-10-05 10:00 | Investigation opened; fractional architect assigned |
| 2026-10-05 11:30 | Interim containment applied (§4) |
| 2026-10-08 | Reported to the Board ([BM-2026-10-08](../../03-audit-information/board-minutes/BM-2026-10-08.md)) |

## 3. Root cause (so far)

| # | Cause | Type |
|---|---|---|
| 1 | Stock buffer of 0 on low-stock SKUs. Any sync delay therefore exposes the last unit on both channels. | Configuration |
| 2 | Authorisation refresh failures are not alerted. The connector's failure-email setting was off by default. | Configuration / vendor |
| 3 | The WP-02 acceptance tests covered normal sync latency but not a sync outage | Test coverage |
| 4 | REQ-15 ("≤ 15 minutes") states the latency target but not the behaviour when sync fails | Requirement gap |

The 15-minute target (REQ-15) was met at all times **while the sync was running**. The failure was in detecting and containing an outage, not in the design of INT-01.

## 4. Interim containment (in place since 2026-10-05)

- A stock buffer of **1** on every SKU with ≤ 3 units on hand: Amazon shows 0 when only 1 unit is left. This change is recorded in the SA-22 configuration baseline.
- The Ops Lead checks the connector sync log at 09:00 and 14:00 every working day.
- Vendor support ticket raised, asking why the authorisation refresh failed and whether there is a webhook or email alert.

No further oversells have occurred since 2026-10-05.

## 5. Actions

| # | Action | Owner | Due | State |
|---|---|---|---|---|
| INV-2026-01/A1 | Turn on the connector's failure-email alerts to `ops@`; test by revoking and re-granting the authorisation in the sandbox | Ops Lead | 2026-10-21 | Open |
| INV-2026-01/A2 | Get the vendor's root-cause analysis for the refresh failure | Ops Lead | 2026-10-23 | Open: vendor acknowledged 2026-10-06 |
| INV-2026-01/A3 | Add "sync outage of 60 minutes" and "authorisation expiry" scenarios to the CA-2026-003 checklist | Fractional architect | 2026-10-26 | Open |
| INV-2026-01/A4 | Propose a permanent stock-buffer rule and an outage behaviour for REQ-15 (new requirement record and CR in the requirements repository) | Ops Lead | 2026-10-26 | Open |
| INV-2026-01/A5 | Decide whether 2 seller-cancellations need any action under Amazon policy (LEG-07) | Ops Lead | 2026-10-21 | Done 2026-10-12: within the account health limits, no action needed |

## 6. Closure criteria

Actions A1–A4 are done, the evidence is filed, and the result is reported to the Board on 2026-11-05. Closing the investigation unblocks CA-2026-003.
