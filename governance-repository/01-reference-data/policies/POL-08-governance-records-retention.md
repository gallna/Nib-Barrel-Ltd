# POL-08: Governance Records Retention

| Status | Owner | Version | Approved | Date |
|---|---|---|---|---|
| Approved | Finance Manager | 1.0 | BM-2026-08-13 | 2026-08-13 |

## Purpose

Governance records are evidence. They must survive long enough to answer an auditor, a regulator or a future Board asking "why did we do this?". They must also contain no more personal data than they need. Business data retention is set per entity in the [Data Architecture](../../../architecture-repository/02-architecture-landscape/strategic/data-architecture.md#1-data-entity-catalogue). This policy covers only the records of governance itself.

## Retention schedule

| Record | Where | Retention | Then |
|---|---|---|---|
| Policies (all versions) | `01-reference-data/` (Git history) | Life of company | — |
| Board minutes | `03-audit-information/board-minutes/` | 6 years after the meeting | Archive |
| Audit trail | `03-audit-information/audit-trail.md` | 6 years after the event | Archive |
| Evidence files | Restricted drive `NB-Governance/Evidence/` | 6 years after the related item closes | Delete; add a "destroyed" row to the evidence index |
| ADRs, CAs, DSPs | AR [governance log](../../../architecture-repository/05-governance-log/) | Life of the decision + 6 years | Archive |
| Investigation files | `02-process-status/investigations/` while open; then kept in place, marked Closed | 6 years after closure | Archive |
| Evidence containing personal data (only where unavoidable, e.g. an ICO notification) | Restricted drive, sub-folder `restricted-pii/`, MD + Ops Lead only | Minimum needed, at most 6 years | Delete |

## Integrity rules

1. The audit trail and the evidence index are **append-only**. A correction is a new row that references the original row.
2. Evidence files are stored as PDF or PNG with the date in the file name. They are never edited after filing; a replacement file gets a new EV number.
3. The restricted drive is in the weekly backup scope (TEC-07, PAT-03).
4. "Archive" means: moved to the `archive/` branch-protected folder in Git, or to the read-only `NB-Governance/Archive/` folder on the drive.
