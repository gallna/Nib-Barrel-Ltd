# CA-2026-001: Compliance Assessment — WP-01 Shopify Re-platform

| Assessed | Assessor | Phase | Contract |
|---|---|---|---|
| 2026-09-08 | Fractional architect + Ops Lead | Pre-go-live | Agency SOW (fixed price) |

| # | Check | Ref | Result | Evidence / notes |
|---|---|---|---|---|
| 1 | Shopify is the system of record for DE-01–04 and DE-09–10; WooCommerce set to read-only | PR-02 | ✅ | Woo admin locked; checkout disabled |
| 2 | Only approved integrations installed (Xero, Click & Drop, Matrixify) | STD-03 | ⚠️ | Agency installed a "reviews" app that wasn't approved; **removed 2026-09-09** |
| 3 | Hosted checkout only; no card data in theme or apps | REQ-07 | ✅ | SAQ A eligibility confirmed |
| 4 | Personalised-goods cancellation exemption shown at checkout | REQ-04 | ✅ | Screenshot in evidence folder |
| 5 | Consent checkbox unticked by default | REQ-08 | ✅ | |
| 6 | All staff on Google SSO + MFA | REQ-12 | ✅ | 7/7 accounts |
| 7 | 301 redirects for all 612 indexed URLs | Vision risk | ✅ | Crawl test: 0 404s |
| 8 | Load test at 3× average (300 orders/day equivalent) | REQ-11 | ✅ | Vendor-managed; checkout tested with 40 concurrent sessions |
| 9 | Weekly export running; first restore drill done | REQ-13 | ⚠️ | Export running; **restore drill due by 2026-10-15** |
| 10 | Repository updated (application catalogue, interface catalogue) | — | ✅ | |

## Outcome
**Compliant with conditions.** Go-live approved for 2026-09-14.

| Condition | Owner | Due | Status |
|---|---|---|---|
| Complete first restore drill from weekly export | Ops Lead | 2026-10-15 | ✅ Done 2026-10-06 |
