# package_manager_backend/battery
Battery canister or battery module is a canister that holds cycles and delivers them to other canisters.

## Actor Class `Battery`

``` motoko no-repl
class Battery()
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



### Function `getOwners`
``` motoko no-repl
func getOwners() : async [Principal]
```



### Function `init`
``` motoko no-repl
func init() : async ()
```



### Function `b44c4a9beec74e1c8a7acbe46256f92f_isInitialized`
``` motoko no-repl
func b44c4a9beec74e1c8a7acbe46256f92f_isInitialized() : async ()
```



### Type `ModuleLocation`
``` motoko no-repl
type ModuleLocation = { package : { packageName : Text; guid : Blob }; moduleName : Text }
```



### Type `CanisterKind`
``` motoko no-repl
type CanisterKind = Text
```



### Type `CanisterMap`
``` motoko no-repl
type CanisterMap = Map.Map<ModuleLocation, CanisterKind>
```



### Type `CanisterKindsMap`
``` motoko no-repl
type CanisterKindsMap = Map.Map<CanisterKind, Common.CanisterFulfillment>
```



### Type `Battery`
``` motoko no-repl
type Battery = { canisterInitialCycles : Nat; defaultFulfillment : Common.CanisterFulfillment; canisterMap : CanisterMap; canisterKindsMap : CanisterKindsMap; var activatedCycles : Nat }
```



### Function `getCanisterInitialCycles`
``` motoko no-repl
func getCanisterInitialCycles() : async Nat
```



### Function `withdrawCycles`
``` motoko no-repl
func withdrawCycles(amount : Nat, payee : Principal) : async ()
```



### Function `withdrawCycles2`
``` motoko no-repl
func withdrawCycles2(amount : Nat, payee : Principal) : async ()
```

TODO@P3: Unused function.


### Function `withdrawCycles3`
``` motoko no-repl
func withdrawCycles3(amount : Nat, payee : Principal) : async ()
```



### Function `withdrawCycles4`
``` motoko no-repl
func withdrawCycles4(amount : Nat) : async ()
```



### Function `balance`
``` motoko no-repl
func balance() : async Nat
```

