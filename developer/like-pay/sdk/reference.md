---
description: 'LIKE pay SDK Reference, version 0.0.1'
---

# Reference

## Methods

### createPaymentQRCode\(selector, likerId, amount, options\)

Creates a unique one time use QR Code for LIKE payment. Default resolves when the transaction was paid and completed, returns an object containing tx id and tx information \(see options\).

| Params | Description |
| :--- | :--- |
| selector | DOM selector of QR code |
| likerId | Liker ID of the receiving party |
| amount | Amount of LIKE to be received |
| options | Extra options object \(optional\) |

| Options | Description |
| :--- | :--- |
| blocking | Resolve promise only when transaction is complete. Default to true. Resolve after QR code is created, with an object containing pending tx id if set to false.  |

### pollForTxComplete\({ id }, options\)

Poll for a tx to be complete. Resolves with tx information after the tx is completed.

| Params | Description |
| :--- | :--- |
| id | Tx id of target  |

| Options | Description |
| :--- | :--- |
| waitForSuccess | Default to true. If set to fals, the function will return if the tx is found even if in pending state. |

### getTx\(txId\)

Get information of a tx by its id.

| Params | Description |
| :--- | :--- |
| txId | Tx id of target  |

