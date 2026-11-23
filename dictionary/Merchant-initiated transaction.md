---
description: A payment the merchant starts without the cardholder present, under an agreement made in an earlier transaction.
---

A merchant-initiated transaction, or MIT, is a card payment that a merchant starts without the [cardholder](./Cardholder.md) taking part, relying on an agreement made earlier. The merchant must have a [stored credential](./Stored%20credential.md) and consent to use it, and each MIT is flagged so the [issuer](./Issuer.md) can see it belongs to an existing agreement.

| Type         | Example                              | Schedule                |
| ------------ | ------------------------------------ | ----------------------- |
| Recurring    | Monthly software subscription        | Fixed interval          |
| Instalment   | A purchase split into set payments   | Fixed number of payments |
| Unscheduled  | Account top-up when balance runs low | Triggered by an event   |
| Industry-specific | Hotel no-show or delayed charge | Set by network rules    |

Each MIT normally carries the [network transaction ID](./Network%20transaction%20ID.md) of the original or a previous transaction. This links it to the [customer-initiated transaction](./Customer-initiated%20transaction.md) in which the cardholder agreed. Without that link, an issuer may treat the payment as unexpected and decline it.

In the EEA and UK, an MIT is treated as outside [strong customer authentication](./Strong%20customer%20authentication.md) because the payer is not involved at the time of payment. That position depends on a valid setup. European Banking Authority Q&As say SCA applies when the mandate is given, usually during the first payment. An MIT is not an [SCA exemption](./SCA%20exemption.md), and labelling a payment MIT when the customer is present is misuse.

The failure teams see is a batch of renewals declined with an authentication-required code. Cards saved before SCA, or saved without authentication, have no valid agreement behind them. The customer is offline and cannot complete a challenge, so the fix is to bring them back for an authenticated payment that creates a new agreement.

A customer who forgot about a subscription may dispute it as fraud, so keep the consent record and stop billing as soon as they cancel.

_Usage:_

"Half the renewal batch failed with authentication required."

"Those cards were saved without SCA, so the merchant-initiated transactions have no valid mandate. Email customers to reauthenticate."
