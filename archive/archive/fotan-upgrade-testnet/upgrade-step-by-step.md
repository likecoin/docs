---
description: >-
  The Testnet upgrade aims to provide a platform for validators to have
  rehearsal on upgrading the chain from SheungWan to FoTan.
---

# Upgrade Step-by-step

{% hint style="danger" %}
Archived on 2022/06/14. Information is out of date.
{% endhint %}

## Overview&#x20;

### Preparation

* Set up a Testnet chain running _SheungWan_ software (to mimic the current state of _SheungWan_ Mainnet).

### Pre-upgrade

*   Make sure you have all keys&#x20;

    * operator key in `.likecli` folder, or in mnemonic format,
    * node key in `.liked/config/node_key.json`
    * consensus key in `.liked/config/priv_validator_key.json`

    backed up properly, in case anything disastrous happens.
* Pass the proposal, determining the **date**, **time**, **software version** and **parameters** of the upgrade
* Change the node config, so it will automatically halt at the determined upgrade time

### During upgrade

* Run a web conference with other validators
  * Need to discuss **export height** and **genesis time** in realtime
* Export keys and files
  * Export node key and consensus key by copying the key files
  * Export address book by copying the key files
* Create new genesis
  * Determine export height
  * Determine new chain genesis time
  * Export old chain state
  * Migrate old chain state to new chain genesis
  * Verify new chain state
* Setup new chain node
  * Initialize new chain node
  * Import new chain state
  * Import operator key
  * Import node key and consensus key
  * Import address book
  * Migrate operator key
* Start the node and wait for what would happen at the new chain genesis time

## Setup Testnet with SheungWan software

{% hint style="info" %}
### :man\_mage:Part I - Setup Testnet with SheungWan software
{% endhint %}

### Requirements

{% hint style="success" %}
## Requirements

* [ ] A server/ computer which will always be online.
* [ ] May get one from [Google Cloud Compute Engine free tier](https://cloud.google.com/free/docs/gcp-free-tier/#compute), though the networking may have some cost.
* [ ] Or use a free trial quota from cloud providers
* [ ] At least 40 GB of disk space
* [ ] SSD preferred
* [ ] Install [Git](https://git-scm.com/)
* [ ] Install [Docker](https://docs.docker.com/engine/install/) and [Docker Compose](https://docs.docker.com/compose/install/), Docker Compose needs to have version ≥ 1.28
{% endhint %}

### Parameters

* **Chain ID:** `likecoin-chain-public-testnet-2`
* **Genesis file:** [https://gist.githubusercontent.com/nnkken/a4eff0359b1acd816aa536bd664eb7ed/raw/207206a952078184b7dea1f152d4068612ef7bd6/genesis.json](https://www.notion.so/a4eff0359b1acd816aa536bd664eb7ed)
  * SHA256: `313f93afce5438655239f8f6915af02fd500a7485c6e0a2a0fb8ae8b6ed1decb`
* **Seed node:** `c5e678f14219c1f161cb608aaeda37933d71695d@nnkken.dev:31801`
* Software:
  * before upgrade: [https://github.com/likecoin/likecoin-chain/tree/sheungwan-2](https://github.com/likecoin/likecoin-chain/tree/sheungwan-2)
    * commit: `f81b7c728c0cdf22db4c324d8a12003c99b09703`
  * after upgrade: [https://github.com/likecoin/likecoin-chain/tree/fotan-1](https://github.com/likecoin/likecoin-chain/tree/fotan-1)
    * commit: `32056fc4759d276a11180256474cc4ed5e3ed8d4`
* Faucet: [https://likecoin-public-testnet-faucet.nnkken.dev](https://likecoin-public-testnet-faucet.nnkken.dev)
* Explorer: [https://likecoin-chain-public-testnet-2.netlify.app/](https://likecoin-chain-public-testnet-2.netlify.app/)
* Denom (unit of token): `nanoekil` (ekil is reverse of like)

### Setup procedure

1. Install [Git](https://git-scm.com/), [Docker](https://docs.docker.com/engine/install/) and [Docker Compose](https://docs.docker.com/compose/install/)
2.  Clone the deployment repo with the corresponding branch:

    ```
    git clone https://github.com/likecoin/likecoin-chain --branch sheungwan-2
    ```
3.  Go into the cloned repo:

    ```
    cd likecoin-chain
    ```
4.  Copy the template `docker-compose.yml.template` and `.env.template` as `docker-compose.yml` and `.env` respectively:

    ```
    cp docker-compose.yml.template docker-compose.yml
    cp .env.template .env
    ```
5. Edit `.env` file to fill in the details, including chain parameters and custom parameters:
   * `LIKECOIN_DOCKER_IMAGE`: `"likecoin/likecoin-chain:sheungwan-2-testnet"`
   * `LIKECOIN_CHAIN_ID`: `"likecoin-chain-public-testnet-2"`
   * `LIKECOIN_UID`: normally keep it as `"1000"` is fine, but if you are using root user under Linux (e.g. in some VPS) then you should change it to `"0"`.
   * `LIKECOIN_MONIKER`: any name you want to call your node. Will be displayed on validator list as the name of the validator.
   * `LIKECOIN_GENESIS_URL`: `"https://gist.githubusercontent.com/nnkken/a4eff0359b1acd816aa536bd664eb7ed/raw/207206a952078184b7dea1f152d4068612ef7bd6/genesis.json"`
   * `LIKECOIN_SEED_NODES`: `"c5e678f14219c1f161cb608aaeda37933d71695d@nnkken.dev:31801"`
6.  Initialize the node:

    ```
    docker-compose run --rm init
    ```

    This will create `.liked` and `.likecli` folders, setup the node config files and download genesis file according to the parameters in `.env`.

    Note that building the Docker image is not necessary, as the image is already on Docker Hub and Docker Compose will download the image automatically.\

7.  Setup the keystore and the operator key:

    ```
    docker-compose run --rm likecli-command keys add validator
    ```

    Follow the instruction to setup the keystore with passphrase. Eventually the command will output the address and a set of mnemonic words. Please write down the mnemonic words for backup.\

8.  Start the node

    ```
    docker-compose up -d
    ```
9.  Check the logs:

    ```
    docker-compose logs --tail 100 -f
    ```

    You should see the node synchronizing the blocks from the network. You may stop the display of the logs by `Ctrl+C` at anytime, it won't stop the node operation.\

10. Wait until the node is synchronized. This may take some time (hours), depending on the current block height of the chain.

    You may check by going to [http://localhost:26657/status](http://localhost:26657/status) and check `result.sync_info.catching_up`. If the value is `false`, that means the node has caught up the latest block of the network.\

11. Run the following command to check the operator address:

    ```
    docker-compose run --rm likecli-command keys show validator --address
    ```
12. Get some token from the faucet at [https://likecoin-public-testnet-faucet.nnkken.dev](https://likecoin-public-testnet-faucet.nnkken.dev). Fill in the operator address for receiving the token.\

13. You may check the balance by:

    ```
    docker-compose run --rm likecli-command \
    query account \
    --chain-id likecoin-chain-public-testnet-2 \
    --node tcp://liked-service:26657 \
    <OPERATOR_ADDRESS>
    ```

    Here modify `<OPERATOR_ADDRESS>` to the operator address you get from the previous step.\

14. Sign and send a transaction for creating a validator:

    ```
    docker-compose run --rm create-validator \
    --amount <AMOUNT> \
    --details <DETAILS> \
    --commission-rate <COMMISSION_RATE>
    ```

    Modify the parameters:

    * `<AMOUNT>`: the amount to self-delegate on the validator at the beginning (e.g. `90000000000000nanoekil`).
    * `<DETAILS>`: the detailed description of the validator. Remember to quote it using `"`.:
    * `<COMMISSION_RATE>`: the validator's commission rate, which could be seen as the "tax" received by the validator from delegators, e.g. `0.5` (50%).

    Optionally, you may add the following additional parameters:

    * `--identity <IDENTITY>`: a string representing the identity of the validator, usually the GPG fingerprint. Some block explorers (e.g. Big Dipper) will query this field and search [Keybase](https://keybase.io/) for the user profile.
    * `--website <WEBSITE>`: the website of the validator.\

15. You should be able to query the validator by:

    ```
    docker-compose run --rm likecli-command \
    query staking validators \
    --chain-id likecoin-chain-public-testnet-2 \
    --node tcp://liked-service:26657
    ```

    Note that the operator address referring the validator will start by `cosmosvaloper1` instead of `cosmos1`, and the last few letters (checksum characters) are also different.

## Pre-upgrade: proposal & preparation

{% hint style="info" %}
### ​​ :man\_mage: Part II - Pre-upgrade: proposal & preparation
{% endhint %}

### Pre-upgrade

1.  Raise and pass a proposal on the upgrade.

    To raise a proposal, one of the validators run the following command:

    ```
    docker-compose run --rm likecli-command \
    tx gov submit-proposal \
    --chain-id likecoin-chain-public-testnet-2 \
    --node tcp://liked-service:26657 \
    --from validator \
    --title "Upgrade software version to fotan-1" \
    --type text \
    --deposit 10000000000000nanoekil \
    --description <DESCRIPTION>
    ```

    Modify the parameters:

    * `<DESCRIPTION>`: the content of the proposal, which should include some introduction to the upgrade, and also the following contents:
      * the halt time (in both human-readable format with timezone, and also Unix timestamp)
      * the new chain parameters for the new ISCN module, namely:
        * ISCN registry name
        * ISCN fee per byte
      * the new software version (in Git commit hash)
      * and the new chain ID (e.g. `likecoin-chain-public-testnet-3`)\

2.  After the creation of the proposal, one may query the content of the proposal by:

    ```
    docker-compose run --rm likecli-command \
    query gov proposals \
    --chain-id likecoin-chain-public-testnet-2 \
    --node tcp://liked-service:26657
    ```

    This will also show the proposal ID (should be `1` for the first proposal).\

3.  To pass the proposal, all validators vote for the proposal by running:

    ```
    docker-compose run --rm vote 1 yes
    ```

    Which means `vote "yes" in proposal ID 1`.\

4. After the proposal is passed, setup chain halt time by modifying `.env` file and changing `LIKECOIN_HALT_TIME` to the Unix timestamp of the halt time in the proposal.\

5.  Restart the chain node by running:

    ```
    docker-compose up -d
    ```
6. Jot down the content of the proposal, since chain explorers and APIs may not work during upgrade.

## During upgrade

{% hint style="info" %}
### :man\_mage: Part III - During the upgrade
{% endhint %}

1. Right before the upgrade, validators should jot down the content of the proposal, since chain explorers and APIs may not work during the upgrade.
2. Validators should hold a meeting right before the upgrade time for discussing issues during the upgrade.
3. When the upgrade time comes, the chain node should be halt automatically.
4.  Go into the node folder:

    ```
    cd likecoin-chain
    ```
5.  Turn down the node:

    ```
    docker-compose stop
    ```
6.  Check the consensus public key:

    ```
    docker-compose run --rm liked-command tendermint show-validator
    ```

    Record the output as consensus public key for later verification\

7.  Check the node ID:

    ```
    docker-compose run --rm liked-command tendermint show-node-id
    ```

    Record the output as node ID for later verification\

8.  Check the halting height of the node by:

    ```
    docker-compose run --rm liked-command show-height
    ```
9. Confirm with other validators for the minimum height of exporting the state. The principle is to have consent and prevent state lost. For example, if the heights are `1234`, `1234`, `1234`, `1233`, `1233` for different validators, then validators may use `1233` as the height for exporting state.\

10. Export chain state:

    ```
    docker-compose run --rm liked-command \
    export --for-zero-height \
    --height <HEIGHT> \
    > exported.json
    ```

    Where the `<HEIGHT>` is the height confirmed with other validators in the previous step.\

11. Copy `node_key.json` (node key), `priv_validator_key.json` (consensus key) and `addrbook.json` (address book) from `.liked/config` into the fotan node folder:

    ```
    mkdir keys
    cp .liked/config/node_key.json \
    .liked/config/priv_validator_key.json \
    .liked/config/addrbook.json \
    keys
    ```

    This is to preserve the same keys and address book for the new fotan node.\

12. Discuss with others the new genesis time, should have consensus according to the progress of the majority.\

13. Fetch the newest software branch for the upgrade:

    ```
    git fetch
    ```
14. Checkout to the new software:

    ```
    git checkout fotan-1
    ```
15. Use new template of `docker-compose.yml` from the new software:

    ```
    cp docker-compose.yml docker-compose.yml.old
    cp docker-compose.yml.template docker-compose.yml
    ```
16. Modify `.env` for the new chain:
    * `LIKECOIN_DOCKER_IMAGE`: `likecoin/likecoin-chain:fotan-1-testnet`
    * `LIKECOIN_CHAIN_ID`: the new chain ID specified in the proposal.
    * `LIKECOIN_HALT_TIME`: `"0"` so that the new chain node can start up.
    * `LIKECOIN_GENESIS_URL`: `"genesis.json"`. The init script will detect that it is a local file and copy it from the migrated genesis file generated in the next step.\

17. Migrate genesis state:

    ```
    docker-compose run --rm liked-command \
    migrate /host/exported.json \
    --log_level "error" \
    --chain-id <NEW_CHAIN_ID> \
    --iscn-registry-name <ISCN_REGISTRY_NAME> \
    --iscn-fee-per-byte <ISCN_FEE_PER_BYTE> \
    --genesis-time <GENESIS_TIME> \
    --output /host/genesis.json
    ```

    Where `<NEW_CHAIN_ID>`, `<ISCN_REGISTRY_NAME>` and `<ISCN_FEE_PER_BYTE>` should be modified to the values specified in the upgrade proposal, and `<GENESIS_TIME>` is determined in the previous step (format: `YYYY-MM-DDThh:mm:ssZ`, in UTC).\

18. Archive the old `.liked` folder:

    ```
    mv .liked .liked-old
    ```
19. Compute the checksum of genesis state with others:

    ```
    sha256sum genesis.json
    ```

    For Mac, use the following command instead:

    ```
    shasum -a 256 genesis.json
    ```

    Verify the output checksum with other validators.\

20. Re-initialize the node:

    ```
    docker-compose run --rm init
    ```

    Note that this will create and write a new consensus public key at the end of `.env` file, which won't be used since we will use the original key instead. If you are already a validator, you will probably never use the field again so this is fine, but you are free to delete this line.\

21. (optional) Configure the new node (`config.toml` & `app.toml`, both are in `.liked/config`)
    * in `app.toml`:
      * setup `minimum-gas-prices` if needed, see the setting in your sheungwan node config
      * under `[api]` section, if you need a local RESTful API server, then set `enable` to `true`, and also setup the corresponding port mapping in `docker-compose.yml`
    * in `config.toml`:
      * under `[p2p]` section, if you don't want to use the `--get-ip` option in the command parameter when starting the node for retrieving your externally accessible IP from third parties, then you need to enter your external address and port in `external_address` (e.g. `123.123.123.123:26656`)\

22. Migrate the operator key:

    ```
    docker-compose run liked-command keys migrate /host/.likecli
    ```

    Follow the instructions to migrate the keys in the old keystore.

    For passphrases, the first one is for decrypting the old keystore, and the following 2 are for creating the new keystore.

    Note that when it asks `Skip key migration? [y/N]:`, `N` actually means `not skipping`, which is what we need.\

23. Verify the operator key is properly imported:

    ```
    docker-compose run --rm liked-command keys list
    ```

    Check if the key with operator's address is listed and is the same address as before.\

24. Re-import node key, consensus key and address book:

    ```
    cp keys/node_key.json \
    keys/priv_validator_key.json \
    keys/addrbook.json \
    .liked/config
    ```
25. Verify the consensus key has been properly imported:

    ```
    docker-compose run --rm liked-command \
    tendermint show-validator
    ```

    Verify that the output is the same as the previous recorded consensus public key.\

26. Verify the node key has been properly imported:

    ```
    docker-compose run --rm liked-command \
    tendermint show-node-id
    ```

    Verify that the output is the same as the previous recorded node ID.\

27. Restart the node:

    ```
    docker-compose up -d
    ```
28. Monitor the logs:

    ```
    docker-compose logs -f
    ```
29. Wait for the new genesis time to see if anything goes wrong.
30. Properly process the `.liked-old`, `.likecli` and `keys` folders, so the credentials are not leaked.

## When Upgrade failed

{% hint style="warning" %}
### :man\_mage: Part IV - When Upgrade failed
{% endhint %}

If fatal issues happened during the upgrade (e.g. serious software bugs), then with the consent from the majority of the validators, validators may give up the upgrade and restart the SheungWan chain.

The procedure is simple:

1. Revert changes to `docker-compose.yml` and `.env`.
2. Set `halt-time` to `"0"` in `.env`.
3. Revert `.liked` folder from `.liked-bak`.
4. Start the node by `docker-compose up -d`.
5. Wait for enough validators to get online.

