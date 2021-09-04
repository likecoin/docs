---
description: Provides javascript/typescript protobuf message definition for ISCN message.
---

# iscn-message-types

## Repositories

Github repo: [https://github.com/likecoin/iscn-message-types](https://github.com/likecoin/iscn-message-types)  
npm: [https://www.npmjs.com/package/@likecoin/iscn-message-types](https://www.npmjs.com/package/@likecoin/iscn-message-types)

## Sample usage:

```text
import { MsgCreateIscnRecord } from '@likecoin/iscn-message-types/dist/iscn/tx';

const registry = new Registry([
  ...defaultRegistryTypes,
  ['/likechain.iscn.MsgCreateIscnRecord', MsgCreateIscnRecord],
]);

const client = await SigningStargateClient.connectWithSigner(
  RPC_URL,
  signer,
  { registry }
);

...

const message = {
  typeUrl: '/likechain.iscn.MsgCreateIscnRecord',
  value: {
    from: address,
    record,
  },
};

...

const response = await client.signAndBroadcast(address, [message], fee, '');
assertIsBroadcastTxSuccess(response);
```

