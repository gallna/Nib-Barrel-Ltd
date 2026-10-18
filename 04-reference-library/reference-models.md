# Reference Library

Reference material we've adopted or adapted. Most of it is external; our own adaptations are noted.

| Ref | Material | Used for | How we use it |
|---|---|---|---|
| RL-01 | TOGAF Standard, 10th Edition — ADM, Content Framework, Architecture Repository | Overall method | Tailored in [tailored-adm.md](../01-architecture-capability/tailored-adm.md) |
| RL-02 | TOGAF Series Guide: *Business Capabilities* | Capability map | BC-01..10 follow its "noun, stable over time" guidance |
| RL-03 | TOGAF Series Guide: *Value Streams* | "Gift that Delights" value stream | Six stages, each mapped to capabilities |
| RL-04 | ArchiMate 3.2 Specification | Element naming and relationships | We use its concept names in Mermaid; no ArchiMate tool needed at our size |
| RL-05 | TOGAF Technical Reference Model (TRM) | Technology categories | Simplified categories in the technology catalogue |
| RL-06 | Michael Nygard's ADR format | Decision records | [templates/adr-template.md](templates/adr-template.md) |
| RL-07 | Shopify app & webhook best practices (vendor docs) | INT-07, INT-08 | HMAC verification, idempotency, retries |
| RL-08 | ICO guidance: *Right of erasure*, *Direct marketing* | BC-10 | Basis of the BP-09 runbook |
| RL-09 | PCI SSC: *SAQ A* eligibility criteria | Payments | Confirms hosted-checkout scope |

## Reusable patterns

### PAT-01 SaaS hub-and-spoke with a single system of record
Shopify is the hub for product, inventory, customer and order data, and every spoke subscribes to it. New tools must connect to the hub, not to each other. *Derived from PR-02 and PR-03.*

### PAT-02 Webhook consumer with hold-and-release
Use this for any custom step that must happen before fulfilment: (1) Shopify places a fulfilment hold, (2) a webhook triggers the job, (3) the custom app releases the hold when done. If the custom app fails, the order stays safely held instead of shipping incomplete. *First used in APP-09.*

### PAT-03 Weekly open-format export
Every system of record gets a scheduled export to TEC-07 in CSV/JSON, and a restore drill runs twice a year. *Derived from PR-06.*
