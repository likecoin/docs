---
description: >-
  Transfer, Delegate, Undelegate, Redelegate and Withdraw Rewards requires
  transaction fees
---

# Transaction Fee

Since March 9, 2021, the [LikeCoin chain](https://www.mintscan.io/likecoin) has followed the [Cosmos Hub](https://hub.cosmos.network/) upgrades and added the Gas parameter, which is the same as other projects in the Cosmos Hub network. Gas refers to the unit that measures the amount of computational effort required to execute specific operations on the blockchain. Not only on Cosmos Hub, but other blockchain platforms such as Ethereum also use Gas as the unit of measurement.

## The importance of transaction fee

The LikeCoin chain charges a Gas fee, also known as a transaction fee, according to the computational resources required to successfully conduct a transaction, which is calculated in Gas. In short, transaction fees help keep the LikeCoin chain secure. By requiring a fee for every computation executed on the network, we prevent actors from spamming the network. In order to prevent accidental or hostile infinite loops or other computational wastage in code, each transaction is required to set a limit to how many computational steps of code execution it can use. The fundamental unit of computation is "Gas".

## Estimation of transaction fee

Transaction fees are calculated according to the computational steps of code execution required for each transaction. As the network situation is different during each transaction, the following are estimations of scenarios:

* [LIKE pay](like-pay.md): Around 0.16 LIKE
* [Delegate](../stake/delegation-of-likecoin/): Around 0.32 LIKE
* [Undelegate](../stake/undelegation-of-likecoin/): Around 0.4 LIKE&#x20;
* [Redelegate](../stake/redelegation-of-likecoin/): Around 0.55 LIKE
* [Withdraw Rewards](../stake/delegation-of-likecoin/#step-3-relax-and-withdraw-rewards): Around 1.25 LIKE

Click on "Details" in the Liker Land app and web during LIKE pay, delegate, undelegate, redelegate, and withdraw rewards to check the estimated transaction fee."

![Click on "Details" and check the estimated transaction fee](../../.gitbook/assets/like-pay-4-en.png)

![Check the current transaction fee](../../.gitbook/assets/1620197765521.png)

## Please leave transaction fee in your wallet

{% hint style="danger" %}
It is suggested to leave around 2 to 10 LikeCoin as a transaction fee in your wallet. If there is not enough LikeCoin to complete the transaction and it fails, the transaction fee used in the attempt will not be returned.
{% endhint %}

You may not be able to complete the transaction in these marginal cases:

* You are not able to transfer all the LikeCoin out of a wallet because you have to leave some LikeCoin behind to pay the transaction fee. If your wallet has 1 LIKE left, the highest amount to transfer out is around 0.94 LIKE.
* You have delegated all the LikeCoin and cannot undelegate, as a small amount of LIKE has to be prepared to pay for the transaction fee. Under the same situation, you are able to delegate all the LikeCoin out of a wallet.
* Please ensure that you have enough transaction fee for reward withdrawal.

## Who gets the transaction fee?

Validators of the LikeCoin chain operate a set of servers 24x7 to validate all transactions of Likers, including token transfers, content publishing, voting, etc. The validator's rewards for recording all transactions come from inflation and when setting up the node in servers, they can set up minimum gas price parameters to decide the basic requirement of each computational step. Delegators get rewards from validators as the delegation of LikeCoin helps to validate transactions. The rewards for the validator and delegator are called block rewards and it comes from the inflation and transaction fee after deducting community pool taxes from the transaction of each block. The block rewards of a validator depend on the commission rate set by themselves. Therefore, the transaction fee from LikeCoin chain users is split for each stakeholder and community pool taxes according to the proportion and is not charged by the LikeCoin team.
