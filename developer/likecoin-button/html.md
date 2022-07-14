---
description: Embed LikeCoin button by just including <script> in your website
---

# Javascript CDN

## Usage

1. Add the following `div` tag into the webpage at the position for embedding LikeCoin button:

`<div class="likecoin-embed likecoin-button" data-liker-id="{YOUR_LIKECOIN_ID}" data-href="YOUR_WEBPAGE_URL"></div>`

| Param             | Description                                    |
| ----------------- | ---------------------------------------------- |
| data-iscn-id      | Content's ISCN ID, overrides href and Liker ID |
| `data-liker-id`   | Creator's Liker ID                             |
| `data-liker-href` | Current content's canonical URL                |

Here, `data-liker-id` is required and refers to your Liker ID, where `data-href` is optional and refers to your page's canonical URL. If omitted, the SDK will use the current URL of the browser. It is suggested to always include a `data-href`

2\. Add the following `script` tag at the end of the `body` tag:

`<script src="https://static.like.co/sdk/v1/button.js"></script>`

### Sample HTML

{% code title="index.html" %}
```bash
<!DOCTYPE html>
<html lang="en">
<head>
    <title>LikeCoin button SDK demo</title>
</head>
<body>
<div class="likecoin-embed likecoin-button" data-liker-id="chungwu" data-href="https://docs.like.co/developer/likecoin-button/"></div>
<script src="https://static.like.co/sdk/v1/button.js"></script>
</body>
</html>

```
{% endcode %}

### Source Repository

[https://github.com/likecoin/likecoin-button-sdk](https://github.com/likecoin/likecoin-button-sdk)
