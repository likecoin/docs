---
description: After the LikeCoin v2.0.0 LaiChiKok Prefix Upgrade
---

# New LikeCoin address prefix "like" - FAQ

## What is wallet address prefix?

The Cosmos ecosystem encourages each blockchain to focus on a single application. Each blockchain will define the address format of its native token with a specific prefix. It is not a mandatory requirement but each blockchain will have its own address format. For example, the Cosmos Hub address starts with “cosmos”, Osmosis with “osmo”, Juno with “juno”, etc.

## Why didn’t LikeCoin use “like” as its address prefix?

When LikeCoin migrated to Cosmos, the Cosmos Ecosystem had just started, and the address prefixes format had not yet been formularized. The LikeCoin founding team chose “cosmos” as the wallet address prefix of $LIKE at that time which was the same as the Cosmos native token $ATOM. But after two years, we should follow the consensus of the Cosmos ecosystem and change the prefix to the “like”.

## What is the advantage of using “like” as address prefix?

Many Cosmos ecosystem applications, including Dapps or API rely on the prefix to identify which blockchain the address belongs to. Both Cosmos Hub and LikeCoin addresses start with the “cosmos” string therefore they cannot be easily distinguished and increases the difficulty of integrating LikeCoin with other projects, such as wallets, exchanges, blockchain browsers, etc. A lot of extra effort is needed to integrate LikeCoin.

The change of LikeCoin address format from the “cosmos” prefix (referred as the “old format”) to the “like” prefix (referred as the “new format”) will speed up the integration of LikeCoin with other Cosmos applications and hence better synergy.

## What is the impact of changing prefix on existing users?

* With the new format LikeCoin address, you can still review, send and receive transactions on Dapps that support the old format.
* Although “backward compatibility” of the new format will be available for a certain time, applications related to LikeCoin will gradually support the new format, and the old format will be phased out eventually.
* On some Dapps, users may need to manually reconfigure it in order to use the new format, such as Keplr.

{% embed url="https://www.youtube.com/watch?v=CPXY9A42zBo" %}
Configure Keplr to use the new LikeCoin wallet prefix (“like”)
{% endembed %}

## What if I accidentally send LikeCoin to an old format address?

The old format and the new format address are one-to-one pointing to the same wallet. Therefore, LikeCoins in the old and new addresses format are also the same asset, and LikeCoin sent to addresses in the old format can also be found in the new address. However if the backward compatibility function of Dapp in the application interface is not perfect enough, it may cause some functions to not able to work properly during operation,

But the bottom line is: as long as you have the private key that generates the address, you still have full control over your asset.

## Check if the exchange supports the new format

When depositing LikeCoin to exchanges, especially centralized exchange, please pay attention and check out if the exchange has supported the new format. The exchange may not fully support the new format resulting in deposit and withdrawal failure.

When depositing to a centralized exchange, the private key of the deposit address is owned by the exchange, users must have assistance from the exchange to control the assets, please pay attention.

## Tool to check the mapping of new/old addresses

You may still need to check with the old wallet address in some past transaction records. You can always check the new/old address mapping in LikeCoin Discord [#translate-wallet-prefix](../community/translate-wallet-prefix.md) channel. For example you can get the corresponding new address by entering “/translate cosmosxxxxxx”, or vice versa, to get the corresponding old address by entering “/translate likexxxxxx”.

#### To Learn More

[LikeCoin New Address Format: The Story of “like1” | LikeCoin Update](https://blog.like.co/likecoin-newsletter-like1-story/)
