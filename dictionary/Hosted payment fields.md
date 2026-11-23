---
description: Card inputs served by a payment provider inside a merchant's page, so card data bypasses the merchant's servers.
---

Hosted payment fields are card input boxes served by a [payment service provider](./Payment%20service%20provider.md) and embedded in a [merchant's](./Merchant.md) checkout, usually as iframes. An iframe is a small page from another domain displayed inside the main page. The customer appears to type on the merchant's site, but the [PAN](./PAN.md) and [CVV](./CVV.md) go directly from the browser to the provider, which returns a [token](./Tokenization.md).

| Step | Who      | What happens                                          |
| ---- | -------- | ----------------------------------------------------- |
| 1    | Browser  | Loads the merchant page and the provider's iframes    |
| 2    | Customer | Types card details into the iframes                   |
| 3    | Provider | Receives the card data and returns a token            |
| 4    | Merchant | Sends the token from its server to create the payment |

The approach sits between two other integration styles.

| Integration            | Who controls the page | Card data reaches merchant servers? | Common SAQ        |
| ---------------------- | --------------------- | ----------------------------------- | ----------------- |
| Full redirect          | Provider              | No                                  | SAQ A             |
| Hosted payment fields  | Merchant, with provider inputs | No                         | SAQ A, if eligible |
| Merchant script-built form | Merchant          | No, but its page handles the data | SAQ A-EP          |
| Direct API             | Merchant              | Yes                                 | SAQ D             |

Embedded fields do not make the page safe by default. A malicious script on the surrounding page cannot normally read an iframe from another origin, but it could draw a fake form over it or send the customer elsewhere. For this reason, the [PCI DSS](./PCI%20DSS.md) v4.0.1 version of the [self-assessment questionnaire](./Self-assessment%20questionnaire.md) SAQ A requires merchants embedding a provider's form to confirm their site is not susceptible to script attacks.

Engineers usually encounter a different failure. A tightened Content Security Policy, the browser rule listing allowed content sources, blocks the provider's domain. The card fields then render blank or the Pay button does nothing, often in production only. Allow the provider's documented domains and test checkout after changing security headers.

_Usage:_

"The card fields are blank in production, but they work locally."

"The new CSP is blocking the provider's iframe. Add their domains to frame-src."
