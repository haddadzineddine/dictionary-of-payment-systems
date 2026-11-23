---
description: Replacing a card number with a substitute value, so most systems never hold the real account data.
---

Tokenization replaces a sensitive value, such as a card's [PAN](./PAN.md), with a substitute called a token. The token can be stored and passed around in place of the card number, and only a controlled system can map it back or use it to make a payment. It is the usual way a [merchant](./Merchant.md) keeps a customer's card on file without holding the card number.

Tokenization differs from encryption. Encrypted data can be recovered by anyone holding the key, while a token normally has no mathematical relationship to the original and is resolved by lookup in a [card vault](./Card%20vault.md) or by a token service.

"Token" covers several things in payments, and the differences matter.

| Type                               | Created by                       | Usable where                     |
| ---------------------------------- | -------------------------------- | -------------------------------- |
| PSP token                          | [Payment service provider](./Payment%20service%20provider.md) | Usually that provider only |
| [Network token](./Network%20token.md) | Network token service         | Across the network, within its domain limits |
| Device wallet token                | Network token service, for a wallet | That device or wallet          |
| Merchant-internal token            | Merchant's own vault             | That merchant's systems          |

The first two are often confused. A team switching providers can discover that its saved PSP tokens do not work elsewhere, and that a card data migration is needed before renewals can continue.

Tokenization reduces [PCI DSS](./PCI%20DSS.md) scope but does not remove it. PCI SSC's tokenization guidance says the tokenization system itself remains part of the cardholder data environment. Systems holding only tokens may fall out of scope if they have no route back to the PAN. A token that can itself initiate a transaction may still need protection because it can be used to spend money.

For that reason, restrict which API keys can charge a token, and treat token stores as sensitive even when they contain no card numbers.

_Usage:_

"We tokenized everything, so a leak of this table is harmless, right?"

"Not quite. Those tokens can charge customers through our API key, so they still need protecting."
