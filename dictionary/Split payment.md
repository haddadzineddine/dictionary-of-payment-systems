---
description: One customer payment divided among several parties, such as a marketplace, its sellers and fee recipients.
---

A split payment is a single customer payment whose funds are divided among several recipients, such as a marketplace, one or more sellers and a delivery partner. The customer sees one charge.

This example uses [minor units](./Minor%20unit.md) for a 10000 order:

| Account             | Debit | Credit |
| ------------------- | ----: | -----: |
| Provider receivable |  9700 |        |
| Processing fees     |   300 |        |
| Seller payable      |       |   8500 |
| Platform commission |       |   1500 |
| **Total**           | **10000** | **10000** |

The platform absorbs the processing fee here, so its net income from this order is 1200.

A split payment differs from split tender, where one customer pays a single bill using two cards or methods.

Regulation is a central design issue. Receiving money and passing it to third parties can count as a regulated payment service or money transmission, depending on the country. Platforms commonly use a licensed provider's marketplace product, or act as a [payment facilitator](./Payment%20facilitator.md) or a [merchant of record](./Merchant%20of%20record.md). Get legal advice on the chosen structure, and expect [KYC](./KYC.md) or [KYB](./KYB.md) checks on sellers.

The hard failures occur after the split. A customer gets a [refund](./Refund.md) or wins a [chargeback](./Chargeback.md) after the seller has already received a [payout](./Payout.md). The platform must recover the money from that seller, and if the seller has no balance or has left, the platform carries the loss. Delay seller payouts according to risk, and let seller balances go negative in the [ledger](./Ledger.md) so future earnings can offset them.

Rounding is the other common bug. Splitting 10000 three ways gives 3333 each and leaves 1 unit unallocated. Use integer minor units, assign any remainder by a fixed rule, and assert that the parts sum to the total. Record the split at payment time so that later commission changes do not alter past orders.

_Usage:_

"The seller was paid out, then the buyer got a chargeback. Who covers it?"

"Under our split payment terms, the seller. Post it against their balance, and we carry it if they can't repay."
