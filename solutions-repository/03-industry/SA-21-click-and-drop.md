# SA-21: Royal Mail Click & Drop Configuration

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Ops Lead | 1.1 | 2026-09-14 |

| SBB | Continuum | System of record | Lifecycle | Contract | Change refs |
|---|---|---|---|---|---|
| SBB-04 / APP-04 / INT-03, INT-04 | Industry | Click & Drop. **The baseline here is authoritative.** System of record for DE-07 Shipment | Active | [CTR-10](../contracts/contracts-register.md) | WP-01, GAP-07, RQ-010 |

## Baseline

```yaml
integration: Click & Drop Shopify integration
import:
  interval: 5 min                                  # INT-03
  import_statuses: [paid, unfulfilled]
  exclude: fulfilment orders "on hold"             # engraved orders appear only after INT-08 release
tracking_writeback: on label print                 # INT-04, then Shopify sends the shipping email
service_mapping:                                   # from the Shopify shipping rate name (SA-20)
  "Royal Mail Tracked 48": TPS48
  "Royal Mail Tracked 24": TPN24
  "DPD Next Day*": skip (manual DPD portal; CR-002 pending)
  default_weight_g: 120                            # single pen in a gift box
packaging_presets: [Pen box small 220×110×40, Ink bottle 150×100×100, Large letter]
labels: { format: 4x6in thermal, printer: fulfilment stations (SA-05) }   # minor decision 2026-08-14
packing_slip:
  template: "NB slip v2"
  shows: [order number, items, engraving yes/no flag (never the text), gift message when RQ-019 is delivered]
accounts:
  login: local (no SSO support); credentials at vault:1Password/Nib & Barrel/Fulfilment/click-and-drop
  users: [Ops Lead (admin), fulfilment operatives (individual logins)]
data_retention: shipments 2 years (DE-07)
```

## Notes
The packing slip deliberately never prints engraving text. That keeps DE-05 out of paper records, which cannot be purged at 90 days (REQ-09).
