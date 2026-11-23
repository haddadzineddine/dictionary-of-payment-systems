---
description: The merchant name and details a cardholder sees for a payment on a bank or card statement.
---

A statement descriptor is the text identifying a [merchant](./Merchant.md) on a [cardholder's](./Cardholder.md) bank or card statement. It is built from the merchant name and location data carried in the [card authorization](./Card%20authorization.md) and [clearing](./Clearing.md) messages, such as the card acceptor name field in [ISO 8583](./ISO%208583.md). The [issuer](./Issuer.md) decides how to display it, so the same payment can look different across banking apps.

An unclear descriptor directly causes disputes. A customer buys from a shop called Northwind but the statement reads `NWD HOLDINGS LTD`. Weeks later they do not recognise it and report it to their bank as fraud, producing a [chargeback](./Chargeback.md) on a legitimate order. This is a common form of [friendly fraud](./Friendly%20fraud.md).

Visa's Merchant Data Standards Manual calls the merchant name the most important factor in cardholder recognition, and requires it to be the name most prominently displayed by the merchant and recognised by cardholders. Visa's rules also require [acquirers](./Acquirer.md) to correct names that are non-compliant or that confuse cardholders.

| Descriptor                 | Result                                         |
| -------------------------- | ---------------------------------------------- |
| Legal company name only    | Often unrecognised                             |
| Trading or brand name      | Usually recognised                             |
| Brand and order reference  | Easier to match to a receipt                   |
| Platform name only         | Customer may not recognise the actual seller   |

Length limits are tight and vary by network and provider, so test the shortened version. A [payment service provider](./Payment%20service%20provider.md) may let you set a static descriptor for the account and a dynamic suffix per payment. Platforms often use a prefix and seller name. If a [merchant of record](./Merchant%20of%20record.md) is involved, its name normally appears, so mention it at checkout and on the receipt.

To reduce disputes, use the name customers see on your website, send a receipt that shows the exact descriptor, and include a support contact where the format allows.

_Usage:_

"Half of this month's fraud disputes are from customers who did get their orders."

"Our descriptor still shows the holding company. Change it to the store name."
