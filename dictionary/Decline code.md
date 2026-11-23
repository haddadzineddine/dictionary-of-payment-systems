---
description: The response code returned when a card authorization is refused, indicating the reason and whether a retry makes sense.
---

A decline code is the value returned when a [card authorization](./Card%20authorization.md) is refused. It usually originates from the [issuer](./Issuer.md) in the response code field of an [ISO 8583](./ISO%208583.md) message, though a network, [acquirer](./Acquirer.md) or fraud tool can also generate one. Examples include `51` for insufficient funds and `05` for "do not honor".

Meanings are not identical across networks, and [payment service providers](./Payment%20service%20provider.md) often translate raw codes into their own labels. Keep the original code as well.

Visa's rules group decline codes into four categories that control retry behaviour.

| Visa category                | Example codes                            | [Merchant](./Merchant.md) response                      |
| ---------------------------- | ---------------------------------------- | -------------------------------------- |
| 1. Issuer will never approve | `04`, `41` lost, `43` stolen, `46` closed | Do not retry this card                 |
| 2. Cannot approve at this time | `51` funds, `61` limit, `91` issuer down | Retry within Visa's limits             |
| 3. Data quality              | `54` expired, `82` failed card check     | Correct the data, then retry           |
| 4. Generic                   | All other codes                          | Retry within limits, or ask for another card |

These categories are Visa's. Mastercard signals retry guidance differently, including through merchant advice codes in its responses. Reattempt limits are set by each network and can change, so take them from current rules or your provider.

The practical distinction is between a [soft decline](./Soft%20decline.md), which may succeed after a change, and a [hard decline](./Hard%20decline.md), which will not. A retry job that treats all failures the same will keep charging lost or closed cards, adding cost and possibly breaching network limits. This is a common defect in [recurring billing](./Recurring%20billing.md) and [dunning](./Dunning.md).

Be careful with customer messages. Showing "suspected fraud" or "stolen card" can alert a criminal and embarrass a real customer. Say the payment was declined and suggest another method. A jump in one code can indicate an integration problem or [card testing](./Card%20testing.md).

_Usage:_

"The billing job retried this card eleven times last week."

"It's a code 46, closed account. That's category 1 for Visa, so we should never have retried it."
