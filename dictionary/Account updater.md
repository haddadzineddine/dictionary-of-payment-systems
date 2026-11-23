---
description: A card network service that gives merchants updated card numbers and expiry dates for stored cards.
---

An account updater is a [card network](./Card%20network.md) service that gives [merchants](./Merchant.md) new details for cards they have on file when a card is reissued, expires or is closed. Visa Account Updater and Mastercard Automatic Billing Updater are the main examples. [Issuers](./Issuer.md) report changes to the network, and the merchant's [acquirer](./Acquirer.md) or provider requests updates, either in batches before billing or in real time during authorization.

| Response             | Meaning                         | Merchant action                         |
| -------------------- | ------------------------------- | --------------------------------------- |
| New card number      | Card was replaced               | Update the [stored credential](./Stored%20credential.md)            |
| New expiry           | Same number, new date           | Update the expiry                       |
| Account closed       | Card is no longer valid         | Stop billing and ask for a new method   |
| Contact [cardholder](./Cardholder.md)   | Issuer gives no replacement     | Ask the customer                        |
| No match             | Issuer has no change or doesn't participate | Continue, and handle any decline |

Coverage depends on issuer participation, and some cardholders can opt out, so a stored card may still fail.

An account updater differs from a [network token](./Network%20token.md). A token is a substitute credential whose lifecycle is managed by the network, so the merchant can keep charging the same token after the underlying card is replaced. Account updater returns new card data to whoever holds the original [PAN](./PAN.md). [Dunning](./Dunning.md), by contrast, reacts after a payment fails.

The symptom it addresses is a burst of renewal declines around month end from expired cards, with customers who never meant to leave. A related bug happens when the provider updates its vault but the merchant's own record keeps the old last four digits and expiry, so the billing page shows an expired card.

Consume the provider's update events and sync display fields. Also stop charging on a closed-account response. Updated card numbers are cardholder data, so handle them within your [PCI DSS](./PCI%20DSS.md) scope, or leave them with the provider.

_Usage:_

"Renewals are failing because so many cards expired this month."

"Turn on the account updater with our acquirer, and sync the new expiry dates to our billing records."
