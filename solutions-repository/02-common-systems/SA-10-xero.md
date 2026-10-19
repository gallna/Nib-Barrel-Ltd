# SA-10: Xero Configuration & Shopify Connector Mapping

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Finance Manager | 1.1 | 2026-09-14 |

| SBB | Continuum | System of record | Lifecycle | Contract | Change refs |
|---|---|---|---|---|---|
| SBB-03 / APP-03 / INT-02 | Common systems | Xero + official Shopify→Xero app. **The baseline here is authoritative.** | Active | [CTR-04](../contracts/contracts-register.md) | ADR-005, WP-04, GAP-06, REQ-05, REQ-06 |

[ADR-005](../../architecture-repository/05-governance-log/decision-log.md#adr-005) sets the core rule: **one daily summary invoice per channel**, plus payout and fee entries, and no per-order invoices. Order-level detail stays in Shopify (the DE-03 system of record).

## Connector mapping baseline

```yaml
connector: Shopify → Xero (official app)
posting_mode: daily_summary              # ADR-005; supersedes per-order posting (RQ-012 → RQ-013)
summary_cutoff: "23:59 Europe/London"
summaries_per_channel:
  - channel: Online Store                # web shop
    tracking_category: { Channel: Web }
  - channel: Amazon (imported via INT-01)
    tracking_category: { Channel: Amazon }

account_mapping:                         # Xero chart of accounts codes
  sales_pens:            "200  Sales – Pens & Inks"
  sales_engraving:       "202  Sales – Engraving"          # £7.50 add-on lines
  sales_gift_wrap:       "203  Sales – Gift Wrap"          # RQ-018, from 2026-10-15
  shipping_income:       "210  Shipping Income"
  discounts:             "220  Discounts Given"
  refunds:               "230  Sales Refunds"              # same-day credit note (REQ-05)
  gift_cards_liability:  "835  Gift Card Liability"
  payment_fees:          "404  Payment Processing Fees"
  amazon_fees:           "405  Marketplace Fees"
  clearing_shopify_payments: "090  Shopify Payments Clearing"
  clearing_paypal:           "091  PayPal Clearing"
  clearing_amazon:           "092  Amazon Clearing"
  rounding:              "860  Rounding"

tax:
  prices_include_vat: true
  default_rate: "20% (VAT on Income)"
  shipping_rate: "20% (VAT on Income)"   # follows the goods
  gift_cards: "No VAT (multi-purpose voucher)"

payouts:
  shopify_payments: { match_to: "Business Current Account", schedule: daily }
  paypal:           { match_to: "Business Current Account", schedule: weekly sweep }
  amazon:           { match_to: "Business Current Account", schedule: fortnightly settlement }

contacts: Suppliers (DE-08) are maintained in Xero. Customers are NOT synced (summary posting means no per-customer contacts).
mtd_vat: enabled (quarterly, MTD-compatible, LEG-06)
```

## Checks
- Month-end: each clearing account should be within ±£5 after payouts are matched. Payout reconciliation target ≤ 1 hr/month ([Order-to-Cash segment](../../architecture-repository/02-architecture-landscape/segment/order-to-cash.md)).
- The accountant reviewed this mapping for MTD on 2026-06-16 (ADR-005).
- Access: Finance Manager (adviser role), MD (standard), accountant (adviser, external). Everyone signs in with Google ([SA-03](../01-foundation/SA-03-google-workspace-security.md)).
