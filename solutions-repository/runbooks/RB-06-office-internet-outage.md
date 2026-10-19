# RB-06: Office Internet Outage

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Ops Lead | 1.0 | 2026-07-20 |

| Implements | Requirement | Asset |
|---|---|---|
| WP-06 resilience baseline, GAP-11 | REQ-10 ("an office outage must not stop online selling") | [SA-06](../01-foundation/SA-06-office-network.md) |

## When the primary line fails
1. The router fails over to 4G automatically after 30 s. Check that the router's WAN LED shows "LTE".
2. Online selling is unaffected (Shopify is SaaS). CS can carry on from home on Google SSO.
3. On 4G, keep fulfilment going: Click & Drop labels and Engraving Queue job files both work. **Pause** large uploads (QC photo batches upload at the end of the day).
4. Watch the data allowance: 100 GB/month is about 3 weeks of normal fulfilment use.
5. Report the fault to the ISP (account reference in 1Password: `Nib & Barrel/Admin/isp-account`).

## If both links fail
- Fulfilment operatives tether one Chromebook to a staff phone to print labels.
- Engraving stops (it is the only on-site dependency). Orders stay held (PAT-02), so there is nothing to undo.
- After 4 h, the Ops Lead decides whether to add a "dispatch delayed" banner to the storefront.

## Quarterly test
Unplug the FTTP link for 10 minutes during a quiet period. Confirm failover, label printing and job-file fetch. Last test: 2026-09-29 ✅. Next: before 2026-12-31. A 10-minute test with no production change is allowed under the freeze.
