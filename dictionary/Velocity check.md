---
description: A fraud control that counts events per card, device, IP or account in a time window and reacts when a limit is exceeded.
---

A velocity check is a fraud control that counts how many times something happens within a time window and acts when the count exceeds a limit. In payments, it might count attempts per card in ten minutes, or the number of different cards used by one device in an hour. It is used against automated attacks such as [card testing](./Card%20testing.md) and [account takeover](./Account%20takeover.md).

A rule has four parts.

| Part   | Options                                                    |
| ------ | ---------------------------------------------------------- |
| Key    | Card fingerprint, device, IP, account, email, [BIN](./BIN.md) |
| Event  | Attempt, decline, approval, new card added, login, [refund](./Refund.md)  |
| Window | Minutes, hours or days                                     |
| Action | Allow, add friction, send to review, block                 |

Different keys catch different patterns.

| Pattern                       | Useful count                               |
| ----------------------------- | ------------------------------------------ |
| One card tried repeatedly     | Attempts per card                          |
| Many cards from one source    | Distinct cards per device, IP or session   |
| Stolen list spread across IPs | Declines per [merchant](./Merchant.md), overall or by BIN   |
| Reused accounts               | Failed logins per account or per source    |

Limits should be based on your own traffic, because a normal pattern for a ticketing site at launch time would look like an attack for a furniture store. Test rules in log-only mode first.

The common failure is blocking legitimate customers. Offices, universities and mobile carriers put many users behind one IP address, so a strict per-IP limit can stop everyone at that location. Combine keys, prefer a step-up such as [3-D Secure](./3-D%20Secure.md) over an outright block where possible.

Implementation has its own traps. A counter that reads and then writes separately can undercount under concurrency, so use an atomic increment in a store such as Redis. Avoid using a raw [PAN](./PAN.md) as a key, since that places the counter store in [PCI DSS](./PCI%20DSS.md) scope. Use the provider's card fingerprint or a token.

_Usage:_

"The whole university campus is getting blocked at checkout."

"Our IP velocity rule is too tight. Key it on device plus distinct cards instead."
