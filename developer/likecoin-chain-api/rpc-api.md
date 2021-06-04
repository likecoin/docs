# RPC API

## RPC API

Please refer to swagger document for a full list of API

[https://mainnet-node.like.co/swagger-ui/](https://mainnet-node.like.co/swagger-ui/)

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

[https://mainnet-node.like.co/txs/F7AE531BC8CDD70A8C69ADBCD1F77029C11965900F3F0F239627E1DAF2C72A77](https://mainnet-node.like.co/txs/F7AE531BC8CDD70A8C69ADBCD1F77029C11965900F3F0F239627E1DAF2C72A77)

```text
{
  "height": "8606074",
  "txhash": "F7AE531BC8CDD70A8C69ADBCD1F77029C11965900F3F0F239627E1DAF2C72A77",
  "raw_log": "[{\\"msg_index\\":0,\\"success\\":true,\\"log\\":\\"\\",\\"events\\":[{\\"type\\":\\"message\\",\\"attributes\\":[{\\"key\\":\\"sender\\",\\"value\\":\\"cosmos1w4hq98jtjg729ft4um63y7z4l9wdtgrlv9n5y0\\"},{\\"key\\":\\"module\\",\\"value\\":\\"bank\\"},{\\"key\\":\\"action\\",\\"value\\":\\"send\\"}]},{\\"type\\":\\"transfer\\",\\"attributes\\":[{\\"key\\":\\"recipient\\",\\"value\\":\\"cosmos1rtwfrx9cq2ly7l59gy9607pxtp5nnutc3l3x2u\\"},{\\"key\\":\\"amount\\",\\"value\\":\\"9000000000nanolike\\"}]}]},{\\"msg_index\\":1,\\"success\\":true,\\"log\\":\\"\\",\\"events\\":[{\\"type\\":\\"message\\",\\"attributes\\":[{\\"key\\":\\"sender\\",\\"value\\":\\"cosmos1w4hq98jtjg729ft4um63y7z4l9wdtgrlv9n5y0\\"},{\\"key\\":\\"module\\",\\"value\\":\\"bank\\"},{\\"key\\":\\"action\\",\\"value\\":\\"send\\"}]},{\\"type\\":\\"transfer\\",\\"attributes\\":[{\\"key\\":\\"recipient\\",\\"value\\":\\"cosmos1yyrcdn5j5pw2vf8yk2r9u04kk8kltxza6jd0ke\\"},{\\"key\\":\\"amount\\",\\"value\\":\\"3000000000nanolike\\"}]}]}]",
  "logs": [
    {
      "msg_index": 0,
      "success": true,
      "log": "",
      "events": [
        {
          "type": "message",
          "attributes": [
            {
              "key": "sender",
              "value": "cosmos1w4hq98jtjg729ft4um63y7z4l9wdtgrlv9n5y0"
            },
            {
              "key": "module",
              "value": "bank"
            },
            {
              "key": "action",
              "value": "send"
            }
          ]
        },
        {
          "type": "transfer",
          "attributes": [
            {
              "key": "recipient",
              "value": "cosmos1rtwfrx9cq2ly7l59gy9607pxtp5nnutc3l3x2u"
            },
            {
              "key": "amount",
              "value": "9000000000nanolike"
            }
          ]
        }
      ]
    },
    {
      "msg_index": 1,
      "success": true,
      "log": "",
      "events": [
        {
          "type": "message",
          "attributes": [
            {
              "key": "sender",
              "value": "cosmos1w4hq98jtjg729ft4um63y7z4l9wdtgrlv9n5y0"
            },
            {
              "key": "module",
              "value": "bank"
            },
            {
              "key": "action",
              "value": "send"
            }
          ]
        },
        {
          "type": "transfer",
          "attributes": [
            {
              "key": "recipient",
              "value": "cosmos1yyrcdn5j5pw2vf8yk2r9u04kk8kltxza6jd0ke"
            },
            {
              "key": "amount",
              "value": "3000000000nanolike"
            }
          ]
        }
      ]
    }
  ],
  "gas_wanted": "90000",
  "gas_used": "59405",
  "tx": {
    "type": "cosmos-sdk/StdTx",
    "value": {
      "msg": [
        {
          "type": "cosmos-sdk/MsgSend",
          "value": {
            "from_address": "cosmos1w4hq98jtjg729ft4um63y7z4l9wdtgrlv9n5y0",
            "to_address": "cosmos1rtwfrx9cq2ly7l59gy9607pxtp5nnutc3l3x2u",
            "amount": [
              {
                "denom": "nanolike",
                "amount": "9000000000"
              }
            ]
          }
        },
        {
          "type": "cosmos-sdk/MsgSend",
          "value": {
            "from_address": "cosmos1w4hq98jtjg729ft4um63y7z4l9wdtgrlv9n5y0",
            "to_address": "cosmos1yyrcdn5j5pw2vf8yk2r9u04kk8kltxza6jd0ke",
            "amount": [
              {
                "denom": "nanolike",
                "amount": "3000000000"
              }
            ]
          }
        }
      ],
      "fee": {
        "amount": [
          {
            "denom": "nanolike",
            "amount": "9000000"
          }
        ],
        "gas": "90000"
      },
      "signatures": [
        {
          "pub_key": {
            "type": "tendermint/PubKeySecp256k1",
            "value": "Ao6v0S5CPswEb9qqhtrgWo6asFYZtXKmxrBhISk5qfVe"
          },
          "signature": "TtFrJq6shII+a/yUFBUtx06FnhC4bG/BYy7QaoSpra91aiaJAlBgjSJmFGvQwl0rICG/BhxG7V2mHysIkx8QZw=="
        }
      ],
      "memo": "superlike: 2446920329705075"
    }
  },
  "timestamp": "2021-05-27T16:12:22Z",
  "events": [
    {
      "type": "message",
      "attributes": [
        {
          "key": "sender",
          "value": "cosmos1w4hq98jtjg729ft4um63y7z4l9wdtgrlv9n5y0"
        },
        {
          "key": "module",
          "value": "bank"
        },
        {
          "key": "action",
          "value": "send"
        },
        {
          "key": "sender",
          "value": "cosmos1w4hq98jtjg729ft4um63y7z4l9wdtgrlv9n5y0"
        },
        {
          "key": "module",
          "value": "bank"
        },
        {
          "key": "action",
          "value": "send"
        }
      ]
    },
    {
      "type": "transfer",
      "attributes": [
        {
          "key": "recipient",
          "value": "cosmos1rtwfrx9cq2ly7l59gy9607pxtp5nnutc3l3x2u"
        },
        {
          "key": "amount",
          "value": "9000000000nanolike"
        },
        {
          "key": "recipient",
          "value": "cosmos1yyrcdn5j5pw2vf8yk2r9u04kk8kltxza6jd0ke"
        },
        {
          "key": "amount",
          "value": "3000000000nanolike"
        }
      ]
    }
  ]
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

