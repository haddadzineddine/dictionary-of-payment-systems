---
description: A payment card that spends a preloaded balance held by the programme, not a linked current account or a credit line.
---

A prepaid card is a payment card that draws on money loaded in advance rather than on a linked bank account or a credit line. An [issuer](./Issuer.md), or a programme manager working with one, holds the balance. Common forms are gift, payroll, travel and reloadable general-purpose cards. Most run on a [card network](./Card%20network.md), so a [merchant](./Merchant.md) accepts them like other cards.

| Card type | Spends from                        | Issuer's exposure       |
| --------- | ---------------------------------- | ----------------------- |
| Credit    | A credit line, repaid later        | Credit risk             |
| Debit     | The holder's bank account          | Mostly the account balance |
| Prepaid   | A balance loaded in advance        | Limited to the balance, plus programme risk |

Regulation depends on the product and the jurisdiction. In the US, the Consumer Financial Protection Bureau's Prepaid Rule applies disclosure and error-resolution protections to many prepaid accounts. In the EU and UK, many prepaid products are e-money, so issuers need authorisation and must meet [safeguarding](./Safeguarding.md) requirements. Gift cards and closed-loop cards usable at one merchant may fall under different rules or exemptions.

A merchant usually meets prepaid cards through declines. An [authorization hold](./Authorization%20hold.md) for an estimated amount can exceed the remaining balance, which is common at fuel pumps and hotels, even if the final charge would have fit. The [BIN](./BIN.md) can also show that a card is prepaid, and some merchants block these cards for subscriptions because they run out of funds on renewal.

Some card programmes support partial approval, where the issuer approves only the available balance and the customer pays the rest another way. Enable it if your checkout can collect a second payment. [Refunds](./Refund.md) can also be awkward when a card has expired or been discarded, so keep an alternative refund route, such as store credit where the law allows.

_Usage:_

"This customer's card keeps declining at pre-auth, but they say there's money on it."

"It's a prepaid card and our hold is bigger than the balance. Lower the hold or support partial approval."
