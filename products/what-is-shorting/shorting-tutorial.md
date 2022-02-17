---
description: A step-by-step guide to Shorting on Kwenta
---

# Shorting Tutorial

## How to trade shorts on Kwenta

{% hint style="warning" %}
Make sure you have sufficient ETH in your L2 wallet to pay for on-chain gas costs
{% endhint %}

This tutorial guides you through the Kwenta interface for shorting synthetic assets. At the end of this guide, you will have successfully shorted sUSD on Kwenta, managed your collateral, and paid back your loan.

This guide runs the reader through the Kwenta Shorting mechanism on [Optimism Layer 2](../../onboard/how-to-start-using-kwenta/getting-started-on-optimistic-ethereum.md#getting-started-with-optimism).

### How to set up a short position on Kwenta

![Kwenta Shorting Dashboard](../../.gitbook/assets/shorting\_dashboard.png)

On Kwenta, navigate to the **Shorting** dashboard. Make yourself familiar with the interface and the information provided. This tutorial focuses on the trading interface.&#x20;

In our example, we wish to short 500 sUSD out of our 1000 sUSD balance against sLINK.&#x20;

![Kwenta Shorting Input](../../.gitbook/assets/shorting\_select\_assets.png)

1. Click on **sETH** and select the asset you wish to short, in our example **sLINK**.
2. Once sLINK has been selected, choose the amount of sUSD to short. In our example, 500 sUSD.
3. Select your preferred [C-Ratio](./). In our example, we play it safe at 200%.
4. Make yourself familiar with the gas price and transaction fees.
5. Click **Approve** to give the [shorting contract](../../resources/smart-contracts.md) permission to access your sUSD. You have to do this only once, independent of the synth you wish to short.
6. Once the transaction is confirmed, click **Submit order**.
7. Verify all data in the confirmation window. If you are satisfied with what you see, confirm the transaction with your web3 wallet.
8. Wait a few seconds and the new position will show up on your Shorting dashboard!

![Shorting Position Overview](../../.gitbook/assets/shorting\_position\_slink.png)

### How to manage your position

After opening a short position, traders should regularly monitor their c-ratio. If the c-ratio falls below 120%, the position will be at risk of liquidation.

In order to manage an open position, traders can click on the :pencil2: symbol to the right of their position.

![Manage a Shorting position](../../.gitbook/assets/shorting\_manage\_slink.png)

Traders now can execute one of the following five options according to their trading strategy:

* Add Collateral
* Remove Collateral
* Increase Position
* Decrease Position
* Close Position

In order to close a position, click the **Close Position** tab and verify the amount to be repaid. Click the final Close Position button and confirm the transaction.&#x20;

![Shorting: Close a position to repay your loan](../../.gitbook/assets/shorting\_close\_slink.png)

Congratulations, you successfully shorted synthetic assets with Kwenta!
