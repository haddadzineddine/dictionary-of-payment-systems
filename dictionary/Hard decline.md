---
description: A card refusal that retrying will not fix, such as a closed account or a card reported lost or stolen.
---

A hard decline is a card refusal that will not be resolved by trying the same card again. The account may be closed, the card may be reported lost or stolen, or the transaction type may not be allowed. The next step is to get a different payment method.

"Hard decline" is industry shorthand and has no single definition across networks. Visa's rules contain the closest formal version: Category 1 [decline codes](./Decline%20code.md), labelled "[issuer](./Issuer.md) will never approve", which a [merchant](./Merchant.md) must never reattempt.

| Visa Category 1 code | Meaning                              |
| -------------------- | ------------------------------------ |
| `04`                 | Pick up card, no fraud               |
| `07`                 | Pick up card, special condition      |
| `41`                 | Lost card                            |
| `43`                 | Stolen card                          |
| `46`                 | Closed account                       |
| `57`                 | Transaction not permitted to [cardholder](./Cardholder.md) |
| `R0`, `R1`, `R3`     | Stop-payment instructions            |

Other networks classify codes differently. Mastercard, for example, uses merchant advice codes to tell merchants how to respond, so a mapping built only from Visa's table is incomplete. Generic codes such as `05` "do not honor" should not automatically count as hard or soft. A [soft decline](./Soft%20decline.md), by contrast, may succeed after a change.

The common failure occurs in [recurring billing](./Recurring%20billing.md). A subscription job retries a closed card on every [dunning](./Dunning.md) cycle. Each attempt fails, adds authorization cost, and lowers the merchant's [authorization rate](./Authorization%20rate.md), and it can also breach network retry rules.

The correct handling is to stop retries, mark the stored card unusable, and ask the customer to update it. An [account updater](./Account%20updater.md) or [network token](./Network%20token.md) can sometimes supply new details after a reissue, but do not use these to continue charging a card reported stolen or an account the customer closed deliberately. Tell the customer only that the payment was declined.

_Usage:_

"This subscription has failed six months in a row. Should dunning keep going?"

"Check the code. If it's a 46, that's a hard decline, so stop retrying and email them for a new card."
