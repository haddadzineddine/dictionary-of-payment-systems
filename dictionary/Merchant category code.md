---
description: A four-digit code classifying a merchant's type of business, used for fees, card restrictions and risk rules.
---

A merchant category code (MCC) is a four-digit number that classifies a merchant's type of business, such as a grocery store, airline or software seller. ISO 18245 defines a set of these codes, and [card networks](./Card%20network.md) publish their own lists and assignment rules. Visa's Merchant Data Standards Manual says the MCC describes a merchant's primary business, based on annual sales volume.

The [acquirer](./Acquirer.md) or [payment service provider](./Payment%20service%20provider.md) normally assigns the code at onboarding. It then travels in each [card authorization](./Card%20authorization.md) and [clearing](./Clearing.md) record, where several parties use it.

| Party       | How it uses the MCC                                                 |
| ----------- | ------------------------------------------------------------------- |
| [Issuer](./Issuer.md) | Applies rewards, spending controls and block rules         |
| Network     | Applies category-specific rules and [interchange](./Interchange%20fee.md) programs |
| Acquirer    | Assesses merchant risk and pricing                                  |
| [Cardholder](./Cardholder.md) | Sees spending categories in a banking app                 |

An incorrect code can cause failures that look unrelated. A company card program may block some categories, so a business coded as gambling or money transfer can see declines from customers whose cards work elsewhere. A wrong MCC can also change the fees the merchant pays, or remove eligibility for a feature such as [incremental authorization](./Incremental%20authorization.md), which networks often limit by category.

MCC is different from a product category in your own catalogue. It describes the business as a whole, so one transaction for a single item does not get its own code. A merchant with distinct lines of business may need separate merchant IDs with separate MCCs, depending on network rules.

Deliberately using a misleading code to obtain lower fees or avoid a restricted category is a rule violation, and it can lead to network penalties passed on by the acquirer or to closure of the [merchant account](./Merchant%20account.md). If the business changes, ask the acquirer to review the code.

_Usage:_

"Corporate cards keep getting declined on our site, but only corporate cards."

"We're coded under a restricted MCC. Ask the acquirer to review our classification."
