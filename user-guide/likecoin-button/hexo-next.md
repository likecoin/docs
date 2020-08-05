# Hexo

Thanks user [只是個打字的](https://blog.typeart.cc/) for the tutorial.

Before adding the LikeCoin button, please [register a Liker ID](https://docs.like.co/user-guide/liker-id/how-to-register-a-liker-id).

### Function: Add LikeCoin button automatically according to the article URL

In directly `themes/next/layout/_custom/` add a new file `like_coin.ejs` and paste in the following code, change the \[LikerID\] to your Like ID.

```text
<div>
  <script type="text/javascript">
    document.write(
      "<iframe scrolling='no' frameborder='0' sandbox='allow-scripts allow-same-origin allow-popups allow-popups-to-escape-sandbox allow-storage-access-by-user-activation' style='height: 212px; width: 100%;' src='https://button.like.co/in/embed/[LikerID]/button?referrer=" +
      encodeURIComponent(location.href.split("?")[0].split("#")[0]) + "'></iframe>");
  </script>
<div>
```

### Add LikeCoin button at the end of each article

Open `themes/next/layout/_macro/post.swig` and put `like_coin.ejs`  into the approproate position

```text
 {% if theme.related_posts.enable and (theme.related_posts.display_in_home or not is_index) %}
+      {% include '../_custom/like_coin.ejs' %}
      {% include '../_partials/post/post-related.swig' with { post: post } %}
    {% endif %}
```

 如果您沒有開啟相關文章的話，則加在往上幾行的 `{{ post.content }}` 後方

```text
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
    </div>
```

完成後就可以看到讚賞鍵出現在文章中。

### 參考文章

> [在 Hexo Blog 上安裝 LikeCoin 賺錢錢 👍](https://sealman234.github.io/hexo/20200622/2807510721/)

> [在Hexo NexT增加like Button](https://blog.typeart.cc/%E5%9C%A8Hexo%20NexT%E5%A2%9E%E5%8A%A0like%20Button/)

> [如何将Liker按钮集成到Hexo](https://hive.blog/cn/@aafeng/liker-hexo)

> [藍圖重生（一）：給 Hexo 文章 加上 LikeCoin 的贊賞鍵](https://blog.mykeyvans.science/posts/add-likebutton-for-hexo.html)

> [Hexo教學2 iframe\(likecoin\)](https://allem40306.github.io/blog/posts/183a/)

