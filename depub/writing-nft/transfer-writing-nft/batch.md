---
description: 導出支持者錢包地址，再群發 NFT 給他們
---

# 群發 NFT 紀念品給支持者

### 教學影片

[導出支持者錢包地址，再群發 NFT 給他們 （廣東話）](https://www.youtube.com/watch?v=APw46UIzJLM)

### **詳盡介紹**

[以文會友的人情味和空間感 — 購買 Writing NFT 時，留言給作者](https://blog.like.co/zh/%E4%BB%A5%E6%96%87%E6%9C%83%E5%8F%8B%E7%9A%84%E4%BA%BA%E6%83%85%E5%91%B3%E5%92%8C%E7%A9%BA%E9%96%93%E6%84%9F-%E8%B3%BC%E8%B2%B7-writing-nft-%E6%99%82%EF%BC%8C%E7%95%99%E8%A8%80%E7%B5%A6/)

### 操作步驟

**步驟一**：在 [LikeCoin NFT Dashboard](https://likecoin.github.io/likecoin-nft-dashboard/#/) 搜尋（Search）自己錢包的收藏者 ( Get Collector )。

**步驟二**：導出所有數據 ( Export all data )。

**步驟三**：將數據的 csv 導入試算表工具進行分類與排序，並將支持者錢包地址整理成清單。之後用戶可選擇同種不同方式去群發 NFT：

#### 方法一

* 在 [LikeCoin NFT Marketplace](https://likecoin.github.io/likecoin-nft-marketplace/) 的介面工具 ( Tools ) 中選 [Send NFTs](https://likecoin.github.io/likecoin-nft-marketplace/tools/send) 並登入 Keplr。
* 在用以群發給支持者的 Writing NFT 找出 [NFT Class ID](../collect-writing-nft/nft-details.md#nft-class-id)。
* 將 NFT Class ID 輸入 Send NFTs 工具，並輸入支持者的錢包地址清單 ( Recepient Address list ) 及留給他們的話 ( Transfer message ) ，再點「Send」及在 Keplr 簽署，即可群發 NFT。

#### 方法二

* 在 [LikeCoin ISCN/NFT Tools](https://likecoin.github.io/iscn-nft-tools/) 選 [Send NFT](https://likecoin.github.io/iscn-nft-tools/send-nft) 並登入 Keplr。
* 預備 csv 檔案（見[範例](https://github.com/likecoin/iscn-nft-tools/blob/master/send-nft/list\_example.csv)），內裡包括錢包地址 ( address )，送出 NFT 的 [classid](../collect-writing-nft/nft-details.md#nft-class-id) 及 memo，亦即是[附加留言](batch.md#bu-zhou-er-shu-ru-qian-bao-di-zhi-ji-fu-jia-liu-yan)，再點「Send」及在 Keplr 簽署，即可群發 NFT。
