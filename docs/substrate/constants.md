---
title: Constants
---

The following sections contain the module constants, also known as parameter types. These can only be changed as part of a runtime upgrade. On the api, these are exposed via `api.consts.<module>.<method>`. 

(NOTE: These were generated from a static/snapshot view of a recent default Substrate runtime. Some items may not be available in older nodes, or in any customized implementations.)

- **[assets](#assets)**

- **[assetsExt](#assetsext)**

- **[authorship](#authorship)**

- **[babe](#babe)**

- **[balances](#balances)**

- **[dex](#dex)**

- **[echo](#echo)**

- **[electionProviderMultiPhase](#electionprovidermultiphase)**

- **[feeProxy](#feeproxy)**

- **[grandpa](#grandpa)**

- **[imOnline](#imonline)**

- **[nft](#nft)**

- **[nftPeg](#nftpeg)**

- **[proxy](#proxy)**

- **[recovery](#recovery)**

- **[scheduler](#scheduler)**

- **[sft](#sft)**

- **[staking](#staking)**

- **[system](#system)**

- **[timestamp](#timestamp)**

- **[transactionPayment](#transactionpayment)**

- **[txFeePot](#txfeepot)**

- **[utility](#utility)**

- **[voterList](#voterlist)**

- **[xRPLBridge](#xrplbridge)**


___


## assets
 
### approvalDeposit: `u128`
- **interface**: `api.consts.assets.approvalDeposit`
- **summary**:    The amount of funds that must be reserved when creating a new approval. 
 
### assetAccountDeposit: `u128`
- **interface**: `api.consts.assets.assetAccountDeposit`
- **summary**:    The amount of funds that must be reserved for a non-provider asset account to be  maintained. 
 
### assetDeposit: `u128`
- **interface**: `api.consts.assets.assetDeposit`
- **summary**:    The basic amount of funds that must be reserved for an asset. 
 
### metadataDepositBase: `u128`
- **interface**: `api.consts.assets.metadataDepositBase`
- **summary**:    The basic amount of funds that must be reserved when adding metadata to your asset. 
 
### metadataDepositPerByte: `u128`
- **interface**: `api.consts.assets.metadataDepositPerByte`
- **summary**:    The additional funds that must be reserved for the number of bytes you store in your  metadata. 
 
### stringLimit: `u32`
- **interface**: `api.consts.assets.stringLimit`
- **summary**:    The maximum length of a name or symbol stored on-chain. 

___


## assetsExt
 
### maxHolds: `u32`
- **interface**: `api.consts.assetsExt.maxHolds`
- **summary**:    The maximum * of holds per asset & account 
 
### nativeAssetId: `u32`
- **interface**: `api.consts.assetsExt.nativeAssetId`
- **summary**:    The native token asset Id (managed by pallet-balances) 
 
### palletId: `FrameSupportPalletId`
- **interface**: `api.consts.assetsExt.palletId`
- **summary**:    This pallet's Id, used for deriving a sovereign account ID 

___


## authorship
 
### uncleGenerations: `u32`
- **interface**: `api.consts.authorship.uncleGenerations`
- **summary**:    The number of blocks back we should accept uncles.  This means that we will deal with uncle-parents that are  `UncleGenerations + 1` before `now`. 

___


## babe
 
### epochDuration: `u64`
- **interface**: `api.consts.babe.epochDuration`
- **summary**:    The amount of time, in slots, that each epoch should last.  NOTE: Currently it is not possible to change the epoch duration after  the chain has started. Attempting to do so will brick block production. 
 
### expectedBlockTime: `u64`
- **interface**: `api.consts.babe.expectedBlockTime`
- **summary**:    The expected average block time at which BABE should be creating  blocks. Since BABE is probabilistic it is not trivial to figure out  what the expected average block time should be based on the slot  duration and the security parameter `c` (where `1 - c` represents  the probability of a slot being empty). 
 
### maxAuthorities: `u32`
- **interface**: `api.consts.babe.maxAuthorities`
- **summary**:    Max number of authorities allowed 

___


## balances
 
### existentialDeposit: `u128`
- **interface**: `api.consts.balances.existentialDeposit`
- **summary**:    The minimum amount required to keep an account open. 
 
### maxLocks: `u32`
- **interface**: `api.consts.balances.maxLocks`
- **summary**:    The maximum number of locks that should exist on an account.  Not strictly enforced, but used for weight estimation. 
 
### maxReserves: `u32`
- **interface**: `api.consts.balances.maxReserves`
- **summary**:    The maximum number of named reserves that can exist on an account. 

___


## dex
 
### dexBurnPalletId: `FrameSupportPalletId`
- **interface**: `api.consts.dex.dexBurnPalletId`
- **summary**:    The DEX's burn id, to provide for a redundant, unredeemable minter/burner address. 
 
### getExchangeFee: `(u32,u32)`
- **interface**: `api.consts.dex.getExchangeFee`
- **summary**:    Trading fee rate  The first item of the tuple is the numerator of the fee rate, second  item is the denominator, fee_rate = numerator / denominator,  use (u32, u32) over `Rate` type to minimize internal division  operation. 
 
### lpTokenDecimals: `u8`
- **interface**: `api.consts.dex.lpTokenDecimals`
- **summary**:    Liquidity pair default token decimals 
 
### tradingPathLimit: `u32`
- **interface**: `api.consts.dex.tradingPathLimit`
- **summary**:    The limit for length of trading path 

___


## echo
 
### palletId: `FrameSupportPalletId`
- **interface**: `api.consts.echo.palletId`
- **summary**:    This pallet's Id, used for deriving a sovereign account ID 

___


## electionProviderMultiPhase
 
### betterSignedThreshold: `Perbill`
- **interface**: `api.consts.electionProviderMultiPhase.betterSignedThreshold`
- **summary**:    The minimum amount of improvement to the solution score that defines a solution as  "better" in the Signed phase. 
 
### betterUnsignedThreshold: `Perbill`
- **interface**: `api.consts.electionProviderMultiPhase.betterUnsignedThreshold`
- **summary**:    The minimum amount of improvement to the solution score that defines a solution as  "better" in the Unsigned phase. 
 
### maxElectableTargets: `u16`
- **interface**: `api.consts.electionProviderMultiPhase.maxElectableTargets`
- **summary**:    The maximum number of electable targets to put in the snapshot. 
 
### maxElectingVoters: `u32`
- **interface**: `api.consts.electionProviderMultiPhase.maxElectingVoters`
- **summary**:    The maximum number of electing voters to put in the snapshot. At the moment, snapshots  are only over a single block, but once multi-block elections are introduced they will  take place over multiple blocks. 
 
### minerTxPriority: `u64`
- **interface**: `api.consts.electionProviderMultiPhase.minerTxPriority`
- **summary**:    The priority of the unsigned transaction submitted in the unsigned-phase 
 
### offchainRepeat: `u32`
- **interface**: `api.consts.electionProviderMultiPhase.offchainRepeat`
- **summary**:    The repeat threshold of the offchain worker. 

   For example, if it is 5, that means that at least 5 blocks will elapse between attempts  to submit the worker's solution. 
 
### signedDepositBase: `u128`
- **interface**: `api.consts.electionProviderMultiPhase.signedDepositBase`
- **summary**:    Base deposit for a signed solution. 
 
### signedDepositByte: `u128`
- **interface**: `api.consts.electionProviderMultiPhase.signedDepositByte`
- **summary**:    Per-byte deposit for a signed solution. 
 
### signedDepositWeight: `u128`
- **interface**: `api.consts.electionProviderMultiPhase.signedDepositWeight`
- **summary**:    Per-weight deposit for a signed solution. 
 
### signedMaxRefunds: `u32`
- **interface**: `api.consts.electionProviderMultiPhase.signedMaxRefunds`
- **summary**:    The maximum amount of unchecked solutions to refund the call fee for. 
 
### signedMaxSubmissions: `u32`
- **interface**: `api.consts.electionProviderMultiPhase.signedMaxSubmissions`
- **summary**:    Maximum number of signed submissions that can be queued. 

   It is best to avoid adjusting this during an election, as it impacts downstream data  structures. In particular, `SignedSubmissionIndices<T>` is bounded on this value. If you  update this value during an election, you _must_ ensure that  `SignedSubmissionIndices.len()` is less than or equal to the new value. Otherwise,  attempts to submit new solutions may cause a runtime panic. 
 
### signedMaxWeight: `u64`
- **interface**: `api.consts.electionProviderMultiPhase.signedMaxWeight`
- **summary**:    Maximum weight of a signed solution. 

   If [`Config::MinerConfig`] is being implemented to submit signed solutions (outside of  this pallet), then [`MinerConfig::solution_weight`] is used to compare against  this value. 
 
### signedPhase: `u32`
- **interface**: `api.consts.electionProviderMultiPhase.signedPhase`
- **summary**:    Duration of the signed phase. 
 
### signedRewardBase: `u128`
- **interface**: `api.consts.electionProviderMultiPhase.signedRewardBase`
- **summary**:    Base reward for a signed solution 
 
### unsignedPhase: `u32`
- **interface**: `api.consts.electionProviderMultiPhase.unsignedPhase`
- **summary**:    Duration of the unsigned phase. 

___


## feeProxy
 
### feeAssetId: `u32`
- **interface**: `api.consts.feeProxy.feeAssetId`
- **summary**:    The native token asset Id (managed by pallet-balances) 

___


## grandpa
 
### maxAuthorities: `u32`
- **interface**: `api.consts.grandpa.maxAuthorities`
- **summary**:    Max Authorities in use 

___


## imOnline
 
### unsignedPriority: `u64`
- **interface**: `api.consts.imOnline.unsignedPriority`
- **summary**:    A configuration for base priority of unsigned transactions. 

   This is exposed so that it can be tuned for particular runtime, when  multiple pallets send unsigned transactions. 

___


## nft
 
### defaultListingDuration: `u32`
- **interface**: `api.consts.nft.defaultListingDuration`
- **summary**:    Default auction / sale length in blocks 
 
### palletId: `FrameSupportPalletId`
- **interface**: `api.consts.nft.palletId`
- **summary**:    This pallet's Id, used for deriving a sovereign account ID 
 
### stringLimit: `u32`
- **interface**: `api.consts.nft.stringLimit`
- **summary**:    The maximum length of a collection name, stored on-chain 

___


## nftPeg
 
### delayLength: `u32`
- **interface**: `api.consts.nftPeg.delayLength`

___


## proxy
 
### announcementDepositBase: `u128`
- **interface**: `api.consts.proxy.announcementDepositBase`
- **summary**:    The base amount of currency needed to reserve for creating an announcement. 

   This is held when a new storage item holding a `Balance` is created (typically 16  bytes). 
 
### announcementDepositFactor: `u128`
- **interface**: `api.consts.proxy.announcementDepositFactor`
- **summary**:    The amount of currency needed per announcement made. 

   This is held for adding an `AccountId`, `Hash` and `BlockNumber` (typically 68 bytes)  into a pre-existing storage value. 
 
### maxPending: `u32`
- **interface**: `api.consts.proxy.maxPending`
- **summary**:    The maximum amount of time-delayed announcements that are allowed to be pending. 
 
### maxProxies: `u32`
- **interface**: `api.consts.proxy.maxProxies`
- **summary**:    The maximum amount of proxies allowed for a single account. 
 
### proxyDepositBase: `u128`
- **interface**: `api.consts.proxy.proxyDepositBase`
- **summary**:    The base amount of currency needed to reserve for creating a proxy. 

   This is held for an additional storage item whose value size is  `sizeof(Balance)` bytes and whose key size is `sizeof(AccountId)` bytes. 
 
### proxyDepositFactor: `u128`
- **interface**: `api.consts.proxy.proxyDepositFactor`
- **summary**:    The amount of currency needed per proxy added. 

   This is held for adding 32 bytes plus an instance of `ProxyType` more into a  pre-existing storage value. Thus, when configuring `ProxyDepositFactor` one should take  into account `32 + proxy_type.encode().len()` bytes of data. 

___


## recovery
 
### configDepositBase: `u128`
- **interface**: `api.consts.recovery.configDepositBase`
- **summary**:    The base amount of currency needed to reserve for creating a recovery configuration. 

   This is held for an additional storage item whose value size is  `2 + sizeof(BlockNumber, Balance)` bytes. 
 
### friendDepositFactor: `u128`
- **interface**: `api.consts.recovery.friendDepositFactor`
- **summary**:    The amount of currency needed per additional user when creating a recovery  configuration. 

   This is held for adding `sizeof(AccountId)` bytes more into a pre-existing storage  value. 
 
### maxFriends: `u32`
- **interface**: `api.consts.recovery.maxFriends`
- **summary**:    The maximum amount of friends allowed in a recovery configuration. 

   NOTE: The threshold programmed in this Pallet uses u16, so it does  not really make sense to have a limit here greater than u16::MAX.  But also, that is a lot more than you should probably set this value  to anyway... 
 
### recoveryDeposit: `u128`
- **interface**: `api.consts.recovery.recoveryDeposit`
- **summary**:    The base amount of currency needed to reserve for starting a recovery. 

   This is primarily held for deterring malicious recovery attempts, and should  have a value large enough that a bad actor would choose not to place this  deposit. It also acts to fund additional storage item whose value size is  `sizeof(BlockNumber, Balance + T * AccountId)` bytes. Where T is a configurable  threshold. 

___


## scheduler
 
### maximumWeight: `u64`
- **interface**: `api.consts.scheduler.maximumWeight`
- **summary**:    The maximum weight that may be scheduled per block for any dispatchables of less  priority than `schedule::HARD_DEADLINE`. 
 
### maxScheduledPerBlock: `u32`
- **interface**: `api.consts.scheduler.maxScheduledPerBlock`
- **summary**:    The maximum number of scheduled calls in the queue for a single block.  Not strictly enforced, but used for weight estimation. 

___


## sft
 
### maxOwnersPerSftToken: `u32`
- **interface**: `api.consts.sft.maxOwnersPerSftToken`
- **summary**:    Max unique owners that can own an SFT token 
 
### maxSerialsPerMint: `u32`
- **interface**: `api.consts.sft.maxSerialsPerMint`
- **summary**:    Max tokens that can be minted in one transaction 
 
### maxTokensPerSftCollection: `u32`
- **interface**: `api.consts.sft.maxTokensPerSftCollection`
- **summary**:    Max tokens that a collection can contain 
 
### palletId: `FrameSupportPalletId`
- **interface**: `api.consts.sft.palletId`
- **summary**:    This pallet's Id, used for deriving a sovereign account ID 
 
### stringLimit: `u32`
- **interface**: `api.consts.sft.stringLimit`
- **summary**:    The maximum length of a collection or token name, stored on-chain 

___


## staking
 
### bondingDuration: `u32`
- **interface**: `api.consts.staking.bondingDuration`
- **summary**:    Number of eras that staked funds must remain bonded for. 
 
### maxNominations: `u32`
- **interface**: `api.consts.staking.maxNominations`
- **summary**:    Maximum number of nominations per nominator. 
 
### maxNominatorRewardedPerValidator: `u32`
- **interface**: `api.consts.staking.maxNominatorRewardedPerValidator`
- **summary**:    The maximum number of nominators rewarded for each validator. 

   For each validator only the `$MaxNominatorRewardedPerValidator` biggest stakers can  claim their reward. This used to limit the i/o cost for the nominator payout. 
 
### maxUnlockingChunks: `u32`
- **interface**: `api.consts.staking.maxUnlockingChunks`
- **summary**:    The maximum number of `unlocking` chunks a [`StakingLedger`] can have. Effectively  determines how many unique eras a staker may be unbonding in. 
 
### sessionsPerEra: `u32`
- **interface**: `api.consts.staking.sessionsPerEra`
- **summary**:    Number of sessions per era. 
 
### slashDeferDuration: `u32`
- **interface**: `api.consts.staking.slashDeferDuration`
- **summary**:    Number of eras that slashes are deferred by, after computation. 

   This should be less than the bonding duration. Set to 0 if slashes  should be applied immediately, without opportunity for intervention. 

___


## system
 
### blockHashCount: `u32`
- **interface**: `api.consts.system.blockHashCount`
- **summary**:    Maximum number of block number to block hash mappings to keep (oldest pruned first). 
 
### blockLength: `FrameSystemLimitsBlockLength`
- **interface**: `api.consts.system.blockLength`
- **summary**:    The maximum length of a block (in bytes). 
 
### blockWeights: `FrameSystemLimitsBlockWeights`
- **interface**: `api.consts.system.blockWeights`
- **summary**:    Block & extrinsics weights: base values and limits. 
 
### dbWeight: `FrameSupportWeightsRuntimeDbWeight`
- **interface**: `api.consts.system.dbWeight`
- **summary**:    The weight of runtime database operations the runtime can invoke. 
 
### ss58Prefix: `u16`
- **interface**: `api.consts.system.ss58Prefix`
- **summary**:    The designated SS85 prefix of this chain. 

   This replaces the "ss58Format" property declared in the chain spec. Reason is  that the runtime should know about the prefix in order to make use of it as  an identifier of the chain. 
 
### version: `SpVersionRuntimeVersion`
- **interface**: `api.consts.system.version`
- **summary**:    Get the chain's current version. 

___


## timestamp
 
### minimumPeriod: `u64`
- **interface**: `api.consts.timestamp.minimumPeriod`
- **summary**:    The minimum period between blocks. Beware that this is different to the *expected*  period that the block production apparatus provides. Your chosen consensus system will  generally work with this to determine a sensible block time. e.g. For Aura, it will be  double this period on default settings. 

___


## transactionPayment
 
### operationalFeeMultiplier: `u8`
- **interface**: `api.consts.transactionPayment.operationalFeeMultiplier`
- **summary**:    A fee mulitplier for `Operational` extrinsics to compute "virtual tip" to boost their  `priority` 

   This value is multipled by the `final_fee` to obtain a "virtual tip" that is later  added to a tip component in regular `priority` calculations.  It means that a `Normal` transaction can front-run a similarly-sized `Operational`  extrinsic (with no tip), by including a tip value greater than the virtual tip. 

   ```rust,ignore  // For `Normal`  let priority = priority_calc(tip); 

   // For `Operational`  let virtual_tip = (inclusion_fee + tip) * OperationalFeeMultiplier;  let priority = priority_calc(tip + virtual_tip);  ``` 

   Note that since we use `final_fee` the multiplier applies also to the regular `tip`  sent with the transaction. So, not only does the transaction get a priority bump based  on the `inclusion_fee`, but we also amplify the impact of tips applied to `Operational`  transactions. 

___


## txFeePot
 
### txFeePotId: `FrameSupportPalletId`
- **interface**: `api.consts.txFeePot.txFeePotId`

___


## utility
 
### batchedCallsLimit: `u32`
- **interface**: `api.consts.utility.batchedCallsLimit`
- **summary**:    The limit on the number of batched calls. 

___


## voterList
 
### bagThresholds: `Vec<u64>`
- **interface**: `api.consts.voterList.bagThresholds`
- **summary**:    The list of thresholds separating the various bags. 

   Ids are separated into unsorted bags according to their score. This specifies the  thresholds separating the bags. An id's bag is the largest bag for which the id's score  is less than or equal to its upper threshold. 

   When ids are iterated, higher bags are iterated completely before lower bags. This means  that iteration is _semi-sorted_: ids of higher score tend to come before ids of lower  score, but peer ids within a particular bag are sorted in insertion order. 

   #### Expressing the constant 

   This constant must be sorted in strictly increasing order. Duplicate items are not  permitted. 

   There is an implied upper limit of `Score::MAX`; that value does not need to be  specified within the bag. For any two threshold lists, if one ends with  `Score::MAX`, the other one does not, and they are otherwise equal, the two  lists will behave identically. 

   #### Calculation 

   It is recommended to generate the set of thresholds in a geometric series, such that  there exists some constant ratio such that `threshold[k + 1] == (threshold[k] *  constant_ratio).max(threshold[k] + 1)` for all `k`. 

   The helpers in the `/utils/frame/generate-bags` module can simplify this calculation. 

   #### Examples 

   - If `BagThresholds::get().is_empty()`, then all ids are put into the same bag, and  iteration is strictly in insertion order. 

  - If `BagThresholds::get().len() == 64`, and the thresholds are determined according to the procedure given above, then the constant ratio is equal to 2. 

  - If `BagThresholds::get().len() == 200`, and the thresholds are determined according to the procedure given above, then the constant ratio is approximately equal to 1.248. 

  - If the threshold list begins `[1, 2, 3, ...]`, then an id with score 0 or 1 will fall into bag 0, an id with score 2 will fall into bag 1, etc. 

   #### Migration 

   In the event that this list ever changes, a copy of the old bags list must be retained.  With that `List::migrate` can be called, which will perform the appropriate migration. 

___


## xRPLBridge
 
### challengePeriod: `u32`
- **interface**: `api.consts.xRPLBridge.challengePeriod`
- **summary**:    Challenge Period to wait for a challenge before processing the transaction 
 
### clearTxPeriod: `u32`
- **interface**: `api.consts.xRPLBridge.clearTxPeriod`
- **summary**:    Clear Period to wait for a transaction to be cleared from settled storages 
 
### xrpAssetId: `u32`
- **interface**: `api.consts.xRPLBridge.xrpAssetId`
- **summary**:    XRP Asset Id set at runtime 
