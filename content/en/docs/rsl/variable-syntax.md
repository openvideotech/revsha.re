---
title: "Variable Syntax (draft)"
description: "RSL allowing for external variables that are undefined at agreement creation, such as for expenses."
lead: "This would allow for variables defined outside of the agreement to feed into the agreement; such as for costs that aren't known at the time of agreement creation. Still a draft, without working implemntations"
date: 2022-01-12T01:20:13+01:00
lastmod: 2022-01-12T01:20:13+01:00
draft: false
images: []
menu: 
  docs:
    parent: "rsl"
weight: 100
toc: true
---

Variable Syntax uses {{double -curly bracketed values}} in a contract, which will change after a revenue share agreement is first created. For instance annual expenses which must be deducted before profits are shared; or cooperative members when new members are joining all the time. 

As well as allowing for {{double bracketed}} reference points which can be changed after a contract has been generated, this would require further lines to be supported in the YAML:

## Additional variables for a step in the agreement:
- *Endpoint*: A url for the API to resolve the variables used in that step.
- *Key*: If the API endpoint requires a key to access the values.
- payeeTemplate: a generic array for that can resolve as new payees are added. An additional value is used to describe the list containing:
	- {{name_of_group.name}} (e.g. {{worker_owners.name}}, {{user_owners.name}}, {{investors.name}} - would each point to a different lists of payees)
	- {{name_of_group.pointer}}
	- {{name_of_group.payout}} or just N for an equally split percentage share.
	- {{name_of_group.type}}

## Examples

### 3: Filmmaker / website revenue share after streaming costs

A filmmaker allows anyone embedding their film to take 20% of Web Monetization, donations and pay-per-view fees, after the cost of video streaming and a carbon footprint offset, which are split 3:4. 

```
---  
name: “Film distribution share”
rsl: 1.0
description: “Profit share for video embeds”
url: ilp.example.com/name
currency: USD
period: 1 transaction
jurisdiction: California, USA
steps:
  -
    type: ratio
    cap: 0.30
    payee:
      - [ "Streaming costs", $fee.example.com, ilp, 3]
      - [ "Ocean forest restoration", $offset.example.com, ilp, 4]
  -
    type: percent
    endpoint: celiafilm.example.com
    payeeTemplate:
      - [ "Celia Bee Da'mil", $example.com/celia, ilp, 80]
      - [ "{{website}}", "{{pointer}}", ilp, 20]
```

### 4: Filmmaker deferrals and revenue share 

Following on from the above example; when the filmmaker receives income from websites embedding her film, she will first pay back her credit card; then deferred salaries & her expenses; then a profit share with the cast and crew and investors.

```
---  
name: “Film income share”
rsl: 1.0
description: “Profit share for feature film”
url: $example.com/celia
currency: USD
contact: Celia Bee Da'mil
jurisdiction: California, USA
steps:
  - 
    type: fixed
    endpoint: bank.example.com/interest
    payee:
      - [ "Credit Card", $bank.example.com, ilp, 50000]
      - [ "Interest", $bank.example.com,  ilp, "{{interest}}"]
  -
    type: fixed
    endpoint: deferals.example.com/unpaidsalary
    key: 10923m10293mix
    payeeTemplate: 
      - [ "{{deferal.name}}", "{{deferal.pointer}}", "{{deferal.type}}", "{{deferal.amount}}"]
  -
    type: percent
    payee:
      - [ "Lead actor", $ilp.example.com/uche, ilp, 10]
      - [ "Writer", $ilp.example.com/jalāl, ilp, 10]
      - [ "Director", $ilp.example.com/akira, ilp, 10]
      - [ "Composer", $ilp.example.com/clara, ilp, 10]
      - [ "Cinematographer", $ilp.example.com/sven, ilp, 10]
      - [ "Producer", $ilp.example.com/celia-personal, ilp, 25]
      - [ "Investor", $ilp.example.com/investor, ilp, 25]
```

### 5: Filmmaker studio cooperative

A group of filmmakers have setup a film studio cooperative  (with apologies to [United Artists](https://en.wikipedia.org/wiki/United_Artists)). They will take an annual founders bonus, then split the profits after expenses equally. It is worth noting that steps two and three are effectively the same, but with Step 3, the addition of Buster Keaton or Lilian Gish to the list of 'owners' at the specified endpoint would change the payout per owner (marked as N) from 25% to 20%.

```
---  
name: “Artists United”  
rsl: 1.0
description: “Founding agreement for film studio coop”
url: deal.example.com
pointer: $ilp.example.com/pN3K3rKULNQh
currency: USD
period: 1 year
steps:
  -
    type: fixed  
    endpoint: au.example.com/costs
    key: 203984c20934m0c29348
    payee: 
      - [ "Annual expenses", ID002, dbse, "{{costs}}" ]
  -
    type: percent
    cap: 1000000
    description: bonus for the studio founders
    payee: 
      - [ "Chaplin", $payee.example.com/charles, ilp, 25]
      - [ "Pickford", $payee.example.com/mary, ilp, 25]
      - [ "Griffith", $payee.example.com/melanie, ilp, 25]
      - [ "Fairbanks", $payee.example.com/douglass, ilp, 25]
  -
    type: percent
    endpoint: au.example.com/owners
    payeeTemplate: 
      - [ {{owners.name}}, {{owners.pointer}}, ilp, N ]
```

### 6: Coding camps in refugee camps

A charity helps developers give coding lessons in refugee camps around the world, and sells the apps and games created. Each student developer gets a fee per sale; what's left is split between the charity and all developers for that year.

```
---  
name: “Dev Camp”  
rsl: 1.0
description: “Profit share for trainee developers”
currency: JPY
decimals: none
period: 1 transaction
steps:
  - 
    type: fixed
    endpoint: transactions.example.com/developers
    payeeTemplate:
      - [ "{{developer.name}}", "{{pointer}}", ilp, 1000]
  -
    type: percent
    cap: null
    endpoint: devcamp.example.org/all_developers
    payeeTemplate:
      - [ "Charity", $ilp.example.org/devcamp, ilp, 50]
      - [ "{{all_developers.name}}", "{{all_developers.name}}", ilp, N]
```