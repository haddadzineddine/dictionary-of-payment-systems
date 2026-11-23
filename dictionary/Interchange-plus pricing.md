---
description: A pricing model passing actual interchange and often scheme fees to the merchant, plus a disclosed acquirer markup.
---

Interchange-plus pricing is a card pricing model in which the [acquirer](./Acquirer.md) charges the [merchant](./Merchant.md) the actual [interchange fee](./Interchange%20fee.md) for each transaction plus a fixed, disclosed markup. A common variant, interchange-plus-plus or IC++, itemises the [scheme fee](./Scheme%20fee.md) as well. Providers use these labels inconsistently, so check the contract to see whether scheme fees are passed through or included in the markup.

The alternative is [blended pricing](./Blended%20pricing.md), where the merchant pays one rate and the provider absorbs the variation. With interchange-plus, the merchant carries that variation and can see what each card cost.

This example uses invented figures for two sales of 100.00 with a markup of 0.30:

| Line             | Domestic debit | Foreign commercial credit |
| ---------------- | -------------: | ------------------------: |
| Interchange      |           0.20 |                      1.80 |
| Scheme fees      |           0.05 |                      0.40 |
| Acquirer markup  |           0.30 |                      0.30 |
| **Total cost**   |       **0.55** |                  **2.50** |
| **Net received** |      **99.45** |                 **97.50** |

The markup is the same in both columns, and the total differs because of the underlying card. This transparency makes it easier to compare acquirers, since the markup is the part they control.

The drawback is unpredictability. A merchant's monthly cost can rise with no change in contract because customers used more premium or foreign cards. Statements are also longer, and fees may be reported a day or more after the sale, or billed monthly rather than netted from each [payout](./Payout.md). Engineering teams feel this during [payment reconciliation](./Payment%20reconciliation.md), because the final fee is unknown when the order is recorded. Store an estimated fee if needed, then post an adjusting [ledger](./Ledger.md) entry when the actual fee arrives, keeping both visible.

_Usage:_

"Why did our fees move when the acquirer's rate didn't change?"

"We're on interchange-plus pricing. Our markup stayed fixed, but more customers paid with foreign commercial cards."
