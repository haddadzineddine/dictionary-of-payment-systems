---
description: A bank-rail reversal in which a debit or credit is sent back, with a reason code, after being submitted or settled.
---

A payment return is a bank-rail message that sends a debit or credit back to the originating bank because it could not be applied or is being contested. The money moves back, and the message carries a reason code. Returns occur on [ACH](./ACH.md), SEPA and other bank rails, often after the payment appeared successful.

A return is different from a [refund](./Refund.md), which the [merchant](./Merchant.md) chooses to issue, and from a [chargeback](./Chargeback.md), which is the card dispute process. It also differs from a rejection, where a payment is refused before [settlement](./Settlement.md). SEPA groups these exceptions as R-transactions, including rejects, returns, refunds and recalls.

| Rail | Code   | Meaning                              |
| ---- | ------ | ------------------------------------ |
| ACH  | `R01`  | Insufficient funds                   |
| ACH  | `R02`  | Account closed                       |
| ACH  | `R03`  | No account, or unable to locate it   |
| ACH  | `R10`  | Consumer says the debit was unauthorised |
| ACH  | `R29`  | Business says the debit was unauthorised |
| SEPA | `AC04` | Account closed                       |
| SEPA | `AM04` | Insufficient funds                   |
| SEPA | `MD01` | No valid mandate                     |

Return windows depend on the rail, the code and the payer type. Nacha and the European Payments Council set them in their rules, and they can change. An unauthorised claim can arrive much later than an insufficient-funds return.

A loss occurs when a platform credits a user's balance on submission, the user withdraws the money, and the debit then returns. The platform carries the loss. Hold funds according to risk, and treat bank debits as provisional until the relevant window has passed.

Record a return as a new [ledger](./Ledger.md) entry that reverses the original, and never edit or delete the original row. Handle codes differently: `R01` may justify a later retry within scheme limits, while `R10` means stop collecting and investigate. Nacha limits how a returned debit may be reinitiated.

_Usage:_

"This user's balance went negative overnight. What happened?"

"Their funding debit came back as a payment return, `R01`, after they'd withdrawn. Post a reversal and restrict the account."
