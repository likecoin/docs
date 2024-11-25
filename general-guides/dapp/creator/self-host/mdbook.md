---
description: How to embed LikeCoin button into mdBook
---

# mdBook

Thanks to the user [道場除草機](https://dltdojo.github.io/taichu-crypto/dao/likecoin.html#likecoin) for providing the tutorial.

Before adding the LikeCoin button, please [register a Liker ID](../../liker-id/).

Follow the steps below:

Use JavaScript to create the HTML: In the browser, create the following HTML structure and put it into the static HTML created by mdBook:

```
<div class="likecoin-embed likecoin-button">
  <div></div>
  <iframe scrolling="no" frameborder="0" 
    src="https://button.like.co/in/embed/LikerID/button?referrer=http://yourhost/foo/page.html">
  </iframe>
</div>
```

Add the `likebutton.js`: Place a file named `likebutton.js` next to `book.toml` in your custom-made mdBook. You can also use `sdk.js` from the [likecoin/likecoin-button-sdk](https://github.com/likecoin/likecoin-button-sdk), as it works the same.

Here's an example of the likebutton.js code:

```
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

Copy and modify the CSS: Copy the [LikeCoinButton-integration/style.css](https://github.com/likecoin/LikeCoinButton-integration/blob/master/web/style.css) file and rename it to become `likebutton.css`. Make the following modifications:

```
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

Edit the `book.toml`: Open the `book.toml` and add the following lines under the `output.html` section:

```
[output.html]
default-theme = "coal"
mathjax-support = true
additional-js = ["likebutton.js"]
additional-css = ["likebutton.css"]
```

Add the LikeCoin button to specific pages: In your markdown (md) files, add a \<div> element with the class "likebutton" where you want the LikeCoin button to appear. For example:&#x20;

```
<div class="likebutton"/>
```

The above instructions are for a single Liker ID. If you want to support multiple users, you can achieve it by using getElementsByClassName(LikerIDFoo).

Remember to build the mdBook and preview your website to see the LikeCoin button in action.
