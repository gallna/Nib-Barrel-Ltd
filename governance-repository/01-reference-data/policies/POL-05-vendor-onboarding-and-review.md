# POL-05: Vendor Onboarding and Review

| Status | Owner | Version | Approved | Date |
|---|---|---|---|---|
| Approved | Architecture Lead | 1.0 | BM-2026-08-13 | 2026-08-13 |

## Purpose

[PR-01](../../../architecture-repository/01-architecture-capability/architecture-principles.md#pr-01-customer-trust-comes-first) requires every new SaaS vendor to pass a privacy and security check before adoption. [PR-06](../../../architecture-repository/01-architecture-capability/architecture-principles.md#pr-06-avoid-lock-in-where-exit-is-expensive) requires a credible exit route. This policy says how both are done and when they are repeated.

## 1. Scope

Any new SaaS product, Shopify app, contractor with access to our systems, or data processor. Free tools are in scope as well; free tools that hold personal data are the riskiest.

A **new vendor** always goes through the Board, because the charter routes "adds a vendor" to an ADR ([POL-01](POL-01-architecture-governance-procedure.md)). A Shopify app counts as a new vendor.

## 2. Onboarding steps

1. **Evaluate** using the [vendor evaluation template](../../../architecture-repository/04-reference-library/templates/vendor-evaluation-template.md). At least two options plus "do nothing".
2. **Privacy and security check** using the [vendor onboarding checklist](../checklists/vendor-onboarding.md).
3. **Exit test** before contract signature: export all our data and confirm it opens in a spreadsheet with the IDs intact. File the result as evidence.
4. **DPA signed** if the vendor processes personal data. Add it to the [processor register](../../../architecture-repository/03-standards-information-base/legal-and-regulatory.md#processor-register-summary).
5. **ADR** approved by the Board.
6. **Contract recorded** in the contracts register in the [solutions repository](../../../solutions-repository/) (term, notice period, cost and owner).
7. **Access set up** per [POL-06](POL-06-access-control.md): SSO where supported, named accounts, least privilege.

## 3. Annual review (every March)

For each vendor in the contracts register, the owner confirms:

| Check | Fail action |
|---|---|
| Still needed, still the best fit | CR to replace or retire |
| Cost at current volume, and at 3× (PR-05) | Renegotiate before renewal |
| Security certifications still valid (SOC 2 / ISO 27001) | Ask the vendor; if not resolved, Board |
| DPA and transfer mechanism still valid | Update the processor register |
| Exit test repeated for systems of record | Fix the export (PAT-03) |
| Users and API keys reviewed | Revoke unused ones |

Results are filed as evidence and summarised in the Q1 monitoring report. The next review is **2027-03**.

## 4. Offboarding

- Export the data and verify the export.
- Delete or anonymise the data, and get written confirmation from the vendor.
- Revoke API keys and remove SSO apps.
- Cancel the contract.
- Update the processor register and the solutions repository.

Examples on the roadmap: Mailchimp (2026-11-20, GA-006) and WooCommerce hosting (2026-12-14, GA-007).
