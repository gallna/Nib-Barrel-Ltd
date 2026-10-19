# Checklist: Go-live Readiness

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Fractional architect | 1.0 | 2026-08-13 |

The **implementer** completes this checklist before a compliance assessment ([POL-02](../policies/POL-02-compliance-review-procedure.md)). It collects the operational evidence. The architectural conformance checks are in the AR [compliance assessment template](../../../architecture-repository/04-reference-library/templates/compliance-assessment-template.md), which the **assessor** uses; they are not repeated here.

| # | Check | Evidence to file | ✅ |
|---|---|---|---|
| 1 | The go-live date is outside the change freeze, or the item is allowed under [POL-04 §3](../policies/POL-04-change-freeze-policy.md#3-what-is-allowed-during-the-freeze) | Roadmap reference | ☐ |
| 2 | Architecture contract or SOW obligations met (e.g. AC-001 §2) | Implementer's statement | ☐ |
| 3 | Only approved apps and integrations are installed; the installed list matches the solutions repository baseline | Screenshot of the app list | ☐ |
| 4 | Accounts are named, SSO + MFA is on, and admin roles are limited to 2 people ([POL-06](../policies/POL-06-access-control.md)) | Admin user list | ☐ |
| 5 | Secrets are in 1Password; the repository contains vault paths only | Code / config scan output | ☐ |
| 6 | DPA signed and processor register updated (if personal data is processed) | DPA copy | ☐ |
| 7 | Retention configured in the tool to match the Data Architecture | Settings screenshot | ☐ |
| 8 | Runbook written or updated in the solutions repository (operate, fail over, restore) | Link | ☐ |
| 9 | Backup or export running, and a restore tested (REQ-13) | Restore log | ☐ |
| 10 | Rollback plan stated and rehearsed in staging | Plan + rehearsal note | ☐ |
| 11 | Staff trained; quick guide at the station where relevant | Attendance list | ☐ |
| 12 | Repository updates prepared: application and interface catalogues, SBB lifecycle, solutions baseline | PR links | ☐ |
| 13 | At least one end user (e.g. a fulfilment operative) took part in UAT (GA-008) | UAT sign-off | ☐ |

**Sign-off:** implementer (name, role, date) → passed to the assessor.
