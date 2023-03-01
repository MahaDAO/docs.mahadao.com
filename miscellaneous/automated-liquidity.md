---
description: >-
  This section talks about how the protocol automates growing liquidity for the
  ecosystem.
---

# Automated Liquidity

Automated Liquidity is a feature of the MahaDAO ecosystem that automates the growth of liquidity from the fees earned from the ecosystem.&#x20;

Whenever the ecosystem earns fees from the various sources of revenue, a portion of it goes towards growing liquidity. A highly liquid market allows people to enter/exit the ecosystem easily.

{% embed url="https://github.com/MahaDAO/liquidity-contracts" %}
Source code for the liquidity automation contracts
{% endembed %}

## How does it work?

A share of the revenue from the protocol first gets collected at a common contract called as the `MasterRouter` contract, which is deployed at [0x8be9cbbdfeeaf1dcacfb608105ec27384b6ff628](https://etherscan.io/address/0x8be9cbbdfeeaf1dcacfb608105ec27384b6ff628#code).

Revenue can be in the form `ETH`, `ARTH`, `MAHA` or any ERC20 token.&#x20;

From there, the MasterRouter contract decides how much liquidity to add to the various pools. Currently, the logic implemented is as follows.

| Asset           | Liquidity Pool                                                                                             | How does it add to LP?                                                                                                   |
| --------------- | ---------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| `ARTH`          | Curve ARTH/USDC - [Link](https://curve.fi/#/ethereum/pools/factory-crypto-185/deposit)                     | All the ARTH captured is directly added into Curve.                                                                      |
| `ETH` or `WETH` | MAHA/WETH 1% Uniswap - [Link](https://info.uniswap.org/#/pools/0xb28ddf1ee8ee014eafbecd8de979ac8d297931c7) | Half of the WETH is first swapped to MAHA and then the rest is added into the Uniswap V3 position (as much as possible). |
