---
description: India's real-time account-to-account payment system, operated by NPCI under Reserve Bank of India oversight.
---

UPI, the Unified Payments Interface, is India's real-time payment system for moving money between bank accounts through mobile apps. The National Payments Corporation of India (NPCI) operates it, under the oversight of the Reserve Bank of India. Banks and licensed third-party apps connect to it, so customers of different banks can pay each other.

| Element           | What it is                                                |
| ----------------- | --------------------------------------------------------- |
| UPI ID            | A virtual address such as `name@bank`, hiding account details |
| UPI PIN           | A secret the customer enters to authorise a debit         |
| PSP app           | The app the customer uses to send or approve a payment    |
| [QR code payment](./QR%20code%20payment.md)   | A [merchant](./Merchant.md) code the customer scans to pay                 |
| AutoPay           | A registered mandate for recurring debits                 |
| UPI Lite          | An on-device balance for small payments without a PIN     |

UPI is the rail, and consumer apps are built on it. It differs from a card payment because funds normally come straight from a bank account, although NPCI also supports RuPay credit cards and pre-sanctioned credit lines on UPI.

NPCI's rules change regularly. Its consolidated circular of September 2026 says the collect function must not be available for person-to-person payments. For recurring payments, the Reserve Bank's E-mandate Framework, 2026 covers registration, additional authentication and pre-debit notification. Limits and fees are set by NPCI, the Reserve Bank and banks, so confirm them at the source.

The typical failure is a payment stuck as pending. The customer's bank has debited the account, but the merchant has received no confirmation, and the customer pays again. Treat pending as an unknown outcome. Query the transaction status with your reference before offering a retry.

_Usage:_

"The customer was debited, but the order shows unpaid."

"The UPI transaction is still pending. Run a status check on our reference before letting them pay again."
