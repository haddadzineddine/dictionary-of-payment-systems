---
description: Checking customers and payments against government sanctions lists to stop prohibited dealings.
---

Sanctions screening is the process of checking customers, counterparties and payments against government sanctions lists to avoid prohibited dealings. Common sources include the US Treasury's Office of Foreign Assets Control (OFAC), the EU consolidated list, the UK's sanctions list and United Nations lists. Which regimes bind a firm depends on its location, nationality and partners.

Screening usually happens at several points.

| Point       | What is checked                                         | Example result                     |
| ----------- | ------------------------------------------------------- | ---------------------------------- |
| Onboarding  | Customer, directors and beneficial owners | Account opening is paused          |
| Ongoing     | Existing customers against updated lists                | Account is restricted              |
| Transaction | Payer, payee, banks, countries and payment text         | Payment is held for review         |

[AML](./AML.md) is largely risk-based and focuses on suspicious behaviour. A sanctions prohibition can apply regardless of behaviour, and OFAC can impose civil penalties on a strict liability basis, meaning a firm can be liable even if it did not know a transaction was prohibited. Some regimes extend to entities owned or controlled by a listed person, so combine screening with [KYB](./KYB.md) ownership data.

Under US rules, some property must be blocked, meaning frozen and reported, while other prohibited transactions are rejected and returned. Returning funds that should have been blocked can itself be a violation. Compliance teams, and not application code, should decide which outcome applies.

The main operational problem is false positives. Names are transliterated in different ways and many people share them, so screening uses fuzzy matching. A customer named similarly to a listed person may find a [payout](./Payout.md) or payment held until an analyst clears the alert.

Engineers should rescreen when lists change, version the list used for each decision, and fail closed if the screening service is unavailable on flows that require it. Record who cleared each alert and why.

_Usage:_

"Why is this payout stuck in review? The seller's been with us for years."

"Their name partly matched a new sanctions listing. Compliance has to clear the alert before it can go out."
