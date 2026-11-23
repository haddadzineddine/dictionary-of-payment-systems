---
description: A charge applied when a card's issuing country differs from the merchant's or acquirer's country, even in one currency.
---

A cross-border fee is a charge applied when a card payment crosses a country or region boundary, usually because the [issuer](./Issuer.md) and the [merchant](./Merchant.md)'s [acquirer](./Acquirer.md) are in different places. The [card network](./Card%20network.md) defines what counts as cross-border, and those definitions can treat a region such as the European Economic Area differently from a single country.

The term covers several charges that people often merge:

| Charge                    | Who pays                 | Who sets it          | Trigger                                 |
| ------------------------- | ------------------------ | -------------------- | --------------------------------------- |
| Network cross-border fee  | Acquirer and issuer      | Card network         | Issuer and acquirer in different regions |
| Cross-border interchange  | Acquirer, paid to issuer | Network or regulator | Inter-regional transaction              |
| Foreign transaction fee   | [Cardholder](./Cardholder.md)               | Issuer               | Foreign purchase, under the card terms  |
| Currency conversion margin | Payer or merchant       | Whoever converts     | Currencies differ                       |

A cross-border fee does not require a currency conversion. A US cardholder paying a merchant in US dollars can still be charged a foreign transaction fee if the merchant's acquirer is abroad. The customer then complains about a fee on a payment that appeared to be domestic, and the merchant's support team cannot see the charge because the issuer applied it.

Merchants see the cost as a higher fee on foreign cards. Interchange can rise sharply when a payment becomes inter-regional. Payments between the UK and EEA are a current example: the UK's Payment Systems Regulator has been working on a cap for fees on EEA-issued cards used online at UK businesses.

Businesses with significant foreign volume can reduce the cost by acquiring locally, using a domestic acquirer in each main market. That requires a local legal entity or an eligible provider setup in many countries, so check the requirements. [Payment routing](./Payment%20routing.md) can then send each card to the local acquirer.

_Usage:_

"A US customer was charged a foreign fee, but we billed in dollars."

"Our acquirer is in Ireland, so the issuer treated it as cross-border. Currency wasn't the trigger."
