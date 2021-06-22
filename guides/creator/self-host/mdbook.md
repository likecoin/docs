---
description: How to embed LikeCoin button into mdBook
---

# mdBook

Thanks to the user [道場除草機](https://dltdojo.github.io/taichu-crypto/dao/likecoin.html#likecoin) for the tutorial.

Before adding the LikeCoin button, please [register a Liker ID](https://docs.like.co/user-guide/liker-id/register).

Use Javascript to create the following HTML in browsers and put it into static HTML created by mdBook.

```text
<div class="likecoin-embed likecoin-button">
  <div></div>
  <iframe scrolling="no" frameborder="0" 
    src="https://button.like.co/in/embed/LikerID/button?referrer=http://yourhost/foo/page.html">
  </iframe>
</div>
```

Add`likebutton.js` besides `book.toml` to custom made mdBook，you can also use `sdk.js` in [likecoin/likecoin-button-sdk](https://github.com/likecoin/likecoin-button-sdk), it works the same.

likebutton.js

```text
const LIKER_ID = "dltdojo";//Replace your own Liker ID
let likeurl = `https://button.like.co/in/embed/${LikerID}/button?referrer=${encodeURI(window.location.href)}`;
let el = document.getElementsByClassName("likebutton")[0];
if(el){
    el.innerHTML = `<div class="likecoin-embed likecoin-button">
  <div></div>
  <iframe scrolling="no" frameborder="0" src="${likeurl}"></iframe>
</div>`;
}
```

 Copy [LikeCoinButton-integration/style.css](https://github.com/likecoin/LikeCoinButton-integration/blob/master/web/style.css) and make it to become `likebutton.css`

```text
.likecoin-button {
  position: relative;
  width: 100%;
  max-width: 485px;
  max-height: 240px;
  margin: 0 auto;
}
.likecoin-button > div {
  padding-top: 49.48454%;
}
.likecoin-button > iframe {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}
```

Edit `book.toml` in `output.html` and add the js and css

```text
[output.html]
default-theme = "coal"
mathjax-support = true
additional-js = ["likebutton.js"]
additional-css = ["likebutton.css"]
```

Take a look at which pages you need to add your LikeCoin button in md, just add a div and use class to display the LikeCoin button.

```text
<div class="likebutton"/>
```

The above indicates that the div in md convert to HTML by mdbook build and release the LikeCoin button.

This is for one Liker ID only, multiple users can be achieved by getElementsByClassName\(LikerIDFoo\).

