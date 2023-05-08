---
description: >-
  This section explains more about how MAHA NFTs can be used for voting on where
  MAHA emissions go.
---

# Pool Voting

{% hint style="info" %}
Pool Voting is handled by the [BaseV2Voter](https://github.com/MahaDAO/governance-contracts/blob/master/contracts/voter/BaseV2Voter.sol) contract which is deployed at [0xfbbe448d38231c298e9a2251bc0c567543e2cca6](https://etherscan.io/address/0xfbbe448d38231c298e9a2251bc0c567543e2cca6)
{% endhint %}

A certain percentage of the `MAHA` inflation is directed to users who provide liquidity within the protocol.

This usage is measured via "`Gauge`" contracts. The [Gauge Voting Contract](https://github.com/MahaDAO/governance-contracts/blob/master/contracts/voter/BaseV2Voter.sol) maintains a list of gauges and the amount of `MAHAX` votes each gauge has received. Each pool has an individual liquidity gauge.

A liquidity provider deposits their liquidity pool (LP) tokens into the gauge to receive these `MAHA` rewards. The more votes from `MAHAX` holders a gauge receives, the more share of `MAHA` emissions it receives.

![The pool voting page that showcases how much votes a pool receives](<../../.gitbook/assets/image (2) (3).png>)

Each user receives a share of newly minted `MAHA` proportional to the amount of LP tokens they've deposited. Additionally, rewards may be boosted by up to a factor of `5x` if the user holds a `MAHAX NFT` (to learn more about boosting, read [Boosting Pool Incentives](boosting-pools.md)).

## Whitelisting Gauges/Pools

To protect the protocol from malicious tokens/gauges a whitelist mechanism is enforced. This ensures that every contract that receives with `MAHA` emissions is properly reviewed by the community.

The whitelist exists in the [BaseVoter contract](https://github.com/MahaDAO/governance-contracts/blob/master/contracts/voter/BaseV2Voter.sol) which is owned by the [Governor contract](https://github.com/MahaDAO/governance-contracts/blob/master/contracts/MAHAXGovernor.sol), which means to whitelist a new token it will have to pass via a on-chain [Governance vote](../creating-voting-on-proposals.md).

{% hint style="info" %}
To make a request for a new gauge, start a thread at the discussion forums under the ["Gauge Proposals" category](https://discuss.mahadao.com/c/governance/gauge-proposals/54).
{% endhint %}

{% embed url="https://discuss.mahadao.com/c/governance/gauge-proposals/54" %}
