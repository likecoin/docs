---
description: 將電子書發行為 NFT
---

# 發行 NFT 書（測試版）

### 📣發行 Writing NFT 需要 LikeCoin，用戶可以從[水龍頭](../faucet.md)獲取少量 LikeCoin 進行測試。&#x20;

### 📣此說明需要具備執行 node.js 語法及編輯 JSON 文件的技術知識

## 事前準備

### 預備你的電子書文檔

在發布 NFT 書籍之前，你必須預備好電子書文檔，該文檔可以是任何流行的電子書格式，例如 pdf 或 epub。本指南不包括介紹如何製作電子書文檔。

### 預備好你的 NFT 書封面

你必須為你的 NFT 書至少準備兩張封面圖片，一張用於列表模式 ( listing view )，另一張用於書籍詳細資料模式 ( book detail view )。列表模式圖片供用戶瀏覽書店的 NFT書資紏，而書籍詳細資料模式則是每本 NFT 書的獨特封面。

### 準備好你的「圖書資料」頁面

圖書資料頁是列出書籍資料的單一頁面，例如作者及出版商的資料、書籍介紹及推薦等。它可以是任何類型的網頁。

### 準備元資料

在出版 NFT 書之前，最好令你的書籍元資料 ( metadata ) 盡可能完整。但是如有必要，你也通過更新書的 ISCN 的版本不斷更新元資料。書籍元資料包括但不限於作者姓名、書籍名稱、持份者及其錢包地址、書籍描述、使用條款等。

### 準備資料文檔  <a href="#preparing-the-data-files" id="preparing-the-data-files"></a>

於 [https://github.com/likecoin/iscn-nft-tools/tree/master/mint-nft](https://github.com/likecoin/iscn-nft-tools/tree/master/mint-nft) 目錄下獲得一些 JSON 格式的示範資料文件。你必須準備好必要的資料文檔。資料文檔的定義如下：

**iscn.json**

| 欄位                            | 內容                                                                                                                                                                     |
| ----------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| contentMetadata → url         | 書籍資料的 URL。例如：https://ckxpress.com/moneyverse/ 是 NFT 詳細資料資料頁面「瀏覽內容」按鍵的鏈接，位於 NFT 主圖的下方。                                                                                  |
| contentMetadata → name        | ISCN 標題                                                                                                                                                                |
| contentMetadata → type        | “Book”（NFT 的類型）                                                                                                                                                        |
| contentMetadata → version     | ISCN 版本號碼                                                                                                                                                              |
| contentMetadata → context     | "[http://schema.org/](http://schema.org/)"                                                                                                                             |
| contentMetadata → keywords    | 格式為："a, b, c, d"                                                                                                                                                       |
| contentMetadata → usageInfo   | 例：CC BY-SA 4.0                                                                                                                                                         |
| contentMetadata → sameAs      | NFT Book 的其他 URL 表達陣列。如果 URL 以 .epub 或 .pdf 結尾，Liker Land 中將出現一個獨特的瀏覽按鍵。例如：\["https://url/book.epub", "https://url/book.pdf"]                                          |
| contentMetadata → description | ISCN 的描述                                                                                                                                                               |
| stakeholders                  | 待份者的資料列表，例如 { "contributionType":"http://schema.org/author", "entity": { "@id":"like13f4glvg80zvfrrs7utft5p68pct4mcq7t5atf6", "name":"高重建" }, "rewardProportion":"2" } |
| contentFingerprint            | 分散式儲存哈希，例如："ipfs://QmVsa6WuHLiZtyfwQrFjgxwLvVqMPsvvvusTdCKmTyqkca"，"ar://e-bMr7c3O\_sm20zb7X5Vu870Q8b-Pc7eIxmjYXgJmsI"                                                 |
| recordNotes                   | 保留                                                                                                                                                                     |

**​​**

<figure><img src="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LL4mdaVjNgL6A1--PV0-1972196547%2Fuploads%2FZZ2EgkjFmyXs9mwNexNW%2Fimage.png?alt=media&#x26;token=e9c15bd8-4a3c-4e15-b89b-cafa937d0805" alt=""><figcaption></figcaption></figure>

**nft\_class.json**

| 名稱                                           | NFT 標題顯示於 NFT 展示櫃/儀表板、類別資訊及詳細資料模式                                                                                                                        |
| -------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| description                                  | 於類別資訊及詳細資料模式的 NFT 描述。                                                                                                                                    |
| symbol                                       | 保留。                                                                                                                                                      |
| uri                                          | <p>可選，預設值設定為空。<br></p><p>高級用法：API 生成圖片的 URI 並使用它作為 NFT 類別的 og 圖片，展示於 liker.land 的 NFT 展示櫃/儀表板及類別資訊中，如果 nfts.csv 與nfts_default.json 設定不正確，也將顯示於詳細資料中。</p> |
| metadata → image                             | 圖片的 URL 作為 NFT 的 og 圖片，並展示於 liker.land 的 NFT 展示櫃/儀表板及類別資訊中，如果 nfts.csv 與 nfts\_default.json 設定不正確，也將顯示於詳細資料中。                                            |
| metadata → external\_url                     | <p>NFT 詳細資料頁面中「瀏覽內容」按鍵的鏈接，位於 NFT 主圖片下方。</p><p>iscn.json 中的 url 字段優先。</p>                                                                                 |
| metadata → message                           | 附加到同一類別中每個 NFT 的「作者留言」。                                                                                                                                  |
| metadata → nft\_meta\_collection\_id         | NFT 類別，例如：nft\_book、nft\_mail、nft\_photo、nft\_illustration 等。Liker Land 使用此欄位來決定 NFT 顯示在哪個部分。                                                            |
| metadata → nft\_meta\_collection\_name       | NFT 類別名稱                                                                                                                                                 |
| metadata → nft\_meta\_collection\_descrption | NFT 類別描述                                                                                                                                                 |

#### **nfts\_default.json**

| 欄位                       | 內容                                                                                                                                                       |
| ------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| uri                      | <p>可選，預設值設定為空。<br></p><p>高級用法：API 生成圖片的 URI 並使用它作為 NFT 類別的 og 圖片，展示於 liker.land 的 NFT 展示櫃/儀表板及類別資訊中，如果 nfts.csv 與nfts_default.json 設定不正確，也將顯示於詳細資料中。</p> |
| metadata → name          | 預設的 NFT 名稱，如該欄位未在 nfts.csv 元資料中被指定。                                                                                                                      |
| metadata → description   | 預設的 NFT 描述，如該欄位未在 nfts.csv 元資料中被指定。                                                                                                                      |
| metadata → image         | 如果圖片內容在 nfts.csv 中不可用，圖片將首先由這個 URI 提供，其次由元資料 → 圖片欄位提供。                                                                                                   |
| metadata → external\_url | <p>NFT 詳細資料頁面中「瀏覽內容」按鍵的鏈接，位於 NFT 主圖下方。</p><p>iscn.json 中的 url 欄位優先。</p>                                                                                  |

#### nfts.csv

| 欄位       | 內容                                                                                                                                                       |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| nftId    | 特定 NFT class ID 下的獨有的 NFT ID。如果並未指定，系統將生成一個隨機 ID。 格式要求：https://docs.like.co/developer/likenft/likecoin-nft-module-spec#mintnft。                          |
| uri      | <p>可選，預設值設定為空。<br></p><p>高級用法：API 生成圖片的 URI 並使用它作為 NFT 類別的 og 圖片，展示於 liker.land 的 NFT 展示櫃/儀表板及類別資訊中，如果 nfts.csv 與nfts_default.json 設定不正確，也將顯示於詳細資料中。</p> |
| image    | 圖片的 URL 將作為 NFT 的 og 圖片並顯示於 liker.land NFT 詳細資料頁面                                                                                                        |
| metadata | NFT 圖片的元資料與任何相關參數並將被記錄於鏈上。                                                                                                                               |

#### 示範文檔

{% file src="../../.gitbook/assets/iscn.json" %}

{% file src="../../.gitbook/assets/nft_class.json" %}

{% file src="../../.gitbook/assets/nfts_default.json" %}

{% file src="../../.gitbook/assets/nfts.csv" %}

NFT 書的技術細節請參考以下指南：

{% embed url="https://docs.like.co/developer/likenft/nft-book-spec" %}

## 發行 NFT 書

### 方法一：使用 Mint LikeCoin NFT/NFT Book 發行 NFT 書

#### 步驟一：上載 iscn.json 並註冊 ISCN

請先登入你的 [Keplr](../wallet/keplr/)，並於 [LikeCoin NFT Book Press](https://likecoin-nft-book-press-testnet.netlify.app/) 選 [MINT NFT](https://likecoin-nft-book-press-testnet.netlify.app/mint-nft)，再點右上角「Connect」連接 Keplr。

在 Mint LikeCoin NFT/NFT Book 頁面選取已預備好的 iscn.json，點「Choose file」上載後點「Create」，Keplr 將彈出視窗。系統會跟據你預備的資料註冊 ISCN，請點「Approve」簽署並註冊。

<figure><img src="../../.gitbook/assets/Mint NFT Book 1.png" alt=""><figcaption><p>點「Choose file」上載 iscn.json 再點「Create」</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/Mint NFT Book 2.png" alt=""><figcaption><p>於 Keplr 點「Approve」簽署並註冊</p></figcaption></figure>

#### 步驟二：創建 NFT Class

成功註冊 ISCN 後根據它去創造一個 NFT Class。

除非希望限制發行上限，否則 Max number of supply for the NFT Class (optional) 不用填寫。

按著點「Choose file」上傳預先製作好的 nft\_class.json，再點「Create」並於 Keplr 點「Approve」簽署兩次成功生成 NFT Class。

<figure><img src="../../.gitbook/assets/Mint NFT Book 3.png" alt=""><figcaption><p>點「Choose file」上載 nft_class.json 再點「Create」</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/Mint NFT Book 4.png" alt=""><figcaption><p>於 Keplr 點「Approve」兩次生成 NFT Class</p></figcaption></figure>

#### 步驟三：正式發行 NFT

接下來需要上載兩個檔案，點「Choose file」分別上載 nfts\_default.json 及 nfts.csv。留意在 CSV 裡面會真正指定你準備發行多少枚 NFT，並且需要在 Number of NFT to mint 輸入相同的數量。然後再點「Create」並於 Keplr 點「Approve」簽署確認。

<figure><img src="../../.gitbook/assets/Mint NFT Book 5.png" alt=""><figcaption><p>點「Choose file」上載 nfts_default.json 及 nfts.csv，在 Number of NFT to mint 輸入發行數量，再於 Keplr 點「Approve」簽署確認</p></figcaption></figure>

#### 步驟四：成功發行

彈出視窗並儲存發行結果檔案，將檔案儲存後回到頁面出現 Success! 字樣即代表成功發行 NFT。點「View your NFT」在 Liker Land 查看已發行的 NFT 書。

<figure><img src="../../.gitbook/assets/Mint NFT Book 6.png" alt=""><figcaption><p>彈出視窗儲存發行結果檔案</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/Mint NFT Book 7.png" alt=""><figcaption><p>點「View your NFT」</p></figcaption></figure>

由於只完成發行但並未上架開放銷售，書籍數量會顯示為 Sold out。故此下一個步驟就是要把已發行的 NFT 書放上 Liker Land 售賣。

<figure><img src="../../.gitbook/assets/Mint NFT Book 9.png" alt=""><figcaption><p>在 Liker Land 查看已發行的 NFT 書</p></figcaption></figure>

### 方法二：安裝並使用鑄造語法發行 NFT（舊版）

鑄造語法是一個 node.js 語法。

#### 安裝語法

打開你的終端 ( terminal ) 並按照以下步驟操作：

1. 鍵入指令

`git clone` [`https://github.com/likecoin/iscn-nft-tools`](https://github.com/likecoin/iscn-nft-tools)`​`

2. 在 mint-nft 文件夾及 send-nft 文件夾中，執行指令

`npm install`

​Program path: iscn-nft-tools/mint-nft

Executable: index.js

#### 執行語法

&#x20;該語法將執行三個步驟：

1. 註冊 ISCN
2. 創建 NFT class
3. 鑄造 NFT

可以通過參數 --iscn-id 指定一個現存的 ISCN，通過參數 --class-id 指定一個現存的 NFT class ID。 你更可以讓語法從頭開始創建一切。

<table><thead><tr><th width="129">參數</th><th width="230">論元</th><th width="217">例字</th><th>是否強制</th></tr></thead><tbody><tr><td>nft-count</td><td>一個整數。要鑄造的 NFT 總數。</td><td>--nft-count 100</td><td>是</td></tr><tr><td>iscn-id</td><td>一個字符串。NFT 所指的 ISCN ID。</td><td>--iscn-id iscn://likecoin-chain/IKI9PueuJiOsYvhN6z9jPJIm3UGMh17BQ3tEwEzslQo/3</td><td>不是</td></tr><tr><td>create-new-iscn</td><td>空值。如果設定了此參數，將根照 iscn.json 文檔註冊一個新的 ISCN。不能和 iscn-id 參數一起使用。</td><td>--create-new-iscn</td><td>不是</td></tr><tr><td>class-id</td><td>一個字符串。NFT 所屬的 NFT class ID。 它用於在同一 Class ( collection ) 中鑄造額外的 NFT。 如果未設定，該語法將基於 nft-class.json 創建一個新的。</td><td>--class-id likenft1yhsps5l8tmeuy9y7k0rjpx97cl67cjkjnzkycecw5xrvjjp6c5yqz0ttmc</td><td>不是</td></tr><tr><td>nft-max-supply</td><td>一個整數。在一個 NFT class 中可以鑄造的 NFT 的最大數量。 如無特別說明則無限制。</td><td>--nft-max-supply 1000</td><td>不是</td></tr></tbody></table>

例子：

`IS_TESTNET=TRUE MNEMONIC="...." node index.js --nft-count 100 --create-new-iscn`

`IS_TESTNET=TRUE MNEMONIC="...." node index.js --nft-count 100 --iscn-id iscn://xxxx`

筆記：

* 必須指定 iscn-id 或 create-new-iscn 參數，但不能同時使用兩者。
* 如果已提供 create-new-iscn 參數，程序將引用 data/iscn.json 註冊一個新的 ISCN ID。
* 如果沒有提供 class-id 參數，程序會參考 data/nft\_class.json。
* class-id 和 nft-max-supply 不應該一起存在，因為 nft-max-supply 應該**只在**創建新的 nft class 時使用。
* nft-count 中指定的數字應與 data/nfts.csv 中的行數相匹配。

執行語法後，你應該已經成功鑄造了 NFT。恭喜！

## 上架 NFT 書

### 步驟一：上架 NFT 書

請先登入你的 [Keplr](../wallet/keplr/)，並於 [LikeCoin NFT Book Press](https://likecoin-nft-book-press-testnet.netlify.app/) 選 [Manage NFT Books](https://likecoin-nft-book-press-testnet.netlify.app/nft-book-store)，再點右上角「Connect」連接 Keplr。在 New NFT Book Listing 頁面輸入以下資料：

| 欄位                                         | 內容                                                |
| ------------------------------------------ | ------------------------------------------------- |
| NFT Class ID                               | 已發行的 NFT 書 Class ID                               |
| Price(USD) per NFT Book (Minimal $5)       | NFT 書的最低售價（不少於 5 美元）                              |
| Total number of NFT for sale at this price | 該售價的 NFT 書總銷售數量。例如將已發行 1,000 本 NFT 書中的 100 書作售賣之用 |
| Product name of this price                 | 該售價 NFT 書的產品名稱，支援中英文設定                            |
| Product description of this price          | 該售價 NFT 書的產品描述，支援中英文設定                            |

點「Add more prices」可以設定不同版本的 NFT 書售價及產品描述。

此外在 Share sales data to wallets (moderator) 可加入共同協作者的錢包以參看銷售數據；Email to receive sales notifications 除了作者以外，可設定其他收取銷售訊息的電郵地址。

填寫完成後點「Submit」。

<figure><img src="../../.gitbook/assets/List NFT Book 1.png" alt=""><figcaption><p>在 New NFT Book Listing 頁面輸入資料再點「Submit」</p></figcaption></figure>

### 步驟二：查看已上架的 NFT 書

成功上架後在 Current listing 出現已上架的 NFT 書，點 Class ID 可在 NFT Book Status 查看上架狀態。

<figure><img src="../../.gitbook/assets/List NFT Book 2.png" alt=""><figcaption><p>成功上架後在 Current listing 出現已上架的 NFT 書，點 Class ID 查看上架狀態</p></figcaption></figure>

回到 Liker Land 查看已發行的 NFT 書，會看到銷售數量由 Sold out 變成已上架開放銷售，並於版面顯示產品名稱、描述及售價等資訊。

<figure><img src="../../.gitbook/assets/List NFT Book 3.png" alt=""><figcaption><p>在 Liker Land 查看已發行的 NFT 書</p></figcaption></figure>

### 步驟三：透過不同渠道賣書

在 NFT Book Status 於 Copy Purhcase Link 選擇已上架 NFT 書產品，然後在 Sales channel for this link (Optional) 輸入銷售渠道的名稱，在下方將出現銷售連結的 Stripe 網址 URL。可將網址提供給銷售渠道宣傳吸引客戶買書，

<figure><img src="../../.gitbook/assets/List NFT Book 4.png" alt=""><figcaption><p>輸入銷售渠道的名稱出現銷售連結的 Stripe 網址 URL</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/List NFT Book 5.png" alt=""><figcaption><p>客戶使用連結購書</p></figcaption></figure>

### 步驟四：查看已售出的 NFT 書

客戶購買 NFT 書後，NFT Book Listing 中的 Current listing 將顯示 NFT 書的數量減少了。

<figure><img src="../../.gitbook/assets/List NFT Book 6.png" alt=""><figcaption><p>Current listing 顯示新的 NFT 書數量</p></figcaption></figure>

於 NFT Book Status 可查看該 NFT 書的銷售數據。在 Status 可看到 NFT 書的整體銷售狀態：Orders 出現已收到的 NFT 書訂單、顯示 pendingNFT 代表尚待發出予客戶、Sales channel 顯示從哪個銷售渠道賣出。

<figure><img src="../../.gitbook/assets/List NFT Book 7.png" alt=""><figcaption><p>於 NFT Book Status 可查看 NFT 書的銷售數據， 點「Send NFT」傳送 NFT 書予客戶</p></figcaption></figure>

### 步驟五：傳送 NFT 書予客戶

在 Action 點「Send NFT」出現 Deliver NFT Book 頁面。在 Enter Author's Message (optional) 輸入給讀者的話（可選填），在 Specify NFT ID 點「Auto-fetch NFT ID」自動抓取其中一份已發行的 NFT 書，再使用 Keplr 簽署並傳送給客戶。

<figure><img src="../../.gitbook/assets/List NFT Book 8.png" alt=""><figcaption><p>輸入給讀者的話，點「Auto-fetch NFT ID」自動抓取其中一份已發行的 NFT 書</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/List NFT Book 9.png" alt=""><figcaption><p>使用 Keplr 簽署並傳送給客戶</p></figcaption></figure>

傳送完成後，Action 的 Send NFT 變成了「View Transaction」並可查看已傳送予客戶的 NFT 書。

<figure><img src="../../.gitbook/assets/List NFT Book 10.png" alt=""><figcaption><p>點「View Transaction」查看已傳送予客戶的 NFT 書</p></figcaption></figure>

## 更新電子書文件或任何元資料的版本

你可能需要更新電子書文檔 (epub/pdf) 或任何元資料，例如，典型的情況是將註冊的 ISCN 包含到電子書文檔中，因此你將獲得新的內容指紋。以此例子，你需要：

1. 將 ISCN 內容添加到電子書文檔 (pdf/epub)。
2. 將電子書文檔上傳到 IPFS 並獲取新的哈希值 (contentFingerprint)。
3. 更新 ISCN 使用新的替換舊的 contentFingerprint。

你可以隨時追溯舊 ISCN 版本的資訊，但 Liker Land 前端將顯示最新的 ISCN 版本資訊。

查看用於更新 ISCN 的工具：

{% content-ref url="../decentralized-publishing/iscn-browser.md" %}
[iscn-browser.md](../decentralized-publishing/iscn-browser.md)
{% endcontent-ref %}

此外，可在此處找到[測試網上的 ISCN 瀏覽器工具](https://likecoin-iscn-browser-testnet.netlify.app/)。
