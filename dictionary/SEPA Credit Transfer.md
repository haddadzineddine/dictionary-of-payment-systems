---
description: The euro bank transfer scheme across SEPA countries, where the payer's bank pushes funds under European Payments Council rules.
---

A SEPA Credit Transfer, or SCT, is a euro payment that a payer instructs their bank to push to a payee's account within the Single Euro Payments Area. The European Payments Council publishes the rulebook for participating [payment service providers](./Payment%20service%20provider.md) (PSPs). SEPA is wider than the EU and includes non-EU countries such as Norway, Switzerland and the United Kingdom.

| Step | Who         | What happens                                         |
| ---- | ----------- | ---------------------------------------------------- |
| 1    | Payer       | Enters the payee's [IBAN](./IBAN.md), name, amount and reference  |
| 2    | Payer's PSP | Validates and debits the account                     |
| 3    | Clearing system | Exchanges the [ISO 20022](./ISO%2020022.md) message and settles between PSPs |
| 4    | Payee's PSP | Credits the payee                                    |

EU payment services law generally requires a euro transfer to reach the payee's provider by the end of the next business day. A standard SCT is therefore not instant. [SEPA Instant](./SEPA%20Instant.md) is a separate scheme that runs continuously, while [SEPA Direct Debit](./SEPA%20Direct%20Debit.md) is a pull payment started by the creditor.

Since 9 October 2025, the Instant Payments Regulation has required euro-area banks to offer verification of payee on euro credit transfers. The check compares the payee name with the IBAN before the payer confirms. Providers in non-euro EU member states have a later date of 9 July 2027, and payment and e-money institutions follow their own timetable.

Two failures are common for businesses collecting by transfer. A customer omits or mistypes the reference, so the money arrives but nothing links it to an invoice, and it waits in a suspense account. Or a payer sends funds to the wrong IBAN and asks for them back. The payer's bank can send a recall, which the receiving side may refuse. Issue a unique reference per invoice and match on it automatically.

_Usage:_

"The customer sent proof of transfer, but the invoice is still unpaid."

"The SEPA Credit Transfer arrived without a reference. Match it from the suspense account and make the reference field clearer on the invoice."
