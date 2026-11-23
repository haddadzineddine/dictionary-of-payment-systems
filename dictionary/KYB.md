---
description: Know Your Business, the checks used to verify a company, its ownership and the people who control it.
---

KYB, or Know Your Business, is the process of verifying a business customer: that it legally exists, what it does, who owns it and who controls it. Banks, [acquirers](./Acquirer.md) and [payment facilitators](./Payment%20facilitator.md) run KYB before letting a company accept or move money, as part of their [AML](./AML.md) and risk controls.

The difficult part is identifying beneficial owners, the natural persons who ultimately own or control a company. FATF standards and Regulation (EU) 2024/1624 both require firms to identify beneficial owners and understand the ownership and control structure. In the US, FinCEN's customer due diligence rule sets beneficial ownership requirements for covered financial institutions, and FinCEN proposed changes to it in November 2026. Ownership thresholds and methods differ by jurisdiction.

| Check          | Question                               | Typical evidence                     |
| -------------- | -------------------------------------- | ------------------------------------ |
| Legal entity   | Does the company exist?                | Registry extract, tax number         |
| Business model | What does it actually sell?            | Website, invoices, description       |
| Ownership      | Who ultimately owns it?                | Shareholder register, group chart    |
| Control        | Who runs it?                           | Director list, officer details       |
| Individuals    | Are those people who they say?         | [KYC](./KYC.md) on owners and directors |
| Screening      | Is anyone restricted?                  | [Sanctions screening](./Sanctions%20screening.md) |

For a [merchant](./Merchant.md), KYB also covers commercial risk: [refund](./Refund.md) policy, delivery times and whether the product fits its [merchant category code](./Merchant%20category%20code.md).

The failure businesses feel is a hold on funds. Many platforms allow a new seller to begin processing after basic checks, then request full documents once volume grows. If the seller does not respond, or a new investor changes the ownership, the [payout](./Payout.md) can be paused until the review is complete.

Ownership and directors change, so records need periodic and event-driven review. Engineers should store ownership as a graph or linked records, since a flat field for "owner" cannot represent a chain of holding companies.

_Usage:_

"This seller's payout has been on hold since their funding round."

"The cap table changed. We need updated beneficial owner details before KYB can clear."
