# Governance Audit Trail

| Status | Owner | Rule | Last entry |
|---|---|---|---|
| Live, **append-only** | Architecture Lead | New rows at the bottom only; corrections are new rows ([POL-08](../01-reference-data/policies/POL-08-governance-records-retention.md)) | 2026-10-14 |

A record of every completed governance action: who did what, when, who approved it, and where the evidence is. The **outcome** itself (the ADR, CA or DSP text) is in the AR [governance log](../../architecture-repository/05-governance-log/). This log is the chronological index across all processes.

Branch protection makes every merge to this file a reviewed, timestamped commit ([POL-06](../01-reference-data/policies/POL-06-access-control.md)). The Git history therefore shows that rows were not altered later.

Times are UK local time, ISO 8601. Actors and approvers are recorded by role.

| # | Timestamp | Process | Event | Ref | Actor | Approver | Evidence |
|---|---|---|---|---|---|---|---|
| 1 | 2026-03-12T10:30 | Policy take-on | Tailored TOGAF approach and Git repository adopted | ADR-001 | Architecture Lead | Board (MD, Ops Lead, Finance) | BM-2026-03-12 |
| 2 | 2026-03-20T16:00 | Monitoring | Capability maturity self-assessment completed | [Assessment](../../architecture-repository/01-architecture-capability/capability-maturity.md) | Architecture Lead + fractional architect | — | — |
| 3 | 2026-04-09T10:20 | Policy take-on | Architecture Principles v2.0 approved | ADR-002 | Architecture Lead | Board | BM-2026-04-09 |
| 4 | 2026-04-23T10:40 | Policy take-on | Statement of Architecture Work approved; POL-04 v1.0 change freeze approved | ADR-003, POL-04 | Architecture Lead | Board | BM-2026-04-23 |
| 5 | 2026-05-07T12:00 | Compliance | DPAs collected for all processors; processor register approved | LEG-01 | Finance Manager | Architecture Lead | EV-2026-001 |
| 6 | 2026-06-02T15:00 | Compliance | Shopify exit test passed (full export opened with IDs intact) | PR-06, ADR-004 | Fractional architect | — | EV-2026-002 |
| 7 | 2026-06-04T10:35 | Compliance | Re-platform to Shopify approved | ADR-004 | Architecture Lead | Board | EV-2026-003, BM-2026-06-04 |
| 8 | 2026-06-18T10:25 | Compliance | Daily Xero summaries approved | ADR-005 | Finance Manager | Board (Finance abstained) | BM-2026-06-18 |
| 9 | 2026-06-18T10:40 | Compliance | Custom Engraving Queue build approved | ADR-006 | Architecture Lead | Board | BM-2026-06-18 |
| 10 | 2026-07-02T10:20 | Compliance | Cloudflare Workers + D1 hosting approved | ADR-007 | Fractional architect | Board | BM-2026-07-02 |
| 11 | 2026-07-02T10:35 | Compliance | Klaviyo replaces Mailchimp approved | ADR-008 | Marketing Manager | Board | BM-2026-07-02 |
| 12 | 2026-07-02T10:45 | Compliance | CR-001 approved: REQ-15 added to the architecture requirements | CR-001 | Ops Lead | Board (Ops Lead abstained) | BM-2026-07-02 |
| 13 | 2026-07-16T10:15 | Dispensation | DSP-001 granted (manual engraving transcription until 2027-01-31) | DSP-001 | Ops Lead (requester) | Board: MD + Finance Manager | [BM-2026-07-16](board-minutes/BM-2026-07-16.md) |
| 14 | 2026-07-16T10:25 | Dispensation | DSP-002 granted (engraving PC local account until 2027-07-16) | DSP-002 | Ops Lead (requester) | Board: MD + Finance Manager | BM-2026-07-16 |
| 15 | 2026-07-16T10:35 | Compliance | AC-001 terms approved; signature delegated to the MD | AC-001 | Fractional architect | Board | BM-2026-07-16 |
| 16 | 2026-07-30T14:00 | Compliance | AC-001 signed with the contractor | AC-001 | MD | — | EV-2026-004 |
| 17 | 2026-08-13T10:30 | Policy take-on | POL-01..03 and POL-05..08 approved; policy register v1.0 | Policy register | Architecture Lead | Board | BM-2026-08-13 |
| 18 | 2026-08-14T09:00 | Compliance | Minor decision: 4×6" thermal labels standardised | Decision log (minor) | Ops Lead | Ops Lead (minor) | — |
| 19 | 2026-09-04T17:00 | Monitoring | Peak capacity test passed (3× average, 40 concurrent checkout sessions) | REQ-11 | Ops Lead + agency | — | EV-2026-005 |
| 20 | 2026-09-08T16:30 | Compliance | CA-2026-001 completed: compliant with conditions | CA-2026-001 | Fractional architect + Ops Lead | — | EV-2026-006, -007, -008 |
| 21 | 2026-09-09T11:00 | Compliance | GA-002 closed: unapproved reviews app removed | GA-002 | Ops Lead | Fractional architect (verified) | EV-2026-009 |
| 22 | 2026-09-10T10:30 | Compliance | Shopify go-live on 2026-09-14 approved, with condition GA-001 | CA-2026-001 | Architecture Lead | Board | [BM-2026-09-10](board-minutes/BM-2026-09-10.md) |
| 23 | 2026-09-14T06:00 | Compliance | Shopify live; WooCommerce set to read-only | WP-01, SBB-01 | Ops Lead | — | Cut-over log in the solutions repository |
| 24 | 2026-09-30T15:00 | Compliance | PCI DSS SAQ A attestation submitted | REQ-07, LEG-03 | Finance Manager | MD (signatory) | EV-2026-010 |
| 25 | 2026-09-30T16:30 | Environment mgmt | Q3 access review completed; 1 stale account removed (former seasonal operative) | POL-06 | Architecture Lead | MD | EV-2026-013 |
| 26 | 2026-10-01T17:00 | Monitoring | DSAR/erasure drill completed in 3 days (target ≤ 7) | REQ-08, GOL-06 | CS Lead + Ops Lead | — | EV-2026-011 |
| 27 | 2026-10-05T10:00 | Business control | INV-2026-01 opened: Amazon oversells on 2026-10-03 | INV-2026-01 | Ops Lead | — | EV-2026-016 |
| 28 | 2026-10-06T15:30 | Compliance | GA-001 closed: first restore drill completed | GA-001, CA-2026-001 | Ops Lead | Fractional architect (verified) | EV-2026-012 |
| 29 | 2026-10-08T10:00 | Monitoring | Q3 2026 Architecture & Governance Report presented | Q3 report | Architecture Lead | Board (noted) | EV-2026-018 |
| 30 | 2026-10-08T10:30 | Policy take-on | POL-04 v1.1 approved (decommissioning during the freeze) | POL-04 | Ops Lead | Board: MD + Finance Manager | [BM-2026-10-08](board-minutes/BM-2026-10-08.md) |
| 31 | 2026-10-08T10:40 | Compliance | Engraving pilot approval delegated to MD + Ops Lead, conditional on CA-2026-002 | POL-01 §4 | Board | — | BM-2026-10-08 |
| 32 | 2026-10-09T15:00 | Compliance | CA-2026-002 completed: compliant with conditions (GA-003) | CA-2026-002 | Fractional architect | — | EV-2026-014, EV-2026-015 |
| 33 | 2026-10-09T16:10 | Compliance | Engraving pilot approved on 3 SKUs, 2026-10-12 → 2026-10-30 | CA-2026-002 | Ops Lead | MD (delegated) | Email approval filed as part of EV-2026-014 |
| 34 | 2026-10-12T11:00 | Dispensation | DSP-003 requested (keep WooCommerce read-only until 2027-03-31) | DSP-003, RQ-040 | Finance Manager | — (pending) | [Request](../02-process-status/dispensation-requests/DSP-003-woocommerce-extension.md) |
| 35 | 2026-10-14T09:30 | Compliance | CR-003 approved as a minor decision: Shopify native self-serve returns | CR-003, RQ-017 | CS Lead (requester) | Ops Lead (minor) | Requirements repository |

Next entries expected: ratification of row 33 and decisions on DSP-003, CR-002 and CR-004 at BM-2026-11-05.
