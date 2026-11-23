---
description: Charging a customer automatically on a schedule, using a saved card, bank mandate or local recurring rail.
---

Recurring billing is the process of charging a customer automatically at regular intervals, such as monthly for a subscription. A billing system determines what is due and creates a payment on an underlying method, which sets the rules for authentication, notice and failure.

| Method                  | Permission                 | Typical failure signal        |
| ----------------------- | -------------------------- | ----------------------------- |
| Card                    | [Stored credential](./Stored%20credential.md), charged as a [merchant-initiated transaction](./Merchant-initiated%20transaction.md) | Immediate decline |
| [SEPA Direct Debit](./SEPA%20Direct%20Debit.md)       | [Direct debit mandate](./Direct%20debit%20mandate.md)       | Later return or refund        |
| US [ACH](./ACH.md) debit            | Authorization under Nacha rules | Later [payment return](./Payment%20return.md)     |
| [UPI](./UPI.md) AutoPay (India)     | Registered e-mandate       | Mandate or debit failure      |
| [Pix](./Pix.md) Automático (Brazil) | Prior payer authorization  | Scheduled payment failure     |

Rules differ by market. India's E-mandate Framework, 2026, from the Reserve Bank of India, generally requires a notification before each recurring debit on cards, prepaid instruments and UPI, and additional authentication above set amounts. Consumer rules on renewal notices and cancellation also vary by market.

Recurring billing differs from a saved card used for one-click checkout, where the customer starts each payment. It also differs from [dunning](./Dunning.md), which handles what happens after a recurring payment fails.

A scheduler rerun after a crash can bill the same period twice. To prevent this, use an idempotency key (a unique value marking one logical charge) built from the subscription ID and billing period, and enforce it with a unique constraint. Date arithmetic also causes errors: adding one month to 31 January has no obvious answer, so store a fixed billing anchor day and clamp it to the month's length. Mid-cycle plan changes need explicit proration rules, using integer [minor units](./Minor%20unit.md) and a defined rounding direction.

Expired cards are the main cause of unintended cancellation. An [account updater](./Account%20updater.md) reduces these, and dunning recovers some of the remainder.

_Usage:_

"Some customers were billed twice on the first of the month."

"The recurring billing job restarted mid-run. Key each charge on subscription and period so a rerun can't duplicate it."
