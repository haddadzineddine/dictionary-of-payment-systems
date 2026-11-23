---
description: An option at checkout or an ATM to pay in the card's home currency, using a rate set by the merchant's provider.
---

Dynamic currency conversion, or DCC, is a service that offers a [cardholder](./Cardholder.md) the choice to pay in their card's home currency at a terminal, ATM or online checkout. The [merchant](./Merchant.md)'s provider performs the conversion and sets the rate, usually including a markup. If the customer declines, the payment proceeds in the local currency and the [card network](./Card%20network.md) or [issuer](./Issuer.md) handles the conversion.

The choice is commonly shown as a prompt such as "Pay 54.20 USD or 50.00 EUR". Choosing the home currency gives certainty about the amount, but the rate can be less favourable than the one the card would otherwise receive.

| Option                 | Who converts          | Who sets the price shown        |
| ---------------------- | --------------------- | ------------------------------- |
| Pay in local currency  | Network or issuer     | Merchant, in local currency     |
| DCC                    | Merchant's provider   | Provider, at the point of sale  |
| [Multi-currency pricing](./Multi-currency%20pricing.md) | Usually the [acquirer](./Acquirer.md)  | Merchant, in the buyer's currency |

DCC is often confused with multi-currency pricing. With multi-currency pricing the merchant sets a price in the buyer's currency in advance. With DCC the item is priced in local currency and converted at the moment of payment.

Card network rules require the cardholder to make an active choice. In the EU, Regulation (EU) 2021/1230 requires parties offering conversion at an ATM or point of sale to disclose the charges before payment as a percentage markup over the latest European Central Bank reference rate.

The typical failure is a traveller who sees a higher amount than expected on their statement and says they never agreed to the conversion. A terminal that preselects home currency, or staff who choose for the customer, can lead to complaints and [chargebacks](./Chargeback.md). Keep evidence of the customer's choice, the rate and the markup on the receipt.

_Usage:_

"A customer disputes the amount, saying we charged them in pounds without asking."

"The terminal had dynamic currency conversion on by default. Turn off preselection and check the receipt shows the markup."
