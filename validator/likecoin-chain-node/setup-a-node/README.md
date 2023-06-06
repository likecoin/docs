# Setup a node (mainnet / public testnet)

## Welcome

Thank you for your interest in joining our validator community! Your participation is important to the security of LikeCoin chain.

This guide covers steps to host a validator node with Cosmovisor via Linux Systemd or Docker Compose.

We recommend all operators to adopt the Systemd method. The Docker Compose method is deprecated and will not be maintained in the future.

### To Existing Operators

#### Why the change?

Since the v1.2.0 release, LikeCoin chain binary supports Cosmovisor, a process manager that manages chain binaries and monitors for upgrade proposals.

Cosmovisor allows future chain upgrades to utilize upgrade proposals and in-place store migrations, which vastly reduces the coordination effort and chain downtime required compared to the past manual upgrades.

Under this new workflow, once an upgrade proposal is approved by the community and the chain reaches the defined upgrade block height, validators will automatically swap to the new binary version and run state migration scripts. Operators will only be required to place the next binary into the `upgrades` folder of cosmovisor before upgrade time.

Optionally, operators can opt into using the auto-download feature, which automatically downloads the new binary from url defined in the upgrade proposal before upgrade.

For usage and folder layout of Cosmovisor, please refer to [Cosmovisor quick start guide](https://docs.cosmos.network/v0.44/run-node/cosmovisor.html)

#### Before we continue

Existing operators migrating their node should ensure that there is **only one instance running concurrently** at all times to avoid double signing.

> Be aware of blocks like this for migration specific notes

## System Requirements

_Note that system requirements, especially memory, may increase drastically when performing chain upgrade or state sync._

### Hardware

* Recommended
  * 2 CPU Cores
  * 16GB RAM
  * 500GB+ SSD
* Minimum
  * 2 CPU Cores
  * 4GB RAM
  * 250GB+ SSD
    * Current snapshot size is 120GB with 70GB growth each year.
    * We expect the growth rate to increase after our NFT module and new dApps are rolled out.

### OS

* Ubuntu 20.04 LTS
  * YMMV on other Linux distros
  * Debian-based ones will likely work fine with this guide
* Using non-Linux host is not recommended
  * The Docker Compose method works on other OS, but it will be discontinued in the future.

### Network Ports

* Required
  * TCP 26656 for P2P
* Optional, if you use the node as RPC endpoint
  * TCP 9090 for gRPC
  * TCP 1317 for REST
  * TCP 26657 for Tendermint RPC

### Outline

Below are major steps to create a validator node:

1. Secure the host
2. Initialize the node
3. Synchronize the node to the latest block
4. Create operator account
5. Create validator

### Secure the host

Refer to Node Security page.

### Systemd Route (Recommended)

We will run a setup script to download the latest binary release, write config files and start up the service.

Again, this method is supported on Linux only. We prepared this guide with Ubuntu 20.04 LTS. YMMV on other distros.

> When you see `<Placeholder>` in code blocks below, please replace them with correct values.

#### Obtain dependencies

We will first clone the likecoin-chain repo to obtain required scripts

> For validator migration, we recommend cloning a new copy to avoid confusion, since the previous guide stored data within the repo folder.
>
> If your existing repo folder is already at `~`, appending the clone command with a new folder name, and adopt this guide by changing the `cd ~/likecoin-chain` commands.

```shell
cd ~
git clone https://github.com/likecoin/likecoin-chain.git --branch release/v3.x --single-branch
```

Then, install required tools:

```shell
sudo apt update
sudo apt install make
```

### Run the setup-node script

This script will download cosmovisor, chain binary, and the genesis file. Then, it will run `liked init` and prepare a systemd service file.

By default, binaries will be downloaded to the user's home directory `~/`, and the liked data directory will be `~/.liked`

For advanced configuration, such as changing folder locations or specifying binary versions, refer to [the developer facing guide](https://github.com/likecoin/likecoin-chain/blob/master/SETUP.md)

> If you are migrating an existing node on the same host, please ensure that your existing `.liked` folder is not at your home directory, otherwise this might overwrite your files!

For latest genesis url and seed node, we host the latest info on Github: [Mainnet](https://github.com/likecoin/mainnet/). Following is the command for running the setup-node script for mainnet. Please confirm the `LIKED_VERSION` to be used in the above Mainnet Github repository.

```shell
export MONIKER='<My Validator>'
export GENESIS_URL='https://raw.githubusercontent.com/likecoin/mainnet/master/genesis.json'
export LIKED_SEED_NODES='913bd0f4bea4ef512ffba39ab90eae84c1420862@34.82.131.35:26656,e44a2165ac573f84151671b092aa4936ac305e2a@nnkken.dev:26656'
export LIKED_VERSION='4.0.0'
cd ~/likecoin-chain
make -C deploy setup-node
```

Testnet Info of can find here: [Public Testnet](https://github.com/likecoin/testnets), current active testnet is `likecoin-public-testnet-5`. Following is the command for running the setup-node script for testnet. Please confirm the latest testnet and parameters to be used in the testnet Github repository.

```bash
export MONIKER='<My Validator>'
export GENESIS_URL='https://raw.githubusercontent.com/likecoin/testnets/master/likecoin-public-testnet-5/genesis.json'
export LIKED_SEED_NODES='1ca24cb5e744287284372cfdfe545f9ee16703c6@20.6.73.206:26656,49976c3bd43da9271f226cbedf02d4b6b8fc880c@35.233.143.230:26656'
export LIKED_VERSION='4.0.0'
cd ~/likecoin-chain
make -C deploy setup-node
```

If you decided not to using state sync as describe below, you may need to change the `LIKED_VERSION=4.0.0`. 4.0.0 is the version we start adpoting cosmovisor, it should upgrade itself to newer version during sync. There is still some manual upgrade need due to patch or bugs, please refer to [syncing-from-genesis.md](syncing-from-genesis.md "mention").

### Import existing validator files

> For existing validators hosted with the Docker Compose guide only. New operators should skip this section.
>
> Steps below generally applies to custom setups but paths to your old `.liked` folder and the command to stop the node will be different.

First, rename the `.liked` folder generated by the script as `.liked.template`:

```shell
mv ~/.liked ~/.liked.template
```

Then, stop your existing node:

```shell
cd /path/to/old/repo/likecoin-chain
docker-compose down
```

Move the old `.liked` folder to `~/.liked`:

```shell
cd /path/to/old/repo/likecoin-chain
mv ./.liked ~/.liked
```

Add the new `cosmovisor` sub-folder created by the script to `~/.liked`:

```shell
cp -r ~/.liked.template/cosmovisor ~/.liked/cosmovisor
```

Check that there are 4 folders within `~/.liked`:

```shell
config
cosmovisor
data
keyring-file
```

For some setups, the keyring files may be on the root of `.liked` directly instead of inside `keyring-file` folder, please move the following files to `~/.liked/keyring-file` folder so the liked flag `--keyring-backend=file` works:

```shell
<hash>.address
keyhash
<account name>.info
```

### State Sync

> Skip this section for migrating operators

Syncing a node from genesis often requires hours if not days. To save time, we can start the new node from a known block.

_Note that state sync requires at least 16GB (32GB recommended) of memory to complete successfully. After state sync is done, you can lower the amount of memory for daily operations._

Firstly, obtain two trusted rpc endpoints. These info can often be found on the same repos hosting genesis files. We have included the addresses of mainnet public nodes below.

Then, we will need to obtain the latest block height and hash from one of the rpc endpoints:

```shell
curl -s https://fotan-node-1.like.co:443/rpc/block
```

{% hint style="info" %}
For testnet, it should be `curl -s https://node.testnet.like.co/rpc/block`
{% endhint %}

The height is `result.block.header.height`, while the hash is `result.block_id.hash`

Next, we will edit `~/.liked/config/config.toml`. Locate the `[statesync]` section and update it to the following values:

```toml
[statesync]
enable = true
rpc_servers = "https://fotan-node-1.like.co:443/rpc/,https://fotan-node-2.like.co:443/rpc/"
trust_height = <known height>
trust_hash = "<known hash>"
trust_period = "168h0m0s"
discovery_time = "15s"
temp_dir = ""
chunk_request_timeout = "60s"
chunk_fetchers = "4"
```

{% hint style="info" %}
Use`rpc_servers = "`[`https://node.testnet.like.co:443/rpc/,https://node.testnet.like.co:443/rpc/`](https://node.testnet.like.co/rpc/,https://node.testnet.like.co:443/rpc/)`"` if you are setting up testnet.
{% endhint %}

Then, the node will use state sync to synchronize with the network instead of replaying from genesis at launch.

If you have already started the service once, i.e. there is an ongoing sync, you will have to reset the state back to genesis, otherwise state sync will not start:

```shell
~/liked tendermint unsafe-reset-all
```

### Change node configuration

You are recommended to review `~/.liked/config/config.toml` and `~/.liked/config/app.toml`, then change the defaults as desired.

In particular, please set a minimum gas price for your node and enable state sync in `app.toml`:

```toml
minimum-gas-prices = "1.0nanolike"
snapshot-interval = 1000
```

{% hint style="info" %}
The unit for testnet is `nanoekil`
{% endhint %}

This avoids spams on the network and help new nodes sync to the latest state quickly.

For more details, please refer to [Node Configuration docs](https://docs.like.co/validator/likecoin-chain-node/node-configuration).

### Activate the service

Now we will call the setup script again to activate the systemd config and start the node.

The service is configured to start the node via Cosmovisor. It will auto-start whenever the machine is booted.

The service file will be placed at `/etc/systemd/system/liked.service`.

> For migrating validators, please ensure the old instance is turned off before you proceed!

```shell
cd ~/likecoin-chain
make -C deploy initialize-systemctl
make -C deploy start-node
```

New nodes will now synchronize with the network. We can continue below steps to create a validator afterwards.

You can check the sync status by:

```shell
curl -s localhost:26657/status
```

The synced height is `result.sync_info.latest_block_height`, while `result.sync_info.catching_up` reflects if the node has finished sync up.

> For migrating validators, this is the final step. The validator node should resume operation immediately.

#### View status and logs

Check the status of the service by:

```shell
sudo systemctl status liked
```

Follow logs by `journalctl`:

```shell
journalctl -u liked.service -f
```

#### Managing the service

The service can be managed via `systemctl`:

```shell
sudo systemctl stop liked
sudo systemctl start liked
```

### Create operator account

We will generate a new operator account. The key will be stored in password-protected files in `~/.liked/keyring-file`. This account is required to manage the validator and cast votes on proposals.

```shell
export KEY_NAME='my-validator'
~/liked keys add $KEY_NAME --keyring-backend file
```

The mnemonic phrase will then be displayed. Write this phrase down physically and keep it in secure storage. Do not type the phrase on a computer.

To display the operator key address:

```shell
~/liked keys show $KEY_NAME --keyring-backend file --bech val
```

### Becoming a validator node

Please ensure your account owns more than the initial self-delegate amount.

Note that `commission-max-rate` and `commission-max-change-rate` cannot be changed afterwards.

Below values are examples and can be customized.

```shell
~/liked tx staking create-validator \
--amount=500000000000nanolike \
--pubkey=$(~/liked tendermint show-validator) \
--moniker=$MONIKER \
--commission-rate="0.10" \
--commission-max-rate="0.50" \
--commission-max-change-rate="0.05" \
--min-self-delegation="500000000000" \
--chain-id="likecoin-mainnet-2" \
--from=$KEY_NAME \
--keyring-backend=file \
--gas-prices 10nanolike
```

You can obtain the validator address by:

```shell
~/liked tendermint show-address
```

At this stage, you should back up `~/.liked/config` and `~/.liked/keyring-file` which contains your node key, consensus key and operator key. For security, please consider encrypting your backup with tools like GPG before transferring off the host.

#### Confirm the validator is running

```shell
~/liked query tendermint-validator-set | grep "$(~/liked tendermint show-address)"
```

You can also check via chain explorers: [dao.like.co](https://dao.like.co), [Big Dipper](https://likecoin.bigdipper.live/)

### Common operations for validator

#### Edit Validator

You may edit validator details anytime:

```shell
~/liked tx staking edit-validator \
--moniker="New Name" \
--website="https://example.com" \
--details="Description of my validator" \
--commission-rate="0.05" \
--chain-id="likecoin-mainnet-2" \
--from=$KEY_NAME \
--keyring-backend=file \
--gas-prices 10nanolike
```

#### Vote

An important job of being an operator is to participate in DAO governance. To vote on a proposal:

```shell
~/liked tx gov vote 123 yes \
--chain-id='likecoin-mainnet-2' \
--from=$KEY_NAME \
--keyring-backend=file
```

where `123` is the proposal number and `yes` is the vote

#### Unjail

A validator may be jailed after some downtime. To resume receiving rewards, submit an `unjail` transaction:

```shell
~/liked tx slashing unjail \
--chain-id='likecoin-mainnet-2' \
--from=$KEY_NAME \
--keyring-backend=file
```

## Docker Compose Route (Deprecated)

This route is transitional for existing operators who followed our old setup guide to quickly adopt cosmovisor in time for the next chain upgrade.

In newer docker image releases, cosmovisor is bundled in the image. When an upgrade is announced and approved, operators should prepare and place the next version `liked` binary within `.liked/cosmovisor/upgrades` folder before the upgrade time. Please refer to related chain upgrade guides for exact steps.

### Adopt Cosmovisor for existing validators on Docker

First, shut down the existing stack:

```shell
cd /path/to/cloned/repo/likecoin-chain
docker-compose down
```

Check out the new release tag to obtain the new version of docker-compose template:

```shell
git fetch --tags
git checkout release/v3.x
```

Back up the existing `docker-compose.yml` and replace it with the new version:

```shell
mv docker-compose.yml docker-compose.yml.bak
cp docker-compose.yml.template docker-compose.yml
```

Edit `.env` to target new docker image tag:

```shell
LIKECOIN_DOCKER_IMAGE="likecoin/likecoin-chain:v4.0.0"
```

Create cosmovisor folders structure:

```shell
mkdir .liked/cosmovisor
mkdir .liked/cosmovisor/upgrades
```

We can now start the stack again:

```shell
docker-compose up -d
```
