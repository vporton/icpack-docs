# MockCMC
Mock `CMC.notify_create_canister` implementation using `IC.create_canister` (for testing).
IT DOES NOT CONFORM TO THE SPECS!
It's useful for testing code using `CMC.notify_create_canister` on local net.

## Type `AccountIdentifier`
``` motoko no-repl
type AccountIdentifier = Text
```


## Type `BlockIndex`
``` motoko no-repl
type BlockIndex = Nat64
```


## Type `CanisterSettings`
``` motoko no-repl
type CanisterSettings = { freezing_threshold : ?Nat; wasm_memory_threshold : ?Nat; controllers : ?[Principal]; reserved_cycles_limit : ?Nat; log_visibility : ?log_visibility; wasm_memory_limit : ?Nat; memory_allocation : ?Nat; compute_allocation : ?Nat }
```


## Type `CreateCanisterArg`
``` motoko no-repl
type CreateCanisterArg = { subnet_selection : ?SubnetSelection; settings : ?CanisterSettings; subnet_type : ?Text }
```


## Type `CreateCanisterError`
``` motoko no-repl
type CreateCanisterError = {#Refunded : { create_error : Text; refund_amount : Nat }}
```


## Type `CreateCanisterResult`
``` motoko no-repl
type CreateCanisterResult = {#Ok : Principal; #Err : CreateCanisterError}
```


## Type `Cycles`
``` motoko no-repl
type Cycles = Nat
```


## Type `CyclesCanisterInitPayload`
``` motoko no-repl
type CyclesCanisterInitPayload = { exchange_rate_canister : ?ExchangeRateCanister; cycles_ledger_canister_id : ?Principal; last_purged_notification : ?Nat64; governance_canister_id : ?Principal; minting_account_id : ?AccountIdentifier; ledger_canister_id : ?Principal }
```


## Type `ExchangeRateCanister`
``` motoko no-repl
type ExchangeRateCanister = {#Set : Principal; #Unset}
```


## Type `IcpXdrConversionRate`
``` motoko no-repl
type IcpXdrConversionRate = { xdr_permyriad_per_icp : Nat64; timestamp_seconds : Nat64 }
```


## Type `IcpXdrConversionRateResponse`
``` motoko no-repl
type IcpXdrConversionRateResponse = { certificate : Blob; data : IcpXdrConversionRate; hash_tree : Blob }
```


## Type `Memo`
``` motoko no-repl
type Memo = ?Blob
```


## Type `NotifyCreateCanisterArg`
``` motoko no-repl
type NotifyCreateCanisterArg = { controller : Principal; block_index : BlockIndex; subnet_selection : ?SubnetSelection; settings : ?CanisterSettings; subnet_type : ?Text }
```


## Type `NotifyCreateCanisterResult`
``` motoko no-repl
type NotifyCreateCanisterResult = {#Ok : Principal; #Err : NotifyError}
```


## Type `NotifyError`
``` motoko no-repl
type NotifyError = {#Refunded : { block_index : ?BlockIndex; reason : Text }; #InvalidTransaction : Text; #Other : { error_message : Text; error_code : Nat64 }; #Processing; #TransactionTooOld : BlockIndex}
```


## Type `NotifyMintCyclesArg`
``` motoko no-repl
type NotifyMintCyclesArg = { block_index : BlockIndex; deposit_memo : Memo; to_subaccount : Subaccount }
```


## Type `NotifyMintCyclesResult`
``` motoko no-repl
type NotifyMintCyclesResult = {#Ok : NotifyMintCyclesSuccess; #Err : NotifyError}
```


## Type `NotifyMintCyclesSuccess`
``` motoko no-repl
type NotifyMintCyclesSuccess = { balance : Nat; block_index : Nat; minted : Nat }
```


## Type `NotifyTopUpArg`
``` motoko no-repl
type NotifyTopUpArg = { block_index : BlockIndex; canister_id : Principal }
```


## Type `NotifyTopUpResult`
``` motoko no-repl
type NotifyTopUpResult = {#Ok : Cycles; #Err : NotifyError}
```


## Type `PrincipalsAuthorizedToCreateCanistersToSubnetsResponse`
``` motoko no-repl
type PrincipalsAuthorizedToCreateCanistersToSubnetsResponse = { data : [(Principal, [Principal])] }
```


## Type `Subaccount`
``` motoko no-repl
type Subaccount = ?Blob
```


## Type `SubnetFilter`
``` motoko no-repl
type SubnetFilter = { subnet_type : ?Text }
```


## Type `SubnetSelection`
``` motoko no-repl
type SubnetSelection = {#Filter : SubnetFilter; #Subnet : { subnet : Principal }}
```


## Type `SubnetTypesToSubnetsResponse`
``` motoko no-repl
type SubnetTypesToSubnetsResponse = { data : [(Text, [Principal])] }
```


## Type `log_visibility`
``` motoko no-repl
type log_visibility = {#controllers; #public_}
```


## Function `create_canister`
``` motoko no-repl
func create_canister(arg : CreateCanisterArg) : async CreateCanisterResult
```

