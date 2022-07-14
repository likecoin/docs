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

| Key           | Description                                                                                                                                     |
| ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| action        | SUBMIT\_ISCN\_DATA                                                                                                                              |
| data          | ISCN Data for submission                                                                                                                        |
| data.files    | Array of files to be uploaded to Arweave, must contain an `index.html` if more than one file. Please refer to the tables below for file formats |
| data.metadata | ISCN metadata. Please refer to the tables below for metadata formats                                                                            |

Supported field for ISCN metadata

<table><thead><tr><th>Metadata keys</th><th data-type="select">Required</th><th>Description</th><th>Sample</th></tr></thead><tbody><tr><td>name</td><td></td><td>Name for the ISCN content</td><td>"Computing recursive function with matrix multiplication"</td></tr><tr><td>description</td><td></td><td>Description for the ISCN content</td><td>"An article on computing recursive function with matrix multiplication."</td></tr><tr><td>tags</td><td></td><td>Tags for the ISCN content</td><td>["matrix", "recursion"]</td></tr><tr><td>author</td><td></td><td>Name of the author</td><td>"Chung Wu"</td></tr><tr><td>authorDescription</td><td></td><td>Description of the author</td><td>"Developer"</td></tr><tr><td>url</td><td></td><td>URL of the content</td><td>​"<a href="https://nnkken.github.io/post/recursive-relation/%22,">https://nnkken.github.io/post/recursive-relation/"</a></td></tr><tr><td>stakeholders</td><td></td><td>Stakeholder list as defined in ISCN specification. If <code>author</code> or <code>publisher</code> is defined, they will be automatically appended into <code>stakeholders</code> by the widget</td><td>{ "rewardProportion": 5, "contributionType": "http://schema.org/citation", "footprint": "https://en.wikipedia.org/wiki/Fibonacci_number", "description": "The blog post referred the matrix form of computing Fibonacci numbers." }</td></tr><tr><td>fingerprints</td><td></td><td>Fingerprint of the content, e.g. SHA hash, IPFS hash and Arweave ID. If <code>files</code> are defined, resulting Arweave ID and IPFS hash will be automatically appended into <code>fingerprints</code></td><td>["hash://sha256/9564b85669d5e96ac969dd0161b8475bbced9e5999c6ec598da718a3045d6f2e"]</td></tr><tr><td>publisher</td><td></td><td>One of <code>matters</code>, <code>depub</code> , an arbitrary string representing ID of a publisher, or a <code>stakeholder</code> object . Publisher object allow platforms to add itself into <code>stakeholders</code> and define <code>rewardProportion</code></td><td>{"entity":{"description":"Matters is a decentralized, cryptocurrency driven content creation and discussion platform.","@id":"https://matters.news/","name":"Matters"},"rewardProportion":0}</td></tr><tr><td>license</td><td></td><td>URL of the license of the ISCN content</td><td>"<a href="https://creativecommons.org/licenses/by-sa/4.0/">https://creativecommons.org/licenses/by-sa/4.0/</a>"</td></tr><tr><td>recordNotes</td><td></td><td>Arbitrary string that will be recorded in ISCN as note</td><td>"This record is created by ISCN widget"</td></tr><tr><td>memo</td><td></td><td>Arbitrary string that will be recorded in the create ISCN Transaction as memo</td><td>"This tx is sent by ISCN widget"</td></tr></tbody></table>

Required fields for `data.files`:

| File Keys | Description                                                               |
| --------- | ------------------------------------------------------------------------- |
| filename  | Name of the file, can be a full path containing directory                 |
| mimetype  | mime type of the file, needed for proper display in IPFS/Arweave gateways |
| data      | Base64 encoded file data                                                  |

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
  if (event.origin !== ISCN_WIDGET_ORIGIN) {
    return;
  }
  try {
    const { action, data } = JSON.parse(event.data);
    if (action === 'ISCN_WIDGET_READY') {
      w.postMessage(JSON.stringify({ action: 'INIT_WIDGET' }), ISCN_WIDGET_ORIGIN);
      sendISCNPayload();
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
          // bytes encoded in base64
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
