---
description: Choosing which acquirer, network or rail handles a payment, based on cost, approval odds, availability and rules.
---

Payment routing is the decision about which path a payment takes: which [acquirer](./Acquirer.md), which debit network, or which bank rail. A [merchant](./Merchant.md) with several providers can route each payment based on the card, country, amount and current performance.

| Strategy           | Decides by                                | Trade-off                                  |
| ------------------ | ----------------------------------------- | ------------------------------------------ |
| Local acquiring    | Matching acquirer to the [issuer](./Issuer.md)'s country | Better approvals and lower [cross-border fee](./Cross-border%20fee.md) costs, more contracts |
| Least-cost         | Expected fees                             | May lower approval rates                   |
| Performance-based  | Recent [authorization rate](./Authorization%20rate.md)                 | Needs volume and monitoring                |
| Failover           | Provider or route health                  | Must handle uncertain outcomes             |
| Rule-based         | Regulation, currency or product           | Rules drift without maintenance            |

Routing is the decision. [Payment orchestration](./Payment%20orchestration.md) is the wider layer that carries it out and also covers integrations, tokens and reporting.

Some routing is shaped by law. In the US, the Durbin Amendment requires debit cards to be enabled on at least two unaffiliated networks, which gives merchants a routing choice. In the EU, the [Interchange Fee](./Interchange%20fee.md) Regulation addresses the choice of brand on co-badged cards.

Failover after a timeout can charge a customer twice. Provider A does not answer, the router sends the same payment to provider B, B approves it, and A's approval then appears. The customer has a [double charge](./Double%20charge.md), and an idempotency key cannot prevent it because each provider has its own key space. Fail over only after a definite failure, such as a connection refused before sending or a retryable decline. For a timeout, resolve the first attempt by querying its status.

Stored cards add a constraint. A token issued by one provider usually cannot be charged through another unless you hold portable credentials or [network tokens](./Network%20token.md). Log the chosen route and reason on every attempt.

_Usage:_

"Provider A timed out, so the router sent it to B. Now the customer has two charges."

"Payment routing can't fail over on a timeout. Check A's status first and only reroute if it didn't go through."
