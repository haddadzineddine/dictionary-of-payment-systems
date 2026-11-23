---
description: Regulated or standardised access for authorised third parties to bank account data and payment initiation, with customer consent.
---

Open banking is a framework that lets authorised third parties, with a customer's consent, read bank account data or initiate payments from that account through the bank's interfaces. An account information provider reads balances and transactions. A payment initiation provider starts a payment from the customer's account.

The legal basis differs by country:

| Jurisdiction | Basis                                  | Status to check                                         |
| ------------ | -------------------------------------- | ------------------------------------------------------- |
| EU           | [PSD2](./PSD2.md)                                   | PSD3 and a Payment Services Regulation were provisionally agreed in November 2025; check publication and application dates |
| UK           | 2017 Competition and Markets Authority order for the largest banks | Long-term framework under the Data (Use and Access) Act 2025 is still being put in place |
| US           | Consumer Financial Protection Bureau Section 1033 rule | The 2024 rule is under agency reconsideration, and compliance dates have been in flux |
| Brazil       | Open Finance under Banco Central do Brasil rules | Operating, with rules that continue to develop |

Open banking differs from [pay by bank](./Pay%20by%20bank.md), which is one product built on top of it. It also differs from screen scraping, where a service logs in with the customer's credentials and reads web pages. Regulated interfaces use consent and scoped access, so the third party never receives the banking password.

Consent is the most common operational problem. Access can expire or need renewed customer authentication, depending on the regime and the bank. A lending or accounting product then stops receiving transactions, and users see stale balances with no obvious error. Bank interfaces also vary in quality, so one bank's outage can break a segment of customers.

Track consent expiry and prompt users before it lapses. Monitor success rates per bank, and show the last successful sync time so a stale balance is visible. Check whether your activity requires authorisation or can run through a licensed provider.

_Usage:_

"Half our users' bank feeds stopped updating last night."

"Their open banking consents expired. Prompt them to reauthenticate, and warn them before expiry from now on."
