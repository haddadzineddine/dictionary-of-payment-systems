---
description: A secured system that stores card numbers and returns tokens so other systems never need to hold the real data.
---

A card vault is a secured system that stores card numbers and gives other systems a [token](./Tokenization.md) to use in their place. When a payment is needed, an authorised service sends the token, and the vault supplies the [PAN](./PAN.md) to the payment connection without exposing it to the rest of the application.

| Step | Who                  | What happens                                     |
| ---- | -------------------- | ------------------------------------------------ |
| 1    | Checkout             | Sends card details directly to the vault         |
| 2    | Vault                | Encrypts and stores the PAN, returns a token     |
| 3    | Application          | Stores only the token and display details        |
| 4    | Payment service      | Requests a charge using the token                |
| 5    | Vault                | Forwards the PAN to the [acquirer](./Acquirer.md) or processor    |

A vault holds the data that attackers want, so it is firmly in [PCI DSS](./PCI%20DSS.md) scope. It can store the PAN and expiry date, but it must not keep the [CVV](./CVV.md) after [card authorization](./Card%20authorization.md).

| Option                                                        | Benefit                   | Cost                                 |
| ------------------------------------------------------------- | ------------------------- | ------------------------------------ |
| [Payment service provider](./Payment%20service%20provider.md) vault | Least effort and scope    | Tied to that provider                |
| Independent third-party vault                                 | Can route to several PSPs | Another vendor, some integration work |
| Self-hosted vault                                             | Full control of the data  | Full PCI burden and security operations |

The choice usually becomes visible when a business wants to change provider or add a second one for [payment routing](./Payment%20routing.md). With a provider vault, stored cards cannot be moved by the [merchant](./Merchant.md). The old provider must export the data securely to a PCI-compliant recipient, which can take weeks and depends on the contract. Read the export terms before committing.

Migrations carry their own failure risk. Token mappings can be incomplete, and renewals can start declining if [network transaction IDs](./Network%20transaction%20ID.md) were not transferred with the cards. Run a test batch and compare [authorization rates](./Authorization%20rate.md) before and after.

_Usage:_

"Can we export our saved cards ourselves and upload them to the new provider?"

"No. The old vault has to transfer them directly to the new one under PCI controls."
