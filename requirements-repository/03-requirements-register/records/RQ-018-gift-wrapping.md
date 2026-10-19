# RQ-018: Gift wrapping option at checkout (delivery only)

| Status | Owner | Version | Date |
|---|---|---|---|
| Implemented | Marketing Manager | 1.1 | 2026-10-15 |

This example shows a **delivery-only** requirement: it is recorded and approved here, but it never reaches the Architecture Board or the AR requirements catalogue.

| Attribute | Value |
|---|---|
| Statement | Customers can add gift wrapping (£3.50 per order) at checkout |
| Rationale | Over 40% of Q4 orders are gifts; competitors offer wrapping; estimated £4k/year margin |
| Type / priority | F / Could |
| Raised by | Marketing Manager, 2026-09-17 (SC-05) |
| Owner | Marketing Manager |
| Significance | **Delivery** |
| Building blocks | APP-01 only (a non-shippable add-on product plus a cart line) |
| Acceptance | Option shown in the cart; the wrap line appears on the Click & Drop packing list; VAT at the standard rate |

## Triage result (2026-09-21)

| Charter test | Result |
|---|---|
| Touches a system of record in a new way? | No: it is a standard Shopify product, and DE-01/DE-03 are unchanged |
| Adds a vendor? | No: native Shopify, with no app |
| Costs > £2k/yr? | No: ~£300/yr in wrapping stock |
| Changes an interface, data entity or standard? | No |

**Outcome:** Approved by the Ops Lead as delivery only. It went into the backlog for completion before the 2026-11-01 freeze, and no ADR was needed.

## Change history

| Date | Change | By |
|---|---|---|
| 2026-09-17 | Raised | Marketing Manager |
| 2026-09-21 | Triaged: delivery only; approved | Ops Lead |
| 2026-10-15 | Live; acceptance checked on 3 test orders | Marketing Manager |
