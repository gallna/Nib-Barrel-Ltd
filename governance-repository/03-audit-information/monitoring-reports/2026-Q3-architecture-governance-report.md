# Q3 2026 Architecture & Governance Report

| Status | Owner | Period | Issued | Presented |
|---|---|---|---|---|
| Final | Architecture Lead | 2026-07-01 → 2026-09-30 (events to 2026-10-06 included where noted) | 2026-10-08 | [BM-2026-10-08](../board-minutes/BM-2026-10-08.md) |

## 1. Headline

**Transition 1 (Stable platform) was delivered on 2026-09-14, one day inside the hard deadline.** Shopify is now the system of record for product, inventory, customer and order data. Click & Drop and Xero are integrated, and all staff use SSO + MFA. Engraving accuracy has already improved under the interim copy-paste process (DSP-001). The one goal off track is oversells, because Amazon stock was still updated by hand until the connector cut-over in October.

## 2. Goal measures

From the [Architecture Vision §3](../../../architecture-repository/02-architecture-landscape/strategic/architecture-vision.md#3-goals-and-measures). The "current" values cover the period since go-live (2026-09-14 → 2026-09-30) unless stated otherwise.

| Goal | Measure | Baseline (2025) | Current | Target (Q4 2027) | Trend | RAG |
|---|---|---|---|---|---|---|
| GOL-01 | Engraving error rate / turnaround | 2.1% / 4 days | **0.9%** (2 of 230 engraved orders) / 3 days | < 0.3% / ≤ 2 working days | ⬆️ | 🟡 |
| GOL-02 | % non-engraved orders shipped same/next working day | 91% | **94%** | 98% | ⬆️ | 🟡 |
| GOL-03 | Oversell incidents | 41 / yr | **27 YTD** (25 before T1; 2 from 14–30 Sep, Amazon still manual) | 0 | ➡️ | 🔴 |
| GOL-04 | Web shop availability, Nov–Dec | 99.1% | Not measurable until Q4; Shopify 100% since go-live | 99.9% | — | 🟢 |
| GOL-05 | Hours/week of manual data entry | ~20 | **~11** | ≤ 5 | ⬆️ | 🟡 |
| GOL-06 | Days to fulfil a DSAR / erasure | untested | **3 days** (drill on 2026-10-01) | ≤ 7, tested quarterly | ⬆️ | 🟢 |

**Note on GOL-03:** two further oversells occurred on 2026-10-03 during the connector cut-over (Q4 figures, [INV-2026-01](../../02-process-status/investigations/INV-2026-01-amazon-oversells.md)).

## 3. Roadmap status

| Transition / WP | Plan | Status |
|---|---|---|
| T1 Stable platform: WP-01, WP-04, WP-06 | 2026-09-14 | ✅ Delivered 2026-09-14 (CA-2026-001) |
| T2 Connected channels: WP-02 Amazon connector | Cut-over 2026-10-03 | 🟡 Live; acceptance (CA-2026-003) pending the investigation |
| T2: WP-05 Klaviyo + Gorgias | 2026-10-20 / 2026-10-27 | 🟢 On track |
| Target: WP-03 Engraving Queue | Pilot from 2026-10-12; rollout 2027-01-11 | 🟢 Build complete (1,640 LOC); CA-2026-002 scheduled for 2026-10-09 |

## 4. Governance KPIs

| KPI | Q3 2026 | Comment |
|---|---|---|
| Board meetings held (regular + ad hoc) | 4 (07-02, 07-16, 08-13, 09-10) | All quorate |
| ADRs accepted | 2 (ADR-007, ADR-008) | — |
| Minor decisions | 1 (2026-08-14 labels) | — |
| Change requests decided | 1 (CR-001) | — |
| Requirement records raised / triaged within 7 days | 9 / 9 | RQ-017, -018, -019, -029, -033, -034, -035, -036, -037 |
| Compliance assessments completed | 1 (CA-2026-001: compliant with conditions) | 1 non-compliant finding (unapproved app), fixed within 1 day |
| CA conditions closed on time | 1 of 1 (GA-001, closed 2026-10-06, due 2026-10-15) | — |
| Dispensations active | 2 (DSP-001, DSP-002) | Neither within 30 days of expiry |
| Expired dispensations still in use | 0 | — |
| Governance actions overdue | 0 | — |
| Recurring controls done on time | 4 of 4 (capacity test, SAQ A, access review, DSAR drill on 2026-10-01) | — |
| Policies approved | 7 (POL-01..03, POL-05..08) | Policy register created |

## 5. Capability maturity (follow-up to the [2026 assessment](../../../architecture-repository/01-architecture-capability/capability-maturity.md))

| Dimension (2026 score → target 3) | Q3 progress |
|---|---|
| Architecture governance (2) | Policies approved; contracts in use (AC-001); dispensation policy in force. On course for 3 at the 2027-03 review. |
| Operating unit participation (2) | Not yet: GA-008 (a fulfilment operative in CA-2026-004 UAT) |
| IT security (2) | MFA 7/7; incident annex still missing (GA-009) |

## 6. Top risks

| Risk | Likelihood | Impact | Response |
|---|---|---|---|
| Amazon connector sync failure during peak causes oversells and Amazon account-health penalties | Medium | High | INV-2026-01 actions; alerting; stock buffer; CA-2026-003 tests outage scenarios |
| Engraving demand in the Q4 peak overwhelms manual copy-paste (DSP-001) | Medium | Medium | Seasonal operative trained on the engraving station; 4-eyes check; pilot SKUs on the queue |
| WooCommerce kept beyond 2026-12-14 for Finance look-ups | Low (pending decision) | High (PII on unpatched site) | DSP-003 decision on 2026-11-05; export alternative |
| Laser vendor never supports SSO | High | Low | DSP-002 review in 2027-01; VLAN isolation stays |

## 7. Decisions requested from the Board

1. Note the report. This also serves as the quarterly Phase H driver review: no new ADM cycle triggered.
2. Endorse the interim containment for INV-2026-01.
3. Approve POL-04 v1.1 (paper attached separately).
