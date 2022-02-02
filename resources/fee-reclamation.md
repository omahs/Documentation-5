# Fee Reclamation



### Fee Reclamation and Rebates

[SIP-37](https://sips.synthetix.io/sips/sip-37) introduced fee reclamation and rebates. These are intended to prevent traders from front-running the latency of Ethereum block processing on Ethereum (L1).&#x20;

{% hint style="info" %}
Fee reclamation and rebates **only apply to Ethereum Mainnet** (L1). Trades on Optimism Layer 2 are not affected by SIP-37.
{% endhint %}

Synthetic assets traded on Kwenta need regular price updates on-chain. More frequent price updates require a substantial amount of gas. When a change occurs in price it must be updated on-chain. The delay between real-time prices and the new price being confirmed in an oracle update (price pushed on-chain) is known as oracle latency. Fee reclamation provides a complex yet needed solution.

For trades executed on L1 Kwenta, there is a waiting period of 6 minutes. During this window of time, users cannot exchange, transfer, or burn the synth they have just traded into. This waiting period gives the oracles enough time to check the difference between the initial price and the new price - in other words, they check to see if a trade was affected by a lag in price updates.\
\
If a trade was affected by fee reclamation, they either owe synths (reclamation) or are owed synths (rebate), and must either pay or be paid these synths. The next time the user exchanges or burns that synth, the `settle` function is automatically called, which settles this debt.&#x20;

{% hint style="danger" %}
The max queue of reclamations per wallet per synthetic asset is 12. Once 12 reclamations are queued without the user settling any fee reclamations, the system will disallow the 13th attempt until traders call the `settle` function.
{% endhint %}
