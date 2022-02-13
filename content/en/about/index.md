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
 - **Revenue Sharing Language (RSL):** a new YAML-subtytpe syntax to describe Revenue Sharing agreements in a human and machine readable way.
 - **Cascade:** a drag and drop interface to create RSL agreements. There are both framework-free native-JS and a Svelte-JS version.
 - **CiviSplit:** a suite of three CiviCRM extensions to save, process and payout RSL agreements:
    - *Agreement Builder* integrates Cascade, with save/edit, Civi contact lookup, reporting, viewing and fixing agreements. 
    - *Processor* calculates who is owed what, and could be used for manual entry and integration with other systems/extensions. 
    - *Uphold* is the payment processor integration with Uphold to create a dedicated payee account, generate a custom ILP address, check balances and make payouts to payees. 

You can see these in action below in a presentation, by Matthew Wire:

{{< vimeo id="667763569" title="Demo of CiviSplit" >}}

## In other words
1. **Multi-step pro-rata & pari-passu revenue sharing…** <br />Supporting a succession of fixed and percentage payouts from a specific payee address.
2. **Agreements stored in a human and machine readable syntax…** <br />Revenue Sharing Language (RSL) is a YAML-subtype describing multi-step, multi-payee revenue plans.
3. **Created through a drag-and-drop user-friendly Javascript app…** <br />RSL agreements are built through an intuitive builder, Cascade, available as native-JS and Svelte.js.
4. **Stored with its SHA-hash signature to prevent future changes…**<br />RSL agreements form the basis for payouts, so once securely hashed prevent future changes.
5. **Collecting income at a unique sub-account/ILP for the agreement…** <br />Each agreement has it's own sub-account and payment address (Uphold only).
6. **To calculate & make payouts in CiviCRM...** <br />CiviCRM (available for over ½ of world's websites) extensions manage agreements, payees and payments with notifications and reporting.

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
- [lab.openvideo.tech](https://gitlab.openvideo.tech) – Gitlab, codebase & issues
