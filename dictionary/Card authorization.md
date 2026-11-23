---
description: A real-time request asking the card issuer to approve a payment and usually reserve funds, without moving money yet.
---

A card authorization is a real-time request asking the [issuer](./Issuer.md) whether a card payment can go ahead. If approved, the issuer usually reserves the amount with an [authorization hold](./Authorization%20hold.md). In the usual dual-message card flow, no money moves at this step.

| Step | Who                                 | What happens                                         |
| ---- | ----------------------------------- | ---------------------------------------------------- |
| 1    | [Merchant](./Merchant.md)           | Sends amount and card details through its provider   |
| 2    | [Acquirer](./Acquirer.md)           | Formats the request and forwards it to the network   |
| 3    | [Card network](./Card%20network.md) | Routes the request to the issuer                     |
| 4    | Issuer                              | Checks status, funds and risk, then responds         |
| 5    | Merchant                            | Receives an approval or a [decline code](./Decline%20code.md) |

Authorization is the first of four stages that people often merge into "the payment".

| Stage            | Question it answers                     | Money moves?             |
| ---------------- | --------------------------------------- | ------------------------ |
| Authorization    | Will the issuer approve this?           | No, funds are reserved   |
| [Capture](./Capture.md)    | Does the merchant want to take payment? | No                       |
| [Clearing](./Clearing.md)   | What is the final transaction record?   | No, amounts are calculated |
| [Settlement](./Settlement.md) | Who pays whom?                          | Yes, between institutions |

Treating an approval as completed payment causes a familiar bug. An order system marks a sale "paid" after authorization, the capture job later fails, and the goods ship with no money collected. The approval eventually expires and the hold disappears. Record authorized and captured as separate states in the [payment state machine](./Payment%20state%20machine.md).

Some transactions combine stages. A "sale" API call authorizes and captures together. In a single-message system, common for PIN debit, one message carries both the authorization and the financial transaction.

How long an approval stays valid varies by network, region and transaction type. Mastercard, for example, distinguishes preauthorizations, final and undefined authorizations. A valid approval also does not prove that the real [cardholder](./Cardholder.md) made the purchase, so it does not protect the merchant from a later fraud [chargeback](./Chargeback.md).

_Usage:_

"The order says paid, but finance can't find the money."

"It was only authorized. The capture job failed, so nothing ever went to clearing."
