---
description: The exchange of final card transaction records between acquirer and issuer, which sets what each institution owes.
---

Clearing is the exchange of final transaction records between an [acquirer](./Acquirer.md) and an [issuer](./Issuer.md) through a [card network](./Card%20network.md). It tells the issuer the final amount to post to the customer's account and calculates what the institutions owe each other. Visa's rules describe it as the validation and valuation of records exchanged between Visa and its members. Mastercard calls the record a first presentment.

Clearing sits between the [merchant's](./Merchant.md) instruction and the actual movement of money.

| Stage                                     | What it does                          | Output                           |
| ----------------------------------------- | ------------------------------------- | -------------------------------- |
| [Card authorization](./Card%20authorization.md) | Issuer approves the payment           | Approval and hold                |
| [Capture](./Capture.md)                   | Merchant confirms the amount          | Instruction to acquirer or batch |
| Clearing                                  | Records are exchanged and valued      | Final amounts, fees, positions   |
| [Settlement](./Settlement.md)             | Institutions pay net amounts          | Funds transferred                |
| [Payout](./Payout.md)                     | Provider pays the merchant            | Bank deposit                     |

Clearing is where the actual transaction amount becomes final, and it can differ from the authorized amount. A restaurant authorizes the bill and clears it with a tip. A clearing record is also where [interchange](./Interchange%20fee.md) and [scheme fees](./Scheme%20fee.md) are typically determined, so data quality at this stage affects cost. Incorrect [merchant category codes](./Merchant%20category%20code.md) or missing fields can lead to a higher fee category.

Most card transactions use a dual-message flow, with one message for authorization and another for clearing. Some debit systems use a single message for both.

A common engineering problem is treating the authorization as the final record. If the clearing amount differs, or clears on a different date or in a different currency, a ledger built from authorization data will not match the [settlement file](./Settlement%20file.md). Build [payment reconciliation](./Payment%20reconciliation.md) from cleared records. Visa also assesses fees on clearing records with no matching approval, so clearing transactions must keep the references from the original authorization.

_Usage:_

"Why does the charge in our ledger differ from the settlement report by the tip amount?"

"The ledger used the auth. Clearing carried the final amount, so reconcile against that."
