# SA-31: Engraving Job-File Interface (INT-09)

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Ops Lead | v1 | 2026-09-25 |

| SBB | Continuum | System of record | Lifecycle | Change refs |
|---|---|---|---|---|
| SBB-09 / INT-09 | Organisation-specific | **Authoritative copy:** `engraving-queue/docs/job-file.md` (GitHub). This page is a summary for readers outside the dev team. | Active (pilot) | AC-001 §1, STD-11 |

## How it flows
1. When a job reaches `Approved`, SA-30 makes a job file available at `/agent/jobs/{job_id}`.
2. The EQ agent on the engraving PC ([SA-05](../01-foundation/SA-05-endpoint-baselines.md)) polls every 15 s using the Access service token, then writes the file to `C:\EQ\inbox`.
3. The laser software's variable-text import reads the file. The operative scans the job barcode, engraves, and marks the job `Engraved` in SA-30.

## File summary

One file per engraved item: `{job_id}.csv`, UTF-8 with BOM (the vendor software needs it), a header row, and one data row.

| Field | Type | Example | Notes |
|---|---|---|---|
| `job_id` | string | `EQ-2026-004211` | Also printed as a Code 128 barcode on the job ticket |
| `order_name` | string | `NB10482` | Shopify order number; no customer data |
| `line_item_id` | string | `14231…` | Shopify ID, for idempotency |
| `sku` | string | `NB-FP-0142` | Selects the position template |
| `template` | string | `barrel-std-20` | Laser template file name in `engraving-queue/templates/` |
| `line_1` | string | `Happy 40th, Ana` | ≤ `engraving.max_chars` (SA-33) |
| `line_2` | string | `` | Optional |
| `font` | enum | `Classic Serif` | Mapped to a vendor font ID by template |
| `text_height_mm` | decimal | `2.8` | From template |
| `alignment` | enum | `centre` | |
| `proof_hash` | string | `sha256:…` | Ties the engraving to the approved proof |
| `created_at` | ISO 8601 UTC | `2026-10-14T09:12:33Z` | |

Rule: any change to the fields is a **breaking interface change**. It needs a template test engrave on scrap and a note in the [configuration register](../configuration-register.md).
