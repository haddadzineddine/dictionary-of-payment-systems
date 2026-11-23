---
description: A temporary reduction in a cardholder's available funds after an approved authorization, before any money is taken.
---

An authorization hold is a temporary reduction in a [cardholder's](./Cardholder.md) available balance or credit after an [issuer](./Issuer.md) approves a [card authorization](./Card%20authorization.md). The money stays in the account but cannot be spent. Banking apps usually show it as "pending", which is why customers often read a hold as a completed charge.

This is the source of a frequent support ticket. A customer's first checkout attempt appears to fail, they try again, and now see two pending amounts. Only one order exists, but both approvals are holding funds. The customer reports being charged twice, even though neither hold has been captured. On a debit card with a low balance, the extra hold can also cause an unrelated payment or rent debit to fail.

| Event                                          | Effect on the hold                         |
| ---------------------------------------------- | ------------------------------------------ |
| [Capture](./Capture.md) and [clearing](./Clearing.md)                         | Replaced by the posted transaction         |
| [Partial capture](./Partial%20capture.md)      | Unused part should be released             |
| [Incremental authorization](./Incremental%20authorization.md) | Held amount increases                      |
| [Authorization reversal](./Authorization%20reversal.md) | Issuer releases the funds                  |
| No further action                              | Issuer drops it after its own time limit   |

A [merchant](./Merchant.md) controls whether a hold is captured or released, but the issuer controls how quickly the customer sees the change. A released hold can continue to display for some time in a banking app. How long an unused hold lasts depends on the issuer, the network and the transaction type, so avoid promising customers a specific number of days.

The fix for abandoned or duplicate approvals is to send a reversal as soon as you know the funds are not needed. Visa's rules require a reversal in specified cases, including when a transaction is cancelled or finishes below the authorized amount, and Visa can assess a fee on approvals that are neither cleared nor reversed. Mastercard has its own requirements.

_Usage:_

"A customer says we charged her twice for one order."

"One is a stale hold from the failed attempt. Send the reversal and tell her it should drop off once her bank processes it."
