# Dispensations Register

A dispensation is a time-limited, Board-approved exception to a principle or standard.

| ID | Exception | Principle / standard | Reason | Mitigation | Approved | Expires | Status |
|---|---|---|---|---|---|---|---|
| DSP-001 | Engraving text may be manually transcribed from the Shopify order page into the laser software between T1 go-live and the Engraving Queue full rollout | PR-04, PR-01 | APP-09 full rollout falls after the Q4 freeze. Text capture is structured from T1, but production is still manual. | Text is copy-pasted (not retyped) from the Shopify order page; second-person check on every engraved order; error rate reported weekly | 2026-07-16 | 2027-01-31 | Active |
| DSP-002 | Engraving PC uses a local Windows account rather than Google SSO | STD-05 | Laser vendor software won't run under a managed/SSO Windows profile | PC isolated on its own VLAN (STD-09); no email/browser; local account has a strong unique password in the password manager; vendor asked for SSO support | 2026-07-16 | 2027-07-16 (review) | Active |
