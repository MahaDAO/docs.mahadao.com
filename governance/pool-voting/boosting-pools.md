---
description: >-
  This page explains how a user can boost their rewards by up-to 5x by holding a
  MAHA lock
---

# Boosting Pools

In order to incentivize users to participate in governance and additionally create stickiness for liquidity, we implement the following mechanism.&#x20;

A user’s balance, counted in the gauge, gets boosted by users locking `MAHA` tokens in the [NFT Locker](../locking-mechanism.md), depending on their `MAHAX` voting power.&#x20;

$$
liquidty_{boosted}=min(0.2 *liquidty_{initial}+0.8\frac{mahax_{user}}{mahax_{supply}}, liquidty_{initial})
$$

The value of $$mahax_{user}$$ is taken at the time the user performs any action (deposit, withdrawal, withdrawal of `MAHA` tokens) and is applied until the next action this user performs.

If no liquidity stakers have any `MAHAX`, then the `MAHA` emissions will simply be distributed proportionally to the liquidity ($$liquidity_{initial}$$) each one of them provided.&#x20;

However, if a user [locks enough MAHA](../locking-mechanism.md), they are able to boost their `MAHA` rewards by a factor of 5 (reducing it slightly for all users who are not doing that).

Since [voting power decreases with time](broken-reference), it is favorable for users to apply a boost and do no further actions until they lock more tokens. However, once the lock expires, anyone can “kick” the user by creating a checkpoint for that user and, essentially, resetting the user to no boost if they have no voting power at that point already.
