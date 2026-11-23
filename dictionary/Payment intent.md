---
description: A record of what a customer intends to pay, which tracks one or more attempts until the payment reaches a final state.
---

A payment intent is a record that represents one thing a customer intends to pay for, including the amount, currency and current status. It stays the same while the attempts to fulfil it change. Stripe uses the name PaymentIntent. Other providers call a similar object an order, session or payment, and many teams build their own.

The important split is between the intent and its attempts. A customer may try one card, get a decline, and succeed with another. That is one intent with two attempts.

```json
{
  "id": "pi_123",
  "order_id": "ord_987",
  "amount": 4999,
  "currency": "EUR",
  "status": "requires_payment_method",
  "attempts": [{ "id": "att_1", "outcome": "declined" }]
}
```

| Concept  | Question it answers             | Cardinality            |
| -------- | ------------------------------- | ---------------------- |
| Order    | What is being bought?           | One order              |
| Intent   | What needs to be paid?          | Usually one per order  |
| Attempt  | What happened this time?        | Many per intent        |

The amount is stored as an integer in the currency's [minor unit](./Minor%20unit.md), so 4999 in EUR means 49.99.

Without this object, a system often models each click as a new payment. The failure is familiar: a customer's card is declined, they reload the page and try again, the earlier request also completes, and they suffer a [double charge](./Double%20charge.md) because two independent payments exist. With an intent, every attempt attaches to one record, and the system can refuse a new attempt once one has succeeded.

Enforce one active intent per order with a unique database constraint. Reuse the existing intent when the checkout page reloads, and send a provider idempotency key (a unique value that lets a server recognise a repeated request) for each attempt. Drive its status through a [payment state machine](./Payment%20state%20machine.md) rather than free updates. If the amount changes, update the intent only while no attempt is in progress.

_Usage:_

"Refreshing checkout creates a new payment each time."

"Look up the existing payment intent by order ID and reuse it. Only attempts should multiply."
