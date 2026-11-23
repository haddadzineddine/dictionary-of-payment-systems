---
description: A payment using a blockchain token designed to track a reference asset, subject to crypto and payments regulation.
---

A stablecoin payment is a transfer of value using a blockchain token designed to hold a stable price against a reference asset, usually a currency. An issuer creates the tokens and, for fiat-backed designs, holds reserves intended to support redemption. A sender signs a transaction from a wallet, the blockchain records it, and the recipient's wallet receives the token. Businesses often use a provider to convert between bank money and tokens, known as on-ramping and off-ramping.

A stablecoin is not a bank deposit, and stability is not guaranteed. A token can trade below its reference value if confidence in its reserves or redemption falls. Whether holders can redeem directly, and on what terms, depends on the issuer and the applicable law. This entry is not investment or financial advice.

The legal position differs by jurisdiction:

| Jurisdiction | Position                                                                                 |
| ------------ | ---------------------------------------------------------------------------------------- |
| EU           | MiCA regulates e-money and asset-referenced tokens. The European Banking Authority advised that some e-money token services also need [PSD2](./PSD2.md) authorisation from 2 March 2026 |
| US           | The GENIUS Act and the OCC's final rule for its issuers take effect on 18 January 2027   |
| UK           | Financial Conduct Authority stablecoin rules are final, with the regime starting 25 October 2027 |

Unlike a card payment, a stablecoin transfer has no [chargeback](./Chargeback.md), and a confirmed transfer to a wrong address is generally unrecoverable. The same token can exist on several blockchains, so sending on a network the recipient does not support can strand funds. [Sanctions screening](./Sanctions%20screening.md) and [AML](./AML.md) duties can still apply.

Wait for the confirmation depth your risk policy requires before crediting a user. Store the chain, token contract, transaction hash and amount as an integer in the token's base units, because tokens define their own decimals.

_Usage:_

"The customer sent the stablecoin payment, but our wallet shows nothing."

"They used a chain we don't support. Check the transaction hash, and show the network at checkout."
