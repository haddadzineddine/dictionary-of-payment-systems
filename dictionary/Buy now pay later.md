---
description: Short-term credit at checkout that splits a purchase into instalments, with rules that depend on the jurisdiction.
---

Buy now pay later, or BNPL, is a form of short-term credit offered at checkout that lets a customer split a purchase into instalments or defer payment. A BNPL provider typically pays the [merchant](./Merchant.md) up front, less a fee, and then collects repayments from the customer. Some plans charge no interest and may charge late fees, while longer plans can charge interest. Terms vary by provider and country.

| Party    | Role                                                   |
| -------- | ------------------------------------------------------ |
| Customer | Agrees a credit plan and repays on schedule            |
| Provider | Assesses the customer, pays the merchant, collects     |
| Merchant | Receives funds, pays a fee, handles returns and [refunds](./Refund.md) |

BNPL differs from a credit card in that each purchase is usually a separate loan with a fixed schedule, not a revolving limit.

The product depends heavily on regulation, which has been changing:

| Jurisdiction | Position                                                                                      |
| ------------ | --------------------------------------------------------------------------------------------- |
| UK           | The Financial Conduct Authority began regulating deferred payment credit on 15 July 2026      |
| EU           | Consumer Credit Directive (EU) 2023/2225 applies from 20 November 2026 and covers BNPL, with limited exclusions |
| US           | The Consumer Financial Protection Bureau withdrew its 2024 BNPL interpretive rule in May 2025. Federal and state lending laws may still apply |

Merchants offering BNPL should confirm the required disclosures and marketing rules with the provider and legal counsel. This entry describes the product and is not financial advice.

The operational failure usually involves returns. A customer returns one item from a split order, but the instalments do not update until the merchant sends the refund to the provider. The customer sees a payment still due on goods they sent back and contacts support. Send partial refunds through the provider's API against the original order, and keep the provider's plan ID in your payment record.

_Usage:_

"A customer returned the shoes but is still being asked for instalments."

"We never sent the refund to the buy now pay later provider. Post it against the original order so the plan recalculates."
