---
description: Embed LikeCoin button using <iframe>
---

# IFrame

### **Instructions**

#### **1. Construct an embedded URL according to the following format:**

```text
https://button.like.co/in/embed/{{LikerID}}/button?referrer={{referrer}}&type={{type}}
```

| Parameter | Type | Required? | Description |
| :--- | :--- | :--- | :--- |
| `LikerID` | `string` | required | The author of the content |
| `referrer` | `string` | required | The source \(canonical\) URL of the content in `encodeURIComponent()` format \(this also works as the content key\) |
| `type` | `string` | optional | `wp` for WordPress site, omit for the others |
| `preview` | `number` | optional | Set to `1` to set the button to preview mode. This stop the button from automatically calling like.co API. Useful for develop/staging environment e.g. to prevent leaking dev server's address. |

> For testing purpose, you may use `button.rinkeby.like.co` instead of `button.like.co`

> In case of iframe sandbox, `allow-scripts`, `allow-same-origin`, `allow-popups` `allow-popups-to-escape-sandbox`, `allow-top-navigation-by-user-activation`, `allow-storage-access-by-user-activation` are needed for proper register/login functionality.

**2 Embed the** [**sample HTML**](https://github.com/likecoin/LikeCoinButton-integration/blob/master/web/index.html) **and replace {{ src }} with the embed URL into your HTML**

**3 Include the** [**CSS code**](https://github.com/likecoin/LikeCoinButton-integration/blob/master/web/style.css)\*\*\*\*

**4 \(Optional\) Update referrer via** [**postMessage**](https://github.com/likecoin/LikeCoinButton-integration/blob/master/web/postMessage.html)\*\*\*\*

The LikeCoin button `<iframe>`'s src \(especially the `referrer` param\) should be updated to when the URL is changed. In case updating `<iframe>`'s src is not possible \(e.g. for some SPA usecases\), you may call `postMessage()` to the `<iframe>` with following payload to update the `referrer`.

```text
{
  action: 'SET_REFERRER',
  content: { referrer: `${ newReferrer||window.location.href }` }
}, 'https://button.like.co'
```

### Reference Repository

[https://github.com/likecoin/LikeCoinButton-integration](https://github.com/likecoin/LikeCoinButton-integration/tree/master/web)  


### Integration Examples

[https://medium.com/likecoin/likecoin-button-%E6%95%B4%E5%90%88%E6%96%B9%E6%B3%95%E5%92%8C%E7%A4%BA%E7%AF%84-579045858eae](https://medium.com/likecoin/likecoin-button-%E6%95%B4%E5%90%88%E6%96%B9%E6%B3%95%E5%92%8C%E7%A4%BA%E7%AF%84-579045858eae)  
\(Chinese article\)

