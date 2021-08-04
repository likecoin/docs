# Useful commands

## Auth

The `auth` module defines basic account logic like sequences.

### Query: Account Info

Query account info, including balances, account number and sequence.

```text
likecli query auth account [ADDRESS]
```

## Bank

The `bank` module mainly defines transfer of coins.

### Transaction: Send

Send coins to recipient.

* \[COINS\] should be formatted like `1000000000nanolike` \(1 LIKE in this example\)

```text
likecli tx send [FROM_ADDRESS_OR_KEY_NAME] [TO_ADDRESS] [COINS]
```

## Staking related modules

There are a few modules related to staking: `staking`, `mint`, `distribution`, `slashing`.

### Transaction: Create Validator

Create validator, so the node with the corresponding consensus key can start to validate blocks.

Others can then delegate to the validator to increase its voting power and receive block rewards and transaction fee as return.

```text
likecli tx staking create-validator [OPTIONS]
```

See `--help` for available options.

### Transaction: Edit Validator

Edit validator info, including moniker, description, identity, website and commission rate.

Commission rate modification is limited by the validators maximum commission rate and maximum commission change rate which are set when creating the validators.

```text
likecli tx staking edit-validator [OPTIONS]
```

See `--help` for available options.

### Transaction: Delegate

Delegate to a validator, increasing its voting power, collecting block rewards and transaction fee as return.

```text
likecli tx staking delegate [VALIDATOR_ADDRESS] --from [DELEGATOR_ADDRESS] [COINS] --chain-id [CHAIN_ID]
```

### Transaction: Redelegate

Move some delegations from one validator to another.

Unlike unbond, this action takes effect immediately and does not need to wait for unbond period.

However, user needs to wait for 3 weeks before the same redelegation can be redelegated again. For example, user delegated to A and then redelegated from A to B, then the user needs to wait for 3 weeks before redelegating from B to C.

```text
likecli tx staking redelegate [FROM_VALIDATOR_ADDRESS] [TO_VALIDATOR_ADDRESS] --from [DELEGATOR_ADDRESS] [COINS] --chain-id [CHAIN_ID]
```

### Transaction: Unbond

Take away some delegations from a validator.

The delegation will enter unbonding state, which is locked for unbond period \(3 weeks\) before moving back into available balance.

```text
likecli tx staking unbond [VALIDATOR_ADDRESS] --from [DELEGATOR_ADDRESS] [COINS] --chain-id [CHAIN_ID]
```

### Transaction: Withdraw Rewards

Get the accumulated rewards from a delegation. Can add the `--commission` flag to also withdraw validator's commission.

```text
likecli tx distribution withdraw-rewards [VALIDATOR_ADDRESS] --from [DELEGATOR_ADDRESS] [--commission] --chain-id [CHAIN_ID]
```

### Transaction: Withdraw All Rewards

Get the accumulated rewards from all delegations among different validators.

```text
likecli tx distribution withdraw-all-rewards --from [DELEGATOR_ADDRESS] --chain-id [CHAIN_ID]
```

### Transaction: Unjail

Unjail validator who got jailed because of downtime.

Note that validators who got jailed because of double signing cannot be unjailed.

```text
likecli tx slashing unjail
```

### Query: Delegations

Get current delegations info from a delegator.

```text
likecli query staking delegations [DELEGATOR_ADDRESS] --chain-id [CHAIN_ID]
```

### Query: Validators

Get current validators info.

```text
likecli query staking validators
```

### Query: Inflation

Get current inflation rate.

```text
likecli query mint inflation
```

### Query: Rewards

Get current rewards which are not yet withdrawn.

```text
likecli query distribution rewards [DELEGATOR_ADDRESS] --chain-id [CHAIN_ID] [OPTIONAL_VALIDATOR_ADDRESS]
```

## Governance

### Transaction: Submit Proposal

Submit a governance proposal, open for deposits before getting into voting.

Proposal content can be supplied either by command arguments or a file.

```text
likecli tx gov submit-proposal [OPTIONS]
```

### Transaction: Deposit

Deposit into an open proposal for voting.

```text
likecli tx gov deposit [PROPOSAL_ID] [COINS]
```

### Transaction: Vote

Vote in a proposal.

```text
likecli tx gov vote [PROPOSAL_ID] [yes|no|abstain]
```

### Query: Proposals

Query proposals.

```text
likecli query gov proposals
```

### Query: Deposits

Query proposal deposits.

```text
likecli query gov deposits [PROPOSAL_ID]
```

### Query: Votes

Query proposal votes.

```text
likecli query gov votes [PROPOSAL_ID]
```

