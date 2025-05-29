# package_manager_backend/main_indirect
Canister that takes on itself potentially non-returning calls.

## Actor Class `MainIndirect`

``` motoko no-repl
class MainIndirect({ packageManager : Principal; mainIndirect : Principal; simpleIndirect : Principal; battery : Principal; user : Principal; installationId : Common.InstallationId; userArg : Blob })
```


### Function `init`
``` motoko no-repl
func init({ installationId : Common.InstallationId }) : async ()
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
func installPackagesWrapper({ pmPrincipal : Principal; packages : [{ repo : Common.RepositoryRO; packageName : Common.PackageName; version : Common.Version; preinstalledModules : [(Text, Principal)]; arg : Blob; initArg : ?Blob }]; minInstallationId : Common.InstallationId; user : Principal; afterInstallCallback : ?{ canister : Principal; name : Text; data : Blob }; bootstrapping : Bool }) : ()
```

Internal.


### Function `installModule`
``` motoko no-repl
func installModule({ installationId : Common.InstallationId; moduleNumber : Nat; moduleName : ?Text; wasmModule : Common.SharedModule; user : Principal; packageManager : Principal; mainIndirect : Principal; simpleIndirect : Principal; preinstalledCanisterId : ?Principal; arg : Blob; afterInstallCallback : ?{ canister : Principal; name : Text; data : Blob } }) : ()
```



### Function `upgradePackageWrapper`
``` motoko no-repl
func upgradePackageWrapper({ minUpgradeId : Common.UpgradeId; packages : [{ installationId : Common.InstallationId; packageName : Common.PackageName; version : Common.Version; repo : Common.RepositoryRO; arg : Blob; initArg : ?Blob }]; user : Principal; afterUpgradeCallback : ?{ canister : Principal; name : Text; data : Blob } }) : ()
```



### Function `upgradeOrInstallModule`
``` motoko no-repl
func upgradeOrInstallModule({ upgradeId : Common.UpgradeId; installationId : Common.InstallationId; moduleNumber : Nat; moduleName : Text; wasmModule : Common.SharedModule; user : Principal; packageManager : Principal; simpleIndirect : Principal; arg : Blob; canister_id : ?Principal; afterUpgradeCallback : ?{ canister : Principal; name : Text; data : Blob } }) : ()
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

