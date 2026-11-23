---
description: A payment started by scanning a QR code, which carries payment data while a separate rail moves the money.
---

A QR code payment is a payment started by scanning a two-dimensional code that carries payment information. The QR code is only a way to pass data between devices. The money moves on a separate rail, such as [UPI](./UPI.md), [Pix](./Pix.md), a [card network](./Card%20network.md) or a [digital wallet](./Digital%20wallet.md)'s own system. Two transactions that look identical at the till can therefore have different fees, finality and dispute rights.

EMVCo, the card industry's technical standards body, publishes QR specifications for two modes:

| Mode                | Who shows the code | Who scans | Typical use                |
| ------------------- | ------------------ | --------- | -------------------------- |
| Merchant-presented  | Merchant           | Customer  | Stickers, screens, invoices |
| Consumer-presented  | Customer's app     | Merchant  | Retail tills with scanners |

Merchant-presented codes can be static or dynamic. A static code is printed once and normally identifies only the payee, so the customer types in the amount. A dynamic code is generated for one payment and includes the amount and a reference, which makes automatic matching possible. National systems define their own formats, many of them based on the EMVCo specification.

QR payment is often confused with contactless card payment. A tap uses NFC, a short-range radio link, and [EMV](./EMV.md) card technology. A QR payment uses a camera and usually an app, and needs no card terminal in merchant-presented mode.

Static codes create two recognisable failures. A fraudster places a sticker with their own code over the merchant's, and customers pay the wrong account while believing the payment succeeded. A shop assistant accepts a customer's success screen, which can be faked or may show a payment that later failed.

Use dynamic codes where possible, and check displayed codes regularly if you use static ones. Release goods only when your own terminal, app or provider confirms the credit.

_Usage:_

"Three customers say they paid, but nothing reached our account."

"Someone put a fake sticker over the QR code at the till. Replace it and switch to dynamic codes."
