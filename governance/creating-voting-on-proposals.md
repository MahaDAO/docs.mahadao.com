---
description: This section explains how to create proposals and how to vote on them.
---

# Creating/Voting on Proposals

Creating and voting on proposals is currently handled by Tally, a frontend platform for DAO looking to manage their governance. Tally provides a dashboard, interfaces for creating proposals and an interface to vote on them as well.

Every user that intends to create a proposal must have a minimum balance of 250 MAHAX with them (this can however be changed by governance). And should ideally conduct a discussion with the community by creating a thread on [discuss.mahadao.com](https://discuss.mahadao.com/) under the proposal's category on what the proposal will execute upon.

{% embed url="https://discuss.mahadao.com/c/governance/10" %}
Every proposal before passed onto the governance portal should be discussed with the community before being put up for vote.
{% endembed %}

Any proposal that is passed onto the governance portal without having discussed at length by the community at first could have malicious intent and should get voted against by DAO members.&#x20;

### Emergency DAO

As a measure of last resort, in the event that a malicious proposal has gotten itself voted in and is now queued into the timelock, an Emergency DAO exists with special abilities to veto any malicious proposal that might impact the protocol.

The Emergency DAO is a multi-sig wallet consisting of long-term community members who have the best interest for the protocol and look to veto any malicious proposals until the protocol stays decentralized enough.

Besides veto-ing proposals, the Emergency DAO members have no other power.

{% hint style="warning" %}
The Emergency DAO will get dissolved once the protocol becomes sufficiently decentralized.
{% endhint %}

## Governance&#x20;

The governance portal itself has various parameters that can be changed via a vote. This includes:

* **Proposal Threshold:** The amount of consensus needed for a proposal to pass. This is currently set at 60%
* **Minimum Balance for Creation of a Proposal:** The minimum balance a wallet needs for it to create a proposal. This is currently set at 250 MAHAX.
* **Vote Delay:** The amount of time where a vote can get cancelled by the proposer before it goes live. This is currently set at 1 day.
* **Voting Period:** The amount of time where a vote is live and is voted upon by participants. This is currently set at 4 days.
* **Timelock Period**: The amount of time a successfully voted proposal is kept in the Timelock before it is executed. This is set at 12 days.