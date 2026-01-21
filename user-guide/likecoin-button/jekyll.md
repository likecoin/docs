---
description: 如何在 Jekyll 開發環境的文章中加入讚賞鍵
---

# Jekyll

感謝用戶 [PinGuの独り言](https://pingu.moe/2020/01/integrate-likebutton-with-jekyll/) 的教學範本。

安裝讚賞鍵以前，請先 [註冊 Liker ID](https://docs.like.co/v/zh/user-guide/liker-id/how-to-register-a-liker-id)。

### 從 \_config.yml 設定 liker\_id <a id="&#x5F9E;_configyml&#x8A2D;&#x5B9A;liker_id"></a>

先在 `_config.yml` 加入 `liker_id` 鍵值，並將 \[LikerID\] 更改為你的 Liker ID

```text
# Enter your Liker ID to enable LikeCoin button
liker_id: [LikerID]
```

宣告在`_config.yml` 的變數可以從物件 site 中取得，也就是 `{{site.liker_id}}`

```text
https://button.like.co/in/embed/{{site.liker_id}}/button?referrer={{ page.url | absolute_url | cgi_escape }}
```

### 插入 iframe <a id="&#x63D2;&#x5165;iframe"></a>

先建立讚賞鍵的 HTML 片段

```text
{% if site.liker_id %}
<iframe
  src="https://button.like.co/in/embed/{{site.liker_id}}/button?referrer={{ page.url | absolute_url | cgi_escape }}">
</iframe>
{% endif %}
```

 用 if 檢查 `liker_id` 是否存在。接著要在 post 樣板裡加入剛才的片段，找個接近區段結束的地方寫上 `{% include likeco.html %}`

建置一次，文章末端已經可以看到讚賞鍵，不過大小還要調整。讚賞鍵的元件會自行適應以維持長寬比，其長寬約為 485px\*240px。使用以下程式碼把它置中自動縮放並隱藏卷軸。

```text
{% if site.liker_id %}
<iframe
  style="width: 100%; max-width: 485px; height: 240px; margin: auto; overflow: hidden; display: block; border: 0;"
  src="https://button.like.co/in/embed/{{site.liker_id}}/button?referrer={{ page.url | absolute_url | cgi_escape }}">
</iframe>
{% endif %}
```

### 參考文章

> [幫jekyll加上likecoin](https://blog.allmwh.org/2020-02/jekyll-likecoin/)

> [給Jekyll加上LikeButton賺錢錢](https://pingu.moe/2020/01/integrate-likebutton-with-jekyll/)

> [Add LikeWidget to Github Pages](https://klee1611.github.io/likecoin-button-jekyll.html)

