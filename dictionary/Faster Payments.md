---
description: The UK's always-on retail bank transfer system, operated by Pay.UK and settled net at the Bank of England.
---

Faster Payments is the UK's system for near-real-time bank transfers in sterling, operated by Pay.UK. It runs 24 hours a day and carries everyday transfers, bill payments and many [payouts](./Payout.md). A customer usually sees the money arrive within seconds, although banks can hold a payment for fraud checks.

| Step | Who                  | What happens                                 |
| ---- | -------------------- | -------------------------------------------- |
| 1    | Payer                | Enters the sort code, account number and reference |
| 2    | Sending bank         | Checks the payment and submits it            |
| 3    | Faster Payments      | Routes it to the receiving bank              |
| 4    | Receiving bank       | Accepts it and credits the payee             |
| 5    | Bank of England      | Settles net positions in cycles              |

The customer experience is immediate, but interbank [settlement](./Settlement.md) is not. According to the Bank of England, Faster Payments settles on a deferred net basis three times each business day in its [RTGS](./RTGS.md) service, with direct participants prefunding their maximum exposure. It should not be confused with CHAPS, the UK's high-value system, which settles each payment gross. Bacs is a third, batch-based UK system and is the one used for UK direct debits.

Pay.UK's New Payments Architecture is intended to replace Faster Payments and use [ISO 20022](./ISO%2020022.md). Its timing has moved before, so check Pay.UK's current plans.

A common failure is authorised push payment fraud, where a criminal persuades a customer to send money. The customer approved it, so the transfer completes. Since 7 October 2024, Payment Systems Regulator rules have required in-scope payment firms to reimburse victims, subject to conditions and a maximum amount that can be revised. A missing reference is a separate problem, because it leaves a received payment unmatched. Give each customer a unique reference, and use Confirmation of Payee, the UK name-checking service, before paying new accounts.

_Usage:_

"The customer says they paid by bank transfer, but the order is still open."

"The Faster Payment landed without our reference. Match it manually and show the reference more clearly at checkout."
