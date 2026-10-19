# SA-32: Customised Dawn Theme "nb-dawn"

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Ops Lead | v2.3.0 | 2026-10-15 |

| SBB | Continuum | System of record | Lifecycle | Contract | Change refs |
|---|---|---|---|---|---|
| SBB-01 (storefront presentation) | Organisation-specific | **GitHub** `github.com/nib-and-barrel/nb-dawn` (Shopify GitHub integration). **Index record only.** | Active | [CTR-13](../contracts/contracts-register.md) (agency build, closed) | Minor decision 2026-06-20 (Dawn, no page builder), REQ-03, RQ-018 |

| Attribute | Value |
|---|---|
| Base | Shopify Dawn (upstream tracked on branch `upstream`) |
| Live version | v2.3.0 (2026-10-15: gift-wrap cart add-on) |
| Branching | `main` = live theme (Shopify GitHub sync); changes via PR from a feature branch, previewed on the dev store |
| Customisations | Pen attribute filters (SA-33 metafields); engraving field block for SA-23; cancellation-notice snippet (REQ-04); gift-wrap add-on (RQ-018) |
| Page builder apps | None allowed (performance, accessibility) |
| Accessibility | Lighthouse accessibility ≥ 95 on the home, collection and product templates, checked on each release; full WCAG 2.2 AA audit in CA-2026-004 |
| Pending | CSS override for the font-picker contrast if the vendor misses 2027-01-04 (CR-005 / RQ-039) |
| Freeze | No theme publishes 2026-11-01 → 2027-01-05 except security or legal fixes |
