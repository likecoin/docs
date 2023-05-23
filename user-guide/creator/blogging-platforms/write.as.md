---
description: How to embed LikeCoin button into Write.as
---

# Write.as

Thanks to the user [夏](https://natsushyo.me/sha-gua-ru-he-jia-ru-likebuttondao-write-aswang-zhi-zhong) for providing the tutorial.

Before adding the LikeCoin button, please [register a Liker ID](../../liker-id/).

First of all you have to register [Write.as Pro](https://write.as/pro) to use Javascript.

Change the Javascript code's \[LikerID] into your Liker ID, and post them into the "Custom Javascript" setting. Add CSS to adjust the fonts and outlook of the LikeCoin button if required.

```
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
cont.insertAdjacentHTML("afterend", "<div class='custom-nav likecoin'><p>-<br><em>如果你喜歡我的文字，請幫忙按 5 下 Like！我將得到 LikeCoin 的回饋。</em></p><p>回饋由 <a rel='nofollow'  href='https://like.co/'>LikeCoin</a> 基金會出資，只要註冊/登入帳號，點 5 下 Like 就可以贊助我的文章。化讚為賞，支持創作。謝謝你！</p><iframe scrolling='no' frameborder='0' width='640' height='212' src='https://button.like.co/in/embed/[LikerID]/button?referrer="+encodeURIComponent(location.href.split("?")[0].split("#")[0])+"'></iframe></div>");
}
```
