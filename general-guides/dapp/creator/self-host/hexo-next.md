---
description: How to embed LikeCoin button into Hexo
---

# Hexo

Thanks to the user [只是個打字的](https://docs.like.co/v/zh/user-guide/likecoin-button/hexo-next) for providing the tutorial.

Before adding the LikeCoin button, please [register a Liker ID](../../liker-id/).

### Function: Add LikeCoin button automatically according to the post URL

In directory `themes/next/layout/_custom/` add a new file named `like_coin.ejs` and paste in the following code, change the \[LikerID] to your actual Like ID.

```
<div>
  <script type="text/javascript">
    document.write(
      "<iframe scrolling='no' frameborder='0' sandbox='allow-scripts allow-same-origin allow-popups allow-popups-to-escape-sandbox allow-storage-access-by-user-activation' style='height: 212px; width: 100%;' src='https://button.like.co/in/embed/[LikerID]/button?referrer=" +
      encodeURIComponent(location.href.split("?")[0].split("#")[0]) + "'></iframe>");
  </script>
<div>
```

### Add the LikeCoin button at the end of each post

Open `themes/next/layout/_macro/post.swig` and place the `like_coin.ejs` in the appropriate position:

```
 {% raw %}
{% if theme.related_posts.enable and (theme.related_posts.display_in_home or not is_index) %}
+      {% include '../_custom/like_coin.ejs' %}
      {% include '../_partials/post/post-related.swig' with { post: post } %}
    {% endif %}
{% endraw %}
```

&#x20;If you do not enable the related post function, then add it after the `{{ post.content }}`

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

LikeCoin buttons will now appear on your articles.
