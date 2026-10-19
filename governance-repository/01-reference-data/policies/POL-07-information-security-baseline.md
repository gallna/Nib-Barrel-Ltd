# POL-07: Information Security Baseline

| Status | Owner | Version | Approved | Date |
|---|---|---|---|---|
| Approved (incident annex pending) | Fractional architect | 0.9 | BM-2026-08-13 | 2026-08-13 |

## Purpose

A short, enforceable baseline for a 7-person company that runs almost entirely on SaaS. It turns PR-01 (customer trust) and PR-07 (compliance by design) into rules that staff can follow. The [capability maturity assessment](../../../architecture-repository/01-architecture-capability/capability-maturity.md) rates IT security at 2 out of 3. The missing piece is the incident procedure (GA-009).

## Rules

| # | Rule | Ref |
|---|---|---|
| 1 | Sign in with Google SSO and MFA (passkey or authenticator app). SMS-based MFA only where nothing else is offered. | REQ-12, STD-05 |
| 2 | Store passwords that cannot be SSO'd in 1Password (vault `Nib & Barrel`), never in documents, chat or code. | — |
| 3 | Refer to secrets in any repository by vault path only, e.g. `1Password: Nib & Barrel / Engineering / shopify-admin-api-token`. | AC-001 §2.7 |
| 4 | Payment card data never enters our systems: no card numbers by email, phone notes or helpdesk. Customers are pointed to the checkout. | REQ-07, STD-02a |
| 5 | Company devices only, managed through Google Admin (ChromeOS / macOS). The Windows engraving PC is isolated on its own VLAN. | STD-08, STD-09 |
| 6 | Apply vendor updates within 14 days, or within 48 hours for updates marked critical. | — |
| 7 | Personal data is kept only in its system of record. Do not download customer lists to laptops. | PR-02, LEG-01 |
| 8 | Report suspected incidents (phishing, lost device, wrong data sent) to the Ops Lead **immediately**, even outside working hours. | — |
| 9 | Use test personas, never real customers, in DSAR and restore drills. | POL-08 |

## Incident handling (interim)

Until the incident annex is approved (GA-009, due 2027-02):
1. The Ops Lead triages the incident and opens an `INV-yyyy-nn` investigation in [`02-process-status/investigations/`](../../02-process-status/investigations/).
2. If personal data may be affected, the MD decides **within 72 hours** whether to notify the ICO. The decision and its reasons are recorded in the investigation, whichever way it goes.
3. Containment changes during the freeze follow the emergency route in [POL-04](POL-04-change-freeze-policy.md#4-emergency-change).

## Open items
- GA-009: write an incident response annex (roles, ICO notification template, customer comms, contact list) by 2027-02.
