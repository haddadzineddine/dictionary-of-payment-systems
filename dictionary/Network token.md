---
description: A card-network-level substitute for a card number, limited to a merchant, device or payment scenario.
---

A network token is a substitute for a card's [PAN](./PAN.md), issued through a [card network's](./Card%20network.md) token service and recognised from the point of purchase through the [acquirer](./Acquirer.md) and network to the [issuer](./Issuer.md). It follows EMVCo's Payment Tokenisation Specification, where it is called an [EMV](./EMV.md) Payment Token. Visa Token Service and Mastercard Digital Enablement Service are two network implementations.

| Role                  | Who                                    | What it does                                   |
| --------------------- | -------------------------------------- | ---------------------------------------------- |
| Token Requestor       | [Merchant](./Merchant.md), wallet or provider | Registers and requests tokens                  |
| Token Service Provider | Usually the network                   | Creates tokens and maps them to the PAN        |
| Issuer                | [Cardholder](./Cardholder.md)'s institution               | Approves token creation and the payments       |
| Token User            | Merchant or wallet                     | Presents the token for payment                 |

A token is limited in use, for example to one merchant, one device, or a specific payment scenario, so a stolen token is worth far less than a card number. Depending on the use case, a one-time token cryptogram accompanies the payment to prove it is genuine. EMVCo also defines a Payment Account Reference, which lets systems link different tokens for the same underlying account without exposing the PAN.

The term is most often confused with a PSP [token](./Tokenization.md).

| Property            | Network token                    | PSP token                     |
| ------------------- | -------------------------------- | ----------------------------- |
| Issued by           | Token service, usually network   | Payment provider              |
| Seen by issuer      | Yes                              | No, the issuer sees the PAN   |
| Works across providers | Possible, if set up for it    | Generally no                  |
| Follows card changes | Can be updated by the issuer    | Depends on the provider       |

Because a network token can stay valid when the physical card is reissued, it can reduce failures on [recurring billing](./Recurring%20billing.md) after a card expires. A payment sent without a required cryptogram can still be declined. Code that reads a token's first digits as the card's [BIN](./BIN.md) may also misclassify the card, so ask your provider for the underlying card attributes.

_Usage:_

"Renewals keep failing whenever banks reissue cards."

"Turn on network tokens for stored cards. The issuer updates them when the card changes."
