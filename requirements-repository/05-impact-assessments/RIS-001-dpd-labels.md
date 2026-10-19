# RIS-001: Requirements Impact Statement — CR-002 Automate DPD labels

| Status | Owner | Version | Date |
|---|---|---|---|
| Final | Fractional architect | 1.0 | 2026-10-14 |

TOGAF Phase H uses a Requirements Impact Statement to show which parts of the architecture a change touches, before the Board decides on it.

## 1. Requirement under assessment

[RQ-036](../03-requirements-register/functional.md#rq-036-automatic-dpd-labels): create DPD labels automatically for high-value (> £150) and next-day orders, with tracking flowing back to Shopify. Volume is ~3 orders/day (3%), rising to ~9/day at peak.

## 2. Impact on the architecture

| Area | Item | Impact | Severity |
|---|---|---|---|
| Business | BC-04 Order Fulfilment, BP-03 | Removes manual portal entry; the operative picks the carrier from the Shopify shipping rate instead | Low |
| Data | DE-07 Shipment | A second system creates Shipments. Click & Drop stays the system of record for Royal Mail shipments, and DPD's app becomes the system of record for DPD shipments. Ambiguous under PR-02 unless DE-07 is defined **per carrier** | **Medium** |
| Data | DE-04 Customer (address) | Address shared with DPD, which is already a carrier (ACT-08). The DPA must be checked in the processor register | Low |
| Application | New APP-12 candidate (DPD Shopify app) | New SaaS component; app catalogue and app/function matrix updated | Medium |
| Interfaces | New INT-11 candidate: APP-01 → DPD (orders), DPD → APP-01 (tracking) | Native integration (STD-03 compliant) | Low |
| Engraving | INT-08 release | Engraved high-value pens must still be released by APP-09 before a DPD label is printed (PAT-02 hold applies to both carriers) | **Medium**: test required |
| Requirements | REQ-10, REQ-11 | No change; must handle the peak of 9/day | — |
| Principles | PR-02 ⚠️, PR-03 ✅, PR-04 ✅, PR-06 (exit test needed) | See data row | — |
| Standards | STD-03 ✅ native integration; STD-05: app login via Shopify, so no separate staff accounts | — | — |
| Legal | LEG-01 processor register | DPD DPA to be confirmed | Low |
| Cost | ~£300 one-off; £0 recurring (DPD tariff unchanged) | Below the £2k/yr threshold, but a new vendor and a system-of-record change mean an ADR is still required | — |
| Schedule | Inside the Q4 freeze, so the earliest go-live is 2027-01-18 | — | — |

## 3. Options assessed

| Option | Fit | PR-02 | Cost (3 yr) | Risk |
|---|---|---|---|---|
| **A. DPD official Shopify app (DPD only)** | Good | ⚠️ resolved by a per-carrier DE-07 definition | ~£300 | Two shipping tools for operatives |
| B. Multi-carrier tool replacing Click & Drop | Good | ✅ one system of record for DE-07 | ~£2.9k | Re-integrates INT-03/04, which went live only in September; retraining before peak is not possible |
| C. Stay manual | Poor | ✅ | ~£2.5k staff time | Address errors on the most expensive orders |

## 4. Recommendation

**Option A.** Draft **ADR-009 "Add DPD Shopify app for DPD shipments"**, which records DE-07 as mastered per carrier. Deliver it in January 2027 after the Engraving Queue rollout. Re-evaluate option B at the Click & Drop review in ADM cycle 3.

Follow-up if approved:
- AR updates: application catalogue (APP-12), interface catalogue (INT-11), data entity catalogue (DE-07 note), SBB-14.
- Solutions repository: new asset record and a contract record for DPD.
- New requirement record for the APP-09 hold behaviour with DPD, as acceptance for INT-08.
