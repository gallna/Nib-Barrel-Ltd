# Solutions Catalogue

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Architecture Lead (Ops Lead) | 1.0 | 2026-10-19 |

Master index of every solution asset. "Baseline here" means this repository holds the authoritative configuration baseline (SaaS). "Index" means the asset's own repository is the record.

## Asset index

| SA | Asset | Continuum | Realises | Owner | System of record | Version / state | Lifecycle | Contract | Runbooks |
|---|---|---|---|---|---|---|---|---|---|
| [SA-01](01-foundation/SA-01-cloudflare-dns.md) | Cloudflare DNS zone & proxy, `nibandbarrel.co.uk` | Foundation | SBB-11 / TEC-06 | Ops Lead | Cloudflare (baseline here) | Baseline 1.1 | Active | CTR-03 | RB-06 |
| [SA-02](01-foundation/SA-02-cloudflare-access.md) | Cloudflare Access policy "fulfilment-apps" | Foundation | SBB-11 / TEC-05 | Ops Lead | Cloudflare (baseline here) | Baseline 1.0 | Active | CTR-03 | RB-04 |
| [SA-03](01-foundation/SA-03-google-workspace-security.md) | Google Workspace security baseline | Foundation | SBB-10 / TEC-05 | MD | Google Admin (baseline here) | Baseline 1.2 | Active | CTR-02 | — |
| [SA-04](01-foundation/SA-04-export-drive.md) | Backup shared drive "NB-Exports" | Foundation | TEC-07 | Ops Lead | Google Drive (baseline here) | Baseline 1.0 | Active | CTR-02 | RB-02 |
| [SA-05](01-foundation/SA-05-endpoint-baselines.md) | Endpoint baselines: fulfilment Chromebooks, engraving PC | Foundation | TEC-03, TEC-08 | Ops Lead | Google Admin / this repo | Baseline 1.1 | Active | — | RB-03 |
| [SA-06](01-foundation/SA-06-office-network.md) | Office network: broadband, 4G failover, VLANs | Foundation | TEC-09 | Ops Lead | This repo | Baseline 1.0 | Active | — | RB-06 |
| [SA-10](02-common-systems/SA-10-xero.md) | Xero configuration & Shopify connector mapping | Common systems | SBB-03 / INT-02 | Finance Manager | Xero (baseline here) | Baseline 1.1 | Active | CTR-04 | — |
| [SA-11](02-common-systems/SA-11-klaviyo.md) | Klaviyo configuration | Common systems | SBB-05 / INT-05 | Marketing Manager | Klaviyo (baseline here) | Baseline 1.0 | Implementing (go-live 2026-10-20) | CTR-05 | RB-01 |
| [SA-12](02-common-systems/SA-12-gorgias.md) | Gorgias configuration | Common systems | SBB-06 / INT-06 | CS Lead | Gorgias (baseline here) | Baseline 1.0 | Implementing (go-live 2026-10-27) | CTR-06 | RB-01 |
| [SA-13](02-common-systems/SA-13-matrixify.md) | Matrixify export & import jobs | Common systems | SBB-12 / INT-10 | Ops Lead | Matrixify (baseline here) | Baseline 1.2 | Active | CTR-07 | RB-02 |
| [SA-14](02-common-systems/SA-14-payments.md) | Payments configuration | Common systems | SBB-02 | Finance Manager | Shopify / PayPal (baseline here) | Baseline 1.0 | Active | CTR-01, CTR-16 | — |
| [SA-20](03-industry/SA-20-shopify-store.md) | Shopify store configuration | Industry | SBB-01 / TEC-02 | Ops Lead | Shopify (baseline here) | Baseline 1.3 | Active (since 2026-09-14) | CTR-01 | RB-05, RB-07 |
| [SA-21](03-industry/SA-21-click-and-drop.md) | Click & Drop configuration | Industry | SBB-04 / INT-03, INT-04 | Ops Lead | Click & Drop (baseline here) | Baseline 1.1 | Active | CTR-10 | RB-05 |
| [SA-22](03-industry/SA-22-marketplace-connector.md) | Marketplace connector configuration | Industry | SBB-08 / INT-01 | Ops Lead | Connector app (baseline here) | Baseline 1.1 | Implementing (acceptance pending) | CTR-09, CTR-11 | — |
| [SA-23](03-industry/SA-23-personaliser-app.md) | Product personaliser app configuration | Industry | SBB-01a | Ops Lead | Personaliser app (baseline here) | Baseline 1.0 | Active (pilot) | CTR-08 | RB-03 |
| [SA-30](04-organisation-specific/SA-30-engraving-queue.md) | Engraving Queue application | Organisation-specific | SBB-09 / APP-09 | Ops Lead | GitHub `engraving-queue` (index) | v0.9.2 in prod (pilot) | Active (pilot) | CTR-12, CTR-03 | RB-03, RB-04, RB-07 |
| [SA-31](04-organisation-specific/SA-31-job-file-format.md) | Engraving job-file interface spec | Organisation-specific | SBB-09 / INT-09 | Ops Lead | `engraving-queue/docs/job-file.md` (index) | v1 | Active (pilot) | CTR-12 | RB-03 |
| [SA-32](04-organisation-specific/SA-32-nb-dawn-theme.md) | Customised Dawn theme "nb-dawn" | Organisation-specific | SBB-01 | Ops Lead | GitHub `nb-dawn` (index) | v2.3.0 | Active | CTR-13 (closed) | — |
| [SA-33](04-organisation-specific/SA-33-pen-product-data-model.md) | Pen product data model (metafields) | Organisation-specific | SBB-01 / DE-01 | Ops Lead | Shopify (baseline here) | v1.1 | Active | — | — |
| [SA-90](90-legacy/SA-90-woocommerce.md) | WooCommerce legacy site + DB | (legacy) | SBB-13 / APP-B1 | Ops Lead | Shared hosting | Read-only | Deprecated (decommission 2026-12-14) | CTR-14 | RB-02 |

ID gaps (SA-07–09, 15–19, 24–29, 34–89) are left on purpose so that each Continuum level can grow without renumbering.

## Coverage check: every SBB has at least one asset

| SBB | Assets |
|---|---|
| SBB-01 Shopify Advanced | SA-20, SA-32, SA-33 |
| SBB-01a Personaliser app | SA-23 |
| SBB-02 Shopify Payments + PayPal | SA-14 |
| SBB-03 Xero + connector | SA-10 |
| SBB-04 Click & Drop | SA-21 |
| SBB-05 Klaviyo | SA-11 |
| SBB-06 Gorgias | SA-12 |
| SBB-07 Amazon Seller Central | Covered inside SA-22 (Seller Central settings that the connector depends on) |
| SBB-08 Marketplace connector | SA-22 |
| SBB-09 Engraving Queue | SA-30, SA-31 |
| SBB-10 Google Workspace | SA-03, SA-04 |
| SBB-11 Cloudflare | SA-01, SA-02 |
| SBB-12 Matrixify | SA-13 |
| SBB-13 WooCommerce (legacy) | SA-90 |

## Requirements → assets

Architecture requirements are defined in the [Requirements Catalogue](../architecture-repository/06-architecture-requirements/requirements-catalog.md). Their source records are in the [Requirements Repository](../requirements-repository/).

| REQ | Satisfied by assets |
|---|---|
| REQ-01, REQ-02 | SA-23 (capture, preview, validation), SA-30 (re-validation) |
| REQ-03 | SA-32 (theme), SA-23 (preview) |
| REQ-04, REQ-08 (capture) | SA-20 (checkout settings) |
| REQ-05, REQ-06 | SA-10, SA-20 |
| REQ-07 | SA-14, SA-20 |
| REQ-08 (DSAR) | RB-01 across SA-20, SA-11, SA-12, SA-30 |
| REQ-09 | SA-30 (purge cron) |
| REQ-10 | SA-20, SA-06, SA-30 (hold-and-release) |
| REQ-11 | RB-05 |
| REQ-12 | SA-03, SA-02 |
| REQ-13 | SA-13, SA-04, RB-02, SA-30 (D1 PITR) |
| REQ-14 | SA-30 |
| REQ-15 | SA-22 |
