---
description: A fee the acquirer pays the issuer on most card payments, set by network schedules and capped by regulators in some regions.
---

An interchange fee is a fee the [acquirer](./Acquirer.md), the [merchant](./Merchant.md)'s bank, pays to the [issuer](./Issuer.md), the [cardholder](./Cardholder.md)'s bank, on most card purchases in a [four-party model](./Four-party%20model.md). The [card network](./Card%20network.md) publishes the rates. They vary by card type, region, merchant category, sales channel and the data sent with the transaction. The merchant does not pay the issuer directly. The acquirer recovers the cost through the merchant's pricing.

Interchange is often confused with the total cost of accepting a card. It is one component. A [scheme fee](./Scheme%20fee.md) goes to the network, the acquirer adds its own margin, and the [merchant discount rate](./Merchant%20discount%20rate.md) expresses the combined charge.

Regulators cap interchange in some markets, and the rules differ:

| Region    | Rule                                                               | Current point to check                                                     |
| --------- | ------------------------------------------------------------------ | -------------------------------------------------------------------------- |
| EU        | Regulation (EU) 2015/751 caps most consumer debit and credit cards | Commercial cards and three-party schemes generally fall outside the caps   |
| UK        | Onshored version of the EU caps                                    | The Payment Systems Regulator is working on a UK-EEA cross-border cap      |
| US        | Regulation II caps debit interchange for large issuers             | An October 2026 Eighth Circuit ruling upheld vacating the cap, effective only once the court's mandate issues |
| Australia | Reserve Bank of Australia standards                                | Lower domestic caps began on 1 October 2026                                |

A merchant usually notices interchange when monthly card costs rise while prices and sales stay flat. A larger share of premium, commercial or foreign cards can cause this. Missing transaction data can also push a payment into a more expensive category, which acquirers call a downgrade. Whether interchange comes back on a [refund](./Refund.md) depends on the network and the acquirer contract, so check it instead of assuming.

_Usage:_

"Card costs went up this month, but revenue is flat."

"More volume came from commercial and foreign cards, and interchange is higher on both. Pull the fee report by card type."
