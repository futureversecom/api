---
title: Storage
---

The following sections contain Storage methods are part of the default porcini runtime. On the api, these are exposed via `api.query.<module>.<method>`. 

(NOTE: These were generated from a static/snapshot view of a recent default porcini runtime. Some items may not be available in older nodes, or in any customized implementations.)

- **[assets](#assets)**

- **[assetsExt](#assetsext)**

- **[authorship](#authorship)**

- **[babe](#babe)**

- **[balances](#balances)**

- **[dex](#dex)**

- **[echo](#echo)**

- **[electionProviderMultiPhase](#electionprovidermultiphase)**

- **[erc20Peg](#erc20peg)**

- **[ethBridge](#ethbridge)**

- **[ethereum](#ethereum)**

- **[eVM](#evm)**

- **[eVMChainId](#evmchainid)**

- **[feeControl](#feecontrol)**

- **[futurepass](#futurepass)**

- **[grandpa](#grandpa)**

- **[imOnline](#imonline)**

- **[nft](#nft)**

- **[nftPeg](#nftpeg)**

- **[offences](#offences)**

- **[proxy](#proxy)**

- **[recovery](#recovery)**

- **[scheduler](#scheduler)**

- **[session](#session)**

- **[sft](#sft)**

- **[staking](#staking)**

- **[substrate](#substrate)**

- **[sudo](#sudo)**

- **[system](#system)**

- **[timestamp](#timestamp)**

- **[tokenApprovals](#tokenapprovals)**

- **[transactionPayment](#transactionpayment)**

- **[txFeePot](#txfeepot)**

- **[voterList](#voterlist)**

- **[xls20](#xls20)**

- **[xRPLBridge](#xrplbridge)**


___


## assets
 
### account(`u32, SeedPrimitivesSignatureAccountId20`): `Option<PalletAssetsAssetAccount>`
- **interface**: `api.query.assets.account`
- **summary**:    The holdings of a specific account for a specific asset. 
 
### approvals(`u32, SeedPrimitivesSignatureAccountId20, SeedPrimitivesSignatureAccountId20`): `Option<PalletAssetsApproval>`
- **interface**: `api.query.assets.approvals`
- **summary**:    Approved balance transfers. First balance is the amount approved for transfer. Second  is the amount of `T::Currency` reserved for storing this.  First key is the asset ID, second key is the owner and third key is the delegate. 
 
### asset(`u32`): `Option<PalletAssetsAssetDetails>`
- **interface**: `api.query.assets.asset`
- **summary**:    Details of an asset. 
 
### metadata(`u32`): `PalletAssetsAssetMetadata`
- **interface**: `api.query.assets.metadata`
- **summary**:    Metadata of an asset. 

___


## assetsExt
 
### holds(`u32, SeedPrimitivesSignatureAccountId20`): `Vec<([u8;8],u128)>`
- **interface**: `api.query.assetsExt.holds`
- **summary**:    The holdings of a specific account for a specific asset. 
 
### nextAssetId(): `u32`
- **interface**: `api.query.assetsExt.nextAssetId`
- **summary**:    The total units issued in the system. 

___


## authorship
 
### author(): `Option<SeedPrimitivesSignatureAccountId20>`
- **interface**: `api.query.authorship.author`
- **summary**:    Author of current block. 
 
### didSetUncles(): `bool`
- **interface**: `api.query.authorship.didSetUncles`
- **summary**:    Whether uncles were already set in this block. 
 
### uncles(): `Vec<PalletAuthorshipUncleEntryItem>`
- **interface**: `api.query.authorship.uncles`
- **summary**:    Uncles 

___


## babe
 
### authorities(): `Vec<(SpConsensusBabeAppPublic,u64)>`
- **interface**: `api.query.babe.authorities`
- **summary**:    Current epoch authorities. 
 
### authorVrfRandomness(): `Option<[u8;32]>`
- **interface**: `api.query.babe.authorVrfRandomness`
- **summary**:    This field should always be populated during block processing unless  secondary plain slots are enabled (which don't contain a VRF output). 

   It is set in `on_finalize`, before it will contain the value from the last block. 
 
### currentSlot(): `u64`
- **interface**: `api.query.babe.currentSlot`
- **summary**:    Current slot number. 
 
### epochConfig(): `Option<SpConsensusBabeBabeEpochConfiguration>`
- **interface**: `api.query.babe.epochConfig`
- **summary**:    The configuration for the current epoch. Should never be `None` as it is initialized in  genesis. 
 
### epochIndex(): `u64`
- **interface**: `api.query.babe.epochIndex`
- **summary**:    Current epoch index. 
 
### epochStart(): `(u32,u32)`
- **interface**: `api.query.babe.epochStart`
- **summary**:    The block numbers when the last and current epoch have started, respectively `N-1` and  `N`.  NOTE: We track this is in order to annotate the block number when a given pool of  entropy was fixed (i.e. it was known to chain observers). Since epochs are defined in  slots, which may be skipped, the block numbers may not line up with the slot numbers. 
 
### genesisSlot(): `u64`
- **interface**: `api.query.babe.genesisSlot`
- **summary**:    The slot at which the first epoch actually started. This is 0  until the first block of the chain. 
 
### initialized(): `Option<Option<SpConsensusBabeDigestsPreDigest>>`
- **interface**: `api.query.babe.initialized`
- **summary**:    Temporary value (cleared at block finalization) which is `Some`  if per-block initialization has already been called for current block. 
 
### lateness(): `u32`
- **interface**: `api.query.babe.lateness`
- **summary**:    How late the current block is compared to its parent. 

   This entry is populated as part of block execution and is cleaned up  on block finalization. Querying this storage entry outside of block  execution context should always yield zero. 
 
### nextAuthorities(): `Vec<(SpConsensusBabeAppPublic,u64)>`
- **interface**: `api.query.babe.nextAuthorities`
- **summary**:    Next epoch authorities. 
 
### nextEpochConfig(): `Option<SpConsensusBabeBabeEpochConfiguration>`
- **interface**: `api.query.babe.nextEpochConfig`
- **summary**:    The configuration for the next epoch, `None` if the config will not change  (you can fallback to `EpochConfig` instead in that case). 
 
### nextRandomness(): `[u8;32]`
- **interface**: `api.query.babe.nextRandomness`
- **summary**:    Next epoch randomness. 
 
### pendingEpochConfigChange(): `Option<SpConsensusBabeDigestsNextConfigDescriptor>`
- **interface**: `api.query.babe.pendingEpochConfigChange`
- **summary**:    Pending epoch configuration change that will be applied when the next epoch is enacted. 
 
### randomness(): `[u8;32]`
- **interface**: `api.query.babe.randomness`
- **summary**:    The epoch randomness for the *current* epoch. 

   #### Security 

   This MUST NOT be used for gambling, as it can be influenced by a  malicious validator in the short term. It MAY be used in many  cryptographic protocols, however, so long as one remembers that this  (like everything else on-chain) it is public. For example, it can be  used where a number is needed that cannot have been chosen by an  adversary, for purposes such as public-coin zero-knowledge proofs. 
 
### segmentIndex(): `u32`
- **interface**: `api.query.babe.segmentIndex`
- **summary**:    Randomness under construction. 

   We make a trade-off between storage accesses and list length.  We store the under-construction randomness in segments of up to  `UNDER_CONSTRUCTION_SEGMENT_LENGTH`. 

   Once a segment reaches this length, we begin the next one.  We reset all segments and return to `0` at the beginning of every  epoch. 
 
### underConstruction(`u32`): `Vec<[u8;32]>`
- **interface**: `api.query.babe.underConstruction`
- **summary**:    TWOX-NOTE: `SegmentIndex` is an increasing integer, so this is okay. 

___


## balances
 
### account(`SeedPrimitivesSignatureAccountId20`): `PalletBalancesAccountData`
- **interface**: `api.query.balances.account`
- **summary**:    The Balances pallet example of storing the balance of an account. 

   #### Example 

   ```nocompile  impl pallet_balances::Config for Runtime {  type AccountStore = StorageMapShim<Self::Account<Runtime>, frame_system::Provider<Runtime>, AccountId, Self::AccountData<Balance>>  }  ``` 

   You can also store the balance of an account in the `System` pallet. 

   #### Example 

   ```nocompile  impl pallet_balances::Config for Runtime {  type AccountStore = System  }  ``` 

   But this comes with tradeoffs, storing account balances in the system pallet stores  `frame_system` data alongside the account data contrary to storing account balances in the  `Balances` pallet, which uses a `StorageMap` to store balances data only.  NOTE: This is only used in the case that this pallet is used to store balances. 
 
### locks(`SeedPrimitivesSignatureAccountId20`): `Vec<PalletBalancesBalanceLock>`
- **interface**: `api.query.balances.locks`
- **summary**:    Any liquidity locks on some account balances.  NOTE: Should only be accessed when setting, changing and freeing a lock. 
 
### reserves(`SeedPrimitivesSignatureAccountId20`): `Vec<PalletBalancesReserveData>`
- **interface**: `api.query.balances.reserves`
- **summary**:    Named reserves on some account balances. 
 
### storageVersion(): `PalletBalancesReleases`
- **interface**: `api.query.balances.storageVersion`
- **summary**:    Storage version of the pallet. 

   This is set to v2.0.0 for new networks. 
 
### totalIssuance(): `u128`
- **interface**: `api.query.balances.totalIssuance`
- **summary**:    The total units issued in the system. 

___


## dex
 
### liquidityPool(`PalletDexTradingPair`): `(u128,u128)`
- **interface**: `api.query.dex.liquidityPool`
 
### tradingPairLPToken(`PalletDexTradingPair`): `Option<u32>`
- **interface**: `api.query.dex.tradingPairLPToken`
 
### tradingPairStatuses(`PalletDexTradingPair`): `PalletDexTradingPairStatus`
- **interface**: `api.query.dex.tradingPairStatuses`

___


## echo
 
### nextSessionId(): `u64`
- **interface**: `api.query.echo.nextSessionId`
- **summary**:    The next available offer_id 

___


## electionProviderMultiPhase
 
### currentPhase(): `PalletElectionProviderMultiPhasePhase`
- **interface**: `api.query.electionProviderMultiPhase.currentPhase`
- **summary**:    Current phase. 
 
### desiredTargets(): `Option<u32>`
- **interface**: `api.query.electionProviderMultiPhase.desiredTargets`
- **summary**:    Desired number of targets to elect for this round. 

   Only exists when [`Snapshot`] is present. 
 
### minimumUntrustedScore(): `Option<SpNposElectionsElectionScore>`
- **interface**: `api.query.electionProviderMultiPhase.minimumUntrustedScore`
- **summary**:    The minimum score that each 'untrusted' solution must attain in order to be considered  feasible. 

   Can be set via `set_minimum_untrusted_score`. 
 
### queuedSolution(): `Option<PalletElectionProviderMultiPhaseReadySolution>`
- **interface**: `api.query.electionProviderMultiPhase.queuedSolution`
- **summary**:    Current best solution, signed or unsigned, queued to be returned upon `elect`. 
 
### round(): `u32`
- **interface**: `api.query.electionProviderMultiPhase.round`
- **summary**:    Internal counter for the number of rounds. 

   This is useful for de-duplication of transactions submitted to the pool, and general  diagnostics of the pallet. 

   This is merely incremented once per every time that an upstream `elect` is called. 
 
### signedSubmissionIndices(): `BTreeMap<SpNposElectionsElectionScore, u32>`
- **interface**: `api.query.electionProviderMultiPhase.signedSubmissionIndices`
- **summary**:    A sorted, bounded set of `(score, index)`, where each `index` points to a value in  `SignedSubmissions`. 

   We never need to process more than a single signed submission at a time. Signed submissions  can be quite large, so we're willing to pay the cost of multiple database accesses to access  them one at a time instead of reading and decoding all of them at once. 
 
### signedSubmissionNextIndex(): `u32`
- **interface**: `api.query.electionProviderMultiPhase.signedSubmissionNextIndex`
- **summary**:    The next index to be assigned to an incoming signed submission. 

   Every accepted submission is assigned a unique index; that index is bound to that particular  submission for the duration of the election. On election finalization, the next index is  reset to 0. 

   We can't just use `SignedSubmissionIndices.len()`, because that's a bounded set; past its  capacity, it will simply saturate. We can't just iterate over `SignedSubmissionsMap`,  because iteration is slow. Instead, we store the value here. 
 
### signedSubmissionsMap(`u32`): `Option<PalletElectionProviderMultiPhaseSignedSignedSubmission>`
- **interface**: `api.query.electionProviderMultiPhase.signedSubmissionsMap`
- **summary**:    Unchecked, signed solutions. 

   Together with `SubmissionIndices`, this stores a bounded set of `SignedSubmissions` while  allowing us to keep only a single one in memory at a time. 

   Twox note: the key of the map is an auto-incrementing index which users cannot inspect or  affect; we shouldn't need a cryptographically secure hasher. 
 
### snapshot(): `Option<PalletElectionProviderMultiPhaseRoundSnapshot>`
- **interface**: `api.query.electionProviderMultiPhase.snapshot`
- **summary**:    Snapshot data of the round. 

   This is created at the beginning of the signed phase and cleared upon calling `elect`. 
 
### snapshotMetadata(): `Option<PalletElectionProviderMultiPhaseSolutionOrSnapshotSize>`
- **interface**: `api.query.electionProviderMultiPhase.snapshotMetadata`
- **summary**:    The metadata of the [`RoundSnapshot`] 

   Only exists when [`Snapshot`] is present. 

___


## erc20Peg
 
### assetIdToErc20(`u32`): `Option<H160>`
- **interface**: `api.query.erc20Peg.assetIdToErc20`
- **summary**:    Map GA asset Id to ERC20 address 
 
### contractAddress(): `H160`
- **interface**: `api.query.erc20Peg.contractAddress`
- **summary**:    The peg contract address on Ethereum 
 
### delayedPayments(`u64`): `Option<PalletErc20PegPendingPayment>`
- **interface**: `api.query.erc20Peg.delayedPayments`
- **summary**:    Map from DelayedPaymentId to PendingPayment 
 
### delayedPaymentSchedule(`u32`): `Vec<u64>`
- **interface**: `api.query.erc20Peg.delayedPaymentSchedule`
- **summary**:    Map from block number to DelayedPaymentIds scheduled for that block 
 
### depositsActive(): `bool`
- **interface**: `api.query.erc20Peg.depositsActive`
- **summary**:    Whether deposit are active 
 
### erc20Meta(`H160`): `Option<(Bytes,u8)>`
- **interface**: `api.query.erc20Peg.erc20Meta`
- **summary**:    Metadata for well-known erc20 tokens (symbol, decimals) 
 
### erc20ToAssetId(`H160`): `Option<u32>`
- **interface**: `api.query.erc20Peg.erc20ToAssetId`
- **summary**:    Map ERC20 address to GA asset Id 
 
### nextDelayedPaymentId(): `u64`
- **interface**: `api.query.erc20Peg.nextDelayedPaymentId`
- **summary**:    The next available payment id for withdrawals and deposits 
 
### paymentDelay(`u32`): `Option<(u128,u32)>`
- **interface**: `api.query.erc20Peg.paymentDelay`
- **summary**:    Map from asset_id to minimum amount and delay 
 
### readyBlocks(): `Vec<u32>`
- **interface**: `api.query.erc20Peg.readyBlocks`
- **summary**:    The blocks with payments that are ready to be processed 
 
### withdrawalsActive(): `bool`
- **interface**: `api.query.erc20Peg.withdrawalsActive`
- **summary**:    Whether withdrawals are active 

___


## ethBridge
 
### authoritiesChangedThisEra(): `bool`
- **interface**: `api.query.ethBridge.authoritiesChangedThisEra`
- **summary**:    Flag to indicate whether authorities have been changed during the current era 
 
### bridgePaused(): `bool`
- **interface**: `api.query.ethBridge.bridgePaused`
- **summary**:    Whether the bridge is paused (e.g. during validator transitions or by governance) 
 
### challengePeriod(): `u32`
- **interface**: `api.query.ethBridge.challengePeriod`
- **summary**:    The (optimistic) challenge period after which a submitted event is considered valid 
 
### challengerAccount(`u64`): `Option<(SeedPrimitivesSignatureAccountId20,u128)>`
- **interface**: `api.query.ethBridge.challengerAccount`
- **summary**:    Maps from event claim id to challenger and bond amount paid 
 
### contractAddress(): `H160`
- **interface**: `api.query.ethBridge.contractAddress`
- **summary**:    The bridge contract address on Ethereum 
 
### delayedEventProofsPerBlock(): `u8`
- **interface**: `api.query.ethBridge.delayedEventProofsPerBlock`
- **summary**:    The maximum number of delayed events that can be processed in on_initialize() 
 
### ethCallNotarizations(`u64, SeedPrimitivesEthyCryptoAppCryptoPublic`): `Option<PalletEthyCheckedEthCallResult>`
- **interface**: `api.query.ethBridge.ethCallNotarizations`
- **summary**:    EthCallOracle notarizations keyed by (Id, Notary) 
 
### ethCallNotarizationsAggregated(`u64`): `Option<BTreeMap<PalletEthyCheckedEthCallResult, u32>>`
- **interface**: `api.query.ethBridge.ethCallNotarizationsAggregated`
- **summary**:    map from EthCallOracle notarizations to an aggregated count 
 
### ethCallRequestInfo(`u64`): `Option<PalletEthyCheckedEthCallRequest>`
- **interface**: `api.query.ethBridge.ethCallRequestInfo`
- **summary**:    EthCallOracle request info 
 
### ethCallRequests(): `Vec<u64>`
- **interface**: `api.query.ethBridge.ethCallRequests`
- **summary**:    Queue of pending EthCallOracle requests 
 
### eventBlockConfirmations(): `u64`
- **interface**: `api.query.ethBridge.eventBlockConfirmations`
- **summary**:    The minimum number of block confirmations needed to notarize an Ethereum event 
 
### eventNotarizations(`u64, SeedPrimitivesEthyCryptoAppCryptoPublic`): `Option<PalletEthyEventClaimResult>`
- **interface**: `api.query.ethBridge.eventNotarizations`
- **summary**:    Notarizations for queued events  Either: None = no notarization exists OR Some(yay/nay) 
 
### messagesValidAt(`u32`): `Vec<u64>`
- **interface**: `api.query.ethBridge.messagesValidAt`
- **summary**:    Map from block number to list of EventClaims that will be considered valid and should be forwarded to handlers (i.e after the optimistic challenge period has passed without issue) 
 
### nextAuthorityChange(): `Option<u32>`
- **interface**: `api.query.ethBridge.nextAuthorityChange`
- **summary**:    The block in which we process the next authority change 
 
### nextEthCallId(): `u64`
- **interface**: `api.query.ethBridge.nextEthCallId`
- **summary**:    Subscription Id for EthCall requests 
 
### nextEventProofId(): `u64`
- **interface**: `api.query.ethBridge.nextEventProofId`
- **summary**:    Id of the next event proof 
 
### nextNotaryKeys(): `Vec<SeedPrimitivesEthyCryptoAppCryptoPublic>`
- **interface**: `api.query.ethBridge.nextNotaryKeys`
- **summary**:    Scheduled notary (validator) public keys for the next session 
 
### notaryKeys(): `Vec<SeedPrimitivesEthyCryptoAppCryptoPublic>`
- **interface**: `api.query.ethBridge.notaryKeys`
- **summary**:    Active notary (validator) public keys 
 
### notarySetId(): `u64`
- **interface**: `api.query.ethBridge.notarySetId`
- **summary**:    The current validator set id 
 
### notarySetProofId(): `u64`
- **interface**: `api.query.ethBridge.notarySetProofId`
- **summary**:    The event proof Id generated by the previous validator set to notarize the current set.  Useful for syncing the latest proof to Ethereum 
 
### notaryXrplKeys(): `Vec<SeedPrimitivesEthyCryptoAppCryptoPublic>`
- **interface**: `api.query.ethBridge.notaryXrplKeys`
- **summary**:    Active xrpl notary (validator) public keys 
 
### pendingClaimChallenges(): `Vec<u64>`
- **interface**: `api.query.ethBridge.pendingClaimChallenges`
- **summary**:    List of all event ids that are currently being challenged 
 
### pendingClaimStatus(`u64`): `Option<PalletEthyEventClaimStatus>`
- **interface**: `api.query.ethBridge.pendingClaimStatus`
- **summary**:    Status of pending event claims 
 
### pendingEventClaims(`u64`): `Option<PalletEthyEventClaim>`
- **interface**: `api.query.ethBridge.pendingEventClaims`
- **summary**:    Queued event claims, can be challenged within challenge period 
 
### pendingEventProofs(`u64`): `Option<PalletEthyEthySigningRequest>`
- **interface**: `api.query.ethBridge.pendingEventProofs`
- **summary**:    Queued event proofs to be processed once bridge has been re-enabled 
 
### processedMessageIds(): `Vec<u64>`
- **interface**: `api.query.ethBridge.processedMessageIds`
- **summary**:    Tracks processed message Ids (prevent replay) 
 
### relayer(): `Option<SeedPrimitivesSignatureAccountId20>`
- **interface**: `api.query.ethBridge.relayer`
- **summary**:    The permissioned relayer 
 
### relayerPaidBond(`SeedPrimitivesSignatureAccountId20`): `u128`
- **interface**: `api.query.ethBridge.relayerPaidBond`
- **summary**:    Maps from relayer account to their paid bond amount 
 
### xrplDoorSigners(`SeedPrimitivesEthyCryptoAppCryptoPublic`): `bool`
- **interface**: `api.query.ethBridge.xrplDoorSigners`
- **summary**:    Door Signers set by sudo (white list) 
 
### xrplNotarySetProofId(): `u64`
- **interface**: `api.query.ethBridge.xrplNotarySetProofId`
- **summary**:    The event proof Id generated by the previous validator set to notarize the current set.  Useful for syncing the latest proof to Xrpl 

___


## ethereum
 
### blockHash(`U256`): `H256`
- **interface**: `api.query.ethereum.blockHash`
 
### currentBlock(): `Option<EthereumBlock>`
- **interface**: `api.query.ethereum.currentBlock`
- **summary**:    The current Ethereum block. 
 
### currentReceipts(): `Option<Vec<EthereumReceiptReceiptV3>>`
- **interface**: `api.query.ethereum.currentReceipts`
- **summary**:    The current Ethereum receipts. 
 
### currentTransactionStatuses(): `Option<Vec<FpRpcTransactionStatus>>`
- **interface**: `api.query.ethereum.currentTransactionStatuses`
- **summary**:    The current transaction statuses. 
 
### pending(): `Vec<(EthereumTransactionTransactionV2,FpRpcTransactionStatus,EthereumReceiptReceiptV3)>`
- **interface**: `api.query.ethereum.pending`
- **summary**:    Current building block's transactions and receipts. 

___


## eVM
 
### accountCodes(`H160`): `Bytes`
- **interface**: `api.query.eVM.accountCodes`
 
### accountStorages(`H160, H256`): `H256`
- **interface**: `api.query.eVM.accountStorages`

___


## eVMChainId
 
### chainId(): `u64`
- **interface**: `api.query.eVMChainId.chainId`
- **summary**:    The EVM chain ID. 

___


## feeControl
 
### data(): `PalletFeeControlFeeConfig`
- **interface**: `api.query.feeControl.data`

___


## futurepass
 
### defaultProxy(`SeedPrimitivesSignatureAccountId20`): `Option<SeedPrimitivesSignatureAccountId20>`
- **interface**: `api.query.futurepass.defaultProxy`
- **summary**:    Accounts which have set futurepass as default proxied on-chain account (delegate ->  futurepass) 
 
### holders(`SeedPrimitivesSignatureAccountId20`): `Option<SeedPrimitivesSignatureAccountId20>`
- **interface**: `api.query.futurepass.holders`
- **summary**:    Futurepass holders (account -> futurepass) 
 
### migrationAdmin(): `Option<SeedPrimitivesSignatureAccountId20>`
- **interface**: `api.query.futurepass.migrationAdmin`
- **summary**:    Migration data for user (root) and collections they can migrate 
 
### nextFuturepassId(): `u128`
- **interface**: `api.query.futurepass.nextFuturepassId`
- **summary**:    The next available incrementing futurepass id 

___


## grandpa
 
### currentSetId(): `u64`
- **interface**: `api.query.grandpa.currentSetId`
- **summary**:    The number of changes (both in terms of keys and underlying economic responsibilities)  in the "set" of Grandpa validators from genesis. 
 
### nextForced(): `Option<u32>`
- **interface**: `api.query.grandpa.nextForced`
- **summary**:    next block number where we can force a change. 
 
### pendingChange(): `Option<PalletGrandpaStoredPendingChange>`
- **interface**: `api.query.grandpa.pendingChange`
- **summary**:    Pending change: (signaled at, scheduled change). 
 
### setIdSession(`u64`): `Option<u32>`
- **interface**: `api.query.grandpa.setIdSession`
- **summary**:    A mapping from grandpa set ID to the index of the *most recent* session for which its  members were responsible. 

   TWOX-NOTE: `SetId` is not under user control. 
 
### stalled(): `Option<(u32,u32)>`
- **interface**: `api.query.grandpa.stalled`
- **summary**:    `true` if we are currently stalled. 
 
### state(): `PalletGrandpaStoredState`
- **interface**: `api.query.grandpa.state`
- **summary**:    State of the current authority set. 

___


## imOnline
 
### authoredBlocks(`u32, SeedPrimitivesSignatureAccountId20`): `u32`
- **interface**: `api.query.imOnline.authoredBlocks`
- **summary**:    For each session index, we keep a mapping of `ValidatorId<T>` to the  number of blocks authored by the given authority. 
 
### heartbeatAfter(): `u32`
- **interface**: `api.query.imOnline.heartbeatAfter`
- **summary**:    The block number after which it's ok to send heartbeats in the current  session. 

   At the beginning of each session we set this to a value that should fall  roughly in the middle of the session duration. The idea is to first wait for  the validators to produce a block in the current session, so that the  heartbeat later on will not be necessary. 

   This value will only be used as a fallback if we fail to get a proper session  progress estimate from `NextSessionRotation`, as those estimates should be  more accurate then the value we calculate for `HeartbeatAfter`. 
 
### keys(): `Vec<PalletImOnlineSr25519AppSr25519Public>`
- **interface**: `api.query.imOnline.keys`
- **summary**:    The current set of keys that may issue a heartbeat. 
 
### receivedHeartbeats(`u32, u32`): `Option<WrapperOpaque<PalletImOnlineBoundedOpaqueNetworkState>>`
- **interface**: `api.query.imOnline.receivedHeartbeats`
- **summary**:    For each session index, we keep a mapping of `SessionIndex` and `AuthIndex` to  `WrapperOpaque<BoundedOpaqueNetworkState>`. 

___


## nft
 
### collectionInfo(`u32`): `Option<PalletNftCollectionInformation>`
- **interface**: `api.query.nft.collectionInfo`
- **summary**:    Map from collection to its information 
 
### listingEndSchedule(`u32, u128`): `Option<bool>`
- **interface**: `api.query.nft.listingEndSchedule`
- **summary**:    Block numbers where listings will close. Value is `true` if at block number `listing_id` is  scheduled to close. 
 
### listings(`u128`): `Option<PalletNftListing>`
- **interface**: `api.query.nft.listings`
- **summary**:    NFT sale/auction listings keyed by listing id 
 
### listingWinningBid(`u128`): `Option<(SeedPrimitivesSignatureAccountId20,u128)>`
- **interface**: `api.query.nft.listingWinningBid`
- **summary**:    Winning bids on open listings. 
 
### nextCollectionId(): `u32`
- **interface**: `api.query.nft.nextCollectionId`
- **summary**:    The next available incrementing collection id 
 
### nextListingId(): `u128`
- **interface**: `api.query.nft.nextListingId`
- **summary**:    The next available listing Id 
 
### nextMarketplaceId(): `u32`
- **interface**: `api.query.nft.nextMarketplaceId`
- **summary**:    The next available marketplace id 
 
### nextOfferId(): `u64`
- **interface**: `api.query.nft.nextOfferId`
- **summary**:    The next available offer_id 
 
### offers(`u64`): `Option<PalletNftOfferType>`
- **interface**: `api.query.nft.offers`
- **summary**:    Map from offer_id to the information related to the offer 
 
### openCollectionListings(`u32, u128`): `Option<bool>`
- **interface**: `api.query.nft.openCollectionListings`
- **summary**:    Map from collection to any open listings 
 
### registeredMarketplaces(`u32`): `Option<PalletNftMarketplace>`
- **interface**: `api.query.nft.registeredMarketplaces`
- **summary**:    Map from marketplace account_id to royalties schedule 
 
### tokenLocks(`(u32,u32)`): `Option<PalletNftTokenLockReason>`
- **interface**: `api.query.nft.tokenLocks`
- **summary**:    Map from a token to lock status if any 
 
### tokenOffers(`(u32,u32)`): `Option<Vec<u64>>`
- **interface**: `api.query.nft.tokenOffers`
- **summary**:    Maps from token_id to a vector of offer_ids on that token 

___


## nftPeg
 
### contractAddress(): `H160`
- **interface**: `api.query.nftPeg.contractAddress`
 
### ethToRootNft(`H160`): `Option<u32>`
- **interface**: `api.query.nftPeg.ethToRootNft`
 
### rootNftToErc721(`u32`): `Option<H160>`
- **interface**: `api.query.nftPeg.rootNftToErc721`

___


## offences
 
### concurrentReportsIndex(`[u8;16], Bytes`): `Vec<H256>`
- **interface**: `api.query.offences.concurrentReportsIndex`
- **summary**:    A vector of reports of the same kind that happened at the same time slot. 
 
### reports(`H256`): `Option<SpStakingOffenceOffenceDetails>`
- **interface**: `api.query.offences.reports`
- **summary**:    The primary structure that holds all offence records keyed by report identifiers. 
 
### reportsByKindIndex(`[u8;16]`): `Bytes`
- **interface**: `api.query.offences.reportsByKindIndex`
- **summary**:    Enumerates all reports of a kind along with the time they happened. 

   All reports are sorted by the time of offence. 

   Note that the actual type of this mapping is `Vec<u8>`, this is because values of  different types are not supported at the moment so we are doing the manual serialization. 

___


## proxy
 
### announcements(`SeedPrimitivesSignatureAccountId20`): `(Vec<PalletProxyAnnouncement>,u128)`
- **interface**: `api.query.proxy.announcements`
- **summary**:    The announcements made by the proxy (key). 
 
### proxies(`SeedPrimitivesSignatureAccountId20`): `(Vec<PalletProxyProxyDefinition>,u128)`
- **interface**: `api.query.proxy.proxies`
- **summary**:    The set of account proxies. Maps the account which has delegated to the accounts  which are being delegated to, together with the amount held on deposit. 

___


## recovery
 
### activeRecoveries(`SeedPrimitivesSignatureAccountId20, SeedPrimitivesSignatureAccountId20`): `Option<PalletRecoveryActiveRecovery>`
- **interface**: `api.query.recovery.activeRecoveries`
- **summary**:    Active recovery attempts. 

   First account is the account to be recovered, and the second account  is the user trying to recover the account. 
 
### proxy(`SeedPrimitivesSignatureAccountId20`): `Option<SeedPrimitivesSignatureAccountId20>`
- **interface**: `api.query.recovery.proxy`
- **summary**:    The list of allowed proxy accounts. 

   Map from the user who can access it to the recovered account. 
 
### recoverable(`SeedPrimitivesSignatureAccountId20`): `Option<PalletRecoveryRecoveryConfig>`
- **interface**: `api.query.recovery.recoverable`
- **summary**:    The set of recoverable accounts and their recovery configuration. 

___


## scheduler
 
### agenda(`u32`): `Vec<Option<PalletSchedulerScheduledV3>>`
- **interface**: `api.query.scheduler.agenda`
- **summary**:    Items to be executed, indexed by the block number that they should be executed on. 
 
### lookup(`Bytes`): `Option<(u32,u32)>`
- **interface**: `api.query.scheduler.lookup`
- **summary**:    Lookup from identity to the block number and index of the task. 

___


## session
 
### currentIndex(): `u32`
- **interface**: `api.query.session.currentIndex`
- **summary**:    Current index of the session. 
 
### disabledValidators(): `Vec<u32>`
- **interface**: `api.query.session.disabledValidators`
- **summary**:    Indices of disabled validators. 

   The vec is always kept sorted so that we can find whether a given validator is  disabled using binary search. It gets cleared when `on_session_ending` returns  a new set of identities. 
 
### keyOwner(`(SpCoreCryptoKeyTypeId,Bytes)`): `Option<SeedPrimitivesSignatureAccountId20>`
- **interface**: `api.query.session.keyOwner`
- **summary**:    The owner of a key. The key is the `KeyTypeId` + the encoded key. 
 
### nextKeys(`SeedPrimitivesSignatureAccountId20`): `Option<SeedRuntimeSessionKeys>`
- **interface**: `api.query.session.nextKeys`
- **summary**:    The next session keys for a validator. 
 
### queuedChanged(): `bool`
- **interface**: `api.query.session.queuedChanged`
- **summary**:    True if the underlying economic identities or weighting behind the validators  has changed in the queued validator set. 
 
### queuedKeys(): `Vec<(SeedPrimitivesSignatureAccountId20,SeedRuntimeSessionKeys)>`
- **interface**: `api.query.session.queuedKeys`
- **summary**:    The queued keys for the next session. When the next session begins, these keys  will be used to determine the validator's session keys. 
 
### validators(): `Vec<SeedPrimitivesSignatureAccountId20>`
- **interface**: `api.query.session.validators`
- **summary**:    The current set of validators. 

___


## sft
 
### sftCollectionInfo(`u32`): `Option<PalletSftSftCollectionInformation>`
- **interface**: `api.query.sft.sftCollectionInfo`
- **summary**:    Map from collection to its information 
 
### tokenInfo(`(u32,u32)`): `Option<PalletSftSftTokenInformation>`
- **interface**: `api.query.sft.tokenInfo`
- **summary**:    Map from token to its token information, including ownership information 

___


## staking
 
### activeEra(): `Option<PalletStakingActiveEraInfo>`
- **interface**: `api.query.staking.activeEra`
- **summary**:    The active era information, it holds index and start. 

   The active era is the era being currently rewarded. Validator set of this era must be  equal to [`SessionInterface::validators`]. 
 
### bonded(`SeedPrimitivesSignatureAccountId20`): `Option<SeedPrimitivesSignatureAccountId20>`
- **interface**: `api.query.staking.bonded`
- **summary**:    Map from all locked "stash" accounts to the controller account. 
 
### bondedEras(): `Vec<(u32,u32)>`
- **interface**: `api.query.staking.bondedEras`
- **summary**:    A mapping from still-bonded eras to the first session index of that era. 

   Must contains information for eras for the range:  `[active_era - bounding_duration; active_era]` 
 
### canceledSlashPayout(): `u128`
- **interface**: `api.query.staking.canceledSlashPayout`
- **summary**:    The amount of currency given to reporters of a slash event which was  canceled by extraordinary circumstances (e.g. governance). 
 
### chillThreshold(): `Option<Percent>`
- **interface**: `api.query.staking.chillThreshold`
- **summary**:    The threshold for when users can start calling `chill_other` for other validators /  nominators. The threshold is compared to the actual number of validators / nominators  (`CountFor*`) in the system compared to the configured max (`Max*Count`). 
 
### counterForNominators(): `u32`
- **interface**: `api.query.staking.counterForNominators`
- **summary**:    Counter for the related counted storage map 
 
### counterForValidators(): `u32`
- **interface**: `api.query.staking.counterForValidators`
- **summary**:    Counter for the related counted storage map 
 
### currentEra(): `Option<u32>`
- **interface**: `api.query.staking.currentEra`
- **summary**:    The current era index. 

   This is the latest planned era, depending on how the Session pallet queues the validator  set, it might be active or not. 
 
### currentPlannedSession(): `u32`
- **interface**: `api.query.staking.currentPlannedSession`
- **summary**:    The last planned session scheduled by the session pallet. 

   This is basically in sync with the call to [`pallet_session::SessionManager::new_session`]. 
 
### erasRewardPoints(`u32`): `PalletStakingEraRewardPoints`
- **interface**: `api.query.staking.erasRewardPoints`
- **summary**:    Rewards for the last `HISTORY_DEPTH` eras.  If reward hasn't been set or has been removed then 0 reward is returned. 
 
### erasStakers(`u32, SeedPrimitivesSignatureAccountId20`): `PalletStakingExposure`
- **interface**: `api.query.staking.erasStakers`
- **summary**:    Exposure of validator at era. 

   This is keyed first by the era index to allow bulk deletion and then the stash account. 

   Is it removed after `HISTORY_DEPTH` eras.  If stakers hasn't been set or has been removed then empty exposure is returned. 
 
### erasStakersClipped(`u32, SeedPrimitivesSignatureAccountId20`): `PalletStakingExposure`
- **interface**: `api.query.staking.erasStakersClipped`
- **summary**:    Clipped Exposure of validator at era. 

   This is similar to [`ErasStakers`] but number of nominators exposed is reduced to the  `T::MaxNominatorRewardedPerValidator` biggest stakers.  (Note: the field `total` and `own` of the exposure remains unchanged).  This is used to limit the i/o cost for the nominator payout. 

   This is keyed fist by the era index to allow bulk deletion and then the stash account. 

   Is it removed after `HISTORY_DEPTH` eras.  If stakers hasn't been set or has been removed then empty exposure is returned. 
 
### erasStartSessionIndex(`u32`): `Option<u32>`
- **interface**: `api.query.staking.erasStartSessionIndex`
- **summary**:    The session index at which the era start for the last `HISTORY_DEPTH` eras. 

   Note: This tracks the starting session (i.e. session index when era start being active)  for the eras in `[CurrentEra - HISTORY_DEPTH, CurrentEra]`. 
 
### erasTotalStake(`u32`): `u128`
- **interface**: `api.query.staking.erasTotalStake`
- **summary**:    The total amount staked for the last `HISTORY_DEPTH` eras.  If total hasn't been set or has been removed then 0 stake is returned. 
 
### erasValidatorPrefs(`u32, SeedPrimitivesSignatureAccountId20`): `PalletStakingValidatorPrefs`
- **interface**: `api.query.staking.erasValidatorPrefs`
- **summary**:    Similar to `ErasStakers`, this holds the preferences of validators. 

   This is keyed first by the era index to allow bulk deletion and then the stash account. 

   Is it removed after `HISTORY_DEPTH` eras. 
 
### erasValidatorReward(`u32`): `Option<u128>`
- **interface**: `api.query.staking.erasValidatorReward`
- **summary**:    The total validator era payout for the last `HISTORY_DEPTH` eras. 

   Eras that haven't finished yet or has been removed doesn't have reward. 
 
### forceEra(): `PalletStakingForcing`
- **interface**: `api.query.staking.forceEra`
- **summary**:    Mode of era forcing. 
 
### historyDepth(): `u32`
- **interface**: `api.query.staking.historyDepth`
- **summary**:    Number of eras to keep in history. 

   Information is kept for eras in `[current_era - history_depth; current_era]`. 

   Must be more than the number of eras delayed by session otherwise. I.e. active era must  always be in history. I.e. `active_era > current_era - history_depth` must be  guaranteed. 
 
### invulnerables(): `Vec<SeedPrimitivesSignatureAccountId20>`
- **interface**: `api.query.staking.invulnerables`
- **summary**:    Any validators that may never be slashed or forcibly kicked. It's a Vec since they're  easy to initialize and the performance hit is minimal (we expect no more than four  invulnerables) and restricted to testnets. 
 
### ledger(`SeedPrimitivesSignatureAccountId20`): `Option<PalletStakingStakingLedger>`
- **interface**: `api.query.staking.ledger`
- **summary**:    Map from all (unlocked) "controller" accounts to the info regarding the staking. 
 
### maxNominatorsCount(): `Option<u32>`
- **interface**: `api.query.staking.maxNominatorsCount`
- **summary**:    The maximum nominator count before we stop allowing new validators to join. 

   When this value is not set, no limits are enforced. 
 
### maxValidatorsCount(): `Option<u32>`
- **interface**: `api.query.staking.maxValidatorsCount`
- **summary**:    The maximum validator count before we stop allowing new validators to join. 

   When this value is not set, no limits are enforced. 
 
### minCommission(): `Perbill`
- **interface**: `api.query.staking.minCommission`
- **summary**:    The minimum amount of commission that validators can set. 

   If set to `0`, no limit exists. 
 
### minimumValidatorCount(): `u32`
- **interface**: `api.query.staking.minimumValidatorCount`
- **summary**:    Minimum number of staking participants before emergency conditions are imposed. 
 
### minNominatorBond(): `u128`
- **interface**: `api.query.staking.minNominatorBond`
- **summary**:    The minimum active bond to become and maintain the role of a nominator. 
 
### minValidatorBond(): `u128`
- **interface**: `api.query.staking.minValidatorBond`
- **summary**:    The minimum active bond to become and maintain the role of a validator. 
 
### nominators(`SeedPrimitivesSignatureAccountId20`): `Option<PalletStakingNominations>`
- **interface**: `api.query.staking.nominators`
- **summary**:    The map from nominator stash key to their nomination preferences, namely the validators that  they wish to support. 

   Note that the keys of this storage map might become non-decodable in case the  [`Config::MaxNominations`] configuration is decreased. In this rare case, these nominators  are still existent in storage, their key is correct and retrievable (i.e. `contains_key`  indicates that they exist), but their value cannot be decoded. Therefore, the non-decodable  nominators will effectively not-exist, until they re-submit their preferences such that it  is within the bounds of the newly set `Config::MaxNominations`. 

   This implies that `::iter_keys().count()` and `::iter().count()` might return different  values for this map. Moreover, the main `::count()` is aligned with the former, namely the  number of keys that exist. 

   Lastly, if any of the nominators become non-decodable, they can be chilled immediately via  [`Call::chill_other`] dispatchable by anyone. 
 
### nominatorSlashInEra(`u32, SeedPrimitivesSignatureAccountId20`): `Option<u128>`
- **interface**: `api.query.staking.nominatorSlashInEra`
- **summary**:    All slashing events on nominators, mapped by era to the highest slash value of the era. 
 
### offendingValidators(): `Vec<(u32,bool)>`
- **interface**: `api.query.staking.offendingValidators`
- **summary**:    Indices of validators that have offended in the active era and whether they are currently  disabled. 

   This value should be a superset of disabled validators since not all offences lead to the  validator being disabled (if there was no slash). This is needed to track the percentage of  validators that have offended in the current era, ensuring a new era is forced if  `OffendingValidatorsThreshold` is reached. The vec is always kept sorted so that we can find  whether a given validator has previously offended using binary search. It gets cleared when  the era ends. 
 
### payee(`SeedPrimitivesSignatureAccountId20`): `PalletStakingRewardDestination`
- **interface**: `api.query.staking.payee`
- **summary**:    Where the reward payment should be made. Keyed by stash. 
 
### slashingSpans(`SeedPrimitivesSignatureAccountId20`): `Option<PalletStakingSlashingSlashingSpans>`
- **interface**: `api.query.staking.slashingSpans`
- **summary**:    Slashing spans for stash accounts. 
 
### slashRewardFraction(): `Perbill`
- **interface**: `api.query.staking.slashRewardFraction`
- **summary**:    The percentage of the slash that is distributed to reporters. 

   The rest of the slashed value is handled by the `Slash`. 
 
### spanSlash(`(SeedPrimitivesSignatureAccountId20,u32)`): `PalletStakingSlashingSpanRecord`
- **interface**: `api.query.staking.spanSlash`
- **summary**:    Records information about the maximum slash of a stash within a slashing span,  as well as how much reward has been paid out. 
 
### storageVersion(): `PalletStakingReleases`
- **interface**: `api.query.staking.storageVersion`
- **summary**:    True if network has been upgraded to this version.  Storage version of the pallet. 

   This is set to v7.0.0 for new networks. 
 
### unappliedSlashes(`u32`): `Vec<PalletStakingUnappliedSlash>`
- **interface**: `api.query.staking.unappliedSlashes`
- **summary**:    All unapplied slashes that are queued for later. 
 
### validatorCount(): `u32`
- **interface**: `api.query.staking.validatorCount`
- **summary**:    The ideal number of staking participants. 
 
### validators(`SeedPrimitivesSignatureAccountId20`): `PalletStakingValidatorPrefs`
- **interface**: `api.query.staking.validators`
- **summary**:    The map from (wannabe) validator stash key to the preferences of that validator. 
 
### validatorSlashInEra(`u32, SeedPrimitivesSignatureAccountId20`): `Option<(Perbill,u128)>`
- **interface**: `api.query.staking.validatorSlashInEra`
- **summary**:    All slashing events on validators, mapped by era to the highest slash proportion  and slash value of the era. 

___


## substrate

_These are well-known keys that are always available to the runtime implementation of any Substrate-based network._
 
### changesTrieConfig(): `u32`
- **interface**: `api.query.substrate.changesTrieConfig`
- **summary**:    Changes trie configuration is stored under this key. 
 
### childStorageKeyPrefix(): `u32`
- **interface**: `api.query.substrate.childStorageKeyPrefix`
- **summary**:    Prefix of child storage keys. 
 
### code(): `Bytes`
- **interface**: `api.query.substrate.code`
- **summary**:    Wasm code of the runtime. 
 
### extrinsicIndex(): `u32`
- **interface**: `api.query.substrate.extrinsicIndex`
- **summary**:    Current extrinsic index (u32) is stored under this key. 
 
### heapPages(): `u64`
- **interface**: `api.query.substrate.heapPages`
- **summary**:    Number of wasm linear memory pages required for execution of the runtime. 

___


## sudo
 
### key(): `Option<SeedPrimitivesSignatureAccountId20>`
- **interface**: `api.query.sudo.key`
- **summary**:    The `AccountId` of the sudo key. 

___


## system
 
### account(`SeedPrimitivesSignatureAccountId20`): `FrameSystemAccountInfo`
- **interface**: `api.query.system.account`
- **summary**:    The full account information for a particular account ID. 
 
### allExtrinsicsLen(): `Option<u32>`
- **interface**: `api.query.system.allExtrinsicsLen`
- **summary**:    Total length (in bytes) for all extrinsics put together, for the current block. 
 
### blockHash(`u32`): `H256`
- **interface**: `api.query.system.blockHash`
- **summary**:    Map of block numbers to block hashes. 
 
### blockWeight(): `FrameSupportWeightsPerDispatchClassU64`
- **interface**: `api.query.system.blockWeight`
- **summary**:    The current weight for the block. 
 
### digest(): `SpRuntimeDigest`
- **interface**: `api.query.system.digest`
- **summary**:    Digest of the current block, also part of the block header. 
 
### eventCount(): `u32`
- **interface**: `api.query.system.eventCount`
- **summary**:    The number of events in the `Events<T>` list. 
 
### events(): `Vec<FrameSystemEventRecord>`
- **interface**: `api.query.system.events`
- **summary**:    Events deposited for the current block. 

   NOTE: The item is unbound and should therefore never be read on chain.  It could otherwise inflate the PoV size of a block. 

   Events have a large in-memory size. Box the events to not go out-of-memory  just in case someone still reads them from within the runtime. 
 
### eventTopics(`H256`): `Vec<(u32,u32)>`
- **interface**: `api.query.system.eventTopics`
- **summary**:    Mapping between a topic (represented by T::Hash) and a vector of indexes  of events in the `<Events<T>>` list. 

   All topic vectors have deterministic storage locations depending on the topic. This  allows light-clients to leverage the changes trie storage tracking mechanism and  in case of changes fetch the list of events of interest. 

   The value has the type `(T::BlockNumber, EventIndex)` because if we used only just  the `EventIndex` then in case if the topic has the same contents on the next block  no notification will be triggered thus the event might be lost. 
 
### executionPhase(): `Option<FrameSystemPhase>`
- **interface**: `api.query.system.executionPhase`
- **summary**:    The execution phase of the block. 
 
### extrinsicCount(): `Option<u32>`
- **interface**: `api.query.system.extrinsicCount`
- **summary**:    Total extrinsics count for the current block. 
 
### extrinsicData(`u32`): `Bytes`
- **interface**: `api.query.system.extrinsicData`
- **summary**:    Extrinsics data for the current block (maps an extrinsic's index to its data). 
 
### lastRuntimeUpgrade(): `Option<FrameSystemLastRuntimeUpgradeInfo>`
- **interface**: `api.query.system.lastRuntimeUpgrade`
- **summary**:    Stores the `spec_version` and `spec_name` of when the last runtime upgrade happened. 
 
### number(): `u32`
- **interface**: `api.query.system.number`
- **summary**:    The current block number being processed. Set by `execute_block`. 
 
### parentHash(): `H256`
- **interface**: `api.query.system.parentHash`
- **summary**:    Hash of the previous block. 
 
### upgradedToTripleRefCount(): `bool`
- **interface**: `api.query.system.upgradedToTripleRefCount`
- **summary**:    True if we have upgraded so that AccountInfo contains three types of `RefCount`. False  (default) if not. 
 
### upgradedToU32RefCount(): `bool`
- **interface**: `api.query.system.upgradedToU32RefCount`
- **summary**:    True if we have upgraded so that `type RefCount` is `u32`. False (default) if not. 

___


## timestamp
 
### didUpdate(): `bool`
- **interface**: `api.query.timestamp.didUpdate`
- **summary**:    Did the timestamp get updated in this block? 
 
### now(): `u64`
- **interface**: `api.query.timestamp.now`
- **summary**:    Current time for the current block. 

___


## tokenApprovals
 
### eRC1155ApprovalsForAll(`SeedPrimitivesSignatureAccountId20, (u32,SeedPrimitivesSignatureAccountId20)`): `Option<bool>`
- **interface**: `api.query.tokenApprovals.eRC1155ApprovalsForAll`
 
### eRC20Approvals(`(SeedPrimitivesSignatureAccountId20,u32), SeedPrimitivesSignatureAccountId20`): `Option<u128>`
- **interface**: `api.query.tokenApprovals.eRC20Approvals`
 
### eRC721Approvals(`(u32,u32)`): `Option<SeedPrimitivesSignatureAccountId20>`
- **interface**: `api.query.tokenApprovals.eRC721Approvals`
 
### eRC721ApprovalsForAll(`SeedPrimitivesSignatureAccountId20, (u32,SeedPrimitivesSignatureAccountId20)`): `Option<bool>`
- **interface**: `api.query.tokenApprovals.eRC721ApprovalsForAll`

___


## transactionPayment
 
### nextFeeMultiplier(): `u128`
- **interface**: `api.query.transactionPayment.nextFeeMultiplier`
 
### storageVersion(): `PalletTransactionPaymentReleases`
- **interface**: `api.query.transactionPayment.storageVersion`

___


## txFeePot
 
### eraTxFees(): `u128`
- **interface**: `api.query.txFeePot.eraTxFees`
- **summary**:    Accrued transaction fees in the current staking Era 

___


## voterList
 
### counterForListNodes(): `u32`
- **interface**: `api.query.voterList.counterForListNodes`
- **summary**:    Counter for the related counted storage map 
 
### listBags(`u64`): `Option<PalletBagsListListBag>`
- **interface**: `api.query.voterList.listBags`
- **summary**:    A bag stored in storage. 

   Stores a `Bag` struct, which stores head and tail pointers to itself. 
 
### listNodes(`SeedPrimitivesSignatureAccountId20`): `Option<PalletBagsListListNode>`
- **interface**: `api.query.voterList.listNodes`
- **summary**:    A single node, within some bag. 

   Nodes store links forward and back within their respective bags. 

___


## xls20
 
### relayer(): `Option<SeedPrimitivesSignatureAccountId20>`
- **interface**: `api.query.xls20.relayer`
- **summary**:    The permissioned relayer 
 
### xls20MintFee(): `u128`
- **interface**: `api.query.xls20.xls20MintFee`
- **summary**:    The extra cost of minting an XLS-20 compatible NFT 
 
### xls20TokenMap(`u32, u32`): `Option<[u8;64]>`
- **interface**: `api.query.xls20.xls20TokenMap`
- **summary**:    Maps from TRN native token_id to XLS-20 TokenId 

___


## xRPLBridge
 
### challengeXRPTransactionList(`H512`): `Option<SeedPrimitivesSignatureAccountId20>`
- **interface**: `api.query.xRPLBridge.challengeXRPTransactionList`
- **summary**:    Challenge received for a transaction mapped by hash, will be cleared when validator  validates 
 
### doorAddress(): `Option<H160>`
- **interface**: `api.query.xRPLBridge.doorAddress`
- **summary**:    The door address on XRPL 
 
### doorTicketSequence(): `u32`
- **interface**: `api.query.xRPLBridge.doorTicketSequence`
- **summary**:    The current ticket sequence of the XRPL door account 
 
### doorTicketSequenceParams(): `PalletXrplBridgeHelpersXrplTicketSequenceParams`
- **interface**: `api.query.xRPLBridge.doorTicketSequenceParams`
- **summary**:    The Ticket sequence params of the XRPL door account for the current allocation 
 
### doorTicketSequenceParamsNext(): `PalletXrplBridgeHelpersXrplTicketSequenceParams`
- **interface**: `api.query.xRPLBridge.doorTicketSequenceParamsNext`
- **summary**:    The Ticket sequence params of the XRPL door account for the next allocation 
 
### doorTxFee(): `u64`
- **interface**: `api.query.xRPLBridge.doorTxFee`
- **summary**:    The flat fee for XRPL door txs 
 
### processXRPTransaction(`u32`): `Option<Vec<H512>>`
- **interface**: `api.query.xRPLBridge.processXRPTransaction`
- **summary**:    Temporary storage to set the transactions ready to be processed at specified block number 
 
### processXRPTransactionDetails(`H512`): `Option<(u64,PalletXrplBridgeHelpersXrpTransaction,SeedPrimitivesSignatureAccountId20)>`
- **interface**: `api.query.xRPLBridge.processXRPTransactionDetails`
- **summary**:    Stores submitted transactions from XRPL waiting to be processed  Transactions will be cleared `ClearTxPeriod` blocks after processing 
 
### relayer(`SeedPrimitivesSignatureAccountId20`): `Option<bool>`
- **interface**: `api.query.xRPLBridge.relayer`
- **summary**:    List of all XRP transaction relayers 
 
### settledXRPTransactionDetails(`u32`): `Option<Vec<H512>>`
- **interface**: `api.query.xRPLBridge.settledXRPTransactionDetails`
- **summary**:    Settled xrp transactions stored as history for a specific period 
 
### ticketSequenceThresholdReachedEmitted(): `bool`
- **interface**: `api.query.xRPLBridge.ticketSequenceThresholdReachedEmitted`
- **summary**:    Keeps track whether the TicketSequenceThresholdReached event is emitted 
