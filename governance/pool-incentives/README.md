# Pool Incentives

A certain percentage of the `MAHA` inflation is directed to users who provide liquidity within the protocol. This usage is measured via "Gauge" contracts. Each pool has an individual liquidity gauge.&#x20;

The [Gauge Voting Contract](https://github.com/MahaDAO/governance-contracts/blob/master/contracts/voter/BaseV2Voter.sol) maintains a list of gauges and their types, with the weights of each gauge and type.

The user deposits their LP tokens into the liquidity gauge to measure liquidity over time. Coin rates the gauge is getting depend on the current inflation rate, gauge weight, and gauge type weights.&#x20;

Each user receives a share of newly minted `MAHA` proportional to the amount of LP tokens locked. Additionally, rewards may be boosted by up to a factor of 5x if the user holds a `MAHAX NFT` (to learn more about boosting, read [Boosting Pool Incentives](../boosting-staking-rewards.md)).\
