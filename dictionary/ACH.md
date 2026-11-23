---
description: The US batch bank-to-bank network for credits and debits, governed by Nacha rules and operated by FedACH and EPN.
---

ACH, the Automated Clearing House network, is the US system for moving batched electronic credits and debits between bank accounts. Nacha writes the operating rules. Two operators process the entries: the Federal Reserve's FedACH and The Clearing House's Electronic Payments Network. Payroll and bill payments commonly use it.

| Step | Who                              | What happens                                      |
| ---- | -------------------------------- | ------------------------------------------------- |
| 1    | Originator (business)            | Gets authorization and creates an entry           |
| 2    | ODFI (originating bank)          | Submits batched entries to an operator            |
| 3    | ACH operator                     | Sorts entries and delivers them to receiving banks |
| 4    | RDFI (receiving bank)            | Posts the credit or debit to the receiver's account |
| 5    | RDFI                             | Sends a return if the entry cannot be honoured    |

An ACH credit pushes money to a receiver. An ACH debit pulls money from a payer under an authorization, which is why debits carry more risk for the business collecting them. Same Day ACH offers faster processing within windows and per-payment limits set by Nacha, but it remains batched. It is not the same as an instant rail such as [FedNow](./FedNow.md) or the [RTP network](./RTP%20network.md).

ACH is often confused with a wire. A [Fedwire](./Fedwire.md) payment settles individually and is final. An ACH debit can settle and still come back later as a [payment return](./Payment%20return.md), for reasons such as insufficient funds or a claim that it was unauthorised.

The failure this causes is familiar to anyone shipping goods on ACH. The dashboard shows "paid", the order ships, and days later a return such as `R01` reverses the money. Treat a debit as provisional until your risk window has passed, and record the return as a new [ledger](./Ledger.md) entry. Nacha also added fraud-monitoring duties that took effect in phases during 2026, so confirm current obligations with your bank.

_Usage:_

"The customer's payment cleared Monday, so why did we lose the money today?"

"It was an ACH debit and came back `R01`. Settled doesn't mean final, so hold high-value orders longer."
