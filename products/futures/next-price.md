# Next Price

#### What is Next-Price? <a href="#what-is-next-price" id="what-is-next-price"></a>

In order to allow funding rate arbitrage to be profitable and for fees on Kwenta to be competitive we are introducing a new “order type” on Kwenta Futures: **Next Price Orders**. A special exchange fee will be applied to this specific mechanism of non-atomic trades that will use the future (next price) update coming from the oracle.

Due to using the future, unknown price to initiate a trade, this mechanism should thwart users looking to make risk-free profits by front running (because two prices ahead, instead of one, need to be known to profitably front-run next-price). This also gives Kwenta the opportunity to offer a low bps fee alternative for genuine traders using the platform.

#### Keepers <a href="#keepers" id="keepers"></a>

Keepers can do things like execute limit orders, liquidate under-collateralized loans, and just about anything on-chain autonomously. An automated keeper was developed to automatically execute Next-Price orders when their conditions are met (enough oracle price updates have passed). Due to this development, there will be no manual intervention needed from traders on Kwenta to execute next price orders.

#### How does Next-Price Work? <a href="#how-does-next-price-work" id="how-does-next-price-work"></a>

The Next-Price mechanism has 3 functions:

* `submitNextPriceOrder`: stores an order to be executed at the next-price update. Only one order can be stored for one account at a time. A certain amount of fees are deducted from the account on submission: commitment fee, and keeper fee. The commitment fee is refundable if the order will be executed successfully, the keeper fee will be paid to the keeper executing it as an incentive. The commitment fee is a proportional fee and is equal to the exchange fee that would be charged for a regular order. The keeper fee is equal to the minimum keeper fee (\~20 sUSD initially). The purpose of the commitment fee is to make cancellation cost as much as a regular trade to prevent free optionality (which would mean that the decision to trade is taken when next price is known, which reduces its effectiveness).
* `cancelNextPriceOrder`: a stored order can be canceled by the account itself at any time. It can also be canceled by any other account (e.g. keeper) after the confirmation window (the window during which the order can be executed). If an order is canceled, the keeper fee is paid to whoever submitted the cancellation transaction, and the commitment fee is paid to the fee pool.
* `executeNextPriceOrder`: the order can be executed by the keeper during the confirmation window (initially 2 oracle price rounds). If the order executes successfully, the (**commitment fee (-) the next price fee)** is refunded to the account. The keeper fee is paid to whoever submitted the transaction. If the confirmation window is over, or if the order cannot be executed (reverts), the order will be canceled instead and the keeper fee + the commitment fee is forfeited.

> This mechanism allows lower exchange fees (taker and maker) for such orders, the fees will be set to: taker - 5 basis points, and maker - 0. The dynamic fee will still be added according to the dynamic fee conditions during the execution round (to prevent circumventing the dynamic fee mechanism).

#### TL: DR On Next Price <a href="#tl-dr-on-next-price" id="tl-dr-on-next-price"></a>

* There is a Keeper fee (initially set to 20 sUSD non-refundable once the order is set)
* There is a commitment fee (standard exchange bps fees with the difference between standard “market order fees” and “Next Price fees'“ rebated to the trader once the order executes successfully.)
* If for any reason the next price order fails (edge cases) or is canceled, traders forfeit the commitment fee.

#### How to use the next price order on Kwenta? <a href="#how-to-use-the-next-price-order-on-kwenta" id="how-to-use-the-next-price-order-on-kwenta"></a>

Traders on Kwenta will see a new addition to “order types” available on Kwenta. Traders can take advantage of “next price orders” and their matching lower bps fees, by heading to Kwenta, navigating to the ‘Futures’ Tab, and connecting their wallet.

![](data:image/svg+xml,%3csvg%20xmlns=%27http://www.w3.org/2000/svg%27%20version=%271.1%27%20width=%272544%27%20height=%271402%27/%3e)![Connect your wallet](https://mirror.xyz/\_next/image?url=https%3A%2F%2Fimages.mirror-media.xyz%2Fpublication-images%2FHLPpQms3RhEKT7e1YuxCp.png\&w=3840\&q=90)

Once connected traders can select the asset they wish to trade from the ‘Asset Selection Dropdown’ to be taken to the perspective markets dashboard.

In the ‘Order Entry’ panel, you’ll see two types of orders. The existing market order will execute a trade at the current market rate (oracle price) instantly with regular exchange fees, and our new Next Price orders, offering a substantial reduction in exchange bps fees.

![](data:image/svg+xml,%3csvg%20xmlns=%27http://www.w3.org/2000/svg%27%20version=%271.1%27%20width=%272544%27%20height=%271424%27/%3e)![Select Next Price To Get Started](https://mirror.xyz/\_next/image?url=https%3A%2F%2Fimages.mirror-media.xyz%2Fpublication-images%2FPMtoKnkICS3aycJtmohBO.png\&w=3840\&q=90)

Once you’ve toggled to Next-Price you won’t notice a huge change on the order entry Panel, but rest assured as long as Next Price is selected orders will be placed accordingly and traders can submit trades as they normally would.

![](data:image/svg+xml,%3csvg%20xmlns=%27http://www.w3.org/2000/svg%27%20version=%271.1%27%20width=%272536%27%20height=%271416%27/%3e)

Once approved traders will see their pending next price order in the Open Orders tab along with its relevant information, from here traders can also cancel a next price order in case they need to. (note that the keeper fee along with the commitment fee will be forfeited when traders cancel the next price order.

![](data:image/svg+xml,%3csvg%20xmlns=%27http://www.w3.org/2000/svg%27%20version=%271.1%27%20width=%272548%27%20height=%271450%27/%3e)![Find Your Next Price Order](https://mirror.xyz/\_next/image?url=https%3A%2F%2Fimages.mirror-media.xyz%2Fpublication-images%2FHGRg8j7cgcQvVDObaLHyW.png\&w=3840\&q=90)
