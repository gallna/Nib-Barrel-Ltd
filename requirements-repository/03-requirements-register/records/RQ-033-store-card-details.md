# RQ-033: Store card details ourselves for one-click reorder (rejected)

| Status | Owner | Version | Date |
|---|---|---|---|
| Rejected | Finance Manager | 1.0 | 2026-07-13 |

This example shows a **rejected** requirement whose reason is kept, so the same idea is not proposed again from scratch.

| Attribute | Value |
|---|---|
| Statement | Save customers' card numbers in our own database (via a custom app) to offer one-click reorders of ink |
| Rationale given | Faster repeat purchase of refills |
| Type | F |
| Raised by | Re-platforming agency during WP-01, 2026-07-09 |
| Owner | Finance Manager |
| Status | **Rejected** at triage, 2026-07-13 |

## Reason for rejection

1. **Violates a constraint:** REQ-07 (from RQ-023, LEG-03) says card data never enters systems we operate. Storing card data would move us from PCI DSS SAQ A to SAQ D, which is far beyond our capability.
2. **Prohibited standard:** STD-02a, "any integration that puts card data on our systems", is **Prohibited** in the [SIB](../../../architecture-repository/03-standards-information-base/technology-standards.md).
3. **Principle:** it conflicts with PR-01 (customer trust) and PR-03 (buy before build).
4. **The need is already met:** Shopify's accelerated checkout (Shop Pay) and PayPal already offer one-tap repeat purchase, with the vault held by the PCI DSS Level 1 provider.

The underlying need, quicker refill reorders, is still valid and lives on in **RQ-035** (ink refill subscription, CR-004). That approach keeps cards in the payment provider's vault.

## Change history

| Date | Change | By |
|---|---|---|
| 2026-07-09 | Raised in a WP-01 workshop | Agency, via Ops Lead |
| 2026-07-13 | Rejected at triage; agency informed in writing | Ops Lead + Finance Manager |
| 2026-09-03 | Cross-referenced from RQ-035 | Marketing Manager |
