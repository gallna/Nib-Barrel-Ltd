# Nib & Barrel Ltd — example TOGAF Enterprise Repository

Example content only. Nib & Barrel Ltd is a **fictional** UK online retailer of fountain pens, ballpoints, inks and refills, with an optional laser-engraving service (7 staff, Bristol). The repository shows how a small business could organise its architecture work using the four repositories of the **TOGAF Standard, 10th Edition**. The top-level `README.md` explains the TOGAF concepts; the four folders hold the worked example.

## Summary of the content

All four repositories describe one moment: **2026-10-19**, during Phase G of ADM cycle 2 ("Project Quill"). Shopify went live on 2026-09-14, the engraving pilot runs 2026-10-12 → 10-30, and the Q4 change freeze runs 2026-11-01 → 2027-01-05. The Architecture Board meets on Thursdays; the next meeting is 2026-11-05. Keep new content consistent with these dates and with the existing IDs.

| Repository | Holds | Key files |
|---|---|---|
| `architecture-repository/` | Architecture description: metamodel, principles PR-01..07, landscape (strategic / segment / capability), SIB, reference library, governance log (ADR-001..008, CA-2026-001..002, DSP-001..002), architecture requirements REQ-01..15, solutions landscape SBB-01..13 | `README.md`, `00-architecture-metamodel/content-metamodel.md` (all ID prefixes) |
| `requirements-repository/` | Every requirement in any status (RQ-001..042), stakeholder concerns SC-01..08, change requests CR-001..006, impact statements RIS-001..002, traceability | `03-requirements-register/register.md`, `06-traceability/traceability-matrix.md` |
| `solutions-repository/` | Real assets by Solutions Continuum level: SA-nn configuration baselines (YAML), index of custom code (SA-30 Engraving Queue), contracts CTR-01..17, runbooks RB-01..07, configuration register | `solutions-catalogue.md`, `contracts/contracts-register.md` |
| `governance-repository/` | Reference data (POL-01..08, checklists, calendar), process status (open items GA-001..010, DSP-003 request, INV-2026-01, 2026-11-05 agenda), audit information (Board minutes BM-*, audit trail, evidence index EV-2026-*, Q3 2026 report) | `02-process-status/open-items.md`, `03-audit-information/audit-trail.md` |

## Rules for editing

- **Reference, don't copy.** Link across repositories by stable ID and relative path. An architecture requirement `REQ-nn` points to its source record `RQ-nnn` in the "Source record" column; it never duplicates it.
- **One governance store.** Completed outcomes (ADRs, compliance assessments, dispensations) live only in `architecture-repository/05-governance-log/`. The governance repository holds procedures, in-flight state and operational evidence, and links to the log.
- **Append-only.** Never delete rejected, deferred or superseded requirements, or audit-trail rows; change the status or add a correcting row.
- **No secrets or real PII.** Refer to credentials only by vault path (`1Password: Nib & Barrel / ...`).
- **Configuration baselines.** For SaaS, the configuration baseline in the solutions repository is the version-controlled record. For custom code (Engraving Queue, nb-dawn theme), GitHub is the record and the solutions repository only indexes it.
- **Document style.** Markdown + Mermaid, British English. Each document opens with an H1 and a metadata table (Status | Owner | Version | Date); bump the version and add a change-log row when you change an Approved document.
- **New IDs.** Register any new ID prefix in the metamodel's ID conventions.
- **Link check.** After editing, check that every relative link resolves.

## Known open threads

These are deliberate story hooks, not errors:
- **GA-003:** font-picker contrast condition from CA-2026-002.
- **GA-010:** the processor register in the SIB is missing six vendors.
- **DSP-003:** request to keep WooCommerce read-only until 2027-03; the Ops Lead recommends rejecting it.
- **INV-2026-01:** Amazon oversells; it blocks CA-2026-003.
- **CR-002 and CR-004:** awaiting the 2026-11-05 Board. CR-002 has a proposed ADR-009 for DPD labels.