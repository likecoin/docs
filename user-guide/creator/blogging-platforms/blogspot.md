---
description: 以 JavaScript 在 Blogspot 等各家網誌的文末、側欄產生讚賞鍵
---

# Blogspot

感謝用戶 [浩剛](https://danieltw.net/archives/author/daniel) 製作程式碼，只需透過側欄小工具或者修改佈景主題原始碼，置入 JavaScript 就可以在每篇文筆中自動產生讚賞鍵。

安裝讚賞鍵以前，請先 [註冊 Liker ID](../../liker-id/)。

### 在側欄放置讚賞鍵

在版面配置的頁面，任一地方新增 "HTML/JavaScript" 小工具，貼上以下的 JavaScript 程式碼並將 \[LikerID] 更改為你的 Liker ID 再儲存，讚賞鍵便會自動出現。

```
<script type="text/javascript">
    document.write("<iframe scrolling='no' frameborder='0' sandbox='allow-scripts allow-same-origin allow-popups allow-popups-to-escape-sandbox allow-storage-access-by-user-activation' style='height: 212px; width: 100%;' src='https://button.like.co/in/embed/[LikerID]/button?referrer="+encodeURIComponent(location.href.split("?")[0].split("#")[0])+"'></iframe>");
</script>
```

### 在文章末段放置讚賞鍵

進入佈景「主題」後點「編輯HTML」並搜尋 **data:post.body** ，在看到 `</div>` 後換行插入以下程式碼，並將 \[LikerID] 更改為你的 Liker ID ：

```
<b:if cond='data:blog.pageType == "item"'>
    <script type="text/javascript">
        document.write("<iframe scrolling='no' frameborder='0' sandbox='allow-scripts allow-same-origin allow-popups allow-popups-to-escape-sandbox allow-storage-access-by-user-activation' style='height: 212px; width: 100%;' src='https://button.like.co/in/embed/[LikerID]/button?referrer="+encodeURIComponent(location.href.split("?")[0].split("#")[0])+"'></iframe>");
    </script>
</b:if>
```

**data:post.body** 舉例如下&#x20;

```
<!-- Then use the post body as the schema.org description, for good G+/FB snippeting. -->
<div class='post-body entry-content' expr:id='"post-body-" + data:post.id' expr:itemprop='(data:blog.metaDescription ? "" : "description ") + "articleBody"'>
  <data:post.body/>
  <div style='clear: both;'/> <!-- clear for photos floats -->
</div>
```

在 `</div>` 後加入程式碼後變成

```
<!-- Then use the post body as the schema.org description, for good G+/FB snippeting. -->
<div class='post-body entry-content' expr:id='"post-body-" + data:post.id' expr:itemprop='(data:blog.metaDescription ? "" : "description ") + "articleBody"'>
  <data:post.body/>
  <div style='clear: both;'/> <!-- clear for photos floats -->
</div>

<b:if cond='data:blog.pageType == "item"'>
    <script type="text/javascript">
        document.write("<iframe scrolling='no' frameborder='0' sandbox='allow-scripts allow-same-origin allow-popups allow-popups-to-escape-sandbox allow-storage-access-by-user-activation' style='height: 212px; width: 100%;' src='https://button.like.co/in/embed/[LikerID]/button?referrer="+encodeURIComponent(location.href.split("?")[0].split("#")[0])+"'></iframe>");
    </script>
</b:if>
```

假如「編輯HTML」看到有兩個 **data:post.body** 有可能一個是電腦頁面，另一個是手機頁面，那麼兩邊都要放置程式碼。留意手機版面要改成「自訂」才會顯示讚賞鍵。

\-------------------------

使用其他網誌服務的用戶，只要支援修改佈景主題，也可以嘗試使用這種方式加入讚賞鍵。

### 參考文章

> [以JavaScript在Blogger等各家網誌的文末、側欄產生LikeButton](https://danieltw.net/archives/2444)

> [LikeCoin如何放在Blogger或其他地方](https://stationery.raypuppy.com/2019/01/08/2755/)
