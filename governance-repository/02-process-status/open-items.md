# Open Governance Items

| Status | Owner | As at | Next update |
|---|---|---|---|
| Live | Architecture Lead | 2026-10-19 | After Board 2026-11-05 |

This is the live state of every governance process. Rows are updated as work progresses. A closed row stays in the **Recently closed** table for one quarter and then moves to the [audit trail](../03-audit-information/audit-trail.md). Outcomes are recorded in the AR [governance log](../../architecture-repository/05-governance-log/), not here.

## Summary

| Process | Open | Awaiting Board 2026-11-05 | Overdue |
|---|---|---|---|
| Change requests | 3 | 2 | 0 |
| Dispensation requests | 1 | 1 | 0 |
| Compliance assessments (scheduled) | 3 | — | 0 |
| Investigations | 1 | 1 (report) | 0 |
| Governance actions | 6 | — | 0 |

## 1. Change requests needing governance

Change requests live in the [requirements repository](../../requirements-repository/). Only their governance state is tracked here.

| CR | Title | Class | Source | State | Next step | Owner |
|---|---|---|---|---|---|---|
| CR-002 | Automate DPD labels | Incremental | RQ-036 | RIS-001 complete | **Board 2026-11-05.** Recommendation: ADR-009, deliver Jan 2027 after the freeze | Ops Lead (raised by them, so not a minor decision) |
| CR-004 | Ink refill subscription | Incremental | RQ-035 | RIS-002 complete | **Board 2026-11-05.** Recommendation: put in ADM cycle 3 scope, not now | Marketing Manager |
| CR-005 | Font-picker contrast fix | Simplification | RQ-039 | Vendor ticket open | Theme CSS override if the vendor has not fixed it by 2026-12-11; deploy after the freeze | Ops Lead |

Not in the table: CR-003 (approved as a minor decision 2026-10-14, delivery scheduled) and CR-006 (deferred to the Q1 2027 driver review). Neither needs governance action now.

## 2. Dispensation requests

| DSP | Exception requested | Conflicts with | Requested by | Filed | State | Recommendation |
|---|---|---|---|---|---|---|
| [DSP-003](dispensation-requests/DSP-003-woocommerce-extension.md) | Keep WooCommerce read-only until 2027-03-31 | STD-01a, SBB-13 decommission 2026-12-14, PR-01 | Finance Manager (RQ-040) | 2026-10-12 | **Pending Board 2026-11-05** | Reject in favour of a searchable final export |

## 3. Compliance assessments (scheduled)

| CA | Scope | Type | Planned | Assessor | State |
|---|---|---|---|---|---|
| CA-2026-003 | WP-02 Amazon marketplace connector (REQ-15, SA-22) | Acceptance | 2026-10-28 | Fractional architect | **Blocked** until [INV-2026-01](investigations/INV-2026-01-amazon-oversells.md) closes |
| CA-2026-005 | WP-05 Klaviyo + Gorgias (SBB-05, SBB-06) | Post-implementation | 2026-11-19 | Fractional architect | Scheduled (allowed during the freeze, [POL-02 §5](../01-reference-data/policies/POL-02-compliance-review-procedure.md#5-during-the-change-freeze)) |
| CA-2026-004 | WP-03 Engraving Queue full rollout (AC-001) | Pre-rollout | 2027-01-07 | Fractional architect | Scheduled; GA-003 must be closed first |

## 4. Investigations

| INV | Subject | Opened | Lead | State | Target close |
|---|---|---|---|---|---|
| [INV-2026-01](investigations/INV-2026-01-amazon-oversells.md) | 2 Amazon oversells during connector cut-over, 2026-10-03 | 2026-10-05 | Fractional architect | Root cause identified; actions in progress | 2026-10-26 |

## 5. Governance actions

| GA | Action | Source | Owner | Due | State |
|---|---|---|---|---|---|
| GA-003 | Fix the font-picker contrast in the engraving preview (vendor or theme CSS) | CA-2026-002 condition | Ops Lead | 2027-01-11 (before full rollout) | Open: vendor ticket raised 2026-10-09 |
| GA-004 | Report the engraving error rate weekly while DSP-001 is active | DSP-001 mitigation | Ops Lead | Weekly until 2027-01-31 | Ongoing: last report 2026-10-16 |
| GA-005 | Ask the laser vendor for SSO / managed-profile support | DSP-002 mitigation | Ops Lead | Before the DSP-002 review on 2027-01-16 | Open: chased 2026-10-01, no reply yet |
| GA-006 | Close the Mailchimp account after exporting the audience and consent log | ADR-008, SBB retirement plan | Marketing Manager | 2026-11-20 | Open: allowed during the freeze ([POL-04 §3](../01-reference-data/policies/POL-04-change-freeze-policy.md#3-what-is-allowed-during-the-freeze)) |
| GA-007 | Decommission WooCommerce: final encrypted export to TEC-07, then delete hosting | SBB retirement plan | Ops Lead | 2026-12-14 | Open: **depends on the DSP-003 decision** |
| GA-008 | Involve a fulfilment operative in compliance reviews, starting with CA-2026-004 UAT | [Capability maturity](../../architecture-repository/01-architecture-capability/capability-maturity.md) gap | Architecture Lead | 2027-01-07 | Open |
| GA-009 | Write an incident response annex to POL-07 | Capability maturity ("no formal incident runbook") | Fractional architect | 2027-02-26 | Open: not started |
| GA-010 | Add the missing processors (Google, Matrixify, personaliser app, marketplace connector, Amazon, PayPal) to the AR [processor register](../../architecture-repository/03-standards-information-base/legal-and-regulatory.md#processor-register-summary). DPAs are in place, but the register (record of processing) is incomplete | Finding in the solutions repository contracts register | Architecture Lead | Board 2026-11-05 (SIB update for approval) | Open: raised 2026-10-19 |

## Recently closed (Q3–Q4 2026)

| Item | Closed | Outcome | Record |
|---|---|---|---|
| GA-001 | 2026-10-06 | First restore drill from the weekly export completed (CA-2026-001 condition) | [CA-2026-001](../../architecture-repository/05-governance-log/compliance-assessments/CA-2026-001-shopify-replatform.md), EV-2026-012 |
| GA-002 | 2026-09-09 | Unapproved "reviews" app removed (CA-2026-001 check 2) | CA-2026-001, EV-2026-009 |
| CA-2026-002 | 2026-10-09 | Compliant with conditions; pilot approved by delegated approvers | [CA-2026-002](../../architecture-repository/05-governance-log/compliance-assessments/CA-2026-002-engraving-queue-pilot.md) |
| CA-2026-001 | 2026-09-10 | Compliant with conditions; go-live 2026-09-14 approved | [CA-2026-001](../../architecture-repository/05-governance-log/compliance-assessments/CA-2026-001-shopify-replatform.md), BM-2026-09-10 |
| CR-003 | 2026-10-14 | Approved as a minor decision (Ops Lead) | Requirements repository |
