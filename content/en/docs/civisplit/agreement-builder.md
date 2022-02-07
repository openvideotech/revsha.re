---
title: "Agreement Builder"
description: "CiviSplit Agreement Builder"
lead: ""
date: 2022-02-05T01:20:13+01:00
lastmod: 2022-02-05T01:20:13+01:00
draft: false
images: []
menu: 
  docs:
    parent: "civisplit"
weight: 35
toc: true
---

This CiviCRM extension is built around [Cascade](/docs/cascade/intro/), a Javascript [Revenue Sharing Language](/docs/rsl/intro/) drag-and-drop builder. 

Agreements can either be in **draft state**, allowing edits, or **generated**. Once an agreement is 'generated' it can't be edited and if running with the Uphold extension then a sub-account will have been created with a Payment Pointer returned.

## Dashboard

The main CiviSPlit dashboard (`/civicrm/agreement-builder/index`) contains a list of your draft, generated and running agreements. From here you can:
 - edit agreements (if still in draft), 
 - view agreements in a shareable form 
 - view a report of payments

## Agreement creation

As well as some general data (currency, payment pointer, start/end date, etc), agreements are based on a series of **steps**, with each step paying out to one or more **payees**. As you create the agreement you will see the Revenue Sharing Language YAML output appear at the bottom of the page - or if there are errors in your agreement an appropriate message/instruction.

The only required fields are *Name* for the agreement and *Currency*. You can optional select if you are using comma (',') or period ('.') notation for decimal places in the numbers you enter. You should leave the *Payment address* field blank, unless you have an existing [Payment Pointer](https://paymentpointers.org) you want to use for this agreement.

### Steps
A step can be either:
 - **fixed**, meaning every payee at that step gets paid a fixed amount.
 - **percentage**, meaning every payee at that step gets paid pro-rata.
 - **ratio**, the same as percentage, but handles percentages with recurring decimals. So a one-third/two-thirds split is better expressed as a 1-2 ratio, than 33%/66% because no matter how many decimal places are used there will always be a remainder.

**Caps**

Any percentage or ratio step can have a cap which is a limit forcing a trigger onto the next step. If you don't set a cap, then percentage/ratio payouts will run forever.

**Pari Passu**

Fixed payments are paid out 'Pari Passu' which means all parties are paid the same amount at the same time. So if Anja and Björn are owed $20 and $10, and $20 is to be shared out - both will be paid equally, ie $10 each.

If you want to repay fixed amounts pro-rata (ie in the above example paying Anja twice as much as Björn until both parties are fully repaid), then you should use a percentage split with a Cap. So you would set a cap of $30 and a ratio of Anja 2; Björn 1.

### Payees

**First create CiviCRM contact records**

Payees need to be CiviCRM Contacts, so before creating an agreement you should have added contact records for each of your payees (ie via `/civicrm/contact/add?reset=1&ct=Individual` or `/civicrm/contact/add?reset=1&ct=Organization`).  Contacts only need to have a name, and if you are using the Uphold extenion, a payment address. 

On installing the extension a new custom field 'Uphold Desintation Address' will have been added to contact screens, where you can add the Uphold payee address. 

If you store an email address or phone number with each contact, you could automate notifications on payout with further configuration. 

**Associating a CiviCRM contact**

After clicking 'add payee' jump to the second field 'Payment Address' and begin typing in the name of your saved Contact. A list of possible contacts should appear. Click return to select the right one.

In the fourth box you need to enter a number for the fixed, percentage or ratio split. Don't add any other characters here beyond a , or . to denote any decimals.

You can also overwrite the name in the first box - which you could use to leave a note.

## Generating

You can save your agreement at any point to return to it and make changes. When you are happy with it, click 'Generate final agreement' and you will be warned that 'you will no longer be able to make edits to this agreement'. Click ok.

### Standard generation

Does several things:
 - Makes the agreement uneditable, removing the edit buttons.
 - Generates a SHA hash of the RSL agreement which protects against anyone changing the payout agreement once it's been generated.
 - Allows you to view the agreement, via a link in the dashboard.

 ### Uphold generation
  If you are using the Uphold extension, Generating will also:
 - if you have entered a Payment Pointer it will search for a matching Payment Pointer in your Uphold account and save the associated Card  (aka a sub-account) ID.
 - if you don't have a Payment Pointer, it will create a new Card in Uphold and return the Payment Pointer and Card ID. You can then use this Payment Pointer to collect income, for instance with Web Monetization header embeds.

