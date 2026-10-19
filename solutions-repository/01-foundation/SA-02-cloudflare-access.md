# SA-02: Cloudflare Access Policy "fulfilment-apps"

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | Ops Lead | 1.0 | 2026-10-09 |

| SBB | Continuum | System of record | Lifecycle | Contract | Change refs |
|---|---|---|---|---|---|
| SBB-11 (Zero-Trust Access) / TEC-05 | Foundation | Cloudflare Zero Trust. **The baseline here is authoritative.** | Active | [CTR-03](../contracts/contracts-register.md) | ADR-007, REQ-12, AC-001 §2, CA-2026-002 check 3 |

Access gives the Engraving Queue ([SA-30](../04-organisation-specific/SA-30-engraving-queue.md)) Google SSO without any auth code in the app.

## Policy baseline

```yaml
identity_providers:
  - name: google-workspace
    type: google-workspace
    domain: nibandbarrel.co.uk        # MFA is enforced by Google (SA-03), not by Access

applications:
  - name: engraving-queue-prod
    domain: queue.nibandbarrel.co.uk
    session_duration: 12h             # one shift
    policies:
      - name: staff-fulfilment
        decision: allow
        include: [ group: fulfilment@nibandbarrel.co.uk, group: ops@nibandbarrel.co.uk ]
        require: [ idp: google-workspace ]
      - name: engraving-pc-agent      # job-file fetch from engraving PC (SA-05, DSP-002)
        decision: non_identity
        include: [ service_token: eq-engraving-pc ]
        path: /agent/*
    bypass_paths:
      - path: /webhooks/shopify       # Shopify cannot do SSO. The Worker verifies HMAC instead (REQ-14)

  - name: engraving-queue-staging
    domain: queue-staging.nibandbarrel.co.uk
    session_duration: 12h
    policies:
      - name: builders
        decision: allow
        include: [ group: ops@nibandbarrel.co.uk, email: contractor@<contractor-domain> ]
        require: [ idp: google-workspace ]   # contractor holds a Workspace guest account

service_tokens:
  - name: eq-engraving-pc
    client_id: vault:1Password/Nib & Barrel/Engineering/eq-engraving-pc-access-client-id
    client_secret: vault:1Password/Nib & Barrel/Engineering/eq-engraving-pc-access-client-secret
    duration: 1y                      # rotate by 2027-10-01 (calendar reminder in governance repository)
```

## Notes
- The webhook bypass is the only unauthenticated path. It is limited to `POST` and protected by HMAC plus idempotency (CA-2026-002 check 2).
- Removing a leaver from the Google group removes Access within the session duration. The quarterly access review checks group membership ([governance repository](../../governance-repository/)).
