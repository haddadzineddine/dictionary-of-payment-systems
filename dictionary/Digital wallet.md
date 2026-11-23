---
description: An app or account that stores payment credentials or a balance, so a customer can pay without entering card details.
---

A digital wallet is an app or online account that stores a customer's payment credentials, a balance, or both, and uses them to make payments. The type determines who holds the money and which rail carries the payment.

| Type          | Example               | How it pays                                             | Holds funds? |
| ------------- | --------------------- | ------------------------------------------------------- | ------------ |
| Pass-through  | Apple Pay, Google Pay | Passes a card credential, often a [network token](./Network%20token.md), to the [merchant](./Merchant.md) | No |
| Staged        | PayPal paying with a linked card | Wallet charges the funding source, then pays the merchant | Sometimes |
| Stored value  | Balance in a wallet account | Spends a balance held by the provider              | Yes          |

In a pass-through wallet, the payment is still a card payment. The [issuer](./Issuer.md) approves it, the merchant's [acquirer](./Acquirer.md) processes it, and the usual card fees and [chargeback](./Chargeback.md) rules apply. A wallet is therefore not a rail in its own right. A staged or stored-value wallet is different, because the wallet provider is a party to the payment, and holding customer balances generally requires a licence such as e-money authorisation, with duties such as [safeguarding](./Safeguarding.md).

Device wallets replace the card number with a device-specific token and authenticate the customer with a biometric or passcode. Because of this, the last four digits shown in the wallet may differ from those printed on the physical card. A common support ticket follows: a customer gives the digits from their plastic card, and the agent cannot find the order. Search by the token's last four digits, the amount and the date, or use the provider's transaction reference.

Expect a saved wallet token to stop working when a customer changes device or removes the card. Store the wallet type separately for reporting, since [authorization rates](./Authorization%20rate.md) and fraud patterns can differ from manually entered cards.

_Usage:_

"Support can't find this order using the customer's card number."

"They paid with a digital wallet, so the last four belong to the device token. Search by amount and date."
