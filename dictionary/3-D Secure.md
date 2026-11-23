---
description: A protocol that lets a card issuer authenticate the customer during an online payment, with or without a challenge.
---

3-D Secure (3DS) is a messaging protocol that lets a card [issuer](./Issuer.md) authenticate a customer during an online payment. [EMVCo](./EMV.md) publishes the current specification as EMV 3-D Secure, and networks brand their programs, for example Visa Secure and Mastercard Identity Check. The "three domains" are the [acquirer](./Acquirer.md) side, the issuer side and the interoperability layer connecting them.

| Step | Who                 | What happens                                                |
| ---- | ------------------- | ----------------------------------------------------------- |
| 1    | [Merchant's](./Merchant.md) 3DS Server | Sends transaction and device data                          |
| 2    | Directory Server    | Run by the network, routes the request to the issuer        |
| 3    | Access Control Server | Issuer's system assesses risk                              |
| 4a   | Issuer              | Frictionless: authenticates without involving the customer  |
| 4b   | Customer            | Challenge: completes an app approval, passcode or biometric |
| 5    | Merchant | Includes the authentication result in the [card authorization](./Card%20authorization.md) |

Authentication and authorization are separate. 3DS asks "is this the real [cardholder](./Cardholder.md)?". The authorization that follows asks "will the issuer approve this payment?". A customer can pass a challenge and still be declined for insufficient funds.

3DS is often confused with [strong customer authentication](./Strong%20customer%20authentication.md). SCA is a legal requirement under [PSD2](./PSD2.md) in the EEA. 3DS is a technical protocol and a common way of meeting that requirement for cards. A frictionless 3DS result is not necessarily SCA, and 3DS is also used in regions with no SCA rule.

3DS also supports a [liability shift](./Liability%20shift.md) for fraud, under network rules. Visa's rules, for example, make certain fraud disputes invalid for a transaction authenticated through Visa Secure when the authorization carried the required authentication value and indicator.

A frequent bug is losing that value. The challenge succeeds, but the integration does not pass the authentication data into the authorization, so the issuer sees an unauthenticated payment. It can then return a [soft decline](./Soft%20decline.md), and the merchant loses any fraud protection.

_Usage:_

"The customer passed the 3DS challenge, but we still got a fraud chargeback."

"Check the auth request. We dropped the CAVV, so the issuer never saw the authentication."
