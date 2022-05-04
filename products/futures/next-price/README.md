# Next Price

#### TL: DR On Next Price <a href="#tl-dr-on-next-price" id="tl-dr-on-next-price"></a>

* There is a Keeper fee (initially set to 20 sUSD non-refundable once the order is set)
* There is a commitment fee (standard exchange bps fees with the difference between standard “market order fees” and “Next Price fees'“ rebated to the trader once the order executes successfully.)
* If for any reason the next price order fails (edge cases) or is canceled, traders forfeit the commitment fee.

#### What is Next-Price? <a href="#what-is-next-price" id="what-is-next-price"></a>

In order to allow funding rate arbitrage to be profitable and for fees on Kwenta to be competitive we are introducing a new “order type” on Kwenta Futures: **Next Price Orders**. A special exchange fee will be applied to this specific mechanism of non-atomic trades that will use the future (next price) update coming from the oracle.

Due to using the future, unknown price to initiate a trade, this mechanism should thwart users looking to make risk-free profits by front running (because two prices ahead, instead of one, need to be known to profitably front-run next-price). This also gives Kwenta the opportunity to offer a low bps fee alternative for genuine traders using the platform.

#### Keepers <a href="#keepers" id="keepers"></a>

Keepers can do things like execute limit orders, liquidate under-collateralized loans, and just about anything on-chain autonomously. An automated keeper was developed to automatically execute Next-Price orders when their conditions are met (enough oracle price updates have passed). Due to this development, there will be no manual intervention needed from traders on Kwenta to execute next price orders.

#### How does Next-Price Work? <a href="#how-does-next-price-work" id="how-does-next-price-work"></a>

The Next-Price mechanism has 3 functions:

* `submitNextPriceOrder`: Stores an order to be executed at the next-price update. Only one order can be stored per asset at a time. A certain amount of fees are deducted from the account on submission: commitment fee, and keeper fee. A portion of the commitment fee is refundable if the order is executed successfully, the keeper fee will be paid to the keeper executing it as an incentive. The commitment fee is a proportional fee and is equal to the exchange fee that would be charged for a regular order. The keeper fee is equal to the minimum keeper fee (\~20 sUSD initially). The purpose of the commitment fee is to make cancellation cost as much as a regular trade to prevent free optionality (which would mean that the decision to trade is taken when Next Price is known, which reduces its effectiveness).
* `cancelNextPriceOrder`: a stored order can be canceled by the account itself at any time. It can also be canceled by any other account (e.g. keeper) after the confirmation window passes(the window during which the order can be executed). If an order is canceled, the keeper fee is paid to whoever submitted the cancellation transaction, and the commitment fee is paid to the fee pool.
* `executeNextPriceOrder`: the order can be executed by the keeper during the confirmation window (initially a minimum of 1 oracle update and a maximum of 2 price rounds). If the order executes successfully, the (**commitment fee (-) the next price fee)** is refunded to the account. The keeper fee is paid to whoever submitted the transaction. If the confirmation window is over, or if the order cannot be executed (reverts), the order will be canceled instead and the keeper fee will be paid to the entity canceling the stale order & the commitment fee is forfeited.

> This mechanism allows lower exchange fees (taker and maker) for such orders, the fees will be set to the following fee schedule below. The dynamic fee will still be added according to the dynamic fee conditions during the execution round (to prevent circumventing the dynamic fee mechanism).

![Current Fee Schedule](../../../.gitbook/assets/123.png)

