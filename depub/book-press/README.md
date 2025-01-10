---
description: 使用 Liker Land Book Press 上架 EPUB 電子書
---

# 上架電子書

{% hint style="info" %}
上架前可參考 [上架 Liker Land 電子書的常見問題](../faq.md)
{% endhint %}

{% hint style="info" %}
上架電子書需使用桌面電腦及 [LikeCoin](https://like.co/)
{% endhint %}

在區塊鏈上架電子書包含以下流程：

1. [備妥 EPUB](./#edit-metadata) 或 [PDF 檔案](pdf.md)
2. [註冊 ISCN](./#register-iscn)
3. [上架銷售](./#nft-book-store)

並可進行其他後續操作：

4. [管理電子書](../book-store/)
5. [設定電子書套裝](../book-store/collection.md)
6. [Liker Land Book Press 用戶設定](../user/)
7. [設定購買連結](../book-store/purchase-link.md)
8. [補書上架](../book-store/replenishment.md)
9. [修改已上架的電子書資料](../book-store/modify.md)
10. [銷毁已上架的電子書](../book-store/burn.md)
11. [發送電子書及群發 NFT 紀念品到多個錢包](../transfer-nft/)
12. [匯入 EPUB 檔案到各家閱讀器](../ebook/read.md)
13. [設置 Liker Land 書店作者簡介](../register/edit-avatar-displayname.md)

***

## 在 Liker Land 上架 EPUB

首先製作好電子書的 [EPUB](https://zh.wikipedia.org/zh-hk/EPUB) 檔案，並確保經已輸入並整理好 Metadata。Metadata 即是[元數據](../what-is-iscn/)。包括書名、作者、封面圖、出版日期、描述等內容，接下內系統能自動從 EPUB Metadata 抽取所需資料以供上架之用。

如果您想在 Liker Land 上架 PDF，請參考：

{% content-ref url="pdf.md" %}
[pdf.md](pdf.md)
{% endcontent-ref %}

***

## 註冊 ISCN <a href="#register-iscn" id="register-iscn"></a>

準備好 EPUB 檔案後，接下來把它註冊成 ISCN。

### 步驟一：上載檔案 <a href="#upload-file" id="upload-file"></a>

到 [app.like.co](https://app.like.co/) 網站，點「**Register ISCN**」。

<figure><img src="../../.gitbook/assets/NFT Book Press 5.png" alt=""><figcaption><p>到 app.like.co 網站，點「Register ISCN」</p></figcaption></figure>

彈出視窗並連結錢包，**建議使用 Email/Social 註冊 Liker ID 並登入**，詳見：

{% content-ref url="../register/" %}
[register](../register/)
{% endcontent-ref %}

<figure><img src="../../.gitbook/assets/NFT Book Press 6.png" alt=""><figcaption><p>彈出視窗並連結錢包</p></figcaption></figure>

登入後點「**Select a file**」上載已預備好的 EPUB 檔案。

<figure><img src="../../.gitbook/assets/NFT Book Press 7.png" alt=""><figcaption><p>點「Select a file」上載已預備好的 EPUB 檔案</p></figcaption></figure>

系統會自動把 EPUB 檔案內容分解成兩個檔案，一個是 EPUB 檔案，另一個是封面圖檔。如果沒有問題點「**Start Upload**」，系統會將這兩個檔案上傳到分散式網絡。

<figure><img src="../../.gitbook/assets/NFT Book Press 8.png" alt=""><figcaption><p>點「Start Upload」將檔案上傳到分散式網絡</p></figcaption></figure>

### 步驟二：輸入書籍資料 <a href="#metadata" id="metadata"></a>

出現 File Ready 代表檔案上傳成功，系統會依照元數據內容生成以下資料，如有需要可作修改：

<figure><img src="../../.gitbook/assets/NFT Book Press 10.png" alt=""><figcaption><p>File Ready 頁面</p></figcaption></figure>

1. **Type**：顯示 ISCN 種類為 Book 即電子書。
2. **Lang：**&#x7CFB;統會跟據 Metadata 顯示對應語言，以圖示為例，zh 為繁體中文
3. **ISCN Title**：書名
4. **Description**：描述
5. **Author**：作者
6. **Stakeholders**：持份者。系統預設加入作者及正在製作電子書的帳戶為持份者。
7. **Tags**：標籤，可加入作為分類。
8. **Hide file storage link from public blockchain**：隱藏文件儲存鏈接，避免公開在區塊鏈上。
9. **Downloadable URL**：下載書檔時所顯示的名稱
10. **URL**：書檔所對應的 URL
11. **License**：可以選擇合適的版權宣告，預設是版權所有 ( Copyright. All rights reserved. )
12. **Content Fingerprints**：顯示書檔及封面 Hash 網址，每兩條 Hash 對應一個檔案。包括 [IPFS](https://ipfs.tech/) 及 [AR ( Arweave ) ](https://www.arweave.org/)格式。以附圖為例，四條 Hash 代表 IPFS 的 EPUB 檔、IPFS 的封面檔、AR 的 EPUB 檔和 AR 的封面檔，不妨點擊網址核對並查看內容是否經已成功上傳。
13. **Registrant**：註冊時使用的錢包地址

點開 +Other settings 選擇填寫更多內容：

14. **URL**：書籍內容對應的網址
15. **ISBN**：書籍的 ISBN
16. **Publisher**：發行商
17. **Original Date Published**：最初的出版日期

<figure><img src="../../.gitbook/assets/NFT Book Press 11.png" alt=""><figcaption><p>點「Register」註冊 ISCN</p></figcaption></figure>

完成後點「**Register**」。

### 步驟三：註冊 ISCN 完成 <a href="#successfully-registered-iscn" id="successfully-registered-iscn"></a>

出現 Completed! Here is your ISCN 說明 ISCN 經已成功註冊。留意 ISCN ID 欄位的一串字符接下來於電子書上架時將需要用到。圖中的 /1 是這個 ISCN 第 1 個版本的意思。

<figure><img src="../../.gitbook/assets/NFT Book Press 15.png" alt=""><figcaption><p>成功註冊並出現 ISCN ID</p></figcaption></figure>

***

## 上架銷售 <a href="#nft-book-store" id="nft-book-store"></a>

上架銷售分開兩個步驟：鑄造電子書及上架。類比傳統出版就是將書稿印刷成書和上架販賣。

### 步驟一：鑄造電子書 <a href="#mint-nft-book" id="mint-nft-book"></a>

在 ISCN 記錄右上角點「**Mint Book**」。

<figure><img src="../../.gitbook/assets/NFT Book Press 9.png" alt=""><figcaption><p>點「Mint Book」</p></figcaption></figure>

系統會自動跳轉到 [Liker Land Book Press](https://publish.liker.land/) 網站的 Mint Liker Land NFT Book 頁面，並於 Enter ISCN ID or NFT Class ID 一欄預先輸入 ISCN ID。點左下角「**Sign In**」登入網站後再點「**Submit**」。

<figure><img src="../../.gitbook/assets/NFT Book Press 17 (1).png" alt=""><figcaption><p>在 Enter ISCN ID or NFT Class ID 一欄輸入 ISCN ID</p></figcaption></figure>

又或者直接到 [Liker Land Book Press](https://publish.liker.land/) 網站點左下角「**Sign In**」登入，再點「[Print New Books](https://publish.liker.land/mint-nft)」，進入網站後並於 Enter ISCN ID or NFT Class ID 一欄手動輸入早前註冊的 ISCN ID 再點「**Submit**」。

<figure><img src="../../.gitbook/assets/NFT Book Press 16.png" alt=""><figcaption><p>到 Liker Land Book Press 網站，點「Print New Books」</p></figcaption></figure>

{% hint style="info" %}
假如你忘記了你的 ISCN ID，可以隨時到 app.like.co 的 [My Works](https://app.like.co/works) 找回它。
{% endhint %}

系統會為你自動抽出 ISCN 的基本資料，接著你需要於「By filling required information」分頁填寫其他資料：

* 在 **Number of NFT to mint** 一欄輸入需要鑄造多少個 NFT
* 如若你的書檔是 EPUB，系統會自動抽出 AR 封面的連結放在 image URL 一欄
* External URL (optional)、URI (optional) 及 Max number of supply for this NFT Class (optional) 可按需要填寫。

填寫完成並確認無誤後點「**Mint**」。

<figure><img src="../../.gitbook/assets/NFT Book Press 18.png" alt=""><figcaption><p>填寫所需資料，確認無誤後點「Mint」</p></figcaption></figure>

出現 🎉 Success! 畫面代表經已成功鑄造 NFT，點「**Continue to publish NFT Book**」可繼續完成上架。點「**View your NFT**」可以到 [Liker Land](https://liker.land/) 查看已鑄造的電子書。

<figure><img src="../../.gitbook/assets/NFT Book Press 20.png" alt=""><figcaption><p>點「Continue to publish NFT Book」可繼續完成上架。點「View your NFT」可以到 Liker Land 查看已鑄造的電子書</p></figcaption></figure>

由於現時還未上架販賣，所以在 Liker Land 會看到「售罄」字樣。

<figure><img src="../../.gitbook/assets/NFT Book Press 21.png" alt=""><figcaption><p>還未上架販賣出現「售罄」字樣</p></figcaption></figure>

### 步驟二：上架 <a href="#publish-nft-book" id="publish-nft-book"></a>

回到 Liker Land Book Press，點「**Continue to publish NFT Book**」後出現 NFT Bookstore Management Page 頁面。

{% hint style="info" %}
假如你不小心關掉了之前的頁面，你可以在[步驟一](./#mint-nft-book) Enter ISCN ID or NFT Class ID 一欄輸入你的 NFT Class ID 即可看到「Continue to publish NFT Book」。Class ID 是你的電子書網址後面的一串。舉例你的 NFT 網址是 https://liker.land/zh-Hant/nft/class/likenft1qq06n42guzvt087wxunaajvz3alx6wadq6mfz0yz57gffwsrgrasl2m59x ，NFT Class ID 就是 likenft1qq06n42guzvt087wxunaajvz3alx6wadq6mfz0yz57gffwsrgrasl2m59x 。
{% endhint %}

### New NFT Book Listing

在 New NFT Book Listing 出現已鑄造電子書的 NFT Class ID，並請填寫以下欄位。

<figure><img src="../../.gitbook/assets/NFT Book Press 22.png" alt=""><figcaption><p>在 New NFT Book Listing 出現已鑄造電子書的 NFT Class ID</p></figcaption></figure>

### Pricing and Availability

* **Unit Price in USD (Minimum 0.99 or 0 for free)** - 最低價格為 0.99 美金，又或者輸入 0 代表免費送出
* **Total number of NFT ebook for sale** - 填寫這一個版本的電子書銷售數量。假設你鑄造了 10 本書，可以設定 5 本書為版本一、另外 5 本書為版本二之類。點下方的「**Add Edition**」可加入多個不同版本。留意每一個版本可供銷售的電子書數量加起來不能多於已鑄造的數量。
* **Delivery method of this book** - 可選擇兩種不同傳送電子書的方式：
  1. **Automatic deliver NFT** - 自動傳送電子書給讀者。選項一經設定，不能修改。
     * **Memo of this book** - 如選擇自動傳送電子書給讀者，於傳送時自動加入給讀者的話。
  2. **Sign memo and manually deliver each NFT** - 自行簽署並手動傳送電子書給讀者
     * **Is Physical only good** - 如選擇自行簽署會彈出此選項詢問書籍是否只包含實體版本，並出現 **This edition does not contain digital file/NFT**。如選取，則代表此版本不提供電子書檔，並將由作者寄出實體書。請於 Advanced Settings 加入郵費選項。
* **Allow custom price** - 選擇 **Allow uers to pay more than defined price** 設定讀者購買電子書的時候可[額外支持作者](../ebook/)。
* **Unlist Edition** - 選擇 **Pause selling of this Edition** 可暫時停止供應此版本電子書

<figure><img src="../../.gitbook/assets/NFT Book Press 23.png" alt=""><figcaption><p>在 Pricing and Availability 輸入各種內容</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/NFT Book Press 23more.png" alt=""><figcaption><p>Sign memo and manually deliver each NFT</p></figcaption></figure>

### Product Information

* **Product name / 產品名稱** - 可依照個人喜好為電子書設定版本，例如 Standard Edition 標準版、Free 免費版等
* **Description (Optional) / 描述（選項）** - 可輸入電子書版本的中英文描述

<figure><img src="../../.gitbook/assets/NFT Book Press 23a.png" alt=""><figcaption><p>設定 Product Information</p></figcaption></figure>

### Shipping Optioins

**Physical Goods** - 選取 **Includes physical good that requires shipping** 後代表書籍版本為實體書，讀者需要支付寄送費用。但需要先在 advanced settings 進行設定才可啟用此選項。

<figure><img src="../../.gitbook/assets/NFT Book Press 26.png" alt=""><figcaption></figcaption></figure>

### Connect to a Stripe  Account

連結 Stripe 帳戶，點擊後將開始連結 Stripe 帳戶，詳見：

{% content-ref url="../user/" %}
[user](../user/)
{% endcontent-ref %}

<figure><img src="../../.gitbook/assets/NFT Book Press 27.png" alt=""><figcaption><p>Connect to a Stripe Account</p></figcaption></figure>

### Email to receive sales notification

輸入需要接收銷售通知的電郵地址，再點「**Add**」。

<figure><img src="../../.gitbook/assets/NFT Book Press 23b.png" alt=""><figcaption><p>Email to receive sales notification</p></figcaption></figure>

### Advance Settings

點 Advance Settings 可額外設定以下內容：

<figure><img src="../../.gitbook/assets/NFT Book Press 23c.png" alt=""><figcaption><p>Advance Settings</p></figcaption></figure>

### Shipping Options

寄送費用選項，點右上角「**+Add**」。

<figure><img src="../../.gitbook/assets/NFT Book Press 23f.png" alt=""><figcaption><p>點右上角「+Add」</p></figcaption></figure>

出現 Editing Shipping Options 頁面。

* **Name of the shipping option** - 填寫寄送方式的中英文名稱
* **Price(USD) of this shipping option** - 該寄送方式以美元計算的費用
* 點「**Add Options**」可增加更多寄送方式

完成後點「**Save**」儲存該寄送方式。

<figure><img src="../../.gitbook/assets/NFT Book Press 23g.png" alt=""><figcaption><p>Editing Shipping Options</p></figcaption></figure>

### Share sales data to wallets

輸入需要接收銷售數據的錢包地址，再點「**Add**」。預設已加入 Liker Land 的錢包地址。在 Send NFT Grant 點「**Grant**」 可授權該錢包為你自動傳送電子書。

<figure><img src="../../.gitbook/assets/NFT Book Press 23h.png" alt=""><figcaption><p>Share sales data to wallets</p></figcaption></figure>

在 Send NFT Authz Grants Management Page 點「**Submit**」即可授權。

<figure><img src="../../.gitbook/assets/NFT Book Press 23i.png" alt=""><figcaption><p>Send NFT Authz Grants Management Page</p></figcaption></figure>

如需撒銷 Authz 授權請參考：

{% content-ref url="../book-store/authz.md" %}
[authz.md](../book-store/authz.md)
{% endcontent-ref %}

### DRM Options

在 DRM Options 進行數位版權管理：

* **Force NFT claim before view** - 選取 **Must claim NFT to view** 代表讀者一定要領取電子書方可閱讀
* **Disable File Download** - 選取 **Disable Download** 代表不讓讀者下載電子書，只容許線上閱讀
* **Insert cutomized message page in eBook** - 選擇 **Enable custom message page** 將自動插入簽名頁於 EPUB 檔案中

<figure><img src="../../.gitbook/assets/NFT Book Press 23j.png" alt=""><figcaption><p>DRM Options</p></figcaption></figure>

完成設定後點「**Submit**」。假如用戶選擇 Automatic deliver NFT，將出現提示說明一但選擇自動傳送電子書給讀者將不能更改為手動。確認無誤後點「**OK**」。

<figure><img src="../../.gitbook/assets/NFT Book Press 23e.png" alt=""><figcaption><p>確認無誤後點「OK」</p></figcaption></figure>

接著在 Current Listing 會出現已上架的書藉版本。

<figure><img src="../../.gitbook/assets/NFT Book Press 24 (1).png" alt=""><figcaption><p>在 Current Listing 出現已上架的書藉版本</p></figcaption></figure>

回到 Liker Land 查看，電子書經已成功上架。

<figure><img src="../../.gitbook/assets/NFT Book Press 25.png" alt=""><figcaption><p>電子書經已成功上架</p></figcaption></figure>
