---
description: Using Javascript/node.js to sign a transaction
---

# Javascript

### Encode and Sign Raw Message

The parameters should consist with your account information. The `accountNumber` and `sequence` could be found by querying LCD `/cosmos/auth/v1beta1/accounts/{fromAddress}` endpoint.

```javascript
const secp256k1 = require('secp256k1');
const createHash = require('create-hash');
const Long = require('long');
const { MsgSend } = require("cosmjs-types/cosmos/bank/v1beta1/tx");
const { TxBody, AuthInfo, SignDoc, TxRaw } = require("cosmjs-types/cosmos/tx/v1beta1/tx");
const { PubKey } = require("cosmjs-types/cosmos/crypto/secp256k1/keys");

// define parameters
const chainId = "likechain-local-testnet";
const privateKey = "69b4e47d3aa61ad6184493529cd0feb0d2dfb55ea31aa9799af42607de3cd1a9";
const publicKey = "A4Fj1Y4k77Qaxuy496CHYB2rpfWXkM3LCnlyrU8eKbH7";
const accountNumber = 1;
const fromAddress = "cosmos1lsagfzrm4gz28he4wunt63sts5xzmczw8pkek3";
const toAddress = "cosmos1mnyn7x24xj6vraxeeq56dfkxa009tvhgknhm04";
const tokenAmount = 1000000;
const memo = "Enjoy your money";
const gasLimit = 100000;
const sequence = 10;

const messages = [{
  typeUrl: "/cosmos.bank.v1beta1.MsgSend",
  value: {
    fromAddress,
    toAddress,
    amount: [
      {
        denom: "nanolike",
        amount: tokenAmount.toString(),
      },
    ],
  }
}];

const wrappedMessages = messages.map(msg => {
  return {
    typeUrl: msg.typeUrl,
    value: MsgSend.encode(msg.value).finish(),
  }
})

const body = {
  typeUrl: "/cosmos.tx.v1beta1.TxBody",
  value: {
    memo,
    messages: wrappedMessages,
    timeoutHeight: Long.UZERO,
    extensionOptions: [],
    nonCriticalExtensionOptions: [],
  },
}
const bodyBytes = TxBody.encode(body.value).finish();

const pubkeyBytes = PubKey.encode({ key: publicKey }).finish();

const authInfo = {
  signerInfos: [
    {
      sequence: Long.fromNumber(sequence),
      publicKey: {
        typeUrl: "/cosmos.crypto.secp256k1.PubKey",
        value: pubkeyBytes,
      },
      modeInfo: {
        single: {
          mode: 1,
        },
      },
    },
  ],
  fee: {
    gasLimit: Long.fromNumber(gasLimit),
    payer: "",
    granter: "",
    amount: [
      {
        denom: "nanolike",
        amount: "0",
      },
    ],
  },
}

const authInfoBytes = AuthInfo.encode(authInfo).finish();
const signDoc = {
  bodyBytes,
  authInfoBytes,
  chainId,
  accountNumber: Long.fromNumber(accountNumber),
}
const signBytes = SignDoc.encode(signDoc).finish();

const privkeyBytes = Buffer.from(privateKey, 'hex')

const sign = (msg, privateKey) => {
  const msgSha256 = createHash('sha256');
  msgSha256.update(msg);
  const msgHash = msgSha256.digest();
  const { signature: signatureArr } = secp256k1.ecdsaSign(msgHash, privateKey);
  const signature = Buffer.from(signatureArr)
  return signature;
}
const signatureBytes = sign(signBytes, privkeyBytes);

const tx = {
  bodyBytes,
  authInfoBytes,
  signatures: [signatureBytes],
}

const txBytes = TxRaw.encode(tx).finish();

console.log("Your tx_bytes:");
console.log(txBytes.toString('base64'));
```

### Commit a Transaction

Put the `tx_bytes` from above step in the JSON request body as below, and post the LCD`/cosmos/tx/v1beta1/txs` endpoint.

```text
{
  "tx_bytes": "Your tx bytes here",
  "mode": "BROADCAST_MODE_SYNC"
}
```

For details of the [`POST /txs`](../rpc-api/#post-txs) and other chain RPC API, please refer to the [LikeCoin chain RPC API section](../rpc-api/).

