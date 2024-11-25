---
description: How to embed LikeCoin button into ghost
---

# ghost

Thanks to the user [STANLEY TSAU](https://stanleytsau.me/likebutton-ghost-integration/) for providing the tutorial. Please note that a membership fee is required for using [Ghost](https://ghost.org/pricing/).

Before adding the LikeCoin button, please [register a Liker ID](../../liker-id/).

### Modify post hbs

Add the IFrame source code into `post.hbs` , change the \[LikerID] into your actual Liker ID

```
<div class="likecoin-embed likecoin-like-button" style="text-align:center">
    <div>
        <iframe scrolling="no" frameborder="0" src="https://button.like.co/in/embed/[LikerID]/button/?referrer={{ url absolute="true"}}" sandbox="allow-scripts allow-same-origin allow-popups allow-popups-to-escape-sandbox allow-top-navigation-by-user-activation allow-storage-access-by-user-activation"></iframe>
    </div>
</div>
```

### Adjust the look and feel of the LikeCoin button

Paste the follow code into the CSS:

```
.likecoin-like-button {
  max-width: 485px;
  max-height: 240px;
  margin: 0 auto;
}
.likecoin-like-button > div {
  position: relative;
  padding-top: 49.48454%;
}
.likecoin-like-button > div iframe {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}
```

&#x20;All done.
