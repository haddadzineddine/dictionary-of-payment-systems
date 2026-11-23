---
description: The Federal Reserve's around-the-clock US instant payment service for final, individually settled credit transfers.
---

FedNow is an instant payment service operated by the Federal Reserve Banks, launched in July 2023. It runs 24 hours a day, every day of the year. A participating bank or credit union sends a credit transfer, and the service settles it individually across Federal Reserve master accounts, or through a correspondent acting for the institution. The receiver can have the funds within seconds, and the payment is final.

| Step | Who            | What happens                                 |
| ---- | -------------- | -------------------------------------------- |
| 1    | Payer's bank   | Validates the payment and sends an [ISO 20022](./ISO%2020022.md) message |
| 2    | FedNow         | Checks it and forwards it to the receiving bank |
| 3    | Receiver's bank | Accepts or rejects                          |
| 4    | FedNow         | Settles and notifies both banks              |
| 5    | Receiver's bank | Makes the funds available                   |

FedNow is often confused with [Fedwire](./Fedwire.md) because both belong to the Federal Reserve. Fedwire is the established high-value wire service with a limited operating day. FedNow is designed for continuous, everyday instant payments. It is also separate from the [RTP network](./RTP%20network.md), a private-sector instant system run by The Clearing House. A bank can join either, both or neither, and the two do not automatically exchange payments.

FedNow is a credit push. The payer's institution sends the money, so the service cannot be used as a card-style pull. Request-for-payment messages exist, but the payer still has to approve the payment. The Federal Reserve sets a network transaction limit, and participants may set lower ones, so check current values with your bank.

The failure teams usually meet is reachability. A checkout or [payout](./Payout.md) offers "instant", but the recipient's bank is not enabled to receive FedNow, or it only receives and cannot send. Check reachability by routing number first, and fall back to another rail with the customer told about the slower timing.

_Usage:_

"Why did this instant payout fail for only some customers?"

"Their banks aren't enabled for FedNow. Check reachability by routing number and fall back to [ACH](./ACH.md)."
