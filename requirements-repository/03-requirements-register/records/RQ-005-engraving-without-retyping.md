# RQ-005: Engraving text reaches the laser without retyping

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Ops Lead | 1.3 | 2026-10-09 |

| Attribute | Value |
|---|---|
| Type | F (functional) |
| Priority | Must |
| Significance | **Architectural**: it justified the only custom build ([ADR-006](../../../architecture-repository/05-governance-log/decision-log.md#adr-006)) |
| Raised by | Fulfilment team, bench interviews 2026-04-02 (SC-03) |
| Owner | Ops Lead |
| ADM phases | B (BP-04), C (APP-09, INT-07..09), E/F (WP-03), G (AC-001) |
| Building blocks | ABB Personalisation Workflow Service, Production Device Adapter → SBB-09 → SA-30, SA-31 |

## Statement

The engraving text, font and position that the customer enters are passed to the laser software as a job file. Nobody retypes or re-keys them at any step.

## Rationale

In the baseline, text is transcribed three times (email → spreadsheet → laser software). That causes a 2.1% error rate, about 120 remakes a year and roughly £4.6k in written-off pens (DRV-01, [capability architecture](../../../architecture-repository/02-architecture-landscape/capability/personalised-engraving.md#1-baseline-process-2026-03)).

## Acceptance criteria

1. For 100% of engraved orders, the job file content is byte-identical to the captured line-item properties (sampled weekly during the pilot).
2. Engraving error rate < 0.3% over 3 consecutive months after full rollout (GOL-01).
3. If APP-09 is down, orders stay held (PAT-02), and the fallback is copy-paste with a 4-eyes check, never retyping ([RB-03](../../../solutions-repository/README.md)).

## Traceability

| Link | ID |
|---|---|
| Driver / goal | DRV-01 / GOL-01 |
| Gap / work package | GAP-04 / WP-03 |
| Related records | RQ-003 (preview), RQ-004 (validation), RQ-006 (proof), RQ-025 (purge), RQ-028 (webhook) |
| Architecture requirements | Realised together with REQ-02, REQ-09 and REQ-14. The record itself is captured in the approved capability architecture rather than as a separate REQ |
| Decision / contract | ADR-006, ADR-007, [AC-001](../../../architecture-repository/06-architecture-requirements/architecture-contracts/AC-001-engraving-queue.md) |
| Interim exception | [DSP-001](../../../architecture-repository/05-governance-log/dispensations.md): copy-paste from the Shopify order page until full rollout, expires 2027-01-31 |
| Verification | CA-2026-002 (pilot); CA-2026-004 (full rollout, planned 2027-01-07) |

## Change history

| Date | Change | By |
|---|---|---|
| 2026-04-02 | Raised: "Stop us retyping engraving text from emails" | Fulfilment team via Ops Lead |
| 2026-04-06 | Triaged: architecturally significant (new capability, custom-build candidate) | Ops Lead |
| 2026-04-23 | Approved within the Project Quill scope (ADR-003) | Architecture Board |
| 2026-06-18 | Solution option B chosen (buy capture/preview, build queue) | Architecture Board (ADR-006) |
| 2026-07-16 | Interim exception DSP-001 approved, because full rollout falls after the Q4 freeze | Architecture Board |
| 2026-10-09 | Pilot passed CA-2026-002 (conditions on REQ-03 only); acceptance criterion 1 met for pilot SKUs | Fractional architect |
