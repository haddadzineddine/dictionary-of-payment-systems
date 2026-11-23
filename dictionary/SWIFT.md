---
description: The member-owned network that sends payment messages between banks without itself holding or moving their funds.
---

SWIFT, the Society for Worldwide Interbank Financial Telecommunication, now styled Swift, is a member-owned cooperative based in Belgium that runs a secure messaging network for financial institutions. It carries payment instructions between banks. It does not hold customer accounts or settle funds. The money moves through accounts that banks hold with each other, known as [correspondent banking](./Correspondent%20banking.md), or through a [settlement](./Settlement.md) system such as an [RTGS](./RTGS.md).

A "Swift code" is a Business Identifier Code, or BIC, defined by ISO 9362. It identifies a bank or branch. It is different from an [IBAN](./IBAN.md), which identifies a customer account.

| Layer       | Example                         | Job                               |
| ----------- | ------------------------------- | --------------------------------- |
| Identifier  | BIC                             | Names the institution             |
| Message     | `pacs.008`, formerly MT103      | Describes the payment             |
| Network     | Swift                           | Delivers the message              |
| Funds       | [Nostro account](./Nostro%20account.md) or RTGS          | Moves the value                   |

The message format has changed. For cross-border payment instructions between financial institutions, the coexistence period for legacy MT messages and [ISO 20022](./ISO%2020022.md) ended on 22 November 2025. Swift had also planned to remove fully unstructured postal addresses in November 2026. In 2026 it agreed to extend that timeline for payment messages after community requests, so check its current roadmap before relying on a date.

The usual confusion appears when a business receives a "Swift copy" as proof of payment. That document shows an instruction was sent. It does not prove the beneficiary was credited. A payment can still be held by an intermediary for compliance review, rejected for bad details, or arrive short because a bank in the chain deducted a fee. To trace one, ask the sending bank for its Unique End-to-end Transaction Reference (UETR), which banks use to track the payment across the chain.

_Usage:_

"The supplier says they never got the money, but we have the Swift confirmation."

"That only proves our bank sent the message. Give them the UETR and ask the bank to trace it."
