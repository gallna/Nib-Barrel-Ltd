# SA-30: Engraving Queue Application

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Ops Lead | 1.0 | 2026-10-12 |

| SBB | Continuum | System of record | Lifecycle | Contract | Change refs |
|---|---|---|---|---|---|
| SBB-09 / APP-09 / TEC-04 / INT-07, INT-08, INT-09 | Organisation-specific | **GitHub** `github.com/nib-and-barrel/engraving-queue`. This is an **index record only**. | Active (**pilot**) → full rollout 2027-01-11 | [CTR-12](../contracts/contracts-register.md) (AC-001 + retainer), [CTR-03](../contracts/contracts-register.md) | ADR-006, ADR-007, AC-001, CA-2026-002, DSP-001 |

Design: [capability architecture BC-05](../../architecture-repository/02-architecture-landscape/capability/personalised-engraving.md). Contract: [AC-001](../../architecture-repository/06-architecture-requirements/architecture-contracts/AC-001-engraving-queue.md). Source code, schema and the detailed runbook live in the repository above, and are **not** copied here.

## Index

| Attribute | Value |
|---|---|
| Repository | `github.com/nib-and-barrel/engraving-queue` (private; branch protection on `main`, 1 review required, STD-10) |
| Language / runtime | TypeScript on Cloudflare Workers + D1 (STD-04) |
| Deployed version (prod) | **v0.9.2** (2026-10-12, pilot start) |
| Next release | **v1.0.0**, planned for full rollout 2027-01-11, after CA-2026-004 (2027-01-07) |
| Size | 1,640 LOC excluding tests and generated code (AC-001 cap: < 2,000) |
| Tests | CI green on `main`; job-state transition coverage **91%** (AC-001 requires ≥ 80%) |
| CI/CD | GitHub Actions: lint → test → `wrangler deploy --env staging` on merge; prod deploy is manual, approved by the Ops Lead |
| Owner / maintainer | Ops Lead (accountable) / independent contractor (AC-001; retainer 4 h/month after rollout) |
| Users | Fulfilment operatives (ACT-02), Ops Lead (ACT-03), via [SA-02](../01-foundation/SA-02-cloudflare-access.md) |
| Data held | DE-05 Personalisation Spec + Shopify order ID + SKU + QC photo. No addresses, emails or payment data |

## Environments

| Env | Worker | Hostname | D1 database | Shopify store | Notes |
|---|---|---|---|---|---|
| prod | `engraving-queue-prod` | `queue.nibandbarrel.co.uk` | `eq-prod` (EU jurisdiction) | `nib-and-barrel.myshopify.com` | PITR on, 30 days (REQ-13) |
| staging | `engraving-queue-staging` | `queue-staging.nibandbarrel.co.uk` | `eq-staging` (EU) | `nib-and-barrel-dev.myshopify.com` | Test orders only, no real customer text |

## Scheduled jobs (Worker cron triggers)

| Cron (UTC) | Job | Requirement |
|---|---|---|
| `30 2 * * *` | Purge DE-05 text and QC photos 90 days after delivery (state `Released` → `Purged`) | REQ-09 |
| `0 3 * * 0` | Weekly JSON export of open jobs to NB-Exports (SA-04) | REQ-13, PAT-03 |
| `*/10 * * * *` | Reconcile: find Shopify orders on hold with no job (a missed webhook) and alert ops@ | PAT-02 |

## Secrets (names only; values are in Worker secrets and 1Password)

| Worker secret | Vault reference |
|---|---|
| `SHOPIFY_WEBHOOK_SECRET` | `vault:1Password/Nib & Barrel/Engineering/eq-shopify-webhook-secret` |
| `SHOPIFY_ADMIN_TOKEN` | `vault:1Password/Nib & Barrel/Engineering/eq-shopify-admin-token` |
| `CF_ACCESS_AUD` (not secret, config) | in `wrangler.toml` |
| `AGENT_SERVICE_TOKEN_ID` | `vault:1Password/Nib & Barrel/Engineering/eq-engraving-pc-access-client-id` |

Rotation: Shopify tokens on contractor offboarding or yearly. The Access service token expires 2027-10 ([SA-02](../01-foundation/SA-02-cloudflare-access.md)).

## Interfaces

| INT | Direction | Detail |
|---|---|---|
| INT-07 | Shopify → EQ | `orders/paid` webhook, HMAC-verified, idempotent on order ID (REQ-14) |
| INT-08 | EQ → Shopify | Release fulfilment hold, Admin GraphQL API version 2026-07 |
| INT-09 | EQ → engraving PC | Job file; see [SA-31](SA-31-job-file-format.md) |

## Runbooks
[RB-03 outage fallback](../runbooks/RB-03-engraving-queue-outage.md) · [RB-04 redeploy from scratch](../runbooks/RB-04-engraving-queue-redeploy.md) · [RB-07 Shopify API upgrade](../runbooks/RB-07-shopify-api-upgrade.md)

## Compliance
[CA-2026-002](../../architecture-repository/05-governance-log/compliance-assessments/CA-2026-002-engraving-queue-pilot.md) (pre-pilot): compliant with conditions. **CA-2026-004** (before full rollout) is planned for 2027-01-07. During the pilot, non-pilot engraved orders follow [DSP-001](../../architecture-repository/05-governance-log/dispensations.md).
