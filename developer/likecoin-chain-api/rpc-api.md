# RPC API

## RPC API

### GET /auth/accounts/{address}

\(TODO\)

Returns the information about the account.

Some commonly used fields:

`response.result.value.coins` \(`[{amount: string, denom: string}]`\): the balance of the account. `response.result.value.account_number` \(`string`\): the account number, which is needed when signing transactions. `response.result.value.sequence` \(`string`\): the sequence for replay protection, which is needed when signing transactions.

Example: [http://34.66.207.129:1317/auth/accounts/cosmos1mnyn7x24xj6vraxeeq56dfkxa009tvhgknhm04](http://34.66.207.129:1317/auth/accounts/cosmos1mnyn7x24xj6vraxeeq56dfkxa009tvhgknhm04)

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

\(TODO\)

Fetch the transaction information.

A transaction may contain multiple messages, and if any of them failed during execution, the whole transaction fails without any state change, i.e. previous messages will be rollbacked.

User can check if the whole transaction succeeded by checking if the last object in `response.logs` shows `success: true` or not.

Example: [http://34.66.207.129:1317/txs/4F5DC521E5A37F1EBB08B36DDA64A1051352C3F9070D6D969ADE28CA6F33B5C2](http://34.66.207.129:1317/txs/4F5DC521E5A37F1EBB08B36DDA64A1051352C3F9070D6D969ADE28CA6F33B5C2)

```text
{
  "height":"574778",
  "txhash":"4F5DC521E5A37F1EBB08B36DDA64A1051352C3F9070D6D969ADE28CA6F33B5C2",
  "raw_log":"[{\"msg_index\":0,\"success\":true,\"log\":\"\"}]",
  "logs":[
    {
      "msg_index":0,
      "success":true,
      "log":""
    }
  ],
  "gas_wanted":"44000",
  "gas_used":"43053",
  "events":[
    {
      "type":"message",
      "attributes":[
        {
          "key":"action",
          "value":"send"
        },
        {
          "key":"sender",
          "value":"cosmos1ca0zlqxjqv5gek5qxm602umtkmu88564hpyws4"
        },
        {
          "key":"module",
          "value":"bank"
        }
      ]
    },
    {
      "type":"transfer",
      "attributes":[
        {
          "key":"recipient",
          "value":"cosmos1mnyn7x24xj6vraxeeq56dfkxa009tvhgknhm04"
        },
        {
          "key":"amount",
          "value":"10000000000nanolike"
        }
      ]
    }
  ],
  "tx":{
    "type":"cosmos-sdk/StdTx",
    "value":{
      "msg":[
        {
          "type":"cosmos-sdk/MsgSend",
          "value":{
            "from_address":"cosmos1ca0zlqxjqv5gek5qxm602umtkmu88564hpyws4",
            "to_address":"cosmos1mnyn7x24xj6vraxeeq56dfkxa009tvhgknhm04",
            "amount":[
              {
                "denom":"nanolike",
                "amount":"10000000000"
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
      "signatures":[
        {
          "pub_key":{
            "type":"tendermint/PubKeySecp256k1",
            "value":"AwqajsW8qgrN0evcrRzz893GeGt4wl2ALbqXbaoGoYiB"
          },
          "signature":"E18vj9ENpYtXD35CgbEtdFXMiMQPF/+MvoEJ7dBIuJ05trQJGDihJhki5ctne9TuW1tl4oafRED37sXwslR7Fg=="
        }
      ],
      "memo":""
    }
  },
  "timestamp":"2019-10-16T07:40:27Z"
}
```

### POST /txs

\(TODO\)

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

