---
description: How to embed LikeCoin button into Jekyll
---

# Jekyll

Thanks user [PinGuの独り言](https://pingu.moe/2020/01/integrate-likebutton-with-jekyll/) for the tutorial.

Before adding the LikeCoin button, please [register a Liker ID](https://docs.like.co/user-guide/liker-id/how-to-register-a-liker-id).

### Config liker\_id in \_config.yml  <a id="&#x5F9E;_configyml&#x8A2D;&#x5B9A;liker_id"></a>

Add `liker_id` in `_config.yml` , and change \[LikerID\] into your Liker ID

```text
# Enter your Liker ID to enable LikeCoin button
liker_id: [LikerID]
```

Define the variables in `_config.yml` can be obtained in the site object, which is `{{site.liker_id}}`

```text
https://button.like.co/in/embed/{{site.liker_id}}/button?referrer={{ page.url | absolute_url | cgi_escape }}
```

### Insert iframe <a id="&#x63D2;&#x5165;iframe"></a>

Develop the LikeCoin buton HTML

```text
{% if site.liker_id %}
<iframe
  src="https://button.like.co/in/embed/{{site.liker_id}}/button?referrer={{ page.url | absolute_url | cgi_escape }}">
</iframe>
{% endif %}
```

 用 if 檢查 liker\_id 是否存在。接著要在 post 樣板裡加入剛才的片段，找個接近區段結束的地方寫上 `{% include likeco.html %}`

Use if to inspect if liker\_id exists. Then add the code into post template, find a place near the end and add

建置一次，文章末端已經可以看到讚賞鍵，不過大小還要調整。讚賞鍵的元件會自行適應以維持長寬比，其長寬約為 485px\*240px。使用以下程式碼把它置中自動縮放並隱藏卷軸。

```text
{% if site.liker_id %}
<iframe
  style="width: 100%; max-width: 485px; height: 240px; margin: auto; overflow: hidden; display: block;"
  src="https://button.like.co/in/embed/{{site.liker_id}}/button?referrer={{ page.url | absolute_url | cgi_escape }}">
</iframe>
{% endif %}
```

### 參考文章

> [幫jekyll加上likecoin](https://blog.allmwh.org/2020-02/jekyll-likecoin/)

> [給Jekyll加上LikeButton賺錢錢](https://pingu.moe/2020/01/integrate-likebutton-with-jekyll/)

> [Add LikeWidget to Github Pages](https://klee1611.github.io/likecoin-button-jekyll.html)

