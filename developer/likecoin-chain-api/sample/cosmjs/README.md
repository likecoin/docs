# CosmJS \(Recommended\)

Use [https://github.com/cosmos/cosmjs](https://github.com/cosmos/cosmjs) to simplify coding.

```javascript
import { DirectSecp256k1HdWallet } from "@cosmjs/proto-signing";
import { assertIsBroadcastTxSuccess, SigningStargateClient, StargateClient } from "@cosmjs/stargate";

const mnemonic = "surround miss nominee dream gap cross assault thank captain prosper drop duty group candy wealth weather scale put";
const wallet = await DirectSecp256k1HdWallet.fromMnemonic(mnemonic);
const [firstAccount] = await wallet.getAccounts();

const rpcEndpoint = "https://mainnet-node.like.co/rpc/";
const client = await SigningStargateClient.connectWithSigner(rpcEndpoint, wallet);

const recipient = "cosmos1xv9tklw7d82sezh9haa573wufgy59vmwe6xxe5";
const amount = {
  denom: "nanolike",
  amount: "1234567",
};
const result = await client.sendTokens(firstAccount.address, recipient, [amount], "LIKE as rewards");
assertIsBroadcastTxSuccess(result);
```

