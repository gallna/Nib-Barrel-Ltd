# SA-33: Pen Product Data Model (Shopify Metafield Definitions)

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Ops Lead | v1.1 | 2026-09-01 |

| SBB | Continuum | System of record | Lifecycle | Change refs |
|---|---|---|---|---|
| SBB-01 / DE-01 Product | Organisation-specific | Shopify metafield definitions. **The baseline here is authoritative.** | Active | BC-01 (strategic differentiator: curation), BP-01, REQ-02 |

This is our curation expressed as data. It extends the [DE-01 Product](../../architecture-repository/02-architecture-landscape/strategic/data-architecture.md) entity.

```yaml
namespace: pen
definitions:
  - { key: nib_size,     type: single_line_text, choices: [EF, F, M, B, Stub 1.1, Italic], applies_to: fountain pens }
  - { key: nib_material, type: single_line_text, choices: [Steel, Gold 14k, Gold 18k, Titanium] }
  - { key: fill_system,  type: single_line_text, choices: [Cartridge/converter, Piston, Vacuum, Eyedropper] }
  - { key: body_material,type: single_line_text, choices: [Resin, Metal, Wood, Celluloid, Ebonite] }
  - { key: refill_type,  type: single_line_text, applies_to: ballpoints/rollerballs, note: "links to refill compatibility" }
namespace: ink
definitions:
  - { key: type,          type: single_line_text, choices: [Dye, Pigment, Iron gall, Shimmer] }
  - { key: volume_ml,     type: number_integer }
  - { key: colour_family, type: single_line_text }
namespace: engraving
definitions:
  - { key: eligible,      type: boolean, default: false }
  - { key: max_chars,     type: number_integer, validation: "1..30", required_if: eligible }   # drives SA-23 and SA-30 validation
  - { key: lines,         type: number_integer, validation: "1..2", default: 1 }
  - { key: template,      type: single_line_text, note: "laser template name, SA-31" }
  - { key: four_eyes,     type: boolean, computed: "price > 150", note: "4-eyes proof check (RQ-006)" }
```

v1.1 (2026-09-01) added `engraving.lines` and `engraving.template`, needed by the Engraving Queue pilot.
