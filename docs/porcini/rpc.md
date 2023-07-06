---
title: JSON-RPC
---

The following sections contain known RPC methods that may be available on specific nodes (depending on configuration and available pallets) and allow you to interact with the actual node, query, and submit.

- **[author](#author)**

- **[babe](#babe)**

- **[chain](#chain)**

- **[childstate](#childstate)**

- **[dex](#dex)**

- **[eth](#eth)**

- **[eth/net](#eth/net)**

- **[eth/web3](#eth/web3)**

- **[ethy](#ethy)**

- **[grandpa](#grandpa)**

- **[nft](#nft)**

- **[offchain](#offchain)**

- **[payment](#payment)**

- **[rpc](#rpc)**

- **[state](#state)**

- **[system](#system)**


___


## author
 
### hasKey(publicKey: `Bytes`, keyType: `Text`): `bool`
- **interface**: `api.rpc.author.hasKey`
- **jsonrpc**: `author_hasKey`
- **summary**: Returns true if the keystore has private keys for the given public key and key type.
- **unsafe**: This method is only active with appropriate flags
 
### hasSessionKeys(sessionKeys: `Bytes`): `bool`
- **interface**: `api.rpc.author.hasSessionKeys`
- **jsonrpc**: `author_hasSessionKeys`
- **summary**: Returns true if the keystore has private keys for the given session public keys.
- **unsafe**: This method is only active with appropriate flags
 
### insertKey(keyType: `Text`, suri: `Text`, publicKey: `Bytes`): `Bytes`
- **interface**: `api.rpc.author.insertKey`
- **jsonrpc**: `author_insertKey`
- **summary**: Insert a key into the keystore.
- **unsafe**: This method is only active with appropriate flags
 
### pendingExtrinsics(): `Vec<Extrinsic>`
- **interface**: `api.rpc.author.pendingExtrinsics`
- **jsonrpc**: `author_pendingExtrinsics`
- **summary**: Returns all pending extrinsics, potentially grouped by sender
 
### removeExtrinsic(bytesOrHash: `Vec<ExtrinsicOrHash>`): `Vec<Hash>`
- **interface**: `api.rpc.author.removeExtrinsic`
- **jsonrpc**: `author_removeExtrinsic`
- **summary**: Remove given extrinsic from the pool and temporarily ban it to prevent reimporting
- **unsafe**: This method is only active with appropriate flags
 
### rotateKeys(): `Bytes`
- **interface**: `api.rpc.author.rotateKeys`
- **jsonrpc**: `author_rotateKeys`
- **summary**: Generate new session keys and returns the corresponding public keys
- **unsafe**: This method is only active with appropriate flags
 
### submitAndWatchExtrinsic(extrinsic: `Extrinsic`): `ExtrinsicStatus`
- **interface**: `api.rpc.author.submitAndWatchExtrinsic`
- **jsonrpc**: `author_submitAndWatchExtrinsic`
- **summary**: Submit and subscribe to watch an extrinsic until unsubscribed
 
### submitExtrinsic(extrinsic: `Extrinsic`): `Hash`
- **interface**: `api.rpc.author.submitExtrinsic`
- **jsonrpc**: `author_submitExtrinsic`
- **summary**: Submit a fully formatted extrinsic for block inclusion

___


## babe
 
### epochAuthorship(): `HashMap<AuthorityId, EpochAuthorship>`
- **interface**: `api.rpc.babe.epochAuthorship`
- **jsonrpc**: `babe_epochAuthorship`
- **summary**: Returns data about which slots (primary or secondary) can be claimed in the current epoch with the keys in the keystore
- **unsafe**: This method is only active with appropriate flags

___


## chain
 
### getBlock(hash?: `BlockHash`): `SignedBlock`
- **interface**: `api.rpc.chain.getBlock`
- **jsonrpc**: `chain_getBlock`
- **summary**: Get header and body of a relay chain block
 
### getBlockHash(blockNumber?: `BlockNumber`): `BlockHash`
- **interface**: `api.rpc.chain.getBlockHash`
- **jsonrpc**: `chain_getBlockHash`
- **summary**: Get the block hash for a specific block
 
### getFinalizedHead(): `BlockHash`
- **interface**: `api.rpc.chain.getFinalizedHead`
- **jsonrpc**: `chain_getFinalizedHead`
- **summary**: Get hash of the last finalized block in the canon chain
 
### getHeader(hash?: `BlockHash`): `Header`
- **interface**: `api.rpc.chain.getHeader`
- **jsonrpc**: `chain_getHeader`
- **summary**: Retrieves the header for a specific block
 
### subscribeAllHeads(): `Header`
- **interface**: `api.rpc.chain.subscribeAllHeads`
- **jsonrpc**: `chain_subscribeAllHeads`
- **summary**: Retrieves the newest header via subscription
 
### subscribeFinalizedHeads(): `Header`
- **interface**: `api.rpc.chain.subscribeFinalizedHeads`
- **jsonrpc**: `chain_subscribeFinalizedHeads`
- **summary**: Retrieves the best finalized header via subscription
 
### subscribeNewHeads(): `Header`
- **interface**: `api.rpc.chain.subscribeNewHeads`
- **jsonrpc**: `chain_subscribeNewHeads`
- **summary**: Retrieves the best header via subscription

___


## childstate
 
### getKeys(childKey: `PrefixedStorageKey`, prefix: `StorageKey`, at?: `Hash`): `Vec<StorageKey>`
- **interface**: `api.rpc.childstate.getKeys`
- **jsonrpc**: `childstate_getKeys`
- **summary**: Returns the keys with prefix from a child storage, leave empty to get all the keys
 
### getKeysPaged(childKey: `PrefixedStorageKey`, prefix: `StorageKey`, count: `u32`, startKey?: `StorageKey`, at?: `Hash`): `Vec<StorageKey>`
- **interface**: `api.rpc.childstate.getKeysPaged`
- **jsonrpc**: `childstate_getKeysPaged`
- **summary**: Returns the keys with prefix from a child storage with pagination support
 
### getStorage(childKey: `PrefixedStorageKey`, key: `StorageKey`, at?: `Hash`): `Option<StorageData>`
- **interface**: `api.rpc.childstate.getStorage`
- **jsonrpc**: `childstate_getStorage`
- **summary**: Returns a child storage entry at a specific block state
 
### getStorageEntries(childKey: `PrefixedStorageKey`, keys: `Vec<StorageKey>`, at?: `Hash`): `Vec<Option<StorageData>>`
- **interface**: `api.rpc.childstate.getStorageEntries`
- **jsonrpc**: `childstate_getStorageEntries`
- **summary**: Returns child storage entries for multiple keys at a specific block state
 
### getStorageHash(childKey: `PrefixedStorageKey`, key: `StorageKey`, at?: `Hash`): `Option<Hash>`
- **interface**: `api.rpc.childstate.getStorageHash`
- **jsonrpc**: `childstate_getStorageHash`
- **summary**: Returns the hash of a child storage entry at a block state
 
### getStorageSize(childKey: `PrefixedStorageKey`, key: `StorageKey`, at?: `Hash`): `Option<u64>`
- **interface**: `api.rpc.childstate.getStorageSize`
- **jsonrpc**: `childstate_getStorageSize`
- **summary**: Returns the size of a child storage entry at a block state

___


## dex
 
### getAmountsIn(amountOut: `Balance`, path: `Vec<AssetId>`): `Json`
- **interface**: `api.rpc.dex.getAmountsIn`
- **jsonrpc**: `dex_getAmountsIn`
- **summary**: Given an array of AssetIds, return amounts in for an amount out
 
### getAmountsOut(amountIn: `Balance`, path: `Vec<AssetId>`): `Json`
- **interface**: `api.rpc.dex.getAmountsOut`
- **jsonrpc**: `dex_getAmountsOut`
- **summary**: Given an array of AssetIds, return amounts out for an amount in
 
### getLPTokenID(assetA: `AssetId`, assetB: `AssetId`): `Json`
- **interface**: `api.rpc.dex.getLPTokenID`
- **jsonrpc**: `dex_getLPTokenID`
- **summary**: Given two AssetIds, return liquidity token created for the pair
 
### getLiquidity(assetA: `AssetId`, assetB: `AssetId`): `Json`
- **interface**: `api.rpc.dex.getLiquidity`
- **jsonrpc**: `dex_getLiquidity`
- **summary**: Given two AssetIds, return liquidity
 
### getTradingPairStatus(assetA: `AssetId`, assetB: `AssetId`): `Json`
- **interface**: `api.rpc.dex.getTradingPairStatus`
- **jsonrpc**: `dex_getTradingPairStatus`
- **summary**: Given two AssetIds, return whether trading pair is enabled or disabled
 
### quote(amountA: `u128`, reserveA: `u128`, reserveB: `u128`): `Json`
- **interface**: `api.rpc.dex.quote`
- **jsonrpc**: `dex_quote`
- **summary**: Given some amount of an asset and pair reserves, returns an equivalent amount of the other asset

___


## eth
 
### accounts(): `Vec<H160>`
- **interface**: `api.rpc.eth.accounts`
- **jsonrpc**: `eth_accounts`
- **summary**: Returns accounts list.
 
### blockNumber(): `U256`
- **interface**: `api.rpc.eth.blockNumber`
- **jsonrpc**: `eth_blockNumber`
- **summary**: Returns the blockNumber
 
### call(request: `EthCallRequest`, number?: `BlockNumber`): `Bytes`
- **interface**: `api.rpc.eth.call`
- **jsonrpc**: `eth_call`
- **summary**: Call contract, returning the output data.
 
### chainId(): `U64`
- **interface**: `api.rpc.eth.chainId`
- **jsonrpc**: `eth_chainId`
- **summary**: Returns the chain ID used for transaction signing at the current best block. None is returned if not available.
 
### coinbase(): `H160`
- **interface**: `api.rpc.eth.coinbase`
- **jsonrpc**: `eth_coinbase`
- **summary**: Returns block author.
 
### estimateGas(request: `EthCallRequest`, number?: `BlockNumber`): `U256`
- **interface**: `api.rpc.eth.estimateGas`
- **jsonrpc**: `eth_estimateGas`
- **summary**: Estimate gas needed for execution of given contract.
 
### feeHistory(blockCount: `U256`, newestBlock: `BlockNumber`, rewardPercentiles: `Option<Vec<f64>>`): `EthFeeHistory`
- **interface**: `api.rpc.eth.feeHistory`
- **jsonrpc**: `eth_feeHistory`
- **summary**: Returns fee history for given block count & reward percentiles
 
### gasPrice(): `U256`
- **interface**: `api.rpc.eth.gasPrice`
- **jsonrpc**: `eth_gasPrice`
- **summary**: Returns current gas price.
 
### getBalance(address: `H160`, number?: `BlockNumber`): `U256`
- **interface**: `api.rpc.eth.getBalance`
- **jsonrpc**: `eth_getBalance`
- **summary**: Returns balance of the given account.
 
### getBlockByHash(hash: `H256`, full: `bool`): `Option<EthRichBlock>`
- **interface**: `api.rpc.eth.getBlockByHash`
- **jsonrpc**: `eth_getBlockByHash`
- **summary**: Returns block with given hash.
 
### getBlockByNumber(block: `BlockNumber`, full: `bool`): `Option<EthRichBlock>`
- **interface**: `api.rpc.eth.getBlockByNumber`
- **jsonrpc**: `eth_getBlockByNumber`
- **summary**: Returns block with given number.
 
### getBlockTransactionCountByHash(hash: `H256`): `U256`
- **interface**: `api.rpc.eth.getBlockTransactionCountByHash`
- **jsonrpc**: `eth_getBlockTransactionCountByHash`
- **summary**: Returns the number of transactions in a block with given hash.
 
### getBlockTransactionCountByNumber(block: `BlockNumber`): `U256`
- **interface**: `api.rpc.eth.getBlockTransactionCountByNumber`
- **jsonrpc**: `eth_getBlockTransactionCountByNumber`
- **summary**: Returns the number of transactions in a block with given block number.
 
### getCode(address: `H160`, number?: `BlockNumber`): `Bytes`
- **interface**: `api.rpc.eth.getCode`
- **jsonrpc**: `eth_getCode`
- **summary**: Returns the code at given address at given time (block number).
 
### getFilterChanges(index: `U256`): `EthFilterChanges`
- **interface**: `api.rpc.eth.getFilterChanges`
- **jsonrpc**: `eth_getFilterChanges`
- **summary**: Returns filter changes since last poll.
 
### getFilterLogs(index: `U256`): `Vec<EthLog>`
- **interface**: `api.rpc.eth.getFilterLogs`
- **jsonrpc**: `eth_getFilterLogs`
- **summary**: Returns all logs matching given filter (in a range 'from' - 'to').
 
### getLogs(filter: `EthFilter`): `Vec<EthLog>`
- **interface**: `api.rpc.eth.getLogs`
- **jsonrpc**: `eth_getLogs`
- **summary**: Returns logs matching given filter object.
 
### getStorageAt(address: `H160`, index: `U256`, number?: `BlockNumber`): `H256`
- **interface**: `api.rpc.eth.getStorageAt`
- **jsonrpc**: `eth_getStorageAt`
- **summary**: Returns content of the storage at given address.
 
### getTransactionByBlockHashAndIndex(hash: `H256`, index: `U256`): `EthTransaction`
- **interface**: `api.rpc.eth.getTransactionByBlockHashAndIndex`
- **jsonrpc**: `eth_getTransactionByBlockHashAndIndex`
- **summary**: Returns transaction at given block hash and index.
 
### getTransactionByBlockNumberAndIndex(number: `BlockNumber`, index: `U256`): `EthTransaction`
- **interface**: `api.rpc.eth.getTransactionByBlockNumberAndIndex`
- **jsonrpc**: `eth_getTransactionByBlockNumberAndIndex`
- **summary**: Returns transaction by given block number and index.
 
### getTransactionByHash(hash: `H256`): `EthTransaction`
- **interface**: `api.rpc.eth.getTransactionByHash`
- **jsonrpc**: `eth_getTransactionByHash`
- **summary**: Get transaction by its hash.
 
### getTransactionCount(address: `H160`, number?: `BlockNumber`): `U256`
- **interface**: `api.rpc.eth.getTransactionCount`
- **jsonrpc**: `eth_getTransactionCount`
- **summary**: Returns the number of transactions sent from given address at given time (block number).
 
### getTransactionReceipt(hash: `H256`): `EthReceipt`
- **interface**: `api.rpc.eth.getTransactionReceipt`
- **jsonrpc**: `eth_getTransactionReceipt`
- **summary**: Returns transaction receipt by transaction hash.
 
### getUncleByBlockHashAndIndex(hash: `H256`, index: `U256`): `EthRichBlock`
- **interface**: `api.rpc.eth.getUncleByBlockHashAndIndex`
- **jsonrpc**: `eth_getUncleByBlockHashAndIndex`
- **summary**: Returns an uncles at given block and index.
 
### getUncleByBlockNumberAndIndex(number: `BlockNumber`, index: `U256`): `EthRichBlock`
- **interface**: `api.rpc.eth.getUncleByBlockNumberAndIndex`
- **jsonrpc**: `eth_getUncleByBlockNumberAndIndex`
- **summary**: Returns an uncles at given block and index.
 
### getUncleCountByBlockHash(hash: `H256`): `U256`
- **interface**: `api.rpc.eth.getUncleCountByBlockHash`
- **jsonrpc**: `eth_getUncleCountByBlockHash`
- **summary**: Returns the number of uncles in a block with given hash.
 
### getUncleCountByBlockNumber(number: `BlockNumber`): `U256`
- **interface**: `api.rpc.eth.getUncleCountByBlockNumber`
- **jsonrpc**: `eth_getUncleCountByBlockNumber`
- **summary**: Returns the number of uncles in a block with given block number.
 
### getWork(): `EthWork`
- **interface**: `api.rpc.eth.getWork`
- **jsonrpc**: `eth_getWork`
- **summary**: Returns the hash of the current block, the seedHash, and the boundary condition to be met.
 
### hashrate(): `U256`
- **interface**: `api.rpc.eth.hashrate`
- **jsonrpc**: `eth_hashrate`
- **summary**: Returns the number of hashes per second that the node is mining with.
 
### maxPriorityFeePerGas(): `U256`
- **interface**: `api.rpc.eth.maxPriorityFeePerGas`
- **jsonrpc**: `eth_maxPriorityFeePerGas`
- **summary**: Returns max priority fee per gas
 
### mining(): `bool`
- **interface**: `api.rpc.eth.mining`
- **jsonrpc**: `eth_mining`
- **summary**: Returns true if client is actively mining new blocks.
 
### newBlockFilter(): `U256`
- **interface**: `api.rpc.eth.newBlockFilter`
- **jsonrpc**: `eth_newBlockFilter`
- **summary**: Returns id of new block filter.
 
### newFilter(filter: `EthFilter`): `U256`
- **interface**: `api.rpc.eth.newFilter`
- **jsonrpc**: `eth_newFilter`
- **summary**: Returns id of new filter.
 
### newPendingTransactionFilter(): `U256`
- **interface**: `api.rpc.eth.newPendingTransactionFilter`
- **jsonrpc**: `eth_newPendingTransactionFilter`
- **summary**: Returns id of new block filter.
 
### protocolVersion(): `u64`
- **interface**: `api.rpc.eth.protocolVersion`
- **jsonrpc**: `eth_protocolVersion`
- **summary**: Returns protocol version encoded as a string (quotes are necessary).
 
### sendRawTransaction(bytes: `Bytes`): `H256`
- **interface**: `api.rpc.eth.sendRawTransaction`
- **jsonrpc**: `eth_sendRawTransaction`
- **summary**: Sends signed transaction, returning its hash.
 
### sendTransaction(tx: `EthTransactionRequest`): `H256`
- **interface**: `api.rpc.eth.sendTransaction`
- **jsonrpc**: `eth_sendTransaction`
- **summary**: Sends transaction; will block waiting for signer to return the transaction hash
 
### submitHashrate(index: `U256`, hash: `H256`): `bool`
- **interface**: `api.rpc.eth.submitHashrate`
- **jsonrpc**: `eth_submitHashrate`
- **summary**: Used for submitting mining hashrate.
 
### submitWork(nonce: `H64`, headerHash: `H256`, mixDigest: `H256`): `bool`
- **interface**: `api.rpc.eth.submitWork`
- **jsonrpc**: `eth_submitWork`
- **summary**: Used for submitting a proof-of-work solution.
 
### subscribe(kind: `EthSubKind`, params?: `EthSubParams`): `Null`
- **interface**: `api.rpc.eth.subscribe`
- **jsonrpc**: `eth_subscribe`
- **summary**: Subscribe to Eth subscription.
 
### syncing(): `EthSyncStatus`
- **interface**: `api.rpc.eth.syncing`
- **jsonrpc**: `eth_syncing`
- **summary**: Returns an object with data about the sync status or false.
 
### uninstallFilter(index: `U256`): `bool`
- **interface**: `api.rpc.eth.uninstallFilter`
- **jsonrpc**: `eth_uninstallFilter`
- **summary**: Uninstalls filter.

___


## eth/net
 
### listening(): `bool`
- **interface**: `api.rpc.net.listening`
- **jsonrpc**: `net_listening`
- **summary**: Returns true if client is actively listening for network connections. Otherwise false.
 
### peerCount(): `Text`
- **interface**: `api.rpc.net.peerCount`
- **jsonrpc**: `net_peerCount`
- **summary**: Returns number of peers connected to node.
 
### version(): `Text`
- **interface**: `api.rpc.net.version`
- **jsonrpc**: `net_version`
- **summary**: Returns protocol version.

___


## eth/web3
 
### clientVersion(): `Text`
- **interface**: `api.rpc.web3.clientVersion`
- **jsonrpc**: `web3_clientVersion`
- **summary**: Returns current client version.
 
### sha3(data: `Bytes`): `H256`
- **interface**: `api.rpc.web3.sha3`
- **jsonrpc**: `web3_sha3`
- **summary**: Returns sha3 of the given data

___


## ethy
 
### getEventProof(eventId: `EventProofId`): `Option<EthEventProofResponse>`
- **interface**: `api.rpc.ethy.getEventProof`
- **jsonrpc**: `ethy_getEventProof`
- **summary**: Get ETH event proof for event Id
 
### getXrplTxProof(eventId: `EventProofId`): `Option<XrplEventProofResponse>`
- **interface**: `api.rpc.ethy.getXrplTxProof`
- **jsonrpc**: `ethy_getXrplTxProof`
- **summary**: Get XRPL event proof for event Id
 
### subscribeEventProofs(): `Null`
- **interface**: `api.rpc.ethy.subscribeEventProofs`
- **jsonrpc**: `ethy_subscribeEventProofs`
- **summary**: Subscribe to Eth event proof.

___


## grandpa
 
### proveFinality(blockNumber: `BlockNumber`): `Option<EncodedFinalityProofs>`
- **interface**: `api.rpc.grandpa.proveFinality`
- **jsonrpc**: `grandpa_proveFinality`
- **summary**: Prove finality for the given block number, returning the Justification for the last block in the set.
 
### roundState(): `ReportedRoundStates`
- **interface**: `api.rpc.grandpa.roundState`
- **jsonrpc**: `grandpa_roundState`
- **summary**: Returns the state of the current best round state as well as the ongoing background rounds
 
### subscribeJustifications(): `JustificationNotification`
- **interface**: `api.rpc.grandpa.subscribeJustifications`
- **jsonrpc**: `grandpa_subscribeJustifications`
- **summary**: Subscribes to grandpa justifications

___


## nft
 
### ownedTokens(collectionId: `CollectionUuid`, who: `AccountId`, cursor: `SerialNumber`, limit: `u16`): `Json`
- **interface**: `api.rpc.nft.ownedTokens`
- **jsonrpc**: `nft_ownedTokens`
- **summary**: Get all NFTs owned by an account
 
### tokenUri(tokenId: `TokenId`): `Json`
- **interface**: `api.rpc.nft.tokenUri`
- **jsonrpc**: `nft_tokenUri`
- **summary**: Get the URI of a token

___


## offchain
 
### localStorageGet(kind: `StorageKind`, key: `Bytes`): `Option<Bytes>`
- **interface**: `api.rpc.offchain.localStorageGet`
- **jsonrpc**: `offchain_localStorageGet`
- **summary**: Get offchain local storage under given key and prefix
- **unsafe**: This method is only active with appropriate flags
 
### localStorageSet(kind: `StorageKind`, key: `Bytes`, value: `Bytes`): `Null`
- **interface**: `api.rpc.offchain.localStorageSet`
- **jsonrpc**: `offchain_localStorageSet`
- **summary**: Set offchain local storage under given key and prefix
- **unsafe**: This method is only active with appropriate flags

___


## payment
 
### queryFeeDetails(extrinsic: `Bytes`, at?: `BlockHash`): `FeeDetails`
- **interface**: `api.rpc.payment.queryFeeDetails`
- **jsonrpc**: `payment_queryFeeDetails`
- **summary**: Query the detailed fee of a given encoded extrinsic
- **deprecated**: Use `api.call.transactionPaymentApi.queryFeeDetails` instead
 
### queryInfo(extrinsic: `Bytes`, at?: `BlockHash`): `RuntimeDispatchInfoV1`
- **interface**: `api.rpc.payment.queryInfo`
- **jsonrpc**: `payment_queryInfo`
- **summary**: Retrieves the fee information for an encoded extrinsic
- **deprecated**: Use `api.call.transactionPaymentApi.queryInfo` instead

___


## rpc
 
### methods(): `RpcMethods`
- **interface**: `api.rpc.rpc.methods`
- **jsonrpc**: `rpc_methods`
- **summary**: Retrieves the list of RPC methods that are exposed by the node

___


## state
 
### call(method: `Text`, data: `Bytes`, at?: `BlockHash`): `Bytes`
- **interface**: `api.rpc.state.call`
- **jsonrpc**: `state_call`
- **summary**: Perform a call to a builtin on the chain
 
### getChildReadProof(childStorageKey: `PrefixedStorageKey`, keys: `Vec<StorageKey>`, at?: `BlockHash`): `ReadProof`
- **interface**: `api.rpc.state.getChildReadProof`
- **jsonrpc**: `state_getChildReadProof`
- **summary**: Returns proof of storage for child key entries at a specific block state.
 
### getKeys(key: `StorageKey`, at?: `BlockHash`): `Vec<StorageKey>`
- **interface**: `api.rpc.state.getKeys`
- **jsonrpc**: `state_getKeys`
- **summary**: Retrieves the keys with a certain prefix
- **deprecated**: Use `api.rpc.state.getKeysPaged` to retrieve keys
 
### getKeysPaged(key: `StorageKey`, count: `u32`, startKey?: `StorageKey`, at?: `BlockHash`): `Vec<StorageKey>`
- **interface**: `api.rpc.state.getKeysPaged`
- **jsonrpc**: `state_getKeysPaged`
- **summary**: Returns the keys with prefix with pagination support.
 
### getMetadata(at?: `BlockHash`): `Metadata`
- **interface**: `api.rpc.state.getMetadata`
- **jsonrpc**: `state_getMetadata`
- **summary**: Returns the runtime metadata
 
### getPairs(prefix: `StorageKey`, at?: `BlockHash`): `Vec<KeyValue>`
- **interface**: `api.rpc.state.getPairs`
- **jsonrpc**: `state_getPairs`
- **summary**: Returns the keys with prefix, leave empty to get all the keys (deprecated: Use getKeysPaged)
- **deprecated**: Use `api.rpc.state.getKeysPaged` to retrieve keys
- **unsafe**: This method is only active with appropriate flags
 
### getReadProof(keys: `Vec<StorageKey>`, at?: `BlockHash`): `ReadProof`
- **interface**: `api.rpc.state.getReadProof`
- **jsonrpc**: `state_getReadProof`
- **summary**: Returns proof of storage entries at a specific block state
 
### getRuntimeVersion(at?: `BlockHash`): `RuntimeVersion`
- **interface**: `api.rpc.state.getRuntimeVersion`
- **jsonrpc**: `state_getRuntimeVersion`
- **summary**: Get the runtime version
 
### getStorage(key: `StorageKey`, at?: `BlockHash`): `StorageData`
- **interface**: `api.rpc.state.getStorage`
- **jsonrpc**: `state_getStorage`
- **summary**: Retrieves the storage for a key
 
### getStorageHash(key: `StorageKey`, at?: `BlockHash`): `Hash`
- **interface**: `api.rpc.state.getStorageHash`
- **jsonrpc**: `state_getStorageHash`
- **summary**: Retrieves the storage hash
 
### getStorageSize(key: `StorageKey`, at?: `BlockHash`): `u64`
- **interface**: `api.rpc.state.getStorageSize`
- **jsonrpc**: `state_getStorageSize`
- **summary**: Retrieves the storage size
 
### queryStorage(keys: `Vec<StorageKey>`, fromBlock: `Hash`, toBlock?: `BlockHash`): `Vec<StorageChangeSet>`
- **interface**: `api.rpc.state.queryStorage`
- **jsonrpc**: `state_queryStorage`
- **summary**: Query historical storage entries (by key) starting from a start block
- **unsafe**: This method is only active with appropriate flags
 
### queryStorageAt(keys: `Vec<StorageKey>`, at?: `BlockHash`): `Vec<StorageChangeSet>`
- **interface**: `api.rpc.state.queryStorageAt`
- **jsonrpc**: `state_queryStorageAt`
- **summary**: Query storage entries (by key) starting at block hash given as the second parameter
 
### subscribeRuntimeVersion(): `RuntimeVersion`
- **interface**: `api.rpc.state.subscribeRuntimeVersion`
- **jsonrpc**: `state_subscribeRuntimeVersion`
- **summary**: Retrieves the runtime version via subscription
 
### subscribeStorage(keys?: `Vec<StorageKey>`): `StorageChangeSet`
- **interface**: `api.rpc.state.subscribeStorage`
- **jsonrpc**: `state_subscribeStorage`
- **summary**: Subscribes to storage changes for the provided keys
 
### traceBlock(block: `Hash`, targets: `Option<Text>`, storageKeys: `Option<Text>`, methods: `Option<Text>`): `TraceBlockResponse`
- **interface**: `api.rpc.state.traceBlock`
- **jsonrpc**: `state_traceBlock`
- **summary**: Provides a way to trace the re-execution of a single block
- **unsafe**: This method is only active with appropriate flags

___


## system
 
### accountNextIndex(accountId: `AccountId`): `Index`
- **interface**: `api.rpc.system.accountNextIndex`
- **jsonrpc**: `system_accountNextIndex`
- **summary**: Retrieves the next accountIndex as available on the node
 
### addLogFilter(directives: `Text`): `Null`
- **interface**: `api.rpc.system.addLogFilter`
- **jsonrpc**: `system_addLogFilter`
- **summary**: Adds the supplied directives to the current log filter
- **unsafe**: This method is only active with appropriate flags
 
### addReservedPeer(peer: `Text`): `Text`
- **interface**: `api.rpc.system.addReservedPeer`
- **jsonrpc**: `system_addReservedPeer`
- **summary**: Adds a reserved peer
- **unsafe**: This method is only active with appropriate flags
 
### chain(): `Text`
- **interface**: `api.rpc.system.chain`
- **jsonrpc**: `system_chain`
- **summary**: Retrieves the chain
 
### chainType(): `ChainType`
- **interface**: `api.rpc.system.chainType`
- **jsonrpc**: `system_chainType`
- **summary**: Retrieves the chain type
 
### dryRun(extrinsic: `Bytes`, at?: `BlockHash`): `ApplyExtrinsicResult`
- **interface**: `api.rpc.system.dryRun`
- **jsonrpc**: `system_dryRun`
- **summary**: Dry run an extrinsic at a given block
- **unsafe**: This method is only active with appropriate flags
 
### health(): `Health`
- **interface**: `api.rpc.system.health`
- **jsonrpc**: `system_health`
- **summary**: Return health status of the node
 
### localListenAddresses(): `Vec<Text>`
- **interface**: `api.rpc.system.localListenAddresses`
- **jsonrpc**: `system_localListenAddresses`
- **summary**: The addresses include a trailing /p2p/ with the local PeerId, and are thus suitable to be passed to addReservedPeer or as a bootnode address for example
 
### localPeerId(): `Text`
- **interface**: `api.rpc.system.localPeerId`
- **jsonrpc**: `system_localPeerId`
- **summary**: Returns the base58-encoded PeerId of the node
 
### name(): `Text`
- **interface**: `api.rpc.system.name`
- **jsonrpc**: `system_name`
- **summary**: Retrieves the node name
 
### nodeRoles(): `Vec<NodeRole>`
- **interface**: `api.rpc.system.nodeRoles`
- **jsonrpc**: `system_nodeRoles`
- **summary**: Returns the roles the node is running as
 
### peers(): `Vec<PeerInfo>`
- **interface**: `api.rpc.system.peers`
- **jsonrpc**: `system_peers`
- **summary**: Returns the currently connected peers
- **unsafe**: This method is only active with appropriate flags
 
### properties(): `ChainProperties`
- **interface**: `api.rpc.system.properties`
- **jsonrpc**: `system_properties`
- **summary**: Get a custom set of properties as a JSON object, defined in the chain spec
 
### removeReservedPeer(peerId: `Text`): `Text`
- **interface**: `api.rpc.system.removeReservedPeer`
- **jsonrpc**: `system_removeReservedPeer`
- **summary**: Remove a reserved peer
- **unsafe**: This method is only active with appropriate flags
 
### reservedPeers(): `Vec<Text>`
- **interface**: `api.rpc.system.reservedPeers`
- **jsonrpc**: `system_reservedPeers`
- **summary**: Returns the list of reserved peers
 
### resetLogFilter(): `Null`
- **interface**: `api.rpc.system.resetLogFilter`
- **jsonrpc**: `system_resetLogFilter`
- **summary**: Resets the log filter to Substrate defaults
- **unsafe**: This method is only active with appropriate flags
 
### syncState(): `SyncState`
- **interface**: `api.rpc.system.syncState`
- **jsonrpc**: `system_syncState`
- **summary**: Returns the state of the syncing of the node
 
### version(): `Text`
- **interface**: `api.rpc.system.version`
- **jsonrpc**: `system_version`
- **summary**: Retrieves the version of the node
