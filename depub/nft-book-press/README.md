---
description: 使用 NFT Book Press 將電子書出版為 NFT
---

# 出版 NFT 電子書

{% hint style="info" %}
出版前可參考 [上架 Liker Land NFT 電子書的常見問題](nft-book-press-faq.md)
{% endhint %}

{% hint style="info" %}
出版 NFT 電子書需使用桌面電腦及 [LikeCoin](https://like.co/)
{% endhint %}

在區塊鏈出版 NFT 電子書包含以下流程：

1. [備妥 EPUB 檔](./#edit-metadata)
2. [註冊 ISCN](./#register-iscn)
3. [上架銷售](./#nft-book-store)

並可進行其他後續操作：

4. [設置 Liker Land 書店作者簡介](./#creators-introduction)
5. [NFT Book Press 用戶設定](user-setting/)
6. [發送 NFT 電子書及群發 NFT 紀念品到多個錢包](./#fa-song-nft-ji-qun-fa-nft-ji-nian-pin-dao-duo-ge-qian-bao)
7. [匯入 EPUB 檔案到各家閱讀器](./#ereader)
8. [管理 NFT 電子書](nft-book-store.md)
9. [設定 NFT 電子書套裝](collection.md)
10. [補書上架](replenishment.md)
11. [修改已出版的 NFT 電子書資料](modify-nft-ebook.md)
12. [銷毁已出版的 NFT 電子書](burn-nft-ebook.md)

參看短片了解出版原理（留意以下影片使用 Keplr 登入，如使用 Email/Social 登入流程將更為簡單）：

[5 分鐘出版電子書到區塊鏈（國語 TTS 旁白）](https://www.youtube.com/watch?v=QppGdM-EtBY)

[5 分鐘出版電子書到區塊鏈（廣東話 TTS 旁白）](https://www.youtube.com/watch?v=T08nI\_G1c8E)

***

## 製作 EPUB 檔案並輸入元數據 <a href="#edit-metadata" id="edit-metadata"></a>

首先製作好電子書的 [EPUB](https://zh.wikipedia.org/zh-hk/EPUB) 檔案，並確保經已輸入並整理好 Metadata。Metadata 即是[元數據](../what-is-iscn/)。包括書名、作者、封面圖、出版日期、描述等內容。以常用的 EPUB 編輯軟件為例：

#### calibre

在 [calibre](https://calibre-ebook.com/) 編輯元數據的按鈕就在畫面的左上角 Edit Metadata，整理好元數據後記緊按 Save to disk。

<figure><img src="../../.gitbook/assets/NFT Book Press 1.png" alt=""><figcaption><p>在 calibre 點 Edit Metadata 開啟編輯元數據介面，完成後按 Save to disk</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/NFT Book Press 2.png" alt=""><figcaption><p>編輯元數據後按「OK」</p></figcaption></figure>

#### Sigil

在 [Sigil](https://sigil-ebook.com/) 可按 F8 鍵可即時編輯元數據。

<figure><img src="../../.gitbook/assets/NFT Book Press 3.png" alt=""><figcaption><p>在 Sigl 按 F8 鍵編輯元數據</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/NFT Book Press 4.png" alt=""><figcaption><p>編輯元數據後按「確定」</p></figcaption></figure>

***

## 註冊 ISCN <a href="#register-iscn" id="register-iscn"></a>

準備好 EPUB 檔案後，接下來把它註冊成 ISCN。

### 步驟一：上載檔案 <a href="#upload-file" id="upload-file"></a>

到 [app.like.co](https://app.like.co/) 網站，點「Register ISCN」。

<figure><img src="../../.gitbook/assets/NFT Book Press 5.png" alt=""><figcaption><p>到 app.like.co 網站，點「Register ISCN」</p></figcaption></figure>

彈出視窗並連結錢包，**建議使用 Email/Social 註冊 Liker ID 並登入**，詳見：

{% content-ref url="../../user-guide/liker-id/register/" %}
[register](../../user-guide/liker-id/register/)
{% endcontent-ref %}

<figure><img src="../../.gitbook/assets/NFT Book Press 6.png" alt=""><figcaption><p>彈出視窗並連結錢包</p></figcaption></figure>

登入後點「Select a file」上載已預備好的 EPUB 檔案。

<figure><img src="../../.gitbook/assets/NFT Book Press 7.png" alt=""><figcaption><p>點「Select a file」上載已預備好的 EPUB 檔案</p></figcaption></figure>

系統會自動把 EPUB 檔案內容分解成兩個檔案，一個是 EPUB 檔案，另一個是封面圖檔。如果沒有問題點「Start Upload」，系統會將這兩個檔案上傳到分散式網絡。

<figure><img src="../../.gitbook/assets/NFT Book Press 8.png" alt=""><figcaption><p>點「Start Upload」將檔案上傳到分散式網絡</p></figcaption></figure>

### 步驟二：輸入書籍資料 <a href="#metadata" id="metadata"></a>

出現 File Ready 代表檔案上傳成功，系統會依照元數據內容生成以下資料，如有需要可作修改：

<figure><img src="../../.gitbook/assets/NFT Book Press 10.png" alt=""><figcaption><p>File Ready 頁面</p></figcaption></figure>

1. Type：顯示 ISCN 種類為 Book 即 NFT 電子書。
2. ISCN Title：書名
3. Description：描述
4. Author：作者
5. Stakeholders：持份者。系統預設加入作者及正在製作 NFT 電子書的帳戶為持份者。
6. Tags：標籤，可加入作為分類。
7. Downloadable URL：下載書檔時所顯示的名稱
8. URL：書檔所對應的 URL
9. License：可以選擇合適的版權宣告，預設是版權所有 ( Copyright. All rights reserved. )
10. Content Fingerprints：顯示書檔及封面 Hash 網址，每兩條 Hash 對應一個檔案。包括 [IPFS](https://ipfs.tech/) 及 [AR ( Arweave ) ](https://www.arweave.org/)格式。以附圖為例，四條 Hash 代表 IPFS 的 EPUB 檔、IPFS 的封面檔、AR 的 EPUB 檔和 AR 的封面檔，不妨點擊網址核對並查看內容是否經已成功上傳。
11. \+Other settings：點開它出現 URL 可輸入書籍的網址及 ISBN 輸入 ISBN 號碼。

完成後點「Register」。

<figure><img src="../../.gitbook/assets/NFT Book Press 11.png" alt=""><figcaption><p>點「Register」註冊 ISCN</p></figcaption></figure>

### 步驟三：註冊 ISCN 完成 <a href="#successfully-registered-iscn" id="successfully-registered-iscn"></a>

出現 Completed! Here is your ISCN 說明 ISCN 經已成功註冊。留意 ISCN ID 欄位的一串字符接下來於 NFT 電子書上架時將需要用到。圖中的 /1 是這個 ISCN 第 1 個版本的意思。

<figure><img src="../../.gitbook/assets/NFT Book Press 15.png" alt=""><figcaption><p>成功註冊並出現 ISCN ID</p></figcaption></figure>

***

## 上架銷售 <a href="#nft-book-store" id="nft-book-store"></a>

上架銷售分開兩個步驟：鑄造 NFT 電子書及上架。類比傳統出版就是將書稿印刷成書和上架販賣。

### 步驟一：鑄造 NFT 電子書 <a href="#mint-nft-book" id="mint-nft-book"></a>

在 ISCN 記錄右上角點「Mint Book」。

<figure><img src="../../.gitbook/assets/NFT Book Press 9.png" alt=""><figcaption><p>點「Mint Book」</p></figcaption></figure>

系統會自動跳轉到 [LikeCoin NFT Book Press](https://likecoin.github.io/nft-book-press/) 網站，並於 Enter ISCN ID or NFT Class ID 一欄預先輸入ISCN ID。點右上角「Sign In」登入網站後再點「Submit」。

<figure><img src="../../.gitbook/assets/NFT Book Press 17.png" alt=""><figcaption><p>在 Enter ISCN ID or NFT Class ID 一欄輸入 ISCN ID</p></figcaption></figure>

又或者直接到 [LikeCoin NFT Book Press](https://likecoin.github.io/nft-book-press/) 網站，點「Mint NFT」，進入網站後按右上角「Sign In」登入。並於 Enter ISCN ID or NFT Class ID 一欄手動輸入早前註冊的 ISCN ID 再點「Submit」。

<figure><img src="../../.gitbook/assets/NFT Book Press 16.png" alt=""><figcaption><p>到 LikeCoin NFT BookPress 網站，點「Mint NFT」</p></figcaption></figure>

{% hint style="info" %}
假如你忘記了你的 ISCN ID，可以隨時到 app.like.co 的 [My Works](https://app.like.co/works) 找回它。
{% endhint %}

系統會為你自動抽出 ISCN 的基本資料，接著你需要於「By filling required information」分頁填寫其他資料：

* 在 Number of NFT to mint 一欄輸入需要鑄造多少個 NFT
* 如若你的書檔是 EPUB，系統會自動抽出 AR 封面的連結放在 image URL 一欄
* External URL (optional)、URI (optional) 及 Max number of supply for this NFT Class (optional) 可按需要填寫。

填寫完成並確認無誤後按「Mint」。

<figure><img src="../../.gitbook/assets/NFT Book Press 18.png" alt=""><figcaption><p>填寫所需資料，確認無誤後按「Mint」</p></figcaption></figure>

出現 🎉 Success! 畫面代表經已成功鑄造 NFT，點「Continue to publish NFT Book」可繼續完成上架。點「View your NFT」可以到 [Liker Land](https://liker.land/) 查看已鑄造的 NFT 電子書。

<figure><img src="../../.gitbook/assets/NFT Book Press 20.png" alt=""><figcaption><p>點「Continue to publish NFT Book」可繼續完成上架。點「View your NFT」可以到 Liker Land 查看已鑄造的 NFT 電子書</p></figcaption></figure>

由於現時還未上架販賣，所以會看到「售罄」字樣。

<figure><img src="../../.gitbook/assets/NFT Book Press 21.png" alt=""><figcaption><p>還未上架販賣出現「售罄」字樣</p></figcaption></figure>

### 步驟二：上架 <a href="#publish-nft-book" id="publish-nft-book"></a>

回到 LikeCoin NFT BookPress，點「Continue to publish NFT Book」後出現 NFT Book Store Management Page 頁面。

{% hint style="info" %}
假如你不小心關掉了之前的頁面，你可以在[步驟一](./#mint-nft-book) Enter ISCN ID or NFT Class ID 一欄輸入你的 NFT Class ID 即可看到「Continue to publish NFT Book」。Class ID 是你的 NFT 電子書網址後面的一串。舉例你的 NFT 網址是 https://liker.land/zh-Hant/nft/class/likenft1qq06n42guzvt087wxunaajvz3alx6wadq6mfz0yz57gffwsrgrasl2m59x ，NFT Class ID 就是 likenft1qq06n42guzvt087wxunaajvz3alx6wadq6mfz0yz57gffwsrgrasl2m59x 。
{% endhint %}

#### New NFT Book Listing

在 New NFT Book Listing 出現已鑄造 NFT 電子書的 NFT Class ID。

<figure><img src="../../.gitbook/assets/NFT Book Press 22.png" alt=""><figcaption><p>在 New NFT Book Listing 出現已鑄造 NFT 電子書的 NFT Class ID</p></figcaption></figure>

#### Pricing and Availability

* Unit Price in USD (Minimum 0.99 or 0 for free) - 最低價格為 0.9 美金，又或者輸入 0 代表免費送出
* Total number of NFT ebook/edition for sale - 填寫這一個版本的 NFT 電子書銷售數量。假設你鑄造了 10 本書，可以設定 5 本書為版本一、另外 5 本書為版本二之類。點下方的「Add Edition」可加入多個不同版本。留意每一個版本可供銷售的 NFT 電子書數量加起來不能多於已鑄造的數量。
* Delivery method of this book
  * Automatic deliver NFT - 自動傳送 NFT 電子書給讀者。選項一經設定，不能修改。
  * Sign memo and manually deliver each NFT - 自行簽署並手動傳送 NFT 電子書給讀者
* Memo of this book - 於傳送 NFT 電子書時自動加入給讀者的話
* Allow custom price - 設定讀者購買電子書的時候可[額外支持作者](../nft-ebook/)

<figure><img src="../../.gitbook/assets/NFT Book Press 23.png" alt=""><figcaption><p>在 Pricing and Availability 輸入各種內容</p></figcaption></figure>

#### Product Information

* Product name - 可依照個人喜好為 NFT 電子書設定版本，例如 Standard Edition 標準版、Free 免費版等
* Description (Optional) - 可輸入 NFT 電子書版本的中英文描述

#### Shipping Optioins

Physical Goods - 選取 Includes physical good that requires shipping 後代表書籍版本為實體書，讀者需要支付寄送費用。點「View Current Shipping Options」可查看現時已設定的寄送方式。

<figure><img src="../../.gitbook/assets/NFT Book Press 23a.png" alt=""><figcaption><p>Product Information 與 Shipping Optioins</p></figcaption></figure>

#### Shipping Options Info

* Name of the shipping option - 填寫寄送方式的中英文名稱
* Price(USD) of this shipping option - 該寄送方式以美元計算的費用

點「Set Shipping Options」儲存該寄送方式，點「Add Options」增加更多寄送方式，完成後點「Save」。

<figure><img src="../../.gitbook/assets/NFT Book Press 23f.png" alt=""><figcaption><p>Shipping Options</p></figcaption></figure>

#### Connect to a Stripe  Account

連結 Stripe 帳戶，點擊後將開始連結 Stripe 帳戶，詳見：

{% content-ref url="user-setting/stripe.md" %}
[stripe.md](user-setting/stripe.md)
{% endcontent-ref %}

#### Email to receive sales notification

輸入需要接收銷售通知的電郵地址，再點「Add」

<figure><img src="../../.gitbook/assets/NFT Book Press 23b.png" alt=""><figcaption><p>Connect to a Stripe  Account 與 Email to receive sales notification</p></figcaption></figure>

#### Advance Settings

點 Advance Settings 可額外輸入以下內容：

* Default Display Currency at Check out - 將預設顯示美元改為顯示港元
* Shipping Options - 寄送費用選項
* Share sales data to wallets - 輸入需要接收銷售數據的錢包地址，再點「Add」
* Send NFT Grant - 如選擇了 Automatic deliver NFT，Liker Land 預設擁有「Grant」權限為你自動傳送 NFT 電子書
* DRM Options
  * Force NFT claim before view - 選取 Must claim NFT to view 代表讀者一定要領取 NFT 電子書方可閱讀
  * Insert cutomized message page in eBook - 自動插入訊息於 NFT 電子書中
  * Disable File Download - 選取 Disable Download 代表不讓讀者下載 NFT 電子書，只容許線上閱讀
* Coupon Codes - 點「Add New」設定優惠券：
  * Coupon Code - 設定優惠券的名稱
  * Discount Multiplier - 優惠幅度，例如 10% 即九折優惠
  * Expiry Date - 優惠結束期限
  * 設定完成後點「Add」加入優惠券。
* Copy Purchase Link - 設定購買連結
  * Price - 選擇哪一個版本的 NFT 電子書
  * Sales channel for this link - 輸入名字，為你的銷售渠道設定專屬購買連結以便促銷
  * Copy Purchase Link」 - 點「Copy Purchase Link」復製銷售渠道專屬連結
  * Purchase Link QR Code - 點「Download」下載專屬連結的 QR Code

<figure><img src="../../.gitbook/assets/NFT Book Press 23c.png" alt=""><figcaption><p>Advance Settings</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/Manage NFT Books 6.png" alt=""><figcaption><p>Coupon Codes</p></figcaption></figure>

完成設定後點「Submit」。假如用戶選擇 Automatic deliver NFT，將出現提示說明一但選擇自動傳送 NFT 電子書給讀者將不能更改為手動。確認無誤後點「OK」。

<figure><img src="../../.gitbook/assets/NFT Book Press 23e.png" alt=""><figcaption><p>確認無誤後點「OK」</p></figcaption></figure>

接著在 Current Listing 會出現已上架的書藉版本。

<figure><img src="../../.gitbook/assets/NFT Book Press 24.png" alt=""><figcaption><p>在 Current Listing 出現已上架的書藉版本</p></figcaption></figure>

回到 Liker Land 查看，NFT 電子書經已成功上架。

<figure><img src="../../.gitbook/assets/NFT Book Press 25.png" alt=""><figcaption><p>NFT 電子書經已成功上架</p></figcaption></figure>

***

## 設置 Liker Land 書店作者簡介 <a href="#creators-introduction" id="creators-introduction"></a>

建議設置創作者個人簡介、圖片及顯示名稱讓你的支持者更加了解你。

{% content-ref url="../../user-guide/liker-id/edit-avatar-displayname.md" %}
[edit-avatar-displayname.md](../../user-guide/liker-id/edit-avatar-displayname.md)
{% endcontent-ref %}

## 發送 NFT 電子書及群發 NFT 禮物到多個錢包 <a href="#transfer-nft-ebook" id="transfer-nft-ebook"></a>

將作品發送到個別錢包又或者將 NFT 電子書作為禮物群發到多個錢包。

{% content-ref url="../transfer-writing-nft/" %}
[transfer-writing-nft](../transfer-writing-nft/)
{% endcontent-ref %}

{% content-ref url="nft-book-store.md" %}
[nft-book-store.md](nft-book-store.md)
{% endcontent-ref %}

## 匯入 EPUB 檔案到各家閱讀器 <a href="#ereader" id="ereader"></a>

除了可使用 USB 方式匯入 EPUB 檔案到閱讀器。不同廠牌亦支援以網絡介面上載，更多詳情可參看：

* Readmoo - [桌機](https://cloudhey.medium.com/readmoo%E8%AE%80%E5%A2%A8%E9%9B%BB%E5%AD%90%E6%9B%B8%E9%80%B2%E9%9A%8E%E4%BD%BF%E7%94%A8%E7%B4%80%E9%8C%84-ebf534ab6408)、[iOS](https://news.readmoo.com/2023/05/24/new-new-update-133/)、[Android](https://news.readmoo.com/2023/04/07/new-new-update-128/)
* Kobo - [使用 Dropbox 將書籍新增至您的 eReader](https://help.kobo.com/hc/zh-tw/articles/360033830114-%E4%BD%BF%E7%94%A8-Dropbox-%E5%B0%87%E6%9B%B8%E7%B1%8D%E6%96%B0%E5%A2%9E%E8%87%B3%E6%82%A8%E7%9A%84-eReader)
* HyRead - [傳輸檔案&放書](https://www.youtube.com/watch?v=nQFnyYgDCCE)
* Pubook - [如何使用 Pubook 閱讀自己擁有的電子書檔案？](https://support.pubu.tw/hc/zh-tw/articles/12485186892185-%E5%A6%82%E4%BD%95%E4%BD%BF%E7%94%A8-Pubook-%E9%96%B1%E8%AE%80%E8%87%AA%E5%B7%B1%E6%93%81%E6%9C%89%E7%9A%84%E9%9B%BB%E5%AD%90%E6%9B%B8%E6%AA%94%E6%A1%88-)
* Kindle - [Send to Kindle](https://www.amazon.com/-/zh\_TW/gp/sendtokindle)
* Boox - [不用傳輸線 BOOX 如何分享文件？](https://boox.com.tw/?p=1052)
