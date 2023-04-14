---
description: Publishing eBook as an NFT
---

# Mint NFT Book (beta)

### 📣Minting Writing NFT requires LikeCoin, users can get a small amount of LikeCoin from the faucet for testing.

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

## Install the Minting Script

The minting script is a node.js script. &#x20;

### Install the script

Open your terminal and follow the below steps:

1. Type the command&#x20;

`git clone` [`https://github.com/likecoin/iscn-nft-tools`](https://github.com/likecoin/iscn-nft-tools)

2. In the mint-nft folder and send-nft folder, run the command&#x20;

`npm install`



Program path: iscn-nft-tools/mint-nft

Executable: index.js

### Preparing the data files&#x20;

After installing the script, you will get a few sample data files in JSON format under the directory `iscn-nft-tools/mint-nft/data`.  Before running the script, you must prepare the necessary data file.

The definitions of each data files are stated below:

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

<img src="../../.gitbook/assets/image (1).png" alt="Preview on liker.land" data-size="original">

**nft\_class.json**

| name                                         | NFT title displaying in portfolio/dashboard, class view and detail view.                                                                                                                                                                                       |
| -------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| description                                  | NFT description displaying in class view and detail view.                                                                                                                                                                                                      |
| symbol                                       | Reserved                                                                                                                                                                                                                                                       |
| uri                                          | The URI of an API to return an image that serves as the og image of the NFT class, which is displayed in the portfolio/dashboard and class view of liker.land, and may display in detail view as well if nfts.csv and nfts\_default.json are not set properly. |
| metadata → image                             | The URL of an image that serves as the og image of the NFT, which is displayed in the portfolio/dashboard and class view of liker.land, and may display in detail view as well if nfts.csv and nfts\_default.json are not set properly.                        |
| metadata → external\_url                     | <p>The link to the “View Content” button in the NFT detail page, under the main NFT image.  <br>The url field in iscn.json takes preference.</p>                                                                                                               |
| metadata → message                           | The “creator message” that is appended to every NFT in the same class                                                                                                                                                                                          |
| metadata → nft\_meta\_collection\_id         | NFT category, e.g.: nft\_book, nft\_mail, nft\_photo, nft\_illustration etc. Liker Land use this field to decide which section the NFT is displayed.                                                                                                           |
| metadata → nft\_meta\_collection\_name       | NFT category name                                                                                                                                                                                                                                              |
| metadata → nft\_meta\_collection\_descrption | NFT category description                                                                                                                                                                                                                                       |

#### nfts.csv

| Fields   | Values                                                                                                                                                                                                                                                                                 |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| nftId    | The unique NFT ID under a specific NFT class ID. The system will generate a random ID if it is not specified. Format requirement: [https://docs.like.co/developer/likenft/likecoin-nft-module-spec#mintnft](https://docs.like.co/developer/likenft/likecoin-nft-module-spec#mintnft) . |
| uri      | The URI of an API to return an image that serves as the og image of the NFT, which is displayed in the NFT detail view of liker.land. The uri parameter override the “image” parameter.                                                                                                |
| image    | The URL of an image that serves as the og image of the NFT, which is displayed in the NFT detail view of liker.land.                                                                                                                                                                   |
| metadata | Metadata of the NFT image of any related parameter which is expected to be record on chain.                                                                                                                                                                                            |

#### **nft\_default.json**

| Fields                   | Values                                                                                                                                                                      |
| ------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| uri                      | If image info is not available in nfts.csv, the image will be provided first by this this URI and second by the metadata→image field. This uri is supposed to be a web API. |
| metadata → name          | default NFT name if the field is not specified in nfts.csv metadata                                                                                                         |
| metadata → description   | default NFT description if the field is not specified in nfts.csv metadata                                                                                                  |
| metadata → image         | If image info is not available in nfts.csv, the image will be provided first by this this URI and second by the metadata→image field.                                       |
| metadata → external\_url | <p>The link to the “View Content” button in the NFT detail page, under the main NFT image.  <br>The url field in iscn.json takes preference.</p>                            |

#### Sample files

{% file src="../../.gitbook/assets/iscn.json" %}

{% file src="../../.gitbook/assets/nft_class (1).json" %}

{% file src="../../.gitbook/assets/nfts.csv" %}

{% file src="../../.gitbook/assets/nfts_default.json" %}

For technical details of NFT book, please refer to the below guide:

{% content-ref url="../../developer/likenft/writing-nft-1.md" %}
[writing-nft-1.md](../../developer/likenft/writing-nft-1.md)
{% endcontent-ref %}

## Executing the Script

The script will perform three steps:&#x20;

1\) Register ISCN\
2\) Create NFT class\
3\) Mint NFT(s)

You can specify an existing ISCN by the parameter --iscn-id, and specify an existing NFT class ID by the parameter --class-id.  You can also let the script to create everything new.

| Parameter       | Argument                                                                                                                                                                                                    | Example                                                                       | Mandatory? |
| --------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ---------- |
| nft-count       | An integer. Total number of NFT to be minted.                                                                                                                                                               | --nft-count 100                                                               | YES        |
| iscn-id         | A string. The ISCN ID that the NFT is referring to.                                                                                                                                                         | --iscn-id iscn://likecoin-chain/IKI9PueuJiOsYvhN6z9jPJIm3UGMh17BQ3tEwEzslQo/3 | NO         |
| create-new-iscn | Null. If ther parameter is specified, a new ISCN will be registered according to the iscn.json file. Cannot use together with the parameter iscn-id                                                         | --create-new-iscn                                                             | NO         |
| class-id        | A string. The NFT class ID that the NFT belongs to. It is used in the case to mint additional NFTs within the same Class (collection). The script will create one based on nft-class.json if not specified. | --class-id likenft1yhsps5l8tmeuy9y7k0rjpx97cl67cjkjnzkycecw5xrvjjp6c5yqz0ttmc | NO         |
| nft-max-supply  | An integer. Maximum number of NFTs that can be minted in an NFT class. No limitation if not specified.                                                                                                      | --nft-max-supply 1000                                                         | NO         |

Example:

`IS_TESTNET=TRUE MNEMONIC="...." node index.js --nft-count 100 --create-new-iscn`

`IS_TESTNET=TRUE MNEMONIC="...." node index.js --nft-count 100 --iscn-id iscn://xxxx`



Note:

* either the parameter iscn-id or create-new-iscn must be specified, but cannot use both.
* If create-new-iscn parameter is given, the program will refer to data/iscn.json to register a new ISCN ID
* if class-id parameter is absent, the program will refer to data/nft\_class.json
* class-id and nft-max-supply should not be present together, as nft-max-supply should be useful upon creating new nft class **only**
* The number specified in nft-count should be matched the number of rows in data/nfts.csv.

After executing the script, you should have minted the NFT successfully.  Congratulation!

## Updating eBook File and any Metadata's Version

You may have the need to update the eBook files (epub/pdf) or any metadata, for example, a typical scenario is to include the registered ISCN into the eBook files, and hence you will get new contentFingerprints.   Take this use case as an example, you need to:

1\) Add the ISCN information to the eBook files (pdf/epub)\
2\) Upload the eBook files to IPFS and get the new hash (contentFingerprint)\
3\) Update the ISCN to replace the old contentFingerprint by the new one

You can always trace back the information of the old ISCN versions, but Liker Land frontend will display the information of the most updated ISCN version.  &#x20;

Check out the tools to update ISCN below:

{% content-ref url="../decentralized-publishing/iscn-browser.md" %}
[iscn-browser.md](../decentralized-publishing/iscn-browser.md)
{% endcontent-ref %}

Moreover, please find the ISCN browser tool on testnet [here](http://localhost:5000/s/-LL4mdaVjNgL6A1--PV0-1995411665/general-guides/wallet/migration/migration-faq).









