---
description: Publish eook with LikeCoin NFT Book Press
---

# Publish ebook

{% hint style="info" %}
Before publishing, you can refer to the [FAQ: Listing Liker Land ebooks](faq.md)
{% endhint %}

{% hint style="info" %}
Publish NFT requires a desktop computer and [LikeCoin](https://like.co/) on a desktop computer
{% endhint %}

Publishing an ebook on the blockchain involves the following processes:

1. [Prepare the EPUB File](./#create-an-epub-file-and-enter-metadata)
2. [Register ISCN](./#register-iscn)
3. [List the Book for Sale](./#list-the-book-for-sale)

and other follow up actions:

4. [Manage NFT books](nft-book-store.md)
5. [Manage Book Collection](collection.md)
6. [NFT Book Press User Setting](user.md)
7. [Affiliation Link Setting](affiliation-link.md)
8. [ebooks Replenishment](replenishment.md)
9. [Modify ebook](modify.md)
10. [Burn ebook](burn.md)
11. [Transfer ebook or Batch send NFT to more than one wallet](../transfer-nft.md)
12. [Import EPUB files to various ereaders](./#ereader)
13. [Creator’s Introduction on Liker Land BookStore](../register/edit-avatar-displayname.md)

***

## Create an EPUB file and enter metadata

Create an [EPUB](https://en.wikipedia.org/wiki/EPUB) file and enter [metadata](../what-is-iscn/). First, create the EPUB file for the ebook, and ensure that the metadata has been entered and organized. Metadata includes book title, author, cover image, publication date, description, etc. The system can automatically extract the necessary information from EPUB Metadata for publishing later on.

***

## Register ISCN

After preparing the EPUB file, register it as an ISCN.

### Step 1: Upload the file

Visit the[ app.like.co](https://app.like.co/) website and click "**Register ISCN**".

<figure><img src="../../.gitbook/assets/NFT Book Press 5.png" alt=""><figcaption><p>Visit the app.like.co website and click "Register ISCN"</p></figcaption></figure>

A pop-up window will appear to connect your wallet. It is recommended to register and **log in with a Liker ID using Email/Social**. For more details, refer to:

{% content-ref url="../register/" %}
[register](../register/)
{% endcontent-ref %}

<figure><img src="../../.gitbook/assets/NFT Book Press 6.png" alt=""><figcaption><p>A pop-up window will appear; click and connect to a wallet</p></figcaption></figure>

Click "**Select a file**" to upload the prepared EPUB file.

<figure><img src="../../.gitbook/assets/NFT Book Press 7.png" alt=""><figcaption><p>Click "Select a file" to upload the prepared EPUB file</p></figcaption></figure>

The system will automatically split the EPUB file content into two files: one is the EPUB file, and the other is the book cover image file. Check if everything is okay, then click "**Start Upload**". The system will upload these two files to the distributed network.

<figure><img src="../../.gitbook/assets/NFT Book Press 8.png" alt=""><figcaption><p>Click "Start Upload" to upload the two files to the distributed network</p></figcaption></figure>

### Step 2: Enter book information

"File Ready" appears, indicating that the file has been successfully uploaded. The system will automatically fill in the information based on the metadata content. The user can change them if they want:

<figure><img src="../../.gitbook/assets/NFT Book Press 10.png" alt=""><figcaption><p>"File Ready" appears</p></figcaption></figure>

1. **Type**: The default is "Book" for ebook.
2. **Lang**: The system will display the corresponding language based on the Metadata. For example, zh stands for Traditional Chinese.
3. **ISCN Title**: The title of the book associated with the ISCN.
4. **Description**: A brief description of the ebook.
5. **Author**: The author's name.
6. **Stakeholders**: The system will automatically add the author and the ISCN registrant as stakeholders.
7. **Tags**: These are used for classification purposes.
8. **Hide file storage link from public blockchain**: Avoid the link appearing in general public.
9. **Downloadable URL**: The file's name of the EPUB when it is being downloaded.
10. **URL**: The URL of the EPUB.
11. **License**: The default is "Copyright. All rights reserved" for copyright declaration.
12. **Content Fingerprints**: These are URL hashes of the book and its cover. Each pair corresponds to one file, including IPFS and AR (Arweave) formats. Click on the URLs to check whether the content has been successfully uploaded. For instance, the four hashes in the attached screenshot represent the IPFS EPUB file, IPFS book cover file, AR EPUB file, and AR book cover file.
13. **Registrant**: Wallet address used during registration

Click on +Other settings and fill in more content if required:

14. **URL:** The corresponding URL for the book content
15. **ISBN:** The book's ISBN
16. **Publisher:** Publisher of the book
17. **Original Date Published:** The original publication date

<figure><img src="../../.gitbook/assets/NFT Book Press 11.png" alt=""><figcaption><p>Click "Register"</p></figcaption></figure>

After confirming that everything is correct, click "**Register**".

### Step 3: ISCN registration completed

The message "Completed! Here is your ISCN" appears, indicating that the ISCN has been successfully registered. The string of characters in the ISCN ID field will be used when listing the ebook for sale. Note that the '/1' in the picture is the ISCN version number.

<figure><img src="../../.gitbook/assets/NFT Book Press 15.png" alt=""><figcaption><p>Completed ISCN registration and copy the ISCN ID</p></figcaption></figure>

***

## List the Book for Sale

Listing for sale is divided into two steps: minting the ebook and listing it. An analogy to traditional publishing is printing manuscripts into books and placing them on bookshelves for sale.

### Step 1: Mint the ebook

Click ‘**Mint Book**’ at the top right corner of the ISCN record.

<figure><img src="../../.gitbook/assets/NFT Book Press 9.png" alt=""><figcaption><p>Click "Mint Book"</p></figcaption></figure>

The system will automatically redirect to the [LikeCoin NFT Book Press](https://likecoin.github.io/nft-book-press/) website, and the ISCN ID will be pre-entered in the ‘Enter ISCN ID or NFT Class ID’ field. After clicking 'Sign In' at the bottom left corner to log in to the website, click **'Submit**'.

<figure><img src="../../.gitbook/assets/NFT Book Press 17.png" alt=""><figcaption><p>In the "Enter ISCN ID or NFT Class ID" field, enter the ISCN ID</p></figcaption></figure>

Alternatively, go directly to the [LikeCoin NFT Book Press](https://likecoin.github.io/nft-book-press/) website and click "[Mint NFT](https://likecoin-nft-book-press-testnet.netlify.app/mint-nft)". Click ‘Sign In’ at the bottom left corner to log in. Manually enter the previously registered ISCN ID in the "Enter ISCN ID or NFT Class ID" field and then click "**Submit**".

<figure><img src="../../.gitbook/assets/NFT Book Press 16.png" alt=""><figcaption><p>Visit the LikeCoin NFT BookPress website, click "Mint NFT"</p></figcaption></figure>

In the "Enter ISCN ID or NFT Class ID" field, input the ISCN ID previously registered on app.like.co, and please note that there is no need to include the ISCN version number. Afterward, click "**Submit**".

{% hint style="info" %}
If you forget your ISCN ID, you can retrieve it in "[My Works](https://app.like.co/works)" at app.like.co.&#x20;
{% endhint %}

The system will automatically extract the basic information of ISCN for you. Fill in other information required in the "By filling required information" tab.

* Enter the number of NFTs to mint in the "**Number of NFT to mint**" field.
* If your book file is in EPUB format, the system will automatically extract the link to the AR cover and place it in the "Image URL" column.
* "External URL (optional)", "URI (optional)", and "Max number of supply for this NFT Class (optional)" can be filled in as needed.

After filling in and confirming that everything is correct, click "**Mint**".

<figure><img src="../../.gitbook/assets/NFT Book Press 18.png" alt=""><figcaption><p>Enter all the information and click "Mint"</p></figcaption></figure>

The 🎉 Success! screen appears, indicating that the NFT has been successfully minted. Click "**Continue to publish NFT Book**" to complete the listing. Click "**View your NFT**" to view minted ebook in [Liker Land](https://liker.land/).

<figure><img src="../../.gitbook/assets/NFT Book Press 20.png" alt=""><figcaption><p>. Click "Continue to publish NFT Book" to complete the listing. Click "View your NFT" to view minted ebook in Liker Land</p></figcaption></figure>

Since it is not yet available for sale, you will see the words "Sold Out" on Liker Land.

<figure><img src="../../.gitbook/assets/NFT Book Press 21.png" alt=""><figcaption><p>Since it is not yet available for sale, you will see the words "Sold Out"</p></figcaption></figure>

### Step 2: Book Listing

Return to LikeCoin NFT BookPress, click "**Continue to publish NFT Book**", and the [NFT Book Store Management Page](https://likecoin.github.io/nft-book-press/nft-book-store) will appear.

{% hint style="info" %}
If you accidentally closed the page, you can enter your NFT Class ID in [Step 1](./#register-iscn) "Enter ISCN ID or NFT Class ID", and you will see "Continue to publish NFT Book". The Class ID is the string after the URL of your ebook. For example, your NFT URL is  https://liker.land/zh-Hant/nft/class/likenft1qq06n42guzvt087wxunaajvz3alx6wadq6mfz0yz57gffwsrgrasl2m59x, and the NFT Class ID is likenft1qq06n42guzvt087wxunaajvz3alx6wadq6mf z0yz57gffwsrgrasl2m59x.
{% endhint %}

### New NFT Book Listing

The NFT Class ID of the minted ebook appears in the New NFT Book Listing

<figure><img src="../../.gitbook/assets/NFT Book Press 22.png" alt=""><figcaption><p>The NFT Class ID of the minted ebook appears in the New NFT Book Listing</p></figcaption></figure>

### Pricing and Availability

* **Unit Price in USD (Minimum 0.99 or 0 for free)** - The minimum price is 0.99 US dollars, or enter 0 to give it away for free.
* **Total number of NFT ebook for sale** - Fill in the sales quantity of this version of the ebook. Suppose you minted 10 books, you can set 5 books as version one, and the other 5 books as version two, etc. Click "Add Edition" below to add multiple different versions. Note that the total number of ebooks available for sale in each version cannot exceed the minted quantity.
* **Delivery method of this book** - You can choose between two different ways to send ebooks:
  1. **Automatic deliver NFT** - Automatically send the ebook to the reader. Once this option is set, it cannot be changed.
     * **Memo of this book** - If you choose to automatically send the ebook to the reader, a memo will be automatically added to the reader upon delivery.
  2. **Sign memo and manually deliver each NFT** - Sign and manually send the ebook to the reader
     * **Is Physical only good** - If you choose to sign manually, this option will pop up to ask if the book only contains a physical version, displaying "This edition does not contain digital file/NFT". If selected, it means this version does not provide an ebook file and the physical book will be sent by the author. Please add the postage option in Advanced Settings.
* **Allow custom price** - Choose "**Allow users to pay more than the defined price**".' Readers can provide an [extra tip](../ebook/#step-2-show-your-support-with-a-tip) to the author when purchasing the eBook.
* **Unlist Edition** - Select "**Pause selling of this Edition**" to temporarily stop offering this eBook edition.

<figure><img src="../../.gitbook/assets/NFT Book Press 23.png" alt=""><figcaption><p>Pricing and Availability</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/NFT Book Press 23more.png" alt=""><figcaption><p>Sign memo and manually deliver each NFT</p></figcaption></figure>

### Product Information

* **Product name** - You can set the version of the ebook according to personal preference, such as Standard Edition, Free version, etc.
* **Description (Optional)** - You can enter a Chinese and English description of the ebook version.

<figure><img src="../../.gitbook/assets/NFT Book Press 23a.png" alt=""><figcaption><p>Product Information</p></figcaption></figure>

### Shipping Options

**Physical Goods** - After selecting “**Includes physical good that requires shipping**”, it indicates that the book version is a physical copy, and readers will need to pay for shipping. However, you need to configure the settings in Advanced Settings first before this option can be enabled.

<figure><img src="../../.gitbook/assets/NFT Book Press 26.png" alt=""><figcaption><p>Shipping Options</p></figcaption></figure>

### Connect to a Stripe Account

Click to start connecting to the Stripe account, see details:

{% content-ref url="user.md" %}
[user.md](user.md)
{% endcontent-ref %}

<figure><img src="../../.gitbook/assets/NFT Book Press 27.png" alt=""><figcaption><p>Connect to a Stripe Account</p></figcaption></figure>

### Email to receive sales notification

Enter the email address that needs to receive sales notifications, then click “**Add**”.

<figure><img src="../../.gitbook/assets/NFT Book Press 23b.png" alt=""><figcaption><p>Email to receive sales notification</p></figcaption></figure>

### Advance Settings

Click Advanced Settings to configure the following additional options:

<figure><img src="../../.gitbook/assets/NFT Book Press 23c (1).png" alt=""><figcaption><p>Advance Settings</p></figcaption></figure>

### **Shipping Options**

Shipping options, click the **“+Add**” in the top right corner.

<figure><img src="../../.gitbook/assets/NFT Book Press 23f.png" alt=""><figcaption><p>Click the “+Add” in the top right corner</p></figcaption></figure>

The “Editing Shipping Options” page appears.

* **Name of the shipping option** - Fill in the name of the shipping method in both Chinese and English.
* **Price(USD) of this shipping option** - Specify the cost of this shipping method in US dollars.
* Click “**Add Options**” to add more shipping methods.

Once done, click “**Save**" to save this shipping method.

<figure><img src="../../.gitbook/assets/NFT Book Press 23g.png" alt=""><figcaption><p>Editing Shipping Options</p></figcaption></figure>

### Share sales data to wallets

Enter the wallet address that needs to receive sales data, then click “**Add**”. The Liker Land wallet address is added by default. Click “**Grant**” in the Send NFT Grant section to authorize this wallet to automatically send ebooks for you.

<figure><img src="../../.gitbook/assets/NFT Book Press 23h.png" alt=""><figcaption><p>Share sales data to wallets</p></figcaption></figure>

Click “**Submit**” on the Send NFT Authz Grants Management Page to authorize.

<figure><img src="../../.gitbook/assets/NFT Book Press 23i.png" alt=""><figcaption><p>Send NFT Authz Grants Management Page</p></figcaption></figure>

### DRM Options

Manage digital rights in DRM Options:

* **Force NFT claim before view** - Selecting Must claim NFT to view means that readers must claim the ebook to read
* **Disable File Download** - Selecting Disable Download means not allowing readers to download the ebook, only allowing online reading.
* **Insert cutomized message page in ebook** - Automatically insert a custom message page into the EPUB file.

<figure><img src="../../.gitbook/assets/NFT Book Press 23j.png" alt=""><figcaption><p>DRM Options</p></figcaption></figure>

After completing the settings, click "**Submit**". If the user chooses Automatic deliver NFT, a prompt will appear stating that once you choose to automatically send the ebook to the reader, it cannot be changed to manual delivery. After confirming that it is correct, click "**OK**".

<figure><img src="../../.gitbook/assets/NFT Book Press 23e.png" alt=""><figcaption><p>Click "OK"</p></figcaption></figure>

The version of the book will appear in "Current Listing".

<figure><img src="../../.gitbook/assets/NFT Book Press 24.png" alt=""><figcaption><p>The version of the book will appear in "Current Listing"</p></figcaption></figure>

Go back to Liker Land to check that the ebook has been successfully listed for sale.

<figure><img src="../../.gitbook/assets/NFT Book Press 25.png" alt=""><figcaption><p>The ebook has been successfully listed for sale</p></figcaption></figure>
