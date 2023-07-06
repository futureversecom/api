---
title: Extrinsics
---

The following sections contain Extrinsics methods are part of the default root runtime. On the api, these are exposed via `api.tx.<module>.<method>`. 

(NOTE: These were generated from a static/snapshot view of a recent default root runtime. Some items may not be available in older nodes, or in any customized implementations.)

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

- **[evm](#evm)**

- **[evmChainId](#evmchainid)**

- **[feeControl](#feecontrol)**

- **[feeProxy](#feeproxy)**

- **[futurepass](#futurepass)**

- **[grandpa](#grandpa)**

- **[imOnline](#imonline)**

- **[marketplace](#marketplace)**

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

- **[timestamp](#timestamp)**

- **[tokenApprovals](#tokenapprovals)**

- **[utility](#utility)**

- **[voterList](#voterlist)**

- **[xls20](#xls20)**

- **[xrplBridge](#xrplbridge)**


___


## assets
 
### approveTransfer(id: `Compact<u32>`, delegate: `SeedPrimitivesSignatureAccountId20`, amount: `Compact<u128>`)
- **interface**: `api.tx.assets.approveTransfer`
- **summary**:    Approve an amount of asset for transfer by a delegated third-party account. 

   Origin must be Signed. 

   Ensures that `ApprovalDeposit` worth of `Currency` is reserved from signing account  for the purpose of holding the approval. If some non-zero amount of assets is already  approved from signing account to `delegate`, then it is topped up or unreserved to  meet the right value. 

   NOTE: The signing account does not need to own `amount` of assets at the point of  making this call. 

   - `id`: The identifier of the asset. 

  - `delegate`: The account to delegate permission to transfer asset.

  - `amount`: The amount of asset that may be transferred by `delegate`. If there is already an approval in place, then this acts additively. 

   Emits `ApprovedTransfer` on success. 

   Weight: `O(1)` 
 
### burn(id: `Compact<u32>`, who: `SeedPrimitivesSignatureAccountId20`, amount: `Compact<u128>`)
- **interface**: `api.tx.assets.burn`
- **summary**:    Reduce the balance of `who` by as much as possible up to `amount` assets of `id`. 

   Origin must be Signed and the sender should be the Manager of the asset `id`. 

   Bails with `NoAccount` if the `who` is already dead. 

   - `id`: The identifier of the asset to have some amount burned. 

  - `who`: The account to be debited from.

  - `amount`: The maximum amount by which `who`'s balance should be reduced.

   Emits `Burned` with the actual amount burned. If this takes the balance to below the  minimum for the asset, then the amount burned is increased to take it to zero. 

   Weight: `O(1)`  Modes: Post-existence of `who`; Pre & post Zombie-status of `who`. 
 
### cancelApproval(id: `Compact<u32>`, delegate: `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.tx.assets.cancelApproval`
- **summary**:    Cancel all of some asset approved for delegated transfer by a third-party account. 

   Origin must be Signed and there must be an approval in place between signer and  `delegate`. 

   Unreserves any deposit previously reserved by `approve_transfer` for the approval. 

   - `id`: The identifier of the asset. 

  - `delegate`: The account delegated permission to transfer asset.

   Emits `ApprovalCancelled` on success. 

   Weight: `O(1)` 
 
### clearMetadata(id: `Compact<u32>`)
- **interface**: `api.tx.assets.clearMetadata`
- **summary**:    Clear the metadata for an asset. 

   Origin must be Signed and the sender should be the Owner of the asset `id`. 

   Any deposit is freed for the asset owner. 

   - `id`: The identifier of the asset to clear. 

   Emits `MetadataCleared`. 

   Weight: `O(1)` 
 
### create(id: `Compact<u32>`, admin: `SeedPrimitivesSignatureAccountId20`, min_balance: `u128`)
- **interface**: `api.tx.assets.create`
- **summary**:    Issue a new class of fungible assets from a public origin. 

   This new asset class has no assets initially and its owner is the origin. 

   The origin must be Signed and the sender must have sufficient funds free. 

   Funds of sender are reserved by `AssetDeposit`. 

   Parameters: 

  - `id`: The identifier of the new asset. This must not be currently in use to identify an existing asset. 

  - `admin`: The admin of this class of assets. The admin is the initial address of each member of the asset class's admin team. 

  - `min_balance`: The minimum balance of this new asset that any single account must have. If an account's balance is reduced below this, then it collapses to zero. 

   Emits `Created` event when successful. 

   Weight: `O(1)` 
 
### destroy(id: `Compact<u32>`, witness: `PalletAssetsDestroyWitness`)
- **interface**: `api.tx.assets.destroy`
- **summary**:    Destroy a class of fungible assets. 

   The origin must conform to `ForceOrigin` or must be Signed and the sender must be the  owner of the asset `id`. 

   - `id`: The identifier of the asset to be destroyed. This must identify an existing  asset. 

   Emits `Destroyed` event when successful. 

   NOTE: It can be helpful to first freeze an asset before destroying it so that you  can provide accurate witness information and prevent users from manipulating state  in a way that can make it harder to destroy. 

   Weight: `O(c + p + a)` where: 

  - `c = (witness.accounts - witness.sufficients)`

  - `s = witness.sufficients`

  - `a = witness.approvals`
 
### forceAssetStatus(id: `Compact<u32>`, owner: `SeedPrimitivesSignatureAccountId20`, issuer: `SeedPrimitivesSignatureAccountId20`, admin: `SeedPrimitivesSignatureAccountId20`, freezer: `SeedPrimitivesSignatureAccountId20`, min_balance: `Compact<u128>`, is_sufficient: `bool`, is_frozen: `bool`)
- **interface**: `api.tx.assets.forceAssetStatus`
- **summary**:    Alter the attributes of a given asset. 

   Origin must be `ForceOrigin`. 

   - `id`: The identifier of the asset. 

  - `owner`: The new Owner of this asset.

  - `issuer`: The new Issuer of this asset.

  - `admin`: The new Admin of this asset.

  - `freezer`: The new Freezer of this asset.

  - `min_balance`: The minimum balance of this new asset that any single account must have. If an account's balance is reduced below this, then it collapses to zero. 

  - `is_sufficient`: Whether a non-zero balance of this asset is deposit of sufficient value to account for the state bloat associated with its balance storage. If set to  `true`, then non-zero balances may be stored without a `consumer` reference (and thus  an ED in the Balances pallet or whatever else is used to control user-account state  growth). 

  - `is_frozen`: Whether this asset class is frozen except for permissioned/admin instructions. 

   Emits `AssetStatusChanged` with the identity of the asset. 

   Weight: `O(1)` 
 
### forceCancelApproval(id: `Compact<u32>`, owner: `SeedPrimitivesSignatureAccountId20`, delegate: `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.tx.assets.forceCancelApproval`
- **summary**:    Cancel all of some asset approved for delegated transfer by a third-party account. 

   Origin must be either ForceOrigin or Signed origin with the signer being the Admin  account of the asset `id`. 

   Unreserves any deposit previously reserved by `approve_transfer` for the approval. 

   - `id`: The identifier of the asset. 

  - `delegate`: The account delegated permission to transfer asset.

   Emits `ApprovalCancelled` on success. 

   Weight: `O(1)` 
 
### forceClearMetadata(id: `Compact<u32>`)
- **interface**: `api.tx.assets.forceClearMetadata`
- **summary**:    Clear the metadata for an asset. 

   Origin must be ForceOrigin. 

   Any deposit is returned. 

   - `id`: The identifier of the asset to clear. 

   Emits `MetadataCleared`. 

   Weight: `O(1)` 
 
### forceCreate(id: `Compact<u32>`, owner: `SeedPrimitivesSignatureAccountId20`, is_sufficient: `bool`, min_balance: `Compact<u128>`)
- **interface**: `api.tx.assets.forceCreate`
- **summary**:    Issue a new class of fungible assets from a privileged origin. 

   This new asset class has no assets initially. 

   The origin must conform to `ForceOrigin`. 

   Unlike `create`, no funds are reserved. 

   - `id`: The identifier of the new asset. This must not be currently in use to identify  an existing asset. 

  - `owner`: The owner of this class of assets. The owner has full superuser permissions over this asset, but may later change and configure the permissions using  `transfer_ownership` and `set_team`. 

  - `min_balance`: The minimum balance of this new asset that any single account must have. If an account's balance is reduced below this, then it collapses to zero. 

   Emits `ForceCreated` event when successful. 

   Weight: `O(1)` 
 
### forceSetMetadata(id: `Compact<u32>`, name: `Bytes`, symbol: `Bytes`, decimals: `u8`, is_frozen: `bool`)
- **interface**: `api.tx.assets.forceSetMetadata`
- **summary**:    Force the metadata for an asset to some value. 

   Origin must be ForceOrigin. 

   Any deposit is left alone. 

   - `id`: The identifier of the asset to update. 

  - `name`: The user friendly name of this asset. Limited in length by `StringLimit`.

  - `symbol`: The exchange symbol for this asset. Limited in length by `StringLimit`.

  - `decimals`: The number of decimals this asset uses to represent one unit.

   Emits `MetadataSet`. 

   Weight: `O(N + S)` where N and S are the length of the name and symbol respectively. 
 
### forceTransfer(id: `Compact<u32>`, source: `SeedPrimitivesSignatureAccountId20`, dest: `SeedPrimitivesSignatureAccountId20`, amount: `Compact<u128>`)
- **interface**: `api.tx.assets.forceTransfer`
- **summary**:    Move some assets from one account to another. 

   Origin must be Signed and the sender should be the Admin of the asset `id`. 

   - `id`: The identifier of the asset to have some amount transferred. 

  - `source`: The account to be debited.

  - `dest`: The account to be credited.

  - `amount`: The amount by which the `source`'s balance of assets should be reduced and `dest`'s balance increased. The amount actually transferred may be slightly greater in  the case that the transfer would otherwise take the `source` balance above zero but  below the minimum balance. Must be greater than zero. 

   Emits `Transferred` with the actual amount transferred. If this takes the source balance  to below the minimum for the asset, then the amount transferred is increased to take it  to zero. 

   Weight: `O(1)`  Modes: Pre-existence of `dest`; Post-existence of `source`; Account pre-existence of  `dest`. 
 
### freeze(id: `Compact<u32>`, who: `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.tx.assets.freeze`
- **summary**:    Disallow further unprivileged transfers from an account. 

   Origin must be Signed and the sender should be the Freezer of the asset `id`. 

   - `id`: The identifier of the asset to be frozen. 

  - `who`: The account to be frozen.

   Emits `Frozen`. 

   Weight: `O(1)` 
 
### freezeAsset(id: `Compact<u32>`)
- **interface**: `api.tx.assets.freezeAsset`
- **summary**:    Disallow further unprivileged transfers for the asset class. 

   Origin must be Signed and the sender should be the Freezer of the asset `id`. 

   - `id`: The identifier of the asset to be frozen. 

   Emits `Frozen`. 

   Weight: `O(1)` 
 
### mint(id: `Compact<u32>`, beneficiary: `SeedPrimitivesSignatureAccountId20`, amount: `Compact<u128>`)
- **interface**: `api.tx.assets.mint`
- **summary**:    Mint assets of a particular class. 

   The origin must be Signed and the sender must be the Issuer of the asset `id`. 

   - `id`: The identifier of the asset to have some amount minted. 

  - `beneficiary`: The account to be credited with the minted assets.

  - `amount`: The amount of the asset to be minted.

   Emits `Issued` event when successful. 

   Weight: `O(1)`  Modes: Pre-existing balance of `beneficiary`; Account pre-existence of `beneficiary`. 
 
### refund(id: `Compact<u32>`, allow_burn: `bool`)
- **interface**: `api.tx.assets.refund`
- **summary**:    Return the deposit (if any) of an asset account. 

   The origin must be Signed. 

   - `id`: The identifier of the asset for the account to be created. 

  - `allow_burn`: If `true` then assets may be destroyed in order to complete the refund.

   Emits `Refunded` event when successful. 
 
### setMetadata(id: `Compact<u32>`, name: `Bytes`, symbol: `Bytes`, decimals: `u8`)
- **interface**: `api.tx.assets.setMetadata`
- **summary**:    Set the metadata for an asset. 

   Origin must be Signed and the sender should be the Owner of the asset `id`. 

   Funds of sender are reserved according to the formula:  `MetadataDepositBase + MetadataDepositPerByte * (name.len + symbol.len)` taking into  account any already reserved funds. 

   - `id`: The identifier of the asset to update. 

  - `name`: The user friendly name of this asset. Limited in length by `StringLimit`.

  - `symbol`: The exchange symbol for this asset. Limited in length by `StringLimit`.

  - `decimals`: The number of decimals this asset uses to represent one unit.

   Emits `MetadataSet`. 

   Weight: `O(1)` 
 
### setTeam(id: `Compact<u32>`, issuer: `SeedPrimitivesSignatureAccountId20`, admin: `SeedPrimitivesSignatureAccountId20`, freezer: `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.tx.assets.setTeam`
- **summary**:    Change the Issuer, Admin and Freezer of an asset. 

   Origin must be Signed and the sender should be the Owner of the asset `id`. 

   - `id`: The identifier of the asset to be frozen. 

  - `issuer`: The new Issuer of this asset.

  - `admin`: The new Admin of this asset.

  - `freezer`: The new Freezer of this asset.

   Emits `TeamChanged`. 

   Weight: `O(1)` 
 
### thaw(id: `Compact<u32>`, who: `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.tx.assets.thaw`
- **summary**:    Allow unprivileged transfers from an account again. 

   Origin must be Signed and the sender should be the Admin of the asset `id`. 

   - `id`: The identifier of the asset to be frozen. 

  - `who`: The account to be unfrozen.

   Emits `Thawed`. 

   Weight: `O(1)` 
 
### thawAsset(id: `Compact<u32>`)
- **interface**: `api.tx.assets.thawAsset`
- **summary**:    Allow unprivileged transfers for the asset again. 

   Origin must be Signed and the sender should be the Admin of the asset `id`. 

   - `id`: The identifier of the asset to be thawed. 

   Emits `Thawed`. 

   Weight: `O(1)` 
 
### touch(id: `Compact<u32>`)
- **interface**: `api.tx.assets.touch`
- **summary**:    Create an asset account for non-provider assets. 

   A deposit will be taken from the signer account. 

   - `origin`: Must be Signed; the signer account must have sufficient funds for a deposit  to be taken. 

  - `id`: The identifier of the asset for the account to be created.

   Emits `Touched` event when successful. 
 
### transfer(id: `Compact<u32>`, target: `SeedPrimitivesSignatureAccountId20`, amount: `Compact<u128>`)
- **interface**: `api.tx.assets.transfer`
- **summary**:    Move some assets from the sender account to another. 

   Origin must be Signed. 

   - `id`: The identifier of the asset to have some amount transferred. 

  - `target`: The account to be credited.

  - `amount`: The amount by which the sender's balance of assets should be reduced and `target`'s balance increased. The amount actually transferred may be slightly greater in  the case that the transfer would otherwise take the sender balance above zero but below  the minimum balance. Must be greater than zero. 

   Emits `Transferred` with the actual amount transferred. If this takes the source balance  to below the minimum for the asset, then the amount transferred is increased to take it  to zero. 

   Weight: `O(1)`  Modes: Pre-existence of `target`; Post-existence of sender; Account pre-existence of  `target`. 
 
### transferApproved(id: `Compact<u32>`, owner: `SeedPrimitivesSignatureAccountId20`, destination: `SeedPrimitivesSignatureAccountId20`, amount: `Compact<u128>`)
- **interface**: `api.tx.assets.transferApproved`
- **summary**:    Transfer some asset balance from a previously delegated account to some third-party  account. 

   Origin must be Signed and there must be an approval in place by the `owner` to the  signer. 

   If the entire amount approved for transfer is transferred, then any deposit previously  reserved by `approve_transfer` is unreserved. 

   - `id`: The identifier of the asset. 

  - `owner`: The account which previously approved for a transfer of at least `amount` and from which the asset balance will be withdrawn. 

  - `destination`: The account to which the asset balance of `amount` will be transferred.

  - `amount`: The amount of assets to transfer.

   Emits `TransferredApproved` on success. 

   Weight: `O(1)` 
 
### transferKeepAlive(id: `Compact<u32>`, target: `SeedPrimitivesSignatureAccountId20`, amount: `Compact<u128>`)
- **interface**: `api.tx.assets.transferKeepAlive`
- **summary**:    Move some assets from the sender account to another, keeping the sender account alive. 

   Origin must be Signed. 

   - `id`: The identifier of the asset to have some amount transferred. 

  - `target`: The account to be credited.

  - `amount`: The amount by which the sender's balance of assets should be reduced and `target`'s balance increased. The amount actually transferred may be slightly greater in  the case that the transfer would otherwise take the sender balance above zero but below  the minimum balance. Must be greater than zero. 

   Emits `Transferred` with the actual amount transferred. If this takes the source balance  to below the minimum for the asset, then the amount transferred is increased to take it  to zero. 

   Weight: `O(1)`  Modes: Pre-existence of `target`; Post-existence of sender; Account pre-existence of  `target`. 
 
### transferOwnership(id: `Compact<u32>`, owner: `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.tx.assets.transferOwnership`
- **summary**:    Change the Owner of an asset. 

   Origin must be Signed and the sender should be the Owner of the asset `id`. 

   - `id`: The identifier of the asset. 

  - `owner`: The new Owner of this asset.

   Emits `OwnerChanged`. 

   Weight: `O(1)` 

___


## assetsExt
 
### createAsset(name: `Bytes`, symbol: `Bytes`, decimals: `u8`, min_balance: `Option<u128>`, owner: `Option<SeedPrimitivesSignatureAccountId20>`)
- **interface**: `api.tx.assetsExt.createAsset`
- **summary**:    Creates a new asset with unique ID according to the network asset id scheme. 

___


## authorship
 
### setUncles(new_uncles: `Vec<SpRuntimeHeader>`)
- **interface**: `api.tx.authorship.setUncles`
- **summary**:    Provide a set of uncles. 

___


## babe
 
### planConfigChange(config: `SpConsensusBabeDigestsNextConfigDescriptor`)
- **interface**: `api.tx.babe.planConfigChange`
- **summary**:    Plan an epoch config change. The epoch config change is recorded and will be enacted on  the next call to `enact_epoch_change`. The config will be activated one epoch after.  Multiple calls to this method will replace any existing planned config change that had  not been enacted yet. 
 
### reportEquivocation(equivocation_proof: `SpConsensusSlotsEquivocationProof`, key_owner_proof: `SpSessionMembershipProof`)
- **interface**: `api.tx.babe.reportEquivocation`
- **summary**:    Report authority equivocation/misbehavior. This method will verify  the equivocation proof and validate the given key ownership proof  against the extracted offender. If both are valid, the offence will  be reported. 
 
### reportEquivocationUnsigned(equivocation_proof: `SpConsensusSlotsEquivocationProof`, key_owner_proof: `SpSessionMembershipProof`)
- **interface**: `api.tx.babe.reportEquivocationUnsigned`
- **summary**:    Report authority equivocation/misbehavior. This method will verify  the equivocation proof and validate the given key ownership proof  against the extracted offender. If both are valid, the offence will  be reported.  This extrinsic must be called unsigned and it is expected that only  block authors will call it (validated in `ValidateUnsigned`), as such  if the block author is defined it will be defined as the equivocation  reporter. 

___


## balances
 
### forceTransfer(source: `SeedPrimitivesSignatureAccountId20`, dest: `SeedPrimitivesSignatureAccountId20`, value: `Compact<u128>`)
- **interface**: `api.tx.balances.forceTransfer`
- **summary**:    Exactly as `transfer`, except the origin must be root and the source account may be  specified.   
 
### forceUnreserve(who: `SeedPrimitivesSignatureAccountId20`, amount: `u128`)
- **interface**: `api.tx.balances.forceUnreserve`
- **summary**:    Unreserve some balance from a user by force. 

   Can only be called by ROOT. 
 
### setBalance(who: `SeedPrimitivesSignatureAccountId20`, new_free: `Compact<u128>`, new_reserved: `Compact<u128>`)
- **interface**: `api.tx.balances.setBalance`
- **summary**:    Set the balances of a given account. 

   This will alter `FreeBalance` and `ReservedBalance` in storage. it will  also alter the total issuance of the system (`TotalIssuance`) appropriately.  If the new free or reserved balance is below the existential deposit,  it will reset the account nonce (`frame_system::AccountNonce`). 

   The dispatch origin for this call is `root`. 
 
### transfer(dest: `SeedPrimitivesSignatureAccountId20`, value: `Compact<u128>`)
- **interface**: `api.tx.balances.transfer`
- **summary**:    Transfer some liquid free balance to another account. 

   `transfer` will set the `FreeBalance` of the sender and receiver.  If the sender's account is below the existential deposit as a result  of the transfer, the account will be reaped. 

   The dispatch origin for this call must be `Signed` by the transactor. 

    
 
### transferAll(dest: `SeedPrimitivesSignatureAccountId20`, keep_alive: `bool`)
- **interface**: `api.tx.balances.transferAll`
- **summary**:    Transfer the entire transferable balance from the caller account. 

   NOTE: This function only attempts to transfer _transferable_ balances. This means that  any locked, reserved, or existential deposits (when `keep_alive` is `true`), will not be  transferred by this function. To ensure that this function results in a killed account,  you might need to prepare the account by removing any reference counters, storage  deposits, etc... 

   The dispatch origin of this call must be Signed. 

   - `dest`: The recipient of the transfer. 

  - `keep_alive`: A boolean to determine if the `transfer_all` operation should send all of the funds the account has, causing the sender account to be killed (false), or  transfer everything except at least the existential deposit, which will guarantee to  keep the sender account alive (true). #  
 
### transferKeepAlive(dest: `SeedPrimitivesSignatureAccountId20`, value: `Compact<u128>`)
- **interface**: `api.tx.balances.transferKeepAlive`
- **summary**:    Same as the [`transfer`] call, but with a check that the transfer will not kill the  origin account. 

   99% of the time you want [`transfer`] instead. 

   [`transfer`]: struct.Pallet.html#method.transfer 

___


## dex
 
### addLiquidity(token_a: `u32`, token_b: `u32`, amount_a_desired: `Compact<u128>`, amount_b_desired: `Compact<u128>`, amount_a_min: `Compact<u128>`, amount_b_min: `Compact<u128>`, to: `Option<SeedPrimitivesSignatureAccountId20>`, deadline: `Option<u32>`)
- **interface**: `api.tx.dex.addLiquidity`
- **summary**:    Add liquidity to Enabled trading pair, or add provision to Provisioning trading pair. 

  - Add liquidity success will issue shares in current price which decided by the liquidity scale. Shares are temporarily not  allowed to transfer and trade, it represents the proportion of  assets in liquidity pool. 

  - Add provision success will record the provision, issue shares to caller in the initial price when trading pair convert to Enabled. 

  - Creates and enables TradingPair LP token if it does not exist for trading pair.

  - Fails to add liquidity for `NotEnabled` trading pair.

   - `token_a`: Asset id A. 

  - `token_b`: Asset id B.

  - `amount_a_desired`: amount a desired to add.

  - `amount_b_desired`: amount b desired to add.

  - `amount_a_min`: amount a minimum willing to add.

  - `amount_b_min`: amount b minimum willing to add.

  - `to`: The recipient of the LP token. The caller is the default recipient if it is set to None. 

  - `deadline`: The deadline of executing this extrinsic. The deadline won't be checked if it is set to None 
 
### disableTradingPair(token_a: `u32`, token_b: `u32`)
- **interface**: `api.tx.dex.disableTradingPair`
- **summary**:    Disable an `Enabled` trading pair. 

  - Requires LP token to be created and in the `Enabled` status

  - Only root can disable trading pair

   - `token_a`: Asset id A. 

  - `token_b`: Asset id B.
 
### reenableTradingPair(token_a: `u32`, token_b: `u32`)
- **interface**: `api.tx.dex.reenableTradingPair`
- **summary**:    Re enable a `NotEnabled` trading pair. 

  - Requires LP token to be created and in the `NotEnabled` status

  - Only root can enable a disabled trading pair

   - `token_a`: Asset id A. 

  - `token_b`: Asset id B.
 
### removeLiquidity(token_a: `u32`, token_b: `u32`, liquidity: `Compact<u128>`, amount_a_min: `Compact<u128>`, amount_b_min: `Compact<u128>`, to: `Option<SeedPrimitivesSignatureAccountId20>`, deadline: `Option<u32>`)
- **interface**: `api.tx.dex.removeLiquidity`
- **summary**:    Remove liquidity from specific liquidity pool in the form of burning  shares, and withdrawing currencies in trading pairs from liquidity  pool in proportion, and withdraw liquidity incentive interest. 

  - note: liquidity can still be withdrawn for `NotEnabled` trading pairs.

   - `token_a`: Asset id A. 

  - `token_b`: Asset id B.

  - `liquidity`: liquidity amount to remove.

  - `amount_a_min`: minimum amount of asset A to be withdrawn from LP token.

  - `amount_b_min`: minimum amount of asset B to be withdrawn from LP token.

  - `to`: The recipient of the withdrawn token assets. The caller is the default recipient if it is set to None. 

  - `deadline`: The deadline of executing this extrinsic. The deadline won't be checked if it is set to None 
 
### swapWithExactSupply(amount_in: `Compact<u128>`, amount_out_min: `Compact<u128>`, path: `Vec<u32>`, to: `Option<SeedPrimitivesSignatureAccountId20>`, deadline: `Option<u32>`)
- **interface**: `api.tx.dex.swapWithExactSupply`
- **summary**:    Trading with DEX, swap with exact supply amount. Specify your input; retrieve variable  output. 

  - note: analogous to Uniswapv2 `swapExactTokensForTokens`

   - `path`: trading path. 

  - `amount_in`: exact supply amount.

  - `amount_out_min`: acceptable minimum target amount.

  - `to`: The recipient of the swapped token asset. The caller is the default recipient if it is set to None. 

  - `deadline`: The deadline of executing this extrinsic. The deadline won't be checked if it is set to None 
 
### swapWithExactTarget(amount_out: `Compact<u128>`, amount_in_max: `Compact<u128>`, path: `Vec<u32>`, to: `Option<SeedPrimitivesSignatureAccountId20>`, deadline: `Option<u32>`)
- **interface**: `api.tx.dex.swapWithExactTarget`
- **summary**:    Trading with DEX, swap with exact target amount. Specify your output; supply variable  input. 

  - note: analogous to Uniswapv2 `swapTokensForExactTokens`

   - `amount_out`: exact target amount. 

  - `amount_in_max`: acceptable maximum supply amount.

  - `path`: trading path.

  - `to`: The recipient of the swapped token asset. The caller is the default recipient if it is set to None. 

  - `deadline`: The deadline of executing this extrinsic. The deadline won't be checked if it is set to None 

___


## echo
 
### ping(destination: `H160`)
- **interface**: `api.tx.echo.ping`
- **summary**:    Ping extrinsic sends an event to the bridge containing a message 

___


## electionProviderMultiPhase
 
### governanceFallback(maybe_max_voters: `Option<u32>`, maybe_max_targets: `Option<u32>`)
- **interface**: `api.tx.electionProviderMultiPhase.governanceFallback`
- **summary**:    Trigger the governance fallback. 

   This can only be called when [`Phase::Emergency`] is enabled, as an alternative to  calling [`Call::set_emergency_election_result`]. 
 
### setEmergencyElectionResult(supports: `Vec<(SeedPrimitivesSignatureAccountId20,SpNposElectionsSupport)>`)
- **interface**: `api.tx.electionProviderMultiPhase.setEmergencyElectionResult`
- **summary**:    Set a solution in the queue, to be handed out to the client of this pallet in the next  call to `ElectionProvider::elect`. 

   This can only be set by `T::ForceOrigin`, and only when the phase is `Emergency`. 

   The solution is not checked for any feasibility and is assumed to be trustworthy, as any  feasibility check itself can in principle cause the election process to fail (due to  memory/weight constrains). 
 
### setMinimumUntrustedScore(maybe_next_score: `Option<SpNposElectionsElectionScore>`)
- **interface**: `api.tx.electionProviderMultiPhase.setMinimumUntrustedScore`
- **summary**:    Set a new value for `MinimumUntrustedScore`. 

   Dispatch origin must be aligned with `T::ForceOrigin`. 

   This check can be turned off by setting the value to `None`. 
 
### submit(raw_solution: `PalletElectionProviderMultiPhaseRawSolution`)
- **interface**: `api.tx.electionProviderMultiPhase.submit`
- **summary**:    Submit a solution for the signed phase. 

   The dispatch origin fo this call must be __signed__. 

   The solution is potentially queued, based on the claimed score and processed at the end  of the signed phase. 

   A deposit is reserved and recorded for the solution. Based on the outcome, the solution  might be rewarded, slashed, or get all or a part of the deposit back. 
 
### submitUnsigned(raw_solution: `PalletElectionProviderMultiPhaseRawSolution`, witness: `PalletElectionProviderMultiPhaseSolutionOrSnapshotSize`)
- **interface**: `api.tx.electionProviderMultiPhase.submitUnsigned`
- **summary**:    Submit a solution for the unsigned phase. 

   The dispatch origin fo this call must be __none__. 

   This submission is checked on the fly. Moreover, this unsigned solution is only  validated when submitted to the pool from the **local** node. Effectively, this means  that only active validators can submit this transaction when authoring a block (similar  to an inherent). 

   To prevent any incorrect solution (and thus wasted time/weight), this transaction will  panic if the solution submitted by the validator is invalid in any way, effectively  putting their authoring reward at risk. 

   No deposit or reward is associated with this submission. 

___


## erc20Peg
 
### activateDeposits(activate: `bool`)
- **interface**: `api.tx.erc20Peg.activateDeposits`
- **summary**:    Activate/deactivate deposits (root only) 
 
### activateWithdrawals(activate: `bool`)
- **interface**: `api.tx.erc20Peg.activateWithdrawals`
- **summary**:    Activate/deactivate withdrawals (root only) 
 
### setContractAddress(eth_address: `H160`)
- **interface**: `api.tx.erc20Peg.setContractAddress`
 
### setErc20Meta(details: `Vec<(H160,Bytes,u8)>`)
- **interface**: `api.tx.erc20Peg.setErc20Meta`
 
### setPaymentDelay(asset_id: `u32`, min_balance: `u128`, delay: `u32`)
- **interface**: `api.tx.erc20Peg.setPaymentDelay`
 
### withdraw(asset_id: `u32`, amount: `u128`, beneficiary: `H160`)
- **interface**: `api.tx.erc20Peg.withdraw`

___


## ethBridge
 
### depositRelayerBond()
- **interface**: `api.tx.ethBridge.depositRelayerBond`
 
### finaliseAuthoritiesChange(next_notary_keys: `Vec<SeedPrimitivesEthyCryptoAppCryptoPublic>`)
- **interface**: `api.tx.ethBridge.finaliseAuthoritiesChange`
 
### setBridgePaused(paused: `bool`)
- **interface**: `api.tx.ethBridge.setBridgePaused`
 
### setChallengePeriod(blocks: `u32`)
- **interface**: `api.tx.ethBridge.setChallengePeriod`
 
### setContractAddress(contract_address: `H160`)
- **interface**: `api.tx.ethBridge.setContractAddress`
 
### setDelayedEventProofsPerBlock(count: `u8`)
- **interface**: `api.tx.ethBridge.setDelayedEventProofsPerBlock`
 
### setEventBlockConfirmations(confirmations: `u64`)
- **interface**: `api.tx.ethBridge.setEventBlockConfirmations`
 
### setRelayer(relayer: `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.tx.ethBridge.setRelayer`
 
### setXrplDoorSigners(new_signers: `Vec<SeedPrimitivesEthyCryptoAppCryptoPublic>`)
- **interface**: `api.tx.ethBridge.setXrplDoorSigners`
 
### submitChallenge(event_claim_id: `u64`)
- **interface**: `api.tx.ethBridge.submitChallenge`
 
### submitEvent(tx_hash: `H256`, event: `Bytes`)
- **interface**: `api.tx.ethBridge.submitEvent`
 
### submitNotarization(payload: `PalletEthyNotarizationPayload`, _signature: `SeedPrimitivesEthyCryptoAppCryptoSignature`)
- **interface**: `api.tx.ethBridge.submitNotarization`
 
### withdrawRelayerBond()
- **interface**: `api.tx.ethBridge.withdrawRelayerBond`

___


## ethereum
 
### transact(transaction: `EthereumTransactionTransactionV2`)
- **interface**: `api.tx.ethereum.transact`
- **summary**:    Transact an Ethereum transaction. 

___


## evm
 
### call(source: `H160`, target: `H160`, input: `Bytes`, value: `U256`, gas_limit: `u64`, max_fee_per_gas: `U256`, max_priority_fee_per_gas: `Option<U256>`, nonce: `Option<U256>`, access_list: `Vec<(H160,Vec<H256>)>`)
- **interface**: `api.tx.evm.call`
- **summary**:    Issue an EVM call operation. This is similar to a message call transaction in Ethereum. 
 
### create(source: `H160`, init: `Bytes`, value: `U256`, gas_limit: `u64`, max_fee_per_gas: `U256`, max_priority_fee_per_gas: `Option<U256>`, nonce: `Option<U256>`, access_list: `Vec<(H160,Vec<H256>)>`)
- **interface**: `api.tx.evm.create`
- **summary**:    Issue an EVM create operation. This is similar to a contract creation transaction in  Ethereum. 
 
### create2(source: `H160`, init: `Bytes`, salt: `H256`, value: `U256`, gas_limit: `u64`, max_fee_per_gas: `U256`, max_priority_fee_per_gas: `Option<U256>`, nonce: `Option<U256>`, access_list: `Vec<(H160,Vec<H256>)>`)
- **interface**: `api.tx.evm.create2`
- **summary**:    Issue an EVM create2 operation. 
 
### withdraw(address: `H160`, value: `u128`)
- **interface**: `api.tx.evm.withdraw`
- **summary**:    Withdraw balance from EVM into currency/balances pallet. 

___


## evmChainId
 
### setChainId(chain_id: `Compact<u64>`)
- **interface**: `api.tx.evmChainId.setChainId`

___


## feeControl
 
### setEvmBaseFee(value: `U256`)
- **interface**: `api.tx.feeControl.setEvmBaseFee`
 
### setWeightMultiplier(value: `Perbill`)
- **interface**: `api.tx.feeControl.setWeightMultiplier`

___


## feeProxy
 
### callWithFeePreferences(payment_asset: `u32`, max_payment: `u128`, call: `Call`)
- **interface**: `api.tx.feeProxy.callWithFeePreferences`
- **summary**:    Call an internal call with specified gas token  payment_asset: The token to be used for paying gas fees. This is exchanged in  OnChargeTransaction::withdraw_fee()  max_payment: The limit of how many tokens will be used to perform the exchange  call: The inner call to be performed after the exchange 

___


## futurepass
 
### create(account: `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.tx.futurepass.create`
- **summary**:    Create a futurepass account for the delegator that is able to make calls on behalf of  futurepass. 

   The dispatch origin for this call must be _Signed_. 

   Parameters: 

  - `account`: The delegated account for the futurepass.
 
### migrateEvmFuturepass(owner: `SeedPrimitivesSignatureAccountId20`, evm_futurepass: `SeedPrimitivesSignatureAccountId20`, asset_ids: `Vec<u32>`, collection_ids: `Vec<u32>`)
- **interface**: `api.tx.futurepass.migrateEvmFuturepass`
- **summary**:    This extrinsic migrates EVM-based Futurepass assets to the Substrate-based Futurepass  (native). 

   Parameters: 

  - `owner` - The account ID of the owner of the EVM-based Futurepass.

  - `evm_futurepass` - The account ID of the EVM-based Futurepass.

  - `asset_ids` - A vector of asset IDs representing the assets to be migrated.

  - `collection_ids` - A vector of collection IDs representing the NFTs collections to be migrated. 

    
 
### proxyExtrinsic(futurepass: `SeedPrimitivesSignatureAccountId20`, call: `Call`)
- **interface**: `api.tx.futurepass.proxyExtrinsic`
- **summary**:    Dispatch the given call through Futurepass account. Transaction fees will be paid by the  Futurepass The dispatch origin for this call must be _Signed_ 

   Parameters: 

  - `futurepass`: The Futurepass account though which the call is dispatched

  - `call`: The Call that needs to be dispatched through the Futurepass account

    
 
### registerDelegate(futurepass: `SeedPrimitivesSignatureAccountId20`, delegate: `SeedPrimitivesSignatureAccountId20`, proxy_type: `SeedRuntimeImplsProxyType`)
- **interface**: `api.tx.futurepass.registerDelegate`
- **summary**:    Register a delegator to an existing futurepass account.  Note: Only futurepass owner account can add more delegates. 

   The dispatch origin for this call must be _Signed_. 

   Parameters: 

  - `futurepass`: Futurepass account to register the account as delegate.

  - `proxy_type`: Delegate permission level

  - `delegate`: The delegated account for the futurepass.

    
 
### setFuturepassMigrator(migrator: `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.tx.futurepass.setFuturepassMigrator`
- **summary**:    Update futurepass native assets migrator admin account. 

   The dispatch origin for this call must be sudo/root origin. 

   Parameters: 

  - `migrator`: The new account that will become the futurepass asset migrator.
 
### transferFuturepass(new_owner: `Option<SeedPrimitivesSignatureAccountId20>`)
- **interface**: `api.tx.futurepass.transferFuturepass`
- **summary**:    Transfer ownership of a futurepass to a new account.  The new owner must not already own a futurepass.  This removes all delegates from the futurepass.  The new owner will be the only delegate; they can add more delegates. 

   The dispatch origin for this call must be _Signed_ and must be the current owner of the  futurepass. 

   Parameters: 

  - `new_owner`: The new account that will become the owner of the futurepass.
 
### unregisterDelegate(futurepass: `SeedPrimitivesSignatureAccountId20`, delegate: `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.tx.futurepass.unregisterDelegate`
- **summary**:    Unregister a delegate from a futurepass account. 

   The dispatch origin for this call must be _Signed_. 

   Parameters: 

  - `futurepass`: Futurepass account to unregister the delegate from.

  - `delegate`: The delegated account for the futurepass. Note: if caller is futurepass holder onwer,  they can remove any delegate (including themselves); otherwise the caller must be the  delegate (can only remove themself). 

    

___


## grandpa
 
### noteStalled(delay: `u32`, best_finalized_block_number: `u32`)
- **interface**: `api.tx.grandpa.noteStalled`
- **summary**:    Note that the current authority set of the GRANDPA finality gadget has stalled. 

   This will trigger a forced authority set change at the beginning of the next session, to  be enacted `delay` blocks after that. The `delay` should be high enough to safely assume  that the block signalling the forced change will not be re-orged e.g. 1000 blocks.  The block production rate (which may be slowed down because of finality lagging) should  be taken into account when choosing the `delay`. The GRANDPA voters based on the new  authority will start voting on top of `best_finalized_block_number` for new finalized  blocks. `best_finalized_block_number` should be the highest of the latest finalized  block of all validators of the new authority set. 

   Only callable by root. 
 
### reportEquivocation(equivocation_proof: `SpFinalityGrandpaEquivocationProof`, key_owner_proof: `SpCoreVoid`)
- **interface**: `api.tx.grandpa.reportEquivocation`
- **summary**:    Report voter equivocation/misbehavior. This method will verify the  equivocation proof and validate the given key ownership proof  against the extracted offender. If both are valid, the offence  will be reported. 
 
### reportEquivocationUnsigned(equivocation_proof: `SpFinalityGrandpaEquivocationProof`, key_owner_proof: `SpCoreVoid`)
- **interface**: `api.tx.grandpa.reportEquivocationUnsigned`
- **summary**:    Report voter equivocation/misbehavior. This method will verify the  equivocation proof and validate the given key ownership proof  against the extracted offender. If both are valid, the offence  will be reported. 

   This extrinsic must be called unsigned and it is expected that only  block authors will call it (validated in `ValidateUnsigned`), as such  if the block author is defined it will be defined as the equivocation  reporter. 

___


## imOnline
 
### heartbeat(heartbeat: `PalletImOnlineHeartbeat`, signature: `PalletImOnlineSr25519AppSr25519Signature`)
- **interface**: `api.tx.imOnline.heartbeat`
- **summary**:     

___


## marketplace
 
### acceptOffer(offer_id: `u64`)
- **interface**: `api.tx.marketplace.acceptOffer`
- **summary**:    Accepts an offer on a token  Caller must be token owner 
 
### auctionNft(collection_id: `u32`, serial_numbers: `Vec<u32>`, payment_asset: `u32`, reserve_price: `u128`, duration: `Option<u32>`, marketplace_id: `Option<u32>`)
- **interface**: `api.tx.marketplace.auctionNft`
- **summary**:    Auction a bundle of tokens on the open market to the highest bidder 

  - Tokens must be from the same collection

  - Tokens with individual royalties schedules cannot be sold in bundles

   Caller must be the token owner 

  - `payment_asset` fungible asset Id to receive payment with

  - `reserve_price` winning bid must be over this threshold

  - `duration` length of the auction (in blocks), uses default duration if unspecified
 
### bid(listing_id: `u128`, amount: `u128`)
- **interface**: `api.tx.marketplace.bid`
- **summary**:    Place a bid on an open auction 

  - `amount` to bid (in the seller's requested payment asset)
 
### buy(listing_id: `u128`)
- **interface**: `api.tx.marketplace.buy`
- **summary**:    Buy a token listing for its specified price 
 
### cancelOffer(offer_id: `u64`)
- **interface**: `api.tx.marketplace.cancelOffer`
- **summary**:    Cancels an offer on a token  Caller must be the offer buyer 
 
### cancelSale(listing_id: `u128`)
- **interface**: `api.tx.marketplace.cancelSale`
- **summary**:    Close a sale or auction returning tokens  Requires no successful bids have been made for an auction.  Caller must be the listed seller 
 
### makeSimpleOffer(token_id: `(u32,u32)`, amount: `u128`, asset_id: `u32`, marketplace_id: `Option<u32>`)
- **interface**: `api.tx.marketplace.makeSimpleOffer`
- **summary**:    Create an offer on a token  Locks funds until offer is accepted, rejected or cancelled  An offer can't be made on a token currently in an auction  (This follows the behaviour of Opensea and forces the buyer to bid rather than create an  offer) 
 
### registerMarketplace(marketplace_account: `Option<SeedPrimitivesSignatureAccountId20>`, entitlement: `Permill`)
- **interface**: `api.tx.marketplace.registerMarketplace`
- **summary**:    Flag an account as a marketplace 

   `marketplace_account` - if specified, this account will be registered  `entitlement` - Permill, percentage of sales to go to the marketplace  If no marketplace is specified the caller will be registered 
 
### sellNft(collection_id: `u32`, serial_numbers: `Vec<u32>`, buyer: `Option<SeedPrimitivesSignatureAccountId20>`, payment_asset: `u32`, fixed_price: `u128`, duration: `Option<u32>`, marketplace_id: `Option<u32>`)
- **interface**: `api.tx.marketplace.sellNft`
- **summary**:    Sell a bundle of tokens at a fixed price 

  - Tokens must be from the same collection

  - Tokens with individual royalties schedules cannot be sold with this method

   `buyer` optionally, the account to receive the NFT. If unspecified, then any account may  purchase `asset_id` fungible asset Id to receive as payment for the NFT  `fixed_price` ask price  `duration` listing duration time in blocks from now  Caller must be the token owner 
 
### updateFixedPrice(listing_id: `u128`, new_price: `u128`)
- **interface**: `api.tx.marketplace.updateFixedPrice`
- **summary**:    Update fixed price for a single token sale 

   `listing_id` id of the fixed price listing  `new_price` new fixed price  Caller must be the token owner 

___


## nft
 
### acceptOffer(offer_id: `u64`)
- **interface**: `api.tx.nft.acceptOffer`
- **summary**:    Accepts an offer on a token  Caller must be token owner 
 
### auction(collection_id: `u32`, serial_numbers: `Vec<u32>`, payment_asset: `u32`, reserve_price: `u128`, duration: `Option<u32>`, marketplace_id: `Option<u32>`)
- **interface**: `api.tx.nft.auction`
- **summary**:    Auction a bundle of tokens on the open market to the highest bidder 

  - Tokens must be from the same collection

  - Tokens with individual royalties schedules cannot be sold in bundles

   Caller must be the token owner 

  - `payment_asset` fungible asset Id to receive payment with

  - `reserve_price` winning bid must be over this threshold

  - `duration` length of the auction (in blocks), uses default duration if unspecified
 
### bid(listing_id: `u128`, amount: `u128`)
- **interface**: `api.tx.nft.bid`
- **summary**:    Place a bid on an open auction 

  - `amount` to bid (in the seller's requested payment asset)
 
### burn(token_id: `(u32,u32)`)
- **interface**: `api.tx.nft.burn`
- **summary**:    Burn a token 🔥 

   Caller must be the token owner 
 
### buy(listing_id: `u128`)
- **interface**: `api.tx.nft.buy`
- **summary**:    Buy a token listing for its specified price 
 
### cancelOffer(offer_id: `u64`)
- **interface**: `api.tx.nft.cancelOffer`
- **summary**:    Cancels an offer on a token  Caller must be the offer buyer 
 
### cancelSale(listing_id: `u128`)
- **interface**: `api.tx.nft.cancelSale`
- **summary**:    Close a sale or auction returning tokens  Requires no successful bids have been made for an auction.  Caller must be the listed seller 
 
### claimUnownedCollection(collection_id: `u32`, new_owner: `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.tx.nft.claimUnownedCollection`
- **summary**:    Bridged collections from Ethereum will initially lack an owner. These collections will  be assigned to the pallet. This allows for claiming those collections assuming they were  assigned to the pallet 
 
### createCollection(name: `Bytes`, initial_issuance: `u32`, max_issuance: `Option<u32>`, token_owner: `Option<SeedPrimitivesSignatureAccountId20>`, metadata_scheme: `Bytes`, royalties_schedule: `Option<SeedPrimitivesNftRoyaltiesSchedule>`, cross_chain_compatibility: `PalletNftCrossChainCompatibility`)
- **interface**: `api.tx.nft.createCollection`
- **summary**:    Create a new collection  Additional tokens can be minted via `mint_additional` 

   `name` - the name of the collection  `initial_issuance` - number of tokens to mint now  `max_issuance` - maximum number of tokens allowed in collection  `token_owner` - the token owner, defaults to the caller  `metadata_scheme` - The off-chain metadata referencing scheme for tokens in this  `royalties_schedule` - defacto royalties plan for secondary sales, this will  apply to all tokens in the collection by default. 
 
### makeSimpleOffer(token_id: `(u32,u32)`, amount: `u128`, asset_id: `u32`, marketplace_id: `Option<u32>`)
- **interface**: `api.tx.nft.makeSimpleOffer`
- **summary**:    Create an offer on a token  Locks funds until offer is accepted, rejected or cancelled  An offer can't be made on a token currently in an auction  (This follows the behaviour of Opensea and forces the buyer to bid rather than create an  offer) 
 
### mint(collection_id: `u32`, quantity: `u32`, token_owner: `Option<SeedPrimitivesSignatureAccountId20>`)
- **interface**: `api.tx.nft.mint`
- **summary**:    Mint tokens for an existing collection 

   `collection_id` - the collection to mint tokens in  `quantity` - how many tokens to mint  `token_owner` - the token owner, defaults to the caller if unspecified  Caller must be the collection owner 

  ----------- Weight is O(N) where N is `quantity` 
 
### registerMarketplace(marketplace_account: `Option<SeedPrimitivesSignatureAccountId20>`, entitlement: `Permill`)
- **interface**: `api.tx.nft.registerMarketplace`
- **summary**:    Flag an account as a marketplace 

   `marketplace_account` - if specified, this account will be registered  `entitlement` - Permill, percentage of sales to go to the marketplace  If no marketplace is specified the caller will be registered 
 
### sell(collection_id: `u32`, serial_numbers: `Vec<u32>`, buyer: `Option<SeedPrimitivesSignatureAccountId20>`, payment_asset: `u32`, fixed_price: `u128`, duration: `Option<u32>`, marketplace_id: `Option<u32>`)
- **interface**: `api.tx.nft.sell`
- **summary**:    Sell a bundle of tokens at a fixed price 

  - Tokens must be from the same collection

  - Tokens with individual royalties schedules cannot be sold with this method

   `buyer` optionally, the account to receive the NFT. If unspecified, then any account may  purchase `asset_id` fungible asset Id to receive as payment for the NFT  `fixed_price` ask price  `duration` listing duration time in blocks from now  Caller must be the token owner 
 
### setBaseUri(collection_id: `u32`, base_uri: `Bytes`)
- **interface**: `api.tx.nft.setBaseUri`
- **summary**:    Set the base URI of a collection  Caller must be the current collection owner 
 
### setMaxIssuance(collection_id: `u32`, max_issuance: `u32`)
- **interface**: `api.tx.nft.setMaxIssuance`
- **summary**:    Set the max issuance of a collection  Caller must be the current collection owner 
 
### setOwner(collection_id: `u32`, new_owner: `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.tx.nft.setOwner`
- **summary**:    Set the owner of a collection  Caller must be the current collection owner 
 
### transfer(collection_id: `u32`, serial_numbers: `Vec<u32>`, new_owner: `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.tx.nft.transfer`
- **summary**:    Transfer ownership of an NFT  Caller must be the token owner 
 
### updateFixedPrice(listing_id: `u128`, new_price: `u128`)
- **interface**: `api.tx.nft.updateFixedPrice`
- **summary**:    Update fixed price for a single token sale 

   `listing_id` id of the fixed price listing  `new_price` new fixed price  Caller must be the token owner 

___


## nftPeg
 
### setContractAddress(contract: `H160`)
- **interface**: `api.tx.nftPeg.setContractAddress`
 
### withdraw(collection_ids: `Vec<u32>`, serial_numbers: `Vec<Vec<u32>>`, destination: `H160`)
- **interface**: `api.tx.nftPeg.withdraw`

___


## proxy
 
### addProxy(delegate: `SeedPrimitivesSignatureAccountId20`, proxy_type: `SeedRuntimeImplsProxyType`, delay: `u32`)
- **interface**: `api.tx.proxy.addProxy`
- **summary**:    Register a proxy account for the sender that is able to make calls on its behalf. 

   The dispatch origin for this call must be _Signed_. 

   Parameters: 

  - `proxy`: The account that the `caller` would like to make a proxy.

  - `proxy_type`: The permissions allowed for this proxy account.

  - `delay`: The announcement period required of the initial proxy. Will generally be zero. 

    
 
### announce(real: `SeedPrimitivesSignatureAccountId20`, call_hash: `H256`)
- **interface**: `api.tx.proxy.announce`
- **summary**:    Publish the hash of a proxy-call that will be made in the future. 

   This must be called some number of blocks before the corresponding `proxy` is attempted  if the delay associated with the proxy relationship is greater than zero. 

   No more than `MaxPending` announcements may be made at any one time. 

   This will take a deposit of `AnnouncementDepositFactor` as well as  `AnnouncementDepositBase` if there are no other pending announcements. 

   The dispatch origin for this call must be _Signed_ and a proxy of `real`. 

   Parameters: 

  - `real`: The account that the proxy will make a call on behalf of.

  - `call_hash`: The hash of the call to be made by the `real` account.

    
 
### anonymous(proxy_type: `SeedRuntimeImplsProxyType`, delay: `u32`, index: `u16`)
- **interface**: `api.tx.proxy.anonymous`
- **summary**:    Spawn a fresh new account that is guaranteed to be otherwise inaccessible, and  initialize it with a proxy of `proxy_type` for `origin` sender. 

   Requires a `Signed` origin. 

   - `proxy_type`: The type of the proxy that the sender will be registered as over the  new account. This will almost always be the most permissive `ProxyType` possible to  allow for maximum flexibility. 

  - `index`: A disambiguation index, in case this is called multiple times in the same transaction (e.g. with `utility::batch`). Unless you're using `batch` you probably just  want to use `0`. 

  - `delay`: The announcement period required of the initial proxy. Will generally be zero. 

   Fails with `Duplicate` if this has already been called in this transaction, from the  same sender, with the same parameters. 

   Fails if there are insufficient funds to pay for deposit. 

     TODO: Might be over counting 1 read 
 
### killAnonymous(spawner: `SeedPrimitivesSignatureAccountId20`, proxy_type: `SeedRuntimeImplsProxyType`, index: `u16`, height: `Compact<u32>`, ext_index: `Compact<u32>`)
- **interface**: `api.tx.proxy.killAnonymous`
- **summary**:    Removes a previously spawned anonymous proxy. 

   WARNING: **All access to this account will be lost.** Any funds held in it will be  inaccessible. 

   Requires a `Signed` origin, and the sender account must have been created by a call to  `anonymous` with corresponding parameters. 

   - `spawner`: The account that originally called `anonymous` to create this account. 

  - `index`: The disambiguation index originally passed to `anonymous`. Probably `0`.

  - `proxy_type`: The proxy type originally passed to `anonymous`.

  - `height`: The height of the chain when the call to `anonymous` was processed.

  - `ext_index`: The extrinsic index in which the call to `anonymous` was processed.

   Fails with `NoPermission` in case the caller is not a previously created anonymous  account whose `anonymous` call has corresponding parameters. 

    
 
### proxy(real: `SeedPrimitivesSignatureAccountId20`, force_proxy_type: `Option<SeedRuntimeImplsProxyType>`, call: `Call`)
- **interface**: `api.tx.proxy.proxy`
- **summary**:    Dispatch the given `call` from an account that the sender is authorised for through  `add_proxy`. 

   Removes any corresponding announcement(s). 

   The dispatch origin for this call must be _Signed_. 

   Parameters: 

  - `real`: The account that the proxy will make a call on behalf of.

  - `force_proxy_type`: Specify the exact proxy type to be used and checked for this call.

  - `call`: The call to be made by the `real` account.

    
 
### proxyAnnounced(delegate: `SeedPrimitivesSignatureAccountId20`, real: `SeedPrimitivesSignatureAccountId20`, force_proxy_type: `Option<SeedRuntimeImplsProxyType>`, call: `Call`)
- **interface**: `api.tx.proxy.proxyAnnounced`
- **summary**:    Dispatch the given `call` from an account that the sender is authorized for through  `add_proxy`. 

   Removes any corresponding announcement(s). 

   The dispatch origin for this call must be _Signed_. 

   Parameters: 

  - `real`: The account that the proxy will make a call on behalf of.

  - `force_proxy_type`: Specify the exact proxy type to be used and checked for this call.

  - `call`: The call to be made by the `real` account.

    
 
### rejectAnnouncement(delegate: `SeedPrimitivesSignatureAccountId20`, call_hash: `H256`)
- **interface**: `api.tx.proxy.rejectAnnouncement`
- **summary**:    Remove the given announcement of a delegate. 

   May be called by a target (proxied) account to remove a call that one of their delegates  (`delegate`) has announced they want to execute. The deposit is returned. 

   The dispatch origin for this call must be _Signed_. 

   Parameters: 

  - `delegate`: The account that previously announced the call.

  - `call_hash`: The hash of the call to be made.

    
 
### removeAnnouncement(real: `SeedPrimitivesSignatureAccountId20`, call_hash: `H256`)
- **interface**: `api.tx.proxy.removeAnnouncement`
- **summary**:    Remove a given announcement. 

   May be called by a proxy account to remove a call they previously announced and return  the deposit. 

   The dispatch origin for this call must be _Signed_. 

   Parameters: 

  - `real`: The account that the proxy will make a call on behalf of.

  - `call_hash`: The hash of the call to be made by the `real` account.

    
 
### removeProxies()
- **interface**: `api.tx.proxy.removeProxies`
- **summary**:    Unregister all proxy accounts for the sender. 

   The dispatch origin for this call must be _Signed_. 

   WARNING: This may be called on accounts created by `anonymous`, however if done, then  the unreserved fees will be inaccessible. **All access to this account will be lost.** 

    
 
### removeProxy(delegate: `SeedPrimitivesSignatureAccountId20`, proxy_type: `SeedRuntimeImplsProxyType`, delay: `u32`)
- **interface**: `api.tx.proxy.removeProxy`
- **summary**:    Unregister a proxy account for the sender. 

   The dispatch origin for this call must be _Signed_. 

   Parameters: 

  - `proxy`: The account that the `caller` would like to remove as a proxy.

  - `proxy_type`: The permissions currently enabled for the removed proxy account.

    

___


## recovery
 
### asRecovered(account: `SeedPrimitivesSignatureAccountId20`, call: `Call`)
- **interface**: `api.tx.recovery.asRecovered`
- **summary**:    Send a call through a recovered account. 

   The dispatch origin for this call must be _Signed_ and registered to  be able to make calls on behalf of the recovered account. 

   Parameters: 

  - `account`: The recovered account you want to make a call on-behalf-of.

  - `call`: The call you want to make with the recovered account.
 
### cancelRecovered(account: `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.tx.recovery.cancelRecovered`
- **summary**:    Cancel the ability to use `as_recovered` for `account`. 

   The dispatch origin for this call must be _Signed_ and registered to  be able to make calls on behalf of the recovered account. 

   Parameters: 

  - `account`: The recovered account you are able to call on-behalf-of.
 
### claimRecovery(account: `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.tx.recovery.claimRecovery`
- **summary**:    Allow a successful rescuer to claim their recovered account. 

   The dispatch origin for this call must be _Signed_ and must be a "rescuer"  who has successfully completed the account recovery process: collected  `threshold` or more vouches, waited `delay_period` blocks since initiation. 

   Parameters: 

  - `account`: The lost account that you want to claim has been successfully recovered by you. 
 
### closeRecovery(rescuer: `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.tx.recovery.closeRecovery`
- **summary**:    As the controller of a recoverable account, close an active recovery  process for your account. 

   Payment: By calling this function, the recoverable account will receive  the recovery deposit `RecoveryDeposit` placed by the rescuer. 

   The dispatch origin for this call must be _Signed_ and must be a  recoverable account with an active recovery process for it. 

   Parameters: 

  - `rescuer`: The account trying to rescue this recoverable account.
 
### createRecovery(friends: `Vec<SeedPrimitivesSignatureAccountId20>`, threshold: `u16`, delay_period: `u32`)
- **interface**: `api.tx.recovery.createRecovery`
- **summary**:    Create a recovery configuration for your account. This makes your account recoverable. 

   Payment: `ConfigDepositBase` + `FriendDepositFactor` * #_of_friends balance  will be reserved for storing the recovery configuration. This deposit is returned  in full when the user calls `remove_recovery`. 

   The dispatch origin for this call must be _Signed_. 

   Parameters: 

  - `friends`: A list of friends you trust to vouch for recovery attempts. Should be ordered and contain no duplicate values. 

  - `threshold`: The number of friends that must vouch for a recovery attempt before the account can be recovered. Should be less than or equal to the length of the list of  friends. 

  - `delay_period`: The number of blocks after a recovery attempt is initialized that needs to pass before the account can be recovered. 
 
### initiateRecovery(account: `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.tx.recovery.initiateRecovery`
- **summary**:    Initiate the process for recovering a recoverable account. 

   Payment: `RecoveryDeposit` balance will be reserved for initiating the  recovery process. This deposit will always be repatriated to the account  trying to be recovered. See `close_recovery`. 

   The dispatch origin for this call must be _Signed_. 

   Parameters: 

  - `account`: The lost account that you want to recover. This account needs to be recoverable (i.e. have a recovery configuration). 
 
### removeRecovery()
- **interface**: `api.tx.recovery.removeRecovery`
- **summary**:    Remove the recovery process for your account. Recovered accounts are still accessible. 

   NOTE: The user must make sure to call `close_recovery` on all active  recovery attempts before calling this function else it will fail. 

   Payment: By calling this function the recoverable account will unreserve  their recovery configuration deposit.  (`ConfigDepositBase` + `FriendDepositFactor` * #_of_friends) 

   The dispatch origin for this call must be _Signed_ and must be a  recoverable account (i.e. has a recovery configuration). 
 
### setRecovered(lost: `SeedPrimitivesSignatureAccountId20`, rescuer: `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.tx.recovery.setRecovered`
- **summary**:    Allow ROOT to bypass the recovery process and set an a rescuer account  for a lost account directly. 

   The dispatch origin for this call must be _ROOT_. 

   Parameters: 

  - `lost`: The "lost account" to be recovered.

  - `rescuer`: The "rescuer account" which can call as the lost account.
 
### vouchRecovery(lost: `SeedPrimitivesSignatureAccountId20`, rescuer: `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.tx.recovery.vouchRecovery`
- **summary**:    Allow a "friend" of a recoverable account to vouch for an active recovery  process for that account. 

   The dispatch origin for this call must be _Signed_ and must be a "friend"  for the recoverable account. 

   Parameters: 

  - `lost`: The lost account that you want to recover.

  - `rescuer`: The account trying to rescue the lost account that you want to vouch for.

   The combination of these two parameters must point to an active recovery  process. 

___


## scheduler
 
### cancel(when: `u32`, index: `u32`)
- **interface**: `api.tx.scheduler.cancel`
- **summary**:    Cancel an anonymously scheduled task. 
 
### cancelNamed(id: `Bytes`)
- **interface**: `api.tx.scheduler.cancelNamed`
- **summary**:    Cancel a named scheduled task. 
 
### schedule(when: `u32`, maybe_periodic: `Option<(u32,u32)>`, priority: `u8`, call: `FrameSupportScheduleMaybeHashed`)
- **interface**: `api.tx.scheduler.schedule`
- **summary**:    Anonymously schedule a task. 
 
### scheduleAfter(after: `u32`, maybe_periodic: `Option<(u32,u32)>`, priority: `u8`, call: `FrameSupportScheduleMaybeHashed`)
- **interface**: `api.tx.scheduler.scheduleAfter`
- **summary**:    Anonymously schedule a task after a delay. 

    
 
### scheduleNamed(id: `Bytes`, when: `u32`, maybe_periodic: `Option<(u32,u32)>`, priority: `u8`, call: `FrameSupportScheduleMaybeHashed`)
- **interface**: `api.tx.scheduler.scheduleNamed`
- **summary**:    Schedule a named task. 
 
### scheduleNamedAfter(id: `Bytes`, after: `u32`, maybe_periodic: `Option<(u32,u32)>`, priority: `u8`, call: `FrameSupportScheduleMaybeHashed`)
- **interface**: `api.tx.scheduler.scheduleNamedAfter`
- **summary**:    Schedule a named task after a delay. 

    

___


## session
 
### purgeKeys()
- **interface**: `api.tx.session.purgeKeys`
- **summary**:    Removes any session key(s) of the function caller. 

   This doesn't take effect until the next session. 

   The dispatch origin of this function must be Signed and the account must be either be  convertible to a validator ID using the chain's typical addressing system (this usually  means being a controller account) or directly convertible into a validator ID (which  usually means being a stash account). 

    
 
### setKeys(keys: `SeedRuntimeSessionKeys`, proof: `Bytes`)
- **interface**: `api.tx.session.setKeys`
- **summary**:    Sets the session key(s) of the function caller to `keys`.  Allows an account to set its session key prior to becoming a validator.  This doesn't take effect until the next session. 

   The dispatch origin of this function must be signed. 

    

___


## sft
 
### burn(collection_id: `u32`, serial_numbers: `Vec<(u32,u128)>`)
- **interface**: `api.tx.sft.burn`
- **summary**:    Burn a token 🔥 

   Caller must be the token owner 
 
### createCollection(collection_name: `Bytes`, collection_owner: `Option<SeedPrimitivesSignatureAccountId20>`, metadata_scheme: `Bytes`, royalties_schedule: `Option<SeedPrimitivesNftRoyaltiesSchedule>`)
- **interface**: `api.tx.sft.createCollection`
- **summary**:    Create a new collection to group multiple semi-fungible tokens  Tokens can be created within the collection by calling create_token 

   `collection_name` - the name of the collection  `collection_owner` - the collection owner, defaults to the caller  `metadata_scheme` - The off-chain metadata referencing scheme for tokens in this  `royalties_schedule` - defacto royalties plan for secondary sales, this will  apply to all tokens in the collection by default. 

   The collectionUuid used to store the SFT CollectionInfo is retrieved from the NFT  pallet. This is so that CollectionUuids are unique across all collections, regardless  of if they are SFT or NFT collections. 
 
### createToken(collection_id: `u32`, token_name: `Bytes`, initial_issuance: `u128`, max_issuance: `Option<u128>`, token_owner: `Option<SeedPrimitivesSignatureAccountId20>`)
- **interface**: `api.tx.sft.createToken`
- **summary**:    Create additional tokens for an existing collection  These tokens act similar to tokens within an ERC1155 contract  Each token has individual issuance, max_issuance, 
 
### mint(collection_id: `u32`, serial_numbers: `Vec<(u32,u128)>`, token_owner: `Option<SeedPrimitivesSignatureAccountId20>`)
- **interface**: `api.tx.sft.mint`
- **summary**:    Mints some balances into some serial numbers for an account  This acts as a batch mint function and allows for multiple serial numbers and quantities  to be passed in simultaneously.  Must be called by the collection owner 

   `collection_id` - the SFT collection to mint into  `serial_numbers` - A list of serial numbers to mint into  `quantities` - A list of quantities to mint into each serial number  `token_owner` - The owner of the tokens, defaults to the caller 
 
### setBaseUri(collection_id: `u32`, metadata_scheme: `Bytes`)
- **interface**: `api.tx.sft.setBaseUri`
- **summary**:    Set the base URI of a collection (MetadataScheme)  Caller must be the current collection owner 
 
### setMaxIssuance(token_id: `(u32,u32)`, max_issuance: `u128`)
- **interface**: `api.tx.sft.setMaxIssuance`
- **summary**:    Set the max issuance of a collection  Caller must be the current collection owner 
 
### setOwner(collection_id: `u32`, new_owner: `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.tx.sft.setOwner`
- **summary**:    Set the owner of a collection  Caller must be the current collection owner 
 
### transfer(collection_id: `u32`, serial_numbers: `Vec<(u32,u128)>`, new_owner: `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.tx.sft.transfer`
- **summary**:    Transfer ownership of an SFT  Caller must be the token owner 

___


## staking
 
### bond(controller: `SeedPrimitivesSignatureAccountId20`, value: `Compact<u128>`, payee: `PalletStakingRewardDestination`)
- **interface**: `api.tx.staking.bond`
- **summary**:    Take the origin account as a stash and lock up `value` of its balance. `controller` will  be the account that controls it. 

   `value` must be more than the `minimum_balance` specified by `T::Currency`. 

   The dispatch origin for this call must be _Signed_ by the stash account. 

   Emits `Bonded`.   
 
### bondExtra(max_additional: `Compact<u128>`)
- **interface**: `api.tx.staking.bondExtra`
- **summary**:    Add some extra amount that have appeared in the stash `free_balance` into the balance up  for staking. 

   The dispatch origin for this call must be _Signed_ by the stash, not the controller. 

   Use this if there are additional funds in your stash account that you wish to bond.  Unlike [`bond`](Self::bond) or [`unbond`](Self::unbond) this function does not impose  any limitation on the amount that can be added. 

   Emits `Bonded`. 

    
 
### cancelDeferredSlash(era: `u32`, slash_indices: `Vec<u32>`)
- **interface**: `api.tx.staking.cancelDeferredSlash`
- **summary**:    Cancel enactment of a deferred slash. 

   Can be called by the `T::SlashCancelOrigin`. 

   Parameters: era and indices of the slashes for that era to kill. 
 
### chill()
- **interface**: `api.tx.staking.chill`
- **summary**:    Declare no desire to either validate or nominate. 

   Effects will be felt at the beginning of the next era. 

   The dispatch origin for this call must be _Signed_ by the controller, not the stash. 

    
 
### chillOther(controller: `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.tx.staking.chillOther`
- **summary**:    Declare a `controller` to stop participating as either a validator or nominator. 

   Effects will be felt at the beginning of the next era. 

   The dispatch origin for this call must be _Signed_, but can be called by anyone. 

   If the caller is the same as the controller being targeted, then no further checks are  enforced, and this function behaves just like `chill`. 

   If the caller is different than the controller being targeted, the following conditions  must be met: 

   * `controller` must belong to a nominator who has become non-decodable, 

   Or: 

   * A `ChillThreshold` must be set and checked which defines how close to the max  nominators or validators we must reach before users can start chilling one-another. 

  * A `MaxNominatorCount` and `MaxValidatorCount` must be set which is used to determine how close we are to the threshold. 

  * A `MinNominatorBond` and `MinValidatorBond` must be set and checked, which determines if this is a person that should be chilled because they have not met the threshold  bond required. 

   This can be helpful if bond requirements are updated, and we need to remove old users  who do not satisfy these requirements. 
 
### forceApplyMinCommission(validator_stash: `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.tx.staking.forceApplyMinCommission`
- **summary**:    Force a validator to have at least the minimum commission. This will not affect a  validator who already has a commission greater than or equal to the minimum. Any account  can call this. 
 
### forceNewEra()
- **interface**: `api.tx.staking.forceNewEra`
- **summary**:    Force there to be a new era at the end of the next session. After this, it will be  reset to normal (non-forced) behaviour. 

   The dispatch origin must be Root. 

   #### Warning 

   The election process starts multiple blocks before the end of the era.  If this is called just before a new era is triggered, the election process may not  have enough blocks to get a result. 

    
 
### forceNewEraAlways()
- **interface**: `api.tx.staking.forceNewEraAlways`
- **summary**:    Force there to be a new era at the end of sessions indefinitely. 

   The dispatch origin must be Root. 

   #### Warning 

   The election process starts multiple blocks before the end of the era.  If this is called just before a new era is triggered, the election process may not  have enough blocks to get a result. 
 
### forceNoEras()
- **interface**: `api.tx.staking.forceNoEras`
- **summary**:    Force there to be no new eras indefinitely. 

   The dispatch origin must be Root. 

   #### Warning 

   The election process starts multiple blocks before the end of the era.  Thus the election process may be ongoing when this is called. In this case the  election will continue until the next era is triggered. 

    
 
### forceUnstake(stash: `SeedPrimitivesSignatureAccountId20`, num_slashing_spans: `u32`)
- **interface**: `api.tx.staking.forceUnstake`
- **summary**:    Force a current staker to become completely unstaked, immediately. 

   The dispatch origin must be Root. 
 
### increaseValidatorCount(additional: `Compact<u32>`)
- **interface**: `api.tx.staking.increaseValidatorCount`
- **summary**:    Increments the ideal number of validators. 

   The dispatch origin must be Root. 

    
 
### kick(who: `Vec<SeedPrimitivesSignatureAccountId20>`)
- **interface**: `api.tx.staking.kick`
- **summary**:    Remove the given nominations from the calling validator. 

   Effects will be felt at the beginning of the next era. 

   The dispatch origin for this call must be _Signed_ by the controller, not the stash. 

   - `who`: A list of nominator stash accounts who are nominating this validator which  should no longer be nominating this validator. 

   Note: Making this call only makes sense if you first set the validator preferences to  block any further nominations. 
 
### nominate(targets: `Vec<SeedPrimitivesSignatureAccountId20>`)
- **interface**: `api.tx.staking.nominate`
- **summary**:    Declare the desire to nominate `targets` for the origin controller. 

   Effects will be felt at the beginning of the next era. 

   The dispatch origin for this call must be _Signed_ by the controller, not the stash. 

    
 
### payoutStakers(validator_stash: `SeedPrimitivesSignatureAccountId20`, era: `u32`)
- **interface**: `api.tx.staking.payoutStakers`
- **summary**:    Pay out all the stakers behind a single validator for a single era. 

   - `validator_stash` is the stash account of the validator. Their nominators, up to  `T::MaxNominatorRewardedPerValidator`, will also receive their rewards. 

  - `era` may be any era between `[current_era - history_depth; current_era]`.

   The origin of this call must be _Signed_. Any account can call this function, even if  it is not one of the stakers. 

    
 
### reapStash(stash: `SeedPrimitivesSignatureAccountId20`, num_slashing_spans: `u32`)
- **interface**: `api.tx.staking.reapStash`
- **summary**:    Remove all data structures concerning a staker/stash once it is at a state where it can  be considered `dust` in the staking system. The requirements are: 

   1. the `total_balance` of the stash is below existential deposit.  2. or, the `ledger.total` of the stash is below existential deposit. 

   The former can happen in cases like a slash; the latter when a fully unbonded account  is still receiving staking rewards in `RewardDestination::Staked`. 

   It can be called by anyone, as long as `stash` meets the above requirements. 

   Refunds the transaction fees upon successful execution. 
 
### rebond(value: `Compact<u128>`)
- **interface**: `api.tx.staking.rebond`
- **summary**:    Rebond a portion of the stash scheduled to be unlocked. 

   The dispatch origin must be signed by the controller. 

    
 
### scaleValidatorCount(factor: `Percent`)
- **interface**: `api.tx.staking.scaleValidatorCount`
- **summary**:    Scale up the ideal number of validators by a factor. 

   The dispatch origin must be Root. 

    
 
### setController(controller: `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.tx.staking.setController`
- **summary**:    (Re-)set the controller of a stash. 

   Effects will be felt instantly (as soon as this function is completed successfully). 

   The dispatch origin for this call must be _Signed_ by the stash, not the controller. 

    
 
### setHistoryDepth(new_history_depth: `Compact<u32>`, era_items_deleted: `Compact<u32>`)
- **interface**: `api.tx.staking.setHistoryDepth`
- **summary**:    Set `HistoryDepth` value. This function will delete any history information  when `HistoryDepth` is reduced. 

   Parameters: 

  - `new_history_depth`: The new history depth you would like to set.

  - `era_items_deleted`: The number of items that will be deleted by this dispatch. This should report all the storage items that will be deleted by clearing old era history.  Needed to report an accurate weight for the dispatch. Trusted by `Root` to report an  accurate number. 

   Origin must be root. 

    
 
### setInvulnerables(invulnerables: `Vec<SeedPrimitivesSignatureAccountId20>`)
- **interface**: `api.tx.staking.setInvulnerables`
- **summary**:    Set the validators who cannot be slashed (if any). 

   The dispatch origin must be Root. 
 
### setPayee(payee: `PalletStakingRewardDestination`)
- **interface**: `api.tx.staking.setPayee`
- **summary**:    (Re-)set the payment target for a controller. 

   Effects will be felt instantly (as soon as this function is completed successfully). 

   The dispatch origin for this call must be _Signed_ by the controller, not the stash. 

    
 
### setStakingConfigs(min_nominator_bond: `PalletStakingPalletConfigOpU128`, min_validator_bond: `PalletStakingPalletConfigOpU128`, max_nominator_count: `PalletStakingPalletConfigOpU32`, max_validator_count: `PalletStakingPalletConfigOpU32`, chill_threshold: `PalletStakingPalletConfigOpPercent`, min_commission: `PalletStakingPalletConfigOpPerbill`)
- **interface**: `api.tx.staking.setStakingConfigs`
- **summary**:    Update the various staking configurations . 

   * `min_nominator_bond`: The minimum active bond needed to be a nominator. 

  * `min_validator_bond`: The minimum active bond needed to be a validator.

  * `max_nominator_count`: The max number of users who can be a nominator at once. When set to `None`, no limit is enforced. 

  * `max_validator_count`: The max number of users who can be a validator at once. When set to `None`, no limit is enforced. 

  * `chill_threshold`: The ratio of `max_nominator_count` or `max_validator_count` which should be filled in order for the `chill_other` transaction to work. 

  * `min_commission`: The minimum amount of commission that each validators must maintain. This is checked only upon calling `validate`. Existing validators are not affected. 

   Origin must be Root to call this function. 

   NOTE: Existing nominators and validators will not be affected by this update.  to kick people under the new limits, `chill_other` should be called. 
 
### setValidatorCount(new: `Compact<u32>`)
- **interface**: `api.tx.staking.setValidatorCount`
- **summary**:    Sets the ideal number of validators. 

   The dispatch origin must be Root. 

    
 
### unbond(value: `Compact<u128>`)
- **interface**: `api.tx.staking.unbond`
- **summary**:    Schedule a portion of the stash to be unlocked ready for transfer out after the bond  period ends. If this leaves an amount actively bonded less than  T::Currency::minimum_balance(), then it is increased to the full amount. 

   The dispatch origin for this call must be _Signed_ by the controller, not the stash. 

   Once the unlock period is done, you can call `withdraw_unbonded` to actually move  the funds out of management ready for transfer. 

   No more than a limited number of unlocking chunks (see `MaxUnlockingChunks`)  can co-exists at the same time. In that case, [`Call::withdraw_unbonded`] need  to be called first to remove some of the chunks (if possible). 

   If a user encounters the `InsufficientBond` error when calling this extrinsic,  they should call `chill` first in order to free up their bonded funds. 

   Emits `Unbonded`. 

   See also [`Call::withdraw_unbonded`]. 
 
### validate(prefs: `PalletStakingValidatorPrefs`)
- **interface**: `api.tx.staking.validate`
- **summary**:    Declare the desire to validate for the origin controller. 

   Effects will be felt at the beginning of the next era. 

   The dispatch origin for this call must be _Signed_ by the controller, not the stash. 
 
### withdrawUnbonded(num_slashing_spans: `u32`)
- **interface**: `api.tx.staking.withdrawUnbonded`
- **summary**:    Remove any unlocked chunks from the `unlocking` queue from our management. 

   This essentially frees up that balance to be used by the stash account to do  whatever it wants. 

   The dispatch origin for this call must be _Signed_ by the controller. 

   Emits `Withdrawn`. 

   See also [`Call::unbond`]. 

    

___


## sudo
 
### setKey(new: `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.tx.sudo.setKey`
- **summary**:    Authenticates the current sudo key and sets the given AccountId (`new`) as the new sudo  key. 

   The dispatch origin for this call must be _Signed_. 

    
 
### sudo(call: `Call`)
- **interface**: `api.tx.sudo.sudo`
- **summary**:    Authenticates the sudo key and dispatches a function call with `Root` origin. 

   The dispatch origin for this call must be _Signed_. 

    
 
### sudoAs(who: `SeedPrimitivesSignatureAccountId20`, call: `Call`)
- **interface**: `api.tx.sudo.sudoAs`
- **summary**:    Authenticates the sudo key and dispatches a function call with `Signed` origin from  a given account. 

   The dispatch origin for this call must be _Signed_. 

    
 
### sudoUncheckedWeight(call: `Call`, weight: `u64`)
- **interface**: `api.tx.sudo.sudoUncheckedWeight`
- **summary**:    Authenticates the sudo key and dispatches a function call with `Root` origin.  This function does not check the weight of the call, and instead allows the  Sudo user to specify the weight of the call. 

   The dispatch origin for this call must be _Signed_. 

    

___


## system
 
### fillBlock(ratio: `Perbill`)
- **interface**: `api.tx.system.fillBlock`
- **summary**:    A dispatch that will fill the block weight up to the given ratio. 
 
### killPrefix(prefix: `Bytes`, subkeys: `u32`)
- **interface**: `api.tx.system.killPrefix`
- **summary**:    Kill all storage items with a key that starts with the given prefix. 

   **NOTE:** We rely on the Root origin to provide us the number of subkeys under  the prefix we are removing to accurately calculate the weight of this function. 
 
### killStorage(keys: `Vec<Bytes>`)
- **interface**: `api.tx.system.killStorage`
- **summary**:    Kill some items from storage. 
 
### remark(remark: `Bytes`)
- **interface**: `api.tx.system.remark`
- **summary**:    Make some on-chain remark. 

    
 
### remarkWithEvent(remark: `Bytes`)
- **interface**: `api.tx.system.remarkWithEvent`
- **summary**:    Make some on-chain remark and emit event. 
 
### setCode(code: `Bytes`)
- **interface**: `api.tx.system.setCode`
- **summary**:    Set the new runtime code. 

    
 
### setCodeWithoutChecks(code: `Bytes`)
- **interface**: `api.tx.system.setCodeWithoutChecks`
- **summary**:    Set the new runtime code without doing any checks of the given `code`. 

    
 
### setHeapPages(pages: `u64`)
- **interface**: `api.tx.system.setHeapPages`
- **summary**:    Set the number of pages in the WebAssembly environment's heap. 
 
### setStorage(items: `Vec<(Bytes,Bytes)>`)
- **interface**: `api.tx.system.setStorage`
- **summary**:    Set some items of storage. 

___


## timestamp
 
### set(now: `Compact<u64>`)
- **interface**: `api.tx.timestamp.set`
- **summary**:    Set the current time. 

   This call should be invoked exactly once per block. It will panic at the finalization  phase, if this call hasn't been invoked by that time. 

   The timestamp should be greater than the previous one by the amount specified by  `MinimumPeriod`. 

   The dispatch origin for this call must be `Inherent`. 

    

___


## tokenApprovals
 
### erc20Approval(caller: `SeedPrimitivesSignatureAccountId20`, spender: `SeedPrimitivesSignatureAccountId20`, asset_id: `u32`, amount: `u128`)
- **interface**: `api.tx.tokenApprovals.erc20Approval`
- **summary**:    Set approval for an account to transfer an amount of tokens on behalf of the caller  Mapping from caller to spender and amount  mapping(address => mapping(address => uint256)) private _allowances; 
 
### erc20UpdateApproval(caller: `SeedPrimitivesSignatureAccountId20`, spender: `SeedPrimitivesSignatureAccountId20`, asset_id: `u32`, amount: `u128`)
- **interface**: `api.tx.tokenApprovals.erc20UpdateApproval`
- **summary**:    Removes an approval over an account and asset_id  mapping(address => mapping(address => uint256)) private _allowances; 
 
### erc721Approval(caller: `SeedPrimitivesSignatureAccountId20`, operator_account: `SeedPrimitivesSignatureAccountId20`, token_id: `(u32,u32)`)
- **interface**: `api.tx.tokenApprovals.erc721Approval`
- **summary**:    Set approval for a single NFT  Mapping from token_id to operator  clears approval on transfer  mapping(uint256 => address) private _tokenApprovals; 
 
### erc721ApprovalForAll(caller: `SeedPrimitivesSignatureAccountId20`, operator_account: `SeedPrimitivesSignatureAccountId20`, collection_uuid: `u32`, approved: `bool`)
- **interface**: `api.tx.tokenApprovals.erc721ApprovalForAll`
- **summary**:    Set approval for an account (or contract) to transfer any tokens from a collection  mapping(address => mapping(address => bool)) private _operatorApprovals; 
 
### erc721RemoveApproval(token_id: `(u32,u32)`)
- **interface**: `api.tx.tokenApprovals.erc721RemoveApproval`
- **summary**:    Public method which allows users to remove approvals on a token they own 

___


## utility
 
### asDerivative(index: `u16`, call: `Call`)
- **interface**: `api.tx.utility.asDerivative`
- **summary**:    Send a call through an indexed pseudonym of the sender. 

   Filter from origin are passed along. The call will be dispatched with an origin which  use the same filter as the origin of this call. 

   NOTE: If you need to ensure that any account-based filtering is not honored (i.e.  because you expect `proxy` to have been used prior in the call stack and you do not want  the call restrictions to apply to any sub-accounts), then use `as_multi_threshold_1`  in the Multisig pallet instead. 

   NOTE: Prior to version *12, this was called `as_limited_sub`. 

   The dispatch origin for this call must be _Signed_. 
 
### batch(calls: `Vec<Call>`)
- **interface**: `api.tx.utility.batch`
- **summary**:    Send a batch of dispatch calls. 

   May be called from any origin. 

   - `calls`: The calls to be dispatched from the same origin. The number of call must not  exceed the constant: `batched_calls_limit` (available in constant metadata). 

   If origin is root then call are dispatch without checking origin filter. (This includes  bypassing `frame_system::Config::BaseCallFilter`). 

    

   This will return `Ok` in all circumstances. To determine the success of the batch, an  event is deposited. If a call failed and the batch was interrupted, then the  `BatchInterrupted` event is deposited, along with the number of successful calls made  and the error of the failed call. If all were successful, then the `BatchCompleted`  event is deposited. 
 
### batchAll(calls: `Vec<Call>`)
- **interface**: `api.tx.utility.batchAll`
- **summary**:    Send a batch of dispatch calls and atomically execute them.  The whole transaction will rollback and fail if any of the calls failed. 

   May be called from any origin. 

   - `calls`: The calls to be dispatched from the same origin. The number of call must not  exceed the constant: `batched_calls_limit` (available in constant metadata). 

   If origin is root then call are dispatch without checking origin filter. (This includes  bypassing `frame_system::Config::BaseCallFilter`). 

    
 
### dispatchAs(as_origin: `SeedRuntimeOriginCaller`, call: `Call`)
- **interface**: `api.tx.utility.dispatchAs`
- **summary**:    Dispatches a function call with a provided origin. 

   The dispatch origin for this call must be _Root_. 

    
 
### forceBatch(calls: `Vec<Call>`)
- **interface**: `api.tx.utility.forceBatch`
- **summary**:    Send a batch of dispatch calls.  Unlike `batch`, it allows errors and won't interrupt. 

   May be called from any origin. 

   - `calls`: The calls to be dispatched from the same origin. The number of call must not  exceed the constant: `batched_calls_limit` (available in constant metadata). 

   If origin is root then call are dispatch without checking origin filter. (This includes  bypassing `frame_system::Config::BaseCallFilter`). 

    

___


## voterList
 
### putInFrontOf(lighter: `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.tx.voterList.putInFrontOf`
- **summary**:    Move the caller's Id directly in front of `lighter`. 

   The dispatch origin for this call must be _Signed_ and can only be called by the Id of  the account going in front of `lighter`. 

   Only works if 

  - both nodes are within the same bag,

  - and `origin` has a greater `Score` than `lighter`.
 
### rebag(dislocated: `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.tx.voterList.rebag`
- **summary**:    Declare that some `dislocated` account has, through rewards or penalties, sufficiently  changed its score that it should properly fall into a different bag than its current  one. 

   Anyone can call this function about any potentially dislocated account. 

   Will always update the stored score of `dislocated` to the correct score, based on  `ScoreProvider`. 

   If `dislocated` does not exists, it returns an error. 

___


## xls20
 
### enableXls20Compatibility(collection_id: `u32`)
- **interface**: `api.tx.xls20.enableXls20Compatibility`
- **summary**:    Enables XLS-20 compatibility on a collection 

  - Collection must not have any tokens minted

  - Caller must be collection owner
 
### fulfillXls20Mint(collection_id: `u32`, token_mappings: `Vec<(u32,[u8;64])>`)
- **interface**: `api.tx.xls20.fulfillXls20Mint`
- **summary**:    Submit XLS-20 token ids to The Root Network  Only callable by the trusted relayer account  Can apply multiple mappings from the same collection in one transaction 
 
### reRequestXls20Mint(collection_id: `u32`, serial_numbers: `Vec<u32>`)
- **interface**: `api.tx.xls20.reRequestXls20Mint`
 
### setRelayer(relayer: `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.tx.xls20.setRelayer`
- **summary**:    Set the relayer address 
 
### setXls20Fee(new_fee: `u128`)
- **interface**: `api.tx.xls20.setXls20Fee`
- **summary**:    Set the xls20 mint fee which is paid per token by the collection owner  This covers the additional costs incurred by the relayer for the following: 

  - Minting the token on XRPL

  - Calling fulfill_xls20_mint on The Root Network

___


## xrplBridge
 
### addRelayer(relayer: `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.tx.xrplBridge.addRelayer`
- **summary**:    add a relayer 
 
### removeRelayer(relayer: `SeedPrimitivesSignatureAccountId20`)
- **interface**: `api.tx.xrplBridge.removeRelayer`
- **summary**:    remove a relayer 
 
### setDoorAddress(door_address: `H160`)
- **interface**: `api.tx.xrplBridge.setDoorAddress`
- **summary**:    Set XRPL door address managed by this pallet 
 
### setDoorTxFee(fee: `u64`)
- **interface**: `api.tx.xrplBridge.setDoorTxFee`
- **summary**:    Set the door tx fee amount 
 
### setTicketSequenceCurrentAllocation(ticket_sequence: `u32`, start_ticket_sequence: `u32`, ticket_bucket_size: `u32`)
- **interface**: `api.tx.xrplBridge.setTicketSequenceCurrentAllocation`
- **summary**:    Set the door account current ticket sequence params for current allocation - force set 
 
### setTicketSequenceNextAllocation(start_ticket_sequence: `u32`, ticket_bucket_size: `u32`)
- **interface**: `api.tx.xrplBridge.setTicketSequenceNextAllocation`
- **summary**:    Set the door account ticket sequence params for the next allocation 
 
### submitChallenge(transaction_hash: `H512`)
- **interface**: `api.tx.xrplBridge.submitChallenge`
- **summary**:    Submit xrp transaction challenge 
 
### submitTransaction(ledger_index: `u64`, transaction_hash: `H512`, transaction: `PalletXrplBridgeHelpersXrplTxData`, timestamp: `u64`)
- **interface**: `api.tx.xrplBridge.submitTransaction`
- **summary**:    Submit xrp transaction 
 
### withdrawXrp(amount: `u128`, destination: `H160`)
- **interface**: `api.tx.xrplBridge.withdrawXrp`
- **summary**:    Withdraw xrp transaction 
