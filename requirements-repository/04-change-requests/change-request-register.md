# Change Request Register (ADM Phase H)

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Architecture Lead (Ops Lead) | 1.2 | 2026-10-19 |

A change request (CR) is raised when triage finds that a requirement is **architecturally significant**, or when a driver changes. Each CR is classified using the TOGAF Phase H change classes (see [process §4](../01-requirements-management/process.md#4-change-classification-togaf-phase-h)). The Board's decisions are recorded in the AR [decision log](../../architecture-repository/05-governance-log/decision-log.md). Agenda and status tracking are in the [governance repository](../../governance-repository/README.md).

| CR | Title | Class | Raised | Requirement | Impact statement | Status | Next step |
|---|---|---|---|---|---|---|---|
| CR-001 | Add REQ-15 after the Amazon policy review | Incremental | 2026-07-02 | RQ-029 | — (minor: no new component) | **Closed**: approved by the Board 2026-07-02 | REQ-15 added to the AR requirements catalogue |
| [CR-002](CR-002-dpd-labels.md) | Automate DPD labels | Incremental | 2026-09-17 | RQ-036 | [RIS-001](../05-impact-assessments/RIS-001-dpd-labels.md) | **Awaiting Board** 2026-11-05 | Recommend ADR-009 (DPD integration), delivered Jan 2027 after the freeze |
| CR-003 | Shopify native self-serve returns | Simplification | 2026-09-24 | RQ-017 | — (configuration of the existing SoR) | **Approved** as a minor decision by the Ops Lead, 2026-10-14 | Configure 2027-01-11 (after the freeze) |
| [CR-004](CR-004-ink-subscription.md) | Ink refill subscription | Incremental | 2026-09-03 | RQ-035 | [RIS-002](../05-impact-assessments/RIS-002-ink-subscription.md) | **Awaiting Board** 2026-11-05 | Recommend including it in the ADM cycle 3 scope, not now |
| CR-005 | Font-picker contrast fix | Simplification | 2026-10-09 | RQ-039 | — | **Open**: vendor ticket raised | Fallback is a theme CSS override; must be fixed before 2027-01-11 |
| CR-006 | EU expansion | Re-architecting | 2026-05-14 | RQ-030 | — (would need a full ADM cycle) | **Deferred** | Assess at the Phase H driver review on 2027-01-14; would trigger ADM cycle 3 ("new country") |

## CR-003 summary (minor decision)

Shopify's native self-serve returns run inside the existing system of record (DE-10 Return is already mastered in APP-01). There is no new vendor, no new interface and no extra cost, so it falls under the charter's **minor** route. The Ops Lead approved it on 2026-10-14, and it will be logged as a minor decision in the AR decision log when it is configured. Personalised items are excluded from the return rules (REQ-04).

## CR-005 summary

This came from the CA-2026-002 condition (governance action GA-003). It is a fix inside the existing REQ-03 and SBB-01a, so it needs no architecture change. Because it is an accessibility fix rather than a security fix, it must ship before the freeze starts (2026-11-01) or after it ends (2027-01-05). Either way, it must be done before the full rollout on 2027-01-11.
