---
description: LikeCoin v2.0.0 LaiChiKok Prefix 大升級後的變更
---

# 新地址前綴 (like) 常見問題

## 什麼是錢包地址前綴？

Cosmos 生態鼓勵一條區塊鏈專注一種應用，每條區塊鏈會以不同的前綴定義原生貨幣的地址，技術上需不是硬性規定，但約定俗成。例如 Cosmos Hub 的地址以 “cosmos” 開始，Osmosis 以 “osmo” 開始，Juno 以 “juno” 開始，等等。

## 為何 LikeCoin 沒有選用 “like” 作為地址前綴？

當 [LikeCoin](https://like.co/) 剛轉到 Cosmos 時，Cosmos 生態才剛剛起步發展，地址前綴取名的方法還未成為普遍共識。當時 LikeCoin 創始團隊選擇與 Cosmos 原生通證 ATOM 相同的 “cosmos” 作為 LikeCoin 的錢包地址前綴，但發展至兩年後的今天，理應跟隨 Cosmos 生態的共識轉成 like 前綴。

## 轉用 “like” 作地址前綴有什麼優點？

很多 Cosmos 生態的應用，包括 Dapps 或開放的技術接口，也會靠地前綴來辨認該地址是屬於哪條區塊鏈。Cosmos Hub 跟 LikeCoin 地址均是以 cosmos 字串開始，所以無法簡單地區分。這增加了LikeCoin 跟其他項目接軌的難度，例如錢包、交易所、區塊鏈瀏覽器等，均要額外的功夫才能整合 LikeCoin。

LikeCoin 地址從 cosmos 前綴（下稱「舊格式」）轉到 like 前綴（下稱「新格式」），將能加速 LikeCoin 跟其他 Cosmos 應用的整合，產生更多可能。

## 轉地址前綴，對現有用戶的實際影響是什麼？

* 新格式地址的 LikeCoin，在支援舊格式的 Dapps 上仍可以舊格式進行查閱、發送和接受等等操作
* 雖然新格式「向後兼容」會維持一段時間，但 LikeCoin 相關的應用會漸漸以支援新格式為主，舊格式將有一天被淘汰。
* 在某些 Dapp 上用戶或需手動設定才能用到新格式，例如 Keplr。

{% embed url="https://www.youtube.com/watch?v=0zAfhIAgj44" %}

{% embed url="https://www.youtube.com/watch?v=CPXY9A42zBo" %}

## 若不小心把 LikeCoin 傳送了到舊格式地址，怎麼辦？

舊格式跟新格式地址是 1 對 1 的，指向同一個錢包。因此，新舊地址中的 LikeCoin 也是同一筆資產，傳送到舊格式地址的 LikeCoin 也可在新地址查到。然而實際操作上，若 Dapp 在應用介面的向後支援功能不夠完善，便有可能導致某些功能無法正常運作。

但底線是：只要擁有產生地址的私鑰，仍能完全控制資產。

## 留意交易所是否支援新格式

轉帳 LikeCoin 到交易所，尤其是中心化交易所，請留意交易所方面是否已支援新格式。交易所有可能因為未完全支援新格式，導致存款及提款操作失敗。

由於存款到中心化交易所時，存款地址的私鑰是由交易所保管，所以用戶必須獲得交易所協助才能控制資產，請留意。

## 新/舊地址對應查閱工具

某些交易記錄可能仍是用舊地址。你隨時可在 LikeCoin Discord 的 [#translate-wallet-prefix](../community/translate-wallet-prefix.md) 頻道，以新/舊地址查閱對應的地址。例如在頻道中輸入 /translate cosmos1xxxxxx ，系統會返回對應的 like1xxxxxxx 新地址；相反若輸入 /translate like1xxxxxx，系統則會返回 cosmos1xxxxxx 格式的舊地址。

#### 更多詳情

[LikeCoin 新地址格式 – “like1” 的故事 ｜ LikeCoin 社群報](https://blog.like.co/zh/community-update-20220321-zh/)
