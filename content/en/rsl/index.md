---
title: "Revenue Sharing Language (RSL)"
description: ""
lead: "Revenue Sharing Language (RSL) is a human and machine readable language for describing complex multiple-step revenue-sharing agreements between multiple parties."
date: 2022-01-12T01:16:28+01:00
lastmod: 2022-01-12T01:16:28+01:00
draft: false
images: []
---

{{< alert icon="👉" text="Nothing written here or on this website is a replacement for legal or financial advice. Use of these tools and ideas is at your own risk." />}}

Revenue Sharing Language (RSL) is inspired by Ian Grigg's idea of a [Ricardian Contract](https://en.wikipedia.org/wiki/Ricardian_contract), which is a machine- and human- readable agreement. A Ricardian Contract for revenue sharing has the advantages of potentially reducing human error, mispayments, delays or 'creative adjustments' when an agreement is paid out. So RSL is proposed as a common set of instructions that can be generated and processed when creating multi-step recoupment and profit-share agreements. 

One of the main benefits of a human and machine readable contract is that a cryptographic [SHA hash](https://en.wikipedia.org/wiki/SHA-1) can be generated from it, which would alter if the agreement changes. This can act as a check against changes - or 'Hollywood accounting'. In this way, a system using the machine instructions from such a contract as the basis for royalty or revenue-share payouts can be sure that it's the same agreement as the one originally agreed to. But this is why machine-readable isn't sufficient - non-developer humans should be able to read the agreement and understand its principles. For this reason [YAML](https://yaml.org/) was chosen over JSON because while it has limitations, it is more easily readable by non-developers.

RSL forms the basis of the Javascript libraries Cascade, Waterfall and the CiviCRM extension suite for Backdrop, Drupal, Joomla! and WordPress, CiviSplit.

The syntax has two levels:
 - **a Standard Syntax**, to describe a potentially unlimited series of steps of fixed, percentage or ratio splits, which can loop by both time period or per transaction. This has been implemented in three projects.
 - **an expeerimental Variable Syntax**, still a draft, and not yet implemented, which allows for variables defined elsewhere, for instance an external value for expenses, that allows to exist between certain levels.

[Read documentation](/docs/rsl/standard-syntax/)

