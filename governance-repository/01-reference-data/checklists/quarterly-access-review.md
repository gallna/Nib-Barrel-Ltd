# Checklist: Quarterly Access Review

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Managing Director | 1.0 | 2026-08-13 |

Run by the Architecture Lead in the last week of each quarter and signed off by the MD ([POL-06 §4](../policies/POL-06-access-control.md#4-quarterly-access-review)). The result is filed as evidence. The Q3 2026 review is EV-2026-013.

| # | Check | Systems | Result |
|---|---|---|---|
| 1 | Every active account belongs to a current employee or contractor | Google Workspace, then each SaaS admin console | ☐ |
| 2 | Leavers and seasonal staff removed (seasonal staff: by 15 January) | All | ☐ |
| 3 | MFA enforced for 100% of Google accounts; SMS-based MFA listed | Google Admin | ☐ |
| 4 | At most 2 admins per system | Shopify, Xero, Klaviyo, Gorgias, Cloudflare, GitHub, Click & Drop | ☐ |
| 5 | Shopify staff permissions match roles (fulfilment staff have no access to payouts or customer exports) | Shopify | ☐ |
| 6 | Installed Shopify apps and their scopes match the solutions repository baseline | Shopify | ☐ |
| 7 | API tokens and webhooks: none unused, none older than 12 months without rotation | Shopify, Cloudflare, connector | ☐ |
| 8 | Cloudflare Access policy: only the `fulfilment@` and `ops@` groups can reach the Engraving Queue | Cloudflare | ☐ |
| 9 | GitHub: branch protection and code owners active on all 4 repositories and on the app repositories | GitHub | ☐ |
| 10 | Restricted drives `NB-Governance` and `NB-Exports`: membership matches the list in POL-06 / SA-04 | Google Drive | ☐ |
| 11 | Engraving PC local account password rotated (DSP-002 mitigation) | 1Password | ☐ |
| 12 | Exceptions found → actions raised as GA-nnn | — | ☐ |

**Signed off:** MD (date) · Evidence filed as EV-yyyy-nnn.
