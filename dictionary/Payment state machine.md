---
description: A model defining a payment's allowed states and transitions, so that late or duplicate events cannot corrupt its status.
---

A payment state machine is a model that lists every status a payment can have and the transitions allowed between them. Payment events arrive from customers, providers and scheduled jobs, often late, duplicated or out of order. The state machine decides whether each event may change the record.

| From       | Event                | To         |
| ---------- | -------------------- | ---------- |
| `created`  | Authorization approved | `authorized` |
| `created`  | Declined             | `failed`   |
| `created`  | Timeout              | `unknown`  |
| `unknown`  | Status query: approved | `authorized` |
| `unknown`  | Status query: not processed | `failed` |
| `authorized` | [Capture](./Capture.md) confirmed  | `captured` |
| `authorized` | [Void](./Void.md) confirmed     | `voided`   |
| `captured` | Funds settled        | `settled`  |
| `settled`  | [Refund](./Refund.md) confirmed     | `refunded` |

Real systems add partial states, such as partially captured or partially refunded, and a [chargeback](./Chargeback.md) path. The separate `unknown` state matters because a timeout is not a failure. It holds the payment until a status query resolves an [unknown payment outcome](./Unknown%20payment%20outcome.md).

A status column without these rules is the usual starting point, and it fails under concurrency. A `failed` event from an earlier attempt arrives after `captured` and overwrites it, so support sees a failed payment that the customer has paid for. Or a provider resends an event, and the fulfilment code ships twice.

Apply transitions atomically with a conditional update, so that only one writer can win:

```sql
UPDATE payments
SET status = 'captured', version = version + 1
WHERE id = $1 AND status = 'authorized';
```

If zero rows change, read the current state. A repeat of the same event is a harmless no-op, so acknowledge it. An impossible transition should be logged and alerted, not forced. Keep an append-only history of every event, because the current status alone cannot explain how the payment got there. Side effects such as shipping should run once per transition.

_Usage:_

"A late failure event flipped a captured payment back to failed."

"The handler writes whatever status it receives. Put it behind the payment state machine and reject that transition."
