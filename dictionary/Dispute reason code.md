---
description: A network code stating why a card payment was disputed, which determines the evidence needed to respond.
---

A dispute reason code is the value a [card network](./Card%20network.md) attaches to a [chargeback](./Chargeback.md) to state why the payment is being disputed. It tells the [merchant](./Merchant.md) which rules apply and what evidence can answer the claim. Code sets are network-specific, so the same complaint can carry different labels.

Visa organises its codes as dispute conditions within four categories. Mastercard uses message reason codes.

| Type of claim   | Visa                                                  | Mastercard example                     |
| --------------- | ----------------------------------------------------- | -------------------------------------- |
| Fraud           | Category 10, such as 10.4 Other Fraud, Card-Absent    | 4837 No Cardholder Authorization       |
| Chip liability  | 10.1 and 10.2, [EMV](./EMV.md) [liability shift](./Liability%20shift.md)                 | 4870 Chip Liability Shift              |
| Authorization   | Category 11, such as 11.3 No Authorization/Late Presentment | 4808 Authorization-related       |
| Processing error | Category 12, such as 12.6 Duplicate Processing       | 4834 Point-of-Interaction Error        |
| Consumer        | Category 13, such as 13.1 Not Received                | 4853 Cardholder Dispute                |

Examples are from Visa's October 2026 rules and Mastercard's May 2025 guide, and can change.

A reason code is different from a [decline code](./Decline%20code.md). A decline code explains why an authorization was refused at the time of payment. A reason code explains why a completed payment is being challenged afterward.

The code decides the strategy for [representment](./Representment.md). A 13.1 "not received" claim can often be answered with carrier tracking. The same tracking does little against a 10.4 fraud claim, where the question is who made the purchase.

A customer who forgot a subscription may still be recorded under a fraud code, a common sign of [friendly fraud](./Friendly%20fraud.md).

[Payment service providers](./Payment%20service%20provider.md) often map raw codes to simplified categories such as "fraudulent" or "product not received". Store the raw code and network too. Reporting by code also shows where to fix the source: rising 13.1 points to fulfilment, and rising 12.6 points to a [double charge](./Double%20charge.md) bug.

_Usage:_

"Should I send the delivery proof for this dispute?"

"Check the reason code first. It's a 10.4, so we need evidence of who bought it, not just where it went."
