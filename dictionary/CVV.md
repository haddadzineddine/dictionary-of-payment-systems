---
description: The short card security code checked by the issuer on remote payments. PCI DSS forbids storing it after authorization.
---

A CVV, or card verification value, is the short security code on a payment card that an [issuer](./Issuer.md) can check during a [card-not-present transaction](./Card-not-present%20transaction.md). It is meant to show that the person paying has access to the card rather than only the [PAN](./PAN.md). The name varies by network.

| Network          | Common name | Usual length and location     |
| ---------------- | ----------- | ----------------------------- |
| Visa             | CVV2        | Three digits, back of card    |
| Mastercard       | CVC2        | Three digits, back of card    |
| American Express | CID         | Four digits, front of card    |

The printed code differs from the value encoded on the magnetic stripe, and chip transactions use separate cryptographic values.

[PCI DSS](./PCI%20DSS.md) classes the card verification code as sensitive authentication data. Requirement 3.3.1 forbids storing such data after [authorization](./Card%20authorization.md), even if encrypted. Issuers and companies supporting issuing services have a narrow exception. Teams building subscriptions sometimes save the CVV for later charges. That breaches the standard and is unnecessary: a later [merchant-initiated transaction](./Merchant-initiated%20transaction.md) relies on the [stored credential](./Stored%20credential.md) framework and does not need the code. Keep it out of logs and queues too.

A CVV check is a signal and does not prove identity. The result comes back with the authorization, and a mismatch does not always cause a decline, because some issuers approve anyway and leave the decision to the [merchant](./Merchant.md). Decide in your [risk scoring](./Risk%20scoring.md) rules whether to reverse an approved payment with a failed check. If you do, send an [authorization reversal](./Authorization%20reversal.md) so the funds are released.

Stolen card data often includes the code, so a correct CVV does not rule out fraud. Unlike [3-D Secure](./3-D%20Secure.md), a passing CVV check does not by itself give the merchant a [liability shift](./Liability%20shift.md). Repeated CVV failures across attempts on one card are a sign of [card testing](./Card%20testing.md).

_Usage:_

"Can we store the CVV encrypted so renewals don't need the customer?"

"No, PCI DSS bans storing it after authorization, even encrypted. Renewals should use the stored credential flow."
