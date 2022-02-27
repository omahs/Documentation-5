---
description: Discover the Shorting mechanism on Kwenta
---

# Shorting

## Shorting

{% hint style="success" %}
Shorting allows traders to short synthetic assets against sUSD.
{% endhint %}

In traditional markets, assets can be borrowed and sold short to gain inverse price exposure. The borrower is legally obligated to repurchase the asset in the future and return it. With the introduction of fixed debt loans in Synthetix, a shorting mechanism can be provided which relies on overcollateralization in the absence of legal enforcement. By depositing sUSD collateral, traders can borrow and short sell synthetic assets (synths). To retrieve their collateral, they must repurchase the borrowed synth and return it.

This mechanism provides an alternative to traders seeking inverse price exposure. While these positions require collateral, they return the sUSD proceeds of the sale to the shorter, which can then be deployed productively throughout DeFi.

{% hint style="warning" %}
Shorting is only available on **Optimism Layer 2.**
{% endhint %}

{% content-ref url="shorting-tutorial.md" %}
[shorting-tutorial.md](shorting-tutorial.md)
{% endcontent-ref %}

### Example of the mechanism

Essentially, shorts are fixed debt, over-collaterised loans using [sUSD](../../onboard/how-to-start-using-kwenta/why-susd/#why-do-i-need-susd) as collateral.&#x20;

In order to open a short position, the trader deposits sUSD and can select the respective synth they wish to short. All positions have a collateralisation requirement. For example:&#x20;

* Trader deposits 10.000 sUSD and elects to short 10 sETH
* A loan is created for the value of 10 sETH.
* The trader is issued 5000 sUSD.
* To reclaim the 10.000 sUSD, the trader must return 10 sETH to the contract.&#x20;

{% hint style="info" %}
For a more in-depth specification, please see [SIP-103](https://sips.synthetix.io/sips/sip-103).
{% endhint %}

