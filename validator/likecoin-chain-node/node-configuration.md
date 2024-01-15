# Node configuration

Note that most of the configurations could be overridden by environment variables or command line arguments when starting the node.

## app.toml

app.toml is a configuration file located in `~/.liked/config/app.toml` which controls the behaviour of node application logic.

### minimum-gas-prices

The minimum price per gas which your node will accept a transaction. The amount part should be in decimal format, e.g. `1000.0nanolike`, otherwise the node will fail to start. Note that if there is another node proposed a block including a transaction with gas price lower than this value, this node will still process the transaction. An ordinary LikeCoin transfer transaction takes about 80000 gas.

Validators are recommend to set a `minimum-gas-prices` to a non zero value,  e.g.&#x20;

```
minimum-gas-prices = "10000.0nanolike"
```

Transaction that has a gas price lower than the configured value would not be processed by the validator. Forcing a minimum gas price to be set for all transactions helps combatting spam transactions.

For details, please refer to [cosmos documentation](https://docs.cosmos.network/v0.39/modules/auth/01\_concepts.html)

### RESTful API

Under the `[api]` section are the config for the RESTful API. Basically, if you need to enable the RESTful API, you may set `enable = true` under this section, and open the `1317` port (or any other ports you configure by the `address` option in this section) in the Docker config (or any other configs  according to your setup).

### gRPC API

Similar to the RESTful API, the gRPC API is controlled under the `[grpc]` section. It is enabled by default, so you may just need to setup in Docker config.

### State Sync

Under the `[state-sync]` section is the state sync functionality configs.

State sync is for other nodes to synchronize by state snapshots without downloading the blocks one by one.

It is disabled by default. To enable this option, set `snapshot-interval` to a multiple of 500 (or other value according to the `pruning-keep-every` config).

## config.toml

config.toml is a configuration file located in `.liked/config/config.toml` which controls node tendermint configurations.

See [Tendermint docs](https://tendermint.com/docs/tendermint-core/configuration.html) for the detailed lists.

### moniker

Edit your node's moniker(name) when appeared in other connected node.

### rpc.laddr

HTTP RPC endpoint for querying node infos, default is only for localhost.

### p2p.laddr

Endpoint which other P2P nodes can connect with this node.

### p2p.external\_address

External IP address which this node claims to others. If this field is not set, Tendermint will use `p2p.laddr` address (which usually doesn't work, see [issues and workarounds](https://github.com/likecoin/likecoin-chain/wiki/LikeCoin-Chain-Validator-101-\(Technical-Part\)#ip-address-exchange) below).

### p2p.seeds

Bootstrap nodes which this node will connect to and obtain addresses from for more peers.

### p2p.persistent\_peers

&#x20;This node will connect to these nodes persistently.

### p2p.private\_peer\_ids

These nodes' addresses will not be exchanged with others. Can be used to hide the validator signing node's address. See [Sentry Node Architecture](https://github.com/likecoin/likecoin-chain/wiki/LikeCoin-Chain-Validator-101-\(Technical-Part\)#sentry-node-architecture) below.

### consensus.timeout\_commit

This value controls the blocktime.
