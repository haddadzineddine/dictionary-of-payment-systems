---
description: An issuer's request for a copy of a card transaction's details, used before or instead of raising a chargeback.
---

A retrieval request is a request from an [issuer](./Issuer.md), sent through the [acquirer](./Acquirer.md), for a copy of the records behind a card transaction. It is usually triggered when a [cardholder](./Cardholder.md) does not recognise a charge and the issuer wants more information. The request does not take money back from the [merchant](./Merchant.md).

| Step | Who      | What happens                                                |
| ---- | -------- | ----------------------------------------------------------- |
| 1    | Cardholder | Queries a charge with the issuer                          |
| 2    | Issuer   | Requests transaction information                            |
| 3    | Acquirer or provider | Passes the request to the merchant              |
| 4    | Merchant | Supplies a receipt, order details or other records          |
| 5    | Issuer   | Resolves the query, or may proceed to a [chargeback](./Chargeback.md) |

A retrieval request leaves funds in place, while a chargeback pulls them from the merchant.

Availability differs by network, and this is where older guides are often wrong. Visa announced in August 2020 that it would sunset its retrieval request process after 16 October 2020, when signature capture became optional. Mastercard's Mastercom dispute system continues to document retrieval request and fulfilment functions for its members. Because many merchants reach these systems through a [payment service provider](./Payment%20service%20provider.md), whether you ever see one depends on the provider and network.

Where the process exists, a merchant may see a dashboard notice with a short response time. Ignoring it can remove the chance to resolve an innocent misunderstanding, and the issuer may go on to raise a dispute. Answer with clear records: the order date, amount, customer details, delivery confirmation and the exact [statement descriptor](./Statement%20descriptor.md).

Do not include a full [PAN](./PAN.md) or [CVV](./CVV.md) in the documents you upload. Mask card numbers and follow [PCI DSS](./PCI%20DSS.md) when storing or transmitting receipts.

Repeated requests from customers who do not recognise a charge usually point to a descriptor problem.

_Usage:_

"The provider sent a retrieval request on a Mastercard sale. Is that a chargeback?"

"Not yet. No money has moved. Send the receipt and delivery proof so it doesn't become one."
