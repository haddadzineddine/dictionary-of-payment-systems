---
description: Collecting less than the authorized card amount, for example when only part of an order ships.
---

A partial capture collects less than the amount approved in a [card authorization](./Card%20authorization.md). A customer orders three items for 90, the [merchant](./Merchant.md) authorizes 90, one item is out of stock, and the merchant captures 60.

The step people miss is what happens to the remaining 30. Capturing 60 does not guarantee that the rest of the [authorization hold](./Authorization%20hold.md) is released promptly. The customer can see a 60 charge and a 90 pending amount at the same time and believe they were overcharged.

| Situation                 | Correct handling                                                     |
| ------------------------- | -------------------------------------------------------------------- |
| Final amount is lower     | Capture the lower amount, release the difference     |
| Order cancelled entirely  | Send a full [authorization reversal](./Authorization%20reversal.md)  |
| Final amount is higher    | Use [incremental authorization](./Incremental%20authorization.md) if eligible |
| Already settled, too high | Issue a [refund](./Refund.md) for the difference                     |

Network rules address the unused amount. Visa requires a merchant to submit an authorization reversal for the difference when a completed transaction's final amount is less than the amount authorized. Mastercard's rules for Europe require a reversal when a transaction is finalised at a lower amount, and its other regions have their own wording. Many [payment service providers](./Payment%20service%20provider.md) send this automatically, but confirm it rather than assume.

Partial capture is different from multiple capture, which takes several amounts against one authorization, usually for split shipments. Multiple capture is more restricted. Visa permits a single authorization with multiple [clearing](./Clearing.md) records only in listed cases, including airlines, cruise lines, US railways, and card-absent merchants shipping goods in parts, with conditions such as telling the [cardholder](./Cardholder.md).

Engineers should store authorized, captured and refunded amounts as separate fields in [minor units](./Minor%20unit.md). A single `amount` column cannot represent a partly captured payment, and support then cannot tell what the customer actually paid.

_Usage:_

"She was charged 60 but her bank still shows 90 pending."

"We did a partial capture and never released the other 30. Check whether the provider sent the reversal."
