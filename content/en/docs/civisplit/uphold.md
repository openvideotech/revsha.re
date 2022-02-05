---
title: "Uphold"
description: "CiviSplit Uphold"
lead: ""
date: 2022-02-05T01:20:13+01:00
lastmod: 2022-02-05T01:20:13+01:00
draft: false
images: []
menu: 
  docs:
    parent: "civisplit"
weight: 30
toc: true
---

## Current Uphold integrations
The CiviSplit Uphold extension handles several integration functions with Uphold:
- create a new sub-account for each [RSL](/docs/rsl/intro/) agreement (Uphold calls these sub-accounts Cards)
- return an ILP address (aka [payment pointer](https://paymentpointers.org)) for that Card/Agreement. 
- if you already have an ILP address for an Uphold Card, you can enter this in the RSL and it should find the correct card ID
- check the current balance
- **Coming April 2022:** make payouts to Uphold users, based on a user ID saved in the Civi contact record (see below).

## Get an Uphold API key

Firstly you need to get an Uphold API key, which is available by signing up [here](https://uphold.com/en-eu/get-started/developer). This requires quite extensive Know Your Customer (KYC) checks, so allow good time to prepare the requried doumentation and wait up to several weeks for the account to be approved. 

## Setup a new Payment Processor

Once you have enabled the Uphold extension, go to `/civicrm/admin/paymentProcessor?reset=1` in Drupal (or Administrator > System Settings > Payment Processors) and click 'add Payment Processor'.

- Under Payment Processor Type, select 'Uphold'.
- Under Payment Processor, give a name, ie 'Uphold'.
- You can leave Processor Title and Description blank unless you want to manage multiple Uphold API keys/accounts.
- Leave the other settings as they are
- Under 'Processor Details for Live Payments' you can add your API ID and secret. Enter `https://wallet.uphold.com` for Site URL.
- Under 'Processor Details for Test Payments' you can add the API ID and secret for the sandbox. Enter `https://wallet-sandbox.uphold.com` for Site URL
- Click save.

**Check it works:** in the CiviSplit menu there is a link 'Uphold API diagnositics' (`/civicrm/admin/civisplituphold/diagnostics`). If youre API keys are working correctly you see something here, otherwise it will be blank. 

## Save a Uphold Payment Address for each user

On installing the extension, a new custom field set will appear on every user's contact record 'CiviSplit Uphold'. If you expand this, there is a field 'Uphold Destination Address' where you can add the ID for any registered Uphold user to receive income.

We're expecting this ID can be in the form of an ILP payment pointer, a crypto wallet address, an email address, an account id, an application id, or a card id (which would allow payouts between multiple agreements).

{{< alert icon="⚠️" text="<strong>Uphold fees:</strong> Uphold charges usage fees of 3% on all transactions - if you are a non-profit looking to register an API key - please get in touch at support@revenuesha.re as we may be able to help you get fee-free access for 12-24 months." />}}


