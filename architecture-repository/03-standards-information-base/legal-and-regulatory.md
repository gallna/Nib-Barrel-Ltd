# Standards Information Base — Legal & Regulatory Obligations

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Finance Manager + Architecture Lead | 1.1 | 2026-05-07 |

> Not legal advice. This is a summary of the obligations that shape our architecture. The authoritative source is our external adviser's annual review.

| ID | Obligation | Applies to | Architectural implication | Requirements |
|---|---|---|---|---|
| LEG-01 | **UK GDPR & Data Protection Act 2018** | DE-04, DE-05, DE-11, DE-13 | Lawful basis recorded per entity; retention configured; DSAR/erasure runbook; DPAs with every processor; records of processing | REQ-08, REQ-09 |
| LEG-02 | **PECR** (Privacy and Electronic Communications Regs) | DE-11, marketing email/SMS, cookies | Explicit opt-in at checkout, not pre-ticked; cookie consent banner before analytics fire | REQ-08 |
| LEG-03 | **PCI DSS v4.0** | Payments | Use hosted checkout only (SAQ A scope); annual SAQ A attestation | REQ-07 |
| LEG-04 | **Consumer Contracts Regulations 2013** | Orders, returns | 14-day cancellation right; **personalised goods exempt**, so checkout must state this clearly before purchase | REQ-04 |
| LEG-05 | **Consumer Rights Act 2015** | Goods quality, refunds | Faulty-goods returns process; refunds within 14 days | REQ-05 |
| LEG-06 | **HMRC record keeping / Making Tax Digital (VAT)** | DE-03, DE-06, DE-12 | 6-year retention; MTD-compatible software (Xero) | REQ-06 |
| LEG-07 | **Amazon Selling Partner policies** | APP-07/08 | Dispatch within stated handling time; valid tracking; connector must use approved SP-API app | REQ-15 |
| LEG-08 | **Equality Act 2010 / accessibility** (good practice: WCAG 2.2 AA) | Storefront, engraving preview | Accessible theme; preview must be operable by keyboard and screen reader | REQ-03 |

## Processor register (summary)

| Processor | Data | DPA in place | Transfer mechanism |
|---|---|---|---|
| Shopify | DE-01–04, DE-10, DE-11 | ✅ | UK IDTA / adequacy |
| Klaviyo | DE-04, DE-11 | ✅ | UK IDTA |
| Gorgias | DE-04, DE-13 | ✅ | UK IDTA |
| Cloudflare | DE-05 | ✅ | UK IDTA; D1 database pinned to EU region |
| Xero | DE-08, DE-12 | ✅ | Adequacy |
| Royal Mail | DE-04 (address), DE-07 | ✅ | UK |
