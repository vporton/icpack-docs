# package_manager_backend/main_indirect
Canister that takes on itself potentially non-returning calls.

## Actor Class `MainIndirect`

``` motoko no-repl
class MainIndirect()
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



### Function `setOurPM`
``` motoko no-repl
func setOurPM(pm : Principal) : async ()
```



### Function `installPackagesWrapper`
``` motoko no-repl
func installPackagesWrapper() : ()
```

Internal.


### Function `installModule`
``` motoko no-repl
func installModule() : async ()
```



### Function `upgradePackageWrapper`
``` motoko no-repl
func upgradePackageWrapper() : ()
```



### Function `upgradeOrInstallModule`
``` motoko no-repl
func upgradeOrInstallModule() : ()
```



### Function `topUpOneCanisterFinish`
``` motoko no-repl
func topUpOneCanisterFinish(canister_id : Principal, fulfillment : Common.CanisterFulfillment) : ()
```

Internal.


### Function `withdrawCycles`
``` motoko no-repl
func withdrawCycles(amount : Nat, payee : Principal) : async ()
```

