---
description: A payment reference that a customer takes to a shop or bank to pay in cash, with the merchant confirmed afterwards.
---

A cash voucher is a payment method in which a [merchant](./Merchant.md)'s checkout generates a reference or barcode, and the customer pays it in cash at a participating location such as a convenience store, bank agent or lottery kiosk. The collection network then reports the payment. Examples include boleto in Brazil, OXXO in Mexico and konbini payments in Japan. Vouchers let people without cards or bank accounts buy online. Boleto can also be paid through banking apps.

| Step | Who                | What happens                               |
| ---- | ------------------ | ------------------------------------------ |
| 1    | Customer           | Chooses the voucher method at checkout     |
| 2    | Provider           | Issues a reference with an amount and expiry |
| 3    | Customer           | Pays at a store, agent or banking app      |
| 4    | Collection network | Records the payment and notifies the provider |
| 5    | Merchant           | Receives confirmation and fulfils          |

A voucher is asynchronous. The order sits unpaid between steps 2 and 4, for hours or days, and some customers never pay. It is different from a [prepaid card](./Prepaid%20card.md), where value is loaded before the purchase and spent through a [card network](./Card%20network.md). It also has no authorization step, so a merchant cannot know at checkout whether payment will happen.

Stock is the usual problem. Reserving items for every voucher lets unpaid orders hold stock, while reserving nothing lets a customer pay for an item that has sold out. Set an expiry that fits your stock, and define what happens when a payment is reported after expiry. Provider notifications may also arrive late or more than once, so make the handler safe to run repeatedly.

Vouchers generally have no card-style [chargebacks](./Chargeback.md), but a [refund](./Refund.md) can need the customer's bank details because there is no card to credit. Forged vouchers also exist, so generate them only through your provider.

_Usage:_

"A customer paid their boleto, but the order had already been cancelled."

"The cash voucher expired before the payment was reported. Refund it or reinstate the order, and handle late payments in the state machine."
