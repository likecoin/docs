---
description: How to embed LikeCoin button into ghost
---

# ghost

Thanks to the user [STANLEY TSAU](https://stanleytsau.me/likebutton-ghost-integration/) for the tutorial, please note that you have to pay a membership fee for using [ghost](https://ghost.org/pricing/).

Before adding the LikeCoin button, please [register a Liker ID](https://docs.like.co/user-guide/liker-id/how-to-register-a-liker-id).

### Modify post hbs

Add the IFrame source code into `post.hbs` , change the  \[LikerID\] into your Liker ID

```text
<div class="likecoin-embed likecoin-like-button" style="text-align:center">
    <div>
        <iframe scrolling="no" frameborder="0" src="https://button.like.co/in/embed/[LikerID]/button/?referrer={{ url absolute="true"}}" sandbox="allow-scripts allow-same-origin allow-popups allow-popups-to-escape-sandbox allow-top-navigation-by-user-activation allow-storage-access-by-user-activation"></iframe>
    </div>
</div>
```

### Adjust the look and feel of LikeCoin button

Paste the follow code to css

```text
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

 All done.

