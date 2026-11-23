---
description: The transfer of a merchant's available funds from its acquirer or payment provider to its bank account.
---

A payout is the transfer of funds from an [acquirer](./Acquirer.md) or [payment service provider](./Payment%20service%20provider.md) to a [merchant's](./Merchant.md) bank account. It is the last step of the card flow and the first point at which the business can spend the money. Some providers call it a deposit, remittance or funding.

A payout differs from [settlement](./Settlement.md), which moves money between institutions. Settlement can complete while the merchant still has not been paid.

A payout is rarely the sum of the day's sales. It is a net amount.

| Line item                                         | Effect on payout |
| ------------------------------------------------- | ---------------- |
| Captured sales                                    | Adds             |
| [Refunds](./Refund.md)                            | Subtracts        |
| [Chargebacks](./Chargeback.md) and dispute fees   | Subtracts        |
| Processing fees                                   | Subtracts        |
| Newly withheld [rolling reserve](./Rolling%20reserve.md) | Subtracts        |
| Released reserve                                  | Adds             |
| Reversed chargebacks                              | Adds             |

This is why finance teams often find a deposit that matches no order total. Reconcile by obtaining the provider's list of transactions included in each payout, using its payout ID, rather than comparing bank deposits with daily sales. This is a main task of [payment reconciliation](./Payment%20reconciliation.md).

A balance can also go negative. If refunds and chargebacks exceed new sales, there is nothing to pay out, and the provider may debit the merchant's bank account or recover the shortfall from future sales. A payout can fail when bank details are wrong or an account is closed, and the funds then return to the provider's balance.

Providers may pause payouts during a risk or compliance review, for example when [KYB](./KYB.md) details are missing, sales patterns change sharply, or a [sanctions screening](./Sanctions%20screening.md) alert is unresolved.

On a platform, the term also covers payments to sellers, which may use a [split payment](./Split%20payment.md). Model each payout in your [ledger](./Ledger.md) as a separate record linked to the transactions it contains, and treat a provider's "paid" status as provisional until the bank confirms receipt.

_Usage:_

"Today's deposit is 3,100 but we sold 4,000 yesterday."

"Pull the payout breakdown. It nets out refunds, fees and that chargeback from last week."
