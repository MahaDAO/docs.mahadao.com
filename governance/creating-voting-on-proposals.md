---
description: This section explains how to create proposals and how to vote on them.
---

# Creating/Voting on Proposals

{% hint style="info" %}
Creating Proposals, Voting and Executing Proposals are handled by the [`Governor`](https://github.com/MahaDAO/governance-contracts/blob/master/contracts/MAHAXGovernor.sol) contract which is deployed at [0xFfEC018583152aB5f056c5323f1f68b701bF1Bc5](https://etherscan.io/address/0xffec018583152ab5f056c5323f1f68b701bf1bc5)
{% endhint %}

Creating and voting on proposals is currently handled by [Tally](https://www.tally.xyz/governance/eip155:1:0xFfEC018583152aB5f056c5323f1f68b701bF1Bc5), a frontend platform for DAO looking to manage their governance. Tally provides a dashboard, interfaces for creating proposals, and an interface to vote on them as well.

A user who intends to create a proposal must have a minimum balance of `250 MAHAX` with them (this can be changed by governance). And should ideally conduct a discussion with the community by creating a thread on [discuss.mahadao.com](https://discuss.mahadao.com/) under the proposal's category on what the proposal will execute upon.

{% embed url="https://discuss.mahadao.com/c/governance/10" %}
Every proposal before passed onto the governance portal should be discussed with the community before being put up for vote.
{% endembed %}

Any proposal passed onto the governance portal without having been discussed at length by the community at first could have malicious intent and should get voted against by DAO members.&#x20;

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption><p>An example of a live vote on Tally, where MAHAX NFT voters came together and voted to initialize the protocol </p></figcaption></figure>

{% embed url="https://www.tally.xyz/governance/eip155:1:0xFfEC018583152aB5f056c5323f1f68b701bF1Bc5" %}
The MahaDAO tally webpage
{% endembed %}

Once a proposal is discussed at length by the community, an on-chain proposal is created using Tally's frontend, allowing for DAO members to start voting on the proposal.

## Emergency DAO

{% hint style="info" %}
The Emergency DAO is currently deployed as a Gnosis Safe here [0x516bd18Ba17f70f08C8C91fE7F9Ee2105DC275d2](https://gnosis-safe.io/app/eth:0x516bd18Ba17f70f08C8C91fE7F9Ee2105DC275d2/home)
{% endhint %}

As a measure of last resort, in the event that a malicious proposal has gotten itself voted in and is now queued into the timelock, an Emergency DAO exists with special abilities to veto any malicious proposal that might impact the protocol.

The Emergency DAO is a multi-sig wallet consisting of long-term community members who have the best interest of the protocol and look to veto any malicious proposals until the protocol stays decentralized enough.

Besides veto-ing proposals, the Emergency DAO members have no other powers.

{% hint style="warning" %}
The Emergency DAO will get dissolved once the protocol becomes sufficiently decentralized.
{% endhint %}

## Timelock

{% hint style="info" %}
The Timelock where all proposal execution parameters are executed is currently deployed at [0xd9333e02a4d85611d0f0498b858b2ae3c29de6fb](https://etherscan.io/address/0xd9333e02a4d85611d0f0498b858b2ae3c29de6fb#code) with a minimum delay of `12 days` for every action.&#x20;
{% endhint %}

An important aspect of governance is ensuring that all actions are time-locked so as to allow the community enough time to propose and vote against (or veto) a proposal before it gets executed.

With a 12 day timelock and a 4 day voting period, this gives the community enough timeframe to veto a vote before it becomes active. This becomes especially relevant when the Emergency DAO is dissolved and there is no way to veto existing proposals.

The reason for having a timelock is to ensure that bad-actors who manage to acquire enough voting power to approve a proposal get discovered by having their actions go through a 12 day delay.&#x20;

_(To avoid a situation similar to the_ [_Beanstalk h_ack](https://cointelegraph.com/news/beanstalk-farms-loses-182m-in-defi-governance-exploit)_)_

## Governance Parameters

The governance portal itself has various parameters that can be changed via a vote. This includes:

* **Proposal Threshold:** The amount of consensus needed for a proposal to pass. This is currently set at 60%
* **Minimum Balance for Creation of a Proposal:** The minimum balance a wallet needs for it to create a proposal. This is currently set at 250 `MAHAX`.
* **Vote Delay:** The amount of time where a vote can get canceled by the proposer before it goes live. This is currently set at 1 day.
* **Voting Period:** The amount of time where a vote is live and is voted upon by participants. This is currently set at 4 days.
* **Timelock Period**: The amount of time a successfully voted proposal is kept in the Timelock before it is executed. This is set at 12 days.
