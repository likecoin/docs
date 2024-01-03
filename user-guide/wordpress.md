---
description: 如何在自架 WordPress 網站加入 NFT 小部件，出版 WordPress 作品到區塊鏈？
---

# Web3Press

過往要把文章以 NFT 形式出版，工序很䌓複：作者須先把內容及元數據儲存在如 IPFS 等分散式空間或區塊鏈上，再上傳到 NFT 市場定價出售，過程中還要入手幾款不同用途的密碼貨幣。然而現在 WordPress 的用戶有福了，因為寫完文章以後只需按一個鍵，便能完成出版 NFT 的工序，內容立即上鏈，過程只需一分鐘！

LikeCoin [Web3Press plugin](https://zh-hk.wordpress.org/plugins/likecoin/) 為古騰堡編輯器度身訂造，讓 WordPress 網站一鍵接通 Web3，實現完整的分散式出版。功能包括：

* 抓取文章的標籤和標題等內容作為 NFT 的元數據
* 一鍵發佈文章到 [LikeCoin](https://like.co/) 並儲存於 [IPFS](https://ipfs.tech/) 及 [Arweave](https://www.arweave.org/) 分散式檔案系統並註冊 [ISCN](../general-guides/decentralized-publishing/what-is-iscn.md)
* 以 LikeCoin 一筆過支付內容上鏈及分散式儲存費用
* 鑄造 Writing NFT 後 [NFT 小部件 ( Widget )](../general-guides/writing-nft/collect-writing-nft/nft-widget.md) 自動在文章下方顯示，讓讀者[收集 NFT](../general-guides/writing-nft/collect-writing-nft/)，並整合 [LikeCoin button 讚賞鍵](creator/)功能
* 支援 [Internet Archive](https://archive.org/) 自動備份

由於內容備份了在分散式檔案系統，擁有 NFT 的讀者等於擁有了一份內容的正本，可以隨時閱覽。

#### 更多詳情

[Web3Press – 助 WordPress 作者邁向 Web3](https://blog.like.co/zh/web3press-%E5%8A%A9-wordpress-%E4%BD%9C%E8%80%85%E9%82%81%E5%90%91-web3/)

[Web3Press 於 WordCamp Asia 2023 熱烈登場 | LikeCoin 社群報](https://blog.like.co/zh/web3press-%E6%96%BC-wordcamp-asia-2023-likecoin-%E7%A4%BE%E7%BE%A4%E5%A0%B1/)

## 如何安裝 Web3Press <a href="#installation" id="installation"></a>

請執行以下步驟：

### 步驟一：登入 WordPress 管理員頁面

進入 WordPress 網站管理員頁面並登入（若網址是 www.abc.com ，管理員頁面一般便是 www.abc.com/wp-admin）。

### 步驟二：開始安裝

如圖點左方「外掛」，再點上方「安裝外掛」。

<figure><img src="../.gitbook/assets/wordpress 1.png" alt=""><figcaption><p>點「安裝外掛」</p></figcaption></figure>

### 步驟三：啟用外掛

搜尋關鍵字 "Web3Press" 或 "LikeCoin"，找到 Web3Press 外掛，點「立即安裝」並等待完成，再點「啟用」。

<figure><img src="../.gitbook/assets/wordpress 2.png" alt=""><figcaption><p>點「立即安裝」</p></figcaption></figure>

<figure><img src="../.gitbook/assets/wordpress 3.png" alt=""><figcaption><p>點「啟用」</p></figcaption></figure>

### 步驟四：完成安裝

安裝完成後，你會發現在左方的菜單中多了一個「Web3Press」的選項。恭喜你，你已經完成安裝了！

<figure><img src="../.gitbook/assets/wordpress 4.png" alt=""><figcaption><p>Web3Press 選項</p></figcaption></figure>

## 以 Keplr 簽署發佈 Writing NFT

在出版 Writing NFT 前請安裝 [Keplr 瀏覽器擴充功能](../general-guides/wallet/keplr/)並登入。此外亦需要 LikeCoin 進行操作，新用戶可使用[水龍頭](../general-guides/faucet.md)獲得少量 LikeCoin，或查看[購買 LikeCoin](../general-guides/trade/buy-likecoin.md) 的方式。

留意用戶並不需要註冊 Liker ID 也可以使用 Web3Press 去中心出版。

### 步驟一：開始發佈 Writing NFT

發佈文章後，在 Web3Press 底下點「Publish」。

<figure><img src="../.gitbook/assets/W3Press mint 1.png" alt=""><figcaption><p>點「Publish」</p></figcaption></figure>

彈出 Convert Content to Wrirting NFT 視窗及 Keplr 視窗，點「Approve」。

<figure><img src="../.gitbook/assets/W3Press mint 2.png" alt=""><figcaption><p>於 Keplr 視窗點「Approve」</p></figcaption></figure>

### 步驟二：預覽 Writing NFT

預覽你的 Writing NFT，如需添加或更改或生成 AI 封面可點「:pencil2:」，如不需更改 / 文章沒有圖片，將顯示文章預設的 OG 圖 / 不顯示圖片；你亦可以點「:pencil2:」更改 Writing NFT 的標題及簡介，詳情可到[發行 Writing NFT](../general-guides/writing-nft/nft-portal/) 了解更多。完成後點「Next」。

<figure><img src="../.gitbook/assets/W3Press mint 3.png" alt=""><figcaption><p>修改 Writing NFT 封面、標題及簡介後點「Next」</p></figcaption></figure>

你可為你的 Writing NFT 輸入作者給讀者的話，點「Add message to your collectors」並輸入訊息。此外如需要預留一些 Writing NFT 給自己及調整售價，可點「More settings」查多更多設定。

<figure><img src="../.gitbook/assets/W3Press mint 4.png" alt=""><figcaption><p>輸入 Writing NFT 作者留言及查看更多設定</p></figcaption></figure>

在 Numbers of NFTs reserved for giveaways 可輸入 0-255 之間的預留數量；

在 Sales Settings 可設定 Writing NFT 起始售價為 8、128、1024 或 4096 LIKE；

完成後點「Next」繼續。

<figure><img src="../.gitbook/assets/W3Press mint 5.png" alt=""><figcaption><p>輸入預留 Writing NFT 數量及設定起始售價</p></figcaption></figure>

彈出 Keplr 視窗數次以鑄造 Writing NFT，全部點「Approve」。

<figure><img src="../.gitbook/assets/W3Press mint 6.png" alt=""><figcaption><p>彈出 Keplr 視窗數次以鑄造 Writing NFT，全部點「Approve」</p></figcaption></figure>

### 步驟三：完成鑄造

出現 Complete! 頁面代表經已成功鑄造，點「View Your NFT」或在編輯介面點「View NFT」瀏覽你的 Writing NFT。

<figure><img src="../.gitbook/assets/W3Press mint 7.png" alt=""><figcaption><p>點「View Your NFT」</p></figcaption></figure>

<figure><img src="../.gitbook/assets/W3Press mint 8.png" alt=""><figcaption><p>點「View NFT」</p></figcaption></figure>

你也可以到 Liker Land [我的書架](../general-guides/writing-nft/collect-writing-nft/dashboard.md)查看你的創作。

<figure><img src="../.gitbook/assets/W3Press mint 9.png" alt=""><figcaption><p>到 Liker Land 我的書架查看創作</p></figcaption></figure>

## 設定 Liker ID <a href="#setting" id="setting"></a>

設定前請先[註冊 Liker ID](liker-id/)。

在管理介面左方菜單，點選 "Web3Press" 外掛設定，再選「Liker ID」。在右方畫面中，輸入 Liker ID 並點「Confirm」：

<figure><img src="../.gitbook/assets/wordpress 5.png" alt=""><figcaption><p>輸入 Liker ID</p></figcaption></figure>

<figure><img src="../.gitbook/assets/wordpress 6.png" alt=""><figcaption><p>點「Confirm」</p></figcaption></figure>

* Website Liker ID - 假如網站有多於一個作者，設定 Website Liker ID 後將於沒有設置 Liker ID 的作者文章顯示這個 Liker ID。
* You Liker ID - 設定你自己的 Liker ID。而成功新增 WordPress 網站新使用者後，新用戶以自己的 WordPress 帳號登入，便可設定自己的 Liker ID 並顯示自己的 NFT Widget / 讚賞鍵。

<figure><img src="../.gitbook/assets/wordpress 7.png" alt=""><figcaption><p>新增使用者</p></figcaption></figure>

## 更多有用功能 <a href="#publish-setting" id="publish-setting"></a>

### Publish to Internet Archive

填寫 Internet Archive S3 API Key 後即可於發佈文章時同步到 Internet Archive。

{% hint style="info" %}
Web3Press 支援 [Internet Archive](https://archive.org/)，用戶在發佈文章的同時可同步發佈到 Internet Archive 備份存檔，例子可參考《法庭線》的這[這篇文章](https://web.archive.org/web/20221215135952/https://thewitnesshk.com/%E6%94%AF%E8%81%AF%E6%9C%83%E6%8B%92%E4%BA%A4%E8%B3%87%E6%96%99%E6%A1%88-%E9%84%92%E5%B9%B8%E5%BD%A4%E6%8C%87%E9%80%9A%E7%9F%A5%E6%9B%B8%E5%B1%AC%E4%B8%8D%E5%8F%AF%E8%83%BD%E4%BB%BB%E5%8B%99-%E6%8B%92/)。

若你不知道什麼是 Internet Archive，它是一個非牟利數位圖書館，收藏書籍、電影、音樂及多達 6240 億個網頁存檔以供免費查閱，是網絡開放與自由化的倡議者。更多介紹可參看 ckxpress 有關 [DWeb Camp 之行的體驗分享](https://liker.land/nft/class/likenft1l6875l0mdvz4u9060t5nacd4xcx5ge5wlef2tj2jff2wkna93d2sfezzp9)。
{% endhint %}

<figure><img src="../.gitbook/assets/wordpress 11.png" alt=""><figcaption><p>Publish to Internet Archive 設定</p></figcaption></figure>

### Publish to Matters <a href="#publish-to-matters" id="publish-to-matters"></a>

由現在開始你可以把 WordPress 網站的文章同步到 Matters。只需簡單登入你的 Matters 電郵 ( Matters login email ) 及密碼 ( Password ) 再點「Login」即可完成設定。

撰寫文章時有三個選項：

* 自動儲存草稿到 Matters ( Auto save draft to Matters ) － 文章草稿將同步到你的 Matters 草稿箱。
* 自動發佈文章至 Matters ( Auto publish post to Matters )－ 當你在 WordPress 網站發佈文章時，該文章亦會同時於 Matters 發佈。
* 在頁尾增加原文鏈結 ( Add post link in footer ) － 在 Matters 文章中加入 WordPress 文章的原文鏈結。

<figure><img src="../.gitbook/assets/wordpress 10.png" alt=""><figcaption><p>Publish to Matters 設定</p></figcaption></figure>

在 Matters 上發布的作品皆會被上載到星際文件系統（InterPlanetary File System，IPFS）的節點之上。

### Web Monetization

啟用 Web monetization，[Coil](https://coil.com/) 訂戶訪問網站時可得到打賞。

<figure><img src="../.gitbook/assets/wordpress 12.png" alt=""><figcaption><p>Web Monetization 設定</p></figcaption></figure>

## 其他設定

### LikeCoin Widget

* Show in Posts：設定 Liker ID 後，預設為顯示 NFT Widget / 讚賞鍵於網站文章的下方
* Show in Pages：於 WordPress 頁面中顯示 NFT Widget / 讚賞鍵

<figure><img src="../.gitbook/assets/wordpress 8.png" alt=""><figcaption><p>LikeCoin Widget 設定在何處顯示 NFT Widget / 讚賞鍵</p></figcaption></figure>

### LikeCoin widget advanced settings

自訂每篇網站文章的 NFT Widge  / 讚賞鍵顯示設置。

<figure><img src="../.gitbook/assets/wordpress 9.png" alt=""><figcaption><p>LikeCoin widget advanced settings 自訂每篇網站文章的 NFT Widget / 讚賞鍵顯示設置</p></figcaption></figure>

{% hint style="info" %}
#### 於任何位置顯示 NFT Widget <a href="#how-to-support-multiple-liker-id-on-a-wordpress-site" id="how-to-support-multiple-liker-id-on-a-wordpress-site"></a>

你可使用短代碼 \[likecoin] 在文章中任何位置顯示額外的 NFT Widget / 讚賞鍵。
{% endhint %}

#### 廷伸閱讀[&#xD;](https://coralive.site/likecoin-wordpress%E4%B8%8A%E5%A6%82%E4%BD%95%E5%AE%89%E8%A3%9D%E8%A8%AD%E5%AE%9Alikecoin/) <a href="#read-more" id="read-more"></a>

> [請人幫忙分享、留言、拍手的好東西：「可重複使用區塊」](https://xrine.com/gutenburg-%E5%8F%AF%E9%87%8D%E8%A4%87%E4%BD%BF%E7%94%A8%E5%8D%80%E5%A1%8A/)

> [如何在 Medium 和 WordPress 設置錨點 (Anchor)](https://bchai.cc/2019/03/30/how-to-setup-anchor-medium-wordpress/)

### ISCN Badge <a href="#publish-to-iscn" id="publish-to-iscn"></a>

文章註冊 ISCN 後，可設定是否展示 ISCN badge。狀態分為不展示 ( Not shown )、正常模式 ( Light Mode ) 及深色模式 ( Dark Mode )，選擇後點「Confirm」確認。

<figure><img src="../.gitbook/assets/wordpress 13.png" alt=""><figcaption><p>ISCN Badge 設定</p></figcaption></figure>
