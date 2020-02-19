---
description: 以 JavaScript 在 Blogspot 等各家網誌的文末、側欄產生 LikeCoin button
---

# Blogspot

感謝用戶 [浩剛](https://danieltw.net/archives/author/daniel) 製作程式碼，只需透過側欄小工具或者修改佈景主題原始碼，置入 JavaScript 就可以在每篇文筆中自動產生讚賞鍵。

安裝讚賞鍵以前，請先 [註冊 Liker ID](https://docs.like.co/v/zh/user-guide/liker-id/how-to-register-a-liker-id)。

### 在側欄放置讚賞鍵

在版面配置的頁面，任一地方新增「HTML/JavaScript」小工具，貼上以下的 JavaScript 語法並將 \[Liker ID\] 更改為你的 Liker ID 再儲存，讚賞鍵便會自動出現。

```text
<script type="text/javascript">
    document.write("<iframe scrolling='no' frameborder='0' sandbox='allow-scripts allow-same-origin allow-popups allow-popups-to-escape-sandbox allow-storage-access-by-user-activation' style='height: 212px; width: 100%;' src='https://button.like.co/in/embed/[Liker ID]/button?referrer="+encodeURIComponent(location.href.split("?")[0].split("#")[0])+"'></iframe>");
</script>
```

### 在文章末段放置讚賞鍵







