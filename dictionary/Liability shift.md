---
description: A network rule moving the cost of certain card fraud from one party to another, usually after chip or 3-D Secure use.
---

A liability shift is a [card network](./Card%20network.md) rule that moves the cost of certain fraud from one party to another when a security measure was or was not used. It determines whether the [merchant's](./Merchant.md) side or the [issuer](./Issuer.md) absorbs the loss on a fraudulent transaction. The two common forms cover chip payments and online authentication.

| Type                    | Where                               | Who usually bears the fraud                                       |
| ----------------------- | ----------------------------------- | ----------------------------------------------------------------- |
| Chip                    | [Card-present](./Card-present%20transaction.md), participating regions | The party that did not support [EMV](./EMV.md) chip                |
| [3-D Secure](./3-D%20Secure.md) | [Card-not-present](./Card-not-present%20transaction.md) | Issuer, where the payment was properly authenticated  |
| No shift                | Other online payments               | Usually the merchant                                              |

The details are network- and region-specific.

| Network    | Chip rule                                   | Authentication rule                                          |
| ---------- | ------------------------------------------- | ------------------------------------------------------------ |
| Visa       | Dispute Conditions 10.1 and 10.2, with listed regions | Condition 10.4 invalid for qualifying Visa Secure payments |
| Mastercard | Reason code 4870, chip liability shift      | Reason code 4837 excludes properly authenticated payments    |

A common misunderstanding is believing that 3-D Secure stops all [chargebacks](./Chargeback.md). The shift applies to fraud claims. A customer who says goods never arrived or were defective can still dispute an authenticated payment, because that is a consumer dispute.

A shift can also fail for technical reasons. If an integration drops the authentication value from the [card authorization](./Card%20authorization.md), or sends the wrong electronic commerce indicator, the network treats the payment as unauthenticated even though the customer completed a challenge. Network rules also contain exclusions, and an [SCA exemption](./SCA%20exemption.md) generally leaves liability where it was.

This contractual shift is different from the legal allocation under [PSD2](./PSD2.md). Article 74(2) says that a payee or payee's provider that fails to accept [strong customer authentication](./Strong%20customer%20authentication.md) must [refund](./Refund.md) the financial damage caused to the payer's provider.

Store the authentication result on each payment so it can be used as evidence in [representment](./Representment.md).

_Usage:_

"We used 3DS on that order, so why are we losing this chargeback?"

"It's a not-received dispute. The liability shift only covers fraud claims."
