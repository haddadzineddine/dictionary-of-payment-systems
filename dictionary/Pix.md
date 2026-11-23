---
description: Brazil's instant payment system, created and run by the Banco Central do Brasil, available around the clock.
---

Pix is Brazil's instant payment system, created and operated by the Banco Central do Brasil. It runs 24 hours a day and moves money between accounts at participating institutions within seconds. Transfers settle through the central bank's Instant Payment System, known as SPI.

| Element         | What it is                                                   |
| --------------- | ------------------------------------------------------------ |
| Pix key         | An alias such as a tax ID, phone, email or random key        |
| DICT            | The central bank's directory mapping keys to accounts        |
| Static QR       | A reusable code, often with an open amount                   |
| Dynamic QR      | A code generated per charge, with an amount and identifier   |
| Pix Automático  | Recurring collection under one prior payer authorization, live since 16 June 2025 |
| MED             | Special Return Mechanism for suspected fraud and certain failures |

Pix is a credit push: the payer's institution sends the funds. That distinguishes it from a card payment, which involves an authorization and later [settlement](./Settlement.md), and from boleto, a payment slip that clears on a slower cycle.

Pix has a dedicated fraud-return process. Under MED, the receiving institution can block funds and return them when fraud is reasonably suspected. The central bank made MED 2.0, which extends tracing of funds across accounts, mandatory from 2 February 2026. A [merchant](./Merchant.md) can therefore lose funds it believed were final. Rules continue to change, so check the current Pix regulation.

For merchants, the most common operational failure is matching. A static QR code without a usable identifier produces a credit that cannot be tied to an order. Use a dynamic QR with a unique transaction ID per order, confirm from the provider's server-side event, and never accept a customer's screenshot as proof, because it can be faked. Record any later MED return as a new [ledger](./Ledger.md) entry.

_Usage:_

"Finance has a Pix credit with no matching order."

"That came through our old static QR. Move checkout to dynamic codes so every payment carries an order ID."
