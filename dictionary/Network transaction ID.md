---
description: A card network's identifier for a transaction, used to link later messages and stored-card payments to the original.
---

A network transaction ID is the identifier a [card network](./Card%20network.md) assigns to a transaction, returned with the [card authorization](./Card%20authorization.md) response. Later messages for the same payment, and later payments that depend on it, carry this value so that the network and [issuer](./Issuer.md) can connect them. The generic term covers different network-specific fields.

| Network    | Name in the rules      | Notes                                                             |
| ---------- | ---------------------- | ----------------------------------------------------------------- |
| Visa       | Transaction Identifier | Assigned per transaction, used as an audit trail through the life cycle |
| Mastercard | Trace ID               | Built from network reference data and settlement date             |

It is different from the [acquirer reference number](./Acquirer%20reference%20number.md), which appears at [clearing](./Clearing.md) and is the usual reference for tracing a [refund](./Refund.md) with a bank. The network transaction ID exists from authorization onward and is primarily for system-to-system linking.

The ID matters most for [stored credentials](./Stored%20credential.md). When a customer saves a card, the first [customer-initiated transaction](./Customer-initiated%20transaction.md) establishes consent. Each later [merchant-initiated transaction](./Merchant-initiated%20transaction.md) references that original ID, showing the issuer that this charge belongs to an agreed series. Under [PSD2](./PSD2.md), this link also helps show why a later charge, made without the customer present, was sent without [strong customer authentication](./Strong%20customer%20authentication.md).

The failure usually appears during a migration. A company moves to a new [payment service provider](./Payment%20service%20provider.md), imports card numbers or tokens, but leaves the original network IDs behind. Renewals now look like unlinked payments with no customer present, and issuers decline more of them, often with an authentication-required [soft decline](./Soft%20decline.md). Ask for the network transaction IDs in the export, and confirm the new provider can accept them.

Store the ID with the payment method and with each payment, and pass through the value from the correct original transaction. Fabricating or reusing an unrelated ID misrepresents the transaction.

_Usage:_

"Renewal declines jumped right after the PSP migration."

"We imported the tokens but not the network transaction IDs, so the issuers can't link those charges to the original consent."
