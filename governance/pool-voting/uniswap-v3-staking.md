---
description: >-
  This section talks about how Uniswap V3 liquidity providers can participate in
  providing liquidity for MAHA rewards
---

# Uniswap V3 Staking

In [Uniswap V3](https://uniswap.org/blog/uniswap-v3), liquidity providers (LPs) can concentrate their capital within custom price ranges, providing greater amounts of liquidity at desired prices. In doing so, LPs construct individualized price curves that reflect their preferences.

LP positions will be represented by non-fungible tokens (NFTs) which can be staked for `MAHA` via the governance portal.

{% hint style="info" %}
To learn more about how Uniswap v3 works, visit [https://uniswap.org/blog/uniswap-v3](https://uniswap.org/blog/uniswap-v3)
{% endhint %}

Using a modified version of the [Uniswap V3 staking contract](https://github.com/Uniswap/v3-staker/blob/main/contracts/UniswapV3Staker.sol) and [Solidly's Gauge](https://github.com/solidlyexchange/solidly/blob/master/contracts/BaseV1-gauges.sol), MahaDAO introduces [MAHA Uniswap v3 Gauges](https://github.com/MahaDAO/governance-contracts/blob/master/contracts/gauges/BaseGaugeV2UniV3.sol) that give out `MAHA` incentives voted upon by `MAHAX NFT` holders to liquidity providers (LP) who provide liquidity to Uniswap V3 LP pairs.

LP stakers will receive `MAHA` rewards for the time when the current price of the liquidity pair is within range of their liquidity position.&#x20;

![An example of ARTH/MAHA Uniswap LP position where the min and max price can be specified by the user.](<../../.gitbook/assets/image (12).png>)

## FAQs

### Will I suffer from Impermanent Loss from Uniswap V3 staking?

Uniswap V3 minimizes impermanent loss by allowing liquidity providers to choose the range for which they'd like to provide liquidity for. To understand more about this mechanism, read [https://uniswap.org/blog/uniswap-v3](https://uniswap.org/blog/uniswap-v3)&#x20;

### If the price of the liquidity pair goes out of range, will I stop earning rewards?

Yes. The staking contract takes into account the seconds at which your pool was driving the most liquidity. So if the price moves out of range, then your liquidity position will stop earning rewards.

### If I provide more liquidity, do I earn more rewards?

Yes. You should ideally aim to provide not just the most liquidity but also make sure your position is within the range of the current price to earn the most amount of rewards.

### If I have a staked a MAHAX NFT, does my APR get boosted?

Yes. Based on the amount of `MAHAX` you hold, your staking APR can get boosted by up to 5x. For details on how this is calculated, visit [Boosting Pool Incentives](boosting-pools.md).
