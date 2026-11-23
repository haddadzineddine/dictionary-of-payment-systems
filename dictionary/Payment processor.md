---
description: The company whose systems handle card transaction messages and records for an acquirer or issuer.
---

A payment processor is a company that runs the systems handling card transactions on behalf of an [acquirer](./Acquirer.md) or [issuer](./Issuer.md). It formats and routes messages, tracks transaction state, and produces the files used for [clearing](./Clearing.md) and [settlement](./Settlement.md). The licensed institution remains accountable to the [card network](./Card%20network.md) even when a processor does the technical work.

Processors are usually divided by side and by stage.

| Type                | Works for | Handles                                                         |
| ------------------- | --------- | --------------------------------------------------------------- |
| Acquirer processor  | Acquirer  | Card acceptance, batches and reporting              |
| Issuer processor    | Issuer    | Card accounts, authorization decisions under issuer rules, posting |
| Front-end processor | Either    | Real-time [card authorization](./Card%20authorization.md) messages                    |
| Back-end processor  | Either    | Clearing files, settlement data and dispute records             |

The distinction from nearby terms is about responsibility. A [payment gateway](./Payment%20gateway.md) connects a [merchant's](./Merchant.md) checkout to processing. A processor runs the transaction work behind that connection. An acquirer holds the licence or network membership and takes on the merchant's risk. A [payment service provider](./Payment%20service%20provider.md) may package all three. Merchants often say "our processor" when they mean whichever vendor they pay, so confirm the actual role before relying on the word.

Processor problems tend to appear as gaps between systems. A batch that was not submitted on time means authorized sales do not reach clearing, so funds arrive late and the hold stays on the customer's card. A partial outage may produce approvals in one system with no matching record in another. These cases surface during [payment reconciliation](./Payment%20reconciliation.md), when expected sales are missing from a [settlement file](./Settlement%20file.md).

When investigating, compare identifiers across stages: the authorization code, the [network transaction ID](./Network%20transaction%20ID.md) and, once cleared, the [acquirer reference number](./Acquirer%20reference%20number.md). The stage where the identifier disappears shows where the transaction stopped.

_Usage:_

"Tuesday's sales were authorized, but they're missing from the settlement report."

"Looks like the processor never submitted that batch. Ask them to confirm it and resubmit before the authorizations go stale."
