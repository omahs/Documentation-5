---
description: devDAO guide to set up automated e2e testing with Kwenta
---

# Testing

### Introduction

Automated end-2-end (e2e) testing for functional scenarios of the Kwenta dApp is essential for detecting regressions in functionality after updates. To reduce technical debt, the devDAO is assisting the [Core Contributors](../../dao-roles/core-contributors.md) in developing an e2e testing framework for the Kwenta dApp.

### Current Status

At the moment, two e2e test for UI features are available:

* Wallet login: `login-spec.js`
* Exchange: `trade-spec.js`

Bounty hunters of the devDAO are currently working on improving and adding additional e2e tests for all other major UI features. If you're interested in helping out, don't be shy to drop a line in the `#community-dev` channel on our [Discord](https://discord.gg)!

### How-to: End-2-end testing guidance

In order to run fully automated end-2-end (e2e) tests Kwenta uses [Synpress](https://github.com/Synthetixio/synpress) (a wrapper around [Cynpress](https://www.cypress.io)).

{% hint style="success" %}
Contact the community PM on Discord if you're working on a ticket and are looking for kETH and Kovan sUSD for testing purposes.
{% endhint %}

#### **Constraints**

The current e2e tests are written to be run on Optimistic Kovan using Chrome as the browser.

#### **Setup**

* Download and install Google Chrome
* Setup a test wallet on Optimistic Kovan and fund it with plenty of ETH (to pay for gas) and sUSD
* Prior to running the tests you must set the environment variables below in the shell from which npm is started. Unfortunately, at this time other methods to set said environment variables (eg. through `.env.local`) don't work in conjunction with Synpress.

```bash
PRIVATE_KEY=<INSERTPRIVATEKEY>
NETWORK_NAME=OptimisticKovan
RPC_URL=https://kovan.optimism.io
CHAIN_ID=69
BLOCK_EXPLORER=https://kovan-optimistic.etherscan.io
IS_TESTNET=true
```

#### **Bash convenience script for setting up the environment**

A Bash convenience script [has been made available here](https://gist.github.com/raffiegang/b24a6b97bcd054645abf59be852bc88d).

* Open bash
* Copy the private key of the test wallet into the file `SYNPRESS_PRIVATEKEY` into the same folder location as the script. While using this method, please don't forget to update your .gitignore file to prevent your private key to be leaked.
* Run the following command `source ./synpress-envsetter.sh`

#### Run the tests

```bash
npm run build
npm start
npm run test:e2e:only:tests
```

