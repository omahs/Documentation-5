# Volume Source Fee

The current approach to Synthetix ecosystem partners is to leverage the volume program which pays out monthly rewards in SNX to integrators based on the volume generated. \
\
The issue with this program is that it does not scale linearly with volume so there is limited upside for integrators generating large volumes. By splitting the exchange fee into a Protocol Fee and Source Fee we can ensure that the upfront integration effort is worthwhile for potential ecosystem partners. \
\
This will create a reliance on revenue generated via a Synthetix integration and further reinforce the reliance of these protocols on Synthetix volume creating strongly aligned incentives throughout the ecosystem.

The transaction fee variable will be split into two parts, a base level Protocol Fee and an optional Source Fee that can be triggered by a frontend passing a Volume Partner Code to the Exchange Contracts. \


The Source Fee will be fixed at 10% of Synthetix fees generated.
