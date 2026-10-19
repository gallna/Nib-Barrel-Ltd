# RB-07: Shopify API Version Upgrade

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Ops Lead | 1.0 | 2026-10-12 |

| Implements | Contract | Cadence |
|---|---|---|
| AC-001 §5: the retainer covers Shopify API version upgrades | [CTR-12](../contracts/contracts-register.md) | Shopify releases a version every quarter, and each is supported for about 12 months. We upgrade **at least twice a year** and never run on a version with less than 3 months of support left |

Scope: the custom pieces only, which are the `orders/paid` webhook subscription and the Engraving Queue's Admin GraphQL calls ([SA-30](../04-organisation-specific/SA-30-engraving-queue.md)). Vendor apps upgrade themselves. Their health is checked through the [configuration register](../configuration-register.md).

## Steps
1. **Plan:** read the release notes for the target version and list the breaking changes for `fulfillmentOrderReleaseHold`, `order` and the webhook payload fields used.
2. **Contractor:** bump the version constant in `engraving-queue`, run the tests against the dev store, and open a PR.
3. **Staging:** point the dev-store webhook at staging with the new `api_version`, then run 10 test orders through the full job lifecycle.
4. **Prod:** deploy the Worker and **then** update the webhook subscription `api_version` in SA-20 (in that order, so the payload the Worker expects never arrives early).
5. **Record:** update SA-20, SA-30 and the configuration register in one PR.
6. **Freeze:** do not upgrade between 1 Nov and 5 Jan unless Shopify is removing the version in use.

## Plan
| Current | Target | When | Why |
|---|---|---|---|
| 2026-07 | 2027-01 | With v1.0.0, week of 2027-01-11 | 2026-07 is supported until about 2027-07; upgrading with the rollout avoids a separate change |
