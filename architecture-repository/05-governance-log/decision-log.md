# Architecture Decision Log

Decisions approved by the Architecture Board. Minor decisions approved by the Ops Lead are listed at the end. The full template is in [templates/adr-template.md](../04-reference-library/templates/adr-template.md).

| ADR | Title | Status | Date |
|---|---|---|---|
| [ADR-001](#adr-001) | Adopt a tailored TOGAF approach with a Git-based repository | Accepted | 2026-03-12 |
| [ADR-002](#adr-002) | Architecture Principles v2.0 | Accepted | 2026-04-09 |
| [ADR-003](#adr-003) | Approve Statement of Architecture Work: Project Quill | Accepted | 2026-04-23 |
| [ADR-004](#adr-004) | Re-platform from WooCommerce to Shopify | Accepted | 2026-06-04 |
| [ADR-005](#adr-005) | Post daily summaries, not per-order invoices, to Xero | Accepted | 2026-06-18 |
| [ADR-006](#adr-006) | Build a custom Engraving Queue rather than buy a personaliser app | Accepted | 2026-06-18 |
| [ADR-007](#adr-007) | Host the Engraving Queue on Cloudflare Workers + D1 | Accepted | 2026-07-02 |
| [ADR-008](#adr-008) | Replace Mailchimp with Klaviyo | Accepted | 2026-07-02 |

---

## ADR-001
**Adopt a tailored TOGAF approach with a Git-based repository** · Accepted · 2026-03-12

**Context:** Growth is causing ad hoc tool choices: 31 WooCommerce plugins, 3 stock copies. We need a lightweight way to make and remember decisions.
**Decision:** Use the TOGAF ADM tailored for a 7-person company, with the Architecture Repository held as Markdown in GitHub.
**Rejected:** a commercial EA tool (cost and overhead), and a Confluence space (not diffable, and drifted from reality last time).
**Consequences:** The Ops Lead spends ~4 hrs/week on architecture during active cycles. The fractional architect is retained for 2 days/month.

## ADR-002
**Architecture Principles v2.0** · Accepted · 2026-04-09

**Decision:** Adopt the seven principles in [architecture-principles.md](../01-architecture-capability/architecture-principles.md). v2.0 adds PR-05 (peak) and PR-07 (compliance) after the Black Friday 2025 outage and a review of how consent was being recorded.

## ADR-003
**Approve Statement of Architecture Work: Project Quill** · Accepted · 2026-04-23

**Decision:** Approve the [Architecture Vision](../02-architecture-landscape/strategic/architecture-vision.md), scope and £38k budget. Go-live for the re-platform has a hard deadline of 2026-09-15 to avoid the Q4 freeze.

## ADR-004
**Re-platform from WooCommerce to Shopify** · Accepted · 2026-06-04

**Context:** DRV-03 (peak outages, plugin rot), GOL-04 (99.9% Q4 availability), PR-03 (buy before build), PR-05 (design for peak).

| Option | Pros | Cons | 3-yr TCO |
|---|---|---|---|
| A. Stay on WooCommerce, move to managed WP hosting | Lowest migration effort; keeps URLs | Still maintains 31 plugins; still our problem at peak | £27k |
| **B. Shopify Advanced** | Vendor-managed scaling; native integrations for Xero, Click & Drop, Klaviyo, Gorgias, Amazon; line-item properties for engraving | Transaction fees if not using Shopify Payments; some lock-in | **£24k** |
| C. BigCommerce | Strong B2B features; no transaction fees | Fewer UK-specific integrations; B2B is out of scope | £26k |

**Decision:** Option B.
**Principles check:** PR-03 ✅, PR-05 ✅, PR-02 ✅ (becomes the single system of record), PR-06 ⚠️ lock-in, mitigated by weekly exports (PAT-03) and a passed exit test.
**Consequences:** 301-redirect map is required (SEO risk). Shopify Payments is the default gateway, with PayPal kept for customers who prefer it.

## ADR-005
**Post daily summaries to Xero** · Accepted · 2026-06-18

**Decision:** The Shopify→Xero integration posts one daily summary invoice per channel, plus payout and fee entries, rather than one invoice per order.
**Rationale:** Per-order posting (~100/day) clutters the ledger and needs a higher Xero plan. Order-level detail stays in Shopify (the system of record for DE-03). The accountant confirmed this is acceptable for VAT under MTD.

## ADR-006
**Build a custom Engraving Queue rather than buy** · Accepted · 2026-06-18

**Context:** DRV-01, GOL-01. PR-03 says buy first, so this ADR must justify a build.

| Option | Pros | Cons |
|---|---|---|
| A. Off-the-shelf "product personaliser" Shopify app | Fast; capture + preview | None of them drive our laser software or track proof → engrave → QC; we'd still retype text |
| B. Personaliser app for capture/preview **+** custom queue for production | Buy the commodity part (capture/preview) and build only the differentiator | Two components to manage |
| C. Full custom build including preview | Total control | Most code; least aligned with PR-03 |

**Decision:** Option B. Buy the customer-facing capture and preview (SBB-01a), and build a small production queue (APP-09).
**Why this passes PR-03:** Personalisation is a strategic differentiator (BC-05 ⭐), and no product on the market integrates with our engraving device workflow. The build is capped at < 2,000 LOC and governed by [AC-001](../06-architecture-requirements/architecture-contracts/AC-001-engraving-queue.md).

## ADR-007
**Host the Engraving Queue on Cloudflare Workers + D1** · Accepted · 2026-07-02

**Options:** Cloudflare Workers + D1 · Vercel + managed Postgres · a small VPS.
**Decision:** Cloudflare Workers + D1. We already use Cloudflare for DNS (STD-06). Cloudflare Access gives us Google SSO without writing auth code. No servers to patch. Cost is under £40/month at peak.
**Rejected:** VPS (prohibited by STD-04a, since we have no ops capacity). Vercel (comparable, but would add a separate vendor and require building auth).

## ADR-008
**Replace Mailchimp with Klaviyo** · Accepted · 2026-07-02

**Decision:** Klaviyo, using its native Shopify integration. Consent is imported with source and timestamp preserved. Mailchimp contacts without provable opt-in are **not** migrated (LEG-02).
**Consequence:** The list shrinks from 18.2k to an estimated 11.5k contacts, which the Marketing Manager has accepted.

---

## Minor decisions (Ops Lead)

| Date | Decision | Rationale |
|---|---|---|
| 2026-05-02 | Use Matrixify for weekly Shopify exports | Implements PAT-03; £20/month |
| 2026-06-20 | Standard Shopify theme "Dawn" (customised), no page builder | Accessibility, performance, fewer apps |
| 2026-08-14 | Thermal label printers standardised on 4×6" | Click & Drop + DPD both support it |
