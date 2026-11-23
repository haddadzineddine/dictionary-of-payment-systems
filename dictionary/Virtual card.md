---
description: A card number issued digitally for a specific use, often with limits on merchant, amount or time.
---

A virtual card is a payment card that exists only as digital details: a card number, expiry date and security code. An [issuer](./Issuer.md) creates it, often through a card programme run by a fintech with a [sponsor bank](./Sponsor%20bank.md). It can be restricted to one [merchant](./Merchant.md), one use, a maximum amount or a period of time. Businesses use them to pay suppliers, control employee spending and book travel.

| Control          | Effect                                               |
| ---------------- | ---------------------------------------------------- |
| Single use       | Closes after the first successful payment            |
| Merchant lock    | Works only at a chosen merchant or [merchant category code](./Merchant%20category%20code.md) |
| Amount limit     | Declines anything above the set value                |
| Expiry           | Stops working after a chosen date                    |

A virtual card is often confused with a [network token](./Network%20token.md). A virtual card has a real [PAN](./PAN.md) and can be used anywhere its controls allow, on the [card network](./Card%20network.md) like any other card. A network token replaces an existing card number for a specific merchant or device, and it cannot be typed into another checkout.

The controls that make these cards useful also cause most of their failures. A merchant lock fails because the supplier's payment went through a parent company or a different merchant category. A hotel adds an [incremental authorization](./Incremental%20authorization.md) above the amount limit and the charge is declined. A single-use card is closed, and a later top-up or subscription renewal fails. A [refund](./Refund.md) to a closed virtual card may need manual handling by the issuer.

A hotel or rental desk may also ask for the physical card used at booking, which does not exist. Set the limit to cover expected holds and final charges, keep the card open until the transaction has fully completed, and tell the traveller in advance how payment will work.

_Usage:_

"The supplier says our payment was declined again."

"The virtual card is locked to their old merchant category. Reissue it with the new one and raise the limit."
