# Vendor Contracts & Licences Register

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Finance Manager + Ops Lead | 1.0 | 2026-10-19 |

Contract documents are held in `NB-Governance/Contracts/` (restricted Google shared drive). This register holds no contract copies, account numbers or credentials.

Costs match the [application portfolio catalogue](../../architecture-repository/02-architecture-landscape/strategic/application-architecture.md) (target annual cost). The DPA column refers to the [processor register](../../architecture-repository/03-standards-information-base/legal-and-regulatory.md#processor-register-summary). The exit test is the [vendor evaluation](../../architecture-repository/04-reference-library/templates/vendor-evaluation-template.md) "export all data and open it with IDs intact" test (PR-06).

## Register

| CTR | Vendor / product | Assets | Term | Renewal / notice | Annual cost | DPA | Exit test | Owner | Next action |
|---|---|---|---|---|---|---|---|---|---|
| CTR-01 | Shopify Advanced (incl. Shopify Payments) | SA-20, SA-14, SA-33 | Annual, 2026-09-14 → 2027-09-13 | Auto-renews; downgrade notice 30 days | £3,500 + payment fees (~1.5% + 20p) | ✅ in AR register | ✅ Pass (ADR-004; Matrixify export) | Ops Lead | 2027-07-15: renewal review |
| CTR-02 | Google Workspace Business Standard | SA-03, SA-04 | Annual, renews 2027-03-31 | 30 days | £900 | ✅ (not yet in AR register) | ✅ Pass (Takeout) | MD | 2027-02-28: seat count review |
| CTR-03 | Cloudflare (Workers Paid + D1; DNS, Access on free tier) | SA-01, SA-02, SA-30 | Monthly | Any time | ~£420 (< £40/month at peak, ADR-007) | ✅ in AR register | ✅ Pass (D1 export, zone file) | Ops Lead | 2027-03: annual vendor review |
| CTR-04 | Xero Standard | SA-10 | Monthly | Any time | £600 | ✅ in AR register | ✅ Pass (CSV + reports) | Finance Manager | 2027-03: annual vendor review |
| CTR-05 | Klaviyo (email, by contact count) | SA-11 | Monthly, from 2026-10-01 | Any time; price tier changes at 15k profiles | £1,400 | ✅ in AR register | ✅ Pass (profile + consent CSV) | Marketing Manager | 2027-01-31: tier check after the Q4 list growth |
| CTR-06 | Gorgias Basic | SA-12 | Monthly, from 2026-10-01 | Any time; ticket overage billed | £1,100 | ✅ in AR register | ✅ Pass (ticket CSV export) | CS Lead | 2027-01-31: ticket volume vs plan |
| CTR-07 | Matrixify | SA-13 | Monthly | Any time | £240 (£20/month) | ✅ (not yet in AR register) | N/A: it *is* the export tool | Ops Lead | 2027-03: annual vendor review |
| CTR-08 | Product personaliser app | SA-23 | Monthly, from 2026-08-20 | Any time | ~£190 (£16/month) | ✅ (not yet in AR register) | ⚠️ Partial: settings export only; no data held | Ops Lead | 2027-01-04: font-picker fix deadline (CR-005) |
| CTR-09 | Marketplace connector app | SA-22 | Monthly, from 2026-09-21 | Any time | £360 | ✅ (not yet in AR register) | ✅ Pass (SKU map CSV) | Ops Lead | After INV-2026-01: confirm it meets REQ-15 |
| CTR-10 | Royal Mail Click & Drop | SA-21 | Rolling, no fee | — | Free (per-label postage) | ✅ in AR register | ✅ Pass (shipment CSV) | Ops Lead | — |
| CTR-11 | Amazon Seller Central (Professional) | SA-22 | Monthly | Any time | £300 + referral fees | ✅ Amazon BSA terms (not yet in AR register) | ✅ Pass (order reports) | Ops Lead | — |
| CTR-12 | Independent software contractor: AC-001 build + support retainer | SA-30, SA-31 | Build: fixed price £12k (signed 2026-07-30). Retainer: 4 h/month for 12 months after rollout (to 2028-01) | Retainer: 1 month notice either side | Build £12k (one-off); retainer billed monthly | ✅ Sub-processor clause in AC-001 | ✅ IP and source owned by Nib & Barrel (AC-001 §4) | Ops Lead | 2027-01-11: final payment after the D5 handover |
| CTR-13 | Shopify agency: WP-01 fixed-price SOW | SA-20, SA-32 | 2026-06-15 → 2026-09-28 (closed) | — | £18k (one-off, WP-01) | ✅ (ended; access revoked 2026-09-28) | ✅ Theme in our GitHub | Ops Lead | Closed |
| CTR-14 | Shared PHP hosting (cPanel) | SA-90 | Annual, ends 2026-12-31 | **Cancelled**: not renewing | — | ✅ (ends) | ✅ Final export planned 2026-12-14 | Ops Lead | 2026-12-14: decommission (see DSP-003) |
| CTR-15 | Fractional architect (2 days/month) | — (advisory) | Rolling monthly | 1 month | Day rate held by Finance | ✅ NDA + DPA addendum | N/A | MD | 2027-04: review with the charter |
| CTR-16 | PayPal Business | SA-14 | Rolling | Any time | Transaction fees only | ✅ (not yet in AR register) | ✅ Pass (transaction CSV) | Finance Manager | — |
| CTR-17 | Mailchimp | (retiring; replaced by SA-11) | Monthly | **Closing 2026-11-20** | — | ✅ (ends) | ✅ Audience + consent log exported | Marketing Manager | 2026-11-20: export, then close the account (ADR-008) |

## Findings for the Architecture Lead
- **The processor register in the AR is incomplete.** Google, Matrixify, the personaliser app, the marketplace connector, Amazon and PayPal all process personal data but are not listed in the [SIB processor register](../../architecture-repository/03-standards-information-base/legal-and-regulatory.md). This is tracked as **GA-010** in the governance repository; the SIB update goes to the Board on 2026-11-05.
- **Renewal concentration:** none of the annual contracts renews during the Q4 freeze.
