# POL-01: Architecture Governance Procedure

| Status | Owner | Version | Approved | Date |
|---|---|---|---|---|
| Approved | Architecture Lead | 1.0 | BM-2026-08-13 | 2026-08-13 |

## Purpose

This procedure puts the governance process from the [Architecture Charter](../../../architecture-repository/01-architecture-capability/architecture-charter.md#governance-process) into practice. The charter says **what** the Board decides. This procedure says **how** an item gets there and where each step is recorded.

## 1. Intake

Every request starts as a record in the [requirements repository](../../../requirements-repository/), whatever its source (staff, customers, a compliance condition or a vendor change). The Architecture Lead triages new records every week (Mondays, 15 minutes).

## 2. Routing

The routing test is the one in the charter. Does the request touch a system of record, add a vendor, or cost more than £2k a year?

| Answer | Route | Approver | Recorded in |
|---|---|---|---|
| No | **Minor decision** | Ops Lead | AR [decision log](../../../architecture-repository/05-governance-log/decision-log.md#minor-decisions-ops-lead) (minor table) |
| Yes | **Change request** with a Requirements Impact Statement, then an ADR if approved | Architecture Board | Requirements repository (CR, RIS), then the AR decision log (ADR) |
| Conflicts with a principle or standard | **Dispensation request** ([POL-03](POL-03-dispensation-policy.md)) | Architecture Board | `02-process-status/dispensation-requests/`, then the AR [dispensations register](../../../architecture-repository/05-governance-log/dispensations.md) |

If the Ops Lead raised the request, they cannot approve it as a minor decision. It goes to the MD instead ([POL-06](POL-06-access-control.md)).

## 3. Board meetings

| Step | When | Who |
|---|---|---|
| Agenda and papers (CRs, RISs, DSP requests, CA results) published in `02-process-status/` | 5 working days before | Architecture Lead |
| Members read the papers; questions go as comments on the pull request | Before the meeting | All members |
| Meeting (45 minutes, Thursdays) | Monthly + ad hoc | MD chairs |
| Minutes published in [`03-audit-information/board-minutes/`](../../03-audit-information/board-minutes/) | Within 3 working days | Architecture Lead |
| Outcomes recorded in the AR governance log; open-items rows closed; audit-trail rows added | Within 3 working days | Architecture Lead |

**Quorum:** MD plus one other voting member. A member who raised an item does not vote on it, and if that breaks quorum the item waits.

## 4. Delegated and out-of-meeting decisions

The Board may delegate a decision that is conditional on a defined event. For example, the engraving pilot was approved once CA-2026-002 passed (BM-2026-10-08). Rules:
- The delegation is minuted, with the named approvers and the condition.
- The approvers record the decision in the [audit trail](../../03-audit-information/audit-trail.md) on the day.
- The next Board meeting ratifies it.

## 5. Escalation

If the Board cannot agree, the MD decides and the dissent is recorded in the ADR (charter, *Escalation*).

## 6. Measures

These are reported every quarter in the [monitoring report](../../03-audit-information/monitoring-reports/):
- requests triaged within 7 days;
- ADRs and minor decisions made;
- open actions past their due date;
- items decided at the first meeting at which they were tabled.
