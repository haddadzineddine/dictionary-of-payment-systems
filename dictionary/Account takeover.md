---
description: Fraud in which a criminal gains access to a real customer's account and uses its saved payment methods or balance.
---

Account takeover (ATO) is fraud in which a criminal gains access to a genuine customer's account and acts as that customer. In a payments context, the attacker uses saved cards, spends a stored balance, redirects a [payout](./Payout.md), or changes contact details to lock out the owner. Access commonly comes from reused passwords leaked elsewhere, phishing or malware on the customer's device.

ATO differs from stolen-card fraud. With a stolen card, the fraudster brings a card to a new account. With ATO, the account, the card on file and the purchase history all look legitimate, so payment signals such as a passing [CVV](./CVV.md) or a known card reveal little. Detection has to focus on the session and the account's behaviour.

| Warning sign                                       | Why it matters                            |
| -------------------------------------------------- | ----------------------------------------- |
| Login from a new device or unusual location        | Possible credential use                   |
| Many failed logins across accounts from one source | Automated password testing against the site |
| Password reset followed quickly by a purchase      | Attacker securing access                  |
| Email, phone or payout details changed             | Locks out the owner or redirects funds    |

The real [cardholder](./Cardholder.md) then disputes the charges, so the [merchant](./Merchant.md) receives a fraud [chargeback](./Chargeback.md) on what looked like a loyal customer's order.

| Control                                            | Purpose                                 |
| -------------------------------------------------- | --------------------------------------- |
| Multi-factor authentication                        | Stolen password alone is not enough     |
| Breached-password checks                           | Blocks known leaked credentials         |
| Login rate limits and [velocity checks](./Velocity%20check.md) | Slows automated attempts    |
| Step-up on sensitive changes                       | Reconfirms before payout or email edits |
| Notify the old email or phone of changes           | Lets the real owner react               |
| Delay payouts after bank detail changes            | Gives time to catch a redirect          |

When ATO is confirmed, revoke all sessions and API tokens, reset credentials, reverse attacker changes, and review recent orders and payouts.

_Usage:_

"This customer's been with us five years, and suddenly three orders shipped to a new address."

"Password reset an hour earlier from a new device. Looks like account takeover, so lock it and hold the orders."
