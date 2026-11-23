---
description: A card payment the cardholder actively starts and takes part in, even when using a saved card.
---

A customer-initiated transaction, or CIT, is a card payment in which the [cardholder](./Cardholder.md) is present in the flow and actively takes part, for example by pressing Pay on a website or in an app. Visa calls these cardholder-initiated transactions. The card can be newly entered or saved. What makes it a CIT is the customer's involvement at that moment.

| Question                       | CIT                         | [Merchant-initiated transaction](./Merchant-initiated%20transaction.md)       |
| ------------------------------ | --------------------------- | ------------------------------------ |
| Who starts it?                 | Cardholder                  | [Merchant](./Merchant.md), under a prior agreement    |
| Is the customer in session?    | Yes                         | No                                   |
| Can they complete a challenge? | Yes                         | No                                   |
| EEA and UK authentication      | [Strong customer authentication](./Strong%20customer%20authentication.md) unless exempt | Generally outside it when set up correctly |

The most common confusion is treating any saved-card payment as merchant-initiated. A returning customer who clicks Buy using a saved card is still making a CIT. In the EEA and UK, that payment falls under strong customer authentication unless an [SCA exemption](./SCA%20exemption.md) applies, and the European Banking Authority has said that card payments initiated by the payer through the payee are in scope.

A CIT also normally sets up a [stored credential](./Stored%20credential.md). The first payment carries the authentication and consent, and its [network transaction ID](./Network%20transaction%20ID.md) anchors later merchant-initiated payments.

The failure appears when an engineer marks one-click checkout as merchant-initiated to avoid the extra authentication step. [Issuers](./Issuer.md) can decline these payments, networks can treat the flag as misuse, and the merchant may lose [3-D Secure](./3-D%20Secure.md) liability protection. The reverse error also occurs, when an off-session renewal is sent as a CIT and fails because nobody is there to complete a challenge.

Set the initiator from what the user is doing in that request, rather than from whether a card is saved.

_Usage:_

"Can we flag one-click purchases as MIT to skip 3-D Secure?"

"No. The customer clicked Buy, so it's a customer-initiated transaction and needs SCA unless an exemption applies."
