---
description: A report from an acquirer or provider listing transactions, fees and adjustments that make up a payout.
---

A [settlement](./Settlement.md) file is a report from an [acquirer](./Acquirer.md) or [payment service provider](./Payment%20service%20provider.md) that lists each transaction, fee and adjustment included in a [payout](./Payout.md). The bank statement usually shows one net deposit. The settlement file explains how that number was reached, so teams use it as the main input to [payment reconciliation](./Payment%20reconciliation.md).

Formats vary by provider and include CSV, fixed-width files, XML and API reports. Typical fields are:

| Field            | Purpose                                     |
| ---------------- | ------------------------------------------- |
| Batch or payout ID | Ties rows to one bank deposit             |
| [Merchant](./Merchant.md) reference | Links a row to your order or payment      |
| Provider reference | Provider's own transaction ID             |
| Type             | Sale, [refund](./Refund.md), [chargeback](./Chargeback.md), fee or adjustment |
| Gross, fee, net  | The amounts for that row                    |
| Currency         | Settlement currency, sometimes also presentment |
| Dates            | Transaction date and settlement date        |

Rows must add up to the payout. This example uses [minor units](./Minor%20unit.md):

| Row type   | Net amount |
| ---------- | ---------: |
| Sales      |      10000 |
| Fees       |       -300 |
| Refunds    |      -2000 |
| Chargeback |      -1500 |
| **Payout** |   **6200** |

A settlement file is not a transaction export from a dashboard. An export shows activity by the time it occurred, while the settlement file groups items by the payout they were paid in. A sale on Friday night may fall into Monday's file because of a cut-off, so comparing it with Friday's orders produces false mismatches.

A provider can resend a corrected file, and if its rows import twice, revenue doubles. A column changes and the parser silently reads the fee as zero. A file arrives late and the reconciliation run reports hundreds of false breaks.

Keep the raw file unchanged, and make the import idempotent using the file identifier and a stable row key. Validate that rows sum to the stated total before accepting the file, and alert when a file is missing or its schema changes.

_Usage:_

"Revenue doubled on Tuesday, but the bank balance didn't."

"The provider resent the settlement file and we imported it twice. Dedupe on the row key and rerun."
