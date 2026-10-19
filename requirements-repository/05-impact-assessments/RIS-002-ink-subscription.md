# RIS-002: Requirements Impact Statement — CR-004 Ink refill subscription

| Status | Owner | Version | Date |
|---|---|---|---|
| Final | Fractional architect | 1.0 | 2026-10-14 |

## 1. Requirement under assessment

[RQ-035](../03-requirements-register/functional.md#rq-035-ink-refill-subscription): customers subscribe to a regular ink or refill delivery every 1, 2 or 3 months. Estimated at ~250 active subscriptions in year 1, or ~4 extra orders/day.

## 2. Impact on the architecture

| Area | Item | Impact | Severity |
|---|---|---|---|
| Business | BC-06, BC-07, BC-09; BP-05 (cancellations, returns) | New "manage subscription" customer journey; CS handles skips and cancellations | Medium |
| Data | New entity candidate: Subscription (customer, SKUs, interval, next date, status) | The system of record would be the subscription app. It must be added to the data entity catalogue with a retention rule | **Medium** |
| Data | DE-03 Order | The app creates orders in Shopify on schedule. Shopify stays the system of record for orders (PR-02 ✅) | Low |
| Data | DE-06 Payment | Card vaulted by Shopify Payments (subscription payment API). **No card data reaches us or the app vendor's own store, so SAQ A holds** (REQ-07 ✅) | Low (verify in assessment) |
| Data | DE-02 Inventory | Recurring demand isn't reserved. There is a risk of running out on renewal day (GOL-03, RQ-002) | **Medium** |
| Application | New APP candidate (subscription app from the Shopify App Store) | New vendor touching the DE-03 system of record, so an **ADR is required** under the charter, even at ~£1.2k/yr | Medium |
| Interfaces | APP-01 ↔ subscription app (native); Klaviyo events for renewal reminders (INT-05 extended) | Native only (STD-03 ✅) | Low |
| Accounting | INT-02 / ADR-005 | Subscription orders roll into the daily summary per channel; need to confirm the app's orders are tagged as a separate channel or tracking category | Low |
| Legal | LEG-02 PECR, LEG-04 Consumer Contracts Regulations | Renewal reminders are service messages, not marketing; cancellation must be as easy as sign-up; pre-contract information must state renewal terms | **Medium** |
| Requirements | REQ-04, REQ-07, REQ-08, REQ-11 | New acceptance checks; none changes | — |
| Principles | PR-01 ✅ (vaulted cards), PR-02 ✅, PR-03 ✅ buy, PR-05 ✅ usage-based, PR-06 ⚠️ exit test needed (subscription export incl. tokens migratable within Shopify) | — | — |
| Cost | ~£1.2k/yr app fee; ~£1k one-off configuration | — | — |
| Schedule | It conflicts with the Q4 freeze and the January rollouts | — | — |

## 3. Recommendation

**Don't deliver in ADM cycle 2.** Add RQ-035 to the **ADM cycle 3** Statement of Architecture Work. Phase B/C will need to:
1. add a Subscription data entity and its retention,
2. design stock reservation for renewals,
3. run a vendor evaluation including the exit test, and
4. take legal advice on renewal and cancellation wording.

The record stays **Analysed** until the Board decides. If the Board defers it, the status becomes Deferred, with the cycle 3 reference.
