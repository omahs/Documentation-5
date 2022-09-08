---
description: Frequently Asked Questions
---

# FAQ

#### Where does the liquidity come from?

Kwenta is built on the Synthetix protocol, so the liquidity traders can access on Kwenta is entirely created by SNX stakers on Synthetix.

#### How does trading work if there are no counterparts?

There are no direct counterparties for each trade in the Synthetix protocol, but it does use a counterparty-like model in which SNX stakers assume a proportion of the Synthetix debt pool when they mint sUSD. For more details, see the Synthetix [litepaper](https://docs.synthetix.io/litepaper/).

#### Why Layer 2 Optimism?

To aid us in scaling on-chain derivatives trading, Kwenta is built on Layer 2 Optimism for isolated perpetual futures, utilizing Synthetix smart contracts. Traders can expect significantly lower gas costs, and in turn, much lower trading fees and minimum trade sizes.

Optimism is an "Optimistic Rollup," which is basically just a fancy way of describing a blockchain that piggy-backs off of the security of another "parent" blockchain. Specifically, Optimistic Rollups take advantage of the consensus mechanism (like PoW or PoS) of their parent chain instead of providing their own. In Optimism's case, this parent blockchain is Ethereum.Trades transactions are settled on a Layer 2 and batched to Ethereum l1

**How Optimistic Roll-ups work?**

Optimistic rollups sit in parallel to the main Ethereum chain on layer 2. They can offer improvements in scalability because they don't do any computation by default. Instead, after a transaction, they propose the new state to Mainnet or "notarise" the transaction. With Optimistic rollups, transactions are written to the main Ethereum chain as calldata, optimizing them further by reducing the gas cost.

As computation is the slow, expensive part of using Ethereum, Optimistic rollups can offer up to 10-100x improvements in scalability dependent on the transaction. This number will increase even more with the introduction of shard chains as more data will be available if a transaction is disputed.

**Will there be more assets in the Future?**

Synthetix provides decentralized derivatives liquidity for protocols like Kwenta. The selection process for adding new Synths to Synthetix is driven by demand, liquidity, and volatility. [Chainlink](https://chain.link/) must support the data feeds necessary for any proposed assets to be considered for inclusion. If the above requirements are met anyone can write a SIP (synthetix improvement proposal) to have an asset considered for listing.

**Type of Collateral accepted on Kwenta**

Kwenta currently denotes its quote asset in sUSD, anyone trading on Kwenta must deposit sUSD to begin trading.

**How do i Deposit sUSD?**

Traders looking to use Kwenta Perpetual Futures need a metamask wallet, optimism added as a selectable network, and sUSD on layer 2 optimism. Once traders have all of the above they can head to Kwenta, select any of the available assets to trade connect their wallet, and deposit funds to begin trading. Once done trading a specific asset pair traders can remove any sUSD back to their wallet and make use of their funds elsewhere.

**Minimum Deposit & Why?**

Due to being built on Optimism transaction costs to execute trades are ridiculously cheap allowing us to have low minimum deposit requirements. Liquidations on Kwenta can be executed by anyone with a web3 wallet and since there are no centralized entities making sure positions get liquidated in a timely manner we must incentivize liquidations to happen timely for system stability reasons.

Because of this liquidators are paid $25 sUSD as an incentive to aid in making sure liquidations are actually occurring. Since there is a minimum fee paid to these liquidators a $40 minimum deposit has been implemented as depositing anything less wouldn’t leave a ton of room between opening a position and having that position liquidated with enough funds to cover the liquidator cost.

**How does isolated margin work?**

An isolated Margin is the margin balance allocated to an individual asset. Isolated Margin contracts allow traders to manage their risk on individual assets being traded by restricting the amount of margin allocated to each one. The allocated margin balance for each asset can be individually adjusted.

**How much leverage is available?**

Currently, Kwenta offers 10x leverage, with plans to raise the available leverage in the future dynamically per asset.

**How does Kwenta determine an asset's price?**

Kwenta utilizes the decentralized Chainlink [oracle network](https://chain.link/education/blockchain-oracles) which provides up-to-date token price data to smart contracts on Ethereum and is used to determine an asset’s current price.

