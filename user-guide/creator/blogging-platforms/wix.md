---
description: How to embed LikeCoin button into Wix
---

# Wix / Weebly

Before adding the LikeCoin button, please [register a Liker ID](https://docs.like.co/user-guide/liker-id/register).

Create your LikeCoin button link according to the format below:

```text
https://button.like.co/in/embed/[LikerID]/button?referrer=[Web page URL]
```

If your Liker ID is ckxpress, URL is https://ckxpress.wixsite.com/likecoin/single-post/2020/02/22/LikeCoin

Your LikeCoin button link should be https://button.like.co/in/embed/ckxpress/button?referrer=https://ckxpress.wixsite.com/likecoin/single-post/2020/02/22/LikeCoin

Then open Edit HTML mode, copy and paste the following code into the position where your LikeCoin button to display. Please note that you have to replace the `{{ src }}` to be your LikeCoin button link.

```text
<div class="likecoin-embed likecoin-button">
  <div></div>
  <iframe scrolling="no" frameborder="0" src="{{ src }}"></iframe>
</div>
```

Like This

```text
<div class="likecoin-embed likecoin-button">
  <div></div>
  <iframe scrolling="no" frameborder="0" src="https://button.like.co/in/embed/ckxpress/button?referrer=https://ckxpress.wixsite.com/likecoin/single-post/2020/02/22/LikeCoin"></iframe>
</div>
```

After saving the code, the LikeCoin button will display on your article. You may want to use the advanced CSS function of WIX and modify the look and feel of the button.

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

### Reference

> [likecoin / LikeCoinButton-integration iframe](https://github.com/likecoin/LikeCoinButton-integration/tree/master/web#2iframe)

-------------------------

Weebly users can follow the same procedures to add a LikeCoin button.

-------------------------

You can also add LikeCoin button by the Javascript way, please refer to:

{% page-ref page="blogspot.md" %}

