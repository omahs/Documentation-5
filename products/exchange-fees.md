---
description: Kwenta fees explained.
---

# Fee Structure

Kwenta is built upon the Synthetix Protocol. In order to enable the exchange of synthetic assets, an [exchange fee](exchange-fees.md#exchange-fees) is charged by Synthetix whose fees are sent to the fee pool for Synthetix (SNX) stakers to claim.

In addition to the exchange fee, a [dynamic fee](exchange-fees.md#dynamic-fees) is in place which kicks in during times of high market volatility in order to neutralize front-running opportunities and protect stakers.

A [proposal is being drafted](exchange-fees.md#integration-of-source-fee) for Kwenta to receive a rebate on fees, allowing Kwenta to be cash-flow positive in the future.

Post-launch, Kwenta is planning on introducing native fees for new product offers, e.g. mixed marked products, advanced orders, etc. Possible future platform fees are in development and need to be voted on once proposed (see [Governance Framework](../dao/governance-framework.md)). If you are a trader interested in participating and shaping the decentralized governance and future of Kwenta, please join our [Discord](https://discord.gg/kwenta)!

### Exchange Fees

Exchange fees are charged when a trader exchanges one synthetic asset (synth) for another through the Kwenta platform. Exchange fees are set to **25 bps** (0.25%) on Optimism Layer 2 and between 20 and 50 bps (0.2-0.5%) on Ethereum Layer 1. These fees are sent to the fee pool, where they are available to be claimed by SNX stakers each week.

Exchange fees may vary depending on a selected market & network. The most current fees are prominently displayed within the Kwenta trading platform while trading.

{% hint style="info" %}
Basis Points (BPS) are a unit of measurement equal to 1/100th of 1 percent commonly used in financial markets.
{% endhint %}

| Percentage | .bps   |
| ---------- | ------ |
| 0.01%      | 1 bps  |
| 0.40%      | 40 bps |

### Dynamic Fees

Dynamic exchange fees are additional fees paid by traders under volatile market conditions that neutralize front-running opportunities and protect stakers.

During periods of high volatility in the crypto markets, a dynamic fee will be levied upon trades to ensure that there are no front-running opportunities present for traders. Once market volatility subsidies, the dynamic exchange fee reverts to zero.

Dynamic fees will be prominently displayed on Kwenta once levied (see example image below).

![Example Display of Dynamic Fees on Kwenta](../.gitbook/assets/dynamic\_fees.png)

#### Technical explanation on how dynamic fees work

During times of price instability, the dynamic fee is incremented higher according to observed volatility. So as volatility builds, it will accumulate in the dynamic fee. It also has a built-in decay factor, meaning that the dynamic fee will decay exponentially over time when volatility subsides.

At the beginning of each epoch, a dynamic fee gauge contract measures the asset [oracle](../resources/oracles.md) price change between epochs. If this difference is more than twice the prescribed deviation threshold (minimum frontrunnable threshold), the dynamic fee is increased by the size of the differential.

In the subsequent epoch, the dynamic fee is reduced by a decay factor but again subject to additional boosting if price movement between epochs exceeds prescribed thresholds.

{% hint style="info" %}
For more technical information about dynamic exchange fees, refer directly to the [SIP-184](https://sips.synthetix.io/sips/sip-184/).&#x20;
{% endhint %}

### Future Developments

#### Integration of Volume Source Fee

A current Synthetix Improvement Proposal draft ([SIP-203](https://sips.synthetix.io/sips/sip-203/)) outlines a possible split of the exchange fee into a Protocol Fee and Source Fee. By integrating a sourcing fee, it would give Kwenta stakers access to a percentage of the fees generated on the Kwenta platform while simultaneously generating a stable income. For more information, see our [Volume Source Fee](../tokenomics/volume-source-fee.md) article.
