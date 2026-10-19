# RB-05: Peak Readiness Checklist

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Ops Lead | 1.0 | 2026-09-04 |

| Implements | Requirement | When |
|---|---|---|
| PR-05 Design for peak | REQ-11 (300 orders/day, 70 engraved/day), REQ-10 | Capacity test every **September**; final check before the freeze starts on **1 Nov** |

## September capacity test

| # | Check | 2026 result |
|---|---|---|
| 1 | Checkout load: 40 concurrent sessions on the production theme (vendor-managed platform) | ✅ 2026-09-04 (CA-2026-001 check 8) |
| 2 | Click & Drop import keeps up with 300 orders in one batch on the dev store | ✅ 4 import cycles |
| 3 | Engraving Queue: 70 synthetic jobs in staging within one shift, with proof rendering < 3 s each | ✅ 70 jobs, p95 1.4 s |
| 4 | Engraving station throughput: one laser, 2 operatives, ~6 min/job including QC → 70 jobs needs about 7 h | ⚠️ Tight. The seasonal operative is trained on the engraving station (RQ-041, validate 2026-10-23) |
| 5 | Klaviyo/Gorgias plan limits at 3× volume | ✅ Checked against CTR-05/06 tiers |
| 6 | Packaging and label stock for 6 weeks of peak | ✅ Ordered |

## Pre-freeze check (by 2026-10-30)

- [ ] All T2 go-lives done (Klaviyo 2026-10-20, Gorgias 2026-10-27), or explicitly moved to January
- [ ] [Configuration register](../configuration-register.md) shows no change "in progress"
- [ ] App allowlist in SA-20 matches the live store (drift check)
- [ ] 4G failover tested this quarter ([RB-06](RB-06-office-internet-outage.md))
- [ ] RB-03 manual fallback rehearsed with the seasonal operatives
- [ ] Contacts list for vendors' support printed and pinned at the fulfilment stations
- [ ] Emergency change rule restated to all staff: security fixes only (POL-04 in the [governance repository](../../governance-repository/))
