# Command line interface

## liked

`liked` is for launching the node and manipulating node related files, e.g. adding accounts into `genesis.json`.

Chain data, consensus key, node key and configuration files will be stored in `.liked` folder, default location is `$HOME/.liked`.

Common usage:

### Initializing chain node

```
liked init [MONIKER]
```

This will initialize default configuration files, generate consensus key and node key in `.liked` folder.

### Adding genesis account

```
liked add-genesis-account [ADDRESS] [COINS]
```

This will append the account with the coins in `.liked/config/genesis.json`.

### Generating and signing genesis transaction

```
liked gentx [OPTIONS]
```

This will generate and sign a genesis transaction for creating validator during genesis.

The parameters are set by options.

The generated transaction with signature will be stored in `.liked/config/gentx/` folder as JSON file.

See `--help` for more details.

### Aggregating genesis transactions

```
liked collect-gentxs
```

This will collect genesis transactions in JSON files in `.liked/config/gentx/` into `.liked/config/genesis.json`.

### Starting node

```
liked start
```

This will start the node.

### Reseting chain data

```
liked unsafe-reset-all
```

This will clear the chain block data, resetting it to the initial state.

The configurations, consensus key, node key and `genesis.json` will remain unchanged.

### Querying Tendermint related info

```
liked tendermint [SUBCOMMANDS]
```

This command provides subcommands for querying info about Tendermint, e.g. consensus public key and node ID.

See `--help` for more details.

### Key management

```
liked keys [SUBCOMMANDS]
```

This command provides subcommands for managing address keys, e.g. adding, removing, exporting, importing keys.

#### List keys available

```
liked keys list
```

#### Create a new key

```
liked keys add [KEY_NAME]
```

#### Import a recovery phase

```
liked keys add --recover [KEY_NAME]
```

See `--help` for more details.

### Querying chain info

```
liked query [SUBCOMMANDS]
```

This command aggregates subcommands provided by Cosmos SDK modules for querying chain data.

#### Querying account info

```
liked query auth account cosmos1xvymudttgxrypxwy0ujnu5pgd6fq6c079yuf92
```

### Signing and sending transactions

```
liked tx [SUBCOMMANDS]
```

This command aggregates subcommands provided by Cosmos SDK modules for generating and signing transactions.

Example: sending 1000 LIKE from the `faucet` account managed by `liked`

```
likecli tx bank send faucet cosmos1mw2l98asefxev9s9mvdtm2j5mcap9mn5t3u8lh 1000000000000nanolike \
    --chain-id likecoin-public-testnet-3 \
    --gas 100000 \
    --gas-prices 100.0nanolike
```

## likecli

In the old SheungWan software, commands are split into two executables: `liked` for server and `likecli` for client.

However, since the FoTan upgrade, two commands are now combined, so `likecli` is deprecated.

If you have keys managed by `likecli`, you can migrate those keys by `liked keys migrate`.

For the RESTful API, it is also built into `liked`, you may enable the APIs from `.liked/config/app.toml` and open the corresponding ports.
