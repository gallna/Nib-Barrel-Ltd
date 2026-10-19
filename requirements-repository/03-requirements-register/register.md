# Requirements Register — Master Index

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Architecture Lead (Ops Lead) | 2.3 | 2026-10-19 |

This index lists every requirement record ever raised. The full attributes of each record (statement, rationale, acceptance criteria, ADM phases, building blocks) are in the type files:

- [Business requirements](business.md) (B)
- [Functional requirements](functional.md) (F)
- [Non-functional requirements, constraints and assumptions](quality-constraints-assumptions.md) (NF, C, A)
- [Detailed records](records/) for illustrative cases, each with its own change history

Type: **B** business · **F** functional · **NF** non-functional · **C** constraint · **A** assumption. Priority: MoSCoW. **Promoted to** = the architecture requirement in the [AR catalogue](../../architecture-repository/06-architecture-requirements/requirements-catalog.md) that cites this record as its source.

| RQ | Title | Type | Priority | Raised | Raised by | Owner | Status | Significance | Promoted to | Key links |
|---|---|---|---|---|---|---|---|---|---|---|
| RQ-001 | 2× 2025 volume by end 2027, same headcount | B | Must | 2026-03-12 | MD | MD | Approved | Architectural | — (Vision goals) | GOL-02, GOL-05 |
| RQ-002 | No oversells across channels | B | Must | 2026-03-12 | Ops Lead | Ops Lead | Approved | Architectural | — (GOL-03) | REQ-15 |
| RQ-003 | Live engraving preview before basket | F | Must | 2026-04-02 | CS Lead | Ops Lead | Approved (pilot live) | Architectural | REQ-01 | SBB-01a, GAP-05 |
| RQ-004 | Validate engraving text at capture | F | Must | 2026-04-02 | Ops Lead | Ops Lead | Approved (pilot live) | Architectural | REQ-02 | SBB-01a, APP-09 |
| RQ-005 | [Engraving text reaches the laser without retyping](records/RQ-005-engraving-without-retyping.md) | F | Must | 2026-04-02 | Fulfilment team | Ops Lead | Approved | Architectural | — (capability architecture) | GAP-04, ADR-006, AC-001, DSP-001 |
| RQ-006 | Proof approval; 4-eyes for pens > £150 | F | Must | 2026-05-14 | Ops Lead | Ops Lead | Approved | Architectural | — (capability architecture) | BC-05 |
| RQ-007 | QC photo per engraved item | F | Should | 2026-05-14 | CS Lead | Ops Lead | Approved | Delivery | — | APP-09, REQ-09 |
| RQ-008 | No peak outage; ≥ 99.9% Nov–Dec | NF | Must | 2026-03-12 | MD | Ops Lead | Approved | Architectural | REQ-10 | GOL-04 |
| RQ-009 | Handle 3× average volume | NF | Must | 2026-04-09 | Ops Lead | Ops Lead | Implemented | Architectural | REQ-11 | CA-2026-001 |
| RQ-010 | Paid orders to Click & Drop without re-keying | F | Must | 2026-04-09 | Fulfilment team | Ops Lead | Implemented (T1) | Architectural | — (INT-03/04) | GAP-07 |
| RQ-011 | Daily sales reach Xero automatically | F | Must | 2026-04-09 | Finance Manager | Finance Manager | Implemented (T1) | Architectural | — (INT-02) | GAP-06 |
| RQ-012 | [Every web order posted to Xero as an invoice](records/RQ-012-RQ-013-xero-posting.md) | F | — | 2026-05-14 | Finance Manager | Finance Manager | **Superseded** by RQ-013 | — | — | ADR-005 |
| RQ-013 | [Daily summary per channel + payouts/fees to Xero](records/RQ-012-RQ-013-xero-posting.md) | F | Must | 2026-06-18 | Finance Manager + accountant | Finance Manager | Implemented | Architectural | — (ADR-005, INT-02) | ADR-005 |
| RQ-014 | Refunds within 14 days, same day in Xero | F | Must | 2026-04-09 | Finance + CS | Finance Manager | Implemented | Architectural | REQ-05 | INT-02 |
| RQ-015 | Order context next to customer emails | F | Must | 2026-04-09 | CS Lead | CS Lead | Approved (go-live 2026-10-27) | Architectural | — (GAP-08) | SBB-06 |
| RQ-016 | Purchase-based campaign segments | F | Should | 2026-04-09 | Marketing Manager | Marketing Manager | Approved (go-live 2026-10-20) | Architectural | — (ADR-008) | SBB-05 |
| RQ-017 | Self-serve returns portal | F | Should | 2026-09-24 | CS Lead | CS Lead | Approved, scheduled 2027-01 | Delivery | — | BP-05, CR-003 |
| RQ-018 | [Gift wrapping option at checkout](records/RQ-018-gift-wrapping.md) | F | Could | 2026-09-17 | Marketing Manager | Marketing Manager | Implemented 2026-10-15 | Delivery | — | — |
| RQ-019 | Gift message on packing slip | F | Could | 2026-09-17 | Marketing Manager | Ops Lead | Approved | Delivery | — | SBB-04 |
| RQ-020 | WCAG 2.2 AA storefront and preview | C | Should | 2026-04-23 | LEG-08 | Ops Lead | Approved (partially met) | Architectural | REQ-03 | CA-2026-002 |
| RQ-021 | Personalised-goods exemption shown at checkout | C | Must | 2026-04-23 | LEG-04 | Ops Lead | Implemented | Architectural | REQ-04 | CA-2026-001 |
| RQ-022 | 6-year records in MTD software | C | Must | 2026-04-23 | LEG-06 (accountant) | Finance Manager | Implemented | Architectural | REQ-06 | CA-2026-001 |
| RQ-023 | Card data never enters our systems | C | Must | 2026-04-23 | LEG-03 | Finance Manager | Implemented | Architectural | REQ-07 | STD-02a |
| RQ-024 | Consent with provenance; DSAR within 7 days | C | Must | 2026-04-23 | Marketing + LEG-01/02 | Marketing Manager | Implemented | Architectural | REQ-08 | BP-09 |
| RQ-025 | Purge engraving text 90 days after delivery | C | Must | 2026-05-14 | Fractional architect | Ops Lead | Implemented | Architectural | REQ-09 | CA-2026-002 |
| RQ-026 | Google SSO + MFA for all staff | NF | Must | 2026-04-23 | Fractional architect | Ops Lead | Implemented | Architectural | REQ-12 | DSP-002 |
| RQ-027 | Weekly open-format export + restore drills | NF | Must | 2026-04-23 | Fractional architect | Ops Lead | Implemented | Architectural | REQ-13 | PAT-03 |
| RQ-028 | Webhooks verify HMAC, idempotent | NF | Must | 2026-06-18 | Fractional architect | Ops Lead | Implemented | Architectural | REQ-14 | CA-2026-002 |
| RQ-029 | Amazon stock ≤ 15 min behind; dispatch confirmation on time | C | Must | 2026-07-02 | Ops Lead | Ops Lead | Approved (in progress) | Architectural | REQ-15 | CR-001, INV-2026-01 |
| RQ-030 | Sell to EU customers | B | Could | 2026-05-14 | MD + Marketing | MD | **Deferred** to ADM cycle 3 | (would be Architectural) | — | CR-006 |
| RQ-031 | Wholesale / B2B portal | B | Won't (this cycle) | 2026-05-14 | MD | MD | **Deferred** | — | — | Vision §4 |
| RQ-032 | Customer-uploaded logos / artwork | F | Could | 2026-06-04 | Customers | Ops Lead | **Deferred** to after full rollout | — | — | BC-05 |
| RQ-033 | [Store card details ourselves for one-click reorder](records/RQ-033-store-card-details.md) | F | — | 2026-07-09 | Agency (WP-01) | Finance Manager | **Rejected** | — | — | REQ-07, STD-02a |
| RQ-034 | Engrave pens posted in from elsewhere | F | — | 2026-08-06 | CS Lead | Ops Lead | **Rejected** | — | — | BC-05 |
| RQ-035 | Ink refill subscription | F | Should | 2026-09-03 | Marketing Manager | Marketing Manager | Analysed | Architectural (candidate) | — | CR-004, RIS-002 |
| RQ-036 | Automatic DPD labels | F | Should | 2026-09-17 | Ops Lead | Ops Lead | Analysed | Architectural | — | CR-002, RIS-001 |
| RQ-037 | Live chat on the web shop | F | Could | 2026-09-24 | CS Lead | CS Lead | Approved, scheduled 2027-01 | Delivery | — | SBB-06 |
| RQ-038 | Engraving turnaround ≤ 2 working days incl. peak | NF | Must | 2026-04-23 | MD | Ops Lead | Approved | Architectural | — (GOL-01) | GOL-01 |
| RQ-039 | Fix font-picker colour contrast | NF | Must | 2026-10-09 | CA-2026-002 | Ops Lead | Approved, due before 2027-01-11 | Delivery | — (within REQ-03) | CR-005, GA-003 |
| RQ-040 | [Keep WooCommerce read-only until 2027-03](records/RQ-040-woocommerce-read-only.md) | F | Should | 2026-10-12 | Finance Manager | Finance Manager | Analysed (conflict) | Architectural (conflict) | — | DSP-003, STD-01a |
| RQ-041 | Assumption: 2 seasonal operatives Nov–Dec | A | — | 2026-04-23 | Ops Lead | Ops Lead | Approved (validate 2026-10-23) | — | — | REQ-11 |
| RQ-042 | Assumption: engraved orders ≤ 30% through 2027 | A | — | 2026-04-23 | Ops Lead | Ops Lead | Approved (validate quarterly) | — | — | TEC-03 |

## Summary by status (2026-10-19)

| Status | Count | Records |
|---|---|---|
| Proposed | 0 | — |
| Analysed | 3 | RQ-035, RQ-036, RQ-040 |
| Approved | 19 | RQ-001–008, 015–017, 019, 020, 029, 037–039, 041, 042 |
| Implemented | 14 | RQ-009–011, 013, 014, 018, 021–028 |
| Deferred | 3 | RQ-030, RQ-031, RQ-032 |
| Rejected | 2 | RQ-033, RQ-034 |
| Superseded | 1 | RQ-012 |
| **Total** | **42** | 15 promoted to `REQ-nn` |

## Change history

| Date | Change | By |
|---|---|---|
| 2026-03-12 | RQ-001, 002, 008 raised at the Vision workshop | Architecture Lead |
| 2026-04-23 | RQ-003..011, 014..016, 020..024, 026, 027, 038, 041, 042 baselined with the Statement of Architecture Work (ADR-003) | Architecture Lead |
| 2026-05-14 | REQ-01..12 promoted; RQ-030, 031 deferred (out of scope) | Architecture Board |
| 2026-06-18 | RQ-012 superseded by RQ-013 (ADR-005); RQ-028 raised; REQ-13, 14 promoted | Architecture Board |
| 2026-07-02 | RQ-029 raised and promoted to REQ-15 (CR-001) | Architecture Board |
| 2026-07-13 | RQ-033 rejected at triage | Ops Lead |
| 2026-08-10 | RQ-034 rejected at triage | Ops Lead |
| 2026-10-09 | RQ-039 raised from the CA-2026-002 condition | Fractional architect |
| 2026-10-14 | RQ-017 approved as a minor decision (CR-003) | Ops Lead |
| 2026-10-15 | RQ-018 implemented | Marketing Manager |
| 2026-10-19 | RQ-040 analysed; dispensation request DSP-003 raised | Ops Lead |
