---
description: >-
  How to embed a NFT Widget into a self-hosted WordPress. and publishing post to
  blockchain?
---

# Word3Press

The current hassle to publish articles as NFTs: Creators needed to find ways to save the contents and metadata on decentralized storage such as IPFS or blockchain, before selling them on the NFT marketplaces. Furthermore, they had to purchase several kinds of cryptocurrencies during the process. We have good news for WordPress users: After finishing your articles, you only need one click to publish NFT credentials to blockchain. the whole process just takes one minute to complete within the WordPress editor!

The brand new [LikeCoin Web3Press plugin](https://wordpress.org/plugins/likecoin/) is tailor made for Gutenberg editor, which links up the WordPress website with Web3 by just one click and decentralized publishing can be actualized to the fullest. It's functions include:

* Set the post title and tags as the NFT metadata automatically
* One-click publishing to LikeCoin plus storage at IPFS and Arweave and register [ISCN](../general-guides/decentralized-publishing/what-is-iscn.md).
* On-chain and decentralized storage fees can be paid by LikeCoin in one go
* After minting Writing NFT, a [NFT Widget](../general-guides/writing-nft/collect-writing-nft/nft-widget.md) is automatically embedded at the bottom of each post for readers to [collect Writing NFT](../general-guides/writing-nft/collect-writing-nft/) and Integrate [LikeCoin button](creator/).
* Support [Internet Archive](https://archive.org/) auto backups

## How to install Word3Press <a href="#likecoin" id="likecoin"></a>

Follow the steps:

### Step 1：Login WordPress admin dashboard

Go to the WordPress admin dashboard and login ( For example if your website is www.abc.com, the admin panel address is usually on www.abc.com/wp-admin ).

### Step 2：Start Installing

Click on the Menu on the left, go to "Plugin" and click on "Add New" on top.

![](../.gitbook/assets/wordpress-1-en.png)

### Step 3：Activate Word3Press

Search for "LikeCoin" and find the LikeCoin plugin, click "Install Now" and wait for the system to finish the job, then click "Activate".

<figure><img src="../.gitbook/assets/wordpress 2-en.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/wordpress 3-en.png" alt=""><figcaption></figcaption></figure>

### Step 4：Installation Completed

After installation, there will be an "LikeCoin" option in the menu. Congratulations,  installation is done!

<figure><img src="../.gitbook/assets/wordpress 4-en.png" alt=""><figcaption></figcaption></figure>

## Publishing Writing NFT with Keplr

Please install the [Keplr browser extension](../general-guides/wallet/keplr/) and login before publishing Writing NFT and a small amount of LikeCoin is required. New users can use the [faucet](../general-guides/faucet.md) to get a small amount of LikeCoin to test, or check out how to [buy LikeCoin](../general-guides/trade/buy-likecoin.md).

### Step 1: Register an ISCN

After publishing the article, click "Publish" under Decentralized Publishing.

<figure><img src="../.gitbook/assets/W3Press mint 1.png" alt=""><figcaption></figcaption></figure>

Click "Next" on the pop-up windows.

<figure><img src="../.gitbook/assets/W3Press mint 2.png" alt=""><figcaption></figcaption></figure>

Click "Approve" on the Keplr pop-up window to start uploading content to IPFS and Arweave.

<figure><img src="../.gitbook/assets/W3Press mint 3.png" alt=""><figcaption></figcaption></figure>

Please do not close the window during uploading.

<figure><img src="../.gitbook/assets/W3Press mint 4.png" alt=""><figcaption></figcaption></figure>

Click "Approve" on the Keplr pop-up window to register the content metadata to the LikeCoin chain.

<figure><img src="../.gitbook/assets/W3Press mint 5.png" alt=""><figcaption></figcaption></figure>

Please do not close the window during registration.

<figure><img src="../.gitbook/assets/W3Press mint 6.png" alt=""><figcaption></figcaption></figure>

### Step 2: Minting Writing NFT

ISCN has been successfully registered, click "Continue to mint Writing NFTs".

<figure><img src="../.gitbook/assets/W3Press mint 7.png" alt=""><figcaption></figcaption></figure>

Preview your Writing NFT. If you want to add or change the cover of the Writing NFT, click ":pencil2:". If you don't need to change it / the article has no picture, the default OG picture of the article will be displayed / no picture will be displayed. Click "Next" to continue.

<figure><img src="../.gitbook/assets/W3Press mint 8.png" alt=""><figcaption></figcaption></figure>

You can also enter the Creator message. Click "Add message to your collectors" and enter a message. Click "Next" to continue.

<figure><img src="../.gitbook/assets/W3Press mint 9.png" alt=""><figcaption></figcaption></figure>

Click "Approve" on all the Keplr pop-up window during the minting process.

<figure><img src="../.gitbook/assets/W3Press mint 10.png" alt=""><figcaption></figcaption></figure>

### Step 3: Complete minting

Complete! appears and the Writing NFT has been minted successfully. Click "View NFT" to preview your Writing NFT.

<figure><img src="../.gitbook/assets/W3Press mint 11.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/W3Press mint 12.png" alt=""><figcaption></figcaption></figure>

You can also check out your creations on the Liker Land [My Dashboard](../general-guides/writing-nft/dashboard.md).

<figure><img src="../.gitbook/assets/W3Press mint 13-en.png" alt=""><figcaption></figcaption></figure>

## Configuring Liker ID

Before configuring the LikeCoin plugin, please [register a Liker ID](liker-id/).

On the menu, select the "LikeCoin" plugin and select "Liker ID", then fill in the Liker ID and click "Confirm".

<figure><img src="../.gitbook/assets/wordpress 5.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/wordpress 6.png" alt=""><figcaption></figcaption></figure>

* Website Liker ID - If the website has more than one author, the Liker ID will be displayed as default on the author's article if he/she has not set up his/her own Liker ID.
* Your Liker ID - Set up your own Liker ID. And after successfully adding a new user on the WordPress website, the new user can log in with their WordPress account, set their Liker ID and display their own NFT Widget / Like button.

## Other Important features

### Publish to Internet Archive

Fill in the Internet Archive S3 API Key and synchronize the article to Internet Archive when it is published.

<figure><img src="../.gitbook/assets/wordpress 11.png" alt=""><figcaption></figcaption></figure>

### Publish to Matters

From now on you can sync your WordPress article to Matters. Simply login your Matters email and password then write an article, the content will be on Matters as well.

There are 3 options:

* Auto save draft to Matters - Posts drafted will be sync to your Matters's draft box  .
* Auto publish post to Matters - A copy of the post will be automatically published to Matter when you publish a post on your WordPress site.
* Add post link in footer - Link of the original WordPress post will be added to the post in Matters.

By publishing on Matters, your articles will be stored to the distributed InterPlanetary File System (IPFS) nodes.

### Web Monetization

Web monetization is now enabled on LikeCoin WordPress plugin. It allows content creators to receive streaming money when [Coil](https://coil.com/) subscribers visit the website.

<figure><img src="../.gitbook/assets/wordpress 12.png" alt=""><figcaption></figcaption></figure>

## Other Settings

### LikeCoin Widget

* Show in Posts: After configuring Liker ID, default to display NFT Widget / LikeCoin button button underneath each article
* Show in Pages: Display like button in WordPress pages

{% hint style="info" %}
**Config NFT Widget / LikeCoin button to appear in anywhere of the articles**

You can also use shortcode \[likecoin] to display extra NFT Widget / LikeCoin buttons.
{% endhint %}

### ISCN Badge

After the article is published to ISCN, you can set it if you want to display the ISCN badge. The options are "Not shown", "Light Mode" and "Dark Mode". Select and click "Confirm".

<figure><img src="../.gitbook/assets/wordpress 8.png" alt=""><figcaption></figcaption></figure>

### LikeCoin widget advanced settings

Customize NFT Widget / Appreciation button display settings for each article.

<figure><img src="../.gitbook/assets/wordpress 9.png" alt=""><figcaption></figcaption></figure>

