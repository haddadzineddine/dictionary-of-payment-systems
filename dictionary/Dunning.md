---
description: The process of recovering failed recurring payments through scheduled retries and customer reminders.
---

Dunning is the process of recovering a failed recurring payment through scheduled retries and messages to the customer. In subscription businesses, it mainly addresses involuntary churn, where a customer who intended to stay loses service because a payment failed.

A dunning policy combines payment actions and communication:

| Stage | Action                                                       |
| ----- | ------------------------------------------------------------ |
| 1     | Payment fails. Classify the decline and record the reason    |
| 2     | Run an [account updater](./Account%20updater.md) check if the card may have changed    |
| 3     | Notify the customer with a link to update payment details    |
| 4     | Retry [soft declines](./Soft%20decline.md) on a spaced schedule                     |
| 5     | Send further reminders and warn of service loss              |
| 6     | Restrict or cancel the subscription, and stop retrying       |

Dunning differs from a [payment retry](./Payment%20retry.md). A retry is one technical attempt, and dunning is the business process that decides when to retry, what to tell the customer, and when to give up. The retry schedule must respect the rail: a [hard decline](./Hard%20decline.md) should not be repeated, [card networks](./Card%20network.md) limit reattempts, and Nacha restricts how a returned [ACH](./ACH.md) debit can be reinitiated. Reminder content and timing may also be subject to local consumer and debt-collection rules, particularly once an amount is treated as overdue.

Dunning systems fail through missing state. A customer updates their card, but the job keeps retrying the old one and sends another warning. A customer cancels, and a scheduled retry charges them anyway, producing a complaint or a [chargeback](./Chargeback.md).

Before each step, re-read the subscription, invoice and payment method, and exit if the invoice is paid or the subscription is cancelled. When a customer adds a new card, attempt the outstanding invoice once, then end the sequence on success. Track recovered revenue and recovery rate per stage to tune the schedule.

_Usage:_

"A customer cancelled last week and we charged them again today."

"The dunning job didn't recheck the subscription before retrying. Exit the sequence on cancel and [refund](./Refund.md) that charge."
