# Architecture Principles

| Status | Owner | Version | Approved by | Date |
|---|---|---|---|---|
| Approved | Architecture Board | 2.0 | Architecture Board | 2026-04-09 |

Each principle uses the TOGAF format: **Statement / Rationale / Implications**. They are listed in priority order. When two principles conflict, the higher one wins unless the Board records a dispensation.

---

### PR-01 Customer trust comes first
**Statement:** We never trade customer data protection, payment security or order accuracy for speed or cost.
**Rationale:** We sell gifts, often engraved and impossible to resell. One mis-engraved or lost order costs us the customer, and one data breach could end the business.
**Implications:**
- Payment card data is handled only by PCI DSS Level 1 providers (see [REQ-07](../06-architecture-requirements/requirements-catalog.md)).
- Personalisation text is captured once, validated and never retyped by hand.
- Every new SaaS vendor gets a privacy and security check before adoption.

### PR-02 One system of record per data entity
**Statement:** Each data entity has exactly one authoritative system. Every other system holds a synchronised copy and treats it as read-only.
**Rationale:** In the baseline, stock lived in three places (WooCommerce, Amazon, a spreadsheet), which caused about 40 oversells a year.
**Implications:**
- The [Data Architecture](../02-architecture-landscape/strategic/data-architecture.md) names the system of record for every entity.
- Integrations are one-directional from the system of record, unless an ADR records otherwise.

### PR-03 Buy before build
**Statement:** Prefer SaaS, then configure, then low-code extensions. Write custom code only for genuine differentiators.
**Rationale:** We employ no developers. Every line of custom code is a long-term liability we pay contractors to maintain.
**Implications:**
- Custom builds need an ADR that names the differentiating capability.
- Engraving workflow is the **only** capability currently approved for custom build ([ADR-006](../05-governance-log/decision-log.md#adr-006)).

### PR-04 Automate the repetitive, not the judgement
**Statement:** Automate data movement and routine steps. Keep humans in the loop for quality and customer judgement.
**Rationale:** A small team should spend its time on curation, quality control and customer care, not copy-paste.
**Implications:**
- Order data flows to accounting, shipping and marketing without manual re-entry.
- Engraving proofs are always checked by a person before the laser runs.

### PR-05 Design for peak, pay for average
**Statement:** The architecture must handle 3× average load in Q4 without re-engineering, and costs should scale with volume.
**Rationale:** 38% of annual revenue arrives between 1 Nov and 23 Dec.
**Implications:**
- Prefer usage-based or tiered SaaS pricing over fixed infrastructure.
- Capacity tests happen every September ([REQ-11](../06-architecture-requirements/requirements-catalog.md)).

### PR-06 Avoid lock-in where exit is expensive
**Statement:** For any system of record, we must be able to export our data in an open format.
**Rationale:** Small businesses get squeezed on price at renewal, and a credible exit route is our negotiating leverage.
**Implications:**
- Vendor selection includes a documented exit/export test.
- Customer, product and order data is exported weekly to our own storage ([TEC-07](../02-architecture-landscape/strategic/technology-architecture.md)).

### PR-07 Compliance by design
**Statement:** Legal and regulatory obligations ([SIB](../03-standards-information-base/legal-and-regulatory.md)) are architecture requirements from day one, not a post-launch audit.
**Rationale:** UK GDPR, the Consumer Contracts Regulations and PCI DSS all apply, even at our size.
**Implications:**
- Each solution design includes a compliance checklist section.
- Data retention rules are configured in tools, not left to memory.
