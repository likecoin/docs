---
description: 如何在 Osmosis 獲得流動性挖礦獎勵
---

# Osmosis

現時 [LikeCoin](https://like.co/) 在 [Osmosis](https://osmosis.zone/) 有兩個流動性池 ，提供流動性就能獲得互換交易費 ( Swap Fee ) 及流動性挖礦獎勵 ( Liquidity Mining Incentives )。

注意流動性挖礦有機會讓用戶遭遇無常損失 ( Impermanent Loss )，請自行評估相關風險。

進行流動性挖礦方法很簡單，首先你需要於桌面電腦操作並先註冊 [Keplr](../wallet/keplr/)、[Leap](../wallet/leap/)、[Cosmostation](../wallet/cosmostation/) 或 [Keplr Mobile](../wallet/keplr-mobile/) 及將 LikeCoin 轉帳到錢包內。

{% content-ref url="../wallet/like-pay.md" %}
[like-pay.md](../wallet/like-pay.md)
{% endcontent-ref %}

## 為流動性池提供流動性 <a href="#providing-liquidity" id="providing-liquidity"></a>

### 步驟一：選定流動性池

現時 LikeCoin 在 [Osmosis](https://app.osmosis.zone/) 中設置了兩個流動性池：

[Pool #553 LIKE/OSMO](https://app.osmosis.zone/pool/553)

[Pool #555 LIKE/ATOM](https://app.osmosis.zone/pool/555)

你亦可以在 Osmosis 點左手邊菜單 Pools，再搜尋「LIKE」找到這兩個流動性池。

以下使用 Pool #553 LIKE/OSMO 作例子。

### 步驟二：預備密碼貨幣

每一個流動性池都有自己的比例，點「Show pool composition」查看 Pool #553 LIKE/OSMO 的比例是 50% / 50%，換而言之你需要預備 50% LIKE 配對 50% OSMO。與此同時亦可查看以下資訊：

* 24h Trading volume：過去 24 小時交易量
* Pool Liquidity：整個池的流動性總值
* Swap Fee：幣幣互換交易費，當別的用戶使用這個池提供的流動性進行交易時所需要付出的費用

<figure><img src="../../.gitbook/assets/Osmosis LP 1.png" alt=""><figcaption><p>查看流動性池資訊</p></figcaption></figure>

可點左手邊菜單 Swap 進行交易以獲得 LIKE 或 OSMO，或參考以下內容購買 LikeCoin：

{% content-ref url="../trade/trade-in-osmosis.md" %}
[trade-in-osmosis.md](../trade/trade-in-osmosis.md)
{% endcontent-ref %}

### 步驟三：為流動性池添加流動性

預備好 LIKE 及 OSMO 後，Level 1 為這個池提供流動性可獲得互換交易費 ( Earn swap fees )。點「Add Liquidity」。

<figure><img src="../../.gitbook/assets/Osmosis LP 2.png" alt=""><figcaption><p>點「Add Liquidity」</p></figcaption></figure>

出現 Add Liquidity 畫面，填寫放置進流動性池的 LIKE 數量，OSMO 數量會自動依比例填入，再點「Add Liquidity」添加流動性，Keplr 錢包將彈出確認視窗，點「Approve」即可。接下的數項操作亦將需要 Keplr 確認操作，到時均可一律點「Approve」。

使用 Leap、Cosmostation、Keplr Mobile 亦會彈出相應確認畫面。

<figure><img src="../../.gitbook/assets/Osmosis LP 3.png" alt=""><figcaption><p>輸入 LIKE 及 OSMO 數量再點「Add Liquidity」</p></figcaption></figure>

假如希望獲得更多 LIKE 和 OSMO 添加流動性，可隨時點「Trade Pair」進行交易。

## 綁定 shares 獲得流動性挖礦獎勵 <a href="#yield-farming" id="yield-farming"></a>

添加流動性後，會依照整個池的流動性對應你提供流動性的份額比例獲得份額（ shares，有人會稱之為 LP Token），綁定這些 shares 可獲流動性挖礦獎勵。

### 步驟一：開始綁定

查看已擁有的 shares 數量及大概價值，了解後可進入 Level 2 綁定流動性 ( Bond liquidity )，點「Bond Shares」。

<figure><img src="../../.gitbook/assets/Osmosis LP 4.png" alt=""><figcaption><p>點「Bond Shares」</p></figcaption></figure>

### 步驟二：綁定 shares

彈出視窗顯示年利率 ( APR, Annual Percentage Rate ) 並必須綁定 14 天（14 days）方可獲得流動性挖礦獎勵。在 Amount to bond 輸入需要綁定的 shares 數量再點「Bond」。

<figure><img src="../../.gitbook/assets/Osmosis LP 5.png" alt=""><figcaption><p>輸入需要綁定的 shares 數量再點「Bond」</p></figcaption></figure>

完成後顯示 shares 需要 14 天去解綁 ( 14 days unbonding )、已綁定的 shares 數量，及 APR 等。

<figure><img src="../../.gitbook/assets/Osmosis LP 6.png" alt=""><figcaption><p>完成後顯示已綁定 shares 資訊</p></figcaption></figure>

### 步驟三：獎勵派發

回到頂部的資訊欄會發現多了一些內容，它們分別為：

* Your Pool Balance：流動性池所綁定的 LIKE 及 OSMO 數量及它們於池中所的 share 為何&#x20;
* Bonded：已綁定的流動性總值
* My Liquidity：自己在這個池擁有的流動性總值
* You're currently earning：你每天正在賺了多少

<figure><img src="../../.gitbook/assets/Osmosis LP 7.png" alt=""><figcaption><p>顯示獎勵派發情況</p></figcaption></figure>

Osmosis 的流動性挖礦獎勵將以 OSMO 回饋予流動性挖礦者，並於每天紀元 ( Daily Epoch ) 17:00 UTC 直接發送到 Keplr 錢包。

## 解綁 shares 取回密碼貨幣

### 步驟一：解除 shares 綁定

回到 Bond liquidity 點「Unbond」。

<figure><img src="../../.gitbook/assets/Osmosis LP 8.png" alt=""><figcaption><p>點「Unbond」解除 shares 綁定</p></figcaption></figure>

留意解綁需時 14 天。解綁期間，你仍然可以收取流動性挖礦獎勵，直至解綁完成為止。

### 步驟二：取回密碼貨幣

解綁完成後回到 Level 1 點「Remove Liquidity」即可取回密碼貨幣。可於左手邊菜單選 Assets 查看已取回的  LIKE 及 OSMO。

## 查看以往數據

點左手邊菜單 Info 或到 [https://info.osmosis.zone/](https://info.osmosis.zone/) 可以查看各個流動性池的數據。

{% hint style="info" %}
用戶也可以使用 Keplr Mobile 內的 Osmosis App 管理流動性。
{% endhint %}
