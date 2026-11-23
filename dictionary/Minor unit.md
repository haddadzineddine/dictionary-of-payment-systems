---
description: The smallest unit of a currency under ISO 4217, such as cents for USD, used to store money as an integer.
---

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

Some message formats use decimal strings instead. [ISO 20022](./ISO%2020022.md), for example, carries amounts such as `10.50` with a currency attribute. Convert these to integers at the system edge using exact decimal parsing, and define a rounding rule for tax, fee and foreign exchange calculations.

_Usage:_

"A Japanese customer was charged 100 times the price."

"We multiplied by 100 for every currency. JPY has no minor unit, so read the exponent from the ISO 4217 table."
