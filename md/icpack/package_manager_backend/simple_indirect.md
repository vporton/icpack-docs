# package_manager_backend/simple_indirect

## Actor Class `SimpleIndirect`

``` motoko no-repl
class SimpleIndirect()
```


### Function `init`
``` motoko no-repl
func init() : async ()
```



### Function `b44c4a9beec74e1c8a7acbe46256f92f_isInitialized`
``` motoko no-repl
func b44c4a9beec74e1c8a7acbe46256f92f_isInitialized() : async ()
```



### Function `getOwners`
``` motoko no-repl
func getOwners() : async [Principal]
```



### Function `setOwners`
``` motoko no-repl
func setOwners(newOwners : [Principal]) : async ()
```



### Function `addOwner`
``` motoko no-repl
func addOwner(newOwner : Principal) : async ()
```



### Function `removeOwner`
``` motoko no-repl
func removeOwner(oldOwner : Principal) : async ()
```



### Type `OnError`
``` motoko no-repl
type OnError = {#abort; #keepDoing}
```



### Function `callAll`
``` motoko no-repl
func callAll(methods : [{ canister : Principal; name : Text; data : Blob; error : OnError }]) : async ()
```



### Function `canister_info`
``` motoko no-repl
func canister_info(args : IC.CanisterInfoArgs, amount : Nat) : async IC.CanisterInfoResult
```



### Function `canister_status`
``` motoko no-repl
func canister_status(args : IC.CanisterStatusArgs, amount : Nat) : async IC.CanisterStatusResult
```



### Function `clear_chunk_store`
``` motoko no-repl
func clear_chunk_store(args : IC.ClearChunkStoreArgs, amount : Nat) : async ()
```



### Function `create_canister`
``` motoko no-repl
func create_canister(args : IC.CreateCanisterArgs, amount : Nat) : async IC.CreateCanisterResult
```



### Function `delete_canister`
``` motoko no-repl
func delete_canister(args : IC.DeleteCanisterArgs, amount : Nat) : async ()
```



### Function `delete_canister_snapshot`
``` motoko no-repl
func delete_canister_snapshot(args : IC.DeleteCanisterSnapshotArgs, amount : Nat) : async ()
```



### Function `deposit_cycles`
``` motoko no-repl
func deposit_cycles(args : IC.DepositCyclesArgs, amount : Nat) : async ()
```



### Function `ecdsa_public_key`
``` motoko no-repl
func ecdsa_public_key(args : IC.EcdsaPublicKeyArgs, amount : Nat) : async IC.EcdsaPublicKeyResult
```



### Function `fetch_canister_logs`
``` motoko no-repl
func fetch_canister_logs(args : IC.FetchCanisterLogsArgs) : async IC.FetchCanisterLogsResult
```



### Function `http_request`
``` motoko no-repl
func http_request(args : IC.HttpRequestArgs, amount : Nat) : async IC.HttpRequestResult
```



### Function `install_chunked_code`
``` motoko no-repl
func install_chunked_code(args : IC.InstallChunkedCodeArgs, amount : Nat) : async ()
```



### Function `install_code`
``` motoko no-repl
func install_code(args : IC.InstallCodeArgs, amount : Nat) : async ()
```



### Function `list_canister_snapshots`
``` motoko no-repl
func list_canister_snapshots(args : IC.ListCanisterSnapshotsArgs, amount : Nat) : async IC.ListCanisterSnapshotsResult
```



### Function `load_canister_snapshot`
``` motoko no-repl
func load_canister_snapshot(args : IC.LoadCanisterSnapshotArgs, amount : Nat) : async ()
```



### Function `node_metrics_history`
``` motoko no-repl
func node_metrics_history(args : IC.NodeMetricsHistoryArgs, amount : Nat) : async IC.NodeMetricsHistoryResult
```



### Function `provisional_create_canister_with_cycles`
``` motoko no-repl
func provisional_create_canister_with_cycles(args : IC.ProvisionalCreateCanisterWithCyclesArgs, amount : Nat) : async IC.ProvisionalCreateCanisterWithCyclesResult
```



### Function `provisional_top_up_canister`
``` motoko no-repl
func provisional_top_up_canister(args : IC.ProvisionalTopUpCanisterArgs, amount : Nat) : async ()
```



### Function `raw_rand`
``` motoko no-repl
func raw_rand(amount : Nat) : async IC.RawRandResult
```



### Function `schnorr_public_key`
``` motoko no-repl
func schnorr_public_key(args : IC.SchnorrPublicKeyArgs, amount : Nat) : async IC.SchnorrPublicKeyResult
```



### Function `sign_with_ecdsa`
``` motoko no-repl
func sign_with_ecdsa(args : IC.SignWithEcdsaArgs, amount : Nat) : async IC.SignWithEcdsaResult
```



### Function `sign_with_schnorr`
``` motoko no-repl
func sign_with_schnorr(args : IC.SignWithSchnorrArgs, amount : Nat) : async IC.SignWithSchnorrResult
```



### Function `start_canister`
``` motoko no-repl
func start_canister(args : IC.StartCanisterArgs, amount : Nat) : async ()
```



### Function `stop_canister`
``` motoko no-repl
func stop_canister(args : IC.StopCanisterArgs, amount : Nat) : async ()
```



### Function `stored_chunks`
``` motoko no-repl
func stored_chunks(args : IC.StoredChunksArgs, amount : Nat) : async IC.StoredChunksResult
```



### Function `take_canister_snapshot`
``` motoko no-repl
func take_canister_snapshot(args : IC.TakeCanisterSnapshotArgs, amount : Nat) : async IC.TakeCanisterSnapshotResult
```



### Function `uninstall_code`
``` motoko no-repl
func uninstall_code(args : IC.uninstall_code_args, amount : Nat) : async ()
```



### Function `update_settings`
``` motoko no-repl
func update_settings(args : IC.UpdateSettingsArgs, amount : Nat) : async ()
```



### Function `upload_chunk`
``` motoko no-repl
func upload_chunk(args : IC.UploadChunkArgs, amount : Nat) : async IC.UploadChunkResult
```



### Function `withdrawCycles`
``` motoko no-repl
func withdrawCycles(amount : Nat, payee : Principal) : async ()
```

