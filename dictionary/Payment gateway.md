---
description: The technical service that carries payment details from a checkout to processing systems and returns the result.
---

A payment gateway is the technical service that takes payment details from a [merchant's](./Merchant.md) checkout, sends them securely toward the [payment processor](./Payment%20processor.md) or [acquirer](./Acquirer.md), and returns the response. It is the connection between the merchant's system and the card payment infrastructure. In a physical shop, the terminal and its software do a similar job.

| Role                                                  | Main question it answers                     |
| ----------------------------------------------------- | -------------------------------------------- |
| Gateway                                               | How does this request reach the card rails?  |
| Payment processor                                     | How is the transaction message handled?      |
| Acquirer                                              | Which licensed institution takes on this merchant? |
| [Payment service provider](./Payment%20service%20provider.md) | Who sells the merchant the packaged service? |

A standalone gateway usually does not hold the merchant's money. Under [PSD2](./PSD2.md), technical service providers that support payments without ever possessing the funds are excluded from the directive, which is one reason a pure gateway may not need a payment licence in the EU. Whether a specific business qualifies depends on what it actually does. Many modern providers combine gateway, processing and acquiring, so "gateway" often describes one layer of a larger product.

Because it handles card data, a gateway falls under [PCI DSS](./PCI%20DSS.md) as a service provider. It commonly also offers [tokenization](./Tokenization.md), [hosted payment fields](./Hosted%20payment%20fields.md), and [3-D Secure](./3-D%20Secure.md) integration.

The failure engineers meet most often here is a timeout. The merchant sends a charge to the gateway, the connection drops, and nobody on the merchant's side knows whether the [issuer](./Issuer.md) approved it. This is an [unknown payment outcome](./Unknown%20payment%20outcome.md). Retrying blindly can produce a [double charge](./Double%20charge.md). Instead, send a stable idempotency key (a client-generated value that makes retries safe) if the gateway supports one, then query the transaction status before attempting the payment again.

_Usage:_

"The gateway timed out on that order. Should the worker just retry the charge?"

"Not yet. Look up the payment by its reference first. It may have been approved even though we never got the response."
