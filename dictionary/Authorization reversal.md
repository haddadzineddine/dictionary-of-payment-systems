---
description: A message telling the issuer to cancel all or part of an approved authorization so the held funds are released.
---

An authorization reversal is a message that cancels all or part of an approved [card authorization](./Card%20authorization.md), telling the [issuer](./Issuer.md) to release the funds it was holding. Visa's rules describe it as a system message that cancels an approval response. It applies before the transaction has been cleared.

| Term                  | Stage                          | Mechanism                         | Money already moved? |
| --------------------- | ------------------------------ | --------------------------------- | -------------------- |
| Authorization reversal | After approval, before [clearing](./Clearing.md) | Network message to the issuer     | No                   |
| [Void](./Void.md)     | Before clearing submission     | Provider action, often sends a reversal | No                   |
| [Refund](./Refund.md) | After clearing                 | New credit transaction            | Yes                  |

A [merchant](./Merchant.md) needs a reversal in four common situations: the customer cancels, stock runs out, the final amount is lower than approved, or a timeout leaves an approval the merchant cannot use. The issuer approves, the response is lost, and the merchant records a failure. The customer's funds stay on hold for an order that does not exist. Visa's rules require a reversal when a point-of-sale merchant receives an approval after timing out.

Requirements are network-specific. Visa requires merchants to submit reversals in listed cases and can charge a misuse-of-authorization fee on approvals matched to neither a clearing record nor a reversal. Mastercard's Transaction Processing Rules set separate requirements, including a timed rule in the Europe region for cancelled or reduced transactions.

Reversals can be full or partial. A partial reversal reduces the held amount and is the usual companion to a [partial capture](./Partial%20capture.md). The message must reference the original authorization, normally through the [network transaction ID](./Network%20transaction%20ID.md) or matching data, or the issuer may not connect the two.

Visa also uses "Reversal" for a separate correction of a transaction sent through clearing in error. When reading a rulebook or provider log, check which of the two is meant.

_Usage:_

"The auth call timed out, so we marked the order failed. Are we done?"

"No. It may have been approved. Send a reversal, or the customer's money stays on hold."
