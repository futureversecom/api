---
title: Events
---

Events are emitted for certain operations on the runtime. The following sections describe the events that are part of the default Substrate runtime. 

(NOTE: These were generated from a static/snapshot view of a recent default Substrate runtime. Some items may not be available in older nodes, or in any customized implementations.)

- **[assets](#assets)**

- **[assetsExt](#assetsext)**

- **[balances](#balances)**

- **[dex](#dex)**

- **[echo](#echo)**

- **[electionProviderMultiPhase](#electionprovidermultiphase)**

- **[erc20Peg](#erc20peg)**

- **[ethBridge](#ethbridge)**

- **[ethereum](#ethereum)**

- **[evm](#evm)**

- **[evmChainId](#evmchainid)**

- **[feeControl](#feecontrol)**

- **[feeProxy](#feeproxy)**

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

- **[sudo](#sudo)**

- **[system](#system)**

- **[transactionPayment](#transactionpayment)**

- **[utility](#utility)**

- **[voterList](#voterlist)**

- **[xls20](#xls20)**

- **[xrplBridge](#xrplbridge)**


___


## assets
 
### ApprovalCancelled(`u32`, `SeedPrimitivesSignatureAccountId20`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.assets.ApprovalCancelled.is`
- **summary**:    An approval for account `delegate` was cancelled by `owner`. 
 
### ApprovedTransfer(`u32`, `SeedPrimitivesSignatureAccountId20`, `SeedPrimitivesSignatureAccountId20`, `u128`)
- **interface**: `api.events.assets.ApprovedTransfer.is`
- **summary**:    (Additional) funds have been approved for transfer to a destination account. 
 
### AssetFrozen(`u32`)
- **interface**: `api.events.assets.AssetFrozen.is`
- **summary**:    Some asset `asset_id` was frozen. 
 
### AssetStatusChanged(`u32`)
- **interface**: `api.events.assets.AssetStatusChanged.is`
- **summary**:    An asset has had its attributes changed by the `Force` origin. 
 
### AssetThawed(`u32`)
- **interface**: `api.events.assets.AssetThawed.is`
- **summary**:    Some asset `asset_id` was thawed. 
 
### Burned(`u32`, `SeedPrimitivesSignatureAccountId20`, `u128`)
- **interface**: `api.events.assets.Burned.is`
- **summary**:    Some assets were destroyed. 
 
### Created(`u32`, `SeedPrimitivesSignatureAccountId20`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.assets.Created.is`
- **summary**:    Some asset class was created. 
 
### Destroyed(`u32`)
- **interface**: `api.events.assets.Destroyed.is`
- **summary**:    An asset class was destroyed. 
 
### ForceCreated(`u32`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.assets.ForceCreated.is`
- **summary**:    Some asset class was force-created. 
 
### Frozen(`u32`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.assets.Frozen.is`
- **summary**:    Some account `who` was frozen. 
 
### Issued(`u32`, `SeedPrimitivesSignatureAccountId20`, `u128`)
- **interface**: `api.events.assets.Issued.is`
- **summary**:    Some assets were issued. 
 
### MetadataCleared(`u32`)
- **interface**: `api.events.assets.MetadataCleared.is`
- **summary**:    Metadata has been cleared for an asset. 
 
### MetadataSet(`u32`, `Bytes`, `Bytes`, `u8`, `bool`)
- **interface**: `api.events.assets.MetadataSet.is`
- **summary**:    New metadata has been set for an asset. 
 
### OwnerChanged(`u32`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.assets.OwnerChanged.is`
- **summary**:    The owner changed. 
 
### TeamChanged(`u32`, `SeedPrimitivesSignatureAccountId20`, `SeedPrimitivesSignatureAccountId20`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.assets.TeamChanged.is`
- **summary**:    The management team changed. 
 
### Thawed(`u32`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.assets.Thawed.is`
- **summary**:    Some account `who` was thawed. 
 
### Transferred(`u32`, `SeedPrimitivesSignatureAccountId20`, `SeedPrimitivesSignatureAccountId20`, `u128`)
- **interface**: `api.events.assets.Transferred.is`
- **summary**:    Some assets were transferred. 
 
### TransferredApproved(`u32`, `SeedPrimitivesSignatureAccountId20`, `SeedPrimitivesSignatureAccountId20`, `SeedPrimitivesSignatureAccountId20`, `u128`)
- **interface**: `api.events.assets.TransferredApproved.is`
- **summary**:    An `amount` was transferred in its entirety from `owner` to `destination` by  the approved `delegate`. 

___


## assetsExt
 
### CreateAsset(`u32`, `SeedPrimitivesSignatureAccountId20`, `u128`)
- **interface**: `api.events.assetsExt.CreateAsset.is`
- **summary**:    New asset has been created 
 
### InternalDeposit(`u32`, `SeedPrimitivesSignatureAccountId20`, `u128`)
- **interface**: `api.events.assetsExt.InternalDeposit.is`
- **summary**:    Assets were deposited into this account by the system e.g. refunding gas 
 
### InternalWithdraw(`u32`, `SeedPrimitivesSignatureAccountId20`, `u128`)
- **interface**: `api.events.assetsExt.InternalWithdraw.is`
- **summary**:    Assets were withdrawn from this account by the system e.g. paying tx fees 
 
### PlaceHold(`u32`, `SeedPrimitivesSignatureAccountId20`, `u128`, `[u8;8]`)
- **interface**: `api.events.assetsExt.PlaceHold.is`
- **summary**:    Some assets have been placed on hold by a pallet 
 
### ReleaseHold(`u32`, `SeedPrimitivesSignatureAccountId20`, `u128`, `[u8;8]`)
- **interface**: `api.events.assetsExt.ReleaseHold.is`
- **summary**:    Some held assets have been released by a pallet 
 
### SpendHold(`u32`, `SeedPrimitivesSignatureAccountId20`, `Vec<(SeedPrimitivesSignatureAccountId20,u128)>`, `[u8;8]`)
- **interface**: `api.events.assetsExt.SpendHold.is`
- **summary**:    Some held assets were spend by a pallet 
 
### SplitTransfer(`u32`, `SeedPrimitivesSignatureAccountId20`, `Vec<(SeedPrimitivesSignatureAccountId20,u128)>`)
- **interface**: `api.events.assetsExt.SplitTransfer.is`
- **summary**:    Multi-part transfer of assets from who 

___


## balances
 
### BalanceSet(`SeedPrimitivesSignatureAccountId20`, `u128`, `u128`)
- **interface**: `api.events.balances.BalanceSet.is`
- **summary**:    A balance was set by root. 
 
### Deposit(`SeedPrimitivesSignatureAccountId20`, `u128`)
- **interface**: `api.events.balances.Deposit.is`
- **summary**:    Some amount was deposited (e.g. for transaction fees). 
 
### DustLost(`SeedPrimitivesSignatureAccountId20`, `u128`)
- **interface**: `api.events.balances.DustLost.is`
- **summary**:    An account was removed whose balance was non-zero but below ExistentialDeposit,  resulting in an outright loss. 
 
### Endowed(`SeedPrimitivesSignatureAccountId20`, `u128`)
- **interface**: `api.events.balances.Endowed.is`
- **summary**:    An account was created with some free balance. 
 
### Reserved(`SeedPrimitivesSignatureAccountId20`, `u128`)
- **interface**: `api.events.balances.Reserved.is`
- **summary**:    Some balance was reserved (moved from free to reserved). 
 
### ReserveRepatriated(`SeedPrimitivesSignatureAccountId20`, `SeedPrimitivesSignatureAccountId20`, `u128`, `FrameSupportTokensMiscBalanceStatus`)
- **interface**: `api.events.balances.ReserveRepatriated.is`
- **summary**:    Some balance was moved from the reserve of the first account to the second account.  Final argument indicates the destination balance type. 
 
### Slashed(`SeedPrimitivesSignatureAccountId20`, `u128`)
- **interface**: `api.events.balances.Slashed.is`
- **summary**:    Some amount was removed from the account (e.g. for misbehavior). 
 
### Transfer(`SeedPrimitivesSignatureAccountId20`, `SeedPrimitivesSignatureAccountId20`, `u128`)
- **interface**: `api.events.balances.Transfer.is`
- **summary**:    Transfer succeeded. 
 
### Unreserved(`SeedPrimitivesSignatureAccountId20`, `u128`)
- **interface**: `api.events.balances.Unreserved.is`
- **summary**:    Some balance was unreserved (moved from reserved to free). 
 
### Withdraw(`SeedPrimitivesSignatureAccountId20`, `u128`)
- **interface**: `api.events.balances.Withdraw.is`
- **summary**:    Some amount was withdrawn from the account (e.g. for transaction fees). 

___


## dex
 
### AddLiquidity(`SeedPrimitivesSignatureAccountId20`, `u32`, `u128`, `u32`, `u128`, `u128`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.dex.AddLiquidity.is`
- **summary**:    Add liquidity success. \[who, asset_id_0, reserve_0_increment,  asset_id_1, reserve_1_increment, share_increment, to\] 
 
### AddProvision(`SeedPrimitivesSignatureAccountId20`, `u32`, `u128`, `u32`, `u128`)
- **interface**: `api.events.dex.AddProvision.is`
- **summary**:    add provision success \[who, asset_id_0, contribution_0,  asset_id_1, contribution_1\] 
 
### DisableTradingPair(`PalletDexTradingPair`)
- **interface**: `api.events.dex.DisableTradingPair.is`
- **summary**:    Disable trading pair. \[trading_pair\] 
 
### EnableTradingPair(`PalletDexTradingPair`)
- **interface**: `api.events.dex.EnableTradingPair.is`
- **summary**:    Enable trading pair. \[trading_pair\] 
 
### ProvisioningToEnabled(`PalletDexTradingPair`, `u128`, `u128`, `u128`)
- **interface**: `api.events.dex.ProvisioningToEnabled.is`
- **summary**:    Provisioning trading pair convert to Enabled. \[trading_pair,  pool_0_amount, pool_1_amount, total_share_amount\] 
 
### RemoveLiquidity(`SeedPrimitivesSignatureAccountId20`, `u32`, `u128`, `u32`, `u128`, `u128`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.dex.RemoveLiquidity.is`
- **summary**:    Remove liquidity from the trading pool success. \[who,  asset_id_0, reserve_0_decrement, asset_id_1, reserve_1_decrement,  share_decrement, to\] 
 
### Swap(`SeedPrimitivesSignatureAccountId20`, `Vec<u32>`, `u128`, `u128`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.dex.Swap.is`
- **summary**:    Use supply Asset to swap target Asset. \[trader, trading_path,  supply_Asset_amount, target_Asset_amount, to\] 

___


## echo
 
### PingReceived(`u64`, `H160`, `Bytes`)
- **interface**: `api.events.echo.PingReceived.is`
- **summary**:    A ping was received from Ethereum 
 
### PingSent(`u64`, `H160`, `H160`, `u64`)
- **interface**: `api.events.echo.PingSent.is`
- **summary**:    A ping message was sent to Ethereum 
 
### PongReceived(`u64`, `H160`, `Bytes`)
- **interface**: `api.events.echo.PongReceived.is`
- **summary**:    A pong response was received from Ethereum 
 
### PongSent(`u64`, `H160`, `H160`, `u64`)
- **interface**: `api.events.echo.PongSent.is`
- **summary**:    A pong message was sent to Ethereum 

___


## electionProviderMultiPhase
 
### ElectionFinalized(`Option<PalletElectionProviderMultiPhaseElectionCompute>`)
- **interface**: `api.events.electionProviderMultiPhase.ElectionFinalized.is`
- **summary**:    The election has been finalized, with `Some` of the given computation, or else if the  election failed, `None`. 
 
### Rewarded(`SeedPrimitivesSignatureAccountId20`, `u128`)
- **interface**: `api.events.electionProviderMultiPhase.Rewarded.is`
- **summary**:    An account has been rewarded for their signed submission being finalized. 
 
### SignedPhaseStarted(`u32`)
- **interface**: `api.events.electionProviderMultiPhase.SignedPhaseStarted.is`
- **summary**:    The signed phase of the given round has started. 
 
### Slashed(`SeedPrimitivesSignatureAccountId20`, `u128`)
- **interface**: `api.events.electionProviderMultiPhase.Slashed.is`
- **summary**:    An account has been slashed for submitting an invalid signed submission. 
 
### SolutionStored(`PalletElectionProviderMultiPhaseElectionCompute`, `bool`)
- **interface**: `api.events.electionProviderMultiPhase.SolutionStored.is`
- **summary**:    A solution was stored with the given compute. 

   If the solution is signed, this means that it hasn't yet been processed. If the  solution is unsigned, this means that it has also been processed. 

   The `bool` is `true` when a previous solution was ejected to make room for this one. 
 
### UnsignedPhaseStarted(`u32`)
- **interface**: `api.events.electionProviderMultiPhase.UnsignedPhaseStarted.is`
- **summary**:    The unsigned phase of the given round has started. 

___


## erc20Peg
 
### DelayedErc20DepositFailed(`u64`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.erc20Peg.DelayedErc20DepositFailed.is`
- **summary**:    A delayed erc20 deposit has failed (payment_id, beneficiary) 
 
### DelayedErc20WithdrawalFailed(`u32`, `H160`)
- **interface**: `api.events.erc20Peg.DelayedErc20WithdrawalFailed.is`
- **summary**:    A delayed erc20 withdrawal has failed (asset_id, beneficiary) 
 
### Erc20Deposit(`u32`, `u128`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.erc20Peg.Erc20Deposit.is`
- **summary**:    A bridged erc20 deposit succeeded. (asset, amount, beneficiary) 
 
### Erc20DepositDelayed(`u64`, `u32`, `u128`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.erc20Peg.Erc20DepositDelayed.is`
- **summary**:    An erc20 deposit has been delayed.(payment_id, scheduled block, amount, beneficiary) 
 
### Erc20DepositFail(`H160`, `Bytes`)
- **interface**: `api.events.erc20Peg.Erc20DepositFail.is`
- **summary**:    A bridged erc20 deposit failed. (source address, abi data) 
 
### Erc20Withdraw(`u32`, `u128`, `H160`)
- **interface**: `api.events.erc20Peg.Erc20Withdraw.is`
- **summary**:    Tokens were burnt for withdrawal on Ethereum as ERC20s (asset, amount, beneficiary) 
 
### Erc20WithdrawalDelayed(`u64`, `u32`, `u128`, `H160`)
- **interface**: `api.events.erc20Peg.Erc20WithdrawalDelayed.is`
- **summary**:    A withdrawal has been delayed.(payment_id, scheduled block, amount, beneficiary) 
 
### NoAvailableDelayedPaymentIds()
- **interface**: `api.events.erc20Peg.NoAvailableDelayedPaymentIds.is`
- **summary**:    There are no more payment ids available, they've been exhausted 
 
### PaymentDelaySet(`u32`, `u128`, `u32`)
- **interface**: `api.events.erc20Peg.PaymentDelaySet.is`
- **summary**:    A delay was added for an asset_id (asset_id, min_balance, delay) 
 
### SetContractAddress(`H160`)
- **interface**: `api.events.erc20Peg.SetContractAddress.is`
- **summary**:    The peg contract address has been set 

___


## ethBridge
 
### AuthoritySetChange(`u64`, `u64`)
- **interface**: `api.events.ethBridge.AuthoritySetChange.is`
- **summary**:    A notary (validator) set change is in motion (event_id, new_validator_set_id)  A proof for the change will be generated with the given `event_id` 
 
### Challenged(`u64`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.ethBridge.Challenged.is`
- **summary**:    An event has been challenged (claim_id, challenger) 
 
### EventSend(`u64`, `PalletEthyEthySigningRequest`)
- **interface**: `api.events.ethBridge.EventSend.is`
- **summary**:    An event proof has been sent for signing by ethy-gadget 
 
### EventSubmit(`u64`, `PalletEthyEventClaim`, `u32`)
- **interface**: `api.events.ethBridge.EventSubmit.is`
- **summary**:    An event has been submitted from Ethereum (event_claim_id, event_claim, process_at) 
 
### FinaliseScheduleFail(`u32`)
- **interface**: `api.events.ethBridge.FinaliseScheduleFail.is`
- **summary**:    The schedule to unpause the bridge has failed (scheduled_block) 
 
### Invalid(`u64`)
- **interface**: `api.events.ethBridge.Invalid.is`
- **summary**:    Verifying an event failed 
 
### ProcessAtExtended(`u64`, `u32`)
- **interface**: `api.events.ethBridge.ProcessAtExtended.is`
- **summary**:    The event is still awaiting consensus. Process block pushed out (claim_id, process_at) 
 
### ProcessingFailed(`u64`, `SeedPalletCommonEventRouterError`)
- **interface**: `api.events.ethBridge.ProcessingFailed.is`
- **summary**:    Processing an event failed 
 
### ProcessingOk(`u64`)
- **interface**: `api.events.ethBridge.ProcessingOk.is`
- **summary**:    Processing an event succeeded 
 
### ProofDelayed(`u64`)
- **interface**: `api.events.ethBridge.ProofDelayed.is`
- **summary**:    Generating event proof delayed as bridge is paused 
 
### RelayerBondDeposit(`SeedPrimitivesSignatureAccountId20`, `u128`)
- **interface**: `api.events.ethBridge.RelayerBondDeposit.is`
- **summary**:    An account has deposited a relayer bond 
 
### RelayerBondWithdraw(`SeedPrimitivesSignatureAccountId20`, `u128`)
- **interface**: `api.events.ethBridge.RelayerBondWithdraw.is`
- **summary**:    An account has withdrawn a relayer bond 
 
### RelayerSet(`Option<SeedPrimitivesSignatureAccountId20>`)
- **interface**: `api.events.ethBridge.RelayerSet.is`
- **summary**:    A new relayer has been set 
 
### SetContractAddress(`H160`)
- **interface**: `api.events.ethBridge.SetContractAddress.is`
- **summary**:    The bridge contract address has been set 
 
### Verified(`u64`)
- **interface**: `api.events.ethBridge.Verified.is`
- **summary**:    Verifying an event succeeded 
 
### XrplAuthoritySetChange(`u64`, `u64`)
- **interface**: `api.events.ethBridge.XrplAuthoritySetChange.is`
- **summary**:    A notary (validator) set change for Xrpl is in motion (event_id, new_validator_set_id)  A proof for the change will be generated with the given `event_id` 
 
### XrplAuthoritySetChangeRequestFailed()
- **interface**: `api.events.ethBridge.XrplAuthoritySetChangeRequestFailed.is`
- **summary**:    Xrpl authority set change request failed 
 
### XrplDoorSignersSet()
- **interface**: `api.events.ethBridge.XrplDoorSignersSet.is`
- **summary**:    Xrpl Door signers are set 

___


## ethereum
 
### Executed(`H160`, `H160`, `H256`, `EvmCoreErrorExitReason`)
- **interface**: `api.events.ethereum.Executed.is`
- **summary**:    An ethereum transaction was successfully executed. 

___


## evm
 
### Created(`H160`)
- **interface**: `api.events.evm.Created.is`
- **summary**:    A contract has been created at given address. 
 
### CreatedFailed(`H160`)
- **interface**: `api.events.evm.CreatedFailed.is`
- **summary**:    A contract was attempted to be created, but the execution failed. 
 
### Executed(`H160`)
- **interface**: `api.events.evm.Executed.is`
- **summary**:    A contract has been executed successfully with states applied. 
 
### ExecutedFailed(`H160`)
- **interface**: `api.events.evm.ExecutedFailed.is`
- **summary**:    A contract has been executed with errors. States are reverted with only gas fees applied. 
 
### Log(`EthereumLog`)
- **interface**: `api.events.evm.Log.is`
- **summary**:    Ethereum events from contracts. 

___


## evmChainId
 
### ChainIdSet(`u64`)
- **interface**: `api.events.evmChainId.ChainIdSet.is`

___


## feeControl

___


## feeProxy
 
### CallWithFeePreferences(`SeedPrimitivesSignatureAccountId20`, `u32`, `u128`)
- **interface**: `api.events.feeProxy.CallWithFeePreferences.is`
- **summary**:    A call was made with specified payment asset 

___


## futurepass
 
### DefaultFuturepassSet(`SeedPrimitivesSignatureAccountId20`, `Option<SeedPrimitivesSignatureAccountId20>`)
- **interface**: `api.events.futurepass.DefaultFuturepassSet.is`
- **summary**:    Futurepass set as default proxy 
 
### DelegateRegistered(`SeedPrimitivesSignatureAccountId20`, `SeedPrimitivesSignatureAccountId20`, `SeedRuntimeImplsProxyType`)
- **interface**: `api.events.futurepass.DelegateRegistered.is`
- **summary**:    Delegate registration to Futurepass account 
 
### DelegateUnregistered(`SeedPrimitivesSignatureAccountId20`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.futurepass.DelegateUnregistered.is`
- **summary**:    Delegate unregistration from Futurepass account 
 
### FuturepassAssetsMigrated(`SeedPrimitivesSignatureAccountId20`, `SeedPrimitivesSignatureAccountId20`, `Vec<u32>`, `Vec<u32>`)
- **interface**: `api.events.futurepass.FuturepassAssetsMigrated.is`
- **summary**:    Migration of Futurepass assets 
 
### FuturepassCreated(`SeedPrimitivesSignatureAccountId20`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.futurepass.FuturepassCreated.is`
- **summary**:    Futurepass creation 
 
### FuturepassMigratorSet(`SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.futurepass.FuturepassMigratorSet.is`
- **summary**:    Updating Futurepass migrator account 
 
### FuturepassTransferred(`SeedPrimitivesSignatureAccountId20`, `Option<SeedPrimitivesSignatureAccountId20>`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.futurepass.FuturepassTransferred.is`
- **summary**:    Futurepass transfer 
 
### ProxyExecuted(`SeedPrimitivesSignatureAccountId20`, `Result<Null, SpRuntimeDispatchError>`)
- **interface**: `api.events.futurepass.ProxyExecuted.is`
- **summary**:    A proxy call was executed with the given call 

___


## grandpa
 
### NewAuthorities(`Vec<(SpFinalityGrandpaAppPublic,u64)>`)
- **interface**: `api.events.grandpa.NewAuthorities.is`
- **summary**:    New authority set has been applied. 
 
### Paused()
- **interface**: `api.events.grandpa.Paused.is`
- **summary**:    Current authority set has been paused. 
 
### Resumed()
- **interface**: `api.events.grandpa.Resumed.is`
- **summary**:    Current authority set has been resumed. 

___


## imOnline
 
### AllGood()
- **interface**: `api.events.imOnline.AllGood.is`
- **summary**:    At the end of the session, no offence was committed. 
 
### HeartbeatReceived(`PalletImOnlineSr25519AppSr25519Public`)
- **interface**: `api.events.imOnline.HeartbeatReceived.is`
- **summary**:    A new heartbeat was received from `AuthorityId`. 
 
### SomeOffline(`Vec<(SeedPrimitivesSignatureAccountId20,PalletStakingExposure)>`)
- **interface**: `api.events.imOnline.SomeOffline.is`
- **summary**:    At the end of the session, at least one validator was found to be offline. 

___


## nft
 
### AuctionClose(`u32`, `u128`, `PalletNftAuctionClosureReason`)
- **interface**: `api.events.nft.AuctionClose.is`
- **summary**:    An auction has closed without selling 
 
### AuctionOpen(`u32`, `Vec<u32>`, `u32`, `u128`, `u128`, `Option<u32>`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.nft.AuctionOpen.is`
- **summary**:    An auction has opened 
 
### AuctionSold(`u32`, `u128`, `u32`, `u128`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.nft.AuctionSold.is`
- **summary**:    An auction has sold 
 
### BaseUriSet(`u32`, `Bytes`)
- **interface**: `api.events.nft.BaseUriSet.is`
- **summary**:    Base URI was set 
 
### Bid(`u32`, `Vec<u32>`, `u128`, `u128`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.nft.Bid.is`
- **summary**:    A new highest bid was placed 
 
### BridgedMint(`u32`, `Vec<u32>`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.nft.BridgedMint.is`
- **summary**:    Token(s) were bridged 
 
### Burn(`u32`, `u32`)
- **interface**: `api.events.nft.Burn.is`
- **summary**:    A token was burned 
 
### CollectionClaimed(`SeedPrimitivesSignatureAccountId20`, `u32`)
- **interface**: `api.events.nft.CollectionClaimed.is`
- **summary**:    Collection has been claimed 
 
### CollectionCreate(`u32`, `u32`, `Option<u32>`, `SeedPrimitivesSignatureAccountId20`, `Bytes`, `Bytes`, `Option<SeedPrimitivesNftRoyaltiesSchedule>`, `SeedPrimitivesNftOriginChain`, `PalletNftCrossChainCompatibility`)
- **interface**: `api.events.nft.CollectionCreate.is`
- **summary**:    A new collection of tokens was created 
 
### FixedPriceSaleClose(`u32`, `Vec<u32>`, `u128`, `PalletNftFixedPriceClosureReason`)
- **interface**: `api.events.nft.FixedPriceSaleClose.is`
- **summary**:    A fixed price sale has closed without selling 
 
### FixedPriceSaleComplete(`u32`, `Vec<u32>`, `u128`, `u128`, `u32`, `SeedPrimitivesSignatureAccountId20`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.nft.FixedPriceSaleComplete.is`
- **summary**:    A fixed price sale has completed 
 
### FixedPriceSaleList(`u32`, `Vec<u32>`, `u128`, `Option<u32>`, `u128`, `u32`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.nft.FixedPriceSaleList.is`
- **summary**:    A fixed price sale has been listed 
 
### FixedPriceSalePriceUpdate(`u32`, `Vec<u32>`, `u128`, `u128`)
- **interface**: `api.events.nft.FixedPriceSalePriceUpdate.is`
- **summary**:    A fixed price sale has had its price updated 
 
### MarketplaceRegister(`SeedPrimitivesSignatureAccountId20`, `Permill`, `u32`)
- **interface**: `api.events.nft.MarketplaceRegister.is`
- **summary**:    An account has been registered as a marketplace 
 
### MaxIssuanceSet(`u32`, `u32`)
- **interface**: `api.events.nft.MaxIssuanceSet.is`
- **summary**:    Max issuance was set 
 
### Mint(`u32`, `u32`, `u32`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.nft.Mint.is`
- **summary**:    Token(s) were minted 
 
### Offer(`u64`, `u128`, `u32`, `Option<u32>`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.nft.Offer.is`
- **summary**:    An offer has been made on an NFT 
 
### OfferAccept(`u64`, `(u32,u32)`, `u128`, `u32`)
- **interface**: `api.events.nft.OfferAccept.is`
- **summary**:    An offer has been accepted 
 
### OfferCancel(`u64`, `(u32,u32)`)
- **interface**: `api.events.nft.OfferCancel.is`
- **summary**:    An offer has been cancelled 
 
### OwnerSet(`u32`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.nft.OwnerSet.is`
- **summary**:    A new owner was set 
 
### Transfer(`SeedPrimitivesSignatureAccountId20`, `u32`, `Vec<u32>`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.nft.Transfer.is`
- **summary**:    A token was transferred 

___


## nftPeg
 
### ContractAddressSet(`H160`)
- **interface**: `api.events.nftPeg.ContractAddressSet.is`
- **summary**:    The NFT-peg contract address was set 
 
### Erc721Deposit(`SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.nftPeg.Erc721Deposit.is`
- **summary**:    An ERC721 deposit was made 
 
### Erc721Mint(`u32`, `Vec<u32>`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.nftPeg.Erc721Mint.is`
- **summary**:    Bridged ERC721 tokens were minted 
 
### Erc721Withdraw(`SeedPrimitivesSignatureAccountId20`, `Vec<u32>`, `Vec<Vec<u32>>`, `H160`)
- **interface**: `api.events.nftPeg.Erc721Withdraw.is`
- **summary**:    An ERC721 withdraw was made 

___


## offences
 
### Offence(`[u8;16]`, `Bytes`)
- **interface**: `api.events.offences.Offence.is`
- **summary**:    There is an offence reported of the given `kind` happened at the `session_index` and  (kind-specific) time slot. This event is not deposited for duplicate slashes.  \[kind, timeslot\]. 

___


## proxy
 
### Announced(`SeedPrimitivesSignatureAccountId20`, `SeedPrimitivesSignatureAccountId20`, `H256`)
- **interface**: `api.events.proxy.Announced.is`
- **summary**:    An announcement was placed to make a call in the future. 
 
### AnonymousCreated(`SeedPrimitivesSignatureAccountId20`, `SeedPrimitivesSignatureAccountId20`, `SeedRuntimeImplsProxyType`, `u16`)
- **interface**: `api.events.proxy.AnonymousCreated.is`
- **summary**:    Anonymous account has been created by new proxy with given  disambiguation index and proxy type. 
 
### ProxyAdded(`SeedPrimitivesSignatureAccountId20`, `SeedPrimitivesSignatureAccountId20`, `SeedRuntimeImplsProxyType`, `u32`)
- **interface**: `api.events.proxy.ProxyAdded.is`
- **summary**:    A proxy was added. 
 
### ProxyExecuted(`Result<Null, SpRuntimeDispatchError>`)
- **interface**: `api.events.proxy.ProxyExecuted.is`
- **summary**:    A proxy was executed correctly, with the given. 
 
### ProxyRemoved(`SeedPrimitivesSignatureAccountId20`, `SeedPrimitivesSignatureAccountId20`, `SeedRuntimeImplsProxyType`, `u32`)
- **interface**: `api.events.proxy.ProxyRemoved.is`
- **summary**:    A proxy was removed. 

___


## recovery
 
### AccountRecovered(`SeedPrimitivesSignatureAccountId20`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.recovery.AccountRecovered.is`
- **summary**:    Lost account has been successfully recovered by rescuer account. 
 
### RecoveryClosed(`SeedPrimitivesSignatureAccountId20`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.recovery.RecoveryClosed.is`
- **summary**:    A recovery process for lost account by rescuer account has been closed. 
 
### RecoveryCreated(`SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.recovery.RecoveryCreated.is`
- **summary**:    A recovery process has been set up for an account. 
 
### RecoveryInitiated(`SeedPrimitivesSignatureAccountId20`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.recovery.RecoveryInitiated.is`
- **summary**:    A recovery process has been initiated for lost account by rescuer account. 
 
### RecoveryRemoved(`SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.recovery.RecoveryRemoved.is`
- **summary**:    A recovery process has been removed for an account. 
 
### RecoveryVouched(`SeedPrimitivesSignatureAccountId20`, `SeedPrimitivesSignatureAccountId20`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.recovery.RecoveryVouched.is`
- **summary**:    A recovery process for lost account by rescuer account has been vouched for by sender. 

___


## scheduler
 
### CallLookupFailed(`(u32,u32)`, `Option<Bytes>`, `FrameSupportScheduleLookupError`)
- **interface**: `api.events.scheduler.CallLookupFailed.is`
- **summary**:    The call for the provided hash was not found so the task has been aborted. 
 
### Canceled(`u32`, `u32`)
- **interface**: `api.events.scheduler.Canceled.is`
- **summary**:    Canceled some task. 
 
### Dispatched(`(u32,u32)`, `Option<Bytes>`, `Result<Null, SpRuntimeDispatchError>`)
- **interface**: `api.events.scheduler.Dispatched.is`
- **summary**:    Dispatched some task. 
 
### Scheduled(`u32`, `u32`)
- **interface**: `api.events.scheduler.Scheduled.is`
- **summary**:    Scheduled some task. 

___


## session
 
### NewSession(`u32`)
- **interface**: `api.events.session.NewSession.is`
- **summary**:    New session has happened. Note that the argument is the session index, not the  block number as the type might suggest. 

___


## sft
 
### BaseUriSet(`u32`, `Bytes`)
- **interface**: `api.events.sft.BaseUriSet.is`
- **summary**:    Base URI was set 
 
### Burn(`u32`, `Vec<u32>`, `Vec<u128>`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.sft.Burn.is`
- **summary**:    A token was burned 
 
### CollectionCreate(`u32`, `SeedPrimitivesSignatureAccountId20`, `Bytes`, `Bytes`, `Option<SeedPrimitivesNftRoyaltiesSchedule>`, `SeedPrimitivesNftOriginChain`)
- **interface**: `api.events.sft.CollectionCreate.is`
- **summary**:    A new collection of tokens was created 
 
### MaxIssuanceSet(`(u32,u32)`, `u128`)
- **interface**: `api.events.sft.MaxIssuanceSet.is`
- **summary**:    Max issuance was set 
 
### Mint(`u32`, `Vec<u32>`, `Vec<u128>`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.sft.Mint.is`
- **summary**:    Token(s) were minted 
 
### OwnerSet(`u32`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.sft.OwnerSet.is`
- **summary**:    A new owner was set 
 
### TokenCreate(`(u32,u32)`, `u128`, `Option<u128>`, `Bytes`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.sft.TokenCreate.is`
- **summary**:    A new token was created within a collection 
 
### Transfer(`SeedPrimitivesSignatureAccountId20`, `u32`, `Vec<u32>`, `Vec<u128>`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.sft.Transfer.is`
- **summary**:    A token was transferred 

___


## staking
 
### Bonded(`SeedPrimitivesSignatureAccountId20`, `u128`)
- **interface**: `api.events.staking.Bonded.is`
- **summary**:    An account has bonded this amount. \[stash, amount\] 

   NOTE: This event is only emitted when funds are bonded via a dispatchable. Notably,  it will not be emitted for staking rewards when they are added to stake. 
 
### Chilled(`SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.staking.Chilled.is`
- **summary**:    An account has stopped participating as either a validator or nominator.  \[stash\] 
 
### EraPaid(`u32`, `u128`, `u128`)
- **interface**: `api.events.staking.EraPaid.is`
- **summary**:    The era payout has been set; the first balance is the validator-payout; the second is  the remainder from the maximum amount of reward.  \[era_index, validator_payout, remainder\] 
 
### Kicked(`SeedPrimitivesSignatureAccountId20`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.staking.Kicked.is`
- **summary**:    A nominator has been kicked from a validator. \[nominator, stash\] 
 
### OldSlashingReportDiscarded(`u32`)
- **interface**: `api.events.staking.OldSlashingReportDiscarded.is`
- **summary**:    An old slashing report from a prior era was discarded because it could  not be processed. \[session_index\] 
 
### PayoutStarted(`u32`, `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.staking.PayoutStarted.is`
- **summary**:    The stakers' rewards are getting paid. \[era_index, validator_stash\] 
 
### Rewarded(`SeedPrimitivesSignatureAccountId20`, `u128`)
- **interface**: `api.events.staking.Rewarded.is`
- **summary**:    The nominator has been rewarded by this amount. \[stash, amount\] 
 
### Slashed(`SeedPrimitivesSignatureAccountId20`, `u128`)
- **interface**: `api.events.staking.Slashed.is`
- **summary**:    One validator (and its nominators) has been slashed by the given amount.  \[validator, amount\] 
 
### StakersElected()
- **interface**: `api.events.staking.StakersElected.is`
- **summary**:    A new set of stakers was elected. 
 
### StakingElectionFailed()
- **interface**: `api.events.staking.StakingElectionFailed.is`
- **summary**:    The election failed. No new era is planned. 
 
### Unbonded(`SeedPrimitivesSignatureAccountId20`, `u128`)
- **interface**: `api.events.staking.Unbonded.is`
- **summary**:    An account has unbonded this amount. \[stash, amount\] 
 
### ValidatorPrefsSet(`SeedPrimitivesSignatureAccountId20`, `PalletStakingValidatorPrefs`)
- **interface**: `api.events.staking.ValidatorPrefsSet.is`
- **summary**:    A validator has set their preferences. 
 
### Withdrawn(`SeedPrimitivesSignatureAccountId20`, `u128`)
- **interface**: `api.events.staking.Withdrawn.is`
- **summary**:    An account has called `withdraw_unbonded` and removed unbonding chunks worth `Balance`  from the unlocking queue. \[stash, amount\] 

___


## sudo
 
### KeyChanged(`Option<SeedPrimitivesSignatureAccountId20>`)
- **interface**: `api.events.sudo.KeyChanged.is`
- **summary**:    The \[sudoer\] just switched identity; the old key is supplied if one existed. 
 
### Sudid(`Result<Null, SpRuntimeDispatchError>`)
- **interface**: `api.events.sudo.Sudid.is`
- **summary**:    A sudo just took place. \[result\] 
 
### SudoAsDone(`Result<Null, SpRuntimeDispatchError>`)
- **interface**: `api.events.sudo.SudoAsDone.is`
- **summary**:    A sudo just took place. \[result\] 

___


## system
 
### CodeUpdated()
- **interface**: `api.events.system.CodeUpdated.is`
- **summary**:    `:code` was updated. 
 
### ExtrinsicFailed(`SpRuntimeDispatchError`, `FrameSupportWeightsDispatchInfo`)
- **interface**: `api.events.system.ExtrinsicFailed.is`
- **summary**:    An extrinsic failed. 
 
### ExtrinsicSuccess(`FrameSupportWeightsDispatchInfo`)
- **interface**: `api.events.system.ExtrinsicSuccess.is`
- **summary**:    An extrinsic completed successfully. 
 
### KilledAccount(`SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.system.KilledAccount.is`
- **summary**:    An account was reaped. 
 
### NewAccount(`SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.system.NewAccount.is`
- **summary**:    A new account was created. 
 
### Remarked(`SeedPrimitivesSignatureAccountId20`, `H256`)
- **interface**: `api.events.system.Remarked.is`
- **summary**:    On on-chain remark happened. 

___


## transactionPayment
 
### TransactionFeePaid(`SeedPrimitivesSignatureAccountId20`, `u128`, `u128`)
- **interface**: `api.events.transactionPayment.TransactionFeePaid.is`
- **summary**:    A transaction fee `actual_fee`, of which `tip` was added to the minimum inclusion fee,  has been paid by `who`. 

___


## utility
 
### BatchCompleted()
- **interface**: `api.events.utility.BatchCompleted.is`
- **summary**:    Batch of dispatches completed fully with no error. 
 
### BatchCompletedWithErrors()
- **interface**: `api.events.utility.BatchCompletedWithErrors.is`
- **summary**:    Batch of dispatches completed but has errors. 
 
### BatchInterrupted(`u32`, `SpRuntimeDispatchError`)
- **interface**: `api.events.utility.BatchInterrupted.is`
- **summary**:    Batch of dispatches did not complete fully. Index of first failing dispatch given, as  well as the error. 
 
### DispatchedAs(`Result<Null, SpRuntimeDispatchError>`)
- **interface**: `api.events.utility.DispatchedAs.is`
- **summary**:    A call was dispatched. 
 
### ItemCompleted()
- **interface**: `api.events.utility.ItemCompleted.is`
- **summary**:    A single item within a Batch of dispatches has completed with no error. 
 
### ItemFailed(`SpRuntimeDispatchError`)
- **interface**: `api.events.utility.ItemFailed.is`
- **summary**:    A single item within a Batch of dispatches has completed with error. 

___


## voterList
 
### Rebagged(`SeedPrimitivesSignatureAccountId20`, `u64`, `u64`)
- **interface**: `api.events.voterList.Rebagged.is`
- **summary**:    Moved an account from one bag to another. 
 
### ScoreUpdated(`SeedPrimitivesSignatureAccountId20`, `u64`)
- **interface**: `api.events.voterList.ScoreUpdated.is`
- **summary**:    Updated the score of some account to the given amount. 

___


## xls20
 
### RelayerSet(`SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.xls20.RelayerSet.is`
- **summary**:    A new relayer has been set 
 
### Xls20CompatibilityEnabled(`u32`)
- **interface**: `api.events.xls20.Xls20CompatibilityEnabled.is`
- **summary**:    A collection has had XLS-20 compatibility enabled 
 
### Xls20MappingSet(`u32`, `Vec<(u32,[u8;64])>`)
- **interface**: `api.events.xls20.Xls20MappingSet.is`
- **summary**:    A new XLS20 mapping has been set 
 
### Xls20MintFeePaid(`SeedPrimitivesSignatureAccountId20`, `u128`)
- **interface**: `api.events.xls20.Xls20MintFeePaid.is`
- **summary**:    Additional mint fee for XLS-20 mint has been paid to relayer 
 
### Xls20MintFeeSet(`u128`)
- **interface**: `api.events.xls20.Xls20MintFeeSet.is`
- **summary**:    A new Xls20 Mint Fee has been set 
 
### Xls20MintRequest(`u32`, `Vec<u32>`, `Vec<Bytes>`)
- **interface**: `api.events.xls20.Xls20MintRequest.is`
- **summary**:    Request sent to XLS20 Relayer 

___


## xrplBridge
 
### DoorAddressSet(`H160`)
- **interface**: `api.events.xrplBridge.DoorAddressSet.is`
 
### DoorNextTicketSequenceParamSet(`u32`, `u32`)
- **interface**: `api.events.xrplBridge.DoorNextTicketSequenceParamSet.is`
 
### DoorTicketSequenceParamSet(`u32`, `u32`, `u32`)
- **interface**: `api.events.xrplBridge.DoorTicketSequenceParamSet.is`
 
### NotSupportedTransaction()
- **interface**: `api.events.xrplBridge.NotSupportedTransaction.is`
- **summary**:    Transaction not supported 
 
### ProcessingFailed(`u64`, `H512`, `SpRuntimeDispatchError`)
- **interface**: `api.events.xrplBridge.ProcessingFailed.is`
- **summary**:    Processing an event failed 
 
### ProcessingOk(`u64`, `H512`)
- **interface**: `api.events.xrplBridge.ProcessingOk.is`
- **summary**:    Processing an event succeeded 
 
### RelayerAdded(`SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.xrplBridge.RelayerAdded.is`
 
### RelayerRemoved(`SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.events.xrplBridge.RelayerRemoved.is`
 
### TicketSequenceThresholdReached(`u32`)
- **interface**: `api.events.xrplBridge.TicketSequenceThresholdReached.is`
 
### TransactionAdded(`u64`, `H512`)
- **interface**: `api.events.xrplBridge.TransactionAdded.is`
 
### TransactionChallenge(`u64`, `H512`)
- **interface**: `api.events.xrplBridge.TransactionChallenge.is`
 
### WithdrawRequest(`u64`, `SeedPrimitivesSignatureAccountId20`, `u128`, `H160`)
- **interface**: `api.events.xrplBridge.WithdrawRequest.is`
- **summary**:    Request to withdraw some XRP amount to XRPL 
