---
description: Assigning a payment a score estimating its fraud risk, used to approve it, add authentication, review or block it.
---

Risk scoring assigns a transaction, account or event a value that estimates how likely it is to be fraudulent. A system then uses the score to choose an action. Scores may come from rules, machine-learning models or both, and several parties can compute them independently.

| Party                                 | What it scores from                                 |
| ------------------------------------- | --------------------------------------------------- |
| [Merchant](./Merchant.md)             | Account history, device, basket, delivery details   |
| [Payment service provider](./Payment%20service%20provider.md) | Patterns across its merchants |
| [Card network](./Card%20network.md)   | Activity across its members          |
| [Issuer](./Issuer.md)                 | [Cardholder](./Cardholder.md)'s spending and account behaviour         |

The score is an input to a decision, and the action is set by thresholds.

| Score band | Typical action                                       |
| ---------- | ---------------------------------------------------- |
| Low        | Approve, possibly request an [SCA exemption](./SCA%20exemption.md) |
| Medium     | Add [3-D Secure](./3-D%20Secure.md)                  |
| High       | Send to manual review                                |
| Very high  | Block                                                |

Scales are vendor-specific, so a score of 80 from one provider is not comparable with 80 from another.

The cost of false positives is easy to miss. A blocked legitimate customer rarely complains and may leave, so a dashboard can show falling fraud while revenue drops. Measure false declines by sampling blocked orders or holding back a small control group, where that is lawful and acceptable.

Training data has a built-in delay. Fraud labels often arrive weeks later through [chargebacks](./Chargeback.md), and [friendly fraud](./Friendly%20fraud.md) can label genuine customers as criminals. Blocked orders also have no outcome, so a model learns only from what it allowed. Monitor for drift, and keep the score, model version and input features for each decision so it can be explained later.

Regulation can make risk analysis mandatory for some uses. Under EU Delegated Regulation 2018/389, a provider using the transaction risk analysis exemption must perform real-time analysis covering factors such as abnormal spending, unusual device information, known fraud scenarios and abnormal payer location.

_Usage:_

"Fraud is down since we tightened the model, but so are sales."

"The threshold's too aggressive. Send the middle band to 3DS rather than blocking it."
