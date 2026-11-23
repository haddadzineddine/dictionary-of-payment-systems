---
description: A check comparing a customer's billing postcode and street address with the card issuer's records for online payments.
---

Address verification, often called AVS after the Address Verification Service, is a check that compares the billing address a customer enters with the address held by their [issuer](./Issuer.md). It runs during a [card authorization](./Card%20authorization.md) for a [card-not-present transaction](./Card-not-present%20transaction.md). The issuer returns a result code, and the [merchant](./Merchant.md) decides what to do with it.

| Result                  | What it suggests                    | Common handling                          |
| ----------------------- | ----------------------------------- | ---------------------------------------- |
| Full match              | Address details agree               | Treat as a positive signal               |
| Postcode only           | Street differs or was not checked   | Weigh with other signals                 |
| Street only             | Postcode differs                    | Weigh with other signals                 |
| No match                | Neither agrees                      | Review or request more authentication    |
| Unavailable             | Issuer or region does not support it | Do not treat as a failure                |

Exact result codes vary by network and provider.

AVS is regional. Visa's rules require issuers to participate in listed regions and countries, including the US, Canada, Europe, Australia, New Zealand and Singapore, and added several Latin American countries effective October 2026. Those rules focus on postal code verification, with street address checked when present. Coverage elsewhere is limited, so a global rule that blocks every non-match will reject many valid international customers.

An AVS mismatch usually does not stop an approval on its own. An issuer can approve a payment with a failed address check, so the merchant holds an approved transaction and has to choose. If it rejects the order, it should send an [authorization reversal](./Authorization%20reversal.md). Otherwise the customer sees a pending [authorization hold](./Authorization%20hold.md) for an order that was refused.

False mismatches are common, because customers move house or abbreviate street names.

Treat AVS as one input to [risk scoring](./Risk%20scoring.md). It does not authenticate the [cardholder](./Cardholder.md), and a match does not provide the [liability shift](./Liability%20shift.md) that [3-D Secure](./3-D%20Secure.md) can.

_Usage:_

"We're rejecting a lot of UK orders on address mismatch."

"Stop hard-blocking on AVS. Use it as one risk signal and send a reversal when we do refuse."
