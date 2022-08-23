---
description: 去中心交易所，無需註冊，立即交易
---

# 在 Osmosis 交易

{% hint style="warning" %}
提示：進行任何大額交易前請先作少量嘗試
{% endhint %}

2021年10月20日開始你可在 Osmosis 去中心交易所 ( DEX )，以 LikeCoin 交易包括美元穩定幣 USDC 在內的幾十種貨幣。過程無需註冊、不設入金出金門檻、用戶只需一個電子錢包即可操作，全程去中心化。

### 步驟一：接通 Osmosis

到 Osmosis 網址 [https://app.osmosis.zone/](https://app.osmosis.zone/)，點左下角「Connect Wallet」。

![](<../../.gitbook/assets/Osmosis 01.png>)

在 Connect Wallet 選「[Keplr Wallet](../wallet/keplr/)」。

![](<../../.gitbook/assets/Osmosis 02.png>)

左下角出現你的錢包名稱及經已擁有 OSMO 密碼貨幣的數量。你亦可以隨時點「Sign Out」退出 Osmosis。

![](<../../.gitbook/assets/Osmosis 03.png>)

### 步驟二：將 LikeCoin 存進 Osmosis

Osmosis 本身也是一條區塊鏈，它的鏈叫做 Osmosis blockchain，要在 Osmosis 交易 LikeCoin，要先在 Osmosis blockchain 存進資產。

到左手邊菜單選 Assets，找到 LikeCoin - LIKE 後，點「Deposit >」進行 IBC Deposit。

![](<../../.gitbook/assets/Osmosis 04.png>)

出現 Deposit IBC Asset 頁面，在「Amount To Deposit」輸入需要存進的 LikeCoin 數量，再點「Deposit」。留意請在 Keplr 錢包保留一點 LikeCoin 作[手續費](../wallet/transaction-fee.md)，否則將不能成功存進。

![](<../../.gitbook/assets/Osmosis 05.png>)

Keplr 彈出 IBC Transfer 畫面，點「Approve」。

![](<../../.gitbook/assets/Osmosis 06.png>)

Osmosis 彈出視窗，出現 IBC Transfer Successful 即代表成功存進 Osmosis。

![](<../../.gitbook/assets/Osmosis 07.png>)

### 步驟三：進行交易

點左手邊菜單選 Trade，在「From」下拉選單點 LIKE，並在「To」下拉選單選取需要交易的密碼貨幣。在下方可查看兌換率 Rate，及需要付出的互換交易費用 Swap Fee，以及預計的滑點 Estimate Slippage。查看無誤後點「Swap」進行交易。

![](<../../.gitbook/assets/Osmosis 08.png>)

Keplr 彈出交易畫面，點「Approve 」繼續。

![](<../../.gitbook/assets/Osmosis 09.png>)

換幣完成後，回到 Assets 可看到交易的密碼貨幣增加了。

### 步驟四：取回密碼貨幣

請將密碼貨幣先從 Assets 的「Withdraw >」使用 IBC Withdraw 提取回你的 Keplr 錢包後再傳送到交易所或其他錢包。

{% hint style="info" %}
使用 Osmosis 必需使用 Keplr 錢包登入。若你慣用 Liker Land 儲存 LikeCoin，可以：

* 將 LikeCoin 使用 [Liker Land app](../../user-guide/liker-land/download.md) 以 [LIKE pay](../wallet/like-pay.md) 轉帳到 Keplr 管理的地址
* 選擇 [匯出以一般方法 ( Authcore ) 註冊 Liker ID 的助記詞](../../user-guide/liker-id/export-seed-words.md)，並於 Keplr 管理你的 LikeCoin。
{% endhint %}
