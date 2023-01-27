---
description: 把任何網頁文章內容出版成 NFT
---

# NFT Portal

## 📣Writng NFT 功能依然處於初期發展階段，我們誠意邀請創作者參與早期測試反饋意見，一起改善產品，有興趣者請申請加入 [Writing NFT 白名單](https://docs.google.com/forms/u/1/d/e/1FAIpQLSdPkunbI-68k7dzDqNNDX0U8Lr6lg3R2Jsm-RPduUNQ9Om05Q/viewform?usp=send\_form)。

## 📣鑄造 Writing NFT 需要使用 LikeCoin，用戶可於水龍頭取得少量 LikeCoin 以作測試

{% content-ref url="../faucet.md" %}
[faucet.md](../faucet.md)
{% endcontent-ref %}



若作者不是使用 [WordPress](writing-nft-wordpress-plugin.md) 網站：

**選擇一：**可到 **** [**NFT Portal**](https://app.like.co/nft/url) 網站貼上文章的網址，系統會自動抓取文章標題及把文章內容儲存到分散式檔案系統成為 ISCN 並生成 NFT

**選擇二**：將文章的文字、PDF、圖片、聲音…先[註冊成 ISCN](../decentralized-publishing/app.like.co.md)，再將 ISCN ID 貼到 [NFT Portal](https://app.like.co/nft/url) 生成 NFT

出版 Writing NFT 後可以 iframe 的方式把 [NFT Widget](collect-writing-nft/nft-widget.md) 嵌入文章，但需手動把 Portal 生成的 ISCN 填作 widget 的參數，詳見 [LikeCoin button 讚賞鍵](../../user-guide/creator/)章節。

## 登入 NFT Portal

直接進入 [NFT Porta](https://app.like.co/nft/url)l 並以 [Keplr Browser Extension](../wallet/keplr/) 或 [Liker Land app](../../user-guide/liker-id/register-with-keplr.md) 登入網站。

![](<../../.gitbook/assets/NFT Portal 1.png>)

### **Keplr Browser Extension 登入**

請於瀏覽器登入 [Keplr Browser Extension](../wallet/keplr/)，點「Keplr Wallet」後彈出視窗要求連結，點「Approve」。

<figure><img src="../../.gitbook/assets/NFT Portal 1a.png" alt=""><figcaption></figcaption></figure>

### Liker Land app 登入

點「Liker ID」後出現二維碼。

<figure><img src="../../.gitbook/assets/NFT Portal 1b.png" alt=""><figcaption></figcaption></figure>

在 [Liker Land 手機應用程式](../../user-guide/liker-land/download.md)點二維碼圖示調用鏡頭，並掃瞄二維碼。

<figure><img src="../../.gitbook/assets/NFT Portal 1c.png" alt=""><figcaption></figcaption></figure>

彈出 ISCN App 視窗，點「允許」。

<figure><img src="../../.gitbook/assets/NFT Portal 1d.png" alt=""><figcaption></figcaption></figure>

成功登入後右上角將顯示你的錢包地址及註冊頁面。

<figure><img src="../../.gitbook/assets/NFT Portal 1e.png" alt=""><figcaption></figcaption></figure>

## 以文章網址出版 Writing NFT

### 步驟 1/4：註冊 ISCN <a href="#register-iscn" id="register-iscn"></a>

假如文章並未註冊 ISCN，請直接把文章網址輸入空格並點「Register ISCN」。

{% hint style="info" %}
留意如果將網址直接以這個方法註冊 ISCN 並出版 Writing NFT，系統會自動抓取文章標題及內容作為元資料。

**如希望作品擁有詳盡元資料，請先** [**註冊 ISCN**](../decentralized-publishing/app.like.co.md) **再** [**以 ISCN ID 出版 Writing NFT**](nft-portal.md#yi-iscn-id-chu-ban-writing-nft)**。**&#x20;
{% endhint %}

<figure><img src="../../.gitbook/assets/NFT Portal 2.png" alt=""><figcaption></figcaption></figure>

#### Keplr

彈出 Keplr 視窗，點「Approve」。

<figure><img src="../../.gitbook/assets/NFT Portal 3.png" alt=""><figcaption></figcaption></figure>

再次彈出 Keplr 視窗，點「Approve」。

<figure><img src="../../.gitbook/assets/NFT Portal 4.png" alt=""><figcaption></figcaption></figure>

### 步驟 2/4：預覽Writing NFT <a href="#preview-nft" id="preview-nft"></a>

出現 Writing NFT 預覽頁面，點「Next」。

<figure><img src="../../.gitbook/assets/NFT Portal 5.png" alt=""><figcaption></figcaption></figure>

### 步驟 3/4：輸入作者的話 <a href="#creator-message" id="creator-message"></a>

作者的話是作者於每篇文章顯示的特別段落。與轉贈時附加留言不同的是，同一個合集下的所有 Writing NFT 將共用同一段作者的話，並儲存於鏈上的 NFT class 資料中。

點「Add mesage to your collectors」輸入作者的話。

<figure><img src="../../.gitbook/assets/NFT Portal 6.png" alt=""><figcaption></figcaption></figure>

彈出視窗，輸入內容後點「Confirm」。注意訊息不能寫超過 256個字元。

<figure><img src="../../.gitbook/assets/NFT Portal 7.png" alt=""><figcaption></figcaption></figure>

再次查看內容是否正確，如需要修改可按「Edit」，否則按「Next」繼續。

<figure><img src="../../.gitbook/assets/NFT Portal 8.png" alt=""><figcaption></figcaption></figure>

### 步驟 4/4：完成簽署 <a href="#sign" id="sign"></a>

彈出 Keplr 視窗以取得 Class ID，點「Approve」兩次。

<figure><img src="../../.gitbook/assets/NFT Portal 9.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/NFT Portal 10.png" alt=""><figcaption></figcaption></figure>

再次彈出 Keplr 視窗以鑄造 NFT，點「Approve」。

<figure><img src="../../.gitbook/assets/NFT Portal 11.png" alt=""><figcaption></figcaption></figure>

出現「Done」及 Writing NFT 網址即代表 NFT 已鑄造完成，點「View NFT」查看。

<figure><img src="../../.gitbook/assets/NFT Portal 12.png" alt=""><figcaption></figcaption></figure>

Writing NFT 已成功鑄造並可供其他用戶購買，然而在內容頁面並沒法看到於步驟 3/4 所輸入的訊息。

<figure><img src="../../.gitbook/assets/NFT Portal 13.png" alt=""><figcaption></figcaption></figure>

當收藏者購買該 Writing NFT 就會看到訊息了。

<figure><img src="../../.gitbook/assets/NFT Portal 14.png" alt=""><figcaption></figcaption></figure>

#### Liker Land app

步驟與 Keplr 用戶完全相同，只是在手機上出現數次簽名請求時請一律點「允許」。

![](<../../.gitbook/assets/NFT Portal 3a.png>)

## 以 ISCN ID 出版 Writing NFT

假如你的文章經已註冊 ISCN，你同樣可以使用 **** [**NFT Portal**](https://app.like.co/nft/url) 網站出版 Writing NFT。

### 為 Matters 文章註冊 ISCN

以 Matters 為例，用戶可以在發佈前選擇一拼註冊 ISCN。

![](<../../.gitbook/assets/NFT Portal ISCN 1 (1).png>)

#### 影片教學

{% embed url="https://www.youtube.com/watch?v=y0_mmmIqp3E&t" %}

### 方法 1：查找 ISCN 後直接出版 Writing NFT

文章刊出後，到 [app.like.co](https://app.like.co/) 的「[My Publishing](https://app.like.co/works)」尋找已註冊文章的 ISCN，點右上角「Mint NFTs」直接將 ISCN 鑄造為 Writing NFT，所需步驟與[以文章網址出版 Writing NFT 步驟 2-4/4](nft-portal.md#preview-nft) 完全相同。

<figure><img src="../../.gitbook/assets/NFT Portal ISCN 4.png" alt=""><figcaption></figcaption></figure>

### 方法 2：複製 ISCN ID 再出版 Writing NFT

到 [app.like.co](https://app.like.co/) 的「[My Publishing](https://app.like.co/works)」尋找已註冊文章的 ISCN ID 並把它複製。

<figure><img src="../../.gitbook/assets/NFT Portal ISCN 2.png" alt=""><figcaption></figcaption></figure>

到 **** [NFT Portal](https://app.like.co/nft/url) 的空格輸入 ISCN ID 並點「Register ISCN」，餘下步驟與[以文章網址出版 Writing NFT 步驟 2-4/4](nft-portal.md#preview-nft) 完全相同。

<figure><img src="../../.gitbook/assets/NFT Portal ISCN 3.png" alt=""><figcaption></figcaption></figure>

#### 影片教學

{% embed url="https://www.youtube.com/watch?v=X0uLaPOkucA" %}

## 把語音檔出版成 Writing NFT

{% embed url="https://www.youtube.com/watch?v=YkVZzYVeT_E" %}

## 設置作者簡介

設置個人簡介、圖片及顯示名稱讓你的支持者更加了解你吧！（必須註冊 Liker ID）

{% content-ref url="../../user-guide/liker-id/edit-avatar-displayname.md" %}
[edit-avatar-displayname.md](../../user-guide/liker-id/edit-avatar-displayname.md)
{% endcontent-ref %}

## 群發 NFT 紀念品給支持者

#### 影片教學

{% embed url="https://www.youtube.com/watch?v=APw46UIzJLM" %}

#### **詳盡介紹**

{% embed url="https://blog.like.co/zh/%E4%BB%A5%E6%96%87%E6%9C%83%E5%8F%8B%E7%9A%84%E4%BA%BA%E6%83%85%E5%91%B3%E5%92%8C%E7%A9%BA%E9%96%93%E6%84%9F-%E8%B3%BC%E8%B2%B7-writing-nft-%E6%99%82%EF%BC%8C%E7%95%99%E8%A8%80%E7%B5%A6/" %}

**步驟一**：在 [LikeCoin NFT Dashboard](https://likecoin.github.io/likecoin-nft-dashboard/#/) 搜尋（Search）自己錢包的收藏者 ( Get Collector )。

**步驟二**：導出所有數據 ( Export all data )。

**步驟三**：將數據的 csv 導入試算表工具進行分類與排序，並將支持者錢包地址整理成清單。

**步驟四**：在 [LikeCoin NFT Marketplace](https://likecoin.github.io/likecoin-nft-marketplace/) 的介面工具 ( Tools ) 中選 Send NFTs 並登入 Keplr。

**步驟五**：在用以群發給支持者的 Writing NFT 找出 NFT Class ID。

**步驟六**：將 NFT Class ID 輸入 Send NFTs 工具，並輸入支持者的錢包地址清單 ( Recepient Address list ) 及留給他們的話 ( Transfer message ) ，再按「Send」及在 Keplr 簽署，即可群發 NFT。
