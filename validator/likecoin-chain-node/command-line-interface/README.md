# Command line interface

## liked

`liked` is for launching the node and manipulating node related files, e.g. adding accounts into `genesis.json`.

Chain data, consensus key, node key and configuration files will be stored in `.liked` folder, default location is `$HOME/.liked`.

In the init script, we are running `liked` in Docker \(image `likechain_liked`\) and the `.liked` directory is placed in `likechain` root directory. So to run the commands below, you may need:

```text
docker run --rm -it -v `pwd`/.liked:/likechain/.liked likechain_likechain liked --home /likechain/.liked COMMANDS...
```

\(Sometimes you may also need the `.likecli` directory mounted into the container, e.g. `gentx` which uses the keys managed by `likecli` to sign transaction\)

If you already have the `likechain_liked` container running and wants to connect to it, you may need:

```text
docker exec -it likechain_liked liked --home /likechain/.liked COMMANDS...
```

Common usage:

### Initializing chain node

```text
liked init [MONIKER]
```

This will initialize default configuration files, generate consensus key and node key in `.liked` folder.

### Adding genesis account

```text
liked add-genesis-account [ADDRESS] [COINS]
```

This will append the account with the coins in `.liked/config/genesis.json`.

### Generating and signing genesis transaction

```text
liked gentx [OPTIONS]
```

This will generate and sign a genesis transaction for creating validator during genesis.

The parameters are set by options.

The generated transaction with signature will be stored in `.liked/config/gentx/` folder as JSON file.

See `--help` for more details.

### Aggregating genesis transactions

```text
liked collect-gentxs
```

This will collect genesis transactions in JSON files in `.liked/config/gentx/` into `.liked/config/genesis.json`.

### Starting node

```text
liked start
```

This will start the node.

### Reseting chain data

```text
liked unsafe-reset-all
```

This will clear the chain block data, resetting it to the initial state.

The configurations, consensus key, node key and `genesis.json` will remain unchanged.

### Querying Tendermint related info

```text
liked tendermint [SUBCOMMANDS]
```

This command provides subcommands for querying info about Tendermint, e.g. consensus public key and node ID.

See `--help` for more details.

## likecli

`likecli` is for communicating with nodes, e.g. query chain info, send transactions.

It also manages address private keys and starts lite client.

Keys and lite client data will be stored in `.likecli` folder, default location is `$HOME/.likecli`.

In the init script, we are running `likecli` in Docker \(image `likechain/likechain`\) and the `.likecli` directory is placed in `likechain` root directory. So to run the commands below, you may need:

```text
docker run --rm -it -v `pwd`/.likecli:/likechain/.likecli likechain/likechain likecli --home /likechain/.likecli COMMANDS...
```

If you already have the `likechain/liked` container running and wants to connect to it, you may need:

```text
docker exec -it likechain/liked likecli --home /likechain/.likecli COMMANDS...
```

Common usage:

### Key management

```text
likecli keys [SUBCOMMANDS]
```

This command provides subcommands for managing address keys, e.g. adding, removing, exporting, importing keys.

#### List keys available

```text
likecli keys list
```

#### Create a new key

```text
likecli keys add [KEY_NAME]
```

#### Import a recovery phase

```text
likecli keys add --recover [KEY_NAME]
```

See `--help` for more details.

### Querying chain info

```text
likecli query [SUBCOMMANDS]
```

This command aggregates subcommands provided by Cosmos SDK modules for querying chain data.

#### Querying account info

```text
likecli query auth account cosmos1xvymudttgxrypxwy0ujnu5pgd6fq6c079yuf92
```

### Signing and sending transactions

```text
likecli tx [SUBCOMMANDS]
```

This command aggregates subcommands provided by Cosmos SDK modules for generating and signing transactions.

Example: sending 1000 LikeCoins from the `faucet` account managed by `likecli`

```text
likecli tx send faucet cosmos1mw2l98asefxev9s9mvdtm2j5mcap9mn5t3u8lh 1000000000000nanolike \
    --chain-id likechain-testnet-taipei-1 \
    --gas 44000 \
    --gas-prices 1000.0nanolike
```

## Lite client

```text
likecli rest-server
```

This command starts the lite client, which exposes the node APIs as understandable RESTful APIs.



See the [Cosmos SDK RPC doc](https://cosmos.network/rpc/) for more details.

