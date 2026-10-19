# Non-functional Requirements, Constraints and Assumptions (NF, C, A)

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Architecture Lead (Ops Lead) | 1.3 | 2026-10-19 |

Index: [register.md](register.md). Constraints mostly originate in the [SIB legal and regulatory obligations](../../architecture-repository/03-standards-information-base/legal-and-regulatory.md) (LEG-nn). This file records *who raised them and why*; the binding wording is in the promoted `REQ-nn`.

## Non-functional (NF)

| RQ | Statement (as raised) | Raised by | Owner | Priority | Status | Promoted to | Acceptance (summary) |
|---|---|---|---|---|---|---|---|
| RQ-008 | "We must never go down on Black Friday again." Storefront ≥ 99.9% in Nov–Dec; an office internet outage must not stop online selling | MD (SC-01), after a 6-hour outage on 2025-11-28 | Ops Lead | Must | Approved | REQ-10 | Q4 2026 availability report ≥ 99.9% |
| RQ-009 | Handle 3× average volume: 300 orders/day, 70 engraved/day | Ops Lead | Ops Lead | Must | Implemented | REQ-11 | September load test passed (CA-2026-001 #8) |
| RQ-026 | All staff sign in through Google SSO + MFA wherever the product supports it | Fractional architect (SC-08) | Ops Lead | Must | Implemented | REQ-12 | 7/7 accounts; exception DSP-002 |
| RQ-027 | Weekly open-format export of every system of record; restore drill twice a year | Fractional architect (PR-06) | Ops Lead | Must | Implemented | REQ-13 | First drill 2026-10-06 |
| RQ-028 | Webhook consumers verify HMAC signatures and are idempotent on order ID | Fractional architect, during ADR-006 analysis | Ops Lead | Must | Implemented | REQ-14 | Replay test (CA-2026-002 #2) |
| RQ-038 | Engraved orders dispatched within 2 working days, including peak | MD (GOL-01) | Ops Lead | Must | Approved | — (measured as GOL-01) | ≥ 95% within 2 working days, Nov 2027 |
| RQ-039 | Fix the font-picker colour contrast in the engraving preview (WCAG 2.2 AA, 1.4.3) | CA-2026-002 condition | Ops Lead | Must | Approved, due before 2027-01-11 | — (fix within REQ-03) | Contrast ≥ 4.5:1; re-checked in CA-2026-004 |

## Constraints (C)

| RQ | Statement (as raised) | Source | Owner | Status | Promoted to |
|---|---|---|---|---|---|
| RQ-020 | Storefront and engraving preview meet WCAG 2.2 AA | LEG-08 | Ops Lead | Approved (partially met: RQ-039 open) | REQ-03 |
| RQ-021 | Checkout states clearly that personalised items are exempt from the 14-day cancellation right | LEG-04 | Ops Lead | Implemented | REQ-04 |
| RQ-022 | Financial and order records retained for 6 years in MTD-compatible software | LEG-06, external accountant | Finance Manager | Implemented | REQ-06 |
| RQ-023 | Payment card data never enters any system we operate (SAQ A) | LEG-03 | Finance Manager | Implemented | REQ-07 |
| RQ-024 | Marketing consent is unticked by default and recorded with source and timestamp; DSAR/erasure is completed within 7 days | LEG-01, LEG-02, Marketing Manager | Marketing Manager | Implemented | REQ-08 |
| RQ-025 | Engraving text (often names and dates) is purged 90 days after delivery | LEG-01 minimisation, fractional architect | Ops Lead | Implemented | REQ-09 |

### RQ-029 Amazon stock sync and dispatch confirmation
**Statement:** Amazon stock reflects Shopify within 15 minutes, and dispatch confirmation with valid tracking is sent within the stated handling time.
**Rationale:** Amazon Selling Partner policies (LEG-07); late confirmation and cancellations affect the account health score.
**Source:** Ops Lead, Amazon policy review 2026-07-02 · **Owner:** Ops Lead · **Priority:** Must · **Status:** Approved (in progress) · **Promoted to:** **REQ-15** via [CR-001](../04-change-requests/change-request-register.md)
**Building blocks:** APP-08, INT-01, SA-22 · **Verification:** CA-2026-003 (planned 2026-10-28, blocked until investigation INV-2026-01 closes)
**Note:** Two oversells on 2026-10-03 during the connector cut-over are under investigation (INV-2026-01, in the [governance repository](../../governance-repository/README.md)). Interim control: a stock buffer of 1 on SKUs with ≤ 3 units.

## Assumptions (A)

Assumptions are recorded with a validation date. If an assumption fails, the result is a new requirement or a roadmap risk.

| RQ | Assumption | Depends on it | Owner | Validate by | Status |
|---|---|---|---|---|---|
| RQ-041 | Two seasonal fulfilment operatives can be hired and trained for Nov–Dec | REQ-11 (staffing plan), RQ-038 | Ops Lead | 2026-10-23 | Approved: one confirmed, one interviewing (2026-10-19) |
| RQ-042 | Engraved orders stay ≤ 30% of all orders through 2027, so one laser (TEC-03) is enough | TEC-03 capacity, REQ-11 (70 engraved/day) | Ops Lead | Quarterly (next 2027-01-14) | Approved: 22% in 2025, 24% in Q3 2026 |
