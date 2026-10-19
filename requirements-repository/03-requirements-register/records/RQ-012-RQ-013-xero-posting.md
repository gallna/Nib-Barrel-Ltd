# RQ-012 → RQ-013: Xero posting granularity (superseded record)

| Status | Owner | Version | Date |
|---|---|---|---|
| RQ-012 Superseded · RQ-013 Implemented | Finance Manager | 1.2 | 2026-09-21 |

This example shows how a requirement is **superseded, not edited or deleted**. The original request stays visible, so the reasoning can be followed later, for example by a new accountant who asks why Xero has no per-order invoices.

## RQ-012 (superseded)

| Attribute | Value |
|---|---|
| Statement | Every web and Amazon order is posted to Xero as an individual sales invoice |
| Type / priority | F / — (was Must) |
| Raised by | Finance Manager, 2026-05-14 (SC-06) |
| Rationale given | "I want to find any order in Xero" |
| Status | **Superseded** by RQ-013 on 2026-06-18 |
| Why superseded | ~100 invoices/day would clutter the ledger and require a higher Xero plan. Order-level detail already lives in Shopify, the system of record for DE-03 (PR-02). The accountant confirmed that a daily summary is acceptable for VAT under MTD. |
| Decision | [ADR-005](../../../architecture-repository/05-governance-log/decision-log.md#adr-005) |

## RQ-013 (current)

| Attribute | Value |
|---|---|
| Statement | The Shopify→Xero integration posts one summary invoice per channel per day, plus payout and fee entries, so that payouts reconcile automatically |
| Type / priority | F / Must |
| Raised by | Finance Manager + external accountant, 2026-06-18 |
| Owner | Finance Manager |
| Significance | Architectural (INT-02 design; ADR-005) |
| Building blocks | SBB-03, INT-02, [SA-10 Xero configuration](../../../solutions-repository/README.md) (account mapping) |
| Acceptance | Month-end payout reconciliation ≤ 1 h/month (segment goal); every Shopify order ID can be traced from the daily summary to Shopify |
| Status | Implemented (T1 go-live 2026-09-14; first month-end 2026-09-30 took 50 minutes) |

## Change history

| Date | Record | Change | By |
|---|---|---|---|
| 2026-05-14 | RQ-012 | Raised and analysed | Finance Manager / Ops Lead |
| 2026-06-04 | RQ-012 | Fractional architect flags plan-limit and ledger-clutter concerns; accountant consulted | Fractional architect |
| 2026-06-18 | RQ-013 | Raised as the replacement | Finance Manager + accountant |
| 2026-06-18 | RQ-012 | Status → Superseded (ADR-005) | Architecture Board |
| 2026-09-21 | RQ-013 | Status → Implemented after the first week of live postings | Finance Manager |
