# SA-14: Payments Configuration

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Finance Manager | 1.0 | 2026-09-14 |

| SBB | Continuum | System of record | Lifecycle | Contract | Change refs |
|---|---|---|---|---|---|
| SBB-02 / APP-02 | Common systems | Shopify Payments + PayPal. **The baseline here is authoritative.** System of record for DE-06 Payment | Active | [CTR-01](../contracts/contracts-register.md), [CTR-16](../contracts/contracts-register.md) | ADR-004, REQ-07, LEG-03, STD-02 |

## Baseline

```yaml
gateways:
  shopify_payments: { enabled: true, methods: [cards, Apple Pay, Google Pay, Shop Pay], statement_descriptor: "NIBANDBARREL" }
  paypal_express:   { enabled: true, note: "kept for customers who prefer it (ADR-004)" }
  others: none                                  # STD-02: PCI DSS Level 1 providers only
checkout: Shopify-hosted only                   # SAQ A scope (REQ-07)
card_data_in_our_estate: none                   # no apps with card-field access; theme cannot touch checkout
three_d_secure: per Shopify Payments (SCA-compliant by default)
fraud: { shopify_fraud_analysis: on, high_risk_orders: hold for manual review by Ops Lead }
capture: automatic                              # engraving holds use fulfilment holds, not payment authorisation
payouts:
  shopify_payments: daily to Business Current Account (matched in SA-10)
  paypal: weekly manual sweep by Finance
refunds: Shopify admin only, by CS or Finance; target within 14 days (REQ-05, LEG-05)
saved_cards: Shop Pay only (Shopify-held). We never store cards ourselves (RQ-033 rejected)
pci_attestation: SAQ A, annual. Last completed 2026-09-30 (evidence indexed in the governance repository)
credentials:
  paypal_api: vault:1Password/Nib & Barrel/Finance/paypal-api
```
