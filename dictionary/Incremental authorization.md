---
description: An added authorization that raises the approved amount on an existing card transaction when the final cost grows.
---

An incremental authorization is an extra request that increases the amount approved on an existing card transaction. It is used when the cost grows after the first approval: a hotel guest extends a stay, a rental car is kept longer, or a bar tab increases.

Visa defines it as a request that follows an approved estimated [authorization](./Card%20authorization.md) and covers an additional amount the [cardholder](./Cardholder.md) is expected to spend or has incurred in that same transaction. Mastercard handles the same need through preauthorizations, with additional requests referencing the original by its trace identifier. Eligibility varies by network, region, [merchant category](./Merchant%20category%20code.md) and [acquirer](./Acquirer.md), so a flow that works for one brand may not work for another.

| Option                    | Links to original? | Effect on the customer                  |
| ------------------------- | ------------------ | --------------------------------------- |
| Incremental authorization | Yes                | One growing [authorization hold](./Authorization%20hold.md) |
| New separate authorization | No                 | Two holds, which can look like two charges |
| Reauthorization           | Yes, by rule       | Refreshes an approval that is expiring  |
| [Partial capture](./Partial%20capture.md) | Yes                | Takes less than was approved            |

The link matters because the [issuer](./Issuer.md) needs to know this is the same purchase. Without it, a [merchant](./Merchant.md) that sends a fresh approval for the extra amount creates a second hold and a second record. The customer sees two pending entries, and [clearing](./Clearing.md) may no longer match cleanly to one authorization.

An incremental request is a new decision and can be declined. A guest with a nearly full credit limit may be approved at check-in and declined when the stay is extended. The merchant is then exposed for the extra amount unless it collects another payment method, so request the increase before providing the additional service.

Pass the [network transaction ID](./Network%20transaction%20ID.md) from the original approval on each increment and release any unused amount at the end.

_Usage:_

"The guest added two nights and now has two pending hotel charges."

"We sent a new auth. It should have been an incremental on the original transaction."
