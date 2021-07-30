# For other full node operators

For non-validator nodes, or for validator nodes who cannot join the upgrade process, you may setup a full node or replace your current full node after the upgrade is finished.

1. Clone the software if you haven't already have one:

   ```text
   git clone https://github.com/likecoin/likecoin-chain
   ```

2. Switch to the `fotan-1` branch:

   ```text
   git checkout fotan-1
   ```

3. Backup `docker-compose.yml` if you have one:

   ```text
   cp docker-compose.yml docker-compose.yml.sheungwan
   ```

4. Setup `docker-compose.yml` and `.env` file:

   ```text
   cp docker-compose.yml.template docker-compose.yml
   cp .env.template .env
   ```

5. Get the genesis URL, which will be generated \(uploaded\) during the upgrade process by validators.
6. Setup `.env` file according to the chain parameter:
   * `LIKECOIN_DOCKER_IMAGE`: `"likecoin/likecoin-chain:fotan-1"`
   * `LIKECOIN_CHAIN_ID`: to be decided by the upgrade proposal
   * `LIKECOIN_UID`: normally keep it as `"1000"` is fine, but if you are using root user under Linux \(e.g. in some VPS\) then you should change it to `"0"`.
   * `LIKECOIN_MONIKER`: the original moniker \(in `.liked/config/config.toml`, search for `moniker`\). If not sure, any name indicating your node is OK.
   * `LIKECOIN_GENESIS_URL`: the genesis URL you obtained from the previous step.
   * `LIKECOIN_SEED_NODES`: to be setup
7. Backup the original node if you have one:

   ```text
   mv .liked .liked.bak
   ```

8. Initialize the node with new software:

   ```text
   docker-compose run --rm init
   ```

9. Re-import the keys and address books from the old node if you have one:

   ```text
   cp \
     .liked.bak/config/node_key.json \
     .liked.bak/config/priv_validator_key.json \
     .liked.bak/config/addrbook.json \
     .liked/config
   ```

10. Start up the node:

    ```text
    docker-compose up -d
    ```

11. Wait for synchronization, which you may check by going to [http://localhost:26657/status](http://localhost:26657/status) and see `result.sync_info.catching_up` . If it shows `false` then the node has caught up.
12. If you have keystore, you may migrate the keys by running the following command:

    ```text
    docker-compose run liked-command keys migrate /host/.likecli
    ```

