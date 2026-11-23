---
description: A card payment where the card and cardholder are physically at the terminal, typically by chip or contactless.
---

A card-present transaction is a payment in which the card and [cardholder](./Cardholder.md) are physically at the point of sale. Visa's rules call this a Card-Present Environment, and define it by both being present at the [merchant's](./Merchant.md) premises or a similar acceptance point.

| Entry method           | How data is captured              | Fraud protection                       |
| ---------------------- | --------------------------------- | -------------------------------------- |
| Chip                   | Card generates a cryptogram       | Strong against counterfeit cards       |
| Contactless card       | Card generates a cryptogram       | Strong against counterfeit cards       |
| Mobile wallet tap      | Device presents a [network token](./Network%20token.md) | Token and device authentication |
| Magnetic stripe        | Static data read from the stripe  | Weak, data can be copied               |
| Key-entered at terminal | Staff type the number            | Weak, may lose card-present treatment  |

The contrast is with a [card-not-present transaction](./Card-not-present%20transaction.md), where no terminal reads the card. Because an [EMV](./EMV.md) chip proves the card is genuine, card-present payments generally carry lower fraud risk, and pricing often reflects that.

The classification comes from data in the [card authorization](./Card%20authorization.md) message, such as point-of-sale entry mode. It is not inferred from where the merchant is. A card number keyed in after a chip failure may cost more and give the merchant weaker evidence in a dispute. If a chip card is swiped or keyed where the [liability shift](./Liability%20shift.md) applies, the merchant can be liable for counterfeit fraud.

Physical presence does not rule out all fraud. A lost or stolen card can be used in person, particularly for low-value contactless payments that do not ask for a PIN. Under EU rules, the contactless [SCA exemption](./SCA%20exemption.md) has cumulative limits, so a terminal may occasionally ask a customer to insert the card and enter a PIN.

_Usage:_

"The terminal asked her for a PIN on a tiny coffee payment. Is it broken?"

"No. She hit the contactless limit on that card, so the issuer wants a chip and PIN."
