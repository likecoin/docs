---
description: ChungKing is the fourth major upgrade to the LikeCoin chain
---

# ChungKing++ Upgrade

{% include "../.gitbook/includes/warning.md" %}

#### Please join the [#mainnet-validators](https://discord.gg/yGUqtcHGjv) channel.

### Changelog

* Upgrade ibc-go to 6.3.0
* Upgrade cosmos-sdk to 0.46.16

### IBC Upgrade

This release upgrade ibc module to v6.3.0. This upgrade does not not include any significant features except an ibc-go upgrade for a vulnerability patch.

### Timeline

| Event            | Time            |
| ---------------- | --------------- |
| Testnet Proposal | 8th April 2024  |
| Testnet Deploy   | 10th April 2024 |
| Mainnet Proposal | 12th April 2024 |
| Mainnet Deploy   | 23th April 2024 |

#### Chain Upgrades List

| Upgrade Name | Binary Version | Binary Path                                   |
| ------------ | -------------- | --------------------------------------------- |
| FoTan        | v1.2.0         | `.liked/cosmovisor/genesis/bin/liked`         |
| LaiChiKok    | v2.0.2         | `.liked/cosmovisor/upgrades/v2.0.0/bin/liked` |
| StarFerry    | v3.0.0         | `.liked/cosmovisor/upgrades/v3.0.0/bin/liked` |
| ChungKing    | v4.0.0         | `.liked/cosmovisor/upgrades/v4.0.0/bin/liked` |
| ChungKing+   | v4.1.1         | `.liked/cosmovisor/upgrades/v4.1.1/bin/liked` |
| ChungKing++  | v4.2.0         | `.liked/cosmovisor/upgrades/v4.2.0/bin/liked` |

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

1. `v4.2.0` is tagged on repo and binary builds are released on github via CI
2. Upgrade proposal is raised on-chain, which specifies the following parameters:
   * Upgrade Name: `v4.2.0`
   * Upgrade Height: 14103500
   *   Upgrade Info:

       ```json
       {
         "binaries": {
           "linux/amd64": "https://github.com/likecoin/likecoin-chain/releases/download/v4.2.0/likecoin-chain_4.2.0_Linux_x86_64.tar.gz",
           "linux/arm64": "https://github.com/likecoin/likecoin-chain/releases/download/v4.2.0/likecoin-chain_4.2.0_Linux_arm64.tar.gz",
           "darwin/amd64": "https://github.com/likecoin/likecoin-chain/releases/download/v4.2.0/likecoin-chain_4.2.0_Darwin_x86_64.tar.gz",
           "darwin/arm64": "https://github.com/likecoin/likecoin-chain/releases/download/v4.2.0/likecoin-chain_4.2.0_Darwin_arm64.tar.gz",
           "windows/amd64": "https://github.com/likecoin/likecoin-chain/releases/download/v4.2.0/likecoin-chain_4.2.0_Windows_x86_64.zip"
         }
       }
       ```
3. After the proposal is approved, operators should place the `v4.2.0` binary at the Cosmovisor upgrades folder BEFORE the upgrade time. Alternatively, operators can configure cosmovisor to download binaries automatically.
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
.liked/cosmovisor/upgrades/v4.2.0/bin/liked
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

Point the `current` binary symlink to the previous version (`v4.1.1` for this upgrade):

```shell
 cd ~/.liked/cosmovisor
 rm current
 ln -s $(pwd)/v4.1.1 current
 rm -r upgrades/v4.2.0
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

Once a release candidate is validated on devnet / testnet, please tag the commit with version `v4.2.0`. CI will test and build with the tagged commit, then release it on GitHub.

Please also push commits to `release/v4.x` and update branch names in node setup guides.

**Submit Proposal**

The proposer should submit a proposal with below command:

```shell
 ./liked tx gov submit-legacy-proposal software-upgrade "v4.2.0" \
  --title 'LikeCoin v4.2.0 ChungKing++ Upgrade' \
  --description "LikeCoin ChungKing++ Upgrade\n\nBy voting YES you approve that the chain to do a software upgrade [v4.2.0](https://github.com/likecoin/likecoin-chain/releases/tag/v4.2.0) on block height 14103500, which is estimated to occur on April 23th, around UTC 11:00.\n\n## Upgrade features\n\n- Upgrade ibc-go to 6.3.0\n\n- Upgrade cosmos-sdk to 0.46.16\n\n## Getting prepared for the upgrade\n\nNo state migration is expected for this upgrade. However all nodes are still recommended to have at least 16GB of memory. Not enough memory would result in corrupted data during upgrade.\n\nNode operators are advised to use cosmovisor, please refer to the following guides for setup and upgrade procedure. \n\nhttps://docs.like.co/validator/likecoin-chain-node/setup-a-node#to-existing-operators\n\n## Details of upgrade time\n\nThe proposal targets the upgrade proposal block to be 14103500, anticipated to be at April 23th, around UTC 11:00AM. Note that block times have high variance, so keep monitoring the time.\n\nThe upgrade is anticipated to take less than 60 minutes, during which time, there will not be any on-chain activity on the network.\n\nIn the event of an issue at upgrade time, we should coordinate via the validators channel in Discord.\n\nThis upgrade does not not include any significant features except an ibc-go upgrade for a vulnerability patch.\n\nhttps://app.like.co/view/iscn:%2F%2Flikecoin-chain%2FzLN30V-Jzmq5yDOFnBNlYuYd6u6FiHMTGGt16Qr5vBg\n" \
  --from $ACCOUNT \
  --upgrade-height $UPGRADE_HEIGHT \
  --upgrade-info '{"binaries":{"linux/amd64":"https://github.com/likecoin/likecoin-chain/releases/download/v4.2.0/likecoin-chain_4.2.0_Linux_x86_64.tar.gz?checksum=sha256:07f138489ae4b2d31a95132db3efd1e0848eeb70afe33a89a8a326a1dc0d94c9","linux/arm64":"https://github.com/likecoin/likecoin-chain/releases/download/v4.2.0/likecoin-chain_4.2.0_Linux_arm64.tar.gz?checksum=sha256:2fc26a97b2eb8ac7c6bd2dc453b9bc6b6b301b3e9faeb6b5a1e98e1637b2e34e","darwin/amd64":"https://github.com/likecoin/likecoin-chain/releases/download/v4.2.0/likecoin-chain_4.2.0_Darwin_x86_64.tar.gz?checksum=sha256:a0287b0fcd085908f2b27a829534a0b2a6e47b65a17fd5724f3061ef220b23d9","darwin/arm64":"https://github.com/likecoin/likecoin-chain/releases/download/v4.2.0/likecoin-chain_4.2.0_Darwin_arm64.tar.gz?checksum=sha256:66e845ca29866af10f7ba99a57c3e1ce438de6232a66aa2ca4a726c04cde7de0"}}' \
  --deposit 10000000nanolike \
  --chain-id "likecoin-mainnet-2"
```

The proposal content, especially `upgrade-info` should be validated on testnet beforehand.

Please also refer to the technical documentation on upgrade proposal usage [here](https://github.com/likecoin/likecoin-chain/blob/master/SETUP.md#upgrade-proposal).
