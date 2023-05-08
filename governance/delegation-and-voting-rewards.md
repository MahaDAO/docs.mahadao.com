---
description: >-
  This section explains about delegation and how a user can claim voting rewards
  for participating in the governance portal.
---

# Delegation & Voting Rewards

{% hint style="info" %}
Delegation is handled by the [Staker](https://github.com/MahaDAO/governance-contracts/blob/master/contracts/MAHAXStaker.sol) Contract which is currently deployed at [0x608917f8392634428ec71c6766f3ec3f5cc8f421](https://etherscan.io/address/0x608917f8392634428ec71c6766f3ec3f5cc8f421)
{% endhint %}

Delegation is an important attribute in encouraging high voter participation. Delegation means that a voter (who ideally is inactive) transfers their voting power to another (more active) voter without losing the ownership of the NFT where the initial voting power comes from. Delegation also allows voters to revoke the voting power that they've delegated at any point in time.&#x20;

It provides a safe and easy way for voters to lend their voting power to voters that share their best interests or is more active.

_This is similar to how an election is run in modern-day democracies, where voters vote for politicians who will take their votes to represent their interests best._

Delegation is built directly into the NFTs and is possible only if a user [stakes his MAHAX NFT](locking-mechanism.md#staking-nfts).&#x20;

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption><p><a href="https://etherscan.io/tx/0x93c5b601ef265151b7594e8cfaca09d3ca3e59d9f375a8866a8daef223c50bfa">https://etherscan.io/tx/0x93c5b601ef265151b7594e8cfaca09d3ca3e59d9f375a8866a8daef223c50bfa</a> An example transaction of a voter delegating his voting power to another address.</p></figcaption></figure>

## Levels of Delegation

Delegation can work at a single level only. That is, if `Alice` delegates voting power to `Bob`, and `Bob` delegates voting power to `Charlie`. Then `Charlie` does not get the voting power of both `Alice` and `Bob`. The below table explains the scenario:

| Person  | Starting Voting Power  | Alice delegates to Bob | Bob delegates to Charlie |
| ------- | ---------------------- | ---------------------- | ------------------------ |
| Alice   | `300 MAHAX`            | `0   MAHAX`            | `0   MAHAX`              |
| Bob     | `300 MAHAX`            | `600 MAHAX`            | `300 MAHAX`              |
| Charlie | `300 MAHAX`            | `300 MAHAX`            | `600 MAHAX`              |

To achieve multiple levels of delegation, we recommend building off-chain tools or periphery smart-contracts that interface with the current implementation.

## Voting Rewards

Voting rewards are a way to incentivize governance participants to partake in votes and become more active in decisions made within the DAO. A certain budget of `MAHA` is kept aside (coming from [MAHA's monthly inflation](../the-maha-token/distribution.md) that is used for rewards to governance voters).

Voting rewards are given to users who also delegate their power. That is, if you delegate your voting power to `Alice` and `Alice` participates on your behalf and receives `MAHA` rewards, those rewards are distributed between you and `Alice` depending on how much percentage of `MAHA` that was voted was yours.

This example explains a little more in detail. Assume `Alice` delegates her voting power to `Bob` and a `1000 MAHA` reward was given to voters and `Bob` owned `10%` of all the voting power that participated in the governance.

| Person        | Voting Power | Voting Power After Delegation | Rewards for Participation (1000 MAHA) |
| ------------- | ------------ | ----------------------------- | ------------------------------------- |
| Alice         | `750  MAHAX` | `0    MAHAX`                  | `75  MAHA`                            |
| Bob           | `250  MAHAX` | `1000 MAHAX`                  | `25  MAHA`                            |
| Everyone Else | `9000 MAHAX` | `9000 MAHAX`                  | `900 MAHA`                            |

_Voting Rewards are currently calculated off-chain using_ [_merkle proofs_](https://www.webopedia.com/definitions/merkle-proof/) _to maintain lower gas costs. Future implements will execute on-chain in a completely decentralized manner._&#x20;

## FAQs

### Can I delegate to someone and can that person delegate to another person?

Yes. Anybody can delegate their voting power to anyone. However they can only delegate the voting power that they own, not what has been delegated to them.

### Can I delegate half of my voting power to someone?

No. At this moment, delegation is either 0 or 100%. That you can only delegate all your voting powers to one person.

### Can I delegate my governance voting power and my pool voting power separately?

No. At this stage, when you delegate your voting power, your delegate will get rights to both governance proposals and to pool voting gauges.

