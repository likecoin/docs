---
description: >-
  This is the deprecated method of setting up a node. Please read the latest
  guide first.
---

# Setup on docker (Deprecated)

### Setup steps

1. Clone the project
2. Build the Docker image
3. Initialize the node and account keys
4. Start up the node and wait for synchronization catch up

#### Clone the project

Run `git clone https://github.com/likecoin/likecoin-chain --branch release/v3.x --single-branch`, then `cd likecoin-chain`.

#### Build the Docker image

Run `make build-docker`.

#### Initialize the node and account keys

1. Run\
   `cp docker-compose.yml.template docker-compose.yml`\
   `cp .env.template .env`\
   \`\`for setting up the `docker-compose.yml` and `.env`.\\
2. Modify `.env` file for the network config.\
   For [mainnet](https://github.com/likecoin/mainnet):\
   `LIKECOIN_MONIKER="<change this for your node's name>"`\
   `LIKECOIN_DOCKER_IMAGE="likecoin/likecoin-chain:v3.0.0"`\
   `LIKECOIN_CHAIN_ID="likecoin-mainnet-2"`\
   `LIKECOIN_GENESIS_URL="https://gist.githubusercontent.com/williamchong/de1bdf2b2a8f3bce50a4b5e46af26959/raw/4e21bff586771c849d22e1916bcb88c6463fbaa0/genesis.json"`\
   `LIKECOIN_SEED_NODES="913bd0f4bea4ef512ffba39ab90eae84c1420862@34.82.131.35:26656,e44a2165ac573f84151671b092aa4936ac305e2a@nnkken.dev:26656"`\
   `\` For [testnet](https://github.com/likecoin/testnets):\
   `LIKECOIN_MONIKER="<change this for your node's name>"`\
   `LIKECOIN_DOCKER_IMAGE="likecoin/likecoin-chain:v3.0.0"`\
   `LIKECOIN_CHAIN_ID="likecoin-public-testnet-5"`\
   `LIKECOIN_GENESIS_URL="https://gist.githubusercontent.com/nnkken/4a161c14e9dc03f412c36d11cdf7ea27/raw/9265c348c9f79b918d99aeee7f6c29b6b3bc449f/genesis.json"`\
   `LIKECOIN_SEED_NODES="c5e678f14219c1f161cb608aaeda37933d71695d@nnkken.dev:31801"`\
   `\` Note that `LIKECOIN_MONIKER` is a custom name you decide for your node's name.\\
3. Run `docker-compose run --rm init` to create `.liked` directories, with node config and keys initialized.\\
4. Run `docker-compose run --rm liked-command keys add validator` to add an operator key. The command will output your operator address, and also a 12-24 words mnemonic phrase. Please backup the mnemonic phrase properly as it represents your validator's private key.\
   When asked, enter and repeat a passphrase for protecting your account key.

#### Start up the node

Run `docker-compose up -d`. This will create and run the Docker containers in background.

To see if the node is running well, you can input `docker-compose logs` to see if there is any error.
