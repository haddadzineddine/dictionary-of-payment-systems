---
description: A PCI DSS validation form for eligible organisations, with the version chosen by how they handle card data.
---

A self-assessment questionnaire (SAQ) is a form that eligible organisations use to validate their [PCI DSS](./PCI%20DSS.md) compliance without a full on-site assessment. The right version depends on how the business accepts cards.

| SAQ    | Typical [merchant](./Merchant.md)                                     |
| ------ | --------------------------------------------------------------------- |
| A      | Card-not-present, with all account data functions fully outsourced    |
| A-EP   | E-commerce where the merchant's site can affect payment page security |
| B      | Imprint machines or standalone dial-out terminals                     |
| B-IP   | Standalone approved terminals with an IP connection                   |
| C      | Payment application connected to the internet, no electronic storage  |
| C-VT   | Manual entry into a third-party virtual terminal on an isolated device |
| P2PE   | Only a validated, PCI-listed [point-to-point encryption](./Point-to-point%20encryption.md) solution |
| SPoC   | Listed software-based PIN entry solution on a commercial mobile device |
| D      | All other eligible merchants, and all eligible service providers      |

An [acquirer](./Acquirer.md) or payment brand decides whether a merchant may self-assess or needs an assessor's report.

A common mistake is assuming any hosted checkout qualifies for SAQ A. The v4.0.1 revision of SAQ A removed requirements 6.4.3, 11.6.1 and 12.3.1 from that form and added an eligibility criterion: an e-commerce merchant must confirm its site is not susceptible to attacks from scripts that could affect its systems.

PCI SSC's FAQ 1588 explains that this criterion applies to pages that embed a provider's form, such as through an iframe with [hosted payment fields](./Hosted%20payment%20fields.md). It does not apply to a full redirect to the provider or a fully outsourced flow such as an emailed payment link. A merchant can meet it with protective techniques or a compliant provider's confirmation.

If a developer later adds a custom card form or stores card numbers, the business may no longer qualify, so review eligibility whenever checkout changes.

_Usage:_

"We embed the PSP's iframe, so we just tick SAQ A?"

"Only if we meet the script-attack criterion. Get the provider's confirmation or put the controls on our page."
