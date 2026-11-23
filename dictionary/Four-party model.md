---
description: The card payment structure linking cardholder, merchant, issuer and acquirer through a card network.
---

The four-party model is the standard structure of a card payment. The four parties are the [cardholder](./Cardholder.md), the [merchant](./Merchant.md), the cardholder's [issuer](./Issuer.md) and the merchant's [acquirer](./Acquirer.md). A [card network](./Card%20network.md) sits between the two institutions and is not counted as one of the four.

| Party      | Relationship                          | Role in a payment                       |
| ---------- | ------------------------------------- | --------------------------------------- |
| Cardholder | Customer of the issuer                | Presents the card                       |
| Merchant   | Customer of the acquirer              | Sells goods and requests payment        |
| Issuer     | Member of the network                 | Approves and pays on the cardholder's behalf |
| Acquirer   | Member of the network                 | Submits transactions and funds the merchant |
| Network    | Connects issuer and acquirer          | Routes messages and applies rules       |

The structure explains why a merchant cannot ask "the bank" what happened to a payment. The merchant has a relationship only with its acquirer or [payment service provider](./Payment%20service%20provider.md), and the cardholder has one only with the issuer. A decline reason, a missing [refund](./Refund.md) or a [chargeback](./Chargeback.md) has to pass through that chain, so each side sees only part of the picture. Shared references such as the [acquirer reference number](./Acquirer%20reference%20number.md) exist to connect the two views.

The alternative is a three-party scheme, in which the scheme itself acts as both issuer and acquirer. EU [Interchange](./Interchange%20fee.md) Fee Regulation 2015/751 defines both structures, and treats a three-party scheme as four-party when it licenses other providers to issue or acquire, or issues cards with a co-branding partner or through an agent. American Express and Discover are commonly described as three-party networks, but both also work with partner institutions in some markets, so the label depends on the product and country.

Money flows between issuer and acquirer through [settlement](./Settlement.md).

_Usage:_

"Can't we just ask the customer's bank why it failed?"

"They won't talk to us. We're on the acquirer side of the four-party model, so the customer has to contact their issuer."
