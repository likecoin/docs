# Setup local test node

1. Clone the [likecoin-chain](https://github.com/likecoin/likecoin-chain) git repository

* For SheungWan

```text
git clone https://github.com/likecoin/likecoin-chain \
--branch sheungwan --single-branch \
likecoin-chain-sheungwan && cd likecoin-chain-sheungwan
```

* For FoTan

```text
git clone https://github.com/likecoin/likecoin-chain \
--branch fotan-1 --single-branch \
likecoin-chain-fotan && cd likecoin-chain-fotan
```

2. Build the chain Docker image

```text
./docker/build.sh
```

3. Add a key for local use, please record the **mnemonic** shown

```text
export YOUR_KEY_NAME=<type your key name here>
export CHAIN_ID=likechain-local-testnet
docker-compose run --rm liked \
liked --home /likechain/.liked \
keys add $YOUR_KEY_NAME
```

4. Init the testnet

```text
docker-compose run --rm liked \
liked --home /likechain/.liked \
init testnet --chain-id $CHAIN_ID
```

5. Set all denom in `genesis.json` to nanolike

```text
docker-compose run --rm liked \
sed -i  's/"stake"/"nanolike"/g' /likechain/.liked/config/genesis.json
```

6. Init the testnet accounts

```text
docker-compose run --rm liked \
liked --home /likechain/.liked \
add-genesis-account $YOUR_KEY_NAME 1000000000000000000nanolike

docker-compose run --rm liked \
liked --home /likechain/.liked \
gentx $YOUR_KEY_NAME 1000000000000000000nanolike --chain-id $CHAIN_ID

docker-compose run --rm liked \
liked --home /likechain/.liked collect-gentxs
```

7. Modify `docker-compose.yml` and `./.liked/config/app.toml` if you need lcd / grpc services

```text
#docker-compose.yml
				ports:
            - 1317:1317
            - 9090:9090
            - 26656:26656
            - 127.0.0.1:26657:26657
```

```text
# app.toml
[api]

# Enable defines if the API server should be enabled.
enable = true
```

8. Start running the node

```text
docker-compose up -d
```

