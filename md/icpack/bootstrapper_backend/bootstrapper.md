# bootstrapper_backend/bootstrapper
This module is legible to non-returning-function attack. Throw it away if it fails this way.
Data is stored in `bootstrapper_data` instead.

## Actor Class `Bootstrapper`

``` motoko no-repl
class Bootstrapper()
```


### Type `PubKey`
``` motoko no-repl
type PubKey = Blob
```



### Function `doBootstrapFrontend`
``` motoko no-repl
func doBootstrapFrontend(frontendTweakPubKey : PubKey, user : Principal, amountToMove : Nat) : async { installedModules : [(Text, Principal)] }
```



### Function `bootstrapFrontend`
``` motoko no-repl
func bootstrapFrontend({ frontendTweakPubKey : PubKey }) : async { installedModules : [(Text, Principal)]; spentCycles : Int }
```

We don't allow to substitute user-chosen modules, because it would be a security risk of draining cycles.

In testing mode, cycles are supplied as the main account of the bootstrapper canister
and returned back to the same account.


### Function `bootstrapBackend`
``` motoko no-repl
func bootstrapBackend({ frontendTweakPubKey : PubKey; installedModules : [(Text, Principal)]; user : Principal; signature : Blob; additionalPackages : [{ packageName : Common.PackageName; version : Common.Version; repo : Common.RepositoryRO }] }) : async { spentCycles : Int }
```

Installs the backend after frontend is already installed, tweaks frontend.

We don't allow to substitute user-chosen modules for the package manager itself,
because it would be a security risk of draining cycles.


### Function `doBootstrapBackend`
``` motoko no-repl
func doBootstrapBackend({ pubKey : PubKey; installedModules : [(Text, Principal)]; user : Principal; amountToMove : Nat; tweaker : Data.FrontendTweaker; additionalPackages : [{ packageName : Common.PackageName; version : Common.Version; repo : Common.RepositoryRO }] }) : async { battery : Principal }
```



### Function `userAccountText`
``` motoko no-repl
func userAccountText() : async Text
```



### Function `topUpCycles`
``` motoko no-repl
func topUpCycles() : async { balance : Nat }
```



### Function `topUpWithICP`
``` motoko no-repl
func topUpWithICP() : async { balance : Nat }
```



### Function `balance`
``` motoko no-repl
func balance() : async Nat
```



### Function `userCycleBalance`
``` motoko no-repl
func userCycleBalance() : async Nat
```

