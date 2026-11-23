---
description: The total percentage an acquirer or provider deducts from a card sale, covering interchange, scheme fees and margin.
---

The [merchant](./Merchant.md) discount rate, or MDR, is the total percentage an [acquirer](./Acquirer.md) or [payment service provider](./Payment%20service%20provider.md) deducts from a merchant's card sales. It normally covers the [interchange fee](./Interchange%20fee.md), the [scheme fee](./Scheme%20fee.md) and the acquirer's margin. Some contracts add a fixed amount per transaction, so the quoted percentage may not be the full cost.

The MDR is often mistaken for interchange. Interchange is one input, paid to the [issuer](./Issuer.md). The MDR is what the merchant sees deducted. Under [blended pricing](./Blended%20pricing.md) the MDR is one published rate. Under [interchange-plus pricing](./Interchange-plus%20pricing.md) there is no single rate in advance, but an effective MDR can be calculated after the fact.

This worked example uses invented figures to show how a sale of 100.00 divides:

| Component          | Receiver | Amount |
| ------------------ | -------- | -----: |
| Interchange        | Issuer   |   1.20 |
| Scheme fee         | Network  |   0.15 |
| Acquirer margin    | Acquirer |   0.65 |
| **Total deducted** |          |   2.00 |
| **Net to merchant** |         |  98.00 |

The effective rate is total fees divided by processed volume. Calculate it over a full statement, including fixed fees, monthly charges and [chargeback](./Chargeback.md) fees. A fixed per-transaction fee matters more on small orders: the same fixed amount is a much larger share of a 3.00 sale than of a 300.00 sale.

The failure finance teams see is a [payout](./Payout.md) lower than recorded sales, with the difference booked as an unexplained variance. Record gross, fees and net separately for each transaction so that [payment reconciliation](./Payment%20reconciliation.md) can explain the gap. When comparing provider quotes, compare effective rates on your own card mix, because a lower headline rate can cost more if other fees apply.

_Usage:_

"The provider quoted us 1.9%, but we're paying nearer 2.6%."

"That quote left out the per-transaction fee. On our small baskets, the effective merchant discount rate is much higher."
