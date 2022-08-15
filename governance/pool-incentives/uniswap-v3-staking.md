---
description: >-
  This section talks about how Uniswap V3 liquidity providers can participate in
  providing liquidity for MAHA rewards
---

# Uniswap V3 Staking

In [Uniswap V3](https://uniswap.org/blog/uniswap-v3), liquidity providers (LPs) can concentrate their capital within custom price ranges, providing greater amounts of liquidity at desired prices. In doing so, LPs construct individualized price curves that reflect their own preferences.

LP positions will be represented by non-fungible tokens (NFTs) which can be staked for MAHA via the governance portal.

{% hint style="info" %}
To learn more about how Uniswap v3 works, visit [https://uniswap.org/blog/uniswap-v3](https://uniswap.org/blog/uniswap-v3)
{% endhint %}

Using a modified version of the [Uniswap V3 staking contract](https://github.com/Uniswap/v3-staker/blob/main/contracts/UniswapV3Staker.sol) and [Solidly's Gauge](https://github.com/solidlyexchange/solidly/blob/master/contracts/BaseV1-gauges.sol), MahaDAO introduces [MAHA Uniswap v3 Gauges](https://github.com/MahaDAO/governance-contracts/blob/master/contracts/gauges/BaseGaugeV2UniV3.sol) that give out MAHA incentives voted upon by MAHAX NFT holders to liquidity providers (LP) who provide liquidity to Uniswap V3 LP pairs.

LP stakers will receive MAHA rewards for the time when the current price of the liquidity pair is within range of their liquidity position.&#x20;

![An example of ARTH/MAHA Uniswap LP position where the min and max price can be specified by the user.](<../../.gitbook/assets/image (6).png>)

## FAQs

### Will I suffer from Impermanent Loss from Uniswap V3 staking?

### If the price of the liquidity pair goes out of range, will I stop earning rewards?

### If I provide more liquidity do I earn more rewards?

### If I have a staked a MAHAX NFT, does my APR get boosted?

