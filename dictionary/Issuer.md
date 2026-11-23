---
description: The bank or licensed institution that provides a card, approves or declines its payments and handles cardholder disputes.
---

An issuer is the bank or licensed financial institution that provides a payment card to a [cardholder](./Cardholder.md) and holds the account behind it. When a card is used, the issuer makes the final decision on the [card authorization](./Card%20authorization.md).

| Stage         | What the issuer does                                                    |
| ------------- | ----------------------------------------------------------------------- |
| Card issue    | Checks the customer, opens the account, sets limits, provides the card  |
| Authorization | Checks funds, card status and fraud risk, then approves or declines     |
| [Clearing](./Clearing.md)      | Receives the final transaction record and posts it to the account       |
| [Settlement](./Settlement.md)    | Pays the amount owed through the [card network](./Card%20network.md)                              |
| Dispute       | Takes the cardholder's claim and may raise a [chargeback](./Chargeback.md)                    |

The issuer is often confused with the network. A customer may say "Visa declined my card", but Visa and Mastercard do not usually make the credit or balance decision. The issuer does, and a [merchant](./Merchant.md) or [payment service provider](./Payment%20service%20provider.md) cannot override it. When a payment fails at checkout with a generic [decline code](./Decline%20code.md), the person who can explain it is usually the issuer's support team. The merchant often sees only the code.

The issuer is also a different party from the [acquirer](./Acquirer.md), which works for the merchant. One bank can play both roles in different transactions.

Consumer fintech cards add a layer. The app's brand may appear on the card while a licensed bank or e-money institution is the actual issuer, often with a program manager running the product. A [sponsor bank](./Sponsor%20bank.md) arrangement of this kind is common in the US.

In the EU, [PSD2](./PSD2.md) treats issuing payment instruments as a regulated payment service, and the issuer is responsible for applying [strong customer authentication](./Strong%20customer%20authentication.md) unless an exemption applies.

_Usage:_

"The customer says their card works everywhere except on our site."

"Our logs show a do-not-honor from the issuer. We can't see why, so they need to call the number on the back of the card."
