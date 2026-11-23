---
description: An arrangement where one bank holds an account at another to make payments in a currency or country it cannot reach directly.
---

Correspondent banking is an arrangement in which one bank, the correspondent, holds an account for another bank, the respondent, and makes or receives payments on its behalf. A bank needs this when it has no direct access to the payment system of a currency. A small bank in France, for example, usually cannot settle US dollars in [Fedwire](./Fedwire.md), so it holds dollars at a US bank that can.

A cross-border payment may pass through several banks:

| Step | Who                    | What happens                                       |
| ---- | ---------------------- | -------------------------------------------------- |
| 1    | Payer's bank           | Debits the payer and sends the instruction         |
| 2    | Its correspondent      | Debits the payer's bank's account and screens the payment |
| 3    | Intermediary, if any   | Passes value toward the beneficiary's bank         |
| 4    | Beneficiary's bank     | Receives value and credits the beneficiary         |

Correspondent banking is often confused with [SWIFT](./SWIFT.md). Swift carries the messages between these banks. The correspondent accounts, or a [settlement](./Settlement.md) system such as an [RTGS](./RTGS.md), carry the value. The account is called a [nostro account](./Nostro%20account.md) by the bank that owns it and a vostro account by the bank that holds it.

Each bank in the chain performs its own compliance checks, including [sanctions screening](./Sanctions%20screening.md) and [AML](./AML.md) review, and may charge a fee. This produces two common complaints. The first is a short payment: an invoice for 10,000 arrives as 9,965 because an intermediary deducted its charge. The sender can reduce this by choosing a charge option, where `OUR` means the sender pays, `SHA` means costs are shared and `BEN` means the beneficiary pays, though not every bank honours it fully. The second is a payment that stops for days while a bank asks about its purpose or parties.

Correspondents may also withdraw from relationships they consider high-risk, known as de-risking.

_Usage:_

"The supplier received 35 dollars less than we sent."

"An intermediary in the correspondent banking chain took its fee. Send it as `OUR` next time, and gross up if needed."
