---
description: 如何在 Emeris 提供流動性
---

# Emeris

現時 LikeCoin 在 Emeris 有一個 ATOM-LIKE 流動性池，提供流動性 ( Liquidity Providing ) 就能獲得互換交易費 ( Swap Fee ) 。

注意提供流動性有機會讓用戶遭遇無常損失 ( Impermanent Loss )，請自行評估相關風險。

提供流動性方法很簡單，首先你需要先註冊 Keplr 錢包

{% content-ref url="../../../user-guide/liker-id/register-with-keplr.md" %}
[register-with-keplr.md](../../../user-guide/liker-id/register-with-keplr.md)
{% endcontent-ref %}

及將 LikeCoin 傳送到錢包內。

{% content-ref url="../../../guides/wallet/keplr.md" %}
[keplr.md](../../../guides/wallet/keplr.md)
{% endcontent-ref %}

## 為流動性池提供流動性

### 步驟一：接通 Emeris

到 Emeris 網址 [https://app.emeris.com/](https://app.emeris.com/)，點右上角「Connect wallet」。

![](<../../../.gitbook/assets/Emeris LP 01.png>)

出現 Connect your wallet 畫面，點「Connect Keplr」。

![](<../../../.gitbook/assets/Emeris LP 02.png>)

### 步驟二：選擇流動性池

登入後點「Pools」。

![](<../../../.gitbook/assets/Emeris LP 03.png>)

再選 ATOM-LIKE 流動性池。

![](<../../../.gitbook/assets/Emeris LP 04.png>)

### 步驟三：添加流動性

在 ATOM-LIKE 流動性池畫面，點右手邊「Add liquidity」。

![](<../../../.gitbook/assets/Emeris LP 05.png>)

ATOM-LIKE 流動性池的比率為 50%/50%，填入 ATOM 數字，LIKE 數字自動填上，反之亦然。你亦可以查看 Receive LP asset 亦即是在此池中預計可獲得的流動性份額及 Fees (included) 手續費。確認無誤後點「Continue」。

![](<../../../.gitbook/assets/Emeris LP 06.png>)

### 步驟四：將 LIKE 帶進 Cosmos Hub 網絡

Emeris 的操作位於 Cosmos Hub 鏈上，所以你需要把 LikeCoin 帶進 Cosmos Hub 網絡。在 Pools are on the Cosmos Hub 畫面點「Continue」。

![](<../../../.gitbook/assets/Emeris LP 07.png>)

以下畫面顯示 LIKE 由 LikeCoin chain 傳送到 Cosmos Hub，Transaction Fee 手續費。確認無誤後點「Confirm and continue」。

![](<../../../.gitbook/assets/Emeris LP 08.png>)

Keplr 彈出交易畫面，點「Approve 」繼續。

![](<../../../.gitbook/assets/Emeris LP 09.png>)

出現 Transferring 傳送中動畫。

![](<../../../.gitbook/assets/Emeris LP 10.png>)

出現 Transferred 畫面代表完成傳送。你可以點「View on explorer」查看傳送內容，然後點「Continue」。

![](<../../../.gitbook/assets/Emeris LP 11.png>)

### 步驟五：確認添加流動性

Review your pool liquidity provision 畫面顯示提供流動性的幣、Receive (estimated) 亦即是在此池中預計可獲得的流動性份額及 Transaction fee 手續費。確認無誤後點「Confirm and continue」。

![Keplr 彈出交易畫面，點「Approve 」繼續。](<../../../.gitbook/assets/Emeris LP 12.png>)

Keplr 彈出交易畫面，點「Approve 」繼續。

![](<../../../.gitbook/assets/Emeris LP 13.png>)

出現 Adding liquidity 動畫。

![](<../../../.gitbook/assets/Emeris LP 14.png>)

流動性已成功添加並顯示交易明細，你可以點「View on explorer」到 Mintscan 查看相關內容。

![](<../../../.gitbook/assets/Emeris LP 15.png>)

點「Done」開閉畫面後回到 ATOM-LIKE 流動性池，在 Equity 可看到經已提供的流動性。 點「Add」可增加更多流動性，點「Withdraw」可取回流動性。

![](<../../../.gitbook/assets/Emeris LP 16.png>)

{% hint style="info" %}
Emeris 現時處於 Beta 階段，並未提供流動性挖礦獎勵。
{% endhint %}
