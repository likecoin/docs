# Setup mainnet node

### Requirements

1 core machine with 2 GB RAM, running Linux or Mac, with Docker and Docker Compose installed.

At least 100 GB storage for chain data. \(Estimated storage requirement: 40 GB per year\)

Please make sure that your TCP port 26656 is connectable from external network.

### Setup steps

1. [Clone the project](https://github.com/likecoin/likecoin-chain/wiki/Setup-LikeCoin-chain-mainnet-node#clone-the-project)
2. [Build the Docker image](https://github.com/likecoin/likecoin-chain/wiki/Setup-LikeCoin-chain-mainnet-node#build-the-docker-image)
3. [Initialize the node and account keys](https://github.com/likecoin/likecoin-chain/wiki/Setup-LikeCoin-chain-mainnet-node#initialize-the-node-and-account-keys)
4. [Start up the node](https://github.com/likecoin/likecoin-chain/wiki/Setup-LikeCoin-chain-mainnet-node#start-up-the-node) and wait for synchronization catch up

#### Clone the project

Run `git clone https://github.com/likecoin/likecoin-chain --branch sheungwan --single-branch`, then `cd likecoin-chain`.

#### Build the Docker image

Run `./scripts/build.sh`.

#### Initialize the node and account keys

Download `genesis.json` [here](https://gist.githubusercontent.com/nnkken/1d1b9d4aae4acb3d835dd3150f546d44/raw/4d97fd471b4bf3be8c5475efbc0361f4926e65e5/genesis.json) and put it somewhere \(e.g. in `likecoin-chain` folder\).

Run `./scripts/init.sh MONIKER genesis.json 913bd0f4bea4ef512ffba39ab90eae84c1420862@34.82.131.35:26656`, where `MONIKER` is your node's custom name.

When asked, enter and repeat a passphrase for protecting your account key.

This will create `.liked` and `.likecli` directories, with node config and keys initialized.

#### Start up the node

Run `docker-compose up -d`. This will create and run the Docker containers in background.

To see if the node is running well, you can input `docker-compose logs` to see if there is any error.

The node will connect to the network and start to synchronize blocks, which may take some time depends on how long the network is started.

You can check the synchronization progress at http://{YOUR\_NODES\_IP}:26657/status. `result.sync_info.catching_up` will be `false` if the node has already caught up the network's blocks.

