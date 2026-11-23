---
description: Card details saved with the cardholder's consent for later payments, flagged under card network rules.
---

A stored credential is a card number or token that a [merchant](./Merchant.md) or its provider saves, with the [cardholder](./Cardholder.md)'s consent, to use for future payments. Visa and Mastercard define frameworks for these transactions. Under them, the first payment establishes the agreement, and later payments are flagged to show that the credential was stored and how it is being used.

| Stage                     | Who starts it | What must happen                                     |
| ------------------------- | ------------- | ---------------------------------------------------- |
| Consent                   | Cardholder    | Agrees to storage and the terms of future use        |
| Initial transaction       | Cardholder    | Authenticated where required, flagged as first storage |
| Later customer payment    | Cardholder    | Sent as a [customer-initiated transaction](./Customer-initiated%20transaction.md)             |
| Later merchant payment    | Merchant      | Sent as a [merchant-initiated transaction](./Merchant-initiated%20transaction.md) with the original reference |

The original reference is usually the [network transaction ID](./Network%20transaction%20ID.md) returned by the first authorization. Keep it with the saved credential, because later merchant-initiated payments must reference it.

Stored credentials are often confused with [tokenization](./Tokenization.md). Tokenization is how the card number is protected, by replacing it with a substitute value. A stored credential describes the business arrangement and its transaction flags. Saving a token does not by itself create the consent or the correct flags.

The failure is often silent. A team saves cards and charges them later as if each were a normal online payment, with no stored-credential flag and no original ID. [Issuers](./Issuer.md) see an unexpected transaction with no [CVV](./CVV.md) and decline more of them, and European issuers may demand [strong customer authentication](./Strong%20customer%20authentication.md) that the absent customer cannot complete. Renewals fail while first payments look healthy.

Record the consent text and time, the agreed purpose, the initial transaction ID and the credential's status. Do not store the CVV after authorization, which [PCI DSS](./PCI%20DSS.md) prohibits. If a customer removes a saved card, stop using it.

_Usage:_

"First payments work, but renewals decline far more often."

"We're not sending the stored credential flags or the original transaction ID. Issuers can't tell these are agreed renewals."
