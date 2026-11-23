---
description: Encrypting card data at the payment terminal so it stays unreadable until it reaches a secure decryption environment.
---

Point-to-point encryption (P2PE) encrypts card data inside a secure payment terminal at the moment the card is read, and keeps it encrypted until it reaches a protected decryption environment away from the [merchant](./Merchant.md). The shop's network, tills and back-office systems carry only ciphertext they cannot read. It is used with payment terminals, not online checkout.

The term has a general meaning and a specific one under [PCI DSS](./PCI%20DSS.md). Any vendor can describe its terminal as "encrypted". PCI P2PE is a separate PCI SSC standard, and only solutions validated against it and listed by the Council carry its compliance benefits.

| Feature                  | Encrypted terminal (generic)     | Validated PCI P2PE solution              |
| ------------------------ | -------------------------------- | ---------------------------------------- |
| Independently assessed   | Not necessarily                  | Yes, against the P2PE standard           |
| Listed by PCI SSC        | No                               | Yes                                      |
| Eligible for SAQ P2PE    | No                               | Yes, if the merchant meets the criteria  |

A retailer buys terminals advertised as end-to-end encrypted and assumes it qualifies for the shorter [self-assessment questionnaire](./Self-assessment%20questionnaire.md). An assessor then finds the solution is not on the PCI list, so the shop's network remains in scope. Check the PCI SSC listing before buying and again at renewal, because a solution whose listing has expired is no longer treated as validated, and the merchant should then ask its [acquirer](./Acquirer.md) what applies.

SAQ P2PE covers merchants that take account data only through a validated solution's terminals and have no clear-text account data on their computer systems. It does not apply to e-commerce. The merchant must also follow the solution's instruction manual.

P2PE is different from TLS, the encryption used for web traffic, which protects data between two connected systems. P2PE protects the card data from the terminal itself.

_Usage:_

"The vendor says the terminals are encrypted, so our network is out of scope."

"Only if it's a validated P2PE solution. Check that it's listed by PCI SSC."
