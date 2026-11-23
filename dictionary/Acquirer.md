---
description: The licensed institution that signs merchants, submits their card transactions and answers to the network for them.
---

An acquirer is the bank or licensed institution that contracts with a [merchant](./Merchant.md) to accept card payments, enters those transactions into the [card network](./Card%20network.md), and arranges for the merchant to be paid. Visa's rules define it as a member that signs a merchant or [payment facilitator](./Payment%20facilitator.md) and enters transactions into interchange, the exchange of transactions between members. In the EU, [PSD2](./PSD2.md) treats acquiring as a regulated payment service.

The acquirer is the merchant-side counterpart of the [issuer](./Issuer.md).

| Party                                         | Works for    | Main job                                                 |
| --------------------------------------------- | ------------ | -------------------------------------------------------- |
| Issuer                                        | [Cardholder](./Cardholder.md)   | Approves payments and bills the card account             |
| Acquirer                                      | Merchant     | Sponsors the merchant on the network and funds it        |
| [Payment processor](./Payment%20processor.md) | Either party | Runs the transaction systems, often for an acquirer      |
| [Payment gateway](./Payment%20gateway.md)     | Merchant     | Connects the checkout to the processing systems          |

The acquirer carries financial responsibility to the network for the merchants it signs. If a merchant closes while [chargebacks](./Chargeback.md) are still arriving, and cannot repay them, the acquirer can be left covering the loss. Mastercard's rules also make an acquirer responsible for the acts and omissions of its payment facilitators and their sponsored merchants.

An acquirer therefore reviews a business before onboarding, using [KYB](./KYB.md) checks, and keeps monitoring it afterwards. A sudden jump in sales, a rising [chargeback ratio](./Chargeback%20ratio.md), or a move into a higher-risk product can lead it to delay a [payout](./Payout.md), impose a [rolling reserve](./Rolling%20reserve.md), or end the relationship.

Many businesses never deal with an acquirer directly. A [payment service provider](./Payment%20service%20provider.md) may hold the acquiring relationship, or partner with one or more acquirers, and present a single contract. If support asks "who is your acquirer?", check the provider's terms or [settlement](./Settlement.md) reports rather than assuming the provider is the acquirer.

_Usage:_

"Why are they holding back part of our payouts all of a sudden?"

"Our volume tripled in a month. The acquirer is on the hook if those orders turn into chargebacks, so it added a reserve."
