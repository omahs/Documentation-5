---
description: devDAO guide to set up automated e2e testing with Kwenta
---

# Testing

### Introduction

Automated end-2-end (e2e) testing for functional scenarios of the Kwenta dApp is essential for detecting regressions in functionality after updates. To reduce technical debt, the devDAO is assisting the [Core Contributors](../../dao-roles/core-contributors.md) in developing an e2e testing framework for the Kwenta dApp.

### Current Status

At the moment, two e2e test for UI features are available:

* Wallet login: `login-spec.js`
* Exchang`: trade-spec.js`

Bounty hunters of the devDAO are currently working on improving and adding additional e2e tests for all other major UI features. If you're interested in helping out, don't be shy to drop a line in the `#community-dev` channel on our [Discord](https://discord.gg)!

### How-to: End-2-end testing guidance

In order to run fully automated e2e tests Kwenta uses [Synpress](https://github.com/Synthetixio/synpress) (a wrapper around [Cynpress](https://www.cypress.io)).

#### Constraints

The current e2e tests are written to be run on **Optimistic Kovan** using **Chrome** as the browser.

#### Setup

* Download and install Google Chrome
* Setup a testing wallet on Optimistic Kovan and fund it with plenty of kETH (to pay for gas) and sUSD
* Copy the private key of the wallet into the file `TEST-PRIVATEKEY` into the repository folder `/tests/e2e/`
* Before proceeding to the next step you need to setup environment variables. Navigate to the folder`/tests/e2e` and run the following command:\
  \
  &#x20;`source ./RUN-WITH-SOURCE-synpress-env-KovanOE.sh`

{% hint style="success" %}
Contact the community PM on Discord if you're working on a ticket and are looking for kETH and Kovan sUSD for testing purposes.
{% endhint %}

### Run the tests

````
```bash
npm run build
npm start
npm run test:e2e:only:tests
```
````

