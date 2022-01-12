---
title: "Standard Syntax"
description: "RSL to describe a potentially unlimited series of steps of fixed, percentage or ratio splits, which can loop by both time period or per transaction."
lead: "A potentially unlimited series of steps of fixed, percentage or ratio splits, which can loop by both time period or by transaction."
date: 2022-01-12T01:20:13+01:00
lastmod: 2022-01-12T01:20:13+01:00
draft: false
images: []
menu: 
  docs:
    parent: "rsl"
weight: 80
toc: true
---

An RSL agreement features three components:
 1. Data for the whole **Agreement**, which appears once, and of which only Name and Currency is required.
 2. Data for a **Step** in the agreement which can appear multiple times, and of which only Type (fixed, ratio or percentage) is required. A step will contain one or more Payees.
 3. Data for a **Payee**, who can  appear multiple times per step, and of which only amount and wallet is required.

## Data for the agreement
- **Name**: 256 chars max - *REQUIRED*.
- **Currency**: (three letter [ISO currency](https://en.wikipedia.org/wiki/ISO_4217) or [crypto](https://www.finder.com.au/cryptocurrency/altcoins) code) - *REQUIRED*.
- **Decimals**: comma (,), period (.) or none. Determines if decimal places in currency ammounts are denoted with '.' or ',' or (as is the case with currencies such as Yen) no decimal places. If not set, period (.) is assumed.
- **RSL**: which RSL version is used (e.g. 0.6). This allows for future changes in RSL syntax to not break on older RSL files.
- **Description**.
- **Period**: When does the agreement reset? If not set is assumed to run indefinitely, or until the end date. Takes form of '10 transactions', '1 year', '4 weeks', etc, made up of:
	- A positive integer;
	- An interval, either 'transaction' sich as per donation, sale or membership; or time period such as day, month, year, etc
- **Starts**: a starting date for the agreement (YYYY-MM-DD), e.g. 2021-12-31. This can be used with Term to match financial reporting periods.
- **Ends**: an end date, which allows for a fixed period agreement to stop. 
- **Pointer**: following the idea of [Payment Pointers](https://paymentpointers.org/), this references a wallet, bank account, collecting society or escrow account that will receive the initial funds this agreement relates to. 
- **URL**: A public address for the agreement.
- **Contact**: Contact name for the agreement.
- **Email**: Email address for the contact.
- **Jurisdiction**: Legal jurisdiction for the agreement, ie which country the agreement is operated from / answerable to. Could be country, region or state.
- **Steps**: An array of steps

## Data for a step in the agreement, numbered sequentially:
- **Type**:  fixed, percent or ratio. Ratios are an alternative to percent, helpful for splits with recurring decimals when expressed as a % - *REQUIRED*.
- **Description**:
- **Cap**: for percentage payouts, a max payout before moving to the next step. ‘null’, or unset indicates distribution runs indefinitely.
- **Payee**: an array for payees, containing:
	- **name**;
	- **pointer**: [Payment pointer](https://paymentpointers.org/), bank account/sortcode, IBAN, Swift, email, dbse ID, etc) - *REQUIRED*;
	- **amount**: If fixed this is the fee, if percentage it is the mount (without a percentage symbol). Ratios are expressed only as the numerator (ie '1' for an equal 3-way split) - required.
	- **type** (describes the nature of the pointer, e.g. ILP, AC/sort, Wise, Stripe, Paypal, Ref, ID)

### Notes:
- payees in each step are paid at the same time, ['pari passu'](https://en.wikipedia.org/wiki/Pari_passu) until all are paid.
- if payees are in a percentage step but don’t add up to 100, the processor must transform them into a % of their sum.

## Examples

### 1: Book publisher advance
An author signs a deal for 25% of net sales (with 10% to her agent) after a £10,000 advance is paid back to the publisher. To return the advance, the first step (step1) pays only the publisher until the 25% net figure is reached, ie when the publisher has earned £40,000.

```
---
name: "Best of times, Worst of times"
rsl version: 1.0
description: "Book deal for the new novel by Charlene Dickens"
url: example.com/248mc0u3489mc
currency: GBP
decimals: period
steps:
  -
    type: fixed
    payee:
      - ["PRNG House", $ilp.example.com/prng, ilp, 40000]
  -
    type: percent
    payee: 
      - ["Charlene Dickens", 12345678/12-34-56, uk-ac, 22.5 ]
      - ["Internet Aritsts Management", payment@example.com, paypal, 2.5]
      - ["PRNG House", $ilp.example.com, ilp, dbse, 75 ]
```

### 2: Album recording costs, split and donation
After paying their record label and producer, band members split income from their album up to $1m equally, and give the remainder to charity.

```
---  
name: “Abi's Road”  
rsl: 1.0
description: “Record deal for the band Be At Less”
url: beatless.example.com/deal
pointer: $ilp.example.com/pN3K3rKULNQh
contact: Big Lawyers Inc.
email: big.lawyers@example.com
currency: EUR
decimals: comma
steps:
  -
    type: fixed  
    payee: 
      - [“Orange Records”, ID001, dbse, 5000 ]
      - ["Georgina Martina", producer@example.com, paypal, 5000 ]
  -
    type: percent
    cap: 1000000  
    payee: 
      - [ "Joan", $ilp.example.com/joan, ilp, 25 ]  
      - [ "Paula", 12345678/12-34-56, uk-ac, 25 ]  
      - [ "Georgie", $ilp.example.com/georgie, ilp, 25 ]  
      - [ "Reena", NO 93 8601 1117947, iban, 25 ]
  -
    type: percent
    cap: null
    payee: 
      - [ "Unicef", $ilp.example.org/unicef, ilp, 100 ]
```