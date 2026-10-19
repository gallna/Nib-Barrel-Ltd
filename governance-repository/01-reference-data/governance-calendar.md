# Governance Calendar — Recurring Controls

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Architecture Lead | 1.2 | 2026-10-19 |

Every recurring control, with when it was last done and when it is next due. Each due date is also a Google Calendar event on the shared "Governance" calendar, with a reminder 7 days before (30 days for dispensation expiries). An overdue control appears in [open items](../02-process-status/open-items.md).

## Recurring controls

| Control | Frequency | Owner | Last done | Next due | Evidence (last) | Ref |
|---|---|---|---|---|---|---|
| Architecture Board meeting | Monthly (Thursday) + ad hoc | MD | 2026-10-08 | **2026-11-05**, then 2026-12-03, 2027-01-07 | [BM-2026-10-08](../03-audit-information/board-minutes/BM-2026-10-08.md) | Charter |
| Requirements triage | Weekly (Monday) | Architecture Lead | 2026-10-19 | 2026-10-26 | Requirements repository history | POL-01 |
| DSAR / erasure drill (test persona) | Quarterly | CS Lead + Ops Lead | 2026-10-01 (3 days) | 2027-01-08 | EV-2026-011 | REQ-08, GOL-06 |
| Restore drill from weekly export | Twice yearly | Ops Lead | 2026-10-06 | 2027-04 | EV-2026-012 | REQ-13, PAT-03 |
| Peak capacity test | Annually (September) | Ops Lead | 2026-09-04 | 2027-09 | EV-2026-005 | REQ-11, PR-05 |
| Peak readiness checklist (RB-05) | Annually, by 25 October | Ops Lead | 2025-10 (informal) | **2026-10-25** | — | POL-04 §5 |
| PCI DSS SAQ A attestation | Annually | Finance Manager | 2026-09-30 | 2027-09 | EV-2026-010 | REQ-07, LEG-03 |
| Access review | Quarterly | Architecture Lead; MD signs off | 2026-09-30 | 2026-12-31 | EV-2026-013 | POL-06 |
| Vendor and DPA review | Annually (March) | Architecture Lead | — (first cycle) | 2027-03 | — | POL-05 |
| Capability maturity self-assessment | Annually | Architecture Lead + fractional architect | 2026-03-20 | 2027-03 | [Assessment](../../architecture-repository/01-architecture-capability/capability-maturity.md) | — |
| Principles, charter and policy review | Annually (April) | Board | 2026-04-09 (principles) | 2027-04 | ADR-002 | Policy register |
| Phase H driver review | Quarterly | Architecture Lead | 2026-10-08 (with Q3 report) | 2027-01-14 | Q3 report | Tailored ADM |
| Quarterly monitoring report | Quarterly | Architecture Lead | 2026-10-08 (Q3) | 2027-01-07 (Q4) | EV-2026-018 | POL-01 §6 |
| Shopify API version upgrade (APP-09) | Quarterly | AC-001 retainer contractor | 2026-07 (2026-07 API version) | 2027-01 (after the freeze) | Solutions repository RB-07 | AC-001 §5 |
| Assumption validation | Per assumption | Ops Lead | — | RQ-041: **2026-10-23**; RQ-042: 2027-01 | Requirements repository | — |
| DSP-001 engraving error-rate report | Weekly (Friday) | Ops Lead | 2026-10-16 | 2026-10-23 | EV-2026-017 (rolling) | DSP-001, GA-004 |

## Dispensation dates

| DSP | Event | Date | Reminder |
|---|---|---|---|
| DSP-001 | Expiry | 2027-01-31 | 2027-01-01 |
| DSP-002 | 6-month review ([POL-03 §3](policies/POL-03-dispensation-policy.md#3-duration)) | 2027-01-16 | 2026-12-17 |
| DSP-002 | Expiry | 2027-07-16 | 2027-06-16 |

## Fixed dates (2026–27)

| Date | Event |
|---|---|
| 2026-10-20 | Klaviyo go-live (SBB-05) |
| 2026-10-27 | Gorgias go-live (SBB-06); shared inbox becomes a forwarding alias |
| 2026-10-28 | CA-2026-003 Amazon connector (if INV-2026-01 is closed) |
| 2026-10-30 | Engraving pilot ends |
| 2026-10-31 | Stock spreadsheet archived (read-only) |
| **2026-11-01 → 2027-01-05** | **Q4 change freeze** ([POL-04](policies/POL-04-change-freeze-policy.md)) |
| 2026-11-19 | CA-2026-005 Klaviyo + Gorgias post-implementation review |
| 2026-11-20 | Mailchimp account closure (GA-006) |
| 2026-12-14 | WooCommerce decommission (GA-007; depends on DSP-003) |
| 2027-01-07 | CA-2026-004 Engraving Queue full rollout |
| 2027-01-11 | Engraving Queue full rollout; self-serve returns (CR-003) |
