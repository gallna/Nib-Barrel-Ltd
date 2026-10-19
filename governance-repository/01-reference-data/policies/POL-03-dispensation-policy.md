# POL-03: Dispensation Policy

| Status | Owner | Version | Approved | Date |
|---|---|---|---|---|
| Approved | Managing Director | 1.0 | BM-2026-08-13 | 2026-08-13 |

## Purpose

A dispensation is a **time-limited, Board-approved exception** to an architecture principle, a SIB standard or an architecture requirement. This policy keeps exceptions visible, owned and temporary. Without it, a waiver quietly becomes the new architecture.

This policy was written after the Board granted DSP-001 and DSP-002 on 2026-07-16. It formalises the practice used for those two, and both comply with it.

## 1. When a dispensation is needed

A dispensation is needed when a solution, process or configuration would:
- breach a principle in the [Architecture Principles](../../../architecture-repository/01-architecture-capability/architecture-principles.md);
- use a SIB standard in the **Retire** or **Prohibited** state, or extend one in the **Contain** state ([technology standards](../../../architecture-repository/03-standards-information-base/technology-standards.md));
- fail an approved architecture requirement (REQ-nn) or an architecture contract obligation (for example AC-001 §2).

A dispensation is **not** available for legal obligations (LEG-01..08). No dispensation can approve non-compliance with the law, and STD-02a (card data on our systems) cannot be waived either.

## 2. Request content

The requester files `02-process-status/dispensation-requests/DSP-nnn-<slug>.md`. The Architecture Lead allocates the number when the request is filed, so a rejected request keeps its number. The request must state:

| Field | Required |
|---|---|
| Exception requested, in one sentence | ✅ |
| Principle / standard / requirement affected | ✅ |
| Reason, and why compliance is not possible now | ✅ |
| Options considered, including "comply" | ✅ |
| Risk and mitigation | ✅ |
| Owner (one named role) | ✅ |
| Requested expiry date | ✅ |
| Exit plan: what ends the exception | ✅ |
| Source requirement record (RQ-nnn), if any | If one exists |

## 3. Duration

| Case | Maximum duration |
|---|---|
| Default | **6 months** from approval |
| The cause is a **third-party product limitation** outside our control (e.g. DSP-002: laser vendor software) | 12 months, with a mandatory review at 6 months |
| The cause is a **fixed external date** (e.g. DSP-001: the Q4 change freeze) | Until 4 weeks after that date, and no more than 12 months |

The Board may renew a dispensation **once**, for no longer than its original term. A second renewal requires an ADR that changes the principle or standard instead.

## 4. Approval

- Only the Architecture Board can grant a dispensation (quorum per the [charter](../../../architecture-repository/01-architecture-capability/architecture-charter.md#architecture-board)).
- The requester and the owner do not vote on their own request ([POL-06](POL-06-access-control.md)).
- The decision is one of: **Granted**, **Granted with conditions**, **Rejected** (with the alternative the Board prefers), or **Deferred** (more information needed).

## 5. Recording

| Outcome | Where it is recorded |
|---|---|
| Granted | New row in the AR [dispensations register](../../../architecture-repository/05-governance-log/dispensations.md); expiry and review reminders in the [governance calendar](../governance-calendar.md) |
| Rejected | Decision and rationale appended to the request file, which moves to the closed section of [open items](../../02-process-status/open-items.md); the request file is kept as precedent |
| Any | Audit-trail row; minutes |

## 6. Monitoring

- **30 days before expiry**, the calendar reminder goes to the owner and the Architecture Lead.
- At expiry, the owner reports one of: the exception has ended (evidence filed), a renewal is requested, or an ADR is proposed.
- An expired dispensation that is still in use is a **governance breach**. It is logged as an investigation (`INV-yyyy-nn`) and reported to the next Board.
- Active dispensations are listed in every quarterly [monitoring report](../../03-audit-information/monitoring-reports/).

## 7. Current position (2026-10-19)

| DSP | Basis for duration | Review | Expiry | Status |
|---|---|---|---|---|
| DSP-001 | Fixed external date (Q4 freeze, rollout 2027-01-11) | — | 2027-01-31 | Active |
| DSP-002 | Third-party product limitation | 2027-01-16 | 2027-07-16 | Active |
| DSP-003 | Requested; see the [request](../../02-process-status/dispensation-requests/DSP-003-woocommerce-extension.md) | — | — | Pending Board 2026-11-05 |
