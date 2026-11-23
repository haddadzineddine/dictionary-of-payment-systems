---
description: An append-only record of money movements between accounts, from which balances are derived and audited.
---

A ledger is an append-only record of every movement of money between accounts. Each posting records the account, amount, currency, direction and a reference to the event that caused it. Balances are computed from those entries, or kept as a cached figure that can be rebuilt from them.

A ledger differs from a `payments` table. The payments table describes the state of a payment attempt and changes over time. The ledger records the financial effect of each step and never changes. A `balance` column on a user row shows a total but cannot explain it, so when a customer asks why their balance is wrong, there is no answer.

Most payment ledgers use [double-entry bookkeeping](./Double-entry%20bookkeeping.md), so each transaction's debits and credits are equal. Amounts are integers in each currency's [minor unit](./Minor%20unit.md).

Entries are never edited or deleted. To correct a mistake, post a reversal and then the correct entry. In this example, a 5000 top-up was recorded instead of 500:

| Txn | Reason         | Account          | Debit | Credit |
| --- | -------------- | ---------------- | ----: | -----: |
| 1   | Original       | Cash at provider |  5000 |        |
| 1   | Original       | Customer balance |       |   5000 |
| 2   | Reversal of 1  | Customer balance |  5000 |        |
| 2   | Reversal of 1  | Cash at provider |       |   5000 |
| 3   | Correct amount | Cash at provider |   500 |        |
| 3   | Correct amount | Customer balance |       |    500 |

After all three, cash has a net debit of 500 and the customer balance a net credit of 500. The error and its fix both remain visible to auditors.

Enforce the invariants in the database. Reject a transaction whose debits and credits differ per currency, write all of its entries atomically, and use a unique key on the source event so a replayed event cannot post twice. Reconcile it against provider and bank records, because a balanced ledger can still be wrong.

_Usage:_

"Can I just update this customer's balance to fix the mistake?"

"No. Post a reversal and a correcting entry in the ledger, so the history still adds up."
