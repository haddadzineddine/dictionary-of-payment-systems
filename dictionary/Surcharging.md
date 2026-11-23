---
description: Adding a fee at checkout for paying with a particular method, which is allowed, limited or banned depending on place and network.
---

Surcharging is when a [merchant](./Merchant.md) adds a fee to the price because the customer chose a particular payment method, usually a credit card. Whether a merchant may do it depends on the jurisdiction, the [card network](./Card%20network.md)'s rules, the card type and sometimes the sector. There is no universal rule.

| Jurisdiction | Position at the time of writing                                                                                     |
| ------------ | ------------------------------------------------------------------------------------------------------------------- |
| EU           | [PSD2](./PSD2.md) bars surcharges on consumer cards under the interchange caps and on SEPA transfers and debits. Other instruments vary by member state |
| UK           | The Consumer Rights (Payment Surcharges) Regulations 2012 ban surcharges on consumer cards and some other methods. Commercial cards may be surcharged up to cost |
| US           | State laws and network rules apply, and network rules generally exclude debit and [prepaid cards](./Prepaid%20card.md)                     |
| Australia    | From 1 October 2026, Reserve Bank of Australia changes ended surcharging on designated eftpos, Mastercard and Visa cards |

Surcharging is often confused with two nearby practices. A convenience fee is charged for using a particular channel and has its own network rules. A cash discount lowers the price for non-card payment instead of raising it for card payment. Relabelling a surcharge does not necessarily change how it is classified.

A merchant may apply a blanket checkout fee and then receive a network compliance notice, a regulator complaint or a [chargeback](./Chargeback.md) for the added amount. An engineering team detects card type from the [BIN](./BIN.md) and applies a credit surcharge to a debit card, because the lookup data was stale.

Before launching, confirm the current rules for every country and network you sell in, and ask your [acquirer](./Acquirer.md) or a lawyer. Keep the fee as its own line item, so it can be refunded and reported correctly.

_Usage:_

"Can we add a 2% card fee to all checkouts?"

"Not across all markets. The EU and UK ban it on consumer cards, and US rules vary by state and network. Ask legal first."
