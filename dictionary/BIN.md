---
description: The leading digits of a card number, identifying the issuer or program. ISO calls it the issuer identification number.
---

A BIN, or bank identification number, is the leading part of a [PAN](./PAN.md) that identifies the [issuer](./Issuer.md) or card program. ISO/IEC 7812 calls it the issuer identification number, or IIN.

The BIN was historically six digits. ISO revised the standard to make it eight, converting each six-digit range into a block of one hundred eight-digit ranges. Visa set April 2022 as the date for its clients to support eight-digit BINs and stopped assigning new six-digit issuing BINs after that.

Systems use BIN data to answer questions about a card before or during payment.

| Question                      | Used for                                                 |
| ----------------------------- | -------------------------------------------------------- |
| Which network?                | Showing the logo, [payment routing](./Payment%20routing.md) |
| Credit, debit or prepaid?     | Pricing, eligibility, blocking card types                |
| Issuing country?              | Fraud rules, [cross-border fee](./Cross-border%20fee.md) estimates |
| Consumer or commercial?       | Fee estimates, invoicing flows                           |

The move to eight digits created a quiet failure. Code that takes `pan.slice(0, 6)` and looks it up in a local table still runs, but two different programs can now share the same first six digits. A fraud rule or a block aimed at one program can then hit another, and a credit card can be classified as debit. Use the longest available prefix, and refresh BIN tables from your provider or network, because ranges are reassigned.

BIN data is an attribute of the card, so it is not proof of anything about the person using it. Issuing country in particular says where the card was issued, which may differ from where the customer lives. A [network token](./Network%20token.md) can carry its own token range rather than the underlying card's BIN.

A sudden run of declines on sequential cards from the same BIN at one [merchant](./Merchant.md) is a warning sign of [card testing](./Card%20testing.md).

_Usage:_

"Our prepaid block started rejecting normal credit cards from this bank."

"The rule matches on six digits. That range is now split across products, so move the lookup to eight-digit BINs."
