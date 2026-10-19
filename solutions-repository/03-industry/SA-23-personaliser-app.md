# SA-23: Product Personaliser App Configuration

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Ops Lead | 1.0 | 2026-10-09 |

| SBB | Continuum | System of record | Lifecycle | Contract | Change refs |
|---|---|---|---|---|---|
| SBB-01a (Personalisation Capture & Preview) on APP-01 | Industry | Personaliser app. **The baseline here is authoritative.** | Active (**pilot**: 3 SKUs, 2026-10-12 → 2026-10-30) | [CTR-08](../contracts/contracts-register.md) | ADR-006 option B, REQ-01, REQ-02, REQ-03, CA-2026-002 |

This is the "buy" half of [ADR-006](../../architecture-repository/05-governance-log/decision-log.md#adr-006). It captures the text and font and shows a live preview. Production happens in [SA-30](../04-organisation-specific/SA-30-engraving-queue.md).

## Baseline

```yaml
enabled_on:
  pilot_skus: [NB-FP-0142, NB-FP-0187, NB-BP-0033]          # full rollout: all SKUs with engraving.eligible=true
add_on_price: 7.50                                          # adds hidden product "Engraving" to cart
fields:
  - { key: _engraving_line_1, label: "Line 1", required: true }
  - { key: _engraving_line_2, label: "Line 2 (optional)", required: false, only_if: "engraving.lines = 2" }
  - { key: _engraving_font,   label: "Font", options: [Classic Serif, Copperplate Script, Block Sans], default: Classic Serif }
validation:                                                 # REQ-02. SA-30 re-validates server-side
  max_chars_source: product metafield engraving.max_chars   # SA-33, e.g. 20 for most barrels, 12 for slim
  charset: "A–Z a–z 0–9 space . , ' & - ! ? and Latin-1 accented letters (é, ö, ñ …)"   # STD-11 UTF-8
  trim_whitespace: true
  profanity_filter: on (vendor list + our additions, maintained by CS Lead)
  emoji: rejected
preview:
  type: live SVG on product page, true-scale outline of the barrel
  accessibility: keyboard operable; preview text also read by screen readers (aria-live)
  known_issue: font-picker contrast below WCAG 2.2 AA     # CA-2026-002 check 7 → CR-005 / RQ-039 / GA-003
  fallback_fix: theme CSS override in SA-32 if the vendor has not fixed it by 2027-01-04
data_held_by_vendor: engraving text inside cart/line-item properties only; vendor stores none (confirmed in DPA)
cancellation_notice: rendered under the fields (REQ-04 text from SA-20)
```

## Exit
The app's settings export is JSON only and has no data of its own (the text lives in Shopify orders). It is rated "partial pass" on the exit test (see [CTR-08](../contracts/contracts-register.md)), which is acceptable because the asset holds configuration only.
