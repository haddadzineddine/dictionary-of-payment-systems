---
description: A chargeback on a genuine purchase, raised by mistake or dishonestly by the cardholder or someone they know.
---

Friendly fraud is a [chargeback](./Chargeback.md) raised on a genuine purchase, where the [cardholder](./Cardholder.md) or someone connected to them received the goods or service. The name is misleading because many cases are not deliberate. Visa uses the more neutral term first-party misuse for cardholders reporting fraud on transactions they actually made.

| Cause                   | Example                                                  | Deliberate? |
| ----------------------- | -------------------------------------------------------- | ----------- |
| Unrecognised charge     | Unclear [statement descriptor](./Statement%20descriptor.md) | No       |
| Family use              | A child buys in-game currency on a parent's card         | Usually no  |
| Forgotten subscription  | Renewal the customer forgot about                        | Usually no  |
| [Refund](./Refund.md) shortcut | Customer calls the bank instead of the [merchant](./Merchant.md) | Mixed |
| Buyer's remorse         | Customer keeps the item and claims fraud                 | Yes         |

It differs from true third-party fraud, where a stranger used stolen card details. The two look identical to the merchant at first because both typically arrive under a fraud [dispute reason code](./Dispute%20reason%20code.md). Do not assume dishonesty.

Use a descriptor customers recognise, send clear receipts, remind customers before a renewal, make cancelling easy, and offer a visible refund route so that contacting support is easier than calling the bank.

When a dispute arrives, the merchant can contest it through [representment](./Representment.md) with evidence that the cardholder took part. Visa's Compelling Evidence 3.0, under Dispute Condition 10.4, lets a merchant use matching data from earlier undisputed transactions on the same card, such as IP address or device ID, when specific conditions are met. Those conditions change, so check the current Visa rules. Mastercard has its own evidence requirements for its fraud-related chargebacks.

To be usable, the evidence must be collected at purchase time. Log device, IP, account and delivery data against each order, within applicable privacy law. Each dispute also adds to the merchant's [chargeback ratio](./Chargeback%20ratio.md).

_Usage:_

"He says he never bought it, but he's played the game on that account for two years."

"Looks like friendly fraud. Pull the device and IP history and see whether it qualifies for CE 3.0."
