---
description: An overview of how MahaDAO's governance is laid out
---

# Governance Overview

MahaDAO's governance model is designed to keep malicious attackers out of the way and ensure that the project is kept as decentralized as possible.

The model described in this section is designed takes inspiration from best practices from various protocols in creating a governance structure that is:

* Meant to be as decentralized as possible
* Allows for delegation to encourage high voter participation
*   Has a time-lock to ensure that malicious proposals can get rejected/voted in time

    <figure><img src="../.gitbook/assets/image (22).png" alt=""><figcaption><p>A rough summary of how the governance is architected</p></figcaption></figure>

Besides just securing the protocol, governance participants also get additional benefits such as:

* [Voting and earning from pool incentives](pool-voting/)
* [Earning fees from the protocol](earning-fees.md)
* [Boosting their farming rewards](pool-voting/boosting-pools.md)

MahaDAO's governance has various components, each of them briefly explained below.

* **MAHA NFT Locker**: Locks `MAHA` to create NFTs with voting power based on how much and long the MAHA tokens were locked for. (Read: [Locking Maha](locking-mechanism.md))
* **NFT Staker:** A staking contract that stakes a `MAHA` NFT to be used for various aspects of the governance. (Read [Staking NFTs](locking-mechanism.md#staking-nfts))
* **Governance Portal:** A web portal that allows users to create and vote on proposals that change various aspects of the DAO. (Read: [Voting Portal](broken-reference))
* **Time-locks**: A smart-contract that puts all transactions into a queue before they are committed onto the blockchain.
* **Emergency DAO**: A community-owned multi-sig wallet that has the ability to veto any malicious votes. (Read [Emergency DAO](creating-voting-on-proposals.md#emergency-dao))
* **Pool Voter:** A voting contract that votes and determines how much `MAHA` goes to what gauge. (Read [Pool Voting](pool-voting/))
* **Pool Gauge:** A contract that stakes liquidity pool tokens and determines how much `MAHA` rewards should be given out. (Read [Uniswap Staking](pool-voting/uniswap-v3-staking.md))
