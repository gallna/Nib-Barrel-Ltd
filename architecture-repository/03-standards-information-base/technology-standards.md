# Standards Information Base — Technology & Product Standards

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Architecture Board | 1.3 | 2026-07-02 |

Lifecycle: **Trial** (evaluating) → **Adopt** (use for new work) → **Contain** (keep, but don't extend) → **Retire** (plan removal) → **Prohibited**.

| ID | Area | Standard | Lifecycle | Notes / rationale |
|---|---|---|---|---|
| STD-01 | Commerce platform | Shopify (Advanced) | Adopt | [ADR-004](../05-governance-log/decision-log.md#adr-004) |
| STD-01a | Commerce platform | WooCommerce / self-hosted PHP | Retire | Retire by 2026-12 |
| STD-02 | Payments | Shopify Payments, PayPal (PCI DSS Level 1 providers only) | Adopt | REQ-07 |
| STD-02a | Payments | Any integration that puts card data on our systems | **Prohibited** | PCI scope explosion |
| STD-03 | Integration | Native/official vendor integrations first; then iPaaS; custom webhooks only for APP-09 | Adopt | PR-03 |
| STD-03a | Integration | Zapier | Contain | Allowed for non-critical, non-personal-data automations only |
| STD-04 | Custom app hosting | Cloudflare Workers + D1, TypeScript | Adopt | [ADR-007](../05-governance-log/decision-log.md#adr-007) |
| STD-04a | Custom app hosting | Self-managed VPS/VMs | Prohibited | No ops capacity |
| STD-05 | Identity | Google Workspace SSO (SAML/OIDC) + MFA (passkey or authenticator app) | Adopt | SMS-based MFA is Contain |
| STD-06 | DNS / domains | Cloudflare | Adopt | |
| STD-07 | Backups / exports | CSV/JSON to restricted Google shared drive, weekly | Adopt | PR-06 |
| STD-08 | Endpoints | ChromeOS (fulfilment), macOS (office), managed via Google admin | Adopt | Windows only for TEC-03 engraving PC |
| STD-09 | Engraving device | Engraving PC isolated on a separate VLAN; no email or web browsing | Adopt | Vendor software needs Windows |
| STD-10 | Source control | GitHub (company organisation), branch protection on `main` | Adopt | APP-09 source + this repository |
| STD-11 | Data formats | UTF-8 everywhere; ISO 8601 dates; GBP in minor units (pence) for custom code | Adopt | Engraving supports accented characters |
| STD-12 | Architecture notation | Markdown + Mermaid; ArchiMate 3.2 concepts for naming | Adopt | Keeps docs in-repo and diffable |
