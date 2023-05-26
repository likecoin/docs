---
description: StarFerry is the fourth major upgrade to the LikeCoin chain
---

# ChungKing Upgrade

#### Please join the [#mainnet-validators](https://discord.gg/yGUqtcHGjv) channel.

### Changelog

* Upgrade go lang to 1.19.5
* Upgrade cosmos-sdk to 0.46.12
* Upgrade ibc-go to 5.3.1
* Remove x/nft backport
* Add `full_pay_to_royalty` flag to sell NFT event
* Add deterministic ISCN ID when creating ISCN
* Add custom authz message in iscn and likenft module
* Add feegrant in iscn and likenft module messages

### SDK Upgrade

We will be upgrading to cosmos-sdk 0.46, which contains x/nft(which we already back-ported to sdk 0.45 in last version) and x/group module. Also ledger support for authz module is re-introduced. We will be also upgrading to ibc-go 5.3.1, which is the supported version containing security fix for Huckleberry.

### Fee grant and authz support

We have implement feegrant and authz support for iscn and x/likenft module, enabling better onboard and minting UX for users and more possibility for dApp use cases.

### Miscellaneous update

A new flag `full_pay_to_royalty` is added to NFT sale related events, which allow seller to optionally send all revenue to stakeholders listed in the NFT's royalty config.

ISCN ID can be now calculated deterministically, which allow messages that required ISCN ID as parameter to be batched together with ISCN creation message in one transaction .



### Timeline

| Event            | Time          |
| ---------------- | ------------- |
| Testnet Proposal | 18th May 2023 |
| Testnet Deploy   | 19th May 2023 |
| Mainnet Proposal | W4 May 2023   |
| Mainnet Deploy   | W2 June 2023  |

#### Chain Upgrades List

| Upgrade Name | Binary Version | Binary Path                                   |
| ------------ | -------------- | --------------------------------------------- |
| FoTan        | v1.2.0         | `.liked/cosmovisor/genesis/bin/liked`         |
| LaiChiKok    | v2.0.2         | `.liked/cosmovisor/upgrades/v2.0.0/bin/liked` |
| StarFerry    | v3.0.0         | `.liked/cosmovisor/upgrades/v3.0.0/bin/liked` |
| ChungKing    | v4.0.0         | `.liked/cosmovisor/upgrades/v4.0.0/bin/liked` |

#### System Requirements During Upgrade

The system resources required during the upgrade might be higher than normal operation for data migration tasks. In particular, large amount of memory will be used, and data files will be duplicated for backup. Any machine with less than recommended specification might result in OOM (out of memory) error thus data corruption. Also note that using swap might lengthen the upgrade duration considerably.

Since there is no store migration for this upgrade, we do not expect memory usage to be huge except for data back up.

After the upgrade is applied, the day-to-day resources requirement is same as previously suggested in our Node Setup Guide.

**Recommended**

* 4 CPU Cores
* 16GB RAM + 16GB Swap
* 500GB+ SSD

**Minimum**

* 2 CPU Cores
* 16GB RAM
* 500GB+ SSD

Refer to [this third party guide](https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-20-04) for steps to add swap space.

Using RAM lower than required will likely result a OOM and corruption of data.

Operators who could not arrange a capable machine might opt to temporarily stop validating until the network has upgraded, then catch up to trusted nodes using state sync.

#### Workflow

1. `v4.0.0` is tagged on repo and binary builds are released on github via CI
2. Upgrade proposal is raised on-chain, which specifies the following parameters:
   * Upgrade Name: `v4.0.0`
   * Upgrade Height: 9419200
   *   Upgrade Info:

       ```json
       {
         "binaries": {
           "linux/amd64": "https://github.com/likecoin/likecoin-chain/releases/download/v4.0.0/likecoin-chain_4.0.0_Linux_x86_64.tar.gz",
           "linux/arm64": "https://github.com/likecoin/likecoin-chain/releases/download/v4.0.0/likecoin-chain_4.0.0_Linux_arm64.tar.gz",
           "darwin/amd64": "https://github.com/likecoin/likecoin-chain/releases/download/v4.0.0/likecoin-chain_4.0.0_Darwin_x86_64.tar.gz",
           "darwin/arm64": "https://github.com/likecoin/likecoin-chain/releases/download/v4.0.0/likecoin-chain_4.0.0_Darwin_arm64.tar.gz",
           "windows/amd64": "https://github.com/likecoin/likecoin-chain/releases/download/v4.0.0/likecoin-chain_4.0.0_Windows_x86_64.zip"
         }
       }
       ```
3. After the proposal is approved, operators should place the `v4.0.0` binary at the Cosmovisor upgrades folder BEFORE the upgrade time. Alternatively, operators can configure cosmovisor to download binaries automatically.
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
.liked/cosmovisor/upgrades/v4.0.0/bin/liked
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

Point the `current` binary symlink to the previous version (`v3.0.0` for this upgrade):

```shell
 cd ~/.liked/cosmovisor
 rm current
 ln -s $(pwd)/v3.0.0 current
 rm -r upgrades/v4.0.0
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

Once a release candidate is validated on devnet / testnet, please tag the commit with version `v4.0.0`. CI will test and build with the tagged commit, then release it on GitHub.

Please also push commits to `release/v4.x` and update branch names in node setup guides.

**Submit Proposal**

The proposer should submit a proposal with below command:

```shell
 ./liked tx gov submit-proposal software-upgrade "v4.0.0" \
 --title "Upgrade LikeCoin chain mainnet to v4.0.0" \
 --description "This proposal is for upgrading the LikeCoin chain mainnet software from v3.0.0 to v4.0.0. Full proposal: https://ipfs.io/ipfs/..." \
 --from $ACCOUNT \
 --upgrade-height $UPGRADE_HEIGHT \
 --upgrade-info '{"binaries":{"linux/amd64":"https://github.com/likecoin/likecoin-chain/releases/download/v4.0.0/likecoin-chain_4.0.0_Linux_x86_64.tar.gz?checksum=sha256:79c2307d2550c618092b71877f0b9c6fee6effa5976f436f0cd77c8a1d9f8738","linux/arm64":"https://github.com/likecoin/likecoin-chain/releases/download/v4.0.0/likecoin-chain_4.0.0_Linux_arm64.tar.gz?checksum=sha256:239586638ba9d355ab5e319c3956eefcbab0cbfadf275e137247df474b38d085","darwin/amd64":"https://github.com/likecoin/likecoin-chain/releases/download/v4.0.0/likecoin-chain_4.0.0_Darwin_x86_64.tar.gz?checksum=sha256:617d42523f98ec4c9bb9ed8fc379e77df1af3da9c5162ce790369660e4e851eb","darwin/arm64":"https://github.com/likecoin/likecoin-chain/releases/download/v4.0.0/likecoin-chain_4.0.0_Darwin_arm64.tar.gz?checksum=sha256:589855fbd362317b3df37b5aa2d4c1982e8e9a72f356d0126aa391364cc1355b","windows/amd64":"https://github.com/likecoin/likecoin-chain/releases/download/v4.0.0/likecoin-chain_4.0.0_Windows_x86_64.zip?checksum=sha256:90c09546596378bbf11ffcee09b6c8c7fc047d173316337068ca3859edcfd619"}}' \
 --deposit 10000000nanolike \
 --chain-id "likecoin-mainnet-2"
```

The proposal content, especially `upgrade-info` should be validated on testnet beforehand.

Please also refer to the technical documentation on upgrade proposal usage [here](https://github.com/likecoin/likecoin-chain/blob/master/SETUP.md#upgrade-proposal).
