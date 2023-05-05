---
description: 升級 LikeCoin 的過程遇到阻滯，怎麼辦？
---

# 升級 LikeCoin 的常見問題

這篇集合了一些常見的問題及解決辦法，看看有沒有你需要的答案吧！

## **1. 我從沒安裝過 MetaMask，要怎樣升級？**

既然你沒有安裝過 MetaMask，即是你從沒用過自己的錢包儲存 LikeCoin， [Like.co/in](http://like.co/in) 網頁上顯示的 LikeCoin 數字只是系統幫你暫時寄存的。

你不用跑升級流程，只需用慣常的方法登入 [Liker Land 手機應用程式](../../../user-guide/liker-land/download.md)，待領的 LikeCoin 便會自動存入你的新錢包。

## **2. 升級過程中，MetaMask 及 like.co/in 網頁上顯示的 LikeCoin 數變成 0 了！**

由於系統會先從你的 MetaMask 轉帳 LikeCoin ERC-20 到智能合約，所以你的 LikeCoin 會有數分鐘時間在你的 MetaMask 錢包中消失，因為你的 LikeCoin 正在被傳送的途中呢。請耐心等候一會。

## **3. Like.co 網站上顯示的 LikeCoin 數跟 Liker Land 手機應用程式上的不乎**

很可能是你從來都沒有綁定以太坊錢包地址到你的 Liker ID，導致你所賺得的 LikeCoin 積存了在系統上還未派出。請你耐心等待幾天再查看。

## 4. 升級過程中不斷出現「Error: NOT\_ENOUGH\_GAS, NEED X.XXXXX」

你需要有足夠的 ETH ( NEED X.XXXXX 那個數值）作為碼工費 ( GAS Fee ) 方可完成升級，有關數值計算請參考 [ETH GAS Station](https://ethgasstation.info/)。&#x20;

## **5. 卡在「正在等待 ETH TX」很久**

系統會先從你的 MetaMask 轉帳 LikeCoin ERC-20 到智能合約，再把新 LikeCoin 存款到你的 LikeCoin chain 錢包。這兩個步驟涉及轉帳，一般需時最少 5-10 分鐘。請耐心等候。

若過了超過 15 分鐘仍未成功升級，有可能是後台出現問題，請聯絡客服。

## **6. 在簽署步驟遇上「無法偵測瀏器的 web3」錯誤**

![Error「無法偵測瀏器的 web3」](../../../.gitbook/assets/likecoin-migration-faq.png)

這個錯誤是指偵測不到 MetaMask 電子錢包。請檢查你是否在用 Chrome 瀏覽器，及 MetaMask Chrome extension 是否已安裝好。

## **7. 錯誤：「請用已綁定你的 Liker ID 的以太坊地址 \[0x...] 來簽署」**

你正在使用的 MetaMask 的當前電子錢包地址，跟你 Liker ID 綁定的地址不乎。請留意 MetaMask 只是一個電子錢包管理工具，可以管理多個地址。\
請仔細想想：

* 有沒有重新安裝過 MetaMask？
* 有沒有重灌過電腦？
* 你是否正在使用註冊 Liker ID 時所用的電腦？

建議你找回你註冊時的 MetaMask 電子錢包，再跑一次升級流程。

假若你懷疑自己遺失了電子錢包的地址，請查看你是否有備份助記詞 ( Seed Phrase ) 或私鑰。私鑰及助記詞是恢復電子錢包的唯一方法。若你不幸同時遺失了兩者，便像在街上掉了錢包一樣，永遠無法再操作錢包了。

## 8. 錯誤：「你的 MetaMask 錢包並未註冊任何 Liker ID，如需註冊新帳號，請返回使用 Authcore」

原因與 7. 相同。
