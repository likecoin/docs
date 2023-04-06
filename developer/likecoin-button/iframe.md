---
description: WidgetEmbed LikeCoin button using <iframe>
---

# Widget & Iframe

LikeCoin button is available as either an embedded page which can be used in an `iframe`, or a widget which can be used as a clickable link or popup.

### **Instructions**

#### **Construct an URL according to the following format:**

* **Iframe** base URL:

`https://button.like.co/in/embed/{{LikerID}}/button?iscn_id={{iscn_id}}&referrer={{referrer}}&type={{type}}`

* **Widget** base URL:

`https://button.like.co/in/like/{{LikerID}}?iscn_id={{iscn_id}}&referrer={{referrer}}&type={{type}}`

| Parameter  | Type     | Required?                                                      | Description                                                                                                                                                                                     |
| ---------- | -------- | -------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `LikerID`  | `string` | required if using `referrer`, set to `iscn` if using `iscn_id` | The LikerID of the content author. Set to `iscn` if using `iscn_id`                                                                                                                             |
| `iscn_id`  | `string` | either `referrer` or `iscn_id` is required                     | The ISCN ID of the content, overrides `referrer`                                                                                                                                                |
| `referrer` | `string` | either `referrer` or `iscn_id` is required                     | The source (canonical) URL of the content in `encodeURIComponent()` format (this also works as the content key)                                                                                 |
| `type`     | `string` | optional                                                       | `wp` for WordPress site, omit for the others                                                                                                                                                    |
| `preview`  | `number` | optional                                                       | Set to `1` to set the button to preview mode. This stop the button from automatically calling like.co API. Useful for develop/staging environment e.g. to prevent leaking dev server's address. |

> For testing purpose, you may use `button.rinkeby.like.co` instead of `button.like.co`

Example links:

* Widget with `referrer` : [`https://button.rinkeby.like.co/in/like/williamchong-du/?referrer=https%3A%2F%2Fmedium.com%2F%40likecoin_fdn%2Ftest-776059ed593523322`](https://button.rinkeby.like.co/in/like/williamchong-du/?referrer=https%3A%2F%2Fmedium.com%2F%40likecoin\_fdn%2Ftest-776059ed593523322)
* Iframe embbed with `iscn_id` : [`https://button.rinkeby.like.co/in/embed/iscn/button?iscn_id=iscn%3A%2F%2Flikecoin-chain%2Fy4JWyvv9mW6zo9rB0Pp-aPw6_655ljCFJI-B19R6F-g%2F1`](https://button.rinkeby.like.co/in/embed/iscn/button?iscn\_id=iscn%3A%2F%2Flikecoin-chain%2Fy4JWyvv9mW6zo9rB0Pp-aPw6\_655ljCFJI-B19R6F-g%2F1)

> In case of iframe sandbox, `allow-scripts`, `allow-same-origin`, `allow-popups` `allow-popups-to-escape-sandbox`, `allow-top-navigation-by-user-activation`, `allow-storage-access-by-user-activation` are needed for proper register/login functionality.

#### **Extra feature for embedded Iframe**

* CSS Style

Embed the [sample HTML](https://github.com/likecoin/LikeCoinButton-integration/blob/master/web/index.html) and replace \{{ src \}} with the embed URL into your HTML, include the [CSS code](https://github.com/likecoin/LikeCoinButton-integration/blob/master/web/style.css) for recommended display style.

* &#x20;Update referrer via [postMessage](https://github.com/likecoin/LikeCoinButton-integration/blob/master/web/postMessage.html)

The LikeCoin button `<iframe>`'s src (especially the `referrer` param) should be updated to when the URL is changed. In case updating `<iframe>`'s src is not possible (e.g. for some SPA usecases), you may call `postMessage()` to the `<iframe>` with following payload to update the `referrer`.

```
{
  action: 'SET_REFERRER',
  content: { referrer: `${ newReferrer||window.location.href }` }
}, 'https://button.like.co'
```

### Sample Repository

[https://github.com/likecoin/LikeCoinButton-integration](https://github.com/likecoin/LikeCoinButton-integration/tree/master/web)\


### Integration Examples

[https://medium.com/likecoin/likecoin-button-%E6%95%B4%E5%90%88%E6%96%B9%E6%B3%95%E5%92%8C%E7%A4%BA%E7%AF%84-579045858eae](https://medium.com/likecoin/likecoin-button-%E6%95%B4%E5%90%88%E6%96%B9%E6%B3%95%E5%92%8C%E7%A4%BA%E7%AF%84-579045858eae)\
(Chinese article)
