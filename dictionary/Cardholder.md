---
description: The person a payment card is issued to, who pays with it and can challenge charges through the card issuer.
---

A cardholder is the person a payment card is issued to. In the [four-party model](./Four-party%20model.md), the cardholder pays a [merchant](./Merchant.md), and their [issuer](./Issuer.md) decides whether to approve the payment and then bills them or debits their account.

The cardholder is not always the party that owns the account or the person who placed the order. Those differences explain many payment support cases.

| Role                | Who it is                         | Example                            |
| ------------------- | --------------------------------- | ---------------------------------- |
| Cardholder          | Person issued the card            | Employee with a company card       |
| Account holder      | Party responsible for the account | The company paying the card bill   |
| Merchant's customer | Person who placed the order       | A teenager using a parent's card   |

The last row causes a common failure. A parent sees an unfamiliar line on a statement, does not connect it with a purchase made by someone in the household, and reports it to the bank. The merchant then receives a [chargeback](./Chargeback.md) for an order that was delivered correctly. This is one route to [friendly fraud](./Friendly%20fraud.md), and a clear [statement descriptor](./Statement%20descriptor.md) makes it less likely.

Cardholder protection depends on region and product. In the EU, [PSD2](./PSD2.md) gives payers [refund](./Refund.md) rights for unauthorised transactions and limits their liability. In the US, Regulation Z covers credit cards and Regulation E covers debit cards, with different limits. Network dispute rights sit alongside these laws, and the cardholder uses them by contacting the issuer rather than the [card network](./Card%20network.md).

Merchants should keep only the cardholder data they need. The card number, or [PAN](./PAN.md), and the [CVV](./CVV.md) are covered by [PCI DSS](./PCI%20DSS.md), so most systems hold a [token](./Tokenization.md) in their place.

_Usage:_

"This customer says they never bought from us, but the order shipped to their home address."

"Someone else in the household may have used the card. Send the cardholder the order details before the dispute goes further."
