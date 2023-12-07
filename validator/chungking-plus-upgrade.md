---
description: ChungKing is the fourth major upgrade to the LikeCoin chain
---

# ChungKing+ Upgrade

#### Please join the [#mainnet-validators](https://discord.gg/yGUqtcHGjv) channel.

### Changelog

* Upgrade ibc-go to 6.2.1
* Upgrade cosmovisor in container image to 1.5

### IBC Upgrade

This release upgrade ibc module to v6. This is a minor upgrade before the 0.47 sdk upgrade which is expected to take some time for development and testing.

### Timeline

| Event            | Time          |
| ---------------- | ------------- |
| Testnet Proposal | 15th Nov 2023 |
| Testnet Deploy   | 16th Nov 2023 |
| Mainnet Proposal | W4 Nov 2023   |
| Mainnet Deploy   | W2 Dec 2023   |

#### Chain Upgrades List

| Upgrade Name | Binary Version | Binary Path                                   |
| ------------ | -------------- | --------------------------------------------- |
| FoTan        | v1.2.0         | `.liked/cosmovisor/genesis/bin/liked`         |
| LaiChiKok    | v2.0.2         | `.liked/cosmovisor/upgrades/v2.0.0/bin/liked` |
| StarFerry    | v3.0.0         | `.liked/cosmovisor/upgrades/v3.0.0/bin/liked` |
| ChungKing    | v4.0.0         | `.liked/cosmovisor/upgrades/v4.0.0/bin/liked` |
| ChungKing+   | v4.1.1         | `.liked/cosmovisor/upgrades/v4.1.1/bin/liked` |

#### System Requirements During Upgrade

The system resources required during the upgrade might be higher than normal operation for data migration tasks. In particular, large amount of memory will be used, and data files will be duplicated for backup. Any machine with less than recommended specification might result in OOM (out of memory) error thus data corruption. Also note that using swap might lengthen the upgrade duration considerably.

Since there is no store migration for this upgrade, we do not expect memory usage to be huge except for data back up.

After the upgrade is applied, the day-to-day resources requirement is same as previously suggested in our Node Setup Guide.

**Recommended**

* 4 CPU Cores
* 32GB RAM + 16GB Swap
* 500GB+ SSD

**Minimum**

* 2 CPU Cores
* 16GB RAM + 16GB Swap
* 500GB+ SSD

Refer to [this third party guide](https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-20-04) for steps to add swap space.

Using RAM lower than required will likely result a OOM and corruption of data.

Operators who could not arrange a capable machine might opt to temporarily stop validating until the network has upgraded, then catch up to trusted nodes using state sync.

#### Workflow

1. `v4.1.1` is tagged on repo and binary builds are released on github via CI
2. Upgrade proposal is raised on-chain, which specifies the following parameters:
   * Upgrade Name: `v4.1.1`
   * Upgrade Height: 12102100
   *   Upgrade Info:

       ```json
       {
         "binaries": {
           "linux/amd64": "https://github.com/likecoin/likecoin-chain/releases/download/v4.1.1/likecoin-chain_4.1.1_Linux_x86_64.tar.gz",
           "linux/arm64": "https://github.com/likecoin/likecoin-chain/releases/download/v4.1.1/likecoin-chain_4.1.1_Linux_arm64.tar.gz",
           "darwin/amd64": "https://github.com/likecoin/likecoin-chain/releases/download/v4.1.1/likecoin-chain_4.1.1_Darwin_x86_64.tar.gz",
           "darwin/arm64": "https://github.com/likecoin/likecoin-chain/releases/download/v4.1.1/likecoin-chain_4.1.1_Darwin_arm64.tar.gz",
           "windows/amd64": "https://github.com/likecoin/likecoin-chain/releases/download/v4.1.1/likecoin-chain_4.1.1_Windows_x86_64.zip"
         }
       }
       ```
3. After the proposal is approved, operators should place the `v4.1.1` binary at the Cosmovisor upgrades folder BEFORE the upgrade time. Alternatively, operators can configure cosmovisor to download binaries automatically.
4. Cosmovisor will automatically switch binaries at the scheduled block height. Operators will not be required to run migrations or restart chain manually. However, operators are recommended to be present during the upgrade time in case of any unforeseen issues.

#### Instructions for Validator Operators

**Migrate to Cosmovisor**

To support the automatic upgrade, operators should **migrate to host their node with Cosmovisor** beforehand, which is supported since `v1.2.0`. A setup guide with migration instructions is available [here](likecoin-chain-node/setup-a-node/).

Operators can also test their setup and practice the migration flow on testnet before the actual upgrade.

**Upgrading without Cosmovisor**

Although not recommended, it is possible for operators to opt out of using Cosmovisor.

At the upgrade height, the old chain binary will halt with `upgrade needed` panic. Afterwards, operators shall backup their `.liked` folder, then start their node using the new version binary.

**Prepare the next binary ahead of upgrade height**

Once the proposal is approved on-chain, operators should either download or build the next binary version, and place it within the Cosmovisor upgrades folder.

The path to the new binary should be:

```shell
.liked/cosmovisor/upgrades/v4.1.1/bin/liked
```

Alternatively, operators can enable the auto-download feature of Cosmovisor by setting environment variable `DAEMON_ALLOW_DOWNLOAD_BINARIES` to `true`, which is the default if our setup script or docker image was used. To be safe, we recommend you do prepare the binary manually.

**Backups**

Cosmovisor will backup the `.liked/data` folder to `.liked/data-backup-<date>` after the chain has halted at upgrade height and before the new binary has started.

**Contingency Steps to Skip or Rollback Upgrades**

Below are steps to skip the upgrade forcefully. This workflow can be used under the following circumstances:

* A critical bug is found shortly before upgrade height, thus there is no time to cancel the upgrade on-chain via `CancelSoftwareUpgrade` proposal
* The upgrade failed on mainnet and the community reached consensus to rollback the chain to the state before the upgrade height

To skip an upgrade on short notice, operators shall append `--unsafe-skip-upgrades <upgrade height>` to their cosmovisor launch argument.

**Set launch argument for systemd**

1. Stop the node by `sudo systemctl stop liked`
2. Edit `/etc/systemd/system/liked.service`
3. Locate line beginning with `ExecStart=`, append `--unsafe-skip-upgrades <upgrade height>` to the end
4. Save the file
5. (For rollback, restore `.liked` folder with additional steps in the next section)
6. Run `sudo systemctl daemon-reload`, then `sudo systemctl restart liked`

**Restore `.liked` folder to rollback upgrade**

This is in addition to adding the skip upgrade flag step above.

Point the `current` binary symlink to the previous version (`v4.0.0` for this upgrade):

```shell
 cd ~/.liked/cosmovisor
 rm current
 ln -s $(pwd)/v4.0.0 current
 rm -r upgrades/v4.1.1
 rm ~/.liked/data/upgrade-info.json
```

If the community decided to rollback after blocks were produced post-upgrade, we will need to restore the data folder from backup:

```shell
cd ~/.liked
mv data data-backup-failed-upgrade
cp -r data-backup-<date> data
rm ~/.liked/data/upgrade-info.json
```

#### Instructions for Upgrade Proposer

**CI/CD Release**

Once a release candidate is validated on devnet / testnet, please tag the commit with version `v4.1.1`. CI will test and build with the tagged commit, then release it on GitHub.

Please also push commits to `release/v4.x` and update branch names in node setup guides.

**Submit Proposal**

The proposer should submit a proposal with below command:

```shell
 ./liked tx gov submit-legacy-proposal software-upgrade "v4.1.1" \
 --title 'LikeCoin v4.1.1 ChungKing+ Upgrade' \
 --description "LikeCoin ChungKing+ Upgrade\n\nBy voting YES you approve that the chain to do a software upgrade [v4.1.1](https://github.com/likecoin/likecoin-chain/releases/tag/v4.1.1) on block height 12102100, which is estimated to occur on Dec 7th, around UTC 11:00.\n\n## Upgrade features\n\n- Upgrade ibc-go to 6.2.1\n\n- Upgrade cosmovisor in container image to 1.15\n\n## Getting prepared for the upgrade\n\nNo state migration is expected for this upgrade. However all nodes are still recommended to have at least 16GB of memory. Not enough memory would result in corrupted data during upgrade.\n\nNode operators are advised to use cosmovisor, please refer to the following guides for setup and upgrade procedure. Node operators are also advised to upgrade cosmovisor to 1.5.0\n\nhttps://docs.like.co/validator/likecoin-chain-node/setup-a-node#to-existing-operators\n\n## Details of upgrade time\n\nThe proposal targets the upgrade proposal block to be 12102100, anticipated to be at Dec 7th, around UTC 11:00AM. Note that block times have high variance, so keep monitoring the time.\n\nThe upgrade is anticipated to take less than 60 minutes, during which time, there will not be any on-chain activity on the network.\n\nIn the event of an issue at upgrade time, we should coordinate via the validators channel in discord.\n\nThis upgrade does not not include any significant features except the IBC v6 upgrade. This is meant to be a final minor upgrade before the cosmos-sdk 0.47 upgrade, which is expected to contain huge changes.\n\nhttps://app.like.co/view/iscn:%2F%2Flikecoin-chain%2FcfDXloB0gTfMgoHM0WAwzyqr1vUXD57w6Jac9BtoDhE%2F1\n" \
 --from $ACCOUNT \
 --upgrade-height $UPGRADE_HEIGHT \
  --upgrade-info '{"binaries":{"linux/amd64":"https://github.com/likecoin/likecoin-chain/releases/download/v4.1.1/likecoin-chain_4.1.1_Linux_x86_64.tar.gz?checksum=sha256:82b8a66959998dae7e249b0b0a29c6bdca118638e1cad5bc5c8821002f6051cc","linux/arm64":"https://github.com/likecoin/likecoin-chain/releases/download/v4.1.1/likecoin-chain_4.1.1_Linux_arm64.tar.gz?checksum=sha256:8635ce8e7e3c1bf0599469a75fd1579c10c7e593a35bff6572cc1c66a9ca6072","darwin/amd64":"https://github.com/likecoin/likecoin-chain/releases/download/v4.1.1/likecoin-chain_4.1.1_Darwin_x86_64.tar.gz?checksum=sha256:17a7532031adeffdae3bbeb0bed2f8e159f16889ffd734826e34a595411c0953","darwin/arm64":"https://github.com/likecoin/likecoin-chain/releases/download/v4.1.1/likecoin-chain_4.1.1_Darwin_arm64.tar.gz?checksum=sha256:35da3c84e447431bf6c16a1c11f8993fd013cc161578aa5fef855c59f72caa39"}}' \
 --deposit 10000000nanolike \
 --chain-id "likecoin-mainnet-2"
```

The proposal content, especially `upgrade-info` should be validated on testnet beforehand.

Please also refer to the technical documentation on upgrade proposal usage [here](https://github.com/likecoin/likecoin-chain/blob/master/SETUP.md#upgrade-proposal).
