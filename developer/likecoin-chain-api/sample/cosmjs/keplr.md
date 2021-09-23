# Keplr

For [Keplr](https://wallet.keplr.app/), we would need to use [suggestChain API.](https://docs.keplr.app/api/suggest-chain.html)

Chain configuration object needed can found in [https://github.com/likecoin/mainnet/](https://github.com/likecoin/mainnet/) or [https://github.com/likecoin/testnets/](https://github.com/likecoin/testnets/)

```javascript
await window.keplr.experimentalSuggestChain(config);
await window.keplr.enable('likecoin-mainnet-2');
const signer = window.getOfflineSigner('likecoin-mainnet-2');
const [firstAccount] = await signer.getAccounts();


const rpcEndpoint = "https://mainnet-node.like.co/rpc/";
const client = await SigningStargateClient.connectWithSigner(rpcEndpoint, signer);

const recipient = "cosmos1xv9tklw7d82sezh9haa573wufgy59vmwe6xxe5";
const amount = {
  denom: "nanolike",
  amount: "1234567",
};
const result = await client.sendTokens(firstAccount.address, recipient, [amount], "LIKE as rewards");
assertIsBroadcastTxSuccess(result);
```

