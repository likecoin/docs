---
description: NFT Portal technical reference
---

# NFT Portal Reference

## URL Portal

Allows inputting https URL or ISCN ID to prepare minting of Writing NFT

![](<../../../.gitbook/assets/image (33).png>)

### Base URL <a href="#base-url" id="base-url"></a>

Testnet: [`https://app.testnet.like.co/nft/url`](https://app.like.co/nft/url)

Production: [`https://app.like.co/nft/url`](https://app.like.co/nft/url)

### &#x20;Input Params <a href="#input-params" id="input-params"></a>

| Query String | Description                                                                                             |
| ------------ | ------------------------------------------------------------------------------------------------------- |
| url          | (optional) Prefill target URL                                                                           |
| iscn\_id     | (optional) Prefill target ISCN ID                                                                       |
| liker\_id    | (optional) Enforce Liker ID checking on user, an error would be prompted if target Liker ID is not used |

Other query strings are passed below to the ISCN page.

## ISCN Page

Mints an ISCN into Writing NFT

![](<../../../.gitbook/assets/image (32).png>)

### Base URL <a href="#base-url" id="base-url"></a>

Testnet: [`https://app.testnet.like.co/nft/iscn/${uri_encoded_iscn_id}/`](https://app.like.co/nft/url)

Production: [`https://app.like.co/nft/iscn/${uri_encoded_iscn_id}/`](https://app.like.co/nft/url)

### Input Params <a href="#input-params" id="input-params"></a>

|               |                                                                                                                                                    |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| nft\_prefix   | (optional) Override NFT name prefix, default is `Writing NFT`                                                                                      |
| class\_id     | (optional) Existing NFT Class ID to resume minting process from                                                                                    |
| redirect\_uri | (optional) Act as a whitelist host for postMessage, actual redirect is not implemented, please use with `opener` below                             |
| opener        | (optional) default false. If set, would fire a `postMessage` back to `window.opener` with `redirect_uri` host as target, then close current window |

### PostMessage Event Format

```javascript
window.opener.postMessage(JSON.stringify({
  action: 'NFT_MINT_DATA',
  data: {
    iscnId,
    classId,
    nftCount,
    sellerWallet,
  },
}), this.redirectOrigin)
```
