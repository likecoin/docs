# Syncing from genesis

If have any reason not using statesync and opt to sync from the genesis, here is some notes for you.

For replacing binary at cosmovisor, download the respective binary and copy to this location:`.liked/cosmovisor/current/bin/liked`

#### Mainnet

Genesis: https://raw.githubusercontent.com/likecoin/mainnet/master/genesis.json

* v1.2.0
* v2.0.0
  * The upgrade should be automated by cosmovisor at height 3,692,800
* v2.0.2
  * You should replace v2.0.0 with v2.0.2 manually after the upgrade.
* v3.0.0
  * The upgrade should be automated by cosmovisor at height 4,810,000

#### Testnet

Genesis: https://raw.githubusercontent.com/likecoin/testnets/master/likecoin-public-testnet-5/genesis.json

* v1.2.0
* v2.0.0
  * The upgrade should be automated by cosmovisor at height 159,500
* v2.0.2
  * You should replace v2.0.0 with v2.0.2 manually after the upgrade.
* v3.0.0
  * The upgrade will be fail to be automated by cosmovisor at height 1505000 (Due to wrong proposal parameter, not the bugs in the binary)
  * You will have to replace the the binary with a hotfix: [https://github.com/oursky/likecoin-chain/releases/tag/v3.0.0-rc1-hotfix-testnet-handler](https://github.com/oursky/likecoin-chain/releases/tag/v3.0.0-rc1-hotfix-testnet-handler) . The hotfix match the proposal parameter.
