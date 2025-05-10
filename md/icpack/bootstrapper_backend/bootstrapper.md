# bootstrapper_backend/bootstrapper
This module is legible to non-returning-function attack. Throw it away if it fails this way.
Data is stored in `bootstrapper_data` instead.

## Actor Class `Bootstrapper`

``` motoko no-repl
class Bootstrapper()
```


### Function `doBootstrapFrontend`
``` motoko no-repl
func doBootstrapFrontend(frontendTweakPubKey : PubKey, user : Principal, amountToMove : Nat) : async { installedModules : [(Text, Principal)] }
```



### Function `bootstrapFrontend`
``` motoko no-repl
func bootstrapFrontend() : async { installedModules : [(Text, Principal)]; spentCycles : Nat }
```

We don't allow to substitute user-chosen modules, because it would be a security risk of draining cycles.

In testing mode, cycles are supplied as the main account of the bootstrapper canister
and returned back to the same account.


### Function `bootstrapBackend`
``` motoko no-repl
func bootstrapBackend() : async { spentCycles : Nat }
```

Installs the backend after frontend is already installed, tweaks frontend.

We don't allow to substitute user-chosen modules for the package manager itself,
because it would be a security risk of draining cycles.


### Function `doBootstrapBackend`
``` motoko no-repl
func doBootstrapBackend() : async { battery : Principal }
```



### Type `PubKey`
``` motoko no-repl
type PubKey = Blob
```



### Type `PrivKey`
``` motoko no-repl
type PrivKey = Blob
```



### Function `userAccountText`
``` motoko no-repl
func userAccountText() : async Text
```



### Function `balance`
``` motoko no-repl
func balance() : async Nat
```

