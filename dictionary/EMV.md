---
description: Technical specifications managed by EMVCo for chip and contactless card payments, and for related payment technologies.
---

EMV is a family of technical specifications for secure card payments, best known for chip cards and contactless payments. The name comes from Europay, Mastercard and Visa. The specifications are managed by EMVCo, a technical body collectively owned by American Express, Discover, JCB, Mastercard, UnionPay and Visa.

A chip card differs from a magnetic stripe in how it proves itself. A stripe holds static data that can be copied. A chip holds secret keys and generates a cryptogram, a one-time code computed over the transaction's details, which the [issuer](./Issuer.md) can verify.

| Step | Who      | What happens                                                    |
| ---- | -------- | --------------------------------------------------------------- |
| 1    | Terminal | Reads the card and sends transaction details to the chip        |
| 2    | Card     | Generates a cryptogram for this transaction                     |
| 3    | Terminal | Sends it in the [card authorization](./Card%20authorization.md) request            |
| 4    | Issuer   | Recalculates the cryptogram and approves or declines            |
| 5    | Card     | Can verify the issuer's response and complete the transaction   |

Because each cryptogram is tied to one transaction, data captured from a chip payment cannot be replayed to make a counterfeit card work. This is the protection chip adds in a [card-present transaction](./Card-present%20transaction.md).

EMV does not protect a [card-not-present transaction](./Card-not-present%20transaction.md), because no chip takes part. For that channel, EMVCo publishes separate specifications for [3-D Secure](./3-D%20Secure.md) and for payment tokens, which are used in [network tokens](./Network%20token.md). The shared name causes confusion: "EMV 3DS" is an online authentication protocol and has no chip involved.

EMVCo does not set network rules or enforce adoption. Each [card network](./Card%20network.md) decides those separately, including the chip [liability shift](./Liability%20shift.md). Where it applies, a [merchant](./Merchant.md) that swipes a chip card on a terminal that cannot read chips can be liable for resulting counterfeit fraud.

_Usage:_

"The new terminal keeps failing on chip, so staff are just swiping."

"Stop that. If those turn out to be counterfeit, the liability can land on us. Get the reader replaced."
