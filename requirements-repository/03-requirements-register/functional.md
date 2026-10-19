# Functional Requirements (F)

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Architecture Lead (Ops Lead) | 1.4 | 2026-10-19 |

Index: [register.md](register.md). Promoted records show the architecture requirement that cites them. Once a record is promoted, the binding wording lives in the [AR catalogue](../../architecture-repository/06-architecture-requirements/requirements-catalog.md).

## Personalisation (BC-05)

### RQ-003 Live engraving preview
**Statement:** Customers see their engraving text and chosen font rendered on the pen before adding it to the basket.
**Rationale:** 12 complaints in 2025 that the engraving "didn't look like I expected" (SC-04, SC-07).
**Source:** CS Lead · **Owner:** Ops Lead · **Priority:** Must · **Status:** Approved (pilot live) · **Significance:** Architectural → **REQ-01**
**ADM phases:** B, C · **Building blocks:** SBB-01a on APP-01 · **Links:** GOL-01, GAP-05, CA-2026-002
**Acceptance:** Preview is shown on every engravable SKU; pilot customers' "looks different" complaints = 0.

### RQ-004 Validate engraving text at capture
**Statement:** Engraving text is checked when the customer enters it: maximum length per SKU, supported characters only, and a profanity filter.
**Rationale:** 38% of 2025 remakes were overlong text or unsupported characters (remake analysis, 2026-03).
**Source:** Ops Lead · **Owner:** Ops Lead · **Priority:** Must · **Status:** Approved (pilot live) · **Significance:** Architectural → **REQ-02**
**ADM phases:** C · **Building blocks:** SBB-01a, APP-09 (re-validates) · **Links:** SA-23, SA-33 (max chars metafield)
**Acceptance:** Text that is invalid for the SKU cannot be submitted, and APP-09 rejects invalid jobs.

### RQ-005 Engraving text reaches the laser without retyping
See the detailed record [RQ-005](records/RQ-005-engraving-without-retyping.md).

### RQ-006 Proof approval with a 4-eyes check for high-value pens
**Statement:** An operative approves a rendered proof before the laser runs. Pens over £150 need a second person's approval.
**Rationale:** A mis-engraved premium pen costs up to £400 and cannot be resold (PR-01).
**Source:** Ops Lead · **Owner:** Ops Lead · **Priority:** Must · **Status:** Approved · **Significance:** Architectural (in the [capability architecture](../../architecture-repository/02-architecture-landscape/capability/personalised-engraving.md))
**ADM phases:** B, C · **Building blocks:** APP-09 job state model · **Acceptance:** No job reaches `Approved` without an approver; jobs over £150 show two approvers.

### RQ-007 QC photo per engraved item
**Statement:** The operative attaches a photo of the finished engraving to the job before release.
**Rationale:** It settles "it was engraved wrong" disputes quickly (SC-04).
**Source:** CS Lead · **Owner:** Ops Lead · **Priority:** Should · **Status:** Approved · **Significance:** Delivery (the feature sits inside APP-09's agreed scope)
**Links:** APP-09; the photo is purged with the text after 90 days (REQ-09) · **Acceptance:** A photo is present on 100% of jobs in `QCPassed`.

### RQ-032 Customer-uploaded logos and artwork
**Statement:** Customers can upload a logo or image to engrave.
**Rationale:** ~30 requests in 2025, mostly corporate gifts.
**Source:** Customers (SC-07) · **Owner:** Ops Lead · **Priority:** Could · **Status:** **Deferred** to after the Engraving Queue full rollout (2027-01-25)
**Deferral reason:** It needs vector conversion, a manual IP/copyright check and a new proof type. Adding it before the core queue is stable would increase pilot risk.

### RQ-034 Engrave pens customers post in from elsewhere
**Status:** **Rejected** (2026-08-10, triage) · **Source:** CS Lead (customer requests) · **Owner:** Ops Lead
**Reason kept:** We would carry damage liability for pens of unknown material and value. It also breaks the SKU-based engraving model, where maximum length and position are defined per SKU (SA-33), and it would require an inbound-goods process we don't have. CS reply macro: "Sorry, we can only engrave pens bought from us."

## Order-to-cash (BC-04, BC-06, BC-09)

### RQ-010 Paid orders flow to Click & Drop without re-keying
**Statement:** Paid, non-held orders appear in Click & Drop automatically within 5 minutes; tracking flows back.
**Source:** Fulfilment team (SC-03) · **Owner:** Ops Lead · **Priority:** Must · **Status:** Implemented (T1, 2026-09-14) · **Significance:** Architectural (INT-03, INT-04)
**Links:** GAP-07, SBB-04, SA-21 · **Acceptance:** Zero manual label entries in week 1 after go-live (verified 2026-09-21).

### RQ-011 Daily sales reach Xero automatically
**Statement:** Sales, fees, refunds and payouts are posted to Xero without re-keying.
**Source:** Finance Manager (SC-06) · **Owner:** Finance Manager · **Priority:** Must · **Status:** Implemented (T1) · **Significance:** Architectural (INT-02)
**Links:** GAP-06, SBB-03, SA-10, RQ-013 (how it's posted)

### RQ-012 / RQ-013 Xero posting granularity
See the detailed record [RQ-012 → RQ-013](records/RQ-012-RQ-013-xero-posting.md). RQ-012 (per-order invoices) was **superseded** by RQ-013 (daily summary), per ADR-005.

### RQ-014 Refunds within 14 days and in Xero the same day
**Source:** Finance + CS (SC-04, SC-06), LEG-05 · **Owner:** Finance Manager · **Priority:** Must · **Status:** Implemented · **Significance:** Architectural → **REQ-05**
**Acceptance:** Refund-to-ledger lag is the same day (segment goal); every refund is issued within 14 days.

### RQ-017 Self-serve returns portal
**Statement:** Customers start a return from their order page and receive a label without emailing CS.
**Rationale:** ~6 returns/day handled by email (BP-05); the target process in the [business architecture](../../architecture-repository/02-architecture-landscape/strategic/business-architecture.md#4-business-process-catalogue) assumes self-serve.
**Source:** CS Lead · **Owner:** CS Lead · **Priority:** Should · **Status:** Approved, scheduled 2027-01-11 · **Significance:** Delivery (it configures Shopify's native returns in the existing system of record, with no new vendor)
**Links:** [CR-003](../04-change-requests/change-request-register.md), BP-05 · **Acceptance:** ≥ 70% of returns started self-serve in February 2027; personalised items are excluded automatically (REQ-04).

### RQ-029 Amazon stock sync and dispatch confirmation
Constraint from Amazon policy: see [quality-constraints-assumptions.md](quality-constraints-assumptions.md#rq-029-amazon-stock-sync-and-dispatch-confirmation).

### RQ-033 Store card details ourselves for one-click reorder
See the detailed record [RQ-033](records/RQ-033-store-card-details.md) (**Rejected**).

### RQ-036 Automatic DPD labels
**Statement:** DPD labels for high-value (> £150) and next-day orders are created automatically from Shopify, and tracking flows back.
**Rationale:** ~3 orders/day (3%) are typed by hand into DPD's web portal, which leads to address errors and tracking that never reaches the customer.
**Source:** Ops Lead (SC-02) · **Owner:** Ops Lead · **Priority:** Should · **Status:** Analysed · **Significance:** Architectural (a new interface, and possibly a new vendor)
**Links:** [CR-002](../04-change-requests/CR-002-dpd-labels.md), [RIS-001](../05-impact-assessments/RIS-001-dpd-labels.md), ACT-08

## Customer engagement and service (BC-07, BC-08)

### RQ-015 Order context next to customer emails
**Source:** CS Lead · **Owner:** CS Lead · **Priority:** Must · **Status:** Approved (go-live 2026-10-27) · **Significance:** Architectural (GAP-08, INT-06)
**Acceptance:** Agents see order, tracking and engraving status in the ticket sidebar for 100% of tickets from known customers.

### RQ-016 Purchase-based campaign segments
**Source:** Marketing Manager · **Owner:** Marketing Manager · **Priority:** Should · **Status:** Approved (go-live 2026-10-20) · **Significance:** Architectural (ADR-008, INT-05)
**Acceptance:** Segments can be built on product type, ink colour and last-order date, using consented contacts only.

### RQ-018 Gift wrapping option
See the detailed record [RQ-018](records/RQ-018-gift-wrapping.md) (**Delivery** only).

### RQ-019 Gift message printed on the packing slip
**Statement:** The gift message entered at checkout is printed on the packing slip, and the price is not shown.
**Source:** Marketing Manager · **Owner:** Ops Lead · **Priority:** Could · **Status:** Approved · **Significance:** Delivery (Click & Drop packing slip template, SA-21)
**Note:** The message is personal data held on the order (DE-03) and follows the order's retention. It is not copied anywhere else.

### RQ-035 Ink refill subscription
**Statement:** Customers subscribe to a regular delivery of ink or refills every 1, 2 or 3 months.
**Rationale:** Refills are 31% of orders and highly repetitive, so recurring revenue would smooth the Q4 spike.
**Source:** Marketing Manager (SC-05) · **Owner:** Marketing Manager · **Priority:** Should · **Status:** Analysed · **Significance:** Architectural (candidate: a new vendor that touches the DE-03 system of record)
**Links:** [CR-004](../04-change-requests/CR-004-ink-subscription.md), [RIS-002](../05-impact-assessments/RIS-002-ink-subscription.md)

### RQ-037 Live chat on the web shop
**Source:** CS Lead · **Owner:** CS Lead · **Priority:** Could · **Status:** Approved, scheduled 2027-01 (after the freeze) · **Significance:** Delivery (Gorgias chat widget; transcripts are DE-13 in the existing system of record)

## Legacy and transition

### RQ-040 Keep WooCommerce read-only until 2027-03
See the detailed record [RQ-040](records/RQ-040-woocommerce-read-only.md) (conflict, leading to a dispensation request).
