---
description: 如何在 Write.as 文章中加入讚賞鍵
---

# Write.as

感謝用戶 [夏](https://natsushyo.me/) 的教學範本。

安裝讚賞鍵以前，請先 [註冊 Liker ID](https://docs.like.co/v/zh/user-guide/liker-id/how-to-register-a-liker-id)。

首先你需要加入 [Write.as Pro](https://write.as/pro) 服務方可使用 Javascript。

把 Javascript 程式碼中的 \[LikerID\] 更改為你的 Liker ID，再將它黏貼到 Write.as 設定裡的 "Custom Javascript" 欄位，有需要可加入 CSS 調整版面字型等樣式即可。

```text
var topP = document.createElement("p");
topP.innerHTML = '<div class="custom-nav"><a href="#">Back to top ↑</a></div>';

var cont = document.getElementById("wrapper");
if (cont !== null) {
// Add to blog index and tag pages
cont.appendChild(topP);
} else {
// Add to individual blog post page
cont = document.getElementById("post-body");
cont.insertAdjacentHTML("afterend", topP.outerHTML);
cont.insertAdjacentHTML("afterend", "<div class='custom-nav likecoin'><p>-<br><em>如果你喜歡我的文字，請幫忙按 5 下 Like！我將得到 LikeCoin 的回饋。</em></p><p>回饋由 <a rel='nofollow'  href='https://like.co/'>LikeCoin</a> 基金會出資，只要註冊/登入帳號，點 5 下 Like 就可以贊助我的文章。化讚為賞，支持創作。謝謝你！</p><iframe scrolling='no' frameborder='0' width='640' height='212' src='https://button.like.co/in/embed/[LikerID]
/button?referrer="+encodeURIComponent(location.href.split("?")[0].split("#")[0])+"'></iframe></div>");
}
```

### 參考文章

> [傻瓜如何加入LikeButton到Write.as網誌中](https://natsushyo.me/sha-gua-ru-he-jia-ru-likebuttondao-write-aswang-zhi-zhong)

