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
weight: 30
toc: true
---

## Install CiviCRM for your CMS (if you haven't already)
After installing a CMS following the instructions on their site, you will need to download and install the appropriate CiviCRM build for your CMS from [civicrm.org/download](https://civicrm.org/download) using the following instructions:
- Backdrop - [docs.civicrm.org/installation/backdrop](https://docs.civicrm.org/installation/en/latest/backdrop/)
- Drupal 7.x - [docs.civicrm.org/installation/drupal7](https://docs.civicrm.org/installation/en/latest/drupal7/)
- Drupal 8/9.x - [docs.civicrm.org/installation/drupal8](https://docs.civicrm.org/installation/en/latest/drupal8/)
- Joomla - [docs.civicrm.org/installation/joomla](https://docs.civicrm.org/installation/en/latest/joomla/)
- WordPress - [docs.civicrm.org/installation/wordpress](https://docs.civicrm.org/installation/en/latest/wordpress/)

### Important note
CiviCRM is a large multi-function CRM with higher server requirements than many hosts offer, and a slower upgrade process than many CMS extensions. Picture that you're installing volunteer-built version of Salesforce onto your website.

## Install the extensions
Manually download and install the following three extensions, using the CiviCRM [extensions installer guide](https://docs.civicrm.org/sysadmin/en/latest/customize/extensions/#installing-a-new-extension) for manual installation (the location of the extensions folder willl vary with each CMS)
 - CiviSplit Agreement builder
 - CiviSplit Processor
 - CiviSplit Uphold Payments

After installing, enable each extension.

{{< alert icon="⚠️" text="<strong>Important note:</strong> Self-hosting is at your own risk. As specified in the AGPL, we are not liable or responsible for any issues you have with the software, make no guarantees of suitability or fitness for purpose, and are under no obligation to fix or maintain the software in the future." />}}


