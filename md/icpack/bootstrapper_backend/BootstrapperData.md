# bootstrapper_backend/BootstrapperData

## Actor Class `BootstrapperData`

``` motoko no-repl
class BootstrapperData(initialOwner : Principal)
```


### Type `PubKey`
``` motoko no-repl
type PubKey = Blob
```



### Function `changeOwner`
``` motoko no-repl
func changeOwner(newOwner : Principal)
```



### Type `FrontendTweaker`
``` motoko no-repl
type FrontendTweaker = { frontend : Principal; user : Principal }
```



### Function `setOwner`
``` motoko no-repl
func setOwner(newOwner : Principal)
```



### Function `putFrontendTweaker`
``` motoko no-repl
func putFrontendTweaker(pubKey : Blob, tweaker : FrontendTweaker) : async ()
```



### Function `getFrontendTweaker`
``` motoko no-repl
func getFrontendTweaker(pubKey : PubKey) : async FrontendTweaker
```



### Function `deleteFrontendTweaker`
``` motoko no-repl
func deleteFrontendTweaker(pubKey : PubKey) : async ()
```

