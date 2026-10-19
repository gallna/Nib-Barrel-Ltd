# POL-02: Compliance Review Procedure

| Status | Owner | Version | Approved | Date |
|---|---|---|---|---|
| Approved | Fractional architect | 1.0 | BM-2026-08-13 | 2026-08-13 |

## Purpose

To make sure that what we implement matches the architecture we approved, **before** customers depend on it. This is ADM Phase G, as tailored in the [tailored ADM](../../../architecture-repository/01-architecture-capability/tailored-adm.md).

## 1. When a compliance assessment is mandatory

| Trigger | Assessment type | Example |
|---|---|---|
| Go-live of any work package that changes a system of record or an interface | Pre-go-live | CA-2026-001 Shopify re-platform |
| Pilot of a custom-built component | Pre-pilot | CA-2026-002 Engraving Queue pilot |
| Full rollout after a pilot | Pre-rollout | CA-2026-004 Engraving Queue full rollout |
| Acceptance of a configured integration that a requirement depends on | Acceptance | CA-2026-003 Amazon connector (REQ-15) |
| 4–6 weeks after a go-live with no pre-go-live CA, or where conditions were set | Post-implementation | CA-2026-005 Klaviyo + Gorgias |

Minor decisions ([POL-01](POL-01-architecture-governance-procedure.md)) do not need a CA unless the Ops Lead asks for one.

## 2. Roles

- **Assessor:** the fractional architect, or the Architecture Lead if the fractional architect designed or built the solution. The assessor is never the implementer.
- **Implementer:** provides evidence; for example the agency, the AC-001 contractor or an internal owner.
- **Approver of the outcome:** the Board, or delegated approvers named in the minutes.

## 3. Steps

1. **Schedule.** The Architecture Lead allocates the next `CA-yyyy-nnn` number and adds a row to [open items](../../02-process-status/open-items.md). The number is reserved even if the assessment is later cancelled.
2. **Prepare.** The implementer completes the [go-live readiness checklist](../checklists/go-live-readiness.md) and files the evidence on the restricted drive.
3. **Assess.** The assessor fills in the [compliance assessment template](../../../architecture-repository/04-reference-library/templates/compliance-assessment-template.md) and stores the result in the AR [compliance assessments](../../../architecture-repository/05-governance-log/compliance-assessments/) folder. That is the only copy.
4. **Decide.** The outcome is **Compliant**, **Compliant with conditions** or **Non-compliant**.
5. **Track conditions.** Each condition becomes a `GA-nnn` action with an owner and a due date in [open items](../../02-process-status/open-items.md). Conditions that block go-live must be closed before go-live.
6. **Close.** Add audit-trail and evidence-index rows, and close the open-items row with a link to the CA.

## 4. Non-compliance

A non-compliant result blocks go-live. The implementer fixes the issue and the assessment is repeated under the same CA number, with a new dated section. If the implementer cannot comply, the owner raises a dispensation request ([POL-03](POL-03-dispensation-policy.md)).

## 5. During the change freeze

Post-implementation assessments are allowed during the freeze, because they change nothing in production. Pre-go-live assessments for work that will go live after the freeze are scheduled for its last week ([POL-04](POL-04-change-freeze-policy.md)).
