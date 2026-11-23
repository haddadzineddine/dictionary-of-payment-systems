---
description: An international bank account number under ISO 13616, with a country code, check digits and a domestic account identifier.
---

An IBAN, or International Bank Account Number, is a standard format for identifying a bank account across borders, defined by ISO 13616. It starts with a two-letter country code and two check digits, followed by a country-specific Basic Bank Account Number. It can be up to 34 characters long, and each country has a fixed length. [Swift](./SWIFT.md) acts as the registration authority and publishes the registry of national formats.

| Part         | Example from `GB82 WEST 1234 5698 7654 32` | Meaning                  |
| ------------ | ------------------------------------------ | ------------------------ |
| Country      | `GB`                                       | United Kingdom           |
| Check digits | `82`                                       | Detects typing errors    |
| BBAN         | `WEST12345698765432`                       | Domestic bank and account |

IBANs are used across Europe and in many countries in the Middle East and elsewhere. They are required for [SEPA Credit Transfer](./SEPA%20Credit%20Transfer.md) payments. The US does not use them, relying on a routing number and account number instead, so a form that insists on an IBAN will block American payees. An IBAN is also not a BIC: the BIC identifies a bank, while the IBAN identifies an account.

The check digits use a modulo 97 calculation. Move the first four characters to the end, convert letters to numbers (A is 10, B is 11), and the remainder must equal 1.

```js
const valid = (iban) => {
  const s = iban.replace(/\s/g, "").toUpperCase();
  const n = (s.slice(4) + s.slice(0, 4)).replace(/[A-Z]/g, (c) => c.charCodeAt(0) - 55);
  return BigInt(n) % 97n === 1n;
};
```

Passing this check only means the number is well formed. It does not prove that the account exists or belongs to the named person, so a mistyped but valid IBAN can still send money to a stranger. Verification of payee, which is required for euro transfers under the EU Instant Payments Regulation, addresses that gap. Store IBANs in uppercase without spaces, display them in groups of four, and validate length per country.

_Usage:_

"The form rejected a customer's IBAN, but it's correct on their statement."

"They pasted it with non-breaking spaces. Strip all whitespace before validating."
