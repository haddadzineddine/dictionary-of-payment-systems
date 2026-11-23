---
description: The merchant's challenge to a chargeback, submitted through the acquirer with evidence that the charge was valid.
---

Representment is the process of contesting a [chargeback](./Chargeback.md) by resubmitting the transaction with evidence that the charge was valid. The [merchant](./Merchant.md) prepares the case, and the [acquirer](./Acquirer.md) presents it to the [issuer](./Issuer.md) through the [card network](./Card%20network.md). The word is industry shorthand, and each network uses its own terms.

| Network    | Dispute type                              | Merchant's first challenge is called |
| ---------- | ----------------------------------------- | ------------------------------------ |
| Visa       | Fraud and authorization (categories 10, 11) | [Pre-Arbitration](./Pre-arbitration.md) |
| Visa       | Processing errors and consumer (12, 13)   | Dispute Response                     |
| Mastercard | Chargebacks generally                     | Second presentment                   |

The evidence must answer the specific [dispute reason code](./Dispute%20reason%20code.md). A merchant facing a fraud claim submits a delivery receipt, but delivery alone does not show who placed the order. A merchant facing "not as described" sends proof of payment, which does not address the quality complaint.

| Claim                          | Useful evidence                                                |
| ------------------------------ | -------------------------------------------------------------- |
| Fraud, card-not-present        | [3-D Secure](./3-D%20Secure.md) result, Visa Compelling Evidence if eligible |
| Goods not received             | Carrier tracking to the [cardholder](./Cardholder.md)'s address                   |
| Not as described               | Product description, correspondence, return policy             |
| Credit not processed           | [Refund](./Refund.md) details and [acquirer reference number](./Acquirer%20reference%20number.md) |
| Cancelled recurring            | Terms shown, consent, cancellation records                     |
| Authorization-related          | Valid approval and timely [capture](./Capture.md)              |

Some disputes cannot be won with evidence of delivery. Visa's merchant guidance says that for authorization disputes, proof that the customer received the goods generally does not override a missing, expired or incorrectly used authorization.

Representment takes staff time and can add fees if it escalates, so accept disputes the merchant would lose. Winning returns the funds, though the original dispute may still count toward the [chargeback ratio](./Chargeback%20ratio.md) depending on the network's method.

Deadlines are strict and set by network rules. A late response usually loses automatically, so route dispute notifications to a monitored queue, and rely on the due date your provider supplies.

_Usage:_

"We sent the tracking number, and we still lost the fraud dispute."

"Tracking shows delivery, not who bought it. For representment we needed the 3DS result or device history."
