# Setup local test node

1. Clone the [likecoin-chain](https://github.com/likecoin/likecoin-chain) git repository using the latest tag. As of now latest version is `v3.0.0`, please check the mainnet repository to confirm version.

```
git clone https://github.com/likecoin/likecoin-chain \
--branch v3.0.0 --single-branch \
likecoin-chain && cd likecoin-chain
```

2\. (optional) Build the chain Docker image

```
make build-docker
```

3\. Setup the needed files and folders

```
cp docker-compose.yml.template docker-compose.yml
cp .env.template .env
mkdir -p .liked
```

4\. Add a key for local use, please record the **mnemonic** shown

```
export YOUR_KEY_NAME=<type your key name here>
export CHAIN_ID=<type your chain ID here>
docker-compose run --rm liked-command \
    keys add $YOUR_KEY_NAME
```

5\. Init the testnet

```
docker-compose run --rm liked-command \
    init testnet --chain-id $CHAIN_ID
```

6\. Set all denom in `genesis.json` to nanolike

```
docker-compose run --rm liked-service \
    sed -i 's/"stake"/"nanolike"/g' /likechain/.liked/config/genesis.json
```

7\. Init the testnet accounts

```
docker-compose run --rm liked-command \
    add-genesis-account $YOUR_KEY_NAME 2000000000000000000nanolike

docker-compose run --rm liked-command \
    gentx $YOUR_KEY_NAME 1000000000000000000nanolike --chain-id $CHAIN_ID

docker-compose run --rm liked-command \
    collect-gentxs
```

8\. Modify `docker-compose.yml` and `./.liked/config/app.toml` if you need lcd / grpc services

```
#docker-compose.yml
	    ports:
            - 1317:1317
            - 9090:9090
            - 26656:26656
            - 127.0.0.1:26657:26657
```

```
# app.toml
[api]

# Enable defines if the API server should be enabled.
enable = true
```

9\. Start running the node

```
docker-compose up -d
```
