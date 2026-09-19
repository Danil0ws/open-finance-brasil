# CIBA

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/CIBA](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/CIBA)
**Slug:** `CIBA`

---

---
title: CIBA
---

# Overview

CIBA (Client Initiated Backchannel Authentication) lets a receiving institution
obtain the customer's authorisation through a decoupled channel, with no browser
redirect. The customer is notified in the transmitting institution's own app,
approves there, and the receiver is told the result over the backchannel.

CIBA is tested per product, because the consent, the scopes and the protected
resources differ between them. This page is the entry point for all of them.

The test plans validate the authorisation flow itself, the delivery mode
notification, and that the resulting token is accepted at a protected endpoint.
They do not re-validate the payload of the Consents or Resources APIs, which the
dedicated plans for those APIs cover.

# Pages

| Page | Plans |
|---|---|
| [Customer Data](CIBA/Customer-Data) | 1 |

# Spreadsheet

[CS-CIBA.xlsx](uploads/c0f60391f0c227490047632cc6a87c58/CS-CIBA.xlsx)

# Change history

<details>
<summary>2026 - 1 change</summary>

| Date | What changed | Breaking | Issue |
|---|---|---|---|
| 30/08/2026 | Page restructured. It now carries the certification cut-off per test plan, the plans and modules read from the suite itself, and a change history. Every change to any plan on this page is recorded here from this date. | No |  |

</details>

As the tests are in continuous development until certification starts institutions might find issues when executing the tests. Those issues can be related to both dubious specifications or because the test is executing a behaviour that is not in line with the defined specifications. In either case, we require institutions to open a [GitLab issue ticket](https://gitlab.com/obb1/certification/-/issues) so we can have it evaluated by our engineering team.

*Generated from certification `8fb87ca` on 14/09/2026.*


---

*Conteúdo baixado em 16/09/2026, 15:37:10*
