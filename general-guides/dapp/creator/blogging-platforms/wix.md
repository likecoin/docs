---
description: 如何在 Wix 文章中加入 LikeCoin button
---

# Wix / Weebly

安裝讚賞鍵以前，請先 [註冊 Liker ID](../../liker-id/)。

依照以下格式製作你的讚賞鍵鏈結：

```
https://button.like.co/in/embed/[LikerID]/button?referrer=[網頁URL]
```

假設你的 Liker ID 是 ckxpress，網頁 URL 是 https://ckxpress.wixsite.com/likecoin/single-post/2020/02/22/LikeCoin

讚賞鍵的鏈結便是 https://button.like.co/in/embed/ckxpress/button?referrer=https://ckxpress.wixsite.com/likecoin/single-post/2020/02/22/LikeCoin

接著開啟 HTML 編輯模式，將以下程式碼加到你需要顯示讚賞鍵的地方，留意要把 `{{ src }}` 的部份替換為讚賞鍵鏈結

```
<div class="likecoin-embed likecoin-button">
  <div></div>
  <iframe scrolling="no" frameborder="0" src="{{ src }}"></iframe>
</div>
```

亦即是這樣

```
<div class="likecoin-embed likecoin-button">
  <div></div>
  <iframe scrolling="no" frameborder="0" src="https://button.like.co/in/embed/ckxpress/button?referrer=https://ckxpress.wixsite.com/likecoin/single-post/2020/02/22/LikeCoin"></iframe>
</div>
```

儲存後，讚賞鍵便會出現在文章中。然而你需要使用 Wix 的進階功能加入 CSS，讓它顯示的模樣更為清淅

```
.likecoin-button {
  position: relative;
  width: 100%;
  max-width: 485px;
  max-height: 240px;
  margin: 0 auto;
}
.likecoin-button > div {
  padding-top: 49.48454%;
}
.likecoin-button > iframe {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}
```

### 參考文章

> [likecoin / LikeCoinButton-integration iframe](https://github.com/likecoin/LikeCoinButton-integration/tree/master/web#2iframe)

\-------------------------

Weebly 用戶也可使用同樣方式插入讚賞鍵。

\-------------------------

也可以嘗試使用 JavaScript 的方式看看能否產生讚賞鍵，詳見：

{% content-ref url="blogspot.md" %}
[blogspot.md](blogspot.md)
{% endcontent-ref %}
