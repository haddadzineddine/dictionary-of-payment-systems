---
description: A fee the card network charges acquirers and issuers for using its network, separate from interchange.
---

A scheme fee is a charge that a [card network](./Card%20network.md) such as Visa or Mastercard applies for use of its network. [Acquirers](./Acquirer.md) and [issuers](./Issuer.md) both pay scheme fees, and in the US they are often called assessments or network fees. An acquirer normally passes its share on to the [merchant](./Merchant.md), either as itemised lines or inside a single rate.

Scheme fees differ from an [interchange fee](./Interchange%20fee.md) in who receives the money. Interchange moves from the acquirer to the issuer. A scheme fee goes to the network. Interchange is capped in some jurisdictions, while scheme fees are set by each network and are generally not covered by those same caps.

A single payment can trigger several scheme fees:

| Fee type            | Triggered by                                                  |
| ------------------- | ------------------------------------------------------------- |
| Volume assessment   | The value of transactions processed                           |
| Authorization fee   | Each authorization request, including declined ones in some programmes |
| [Clearing](./Clearing.md) fee        | Each transaction submitted for clearing                       |
| [Cross-border fee](./Cross-border%20fee.md)    | The issuer and merchant being in different countries or regions |
| Compliance or misuse fee | Breaching a network rule, which can include repeated reattempts |

The names, amounts and triggers change, and each network publishes updates to its acquirers rather than a single public price list. For that reason, a merchant's statement can gain an unfamiliar line with no change to its contract.

The usual symptom is a set of small, oddly named charges that finance cannot explain. A retry loop can make this worse, because each repeated [authorization](./Card%20authorization.md) attempt may incur a fee even when the issuer declines it. To investigate, ask the acquirer for a per-transaction fee report, group charges by fee code, and compare the count of authorization attempts with the count of successful orders. A large gap often points to retries or [card testing](./Card%20testing.md).

_Usage:_

"What is this new network access line on the acquirer statement?"

"It's a scheme fee charged per authorization. Our retry job doubled the attempts last month, so the line doubled too."
