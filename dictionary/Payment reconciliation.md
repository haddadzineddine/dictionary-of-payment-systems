---
description: Comparing internal payment records with provider and bank records to find and resolve differences.
---

Payment reconciliation is the process of comparing your own payment records with external records, such as provider reports, a [settlement file](./Settlement%20file.md) and bank statements, and resolving every difference. Internal systems can show that a payment succeeded when it did not, or miss one that did. Reconciliation is how a business finds out.

A full reconciliation usually has three layers:

| Layer | Compares                           | Finds                                 |
| ----- | ---------------------------------- | ------------------------------------- |
| 1     | Internal [ledger](./Ledger.md) and provider report | Missing or mismatched transactions   |
| 2     | Provider report and [payout](./Payout.md) total   | Fees, [refunds](./Refund.md) and [chargebacks](./Chargeback.md) netted out |
| 3     | Payout total and bank statement    | Payouts that did not arrive          |

An item that does not match is called a break:

| Break                 | Likely cause                         | Action                                  |
| --------------------- | ------------------------------------ | --------------------------------------- |
| Provider has it, you don't | Lost response or event          | Create the record from provider data    |
| You have it, provider doesn't | Failed call marked successful | Correct status, check fulfilment        |
| Amount differs        | Fee, [partial capture](./Partial%20capture.md), currency       | Post an adjustment                      |
| Timing difference     | Cut-off or time zone                 | Expect it to clear in the next run      |

The familiar symptom is a payout that does not equal the day's orders. The payout is net of fees, refunds and disputes, and it may span several days under the provider's cut-off. Comparing it directly with a daily sales total will always produce noise.

Match on a stable identifier that you send to the provider and receive back in its reports, and store the provider's own ID too. Run reconciliation automatically every day and track each break's age, because a timing difference clears within days while a real error does not. Fix breaks by posting a new correcting ledger entry, never by editing history. An [unknown payment outcome](./Unknown%20payment%20outcome.md) that was never resolved will often first show up here.

_Usage:_

"The provider's report shows 14 payments that aren't in our database."

"Those are payment reconciliation breaks from the event outage. Backfill them from provider data and check they were fulfilled."
