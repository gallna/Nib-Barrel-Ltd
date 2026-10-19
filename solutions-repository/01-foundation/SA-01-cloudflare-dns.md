# SA-01: Cloudflare DNS Zone & Proxy, `nibandbarrel.co.uk`

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Ops Lead | 1.1 | 2026-09-14 |

| SBB | Continuum | System of record | Lifecycle | Contract | Change refs |
|---|---|---|---|---|---|
| SBB-11 / TEC-06 | Foundation | Cloudflare dashboard. **The baseline here is authoritative.** | Active | [CTR-03](../contracts/contracts-register.md) | STD-06, WP-01 (cut-over to Shopify 2026-09-14) |

## Zone baseline

Only records that matter architecturally are listed. Verification TXT values are redacted, because their values do not need to be in Git.

```yaml
zone: nibandbarrel.co.uk
plan: free
registrar: cloudflare            # moved from previous registrar 2026-06 (TEC-06 migrate)
dnssec: enabled
records:
  - { name: "@",       type: A,     value: 23.227.38.65,            proxied: false, note: "Shopify storefront (Shopify-managed TLS)" }
  - { name: www,       type: CNAME, value: shops.myshopify.com,     proxied: false, note: "Shopify storefront" }
  - { name: queue,     type: CNAME, value: engraving-queue-prod (Worker route), proxied: true, note: "SA-30, behind SA-02 Access" }
  - { name: queue-staging, type: CNAME, value: engraving-queue-staging (Worker route), proxied: true }
  - { name: "@",       type: MX,    value: "smtp.google.com", priority: 1, note: "Google Workspace mail" }
  - { name: "@",       type: TXT,   value: "v=spf1 include:_spf.google.com include:shops.shopify.com include:_spf.klaviyo.com ~all" }
  - { name: _dmarc,    type: TXT,   value: "v=DMARC1; p=quarantine; rua=mailto:dmarc@nibandbarrel.co.uk" }
  - { name: google._domainkey,  type: TXT,   value: "<DKIM key — see Google Admin>" }
  - { name: kl._domainkey,      type: CNAME, value: "<Klaviyo sending domain — see SA-11>" }
  - { name: shop,      type: CNAME, value: "<legacy redirect>", note: "301 to www (old WooCommerce subdomain)" }
legacy:
  - { name: old,       type: A,     value: "<shared hosting IP>",   note: "SA-90 read-only Woo, remove at decommission 2026-12-14" }
ssl_tls:
  min_tls_version: "1.2"         # TLS 1.0/1.1 prohibited
  always_use_https: true
```

## Notes
- Shopify serves the storefront directly, so it is **not** proxied (Shopify requirement). Cloudflare proxies only the Engraving Queue hostnames.
- Adding a record that sends email on our behalf (SPF/DKIM) counts as adding a sending vendor, so it needs a POL-05 vendor check in the [governance repository](../../governance-repository/).
- DNS change access: Ops Lead and the fractional architect only (Cloudflare roles "Administrator" and "DNS"), both through Google SSO.
