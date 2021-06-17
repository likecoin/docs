# Validator Technical Introduction

This document includes some technical information which LikeCoin Chain validators should know.

* [Overview](https://github.com/likecoin/likecoin-chain/wiki/LikeCoin-Chain-Validator-101-%28Technical-Part%29#overview)
  * [Tendermint](https://github.com/likecoin/likecoin-chain/wiki/LikeCoin-Chain-Validator-101-%28Technical-Part%29#tendermint)
  * [Cosmos SDK Application](https://github.com/likecoin/likecoin-chain/wiki/LikeCoin-Chain-Validator-101-%28Technical-Part%29#cosmos-sdk-application)
* [Command Line Interface](https://github.com/likecoin/likecoin-chain/wiki/LikeCoin-Chain-Validator-101-%28Technical-Part%29#command-line-interface)
  * [liked](https://github.com/likecoin/likecoin-chain/wiki/LikeCoin-Chain-Validator-101-%28Technical-Part%29#liked)
  * [likecli](https://github.com/likecoin/likecoin-chain/wiki/LikeCoin-Chain-Validator-101-%28Technical-Part%29#likecli)
* [Configurations](https://github.com/likecoin/likecoin-chain/wiki/LikeCoin-Chain-Validator-101-%28Technical-Part%29#configurations)
  * [Tendermint](https://github.com/likecoin/likecoin-chain/wiki/LikeCoin-Chain-Validator-101-%28Technical-Part%29#tendermint-1)
  * [Cosmos SDK](https://github.com/likecoin/likecoin-chain/wiki/LikeCoin-Chain-Validator-101-%28Technical-Part%29#cosmos-sdk)
* [Deployment](https://github.com/likecoin/likecoin-chain/wiki/LikeCoin-Chain-Validator-101-%28Technical-Part%29#deployment)
  * [Basic Launching Flow](https://github.com/likecoin/likecoin-chain/wiki/LikeCoin-Chain-Validator-101-%28Technical-Part%29#basic-launching-flow)
  * [Availability](https://github.com/likecoin/likecoin-chain/wiki/LikeCoin-Chain-Validator-101-%28Technical-Part%29#availability)
  * [Key Management](https://github.com/likecoin/likecoin-chain/wiki/LikeCoin-Chain-Validator-101-%28Technical-Part%29#key-management)
* [Transactions](https://github.com/likecoin/likecoin-chain/wiki/LikeCoin-Chain-Validator-101-%28Technical-Part%29#transactions)
  * [Transaction Structure](https://github.com/likecoin/likecoin-chain/wiki/LikeCoin-Chain-Validator-101-%28Technical-Part%29#transaction-structure)
  * [Transaction Execution Flow](https://github.com/likecoin/likecoin-chain/wiki/LikeCoin-Chain-Validator-101-%28Technical-Part%29#transaction-execution-flow)
* [Common Modules, Transactions and Queries](https://github.com/likecoin/likecoin-chain/wiki/LikeCoin-Chain-Validator-101-%28Technical-Part%29#common-modules-transactions-and-queries)
  * [Auth](https://github.com/likecoin/likecoin-chain/wiki/LikeCoin-Chain-Validator-101-%28Technical-Part%29#auth)
  * [Bank](https://github.com/likecoin/likecoin-chain/wiki/LikeCoin-Chain-Validator-101-%28Technical-Part%29#bank)
  * [Staking related modules](https://github.com/likecoin/likecoin-chain/wiki/LikeCoin-Chain-Validator-101-%28Technical-Part%29#staking-related-modules)
  * [Governance](https://github.com/likecoin/likecoin-chain/wiki/LikeCoin-Chain-Validator-101-%28Technical-Part%29#governance)
* [Known Issues and Workarounds](https://github.com/likecoin/likecoin-chain/wiki/LikeCoin-Chain-Validator-101-%28Technical-Part%29#known-issues-and-workarounds)
  * [IP Address Exchange](https://github.com/likecoin/likecoin-chain/wiki/LikeCoin-Chain-Validator-101-%28Technical-Part%29#ip-address-exchange)
  * [Empty Blocks](https://github.com/likecoin/likecoin-chain/wiki/LikeCoin-Chain-Validator-101-%28Technical-Part%29#empty-blocks)

## Overview

LikeCoin Chain is developed base on Cosmos SDK. When started, the software will launch 2 components: Tendermint, which communicates with other nodes and process blockchain / consensus related stuffs; Cosmos SDK application, which receives transactions from Tendermint and process them according to the application logic.

### Tendermint

Tendermint is a consensus engine, which helps developers to develop their own blockchain by separating the blockchain specific parts \(consensus, block processing, P2P networking, etc\) and the application logic.

Developers only need to implement their application logic according to an interface called `Application BlockChain Interface (ABCI)`, then Tendermint will take care the blockchain parts.

With Tendermint alone, the chain will be a consortium chain, which means that only predefined set of key holders can propose and validate blocks.

However, Tendermint provides mechanisms for the application logic to determine who can be the validators, making it possible to select validators from a large pool of participants and thus turning into a public chain.

### Cosmos SDK Application

Cosmos SDK is an SDK which helps developers to developer their ABCI app by providing standard modules of common blockchain features, e.g. coin transfer.

It also provides Proof of Stake related module, which makes the chain a public blockchain by selecting validators according to the amount of coins they staked.

## Command Line Interface

### liked

`liked` is for launching the node and manipulating node related files, e.g. adding accounts into `genesis.json`.

Chain data, consensus key, node key and configuration files will be stored in `.liked` folder, default location is `$HOME/.liked`.

In the init script, we are running `liked` in Docker \(image `likechain/likechain`\) and the `.liked` directory is placed in `likechain` root directory. So to run the commands below, you may need:

``docker run --rm -it -v `pwd`/.liked:/likechain/.liked likechain/likechain liked --home /likechain/.liked COMMANDS...``

\(Sometimes you may also need the `.likecli` directory mounted into the container, e.g. `gentx` which uses the keys managed by `likecli` to sign transaction\)

If you already have the `likechain/liked` container running and wants to connect to it, you may need:

`docker exec -it likechain/liked liked --home /likechain/.liked COMMANDS...`

Common usage:

#### Initializing chain node

`liked init [MONIKER]`

This will initialize default configuration files, generate consensus key and node key in `.liked` folder.

#### Adding genesis account

`liked add-genesis-account [ADDRESS] [COINS]`

This will append the account with the coins in `.liked/config/genesis.json`.

#### Generating and signing genesis transaction

`liked gentx [OPTIONS]`

This will generate and sign a genesis transaction for creating validator during genesis.

The parameters are set by options.

The generated transaction with signature will be stored in `.liked/config/gentx/` folder as JSON file.

See `--help` for more details.

#### Aggregating genesis transactions

`liked collect-gentxs`

This will collect genesis transactions in JSON files in `.liked/config/gentx/` into `.liked/config/genesis.json`.

#### Starting node

`liked start`

This will start the node.

#### Reseting chain data

`liked unsafe-reset-all`

This will clear the chain block data, resetting it to the initial state.

The configurations, consensus key, node key and `genesis.json` will remain unchanged.

#### Querying Tendermint related info

`liked tendermint [SUBCOMMANDS]`

This command provides subcommands for querying info about Tendermint, e.g. consensus public key and node ID.

See `--help` for more details.

### likecli

`likecli` is for communicating with nodes, e.g. query chain info, send transactions.

It also manages address private keys and starts lite client.

Keys and lite client data will be stored in `.likecli` folder, default location is `$HOME/.likecli`.

In the init script, we are running `likecli` in Docker \(image `likechain/likechain`\) and the `.likecli` directory is placed in `likechain` root directory. So to run the commands below, you may need:

``docker run --rm -it -v `pwd`/.likecli:/likechain/.likecli likechain/likechain likecli --home /likechain/.likecli COMMANDS...``

If you already have the `likechain/liked` container running and wants to connect to it, you may need:

`docker exec -it likechain/liked likecli --home /likechain/.likecli COMMANDS...`

Common usage:

#### Key management

`likecli keys [SUBCOMMANDS]`

This command provides subcommands for managing address keys, e.g. adding, removing, exporting, importing keys.

See `--help` for more details.

#### Querying chain info

`likecli query [SUBCOMMANDS]`

This command aggregates subcommands provided by Cosmos SDK modules for querying chain data.

Example: querying account info

`likecli query auth account cosmos1xvymudttgxrypxwy0ujnu5pgd6fq6c079yuf92 --chain-id likechain-testnet-taipei-1`

#### Signing and sending transactions

`likecli tx [SUBCOMMANDS]`

This command aggregates subcommands provided by Cosmos SDK modules for generating and signing transactions.

Example: sending 1000 LikeCoins from the `faucet` account managed by `likecli`

```text
likecli tx send faucet cosmos1mw2l98asefxev9s9mvdtm2j5mcap9mn5t3u8lh 1000000000000nanolike \
    --chain-id likechain-testnet-taipei-1 \
    --gas 44000 \
    --gas-prices 1000.0nanolike
```

#### Lite client

`likecli rest-server`

This command starts the lite client, which exposes the node APIs as understandable RESTful APIs.

See the [Cosmos SDK RPC doc](https://cosmos.network/rpc/) for more details.

## Configurations

Note that most of the configurations could be overridden by environment variables or command line arguments when starting the node.

### Tendermint

Tendermint configurations are related to the consensus part, e.g. node's name, P2P seed address, blocktime.

#### config.toml

See [Tendermint docs](https://tendermint.com/docs/tendermint-core/configuration.html) for the detailed lists.

Some notable items:

* `rpc.laddr`: HTTP RPC endpoint for querying node infos, default is only for localhost.
* `p2p.laddr`: Endpoint which other P2P nodes can connect with this node.
* `p2p.external_address`: External IP address which this node claims to others. If this field is not set, Tendermint will use `p2p.laddr` address \(which usually doesn't work, see [issues and workarounds](https://github.com/likecoin/likecoin-chain/wiki/LikeCoin-Chain-Validator-101-%28Technical-Part%29#ip-address-exchange) below\).
* `p2p.seeds`: Bootstrap nodes which this node will connect to and obtain addresses from for more peers.
* `p2p.persistent_peers`: This node will conenct to these nodes persistently.
* `p2p.private_peer_ids`: These nodes' addresses will not be exchanged with others. Can be used to hide the validator signing node's address. See [Sentry Node Architecture](https://github.com/likecoin/likecoin-chain/wiki/LikeCoin-Chain-Validator-101-%28Technical-Part%29#sentry-node-architecture) below.
* `consensus.timeout_commit`: This value controls the blocktime.

### Cosmos SDK

#### app.toml

This file contains application specific configurations.

* `minimum-gas-prices`: The minimum price per gas which your node will accept a transaction. The amount part should be in decmial format, e.g. `1000.0nanolike`, otherwise the node will fail to start. Note that if there is another node proposed a block including a transaction with gas price lower than this value, this node will still process the transaction. An ordinary LikeCoin transfer transaction takes about 40000 gas.

#### genesis.json

This file contains the genesis state of the blockchain. Every node in the same network should share the same `genesis.json`, otherwise they will fail to achieve consensus.

## Deployment

### Basic Launching Flow

1. Initial the chain via `liked init MONIKER`. This will generate basic configuration files and a template `genesis.json`.
2. Modify configuration files, especially `genesis.json` for chain parameters.
3. Add accounts by `liked add-genesis-account` \(or just modify `genesis.json` manually\) to initialize genesis account list.
4. All validators use the same `genesis.json` to generate and sign genesis transaction by `liked gentx`. The genesis transaction with signature will be stored in `.liked/config/gentx/` folder.
5. Someone aggregate these genesis transaction files and call `liked collect-gentxs` to collect the genesis transactions into `genesis.json`.
6. Discuss and set the genesis block time in `genesis.json`.
7. Distribute the final `genesis.json` to all validators.
8. Somebody set up seed nodes for nodes to bootstrap the P2P network.
9. All validators use the same `genesis.json` to start the node.
10. At genesis blocktime, the nodes will connect to seed nodes to exchange IP addresses, connect to each other and start to produce blocks.

### Availability

The staking related modules have availability requirements on validator nodes. If validator nodes cannot meet the availability requirement, some portion of delegated coins will be slashed \(burnt\) and the validator node will be temporary jailed, unable to participate in consensus and receive rewards.

Currently, LikeCoin Chain follows Cosmos Hub, setting availability parameters as follows: if a validator node's participation is less than 5% in the previous 10000 blocks, 0.01% of its delegated coins will be slashed.

To maintain a high availability validator node, the Cosmos cummunity has proposed the Sentry Node Architecture.

#### Sentry Node Architecture

The validator node which keeps the consensus key is hidden behind the sentry nodes.

The sentry nodes connect with the validator node using persistent and private connection, so the validator node's address will not be broadcasted in the network. The validator node only communicate with the network through the sentry nodes.

If sentry nodes are down, or loading increases, one can deploy more sentry nodes to balance the loadings.

See: [https://forum.cosmos.network/t/sentry-node-architecture-overview/454](https://forum.cosmos.network/t/sentry-node-architecture-overview/454)

### Key Management

A validator node will hold a few keys.

#### Consensus Key

The consensus key is the key a validator node used to sign the blocks. One can find signatures from these keys from prevote and precommit messages from validators.

By default, the consensus key is generated and stored in `.liked/config/priv_validator_key.json` in plaintext, while the signing state is stored in `.liked/data/priv_validator_state.json`. One can get its consensus public key by running `liked tendermint show-validator`.

If the consensus key is leaked, the attacker can use the key to sign conflicting blocks, making the corresponding validator gets slashed due to double signing. If more than 2/3 of voting power's consensus keys are leaked, attacker will be able to forge another chain which looks complete valid, making the whole blockchain meaningless.

Note that improper failover architecture \(e.g. 2 nodes with the same consensus key are online simutanously due to invalid failure detection\) also make double signing possible, so either the architecture should ensure that only one node will have the consensus key, or there should be measurements to explicitly prevent double signing \(e.g. ZooKeeper between signing services to ensure only one block hash will be signed for the same height and same round\).

Tendermint allows user to use an external service as signer service. User can set `priv_validator_laddr` in `config.toml` to allow the external service to connect to the node and provide signatures when needed.

Tendermint community has worked out a KMS service which uses hardware wallets \(Ledger / YubiHSM 2\) to keep the consensus key, to prevent the consensus key from leaking. See: [https://github.com/tendermint/kms](https://github.com/tendermint/kms)

#### Node Key

The node key is for authenticating the connection. For instance, seed peers and persistent peers are authenticated using the node ID, which is generated from the node key.

By default, the node key is generated and stored in `.liked/config/node_key.json` in plaintext. One can get its node ID by running `liked tendermint show-node-id`.

The security of the node key is not as important as the other two keys, because attacker would need to take over the IP addresses or domain names used for the node in order to forge the node's connection.

#### Operator Key

Operator key is for managing the application logic, e.g. delegation, editing validator commission rate, governance, etc.

This key is similar to a normal user's private key, except it has more permission on the validator.

When the operator key is initialized by `likecli keys add`, it is stored and encrypted inside the database in `.likecli`. The initialization process will show mnemonic words for backup the key.

One can keep this key using hardware wallets like Ledger:

1. Install the Ledger Cosmos application on your Ledger hardware following the instructions from [here](https://github.com/cosmos/ledger-cosmos).
2. Compile the `liked` and `likecli` applications with `ledger` tag. The applications require Go 1.13+ to compile. One can compile the applications by `go build -o likecli --tags 'ledger' cmd/likecli/main.go` \(change the paths for `liked`\).
3. When initializing the operator key, connect your Ledger and open the Cosmos application, and add the `--ledger` option in command line arguments: `likecli keys add my_key_name --ledger`.
4. When signing transactions using the key, connect your Ledger and open the Cosmos application.

## Transactions

A transaction is like a command to the blockchain, making the blockchain to change its state.

### Transaction Structure

In Tendermint, a transaction can be any binary string, as long as the application logic can process it.

In Cosmos SDK, a standard transaction is defined as a serialization of the following [structure](https://godoc.org/github.com/cosmos/cosmos-sdk/x/auth/types#StdTx):

```text
type StdTx struct {
    Msgs       []sdk.Msg      `json:"msg" yaml:"msg"`
    Fee        StdFee         `json:"fee" yaml:"fee"`
    Signatures []StdSignature `json:"signatures" yaml:"signatures"`
    Memo       string         `json:"memo" yaml:"memo"`
}
```

#### Messages

`sdk.Msg` is an interface implemented by Cosmos modules. It wraps the application logic related data, and has interface on things like who should be signing the message, how should the message be signed, how to validate the message, etc.

For example, a [MsgSend](https://godoc.org/github.com/cosmos/cosmos-sdk/x/bank/internal/types#MsgSend) defined by the bank module is as follows:

```text
type MsgSend struct {
    FromAddress sdk.AccAddress `json:"from_address" yaml:"from_address"`
    ToAddress   sdk.AccAddress `json:"to_address" yaml:"to_address"`
    Amount      sdk.Coins      `json:"amount" yaml:"amount"`
}
```

which indicates who is sending the coins, who is the receiver, and the amount of coins to be sent.

A transaction can include more than one message.

#### Gas, Gas Price and Transaction Fee

Each transaction will consume gas, which roughly indicates how much work is needed for processing the transaction. For instance, a normal transfer takes about 40000 gas.

A transaction must provide its maximum gas consumption, so that nodes can evaluate whether the transaction should be accepted or not by the transaction fee. During execution, if the actual gas consumption is greater than the claimed one, the execution will fail.

User can get the rough gas consumption by asking the node to run simulations. However, sometimes the simulated gas consumption will be much lower than the actual one, so one should multiply the simulated result by some factor \(e.g. multiply by 2\) to prevent transaction failure due to out of gas.

User can assign a transaction fee in the transaction. The gas price of the transaction equals to the transaction fee assigned divided by the gas consumption.

The fee will not be returned even if the actual gas consumption is lower than the assigned one.

Each node can set a minimum gas price. These nodes will not accept transactions which has gas price lower than the minimum they have set.

For validator nodes, these nodes will not get the transactions into their memory pool, hence will never propose a block including these transactions when they become a block proposer.

However, other nodes may have lower minimum gas price setting and hence including these transactions in their proposed blocks. In this case, all nodes must accept these transactions even if they have gas price lower than their minimum.

On the other hand, the lower the gas price is set, the lower the chance that a block proposer will get it into the block, hence delaying the execution of the transaction.

#### Sequence

Transactions are usually signed by user for authentication. Since blockchain transactions are public, it must have mechanism for preventing signature replay.

In Cosmos SDK, each account comes with a sequence number, which can be queried from account info. The sequence indicates the number of executed transactions this account has signed.

A new transaction must include the sequence number matching the signing account's current sequence. Therefore if a transaction is replayed, it will fail due to invalid sequence number.

A consequence is that if multiple transactions are being sent and processed in the same block, they must have contiguous sequence number and be sent in the order according to their sequence number.

### Transaction Execution Flow

This section explains the lifecycle of a transaction.

#### Constructing and Signing

First, the user constructs and signs a transaction through a client \(CLI / web\). The transaction is then either sent to a node directly \(CLI\), or first sent to a lite client \(web\), then encoded and forwarded by the lite client to a node.

#### CheckTx and Mempool

When a node receives a transaction, it performs `CheckTx` to do basic verifications for the trasnaction, e.g. checking sequence and signature.

It also checks the gas price of the transaction to see if it meets the minimum gas price requirement set by the node, and rejects the transaction if not.

After passing through the checkings, the transactions enters the memory pool of the node, and is forwarded to other nodes connected to this node.

Other nodes do the same procedure, check the transaction, add it into local memory pool and forward it to other nodes, spreading the transaction in the network.

#### Including into a block

When a validator becomes a proposer, it get transactions from its own memory pool and use them to construct a candidate block.

After the consensus process, the candidate block will be finalized as the new block.

See [Tendermint docs](https://tendermint.com/docs/introduction/what-is-tendermint.html#consensus-overview) for more details on the consensus process.

#### DeliverTx

After validators have finalized a block, nodes in the network the will execute transactions in the block.

Since the transactions are finalized, nodes must deterministically execute the transactions with the same result. Therefore in this stage, nodes must not reject the transaction only according to their local setting on minimum gas price.

The Cosmos SDK application updates the blockchain state \(e.g. account sequence and balance\) according to the content of the transactions.

## Common Modules, Transactions and Queries

### Auth

The `auth` module defines basic account logic like sequences.

#### Query: Account Info

Query account info, including balances, account number and sequence.

CLI: `likecli query auth account [ADDRESS]`

### Bank

The `bank` module mainly defines transfer of coins.

#### Transaction: Send

Send coins to receipent.

CLI: `likecli tx send [FROM_ADDRESS_OR_KEY_NAME] [TO_ADDRESS] [COINS]`

### Staking related modules

There are a few modules related to staking: `staking`, `mint`, `distribution`, `slashing`.

#### Transaction: Create Validator

Create validator, so the node with the corresponding consensus key can start to validate blocks.

Others can then delegate to the validator to increase its voting power and receive block rewards and transaction fee as return.

CLI: `likecli tx staking create-validator [OPTIONS]`

See `--help` for available options.

#### Transaction: Edit Validator

Edit validator info, including moniker, description, identity, website and commission rate.

Commission rate modification is limited by the validators maximum commission rate and maximum commission change rate which are set when creating the validators.

CLI: `likecli tx staking edit-validator [OPTIONS]`

See `--help` for available options.

#### Transaction: Delegate

Delegate to a validator, increasing its voting power, collecting block rewards and transaction fee as return.

CLI: `likecli tx staking delegate [VALIDATOR_ADDRESS] [COINS]`

#### Transaction: Redelegate

Move some delegations from one validator to another.

Unlike unbond, this action takes effect immediately and does not need to wait for unbond period.

However, user needs to wait for 3 weeks before the same redelegation can be redelegated again. For example, user delegated to A and then redelegated from A to B, then the user needs to wait for 3 weeks before redelegating from B to C.

CLI: `likecli tx staking redelegate [FROM_VALIDATOR_ADDRESS] [TO_VALIDATOR_ADDRESS] [COINS]`

#### Transaction: Unbond

Take away some delegations from a validator.

The delegation will enter unbonding state, which is locked for unbond period \(3 weeks\) before moving back into available balance.

CLI: `likecli tx staking unbond [VALIDATOR_ADDRESS] [COINS]`

#### Transaction: Withdraw Rewards

Get the accumulated rewards from a delegation. Can add the `--commission` flag to also withdraw validator's commission.

CLI: `likecli tx distribution withdraw-rewards [VALIDATOR_ADDRESS] [--commission]`

#### Transaction: Withdraw All Rewards

Get the accumulated rewards from all delegations among different validators.

CLI: `likecli tx distribution withdraw-all-rewards`

#### Transaction: Unjail

Unjail validator who got jailed because of downtime.

Note that validators who got jailed because of double signing cannot be unjailed.

CLI: `likecli tx slashing unjail`

#### Query: Delegations

Get current delegations info from a delegator.

CLI: `likecli query staking delegations [DELEGATOR_ADDRESS]`

#### Query: Validators

Get current validators info.

CLI: `likecli query staking validators`

#### Query: Inflation

Get current inflation rate.

CLI: `likecli query mint inflation`

#### Query: Rewards

Get current rewards which are not yet withdrawn.

CLI: `likecli query distribution rewards [DELEGATOR_ADDRESS] [OPTIONAL_VALIDATOR_ADDRESS]`

### Governance

#### Transaction: Submit Proposal

Submit a governance proposal, open for deposits before getting into voting.

Proposal content can be supplied either by command arguments or a file.

CLI: `likecli tx gov submit-proposal [OPTIONS]`

#### Transaction: Depositt

Deposit into an open proposal for voting.

CLI: `likecli tx gov deposit [PROPOSAL_ID] [COINS]`

#### Transaction: Vote

Vote in a proposal.

CLI: `likecli tx gov vote [PROPOSAL_ID] [yes|no|abstain]`

#### Query: Proposals

Query proposals.

CLI: `likecli query gov proposals`

#### Query: Deposits

Query proposal deposits.

CLI: `likecli query gov deposits [PROPOSAL_ID]`

#### Query: Votes

Query proposal votes.

CLI: `likecli query gov votes [PROPOSAL_ID]`

## Known Issues and Workarounds

### IP Address Exchange

Tendermint claims that if `p2p.external_address` is not set in `config.toml`, Tendermint will detect the external address from the listener or UPnP.

However, when using default settings, UPnP option will be turned off, and the listener address will be `tcp://0.0.0.0:26656`, the node will broadcast its own IP as `0.0.0.0:26657`, which is invalid for others to connect to.

This makes seed node unable to exchange addresses for these nodes, and the nodes can only connect to persistent peers. In previous testnet, the persistent peer provided by LikeCoin Foundation was the only node which other nodes are able to connect to, making it a centralized, failure-prone network architecture.

Even worse, the `p2p.external_address` option cannot be overridden by command line arguments or environment variables, so it is not possible to fix by external programs.

Current workaround: added a `--get-ip` option in `liked`, which detects external IP by some common IP detecting services \(e.g. httpbin.org\) and set the `p2p.external_address` field in the configuration structure before real execution.

Validators may disable this flag and set their `p2p.external_address` instead in `config.toml`, but should remember to update this field when the external address changes.

See:

[https://github.com/tendermint/tendermint/issues/3714](https://github.com/tendermint/tendermint/issues/3714)

[https://github.com/tendermint/tendermint/pull/3646](https://github.com/tendermint/tendermint/pull/3646)

### Empty Blocks

Currently, the block time is set to about 5 seconds, no matter there are transactions or not.

By statistics, the storage consumption of empty blocks is about 500 bytes per validator.

So for instance, a chain with 10 validators will consumes about 5 KB per 5 seconds, or about 29 GB per year, when there is totally no transaction. Such storage consumption for empty block data is not desirable.

Tendermint actually supports not creating empty blocks when there is no transaction. As an alternative, we may also adjust blocktime to a longer period.

However, there are some considerations in practice:

#### Application state changes

When application state changes, Tendermint will produce additional empty blocks for confirming that all validators has consensus in the application state, until there are consecutive blocks with the same application hash \(representing the application state\).

However, with the Proof of Stake modules, the application state is changing for every block. For example, the `mint` module will create coins for inflation, and the `distribution` module will record block validators precommit info to count missing validators. Since the application state is always changing, Tendermint will keep creating new empty blocks.

#### Inflation rate

Another issue is that the inflation rate is computed by number of blocks instead of the actual block's time.

In the `mint` module, there is a parameter on the expected number of blocks per year. Then, in the chain's application logic, the inflation rate and annual provision will be computed by that block period instead of actually one year.

For instance, 4% inflation rate per year actually means "4% of inflation per N blocks", where N is the number of blocks set per year.

However, in Tendermint, there is no way to fix the block time. When to create a block is determined by the proposer. Others may consider the proposer as timeout if the block time is too long, but there is no limit on how short the block time can be.

Therefore if the block time is "set" to say 60 seconds, and the expected blocks per year is set to `365.25 * 24 * 3600 / 60 = 525960` blocks per year, but then there are transactions every 10 seconds, then the actual number of blocks per year will be 6 times as the expected one.

This makes the number of coins minted for inflation 6 times as the expected one, breaking the economy.

This issue limits the expected block time to a relative short period.

It is possible to modify the `mint` module to use block timestamp instead of block number as the measure on time, but more investigation is needed.

