---
description: The security standard for organisations that store, process or transmit payment card account data.
---

PCI DSS, the Payment Card Industry Data Security Standard, is the security standard for organisations that store, process or transmit payment card account data, or that can affect its security. It is published by the PCI Security Standards Council (PCI SSC), founded by the major [card networks](./Card%20network.md). The current series is v4.x, and the Council's document library holds the latest revision.

Account data has two parts, and the rules treat them differently.

| Data type                     | Examples                                  | Storage after authorization        |
| ----------------------------- | ----------------------------------------- | ---------------------------------- |
| Cardholder data               | [PAN](./PAN.md), name, expiry, service code | Allowed if protected and justified |
| Sensitive authentication data | Full track, [CVV](./CVV.md), PIN          | Not allowed, even if encrypted     |

A narrow exception exists for [issuers](./Issuer.md) and companies supporting issuing services.

The Council writes the standard, but it does not enforce it. Whether an organisation must comply or validate is decided by those running compliance programs.

| Party                      | Role                                                  |
| -------------------------- | ----------------------------------------------------- |
| PCI SSC                    | Publishes the standard and trains assessors           |
| Payment brands             | Set compliance programs and any penalties             |
| [Acquirers](./Acquirer.md) | Require their [merchants](./Merchant.md) to validate  |
| Qualified Security Assessor | Independently assesses an organisation               |
| Merchants and providers    | Implement and maintain the controls                   |

PCI DSS is a contractual industry standard and not, in general, a law, although some jurisdictions refer to it. A merchant usually encounters it through an acquirer's request for a [self-assessment questionnaire](./Self-assessment%20questionnaire.md) or a formal assessment report.

The practical work is reducing scope, meaning the set of systems the standard covers. Teams do this by not handling card data at all, using [hosted payment fields](./Hosted%20payment%20fields.md), [tokenization](./Tokenization.md) or [point-to-point encryption](./Point-to-point%20encryption.md).

Scope often grows by accident. A log line captures a card number, or a marketing script is added to the payment page. Requirements 6.4.3 and 11.6.1 address that second risk by requiring control and monitoring of payment page scripts.

_Usage:_

"We use a PSP, so PCI doesn't apply to us, right?"

"It still applies. The PSP shrinks our scope, but we still validate with the right SAQ."
