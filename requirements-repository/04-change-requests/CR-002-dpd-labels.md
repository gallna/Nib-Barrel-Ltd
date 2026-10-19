# CR-002: Automate DPD labels

| Status | Owner | Version | Date |
|---|---|---|---|
| Awaiting Board (2026-11-05) | Ops Lead | 1.0 | 2026-10-19 |

| Attribute | Value |
|---|---|
| Requirement | [RQ-036](../03-requirements-register/functional.md#rq-036-automatic-dpd-labels) |
| Change class | **Incremental**: a new interface and possibly a new vendor; the target architecture stays the same |
| Raised by / date | Ops Lead, 2026-09-17 |
| Capabilities | BC-04 Order Fulfilment |
| Impact statement | [RIS-001](../05-impact-assessments/RIS-001-dpd-labels.md) |
| Requested decision | Approve option A and an ADR-009 to be drafted, for delivery in January 2027 |

## Problem

Royal Mail Click & Drop (APP-04) does not create DPD labels. About 3 orders a day (high-value > £150 and next-day) are typed by hand into DPD's web portal. That breaks [PR-04](../../architecture-repository/01-architecture-capability/architecture-principles.md#pr-04-automate-the-repetitive-not-the-judgement) and means tracking for these orders never reaches Shopify or the customer automatically. Three address errors in Q3 2026 caused failed deliveries of high-value pens.

## Options (summary; details in RIS-001)

| Option | Summary | One-off | Recurring |
|---|---|---|---|
| **A** | DPD's official Shopify app for DPD orders only; Click & Drop stays for Royal Mail | £300 (setup + test) | £0 (per-label tariff unchanged) |
| B | Replace Click & Drop with a multi-carrier shipping tool for all carriers | £1.5k | ~£480/yr |
| C | Keep it manual and add a checklist | £0 | ~1 h/week of effort |

## Constraints

- **Q4 freeze:** no production change before 2027-01-05. Proposed go-live is 2027-01-18, after the Engraving Queue rollout week.
- Any new app needs a privacy and security check (PR-01) and an exit test (PR-06), following the [vendor evaluation template](../../architecture-repository/04-reference-library/templates/vendor-evaluation-template.md).
- The new interface must be one-directional from the system of record (PR-02), apart from tracking coming back, which matches the INT-03/INT-04 pattern.

## Decision record

Pending. The outcome will be logged as ADR-009 (if approved) in the AR [decision log](../../architecture-repository/05-governance-log/decision-log.md).

## Change history

| Date | Change | By |
|---|---|---|
| 2026-09-17 | Raised with RQ-036 | Ops Lead |
| 2026-09-21 | Triaged as architecturally significant (new interface, possible new vendor) | Ops Lead |
| 2026-10-08 | Added to the Board agenda for 2026-11-05 (BM-2026-10-08); RIS-001 due 2026-10-22 | Architecture Board |
| 2026-10-14 | RIS-001 completed | Fractional architect |
