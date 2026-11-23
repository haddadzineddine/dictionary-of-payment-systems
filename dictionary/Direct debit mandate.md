---
description: A payer's authorization allowing a named creditor to collect payments from their bank account under scheme rules.
---

A direct debit mandate is the authorization a payer gives a creditor to collect money from their bank account. It identifies the parties and the account, and it sets the terms of the collection. Without a valid mandate, a debit can be returned as unauthorised. Each scheme has its own name and rules for it:

| Region | Scheme or service         | Mandate details                                                   |
| ------ | ------------------------- | ----------------------------------------------------------------- |
| SEPA   | [SEPA Direct Debit](./SEPA%20Direct%20Debit.md)         | Creditor identifier plus a unique mandate reference               |
| UK     | Bacs Direct Debit         | Direct Debit Instruction, backed by the Direct Debit Guarantee    |
| US     | [ACH](./ACH.md)                       | Authorization under Nacha rules, with requirements by entry type  |
| India  | [UPI](./UPI.md) AutoPay and NACH      | Registered e-mandate, under Reserve Bank of India and NPCI rules  |
| Brazil | [Pix](./Pix.md) Automático            | Payer's prior authorization, under Banco Central do Brasil rules  |

A mandate differs from a [stored credential](./Stored%20credential.md). A stored credential is a saved card used under [card network](./Card%20network.md) rules. A mandate authorises debits from a bank account under a bank scheme. It also differs from [recurring billing](./Recurring%20billing.md), which is the business process that decides when to collect. A mandate is only the permission.

Under the UK guarantee, if an error is made, the payer's bank must give a full and immediate refund, then reclaim it from the collecting organisation through an indemnity claim.

The failures are mostly about evidence and lifecycle. A customer disputes a debit and the business cannot produce the mandate, so it loses the money. A migration between providers drops mandate references, and the next collection is rejected. A price rise goes out without the required advance notice, and customers claim refunds.

Store the reference, scheme, signature date, wording version and proof of consent. Mark a mandate as cancelled as soon as the bank or customer revokes it, and stop collecting against it.

_Usage:_

"The bank returned the debit saying there's no valid mandate."

"We lost the mandate references in the provider migration. Pause collections and re-collect them from affected customers."
