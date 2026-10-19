# RQ-040: Keep WooCommerce read-only until 2027-03 (conflict → dispensation request)

| Status | Owner | Version | Date |
|---|---|---|---|
| Analysed | Finance Manager | 1.1 | 2026-10-19 |

This example shows a requirement that **conflicts with an approved standard**. Requirements Management does not decide it alone; it routes the record to the Board as a dispensation request.

| Attribute | Value |
|---|---|
| Statement | Keep the legacy WooCommerce admin available read-only until 2027-03-31, so Finance can look up pre-September 2026 orders during year-end |
| Rationale given | Year-end (31 March) queries often need the original order, refund and Stripe reference |
| Type / priority | F / Should |
| Raised by | Finance Manager, email 2026-10-12 (SC-06) |
| Owner | Finance Manager |
| Significance | **Architectural (conflict)** |
| Conflicts with | STD-01a WooCommerce = **Retire** by 2026-12; SBB-13 decommission 2026-12-14; [roadmap T1](../../../architecture-repository/02-architecture-landscape/strategic/architecture-roadmap.md#3-transition-architectures) ("WooCommerce read-only for 90 days, then retired") |
| Also affects | TEC-01 shared hosting (renewal cost ~£180 for 3 more months, plus an unpatched PHP site kept online) |

## Analysis (2026-10-19)

| Option | Pros | Cons |
|---|---|---|
| A. Grant the request: keep WooCommerce read-only to 2027-03-31 | No change for Finance | An unpatched PHP site holding 6 years of customer PII stays online for 3 more months (PR-01); needs a dispensation from STD-01a |
| **B. Searchable final export** (XLSX + JSON in TEC-07), plus a Finance lookup sheet keyed by order number | Meets the need; the site is retired on schedule; the export is kept 6 years anyway (REQ-06) | One-off effort of about 1 day; the lookup is less convenient than the admin UI |
| C. Import historic orders into Shopify | Single place to search | Pollutes the DE-03 system of record and customer histories; Matrixify cost and effort |

**Ops Lead recommendation:** Option B. Raised as dispensation request **DSP-003** for Board decision on 2026-11-05, with a recommendation to reject the dispensation in favour of option B. The status and Board outcome are tracked in the [governance repository process status](../../../governance-repository/README.md). The outcome will be logged in the AR [dispensations register](../../../architecture-repository/05-governance-log/dispensations.md).

## Acceptance (if option B is approved)

The Finance Manager finds 10 randomly chosen 2024–2025 orders, including refunds, in the export within 2 minutes each, before 2026-12-10.

## Change history

| Date | Change | By |
|---|---|---|
| 2026-10-12 | Raised | Finance Manager |
| 2026-10-12 | Triaged: conflicts with STD-01a; impact analysis requested | Ops Lead |
| 2026-10-19 | Analysed; DSP-003 request raised; on Board agenda 2026-11-05 | Ops Lead |
