---
description: 使用 NFT Book Press 將電子書發行為 NFT
---

# 發行 NFT 電子書

{% hint style="info" %}
發行 NFT 電子書需於桌面電腦使用 [Keplr 瀏覽器擴充功能](../../wallet/keplr/)及 [LikeCoin](https://like.co/)
{% endhint %}

在區塊鏈出版 NFT 電子書包含以下流程：

1. [備妥 epub 檔](./#edit-metadata)
2. [註冊 ISCN](./#register-iscn)
3. [上架銷售](./#nft-book-store)

## 教學影片

[5 分鐘出版電子書到區塊鏈（國語 TTS 旁白）](https://www.youtube.com/watch?v=QppGdM-EtBY)

[5 分鐘出版電子書到區塊鏈（廣東話 TTS 旁白）](https://www.youtube.com/watch?v=T08nI\_G1c8E)

***

## 製作 epub 檔案並輸入元數據 <a href="#edit-metadata" id="edit-metadata"></a>

首先製作好電子書的 [epub](https://zh.wikipedia.org/zh-hk/EPUB) 檔案，並確保經已輸入並整理好 Metadata。Metadata 即是[元數據](../../decentralized-publishing/what-is-iscn.md)。包括書名、作者、封面圖、出版日期、描述等內容。以常用的 epub 編輯軟件為例：

#### calibre

在 [calibre](https://calibre-ebook.com/) 編輯元數據的按鈕就在畫面的左上角 Edit Metadata，整理好元數據後記緊按 Save to disk。

<figure><img src="../../../.gitbook/assets/NFT Book Press 1.png" alt=""><figcaption><p>在 calibre 點 Edit Metadata 開啟編輯元數據介面，完成後按 Save to disk</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/NFT Book Press 2.png" alt=""><figcaption><p>編輯元數據後按「OK」</p></figcaption></figure>

#### Sigil

在 [Sigil](https://sigil-ebook.com/) 可按 F8 鍵可即時編輯元數據。

<figure><img src="../../../.gitbook/assets/NFT Book Press 3.png" alt=""><figcaption><p>在 Sigl 按 F8 鍵編輯元數據</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/NFT Book Press 4.png" alt=""><figcaption><p>編輯元數據後按「確定」</p></figcaption></figure>

***

## 註冊 ISCN <a href="#register-iscn" id="register-iscn"></a>

準備好 epub 檔案後，接下來把它註冊成 ISCN。

### 步驟一：上載檔案

到 [app.like.co](https://app.like.co/) 網站，點「Register ISCN」。

<figure><img src="../../../.gitbook/assets/NFT Book Press 5.png" alt=""><figcaption><p>到 app.like.co 網站，點「Register ISCN」</p></figcaption></figure>

彈出視窗並點 Keplr 連結錢包。

<figure><img src="../../../.gitbook/assets/NFT Book Press 6.png" alt=""><figcaption><p>彈出視窗並點 Keplr 連結錢包</p></figcaption></figure>

點「Select a file」上載已預備好的 epub 檔案。

<figure><img src="../../../.gitbook/assets/NFT Book Press 7.png" alt=""><figcaption><p>點「Select a file」上載已預備好的 epub 檔案</p></figcaption></figure>

系統會自動把 epub 檔案內容分解成兩個檔案，一個是 epub 檔案，另一個是封面圖檔。如果沒有問題點「Start Upload」，系統會將這兩個檔案上傳到分散式網絡。

<figure><img src="../../../.gitbook/assets/NFT Book Press 8.png" alt=""><figcaption><p>點「Start Upload」將檔案上傳到分散式網絡</p></figcaption></figure>

Keplr 錢包將彈出視窗數次，點「Approve」簽署後靜侯一會兒。

<figure><img src="../../../.gitbook/assets/NFT Book Press 9.png" alt=""><figcaption><p>在 Keplr 點「Approve」簽署</p></figcaption></figure>

### 步驟二：輸入書籍資料

出現 File Ready 代表檔案上傳成功，系統會依照元數據內容生成以下資料，如有需要可作修改：

<figure><img src="../../../.gitbook/assets/NFT Book Press 10.png" alt=""><figcaption><p>File Ready 頁面</p></figcaption></figure>

1. Type：顯示 ISCN 種類為 Book 即 NFT 電子書。
2. ISCN Title：書名
3. Description：描述
4. Author：作者
5. Stakeholders：持份者。系統預設加入作者及正在製作電子書的帳戶為持份者。
6. Tags：標籤，可加入作為分類。
7. Downloadable URL：下載書檔時所顯示的名稱
8. URL：書檔所對應的 URL
9. License：可以選擇合適的版權宣告，預設是版權所有 ( Copyright. All rights reserved. )
10. Content Fingerprints：顯示 Hash 網址，每兩條 Hash 對應一個檔案。包括 [IPFS](https://ipfs.tech/) 及 [AR ( Arweave ) ](https://www.arweave.org/)格式。以附圖為例，四條 Hash 代表 IPFS 的 epub 檔、IPFS 的封面檔、AR 的 epub 檔和 AR 的封面檔，不妨點擊網址核對並查看內容是否經已成功上傳。
11. \+Other settings：點開它出現 URL 可輸入書籍的網址及 ISBN 輸入 ISBN 號碼。完成後點「Register」。

<figure><img src="../../../.gitbook/assets/NFT Book Press 11.png" alt=""><figcaption><p>點「Register」註冊 ISCN</p></figcaption></figure>

Keplr 錢包將彈出視窗數次，點「Approve」簽署。留意在這個位置不要點 Retry，靜侯一會兒就可以了。

<figure><img src="../../../.gitbook/assets/NFT Book Press 14.png" alt=""><figcaption><p>在 Keplr 點「Approve」簽署</p></figcaption></figure>

### 步驟三：註冊 ISCN 完成

出現 Completed! Here is your ISCN 說明 ISCN 經已成功註冊。點 ISCN ID 欄位的一串字符把它複製，接下來於 NFT 電子書上架時會需要用到。圖中的 /1 是這個 ISCN 第 1 個版本的意思，於製作 NFT 電子書時並不重要。

<figure><img src="../../../.gitbook/assets/NFT Book Press 15.png" alt=""><figcaption><p>成功註冊並複製 ISCN ID</p></figcaption></figure>

***

## 上架銷售 <a href="#nft-book-store" id="nft-book-store"></a>

上架銷售分開兩個步驟：鑄造 NFT 電子書及上架。類比傳統出版就是將書稿印刷成書和上架販賣。

### 步驟一：鑄造 NFT 電子書 <a href="#mint-nft-book" id="mint-nft-book"></a>

到 [LikeCoin NFT BookPress](https://likecoin.github.io/nft-book-press/) 網站，點「Mint NFT」，進入網站後按右上角「Connect Wallet」連結 Keplr。

<figure><img src="../../../.gitbook/assets/NFT Book Press 16.png" alt=""><figcaption><p>到 LikeCoin NFT BookPress 網站，點「Mint NFT」</p></figcaption></figure>

在 Enter ISCN ID or NFT Class ID 一欄輸入早前在 app.like.co 註冊完成並已複製的 ISCN ID，輸入完成後點「Submit」。

<figure><img src="../../../.gitbook/assets/NFT Book Press 17.png" alt=""><figcaption><p>在 Enter ISCN ID or NFT Class ID 一欄輸入 ISCN ID</p></figcaption></figure>

{% hint style="info" %}
假如你忘記了你的 ISCN ID，可以到 app.like.co 的 [My Works](https://app.like.co/works) 找回它。
{% endhint %}

系統會為你自動抽出 ISCN 的基本資料，接著你需要於「By filling required information」分頁填寫其他資料。

在 Number of NFT to mint: 一欄輸入需要鑄造多少個 NFT。

如若你的書檔是 epub，系統會自動抽出 AR 封面的連結放在 image URL 一欄。

External URL (optional): 與 URI (optional): 不用填寫。

填寫完成並確認無誤後按「Mint」，Keplr 錢包將彈出視窗數次，點「Approve」簽署。

<figure><img src="../../../.gitbook/assets/NFT Book Press 18.png" alt=""><figcaption><p>填寫所需資料，確認無誤後按「Mint」</p></figcaption></figure>

出現 🎉 Success! 畫面代表經已成功鑄造 NFT，點「Continue to publish NFT Book」可繼續完成上架。點「View your NFT」可以到 [Liker Land](https://liker.land/) 查看已鑄造的 NFT 電子書。

<figure><img src="../../../.gitbook/assets/NFT Book Press 20.png" alt=""><figcaption><p>點「Continue to publish NFT Book」可繼續完成上架。點「View your NFT」可以到 Liker Land 查看已鑄造的 NFT 電子書</p></figcaption></figure>

由於現時還未上架販賣，所以會看到「售罄」字樣。

<figure><img src="../../../.gitbook/assets/NFT Book Press 21.png" alt=""><figcaption><p>還未上架販賣出現「售罄」字樣</p></figcaption></figure>

### 步驟二：上架 <a href="#publish-nft-book" id="publish-nft-book"></a>

回到 LikeCoin NFT BookPress，點「Continue to publish NFT Book」後出現 NFT Book Store Management Page 頁面。

{% hint style="info" %}
假如你不小心關掉了之前的頁面，你可以在[步驟一](./#mint-nft-book) Enter ISCN ID or NFT Class ID 一欄輸入你的 NFT Class ID 即可看到「Continue to publish NFT Book」。Class ID 是你的 NFT 電子書網址後面的一串。舉例你的 NFT 網址是 https://liker.land/zh-Hant/nft/class/likenft1qq06n42guzvt087wxunaajvz3alx6wadq6mfz0yz57gffwsrgrasl2m59x ，NFT Class ID 就是 likenft1qq06n42guzvt087wxunaajvz3alx6wadq6mfz0yz57gffwsrgrasl2m59x 。
{% endhint %}

在 New NFT Book Listing 自動出現 NFT Class ID 及 Total number of NFT for sale 即是經已鑄造的 NFT 電子書數量。

<figure><img src="../../../.gitbook/assets/NFT Book Press 22.png" alt=""><figcaption><p> 自動出現 NFT Class ID 及 Total number of NFT for sale 即是經已鑄造的 NFT 電子書數量</p></figcaption></figure>

在 Pricing and Availability 輸入以下內容：

* Default display currency when user checkout - 訂價為 USD 或 HKD
* Price(USD) of this book (Minimal 0.9 or free) - 最低價格為 0.9 美金，又或者輸入 0 代表免費送出
* Total number of NFT for sale of this edition - 這一個版本的 NFT 電子書銷售數量。留意 Total number of NFT for sale 指的是經已鑄造的 NFT 電子書數量，而 Total number of NFT for sale of this edition 則是設定這個特定版本的銷售數量。
* Product name of this edition - 可依照個人喜好為 NFT 設定版本，例如 Standard Edition 標準版、Free 免費版等。點右上角的「Add Edition」可以加入多個不同版本
* 在 Product description of this edition 可輸入 NFT 電子書版本的中英文描述

<figure><img src="../../../.gitbook/assets/NFT Book Press 23.png" alt=""><figcaption><p>在 Pricing and Availability 輸入各種內容</p></figcaption></figure>

此外用戶還可以設定是否搭配實體貨品作售賣 ( Physical Goods )，連結 Stripe 帳戶 ( Connect to your own Stripe Account ) 及指定 NFT 電子書的 PDF 檔案是否能被下載等等 ( Disable file download for PDF )。完成輸入後點「Submit」。

接著在 Current Listing 會出現已上架的書藉版本。

<figure><img src="../../../.gitbook/assets/NFT Book Press 24.png" alt=""><figcaption><p>在 Current Listing 出現已上架的書藉版本</p></figcaption></figure>

回到 Liker Land 查看，NFT 電子書經已成功上架。

<figure><img src="../../../.gitbook/assets/NFT Book Press 25.png" alt=""><figcaption><p>NFT 電子書經已成功上架</p></figcaption></figure>

***

### 匯入 epub 檔案到各家閱讀器

除了可使用 USB 方式匯入 epub 檔案到閱讀器。不同廠牌亦支援以網絡介面上載，更多詳情可參看：

* Readmoo - [桌機](https://cloudhey.medium.com/readmoo%E8%AE%80%E5%A2%A8%E9%9B%BB%E5%AD%90%E6%9B%B8%E9%80%B2%E9%9A%8E%E4%BD%BF%E7%94%A8%E7%B4%80%E9%8C%84-ebf534ab6408)、[iOS](https://news.readmoo.com/2023/05/24/new-new-update-133/)、[Android](https://news.readmoo.com/2023/04/07/new-new-update-128/)
* Kobo - [使用 Dropbox 將書籍新增至您的 eReader](https://help.kobo.com/hc/zh-tw/articles/360033830114-%E4%BD%BF%E7%94%A8-Dropbox-%E5%B0%87%E6%9B%B8%E7%B1%8D%E6%96%B0%E5%A2%9E%E8%87%B3%E6%82%A8%E7%9A%84-eReader)
* HyRead - [傳輸檔案&放書](https://www.youtube.com/watch?v=nQFnyYgDCCE)
* Pubook - [如何使用 Pubook 閱讀自己擁有的電子書檔案？](https://support.pubu.tw/hc/zh-tw/articles/12485186892185-%E5%A6%82%E4%BD%95%E4%BD%BF%E7%94%A8-Pubook-%E9%96%B1%E8%AE%80%E8%87%AA%E5%B7%B1%E6%93%81%E6%9C%89%E7%9A%84%E9%9B%BB%E5%AD%90%E6%9B%B8%E6%AA%94%E6%A1%88-)
* Kindle - [Send to Kindle](https://www.amazon.com/-/zh\_TW/gp/sendtokindle)
* Boox - [不用傳輸線 BOOX 如何分享文件？](https://boox.com.tw/?p=1052)
