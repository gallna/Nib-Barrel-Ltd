# Configuration Register (CMDB-lite)

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Ops Lead | 1.4 | 2026-10-19 |

What is deployed where, at which version, and what changed last. Update it in the **same PR** as any asset baseline change.

**Freeze status:** 🟢 Open until 2026-10-31 · 🔴 **Q4 change freeze 2026-11-01 → 2027-01-05** (security fixes only; decommissions and read-only reviews allowed, see POL-04 in the [governance repository](../governance-repository/)).

## Environments

| Environment | What | Used for |
|---|---|---|
| Production | `nib-and-barrel.myshopify.com`, `engraving-queue-prod`, live SaaS tenants | Trading |
| Dev / staging | `nib-and-barrel-dev.myshopify.com` (development store), `engraving-queue-staging`, theme previews | Testing, drills (RB-02), contractor work |

There is no staging tenant for Klaviyo, Gorgias, Xero or Click & Drop. Changes are tested on a test profile or test order in production, and recorded here.

## Configuration items

| CI | Asset | Environment | Deployed version / baseline | Last change | Change ref | Freeze status |
|---|---|---|---|---|---|---|
| CI-01 | Shopify store (SA-20) | Prod | Baseline 1.3 | 2026-10-15: gift-wrap add-on | RQ-018 | Frozen from 11-01 |
| CI-02 | nb-dawn theme (SA-32) | Prod | v2.3.0 | 2026-10-15 | RQ-018 | Frozen from 11-01 |
| CI-03 | Pen metafields (SA-33) | Prod | v1.1 | 2026-09-01 | WP-03 prep | Frozen from 11-01 |
| CI-04 | Payments (SA-14) | Prod | Baseline 1.0 | 2026-09-14: go-live | ADR-004 | Frozen from 11-01 |
| CI-05 | Personaliser app (SA-23) | Prod (3 pilot SKUs) | Baseline 1.0, app v4.12 (vendor) | 2026-10-12: pilot start | CA-2026-002 | Vendor contrast fix allowed (accessibility defect, CR-005) |
| CI-06 | Engraving Queue (SA-30) | Prod | **v0.9.2** (tag `v0.9.2`, deployment `d7f3…`) | 2026-10-12: pilot | AC-001, CA-2026-002 | Defect fixes only during pilot; v1.0.0 on 2027-01-11 |
| CI-07 | Engraving Queue (SA-30) | Staging | v0.9.3-rc.1 | 2026-10-16 | Pilot defect fixes | Not frozen (staging) |
| CI-08 | EQ job agent on engraving PC (SA-05/SA-31) | Prod | agent v0.4.0, job-file format v1 | 2026-10-09 | AC-001 | Frozen from 11-01 |
| CI-09 | Webhook `orders/paid` → EQ | Prod | API version 2026-07 | 2026-10-12 | INT-07 | Upgrade to 2027-01 with v1.0.0 (RB-07) |
| CI-10 | Click & Drop (SA-21) | Prod | Baseline 1.1 | 2026-09-14 | WP-01 | Frozen from 11-01 |
| CI-11 | Xero + connector (SA-10) | Prod | Baseline 1.1 | 2026-10-15: account 203 Gift Wrap added | RQ-018 | Frozen from 11-01 |
| CI-12 | Marketplace connector (SA-22) | Prod | Baseline 1.1 | 2026-10-06: low-stock buffer + token alert | INV-2026-01 (interim) | 🔴 Frozen. A further INV-2026-01 fix during the freeze goes through the POL-04 §4 emergency-change route (Ops Lead + MD) |
| CI-13 | Klaviyo (SA-11) | Prod | Baseline 1.0 | **Go-live 2026-10-20** | ADR-008, WP-05 | Must be live by 10-31, else move to January |
| CI-14 | Gorgias (SA-12) | Prod | Baseline 1.0 | **Go-live 2026-10-27** | WP-05 | Must be live by 10-31, else move to January |
| CI-15 | Matrixify jobs (SA-13) | Prod | Baseline 1.2 | 2026-10-06: added Metafields sheet | RB-02 drill finding | Frozen from 11-01 |
| CI-16 | Cloudflare DNS (SA-01) | Prod | Baseline 1.1 | 2026-09-14: cut-over | WP-01 | `old` record removed at decommission (allowed) |
| CI-17 | Cloudflare Access (SA-02) | Prod | Baseline 1.0 | 2026-10-09 | CA-2026-002 | Membership changes allowed (joiners/leavers) |
| CI-18 | Google Workspace (SA-03) | Prod | Baseline 1.2 | 2026-09-30: access review | REQ-12 | Joiners/leavers allowed (seasonal staff) |
| CI-19 | Office network (SA-06) | Prod | Baseline 1.0, router firmware auto | 2026-07-20 | WP-06 | Firmware security updates allowed |
| CI-20 | WooCommerce (SA-90) | Legacy | Read-only | 2026-09-14 | ADR-004 | Decommission 2026-12-14 (allowed), unless DSP-003 is approved |

## Scheduled changes after the freeze

| Planned | Change | Ref | CA |
|---|---|---|---|
| 2027-01-11 | Engraving Queue v1.0.0, full rollout to all engravable SKUs; personaliser app on all SKUs | WP-03, DSP-001 ends 2027-01-31 | CA-2026-004 (2027-01-07) |
| 2027-01-11 | Shopify native self-serve returns | CR-003 / RQ-017 | Minor (Ops Lead) |
| 2027-01 | Gorgias chat widget | RQ-037 | Minor |
| 2027-01 | DPD label automation, if approved | CR-002 / RQ-036 | Needs an ADR first |
| by 2027-01-04 | Font-picker contrast (vendor fix or SA-32 CSS override) | CR-005 / RQ-039 | Checked in CA-2026-004 |
