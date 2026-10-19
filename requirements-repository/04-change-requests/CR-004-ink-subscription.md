# CR-004: Ink refill subscription

| Status | Owner | Version | Date |
|---|---|---|---|
| Awaiting Board (2026-11-05) | Marketing Manager | 1.0 | 2026-10-19 |

| Attribute | Value |
|---|---|
| Requirement | [RQ-035](../03-requirements-register/functional.md#rq-035-ink-refill-subscription) |
| Change class | **Incremental** (new vendor, new recurring-order flow); the capability map does not change |
| Raised by / date | Marketing Manager, 2026-09-03 |
| Capabilities | BC-06 Sales Channel Management, BC-07 Marketing & Customer Engagement, BC-09 Payments & Finance |
| Impact statement | [RIS-002](../05-impact-assessments/RIS-002-ink-subscription.md) |
| Requested decision | Add it to the ADM cycle 3 scope (Phase A starts Q1 2027); do not deliver it in this cycle |

## Business case (summary)

Refills and ink are 31% of orders and highly repetitive. A subscription with 10% off at a 5% take-up of refill customers is estimated at £18k/year in revenue and a smoother monthly order profile. It also meets the need behind the rejected [RQ-033](../03-requirements-register/records/RQ-033-store-card-details.md) (quick reorders) without us ever holding card data.

## Why not now

1. The Q4 freeze, then the Engraving Queue rollout and CR-002 in January, already fill the change capacity of a team with no developers.
2. RIS-002 found open questions that need Phase B/C work: stock reservation for subscriptions (GOL-03), subscription consent and cancellation under the Consumer Contracts Regulations (LEG-04), and how recurring orders post to Xero (ADR-005).
3. It adds a vendor that touches the DE-03 Order system of record, so under the charter it needs an ADR in any case.

## Change history

| Date | Change | By |
|---|---|---|
| 2026-09-03 | Raised with RQ-035 | Marketing Manager |
| 2026-09-07 | Triaged as architecturally significant (new vendor touching a system of record) | Ops Lead |
| 2026-10-08 | Added to the Board agenda for 2026-11-05 (BM-2026-10-08); RIS-002 due 2026-10-22 | Architecture Board |
| 2026-10-14 | RIS-002 completed | Fractional architect |
