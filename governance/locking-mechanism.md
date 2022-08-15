---
description: This section talks about the locking mechanism behind the MAHAX NFTs
---

# Locking MAHA for NFTs

`MAHAX` is a representation of the voting power a user gets when they lock their `MAHA`. It is calculated using two metrics:

* How long is the MAHA locked for?
* How much MAHA is locked?

The goal with this kind of mechanism is to create a fair and decentralized distribution for voting power that gives as much as power for the common man as compared to a whale.&#x20;

In most cases smaller holders will tend to lock their tokens for longer periods of time to get the same amount of voting power as whales who will tend to larger amounts of tokens but for lesser periods of time. This allows participants to have their voice recognized better by simply locking their tokens for longer periods of time.

![A screenshot of the lock screen that allows a user to choose how much MAHA they'd like to lock, for how long and if they'd like to stake their NFT as well.](../.gitbook/assets/image.png)

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

One of the most important properties of a true democracy is the right of members to secede from the group.

Transitioning of power is an important aspect of any future footed governance. Current participants need to give space for newer participants to come forward.&#x20;

First-mover advantages which often leads to governance structures that are centralized to early adopters makes it harder for power to successful secede. Which is why having the voting power decay over time slowly is an important aspect in creating a future-footed governance.

Unless staked, every `MAHAX` NFT has its voting power decay over time if it is not participating in active governance. This creates an incentive for holders to not just stake their NFTs but also have voting power that secedes if unstaked.

## Staking NFTs

`MAHAX` NFTs unless staked have no important or functionality within the governance platform. These include benefits like earning fees, exercising voting power and providing legitimacy to a group of individuals.

Once a NFT is staked:

* It cannot be moved to another wallet address and its voting power (`MAHAX` balance) is frozen.
* It cannot also be traded on third-party market places such as [OpenSea](https://opensea.io/).&#x20;
* It can however be unstaked at any point in time.

Unstaking a NFT allows the NFTs removes all the restrictions above, but at the same time unfreezes the voting power (`MAHAX` balance) which starts to decay over time.

To claim the underlying `MAHA` behind a NFT or to merge a NFT with another NFT, they both need to be unstaked.

## Merging NFTs

`MAHAX` NFTs can be merged into one another, allowing for voting power to get combined and a greater MAHAX balance.

When a NFT is merged the following steps take place:

* A check is run if both NFTs are staked or not. Merging only happens if both NFTs are unstaked.
* The first NFT is burnt
* The second NFT is updated with the combined underlying MAHA balances for both NFTs
* The second NFT is updated with a lock duration that is longer of the two NFTs

Merging NFTs creates scarcity of NFT pieces and more powerful NFTs that have more voting power than before.

## Governance

The MAHA NFT locker has various parameters that can be controlled by Governance:

* **The minimum amount of MAHA required for a lock:** This is currently set at 99 MAHAX (or rather 100 MAHA locked for 4 years). Ideally if the cost of minting a NFT becomes higher, lowering the minimum mint floor will allow for more NFTs to be minted as the cost of minting a piece becomes lower.
* **NFT minting privileges:** Currently only used for the migration of NTFs from the polygon, this function allows addresses/contracts to mint NFTs at will. Only to be used in rare scenarios.
