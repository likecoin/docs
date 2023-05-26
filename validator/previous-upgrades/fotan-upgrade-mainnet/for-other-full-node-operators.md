# For other full node operators

For non-validator nodes, or for validator nodes who cannot join the upgrade process, you may setup a [full node](../../likecoin-chain-node/setup-a-node/) or replace your current full node after the upgrade is finished.

1.  Clone the software if you haven't already have one:

    ```
    git clone https://github.com/likecoin/likecoin-chain
    ```
2.  Switch to the `fotan-1` branch:

    ```
    git checkout fotan-1
    ```
3.  Backup `docker-compose.yml` if you have one:

    ```
    cp docker-compose.yml docker-compose.yml.sheungwan
    ```
4.  Setup `docker-compose.yml` and `.env` file:

    ```
    cp docker-compose.yml.template docker-compose.yml
    cp .env.template .env
    ```
5. Get the genesis URL, which will be generated (uploaded) during the upgrade process by validators.
6. Setup `.env` file according to the chain parameter:
   * `LIKECOIN_DOCKER_IMAGE`: `"likecoin/likecoin-chain:fotan-1"`
   * `LIKECOIN_CHAIN_ID`: `"likecoin-mainnet-2"`
   * `LIKECOIN_UID`: normally keep it as `"1000"` is fine, but if you are using root user under Linux (e.g. in some VPS) then you should change it to `"0"`.
   * `LIKECOIN_MONIKER`: the original moniker (in `.liked/config/config.toml`, search for `moniker`). If not sure, any name indicating your node is OK.
   * `LIKECOIN_GENESIS_URL`: `https://gist.githubusercontent.com/williamchong/de1bdf2b2a8f3bce50a4b5e46af26959/raw/4e21bff586771c849d22e1916bcb88c6463fbaa0/genesis.json`
   * `LIKECOIN_SEED_NODES`: `913bd0f4bea4ef512ffba39ab90eae84c1420862@34.82.131.35:26656,e44a2165ac573f84151671b092aa4936ac305e2a@nnkken.dev:26656`
7.  Backup the original node if you have one:

    ```
    mv .liked .liked.bak
    ```
8.  Initialize the node with new software:

    ```
    docker-compose run --rm init
    ```
9.  Re-import the keys and address books from the old node if you have one:

    ```
    cp \
      .liked.bak/config/node_key.json \
      .liked.bak/config/priv_validator_key.json \
      .liked.bak/config/addrbook.json \
      .liked/config
    ```
10. Start up the node:

    ```
    docker-compose up -d
    ```
11. Wait for synchronization, which you may check by going to [http://localhost:26657/status](http://localhost:26657/status) and see `result.sync_info.catching_up` . If it shows `false` then the node has caught up.
12. If you have keystore, you may migrate the keys by running the following command:

    ```
    docker-compose run liked-command keys migrate /host/.likecli
    ```
