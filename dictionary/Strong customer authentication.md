---
description: The EU requirement under PSD2 to authenticate payers with two independent factors, for many electronic payments.
---

Strong customer authentication (SCA) is a legal requirement in the European Economic Area, set by [PSD2](./PSD2.md), that a payer be authenticated using at least two independent factors from different categories. Article 4(30) defines the categories, and independence means that compromising one factor does not compromise the others.

| Category   | Meaning                        | Examples                     |
| ---------- | ------------------------------ | ---------------------------- |
| Knowledge  | Something only the user knows  | PIN, password                |
| Possession | Something only the user has    | Registered phone, chip card  |
| Inherence  | Something the user is          | Fingerprint, face            |

Article 97 requires a [payment service provider](./Payment%20service%20provider.md) to apply SCA when a payer accesses a payment account online, initiates an electronic payment, or takes a remote action that could carry fraud risk. For remote payments, the authentication must also be dynamically linked to the specific amount and payee. Delegated Regulation (EU) 2018/389 holds the detail, and the UK maintains its own version through the FCA.

SCA is an outcome and [3-D Secure](./3-D%20Secure.md) is a method. For online card payments, 3DS with a challenge is the usual way to meet it.

The obligation falls on the payer's provider, usually the [issuer](./Issuer.md), and the [merchant](./Merchant.md) must support the flow. Under Article 74(2), if the payer's provider does not require SCA, the payer does not bear financial losses unless they acted fraudulently, and a payee or payee's provider that fails to accept SCA must [refund](./Refund.md) the damage caused to the payer's provider.

An [SCA exemption](./SCA%20exemption.md) can remove the step, and purely [merchant-initiated transactions](./Merchant-initiated%20transaction.md) and mail or telephone orders are outside the requirement.

The symptom for a merchant is a rise in [soft declines](./Soft%20decline.md) from European cards when checkout does not support authentication. Saved-card flows often fail the same way if SCA was not performed when the card was first stored.

_Usage:_

"Why are EU cards failing when our US cards are fine?"

"Issuers are asking for SCA and our checkout has no 3DS step. We need to add it."
