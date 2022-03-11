# LaiChiKok-2.0 Upgrade (v2.0.0)

LaiChiKok-2.0 is the second major upgrade to the LikeCoin chain. It updates Cosmos SDK to 0.44.6 and adds support for `like` account prefix.

## Timeline

|Event           |Time                |
|----------------|--------------------|
|Testnet Proposal|W1 April            |
|Testnet Deploy  |W2 April, height TBC|
|Mainnet Proposal|W2 April            |
|Mainnet Deploy  |W3 April, height TBC|

## Software Versioning Changes

After `Fotan-1.1`, releases will be tagged with semantic versioning to facilitate the usage of CI/CD pipelines, e.g. `v1.2.3`. Pre-release versions will contain suffixes such as `-rc1`, `-beta2`, `-alpha3`.

Below is a list of recent stable releases:

- `FoTan-1.1`: Current mainnet version
- `v1.2.0`: First version to support cosmovisor, binary-compatible with mainnet
- `v2.0.0`: LaiChiKok upgrade

## Workflow

1. `v2.0.0` is tagged on repo and binary builds are released on github via CI

2. Upgrade proposal is raised on-chain, which specifies the following parameters:

- Upgrade Name: `LaiChiKok-2.0`
- Upgrade Height: (TBC)
- Upgrade Info:

  ```json
  {
    "binaries": {
      "linux/amd64": "https://github.com/likecoin/likecoin-chain/releases/download/v2.0.0/likecoin-chain_2.0.0_Linux_x86_64.tar.gz",
      "linux/arm64": "https://github.com/likecoin/likecoin-chain/releases/download/v2.0.0/likecoin-chain_2.0.0_Linux_arm64.tar.gz",
      "darwin/amd64": "https://github.com/likecoin/likecoin-chain/releases/download/v2.0.0/likecoin-chain_2.0.0_Darwin_x86_64.tar.gz",
      "darwin/arm64": "https://github.com/likecoin/likecoin-chain/releases/download/v2.0.0/likecoin-chain_2.0.0_Darwin_arm64.tar.gz"
    }
  }
  ```

3. After the proposal is approved, operators should place the `v2.0.0` binary at the Cosmovisor upgrades folder BEFORE the upgrade time. Alternatively, operators can configure cosmovisor to download binaries automatically.

4. Cosmovisor will automatically switch binaries at the scheduled block height. Operators will not be required to run migrations or restart chain manually.

## Instructions for Validator Operators

### Migrate to Cosmovisor

To support the automatic upgrade, operators should **migrate to host their node with Cosmovisor** beforehand, which is supported since `v1.2.0`. A setup guide with migration instructions is available [here](../likecoin-chain-node/setup-a-node.md). `v1.2.0` is binary compatible with `fotan-1.1`, so operators can **upgrade at their own pace**.

Operators can also test their setup and practice the migration flow on testnet before the actual upgrade.

Operators who opt out of adopting Cosmovisor will need to swap binaries manually during the upgrade time, which will introduce extra downtime on their node.

### Prepare the next binary ahead of upgrade height

Once the proposal is approved on-chain, operators should either download or build the next binary version, and place it within the Cosmovisor upgrades folder.

The path to the new binary should be:

```shell
.liked/cosmovisor/upgrades/LaiChiKok-2.0/bin/liked
```

Alternatively, operators can enable the auto-download feature of Cosmovisor by setting environment variable `DAEMON_ALLOW_DOWNLOAD_BINARIES` to `true`, which is the default if our setup script or docker image was used. To be safe, we recommend you do prepare the binary manually.

### Review node configuration

Due to Cosmos SDK changes, there is a requirement of configuring **minimum gas price**. In the past, the configuration is empty string (zero gas price) by default. After the upgrade, the node **will refuse to start up if a gas price is not explicitly set**. We recommend setting a non-zero value, which can mitigate spam transactions on the network.

We also urge all validators to take this chance to review their `app.toml` config, especially the **state-sync snapshots** feature. By contributing state-sync snapshots, the synchronization process of new nodes can be speeded up from days to minutes. This will be vital to the growth of our network, as the full chain data size is growing rapidly due to more features and applications being added to LikeCoin chain.

Below are items to be updated in `app.toml`:

```toml
minimum-gas-prices="1.0nanolike" # set your own price

[state-sync]
snapshot-interval=1000 # set non-zero value to enable
snapshot-keep-recent=2 # set your own value depending on disk space
```

## Instructions for Upgrade Proposer

### CI/CD Release

Once a release candidate is validated on devnet / testnet, please tag the commit with version `v2.0.0`. CI will test and build with the tagged commit, then release it on GitHub.

Please also push commits to `release/v2.x` and update branch names in node setup guides.

### Submit Proposal

The proposer should submit a proposal with below command:

```shell
./liked tx gov submit-proposal software-upgrade "LaiChiKok-2.0" \
--title "Upgrade LikeCoin chain mainnet to LaiChiKok-2.0" \
--description "This proposal is for upgrading the LikeCoin chain mainnet software from FoTan-1.1/FoTan-1.2 to LaiChiKok-2.0. Full proposal: https://ipfs.io/ipfs/..." \
--from $ACCOUNT \
--upgrade-height $UPGRADE_HEIGHT \
--upgrade-info '{"binaries":{"linux/amd64":"https://github.com/likecoin/likecoin-chain/releases/download/v2.0.0/likecoin-chain_2.0.0_Linux_x86_64.tar.gz","linux/arm64":"https://github.com/likecoin/likecoin-chain/releases/download/v2.0.0/likecoin-chain_2.0.0_Linux_arm64.tar.gz","darwin/amd64":"https://github.com/likecoin/likecoin-chain/releases/download/v2.0.0/likecoin-chain_2.0.0_Darwin_x86_64.tar.gz","darwin/arm64":"https://github.com/likecoin/likecoin-chain/releases/download/v2.0.0/likecoin-chain_2.0.0_Darwin_arm64.tar.gz"}}' \
--deposit 10000000nanolike \
--chain-id "likecoin-mainnet-2"
```

The proposal content, especially `upgrade-info` should be validated on testnet beforehand.

Please also refer to the technical documentation on upgrade proposal usage [here](https://github.com/likecoin/likecoin-chain/blob/master/SETUP.md#upgrade-proposal).
