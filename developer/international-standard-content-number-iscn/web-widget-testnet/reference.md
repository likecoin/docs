---
description: ISCN(iscn-dev) web widget API Reference
---

# Reference

## Introduction

This is a PoC web widget connected to iscn-dev network for testing/demo/development purpose. We will update this widget later when ISCN feature is released on our production chain.

## Formatting the widget URL <a id="formatting-the-widget-url"></a>

### Base URL <a id="base-url"></a>

Testnet: [`https://rinkeby.like.co/in/widget/iscn/dev`](https://rinkeby.like.co/in/widget/iscn/dev)\`\`

Production: [`https://like.co/in/widget/iscn/dev`](https://like.co/in/widget/iscn/dev)\`\`

###  Input Params <a id="input-params"></a>

| Query String | Description |
| :--- | :--- |
| fingerprint | IPFS hash of content, cid v0 |
| type | Type of content, default is `article` |
| tags | \(optional\) list of tags separated by comma |
| title | Title of the content |
| license | License of the content. Fixed as CCSA 4.0 for now if `publisher` is not set |
| publisher | \(optional\) name of the platform if your content was published through a platform. Currently only `matters` is valid option. |
| state | \(optional\) local state to be passed back after signing success, used for data/security purpose |
| redirect\_uri | \(optional\) Act as a whitelist host for postMessage, actual redirect is not implemented, please use with `opener` below |
| opener | \(optional\) default false. If set, would fire a `postMessage` back to `window.opener` with `redirect_uri` host as target, then close current window |
| blocking | \(optional\) default false, wait until transaction is confirmed before finishing |

### Output Params <a id="output-params"></a>

| Query String | Description |
| :--- | :--- |
| tx\_hash | transaction hash of resulting payment, verify status using transaction status query API |
| error | set if any catchable error occur |
| success | only if `blocking` is set, return true if transaction success |
| state | locale state that was passed as input, used for data/security purpose |

### PostMessage format

if `opener` and `redirect_uri` is set, the widget would fire a `postMessage` to `redirect_uri` 's origin. 

```text
const message = JSON.stringify({
  action: 'ISCN_SUBMITTED',
  data: {
    tx_hash,
    error,
    state,
    success,
  },
});
this.windowOpener.postMessage(message, this.redirectOrigin);
window.close();
```

> >

### Example Link <a id="example-link"></a>

Following links are in testnet.

#### Input Link: <a id="input-link-https-rinkeby-like-co-in-widget-pay-to-ckxpress-and-amount-1-and-via-kiutest-0-and-fee-1-and-state-123-and-redirect_uri-http-3-a-2-f-2-flocalhost-3-a3000"></a>

#### [`https://rinkeby.like.co/in/widget/iscn/dev?fingerprint=QmcTD5FbyBimKbd3EZ8PtR19PyeMnouZ7hZ178z75hZGrs&publisher=matters&title=iscn&tags=%5B"iscn"%5D&opener=1&redirect_uri=http%3A%2F%2Flocalhost%3A8080`](https://rinkeby.like.co/in/widget/iscn/dev?fingerprint=QmcTD5FbyBimKbd3EZ8PtR19PyeMnouZ7hZ178z75hZGrs&publisher=matters&title=iscn&tags=%5B"iscn"%5D&opener=1&redirect_uri=http%3A%2F%2Flocalhost%3A8080)​ <a id="input-link-https-rinkeby-like-co-in-widget-pay-to-ckxpress-and-amount-1-and-via-kiutest-0-and-fee-1-and-state-123-and-redirect_uri-http-3-a-2-f-2-flocalhost-3-a3000"></a>

#### Tx Status Query:[`https://rinkeby.like.co/in/tx/iscn/dev/5108A861A1B21EB78ABEE8522F5933F0CB97CC11D2866FC93F4B8038C3B3730`](https://rinkeby.like.co/in/tx/iscn/dev/5108A861A1B21EB78ABEE8522F5933F0CB97CC11D2866FC93F4B8038C3B37301)\`\`[ ](https://docs.like.co/developer/like-pay/web-widget)

