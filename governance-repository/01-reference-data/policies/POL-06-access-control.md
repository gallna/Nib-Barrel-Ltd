# POL-06: Access Control and Repository Write Rights

| Status | Owner | Version | Approved | Date |
|---|---|---|---|---|
| Approved | Managing Director | 1.0 | BM-2026-08-13 | 2026-08-13 |

## Purpose

Governance only has evidential value if nobody can approve their own request and still appear compliant. This policy covers TOGAF *environment management*: who can change the repositories and the governance tools, and how that is checked.

## 1. Repository rights

All four repositories are in the company GitHub organisation, with branch protection on `main` (STD-10). Code owners require the approvals below.

| Repository / folder | Propose (open a PR) | Approve and merge | Notes |
|---|---|---|---|
| `architecture-repository/` | Architecture Lead, fractional architect | 1 Board voting member who is not the author | Changes to `Approved` documents need a Board decision reference |
| `architecture-repository/05-governance-log/` | Architecture Lead | MD or Finance Manager | Append-only, except status updates |
| `requirements-repository/` | Anyone on staff | Architecture Lead (as Requirements Manager) | Status changes to Approved / Rejected need the deciding minute or minor-decision reference |
| `solutions-repository/` | Asset owners | Architecture Lead | No secrets: vault paths only |
| `governance-repository/01-reference-data/` | Policy owners | Board decision, merged by a voting member who is not the author | — |
| `governance-repository/02-process-status/` | Architecture Lead, fractional architect | Architecture Lead | Live state; edits expected |
| `governance-repository/03-audit-information/` | Architecture Lead | MD or Finance Manager | **Append-only**; corrections are new rows |

Everyone on staff has read access to all four repositories. Contractors get read access to specific folders on request, for the length of their contract.

## 2. Separation of duties

| Rule | Example |
|---|---|
| Nobody approves their own request | The Ops Lead raised RQ-036, so CR-002 goes to the Board, not to a minor decision |
| A requester does not vote on their own dispensation | The Finance Manager does not vote on DSP-003 |
| An assessor is not the implementer | The fractional architect did not assess their own integration design |
| A PR author cannot merge their own PR | Enforced by branch protection |
| If separation breaks quorum, the item waits or goes to the MD | The MD is the final escalation (charter) |

## 3. System access

- Google Workspace SSO + MFA for every product that supports it (REQ-12, STD-05). The only exception is the engraving PC (DSP-002).
- Named accounts only. No shared logins except the documented ones in the solutions repository.
- Admin roles: at most 2 people per system (normally the MD and the system owner).
- Leavers: every account is removed on the last working day, using the Google Workspace offboarding list.

## 4. Quarterly access review

Each quarter, the Architecture Lead runs the [access review checklist](../checklists/quarterly-access-review.md) and the MD signs it off. The last review was on 2026-09-30 (EV-2026-013); the next is due on 2026-12-31.
