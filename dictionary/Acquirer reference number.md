---
description: A reference created for a cleared card transaction, used to trace refunds and disputes between acquirer and issuer.
---

An acquirer reference number (ARN) is an identifier attached to a card transaction when it enters [clearing](./Clearing.md). Both the acquirer and the [issuer](./Issuer.md) can use it to find the same transaction, so it is the reference most often used to trace a [refund](./Refund.md) or a dispute. Visa's rules refer to the acquirer reference number, and Mastercard's rules call the equivalent value acquirer reference data (ARD).

The ARN is one of several identifiers that appear at different stages, and they are easy to confuse.

| Identifier                                             | Created at          | Main use                                 |
| ------------------------------------------------------ | ------------------- | ---------------------------------------- |
| Authorization code                                     | Approval            | Short code from the issuer for that approval |
| [Network transaction ID](./Network%20transaction%20ID.md) | Authorization       | Links related network messages           |
| ARN                                                    | Clearing            | Tracing between acquirer and issuer      |
| Provider payment ID                                    | Provider API        | Finding the payment in your provider     |
| [Merchant's](./Merchant.md) order ID                   | Checkout            | Finding the order in your own system     |

Because the ARN comes from clearing, it does not exist at authorization. A payment that has been authorized but not [captured](./Capture.md) has none, and one that has just been refunded may not have one until the refund is submitted. Model it as optional and populate it from a later event or report.

A typical use is a refund complaint. A customer says the money never arrived, and the [cardholder's](./Cardholder.md) bank says it has no record. The merchant asks its [payment service provider](./Payment%20service%20provider.md) for the refund's ARN and gives it to the customer, who gives it to the bank. The bank can then search its records for that exact credit. The refund has its own reference, so make sure you send that one and not the ARN of the original purchase.

In a [chargeback](./Chargeback.md), the ARN ties the dispute back to the original sale. Store it against the payment record.

_Usage:_

"Her bank says they can't see the refund we sent."

"Get the ARN for the refund from the provider. The bank can trace the credit with that."
