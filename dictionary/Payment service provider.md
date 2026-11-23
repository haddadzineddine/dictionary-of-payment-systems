---
description: A company that lets merchants accept payments, or in EU law, an institution authorised to provide payment services.
---

A payment service provider (PSP) is a company that gives [merchants](./Merchant.md) the means to accept payments, usually through one contract and one API. The term has two meanings, and they do not always describe the same company.

| Sense      | Meaning                                                                                                     |
| ---------- | ----------------------------------------------------------------------------------------------------------- |
| Commercial | A vendor that bundles checkout, processing, reporting and payouts                                           |
| EU legal   | Under [PSD2](./PSD2.md), a defined category such as a credit institution, e-money institution or payment institution |

A company can be a PSP commercially while relying on a licensed partner for the regulated activity. Check the contract to see which entity holds the funds and which is the [acquirer](./Acquirer.md).

The roles around a PSP are often blurred because one vendor may perform several of them.

| Role                                              | What it does                                   | Holds merchant funds? |
| ------------------------------------------------- | ---------------------------------------------- | --------------------- |
| [Payment gateway](./Payment%20gateway.md)         | Passes payment data to processing systems      | Usually not           |
| [Payment processor](./Payment%20processor.md)     | Runs authorization and [clearing](./Clearing.md) messages       | Usually not           |
| Acquirer                                          | Signs the merchant and answers to the network  | Yes, or via a partner |
| [Payment facilitator](./Payment%20facilitator.md) | Onboards sub-merchants under an acquirer       | Often                 |
| [Merchant of record](./Merchant%20of%20record.md) | Is the legal seller of the goods to the buyer  | Yes                   |
| PSP                                               | Packages some or all of the above              | Depends on the model  |

A PSP may be a payment facilitator for small accounts and offer a direct acquiring contract to large ones, so the same vendor name can imply different responsibilities.

The cost of this bundling appears when a merchant tries to leave. Saved cards are often held as PSP-specific [tokens](./Tokenization.md) in the provider's [card vault](./Card%20vault.md), so they do not work elsewhere until the card data is migrated. Ask about export terms before integrating, and store your own record of each payment rather than treating the PSP's dashboard as your only source of truth.

_Usage:_

"We can switch PSPs over the weekend, right?"

"Not with saved cards. Our tokens only work with the current provider, so we need a vault migration first."
