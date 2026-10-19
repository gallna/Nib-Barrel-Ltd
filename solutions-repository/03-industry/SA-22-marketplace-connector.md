# SA-22: Marketplace Connector Configuration (Shopify ↔ Amazon UK)

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Ops Lead | 1.1 | 2026-10-06 |

| SBB | Continuum | System of record | Lifecycle | Contract | Change refs |
|---|---|---|---|---|---|
| SBB-08 / APP-08 / INT-01, plus SBB-07 Seller Central settings | Industry | Connector app. **The baseline here is authoritative.** | **Implementing**: WP-02 acceptance pending | [CTR-09](../contracts/contracts-register.md), [CTR-11](../contracts/contracts-register.md) | WP-02, GAP-02, GAP-03, REQ-15, LEG-07, INV-2026-01 |

Shopify is the inventory system of record (PR-02). The connector only **pushes** stock and listings to Amazon and **pulls** Amazon orders into Shopify.

## Baseline

```yaml
connector: Marketplace connector (Shopify App Store, Amazon SP-API approved app)   # LEG-07
amazon_marketplace: amazon.co.uk
auth:
  sp_api_authorisation: granted by Ops Lead in Seller Central; refresh token held by the app vendor
  token_expiry_alert: email ops@ 14 days before expiry      # added 2026-10-06 after INV-2026-01
sync:
  inventory_push_interval: 15 min                           # REQ-15
  price_push: on (Shopify price list "Amazon", +8%)
  listing_push: create/update only for mapped SKUs
  stock_buffer:
    default: 0
    low_stock_rule: { when_available_lte: 3, buffer: 1 }   # interim mitigation, INV-2026-01
orders:
  import_to_shopify: on, tag "amazon", channel "Amazon"
  customer_records: create as Shopify customer with Amazon relay email (no marketing consent)
  tracking_push_to_amazon: on (from INT-04 tracking)        # dispatch confirmation within handling time
sku_mapping:
  mapped: 312 of ~420 SKUs
  excluded:
    - all engraving-eligible variants sold *with* engraving (Amazon has no engraving flow)
    - gift wrap product (RQ-018)
    - bundles
health_checks:
  daily: compare 20 random SKUs Shopify vs Amazon available qty; alert if any mismatch > 0 for > 15 min
seller_central (SBB-07) settings relied on:
  handling_time_days: 1
  fulfilment_channel: merchant fulfilled (MFN)
  2-step verification: on (Amazon-enforced)
```

## Acceptance status
WP-02 acceptance and **CA-2026-003** (planned 2026-10-28) are blocked until **INV-2026-01** closes: 2 oversells on 2026-10-03 during cut-over, caused by a zero stock buffer and a 45-minute sync gap after a token expiry. Status is tracked in the [governance repository](../../governance-repository/).
