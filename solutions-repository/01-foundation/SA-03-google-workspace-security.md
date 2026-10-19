# SA-03: Google Workspace Security Baseline

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Managing Director | 1.2 | 2026-09-30 |

| SBB | Continuum | System of record | Lifecycle | Contract | Change refs |
|---|---|---|---|---|---|
| SBB-10 / TEC-05 / APP-10 | Foundation | Google Admin console. **The baseline here is authoritative.** | Active | [CTR-02](../contracts/contracts-register.md) | STD-05, REQ-12, WP-06, GAP-10 |

Google Workspace is our identity provider. Every other SaaS product signs in through it wherever it can (REQ-12).

## Baseline

```yaml
edition: Business Standard
super_admins: [md@, ops-admin@]        # two break-glass accounts; ops-admin@ is not used day to day
break_glass_recovery_codes: vault:1Password/Nib & Barrel/Admin/google-break-glass

two_step_verification:
  enforcement: on                      # all users, since 2026-06-22
  new_user_grace_period: 1d
  allowed_methods: [passkey, security_key, authenticator_app]
  sms_and_voice: contain               # STD-05: allowed only until a passkey is enrolled; none in use at 2026-09-30

password_policy: { min_length: 14, reuse: disallow }
session: { web_session_duration: 14d, reauth_for_admin: 1h }

groups:                                # used by SA-02 Access and by SaaS role mapping
  board@:       [MD, Ops Lead, Finance Manager]
  ops@:         [Ops Lead, fractional architect (guest)]
  fulfilment@:  [2 fulfilment operatives, seasonal operatives (Nov–Dec, removed in January)]
  cs@:          [CS Lead]
  marketing@:   [Marketing Manager]
  finance@:     [Finance Manager]

sign_in_with_google:                   # how each product authenticates (REQ-12)
  shopify:     google_login            # Shopify Advanced has no SAML; Google login + Shopify 2-step enforced
  xero:        google_login
  klaviyo:     saml
  gorgias:     google_login
  cloudflare:  saml                    # dashboard + Access (SA-02)
  github:      google_login + github_2fa_required
  click_and_drop: not_supported        # local accounts, unique passwords in 1Password, reviewed quarterly
  amazon_seller_central: not_supported # Amazon 2SV enforced instead

devices:
  chromeos: managed (SA-05)
  macos: basic_endpoint_management
  windows: not_enrolled                # engraving PC only, see DSP-002

data_protection:
  external_drive_sharing: allowlist_only   # NB-Exports drive (SA-04) cannot be shared externally
  gmail_auto_forwarding_external: blocked
```

## Coverage (as at 2026-09-30 access review)
7/7 staff on MFA. 0 users on SMS. Products without SSO are listed above and accepted under REQ-12's "where the product supports it". The engraving PC is covered by [DSP-002](../../architecture-repository/05-governance-log/dispensations.md).
