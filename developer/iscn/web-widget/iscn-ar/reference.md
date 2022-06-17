---
description: ISCN AR web widget API Reference
---

# Reference

### Base URL <a href="#base-url" id="base-url"></a>

Testnet: [`https://testnet.like.co/in/widget/iscn-ar`](https://testnet.like.co/in/widget/iscn-ar)``

Production: [`https://like.co/in/widget/iscn-ar`](https://like.co/in/widget/iscn-ar)``

Since `postMessage()` would be needed for operating this widget, caller is expected to use `window.open` on the above urls.

### &#x20;Input Params <a href="#input-params" id="input-params"></a>

| redirect\_uri | Act as a whitelist host for postMessage, actual redirect is not implemented, please use with `opener` below                                              |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| opener        | default 0. If set, would fire a `postMessage` back to `window.opener` with `redirect_uri` host as target, then close current window                      |
| iscn\_id      | (optional) For updating existing ISCN record, the encoded ISCN ID for update. Note that the record would be completely overwritten with the new metadata |

### PostMessage input format

#### Mark widget as ready

Send this action to switch widget to ready to accept mode.

```javascript
{ action: 'INIT_WIDGET' }
```

| Key    | Value        |   |
| ------ | ------------ | - |
| action | INIT\_WIDGET |   |

#### Send ISCN Data

Submit ISCN data to widget

```javascript
{
    action: 'SUBMIT_ISCN_DATA',
    data: {
      files: [
        {
          filename: 'index.html',
          mimeType: 'text/html',
          data: 'PCFET0NUWVBFIGh0bWw+PGh0bWw+Ci...',
        },
        {
          filename: 'wp-content/uploads/image.png',
          mimeType: 'image/png',
          data: 'iVBORw0KGgoAAAANSUhEUgAABAAAAA...',
        },
      ],
      metadata: {
        name: 'LikeCoin Update &#124; Launching $LIKE Airdrop and Civic Likers Web3',
        tags: ['Airdrop', 'Civic Liker', 'Depub', 'LikeCoin', 'Progress Update'],
        author: 'likecoin',
        description: 'Launch of LikeCoin Airdrop The long-awaited 50 million...',
      }
    },
  }
```

| Key                       | Description                              |
| ------------------------- | ---------------------------------------- |
| action                    | SUBMIT\_ISCN\_DATA                       |
| data                      | ISCN Data for submission                 |
| data.files                | Array of files to be uploaded to Arweave |
| data.metadata             | ISCN metadata                            |
| data.metadata.name        | Title for the ISCN content               |
| data.metadata.tags        | Tags for the content                     |
| data.metadata.author      | Name of the author                       |
| data.metadata.description | Description for the content              |

File `data` should be encoded in base64, with proper `mimeType` defined. `filename` can either be the actual filename, or include a directory path as prefix.

If multiple files are to be uploaded, an `index.html` must be included which would be shown as the default page when the files are accessed through Arweave or IPFS.

### Emit event format

#### ISCN\_WIDGET\_READY

Fired when widget is ready to receive message

```
{ 
  action: 'ISCN_WIDGET_READY',
}
```

#### ARWEAVE\_SUBMITTED

Fired when files are uploaded to Arweave and IPFS

```
{ 
  action: 'ARWEAVE_SUBMITTED',
  data: {
    ipfsHash,
    arweaveId,
  }
}
```

#### ISCN\_SUBMITTED

Fired when content is submitted to ISCN

```javascript
{ 
  action: 'ISCN_SUBMITTED',
  data: {
    tx_hash,
    iscnId,
  }
}
```

### Example Code <a href="#example-link" id="example-link"></a>

```javascript
const w = window.open('https://like.co/in/widget/iscn-ar?opener=1&redirect_uri=https%3A%2F%2Flike.community');

const ISCN_WIDGET_ORIGIN = 'https://like.co';

function onPostMessage(event) {
  if (event.origin !== 'like.co') {
    return;
  }
  try {
    const { action, data } = JSON.parse(event.data);
    if (action === 'ISCN_WIDGET_READY') {
      w.postMessage(JSON.stringify({ action: 'INIT_WIDGET' }), ISCN_WIDGET_ORIGIN);
      w.postMessage(sendISCNPayload());
    } else if (action === 'ARWEAVE_SUBMITTED') {
      const {
        ipfsHash, arweaveId,
      } = data;
      console.log(ipfsHash, arweaveId);
    } else if (action === 'ISCN_SUBMITTED') {
      const {
        tx_hash: txHash, iscnId,
      } = data;
      console.log(txHash, iscnId);
    } else {
      console.log(`Unknown event: ${action}`);
    }
  } catch (err) {
    console.error(err);
  }
}
window.addEventListener('message', onPostMessage, false);

function sendISCNPayload() {
  w.postMessage(JSON.stringify({
    action: 'SUBMIT_ISCN_DATA',
    data: {
      files: [
        {
          filename: 'index.html',
          mimeType: 'text/html',
          data: 'PCFET0NUWVBFIGh0bWw+PGh0bWw+Ci...',
        },
        {
          filename: 'wp-content/uploads/image.png',
          mimeType: 'image/png',
          data: 'iVBORw0KGgoAAAANSUhEUgAABAAAAA...',
        },
      ],
      metadata: {
        name: 'LikeCoin Update &#124; Launching $LIKE Airdrop and Civic Likers Web3',
        tags: ['Airdrop', 'Civic Liker', 'Depub', 'LikeCoin', 'Progress Update'],
        author: 'likecoin',
        description: 'Launch of LikeCoin Airdrop The long-awaited 50 million...',
      }
    },

  }), ISCN_WIDGET_ORIGIN);
}

```

[\
](https://docs.like.co/developer/like-pay/web-widget)
