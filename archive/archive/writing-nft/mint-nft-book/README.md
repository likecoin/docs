---
description: Publishing eBook as an NFT
---

# Mint NFT Book (beta)

{% hint style="info" %}
### 📣Minting Writing NFT requires LikeCoin, users can get a small amount of LikeCoin from the [faucet](../../../../general-guides/faucet.md) for testing.
{% endhint %}

{% hint style="info" %}
### 📣This instruction requires technical knowledge about running node.js scripe and editing JSON files
{% endhint %}

Publishing an NFT book involves three stages:

1. Preparing the eBook files, NFT book cover, and various data files.
2. Minting the NFT book.
3. Listing the NFT book on Liker Land and sales

The following will provide a detailed explanation of each step.

***

## Prerequisites&#x20;

### Prepare your eBook files&#x20;

You must have your eBook file ready before publishing your NFT book; the file can be in any popular ebook format, such as pdf and epub. This guide will not cover how to make an ebook file.

### Prepare your NFT book covers

You must prepare at least two cover images for your NFT book, one for the listing view and another for the book detail view. The listing view is for the user to browse the NFT book information in-store, and the book detail view is the unique cover of each NFT book.

### Get your "book info" page ready

The book info page is a single page that lists the book information, such as information about the authors and publisher, descriptions and recommendations, etc. It can be any webpage.

### Prepare the metadata

It would be best to have your book metadata as complete as possible before publishing the NFT book. You can continually update the metadata by updating the version of the book ISCN later if necessary, however. Book metadata includes but is not limited to author name, book name, stakeholders and their wallet address, book description, usage terms, etc.&#x20;

### Preparing the data files&#x20;

Get a few sample data files in JSON format under the directory [https://github.com/likecoin/iscn-nft-tools/tree/master/mint-nft](https://github.com/likecoin/iscn-nft-tools/tree/master/mint-nft). You must prepare the necessary data file. The definitions of data files are stated below:

#### iscn.json

| Fields                        | Values                                                                                                                                                                                                                |
| ----------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| contentMetadata → url         | <p>URL of the book information. For example: https://ckxpress.com/moneyverse/<br>It is the link to the “View Content” button in the NFT detail page, under the main NFT image.  </p>                                  |
| contentMetadata → name        | Title of the ISCN                                                                                                                                                                                                     |
| contentMetadata → type        | “Book”                                                                                                                                                                                                                |
| contentMetadata → version     | ISCN version number                                                                                                                                                                                                   |
| contentMetadata → context     | "[http://schema.org/](http://schema.org/)"                                                                                                                                                                            |
| contentMetadata → keywords    | Format: “a,b,c,d”                                                                                                                                                                                                     |
| contentMetadata → usageInfo   | e.g.: CC BY-SA 4.0                                                                                                                                                                                                    |
| contentMetadata → sameAs      | Array of other URL representations of the NFT Book. If the URL ends with `.epub` or `.pdf` a special button for viewing would appear in Liker Land.  e.g.: \["https://url/book.epub", "https://url/book.pdf"]         |
| contentMetadata → description | Description of the ISCN                                                                                                                                                                                               |
| stakeholders                  | list of stakeholder info, e.g. { "contributionType":"[http://schema.org/author](http://schema.org/author)", "entity": { "@id":"like13f4glvg80zvfrrs7utft5p68pct4mcq7t5atf6", "name":"高重建" }, "rewardProportion":"2" } |
| contentFingerprint            | decentralized storage hash, e.g.: "ipfs://QmVsa6WuHLiZtyfwQrFjgxwLvVqMPsvvvusTdCKmTyqkca", "ar://e-bMr7c3O\_sm20zb7X5Vu870Q8b-Pc7eIxmjYXgJmsI”                                                                        |
| recordNotes                   | reserved                                                                                                                                                                                                              |

<figure><img src="../../../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

**nft\_class.json**

| name                                         | NFT title displaying in portfolio/dashboard, class view and detail view.                                                                                                                                                                                                                                                    |
| -------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| description                                  | NFT description displaying in class view and detail view.                                                                                                                                                                                                                                                                   |
| symbol                                       | Reserved                                                                                                                                                                                                                                                                                                                    |
| uri                                          | <p>Optional, default value is null.<br><br>Advance usage: the URI of an API to return an image that serves as the og image of the NFT class, which is displayed in the portfolio/dashboard and class view of liker.land, and may display in detail view as well if nfts.csv and nfts_default.json are not set properly.</p> |
| metadata → image                             | The URL of an image that serves as the og image of the NFT, which is displayed in the portfolio/dashboard and class view of liker.land, and may display in detail view as well if nfts.csv and nfts\_default.json are not set properly.                                                                                     |
| metadata → external\_url                     | <p>The link to the “View Content” button in the NFT detail page, under the main NFT image.  <br>The url field in iscn.json takes preference.</p>                                                                                                                                                                            |
| metadata → message                           | The “creator message” that is appended to every NFT in the same class.                                                                                                                                                                                                                                                      |
| metadata → nft\_meta\_collection\_id         | NFT category, e.g.: nft\_book, nft\_mail, nft\_photo, nft\_illustration etc. Liker Land use this field to decide which section the NFT is displayed.                                                                                                                                                                        |
| metadata → nft\_meta\_collection\_name       | NFT category name                                                                                                                                                                                                                                                                                                           |
| metadata → nft\_meta\_collection\_descrption | NFT category description                                                                                                                                                                                                                                                                                                    |

#### **nfts\_default.json**

| Fields                   | Values                                                                                                                                                                                                                                                                                                                      |
| ------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| uri                      | <p>Optional, default value is null.<br><br>Advance usage: the URI of an API to return an image that serves as the og image of the NFT class, which is displayed in the portfolio/dashboard and class view of liker.land, and may display in detail view as well if nfts.csv and nfts_default.json are not set properly.</p> |
| metadata → name          | default NFT name if the field is not specified in nfts.csv metadata.                                                                                                                                                                                                                                                        |
| metadata → description   | default NFT description if the field is not specified in nfts.csv metadata.                                                                                                                                                                                                                                                 |
| metadata → image         | If image info is not available in nfts.csv, the image will be provided first by this this URI and second by the metadata→image field.                                                                                                                                                                                       |
| metadata → external\_url | <p>The link to the “View Content” button in the NFT detail page, under the main NFT image.  <br>The url field in iscn.json takes preference.</p>                                                                                                                                                                            |

#### nfts.csv

| Fields   | Values                                                                                                                                                                                                                                                                                                                      |
| -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| nftId    | The unique NFT ID under a specific NFT class ID. The system will generate a random ID if it is not specified. Format requirement: [https://docs.like.co/developer/likenft/likecoin-nft-module-spec#mintnft](https://docs.like.co/developer/likenft/likecoin-nft-module-spec#mintnft) .                                      |
| uri      | <p>Optional, default value is null.<br><br>Advance usage: the URI of an API to return an image that serves as the og image of the NFT class, which is displayed in the portfolio/dashboard and class view of liker.land, and may display in detail view as well if nfts.csv and nfts_default.json are not set properly.</p> |
| image    | The URL of an image that serves as the og image of the NFT, which is displayed in the NFT detail view of liker.land.                                                                                                                                                                                                        |
| metadata | Metadata of the NFT image of any related parameter which is expected to be record on chain.                                                                                                                                                                                                                                 |

#### Sample files

{% file src="../../../../.gitbook/assets/iscn.json" %}

{% file src="../../../../.gitbook/assets/nft_class (1).json" %}

{% file src="../../../../.gitbook/assets/nfts.csv" %}

{% file src="../../../../.gitbook/assets/nfts_default.json" %}

For technical details of NFT book, please refer to the below guide:

{% content-ref url="../../../../developer/likenft/writing-nft-1.md" %}
[writing-nft-1.md](../../../../developer/likenft/writing-nft-1.md)
{% endcontent-ref %}

***

## Mint NFT Book

### Step 1: Upload iscn.json and Register ISCN

Please log in to your [Keplr](../../../../general-guides/wallet/keplr/) and select "[Mint NFT](https://likecoin.github.io/nft-book-press/mint-nft)" on [LikeCoin NFT Book Press](https://likecoin.github.io/nft-book-press/). Then click "Connect" in the upper right corner to connect to Keplr.

On the Mint LikeCoin NFT/NFT Book page, select the prepared iscn.json file and click "Choose file" to upload it. After that, click "Create". Keplr will display a pop-up window. The system will register the ISCN based on the provided data. Please click "Approve" to sign and register.

<figure><img src="../../../../.gitbook/assets/Mint NFT Book 1.png" alt=""><figcaption><p>Click "Choose file" to upload iscn.json and then click "Create"</p></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/Mint NFT Book 2.png" alt=""><figcaption><p>Click "Approve" on Keplr to sign and register</p></figcaption></figure>

### Step 2: Create NFT Class

After successfully registering the ISCN, create an NFT Class based on it. Unless you want to set a maximum supply limit, you don't need to fill in the "Max number of supply for the NFT Class (optional)" field. Click "Choose file" to upload the prepared nft\_class.json file. Then click "Create" and sign twice with Keplr by clicking "Approve" to generate the NFT Class.

<figure><img src="../../../../.gitbook/assets/Mint NFT Book 3.png" alt=""><figcaption><p>Click "Choose file" to upload nft_class.json and then click "Create"</p></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/Mint NFT Book 4.png" alt=""><figcaption><p>Click "Approve" twice on Keplr to generate the NFT Class</p></figcaption></figure>

### Step 3: Mint the NFT Book

You need to upload two files: nfts\_default.json and nfts.csv to mint the NFT Book. Please note that the CSV file specifies the actual number of NFTs you want to publish, and you need to enter the same quantity in the "Number of NFT to mint" field. Then click "Create" and sign with Keplr by clicking "Approve" to confirm.

<figure><img src="../../../../.gitbook/assets/Mint NFT Book 5.png" alt=""><figcaption><p>Click "Choose file" to upload nfts_default.json and nfts.csv, enter the Number of NFT to mint, and then click "Approve" on Keplr to sign and confirm</p></figcaption></figure>

### Step 4: Successfully mint the NFT Book

A pop-up window will appear, and you can save the result file. Then return to the page where "Success!" is displayed, indicating NFT Book minted successfully. Click "View your NFT" to check the NFT book in Liker Land.

<figure><img src="../../../../.gitbook/assets/Mint NFT Book 6.png" alt=""><figcaption><p>save the resSave the result file on the pop-up windowsult file</p></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/Mint NFT Book 7.png" alt=""><figcaption><p>Click "View your NFT"</p></figcaption></figure>

Since you have only completed minting and have not made them available for sale, the book quantity will be shown as "Sold out." The next step is to list the NFT books for sale on Liker Land.

<figure><img src="../../../../.gitbook/assets/Mint NFT Book 9.png" alt=""><figcaption><p>View published NFT books at Liker Land</p></figcaption></figure>

***

## Updating eBook File and any Metadata's Version

You may have the need to update the eBook files (epub/pdf) or any metadata, for example, a typical scenario is to include the registered ISCN into the eBook files, and hence you will get new contentFingerprints.   Take this use case as an example, you need to:

1. Add the ISCN information to the eBook files (pdf/epub).
2. Upload the eBook files to IPFS and get the new hash (contentFingerprint).
3. Update the ISCN to replace the old contentFingerprint by the new one.

You can always trace back the information of the old ISCN versions, but Liker Land frontend will display the information of the most updated ISCN version.  &#x20;

Check out the tools to update ISCN below:

{% content-ref url="../../../../general-guides/decentralized-publishing/iscn-browser.md" %}
[iscn-browser.md](../../../../general-guides/decentralized-publishing/iscn-browser.md)
{% endcontent-ref %}

Moreover, please find the ISCN browser tool on testnet [here](https://likecoin-iscn-browser-testnet.netlify.app/).

#### Continue Reading:

{% content-ref url="list-nft-book.md" %}
[list-nft-book.md](list-nft-book.md)
{% endcontent-ref %}
