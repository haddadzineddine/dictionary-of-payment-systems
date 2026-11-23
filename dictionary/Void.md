---
description: Cancelling a card payment before it is submitted for clearing, so that no money is collected from the customer.
---

A void cancels a card payment before it has been submitted for [clearing](./Clearing.md). Because the transaction has not been finalised, no money is taken and no [refund](./Refund.md) is needed. A shop assistant who rings up the wrong amount and cancels it immediately is performing a void.

"Void" is mainly a term used by [payment service providers](./Payment%20service%20provider.md), terminals and processors, and its exact behaviour depends on the provider. What happens underneath depends on how far the payment has gone.

| Term                                                 | When it applies                   | What happens                                  | Customer sees                 |
| ---------------------------------------------------- | --------------------------------- | --------------------------------------------- | ----------------------------- |
| Void                                                 | Before clearing submission        | Provider cancels the pending transaction      | Pending entry, then nothing   |
| [Authorization reversal](./Authorization%20reversal.md) | After approval, before [capture](./Capture.md) | Message tells the [issuer](./Issuer.md) to release funds | Hold disappears               |
| Refund                                               | After clearing or [settlement](./Settlement.md) | New credit transaction returns the money      | Charge, then a separate credit |

A void and a reversal are often the same event seen at two levels. The [merchant](./Merchant.md) calls "void" in an API, and the provider sends an authorization reversal to the issuer. A void can, however, fail to release the customer's money if the provider only removes the transaction from its own batch and sends no reversal. The sale is cancelled, but the [authorization hold](./Authorization%20hold.md) stays on the card until the issuer's time limit passes. Check which behaviour your provider documents.

Timing is the common source of errors. Providers usually close batches on a schedule, and after the cutoff a void call is rejected with an error such as "already settled". Support tools should try a void first when the payment is eligible and otherwise issue a refund. Doing both can credit a customer for money never taken, so code the choice from the payment's current state in the [payment state machine](./Payment%20state%20machine.md).

_Usage:_

"Support tried to void yesterday's order and got an error."

"The batch already closed, so it can't be voided. Issue a refund instead."
