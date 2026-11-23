---
description: Real-time gross settlement, where a central bank settles each interbank payment individually and with finality.
---

Real-time gross [settlement](./Settlement.md), or RTGS, is a type of settlement system in which interbank payments settle one at a time, as soon as they are processed, usually across accounts at a central bank. "Gross" means each payment settles for its full amount and is not netted against others. Settlement in central bank money removes the risk that the paying bank fails before settling.

Major examples are [Fedwire](./Fedwire.md) in the US, T2 in the euro area and the Bank of England's RTGS service, which settles CHAPS payments in the UK.

The main alternative is deferred net settlement, where a system adds up what participants owe each other and settles only the difference at set times:

| Property          | RTGS                                | Deferred net settlement             |
| ----------------- | ----------------------------------- | ----------------------------------- |
| Settlement        | Each payment, in full               | Net positions, in cycles            |
| Liquidity needed  | Higher                              | Lower                               |
| Settlement risk   | Low, because settlement is immediate | Exists between cycles unless covered |
| Example           | Fedwire, T2, CHAPS                  | [Faster Payments](./Faster%20Payments.md)                     |

RTGS is often confused with instant payments. RTGS describes how banks settle. Instant payments describe what the customer experiences. Faster Payments credits customers quickly but settles between banks on a net basis three times per business day, according to the Bank of England, with participants prefunding their exposure. A traditional RTGS can also close overnight and on weekends, while a customer-facing instant service runs all the time.

Because every payment needs its full value, a bank must hold enough liquidity during the day. If it does not, the system may queue the payment until incoming funds arrive. A treasury team sees this as a high-value payment stuck in "queued" near a cut-off. Banks manage it with intraday credit, payment scheduling and liquidity-saving features in the system.

_Usage:_

"Why is this CHAPS payment still queued?"

"Our settlement account is short on intraday liquidity. RTGS needs the full amount, so treasury has to fund it first."
