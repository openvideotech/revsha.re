---
title: "About Revenue Share"
description: "Who and what is this?"
lead: "RevenueSha.re is an OpenVideo.tech project trying to make it easier for creatives, non-profits and other collaborators to easily and safely create revenue-sharing plans for little/no cost."
date: 2020-08-27T19:23:18+02:00
lastmod: 2020-08-27T19:23:18+02:00
draft: false
images: []
---

We do this thru three layers:
 - **[Revenue Sharing Language (RSL):](https://github.com/openvideotech/rsl)** a new YAML-subtytpe syntax to describe Revenue Sharing plans in a human and machine readable way.
 - **[Cascade:](https://github.com/openvideotech/cascade-svelte)** a drag and drop interface to create RSL agreements. There are both framework-free [native-JS](https://github.com/openvideotech/cascade-native) and a [Svelte-JS](https://github.com/openvideotech/cascade-svelte) version.
 - **[CiviSplit:](https://lab.openvideo.tech/civisplit)** a suite of three CiviCRM extensions to save, process and payout RSL agreements:
    - *[Agreement Builder](https://lab.openvideo.tech/civisplit/agreement-builder)* integrates Cascade, with save/edit, Civi contact lookup, reporting, viewing and fixing agreements. 
    - *[Processor](https://lab.openvideo.tech/civisplit/processor)* calculates who is owed what, and could be used for manual entry and integration with other systems/extensions. 
    - *Uphold* is the payment processor integration with Uphold to create a dedicated payee account, generate a custom ILP address, check balances and make payouts to payees. 

You can see these in action below in a presentation, by Matthew Wire taken from the December 2021 [Grant for the Web skillshare](https://community.webmonetization.org/grantfortheweb/join-us-december-15th-grant-for-the-web-skill-share-with-awardee-nic-wistreich-of-mova-dlg):

{{< vimeo id="667763569" title="Demo of CiviSplit" >}}

## What exactly does CiviSplit do?
1. **Setup multi-step pro-rata & pari-passu revenue sharing…** <br />Supporting a succession of fixed and percentage payouts from a specific payee address.
2. **Store agreements in a human and machine readable syntax…** <br />Revenue Sharing Language (RSL) is a YAML-subtype describing multi-step, multi-payee revenue plans.
3. **Create with a drag-and-drop user-friendly Javascript app…** <br />RSL agreements are built through an intuitive builder, Cascade, available in native-JS and Svelte.js.
4. **Generate agreements with SHA-hash signature to prevent future changes…**<br />RSL agreements form the basis for payouts, so once securely hashed prevent future changes.
5. **Collect income for each agreeement at a dedicated sub-account with its own Payment Pointer** <br />Each agreement has it's own sub-account and payment address (Uphold only).
6. **Calculate, make, track and report on payouts in CiviCRM...** <br />CiviCRM (available for over ½ of world's websites) extensions manage agreements, payees and payments with notifications and reporting.

## Team

- [Rich Lott, Artful Robot](https://artfulrobot.uk): Initial Cascade Svelt JS Build, all unit tests, developer & structural input.
- [Matthew Wire, MJW Consulting](https://www.mjwconsult.co.uk/en/): CiviSplit extensions build and architecture.
- [Nicol Wistreich, Netribution Ltd](https://netribution.org): Project lead, RSL author and designer.

*With…*

- [Mark Boas](https://maboas.co): Initial Cascade Standalone JS Build.
- [Silvia Schmidt](https://silviaschmidt.org/): Film and legal advice.

And thanks to [Dave Boyle](https://communityshares.co.uk/about-us-dave-boyle/) of the Community Shares Unit and [Aidan Saunders](http://www.squiffle.uk/) for their input.

## Links

- [matter.openvide.tech](https://matter.openvide.tech) – Mattermost chat space
- [lab.openvideo.tech](https://lab.openvideo.tech/civisplit) – Gitlab & issues
- [github.com/openvideotech](https://github.com/openvideotech) – Github
