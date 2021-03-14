---
description: >-
  Currently the transaction fee required to LIKE pay is around 0.059 LIKE, which
  is about US$0.0006. The amount is too less and don't worry about it!
---

# LikeCoin Transaction Fee

Since March 9 2021, LikeCoin chain followed Cosmos Hub upgrades and added the Gas parameter, and stayed the same as other projects in the Cosmos Hub network. Gas refers to the unit that measures the amount of computational effort required to execute specific operations on the blockchain. No only on Cosmos Hub, other blockchain platforms such as Ethereum also use Gas as the unit of measurement.

### The importance of transaction fee

LikeCoin chain charges Gas fee or name it as transaction fee according to the computational resources required calculated in Gas to successfully conduct a transaction. In short, transaction fees help keep the LikeCoin chain secure. By requiring a fee for every computation executed on the network, we prevent actors from spamming the network. In order to prevent accidental or hostile infinite loops or other computational wastage in code, each transaction is required to set a limit to how many computational steps of code execution it can use. The fundamental unit of computation is "Gas".

### Estimation of transaction fee

Transaction fee is calculated according to the computational steps of code execution required for each transaction. As the network situation is difference during each transaction, the below are estimation of each scenario:

* LIKE pay: Around 0.059 LIKE
* Delegate: Around 0.19 LIKE
* Undelegate: Around 0.32 LIKE 
* Redelegate: Around 0.48 LIKE
* Withdraw Rewards: Around 1.25 LIKE

Clicks on "Details" in the Liker Land app during LIKE pay, delegate, undelegate, redelegate and withdraw rewards and check the estimated transaction fee.

![](../../.gitbook/assets/like-pay-4-en.png)

### Important

{% hint style="danger" %}
Suggested to leave around 2 to 10 LikeCoin as transaction fee in your wallet. If there is not enough LikeCoin to complete the transaction and it is failed, the transaction fee used in the attempt will not be returned.
{% endhint %}

You may not be able complete the transaction in these marginal cases:

* You are not able to transfer all the LikeCoin out of a wallet, it is because you have to leave some LikeCoin behind to pay the transaction fee. If your wallet has 1 LIKE left, the highest amount to transfer out is around 0.94 LIKE.
* Delegated all the LikeCoin and cannot undelegate, as a small amount of LIKE has to be prepared to pay for the transaction fee. Under the same situation, you are able to delegate all the LikeCon out of a wallet.
* Please ensure that you have enough transaction fee for reward withdrawal.

### Who gets the transaction fee?

Validators of LikeCoin chain operate a set of servers 24x7 to validate all transactions of Likers, including token transfers, content publishing, voting and etc. Validator's rewards for recording all transactions is from inflation and when setting up the node in servers they can set up min-gas-price parameters to decide the basic requirement of each computational step. Delegators get rewards from validators as delegation of LikeCoin helps to validate transactions. The rewards for validator and delegator are called block reward and it comes from the inflation and transaction fee after deducting community pool taxes of the transaction of each block. The block rewards of a validator can get depends on the Commission rate set by themselves. Therefore the transaction fee form LikeCoin chain users are splitted for each stakeholders and community pool taxes according to proportion, and is not charged by the LikeCoin foundation.  


