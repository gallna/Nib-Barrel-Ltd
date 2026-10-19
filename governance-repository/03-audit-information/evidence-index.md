# Evidence Index

| Status | Owner | Rule | Storage |
|---|---|---|---|
| Live, **append-only** | Architecture Lead | One row per evidence item; never edited; a replacement gets a new EV number ([POL-08](../01-reference-data/policies/POL-08-governance-records-retention.md)) | Restricted shared drive `NB-Governance/Evidence/` (Board members + fractional architect) |

This index records **where** each piece of evidence is and what it proves. The evidence itself is never stored in this repository: screenshots and exports may contain personal data, and attestations contain signatures. Drills use test personas only ([POL-07](../01-reference-data/policies/POL-07-information-security-baseline.md) rule 9).

Path pattern: `NB-Governance/Evidence/<year>/<EV-id>-<slug>/`.

| EV | Date | Evidence | Proves | Used by | Filed by | Retain until |
|---|---|---|---|---|---|---|
| EV-2026-001 | 2026-05-07 | Signed DPAs: Shopify, Klaviyo, Gorgias, Cloudflare, Xero, Royal Mail | Processor register complete (LEG-01) | [Processor register](../../architecture-repository/03-standards-information-base/legal-and-regulatory.md#processor-register-summary) | Finance Manager | 6 yrs after each contract ends |
| EV-2026-002 | 2026-06-02 | Shopify trial-store exit test: export files and a check sheet | PR-06 exit test passed | ADR-004 | Fractional architect | 2032-06 |
| EV-2026-003 | 2026-06-04 | Vendor evaluation scoring: Shopify, WooCommerce managed hosting, BigCommerce | Options appraisal for ADR-004 | ADR-004 | Architecture Lead | 2032-06 |
| EV-2026-004 | 2026-07-30 | AC-001 signed contract (PDF) | Contract in force | AC-001 | MD | Contract end + 6 yrs |
| EV-2026-005 | 2026-09-04 | Peak capacity test record (3× average, 40 concurrent checkout sessions) | REQ-11 tested in September | CA-2026-001 #8 | Ops Lead | 2032-09 |
| EV-2026-006 | 2026-09-07 | Redirect crawl test: 612 URLs, 0 × 404 | SEO risk mitigated (Vision §8) | CA-2026-001 #7 | Agency → Ops Lead | 2032-09 |
| EV-2026-007 | 2026-09-08 | Checkout screenshots: personalised-goods exemption notice; consent checkbox unticked | REQ-04, REQ-08 | CA-2026-001 #4, #5 | Ops Lead | 2032-09 |
| EV-2026-008 | 2026-09-08 | Google Admin MFA enrolment report: 7/7 accounts | REQ-12 | CA-2026-001 #6 | Ops Lead | 2032-09 |
| EV-2026-009 | 2026-09-09 | Shopify app list after the reviews app was removed | GA-002 closed | CA-2026-001 #2 | Ops Lead | 2032-09 |
| EV-2026-010 | 2026-09-30 | PCI DSS SAQ A 2026 attestation (submitted) | REQ-07, LEG-03 | Annual control | Finance Manager | 2032-09 |
| EV-2026-011 | 2026-10-01 | DSAR/erasure drill log: test persona, every system, 3 days end to end | REQ-08 (≤ 7 days), GOL-06 | Quarterly control | CS Lead | 2032-10 |
| EV-2026-012 | 2026-10-06 | Restore drill log: weekly Matrixify export restored into a development store, row counts matched | REQ-13, GA-001 | CA-2026-001 condition | Ops Lead | 2032-10 |
| EV-2026-013 | 2026-09-30 | Q3 access review checklist, signed by the MD; 1 stale account removed | POL-06 | Quarterly control | Architecture Lead | 2032-09 |
| EV-2026-014 | 2026-10-09 | Engraving Queue pilot test pack: webhook replay ×5 (one job created), D1 schema review, Worker-disabled hold test; delegated pilot approval email | REQ-14, REQ-10, PAT-02 | CA-2026-002 | Fractional architect | 2032-10 |
| EV-2026-015 | 2026-10-09 | Accessibility check of the engraving preview (keyboard pass; font-picker contrast fail) | REQ-03 partially met; GA-003 | CA-2026-002 #7 | Fractional architect | 2032-10 |
| EV-2026-016 | 2026-10-05 | Marketplace connector sync-log export for 2026-10-03, and the two order references | INV-2026-01 timeline | INV-2026-01 | Ops Lead | Closure + 6 yrs |
| EV-2026-017 | Weekly from 2026-09-18 | Engraving error-rate reports (one file per week) | DSP-001 mitigation | GA-004 | Ops Lead | DSP-001 expiry + 6 yrs |
| EV-2026-018 | 2026-10-08 | Q3 2026 Architecture & Governance Report as presented (PDF snapshot) | Quarterly monitoring | [Q3 report](monitoring-reports/2026-Q3-architecture-governance-report.md) | Architecture Lead | 2032-10 |

**Expected next:** RB-05 peak readiness checklist (by 2026-10-25), INV-2026-01 vendor root-cause analysis, CA-2026-003 test pack, and the Mailchimp final audience and consent export (before 2026-11-20).
