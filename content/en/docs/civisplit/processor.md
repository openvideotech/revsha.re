---
title: "Processor"
description: "CiviSplit Processor"
lead: ""
date: 2022-01-12T01:20:13+01:00
lastmod: 2022-01-12T01:20:13+01:00
draft: false
images: []
menu: 
  docs:
    parent: "civisplit"
weight: 40
toc: true
---

The Processor extension's job is to process income in, calculate who is owed what, and track these payments and doesn't have a user interface. It's used with the Uphold extension to process balances so wouldn't normally be used directly.

However it's possible to use Processor with manually entered or offline income, ie for payment and accounting systems that don't integrate with CiviCRM/CiviSPlit. This is also a way to test and preview complex agreements.

## Using Processor for manual income handling

This uses API3. 
 - Go to `/civicrm/api3` (in menu Support > Developer > API3).
 - Under Entity, select 'CiviSplit'
 - Under Action, select 'fundsavailable'
 - This brings up a new select list. Click 'Add Parameter' and select Agreement Hash. 
 - Set this to the hash for your agreement, which you can find on the dashboard -> view
 - Next to Amount Available enter the amount of income you wish to process.
 - Now when you go back to the Dashboard and click Report you should see the income you've just provided in an updated report.

