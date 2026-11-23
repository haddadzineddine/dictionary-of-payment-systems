---
description: The transfer of net funds between issuers, acquirers and the card network after clearing has set the amounts owed.
---

Settlement is the movement of money between financial institutions after [clearing](./Clearing.md) has established what each one owes. In a card payment, the [issuer](./Issuer.md) pays, usually on a net basis, through the [card network's](./Card%20network.md) settlement arrangements, and the [acquirer](./Acquirer.md) receives funds. Visa's rules define settlement as the reporting and funds transfer of amounts owed by one member to another, or to Visa, as a result of clearing.

Networks usually settle net positions rather than each individual card payment. An acquirer may be owed for millions of purchases and owe for [refunds](./Refund.md) and [chargebacks](./Chargeback.md), so one net amount moves in a settlement currency.

| Stage                         | Parties                        | What moves                     |
| ----------------------------- | ------------------------------ | ------------------------------ |
| [Card authorization](./Card%20authorization.md) | [Merchant](./Merchant.md) to issuer | A message and a hold           |
| Clearing                      | Acquirer, network, issuer      | Transaction records            |
| Settlement                    | Issuer, network, acquirer      | Net funds between institutions |
| [Payout](./Payout.md)         | Acquirer or provider to merchant | Funds to a business bank account |

The word causes a specific misunderstanding. A provider dashboard may show a payment as "settled" while the merchant's bank has received nothing. That status can mean the transaction was submitted, that the provider has received funds, or that the payment is in the next payout. Each provider defines it differently, so read the documentation rather than assuming that settled means deposited.

Settlement timing depends on the network, currency, business days and bank holidays. A [payment service provider](./Payment%20service%20provider.md) may add its own payout delay.

Engineers usually meet settlement through a [settlement file](./Settlement%20file.md) or report. It often lists amounts grouped by batch and net of fees, in the settlement currency, which may differ from the customer's currency. Matching those records to orders requires shared identifiers, and it is the purpose of [payment reconciliation](./Payment%20reconciliation.md). Track settlement in your [ledger](./Ledger.md) as a separate event from [capture](./Capture.md) so finance can see money in transit.

_Usage:_

"The dashboard says Friday's sales settled. Why isn't the money in the bank?"

"Settled just means the acquirer has it. The payout runs on Tuesday."
