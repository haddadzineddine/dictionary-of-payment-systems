---
description: The euro pull-payment scheme in which a creditor collects from a debtor's account under a signed mandate.
---

SEPA Direct Debit, or SDD, is a European Payments Council scheme that lets a creditor collect euro payments from a debtor's account under a [direct debit mandate](./Direct%20debit%20mandate.md). There are two schemes. SDD Core is available to consumers and businesses. SDD B2B is for business debtors only and needs the debtor bank to confirm the mandate.

| Step | Who           | What happens                                              |
| ---- | ------------- | --------------------------------------------------------- |
| 1    | Creditor      | Obtains the mandate with its creditor identifier and a unique reference |
| 2    | Creditor      | Gives the debtor advance notice of the amount and date    |
| 3    | Creditor's PSP | Submits the collection                                   |
| 4    | Debtor's PSP  | Debits the account, or rejects or returns the collection  |
| 5    | Debtor        | May request a refund under the scheme rules               |

The refund right is where SDD differs most from a card payment. Under the current SDD Core rulebook, a debtor can get a no-questions-asked refund within eight weeks of the debit, and can claim for an unauthorised collection for up to 13 months. SDD B2B has no equivalent refund right for an authorised collection. These periods come from the rulebook and can change.

An SDD refund is also different from a [chargeback](./Chargeback.md). Card disputes have a [representment](./Representment.md) stage where the [merchant](./Merchant.md) can contest with evidence. In the eight-week window, the creditor cannot block the refund through the scheme and must pursue any valid debt separately.

The symptom is revenue reversing weeks after delivery, with a reason code such as `MD06`, while a failed collection may show `AM04` for insufficient funds. Treat each collection as provisional in your [ledger](./Ledger.md), post reversals as new entries, and keep the mandate available, because the debtor's bank can request a copy for an unauthorised claim.

_Usage:_

"A customer got their money back seven weeks after we delivered."

"That's an SDD Core refund, `MD06`. We can't contest it in the scheme, so finance has to invoice them again."
