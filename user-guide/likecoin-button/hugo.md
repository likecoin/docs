---
description: How to embed LikeCoin button into Hugo
---

# Hugo

Thanks user [Wancat](https://www.wancat.cc/post/hugo-install-likecoin/) for the tutorial.

Before adding the LikeCoin button, please [register a Liker ID](https://docs.like.co/user-guide/liker-id/how-to-register-a-liker-id).

Choose a theme for your website first, the following is an example of [CleanWhite](https://themes.gohugo.io/hugo-theme-cleanwhite). 

Hugo allows user to use custom Layout in order to change the website design without altering the theme, LikeCoin button can be added with this function.

The 1st step is to copy the article template, copy the layouts folder in theme to the directory of the repository

```text
cp -r theme/YOUR_THEME/layouts/ .
```

Hugo allows users to create simple templates with [Partial Templates](https://gohugo.io/templates/partials/) and embed it into a page. Create `likecoin.html` in `partials` folder of `layouts`, fill in the following code. Words to encourage clapping of LikeCoin button can also be included in HTML format.

```text
<iframe class="LikeCoin" height="235" src="https://button.like.co/in/embed/{{ .Site.Params.likerID }}/button?referrer={{ .Permalink }}" width="100%" frameborder=0></iframe>
```

 接下來在 `config.toml` 中加入以下程式碼，並將 \[LikerID\] 更改為你的 Liker ID 

```text
[[params]]
	likerID = "likerID"
```

接著編輯文章使用的模板，通常位處於 `_default/single.html`。這就是一個 Go Template，在你想要的地方插入，建議插在 `{{ .Content }}` 後面，這樣 LikeCoin button 就會接續出現文章下面

```text
{{ partial "likecoin.html" . }}
```

這樣 Hugo 就會將 LikeCoin 這個 partial render 到你的文章中了。記得加上 “."，沒有的話，LikeCoin 的模板讀不到資料。留意整個過程都不需要修改 theme 的原始程式

最後執行 `hugo server` 預覽你的網站。

