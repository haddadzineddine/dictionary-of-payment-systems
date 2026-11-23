---
description: Automated use of a merchant's checkout to find which stolen card details work, seen as bursts of small failed payments.
---

Card testing is a fraud attack in which criminals use a [merchant's](./Merchant.md) payment flow to find out which stolen or generated card details are valid. Visa calls the wider activity account enumeration. The checkout is used as a validity check, and working cards are used or sold elsewhere.

The usual sign is a sudden burst of [card authorization](./Card%20authorization.md) attempts, many of them declined, often for small amounts and often outside business hours.

| Signal                                       | Where to look                     |
| -------------------------------------------- | --------------------------------- |
| Spike in authorization attempts              | Provider dashboard, API metrics   |
| Sharp fall in [authorization rate](./Authorization%20rate.md) | Payment monitoring |
| Many different cards from one device, IP or session | Checkout and fraud logs    |
| Many cards sharing a [BIN](./BIN.md)         | [Decline code](./Decline%20code.md) reports |
| Repeated [CVV](./CVV.md) or expiry failures  | Authorization responses           |
| Unusual activity on add-card or donation pages | Endpoint metrics                |

The cost falls on the merchant in several ways: authorization fees, a damaged reputation with [issuers](./Issuer.md), later [chargebacks](./Chargeback.md) on successful attempts, and holds on real customers' cards. Visa's monitoring program, VAMP, includes a separate enumeration measure, so sustained attacks can bring network attention to the merchant and its [acquirer](./Acquirer.md).

Visa's guidance for merchants recommends layered controls.

| Control                                     | Effect                                         |
| ------------------------------------------- | ---------------------------------------------- |
| CAPTCHA on every card-validating request    | Slows automated traffic                        |
| [Velocity checks](./Velocity%20check.md)    | Limits attempts per card, device, IP, account  |
| Required CVV and [address verification](./Address%20verification.md) | Adds checks on entry     |
| Protect add-card and save-card flows        | Closes commonly overlooked endpoints           |
| Rotate API keys if abused                   | Cuts off stolen credentials                    |

During an active attack, block the traffic quickly and tell your provider or acquirer. Reverse approved test payments with an [authorization reversal](./Authorization%20reversal.md), or [refund](./Refund.md) them if already captured, because those [cardholders](./Cardholder.md) did not make them.

Keep customer-facing error messages generic, so the checkout does not reveal which card field failed.

_Usage:_

"We just had 4,000 one-dollar auths in twenty minutes, nearly all declined."

"That's card testing. Turn on the CAPTCHA, rate-limit the endpoint and tell the acquirer."
