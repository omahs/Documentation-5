# Jargon

**Live Price:** The price is tracked from a centralized reporting entity. This price will often divert from the exchange oracle price.

**Oracle Price:** Kwenta utilizes a decentralized [Chainlink oracle network](../../../resources/oracles.md) to price its assets. These oracles provide up-to-date token prices data to smart contracts on Ethereum.

**Unrealized PNL:** The unrealized PNL is based on the difference between the average entry price and oracle price. It is a reference PNL of a position.&#x20;

**Realized PNL**_**:**_ This is based on the difference between the entry price and close price of a position. Trading Fees and Funding Fees are also included in the realized PNL.

**Liquidation:** To keep the positions open, traders are required to hold a percentage of the value of their position, i.e., the Maintenance Margin percentage. If a trader fails to fulfill the maintenance requirement, his/her position will be flagged for liquidation, and any margin will be lost.

**Initial margin:** Is the percentage of the purchase price of a future position that must be covered by cash or collateral when leverage trading.

**Leverage:** Leverage refers to using borrowed capital to make trades. Leverage trading applied a multiplier to your buying or selling power, allowing you to trade larger amounts.

**Funding Rate:** Funding rates are periodic payments to or from traders depending on their trade direction. These rates are used by Kwenta to balance the skew of the Open Interest on Kwenta, be aware of these rates because they impact the daily holding cost of a perpetual contract position.

**Open Interest:** Open interest is the total number of outstanding derivative contracts, futures that have not been settled. Open interest equals the total difference of bought and sold contracts, not the total of both added together

**Volume:** Volume is the total notional value being traded between market participants.

**Notional Position Size:** The notional value is the total amount of an asset's underlying value at its spot price. The notional value distinguishes between the amount of money invested and the amount of money associated with the whole position. The notional value is calculated by multiplying the units in one contract by the spot price.

