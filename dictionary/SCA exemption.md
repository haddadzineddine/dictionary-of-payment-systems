---
description: A condition in EU rules that allows a payment provider not to apply strong customer authentication to a payment.
---

An SCA exemption is a condition in EU rules that allows a [payment service provider](./Payment%20service%20provider.md) not to apply [strong customer authentication](./Strong%20customer%20authentication.md) to a payment. The exemptions are in Chapter III of Commission Delegated Regulation (EU) 2018/389 under [PSD2](./PSD2.md). A provider is "allowed not to apply" SCA and is never obliged to skip it. The table lists the main payment exemptions.

| Article | Exemption                  | Applies to                                                  |
| ------- | -------------------------- | ----------------------------------------------------------- |
| 11      | Contactless at point of sale | Small in-person payments, within cumulative limits        |
| 12      | Unattended terminals       | Transport fares and parking fees                            |
| 13      | Trusted beneficiaries      | Payees the payer listed with their provider                 |
| 14      | Recurring transactions     | Later payments in a series with the same amount and payee   |
| 16      | Low-value transactions     | Small remote payments, within cumulative limits             |
| 17      | Secure corporate payments  | Dedicated non-consumer processes accepted by the regulator  |
| 18      | Transaction risk analysis  | Low-risk remote payments, tied to the provider's fraud rate |

Amount limits are in the regulation and may change.

An exempt payment is covered by SCA rules but relieved of the step, while out-of-scope payments are not covered at all. The EBA and ECB list purely [merchant-initiated transactions](./Merchant-initiated%20transaction.md), mail and telephone orders, and many "one-leg" payments where one provider is outside the EEA as outside SCA.

The [merchant](./Merchant.md) or [acquirer](./Acquirer.md) can request an exemption, but the [issuer](./Issuer.md) has the final say. An EBA Q&A confirms the issuer can accept an acquirer's risk-analysis exemption, or refuse it and apply SCA. Cumulative counters are invisible to the merchant, so a small payment can still receive a [soft decline](./Soft%20decline.md). Checkout must be able to fall back to [3-D Secure](./3-D%20Secure.md).

An exempted payment also generally does not get the fraud [liability shift](./Liability%20shift.md) that an authenticated one can, although network rules vary.

_Usage:_

"We flagged this as low value, so why did the issuer decline it?"

"The issuer tracks the cumulative limit and can refuse the exemption. Fall back to 3DS on that code."
