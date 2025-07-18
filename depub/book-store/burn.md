---
description: Remove the published ebook
---

# Burn ebook

{% include "../../.gitbook/includes/warning.md" %}

If you wish to remove a published ebook, keep in mind that the ebook cannot be entirely deleted once it's "printed". The only viable method is to "abandon" it. Here's the step-by-step process:

* Open a new wallet address not publicly disclosed
* Send all NFTs slated for abandonment to this new "trash can" wallet address
* Transfer the ownership of ISCN to the new address to officially abandon the ebook.

## Step 1: Prepare a CSV file

Given that multiple NFTs are typically minted when creating an ebook, using the Liker Land [Transfer Writing NFT](../transfer-nft/) function to send one NFT at a time is inefficient. It's recommended to utilize the LikeCoin ISCN/NFT Tools for batch sending. Begin by preparing a CSV file. Download a sample here:

[https://github.com/likecoin/iscn-nft-tools/blob/master/send-nft/list\_example.csv](https://github.com/likecoin/iscn-nft-tools/blob/master/send-nft/list_example.csv)

Enter the trash can address in the address column, and input the NFT Class ID of the ebook you want to abandon in the classid. If, for example, you have 100 NFTs to dispose of, the CSV file will have 100 columns of duplicate data.

<figure><img src="../../.gitbook/assets/Burn NFT Book 1.png" alt=""><figcaption><p>CSV file sample</p></figcaption></figure>

## Step 2: Use Liker Land BookPress to batch NFT to the trash can address

Visit the [Liker Land BookPress](https://publish.liker.land/) website and click on "[LikeCoin ISCN/NFT Tools](https://likecoin.github.io/iscn-nft-tools/)".

<figure><img src="../../.gitbook/assets/Burn NFT Book 2.png" alt=""><figcaption><p>Click "LikeCoin ISCN/NFT Tools"</p></figcaption></figure>

On the [LikeCoin ISCN/NFT Tools](https://likecoin.github.io/iscn-nft-tools/) website, click "Connect" in the upper right corner to link the wallet, then click "[Send NFT](https://likecoin.github.io/iscn-nft-tools/send-nft)".

<figure><img src="../../.gitbook/assets/Burn NFT Book 3.png" alt=""><figcaption><p>Click "Send NFT"</p></figcaption></figure>

Upload the CSV by clicking "Choose File". Confirm the CSV content in the Summary, and click "Send" after ensuring correctness. Confirm the NFT send in Keplr.

<figure><img src="../../.gitbook/assets/Burn NFT Book 4.png" alt=""><figcaption><p>Click "Choose File" upload the CSV and click "Send"</p></figcaption></figure>

Once complete, the Result page will confirm the successful transfer of NFTs.

<figure><img src="../../.gitbook/assets/Burn NFT Book 5.png" alt=""><figcaption></figcaption></figure>

## Step 3: Transfer ISCN ownership to the trash can address

Finally, go to the ISCN Browser tool website, click "Connect" to link the wallet, and search for the ISCN of the ebook in the Search bar.

<figure><img src="../../.gitbook/assets/Burn NFT Book 6.png" alt=""><figcaption><p> Click "Connect" to link the wallet, and search for the ISCN</p></figcaption></figure>

Once found, click "Transfer".

<figure><img src="../../.gitbook/assets/Burn NFT Book 7.png" alt=""><figcaption><p>Click "Transfer"</p></figcaption></figure>

Enter the trash can address in "Transfer to", click "Transfer", and confirm in Keplr to transfer the ISCN ownership to the trash can address.

<figure><img src="../../.gitbook/assets/Burn NFT Book 8.png" alt=""><figcaption><p>Enter the trash can address in "Transfer to" and click "Transfer"</p></figcaption></figure>

Following these steps, the abandoned book will no longer appear on your Liker Land [Bookshelf](../liker-land/bookshelf.md).
