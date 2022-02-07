---
title: "Installation"
description: "How to install CiviCRM & CiviSplit"
lead: ""
date: 2022-01-12T01:20:13+01:00
lastmod: 2022-01-12T01:20:13+01:00
draft: false
images: []
menu: 
  docs:
    parent: "civisplit"
weight: 25
toc: true
---

## Install CiviCRM for your CMS (if you haven't already)
After installing a CMS following their instructions, you will need to download and install the appropriate CiviCRM build for your CMS from [civicrm.org/download](https://civicrm.org/download) using the following instructions:
- Backdrop - [docs.civicrm.org/installation/backdrop](https://docs.civicrm.org/installation/en/latest/backdrop/)
- Drupal 7.x - [docs.civicrm.org/installation/drupal7](https://docs.civicrm.org/installation/en/latest/drupal7/)
- Drupal 8/9.x - [docs.civicrm.org/installation/drupal8](https://docs.civicrm.org/installation/en/latest/drupal8/)
- Joomla - [docs.civicrm.org/installation/joomla](https://docs.civicrm.org/installation/en/latest/joomla/)
- WordPress - [docs.civicrm.org/installation/wordpress](https://docs.civicrm.org/installation/en/latest/wordpress/)

### Important note
CiviCRM is a large multi-function CRM with higher server requirements than many hosts offer, and a slower upgrade process than most CMS extensions. CRMs are much bigger and more demanding than CMSs - and require time and technical confidence to setup and maintain (although you don't need to be a coder). If you don't feel confident, you could contact one of the CiviCRM partners listed [here](https://civicrm.org/experts).

## Install the extensions
Manually download and install the following three extensions, using the CiviCRM [extensions installer guide](https://docs.civicrm.org/sysadmin/en/latest/customize/extensions/#installing-a-new-extension) for manual installation (the location of the extensions folder willl vary with each CMS).

The extensions separate the functionality - if you just want to build and save agreements you only need Agreement Builder. If you want to handle payouts maually you should be able to install just Agreement Builder and Processor. However most testing has been done with all three extensions running, so that's the recommended setup.

### CiviSplit Agreement Builder
Minimum extension required to generate and save RSL agreements. Download from [lab.openvideo.tech/civisplit/agreement-builder](https://lab.openvideo.tech/civisplit/agreement-builder). If you only want to create, save and share RSL agreements you can do this with just the Agreement Builder.

### CiviSplit Processor
Required in addition to calculate payouts (for offline payment): [lab.openvideo.tech/civisplit/processor](https://lab.openvideo.tech/civisplit/processor)

### CiviSplit Uphold Payments
Required in addition to process payouts and get a balance from Uphold: [lab.openvideo.tech/civisplit/uphold](https://lab.openvideo.tech/civisplit/uphold)

 
## After installation

After enabling the extensions, if everything is successful, there will be a new menu in your main CiviCRM menu bar: CiviSplit.

{{< alert icon="⚠️" text="<strong>Important note:</strong> Self-hosting is at your own risk. As specified in the AGPL, we are not liable or responsible for any issues you have with the software, make no guarantees of suitability or fitness for purpose, and are under no obligation to fix or maintain the software in the future." />}}
