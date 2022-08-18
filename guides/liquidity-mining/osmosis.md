---
description: 如何在 Osmosis 獲得流動性挖礦獎勵
---

# Osmosis

現時 LikeCoin 在 Osmosis 有兩個流動性池 ，提供流動性就能獲得互換交易費 ( Swap Fee ) 及流動性挖礦獎勵 ( Liquidity Mining Incentives )。

注意流動性挖礦有機會讓用戶遭遇無常損失 ( Impermanent Loss )，請自行評估相關風險。

進行流動性挖礦方法很簡單，首先你需要先註冊 Keplr 錢包

{% content-ref url="../../user-guide/liker-id/register-with-keplr.md" %}
[register-with-keplr.md](../../user-guide/liker-id/register-with-keplr.md)
{% endcontent-ref %}

及將 LikeCoin 轉帳到錢包內。

{% content-ref url="../wallet/keplr.md" %}
[keplr.md](../wallet/keplr.md)
{% endcontent-ref %}

## 為流動性池提供流動性

### 步驟一：選定流動性池

現時 LikeCoin 在 [Osmosis](https://app.osmosis.zone/) 中設置了兩個流動性池：

[Pool #553 LIKE/OSMO](https://app.osmosis.zone/pool/553)

[Pool #555 LIKE/ATOM](https://app.osmosis.zone/pool/555)

在 Osmosis 點左手邊菜單 Pools，再搜尋「LIKE」。以下使用 Pool #553 LIKE/OSMO 作例子。

### 步驟二：預備密碼貨幣

每一個流動性池都有自己的比例，Pool #553 LIKE/OSMO 的比例是 50% / 50%，換而言之你需要預備 50% LIKE 配對 50% OSMO。

![](<../../.gitbook/assets/Osmosis LP 01.png>)

可點左手邊菜單 Trade 進行交易以獲得 LIKE 或 OSMO。

{% content-ref url="../trade/trade-in-osmosis.md" %}
[trade-in-osmosis.md](../trade/trade-in-osmosis.md)
{% endcontent-ref %}

### 步驟三：為流動性池添加流動性

左上角顯示：

* Pool Liquidity 整個池的流動性總值
* My Liquidity 自己在這個池擁有的流動性總值
* Bonded 已綁定的流動性總值
* Swap Fee 互換交易費，當別的用戶使用這個池提供的流動性進行交易時所需要付出的費用
* Exit Fee 出池費，離開這池需要付出的費用

點「Add / Remove Liquidity」。

![](<../../.gitbook/assets/Osmosis LP 02.png>)

出現 Manage Liquidity 畫面，填寫放置進流動性池的 LIKE 數量，OSMO 數量會自動依比例填入，再點「Add Liquidity」添加流動性，Keplr 錢包將彈出確認視窗，點「Approve」即可。接下的數項操作亦將需要 Keplr 確認操作，到時均可一拼點「Approve」。

![](<../../.gitbook/assets/Osmosis LP 03.png>)

假如希望獲得更多貨幣去添加流動性，可隨時點「Swap Tokens」進行交易。

提供流動性可獲得互換交易費 ( Swap Fee )。

## 綁定 LP Token 獲得流動性挖礦獎勵

添加流動性後，會依照整個池的流動性對應你提供流動性的份額比例獲得 LP Token，綁定這些 LP Token 可獲流動性挖礦獎勵。

### 步驟一：開始綁定

在右手邊的 Available LP tokens 顯示已獲得的 LP Token 數量。然後點「Start Earning」。

![](<../../.gitbook/assets/Osmosis LP 04.png>)

### 步驟二：綁定不同天數

出現 Bond LP tokens 畫面並出現三個流動性計量器，分別為 1 天、7 天 及 14 天，並設有不同的 APR 即年利率，綁定天數越長 APR 越高。你可以選擇一次過綁定所有 LP Token 到 14 天，也可以選擇將不同數量的 LP Token 綁定不同天數。輸入需要綁定的 LP Token 數量，再點「Bond」。

![](<../../.gitbook/assets/Osmosis LP 05.png>)

完成綁定後於 My Bondings 查看經已綁定的 LP Token 數量。

![](<../../.gitbook/assets/Osmosis LP 06.png>)

左上角 Bonded 亦顯示經已綁定的流動性總值經已增加。

![](<../../.gitbook/assets/Osmosis LP 09.png>)

### 步驟三：獎勵派發

Osmosis 的流動性挖礦獎勵將以 OSMO 回饋予流動性挖礦者，並於每天紀元 ( Daily Epoch ) 17:00 UTC 直接發送到 Keplr 錢包。

## 解綁 LP Token 取回密碼貨幣

### 步驟一：解除 LP Token 綁定

回到 My Bondings，在需要解綁的流動性計量器選「Unbond all」。

![](<../../.gitbook/assets/Osmosis LP 07.png>)

留意解綁所需時間為你選定的流動性計量器的時間，例如選 14 天就需要 14 天才能完成解綁，7 天就需要 7 天才能完成解綁。解綁期間，你仍然可以收取流動性挖礦獎勵，直至解綁完成為止。

### 步驟二：取回密碼貨幣

點「Add / Remove Liquidity」，在 Manage Liquidity 將畫面切換到 Remove Liquidity 選擇取回 100% 即全部、75%、50% 或 25%，即可將密碼貨幣取回。取回貨幣需要支付出池費，並可依照你提供的流動性份額比例一拼取回互換交易費。

![](<../../.gitbook/assets/Osmosis LP 08.png>)

取回的密碼貨幣可於左手邊菜單選 Assets 查看，

## 查看以往數據

點左手邊菜單 Info 或到 [https://info.osmosis.zone/](https://info.osmosis.zone/) 可以查看各個流動性池的數據。
