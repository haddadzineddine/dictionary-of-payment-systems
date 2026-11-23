---
description: A checkout method where the customer pays directly from their bank account, often through open banking payment initiation.
---

Pay by bank is a checkout method in which a customer pays a [merchant](./Merchant.md) directly from a bank account instead of with a card. In many markets it uses [open banking](./Open%20banking.md): a licensed payment initiation provider sends the customer to their bank to approve a pre-filled transfer. The underlying rail depends on the country, for example [Faster Payments](./Faster%20Payments.md) in the UK or a [SEPA Credit Transfer](./SEPA%20Credit%20Transfer.md) or [SEPA Instant](./SEPA%20Instant.md) in Europe. In the US, products under this name often use linked accounts and an [ACH](./ACH.md) debit, and some use instant rails.

| Step | Who                   | What happens                                 |
| ---- | --------------------- | -------------------------------------------- |
| 1    | Customer              | Chooses pay by bank and selects a bank       |
| 2    | Payment provider      | Creates a payment with amount and reference  |
| 3    | Customer's bank       | Authenticates the customer, who approves     |
| 4    | Customer's bank       | Sends the payment on the rail                |
| 5    | Merchant              | Confirms receipt, then fulfils               |

Compared with cards, there is no [interchange fee](./Interchange%20fee.md) and usually no card-style [chargeback](./Chargeback.md). That shifts the risk. Consumer protection comes from the rail and local law, not [card network](./Card%20network.md) rules, and it differs by market. A push payment is generally hard to reverse, while a US ACH debit can come back later as a [payment return](./Payment%20return.md).

The common engineering mistake is treating the customer's approval as payment received. "Authorised" at the bank can still become rejected, pending or delayed by a fraud check. A customer can also close the browser after approving, so the redirect never reaches your site and the order looks abandoned. Rely on server-side status from the provider and query it if no update arrives.

[Refunds](./Refund.md) also work differently. There is no card to credit, so the merchant needs the payer's account details or a provider feature that returns funds.

_Usage:_

"The customer's bank says they paid, but our order is still pending."

"With pay by bank the redirect can fail after approval. Query the provider's status instead of relying on the return URL."
