# CA-2026-002: Compliance Assessment — WP-03 Engraving Queue (Pilot)

| Assessed | Assessor | Phase | Contract |
|---|---|---|---|
| 2026-10-09 | Fractional architect | Pre-pilot | [AC-001](../../06-architecture-requirements/architecture-contracts/AC-001-engraving-queue.md) |

| # | Check | Ref | Result | Evidence / notes |
|---|---|---|---|---|
| 1 | Holds only DE-05 + order ID + SKU | Data arch | ✅ | D1 schema reviewed |
| 2 | Webhook HMAC verification and idempotency | REQ-14 | ✅ | Replayed same webhook 5×, one job created |
| 3 | Access via Cloudflare Access + Google SSO only | REQ-12 | ✅ | |
| 4 | Text purge job after 90 days | REQ-09 | ✅ | Unit test + scheduled Worker (cron) |
| 5 | Hold-and-release pattern (PAT-02); orders stay held if APP-09 is down | REQ-10 | ✅ | Tested by disabling the Worker route |
| 6 | Code size < 2,000 LOC; README + runbook in repo | AC-001 | ✅ | 1,640 LOC |
| 7 | Preview meets WCAG 2.2 AA | REQ-03 | ⚠️ | Purchased preview app passes keyboard nav; **contrast issue on font picker**, vendor ticket raised |
| 8 | D1 point-in-time recovery enabled | REQ-13 | ✅ | |

## Outcome
**Compliant with conditions.** Pilot approved for engraved orders on 3 SKUs (2026-10-12 → 2026-10-30).

| Condition | Owner | Due | Status |
|---|---|---|---|
| Font-picker contrast fixed by vendor or overridden in theme CSS | Ops Lead | Before full rollout (2027-01-11) | Open |
