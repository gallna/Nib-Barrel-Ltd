# SA-11: Klaviyo Configuration

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Marketing Manager | 1.0 | 2026-10-15 |

| SBB | Continuum | System of record | Lifecycle | Contract | Change refs |
|---|---|---|---|---|---|
| SBB-05 / APP-05 / INT-05 | Common systems | Klaviyo. **The baseline here is authoritative.** System of record for DE-11 Marketing Consent | Implementing: go-live **2026-10-20** | [CTR-05](../contracts/contracts-register.md) | ADR-008, WP-05, GAP-09, REQ-08, RQ-016 |

## Consent and data baseline

```yaml
integration: Shopify native (INT-05), real-time; syncs customers, orders, browse events, consent
consent_source_of_truth: Klaviyo (DE-11)  # captured at Shopify checkout, then Klaviyo owns it
consent_properties:
  email_marketing:
    capture_points: [shopify_checkout_checkbox (unticked by default), footer_signup_form]
    stored: [consent_status, consent_source, consent_timestamp_utc, consent_form_id, ip_country]
    double_opt_in: footer_form only        # checkout opt-in is single, provable via the Shopify order
  sms_marketing: disabled                  # not in scope this cycle (PECR); any change needs a CR
migration_from_mailchimp:                  # ADR-008
  imported: ~11.5k profiles with provenance (source + timestamp preserved), from 18.2k in Mailchimp
  not_migrated: contacts without provable opt-in (deleted with the Mailchimp account, 2026-11-20)
lists:
  - Newsletter (all consented)
  - Fountain Pen Enthusiasts (preference centre)
  - Ink & Refills (preference centre)
segments:                                  # purchase-based (RQ-016)
  - Bought engraved gift in last 12 months
  - Fountain pen buyers, no ink purchase in 120 days
  - Repeat customers (≥ 2 orders)
  - VIP (lifetime spend > £300)
flows:
  - Welcome series (consented only)
  - Abandoned checkout (consented only)
  - Post-purchase care guide (transactional-adjacent; sent only with consent)
transactional_email: NOT sent by Klaviyo     # order/shipping emails stay in Shopify
data_retention:
  suppressed_profiles: keep consent proof 2 years after withdrawal, then delete (DE-11 retention)
  inactive_profiles: delete 3 years after last order (aligns with DE-04 retention)
erasure: "Profile → Delete & request GDPR erasure" (RB-01 step 4)
access: { owner: Marketing Manager, admin: Ops Lead, sso: Google SAML (SA-03) }
private_api_keys: none issued              # no direct tool-to-tool integrations (PAT-01: spokes connect to the hub)
```

## Go-live checklist (2026-10-20)
Consent import verified on a sample of 50 profiles · checkout checkbox unticked (re-verified after CA-2026-001) · Mailchimp sending paused · post-implementation review **CA-2026-005**, planned 2026-11-19 ([governance repository](../../governance-repository/)).
