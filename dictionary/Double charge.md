---
description: A customer being billed twice for one purchase, usually from an unsafe retry or duplicate processing.
---

A double charge is when a customer is billed more than once for a single purchase. The usual causes are a retry after a timeout, a repeated click, two workers processing the same job, or a duplicated [capture](./Capture.md). The customer sees two entries on their statement and contacts support, or disputes one with their bank.

Not every pair of entries is a true duplicate. An [authorization hold](./Authorization%20hold.md) can appear next to the final charge for a few days, particularly when the amounts differ, such as a hotel or fuel purchase. The bank later drops the hold. Before refunding, check whether both items were captured.

| Cause                          | How it happens                                           | Prevention                                  |
| ------------------------------ | -------------------------------------------------------- | ------------------------------------------- |
| Retry after timeout            | First request succeeded, client sent a new one           | Query status, reuse the same idempotency key |
| Double click                   | Two submissions from one form                            | Disable button, enforce one intent per order |
| Concurrent workers             | Two jobs pick up the same invoice                        | Unique constraint or row lock               |
| Replayed provider event        | Handler repeats its side effect                          | Deduplicate on event ID                     |
| Failover to another provider   | Second provider charges after an unknown first outcome   | Resolve the first attempt before routing    |

An idempotency key (a unique value that lets a server recognise a repeated request) protects one provider boundary only, so a failover to a second provider needs a status check first.

To repair a real duplicate, [void](./Void.md) the second payment if it has not been captured, or [refund](./Refund.md) it if it has. Record that correction as a new [ledger](./Ledger.md) entry, leaving the original entries in place. Then find every affected customer by searching for multiple successful payments with the same order, or the same card, amount and short time window. Contact them before they raise a [chargeback](./Chargeback.md).

_Usage:_

"Support has ten tickets about a double charge since this morning."

"The new retry job generates a fresh key per attempt. Stop it, find the duplicates by order ID, and refund them."
