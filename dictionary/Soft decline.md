---
description: A card decline that may succeed after a change, most specifically when the issuer requires stronger authentication.
---

A soft decline is a card refusal that may succeed if something changes. The term has two uses, and teams often mix them up.

| Use    | Meaning                                                    | Correct response                  |
| ------ | ---------------------------------------------------------- | --------------------------------- |
| Narrow | [Issuer](./Issuer.md) requires [strong customer authentication](./Strong%20customer%20authentication.md) | Authenticate, then send a new request |
| Broad  | Any temporary condition, such as insufficient funds or an issuer outage | Retry later, within network limits |

The narrow sense comes from European regulation. Under [PSD2](./PSD2.md), when a payment needs authentication and arrives without it, the issuer can decline with a specific code asking for it. Mastercard's Transaction Processing Rules require issuers in its listed SCA countries to use a "soft decline" response in this case, and require the [merchant](./Merchant.md) to attempt [3-D Secure](./3-D%20Secure.md) with a mandated challenge or use another SCA method. Visa's rules list code `1A`, "additional customer authentication required", for its Europe and CEMEA regions.

The typical symptom appears after a merchant requests an [SCA exemption](./SCA%20exemption.md). The issuer does not accept it and returns a soft decline. If the checkout shows a generic "card declined" message, the customer leaves even though one authentication step would probably have completed the sale.

The handling should be explicit in the [payment state machine](./Payment%20state%20machine.md):

| Step | Who      | What happens                                                |
| ---- | -------- | ----------------------------------------------------------- |
| 1    | Merchant | Sends the [card authorization](./Card%20authorization.md)   |
| 2    | Issuer   | Returns the authentication-required code                    |
| 3    | Merchant | Starts 3-D Secure with the customer present                 |
| 4    | Merchant | Sends a new authorization with the authentication data      |

If the customer is absent, as in a [merchant-initiated transaction](./Merchant-initiated%20transaction.md), step 3 cannot happen immediately. Ask them to return and authenticate through an email or in-app prompt.

The broad usage needs a [payment retry](./Payment%20retry.md) policy with limits and spacing. Contrast both uses with a [hard decline](./Hard%20decline.md), where retrying the same card will not help.

_Usage:_

"Conversion in Germany dropped after we turned on the low-value exemption."

"Those are soft declines. We're showing an error instead of falling back to 3DS."
