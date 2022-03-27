# Exchange Fees

Users pay a fee whenever they open or increase a position. However, we wish to incentivize the reduction of skew, so we distinguish between maker and taker fees. A maker is someone reducing skew and a taker is someone increasing it, and so we charge makers less than takers, possibly even zero insofar as this is possible in the presence of front-running.&#x20;

This fee will be charged out of the user's remaining margin. If the user has insufficient margin remaining to cover the fee, then the transaction should revert unless they deposit more margin or make some profit. As the fee diminishes a user's margin and is charged after order confirmation, they should be aware that it will slightly increase their effective leverage.

The fees will be denoted by the symbol ϕ as follows:

| Symbol | Description    | Notes                                                                                |
| ------ | -------------- | ------------------------------------------------------------------------------------ |
| ϕt     | Taker fee rate | Charged against the notional value of orders increasing the skew. Initially, ϕt=0.3. |
| ϕm     | Maker fee rate | Charged against the notional value of orders reducing the skew. Initially, ϕm=0.1.   |

Please visit [Exchange Fees](../l2-perpetual-contracts/#exchange-fees) & [Dynamic Fees](../../exchange-fees.md#dynamic-fees) for more information in regards to Exchange Fes.
