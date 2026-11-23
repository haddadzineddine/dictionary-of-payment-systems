---
description: A forced reversal of a card payment, started by the issuer through the card network after a cardholder dispute.
---

A chargeback is a forced reversal of a card payment, initiated by the [issuer](./Issuer.md) through the [card network](./Card%20network.md), usually after a [cardholder](./Cardholder.md) disputes a charge. The money is taken back from the [acquirer](./Acquirer.md), which recovers it from the [merchant](./Merchant.md). Visa's rules call this a Dispute, defined as a transaction an issuer returns to an acquirer, and Mastercard's call it a chargeback.

A chargeback differs from a [refund](./Refund.md). A merchant chooses to issue a refund. A chargeback happens regardless of what the merchant wants, generally adds a fee, and counts toward the merchant's [chargeback ratio](./Chargeback%20ratio.md).

| Stage                  | Visa term       | Mastercard term        | Who acts                 |
| ---------------------- | --------------- | ---------------------- | ------------------------ |
| Claim                  | Dispute         | First chargeback       | Issuer                   |
| Merchant's challenge   | Dispute Response, or [pre-Arbitration](./Pre-arbitration.md) | Second presentment | Acquirer, for merchant |
| Further challenge      | Pre-Arbitration, or its response | Pre-arbitration (optional) | Depends on the flow |
| Final decision         | Arbitration     | Arbitration            | The network decides      |

Visa's flow depends on the category. For fraud and authorization disputes, the acquirer's first challenge is a pre-Arbitration. For processing errors and consumer disputes, it is a Dispute Response. The general term for the merchant's challenge is [representment](./Representment.md).

Each case has a [dispute reason code](./Dispute%20reason%20code.md) that determines what evidence can win it. Time limits are strict and differ by network, reason and region, so use the dates your provider gives you and do not hard-code them.

Merchants usually discover a chargeback when a [payout](./Payout.md) arrives short, with the disputed amount and a fee deducted. The merchant can lose both the product and the money even when the sale was genuine, as with [friendly fraud](./Friendly%20fraud.md).

Do not issue a refund after a chargeback has already been raised, because the customer may be paid twice. Handle disputes as a separate state in your [ledger](./Ledger.md), because funds can leave and return weeks apart.

_Usage:_

"This payout is 240 short and I can't see why."

"There's a chargeback on an order from May. The issuer pulled the funds, so check the response deadline."
