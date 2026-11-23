---
description: The acquiring relationship that lets a business accept cards, identified by a merchant ID. It is not a normal bank account.
---

A merchant account is the arrangement between a business and an [acquirer](./Acquirer.md) that allows the business to accept card payments. It is identified by a merchant ID and carries the terms agreed at onboarding, including what the business sells, its [merchant category code](./Merchant%20category%20code.md), currencies and risk limits.

Despite the name, it is usually not an account the business can spend from. Card proceeds are tracked against it, then paid to a separate bank account.

| Item                     | What it is                                      | Can the business spend from it? |
| ------------------------ | ----------------------------------------------- | ------------------------------- |
| Merchant account         | Acquiring contract and transaction record       | No                              |
| PSP balance              | Amount a provider currently owes the business   | Only by [payout](./Payout.md), in most setups |
| Business bank account    | Ordinary account that receives the payout       | Yes                             |

This explains a common question from finance teams: the dashboard shows sales as successful, but the bank balance has not moved. The funds are still between [settlement](./Settlement.md) and payout, or they have been reduced by [refunds](./Refund.md), fees, [chargebacks](./Chargeback.md) or a [rolling reserve](./Rolling%20reserve.md).

There are two common setups. With a dedicated merchant account, the business has a direct contract with an acquirer, which usually involves more underwriting and more control over pricing and data. With an aggregated setup, a [payment facilitator](./Payment%20facilitator.md) holds the acquiring relationship and the business is a sponsored merchant beneath it, which is quicker to start but gives the provider more control over funds and account status.

If an acquirer closes a merchant account for rule violations, the closure can be recorded in network-run lists of terminated merchants, such as Mastercard's MATCH, which can make it harder to open a new one.

_Usage:_

"The dashboard says we took 40k this week, so why isn't it in the bank?"

"That's the merchant account view. The payout goes out after settlement, minus refunds and the reserve."
