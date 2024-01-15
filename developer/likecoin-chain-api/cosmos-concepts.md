---
description: Concepts before accessing LikeCoin chain
---

# Cosmos concepts

## Key and Address

A private key is a 32 bytes (256 bits) binary.

The public key is derived from the private key according to secp256k1, in 33-bytes compressed format.

The Cosmos address is derived by the follows: `address = ripemd160(sha256(pubKey))`, encoded by bech32 with `cosmos` as prefix.

See [here](https://gist.github.com/nnkken/90428d73f38d957de1b75ec3992d9342#file-sign-js) for an example in JavaScript.

## Nodes and Endpoints

To use the RPC APIs, we need a a lite client endpoint, which communicates with full nodes and verify the data from full nodes cryptographically (e.g. verifying Merkle proof).

For the FoTan mainnet:

```
Lite client endpoint: https://mainnet-node.like.co
Chain ID: likecoin-mainnet-2
```

Users can also run a full node and a lite client.

To setup a full node, please follow the instruction from this document: [https://github.com/likecoin/likecoin-chain/wiki/Setup-LikeCoin-chain-mainnet-node](https://github.com/likecoin/likecoin-chain/tree/fotan-1#readme)

(TODO: genesis URL and seed node)

Since the FoTan upgraed, the RESTful API is built into the `liked` command. You may modify `.liked/config/app.toml` for enabling the RESTful API if needed.

[Here](https://gist.github.com/nnkken/90428d73f38d957de1b75ec3992d9342#file-docker-compose-yml) is an example Docker Compose config file for running the Taipei network full node and lite client. This hosts an RPC API endpoint on port 1317.\


### Chain ID

Chain ID defines which chain / network you are operating on, to prevent replaying transactions on other networks.

### Account

Each address corresponds to an account, which will have an account number and a sequence number.

#### Account Number

Account number is the account's number.

It is required in transactions, and could be queried from the `/auth/accounts/{address}` API.

#### Sequence

Sequence is the number of transactions the account has sent.

It is required in transactions to prevent transaction replays, similar to the concept of nonce in Ethereum.

It could be queried from the `/auth/accounts/{address}` API.

### Coins

In Cosmos SDK, coins are represented as an object with 2 fields: `amount` and `denom`.

`amount` is the number of coins, while `denom` is the identifier of the coins.

In LikeCoin Chain, we only have one `denom`, which is `nanolike`. `1 LikeCoin = 1000000000nanolike`.

When used in short forms (e.g. CLI parameters), the format of coins is `${amount}${denom}`, e.g. `1000000000nanolike`.

### Gas and Fees

In Cosmos SDK, there is a concept called `gas`, which is similar to the concept of `gas` in Ethereum.

Each transaction must specify the maximum amount of gas it may consume.

If the transaction consumed more gas than provided during execution, it will fail.

Different from Ethereum, transactions specify their transaction fee directly, instead of specifying the gas price.

Nodes calculates the gas price by `gas_price = fee / gas`, and may reject transactions with gas price lower than their expectation.

We currently recommend validators to set the gas price to `10000.0nanolike` as per proposal 74. For a typical coin sending transaction, it consumes about 44000 gas, which means the transaction fee is 0.044 LikeCoin.

Since the fee is specified in the transaction, it will not be refunded even if the actual gas consumption is less than the provided one.

### Signature

The signing process is the standard secp256k1 signing.

The output bytes are organized in 64 bytes, which are the `r` and `s` values, 256 bites each, concatenated.

The signature is represented as object in transactions, which includes the public key and the signature bytes.

Example:

```
    {
        "signature": "yXcQvLVEHZMIzZijEgmcL5S7orusBURZoRjWuG1IpoItt5DhY8P9TUaxx31huxV200l6GcEbUlB/Y7jONuf3Bw==",
        "account_number": "21",
        "sequence": "0",
        "pub_key": {
            "type": "tendermint/PubKeySecp256k1",
            "value": "A0ZGrlBHMWtCMNAIbIrOxofwCxzZ0dxjT2yzWKwKmo//"
        }
    }
```

#### Sign Bytes

The sign bytes are the input to the secp256k1 signing algorithm.

Sign bytes are obtained by the following process:

1. construct a standard transaction as follows:

```
{
  "fee": {
    "amount": [
      {
        "denom": "nanolike",
        "amount": "44000000"
      }
    ],
    "gas": "44000"
  },
  "msgs": [msgs...],
  "chain_id": "likechain-testnet-taipei-1",
  "account_number": "21",
  "sequence": "0",
  "memo": "",
}
```

Where `msgs` are the `msg` objects of the transactions. For a typical `Send` transaction, it will look like this:

```
{
  "fee": {
    "amount": [
      {
        "denom": "nanolike",
        "amount": "44000000"
      }
    ],
    "gas": "44000"
  },
  "msgs": [
    {
      "type": "cosmos-sdk/MsgSend",
      "value": {
        "from_address": "cosmos1mnyn7x24xj6vraxeeq56dfkxa009tvhgknhm04",
        "to_address": "cosmos1ca0zlqxjqv5gek5qxm602umtkmu88564hpyws4",
        "amount": [
          {
            "denom": "nanolike",
            "amount": "123456789"
          }
        ]
      }
    }
  ],
  "chain_id": "likechain-testnet-taipei-1",
  "account_number": "21",
  "sequence": "0",
  "memo": "",
}
```

Note that all numbers (e.g. `amount`, `sequence`, `account_number`) are encoded as `string` in the sign bytes.

1. remove all fields with `null` value.
2. reorganize the JSON message to remove all indents and newline formattings, and sort the fields by alphanumeric order.

The sign bytes of the example above after processing will look like this:

```
{"account_number":"21","chain_id":"likechain-testnet-taipei-1","fee":{"amount":[{"amount":"44000000","denom":"nanolike"}],"gas":"44000"},"memo":"","msgs":[{"type":"cosmos-sdk/MsgSend","value":{"amount":[{"amount":"123456789","denom":"nanolike"}],"from_address":"cosmos1mnyn7x24xj6vraxeeq56dfkxa009tvhgknhm04","to_address":"cosmos1ca0zlqxjqv5gek5qxm602umtkmu88564hpyws4"}}],"sequence":"0"}
```

##
