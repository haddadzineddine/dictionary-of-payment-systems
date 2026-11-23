---
description: Know Your Customer, the checks regulated firms use to identify and verify the people they do business with.
---

KYC, or Know Your Customer, is the process a regulated firm uses to identify a customer, verify that identity, and understand the purpose of the relationship. It is part of [AML](./AML.md) compliance. In a payments company, KYC normally applies when opening an account, and again when something about the customer or their activity changes.

International standards come from the Financial Action Task Force (FATF), whose Recommendation 10 sets out customer due diligence. Actual obligations come from national or regional law, so they depend on the firm's licence and location.

| Region | Main source                                                                                   |
| ------ | --------------------------------------------------------------------------------------------- |
| EU     | National laws implementing the AML directives. Regulation (EU) 2024/1624 applies generally from 10 July 2027 |
| US     | Bank Secrecy Act rules, including customer identification programs for banks                  |
| UK     | Money Laundering Regulations                                                                  |

A typical KYC flow has several steps.

| Step      | What happens                                                            |
| --------- | ----------------------------------------------------------------------- |
| Collect   | Name, date of birth, address, identity document                         |
| Verify    | Check the document or data against reliable sources                     |
| Screen    | Run [sanctions screening](./Sanctions%20screening.md) and politically-exposed-person checks |
| Assess    | Assign a risk level                                                     |
| Monitor   | Review activity and refresh information over time                       |

KYC concerns individuals, while [KYB](./KYB.md) applies similar checks to businesses and their owners. It is also separate from authentication: KYC establishes who a customer is at onboarding, whereas [strong customer authentication](./Strong%20customer%20authentication.md) checks that the person making a payment is that customer.

Users experience KYC as friction. A wallet asks for a passport before raising a limit, a selfie check rejects a valid document, or an account is restricted because details need renewing. Engineers should model verification as a set of states, such as pending, verified, rejected and needs refresh. A single boolean cannot represent an expired document or a re-review.

Treat identity documents as highly sensitive personal data, and keep them out of support tools and logs.

_Usage:_

"Why can't this user withdraw? Their balance is fine."

"Their KYC expired when the ID document lapsed. They need to re-verify before we can release payouts."
