---
description: 如何在 ghost 文章中加入 LikeCoin button
---

# ghost

感謝用戶 [STANLEY TSAU](https://stanleytsau.me/author/daydream/) 的教學範本，留意 [ghost 是需要付費加入會員](https://ghost.org/pricing/)方可使用。

安裝讚賞鍵以前，請先 [註冊 Liker ID](https://docs.like.co/v/zh/user-guide/liker-id/how-to-register-a-liker-id)。

### 修改 post.hbs

將 IFrame 代碼加入 `post.hbs`並將 \[LikerID\] 更改為你的 Liker ID

```text
<div class="likecoin-embed likecoin-like-button" style="text-align:center">
    <div>
        <iframe scrolling="no" frameborder="0" src="https://button.like.co/in/embed/[LikerID]/button/?referrer={{ url absolute="true"}}" sandbox="allow-scripts allow-same-origin allow-popups allow-popups-to-escape-sandbox allow-top-navigation-by-user-activation allow-storage-access-by-user-activation"></iframe>
    </div>
</div>
```

### 修整讚賞鍵外觀

增加以下代碼到 css

```text
.likecoin-like-button {
  max-width: 485px;
  max-height: 240px;
  margin: 0 auto;
}
.likecoin-like-button > div {
  position: relative;
  padding-top: 49.48454%;
}
.likecoin-like-button > div iframe {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}
```

 完成。

### 參考文章

> [LikeCoin button ghost integration](https://stanleytsau.me/likebutton-ghost-integration/)

