---
description: Webhook notification for LIKE pay agent (`via`)
---

# Webhook

### Setup:

Please contact us for setting up the webhook for your agent account. You must set the parameter `via` when using LIKE pay to be able to receive notification

### Specification:

#### Transaction Information \(tx\):

| Key | Description |
| :--- | :--- |
| from | Sender cosmos wallet |
| fromId | Sender Liker ID |
| to | Receiver cosmos wallet |
| toId | Receiver Liker ID |
| ts | Originating timestamp |
| completeTs | Transaction complete timestamp |
| txHash | Transaction hash |
| remarks | Transaction remarks/memo |
| status | Transaction status, possible values: pending/success/fail/timeout |
| type | Transaction type |
| amount | Transfer amount |

#### Transaction Metadata\(metadata\):

| Key | Description |
| :--- | :--- |
| likePay | Parameters entered when using LIKE pay widget |
| toIds | Receiver Liker IDs |
| amounts | Receiver LIKE amounts in string |
| agentID | The \`via\` parameter Liker ID |
| agentFee | Agent fee if set |
| redirectUri | Redirect URI if set |
| remarks | LIKE pay transaction remarks |
| blocking | if `blocking` flag was set |
| state | `state` parameters if set |

### Example event:

```text
{
  "tx": {
    "from": "cosmos1wfu97hwfv5ukc0xjyutajq9e6w5xkcdprlmyhj",
    "ts": 1611659587189,
    "to": "cosmos1rcgfvhgvc6r066w9gzvkt74qx5uk9zj8yr6yf3",
    "amount": {
      "amount": "1000000000",
      "denom": "nanolike"
    },
    "completeTs": 1611659583719,
    "txHash": "30A19D04DEFFF62BC3BC268EE3E391C691231EBA87ADC032A2D99D56AC401959",
    "toId": "ckxpress",
    "fromId": "williamchong-du",
    "remarks": "LIKE pay via developer",
    "status": "success",
    "type": "cosmosTransfer"
  },
  "metadata": {
    "likePay": {
      "agentId": "developer",
      "amounts": [
        "1"
      ],
      "remarks": "LIKE pay via developer",
      "agentFee": "0",
      "toIds": [
        "ckxpress"
      ]
    }
  }
}
```

