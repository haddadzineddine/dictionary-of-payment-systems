---
description: The Federal Reserve's real-time gross settlement service for final, typically high-value US dollar payments.
---

Fedwire, formally the Fedwire Funds Service, is a real-time gross [settlement](./Settlement.md) system operated by the Federal Reserve Banks. A participating institution sends a payment order, and the Reserve Banks settle it individually by debiting the sender's Federal Reserve account and crediting the receiver's. Once settled, the payment is final and irrevocable. Businesses know it as a "wire", and it is typically used for large or time-critical payments such as property closings and interbank transfers.

| Rail    | Operator                       | Processing            | Can the money come back automatically? |
| ------- | ------------------------------ | --------------------- | ------------------- |
| Fedwire | Federal Reserve Banks          | Individual, business hours | No, it is final |
| [ACH](./ACH.md)     | FedACH and EPN                 | Batched               | Yes, through returns |
| [FedNow](./FedNow.md)  | Federal Reserve Banks          | Individual, 24x7x365  | No, it is final     |

Fedwire adopted [ISO 20022](./ISO%2020022.md) on 14 July 2025, replacing its proprietary format. Its operating day runs on business days, so a payment instructed late may wait until the next one. In October 2025, the Federal Reserve Board announced that the service will expand to 22 hours a day, six days a week, with implementation planned for 2028 or 2029. Check the published schedule for current hours and cut-offs, because banks often set earlier internal deadlines for their customers.

Finality makes wire fraud hard to recover from. In a common scam, a criminal impersonates a supplier by email and sends new bank details. The finance team pays, the funds settle, and the sending bank can only ask the receiving bank to return them. The receiving bank does not have to agree, and the account may already be empty.

Confirm any change of payment details through a known phone number, require a second approver on high-value wires, and report suspected fraud to your bank immediately.

_Usage:_

"Can we pull back the wire we sent to the new supplier account?"

"Fedwire payments are final. Call the bank now and ask for a recall, but the receiving bank has to agree."
