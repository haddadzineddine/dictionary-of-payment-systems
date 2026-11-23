---
description: Showing and charging customers in their own currency at merchant-set prices, while settling in another or the same currency.
---

Multi-currency pricing is a setup in which a [merchant](./Merchant.md) displays and charges prices in the buyer's currency, then receives [settlement](./Settlement.md) in that currency or a different one. The currency shown to the customer is the presentment currency. The currency paid out to the merchant is the settlement currency. When they differ, the [acquirer](./Acquirer.md) or [payment service provider](./Payment%20service%20provider.md) usually performs the conversion and charges a margin.

The merchant controls the customer-facing price, using a price list per currency or a base price with a chosen rate and rounding rule. This differs from [dynamic currency conversion](./Dynamic%20currency%20conversion.md), where the item is priced in local currency and converted at the moment of payment, with the provider setting the rate.

A multi-currency payment needs more fields than a single amount:

| Field               | Example | Why it is stored                     |
| ------------------- | ------- | ------------------------------------ |
| Presentment amount  | 5000 JPY | What the customer agreed to pay     |
| Settlement amount   | 3120 USD [minor units](./Minor%20unit.md) | What the merchant received |
| Exchange rate       | As reported by the provider | Audit and reconciliation |
| Conversion fee      | 62 USD minor units | Margin cost              |

Each amount is stored in the minor unit of its own currency. In this example, 5000 JPY means 5,000 yen because the yen has no decimal places, while 3120 USD means 31.20 dollars.

The common failure happens on a [refund](./Refund.md). A customer paid 100.00 EUR, the merchant settled in USD, and the rate moved before the refund. The customer gets 100.00 EUR back, but the USD debited from the merchant differs from what it originally received. Finance sees a small unexplained gain or loss. Record the rate for each leg and post the difference to a foreign exchange gain or loss account in the [ledger](./Ledger.md).

_Usage:_

"Our refund cost more in dollars than the original sale brought in."

"That's the exchange rate moving under multi-currency pricing. Record it as an FX loss rather than adjusting the original payment."
