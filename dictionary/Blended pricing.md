---
description: A card pricing model charging one rate across card types, with the provider absorbing variation in underlying costs.
---

Blended pricing is a card pricing model in which a [merchant](./Merchant.md) pays one published rate, or a small set of rates, regardless of the underlying card. A provider might quote one percentage plus a fixed fee for every online card payment. The provider pays the actual [interchange fee](./Interchange%20fee.md) and [scheme fee](./Scheme%20fee.md) from that amount and keeps the difference.

The provider's margin therefore changes from one transaction to the next. It earns more on a low-cost domestic debit card and less, or even loses money, on an expensive foreign commercial card. Providers set the rate using an expected card mix, and may reprice or add surcharges for categories such as international cards.

| Model              | Merchant pays                     | Predictability | Cost visibility |
| ------------------ | --------------------------------- | -------------- | --------------- |
| Blended            | One rate                          | High           | Low             |
| Tiered             | A rate per provider-defined bucket | Medium        | Low             |
| [Interchange-plus pricing](./Interchange-plus%20pricing.md) | Actual cost plus a markup   | Lower          | High            |

Tiered pricing, sometimes described as qualified, mid-qualified and non-qualified rates, is a related model. The provider decides which transactions fall into each tier, so the rate paid can be hard to predict or audit.

Blended pricing suits merchants that value a simple bill and have modest volume. The usual problem appears as a business grows. A merchant whose customers mostly use domestic debit cards may pay well above the underlying cost, and nothing on the statement reveals it because the components are hidden. To check, ask for a sample of transaction-level costs or request an interchange-plus quote, then compare both against the last few months of your real card mix. Include fixed fees, since they can outweigh a small percentage difference on low-value orders.

_Usage:_

"Our provider charges one flat rate. Is that good for us?"

"It's blended pricing, and most of our volume is domestic debit. We're probably overpaying, so let's get an interchange-plus quote."
