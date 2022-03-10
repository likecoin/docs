---
description: Raise a proposal with LikeCoin chain daemon `.liked`.
---

# Raise Proposal

1. Download the `liked`
    
    Download the latest stable version of `liked`(LikeCoin chain daemon) from below link.
    
    https://github.com/likecoin/likecoin-chain/releases

    At the time of writing, it's [v1.2.0](https://github.com/likecoin/likecoin-chain/releases/tag/v1.2.0).
    
    Unzip the file and go to the unzipped folder.
    
2. Open a terminal
    
    Open a terminal under the unzipped folder. If you run `ls` command, you will see files as below.
    
    ```bash
    JohnDoe@MacBook-Pro  likecoin-chain_1.2.0_Darwin_arm64 % ls
    CHANGELOG.md	LICENSE		README.md	bin
    ```
    
3. Add account keys
    
    Run following command to add an operator key with key-name `proposer`. Type-in your passphrase twice, the command will output your operator address, and also a 12-24 words mnemonic phrase. Please backup the mnemonic phrase properly as it represents your validator's private key.
    
    ```bash
    ./bin/liked keys add proposer
    ```
    
4. Deposit some coin 
    
    To enable an empty account on the chain, we need to deposit some coins first. 
    
    For testnet, you can copy the address generated from above step, and go to the testnet faucet to get some coins:
    
    [Testnet Faucet](https://likecoin-public-testnet-faucet.nnkken.dev/)
    
5. Write a proposal file
    
    Run following command to create a `proposals` folder. 
    
    ```bash
    mkdir proposals
    ```
    
    Run following command to create a proposal template. 
    
    ```bash
    cat << EOF > proposals/text-proposal.json
    {
      "title": "Testing",
      "description": "testing",
      "type": "Text",
      "deposit": "1nanoekil"
    }
    EOF
    ```
    
    Edit `title` and `description` for content of the proposal. Use `\n` to break the line in `description`.
    
    Note that the coin denom for mainnet is `nanolike`, for testnet is `nanoekil`. Modify the denom in `deposit` field if you are raising proposal to mainnet.
    
    For example:
    
    ```json
    {
      "title": "[Rectify Proposal 25]XXXX",
      "description": "This is a Test!\nTo rectify Proposal 25\nFull Text:\n...",
      "type": "Text",
      "deposit": "1000000000nanoekil"
    }
    ```
    
6. Raise the proposal
    
    Run following command to raise a proposal.
    
    For mainnet: 
    
    ```bash
    ./bin/liked tx gov submit-proposal \
         --proposal=proposals/text-proposal.json \
         --from proposer \
         --node https://mainnet-node.like.co:443/rpc/ \
         --chain-id likecoin-mainnet-2
    ```
    
    For testnet:
    
    ```bash
    ./bin/liked tx gov submit-proposal \
         --proposal=proposals/text-proposal.json \
         --from proposer \
         --node https://node.testnet.like.co:443/rpc/ \
         --chain-id likecoin-public-testnet-3
    ```
    
7. Deposit the proposal
       
    Find the raised proposal:

    For mainnet: https://stake.like.co/proposals

    For testnet: https://likecoin-public-testnet-3.netlify.app/proposals

    Deposit some coins to the proposal.