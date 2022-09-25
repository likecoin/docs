---
description: 如何一次過為大量資料註冊 ISCN，含少量技術程序
---

# 如何大量註冊 ISCN

大量資料註冊 ISCN
-----------

### 事前準備

1. 可以處理 CSV 檔案的工具，推薦免費的 Google spreadsheet。將要註冊的資料以 CSV 格式整理好。
2. 可執行 Linux command 的電腦。電腦需已安裝 node.js 及 git 的最新版本。下文將以 Mac 為例。
3. 一個已有少量 LikeCoin 的錢包。[錢包需以 Keplr 註冊](../wallet/keplr/)，因為必須用到這錢包的助記詞  ( seed words )。

### 步驟一：資料整理

以註冊《唐詩三百首》為例。按 ISCN 格式要求，上傳的資料欄位應盡量按 schema.org 中的 [CreativeWork](https://schema.org/CreativeWork) 類別定義，所以第一步先要把 [CSV 檔](https://github.com/edmondyu/TangPoems300/blob/main/TangPoems300.csv)的欄位名稱定好。

![](<../../.gitbook/assets/iscn-batch-uploader 01.png>)

轉換後的定義為 （原欄名 > CreativeWork 欄名）：

* ID > identifier
* 作者 > author
* 標題 > name
* 體裁 > genre
* 詩文 > text
* 網址 > url
* 授權方式 > usageinfo

留意以下三個欄位不在 CreativeWork 定義中，而是上傳 ISCN 的 script 工具 [iscn-batch-uploader](https://github.com/likecoin/iscn-batch-uploader) 所需要的：

* ipfsHash: iscn-batch-uploader 會把這欄位中的 hash 填在 ISCN 的「內容指紋」欄 ( content fingerprint )
* type: 這是 schema.org 中的類別，type 可以是 CreativeWork, Book, Game, Painting, Article, Photograph, Episode 等等。若 CSV 內沒有這欄，默認便會填上 CreativeWork

像《唐詩三百首》這種較短的內容，把內文全部以 text 欄位寫進 LikeCoin chain 成本也不高；但為了演示實際用途還是把每篇唐詩都另儲成一個 txt 檔案，批量上傳到 pinata 這 IPFS pinning service 平台，再把回傳的 hash 填在每筆唐詩的對應記錄中。這樣註冊的 ISCN 便會有「內容指紋」資料。又，iscn-batch-uploader 目前暫未支援 Arweave 連結的欄位。

而上傳資料到 IPFS，再獲得 ipfsHash 作內容指紋這工序暫時亦未能批量處理。遺憾地 iscn-batch-uploader 並未能解決這問題。若不懂寫代碼，便恐怕要逐個逐個檔案上傳再抄下 hash，這痛苦的手動程序絕對不適合用作處理大量資料。非技術朋友建議別急著處理內容指紋這欄位，先把內容元資料 ( metadata ) 註冊並拿到 ISCN 編號，因為 _iscn-batch-uploader 工具支援**更新**現有 ISCN 記錄_。日後待資料齊全了，再一口氣把內容指紋更新上區塊鏈不遲。

若是懂技術的朋友，可嘗試使用[整合 pinata 的 python 小工具](https://github.com/edmondyu/pinata-python-util)。歡迎隨便使用，或提交修改建議。

《唐詩三百首》只有 300 多筆記錄，然而就算處理上百萬條記錄，也可用完全相同的方法。把整本《聖經》、莎翁的劇本、自己的所有文章、某些歌曲的樂譜、某份報紙的備份、機構的會議記錄等，也用如此方式批量註冊到區塊鏈。整理資料的工序絕對是非技術人能發揮的巨大舞台。

### 步驟二：安裝 iscn-batch-uploader

```
git clone https://github.com/likecoin/iscn-batch-uploader.git
```

電腦已安裝 git，只需建個文件夾再輸入上面那個指令，便能把 iscn-batch-uploader 文件夾下載了。沒有安裝 git 的話可以[直接從 GitHub 下載 zip 檔](https://github.com/likecoin/iscn-batch-uploader)。（點右上 "Code" 綠色按鍵），解壓獲得 iscn-batch-uploader 文件夾。

![](<../../.gitbook/assets/iscn-batch-uploader 02.png>)

打開 terminal 終端，cd 到 iscn-batch-uploader 文件夾，然後輸入以下指令：

```
npm install
```

這指令會令程式庫就緒。

### 步驟三：修改設定

成功下載後，在 iscn-batch-uploader 文件夾中有個 config 文件夾，裡面有個 config.js 文件。用任何文字編輯器打開它，在 config.COSMOS\_MNEMONIC 那一列填上你 LikeCoin 錢包的助記詞，例如：

config.COSMOS\_MNEMONIC = 'paint man cloud google winnie pool think hell imposition police illegal tyranny';

### 步驟四：複製 CSV 檔到執行目錄

把《唐詩三百首》的 CSV 檔，或任何你想註冊 ISCN 的 CSV 資料檔 copy 到 iscn-batch-uploader 文件夾中去。

![](<../../.gitbook/assets/iscn-batch-uploader 03.png>)

### 步驟五：執行程式

一切就緒了。在 Terminal 終端，確認 iscn-batch-uploader 是當前文件夾，然後輸入以下指令：

```
node index.js [your csv filename] 
```

\[your csv file name] 是你的資料檔名，以《唐詩三百首》範例資料檔為例，指令就是

```
node index.js TangPoems300.csv
```

![](<../../.gitbook/assets/iscn-batch-uploader 04.gif>)

你沒有看錯，註冊三百多筆 ISCN，也不用花 1 LIKE！趁還沒加價快試試看吧。

### 步驟六：檢查結果

程式成功執行後，在 iscn-batch-uploader 文件夾會多了一個 "output.csv" 檔案，跟原資料檔案比較增加了兩個欄位： txHash 及 iscnId。

txHash 是 LikeCoin chain 上的交易記錄編號，你可在 Big Dipper 或 stake.like.co 等區塊瀏覽器中查找這串編碼以檢視該筆記錄，例如你可在 Big Dipper 中輸入這個 TX hash: C75B2BD9C79A83670C49F97522E7670CBB7E4892CAC26D5F09E5913C57870E5C

打開 "Raw" 選項，可看到詳細的 ISCN 註冊資料記錄。

另外，iscnId 則是這筆內容的 ISCN 編號，你可在 app.like.co 查詢這編號，例如輸入 iscn://likecoin-chain/9MewrmZqHT55nJLtW7EGqo8szOwKtp42AmhKyhWrImw/1 能查到李白的《將進酒》：

![李白《將進酒》 ISCN ID iscn://likecoin-chain/9MewrmZqHT55nJLtW7EGqo8szOwKtp42AmhKyhWrImw](<../../.gitbook/assets/iscn-batch-uploader 05.png>)

你也可以剛才用作批量註冊的那 LikeCoin 錢包登入 app.like.co，點 "Your Publishing" 能查到經 iscn-batch-uploader 註冊的內容，可是目前只能查到首 100 筆記錄。

![](<../../.gitbook/assets/iscn-batch-uploader 06.png>)

## 進階用法：內容版本更新

iscn-batch-uploader 工具支援內容版本更新，用法是：

* 在 CSV 中把內容改動整理好，留意要完整地填滿所有欄位的內容，就算欄位內容沒有改動也要照填上。
* 再跑 index.js 一次，但加上 --update 參數，例如：

```
node index.js TangPoems300A.csv --update
```

這樣當程序讀到已存在的 ISCN 記錄時，會更新區塊鏈上同一筆 ISCN 記錄而不是註冊一筆新的。新版本號會在 ISCN ID 最尾的字段反映，例如 /1 代表 version 1，/2 代表 version 2。若在 app.like.co 輸入 ISCN ID 查詢時忽略最後的版本號，系統會默認回傳最新版本。

## 問題：註冊失敗怎麼辦？

跑 iscn-batch-uploader 時偶爾會因不明原因，在註冊某筆記錄時回傳失敗。這時程式會嘗試稍候再重新註冊，若仍然失敗便會跳過當前那筆記錄，註冊下一筆。你可以檢查 output.csv 看看是否所有記錄都有 iscnId，確認有沒有漏掉註冊。

若真的有漏了，最便捷的方法是直接把 output.csv 改個檔名，然後用作 input file 參數重新跑一遍 index.js，例如：

```
node index.js fromOutputFile.csv
```

若沒加上 --update 參數，程式會自動跳過已有 iscnId 的記錄，只執行漏掉註冊的記錄。

{% hint style="info" %}
若希望先作測試才進行大量註冊，可使用 [LikeCoin Chain testnet](https://github.com/likecoin/testnets/tree/master/likecoin-public-testnet-3) 進行測試。
{% endhint %}
