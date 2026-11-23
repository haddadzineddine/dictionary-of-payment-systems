---
description: A software layer connecting a business to several payment providers and methods through one integration.
---

Payment orchestration is a software layer that connects a business to multiple payment providers, [acquirers](./Acquirer.md) and payment methods through one integration. The [merchant](./Merchant.md)'s checkout calls the orchestration layer, and that layer decides where each payment goes and normalises the responses.

| Function            | What it does                                                |
| ------------------- | ----------------------------------------------------------- |
| Connectors          | Translates one internal API to each provider's API          |
| [Payment routing](./Payment%20routing.md)     | Picks a provider per transaction                            |
| Token management    | Stores credentials so they can be used across providers     |
| Retry and failover  | Applies rules after a failed attempt                        |
| Normalisation       | Maps [decline codes](./Decline%20code.md) and statuses to one model                |
| Reporting           | Combines data across providers                              |

An orchestrator is often confused with a [payment service provider](./Payment%20service%20provider.md) or [payment gateway](./Payment%20gateway.md). A PSP has acquiring relationships and processes payments. A gateway transmits payments to a processor. An orchestrator usually sits above them and depends on their contracts, so the merchant typically still needs its own agreement with each provider.

The benefits are redundancy, access to local methods and bargaining power. The layer also adds a network hop and another dependency that can fail, so an orchestrator outage can stop all payments. If it handles raw card data, it also affects [PCI DSS](./PCI%20DSS.md) scope. Normalising responses can hide the detail needed to debug a decline, so keep the raw provider response.

Token ownership often causes problems at migration time. A business adopts multiple providers and finds that its saved cards are tokens owned by the original provider, which cannot be charged elsewhere. Negotiate token portability in advance, or use a neutral [card vault](./Card%20vault.md) or [network tokens](./Network%20token.md).

Pass a stable reference from the merchant through the orchestrator to the provider, so that a retry at any level can be recognised. Treat a timeout at any hop as an [unknown payment outcome](./Unknown%20payment%20outcome.md).

_Usage:_

"Can we just add a second provider if the first goes down?"

"Only with payment orchestration and portable tokens. Otherwise our saved cards won't work on the second provider."
