---
description: How to embed LikeCoin button into mdBook
---

# mdBook

Thanks user [道場除草機](https://dltdojo.github.io/taichu-crypto/dao/likecoin.html#likecoin) for the tutorial.

Before adding the LikeCoin button, please [register a Liker ID](https://docs.like.co/user-guide/liker-id/how-to-register-a-liker-id).

Use Javascript to create the following HTML in browsers and put it into static HTML created by mdBook.

```text
<div class="likecoin-embed likecoin-button">
  <div></div>
  <iframe scrolling="no" frameborder="0" 
    src="https://button.like.co/in/embed/LikerID/button?referrer=http://yourhost/foo/page.html">
  </iframe>
</div>
```

Add`likebutton.js` besides `book.toml` to custom made mdBook，you can also use `sdk.js` in [likecoin/likecoin-button-sdk](https://github.com/likecoin/likecoin-button-sdk), it works the same.

likebutton.js

```text
const LIKER_ID = "dltdojo";//Replace your own Liker ID
let likeurl = `https://button.like.co/in/embed/${LikerID}/button?referrer=${encodeURI(window.location.href)}`;
let el = document.getElementsByClassName("likebutton")[0];
if(el){
    el.innerHTML = `<div class="likecoin-embed likecoin-button">
  <div></div>
  <iframe scrolling="no" frameborder="0" src="${likeurl}"></iframe>
</div>`;
}
```

 並複製 [LikeCoinButton-integration/style.css](https://github.com/likecoin/LikeCoinButton-integration/blob/master/web/style.css) 成為 `likebutton.css`

```text
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

編輯 `book.toml` 的 `output.html` 段落加入 js 與 css

```text
[output.html]
default-theme = "coal"
mathjax-support = true
additional-js = ["likebutton.js"]
additional-css = ["likebutton.css"]
```

最後就是看那一頁 md 裡面要加上按鈕就新增一個 div 後用 class 為 likebutton 來綁住輸出。

```text
<div class="likebutton"/>
```

上面寫在 md 內的 div 在經過 mdbook build 轉化成為 HTML 後即能出現讚賞鍵。

目前只能限制一個 LikerID 使用，如要提供多用戶可以用 getElementsByClassName\(LikerIDFoo\) 來實做。

### 參考文章

> [如何在 mdbook 的文章中加入讚賞鍵 Likecoin Button](https://dltdojo.github.io/taichu-crypto/dao/likecoin.html#likecoin)

