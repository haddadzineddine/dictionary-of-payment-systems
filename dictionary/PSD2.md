---
description: The EU Payment Services Directive (EU) 2015/2366, which regulates payment providers and requires strong authentication.
---

PSD2 is the EU's second Payment Services Directive, formally Directive (EU) 2015/2366. It sets the rules for who may provide payment services in the EU and European Economic Area, what those providers owe their customers, and how payments must be secured. It takes effect through each member state's national law, so details differ by country.

| Area              | What PSD2 does                                                          |
| ----------------- | ----------------------------------------------------------------------- |
| Licensing         | Defines payment services and who must be authorised to provide them     |
| Security          | Requires [strong customer authentication](./Strong%20customer%20authentication.md) (SCA) in Article 97 |
| Customer rights   | Sets [refund](./Refund.md) and liability rules for unauthorised payments               |
| Third-party access | Creates regulated access to accounts, the basis of EU [open banking](./Open%20banking.md) |

Detailed security rules are in a separate, directly applicable law, Commission Delegated Regulation (EU) 2018/389. SCA is one part of PSD2, and [3-D Secure](./3-D%20Secure.md) is a technical protocol the directive does not name.

When both the payer's and payee's providers are in the EEA, SCA generally applies. When only one is, the payment is a "one-leg" transaction. A Commission answer published by the European Banking Authority says that an [acquirer](./Acquirer.md) outside the EU is not subject to PSD2, and the EU [issuer](./Issuer.md) must decide whether to block such a payment or carry the liability. A non-EU [merchant](./Merchant.md) selling to Europeans may therefore see [soft declines](./Soft%20decline.md) despite having no direct PSD2 obligations.

The UK implemented PSD2 before leaving the EU and now maintains its own rules through the FCA.

A replacement is in progress. The EU reached a provisional agreement in November 2025 on a Payment Services Regulation and a third directive, PSD3. As of November 2026, Parliament's procedure files list both as awaiting a second-reading vote, with no Official Journal publication. Until the new laws apply, PSD2 remains in force.

_Usage:_

"We're a US company. Why does PSD2 affect our checkout?"

"Our customers' banks are in the EU, so they may still ask for SCA. Add 3DS for those cards."
