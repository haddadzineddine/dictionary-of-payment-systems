---
description: A new credit transaction returning money to a card after the original payment has been captured and cleared.
---

A refund returns money to a customer's card after the original payment has been [captured](./Capture.md) and [cleared](./Clearing.md). It is a new transaction in the opposite direction. The original charge stays on the statement, and a separate credit appears later.

| Action                                                  | Timing                      | Result on the statement          |
| ------------------------------------------------------- | --------------------------- | -------------------------------- |
| [Void](./Void.md)                                       | Before clearing submission  | Usually no posted entry          |
| [Authorization reversal](./Authorization%20reversal.md) | Before clearing             | Pending hold disappears          |
| Refund                                                  | After clearing              | Charge plus separate credit      |
| [Chargeback](./Chargeback.md)                           | After a dispute with the [issuer](./Issuer.md) | Credit forced through the network |

A refund is initiated by the [merchant](./Merchant.md), which distinguishes it from a chargeback, initiated by the issuer. The money is deducted from the merchant's balance or a future [payout](./Payout.md). If the balance is too low, the provider may delay the refund or debit the merchant's bank account.

A common complaint is "you said you refunded me, but I don't have it". The merchant's system shows success because the provider accepted the instruction, but the credit still has to pass through clearing and be posted by the issuer. That can take days, and the exact time varies. Give the customer the [acquirer reference number](./Acquirer%20reference%20number.md) when your provider exposes one, since their bank can use it to trace the credit.

Refunds interact badly with disputes. If a customer has already opened a chargeback and the merchant also issues a refund, the customer can receive the money twice. Check for an open dispute first. If a refund was issued before the dispute, submit that as evidence through [representment](./Representment.md).

Visa's rules require a refund to the same payment credential where possible, with listed exceptions. Refunds to a different card are a known fraud pattern. Whether the merchant recovers its processing fees depends on its contract.

_Usage:_

"The customer says the refund never arrived, but our dashboard shows it succeeded."

"Send them the ARN. Their bank can use it to find the credit."
