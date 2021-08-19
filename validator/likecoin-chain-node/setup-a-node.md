# Setup a node

### Requirements

1 core machine with 2 GB RAM, running Linux or Mac, with Docker and Docker Compose \(version &gt;= 1.28\) installed.

At least 100 GB storage for chain data. \(Estimated storage requirement: 40 GB per year\)

Please make sure that your TCP port 26656 is connectable from external network.

### Setup steps

1. [Clone the project](https://github.com/likecoin/likecoin-chain/wiki/Setup-LikeCoin-chain-mainnet-node#clone-the-project)
2. [Build the Docker image](https://github.com/likecoin/likecoin-chain/wiki/Setup-LikeCoin-chain-mainnet-node#build-the-docker-image)
3. [Initialize the node and account keys](https://github.com/likecoin/likecoin-chain/wiki/Setup-LikeCoin-chain-mainnet-node#initialize-the-node-and-account-keys)
4. [Start up the node](https://github.com/likecoin/likecoin-chain/wiki/Setup-LikeCoin-chain-mainnet-node#start-up-the-node) and wait for synchronization catch up

#### Clone the project

Run `git clone https://github.com/likecoin/likecoin-chain --branch fotan-1 --single-branch`, then `cd likecoin-chain`.

#### Build the Docker image

Run `./build.sh`.

#### Initialize the node and account keys

Run

`cp docker-compose.yml.template docker-compose.yml  
cp .env.template .env`

for setting up the `docker-compose.yml` and `.env`.

Modify `.env` file for the network config.

For mainnet:

`LIKECOIN_MONIKER="<change this for your node's name>"  
LIKECOIN_DOCKER_IMAGE="likecoin/likecoin-chain:fotan-1"  
LIKECOIN_CHAIN_ID="likecoin-mainnet-2"  
LIKECOIN_GENESIS_URL="https://gist.githubusercontent.com/williamchong/de1bdf2b2a8f3bce50a4b5e46af26959/raw/4e21bff586771c849d22e1916bcb88c6463fbaa0/genesis.json"  
LIKECOIN_SEED_NODES="913bd0f4bea4ef512ffba39ab90eae84c1420862@34.82.131.35:26656,e44a2165ac573f84151671b092aa4936ac305e2a@nnkken.dev:26656"`

For testnet:

`LIKECOIN_MONIKER="<change this for your node's name>"  
LIKECOIN_DOCKER_IMAGE="likecoin/likecoin-chain:fotan-1"  
LIKECOIN_CHAIN_ID="likecoin-public-testnet-3"  
LIKECOIN_GENESIS_URL="https://gist.githubusercontent.com/nnkken/4a161c14e9dc03f412c36d11cdf7ea27/raw/9265c348c9f79b918d99aeee7f6c29b6b3bc449f/genesis.json"  
LIKECOIN_SEED_NODES="c5e678f14219c1f161cb608aaeda37933d71695d@nnkken.dev:31801"`

Note that `LIKECOIN_MONIKER` is a custom name you decide for your node's name.

Run `docker-compose run --rm init` to create `.liked` directories, with node config and keys initialized.

Run `docker-compose run --rm liked-command keys add validator` to add an operator key. The command will output your operator address, and also a 12-24 words mnemonic phrase. Please backup the mnemonic phrase properly as it represents your validator's private key.

When asked, enter and repeat a passphrase for protecting your account key.

#### Start up the node

Run `docker-compose up -d`. This will create and run the Docker containers in background.

To see if the node is running well, you can input `docker-compose logs` to see if there is any error.

The node will connect to the network and start to synchronize blocks, which may take some time depends on how long the network is started.

You can check the synchronization progress at http://{YOUR\_NODES\_IP}:26657/status. `result.sync_info.catching_up` will be `false` if the node has already caught up the network's blocks.

#### Becoming a validator

For a validator node, you will need a node synchronized, which you may setup following the steps above.

You also need some LikeCoin in your operator address.

Then you can use the following command to create a validator, turning your node into a validator node:

`docker-compose run --rm create-validator \  
    --amount <AMOUNT> \  
    --details <DETAILS> \  
    --commission-rate <COMMISSION_RATE>`

Modify the parameters:

* `<AMOUNT>`: the amount to self-delegate on the validator at the beginning \(e.g. `90000000000000nanoekil`\).
* `<DETAILS>`: the detailed description of the validator. Remember to quote it using `"`.:
* `<COMMISSION_RATE>`: the validator's commission rate, which could be seen as the "tax" received by the validator from delegators, e.g. `0.5` \(50%\).

Optionally, you may add the following additional parameters:

* `--identity <IDENTITY>`: a string representing the identity of the validator, usually the GPG fingerprint. Some block explorers \(e.g. Big Dipper\) will query this field and search [Keybase](https://keybase.io/) for the user profile.
* `--website <WEBSITE>`: the website of the validator.

After signing and sending the transaction, your node should turn into a validator node. You may check by viewing `.liked/data/priv_validator_state.json`, the `height` value will change to non-zero if the node is validating blocks.

