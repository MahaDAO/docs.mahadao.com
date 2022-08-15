---
description: This section talks about the locking mechanism behind the MAHAX NFTs
---

# Locking MAHA for NFTs

`MAHAX` is a representation of the voting power a user gets when they lock their `MAHA`. It calculated using two metrics:

* How long is the MAHA locked for?
* How much MAHA is locked?

The goal with this kind of mechanism is to create a fair and decentralized distribution for voting power that gives as much as power for the common man as compared to a whale.&#x20;

In most cases smaller holders will tend to lock their tokens for longer periods of time to get the same amount of voting power as whales who will tend to larger amounts of tokens but for lesser periods of time.&#x20;

This allows us to have participants in the protocol to have the ability to have their voice represented by simply locking their tokens for longer periods of time but with smaller amounts instead.

To get a tutorial on how to vote to lock your MAHA, visit the [Governance Portal Tutorials](governance-portal/staking-maha-for-mahax.md).

## How is MAHAX calculated?

MAHAX is calculated using a simple formula that takes into account time and number of tokens locked.

$$
Amount_{mahax} = (Amount_{maha} * days) / (365 * 4)
$$

The below table showcases an example of how much MAHAX a person receives given 1000 MAHA that is locked across various intervals of time. However note that a user can choose any interval between 2 weeks to 4 years.

| For 1000 MAHA locked | Lock Duration |
| -------------------- | ------------- |
| `1000 MAHAX`         | 4 years       |
| `250 MAHAX`          | 1 year        |
| `127.4 MAHAX`        | 6 month       |
| `63.7 MAHAX`         | 3 month       |
| `21.23 MAHAX`        | 1 month       |
| `4.79 MAHAX`         | 1 week        |

![A graph showcasing the MAHAX power (y-axis) across the number of days locked (x-axis) for 1000 MAHA](<../.gitbook/assets/image (1).png>)

## Voting power that decays over time

Transitioning of power is an important aspect of any future footed governance. Current participants need to give space for newer participants to come forward.&#x20;

First-mover advantages which often leads to governance structures that are centralized to early adopters need to be avoided. Which is why having the voting power decay over time slowly is an important aspect in creating a future-footed governance.

Unless staked, every MAHAX NFT has its voting power decay over time.&#x20;
