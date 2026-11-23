---
description: The organisation that runs a card brand's rules and message rails between issuers and acquirers, such as Visa or Mastercard.
---

A card network, also called a card scheme, is the organisation that operates a card brand. It connects [issuers](./Issuer.md) and [acquirers](./Acquirer.md), carries their messages, calculates what they owe each other, and publishes the rules they must follow. Visa and Mastercard operate globally. Others include American Express, Discover, JCB and UnionPay, along with domestic schemes such as Cartes Bancaires in France and girocard in Germany.

| Function | What the network does                                                                 |
| -------- | ------------------------------------------------------------------------------------- |
| Routing  | Passes each [card authorization](./Card%20authorization.md) from acquirer to issuer and back       |
| [Clearing](./Clearing.md) | Exchanges final transaction records between members                                   |
| [Settlement](./Settlement.md) | Calculates net positions so members can pay each other                                |
| Rules    | Sets acceptance, data, dispute and monitoring requirements                            |
| Fees     | Charges [scheme fees](./Scheme%20fee.md) and administers [interchange](./Interchange%20fee.md) where applicable |

In the [four-party model](./Four-party%20model.md), the network does not hold the [cardholder's](./Cardholder.md) account or lend money. This is why "Visa declined the payment" is usually inaccurate: the issuer declined it, and the network delivered the answer. The network can still affect the result in narrower cases, such as stand-in processing when an issuer is unavailable, or fraud services an issuer chooses to use.

Network rules are private contracts that bind members, which then pass them on to [merchants](./Merchant.md) through their agreements. They are not law, and they vary by network and region. A rule that applies to Visa in Europe may not apply to Visa in the US or to Mastercard anywhere. Networks also revise their rules regularly.

For engineers, this means a behaviour observed on one brand should not be assumed for another. If code branches on `network`, check the current rulebook or your provider's documentation for each brand, and record which edition the logic was based on.

_Usage:_

"Mastercard let us capture this after a week, so Visa should too, right?"

"Not necessarily. The networks have different authorization rules, so check each one before we hard-code the window."
