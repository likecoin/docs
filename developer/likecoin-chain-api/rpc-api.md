# RPC API

## RPC API

Since LikeCoin chain is based on Cosmos SDK, you may refer to the Cosmos SDK documents for most of the API:

[https://v1.cosmos.network/rpc/v0.42.6](https://v1.cosmos.network/rpc/v0.42.6)

### GET /auth/accounts/{address}

Returns the information about the account.

Some commonly used fields:

`response.result.value.coins` \(`[{amount: string, denom: string}]`\): the balance of the account. `response.result.value.account_number` \(`string`\): the account number, which is needed when signing transactions. `response.result.value.sequence` \(`string`\): the sequence for replay protection, which is needed when signing transactions.

Example: 

[https://mainnet-node.like.co/auth/accounts/cosmos1mnyn7x24xj6vraxeeq56dfkxa009tvhgknhm04](https://mainnet-node.like.co/auth/accounts/cosmos1mnyn7x24xj6vraxeeq56dfkxa009tvhgknhm04)

```text
{
  "height": "574791",
  "result": {
    "type": "cosmos-sdk/Account",
    "value": {
      "address": "cosmos1mnyn7x24xj6vraxeeq56dfkxa009tvhgknhm04",
      "coins": [
        {
          "denom": "nanolike",
          "amount": "10000000000"
        }
      ],
      "public_key": null,
      "account_number": "21",
      "sequence": "0"
    }
  }
}
```

### GET /txs/{hash}

Fetch the transaction information.

A transaction may contain multiple messages, and if any of them failed during execution, the whole transaction fails without any state change, i.e. previous messages will be rollbacked.

User can check if the whole transaction succeeded by checking if the last object in `response.logs` shows `success: true` or not.

Example: 

[https://mainnet-node.like.co/txs/F7AE531BC8CDD70A8C69ADBCD1F77029C11965900F3F0F239627E1DAF2C72A77](https://mainnet-node.like.co/txs/0311566B20DDE13FD8323513E94366EFD379812EA3A7283065398BE212399B60)

```text
{
  "height": "6455",
  "txhash": "0311566B20DDE13FD8323513E94366EFD379812EA3A7283065398BE212399B60",
  "data": "0A060A0473656E64",
  "raw_log": "[{\"events\":[{\"type\":\"message\",\"attributes\":[{\"key\":\"action\",\"value\":\"send\"},{\"key\":\"sender\",\"value\":\"cosmos1ww3qews2y5jxe8apw2zt8stqqrcu2tptejfwaf\"},{\"key\":\"module\",\"value\":\"bank\"}]},{\"type\":\"transfer\",\"attributes\":[{\"key\":\"recipient\",\"value\":\"cosmos1ecrze4q94n7je5jyeueeym73t47px8ev0xfjtj\"},{\"key\":\"sender\",\"value\":\"cosmos1ww3qews2y5jxe8apw2zt8stqqrcu2tptejfwaf\"},{\"key\":\"amount\",\"value\":\"1nanolike\"}]}]}]",
  "logs": [
    {
      "events": [
        {
          "type": "message",
          "attributes": [
            {
              "key": "action",
              "value": "send"
            },
            {
              "key": "sender",
              "value": "cosmos1ww3qews2y5jxe8apw2zt8stqqrcu2tptejfwaf"
            },
            {
              "key": "module",
              "value": "bank"
            }
          ]
        },
        {
          "type": "transfer",
          "attributes": [
            {
              "key": "recipient",
              "value": "cosmos1ecrze4q94n7je5jyeueeym73t47px8ev0xfjtj"
            },
            {
              "key": "sender",
              "value": "cosmos1ww3qews2y5jxe8apw2zt8stqqrcu2tptejfwaf"
            },
            {
              "key": "amount",
              "value": "1nanolike"
            }
          ]
        }
      ]
    }
  ],
  "gas_wanted": "200000",
  "gas_used": "64621",
  "tx": {
    "type": "cosmos-sdk/StdTx",
    "value": {
      "msg": [
        {
          "type": "cosmos-sdk/MsgSend",
          "value": {
            "from_address": "cosmos1ww3qews2y5jxe8apw2zt8stqqrcu2tptejfwaf",
            "to_address": "cosmos1ecrze4q94n7je5jyeueeym73t47px8ev0xfjtj",
            "amount": [
              {
                "denom": "nanolike",
                "amount": "1"
              }
            ]
          }
        }
      ],
      "fee": {
        "amount": [],
        "gas": "200000"
      },
      "signatures": [],
      "memo": "",
      "timeout_height": "0"
    }
  },
  "timestamp": "2021-08-19T02:57:22Z"
}

```

### POST /txs

Sends a signed transaction.

Example request body:

```text
{
  "mode":"sync",
  "tx":{
    "msg":[
      {
        "type":"cosmos-sdk/MsgSend",
        "value":{
          "from_address":"cosmos1mnyn7x24xj6vraxeeq56dfkxa009tvhgknhm04",
          "to_address":"cosmos1ca0zlqxjqv5gek5qxm602umtkmu88564hpyws4",
          "amount":[
            {
              "denom":"nanolike",
              "amount":"123456789"
            }
          ]
        }
      }
    ],
    "fee":{
      "amount":[
        {
          "denom":"nanolike",
          "amount":"44000000"
        }
      ],
      "gas":"44000"
    },
    "memo":"",
    "signatures":[
      {
        "signature":"yXcQvLVEHZMIzZijEgmcL5S7orusBURZoRjWuG1IpoItt5DhY8P9TUaxx31huxV200l6GcEbUlB/Y7jONuf3Bw==",
        "account_number":"21",
        "sequence":"0",
        "pub_key":{
          "type":"tendermint/PubKeySecp256k1",
          "value":"A0ZGrlBHMWtCMNAIbIrOxofwCxzZ0dxjT2yzWKwKmo//"
        }
      }
    ]
  }
}
```

Response:

```text
{
  "height":"0",
  "logs":[
    {
      "log":"",
      "msg_index":0,
      "success":true
    }
  ],
  "raw_log":"[{\"msg_index\":0,\"success\":true,\"log\":\"\"}]",
  "txhash":"8C3A38A9F340050C459DCD9C3F52396E7C76FC286BA879C791C233580F7A64F0"
}
```

