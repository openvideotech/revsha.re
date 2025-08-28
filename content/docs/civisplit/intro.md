---
title: "Intro"
description: "CiviSplit is a collection of three CiviCRM extensions to generate, store and process income-sharing agreements, using Revenue Sharing Language (RSL)"
lead: "CiviSplit is a collection of three CiviCRM extensions to generate, store and process income-sharing agreements, using Revenue Sharing Language."
date: 2022-01-12T01:20:13+01:00
lastmod: 2022-01-12T01:20:13+01:00
draft: false
images: []
menu:
  docs:
    parent: "civisplit"
weight: 11
identifier: civisplit-intro
toc: true
---

[Revenue Sharing Language (RSL)](/docs/rsl/) agreements are implemented across three CiviCRM extensions:
 - **CiviSplit Agreement Builder** - extension to create, save and generate income sharing agreements.
 - **CiviSplit Processor** - extension to calculate and process amounts owed to different payees.
 - **CiviSplit Uphold Payments** – a payment processor to create sub-accounts in [Uphold.com](https://uphold.com), check balances for them and make payouts to IBAN bank accounts (requires an Uphold API key).

 {{< callout icon="outline/info-circle" text="Why Uphold?" >}}
 **Why Uphold?** It's one of only two payment processors at present to have implemented ILP [Payment Pointers](https://paymentpointers.org) and sub-accounts for ringfenced income receipts (the other is Gatehub). Uphold is the only one with a sufficient third party API
 {{< /callout >}}
