---
title: Errors
---

This page lists the errors that can be encountered in the different modules. 

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

- **[feeProxy](#feeproxy)**

- **[futurepass](#futurepass)**

- **[grandpa](#grandpa)**

- **[imOnline](#imonline)**

- **[nft](#nft)**

- **[nftPeg](#nftpeg)**

- **[proxy](#proxy)**

- **[recovery](#recovery)**

- **[scheduler](#scheduler)**

- **[session](#session)**

- **[sft](#sft)**

- **[staking](#staking)**

- **[sudo](#sudo)**

- **[system](#system)**

- **[tokenApprovals](#tokenapprovals)**

- **[utility](#utility)**

- **[voterList](#voterlist)**

- **[xls20](#xls20)**

- **[xRPLBridge](#xrplbridge)**


___


## assets
 
### AlreadyExists
- **interface**: `api.errors.assets.AlreadyExists.is`
- **summary**:    The asset-account already exists. 
 
### BadMetadata
- **interface**: `api.errors.assets.BadMetadata.is`
- **summary**:    Invalid metadata given. 
 
### BadWitness
- **interface**: `api.errors.assets.BadWitness.is`
- **summary**:    Invalid witness data given. 
 
### BalanceLow
- **interface**: `api.errors.assets.BalanceLow.is`
- **summary**:    Account balance must be greater than or equal to the transfer amount. 
 
### Frozen
- **interface**: `api.errors.assets.Frozen.is`
- **summary**:    The origin account is frozen. 
 
### InUse
- **interface**: `api.errors.assets.InUse.is`
- **summary**:    The asset ID is already taken. 
 
### MinBalanceZero
- **interface**: `api.errors.assets.MinBalanceZero.is`
- **summary**:    Minimum balance should be non-zero. 
 
### NoAccount
- **interface**: `api.errors.assets.NoAccount.is`
- **summary**:    The account to alter does not exist. 
 
### NoDeposit
- **interface**: `api.errors.assets.NoDeposit.is`
- **summary**:    The asset-account doesn't have an associated deposit. 
 
### NoPermission
- **interface**: `api.errors.assets.NoPermission.is`
- **summary**:    The signing account has no permission to do the operation. 
 
### NoProvider
- **interface**: `api.errors.assets.NoProvider.is`
- **summary**:    Unable to increment the consumer reference counters on the account. Either no provider  reference exists to allow a non-zero balance of a non-self-sufficient asset, or the  maximum number of consumers has been reached. 
 
### Unapproved
- **interface**: `api.errors.assets.Unapproved.is`
- **summary**:    No approval exists that would allow the transfer. 
 
### Unknown
- **interface**: `api.errors.assets.Unknown.is`
- **summary**:    The given asset ID is unknown. 
 
### WouldBurn
- **interface**: `api.errors.assets.WouldBurn.is`
- **summary**:    The operation would result in funds being burned. 
 
### WouldDie
- **interface**: `api.errors.assets.WouldDie.is`
- **summary**:    The source account would not survive the transfer and it needs to stay alive. 

___


## assetsExt
 
### BalanceLow
- **interface**: `api.errors.assetsExt.BalanceLow.is`
- **summary**:    Hold balance is less then the required amount 
 
### CreateAssetFailed
- **interface**: `api.errors.assetsExt.CreateAssetFailed.is`
- **summary**:    Failed to create a new asset 
 
### MaxHolds
- **interface**: `api.errors.assetsExt.MaxHolds.is`
- **summary**:    Maximum holds placed on this asset/account pair 
 
### NoAccount
- **interface**: `api.errors.assetsExt.NoAccount.is`
- **summary**:    The account to alter does not exist 
 
### NoAvailableIds
- **interface**: `api.errors.assetsExt.NoAvailableIds.is`
- **summary**:    No more Ids are available, they've been exhausted 
 
### Overflow
- **interface**: `api.errors.assetsExt.Overflow.is`
- **summary**:    Operation would overflow 

___


## authorship
 
### GenesisUncle
- **interface**: `api.errors.authorship.GenesisUncle.is`
- **summary**:    The uncle is genesis. 
 
### InvalidUncleParent
- **interface**: `api.errors.authorship.InvalidUncleParent.is`
- **summary**:    The uncle parent not in the chain. 
 
### OldUncle
- **interface**: `api.errors.authorship.OldUncle.is`
- **summary**:    The uncle isn't recent enough to be included. 
 
### TooHighUncle
- **interface**: `api.errors.authorship.TooHighUncle.is`
- **summary**:    The uncle is too high in chain. 
 
### TooManyUncles
- **interface**: `api.errors.authorship.TooManyUncles.is`
- **summary**:    Too many uncles. 
 
### UncleAlreadyIncluded
- **interface**: `api.errors.authorship.UncleAlreadyIncluded.is`
- **summary**:    The uncle is already included. 
 
### UnclesAlreadySet
- **interface**: `api.errors.authorship.UnclesAlreadySet.is`
- **summary**:    Uncles already set in the block. 

___


## babe
 
### DuplicateOffenceReport
- **interface**: `api.errors.babe.DuplicateOffenceReport.is`
- **summary**:    A given equivocation report is valid but already previously reported. 
 
### InvalidConfiguration
- **interface**: `api.errors.babe.InvalidConfiguration.is`
- **summary**:    Submitted configuration is invalid. 
 
### InvalidEquivocationProof
- **interface**: `api.errors.babe.InvalidEquivocationProof.is`
- **summary**:    An equivocation proof provided as part of an equivocation report is invalid. 
 
### InvalidKeyOwnershipProof
- **interface**: `api.errors.babe.InvalidKeyOwnershipProof.is`
- **summary**:    A key ownership proof provided as part of an equivocation report is invalid. 

___


## balances
 
### DeadAccount
- **interface**: `api.errors.balances.DeadAccount.is`
- **summary**:    Beneficiary account must pre-exist 
 
### ExistentialDeposit
- **interface**: `api.errors.balances.ExistentialDeposit.is`
- **summary**:    Value too low to create account due to existential deposit 
 
### ExistingVestingSchedule
- **interface**: `api.errors.balances.ExistingVestingSchedule.is`
- **summary**:    A vesting schedule already exists for this account 
 
### InsufficientBalance
- **interface**: `api.errors.balances.InsufficientBalance.is`
- **summary**:    Balance too low to send value 
 
### KeepAlive
- **interface**: `api.errors.balances.KeepAlive.is`
- **summary**:    Transfer/payment would kill account 
 
### LiquidityRestrictions
- **interface**: `api.errors.balances.LiquidityRestrictions.is`
- **summary**:    Account liquidity restrictions prevent withdrawal 
 
### TooManyReserves
- **interface**: `api.errors.balances.TooManyReserves.is`
- **summary**:    Number of named reserves exceed MaxReserves 
 
### VestingBalance
- **interface**: `api.errors.balances.VestingBalance.is`
- **summary**:    Vesting balance too high to send value 

___


## dex
 
### ExcessiveSupplyAmount
- **interface**: `api.errors.dex.ExcessiveSupplyAmount.is`
- **summary**:    Supply amount is more than max_supply_amount 
 
### ExpiredDeadline
- **interface**: `api.errors.dex.ExpiredDeadline.is`
- **summary**:    The deadline has been missed 
 
### IdenticalTokenAddress
- **interface**: `api.errors.dex.IdenticalTokenAddress.is`
 
### InsufficientAmount
- **interface**: `api.errors.dex.InsufficientAmount.is`
- **summary**:    Insufficent amount 
 
### InsufficientAmountA
- **interface**: `api.errors.dex.InsufficientAmountA.is`
- **summary**:    Insufficient asset_a liquidity amount 
 
### InsufficientAmountB
- **interface**: `api.errors.dex.InsufficientAmountB.is`
- **summary**:    Insufficient asset_b liquidity amount 
 
### InsufficientInputAmount
- **interface**: `api.errors.dex.InsufficientInputAmount.is`
- **summary**:    Insufficient input amount 
 
### InsufficientLiquidity
- **interface**: `api.errors.dex.InsufficientLiquidity.is`
- **summary**:    Liquidity is not enough 
 
### InsufficientLiquidityBurnt
- **interface**: `api.errors.dex.InsufficientLiquidityBurnt.is`
- **summary**:    Insufficient liquidity burnt 
 
### InsufficientOutputAmount
- **interface**: `api.errors.dex.InsufficientOutputAmount.is`
- **summary**:    Insufficient output amount 
 
### InsufficientTargetAmount
- **interface**: `api.errors.dex.InsufficientTargetAmount.is`
- **summary**:    Target amount is less to min_target_amount 
 
### InsufficientWithdrawnAmountA
- **interface**: `api.errors.dex.InsufficientWithdrawnAmountA.is`
- **summary**:    Insufficient withdraw amount for token A 
 
### InsufficientWithdrawnAmountB
- **interface**: `api.errors.dex.InsufficientWithdrawnAmountB.is`
- **summary**:    Insufficient withdraw amount for token B 
 
### InvalidAssetId
- **interface**: `api.errors.dex.InvalidAssetId.is`
- **summary**:    Invalid Asset id 
 
### InvalidConstantProduct
- **interface**: `api.errors.dex.InvalidConstantProduct.is`
- **summary**:    Invalid constant product K 
 
### InvalidInputAmounts
- **interface**: `api.errors.dex.InvalidInputAmounts.is`
- **summary**:    Must provide non-zero amount of liquidity 
 
### InvalidLiquidityIncrement
- **interface**: `api.errors.dex.InvalidLiquidityIncrement.is`
- **summary**:    The increment of liquidity is invalid 
 
### InvalidTradingPathLength
- **interface**: `api.errors.dex.InvalidTradingPathLength.is`
- **summary**:    Invalid trading path length 
 
### LiquidityProviderTokenNotCreated
- **interface**: `api.errors.dex.LiquidityProviderTokenNotCreated.is`
- **summary**:    The Liquidity Provider token does not exist 
 
### MustBeEnabled
- **interface**: `api.errors.dex.MustBeEnabled.is`
- **summary**:    Trading pair must be in Enabled status 
 
### MustBeNotEnabled
- **interface**: `api.errors.dex.MustBeNotEnabled.is`
- **summary**:    Trading pair must be in NotEnabled status 
 
### ZeroSupplyAmount
- **interface**: `api.errors.dex.ZeroSupplyAmount.is`
- **summary**:    The supply amount is zero 
 
### ZeroTargetAmount
- **interface**: `api.errors.dex.ZeroTargetAmount.is`
- **summary**:    The target amount is zero 

___


## echo
 
### InvalidAbiEncoding
- **interface**: `api.errors.echo.InvalidAbiEncoding.is`
- **summary**:    The abi received does not match the encoding scheme 
 
### InvalidParameter
- **interface**: `api.errors.echo.InvalidParameter.is`
- **summary**:    Invalid ping_or_pong parameter, must be 0 or 1 
 
### NoAvailableIds
- **interface**: `api.errors.echo.NoAvailableIds.is`
- **summary**:    There are no remaining session ids 

___


## electionProviderMultiPhase
 
### CallNotAllowed
- **interface**: `api.errors.electionProviderMultiPhase.CallNotAllowed.is`
- **summary**:    The call is not allowed at this point. 
 
### FallbackFailed
- **interface**: `api.errors.electionProviderMultiPhase.FallbackFailed.is`
- **summary**:    The fallback failed 
 
### InvalidSubmissionIndex
- **interface**: `api.errors.electionProviderMultiPhase.InvalidSubmissionIndex.is`
- **summary**:    `Self::insert_submission` returned an invalid index. 
 
### MissingSnapshotMetadata
- **interface**: `api.errors.electionProviderMultiPhase.MissingSnapshotMetadata.is`
- **summary**:    Snapshot metadata should exist but didn't. 
 
### OcwCallWrongEra
- **interface**: `api.errors.electionProviderMultiPhase.OcwCallWrongEra.is`
- **summary**:    OCW submitted solution for wrong round 
 
### PreDispatchEarlySubmission
- **interface**: `api.errors.electionProviderMultiPhase.PreDispatchEarlySubmission.is`
- **summary**:    Submission was too early. 
 
### PreDispatchWeakSubmission
- **interface**: `api.errors.electionProviderMultiPhase.PreDispatchWeakSubmission.is`
- **summary**:    Submission was too weak, score-wise. 
 
### PreDispatchWrongWinnerCount
- **interface**: `api.errors.electionProviderMultiPhase.PreDispatchWrongWinnerCount.is`
- **summary**:    Wrong number of winners presented. 
 
### SignedCannotPayDeposit
- **interface**: `api.errors.electionProviderMultiPhase.SignedCannotPayDeposit.is`
- **summary**:    The origin failed to pay the deposit. 
 
### SignedInvalidWitness
- **interface**: `api.errors.electionProviderMultiPhase.SignedInvalidWitness.is`
- **summary**:    Witness data to dispatchable is invalid. 
 
### SignedQueueFull
- **interface**: `api.errors.electionProviderMultiPhase.SignedQueueFull.is`
- **summary**:    The queue was full, and the solution was not better than any of the existing ones. 
 
### SignedTooMuchWeight
- **interface**: `api.errors.electionProviderMultiPhase.SignedTooMuchWeight.is`
- **summary**:    The signed submission consumes too much weight 

___


## erc20Peg
 
### CreateAssetFailed
- **interface**: `api.errors.erc20Peg.CreateAssetFailed.is`
- **summary**:    Could not create the bridged asset 
 
### DepositsPaused
- **interface**: `api.errors.erc20Peg.DepositsPaused.is`
- **summary**:    Deposits are inactive 
 
### EvmWithdrawalFailed
- **interface**: `api.errors.erc20Peg.EvmWithdrawalFailed.is`
- **summary**:    Withdrawals over the set payment delay for EVM calls are disabled 
 
### InvalidAbiEncoding
- **interface**: `api.errors.erc20Peg.InvalidAbiEncoding.is`
- **summary**:    The abi received does not match the encoding scheme 
 
### InvalidAmount
- **interface**: `api.errors.erc20Peg.InvalidAmount.is`
- **summary**:    Deposit has bad amount 
 
### InvalidPalletId
- **interface**: `api.errors.erc20Peg.InvalidPalletId.is`
- **summary**:    Could not convert pallet id to account 
 
### UnsupportedAsset
- **interface**: `api.errors.erc20Peg.UnsupportedAsset.is`
- **summary**:    Withdrawals of this asset are not supported 
 
### WithdrawalsPaused
- **interface**: `api.errors.erc20Peg.WithdrawalsPaused.is`
- **summary**:    Withdrawals are inactive 

___


## ethBridge
 
### BridgePaused
- **interface**: `api.errors.ethBridge.BridgePaused.is`
- **summary**:    The bridge is paused pending validator set changes (once every era / 24 hours)  It will reactive after ~10 minutes 
 
### CantBondRelayer
- **interface**: `api.errors.ethBridge.CantBondRelayer.is`
- **summary**:    The relayer already has a bonded amount 
 
### CantUnbondRelayer
- **interface**: `api.errors.ethBridge.CantUnbondRelayer.is`
- **summary**:    The relayer is active and cant unbond the specified amount 
 
### ClaimAlreadyChallenged
- **interface**: `api.errors.ethBridge.ClaimAlreadyChallenged.is`
- **summary**:    There is already a challenge for this claim 
 
### EventReplayPending
- **interface**: `api.errors.ethBridge.EventReplayPending.is`
- **summary**:    Event was already submitted and is pending 
 
### EventReplayProcessed
- **interface**: `api.errors.ethBridge.EventReplayProcessed.is`
- **summary**:    Event was already submitted and is complete 
 
### HttpFetch
- **interface**: `api.errors.ethBridge.HttpFetch.is`
 
### Internal
- **interface**: `api.errors.ethBridge.Internal.is`
- **summary**:    Some internal operation failed 
 
### InvalidClaim
- **interface**: `api.errors.ethBridge.InvalidClaim.is`
- **summary**:    Claim was invalid e.g. not properly ABI encoded 
 
### InvalidNotarization
- **interface**: `api.errors.ethBridge.InvalidNotarization.is`
- **summary**:    A notarization was invalid 
 
### MaxNewSignersExceeded
- **interface**: `api.errors.ethBridge.MaxNewSignersExceeded.is`
- **summary**:    Someone tried to set a greater amount of validators than allowed 
 
### NoBondPaid
- **interface**: `api.errors.ethBridge.NoBondPaid.is`
- **summary**:    The relayer hasn't paid the relayer bond so can't be set as the active relayer 
 
### NoClaim
- **interface**: `api.errors.ethBridge.NoClaim.is`
- **summary**:    There is no event claim associated with the supplied claim_id 
 
### NoLocalSigningAccount
- **interface**: `api.errors.ethBridge.NoLocalSigningAccount.is`
 
### NoPermission
- **interface**: `api.errors.ethBridge.NoPermission.is`
- **summary**:    Caller does not have permission for that action 
 
### OcwConfig
- **interface**: `api.errors.ethBridge.OcwConfig.is`
- **summary**:    offchain worker not configured properly 
 
### OffchainUnsignedTxSignedPayload
- **interface**: `api.errors.ethBridge.OffchainUnsignedTxSignedPayload.is`

___


## ethereum
 
### BalanceLow
- **interface**: `api.errors.ethereum.BalanceLow.is`
 
### GasLimitTooHigh
- **interface**: `api.errors.ethereum.GasLimitTooHigh.is`
 
### GasLimitTooLow
- **interface**: `api.errors.ethereum.GasLimitTooLow.is`
 
### GasPriceTooLow
- **interface**: `api.errors.ethereum.GasPriceTooLow.is`
 
### InvalidNonce
- **interface**: `api.errors.ethereum.InvalidNonce.is`
 
### InvalidSignature
- **interface**: `api.errors.ethereum.InvalidSignature.is`
- **summary**:    Signature is invalid. 
 
### PreLogExists
- **interface**: `api.errors.ethereum.PreLogExists.is`
- **summary**:    Pre-log is present, therefore transact is not allowed. 
 
### Undefined
- **interface**: `api.errors.ethereum.Undefined.is`

___


## eVM
 
### BalanceLow
- **interface**: `api.errors.evm.BalanceLow.is`
- **summary**:    Not enough balance to perform action 
 
### FeeOverflow
- **interface**: `api.errors.evm.FeeOverflow.is`
- **summary**:    Calculating total fee overflowed 
 
### GasLimitTooHigh
- **interface**: `api.errors.evm.GasLimitTooHigh.is`
- **summary**:    Gas limit is too high. 
 
### GasLimitTooLow
- **interface**: `api.errors.evm.GasLimitTooLow.is`
- **summary**:    Gas limit is too low. 
 
### GasPriceTooLow
- **interface**: `api.errors.evm.GasPriceTooLow.is`
- **summary**:    Gas price is too low. 
 
### InvalidNonce
- **interface**: `api.errors.evm.InvalidNonce.is`
- **summary**:    Nonce is invalid 
 
### PaymentOverflow
- **interface**: `api.errors.evm.PaymentOverflow.is`
- **summary**:    Calculating total payment overflowed 
 
### Undefined
- **interface**: `api.errors.evm.Undefined.is`
- **summary**:    Undefined error. 
 
### WithdrawFailed
- **interface**: `api.errors.evm.WithdrawFailed.is`
- **summary**:    Withdraw fee failed 

___


## feeProxy
 
### FeeTokenIsGasToken
- **interface**: `api.errors.feeProxy.FeeTokenIsGasToken.is`
- **summary**:    The selected fee token is equal to the native gas token 
 
### NestedFeePreferenceCall
- **interface**: `api.errors.feeProxy.NestedFeePreferenceCall.is`
- **summary**:    The inner call is a fee preference call 

___


## futurepass
 
### AccountAlreadyRegistered
- **interface**: `api.errors.futurepass.AccountAlreadyRegistered.is`
- **summary**:    Account is already futurepass holder 
 
### AccountParsingFailure
- **interface**: `api.errors.futurepass.AccountParsingFailure.is`
- **summary**:    AccountParsingFailure 
 
### DelegateAlreadyExists
- **interface**: `api.errors.futurepass.DelegateAlreadyExists.is`
- **summary**:    Account already exists as a delegate 
 
### DelegateNotRegistered
- **interface**: `api.errors.futurepass.DelegateNotRegistered.is`
- **summary**:    Account is not futurepass delegate 
 
### ExpiredDeadline
- **interface**: `api.errors.futurepass.ExpiredDeadline.is`
- **summary**:    ExpiredDeadline 
 
### InvalidDeadline
- **interface**: `api.errors.futurepass.InvalidDeadline.is`
- **summary**:    Invalid deadline 
 
### InvalidProxyType
- **interface**: `api.errors.futurepass.InvalidProxyType.is`
- **summary**:    Invalid proxy type 
 
### InvalidSignature
- **interface**: `api.errors.futurepass.InvalidSignature.is`
- **summary**:    Invalid signature 
 
### MigratorNotSet
- **interface**: `api.errors.futurepass.MigratorNotSet.is`
- **summary**:    Futurepass migrator admin account is not set 
 
### NotFuturepassOwner
- **interface**: `api.errors.futurepass.NotFuturepassOwner.is`
- **summary**:    Account is not futurepass owner 
 
### OwnerCannotUnregister
- **interface**: `api.errors.futurepass.OwnerCannotUnregister.is`
- **summary**:    Futurepass owner cannot remove themselves 
 
### PermissionDenied
- **interface**: `api.errors.futurepass.PermissionDenied.is`
- **summary**:    Account does not have permission to call this function 
 
### RegisterDelegateSignerMismatch
- **interface**: `api.errors.futurepass.RegisterDelegateSignerMismatch.is`
- **summary**:    RegisterDelegateSignerMismatch 

___


## grandpa
 
### ChangePending
- **interface**: `api.errors.grandpa.ChangePending.is`
- **summary**:    Attempt to signal GRANDPA change with one already pending. 
 
### DuplicateOffenceReport
- **interface**: `api.errors.grandpa.DuplicateOffenceReport.is`
- **summary**:    A given equivocation report is valid but already previously reported. 
 
### InvalidEquivocationProof
- **interface**: `api.errors.grandpa.InvalidEquivocationProof.is`
- **summary**:    An equivocation proof provided as part of an equivocation report is invalid. 
 
### InvalidKeyOwnershipProof
- **interface**: `api.errors.grandpa.InvalidKeyOwnershipProof.is`
- **summary**:    A key ownership proof provided as part of an equivocation report is invalid. 
 
### PauseFailed
- **interface**: `api.errors.grandpa.PauseFailed.is`
- **summary**:    Attempt to signal GRANDPA pause when the authority set isn't live  (either paused or already pending pause). 
 
### ResumeFailed
- **interface**: `api.errors.grandpa.ResumeFailed.is`
- **summary**:    Attempt to signal GRANDPA resume when the authority set isn't paused  (either live or already pending resume). 
 
### TooSoon
- **interface**: `api.errors.grandpa.TooSoon.is`
- **summary**:    Cannot signal forced change so soon after last. 

___


## imOnline
 
### DuplicatedHeartbeat
- **interface**: `api.errors.imOnline.DuplicatedHeartbeat.is`
- **summary**:    Duplicated heartbeat. 
 
### InvalidKey
- **interface**: `api.errors.imOnline.InvalidKey.is`
- **summary**:    Non existent public key. 

___


## nft
 
### AttemptedMintOnBridgedToken
- **interface**: `api.errors.nft.AttemptedMintOnBridgedToken.is`
- **summary**:    Attemped to mint a token that was bridged from a different chain 
 
### BidTooLow
- **interface**: `api.errors.nft.BidTooLow.is`
- **summary**:    Auction bid was lower than reserve or current highest bid 
 
### CannotClaimNonClaimableCollections
- **interface**: `api.errors.nft.CannotClaimNonClaimableCollections.is`
- **summary**:    Cannot claim already claimed collections 
 
### CollectionIssuanceNotZero
- **interface**: `api.errors.nft.CollectionIssuanceNotZero.is`
- **summary**:    Total issuance of collection must be zero to add xls20 compatibility 
 
### CollectionNameInvalid
- **interface**: `api.errors.nft.CollectionNameInvalid.is`
- **summary**:    Given collection name is invalid (invalid utf-8, too long, empty) 
 
### InitialIssuanceNotZero
- **interface**: `api.errors.nft.InitialIssuanceNotZero.is`
- **summary**:    Initial issuance on XLS-20 compatible collections must be zero 
 
### InvalidMaxIssuance
- **interface**: `api.errors.nft.InvalidMaxIssuance.is`
- **summary**:    Max issuance needs to be greater than 0 and initial_issuance  Cannot exceed MaxTokensPerCollection 
 
### InvalidMetadataPath
- **interface**: `api.errors.nft.InvalidMetadataPath.is`
- **summary**:    The metadata path is invalid (non-utf8 or empty) 
 
### InvalidNewOwner
- **interface**: `api.errors.nft.InvalidNewOwner.is`
- **summary**:    The caller can not be the new owner 
 
### InvalidOffer
- **interface**: `api.errors.nft.InvalidOffer.is`
- **summary**:    No offer exists for the given OfferId 
 
### IsTokenOwner
- **interface**: `api.errors.nft.IsTokenOwner.is`
- **summary**:    The caller owns the token and can't make an offer 
 
### MarketplaceNotRegistered
- **interface**: `api.errors.nft.MarketplaceNotRegistered.is`
- **summary**:    The account_id hasn't been registered as a marketplace 
 
### MaxIssuanceAlreadySet
- **interface**: `api.errors.nft.MaxIssuanceAlreadySet.is`
- **summary**:    The max issuance has already been set and can't be changed 
 
### MaxIssuanceReached
- **interface**: `api.errors.nft.MaxIssuanceReached.is`
- **summary**:    The collection max issuance has been reached and no more tokens can be minted 
 
### MaxOffersReached
- **interface**: `api.errors.nft.MaxOffersReached.is`
- **summary**:    The maximum number of offers on this token has been reached 
 
### MintLimitExceeded
- **interface**: `api.errors.nft.MintLimitExceeded.is`
- **summary**:    The quantity exceeds the max tokens per mint limit 
 
### MixedBundleSale
- **interface**: `api.errors.nft.MixedBundleSale.is`
- **summary**:    Selling tokens from different collection is not allowed 
 
### NoAvailableIds
- **interface**: `api.errors.nft.NoAvailableIds.is`
- **summary**:    No more Ids are available, they've been exhausted 
 
### NoCollectionFound
- **interface**: `api.errors.nft.NoCollectionFound.is`
- **summary**:    The collection does not exist 
 
### NotBuyer
- **interface**: `api.errors.nft.NotBuyer.is`
- **summary**:    The caller is not the specified buyer 
 
### NotCollectionOwner
- **interface**: `api.errors.nft.NotCollectionOwner.is`
- **summary**:    Origin is not the collection owner and is not permitted to perform the operation 
 
### NotForAuction
- **interface**: `api.errors.nft.NotForAuction.is`
- **summary**:    The token is not listed for auction sale 
 
### NotForFixedPriceSale
- **interface**: `api.errors.nft.NotForFixedPriceSale.is`
- **summary**:    The token is not listed for fixed price sale 
 
### NoToken
- **interface**: `api.errors.nft.NoToken.is`
- **summary**:    The token does not exist 
 
### NotSeller
- **interface**: `api.errors.nft.NotSeller.is`
- **summary**:    The caller is not the seller of the NFT 
 
### NotTokenOwner
- **interface**: `api.errors.nft.NotTokenOwner.is`
- **summary**:    Origin does not own the NFT 
 
### RoyaltiesInvalid
- **interface**: `api.errors.nft.RoyaltiesInvalid.is`
- **summary**:    Total royalties would exceed 100% of sale or an empty vec is supplied 
 
### TokenLimitExceeded
- **interface**: `api.errors.nft.TokenLimitExceeded.is`
- **summary**:    The number of tokens have exceeded the max tokens allowed 
 
### TokenLocked
- **interface**: `api.errors.nft.TokenLocked.is`
- **summary**:    Cannot operate on a listed NFT 
 
### TokenNotListed
- **interface**: `api.errors.nft.TokenNotListed.is`
- **summary**:    The token is not listed for sale 
 
### TokenOnAuction
- **interface**: `api.errors.nft.TokenOnAuction.is`
- **summary**:    Cannot make an offer on a token up for auction 
 
### ZeroOffer
- **interface**: `api.errors.nft.ZeroOffer.is`
- **summary**:    Offer amount needs to be greater than 0 

___


## nftPeg
 
### ExceedsMaxAddresses
- **interface**: `api.errors.nftPeg.ExceedsMaxAddresses.is`
- **summary**:    Send more addresses than are allowed 
 
### ExceedsMaxTokens
- **interface**: `api.errors.nftPeg.ExceedsMaxTokens.is`
- **summary**:    Sent more tokens than are allowed 
 
### ExceedsMaxVecLength
- **interface**: `api.errors.nftPeg.ExceedsMaxVecLength.is`
- **summary**:    The length of the given vec exceeds the maximal allowed length limit 
 
### InvalidAbiEncoding
- **interface**: `api.errors.nftPeg.InvalidAbiEncoding.is`
- **summary**:    The abi data passed in could not be decoded 
 
### InvalidAbiPrefix
- **interface**: `api.errors.nftPeg.InvalidAbiPrefix.is`
- **summary**:    The prefix uint in the abi encoded data was invalid 
 
### NoCollectionFound
- **interface**: `api.errors.nftPeg.NoCollectionFound.is`
- **summary**:    No collection info exists 
 
### NoMappedTokenExists
- **interface**: `api.errors.nftPeg.NoMappedTokenExists.is`
- **summary**:    No mapped token was stored for bridging the token back to the bridged chain  chain(Should not happen) 
 
### NoPermissionToBridge
- **interface**: `api.errors.nftPeg.NoPermissionToBridge.is`
- **summary**:    Tried to bridge a token that originates from Root, which is not yet supported 
 
### StateSyncDisabled
- **interface**: `api.errors.nftPeg.StateSyncDisabled.is`
- **summary**:    The state sync decoding feature is not implemented 
 
### TokenListLengthMismatch
- **interface**: `api.errors.nftPeg.TokenListLengthMismatch.is`
- **summary**:    Multiple tokens were passed from contract, but amounts were unqeual per each array 

___


## proxy
 
### Duplicate
- **interface**: `api.errors.proxy.Duplicate.is`
- **summary**:    Account is already a proxy. 
 
### NoPermission
- **interface**: `api.errors.proxy.NoPermission.is`
- **summary**:    Call may not be made by proxy because it may escalate its privileges. 
 
### NoSelfProxy
- **interface**: `api.errors.proxy.NoSelfProxy.is`
- **summary**:    Cannot add self as proxy. 
 
### NotFound
- **interface**: `api.errors.proxy.NotFound.is`
- **summary**:    Proxy registration not found. 
 
### NotProxy
- **interface**: `api.errors.proxy.NotProxy.is`
- **summary**:    Sender is not a proxy of the account to be proxied. 
 
### TooMany
- **interface**: `api.errors.proxy.TooMany.is`
- **summary**:    There are too many proxies registered or too many announcements pending. 
 
### Unannounced
- **interface**: `api.errors.proxy.Unannounced.is`
- **summary**:    Announcement, if made at all, was made too recently. 
 
### Unproxyable
- **interface**: `api.errors.proxy.Unproxyable.is`
- **summary**:    A call which is incompatible with the proxy type's filter was attempted. 

___


## recovery
 
### AlreadyProxy
- **interface**: `api.errors.recovery.AlreadyProxy.is`
- **summary**:    This account is already set up for recovery 
 
### AlreadyRecoverable
- **interface**: `api.errors.recovery.AlreadyRecoverable.is`
- **summary**:    This account is already set up for recovery 
 
### AlreadyStarted
- **interface**: `api.errors.recovery.AlreadyStarted.is`
- **summary**:    A recovery process has already started for this account 
 
### AlreadyVouched
- **interface**: `api.errors.recovery.AlreadyVouched.is`
- **summary**:    This user has already vouched for this recovery 
 
### BadState
- **interface**: `api.errors.recovery.BadState.is`
- **summary**:    Some internal state is broken. 
 
### DelayPeriod
- **interface**: `api.errors.recovery.DelayPeriod.is`
- **summary**:    The friend must wait until the delay period to vouch for this recovery 
 
### MaxFriends
- **interface**: `api.errors.recovery.MaxFriends.is`
- **summary**:    Friends list must be less than max friends 
 
### NotAllowed
- **interface**: `api.errors.recovery.NotAllowed.is`
- **summary**:    User is not allowed to make a call on behalf of this account 
 
### NotEnoughFriends
- **interface**: `api.errors.recovery.NotEnoughFriends.is`
- **summary**:    Friends list must be greater than zero and threshold 
 
### NotFriend
- **interface**: `api.errors.recovery.NotFriend.is`
- **summary**:    This account is not a friend who can vouch 
 
### NotRecoverable
- **interface**: `api.errors.recovery.NotRecoverable.is`
- **summary**:    This account is not set up for recovery 
 
### NotSorted
- **interface**: `api.errors.recovery.NotSorted.is`
- **summary**:    Friends list must be sorted and free of duplicates 
 
### NotStarted
- **interface**: `api.errors.recovery.NotStarted.is`
- **summary**:    A recovery process has not started for this rescuer 
 
### StillActive
- **interface**: `api.errors.recovery.StillActive.is`
- **summary**:    There are still active recovery attempts that need to be closed 
 
### Threshold
- **interface**: `api.errors.recovery.Threshold.is`
- **summary**:    The threshold for recovering this account has not been met 
 
### ZeroThreshold
- **interface**: `api.errors.recovery.ZeroThreshold.is`
- **summary**:    Threshold must be greater than zero 

___


## scheduler
 
### FailedToSchedule
- **interface**: `api.errors.scheduler.FailedToSchedule.is`
- **summary**:    Failed to schedule a call 
 
### NotFound
- **interface**: `api.errors.scheduler.NotFound.is`
- **summary**:    Cannot find the scheduled call. 
 
### RescheduleNoChange
- **interface**: `api.errors.scheduler.RescheduleNoChange.is`
- **summary**:    Reschedule failed because it does not change scheduled time. 
 
### TargetBlockNumberInPast
- **interface**: `api.errors.scheduler.TargetBlockNumberInPast.is`
- **summary**:    Given target block number is in the past. 

___


## session
 
### DuplicatedKey
- **interface**: `api.errors.session.DuplicatedKey.is`
- **summary**:    Registered duplicate key. 
 
### InvalidProof
- **interface**: `api.errors.session.InvalidProof.is`
- **summary**:    Invalid ownership proof. 
 
### NoAccount
- **interface**: `api.errors.session.NoAccount.is`
- **summary**:    Key setting account is not live, so it's impossible to associate keys. 
 
### NoAssociatedValidatorId
- **interface**: `api.errors.session.NoAssociatedValidatorId.is`
- **summary**:    No associated validator ID for account. 
 
### NoKeys
- **interface**: `api.errors.session.NoKeys.is`
- **summary**:    No keys are associated with this account. 

___


## sft
 
### InsufficientBalance
- **interface**: `api.errors.sft.InsufficientBalance.is`
- **summary**:    The user does not own enough of this token to perform the operation 
 
### InvalidMaxIssuance
- **interface**: `api.errors.sft.InvalidMaxIssuance.is`
- **summary**:    Max issuance needs to be greater than 0 and initial_issuance  Cannot exceed MaxTokensPerCollection 
 
### InvalidNewOwner
- **interface**: `api.errors.sft.InvalidNewOwner.is`
- **summary**:    Caller can not be the new owner 
 
### InvalidQuantity
- **interface**: `api.errors.sft.InvalidQuantity.is`
- **summary**:    The specified quantity must be greater than 0 
 
### MaxIssuanceAlreadySet
- **interface**: `api.errors.sft.MaxIssuanceAlreadySet.is`
- **summary**:    The max issuance has already been set and can't be changed 
 
### MaxIssuanceReached
- **interface**: `api.errors.sft.MaxIssuanceReached.is`
- **summary**:    The collection max issuance has been reached and no more tokens can be minted 
 
### MaxOwnersReached
- **interface**: `api.errors.sft.MaxOwnersReached.is`
- **summary**:    The max amount of owners per token has been reached 
 
### NameInvalid
- **interface**: `api.errors.sft.NameInvalid.is`
- **summary**:    Given collection or token name is invalid (invalid utf-8, empty) 
 
### NoCollectionFound
- **interface**: `api.errors.sft.NoCollectionFound.is`
- **summary**:    The collection does not exist 
 
### NotCollectionOwner
- **interface**: `api.errors.sft.NotCollectionOwner.is`
- **summary**:    Origin is not the collection owner and is not permitted to perform the operation 
 
### NoToken
- **interface**: `api.errors.sft.NoToken.is`
- **summary**:    The token does not exist 
 
### Overflow
- **interface**: `api.errors.sft.Overflow.is`
- **summary**:    The operation would cause a numeric overflow 
 
### RoyaltiesInvalid
- **interface**: `api.errors.sft.RoyaltiesInvalid.is`
- **summary**:    Total royalties would exceed 100% of sale or an empty vec is supplied 

___


## staking
 
### AlreadyBonded
- **interface**: `api.errors.staking.AlreadyBonded.is`
- **summary**:    Stash is already bonded. 
 
### AlreadyClaimed
- **interface**: `api.errors.staking.AlreadyClaimed.is`
- **summary**:    Rewards for this era have already been claimed for this validator. 
 
### AlreadyPaired
- **interface**: `api.errors.staking.AlreadyPaired.is`
- **summary**:    Controller is already paired. 
 
### BadState
- **interface**: `api.errors.staking.BadState.is`
- **summary**:    Internal state has become somehow corrupted and the operation cannot continue. 
 
### BadTarget
- **interface**: `api.errors.staking.BadTarget.is`
- **summary**:    A nomination target was supplied that was blocked or otherwise not a validator. 
 
### CannotChillOther
- **interface**: `api.errors.staking.CannotChillOther.is`
- **summary**:    The user has enough bond and thus cannot be chilled forcefully by an external person. 
 
### CommissionTooLow
- **interface**: `api.errors.staking.CommissionTooLow.is`
- **summary**:    Commission is too low. Must be at least `MinCommission`. 
 
### DuplicateIndex
- **interface**: `api.errors.staking.DuplicateIndex.is`
- **summary**:    Duplicate index. 
 
### EmptyTargets
- **interface**: `api.errors.staking.EmptyTargets.is`
- **summary**:    Targets cannot be empty. 
 
### FundedTarget
- **interface**: `api.errors.staking.FundedTarget.is`
- **summary**:    Attempting to target a stash that still has funds. 
 
### IncorrectHistoryDepth
- **interface**: `api.errors.staking.IncorrectHistoryDepth.is`
- **summary**:    Incorrect previous history depth input provided. 
 
### IncorrectSlashingSpans
- **interface**: `api.errors.staking.IncorrectSlashingSpans.is`
- **summary**:    Incorrect number of slashing spans provided. 
 
### InsufficientBond
- **interface**: `api.errors.staking.InsufficientBond.is`
- **summary**:    Cannot have a validator or nominator role, with value less than the minimum defined by  governance (see `MinValidatorBond` and `MinNominatorBond`). If unbonding is the  intention, `chill` first to remove one's role as validator/nominator. 
 
### InvalidEraToReward
- **interface**: `api.errors.staking.InvalidEraToReward.is`
- **summary**:    Invalid era to reward. 
 
### InvalidNumberOfNominations
- **interface**: `api.errors.staking.InvalidNumberOfNominations.is`
- **summary**:    Invalid number of nominations. 
 
### InvalidSlashIndex
- **interface**: `api.errors.staking.InvalidSlashIndex.is`
- **summary**:    Slash record index out of bounds. 
 
### NoMoreChunks
- **interface**: `api.errors.staking.NoMoreChunks.is`
- **summary**:    Can not schedule more unlock chunks. 
 
### NotController
- **interface**: `api.errors.staking.NotController.is`
- **summary**:    Not a controller account. 
 
### NotSortedAndUnique
- **interface**: `api.errors.staking.NotSortedAndUnique.is`
- **summary**:    Items are not sorted and unique. 
 
### NotStash
- **interface**: `api.errors.staking.NotStash.is`
- **summary**:    Not a stash account. 
 
### NoUnlockChunk
- **interface**: `api.errors.staking.NoUnlockChunk.is`
- **summary**:    Can not rebond without unlocking chunks. 
 
### TooManyNominators
- **interface**: `api.errors.staking.TooManyNominators.is`
- **summary**:    There are too many nominators in the system. Governance needs to adjust the staking  settings to keep things safe for the runtime. 
 
### TooManyTargets
- **interface**: `api.errors.staking.TooManyTargets.is`
- **summary**:    Too many nomination targets supplied. 
 
### TooManyValidators
- **interface**: `api.errors.staking.TooManyValidators.is`
- **summary**:    There are too many validators in the system. Governance needs to adjust the staking  settings to keep things safe for the runtime. 

___


## sudo
 
### RequireSudo
- **interface**: `api.errors.sudo.RequireSudo.is`
- **summary**:    Sender must be the Sudo account 

___


## system
 
### CallFiltered
- **interface**: `api.errors.system.CallFiltered.is`
- **summary**:    The origin filter prevent the call to be dispatched. 
 
### FailedToExtractRuntimeVersion
- **interface**: `api.errors.system.FailedToExtractRuntimeVersion.is`
- **summary**:    Failed to extract the runtime version from the new runtime. 

   Either calling `Core_version` or decoding `RuntimeVersion` failed. 
 
### InvalidSpecName
- **interface**: `api.errors.system.InvalidSpecName.is`
- **summary**:    The name of specification does not match between the current runtime  and the new runtime. 
 
### NonDefaultComposite
- **interface**: `api.errors.system.NonDefaultComposite.is`
- **summary**:    Suicide called when the account has non-default composite data. 
 
### NonZeroRefCount
- **interface**: `api.errors.system.NonZeroRefCount.is`
- **summary**:    There is a non-zero reference count preventing the account from being purged. 
 
### SpecVersionNeedsToIncrease
- **interface**: `api.errors.system.SpecVersionNeedsToIncrease.is`
- **summary**:    The specification version is not allowed to decrease between the current runtime  and the new runtime. 

___


## tokenApprovals
 
### AlreadyApproved
- **interface**: `api.errors.tokenApprovals.AlreadyApproved.is`
- **summary**:    Address is already approved 
 
### ApprovalDoesntExist
- **interface**: `api.errors.tokenApprovals.ApprovalDoesntExist.is`
- **summary**:    There is no approval set for this token 
 
### ApprovedAmountTooLow
- **interface**: `api.errors.tokenApprovals.ApprovedAmountTooLow.is`
- **summary**:    The caller is not approved for the requested amount 
 
### CallerNotApproved
- **interface**: `api.errors.tokenApprovals.CallerNotApproved.is`
- **summary**:    The caller isn't approved for any amount 
 
### CallerNotOperator
- **interface**: `api.errors.tokenApprovals.CallerNotOperator.is`
- **summary**:    The caller account can't be the same as the operator account 
 
### NoToken
- **interface**: `api.errors.tokenApprovals.NoToken.is`
- **summary**:    The token doesn't exist 
 
### NotTokenOwner
- **interface**: `api.errors.tokenApprovals.NotTokenOwner.is`
- **summary**:    The account is not the owner of the token 
 
### NotTokenOwnerOrApproved
- **interface**: `api.errors.tokenApprovals.NotTokenOwnerOrApproved.is`
- **summary**:    The account is not the owner of the token or an approved account 

___


## utility
 
### TooManyCalls
- **interface**: `api.errors.utility.TooManyCalls.is`
- **summary**:    Too many calls batched. 

___


## voterList
 
### List
- **interface**: `api.errors.voterList.List.is`
- **summary**:    A error in the list interface implementation. 

___


## xls20
 
### MappingAlreadyExists
- **interface**: `api.errors.xls20.MappingAlreadyExists.is`
- **summary**:    There is already a Root native -> XLS-20 mapping for this token 
 
### NotCollectionOwner
- **interface**: `api.errors.xls20.NotCollectionOwner.is`
- **summary**:    No the owner of the collection 
 
### NoToken
- **interface**: `api.errors.xls20.NoToken.is`
- **summary**:    The NFT does not exist 
 
### NotRelayer
- **interface**: `api.errors.xls20.NotRelayer.is`
- **summary**:    The caller is not the relayer and does not have permission to perform this action 
 
### NotXLS20Compatible
- **interface**: `api.errors.xls20.NotXLS20Compatible.is`
- **summary**:    The collection is not compatible with XLS-20 
 
### Xls20MintFeeTooLow
- **interface**: `api.errors.xls20.Xls20MintFeeTooLow.is`
- **summary**:    The supplied fee for minting XLS-20 tokens is too low 

___


## xRPLBridge
 
### CannotProcessMoreTransactionsAtThatBlock
- **interface**: `api.errors.xrplBridge.CannotProcessMoreTransactionsAtThatBlock.is`
- **summary**:    Cannot process more transactions at that block 
 
### DoorAddressNotSet
- **interface**: `api.errors.xrplBridge.DoorAddressNotSet.is`
- **summary**:    The door address has not been configured 
 
### InvalidSigners
- **interface**: `api.errors.xrplBridge.InvalidSigners.is`
- **summary**:    The signers are not known by ethy 
 
### NextTicketSequenceParamsInvalid
- **interface**: `api.errors.xrplBridge.NextTicketSequenceParamsInvalid.is`
- **summary**:    The NextTicketSequenceParams is invalid 
 
### NextTicketSequenceParamsNotSet
- **interface**: `api.errors.xrplBridge.NextTicketSequenceParamsNotSet.is`
- **summary**:    The NextTicketSequenceParams has not been set 
 
### NotPermitted
- **interface**: `api.errors.xrplBridge.NotPermitted.is`
 
### RelayerDoesNotExists
- **interface**: `api.errors.xrplBridge.RelayerDoesNotExists.is`
 
### TicketSequenceParamsInvalid
- **interface**: `api.errors.xrplBridge.TicketSequenceParamsInvalid.is`
- **summary**:    The TicketSequenceParams is invalid 
 
### TooManySigners
- **interface**: `api.errors.xrplBridge.TooManySigners.is`
- **summary**:    XRPL does not allow more than 8 signers for door address 
 
### TxReplay
- **interface**: `api.errors.xrplBridge.TxReplay.is`
- **summary**:    Submitted a duplicate transaction hash 
 
### WithdrawInvalidAmount
- **interface**: `api.errors.xrplBridge.WithdrawInvalidAmount.is`
- **summary**:    Withdraw amount must be non-zero and <= u64 
