---
description: >-
  Questions asked by validators, experience on issues we met during testnet
  upgrade, etc
---

# Miscellaneous

## Halt time and sheungwan-2

The mainnet currently is using Cosmos SDK v0.37.4, which unfortunately doesn't support the `halt-time` option. Therefore, before upgrading to `fotan-1` software, validators need to upgrade the image of their node to the `sheungwan-2` software \(`likecoin/likecoin-chain:sheungwan-2` in Docker Hub\). The `sheungwan-2` software is compatible with the current network, so no proposal or upgrade process is needed.

## Performing machine changes during upgrade

Some validators may want to perform machine changes \(e.g. moving to a higher class machine\) during the chain upgrade. After stopping the node software, they may move the whole `.liked` and `.likecli` folder to the new machine, and see if they can catch up the upgrade process. If not, then they may simply setup a new node using the new software and new genesis state produced during the upgrade process \(see [For other full node operators](for-other-full-node-operators.md)\).

## Managing incidents during upgrade

During the testnet upgrade, we encountered a problem on software bug, resulting in panic when initializing the chain \(see [the recording on the public testnet upgrade](https://www.youtube.com/watch?v=RCt8zkwT_Z4) for details\). Our blockchain developer debugged and provided a genesis file mitigating the problem. However, as validator Rick Mak \(from Oursky\) pointed out, a more decentralized way should be providing procedures for validators to generate the fixed genesis file from the problematic one, instead of providing the genesis file directly. Also, such mitigation may not be suitable for the upgrade, as it is untested and may result in other unexpected and more serious bugs \(e.g. state corruption\). Therefore, in the mainnet upgrade, if we met incidents like this, we would prefer halting the upgrade and restarting the old chain instead of live fixing it.

## Keystore

The new software moved the keystore to the `liked` command, and provided new option for using the OS keystore instead of in file. If you are operating on Linux, then it may not be an issue as the OS keystore is not supported on Linux, so the software will simply fallback to file keystore. However, some validators using Ledger may operate their key on local machine, and for macOS users, the default keystore is the one from the OS. Therefore when migrating the key onto Linux server, users may find that they are not able to find the key from the `.liked` folder. In this case, the `--keyring-backend file` option may help.

