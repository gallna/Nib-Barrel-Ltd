# AC-001: Architecture Contract — Engraving Queue (WP-03)

| Parties | Signed | Status |
|---|---|---|
| Nib & Barrel Ltd (Architecture Board) ↔ Independent software contractor (sole trader) | 2026-07-30 | Active |

## 1. Scope of work
Design, build and hand over APP-09 Engraving Queue, as described in the [capability architecture](../../02-architecture-landscape/capability/personalised-engraving.md), including INT-07, INT-08 and INT-09.

## 2. Architecture conformance obligations
The contractor must:
1. Implement on **Cloudflare Workers + D1 in TypeScript** (STD-04, ADR-007).
2. Store **only** DE-05 personalisation data, order ID and SKU. No addresses, emails or payment data.
3. Satisfy REQ-02, REQ-09, REQ-12, REQ-13 and REQ-14.
4. Use the hold-and-release pattern (PAT-02) so that failures leave orders safely held.
5. Keep the codebase under 2,000 lines (excluding tests and generated files), with ≥ 80% test coverage of job-state transitions.
6. Commit all source to the company GitHub organisation (STD-10). No personal repositories.
7. Store no secrets in code. Shopify API credentials go in Worker secrets.

## 3. Deliverables
| # | Deliverable | Acceptance |
|---|---|---|
| D1 | Working application in staging | Demo of the full job lifecycle with test orders |
| D2 | Automated tests | CI green; coverage report |
| D3 | README, architecture note, operations runbook | Ops Lead can redeploy from scratch by following the runbook |
| D4 | Pilot support (3 weeks) | ≤ 1 working-day response to defects |
| D5 | Handover session (recorded) | Delivered before final payment |

## 4. Governance
- Compliance assessment before pilot ([CA-2026-002](../../05-governance-log/compliance-assessments/CA-2026-002-engraving-queue-pilot.md)) and before full rollout.
- Any deviation from §2 needs a Board-approved dispensation.
- IP and source code are owned by Nib & Barrel Ltd.

## 5. Ongoing support
Retainer: 4 hours/month for 12 months after rollout, covering dependency updates and Shopify API version upgrades (released quarterly).
