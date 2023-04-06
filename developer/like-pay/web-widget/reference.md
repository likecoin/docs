---
description: LIKE pay web widget API Reference
---

# Reference

## Introduction

While this feature is being used in production by our partners, many of the configurations needed are not made public accessible yet.Do contact us if you are interested.

## Formatting the widget URL

### Base URL

Testnet: [`https://testnet.like.co/in/widget/pay`](https://testnet.like.co/in/widget/pay)\
Production: [`https://like.co/in/widget/pay`](https://like.co/in/widget/pay)

### &#x20;Input Params

| Query String  | Description                                                                                    |
| ------------- | ---------------------------------------------------------------------------------------------- |
| to            | Target Liker ID                                                                                |
| amount        | amount of LIKE token to be given to target Liker ID                                            |
| via           | (optional) Liker ID of agent/platform                                                          |
| fee           | (optional) extra LIKE token paid to agent/platform as fee                                      |
| remarks       | (optional) public remarks to be written onto LikeCoin chain                                    |
| state         | (optional) local state to be passed back after payment success, used for data/security purpose |
| redirect\_uri | (optional) redirect user to uri after payment success/failed                                   |
| blocking      | (optional) default false, wait until payment is confirmed before redirecting                   |

### Output Params

| Query String | Description                                                                             |
| ------------ | --------------------------------------------------------------------------------------- |
| tx\_hash     | transaction hash of resulting payment, verify status using transaction status query API |
| state        | locale state that was passed as input, used for data/security purpose                   |
| error        | set if any catchable error occur                                                        |
| success      | only if `blocking` is set, return true if transaction success                           |
| remarks      | remarks passed as input params                                                          |

### Transaction query API

Cosmos LCD: `https://api.like.co/cosmos/lcd/txs/${txHash}`

like.co API: `https://api.like.co/tx/id/${txHash}`

### Example Link

Following links are in testnet.

#### Input Link: [`https://testnet.like.co/in/widget/pay?to=ckxpress&amount=1&via=kiutest0&fee=1&state=123&redirect_uri=http%3A%2F%2Flocalhost%3A3000`](https://testnet.like.co/in/widget/pay?to=ckxpress\&amount=1\&via=kiutest0\&fee=1\&state=123\&redirect\_uri=http%3A%2F%2Flocalhost%3A3000)

#### Redirect result:

#### [`http://localhost:3000/?tx_hash=08913DDC16F5F130B9ABCF96C54B22C7AEFEBB303DFD3CDA034171D8950F68C6&state=123&remarks=LIKE%20pay%20via%20kiutest0`](http://localhost:3000/?tx\_hash=08913DDC16F5F130B9ABCF96C54B22C7AEFEBB303DFD3CDA034171D8950F68C6\&state=123\&remarks=LIKE%20pay%20via%20kiutest0)

#### Tx Status Query

[**`https://api.testnet.like.co/cosmos/lcd/txs/08913DDC16F5F130B9ABCF96C54B22C7AEFEBB303DFD3CDA034171D8950F68C`**](https://api.testnet.like.co/cosmos/lcd/txs/08913DDC16F5F130B9ABCF96C54B22C7AEFEBB303DFD3CDA034171D8950F68C)

#### [**`https://api.testnet.like.co/tx/id/08913DDC16F5F130B9ABCF96C54B22C7AEFEBB303DFD3CDA034171D8950F68C6`**](https://api.testnet.like.co/tx/id/08913DDC16F5F130B9ABCF96C54B22C7AEFEBB303DFD3CDA034171D8950F68C6)
