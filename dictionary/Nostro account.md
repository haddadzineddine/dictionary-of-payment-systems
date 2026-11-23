---
description: A bank's account held at another bank, usually in foreign currency, which the other bank calls a vostro account.
---

A nostro account is an account that a bank holds at another bank, usually in a foreign currency, in order to make and receive payments in that currency. The word comes from the Italian for "ours". The bank holding the account calls the same account a vostro account, meaning "yours". Both names describe one account seen from two sides.

A nostro is an asset on the owning bank's books, because it is money owed to that bank. The matching vostro is a liability on the correspondent's books. This example shows Bank A paying 1,000 USD on behalf of a customer through its nostro at Bank B, with the beneficiary also banking at B:

| Bank | Account                   | Type      | Debit | Credit |
| ---- | ------------------------- | --------- | ----: | -----: |
| A    | Customer's USD account    | Liability | 1,000 |        |
| A    | Nostro at Bank B          | Asset     |       |  1,000 |
| B    | Vostro for Bank A         | Liability | 1,000 |        |
| B    | Beneficiary's account     | Liability |       |  1,000 |

Each bank's entries balance. Bank A's nostro asset and its liability to the customer both fall by 1,000. Bank B's total liabilities stay the same, because its obligation moves from Bank A to the beneficiary.

Banks use nostros as part of [correspondent banking](./Correspondent%20banking.md), and their treasury teams must keep enough in each currency to cover outgoing payments. Too little causes failed or delayed payments or overdraft charges. Too much ties up cash in idle balances.

The operational task is nostro reconciliation: comparing the bank's internal record of the account with the statements sent by the correspondent. An item on one side but not the other is called a break. Common causes are a fee the correspondent deducted, a payment in transit across a cut-off, or a duplicate. Unresolved breaks can hide errors or fraud, so teams track their age.

_Usage:_

"Why is the USD position 25 dollars off this morning?"

"There's a nostro break. The correspondent deducted a fee that we haven't booked, so post it and clear the item."
