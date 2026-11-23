---
description: A share of each payout that a provider holds for a set period to cover future refunds and chargebacks.
---

A rolling reserve is an arrangement in which a [payment service provider](./Payment%20service%20provider.md) withholds a percentage of each [settlement](./Settlement.md) and releases it after a fixed period. It protects the provider against losses that arrive after a sale, mainly a [chargeback](./Chargeback.md) or [refund](./Refund.md) the [merchant](./Merchant.md) can no longer fund. If the merchant fails, the [acquirer](./Acquirer.md) can still be liable to the [card network](./Card%20network.md), so it holds this money as cover.

The contract sets the percentage and the holding period. Providers commonly apply a reserve to higher-risk categories, new businesses, merchants with long delivery times, or accounts with rising disputes. Other forms exist: a fixed reserve holds one lump sum, and delayed [payout](./Payout.md) lengthens the time before any funds are paid.

This example uses invented figures and a 10% reserve, with amounts in [minor units](./Minor%20unit.md):

| Event                   | Available | Reserve | Total |
| ----------------------- | --------: | ------: | ----: |
| Sale of 100000 settles  |     90000 |   10000 | 100000 |
| Chargeback of 5000      |     85000 |   10000 |  95000 |
| Reserve period ends     |     95000 |       0 |  95000 |

A reserve is not a fee. The money still belongs to the merchant, subject to the contract, and is normally recorded as a receivable. Booking the withheld amount as an expense overstates costs and hides money the business expects to receive.

Merchants usually discover a reserve when a payout is lower than expected, or when cash runs short during fast growth because a growing portion of revenue is held at any one time. Model a separate reserve balance in the [ledger](./Ledger.md), using the release date from the settlement data, and forecast cash on that basis. To negotiate a lower reserve, show the provider a clean dispute history and shorter delivery times.

_Usage:_

"Payouts are 10% lower than sales since we moved to the new provider."

"They put us on a rolling reserve. It's released after the holding period, so book it as a receivable, not a fee."
