# DSP-003 (Request): Keep WooCommerce Read-only until 2027-03-31

| Status | Requested by | Owner if granted | Filed | Decision |
|---|---|---|---|---|
| **Pending: Board 2026-11-05** | Finance Manager | Finance Manager | 2026-10-12 | — |

Filed under [POL-03](../../01-reference-data/policies/POL-03-dispensation-policy.md). Source requirement: **RQ-040** in the [requirements repository](../../../requirements-repository/).

## 1. Exception requested

Keep the legacy WooCommerce site (SBB-13 / APP-B1 on TEC-01) online in read-only admin mode until **2027-03-31**, instead of decommissioning it on **2026-12-14**.

## 2. What it conflicts with

| Ref | What it says |
|---|---|
| [STD-01a](../../../architecture-repository/03-standards-information-base/technology-standards.md) | WooCommerce / self-hosted PHP is **Retire**: retire by 2026-12 |
| [SBB-13 retirement plan](../../../architecture-repository/07-solutions-landscape/solution-building-blocks.md#retirement-plan-legacy-sbbs) | Final export to TEC-07, then delete hosting on 2026-12-14 |
| [PR-01](../../../architecture-repository/01-architecture-capability/architecture-principles.md#pr-01-customer-trust-comes-first) | The site holds about 6 years of customer personal data (DE-04) on unpatched shared hosting with 31 plugins, 4 of them abandoned (DRV-03) |
| [STD-04a](../../../architecture-repository/03-standards-information-base/technology-standards.md) (by analogy) | We have no ops capacity to patch self-hosted servers |

## 3. Reason given

For the FY2026 year-end (31 December), the Finance Manager and the external accountant need to look up historic orders, refunds and payment references from before Shopify went live (before 2026-09-14). They usually do this until the accounts are finished in March. Searching the WooCommerce admin is familiar to them; a raw database export is not.

## 4. Options

| Option | Pros | Cons | Cost |
|---|---|---|---|
| **A. Grant: keep WooCommerce read-only until 2027-03-31** | No change for Finance | Customer PII stays on an unpatched, internet-facing PHP site for another 3.5 months; one more hosting renewal; STD-01a breached | ~£60 hosting, plus the risk |
| **B. Reject: searchable final export (recommended)** | PII leaves the internet-facing site on schedule; standards respected; the export is needed anyway (REQ-06, 6-year retention) | About 1 day of Ops Lead effort; Finance learns a new lookup | ~1 day internal |
| C. Grant a shorter extension, to 2027-01-31 | Covers the first month of year-end work | Same risk for 7 weeks; Finance still needs the export in February | ~£20 hosting |

Option B in detail:
1. The final encrypted database export to TEC-07 is already planned for 2026-12-14.
2. In addition, the Ops Lead produces an **order lookup workbook** (XLSX, one row per order line, plus refunds and payment references, with no customer addresses) and a JSON copy. Both go in the restricted Finance folder on TEC-07.
3. The Finance Manager and the accountant test the workbook against 20 sample look-ups before **2026-12-04**. If the test fails, the decommission waits until it passes. That would be a delay within the existing plan, not a dispensation.

## 5. Risk assessment

| Risk | Option A | Option B |
|---|---|---|
| Breach of historic customer data via an outdated plugin | Medium likelihood, high impact | Removed on 2026-12-14 |
| Finance cannot find a record | Low | Low, once the 20-sample test has passed |
| Year-end delayed | Low | Low |

## 6. Ops Lead recommendation

**Reject the dispensation and adopt Option B.** The underlying need is legitimate: Finance needs historic look-ups. But it does not require the old *system*, only its *data*. Keeping customer PII on the retiring platform contradicts PR-01, the highest-priority principle, for a convenience that a one-day export can provide.

## 7. Governance notes

- The Finance Manager does not vote on this request ([POL-06 §2](../../01-reference-data/policies/POL-06-access-control.md#2-separation-of-duties)). Quorum is therefore the MD plus the Ops Lead.
- GA-007 (decommission on 2026-12-14) is paused until the Board decides.
- If the request is rejected, this file stays here as precedent, the Board's rationale is appended below, and the row is closed in [open items](../open-items.md). If it is granted, a DSP-003 row is added to the AR [dispensations register](../../../architecture-repository/05-governance-log/dispensations.md).

## 8. Board decision

*To be recorded after BM-2026-11-05.*
