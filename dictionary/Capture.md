---
description: The merchant's instruction to collect an authorized card payment, which sends the transaction toward clearing.
---

Capture is the [merchant's](./Merchant.md) instruction to collect funds that were approved in a [card authorization](./Card%20authorization.md). It converts "the [issuer](./Issuer.md) said yes" into "take this amount". Capture is a provider and API term. At network level, the equivalent step is the submission of a [clearing](./Clearing.md) record, which Mastercard calls first presentment.

| Stage                         | Who acts                   | Result                                 |
| ----------------------------- | -------------------------- | -------------------------------------- |
| Authorization                 | Issuer                     | Approval and [authorization hold](./Authorization%20hold.md)   |
| Capture                       | Merchant or its system     | Final amount is confirmed              |
| Clearing                      | [Acquirer](./Acquirer.md), network, issuer | Transaction record is exchanged        |
| [Settlement](./Settlement.md) | Institutions               | Funds move between them                |

A provider may capture individually or collect captures into a daily batch, so a successful capture response does not mean the money has arrived.

Merchants choose between two flows. With automatic capture, authorization and capture happen together, which suits digital goods delivered immediately. With manual capture, the merchant authorizes at checkout and captures later, which suits physical goods that ship after stock is confirmed. Card rules or local law may also restrict charging before goods are shipped, so check what applies in each market.

The main failure with manual capture is forgetting to do it. A background job crashes, the approval expires, and a shipped order has no payment behind it. Capturing late carries a second risk. Visa has a dispute condition for no authorization or late presentment, and Mastercard has an authorization-related [chargeback](./Chargeback.md) with a defined protection period, so a late capture can be charged back even if the goods were delivered. Time limits differ by network and transaction type.

Alert on authorized payments approaching their capture window, and make the capture call safe to retry so a repeated job cannot create a [double charge](./Double%20charge.md). If you need less than the approved amount, use a [partial capture](./Partial%20capture.md).

_Usage:_

"Why did we get a chargeback on an order that definitely arrived?"

"We captured it three weeks after authorizing. The approval had expired, so proof of delivery doesn't help."
