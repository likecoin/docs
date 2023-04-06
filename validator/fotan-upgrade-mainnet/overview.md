---
description: The Public Testnet is a preview of what the LikeCoin FoTan Mainnet will be.
---

# Overview

## Introduction

The Public Testnet is a preview of what the LikeCoin FoTan Mainnet will be.

The Testnet aims to provide a platform for validators to have rehearsal on upgrading the chain to FoTan. The main goal is to let validators get used to the upgrade procedures, so the upgrade of Mainnet can be more fluent. It also helps to discover software issues early before the Mainnet upgrade.

The Testnet also acts as a platform for developers to test chain features and APIs and could be reused in future upgrades for rehearsal.&#x20;

{% hint style="warning" %}
:man\_mage: **Participating validators are expected to keep the Testnet running.**
{% endhint %}

## What are we going to do in the upgrade?

### Basic idea

* To set up a completely new chain starting from block 1 while preserving necessary data
  * Chain data: application state (balance, delegations, ...)
    * blocks and transactions are abandoned and aggregated into one final state for genesis
  * Validator's personal data: private keys, address books, node config files

### Application state

#### Which application state to upgrade from?

* The snapshot at a certain time which validators have consensus (e.g. 2021-01-01 00:00:00 UTC)
* Such consensus would be determined by the proposal

#### Changes required

* Chain ID
  * Changing the chain ID, so old chain transactions could not be replayed
* Parameters for new modules
  * ISCN registry name
  * ISCN fee per byte
* Default states for new modules
  * e.g. ISCN records (an empty list since there is no previous records)
* Some differences from old software to new software
  * e.g. genesis format changes in accounts
  * handled by the migration software

#### How do we create the application state to genesis?

* Export by old chain software
* Then migrated to by new chain software
  * Input new chain ID and parameters
  * Also input the new genesis time
