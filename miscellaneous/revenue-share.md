---
description: >-
  This page talks about how revenue from the protocol is shared amongst various
  parts of the DAO.
---

# Revenue Share

The MahaDAO ecosystem has various sources of revenue which get collected at a single place and get distributed across various parties.&#x20;

{% hint style="info" %}
All fees get accumulated to the `FeeSplitter` contract which is deployed at [0x9032f1bd0cc645fde1b41941990da85f265a7623](https://etherscan.io/address/0x9032f1bd0cc645fde1b41941990da85f265a7623)
{% endhint %}

Revenue comes from the following channels:

1. **Uniswap / Curve Trading Fees:** All LP tokens and NFT positions staked in one of the various MAHA gauges transfers the trading fees earned to the DAO. Trading fees earned from Uniswap V3 is 1% on every trade.
2. **Opensea, NFT Marketplace Royalties:** All NFT marketplaces charge a creator fee for every sale of NFTs that happen on the protocol. This creator fee is currently set at 5-10%.
3. **MahaLend Fees**: Users that borrow ARTH from the MahaLend protocol pay a borrowing interest in the form of ARTH. This interest is split between lenders and to the DAO.
4. **ARTH Redemptions:** Any time a user redeems ARTH for the underlying ETH from an active loan, a 0.5% redeemption fee is charged in ARTH.

To get a deeper idea of the various sources of revenue, we have prepared a Dune dashboard that showcases this information.

{% embed url="https://dune.com/mahadao/revenue" %}

### How Revenue Gets Distributed

Once revenue gets collected from the `FeeSplitter` contract it then gets sent onto various different sources to grow the protocol.

| Recipient                                                                                                 | Allocation | Comments                                                                                                                                                                                            |
| --------------------------------------------------------------------------------------------------------- | ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Liquidity Growth - [Address](https://etherscan.io/address/0x8be9cbbdfeeaf1dcacfb608105ec27384b6ff628)     | 10%        | To continuously grow the liquidity of the ecosystem. See "[Automated Liquidity](automated-liquidity.md)".                                                                                           |
| Core Team Operations - [Address](https://etherscan.io/address/0x6357EDbfE5aDA570005ceB8FAd3139eF5A8863CC) | 60%        | Mainly to pay for operations of the core team.                                                                                                                                                      |
| ARTH v1 Holders - [Address](https://etherscan.io/address/0xE595b22bEB0dEEE5a41D2B29a86E4eDeC8B7D180)      | 30%        | To repay holders of the ARTH v1 protocol. See ​ [MIP.C2-0019](https://discuss.mahadao.com/t/mip-c2-0019-stop-arthx-mint-function-and-make-arthx-the-fee-bearing-token-for-the-entire-ecosystem/152) |

Changes to this distribution can be made via [governance vote](../governance/creating-voting-on-proposals.md).&#x20;
