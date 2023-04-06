# ISCN API

## LCD API

Please refer to [iscn query definition](https://github.com/likecoin/likecoin-chain/blob/master/proto/likechain/iscn/query.proto#L11) for most updated LCD API

#### Query all ISCN related transactions&#x20;

[`https://mainnet-node.like.co/txs?message.module=iscn`](https://mainnet-node.like.co/txs?message.module=iscn)

#### Query ISCN by ID

[`https://mainnet-node.like.co/iscn/records/id?iscn_id=iscn://likecoin-chain/dLbKMa8EVO9RF4UmoWKk2ocUq7IsxMcnQL1_Ps5Vg80/1`](https://mainnet-node.like.co/iscn/records/id?iscn\_id=iscn://likecoin-chain/dLbKMa8EVO9RF4UmoWKk2ocUq7IsxMcnQL1\_Ps5Vg80/1)

#### Query ISCN by ID prefix

&#x20;[`https://mainnet-node.like.co/iscn/records/id?iscn_id=iscn://likecoin-chain/dLbKMa8EVO9RF4UmoWKk2ocUq7IsxMcnQL1_Ps5Vg80`](https://mainnet-node.like.co/iscn/records/id?iscn\_id=iscn://likecoin-chain/dLbKMa8EVO9RF4UmoWKk2ocUq7IsxMcnQL1\_Ps5Vg80)&#x20;

#### Query ISCN by fingerprint&#x20;

[`https://mainnet-node.like.co/iscn/records/fingerprint?fingerprint=ipfs://QmPiX4izgDNyJJRnd8V5ei5ce58dsxErpNVre5jcMPBARG`](https://mainnet-node.like.co/iscn/records/fingerprint?fingerprint=ipfs://QmPiX4izgDNyJJRnd8V5ei5ce58dsxErpNVre5jcMPBARG)&#x20;

#### Query ISCN by owner&#x20;

[`https://mainnet-node.like.co/iscn/records/owner?owner=cosmos1sf2sc6t37xhd3m0dcaq6h5dz22mtru2ugdwp0v`](https://mainnet-node.like.co/iscn/records/owner?owner=cosmos1sf2sc6t37xhd3m0dcaq6h5dz22mtru2ugdwp0v)&#x20;

## Index Query API

The API provided by [likecoin-chain-tx-indexer](https://github.com/likecoin/likecoin-chain-tx-indexer) provides extra compound query for ISCN\
\
e.g. [https://mainnet-node.like.co/iscn/records?owner=cosmos1ykkpc0dnetfsya88f5nrdd7p57kplaw8sva6pj\&keywords=%E9%A6%99%E6%B8%AF\&limit=5\&page=2](https://mainnet-node.like.co/iscn/records?owner=cosmos1ykkpc0dnetfsya88f5nrdd7p57kplaw8sva6pj\&keywords=%E9%A6%99%E6%B8%AF\&limit=5\&page=2)

Please refer to [examples in chain indexer repository](https://github.com/likecoin/likecoin-chain-tx-indexer/blob/master/examples/iscn.md).\
\
