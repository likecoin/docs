---
description: 刪除已發行的 NFT 電子書
---

# 銷毁 NFT 電子書

如想刪除已發行的 NFT 電子書，由於 NFT 電子書「印」了出來後便不能完全刪除，只能把它「丟」掉。故此暫時可行的方法是：

* 隨便開一個不主動對外公開的新錢包地址；
* 並將所有需要「丟棄」的 NFT 都發到這個新的「垃圾桶」地址
* 最後把 ISCN 的擁有權也轉移到新地址即可將書棄掉

## 步驟一：預備 CSV 檔案

由於鑄造 NFT 電子書時通常會鑄造多於一份 NFT，使用 [Liker Land](https://liker.land/) 發送 Writing NFT 功能每次只能發送一份 NFT 效率未免太低，建議使用 LikeCoin ISCN/NFT Tools 將已鑄造的 NFT 群發到那個作為「垃圾桶」、不主動對外公開的新錢包地址。要群發 NFT，請先預備一個 CSV 檔。範例可於這裡下載：

[https://github.com/likecoin/iscn-nft-tools/blob/master/send-nft/list\_example.csv](https://github.com/likecoin/iscn-nft-tools/blob/master/send-nft/list\_example.csv)

在 address 一欄輸入垃圾桶地址，在 classid 都填上要丟那本書的 NFT Class ID。假如你有 100 個 NFT 要丟，CSV 檔便要有 100 列這樣重覆的資料。

<figure><img src="../../../.gitbook/assets/Burn NFT Book 1.png" alt=""><figcaption><p>CSV 檔案範例</p></figcaption></figure>

## 步驟二：使用 LikeCoin NFT BookPress 群發 NFT 到垃圾桶地址

到 [LikeCoin NFT BookPress](https://likecoin.github.io/nft-book-press/) 網站點「LikeCoin ISCN/NFT Tools」。

<figure><img src="../../../.gitbook/assets/Burn NFT Book 2.png" alt=""><figcaption><p>點「LikeCoin ISCN/NFT Tools」</p></figcaption></figure>

到達 [LikeCoin ISCN/NFT Tools](https://likecoin.github.io/iscn-nft-tools/) 網站後點右上角「Connect」連結錢包，再點「Send NFT」。

<figure><img src="../../../.gitbook/assets/Burn NFT Book 3.png" alt=""><figcaption><p>點「Send NFT」</p></figcaption></figure>

點「Choose File」上載 CSV。在 Summary 能預覽 CSV 內容，確認無誤後點「Send」並於 Keplr 確認傳送 NFT。

<figure><img src="../../../.gitbook/assets/Burn NFT Book 4.png" alt=""><figcaption><p>點「Choose File」上載 CSV 再點「Send」</p></figcaption></figure>

完成後出現 Result 頁面，說明 NFT 經已完成傳送。

<figure><img src="../../../.gitbook/assets/Burn NFT Book 5.png" alt=""><figcaption><p>完成傳送 NFT</p></figcaption></figure>

## 步驟三：轉移 ISCN 擁有權到垃圾桶地址

最後，到 [ISCN Browser](https://likecoin.github.io/iscn-browser/) 工具網站點「Connect」連結錢包，並於 Search: 搜尋該 NFT 書的 ISCN。

<figure><img src="../../../.gitbook/assets/Burn NFT Book 6.png" alt=""><figcaption><p>點「Connect」連結錢包，並於 Search: 搜尋 NFT 書的 ISCN</p></figcaption></figure>

找到以後點「Transfer」。

<figure><img src="../../../.gitbook/assets/Burn NFT Book 7.png" alt=""><figcaption><p>點「Transfer」</p></figcaption></figure>

在 Transfer to 輸入垃圾桶地址，再點「Transfer」並於 Keplr 確認，即可將 ISCN 擁有權轉移給垃圾桶地址。

<figure><img src="../../../.gitbook/assets/Burn NFT Book 8.png" alt=""><figcaption><p>在 Transfer to 輸入垃圾桶地址再點「Transfer」</p></figcaption></figure>

完成以上步驟後，Liker Land 個人主頁便不會再出現已遭丟棄的那本書。
