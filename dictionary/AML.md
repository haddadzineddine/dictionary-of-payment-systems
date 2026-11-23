---
description: Anti-money laundering, the laws and controls for detecting and reporting attempts to disguise the origin of criminal funds.
---

AML, or anti-money laundering, is the set of laws and internal controls that regulated firms use to detect, prevent and report attempts to pass off criminal money as legitimate. The FATF Recommendations set the international standard, and each country turns them into binding law.

A program usually has these parts.

| Control                 | What it does                                                         |
| ----------------------- | -------------------------------------------------------------------- |
| Risk assessment         | Identifies which products, customers and countries carry most risk   |
| Customer due diligence  | [KYC](./KYC.md) for people and [KYB](./KYB.md) for businesses        |
| Transaction monitoring  | Flags activity that does not fit the customer's profile              |
| Investigation           | Analysts review alerts and record decisions                          |
| Reporting               | Files suspicious activity reports with the national authority        |
| Record keeping          | Retains evidence for a legally required period                       |

AML differs from fraud prevention, though the tools overlap. Fraud controls protect the firm and its customers from being robbed. AML looks for customers who may be successfully moving their own illicit funds, where nobody complains. [Sanctions screening](./Sanctions%20screening.md) is also distinct: it checks whether dealing with a party is prohibited at all.

Warning patterns include activity far above a customer's stated business, funds moving in and immediately back out, and payments split to stay under reporting limits. A [merchant](./Merchant.md) account processing payments unrelated to its declared business can indicate transaction laundering, where one business runs card payments for another, undisclosed one.

The symptom for customers is an unexplained restriction. Support cannot say why, and this is often deliberate. Laws in many jurisdictions prohibit "tipping off", meaning telling someone that a suspicious activity report has been filed or is being considered. Engineers should therefore keep case details out of customer-facing logs and support tools, and give agents an approved neutral script.

Record each alert, the analyst's decision and the reasoning, since regulators may ask to see that trail.

_Usage:_

"A customer is demanding to know why their account is restricted. What can I say?"

"Use the standard compliance script. Don't speculate, and don't mention any AML review."
