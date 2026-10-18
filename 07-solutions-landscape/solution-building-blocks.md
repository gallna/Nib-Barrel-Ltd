# Solutions Landscape — Solution Building Blocks

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Architecture Lead | 1.2 | 2026-10-09 |

Each Architecture Building Block (ABB, the *what*) maps to the Solution Building Block (SBB, the *product or implementation*) that realises it.

| SBB | Solution | Realises ABB | Application / Tech ID | Lifecycle | Contract / renewal |
|---|---|---|---|---|---|
| SBB-01 | Shopify Advanced | Commerce Engine; Product Information Store; Inventory Ledger; Order Manager | APP-01 / TEC-02 | Live (2026-09-14) | Annual, renews Sep |
| SBB-01a | Product personaliser app (Shopify App Store) | Personalisation Capture & Preview | on APP-01 | Pilot | Monthly |
| SBB-02 | Shopify Payments + PayPal | Payment Service | APP-02 | Live | Rolling |
| SBB-03 | Xero Standard + official Shopify connector | General Ledger; Sales Posting | APP-03 / INT-02 | Live | Monthly |
| SBB-04 | Royal Mail Click & Drop | Shipping Label Service | APP-04 / INT-03-04 | Live | Free |
| SBB-05 | Klaviyo | Customer Engagement Service; Consent Store | APP-05 | Live (2026-10-20) | Monthly, by contact count |
| SBB-06 | Gorgias Basic | Customer Support Desk | APP-06 | Live (2026-10-27) | Monthly |
| SBB-07 | Amazon Seller Central | Marketplace Channel | APP-07 | Live | Monthly |
| SBB-08 | Marketplace connector app | Channel Sync Service | APP-08 / INT-01 | Implementing | Monthly |
| SBB-09 | Engraving Queue (custom, TypeScript on Cloudflare Workers + D1) | Personalisation Workflow Service; Proof Renderer; Production Device Adapter | APP-09 / TEC-04 / INT-07-09 | Pilot → rollout 2027-01 | AC-001 + retainer |
| SBB-10 | Google Workspace Business Standard | Identity Provider; Productivity | APP-10 / TEC-05 | Live | Annual |
| SBB-11 | Cloudflare (DNS, Access, Workers) | DNS; Zero-Trust Access; Serverless Runtime | TEC-04, TEC-06 | Live | Monthly |
| SBB-12 | Matrixify | Bulk Data Export | INT-10 / PAT-03 | Live | Monthly |
| SBB-13 | WooCommerce on shared hosting | (legacy) Commerce Engine | APP-B1 / TEC-01 | **Read-only; decommission 2026-12-14** | Hosting cancelled at end of term |

## Retirement plan (legacy SBBs)

| SBB | Action | Date | Data handling |
|---|---|---|---|
| SBB-13 WooCommerce | Final DB export to TEC-07 (encrypted), then delete hosting | 2026-12-14 | Orders kept 6 yrs in export (REQ-06) |
| Mailchimp | Export audience + consent log, then close account | 2026-11-20 | Non-migrated contacts deleted (ADR-008) |
| Stock spreadsheet | Archive as read-only | 2026-10-31 | No personal data |
| Shared Gmail inbox | Converted to forwarding alias → Gorgias | 2026-10-27 | Historic mail kept 2 yrs, then purged |
