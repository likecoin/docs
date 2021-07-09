---
description: The Public Testnet is a preview of what the LikeCoin Mainnet will be.
---

# Overview

The Public Testnet is a preview of what the LikeCoin Mainnet will be.

The Testnet aims to provide a platform for validators to have rehearsal on upgrading the chain to FoTan. The main goal is to let validators get used to the upgrade procedures, so the upgrade of Mainnet can be more fluent. It also helps to discover software issues early before the Mainnet upgrade.

The Testnet also acts as a platform for developers to test chain features and APIs and could be reused in future upgrades for rehearsal.

## What are we going to do in the upgrade?

#### Basic idea

* to set up a completely new chain starting from block 1 while preserving necessary data
  * chain data: application state \(balance, delegations, ...\)
    * blocks and transactions are abandoned
  * validator's personal data: private keys, address books, node config files

#### Application state

* which application state?
  * the snapshot at a certain time which validators have consensus \(e.g. 2021-01-01 00:00:00 UTC\)
  * validators consensus: determinned by proposal
* changes
  * chain ID
    * changing the chain ID so old chain transactions could not be replayed
  * parameters for new modules
    * ISCN registry name
    * ISCN fee per byte
  * default states for new modules
    * e.g. ISCN records \(an empty list since there is no previous records\)
  * some differences from old software to new software
    * e.g. genesis format changes in accounts
    * handled by the migration software
* how?
  * export by old chain software
  * then migrate by new chain software
    * input new chain ID and parameters
    * also input the new genesis time

