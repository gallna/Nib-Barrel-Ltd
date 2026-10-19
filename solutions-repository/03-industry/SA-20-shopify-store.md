# SA-20: Shopify Store Configuration

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Ops Lead | 1.3 | 2026-10-15 |

| SBB | Continuum | System of record | Lifecycle | Contract | Change refs |
|---|---|---|---|---|---|
| SBB-01 / APP-01 / TEC-02 | Industry | Shopify admin. **The baseline here is authoritative.** System of record for DE-01–04, DE-09, DE-10 | Active since 2026-09-14 | [CTR-01](../contracts/contracts-register.md) | ADR-004, WP-01, CA-2026-001, RQ-018 (gift wrap) |

Shopify is the hub in [PAT-01](../../architecture-repository/04-reference-library/reference-models.md). Every other system subscribes to it, so this baseline is the most important file in the repository.

## Baseline

```yaml
store: nib-and-barrel.myshopify.com
plan: Advanced
primary_domain: www.nibandbarrel.co.uk          # SA-01
theme: nb-dawn v2.3.0 (SA-32)

markets:
  - name: United Kingdom
    currency: GBP
    countries: [GB]                             # EU is deferred (RQ-030 / CR-006)
  # no other markets enabled

taxes:
  prices_include_tax: true
  vat_rate_gb: 20%
  charge_vat_on_shipping: true

shipping_profiles:
  general:
    - { rate: "Royal Mail Tracked 48",  price: 3.95, free_over: 50.00 }
    - { rate: "Royal Mail Tracked 24",  price: 5.95 }
    - { rate: "DPD Next Day",            price: 9.95, note: "labels made manually in the DPD portal until CR-002 (RQ-036)" }
  high_value (order > £150):
    - { rate: "DPD Next Day (signed)",   price: 0.00 }

checkout:
  hosted: true                                   # REQ-07, SAQ A
  marketing_consent_checkbox: { default: unticked, label: "Email me news and offers" }   # REQ-08
  personalised_goods_notice: >                   # REQ-04, LEG-04
    "Engraved items are made to your specification and are not covered by the
     14-day cancellation right. This does not affect your rights if an item is faulty."
  notice_placement: [product page under engraving fields, cart, checkout order summary]
  customer_accounts: new (passwordless email code)
  gift_wrap: product "Gift wrap" £3.50, shown as a cart add-on   # RQ-018, live 2026-10-15
  gift_message: cart note (RQ-019, printed by SA-21 packing slip once delivered)

orders:
  engraving_detection: line item property "_engraving_line_1" present (set by SA-23)
  fulfilment_hold:                               # PAT-02 hold-and-release
    tool: Shopify Flow
    trigger: Order paid
    condition: any line item has property "_engraving_line_1"
    action: hold fulfilment order, reason "Awaiting engraving"
    released_by: Engraving Queue (INT-08) or manually per RB-03
  order_number_prefix: "NB"
  amazon_orders: imported by the connector (SA-22), tagged "amazon"

webhooks:                                        # custom webhooks are allowed only for APP-09 (STD-03)
  - { topic: orders/paid, address: https://queue.nibandbarrel.co.uk/webhooks/shopify, api_version: 2026-07, format: json }
  signing_secret: vault:1Password/Nib & Barrel/Engineering/eq-shopify-webhook-secret

custom_app:
  name: "Engraving Queue"
  scopes: [read_orders, read_products, write_merchant_managed_fulfillment_orders, read_merchant_managed_fulfillment_orders]
  admin_api_token: vault:1Password/Nib & Barrel/Engineering/eq-shopify-admin-token

approved_apps:                                   # STD-03; anything else is removed (CA-2026-001 check 2)
  - Xero (SA-10)
  - Royal Mail Click & Drop (SA-21)
  - Matrixify (SA-13)
  - Klaviyo (SA-11)
  - Gorgias (SA-12)
  - Marketplace connector (SA-22)
  - Product personaliser (SA-23)
  - Shopify Flow, Shopify Email (transactional templates only)

customer_data:
  inactive_customer_review: quarterly; anonymise 3 years after last order (DE-04)
  erasure: see RB-01

staff:                                           # Google login + Shopify 2-step enforced (SA-03)
  - { role: Owner, holder: MD }
  - { role: Admin, holder: Ops Lead }
  - { role: Fulfilment, holders: fulfilment@, permissions: [orders view/fulfil, products view] }
  - { role: Customer Service, holder: CS Lead, permissions: [orders, refunds, customers, returns] }
  - { role: Marketing, holder: Marketing Manager, permissions: [products, discounts, online store] }
  - { role: Finance, holder: Finance Manager, permissions: [orders view, reports, payouts] }
  collaborator_accounts: none active (agency access revoked 2026-09-28)

redirects: 612 legacy URLs → 301 (crawl test 0 404s, CA-2026-001 check 7)
```

## Known drift and planned changes

| Item | Change ref | When |
|---|---|---|
| Self-serve returns (Shopify native) | CR-003 / RQ-017 | 2027-01-11 (after the freeze) |
| Webhook API version 2026-07 → 2027-01 | RB-07 | With Engraving Queue v1.0.0 |
| DPD label automation | CR-002 / RQ-036 | Awaiting Board 2026-11-05 |
