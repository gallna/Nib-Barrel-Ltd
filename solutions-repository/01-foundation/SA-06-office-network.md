# SA-06: Office Network: Broadband, 4G Failover & VLANs

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Ops Lead | 1.0 | 2026-07-20 |

| Realises | Continuum | System of record | Lifecycle | Change refs |
|---|---|---|---|---|
| TEC-09 | Foundation | This repo (router config export is held encrypted in SA-04, not in Git) | Active | WP-06, GAP-11, REQ-10, STD-09 |

## Baseline

```yaml
site: Bristol unit
wan:
  primary:  { type: FTTP, speed: 500/75 Mbps, isp: "<ISP>", support_ref: vault:1Password/Nib & Barrel/Admin/isp-account }
  failover: { type: 4G LTE, data_plan: 100 GB/month, sim_in_router: true, failover_after: 30s }
router:
  model: dual-WAN SMB router
  admin_access: LAN only, local admin password at vault:1Password/Nib & Barrel/Admin/office-router
  firmware: auto-update weekly (Sunday 04:00)
  config_backup: encrypted export to NB-Exports/network/ after every change
vlans:
  10_staff:   { ssid: NB-Staff,   auth: WPA3-Personal, clients: laptops, Chromebooks, label printers }
  20_guest:   { ssid: NB-Guest,   auth: WPA2, isolation: true, internet_only: true }
  30_devices: { wired_only: true, clients: [engraving PC], egress_allowlist: [queue.nibandbarrel.co.uk:443, windowsupdate, laser-vendor-update-host], inter_vlan: deny }
dns_filtering: Cloudflare Gateway free tier on 10_staff
```

## Failover behaviour
- Online selling does not depend on the office. Shopify, Gorgias and Klaviyo are SaaS, and CS can work from home (REQ-10).
- The only on-site dependency is engraving. On 4G, job-file fetches still work. Label printing via Click & Drop works on both links.
- Failover is tested quarterly by unplugging the FTTP link ([RB-06](../runbooks/RB-06-office-internet-outage.md)).
