---
description: The share of card authorization attempts that issuers approve, which depends heavily on how attempts are counted.
---

An authorization rate, also called an approval rate, is the share of [card authorization](./Card%20authorization.md) requests that [issuers](./Issuer.md) approve. Teams use it to judge payment performance. The figure is meaningful only if everyone agrees on what is being counted.

The same traffic can yield different results. This example uses invented figures:

| Measure                | Approved | Total | Rate  |
| ---------------------- | -------: | ----: | ----: |
| All attempts           |      850 |  1000 | 85.0% |
| Unique payments, final outcome | 830 | 900 | 92.2% |

The first line counts every retry as a separate attempt. The second counts each payment once, using its final result. Neither is wrong, but comparing one provider's attempt-level figure with another's payment-level figure is misleading. Also decide how to treat zero-amount card checks, fraud blocks made before the issuer is asked, and [3-D Secure](./3-D%20Secure.md) failures.

Authorization rate differs from conversion rate, which measures how many visitors complete checkout and includes people who abandon before paying. It also differs from [capture](./Capture.md) rate, which is how many authorized payments are later captured.

A sudden fall is a common alert, and the cause is not always a provider fault. [Card testing](./Card%20testing.md) floods checkout with stolen numbers that mostly fail, pulling the rate down while real customers are unaffected. An aggressive retry job has the same effect. A real problem usually concentrates in one place, such as a single issuer, [BIN](./BIN.md) range, country or [acquirer](./Acquirer.md).

Segment the metric by network, issuer, country, card type, channel, acquirer and [decline code](./Decline%20code.md). Exclude known bot traffic into a separate view. Common improvements include sending complete data, using [network tokens](./Network%20token.md), keeping stored cards fresh with an [account updater](./Account%20updater.md), flagging stored-credential payments correctly, and using local acquiring. Benchmarks vary widely by industry and region, so compare against your own history first.

_Usage:_

"Authorization rate dropped eight points overnight. Is the acquirer down?"

"Segment it first. Declines are all from one BIN range with new cards, so it looks like card testing."
