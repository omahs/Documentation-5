# Liquidations

Liquidations are a part of leveraged trading. When traders open positions with leverage, they are using collateral (margin) to borrow money from the Synthetix Debt pool to purchase an asset.This allows traders to trade with more capital than they actually have. If the value of your position falls and losses begin to approach the value of your initial collateral a Liquidation will take place.&#x20;

> For example, if you open a 10x (Max) leverage position using $500 sUSD, your total position size will be worth $5,000 sUSD. Of that position's value $4500 is borrowed and $500 sUSD (Margin) belongs to the trader.

Kwenta enforces a minimum ratio between the position's value and the margin, called a _maintenance margin_. On Kwenta, the maintenance margin is %.

In our previous example, if your position's value drops to 400 sUSD, it will be liquidated.\
\
Once a position's remaining margin is exhausted, it must be closed in a timely fashion, so that its contribution to the market skew and to the overall debt pool is accounted for as rapidly as possible, necessary for accuracy in funding rate and minting computations.

As price updates cannot directly trigger the liquidation of insolvent positions, it is necessary for keepers to perform this work by executing a public liquidation function. However, as opposed to the usual liquidations pattern, no capital is required for the liquidator - only submitting the transaction specifying the account to be liquidated.

In order to incentivize the keepers, the liquidation penalty proportional to the position size of the account will be paid to the keeper. The penalty will have a minimal size to ensure that transaction costs are covered and small accounts liquidation is also profitable (to prevent small accounts bloat). The initial setting for the penalty/incentive will be 35 basis points (of position size).

Additionally, because a price update might cause an account to have a negative margin after accounting for the liquidation incentive, an additional proportional margin buffer will be used when calculating the liquidation threshold margin and price. The buffer will be set such that on average the remaining margin on liquidation after deducting the penalty is close to 0, but positive. This is to prevent the debt pool from leaking value in these cases. The initial setting for the buffer will be 25 basis points (of notional position size).

The liquidation margin will be computed by summing both the liquidation incentive payable to a keeper, and the buffer (payable to the fee pool if positive).\
\
For more information on Liquidations check out [SIP-80](https://sips.synthetix.io/sips/sip-80/#liquidations-and-keepers)
