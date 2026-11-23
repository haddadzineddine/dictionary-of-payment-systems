---
description: A payment whose result is not known after a timeout or lost response, and which must be resolved before any retry.
---

An unknown payment outcome is the state a payment is in when the sender cannot tell whether it succeeded. It usually follows a timeout, a dropped connection, a crash after sending, or a 5xx error from a provider. The request may never have arrived, or it may have been approved with only the response lost.

This is different from a decline. A decline is a definite answer from the [issuer](./Issuer.md) that no payment was approved. A timeout is no answer at all. Treating it as a failure can cause a [double charge](./Double%20charge.md): the app shows "Payment failed", the customer pays again, and both payments succeed.

| Step | Action                                                         |
| ---- | -------------------------------------------------------------- |
| 1    | Move the payment to `unknown` and do not fulfil or fail it     |
| 2    | Query the provider's status API with your own reference        |
| 3    | If approved, continue the normal flow                          |
| 4    | If declined or never processed, mark it failed                 |
| 5    | If not found, wait and query again, as records can lag         |
| 6    | If still unresolved, follow the provider's reversal or support route |

```text
on timeout:
  payment.status = "unknown"
  result = provider.get_by_reference(payment.reference)
  if result is pending or not_found: schedule another status check
  else: apply result through the state machine
```

Generate your reference and persist it before sending the request, or you will have nothing to query after a crash. If the provider supports idempotency keys (unique values that make a repeat return the first result), a retry with the same key is safe within the provider's documented window. Do not switch to another provider until the first attempt is resolved.

Card systems also use an [authorization reversal](./Authorization%20reversal.md) to release a possibly approved authorization when the response is lost. Show the customer a neutral message such as "We're confirming your payment", and alert when items stay unknown beyond an agreed time. [Payment reconciliation](./Payment%20reconciliation.md) is the final safety net.

_Usage:_

"The gateway timed out. Should I show an error so they can try again?"

"No, it's an unknown payment outcome. Query status by our reference first, because the charge may have gone through."
