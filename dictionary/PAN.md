---
description: The primary account number on a payment card, which identifies the issuer and card account under ISO/IEC 7812.
---

A PAN, or primary account number, is the long number that identifies a payment card account. Its format comes from ISO/IEC 7812, which allows up to 19 digits. Sixteen is common, but not universal, so a form or database column that assumes 16 digits will reject or corrupt valid cards.

| Part                 | Position         | Purpose                                         |
| -------------------- | ---------------- | ----------------------------------------------- |
| [Issuer](./Issuer.md) identifier | Leading digits   | The [BIN](./BIN.md), identifying the issuer or program |
| Account identifier   | Middle digits    | The individual account within that issuer       |
| Check digit          | Final digit      | Catches typing errors using the Luhn formula    |

The Luhn check only detects mistyped numbers. A number that passes is well formed, and that says nothing about whether the account exists, is open, or belongs to the person typing it. Only a [card authorization](./Card%20authorization.md) can check that.

[PCI DSS](./PCI%20DSS.md) treats the PAN as the defining element of cardholder data: if a system stores, processes or transmits it, that system is in scope. Masking and truncation are different. Masking hides digits on a screen while the full value may still exist underneath. Truncation permanently removes digits from the stored value. PCI SSC publishes the formats it accepts for truncation, and these changed with the move to longer BINs.

The usual incident is accidental storage. A debug log captures a full request body, a support agent pastes a card number into a ticket, or an analytics script reads a checkout field. This widens compliance scope and requires clean-up across logs and backups.

Most [merchants](./Merchant.md) avoid handling the PAN by using [hosted payment fields](./Hosted%20payment%20fields.md) and keeping a [PSP token](./Tokenization.md) or [network token](./Network%20token.md). A network token is itself a different number in PAN format, so code should not assume that every card-shaped value is the underlying card number.

_Usage:_

"Why is compliance asking us to purge three months of application logs?"

"The request logger captured full PANs from the checkout endpoint. Those logs are now in PCI scope."
