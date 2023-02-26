---
description: >-
  This section talks about the various automations that are a part of the
  MahaDAO ecosystem.
---

# Automations

Automations help maintain the entire ecosystem stay completely decentralized without the need of human intervention.&#x20;

The following keepers perform various maintenance activities such as updating pricefeeds, deposit staking rewards etc... on a daily, monthly or weekly basis.&#x20;

These automations are mainly deployed using [Chainlink automations](https://automation.chain.link/mainnet) which require `LINK` tokens to execute these operations.

| Automation                      | Description                                                                                              | Links                                                                                                                                                                                                                                                                                                                                   | Frequency                                    |
| ------------------------------- | -------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------- |
| **Stability Pool Keeper**       | Deposits the `MAHA` rewards into the stability pool. Currently the SP gets over `1000 MAHA` every month. | [Chainlink ](https://automation.chain.link/mainnet/59208905967654794269499271144217852610845640577500284274456197411978270169905)- [Etherscan](https://etherscan.io/address/0x5e98d3f8B5074b6389477fD88856f5209748CaA7) - [Source](https://github.com/MahaDAO/chainlink-keepers/blob/master/contracts/StabilityPoolKeeper.sol)          | Monthly                                      |
| **Liquidity Automation Keeper** | Automates growing liquidity for the ecosystem.                                                           | [Chainlink ](https://automation.chain.link/mainnet/3721489002688010012487100574040058577206915083645733239727499897918958857478)- [Etherscan](https://etherscan.io/address/0x8bE9cbbDfEeAF1dCAcfb608105eC27384b6Ff628) - [Source](https://github.com/MahaDAO/liquidity-contracts/blob/master/contracts/MasterRouter.sol)                | Based on how much revenue has been collected |
| **Gauge Emissions Keeper**      | Deposits MAHA rewards for the various gauges.                                                            | [Chainlink ](https://automation.chain.link/mainnet/43649290915381837395458753574003525406351865348348305715432273118473138178917)- [Etherscan](https://etherscan.io/address/0xBd86A195c90ceC4606dBC378Ea0aa338f674a704) - [Source](https://github.com/MahaDAO/chainlink-keepers/blob/master/contracts/EmissionControllerKeeper.sol)     | Every two weeks                              |
| **ARTH Pricefeed Keeper**       | Updates the ARTH price-feed which calculates the price by using moving averages.                         | [Chainlink](https://automation.chain.link/mainnet/23618531437504356035592854747757593228146241914405646307214212844495623843708) - [Etherscan](https://etherscan.io/address/0x066A917fA2e1739ccfc306dc73ff78EECa8B6F29) - [Source](https://github.com/MahaDAO/gmu-oracle-contracts/blob/master/contracts/GMUOracle.sol)                 | Daily                                        |
| **StakingReward Keeper**        | Deposits the staking rewards into the various distributor contracts for MAHA stakers.                    | [Chainlink](https://automation.chain.link/mainnet/41266333116245221905699183984714327620810494154220963165674006901939269314215) - [Etherscan](https://etherscan.io/address/0x2E8978Ae41ec867a0eB5dAf38a4E8b62858DbFCb) -[Source](https://github.com/MahaDAO/chainlink-keepers/blob/master/contracts/StakingRewardsKeeper.sol)          | Weekly                                       |
| **MAHA Emissions Keeper**       | Sends the MAHA tokens from the monthly emissions to the various beneficiaries                            | [Chainlink](https://automation.chain.link/mainnet/100677908923339746482037180250497929693616624651083220566107247329239608938595) - [Etherscan](https://etherscan.io/address/0xd3408050f18024E9412311A3aFf8B8294f083f67) -[Source](https://github.com/MahaDAO/governance-contracts/blob/master/contracts/splitters/MAHASplitKeeper.sol) | Monthly                                      |

Source code for the various keepers can be found in the links above. We also maintain a repository that contains the deployment code for the above keepers.

{% embed url="https://github.com/MahaDAO/chainlink-keepers" %}
