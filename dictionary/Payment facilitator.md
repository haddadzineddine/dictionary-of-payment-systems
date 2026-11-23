---
description: A company registered through an acquirer to onboard and process payments for smaller sponsored merchants.
---

A payment facilitator, or PayFac, is a company registered through an [acquirer](./Acquirer.md) to accept card payments on behalf of smaller businesses, called sponsored [merchants](./Merchant.md) or sub-merchants. Instead of each business getting its own [merchant account](./Merchant%20account.md), the facilitator onboards them under its own acquiring relationship, often quickly.

Network definitions differ. Visa classes a facilitator as a third-party agent and treats an entity as one if it deposits transactions, receives [settlement](./Settlement.md), or contracts with an acquirer on behalf of a sponsored merchant. Mastercard defines it as a service provider registered by an acquirer to facilitate transactions for submerchants, and its rules make the acquirer responsible for the facilitator and those submerchants.

| Party                                        | Responsibility                                        |
| -------------------------------------------- | ----------------------------------------------------- |
| Acquirer                                     | Registers the facilitator, answers to the network     |
| Payment facilitator                          | Onboards, monitors and usually pays sub-merchants     |
| Sponsored merchant                           | Sells goods and remains the seller to the [cardholder](./Cardholder.md)  |
| [Card network](./Card%20network.md)          | Sets the facilitator program rules                    |

The term is often confused with two others. A [payment service provider](./Payment%20service%20provider.md) is a broader commercial label, and many PSPs operate as facilitators for small accounts. A [merchant of record](./Merchant%20of%20record.md) is itself the seller, whereas a sponsored merchant stays the seller and the facilitator provides the acceptance. Visa also treats a marketplace as a separate category.

Fast onboarding has a visible cost. The facilitator may let a business start charging after light checks, then complete fuller [KYB](./KYB.md) review once volume grows. A seller can therefore process payments for weeks and then find its [payout](./Payout.md) paused until it supplies ownership documents. Facilitators do this because they carry risk for [chargebacks](./Chargeback.md) from sub-merchants that disappear.

_Usage:_

"Our new seller processed fine for a month, and now their payout is frozen."

"They hit the review threshold on our PayFac. Ask them for the ownership documents so compliance can release it."
