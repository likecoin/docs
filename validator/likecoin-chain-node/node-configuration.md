# Node configuration

## app.toml

app.toml is a configuration file located in `~/.likerd/config/app.toml` which controls the behaviour of node application logic.

### minimum-gas-prices

Validators are recommend to set a `minimum-gas-prices` to a non zero value,  e.g. 

```text
minimum-gas-prices = "0.01 nanolike" // or "1 nanolike"
```

Transaction that has a gas price lower than the configured value would not be processed by the validator. Forcing a minimum gas price to be set for all transactions helps combatting spam transactions.

For details, please refer to [cosmos documentation](https://docs.cosmos.network/v0.39/modules/auth/01_concepts.html)

## config.toml

config.toml is a configuration file located in `~/.likerd/config/config.toml` which controls node tendermint configurations.

### moniker

Edit your node's moniker\(name\) when appeared in other connected node.

