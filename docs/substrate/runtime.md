---
title: Runtime
---

The following section contains known runtime calls that may be available on specific runtimes (depending on configuration and available pallets). These call directly into the WASM runtime for queries and operations.

- **[accountNonceApi](#accountnonceapi)**

- **[babeApi](#babeapi)**

- **[blockBuilder](#blockbuilder)**

- **[convertTransactionRuntimeApi](#converttransactionruntimeapi)**

- **[core](#core)**

- **[ethereumRuntimeRPCApi](#ethereumruntimerpcapi)**

- **[grandpaApi](#grandpaapi)**

- **[metadata](#metadata)**

- **[offchainWorkerApi](#offchainworkerapi)**

- **[sessionKeys](#sessionkeys)**

- **[taggedTransactionQueue](#taggedtransactionqueue)**

- **[transactionPaymentApi](#transactionpaymentapi)**


___


## AccountNonceApi
 
### accountNonce(accountId: `AccountId`): `Index`
- **interface**: `api.call.accountNonceApi.accountNonce`
- **runtime**: `AccountNonceApi_account_nonce`
- **summary**: The API to query account nonce (aka transaction index)

___


## BabeApi
 
### configuration(): `BabeGenesisConfiguration`
- **interface**: `api.call.babeApi.configuration`
- **runtime**: `BabeApi_configuration`
- **summary**: Return the genesis configuration for BABE. The configuration is only read on genesis.
 
### currentEpoch(): `Epoch`
- **interface**: `api.call.babeApi.currentEpoch`
- **runtime**: `BabeApi_current_epoch`
- **summary**: Returns information regarding the current epoch.
 
### currentEpochStart(): `Slot`
- **interface**: `api.call.babeApi.currentEpochStart`
- **runtime**: `BabeApi_current_epoch_start`
- **summary**: Returns the slot that started the current epoch.
 
### generateKeyOwnershipProof(slot: `Slot`, authorityId: `AuthorityId`): `Option<OpaqueKeyOwnershipProof>`
- **interface**: `api.call.babeApi.generateKeyOwnershipProof`
- **runtime**: `BabeApi_generate_key_ownership_proof`
- **summary**: Generates a proof of key ownership for the given authority in the current epoch.
 
### nextEpoch(): `Epoch`
- **interface**: `api.call.babeApi.nextEpoch`
- **runtime**: `BabeApi_next_epoch`
- **summary**: Returns information regarding the next epoch (which was already previously announced).
 
### submitReportEquivocationUnsignedExtrinsic(equivocationProof: `BabeEquivocationProof`, keyOwnerProof: `OpaqueKeyOwnershipProof`): `Option<Null>`
- **interface**: `api.call.babeApi.submitReportEquivocationUnsignedExtrinsic`
- **runtime**: `BabeApi_submit_report_equivocation_unsigned_extrinsic`
- **summary**: Submits an unsigned extrinsic to report an equivocation.

___


## BlockBuilder
 
### applyExtrinsic(extrinsic: `Extrinsic`): `ApplyExtrinsicResult`
- **interface**: `api.call.blockBuilder.applyExtrinsic`
- **runtime**: `BlockBuilder_apply_extrinsic`
- **summary**: Apply the given extrinsic.
 
### checkInherents(block: `Block`, data: `InherentData`): `CheckInherentsResult`
- **interface**: `api.call.blockBuilder.checkInherents`
- **runtime**: `BlockBuilder_check_inherents`
- **summary**: Check that the inherents are valid.
 
### finalizeBlock(): `Header`
- **interface**: `api.call.blockBuilder.finalizeBlock`
- **runtime**: `BlockBuilder_finalize_block`
- **summary**: Finish the current block.
 
### inherentExtrinsics(inherent: `InherentData`): `Vec<Extrinsic>`
- **interface**: `api.call.blockBuilder.inherentExtrinsics`
- **runtime**: `BlockBuilder_inherent_extrinsics`
- **summary**: Generate inherent extrinsics.

___


## ConvertTransactionRuntimeApi
 
### convertTransaction(transaction: `TransactionV2`): `Extrinsic`
- **interface**: `api.call.convertTransactionRuntimeApi.convertTransaction`
- **runtime**: `ConvertTransactionRuntimeApi_convert_transaction`
- **summary**: Converts an Ethereum-style transaction to Extrinsic

___


## Core
 
### executeBlock(block: `Block`): `Null`
- **interface**: `api.call.core.executeBlock`
- **runtime**: `Core_execute_block`
- **summary**: Execute the given block.
 
### initializeBlock(header: `Header`): `Null`
- **interface**: `api.call.core.initializeBlock`
- **runtime**: `Core_initialize_block`
- **summary**: Initialize a block with the given header.
 
### version(): `RuntimeVersion`
- **interface**: `api.call.core.version`
- **runtime**: `Core_version`
- **summary**: Returns the version of the runtime.

___


## EthereumRuntimeRPCApi
 
### accountBasic(address: `H160`): `EvmAccount`
- **interface**: `api.call.ethereumRuntimeRPCApi.accountBasic`
- **runtime**: `EthereumRuntimeRPCApi_account_basic`
- **summary**: Returns pallet_evm::Accounts by address.
 
### accountCodeAt(address: `H160`): `Bytes`
- **interface**: `api.call.ethereumRuntimeRPCApi.accountCodeAt`
- **runtime**: `EthereumRuntimeRPCApi_account_code_at`
- **summary**: For a given account address, returns pallet_evm::AccountCodes.
 
### author(): `H160`
- **interface**: `api.call.ethereumRuntimeRPCApi.author`
- **runtime**: `EthereumRuntimeRPCApi_author`
- **summary**: Returns the converted FindAuthor::find_author authority id.
 
### call(from: `H160`, to: `H160`, data: `Vec<u8>`, value: `U256`, gasLimit: `U256`, maxFeePerGas: `Option<U256>`, maxPriorityFeePerGas: `Option<U256>`, nonce: `Option<U256>`, estimate: `bool`, accessList: `Option<Vec<(H160, Vec<H256>)>>`): `Result<EvmCallInfo, DispatchError>`
- **interface**: `api.call.ethereumRuntimeRPCApi.call`
- **runtime**: `EthereumRuntimeRPCApi_call`
- **summary**: Returns a frame_ethereum::call response. If `estimate` is true,
 
### chainId(): `u64`
- **interface**: `api.call.ethereumRuntimeRPCApi.chainId`
- **runtime**: `EthereumRuntimeRPCApi_chain_id`
- **summary**: Returns runtime defined pallet_evm::ChainId.
 
### create(from: `H160`, data: `Vec<u8>`, value: `U256`, gasLimit: `U256`, maxFeePerGas: `Option<U256>`, maxPriorityFeePerGas: `Option<U256>`, nonce: `Option<U256>`, estimate: `bool`, accessList: `Option<Vec<(H160, Vec<H256>)>>`): `Result<EvmCreateInfo, DispatchError>`
- **interface**: `api.call.ethereumRuntimeRPCApi.create`
- **runtime**: `EthereumRuntimeRPCApi_create`
- **summary**: Returns a frame_ethereum::call response. If `estimate` is true,
 
### currentAll(): `(Option<BlockV2>, Option<Vec<EthReceiptV3>>, Option<Vec<EthTransactionStatus>>)`
- **interface**: `api.call.ethereumRuntimeRPCApi.currentAll`
- **runtime**: `EthereumRuntimeRPCApi_current_all`
- **summary**: Return all the current data for a block in a single runtime call.
 
### currentBlock(): `BlockV2`
- **interface**: `api.call.ethereumRuntimeRPCApi.currentBlock`
- **runtime**: `EthereumRuntimeRPCApi_current_block`
- **summary**: Return the current block.
 
### currentReceipts(): `Option<Vec<EthReceiptV3>>`
- **interface**: `api.call.ethereumRuntimeRPCApi.currentReceipts`
- **runtime**: `EthereumRuntimeRPCApi_current_receipts`
- **summary**: Return the current receipt.
 
### currentTransactionStatuses(): `Option<Vec<EthTransactionStatus>>`
- **interface**: `api.call.ethereumRuntimeRPCApi.currentTransactionStatuses`
- **runtime**: `EthereumRuntimeRPCApi_current_transaction_statuses`
- **summary**: Return the current transaction status.
 
### elasticity(): `Option<Permill>`
- **interface**: `api.call.ethereumRuntimeRPCApi.elasticity`
- **runtime**: `EthereumRuntimeRPCApi_elasticity`
- **summary**: Return the elasticity multiplier.
 
### extrinsicFilter(xts: `Vec<Extrinsic>`): `Vec<TransactionV2>`
- **interface**: `api.call.ethereumRuntimeRPCApi.extrinsicFilter`
- **runtime**: `EthereumRuntimeRPCApi_extrinsic_filter`
- **summary**: Receives a `Vec<OpaqueExtrinsic>` and filters all the ethereum transactions.
 
### gasPrice(): `u256`
- **interface**: `api.call.ethereumRuntimeRPCApi.gasPrice`
- **runtime**: `EthereumRuntimeRPCApi_gas_price`
- **summary**: Returns FixedGasPrice::min_gas_price
 
### storageAt(address: `H160`, index: `u256`): `H256`
- **interface**: `api.call.ethereumRuntimeRPCApi.storageAt`
- **runtime**: `EthereumRuntimeRPCApi_storage_at`
- **summary**: For a given account address and index, returns pallet_evm::AccountStorages.

___


## GrandpaApi
 
### currentSetId(): `SetId`
- **interface**: `api.call.grandpaApi.currentSetId`
- **runtime**: `GrandpaApi_current_set_id`
- **summary**: Get current GRANDPA authority set id.
 
### generateKeyOwnershipProof(setId: `SetId`, authorityId: `AuthorityId`): `Option<OpaqueKeyOwnershipProof>`
- **interface**: `api.call.grandpaApi.generateKeyOwnershipProof`
- **runtime**: `GrandpaApi_generate_key_ownership_proof`
- **summary**: Generates a proof of key ownership for the given authority in the given set.
 
### grandpaAuthorities(): `AuthorityList`
- **interface**: `api.call.grandpaApi.grandpaAuthorities`
- **runtime**: `GrandpaApi_grandpa_authorities`
- **summary**: Get the current GRANDPA authorities and weights. This should not change except for when changes are scheduled and the corresponding delay has passed.
 
### submitReportEquivocationUnsignedExtrinsic(equivocationProof: `GrandpaEquivocationProof`, keyOwnerProof: `OpaqueKeyOwnershipProof`): `Option<Null>`
- **interface**: `api.call.grandpaApi.submitReportEquivocationUnsignedExtrinsic`
- **runtime**: `GrandpaApi_submit_report_equivocation_unsigned_extrinsic`
- **summary**: Submits an unsigned extrinsic to report an equivocation.

___


## Metadata
 
### metadata(): `OpaqueMetadata`
- **interface**: `api.call.metadata.metadata`
- **runtime**: `Metadata_metadata`
- **summary**: Returns the metadata of a runtime

___


## OffchainWorkerApi
 
### offchainWorker(header: `Header`): `Null`
- **interface**: `api.call.offchainWorkerApi.offchainWorker`
- **runtime**: `OffchainWorkerApi_offchain_worker`
- **summary**: Starts the off-chain task for given block header.

___


## SessionKeys
 
### decodeSessionKeys(encoded: `Bytes`): `Option<Vec<(Bytes, KeyTypeId)>>`
- **interface**: `api.call.sessionKeys.decodeSessionKeys`
- **runtime**: `SessionKeys_decode_session_keys`
- **summary**: Decode the given public session keys.
 
### generateSessionKeys(seed: `Option<Bytes>`): `Bytes`
- **interface**: `api.call.sessionKeys.generateSessionKeys`
- **runtime**: `SessionKeys_generate_session_keys`
- **summary**: Generate a set of session keys with optionally using the given seed.

___


## TaggedTransactionQueue
 
### validateTransaction(source: `TransactionSource`, tx: `Extrinsic`, blockHash: `BlockHash`): `TransactionValidity`
- **interface**: `api.call.taggedTransactionQueue.validateTransaction`
- **runtime**: `TaggedTransactionQueue_validate_transaction`
- **summary**: Validate the transaction.

___


## TransactionPaymentApi
 
### queryFeeDetails(uxt: `Extrinsic`, len: `u32`): `FeeDetails`
- **interface**: `api.call.transactionPaymentApi.queryFeeDetails`
- **runtime**: `TransactionPaymentApi_query_fee_details`
- **summary**: The transaction fee details
 
### queryInfo(uxt: `Extrinsic`, len: `u32`): `RuntimeDispatchInfo`
- **interface**: `api.call.transactionPaymentApi.queryInfo`
- **runtime**: `TransactionPaymentApi_query_info`
- **summary**: The transaction info
