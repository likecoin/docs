---
description: 如何在 Hexo 開發環境的文章中加入 LikeCoin button
---

# Hexo

感謝用戶 [只是個打字的](https://blog.typeart.cc) 的教學範本。

安裝讚賞鍵以前，請先 [註冊 Liker ID](../../liker-id/)。

### 增加根據文章網址，自動產生讚賞鍵鏈結

在 `themes/next/layout/_custom/` 目錄下新增一檔案 `like_coin.ejs` 並貼上下列程式碼，並將 \[LikerID] 更改為你的 Liker ID。

```
<div>
  <script type="text/javascript">
    document.write(
      "<iframe scrolling='no' frameborder='0' sandbox='allow-scripts allow-same-origin allow-popups allow-popups-to-escape-sandbox allow-storage-access-by-user-activation' style='height: 212px; width: 100%;' src='https://button.like.co/in/embed/[LikerID]/button?referrer=" +
      encodeURIComponent(location.href.split("?")[0].split("#")[0]) + "'></iframe>");
  </script>
<div>
```

### 在每篇文章末端加上讚賞鍵

打開 `themes/next/layout/_macro/post.swig` 在合適的位置把 `like_coin.ejs` 放置好

```
 {% raw %}
{% if theme.related_posts.enable and (theme.related_posts.display_in_home or not is_index) %}
+      {% include '../_custom/like_coin.ejs' %}
      {% include '../_partials/post/post-related.swig' with { post: post } %}
    {% endif %}
{% endraw %}
```

&#x20;如果您沒有開啟相關文章的話，則加在往上幾行的 `{{ post.content }}` 後方

```
        {% raw %}
{% else %}
          {% if post.type === 'picture' %}
            <a href="{{ url_for(post.path) }}">{{ post.content }}</a>
          {% else %}
            {{ post.content }}
+      {% include '../_custom/like_coin.ejs' %}
          {% endif %}
        {% endif %}
      {% else %}
        {{ post.content }}
+      {% include '../_custom/like_coin.ejs' %}
      {% endif %}
{% endraw %}
    </div>
```

完成後就可以看到讚賞鍵出現在文章中。

### 參考文章

> [在Hexo NexT增加like Button](https://blog.typeart.cc/%E5%9C%A8Hexo%20NexT%E5%A2%9E%E5%8A%A0like%20Button/)

> [如何将Liker按钮集成到Hexo](https://hive.blog/cn/@aafeng/liker-hexo)

> [藍圖重生（一）：給 Hexo 文章 加上 LikeCoin 的贊賞鍵> ](https://blog.mykeyvans.science/posts/add-likebutton-for-hexo.html)

> [Hexo教學2 iframe(likecoin)> ](https://allem40306.github.io/blog/posts/183a/)
