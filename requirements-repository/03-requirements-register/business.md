# Business Requirements (B)

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Architecture Lead (Ops Lead) | 1.1 | 2026-10-19 |

Index: [register.md](register.md). Business requirements are realised through Vision goals and are not promoted one-to-one to `REQ-nn`. See [Architecture Vision §3](../../architecture-repository/02-architecture-landscape/strategic/architecture-vision.md#3-goals-and-measures).

---

### RQ-001 Grow to 2× 2025 order volume with the same headcount
**Statement:** By the end of 2027, Nib & Barrel can handle twice its 2025 order volume (~52,000 orders/year), including engraved orders, with the same 7 staff plus seasonal help.
**Rationale:** Growth is constrained by manual effort (DRV-01, DRV-04), not by demand.
**Source:** MD, Vision workshop 2026-03-12 (SC-01) · **Owner:** MD · **Priority:** Must · **Status:** Approved · **Significance:** Architectural
**ADM phases:** A, B, E · **Building blocks:** all · **Links:** GOL-02, GOL-05, [Vision statement](../../architecture-repository/02-architecture-landscape/strategic/architecture-vision.md#1-vision-statement)
**Acceptance:** Q4 2027 orders per staff hour ≥ 2× the Q4 2025 figure, and manual data entry ≤ 5 h/week (GOL-05).

### RQ-002 No oversells across channels
**Statement:** A product is never sold on any channel when no stock is available.
**Rationale:** 41 oversells in 2025 (DRV-02), each costing a refund, an apology and often an Amazon performance strike.
**Source:** Ops Lead (SC-02) · **Owner:** Ops Lead · **Priority:** Must · **Status:** Approved · **Significance:** Architectural
**ADM phases:** B, C · **Building blocks:** APP-01, APP-08 · **Links:** GOL-03, GAP-02, GAP-03, PR-02, REQ-15 (via RQ-029), INV-2026-01
**Acceptance:** Zero oversell incidents in a rolling 12 months (GOL-03).

### RQ-030 Sell to EU customers
**Statement:** Accept and ship orders to EU addresses with prices shown including VAT, delivered duty paid.
**Rationale:** ~8% of site visits come from the EU, and fountain-pen enthusiasts are a cross-border community.
**Source:** MD + Marketing Manager (SC-01, SC-05) · **Owner:** MD · **Priority:** Could · **Status:** **Deferred** to ADM cycle 3 · **Significance:** would be Architectural (re-architecting)
**ADM phases:** A–F · **Building blocks:** APP-01 markets, APP-03 (OSS/IOSS VAT), carriers, DE-04 transfers · **Links:** [CR-006](../04-change-requests/change-request-register.md), Vision §4 (out of scope)
**Deferral reason:** Outside the Project Quill scope. A new country is an [ADM cycle trigger](../../architecture-repository/01-architecture-capability/tailored-adm.md#triggers-for-a-new-adm-cycle). Re-assessed at the Phase H review on 2027-01-14.

### RQ-031 Wholesale / B2B portal
**Statement:** Stationery shops can order at trade prices through a self-serve portal.
**Rationale:** Three independent shops asked in 2025; trade orders are currently handled by email.
**Source:** MD (SC-01) · **Owner:** MD · **Priority:** Won't (this cycle) · **Status:** **Deferred** · **Significance:** —
**Links:** Vision §4 (out of scope); BigCommerce's B2B strength was rejected as out of scope in ADR-004.
**Deferral reason:** Low volume (3 shops), and trade orders work well by email. Revisit if trade revenue exceeds 10% of total.
