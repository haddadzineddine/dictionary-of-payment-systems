---
description: The dispute stage after a challenged chargeback, giving both sides a last chance to settle before network arbitration.
---

Pre-arbitration is the stage of a card dispute that follows an initial challenge, giving the [issuer](./Issuer.md) and [acquirer](./Acquirer.md) a final chance to resolve the case before the [card network](./Card%20network.md) is asked to decide it. Who acts at this stage depends on the network and the type of dispute.

Visa's rules use two flows.

| Stage                    | Fraud and authorization (categories 10, 11) | Processing and consumer (12, 13) |
| ------------------------ | ------------------------------------------- | -------------------------------- |
| [Chargeback](./Chargeback.md) | Issuer raises a Dispute                | Issuer raises a Dispute          |
| Dispute Response         | Not a stage in this flow                    | Acquirer responds                |
| Pre-Arbitration          | Acquirer challenges                         | Issuer challenges                |
| Pre-Arbitration Response | Issuer accepts or rejects                   | Acquirer accepts or rejects      |
| Arbitration              | Acquirer may file                           | Issuer may file                  |

So in a Visa fraud dispute, pre-arbitration is the [merchant's](./Merchant.md) first challenge. In a consumer dispute, it is the issuer's reply to the merchant's evidence.

Mastercard works differently. After a chargeback and second presentment, the issuer may file an optional pre-arbitration case, and its Chargeback Guide says Mastercard strongly recommends skipping that step and going directly to an arbitration case.

In pre-arbitration, the two sides can still settle. In arbitration, the network reviews the case and issues a decision, and the losing side generally bears additional fees. Those fees can exceed the value of a small transaction.

For a merchant, this stage usually appears as a notice from the provider that a dispute it thought was finished has come back. Check whether new evidence addresses the objection, compare the transaction amount with the possible fees, and accept liability if the case is weak.

Time limits at this stage are short and differ by flow, so take them from your [payment service provider](./Payment%20service%20provider.md). Model each stage as a separate state, because a [representment](./Representment.md) win can be reopened.

_Usage:_

"We won that dispute last month. Why is it back?"

"The issuer went to pre-arbitration. It's a 30-euro order, so accept it unless we have new evidence."
