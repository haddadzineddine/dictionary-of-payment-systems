# Payment Systems Dictionary

A plain-English dictionary of how money moves: card networks, transaction lifecycles, compliance, fraud and disputes, fees, bank rails, payment methods and payments engineering.

Why does a refunded customer still see a pending charge? Why did the customer pay twice after a timeout? Why does the payout not match the sales report?

Each of these has a short explanation once you know the right words. Entries define the term, describe the failure it explains where there is one, and end with a short example of engineers using it.

This is general education, not legal, financial or compliance advice. Rules, fees and deadlines vary by network, country and provider, and they change, so confirm them with the relevant source before relying on them.

---

## Table of contents

- **[Section 1 — Participants](#section-1--participants)**
  - [Cardholder](#cardholder)
  - [Merchant](#merchant)
  - [Issuer](#issuer)
  - [Acquirer](#acquirer)
  - [Card network](#card-network)
  - [Four-party model](#four-party-model)
  - [Payment service provider](#payment-service-provider)
  - [Payment gateway](#payment-gateway)
  - [Payment processor](#payment-processor)
  - [Payment facilitator](#payment-facilitator)
  - [Merchant of record](#merchant-of-record)
  - [Merchant account](#merchant-account)
  - [Sponsor bank](#sponsor-bank)
- **[Section 2 — Card Transaction Lifecycle](#section-2--card-transaction-lifecycle)**
  - [Card authorization](#card-authorization)
  - [Authorization hold](#authorization-hold)
  - [Capture](#capture)
  - [Partial capture](#partial-capture)
  - [Incremental authorization](#incremental-authorization)
  - [Void](#void)
  - [Authorization reversal](#authorization-reversal)
  - [Refund](#refund)
  - [Clearing](#clearing)
  - [Settlement](#settlement)
  - [Payout](#payout)
- **[Section 3 — Card Data and Messages](#section-3--card-data-and-messages)**
  - [PAN](#pan)
  - [BIN](#bin)
  - [CVV](#cvv)
  - [EMV](#emv)
  - [ISO 8583](#iso-8583)
  - [Decline code](#decline-code)
  - [Soft decline](#soft-decline)
  - [Hard decline](#hard-decline)
  - [Merchant category code](#merchant-category-code)
  - [Acquirer reference number](#acquirer-reference-number)
  - [Network transaction ID](#network-transaction-id)
  - [Statement descriptor](#statement-descriptor)
  - [Address verification](#address-verification)
- **[Section 4 — Security and Compliance](#section-4--security-and-compliance)**
  - [PCI DSS](#pci-dss)
  - [Self-assessment questionnaire](#self-assessment-questionnaire)
  - [Tokenization](#tokenization)
  - [Network token](#network-token)
  - [Card vault](#card-vault)
  - [Point-to-point encryption](#point-to-point-encryption)
  - [Hosted payment fields](#hosted-payment-fields)
  - [3-D Secure](#3-d-secure)
  - [Strong customer authentication](#strong-customer-authentication)
  - [SCA exemption](#sca-exemption)
  - [Liability shift](#liability-shift)
  - [PSD2](#psd2)
  - [KYC](#kyc)
  - [KYB](#kyb)
  - [AML](#aml)
  - [Sanctions screening](#sanctions-screening)
- **[Section 5 — Fraud and Disputes](#section-5--fraud-and-disputes)**
  - [Card-present transaction](#card-present-transaction)
  - [Card-not-present transaction](#card-not-present-transaction)
  - [Card testing](#card-testing)
  - [Account takeover](#account-takeover)
  - [Friendly fraud](#friendly-fraud)
  - [Velocity check](#velocity-check)
  - [Risk scoring](#risk-scoring)
  - [Chargeback](#chargeback)
  - [Retrieval request](#retrieval-request)
  - [Representment](#representment)
  - [Pre-arbitration](#pre-arbitration)
  - [Dispute reason code](#dispute-reason-code)
  - [Chargeback ratio](#chargeback-ratio)
- **[Section 6 — Fees and Currency](#section-6--fees-and-currency)**
  - [Interchange fee](#interchange-fee)
  - [Scheme fee](#scheme-fee)
  - [Merchant discount rate](#merchant-discount-rate)
  - [Interchange-plus pricing](#interchange-plus-pricing)
  - [Blended pricing](#blended-pricing)
  - [Surcharging](#surcharging)
  - [Rolling reserve](#rolling-reserve)
  - [Cross-border fee](#cross-border-fee)
  - [Dynamic currency conversion](#dynamic-currency-conversion)
  - [Multi-currency pricing](#multi-currency-pricing)
  - [Minor unit](#minor-unit)
- **[Section 7 — Bank Rails](#section-7--bank-rails)**
  - [ACH](#ach)
  - [SEPA Credit Transfer](#sepa-credit-transfer)
  - [SEPA Instant](#sepa-instant)
  - [SEPA Direct Debit](#sepa-direct-debit)
  - [SWIFT](#swift)
  - [Fedwire](#fedwire)
  - [RTGS](#rtgs)
  - [FedNow](#fednow)
  - [RTP network](#rtp-network)
  - [Faster Payments](#faster-payments)
  - [Correspondent banking](#correspondent-banking)
  - [Nostro account](#nostro-account)
  - [IBAN](#iban)
  - [ISO 20022](#iso-20022)
  - [Direct debit mandate](#direct-debit-mandate)
  - [Payment return](#payment-return)
  - [Open banking](#open-banking)
  - [Pay by bank](#pay-by-bank)
- **[Section 8 — Payment Methods](#section-8--payment-methods)**
  - [Digital wallet](#digital-wallet)
  - [Buy now pay later](#buy-now-pay-later)
  - [UPI](#upi)
  - [Pix](#pix)
  - [Virtual card](#virtual-card)
  - [Prepaid card](#prepaid-card)
  - [QR code payment](#qr-code-payment)
  - [Cash voucher](#cash-voucher)
  - [Stablecoin payment](#stablecoin-payment)
- **[Section 9 — Payments Engineering](#section-9--payments-engineering)**
  - [Payment intent](#payment-intent)
  - [Payment state machine](#payment-state-machine)
  - [Double charge](#double-charge)
  - [Unknown payment outcome](#unknown-payment-outcome)
  - [Payment retry](#payment-retry)
  - [Ledger](#ledger)
  - [Double-entry bookkeeping](#double-entry-bookkeeping)
  - [Payment reconciliation](#payment-reconciliation)
  - [Settlement file](#settlement-file)
  - [Payment routing](#payment-routing)
  - [Payment orchestration](#payment-orchestration)
  - [Authorization rate](#authorization-rate)
  - [Stored credential](#stored-credential)
  - [Customer-initiated transaction](#customer-initiated-transaction)
  - [Merchant-initiated transaction](#merchant-initiated-transaction)
  - [Recurring billing](#recurring-billing)
  - [Dunning](#dunning)
  - [Account updater](#account-updater)
  - [Split payment](#split-payment)
  - [Safeguarding](#safeguarding)

## Section 1 — Participants

### Cardholder

A cardholder is the person a payment card is issued to. In the [four-party model](#four-party-model), the cardholder pays a [merchant](#merchant), and their [issuer](#issuer) decides whether to approve the payment and then bills them or debits their account.

The cardholder is not always the party that owns the account or the person who placed the order. Those differences explain many payment support cases.

| Role                | Who it is                         | Example                            |
| ------------------- | --------------------------------- | ---------------------------------- |
| Cardholder          | Person issued the card            | Employee with a company card       |
| Account holder      | Party responsible for the account | The company paying the card bill   |
| Merchant's customer | Person who placed the order       | A teenager using a parent's card   |

The last row causes a common failure. A parent sees an unfamiliar line on a statement, does not connect it with a purchase made by someone in the household, and reports it to the bank. The merchant then receives a [chargeback](#chargeback) for an order that was delivered correctly. This is one route to [friendly fraud](#friendly-fraud), and a clear [statement descriptor](#statement-descriptor) makes it less likely.

Cardholder protection depends on region and product. In the EU, [PSD2](#psd2) gives payers [refund](#refund) rights for unauthorised transactions and limits their liability. In the US, Regulation Z covers credit cards and Regulation E covers debit cards, with different limits. Network dispute rights sit alongside these laws, and the cardholder uses them by contacting the issuer rather than the [card network](#card-network).

Merchants should keep only the cardholder data they need. The card number, or [PAN](#pan), and the [CVV](#cvv) are covered by [PCI DSS](#pci-dss), so most systems hold a [token](#tokenization) in their place.

_Usage:_

"This customer says they never bought from us, but the order shipped to their home address."

"Someone else in the household may have used the card. Send the cardholder the order details before the dispute goes further."

### Merchant

A merchant is a business or person that accepts a card as payment for goods or services. Visa's rules separate a merchant with its own agreement with an [acquirer](#acquirer) from a sponsored merchant that contracts through a [payment facilitator](#payment-facilitator). Mastercard uses similar categories, and treats the facilitator as acting for the acquirer.

A business selling online is not automatically the merchant on the card transaction. The contract decides that.

| Setup                                                | Contract is with                      | Seller shown on the transaction |
| ---------------------------------------------------- | ------------------------------------- | ------------------------------- |
| Direct merchant                                      | Acquirer                              | The business                    |
| Sponsored merchant                                   | Payment facilitator                   | The business                    |
| Retailer on a marketplace                            | Marketplace                           | Usually the marketplace         |
| Product sold through a [merchant of record](#merchant-of-record) | Reseller acting as merchant of record | The reseller                    |

The merchant agrees to follow [card network](#card-network) rules through its contract. In practice this means describing the business accurately, showing a recognisable [statement descriptor](#statement-descriptor), protecting card data under [PCI DSS](#pci-dss), issuing a [refund](#refund) when owed, and answering each [chargeback](#chargeback). For most online payments the merchant also carries the loss from fraud unless a [liability shift](#liability-shift) applies.

Each merchant is identified by a merchant ID assigned by its acquirer and classified with a [merchant category code](#merchant-category-code). This classification is a frequent source of trouble. A business approved to sell software that starts selling supplements or gift cards no longer matches what it declared. The acquirer may notice through monitoring, then pause its [payout](#payout) or close the [merchant account](#merchant-account) while it reviews the activity.

To avoid that, tell the acquirer or [payment service provider](#payment-service-provider) before adding a product line, changing ownership, or selling in a new country.

_Usage:_

"Why did our payouts stop after we launched the gift card range?"

"We were onboarded as a software merchant. Risk flagged the new product, so we need to update our business profile with the acquirer."

### Issuer

An issuer is the bank or licensed financial institution that provides a payment card to a [cardholder](#cardholder) and holds the account behind it. When a card is used, the issuer makes the final decision on the [card authorization](#card-authorization).

| Stage         | What the issuer does                                                    |
| ------------- | ----------------------------------------------------------------------- |
| Card issue    | Checks the customer, opens the account, sets limits, provides the card  |
| Authorization | Checks funds, card status and fraud risk, then approves or declines     |
| [Clearing](#clearing)      | Receives the final transaction record and posts it to the account       |
| [Settlement](#settlement)    | Pays the amount owed through the [card network](#card-network)                              |
| Dispute       | Takes the cardholder's claim and may raise a [chargeback](#chargeback)                    |

The issuer is often confused with the network. A customer may say "Visa declined my card", but Visa and Mastercard do not usually make the credit or balance decision. The issuer does, and a [merchant](#merchant) or [payment service provider](#payment-service-provider) cannot override it. When a payment fails at checkout with a generic [decline code](#decline-code), the person who can explain it is usually the issuer's support team. The merchant often sees only the code.

The issuer is also a different party from the [acquirer](#acquirer), which works for the merchant. One bank can play both roles in different transactions.

Consumer fintech cards add a layer. The app's brand may appear on the card while a licensed bank or e-money institution is the actual issuer, often with a program manager running the product. A [sponsor bank](#sponsor-bank) arrangement of this kind is common in the US.

In the EU, [PSD2](#psd2) treats issuing payment instruments as a regulated payment service, and the issuer is responsible for applying [strong customer authentication](#strong-customer-authentication) unless an exemption applies.

_Usage:_

"The customer says their card works everywhere except on our site."

"Our logs show a do-not-honor from the issuer. We can't see why, so they need to call the number on the back of the card."

### Acquirer

An acquirer is the bank or licensed institution that contracts with a [merchant](#merchant) to accept card payments, enters those transactions into the [card network](#card-network), and arranges for the merchant to be paid. Visa's rules define it as a member that signs a merchant or [payment facilitator](#payment-facilitator) and enters transactions into interchange, the exchange of transactions between members. In the EU, [PSD2](#psd2) treats acquiring as a regulated payment service.

The acquirer is the merchant-side counterpart of the [issuer](#issuer).

| Party                                         | Works for    | Main job                                                 |
| --------------------------------------------- | ------------ | -------------------------------------------------------- |
| Issuer                                        | [Cardholder](#cardholder)   | Approves payments and bills the card account             |
| Acquirer                                      | Merchant     | Sponsors the merchant on the network and funds it        |
| [Payment processor](#payment-processor) | Either party | Runs the transaction systems, often for an acquirer      |
| [Payment gateway](#payment-gateway)     | Merchant     | Connects the checkout to the processing systems          |

The acquirer carries financial responsibility to the network for the merchants it signs. If a merchant closes while [chargebacks](#chargeback) are still arriving, and cannot repay them, the acquirer can be left covering the loss. Mastercard's rules also make an acquirer responsible for the acts and omissions of its payment facilitators and their sponsored merchants.

An acquirer therefore reviews a business before onboarding, using [KYB](#kyb) checks, and keeps monitoring it afterwards. A sudden jump in sales, a rising [chargeback ratio](#chargeback-ratio), or a move into a higher-risk product can lead it to delay a [payout](#payout), impose a [rolling reserve](#rolling-reserve), or end the relationship.

Many businesses never deal with an acquirer directly. A [payment service provider](#payment-service-provider) may hold the acquiring relationship, or partner with one or more acquirers, and present a single contract. If support asks "who is your acquirer?", check the provider's terms or [settlement](#settlement) reports rather than assuming the provider is the acquirer.

_Usage:_

"Why are they holding back part of our payouts all of a sudden?"

"Our volume tripled in a month. The acquirer is on the hook if those orders turn into chargebacks, so it added a reserve."

### Card network

A card network, also called a card scheme, is the organisation that operates a card brand. It connects [issuers](#issuer) and [acquirers](#acquirer), carries their messages, calculates what they owe each other, and publishes the rules they must follow. Visa and Mastercard operate globally. Others include American Express, Discover, JCB and UnionPay, along with domestic schemes such as Cartes Bancaires in France and girocard in Germany.

| Function | What the network does                                                                 |
| -------- | ------------------------------------------------------------------------------------- |
| Routing  | Passes each [card authorization](#card-authorization) from acquirer to issuer and back       |
| [Clearing](#clearing) | Exchanges final transaction records between members                                   |
| [Settlement](#settlement) | Calculates net positions so members can pay each other                                |
| Rules    | Sets acceptance, data, dispute and monitoring requirements                            |
| Fees     | Charges [scheme fees](#scheme-fee) and administers [interchange](#interchange-fee) where applicable |

In the [four-party model](#four-party-model), the network does not hold the [cardholder's](#cardholder) account or lend money. This is why "Visa declined the payment" is usually inaccurate: the issuer declined it, and the network delivered the answer. The network can still affect the result in narrower cases, such as stand-in processing when an issuer is unavailable, or fraud services an issuer chooses to use.

Network rules are private contracts that bind members, which then pass them on to [merchants](#merchant) through their agreements. They are not law, and they vary by network and region. A rule that applies to Visa in Europe may not apply to Visa in the US or to Mastercard anywhere. Networks also revise their rules regularly.

For engineers, this means a behaviour observed on one brand should not be assumed for another. If code branches on `network`, check the current rulebook or your provider's documentation for each brand, and record which edition the logic was based on.

_Usage:_

"Mastercard let us capture this after a week, so Visa should too, right?"

"Not necessarily. The networks have different authorization rules, so check each one before we hard-code the window."

### Four-party model

The four-party model is the standard structure of a card payment. The four parties are the [cardholder](#cardholder), the [merchant](#merchant), the cardholder's [issuer](#issuer) and the merchant's [acquirer](#acquirer). A [card network](#card-network) sits between the two institutions and is not counted as one of the four.

| Party      | Relationship                          | Role in a payment                       |
| ---------- | ------------------------------------- | --------------------------------------- |
| Cardholder | Customer of the issuer                | Presents the card                       |
| Merchant   | Customer of the acquirer              | Sells goods and requests payment        |
| Issuer     | Member of the network                 | Approves and pays on the cardholder's behalf |
| Acquirer   | Member of the network                 | Submits transactions and funds the merchant |
| Network    | Connects issuer and acquirer          | Routes messages and applies rules       |

The structure explains why a merchant cannot ask "the bank" what happened to a payment. The merchant has a relationship only with its acquirer or [payment service provider](#payment-service-provider), and the cardholder has one only with the issuer. A decline reason, a missing [refund](#refund) or a [chargeback](#chargeback) has to pass through that chain, so each side sees only part of the picture. Shared references such as the [acquirer reference number](#acquirer-reference-number) exist to connect the two views.

The alternative is a three-party scheme, in which the scheme itself acts as both issuer and acquirer. EU [Interchange](#interchange-fee) Fee Regulation 2015/751 defines both structures, and treats a three-party scheme as four-party when it licenses other providers to issue or acquire, or issues cards with a co-branding partner or through an agent. American Express and Discover are commonly described as three-party networks, but both also work with partner institutions in some markets, so the label depends on the product and country.

Money flows between issuer and acquirer through [settlement](#settlement).

_Usage:_

"Can't we just ask the customer's bank why it failed?"

"They won't talk to us. We're on the acquirer side of the four-party model, so the customer has to contact their issuer."

### Payment service provider

A payment service provider (PSP) is a company that gives [merchants](#merchant) the means to accept payments, usually through one contract and one API. The term has two meanings, and they do not always describe the same company.

| Sense      | Meaning                                                                                                     |
| ---------- | ----------------------------------------------------------------------------------------------------------- |
| Commercial | A vendor that bundles checkout, processing, reporting and payouts                                           |
| EU legal   | Under [PSD2](#psd2), a defined category such as a credit institution, e-money institution or payment institution |

A company can be a PSP commercially while relying on a licensed partner for the regulated activity. Check the contract to see which entity holds the funds and which is the [acquirer](#acquirer).

The roles around a PSP are often blurred because one vendor may perform several of them.

| Role                                              | What it does                                   | Holds merchant funds? |
| ------------------------------------------------- | ---------------------------------------------- | --------------------- |
| [Payment gateway](#payment-gateway)         | Passes payment data to processing systems      | Usually not           |
| [Payment processor](#payment-processor)     | Runs authorization and [clearing](#clearing) messages       | Usually not           |
| Acquirer                                          | Signs the merchant and answers to the network  | Yes, or via a partner |
| [Payment facilitator](#payment-facilitator) | Onboards sub-merchants under an acquirer       | Often                 |
| [Merchant of record](#merchant-of-record) | Is the legal seller of the goods to the buyer  | Yes                   |
| PSP                                               | Packages some or all of the above              | Depends on the model  |

A PSP may be a payment facilitator for small accounts and offer a direct acquiring contract to large ones, so the same vendor name can imply different responsibilities.

The cost of this bundling appears when a merchant tries to leave. Saved cards are often held as PSP-specific [tokens](#tokenization) in the provider's [card vault](#card-vault), so they do not work elsewhere until the card data is migrated. Ask about export terms before integrating, and store your own record of each payment rather than treating the PSP's dashboard as your only source of truth.

_Usage:_

"We can switch PSPs over the weekend, right?"

"Not with saved cards. Our tokens only work with the current provider, so we need a vault migration first."

### Payment gateway

A payment gateway is the technical service that takes payment details from a [merchant's](#merchant) checkout, sends them securely toward the [payment processor](#payment-processor) or [acquirer](#acquirer), and returns the response. It is the connection between the merchant's system and the card payment infrastructure. In a physical shop, the terminal and its software do a similar job.

| Role                                                  | Main question it answers                     |
| ----------------------------------------------------- | -------------------------------------------- |
| Gateway                                               | How does this request reach the card rails?  |
| Payment processor                                     | How is the transaction message handled?      |
| Acquirer                                              | Which licensed institution takes on this merchant? |
| [Payment service provider](#payment-service-provider) | Who sells the merchant the packaged service? |

A standalone gateway usually does not hold the merchant's money. Under [PSD2](#psd2), technical service providers that support payments without ever possessing the funds are excluded from the directive, which is one reason a pure gateway may not need a payment licence in the EU. Whether a specific business qualifies depends on what it actually does. Many modern providers combine gateway, processing and acquiring, so "gateway" often describes one layer of a larger product.

Because it handles card data, a gateway falls under [PCI DSS](#pci-dss) as a service provider. It commonly also offers [tokenization](#tokenization), [hosted payment fields](#hosted-payment-fields), and [3-D Secure](#3-d-secure) integration.

The failure engineers meet most often here is a timeout. The merchant sends a charge to the gateway, the connection drops, and nobody on the merchant's side knows whether the [issuer](#issuer) approved it. This is an [unknown payment outcome](#unknown-payment-outcome). Retrying blindly can produce a [double charge](#double-charge). Instead, send a stable idempotency key (a client-generated value that makes retries safe) if the gateway supports one, then query the transaction status before attempting the payment again.

_Usage:_

"The gateway timed out on that order. Should the worker just retry the charge?"

"Not yet. Look up the payment by its reference first. It may have been approved even though we never got the response."

### Payment processor

A payment processor is a company that runs the systems handling card transactions on behalf of an [acquirer](#acquirer) or [issuer](#issuer). It formats and routes messages, tracks transaction state, and produces the files used for [clearing](#clearing) and [settlement](#settlement). The licensed institution remains accountable to the [card network](#card-network) even when a processor does the technical work.

Processors are usually divided by side and by stage.

| Type                | Works for | Handles                                                         |
| ------------------- | --------- | --------------------------------------------------------------- |
| Acquirer processor  | Acquirer  | Card acceptance, batches and reporting              |
| Issuer processor    | Issuer    | Card accounts, authorization decisions under issuer rules, posting |
| Front-end processor | Either    | Real-time [card authorization](#card-authorization) messages                    |
| Back-end processor  | Either    | Clearing files, settlement data and dispute records             |

The distinction from nearby terms is about responsibility. A [payment gateway](#payment-gateway) connects a [merchant's](#merchant) checkout to processing. A processor runs the transaction work behind that connection. An acquirer holds the licence or network membership and takes on the merchant's risk. A [payment service provider](#payment-service-provider) may package all three. Merchants often say "our processor" when they mean whichever vendor they pay, so confirm the actual role before relying on the word.

Processor problems tend to appear as gaps between systems. A batch that was not submitted on time means authorized sales do not reach clearing, so funds arrive late and the hold stays on the customer's card. A partial outage may produce approvals in one system with no matching record in another. These cases surface during [payment reconciliation](#payment-reconciliation), when expected sales are missing from a [settlement file](#settlement-file).

When investigating, compare identifiers across stages: the authorization code, the [network transaction ID](#network-transaction-id) and, once cleared, the [acquirer reference number](#acquirer-reference-number). The stage where the identifier disappears shows where the transaction stopped.

_Usage:_

"Tuesday's sales were authorized, but they're missing from the settlement report."

"Looks like the processor never submitted that batch. Ask them to confirm it and resubmit before the authorizations go stale."

### Payment facilitator

A payment facilitator, or PayFac, is a company registered through an [acquirer](#acquirer) to accept card payments on behalf of smaller businesses, called sponsored [merchants](#merchant) or sub-merchants. Instead of each business getting its own [merchant account](#merchant-account), the facilitator onboards them under its own acquiring relationship, often quickly.

Network definitions differ. Visa classes a facilitator as a third-party agent and treats an entity as one if it deposits transactions, receives [settlement](#settlement), or contracts with an acquirer on behalf of a sponsored merchant. Mastercard defines it as a service provider registered by an acquirer to facilitate transactions for submerchants, and its rules make the acquirer responsible for the facilitator and those submerchants.

| Party                                        | Responsibility                                        |
| -------------------------------------------- | ----------------------------------------------------- |
| Acquirer                                     | Registers the facilitator, answers to the network     |
| Payment facilitator                          | Onboards, monitors and usually pays sub-merchants     |
| Sponsored merchant                           | Sells goods and remains the seller to the [cardholder](#cardholder)  |
| [Card network](#card-network)          | Sets the facilitator program rules                    |

The term is often confused with two others. A [payment service provider](#payment-service-provider) is a broader commercial label, and many PSPs operate as facilitators for small accounts. A [merchant of record](#merchant-of-record) is itself the seller, whereas a sponsored merchant stays the seller and the facilitator provides the acceptance. Visa also treats a marketplace as a separate category.

Fast onboarding has a visible cost. The facilitator may let a business start charging after light checks, then complete fuller [KYB](#kyb) review once volume grows. A seller can therefore process payments for weeks and then find its [payout](#payout) paused until it supplies ownership documents. Facilitators do this because they carry risk for [chargebacks](#chargeback) from sub-merchants that disappear.

_Usage:_

"Our new seller processed fine for a month, and now their payout is frozen."

"They hit the review threshold on our PayFac. Ask them for the ownership documents so compliance can release it."

### Merchant of record

A merchant of record (MoR) is the legal entity that sells goods or services to the buyer in a transaction. Its name appears on the [cardholder's](#cardholder) statement, it takes the payment, and it handles [refunds](#refund) and [chargebacks](#chargeback) for that sale. A software company may sell through an MoR, which buys or licenses the product and resells it to the end customer.

The term is widely used but is not defined identically everywhere. Visa's risk guidance uses it for a marketplace that contracts with the [acquirer](#acquirer), rather than the underlying retailers. Visa's rules also look at who sells to the cardholder, whose name identifies the outlet, and who gives the cardholder recourse.

| Model                                             | Legal seller to the buyer | Who handles disputes              |
| ------------------------------------------------- | ------------------------- | --------------------------------- |
| Direct merchant                                   | The business              | The business                      |
| [Payment facilitator](#payment-facilitator) | The sponsored merchant    | Sponsored merchant, via facilitator |
| Marketplace                                       | Usually the marketplace   | Marketplace, under its terms      |
| Merchant of record                                | The MoR                   | The MoR                           |

A facilitator helps a business accept cards while that business stays the seller. An MoR takes the seller's position, so it commonly also handles customer invoices and sales tax or VAT collection. The business then receives a net [payout](#payout) from the MoR after its fee, taxes and refunds. Which obligations move, and in which countries, depends on the contract and local tax law.

The symptom customers notice is an unfamiliar name. Someone buys a tool from a small software company and sees the MoR's name on their statement, assumes it is fraud, and calls their bank. A clear [statement descriptor](#statement-descriptor) and a receipt naming both companies reduce these disputes.

_Usage:_

"Customers keep asking why their receipt shows a company they've never heard of."

"That's our merchant of record. Let's put our product name in the descriptor and explain the reseller on the receipt."

### Merchant account

A merchant account is the arrangement between a business and an [acquirer](#acquirer) that allows the business to accept card payments. It is identified by a merchant ID and carries the terms agreed at onboarding, including what the business sells, its [merchant category code](#merchant-category-code), currencies and risk limits.

Despite the name, it is usually not an account the business can spend from. Card proceeds are tracked against it, then paid to a separate bank account.

| Item                     | What it is                                      | Can the business spend from it? |
| ------------------------ | ----------------------------------------------- | ------------------------------- |
| Merchant account         | Acquiring contract and transaction record       | No                              |
| PSP balance              | Amount a provider currently owes the business   | Only by [payout](#payout), in most setups |
| Business bank account    | Ordinary account that receives the payout       | Yes                             |

This explains a common question from finance teams: the dashboard shows sales as successful, but the bank balance has not moved. The funds are still between [settlement](#settlement) and payout, or they have been reduced by [refunds](#refund), fees, [chargebacks](#chargeback) or a [rolling reserve](#rolling-reserve).

There are two common setups. With a dedicated merchant account, the business has a direct contract with an acquirer, which usually involves more underwriting and more control over pricing and data. With an aggregated setup, a [payment facilitator](#payment-facilitator) holds the acquiring relationship and the business is a sponsored merchant beneath it, which is quicker to start but gives the provider more control over funds and account status.

If an acquirer closes a merchant account for rule violations, the closure can be recorded in network-run lists of terminated merchants, such as Mastercard's MATCH, which can make it harder to open a new one.

_Usage:_

"The dashboard says we took 40k this week, so why isn't it in the bank?"

"That's the merchant account view. The payout goes out after settlement, minus refunds and the reserve."

### Sponsor bank

A sponsor bank is a licensed bank, and member of a [card network](#card-network), that lets a company without its own membership take part in card payments. A fintech issuing cards, a non-bank [payment processor](#payment-processor) or a [payment facilitator](#payment-facilitator) can operate under the sponsor's membership, while the sponsor remains answerable to the network and its regulators.

Sponsorship can sit on either side of a transaction.

| Side      | Sponsored company                         | What the sponsor provides                                     |
| --------- | ----------------------------------------- | ------------------------------------------------------------- |
| Issuing   | Fintech card program or program manager   | The [issuer](#issuer) role, [BIN](#bin) access, regulated accounts |
| Acquiring | Independent sales organisation, PayFac    | [Acquirer](#acquirer) membership and access to [settlement](#settlement)   |

A sponsor bank differs from a partner bank that only holds deposits. The sponsor's network membership is what gives the company access to the card rails. It also differs from a processor, which runs technology but does not itself provide the membership.

The model is common in the US, where non-bank companies frequently reach Visa and Mastercard through a sponsoring bank. It is not universal. The Bank of England's guide for FCA-authorised non-bank providers says it is possible to be a direct participant in Visa and Mastercard in most respects while settling through another organisation. In the EU, [PSD2](#psd2) generally requires payment system access rules to be objective, non-discriminatory and proportionate. Each network sets its own eligibility criteria.

Because the sponsor carries the regulatory exposure, it sets conditions on the program. It may review marketing, require [KYC](#kyc) and [AML](#aml) controls, and audit the company's operations. If a sponsor exits a program or a regulator restricts it, the company can lose card access or need to migrate customers to a new BIN, which means new card numbers for customers. Check what the contract says about termination and transition.

_Usage:_

"Why does compliance need to approve the copy for our card launch?"

"We issue under our sponsor bank's membership. If our marketing breaks its rules, it's their licence at risk."

## Section 2 — Card Transaction Lifecycle

### Card authorization

A card authorization is a real-time request asking the [issuer](#issuer) whether a card payment can go ahead. If approved, the issuer usually reserves the amount with an [authorization hold](#authorization-hold). In the usual dual-message card flow, no money moves at this step.

| Step | Who                                 | What happens                                         |
| ---- | ----------------------------------- | ---------------------------------------------------- |
| 1    | [Merchant](#merchant)           | Sends amount and card details through its provider   |
| 2    | [Acquirer](#acquirer)           | Formats the request and forwards it to the network   |
| 3    | [Card network](#card-network) | Routes the request to the issuer                     |
| 4    | Issuer                              | Checks status, funds and risk, then responds         |
| 5    | Merchant                            | Receives an approval or a [decline code](#decline-code) |

Authorization is the first of four stages that people often merge into "the payment".

| Stage            | Question it answers                     | Money moves?             |
| ---------------- | --------------------------------------- | ------------------------ |
| Authorization    | Will the issuer approve this?           | No, funds are reserved   |
| [Capture](#capture)    | Does the merchant want to take payment? | No                       |
| [Clearing](#clearing)   | What is the final transaction record?   | No, amounts are calculated |
| [Settlement](#settlement) | Who pays whom?                          | Yes, between institutions |

Treating an approval as completed payment causes a familiar bug. An order system marks a sale "paid" after authorization, the capture job later fails, and the goods ship with no money collected. The approval eventually expires and the hold disappears. Record authorized and captured as separate states in the [payment state machine](#payment-state-machine).

Some transactions combine stages. A "sale" API call authorizes and captures together. In a single-message system, common for PIN debit, one message carries both the authorization and the financial transaction.

How long an approval stays valid varies by network, region and transaction type. Mastercard, for example, distinguishes preauthorizations, final and undefined authorizations. A valid approval also does not prove that the real [cardholder](#cardholder) made the purchase, so it does not protect the merchant from a later fraud [chargeback](#chargeback).

_Usage:_

"The order says paid, but finance can't find the money."

"It was only authorized. The capture job failed, so nothing ever went to clearing."

### Authorization hold

An authorization hold is a temporary reduction in a [cardholder's](#cardholder) available balance or credit after an [issuer](#issuer) approves a [card authorization](#card-authorization). The money stays in the account but cannot be spent. Banking apps usually show it as "pending", which is why customers often read a hold as a completed charge.

This is the source of a frequent support ticket. A customer's first checkout attempt appears to fail, they try again, and now see two pending amounts. Only one order exists, but both approvals are holding funds. The customer reports being charged twice, even though neither hold has been captured. On a debit card with a low balance, the extra hold can also cause an unrelated payment or rent debit to fail.

| Event                                          | Effect on the hold                         |
| ---------------------------------------------- | ------------------------------------------ |
| [Capture](#capture) and [clearing](#clearing)                         | Replaced by the posted transaction         |
| [Partial capture](#partial-capture)      | Unused part should be released             |
| [Incremental authorization](#incremental-authorization) | Held amount increases                      |
| [Authorization reversal](#authorization-reversal) | Issuer releases the funds                  |
| No further action                              | Issuer drops it after its own time limit   |

A [merchant](#merchant) controls whether a hold is captured or released, but the issuer controls how quickly the customer sees the change. A released hold can continue to display for some time in a banking app. How long an unused hold lasts depends on the issuer, the network and the transaction type, so avoid promising customers a specific number of days.

The fix for abandoned or duplicate approvals is to send a reversal as soon as you know the funds are not needed. Visa's rules require a reversal in specified cases, including when a transaction is cancelled or finishes below the authorized amount, and Visa can assess a fee on approvals that are neither cleared nor reversed. Mastercard has its own requirements.

_Usage:_

"A customer says we charged her twice for one order."

"One is a stale hold from the failed attempt. Send the reversal and tell her it should drop off once her bank processes it."

### Capture

Capture is the [merchant's](#merchant) instruction to collect funds that were approved in a [card authorization](#card-authorization). It converts "the [issuer](#issuer) said yes" into "take this amount". Capture is a provider and API term. At network level, the equivalent step is the submission of a [clearing](#clearing) record, which Mastercard calls first presentment.

| Stage                         | Who acts                   | Result                                 |
| ----------------------------- | -------------------------- | -------------------------------------- |
| Authorization                 | Issuer                     | Approval and [authorization hold](#authorization-hold)   |
| Capture                       | Merchant or its system     | Final amount is confirmed              |
| Clearing                      | [Acquirer](#acquirer), network, issuer | Transaction record is exchanged        |
| [Settlement](#settlement) | Institutions               | Funds move between them                |

A provider may capture individually or collect captures into a daily batch, so a successful capture response does not mean the money has arrived.

Merchants choose between two flows. With automatic capture, authorization and capture happen together, which suits digital goods delivered immediately. With manual capture, the merchant authorizes at checkout and captures later, which suits physical goods that ship after stock is confirmed. Card rules or local law may also restrict charging before goods are shipped, so check what applies in each market.

The main failure with manual capture is forgetting to do it. A background job crashes, the approval expires, and a shipped order has no payment behind it. Capturing late carries a second risk. Visa has a dispute condition for no authorization or late presentment, and Mastercard has an authorization-related [chargeback](#chargeback) with a defined protection period, so a late capture can be charged back even if the goods were delivered. Time limits differ by network and transaction type.

Alert on authorized payments approaching their capture window, and make the capture call safe to retry so a repeated job cannot create a [double charge](#double-charge). If you need less than the approved amount, use a [partial capture](#partial-capture).

_Usage:_

"Why did we get a chargeback on an order that definitely arrived?"

"We captured it three weeks after authorizing. The approval had expired, so proof of delivery doesn't help."

### Partial capture

A partial capture collects less than the amount approved in a [card authorization](#card-authorization). A customer orders three items for 90, the [merchant](#merchant) authorizes 90, one item is out of stock, and the merchant captures 60.

The step people miss is what happens to the remaining 30. Capturing 60 does not guarantee that the rest of the [authorization hold](#authorization-hold) is released promptly. The customer can see a 60 charge and a 90 pending amount at the same time and believe they were overcharged.

| Situation                 | Correct handling                                                     |
| ------------------------- | -------------------------------------------------------------------- |
| Final amount is lower     | Capture the lower amount, release the difference     |
| Order cancelled entirely  | Send a full [authorization reversal](#authorization-reversal)  |
| Final amount is higher    | Use [incremental authorization](#incremental-authorization) if eligible |
| Already settled, too high | Issue a [refund](#refund) for the difference                     |

Network rules address the unused amount. Visa requires a merchant to submit an authorization reversal for the difference when a completed transaction's final amount is less than the amount authorized. Mastercard's rules for Europe require a reversal when a transaction is finalised at a lower amount, and its other regions have their own wording. Many [payment service providers](#payment-service-provider) send this automatically, but confirm it rather than assume.

Partial capture is different from multiple capture, which takes several amounts against one authorization, usually for split shipments. Multiple capture is more restricted. Visa permits a single authorization with multiple [clearing](#clearing) records only in listed cases, including airlines, cruise lines, US railways, and card-absent merchants shipping goods in parts, with conditions such as telling the [cardholder](#cardholder).

Engineers should store authorized, captured and refunded amounts as separate fields in [minor units](#minor-unit). A single `amount` column cannot represent a partly captured payment, and support then cannot tell what the customer actually paid.

_Usage:_

"She was charged 60 but her bank still shows 90 pending."

"We did a partial capture and never released the other 30. Check whether the provider sent the reversal."

### Incremental authorization

An incremental authorization is an extra request that increases the amount approved on an existing card transaction. It is used when the cost grows after the first approval: a hotel guest extends a stay, a rental car is kept longer, or a bar tab increases.

Visa defines it as a request that follows an approved estimated [authorization](#card-authorization) and covers an additional amount the [cardholder](#cardholder) is expected to spend or has incurred in that same transaction. Mastercard handles the same need through preauthorizations, with additional requests referencing the original by its trace identifier. Eligibility varies by network, region, [merchant category](#merchant-category-code) and [acquirer](#acquirer), so a flow that works for one brand may not work for another.

| Option                    | Links to original? | Effect on the customer                  |
| ------------------------- | ------------------ | --------------------------------------- |
| Incremental authorization | Yes                | One growing [authorization hold](#authorization-hold) |
| New separate authorization | No                 | Two holds, which can look like two charges |
| Reauthorization           | Yes, by rule       | Refreshes an approval that is expiring  |
| [Partial capture](#partial-capture) | Yes                | Takes less than was approved            |

The link matters because the [issuer](#issuer) needs to know this is the same purchase. Without it, a [merchant](#merchant) that sends a fresh approval for the extra amount creates a second hold and a second record. The customer sees two pending entries, and [clearing](#clearing) may no longer match cleanly to one authorization.

An incremental request is a new decision and can be declined. A guest with a nearly full credit limit may be approved at check-in and declined when the stay is extended. The merchant is then exposed for the extra amount unless it collects another payment method, so request the increase before providing the additional service.

Pass the [network transaction ID](#network-transaction-id) from the original approval on each increment and release any unused amount at the end.

_Usage:_

"The guest added two nights and now has two pending hotel charges."

"We sent a new auth. It should have been an incremental on the original transaction."

### Void

A void cancels a card payment before it has been submitted for [clearing](#clearing). Because the transaction has not been finalised, no money is taken and no [refund](#refund) is needed. A shop assistant who rings up the wrong amount and cancels it immediately is performing a void.

"Void" is mainly a term used by [payment service providers](#payment-service-provider), terminals and processors, and its exact behaviour depends on the provider. What happens underneath depends on how far the payment has gone.

| Term                                                 | When it applies                   | What happens                                  | Customer sees                 |
| ---------------------------------------------------- | --------------------------------- | --------------------------------------------- | ----------------------------- |
| Void                                                 | Before clearing submission        | Provider cancels the pending transaction      | Pending entry, then nothing   |
| [Authorization reversal](#authorization-reversal) | After approval, before [capture](#capture) | Message tells the [issuer](#issuer) to release funds | Hold disappears               |
| Refund                                               | After clearing or [settlement](#settlement) | New credit transaction returns the money      | Charge, then a separate credit |

A void and a reversal are often the same event seen at two levels. The [merchant](#merchant) calls "void" in an API, and the provider sends an authorization reversal to the issuer. A void can, however, fail to release the customer's money if the provider only removes the transaction from its own batch and sends no reversal. The sale is cancelled, but the [authorization hold](#authorization-hold) stays on the card until the issuer's time limit passes. Check which behaviour your provider documents.

Timing is the common source of errors. Providers usually close batches on a schedule, and after the cutoff a void call is rejected with an error such as "already settled". Support tools should try a void first when the payment is eligible and otherwise issue a refund. Doing both can credit a customer for money never taken, so code the choice from the payment's current state in the [payment state machine](#payment-state-machine).

_Usage:_

"Support tried to void yesterday's order and got an error."

"The batch already closed, so it can't be voided. Issue a refund instead."

### Authorization reversal

An authorization reversal is a message that cancels all or part of an approved [card authorization](#card-authorization), telling the [issuer](#issuer) to release the funds it was holding. Visa's rules describe it as a system message that cancels an approval response. It applies before the transaction has been cleared.

| Term                  | Stage                          | Mechanism                         | Money already moved? |
| --------------------- | ------------------------------ | --------------------------------- | -------------------- |
| Authorization reversal | After approval, before [clearing](#clearing) | Network message to the issuer     | No                   |
| [Void](#void)     | Before clearing submission     | Provider action, often sends a reversal | No                   |
| [Refund](#refund) | After clearing                 | New credit transaction            | Yes                  |

A [merchant](#merchant) needs a reversal in four common situations: the customer cancels, stock runs out, the final amount is lower than approved, or a timeout leaves an approval the merchant cannot use. The issuer approves, the response is lost, and the merchant records a failure. The customer's funds stay on hold for an order that does not exist. Visa's rules require a reversal when a point-of-sale merchant receives an approval after timing out.

Requirements are network-specific. Visa requires merchants to submit reversals in listed cases and can charge a misuse-of-authorization fee on approvals matched to neither a clearing record nor a reversal. Mastercard's Transaction Processing Rules set separate requirements, including a timed rule in the Europe region for cancelled or reduced transactions.

Reversals can be full or partial. A partial reversal reduces the held amount and is the usual companion to a [partial capture](#partial-capture). The message must reference the original authorization, normally through the [network transaction ID](#network-transaction-id) or matching data, or the issuer may not connect the two.

Visa also uses "Reversal" for a separate correction of a transaction sent through clearing in error. When reading a rulebook or provider log, check which of the two is meant.

_Usage:_

"The auth call timed out, so we marked the order failed. Are we done?"

"No. It may have been approved. Send a reversal, or the customer's money stays on hold."

### Refund

A refund returns money to a customer's card after the original payment has been [captured](#capture) and [cleared](#clearing). It is a new transaction in the opposite direction. The original charge stays on the statement, and a separate credit appears later.

| Action                                                  | Timing                      | Result on the statement          |
| ------------------------------------------------------- | --------------------------- | -------------------------------- |
| [Void](#void)                                       | Before clearing submission  | Usually no posted entry          |
| [Authorization reversal](#authorization-reversal) | Before clearing             | Pending hold disappears          |
| Refund                                                  | After clearing              | Charge plus separate credit      |
| [Chargeback](#chargeback)                           | After a dispute with the [issuer](#issuer) | Credit forced through the network |

A refund is initiated by the [merchant](#merchant), which distinguishes it from a chargeback, initiated by the issuer. The money is deducted from the merchant's balance or a future [payout](#payout). If the balance is too low, the provider may delay the refund or debit the merchant's bank account.

A common complaint is "you said you refunded me, but I don't have it". The merchant's system shows success because the provider accepted the instruction, but the credit still has to pass through clearing and be posted by the issuer. That can take days, and the exact time varies. Give the customer the [acquirer reference number](#acquirer-reference-number) when your provider exposes one, since their bank can use it to trace the credit.

Refunds interact badly with disputes. If a customer has already opened a chargeback and the merchant also issues a refund, the customer can receive the money twice. Check for an open dispute first. If a refund was issued before the dispute, submit that as evidence through [representment](#representment).

Visa's rules require a refund to the same payment credential where possible, with listed exceptions. Refunds to a different card are a known fraud pattern. Whether the merchant recovers its processing fees depends on its contract.

_Usage:_

"The customer says the refund never arrived, but our dashboard shows it succeeded."

"Send them the ARN. Their bank can use it to find the credit."

### Clearing

Clearing is the exchange of final transaction records between an [acquirer](#acquirer) and an [issuer](#issuer) through a [card network](#card-network). It tells the issuer the final amount to post to the customer's account and calculates what the institutions owe each other. Visa's rules describe it as the validation and valuation of records exchanged between Visa and its members. Mastercard calls the record a first presentment.

Clearing sits between the [merchant's](#merchant) instruction and the actual movement of money.

| Stage                                     | What it does                          | Output                           |
| ----------------------------------------- | ------------------------------------- | -------------------------------- |
| [Card authorization](#card-authorization) | Issuer approves the payment           | Approval and hold                |
| [Capture](#capture)                   | Merchant confirms the amount          | Instruction to acquirer or batch |
| Clearing                                  | Records are exchanged and valued      | Final amounts, fees, positions   |
| [Settlement](#settlement)             | Institutions pay net amounts          | Funds transferred                |
| [Payout](#payout)                     | Provider pays the merchant            | Bank deposit                     |

Clearing is where the actual transaction amount becomes final, and it can differ from the authorized amount. A restaurant authorizes the bill and clears it with a tip. A clearing record is also where [interchange](#interchange-fee) and [scheme fees](#scheme-fee) are typically determined, so data quality at this stage affects cost. Incorrect [merchant category codes](#merchant-category-code) or missing fields can lead to a higher fee category.

Most card transactions use a dual-message flow, with one message for authorization and another for clearing. Some debit systems use a single message for both.

A common engineering problem is treating the authorization as the final record. If the clearing amount differs, or clears on a different date or in a different currency, a ledger built from authorization data will not match the [settlement file](#settlement-file). Build [payment reconciliation](#payment-reconciliation) from cleared records. Visa also assesses fees on clearing records with no matching approval, so clearing transactions must keep the references from the original authorization.

_Usage:_

"Why does the charge in our ledger differ from the settlement report by the tip amount?"

"The ledger used the auth. Clearing carried the final amount, so reconcile against that."

### Settlement

Settlement is the movement of money between financial institutions after [clearing](#clearing) has established what each one owes. In a card payment, the [issuer](#issuer) pays, usually on a net basis, through the [card network's](#card-network) settlement arrangements, and the [acquirer](#acquirer) receives funds. Visa's rules define settlement as the reporting and funds transfer of amounts owed by one member to another, or to Visa, as a result of clearing.

Networks usually settle net positions rather than each individual card payment. An acquirer may be owed for millions of purchases and owe for [refunds](#refund) and [chargebacks](#chargeback), so one net amount moves in a settlement currency.

| Stage                         | Parties                        | What moves                     |
| ----------------------------- | ------------------------------ | ------------------------------ |
| [Card authorization](#card-authorization) | [Merchant](#merchant) to issuer | A message and a hold           |
| Clearing                      | Acquirer, network, issuer      | Transaction records            |
| Settlement                    | Issuer, network, acquirer      | Net funds between institutions |
| [Payout](#payout)         | Acquirer or provider to merchant | Funds to a business bank account |

The word causes a specific misunderstanding. A provider dashboard may show a payment as "settled" while the merchant's bank has received nothing. That status can mean the transaction was submitted, that the provider has received funds, or that the payment is in the next payout. Each provider defines it differently, so read the documentation rather than assuming that settled means deposited.

Settlement timing depends on the network, currency, business days and bank holidays. A [payment service provider](#payment-service-provider) may add its own payout delay.

Engineers usually meet settlement through a [settlement file](#settlement-file) or report. It often lists amounts grouped by batch and net of fees, in the settlement currency, which may differ from the customer's currency. Matching those records to orders requires shared identifiers, and it is the purpose of [payment reconciliation](#payment-reconciliation). Track settlement in your [ledger](#ledger) as a separate event from [capture](#capture) so finance can see money in transit.

_Usage:_

"The dashboard says Friday's sales settled. Why isn't the money in the bank?"

"Settled just means the acquirer has it. The payout runs on Tuesday."

### Payout

A payout is the transfer of funds from an [acquirer](#acquirer) or [payment service provider](#payment-service-provider) to a [merchant's](#merchant) bank account. It is the last step of the card flow and the first point at which the business can spend the money. Some providers call it a deposit, remittance or funding.

A payout differs from [settlement](#settlement), which moves money between institutions. Settlement can complete while the merchant still has not been paid.

A payout is rarely the sum of the day's sales. It is a net amount.

| Line item                                         | Effect on payout |
| ------------------------------------------------- | ---------------- |
| Captured sales                                    | Adds             |
| [Refunds](#refund)                            | Subtracts        |
| [Chargebacks](#chargeback) and dispute fees   | Subtracts        |
| Processing fees                                   | Subtracts        |
| Newly withheld [rolling reserve](#rolling-reserve) | Subtracts        |
| Released reserve                                  | Adds             |
| Reversed chargebacks                              | Adds             |

This is why finance teams often find a deposit that matches no order total. Reconcile by obtaining the provider's list of transactions included in each payout, using its payout ID, rather than comparing bank deposits with daily sales. This is a main task of [payment reconciliation](#payment-reconciliation).

A balance can also go negative. If refunds and chargebacks exceed new sales, there is nothing to pay out, and the provider may debit the merchant's bank account or recover the shortfall from future sales. A payout can fail when bank details are wrong or an account is closed, and the funds then return to the provider's balance.

Providers may pause payouts during a risk or compliance review, for example when [KYB](#kyb) details are missing, sales patterns change sharply, or a [sanctions screening](#sanctions-screening) alert is unresolved.

On a platform, the term also covers payments to sellers, which may use a [split payment](#split-payment). Model each payout in your [ledger](#ledger) as a separate record linked to the transactions it contains, and treat a provider's "paid" status as provisional until the bank confirms receipt.

_Usage:_

"Today's deposit is 3,100 but we sold 4,000 yesterday."

"Pull the payout breakdown. It nets out refunds, fees and that chargeback from last week."

## Section 3 — Card Data and Messages

### PAN

A PAN, or primary account number, is the long number that identifies a payment card account. Its format comes from ISO/IEC 7812, which allows up to 19 digits. Sixteen is common, but not universal, so a form or database column that assumes 16 digits will reject or corrupt valid cards.

| Part                 | Position         | Purpose                                         |
| -------------------- | ---------------- | ----------------------------------------------- |
| [Issuer](#issuer) identifier | Leading digits   | The [BIN](#bin), identifying the issuer or program |
| Account identifier   | Middle digits    | The individual account within that issuer       |
| Check digit          | Final digit      | Catches typing errors using the Luhn formula    |

The Luhn check only detects mistyped numbers. A number that passes is well formed, and that says nothing about whether the account exists, is open, or belongs to the person typing it. Only a [card authorization](#card-authorization) can check that.

[PCI DSS](#pci-dss) treats the PAN as the defining element of cardholder data: if a system stores, processes or transmits it, that system is in scope. Masking and truncation are different. Masking hides digits on a screen while the full value may still exist underneath. Truncation permanently removes digits from the stored value. PCI SSC publishes the formats it accepts for truncation, and these changed with the move to longer BINs.

The usual incident is accidental storage. A debug log captures a full request body, a support agent pastes a card number into a ticket, or an analytics script reads a checkout field. This widens compliance scope and requires clean-up across logs and backups.

Most [merchants](#merchant) avoid handling the PAN by using [hosted payment fields](#hosted-payment-fields) and keeping a [PSP token](#tokenization) or [network token](#network-token). A network token is itself a different number in PAN format, so code should not assume that every card-shaped value is the underlying card number.

_Usage:_

"Why is compliance asking us to purge three months of application logs?"

"The request logger captured full PANs from the checkout endpoint. Those logs are now in PCI scope."

### BIN

A BIN, or bank identification number, is the leading part of a [PAN](#pan) that identifies the [issuer](#issuer) or card program. ISO/IEC 7812 calls it the issuer identification number, or IIN.

The BIN was historically six digits. ISO revised the standard to make it eight, converting each six-digit range into a block of one hundred eight-digit ranges. Visa set April 2022 as the date for its clients to support eight-digit BINs and stopped assigning new six-digit issuing BINs after that.

Systems use BIN data to answer questions about a card before or during payment.

| Question                      | Used for                                                 |
| ----------------------------- | -------------------------------------------------------- |
| Which network?                | Showing the logo, [payment routing](#payment-routing) |
| Credit, debit or prepaid?     | Pricing, eligibility, blocking card types                |
| Issuing country?              | Fraud rules, [cross-border fee](#cross-border-fee) estimates |
| Consumer or commercial?       | Fee estimates, invoicing flows                           |

The move to eight digits created a quiet failure. Code that takes `pan.slice(0, 6)` and looks it up in a local table still runs, but two different programs can now share the same first six digits. A fraud rule or a block aimed at one program can then hit another, and a credit card can be classified as debit. Use the longest available prefix, and refresh BIN tables from your provider or network, because ranges are reassigned.

BIN data is an attribute of the card, so it is not proof of anything about the person using it. Issuing country in particular says where the card was issued, which may differ from where the customer lives. A [network token](#network-token) can carry its own token range rather than the underlying card's BIN.

A sudden run of declines on sequential cards from the same BIN at one [merchant](#merchant) is a warning sign of [card testing](#card-testing).

_Usage:_

"Our prepaid block started rejecting normal credit cards from this bank."

"The rule matches on six digits. That range is now split across products, so move the lookup to eight-digit BINs."

### CVV

A CVV, or card verification value, is the short security code on a payment card that an [issuer](#issuer) can check during a [card-not-present transaction](#card-not-present-transaction). It is meant to show that the person paying has access to the card rather than only the [PAN](#pan). The name varies by network.

| Network          | Common name | Usual length and location     |
| ---------------- | ----------- | ----------------------------- |
| Visa             | CVV2        | Three digits, back of card    |
| Mastercard       | CVC2        | Three digits, back of card    |
| American Express | CID         | Four digits, front of card    |

The printed code differs from the value encoded on the magnetic stripe, and chip transactions use separate cryptographic values.

[PCI DSS](#pci-dss) classes the card verification code as sensitive authentication data. Requirement 3.3.1 forbids storing such data after [authorization](#card-authorization), even if encrypted. Issuers and companies supporting issuing services have a narrow exception. Teams building subscriptions sometimes save the CVV for later charges. That breaches the standard and is unnecessary: a later [merchant-initiated transaction](#merchant-initiated-transaction) relies on the [stored credential](#stored-credential) framework and does not need the code. Keep it out of logs and queues too.

A CVV check is a signal and does not prove identity. The result comes back with the authorization, and a mismatch does not always cause a decline, because some issuers approve anyway and leave the decision to the [merchant](#merchant). Decide in your [risk scoring](#risk-scoring) rules whether to reverse an approved payment with a failed check. If you do, send an [authorization reversal](#authorization-reversal) so the funds are released.

Stolen card data often includes the code, so a correct CVV does not rule out fraud. Unlike [3-D Secure](#3-d-secure), a passing CVV check does not by itself give the merchant a [liability shift](#liability-shift). Repeated CVV failures across attempts on one card are a sign of [card testing](#card-testing).

_Usage:_

"Can we store the CVV encrypted so renewals don't need the customer?"

"No, PCI DSS bans storing it after authorization, even encrypted. Renewals should use the stored credential flow."

### EMV

EMV is a family of technical specifications for secure card payments, best known for chip cards and contactless payments. The name comes from Europay, Mastercard and Visa. The specifications are managed by EMVCo, a technical body collectively owned by American Express, Discover, JCB, Mastercard, UnionPay and Visa.

A chip card differs from a magnetic stripe in how it proves itself. A stripe holds static data that can be copied. A chip holds secret keys and generates a cryptogram, a one-time code computed over the transaction's details, which the [issuer](#issuer) can verify.

| Step | Who      | What happens                                                    |
| ---- | -------- | --------------------------------------------------------------- |
| 1    | Terminal | Reads the card and sends transaction details to the chip        |
| 2    | Card     | Generates a cryptogram for this transaction                     |
| 3    | Terminal | Sends it in the [card authorization](#card-authorization) request            |
| 4    | Issuer   | Recalculates the cryptogram and approves or declines            |
| 5    | Card     | Can verify the issuer's response and complete the transaction   |

Because each cryptogram is tied to one transaction, data captured from a chip payment cannot be replayed to make a counterfeit card work. This is the protection chip adds in a [card-present transaction](#card-present-transaction).

EMV does not protect a [card-not-present transaction](#card-not-present-transaction), because no chip takes part. For that channel, EMVCo publishes separate specifications for [3-D Secure](#3-d-secure) and for payment tokens, which are used in [network tokens](#network-token). The shared name causes confusion: "EMV 3DS" is an online authentication protocol and has no chip involved.

EMVCo does not set network rules or enforce adoption. Each [card network](#card-network) decides those separately, including the chip [liability shift](#liability-shift). Where it applies, a [merchant](#merchant) that swipes a chip card on a terminal that cannot read chips can be liable for resulting counterfeit fraud.

_Usage:_

"The new terminal keeps failing on chip, so staff are just swiping."

"Stop that. If those turn out to be counterfeit, the liability can land on us. Get the reader replaced."

### ISO 8583

ISO 8583 is the international standard for the messages that card systems exchange, such as authorization requests and responses. It defines a common interface between [acquirers](#acquirer) and [issuers](#issuer), usually through a [card network](#card-network). The current edition is ISO 8583:2023. Older editions remain in production.

An ISO 8583 message has three main parts.

| Part                  | Purpose                                       | Example                     |
| --------------------- | --------------------------------------------- | --------------------------- |
| Message type indicator | Says what the message is                     | `0100` authorization request |
| Bitmap                | Marks which data fields are present           | Bits for fields 2, 3, 4     |
| Data elements         | Carry the values                              | [PAN](#pan), amount, response code |

Mastercard's rules show how these labels appear in practice.

| Message | Meaning                         |
| ------- | ------------------------------- |
| `0100`  | Authorization request           |
| `0110`  | Authorization response          |
| `0400`  | Reversal request                |
| `0420`  | Acquirer reversal advice        |
| `1240`  | First presentment, for [clearing](#clearing) |

The standard is a framework, and each network implements its own variant. Field usage, private data elements and code values differ between Visa, Mastercard and domestic switches. A parser built from the ISO document alone will not correctly handle a real network feed, so work from the network or processor's interface specification.

Most application developers never see ISO 8583 because a [payment service provider](#payment-service-provider) wraps it in a JSON API. It still shapes what they receive. A [decline code](#decline-code) such as `51` comes from a response code field, and a truncated [statement descriptor](#statement-descriptor) reflects a fixed-length name field.

Engineers working closer to the rails meet different failures: a bitmap that does not match the fields sent, an amount in the wrong [minor unit](#minor-unit), or a reversal that omits the original transaction's reference data. Log parsed messages with the PAN and other sensitive fields masked, since raw dumps bring logs into [PCI DSS](#pci-dss) scope.

ISO 8583 is separate from [ISO 20022](#iso-20022), the data standard widely used for bank payments.

_Usage:_

"The processor rejected our message but the JSON looks fine."

"Check the ISO 8583 output. The bitmap flags field 43, but our mapper never set the merchant name."

### Decline code

A decline code is the value returned when a [card authorization](#card-authorization) is refused. It usually originates from the [issuer](#issuer) in the response code field of an [ISO 8583](#iso-8583) message, though a network, [acquirer](#acquirer) or fraud tool can also generate one. Examples include `51` for insufficient funds and `05` for "do not honor".

Meanings are not identical across networks, and [payment service providers](#payment-service-provider) often translate raw codes into their own labels. Keep the original code as well.

Visa's rules group decline codes into four categories that control retry behaviour.

| Visa category                | Example codes                            | [Merchant](#merchant) response                      |
| ---------------------------- | ---------------------------------------- | -------------------------------------- |
| 1. Issuer will never approve | `04`, `41` lost, `43` stolen, `46` closed | Do not retry this card                 |
| 2. Cannot approve at this time | `51` funds, `61` limit, `91` issuer down | Retry within Visa's limits             |
| 3. Data quality              | `54` expired, `82` failed card check     | Correct the data, then retry           |
| 4. Generic                   | All other codes                          | Retry within limits, or ask for another card |

These categories are Visa's. Mastercard signals retry guidance differently, including through merchant advice codes in its responses. Reattempt limits are set by each network and can change, so take them from current rules or your provider.

The practical distinction is between a [soft decline](#soft-decline), which may succeed after a change, and a [hard decline](#hard-decline), which will not. A retry job that treats all failures the same will keep charging lost or closed cards, adding cost and possibly breaching network limits. This is a common defect in [recurring billing](#recurring-billing) and [dunning](#dunning).

Be careful with customer messages. Showing "suspected fraud" or "stolen card" can alert a criminal and embarrass a real customer. Say the payment was declined and suggest another method. A jump in one code can indicate an integration problem or [card testing](#card-testing).

_Usage:_

"The billing job retried this card eleven times last week."

"It's a code 46, closed account. That's category 1 for Visa, so we should never have retried it."

### Soft decline

A soft decline is a card refusal that may succeed if something changes. The term has two uses, and teams often mix them up.

| Use    | Meaning                                                    | Correct response                  |
| ------ | ---------------------------------------------------------- | --------------------------------- |
| Narrow | [Issuer](#issuer) requires [strong customer authentication](#strong-customer-authentication) | Authenticate, then send a new request |
| Broad  | Any temporary condition, such as insufficient funds or an issuer outage | Retry later, within network limits |

The narrow sense comes from European regulation. Under [PSD2](#psd2), when a payment needs authentication and arrives without it, the issuer can decline with a specific code asking for it. Mastercard's Transaction Processing Rules require issuers in its listed SCA countries to use a "soft decline" response in this case, and require the [merchant](#merchant) to attempt [3-D Secure](#3-d-secure) with a mandated challenge or use another SCA method. Visa's rules list code `1A`, "additional customer authentication required", for its Europe and CEMEA regions.

The typical symptom appears after a merchant requests an [SCA exemption](#sca-exemption). The issuer does not accept it and returns a soft decline. If the checkout shows a generic "card declined" message, the customer leaves even though one authentication step would probably have completed the sale.

The handling should be explicit in the [payment state machine](#payment-state-machine):

| Step | Who      | What happens                                                |
| ---- | -------- | ----------------------------------------------------------- |
| 1    | Merchant | Sends the [card authorization](#card-authorization)   |
| 2    | Issuer   | Returns the authentication-required code                    |
| 3    | Merchant | Starts 3-D Secure with the customer present                 |
| 4    | Merchant | Sends a new authorization with the authentication data      |

If the customer is absent, as in a [merchant-initiated transaction](#merchant-initiated-transaction), step 3 cannot happen immediately. Ask them to return and authenticate through an email or in-app prompt.

The broad usage needs a [payment retry](#payment-retry) policy with limits and spacing. Contrast both uses with a [hard decline](#hard-decline), where retrying the same card will not help.

_Usage:_

"Conversion in Germany dropped after we turned on the low-value exemption."

"Those are soft declines. We're showing an error instead of falling back to 3DS."

### Hard decline

A hard decline is a card refusal that will not be resolved by trying the same card again. The account may be closed, the card may be reported lost or stolen, or the transaction type may not be allowed. The next step is to get a different payment method.

"Hard decline" is industry shorthand and has no single definition across networks. Visa's rules contain the closest formal version: Category 1 [decline codes](#decline-code), labelled "[issuer](#issuer) will never approve", which a [merchant](#merchant) must never reattempt.

| Visa Category 1 code | Meaning                              |
| -------------------- | ------------------------------------ |
| `04`                 | Pick up card, no fraud               |
| `07`                 | Pick up card, special condition      |
| `41`                 | Lost card                            |
| `43`                 | Stolen card                          |
| `46`                 | Closed account                       |
| `57`                 | Transaction not permitted to [cardholder](#cardholder) |
| `R0`, `R1`, `R3`     | Stop-payment instructions            |

Other networks classify codes differently. Mastercard, for example, uses merchant advice codes to tell merchants how to respond, so a mapping built only from Visa's table is incomplete. Generic codes such as `05` "do not honor" should not automatically count as hard or soft. A [soft decline](#soft-decline), by contrast, may succeed after a change.

The common failure occurs in [recurring billing](#recurring-billing). A subscription job retries a closed card on every [dunning](#dunning) cycle. Each attempt fails, adds authorization cost, and lowers the merchant's [authorization rate](#authorization-rate), and it can also breach network retry rules.

The correct handling is to stop retries, mark the stored card unusable, and ask the customer to update it. An [account updater](#account-updater) or [network token](#network-token) can sometimes supply new details after a reissue, but do not use these to continue charging a card reported stolen or an account the customer closed deliberately. Tell the customer only that the payment was declined.

_Usage:_

"This subscription has failed six months in a row. Should dunning keep going?"

"Check the code. If it's a 46, that's a hard decline, so stop retrying and email them for a new card."

### Merchant category code

A merchant category code (MCC) is a four-digit number that classifies a merchant's type of business, such as a grocery store, airline or software seller. ISO 18245 defines a set of these codes, and [card networks](#card-network) publish their own lists and assignment rules. Visa's Merchant Data Standards Manual says the MCC describes a merchant's primary business, based on annual sales volume.

The [acquirer](#acquirer) or [payment service provider](#payment-service-provider) normally assigns the code at onboarding. It then travels in each [card authorization](#card-authorization) and [clearing](#clearing) record, where several parties use it.

| Party       | How it uses the MCC                                                 |
| ----------- | ------------------------------------------------------------------- |
| [Issuer](#issuer) | Applies rewards, spending controls and block rules         |
| Network     | Applies category-specific rules and [interchange](#interchange-fee) programs |
| Acquirer    | Assesses merchant risk and pricing                                  |
| [Cardholder](#cardholder) | Sees spending categories in a banking app                 |

An incorrect code can cause failures that look unrelated. A company card program may block some categories, so a business coded as gambling or money transfer can see declines from customers whose cards work elsewhere. A wrong MCC can also change the fees the merchant pays, or remove eligibility for a feature such as [incremental authorization](#incremental-authorization), which networks often limit by category.

MCC is different from a product category in your own catalogue. It describes the business as a whole, so one transaction for a single item does not get its own code. A merchant with distinct lines of business may need separate merchant IDs with separate MCCs, depending on network rules.

Deliberately using a misleading code to obtain lower fees or avoid a restricted category is a rule violation, and it can lead to network penalties passed on by the acquirer or to closure of the [merchant account](#merchant-account). If the business changes, ask the acquirer to review the code.

_Usage:_

"Corporate cards keep getting declined on our site, but only corporate cards."

"We're coded under a restricted MCC. Ask the acquirer to review our classification."

### Acquirer reference number

An acquirer reference number (ARN) is an identifier attached to a card transaction when it enters [clearing](#clearing). Both the acquirer and the [issuer](#issuer) can use it to find the same transaction, so it is the reference most often used to trace a [refund](#refund) or a dispute. Visa's rules refer to the acquirer reference number, and Mastercard's rules call the equivalent value acquirer reference data (ARD).

The ARN is one of several identifiers that appear at different stages, and they are easy to confuse.

| Identifier                                             | Created at          | Main use                                 |
| ------------------------------------------------------ | ------------------- | ---------------------------------------- |
| Authorization code                                     | Approval            | Short code from the issuer for that approval |
| [Network transaction ID](#network-transaction-id) | Authorization       | Links related network messages           |
| ARN                                                    | Clearing            | Tracing between acquirer and issuer      |
| Provider payment ID                                    | Provider API        | Finding the payment in your provider     |
| [Merchant's](#merchant) order ID                   | Checkout            | Finding the order in your own system     |

Because the ARN comes from clearing, it does not exist at authorization. A payment that has been authorized but not [captured](#capture) has none, and one that has just been refunded may not have one until the refund is submitted. Model it as optional and populate it from a later event or report.

A typical use is a refund complaint. A customer says the money never arrived, and the [cardholder's](#cardholder) bank says it has no record. The merchant asks its [payment service provider](#payment-service-provider) for the refund's ARN and gives it to the customer, who gives it to the bank. The bank can then search its records for that exact credit. The refund has its own reference, so make sure you send that one and not the ARN of the original purchase.

In a [chargeback](#chargeback), the ARN ties the dispute back to the original sale. Store it against the payment record.

_Usage:_

"Her bank says they can't see the refund we sent."

"Get the ARN for the refund from the provider. The bank can trace the credit with that."

### Network transaction ID

A network transaction ID is the identifier a [card network](#card-network) assigns to a transaction, returned with the [card authorization](#card-authorization) response. Later messages for the same payment, and later payments that depend on it, carry this value so that the network and [issuer](#issuer) can connect them. The generic term covers different network-specific fields.

| Network    | Name in the rules      | Notes                                                             |
| ---------- | ---------------------- | ----------------------------------------------------------------- |
| Visa       | Transaction Identifier | Assigned per transaction, used as an audit trail through the life cycle |
| Mastercard | Trace ID               | Built from network reference data and settlement date             |

It is different from the [acquirer reference number](#acquirer-reference-number), which appears at [clearing](#clearing) and is the usual reference for tracing a [refund](#refund) with a bank. The network transaction ID exists from authorization onward and is primarily for system-to-system linking.

The ID matters most for [stored credentials](#stored-credential). When a customer saves a card, the first [customer-initiated transaction](#customer-initiated-transaction) establishes consent. Each later [merchant-initiated transaction](#merchant-initiated-transaction) references that original ID, showing the issuer that this charge belongs to an agreed series. Under [PSD2](#psd2), this link also helps show why a later charge, made without the customer present, was sent without [strong customer authentication](#strong-customer-authentication).

The failure usually appears during a migration. A company moves to a new [payment service provider](#payment-service-provider), imports card numbers or tokens, but leaves the original network IDs behind. Renewals now look like unlinked payments with no customer present, and issuers decline more of them, often with an authentication-required [soft decline](#soft-decline). Ask for the network transaction IDs in the export, and confirm the new provider can accept them.

Store the ID with the payment method and with each payment, and pass through the value from the correct original transaction. Fabricating or reusing an unrelated ID misrepresents the transaction.

_Usage:_

"Renewal declines jumped right after the PSP migration."

"We imported the tokens but not the network transaction IDs, so the issuers can't link those charges to the original consent."

### Statement descriptor

A statement descriptor is the text identifying a [merchant](#merchant) on a [cardholder's](#cardholder) bank or card statement. It is built from the merchant name and location data carried in the [card authorization](#card-authorization) and [clearing](#clearing) messages, such as the card acceptor name field in [ISO 8583](#iso-8583). The [issuer](#issuer) decides how to display it, so the same payment can look different across banking apps.

An unclear descriptor directly causes disputes. A customer buys from a shop called Northwind but the statement reads `NWD HOLDINGS LTD`. Weeks later they do not recognise it and report it to their bank as fraud, producing a [chargeback](#chargeback) on a legitimate order. This is a common form of [friendly fraud](#friendly-fraud).

Visa's Merchant Data Standards Manual calls the merchant name the most important factor in cardholder recognition, and requires it to be the name most prominently displayed by the merchant and recognised by cardholders. Visa's rules also require [acquirers](#acquirer) to correct names that are non-compliant or that confuse cardholders.

| Descriptor                 | Result                                         |
| -------------------------- | ---------------------------------------------- |
| Legal company name only    | Often unrecognised                             |
| Trading or brand name      | Usually recognised                             |
| Brand and order reference  | Easier to match to a receipt                   |
| Platform name only         | Customer may not recognise the actual seller   |

Length limits are tight and vary by network and provider, so test the shortened version. A [payment service provider](#payment-service-provider) may let you set a static descriptor for the account and a dynamic suffix per payment. Platforms often use a prefix and seller name. If a [merchant of record](#merchant-of-record) is involved, its name normally appears, so mention it at checkout and on the receipt.

To reduce disputes, use the name customers see on your website, send a receipt that shows the exact descriptor, and include a support contact where the format allows.

_Usage:_

"Half of this month's fraud disputes are from customers who did get their orders."

"Our descriptor still shows the holding company. Change it to the store name."

### Address verification

Address verification, often called AVS after the Address Verification Service, is a check that compares the billing address a customer enters with the address held by their [issuer](#issuer). It runs during a [card authorization](#card-authorization) for a [card-not-present transaction](#card-not-present-transaction). The issuer returns a result code, and the [merchant](#merchant) decides what to do with it.

| Result                  | What it suggests                    | Common handling                          |
| ----------------------- | ----------------------------------- | ---------------------------------------- |
| Full match              | Address details agree               | Treat as a positive signal               |
| Postcode only           | Street differs or was not checked   | Weigh with other signals                 |
| Street only             | Postcode differs                    | Weigh with other signals                 |
| No match                | Neither agrees                      | Review or request more authentication    |
| Unavailable             | Issuer or region does not support it | Do not treat as a failure                |

Exact result codes vary by network and provider.

AVS is regional. Visa's rules require issuers to participate in listed regions and countries, including the US, Canada, Europe, Australia, New Zealand and Singapore, and added several Latin American countries effective October 2026. Those rules focus on postal code verification, with street address checked when present. Coverage elsewhere is limited, so a global rule that blocks every non-match will reject many valid international customers.

An AVS mismatch usually does not stop an approval on its own. An issuer can approve a payment with a failed address check, so the merchant holds an approved transaction and has to choose. If it rejects the order, it should send an [authorization reversal](#authorization-reversal). Otherwise the customer sees a pending [authorization hold](#authorization-hold) for an order that was refused.

False mismatches are common, because customers move house or abbreviate street names.

Treat AVS as one input to [risk scoring](#risk-scoring). It does not authenticate the [cardholder](#cardholder), and a match does not provide the [liability shift](#liability-shift) that [3-D Secure](#3-d-secure) can.

_Usage:_

"We're rejecting a lot of UK orders on address mismatch."

"Stop hard-blocking on AVS. Use it as one risk signal and send a reversal when we do refuse."

## Section 4 — Security and Compliance

### PCI DSS

PCI DSS, the Payment Card Industry Data Security Standard, is the security standard for organisations that store, process or transmit payment card account data, or that can affect its security. It is published by the PCI Security Standards Council (PCI SSC), founded by the major [card networks](#card-network). The current series is v4.x, and the Council's document library holds the latest revision.

Account data has two parts, and the rules treat them differently.

| Data type                     | Examples                                  | Storage after authorization        |
| ----------------------------- | ----------------------------------------- | ---------------------------------- |
| Cardholder data               | [PAN](#pan), name, expiry, service code | Allowed if protected and justified |
| Sensitive authentication data | Full track, [CVV](#cvv), PIN          | Not allowed, even if encrypted     |

A narrow exception exists for [issuers](#issuer) and companies supporting issuing services.

The Council writes the standard, but it does not enforce it. Whether an organisation must comply or validate is decided by those running compliance programs.

| Party                      | Role                                                  |
| -------------------------- | ----------------------------------------------------- |
| PCI SSC                    | Publishes the standard and trains assessors           |
| Payment brands             | Set compliance programs and any penalties             |
| [Acquirers](#acquirer) | Require their [merchants](#merchant) to validate  |
| Qualified Security Assessor | Independently assesses an organisation               |
| Merchants and providers    | Implement and maintain the controls                   |

PCI DSS is a contractual industry standard and not, in general, a law, although some jurisdictions refer to it. A merchant usually encounters it through an acquirer's request for a [self-assessment questionnaire](#self-assessment-questionnaire) or a formal assessment report.

The practical work is reducing scope, meaning the set of systems the standard covers. Teams do this by not handling card data at all, using [hosted payment fields](#hosted-payment-fields), [tokenization](#tokenization) or [point-to-point encryption](#point-to-point-encryption).

Scope often grows by accident. A log line captures a card number, or a marketing script is added to the payment page. Requirements 6.4.3 and 11.6.1 address that second risk by requiring control and monitoring of payment page scripts.

_Usage:_

"We use a PSP, so PCI doesn't apply to us, right?"

"It still applies. The PSP shrinks our scope, but we still validate with the right SAQ."

### Self-assessment questionnaire

A self-assessment questionnaire (SAQ) is a form that eligible organisations use to validate their [PCI DSS](#pci-dss) compliance without a full on-site assessment. The right version depends on how the business accepts cards.

| SAQ    | Typical [merchant](#merchant)                                     |
| ------ | --------------------------------------------------------------------- |
| A      | Card-not-present, with all account data functions fully outsourced    |
| A-EP   | E-commerce where the merchant's site can affect payment page security |
| B      | Imprint machines or standalone dial-out terminals                     |
| B-IP   | Standalone approved terminals with an IP connection                   |
| C      | Payment application connected to the internet, no electronic storage  |
| C-VT   | Manual entry into a third-party virtual terminal on an isolated device |
| P2PE   | Only a validated, PCI-listed [point-to-point encryption](#point-to-point-encryption) solution |
| SPoC   | Listed software-based PIN entry solution on a commercial mobile device |
| D      | All other eligible merchants, and all eligible service providers      |

An [acquirer](#acquirer) or payment brand decides whether a merchant may self-assess or needs an assessor's report.

A common mistake is assuming any hosted checkout qualifies for SAQ A. The v4.0.1 revision of SAQ A removed requirements 6.4.3, 11.6.1 and 12.3.1 from that form and added an eligibility criterion: an e-commerce merchant must confirm its site is not susceptible to attacks from scripts that could affect its systems.

PCI SSC's FAQ 1588 explains that this criterion applies to pages that embed a provider's form, such as through an iframe with [hosted payment fields](#hosted-payment-fields). It does not apply to a full redirect to the provider or a fully outsourced flow such as an emailed payment link. A merchant can meet it with protective techniques or a compliant provider's confirmation.

If a developer later adds a custom card form or stores card numbers, the business may no longer qualify, so review eligibility whenever checkout changes.

_Usage:_

"We embed the PSP's iframe, so we just tick SAQ A?"

"Only if we meet the script-attack criterion. Get the provider's confirmation or put the controls on our page."

### Tokenization

Tokenization replaces a sensitive value, such as a card's [PAN](#pan), with a substitute called a token. The token can be stored and passed around in place of the card number, and only a controlled system can map it back or use it to make a payment. It is the usual way a [merchant](#merchant) keeps a customer's card on file without holding the card number.

Tokenization differs from encryption. Encrypted data can be recovered by anyone holding the key, while a token normally has no mathematical relationship to the original and is resolved by lookup in a [card vault](#card-vault) or by a token service.

"Token" covers several things in payments, and the differences matter.

| Type                               | Created by                       | Usable where                     |
| ---------------------------------- | -------------------------------- | -------------------------------- |
| PSP token                          | [Payment service provider](#payment-service-provider) | Usually that provider only |
| [Network token](#network-token) | Network token service         | Across the network, within its domain limits |
| Device wallet token                | Network token service, for a wallet | That device or wallet          |
| Merchant-internal token            | Merchant's own vault             | That merchant's systems          |

The first two are often confused. A team switching providers can discover that its saved PSP tokens do not work elsewhere, and that a card data migration is needed before renewals can continue.

Tokenization reduces [PCI DSS](#pci-dss) scope but does not remove it. PCI SSC's tokenization guidance says the tokenization system itself remains part of the cardholder data environment. Systems holding only tokens may fall out of scope if they have no route back to the PAN. A token that can itself initiate a transaction may still need protection because it can be used to spend money.

For that reason, restrict which API keys can charge a token, and treat token stores as sensitive even when they contain no card numbers.

_Usage:_

"We tokenized everything, so a leak of this table is harmless, right?"

"Not quite. Those tokens can charge customers through our API key, so they still need protecting."

### Network token

A network token is a substitute for a card's [PAN](#pan), issued through a [card network's](#card-network) token service and recognised from the point of purchase through the [acquirer](#acquirer) and network to the [issuer](#issuer). It follows EMVCo's Payment Tokenisation Specification, where it is called an [EMV](#emv) Payment Token. Visa Token Service and Mastercard Digital Enablement Service are two network implementations.

| Role                  | Who                                    | What it does                                   |
| --------------------- | -------------------------------------- | ---------------------------------------------- |
| Token Requestor       | [Merchant](#merchant), wallet or provider | Registers and requests tokens                  |
| Token Service Provider | Usually the network                   | Creates tokens and maps them to the PAN        |
| Issuer                | [Cardholder](#cardholder)'s institution               | Approves token creation and the payments       |
| Token User            | Merchant or wallet                     | Presents the token for payment                 |

A token is limited in use, for example to one merchant, one device, or a specific payment scenario, so a stolen token is worth far less than a card number. Depending on the use case, a one-time token cryptogram accompanies the payment to prove it is genuine. EMVCo also defines a Payment Account Reference, which lets systems link different tokens for the same underlying account without exposing the PAN.

The term is most often confused with a PSP [token](#tokenization).

| Property            | Network token                    | PSP token                     |
| ------------------- | -------------------------------- | ----------------------------- |
| Issued by           | Token service, usually network   | Payment provider              |
| Seen by issuer      | Yes                              | No, the issuer sees the PAN   |
| Works across providers | Possible, if set up for it    | Generally no                  |
| Follows card changes | Can be updated by the issuer    | Depends on the provider       |

Because a network token can stay valid when the physical card is reissued, it can reduce failures on [recurring billing](#recurring-billing) after a card expires. A payment sent without a required cryptogram can still be declined. Code that reads a token's first digits as the card's [BIN](#bin) may also misclassify the card, so ask your provider for the underlying card attributes.

_Usage:_

"Renewals keep failing whenever banks reissue cards."

"Turn on network tokens for stored cards. The issuer updates them when the card changes."

### Card vault

A card vault is a secured system that stores card numbers and gives other systems a [token](#tokenization) to use in their place. When a payment is needed, an authorised service sends the token, and the vault supplies the [PAN](#pan) to the payment connection without exposing it to the rest of the application.

| Step | Who                  | What happens                                     |
| ---- | -------------------- | ------------------------------------------------ |
| 1    | Checkout             | Sends card details directly to the vault         |
| 2    | Vault                | Encrypts and stores the PAN, returns a token     |
| 3    | Application          | Stores only the token and display details        |
| 4    | Payment service      | Requests a charge using the token                |
| 5    | Vault                | Forwards the PAN to the [acquirer](#acquirer) or processor    |

A vault holds the data that attackers want, so it is firmly in [PCI DSS](#pci-dss) scope. It can store the PAN and expiry date, but it must not keep the [CVV](#cvv) after [card authorization](#card-authorization).

| Option                                                        | Benefit                   | Cost                                 |
| ------------------------------------------------------------- | ------------------------- | ------------------------------------ |
| [Payment service provider](#payment-service-provider) vault | Least effort and scope    | Tied to that provider                |
| Independent third-party vault                                 | Can route to several PSPs | Another vendor, some integration work |
| Self-hosted vault                                             | Full control of the data  | Full PCI burden and security operations |

The choice usually becomes visible when a business wants to change provider or add a second one for [payment routing](#payment-routing). With a provider vault, stored cards cannot be moved by the [merchant](#merchant). The old provider must export the data securely to a PCI-compliant recipient, which can take weeks and depends on the contract. Read the export terms before committing.

Migrations carry their own failure risk. Token mappings can be incomplete, and renewals can start declining if [network transaction IDs](#network-transaction-id) were not transferred with the cards. Run a test batch and compare [authorization rates](#authorization-rate) before and after.

_Usage:_

"Can we export our saved cards ourselves and upload them to the new provider?"

"No. The old vault has to transfer them directly to the new one under PCI controls."

### Point-to-point encryption

Point-to-point encryption (P2PE) encrypts card data inside a secure payment terminal at the moment the card is read, and keeps it encrypted until it reaches a protected decryption environment away from the [merchant](#merchant). The shop's network, tills and back-office systems carry only ciphertext they cannot read. It is used with payment terminals, not online checkout.

The term has a general meaning and a specific one under [PCI DSS](#pci-dss). Any vendor can describe its terminal as "encrypted". PCI P2PE is a separate PCI SSC standard, and only solutions validated against it and listed by the Council carry its compliance benefits.

| Feature                  | Encrypted terminal (generic)     | Validated PCI P2PE solution              |
| ------------------------ | -------------------------------- | ---------------------------------------- |
| Independently assessed   | Not necessarily                  | Yes, against the P2PE standard           |
| Listed by PCI SSC        | No                               | Yes                                      |
| Eligible for SAQ P2PE    | No                               | Yes, if the merchant meets the criteria  |

A retailer buys terminals advertised as end-to-end encrypted and assumes it qualifies for the shorter [self-assessment questionnaire](#self-assessment-questionnaire). An assessor then finds the solution is not on the PCI list, so the shop's network remains in scope. Check the PCI SSC listing before buying and again at renewal, because a solution whose listing has expired is no longer treated as validated, and the merchant should then ask its [acquirer](#acquirer) what applies.

SAQ P2PE covers merchants that take account data only through a validated solution's terminals and have no clear-text account data on their computer systems. It does not apply to e-commerce. The merchant must also follow the solution's instruction manual.

P2PE is different from TLS, the encryption used for web traffic, which protects data between two connected systems. P2PE protects the card data from the terminal itself.

_Usage:_

"The vendor says the terminals are encrypted, so our network is out of scope."

"Only if it's a validated P2PE solution. Check that it's listed by PCI SSC."

### Hosted payment fields

Hosted payment fields are card input boxes served by a [payment service provider](#payment-service-provider) and embedded in a [merchant's](#merchant) checkout, usually as iframes. An iframe is a small page from another domain displayed inside the main page. The customer appears to type on the merchant's site, but the [PAN](#pan) and [CVV](#cvv) go directly from the browser to the provider, which returns a [token](#tokenization).

| Step | Who      | What happens                                          |
| ---- | -------- | ----------------------------------------------------- |
| 1    | Browser  | Loads the merchant page and the provider's iframes    |
| 2    | Customer | Types card details into the iframes                   |
| 3    | Provider | Receives the card data and returns a token            |
| 4    | Merchant | Sends the token from its server to create the payment |

The approach sits between two other integration styles.

| Integration            | Who controls the page | Card data reaches merchant servers? | Common SAQ        |
| ---------------------- | --------------------- | ----------------------------------- | ----------------- |
| Full redirect          | Provider              | No                                  | SAQ A             |
| Hosted payment fields  | Merchant, with provider inputs | No                         | SAQ A, if eligible |
| Merchant script-built form | Merchant          | No, but its page handles the data | SAQ A-EP          |
| Direct API             | Merchant              | Yes                                 | SAQ D             |

Embedded fields do not make the page safe by default. A malicious script on the surrounding page cannot normally read an iframe from another origin, but it could draw a fake form over it or send the customer elsewhere. For this reason, the [PCI DSS](#pci-dss) v4.0.1 version of the [self-assessment questionnaire](#self-assessment-questionnaire) SAQ A requires merchants embedding a provider's form to confirm their site is not susceptible to script attacks.

Engineers usually encounter a different failure. A tightened Content Security Policy, the browser rule listing allowed content sources, blocks the provider's domain. The card fields then render blank or the Pay button does nothing, often in production only. Allow the provider's documented domains and test checkout after changing security headers.

_Usage:_

"The card fields are blank in production, but they work locally."

"The new CSP is blocking the provider's iframe. Add their domains to frame-src."

### 3-D Secure

3-D Secure (3DS) is a messaging protocol that lets a card [issuer](#issuer) authenticate a customer during an online payment. [EMVCo](#emv) publishes the current specification as EMV 3-D Secure, and networks brand their programs, for example Visa Secure and Mastercard Identity Check. The "three domains" are the [acquirer](#acquirer) side, the issuer side and the interoperability layer connecting them.

| Step | Who                 | What happens                                                |
| ---- | ------------------- | ----------------------------------------------------------- |
| 1    | [Merchant's](#merchant) 3DS Server | Sends transaction and device data                          |
| 2    | Directory Server    | Run by the network, routes the request to the issuer        |
| 3    | Access Control Server | Issuer's system assesses risk                              |
| 4a   | Issuer              | Frictionless: authenticates without involving the customer  |
| 4b   | Customer            | Challenge: completes an app approval, passcode or biometric |
| 5    | Merchant | Includes the authentication result in the [card authorization](#card-authorization) |

Authentication and authorization are separate. 3DS asks "is this the real [cardholder](#cardholder)?". The authorization that follows asks "will the issuer approve this payment?". A customer can pass a challenge and still be declined for insufficient funds.

3DS is often confused with [strong customer authentication](#strong-customer-authentication). SCA is a legal requirement under [PSD2](#psd2) in the EEA. 3DS is a technical protocol and a common way of meeting that requirement for cards. A frictionless 3DS result is not necessarily SCA, and 3DS is also used in regions with no SCA rule.

3DS also supports a [liability shift](#liability-shift) for fraud, under network rules. Visa's rules, for example, make certain fraud disputes invalid for a transaction authenticated through Visa Secure when the authorization carried the required authentication value and indicator.

A frequent bug is losing that value. The challenge succeeds, but the integration does not pass the authentication data into the authorization, so the issuer sees an unauthenticated payment. It can then return a [soft decline](#soft-decline), and the merchant loses any fraud protection.

_Usage:_

"The customer passed the 3DS challenge, but we still got a fraud chargeback."

"Check the auth request. We dropped the CAVV, so the issuer never saw the authentication."

### Strong customer authentication

Strong customer authentication (SCA) is a legal requirement in the European Economic Area, set by [PSD2](#psd2), that a payer be authenticated using at least two independent factors from different categories. Article 4(30) defines the categories, and independence means that compromising one factor does not compromise the others.

| Category   | Meaning                        | Examples                     |
| ---------- | ------------------------------ | ---------------------------- |
| Knowledge  | Something only the user knows  | PIN, password                |
| Possession | Something only the user has    | Registered phone, chip card  |
| Inherence  | Something the user is          | Fingerprint, face            |

Article 97 requires a [payment service provider](#payment-service-provider) to apply SCA when a payer accesses a payment account online, initiates an electronic payment, or takes a remote action that could carry fraud risk. For remote payments, the authentication must also be dynamically linked to the specific amount and payee. Delegated Regulation (EU) 2018/389 holds the detail, and the UK maintains its own version through the FCA.

SCA is an outcome and [3-D Secure](#3-d-secure) is a method. For online card payments, 3DS with a challenge is the usual way to meet it.

The obligation falls on the payer's provider, usually the [issuer](#issuer), and the [merchant](#merchant) must support the flow. Under Article 74(2), if the payer's provider does not require SCA, the payer does not bear financial losses unless they acted fraudulently, and a payee or payee's provider that fails to accept SCA must [refund](#refund) the damage caused to the payer's provider.

An [SCA exemption](#sca-exemption) can remove the step, and purely [merchant-initiated transactions](#merchant-initiated-transaction) and mail or telephone orders are outside the requirement.

The symptom for a merchant is a rise in [soft declines](#soft-decline) from European cards when checkout does not support authentication. Saved-card flows often fail the same way if SCA was not performed when the card was first stored.

_Usage:_

"Why are EU cards failing when our US cards are fine?"

"Issuers are asking for SCA and our checkout has no 3DS step. We need to add it."

### SCA exemption

An SCA exemption is a condition in EU rules that allows a [payment service provider](#payment-service-provider) not to apply [strong customer authentication](#strong-customer-authentication) to a payment. The exemptions are in Chapter III of Commission Delegated Regulation (EU) 2018/389 under [PSD2](#psd2). A provider is "allowed not to apply" SCA and is never obliged to skip it. The table lists the main payment exemptions.

| Article | Exemption                  | Applies to                                                  |
| ------- | -------------------------- | ----------------------------------------------------------- |
| 11      | Contactless at point of sale | Small in-person payments, within cumulative limits        |
| 12      | Unattended terminals       | Transport fares and parking fees                            |
| 13      | Trusted beneficiaries      | Payees the payer listed with their provider                 |
| 14      | Recurring transactions     | Later payments in a series with the same amount and payee   |
| 16      | Low-value transactions     | Small remote payments, within cumulative limits             |
| 17      | Secure corporate payments  | Dedicated non-consumer processes accepted by the regulator  |
| 18      | Transaction risk analysis  | Low-risk remote payments, tied to the provider's fraud rate |

Amount limits are in the regulation and may change.

An exempt payment is covered by SCA rules but relieved of the step, while out-of-scope payments are not covered at all. The EBA and ECB list purely [merchant-initiated transactions](#merchant-initiated-transaction), mail and telephone orders, and many "one-leg" payments where one provider is outside the EEA as outside SCA.

The [merchant](#merchant) or [acquirer](#acquirer) can request an exemption, but the [issuer](#issuer) has the final say. An EBA Q&A confirms the issuer can accept an acquirer's risk-analysis exemption, or refuse it and apply SCA. Cumulative counters are invisible to the merchant, so a small payment can still receive a [soft decline](#soft-decline). Checkout must be able to fall back to [3-D Secure](#3-d-secure).

An exempted payment also generally does not get the fraud [liability shift](#liability-shift) that an authenticated one can, although network rules vary.

_Usage:_

"We flagged this as low value, so why did the issuer decline it?"

"The issuer tracks the cumulative limit and can refuse the exemption. Fall back to 3DS on that code."

### Liability shift

A liability shift is a [card network](#card-network) rule that moves the cost of certain fraud from one party to another when a security measure was or was not used. It determines whether the [merchant's](#merchant) side or the [issuer](#issuer) absorbs the loss on a fraudulent transaction. The two common forms cover chip payments and online authentication.

| Type                    | Where                               | Who usually bears the fraud                                       |
| ----------------------- | ----------------------------------- | ----------------------------------------------------------------- |
| Chip                    | [Card-present](#card-present-transaction), participating regions | The party that did not support [EMV](#emv) chip                |
| [3-D Secure](#3-d-secure) | [Card-not-present](#card-not-present-transaction) | Issuer, where the payment was properly authenticated  |
| No shift                | Other online payments               | Usually the merchant                                              |

The details are network- and region-specific.

| Network    | Chip rule                                   | Authentication rule                                          |
| ---------- | ------------------------------------------- | ------------------------------------------------------------ |
| Visa       | Dispute Conditions 10.1 and 10.2, with listed regions | Condition 10.4 invalid for qualifying Visa Secure payments |
| Mastercard | Reason code 4870, chip liability shift      | Reason code 4837 excludes properly authenticated payments    |

A common misunderstanding is believing that 3-D Secure stops all [chargebacks](#chargeback). The shift applies to fraud claims. A customer who says goods never arrived or were defective can still dispute an authenticated payment, because that is a consumer dispute.

A shift can also fail for technical reasons. If an integration drops the authentication value from the [card authorization](#card-authorization), or sends the wrong electronic commerce indicator, the network treats the payment as unauthenticated even though the customer completed a challenge. Network rules also contain exclusions, and an [SCA exemption](#sca-exemption) generally leaves liability where it was.

This contractual shift is different from the legal allocation under [PSD2](#psd2). Article 74(2) says that a payee or payee's provider that fails to accept [strong customer authentication](#strong-customer-authentication) must [refund](#refund) the financial damage caused to the payer's provider.

Store the authentication result on each payment so it can be used as evidence in [representment](#representment).

_Usage:_

"We used 3DS on that order, so why are we losing this chargeback?"

"It's a not-received dispute. The liability shift only covers fraud claims."

### PSD2

PSD2 is the EU's second Payment Services Directive, formally Directive (EU) 2015/2366. It sets the rules for who may provide payment services in the EU and European Economic Area, what those providers owe their customers, and how payments must be secured. It takes effect through each member state's national law, so details differ by country.

| Area              | What PSD2 does                                                          |
| ----------------- | ----------------------------------------------------------------------- |
| Licensing         | Defines payment services and who must be authorised to provide them     |
| Security          | Requires [strong customer authentication](#strong-customer-authentication) (SCA) in Article 97 |
| Customer rights   | Sets [refund](#refund) and liability rules for unauthorised payments               |
| Third-party access | Creates regulated access to accounts, the basis of EU [open banking](#open-banking) |

Detailed security rules are in a separate, directly applicable law, Commission Delegated Regulation (EU) 2018/389. SCA is one part of PSD2, and [3-D Secure](#3-d-secure) is a technical protocol the directive does not name.

When both the payer's and payee's providers are in the EEA, SCA generally applies. When only one is, the payment is a "one-leg" transaction. A Commission answer published by the European Banking Authority says that an [acquirer](#acquirer) outside the EU is not subject to PSD2, and the EU [issuer](#issuer) must decide whether to block such a payment or carry the liability. A non-EU [merchant](#merchant) selling to Europeans may therefore see [soft declines](#soft-decline) despite having no direct PSD2 obligations.

The UK implemented PSD2 before leaving the EU and now maintains its own rules through the FCA.

A replacement is in progress. The EU reached a provisional agreement in November 2025 on a Payment Services Regulation and a third directive, PSD3. As of November 2026, Parliament's procedure files list both as awaiting a second-reading vote, with no Official Journal publication. Until the new laws apply, PSD2 remains in force.

_Usage:_

"We're a US company. Why does PSD2 affect our checkout?"

"Our customers' banks are in the EU, so they may still ask for SCA. Add 3DS for those cards."

### KYC

KYC, or Know Your Customer, is the process a regulated firm uses to identify a customer, verify that identity, and understand the purpose of the relationship. It is part of [AML](#aml) compliance. In a payments company, KYC normally applies when opening an account, and again when something about the customer or their activity changes.

International standards come from the Financial Action Task Force (FATF), whose Recommendation 10 sets out customer due diligence. Actual obligations come from national or regional law, so they depend on the firm's licence and location.

| Region | Main source                                                                                   |
| ------ | --------------------------------------------------------------------------------------------- |
| EU     | National laws implementing the AML directives. Regulation (EU) 2024/1624 applies generally from 10 July 2027 |
| US     | Bank Secrecy Act rules, including customer identification programs for banks                  |
| UK     | Money Laundering Regulations                                                                  |

A typical KYC flow has several steps.

| Step      | What happens                                                            |
| --------- | ----------------------------------------------------------------------- |
| Collect   | Name, date of birth, address, identity document                         |
| Verify    | Check the document or data against reliable sources                     |
| Screen    | Run [sanctions screening](#sanctions-screening) and politically-exposed-person checks |
| Assess    | Assign a risk level                                                     |
| Monitor   | Review activity and refresh information over time                       |

KYC concerns individuals, while [KYB](#kyb) applies similar checks to businesses and their owners. It is also separate from authentication: KYC establishes who a customer is at onboarding, whereas [strong customer authentication](#strong-customer-authentication) checks that the person making a payment is that customer.

Users experience KYC as friction. A wallet asks for a passport before raising a limit, a selfie check rejects a valid document, or an account is restricted because details need renewing. Engineers should model verification as a set of states, such as pending, verified, rejected and needs refresh. A single boolean cannot represent an expired document or a re-review.

Treat identity documents as highly sensitive personal data, and keep them out of support tools and logs.

_Usage:_

"Why can't this user withdraw? Their balance is fine."

"Their KYC expired when the ID document lapsed. They need to re-verify before we can release payouts."

### KYB

KYB, or Know Your Business, is the process of verifying a business customer: that it legally exists, what it does, who owns it and who controls it. Banks, [acquirers](#acquirer) and [payment facilitators](#payment-facilitator) run KYB before letting a company accept or move money, as part of their [AML](#aml) and risk controls.

The difficult part is identifying beneficial owners, the natural persons who ultimately own or control a company. FATF standards and Regulation (EU) 2024/1624 both require firms to identify beneficial owners and understand the ownership and control structure. In the US, FinCEN's customer due diligence rule sets beneficial ownership requirements for covered financial institutions, and FinCEN proposed changes to it in November 2026. Ownership thresholds and methods differ by jurisdiction.

| Check          | Question                               | Typical evidence                     |
| -------------- | -------------------------------------- | ------------------------------------ |
| Legal entity   | Does the company exist?                | Registry extract, tax number         |
| Business model | What does it actually sell?            | Website, invoices, description       |
| Ownership      | Who ultimately owns it?                | Shareholder register, group chart    |
| Control        | Who runs it?                           | Director list, officer details       |
| Individuals    | Are those people who they say?         | [KYC](#kyc) on owners and directors |
| Screening      | Is anyone restricted?                  | [Sanctions screening](#sanctions-screening) |

For a [merchant](#merchant), KYB also covers commercial risk: [refund](#refund) policy, delivery times and whether the product fits its [merchant category code](#merchant-category-code).

The failure businesses feel is a hold on funds. Many platforms allow a new seller to begin processing after basic checks, then request full documents once volume grows. If the seller does not respond, or a new investor changes the ownership, the [payout](#payout) can be paused until the review is complete.

Ownership and directors change, so records need periodic and event-driven review. Engineers should store ownership as a graph or linked records, since a flat field for "owner" cannot represent a chain of holding companies.

_Usage:_

"This seller's payout has been on hold since their funding round."

"The cap table changed. We need updated beneficial owner details before KYB can clear."

### AML

AML, or anti-money laundering, is the set of laws and internal controls that regulated firms use to detect, prevent and report attempts to pass off criminal money as legitimate. The FATF Recommendations set the international standard, and each country turns them into binding law.

A program usually has these parts.

| Control                 | What it does                                                         |
| ----------------------- | -------------------------------------------------------------------- |
| Risk assessment         | Identifies which products, customers and countries carry most risk   |
| Customer due diligence  | [KYC](#kyc) for people and [KYB](#kyb) for businesses        |
| Transaction monitoring  | Flags activity that does not fit the customer's profile              |
| Investigation           | Analysts review alerts and record decisions                          |
| Reporting               | Files suspicious activity reports with the national authority        |
| Record keeping          | Retains evidence for a legally required period                       |

AML differs from fraud prevention, though the tools overlap. Fraud controls protect the firm and its customers from being robbed. AML looks for customers who may be successfully moving their own illicit funds, where nobody complains. [Sanctions screening](#sanctions-screening) is also distinct: it checks whether dealing with a party is prohibited at all.

Warning patterns include activity far above a customer's stated business, funds moving in and immediately back out, and payments split to stay under reporting limits. A [merchant](#merchant) account processing payments unrelated to its declared business can indicate transaction laundering, where one business runs card payments for another, undisclosed one.

The symptom for customers is an unexplained restriction. Support cannot say why, and this is often deliberate. Laws in many jurisdictions prohibit "tipping off", meaning telling someone that a suspicious activity report has been filed or is being considered. Engineers should therefore keep case details out of customer-facing logs and support tools, and give agents an approved neutral script.

Record each alert, the analyst's decision and the reasoning, since regulators may ask to see that trail.

_Usage:_

"A customer is demanding to know why their account is restricted. What can I say?"

"Use the standard compliance script. Don't speculate, and don't mention any AML review."

### Sanctions screening

Sanctions screening is the process of checking customers, counterparties and payments against government sanctions lists to avoid prohibited dealings. Common sources include the US Treasury's Office of Foreign Assets Control (OFAC), the EU consolidated list, the UK's sanctions list and United Nations lists. Which regimes bind a firm depends on its location, nationality and partners.

Screening usually happens at several points.

| Point       | What is checked                                         | Example result                     |
| ----------- | ------------------------------------------------------- | ---------------------------------- |
| Onboarding  | Customer, directors and beneficial owners | Account opening is paused          |
| Ongoing     | Existing customers against updated lists                | Account is restricted              |
| Transaction | Payer, payee, banks, countries and payment text         | Payment is held for review         |

[AML](#aml) is largely risk-based and focuses on suspicious behaviour. A sanctions prohibition can apply regardless of behaviour, and OFAC can impose civil penalties on a strict liability basis, meaning a firm can be liable even if it did not know a transaction was prohibited. Some regimes extend to entities owned or controlled by a listed person, so combine screening with [KYB](#kyb) ownership data.

Under US rules, some property must be blocked, meaning frozen and reported, while other prohibited transactions are rejected and returned. Returning funds that should have been blocked can itself be a violation. Compliance teams, and not application code, should decide which outcome applies.

The main operational problem is false positives. Names are transliterated in different ways and many people share them, so screening uses fuzzy matching. A customer named similarly to a listed person may find a [payout](#payout) or payment held until an analyst clears the alert.

Engineers should rescreen when lists change, version the list used for each decision, and fail closed if the screening service is unavailable on flows that require it. Record who cleared each alert and why.

_Usage:_

"Why is this payout stuck in review? The seller's been with us for years."

"Their name partly matched a new sanctions listing. Compliance has to clear the alert before it can go out."

## Section 5 — Fraud and Disputes

### Card-present transaction

A card-present transaction is a payment in which the card and [cardholder](#cardholder) are physically at the point of sale. Visa's rules call this a Card-Present Environment, and define it by both being present at the [merchant's](#merchant) premises or a similar acceptance point.

| Entry method           | How data is captured              | Fraud protection                       |
| ---------------------- | --------------------------------- | -------------------------------------- |
| Chip                   | Card generates a cryptogram       | Strong against counterfeit cards       |
| Contactless card       | Card generates a cryptogram       | Strong against counterfeit cards       |
| Mobile wallet tap      | Device presents a [network token](#network-token) | Token and device authentication |
| Magnetic stripe        | Static data read from the stripe  | Weak, data can be copied               |
| Key-entered at terminal | Staff type the number            | Weak, may lose card-present treatment  |

The contrast is with a [card-not-present transaction](#card-not-present-transaction), where no terminal reads the card. Because an [EMV](#emv) chip proves the card is genuine, card-present payments generally carry lower fraud risk, and pricing often reflects that.

The classification comes from data in the [card authorization](#card-authorization) message, such as point-of-sale entry mode. It is not inferred from where the merchant is. A card number keyed in after a chip failure may cost more and give the merchant weaker evidence in a dispute. If a chip card is swiped or keyed where the [liability shift](#liability-shift) applies, the merchant can be liable for counterfeit fraud.

Physical presence does not rule out all fraud. A lost or stolen card can be used in person, particularly for low-value contactless payments that do not ask for a PIN. Under EU rules, the contactless [SCA exemption](#sca-exemption) has cumulative limits, so a terminal may occasionally ask a customer to insert the card and enter a PIN.

_Usage:_

"The terminal asked her for a PIN on a tiny coffee payment. Is it broken?"

"No. She hit the contactless limit on that card, so the issuer wants a chip and PIN."

### Card-not-present transaction

A card-not-present (CNP) transaction is a payment made without the card being read by a terminal, typically online, in an app, by phone or by mail order. Visa's rules call this a Card-Absent Environment. Because no chip takes part, the [merchant](#merchant) has to rely on other signals that the person paying is the real [cardholder](#cardholder).

| Property          | [Card-present](#card-present-transaction) | Card-not-present                        |
| ----------------- | ----------------------------------------------- | --------------------------------------- |
| Card verification | [EMV](#emv) chip cryptogram                 | [CVV](#cvv), [network token](#network-token) |
| Customer check    | PIN or device, where required                   | [3-D Secure](#3-d-secure), account signals |
| Address check     | Not usually relevant                            | [Address verification](#address-verification), where supported |
| Fraud liability   | Depends on chip support                         | Often the merchant, unless authenticated |

The main risk is stolen card details. Data taken in a breach, by phishing or by skimming code on a checkout page can be used remotely without the physical card. For this reason, fraud [chargebacks](#chargeback) concentrate in this channel, and network monitoring focuses on it. Visa's [chargeback ratio](#chargeback-ratio) under its Acquirer Monitoring Program, for example, is based on card-not-present activity.

Controls work best in layers, combining authentication, [velocity checks](#velocity-check), device data and [risk scoring](#risk-scoring). Applying 3-D Secure can provide a [liability shift](#liability-shift) on qualifying fraud claims.

Regulation differs by channel. Under [PSD2](#psd2), remote electronic payments generally need [strong customer authentication](#strong-customer-authentication), with dynamic linking to the amount and payee. Mail and telephone orders are treated as outside that requirement, so correctly flagging them matters. Marking ordinary web payments as telephone orders to avoid authentication misrepresents the transaction and can breach network rules.

CNP data handling also has consequences for compliance. Card entry through [hosted payment fields](#hosted-payment-fields) can reduce [PCI DSS](#pci-dss) scope. Phone payments can bring call recordings into scope.

_Usage:_

"Fraud is only showing up on the website, never in our stores."

"That's expected. Online is card-not-present, so there's no chip. Turn on 3DS for the risky orders."

### Card testing

Card testing is a fraud attack in which criminals use a [merchant's](#merchant) payment flow to find out which stolen or generated card details are valid. Visa calls the wider activity account enumeration. The checkout is used as a validity check, and working cards are used or sold elsewhere.

The usual sign is a sudden burst of [card authorization](#card-authorization) attempts, many of them declined, often for small amounts and often outside business hours.

| Signal                                       | Where to look                     |
| -------------------------------------------- | --------------------------------- |
| Spike in authorization attempts              | Provider dashboard, API metrics   |
| Sharp fall in [authorization rate](#authorization-rate) | Payment monitoring |
| Many different cards from one device, IP or session | Checkout and fraud logs    |
| Many cards sharing a [BIN](#bin)         | [Decline code](#decline-code) reports |
| Repeated [CVV](#cvv) or expiry failures  | Authorization responses           |
| Unusual activity on add-card or donation pages | Endpoint metrics                |

The cost falls on the merchant in several ways: authorization fees, a damaged reputation with [issuers](#issuer), later [chargebacks](#chargeback) on successful attempts, and holds on real customers' cards. Visa's monitoring program, VAMP, includes a separate enumeration measure, so sustained attacks can bring network attention to the merchant and its [acquirer](#acquirer).

Visa's guidance for merchants recommends layered controls.

| Control                                     | Effect                                         |
| ------------------------------------------- | ---------------------------------------------- |
| CAPTCHA on every card-validating request    | Slows automated traffic                        |
| [Velocity checks](#velocity-check)    | Limits attempts per card, device, IP, account  |
| Required CVV and [address verification](#address-verification) | Adds checks on entry     |
| Protect add-card and save-card flows        | Closes commonly overlooked endpoints           |
| Rotate API keys if abused                   | Cuts off stolen credentials                    |

During an active attack, block the traffic quickly and tell your provider or acquirer. Reverse approved test payments with an [authorization reversal](#authorization-reversal), or [refund](#refund) them if already captured, because those [cardholders](#cardholder) did not make them.

Keep customer-facing error messages generic, so the checkout does not reveal which card field failed.

_Usage:_

"We just had 4,000 one-dollar auths in twenty minutes, nearly all declined."

"That's card testing. Turn on the CAPTCHA, rate-limit the endpoint and tell the acquirer."

### Account takeover

Account takeover (ATO) is fraud in which a criminal gains access to a genuine customer's account and acts as that customer. In a payments context, the attacker uses saved cards, spends a stored balance, redirects a [payout](#payout), or changes contact details to lock out the owner. Access commonly comes from reused passwords leaked elsewhere, phishing or malware on the customer's device.

ATO differs from stolen-card fraud. With a stolen card, the fraudster brings a card to a new account. With ATO, the account, the card on file and the purchase history all look legitimate, so payment signals such as a passing [CVV](#cvv) or a known card reveal little. Detection has to focus on the session and the account's behaviour.

| Warning sign                                       | Why it matters                            |
| -------------------------------------------------- | ----------------------------------------- |
| Login from a new device or unusual location        | Possible credential use                   |
| Many failed logins across accounts from one source | Automated password testing against the site |
| Password reset followed quickly by a purchase      | Attacker securing access                  |
| Email, phone or payout details changed             | Locks out the owner or redirects funds    |

The real [cardholder](#cardholder) then disputes the charges, so the [merchant](#merchant) receives a fraud [chargeback](#chargeback) on what looked like a loyal customer's order.

| Control                                            | Purpose                                 |
| -------------------------------------------------- | --------------------------------------- |
| Multi-factor authentication                        | Stolen password alone is not enough     |
| Breached-password checks                           | Blocks known leaked credentials         |
| Login rate limits and [velocity checks](#velocity-check) | Slows automated attempts    |
| Step-up on sensitive changes                       | Reconfirms before payout or email edits |
| Notify the old email or phone of changes           | Lets the real owner react               |
| Delay payouts after bank detail changes            | Gives time to catch a redirect          |

When ATO is confirmed, revoke all sessions and API tokens, reset credentials, reverse attacker changes, and review recent orders and payouts.

_Usage:_

"This customer's been with us five years, and suddenly three orders shipped to a new address."

"Password reset an hour earlier from a new device. Looks like account takeover, so lock it and hold the orders."

### Friendly fraud

Friendly fraud is a [chargeback](#chargeback) raised on a genuine purchase, where the [cardholder](#cardholder) or someone connected to them received the goods or service. The name is misleading because many cases are not deliberate. Visa uses the more neutral term first-party misuse for cardholders reporting fraud on transactions they actually made.

| Cause                   | Example                                                  | Deliberate? |
| ----------------------- | -------------------------------------------------------- | ----------- |
| Unrecognised charge     | Unclear [statement descriptor](#statement-descriptor) | No       |
| Family use              | A child buys in-game currency on a parent's card         | Usually no  |
| Forgotten subscription  | Renewal the customer forgot about                        | Usually no  |
| [Refund](#refund) shortcut | Customer calls the bank instead of the [merchant](#merchant) | Mixed |
| Buyer's remorse         | Customer keeps the item and claims fraud                 | Yes         |

It differs from true third-party fraud, where a stranger used stolen card details. The two look identical to the merchant at first because both typically arrive under a fraud [dispute reason code](#dispute-reason-code). Do not assume dishonesty.

Use a descriptor customers recognise, send clear receipts, remind customers before a renewal, make cancelling easy, and offer a visible refund route so that contacting support is easier than calling the bank.

When a dispute arrives, the merchant can contest it through [representment](#representment) with evidence that the cardholder took part. Visa's Compelling Evidence 3.0, under Dispute Condition 10.4, lets a merchant use matching data from earlier undisputed transactions on the same card, such as IP address or device ID, when specific conditions are met. Those conditions change, so check the current Visa rules. Mastercard has its own evidence requirements for its fraud-related chargebacks.

To be usable, the evidence must be collected at purchase time. Log device, IP, account and delivery data against each order, within applicable privacy law. Each dispute also adds to the merchant's [chargeback ratio](#chargeback-ratio).

_Usage:_

"He says he never bought it, but he's played the game on that account for two years."

"Looks like friendly fraud. Pull the device and IP history and see whether it qualifies for CE 3.0."

### Velocity check

A velocity check is a fraud control that counts how many times something happens within a time window and acts when the count exceeds a limit. In payments, it might count attempts per card in ten minutes, or the number of different cards used by one device in an hour. It is used against automated attacks such as [card testing](#card-testing) and [account takeover](#account-takeover).

A rule has four parts.

| Part   | Options                                                    |
| ------ | ---------------------------------------------------------- |
| Key    | Card fingerprint, device, IP, account, email, [BIN](#bin) |
| Event  | Attempt, decline, approval, new card added, login, [refund](#refund)  |
| Window | Minutes, hours or days                                     |
| Action | Allow, add friction, send to review, block                 |

Different keys catch different patterns.

| Pattern                       | Useful count                               |
| ----------------------------- | ------------------------------------------ |
| One card tried repeatedly     | Attempts per card                          |
| Many cards from one source    | Distinct cards per device, IP or session   |
| Stolen list spread across IPs | Declines per [merchant](#merchant), overall or by BIN   |
| Reused accounts               | Failed logins per account or per source    |

Limits should be based on your own traffic, because a normal pattern for a ticketing site at launch time would look like an attack for a furniture store. Test rules in log-only mode first.

The common failure is blocking legitimate customers. Offices, universities and mobile carriers put many users behind one IP address, so a strict per-IP limit can stop everyone at that location. Combine keys, prefer a step-up such as [3-D Secure](#3-d-secure) over an outright block where possible.

Implementation has its own traps. A counter that reads and then writes separately can undercount under concurrency, so use an atomic increment in a store such as Redis. Avoid using a raw [PAN](#pan) as a key, since that places the counter store in [PCI DSS](#pci-dss) scope. Use the provider's card fingerprint or a token.

_Usage:_

"The whole university campus is getting blocked at checkout."

"Our IP velocity rule is too tight. Key it on device plus distinct cards instead."

### Risk scoring

Risk scoring assigns a transaction, account or event a value that estimates how likely it is to be fraudulent. A system then uses the score to choose an action. Scores may come from rules, machine-learning models or both, and several parties can compute them independently.

| Party                                 | What it scores from                                 |
| ------------------------------------- | --------------------------------------------------- |
| [Merchant](#merchant)             | Account history, device, basket, delivery details   |
| [Payment service provider](#payment-service-provider) | Patterns across its merchants |
| [Card network](#card-network)   | Activity across its members          |
| [Issuer](#issuer)                 | [Cardholder](#cardholder)'s spending and account behaviour         |

The score is an input to a decision, and the action is set by thresholds.

| Score band | Typical action                                       |
| ---------- | ---------------------------------------------------- |
| Low        | Approve, possibly request an [SCA exemption](#sca-exemption) |
| Medium     | Add [3-D Secure](#3-d-secure)                  |
| High       | Send to manual review                                |
| Very high  | Block                                                |

Scales are vendor-specific, so a score of 80 from one provider is not comparable with 80 from another.

The cost of false positives is easy to miss. A blocked legitimate customer rarely complains and may leave, so a dashboard can show falling fraud while revenue drops. Measure false declines by sampling blocked orders or holding back a small control group, where that is lawful and acceptable.

Training data has a built-in delay. Fraud labels often arrive weeks later through [chargebacks](#chargeback), and [friendly fraud](#friendly-fraud) can label genuine customers as criminals. Blocked orders also have no outcome, so a model learns only from what it allowed. Monitor for drift, and keep the score, model version and input features for each decision so it can be explained later.

Regulation can make risk analysis mandatory for some uses. Under EU Delegated Regulation 2018/389, a provider using the transaction risk analysis exemption must perform real-time analysis covering factors such as abnormal spending, unusual device information, known fraud scenarios and abnormal payer location.

_Usage:_

"Fraud is down since we tightened the model, but so are sales."

"The threshold's too aggressive. Send the middle band to 3DS rather than blocking it."

### Chargeback

A chargeback is a forced reversal of a card payment, initiated by the [issuer](#issuer) through the [card network](#card-network), usually after a [cardholder](#cardholder) disputes a charge. The money is taken back from the [acquirer](#acquirer), which recovers it from the [merchant](#merchant). Visa's rules call this a Dispute, defined as a transaction an issuer returns to an acquirer, and Mastercard's call it a chargeback.

A chargeback differs from a [refund](#refund). A merchant chooses to issue a refund. A chargeback happens regardless of what the merchant wants, generally adds a fee, and counts toward the merchant's [chargeback ratio](#chargeback-ratio).

| Stage                  | Visa term       | Mastercard term        | Who acts                 |
| ---------------------- | --------------- | ---------------------- | ------------------------ |
| Claim                  | Dispute         | First chargeback       | Issuer                   |
| Merchant's challenge   | Dispute Response, or [pre-Arbitration](#pre-arbitration) | Second presentment | Acquirer, for merchant |
| Further challenge      | Pre-Arbitration, or its response | Pre-arbitration (optional) | Depends on the flow |
| Final decision         | Arbitration     | Arbitration            | The network decides      |

Visa's flow depends on the category. For fraud and authorization disputes, the acquirer's first challenge is a pre-Arbitration. For processing errors and consumer disputes, it is a Dispute Response. The general term for the merchant's challenge is [representment](#representment).

Each case has a [dispute reason code](#dispute-reason-code) that determines what evidence can win it. Time limits are strict and differ by network, reason and region, so use the dates your provider gives you and do not hard-code them.

Merchants usually discover a chargeback when a [payout](#payout) arrives short, with the disputed amount and a fee deducted. The merchant can lose both the product and the money even when the sale was genuine, as with [friendly fraud](#friendly-fraud).

Do not issue a refund after a chargeback has already been raised, because the customer may be paid twice. Handle disputes as a separate state in your [ledger](#ledger), because funds can leave and return weeks apart.

_Usage:_

"This payout is 240 short and I can't see why."

"There's a chargeback on an order from May. The issuer pulled the funds, so check the response deadline."

### Retrieval request

A retrieval request is a request from an [issuer](#issuer), sent through the [acquirer](#acquirer), for a copy of the records behind a card transaction. It is usually triggered when a [cardholder](#cardholder) does not recognise a charge and the issuer wants more information. The request does not take money back from the [merchant](#merchant).

| Step | Who      | What happens                                                |
| ---- | -------- | ----------------------------------------------------------- |
| 1    | Cardholder | Queries a charge with the issuer                          |
| 2    | Issuer   | Requests transaction information                            |
| 3    | Acquirer or provider | Passes the request to the merchant              |
| 4    | Merchant | Supplies a receipt, order details or other records          |
| 5    | Issuer   | Resolves the query, or may proceed to a [chargeback](#chargeback) |

A retrieval request leaves funds in place, while a chargeback pulls them from the merchant.

Availability differs by network, and this is where older guides are often wrong. Visa announced in August 2020 that it would sunset its retrieval request process after 16 October 2020, when signature capture became optional. Mastercard's Mastercom dispute system continues to document retrieval request and fulfilment functions for its members. Because many merchants reach these systems through a [payment service provider](#payment-service-provider), whether you ever see one depends on the provider and network.

Where the process exists, a merchant may see a dashboard notice with a short response time. Ignoring it can remove the chance to resolve an innocent misunderstanding, and the issuer may go on to raise a dispute. Answer with clear records: the order date, amount, customer details, delivery confirmation and the exact [statement descriptor](#statement-descriptor).

Do not include a full [PAN](#pan) or [CVV](#cvv) in the documents you upload. Mask card numbers and follow [PCI DSS](#pci-dss) when storing or transmitting receipts.

Repeated requests from customers who do not recognise a charge usually point to a descriptor problem.

_Usage:_

"The provider sent a retrieval request on a Mastercard sale. Is that a chargeback?"

"Not yet. No money has moved. Send the receipt and delivery proof so it doesn't become one."

### Representment

Representment is the process of contesting a [chargeback](#chargeback) by resubmitting the transaction with evidence that the charge was valid. The [merchant](#merchant) prepares the case, and the [acquirer](#acquirer) presents it to the [issuer](#issuer) through the [card network](#card-network). The word is industry shorthand, and each network uses its own terms.

| Network    | Dispute type                              | Merchant's first challenge is called |
| ---------- | ----------------------------------------- | ------------------------------------ |
| Visa       | Fraud and authorization (categories 10, 11) | [Pre-Arbitration](#pre-arbitration) |
| Visa       | Processing errors and consumer (12, 13)   | Dispute Response                     |
| Mastercard | Chargebacks generally                     | Second presentment                   |

The evidence must answer the specific [dispute reason code](#dispute-reason-code). A merchant facing a fraud claim submits a delivery receipt, but delivery alone does not show who placed the order. A merchant facing "not as described" sends proof of payment, which does not address the quality complaint.

| Claim                          | Useful evidence                                                |
| ------------------------------ | -------------------------------------------------------------- |
| Fraud, card-not-present        | [3-D Secure](#3-d-secure) result, Visa Compelling Evidence if eligible |
| Goods not received             | Carrier tracking to the [cardholder](#cardholder)'s address                   |
| Not as described               | Product description, correspondence, return policy             |
| Credit not processed           | [Refund](#refund) details and [acquirer reference number](#acquirer-reference-number) |
| Cancelled recurring            | Terms shown, consent, cancellation records                     |
| Authorization-related          | Valid approval and timely [capture](#capture)              |

Some disputes cannot be won with evidence of delivery. Visa's merchant guidance says that for authorization disputes, proof that the customer received the goods generally does not override a missing, expired or incorrectly used authorization.

Representment takes staff time and can add fees if it escalates, so accept disputes the merchant would lose. Winning returns the funds, though the original dispute may still count toward the [chargeback ratio](#chargeback-ratio) depending on the network's method.

Deadlines are strict and set by network rules. A late response usually loses automatically, so route dispute notifications to a monitored queue, and rely on the due date your provider supplies.

_Usage:_

"We sent the tracking number, and we still lost the fraud dispute."

"Tracking shows delivery, not who bought it. For representment we needed the 3DS result or device history."

### Pre-arbitration

Pre-arbitration is the stage of a card dispute that follows an initial challenge, giving the [issuer](#issuer) and [acquirer](#acquirer) a final chance to resolve the case before the [card network](#card-network) is asked to decide it. Who acts at this stage depends on the network and the type of dispute.

Visa's rules use two flows.

| Stage                    | Fraud and authorization (categories 10, 11) | Processing and consumer (12, 13) |
| ------------------------ | ------------------------------------------- | -------------------------------- |
| [Chargeback](#chargeback) | Issuer raises a Dispute                | Issuer raises a Dispute          |
| Dispute Response         | Not a stage in this flow                    | Acquirer responds                |
| Pre-Arbitration          | Acquirer challenges                         | Issuer challenges                |
| Pre-Arbitration Response | Issuer accepts or rejects                   | Acquirer accepts or rejects      |
| Arbitration              | Acquirer may file                           | Issuer may file                  |

So in a Visa fraud dispute, pre-arbitration is the [merchant's](#merchant) first challenge. In a consumer dispute, it is the issuer's reply to the merchant's evidence.

Mastercard works differently. After a chargeback and second presentment, the issuer may file an optional pre-arbitration case, and its Chargeback Guide says Mastercard strongly recommends skipping that step and going directly to an arbitration case.

In pre-arbitration, the two sides can still settle. In arbitration, the network reviews the case and issues a decision, and the losing side generally bears additional fees. Those fees can exceed the value of a small transaction.

For a merchant, this stage usually appears as a notice from the provider that a dispute it thought was finished has come back. Check whether new evidence addresses the objection, compare the transaction amount with the possible fees, and accept liability if the case is weak.

Time limits at this stage are short and differ by flow, so take them from your [payment service provider](#payment-service-provider). Model each stage as a separate state, because a [representment](#representment) win can be reopened.

_Usage:_

"We won that dispute last month. Why is it back?"

"The issuer went to pre-arbitration. It's a 30-euro order, so accept it unless we have new evidence."

### Dispute reason code

A dispute reason code is the value a [card network](#card-network) attaches to a [chargeback](#chargeback) to state why the payment is being disputed. It tells the [merchant](#merchant) which rules apply and what evidence can answer the claim. Code sets are network-specific, so the same complaint can carry different labels.

Visa organises its codes as dispute conditions within four categories. Mastercard uses message reason codes.

| Type of claim   | Visa                                                  | Mastercard example                     |
| --------------- | ----------------------------------------------------- | -------------------------------------- |
| Fraud           | Category 10, such as 10.4 Other Fraud, Card-Absent    | 4837 No Cardholder Authorization       |
| Chip liability  | 10.1 and 10.2, [EMV](#emv) [liability shift](#liability-shift)                 | 4870 Chip Liability Shift              |
| Authorization   | Category 11, such as 11.3 No Authorization/Late Presentment | 4808 Authorization-related       |
| Processing error | Category 12, such as 12.6 Duplicate Processing       | 4834 Point-of-Interaction Error        |
| Consumer        | Category 13, such as 13.1 Not Received                | 4853 Cardholder Dispute                |

Examples are from Visa's October 2026 rules and Mastercard's May 2025 guide, and can change.

A reason code is different from a [decline code](#decline-code). A decline code explains why an authorization was refused at the time of payment. A reason code explains why a completed payment is being challenged afterward.

The code decides the strategy for [representment](#representment). A 13.1 "not received" claim can often be answered with carrier tracking. The same tracking does little against a 10.4 fraud claim, where the question is who made the purchase.

A customer who forgot a subscription may still be recorded under a fraud code, a common sign of [friendly fraud](#friendly-fraud).

[Payment service providers](#payment-service-provider) often map raw codes to simplified categories such as "fraudulent" or "product not received". Store the raw code and network too. Reporting by code also shows where to fix the source: rising 13.1 points to fulfilment, and rising 12.6 points to a [double charge](#double-charge) bug.

_Usage:_

"Should I send the delivery proof for this dispute?"

"Check the reason code first. It's a 10.4, so we need evidence of who bought it, not just where it went."

### Chargeback ratio

A chargeback ratio measures a [merchant's](#merchant) disputes relative to its transactions. [Card networks](#card-network) and [acquirers](#acquirer) use it to identify businesses with unusually high fraud or customer problems. There is no universal formula, so a dashboard percentage may not match a network's figure.

| Network    | Program                              | Measure                                                              |
| ---------- | ------------------------------------ | -------------------------------------------------------------------- |
| Visa       | Visa Acquirer Monitoring Program (VAMP) | Count of fraud reports plus disputes, divided by settled transactions, card-not-present only |
| Mastercard | Excessive Chargeback Program         | Chargebacks in a calendar month, divided by Mastercard transactions in the preceding month |

The differences change the result. Visa's VAMP ratio includes reported fraud, so a transaction can count even when no chargeback follows. It can also exclude some disputes resolved through pre-dispute tools and fraud that qualifies for Compelling Evidence 3.0. Mastercard divides by the previous month's transactions, so a seasonal drop in sales can raise the ratio even if the number of chargebacks stays flat.

Both programs apply thresholds and minimum counts, which differ by region and have changed recently. Visa's published fact sheet, for example, records a lower merchant threshold for several regions from April 2026. Take current figures from the network or your acquirer.

Exceeding a program's level can lead to remediation plans, fees passed on by the acquirer, a [rolling reserve](#rolling-reserve), or closure of the [merchant account](#merchant-account). Because disputes arrive weeks after a sale, the ratio lags the cause.

To manage it, compute each network's metric separately, by merchant ID, and alert on the trend rather than waiting for a notice. Address the sources: unclear [statement descriptors](#statement-descriptor), hard-to-cancel subscriptions, slow delivery, and fraud controls such as [3-D Secure](#3-d-secure). A prompt [refund](#refund) before a dispute avoids a chargeback entirely.

Splitting payments or moving volume between merchant accounts to dilute the ratio can breach network rules.

_Usage:_

"Our dashboard says disputes are under one percent, so we're fine, right?"

"That's blended. Visa counts fraud reports too, so check the VAMP ratio by merchant ID."

## Section 6 — Fees and Currency

### Interchange fee

An interchange fee is a fee the [acquirer](#acquirer), the [merchant](#merchant)'s bank, pays to the [issuer](#issuer), the [cardholder](#cardholder)'s bank, on most card purchases in a [four-party model](#four-party-model). The [card network](#card-network) publishes the rates. They vary by card type, region, merchant category, sales channel and the data sent with the transaction. The merchant does not pay the issuer directly. The acquirer recovers the cost through the merchant's pricing.

Interchange is often confused with the total cost of accepting a card. It is one component. A [scheme fee](#scheme-fee) goes to the network, the acquirer adds its own margin, and the [merchant discount rate](#merchant-discount-rate) expresses the combined charge.

Regulators cap interchange in some markets, and the rules differ:

| Region    | Rule                                                               | Current point to check                                                     |
| --------- | ------------------------------------------------------------------ | -------------------------------------------------------------------------- |
| EU        | Regulation (EU) 2015/751 caps most consumer debit and credit cards | Commercial cards and three-party schemes generally fall outside the caps   |
| UK        | Onshored version of the EU caps                                    | The Payment Systems Regulator is working on a UK-EEA cross-border cap      |
| US        | Regulation II caps debit interchange for large issuers             | An October 2026 Eighth Circuit ruling upheld vacating the cap, effective only once the court's mandate issues |
| Australia | Reserve Bank of Australia standards                                | Lower domestic caps began on 1 October 2026                                |

A merchant usually notices interchange when monthly card costs rise while prices and sales stay flat. A larger share of premium, commercial or foreign cards can cause this. Missing transaction data can also push a payment into a more expensive category, which acquirers call a downgrade. Whether interchange comes back on a [refund](#refund) depends on the network and the acquirer contract, so check it instead of assuming.

_Usage:_

"Card costs went up this month, but revenue is flat."

"More volume came from commercial and foreign cards, and interchange is higher on both. Pull the fee report by card type."

### Scheme fee

A scheme fee is a charge that a [card network](#card-network) such as Visa or Mastercard applies for use of its network. [Acquirers](#acquirer) and [issuers](#issuer) both pay scheme fees, and in the US they are often called assessments or network fees. An acquirer normally passes its share on to the [merchant](#merchant), either as itemised lines or inside a single rate.

Scheme fees differ from an [interchange fee](#interchange-fee) in who receives the money. Interchange moves from the acquirer to the issuer. A scheme fee goes to the network. Interchange is capped in some jurisdictions, while scheme fees are set by each network and are generally not covered by those same caps.

A single payment can trigger several scheme fees:

| Fee type            | Triggered by                                                  |
| ------------------- | ------------------------------------------------------------- |
| Volume assessment   | The value of transactions processed                           |
| Authorization fee   | Each authorization request, including declined ones in some programmes |
| [Clearing](#clearing) fee        | Each transaction submitted for clearing                       |
| [Cross-border fee](#cross-border-fee)    | The issuer and merchant being in different countries or regions |
| Compliance or misuse fee | Breaching a network rule, which can include repeated reattempts |

The names, amounts and triggers change, and each network publishes updates to its acquirers rather than a single public price list. For that reason, a merchant's statement can gain an unfamiliar line with no change to its contract.

The usual symptom is a set of small, oddly named charges that finance cannot explain. A retry loop can make this worse, because each repeated [authorization](#card-authorization) attempt may incur a fee even when the issuer declines it. To investigate, ask the acquirer for a per-transaction fee report, group charges by fee code, and compare the count of authorization attempts with the count of successful orders. A large gap often points to retries or [card testing](#card-testing).

_Usage:_

"What is this new network access line on the acquirer statement?"

"It's a scheme fee charged per authorization. Our retry job doubled the attempts last month, so the line doubled too."

### Merchant discount rate

The [merchant](#merchant) discount rate, or MDR, is the total percentage an [acquirer](#acquirer) or [payment service provider](#payment-service-provider) deducts from a merchant's card sales. It normally covers the [interchange fee](#interchange-fee), the [scheme fee](#scheme-fee) and the acquirer's margin. Some contracts add a fixed amount per transaction, so the quoted percentage may not be the full cost.

The MDR is often mistaken for interchange. Interchange is one input, paid to the [issuer](#issuer). The MDR is what the merchant sees deducted. Under [blended pricing](#blended-pricing) the MDR is one published rate. Under [interchange-plus pricing](#interchange-plus-pricing) there is no single rate in advance, but an effective MDR can be calculated after the fact.

This worked example uses invented figures to show how a sale of 100.00 divides:

| Component          | Receiver | Amount |
| ------------------ | -------- | -----: |
| Interchange        | Issuer   |   1.20 |
| Scheme fee         | Network  |   0.15 |
| Acquirer margin    | Acquirer |   0.65 |
| **Total deducted** |          |   2.00 |
| **Net to merchant** |         |  98.00 |

The effective rate is total fees divided by processed volume. Calculate it over a full statement, including fixed fees, monthly charges and [chargeback](#chargeback) fees. A fixed per-transaction fee matters more on small orders: the same fixed amount is a much larger share of a 3.00 sale than of a 300.00 sale.

The failure finance teams see is a [payout](#payout) lower than recorded sales, with the difference booked as an unexplained variance. Record gross, fees and net separately for each transaction so that [payment reconciliation](#payment-reconciliation) can explain the gap. When comparing provider quotes, compare effective rates on your own card mix, because a lower headline rate can cost more if other fees apply.

_Usage:_

"The provider quoted us 1.9%, but we're paying nearer 2.6%."

"That quote left out the per-transaction fee. On our small baskets, the effective merchant discount rate is much higher."

### Interchange-plus pricing

Interchange-plus pricing is a card pricing model in which the [acquirer](#acquirer) charges the [merchant](#merchant) the actual [interchange fee](#interchange-fee) for each transaction plus a fixed, disclosed markup. A common variant, interchange-plus-plus or IC++, itemises the [scheme fee](#scheme-fee) as well. Providers use these labels inconsistently, so check the contract to see whether scheme fees are passed through or included in the markup.

The alternative is [blended pricing](#blended-pricing), where the merchant pays one rate and the provider absorbs the variation. With interchange-plus, the merchant carries that variation and can see what each card cost.

This example uses invented figures for two sales of 100.00 with a markup of 0.30:

| Line             | Domestic debit | Foreign commercial credit |
| ---------------- | -------------: | ------------------------: |
| Interchange      |           0.20 |                      1.80 |
| Scheme fees      |           0.05 |                      0.40 |
| Acquirer markup  |           0.30 |                      0.30 |
| **Total cost**   |       **0.55** |                  **2.50** |
| **Net received** |      **99.45** |                 **97.50** |

The markup is the same in both columns, and the total differs because of the underlying card. This transparency makes it easier to compare acquirers, since the markup is the part they control.

The drawback is unpredictability. A merchant's monthly cost can rise with no change in contract because customers used more premium or foreign cards. Statements are also longer, and fees may be reported a day or more after the sale, or billed monthly rather than netted from each [payout](#payout). Engineering teams feel this during [payment reconciliation](#payment-reconciliation), because the final fee is unknown when the order is recorded. Store an estimated fee if needed, then post an adjusting [ledger](#ledger) entry when the actual fee arrives, keeping both visible.

_Usage:_

"Why did our fees move when the acquirer's rate didn't change?"

"We're on interchange-plus pricing. Our markup stayed fixed, but more customers paid with foreign commercial cards."

### Blended pricing

Blended pricing is a card pricing model in which a [merchant](#merchant) pays one published rate, or a small set of rates, regardless of the underlying card. A provider might quote one percentage plus a fixed fee for every online card payment. The provider pays the actual [interchange fee](#interchange-fee) and [scheme fee](#scheme-fee) from that amount and keeps the difference.

The provider's margin therefore changes from one transaction to the next. It earns more on a low-cost domestic debit card and less, or even loses money, on an expensive foreign commercial card. Providers set the rate using an expected card mix, and may reprice or add surcharges for categories such as international cards.

| Model              | Merchant pays                     | Predictability | Cost visibility |
| ------------------ | --------------------------------- | -------------- | --------------- |
| Blended            | One rate                          | High           | Low             |
| Tiered             | A rate per provider-defined bucket | Medium        | Low             |
| [Interchange-plus pricing](#interchange-plus-pricing) | Actual cost plus a markup   | Lower          | High            |

Tiered pricing, sometimes described as qualified, mid-qualified and non-qualified rates, is a related model. The provider decides which transactions fall into each tier, so the rate paid can be hard to predict or audit.

Blended pricing suits merchants that value a simple bill and have modest volume. The usual problem appears as a business grows. A merchant whose customers mostly use domestic debit cards may pay well above the underlying cost, and nothing on the statement reveals it because the components are hidden. To check, ask for a sample of transaction-level costs or request an interchange-plus quote, then compare both against the last few months of your real card mix. Include fixed fees, since they can outweigh a small percentage difference on low-value orders.

_Usage:_

"Our provider charges one flat rate. Is that good for us?"

"It's blended pricing, and most of our volume is domestic debit. We're probably overpaying, so let's get an interchange-plus quote."

### Surcharging

Surcharging is when a [merchant](#merchant) adds a fee to the price because the customer chose a particular payment method, usually a credit card. Whether a merchant may do it depends on the jurisdiction, the [card network](#card-network)'s rules, the card type and sometimes the sector. There is no universal rule.

| Jurisdiction | Position at the time of writing                                                                                     |
| ------------ | ------------------------------------------------------------------------------------------------------------------- |
| EU           | [PSD2](#psd2) bars surcharges on consumer cards under the interchange caps and on SEPA transfers and debits. Other instruments vary by member state |
| UK           | The Consumer Rights (Payment Surcharges) Regulations 2012 ban surcharges on consumer cards and some other methods. Commercial cards may be surcharged up to cost |
| US           | State laws and network rules apply, and network rules generally exclude debit and [prepaid cards](#prepaid-card)                     |
| Australia    | From 1 October 2026, Reserve Bank of Australia changes ended surcharging on designated eftpos, Mastercard and Visa cards |

Surcharging is often confused with two nearby practices. A convenience fee is charged for using a particular channel and has its own network rules. A cash discount lowers the price for non-card payment instead of raising it for card payment. Relabelling a surcharge does not necessarily change how it is classified.

A merchant may apply a blanket checkout fee and then receive a network compliance notice, a regulator complaint or a [chargeback](#chargeback) for the added amount. An engineering team detects card type from the [BIN](#bin) and applies a credit surcharge to a debit card, because the lookup data was stale.

Before launching, confirm the current rules for every country and network you sell in, and ask your [acquirer](#acquirer) or a lawyer. Keep the fee as its own line item, so it can be refunded and reported correctly.

_Usage:_

"Can we add a 2% card fee to all checkouts?"

"Not across all markets. The EU and UK ban it on consumer cards, and US rules vary by state and network. Ask legal first."

### Rolling reserve

A rolling reserve is an arrangement in which a [payment service provider](#payment-service-provider) withholds a percentage of each [settlement](#settlement) and releases it after a fixed period. It protects the provider against losses that arrive after a sale, mainly a [chargeback](#chargeback) or [refund](#refund) the [merchant](#merchant) can no longer fund. If the merchant fails, the [acquirer](#acquirer) can still be liable to the [card network](#card-network), so it holds this money as cover.

The contract sets the percentage and the holding period. Providers commonly apply a reserve to higher-risk categories, new businesses, merchants with long delivery times, or accounts with rising disputes. Other forms exist: a fixed reserve holds one lump sum, and delayed [payout](#payout) lengthens the time before any funds are paid.

This example uses invented figures and a 10% reserve, with amounts in [minor units](#minor-unit):

| Event                   | Available | Reserve | Total |
| ----------------------- | --------: | ------: | ----: |
| Sale of 100000 settles  |     90000 |   10000 | 100000 |
| Chargeback of 5000      |     85000 |   10000 |  95000 |
| Reserve period ends     |     95000 |       0 |  95000 |

A reserve is not a fee. The money still belongs to the merchant, subject to the contract, and is normally recorded as a receivable. Booking the withheld amount as an expense overstates costs and hides money the business expects to receive.

Merchants usually discover a reserve when a payout is lower than expected, or when cash runs short during fast growth because a growing portion of revenue is held at any one time. Model a separate reserve balance in the [ledger](#ledger), using the release date from the settlement data, and forecast cash on that basis. To negotiate a lower reserve, show the provider a clean dispute history and shorter delivery times.

_Usage:_

"Payouts are 10% lower than sales since we moved to the new provider."

"They put us on a rolling reserve. It's released after the holding period, so book it as a receivable, not a fee."

### Cross-border fee

A cross-border fee is a charge applied when a card payment crosses a country or region boundary, usually because the [issuer](#issuer) and the [merchant](#merchant)'s [acquirer](#acquirer) are in different places. The [card network](#card-network) defines what counts as cross-border, and those definitions can treat a region such as the European Economic Area differently from a single country.

The term covers several charges that people often merge:

| Charge                    | Who pays                 | Who sets it          | Trigger                                 |
| ------------------------- | ------------------------ | -------------------- | --------------------------------------- |
| Network cross-border fee  | Acquirer and issuer      | Card network         | Issuer and acquirer in different regions |
| Cross-border interchange  | Acquirer, paid to issuer | Network or regulator | Inter-regional transaction              |
| Foreign transaction fee   | [Cardholder](#cardholder)               | Issuer               | Foreign purchase, under the card terms  |
| Currency conversion margin | Payer or merchant       | Whoever converts     | Currencies differ                       |

A cross-border fee does not require a currency conversion. A US cardholder paying a merchant in US dollars can still be charged a foreign transaction fee if the merchant's acquirer is abroad. The customer then complains about a fee on a payment that appeared to be domestic, and the merchant's support team cannot see the charge because the issuer applied it.

Merchants see the cost as a higher fee on foreign cards. Interchange can rise sharply when a payment becomes inter-regional. Payments between the UK and EEA are a current example: the UK's Payment Systems Regulator has been working on a cap for fees on EEA-issued cards used online at UK businesses.

Businesses with significant foreign volume can reduce the cost by acquiring locally, using a domestic acquirer in each main market. That requires a local legal entity or an eligible provider setup in many countries, so check the requirements. [Payment routing](#payment-routing) can then send each card to the local acquirer.

_Usage:_

"A US customer was charged a foreign fee, but we billed in dollars."

"Our acquirer is in Ireland, so the issuer treated it as cross-border. Currency wasn't the trigger."

### Dynamic currency conversion

Dynamic currency conversion, or DCC, is a service that offers a [cardholder](#cardholder) the choice to pay in their card's home currency at a terminal, ATM or online checkout. The [merchant](#merchant)'s provider performs the conversion and sets the rate, usually including a markup. If the customer declines, the payment proceeds in the local currency and the [card network](#card-network) or [issuer](#issuer) handles the conversion.

The choice is commonly shown as a prompt such as "Pay 54.20 USD or 50.00 EUR". Choosing the home currency gives certainty about the amount, but the rate can be less favourable than the one the card would otherwise receive.

| Option                 | Who converts          | Who sets the price shown        |
| ---------------------- | --------------------- | ------------------------------- |
| Pay in local currency  | Network or issuer     | Merchant, in local currency     |
| DCC                    | Merchant's provider   | Provider, at the point of sale  |
| [Multi-currency pricing](#multi-currency-pricing) | Usually the [acquirer](#acquirer)  | Merchant, in the buyer's currency |

DCC is often confused with multi-currency pricing. With multi-currency pricing the merchant sets a price in the buyer's currency in advance. With DCC the item is priced in local currency and converted at the moment of payment.

Card network rules require the cardholder to make an active choice. In the EU, Regulation (EU) 2021/1230 requires parties offering conversion at an ATM or point of sale to disclose the charges before payment as a percentage markup over the latest European Central Bank reference rate.

The typical failure is a traveller who sees a higher amount than expected on their statement and says they never agreed to the conversion. A terminal that preselects home currency, or staff who choose for the customer, can lead to complaints and [chargebacks](#chargeback). Keep evidence of the customer's choice, the rate and the markup on the receipt.

_Usage:_

"A customer disputes the amount, saying we charged them in pounds without asking."

"The terminal had dynamic currency conversion on by default. Turn off preselection and check the receipt shows the markup."

### Multi-currency pricing

Multi-currency pricing is a setup in which a [merchant](#merchant) displays and charges prices in the buyer's currency, then receives [settlement](#settlement) in that currency or a different one. The currency shown to the customer is the presentment currency. The currency paid out to the merchant is the settlement currency. When they differ, the [acquirer](#acquirer) or [payment service provider](#payment-service-provider) usually performs the conversion and charges a margin.

The merchant controls the customer-facing price, using a price list per currency or a base price with a chosen rate and rounding rule. This differs from [dynamic currency conversion](#dynamic-currency-conversion), where the item is priced in local currency and converted at the moment of payment, with the provider setting the rate.

A multi-currency payment needs more fields than a single amount:

| Field               | Example | Why it is stored                     |
| ------------------- | ------- | ------------------------------------ |
| Presentment amount  | 5000 JPY | What the customer agreed to pay     |
| Settlement amount   | 3120 USD [minor units](#minor-unit) | What the merchant received |
| Exchange rate       | As reported by the provider | Audit and reconciliation |
| Conversion fee      | 62 USD minor units | Margin cost              |

Each amount is stored in the minor unit of its own currency. In this example, 5000 JPY means 5,000 yen because the yen has no decimal places, while 3120 USD means 31.20 dollars.

The common failure happens on a [refund](#refund). A customer paid 100.00 EUR, the merchant settled in USD, and the rate moved before the refund. The customer gets 100.00 EUR back, but the USD debited from the merchant differs from what it originally received. Finance sees a small unexplained gain or loss. Record the rate for each leg and post the difference to a foreign exchange gain or loss account in the [ledger](#ledger).

_Usage:_

"Our refund cost more in dollars than the original sale brought in."

"That's the exchange rate moving under multi-currency pricing. Record it as an FX loss rather than adjusting the original payment."

### Minor unit

A minor unit is the smallest denomination of a currency, as defined by the ISO 4217 currency standard. One US dollar is 100 cents, so USD has an exponent of 2. Payment systems commonly store and transmit money as an integer count of minor units, because binary floating-point numbers cannot represent many decimal values exactly and accumulate rounding errors.

```json
{ "amount": 1050, "currency": "USD" }
```

That value means 10.50 dollars. The same integer means something else in another currency, so an amount must always be stored with its currency code.

| Currency | ISO 4217 exponent | 1050 means  |
| -------- | ----------------: | ----------- |
| USD      |                 2 | 10.50       |
| EUR      |                 2 | 10.50       |
| JPY      |                 0 | 1,050       |
| KRW      |                 0 | 1,050       |
| KWD      |                 3 | 1.050       |
| BHD      |                 3 | 1.050       |
| CLF      |                 4 | 0.1050      |

A common bug is multiplying every price by 100. A 1,000 yen order is sent as 100000 and the customer is charged 100,000 yen. Dividing by 100 for display makes the reverse error, and a Kuwaiti dinar amount is off by a factor of ten.

Read the exponent from a maintained ISO 4217 table instead of hardcoding it. SIX, the standard's maintenance agency, publishes the current list, and exponents can change when a currency is reformed. Providers sometimes diverge from ISO for particular currencies, such as requiring a two-decimal format for a zero-decimal currency or restricting fractional amounts, so check each provider's documentation and convert at that boundary.

Some message formats use decimal strings instead. [ISO 20022](#iso-20022), for example, carries amounts such as `10.50` with a currency attribute. Convert these to integers at the system edge using exact decimal parsing, and define a rounding rule for tax, fee and foreign exchange calculations.

_Usage:_

"A Japanese customer was charged 100 times the price."

"We multiplied by 100 for every currency. JPY has no minor unit, so read the exponent from the ISO 4217 table."

## Section 7 — Bank Rails

### ACH

ACH, the Automated Clearing House network, is the US system for moving batched electronic credits and debits between bank accounts. Nacha writes the operating rules. Two operators process the entries: the Federal Reserve's FedACH and The Clearing House's Electronic Payments Network. Payroll and bill payments commonly use it.

| Step | Who                              | What happens                                      |
| ---- | -------------------------------- | ------------------------------------------------- |
| 1    | Originator (business)            | Gets authorization and creates an entry           |
| 2    | ODFI (originating bank)          | Submits batched entries to an operator            |
| 3    | ACH operator                     | Sorts entries and delivers them to receiving banks |
| 4    | RDFI (receiving bank)            | Posts the credit or debit to the receiver's account |
| 5    | RDFI                             | Sends a return if the entry cannot be honoured    |

An ACH credit pushes money to a receiver. An ACH debit pulls money from a payer under an authorization, which is why debits carry more risk for the business collecting them. Same Day ACH offers faster processing within windows and per-payment limits set by Nacha, but it remains batched. It is not the same as an instant rail such as [FedNow](#fednow) or the [RTP network](#rtp-network).

ACH is often confused with a wire. A [Fedwire](#fedwire) payment settles individually and is final. An ACH debit can settle and still come back later as a [payment return](#payment-return), for reasons such as insufficient funds or a claim that it was unauthorised.

The failure this causes is familiar to anyone shipping goods on ACH. The dashboard shows "paid", the order ships, and days later a return such as `R01` reverses the money. Treat a debit as provisional until your risk window has passed, and record the return as a new [ledger](#ledger) entry. Nacha also added fraud-monitoring duties that took effect in phases during 2026, so confirm current obligations with your bank.

_Usage:_

"The customer's payment cleared Monday, so why did we lose the money today?"

"It was an ACH debit and came back `R01`. Settled doesn't mean final, so hold high-value orders longer."

### SEPA Credit Transfer

A SEPA Credit Transfer, or SCT, is a euro payment that a payer instructs their bank to push to a payee's account within the Single Euro Payments Area. The European Payments Council publishes the rulebook for participating [payment service providers](#payment-service-provider) (PSPs). SEPA is wider than the EU and includes non-EU countries such as Norway, Switzerland and the United Kingdom.

| Step | Who         | What happens                                         |
| ---- | ----------- | ---------------------------------------------------- |
| 1    | Payer       | Enters the payee's [IBAN](#iban), name, amount and reference  |
| 2    | Payer's PSP | Validates and debits the account                     |
| 3    | Clearing system | Exchanges the [ISO 20022](#iso-20022) message and settles between PSPs |
| 4    | Payee's PSP | Credits the payee                                    |

EU payment services law generally requires a euro transfer to reach the payee's provider by the end of the next business day. A standard SCT is therefore not instant. [SEPA Instant](#sepa-instant) is a separate scheme that runs continuously, while [SEPA Direct Debit](#sepa-direct-debit) is a pull payment started by the creditor.

Since 9 October 2025, the Instant Payments Regulation has required euro-area banks to offer verification of payee on euro credit transfers. The check compares the payee name with the IBAN before the payer confirms. Providers in non-euro EU member states have a later date of 9 July 2027, and payment and e-money institutions follow their own timetable.

Two failures are common for businesses collecting by transfer. A customer omits or mistypes the reference, so the money arrives but nothing links it to an invoice, and it waits in a suspense account. Or a payer sends funds to the wrong IBAN and asks for them back. The payer's bank can send a recall, which the receiving side may refuse. Issue a unique reference per invoice and match on it automatically.

_Usage:_

"The customer sent proof of transfer, but the invoice is still unpaid."

"The SEPA Credit Transfer arrived without a reference. Match it from the suspense account and make the reference field clearer on the invoice."

### SEPA Instant

SEPA Instant, formally the SEPA Instant Credit Transfer or SCT Inst, is a euro credit transfer scheme that runs 24 hours a day on every day of the year. The European Payments Council publishes the rulebook. Regulation (EU) 2024/886, the Instant Payments Regulation, requires funds to reach the payee within 10 seconds of the order being received, and it requires EU providers that offer euro credit transfers to support instant ones.

The regulation phases in by location and firm type, according to the European Central Bank's published timetable:

| Obligation           | Euro area        | Non-euro EU     |
| -------------------- | ---------------- | --------------- |
| Receive instant      | 9 January 2025   | 9 January 2027  |
| Send instant         | 9 October 2025   | 9 July 2027     |
| Verification of payee | 9 October 2025  | 9 July 2027     |

Payment and e-money institutions have separate dates, starting 9 April 2027. Instant transfers may not cost more than the same provider's comparable standard transfers. Providers must also check their customers against EU targeted financial sanctions at least daily, in place of screening each instant transfer against those EU measures.

SEPA Instant differs from a [SEPA Credit Transfer](#sepa-credit-transfer) in speed and availability, but both are credit pushes that the payer starts. Completed transfers cannot be reversed by the payer, so a misdirected payment relies on a recall the receiver can refuse.

For engineers, the short deadline changes failure handling. A client timeout does not prove that a transfer failed, because the provider may have completed it just as the connection dropped. Treat it as an [unknown payment outcome](#unknown-payment-outcome) and query the status using your end-to-end reference before sending again. Also, release goods only on a confirmed credit, not on the customer's "sent" screen. Speed also helps fraudsters, since stolen money can be moved onward within seconds.

_Usage:_

"The transfer API timed out. Should I resend the SEPA Instant payment?"

"Not yet. Query the status with the end-to-end ID, since it may already have landed."

### SEPA Direct Debit

SEPA Direct Debit, or SDD, is a European Payments Council scheme that lets a creditor collect euro payments from a debtor's account under a [direct debit mandate](#direct-debit-mandate). There are two schemes. SDD Core is available to consumers and businesses. SDD B2B is for business debtors only and needs the debtor bank to confirm the mandate.

| Step | Who           | What happens                                              |
| ---- | ------------- | --------------------------------------------------------- |
| 1    | Creditor      | Obtains the mandate with its creditor identifier and a unique reference |
| 2    | Creditor      | Gives the debtor advance notice of the amount and date    |
| 3    | Creditor's PSP | Submits the collection                                   |
| 4    | Debtor's PSP  | Debits the account, or rejects or returns the collection  |
| 5    | Debtor        | May request a refund under the scheme rules               |

The refund right is where SDD differs most from a card payment. Under the current SDD Core rulebook, a debtor can get a no-questions-asked refund within eight weeks of the debit, and can claim for an unauthorised collection for up to 13 months. SDD B2B has no equivalent refund right for an authorised collection. These periods come from the rulebook and can change.

An SDD refund is also different from a [chargeback](#chargeback). Card disputes have a [representment](#representment) stage where the [merchant](#merchant) can contest with evidence. In the eight-week window, the creditor cannot block the refund through the scheme and must pursue any valid debt separately.

The symptom is revenue reversing weeks after delivery, with a reason code such as `MD06`, while a failed collection may show `AM04` for insufficient funds. Treat each collection as provisional in your [ledger](#ledger), post reversals as new entries, and keep the mandate available, because the debtor's bank can request a copy for an unauthorised claim.

_Usage:_

"A customer got their money back seven weeks after we delivered."

"That's an SDD Core refund, `MD06`. We can't contest it in the scheme, so finance has to invoice them again."

### SWIFT

SWIFT, the Society for Worldwide Interbank Financial Telecommunication, now styled Swift, is a member-owned cooperative based in Belgium that runs a secure messaging network for financial institutions. It carries payment instructions between banks. It does not hold customer accounts or settle funds. The money moves through accounts that banks hold with each other, known as [correspondent banking](#correspondent-banking), or through a [settlement](#settlement) system such as an [RTGS](#rtgs).

A "Swift code" is a Business Identifier Code, or BIC, defined by ISO 9362. It identifies a bank or branch. It is different from an [IBAN](#iban), which identifies a customer account.

| Layer       | Example                         | Job                               |
| ----------- | ------------------------------- | --------------------------------- |
| Identifier  | BIC                             | Names the institution             |
| Message     | `pacs.008`, formerly MT103      | Describes the payment             |
| Network     | Swift                           | Delivers the message              |
| Funds       | [Nostro account](#nostro-account) or RTGS          | Moves the value                   |

The message format has changed. For cross-border payment instructions between financial institutions, the coexistence period for legacy MT messages and [ISO 20022](#iso-20022) ended on 22 November 2025. Swift had also planned to remove fully unstructured postal addresses in November 2026. In 2026 it agreed to extend that timeline for payment messages after community requests, so check its current roadmap before relying on a date.

The usual confusion appears when a business receives a "Swift copy" as proof of payment. That document shows an instruction was sent. It does not prove the beneficiary was credited. A payment can still be held by an intermediary for compliance review, rejected for bad details, or arrive short because a bank in the chain deducted a fee. To trace one, ask the sending bank for its Unique End-to-end Transaction Reference (UETR), which banks use to track the payment across the chain.

_Usage:_

"The supplier says they never got the money, but we have the Swift confirmation."

"That only proves our bank sent the message. Give them the UETR and ask the bank to trace it."

### Fedwire

Fedwire, formally the Fedwire Funds Service, is a real-time gross [settlement](#settlement) system operated by the Federal Reserve Banks. A participating institution sends a payment order, and the Reserve Banks settle it individually by debiting the sender's Federal Reserve account and crediting the receiver's. Once settled, the payment is final and irrevocable. Businesses know it as a "wire", and it is typically used for large or time-critical payments such as property closings and interbank transfers.

| Rail    | Operator                       | Processing            | Can the money come back automatically? |
| ------- | ------------------------------ | --------------------- | ------------------- |
| Fedwire | Federal Reserve Banks          | Individual, business hours | No, it is final |
| [ACH](#ach)     | FedACH and EPN                 | Batched               | Yes, through returns |
| [FedNow](#fednow)  | Federal Reserve Banks          | Individual, 24x7x365  | No, it is final     |

Fedwire adopted [ISO 20022](#iso-20022) on 14 July 2025, replacing its proprietary format. Its operating day runs on business days, so a payment instructed late may wait until the next one. In October 2025, the Federal Reserve Board announced that the service will expand to 22 hours a day, six days a week, with implementation planned for 2028 or 2029. Check the published schedule for current hours and cut-offs, because banks often set earlier internal deadlines for their customers.

Finality makes wire fraud hard to recover from. In a common scam, a criminal impersonates a supplier by email and sends new bank details. The finance team pays, the funds settle, and the sending bank can only ask the receiving bank to return them. The receiving bank does not have to agree, and the account may already be empty.

Confirm any change of payment details through a known phone number, require a second approver on high-value wires, and report suspected fraud to your bank immediately.

_Usage:_

"Can we pull back the wire we sent to the new supplier account?"

"Fedwire payments are final. Call the bank now and ask for a recall, but the receiving bank has to agree."

### RTGS

Real-time gross [settlement](#settlement), or RTGS, is a type of settlement system in which interbank payments settle one at a time, as soon as they are processed, usually across accounts at a central bank. "Gross" means each payment settles for its full amount and is not netted against others. Settlement in central bank money removes the risk that the paying bank fails before settling.

Major examples are [Fedwire](#fedwire) in the US, T2 in the euro area and the Bank of England's RTGS service, which settles CHAPS payments in the UK.

The main alternative is deferred net settlement, where a system adds up what participants owe each other and settles only the difference at set times:

| Property          | RTGS                                | Deferred net settlement             |
| ----------------- | ----------------------------------- | ----------------------------------- |
| Settlement        | Each payment, in full               | Net positions, in cycles            |
| Liquidity needed  | Higher                              | Lower                               |
| Settlement risk   | Low, because settlement is immediate | Exists between cycles unless covered |
| Example           | Fedwire, T2, CHAPS                  | [Faster Payments](#faster-payments)                     |

RTGS is often confused with instant payments. RTGS describes how banks settle. Instant payments describe what the customer experiences. Faster Payments credits customers quickly but settles between banks on a net basis three times per business day, according to the Bank of England, with participants prefunding their exposure. A traditional RTGS can also close overnight and on weekends, while a customer-facing instant service runs all the time.

Because every payment needs its full value, a bank must hold enough liquidity during the day. If it does not, the system may queue the payment until incoming funds arrive. A treasury team sees this as a high-value payment stuck in "queued" near a cut-off. Banks manage it with intraday credit, payment scheduling and liquidity-saving features in the system.

_Usage:_

"Why is this CHAPS payment still queued?"

"Our settlement account is short on intraday liquidity. RTGS needs the full amount, so treasury has to fund it first."

### FedNow

FedNow is an instant payment service operated by the Federal Reserve Banks, launched in July 2023. It runs 24 hours a day, every day of the year. A participating bank or credit union sends a credit transfer, and the service settles it individually across Federal Reserve master accounts, or through a correspondent acting for the institution. The receiver can have the funds within seconds, and the payment is final.

| Step | Who            | What happens                                 |
| ---- | -------------- | -------------------------------------------- |
| 1    | Payer's bank   | Validates the payment and sends an [ISO 20022](#iso-20022) message |
| 2    | FedNow         | Checks it and forwards it to the receiving bank |
| 3    | Receiver's bank | Accepts or rejects                          |
| 4    | FedNow         | Settles and notifies both banks              |
| 5    | Receiver's bank | Makes the funds available                   |

FedNow is often confused with [Fedwire](#fedwire) because both belong to the Federal Reserve. Fedwire is the established high-value wire service with a limited operating day. FedNow is designed for continuous, everyday instant payments. It is also separate from the [RTP network](#rtp-network), a private-sector instant system run by The Clearing House. A bank can join either, both or neither, and the two do not automatically exchange payments.

FedNow is a credit push. The payer's institution sends the money, so the service cannot be used as a card-style pull. Request-for-payment messages exist, but the payer still has to approve the payment. The Federal Reserve sets a network transaction limit, and participants may set lower ones, so check current values with your bank.

The failure teams usually meet is reachability. A checkout or [payout](#payout) offers "instant", but the recipient's bank is not enabled to receive FedNow, or it only receives and cannot send. Check reachability by routing number first, and fall back to another rail with the customer told about the slower timing.

_Usage:_

"Why did this instant payout fail for only some customers?"

"Their banks aren't enabled for FedNow. Check reachability by routing number and fall back to [ACH](#ach)."

### RTP network

The RTP network is a US instant payment system operated by The Clearing House, a company owned by large banks. It launched in 2017 and runs around the clock. Participating institutions send credit transfers using [ISO 20022](#iso-20022) messages, and receivers can have the funds within seconds. Payments on the network are final.

[Settlement](#settlement) relies on a prefunded joint account held at the Federal Reserve Bank of New York. Participants fund their positions in that account, and each payment adjusts their balances on The Clearing House's records as it is processed. This model lets the network settle while traditional wire systems are closed.

| Property     | RTP network       | [FedNow](#fednow)                | [ACH](#ach)                 | [Fedwire](#fedwire)             |
| ------------ | ----------------- | --------------------- | ------------------- | ------------------- |
| Operator     | The Clearing House | Federal Reserve Banks | Nacha rules, two operators | Federal Reserve Banks |
| Availability | Continuous        | Continuous            | Processing windows  | Business days       |
| Direction    | Credit push       | Credit push           | Credit and debit    | Credit push         |
| Finality     | Final             | Final                 | Returns possible    | Final               |

The RTP network and FedNow are separate. A bank on one is not automatically reachable through the other, which is the main point of confusion for teams adding instant [payouts](#payout) in the US. The network also carries Request for Payment messages, which ask a payer to approve a push. A request is not a debit, so nothing moves until the payer agrees.

The failure engineers meet is a payout that works in testing and then fails for a portion of real customers because their bank does not receive RTP payments. Check eligibility for each routing number before promising instant delivery, and keep a fallback rail. Because payments are final, a payout to a wrong account depends on the recipient's bank and the recipient agreeing to send it back. Limits are set by the network and by each bank, and they change, so confirm them with your provider.

_Usage:_

"Can we promise instant payouts to every US account?"

"No. The RTP network doesn't reach every bank, so check the routing number and fall back to ACH."

### Faster Payments

Faster Payments is the UK's system for near-real-time bank transfers in sterling, operated by Pay.UK. It runs 24 hours a day and carries everyday transfers, bill payments and many [payouts](#payout). A customer usually sees the money arrive within seconds, although banks can hold a payment for fraud checks.

| Step | Who                  | What happens                                 |
| ---- | -------------------- | -------------------------------------------- |
| 1    | Payer                | Enters the sort code, account number and reference |
| 2    | Sending bank         | Checks the payment and submits it            |
| 3    | Faster Payments      | Routes it to the receiving bank              |
| 4    | Receiving bank       | Accepts it and credits the payee             |
| 5    | Bank of England      | Settles net positions in cycles              |

The customer experience is immediate, but interbank [settlement](#settlement) is not. According to the Bank of England, Faster Payments settles on a deferred net basis three times each business day in its [RTGS](#rtgs) service, with direct participants prefunding their maximum exposure. It should not be confused with CHAPS, the UK's high-value system, which settles each payment gross. Bacs is a third, batch-based UK system and is the one used for UK direct debits.

Pay.UK's New Payments Architecture is intended to replace Faster Payments and use [ISO 20022](#iso-20022). Its timing has moved before, so check Pay.UK's current plans.

A common failure is authorised push payment fraud, where a criminal persuades a customer to send money. The customer approved it, so the transfer completes. Since 7 October 2024, Payment Systems Regulator rules have required in-scope payment firms to reimburse victims, subject to conditions and a maximum amount that can be revised. A missing reference is a separate problem, because it leaves a received payment unmatched. Give each customer a unique reference, and use Confirmation of Payee, the UK name-checking service, before paying new accounts.

_Usage:_

"The customer says they paid by bank transfer, but the order is still open."

"The Faster Payment landed without our reference. Match it manually and show the reference more clearly at checkout."

### Correspondent banking

Correspondent banking is an arrangement in which one bank, the correspondent, holds an account for another bank, the respondent, and makes or receives payments on its behalf. A bank needs this when it has no direct access to the payment system of a currency. A small bank in France, for example, usually cannot settle US dollars in [Fedwire](#fedwire), so it holds dollars at a US bank that can.

A cross-border payment may pass through several banks:

| Step | Who                    | What happens                                       |
| ---- | ---------------------- | -------------------------------------------------- |
| 1    | Payer's bank           | Debits the payer and sends the instruction         |
| 2    | Its correspondent      | Debits the payer's bank's account and screens the payment |
| 3    | Intermediary, if any   | Passes value toward the beneficiary's bank         |
| 4    | Beneficiary's bank     | Receives value and credits the beneficiary         |

Correspondent banking is often confused with [SWIFT](#swift). Swift carries the messages between these banks. The correspondent accounts, or a [settlement](#settlement) system such as an [RTGS](#rtgs), carry the value. The account is called a [nostro account](#nostro-account) by the bank that owns it and a vostro account by the bank that holds it.

Each bank in the chain performs its own compliance checks, including [sanctions screening](#sanctions-screening) and [AML](#aml) review, and may charge a fee. This produces two common complaints. The first is a short payment: an invoice for 10,000 arrives as 9,965 because an intermediary deducted its charge. The sender can reduce this by choosing a charge option, where `OUR` means the sender pays, `SHA` means costs are shared and `BEN` means the beneficiary pays, though not every bank honours it fully. The second is a payment that stops for days while a bank asks about its purpose or parties.

Correspondents may also withdraw from relationships they consider high-risk, known as de-risking.

_Usage:_

"The supplier received 35 dollars less than we sent."

"An intermediary in the correspondent banking chain took its fee. Send it as `OUR` next time, and gross up if needed."

### Nostro account

A nostro account is an account that a bank holds at another bank, usually in a foreign currency, in order to make and receive payments in that currency. The word comes from the Italian for "ours". The bank holding the account calls the same account a vostro account, meaning "yours". Both names describe one account seen from two sides.

A nostro is an asset on the owning bank's books, because it is money owed to that bank. The matching vostro is a liability on the correspondent's books. This example shows Bank A paying 1,000 USD on behalf of a customer through its nostro at Bank B, with the beneficiary also banking at B:

| Bank | Account                   | Type      | Debit | Credit |
| ---- | ------------------------- | --------- | ----: | -----: |
| A    | Customer's USD account    | Liability | 1,000 |        |
| A    | Nostro at Bank B          | Asset     |       |  1,000 |
| B    | Vostro for Bank A         | Liability | 1,000 |        |
| B    | Beneficiary's account     | Liability |       |  1,000 |

Each bank's entries balance. Bank A's nostro asset and its liability to the customer both fall by 1,000. Bank B's total liabilities stay the same, because its obligation moves from Bank A to the beneficiary.

Banks use nostros as part of [correspondent banking](#correspondent-banking), and their treasury teams must keep enough in each currency to cover outgoing payments. Too little causes failed or delayed payments or overdraft charges. Too much ties up cash in idle balances.

The operational task is nostro reconciliation: comparing the bank's internal record of the account with the statements sent by the correspondent. An item on one side but not the other is called a break. Common causes are a fee the correspondent deducted, a payment in transit across a cut-off, or a duplicate. Unresolved breaks can hide errors or fraud, so teams track their age.

_Usage:_

"Why is the USD position 25 dollars off this morning?"

"There's a nostro break. The correspondent deducted a fee that we haven't booked, so post it and clear the item."

### IBAN

An IBAN, or International Bank Account Number, is a standard format for identifying a bank account across borders, defined by ISO 13616. It starts with a two-letter country code and two check digits, followed by a country-specific Basic Bank Account Number. It can be up to 34 characters long, and each country has a fixed length. [Swift](#swift) acts as the registration authority and publishes the registry of national formats.

| Part         | Example from `GB82 WEST 1234 5698 7654 32` | Meaning                  |
| ------------ | ------------------------------------------ | ------------------------ |
| Country      | `GB`                                       | United Kingdom           |
| Check digits | `82`                                       | Detects typing errors    |
| BBAN         | `WEST12345698765432`                       | Domestic bank and account |

IBANs are used across Europe and in many countries in the Middle East and elsewhere. They are required for [SEPA Credit Transfer](#sepa-credit-transfer) payments. The US does not use them, relying on a routing number and account number instead, so a form that insists on an IBAN will block American payees. An IBAN is also not a BIC: the BIC identifies a bank, while the IBAN identifies an account.

The check digits use a modulo 97 calculation. Move the first four characters to the end, convert letters to numbers (A is 10, B is 11), and the remainder must equal 1.

```js
const valid = (iban) => {
  const s = iban.replace(/\s/g, "").toUpperCase();
  const n = (s.slice(4) + s.slice(0, 4)).replace(/[A-Z]/g, (c) => c.charCodeAt(0) - 55);
  return BigInt(n) % 97n === 1n;
};
```

Passing this check only means the number is well formed. It does not prove that the account exists or belongs to the named person, so a mistyped but valid IBAN can still send money to a stranger. Verification of payee, which is required for euro transfers under the EU Instant Payments Regulation, addresses that gap. Store IBANs in uppercase without spaces, display them in groups of four, and validate length per country.

_Usage:_

"The form rejected a customer's IBAN, but it's correct on their statement."

"They pasted it with non-breaking spaces. Strip all whitespace before validating."

### ISO 20022

ISO 20022 is an international standard for building financial messages from a shared data model. It defines business concepts such as debtor, creditor and remittance information, and message definitions built from them, most commonly expressed in XML. It is a language for payment data. It is not a network or a payment rail.

Message names show their purpose:

| Family | Example    | Use                                   |
| ------ | ---------- | ------------------------------------- |
| `pain` | `pain.001` | Customer instructs its bank to pay    |
| `pacs` | `pacs.008` | Bank-to-bank customer credit transfer |
| `pacs` | `pacs.004` | [Payment return](#payment-return)                        |
| `camt` | `camt.053` | Account statement                     |

ISO 20022 is sometimes confused with [ISO 8583](#iso-8583), the older standard for card messages. [Card networks](#card-network) still rely mainly on ISO 8583, while ISO 20022 has spread across bank payment systems:

| System              | ISO 20022 status                                       |
| ------------------- | ------------------------------------------------------ |
| SEPA schemes        | Used by the schemes                                    |
| T2 (euro area)      | Migrated March 2023                                    |
| CHAPS (UK)          | Migrated June 2023                                     |
| CHIPS (US)          | Migrated April 2024                                    |
| [Fedwire](#fedwire)             | Migrated 14 July 2025                                  |
| [Swift](#swift) cross-border  | MT coexistence for payment instructions ended 22 November 2025 |
| [FedNow](#fednow), [RTP network](#rtp-network) | Built on ISO 20022                                     |
| [Faster Payments](#faster-payments)     | Planned through Pay.UK's New Payments Architecture     |

Structured addresses are the main unfinished item. Swift planned to reject fully unstructured postal addresses from November 2026, then agreed in 2026 to extend the timeline for payment messages. Check its current roadmap.

The failures usually come from translation between formats. A system that converts rich ISO 20022 fields into an older format can truncate a long name or lose invoice references, and reconciliation then fails downstream. A payment can also be rejected because a required structured field is empty. Keep the original message, map fields explicitly, and test with real long names, non-Latin transliterations and full remittance data.

_Usage:_

"Invoice references started disappearing from incoming payments."

"Our adapter still flattens ISO 20022 into the old format and truncates the remittance field. Map it directly."

### Direct debit mandate

A direct debit mandate is the authorization a payer gives a creditor to collect money from their bank account. It identifies the parties and the account, and it sets the terms of the collection. Without a valid mandate, a debit can be returned as unauthorised. Each scheme has its own name and rules for it:

| Region | Scheme or service         | Mandate details                                                   |
| ------ | ------------------------- | ----------------------------------------------------------------- |
| SEPA   | [SEPA Direct Debit](#sepa-direct-debit)         | Creditor identifier plus a unique mandate reference               |
| UK     | Bacs Direct Debit         | Direct Debit Instruction, backed by the Direct Debit Guarantee    |
| US     | [ACH](#ach)                       | Authorization under Nacha rules, with requirements by entry type  |
| India  | [UPI](#upi) AutoPay and NACH      | Registered e-mandate, under Reserve Bank of India and NPCI rules  |
| Brazil | [Pix](#pix) Automático            | Payer's prior authorization, under Banco Central do Brasil rules  |

A mandate differs from a [stored credential](#stored-credential). A stored credential is a saved card used under [card network](#card-network) rules. A mandate authorises debits from a bank account under a bank scheme. It also differs from [recurring billing](#recurring-billing), which is the business process that decides when to collect. A mandate is only the permission.

Under the UK guarantee, if an error is made, the payer's bank must give a full and immediate refund, then reclaim it from the collecting organisation through an indemnity claim.

The failures are mostly about evidence and lifecycle. A customer disputes a debit and the business cannot produce the mandate, so it loses the money. A migration between providers drops mandate references, and the next collection is rejected. A price rise goes out without the required advance notice, and customers claim refunds.

Store the reference, scheme, signature date, wording version and proof of consent. Mark a mandate as cancelled as soon as the bank or customer revokes it, and stop collecting against it.

_Usage:_

"The bank returned the debit saying there's no valid mandate."

"We lost the mandate references in the provider migration. Pause collections and re-collect them from affected customers."

### Payment return

A payment return is a bank-rail message that sends a debit or credit back to the originating bank because it could not be applied or is being contested. The money moves back, and the message carries a reason code. Returns occur on [ACH](#ach), SEPA and other bank rails, often after the payment appeared successful.

A return is different from a [refund](#refund), which the [merchant](#merchant) chooses to issue, and from a [chargeback](#chargeback), which is the card dispute process. It also differs from a rejection, where a payment is refused before [settlement](#settlement). SEPA groups these exceptions as R-transactions, including rejects, returns, refunds and recalls.

| Rail | Code   | Meaning                              |
| ---- | ------ | ------------------------------------ |
| ACH  | `R01`  | Insufficient funds                   |
| ACH  | `R02`  | Account closed                       |
| ACH  | `R03`  | No account, or unable to locate it   |
| ACH  | `R10`  | Consumer says the debit was unauthorised |
| ACH  | `R29`  | Business says the debit was unauthorised |
| SEPA | `AC04` | Account closed                       |
| SEPA | `AM04` | Insufficient funds                   |
| SEPA | `MD01` | No valid mandate                     |

Return windows depend on the rail, the code and the payer type. Nacha and the European Payments Council set them in their rules, and they can change. An unauthorised claim can arrive much later than an insufficient-funds return.

A loss occurs when a platform credits a user's balance on submission, the user withdraws the money, and the debit then returns. The platform carries the loss. Hold funds according to risk, and treat bank debits as provisional until the relevant window has passed.

Record a return as a new [ledger](#ledger) entry that reverses the original, and never edit or delete the original row. Handle codes differently: `R01` may justify a later retry within scheme limits, while `R10` means stop collecting and investigate. Nacha limits how a returned debit may be reinitiated.

_Usage:_

"This user's balance went negative overnight. What happened?"

"Their funding debit came back as a payment return, `R01`, after they'd withdrawn. Post a reversal and restrict the account."

### Open banking

Open banking is a framework that lets authorised third parties, with a customer's consent, read bank account data or initiate payments from that account through the bank's interfaces. An account information provider reads balances and transactions. A payment initiation provider starts a payment from the customer's account.

The legal basis differs by country:

| Jurisdiction | Basis                                  | Status to check                                         |
| ------------ | -------------------------------------- | ------------------------------------------------------- |
| EU           | [PSD2](#psd2)                                   | PSD3 and a Payment Services Regulation were provisionally agreed in November 2025; check publication and application dates |
| UK           | 2017 Competition and Markets Authority order for the largest banks | Long-term framework under the Data (Use and Access) Act 2025 is still being put in place |
| US           | Consumer Financial Protection Bureau Section 1033 rule | The 2024 rule is under agency reconsideration, and compliance dates have been in flux |
| Brazil       | Open Finance under Banco Central do Brasil rules | Operating, with rules that continue to develop |

Open banking differs from [pay by bank](#pay-by-bank), which is one product built on top of it. It also differs from screen scraping, where a service logs in with the customer's credentials and reads web pages. Regulated interfaces use consent and scoped access, so the third party never receives the banking password.

Consent is the most common operational problem. Access can expire or need renewed customer authentication, depending on the regime and the bank. A lending or accounting product then stops receiving transactions, and users see stale balances with no obvious error. Bank interfaces also vary in quality, so one bank's outage can break a segment of customers.

Track consent expiry and prompt users before it lapses. Monitor success rates per bank, and show the last successful sync time so a stale balance is visible. Check whether your activity requires authorisation or can run through a licensed provider.

_Usage:_

"Half our users' bank feeds stopped updating last night."

"Their open banking consents expired. Prompt them to reauthenticate, and warn them before expiry from now on."

### Pay by bank

Pay by bank is a checkout method in which a customer pays a [merchant](#merchant) directly from a bank account instead of with a card. In many markets it uses [open banking](#open-banking): a licensed payment initiation provider sends the customer to their bank to approve a pre-filled transfer. The underlying rail depends on the country, for example [Faster Payments](#faster-payments) in the UK or a [SEPA Credit Transfer](#sepa-credit-transfer) or [SEPA Instant](#sepa-instant) in Europe. In the US, products under this name often use linked accounts and an [ACH](#ach) debit, and some use instant rails.

| Step | Who                   | What happens                                 |
| ---- | --------------------- | -------------------------------------------- |
| 1    | Customer              | Chooses pay by bank and selects a bank       |
| 2    | Payment provider      | Creates a payment with amount and reference  |
| 3    | Customer's bank       | Authenticates the customer, who approves     |
| 4    | Customer's bank       | Sends the payment on the rail                |
| 5    | Merchant              | Confirms receipt, then fulfils               |

Compared with cards, there is no [interchange fee](#interchange-fee) and usually no card-style [chargeback](#chargeback). That shifts the risk. Consumer protection comes from the rail and local law, not [card network](#card-network) rules, and it differs by market. A push payment is generally hard to reverse, while a US ACH debit can come back later as a [payment return](#payment-return).

The common engineering mistake is treating the customer's approval as payment received. "Authorised" at the bank can still become rejected, pending or delayed by a fraud check. A customer can also close the browser after approving, so the redirect never reaches your site and the order looks abandoned. Rely on server-side status from the provider and query it if no update arrives.

[Refunds](#refund) also work differently. There is no card to credit, so the merchant needs the payer's account details or a provider feature that returns funds.

_Usage:_

"The customer's bank says they paid, but our order is still pending."

"With pay by bank the redirect can fail after approval. Query the provider's status instead of relying on the return URL."

## Section 8 — Payment Methods

### Digital wallet

A digital wallet is an app or online account that stores a customer's payment credentials, a balance, or both, and uses them to make payments. The type determines who holds the money and which rail carries the payment.

| Type          | Example               | How it pays                                             | Holds funds? |
| ------------- | --------------------- | ------------------------------------------------------- | ------------ |
| Pass-through  | Apple Pay, Google Pay | Passes a card credential, often a [network token](#network-token), to the [merchant](#merchant) | No |
| Staged        | PayPal paying with a linked card | Wallet charges the funding source, then pays the merchant | Sometimes |
| Stored value  | Balance in a wallet account | Spends a balance held by the provider              | Yes          |

In a pass-through wallet, the payment is still a card payment. The [issuer](#issuer) approves it, the merchant's [acquirer](#acquirer) processes it, and the usual card fees and [chargeback](#chargeback) rules apply. A wallet is therefore not a rail in its own right. A staged or stored-value wallet is different, because the wallet provider is a party to the payment, and holding customer balances generally requires a licence such as e-money authorisation, with duties such as [safeguarding](#safeguarding).

Device wallets replace the card number with a device-specific token and authenticate the customer with a biometric or passcode. Because of this, the last four digits shown in the wallet may differ from those printed on the physical card. A common support ticket follows: a customer gives the digits from their plastic card, and the agent cannot find the order. Search by the token's last four digits, the amount and the date, or use the provider's transaction reference.

Expect a saved wallet token to stop working when a customer changes device or removes the card. Store the wallet type separately for reporting, since [authorization rates](#authorization-rate) and fraud patterns can differ from manually entered cards.

_Usage:_

"Support can't find this order using the customer's card number."

"They paid with a digital wallet, so the last four belong to the device token. Search by amount and date."

### Buy now pay later

Buy now pay later, or BNPL, is a form of short-term credit offered at checkout that lets a customer split a purchase into instalments or defer payment. A BNPL provider typically pays the [merchant](#merchant) up front, less a fee, and then collects repayments from the customer. Some plans charge no interest and may charge late fees, while longer plans can charge interest. Terms vary by provider and country.

| Party    | Role                                                   |
| -------- | ------------------------------------------------------ |
| Customer | Agrees a credit plan and repays on schedule            |
| Provider | Assesses the customer, pays the merchant, collects     |
| Merchant | Receives funds, pays a fee, handles returns and [refunds](#refund) |

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

### UPI

UPI, the Unified Payments Interface, is India's real-time payment system for moving money between bank accounts through mobile apps. The National Payments Corporation of India (NPCI) operates it, under the oversight of the Reserve Bank of India. Banks and licensed third-party apps connect to it, so customers of different banks can pay each other.

| Element           | What it is                                                |
| ----------------- | --------------------------------------------------------- |
| UPI ID            | A virtual address such as `name@bank`, hiding account details |
| UPI PIN           | A secret the customer enters to authorise a debit         |
| PSP app           | The app the customer uses to send or approve a payment    |
| [QR code payment](#qr-code-payment)   | A [merchant](#merchant) code the customer scans to pay                 |
| AutoPay           | A registered mandate for recurring debits                 |
| UPI Lite          | An on-device balance for small payments without a PIN     |

UPI is the rail, and consumer apps are built on it. It differs from a card payment because funds normally come straight from a bank account, although NPCI also supports RuPay credit cards and pre-sanctioned credit lines on UPI.

NPCI's rules change regularly. Its consolidated circular of September 2026 says the collect function must not be available for person-to-person payments. For recurring payments, the Reserve Bank's E-mandate Framework, 2026 covers registration, additional authentication and pre-debit notification. Limits and fees are set by NPCI, the Reserve Bank and banks, so confirm them at the source.

The typical failure is a payment stuck as pending. The customer's bank has debited the account, but the merchant has received no confirmation, and the customer pays again. Treat pending as an unknown outcome. Query the transaction status with your reference before offering a retry.

_Usage:_

"The customer was debited, but the order shows unpaid."

"The UPI transaction is still pending. Run a status check on our reference before letting them pay again."

### Pix

Pix is Brazil's instant payment system, created and operated by the Banco Central do Brasil. It runs 24 hours a day and moves money between accounts at participating institutions within seconds. Transfers settle through the central bank's Instant Payment System, known as SPI.

| Element         | What it is                                                   |
| --------------- | ------------------------------------------------------------ |
| Pix key         | An alias such as a tax ID, phone, email or random key        |
| DICT            | The central bank's directory mapping keys to accounts        |
| Static QR       | A reusable code, often with an open amount                   |
| Dynamic QR      | A code generated per charge, with an amount and identifier   |
| Pix Automático  | Recurring collection under one prior payer authorization, live since 16 June 2025 |
| MED             | Special Return Mechanism for suspected fraud and certain failures |

Pix is a credit push: the payer's institution sends the funds. That distinguishes it from a card payment, which involves an authorization and later [settlement](#settlement), and from boleto, a payment slip that clears on a slower cycle.

Pix has a dedicated fraud-return process. Under MED, the receiving institution can block funds and return them when fraud is reasonably suspected. The central bank made MED 2.0, which extends tracing of funds across accounts, mandatory from 2 February 2026. A [merchant](#merchant) can therefore lose funds it believed were final. Rules continue to change, so check the current Pix regulation.

For merchants, the most common operational failure is matching. A static QR code without a usable identifier produces a credit that cannot be tied to an order. Use a dynamic QR with a unique transaction ID per order, confirm from the provider's server-side event, and never accept a customer's screenshot as proof, because it can be faked. Record any later MED return as a new [ledger](#ledger) entry.

_Usage:_

"Finance has a Pix credit with no matching order."

"That came through our old static QR. Move checkout to dynamic codes so every payment carries an order ID."

### Virtual card

A virtual card is a payment card that exists only as digital details: a card number, expiry date and security code. An [issuer](#issuer) creates it, often through a card programme run by a fintech with a [sponsor bank](#sponsor-bank). It can be restricted to one [merchant](#merchant), one use, a maximum amount or a period of time. Businesses use them to pay suppliers, control employee spending and book travel.

| Control          | Effect                                               |
| ---------------- | ---------------------------------------------------- |
| Single use       | Closes after the first successful payment            |
| Merchant lock    | Works only at a chosen merchant or [merchant category code](#merchant-category-code) |
| Amount limit     | Declines anything above the set value                |
| Expiry           | Stops working after a chosen date                    |

A virtual card is often confused with a [network token](#network-token). A virtual card has a real [PAN](#pan) and can be used anywhere its controls allow, on the [card network](#card-network) like any other card. A network token replaces an existing card number for a specific merchant or device, and it cannot be typed into another checkout.

The controls that make these cards useful also cause most of their failures. A merchant lock fails because the supplier's payment went through a parent company or a different merchant category. A hotel adds an [incremental authorization](#incremental-authorization) above the amount limit and the charge is declined. A single-use card is closed, and a later top-up or subscription renewal fails. A [refund](#refund) to a closed virtual card may need manual handling by the issuer.

A hotel or rental desk may also ask for the physical card used at booking, which does not exist. Set the limit to cover expected holds and final charges, keep the card open until the transaction has fully completed, and tell the traveller in advance how payment will work.

_Usage:_

"The supplier says our payment was declined again."

"The virtual card is locked to their old merchant category. Reissue it with the new one and raise the limit."

### Prepaid card

A prepaid card is a payment card that draws on money loaded in advance rather than on a linked bank account or a credit line. An [issuer](#issuer), or a programme manager working with one, holds the balance. Common forms are gift, payroll, travel and reloadable general-purpose cards. Most run on a [card network](#card-network), so a [merchant](#merchant) accepts them like other cards.

| Card type | Spends from                        | Issuer's exposure       |
| --------- | ---------------------------------- | ----------------------- |
| Credit    | A credit line, repaid later        | Credit risk             |
| Debit     | The holder's bank account          | Mostly the account balance |
| Prepaid   | A balance loaded in advance        | Limited to the balance, plus programme risk |

Regulation depends on the product and the jurisdiction. In the US, the Consumer Financial Protection Bureau's Prepaid Rule applies disclosure and error-resolution protections to many prepaid accounts. In the EU and UK, many prepaid products are e-money, so issuers need authorisation and must meet [safeguarding](#safeguarding) requirements. Gift cards and closed-loop cards usable at one merchant may fall under different rules or exemptions.

A merchant usually meets prepaid cards through declines. An [authorization hold](#authorization-hold) for an estimated amount can exceed the remaining balance, which is common at fuel pumps and hotels, even if the final charge would have fit. The [BIN](#bin) can also show that a card is prepaid, and some merchants block these cards for subscriptions because they run out of funds on renewal.

Some card programmes support partial approval, where the issuer approves only the available balance and the customer pays the rest another way. Enable it if your checkout can collect a second payment. [Refunds](#refund) can also be awkward when a card has expired or been discarded, so keep an alternative refund route, such as store credit where the law allows.

_Usage:_

"This customer's card keeps declining at pre-auth, but they say there's money on it."

"It's a prepaid card and our hold is bigger than the balance. Lower the hold or support partial approval."

### QR code payment

A QR code payment is a payment started by scanning a two-dimensional code that carries payment information. The QR code is only a way to pass data between devices. The money moves on a separate rail, such as [UPI](#upi), [Pix](#pix), a [card network](#card-network) or a [digital wallet](#digital-wallet)'s own system. Two transactions that look identical at the till can therefore have different fees, finality and dispute rights.

EMVCo, the card industry's technical standards body, publishes QR specifications for two modes:

| Mode                | Who shows the code | Who scans | Typical use                |
| ------------------- | ------------------ | --------- | -------------------------- |
| Merchant-presented  | Merchant           | Customer  | Stickers, screens, invoices |
| Consumer-presented  | Customer's app     | Merchant  | Retail tills with scanners |

Merchant-presented codes can be static or dynamic. A static code is printed once and normally identifies only the payee, so the customer types in the amount. A dynamic code is generated for one payment and includes the amount and a reference, which makes automatic matching possible. National systems define their own formats, many of them based on the EMVCo specification.

QR payment is often confused with contactless card payment. A tap uses NFC, a short-range radio link, and [EMV](#emv) card technology. A QR payment uses a camera and usually an app, and needs no card terminal in merchant-presented mode.

Static codes create two recognisable failures. A fraudster places a sticker with their own code over the merchant's, and customers pay the wrong account while believing the payment succeeded. A shop assistant accepts a customer's success screen, which can be faked or may show a payment that later failed.

Use dynamic codes where possible, and check displayed codes regularly if you use static ones. Release goods only when your own terminal, app or provider confirms the credit.

_Usage:_

"Three customers say they paid, but nothing reached our account."

"Someone put a fake sticker over the QR code at the till. Replace it and switch to dynamic codes."

### Cash voucher

A cash voucher is a payment method in which a [merchant](#merchant)'s checkout generates a reference or barcode, and the customer pays it in cash at a participating location such as a convenience store, bank agent or lottery kiosk. The collection network then reports the payment. Examples include boleto in Brazil, OXXO in Mexico and konbini payments in Japan. Vouchers let people without cards or bank accounts buy online. Boleto can also be paid through banking apps.

| Step | Who                | What happens                               |
| ---- | ------------------ | ------------------------------------------ |
| 1    | Customer           | Chooses the voucher method at checkout     |
| 2    | Provider           | Issues a reference with an amount and expiry |
| 3    | Customer           | Pays at a store, agent or banking app      |
| 4    | Collection network | Records the payment and notifies the provider |
| 5    | Merchant           | Receives confirmation and fulfils          |

A voucher is asynchronous. The order sits unpaid between steps 2 and 4, for hours or days, and some customers never pay. It is different from a [prepaid card](#prepaid-card), where value is loaded before the purchase and spent through a [card network](#card-network). It also has no authorization step, so a merchant cannot know at checkout whether payment will happen.

Stock is the usual problem. Reserving items for every voucher lets unpaid orders hold stock, while reserving nothing lets a customer pay for an item that has sold out. Set an expiry that fits your stock, and define what happens when a payment is reported after expiry. Provider notifications may also arrive late or more than once, so make the handler safe to run repeatedly.

Vouchers generally have no card-style [chargebacks](#chargeback), but a [refund](#refund) can need the customer's bank details because there is no card to credit. Forged vouchers also exist, so generate them only through your provider.

_Usage:_

"A customer paid their boleto, but the order had already been cancelled."

"The cash voucher expired before the payment was reported. Refund it or reinstate the order, and handle late payments in the state machine."

### Stablecoin payment

A stablecoin payment is a transfer of value using a blockchain token designed to hold a stable price against a reference asset, usually a currency. An issuer creates the tokens and, for fiat-backed designs, holds reserves intended to support redemption. A sender signs a transaction from a wallet, the blockchain records it, and the recipient's wallet receives the token. Businesses often use a provider to convert between bank money and tokens, known as on-ramping and off-ramping.

A stablecoin is not a bank deposit, and stability is not guaranteed. A token can trade below its reference value if confidence in its reserves or redemption falls. Whether holders can redeem directly, and on what terms, depends on the issuer and the applicable law. This entry is not investment or financial advice.

The legal position differs by jurisdiction:

| Jurisdiction | Position                                                                                 |
| ------------ | ---------------------------------------------------------------------------------------- |
| EU           | MiCA regulates e-money and asset-referenced tokens. The European Banking Authority advised that some e-money token services also need [PSD2](#psd2) authorisation from 2 March 2026 |
| US           | The GENIUS Act and the OCC's final rule for its issuers take effect on 18 January 2027   |
| UK           | Financial Conduct Authority stablecoin rules are final, with the regime starting 25 October 2027 |

Unlike a card payment, a stablecoin transfer has no [chargeback](#chargeback), and a confirmed transfer to a wrong address is generally unrecoverable. The same token can exist on several blockchains, so sending on a network the recipient does not support can strand funds. [Sanctions screening](#sanctions-screening) and [AML](#aml) duties can still apply.

Wait for the confirmation depth your risk policy requires before crediting a user. Store the chain, token contract, transaction hash and amount as an integer in the token's base units, because tokens define their own decimals.

_Usage:_

"The customer sent the stablecoin payment, but our wallet shows nothing."

"They used a chain we don't support. Check the transaction hash, and show the network at checkout."

## Section 9 — Payments Engineering

### Payment intent

A payment intent is a record that represents one thing a customer intends to pay for, including the amount, currency and current status. It stays the same while the attempts to fulfil it change. Stripe uses the name PaymentIntent. Other providers call a similar object an order, session or payment, and many teams build their own.

The important split is between the intent and its attempts. A customer may try one card, get a decline, and succeed with another. That is one intent with two attempts.

```json
{
  "id": "pi_123",
  "order_id": "ord_987",
  "amount": 4999,
  "currency": "EUR",
  "status": "requires_payment_method",
  "attempts": [{ "id": "att_1", "outcome": "declined" }]
}
```

| Concept  | Question it answers             | Cardinality            |
| -------- | ------------------------------- | ---------------------- |
| Order    | What is being bought?           | One order              |
| Intent   | What needs to be paid?          | Usually one per order  |
| Attempt  | What happened this time?        | Many per intent        |

The amount is stored as an integer in the currency's [minor unit](#minor-unit), so 4999 in EUR means 49.99.

Without this object, a system often models each click as a new payment. The failure is familiar: a customer's card is declined, they reload the page and try again, the earlier request also completes, and they suffer a [double charge](#double-charge) because two independent payments exist. With an intent, every attempt attaches to one record, and the system can refuse a new attempt once one has succeeded.

Enforce one active intent per order with a unique database constraint. Reuse the existing intent when the checkout page reloads, and send a provider idempotency key (a unique value that lets a server recognise a repeated request) for each attempt. Drive its status through a [payment state machine](#payment-state-machine) rather than free updates. If the amount changes, update the intent only while no attempt is in progress.

_Usage:_

"Refreshing checkout creates a new payment each time."

"Look up the existing payment intent by order ID and reuse it. Only attempts should multiply."

### Payment state machine

A payment state machine is a model that lists every status a payment can have and the transitions allowed between them. Payment events arrive from customers, providers and scheduled jobs, often late, duplicated or out of order. The state machine decides whether each event may change the record.

| From       | Event                | To         |
| ---------- | -------------------- | ---------- |
| `created`  | Authorization approved | `authorized` |
| `created`  | Declined             | `failed`   |
| `created`  | Timeout              | `unknown`  |
| `unknown`  | Status query: approved | `authorized` |
| `unknown`  | Status query: not processed | `failed` |
| `authorized` | [Capture](#capture) confirmed  | `captured` |
| `authorized` | [Void](#void) confirmed     | `voided`   |
| `captured` | Funds settled        | `settled`  |
| `settled`  | [Refund](#refund) confirmed     | `refunded` |

Real systems add partial states, such as partially captured or partially refunded, and a [chargeback](#chargeback) path. The separate `unknown` state matters because a timeout is not a failure. It holds the payment until a status query resolves an [unknown payment outcome](#unknown-payment-outcome).

A status column without these rules is the usual starting point, and it fails under concurrency. A `failed` event from an earlier attempt arrives after `captured` and overwrites it, so support sees a failed payment that the customer has paid for. Or a provider resends an event, and the fulfilment code ships twice.

Apply transitions atomically with a conditional update, so that only one writer can win:

```sql
UPDATE payments
SET status = 'captured', version = version + 1
WHERE id = $1 AND status = 'authorized';
```

If zero rows change, read the current state. A repeat of the same event is a harmless no-op, so acknowledge it. An impossible transition should be logged and alerted, not forced. Keep an append-only history of every event, because the current status alone cannot explain how the payment got there. Side effects such as shipping should run once per transition.

_Usage:_

"A late failure event flipped a captured payment back to failed."

"The handler writes whatever status it receives. Put it behind the payment state machine and reject that transition."

### Double charge

A double charge is when a customer is billed more than once for a single purchase. The usual causes are a retry after a timeout, a repeated click, two workers processing the same job, or a duplicated [capture](#capture). The customer sees two entries on their statement and contacts support, or disputes one with their bank.

Not every pair of entries is a true duplicate. An [authorization hold](#authorization-hold) can appear next to the final charge for a few days, particularly when the amounts differ, such as a hotel or fuel purchase. The bank later drops the hold. Before refunding, check whether both items were captured.

| Cause                          | How it happens                                           | Prevention                                  |
| ------------------------------ | -------------------------------------------------------- | ------------------------------------------- |
| Retry after timeout            | First request succeeded, client sent a new one           | Query status, reuse the same idempotency key |
| Double click                   | Two submissions from one form                            | Disable button, enforce one intent per order |
| Concurrent workers             | Two jobs pick up the same invoice                        | Unique constraint or row lock               |
| Replayed provider event        | Handler repeats its side effect                          | Deduplicate on event ID                     |
| Failover to another provider   | Second provider charges after an unknown first outcome   | Resolve the first attempt before routing    |

An idempotency key (a unique value that lets a server recognise a repeated request) protects one provider boundary only, so a failover to a second provider needs a status check first.

To repair a real duplicate, [void](#void) the second payment if it has not been captured, or [refund](#refund) it if it has. Record that correction as a new [ledger](#ledger) entry, leaving the original entries in place. Then find every affected customer by searching for multiple successful payments with the same order, or the same card, amount and short time window. Contact them before they raise a [chargeback](#chargeback).

_Usage:_

"Support has ten tickets about a double charge since this morning."

"The new retry job generates a fresh key per attempt. Stop it, find the duplicates by order ID, and refund them."

### Unknown payment outcome

An unknown payment outcome is the state a payment is in when the sender cannot tell whether it succeeded. It usually follows a timeout, a dropped connection, a crash after sending, or a 5xx error from a provider. The request may never have arrived, or it may have been approved with only the response lost.

This is different from a decline. A decline is a definite answer from the [issuer](#issuer) that no payment was approved. A timeout is no answer at all. Treating it as a failure can cause a [double charge](#double-charge): the app shows "Payment failed", the customer pays again, and both payments succeed.

| Step | Action                                                         |
| ---- | -------------------------------------------------------------- |
| 1    | Move the payment to `unknown` and do not fulfil or fail it     |
| 2    | Query the provider's status API with your own reference        |
| 3    | If approved, continue the normal flow                          |
| 4    | If declined or never processed, mark it failed                 |
| 5    | If not found, wait and query again, as records can lag         |
| 6    | If still unresolved, follow the provider's reversal or support route |

```text
on timeout:
  payment.status = "unknown"
  result = provider.get_by_reference(payment.reference)
  if result is pending or not_found: schedule another status check
  else: apply result through the state machine
```

Generate your reference and persist it before sending the request, or you will have nothing to query after a crash. If the provider supports idempotency keys (unique values that make a repeat return the first result), a retry with the same key is safe within the provider's documented window. Do not switch to another provider until the first attempt is resolved.

Card systems also use an [authorization reversal](#authorization-reversal) to release a possibly approved authorization when the response is lost. Show the customer a neutral message such as "We're confirming your payment", and alert when items stay unknown beyond an agreed time. [Payment reconciliation](#payment-reconciliation) is the final safety net.

_Usage:_

"The gateway timed out. Should I show an error so they can try again?"

"No, it's an unknown payment outcome. Query status by our reference first, because the charge may have gone through."

### Payment retry

A payment retry is another attempt at a payment that did not succeed or whose result is uncertain. Whether a retry is safe depends on the previous outcome. Retrying the wrong case produces a [double charge](#double-charge), a pointless decline or a network rule breach.

| Previous outcome              | Action                                                                  |
| ----------------------------- | ----------------------------------------------------------------------- |
| [Hard decline](#hard-decline)                  | Do not retry the same credential. Ask for another payment method        |
| [Soft decline](#soft-decline)                  | Retry later, or after the customer completes the requested step         |
| [Issuer](#issuer) unavailable            | Retry with backoff, possibly through another route                      |
| Connection failed before sending | Safe to retry with the same idempotency key                          |
| Timeout or unknown            | Query status first. Retry only if the attempt did not succeed           |

An idempotency key is a unique value that lets a server recognise a repeated request. Reuse it when repeating an attempt after a lost response. A new attempt after a definite decline needs a new key, because the old key would return the old decline.

[Card networks](#card-network) restrict repeated attempts. Visa groups [decline codes](#decline-code) into categories with reattempt rules, and some codes must never be retried. Mastercard returns [merchant](#merchant) advice codes, such as one telling the merchant not to try again. Limits and fees change, so get the current rules from your [acquirer](#acquirer). Hammering an issuer can also lower your [authorization rate](#authorization-rate) and resemble [card testing](#card-testing).

[Dunning](#dunning) is the wider recovery process for failed subscription payments, which schedules retries and contacts the customer.

The common failure comes from generic HTTP retry middleware wrapped around a payment client. It treats a 504 as retryable, sends a fresh request, and charges the customer twice. Remove automatic retries from payment-creating calls and put the decision in code that understands the provider's result. Add exponential backoff with jitter, a maximum attempt count, and a log of every attempt.

_Usage:_

"Should the job retry every declined card overnight?"

"Only the soft declines. A payment retry on a hard decline breaks network rules and won't succeed anyway."

### Ledger

A ledger is an append-only record of every movement of money between accounts. Each posting records the account, amount, currency, direction and a reference to the event that caused it. Balances are computed from those entries, or kept as a cached figure that can be rebuilt from them.

A ledger differs from a `payments` table. The payments table describes the state of a payment attempt and changes over time. The ledger records the financial effect of each step and never changes. A `balance` column on a user row shows a total but cannot explain it, so when a customer asks why their balance is wrong, there is no answer.

Most payment ledgers use [double-entry bookkeeping](#double-entry-bookkeeping), so each transaction's debits and credits are equal. Amounts are integers in each currency's [minor unit](#minor-unit).

Entries are never edited or deleted. To correct a mistake, post a reversal and then the correct entry. In this example, a 5000 top-up was recorded instead of 500:

| Txn | Reason         | Account          | Debit | Credit |
| --- | -------------- | ---------------- | ----: | -----: |
| 1   | Original       | Cash at provider |  5000 |        |
| 1   | Original       | Customer balance |       |   5000 |
| 2   | Reversal of 1  | Customer balance |  5000 |        |
| 2   | Reversal of 1  | Cash at provider |       |   5000 |
| 3   | Correct amount | Cash at provider |   500 |        |
| 3   | Correct amount | Customer balance |       |    500 |

After all three, cash has a net debit of 500 and the customer balance a net credit of 500. The error and its fix both remain visible to auditors.

Enforce the invariants in the database. Reject a transaction whose debits and credits differ per currency, write all of its entries atomically, and use a unique key on the source event so a replayed event cannot post twice. Reconcile it against provider and bank records, because a balanced ledger can still be wrong.

_Usage:_

"Can I just update this customer's balance to fix the mistake?"

"No. Post a reversal and a correcting entry in the ledger, so the history still adds up."

### Double-entry bookkeeping

Double-entry bookkeeping is an accounting method in which every transaction is recorded in at least two accounts, with total debits equal to total credits. Money is always shown as coming from somewhere and going somewhere. If the two sides differ, the record is wrong, and the system can detect it.

Debit and credit do not mean minus and plus. Their effect depends on the account type:

| Account type | Example                 | Debit    | Credit   |
| ------------ | ----------------------- | -------- | -------- |
| Asset        | Cash, provider receivable | Increases | Decreases |
| Liability    | Customer balances owed  | Decreases | Increases |
| Revenue      | Sales                   | Decreases | Increases |
| Expense      | Processing fees         | Increases | Decreases |

This explains a common confusion. When your bank "credits" your account, the bank's liability to you is rising. On your own books, the same cash is an asset and increases with a debit.

Here is a 100.00 sale with a 2.90 processing fee, in [minor units](#minor-unit):

| Account             | Type    | Debit | Credit |
| ------------------- | ------- | ----: | -----: |
| Provider receivable | Asset   |  9710 |        |
| Processing fees     | Expense |   290 |        |
| Sales revenue       | Revenue |       | 10000 |
| **Total**           |         | **10000** | **10000** |

When the provider pays out, debit bank cash by 9710 and credit the provider receivable by 9710. The receivable returns to zero, showing that nothing is still owed.

A single-column approach would record only +100.00 of sales, and finance would then find the bank deposit 2.90 short on every order. Double entry puts the fee in its own account, so the gap is explained.

Balance each currency separately. A conversion between currencies needs a foreign exchange account in each currency, because 100 EUR and 108 USD cannot be summed. Balanced entries do not prove correctness, since a wrong amount posted to both sides still balances, so the [ledger](#ledger) must also be reconciled against external records.

_Usage:_

"The [payout](#payout) is lower than sales. Where did the rest go?"

"Look at the fees account. With double-entry bookkeeping, each sale splits into the receivable and the fee, so the gap is itemised."

### Payment reconciliation

Payment reconciliation is the process of comparing your own payment records with external records, such as provider reports, a [settlement file](#settlement-file) and bank statements, and resolving every difference. Internal systems can show that a payment succeeded when it did not, or miss one that did. Reconciliation is how a business finds out.

A full reconciliation usually has three layers:

| Layer | Compares                           | Finds                                 |
| ----- | ---------------------------------- | ------------------------------------- |
| 1     | Internal [ledger](#ledger) and provider report | Missing or mismatched transactions   |
| 2     | Provider report and [payout](#payout) total   | Fees, [refunds](#refund) and [chargebacks](#chargeback) netted out |
| 3     | Payout total and bank statement    | Payouts that did not arrive          |

An item that does not match is called a break:

| Break                 | Likely cause                         | Action                                  |
| --------------------- | ------------------------------------ | --------------------------------------- |
| Provider has it, you don't | Lost response or event          | Create the record from provider data    |
| You have it, provider doesn't | Failed call marked successful | Correct status, check fulfilment        |
| Amount differs        | Fee, [partial capture](#partial-capture), currency       | Post an adjustment                      |
| Timing difference     | Cut-off or time zone                 | Expect it to clear in the next run      |

The familiar symptom is a payout that does not equal the day's orders. The payout is net of fees, refunds and disputes, and it may span several days under the provider's cut-off. Comparing it directly with a daily sales total will always produce noise.

Match on a stable identifier that you send to the provider and receive back in its reports, and store the provider's own ID too. Run reconciliation automatically every day and track each break's age, because a timing difference clears within days while a real error does not. Fix breaks by posting a new correcting ledger entry, never by editing history. An [unknown payment outcome](#unknown-payment-outcome) that was never resolved will often first show up here.

_Usage:_

"The provider's report shows 14 payments that aren't in our database."

"Those are payment reconciliation breaks from the event outage. Backfill them from provider data and check they were fulfilled."

### Settlement file

A [settlement](#settlement) file is a report from an [acquirer](#acquirer) or [payment service provider](#payment-service-provider) that lists each transaction, fee and adjustment included in a [payout](#payout). The bank statement usually shows one net deposit. The settlement file explains how that number was reached, so teams use it as the main input to [payment reconciliation](#payment-reconciliation).

Formats vary by provider and include CSV, fixed-width files, XML and API reports. Typical fields are:

| Field            | Purpose                                     |
| ---------------- | ------------------------------------------- |
| Batch or payout ID | Ties rows to one bank deposit             |
| [Merchant](#merchant) reference | Links a row to your order or payment      |
| Provider reference | Provider's own transaction ID             |
| Type             | Sale, [refund](#refund), [chargeback](#chargeback), fee or adjustment |
| Gross, fee, net  | The amounts for that row                    |
| Currency         | Settlement currency, sometimes also presentment |
| Dates            | Transaction date and settlement date        |

Rows must add up to the payout. This example uses [minor units](#minor-unit):

| Row type   | Net amount |
| ---------- | ---------: |
| Sales      |      10000 |
| Fees       |       -300 |
| Refunds    |      -2000 |
| Chargeback |      -1500 |
| **Payout** |   **6200** |

A settlement file is not a transaction export from a dashboard. An export shows activity by the time it occurred, while the settlement file groups items by the payout they were paid in. A sale on Friday night may fall into Monday's file because of a cut-off, so comparing it with Friday's orders produces false mismatches.

A provider can resend a corrected file, and if its rows import twice, revenue doubles. A column changes and the parser silently reads the fee as zero. A file arrives late and the reconciliation run reports hundreds of false breaks.

Keep the raw file unchanged, and make the import idempotent using the file identifier and a stable row key. Validate that rows sum to the stated total before accepting the file, and alert when a file is missing or its schema changes.

_Usage:_

"Revenue doubled on Tuesday, but the bank balance didn't."

"The provider resent the settlement file and we imported it twice. Dedupe on the row key and rerun."

### Payment routing

Payment routing is the decision about which path a payment takes: which [acquirer](#acquirer), which debit network, or which bank rail. A [merchant](#merchant) with several providers can route each payment based on the card, country, amount and current performance.

| Strategy           | Decides by                                | Trade-off                                  |
| ------------------ | ----------------------------------------- | ------------------------------------------ |
| Local acquiring    | Matching acquirer to the [issuer](#issuer)'s country | Better approvals and lower [cross-border fee](#cross-border-fee) costs, more contracts |
| Least-cost         | Expected fees                             | May lower approval rates                   |
| Performance-based  | Recent [authorization rate](#authorization-rate)                 | Needs volume and monitoring                |
| Failover           | Provider or route health                  | Must handle uncertain outcomes             |
| Rule-based         | Regulation, currency or product           | Rules drift without maintenance            |

Routing is the decision. [Payment orchestration](#payment-orchestration) is the wider layer that carries it out and also covers integrations, tokens and reporting.

Some routing is shaped by law. In the US, the Durbin Amendment requires debit cards to be enabled on at least two unaffiliated networks, which gives merchants a routing choice. In the EU, the [Interchange Fee](#interchange-fee) Regulation addresses the choice of brand on co-badged cards.

Failover after a timeout can charge a customer twice. Provider A does not answer, the router sends the same payment to provider B, B approves it, and A's approval then appears. The customer has a [double charge](#double-charge), and an idempotency key cannot prevent it because each provider has its own key space. Fail over only after a definite failure, such as a connection refused before sending or a retryable decline. For a timeout, resolve the first attempt by querying its status.

Stored cards add a constraint. A token issued by one provider usually cannot be charged through another unless you hold portable credentials or [network tokens](#network-token). Log the chosen route and reason on every attempt.

_Usage:_

"Provider A timed out, so the router sent it to B. Now the customer has two charges."

"Payment routing can't fail over on a timeout. Check A's status first and only reroute if it didn't go through."

### Payment orchestration

Payment orchestration is a software layer that connects a business to multiple payment providers, [acquirers](#acquirer) and payment methods through one integration. The [merchant](#merchant)'s checkout calls the orchestration layer, and that layer decides where each payment goes and normalises the responses.

| Function            | What it does                                                |
| ------------------- | ----------------------------------------------------------- |
| Connectors          | Translates one internal API to each provider's API          |
| [Payment routing](#payment-routing)     | Picks a provider per transaction                            |
| Token management    | Stores credentials so they can be used across providers     |
| Retry and failover  | Applies rules after a failed attempt                        |
| Normalisation       | Maps [decline codes](#decline-code) and statuses to one model                |
| Reporting           | Combines data across providers                              |

An orchestrator is often confused with a [payment service provider](#payment-service-provider) or [payment gateway](#payment-gateway). A PSP has acquiring relationships and processes payments. A gateway transmits payments to a processor. An orchestrator usually sits above them and depends on their contracts, so the merchant typically still needs its own agreement with each provider.

The benefits are redundancy, access to local methods and bargaining power. The layer also adds a network hop and another dependency that can fail, so an orchestrator outage can stop all payments. If it handles raw card data, it also affects [PCI DSS](#pci-dss) scope. Normalising responses can hide the detail needed to debug a decline, so keep the raw provider response.

Token ownership often causes problems at migration time. A business adopts multiple providers and finds that its saved cards are tokens owned by the original provider, which cannot be charged elsewhere. Negotiate token portability in advance, or use a neutral [card vault](#card-vault) or [network tokens](#network-token).

Pass a stable reference from the merchant through the orchestrator to the provider, so that a retry at any level can be recognised. Treat a timeout at any hop as an [unknown payment outcome](#unknown-payment-outcome).

_Usage:_

"Can we just add a second provider if the first goes down?"

"Only with payment orchestration and portable tokens. Otherwise our saved cards won't work on the second provider."

### Authorization rate

An authorization rate, also called an approval rate, is the share of [card authorization](#card-authorization) requests that [issuers](#issuer) approve. Teams use it to judge payment performance. The figure is meaningful only if everyone agrees on what is being counted.

The same traffic can yield different results. This example uses invented figures:

| Measure                | Approved | Total | Rate  |
| ---------------------- | -------: | ----: | ----: |
| All attempts           |      850 |  1000 | 85.0% |
| Unique payments, final outcome | 830 | 900 | 92.2% |

The first line counts every retry as a separate attempt. The second counts each payment once, using its final result. Neither is wrong, but comparing one provider's attempt-level figure with another's payment-level figure is misleading. Also decide how to treat zero-amount card checks, fraud blocks made before the issuer is asked, and [3-D Secure](#3-d-secure) failures.

Authorization rate differs from conversion rate, which measures how many visitors complete checkout and includes people who abandon before paying. It also differs from [capture](#capture) rate, which is how many authorized payments are later captured.

A sudden fall is a common alert, and the cause is not always a provider fault. [Card testing](#card-testing) floods checkout with stolen numbers that mostly fail, pulling the rate down while real customers are unaffected. An aggressive retry job has the same effect. A real problem usually concentrates in one place, such as a single issuer, [BIN](#bin) range, country or [acquirer](#acquirer).

Segment the metric by network, issuer, country, card type, channel, acquirer and [decline code](#decline-code). Exclude known bot traffic into a separate view. Common improvements include sending complete data, using [network tokens](#network-token), keeping stored cards fresh with an [account updater](#account-updater), flagging stored-credential payments correctly, and using local acquiring. Benchmarks vary widely by industry and region, so compare against your own history first.

_Usage:_

"Authorization rate dropped eight points overnight. Is the acquirer down?"

"Segment it first. Declines are all from one BIN range with new cards, so it looks like card testing."

### Stored credential

A stored credential is a card number or token that a [merchant](#merchant) or its provider saves, with the [cardholder](#cardholder)'s consent, to use for future payments. Visa and Mastercard define frameworks for these transactions. Under them, the first payment establishes the agreement, and later payments are flagged to show that the credential was stored and how it is being used.

| Stage                     | Who starts it | What must happen                                     |
| ------------------------- | ------------- | ---------------------------------------------------- |
| Consent                   | Cardholder    | Agrees to storage and the terms of future use        |
| Initial transaction       | Cardholder    | Authenticated where required, flagged as first storage |
| Later customer payment    | Cardholder    | Sent as a [customer-initiated transaction](#customer-initiated-transaction)             |
| Later merchant payment    | Merchant      | Sent as a [merchant-initiated transaction](#merchant-initiated-transaction) with the original reference |

The original reference is usually the [network transaction ID](#network-transaction-id) returned by the first authorization. Keep it with the saved credential, because later merchant-initiated payments must reference it.

Stored credentials are often confused with [tokenization](#tokenization). Tokenization is how the card number is protected, by replacing it with a substitute value. A stored credential describes the business arrangement and its transaction flags. Saving a token does not by itself create the consent or the correct flags.

The failure is often silent. A team saves cards and charges them later as if each were a normal online payment, with no stored-credential flag and no original ID. [Issuers](#issuer) see an unexpected transaction with no [CVV](#cvv) and decline more of them, and European issuers may demand [strong customer authentication](#strong-customer-authentication) that the absent customer cannot complete. Renewals fail while first payments look healthy.

Record the consent text and time, the agreed purpose, the initial transaction ID and the credential's status. Do not store the CVV after authorization, which [PCI DSS](#pci-dss) prohibits. If a customer removes a saved card, stop using it.

_Usage:_

"First payments work, but renewals decline far more often."

"We're not sending the stored credential flags or the original transaction ID. Issuers can't tell these are agreed renewals."

### Customer-initiated transaction

A customer-initiated transaction, or CIT, is a card payment in which the [cardholder](#cardholder) is present in the flow and actively takes part, for example by pressing Pay on a website or in an app. Visa calls these cardholder-initiated transactions. The card can be newly entered or saved. What makes it a CIT is the customer's involvement at that moment.

| Question                       | CIT                         | [Merchant-initiated transaction](#merchant-initiated-transaction)       |
| ------------------------------ | --------------------------- | ------------------------------------ |
| Who starts it?                 | Cardholder                  | [Merchant](#merchant), under a prior agreement    |
| Is the customer in session?    | Yes                         | No                                   |
| Can they complete a challenge? | Yes                         | No                                   |
| EEA and UK authentication      | [Strong customer authentication](#strong-customer-authentication) unless exempt | Generally outside it when set up correctly |

The most common confusion is treating any saved-card payment as merchant-initiated. A returning customer who clicks Buy using a saved card is still making a CIT. In the EEA and UK, that payment falls under strong customer authentication unless an [SCA exemption](#sca-exemption) applies, and the European Banking Authority has said that card payments initiated by the payer through the payee are in scope.

A CIT also normally sets up a [stored credential](#stored-credential). The first payment carries the authentication and consent, and its [network transaction ID](#network-transaction-id) anchors later merchant-initiated payments.

The failure appears when an engineer marks one-click checkout as merchant-initiated to avoid the extra authentication step. [Issuers](#issuer) can decline these payments, networks can treat the flag as misuse, and the merchant may lose [3-D Secure](#3-d-secure) liability protection. The reverse error also occurs, when an off-session renewal is sent as a CIT and fails because nobody is there to complete a challenge.

Set the initiator from what the user is doing in that request, rather than from whether a card is saved.

_Usage:_

"Can we flag one-click purchases as MIT to skip 3-D Secure?"

"No. The customer clicked Buy, so it's a customer-initiated transaction and needs SCA unless an exemption applies."

### Merchant-initiated transaction

A merchant-initiated transaction, or MIT, is a card payment that a merchant starts without the [cardholder](#cardholder) taking part, relying on an agreement made earlier. The merchant must have a [stored credential](#stored-credential) and consent to use it, and each MIT is flagged so the [issuer](#issuer) can see it belongs to an existing agreement.

| Type         | Example                              | Schedule                |
| ------------ | ------------------------------------ | ----------------------- |
| Recurring    | Monthly software subscription        | Fixed interval          |
| Instalment   | A purchase split into set payments   | Fixed number of payments |
| Unscheduled  | Account top-up when balance runs low | Triggered by an event   |
| Industry-specific | Hotel no-show or delayed charge | Set by network rules    |

Each MIT normally carries the [network transaction ID](#network-transaction-id) of the original or a previous transaction. This links it to the [customer-initiated transaction](#customer-initiated-transaction) in which the cardholder agreed. Without that link, an issuer may treat the payment as unexpected and decline it.

In the EEA and UK, an MIT is treated as outside [strong customer authentication](#strong-customer-authentication) because the payer is not involved at the time of payment. That position depends on a valid setup. European Banking Authority Q&As say SCA applies when the mandate is given, usually during the first payment. An MIT is not an [SCA exemption](#sca-exemption), and labelling a payment MIT when the customer is present is misuse.

The failure teams see is a batch of renewals declined with an authentication-required code. Cards saved before SCA, or saved without authentication, have no valid agreement behind them. The customer is offline and cannot complete a challenge, so the fix is to bring them back for an authenticated payment that creates a new agreement.

A customer who forgot about a subscription may dispute it as fraud, so keep the consent record and stop billing as soon as they cancel.

_Usage:_

"Half the renewal batch failed with authentication required."

"Those cards were saved without SCA, so the merchant-initiated transactions have no valid mandate. Email customers to reauthenticate."

### Recurring billing

Recurring billing is the process of charging a customer automatically at regular intervals, such as monthly for a subscription. A billing system determines what is due and creates a payment on an underlying method, which sets the rules for authentication, notice and failure.

| Method                  | Permission                 | Typical failure signal        |
| ----------------------- | -------------------------- | ----------------------------- |
| Card                    | [Stored credential](#stored-credential), charged as a [merchant-initiated transaction](#merchant-initiated-transaction) | Immediate decline |
| [SEPA Direct Debit](#sepa-direct-debit)       | [Direct debit mandate](#direct-debit-mandate)       | Later return or refund        |
| US [ACH](#ach) debit            | Authorization under Nacha rules | Later [payment return](#payment-return)     |
| [UPI](#upi) AutoPay (India)     | Registered e-mandate       | Mandate or debit failure      |
| [Pix](#pix) Automático (Brazil) | Prior payer authorization  | Scheduled payment failure     |

Rules differ by market. India's E-mandate Framework, 2026, from the Reserve Bank of India, generally requires a notification before each recurring debit on cards, prepaid instruments and UPI, and additional authentication above set amounts. Consumer rules on renewal notices and cancellation also vary by market.

Recurring billing differs from a saved card used for one-click checkout, where the customer starts each payment. It also differs from [dunning](#dunning), which handles what happens after a recurring payment fails.

A scheduler rerun after a crash can bill the same period twice. To prevent this, use an idempotency key (a unique value marking one logical charge) built from the subscription ID and billing period, and enforce it with a unique constraint. Date arithmetic also causes errors: adding one month to 31 January has no obvious answer, so store a fixed billing anchor day and clamp it to the month's length. Mid-cycle plan changes need explicit proration rules, using integer [minor units](#minor-unit) and a defined rounding direction.

Expired cards are the main cause of unintended cancellation. An [account updater](#account-updater) reduces these, and dunning recovers some of the remainder.

_Usage:_

"Some customers were billed twice on the first of the month."

"The recurring billing job restarted mid-run. Key each charge on subscription and period so a rerun can't duplicate it."

### Dunning

Dunning is the process of recovering a failed recurring payment through scheduled retries and messages to the customer. In subscription businesses, it mainly addresses involuntary churn, where a customer who intended to stay loses service because a payment failed.

A dunning policy combines payment actions and communication:

| Stage | Action                                                       |
| ----- | ------------------------------------------------------------ |
| 1     | Payment fails. Classify the decline and record the reason    |
| 2     | Run an [account updater](#account-updater) check if the card may have changed    |
| 3     | Notify the customer with a link to update payment details    |
| 4     | Retry [soft declines](#soft-decline) on a spaced schedule                     |
| 5     | Send further reminders and warn of service loss              |
| 6     | Restrict or cancel the subscription, and stop retrying       |

Dunning differs from a [payment retry](#payment-retry). A retry is one technical attempt, and dunning is the business process that decides when to retry, what to tell the customer, and when to give up. The retry schedule must respect the rail: a [hard decline](#hard-decline) should not be repeated, [card networks](#card-network) limit reattempts, and Nacha restricts how a returned [ACH](#ach) debit can be reinitiated. Reminder content and timing may also be subject to local consumer and debt-collection rules, particularly once an amount is treated as overdue.

Dunning systems fail through missing state. A customer updates their card, but the job keeps retrying the old one and sends another warning. A customer cancels, and a scheduled retry charges them anyway, producing a complaint or a [chargeback](#chargeback).

Before each step, re-read the subscription, invoice and payment method, and exit if the invoice is paid or the subscription is cancelled. When a customer adds a new card, attempt the outstanding invoice once, then end the sequence on success. Track recovered revenue and recovery rate per stage to tune the schedule.

_Usage:_

"A customer cancelled last week and we charged them again today."

"The dunning job didn't recheck the subscription before retrying. Exit the sequence on cancel and [refund](#refund) that charge."

### Account updater

An account updater is a [card network](#card-network) service that gives [merchants](#merchant) new details for cards they have on file when a card is reissued, expires or is closed. Visa Account Updater and Mastercard Automatic Billing Updater are the main examples. [Issuers](#issuer) report changes to the network, and the merchant's [acquirer](#acquirer) or provider requests updates, either in batches before billing or in real time during authorization.

| Response             | Meaning                         | Merchant action                         |
| -------------------- | ------------------------------- | --------------------------------------- |
| New card number      | Card was replaced               | Update the [stored credential](#stored-credential)            |
| New expiry           | Same number, new date           | Update the expiry                       |
| Account closed       | Card is no longer valid         | Stop billing and ask for a new method   |
| Contact [cardholder](#cardholder)   | Issuer gives no replacement     | Ask the customer                        |
| No match             | Issuer has no change or doesn't participate | Continue, and handle any decline |

Coverage depends on issuer participation, and some cardholders can opt out, so a stored card may still fail.

An account updater differs from a [network token](#network-token). A token is a substitute credential whose lifecycle is managed by the network, so the merchant can keep charging the same token after the underlying card is replaced. Account updater returns new card data to whoever holds the original [PAN](#pan). [Dunning](#dunning), by contrast, reacts after a payment fails.

The symptom it addresses is a burst of renewal declines around month end from expired cards, with customers who never meant to leave. A related bug happens when the provider updates its vault but the merchant's own record keeps the old last four digits and expiry, so the billing page shows an expired card.

Consume the provider's update events and sync display fields. Also stop charging on a closed-account response. Updated card numbers are cardholder data, so handle them within your [PCI DSS](#pci-dss) scope, or leave them with the provider.

_Usage:_

"Renewals are failing because so many cards expired this month."

"Turn on the account updater with our acquirer, and sync the new expiry dates to our billing records."

### Split payment

A split payment is a single customer payment whose funds are divided among several recipients, such as a marketplace, one or more sellers and a delivery partner. The customer sees one charge.

This example uses [minor units](#minor-unit) for a 10000 order:

| Account             | Debit | Credit |
| ------------------- | ----: | -----: |
| Provider receivable |  9700 |        |
| Processing fees     |   300 |        |
| Seller payable      |       |   8500 |
| Platform commission |       |   1500 |
| **Total**           | **10000** | **10000** |

The platform absorbs the processing fee here, so its net income from this order is 1200.

A split payment differs from split tender, where one customer pays a single bill using two cards or methods.

Regulation is a central design issue. Receiving money and passing it to third parties can count as a regulated payment service or money transmission, depending on the country. Platforms commonly use a licensed provider's marketplace product, or act as a [payment facilitator](#payment-facilitator) or a [merchant of record](#merchant-of-record). Get legal advice on the chosen structure, and expect [KYC](#kyc) or [KYB](#kyb) checks on sellers.

The hard failures occur after the split. A customer gets a [refund](#refund) or wins a [chargeback](#chargeback) after the seller has already received a [payout](#payout). The platform must recover the money from that seller, and if the seller has no balance or has left, the platform carries the loss. Delay seller payouts according to risk, and let seller balances go negative in the [ledger](#ledger) so future earnings can offset them.

Rounding is the other common bug. Splitting 10000 three ways gives 3333 each and leaves 1 unit unallocated. Use integer minor units, assign any remainder by a fixed rule, and assert that the parts sum to the total. Record the split at payment time so that later commission changes do not alter past orders.

_Usage:_

"The seller was paid out, then the buyer got a chargeback. Who covers it?"

"Under our split payment terms, the seller. Post it against their balance, and we carry it if they can't repay."

### Safeguarding

Safeguarding is the legal requirement for non-bank payment firms and e-money issuers to protect customer money so that it can be returned if the firm becomes insolvent. In the EU, the requirement comes from [PSD2](#psd2) and the Electronic Money Directive. In the UK, it comes from the Payment Services Regulations 2017 and Electronic Money Regulations 2011, supplemented by Financial Conduct Authority (FCA) rules.

Firms typically safeguard in one of two ways:

| Method      | How it works                                                       |
| ----------- | ------------------------------------------------------------------ |
| Segregation | Keep relevant funds apart from the firm's own money, in a designated account or approved secure assets |
| Insurance or guarantee | A policy or guarantee pays out an equivalent amount if the firm fails |

Safeguarding is often confused with deposit insurance. A bank deposit may be covered by a national scheme, such as the UK's Financial Services Compensation Scheme. Money held with a payment or e-money firm generally is not. If the firm fails, customers rely on the safeguarded pool, and the insolvency process can cause delay or shortfall. A [rolling reserve](#rolling-reserve) is also different, because it protects a provider from a [merchant](#merchant)'s losses.

The FCA's Policy Statement PS25/12 introduced a supplementary safeguarding regime that took effect on 7 May 2026, adding requirements such as monthly regulatory returns and, for many firms, annual safeguarding audits. US money transmitters are instead generally subject to state rules on permissible investments. Confirm the rules that apply to your licence with a qualified adviser.

The firm must know how much it owes customers at any time and prove that the safeguarded balance covers it, which requires an accurate [ledger](#ledger) and regular [payment reconciliation](#payment-reconciliation) against the safeguarding account. Failures include customer funds sitting in an operating account during a [payout](#payout) delay and shortfalls discovered days late. Alert on any difference.

_Usage:_

"Can we pay this supplier from the customer funds account until Friday?"

"No, that account is for safeguarding. Customer money can't fund operations, even temporarily."
