---
description: Recording every transaction as equal debits and credits across accounts, so that errors show up as an imbalance.
---

Double-entry bookkeeping is an accounting method in which every transaction is recorded in at least two accounts, with total debits equal to total credits. Money is always shown as coming from somewhere and going somewhere. If the two sides differ, the record is wrong, and the system can detect it.

Debit and credit do not mean minus and plus. Their effect depends on the account type:

| Account type | Example                 | Debit    | Credit   |
| ------------ | ----------------------- | -------- | -------- |
| Asset        | Cash, provider receivable | Increases | Decreases |
| Liability    | Customer balances owed  | Decreases | Increases |
| Revenue      | Sales                   | Decreases | Increases |
| Expense      | Processing fees         | Increases | Decreases |

This explains a common confusion. When your bank "credits" your account, the bank's liability to you is rising. On your own books, the same cash is an asset and increases with a debit.

Here is a 100.00 sale with a 2.90 processing fee, in [minor units](./Minor%20unit.md):

| Account             | Type    | Debit | Credit |
| ------------------- | ------- | ----: | -----: |
| Provider receivable | Asset   |  9710 |        |
| Processing fees     | Expense |   290 |        |
| Sales revenue       | Revenue |       | 10000 |
| **Total**           |         | **10000** | **10000** |

When the provider pays out, debit bank cash by 9710 and credit the provider receivable by 9710. The receivable returns to zero, showing that nothing is still owed.

A single-column approach would record only +100.00 of sales, and finance would then find the bank deposit 2.90 short on every order. Double entry puts the fee in its own account, so the gap is explained.

Balance each currency separately. A conversion between currencies needs a foreign exchange account in each currency, because 100 EUR and 108 USD cannot be summed. Balanced entries do not prove correctness, since a wrong amount posted to both sides still balances, so the [ledger](./Ledger.md) must also be reconciled against external records.

_Usage:_

"The [payout](./Payout.md) is lower than sales. Where did the rest go?"

"Look at the fees account. With double-entry bookkeeping, each sale splits into the receivable and the fee, so the gap is itemised."
