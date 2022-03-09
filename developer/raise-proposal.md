---
description: Raise a proposal with LikeCoin chain daemon `.liked`.
---

# Raise Proposal

Following steps will raise an example proposal in the testnet. The process for mainnet is the same, only the network configs and coin denoms are different.

# Clone the project

1. Run following command to clone the [likecoin/likecoin-chain](https://github.com/likecoin/likecoin-chain) repo:
    
    ```bash
    git clone https://github.com/likecoin/likecoin-chain --branch fotan-1.1 --single-branch
    ```
    
2. Run following command to change working directory:
    
    ```bash
    cd likecoin-chain
    ```
    

# Build the Docker image

Run following command to build the docker image:

```bash
./build.sh
```

# **Initialize the node and account keys**

1. Initialize the node and account keys
    1. Run following command to copy `docker-compose.yml` and `.env` files from templates:
        
        ```bash
        cp docker-compose.yml.template docker-compose.yml
        cp .env.template .env
        ```
        
    2. Modify `.env` file for the network config:
        1. For [mainnet](https://github.com/likecoin/mainnet):
            
            ```
            LIKECOIN_DOCKER_IMAGE="likecoin/likecoin-chain:fotan-1.1"
            LIKECOIN_TOKEN_DENOM="nanolike"
            LIKECOIN_CHAIN_ID="likecoin-mainnet-2"
            
            LIKECOIN_GENESIS_URL="https://gist.githubusercontent.com/williamchong/de1bdf2b2a8f3bce50a4b5e46af26959/raw/4e21bff586771c849d22e1916bcb88c6463fbaa0/genesis.json"
            LIKECOIN_SEED_NODES="913bd0f4bea4ef512ffba39ab90eae84c1420862@34.82.131.35:26656,e44a2165ac573f84151671b092aa4936ac305e2a@nnkken.dev:26656"
            
            LIKECOIN_MONIKER="<change this for your node's name>"
            ```
            
        2. For [testnet](https://github.com/likecoin/testnets):
            
            ```
            LIKECOIN_DOCKER_IMAGE="likecoin/likecoin-chain:fotan-1.1"
            LIKECOIN_TOKEN_DENOM="nanoekil"
            LIKECOIN_CHAIN_ID="likecoin-public-testnet-3"
            
            LIKECOIN_GENESIS_URL="https://gist.githubusercontent.com/nnkken/4a161c14e9dc03f412c36d11cdf7ea27/raw/9265c348c9f79b918d99aeee7f6c29b6b3bc449f/genesis.json"
            LIKECOIN_SEED_NODES="c5e678f14219c1f161cb608aaeda37933d71695d@nnkken.dev:31801"
            
            LIKECOIN_MONIKER="<change this for your node's name>"
            ```
            
        Note that testnet uses coin denom `nanoekil` rather than `nanolike`.
        Note that `LIKECOIN_MONIKER` is a custom name you decide for your node's name.

        
    3. Run following command to create `.liked` directories with node config and keys initialized:
        
        ```bash
        docker-compose run --rm init
        ```
        
    4. Run following command to add an operator key with key-name `validator`. Type-in your passphrase twice, the command will output your operator address, and also a 12-24 words mnemonic phrase. Please backup the mnemonic phrase properly as it represents your validator's private key.
        
        ```bash
        docker-compose run --rm liked-command keys add validator
        ```
        
    5. To enable an empty account on the chain, we need to send some coins first. For testnet, you can copy the address generated from above step, and go to the testnet faucet to get some coins:
        
        [likecoin-chain-internal-testnet-sheungwan Faucet](https://likecoin-public-testnet-faucet.nnkken.dev/)
        
    
    # Write a proposal file
    
    Store the proposal as the `text-proposal.json` file under the `likecoin-chain` folder. 
    
    Modify `title` and `description` for content of the proposal. Use `\n` to break the line in `description`. Here are some samples:
    
    ```json
    {
      "title": "Testing",
      "description": "testing",
      "type": "Text",
      "deposit": "1nanoekil"
    }
    ```
    
    ```json
    {
      "title": "[Rectify Proposal 25]XXXX",
      "description": "This is a Test!\nTo rectify Proposal 25\nFull Text:\n...",
      "type": "Text",
      "deposit": "1000000000nanoekil"
    }
    ```
    
    # Raise the proposal
    
    Run following command to use content file `text-proposal.json` raise a proposal, with default key-name `validator` via http://node.testnet.like.co:443/rpc/ to `likecoin-public-testnet-3` network.
    
    ```bash
    docker-compose run --rm liked-command \
    tx gov submit-proposal \
         --proposal=/host/text-proposal.json \
         --from validator \
         --node https://node.testnet.like.co:443/rpc/ \
         --chain-id likecoin-public-testnet-3
    ```
    
    # Deposit the proposal
    
    Find the raised proposal here:
    
    [mainnet](https://stake.like.co/proposals)
    
    [testnet](https://likecoin-public-testnet-3.netlify.app/proposals)
    
    Deposit some coins to the proposal.