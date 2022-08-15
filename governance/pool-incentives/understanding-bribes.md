---
description: >-
  This section talks more about Bribes and how it can be used to incentivize
  voting for MAHA rewards.
---

# Understanding Bribes

Gauge bribes are natively supported by the protocol, Bribes inherit from Gauges and are automatically adjusted on votes.

Users that voted can claim their bribes via calling `function getReward(address token) public`

Fees accrued by `Gauges` are distributed to `Bribes`

## FAQs

### If I have delegated my voting power, will I still receive bribe rewards?

While we do encourage inactive participants to delegate their voting power to more active participants, the distribution of rewards as of now cannot be delegate if the votes have been delegated.

That is, if you have delegated your voting power to a delegate and that delegate votes for a pool that has an active bribe, all rewards go to the delegate instead to you. It is up-to the delegate to distribute the bribes pro-actively to you.

_(Future implementations of governance will find ways to distribute bribes properly to users who have delegated their power)._
