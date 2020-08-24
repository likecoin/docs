---
description: 如何在 Hugo 開發環境的文章中加入讚賞鍵
---

# Hugo

感謝用戶  [Wancat](https://www.wancat.cc/) 的教學範本。

安裝讚賞鍵以前，請先 [註冊 Liker ID](https://docs.like.co/v/zh/user-guide/liker-id/how-to-register-a-liker-id)。

先為你的網站選擇一個主題，以下採用 [CleanWhite](https://themes.gohugo.io/hugo-theme-cleanwhite) 這套主題作例子。

Hugo 可以使用自訂 Layout 的方式，在不改變主題的情況下改變網站設計，用戶可透過這個方式在每篇文章下放置讚賞鍵。

首先覆蓋文章的模板，將 `theme` 的 `layouts` 資料夾複製到專案目錄下

```text
cp -r theme/YOUR_THEME/layouts/ .
```

Hugo 中的 [Partial Templates](https://gohugo.io/templates/partials/) 可以讓你建立小模板，嵌入在頁面中。在 `layouts` 的 `partials` 資料夾建立 `likecoin.html`，寫入以下內容。你也可以在這裡以 HTML 格式加上想給讀者看的說明文字

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

### 參考文章

> [Hugo 安裝 LikeCoin 教學](https://www.wancat.cc/post/hugo-install-likecoin/)

> [Hugo使用Likecoin教學](https://matters.news/@cason_yang/hugo%E4%BD%BF%E7%94%A8likecoin%E6%95%99%E5%AD%B8-bafyreicc6dbprwwbnx3argddlvrpxjnw5xzh3knecyv3cyr6aelzwiskhy)

> [\[hugo\]在hugo安裝likecoin按鈕](https://web.kmp.tw/post/howtoaddlikecoinbuttoninhugo/)

> [【LikeCoin應用技】我是如何想到在Markdown格式裡面加入LikeCoin讚賞鏈（附上教學）](https://matters.news/@bluebear119/like-coin%E6%87%89%E7%94%A8%E6%8A%80-%E6%88%91%E6%98%AF%E5%A6%82%E4%BD%95%E6%83%B3%E5%88%B0%E5%9C%A8markdown%E6%A0%BC%E5%BC%8F%E8%A3%A1%E9%9D%A2%E5%8A%A0%E5%85%A5like-coin%E8%AE%9A%E8%B3%9E%E9%8F%88-%E9%99%84%E4%B8%8A%E6%95%99%E5%AD%B8-bafyreiej7yckxo6lueua7pyixrra7gai5hxr72n56zob4l7sod5rswloaa)

