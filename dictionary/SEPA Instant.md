---
description: The European Payments Council's euro instant credit transfer scheme, running around the clock under the Instant Payments Regulation.
---

SEPA Instant, formally the SEPA Instant Credit Transfer or SCT Inst, is a euro credit transfer scheme that runs 24 hours a day on every day of the year. The European Payments Council publishes the rulebook. Regulation (EU) 2024/886, the Instant Payments Regulation, requires funds to reach the payee within 10 seconds of the order being received, and it requires EU providers that offer euro credit transfers to support instant ones.

The regulation phases in by location and firm type, according to the European Central Bank's published timetable:

| Obligation           | Euro area        | Non-euro EU     |
| -------------------- | ---------------- | --------------- |
| Receive instant      | 9 January 2025   | 9 January 2027  |
| Send instant         | 9 October 2025   | 9 July 2027     |
| Verification of payee | 9 October 2025  | 9 July 2027     |

Payment and e-money institutions have separate dates, starting 9 April 2027. Instant transfers may not cost more than the same provider's comparable standard transfers. Providers must also check their customers against EU targeted financial sanctions at least daily, in place of screening each instant transfer against those EU measures.

SEPA Instant differs from a [SEPA Credit Transfer](./SEPA%20Credit%20Transfer.md) in speed and availability, but both are credit pushes that the payer starts. Completed transfers cannot be reversed by the payer, so a misdirected payment relies on a recall the receiver can refuse.

For engineers, the short deadline changes failure handling. A client timeout does not prove that a transfer failed, because the provider may have completed it just as the connection dropped. Treat it as an [unknown payment outcome](./Unknown%20payment%20outcome.md) and query the status using your end-to-end reference before sending again. Also, release goods only on a confirmed credit, not on the customer's "sent" screen. Speed also helps fraudsters, since stolen money can be moved onward within seconds.

_Usage:_

"The transfer API timed out. Should I resend the SEPA Instant payment?"

"Not yet. Query the status with the end-to-end ID, since it may already have landed."
