---
description: Publishing eBook as an NFT
---

# Mint NFT Book (beta)

### 📣Minting Writing NFT requires LikeCoin, users can get a small amount of LikeCoin from the [faucet](../faucet.md) for testing.

### 📣This instruction requires technical knowledge about running node.js scripe and editing JSON files

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

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

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

{% file src="../../.gitbook/assets/iscn.json" %}

{% file src="../../.gitbook/assets/nft_class (1).json" %}

{% file src="../../.gitbook/assets/nfts.csv" %}

{% file src="../../.gitbook/assets/nfts_default.json" %}

For technical details of NFT book, please refer to the below guide:

{% content-ref url="../../developer/likenft/writing-nft-1.md" %}
[writing-nft-1.md](../../developer/likenft/writing-nft-1.md)
{% endcontent-ref %}

## Mint NFT Book

### Method 1: Publishing NFT Books using Mint LikeCoin NFT/NFT Book

#### Step 1: Upload iscn.json and Register ISCN

Please log in to your [Keplr](../wallet/keplr/) and select MINT NFT on LikeCoin NFT Book Press. Then click "Connect" in the upper right corner to connect to Keplr.

On the Mint LikeCoin NFT/NFT Book page, select the prepared iscn.json file and click "Choose file" to upload it. After that, click "Create". Keplr will display a pop-up window. The system will register the ISCN based on the provided data. Please click "Approve" to sign and register.

<figure><img src="../../.gitbook/assets/Mint NFT Book 1.png" alt=""><figcaption><p>Click "Choose file" to upload iscn.json and then click "Create"</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/Mint NFT Book 2.png" alt=""><figcaption><p>Click "Approve" on Keplr to sign and register</p></figcaption></figure>

#### Step 2: Create NFT Class

After successfully registering the ISCN, create an NFT Class based on it. Unless you want to set a maximum supply limit, you don't need to fill in the "Max number of supply for the NFT Class (optional)" field. Click "Choose file" to upload the prepared nft\_class.json file. Then click "Create" and sign twice with Keplr by clicking "Approve" to generate the NFT Class.

<figure><img src="../../.gitbook/assets/Mint NFT Book 3.png" alt=""><figcaption><p>Click "Choose file" to upload nft_class.json and then click "Create"</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/Mint NFT Book 4.png" alt=""><figcaption><p>Click "Approve" twice on Keplr to generate the NFT Class</p></figcaption></figure>

#### Step 3: Mint the NFT Book

You need to upload two files: nfts\_default.json and nfts.csv to mint the NFT Book. Please note that the CSV file specifies the actual number of NFTs you want to publish, and you need to enter the same quantity in the "Number of NFT to mint" field. Then click "Create" and sign with Keplr by clicking "Approve" to confirm.

<figure><img src="../../.gitbook/assets/Mint NFT Book 5.png" alt=""><figcaption><p>Click "Choose file" to upload nfts_default.json and nfts.csv, enter the Number of NFT to mint, and then click "Approve" on Keplr to sign and confirm</p></figcaption></figure>

#### Step 4: Successfully mint the NFT Book

A pop-up window will appear, and you can save the result file. Then return to the page where "Success!" is displayed, indicating NFT Book minted successfully. Click "View your NFT" to check the NFT book in Liker Land.

<figure><img src="../../.gitbook/assets/Mint NFT Book 6.png" alt=""><figcaption><p>save the resSave the result file on the pop-up windowsult file</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/Mint NFT Book 7.png" alt=""><figcaption><p>Click "View your NFT"</p></figcaption></figure>

Since you have only completed minting and have not made them available for sale, the book quantity will be shown as "Sold out." The next step is to list the NFT books for sale on Liker Land.

<figure><img src="../../.gitbook/assets/Mint NFT Book 9.png" alt=""><figcaption><p>View published NFT books at Liker Land</p></figcaption></figure>

### Method 2: Install the Minting Script and mint NFT Book with it (Old version)

The minting script is a node.js script. &#x20;

#### Install the script

Open your terminal and follow the below steps:

1. Type the command&#x20;

`git clone` [`https://github.com/likecoin/iscn-nft-tools`](https://github.com/likecoin/iscn-nft-tools)

2. In the mint-nft folder and send-nft folder, run the command&#x20;

`npm install`

Program path: iscn-nft-tools/mint-nft

Executable: index.js

#### Executing the Script

The script will perform three steps:&#x20;

1. Register ISCN
2. Create NFT class
3. Mint NFT(s)

You can specify an existing ISCN by the parameter --iscn-id, and specify an existing NFT class ID by the parameter --class-id.  You can also let the script to create everything new.

<table><thead><tr><th width="129">Parameter</th><th width="230">Argument</th><th width="217">Example</th><th>Mandatory?</th></tr></thead><tbody><tr><td>nft-count</td><td>An integer. Total number of NFT to be minted.</td><td>--nft-count 100</td><td>YES</td></tr><tr><td>iscn-id</td><td>A string. The ISCN ID that the NFT is referring to. </td><td>--iscn-id iscn://likecoin-chain/IKI9PueuJiOsYvhN6z9jPJIm3UGMh17BQ3tEwEzslQo/3</td><td>NO</td></tr><tr><td>create-new-iscn</td><td>Null. If the parameter is specified, a new ISCN will be registered according to the iscn.json file. Cannot use together with the parameter iscn-id</td><td>--create-new-iscn</td><td>NO</td></tr><tr><td>class-id</td><td>A string. The NFT class ID that the NFT belongs to. It is used in the case to mint additional NFTs within the same Class (collection). The script will create one based on nft-class.json if not specified.</td><td>--class-id likenft1yhsps5l8tmeuy9y7k0rjpx97cl67cjkjnzkycecw5xrvjjp6c5yqz0ttmc</td><td>NO</td></tr><tr><td>nft-max-supply</td><td>An integer. Maximum number of NFTs that can be minted in an NFT class. No limitation if not specified.</td><td>--nft-max-supply 1000</td><td>NO</td></tr></tbody></table>

Example:

`IS_TESTNET=TRUE MNEMONIC="...." node index.js --nft-count 100 --create-new-iscn`

`IS_TESTNET=TRUE MNEMONIC="...." node index.js --nft-count 100 --iscn-id iscn://xxxx`

Note:

* either the parameter iscn-id or create-new-iscn must be specified, but cannot use both.
* If create-new-iscn parameter is given, the program will refer to data/iscn.json to register a new ISCN ID
* if class-id parameter is absent, the program will refer to data/nft\_class.json
* class-id and nft-max-supply should not be present together, as nft-max-supply should be useful upon creating new nft class **only.**
* The number specified in nft-count should be matched the number of rows in data/nfts.csv.

After executing the script, you should have minted the NFT successfully.  Congratulation!

## List NFT Books

### Step 1: Start listing NFT Books

Please log in to your [Keplr](https://docs.like.co/v/zh/general-guides/wallet/keplr) and select "Manage NFT Books" on LikeCoin NFT Book Press. Then click "Connect" in the upper right corner to connect to Keplr. On the New NFT Book Listing page, enter the following information:

|                                            |                                                                                                                                |
| ------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------ |
| NFT Class ID                               | The Minted NFT Book Class ID                                                                                                   |
| Price(USD) per NFT Book (Minimal $5)       | Minimum selling price for an NFT book should not be less than $5                                                               |
| Total number of NFT for sale at this price | The total number of NFT books to be sold at this price. For example, 100 books out of 1,000 NFT books to be released for sale  |
| Product name of this price                 | The product name of the NFT book to be sold in the particular price, supports Chinese and English settings                     |
| Product description of this price          | The product description of the NFT book to be sold in the particular price, supports Chinese and English settings              |

Click "Add more prices" to set different prices and product descriptions for different versions of the NFT book.

Additionally, in the "Share sales data to wallets (moderator)" field, you can add the wallets of moderator to allow them to view sales data. In the "Email to receive sales notifications" field, you can enter email addresses other than the creator's to receive sales notifications. Once you have filled in the information, click "Submit".

<figure><img src="../../.gitbook/assets/List NFT Book 1.png" alt=""><figcaption><p>Enter the information on the New NFT Book Listing page and click "Submit"</p></figcaption></figure>

### Step 2: View Listed NFT Books

After successfully listing, the listed NFT books will appear under "Current listing". Click on the Class ID to view the listing status in the NFT Book Status.

<figure><img src="../../.gitbook/assets/List NFT Book 2.png" alt=""><figcaption><p>After successful listing, the NFT book will appear in the Current listing, click the Class ID to view the listing status</p></figcaption></figure>

Go back to Liker Land to view the NFT books. You will see that the sales quantity has changed from "Sold out" to listed for sale. The product name, description, and price will be displayed.

<figure><img src="../../.gitbook/assets/List NFT Book 3.png" alt=""><figcaption><p>View published NFT books at Liker Land</p></figcaption></figure>

### Step 3: Sell Books through Different Channels

In the NFT Book Status, select the listed NFT book product under "Copy Purchase Link". In the "Sales channel for this link (Optional)" field, enter the name of the sales channel. You will see the Stripe URL of the sales link. You can provide this URL to the sales channel to attract customers to purchase the book.

<figure><img src="../../.gitbook/assets/List NFT Book 4.png" alt=""><figcaption><p>Enter the name of the sales channel and Stripe URL sales link appears</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/List NFT Book 5.png" alt=""><figcaption><p>Customers use the link to purchase books</p></figcaption></figure>

### Step 4: View Sold NFT Books

After a customer purchases an NFT book, the quantity of the book will decrease in the "Current listing" section of the NFT Book Listing.

<figure><img src="../../.gitbook/assets/List NFT Book 6.png" alt=""><figcaption><p>Current listing shows the new number of NFT books</p></figcaption></figure>

In the NFT Book Status, you can view the sales data for the NFT book. Under "Status", you can see the overall sales status of the NFT book. "Orders" shows the received NFT book orders, "pendingNFT" indicates pending delivery to customers, and "Sales channel" displays the channel from which the book was sold.

<figure><img src="../../.gitbook/assets/List NFT Book 7.png" alt=""><figcaption><p>In NFT Book Status, you can view the sales data of NFT books, click "Send NFT" to send NFT books to customers</p></figcaption></figure>

### Step 5: Send NFT Books to Customers

In the "Action" section, click "Send NFT" to access the "Deliver NFT Book" page. In the "Enter Author's Message (optional)" field, you can enter a message for the reader (optional). In the "Specify NFT ID" section, enter the NFT ID or click "Auto-fetch NFT ID" to automatically retrieve one of the minted NFT books. Then use Keplr to sign and send it to the customer.

<figure><img src="../../.gitbook/assets/List NFT Book 8.png" alt=""><figcaption><p>"Enter Author's Message (optional)" , click "Auto-fetch NFT ID" to automatically retrieve one of the minted NFT books</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/List NFT Book 9.png" alt=""><figcaption><p>Sign with Keplr and send to client</p></figcaption></figure>

After the delivery is complete, the "Send NFT" action will change to "View Transaction", and you can view the NFT book that has been sent to the customer.

<figure><img src="../../.gitbook/assets/List NFT Book 10.png" alt=""><figcaption><p>Click "View Transaction" to view the NFT book that has been sent to the customer</p></figcaption></figure>

## Updating eBook File and any Metadata's Version

You may have the need to update the eBook files (epub/pdf) or any metadata, for example, a typical scenario is to include the registered ISCN into the eBook files, and hence you will get new contentFingerprints.   Take this use case as an example, you need to:

1. Add the ISCN information to the eBook files (pdf/epub).
2. Upload the eBook files to IPFS and get the new hash (contentFingerprint).
3. Update the ISCN to replace the old contentFingerprint by the new one.

You can always trace back the information of the old ISCN versions, but Liker Land frontend will display the information of the most updated ISCN version.  &#x20;

Check out the tools to update ISCN below:

{% content-ref url="../decentralized-publishing/iscn-browser.md" %}
[iscn-browser.md](../decentralized-publishing/iscn-browser.md)
{% endcontent-ref %}

Moreover, please find the ISCN browser tool on testnet [here](https://likecoin-iscn-browser-testnet.netlify.app/).
