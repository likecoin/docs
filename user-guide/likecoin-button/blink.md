---
description: 如何在 Blink 佈告欄文章中加入讚賞鍵
---

# Blink

安裝讚賞鍵以前，請先 [註冊 Liker ID](https://docs.like.co/v/zh/user-guide/liker-id/how-to-register-a-liker-id)。

依照以下格式製作你的讚賞鍵連結：

```text
https://button.like.co/in/embed/[LikerID]/button?referrer=[網頁URL]
```

假設你的 ID 是 ckxpress，網頁 URL 是 https://blink.com.tw/board/post/83713/

讚賞鍵的鏈結便是 https://button.like.co/in/embed/ckxpress/button?referrer=https://blink.com.tw/board/post/83713/

接著按「插件式/可編輯」影音，再選擇「嵌入」，將以下程式碼加到你需要顯示讚賞鍵的地方，留意要把 **{{ src }}** 的部份替換為讚賞鍵鏈結

```text
<div class="likecoin-embed likecoin-button">
  <div></div>
  <iframe scrolling="no" frameborder="0" src="{{ src }}"></iframe>
</div>
```

亦即是這樣

```text
<div class="likecoin-embed likecoin-button">
  <div></div>
  <iframe scrolling="no" frameborder="0" src="https://button.like.co/in/embed/ckxpress/button?referrer=https://button.like.co/in/embed/ckxpress/button?referrer=https://blink.com.tw/board/post/83713/"></iframe>
</div>
```

再按「OK」，讚賞鍵便會出現在文章中

![](../../.gitbook/assets/wei-ming-ming%20%281%29.png)

你可以按「一般的」，再更改「空間維度」調整讚賞鍵顯示大小。

![](../../.gitbook/assets/wei-ming-ming.png)



