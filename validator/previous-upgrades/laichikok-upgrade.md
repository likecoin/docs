---
description: LaiChiKok is the second major upgrade to the LikeCoin chain
---

# LaiChiKok Upgrade

#### [Upgrade Overview](https://blog.like.co/en/likecoin-chain-upgrade-laichikok-overview/)

### Please join the [#mainnet-validators](https://discord.gg/yGUqtcHGjv) channel.

### Changelog

* Upgrade cosmos-sdk to 0.44.8, ibc-go to 2.1.0
* Add support for `like` account prefix (by LikerLand)
* Add migrations for bech32 stored in state (by LikerLand)
* Add `liked debug convert-prefix` command tool for bech32 conversion

### Timeline

| Event                                                            | Time                                                            |
| ---------------------------------------------------------------- | --------------------------------------------------------------- |
| Testnet Proposal                                                 | W3 April 2022                                                   |
| Testnet Deploy                                                   | W3 April 2022                                                   |
| [Mainnet Proposal](https://likecoin.bigdipper.live/proposals/46) | W4 April 2022                                                   |
| Mainnet Deploy                                                   | <p>4 May 2022, around UTC 11:00AM. <br>Block height 3692800</p> |

Software Versioning Changes

After `fotan-1.1`, releases will be tagged with semantic versioning to facilitate the usage of CI/CD pipelines, e.g. `v1.2.3`. Pre-release versions will contain suffixes such as `-rc1`, `-beta2`, `-alpha3`.

Below is a list of recent stable releases:

* `fotan-1.2`: Current mainnet version
* `v1.2.0`: First version to support cosmovisor, binary compatible with `fotan-1.2`
* `v2.0.0`: LaiChiKok upgrade

### System Requirements During Upgrade

The system resources required during the upgrade will be higher than normal operation for data migration tasks.

In particular, large amount of memory will be used, and data files will be duplicated for backup.

After the upgrade is applied, the day-to-day resources requirement is same as previously suggested in our Node Setup Guide.

Below recommendation is based on recent test runs of migration with mainnet data. Any machine with less than 16GB will likely result in OOM (out of memory) error. Also note that using swap will lengthen the upgrade duration considerably.

#### Recommended

* 8 CPU Cores
* 64GB RAM + 32GB Swap
* 500GB+ SSD

#### Minimum

* 4 CPU Cores
* 16GB RAM + 48GB Swap
* 500GB+ SSD

Refer to [this third party guide](https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-20-04) for steps to add swap space.

Using RAM lower than 16GB will likely result a OOM and corruption of data.

Operators who could not arrange a capable machine might opt to temporarily stop validating until the network has upgraded, then catch up to trusted nodes using state sync.

### Workflow



1. `v2.0.0` is tagged on repo and binary builds are released on github via CI
2. Upgrade proposal is raised on-chain, which specifies the following parameters:
   * Upgrade Name: `v2.0.0`
   * Upgrade Height: (TBC)
   *   Upgrade Info:

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
4. Cosmovisor will automatically switch binaries at the scheduled block height. Operators will not be required to run migrations or restart chain manually. However, operators are recommended to be present during the upgrade time in case of any unforeseen issues.

### Instructions for Validator Operators

#### Migrate to Cosmovisor

To support the automatic upgrade, operators should **migrate to host their node with Cosmovisor** beforehand, which is supported since `v1.2.0`. A setup guide with migration instructions is available [here](../likecoin-chain-node/setup-a-node/). `v1.2.0` is binary compatible with `fotan-1.1`, so operators can **upgrade at their own pace**.

Operators can also test their setup and practice the migration flow on testnet before the actual upgrade.

**Upgrading without Cosmovisor**

Although not recommended, it is possible for operators to opt out of using Cosmovisor.

At the upgrade height, the old chain binary will halt with `upgrade needed` panic. Afterwards, operators shall backup their `.liked` folder, then start their node using the new version binary.

#### Prepare the next binary ahead of upgrade height

Once the proposal is approved on-chain, operators should either download or build the next binary version, and place it within the Cosmovisor upgrades folder.

The path to the new binary should be:

```shell
 .liked/cosmovisor/upgrades/v2.0.0/bin/liked
```

Alternatively, operators can enable the auto-download feature of Cosmovisor by setting environment variable `DAEMON_ALLOW_DOWNLOAD_BINARIES` to `true`, which is the default if our setup script or docker image was used. To be safe, we recommend you do prepare the binary manually.

#### Review node configuration

Due to Cosmos SDK changes, there is a requirement of configuring **minimum gas price**. In the past, the configuration is empty string (zero gas price) by default. After the upgrade, the node **will refuse to start up if a gas price is not explicitly set**. We recommend setting a non-zero value, which can mitigate spam transactions on the network.

We also urge all validators to take this chance to review their `app.toml` config, especially the **state-sync snapshots** feature. By contributing state-sync snapshots, the synchronization process of new nodes can be speeded up from days to minutes. This will be vital to the growth of our network, as the full chain data size is growing rapidly due to more features and applications being added to LikeCoin chain.

Below are items to be updated in `app.toml`:



```toml
 minimum-gas-prices="1.0nanolike" # set your own price
 [state-sync]
 snapshot-interval=1000 # set non-zero value to enable
 snapshot-keep-recent=2 # set your own value depending on disk space
```

#### Backups

Cosmovisor will backup the `.liked/data` folder to `.liked/data-backup-<date>` after the chain has halted at upgrade height and before the new binary has started.

#### Contingency Steps to Skip or Rollback Upgrades

Below are steps to skip the upgrade forcefully. This workflow can be used under the following circumstances:

* A critical bug is found shortly before upgrade height, thus there is no time to cancel the upgrade on-chain via `CancelSoftwareUpgrade` proposal
* The upgrade failed on mainnet and the community reached consensus to rollback the chain to the state before the upgrade height

To skip an upgrade on short notice, operators shall append `--unsafe-skip-upgrades <upgrade height>` to their cosmovisor launch argument.

**Set launch argument for systemd method**

1. Stop the node by `sudo systemctl stop liked`
2. Edit `/etc/systemd/system/liked.service`
3. Locate line beginning with `ExecStart=`, append `--unsafe-skip-upgrades <upgrade height>` to the end
4. Save the file
5. (For rollback, restore `.liked` folder with additional steps in the next section)
6. Run `sudo systemctl daemon-reload`, then `sudo systemctl restart liked`

**Set launch argument for docker method**

1. Stop the node by `docker-compose down`
2. Edit `docker-compose.yml`
3. Locate `liked-service-cosmovisor` service, edit its `command` field to add `"--unsafe-skip-upgrades", "<upgrade height>",` entries in the array.
4. Save the file
5. (For rollback, restore `.liked` folder with additional steps in the next section)
6. Run `docker-compose up -d`

**Restore `.liked` folder to rollback upgrade**

This is in addition to adding the skip upgrade flag step above.

Point the `current` binary symlink to the previous version (`genesis` for this upgrade):

```shell
 cd ~/.liked/cosmovisor
 rm current
 ln -s $(pwd)/genesis current
 rm -r upgrades/v2.0.0
 rm ~/.liked/data/upgrade-info.json
```

If the community decided to rollback after blocks were produced post-upgrade, we will need to restore the data folder from backup:

```shell
cd ~/.liked
mv data data-backup-failed-upgrade
cp -r data-backup-<date> data
rm ~/.liked/data/upgrade-info.json
```

### Instructions for Upgrade Proposer

#### CI/CD Release

Once a release candidate is validated on devnet / testnet, please tag the commit with version `v2.0.0`. CI will test and build with the tagged commit, then release it on GitHub.

Please also push commits to `release/v2.x` and update branch names in node setup guides.

#### Submit Proposal

The proposer should submit a proposal with below command:

```shell
 ./liked tx gov submit-proposal software-upgrade "v2.0.0" \
 --title "Upgrade LikeCoin chain mainnet to v2.0.0" \
 --description "This proposal is for upgrading the LikeCoin chain mainnet software from fotan-1.1/v1.2.0 to v2.0.0. Full proposal: https://ipfs.io/ipfs/..." \
 --from $ACCOUNT \
 --upgrade-height $UPGRADE_HEIGHT \
 --upgrade-info '{"binaries":{"linux/amd64":"https://github.com/likecoin/likecoin-chain/releases/download/v2.0.0/likecoin-chain_2.0.0_Linux_x86_64.tar.gz","linux/arm64":"https://github.com/likecoin/likecoin-chain/releases/download/v2.0.0/likecoin-chain_2.0.0_Linux_arm64.tar.gz","darwin/amd64":"https://github.com/likecoin/likecoin-chain/releases/download/v2.0.0/likecoin-chain_2.0.0_Darwin_x86_64.tar.gz","darwin/arm64":"https://github.com/likecoin/likecoin-chain/releases/download/v2.0.0/likecoin-chain_2.0.0_Darwin_arm64.tar.gz"}}' \
 --deposit 10000000nanolike \
 --chain-id "likecoin-mainnet-2"
```

The proposal content, especially `upgrade-info` should be validated on testnet beforehand.

Please also refer to the technical documentation on upgrade proposal usage [here](https://github.com/likecoin/likecoin-chain/blob/master/SETUP.md#upgrade-proposal).
