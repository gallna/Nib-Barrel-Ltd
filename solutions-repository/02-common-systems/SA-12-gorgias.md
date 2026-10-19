# SA-12: Gorgias Configuration

| Status | Owner | Version | Date |
|---|---|---|---|
| Approved | CS Lead | 1.0 | 2026-10-16 |

| SBB | Continuum | System of record | Lifecycle | Contract | Change refs |
|---|---|---|---|---|---|
| SBB-06 / APP-06 / INT-06 | Common systems | Gorgias. **The baseline here is authoritative.** System of record for DE-13 Support Ticket | Implementing: go-live **2026-10-27** | [CTR-06](../contracts/contracts-register.md) | WP-05, GAP-08, RQ-015 |

## Baseline

```yaml
plan: Basic
integrations:
  shopify: native (INT-06), order sidebar with refund, cancel and edit-address actions
  email: hello@nibandbarrel.co.uk forwarded into Gorgias (the Gmail shared inbox becomes an alias on 2026-10-27)
  amazon_buyer_messages: not connected   # Amazon messages are handled in Seller Central (policy)
channels:
  email: on
  contact_form: on (Shopify contact page)
  chat_widget: off                       # RQ-037: approved, scheduled 2027-01 (after the freeze)
views: [Unassigned, Engraving queries, Returns & refunds, Amazon-related, Waiting on customer]
tags: [engraving-text-issue, wismo, return, damaged, dsar]
macros:
  - Engraving text clarification (used when an EQ job enters NeedsCustomer, SA-30)
  - Where is my order (tracking from Shopify)
  - Personalised-item returns policy (LEG-04 exemption wording)
  - DSAR acknowledgement (starts the RB-01 7-day clock)
rules:
  - tag "dsar" when the subject or body matches "data request|delete my data|GDPR" → assign to CS Lead
  - auto-close "Waiting on customer" after 7 days
data_retention: delete tickets 2 years after close (DE-13)
users: { CS Lead: admin, Ops Lead: agent, Marketing Manager: observer }
sso: Google login (SA-03)
```

## Cut-over notes
Historic Gmail threads are **not** imported. They stay in Gmail for 2 years, then are purged ([solutions landscape retirement plan](../../architecture-repository/07-solutions-landscape/solution-building-blocks.md)). Go-live is part of T2. A post-implementation review, **CA-2026-005**, is planned for 2026-11-19.
