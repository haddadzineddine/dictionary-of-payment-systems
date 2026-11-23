---
description: Attempting a failed or uncertain payment again, with rules based on why it failed and network limits on reattempts.
---

A payment retry is another attempt at a payment that did not succeed or whose result is uncertain. Whether a retry is safe depends on the previous outcome. Retrying the wrong case produces a [double charge](./Double%20charge.md), a pointless decline or a network rule breach.

| Previous outcome              | Action                                                                  |
| ----------------------------- | ----------------------------------------------------------------------- |
| [Hard decline](./Hard%20decline.md)                  | Do not retry the same credential. Ask for another payment method        |
| [Soft decline](./Soft%20decline.md)                  | Retry later, or after the customer completes the requested step         |
| [Issuer](./Issuer.md) unavailable            | Retry with backoff, possibly through another route                      |
| Connection failed before sending | Safe to retry with the same idempotency key                          |
| Timeout or unknown            | Query status first. Retry only if the attempt did not succeed           |

An idempotency key is a unique value that lets a server recognise a repeated request. Reuse it when repeating an attempt after a lost response. A new attempt after a definite decline needs a new key, because the old key would return the old decline.

[Card networks](./Card%20network.md) restrict repeated attempts. Visa groups [decline codes](./Decline%20code.md) into categories with reattempt rules, and some codes must never be retried. Mastercard returns [merchant](./Merchant.md) advice codes, such as one telling the merchant not to try again. Limits and fees change, so get the current rules from your [acquirer](./Acquirer.md). Hammering an issuer can also lower your [authorization rate](./Authorization%20rate.md) and resemble [card testing](./Card%20testing.md).

[Dunning](./Dunning.md) is the wider recovery process for failed subscription payments, which schedules retries and contacts the customer.

The common failure comes from generic HTTP retry middleware wrapped around a payment client. It treats a 504 as retryable, sends a fresh request, and charges the customer twice. Remove automatic retries from payment-creating calls and put the decision in code that understands the provider's result. Add exponential backoff with jitter, a maximum attempt count, and a log of every attempt.

_Usage:_

"Should the job retry every declined card overnight?"

"Only the soft declines. A payment retry on a hard decline breaks network rules and won't succeed anyway."
