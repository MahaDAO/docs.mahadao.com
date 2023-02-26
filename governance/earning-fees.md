---
description: >-
  How does the governance portal distribute fees & rewards to DAO members in the
  protocol
---

# Earning Fees & Rewards

{% hint style="info" %}
To understand sources of revenue and how they get distributed, read the ["Revenue Share"](../miscellaneous/revenue-share.md) section.
{% endhint %}

To incentivize participants to stake in the MahaDAO ecosystem, the governance portal allows stakers to claim fees based on their user activity.

Some fees can be earned by being passive participants in the ecosystem, whereas some fees require more active participation from DAO members.

There are four kinds of fees/incentives that members receive.

* **Inflation Rewards:** This is primarily in `MAHA`. The monthly `MAHA` inflation `5000 MAHA` is set aside to be distributed to all `MAHA` stakers.&#x20;
* **Fees from Protocol:** This is primarily in `ETH` & `ARTH`. Revenue generated from the various products from the protocol will be distributed back to the DAO members.
* **Rewards from Governance Voting:** This is primarily in `MAHA`. To incentivize voter participation, `1000 MAHA` every month is set aside. To learn more, read [voting rewards](delegation-and-voting-rewards.md).
* **Rewards from Pool incentives:** This would be in various other tokens. Projects and DAOs that aim to incentivize `MAHA` voters to vote for their pools can pay DAO members rewards in their own tokens in return for the DAO's voting power. To learn more, read [pool incentives](pool-voting/).

The table below gives a summary of what kind of activities receive what kind of rewards.

<table><thead><tr><th>Reward Kind</th><th data-type="checkbox">Can be a passive member?</th><th data-type="checkbox">Can Rewards be Delegated?</th></tr></thead><tbody><tr><td>Inflation Rewards</td><td>true</td><td>false</td></tr><tr><td>Protocol Fees</td><td>true</td><td>false</td></tr><tr><td>Governance Voting Rewards</td><td>false</td><td>true</td></tr><tr><td>Pool Incentives</td><td>true</td><td>false</td></tr></tbody></table>

Some rewards can be delegated (such as the voting rewards), whereas other rewards can be earned passively without doing anything besides just having their `MAHAX` staked (Inflation Rewards & Protocol fees).

{% hint style="info" %}
In general, participants that are the most active in the DAO, will get the most amount of rewards.&#x20;
{% endhint %}

Pool Incentive rewards require members to be active and can not have rewards be delegated. This means if you have delegated your voting power, the pool incentive rewards will go to your delegate instead of you. This is due to technical limitations of smart-contract code and reducing gas fees, although future revisions can update this feature. (To learn more, read [delegation](delegation-and-voting-rewards.md))

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption><p><a href="https://gov.mahadao.com/#/rewards">https://gov.mahadao.com/#/rewards</a> The rewards page where users can claim rewards from various reward streams</p></figcaption></figure>

_To see a list of contract that distribute fees, see_ [_Deployed Addresses_](deployed-address.md)__

### How Fees are Earned & Distributed

| Kind                      | How they are earned?                                                                               | How they are distributed?                                                                                |
| ------------------------- | -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| Inflation Rewards         | By simply having a MAHAX NFT. All NFTs accumulate rewards over time.                               | From the rewards page under the "Protocol Fees" section. NFTs must be staked to claim inflation rewards. |
| Protocol Fees             | Same as Inflation Rewards. More information at [Revenue Share](../miscellaneous/revenue-share.md). | Same as Inflation Rewards. More information at [Revenue Share](../miscellaneous/revenue-share.md).       |
| Governance Voting Rewards | By participating in the governance portal, creating proposals and voting on them.                  | From the rewards page under the "Governance Voting Rewards" section.                                     |
| Pool Incentives           | By participating the Pool Voting page and voting for pools with active pool incentives             | From the rewards page under the "Pool Voting Rewards" section.                                           |
