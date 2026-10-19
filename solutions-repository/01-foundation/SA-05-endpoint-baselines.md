# SA-05: Endpoint Baselines

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Ops Lead | 1.1 | 2026-08-14 |

| Realises | Continuum | System of record | Lifecycle | Change refs |
|---|---|---|---|---|
| TEC-08 Fulfilment endpoints, TEC-03 Engraving PC | Foundation | Google Admin (Chromebooks). This repo is authoritative for the engraving PC build. | Active | STD-08, STD-09, DSP-002, minor decision 2026-08-14 (4×6" labels) |

## A. Fulfilment station (×2, plus 1 spare for peak)

```yaml
device: Chromebook (ChromeOS, enterprise-enrolled)
org_unit: /Fulfilment
users: fulfilment@ group only
kiosk_pinned_apps:
  - https://queue.nibandbarrel.co.uk        # SA-30
  - https://business.parcel.royalmail.com    # Click & Drop (SA-21)
  - https://admin.shopify.com                # order lookup (fallback RB-03)
peripherals:
  label_printer: 4x6in thermal, USB (Zebra-compatible ZPL)
  barcode_scanner: USB HID, Code 128         # scans job barcodes (SA-31)
  camera: built-in, QC photos uploaded to SA-30
policies: { guest_mode: off, usb_storage: blocked, auto_update: on, idle_lock: 10min }
```

## B. Engraving PC (×1): build sheet

| Item | Setting |
|---|---|
| Hardware | Windows 11 Pro desktop, attached to TEC-03 30W fibre laser over USB |
| Account | Local standard user `engraver` (DSP-002). Password at `vault:1Password/Nib & Barrel/Fulfilment/engraving-pc-local` |
| Admin | Separate local admin, used only by the Ops Lead for vendor updates. Password at `vault:1Password/Nib & Barrel/Admin/engraving-pc-admin` |
| Network | VLAN 30 "devices" only ([SA-06](SA-06-office-network.md)); outbound allowlist only |
| Software | Laser vendor software (APP-11); EQ job agent from the `engraving-queue` repo `agent/` folder, version pinned in the [configuration register](../configuration-register.md) |
| Not installed | Email client, browser (Edge removed from the taskbar and blocked by firewall), Office |
| Watch folder | `C:\EQ\inbox` (job files arrive here), `C:\EQ\done` (moved after consumption, auto-deleted after 7 days) |
| Updates | Windows Update monthly (2nd Tuesday + 1 week); vendor software only after a test engrave on scrap |
| Backup | No local data of value. Laser templates are exported to `engraving-queue/templates/` in Git |

GA-005 in the [governance repository](../../governance-repository/) tracks the request to the vendor for SSO support. That would let DSP-002 close.
