# Checklist: Vendor Onboarding (Privacy & Security Check)

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Architecture Lead | 1.0 | 2026-08-13 |

Used in step 2 of [POL-05](../policies/POL-05-vendor-onboarding-and-review.md). The functional and cost scoring is in the AR [vendor evaluation template](../../../architecture-repository/04-reference-library/templates/vendor-evaluation-template.md). This checklist covers the pass/fail gates: a single ❌ stops onboarding unless the Board grants a dispensation.

| # | Gate | Pass criterion | Result |
|---|---|---|---|
| 1 | Card data | The product never asks for, stores or transmits card data on our behalf (REQ-07) | ✅ / ❌ |
| 2 | Personal data | We list exactly which entities (DE-nn) it will hold. Holding less is better. | ✅ / ❌ |
| 3 | DPA | The vendor signs a UK GDPR-compliant DPA | ✅ / ❌ |
| 4 | Data location / transfer | UK, EU, or an adequacy / UK IDTA mechanism | ✅ / ❌ |
| 5 | Certification | SOC 2 Type II or ISO 27001, or a credible security page for small apps (ask the architect) | ✅ / ⚠️ / ❌ |
| 6 | Authentication | SSO (SAML/OIDC) or "Sign in with Google", plus MFA (REQ-12) | ✅ / ⚠️ / ❌ |
| 7 | Least privilege | For a Shopify app, the requested scopes are justified scope by scope | ✅ / ❌ |
| 8 | Exit test | Full export opens in a spreadsheet with IDs intact (PR-06) | ✅ / ❌ |
| 9 | Peak behaviour | Pricing and limits at 3× volume are known (PR-05) | ✅ / ❌ |
| 10 | Support | UK-hours support; incident notification commitment | ✅ / ⚠️ |
| 11 | Offboarding | The vendor confirms data deletion on termination | ✅ / ❌ |

⚠️ is allowed if the risk is recorded in the ADR.

**Completed by:** Architecture Lead · **Reviewed by:** fractional architect · Evidence filed as EV-yyyy-nnn.
