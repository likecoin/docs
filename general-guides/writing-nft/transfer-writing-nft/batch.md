---
description: Export wallet address of supporters and batch send NFTs to them
---

# Batch send NFT to supporters

**Step 1**: Search for "Collectors" in your own wallet on the [LikeCoin NFT Dashboard](https://likecoin.github.io/likecoin-nft-dashboard/#/).

**Step 2**: Export all data.

**Step 3**: Import the CSV of the data into a spreadsheet tool for sorting and organize the wallet addresses of supporters into a list. There are two method to batch send NFT:

#### Method 1:

* Select "[Send NFTs](https://likecoin.github.io/likecoin-nft-marketplace/tools/send)" in the Tools of [LikeCoin NFT Marketplace](https://likecoin.github.io/likecoin-nft-marketplace/) and log in to Keplr.
* Find the [NFT Class ID](../collect-writing-nft/nft-details.md#nft-class-id) on the Writing NFT that will be distributed to supporters.
* Enter the NFT Class ID into the Send NFTs tool, and enter the supporters’ wallet addresses to the "Recipient Address list" and the "Transfer message", then press "Send" and sign in Keplr to batch send NFTs to supporters.

#### Method 2:

* In [LikeCoin ISCN/NFT Tools](https://likecoin.github.io/iscn-nft-tools/), select "[Send NFT](https://likecoin.github.io/iscn-nft-tools/send-nft)" and log in with Keplr.
* Prepare a CSV file ( see [example](https://github.com/likecoin/iscn-nft-tools/blob/master/send-nft/list\_example.csv) ) containing the wallet addresses, the [Class ID](../collect-writing-nft/nft-details.md#nft-class-id)s of the NFTs to be sent, and the memos, which are the [transfer messages](batch.md#step-2-enter-the-recipients-wallet-address-and-transfer-message). Then click "Send" and sign the transaction in Keplr to mass distribute the NFTs.
