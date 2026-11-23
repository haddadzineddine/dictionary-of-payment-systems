---
description: The Clearing House's private US instant payment network, settling final credit transfers around the clock from a prefunded account.
---

The RTP network is a US instant payment system operated by The Clearing House, a company owned by large banks. It launched in 2017 and runs around the clock. Participating institutions send credit transfers using [ISO 20022](./ISO%2020022.md) messages, and receivers can have the funds within seconds. Payments on the network are final.

[Settlement](./Settlement.md) relies on a prefunded joint account held at the Federal Reserve Bank of New York. Participants fund their positions in that account, and each payment adjusts their balances on The Clearing House's records as it is processed. This model lets the network settle while traditional wire systems are closed.

| Property     | RTP network       | [FedNow](./FedNow.md)                | [ACH](./ACH.md)                 | [Fedwire](./Fedwire.md)             |
| ------------ | ----------------- | --------------------- | ------------------- | ------------------- |
| Operator     | The Clearing House | Federal Reserve Banks | Nacha rules, two operators | Federal Reserve Banks |
| Availability | Continuous        | Continuous            | Processing windows  | Business days       |
| Direction    | Credit push       | Credit push           | Credit and debit    | Credit push         |
| Finality     | Final             | Final                 | Returns possible    | Final               |

The RTP network and FedNow are separate. A bank on one is not automatically reachable through the other, which is the main point of confusion for teams adding instant [payouts](./Payout.md) in the US. The network also carries Request for Payment messages, which ask a payer to approve a push. A request is not a debit, so nothing moves until the payer agrees.

The failure engineers meet is a payout that works in testing and then fails for a portion of real customers because their bank does not receive RTP payments. Check eligibility for each routing number before promising instant delivery, and keep a fallback rail. Because payments are final, a payout to a wrong account depends on the recipient's bank and the recipient agreeing to send it back. Limits are set by the network and by each bank, and they change, so confirm them with your provider.

_Usage:_

"Can we promise instant payouts to every US account?"

"No. The RTP network doesn't reach every bank, so check the routing number and fall back to ACH."
