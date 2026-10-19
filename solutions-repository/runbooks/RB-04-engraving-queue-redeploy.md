# RB-04: Engraving Queue: Redeploy from Scratch

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Ops Lead | 1.0 | 2026-10-12 |

| Implements | Contract | Authoritative detail |
|---|---|---|
| AC-001 deliverable D3 ("Ops Lead can redeploy from scratch by following the runbook") | [AC-001](../../architecture-repository/06-architecture-requirements/architecture-contracts/AC-001-engraving-queue.md) | `engraving-queue/docs/runbook.md` in GitHub. **That file is the record.** This page is the summary and checklist |

## Checklist

| # | Step | Notes |
|---|---|---|
| 1 | Clone `github.com/nib-and-barrel/engraving-queue` at the tag recorded in the [configuration register](../configuration-register.md) | Never deploy an untagged commit to prod |
| 2 | `npm ci && npm test` | Must be green |
| 3 | Log in to Wrangler with your own Google-SSO Cloudflare account | No shared Cloudflare API tokens |
| 4 | If D1 is lost: create `eq-prod` in the EU jurisdiction, apply the migrations in `migrations/`, then restore from PITR or the latest weekly JSON export (SA-04) | RPO 24 h (REQ-13) |
| 5 | Set the Worker secrets from 1Password: `SHOPIFY_WEBHOOK_SECRET`, `SHOPIFY_ADMIN_TOKEN`, `AGENT_SERVICE_TOKEN_ID` | Vault paths in [SA-30](../04-organisation-specific/SA-30-engraving-queue.md) |
| 6 | `wrangler deploy --env production` | Worker `engraving-queue-prod` |
| 7 | Check the Access application (SA-02) and the `/webhooks/shopify` bypass | |
| 8 | In Shopify, send a test `orders/paid` webhook. Expect HTTP 200 and **no** duplicate job on a re-send | REQ-14 |
| 9 | Confirm the cron triggers are listed (purge, export, reconcile) | REQ-09 |
| 10 | Run the reconcile job manually so that any orders held during the outage get jobs | PAT-02 |

**Rollback:** `wrangler rollback` to the previous deployment ID (shown in `wrangler deployments list`). D1 schema migrations are forward-only, so a rollback across a migration needs the contractor.

The full rebuild was tested by the Ops Lead on staging on 2026-10-02, taking 1 h 25 min (AC-001 D3 acceptance).
