---
description: A card payment made without the physical card at a terminal, such as online, in an app or by phone.
---

A card-not-present (CNP) transaction is a payment made without the card being read by a terminal, typically online, in an app, by phone or by mail order. Visa's rules call this a Card-Absent Environment. Because no chip takes part, the [merchant](./Merchant.md) has to rely on other signals that the person paying is the real [cardholder](./Cardholder.md).

| Property          | [Card-present](./Card-present%20transaction.md) | Card-not-present                        |
| ----------------- | ----------------------------------------------- | --------------------------------------- |
| Card verification | [EMV](./EMV.md) chip cryptogram                 | [CVV](./CVV.md), [network token](./Network%20token.md) |
| Customer check    | PIN or device, where required                   | [3-D Secure](./3-D%20Secure.md), account signals |
| Address check     | Not usually relevant                            | [Address verification](./Address%20verification.md), where supported |
| Fraud liability   | Depends on chip support                         | Often the merchant, unless authenticated |

The main risk is stolen card details. Data taken in a breach, by phishing or by skimming code on a checkout page can be used remotely without the physical card. For this reason, fraud [chargebacks](./Chargeback.md) concentrate in this channel, and network monitoring focuses on it. Visa's [chargeback ratio](./Chargeback%20ratio.md) under its Acquirer Monitoring Program, for example, is based on card-not-present activity.

Controls work best in layers, combining authentication, [velocity checks](./Velocity%20check.md), device data and [risk scoring](./Risk%20scoring.md). Applying 3-D Secure can provide a [liability shift](./Liability%20shift.md) on qualifying fraud claims.

Regulation differs by channel. Under [PSD2](./PSD2.md), remote electronic payments generally need [strong customer authentication](./Strong%20customer%20authentication.md), with dynamic linking to the amount and payee. Mail and telephone orders are treated as outside that requirement, so correctly flagging them matters. Marking ordinary web payments as telephone orders to avoid authentication misrepresents the transaction and can breach network rules.

CNP data handling also has consequences for compliance. Card entry through [hosted payment fields](./Hosted%20payment%20fields.md) can reduce [PCI DSS](./PCI%20DSS.md) scope. Phone payments can bring call recordings into scope.

_Usage:_

"Fraud is only showing up on the website, never in our stores."

"That's expected. Online is card-not-present, so there's no chip. Turn on 3DS for the risky orders."
