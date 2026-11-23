---
description: A business or person that accepts card payments for goods or services, directly or through a facilitator.
---

A merchant is a business or person that accepts a card as payment for goods or services. Visa's rules separate a merchant with its own agreement with an [acquirer](./Acquirer.md) from a sponsored merchant that contracts through a [payment facilitator](./Payment%20facilitator.md). Mastercard uses similar categories, and treats the facilitator as acting for the acquirer.

A business selling online is not automatically the merchant on the card transaction. The contract decides that.

| Setup                                                | Contract is with                      | Seller shown on the transaction |
| ---------------------------------------------------- | ------------------------------------- | ------------------------------- |
| Direct merchant                                      | Acquirer                              | The business                    |
| Sponsored merchant                                   | Payment facilitator                   | The business                    |
| Retailer on a marketplace                            | Marketplace                           | Usually the marketplace         |
| Product sold through a [merchant of record](./Merchant%20of%20record.md) | Reseller acting as merchant of record | The reseller                    |

The merchant agrees to follow [card network](./Card%20network.md) rules through its contract. In practice this means describing the business accurately, showing a recognisable [statement descriptor](./Statement%20descriptor.md), protecting card data under [PCI DSS](./PCI%20DSS.md), issuing a [refund](./Refund.md) when owed, and answering each [chargeback](./Chargeback.md). For most online payments the merchant also carries the loss from fraud unless a [liability shift](./Liability%20shift.md) applies.

Each merchant is identified by a merchant ID assigned by its acquirer and classified with a [merchant category code](./Merchant%20category%20code.md). This classification is a frequent source of trouble. A business approved to sell software that starts selling supplements or gift cards no longer matches what it declared. The acquirer may notice through monitoring, then pause its [payout](./Payout.md) or close the [merchant account](./Merchant%20account.md) while it reviews the activity.

To avoid that, tell the acquirer or [payment service provider](./Payment%20service%20provider.md) before adding a product line, changing ownership, or selling in a new country.

_Usage:_

"Why did our payouts stop after we launched the gift card range?"

"We were onboarded as a software merchant. Risk flagged the new product, so we need to update our business profile with the acquirer."
