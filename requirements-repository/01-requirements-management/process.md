# Requirements Management Process (Tailored)

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Architecture Lead (Ops Lead) | 1.0 | 2026-05-14 |

TOGAF places Requirements Management at the centre of the ADM: every phase can add or change requirements. Here it is tailored to a 7-person company with no in-house developers (see the [tailored ADM](../../architecture-repository/01-architecture-capability/tailored-adm.md)).

## 1. Cadence

| Activity | When | Who | Time | Output |
|---|---|---|---|---|
| Intake | Any time | Anyone, via the Ops Lead or a GitHub issue labelled `requirement` | — | New `RQ` record, status **Proposed** |
| Triage | Weekly, Monday 09:15 | Ops Lead (CS Lead attends if customer-facing) | 15 min | Type, priority and significance set; status **Analysed**, **Rejected**, or routed to a CR |
| Impact assessment | Per change request | Fractional architect | 1–4 h | `RIS-nnn` |
| Promotion and approval | Monthly Architecture Board | Board | Agenda item | **Approved** / **Deferred** / **Rejected**; approved architectural records promoted to `REQ-nn` |
| Delivery approval | At triage | Ops Lead | — | Delivery-only records **Approved** and added to the backlog |
| Verification | At acceptance or compliance assessment | Ops Lead / assessor | — | **Implemented**, with evidence (CA-yyyy-nnn or acceptance note) |
| Phase H review | Quarterly (next 2027-01-14) | Architecture Lead + MD | 1 h | Deferred records re-assessed; drivers checked against [ADM cycle triggers](../../architecture-repository/01-architecture-capability/tailored-adm.md#triggers-for-a-new-adm-cycle) |
| Assumption validation | On the date in the record | Record owner | — | Assumption confirmed, or a new requirement or risk raised |

## 2. Triage questions

1. Is it already covered by an existing record? If so, link it and close the new record as a duplicate in its change history.
2. Does it break a principle, a SIB standard or a legal obligation? If so, either **Reject** it, giving the reason, or raise a dispensation request through the [governance repository](../../governance-repository/README.md).
3. Is it architecturally significant (charter test: system of record, new vendor, > £2k/yr; or it changes an interface, data entity or standard)?
   - **No:** it is **Delivery** only. The Ops Lead approves it and it goes into the backlog.
   - **Yes:** raise a change request (`CR-nnn`). The fractional architect writes an impact statement (`RIS-nnn`), and the item goes on the next Board agenda.
4. Does it fall inside the Q4 change freeze (1 Nov – 5 Jan)? If so, schedule it for January.

## 3. Roles and RACI

R responsible · A accountable · C consulted · I informed

| Activity | MD (Board chair) | Ops Lead (Architecture Lead) | Fractional architect | Finance Manager | CS Lead | Marketing Manager | Fulfilment team |
|---|---|---|---|---|---|---|---|
| Raise requirement | R | R | R | R | R | R | R |
| Triage and classify | I | **A/R** | C | I | C | I | I |
| Impact assessment (RIS) | I | A | **R** | C | C | C | C |
| Approve delivery-only | I | **A/R** | I | I | I | I | I |
| Approve / promote architectural | **A** | R | C | R (Board vote) | I | I | I |
| Maintain AR requirements catalogue | I | **A/R** | C | I | I | I | I |
| Verify implemented | I | A | R | C | C | C | C (UAT) |
| Quarterly Phase H review | **A** | R | C | C | I | I | I |

## 4. Change classification (TOGAF Phase H)

| Class | Meaning here | Who approves |
|---|---|---|
| **Simplification** | Removes or reduces something, or configures an existing system of record; no new vendor | Ops Lead (minor decision) |
| **Incremental** | Extends the current architecture: a new interface, a new vendor, or a new data attribute | Architecture Board via an ADR |
| **Re-architecting** | Changes the scope or the target architecture, for example a new country or channel | Board; triggers a new ADM cycle |

## 5. Tooling

- Records are held as Markdown in this repository, under GitHub branch protection (STD-10). Changes go through pull requests reviewed by the Ops Lead.
- GitHub issues are used for discussion only. Each issue title starts with its `RQ` ID, and this repository remains the system of record.
- Commercially or security-sensitive detail (e.g. a vulnerability that drives an NFR) is not written here. The record links to the restricted evidence store instead.
