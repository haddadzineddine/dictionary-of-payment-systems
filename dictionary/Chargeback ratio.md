---
description: A merchant's disputes relative to its transactions, calculated differently by each card network for risk monitoring.
---

A chargeback ratio measures a [merchant's](./Merchant.md) disputes relative to its transactions. [Card networks](./Card%20network.md) and [acquirers](./Acquirer.md) use it to identify businesses with unusually high fraud or customer problems. There is no universal formula, so a dashboard percentage may not match a network's figure.

| Network    | Program                              | Measure                                                              |
| ---------- | ------------------------------------ | -------------------------------------------------------------------- |
| Visa       | Visa Acquirer Monitoring Program (VAMP) | Count of fraud reports plus disputes, divided by settled transactions, card-not-present only |
| Mastercard | Excessive Chargeback Program         | Chargebacks in a calendar month, divided by Mastercard transactions in the preceding month |

The differences change the result. Visa's VAMP ratio includes reported fraud, so a transaction can count even when no chargeback follows. It can also exclude some disputes resolved through pre-dispute tools and fraud that qualifies for Compelling Evidence 3.0. Mastercard divides by the previous month's transactions, so a seasonal drop in sales can raise the ratio even if the number of chargebacks stays flat.

Both programs apply thresholds and minimum counts, which differ by region and have changed recently. Visa's published fact sheet, for example, records a lower merchant threshold for several regions from April 2026. Take current figures from the network or your acquirer.

Exceeding a program's level can lead to remediation plans, fees passed on by the acquirer, a [rolling reserve](./Rolling%20reserve.md), or closure of the [merchant account](./Merchant%20account.md). Because disputes arrive weeks after a sale, the ratio lags the cause.

To manage it, compute each network's metric separately, by merchant ID, and alert on the trend rather than waiting for a notice. Address the sources: unclear [statement descriptors](./Statement%20descriptor.md), hard-to-cancel subscriptions, slow delivery, and fraud controls such as [3-D Secure](./3-D%20Secure.md). A prompt [refund](./Refund.md) before a dispute avoids a chargeback entirely.

Splitting payments or moving volume between merchant accounts to dilute the ratio can breach network rules.

_Usage:_

"Our dashboard says disputes are under one percent, so we're fine, right?"

"That's blended. Visa counts fraud reports too, so check the VAMP ratio by merchant ID."
