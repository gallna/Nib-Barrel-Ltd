# Policy Register

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Architecture Board | 1.1 | 2026-10-08 |

The governance policies and procedures we follow. Architecture principles and standards are **not** listed here. They live in the Architecture Repository ([principles](../../architecture-repository/01-architecture-capability/architecture-principles.md), [SIB](../../architecture-repository/03-standards-information-base/)), and these policies explain how we apply them.

Lifecycle: **Draft** → **Approved** → **Under review** → **Superseded** / **Withdrawn**. A superseded policy file is kept, with a pointer to its replacement.

| ID | Policy / procedure | Owner | Version | Status | Approved | Next review | Process |
|---|---|---|---|---|---|---|---|
| [POL-01](policies/POL-01-architecture-governance-procedure.md) | Architecture governance procedure | Architecture Lead | 1.0 | Approved | BM-2026-08-13 | 2027-04 | All |
| [POL-02](policies/POL-02-compliance-review-procedure.md) | Compliance review procedure | Fractional architect | 1.0 | Approved | BM-2026-08-13 | 2027-04 | Compliance |
| [POL-03](policies/POL-03-dispensation-policy.md) | Dispensation policy | Managing Director | 1.0 | Approved | BM-2026-08-13 | 2027-04 | Dispensation |
| [POL-04](policies/POL-04-change-freeze-policy.md) | Change freeze policy | Operations Lead | 1.1 | Approved | BM-2026-04-23 (v1.0); BM-2026-10-08 (v1.1) | 2027-04 | Business control |
| [POL-05](policies/POL-05-vendor-onboarding-and-review.md) | Vendor onboarding and review | Architecture Lead | 1.0 | Approved | BM-2026-08-13 | 2027-03 | Policy take-on, compliance |
| [POL-06](policies/POL-06-access-control.md) | Access control and repository write rights | Managing Director | 1.0 | Approved | BM-2026-08-13 | 2027-04 | Environment management |
| [POL-07](policies/POL-07-information-security-baseline.md) | Information security baseline | Fractional architect | 0.9 | Approved (incident annex pending, GA-009) | BM-2026-08-13 | 2027-02 | Business control |
| [POL-08](policies/POL-08-governance-records-retention.md) | Governance records retention | Finance Manager | 1.0 | Approved | BM-2026-08-13 | 2027-04 | Environment management |

## Take-on rules

1. A new policy starts as a pull request with Status `Draft` and an owner.
2. The Board approves it at a meeting. The approval is recorded in the minutes and the [audit trail](../03-audit-information/audit-trail.md).
3. The owner adds its review date to the [governance calendar](governance-calendar.md).
4. Policies are reviewed **annually** with the [charter](../../architecture-repository/01-architecture-capability/architecture-charter.md) (April), or sooner after an incident, an audit finding or a change in law.

## Change log

| Date | Change | By |
|---|---|---|
| 2026-04-23 | POL-04 v1.0 approved with the Statement of Architecture Work (ADR-003) | Board |
| 2026-08-13 | POL-01..03 and POL-05..08 approved as a set; this register created | Board |
| 2026-10-08 | POL-04 v1.1: decommissioning of read-only systems allowed during the freeze | Board |
